## Calibration Versus Estimation Approaches

### Overview and Purpose

Once a DSGE model's equilibrium conditions are derived and (log-)linearized or solved via nonlinear methods, its structural parameters — preference parameters, technology parameters, shock persistence and variances, nominal rigidity parameters — must be assigned numerical values before the model can generate quantitative predictions, impulse responses, or forecasts. Two broad methodological traditions accomplish this: **calibration**, which fixes parameters using independent, often microeconomic or steady-state, evidence outside the model's own likelihood; and **estimation**, which infers parameter values from the fit of the model to observed macroeconomic time series, typically via maximum likelihood or Bayesian methods. The choice between them — and increasingly, the hybrid combination of both — shapes what a DSGE model is understood to be doing: a quantitative theory exercise versus a data-fitting/forecasting exercise.

---

### Calibration: Philosophy and Method

Calibration, associated foundationally with Kydland and Prescott's RBC research program, treats the model as a **quantitative theory** to be evaluated by its ability to replicate a *target set of moments* (variances, correlations, relative volatilities) given parameters chosen from sources external to the estimation exercise itself.

**Key Points**

- Parameters are set using **microeconomic evidence, long-run averages, national accounts identities, or steady-state restrictions**, not by maximizing fit to the aggregate time series the model will later be judged against.
- Typical calibration targets:
  - $\beta$ (discount factor) from the average real interest rate: $\beta = \frac{1}{1+\bar{r}}$
  - $\alpha$ (capital share) from labor's share of national income in the data
  - $\delta$ (depreciation rate) from investment-capital ratios or NIPA depreciation data
  - Steady-state hours ($\bar{N} \approx 0.33$ of the time endowment) from time-use survey averages
  - Frisch elasticity of labor supply from micro-panel labor supply studies
- The model is then **simulated** and its second moments (standard deviations, autocorrelations, cross-correlations) are compared to the same moments computed from actual data — this comparison itself is the "test," rather than a formal statistical goodness-of-fit criterion.
- Calibration is philosophically tied to the idea that **a model should not be rejected on statistical grounds** if it captures the qualitative and rough quantitative business cycle facts, since all models are known approximations ("all models are false, some are useful").

**[Inference]** The Kydland-Prescott view that formal econometric testing is largely inappropriate for evaluating a DSGE model is a methodological position that was influential but remains contested; it is best understood as a stance in an ongoing methodological debate rather than a technical consensus.

---

### Estimation: Philosophy and Method

The estimation tradition treats the DSGE model's parameters as objects to be **inferred from the data** using formal statistical/econometric machinery, typically by constructing the model's implied likelihood function over a set of observable time series (output, consumption, investment, hours, inflation, interest rates, wages).

#### Maximum Likelihood Estimation (MLE)

The model is solved (usually via a first-order log-linear approximation) into a linear **state-space form**:

$$s_t = F(\theta) s_{t-1} + G(\theta) \varepsilon_t \quad \text{(transition/state equation)}$$



$$x_t = H(\theta) s_t + u_t \quad \text{(measurement equation)}$$

where $s_t$ is the vector of state variables, $x_t$ the observed data series, $\theta$ the structural parameter vector, and $u_t$ optional measurement error. The **Kalman filter** recursively computes the one-step-ahead prediction errors and their variances, which combine into the Gaussian likelihood $\mathcal{L}(\theta \mid X)$. MLE chooses:

$$\hat{\theta}_{MLE} = \arg\max_{\theta} \; \mathcal{L}(\theta \mid X)$$

**Key Points**

- Pure MLE of full DSGE systems is notoriously difficult: likelihood surfaces are often **flat, multi-modal, or ill-behaved** in directions where parameters are weakly identified, leading to unreliable point estimates and standard errors.
- **[Unverified]** The precise degree of identification failure is model- and dataset-specific; some parameters (e.g., shock persistence in habit formation or price stickiness) are frequently found to be weakly identified in particular applications, but this cannot be asserted as a universal property of all DSGE specifications without checking the specific model's Fisher information matrix or identification diagnostics (e.g., Iskrev's rank conditions, Komunjer-Ng criteria).

#### Bayesian Estimation

The dominant estimation approach in modern practice (An and Schorfheide 2007; Smets and Wouters 2003, 2007). Bayesian estimation combines the likelihood with a **prior distribution** $p(\theta)$ reflecting calibration-style external information, yielding a posterior via Bayes' rule:

$$p(\theta \mid X) \propto \mathcal{L}(X \mid \theta) \cdot p(\theta)$$

