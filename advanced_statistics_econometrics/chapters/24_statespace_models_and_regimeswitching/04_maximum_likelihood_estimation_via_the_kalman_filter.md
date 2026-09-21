## Maximum Likelihood Estimation via the Kalman Filter

### Overview

Maximum likelihood estimation (MLE) for state-space models uses the Kalman filter as a computational device to evaluate the likelihood function of a linear Gaussian state-space model. The filter's prediction-error decomposition converts an otherwise intractable joint density over the observed time series into a product of easily computable one-step-ahead conditional densities, allowing standard numerical optimization to recover the unknown structural or reduced-form parameters governing the system.

### The State-Space Model Setup

The linear Gaussian state-space model consists of a transition (state) equation and a measurement (observation) equation:

$$\alpha_t = T_t \alpha_{t-1} + c_t + R_t \eta_t, \quad \eta_t \sim N(0, Q_t)$$



$$y_t = Z_t \alpha_t + d_t + \varepsilon_t, \quad \varepsilon_t \sim N(0, H_t)$$

Where:

- $\alpha_t$ is the unobserved state vector
- $y_t$ is the observed vector
- $T_t$, $Z_t$, $R_t$ are system matrices (possibly time-varying)
- $Q_t$, $H_t$ are covariance matrices of the state and observation disturbances
- $\eta_t$ and $\varepsilon_t$ are mutually independent white noise sequences

All system matrices are typically functions of a parameter vector $\theta$ that is unknown and must be estimated: $T_t = T_t(\theta)$, $Z_t = Z_t(\theta)$, etc. This dependency is the entire reason the Kalman filter is embedded inside an optimization loop — each candidate $\theta$ produces a different filtered path and a different likelihood value.

### The Prediction-Error Decomposition

The joint density of the observations $y_1, \ldots, y_n$ factors via the chain rule of probability into a product of conditional densities:

$$L(\theta) = p(y_1, \ldots, y_n \mid \theta) = \prod_{t=1}^{n} p(y_t \mid y_1, \ldots, y_{t-1}, \theta)$$

Under the linear Gaussian assumptions, each conditional distribution $y_t \mid y_1, \ldots, y_{t-1}$ is itself Gaussian, with mean and variance produced directly as byproducts of the Kalman filter's prediction step:

$$y_t \mid Y_{t-1} \sim N(Z_t a_{t|t-1}, F_t)$$

where $a_{t|t-1}$ is the predicted state and $F_t = Z_t P_{t|t-1} Z_t' + H_t$ is the prediction-error variance, with $P_{t|t-1}$ the predicted state covariance. Define the prediction error (innovation) as:

$$v_t = y_t - Z_t a_{t|t-1}$$

This is precisely the [Confirmed] **innovations representation** used elsewhere in state-space theory. The log-likelihood follows immediately:

$$\log L(\theta) = -\frac{Nn}{2}\log(2\pi) - \frac{1}{2}\sum_{t=1}^{n} \log|F_t| - \frac{1}{2}\sum_{t=1}^{n} v_t' F_t^{-1} v_t$$

where $N$ is the dimension of $y_t$. This is the **prediction-error decomposition** (Schweppe, 1965; Harvey, 1989). It is the standard route to likelihood evaluation for any linear Gaussian state-space model, including ARIMA, unobserved-components, and dynamic factor models cast in state-space form.

### Kalman Filter Recursions Supporting the Likelihood

For each $t = 1, \ldots, n$, given $a_{t-1}$, $P_{t-1}$ from the previous step:

**Prediction step:**

$$a_{t|t-1} = T_t a_{t-1} + c_t$$



$$P_{t|t-1} = T_t P_{t-1} T_t' + R_t Q_t R_t'$$

**Innovation:**

$$v_t = y_t - Z_t a_{t|t-1} - d_t$$



$$F_t = Z_t P_{t|t-1} Z_t' + H_t$$

**Update (filtering) step:**

$$K_t = P_{t|t-1} Z_t' F_t^{-1}$$



$$a_t = a_{t|t-1} + K_t v_t$$



$$P_t = P_{t|t-1} - K_t Z_t P_{t|t-1}$$

