## Inverse Probability Weighting

### Overview

Inverse probability weighting (IPW) constructs a pseudo-population in which treatment assignment is independent of observed covariates by reweighting each unit by the inverse of its probability of receiving the treatment it actually received. Rather than pruning or pairing units (as in matching), IPW retains the full sample and reweights it, using the propensity score $e(X)=P(D=1\mid X)$ as the weighting mechanism (Horvitz and Thompson 1952; Robins, Hernán, and Brumback 2000).

### Core Estimator

For the **Average Treatment Effect (ATE)**:

$$\hat{\tau}_{ATE}=\frac{1}{N}\sum_{i=1}^N\left(\frac{D_iY_i}{\hat{e}(X_i)}-\frac{(1-D_i)Y_i}{1-\hat{e}(X_i)}\right)$$

For the **Average Treatment Effect on the Treated (ATT)**:

$$\hat{\tau}_{ATT}=\frac{1}{N_1}\sum_{i:D_i=1}Y_i-\frac{1}{N_1}\sum_{i:D_i=0}\frac{\hat{e}(X_i)}{1-\hat{e}(X_i)}Y_i$$

**Key Points**

- The weight for a treated observation under ATE is $1/\hat{e}(X_i)$; for a control observation it is $1/(1-\hat{e}(X_i))$.
- Under the ATT weighting scheme, treated units receive weight 1, and control units are reweighted by the odds $\hat{e}(X_i)/(1-\hat{e}(X_i))$ to resemble the treated population's covariate distribution.
- IPW is intuitively a form of **survey-sampling weighting**: units that are "rare" given their covariates (e.g., a treated unit with covariates that make treatment unlikely) are upweighted because they are informative about the counterfactual population.

### Identification Assumptions

1. **Unconfoundedness (CIA)**: $\{Y_i(0),Y_i(1)\}\perp D_i\mid X_i$.
2. **Overlap/positivity**: $0<e(X)<1$ strictly, for all $X$ in the support — this is especially critical for IPW because near-zero or near-one scores produce extreme weights.
3. **Correct specification of the propensity score model** — unlike matching, standard IPW has no built-in balance-checking safeguard; misspecification directly biases $\hat{\tau}$.

### Stabilized Weights

Raw IPW weights can have extremely high variance. **Stabilized weights** rescale by the marginal treatment probability:

$$sw_i=\frac{D_i\,\hat{P}(D=1)}{\hat{e}(X_i)}+\frac{(1-D_i)\,\hat{P}(D=0)}{1-\hat{e}(X_i)}$$

This preserves consistency while substantially reducing variance relative to unstabilized weights, particularly when the propensity score model has strong predictors.

### Weight Diagnostics and Trimming

```mermaid
flowchart TD
    A[Estimate propensity score e(X)] --> B[Construct IPW weights: raw or stabilized]
    B --> C[Inspect weight distribution: max, effective sample size]
    C --> D{Extreme weights present?}
    D -->|Yes| E[Trim/truncate scores or weights, or use overlap weights]
    D -->|No| F[Proceed to weighted outcome analysis]
    E --> C
    F --> G[Check post-weighting covariate balance]
    G --> H{Balanced?}
    H -->|No| I[Respecify propensity score model]
    I --> A
    H -->|Yes| J[Estimate weighted ATE/ATT with robust/sandwich SEs]
```

**Key Points**

- **Effective sample size (ESS)**: $ESS=\dfrac{(\sum w_i)^2}{\sum w_i^2}$ — quantifies how much a highly variable weight distribution degrades statistical precision relative to the nominal sample size.
- **Trimming**: dropping or capping observations with $\hat{e}(X_i)$ outside a range such as $[0.1,0.9]$ (Crump et al. 2009 derive an optimal trimming rule that minimizes the asymptotic variance of the ATE estimator).
- **Overlap weights** (Li, Morgan, and Zaslavsky 2018): weight by $w_i=(1-\hat{e}(X_i))$ for treated and $\hat{e}(X_i)$ for control — this target population (the "overlap population") automatically down-weights units in poor-overlap regions rather than requiring hard trimming thresholds, and exactly balances covariate means in finite samples for logistic propensity models.

### Doubly Robust / Augmented IPW (AIPW)

Combines an outcome regression model $\hat{m}_d(X)=\hat{E}[Y\mid X,D=d]$ with IPW weighting:

