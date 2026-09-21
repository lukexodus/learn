## Regression Adjustment for Treatment Effects

### Overview

Regression adjustment estimates treatment effects by directly modeling the conditional outcome mean $E[Y\mid X,D]$ and using the fitted model to predict each unit's outcome under both treatment states. It is the most direct implementation of covariate adjustment for confounding under unconfoundedness, contrasting with propensity-score-based methods (matching, IPW) that instead model the treatment assignment mechanism.

### Core Estimator: G-Computation / Standardization

Given a fitted outcome model $\hat{m}_d(X)=\hat{E}[Y\mid X,D=d]$ for $d\in\{0,1\}$, the regression-adjustment (g-computation) estimator of the ATE is:

$$\hat{\tau}_{RA}=\frac{1}{N}\sum_{i=1}^N\left[\hat{m}_1(X_i)-\hat{m}_0(X_i)\right]$$

Each unit's outcome is predicted under **both** treatment arms — including counterfactual predictions for units whose observed treatment status differs — and the individual-level predicted differences are averaged over the full covariate distribution.

**Key Points**

- This differs fundamentally from simply reading off the coefficient on $D$ in a regression $Y=\alpha+\tau D+X'\beta+\varepsilon$ under a constant-effects (no interaction) specification — g-computation with a **fully interacted** model ($D$ interacted with all of $X$) recovers a fully flexible, heterogeneity-respecting ATE.
- The ATT analog restricts the averaging in the formula to treated units only: $\hat{\tau}_{ATT}=\frac{1}{N_1}\sum_{i:D_i=1}[\hat{m}_1(X_i)-\hat{m}_0(X_i)]$.
- Regression adjustment is sometimes termed **"standardization"** in the epidemiological literature, reflecting its origins in direct/indirect standardization of rates across subpopulations.

### Identification Assumptions

1. **Unconfoundedness (CIA)**: $\{Y_i(0),Y_i(1)\}\perp D_i\mid X_i$.
2. **Overlap/positivity**: sufficient covariate overlap for extrapolation across $D$ within each covariate stratum to be meaningful — regression adjustment can silently extrapolate beyond the data's support, unlike matching/IPW which are naturally constrained (or explicitly flagged) by poor overlap.
3. **Correct functional-form specification of $m_d(X)$** — this is regression adjustment's central vulnerability relative to propensity-score and doubly robust approaches.

### Specification Choices

```mermaid
flowchart TD
    A[Specify functional form of m_d(X)] --> B{Interact D with all covariates?}
    B -->|No: constant-effects model| C[Coefficient on D estimates ATE under homogeneity assumption]
    B -->|Yes: fully interacted / separate models by arm| D[G-computation: predict Y under both arms, average difference]
    D --> E[Check extrapolation: are predictions within covariate support?]
    E --> F{Adequate overlap?}
    F -->|No| G[Trim sample or switch to matching/IPW-based method]
    F -->|Yes| H[Report ATE/ATT with appropriate SEs]
    C --> I[Risk: misspecification bias if true effect heterogeneous or nonlinear]
```

**Key Points**

- A single regression with an **additive** $D$ term (no interactions) imposes constant treatment effects across covariate values — a strong and often implausible assumption; it is a special case, not the general form, of regression adjustment.
- Best practice fits **separate models by treatment arm** (or a fully saturated interaction model), letting the functional relationship between $X$ and $Y$ differ freely across treatment groups.
- Flexible/nonparametric outcome models (splines, random forests, gradient boosting) reduce reliance on correct linear functional-form assumptions, at the cost of requiring cross-fitting for valid inference (connects directly to Doubly Robust Estimation / DML).

### Relationship to Other Methods

| Method | Models | Robust to misspecification of... |
| --- | --- | --- |
| Regression adjustment | $E[Y\mid X,D]$ only | Nothing — relies entirely on correct outcome model |
| IPW | $P(D=1\mid X)$ only | Nothing — relies entirely on correct propensity model |
| Doubly robust / AIPW | Both | Either one (not necessarily both) |
| Matching | Neither explicitly (nonparametric on $X$ or $\hat{e}(X)$) | Functional form, via nonparametric pairing |

**Key Points**

- Regression adjustment and IPW are the two "single-model" building blocks that doubly robust estimation combines — understanding regression adjustment in isolation clarifies exactly what the IPW correction term in AIPW is compensating for.
- In randomized experiments, regression adjustment for baseline covariates is used purely to **improve precision** (reduce residual variance), not for identification — $D$ is independent of $X$ by design, so adjustment is optional for consistency though still commonly recommended (Lin 2013 shows fully interacted OLS adjustment is weakly efficiency-improving asymptotically).

### Practical Example (R, base + `margins`)