$K_t$ is the Kalman gain. Each iteration contributes exactly one term $\log|F_t| + v_t' F_t^{-1} v_t$ to the log-likelihood sum, so a single forward pass of the filter both estimates the states and evaluates the likelihood simultaneously — no separate computation is required.

### Initialization of the Filter

The recursion requires a starting point $a_0, P_0$ (or equivalently $a_{1|0}, P_{1|0}$). Three standard approaches exist:

- **Stationary initialization**: for a covariance-stationary state process, $a_0 = 0$ (or the unconditional mean) and $P_0$ solves the discrete Lyapunov equation $P_0 = T P_0 T' + RQR'$. [Confirmed] This is exact and appropriate for stable ARMA-type state vectors.
- **Diffuse initialization**: for nonstationary components (e.g., random walk trends, unit roots), $P_0$ is set to $\kappa I$ for very large $\kappa$, approximating an improper diffuse prior. This is a practical approximation; the **exact diffuse initialization** (de Jong, 1991; Durbin & Koopman, 2012) avoids numerical problems from large $\kappa$ by treating the diffuse and proper parts of the state separately with a modified likelihood formula.
- **Fixed/known initialization**: when theory specifies $a_0, P_0$ (e.g., a known steady state).

[Inference] The choice of initialization can materially affect small-sample parameter estimates for models with near-unit-root dynamics, since the first few diffuse observations contribute no informative likelihood terms under exact diffuse treatment, effectively reducing the usable sample size for those components.

### Numerical Optimization of the Likelihood

Because $\log L(\theta)$ has no closed form as a function of $\theta$ in general (except in special cases like local level models with known signal-to-noise ratio), estimation requires numerical maximization:

$$\hat{\theta} = \arg\max_{\theta} \log L(\theta)$$

Common approaches:

- **Direct numerical optimization**: gradient-based methods (BFGS, L-BFGS, Newton-Raphson) or gradient-free methods (Nelder-Mead) applied directly to the Kalman-filter-evaluated log-likelihood, treating it as a black-box function of $\theta$.
- **Scoring/EM algorithms**: the EM algorithm (Shumway & Stoffer, 1982) alternates an E-step (running the Kalman filter and a backward smoother to get expected sufficient statistics) with an M-step (closed-form or simple updates of $T, Z, Q, H$ given those statistics). [Confirmed] EM tends to be numerically stable and forgiving of poor starting values, but converges more slowly (linearly) than Newton-type methods near the optimum.
- **Analytical/numerical gradients**: the score can be computed via the derivative of the Kalman recursions with respect to $\theta$ (via the information matrix or numerical differencing), improving convergence speed of quasi-Newton methods.

**Practical considerations:**

- Variance parameters ($Q$, $H$ entries) must remain positive (semi-)definite. Standard practice reparameterizes via log-variances or Cholesky factors to enforce this unconstrained during optimization.
- Multiple starting values are recommended because the likelihood surface can be multimodal, particularly for models with variance components near the boundary of the parameter space (a known issue in unobserved-components and structural time series models).
- Concentrating out a scale parameter — if one variance can be factored out of $H$ and $Q$ collectively — reduces the dimension of the numerical search and often improves stability. [Confirmed] This is standard in many local-level and structural time series implementations.

### Concentrated (Profile) Likelihood

When a common scale factor $\sigma^2$ multiplies all disturbance covariances ($Q = \sigma^2 \tilde{Q}$, $H = \sigma^2 \tilde{H}$), $F_t = \sigma^2 \tilde{F}_t$ and $\sigma^2$ can be concentrated out analytically:

$$\hat{\sigma}^2 = \frac{1}{n}\sum_{t=1}^{n} \frac{v_t^2}{\tilde{F}_t}$$

Substituting back yields a **concentrated log-likelihood** as a function of the remaining parameters only, reducing the dimensionality of the numerical optimization problem by one — often improving both speed and convergence reliability.

### Asymptotic Properties and Inference

Under standard regularity conditions (correct specification, stationarity or appropriate handling of nonstationary components, identifiability), the Gaussian MLE $\hat\theta$ is [Confirmed] consistent and asymptotically normal:

$$\sqrt{n}(\hat\theta - \theta_0) \xrightarrow{d} N(0, \mathcal{I}(\theta_0)^{-1})$$

