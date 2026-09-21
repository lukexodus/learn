## Sign Restrictions for Identification

### Conceptual Foundation

Sign restrictions are an identification approach for structural VARs that constrain the *direction* (sign) of impulse response functions to a shock, over a specified set of variables and horizons, rather than imposing exact zero restrictions on contemporaneous or long-run coefficients. Instead of asserting, for example, that a policy shock has *no* contemporaneous effect on output (a zero restriction), a sign-restricted approach might assert only that a contractionary monetary policy shock does not *decrease* the interest rate and does not *increase* prices over some horizon window — restrictions that are typically easier to defend from a wide class of theoretical models (e.g., New Keynesian DSGE models) than precise zero-timing assumptions.

The approach was developed primarily by Faust (1998), Canova and De Nicolò (2002), and Uhlig (2005), with important algorithmic refinements by Rubio-Ramírez, Waggoner, and Zha (2010).

### Motivation Relative to Zero Restrictions

**Key Points**

- Zero restrictions (recursive Cholesky, non-recursive short-run, or long-run Blanchard-Quah) require the researcher to assert *exact* timing or magnitude conditions (e.g., "variable $X$ has literally zero contemporaneous response"), which many economic theories do not sharply imply.
- Many macroeconomic theories instead imply directional/qualitative predictions robustly across model variants and calibrations — e.g., most New Keynesian models agree a contractionary monetary shock raises the nominal rate and lowers output and prices, even if they disagree on exact magnitudes or precise timing of zero effects.
- Sign restrictions leverage this more robust, weaker form of theoretical agreement, at the cost of moving from point identification to **set identification**: the data and restrictions together pin down a *range* of admissible structural models rather than a single one.

### Mathematical Setup

Starting from the reduced-form VAR with $\hat{\Sigma} = \hat{P}\hat{P}'$ (Cholesky factor $\hat{P}$), any orthogonal rotation of $\hat{P}$ is an equally valid factorization of $\hat{\Sigma}$:

$$\tilde{P} = \hat{P}Q, \quad \text{where } QQ' = Q'Q = I_n$$

Since $\tilde{P}\tilde{P}' = \hat{P}QQ'\hat{P}' = \hat{P}\hat{P}' = \hat{\Sigma}$, any orthogonal $Q$ generates an alternative, equally consistent-with-the-data set of structural shocks $\tilde{u}_t = \tilde{P}^{-1}\varepsilon_t$. This is precisely the source of non-uniqueness in SVAR identification: the reduced-form covariance $\Sigma$ alone cannot distinguish among the infinite family of $\tilde{P} = \hat{P}Q$ candidates. Sign restrictions select a *subset* of this family by requiring that the implied IRFs, $\tilde{\Theta}_i = \Phi_i \hat{P}Q$, satisfy pre-specified sign patterns over chosen variables and horizons.

### Algorithmic Implementation

**Example**

Step 1: Estimate the reduced-form VAR and obtain $\hat{\Sigma}$, $\hat{\Phi}_i$; compute the baseline Cholesky factor $\hat{P}$.

Step 2: Draw a random orthogonal matrix $Q$. The standard approach (Rubio-Ramírez, Waggoner, and Zha, 2010) generates $Q$ via QR decomposition of a random matrix drawn from a standard normal distribution, ensuring $Q$ is drawn uniformly (Haar measure) over the space of orthogonal matrices.

Step 3: Compute candidate structural impulse responses $\tilde{\Theta}_i = \hat{\Phi}_i \hat{P}Q$ for the shock(s) of interest.

Step 4: Check whether the implied IRFs satisfy the pre-specified sign pattern over the designated horizon window (e.g., horizons $h = 0$ to $h = 3$ for a contractionary monetary shock: $\text{IR}_{\text{rate}}(h) \geq 0$, $\text{IR}_{\text{prices}}(h) \leq 0$).

Step 5: If satisfied, **accept** and store the draw; if not, **reject** and discard. Repeat Steps 2–4 for many draws (commonly combined with posterior draws of the reduced-form parameters themselves, in a Bayesian setting, to also capture parameter uncertainty) until a target number of accepted draws is reached (e.g., 1,000–10,000).

Step 6: Summarize the accepted draws' IRFs and FEVDs across percentiles (e.g., 16th/84th or 5th/95th) to report credible/probability bands, rather than a single point estimate.

**Output**

For a monetary policy shock identified via sign restrictions on a VAR with output, prices, and the interest rate, a typical reporting format shows the median accepted-draw IRF alongside a shaded 68% credible band: the interest rate response is pinned near zero or positive by construction over the restriction horizon, prices show a restricted non-positive response over the same window, and output — left **unrestricted** — shows a declining path with a wide credible band reflecting the range of admissible models. [Inference: exact magnitudes are illustrative; results are highly dependent on the specific restriction horizon, variable set, and sample used.]

### Design Choices in Specifying Restrictions

**Key Points**

- **Restriction horizon length**: Restrictions can be imposed only at impact ($h=0$), over a short window ($h=0$ to $h=3$, say), or over longer horizons. Longer restriction windows narrow the admissible set but risk imposing assumptions with less robust theoretical support at longer horizons.
- **Which variables to restrict**: Typically only a subset of variables is restricted for a given shock (to preserve set-identification flexibility and let the data speak on the variable of primary research interest, often left unrestricted, such as output in a monetary policy study).
- **Restricting multiple shocks simultaneously**: When identifying more than one structural shock via sign restrictions in the same system, care must be taken that restriction sets for different shocks are mutually consistent and do not overlap in ways that create additional unintended constraints.
- **Zero and sign restrictions combined**: Modern approaches (Arias, Rubio-Ramírez, and Waggoner, 2018) allow combining exact zero restrictions with sign restrictions in a single coherent identification scheme, tightening the identified set relative to sign restrictions alone.

