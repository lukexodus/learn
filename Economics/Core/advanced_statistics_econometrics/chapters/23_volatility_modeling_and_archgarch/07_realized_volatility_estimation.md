## Realized Volatility Estimation


### Conceptual Foundation

Realized volatility (RV) is a model-free, ex-post estimator of the quadratic variation of a price process, constructed by summing squared high-frequency intraday returns over a fixed period (e.g., a trading day). Unlike GARCH or stochastic volatility models, which infer latent conditional variance from a discrete-time parametric model fit to daily (or lower-frequency) returns, realized volatility exploits the availability of high-frequency (intraday) data to construct a direct, largely nonparametric measure of how much an asset actually moved over a given interval. This shifted the volatility literature substantially since the late 1990s/early 2000s, following foundational work by Andersen and Bollerslev (1998) and Andersen, Bollerslev, Diebold, and Labys (2001, 2003).

### Theoretical Foundation: Quadratic Variation

For a continuous-time price process following, in its most general semimartingale form:

$$d\ln P_t = \mu_t \, dt + \sigma_t \, dW_t + \text{jumps}$$

the **quadratic variation** over $[0,1]$ (e.g., one trading day) is the theoretical object realized volatility seeks to estimate:

$$QV = \int_0^1 \sigma_t^2 \, dt + \sum_{0 \leq s \leq 1} J_s^2$$

where the first term is the integrated variance from the continuous (diffusive) component and the second term sums squared jump contributions if the price process includes discontinuous jumps.

### The Realized Variance Estimator

$$RV_t = \sum_{i=1}^{M} r_{t,i}^2$$

where $r_{t,i}$ is the $i$-th intraday log return on day $t$ (e.g., 5-minute returns), and $M$ is the number of intraday intervals (e.g., $M=78$ for 5-minute returns over a 6.5-hour trading day).

**Key Points**

- As the sampling frequency increases (more, smaller intraday intervals, $M \to \infty$), $RV_t$ converges in probability to the quadratic variation $QV_t$ under standard regularity conditions — this consistency result is the theoretical foundation justifying RV as a nonparametric volatility estimator, in contrast to GARCH/SV's model-based (parametric) approach.
- In practice, sampling at the very highest available frequencies (e.g., tick-by-tick or 1-second) is **not** optimal due to market microstructure noise (bid-ask bounce, discreteness of price changes, asynchronous trading), which biases $RV_t$ upward at ultra-high frequencies — this is the central practical tension in realized volatility estimation.
- Realized volatility is often reported as $RV_t^{1/2}$ (realized standard deviation/"realized volatility" in the narrower sense) or annualized for comparability across contexts.

### The Microstructure Noise Problem

**Key Points**

- Observed high-frequency transaction or quote prices are contaminated by market microstructure effects: $p_{t,i}^{obs} = p_{t,i}^{true} + \epsilon_{t,i}$, where $\epsilon_{t,i}$ represents noise from bid-ask bounce, discrete price grids (tick size), and other trading-mechanism artifacts.
- This noise, even if individually small, accumulates in the sum of squared returns as sampling frequency increases, producing an upward-biased and increasingly noisy $RV_t$ estimator at very high frequencies — a "volatility signature plot" (RV plotted against sampling frequency) typically shows $RV_t$ increasing sharply as intervals shrink toward very high frequencies, revealing the noise contamination.
- The classical practical compromise has historically been to sample at a moderate frequency (5-minute sampling became a widely used convention, sometimes called "sparse sampling") that balances the bias-variance trade-off: too coarse a sampling misses genuine intraday variation, too fine a sampling amplifies microstructure noise bias.

### Noise-Robust Realized Volatility Estimators

Because ad hoc sparse sampling discards potentially useful high-frequency information, several formal noise-robust estimators have been developed:

**Two-Scale Realized Volatility (TSRV)** (Zhang, Mykland, and Aït-Sahalia, 2005): Combines a coarse-scale and a fine-scale realized volatility estimate to construct a bias-corrected estimator that remains consistent even at the highest available sampling frequency.

**Realized Kernels** (Barndorff-Nielsen, Hansen, Lunde, and Shephard, 2008): Apply kernel-weighted autocovariance corrections (analogous to HAC/Newey-West-style corrections in standard time series econometrics) to the sum of squared and cross-product returns, explicitly correcting for the autocorrelation induced by microstructure noise.

