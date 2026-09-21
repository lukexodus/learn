## Numerical Pricing of Path Dependent Payoffs

### Overview

Path-dependent payoffs are derivatives whose terminal value depends on the trajectory of the underlying asset over the life of the contract, not merely its terminal price. Barrier options, Asian options, lookback options, and cliquets all fall into this category. Because the payoff is a functional of the entire price path rather than a single point $S_T$, closed-form (Black-Scholes-style) solutions exist only for a narrow set of cases (e.g., continuously monitored geometric-average Asian options, single-barrier options under GBM). For the majority of realistic contracts — discretely monitored barriers, arithmetic-average Asians, path-dependent baskets, or payoffs under local/stochastic volatility — numerical methods are required.

The three dominant numerical families are:

- **Monte Carlo (MC) simulation** — simulates discretized paths and averages discounted payoffs
- **Finite difference (PDE) methods** — solves the pricing PDE on a grid, extended with an auxiliary state variable for the path-dependent feature
- **Lattice/tree methods** — extend binomial/trinomial trees with auxiliary state nodes or forward shooting grids

Each method trades off dimensionality, accuracy, computational cost, and ease of handling discrete monitoring versus continuous monitoring.

### Why Path Dependence Breaks Closed-Form Pricing

**Key Points**

- Under risk-neutral valuation, price $= e^{-rT}\mathbb{E}^{\mathbb{Q}}[\text{Payoff}(S_t, 0 \le t \le T)]$
- For path-independent payoffs, the payoff is a function of $S_T$ alone, so the pricing problem reduces to integrating against the terminal marginal density of $S_T$ — a 1-D integral
- For path-dependent payoffs, the expectation is over the joint law of the entire path, which is infinite-dimensional in continuous time and high-dimensional once discretized (one dimension per monitoring date)
- The PDE approach must augment the state space: instead of solving $V(S,t)$, one must solve $V(S, A, t)$ where $A$ is an auxiliary variable (running average, running maximum, barrier-hit indicator, etc.), turning a 1-D spatial PDE into a 2-D (or higher) PDE

This dimensional blow-up is the central computational challenge driving method selection.

### Method 1: Monte Carlo Simulation

#### Path Discretization

The underlying is simulated under the risk-neutral measure via an SDE discretization. For GBM:

$$S_{t_{i+1}} = S_{t_i} \exp\left[\left(r - q - \frac{\sigma^2}{2}\right)\Delta t + \sigma\sqrt{\Delta t}\, Z_i\right]$$

where $Z_i \sim \mathcal{N}(0,1)$ i.i.d. This exact scheme is preferred over Euler discretization for GBM since it is exact at each step (no discretization bias in the log-price recursion itself). For more general diffusions (local vol, stochastic vol, jump-diffusion), Euler-Maruyama or Milstein schemes introduce $O(\Delta t)$ or $O(\Delta t)$ bias respectively that must be controlled via step-size refinement.

**Algorithm — generic path-dependent MC pricer:**

```mermaid
flowchart TD
    A[Set parameters: S0, r, q, sigma, T, N_steps, N_paths] --> B[For each path j = 1..N_paths]
    B --> C[Simulate path S_0..S_N via discretized SDE]
    C --> D[Compute path-dependent statistic: avg, max, min, barrier hit]
    D --> E[Evaluate payoff function using statistic and S_N]
    E --> F[Store discounted payoff: exp(-rT) * payoff_j]
    F --> G{More paths?}
    G -- yes --> B
    G -- no --> H[Price = mean of discounted payoffs]
    H --> I[Std Error = std(discounted payoffs) / sqrt(N_paths)]
```

#### Payoff Functionals by Instrument Type

- **Arithmetic Asian call**: $\left(\frac{1}{N}\sum_{i=1}^N S_{t_i} - K\right)^+$ — requires running arithmetic average, accumulated at each step
- **Geometric Asian call**: $\left(\left(\prod_{i=1}^N S_{t_i}\right)^{1/N} - K\right)^+$ — has a closed-form solution under GBM and serves as a control variate for the arithmetic case
- **Up-and-out barrier call**: $(S_T - K)^+ \cdot \mathbb{1}\{\max_{i} S_{t_i} < B\}$ — requires tracking the running maximum and checking the barrier condition at (or between) monitoring dates
- **Lookback call (floating strike)**: $S_T - \min_i S_{t_i}$ — requires the running minimum
- **Cliquet / ratchet**: sum of periodic capped/floored returns $\sum_k \min(\max(R_k, f), c)$ — requires storing each sub-period return

