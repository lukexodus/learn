## Propensity Score Estimation

### Overview

The propensity score is the conditional probability of receiving treatment given observed covariates: $e(X)=P(D=1\mid X)$. Rosenbaum and Rubin (1983) established that conditioning on the propensity score alone is sufficient to balance covariates between treated and control groups, allowing dimension reduction from a potentially high-dimensional covariate vector $X$ to a single scalar. This underpins the broad family of propensity-score-based methods: matching, stratification, inverse-probability weighting (IPW), and doubly-robust estimators.

### Identification Assumptions

1. **Unconfoundedness / conditional independence (CIA)**: $\{Y_i(0),Y_i(1)\}\perp D_i\mid X_i$ — treatment assignment is as-good-as-random once $X_i$ is conditioned on.
2. **Overlap / common support**: $0<e(X)<1$ for all $X$ in the support — every covariate profile has a positive probability of being both treated and untreated.
3. **SUTVA**: no interference between units and a single well-defined version of treatment.

**Key Points**

- The propensity score is a **balancing score**: conditional on $e(X)$, the distribution of $X$ is the same for treated and control units, i.e., $X\perp D\mid e(X)$.
- If CIA holds conditional on $X$, it also holds conditional on $e(X)$ alone — this is the theoretical justification for score-based dimension reduction.
- Unconfoundedness is **not testable** from the data; it is an identifying assumption justified by institutional knowledge, richness of $X$, and study design.

### Estimation Approaches

**Parametric (most common)**

