## Doubly Robust Estimation

### Overview

Doubly robust (DR) estimators combine an outcome regression model with a propensity score (treatment) model such that the resulting estimator of the treatment effect is **consistent if either model is correctly specified**, not necessarily both. This "two chances to get it right" property is the defining feature of the class and motivates its widespread use as a default over either pure outcome-regression or pure IPW estimation (Robins, Rotnitzky, and Zhao 1994; Bang and Robins 2005).

### Core Estimator: Augmented IPW (AIPW)

$$\hat{\tau}_{AIPW}=\frac{1}{N}\sum_{i=1}^N\left[\hat{m}_1(X_i)-\hat{m}_0(X_i)\right]+\frac{1}{N}\sum_{i=1}^N\left[\frac{D_i(Y_i-\hat{m}_1(X_i))}{\hat{e}(X_i)}-\frac{(1-D_i)(Y_i-\hat{m}_0(X_i))}{1-\hat{e}(X_i)}\right]$$

where $\hat{m}_d(X)=\hat{E}[Y\mid X,D=d]$ is the outcome regression and $\hat{e}(X)=\hat{P}(D=1\mid X)$ is the propensity score.

**Key Points**

- The first bracketed term is the plug-in outcome-regression estimate of $\tau$.
- The second bracketed term is an **IPW-weighted correction** for the outcome model's residuals — if $\hat{m}_d(X)$ is correctly specified, this correction term has expectation zero; if $\hat{e}(X)$ is correctly specified, the weighting correctly reweights the residual bias from a misspecified $\hat{m}_d(X)$.
- If **both** models are correctly specified, AIPW achieves the semiparametric efficiency bound — it is the most precise estimator available under the unconfoundedness assumption (Hahn 1998).

### Doubly Robustness: Formal Statement

Let $m_d(X;\beta)$ and $e(X;\gamma)$ denote parametric working models. AIPW is consistent for $\tau$ if **either** $m_d(X;\beta)=E[Y\mid X,D=d]$ **or** $e(X;\gamma)=P(D=1\mid X)$ holds — i.e., only one of the two parametric models needs to be correctly specified, though which one is correct need not be known in advance.

[Inference — the practical performance gain from double robustness versus a single well-specified model is context-dependent and debated in applied work, particularly under near-positivity violations]

### Estimation Workflow

```mermaid
flowchart TD
    A[Specify outcome model m_d(X) for each treatment arm] --> C[Combine via AIPW formula]
    B[Specify propensity score model e(X)] --> C
    C --> D[Check overlap/positivity: extreme e(X) values]
    D --> E{Severe positivity violations?}
    E -->|Yes| F[Trim sample or use overlap-weighted DR variant]
    E -->|No| G[Estimate tau_AIPW]
    F --> G
    G --> H{Using ML nuisance estimators?}
    H -->|Yes| I[Apply cross-fitting / sample-splitting]
    H -->|No| J[Compute standard errors via M-estimation/sandwich formula]
    I --> J
    J --> K[Report ATE/ATT with robust inference]
```

### Cross-Fitting and Double/Debiased Machine Learning (DML)

When nuisance functions $\hat{m}_d(X)$ and $\hat{e}(X)$ are estimated via flexible machine learning methods (random forests, gradient boosting, neural networks), naive plug-in AIPW can suffer from **overfitting bias** and slow convergence rates that invalidate standard asymptotic inference. Chernozhukov et al. (2018) formalize a solution:

1. **Neyman orthogonality**: the AIPW moment condition is constructed so that its first-order sensitivity to small errors in the nuisance functions is zero — errors in $\hat{m}_d$ and $\hat{e}$ enter the final estimate only at second order (i.e., as a product of the two errors).
2. **Cross-fitting**: split the sample into $K$ folds; estimate nuisance functions on $K-1$ folds and evaluate the AIPW moment on the held-out fold, then average across folds. This removes the own-observation overfitting bias that would otherwise contaminate flexible ML fits.

**Key Points**

- Neyman orthogonality is what permits nuisance functions to be estimated at slower-than-$\sqrt{N}$ rates (as is typical for ML estimators) while the final treatment effect estimate retains $\sqrt{N}$-consistency and asymptotic normality.
- Cross-fitting is standard practice, not optional, when nuisance functions are estimated via ML — omitting it is a common and serious methodological error in applied DML work.

### Comparison to Non-Robust Alternatives

| Estimator | Consistent if... | Efficient if both models correct? |
| --- | --- | --- |
| Outcome regression only | $m_d(X)$ correctly specified | No |
| IPW only | $e(X)$ correctly specified | No |
| AIPW / Doubly Robust | Either $m_d(X)$ or $e(X)$ correctly specified | Yes (achieves efficiency bound) |
| DML (ML nuisance + cross-fitting) | Either nuisance function estimated at sufficiently fast rate, both consistent | Yes, asymptotically |