**Example**

```python
import numpy as np

def mc_up_and_out_call(S0, K, B, r, q, sigma, T, N_steps, N_paths, seed=42):
    rng = np.random.default_rng(seed)
    dt = T / N_steps
    drift = (r - q - 0.5 * sigma**2) * dt
    vol = sigma * np.sqrt(dt)

    Z = rng.standard_normal((N_paths, N_steps))
    log_increments = drift + vol * Z
    log_paths = np.cumsum(log_increments, axis=1)
    S_paths = S0 * np.exp(log_paths)
    S_paths = np.hstack([np.full((N_paths, 1), S0), S_paths])

    running_max = np.max(S_paths, axis=1)
    knocked_out = running_max >= B
    payoff = np.where(knocked_out, 0.0, np.maximum(S_paths[:, -1] - K, 0.0))

    discounted = np.exp(-r * T) * payoff
    price = discounted.mean()
    stderr = discounted.std(ddof=1) / np.sqrt(N_paths)
    return price, stderr
```

#### The Discrete Monitoring Bias for Barriers

**Key Points**

- Simulated paths only observe $S$ at discrete monitoring dates $t_i$, so a path can breach the barrier *between* dates without the simulation detecting it — this systematically biases knock-out prices upward (overstates survival probability) and knock-in prices downward
- The Broadie-Glasserman-Kou (1997) continuity correction adjusts the discrete barrier level to approximate continuous monitoring: for an up barrier, shift $B \to B\exp(\beta\sigma\sqrt{\Delta t})$, and for a down barrier, $B \to B\exp(-\beta\sigma\sqrt{\Delta t})$, where $\beta = -\zeta(1/2)/\sqrt{2\pi} \approx 0.5826$ ($\zeta$ is the Riemann zeta function)
- An alternative is Brownian bridge correction: between two simulated points $S_{t_i}, S_{t_{i+1}}$, the probability that the *continuous* Brownian bridge connecting them breached the barrier has a known closed form, allowing either (a) analytic adjustment of the payoff probability or (b) rejection/acceptance sampling of a bridge-breach event at each step

$$P(\text{no breach in } [t_i, t_{i+1}] \mid S_{t_i}, S_{t_{i+1}}) = 1 - \exp\left(-\frac{2(B - S_{t_i})^+(B - S_{t_{i+1}})^+}{\sigma^2 S_{t_i}S_{t_{i+1}} \Delta t}\right) \quad \text{(for a lower barrier, informal form)}$$

This bridge-based correction is generally preferred in production systems since it converges to the continuous-monitoring price without needing a heuristic shift constant, and it can be vectorized cheaply.

#### Variance Reduction

Path-dependent MC is often slow to converge ($O(N^{-1/2})$ standard error), so variance reduction is standard practice:

- **Control variates**: For arithmetic Asians, use the geometric Asian (closed-form under GBM) as a control:



  $$\hat{V}_{\text{arith}} = \bar{V}_{\text{arith,MC}} - \left(\bar{V}_{\text{geo,MC}} - V_{\text{geo,exact}}\right)$$

  This can reduce variance by one to two orders of magnitude since arithmetic and geometric averages are highly correlated path-by-path.
- **Antithetic variates**: pair each $Z_i$ with $-Z_i$ to reduce variance for payoffs with monotonic or near-linear dependence on the driving noise
- **Importance sampling**: shift the drift of the simulated measure to increase the frequency of rare-but-payoff-relevant events (e.g., barrier breaches for far out-of-the-money knock-in options), then reweight by the Radon-Nikodym derivative (likelihood ratio)
- **Stratified sampling / Latin hypercube**: ensures more uniform coverage of the driving randomness across paths, especially useful when only a few time steps dominate the payoff variance
- **Quasi-Monte Carlo (QMC)**: replace pseudo-random $Z_i$ with low-discrepancy sequences (Sobol', Halton) combined with a Brownian bridge or PCA path construction (which concentrates variance in the first few dimensions, aligning with QMC's strength in low effective dimension); can achieve near-$O(N^{-1})$ convergence for smooth payoffs

#### Greeks via Monte Carlo

