## Matrix Algebra and Rank


### Matrix Fundamentals

A matrix $A \in \mathbb{R}^{m \times n}$ is a rectangular array of $m$ rows and $n$ columns. In econometrics, matrices organize data (design matrix $X$), transformations (projection matrices), and second-moment information (variance-covariance matrices).

**Key Points**

- $A_{ij}$ denotes the entry in row $i$, column $j$.
- A matrix is **square** if $m = n$, **symmetric** if $A = A^\top$, and **diagonal** if all off-diagonal entries are zero.
- The **transpose** $A^\top$ swaps rows and columns: $(A^\top)_{ij} = A_{ji}$. Properties: $(A^\top)^\top = A$, $(AB)^\top = B^\top A^\top$, $(A+B)^\top = A^\top + B^\top$.
- The **identity matrix** $I_n$ satisfies $I_n A = A I_n = A$ for conformable $A$.

### Matrix Operations

**Addition/Subtraction**: element-wise, requires identical dimensions.

$$(A + B)_{ij} = A_{ij} + B_{ij}$$

**Scalar multiplication**: $(cA)_{ij} = c \cdot A_{ij}$.

**Matrix multiplication**: for $A \in \mathbb{R}^{m \times k}$ and $B \in \mathbb{R}^{k \times n}$, the product $C = AB \in \mathbb{R}^{m \times n}$ has entries:

$$C_{ij} = \sum_{l=1}^{k} A_{il} B_{lj}$$

**Key Points**

- Matrix multiplication requires the inner dimensions to match ($k = k$) and is generally **not commutative**: $AB \neq BA$ in general, even when both products are defined.
- Matrix multiplication is associative, $(AB)C = A(BC)$, and distributive over addition, $A(B+C) = AB + AC$.
- The **trace** of a square matrix, $\text{tr}(A) = \sum_i A_{ii}$, satisfies the cyclic property $\text{tr}(ABC) = \text{tr}(BCA) = \text{tr}(CAB)$, frequently used to simplify expressions like $\text{tr}(X^\top X)$ or in deriving expectations of quadratic forms.

### Matrix Inverse

For a square matrix $A \in \mathbb{R}^{n \times n}$, the inverse $A^{-1}$ (if it exists) satisfies:

$$AA^{-1} = A^{-1}A = I_n$$

**Key Points**

- $A^{-1}$ exists if and only if $A$ is **nonsingular**, equivalently $\det(A) \neq 0$, equivalently $\text{rank}(A) = n$ (full rank).
- $(AB)^{-1} = B^{-1}A^{-1}$ (order reverses), and $(A^\top)^{-1} = (A^{-1})^\top$.
- For a $2\times 2$ matrix $A = \begin{pmatrix} a & b \\ c & d \end{pmatrix}$: $A^{-1} = \frac{1}{ad-bc}\begin{pmatrix} d & -b \\ -c & a \end{pmatrix}$, valid when $ad - bc \neq 0$.
- The **Sherman-Morrison-Woodbury formula** allows efficient updating of $(A + uv^\top)^{-1}$ without recomputing a full inverse — relevant for recursive least squares and leave-one-out diagnostics.
- In OLS, $\hat{\beta} = (X^\top X)^{-1} X^\top \mathbf{y}$ requires $X^\top X$ to be invertible, which holds if and only if $X$ has full column rank.

### Determinants

The determinant $\det(A)$ (or $|A|$) is a scalar summarizing key properties of a square matrix.

**Key Points**

- $\det(A) = 0$ if and only if $A$ is singular (rows/columns linearly dependent).
- $\det(AB) = \det(A)\det(B)$; $\det(A^\top) = \det(A)$; $\det(cA) = c^n \det(A)$ for $A \in \mathbb{R}^{n \times n}$.
- $\det(A^{-1}) = 1/\det(A)$.
- Geometrically, $|\det(A)|$ is the volume-scaling factor of the linear transformation represented by $A$; this connects to the Jacobian determinant used in change-of-variables for probability densities.
- For triangular matrices, $\det(A) = \prod_i A_{ii}$ (product of diagonal entries) — this is exploited computationally via LU decomposition rather than cofactor expansion, which is $O(n!)$.

### Rank of a Matrix

The **rank** of $A \in \mathbb{R}^{m \times n}$ is the dimension of its column space, equivalently the dimension of its row space (these are always equal), equivalently the maximum number of linearly independent columns (or rows).

$$\text{rank}(A) = \dim(\text{Col}(A)) = \dim(\text{Row}(A))$$

**Key Points**

