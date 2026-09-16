## The Vasicek Model

### Overview

The Vasicek model, introduced by Oldřich Vašíček in 1977, is the first widely-used equilibrium short-rate model in fixed income. It models the instantaneous short rate as a mean-reverting Ornstein-Uhlenbeck process, providing closed-form solutions for zero-coupon bond prices and bond option prices. It remains foundational for understanding term structure modeling, even though its constant-volatility, single-factor structure limits its empirical realism.

### Model Specification

The short rate $r_t$ under the risk-neutral measure $Q$ follows:

$$dr_t = a(b - r_t)\, dt + \sigma\, dW_t^Q$$

where:

- $a > 0$: speed of mean reversion
- $b$: long-run mean level of the short rate
- $\sigma$: instantaneous volatility (constant)
- $W_t^Q$: standard Brownian motion under $Q$

**Key Points**

- The drift term $a(b - r_t)$ pulls $r_t$ toward $b$ whenever $r_t$ deviates from it — larger $a$ means faster reversion
- Volatility $\sigma$ is constant (not proportional to $r_t$), which is both a simplifying strength (analytical tractability) and a key weakness (allows negative rates, discussed below)
- This is the continuous-time analogue of an AR(1) process in discrete time — the Ornstein-Uhlenbeck process is the unique continuous-time, stationary, Gaussian Markov process with linear mean reversion

### Solving the SDE

**Example**

The Vasicek SDE is linear and can be solved explicitly. Applying an integrating factor $e^{at}$ to $d(e^{at}r_t)$:

$$d(e^{at}r_t) = ae^{at}r_t\,dt + e^{at}dr_t = e^{at}\left[a r_t \, dt + a(b-r_t)dt + \sigma dW_t\right] = abe^{at}dt + \sigma e^{at}dW_t$$

Integrating from $0$ to $t$:

$$r_t = r_0 e^{-at} + b(1 - e^{-at}) + \sigma \int_0^t e^{-a(t-s)}\, dW_s$$

**Key Points**

- $r_t$ is Gaussian (normally distributed) conditional on $r_0$, since it is a linear (Wiener) integral of deterministic functions against $dW_s$
- Conditional mean: $E[r_t \mid r_0] = r_0 e^{-at} + b(1-e^{-at})$ — an exponentially weighted average of the starting point and long-run mean
- Conditional variance: $\text{Var}[r_t \mid r_0] = \frac{\sigma^2}{2a}\left(1 - e^{-2at}\right)$ — this converges to a stationary variance $\frac{\sigma^2}{2a}$ as $t \to \infty$

### The Critical Drawback: Negative Interest Rates

**Key Points**

- Because $r_t$ is Gaussian, it has unbounded support on $(-\infty, \infty)$ — the model assigns strictly positive probability to negative interest rates at any finite future time
- Historically this was considered a major theoretical flaw (motivating the CIR model, which guarantees non-negativity)
- [Inference] Following the era of negative policy rates in Europe, Japan, and Switzerland (approximately 2014-2022), this "flaw" was reframed by many practitioners as a feature rather than a bug, since it allows the model to naturally accommodate negative-rate environments that non-negative models (CIR) cannot — though this is a practical reassessment rather than a change in the model's mathematical properties

### Zero-Coupon Bond Pricing Formula

Via the Feynman-Kac formula, the zero-coupon bond price $P(t,T)$ solves the PDE:

$$P_t + a(b-r)P_r + \tfrac{1}{2}\sigma^2 P_{rr} - rP = 0, \quad P(T,T) = 1$$

The Vasicek model's affine structure yields the closed-form solution:

$$P(t,T) = A(t,T)\, e^{-B(t,T)\, r_t}$$

with:

$$B(t,T) = \frac{1 - e^{-a(T-t)}}{a}$$



$$A(t,T) = \exp\left[\left(b - \frac{\sigma^2}{2a^2}\right)\big(B(t,T) - (T-t)\big) - \frac{\sigma^2}{4a}B(t,T)^2\right]$$

**Key Points**

- This is an **affine term structure model**: the log bond price is an affine (linear plus constant) function of the state variable $r_t$
- $B(t,T)$ has the interpretation of a duration-like sensitivity of the bond price to the current short rate
- The yield curve $y(t,T) = -\frac{\ln P(t,T)}{T-t}$ is fully determined once $a$, $b$, $\sigma$, and $r_t$ are specified — allowing the model to generate a full term structure from just four inputs

