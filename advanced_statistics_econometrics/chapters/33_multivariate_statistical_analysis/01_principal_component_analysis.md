## Principal Component Analysis


### Overview

Principal Component Analysis (PCA) is a dimensionality reduction technique that transforms a set of possibly correlated variables into a smaller set of linearly uncorrelated variables (principal components), ordered so that the first component captures the maximum possible variance in the data, each subsequent component capturing the maximum remaining variance subject to orthogonality with prior components. In econometrics, PCA underlies factor-augmented forecasting, diffusion index models, and dimension reduction for high-dimensional predictor sets.

### Mathematical Formulation

**Key Points**

Given a data matrix $X \in \mathbb{R}^{n \times p}$ (n observations, p variables), typically centered (and often standardized to unit variance), PCA seeks a linear combination $z_1 = Xw_1$ maximizing variance subject to $\|w_1\| = 1$:

$$w_1 = \arg\max_{\|w\|=1} \; \text{Var}(Xw) = \arg\max_{\|w\|=1} \; w'\Sigma w$$

where $\Sigma = \frac{1}{n-1}X'X$ is the sample covariance matrix (assuming $X$ is centered). This is solved via the eigendecomposition of $\Sigma$:

$$\Sigma = W\Lambda W'$$

where $W$ is the matrix of eigenvectors (the **loadings**, columns orthonormal) and $\Lambda = \text{diag}(\lambda_1, \dots, \lambda_p)$ is the diagonal matrix of eigenvalues, ordered $\lambda_1 \geq \lambda_2 \geq \dots \geq \lambda_p \geq 0$. The **principal components** (scores) are:

$$Z = XW$$

The $k$-th eigenvalue $\lambda_k$ equals the variance explained by the $k$-th principal component, and $\sum_k \lambda_k = \text{tr}(\Sigma) = \sum_j \text{Var}(X_j)$ (total variance is preserved, just redistributed across orthogonal directions).

### Equivalent Formulation via Singular Value Decomposition (SVD)

**Key Points**

PCA is computed in practice via the SVD of the (centered) data matrix directly, which is numerically more stable than eigendecomposing $X'X$:

$$X = U D V'$$

where $U$ is $n \times p$ with orthonormal columns, $D$ is diagonal with singular values $d_1 \geq d_2 \geq \dots \geq 0$, and $V$ is $p \times p$ orthonormal. The relationship to the eigendecomposition: $V = W$ (loadings), and $\lambda_k = d_k^2/(n-1)$ (eigenvalues of $\Sigma$ relate to squared singular values of $X$). Principal component scores are $Z = XV = UD$.

### Diagram: PCA Computational Pipeline

```mermaid
flowchart TD
    A[Raw data matrix X: n obs by p variables] --> B[Center - and optionally standardize - each column]
    B --> C{Computation method}
    C -->|Eigendecomposition| D[Compute covariance matrix Sigma = X'X / (n-1)]
    D --> E[Eigendecompose Sigma = W Lambda W']
    C -->|SVD - preferred, more stable| F[Compute SVD of X: X = U D V']
    F --> G[Loadings W = V; eigenvalues = d^2/(n-1)]
    E --> H[Principal component scores Z = X W]
    G --> H
    H --> I[Select k components via scree plot / variance explained]
    I --> J[Reduced representation Z_k for downstream analysis]
```

### Choosing the Number of Components

**Key Points**

- **Proportion of variance explained**: $\frac{\lambda_k}{\sum_j \lambda_j}$; cumulative variance explained by the first $k$ components is often reported, with common (heuristic, not theoretically derived) thresholds like 80-90%
- **Scree plot**: plotting $\lambda_k$ against $k$ and looking for an "elbow" where marginal variance explained drops sharply
- **Kaiser criterion**: retain components with $\lambda_k > 1$ (applicable specifically to standardized data, where average eigenvalue equals 1); [Inference] this rule is widely used as a quick heuristic but is generally regarded in the statistics literature as somewhat arbitrary and can retain too many or too few components depending on the data structure
- **Parallel analysis** (Horn 1965): compares observed eigenvalues to those obtained from random data of the same dimensions, retaining components whose eigenvalues exceed the corresponding random-data eigenvalues — considered a more principled and empirically better-performing alternative to the Kaiser criterion
- **Cross-validation-based selection**: for use cases where PCA feeds into a predictive model, the number of components can be chosen via out-of-sample predictive performance rather than an in-sample variance criterion

### Illustration: Scree Plot and Elbow Selection (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 280" font-family="sans-serif">
<text x="350" y="20" text-anchor="middle" font-size="16" font-weight="bold">Scree Plot: Eigenvalue by Component (svg_diagram)</text>
<line x1="80" y1="230" x2="640" y2="230" stroke="#333" stroke-width="1.5" />
<line x1="80" y1="230" x2="80" y2="50" stroke="#333" stroke-width="1.5" />
<text x="360" y="260" text-anchor="middle" font-size="11">Component index k</text>
<text x="35" y="140" text-anchor="middle" font-size="11" transform="rotate(-90 35 140)">Eigenvalue λ_k</text>
<polyline points="110,60 180,95 250,150 320,190 390,205 460,213 530,218 600,222" fill="none" stroke="#2b6cb0" stroke-width="2.5" />
<circle cx="110" cy="60" r="4" fill="#2b6cb0" />
<circle cx="180" cy="95" r="4" fill="#2b6cb0" />
<circle cx="250" cy="150" r="4" fill="#a00" />
<circle cx="320" cy="190" r="4" fill="#2b6cb0" />
<circle cx="390" cy="205" r="4" fill="#2b6cb0" />
<circle cx="460" cy="213" r="4" fill="#2b6cb0" />
<circle cx="530" cy="218" r="4" fill="#2b6cb0" />
<circle cx="600" cy="222" r="4" fill="#2b6cb0" />

