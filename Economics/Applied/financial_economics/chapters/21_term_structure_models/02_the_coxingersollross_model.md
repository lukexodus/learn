## The Cox-Ingersoll-Ross Model

### Overview

The Cox-Ingersoll-Ross (CIR) model, introduced in 1985, is a mean-reverting short-rate model that guarantees non-negative interest rates by making volatility proportional to the square root of the rate level. It shares the Vasicek model's mean-reverting drift structure but replaces constant volatility with a state-dependent term, producing a non-central chi-squared rate distribution instead of a Gaussian one, while retaining full analytical tractability for bond and option pricing.

### Model Specification

Under the risk-neutral measure $Q$, the short rate follows:

$$dr_t = a(b - r_t)\, dt + \sigma\sqrt{r_t}\, dW_t^Q$$

where:

- $a > 0$: speed of mean reversion
- $b$: long-run mean level
- $\sigma$: volatility scaling parameter
- $\sqrt{r_t}$: level-dependent volatility (the "square-root" feature defining the model)

**Key Points**

- As $r_t \to 0$, the diffusion term $\sigma\sqrt{r_t} \to 0$, while the drift $a(b - 0) = ab > 0$ pushes the rate back upward — this mechanism is precisely what prevents $r_t$ from going negative
- The model is also known as the CIR process or, in other applications (e.g., stochastic volatility), the **square-root diffusion**
- This same process (with relabeled parameters) is the variance process in the Heston stochastic volatility model, making CIR dynamics doubly important in financial economics

### The Feller Condition

**Key Points**

- The process remains strictly positive for all $t$ (never touches zero) if and only if the **Feller condition** holds: $2ab \geq \sigma^2$
- If $2ab < \sigma^2$, the process can reach zero but is instantaneously reflected back into positive territory (zero is not absorbing) — the process remains non-negative but may touch zero
- This condition is a standard, well-documented mathematical property of the CIR SDE (not an approximation or rule of thumb) and is routinely checked when calibrating CIR-type models in both interest rate and stochastic volatility applications
- [Unverified] Empirically, some calibrated CIR/Heston parameter sets violate the Feller condition, particularly for equity variance processes; whether this causes practical pricing issues depends on the specific numerical method used and is a topic of ongoing discussion in the literature

### Transition Density: Non-Central Chi-Squared Distribution

Unlike Vasicek's Gaussian transitions, $r_t$ conditional on $r_s$ (for $s < t$) follows a **non-central chi-squared distribution**:

$$r_t \mid r_s \sim \frac{\sigma^2(1-e^{-a(t-s)})}{4a} \cdot \chi^2_d\left(\lambda\right)$$

where $d = \frac{4ab}{\sigma^2}$ (degrees of freedom) and $\lambda = \frac{4ae^{-a(t-s)}}{\sigma^2(1-e^{-a(t-s)})} r_s$ (non-centrality parameter).

**Key Points**

- Conditional mean: $E[r_t \mid r_s] = r_s e^{-a(t-s)} + b(1 - e^{-a(t-s)})$ — identical functional form to Vasicek's conditional mean
- Conditional variance: $\text{Var}[r_t \mid r_s] = r_s \frac{\sigma^2}{a}\left(e^{-a(t-s)} - e^{-2a(t-s)}\right) + b\frac{\sigma^2}{2a}\left(1-e^{-a(t-s)}\right)^2$ — notably, unlike Vasicek, the variance depends on the current level $r_s$, reflecting the level-dependent diffusion
- The degrees-of-freedom parameter $d = 4ab/\sigma^2$ directly connects to the Feller condition: $d \geq 2$ is equivalent to $2ab \geq \sigma^2$

### Zero-Coupon Bond Pricing

Via the Feynman-Kac formula, the bond price PDE is:

$$P_t + a(b-r)P_r + \tfrac{1}{2}\sigma^2 r P_{rr} - rP = 0, \quad P(T,T)=1$$

The affine ansatz $P(t,T) = A(t,T)e^{-B(t,T)r_t}$ yields closed-form solutions:

$$B(t,T) = \frac{2(e^{\gamma(T-t)}-1)}{(\gamma+a)(e^{\gamma(T-t)}-1) + 2\gamma}$$



$$A(t,T) = \left[\frac{2\gamma\, e^{(a+\gamma)(T-t)/2}}{(\gamma+a)(e^{\gamma(T-t)}-1)+2\gamma}\right]^{2ab/\sigma^2}$$

