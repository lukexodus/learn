## The GARCH Model and Extensions


### Definition and Conceptual Foundation

The Generalized Autoregressive Conditional Heteroskedasticity (GARCH) model, introduced by Tim Bollerslev (1986), generalizes Engle's ARCH model by allowing the conditional variance to depend not only on past squared innovations but also on its own past values. This parsimony gain is analogous to how an ARMA model generalizes a pure AR model: GARCH can capture the same persistence patterns as a high-order ARCH(q) with far fewer parameters, making it the dominant workhorse specification in applied volatility modeling.

### The GARCH(p,q) Specification

$$\varepsilon_t = \sigma_t z_t, \quad z_t \overset{\text{i.i.d.}}{\sim} (0,1)$$



$$\sigma_t^2 = \omega + \sum_{i=1}^{q} \alpha_i \varepsilon_{t-i}^2 + \sum_{j=1}^{p} \beta_j \sigma_{t-j}^2$$

where $q$ is the ARCH order (lagged squared shocks) and $p$ is the GARCH order (lagged conditional variances). The $\alpha_i$ terms are often referred to as capturing the **short-run** reaction to news/shocks, while the $\beta_j$ terms capture the **persistence** of volatility.

**Key Points**

- **Non-negativity constraints**: $\omega > 0$, $\alpha_i \geq 0$, $\beta_j \geq 0$ for all $i, j$, ensuring $\sigma_t^2 > 0$ almost surely.
- **Covariance stationarity condition**: $\sum_{i=1}^{q}\alpha_i + \sum_{j=1}^{p}\beta_j < 1$, in which case the unconditional variance is:

$$\text{Var}(\varepsilon_t) = \frac{\omega}{1 - \sum \alpha_i - \sum \beta_j}$$

- An ARCH(q) model is the special case $p = 0$; GARCH(1,1) is by far the most widely used specification in applied work due to its strong empirical performance-to-parsimony ratio.

### The GARCH(1,1) Model in Detail

$$\sigma_t^2 = \omega + \alpha_1 \varepsilon_{t-1}^2 + \beta_1 \sigma_{t-1}^2$$

**Key Points**

- $\alpha_1$ measures the sensitivity of current variance to the most recent squared shock ("news impact" or "reactivity").
- $\beta_1$ measures the persistence of past conditional variance itself; empirically, $\hat{\beta}_1$ is typically large (often 0.85–0.95 for daily financial returns), reflecting the strong, slow-decaying persistence in volatility documented among the stylized facts.
- $\alpha_1 + \beta_1$ (sometimes called the **persistence parameter**) determines how quickly shocks to volatility decay: values close to 1 imply long-lasting volatility shocks (consistent with the long-memory-like stylized fact), while values well below 1 imply faster mean reversion toward the unconditional variance.
- By recursive substitution, GARCH(1,1) can be shown to be equivalent to an ARCH($\infty$) model with geometrically declining weights $\alpha_1 \beta_1^{k}$ on $\varepsilon_{t-1-k}^2$, illustrating precisely how GARCH achieves ARCH-like flexibility with only two parameters instead of many lag coefficients.

### Estimation via Maximum Likelihood

**Example**

Step 1: Specify the conditional mean (e.g., constant, or ARMA($r$,$s$) if returns show mean serial correlation) and the GARCH(p,q) variance equation.

Step 2: Choose the conditional distribution of $z_t$: Gaussian (baseline, often misspecified given fat tails), Student's-t (captures excess kurtosis), or generalized error distribution (GED, flexible tail thickness).

Step 3: Construct the conditional log-likelihood, recursively computing $\sigma_t^2$ starting from an initialization (commonly the sample unconditional variance) and iterating forward using the fitted parameters at each optimization step.

Step 4: Maximize the log-likelihood numerically subject to non-negativity and stationarity constraints.

Step 5: Validate the fit: check standardized residuals $\hat{z}_t = \hat{\varepsilon}_t/\hat{\sigma}_t$ for remaining ARCH-LM effects (should show no significant residual clustering if the model is well-specified), assess normality/tail-fit of $\hat{z}_t$ against the assumed distribution, and compare information criteria (AIC/BIC) across candidate $(p,q)$ orders and distributional assumptions.

**Output**

A representative fitted GARCH(1,1) on daily equity index returns might yield $\hat{\omega} = 0.0000015$, $\hat{\alpha}_1 = 0.08$, $\hat{\beta}_1 = 0.90$ (both highly significant), giving $\hat{\alpha}_1 + \hat{\beta}_1 = 0.98$, indicating high but not explosive persistence, and an implied unconditional daily volatility consistent with observed sample volatility. [Inference: illustrative figures only; actual estimates vary substantially by asset, sample period, and data frequency.]

