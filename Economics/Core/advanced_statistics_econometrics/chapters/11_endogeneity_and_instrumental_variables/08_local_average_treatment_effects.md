## Local Average Treatment Effects

### Definition and Conceptual Overview

The local average treatment effect (LATE) is the average causal effect of a treatment on the subpopulation of **compliers** — units whose treatment status is causally affected by the instrument. Introduced by Imbens and Angrist (1994), LATE addresses the problem that when treatment effects are heterogeneous across individuals, instrumental variables (IV) estimation does not recover the average treatment effect (ATE) for the full population, but rather a weighted average effect for the subgroup induced into treatment by variation in the instrument.

Formally, let $D_i$ denote the binary treatment indicator, $Y_i$ the outcome, and $Z_i$ a binary instrument. Let $D_i(1)$ and $D_i(0)$ denote potential treatment status under $Z_i=1$ and $Z_i=0$, respectively. The LATE is defined as:

$$\text{LATE} = E[Y_i(1) - Y_i(0) \mid D_i(1) > D_i(0)]$$

This is the average treatment effect for individuals whose treatment status would switch from untreated to treated if the instrument switched from 0 to 1.

### The Compliance Framework

Under the potential-outcomes framework for treatment assignment, each unit has a compliance type based on how $D_i$ responds to $Z_i$:

- **Compliers**: $D_i(1) = 1, D_i(0) = 0$ — take treatment if and only if assigned/encouraged via $Z_i=1$
- **Always-takers**: $D_i(1) = 1, D_i(0) = 1$ — take treatment regardless of instrument value
- **Never-takers**: $D_i(1) = 0, D_i(0) = 0$ — never take treatment regardless of instrument value
- **Defiers**: $D_i(1) = 0, D_i(0) = 1$ — take treatment only when *not* encouraged (i.e., act in opposition to the instrument)

Since $Z_i$ and $D_i$ are each binary, this creates a $2\times2$ typology. Compliance type is fundamentally unobservable at the individual level, because for any given unit only one value of $D_i(z)$ is ever realized — a unit is observed at either $Z_i=0$ or $Z_i=1$, never both.

```mermaid
quadrantChart
    title Compliance types by D(0) and D(1) (svg_diagram)
    x-axis D(0)=0 --> D(0)=1
    y-axis D(1)=0 --> D(1)=1
    quadrant-1 Always-takers
    quadrant-2 Compliers
    quadrant-3 Never-takers
    quadrant-4 Defiers
```

### Core Assumptions

LATE identification rests on five assumptions, extending the standard IV exclusion/relevance conditions:

1. **Independence (as-good-as-random assignment)**: $Z_i$ is independent of the vector of potential outcomes and potential treatments, $\{Y_i(1), Y_i(0), D_i(1), D_i(0)\} \perp Z_i$. This ensures the instrument is unconfounded — analogous to the exogeneity requirement in standard 2SLS, but stated over potential values.
2. **Exclusion restriction**: $Y_i(z, d) = Y_i(d)$ for $z = 0, 1$ — the instrument affects the outcome only through its effect on treatment, not directly.
3. **First stage / relevance**: $E[D_i(1)] \neq E[D_i(0)]$, i.e., the instrument has a nonzero effect on treatment take-up on average. This guarantees the denominator of the Wald estimator is nonzero.
4. **Monotonicity (no-defiers assumption)**: $D_i(1) \geq D_i(0)$ for all $i$. No unit is a defier. This is the assumption unique to the LATE framework, distinguishing it from earlier IV heterogeneity treatments.
5. **SUTVA (Stable Unit Treatment Value Assumption)**: No interference between units and only one version of treatment/instrument exists.

**Key Points**

- Monotonicity is not testable directly, since compliance type is unobserved for any single unit, but its plausibility must be argued on institutional or behavioral grounds.
- Without monotonicity, the Wald/IV estimand becomes a difference-weighted average of complier and defier effects, which can be uninterpretable or sign-reversed if defiers are non-negligible.
- Independence is stronger than mean-independence used in linear IV; it requires full distributional independence of potential outcomes/treatments from $Z_i$.