where $\gamma = \sqrt{a^2 + 2\sigma^2}$.

**Key Points**

- This is again an affine term structure model, but unlike Vasicek's linear ODE for $B(t,T)$, the level-dependent volatility term produces a genuinely nonlinear **Riccati ODE** for $B(t,T)$: $\frac{\partial B}{\partial t} = aB + \tfrac{1}{2}\sigma^2 B^2 - 1$
- The parameter $\gamma$ arises directly from solving this Riccati equation and has no counterpart in the Vasicek solution
- Despite the added mathematical complexity, the final formula remains fully closed-form — a major reason CIR remains popular for practical implementation

### Bond Option Pricing

CIR bond option prices are available in closed form using the non-central chi-squared cumulative distribution function $\chi^2(\cdot; d, \lambda)$:

$$C(t) = P(t,T)\, \chi^2\big(2r^*[\rho+\psi+B(T_0,T)]; \, d,\, \lambda_1\big) - KP(t,T_0)\, \chi^2\big(2r^*[\rho+\psi]; \, d,\, \lambda_2\big)$$

where $\rho, \psi, r^*$ are model-implied constants and $\lambda_1, \lambda_2$ are non-centrality parameters depending on $r_t$.

**Key Points**

- This is materially more complex to implement than Vasicek's Black-Scholes-style formula, requiring numerical evaluation of the non-central chi-squared CDF
- [Inference] This computational complexity is a commonly cited practical reason some practitioners prefer Vasicek/Hull-White for certain applications despite CIR's theoretical non-negativity advantage, though the actual preference depends on the specific product and desk's existing infrastructure

### Diagram: Feller Condition and Boundary Behavior

```mermaid
flowchart TD
    A[CIR process: dr = a*(b-r)dt + sigma*sqrt(r)*dW] --> B{Check Feller condition: 2ab vs sigma^2}
    B -->|2ab greater or equal sigma^2| C[Process never reaches zero]
    B -->|2ab less than sigma^2| D[Process can touch zero, reflects upward]
    C --> E[Strictly positive rates guaranteed]
    D --> E
    E --> F[Non-central chi-squared transition density]
    F --> G[Affine bond pricing via Riccati ODE for B of t,T]
    G --> H[Closed-form P of t,T = A * exp of minus B times rt]
```

### Diagram: Square-Root Diffusion Behavior Near Zero (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 260">
<text x="320" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a2e">Square-Root Diffusion Behavior Near Zero (svg_diagram)</text>
<line x1="50" y1="230" x2="600" y2="230" stroke="#333" stroke-width="1" />
<line x1="50" y1="30" x2="50" y2="230" stroke="#333" stroke-width="1" />
<text x="605" y="235" font-size="10" fill="#333">time</text>
<text x="30" y="25" font-size="10" fill="#333">rate</text>
<line x1="50" y1="220" x2="600" y2="220" stroke="#dc2626" stroke-width="1.5" stroke-dasharray="4,3" />
<text x="560" y="212" font-size="10" fill="#dc2626">r = 0 boundary</text>

<path d="M 50 100 C 100 140, 130 190, 150 215 C 165 226, 180 220, 200 195 C 230 155, 280 130, 350 140 S 480 150, 600 100" fill="none" stroke="`#4338ca`" stroke-width="2.5" />

<rect x="120" y="150" width="180" height="55" rx="6" fill="#eef2ff" stroke="#4338ca" opacity="0.9" />
<text x="130" y="168" font-size="10" fill="#1a1a2e">As r approaches 0:</text>
<text x="130" y="182" font-size="10" fill="#1a1a2e">diffusion sigma*sqrt(r) shrinks,</text>
<text x="130" y="196" font-size="10" fill="#1a1a2e">drift a*b remains positive - pulls up</text>
</svg>

### Simulation of CIR Processes

**Key Points**

- Naive Euler-Maruyama discretization can produce negative values for $r_t$ due to the discrete-time approximation, even though the true continuous-time process stays non-negative — a well-known numerical artifact, not a flaw in the model itself
- Standard remedies include: reflection ($|r_t|$), truncation ($\max(r_t, 0)$), full truncation schemes, or the exact simulation method (sampling directly from the non-central chi-squared distribution)
- The exact simulation approach avoids discretization bias entirely by using the known transition density, at the cost of requiring efficient non-central chi-squared random variate generation