<text x="250" y="175" text-anchor="middle" font-size="10" fill="#a00">"elbow" — suggested cutoff</text>

</svg>

### Standardization: Correlation Matrix vs. Covariance Matrix

**Key Points**

- PCA on the **covariance matrix** is scale-dependent: variables with larger variance dominate the first components regardless of their substantive importance, which is problematic when variables are measured in different units (e.g., GDP in billions vs. inflation rate in percentage points)
- PCA on the **correlation matrix** (equivalent to standardizing each variable to unit variance before applying PCA on the covariance matrix) removes this scale-dependence, and is the standard default in most applied econometric settings with heterogeneously scaled variables
- The choice materially changes the resulting loadings and components — this is not a minor implementation detail but a substantive modeling decision that should be made deliberately, not by software default

### PCA in Econometrics: Factor-Augmented Regression and Diffusion Indexes

**Key Points**

Stock and Watson's diffusion index / factor-augmented VAR (FAVAR) approach uses PCA to extract a small number of common factors $\hat{F}_t$ from a large panel of macroeconomic time series $X_t$ (potentially hundreds of series), then uses these estimated factors as regressors in a forecasting equation:

$$X_t = \Lambda F_t + e_t \quad \text{(factor model)}$$



$$y_{t+h} = \beta' \hat{F}_t + \gamma y_t + \varepsilon_{t+h} \quad \text{(forecasting equation)}$$

The **principal components estimator** of the factor model is exactly the PCA decomposition of $X_t$: $\hat F_t$ is recovered as the leading principal component scores. Bai and Ng (2002) established formal information-criteria-based methods for consistently selecting the number of factors $r$ in this large-panel setting, extending the heuristic scree-plot logic to a formal statistical procedure with established consistency properties as both $n$ (cross-section) and $T$ (time series) grow.

### PCA vs. Factor Analysis

| Aspect | PCA | Factor Analysis |
| --- | --- | --- |
| Model | Purely a variance-maximizing linear transformation; no error model | Explicit statistical model with common factors + idiosyncratic errors: $X = \Lambda F + e$ |
| Objective | Maximize explained variance | Explain observed covariances via a small number of latent common factors |
| Uniqueness | Components are unique (up to sign) given the data | Factor loadings are only identified up to rotation without further restrictions |
| Idiosyncratic error | Not separately modeled | Explicitly modeled and assumed uncorrelated with common factors |
| Use case in econometrics | Dimension reduction, diffusion indexes, forecasting | Structural interpretation of latent common factors (e.g., "business cycle factor") |

[Inference] In large-$n$, large-$T$ approximate factor model settings common in macroeconometrics, PCA and factor analysis estimates of the common factors often converge to similar practical results, though the two methods rest on different formal justifications and can diverge more noticeably in smaller or lower-dimensional settings.

### Practical and Statistical Caveats

**Key Points**

- **Outlier sensitivity**: PCA is based on variance, which is highly sensitive to outliers; robust PCA variants (e.g., based on robust covariance estimators) are used when outlier contamination is a concern
- **Linearity assumption**: PCA captures only linear combinations of variables; nonlinear dimension reduction (e.g., kernel PCA, autoencoders, UMAP) is required when the underlying structure is nonlinear
- **Interpretability of components**: principal components are mathematical constructs (variance-maximizing linear combinations) and may not correspond to economically meaningful concepts; loadings should be examined to assess whether a component admits a sensible substantive interpretation, but this interpretation is not guaranteed by the method itself
- **Sign and scale indeterminacy**: eigenvectors are unique only up to sign flip; software implementations may return either sign, requiring the researcher to fix sign conventions for interpretability across replications

### Practical Workflow

**Next Steps**

1. Decide whether to use the covariance or correlation matrix based on whether variables are measured on comparable scales
2. Center (and standardize, if using the correlation matrix) the data before applying PCA
3. Compute the decomposition via SVD for numerical stability rather than direct eigendecomposition of the covariance matrix
4. Select the number of components using a formal criterion (parallel analysis, Bai-Ng information criteria for factor models, or cross-validation) rather than relying solely on an arbitrary variance-explained threshold
5. Examine loadings for substantive interpretability, and assess sensitivity to outliers before finalizing the reduced representation for downstream analysis

### Related Topics

- Bai-Ng Information Criteria for Factor Number Selection
- Factor-Augmented VAR (FAVAR) and Diffusion Index Forecasting
- Approximate Factor Models for Large Panels (Stock-Watson)
- Robust PCA and Outlier-Resistant Dimension Reduction
- Kernel PCA and Nonlinear Dimensionality Reduction
- Exploratory vs. Confirmatory Factor Analysis in Econometrics