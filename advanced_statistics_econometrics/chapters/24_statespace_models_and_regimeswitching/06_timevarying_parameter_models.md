## Time-Varying Parameter Models


### Overview

Time-varying parameter (TVP) models relax the standard regression assumption of constant coefficients by allowing them to evolve over time according to a stochastic process. Rather than treating parameter instability as a nuisance to be tested away, TVP models embed the evolution directly into the model specification, typically cast as a state-space system and estimated via the Kalman filter. They are widely used in macroeconomics and finance to capture gradual structural change — evolving monetary policy rules, time-varying risk premia, or drifting Phillips curve slopes — without imposing discrete break dates.

### General Specification

The canonical TVP regression model is:

$$y_t = x_t' \beta_t + \varepsilon_t, \quad \varepsilon_t \sim N(0, \sigma_\varepsilon^2)$$



$$\beta_t = \beta_{t-1} + \eta_t, \quad \eta_t \sim N(0, Q)$$

where $x_t$ is a vector of regressors, $\beta_t$ is the (now time-indexed) coefficient vector, and the coefficient evolution follows a **random walk**. This is a linear Gaussian state-space model with $\beta_t$ as the state vector, $Z_t = x_t'$, $T_t = I$, $H_t = \sigma_\varepsilon^2$, and $R_t Q_t R_t' = Q$, making it directly estimable via the Kalman filter and the prediction-error decomposition for maximum likelihood estimation of $(\sigma_\varepsilon^2, Q)$.

### Alternative Coefficient Evolution Processes

The random walk is the most common but not the only specification for $\beta_t$:

- **Random walk** (as above): $\beta_t = \beta_{t-1} + \eta_t$. Nonstationary; coefficients can drift arbitrarily far over long samples. Standard default when no mean-reverting economic rationale exists.
- **Mean-reverting (stationary AR(1)) coefficients**: $\beta_t - \bar\beta = \Phi(\beta_{t-1} - \bar\beta) + \eta_t$ with eigenvalues of $\Phi$ inside the unit circle. Appropriate when coefficients are believed to fluctuate around a stable long-run value rather than drift permanently.
- **Random coefficient models** (Hildreth-Houck, 1968): $\beta_t = \bar\beta + \eta_t$, i.e., coefficients vary independently around a fixed mean with no persistence — a special, degenerate case rarely used alone in modern practice but historically important as a precursor.
- **Markov-switching coefficients**: coefficients take one of a finite number of discrete values governed by a latent Markov chain (connecting directly to Markov-switching models), representing an alternative, non-smooth form of "time variation."
- **Smoothly time-varying via kernel or spline methods**: nonparametric alternatives (e.g., local likelihood, kernel-weighted least squares) that avoid the state-space/Gaussian machinery entirely, trading a fully specified law of motion for flexibility and reduced parametric assumptions.

### Estimation via Kalman Filter and MLE

Because the model is linear and Gaussian, estimation proceeds exactly as in the general Kalman filter MLE framework:

1. Concentrate the model into state-space form with $\beta_t$ as the state.
2. Choose an initialization for $\beta_0$: either a diffuse prior (if no information is available) or an informative prior (e.g., OLS estimates from a pre-sample or training period).
3. Run the Kalman filter forward, accumulating the log-likelihood via the prediction-error decomposition:

$$\log L(\theta) = -\frac{n}{2}\log(2\pi) - \frac{1}{2}\sum_t \log F_t - \frac{1}{2}\sum_t \frac{v_t^2}{F_t}$$

4. Numerically maximize over $\theta = (\sigma_\varepsilon^2, Q)$, typically reparameterizing variances to ensure positivity.
5. Run the Kalman smoother to obtain full-sample estimates $\hat\beta_{t|n}$ of the coefficient path, which is usually the object of primary economic interest (e.g., "how has the Fed's response to inflation changed over time?").

[Confirmed] A key practical device is the **signal-to-noise ratio** $q_k = Q_{kk}/\sigma_\varepsilon^2$ for each coefficient: small $q_k$ implies the coefficient is estimated as nearly constant (approaching the fixed-coefficient OLS/GLS case as $q_k \to 0$), while larger $q_k$ permits substantial drift. Estimating $Q$ via MLE lets the data determine how much time variation is warranted, rather than imposing it by assumption.

### The TVP-VAR Framework

