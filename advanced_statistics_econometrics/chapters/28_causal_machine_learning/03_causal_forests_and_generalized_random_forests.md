## Causal Forests and Generalized Random Forests


### Overview

Causal forests extend the random forest algorithm from prediction to the estimation of **heterogeneous treatment effects** — the conditional average treatment effect (CATE) $\tau(x)=E[Y(1)-Y(0)\mid X=x]$ as a function of covariates. Rather than partitioning the covariate space to minimize prediction error (as in a standard regression forest), causal forests partition to maximize heterogeneity in the estimated treatment effect across leaves. Causal forests are a special case of the broader **Generalized Random Forest (GRF)** framework (Athey, Tibshirani, and Wager 2019; Wager and Athey 2018), which recasts random forests as an adaptive, locally weighted method for solving a wide class of local moment/estimating equations.

### From Prediction Forests to GRF

A standard random forest can be reinterpreted not merely as an ensemble predictor but as generating **adaptive weights** $\alpha_i(x)$ for each training observation $i$, based on how often $i$ falls in the same leaf as a target point $x$ across trees. A prediction is then a weighted average: $\hat{f}(x)=\sum_i\alpha_i(x)Y_i$.

**Key Points**

- GRF generalizes this weighting idea beyond simple conditional mean prediction: instead of averaging outcomes, GRF uses forest-generated weights $\alpha_i(x)$ to solve a **local generalized method of moments (GMM) problem** at each point $x$, targeting *any* parameter identified by a local moment condition — treatment effects, instrumental variables coefficients, quantile effects, or survival parameters.
- This reframes the tree-splitting criterion itself: rather than splitting to reduce squared prediction error, GRF trees split to maximize the heterogeneity of the *target parameter* (e.g., the treatment effect) across the resulting child nodes.

### Causal Forest Estimating Equation

At each covariate point $x$, the causal forest solves a local, weighted version of the AIPW/orthogonal moment condition (connecting directly to Neyman-orthogonal, doubly-robust estimation):

$$\hat{\tau}(x)=\arg\min_\tau\left\|\sum_{i=1}^N\alpha_i(x)\,\psi\big(Y_i,D_i;\tau,\hat{m}_0(X_i),\hat{m}_1(X_i),\hat{e}(X_i)\big)\right\|$$

where $\psi$ is the doubly robust AIPW-type score and $\alpha_i(x)$ are the forest-adaptive weights.

**Key Points**

- Using an **orthogonalized** local moment (rather than a naive local difference-in-means) is essential — it is what allows causal forests to remain valid under regularization/overfitting bias from the forest itself, mirroring the role of orthogonality in DML more broadly.
- Nuisance functions ($\hat{e}(X)$, $\hat{m}_d(X)$) are typically estimated via a preliminary regression forest step, and the causal forest then uses cross-fitted residuals — directly analogous to the "R-learner" approach (Nie and Wager 2021; Robinson 1988 partialling-out), sometimes referred to as the residual-on-residual regression underlying causal forest splitting.

### Honest Splitting

Causal forests use **"honesty"**: each tree is grown using one subsample to determine the splitting structure (which covariate and threshold to split on) and a **separate, disjoint** subsample to estimate the treatment effect within each resulting leaf.

```mermaid
flowchart TD
    A[Draw subsample for a single tree] --> B[Randomly split into two disjoint halves]
    B --> C[Half 1: determine tree structure via heterogeneity-maximizing splits]
    B --> D[Half 2: held out, unused for splitting decisions]
    C --> E[Apply tree structure to Half 2]
    D --> E
    E --> F[Estimate leaf-level treatment effect using ONLY Half 2 data]
    F --> G[Repeat across many trees: aggregate via adaptive weights alpha_i(x)]
    G --> H[Solve local orthogonal moment at target point x]
```

**Key Points**