- **Pathwise derivative method**: differentiate the discounted payoff with respect to the parameter, valid when the payoff is (a.e.) differentiable in the underlying — works well for European-style path payoffs but requires care at barrier/kink discontinuities (the discontinuity introduces a bias term that must be handled via a boundary correction or via the likelihood ratio method instead)
- **Likelihood ratio method**: differentiate the density instead of the payoff, $\frac{\partial}{\partial\theta}\mathbb{E}[f(S)] = \mathbb{E}\left[f(S)\frac{\partial \log p(S;\theta)}{\partial\theta}\right]$ — robust to discontinuous payoffs (barriers, digitals) but typically has higher variance than pathwise for smooth payoffs
- **Bumping (finite difference on price)**: simplest but requires re-running simulations with common random numbers to control variance of the differenced estimator; biased for discontinuous payoffs unless a large enough bump is used relative to the discretization

### Method 2: PDE / Finite Difference with Auxiliary State

#### State Augmentation

For a payoff depending on running average $A_t = \int_0^t S_u\,du$ (continuous arithmetic Asian), the value function $V(S,A,t)$ solves an augmented Black-Scholes PDE:

$$\frac{\partial V}{\partial t} + rS\frac{\partial V}{\partial S} + \frac{1}{2}\sigma^2 S^2 \frac{\partial^2 V}{\partial S^2} + S\frac{\partial V}{\partial A} - rV = 0$$

with terminal condition $V(S,A,T) = \left(\frac{A}{T} - K\right)^+$. Note the added first-order term $S \partial V/\partial A$ (no diffusion in the $A$ direction — the average evolves deterministically given $S$), which makes this a degenerate, convection-dominated PDE in the second dimension. This requires care with numerical schemes (upwinding in the $A$-direction) to avoid spurious oscillations.

A well-known dimension-reduction trick (Rogers-Shi / Večeř) reduces the 2-D Asian PDE to an effectively 1-D PDE via the change of variable $z = \frac{K - A/T}{S}$ (or similar), producing:

$$\frac{\partial u}{\partial t} + \frac{1}{2}\sigma^2 z^2 \frac{\partial^2 u}{\partial z^2} + \left(1 - r z - \frac{z}{T}\right)\frac{\partial u}{\partial z} = 0$$

This is far more efficient than solving the full 2-D grid, though it still contains a degenerate/singular coefficient structure near $z=0$ requiring careful discretization.

#### Barrier Options via PDE

Barrier options are more naturally handled by imposing the barrier as a **boundary condition** on the standard 1-D Black-Scholes PDE rather than an added state dimension:

- Up-and-out call with barrier $B$: solve the standard BS PDE on the domain $S \in [0, B]$ with boundary condition $V(B,t) = 0$ for all $t$
- Down-and-out put with barrier $B$: solve on $S \in [B, \infty)$ with $V(B,t)=0$
- Discretely monitored barriers: apply the $V=0$ condition (or clamp/reset) only at the grid time-steps that correspond to monitoring dates, leaving the PDE to evolve freely between monitoring dates — this exactly matches the discrete-monitoring structure of the contract and avoids the continuity-correction bias issue seen in MC

**Key Points**

- Crank-Nicolson time-stepping is the standard choice for stability and second-order accuracy in time, but can produce spurious oscillations near the barrier or strike (non-smooth initial/boundary data) — often mitigated by starting with a few fully implicit (Rannacher) steps before switching to Crank-Nicolson
- Grid should be non-uniform, concentrating points near the strike $K$ and the barrier $B$, since these are the regions of highest payoff curvature/discontinuity
- PDE methods scale poorly beyond 2-3 state dimensions (curse of dimensionality via grid size $\sim n^d$), so they are preferred for single-barrier, single-average path-dependent products, while MC dominates for multi-asset or multi-feature path dependence (e.g., basket Asians, multiple barriers, path-dependent baskets)

### Method 3: Lattice / Tree-Based Methods

#### Forward Shooting Grid (FSG)

The Forward Shooting Grid method (Hull-White / Barraquand) extends a standard binomial or trinomial tree by attaching, at each node, a small set of discretized auxiliary state values (e.g., possible running-average levels reachable at that node). The algorithm:

1. Build the standard price tree for $S$
2. At each node, enumerate a discretized set of feasible values of the path-dependent statistic (running average, running max)
3. Propagate forward: for each (price, state) pair, compute the successor states under both the up- and down-moves
4. At maturity, evaluate the payoff for every (price, state) combination
5. Roll back via standard risk-neutral discounting, interpolating between the discretized auxiliary state grid points as needed (since forward propagation of a continuous average does not generally land exactly on the coarse grid)

