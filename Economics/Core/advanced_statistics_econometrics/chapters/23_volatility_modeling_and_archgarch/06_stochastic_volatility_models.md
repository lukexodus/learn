## Stochastic Volatility Models


### Conceptual Foundation

Stochastic volatility (SV) models represent an alternative class of time-varying variance models in which the conditional variance is itself driven by its own latent stochastic (random) process, rather than being a deterministic function of past observable returns and past variances as in GARCH-family models. In GARCH, $\sigma_t^2$ is fully determined (given parameters) by the observed history $\{\varepsilon_{t-1}, \varepsilon_{t-2}, \dots\}$; in SV models, volatility follows its own separate, unobserved (latent) stochastic process with its own innovation term, making the model genuinely a two-source-of-randomness system — one shock driving returns, a separate (though often correlated) shock driving volatility.

### The Basic SV Model Specification

The canonical discrete-time SV model (Taylor, 1982, 1986) is typically written as:

$$r_t = \mu + \varepsilon_t, \quad \varepsilon_t = \exp(h_t/2)\, z_t, \quad z_t \overset{\text{i.i.d.}}{\sim} N(0,1)$$



$$h_t = \phi_0 + \phi_1 h_{t-1} + \eta_t, \quad \eta_t \overset{\text{i.i.d.}}{\sim} N(0, \sigma_\eta^2)$$

where $h_t = \ln(\sigma_t^2)$ is the log-volatility, following its own autoregressive process driven by an independent (or correlated, in the "leverage SV" extension) innovation $\eta_t$.

**Key Points**

- $|\phi_1| < 1$ ensures the log-volatility process is stationary, with $h_t$ mean-reverting to $\phi_0/(1-\phi_1)$.
- $\sigma_\eta^2$ (the "volatility of volatility") governs how much the latent log-variance itself fluctuates randomly, independent of the observed return innovations — this is the fundamental structural difference from GARCH, where volatility evolves deterministically given past data.
- When $\eta_t$ and $z_t$ are allowed to be correlated (typically negatively, $\text{Corr}(\eta_t, z_{t}) = \rho < 0$), the model captures a leverage-effect-like asymmetry analogous to EGARCH/GJR-GARCH, often termed the "leverage SV" model.

### SV vs. GARCH: The Fundamental Distinction

| Aspect | GARCH | Stochastic Volatility |
| --- | --- | --- |
| Volatility driver | Deterministic function of past observables | Own latent stochastic process, separate innovation |
| Number of shock sources | One (return innovation only) | Two (return innovation + volatility innovation) |
| Likelihood computation | Closed-form, direct recursive evaluation | Requires integrating out the latent volatility path — no closed form |
| Estimation complexity | Standard numerical MLE | Simulation-based (MCMC, particle filtering, simulated MLE, or efficient method of moments) |
| Conceptual link to continuous-time finance | Less direct | Natural discrete-time analogue of continuous-time SV models (e.g., Heston model) used in option pricing |

**Key Points**

- Because $\sigma_t^2$ in a GARCH model is a deterministic function of the observed history through time $t-1$, the GARCH likelihood is computable in closed form via direct recursive substitution — this tractability is a major practical advantage over SV models.
- In SV models, the conditional variance $h_t$ is unobserved (latent) and its own innovation $\eta_t$ is not directly identified from the return data alone, meaning the likelihood requires integrating over all possible latent volatility paths — a high-dimensional integral with no closed-form solution, historically the primary obstacle to SV model estimation.
- SV models are widely viewed as the natural discrete-time counterpart to continuous-time stochastic volatility models used extensively in derivatives pricing (e.g., the Heston (1993) model), giving SV a particularly strong theoretical connection to option pricing and continuous-time finance, distinct from GARCH's more purely time-series-econometric origins.

### Estimation Approaches

**Quasi-Maximum Likelihood via Kalman Filter (QML)**: By taking $\ln(\varepsilon_t^2) = h_t + \ln(z_t^2)$, the model can be cast into a linear (though non-Gaussian, since $\ln(z_t^2)$ is not normal even if $z_t$ is) state-space form, allowing an approximate Kalman filter to be applied by treating $\ln(z_t^2)$ as approximately Gaussian (Harvey, Ruiz, and Shephard, 1994). This provides a computationally simple, though only approximately efficient, estimation route.