where $\mathcal{I}(\theta_0)$ is the (asymptotic per-observation) Fisher information matrix, typically estimated by the observed information (negative Hessian of the log-likelihood at $\hat\theta$) or the outer-product-of-gradients (OPG) estimator. Standard errors for $\hat\theta$ are obtained from the square roots of the diagonal of this inverse information matrix.

[Inference] When the true data-generating process is not exactly Gaussian, the same estimator is often interpreted as a **Quasi-Maximum Likelihood Estimator (QMLE)**: it remains consistent for the parameters governing the first two conditional moments, but valid inference then requires the sandwich (robust) covariance estimator $\mathcal{I}^{-1} \mathcal{J} \mathcal{I}^{-1}$, where $\mathcal{J}$ is the outer-product-of-score covariance, since the information matrix equality no longer holds.

### Worked Example: Local Level Model

Consider the simplest unobserved-components model:

$$y_t = \mu_t + \varepsilon_t, \quad \varepsilon_t \sim N(0, \sigma_\varepsilon^2)$$



$$\mu_t = \mu_{t-1} + \eta_t, \quad \eta_t \sim N(0, \sigma_\eta^2)$$

Here $\theta = (\sigma_\varepsilon^2, \sigma_\eta^2)$, $T_t = 1$, $Z_t = 1$, $Q_t = \sigma_\eta^2$, $H_t = \sigma_\varepsilon^2$. The Kalman filter reduces to scalar recursions:

$$P_{t|t-1} = P_{t-1} + \sigma_\eta^2, \quad F_t = P_{t|t-1} + \sigma_\varepsilon^2$$



$$K_t = P_{t|t-1}/F_t, \quad a_t = a_{t|t-1} + K_t v_t, \quad P_t = P_{t|t-1}(1 - K_t)$$

**Example** (numerical procedure):

1. Fix candidate $(\sigma_\varepsilon^2, \sigma_\eta^2)$.
2. Initialize $a_0 = y_1$ (or diffuse), $P_0$ large.
3. Run the filter forward through $t=1,\ldots,n$, accumulating $\sum \log F_t$ and $\sum v_t^2/F_t$.
4. Compute $\log L(\theta)$ via the prediction-error decomposition formula.
5. Pass $-\log L(\theta)$ to a numerical minimizer (e.g., BFGS); repeat steps 1–4 at each proposed $\theta$ until convergence.
6. The ratio $q = \sigma_\eta^2/\sigma_\varepsilon^2$ (signal-to-noise ratio) is the economically interpretable quantity: $q \to 0$ implies $\mu_t$ is nearly a deterministic constant, while large $q$ implies $y_t$ is close to a pure random walk.

### Algorithm Flow Diagram

```mermaid
flowchart TD
    A[Candidate parameter vector theta] --> B[Set system matrices T Z Q H R]
    B --> C[Initialize state a0 P0]
    C --> D[Kalman filter forward pass t = 1 to n]
    D --> E[Prediction step: a_t|t-1, P_t|t-1]
    E --> F[Innovation: v_t, F_t]
    F --> G[Update step: a_t, P_t]
    G --> H{t < n?}
    H -- Yes --> E
    H -- No --> I[Accumulate log L theta via prediction error decomposition]
    I --> J[Numerical optimizer proposes new theta]
    J --> B
    I --> K{Converged?}
    K -- No --> J
    K -- Yes --> L[theta_hat MLE and standard errors from Hessian or OPG]
```

