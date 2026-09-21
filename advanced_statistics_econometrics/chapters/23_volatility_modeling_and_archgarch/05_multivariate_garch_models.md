## Multivariate GARCH Models


### Conceptual Foundation

Multivariate GARCH (MGARCH) models extend the univariate conditional variance framework to model the entire time-varying conditional covariance matrix $H_t$ of a vector of returns simultaneously, capturing not only individual asset volatility dynamics but also time-varying **co-movement** (covariance and correlation) between assets. This is essential for applications where the joint distribution of multiple assets matters directly: portfolio variance and Value-at-Risk, dynamic hedge ratios, optimal portfolio weights, and financial contagion/spillover analysis all require a model of the full conditional covariance structure, not just marginal variances.

### The General MGARCH Framework

For an $n$-dimensional return vector $r_t$:

$$r_t = \mu_t + \varepsilon_t, \quad \varepsilon_t = H_t^{1/2} z_t, \quad z_t \overset{\text{i.i.d.}}{\sim} (0, I_n)$$

where $H_t$ is the $n \times n$ conditional covariance matrix, and $H_t^{1/2}$ is any matrix square root (e.g., Cholesky factor) such that $H_t^{1/2}(H_t^{1/2})' = H_t$. The central modeling challenge is specifying how $H_t$ evolves over time while satisfying two critical requirements:

**Key Points**

- **Positive semi-definiteness**: $H_t$ must be positive semi-definite (ideally positive definite) at every point in time, since it represents a covariance matrix — a much more demanding constraint than the simple non-negativity scalar constraint in univariate GARCH.
- **Parameter parsimony (the "curse of dimensionality")**: A fully unrestricted $H_t$ has $n(n+1)/2$ distinct time-varying elements; naive extensions of univariate GARCH to allow every element to depend flexibly on every other element's history produce a number of parameters growing at rate $O(n^4)$, quickly becoming computationally infeasible even for moderate $n$ (e.g., 10–20 assets). Much of the MGARCH literature is fundamentally about finding structures that balance flexibility against this dimensionality problem.

### VEC and Diagonal VEC Models

The original Bollerslev, Engle, and Wooldridge (1988) VEC model vectorizes the covariance matrix and models each element as a linear function of past squared/cross-products of shocks and past covariance elements — the most general (and least parsimonious) specification, with $O(n^4)$ parameters, rarely used in practice beyond small systems ($n=2,3$) due to computational and estimation burden.

**Diagonal VEC (DVEC)** restricts each element $h_{ij,t}$ to depend only on its own past value and the corresponding cross-product $\varepsilon_{i,t-1}\varepsilon_{j,t-1}$, reducing parameters substantially but still requiring separate positive-definiteness checks that are not automatically guaranteed by the model structure.

### BEKK Model (Baba, Engle, Kraft, Kroner, 1995)

$$H_t = C'C + A'\varepsilon_{t-1}\varepsilon_{t-1}'A + B'H_{t-1}B$$