**Pre-averaging estimators** (Jacod, Li, Mykland, Podolskij, and Vetter, 2009): Average returns over short local windows before squaring and summing, reducing noise impact while preserving much of the signal from high-frequency data.

### Jump-Robust Estimation: Bipower Variation

Since standard $RV_t$ estimates total quadratic variation (continuous **plus** jump components combined), separating the two requires additional tools. **Realized Bipower Variation** (Barndorff-Nielsen and Shephard, 2004, 2006):

$$BV_t = \frac{\pi}{2} \sum_{i=2}^{M} |r_{t,i}||r_{t,i-1}|$$

**Key Points**

- $BV_t$ converges to the **continuous (integrated variance) component only**, $\int_0^1 \sigma_t^2\,dt$, effectively filtering out jump contributions, since a single large jump return is unlikely to be immediately followed by another equally large return (jumps are typically isolated), so the product $|r_{t,i}||r_{t,i-1}|$ largely cancels jump effects while retaining diffusive variance.
- The difference $RV_t - BV_t$ provides a nonparametric estimate of the **jump contribution** to total quadratic variation on day $t$, and (with an appropriate normalization and asymptotic distribution theory) forms the basis of formal jump detection tests, such as the Barndorff-Nielsen and Shephard (BNS) jump test, comparing the relative jump ratio $(RV_t - BV_t)/RV_t$ against its asymptotic distribution under the no-jump null.

### Realized Covariance and Multivariate Extensions

$$RCov_{ij,t} = \sum_{k=1}^{M} r_{i,t,k}\, r_{j,t,k}$$

extending realized variance to the multivariate setting, providing a direct nonparametric estimate of the realized covariance matrix — directly usable, for instance, as a target or input for dynamic conditional covariance modeling.

**Key Points**

- **Asynchronous trading** across different assets (e.g., different stocks trading at different exact times within an interval) introduces additional bias (the Epps effect: realized correlations biased toward zero at high sampling frequencies when returns are not perfectly time-synchronized) requiring specialized synchronization or refresh-time sampling methods, or estimators like the multivariate realized kernel, specifically designed to handle this.

### Practical Estimation Workflow

**Example**

Step 1: Obtain high-frequency (e.g., tick-level or 1-minute) price data for the asset of interest over the trading day(s) of interest.

Step 2: Construct a volatility signature plot: compute $RV_t$ across a range of sampling frequencies (e.g., 1-minute, 5-minute, 15-minute, 30-minute) and plot against frequency to visually assess the extent of microstructure noise contamination.

Step 3: Select a sampling frequency or noise-robust estimator based on the signature plot: if $RV_t$ is relatively flat across a range of moderate frequencies, sparse sampling at that frequency is reasonable; if strong upward bias is evident at high frequencies, apply a noise-robust estimator (TSRV, realized kernel, pre-averaging) to exploit the full data without bias.

Step 4: Compute daily $RV_t$ (and, if jump-robustness is desired, $BV_t$ and the implied jump component) across the sample period, constructing a time series of daily realized volatility.

Step 5: Use the resulting $RV_t$ series either as a standalone descriptive/forecasting object (e.g., via HAR-RV models, below) or as a validation benchmark for comparing GARCH/SV model-implied conditional variance forecasts against a model-free "true" volatility proxy.

**Output**

A typical volatility signature plot for a liquid large-cap equity might show $RV_t$ relatively stable from roughly 5-minute to 30-minute sampling, with a visible upward bias emerging as sampling frequency increases beyond roughly 1-minute intervals — motivating the conventional 5-minute "sparse sampling" choice historically common in the empirical literature, or the use of a noise-robust estimator if finer-frequency data is to be fully exploited. [Inference: the specific frequency at which bias becomes material varies by asset liquidity and market microstructure characteristics; the pattern described is a commonly documented empirical regularity rather than a universal fixed threshold.]

### The HAR-RV Model (Corsi, 2009)

A widely used and highly parsimonious forecasting model for realized volatility, motivated by the long-memory-like persistence stylized fact, without requiring a fully specified fractional-integration model:

$$RV_{t+1} = c + \beta_D RV_t + \beta_W \overline{RV}_{t-5:t} + \beta_M \overline{RV}_{t-22:t} + u_{t+1}$$

