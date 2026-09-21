## Linear Algebra and Matrix Methods


### Overview

Linear algebra provides the computational and structural framework underlying multi-asset derivatives pricing, portfolio risk management, and the numerical methods used to solve pricing PDEs and calibrate models. Matrices efficiently represent covariance structures across many assets, factor models used for risk decomposition, the discretized operators in finite-difference PDE solvers, and the transformations at the heart of principal component analysis for yield curve modeling. This section covers the core matrix concepts and their standard applications in derivatives and risk contexts.

### Vectors, Matrices, and Basic Operations

A **vector** $\mathbf{x} \in \mathbb{R}^n$ is an ordered list of $n$ real numbers; in finance, commonly used to represent a portfolio's asset weights, a set of cash flows, or a vector of factor exposures. A **matrix** $A \in \mathbb{R}^{m \times n}$ is a rectangular array of numbers with $m$ rows and $n$ columns.

**Key operations**:

- **Matrix multiplication**: $(AB)_{ij} = \sum_k A_{ik}B_{kj}$, requiring the number of columns of $A$ to equal the number of rows of $B$; not commutative in general ($AB \neq BA$)
- **Transpose**: $(A^T)_{ij} = A_{ji}$, flipping rows and columns
- **Matrix inverse**: $A^{-1}$, satisfying $AA^{-1} = A^{-1}A = I$ (the identity matrix), exists only for square matrices with nonzero determinant (i.e., **non-singular** matrices)
- **Trace**: $\text{tr}(A) = \sum_i A_{ii}$, the sum of diagonal elements; used in various risk decomposition and PDE contexts (e.g., appears in multi-dimensional Itô's lemma formulations)

### Systems of Linear Equations

A system $A\mathbf{x} = \mathbf{b}$ arises throughout derivatives pricing — for example, in solving the tridiagonal linear systems generated at each time step of an implicit finite-difference PDE scheme (covered in the differential equations section of this chapter), or in solving for portfolio weights that replicate a target set of cash flows.

**Key Points**:

- A unique solution $\mathbf{x} = A^{-1}\mathbf{b}$ exists if and only if $A$ is non-singular (equivalently, $\det(A) \neq 0$, equivalently $A$ has full rank)
- In practice, explicit matrix inversion is rarely used computationally for solving such systems due to numerical inefficiency and instability; instead, **LU decomposition**, **Gaussian elimination**, or specialized algorithms for structured matrices (e.g., the **Thomas algorithm** for tridiagonal systems, which arise naturally from finite-difference PDE discretizations) are used
- [Inference] The Thomas algorithm's efficiency (solving a tridiagonal system in $O(n)$ operations rather than the $O(n^3)$ of general Gaussian elimination) is a standard reason it is the typical choice for the tridiagonal systems produced by implicit and Crank-Nicolson finite-difference PDE solvers, though the exact implementation details vary by numerical library and specific PDE discretization scheme

### Eigenvalues and Eigenvectors

For a square matrix $A$, a scalar $\lambda$ and nonzero vector $\mathbf{v}$ satisfying:

$$A\mathbf{v} = \lambda\mathbf{v}$$

are called an **eigenvalue** and corresponding **eigenvector** of $A$. Eigenvalues are found as roots of the **characteristic polynomial** $\det(A - \lambda I) = 0$.

**Key Points**:

- For a **symmetric matrix** (such as a covariance matrix, since $\text{Cov}(X,Y) = \text{Cov}(Y,X)$), all eigenvalues are real, and eigenvectors corresponding to distinct eigenvalues are orthogonal — this is the foundational fact enabling **spectral decomposition**: $A = Q\Lambda Q^T$, where $Q$ is an orthogonal matrix of eigenvectors and $\Lambda$ is a diagonal matrix of eigenvalues
- A symmetric matrix is **positive semi-definite** if and only if all its eigenvalues are non-negative; a valid covariance matrix must be positive semi-definite (and, for a non-degenerate set of assets, typically positive definite), since variance cannot be negative for any linear combination of the underlying variables — this is a key validity check when constructing or estimating covariance matrices in practice

### Covariance Matrices in Multi-Asset Pricing

For a portfolio of $n$ assets with return vector $\mathbf{r} = (r_1, \ldots, r_n)^T$, the **covariance matrix** $\Sigma$ is the $n \times n$ matrix with:

$$\Sigma_{ij} = \text{Cov}(r_i, r_j), \qquad \Sigma_{ii} = \text{Var}(r_i)$$

**Portfolio variance**, for a vector of portfolio weights $\mathbf{w}$:

$$\text{Var}(\mathbf{w}^T\mathbf{r}) = \mathbf{w}^T \Sigma \mathbf{w}$$

**Key Points**:

- This quadratic form is the standard building block for portfolio risk calculations, Markowitz mean-variance optimization, and multi-asset option pricing (e.g., basket options, spread options) where the joint distribution of several correlated underlyings must be modeled
- $\Sigma$ can be decomposed as $\Sigma = D R D$, where $D$ is a diagonal matrix of individual asset volatilities and $R$ is the correlation matrix — a useful decomposition for separately calibrating volatility levels and cross-asset correlations
- Estimated covariance matrices from historical data can suffer from **estimation error**, particularly when the number of assets $n$ is large relative to the number of historical observations, sometimes producing matrices that are technically positive semi-definite but numerically near-singular or unstable for downstream use (e.g., in optimization routines that require inverting $\Sigma$) — this is a well-known practical challenge in portfolio construction and multi-asset risk modeling, commonly addressed via shrinkage estimators or factor-model-based covariance construction

### Cholesky Decomposition and Correlated Monte Carlo Simulation

The **Cholesky decomposition** factors a symmetric positive-definite matrix $\Sigma$ as:

$$\Sigma = LL^T$$

where $L$ is a lower-triangular matrix.

**Key application — simulating correlated asset paths**: Given independent standard normal random variables $\mathbf{Z} = (Z_1, \ldots, Z_n)^T$, the transformed vector:

$$\mathbf{X} = L\mathbf{Z}$$

has covariance matrix $\text{Cov}(\mathbf{X}) = L\,\text{Cov}(\mathbf{Z})\,L^T = LIL^T = LL^T = \Sigma$

This is the standard technique for generating correlated random draws in Monte Carlo pricing of multi-asset derivatives (basket options, correlation-dependent structured products), converting independently-generated random numbers into a set with the desired covariance structure.

**Key Points**:

- Cholesky decomposition requires $\Sigma$ to be positive definite (not merely semi-definite); a near-singular or only positive-semi-definite estimated covariance matrix may require regularization (e.g., adding a small multiple of the identity matrix, or using a nearest-positive-definite matrix approximation) before Cholesky decomposition can be applied
- The **ordering of assets** in the Cholesky decomposition affects the decomposition itself (though not the resulting joint distribution of $\mathbf{X}$) — a practical detail relevant when interpreting intermediate simulation steps or implementing variance reduction techniques

### Diagram — Cholesky-Based Correlated Simulation (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 780 300">
<text x="390" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Cholesky Decomposition for Correlated Simulation (svg_diagram)</text>
<rect x="40" y="70" width="160" height="100" rx="6" fill="none" stroke="#1f6fd6" stroke-width="2" />
<text x="120" y="105" text-anchor="middle" font-size="13" fill="#1f6fd6">Independent</text>
<text x="120" y="125" text-anchor="middle" font-size="13" fill="#1f6fd6">Z ~ N(0, I)</text>
<text x="120" y="150" text-anchor="middle" font-size="11" fill="#555">(easy to simulate)</text>
<path d="M 210 120 L 280 120" stroke="#333" stroke-width="2" marker-end="url(#arrow1)" />
<text x="245" y="105" text-anchor="middle" font-size="12" fill="#333">X = L·Z</text>
<rect x="290" y="70" width="160" height="100" rx="6" fill="none" stroke="#666" stroke-width="2" />
<text x="370" y="105" text-anchor="middle" font-size="13" fill="#666">Cholesky Factor L</text>
<text x="370" y="125" text-anchor="middle" font-size="12" fill="#666">Sigma = L·L^T</text>
<text x="370" y="150" text-anchor="middle" font-size="11" fill="#555">(lower triangular)</text>
<path d="M 460 120 L 530 120" stroke="#333" stroke-width="2" marker-end="url(#arrow1)" />
<rect x="540" y="70" width="180" height="100" rx="6" fill="none" stroke="#d6291f" stroke-width="2" />
<text x="630" y="105" text-anchor="middle" font-size="13" fill="#d6291f">Correlated</text>
<text x="630" y="125" text-anchor="middle" font-size="13" fill="#d6291f">X ~ N(0, Sigma)</text>
<text x="630" y="150" text-anchor="middle" font-size="11" fill="#555">(used for asset paths)</text>
</svg>

### Principal Component Analysis (PCA)

PCA re-expresses a set of correlated variables in terms of orthogonal (uncorrelated) **principal components**, ordered by the amount of variance each explains. Computed via the eigendecomposition of the covariance (or correlation) matrix: the eigenvectors are the principal component directions, and the eigenvalues indicate the variance explained by each.

**Key application — yield curve modeling**: PCA applied to historical changes in interest rates across the maturity spectrum (e.g., 1-year, 2-year, ..., 30-year yields) typically identifies a small number of dominant factors that explain the large majority of yield curve movements:

1. **Level** (first principal component): a roughly parallel shift up or down across all maturities
2. **Slope** (second principal component): a steepening or flattening of the curve (short and long rates move in opposite directions)
3. **Curvature** (third principal component): a change in the curve's convexity/hump shape (belly moves relative to the wings)

**Key Points**:

- [Inference] It is a widely cited empirical finding in fixed-income literature that these first three principal components together tend to explain a large majority of historical yield curve variance in many markets and periods, which underlies common practices such as using level/slope/curvature factor hedges for interest rate risk management rather than hedging every individual maturity bucket separately; the precise percentage of variance explained is empirical, varies by market, time period, and dataset, and should not be treated as a fixed universal constant
- PCA is also applied to volatility surfaces (decomposing implied volatility movements across strikes and maturities into level/skew/term-structure-type factors) and to equity factor models, extending the same eigendecomposition logic beyond fixed income

### Matrix Formulation of Finite-Difference PDE Schemes

Implicit and Crank-Nicolson finite-difference schemes for solving the Black-Scholes PDE (covered in the differential equations section of this chapter) reduce, at each time step, to solving a linear system of the form:

$$M\mathbf{V}^{(t)} = \mathbf{V}^{(t+\Delta t)} + \mathbf{b}$$

where $\mathbf{V}^{(t)}$ is the vector of option values at each grid point at time $t$, $M$ is a **tridiagonal matrix** (since the discretized second-derivative term in the PDE only couples each grid point to its immediate neighbors), and $\mathbf{b}$ incorporates boundary conditions.

**Key Points**:

- The tridiagonal structure of $M$ is a direct consequence of the PDE's second-order spatial derivative term being approximated by a three-point central difference formula, connecting only adjacent grid points
- This tridiagonal structure is precisely what makes the **Thomas algorithm** the standard efficient solver for each time step of a finite-difference PDE scheme, since generic matrix inversion would be computationally wasteful given the matrix's sparse, banded structure
- For multi-dimensional PDEs (e.g., pricing options on two correlated underlyings, requiring a 2D grid), the matrix $M$ becomes block-tridiagonal or more complex banded structures, and specialized techniques (e.g., **Alternating Direction Implicit (ADI)** methods) are commonly used to reduce the multi-dimensional problem to a sequence of more tractable one-dimensional tridiagonal solves

### Factor Models and Dimensionality Reduction

A linear **factor model** expresses asset returns as a linear combination of a smaller number of common factors plus idiosyncratic noise:

$$\mathbf{r} = B\mathbf{f} + \boldsymbol{\epsilon}$$

where $\mathbf{f}$ is a vector of $k$ factor returns ($k \ll n$, the number of assets), $B$ is an $n \times k$ matrix of factor loadings (sensitivities), and $\boldsymbol{\epsilon}$ is idiosyncratic (asset-specific) noise assumed uncorrelated with $\mathbf{f}$ and, typically, across assets.

**Resulting covariance structure**:

$$\Sigma = B \Sigma_f B^T + \Sigma_\epsilon$$

where $\Sigma_f$ is the ($k \times k$, much smaller) factor covariance matrix and $\Sigma_\epsilon$ is a diagonal matrix of idiosyncratic variances.

**Key Points**:

- This decomposition is central to practical large-scale portfolio risk management: rather than directly estimating an $n \times n$ covariance matrix (which for a large universe of assets may be poorly conditioned or require more historical data than is available), a factor model reduces the estimation problem to a much smaller $k \times k$ factor covariance matrix plus $n$ idiosyncratic variances
- PCA (above) can itself be used as a data-driven method for constructing such factors (statistical factor models), as an alternative to fundamental factor models built from pre-specified economic or market factors (e.g., market beta, size, value, sector)

### Worked Example — Two-Asset Cholesky Decomposition

**Setup**: Two assets with volatilities $\sigma_1 = 0.20$, $\sigma_2 = 0.30$, and correlation $\rho = 0.5$. Covariance matrix:

$$\Sigma = \begin{pmatrix} 0.20^2 & 0.5 \times 0.20 \times 0.30 \\ 0.5 \times 0.20 \times 0.30 & 0.30^2 \end{pmatrix} = \begin{pmatrix} 0.04 & 0.03 \\ 0.03 & 0.09 \end{pmatrix}$$

**Cholesky factor** $L$, solving $\Sigma = LL^T$ with $L = \begin{pmatrix} l_{11} & 0 \\ l_{21} & l_{22} \end{pmatrix}$:

$$l_{11} = \sqrt{0.04} = 0.20$$



$$l_{21} = \frac{0.03}{l_{11}} = \frac{0.03}{0.20} = 0.15$$



$$l_{22} = \sqrt{0.09 - l_{21}^2} = \sqrt{0.09 - 0.0225} = \sqrt{0.0675} \approx 0.2598$$



$$L = \begin{pmatrix} 0.20 & 0 \\ 0.15 & 0.2598 \end{pmatrix}$$

**Generating correlated draws**: For independent $Z_1, Z_2 \sim \mathcal{N}(0,1)$, set $X_1 = 0.20 Z_1$ and $X_2 = 0.15 Z_1 + 0.2598 Z_2$. This produces $(X_1, X_2)$ with the exact target covariance structure, ready to drive two correlated GBM asset paths in a Monte Carlo simulation of a basket or spread option.

### Worked Example — Eigenvalue Check for a Valid Correlation Matrix

**Setup**: A proposed 3-asset correlation matrix:

$$R = \begin{pmatrix} 1 & 0.9 & 0.9 \\ 0.9 & 1 & -0.9 \\ 0.9 & -0.9 & 1 \end{pmatrix}$$

**Validity check**: A valid correlation matrix must be positive semi-definite (all eigenvalues $\geq 0$). Computing the eigenvalues of $R$ (via the characteristic polynomial $\det(R - \lambda I) = 0$) reveals whether this particular combination of pairwise correlations is internally consistent.

[Inference] For this specific matrix, the eigenvalues can be computed numerically; a quick sanity check computing the determinant, $\det(R) = 1(1 - 0.81) - 0.9(0.9 + 0.81) + 0.9(-0.81 - 0.9) \approx 0.19 - 1.539 - 1.539 = -2.888$, is negative, which for a $3\times 3$ symmetric matrix indicates at least one negative eigenvalue and therefore confirms this particular correlation matrix is **not** positive semi-definite and is invalid as stated — illustrating a common practical issue when pairwise correlations are estimated or specified independently (e.g., from different data sources or expert judgment) without jointly enforcing overall matrix consistency.

### Common Pitfalls

- **Treating an estimated correlation/covariance matrix as automatically valid**: Pairwise correlations estimated independently, or specified by combining multiple partial data sources, can produce a matrix that is not positive semi-definite, causing Cholesky decomposition to fail or Monte Carlo simulations to behave unpredictably — a positive-semi-definiteness check (or eigenvalue inspection) should precede downstream use.
- **Using explicit matrix inversion for large or structured linear systems**: Directly computing $A^{-1}$ is numerically less stable and computationally more expensive than specialized decomposition-based solvers (LU, Cholesky, Thomas algorithm for tridiagonal systems), particularly relevant for the large sparse systems arising in finite-difference PDE methods.
- **Overfitting factor models with too many factors**: Including more factors than the data can reliably support (relative to the number of historical observations) can lead to in-sample overfitting of a factor covariance model, degrading out-of-sample risk forecasting performance — this parallels general statistical overfitting concerns and is not unique to finance, but is a frequently encountered practical issue in factor-based risk models.
- **Ignoring the distinction between statistical and economic significance of principal components**: [Inference] A principal component that explains a mathematically non-trivial share of historical variance does not automatically correspond to an economically meaningful or stable factor going forward; practitioners commonly cross-check statistically-derived factors (e.g., from PCA) against economic intuition or known fundamental factors before relying on them for hedging or risk attribution, though practices vary across institutions and use cases.

**Next Steps**:

- Stochastic processes and multi-dimensional Brownian motion
- Monte Carlo methods for multi-asset derivatives pricing
- Portfolio optimization and the Markowitz mean-variance framework
- Multi-factor risk models in practice (fundamental vs. statistical factors)
- Finite difference methods for multi-dimensional PDEs (ADI methods)
- Yield curve construction and interest rate risk factor decomposition
- Copulas and non-linear dependence structures beyond correlation matrices
- Numerical linear algebra: LU, QR, and singular value decomposition (SVD)