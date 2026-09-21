## Nonparametric Regression


### Overview

Nonparametric regression estimates the conditional mean function $m(x)=E[Y\mid X=x]$ without imposing a parametric functional form (linear, quadratic, or otherwise), instead letting the data determine the shape of the relationship locally. This chapter area covers the two dominant estimator families — kernel-based (Nadaraya-Watson) and local polynomial regression — along with their bias-variance properties, bandwidth dependence, and the boundary-bias problem that motivates local polynomial methods over pure kernel smoothing.

### The Nadaraya-Watson Estimator

The Nadaraya-Watson (NW) kernel regression estimator (Nadaraya 1964; Watson 1964) is a locally weighted average of the response:

$$\hat{m}_{NW}(x)=\frac{\sum_{i=1}^N K\left(\frac{x-X_i}{h}\right)Y_i}{\sum_{i=1}^N K\left(\frac{x-X_i}{h}\right)}$$

**Key Points**

- This is equivalent to a **locally weighted constant (local intercept-only) regression**: at each target point $x$, NW fits a weighted average of nearby $Y_i$ values, with weights determined by kernel proximity in $X$.
- As with kernel density estimation, the bandwidth $h$ governs the bias-variance trade-off: small $h$ yields low bias but high variance (the fit is jumpy, driven by few nearby points); large $h$ yields low variance but high bias (the fit oversmooths genuine curvature).
- NW inherits KDE's general theoretical machinery, since $\hat m_{NW}(x)$ can be derived as a ratio of two kernel density-type estimates (the joint density of $(X,Y)$ weighted by $Y$, divided by the marginal density of $X$).

### The Boundary Bias Problem

**Key Points**

- The Nadaraya-Watson estimator suffers from **substantial bias at the boundaries** of the covariate support (and in regions of sparse data), because the kernel window becomes asymmetric — near the left boundary, for instance, all the weighted neighbors lie to the right, systematically biasing the local average.
- This boundary bias is a first-order (not merely a minor, asymptotically negligible) problem — it does not vanish as $N\to\infty$ at the same rate as the interior bias, making it a serious practical concern whenever estimation near the edges of $X$'s support matters (as it often does, e.g., near a regression discontinuity cutoff).
- This limitation is the primary motivation for **local polynomial regression**, which corrects boundary bias automatically as a byproduct of fitting a local slope (or higher-order terms) rather than a local constant.

### Local Polynomial Regression

At each target point $x$, fit a weighted polynomial regression of order $p$ using only data near $x$ (weighted by the kernel):

$$\min_{\beta_0,\dots,\beta_p}\sum_{i=1}^N K\left(\frac{X_i-x}{h}\right)\left[Y_i-\beta_0-\beta_1(X_i-x)-\cdots-\beta_p(X_i-x)^p\right]^2$$

The estimate is $\hat{m}(x)=\hat\beta_0$ (the local intercept, evaluated at $X_i-x=0$).

```mermaid
flowchart TD
    A[Choose target point x] --> B[Assign kernel weights to nearby observations]
    B --> C[Fit weighted polynomial regression of order p locally]
    C --> D[Extract fitted intercept as m_hat(x)]
    D --> E{More target points needed?}
    E -->|Yes| A
    E -->|No| F[Assemble full fitted curve across grid of x values]
```

**Key Points**

- **Local constant (p=0)** regression is exactly the Nadaraya-Watson estimator — local polynomial regression is a strict generalization.
- **Local linear (p=1)** regression automatically corrects the boundary bias problem that plagues local constant/NW regression — this "automatic boundary correction" property is a major reason local linear regression is preferred as the default choice in most applied nonparametric regression work, and is the standard choice in regression discontinuity estimation specifically.
- **Local quadratic (p=2)** and higher orders further reduce bias in regions of high curvature (at the cost of increased variance), but the **odd-order advantage** result (Fan and Gijbels 1996) shows that odd-order local polynomials (linear, cubic) have a bias advantage over the adjacent even order at interior points, reinforcing local linear as a particularly favorable default.
- Higher-order local polynomials require correspondingly larger local sample sizes (more data within the kernel window) to estimate additional parameters reliably, so the choice of $p$ interacts with both bandwidth and local data density.

### Bias-Variance Properties Compared

| Estimator | Boundary bias | Interior bias order | Typical use |
| --- | --- | --- | --- |
| Nadaraya-Watson (local constant) | Severe | $O(h^2)$ | Simple, fast baseline; rarely preferred in practice |
| Local Linear | Automatically corrected | $O(h^2)$ | Standard default; RDD estimation |
| Local Quadratic | Corrected | $O(h^4)$ in favorable cases | High-curvature regions; RDD bias-correction |

### Other Nonparametric Regression Approaches

**Key Points**

- **Series/sieve estimators** (polynomial series, splines, Fourier series) approximate $m(x)$ by a growing linear combination of basis functions as $N$ increases, rather than local weighting — an alternative nonparametric strategy with different bias-variance and computational trade-offs, related in spirit to (but distinct from) local polynomial methods.
- **Smoothing splines** minimize a penalized sum of squares that trades off fit against curvature (via a roughness penalty), with the penalty weight playing an analogous role to the bandwidth in kernel-based methods.
- **Regression trees and random forests** offer a fully nonparametric, adaptive alternative that partitions the covariate space rather than smoothing locally — connecting this topic directly to the tree-based causal ML methods (causal forests, GRF) covered elsewhere in this curriculum, which build on standard regression forests.