$$e(X)=P(D=1\mid X)=\Lambda(X'\beta)$$

estimated via logistic regression ($\Lambda$ = logistic CDF) or probit. Coefficients themselves are not of substantive interest — only the predicted probabilities $\hat{e}(X_i)$ matter.

**Nonparametric / machine learning**

- Generalized boosted models (GBM), random forests, or covariate-balancing propensity score (CBPS, Imai and Ratkovic 2014) methods.
- **CBPS** directly optimizes the score-estimating equations to maximize covariate balance rather than maximizing a likelihood — often produces better balance in practice.
- Machine-learning propensity scores paired with doubly-robust/AIPW or double/debiased ML estimators (Chernozhukov et al. 2018) to control overfitting bias via cross-fitting.

### Specification and Balance Diagnostics

```mermaid
flowchart TD
    A[Select covariates X: pre-treatment, theoretically relevant] --> B[Estimate e(X) via logit/probit/ML]
    B --> C[Check common support: overlap in score distributions]
    C --> D{Sufficient overlap?}
    D -->|No| E[Trim sample or redefine estimand: ATT vs ATE]
    D -->|Yes| F[Use score for matching/weighting/stratification]
    E --> C
    F --> G[Check covariate balance post-adjustment]
    G --> H{Balanced?}
    H -->|No| I[Respecify model: add interactions, polynomials, or switch method]
    I --> B
    H -->|Yes| J[Proceed to outcome analysis]
```

**Key Points**

- Balance, not predictive fit or pseudo-$R^2$, is the criterion for a "good" propensity score model — a model can classify treatment status poorly yet still balance covariates well.
- Standard diagnostics: standardized mean differences (typically target $<0.1$ post-adjustment), variance ratios, and visual overlap plots of the estimated score density by treatment group.
- Iterative respecification (adding polynomial terms, interactions) is standard practice and does not "contaminate" identification, since only $X$ (not $Y$) is used in this step — an important practical distinction from outcome-model specification search.

### Uses of the Propensity Score

| Method | Mechanism |
| --- | --- |
| Matching | Pair treated/control units with similar $\hat{e}(X)$ |
| Stratification/subclassification | Divide sample into score strata (e.g., quintiles), estimate effects within strata, aggregate |
| Inverse Probability Weighting (IPW) | Weight observations by $1/\hat{e}(X)$ (treated) or $1/(1-\hat{e}(X))$ (control) |
| Doubly Robust / AIPW | Combine outcome regression with IPW; consistent if *either* model is correctly specified |
| Covariate adjustment | Include $\hat{e}(X)$ directly as a regressor |

### Practical Example (R, `MatchIt` / `WeightIt`)

```r
library(WeightIt)
library(cobalt)

# Estimate propensity score and IPW weights (ATT)
w_out <- weightit(
  treat ~ age + income + education + baseline_outcome,
  data = df,
  method = "glm",      # logistic regression
  estimand = "ATT"
)

# Balance diagnostics
bal.tab(w_out, un = TRUE, thresholds = c(m = 0.1))
love.plot(w_out, thresholds = c(m = 0.1))

# Outcome model using weights
lm_out <- lm(outcome ~ treat, data = df, weights = w_out$weights)
```

### Practical Example (Python, `causalml` / `scikit-learn`)

```python
from sklearn.linear_model import LogisticRegression
import numpy as np

X = df[["age", "income", "education", "baseline_outcome"]]
D = df["treat"]

ps_model = LogisticRegression(max_iter=1000).fit(X, D)
df["ps"] = ps_model.predict_proba(X)[:, 1]

# Trim to common support
df = df[(df["ps"] > 0.05) & (df["ps"] < 0.95)]

# ATT weights: treated=1, control=ps/(1-ps)
df["ipw"] = np.where(df["treat"] == 1, 1, df["ps"] / (1 - df["ps"]))
```

### Visualizing Overlap (SVG)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 300">
<text x="320" y="20" font-size="14" text-anchor="middle" font-family="sans-serif" font-weight="bold">Propensity Score Overlap by Treatment Status (svg_diagram)</text>
<line x1="60" y1="250" x2="600" y2="250" stroke="black" stroke-width="1" />
<line x1="60" y1="40" x2="60" y2="250" stroke="black" stroke-width="1" />
<text x="60" y="268" font-size="10" text-anchor="middle" font-family="sans-serif">0.0</text>
<text x="600" y="268" font-size="10" text-anchor="middle" font-family="sans-serif">1.0</text>
<text x="330" y="285" font-size="11" text-anchor="middle" font-family="sans-serif">Estimated propensity score e(X)</text>
<path d="M100,250 C150,240 190,80 230,80 C270,80 300,240 340,250" fill="none" stroke="#dc2626" stroke-width="2" />
<path d="M320,250 C370,240 410,100 450,100 C490,100 520,240 560,250" fill="none" stroke="#2563eb" stroke-width="2" />
<text x="230" y="70" font-size="10" fill="#dc2626" text-anchor="middle" font-family="sans-serif">Control</text>
<text x="475" y="90" font-size="10" fill="#2563eb" text-anchor="middle" font-family="sans-serif">Treated</text>
<text x="330" y="120" font-size="10" fill="#555" text-anchor="middle" font-family="sans-serif">region of overlap</text>
</svg>

### Common Pitfalls

- **Insufficient overlap**: extreme propensity scores near 0 or 1 produce enormous IPW weights and unstable estimates; requires trimming or redefinition of the estimand.
- **Post-treatment variables in $X$**: including mediators or post-treatment covariates in the score model biases estimates (blocks part of the causal pathway).
- **Using the propensity score in place of, rather than as a complement to, careful covariate selection** — a well-specified balancing model still relies on $X$ being rich enough to satisfy CIA in the first place.
- **Focusing on prediction accuracy** (AUC, classification metrics) instead of balance when selecting a specification.
- **Ignoring estimation uncertainty in $\hat{e}(X)$** when computing standard errors for downstream matching/weighting estimators — naive SEs can be misleading; bootstrap or sandwich-type corrections are typically needed.

**Next Steps**

- Propensity Score Matching (nearest-neighbor, caliper, kernel)
- Inverse Probability Weighting and Stabilized Weights
- Doubly Robust / Augmented IPW Estimators
- Covariate Balancing Propensity Score (CBPS)
- Double/Debiased Machine Learning
- Overlap and Common Support Diagnostics
- Sensitivity Analysis for Unconfoundedness (Rosenbaum bounds)