### Deriving the Closed-Form Solution

**Example**

Substitute the ansatz $P(t,r,T) = A(t,T)e^{-B(t,T)r}$ into the PDE. Matching coefficients of $r$ (since the PDE must hold for all $r$) yields two ordinary differential equations:

$$\frac{\partial B}{\partial t} = aB - 1, \quad B(T,T) = 0$$



$$\frac{\partial A}{\partial t} = A\left[abB - \tfrac{1}{2}\sigma^2 B^2\right], \quad A(T,T) = 1$$

Solving the Riccati-type ODE for $B$ (linear in this case since Vasicek's volatility is constant) gives $B(t,T) = \frac{1-e^{-a(T-t)}}{a}$; substituting back and integrating gives $A(t,T)$ as stated above.

**Key Points**

- This "guess an affine solution, derive ODEs" technique generalizes to the broader class of affine term structure models (Duffie-Kan framework), of which Vasicek and CIR are special cases
- The fact that the ODE for $B$ is linear (not Riccati/nonlinear) is specific to Vasicek's constant-volatility specification; CIR's $\sqrt{r_t}$ volatility term produces a genuinely nonlinear Riccati ODE

### Bond Option Pricing

Vasicek's Gaussian framework permits closed-form pricing of European options on zero-coupon bonds. For a call option with strike $K$, maturity $T_0$, on a bond maturing at $T$:

$$C(t) = P(t,T)\, N(h) - K\, P(t,T_0)\, N(h - \sigma_P)$$

where:

$$\sigma_P = \sigma\, B(T_0,T)\sqrt{\frac{1-e^{-2a(T_0-t)}}{2a}}, \quad h = \frac{1}{\sigma_P}\ln\left(\frac{P(t,T)}{P(t,T_0)K}\right) + \frac{\sigma_P}{2}$$

**Key Points**

- This formula has the same structure as Black-Scholes, with $\sigma_P$ playing the role of aggregated bond-price volatility over the option's life
- Because the underlying bond price is log-normally distributed under the appropriate forward measure (a consequence of $r_t$ being Gaussian), a Black-Scholes-style closed form is achievable — this tractability is a major practical advantage of the model
- This formula extends directly to pricing caps, floors, and European swaptions (with appropriate adjustments) within the single-factor Vasicek framework

### Estimation and Calibration

**Key Points**

- Parameters $(a, b, \sigma)$ can be estimated from historical short-rate time series using maximum likelihood (exploiting the known conditional Gaussian transition density) or method of moments (matching sample mean/variance/autocorrelation to model-implied values)
- Alternatively, risk-neutral parameters are calibrated to fit observed bond prices/yield curves and cap/swaption volatilities — this typically produces different parameter values than historical estimation, reflecting the term premium (market price of interest-rate risk)
- [Unverified] The choice of short-rate proxy (e.g., overnight rate, 3-month T-bill) for historical estimation can materially affect parameter estimates; there is no single universally agreed proxy, and results are generally sensitive to this choice

### Diagram: Mean Reversion Dynamics

```mermaid
flowchart TD
    A[Current short rate rt] --> B{rt vs long-run mean b}
    B -->|rt greater than b| C[Drift a*(b-rt) is negative: pulls rt downward]
    B -->|rt less than b| D[Drift a*(b-rt) is positive: pulls rt upward]
    B -->|rt equals b| E[Drift is zero: only diffusion moves rt]
    C --> F[Random shock sigma*dWt superimposed on drift]
    D --> F
    E --> F
    F --> G[Resulting rt: Gaussian distribution, mean-reverting to b]
    G --> H[Feed into Feynman-Kac PDE for bond price P of t,T]
    H --> I[Closed-form affine solution: P = A*exp(-B*rt)]
```

### Diagram: Vasicek Short-Rate Paths and Distribution (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 280">
<text x="320" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a2e">Vasicek Short-Rate Paths and Distribution (svg_diagram)</text>
<line x1="50" y1="240" x2="600" y2="240" stroke="#333" stroke-width="1" />
<line x1="50" y1="40" x2="50" y2="240" stroke="#333" stroke-width="1" />
<text x="605" y="245" font-size="10" fill="#333">time</text>
<text x="30" y="35" font-size="10" fill="#333">rate</text>
<line x1="50" y1="130" x2="600" y2="130" stroke="#15803d" stroke-width="1.5" stroke-dasharray="5,3" />
<text x="560" y="122" font-size="11" fill="#15803d">long-run mean b</text>

<path d="M 50 60 C 120 90, 180 110, 250 122 S 380 128, 450 130 S 550 130, 600 130" fill="none" stroke="`#4338ca`" stroke-width="2" />

<text x="90" y="55" font-size="10" fill="`#4338ca`">r0 high, reverts down</text>

<path d="M 50 220 C 120 190, 180 160, 250 140 S 380 132, 450 130 S 550 130, 600 130" fill="none" stroke="`#b45309`" stroke-width="2" />

<text x="90" y="228" font-size="10" fill="`#b45309`">r0 low, reverts up</text>

<ellipse cx="600" cy="130" rx="10" ry="55" fill="#dcfce7" opacity="0.6" stroke="#15803d" />
<text x="500" y="200" font-size="10" fill="#15803d">stationary Gaussian dist.</text>
<text x="500" y="213" font-size="10" fill="#15803d">variance = sigma^2/(2a)</text>
</svg>

### Multi-Factor Extensions

**Key Points**

- Single-factor Vasicek implies perfectly correlated movements across all points on the yield curve (all rates driven by one Brownian motion) — an unrealistic restriction empirically, since yield curve shapes (level, slope, curvature shifts) are not perfectly correlated in practice
- Two-factor and three-factor Vasicek-type models add additional mean-reverting factors (e.g., a long-term and short-term factor) to better fit observed yield curve dynamics and decorrelate movements at different maturities
- The **Hull-White model** extends single-factor Vasicek by allowing the mean-reversion level $b$ (and sometimes $a$) to be time-dependent, enabling exact fit to the initial observed term structure — addressing Vasicek's inability to match an arbitrary initial yield curve exactly

### Comparison with CIR Model

| Feature | Vasicek | CIR (Cox-Ingersoll-Ross) |
| --- | --- | --- |
| Volatility term | $\sigma$ (constant) | $\sigma\sqrt{r_t}$ (level-dependent) |
| Rate distribution | Gaussian (normal) | Non-central chi-squared |
| Can go negative? | Yes | No (if Feller condition $2ab \geq \sigma^2$ holds) |
| Bond price form | Affine, closed-form | Affine, closed-form |
| ODE for $B(t,T)$ | Linear | Riccati (nonlinear) |

**Key Points**

- Both models belong to the broader affine term structure model class and share the "guess affine ansatz, solve ODEs" solution technique
- The choice between them in practice often depends on whether negative rates are a modeling requirement (favoring Vasicek/Hull-White) or non-negativity is prioritized (favoring CIR), alongside calibration fit to the volatility smile of interest-rate derivatives

### Common Pitfalls

**Key Points**

- Treating the historically-estimated (physical-measure) parameters as directly usable for pricing — risk-neutral calibration to market instruments (bonds, caps, swaptions) is required for pricing applications, and the two parameter sets generally differ
- Assuming single-factor Vasicek can fit an arbitrary observed initial yield curve exactly — it generally cannot; the Hull-White extension (time-dependent $b$) is needed for exact initial-curve fitting
- Overlooking the negative-rate possibility when using the model in contexts (e.g., some regulatory or accounting applications) where strictly positive rates are mandated
- Confusing the physical-measure mean-reversion level with the risk-neutral one — these differ by the market price of risk when returns and pricing are analyzed jointly (see Girsanov's theorem)

### Conclusion

The Vasicek model is the foundational mean-reverting short-rate model in term structure theory, prized for its analytical tractability (closed-form bond and bond option prices via the affine structure) despite the theoretical drawback of permitting negative rates. It remains pedagogically central and practically relevant, especially post-2014 negative-rate environments, and serves as the direct ancestor of both the non-negative CIR model and the initial-curve-fitting Hull-White extension.

**Related Topics**

- The Feynman-Kac formula
- Cox-Ingersoll-Ross (CIR) model
- Hull-White model and initial term structure fitting
- Affine term structure models (Duffie-Kan framework)
- Multi-factor short-rate models
- Interest rate caps, floors, and swaptions pricing
- Girsanov's theorem and the market price of risk
- LIBOR/SOFR Market Models