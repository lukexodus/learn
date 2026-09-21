## Impulse Response Functions

### Definition and Conceptual Foundation

An impulse response function (IRF) traces the dynamic effect of a one-time shock to one variable in a VAR system on the current and future values of all variables in the system, holding all other shocks at zero. IRFs answer the question: if variable $j$ experiences an unexpected shock of one unit (or one standard deviation) at time $t$, how does variable $k$ respond at horizons $t, t+1, t+2, \dots, t+h$?

IRFs are the primary tool for interpreting the dynamic, multivariate structure of a VAR, since the raw estimated coefficients of a VAR are difficult to interpret directly due to feedback across equations and lags.

### Moving Average Representation

A stationary VAR($p$),

$$Y_t = c + A_1 Y_{t-1} + A_2 Y_{t-2} + \cdots + A_p Y_{t-p} + \varepsilon_t$$

can be inverted into an infinite-order vector moving average, VMA($\infty$), representation (Wold representation):

$$Y_t = \mu + \sum_{i=0}^{\infty} \Phi_i \varepsilon_{t-i}$$

where $\Phi_0 = I_n$ (the identity matrix) and the $\Phi_i$ matrices are computed recursively from the autoregressive coefficients:

$$\Phi_i = \sum_{j=1}^{i} \Phi_{i-j} A_j, \quad i = 1, 2, \dots$$

with $A_j = 0$ for $j > p$. The elements of $\Phi_i$ represent the **non-orthogonalized** (reduced-form) impulse responses: the $(k,j)$ element of $\Phi_i$ gives the response of variable $k$ at horizon $i$ to a one-unit shock in the reduced-form residual $\varepsilon_{jt}$, assuming all other reduced-form shocks are zero.

### The Identification Problem

Reduced-form residuals $\varepsilon_t$ are generally correlated across equations (their variance-covariance matrix $\Sigma$ is non-diagonal), because contemporaneous relationships among the variables are absorbed into the residual covariance rather than modeled explicitly. This means shocking $\varepsilon_{jt}$ alone while holding other residuals at zero is not a economically meaningful experiment, since in reality the shocks move together. Producing structurally interpretable IRFs therefore requires transforming the reduced-form shocks into **orthogonal** structural shocks $u_t$, where $\text{Var}(u_t) = I$ or a diagonal matrix.

### Orthogonalized (Cholesky) Impulse Responses

The most common identification method is a Cholesky decomposition of $\Sigma$:

$$\Sigma = P P'$$

where $P$ is lower triangular. Structural shocks are recovered as $u_t = P^{-1}\varepsilon_t$, and the orthogonalized IRFs are:

$$\Theta_i = \Phi_i P$$

**Key Points**

- The Cholesky decomposition imposes a **recursive (triangular) causal ordering**: the first variable in the ordering can affect all others contemporaneously, but is affected by others only with a lag; the last variable in the ordering can be contemporaneously affected by all others but affects them only with a lag.
- Results are **ordering-dependent**: different orderings of variables generally produce different IRFs, sometimes substantially. Ordering should be justified by economic theory (e.g., slow-moving variables like output ordered before fast-moving financial variables), and robustness checks across alternative plausible orderings are standard practice.
- This is a key limitation of the basic (non-structural) VAR approach and is the primary motivation for moving to a **Structural VAR (SVAR)**, where the contemporaneous relationships in matrix $B_0$ (from $B_0 Y_t = \dots$) are identified using economic theory, short-run zero restrictions, long-run restrictions (Blanchard-Quah), or sign restrictions, rather than an arbitrary triangular ordering.

### Types of Impulse Responses

**Non-orthogonalized (reduced-form) IRF**: Direct response using $\Phi_i$, without addressing contemporaneous correlation. Rarely used for interpretation alone since it implicitly assumes other shocks stay at exactly zero even though they are correlated with the shocked variable.

**Orthogonalized (Cholesky) IRF**: As above; standard default output in most VAR software, ordering-dependent.

**Structural IRF**: $\Theta_i = \Phi_i B_0^{-1}$ where $B_0^{-1}$ is derived from theoretically motivated identification restrictions rather than a Cholesky factorization. Considered the methodologically preferred approach when credible restrictions are available.

**Generalized Impulse Response Function (GIRF)**, due to Pesaran and Shin (1998): Avoids the ordering problem entirely by accounting for the historically observed correlation between shocks without orthogonalizing them:

$$\theta_{k,j}^{G}(i) = \sigma_{jj}^{-1/2} \, e_k' \Phi_i \Sigma e_j$$

GIRFs are invariant to variable ordering, which makes them attractive for purely descriptive/forecasting purposes, though they lack a clean structural shock interpretation since the "shock" is not orthogonal to other shocks.

### Practical Computation Steps

**Example**

