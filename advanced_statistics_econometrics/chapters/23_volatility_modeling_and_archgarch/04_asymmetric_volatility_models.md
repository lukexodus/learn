## Asymmetric Volatility Models


### Conceptual Foundation

Asymmetric volatility models extend the basic GARCH framework to allow the conditional variance to respond differently to positive versus negative return shocks of equal magnitude. Standard GARCH(p,q) enters shocks only through their squared value ($\varepsilon_{t-i}^2$), which is mathematically blind to sign — a $-2\%$ return and a $+2\%$ return produce an identical variance impact. This symmetry contradicts the empirically well-documented **leverage effect** stylized fact: negative returns tend to be followed by larger increases in volatility than positive returns of the same size. Asymmetric volatility models were developed specifically to close this gap between model assumptions and empirical regularity.

### Economic Motivation

**Key Points**

- **Financial leverage hypothesis** (Black, 1976; Christie, 1982): A stock price decline mechanically increases a firm's debt-to-equity ratio (assuming debt levels are relatively fixed in the short run), raising the financial risk borne by equity holders and thus increasing the volatility of equity returns going forward.
- **Volatility feedback / time-varying risk premium hypothesis** (Pindyck, 1984; French, Schwert, and Stambaugh, 1987; Campbell and Hentschel, 1992): Anticipated increases in future volatility raise the required risk premium, which lowers the current price (a negative return) even before any fundamental shock occurs — implying causality can run from anticipated volatility to returns, not only from past returns to volatility, and that the observed asymmetry may be larger than the pure leverage mechanism alone would predict.
- [Inference: empirical work has generally found the magnitude of the leverage effect is often larger than what financial-leverage mechanics alone would imply, suggesting the volatility feedback channel or other risk-related mechanisms contribute meaningfully, though the relative decomposition between these explanations remains debated in the literature.]

### GJR-GARCH (Glosten-Jagannathan-Runkle)

$$\sigma_t^2 = \omega + \sum_{i=1}^{q}(\alpha_i + \gamma_i I_{t-i})\varepsilon_{t-i}^2 + \sum_{j=1}^{p}\beta_j \sigma_{t-j}^2$$

where $I_{t-i} = 1$ if $\varepsilon_{t-i} < 0$ and $I_{t-i} = 0$ otherwise.

**Key Points**

- For a negative shock, the effective ARCH coefficient is $(\alpha_i + \gamma_i)$; for a positive shock, it is just $\alpha_i$. A positive, statistically significant $\gamma_i$ confirms the leverage effect: negative shocks increase variance more than positive shocks of the same magnitude.
- Non-negativity constraints require $\omega > 0$, $\alpha_i \geq 0$, and $\alpha_i + \gamma_i \geq 0$ (rather than requiring $\gamma_i \geq 0$ itself, since the constraint applies to the effective coefficient on negative shocks).
- The stationarity condition adjusts to account for the asymmetry term, typically involving $\sum \alpha_i + \frac{1}{2}\sum\gamma_i + \sum\beta_j < 1$ under the assumption of a symmetric conditional distribution for $z_t$ (since $I_{t-i}=1$ roughly half the time under symmetry).
- GJR-GARCH(1,1) is the most commonly estimated asymmetric specification in applied work, directly comparable in parameter count (just one additional term, $\gamma_1$) to standard GARCH(1,1).

### EGARCH (Exponential GARCH)

$$\ln(\sigma_t^2) = \omega + \sum_{i=1}^{q}\left[\alpha_i z_{t-i} + \gamma_i\big(|z_{t-i}| - E|z_{t-i}|\big)\right] + \sum_{j=1}^{p}\beta_j \ln(\sigma_{t-j}^2)$$

where $z_{t-i} = \varepsilon_{t-i}/\sigma_{t-i}$ is the standardized shock.

**Key Points**

- Modeling the **log** of conditional variance guarantees $\sigma_t^2 > 0$ for *any* real-valued parameters, eliminating the need for explicit non-negativity constraints that complicate estimation in standard GARCH/GJR-GARCH — a significant practical estimation advantage.
- The term $\alpha_i z_{t-i}$ captures the **sign effect**: a negative $\hat{\alpha}_i$ means negative standardized shocks ($z_{t-i}<0$) push log-variance up (since $\alpha_i z_{t-i}$ becomes positive when both are negative), while positive shocks push it down, directly encoding the leverage effect asymmetry.
- The term $\gamma_i(|z_{t-i}| - E|z_{t-i}|)$ captures the **magnitude effect** (analogous to the standard ARCH/GARCH reactivity to shock size), centered so that its expectation is zero under the assumed distribution of $z_t$.
- Because the specification is multiplicative in the original variance (additive in log-variance), shocks affect $\sigma_t^2$ multiplicatively rather than additively — some researchers view this as a more natural representation of volatility dynamics, though it also complicates certain forms of multi-step-ahead forecast aggregation relative to standard GARCH, since $E[\sigma_{t+h}^2]$ does not have as simple a closed form under EGARCH.

