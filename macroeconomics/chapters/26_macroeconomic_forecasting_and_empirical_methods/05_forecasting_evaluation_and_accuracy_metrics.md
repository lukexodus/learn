## Forecasting Evaluation and Accuracy Metrics


### Overview

Producing a forecast is only half the task; rigorously evaluating its accuracy, comparing it against competitors, and understanding the sources of forecast error are equally central to empirical macroeconomics. Forecast evaluation methodology addresses three broad questions: (1) how large are forecast errors and by what metric should they be judged, (2) is one model's forecast statistically superior to another's, and (3) is the forecast **efficient** — does it appropriately use all available information at the time it was made. This topic covers point-forecast accuracy metrics, statistical tests for comparing forecasts, evaluation of density/probabilistic forecasts, and the practical pitfalls of real-time macro data.

---

### The Forecasting Error and Loss Functions

For a forecast $\hat{y}_{t+h|t}$ of the actual outcome $y_{t+h}$ made at time $t$ for horizon $h$, the forecast error is:

$$e_{t+h|t} = y_{t+h} - \hat{y}_{t+h|t}$$

The choice of accuracy metric is fundamentally a choice of **loss function** $L(e_{t+h|t})$. Under **quadratic loss**, the optimal (loss-minimizing) forecast is the conditional mean $E(y_{t+h}|\Omega_t)$; under **absolute loss**, the optimal forecast is the conditional median. This distinction matters because different metrics implicitly reward different point forecasts, and a model "optimal" under one loss function need not be optimal under another.

---

### Scale-Dependent Accuracy Metrics

These metrics share the same units as the underlying variable, making them useful for comparing models on a *single* series but not directly comparable across series with different scales or units.

**Mean Error (ME)** — measures average bias:

$$ME = \frac{1}{n}\sum_{t=1}^{n} e_t$$

A non-zero ME indicates systematic over- or under-prediction. In efficient forecasts, $ME$ should not be statistically distinguishable from zero.

**Mean Absolute Error (MAE)**:

$$MAE = \frac{1}{n}\sum_{t=1}^{n} |e_t|$$

MAE is the average magnitude of error, treating all deviations linearly, and is more robust to outliers than squared-error measures.

**Mean Squared Error (MSE)** and **Root Mean Squared Error (RMSE)**:

$$MSE = \frac{1}{n}\sum_{t=1}^{n} e_t^2 \qquad RMSE = \sqrt{MSE}$$

Squaring penalizes large errors disproportionately, making RMSE more sensitive to outliers and large misses — often desirable in macro contexts where large errors (e.g., missing a recession) are disproportionately costly.

**RMSE vs. MAE relationship:** RMSE $\geq$ MAE always, with equality only when all errors have identical absolute magnitude. The ratio RMSE/MAE rises with the variance of error magnitudes, so a large gap between the two signals occasional large misses rather than uniformly moderate error.

---

### Scale-Independent (Relative) Metrics

Because macro forecasters often need to compare across series with different units (e.g., comparing GDP forecast accuracy against inflation forecast accuracy) or across countries, scale-free metrics are preferred for cross-series comparison.

**Mean Absolute Percentage Error (MAPE)**:

$$MAPE = \frac{100}{n}\sum_{t=1}^{n}\left|\frac{e_t}{y_t}\right|$$

MAPE is intuitive (expressed in percentage terms) but has well-documented flaws: it is undefined when $y_t = 0$, becomes extreme when $y_t$ is near zero (a common issue for series like inflation or output gaps that fluctuate around zero), and is asymmetric — it penalizes over-forecasts (which can exceed 100%) more heavily than under-forecasts (bounded at 100%).

**Symmetric MAPE (sMAPE)** was proposed to address the asymmetry, though it introduces its own distortions and is not universally adopted:

$$sMAPE = \frac{100}{n}\sum_{t=1}^{n}\frac{|e_t|}{(|y_t| + |\hat{y}_t|)/2}$$

**Mean Absolute Scaled Error (MASE)** (Hyndman & Koehler, 2006) — scales errors by the in-sample MAE of a naive (typically random-walk) benchmark, avoiding the division-by-zero and asymmetry problems of MAPE:

$$MASE = \frac{\frac{1}{n}\sum_{t=1}^{n}|e_t|}{\frac{1}{n-1}\sum_{t=2}^{n}|y_t - y_{t-1}|}$$