### Practical Example (R, `DoubleML`)

```r
library(DoubleML)
library(mlr3learners)

dml_data <- DoubleMLData$new(
  df,
  y_col = "outcome",
  d_cols = "treat",
  x_cols = c("age", "income", "education", "baseline_outcome")
)

ml_g <- lrn("regr.ranger")   # outcome model (random forest)
ml_m <- lrn("classif.ranger") # propensity score model

dml_plr <- DoubleMLIRM$new(
  dml_data,
  ml_g = ml_g,
  ml_m = ml_m,
  n_folds = 5,       # cross-fitting
  score = "ATE"
)

dml_plr$fit()
dml_plr$summary()
```

### Practical Example (Python, `econml`)

```python
from econml.dr import LinearDRLearner
from sklearn.ensemble import RandomForestRegressor, RandomForestClassifier

est = LinearDRLearner(
    model_regression=RandomForestRegressor(n_estimators=200),
    model_propensity=RandomForestClassifier(n_estimators=200),
    cv=5   # cross-fitting folds
)

est.fit(
    Y=df["outcome"],
    T=df["treat"],
    X=df[["age", "income", "education", "baseline_outcome"]]
)

ate = est.ate(X=df[["age", "income", "education", "baseline_outcome"]])
ate_interval = est.ate_interval(X=df[["age", "income", "education", "baseline_outcome"]])
```

### Visualizing the Double-Robustness Property (SVG)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 320">
<text x="320" y="20" font-size="14" text-anchor="middle" font-family="sans-serif" font-weight="bold">Consistency Regions of DR Estimation (svg_diagram)</text>
<line x1="80" y1="280" x2="580" y2="280" stroke="black" stroke-width="1" />
<line x1="80" y1="60" x2="80" y2="280" stroke="black" stroke-width="1" />
<text x="330" y="300" font-size="11" text-anchor="middle" font-family="sans-serif">Propensity model e(X) correct?</text>
<text x="30" y="170" font-size="11" text-anchor="middle" font-family="sans-serif" transform="rotate(-90 30 170)">Outcome model m(X) correct?</text>
<rect x="330" y="60" width="250" height="110" fill="#bbf7d0" stroke="#333" />
<text x="455" y="120" font-size="11" text-anchor="middle" font-family="sans-serif">Consistent + Efficient</text>
<rect x="330" y="170" width="250" height="110" fill="#fef08a" stroke="#333" />
<text x="455" y="230" font-size="11" text-anchor="middle" font-family="sans-serif">Consistent (via e(X))</text>
<rect x="80" y="60" width="250" height="110" fill="#fef08a" stroke="#333" />
<text x="205" y="120" font-size="11" text-anchor="middle" font-family="sans-serif">Consistent (via m(X))</text>
<rect x="80" y="170" width="250" height="110" fill="#fecaca" stroke="#333" />
<text x="205" y="230" font-size="11" text-anchor="middle" font-family="sans-serif">Inconsistent</text>

<text x="205" y="50" font-size="10" text-anchor="middle" font-family="sans-serif">No</text>

<text x="455" y="50" font-size="10" text-anchor="middle" font-family="sans-serif">Yes</text>

</svg>

### Common Pitfalls

- **Omitting cross-fitting** when using flexible ML for nuisance functions — invalidates the theoretical guarantees underlying valid inference (though point estimates alone may still look plausible).
- **Overstating robustness**: DR estimators are only robust to misspecification of *one* of the two models — if both are badly misspecified, or if there is severe positivity violation, DR estimators can perform *worse* than a single well-specified model in finite samples [Inference — this is a documented finite-sample phenomenon, sometimes termed the "double robustness is not a free lunch" critique, e.g., Kang and Schafer 2007].
- **Extreme propensity score weights** still destabilize AIPW even though it is "doubly robust" — trimming/overlap-weight variants remain relevant.
- **Treating DML output as fully assumption-free**: unconfoundedness is still required; DR/DML relaxes functional-form assumptions, not the identifying assumption itself.
- Using too few cross-fitting folds relative to sample size, or failing to average over multiple random fold splits, which can introduce additional finite-sample variability.

**Next Steps**

- Propensity Score Estimation
- Inverse Probability Weighting
- Double/Debiased Machine Learning (general framework)
- Targeted Maximum Likelihood Estimation (TMLE)
- Sensitivity Analysis for Unconfoundedness
- Overlap Weights and Positivity Diagnostics
- Heterogeneous Treatment Effect Estimation (Causal Forests, Meta-Learners)