**Key Points**

- FSG is intuitive and easy to implement for Asian and lookback options on a recombining tree
- Interpolation error introduced by the discretized auxiliary grid is the dominant source of numerical error, distinct from tree discretization error — accuracy improves by refining the auxiliary grid resolution independently of the number of time steps
- For barrier options, the tree encounters a **placement problem**: if the barrier does not coincide exactly with a layer of tree nodes, convergence degrades from $O(1/N)$ to $O(1/\sqrt{N})$ and can even oscillate non-monotonically as $N$ increases; solutions include adjusting the tree geometry so that a node layer sits exactly on the barrier (Boyle-Lau method), or using a trinomial tree with an adjustable middle-branch probability to align nodes to the barrier level

#### Trinomial Tree Barrier Alignment

For an up-and-out barrier $B$, choose the number of time steps $N$ (or equivalently $\Delta t$) such that $B$ coincides with a tree layer:

$$B = S_0 u^m \quad \text{for some integer } m$$

where $u$ is the up-move multiplier. Solving for the tree spacing that satisfies this exactly for a chosen $m$ (Boyle-Lau) removes the placement-induced oscillation and restores fast, monotonic convergence.

### Comparative Summary

| Method | Best suited for | Weakness | Typical convergence |
| --- | --- | --- | --- |
| Monte Carlo | High-dimensional path dependence, multi-asset, path-dependent baskets, exotic monitoring schedules | Slow standard convergence, Greeks require care, discrete-barrier bias | $O(N^{-1/2})$, improved to near $O(N^{-1})$ with QMC |
| PDE / Finite Difference | Single-asset barrier and Asian options, early-exercise features (American-style) | Curse of dimensionality beyond 2-3 state variables | $O(\Delta t) $ to $O(\Delta t^2, \Delta S^2)$ depending on scheme |
| Lattice / FSG | Educational clarity, American-style path-dependent options, moderate accuracy needs | Barrier/node placement bias, interpolation error in auxiliary state | $O(1/N)$ if aligned, $O(1/\sqrt N)$ if misaligned |

### Model Risk Beyond GBM

**Key Points**

- Path-dependent payoffs (especially barriers) are highly sensitive to the *volatility smile/skew*, since the option's value depends on the probability of visiting extreme price levels — pricing under a flat Black-Scholes volatility materially misprices barriers relative to local volatility or stochastic volatility models calibrated to the smile [Inference: the direction and magnitude of mispricing depends on the specific skew shape and barrier type, and is not a universal rule]
- Local volatility models (Dupire) can be incorporated into MC by simulating with the state-and-time-dependent $\sigma_{loc}(S,t)$ drawn from the Dupire formula, or into PDE methods by making the diffusion coefficient a function of $(S,t)$
- Stochastic volatility models (Heston, SABR) require simulating an additional correlated variance process, which increases MC path dimensionality but is still tractable; PDE approaches become 3-D (S, v, and possibly A) and are usually abandoned in favor of MC or Fourier-based methods for the non-path-dependent components combined with MC for the path-dependent overlay
- Jump-diffusion and other discontinuous-path models materially change the discrete-vs-continuous monitoring correction terms for barriers, since jumps can breach a barrier "silently" between very closely spaced monitoring dates in ways continuous-diffusion corrections do not capture [Unverified: exact correction formulas are model-specific and require separate derivation, e.g., via Lévy process barrier-crossing theory]

### Barrier Monitoring Timeline (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 760 220" font-family="Helvetica, Arial, sans-serif">
<text x="380" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Discrete vs. Continuous Barrier Monitoring (svg_diagram)</text>
<line x1="60" y1="150" x2="700" y2="150" stroke="#333" stroke-width="1.5" />
<text x="700" y="170" font-size="12" fill="#333">t</text>

<path d="M 60 150 C 120 100, 160 60, 200 90 C 240 120, 260 40, 300 70 C 340 100, 360 130, 400 80 C 440 40, 480 110, 520 95 C 560 85, 600 60, 640 100 C 660 120, 680 130, 700 140" fill="none" stroke="`#2b6cb0`" stroke-width="2" />

