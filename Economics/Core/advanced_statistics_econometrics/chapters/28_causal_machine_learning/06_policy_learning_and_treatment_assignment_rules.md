## Policy Learning and Treatment Assignment Rules

### Overview

Policy learning addresses a distinct but closely related problem to heterogeneous treatment effect estimation: rather than merely *estimating* how treatment effects vary across individuals ($\tau(x)$), policy learning seeks to **learn an optimal treatment assignment rule** — a decision function $\pi(x)\in\{0,1\}$ mapping covariates to a treatment recommendation — that maximizes expected social welfare (or, more precisely, the expected value of the assigned-outcome) subject to constraints such as budget limits (Manski 2004; Kitagawa and Tetenov 2018; Athey and Wager 2021).

### The Policy Learning Objective

Given a class of candidate policies $\Pi$ (e.g., depth-limited decision trees, linear threshold rules), policy learning solves:

$$\hat\pi=\arg\max_{\pi\in\Pi}\;\hat{V}(\pi)=\frac{1}{N}\sum_{i=1}^N\left[\pi(X_i)\hat{Y}_i(1)+(1-\pi(X_i))\hat{Y}_i(0)\right]$$

where $\hat{V}(\pi)$ is an estimate of the **policy value** (expected outcome under policy $\pi$), typically constructed via a doubly robust/AIPW-style score to remain valid under nuisance model misspecification.

**Key Points**

- This differs fundamentally from CATE estimation: policy learning directly optimizes a **decision rule** rather than a continuous effect-size function, and the loss/objective used (welfare/regret) differs from the squared-error loss used to fit $\hat\tau(x)$.
- A policy $\pi$ need not simply threshold an estimated $\hat\tau(x)$ at zero — optimal policies can differ from naive "treat if $\hat\tau(x)>0$" rules, particularly when the policy class $\Pi$ is restricted (e.g., simple, interpretable rules) or when treatment carries a cost.
- The **policy class** $\Pi$ is a crucial modeling choice: unrestricted (fully flexible, individual-level) policies risk overfitting and lack interpretability/implementability; restricted classes (e.g., shallow trees, linear rules over a few covariates) trade some welfare for transparency and real-world deployability.

### Doubly Robust Policy Value Estimation

$$\hat{V}(\pi)=\frac{1}{N}\sum_{i=1}^N\Big[\hat{m}_{\pi(X_i)}(X_i)+\frac{\mathbb{1}\{D_i=\pi(X_i)\}}{\hat{e}_{\pi(X_i)}(X_i)}\big(Y_i-\hat{m}_{\pi(X_i)}(X_i)\big)\Big]$$

**Key Points**

- This AIPW-style construction ensures $\hat{V}(\pi)$ is a **doubly robust, Neyman-orthogonal** estimate of the true policy value — consistent if either the outcome model or the propensity model is correctly specified, mirroring the doubly robust ATE estimator but evaluated at the policy-assigned treatment rather than the observed treatment.
- Using this AIPW-augmented value function (rather than a naive plug-in) is what allows the subsequent optimization step to inherit statistical guarantees on the learned policy's regret, rather than simply optimizing a potentially biased objective.

### Statistical Guarantees: Regret Bounds

The key theoretical quantity is **regret**: how much expected welfare is lost by using the learned policy $\hat\pi$ instead of the true optimal policy $\pi^*$ within class $\Pi$:

$$R(\hat\pi)=V(\pi^*)-V(\hat\pi)$$

**Key Points**

- Kitagawa and Tetenov (2018) establish that policies learned by maximizing an AIPW-augmented empirical welfare criterion over a policy class with bounded complexity (e.g., VC dimension) achieve regret that shrinks at rate $O(N^{-1/2})$ — matching the best achievable rate for this class of problems.
- This result parallels classical statistical learning theory (empirical risk minimization bounds) but is adapted specifically to the causal policy-value estimation setting, where the "labels" ($Y_i(1)$, $Y_i(0)$) are only partially observed and must be estimated via the doubly robust score.
- Restricting $\Pi$ to a lower-complexity class tightens these regret bounds (faster convergence, less overfitting risk) at the cost of potentially excluding the truly optimal unrestricted policy.