- $\text{rank}(A) \leq \min(m, n)$.
- $A$ has **full row rank** if $\text{rank}(A) = m$; **full column rank** if $\text{rank}(A) = n$.
- Rank is computed practically via **Gaussian elimination**: reduce $A$ to row echelon form; the rank equals the number of nonzero (pivot) rows.
- $\text{rank}(AB) \leq \min(\text{rank}(A), \text{rank}(B))$.
- $\text{rank}(A) = \text{rank}(A^\top) = \text{rank}(A^\top A) = \text{rank}(AA^\top)$ — the middle equality is essential in econometrics since $\text{rank}(X^\top X) = \text{rank}(X)$, meaning $X^\top X$ is invertible exactly when $X$ has full column rank.
- **Rank-Nullity Theorem**: $\text{rank}(A) + \text{nullity}(A) = n$ (number of columns), where nullity is the dimension of the null space $\{\mathbf{v} : A\mathbf{v} = \mathbf{0}\}$.

### Worked Example: Rank via Row Reduction

$$A = \begin{pmatrix} 1 & 2 & 3 \\ 2 & 4 & 7 \\ 3 & 6 & 10 \end{pmatrix}$$

Row reduce: $R_2 \to R_2 - 2R_1$, $R_3 \to R_3 - 3R_1$:

$$\begin{pmatrix} 1 & 2 & 3 \\ 0 & 0 & 1 \\ 0 & 0 & 1 \end{pmatrix} \xrightarrow{R_3 \to R_3 - R_2} \begin{pmatrix} 1 & 2 & 3 \\ 0 & 0 & 1 \\ 0 & 0 & 0 \end{pmatrix}$$

Two nonzero pivot rows remain, so $\text{rank}(A) = 2 < 3$. Column 2 is redundant ($\text{col}_2 = 2 \times \text{col}_1$), confirming linear dependence.

**Output**

| Matrix property | Value |
| --- | --- |
| Dimensions | $3 \times 3$ |
| $\text{rank}(A)$ | 2 |
| $\det(A)$ | 0 (singular, since rank < 3) |
| $\text{nullity}(A)$ | 1 |

### Special Matrix Types in Econometrics

**Key Points**

- **Idempotent matrices**: $P^2 = P$. The OLS "hat matrix" $H = X(X^\top X)^{-1}X^\top$ (projects $\mathbf{y}$ onto $\text{Col}(X)$) and the residual maker $M = I - H$ are both idempotent and symmetric. Idempotent matrices have eigenvalues only 0 or 1, and $\text{rank}(P) = \text{tr}(P)$ for idempotent $P$ — this is why $\text{tr}(H) = p$ (number of regressors) and $\text{tr}(M) = n - p$ (residual degrees of freedom).
- **Positive definite matrices**: symmetric $A$ such that $\mathbf{x}^\top A \mathbf{x} > 0$ for all $\mathbf{x} \neq \mathbf{0}$. Variance-covariance matrices are positive semi-definite by construction; $X^\top X$ is positive definite if and only if $X$ has full column rank.
- **Orthogonal matrices**: $Q^\top Q = QQ^\top = I$, so $Q^{-1} = Q^\top$. Used in QR decomposition for numerically stable computation of $\hat{\beta}$.

### Eigenvalues, Eigenvectors, and Rank

For square $A$, $\mathbf{v} \neq \mathbf{0}$ is an eigenvector with eigenvalue $\lambda$ if:

$$A\mathbf{v} = \lambda \mathbf{v}$$

**Key Points**

- $\text{rank}(A)$ equals the number of nonzero eigenvalues (for diagonalizable $A$).
- $\det(A) = \prod_i \lambda_i$ (product of eigenvalues); $\text{tr}(A) = \sum_i \lambda_i$ (sum of eigenvalues).
- A symmetric matrix is diagonalizable via an orthogonal matrix: $A = Q\Lambda Q^\top$, the **spectral decomposition**, foundational to PCA and to understanding the geometry of quadratic forms in GLS/Mahalanobis-distance contexts.
- A matrix is singular if and only if it has at least one zero eigenvalue.

### Rank Deficiency and Its Econometric Consequences

**Key Points**