Because the posterior has no closed form for nonlinear/nonlinearly-parameterized DSGE likelihoods, it is typically explored via **Markov Chain Monte Carlo (MCMC)**, most commonly the **Random-Walk Metropolis-Hastings (RWMH)** algorithm:

1. Find the posterior mode via numerical optimization (e.g., quasi-Newton), used as the starting point and to compute a proposal covariance from the inverse Hessian.
2. Draw a candidate $\theta'$ from a proposal density (typically $N(\theta_{i-1}, c^2 \Sigma)$ where $\Sigma$ is the mode-Hessian-based covariance and $c$ a tuning scale factor).
3. Accept $\theta'$ with probability $\min\left(1, \frac{p(\theta' \mid X)}{p(\theta_{i-1} \mid X)}\right)$; otherwise retain $\theta_{i-1}$.
4. Iterate for many thousands of draws, discard a "burn-in" sample, and use the retained draws as an approximation to the posterior distribution.

**Key Points**

- Priors serve exactly the role that calibration served in the RBC tradition: they inject external, non-sample information (micro evidence, prior studies, theoretical restrictions like $\alpha, \beta \in (0,1)$) into parameter determination, but do so **probabilistically** rather than by fixing point values.
- Common prior distribution choices reflect parameter support: **Beta** for parameters bounded in $(0,1)$ (e.g., $\theta$ Calvo parameter, $\alpha$ capital share, habit persistence), **Gamma** or **Inverse Gamma** for positive parameters with no natural upper bound (e.g., shock standard deviations, Frisch elasticity inverse), **Normal** for parameters that can take either sign (e.g., Taylor rule response coefficients around a theoretical value).
- Bayesian methods report the full posterior distribution, not just a point estimate — typically summarized by the posterior mean/mode and **90% (or 95%) credible intervals**, along with convergence diagnostics (multiple-chain trace plots, Brooks-Gelman-Rubin statistics).
- The proposal-scale tuning constant $c$ is typically adjusted so the RWMH **acceptance rate falls in roughly the 20–40% range**, a widely used practical heuristic for random-walk MH efficiency in this literature.
- Software: **Dynare** (MATLAB/Octave) is the dominant tool for Bayesian DSGE estimation in academic practice, alongside **IRIS**, **gEcon**, and, increasingly, Python/Julia toolchains (e.g., `dsge.jl`, `gEconpy`).

---

### Calibration Versus Estimation: Structured Comparison

| Dimension | Calibration | Estimation (Bayesian) |
| --- | --- | --- |
| Parameter source | External micro/steady-state evidence | Model fit to aggregate time-series likelihood |
| Uncertainty reporting | Typically none (point values) | Full posterior distributions, credible intervals |
| Model evaluation | Moment-matching, informal comparison | Marginal likelihood / Bayes factors, posterior predictive checks |
| Philosophical stance | Model as quantitative theory | Model as (approximately) data-generating process |
| Sensitivity to misspecification | Explicit — analyst controls parameters directly | Can mask misspecification behind flexible/wide priors |
| Data requirements | Minimal — steady-state and micro data | Full macro time series, often 6–10+ observables |
| Typical era of dominance | RBC literature (1980s–1990s) | NK DSGE literature (2000s–present) |

**[Inference]** The characterization of calibration as an "earlier era" method and Bayesian estimation as "current practice" reflects a broad trend in the published literature but is not a strict chronological rule — many contemporary papers still calibrate a subset of parameters (a hybrid noted below) and pure-calibration RBC papers continue to be published.

---

### Hybrid Practice: Calibrated-and-Estimated Models

In practice, the vast majority of modern medium-scale DSGE papers (the Smets-Wouters lineage being the canonical example) **do not choose purely one approach**. A standard workflow:

1. **Calibrate** parameters that are weakly identified from aggregate time series or better pinned down by steady-state/micro data — e.g., the depreciation rate $\delta$, the government-spending share of GDP, the capital share $\alpha$, and sometimes the discount factor $\beta$.
2. **Estimate** (via Bayesian methods) the parameters governing short-run dynamics and propagation — habit persistence, investment adjustment costs, Calvo price/wage stickiness parameters, Taylor rule coefficients, and the full vector of shock persistence/variance parameters.

This division exists because certain parameters are **not well identified** by the second moments of a handful of observed aggregate series (e.g., $\beta$ and $\delta$ often trade off against each other and against the steady-state great ratios in ways the likelihood cannot cleanly separate), while others (nominal rigidity, adjustment costs) are precisely the "propagation mechanism" parameters that estimation is best suited to recover, since they govern the *dynamic* responses the likelihood is built to fit.

