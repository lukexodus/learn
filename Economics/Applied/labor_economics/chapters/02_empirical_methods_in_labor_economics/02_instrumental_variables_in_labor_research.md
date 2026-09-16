## Instrumental Variables in Labor Research

### The Endogeneity Problem in Labor Economics

Many core labor economics questions involve regressors that are correlated with the error term in an outcome equation, violating the OLS exogeneity assumption and biasing naive estimates. The canonical case is estimating the **returns to schooling**:

$$\ln(w_i) = \beta_0 + \beta_1 S_i + \epsilon_i$$

Schooling $S_i$ is plausibly correlated with unobserved ability, motivation, family background, and financial resources — all of which independently affect wages $w_i$ and are absorbed into $\epsilon_i$. If higher-ability individuals both obtain more schooling *and* would earn higher wages even without that schooling, OLS overstates the causal return to education ("ability bias"). Instrumental variables (IV) estimation addresses this by isolating variation in the endogenous regressor that is plausibly unrelated to the confounding unobservables.

### Formal IV Requirements

A valid instrument $Z_i$ for endogenous regressor $S_i$ in the equation $Y_i = \beta_0 + \beta_1 S_i + \epsilon_i$ must satisfy two conditions:

1. **Relevance**: $\text{Cov}(Z_i, S_i) \neq 0$ — the instrument must be correlated with the endogenous regressor. This is directly testable (via the first-stage regression) and is the source of the "weak instruments" problem when the correlation is small.
2. **Exclusion restriction**: $\text{Cov}(Z_i, \epsilon_i) = 0$ — the instrument must affect the outcome *only* through its effect on the endogenous regressor, with no direct effect on $Y_i$ and no correlation with other determinants of $Y_i$. This condition is fundamentally **untestable** and must be defended on institutional or theoretical grounds specific to the application.

### Two-Stage Least Squares (2SLS)

The standard IV estimator with a single endogenous regressor is computed via two-stage least squares:

**First stage**: regress the endogenous regressor on the instrument (and any included exogenous controls $X_i$):

$$S_i = \pi_0 + \pi_1 Z_i + \pi_2' X_i + \nu_i$$

**Second stage**: regress the outcome on the *fitted values* $\hat{S}_i$ from the first stage:

$$Y_i = \beta_0 + \beta_1 \hat{S}_i + \beta_2' X_i + \epsilon_i$$

The coefficient $\beta_1$ recovers a consistent estimate of the causal effect, provided the two IV conditions hold. With a single instrument and single endogenous regressor (the **just-identified** case), 2SLS is numerically equivalent to the ratio of reduced-form coefficients (the Wald estimator): $\hat{\beta}_1 = \frac{\text{Cov}(Y,Z)}{\text{Cov}(S,Z)}$.

### Canonical Instruments in Labor Economics

**Compulsory schooling laws / quarter of birth (Angrist and Krueger, 1991).** Because most U.S. states historically required school entry based on a fixed birthdate cutoff and permitted dropout at a fixed age, students born in different quarters of the year were compelled to complete different amounts of schooling before reaching the legal dropout age — quarter of birth predicts completed schooling but is plausibly unrelated to innate ability, providing an instrument for schooling in wage equations. This remains one of the most cited applications of natural-experiment IV design in labor economics.

**Draft lottery instruments (Angrist, 1990).** The Vietnam-era draft lottery assigned draft eligibility via randomly drawn birthdates, instrumenting for military service in studies of the effect of veteran status on subsequent earnings — a design prized for the literal randomization of the instrument.

**College proximity (Card, 1995).** Geographic distance to the nearest college at the time an individual made schooling decisions instruments for completed education, on the argument that proximity reduces the cost of college attendance without directly affecting wages (though this exclusion restriction has been challenged on grounds that college location may correlate with regional labor demand or family background).

