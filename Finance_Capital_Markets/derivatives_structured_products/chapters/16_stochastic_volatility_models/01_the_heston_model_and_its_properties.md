## The Heston Model and Its Properties


### Overview

The Heston model (Heston, 1993) is the most widely used stochastic volatility model in derivatives pricing, distinguished by having a **semi-closed-form (analytical) solution for European option prices** via its characteristic function — a rare and highly valuable property among stochastic volatility models, since it allows fast, near-instantaneous calibration to a full implied volatility surface without resorting to Monte Carlo or PDE methods for the calibration loop itself. This item covers the model's dynamics, the characteristic-function pricing machinery, its parameter interpretation, and its well-documented strengths and limitations relative to local and local-stochastic volatility alternatives.

### Model Dynamics

The Heston model specifies a two-factor system: the spot price and its instantaneous variance, each driven by a Brownian motion, with the two Brownian motions correlated:

$$dS_t = (r-q)S_t\,dt + \sqrt{v_t}\,S_t\,dW_t^S$$



$$dv_t = \kappa(\theta - v_t)\,dt + \xi\sqrt{v_t}\,dW_t^v$$



$$dW_t^S \, dW_t^v = \rho\,dt$$

**Parameters:**

- $v_t$: instantaneous variance (not volatility) — the state variable.
- $\kappa$: **mean-reversion speed** of variance toward its long-run level.
- $\theta$: **long-run (long-term) variance level** that $v_t$ reverts toward.
- $\xi$ (sometimes denoted $\sigma_v$): **volatility of variance** ("vol-of-vol") — governs how much $v_t$ itself fluctuates.
- $\rho$: **correlation** between spot returns and variance changes — in equity markets typically calibrated strongly negative, capturing the well-documented leverage effect / negative skew (falling spot associated with rising variance).
- $v_0$: initial variance (also a calibrated parameter, alongside $\kappa,\theta,\xi,\rho$).

The variance process $v_t$ is a **CIR (Cox-Ingersoll-Ross) process**, the same square-root mean-reverting diffusion used for short-rate modeling in the CIR interest rate model — this shared mathematical structure is why Heston's variance process inherits CIR's well-known properties (mean reversion, non-negativity under certain parameter conditions, and a known non-central chi-squared transition density).

### The Feller Condition

For the CIR-type variance process to remain **strictly positive almost surely** (i.e., never reach exactly zero), the parameters must satisfy the **Feller condition**:

$$2\kappa\theta \geq \xi^2$$

**Practical relevance:** many calibrated Heston parameter sets in practice — particularly those fit to equity index smiles with steep, persistent skew — **violate** the Feller condition (require large $\xi$ relative to $\kappa\theta$ to generate enough smile curvature), meaning the variance process can theoretically touch or briefly dip toward zero under the calibrated dynamics. This does not necessarily invalidate the model or its pricing formula (the characteristic function remains well-defined via analytic continuation even when Feller is violated, per the well-known "Heston trap" branch-cut handling discussed below), but it does mean the "long-run positivity" intuition breaks down in a strict sense, which is a well-documented practical wrinkle in Heston calibration. [Verified: the Feller condition and its frequent empirical violation in equity index calibration are widely documented in the stochastic volatility literature.]

### The Characteristic Function and Semi-Closed-Form Pricing

Heston's central practical contribution is an explicit formula for the characteristic function of $\ln S_T$ under the model, of the form:

$$\phi(u; S_0, v_0, T) = \exp\left(C(u,T) + D(u,T)v_0 + iu\ln S_0\right)$$

where $C(u,T)$ and $D(u,T)$ are explicit functions of the model parameters (involving complex exponentials and square roots of complex arguments) obtained by solving the associated Riccati ODEs that arise from the model's affine structure.

**European option pricing via Fourier inversion:** given $\phi(u;\cdot)$, European call/put prices are obtained via a Fourier-inversion integral (e.g., the Carr-Madan formula or the original Heston inversion formula), reducing the computation of a full option price to a **single one-dimensional numerical integral** rather than a full PDE solve or Monte Carlo simulation. This is the key practical advantage: calibrating Heston to a smile of, say, 50-100 quoted strikes/maturities requires evaluating this integral repeatedly inside an optimization loop, which is computationally fast relative to alternatives requiring full PDE/MC repricing at each optimization step.

**The "Heston trap":** the original formulation of $C(u,T)$ and $D(u,T)$ involves complex square roots and logarithms, which are **multi-valued functions** — naive implementation can pick the wrong branch of the complex logarithm as $u$ and $T$ vary, causing the characteristic function to be discontinuous and pricing to fail or produce garbage for certain parameter/strike/maturity combinations. This is a well-known numerical pitfall (documented extensively by Albrecher et al. and others) with a well-established fix: using an alternative, mathematically equivalent formulation of $C(u,T)$ that avoids the problematic branch-cut crossing, commonly referred to as **Gatheral's "little Heston trap" fix** or the "rotation count" / continuous branch-tracking approach. [Verified: the Heston trap and its standard remedies are well-documented, widely cited numerical implementation issues in the quantitative finance literature.]

