## Statistical Estimation and Regression Methods


### Core Concept

Statistical estimation and regression provide the tools to infer unknown model parameters, relationships between variables, and probability distributions from observed market data. In derivatives and structured products, these methods underpin volatility estimation, hedge ratio calculation, factor model construction, historical simulation for VaR, and regression-based Monte Carlo techniques such as Longstaff-Schwartz for American option pricing.

### Point Estimation

#### Method of Moments

Equates sample moments (mean, variance, skewness, kurtosis) to theoretical distributional moments to solve for unknown parameters.

**Key Points**

- Computationally simple but generally less statistically efficient than maximum likelihood estimation.
- Often used as a starting guess for more sophisticated calibration methods.

#### Maximum Likelihood Estimation (MLE)

Chooses parameters $\theta$ that maximize the likelihood of observing the sample data:

$$\hat{\theta} = \arg\max_{\theta} \, L(\theta \mid x_1, \ldots, x_n) = \arg\max_{\theta} \, \prod_{i=1}^n f(x_i \mid \theta)$$

In practice, the log-likelihood is maximized for numerical stability:

$$\hat{\theta} = \arg\max_{\theta} \sum_{i=1}^n \ln f(x_i \mid \theta)$$

**Key Points**

- MLE is the standard approach for fitting GARCH models, jump-diffusion parameters, and historical return distributions.
- Asymptotically efficient and consistent under standard regularity conditions, but can be sensitive to model misspecification.
- Requires numerical optimization (see Newton-Raphson, BFGS) when no closed-form solution exists for $\hat{\theta}$.

### Linear Regression

The ordinary least squares (OLS) model:

$$y_i = \beta_0 + \beta_1 x_{i1} + \cdots + \beta_k x_{ik} + \varepsilon_i$$

Coefficients are estimated by minimizing the sum of squared residuals:

$$\hat{\beta} = \arg\min_{\beta} \sum_{i=1}^n (y_i - X_i \beta)^2 = (X^T X)^{-1} X^T y$$

**Key Points**

- Assumes linearity, homoscedasticity (constant error variance), independence of errors, and normally distributed residuals (for inference purposes).
- The classical use case in derivatives is estimating a hedge ratio (**beta**) — regressing an asset's returns against an index or benchmark.
- $R^2$ measures the proportion of variance explained; adjusted $R^2$ penalizes for additional regressors.

**Example**

Estimating a hedge ratio for a portfolio against a futures contract:

$$\Delta S_{portfolio} = \alpha + \beta \times \Delta S_{futures} + \varepsilon$$

The estimated $\hat{\beta}$ gives the optimal hedge ratio (number of futures contracts per unit of portfolio exposure) under a minimum-variance hedging objective.

### Violations of OLS Assumptions

| Issue | Description | Common Remedy |
| --- | --- | --- |
| Heteroscedasticity | Non-constant error variance | Weighted least squares, robust (White) standard errors |
| Autocorrelation | Correlated errors across time (common in time series) | Newey-West standard errors, GLS |
| Multicollinearity | Regressors highly correlated with each other | Ridge regression, PCA, variable removal |
| Non-stationarity | Statistical properties change over time (common in price levels) | Differencing, cointegration methods |

**Key Points**

- Financial time series (interest rates, volatility, prices) frequently violate homoscedasticity and independence assumptions, making naive OLS standard errors unreliable for hypothesis testing even if point estimates remain unbiased. [Inference: severity depends on the specific series and sampling frequency used.]

### Regularized Regression

#### Ridge Regression (L2 penalty)

$$\hat{\beta}_{ridge} = \arg\min_{\beta} \left[ \sum_i (y_i - X_i\beta)^2 + \lambda \sum_j \beta_j^2 \right]$$

#### LASSO Regression (L1 penalty)

$$\hat{\beta}_{lasso} = \arg\min_{\beta} \left[ \sum_i (y_i - X_i\beta)^2 + \lambda \sum_j |\beta_j| \right]$$

**Key Points**

- Ridge shrinks coefficients toward zero without eliminating them, useful when regressors are highly correlated (e.g., yield curve factors).
- LASSO can shrink coefficients exactly to zero, performing implicit variable selection — useful for factor model construction with many candidate risk factors.

### Time Series Estimation

#### Autoregressive (AR) and GARCH Models

Volatility clustering in financial returns is commonly modeled with **GARCH(1,1)**:

$$\sigma_t^2 = \omega + \alpha \varepsilon_{t-1}^2 + \beta \sigma_{t-1}^2$$

where $\omega, \alpha, \beta$ are estimated via MLE, subject to $\alpha + \beta < 1$ for stationarity.

