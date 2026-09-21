## Structural VAR Identification Schemes


### Conceptual Foundation

A reduced-form VAR captures statistical relationships among variables but cannot, on its own, recover the underlying structural (economically meaningful) shocks, because the reduced-form residuals $\varepsilon_t$ are linear combinations of structural shocks $u_t$. Structural VAR (SVAR) identification is the set of methods used to impose additional restrictions — grounded in economic theory — that allow recovery of the structural shocks and the contemporaneous relationships among variables from the estimated reduced-form parameters. Without identification, IRFs and FEVDs are arbitrary artifacts of an implicit (and often unjustified) Cholesky ordering.

### The Structural Form and the Identification Problem

The structural VAR is written as:

$$B_0 Y_t = c^* + B_1 Y_{t-1} + \cdots + B_p Y_{t-p} + u_t, \quad \text{Var}(u_t) = D \text{ (diagonal)}$$

where $B_0$ captures contemporaneous relationships among variables, and $u_t$ are mutually uncorrelated structural shocks with economic interpretations (e.g., a monetary policy shock, a supply shock). The reduced form is obtained by premultiplying by $B_0^{-1}$:

$$Y_t = B_0^{-1}c^* + B_0^{-1}B_1 Y_{t-1} + \cdots + \varepsilon_t, \quad \varepsilon_t = B_0^{-1}u_t$$

so $A_i = B_0^{-1}B_i$ and $\Sigma = \text{Var}(\varepsilon_t) = B_0^{-1} D (B_0^{-1})'$.

**Key Points**

- The reduced-form VAR can be estimated consistently by OLS equation-by-equation without any identifying assumptions, yielding $\hat{A}_i$ and $\hat{\Sigma}$.
- Recovering $B_0$ (equivalently $B_0^{-1}$) from $\hat{\Sigma}$ requires additional restrictions, because $\Sigma$ is symmetric with $n(n+1)/2$ free elements, while $B_0$ has $n^2$ free elements (assuming $D = I$ after normalization). The **order condition** for exact identification requires at least $n(n-1)/2$ restrictions on $B_0$ (or equivalently on $B_0^{-1}$) beyond normalizing $D$.
- Different identification schemes impose these restrictions in different ways, each embodying different economic assumptions about how variables interact contemporaneously.

### Short-Run (Contemporaneous) Restrictions

The most common approach imposes zero restrictions directly on $B_0$ or $B_0^{-1}$, specifying that certain structural shocks have no contemporaneous effect on certain variables.

**Cholesky (recursive) identification**: A special case where $B_0^{-1} = P$ is lower triangular, obtained directly from the Cholesky factorization $\Sigma = PP'$. This imposes a strict recursive causal chain: the first variable is unaffected contemporaneously by any other shock, the second is affected only by the first, and so on. It is computationally trivial (no separate estimation step beyond the Cholesky factorization) but requires that the recursive ordering be economically defensible.

**Non-recursive short-run restrictions**: More general zero restrictions on $B_0^{-1}$ that do not force a strict triangular structure, allowing, for instance, two variables to be assumed to not affect each other contemporaneously while both affect a third. Estimated via maximum likelihood, since a closed-form solution (like Cholesky) generally does not exist. A classic example is Sims' (1986) or Bernanke's (1986) restrictions on monetary policy VARs, where policy variables are assumed not to respond contemporaneously to slow-moving real variables, but real variables may respond contemporaneously to policy.

### Long-Run Restrictions

**Blanchard-Quah decomposition** (1989): Instead of restricting contemporaneous effects, imposes restrictions on the **cumulative long-run effect** of shocks. The canonical application restricts a shock (e.g., a nominal/demand shock) to have zero permanent effect on the level of a real variable (e.g., output) in the long run, while a real/supply shock is permitted permanent effects on both variables. This is implemented by restricting elements of the long-run cumulative multiplier matrix $\Theta(1) = \sum_{i=0}^{\infty}\Theta_i = (I - A_1 - \cdots - A_p)^{-1}B_0^{-1}$ to zero.

**Key Points**

- Long-run restrictions require the VAR to be estimated in a form where cumulative long-run multipliers are well-defined and economically interpretable, typically requiring variables like output to enter in first differences (growth rates) so that "long-run level effect" corresponds to a permanent change in the growth path.
- Blanchard-Quah restrictions are popular for decomposing supply and demand shocks in output-unemployment or output-inflation systems, following the identifying logic that only supply shocks have permanent output effects.

