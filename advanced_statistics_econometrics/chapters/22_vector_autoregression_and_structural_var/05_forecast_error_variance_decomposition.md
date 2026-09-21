## Forecast Error Variance Decomposition

### Definition and Conceptual Foundation

Forecast error variance decomposition (FEVD) quantifies the proportion of the forecast error variance of each variable in a VAR system that is attributable to structural shocks in each variable (including itself) at a given forecast horizon. While impulse response functions trace the *dynamic path* of a variable's response to a shock, FEVD answers a complementary question: at horizon $h$, what *share* of the uncertainty in forecasting variable $k$ comes from shock $j$?

FEVD is used to assess the relative importance of different shocks in driving fluctuations in each variable, and is a standard companion output to IRFs when interpreting a VAR or SVAR.

### Derivation from the Moving Average Representation

Starting from the orthogonalized VMA representation:

$$Y_t = \mu + \sum_{i=0}^{\infty} \Theta_i u_{t-i}$$

where $u_t$ are orthogonalized (structural) shocks with $\text{Var}(u_t) = I_n$, and $\Theta_i = \Phi_i P$ from the Cholesky factorization (or $\Theta_i = \Phi_i B_0^{-1}$ under SVAR identification).

The $h$-step-ahead forecast error is:

$$Y_{t+h} - E_t[Y_{t+h}] = \sum_{i=0}^{h-1} \Theta_i u_{t+h-i}$$

The forecast error variance of the $k$-th variable at horizon $h$ is:

$$\text{Var}(Y_{k,t+h} - E_t[Y_{k,t+h}]) = \sum_{i=0}^{h-1} \sum_{j=1}^{n} (\theta_{kj,i})^2$$

where $\theta_{kj,i}$ is the $(k,j)$ element of $\Theta_i$, representing the response of variable $k$ to structural shock $j$ at lag $i$. Because the structural shocks are orthogonal (uncorrelated, unit variance), the total forecast error variance splits additively across shock sources.

### The Decomposition Formula

The proportion of the $h$-step-ahead forecast error variance of variable $k$ attributable to shock $j$ is:

$$\omega_{kj}(h) = \frac{\sum_{i=0}^{h-1} (\theta_{kj,i})^2}{\sum_{i=0}^{h-1} \sum_{m=1}^{n} (\theta_{km,i})^2}$$

**Key Points**

- For each variable $k$ and horizon $h$, the shares across all shocks $j = 1, \dots, n$ sum to 1: $\sum_{j=1}^{n} \omega_{kj}(h) = 1$.
- Orthogonality of structural shocks is essential for this additive decomposition to be valid; it is precisely why identification (Cholesky or SVAR) must precede FEVD computation, exactly as with IRFs.
- FEVD is **ordering-dependent** under Cholesky identification, for the same reason IRFs are: the triangular structure of $P$ affects how contemporaneous covariance is attributed to each shock.
- At horizon $h=1$ (or $h=0$ depending on indexing convention), a variable's forecast error variance is often dominated by its own shock, since other variables have not yet had time to transmit their effects through the dynamic system (particularly in a recursive Cholesky ordering where the first-ordered variable's own shock explains 100% of its own one-step-ahead variance).
- As $h \to \infty$, the shares converge to the shock contributions implied by the long-run VMA structure, revealing which shocks are the dominant long-run drivers of each variable's variability.

### Practical Computation Steps

**Example**

Step 1: Estimate the reduced-form VAR($p$), obtain $\hat{\Sigma}$, and compute the VMA coefficients $\hat{\Phi}_0, \dots, \hat{\Phi}_{H-1}$ up to the maximum horizon of interest.