A major applied extension is the **time-varying parameter VAR** (Cogley & Sargent, 2001, 2005; Primiceri, 2005), widely used for macroeconomic structural analysis:

$$y_t = c_t + B_{1,t} y_{t-1} + \cdots + B_{p,t} y_{t-p} + u_t, \quad u_t \sim N(0, \Sigma_t)$$

with the stacked VAR coefficients $\theta_t = \text{vec}(c_t, B_{1,t}, \ldots, B_{p,t})$ following a random walk:

$$\theta_t = \theta_{t-1} + \eta_t, \quad \eta_t \sim N(0, Q)$$

Primiceri's (2005) influential specification additionally allows the error covariance $\Sigma_t$ itself to be time-varying, decomposed as $\Sigma_t = A_t^{-1} H_t (A_t^{-1})'$, where $A_t$ is a lower-triangular matrix of time-varying contemporaneous coefficients (also following a random walk in its free elements) and $H_t$ is a diagonal matrix of time-varying stochastic volatilities. This combination — time-varying coefficients **and** time-varying (stochastic) volatility — makes the joint model conditionally non-Gaussian and non-linear in a way that precludes the standard Kalman filter alone, so estimation moves to Bayesian MCMC.

### Bayesian Estimation via Gibbs Sampling

Because TVP-VAR-SV models are not Gaussian linear systems overall (the volatility block is nonlinear), the dominant estimation approach in the applied macro literature is Bayesian, using a Gibbs sampler that alternates:

1. **Draw $\theta_t$ path** given $\Sigma_t$ (or $A_t, H_t$), data, and hyperparameters — conditional on the volatility block, the coefficient block is linear/Gaussian, so this step uses the standard **simulation smoother** (Carter & Kohn, 1994; Durbin & Koopman, 2002), a stochastic extension of the Kalman smoother that draws from the full joint posterior of the state path rather than just its mean.
2. **Draw stochastic volatility parameters** given $\theta_t$ — typically via the mixture-of-normals approximation (Kim, Shephard & Chib, 1998) that linearizes the log-volatility measurement equation, or via more modern particle-based/MCMC methods for stochastic volatility.
3. **Draw hyperparameters** ($Q$ and volatility innovation variances) from their conditional posteriors, usually inverse-Wishart or inverse-gamma given conjugate priors.
4. Iterate until the chain converges; discard burn-in draws and use the retained draws for posterior inference on $\theta_t$, impulse responses, and other quantities of interest.

[Confirmed] This is standard practice in the empirical macro literature (e.g., time-varying monetary policy transmission, evolving inflation persistence) precisely because closed-form or single-pass MLE is infeasible once stochastic volatility is added to time-varying coefficients.

### Practical Example: Time-Varying Taylor Rule

**Example**: a widely cited TVP application estimates a Taylor-rule-type monetary policy reaction function with drifting coefficients:

$$i_t = \beta_{0,t} + \beta_{\pi,t}\pi_t + \beta_{y,t} y_t^{gap} + \varepsilon_t$$



$$\beta_t = \beta_{t-1} + \eta_t$$

where $i_t$ is the policy rate, $\pi_t$ inflation, and $y_t^{gap}$ the output gap. Applied studies in this tradition have used such specifications to argue that the estimated responsiveness to inflation, $\beta_{\pi,t}$, was markedly weaker in pre-1980s U.S. data than in the post-Volcker period — a central piece of evidence in debates over whether "good luck" (smaller shocks) or "good policy" (a stronger anti-inflation response) explains the Great Moderation. [Unverified] The magnitude and even the sign of such findings are sensitive to sample period, prior choice for $Q$, and whether volatility is jointly modeled as time-varying — this is an actively contested area rather than a settled numerical result, and specific coefficient values should be pulled from the specific paper/vintage being cited rather than treated as a fixed stylized fact.

### State-Space Flow for TVP Estimation

```mermaid
flowchart TD
    A[Specify coefficient law of motion: random walk or AR] --> B[Cast as state-space system: beta_t as state]
    B --> C[Kalman filter forward pass]
    C --> D[Prediction error decomposition: accumulate log L]
    D --> E{Gaussian and linear only?}
    E -- Yes --> F[MLE via numerical optimizer over sigma_eps^2 and Q]
    E -- No, e.g. stochastic volatility --> G[Bayesian Gibbs sampler: simulation smoother plus SV block]
    F --> H[Kalman smoother: full-sample beta_t|n path]
    G --> I[Posterior draws of beta_t path and volatility]
    H --> J[Interpret time-varying coefficient path]
    I --> J
```