### Smile/Skew Generated by Heston Parameters

Each parameter has a broadly interpretable effect on the resulting implied volatility smile:

| Parameter | Effect on Smile |
| --- | --- |
| $v_0$ | Sets overall ATM vol level for near-term maturities |
| $\theta$ | Sets the long-run ATM vol level that longer-dated maturities converge toward |
| $\kappa$ | Governs how quickly the ATM term structure moves from $v_0$ toward $\theta$ — higher $\kappa$ means faster convergence, flattening the term structure of ATM vol sooner |
| $\rho$ | Primary driver of **skew**: strongly negative $\rho$ produces the downward-sloping skew typical of equity index smiles (falling spot, rising vol) |
| $\xi$ | Primary driver of **smile curvature/convexity** (wings): higher vol-of-vol produces more pronounced curvature away from the money, on both sides |

This intuitive parameter-to-shape mapping (skew from correlation, curvature from vol-of-vol, level and term structure from the variance level/mean-reversion parameters) is one of Heston's most valued practical properties — it gives traders and calibration engineers an interpretable handle on the smile shape, unlike a purely non-parametric fit.

### Calibration Procedure

1. **Objective function:** minimize weighted squared error between Heston-implied vols (computed via the characteristic function + Fourier inversion, then implied-vol-inverted) and market-quoted implied vols across the surface — same general vega-weighted least-squares framework as parametric implied-vol-surface calibration (see "Volatility Surface Calibration Techniques"), but here the model directly generates *prices* rather than being a surface-shape parametrization.
2. **Non-convex optimization:** the five parameters $(v_0, \kappa, \theta, \xi, \rho)$ are typically fit via a numerical optimizer (Levenberg-Marquardt, differential evolution, or similar) since the mapping from parameters to smile is nonlinear and the objective surface can have multiple local minima.
3. **Parameter constraints:** bounds are typically imposed (e.g., $\kappa, \theta, \xi > 0$, $-1 \leq \rho \leq 1$) and sometimes the Feller condition is either enforced as a soft penalty or explicitly allowed to be violated depending on desk convention, given the frequent empirical need to violate it for realistic equity skew fits.
4. **Term structure fit quality trade-off:** because Heston has only five free parameters governing the *entire* surface (versus, e.g., an independent SVI slice per maturity with five parameters *each*), Heston generally cannot fit every maturity's smile as precisely as a flexible per-slice parametric fit — this parsimony is often treated as a feature (fewer parameters means more stable, more structurally meaningful dynamics) rather than purely a limitation, but it does mean Heston calibration typically shows somewhat higher residual repricing error on individual quotes than a dedicated SVI/SSVI fit would.

### Heston's Forward Smile and Dynamics Properties

Unlike local volatility, Heston has an **independent stochastic driver for variance**, which gives it materially different — and generally more realistic — forward smile behavior:

- Because $v_t$ evolves according to its own mean-reverting process, the model's forward-start smile does not suffer from the same mechanical "flattening" seen in local vol (see "Forward Volatility Dynamics Under Local Vol"); the forward skew under Heston is governed by $\rho$ and $\xi$ directly and persists in a manner closer to what is often empirically observed.
- This makes Heston (and stochastic volatility models generally) the more commonly preferred choice for genuinely forward-smile-sensitive payoffs (cliquets, forward-starting options) relative to pure local volatility, as discussed under "Applying Local Volatility to Exotic Pricing."
- However, Heston **does not exactly reprice every point of the current vanilla surface** the way local vol does by construction — the five-parameter fit is an approximation, so there is an inherent trade-off between Heston's more realistic dynamics and local vol's exact current-day calibration; this trade-off is precisely what motivates local-stochastic volatility (LSV) models that attempt to get both.

