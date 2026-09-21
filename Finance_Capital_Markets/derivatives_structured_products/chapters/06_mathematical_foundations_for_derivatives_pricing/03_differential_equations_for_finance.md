## Differential Equations for Finance


### Overview

Differential equations formalize the relationship between the price of a derivative and the underlying variables it depends on — most centrally, the underlying asset price and time. Ordinary differential equations (ODEs) describe deterministic dynamics, while partial differential equations (PDEs) capture how a derivative's value evolves as a function of multiple variables simultaneously (price and time, or price, volatility, and time in more advanced models). The Black-Scholes PDE is the single most important result in this domain, translating a stochastic pricing problem into a deterministic PDE that can be solved analytically or numerically.

### From Stochastic Differential Equations to PDEs

A **stochastic differential equation (SDE)** describes how a random process evolves over time, combining a deterministic drift term and a random diffusion term. The canonical SDE for an asset price under geometric Brownian motion (GBM) is:

$$dS_t = \mu S_t \, dt + \sigma S_t \, dW_t$$

where $dW_t$ is the increment of a Wiener process (Brownian motion), covered in depth in the stochastic calculus section of this chapter. The critical conceptual bridge in derivatives pricing is **Itô's lemma**, which allows a function $V(S,t)$ of a stochastic process to itself be expressed via an SDE:

$$dV = \left(\frac{\partial V}{\partial t} + \mu S \frac{\partial V}{\partial S} + \frac{1}{2}\sigma^2 S^2 \frac{\partial^2 V}{\partial S^2}\right)dt + \sigma S \frac{\partial V}{\partial S}\,dW_t$$

**Key Points**:

- This result — that a smooth function of a stochastic process is itself governed by an SDE with a specific, computable drift and diffusion — is the direct mechanism by which the random SDE for $S_t$ is converted into a deterministic PDE for the derivative's value $V(S,t)$, via the no-arbitrage/hedging argument described next
- The presence of the $\frac{1}{2}\sigma^2 S^2 \frac{\partial^2 V}{\partial S^2}$ term (arising from Itô's lemma's second-order correction) is what distinguishes stochastic calculus from ordinary calculus, and is the mathematical origin of the option Greek **gamma**'s role in the pricing PDE

### Derivation of the Black-Scholes PDE

**Setup**: Construct a portfolio $\Pi$ consisting of one long derivative $V(S,t)$ and $-\Delta$ units of the underlying (a hedging/replication argument):

$$\Pi = V - \Delta S$$

Applying Itô's lemma to $dV$ and choosing $\Delta = \partial V/\partial S$ (the option's delta) to eliminate the stochastic term:

$$d\Pi = \left(\frac{\partial V}{\partial t} + \frac{1}{2}\sigma^2 S^2 \frac{\partial^2 V}{\partial S^2}\right) dt$$

**Key Points**:

- The random $dW_t$ term cancels exactly when $\Delta = \partial V/\partial S$ — this is the essence of **delta hedging** and the no-arbitrage argument underlying the entire PDE derivation
- Because the resulting portfolio $\Pi$ has **no stochastic term**, it must, under absence of arbitrage, earn exactly the risk-free rate: $d\Pi = r\Pi \, dt$

Equating the two expressions for $d\Pi$ and substituting $\Pi = V - S\frac{\partial V}{\partial S}$ yields the **Black-Scholes PDE**:

$$\frac{\partial V}{\partial t} + \frac{1}{2}\sigma^2 S^2 \frac{\partial^2 V}{\partial S^2} + rS\frac{\partial V}{\partial S} - rV = 0$$

**Key Points**:

- This is a **linear, second-order parabolic PDE**, structurally related to the heat/diffusion equation from physics (a well-known and frequently exploited analogy that allows heat-equation solution techniques to be adapted for option pricing)
- Critically, the **drift parameter $\mu$ of the underlying's real-world dynamics does not appear** in the final PDE — it was eliminated by the hedging argument. This is the PDE-based manifestation of risk-neutral valuation: since $\mu$ drops out, the PDE (and its solution) are the same regardless of the underlying's real-world expected return, which is why the equation can be solved using the risk-free rate $r$ in place of $\mu$ without reference to actual risk preferences
- Solving this PDE requires **boundary and terminal conditions** specific to the derivative in question (e.g., for a European call, the terminal condition is $V(S,T) = \max(S-K, 0)$)

### Analogy to the Heat Equation

The classical heat equation is:

$$\frac{\partial u}{\partial \tau} = \frac{1}{2}\frac{\partial^2 u}{\partial x^2}$$

With a change of variables (substituting $x = \ln S$, reversing time via $\tau = T - t$, and rescaling the value function to remove the discounting and drift terms), the Black-Scholes PDE can be transformed into exactly this form. This transformation is the classical route by which Black and Scholes originally derived their closed-form solution, borrowing the known heat-equation solution (a convolution with a Gaussian kernel) and mapping it back to option-pricing variables.

