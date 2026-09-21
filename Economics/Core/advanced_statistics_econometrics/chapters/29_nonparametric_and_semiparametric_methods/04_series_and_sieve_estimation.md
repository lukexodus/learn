## Series and Sieve Estimation

### Overview

Series (sieve) estimation approximates an unknown function — most commonly a conditional mean $m(x)=E[Y\mid X=x]$ or density $f(x)$ — by a linear combination of a growing sequence of basis functions, with the number of terms increasing with sample size $N$. Rather than smoothing locally around each target point (as in kernel-based methods), series estimation fits a **single global regression** on a finite but expanding set of basis functions, making it a "sieve" that grows in flexibility as more data become available (Chen 2007 provides a comprehensive survey).

### Core Framework

Given basis functions $p_1(x),p_2(x),\dots$, the series estimator approximates:

$$m(x)\approx\sum_{k=1}^{K}\beta_k\,p_k(x)=P^K(x)'\beta$$

where $K=K(N)$ grows with sample size ($K\to\infty$ as $N\to\infty$, but $K/N\to0$). Coefficients $\hat\beta$ are typically obtained by ordinary least squares of $Y$ on the basis-transformed regressors $P^K(X)$:

$$\hat\beta=(P^K(X)'P^K(X))^{-1}P^K(X)'Y$$

**Key Points**

- Because estimation reduces to **linear regression on transformed covariates**, series estimation inherits the full computational and inferential machinery of OLS — a major practical advantage over kernel-based local methods, which require separate weighted fits at every evaluation point.
- The number of series terms $K$ plays the role that bandwidth $h$ plays in kernel methods: it is the central smoothing/complexity parameter governing the bias-variance trade-off. **More terms** ($K$ large) → lower bias, higher variance (overfitting risk); **fewer terms** ($K$ small) → higher bias, lower variance (oversmoothing/underfitting).
- As $K\to\infty$ (with $K/N\to0$), the series approximation becomes arbitrarily flexible, and under regularity conditions $\hat{m}(x)\to m(x)$ — this **sieve** property (an expanding but always finite-dimensional approximating space) is what gives the method its name and its nonparametric consistency.

### Common Basis Function Families

| Basis | Form | Typical Use |
| --- | --- | --- |
| Polynomial | $1,x,x^2,\dots,x^K$ | Simple, but poor numerical conditioning at high order |
| Orthogonal polynomials (Legendre, Chebyshev) | Orthogonalized polynomial basis | Improved numerical stability over raw polynomials |
| B-splines | Piecewise polynomial with local support | Flexible, well-conditioned, standard default |
| Fourier series | $\sin(kx),\cos(kx)$ | Periodic functions; global smoothness |
| Wavelets | Localized oscillatory basis | Functions with localized irregular features (jumps, spikes) |

**Key Points**

- Raw (unorthogonalized) high-degree **polynomial bases** suffer from severe multicollinearity and numerical instability (the classic Runge's phenomenon of oscillation near boundaries) — orthogonal polynomial or spline bases are strongly preferred in practice for anything beyond low-order approximation.
- **B-splines** (piecewise polynomials joined smoothly at "knots") are the most common modern default: they combine local flexibility (a change in one region does not distort the fit far away, unlike global polynomials) with good numerical conditioning.
- **Knot placement** for splines (number and location of the piecewise breakpoints) is itself a smoothing-parameter choice analogous to bandwidth or series length $K$ — more knots increase flexibility and variance; fewer knots increase smoothness and bias.

### Selecting the Number of Terms (K)

```mermaid
flowchart TD
    A[Choose basis family: polynomial, spline, Fourier] --> B[Choose selection method for K]
    B --> C[Cross-validation: minimize CV prediction error over candidate K]
    B --> D[Information criteria: AIC, BIC, Mallows Cp]
    B --> E[Rule-of-thumb rate: K proportional to N^(1/(2r+1))]
    C --> F[Fit OLS of Y on P^K(X) for selected K]
    D --> F
    E --> F
    F --> G[Obtain m_hat(x) = P^K(x)' beta_hat]
    G --> H[Construct confidence bands accounting for series approximation bias]
```

**Key Points**

- **Cross-validation** (leave-one-out or K-fold) directly minimizes estimated out-of-sample prediction error over a grid of candidate series lengths — the most commonly used data-driven approach in applied series estimation.
- **Information criteria** (AIC, BIC, Mallows $C_p$) penalize model complexity analytically rather than via resampling, offering a computationally cheaper alternative, though the penalty structure was originally derived for parametric model selection and its optimality properties in the sieve/nonparametric context require separate theoretical justification.
- Theoretical work characterizes the **optimal rate** at which $K$ should grow with $N$ as a function of the smoothness of the true underlying function (e.g., $K\propto N^{1/(2r+1)}$ for a function with $r$ continuous derivatives) — informative for understanding asymptotic behavior, though rarely directly implementable without knowing the true smoothness in advance, which is precisely what is unknown in practice.

### Series Estimation vs. Kernel Methods

| Property | Series/Sieve | Kernel/Local Polynomial |
| --- | --- | --- |
| Estimation mechanism | Single global least-squares fit | Separate local weighted fit per evaluation point |
| Smoothing parameter | Number of terms $K$ (or knots) | Bandwidth $h$ |
| Computational cost | Fast (single regression) | Can be slower (per-point fitting), though modern implementations are efficient |
| Global vs. local smoothness | Naturally imposes some global smoothness | More naturally adapts to local features |
| Standard inference tools | Directly inherits OLS-based inference | Requires specialized nonparametric SE formulas |
| Curse of dimensionality | Still present, but additive/interaction structure is easy to impose | Present, generally more severe without explicit structure |

**Key Points**

- Series methods extend naturally to **multivariate settings with additive or low-order interaction structure** (e.g., a tensor-product spline basis, or an additive model summing univariate spline bases across covariates) — a natural way to partially mitigate the curse of dimensionality relative to fully unrestricted multivariate kernel smoothing.
- Because series/sieve estimation is fundamentally a linear-in-parameters regression, it integrates naturally with standard econometric tools: instrumental variables (sieve IV/nonparametric IV), fixed effects, and clustered standard errors all extend relatively directly, which is a significant practical advantage in applied econometric work relative to kernel-based alternatives.

### Sieve Estimation in Semiparametric and Structural Models

**Key Points**

- Sieve methods are widely used as a building block within **semiparametric estimators** — e.g., estimating an unknown link function in a partially linear model, or an unknown reduced-form function within a structural model — where the sieve approximates only the nonparametric *component* while parametric structure is retained elsewhere.
- **Nonparametric instrumental variables (NPIV)** estimation, which recovers an unknown structural function under an ill-posed inverse problem, commonly relies on sieve approximation for both the structural function and instrument-side basis expansion (Newey and Powell 2003; Ai and Chen 2003 provide foundational treatments).
- Sieve estimators also underlie modern **machine learning nuisance function estimation** within DML/AIPW frameworks in some implementations — series regression (e.g., with a lasso penalty for basis selection in high dimensions) is one valid choice of ML method for the nuisance functions in double/debiased machine learning, alongside random forests or boosting.

### Practical Example (R, `splines` / base)

```r
library(splines)

# B-spline basis regression (cubic, 5 interior knots)
model_spline <- lm(y ~ bs(x, degree = 3, df = 8), data = df)

# Compare across series lengths via cross-validation (using caret)
library(caret)
train_control <- trainControl(method = "cv", number = 10)
tuned <- train(
  y ~ x,
  data = df,
  method = "gamSpline",       # or manually loop over df values for bs()
  trControl = train_control
)

x_grid <- data.frame(x = seq(min(df$x), max(df$x), length.out = 200))
pred <- predict(model_spline, newdata = x_grid)
```

### Practical Example (Python, `patsy` / `scikit-learn`)

```python
from sklearn.preprocessing import SplineTransformer
from sklearn.linear_model import LinearRegression
from sklearn.pipeline import make_pipeline
from sklearn.model_selection import GridSearchCV
import numpy as np

# B-spline series regression with CV-selected number of knots
pipe = make_pipeline(
    SplineTransformer(degree=3, n_knots=5),
    LinearRegression()
)

param_grid = {"splinetransformer__n_knots": [3, 5, 7, 10, 15]}
grid = GridSearchCV(pipe, param_grid, cv=10, scoring="neg_mean_squared_error")
grid.fit(x.reshape(-1, 1), y)

best_K = grid.best_params_["splinetransformer__n_knots"]
y_fit = grid.predict(x_grid.reshape(-1, 1))
```

### Visualizing Series Length Sensitivity (SVG)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 300">
<text x="320" y="20" font-size="14" text-anchor="middle" font-family="sans-serif" font-weight="bold">Effect of Series Length K on Fit (svg_diagram)</text>
<line x1="60" y1="250" x2="600" y2="250" stroke="black" stroke-width="1" />
<line x1="60" y1="40" x2="60" y2="250" stroke="black" stroke-width="1" />
<text x="330" y="280" font-size="11" text-anchor="middle" font-family="sans-serif">x</text>
<text x="20" y="150" font-size="11" text-anchor="middle" font-family="sans-serif" transform="rotate(-90 20 150)">Y</text>
<circle cx="90" cy="210" r="3" fill="#999" />
<circle cx="130" cy="170" r="3" fill="#999" />
<circle cx="170" cy="200" r="3" fill="#999" />
<circle cx="210" cy="140" r="3" fill="#999" />
<circle cx="250" cy="180" r="3" fill="#999" />
<circle cx="290" cy="110" r="3" fill="#999" />
<circle cx="340" cy="150" r="3" fill="#999" />
<circle cx="390" cy="90" r="3" fill="#999" />
<circle cx="440" cy="130" r="3" fill="#999" />
<circle cx="490" cy="80" r="3" fill="#999" />
<circle cx="540" cy="100" r="3" fill="#999" />
<line x1="70" y1="200" x2="580" y2="110" stroke="#dc2626" stroke-width="2" />
<text x="480" y="130" font-size="10" fill="#dc2626" font-family="sans-serif">K too small (linear, underfits)</text>
<path d="M70,205 C150,175 200,150 250,160 C300,175 340,130 390,95 C440,120 480,85 540,95" fill="none" stroke="#16a34a" stroke-width="2.5" />
<text x="220" y="230" font-size="10" fill="#16a34a" font-family="sans-serif">K well-chosen</text>
<path d="M70,215 C90,190 110,225 130,175 C150,155 170,215 190,180 C220,140 240,195 260,150 C290,105 310,175 340,130 C365,105 390,130 410,80 C430,115 460,90 480,75 C500,110 520,70 540,90" fill="none" stroke="#2563eb" stroke-width="1.5" />
<text x="480" y="55" font-size="10" fill="#2563eb" font-family="sans-serif">K too large (overfits)</text>
</svg>

### Common Pitfalls

- **Using raw high-degree polynomial bases** rather than orthogonal polynomials or splines, leading to severe numerical instability, multicollinearity, and erratic boundary behavior (Runge's phenomenon) — a common and avoidable implementation error.
- **Selecting $K$ (or knot count/placement) via visual inspection alone** rather than a formal, reproducible cross-validation or information-criterion procedure.
- **Ignoring series approximation bias when constructing confidence intervals**: standard OLS-based standard errors from the fitted series regression do not automatically account for the bias introduced by truncating the series at a finite $K$ — valid nonparametric inference requires care (e.g., appropriate undersmoothing, or specialized sieve-based inference theory).
- **Applying unrestricted multivariate series/tensor-product bases without additive or low-interaction structure**, reintroducing the same curse-of-dimensionality problems series methods can otherwise help mitigate.
- **Extrapolating series fits beyond the support of the observed data** — like any regression-based method, series estimation can produce spurious, poorly-behaved predictions outside the region where the basis functions were fit, an issue that can be especially pronounced for global bases like raw polynomials.

**Next Steps**

- Nonparametric Regression (Kernel and Local Polynomial)
- Bandwidth Selection Methods
- Semiparametric Additive and Single-Index Models
- Nonparametric Instrumental Variables (NPIV)
- Smoothing Splines
- Regularized Regression (Lasso, Ridge) as Nuisance Estimators in DML