**Key Points**

- GARCH models are widely used to estimate and forecast realized/historical volatility as an input or cross-check against implied volatility from option prices.
- $\alpha + \beta$ close to 1 indicates high volatility persistence ("volatility clustering"), a well-documented empirical feature of asset returns.

#### Cointegration and Error Correction Models

Used to identify long-run equilibrium relationships between non-stationary series (e.g., spot and futures prices), critical for statistical arbitrage and basis trading strategies.

**Key Points**

- The Engle-Granger and Johansen tests are standard methods for detecting cointegration between price series.

### Regression in Exotic Derivatives Pricing: Longstaff-Schwartz Method

Regression plays a direct pricing role in the **Least Squares Monte Carlo (LSM)** method for American/Bermudan option pricing:

1. Simulate asset paths forward to maturity.
2. Work backward from maturity; at each exercise date, regress the discounted continuation value (from later simulated payoffs) on a set of basis functions of the current state (e.g., $1, S, S^2$ or Laguerre polynomials).
3. Use the fitted regression to estimate the conditional expected continuation value for each in-the-money path.
4. Compare continuation value to immediate exercise value; exercise optimally based on the comparison.

$$E[\text{Continuation Value} \mid S_t] \approx \sum_{k} \hat{\beta}_k \phi_k(S_t)$$

**Key Points**

- This is one of the most direct applications of regression within derivatives pricing itself (not just calibration), used extensively for American-style and path-dependent structured products (e.g., autocallables with early redemption features, Bermudan swaptions).
- Basis function choice materially affects both accuracy and computational cost; polynomial and Laguerre bases are common defaults. [Unverified: optimal basis choice is problem-specific and often determined empirically.]

### Principal Component Analysis (PCA) in Yield Curve Modeling

PCA decomposes correlated yield curve movements into orthogonal factors:

$$X = \sum_{i=1}^n \lambda_i v_i v_i^T$$

In practice, the first three principal components of yield curve changes are conventionally interpreted as:

| Component | Interpretation |
| --- | --- |
| PC1 | Level (parallel shift) |
| PC2 | Slope (steepening/flattening) |
| PC3 | Curvature (butterfly) |

**Key Points**

- These three factors typically explain the large majority of historical yield curve variance in developed markets, though the exact proportion varies by market and period. [Unverified: precise variance-explained figures are sample- and market-dependent.]
- PCA-based factor models are used for scenario generation, risk factor reduction, and hedging interest rate exposure across a structured product's rate-sensitive cash flows.

### Diagram: Longstaff-Schwartz Backward Induction

```mermaid
flowchart RL
    A["Maturity T: Terminal Payoff"] --> B["t_n-1: Regress continuation value on basis functions"]
    B --> C["Compare: Exercise vs Continue"]
    C --> D["t_n-2: Regress continuation value"]
    D --> E["Compare: Exercise vs Continue"]
    E --> F["t=0: Discounted Expected Value"]
```

### Model Diagnostics and Validation

**Key Points**

- Out-of-sample backtesting is essential to validate that a fitted regression or estimated model generalizes beyond the calibration sample rather than overfitting.
- Residual analysis (autocorrelation plots, Q-Q plots for normality) should accompany any regression used for hedge ratio or volatility estimation to detect assumption violations.
- Cross-validation techniques (k-fold, walk-forward) are standard practice for regularized regression models (Ridge/LASSO) to select the penalty parameter $\lambda$.

### Relevance to Structured Products and Derivatives

- **Hedge ratio estimation**: linear regression (beta estimation) directly informs delta-hedging and cross-hedging strategies for structured product issuers.
- **Volatility forecasting**: GARCH-family models provide historical/realized volatility estimates used alongside implied volatility for relative value and risk management.
- **American/Bermudan exotic pricing**: Longstaff-Schwartz regression is a core numerical technique for pricing callable/putable structured notes and autocallables with early-exercise features.
- **Yield curve risk management**: PCA-based factor decomposition supports scenario analysis and hedge construction for interest-rate-linked structured products.
- **Model calibration diagnostics**: regression residual analysis is used to validate that a pricing model's implied parameters remain stable and consistent with historical data.

**Next Steps**

- Monte Carlo Methods for Derivatives Pricing (Longstaff-Schwartz in Depth)
- GARCH and Stochastic Volatility Model Estimation
- Principal Component Analysis for Yield Curve Risk
- Value-at-Risk (VaR) and Historical Simulation Methods
- Copulas and Dependence Modeling
- Time Series Analysis for Financial Data (Stationarity, Cointegration)