**Key Points**:

- [Inference] This heat-equation analogy is widely taught as the historical and pedagogical bridge connecting option pricing to a well-established area of applied mathematics with known analytical solution techniques, though modern derivations of the Black-Scholes formula (e.g., via risk-neutral expectation and the lognormal density directly) do not strictly require going through this transformation

### PDE Solution Structure (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 780 420">
<text x="390" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Black-Scholes PDE — Domain and Boundary Conditions (svg_diagram)</text>
<line x1="100" y1="360" x2="700" y2="360" stroke="#333" stroke-width="1.5" />
<line x1="100" y1="60" x2="100" y2="360" stroke="#333" stroke-width="1.5" />
<text x="400" y="395" text-anchor="middle" font-size="13" fill="#333">Underlying Price S</text>
<text x="45" y="210" text-anchor="middle" font-size="13" fill="#333" transform="rotate(-90 45 210)">Time t</text>

<text x="100" y="380" font-size="11" fill="#555">0</text>

<text x="690" y="380" font-size="11" fill="#555">S → ∞</text>

<text x="65" y="65" font-size="11" fill="#555">T</text>

<text x="65" y="365" font-size="11" fill="#555">0</text>


<rect x="100" y="60" width="600" height="300" fill="#eaf1fb" opacity="0.5" />
<text x="400" y="200" text-anchor="middle" font-size="13" fill="#1a1a1a">PDE holds in interior:</text>
<text x="400" y="220" text-anchor="middle" font-size="12" fill="#1a1a1a">∂V/∂t + ½σ²S²∂²V/∂S² + rS∂V/∂S − rV = 0</text>

<line x1="100" y1="60" x2="700" y2="60" stroke="#1f6fd6" stroke-width="4" />
<text x="400" y="45" text-anchor="middle" font-size="12" fill="#1f6fd6" font-weight="bold">Terminal condition at t=T: V(S,T) = max(S-K,0)</text>

<line x1="100" y1="60" x2="100" y2="360" stroke="#d6291f" stroke-width="4" />
<text x="120" y="200" font-size="12" fill="#d6291f" font-weight="bold" transform="rotate(-90 120 200)">V(0,t) = 0 (call)</text>

<line x1="700" y1="60" x2="700" y2="360" stroke="#1a8a3a" stroke-width="4" />
<text x="680" y="200" font-size="12" fill="#1a8a3a" font-weight="bold" transform="rotate(-90 680 200)">V(S,t) ~ S - Ke^-r(T-t) as S → ∞</text>
</svg>

### Boundary Conditions for Standard Instruments

| Instrument | Terminal Condition ($t=T$) | Boundary at $S=0$ | Boundary as $S \to \infty$ |
| --- | --- | --- | --- |
| European Call | $V(S,T) = \max(S-K,0)$ | $V(0,t) = 0$ | $V \sim S - Ke^{-r(T-t)}$ |
| European Put | $V(S,T) = \max(K-S,0)$ | $V(0,t) = Ke^{-r(T-t)}$ | $V \to 0$ |
| Binary/Digital Call | $V(S,T) = \mathbb{1}_{\{S>K\}}$ | $V(0,t)=0$ | $V \to e^{-r(T-t)}$ |

**Key Points**: These boundary conditions, combined with the PDE itself, uniquely determine the solution — this is precisely the structure that leads to the closed-form Black-Scholes formula for European calls and puts, since the PDE with these particular boundary/terminal conditions has a known analytical solution via the heat-kernel convolution method.

### American Options: Free Boundary Problems

For American-style options (exercisable at any time before expiration), the PDE framework extends to a **free boundary problem** (also called an obstacle problem), since the option holder's early-exercise decision introduces an additional unknown: the optimal exercise boundary $S^*(t)$ itself.

The governing relationship becomes a **variational inequality** rather than a strict equality:

$$\frac{\partial V}{\partial t} + \frac{1}{2}\sigma^2 S^2\frac{\partial^2 V}{\partial S^2} + rS\frac{\partial V}{\partial S} - rV \leq 0, \qquad V(S,t) \geq \text{Payoff}(S)$$

with equality holding in the **continuation region** (where it is optimal to hold) and the PDE inequality becoming strict in the **exercise region** (where the option value equals the immediate exercise payoff).

**Key Points**:

- This free-boundary formulation has no general closed-form solution (unlike the European case) and is typically solved numerically — via finite-difference methods with an early-exercise check at each grid point, binomial/trinomial trees (which naturally incorporate early exercise via backward induction), or specialized approximation methods
- [Inference] The lack of a general closed-form solution for American options is a standard, well-established result in the derivatives pricing literature; specific closed-form or quasi-closed-form approximations do exist for particular cases (e.g., perpetual American options, or approximations like Barone-Adesi-Whaley), but these are special cases rather than a general solution to the free boundary problem

