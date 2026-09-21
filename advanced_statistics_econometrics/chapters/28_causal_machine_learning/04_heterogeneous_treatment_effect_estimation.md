## Heterogeneous Treatment Effect Estimation


### Overview

Heterogeneous treatment effect (HTE) estimation moves beyond a single average treatment effect to characterize how treatment effects **vary across individuals or subgroups** as a function of observed covariates. The central object of interest is the **Conditional Average Treatment Effect (CATE)**:

$$\tau(x)=E[Y(1)-Y(0)\mid X=x]$$

This chapter area surveys the general estimand, the family of **meta-learner** strategies for estimating it with arbitrary ML base learners, and the validation/inference tools used to assess whether estimated heterogeneity is genuine rather than noise.

### Why Heterogeneity Matters

**Key Points**

- A single ATE can mask substantial variation — a treatment with zero average effect can still have large positive effects for some subgroups and offsetting negative effects for others.
- HTE estimation supports **targeting/policy learning**: identifying which individuals benefit most from treatment (relevant for individualized medicine, targeted interventions, price discrimination, or optimal policy assignment rules).
- Two identification assumptions carry over unchanged from average-effect estimation: **unconfoundedness** ($\{Y(0),Y(1)\}\perp D\mid X$) and **overlap** ($0<e(X)<1$) — now required to hold at each covariate value $x$ where $\tau(x)$ is to be estimated, making overlap diagnostics especially important in sparse regions of the covariate space.

### The Meta-Learner Framework

Meta-learners are estimation strategies that reduce CATE estimation to a sequence of standard supervised-learning (regression/classification) problems, allowing **any** ML method (lasso, random forest, boosting, neural nets) to serve as the underlying "base learner."

```mermaid
flowchart TD
    A[Choose meta-learner strategy] --> B[S-Learner]
    A --> C[T-Learner]
    A --> D[X-Learner]
    A --> E[R-Learner]
    B --> F[Single model: Y ~ f(X, D)]
    C --> G[Two separate models: one per treatment arm]
    D --> H[Impute individual effects, model them, blend via propensity weight]
    E --> I[Partial out E(Y|X) and E(D|X), regress residuals on residuals]
    F --> J[tau_hat(x) = f(x,1) - f(x,0)]
    G --> J
    H --> J
    I --> J
    J --> K[Validate: BLP, calibration, RATE curves]
```

### S-Learner (Single Model)

Fit one model $\hat{m}(x,d)=\hat{E}[Y\mid X=x,D=d]$ treating $D$ as just another covariate; predict:

$$\hat\tau_S(x)=\hat{m}(x,1)-\hat{m}(x,0)$$

**Key Points**

- Simplest approach; risk is that flexible regularized models (e.g., tree-based methods, lasso) can **shrink the coefficient on $D$ toward zero** or fail to select $D$ or its interactions at all if the treatment signal is weak relative to other covariates — potentially masking real heterogeneity (Künzel et al. 2019).
- Works best when $D$ is expected to have a strong, easily detected main effect and interacts simply with covariates.

### T-Learner (Two Models)

Fit separate models per arm: $\hat{m}_1(x)=\hat{E}[Y\mid X=x,D=1]$ and $\hat{m}_0(x)=\hat{E}[Y\mid X=x,D=0]$; predict:

$$\hat\tau_T(x)=\hat{m}_1(x)-\hat{m}_0(x)$$

**Key Points**

- Avoids the S-learner's regularization-toward-zero problem by construction, since $D$ is never a feature to be selected or shrunk.
- Can perform poorly when treatment and control **sample sizes are highly imbalanced**, since each model is fit independently on only its own arm's data, and errors in the two separately-fit regression surfaces do not cancel.

### X-Learner (Künzel et al. 2019)

A two-stage procedure designed for imbalanced treatment/control group sizes:

1. Fit $\hat{m}_1(x)$, $\hat{m}_0(x)$ as in the T-learner.
2. Impute individual-level treatment effects for each group using the *other* group's model: $\hat{D}_i^1=Y_i-\hat{m}_0(X_i)$ for treated units, $\hat{D}_i^0=\hat{m}_1(X_i)-Y_i$ for control units.
3. Regress each imputed effect on $X$ to get $\hat\tau_1(x)$, $\hat\tau_0(x)$.
4. Combine via propensity-score weighting: $\hat\tau_X(x)=g(x)\hat\tau_0(x)+(1-g(x))\hat\tau_1(x)$, where $g(x)$ is often set to $\hat{e}(x)$ or $1-\hat{e}(x)$.

**Key Points**

- Explicitly designed to perform well when one treatment arm has substantially more observations than the other, by allowing information to flow across the imputation step.
- Requires **an additional propensity score model**, introducing a further nuisance component relative to S-/T-learners.

### R-Learner (Robinson 1988 partialling-out; Nie and Wager 2021)

Residualizes both outcome and treatment against covariates, then regresses residual-on-residual:

$$\tilde{Y}_i=Y_i-\hat{m}(X_i),\quad\tilde{D}_i=D_i-\hat{e}(X_i)$$



$$\hat\tau_R(\cdot)=\arg\min_\tau\frac{1}{N}\sum_i\big(\tilde{Y}_i-\tau(X_i)\tilde{D}_i\big)^2+\text{penalty}(\tau)$$

**Key Points**

- Directly built on a **Neyman-orthogonal** loss function — the R-learner's estimating equation is constructed so that first-order nuisance estimation errors in $\hat{m}(X)$ and $\hat{e}(X)$ do not bias the resulting $\hat\tau(x)$, connecting this approach directly to the DML/orthogonality framework.
- **Causal forests** can be understood as an adaptive, forest-based implementation of the R-learner principle, embedding the residual-on-residual logic within honest, heterogeneity-splitting trees rather than a single global second-stage model.
- Requires cross-fitting for the nuisance functions $\hat{m}(X)$, $\hat{e}(X)$ to avoid the same overfitting bias that motivates cross-fitting throughout the DML framework.

### Comparison Summary

| Learner | # Models Fit | Handles Imbalanced Arms | Orthogonalized | Key Weakness |
| --- | --- | --- | --- | --- |
| S-Learner | 1 | Poorly | No | Regularization bias toward $\hat\tau=0$ |
| T-Learner | 2 | Poorly | No | Independent arm-specific model error |
| X-Learner | 2 base + 2 effect + 1 propensity | Well (by design) | Partially | More nuisance components |
| R-Learner | 2 nuisance + 1 effect | Well | Yes | Requires cross-fitting |
| Causal Forest | Forest-adaptive | Well | Yes (honest + orthogonal) | Restricted to forest functional form |

### Validating Estimated Heterogeneity

Because CATE estimates can appear to show heterogeneity purely from noise, formal validation tools are essential:

**Key Points**

- **Best Linear Projection (BLP)**: regress $\hat\tau(X_i)$ on a chosen subset of covariates to test which, if any, significantly predict heterogeneity — a formal hypothesis test rather than visual inspection of a fitted CATE surface.
- **Calibration test**: bin observations by predicted $\hat\tau(x)$, compare the mean *predicted* effect in each bin to the mean *realized* AIPW-score-based effect in that bin — good calibration indicates the CATE model tracks true heterogeneity rather than overfitting.
- **Rank-Weighted Average Treatment Effect (RATE)** (Yadlowsky et al. 2021): assesses whether prioritizing individuals by their estimated $\hat\tau(x)$ (targeting operator characteristic) actually identifies those with systematically larger true effects — directly relevant for policy-targeting applications.
- **Sample splitting for validation**: as with any exploratory analysis, evaluating heterogeneity on a **held-out test set** distinct from the training data used to fit $\hat\tau(x)$ guards against overfitting-driven false discoveries of heterogeneity.

### Practical Example (R, `grf` + meta-learners)