**Sibling sex composition / twin births.** Used as instruments for family size in studies of the effect of fertility on female labor supply (Angrist and Evans, 1998), exploiting the fact that parents with same-sex first two children are more likely to have a third child, plausibly for reasons unrelated to the mother's earnings potential.

**Shift-share ("Bartik") instruments.** Constructed by interacting national industry-level employment growth shares with a region's initial industry composition, used extensively to instrument for local labor demand shocks in studies of wage and employment responses to demand shifts. [Inference] This class of instrument has faced substantial recent methodological scrutiny (Goldsmith-Pinkham, Sorkin, and Swift, 2020, and related work) regarding what specific source of identifying variation it captures and under what conditions its exclusion restriction is credible, so its exact validity is now understood to be considerably more application-specific than earlier practice assumed.

### Weak Instruments

When the first-stage relationship between $Z_i$ and $S_i$ is weak (low $\text{Cov}(Z,S)$), 2SLS estimates become biased toward the OLS estimate in finite samples and standard errors become unreliable, even asymptotically. The conventional diagnostic is the **first-stage F-statistic**, with a widely cited (though not universally endorsed) rule-of-thumb threshold of $F > 10$ as a rough indicator against severe weak-instrument bias, alongside more rigorous approaches such as the Stock-Yogo critical values and weak-instrument-robust inference procedures (e.g., the Anderson-Rubin test).

### Local Average Treatment Effect (LATE) Interpretation

When treatment effects are heterogeneous across individuals — a near-universal feature of real-world schooling or program effects — IV estimates do not recover the average treatment effect (ATE) for the full population. Under monotonicity (no individuals whose treatment status responds to the instrument in the "wrong" direction), the IV estimator recovers the **Local Average Treatment Effect (LATE)**: the average causal effect *only* for the subpopulation of "compliers" — individuals whose treatment status is actually changed by variation in the instrument (Imbens and Angrist, 1994).

$$\text{LATE} = E[Y_i(1) - Y_i(0) \mid \text{complier}_i]$$

This has an important practical implication for labor research: the quarter-of-birth instrument identifies the return to schooling specifically for individuals whose schooling decision was affected by compulsory attendance laws (i.e., those who would have dropped out earlier absent the law) — not necessarily the return to schooling for the average student, a distinction essential for correctly interpreting and generalizing IV estimates across different instruments and populations.

### Overidentification and Testing

When more instruments are available than endogenous regressors (**overidentified** models), the **Sargan/Hansen J-test** can test the joint validity of the overidentifying restrictions — though this test only detects whether the *extra* instruments are correlated with each other's implied residuals and cannot validate the exclusion restriction of the full instrument set if all instruments share a common source of invalidity.

### Illustrative Diagram

```mermaid
graph LR
    Z[Instrument Z: e.g. Quarter of Birth] -->|First Stage: Relevance| S[Endogenous Regressor: Schooling]
    S -->|Second Stage| Y[Outcome: Log Wages]
    U[Unobserved Confounders: Ability, Family Background] -.->|Must be uncorrelated: Exclusion Restriction| Z
    U --> S
    U --> Y
```

### Key Points

- IV addresses endogeneity by isolating variation in a regressor driven by an instrument uncorrelated with the outcome equation's error term.
- Relevance is testable via the first-stage F-statistic; the exclusion restriction is not testable and must rest on institutional argument.
- Canonical labor IV designs include quarter-of-birth/compulsory schooling, the Vietnam draft lottery, college proximity, and shift-share (Bartik) instruments.
- Under heterogeneous treatment effects, IV recovers the LATE for compliers, not the population ATE — a critical interpretive caveat when generalizing IV-based returns-to-schooling estimates.

**Related Topics**

- The LATE Framework and Complier Characterization (Imbens-Angrist)
- Weak Instrument Diagnostics and Robust Inference
- Shift-Share (Bartik) Instrument Validity Debates
- Regression Discontinuity as an Alternative Identification Strategy
- Returns to Schooling: A Survey of Estimates Across Designs