A $MASE < 1$ indicates the forecast outperforms the naive in-sample benchmark on average; $MASE > 1$ indicates it underperforms. [Inference] MASE has become the preferred scale-free metric in the forecasting-competition literature (e.g., the M-competitions) precisely because it avoids MAPE's pathologies, though MAPE remains common in central bank and policy communications due to its intuitive percentage interpretation.

---

### Theil's U Statistics

**Theil's U1** (bounded, 0 to 1) compares RMSE of the forecast to a normalization based on the actual and forecast levels:

$$U_1 = \frac{\sqrt{\frac{1}{n}\sum_{t=1}^n (\hat{y}_t - y_t)^2}}{\sqrt{\frac{1}{n}\sum_{t=1}^n \hat{y}_t^2} + \sqrt{\frac{1}{n}\sum_{t=1}^n y_t^2}}$$

**Theil's U2** compares the model's forecast RMSE against a naive no-change (random walk) forecast:

$$U_2 = \frac{\sqrt{\sum_{t=1}^{n-1}\left(\frac{\hat{y}_{t+1}-y_{t+1}}{y_t}\right)^2}}{\sqrt{\sum_{t=1}^{n-1}\left(\frac{y_{t+1}-y_t}{y_t}\right)^2}}$$

- $U_2 = 1$: forecast is as good as a naive random walk
- $U_2 < 1$: forecast outperforms the naive benchmark
- $U_2 > 1$: forecast is worse than simply predicting no change

This benchmark comparison is central to macro forecast evaluation, since random-walk and simple autoregressive benchmarks are notoriously difficult to beat for many macro series, especially exchange rates (the classic Meese-Rogoff, 1983 result).

---

### Theil's Decomposition of MSE

MSE can be decomposed into three components that diagnose *why* a forecast is inaccurate:

$$MSE = \underbrace{(\bar{y} - \bar{\hat{y}})^2}_{\text{Bias Proportion}} + \underbrace{(s_y - s_{\hat{y}})^2}_{\text{Variance Proportion}} + \underbrace{2(1-\rho)s_y s_{\hat{y}}}_{\text{Covariance Proportion}}$$

where $\bar{y}, \bar{\hat{y}}$ are means, $s_y, s_{\hat{y}}$ are standard deviations, and $\rho$ is the correlation between actual and forecast values.

- **Bias proportion** — systematic over/under-prediction (should be near zero for a well-calibrated forecast)
- **Variance proportion** — the forecast fails to replicate the variability of the actual series (e.g., forecasts are too smooth relative to actual volatility)
- **Covariance proportion** — unsystematic, residual error; ideally this captures the bulk of MSE, since bias and variance proportions represent correctable, systematic errors

A forecaster finding a high bias or variance proportion has diagnostic evidence that the model can be structurally improved, rather than simply facing irreducible noise.

---

### Forecast Efficiency and Rationality Tests

**Mincer-Zarnowitz Regression** (1969) tests whether a forecast is unbiased and efficient by regressing the actual outcome on the forecast:

$$y_{t+h} = \alpha + \beta \hat{y}_{t+h|t} + u_t$$

Under the null of forecast rationality/efficiency: $\alpha = 0$ and $\beta = 1$, tested jointly via an F-test (or Wald test). Rejection indicates either bias ($\alpha \neq 0$) or that the forecast systematically over- or under-reacts to information ($\beta \neq 1$).

**Weak-form efficiency test** — regressing the forecast error on the forecast itself or on information available at time $t$:

$$e_{t+h|t} = \gamma_0 + \gamma_1 \hat{y}_{t+h|t} + v_t$$

If $\gamma_1 \neq 0$, the forecast error is predictable from the forecast, indicating inefficiency — the forecaster is not using available information optimally.

**Orthogonality/information-efficiency test** — regressing the error on other variables known at time $t$ (e.g., past errors, other indicators):

$$e_{t+h|t} = \delta_0 + \delta_1 X_t + w_t$$

A significant $\delta_1$ indicates the forecast fails to incorporate information in $X_t$, violating full-information rational expectations.

---

### Statistical Tests for Comparing Forecast Accuracy

Point estimates of RMSE or MAE differences between two competing models do not, by themselves, establish that one model is *statistically* superior — sampling variation must be accounted for.

**Diebold-Mariano (DM) Test** (1995) — the standard test for equal predictive accuracy between two forecasts, based on the loss differential:

$$d_t = L(e_{1t}) - L(e_{2t})$$