<line x1="60" y1="55" x2="700" y2="55" stroke="#c0392b" stroke-width="1.5" stroke-dasharray="6,3" />
<text x="65" y="48" font-size="12" fill="#c0392b">Barrier B</text>
<circle cx="378" cy="52" r="4" fill="#c0392b" />
<text x="386" y="45" font-size="11" fill="#c0392b">continuous breach (undetected by discrete grid)</text>
<g fill="#2b6cb0">
<circle cx="120" cy="150" r="3" />
<circle cx="200" cy="150" r="3" />
<circle cx="300" cy="150" r="3" />
<circle cx="400" cy="150" r="3" />
<circle cx="520" cy="150" r="3" />
<circle cx="640" cy="150" r="3" />
</g>
<g font-size="11" fill="#2b6cb0" text-anchor="middle">
<text x="120" y="170">t1</text>
<text x="200" y="170">t2</text>
<text x="300" y="170">t3</text>
<text x="400" y="170">t4</text>
<text x="520" y="170">t5</text>
<text x="640" y="170">t6</text>
</g>
<line x1="120" y1="150" x2="120" y2="130" stroke="#2b6cb0" stroke-dasharray="2,2" />
<line x1="200" y1="150" x2="200" y2="90" stroke="#2b6cb0" stroke-dasharray="2,2" />
<line x1="300" y1="150" x2="300" y2="70" stroke="#2b6cb0" stroke-dasharray="2,2" />
<line x1="400" y1="150" x2="400" y2="80" stroke="#2b6cb0" stroke-dasharray="2,2" />
<line x1="520" y1="150" x2="520" y2="95" stroke="#2b6cb0" stroke-dasharray="2,2" />
<line x1="640" y1="150" x2="640" y2="100" stroke="#2b6cb0" stroke-dasharray="2,2" />

<text x="380" y="200" text-anchor="middle" font-size="12" fill="#555">Discrete monitoring samples miss the mid-interval breach near t3–t4, overstating survival probability for a knock-out option.</text>

</svg>

### PDE Grid with Barrier Boundary (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 300" font-family="Helvetica, Arial, sans-serif">
<text x="350" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Finite Difference Grid for Up-and-Out Call (svg_diagram)</text>
<line x1="80" y1="260" x2="620" y2="260" stroke="#333" stroke-width="1.5" />
<text x="640" y="264" font-size="12" fill="#333">t (0 → T)</text>
<line x1="80" y1="260" x2="80" y2="40" stroke="#333" stroke-width="1.5" />
<text x="60" y="35" font-size="12" fill="#333">S</text>
<line x1="80" y1="55" x2="620" y2="55" stroke="#c0392b" stroke-width="2" />
<text x="90" y="48" font-size="12" fill="#c0392b">S = B (V = 0 boundary)</text>
<line x1="80" y1="150" x2="620" y2="150" stroke="#7f8c8d" stroke-width="1.5" stroke-dasharray="4,3" />
<text x="90" y="144" font-size="11" fill="#555">S = K (payoff kink — denser grid nearby)</text>

<text x="70" y="264" font-size="11" fill="#333" text-anchor="end">0</text>

<g stroke="#dcdcdc">
<line x1="140" y1="55" x2="140" y2="260" />
<line x1="200" y1="55" x2="200" y2="260" />
<line x1="260" y1="55" x2="260" y2="260" />
<line x1="320" y1="55" x2="320" y2="260" />
<line x1="380" y1="55" x2="380" y2="260" />
<line x1="440" y1="55" x2="440" y2="260" />
<line x1="500" y1="55" x2="500" y2="260" />
<line x1="560" y1="55" x2="560" y2="260" />
</g>
<g stroke="#dcdcdc">
<line x1="80" y1="200" x2="620" y2="200" />
<line x1="80" y1="175" x2="620" y2="175" />
<line x1="80" y1="125" x2="620" y2="125" />
<line x1="80" y1="100" x2="620" y2="100" />
<line x1="80" y1="75" x2="620" y2="75" />
</g>

<text x="350" y="285" text-anchor="middle" font-size="12" fill="#555">Domain truncated at S = B with Dirichlet V = 0; grid refined near S = K for payoff curvature.</text>

</svg>