### Diagram: Heston Model Structure (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 400" font-family="sans-serif">
<text x="350" y="24" text-anchor="middle" font-size="16" font-weight="bold">Heston Two-Factor Structure (svg_diagram)</text>
<rect x="60" y="60" width="220" height="80" rx="8" fill="none" stroke="#2b6cb0" stroke-width="2" />
<text x="170" y="90" text-anchor="middle" font-size="12" font-weight="bold">Spot process</text>
<text x="170" y="110" text-anchor="middle" font-size="11">dS = (r-q)S dt + sqrt(v) S dW_S</text>
<text x="170" y="128" text-anchor="middle" font-size="10" fill="#4a5568">Driven by variance v_t</text>
<rect x="420" y="60" width="220" height="80" rx="8" fill="none" stroke="#2f855a" stroke-width="2" />
<text x="530" y="90" text-anchor="middle" font-size="12" font-weight="bold">Variance process (CIR)</text>
<text x="530" y="110" text-anchor="middle" font-size="11">dv = k(theta - v) dt + xi sqrt(v) dW_v</text>
<text x="530" y="128" text-anchor="middle" font-size="10" fill="#4a5568">Mean-reverting, own driver</text>
<path d="M 280 100 L 420 100" stroke="#c53030" stroke-width="2" stroke-dasharray="6,3" />
<text x="350" y="90" text-anchor="middle" font-size="11" fill="#c53030">Correlation rho</text>
<rect x="60" y="200" width="580" height="60" rx="6" fill="none" stroke="#4a5568" stroke-width="1.5" />
<text x="350" y="225" text-anchor="middle" font-size="12" font-weight="bold">Characteristic function phi(u) — closed form via Riccati ODEs</text>
<text x="350" y="245" text-anchor="middle" font-size="10">Enables Fourier-inversion pricing: single 1D integral per option</text>
<path d="M 350 140 L 350 200" stroke="black" stroke-width="1.5" marker-end="url(#arrow3)" />
<rect x="150" y="290" width="400" height="60" rx="6" fill="none" stroke="#2b6cb0" stroke-width="1.5" />
<text x="350" y="315" text-anchor="middle" font-size="12">Calibrate (v0, kappa, theta, xi, rho)</text>
<text x="350" y="333" text-anchor="middle" font-size="10">to match market implied vol surface via least squares</text>
<path d="M 350 260 L 350 290" stroke="black" stroke-width="1.5" marker-end="url(#arrow3)" />
</svg>

### Worked Example: Qualitative Parameter Sensitivity

Consider a Heston calibration to a 1-year equity index smile with illustrative parameters: $v_0 = 0.04$ (20% initial vol), $\kappa = 2.0$, $\theta = 0.04$, $\xi = 0.5$, $\rho = -0.7$.

- **ATM level:** $\sqrt{v_0} = 20\%$, consistent with a typical equity index ATM vol.
- **Term structure:** since $v_0 = \theta = 0.04$ here, the model implies a roughly **flat** ATM term structure (no pull toward a different long-run level) — if instead $\theta$ were set higher (say $0.06$), longer maturities would show progressively higher ATM implied vol as $v_t$ is expected to mean-revert upward.
- **Skew:** $\rho = -0.7$ (strongly negative) produces a pronounced downward-sloping skew, consistent with typical equity index behavior — puts trade at meaningfully higher implied vol than calls of equivalent distance from the money.
- **Curvature:** $\xi = 0.5$ (moderately high vol-of-vol) produces visible smile curvature in the wings beyond the linear skew component, consistent with typical equity index wing behavior at 1-year tenor.

[Inference: these are illustrative, qualitatively representative parameter values commonly seen in equity index Heston calibrations, not values drawn from a specific real calibrated market surface.]

### Extensions and Related Models

- **Heston with jumps (Bates model):** adds a jump-diffusion component to the spot process to better capture short-dated smile curvature that pure diffusive stochastic volatility struggles to match, since jumps generate smile convexity more efficiently than diffusive vol-of-vol at very short maturities.
- **Double Heston / multi-factor variance models:** use two CIR-type variance factors (fast and slow mean-reverting) to better fit both the short-end and long-end term structure of implied vol simultaneously, addressing a known limitation of single-factor Heston's term-structure flexibility.
- **Local-stochastic volatility (Heston-based LSV):** layering a local volatility component on top of a Heston-type stochastic base is one of the most common LSV constructions in practice, combining Heston's more realistic forward dynamics with an added local component recalibrated to restore exact current-day vanilla repricing.

### Key Points

- Heston models variance as a mean-reverting CIR-type process correlated with spot returns, giving it a genuine independent stochastic volatility driver unlike local vol.
- Its defining practical advantage is a semi-closed-form characteristic function enabling fast Fourier-inversion pricing, making calibration to a full smile computationally tractable via direct optimization rather than repeated PDE/MC repricing.
- Parameters have clear, interpretable effects on smile shape: $\rho$ drives skew, $\xi$ drives curvature, $(\kappa,\theta,v_0)$ drive the ATM level and term structure.
- The Feller condition ($2\kappa\theta \geq \xi^2$) is frequently violated in realistic equity-index calibrations, a well-documented practical wrinkle that doesn't invalidate the pricing formula but complicates strict interpretation of variance positivity.
- Heston generally cannot exactly reprice every vanilla quote the way local vol can (five parameters constrain the whole surface), but produces materially more realistic forward-smile dynamics — the central trade-off motivating local-stochastic volatility models that attempt to combine both properties.

**Related Topics**

- SABR Model Dynamics and Parameter Interpretation
- Local-Stochastic Volatility (LSV) Models and Particle Method Calibration
- Forward Volatility Dynamics Under Local Vol
- Strengths and Weaknesses of Local Volatility
- The Heston Trap and Characteristic Function Implementation Pitfalls
- Bates Model: Heston With Jump-Diffusion
- Fourier-Inversion Option Pricing Methods (Carr-Madan, COS Method)
- Volatility Surface Calibration Techniques