### Estimation Workflow

```mermaid
flowchart TD
    A[Estimate nuisance functions: outcome model, propensity score] --> B[Construct doubly robust AIPW scores per unit]
    B --> C[Define policy class Pi: e.g., depth-2 tree, linear threshold]
    C --> D[Maximize empirical policy value over Pi using AIPW scores]
    D --> E[Obtain learned policy pi_hat]
    E --> F[Estimate policy value V(pi_hat) via cross-fitting / sample-splitting]
    F --> G[Compare to baseline: treat-all, treat-none, or existing policy]
    G --> H[Assess regret bounds / confidence intervals on policy value]
```

**Key Points**

- Cross-fitting/sample-splitting is standard practice here as well: the same data should not be used both to *learn* the policy and to *evaluate* its value, or the resulting welfare estimate will be optimistically biased — an overfitting concern directly analogous to that in DML and causal forests.
- A common evaluation baseline compares the learned policy's estimated value against simple benchmarks: **treat-everyone**, **treat-no-one**, and (where available) the **existing/status-quo assignment rule** — a learned policy is only useful if it meaningfully outperforms these.

### Interpretable Policy Classes: Policy Trees

**Key Points**

- A widely used restricted policy class is the **shallow decision tree** (policy tree), which recursively partitions the covariate space into a small number of regions, each assigned a fixed treatment recommendation — directly interpretable by practitioners (e.g., clinicians, program administrators) as a simple decision rule ("treat if age > 50 and income < X").
- Depth-2 policy trees (partitioning on at most two sequential covariate splits) are common in applied work as a balance between flexibility and interpretability/implementability, though the appropriate depth is application-specific.
- The `policytree` package (Athey and Wager, building on the `grf` ecosystem) implements exact tree search (rather than greedy splitting) over small policy classes, directly optimizing the doubly robust welfare criterion.

### Practical Example (R, `policytree`)

```r
library(grf)
library(policytree)

X <- as.matrix(df[, c("age", "income", "education", "baseline_outcome")])
Y <- df$outcome
D <- df$treat

# Step 1: doubly robust scores via causal forest
cf <- causal_forest(X, Y, D)
dr_scores <- double_robust_scores(cf)

# Step 2: learn a depth-2 interpretable policy tree
tree <- policy_tree(X, dr_scores, depth = 2)
print(tree)
plot(tree)

# Step 3: evaluate learned policy on held-out/cross-fitted data
predicted_action <- predict(tree, X)
```

### Practical Example (Python, `econml` policy learning)

```python
from econml.policy import PolicyTree
from econml.dr import LinearDRLearner
from sklearn.ensemble import RandomForestRegressor, RandomForestClassifier

X = df[["age", "income", "education", "baseline_outcome"]].values
Y = df["outcome"].values
D = df["treat"].values

# Doubly robust CATE / DR scores
dr_learner = LinearDRLearner(
    model_regression=RandomForestRegressor(n_estimators=300),
    model_propensity=RandomForestClassifier(n_estimators=300)
)
dr_learner.fit(Y, D, X=X)

# Learn interpretable policy tree
policy = PolicyTree(max_depth=2)
policy.fit(X, dr_learner.effect(X).reshape(-1, 1))
recommended_treatment = policy.predict(X)
```