### Filter-Likelihood Data Flow (SVG)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 340">
<text x="400" y="25" font-size="16" font-weight="bold" text-anchor="middle" fill="#1a1a1a">Kalman Filter → Likelihood Pipeline (svg_diagram)</text>
<rect x="30" y="60" width="150" height="60" rx="6" fill="#e3f2fd" stroke="#1565c0" />
<text x="105" y="85" font-size="12" text-anchor="middle" fill="#1a1a1a">Parameters</text>
<text x="105" y="102" font-size="12" text-anchor="middle" fill="#1a1a1a">theta</text>
<rect x="230" y="60" width="150" height="60" rx="6" fill="#e8f5e9" stroke="#2e7d32" />
<text x="305" y="85" font-size="12" text-anchor="middle" fill="#1a1a1a">Prediction</text>
<text x="305" y="102" font-size="12" text-anchor="middle" fill="#1a1a1a">a(t|t-1), P(t|t-1)</text>
<rect x="430" y="60" width="150" height="60" rx="6" fill="#fff3e0" stroke="#e65100" />
<text x="505" y="85" font-size="12" text-anchor="middle" fill="#1a1a1a">Innovation</text>
<text x="505" y="102" font-size="12" text-anchor="middle" fill="#1a1a1a">v(t), F(t)</text>
<rect x="630" y="60" width="150" height="60" rx="6" fill="#fce4ec" stroke="#ad1457" />
<text x="705" y="85" font-size="12" text-anchor="middle" fill="#1a1a1a">Update</text>
<text x="705" y="102" font-size="12" text-anchor="middle" fill="#1a1a1a">a(t), P(t)</text>
<line x1="180" y1="90" x2="230" y2="90" stroke="#555" stroke-width="2" marker-end="url(#arrow)" />
<line x1="380" y1="90" x2="430" y2="90" stroke="#555" stroke-width="2" marker-end="url(#arrow)" />
<line x1="580" y1="90" x2="630" y2="90" stroke="#555" stroke-width="2" marker-end="url(#arrow)" />
<path d="M 705 120 C 705 160 305 160 305 120" fill="none" stroke="#555" stroke-width="2" stroke-dasharray="4,2" marker-end="url(#arrow)" />
<text x="505" y="150" font-size="11" text-anchor="middle" fill="#555">recurse t = 1..n</text>
<rect x="230" y="200" width="350" height="60" rx="6" fill="#ede7f6" stroke="#4527a0" />
<text x="405" y="225" font-size="12" text-anchor="middle" fill="#1a1a1a">Accumulate log L(theta) =</text>
<text x="405" y="242" font-size="11" text-anchor="middle" fill="#1a1a1a">-1/2 sum[log F(t) + v(t)^2/F(t)]</text>
<line x1="505" y1="120" x2="405" y2="200" stroke="#555" stroke-width="2" marker-end="url(#arrow)" />
<rect x="230" y="290" width="350" height="40" rx="6" fill="#f1f8e9" stroke="#33691e" />
<text x="405" y="315" font-size="12" text-anchor="middle" fill="#1a1a1a">Optimizer updates theta; repeat until convergence</text>
<line x1="405" y1="260" x2="405" y2="290" stroke="#555" stroke-width="2" marker-end="url(#arrow)" />
<path d="M 230 310 C 100 310 100 90 30 90" fill="none" stroke="#555" stroke-width="2" stroke-dasharray="4,2" marker-end="url(#arrow)" />
</svg>

### Common Pitfalls

- **Ignoring the diffuse likelihood correction**: using the standard (non-diffuse) prediction-error decomposition on the initial observations of a model with nonstationary states biases the likelihood and resulting parameter estimates.
- **Boundary solutions**: variance estimates collapsing to zero (e.g., $\hat\sigma_\eta^2 = 0$ in the local level model, implying a deterministic trend) are common in small samples and are a legitimate MLE outcome, not necessarily a numerical failure — but they flag potential model misspecification or weak identification.
- **Local optima**: multimodal likelihood surfaces in richer models (e.g., structural time series with seasonal and cycle components) make starting-value sensitivity a real practical risk; multiple restarts or EM-based pre-optimization mitigates this.
- **Confusing filtered with smoothed likelihood contributions**: only the *filtering* (one-sided) recursions enter the likelihood; the backward *smoother* is used for state estimation and EM E-steps, not for likelihood evaluation itself.

**Related Topics**

- Kalman smoother and fixed-interval smoothing (Rauch-Tung-Striebel algorithm)
- EM algorithm for state-space parameter estimation
- Exact diffuse initialization (de Jong / Durbin-Koopman approach)
- Extended and unscented Kalman filters for nonlinear state-space MLE
- Quasi-maximum likelihood and sandwich covariance estimation
- Structural time series models (local level, local linear trend, seasonal components)
- State-space representation of ARIMA models
- Missing data handling within the Kalman filter recursions
- Simulation smoothing for Bayesian state-space estimation (Gibbs sampling with Kalman filter/smoother)