### Numerical Methods for Solving the PDE

**Finite Difference Methods**: Discretize the $(S,t)$ domain into a grid and approximate derivatives using difference formulas.

- **Explicit finite difference**: Approximates $\partial V/\partial t$ using a forward difference, computing the solution at each time step directly from the previous step's known values. Simple to implement but subject to a **stability condition** relating the time step size $\Delta t$ and space step size $\Delta S$ — violating this condition causes the numerical solution to diverge.
- **Implicit finite difference**: Approximates $\partial V/\partial t$ using a backward difference, requiring the solution of a system of linear equations at each time step. Unconditionally stable with respect to $\Delta t, \Delta S$, at the cost of greater computational complexity per step.
- **Crank-Nicolson method**: Averages the explicit and implicit schemes, achieving second-order accuracy in both time and space and generally offering a favorable balance of stability and accuracy — a widely used standard choice in practice for PDE-based option pricing.

**Key Points**:

- [Inference] The relative merits of these schemes (accuracy order, stability region, computational cost) are well-established results in numerical analysis; the specific choice among them in a production pricing system typically depends on additional practical factors (ease of incorporating early exercise, path-dependency, or multiple underlying factors) beyond the basic accuracy/stability tradeoff described here
- Grid-based PDE methods scale poorly to multiple underlying factors (the "curse of dimensionality") — for derivatives depending on several state variables (e.g., basket options, multi-asset derivatives, or stochastic volatility models with a second state variable), Monte Carlo methods (covered elsewhere in this chapter) often become more practical despite their own convergence-rate tradeoffs

### PDE Solution Process (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 780 300">
<text x="390" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Finite Difference Grid — Backward Time-Stepping (svg_diagram)</text>
<line x1="100" y1="260" x2="700" y2="260" stroke="#333" stroke-width="1.5" />
<line x1="100" y1="60" x2="100" y2="260" stroke="#333" stroke-width="1.5" />
<text x="400" y="285" text-anchor="middle" font-size="13" fill="#333">Underlying Price Grid (S)</text>
<text x="45" y="160" text-anchor="middle" font-size="13" fill="#333" transform="rotate(-90 45 160)">Time (t)</text>

<g stroke="#ccc" stroke-width="1">
<line x1="150" y1="60" x2="150" y2="260" />
<line x1="250" y1="60" x2="250" y2="260" />
<line x1="350" y1="60" x2="350" y2="260" />
<line x1="450" y1="60" x2="450" y2="260" />
<line x1="550" y1="60" x2="550" y2="260" />
<line x1="650" y1="60" x2="650" y2="260" />
<line x1="100" y1="100" x2="700" y2="100" />
<line x1="100" y1="140" x2="700" y2="140" />
<line x1="100" y1="180" x2="700" y2="180" />
<line x1="100" y1="220" x2="700" y2="220" />
</g>

<line x1="100" y1="100" x2="700" y2="100" stroke="#1f6fd6" stroke-width="3" />
<text x="710" y="104" font-size="11" fill="#1f6fd6">t=T: known payoff</text>

<line x1="400" y1="105" x2="400" y2="215" stroke="#d6291f" stroke-width="2" marker-end="url(#arrow)" />
<text x="420" y="160" font-size="12" fill="#d6291f">Step backward to t=0</text>

<text x="400" y="255" text-anchor="middle" font-size="11" fill="#555">t=0: solve for V(S0,0)</text>

</svg>

### ODEs in Finance: Simpler Deterministic Settings

While PDEs dominate derivatives pricing, **ordinary differential equations** appear in several related deterministic contexts:

- **Bond pricing under deterministic short-rate models**: Certain interest rate models reduce to ODEs when the short rate itself is treated as deterministic or when solving for the deterministic component of affine term-structure models
- **Perpetual American options**: An American option with no expiration date (a perpetual option) removes the time dimension from the PDE, reducing the Black-Scholes PDE to an ODE in $S$ alone, which does admit a closed-form solution — a notable exception to the general free-boundary problem's lack of closed form
- **Deterministic volatility term structure calibration**: Certain simplified models for fitting a time-dependent (but not stochastic) volatility function to market data can be framed as ODE-based calibration problems

**Worked Example — Perpetual American Put ODE**: For a perpetual American put with no expiration, the Black-Scholes PDE's time-derivative term vanishes ($\partial V/\partial t = 0$ since the option's value cannot depend on calendar time when there is no expiration), reducing the PDE to the ODE:

