## Stylized Facts of Financial Time Series


### Conceptual Foundation

Stylized facts of financial time series are a set of empirical regularities observed with remarkable consistency across asset classes (equities, exchange rates, commodities, fixed income), time periods, and markets, despite the wide diversity of underlying assets and institutional settings. These regularities motivate the specification of volatility models such as ARCH/GARCH, since standard linear Gaussian time series models (e.g., a simple ARMA with i.i.d. Gaussian errors) fail to reproduce them. The term was popularized in econometrics through the work of Rama Cont (2001), who catalogued these facts systematically.

### Return Definition Convention

Most stylized facts are documented for **returns** rather than price levels, since price levels are typically non-stationary (unit-root or near-unit-root processes). The standard convention is log returns:

$$r_t = \ln(P_t) - \ln(P_{t-1}) = \ln\left(\frac{P_t}{P_{t-1}}\right)$$

which approximates the simple percentage return for small changes and has the convenient property of being time-additive over multiple periods.

### Fact 1: Absence of Autocorrelation in Returns

**Key Points**

- Raw returns $r_t$ exhibit little to no linear autocorrelation beyond very short horizons (typically a few minutes to a day at most for liquid markets), consistent with the weak-form efficient markets hypothesis: past price changes have limited power to predict future price changes linearly.
- This does **not** imply returns are independent or unpredictable in higher moments; it specifically refers to the *linear* autocorrelation structure of the returns themselves, not of transformations of returns (see Fact 2).
- Small, sometimes statistically significant but economically negligible, autocorrelation at lag 1 is sometimes documented, often attributed to microstructure effects such as bid-ask bounce, particularly at very high frequencies.

### Fact 2: Volatility Clustering

**Key Points**

- Large price changes tend to be followed by large price changes (of either sign), and small changes tend to be followed by small changes — "large changes tend to be followed by large changes, of either sign, and small changes tend to be followed by small changes," in Mandelbrot's (1963) original characterization.
- This is the central empirical motivation for ARCH/GARCH modeling: while returns themselves show little autocorrelation, squared returns ($r_t^2$) and absolute returns ($|r_t|$) show strong, persistent positive autocorrelation, indicating that the *conditional variance* is time-varying and serially dependent even when the conditional mean is not.
- Volatility clustering implies volatility is forecastable even when returns are not, which is the foundational insight enabling GARCH-family models to have practical forecasting value in risk management despite returns themselves being close to a martingale difference sequence.

### Fact 3: Fat Tails (Excess Kurtosis)

**Key Points**