where $C$ is upper triangular (ensuring $C'C$ is positive semi-definite), and $A$, $B$ are $n \times n$ parameter matrices.

**Key Points**

- The quadratic-form construction **guarantees** $H_t$ is positive semi-definite by construction for any parameter values (given $C$ upper triangular), without requiring additional constraints during estimation — a major advantage over VEC-type models.
- The full (unrestricted) BEKK still has $O(n^2)$ parameters even in its most parsimonious "scalar BEKK" variant (where $A$ and $B$ are scalar multiples of the identity matrix, $A = aI_n$, $B = bI_n$), and grows to $O(n^4)$ for the fully general matrix version, so BEKK remains primarily practical for small systems (a handful of assets) in its general form; scalar and diagonal BEKK restrictions are used to extend feasibility to somewhat larger systems.
- Estimation is by maximum likelihood, typically assuming multivariate Gaussian or multivariate Student's-t conditional errors, and is computationally demanding relative to univariate GARCH due to the matrix-valued likelihood and positive-definiteness-preserving structure.

### CCC — Constant Conditional Correlation (Bollerslev, 1990)

$$H_t = D_t R D_t, \quad D_t = \text{diag}(\sigma_{1,t}, \dots, \sigma_{n,t})$$

where each $\sigma_{i,t}^2$ follows its own univariate GARCH process, and $R$ is a **time-invariant** correlation matrix.

**Key Points**

- CCC dramatically simplifies estimation: univariate GARCH models can be fit separately for each series, and the correlation matrix $R$ is estimated once from standardized residuals, avoiding the joint high-dimensional optimization required by VEC/BEKK.
- The core limitation — and the primary motivation for DCC below — is the assumption of **constant** correlation over time, which is frequently rejected empirically, since correlations between assets (particularly across asset classes, or during crisis periods) are well-documented to vary substantially over time, often rising sharply during market stress ("correlation breakdown" or "contagion" phenomena).

### DCC — Dynamic Conditional Correlation (Engle, 2002)

$$H_t = D_t R_t D_t, \quad D_t = \text{diag}(\sigma_{1,t}, \dots, \sigma_{n,t})$$

where $R_t$ is now **time-varying**, typically modeled as:

$$Q_t = (1-a-b)\bar{Q} + a\, u_{t-1}u_{t-1}' + b\, Q_{t-1}, \quad R_t = \text{diag}(Q_t)^{-1/2} Q_t \, \text{diag}(Q_t)^{-1/2}$$

where $u_t = \varepsilon_t / \sigma_t$ (standardized residuals from the first-stage univariate GARCH fits), $\bar{Q}$ is the unconditional covariance matrix of $u_t$, and $a, b \geq 0$ with $a+b<1$ govern the dynamics of the (unnormalized) pseudo-correlation matrix $Q_t$, which is then rescaled to a proper correlation matrix $R_t$.

**Key Points**

- DCC's two-step estimation procedure — (1) fit univariate GARCH models separately for each series to obtain $D_t$ and standardized residuals $u_t$, then (2) estimate the (typically low-dimensional, often just $a$ and $b$) correlation-dynamics parameters — is dramatically more scalable than BEKK or full VEC, making DCC by far the most widely used MGARCH approach in applied work for moderate-to-large systems.
- The normalization step $R_t = \text{diag}(Q_t)^{-1/2}Q_t\,\text{diag}(Q_t)^{-1/2}$ ensures $R_t$ has unit diagonal elements (valid correlation matrix) even though $Q_t$ itself does not directly.
- The scalar DCC specification (a single $a$ and $b$ applied across all pairs) is the standard simplification; asymmetric DCC (ADCC) extensions allow correlations to respond differently to joint negative shocks, paralleling the leverage-effect logic from univariate asymmetric GARCH.

### Comparative Summary Table

| Model | Positive-definiteness | Parameter count | Estimation approach | Correlation dynamics |
| --- | --- | --- | --- | --- |
| VEC (full) | Not guaranteed | $O(n^4)$ | Joint MLE, infeasible beyond small $n$ | Fully flexible, unrestricted |
| Diagonal VEC | Not guaranteed | $O(n^2)$ | Joint MLE | Element-specific own dynamics |
| BEKK (full) | Guaranteed by construction | $O(n^4)$ | Joint MLE, feasible for small $n$ | Implicit via matrix structure |
| Scalar/Diagonal BEKK | Guaranteed | $O(n^2)$ or fewer | Joint MLE | Restricted common dynamics |
| CCC | Guaranteed (via $D_t$, fixed $R$) | $O(n)$ + few | Two-step (univariate + fixed R) | None (constant) |
| DCC | Guaranteed (via normalization) | $O(n)$ + few (often just 2) | Two-step (univariate + low-dim correlation dynamics) | Dynamic, highly scalable |

### Practical Estimation Workflow (DCC)

**Example**

Step 1: For each of the $n$ return series, fit a univariate GARCH(1,1) (or asymmetric GJR/EGARCH if warranted) model separately, obtaining fitted conditional volatilities $\hat{\sigma}_{i,t}$ and standardized residuals $\hat{u}_{i,t} = \hat{\varepsilon}_{i,t}/\hat{\sigma}_{i,t}$.

Step 2: Form the matrix of standardized residuals $\hat{u}_t = (\hat{u}_{1,t}, \dots, \hat{u}_{n,t})'$ and estimate the unconditional correlation $\bar{Q}$ as the sample covariance of $\hat{u}_t$.

Step 3: Estimate the DCC parameters $(a, b)$ via maximum likelihood on the correlation component of the likelihood, holding the first-stage univariate parameters fixed (quasi-maximum-likelihood, two-step approach).

Step 4: Recover the fitted dynamic correlation matrix $\hat{R}_t$ at each $t$, and construct the full conditional covariance $\hat{H}_t = \hat{D}_t \hat{R}_t \hat{D}_t$.

Step 5: Use $\hat{H}_t$ for downstream applications: dynamic portfolio variance $w_t'\hat{H}_t w_t$ for portfolio weights $w_t$, minimum-variance hedge ratios $\hat{h}_{12,t}/\hat{h}_{22,t}$, or time-varying Value-at-Risk for a multi-asset portfolio.

**Output**

A typical DCC fit across a small equity-bond portfolio might yield $\hat{a} \approx 0.02$–$0.05$ and $\hat{b} \approx 0.90$–$0.97$ (both significant, with $\hat{a}+\hat{b} < 1$ for stationarity of the correlation process), and the resulting time-varying correlation series commonly shows equity-bond correlation shifting — for example, becoming more negative during equity market stress episodes (a "flight to quality" pattern) relative to calmer periods. [Inference: the specific sign and magnitude of correlation regime shifts are asset-pair- and period-specific; the pattern described is a commonly documented qualitative finding in the empirical literature, not a universal result.]

### Applications

**Key Points**

- **Dynamic hedge ratios**: The minimum-variance hedge ratio between a spot position and a futures/hedging instrument, $h_t^* = H_{12,t}/H_{22,t}$, updates period-by-period as the conditional covariance structure evolves, rather than assuming a static hedge ratio.
- **Time-varying portfolio optimization**: Mean-variance or minimum-variance portfolio weights computed using $\hat{H}_t$ rather than a static historical covariance matrix, allowing the portfolio to adapt to changing risk and co-movement conditions.
- **Systemic risk and contagion measurement**: Spikes in DCC-estimated correlations across financial institutions or markets during crisis periods are commonly used as an empirical signature of contagion or systemic stress.
- **Multi-asset Value-at-Risk and Expected Shortfall**: Portfolio-level tail risk measures require the full joint conditional covariance (or higher-moment) structure, which MGARCH directly supplies.

### Common Pitfalls

- **Applying full BEKK or VEC to large systems**: Parameter counts become infeasible beyond a handful of assets; DCC or CCC (or restricted BEKK variants) are the practical choice for larger portfolios.
- **Ignoring the two-step DCC estimator's known inefficiency**: The standard two-step DCC procedure is consistent but not fully efficient relative to a hypothetical one-step joint MLE; in practice, this efficiency loss is generally accepted as a reasonable trade-off for tractability, but should be acknowledged. [Inference: the practical materiality of this efficiency loss depends on sample size and application; it is not typically treated as disqualifying in applied work.]
- **Assuming constant correlation (CCC) when it is empirically time-varying**: Particularly relevant for cross-asset-class portfolios (equities and bonds, or equities and commodities) where correlation regime shifts are well documented; a CCC model would fail to capture this, understating risk during correlation-breakdown episodes.
- **Overlooking non-Gaussian, fat-tailed multivariate distributions**: As in the univariate case, assuming multivariate normal $z_t$ often understates joint tail risk; multivariate Student's-t or copula-based approaches are commonly preferred for portfolio tail-risk applications.
- **Curse of dimensionality in correlation targeting**: Even DCC's "unconditional correlation targeting" step (setting $\bar{Q}$ to the sample correlation) can become imprecise as $n$ grows large relative to the sample size, motivating shrinkage or factor-structure-based approaches in very high-dimensional applications.

### MGARCH Model Family Diagram

```mermaid
flowchart TD
    subgraph mgarch_family MGARCH Model Family and Trade-offs (svg_diagram)
    A["N-dimensional return vector r_t"] --> B{"Positive-definiteness and parsimony trade-off"}
    B -->|"Fully flexible, high parameter count"| C["VEC / Diagonal VEC: O(n^4) or O(n^2) params"]
    B -->|"Guaranteed PSD by quadratic construction"| D["BEKK: full or scalar/diagonal restricted"]
    B -->|"Decompose into volatilities times correlation"| E["D_t R D_t decomposition"]
    E -->|"Constant R"| F["CCC: fixed correlation matrix"]
    E -->|"Time-varying R_t"| G["DCC: two-step, scalable dynamic correlation"]
    G --> H["Step 1: univariate GARCH per series"]
    G --> I["Step 2: low-dimensional correlation dynamics a, b"]
    H --> J["Full conditional covariance H_t = D_t R_t D_t"]
    I --> J
    J --> K["Applications: hedge ratios, portfolio VaR, contagion measures"]
    end
```

### Software Implementation Notes

- **R**: `rmgarch` package (`dccspec()`, `dccfit()` for DCC; `bekk()` in other packages such as `MTS` or specialized BEKK implementations).
- **Python**: MGARCH support is less standardized than univariate GARCH; the `arch` package focuses primarily on univariate models, with DCC/BEKK typically requiring third-party or custom implementations (e.g., `mgarch` community packages) — check current package ecosystem status before relying on a specific library.
- **MATLAB**: The Econometrics Toolbox provides native support for several MGARCH specifications including CCC and DCC.
- **EViews/Stata**: Stata's `mgarch` command supports DCC, CCC, VCC, and BEKK specifications directly; EViews supports system GARCH estimation with correlation modeling options.

[Unverified: exact function names, default optimizer settings, and the current state of Python MGARCH package support may have changed since training; verify against current documentation before implementation.]

**Related Topics**

- The GARCH model and extensions
- Asymmetric volatility models
- Dynamic hedge ratio estimation
- Portfolio Value-at-Risk and Expected Shortfall
- Copula-based dependence modeling
- Financial contagion and systemic risk measurement
- Realized covariance and high-frequency multivariate volatility estimators