```r
library(grf)

X <- as.matrix(df[, c("age", "income", "education", "baseline_outcome")])
Y <- df$outcome
D <- df$treat

# Causal forest (R-learner style, orthogonalized + honest)
cf <- causal_forest(X, Y, D)
tau_hat <- predict(cf)$predictions

# Validate heterogeneity
test_calibration(cf)
blp <- best_linear_projection(cf, X)
rate <- rank_average_treatment_effect(cf, priorities = tau_hat)
```

### Practical Example (Python, `econml` meta-learners)

```python
from econml.metalearners import SLearner, TLearner, XLearner
from sklearn.ensemble import RandomForestRegressor, RandomForestClassifier

X = df[["age", "income", "education", "baseline_outcome"]].values
Y = df["outcome"].values
D = df["treat"].values

# T-Learner
t_learner = TLearner(models=RandomForestRegressor(n_estimators=300))
t_learner.fit(Y, D, X=X)
tau_t = t_learner.effect(X)

# X-Learner (handles imbalanced arms)
x_learner = XLearner(
    models=RandomForestRegressor(n_estimators=300),
    propensity_model=RandomForestClassifier(n_estimators=300)
)
x_learner.fit(Y, D, X=X)
tau_x = x_learner.effect(X)
```

### Visualizing Meta-Learner Comparison (SVG)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 300">
<text x="320" y="20" font-size="14" text-anchor="middle" font-family="sans-serif" font-weight="bold">Meta-Learner CATE Estimates vs. True Effect (svg_diagram)</text>
<line x1="60" y1="250" x2="600" y2="250" stroke="black" stroke-width="1" />
<line x1="60" y1="40" x2="60" y2="250" stroke="black" stroke-width="1" />
<text x="330" y="280" font-size="11" text-anchor="middle" font-family="sans-serif">Covariate X</text>
<text x="20" y="150" font-size="11" text-anchor="middle" font-family="sans-serif" transform="rotate(-90 20 150)">tau(x)</text>
<path d="M80,200 C200,150 400,100 580,60" fill="none" stroke="black" stroke-width="2" stroke-dasharray="6,3" />
<text x="500" y="55" font-size="10" font-family="sans-serif">True tau(x)</text>
<path d="M80,215 C200,205 400,190 580,175" fill="none" stroke="#dc2626" stroke-width="2" />
<text x="500" y="192" font-size="10" fill="#dc2626" font-family="sans-serif">S-learner (attenuated)</text>
<path d="M80,195 C200,148 400,102 580,65" fill="none" stroke="#2563eb" stroke-width="2" />
<text x="440" y="120" font-size="10" fill="#2563eb" font-family="sans-serif">R-learner / Causal forest</text>
</svg>

### Common Pitfalls

- **Interpreting S-learner attenuation as evidence of "no heterogeneity"** — the S-learner's regularization bias systematically shrinks estimated effects toward zero, especially when $D$'s main effect is small relative to other covariates' predictive power.
- **Skipping formal validation (BLP, calibration, RATE)** and instead relying on visual inspection of a fitted CATE curve, which is highly susceptible to overfitting-driven spurious patterns.
- **Multiple-comparisons/data-dredging**: searching over many candidate subgroups for "significant" heterogeneity without correction, akin to subgroup analysis pitfalls in classical statistics.
- **Applying HTE estimates in low-overlap regions**: predicted heterogeneity in covariate regions with poor treatment/control overlap is unreliable regardless of which meta-learner is used.
- **Ignoring cross-fitting for R-learner/DML-based approaches**, reintroducing the overfitting bias that orthogonalization is meant to avoid.
- **Choosing a meta-learner without considering arm-size balance**: defaulting to a T-learner in a heavily imbalanced sample (e.g., 90% control) when an X-learner or causal forest would perform meaningfully better.

**Next Steps**

- Causal Forests and Generalized Random Forests
- Double/Debiased Machine Learning
- Doubly Robust Estimation
- Policy Learning and Optimal Treatment Assignment
- Neyman Orthogonality and Cross-Fitting
- Best Linear Projections and RATE Curves
- Propensity Score Estimation and Overlap Diagnostics