- The unconditional distribution of returns exhibits significantly heavier tails than the normal distribution, with excess kurtosis (kurtosis greater than 3, the Gaussian benchmark) consistently documented across asset classes.
- Extreme returns (large positive or negative moves) occur far more frequently than a Gaussian model would predict, an empirical regularity central to the motivation for risk management approaches that go beyond simple variance (e.g., Value-at-Risk models using fat-tailed conditional distributions, such as Student's t or generalized error distributions, within a GARCH framework).
- Even after conditioning on a GARCH-type time-varying volatility process, standardized residuals ($\hat{z}_t = r_t / \hat{\sigma}_t$) often retain some residual excess kurtosis relative to normal, though typically substantially less than the unconditional returns — motivating the common practice of specifying GARCH models with Student's-t or skewed-t conditional error distributions rather than assuming conditional normality.

### Fact 4: Leverage Effect / Asymmetric Volatility Response

**Key Points**

- Volatility tends to respond asymmetrically to positive versus negative return shocks: negative returns (price declines) are typically followed by larger increases in volatility than positive returns (price increases) of the same magnitude.
- The term "leverage effect" originates from Black's (1976) hypothesis that a stock price decline increases the firm's financial leverage ratio (debt-to-equity), raising the riskiness and hence volatility of the remaining equity — though the empirical magnitude of the asymmetry is often larger than what pure financial-leverage mechanics alone would predict, suggesting other channels (e.g., volatility feedback / time-varying risk premia) also contribute. [Inference: the relative importance of the leverage-mechanism explanation versus alternative explanations remains debated in the literature.]
- This asymmetry motivates asymmetric GARCH extensions such as the EGARCH model (Nelson, 1991), GJR-GARCH (Glosten, Jagannathan, and Runkle, 1993), and TGARCH, which explicitly allow the conditional variance response to differ by the sign of the prior shock.

### Fact 5: Aggregational Gaussianity

**Key Points**

- As the time scale over which returns are computed increases (e.g., from 5-minute to daily to monthly returns), the distribution of returns becomes progressively closer to normal, even though high-frequency returns are strongly non-Gaussian (fat-tailed).
- This is broadly consistent with a Central Limit Theorem-type intuition if returns over the longer interval can be thought of as sums of many shorter-interval, weakly dependent shocks — though the rate of convergence to normality and the persistence of some residual excess kurtosis at even fairly long horizons (e.g., monthly) has been empirically documented and is not perfectly explained by simple CLT arguments alone.

### Fact 6: Long Memory / Slow Decay in Volatility Autocorrelation

**Key Points**

- Autocorrelations of absolute or squared returns decay much more slowly than exponentially (the decay rate implied by standard short-memory ARMA-type processes), remaining statistically significant even at lags of many months, a pattern often described as "long memory" in volatility.
- This has motivated fractionally integrated volatility models (FIGARCH, Baillie, Bollerslev, and Mikkelsen, 1996) and component/long-run-short-run GARCH specifications (Engle and Lee, 1999) that explicitly allow for a slowly decaying persistent component in addition to a faster-decaying transient component.
- [Inference: whether the empirically observed slow decay reflects "true" long memory (a fractionally integrated process) versus structural breaks or regime changes that mimic long memory in finite samples remains an active and somewhat unresolved methodological debate in the literature.]

### Fact 7: Volume-Volatility Correlation

**Key Points**

- Trading volume is positively correlated with measures of volatility (contemporaneously and with some lead-lag structure), consistent with market microstructure theories linking information arrival, disagreement among traders, and price volatility to trading activity.

### Fact 8: Gain/Loss Asymmetry

**Key Points**

- Large drawdowns (cumulative losses from a peak) in individual stock prices or stock indices tend to be more common and/or more severe than comparably large gains over similar time windows — an asymmetry distinct from, but related to, the leverage effect in volatility.

### Summary Table of Stylized Facts

| Stylized fact | Empirical pattern | Primary modeling response |
| --- | --- | --- |
| Absence of return autocorrelation | Weak-form efficiency in levels | Justifies modeling conditional mean simply (e.g., constant or low-order ARMA) |
| Volatility clustering | Strong autocorrelation in $r_t^2$, $ | r_t |
| Fat tails | Excess kurtosis in unconditional returns | Student's-t / GED conditional distributions in GARCH |
| Leverage effect | Asymmetric volatility response to sign of shock | EGARCH, GJR-GARCH, TGARCH |
| Aggregational Gaussianity | Convergence toward normality at longer horizons | Motivates horizon-dependent model choice |
| Long memory in volatility | Slow-decaying autocorrelation in $ | r_t |
| Volume-volatility correlation | Positive co-movement of volume and volatility | Motivates volume as exogenous GARCH regressor |
| Gain/loss asymmetry | Larger/more frequent large drawdowns than gains | Motivates skewed conditional distributions |

### Illustrative Empirical Check

**Example**

Step 1: Obtain a daily price series (e.g., a broad equity index) and compute log returns $r_t = \ln(P_t/P_{t-1})$.

Step 2: Compute the sample autocorrelation function (ACF) of $r_t$ — expect near-zero, statistically insignificant autocorrelations beyond lag 1–2.

Step 3: Compute the ACF of $r_t^2$ (or $|r_t|$) — expect statistically significant positive autocorrelations persisting across many lags, visually confirming volatility clustering.

Step 4: Compute sample kurtosis of $r_t$ — expect a value well above 3 (the Gaussian benchmark), confirming fat tails.

Step 5: Split the sample by sign of $r_{t-1}$ (negative vs. positive prior return) and compare the average of $r_t^2$ conditional on each subsample — expect a materially higher average following negative prior returns, illustrating the leverage effect.

**Output**

A typical equity index dataset might show near-zero return autocorrelation (e.g., lag-1 autocorrelation around $\pm0.02$–$0.05$, often statistically insignificant or only marginally significant), squared-return autocorrelation remaining significantly positive out to 20+ lags, sample kurtosis in the range of roughly 5–10 or higher (well above the Gaussian value of 3), and volatility following negative returns noticeably exceeding volatility following positive returns of similar magnitude. [Inference: precise figures vary substantially by asset, sample period, and frequency; the values given are illustrative of commonly reported orders of magnitude in the empirical literature, not a specific dataset's results.]

### Common Pitfalls

- **Testing return autocorrelation and concluding "no dependence" broadly**: Absence of linear return autocorrelation does not imply independence; squared/absolute returns must be checked separately to detect volatility clustering (nonlinear dependence).
- **Assuming Gaussian conditional errors by default**: Given persistent fat tails even after GARCH filtering, defaulting to a normal conditional distribution without checking standardized residuals can understate tail risk in applications like VaR.
- **Ignoring asymmetry**: Fitting a symmetric GARCH(1,1) when the leverage effect is empirically strong in the data misses an important, well-documented feature and can bias volatility forecasts, particularly around large negative return episodes.
- **Confusing long memory with structural breaks**: Fitting a fractionally integrated model to data whose slow autocorrelation decay is actually driven by a small number of regime shifts (e.g., a volatility level shift around a crisis) can produce a misleading long-memory parameter estimate.

### Volatility Clustering Illustration

```mermaid
flowchart LR
    subgraph stylized_facts_overview Stylized Facts Empirical Checks (svg_diagram)
    A["Daily log returns r_t"] --> B["ACF of r_t"]
    A --> C["ACF of r_t squared or abs(r_t)"]
    A --> D["Sample kurtosis of r_t"]
    A --> E["Split by sign of r_t-1, compare avg r_t squared"]
    B --> B1["Near-zero, fast decay => weak linear dependence"]
    C --> C1["Significant, slow decay => volatility clustering"]
    D --> D1["Value greater than 3 => fat tails"]
    E --> E1["Higher avg after negative r_t-1 => leverage effect"]
    end
```

### Software Implementation Notes

- **R**: `PerformanceAnalytics` (kurtosis, skewness, drawdown functions), base `acf()` for return and squared-return autocorrelation checks, `rugarch` for subsequent GARCH-family modeling once stylized facts are confirmed.
- **Python**: `statsmodels.graphics.tsaplots.plot_acf` for ACF diagnostics, `scipy.stats.kurtosis`, `arch` package for downstream GARCH modeling.

[Unverified: default kurtosis calculation conventions (excess vs. raw) and ACF confidence band construction vary by package/version; verify against current documentation before use.]

**Related Topics**

- ARCH and GARCH model specification
- EGARCH and GJR-GARCH asymmetric volatility models
- FIGARCH and long-memory volatility models
- Value-at-Risk and Expected Shortfall estimation
- Fat-tailed conditional distributions (Student's-t, GED, skewed-t)
- Realized volatility and high-frequency data measures
- Market microstructure and volume-volatility relationships