### Visualizing a Policy Tree (SVG)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 300">
<text x="320" y="20" font-size="14" text-anchor="middle" font-family="sans-serif" font-weight="bold">Depth-2 Policy Tree (svg_diagram)</text>
<rect x="270" y="45" width="120" height="40" fill="#fef08a" stroke="#333" />
<text x="330" y="70" font-size="11" text-anchor="middle" font-family="sans-serif">age &gt; 50?</text>
<line x1="300" y1="85" x2="180" y2="130" stroke="#333" />
<line x1="360" y1="85" x2="480" y2="130" stroke="#333" />
<text x="220" y="110" font-size="10" font-family="sans-serif">No</text>
<text x="440" y="110" font-size="10" font-family="sans-serif">Yes</text>
<rect x="120" y="130" width="120" height="40" fill="#fef08a" stroke="#333" />
<text x="180" y="155" font-size="10" text-anchor="middle" font-family="sans-serif">income &lt; 40k?</text>
<rect x="420" y="130" width="120" height="40" fill="#fef08a" stroke="#333" />
<text x="480" y="155" font-size="10" text-anchor="middle" font-family="sans-serif">baseline &gt; 3?</text>
<line x1="150" y1="170" x2="90" y2="210" stroke="#333" />
<line x1="210" y1="170" x2="270" y2="210" stroke="#333" />
<line x1="450" y1="170" x2="390" y2="210" stroke="#333" />
<line x1="510" y1="170" x2="570" y2="210" stroke="#333" />
<rect x="40" y="210" width="100" height="35" fill="#bbf7d0" stroke="#333" />
<text x="90" y="232" font-size="10" text-anchor="middle" font-family="sans-serif">Treat</text>
<rect x="220" y="210" width="100" height="35" fill="#fecaca" stroke="#333" />
<text x="270" y="232" font-size="10" text-anchor="middle" font-family="sans-serif">Don't treat</text>
<rect x="340" y="210" width="100" height="35" fill="#fecaca" stroke="#333" />
<text x="390" y="232" font-size="10" text-anchor="middle" font-family="sans-serif">Don't treat</text>
<rect x="520" y="210" width="100" height="35" fill="#bbf7d0" stroke="#333" />
<text x="570" y="232" font-size="10" text-anchor="middle" font-family="sans-serif">Treat</text>
</svg>

### Constrained Policy Learning

**Key Points**

- Real-world deployment often requires respecting a **budget constraint** — treating at most a fixed fraction or number of individuals — which converts the problem into a constrained welfare-maximization problem, solvable by thresholding an estimated priority score (e.g., $\hat\tau(x)$ or a doubly robust ranking score) at the level implied by the budget.
- **Fairness constraints** (e.g., equal treatment rates across demographic groups, or parity in policy value delivered to different subgroups) can be incorporated as additional constraints on the optimization, an active area connecting policy learning to the algorithmic fairness literature. [Speculation — the specific fairness formalization appropriate for a given application is a normative/contextual choice, not a purely statistical one]

### Common Pitfalls

- **Evaluating policy value on the same data used to learn the policy** — produces optimistically biased welfare estimates; cross-fitting/sample-splitting between learning and evaluation is essential.
- **Naively thresholding CATE estimates at zero** and calling this the "optimal policy" without accounting for treatment costs, budget constraints, or the statistical noise in $\hat\tau(x)$ near the threshold.
- **Choosing an overly flexible policy class** without appropriate complexity control, leading to overfit, poorly-generalizing, and potentially uninterpretable assignment rules.
- **Ignoring positivity/overlap when constructing doubly robust scores** — the same propensity score instability that affects AIPW/CATE estimation propagates into policy value estimation and learned policy quality.
- **Failing to benchmark against simple baselines** (treat-all, treat-none, status quo) — a sophisticated learned policy that does not clearly outperform simple alternatives provides limited practical value despite methodological sophistication.
- Overlooking distributional/fairness implications of a welfare-maximizing policy that may systematically favor or disadvantage particular subgroups, even when statistically well-estimated.

**Next Steps**

- Heterogeneous Treatment Effect Estimation
- Causal Forests and Generalized Random Forests
- Doubly Robust Estimation
- Double/Debiased Machine Learning
- Best Linear Projections and RATE Curves
- Algorithmic Fairness in Treatment Assignment
- Constrained Optimization Under Budget/Capacity Limits