### Multivariate Extension and the Curse of Dimensionality

**Key Points**

- Extending kernel/local polynomial regression to multiple covariates faces the same curse-of-dimensionality problem as multivariate KDE — data becomes sparse in local neighborhoods as dimension grows, degrading estimation accuracy sharply.
- **Additive models** ($m(x)=\sum_j g_j(x_j)$, estimated via backfitting) and **single-index models** ($m(x)=g(x'\beta)$ for an unknown link function $g$ and unknown index $\beta$) are common semiparametric compromises that retain interpretability and mitigate the curse of dimensionality by restricting how covariates enter the regression function, relative to a fully unrestricted multivariate nonparametric surface.

### Practical Example (R, `np` / `locpol`)

```r
library(np)

# Nadaraya-Watson with cross-validated bandwidth
bw_nw <- npregbw(y ~ x, regtype = "lc")   # local constant
model_nw <- npreg(bws = bw_nw)

# Local linear regression (automatic boundary correction)
bw_ll <- npregbw(y ~ x, regtype = "ll")   # local linear
model_ll <- npreg(bws = bw_ll)

plot(model_ll, plot.errors.method = "asymptotic")

# Alternative: locpol package for explicit polynomial order control
library(locpol)
fit_locquad <- locpol(y ~ x, data = df, deg = 2, kernel = gaussK)
```

### Practical Example (Python, `statsmodels` / `scikit-learn`)

```python
from statsmodels.nonparametric.kernel_regression import KernelReg
import numpy as np

# Local linear kernel regression, CV-selected bandwidth
kr = KernelReg(endog=y, exog=x, var_type="c", reg_type="ll", bw="cv_ls")
y_fit, marginal_effects = kr.fit(x_grid)

# Local constant (Nadaraya-Watson) for comparison
kr_lc = KernelReg(endog=y, exog=x, var_type="c", reg_type="lc", bw="cv_ls")
y_fit_lc, _ = kr_lc.fit(x_grid)
```

### Visualizing Boundary Bias (SVG)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 300">
<text x="320" y="20" font-size="14" text-anchor="middle" font-family="sans-serif" font-weight="bold">Nadaraya-Watson vs. Local Linear at the Boundary (svg_diagram)</text>
<line x1="60" y1="250" x2="600" y2="250" stroke="black" stroke-width="1" />
<line x1="60" y1="40" x2="60" y2="250" stroke="black" stroke-width="1" />
<text x="330" y="280" font-size="11" text-anchor="middle" font-family="sans-serif">x</text>
<text x="20" y="150" font-size="11" text-anchor="middle" font-family="sans-serif" transform="rotate(-90 20 150)">Y</text>
<circle cx="90" cy="220" r="3" fill="#999" />
<circle cx="110" cy="200" r="3" fill="#999" />
<circle cx="130" cy="180" r="3" fill="#999" />
<circle cx="150" cy="160" r="3" fill="#999" />
<circle cx="170" cy="145" r="3" fill="#999" />
<circle cx="200" cy="120" r="3" fill="#999" />
<circle cx="240" cy="100" r="3" fill="#999" />
<circle cx="290" cy="85" r="3" fill="#999" />
<path d="M60,235 C100,200 150,155 200,120 C250,90 300,80 340,80" fill="none" stroke="black" stroke-width="2" stroke-dasharray="5,3" />
<text x="200" y="60" font-size="10" font-family="sans-serif">True m(x)</text>
<path d="M60,190 C110,180 150,160 200,120 C250,90 300,80 340,80" fill="none" stroke="#2563eb" stroke-width="2" />
<text x="80" y="175" font-size="9" fill="#2563eb" font-family="sans-serif">Local linear (corrects)</text>
<path d="M60,150 C110,155 150,155 200,120 C250,90 300,80 340,80" fill="none" stroke="#dc2626" stroke-width="2" />
<text x="70" y="140" font-size="9" fill="#dc2626" font-family="sans-serif">NW (biased at boundary)</text>
</svg>

### Common Pitfalls

- **Using Nadaraya-Watson (local constant) regression by default without recognizing its boundary bias** — particularly problematic in applications like regression discontinuity design, where estimation at the cutoff is exactly a boundary-estimation problem.
- **Selecting bandwidth without accounting for the estimator type**: an appropriate bandwidth for local constant regression is not automatically appropriate for local linear or local quadratic regression, since the bias-variance trade-off differs by polynomial order.
- **Overfitting with high-order local polynomials in sparse data regions**, where too few local observations are available to reliably estimate the additional polynomial coefficients, producing erratic fits despite nominally lower asymptotic bias.
- **Applying fully nonparametric multivariate regression without considering dimensionality**, when a semiparametric additive or single-index model would provide more stable and interpretable estimates with the same or less data.
- **Ignoring standard error/confidence band construction complexities**: nonparametric regression standard errors require care (accounting for bias in addition to variance) and naive parametric-style confidence intervals can be misleading without appropriate bias-correction or undersmoothing adjustments.

**Next Steps**

- Kernel Density Estimation
- Bandwidth Selection Methods
- Regression Discontinuity Designs (local linear estimation at the cutoff)
- Semiparametric Additive and Single-Index Models
- Causal Forests and Generalized Random Forests
- Smoothing Splines and Series Estimators