**Simulated Maximum Likelihood (SML)**: Uses Monte Carlo simulation (e.g., importance sampling, as in Durbin and Koopman, 1997) to approximate the intractable likelihood integral directly, achieving higher efficiency than the QML/Kalman-filter approximation at greater computational cost.

**Markov Chain Monte Carlo (MCMC) / Bayesian estimation**: The dominant modern approach (Jacquier, Polson, and Rossi, 1994; Kim, Shephard, and Chib, 1998), treating the entire latent volatility path $\{h_1, \dots, h_T\}$ as additional parameters to be sampled jointly with the model's structural parameters via Gibbs sampling or related MCMC algorithms, conditional on the observed returns.

**Particle filtering / Sequential Monte Carlo**: Used particularly for online/real-time filtering of the latent volatility state and for models with more complex nonlinear or non-Gaussian structure than the basic log-normal SV model accommodates well.

**Efficient Method of Moments (EMM)** (Gallant and Tauchen, 1996): An indirect inference approach matching moments implied by an auxiliary (easier-to-estimate) model to the SV model's simulated moments.

### Practical Estimation Workflow (MCMC/Bayesian)

**Example**

Step 1: Specify priors for the SV parameters $(\phi_0, \phi_1, \sigma_\eta^2)$ (and correlation $\rho$ if using the leverage SV extension), typically weakly informative priors consistent with stationarity ($|\phi_1|<1$) and positive $\sigma_\eta^2$.

Step 2: Initialize the latent log-volatility path $\{h_1, \dots, h_T\}$, often via a simple proxy such as a rolling-window log squared return.

Step 3: Iterate a Gibbs sampling (or related MCMC) scheme: (a) sample each $h_t$ (or blocks of $h_t$) conditional on the data, neighboring $h_{t-1}, h_{t+1}$, and current parameter values; (b) sample the structural parameters $(\phi_0, \phi_1, \sigma_\eta^2)$ conditional on the current draw of the full latent path.

Step 4: Discard an initial "burn-in" period of draws and retain the remaining posterior draws as the basis for inference (posterior means/medians for point estimates, credible intervals for uncertainty).

Step 5: Use the posterior distribution of $\{h_t\}$ as the estimated (smoothed) volatility path, and posterior predictive simulation for volatility forecasting.

**Output**

A typical fitted SV model on daily equity returns might yield $\hat{\phi}_1$ (log-volatility persistence) in the range of roughly 0.95–0.99 (high persistence, broadly comparable in spirit to $\alpha_1+\beta_1$ in GARCH), with the posterior mean volatility path showing similar broad clustering patterns to a comparably fitted GARCH(1,1), though SV-implied volatility paths are often noted to be somewhat smoother due to the model's separate volatility innovation averaging out some of the noise directly tied to return realizations. [Inference: the relative smoothness and precise persistence estimates are model- and dataset-specific; this is a commonly noted qualitative comparison in the literature rather than a universal quantitative result.]

### Realized Volatility and SV: A Complementary Connection

**Key Points**

- High-frequency-based realized volatility measures (sums of squared intraday returns) provide a direct, model-free empirical proxy for the latent "true" volatility that SV models seek to describe, and are frequently used both as an input to (realized SV models, e.g., Takahashi, Omori, and Watanabe, 2009) and a validation benchmark for SV (and GARCH) model forecasts.
- This connection strengthens SV's conceptual appeal as modeling volatility as a genuinely separate underlying stochastic quantity, consistent with how realized volatility measures reveal volatility as an object with its own observable (at high frequency) dynamics.

### Advantages and Disadvantages Relative to GARCH

**Key Points**