where $L(\cdot)$ is a chosen loss function (e.g., squared or absolute error) and $e_{1t}, e_{2t}$ are the two competing models' forecast errors. Under $H_0: E(d_t) = 0$ (equal accuracy), the test statistic is:

$$DM = \frac{\bar{d}}{\sqrt{\widehat{\text{Var}}(\bar{d})/n}} \sim N(0,1) \text{ asymptotically}$$

The variance estimator must account for serial correlation in $d_t$, which arises mechanically at multi-step horizons ($h>1$) because overlapping forecast errors share common shocks; a Newey-West (HAC) estimator is standard.

**Harvey-Leybourne-Newbold (HLN) correction** (1997) adjusts the DM statistic for small-sample bias, recommended particularly when $n$ is small relative to $h$:

$$DM^* = DM \times \sqrt{\frac{n+1-2h+h(h-1)/n}{n}}$$

compared against a Student's $t_{n-1}$ distribution rather than the standard normal.

**Nested Model Comparisons** — the standard DM test assumes non-nested models. When comparing a restricted model against a nested, more general alternative (e.g., testing whether adding a predictor improves an AR benchmark), the DM test's asymptotic distribution is non-standard under the null because the models converge, and specialized tests are needed:

- **Clark-McCracken (2001) test** and **Clark-West (2007) test** adjust for the added noise from estimating parameters that are zero under the null, restoring valid asymptotic inference for nested comparisons.