### The Wald Estimator and Its LATE Interpretation

For a binary instrument and binary treatment, the simple IV (Wald) estimator is:

$$\hat{\beta}_{IV} = \frac{E[Y_i \mid Z_i=1] - E[Y_i \mid Z_i=0]}{E[D_i \mid Z_i=1] - E[D_i \mid Z_i=0]}$$

Under assumptions 1–5, Imbens and Angrist (1994) show this ratio identifies exactly the LATE:

$$\hat{\beta}_{IV} \xrightarrow{p} E[Y_i(1) - Y_i(0) \mid D_i(1) > D_i(0)] = \text{LATE}$$

The numerator is the intent-to-treat (ITT) effect — the reduced-form effect of the instrument on the outcome. The denominator is the first-stage effect of the instrument on treatment take-up, which equals the proportion of compliers in the population, $P(D_i(1) > D_i(0))$. Thus:

$$\text{LATE} = \frac{\text{ITT effect on } Y}{\text{Share of compliers}}$$

This scaling relationship clarifies why weak first stages (few compliers) amplify small numerator biases into large LATE biases — the mechanical link to weak-instrument problems discussed in prior IV material.

### Extension to Two-Stage Least Squares (2SLS)

With covariates, multiple instruments, or continuous instruments, 2SLS generalizes the Wald estimator. Angrist and Imbens (1995) show that under an extended monotonicity condition, 2SLS with a vector of instruments identifies a **weighted average of local average treatment effects**, where the weights depend on the relative first-stage strength of each instrument-induced variation. Specifically, when treatment intensity is multi-valued or instruments are multiple, the 2SLS estimand is a positively-weighted average of the LATEs associated with each unit interval of instrument-induced variation in $D_i$, provided monotonicity holds for each instrument component.

**Example**

Consider an empirical application: assignment to a job-training lottery ($Z_i$) as an instrument for actual program participation ($D_i$), used to estimate the effect on earnings ($Y_i$). Suppose:

- $E[Y_i \mid Z_i=1] = 21{,}500$, $E[Y_i \mid Z_i=0] = 20{,}000$ (ITT effect = $1,500)
- $E[D_i \mid Z_i=1] = 0.60$, $E[D_i \mid Z_i=0] = 0.20$ (first stage = 0.40, i.e., 40% of the sample are compliers)

$$\hat{\beta}_{IV} = \frac{1500}{0.40} = 3750$$

This $3,750 is interpreted as the average earnings gain **only for the 40% of the sample induced into training by lottery assignment** — not for always-takers (who would train regardless) or never-takers (who never train regardless of winning the lottery).

### LATE vs. ATE vs. ATT

| Estimand | Population | Identification strategy |
| --- | --- | --- |
| ATE | Entire population | Requires unconfoundedness (RCT or full selection-on-observables) |
| ATT (average treatment on treated) | Treated units only | Matching, DiD, or IV under specific conditions |
| LATE | Compliers only | IV with monotonicity |

LATE coincides with ATE only under the special case of **homogeneous treatment effects** (i.e., $Y_i(1) - Y_i(0)$ constant across $i$), in which case the complier subpopulation's effect equals every other subpopulation's effect. LATE coincides with ATT when always-takers do not exist (i.e., treatment participation absent the instrument is zero, as in encouragement designs with no baseline access).

[Inference] In applied practice, LATE is often treated as an approximation to a policy-relevant treatment parameter, but this substitution is valid only when policymakers specifically care about the marginal population affected by the instrument-driven variation (e.g., a specific eligibility expansion), not the full population.

### External Validity and the "Local" Critique

The defining limitation of LATE is that it is inherently **instrument-specific**: different valid instruments for the same treatment-outcome relationship generally identify different LATEs, because they induce compliance among different subpopulations. For example, distance-to-college and tuition-cost instruments for schooling both satisfy IV validity conditions but identify effects for different complier populations (students on the margin of decision due to geographic proximity vs. those on the margin due to price sensitivity).

This creates challenges for:

- **Policy extrapolation**: A LATE estimated from one instrument may not generalize to a different policy intervention affecting a different marginal population.
- **Comparing studies**: Discrepancies in IV estimates across papers using different instruments may reflect genuine effect heterogeneity across complier groups rather than estimation error.

Related identification work (Mogstad, Torgovitsky, and Walters; Heckman and Vytlacil's marginal treatment effect (MTE) framework) generalizes LATE by modeling how treatment effects vary continuously with an unobserved resistance/propensity margin, allowing researchers to extrapolate beyond the complier population under additional structural assumptions.

### Testing and Diagnostics

**Key Points**

- **First-stage strength**: Report first-stage F-statistics; weak first stages (few compliers) inflate finite-sample bias and variance of the LATE estimator, exactly as in standard weak-IV diagnostics.
- **Monotonicity checks**: While not directly testable, researchers assess plausibility via covariate balance across instrument values among always-takers/never-takers if partially identifiable, or via bounds/sensitivity analysis (e.g., testing the sign of the first stage across covariate subgroups — a negative first stage in some subgroup can indicate defiers).
- **Complier characteristics**: Abadie's (2003) kappa-weighting method allows researchers to characterize the covariate distribution of compliers, revealing which subpopulation the LATE actually describes.
- Balance/placebo tests on the exclusion restriction remain essential, as in standard IV.

### Estimating Complier Characteristics (Abadie's Kappa Weights)

To describe compliers' observable characteristics, Abadie (2003) proposes a weighting scheme:

$$\kappa_i = 1 - \frac{D_i(1-Z_i)}{P(Z_i=0 \mid X_i)} - \frac{(1-D_i)Z_i}{P(Z_i=1 \mid X_i)}$$

Weighting the sample by $\kappa_i$ allows estimation of $E[g(Y_i, D_i, X_i) \mid \text{complier}]$ for any function $g$, enabling researchers to compute complier means of covariates, complier-specific treatment effect heterogeneity, and complier-weighted regressions — all conditional on being a complier without directly observing complier status.

### Multi-Valued and Continuous Treatment/Instrument Extensions

- **Fuzzy regression discontinuity (RD)**: When treatment assignment is probabilistically determined by crossing a threshold (rather than deterministically), the fuzzy RD estimator identifies a LATE for compliers at the threshold — sometimes called a "local LATE."
- **Ordered/continuous treatment**: With continuous $D_i$, 2SLS with a binary instrument identifies a weighted average of the derivative of the outcome with respect to treatment intensity, averaged over compliers' induced movement along the treatment margin (Angrist, Graddy, and Imbens 2000).
- **Multiple instruments**: Each instrument (or instrument interacted with covariates) generally identifies a different-weighted LATE; overidentification tests (Hansen J, Sargan) test the *overidentifying restriction* of equal population moments, not equality of underlying LATEs, and can spuriously reject under genuine treatment effect heterogeneity even when both instruments are valid.

### Diagrammatic Summary of Identification Logic

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 900 480" font-family="Arial, sans-serif">
<text x="450" y="30" font-size="18" font-weight="bold" text-anchor="middle">LATE Identification Logic (svg_diagram)</text>
<rect x="40" y="70" width="220" height="70" rx="8" fill="#E8F0FE" stroke="#4285F4" stroke-width="2" />
<text x="150" y="98" font-size="13" text-anchor="middle" font-weight="bold">Instrument Z</text>
<text x="150" y="118" font-size="11" text-anchor="middle">(independent, exclusion,</text>
<text x="150" y="132" font-size="11" text-anchor="middle">relevant, monotonic)</text>
<rect x="340" y="70" width="220" height="70" rx="8" fill="#FEF7E0" stroke="#F9AB00" stroke-width="2" />
<text x="450" y="98" font-size="13" text-anchor="middle" font-weight="bold">Treatment D</text>
<text x="450" y="118" font-size="11" text-anchor="middle">Compliers / Always-takers /</text>
<text x="450" y="132" font-size="11" text-anchor="middle">Never-takers / (no Defiers)</text>
<rect x="640" y="70" width="220" height="70" rx="8" fill="#E6F4EA" stroke="#34A853" stroke-width="2" />
<text x="750" y="98" font-size="13" text-anchor="middle" font-weight="bold">Outcome Y</text>
<text x="750" y="118" font-size="11" text-anchor="middle">Observed earnings,</text>
<text x="750" y="132" font-size="11" text-anchor="middle">test scores, etc.</text>
<line x1="260" y1="105" x2="335" y2="105" stroke="#333" stroke-width="2" marker-end="url(#arrow)" />
<text x="297" y="95" font-size="10" text-anchor="middle">First stage</text>
<line x1="560" y1="105" x2="635" y2="105" stroke="#333" stroke-width="2" marker-end="url(#arrow)" />
<text x="597" y="95" font-size="10" text-anchor="middle">Causal effect</text>
<path d="M 150 140 Q 450 260 750 140" fill="none" stroke="#EA4335" stroke-width="2" stroke-dasharray="5,4" marker-end="url(#arrowred)" />
<text x="450" y="255" font-size="11" text-anchor="middle" fill="#EA4335">Exclusion restriction: NO direct effect of Z on Y</text>
<rect x="130" y="300" width="640" height="150" rx="8" fill="#F8F9FA" stroke="#9AA0A6" stroke-width="1.5" />
<text x="450" y="325" font-size="13" font-weight="bold" text-anchor="middle">Population partition (monotonicity: no defiers)</text>
<rect x="150" y="345" width="140" height="80" fill="#D2E3FC" stroke="#4285F4" />
<text x="220" y="390" font-size="11" text-anchor="middle">Always-takers</text>
<rect x="300" y="345" width="140" height="80" fill="#CEEAD6" stroke="#34A853" />
<text x="370" y="385" font-size="11" text-anchor="middle" font-weight="bold">Compliers</text>
<text x="370" y="400" font-size="10" text-anchor="middle">(LATE identified here)</text>
<rect x="450" y="345" width="140" height="80" fill="#FDE9E9" stroke="#EA4335" />
<text x="520" y="390" font-size="11" text-anchor="middle">Never-takers</text>
<rect x="600" y="345" width="140" height="80" fill="#F1F1F1" stroke="#9AA0A6" stroke-dasharray="4,3" />
<text x="670" y="385" font-size="11" text-anchor="middle">Defiers</text>
<text x="670" y="400" font-size="10" text-anchor="middle">(assumed empty)</text>
</svg>

### Software Implementation

**Example**

In R, using the `ivreg` package (formerly `AER`):

```r
library(ivreg)
# D = treatment, Z = instrument, X = covariates
fit <- ivreg(Y ~ D + X | Z + X, data = mydata)
summary(fit, diagnostics = TRUE)  # includes weak-instrument F-stat
```

In Stata:

```stata
ivregress 2sls Y (D = Z) X, robust
estat firststage
```

For complier characteristic analysis via kappa-weighting, the R package `ivdesc` or manual implementation of Abadie's weights can be used. [Unverified] Exact package availability and function names may vary by version; consult current CRAN/package documentation before use.

### Common Pitfalls

**Key Points**

- Interpreting LATE as if it were ATE — a frequent misstep in applied papers, especially when policy conclusions require population-wide effects.
- Ignoring possible defiers when monotonicity is institutionally implausible (e.g., instruments involving discretionary human judgment where behavioral responses could go either direction).
- Combining multiple instruments into a single 2SLS estimate without recognizing that the resulting estimand is a complier-weighted average across *different* complier populations, not a single well-defined LATE.
- Failing to report or diagnose first-stage strength, leading to weak-instrument bias that is amplified in the LATE ratio.
- Assuming the exclusion restriction holds without institutional justification — LATE inherits full sensitivity to this assumption from standard IV.

### Related Topics

- Two-stage least squares (2SLS) and weak instrument diagnostics
- Marginal treatment effects (MTE) framework (Heckman–Vytlacil)
- Fuzzy regression discontinuity design
- Abadie's kappa-weighting for complier characterization
- Extrapolation methods (Mogstad–Torgovitsky–Walters IV-extrapolation)
- Selection-on-observables vs. selection-on-unobservables identification strategies
- Heterogeneous treatment effects and quantile treatment effects under IV