Step 1: Estimate the reduced-form VAR($p$) and obtain $\hat{A}_1, \dots, \hat{A}_p$ and $\hat{\Sigma}$.

Step 2: Compute the VMA coefficient matrices $\hat{\Phi}_0, \hat{\Phi}_1, \dots, \hat{\Phi}_H$ recursively up to the desired horizon $H$ (e.g., $H = 20$ quarters).

Step 3: Choose an identification scheme:

- Cholesky: order variables (e.g., output → prices → interest rate, a common macro ordering placing slow-moving real variables first) and compute $\hat{P}$ from $\hat{\Sigma} = \hat{P}\hat{P}'$.
- SVAR: impose restrictions on $B_0$ and solve for $\hat{B}_0^{-1}$.

Step 4: Compute $\hat{\Theta}_i = \hat{\Phi}_i \hat{P}$ (or $\hat{\Phi}_i \hat{B}_0^{-1}$) for $i = 0, \dots, H$.

Step 5: Plot each $(k,j)$ element of $\hat{\Theta}_i$ against horizon $i$, typically with confidence bands.

**Output**

A typical IRF plot shows, for example, the response of inflation to a one-standard-deviation interest rate shock: inflation may show little immediate response (0 at $i=0$ if interest rate is ordered after inflation), decline gradually over 4–8 quarters, and converge back toward zero as the effect dissipates — consistent with a monetary tightening's delayed and transitory effect on prices. [Inference: exact dynamics are model- and dataset-specific; this describes a stylized qualitative pattern commonly found in macro VAR studies, not a universal result.]

### Confidence Intervals

Because IRFs are nonlinear functions of estimated VAR coefficients, analytical standard errors are complex. Common approaches:

- **Asymptotic (delta method)**: Uses the asymptotic covariance matrix of VAR coefficients propagated through the nonlinear IRF mapping; can perform poorly in small samples.
- **Bootstrap (standard/recursive)**: Resample residuals, generate pseudo-data recursively from the estimated VAR, re-estimate, and recompute IRFs repeatedly (e.g., 1,000–2,000 replications) to build an empirical distribution.
- **Bias-corrected bootstrap**: Adjusts for the known small-sample downward bias in estimated AR coefficients before resampling.
- **Bayesian VAR (BVAR) credible intervals**: Posterior draws of coefficients directly yield a distribution of IRFs without needing bootstrap resampling.

### Common Pitfalls

- **Over-interpreting ordering-sensitive results**: Presenting only one Cholesky ordering without robustness checks or theoretical justification.
- **Confusing statistical significance with economic significance**: A "significant" IRF (confidence band excluding zero) may still represent a substantively negligible magnitude.
- **Ignoring non-stationarity**: If variables are I(1) and not cointegrated, IRFs from a levels VAR may not converge to zero and can be misleading; a VAR in differences or a VECM with implied levels IRFs is typically more appropriate.
- **Horizon selection**: Choosing $H$ too short can miss slow-adjustment dynamics; too long amplifies estimation uncertainty and stacks up compounding parameter uncertainty in the bootstrap.

### Impulse Response Mechanism Diagram

```mermaid
flowchart TD
    subgraph irf_construction_pipeline IRF Construction Pipeline (svg_diagram)
    A["Reduced-form VAR(p) estimated: A1...Ap, Sigma"] --> B["Invert to VMA(infinity): Phi_0, Phi_1, ... Phi_H"]
    B --> C{"Identification scheme"}
    C -->|"Cholesky ordering"| D["P from Sigma = P P'"]
    C -->|"SVAR restrictions"| E["B0 inverse from theory-based restrictions"]
    C -->|"Generalized IRF"| F["No orthogonalization, uses Sigma directly"]
    D --> G["Theta_i = Phi_i times P"]
    E --> H["Theta_i = Phi_i times B0 inverse"]
    F --> I["GIRF formula with sigma_jj^-1/2"]
    G --> J["Plot response over horizon i = 0...H"]
    H --> J
    I --> J
    J --> K["Add confidence bands: bootstrap or Bayesian"]
    end
```

### Software Implementation Notes

- **R**: `vars::irf()` (Cholesky and bootstrap CIs built in), `svars` package for SVAR-based IRFs.
- **Python**: `statsmodels.tsa.vector_ar.var_model.VARResults.irf()`.
- **EViews/Stata**: Built-in `irf create`/`irf graph` (Stata), impulse response views in EViews VAR objects.

[Unverified: exact default settings for bootstrap replications, confidence levels, and ordering conventions vary by package version; verify against current documentation before use.]

**Related Topics**

- Structural VAR identification (short-run, long-run, and sign restrictions)
- Forecast error variance decomposition
- Granger causality testing
- Cholesky decomposition and ordering sensitivity
- Local projections (Jordà method) as an alternative to VAR-based IRFs
- Bayesian VAR estimation and prior specification
- Blanchard-Quah long-run restriction identification