**Giacomini-White (GW) Test** (2006) — generalizes DM to evaluate **conditional** predictive ability and remains valid for comparing forecasts from models estimated with rolling or fixed windows (relaxing DM's implicit assumption of population-level parameters), a common realistic setting in real-time macro forecasting.

---

### Forecast Encompassing

A distinct question from "which forecast is more accurate" is "does one forecast contain all the useful information in the other." The **forecast encompassing test** (Chong & Hendry, 1986) regresses the actual value on both competing forecasts:

$$y_{t+h} = \lambda \hat{y}_{1,t+h|t} + (1-\lambda)\hat{y}_{2,t+h|t} + u_t$$

If $\lambda = 1$, forecast 1 encompasses forecast 2 (forecast 2 adds no independent information). If $0 < \lambda < 1$, a **combined forecast** — long documented to often outperform either individual component forecast, a robust empirical finding since Bates and Granger (1969) — may improve accuracy.

---

### Evaluating Probabilistic and Density Forecasts

Macro forecasters increasingly report full predictive distributions (fan charts) rather than point forecasts alone, particularly for policy communication (e.g., central bank inflation fan charts). Evaluating these requires different tools.

**Probability Integral Transform (PIT)** — if the forecast density is correctly specified, the PIT values,

$$z_t = F_t(y_t)$$

(where $F_t$ is the forecaster's CDF evaluated at the realized outcome), should be **i.i.d. Uniform(0,1)**. Departures from uniformity (tested via Kolmogorov-Smirnov tests or histograms) indicate miscalibration — e.g., a hump-shaped PIT histogram suggests the forecast intervals are too wide (overdispersed), while a U-shaped histogram indicates intervals are too narrow (underdispersed, overconfident).

**Continuous Ranked Probability Score (CRPS)** — a proper scoring rule generalizing MAE to full distributions:

$$CRPS(F_t, y_t) = \int_{-\infty}^{\infty} \left(F_t(x) - \mathbb{1}\{x \geq y_t\}\right)^2 dx$$

Lower CRPS indicates a better-calibrated, sharper density forecast; it reduces to absolute error when the forecast is a point mass.

**Log Score / Predictive Likelihood** — evaluates the log-density of the forecast distribution at the realized outcome:

$$LS_t = \ln f_t(y_t)$$

Widely used in DSGE and Bayesian VAR model comparison, since it directly rewards both calibration and sharpness and connects naturally to Bayesian model averaging and marginal likelihood comparisons.

**Coverage Rate** — for an announced $(1-\alpha)$ prediction interval, the empirical coverage rate (fraction of realized outcomes falling within the interval) should approximate $1-\alpha$ over repeated forecasts; systematic under-coverage indicates intervals are too narrow.

---

### Real-Time Data and Pseudo-Out-of-Sample Evaluation

**The Real-Time Data Problem**

Macro data are revised repeatedly after initial release (e.g., GDP, employment). Evaluating a forecasting model using **final revised data** — as if the forecaster had known the eventually-revised figures at the time — overstates achievable real-time accuracy and can favor models that happen to fit the revision process well rather than genuinely superior real-time forecasting models. Rigorous evaluation uses **real-time datasets** (e.g., the Federal Reserve Bank of Philadelphia's Real-Time Data Set for Macroeconomists) that reconstruct exactly what data vintage was available at each historical forecast origin date.

**Pseudo-Out-of-Sample (Rolling/Recursive) Evaluation**

To simulate genuine forecasting performance, evaluation should be conducted out-of-sample:

```mermaid
flowchart LR
    A[Split data: training window] --> B[Estimate model on training window]
    B --> C[Forecast h steps ahead]
    C --> D[Compare to actual realized value]
    D --> E[Roll or expand window forward by one period]
    E --> B
```

- **Recursive (expanding window) scheme:** the estimation sample grows with each iteration, using all available history
- **Rolling (fixed window) scheme:** the estimation sample size is held fixed, dropping the oldest observation as a new one is added — better suited to environments with structural change or parameter instability
- **Fixed scheme:** parameters estimated once and held fixed for all subsequent forecasts (rarely used in practice, mainly as a theoretical benchmark)

[Inference] The choice between rolling and recursive schemes is a practical bias-variance tradeoff: recursive schemes use more data (lower parameter estimation variance) but are more exposed to bias from earlier, potentially non-representative regimes, and there is no universal rule for which dominates — it depends on the degree of structural stability in the specific application.

**Common Benchmarks in Macro Forecast Evaluation**

- **Random walk (no-change) forecast** — standard benchmark for exchange rates, asset prices, and often GDP/inflation at short horizons
- **AR(1) or simple ARIMA benchmark** — for series with own-dynamics persistence
- **Survey-based forecasts** (e.g., Survey of Professional Forecasters, Consensus Economics) — used as a benchmark reflecting the information set of professional forecasters, against which model-based forecasts are often compared
- **Random walk with drift** — accounts for a deterministic trend component

---

### Worked Numerical Example

Suppose two models forecast quarterly inflation one quarter ahead over 40 out-of-sample quarters:

| Model | RMSE | MAE | MASE |
| --- | --- | --- | --- |
| AR(1) benchmark | 0.62 | 0.48 | 1.00 |
| Phillips Curve VAR | 0.51 | 0.39 | 0.81 |

The VAR model shows lower RMSE, MAE, and a MASE below 1, suggesting improvement over both the AR(1) benchmark and the naive random-walk scaling reference. To confirm this improvement is **statistically** significant (not just numerically smaller), a Diebold-Mariano test would be applied to the squared-error loss differentials $d_t = e_{1t}^2 - e_{2t}^2$. Suppose this yields $DM = 2.14$ with a corresponding $p$-value of 0.032 — under a conventional 5% significance threshold, the null of equal predictive accuracy would be rejected, providing statistical support that the Phillips Curve VAR significantly outperforms the AR(1) benchmark over this evaluation sample. [Inference] This numerical example is illustrative of the standard workflow; actual DM statistics depend entirely on the realized error series in a given application.

---

### Practical Considerations and Common Pitfalls

- **Multiple-horizon evaluation** — accuracy at $h=1$ does not guarantee accuracy at $h=4$ or $h=8$; forecast rankings frequently change across horizons, so evaluation should be reported horizon-by-horizon
- **Sample-specific results** — accuracy comparisons over one historical period (e.g., the Great Moderation) may not generalize to periods of heightened volatility (e.g., 2008–09, 2020–21); robustness checks across sub-samples are standard practice
- **Data snooping / repeated testing** — comparing many models against a benchmark and reporting only the best performer inflates the risk of false positives; tests like the **Reality Check** (White, 2000) or the **Model Confidence Set** (Hansen, Lunde, and Nason, 2011) address this by controlling for multiple comparisons
- **Overlapping-horizon serial correlation** — must be corrected for (via HAC/Newey-West standard errors) in any multi-step DM test; failing to do so overstates statistical significance
- **Loss function mismatch** — a model selected for lowest RMSE (favoring the conditional mean) may not be the best choice under an asymmetric policy loss function (e.g., a central bank more concerned about upside inflation misses than downside ones)

---

**Related Topics**

- Real-time data vintages and data revision analysis
- Survey of Professional Forecasters and forecast disagreement measures
- Forecast combination methods (simple averaging, Bayesian model averaging)
- The Model Confidence Set and superior predictive ability tests
- Fan charts and central bank probabilistic communication
- Nowcasting and mixed-frequency evaluation
- Backtesting methodologies in applied macro-financial forecasting
- Judgmental vs. model-based forecast reconciliation