- **Advantage**: The additional volatility-specific innovation often provides a more flexible and, in some studies, better-fitting description of the "excess" randomness in volatility beyond what is mechanically implied by past squared returns, and aligns naturally with continuous-time option-pricing theory.
- **Advantage**: SV models in continuous-time form underlie widely used option pricing frameworks (Heston model and extensions), making SV a natural bridge between time-series volatility modeling and derivatives pricing applications.
- **Disadvantage**: Substantially more complex estimation (simulation-based methods, MCMC convergence diagnostics, computational cost) relative to GARCH's straightforward closed-form MLE, which has historically limited SV's adoption in routine applied risk management relative to GARCH's ubiquity.
- **Disadvantage**: Real-time/sequential updating (e.g., daily risk management production systems) is comparatively more involved for SV given the need for filtering/re-estimation of the latent path, whereas GARCH's deterministic recursive variance update is trivially updated with each new observation.
- [Inference: empirical comparisons of SV versus GARCH forecasting performance show mixed results across studies and asset classes, with neither model class uniformly dominating; the choice in practice often reflects a trade-off between GARCH's computational simplicity/ubiquity and SV's theoretical flexibility and continuous-time consistency.]

### Common Pitfalls

- **Underestimating computational/implementation burden**: Researchers accustomed to GARCH's direct MLE may underestimate the substantially greater implementation complexity (MCMC convergence checking, mixing diagnostics, computational time) required for credible SV estimation.
- **Ignoring MCMC convergence diagnostics**: Reporting posterior estimates without checking chain convergence (trace plots, Gelman-Rubin statistics, effective sample size) can produce unreliable inference, a pitfall specific to the simulation-based estimation SV models require.
- **Treating QML/Kalman-filter estimates as fully efficient**: The Harvey-Ruiz-Shephard approach is a useful approximation but is known to be less efficient than full simulation-based (MCMC or SML) estimation; results should be interpreted with this caveat, particularly in smaller samples.
- **Confusing SV's latent volatility path with a directly observed quantity**: Unlike GARCH's fully determined $\sigma_t^2$, SV's $h_t$ is an estimated/inferred latent state with genuine posterior uncertainty that should be reported and considered in downstream applications (e.g., risk management), not treated as a point-certain input.

### SV Model Structure Diagram

```mermaid
flowchart TD
    subgraph sv_model_structure Stochastic Volatility Model Structure (svg_diagram)
    A["Return equation: r_t = mu + epsilon_t"] --> B["epsilon_t = exp(h_t/2) times z_t"]
    B --> C["z_t iid N(0,1): return innovation"]
    D["Latent log-volatility equation: h_t = phi_0 + phi_1 h_t-1 + eta_t"] --> E["eta_t iid N(0, sigma_eta^2): separate volatility innovation"]
    C -.->|"optional correlation rho, leverage SV"| E
    D --> F["h_t unobserved, must be inferred"]
    F --> G["Likelihood requires integrating over latent path: no closed form"]
    G --> H["Estimation: MCMC / Kalman-QML / Simulated ML / Particle filtering"]
    H --> I["Posterior or estimated smoothed volatility path h_t"]
    end
```

### Software Implementation Notes

- **R**: `stochvol` package (Bayesian MCMC estimation of univariate SV models, including leverage SV), `bsvars`/`stochvolTMB` and related packages for extensions.
- **Python**: SV model support is less standardized than GARCH; implementations are often custom-built using general-purpose probabilistic programming frameworks (e.g., PyMC, Stan via `cmdstanpy`) to specify and sample the state-space SV model directly.
- **Stan/BUGS/JAGS**: Commonly used general-purpose Bayesian modeling languages for implementing custom SV specifications via MCMC, given the lack of as ubiquitous "off-the-shelf" SV support as exists for GARCH.

[Unverified: exact package capabilities, default priors, and sampler algorithms vary by software and version; verify against current documentation before implementation.]

**Related Topics**

- The GARCH model and extensions
- Stylized facts of financial time series
- Realized volatility and high-frequency volatility measures
- Heston model and continuous-time stochastic volatility in option pricing
- Bayesian MCMC estimation methods (Gibbs sampling, Metropolis-Hastings)
- State-space models and the Kalman filter
- Particle filtering and sequential Monte Carlo methods