- **Perfect multicollinearity**: if $\text{rank}(X) < p$ (number of columns), $X^\top X$ is singular and $\hat{\beta}_{OLS}$ is not unique.
- **Rank condition for identification**: in instrumental variables (IV) and simultaneous equations models, the **rank condition** requires the relevant cross-moment matrix (e.g., between instruments and endogenous regressors) to have full rank for the model parameters to be identified — a necessary condition beyond the order condition (having enough instruments).
- **Generalized inverses**: when $X^\top X$ is singular, a **Moore-Penrose pseudoinverse** $(X^\top X)^+$ can still produce a (non-unique) minimum-norm solution, used in some regularized/high-dimensional estimation contexts.
- [Inference] Software implementations differ in how they handle rank deficiency — some (e.g., R's `lm()`) automatically drop redundant columns and report `NA` coefficients, while others may throw an error or return a pseudoinverse solution; the specific behavior is implementation-dependent and should be verified against the documentation of the tool in use.

### Diagram: Matrix Rank and OLS Identification Pathway

```mermaid
flowchart TD
    A[Design matrix X, n x p] --> B[Compute rank via row reduction / SVD]
    B --> C{rank(X) = p full column rank?}
    C -->|Yes| D[X^T X positive definite and invertible]
    D --> E[Unique OLS solution: beta-hat = inverse of X^T X times X^T y]
    C -->|No, rank = r less than p| F[X^T X singular, positive semi-definite only]
    F --> G[Infinitely many beta solutions satisfy normal equations]
    G --> H[Software drops columns, errors, or returns pseudoinverse solution]
```

### Diagram: Matrix Transformation and Rank as Dimension of Output (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 320">
<rect x="0" y="0" width="640" height="320" fill="#ffffff" />
<text x="320" y="26" font-size="16" font-family="sans-serif" font-weight="bold" text-anchor="middle" fill="#111827">Matrix Rank as Output Dimension (svg_diagram)</text>


<text x="150" y="55" font-size="13" font-family="sans-serif" font-weight="bold" text-anchor="middle" fill="`#111827`">Full rank: R^2 -&gt; R^2</text>

<rect x="60" y="80" width="120" height="120" fill="`#dbeafe`" stroke="`#2563eb`" stroke-width="1.5" />

<text x="120" y="215" font-size="11" font-family="sans-serif" text-anchor="middle" fill="`#374151`">domain (square)</text>

<line x1="200" y1="140" x2="250" y2="140" stroke="`#374151`" stroke-width="2" marker-end="url(#a1)" />

<text x="225" y="130" font-size="11" font-family="sans-serif" text-anchor="middle" fill="`#374151`">A</text>

<polygon points="270,90 380,110 370,190 280,195" fill="`#bbf7d0`" stroke="`#16a34a`" stroke-width="1.5" />

<text x="325" y="215" font-size="11" font-family="sans-serif" text-anchor="middle" fill="`#374151`">range (still 2D)</text>



<text x="500" y="55" font-size="13" font-family="sans-serif" font-weight="bold" text-anchor="middle" fill="`#111827`">Rank-deficient: R^2 -&gt; R^1</text>

<rect x="440" y="80" width="120" height="120" fill="`#fee2e2`" stroke="`#dc2626`" stroke-width="1.5" />

<text x="500" y="215" font-size="11" font-family="sans-serif" text-anchor="middle" fill="`#374151`">domain (square)</text>

<line x1="565" y1="140" x2="600" y2="140" stroke="`#374151`" stroke-width="2" marker-end="url(#a2)" />

<line x1="600" y1="90" x2="600" y2="190" stroke="`#b91c1c`" stroke-width="4" />

<text x="600" y="215" font-size="11" font-family="sans-serif" text-anchor="middle" fill="`#374151`">range collapses to a line</text>

<text x="320" y="255" font-size="12" font-family="sans-serif" text-anchor="middle" fill="`#4b5563`">Left: full-rank A preserves dimension -&gt; invertible, unique solutions</text>

<text x="320" y="275" font-size="12" font-family="sans-serif" text-anchor="middle" fill="`#4b5563`">Right: rank-deficient A collapses a dimension -&gt; singular, information lost, non-unique solutions</text>

</svg>

### Computational Considerations

**Key Points**

- Direct computation via cofactor expansion is impractical for $n > 4$; standard numerical libraries (LAPACK-backed, e.g., NumPy's `linalg`, R's base linear algebra) use **LU decomposition** for determinants/inverses and **QR** or **SVD** for rank and least-squares problems.
- **Singular Value Decomposition (SVD)**: $A = U\Sigma V^\top$, where $\Sigma$ contains singular values in decreasing order. The rank of $A$ equals the number of nonzero singular values, and SVD is the numerically preferred method for rank determination since it is robust to floating-point rounding (rank is typically declared by counting singular values above a small tolerance threshold).
- [Inference] Because floating-point arithmetic introduces rounding error, "exact" rank deficiency in real data is rarely detected as literally zero; practical rank determination relies on a tolerance cutoff, and results can be sensitive to that choice near-boundary cases (severe multicollinearity).

### Related Topics

- Vector spaces and linear independence (foundational prerequisite)
- Eigenvalues, eigenvectors, and spectral/singular value decomposition
- Idempotent and projection matrices in OLS geometry
- Generalized (Moore-Penrose) inverses and minimum-norm solutions
- Rank condition for identification in IV/GMM estimation
- Positive definiteness and quadratic forms in variance-covariance structures