### TGARCH (Threshold GARCH, Zakoian 1994)

$$\sigma_t = \omega + \sum_{i=1}^{q}\left(\alpha_i^{+} \varepsilon_{t-i}^{+} - \alpha_i^{-}\varepsilon_{t-i}^{-}\right) + \sum_{j=1}^{p}\beta_j \sigma_{t-j}$$

where $\varepsilon_{t-i}^{+} = \max(\varepsilon_{t-i}, 0)$ and $\varepsilon_{t-i}^{-} = \min(\varepsilon_{t-i}, 0)$.

**Key Points**

- TGARCH models the conditional **standard deviation** $\sigma_t$ directly (rather than variance $\sigma_t^2$ as in GJR-GARCH), with separate coefficients for the positive and negative parts of the shock, structurally similar in spirit to GJR-GARCH but on a different scale.
- Sometimes the terms "TGARCH" and "GJR-GARCH" are used loosely/interchangeably in applied literature and software despite the technical distinction between variance-scale and standard-deviation-scale formulations; users should verify which functional form a given software package actually implements. [Unverified: naming conventions vary by source and software package; always confirm the exact functional form used before interpreting coefficients.]

### APARCH (Asymmetric Power ARCH, Ding, Granger, and Engle, 1993)

$$\sigma_t^{\delta} = \omega + \sum_{i=1}^{q}\alpha_i\big(|\varepsilon_{t-i}| - \gamma_i \varepsilon_{t-i}\big)^{\delta} + \sum_{j=1}^{p}\beta_j \sigma_{t-j}^{\delta}$$

**Key Points**

- APARCH generalizes several asymmetric models within a single flexible framework: it nests standard GARCH ($\delta=2$, $\gamma_i=0$), GJR-GARCH-like behavior, TGARCH ($\delta=1$), and other power transformations as special cases, with the power parameter $\delta$ estimated from the data rather than fixed a priori.
- The parameter $\gamma_i \in (-1,1)$ controls the degree of asymmetry, and $\delta$ controls the power transformation applied to the conditional standard deviation, offering additional flexibility to match the specific tail and asymmetry behavior of a given return series at the cost of additional estimated parameters.

### News Impact Curve Comparison

The **news impact curve** (Engle and Ng, 1993) plots $\sigma_t^2$ as a function of $\varepsilon_{t-1}$, holding all other conditioning information (e.g., $\sigma_{t-1}^2$) fixed at its unconditional value, providing a visual and intuitive comparison of how different models translate a shock into a variance response.

**Key Points**

- **Standard GARCH**: produces a symmetric parabola centered at $\varepsilon_{t-1}=0$ — identical variance response to $+x$ and $-x$ shocks.
- **GJR-GARCH**: produces a parabola with two different slopes on either side of zero — steeper (more responsive) on the negative side when $\gamma_i > 0$, with a kink at zero.
- **EGARCH**: produces a smooth, non-parabolic curve, typically steeper and asymmetric around zero, reflecting the exponential/multiplicative functional form; unlike GJR-GARCH's kinked shape, EGARCH's curve transitions smoothly.

### Practical Estimation and Comparison Workflow

**Example**

Step 1: Fit a baseline symmetric GARCH(1,1) to the return series and obtain standardized residuals $\hat{z}_t$.

Step 2: Conduct the **Engle-Ng sign-bias, negative-size-bias, and positive-size-bias tests** by regressing $\hat{z}_t^2$ on an indicator for negative lagged shocks, the negative shock magnitude interacted with the indicator, and the positive shock magnitude interacted with the complementary indicator; significance of these coefficients indicates the symmetric GARCH is misspecified and asymmetric effects are present.

Step 3: If asymmetry is detected, re-estimate using GJR-GARCH and/or EGARCH specifications, comparing AIC/BIC and log-likelihood against the symmetric baseline.

Step 4: Construct and visually compare news impact curves across the fitted symmetric and asymmetric models to characterize the magnitude and shape of the detected asymmetry.

Step 5: Validate via out-of-sample forecast evaluation (comparing forecasted conditional variance against realized volatility proxies), since in-sample likelihood improvements do not guarantee superior forecasting performance.