where $\overline{RV}_{t-5:t}$ and $\overline{RV}_{t-22:t}$ are weekly and monthly moving averages of daily realized variance. The Heterogeneous Autoregressive (HAR) structure — combining daily, weekly, and monthly RV components as regressors — parsimoniously captures the long-memory-like slow decay in volatility persistence, and has become a standard, empirically well-performing benchmark forecasting model in the realized volatility literature, often outperforming more complex fractionally integrated alternatives in out-of-sample forecasting comparisons. [Inference: relative forecasting performance versus alternative long-memory models varies across specific studies, assets, and forecast horizons.]

### RV-Based Applications

**Key Points**

- **Model validation**: RV serves as a model-free volatility proxy against which GARCH and SV model forecasts are commonly benchmarked in out-of-sample forecast evaluation exercises.
- **Realized GARCH / GARCH-X models**: Directly incorporate realized volatility measures as an additional explanatory variable in the GARCH conditional variance equation, combining the parametric structure of GARCH with the information content of high-frequency-based realized measures (Hansen, Huang, and Shek, 2012, "Realized GARCH").
- **Option pricing and implied-vs-realized volatility comparisons**: RV provides a direct empirical counterpart for assessing option-implied volatility (e.g., from the VIX or individual option prices) against subsequently realized outcomes.

### Common Pitfalls

- **Ignoring microstructure noise at very high sampling frequencies**: Computing RV at the finest available frequency (e.g., tick-by-tick) without noise correction produces a substantially biased, inflated volatility estimate.
- **Confusing total quadratic variation with continuous variance**: Standard $RV_t$ captures both continuous and jump variation combined; applications requiring only the diffusive component (e.g., certain option-pricing contexts) should use bipower variation or another jump-robust estimator instead.
- **Ignoring asynchronous trading in multivariate/realized covariance settings**: Naive realized covariance/correlation estimates across assets with different trading intensities or exchange hours can be severely biased toward zero (Epps effect) without proper synchronization methods.
- **Overlooking overnight/weekend returns**: Standard intraday RV measures omit the overnight return, which can represent a substantial share of total daily variance for some assets; some applications explicitly add a separate overnight return term or use estimators designed to incorporate it.
- **Treating RV as entirely "model-free" without caveats**: While RV avoids parametric assumptions about the variance process, it still relies on asymptotic theory (increasingly fine sampling) and practical choices (sampling frequency, noise correction method) that constitute implicit modeling decisions with real consequences for the resulting estimates.

### Realized Volatility Construction Diagram

```mermaid
flowchart TD
    subgraph rv_construction_pipeline Realized Volatility Construction Pipeline (svg_diagram)
    A["High-frequency intraday price data"] --> B["Compute intraday log returns r_t,i"]
    B --> C["Sum of squared returns: RV_t = sum r_t,i^2"]
    C --> D{"Microstructure noise check: volatility signature plot"}
    D -->|"Flat across moderate frequencies"| E["Sparse sampling e.g. 5-min, use directly"]
    D -->|"Upward bias at high frequency"| F["Apply noise-robust estimator: TSRV, realized kernel, pre-averaging"]
    C --> G["Bipower variation BV_t: filters jumps, continuous component only"]
    G --> H["Jump component estimate: RV_t minus BV_t"]
    E --> I["Daily RV time series"]
    F --> I
    I --> J["HAR-RV forecasting model: daily, weekly, monthly components"]
    I --> K["Benchmark for GARCH/SV forecast validation"]
    end
```

### Software Implementation Notes

- **R**: `highfrequency` package (comprehensive: realized variance, bipower variation, realized kernels, jump tests, HAR-RV model estimation via `HARmodel()`), `realized` and related packages for specific estimators.
- **Python**: High-frequency/realized volatility tooling is less centralized than in R; implementations often draw on general time-series libraries (`pandas`, `numpy`) with custom construction of RV/BV estimators, or specialized packages depending on current ecosystem availability.
- **MATLAB**: Widely used in academic realized volatility research, with replication code accompanying many foundational papers (Andersen-Bollerslev-Diebold-Labys, Barndorff-Nielsen-Shephard, Corsi) commonly available in MATLAB.

[Unverified: exact function names, default sampling frequency conventions, and current package ecosystem status vary and may have changed since training; verify against current documentation before implementation.]

**Related Topics**

- Stylized facts of financial time series
- The GARCH model and extensions
- Stochastic volatility models
- HAR-RV forecasting models
- Jump detection tests (Barndorff-Nielsen and Shephard)
- Realized GARCH and GARCH-X models
- Implied volatility and the VIX