### Signal-to-Noise Ratio and Coefficient Smoothness (SVG)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 780 300">
<text x="390" y="25" font-size="16" font-weight="bold" text-anchor="middle" fill="#1a1a1a">Signal-to-Noise Ratio and Coefficient Paths (svg_diagram)</text>
<line x1="60" y1="260" x2="740" y2="260" stroke="#333" stroke-width="1.5" />
<line x1="60" y1="260" x2="60" y2="60" stroke="#333" stroke-width="1.5" />
<text x="400" y="285" font-size="12" text-anchor="middle" fill="#1a1a1a">time</text>
<text x="30" y="160" font-size="12" text-anchor="middle" fill="#1a1a1a" transform="rotate(-90 30 160)">beta_t</text>
<polyline points="60,150 150,150 250,150 350,150 450,150 550,150 650,150 740,150" fill="none" stroke="#1565c0" stroke-width="2.5" />
<text x="150" y="135" font-size="11" fill="#1565c0">q -&gt; 0 (near-constant OLS)</text>
<polyline points="60,200 150,190 250,150 350,110 450,140 550,90 650,120 740,80" fill="none" stroke="#e65100" stroke-width="2.5" />
<text x="500" y="70" font-size="11" fill="#e65100">large q (substantial drift)</text>
<polyline points="60,175 150,178 250,165 350,172 450,160 550,168 650,155 740,162" fill="none" stroke="#2e7d32" stroke-width="2.5" stroke-dasharray="5,3" />
<text x="150" y="195" font-size="11" fill="#2e7d32">moderate q (smooth drift)</text>
</svg>

### Testing for Time Variation

Before committing to a fully time-varying specification, applied work often tests whether coefficients are constant:

- **Nyblom (1989) test**: tests the null hypothesis $Q = 0$ (parameter constancy) against the alternative of a random-walk-varying parameter, using an LM-type statistic based on cumulated score contributions. [Confirmed] This is the standard parametric test directly nested within the TVP random-walk framework.
- **Rolling-window / recursive OLS**: an informal, non-model-based diagnostic — re-estimating fixed-coefficient regressions over rolling or expanding windows and visually inspecting coefficient stability. Useful for exploratory analysis but lacks the formal likelihood-based footing of the state-space approach.
- **CUSUM and CUSUM-of-squares tests**: detect general parameter instability (not necessarily smooth drift) and are complementary diagnostics run alongside or instead of a full TVP specification.

### Common Pitfalls

- **Overfitting via excessive $Q$**: an unconstrained $Q$ estimated by MLE can sometimes drive coefficients to track noise in the data rather than genuine structural change, especially in short samples; informative priors (in a Bayesian setting) or Nyblom-type pre-testing help guard against this.
- **Confusing TVP with stochastic volatility**: allowing only $\sigma_\varepsilon^2$ (the observation-equation variance) to vary while holding $\beta_t$ fixed is a **stochastic volatility** model, not a TVP model in the coefficient sense — the two are often combined but are conceptually distinct sources of time variation.
- **Diffuse initialization sensitivity**: because $\beta_t$ is often modeled as a nonstationary random walk, the choice of diffuse vs. informative prior for $\beta_0$ can materially affect early-sample smoothed estimates; exact diffuse initialization techniques are recommended over ad hoc large-variance approximations.
- **Interpreting smoothed vs. filtered coefficient paths**: real-time policy analysis should use the one-sided filtered path $\hat\beta_{t|t}$ (information available at the time), while retrospective/historical analysis should use the full-sample smoothed path $\hat\beta_{t|n}$; conflating the two produces look-ahead bias in real-time forecasting claims.

**Related Topics**

- Kalman filter and MLE via the prediction-error decomposition
- TVP-VAR with stochastic volatility (Primiceri, 2005) and impulse response analysis
- Simulation smoothing (Carter-Kohn, Durbin-Koopman) for Bayesian state-space models
- Stochastic volatility models and the Kim-Shephard-Chib mixture approximation
- Nyblom stability test and other parameter-constancy diagnostics
- Markov-switching models as a discrete alternative to smooth time variation
- Rolling-window and recursive estimation as informal instability diagnostics
- Great Moderation debates and time-varying monetary policy rules