Step 2: Identify structural shocks via Cholesky ($\hat{\Sigma} = \hat{P}\hat{P}'$) or an SVAR scheme, obtaining $\hat{\Theta}_i = \hat{\Phi}_i \hat{P}$.

Step 3: For each variable $k$ and each horizon $h = 1, \dots, H$, compute the cumulative squared responses $\sum_{i=0}^{h-1}(\hat{\theta}_{kj,i})^2$ for every shock $j$.

Step 4: Normalize by the total forecast error variance at that horizon to obtain $\hat{\omega}_{kj}(h)$.

Step 5: Tabulate or plot the shares (commonly as stacked bar charts) across horizons.

**Output**

Suppose a three-variable macro VAR with output growth, inflation, and the policy interest rate (Cholesky-ordered in that sequence). A representative FEVD table for inflation might show:

| Horizon | Output shock | Inflation shock | Interest rate shock |
| --- | --- | --- | --- |
| 1 | 8% | 92% | 0% |
| 4 | 15% | 78% | 7% |
| 12 | 22% | 60% | 18% |
| 24 | 25% | 55% | 20% |

This pattern (own-shock dominance shrinking as horizon lengthens, with output and interest rate shocks gaining explanatory share) is a common qualitative finding in macro VAR studies, though the exact magnitudes are entirely model- and dataset-specific. [Inference: the numbers above are illustrative only and not drawn from a specific estimated model.]

### Relationship to Impulse Response Functions

FEVD and IRFs are two views of the same underlying $\Theta_i$ matrices: IRFs show the *sign and magnitude path* of responses over time, while FEVD shows the *relative importance* (as a variance share) of each shock, aggregated across horizons up to $h$. A shock can have a visually large IRF response yet explain a small FEVD share if its own innovation variance is small, or if other shocks also strongly affect the same variable — the two tools should be interpreted jointly rather than in isolation.

### Common Pitfalls

- **Treating FEVD shares as causal effect sizes**: A high share attributed to a shock reflects historical *variance contribution under the identifying assumptions*, not necessarily the true structural importance of that channel if identification is misspecified.
- **Ignoring ordering sensitivity**: As with IRFs, presenting FEVD from a single Cholesky ordering without justification or robustness checks (alternative orderings, or a theory-based SVAR) risks misleading conclusions, since reordering can substantially shift shares, especially at short horizons.
- **Over-reading short-horizon results**: Very short-horizon FEVDs mechanically favor the first-ordered variable(s) under Cholesky identification; this can reflect the identification scheme's structure rather than genuine economic dynamics.
- **Non-stationarity**: As with IRFs, applying FEVD to a levels VAR with unit-root, non-cointegrated variables can produce forecast error variances that do not stabilize as expected, complicating interpretation.
- **Confidence intervals often omitted**: FEVD point estimates are frequently reported without uncertainty bands in applied work, even though they are subject to the same estimation uncertainty as IRFs; bootstrap or Bayesian credible intervals are recommended for rigorous reporting.

### FEVD Computation Flow Diagram

```mermaid
flowchart TD
    subgraph fevd_pipeline FEVD Construction Pipeline (svg_diagram)
    A["Reduced-form VAR(p): estimate A1...Ap, Sigma"] --> B["Compute VMA coefficients Phi_0...Phi_H-1"]
    B --> C["Identify structural shocks: Theta_i = Phi_i times P or B0 inverse"]
    C --> D["For each variable k and horizon h: sum squared theta_kj,i across i=0 to h-1, for each shock j"]
    D --> E["Total forecast error variance = sum across all shocks j"]
    E --> F["omega_kj(h) = shock j contribution / total variance"]
    F --> G["Shares sum to 1 across j, for each k and h"]
    G --> H["Report as table or stacked bar chart across horizons"]
    end
```

### Software Implementation Notes

- **R**: `vars::fevd()` (companion function to `irf()` in the same package).
- **Python**: `statsmodels.tsa.vector_ar.var_model.VARResults.fevd()`.
- **EViews/Stata**: `irf table`/`irf graph` with FEVD option (Stata), variance decomposition view in EViews VAR objects.

[Unverified: exact default horizon settings, indexing conventions (h starting at 0 vs. 1), and confidence interval availability vary by package version; verify against current documentation before use.]

**Related Topics**

- Impulse response functions
- Structural VAR identification (Cholesky, sign restrictions, long-run restrictions)
- Granger causality testing
- Historical decomposition in VAR models
- Bayesian VAR estimation and posterior FEVD credible intervals
- VAR lag order selection criteria