```r
# Separate models by treatment arm (g-computation)
m1 <- lm(outcome ~ age + income + education + baseline_outcome,
         data = subset(df, treat == 1))
m0 <- lm(outcome ~ age + income + education + baseline_outcome,
         data = subset(df, treat == 0))

# Predict counterfactual outcomes for the FULL sample under both arms
pred1 <- predict(m1, newdata = df)
pred0 <- predict(m0, newdata = df)

tau_hat <- mean(pred1 - pred0)   # ATE via g-computation

# Bootstrap for standard errors
library(boot)
gcomp_fn <- function(data, indices) {
  d <- data[indices, ]
  m1 <- lm(outcome ~ age + income + education + baseline_outcome, data = subset(d, treat == 1))
  m0 <- lm(outcome ~ age + income + education + baseline_outcome, data = subset(d, treat == 0))
  mean(predict(m1, newdata = d) - predict(m0, newdata = d))
}
boot_out <- boot(df, gcomp_fn, R = 1000)
```

### Practical Example (Python, `statsmodels`)

```python
import statsmodels.formula.api as smf
import numpy as np

m1 = smf.ols(
    "outcome ~ age + income + education + baseline_outcome",
    data=df[df["treat"] == 1]
).fit()
m0 = smf.ols(
    "outcome ~ age + income + education + baseline_outcome",
    data=df[df["treat"] == 0]
).fit()

pred1 = m1.predict(df)
pred0 = m0.predict(df)

tau_hat = np.mean(pred1 - pred0)  # ATE via g-computation
```

### Visualizing Extrapolation Risk (SVG)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 300">
<text x="320" y="20" font-size="14" text-anchor="middle" font-family="sans-serif" font-weight="bold">Regression Adjustment: Extrapolation Beyond Support (svg_diagram)</text>
<line x1="60" y1="250" x2="600" y2="250" stroke="black" stroke-width="1" />
<line x1="60" y1="40" x2="60" y2="250" stroke="black" stroke-width="1" />
<text x="330" y="280" font-size="11" text-anchor="middle" font-family="sans-serif">Covariate X</text>
<text x="20" y="150" font-size="11" text-anchor="middle" font-family="sans-serif" transform="rotate(-90 20 150)">Outcome Y</text>
<circle cx="120" cy="200" r="4" fill="#dc2626" />
<circle cx="150" cy="190" r="4" fill="#dc2626" />
<circle cx="180" cy="185" r="4" fill="#dc2626" />
<circle cx="210" cy="175" r="4" fill="#dc2626" />
<line x1="100" y1="210" x2="230" y2="170" stroke="#dc2626" stroke-width="2" />
<circle cx="350" cy="140" r="4" fill="#2563eb" />
<circle cx="400" cy="110" r="4" fill="#2563eb" />
<circle cx="450" cy="90" r="4" fill="#2563eb" />
<circle cx="500" cy="65" r="4" fill="#2563eb" />
<line x1="330" y1="150" x2="520" y2="55" stroke="#2563eb" stroke-width="2" />
<line x1="230" y1="170" x2="330" y2="150" stroke="#dc2626" stroke-width="2" stroke-dasharray="4,3" />
<rect x="230" y="55" width="100" height="200" fill="#fca5a5" opacity="0.25" />
<text x="280" y="50" font-size="10" text-anchor="middle" fill="#991b1b" font-family="sans-serif">no overlap region</text>
<text x="150" y="225" font-size="10" fill="#dc2626" text-anchor="middle" font-family="sans-serif">Control arm data</text>
<text x="450" y="230" font-size="10" fill="#2563eb" text-anchor="middle" font-family="sans-serif">Treated arm data</text>
</svg>

### Common Pitfalls

- **Silent extrapolation**: because regression models produce predictions for any covariate value, regression adjustment can generate seemingly precise estimates in regions of the covariate space with **no actual overlapping support** — a failure mode less visible than in matching/IPW, where poor overlap manifests as missing matches or extreme weights.
- **Constant-effects misspecification**: fitting a single additive-$D$ model when true effects are heterogeneous biases the estimated "ATE" toward whatever weighting the linear model implicitly imposes, which need not correspond to any well-defined causal estimand (Angrist 1998; Sloczynski 2022 on implicit weighting in regressions with heterogeneous effects and covariate-treatment correlation).
- **Omitting interactions between $D$ and covariates** by default — separate-by-arm models or fully saturated interactions should be the default starting specification, not an afterthought.
- **Underestimating standard errors** by ignoring the estimation uncertainty in the fitted outcome models themselves when the predictions are plugged into a second-stage average — bootstrap or M-estimation-based SEs are generally required.
- Treating a high $R^2$ or good in-sample fit as validation of the causal estimate, when the real requirement is correct specification of $E[Y\mid X,D]$ **and** adequate covariate overlap, neither of which $R^2$ directly verifies.

**Next Steps**

- Doubly Robust Estimation
- Propensity Score Estimation
- Inverse Probability Weighting
- Double/Debiased Machine Learning
- Heterogeneous Treatment Effects (Causal Forests, Meta-Learners)
- Matching Methods and Covariate Balance
- Sensitivity Analysis for Unconfoundedness