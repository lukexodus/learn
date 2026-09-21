## The Kalman Filter

### Definition and Conceptual Foundation

The Kalman filter (Kalman, 1960) is a recursive algorithm for computing the optimal estimate of an unobserved (latent) state vector in a linear state-space model, given all information available up to the current time period. It operates by alternating between a **prediction** step (projecting the state forward using the model's known dynamics) and an **update** step (correcting that projection using the newly observed data point), producing, under Gaussian assumptions, the exact minimum mean-squared-error estimate of the state at each point in time. It is the standard computational engine for estimating, filtering, and forecasting any model expressed in linear Gaussian state-space form.

### Setup: The State-Space System

$$y_t = Z_t \alpha_t + d_t + \varepsilon_t, \quad \varepsilon_t \sim N(0, H_t) \quad \text{(measurement equation)}$$



$$\alpha_{t+1} = T_t \alpha_t + c_t + R_t \eta_t, \quad \eta_t \sim N(0, Q_t) \quad \text{(transition equation)}$$

with $\varepsilon_t$ and $\eta_t$ mutually independent at all leads and lags, and the initial state $\alpha_1 \sim N(a_1, P_1)$.

### The Recursive Algorithm

**Prediction step** (project the state and its uncertainty forward one period, before seeing $y_t$):

$$a_{t|t-1} = T_{t-1} a_{t-1|t-1} + c_{t-1}$$



$$P_{t|t-1} = T_{t-1} P_{t-1|t-1} T_{t-1}' + R_{t-1} Q_{t-1} R_{t-1}'$$

**Update step** (incorporate the newly observed $y_t$ to correct the prediction):

$$v_t = y_t - Z_t a_{t|t-1} - d_t \quad \text{(innovation / prediction error)}$$



$$F_t = Z_t P_{t|t-1} Z_t' + H_t \quad \text{(innovation variance)}$$



$$K_t = P_{t|t-1} Z_t' F_t^{-1} \quad \text{(Kalman gain)}$$



$$a_{t|t} = a_{t|t-1} + K_t v_t$$



$$P_{t|t} = P_{t|t-1} - K_t Z_t P_{t|t-1} = (I - K_t Z_t)P_{t|t-1}$$

**Key Points**

- $v_t$ is the **innovation**: the difference between the actually observed $y_t$ and what the model predicted based on information up to $t-1$. Under correct specification, $\{v_t\}$ is a serially uncorrelated, zero-mean sequence — a property directly exploitable for model diagnostic checking (residual autocorrelation tests on the standardized innovations $v_t/\sqrt{F_t}$).
- The **Kalman gain** $K_t$ determines how much weight is placed on the new observation's surprise ($v_t$) relative to the prior prediction: when $H_t$ (measurement noise) is large relative to $P_{t|t-1}$ (prediction uncertainty), $K_t$ is small and the filter trusts the model's prediction more than the noisy new data point; when $H_t$ is small relative to $P_{t|t-1}$, $K_t$ is large and the filter weights the new observation heavily.
- The recursion requires only the previous period's filtered estimate $(a_{t-1|t-1}, P_{t-1|t-1})$ and the current observation $y_t$ — it does not need to re-process the entire historical data set at each step, making it computationally efficient and naturally suited to sequential/real-time updating as new data arrives.

### The Prediction Error Decomposition and Maximum Likelihood

Because $v_t \sim N(0, F_t)$ under the model's Gaussian assumptions, the exact Gaussian log-likelihood of the entire observed sample can be written as a sum of one-step-ahead prediction error contributions, directly computable from the filter's own outputs:

$$\ln L = -\frac{Tn}{2}\ln(2\pi) - \frac{1}{2}\sum_{t=1}^{T}\left(\ln|F_t| + v_t' F_t^{-1} v_t\right)$$

**Key Points**

- This "prediction error decomposition" (Schweppe, 1965; Harvey, 1989) is the standard route to maximum likelihood estimation of any linear Gaussian state-space model's unknown parameters (variances, autoregressive coefficients, etc.): run the Kalman filter given candidate parameter values, compute $\ln L$, and numerically optimize over the parameters.
- The Kalman filter naturally and gracefully handles **missing observations**: when $y_t$ is missing, the update step is simply skipped for that period (the filter proceeds directly from $a_{t|t-1}$ as if it were $a_{t|t}$), without requiring any special imputation procedure — a significant practical advantage over some conventional time-series estimation approaches.

### Kalman Smoothing

While the filter produces $a_{t|t}$ using only information available up to time $t$ (appropriate for real-time applications), the **Kalman smoother** computes $a_{t|T}$ — the estimated state at time $t$ using the **entire** sample of $T$ observations, including data after time $t$. The standard fixed-interval smoother (Rauch-Tung-Striebel algorithm) runs backward recursively after a full forward filtering pass:

$$a_{t|T} = a_{t|t} + P_{t|t}T_t' P_{t+1|t}^{-1}(a_{t+1|T} - a_{t+1|t})$$

**Key Points**

- Smoothed estimates $a_{t|T}$ are generally more precise (lower variance) than filtered estimates $a_{t|t}$ for the same time point $t$, since they exploit additional (future) information — but this also means smoothed estimates are **not appropriate** for genuinely real-time applications or pseudo-out-of-sample forecast evaluation, where only information available at the time should be used.
- Smoothing is the standard tool for retrospective, historical analysis: e.g., producing a final published decomposition of a macroeconomic series into smoothed trend/cycle/seasonal components using the complete available sample.

### Practical Estimation and Filtering Workflow

**Example**

Step 1: Specify the state-space model (e.g., a local level model for a series believed to follow a noisy random walk) and set initial values $a_1$, $P_1$ for the state, using a diffuse (very large $P_1$) initialization if the state process is non-stationary and lacks a natural unconditional distribution.

Step 2: For given trial values of the unknown variance parameters ($\sigma_\varepsilon^2$, $\sigma_\eta^2$), run the filter recursion forward through the sample, storing $v_t$ and $F_t$ at each step.

Step 3: Compute the Gaussian log-likelihood via the prediction error decomposition, and numerically maximize over the variance parameters.

Step 4: With the maximum-likelihood parameter estimates in hand, re-run the filter (for real-time/filtered estimates) and the smoother (for retrospective/smoothed estimates) to obtain the final state estimates $a_{t|t}$ and $a_{t|T}$.

Step 5: Diagnostic-check the model using standardized innovations $v_t/\sqrt{F_t}$: verify approximate normality, absence of residual autocorrelation, and absence of remaining heteroskedasticity, to confirm the fitted state-space specification is adequate.

**Output**

For a local level model fit to a macroeconomic time series, the Kalman filter typically produces a filtered level estimate that lags slightly behind the smoothed estimate (since the filter only uses past information at each point), with the smoothed series appearing visibly less noisy/more revised near the interior of the sample, and both series converging near the end of the sample where filtered and smoothed information sets nearly coincide. [Inference: the specific degree of divergence between filtered and smoothed paths depends on the estimated signal-to-noise ratio ($\sigma_\eta^2/\sigma_\varepsilon^2$) in the fitted model, which is series-specific.]

### Extensions for Non-Gaussian and Nonlinear Systems

**Key Points**

- **Extended Kalman Filter (EKF)**: Applies local (first-order Taylor) linearization of nonlinear measurement or transition functions at each time step, allowing an approximate Kalman-filter-style recursion to be applied to mildly nonlinear systems, at the cost of losing exact optimality.
- **Unscented Kalman Filter (UKF)**: Uses a deterministic set of sample points ("sigma points") to propagate mean and covariance information through nonlinear functions more accurately than simple linearization, generally outperforming the EKF for systems with substantial nonlinearity.
- **Particle filtering (Sequential Monte Carlo)**: A fully simulation-based approach appropriate for general nonlinear, non-Gaussian state-space systems (e.g., stochastic volatility models), representing the filtering distribution via a weighted set of simulated particles rather than a single Gaussian summary (mean and covariance).
- [Inference: the choice among EKF, UKF, and particle filtering in a given nonlinear application involves a trade-off between computational cost and approximation accuracy that is problem-specific.]

### Common Pitfalls

- **Improper initialization of non-stationary states**: Using an arbitrary finite $P_1$ for a random-walk-type state component (rather than a proper diffuse initialization) can materially bias early filtered estimates, particularly in shorter samples.
- **Using filtered estimates where smoothed estimates (or vice versa) are appropriate**: Substituting smoothed values into a pseudo-real-time forecasting exercise introduces look-ahead bias; conversely, using only filtered values for a final historical/retrospective decomposition sacrifices available precision unnecessarily.
- **Ignoring standardized innovation diagnostics**: Failing to check that $v_t/\sqrt{F_t}$ is approximately i.i.d. $N(0,1)$ under the fitted model can mask misspecification that the raw parameter estimates alone would not reveal.
- **Assuming the Kalman filter requires strict Gaussianity for any use**: While *exact* optimality (in a minimum-MSE sense across all, not just linear, estimators) requires Gaussian innovations, the Kalman filter remains the optimal **linear** estimator under weaker (finite second-moment) assumptions, so its use as a quasi-maximum-likelihood estimation device retains validity more broadly than sometimes assumed.

### Kalman Filter Recursion Diagram

```mermaid
flowchart TD
    subgraph kalman_filter_recursion Kalman Filter Recursive Cycle (svg_diagram)
    A["Filtered state at t-1: a_t-1 given t-1, P_t-1 given t-1"] --> B["Prediction step"]
    B --> C["a_t given t-1 = T times a_t-1 given t-1"]
    B --> D["P_t given t-1 = T P T' + R Q R'"]
    E["New observation y_t arrives"] --> F["Update step"]
    C --> F
    D --> F
    F --> G["Innovation: v_t = y_t minus Z a_t given t-1"]
    F --> H["Innovation variance: F_t = Z P Z' + H"]
    G --> I["Kalman gain: K_t = P Z' F_t inverse"]
    H --> I
    I --> J["Filtered state: a_t given t = a_t given t-1 + K_t v_t"]
    I --> K["Filtered covariance: P_t given t = (I - K_t Z) P_t given t-1"]
    J --> L["Feeds into next period's prediction step"]
    G --> M["Accumulate into log-likelihood via prediction error decomposition"]
    end
```

### Software Implementation Notes

- **R**: `KFAS` package (general linear/exponential-family Kalman filtering and smoothing), `dlm` package (`dlmFilter()`, `dlmSmooth()`), base `stats::StructTS()` for basic structural models.
- **Python**: `statsmodels.tsa.statespace` module provides Kalman filtering/smoothing as the underlying engine for `SARIMAX`, `UnobservedComponents`, and custom models via the `MLEModel` base class; `pykalman` for a more standalone Kalman filter implementation.
- **MATLAB**: Econometrics Toolbox `ssm` (state-space model) objects with built-in `filter()` and `smooth()` methods.

[Unverified: exact function/class names, default diffuse initialization handling, and numerical implementation details (e.g., square-root filtering variants for numerical stability) vary by package and version; verify against current documentation before implementation.]

**Related Topics**

- State-space representation of time series
- Regime-switching and Markov-switching models
- Stochastic volatility models
- Extended and unscented Kalman filters
- Particle filtering and sequential Monte Carlo methods
- Maximum likelihood estimation via prediction error decomposition
- Dynamic factor models