### Key Extensions: Asymmetric Volatility Models

**GJR-GARCH** (Glosten, Jagannathan, and Runkle, 1993):

$$\sigma_t^2 = \omega + \sum_{i=1}^{q}(\alpha_i + \gamma_i I_{t-i})\varepsilon_{t-i}^2 + \sum_{j=1}^{p}\beta_j \sigma_{t-j}^2$$

where $I_{t-i} = 1$ if $\varepsilon_{t-i} < 0$ and $0$ otherwise. A positive, significant $\gamma_i$ indicates negative shocks increase volatility more than positive shocks of equal magnitude — directly capturing the leverage effect.

**EGARCH** (Exponential GARCH, Nelson, 1991):

$$\ln(\sigma_t^2) = \omega + \sum_{i=1}^{q}\left[\alpha_i z_{t-i} + \gamma_i(|z_{t-i}| - E|z_{t-i}|)\right] + \sum_{j=1}^{p}\beta_j \ln(\sigma_{t-j}^2)$$

**Key Points**

- Modeling $\ln(\sigma_t^2)$ rather than $\sigma_t^2$ directly guarantees positivity of the conditional variance **without** requiring non-negativity constraints on the parameters, a notable estimation convenience over standard GARCH/GJR-GARCH.
- The $\alpha_i z_{t-i}$ term allows the sign of the standardized shock (not just its magnitude) to affect log-variance asymmetrically, directly capturing the leverage effect; a negative $\alpha_i$ implies negative shocks increase volatility more than positive shocks of the same size.
- EGARCH's multiplicative (log) structure means shocks affect variance multiplicatively rather than additively, which some researchers view as a more natural representation of volatility dynamics, though it also complicates direct interpretation and some forms of forecast aggregation relative to standard GARCH.

**TGARCH / Threshold GARCH** (Zakoian, 1994): A related asymmetric specification modeling conditional standard deviation (rather than variance) with a threshold term, structurally similar in spirit to GJR-GARCH but formulated on $\sigma_t$ rather than $\sigma_t^2$.

### Key Extensions: Long Memory and Component Models

**IGARCH** (Integrated GARCH): The special case $\alpha_1 + \beta_1 = 1$ exactly, implying shocks to volatility never decay (infinite persistence, analogous to a unit root in the variance equation). The unconditional variance is undefined under IGARCH. [Inference: whether apparent IGARCH-like estimates reflect true unit-root behavior in variance or are an artifact of structural breaks/regime shifts in the estimation sample is debated in the literature.]

**FIGARCH** (Fractionally Integrated GARCH, Baillie, Bollerslev, and Mikkelsen, 1996): Introduces a fractional differencing parameter $d \in (0,1)$ on the variance equation, allowing hyperbolic (slower than exponential, faster than a unit root) decay of shock persistence — directly targeting the long-memory-like slow ACF decay documented among the stylized facts, while avoiding the empirically implausible infinite-persistence implication of IGARCH.

**Component GARCH** (Engle and Lee, 1999): Decomposes conditional variance into a slowly-varying long-run (permanent) component and a transitory (short-run) component that reverts to the long-run component, providing an alternative parametric route to capturing both short-term reactivity and long-term persistent trends in volatility.

### Key Extensions: Distributional and Multivariate

**GARCH-M (GARCH-in-Mean)** (Engle, Lilien, and Robins, 1987): Allows the conditional variance (or standard deviation) to enter the conditional *mean* equation directly, formalizing a time-varying risk premium: $r_t = \mu + \lambda \sigma_t^2 + \varepsilon_t$ (or with $\sigma_t$), testing whether investors demand higher expected returns during higher-volatility periods.

**Multivariate GARCH (MGARCH)**: Extends the univariate framework to model time-varying covariances/correlations across multiple series simultaneously. Key specifications include:

- **BEKK** (Baba, Engle, Kraft, and Kroner): Guarantees positive semi-definiteness of the covariance matrix by construction but suffers from parameter proliferation as the number of series grows.
- **DCC (Dynamic Conditional Correlation)**, (Engle, 2002): Separates the estimation of univariate GARCH variances from a parsimonious dynamic correlation structure, substantially improving scalability to larger systems and becoming the most widely used MGARCH approach in applied work.

### Comparative Summary of GARCH-Family Models

| Model | Key feature | Addresses |
| --- | --- | --- |
| ARCH(q) | Variance depends on past squared shocks | Basic volatility clustering |
| GARCH(p,q) | Adds lagged variance terms | Parsimonious persistence |
| GJR-GARCH | Threshold indicator on negative shocks | Leverage effect (variance form) |
| EGARCH | Log-variance, asymmetric response | Leverage effect, no positivity constraint |
| IGARCH | Persistence parameter exactly 1 | Apparent infinite persistence |
| FIGARCH | Fractional differencing parameter $d$ | Long memory without infinite persistence |
| Component GARCH | Permanent + transitory variance components | Long-run/short-run decomposition |
| GARCH-M | Variance enters conditional mean | Time-varying risk premium |
| DCC-MGARCH | Dynamic correlation across series | Multivariate time-varying covariance |