**Example**

In the Smets-Wouters (2007) US model: the capital depreciation rate ($\delta = 0.025$), the steady-state government spending-to-GDP ratio, and several steady-state great ratios are fixed/calibrated, while roughly 30+ parameters — including habit formation, Calvo price/wage stickiness for both prices and wages, indexation parameters, adjustment cost curvature, monetary policy rule coefficients, and the AR(1)/shock-variance parameters for seven structural shocks — are estimated via Bayesian methods using seven US macro time series (output, consumption, investment, hours, wages, inflation, and the federal funds rate).

---

### Model Comparison and Validation Tools

- **Posterior odds / Bayes factors**: comparing two nested or non-nested DSGE specifications by their **marginal data density** (marginal likelihood integrated over the prior), approximated via the modified harmonic mean estimator (Geweke) or bridge sampling.
- **Posterior predictive checks**: simulating data from the estimated posterior and comparing simulated moments/impulse responses to actual data features not directly targeted in estimation.
- **Impulse response matching / SVAR comparison**: comparing DSGE-implied impulse responses to those from a reduced-form (Bayesian) Structural VAR as an informal cross-validation, especially prominent in the DSGE-VAR hybrid literature (Del Negro and Schorfheide).
- **Out-of-sample forecast evaluation**: comparing real-time forecasting performance (root mean squared errors) of the estimated DSGE model against naive benchmarks (random walk, AR models) or against professional forecasters (e.g., Survey of Professional Forecasters) — historically an important practical validation exercise for policy-institution DSGE models (e.g., the Federal Reserve's FRB/US-adjacent and New York Fed DSGE models).

**Behavior may vary** across specific estimation software (Dynare's `estimation` command, gEcon, IRIS) in exact algorithmic defaults (e.g., default RWMH proposal scale, default optimizer for the posterior mode, treatment of stochastic singularity via measurement error) — practitioners should consult the specific toolbox's documentation before interpreting default output as a universal standard.

---

### Common Pitfalls

- **Stochastic singularity**: if the number of observed data series exceeds the number of structural shocks, the model-implied covariance matrix of observables is singular and the likelihood is undefined; standard fixes are adding measurement error or reducing the observable set to match shock count.
- **Weak identification masked by tight priors**: an informative Beta or Gamma prior can make a weakly identified parameter appear to have a sharp posterior purely because the prior itself is tight — not because the data are informative. Identification diagnostics should be checked independently of posterior sharpness.
- **Conflating calibration targets with estimation targets**: using the same aggregate moments both to calibrate certain parameters *and* as observables in the likelihood for others can introduce circularity or double-counting of information; careful separation of the two information sources is standard best practice.
- **Treating Bayesian credible intervals as frequentist confidence intervals**: they answer a different probabilistic question (probability the parameter lies in the interval *given the model, prior, and data*) and should not be interpreted with frequentist coverage guarantees.

---

### Estimation Workflow Diagram

```mermaid
flowchart TD
    A[Specify DSGE model, derive equilibrium conditions] --> B[Log-linearize / solve state-space form]
    B --> C{Calibrate or Estimate?}
    C -->|Calibrate| D[Fix parameters via micro/steady-state evidence]
    C -->|Estimate| E[Specify priors p(theta)]
    E --> F[Construct likelihood via Kalman filter]
    F --> G[Find posterior mode, Hessian]
    G --> H[Run RWMH MCMC chains]
    H --> I[Check convergence diagnostics]
    I --> J[Report posterior mean/mode, credible intervals]
    D --> K[Simulate model, compare moments to data]
    J --> L[Posterior predictive checks, Bayes factors, forecast evaluation]
    K --> L
```

---

**Related Topics**

- Kalman filtering and state-space representation of linearized DSGE models
- Bayesian priors: Beta, Gamma, and Inverse Gamma distribution selection rationale
- Identification problems in DSGE estimation (Canova-Sala, Iskrev diagnostics)
- The Smets-Wouters model architecture and its estimated shock structure
- DSGE-VAR hybrid models and Bayesian model averaging across DSGEs
- Real-time and pseudo-out-of-sample forecasting with estimated DSGE models
- Simulated Method of Moments (SMM) and Generalized Method of Moments (GMM) as alternative estimation strategies
- Perturbation versus projection solution methods and their interaction with estimation