### Critiques and Known Limitations

**Fry and Pagan (2011) "impulse response matching" critique**: The commonly reported median-response summary (taking the median IRF value separately at each horizon/variable across all accepted draws) does not generally correspond to the IRF of any single accepted model — the "median response" is a composite of potentially different underlying $Q$ draws at different horizons and variables. Fry and Pagan recommend instead selecting and reporting a single "median-target" model (the accepted draw closest to the reported medians) for internally consistent structural interpretation.

**Sign restriction bands can be wide and uninformative**: Because the approach is set-identified, wide credible bands are common, especially for unrestricted variables and at longer horizons, sometimes limiting the ability to draw sharp economic conclusions. [Inference: the severity of this issue is highly context- and application-specific.]

**Restrictions themselves are assumptions, not tests**: As with zero restrictions, the validity of a sign-restriction identification scheme rests on the researcher's theoretical priors, which are not directly tested by the data (though over-identifying combinations with zero restrictions can, in principle, be partially assessed).

**Prior sensitivity in Bayesian implementations**: When sign restrictions are combined with a prior over the space of orthogonal rotations $Q$ (as is standard, since the uniform Haar measure is itself effectively a prior choice), Baumeister and Hamilton (2015) showed that the implicit prior over structural parameters (not just the rotation) can meaningfully influence posterior inference, and researchers should assess sensitivity to this often under-acknowledged choice.

### Comparative Table: Sign Restrictions vs. Point Identification

| Aspect | Zero restrictions (Cholesky/SVAR) | Sign restrictions |
| --- | --- | --- |
| Identification type | Point | Set |
| Theoretical requirement | Precise timing/magnitude assumption | Directional/qualitative agreement |
| Reported output | Single IRF/FEVD estimate with sampling CI | Range across accepted draws (credible bands) |
| Computational approach | Closed-form (Cholesky) or MLE | Random rotation search with accept/reject |
| Key risk | Invalid exact restriction biases entire result | Wide, potentially uninformative bands; median-matching pitfall |

### Common Pitfalls

- **Reporting only the pointwise median IRF without acknowledging the Fry-Pagan critique** or without providing an alternative internally-consistent "representative model" summary.
- **Restricting too many variables/horizons**, effectively approaching point identification through the back door while still reporting results as if genuinely set-identified, obscuring how much of the result is restriction-driven versus data-driven.
- **Ignoring rotation prior sensitivity**: treating the standard uniform-over-orthogonal-matrices approach as assumption-free, when it is itself an implicit prior with potential consequences for posterior shape.
- **Small sample size interacting with wide rotation search space**: In short samples, sign-restricted bands can become extremely wide, sometimes spanning both very large and near-zero effects, limiting practical inferential value.

### Sign Restriction Search Algorithm Diagram

```mermaid
flowchart TD
    subgraph sign_restriction_algorithm Sign Restriction Identification Algorithm (svg_diagram)
    A["Reduced-form VAR: Sigma-hat, Phi_i-hat"] --> B["Baseline Cholesky factor P-hat: Sigma-hat = P-hat P-hat'"]
    B --> C["Draw random orthogonal matrix Q via QR decomposition of random normal matrix"]
    C --> D["Compute candidate Theta_i = Phi_i-hat times P-hat times Q"]
    D --> E{"IRFs satisfy sign pattern over specified variables and horizons?"}
    E -->|"No"| C
    E -->|"Yes"| F["Accept and store draw"]
    F --> G{"Target number of accepted draws reached?"}
    G -->|"No"| C
    G -->|"Yes"| H["Summarize accepted draws: median, 16th/84th or 5th/95th percentile bands"]
    H --> I["Optional: apply Fry-Pagan median-target selection for internally consistent single model"]
    end
```

### Software Implementation Notes

- **R**: `svars` package (`id.dc()` for related decompositions; sign-restriction routines also available via `VARsignR` package, e.g., `uhlig.reject()`, `uhlig.penalty()`, `rwz.reject()` implementing Rubio-Ramírez-Waggoner-Zha style search).
- **MATLAB**: Widely used for sign-restriction implementations in academic macro research; replication codes accompanying Uhlig (2005) and related papers are commonly MATLAB-based.
- **Python**: Sign-restriction tooling is less standardized in mainstream packages (e.g., `statsmodels`) and is frequently custom-implemented following the rotation-search algorithm described above.
- **Dynare (MATLAB/Julia)**: Supports Bayesian SVAR with sign restrictions in some configurations, primarily in DSGE-VAR contexts.

[Unverified: exact function names, default rotation-sampling methods, and package-specific conventions vary across versions and implementations; verify against current package documentation before use.]

**Related Topics**

- Structural VAR identification schemes (zero and long-run restrictions)
- Impulse response functions
- Forecast error variance decomposition
- Bayesian VAR estimation and prior specification
- Fry-Pagan median-target model selection
- Zero-and-sign combined restrictions (Arias, Rubio-Ramírez, Waggoner)
- External instruments / Proxy SVAR identification