**Output**

```python
import numpy as np
from scipy.stats import ncx2

def simulate_cir_exact(r0, a, b, sigma, T, n_steps, n_paths=1):
    dt = T / n_steps
    d = 4 * a * b / sigma**2  # degrees of freedom
    paths = np.zeros((n_paths, n_steps + 1))
    paths[:, 0] = r0
    for t in range(1, n_steps + 1):
        r_prev = paths[:, t-1]
        c = sigma**2 * (1 - np.exp(-a*dt)) / (4*a)
        nc = (4 * a * np.exp(-a*dt) / (sigma**2 * (1 - np.exp(-a*dt)))) * r_prev
        paths[:, t] = c * ncx2.rvs(d, nc)
    return paths
```

**Key Points**

- This code uses the exact non-central chi-squared transition law derived above, sidestepping discretization bias entirely
- [Unverified] Relative computational cost of exact simulation vs. discretized Euler schemes with truncation depends on the random number generation library and number of paths simulated; no universal ranking applies across all implementations

### Comparison with Vasicek Model

| Feature | CIR | Vasicek |
| --- | --- | --- |
| Volatility | $\sigma\sqrt{r_t}$ (level-dependent) | $\sigma$ (constant) |
| Non-negativity | Guaranteed if Feller condition holds | Not guaranteed (Gaussian, unbounded below) |
| Transition distribution | Non-central chi-squared | Normal (Gaussian) |
| Bond price ODE for $B(t,T)$ | Riccati (nonlinear) | Linear |
| Bond option pricing | Non-central chi-squared CDF | Black-Scholes-style closed form |
| Volatility term structure | Rate-dependent (higher rates → higher vol) | Flat (rate-independent) |

**Key Points**

- CIR's level-dependent volatility produces a more empirically realistic feature: interest rate volatility tends to rise with the level of rates, a pattern observed historically and captured naturally by the $\sqrt{r_t}$ term
- This same volatility-level relationship is why the CIR process was later adopted (relabeled) as the workhorse variance process in the Heston stochastic volatility model for equities

### Extensions

**Key Points**

- **CIR++ (shifted CIR)**: adds a deterministic shift function to allow exact fitting of the initial observed yield curve, analogous to how Hull-White extends Vasicek
- **Multi-factor CIR models**: sum of independent CIR processes to better capture yield curve shape dynamics while preserving non-negativity and analytical tractability (each factor retains its own non-central chi-squared marginal distribution)
- The CIR framework generalizes into the broader class of **affine jump-diffusions** when jump components are added to the square-root process (relevant for both interest rate and stochastic volatility applications with jumps, e.g., the Bates model's variance process)

### Common Pitfalls

**Key Points**

- Using naive Euler discretization without truncation/reflection and then observing (and being confused by) simulated negative rates — this is a numerical scheme artifact, not evidence against the model's non-negativity property
- Ignoring the Feller condition during calibration — parameter sets violating $2ab \geq \sigma^2$ are still valid (the process remains non-negative) but behave differently near the zero boundary, which can matter for products sensitive to low-rate scenarios
- Assuming CIR volatility is realistic across all economic regimes — level-dependent volatility fits historically observed patterns reasonably but is still a stylized single mechanism, and may not capture more complex volatility dynamics (e.g., volatility that rises during rate spikes in either direction)
- Confusing CIR's short-rate application with its stochastic-volatility application (Heston) — the mathematical process is identical, but interpretation, typical parameter magnitudes, and calibration targets differ substantially between the two contexts

### Conclusion

The CIR model addresses Vasicek's central theoretical weakness — the possibility of negative rates — by introducing a level-dependent (square-root) volatility term that vanishes as rates approach zero. This produces a non-central chi-squared transition law rather than a Gaussian one, at the cost of a more complex (though still closed-form) bond and option pricing framework requiring a nonlinear Riccati ODE and non-central chi-squared distribution functions. Its influence extends well beyond term structure modeling, forming the mathematical basis of the variance process in the Heston stochastic volatility model.

**Related Topics**

- The Vasicek model
- The Feynman-Kac formula
- Affine term structure models (Duffie-Kan framework)
- Heston stochastic volatility model
- Hull-White model and CIR++ extensions
- Multi-factor short-rate models
- Numerical schemes for square-root diffusions (Euler, Milstein, exact simulation)
- Riccati differential equations in finance