### Model Selection and Diagnostics

**Key Points**

- Compare candidate specifications via AIC/BIC, but also examine economically motivated diagnostics: sign-bias and size-bias tests (Engle and Ng, 1993) specifically test for remaining asymmetric effects not captured by a symmetric GARCH, providing formal justification for moving to GJR-GARCH/EGARCH.
- News impact curves (plotting $\sigma_t^2$ as a function of $\varepsilon_{t-1}$ holding other terms fixed) visually reveal asymmetry: symmetric GARCH produces a symmetric parabola centered at zero, while GJR-GARCH/EGARCH produce a curve that is steeper on the negative side.
- Out-of-sample forecast evaluation (e.g., comparing forecasted $\hat{\sigma}_t^2$ against realized volatility proxies from high-frequency data) is standard practice for validating model choice beyond in-sample fit statistics.

### Common Pitfalls

- **Defaulting to Gaussian conditional errors**: Given persistent excess kurtosis in standardized residuals, a Student's-t or GED distribution is frequently a better default starting assumption for financial return data.
- **Ignoring asymmetry when it is empirically present**: Fitting symmetric GARCH(1,1) to equity index data, where the leverage effect is typically strong, can materially bias volatility forecasts around large negative-return episodes.
- **Over-parameterizing higher-order GARCH(p,q)**: In practice, GARCH(1,1) or low-order asymmetric variants typically outperform higher-order specifications for most financial return series; higher orders often add complexity without material fit improvement.
- **Confusing IGARCH persistence with true non-stationarity**: An estimated $\hat{\alpha}_1+\hat{\beta}_1$ close to or at 1 may reflect structural breaks in the volatility level during the sample rather than genuine unit-root variance behavior.
- **Treating in-sample fit as sufficient validation**: Strong in-sample likelihood does not guarantee good out-of-sample volatility forecasting performance; out-of-sample backtesting against realized volatility is essential, particularly for risk management applications.

### GARCH Family Structure Diagram

```mermaid
flowchart TD
    subgraph garch_family_tree GARCH Model Family Extensions (svg_diagram)
    A["ARCH(q): variance depends on past squared shocks only"] --> B["GARCH(p,q): add lagged variance terms for parsimony"]
    B --> C{"Asymmetric response needed?"}
    C -->|"Yes, variance form"| D["GJR-GARCH: threshold indicator on negative shocks"]
    C -->|"Yes, log-variance form"| E["EGARCH: asymmetric log-variance, no positivity constraint"]
    B --> F{"Persistence near unit root?"}
    F -->|"Exactly 1"| G["IGARCH: infinite persistence"]
    F -->|"Fractional, less than 1"| H["FIGARCH: hyperbolic decay, long memory"]
    B --> I["Component GARCH: permanent plus transitory decomposition"]
    B --> J["GARCH-M: variance enters conditional mean equation"]
    B --> K["Multivariate extension"]
    K --> L["BEKK: guaranteed PSD covariance, parameter-heavy"]
    K --> M["DCC: separate univariate GARCH plus dynamic correlation"]
    end
```

### Software Implementation Notes

- **R**: `rugarch` package (comprehensive: sGARCH, eGARCH, gjrGARCH, fiGARCH, csGARCH component model, multiple conditional distributions via `distribution.model`), `rmgarch` for DCC/BEKK multivariate extensions.
- **Python**: `arch` package (`arch_model()` with `vol='GARCH'`, `'EGARCH'`, `'FIGARCH'`; asymmetric terms via `o` parameter for GJR-type specifications).
- **EViews/Stata**: Both provide native GARCH-family estimation with GUI/command options for standard extensions (Stata's `arch` command supports GARCH, EGARCH-type variants via options; EViews supports a wide range of GARCH-family equation specifications directly).

[Unverified: exact parameterization conventions (e.g., EGARCH functional form details, FIGARCH truncation lag defaults) vary meaningfully across software packages and versions; verify the specific parameterization against current documentation before interpreting coefficients.]

**Related Topics**

- The ARCH model
- Stylized facts of financial time series
- Multivariate GARCH and dynamic conditional correlation (DCC)
- Realized volatility and high-frequency volatility measures
- Value-at-Risk and Expected Shortfall estimation
- News impact curves and asymmetry diagnostics (Engle-Ng tests)
- Long memory and fractional integration in volatility