### Calibration Consistency Workflow (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 720 260" font-family="Helvetica, Arial, sans-serif">
<text x="360" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Smile-Consistent Path-Dependent Pricing Pipeline (svg_diagram)</text>
<rect x="30" y="60" width="150" height="50" rx="6" fill="#eaf2fb" stroke="#2b6cb0" />
<text x="105" y="90" text-anchor="middle" font-size="12" fill="#1a1a1a">Vanilla option</text>
<text x="105" y="104" text-anchor="middle" font-size="12" fill="#1a1a1a">market quotes</text>
<rect x="260" y="60" width="170" height="50" rx="6" fill="#eaf2fb" stroke="#2b6cb0" />
<text x="345" y="84" text-anchor="middle" font-size="12" fill="#1a1a1a">Calibrate local/</text>
<text x="345" y="98" text-anchor="middle" font-size="12" fill="#1a1a1a">stochastic vol model</text>
<rect x="510" y="60" width="170" height="50" rx="6" fill="#eaf2fb" stroke="#2b6cb0" />
<text x="595" y="84" text-anchor="middle" font-size="12" fill="#1a1a1a">Simulate/solve PDE</text>
<text x="595" y="98" text-anchor="middle" font-size="12" fill="#1a1a1a">with calibrated model</text>
<rect x="260" y="170" width="170" height="50" rx="6" fill="#fdf3ea" stroke="#c0781b" />
<text x="345" y="200" text-anchor="middle" font-size="12" fill="#1a1a1a">Path-dependent payoff</text>
<rect x="510" y="170" width="170" height="50" rx="6" fill="#eafbea" stroke="#2f8f4e" />
<text x="595" y="194" text-anchor="middle" font-size="12" fill="#1a1a1a">Discounted expected</text>
<text x="595" y="208" text-anchor="middle" font-size="12" fill="#1a1a1a">payoff = fair value</text>
<line x1="180" y1="85" x2="255" y2="85" stroke="#333" marker-end="url(#arrow1)" />
<line x1="430" y1="85" x2="505" y2="85" stroke="#333" marker-end="url(#arrow1)" />
<line x1="595" y1="110" x2="595" y2="165" stroke="#333" marker-end="url(#arrow1)" />
<line x1="345" y1="170" x2="345" y2="115" stroke="#333" marker-end="url(#arrow1)" stroke-dasharray="4,3" />
<line x1="430" y1="195" x2="505" y2="195" stroke="#333" marker-end="url(#arrow1)" />
<text x="360" y="248" text-anchor="middle" font-size="12" fill="#555">Barrier/Asian pricing must use the same calibrated smile-consistent model as vanilla hedges to avoid arbitrage between hedge and exotic book.</text>

</svg>

### Numerical Convergence Diagnostics

**Key Points**

- Always report a **standard error** alongside the MC price estimate, and ideally a **95% confidence interval** ($\hat{V} \pm 1.96 \cdot SE$), not a bare point estimate — a price without an error bar cannot be judged for reliability
- For PDE methods, perform a **grid refinement study**: halve $\Delta S$ and $\Delta t$ successively and confirm the price converges at the theoretical order (e.g., second order in space for central differencing); a lack of expected convergence order signals a coding error or an unresolved discontinuity (e.g., barrier not aligned to a grid line)
- For lattice methods, plot price against $N$ (number of steps) and check for the expected monotonic or oscillatory convergence pattern; persistent large-amplitude oscillation for barrier options is the classic signature of the node-placement problem discussed above
- Cross-validate different methods against each other on a case where at least one has a closed-form or semi-analytic benchmark (e.g., continuously monitored geometric Asian, single up-and-out call under GBM via reflection principle) before trusting the same code on payoffs lacking a closed form

**Next Steps**

- Barrier option analytics and the reflection principle for continuously monitored single/double barriers
- Discrete monitoring adjustments: Broadie-Glasserman-Kou correction, Brownian bridge correction in depth
- American-style path-dependent products (e.g., American Asian options) and the added complexity of combining early exercise with path dependence
- Least-Squares Monte Carlo (Longstaff-Schwartz) for American/Bermudan features layered onto path-dependent payoffs
- Local volatility model construction (Dupire's formula) and its integration into path-dependent MC engines
- Multi-asset path-dependent products (basket Asians, worst-of/best-of barriers) and copula/correlation modeling implications
- Cliquet and forward-start option structuring and their sensitivity to forward volatility/skew
- Greeks estimation for path-dependent products: pathwise vs. likelihood ratio methods in production risk systems
- Variance reduction deep dive: importance sampling design for deep out-of-the-money knock-in barriers