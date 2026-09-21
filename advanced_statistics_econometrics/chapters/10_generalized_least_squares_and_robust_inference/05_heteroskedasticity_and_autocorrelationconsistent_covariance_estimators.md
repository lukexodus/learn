
### Overview: The Sandwich Estimator Framework

Heteroskedasticity- and Autocorrelation-Consistent (HAC) covariance estimators produce asymptotically valid standard errors for OLS coefficients when the true error covariance structure $\Omega$ is unknown, potentially featuring both non-constant variance and serial correlation. Unlike FGLS, HAC estimators do not attempt to model $\Omega$ and re-weight the data; instead, they leave $\hat{\beta}_{OLS}$ unchanged and correct only its estimated sampling variance.

All HAC (and HC) estimators share the **sandwich form**:

$$\hat{V}(\hat{\beta}) = (X'X)^{-1}\, \hat{S}\, (X'X)^{-1}$$

where $\hat{S}$ is a consistent estimator of the asymptotic covariance of the score $\frac{1}{\sqrt{n}}X'\varepsilon$, sometimes called the "meat" of the sandwich (with $(X'X)^{-1}$ forming the "bread" on each side). The estimators differ in how $\hat{S}$ is constructed.

### Building Block: The White (HC) Estimator

For heteroskedasticity alone (no autocorrelation), White's estimator sets:

$$\hat{S}_{HC0} = \frac{1}{n}\sum_{i=1}^n \hat{u}_i^2\, x_i x_i'$$

This is consistent for $\text{Var}(x_i \varepsilon_i)$ under heteroskedasticity of unknown form, requiring no assumption about the functional relationship between $\text{Var}(\varepsilon_i)$ and $x_i$. [Confirmed]

**Finite-sample corrections** to HC0 are widely used because HC0 tends to understate variance in small samples:

- **HC1**: multiplies by $n/(n-k)$, a degrees-of-freedom correction ($k$ = number of regressors).
- **HC2**: divides each squared residual by $(1-h_{ii})$, where $h_{ii}$ is the leverage (diagonal of the hat matrix), correcting for the fact that OLS residuals are smaller than true errors at high-leverage points.
- **HC3**: divides by $(1-h_{ii})^2$, a more aggressive correction, generally preferred for small samples or influential-observation concerns. [Confirmed]

### Extending to Autocorrelation: The Newey-West (HAC) Estimator

When errors may also be serially correlated, $\hat{S}$ must incorporate cross-products at non-zero lags:

$$\hat{S}_{HAC} = \hat{\Gamma}_0 + \sum_{k=1}^{L} w(k, L)\left(\hat{\Gamma}_k + \hat{\Gamma}_k'\right)$$



$$\hat{\Gamma}_k = \frac{1}{n}\sum_{t=k+1}^n \hat{u}_t \hat{u}_{t-k}\, x_t x_{t-k}'$$

where $w(k, L)$ is a **kernel weighting function** applied to the lag-$k$ autocovariance term, and $L$ is the bandwidth (truncation lag).

### Kernel Choices

Different kernels trade off bias, variance, and guaranteed positive semi-definiteness of $\hat{S}$:

| Kernel | Weight function $w(k, L)$ | Notes |
| --- | --- | --- |
| Truncated (rectangular) | $1$ for $k \leq L$, $0$ otherwise | Simple but not guaranteed PSD |
| Bartlett (Newey-West) | $1 - \frac{k}{L+1}$ | Guarantees PSD; linear decay; most widely used default [Confirmed] |
| Parzen | Piecewise cubic decay | Smoother decay than Bartlett |
| Quadratic Spectral (QS) | Smooth, non-truncated decay | Optimal in a mean-squared-error sense under certain conditions (Andrews, 1991); does not require a hard cutoff $L$ |

The **Bartlett kernel** (used in the classic Newey-West 1987 estimator) is the most common default in applied econometrics due to its simplicity and guaranteed positive semi-definiteness. [Confirmed]

### Bandwidth Selection

The truncation lag / bandwidth $L$ governs how many autocovariance terms are included:

- **Newey-West rule of thumb**: $L = \lfloor 4(n/100)^{2/9}\rfloor$
- **Andrews (1991) automatic bandwidth**: a data-driven procedure that selects $L$ (or the QS kernel's bandwidth parameter) to asymptotically minimize the mean squared error of $\hat{S}$, based on estimating the underlying autoregressive structure of the moment conditions.
- **Newey-West (1994) automatic selection**: an alternative data-dependent plug-in method.

Larger $L$ captures longer-range dependence but increases the variance of $\hat{S}$ (each $\hat{\Gamma}_k$ is estimated from fewer effective term-pairs as $k$ grows); smaller $L$ reduces variance but risks bias from omitted autocovariance terms. [Confirmed]

### Prewhitening

**Prewhitening** (Andrews and Monahan, 1992) is a technique to improve the finite-sample performance of HAC estimators:

1. Fit a low-order VAR (commonly VAR(1)) to the moment vector $x_t \hat{u}_t$.
2. Apply the HAC kernel estimator to the VAR residuals (which have much of the autocorrelation removed).
3. "Re-color" the resulting covariance estimate by inverting the VAR transformation.

Prewhitening can reduce bias in $\hat{S}$ at the cost of some additional estimation variance from fitting the VAR; its benefit is largest when the underlying series exhibits strong, low-order persistence. [Confirmed]

### Extending to Panel Data

Plain time-series HAC estimators assume a single time-ordered series and do not directly handle panel structures with correlation across cross-sectional units. Panel-appropriate variants include:

- **Cluster-robust standard errors** (clustering by entity): consistent under arbitrary within-cluster correlation (including serial correlation within each entity over time) and heteroskedasticity across clusters, provided the number of clusters is reasonably large.
- **Driscoll-Kraay standard errors**: extend HAC/Newey-West logic to panels with cross-sectional dependence, valid even as the cross-sectional dimension grows, by first averaging moment conditions across entities within each time period, then applying a Newey-West-style kernel over time.

### Worked Example: Comparing HC and HAC in Practice

**Python (statsmodels):**

```python
import statsmodels.api as sm

X = sm.add_constant(df[['x1', 'x2']])
y = df['y']
ols_fit = sm.OLS(y, X).fit()

# HC3 (heteroskedasticity only, small-sample robust)
hc3_fit = ols_fit.get_robustcov_results(cov_type='HC3')

# HAC (Newey-West, Bartlett kernel, lag = 4)
hac_fit = ols_fit.get_robustcov_results(cov_type='HAC', maxlags=4)

print(hc3_fit.summary())
print(hac_fit.summary())
```

**R (sandwich):**

```r
library(sandwich)
library(lmtest)

ols_model <- lm(y ~ x1 + x2, data = df)

# HC3
vcov_hc3 <- vcovHC(ols_model, type = "HC3")
coeftest(ols_model, vcov = vcov_hc3)

# HAC with Newey-West kernel and automatic bandwidth
vcov_hac <- vcovHAC(ols_model)
coeftest(ols_model, vcov = vcov_hac)

# Driscoll-Kraay for panel data (via plm)
library(plm)
panel_model <- plm(y ~ x1 + x2, data = df, index = c("entity", "time"), model = "within")
vcov_dk <- vcovSCC(panel_model, type = "HC3", maxlag = 4)
coeftest(panel_model, vcov = vcov_dk)
```

`sandwich::vcovHAC()` implements a general HAC framework where the kernel and bandwidth can be customized (e.g., via `kernHAC()` for Quadratic Spectral/Andrews-style automatic bandwidth selection), while `vcovSCC()` implements the Driscoll-Kraay panel-robust covariance matrix. [Confirmed]

### Comparison Table

| Estimator | Heteroskedasticity | Autocorrelation | Cross-sectional dependence | Typical use case |
| --- | --- | --- | --- | --- |
| HC0-HC3 | Yes | No | No | Cross-sectional data |
| Newey-West (HAC) | Yes | Yes (up to lag $L$) | No | Single time series |
| Cluster-robust | Yes | Yes (within cluster) | No | Panel data, few large clusters |
| Driscoll-Kraay | Yes | Yes | Yes | Panel data with common shocks / cross-sectional dependence |

### Diagram: HAC Estimator Family Tree

```mermaid
flowchart TD
    A[Sandwich estimator: (X'X)^-1 * S_hat * (X'X)^-1] --> B{What does S_hat model?}
    B -- Heteroskedasticity only --> C[White HC0]
    C --> D[HC1: df correction]
    C --> E[HC2: leverage correction]
    C --> F[HC3: squared leverage correction]
    B -- Heteroskedasticity + autocorrelation --> G[Newey-West HAC]
    G --> H[Bartlett kernel, lag L]
    G --> I[Quadratic Spectral kernel, Andrews bandwidth]
    G --> J[Optional: VAR prewhitening]
    B -- Panel: within-cluster correlation --> K[Cluster-robust SE]
    B -- Panel: cross-sectional dependence --> L[Driscoll-Kraay SE]
```

### Properties and Limitations

- **Consistency, not efficiency**: all HAC/HC estimators leave $\hat{\beta}_{OLS}$ unchanged; they only aim for consistent variance estimation, sacrificing the efficiency gains available from a correctly specified FGLS model. [Confirmed]
- **Asymptotic validity**: consistency of $\hat{S}$ requires $n \to \infty$ (and, for HAC, $L \to \infty$ at a controlled rate relative to $n$); finite-sample performance can be poor with small $n$, highly persistent series, or a bandwidth chosen too small or too large. [Confirmed]
- **Not a cure for misspecification**: these estimators correct inference for a given, correctly specified conditional mean model; they do not address omitted variables, endogeneity, or functional-form misspecification.
- **Sensitivity to bandwidth/kernel choice**: results (test statistics, confidence intervals) can shift meaningfully with the chosen $L$ or kernel, motivating sensitivity checks across reasonable bandwidth choices in applied work.

### Common Pitfalls

- **Using plain Newey-West on panel data** ignoring cross-sectional dependence, when Driscoll-Kraay or cluster-robust alternatives would be more appropriate.
- **Choosing HC3 by default for very large samples** where the added computational cost and conservatism are unnecessary; HC1 or even classical SEs may suffice with very large $n$ and no evidence of high-leverage points.
- **Failing to report or justify bandwidth $L$** in HAC applications, which affects reproducibility given the sensitivity of results to this choice.
- **Assuming HAC estimators fix small-sample bias** in $\hat{\beta}$ itself — they do not; they only address the covariance matrix of an already-computed OLS estimator.

### Related Topics

- Weighted Least Squares and Feasible GLS
- Newey-West standard errors (dedicated treatment)
- Cluster-robust inference in panel and grouped data
- Driscoll-Kraay standard errors for cross-sectionally dependent panels
- Bootstrap-based robust inference (wild cluster bootstrap)
- Generalized Method of Moments (GMM) variance estimation, which uses the same sandwich/HAC machinery