**Output**

For a typical equity index, an Engle-Ng test often rejects the null of no sign bias at conventional significance levels, and a subsequently fitted GJR-GARCH(1,1) commonly yields a statistically significant $\hat{\gamma}_1 > 0$ (e.g., in the range of roughly 0.05–0.15, alongside a smaller $\hat{\alpha}_1$ than in the corresponding symmetric GARCH fit, since some of the shock-reactivity is now captured by the asymmetric term) with an improved log-likelihood and lower AIC/BIC relative to symmetric GARCH(1,1). [Inference: precise coefficient magnitudes and the degree of fit improvement vary substantially by asset and sample; the figures above are illustrative orders of magnitude commonly reported in the empirical literature, not from a specific dataset.]

### Comparative Summary Table

| Model | Variance/SD form | Positivity guaranteed without constraints | Asymmetry mechanism |
| --- | --- | --- | --- |
| GARCH | Variance ($\sigma_t^2$) | No (requires non-negativity constraints) | None (symmetric) |
| GJR-GARCH | Variance ($\sigma_t^2$) | No | Threshold indicator on negative shocks |
| EGARCH | Log-variance ($\ln\sigma_t^2$) | Yes | Sign term in log-variance equation |
| TGARCH | Std. deviation ($\sigma_t$) | No | Separate positive/negative shock coefficients |
| APARCH | Power-transformed SD ($\sigma_t^\delta$) | No | Flexible asymmetry parameter $\gamma_i$, nests other models |

### Common Pitfalls

- **Assuming asymmetry is always present and material**: While common in broad equity indices, the strength of the leverage effect varies by asset class (often weaker or differently signed in some commodities or exchange rates), and formal testing (Engle-Ng) should precede specification choice rather than assuming asymmetric models are always superior.
- **Confusing GJR-GARCH and TGARCH functional forms**: Since naming conventions are inconsistent across software and literature, misreading which scale (variance vs. standard deviation) a fitted "threshold GARCH" model operates on can lead to misinterpreted coefficients.
- **Over-parameterizing with APARCH when simpler models suffice**: The added flexibility of estimating $\delta$ and $\gamma_i$ jointly can lead to convergence difficulties or overfitting in shorter samples; a simpler GJR-GARCH or EGARCH is often preferred unless the extra flexibility demonstrably improves out-of-sample performance.
- **Multi-step forecasting complications under EGARCH**: The log-variance formulation does not admit as simple a closed-form multi-step-ahead forecast as standard GARCH; naive approaches can introduce bias, and simulation-based forecasting is often used in practice for EGARCH.

### News Impact Curve Shape Diagram

```mermaid
flowchart TD
    subgraph asymmetric_models_comparison Asymmetric Volatility Models Comparison (svg_diagram)
    A["Lagged shock epsilon_t-1"] --> B{"Model type"}
    B -->|"Symmetric GARCH"| C["Symmetric parabola centered at zero"]
    B -->|"GJR-GARCH"| D["Kinked parabola: steeper slope for negative epsilon_t-1"]
    B -->|"EGARCH"| E["Smooth asymmetric curve via log-variance sign term"]
    B -->|"APARCH"| F["Flexible power-transformed asymmetric curve"]
    C --> G["Equal variance response to plus x and minus x shocks"]
    D --> H["Higher variance response to negative shocks when gamma greater than 0"]
    E --> H
    F --> H
    end
```

### Software Implementation Notes

- **R**: `rugarch::ugarchspec()` with `model="gjrGARCH"`, `"eGARCH"`, `"apARCH"`, `"fGARCH"` (submodel `"TGARCH"`) options in the `variance.model` argument; built-in Engle-Ng-type sign-bias diagnostics available via `signbias()`.
- **Python**: `arch` package, `arch_model(returns, vol='GARCH', o=1)` specifies the asymmetric (GJR-type) term via the `o` order parameter; EGARCH available via `vol='EGARCH'`.
- **EViews/Stata**: Both support GJR-type and EGARCH specifications natively within their GARCH estimation modules/commands.

[Unverified: exact parameterization details (sign conventions, constraint handling, forecast methodology for EGARCH) vary across packages and versions; verify against current documentation before interpreting output.]

**Related Topics**

- The GARCH model and extensions
- Stylized facts of financial time series
- Engle-Ng sign-bias and size-bias tests
- News impact curves
- FIGARCH and long-memory volatility models
- Multivariate GARCH and dynamic conditional correlation
- Value-at-Risk estimation with asymmetric volatility models