### Sign Restrictions

Rather than imposing exact zero restrictions, sign restrictions constrain the *sign* of the IRF response of certain variables to a shock over a specified horizon window (e.g., "a contractionary monetary policy shock must not decrease the interest rate and must not increase prices for $h = 0, \dots, 3$").

**Key Points**

- Sign restrictions are implemented via algorithms that draw random orthogonal rotation matrices $Q$ (satisfying $QQ' = I$) applied to an initial Cholesky factor, accepting draws that satisfy the sign pattern and discarding those that do not (the widely-used approach of Uhlig, 2005, and Rubio-Ramírez, Waggoner, and Zha, 2010).
- This produces a **set** of admissible structural shocks rather than a single point-identified model, so results are typically reported as a range (e.g., the median response across accepted draws, with credible/probability bands), acknowledging that the model is **set-identified** rather than point-identified.
- Sign restrictions are attractive because they require weaker, often more defensible, theoretical assumptions than exact zero restrictions (e.g., from a New Keynesian DSGE model's qualitative predictions), but they can yield wide, sometimes uninformative, bands, and the "reasonable range" of models satisfying the restrictions may still include structurally very different responses on unrestricted variables/horizons.

### External Instruments / Proxy SVAR (SVAR-IV)

Uses an external variable (an instrument) correlated with the structural shock of interest but uncorrelated with other structural shocks, to identify that specific shock without needing to fully specify $B_0$. Common in monetary policy identification using high-frequency interest rate surprises around FOMC announcements as instruments (Gertler and Karadi, 2015; Stock and Watson, 2012; Mertens and Ravn, 2013).

**Key Points**

- Only requires identifying the shock(s) of direct interest, not the full $B_0$ matrix, making it attractive when the researcher cares about one specific structural shock (e.g., a monetary policy shock) rather than the full system.
- Instrument validity requires the same relevance and exogeneity conditions as standard IV estimation: relevance (correlated with the target structural shock) and exogeneity (uncorrelated with other structural shocks and the reduced-form residuals of other equations).

### Sign vs. Zero vs. Long-Run: Comparative Summary

| Scheme | Restriction type | Identification | Typical use case |
| --- | --- | --- | --- |
| Cholesky (recursive) | Zero, contemporaneous, triangular | Point | Baseline/exploratory VARs |
| Non-recursive short-run | Zero, contemporaneous, non-triangular | Point | Theory-motivated contemporaneous timing |
| Blanchard-Quah | Zero, long-run cumulative | Point | Supply/demand decomposition |
| Sign restrictions | Inequality, IRF sign over horizon | Set | Monetary policy, weaker theoretical priors |
| External instruments (Proxy SVAR) | Instrument correlation | Point (for instrumented shock) | Single shock of interest, e.g., monetary surprises |

### Practical Identification Workflow

**Example**

Step 1: Specify the economic model or theoretical priors that motivate the restrictions (e.g., a simple AS-AD framework motivating a Blanchard-Quah demand/supply split).

Step 2: Verify the order condition — count available restrictions against the $n(n-1)/2$ minimum required for exact identification (or confirm the sign-restriction algorithm's search space is well-posed).

Step 3: Estimate $B_0$ (or $B_0^{-1}$) via the chosen method:

- Cholesky: direct factorization of $\hat{\Sigma}$.
- Non-recursive short-run/long-run: maximum likelihood, often via numerical optimization since the likelihood is generally non-linear in the restricted parameters.
- Sign restrictions: draw random orthogonal matrices, filter by sign criteria, retain accepted draws.
- Proxy SVAR: two-stage IV-type procedure regressing reduced-form residuals on the external instrument.

Step 4: Compute structural IRFs and FEVD from the identified $\hat{\Theta}_i = \hat{\Phi}_i \hat{B}_0^{-1}$.

Step 5: Conduct robustness checks — alternative orderings (Cholesky), alternative sign restriction horizons, or alternative instruments — and report sensitivity of key conclusions.

**Output**

For a monetary policy application identified via external instrument (high-frequency Fed funds futures surprises), the identified IRF might show output declining gradually over 6–12 months following a contractionary policy shock, with the peak effect around 8–10 months and a statistically significant negative response. [Inference: precise timing and magnitude are model- and instrument-specific and vary considerably across studies in the empirical literature.]

### Order and Rank Conditions

**Order condition**: A necessary (not sufficient) condition requiring the number of imposed restrictions to be at least $n(n-1)/2$ for exact identification (with $n^2$ restrictions being over-identifying if $D$ is normalized and additional restrictions exceed the minimum).

**Rank condition**: A necessary and sufficient condition verifying that the imposed restrictions are linearly independent and actually pin down each column of $B_0^{-1}$ uniquely, given the structure of $\hat{\Sigma}$. Satisfying the order condition alone does not guarantee identification if restrictions are redundant or the resulting system is singular; the rank condition must be checked, typically numerically, for non-recursive schemes.

### Common Pitfalls

- **Confusing exact and over-identification**: Over-identifying restrictions (more than the minimum required) allow formal testing (likelihood ratio tests) of the restrictions themselves, but under-identification (fewer restrictions than required) means the model is simply not identified and estimates are not interpretable as structural.
- **Weak instrument problems in Proxy SVAR**: An instrument only weakly correlated with the target shock produces unreliable, high-variance structural estimates, analogous to weak-instrument bias in standard IV.
- **Sign restriction "impulse response matching" critique**: Fry and Pagan (2011) showed that the median-response summary commonly reported from sign-restricted SVARs may not correspond to any single internally consistent structural model, since the median is taken separately across each variable/horizon combination from potentially different accepted draws.
- **Overstating point identification confidence**: Presenting zero-restriction results without acknowledging that the specific restrictions are themselves untested assumptions, not empirically verified facts.
- **Non-uniqueness in long-run restrictions with more than 2 variables**: Extending Blanchard-Quah beyond a bivariate system requires care, since long-run restrictions alone may not fully identify larger systems without supplementary short-run restrictions.

### SVAR Identification Landscape Diagram

```mermaid
flowchart TD
    subgraph svar_identification_landscape SVAR Identification Schemes Landscape (svg_diagram)
    A["Reduced-form VAR estimated: A_i, Sigma"] --> B{"Identification approach"}
    B -->|"Zero restrictions, contemporaneous"| C["Short-run restrictions"]
    B -->|"Zero restrictions, cumulative"| D["Long-run restrictions: Blanchard-Quah"]
    B -->|"Inequality on IRF sign"| E["Sign restrictions"]
    B -->|"External correlated variable"| F["Proxy SVAR / External instruments"]
    C --> C1["Recursive: Cholesky triangular P"]
    C --> C2["Non-recursive: MLE-based B0 estimation"]
    D --> D1["Restrict Theta(1) cumulative multiplier matrix"]
    E --> E1["Random orthogonal rotation Q, accept/reject by sign pattern"]
    E1 --> E2["Set-identified: report range or median across accepted draws"]
    F --> F1["IV-type regression of residuals on instrument"]
    C1 --> G["Point-identified B0"]
    C2 --> G
    D1 --> G
    F1 --> H["Point-identified shock of interest only"]
    G --> I["Compute structural IRF and FEVD"]
    E2 --> I
    H --> I
    end
```

### Software Implementation Notes

- **R**: `vars` package (Cholesky baseline), `svars` package (Blanchard-Quah, non-recursive, sign restrictions via `id.chol()`, `id.bq()`, `id.dc()`, `id.ngml()`), `SVARIV`/related packages for proxy SVAR.
- **Python**: `statsmodels` provides basic SVAR support (`statsmodels.tsa.vector_ar.svar_model.SVAR`) with A/B matrix restriction specification; sign-restriction and proxy-SVAR tooling is less standardized and often custom-implemented.
- **MATLAB**: Widely used in academic macro research for sign-restriction and proxy-SVAR routines (e.g., replication codes accompanying Uhlig 2005, Gertler-Karadi 2015).
- **EViews/Stata**: EViews supports short-run and long-run SVAR restrictions natively via its SVAR object; Stata's `svar` command supports short-run and long-run (Blanchard-Quah type) restrictions.

[Unverified: exact function names, default optimizer settings, and package capabilities evolve across versions; verify against current documentation before implementation.]

**Related Topics**

- Impulse response functions
- Forecast error variance decomposition
- Granger causality testing
- Bayesian SVAR estimation and prior elicitation for sign restrictions
- Local projections as an alternative to SVAR-based dynamic causal effects
- DSGE-VAR and theory-consistent identification
- Weak instrument diagnostics in Proxy SVAR (Montiel Olea, Stock, Watson)