- Honesty removes the bias that would otherwise arise from using the same data both to *decide where* the effect looks large (splitting) and to *estimate* how large it is (leaf estimation) — a form of the same overfitting concern that motivates cross-fitting in DML.
- The trade-off is a loss of statistical efficiency relative to non-honest trees (since only half the leaf's subsample is used for the actual effect estimate), but honesty is what enables the asymptotic **normality and valid confidence intervals** derived by Wager and Athey (2018) — without honesty, standard forest predictions have no known valid asymptotic distribution.

### Asymptotic Properties and Inference

**Key Points**

- Under honesty, appropriate subsampling (rather than bootstrap-with-replacement), and regularity conditions on tree depth/leaf size, $\hat\tau(x)$ is asymptotically normal, enabling **pointwise confidence intervals** for the CATE at any covariate value $x$ (Wager and Athey 2018).
- Variance estimation uses an **infinitesimal jackknife for forests** (Efron 2014; adapted for random forests by Wager, Hastie, and Efron 2014) — computing the covariance of tree predictions across the bootstrap/subsample resampling used to grow the forest, without requiring a full separate bootstrap procedure.
- [Inference — coverage properties of these confidence intervals in finite samples, especially in regions of sparse data or near covariate-support boundaries, are an active area of applied and simulation-based investigation] Practitioners should treat confidence intervals with more caution in low-density regions of the covariate space.

### Variable Importance and CATE Exploration

**Key Points**

- Causal forests naturally produce a **variable importance measure** for treatment effect heterogeneity — which covariates are most frequently used in splits — distinct from (and often different from) variable importance for predicting the outcome level itself.
- Standard diagnostic tools include: **Best Linear Projection (BLP)** of the CATE onto covariates (testing whether specific covariates significantly predict heterogeneity), **calibration tests** (comparing predicted vs. realized treatment effects across bins of $\hat\tau(x)$), and **Rank-Weighted Average Treatment Effect (RATE)** curves (Yadlowsky et al. 2021) for assessing whether a CATE estimator successfully targets those with larger effects.

### Relationship to Meta-Learners

| Approach | Mechanism |
| --- | --- |
| S-Learner | Single model with $D$ as a feature; $\hat\tau(x)=\hat{m}(x,1)-\hat{m}(x,0)$ |
| T-Learner | Two separate models, one per arm; $\hat\tau(x)=\hat{m}_1(x)-\hat{m}_0(x)$ |
| X-Learner | Imputes individual treatment effects, models them, combines via propensity-weighted blend |
| R-Learner | Partials out $E[Y\mid X]$ and $E[D\mid X]$, regresses residuals on each other |
| Causal Forest / GRF | Directly targets CATE heterogeneity via honest, orthogonalized local splitting |

**Key Points**

- Causal forests are closely related to the **R-learner** framework — both rely on residualizing outcome and treatment against covariates before estimating the effect function — but causal forests embed this within adaptive, locally weighted forest splitting rather than a single global second-stage regression.
- Compared to S-/T-/X-learners built from arbitrary black-box ML models, causal forests offer built-in, theoretically justified **valid statistical inference** (confidence intervals) at the cost of being restricted to the forest-based functional form.

### Practical Example (R, `grf`)

```r
library(grf)

X <- as.matrix(df[, c("age", "income", "education", "baseline_outcome")])
Y <- df$outcome
D <- df$treat

# Fit causal forest (orthogonalization, honesty, and cross-fitting are internal)
cf <- causal_forest(X, Y, D, num.trees = 4000)

# CATE estimates with confidence intervals
tau_hat <- predict(cf, estimate.variance = TRUE)
tau_hat$predictions
sqrt(tau_hat$variance.estimates)

# Average treatment effect (aggregated from the forest)
average_treatment_effect(cf, target.sample = "all")

# Variable importance for heterogeneity
variable_importance(cf)

# Best linear projection: test which covariates drive heterogeneity
best_linear_projection(cf, X)

# Test for any heterogeneity at all (omnibus test)
test_calibration(cf)
```

### Practical Example (Python, `econml`)

```python
from econml.grf import CausalForest

X = df[["age", "income", "education", "baseline_outcome"]].values
Y = df["outcome"].values
D = df["treat"].values

cf = CausalForest(n_estimators=4000, honest=True, criterion="het")
cf.fit(X, D, Y)

tau_hat, tau_lb, tau_ub = cf.predict(X, interval=True, alpha=0.05)
```

### Visualizing Heterogeneous Effects (SVG)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 300">
<text x="320" y="20" font-size="14" text-anchor="middle" font-family="sans-serif" font-weight="bold">Estimated CATE Across Covariate X (svg_diagram)</text>
<line x1="60" y1="250" x2="600" y2="250" stroke="black" stroke-width="1" />
<line x1="60" y1="40" x2="60" y2="250" stroke="black" stroke-width="1" />
<line x1="60" y1="150" x2="600" y2="150" stroke="#ccc" stroke-width="1" stroke-dasharray="3,3" />
<text x="45" y="154" font-size="9" text-anchor="end" font-family="sans-serif">0</text>
<text x="330" y="280" font-size="11" text-anchor="middle" font-family="sans-serif">Covariate X (e.g., baseline severity)</text>
<text x="20" y="150" font-size="11" text-anchor="middle" font-family="sans-serif" transform="rotate(-90 20 150)">tau(x)</text>
<path d="M80,230 C150,220 200,200 260,170 C320,140 380,90 440,70 C500,55 550,50 580,48" fill="none" stroke="#2563eb" stroke-width="2" />
<path d="M80,245 C150,238 200,222 260,196 C320,168 380,120 440,100 C500,85 550,78 580,75" fill="none" stroke="#93c5fd" stroke-width="1" stroke-dasharray="3,2" />
<path d="M80,215 C150,202 200,178 260,144 C320,112 380,60 440,40 C500,25 550,22 580,21" fill="none" stroke="#93c5fd" stroke-width="1" stroke-dasharray="3,2" />
<text x="500" y="45" font-size="10" fill="#2563eb" font-family="sans-serif">CATE + 95% CI band</text>
</svg>

### Common Pitfalls

- **Interpreting individual-tree splits causally**: any single tree's specific split points are noisy and not individually interpretable — inference should rely on the aggregated forest estimate and its variance, not on inspecting individual trees.
- **Omitting honesty** (or disabling it for perceived efficiency gains): invalidates the theoretical basis for valid confidence intervals, even though point predictions may still look reasonable.
- **Overinterpreting CATE estimates in sparse regions**: predictions at covariate values far from the bulk of the data (poor local overlap/support) can be highly variable despite reported point estimates looking precise — always cross-reference with local propensity score density.
- **Confusing forest-based variable importance for heterogeneity with importance for outcome-level prediction** — a variable can be highly predictive of $Y$ while contributing nothing to treatment effect heterogeneity, and vice versa.
- **Data dredging via CATE subgroup discovery**: exploring many covariate subgroups post hoc for "significant" heterogeneity without correcting for multiple comparisons or pre-registering hypotheses — the BLP and calibration tests are designed to guard against this but are sometimes skipped in applied work.
- Using bootstrap-with-replacement (rather than subsampling) for the underlying trees, which can invalidate the infinitesimal-jackknife variance estimator's theoretical guarantees.

**Next Steps**

- Double/Debiased Machine Learning
- Doubly Robust Estimation (AIPW)
- Meta-Learners (S-, T-, X-, R-Learners)
- Heterogeneous Treatment Effects and Policy Learning
- Neyman Orthogonality and Cross-Fitting
- Instrumental Forests (Causal Forests with Instruments)
- Best Linear Projections and RATE Curves for CATE Validation