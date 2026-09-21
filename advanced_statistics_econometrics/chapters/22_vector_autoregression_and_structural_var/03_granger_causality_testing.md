## Granger Causality Testing

### Definition and Conceptual Foundation

Granger causality is a statistical concept of predictive precedence, not causality in the philosophical or structural sense. A time series $X$ is said to "Granger-cause" $Y$ if past values of $X$ contain information that helps predict $Y$ beyond what is contained in past values of $Y$ alone. The test evaluates whether lagged values of one variable improve the out-of-sample or in-sample forecast accuracy of another variable, conditional on the second variable's own history.

The concept originates from Clive Granger's 1969 formalization, built on the principle that a cause cannot occur after its effect and that a cause must contain unique information about the future values of its effect not available elsewhere. This is a probabilistic, forecast-based notion. It does not establish true causal mechanisms, and misinterpretation of "Granger causality" as structural causality is one of the most common errors in applied econometrics.

### Formal Setup in a VAR Framework

Consider a bivariate VAR($p$) system:

$$Y_t = \alpha_0 + \sum_{i=1}^{p}\alpha_i Y_{t-i} + \sum_{i=1}^{p}\beta_i X_{t-i} + \varepsilon_{1t}$$



$$X_t = \gamma_0 + \sum_{i=1}^{p}\gamma_i X_{t-i} + \sum_{i=1}^{p}\delta_i Y_{t-i} + \varepsilon_{2t}$$

$X$ fails to Granger-cause $Y$ if and only if all $\beta_i = 0$ for $i = 1, \dots, p$. Symmetrically, $Y$ fails to Granger-cause $X$ if all $\delta_i = 0$. The test is directional: $X \to Y$ and $Y \to X$ are tested separately, and both, one, or neither relationship may hold. When both directions are significant, this is termed **feedback** or bidirectional causality.

### Hypotheses

For testing whether $X$ Granger-causes $Y$:

$$H_0: \beta_1 = \beta_2 = \cdots = \beta_p = 0 \quad \text{(no Granger causality from } X \text{ to } Y\text{)}$$



$$H_1: \text{at least one } \beta_i \neq 0$$

### Test Statistic

The standard approach is an F-test (or Wald test) comparing a restricted model (excluding lags of $X$) against an unrestricted model (including them):

$$F = \frac{(RSS_r - RSS_u)/p}{RSS_u/(T - k)}$$

where $RSS_r$ is the residual sum of squares from the restricted regression, $RSS_u$ is the residual sum of squares from the unrestricted regression, $p$ is the number of restrictions (lags of $X$ excluded), $T$ is the sample size, and $k$ is the number of parameters in the unrestricted model. Under $H_0$, $F \sim F(p, T-k)$ asymptotically.

An asymptotically equivalent Wald $\chi^2$ test is also common, especially when the VAR is estimated jointly via least squares or maximum likelihood:

$$W = (R\hat{\theta})' \left[R \, \widehat{\text{Var}}(\hat{\theta}) \, R'\right]^{-1} (R\hat{\theta}) \sim \chi^2(p)$$

where $R$ is the restriction matrix isolating the coefficients on lagged $X$.

### Preconditions and Practical Workflow

**Key Points**

- **Stationarity**: Both series should be stationary (or the VAR should be specified in a form, such as differences or an error-correction representation, that ensures valid asymptotic inference). Testing Granger causality on non-stationary I(1) series in levels can produce spurious results.
- **Lag length selection**: Choose $p$ using information criteria (AIC, BIC/SC, HQIC) or sequential likelihood ratio tests before conducting the causality test, since results are often highly sensitive to lag order.
- **Cointegration consideration**: If $X$ and $Y$ are cointegrated, a standard VAR in differences omits the long-run relationship. A Vector Error Correction Model (VECM) should be used instead, and causality testing then also examines whether the error-correction term itself is significant, which captures long-run causality distinct from short-run (lagged difference) causality. This is the Engle-Granger/Granger representation theorem link: cointegrated series must exhibit Granger causality in at least one direction.
- **Residual diagnostics**: Verify no serial correlation, and reasonable homoskedasticity, in the estimated VAR, since the F/Wald test validity relies on well-specified residuals.
- **Structural breaks and omitted variables**: A third variable driving both $X$ and $Y$ can generate spurious Granger causality; the bivariate case is especially vulnerable to this. Multivariate Granger causality (adding conditioning variables to the VAR) mitigates but does not eliminate this risk.

### Worked Example

Suppose an analyst wants to test whether changes in the money supply (M) Granger-cause inflation ($\pi$), using quarterly data.

**Example**

Step 1: Test both series for stationarity (e.g., Augmented Dickey-Fuller). Suppose both $\Delta M_t$ and $\pi_t$ are stationary.

Step 2: Select lag order via AIC across a VAR(1) through VAR(8); suppose AIC selects $p = 4$.

Step 3: Estimate the unrestricted equation:

$$\pi_t = \alpha_0 + \sum_{i=1}^{4}\alpha_i \pi_{t-i} + \sum_{i=1}^{4}\beta_i \Delta M_{t-i} + \varepsilon_t$$

Step 4: Estimate the restricted equation (drop all $\Delta M_{t-i}$ terms):

$$\pi_t = \alpha_0 + \sum_{i=1}^{4}\alpha_i \pi_{t-i} + u_t$$

Step 5: Compute $F = \frac{(RSS_r - RSS_u)/4}{RSS_u/(T-9)}$. Suppose $F = 3.85$ with a $p$-value of $0.006$.

**Output**

Since $p < 0.05$, reject $H_0$: money supply growth Granger-causes inflation at the 5% level. This means lagged money supply growth has statistically significant predictive content for inflation, beyond inflation's own history — a forecasting statement, not proof that money creation structurally drives price changes.

The reverse test ($\pi \to \Delta M$, i.e., does inflation Granger-cause money supply) would be conducted symmetrically using the equation for $\Delta M_t$.

### Multivariate and Panel Extensions

**Multivariate Granger causality**: In a VAR with $n > 2$ variables, causality from $X$ to $Y$ is tested by restricting only the $X$-lag coefficients in the $Y$ equation while retaining all other variables. This is important because bivariate tests are prone to omitted-variable bias — a spurious causal link can appear if a third variable jointly drives both series.

**Toda-Yamamoto procedure**: Provides a method for testing Granger causality without needing to pre-test for cointegration order or difference the data, by over-fitting the VAR with additional lags equal to the maximum suspected order of integration ($d_{max}$) and applying a modified Wald test (MWALD) that restricts only the first $p$ (not $p + d_{max}$) coefficients. This sidesteps the non-standard asymptotic distributions that arise when testing restrictions on VARs in levels with unit roots.

**Panel Granger causality**: Extensions such as the Dumitrescu-Hurlin (2012) test allow for heterogeneous causal relationships across cross-sectional units in panel data, testing the null of no causality for **any** unit against the alternative that causality holds for **at least one** unit.

### Frequency-Domain and Nonlinear Variants

- **Geweke/Breitung-Candelon frequency-domain test**: Decomposes Granger causality by frequency band, useful when a relationship is causal only at business-cycle or seasonal frequencies rather than uniformly.
- **Nonlinear Granger causality**: Standard tests assume linear VAR structure. The Hiemstra-Jones test and related nonparametric approaches (based on correlation integrals) detect causality operating through nonlinear channels that a linear F-test would miss. [Inference: These nonlinear tests are less standardized in software implementation and results can be sensitive to bandwidth/embedding-dimension choices.]

### Common Pitfalls

- **Causality vs. Granger causality**: Significant results indicate predictive precedence, not a structural causal mechanism. A confound with its own lead-lag structure can generate Granger causality between two unrelated series.
- **Sample size and lag sensitivity**: Small samples relative to lag length reduce power; conversely, excessive lags waste degrees of freedom and can spuriously inflate or deflate significance.
- **Instantaneous causality**: Standard Granger tests only examine lagged relationships; strong contemporaneous correlation between $\varepsilon_{1t}$ and $\varepsilon_{2t}$ (instantaneous causality) is a separate phenomenon sometimes tested via a Sims-style approach or addressed through the covariance structure of the VAR.
- **Aggregation and time-interval bias**: The choice of sampling frequency (e.g., monthly vs. quarterly) can materially affect detected causal direction, since Granger causality is not time-scale invariant. [Inference: this effect is well-documented but the direction and magnitude are context-dependent.]

### Causal Flow Diagram

```mermaid
flowchart LR
    subgraph VAR System bivariate_var_system (svg_diagram)
    X["X_t series"] -->|"lags of X help predict Y?"| Y["Y_t series"]
    Y -->|"lags of Y help predict X?"| X
    end
    X -.->|"F-test on beta_i = 0"| TestXY["Test: X Granger-causes Y"]
    Y -.->|"F-test on delta_i = 0"| TestYX["Test: Y Granger-causes X"]
    TestXY --> Result1["Reject H0 => predictive precedence X to Y"]
    TestYX --> Result2["Reject H0 => predictive precedence Y to X"]
```

### Software Implementation Notes

- **R**: `lmtest::grangertest()`, `vars::causality()` (the latter also decomposes instantaneous causality).
- **Python**: `statsmodels.tsa.stattools.grangercausalitytests()`.
- **EViews/Stata**: Built-in VAR Granger causality/block exogeneity Wald tests (`vargranger` in Stata).

[Unverified: exact function argument names and default lag-selection behavior may differ across package versions; consult current package documentation before implementation.]

**Related Topics**

- Vector Error Correction Models (VECM) and long-run causality
- Cointegration testing (Engle-Granger, Johansen procedure)
- Impulse response functions and forecast error variance decomposition
- Structural VAR identification (Cholesky, sign restrictions)
- Toda-Yamamoto augmented VAR procedure
- Panel Granger causality (Dumitrescu-Hurlin test)
- Frequency-domain (Geweke/Breitung-Candelon) causality testing