$$\hat{\tau}_{AIPW}=\frac{1}{N}\sum_i\left[\hat{m}_1(X_i)-\hat{m}_0(X_i)+\frac{D_i(Y_i-\hat{m}_1(X_i))}{\hat{e}(X_i)}-\frac{(1-D_i)(Y_i-\hat{m}_0(X_i))}{1-\hat{e}(X_i)}\right]$$

**Key Points**

- AIPW is **consistent if either** the propensity score model **or** the outcome regression model is correctly specified (not necessarily both) — the "double robustness" property.
- Modern practice pairs AIPW with **machine-learning nuisance function estimation** and **cross-fitting** (sample-splitting) to avoid overfitting bias, forming the basis of Double/Debiased Machine Learning (Chernozhukov et al. 2018).

### Practical Example (R, `WeightIt` / `survey`)

```r
library(WeightIt)
library(survey)

w_out <- weightit(
  treat ~ age + income + education + baseline_outcome,
  data = df,
  method = "glm",
  estimand = "ATE",
  stabilize = TRUE
)

# Effective sample size check
summary(w_out)

design <- svydesign(ids = ~1, weights = w_out$weights, data = df)
model <- svyglm(outcome ~ treat, design = design)
summary(model)   # robust SEs by construction
```

### Practical Example (Python, manual stabilized IPW)

```python
import numpy as np
from sklearn.linear_model import LogisticRegression
import statsmodels.api as sm

X = df[["age", "income", "education", "baseline_outcome"]]
D = df["treat"].values

ps = LogisticRegression(max_iter=1000).fit(X, D).predict_proba(X)[:, 1]
p_treat = D.mean()

sw = np.where(
    D == 1,
    p_treat / ps,
    (1 - p_treat) / (1 - ps)
)

# Effective sample size
ess = (sw.sum() ** 2) / (sw ** 2).sum()

weighted_model = sm.WLS(
    df["outcome"], sm.add_constant(df["treat"]), weights=sw
).fit(cov_type="HC1")
```

### Visualizing Weight Distribution (SVG)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 300">
<text x="320" y="20" font-size="14" text-anchor="middle" font-family="sans-serif" font-weight="bold">IPW Weight Distribution: Raw vs. Stabilized (svg_diagram)</text>
<line x1="60" y1="250" x2="600" y2="250" stroke="black" stroke-width="1" />
<line x1="60" y1="40" x2="60" y2="250" stroke="black" stroke-width="1" />
<text x="330" y="285" font-size="11" text-anchor="middle" font-family="sans-serif">Weight value</text>
<text x="20" y="150" font-size="11" text-anchor="middle" font-family="sans-serif" transform="rotate(-90 20 150)">Density</text>
<path d="M70,250 C90,245 100,60 120,60 C140,60 180,240 550,248" fill="none" stroke="#dc2626" stroke-width="2" />
<path d="M70,250 C100,230 130,120 170,120 C210,120 260,235 340,248" fill="none" stroke="#2563eb" stroke-width="2" />
<text x="180" y="55" font-size="10" fill="#dc2626" font-family="sans-serif">Raw (long right tail)</text>
<text x="220" y="115" font-size="10" fill="#2563eb" font-family="sans-serif">Stabilized (tighter)</text>
</svg>

### Common Pitfalls

- **Near-positivity violations**: a small number of extreme weights can dominate the estimator, producing high variance and sensitivity to individual observations — always inspect max weight and ESS, not just point estimates.
- **Using raw (unstabilized) weights by default** when stabilized weights are nearly always preferable for variance reduction at no cost to consistency.
- **Ignoring propensity-score estimation uncertainty** in standard errors — weights are estimated, not known, and this first-stage uncertainty should propagate into inference (robust/sandwich SEs via `svyglm`-style estimators partially address this; full accounting may require the M-estimation/GMM framework or bootstrap).
- **Model misspecification with no balance safeguard**: unlike matching, plain IPW does not automatically reveal poor covariate balance — checking weighted balance diagnostics remains essential.
- Confusing **ATE weights** and **ATT weights** — using the wrong scheme changes both the target estimand and which units the weights emphasize.

**Next Steps**

- Propensity Score Estimation
- Doubly Robust / AIPW Estimators
- Double/Debiased Machine Learning
- Overlap Weights and Optimal Trimming (Crump et al. 2009)
- Matching Methods and Covariate Balance
- Marginal Structural Models (time-varying treatment)
- Sensitivity Analysis for Unconfoundedness