$$\frac{1}{2}\sigma^2 S^2 V''(S) + rS V'(S) - rV(S) = 0$$

This is a second-order linear ODE (a Cauchy-Euler / Euler equation, recognizable by its $S^2 V''$ and $SV'$ structure) with a known closed-form solution involving a power-law exercise boundary $S^*$, one of the few American-option cases admitting an exact analytical solution rather than requiring numerical methods.

### Multi-Factor PDEs

When a derivative's value depends on more than one stochastic state variable — for example, in the **Heston stochastic volatility model**, where both the underlying price $S$ and its instantaneous variance $v$ are stochastic — the pricing PDE becomes a **two-dimensional (or higher) PDE**:

$$\frac{\partial V}{\partial t} + \frac{1}{2}vS^2\frac{\partial^2 V}{\partial S^2} + \rho\sigma_v vS \frac{\partial^2 V}{\partial S \partial v} + \frac{1}{2}\sigma_v^2 v \frac{\partial^2 V}{\partial v^2} + rS\frac{\partial V}{\partial S} + \kappa(\theta - v)\frac{\partial V}{\partial v} - rV = 0$$

**Key Points**:

- The **cross-partial term** $\frac{\partial^2 V}{\partial S \partial v}$ arises from the correlation $\rho$ between the underlying's Brownian motion and the variance process's Brownian motion — a structural feature entirely absent from the single-factor Black-Scholes PDE
- Multi-factor PDEs of this type are generally solved via specialized numerical techniques (alternating direction implicit methods, Fourier-transform-based semi-analytical methods exploiting the model's characteristic function) rather than the simple finite-difference grids sufficient for the single-factor case, and are covered in greater depth in the stochastic volatility modeling sections of this curriculum

### Worked Example — Verifying a Solution Satisfies the Black-Scholes PDE

**Claim**: $V(S,t) = S\Phi(d_1) - Ke^{-r(T-t)}\Phi(d_2)$ satisfies the Black-Scholes PDE.

**Verification approach**: Computing $\partial V/\partial t$, $\partial V/\partial S$, and $\partial^2 V/\partial S^2$ from the closed-form formula and substituting into $\frac{\partial V}{\partial t} + \frac{1}{2}\sigma^2 S^2\frac{\partial^2 V}{\partial S^2} + rS\frac{\partial V}{\partial S} - rV$ yields an expression that, after using the identity relating $\phi(d_1)$ (the standard normal density at $d_1$) and $\phi(d_2)$ — specifically $S\phi(d_1) = Ke^{-r(T-t)}\phi(d_2)$, which follows algebraically from the definitions of $d_1, d_2$ — reduces to exactly zero, confirming the formula solves the PDE.

**Key Points**: This verification exercise, standard in derivatives pricing coursework, is the direct proof that the closed-form Black-Scholes formula is not merely a convenient approximation but an exact analytical solution to the PDE derived from the no-arbitrage hedging argument, subject to the model's assumptions (constant volatility, no dividends, frictionless continuous trading, lognormal underlying dynamics).

### Common Pitfalls

- **Confusing the PDE's independent variables with the SDE's**: The Black-Scholes PDE is a deterministic equation in $(S,t)$ — there is no remaining randomness once the PDE is written down; the randomness has been fully absorbed into the hedging argument. A frequent point of confusion for those newer to the topic is expecting the PDE itself to contain a stochastic term.
- **Applying the European-option closed-form solution to American options**: Because American options solve a free-boundary variational inequality rather than the plain PDE with fixed terminal/boundary conditions, using the European Black-Scholes formula to price an American option (particularly a put, where early exercise can be optimal) can materially misprice the instrument, especially for deep ITM puts or dividend-paying underlyings with ITM calls.
- **Numerical instability from violating stability conditions**: Naively implementing an explicit finite-difference scheme without respecting the stability constraint between $\Delta t$ and $\Delta S$ is a common implementation error that produces oscillating or diverging numerical solutions rather than a genuine PDE-solving failure.
- **Assuming the drift $\mu$ belongs in the pricing PDE**: A frequent conceptual error is retaining the real-world expected return $\mu$ in numerical PDE implementations; the correct risk-neutral PDE uses $r$ throughout, precisely because $\mu$ was eliminated by the delta-hedging argument during derivation.

**Related Topics**:

- Stochastic calculus and Itô's lemma (prerequisite derivation tools)
- The Black-Scholes-Merton model: full derivation and assumptions
- Risk-neutral valuation and the fundamental theorem of asset pricing
- Finite difference methods in depth (explicit, implicit, Crank-Nicolson implementation)
- Binomial and trinomial trees as discrete PDE analogs
- American option pricing and early exercise theory
- Stochastic volatility models (Heston) and multi-factor PDEs
- Monte Carlo methods as an alternative to PDE-based pricing