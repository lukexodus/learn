## Research Design in Empirical Legal Scholarship

### Conceptual Foundations

Empirical legal studies (ELS) applies the causal-inference methodology of applied microeconomics and econometrics to legal questions previously addressed primarily through doctrinal analysis, theoretical modeling, or unsystematic case observation — does a given tort-reform statute actually reduce litigation rates, does judicial ideology predictably affect case outcomes, does a minimum-wage increase reduce employment, does a given sentencing-guideline reform affect recidivism. This item establishes the research-design vocabulary and methodological toolkit underlying subsequent chapter items on specific identification strategies (natural experiments, regression discontinuity, difference-in-differences) and on the broader replication and credibility challenges facing the field.

**Key Points**

- The central methodological challenge distinguishing rigorous ELS from purely correlational legal-policy analysis is **causal identification**: establishing that an observed association between a legal rule or intervention and an outcome reflects the rule's actual causal effect, rather than confounding factors that jointly influence both the legal rule's adoption/application and the outcome of interest
- Legal and policy variation is rarely, if ever, randomly assigned in the way a designed laboratory experiment would be — jurisdictions adopting a given tort reform, judges assigned varying caseloads, or defendants receiving varying sentences typically differ systematically along both observed and unobserved dimensions correlated with the outcome being studied, making naive before-after or cross-jurisdictional comparisons highly vulnerable to confounding
- The modern ELS methodological program, heavily influenced by the broader "credibility revolution" in applied microeconomics (associated with economists including Joshua Angrist, Guido Imbens, and others), emphasizes explicit, transparent identification strategies — natural experiments, instrumental variables, regression discontinuity, difference-in-differences — that exploit specific institutional features of the legal system generating quasi-random variation, over purely observational regression-based approaches relying on the much stronger and less verifiable assumption that all relevant confounders have been observed and controlled for

### The Fundamental Problem of Causal Inference and the Potential Outcomes Framework

**Key Points**

- The **Rubin causal model** (potential outcomes framework) formalizes the causal-inference problem underlying all ELS research design: for any unit (a case, a jurisdiction, a defendant) that could potentially receive a legal treatment (a new statute, a sentencing enhancement, a regulatory intervention), there exist two *potential outcomes* — the outcome that would occur under treatment, and the outcome that would occur absent treatment — with the individual causal effect defined as the difference between these two potential outcomes
- The **fundamental problem of causal inference**: for any given unit, only one of the two potential outcomes is ever actually observed (the unit either receives the treatment or does not, in the world that actually unfolds), meaning the individual causal effect is never directly observable, and all causal-inference methodology reduces to strategies for credibly estimating an *average* causal effect across units using comparison groups that approximate the unobserved counterfactual

$$\tau_i = Y_i(1) - Y_i(0)$$

where $\tau_i$ is unit $i$'s individual causal effect, $Y_i(1)$ is the potential outcome under treatment, and $Y_i(0)$ is the potential outcome absent treatment — since only one of $Y_i(1)$ or $Y_i(0)$ is observed for any given unit, credible causal-effect estimation requires a comparison group whose average outcome plausibly approximates the treated group's *counterfactual* untreated outcome (or vice versa).

- **Selection bias as the central threat**: naive comparison of treated and untreated (or before/after) outcomes yields an unbiased causal-effect estimate only if treatment assignment is independent of potential outcomes (as would hold under random assignment) — in observational legal-policy settings, treatment (adoption of a legal rule, assignment to a particular judge, receipt of a particular sentence) is typically *not* independent of potential outcomes, since the same factors influencing whether a jurisdiction adopts a reform, or whether a defendant receives a harsher sentence, frequently also independently influence the outcome being studied

===MERMAID_DIAGRAM===

flowchart TD

A[Research Question: Causal Effect of Legal Rule/Intervention] --> B{Random Assignment Available?}

B -->|Yes: True Experiment| C[Randomized Controlled Trial]

B -->|No: Observational Setting| D[Quasi-Experimental Identification Strategy Required]

D --> E[Natural Experiment / Instrumental Variables]

D --> F[Regression Discontinuity Design]

D --> G[Difference-in-Differences]

D --> H[Matching / Selection-on-Observables]

C --> I[Treatment Independent of Potential Outcomes]

E --> J[Exploits Quasi-Random Institutional Variation]

F --> K[Exploits Discontinuous Rule/Threshold Assignment]

G --> L[Exploits Differential Timing of Policy Adoption]

H --> M[Assumes No Unobserved Confounders - Strongest Assumption]

I --> N[Credible Causal Estimate]

J --> N

K --> N

L --> N

M --> O[Causal Estimate Only as Credible as Unconfoundedness Assumption]

### Internal Validity Versus External Validity in Legal Research Design

**Key Points**

- **Internal validity** concerns whether a study's estimated effect accurately reflects the true causal effect *within the specific sample and context studied* — threats to internal validity in ELS research include selection bias, omitted-variable confounding, reverse causality (the outcome influencing the legal-rule adoption decision rather than vice versa, a particularly acute concern in legal-policy research since legislatures frequently adopt reforms specifically *in response to* deteriorating outcome trends), and measurement error in legal-outcome variables (case-outcome coding, recidivism definitions, litigation-rate measurement)
- **External validity** concerns whether a credibly internally valid causal estimate from a specific study context (a specific jurisdiction, time period, or population) generalizes to other contexts of policy interest — a well-identified natural experiment studying a minimum-wage increase in one state, or a sentencing-reform effect in one court system, may not generalize to a different jurisdiction with different labor-market conditions, different judicial-administration practices, or a different underlying population composition
- The internal-validity/external-validity tradeoff is a recurring methodological tension in ELS: the identification strategies (natural experiments, regression discontinuity) that best address internal-validity threats frequently do so by exploiting narrow, context-specific institutional features (a specific statutory threshold, a specific policy-adoption timing pattern) that inherently limit the finding's direct generalizability, requiring researchers and policy audiences to exercise judgment about the appropriate scope of extrapolation from any single well-identified study — a judgment that should be treated as [Inference] specific to the comparability of the extrapolation context, not as a mechanical extension of the original study's findings

### Selection-on-Observables Versus Selection-on-Unobservables

**Key Points**

- **Selection-on-observables** approaches (multiple regression with control variables, exact or propensity-score matching) rely on the identifying assumption that, conditional on the observed control variables included in the analysis, treatment assignment is as good as random — this is a substantially weaker and more easily violated assumption than true randomization, since it requires the researcher to have measured and included *every* confounding variable that jointly influences both treatment assignment and the outcome, an assumption that is generally unverifiable and frequently implausible in rich institutional settings where legal-rule adoption or case assignment reflects complex, only partially observable institutional and political processes
- **Selection-on-unobservables robustness concerns**: even sophisticated selection-on-observables approaches remain vulnerable to confounding from *unobserved* variables correlated with both treatment and outcome — a persistent methodological concern in, for example, studies of judicial-ideology effects on case outcomes (since judicial assignment, even when formally randomized within a courthouse's case-assignment system, may not be verified as such, and judges' observable characteristics may not capture all relevant unobserved judicial-decision-making heterogeneity) or studies of the effect of legal representation quality on case outcomes (since case or client selection into higher-quality representation is rarely random and rarely fully captured by observable case characteristics)
- **Sensitivity analysis and robustness checks**: given the fundamental unverifiability of the "no unobserved confounders" assumption underlying selection-on-observables approaches, rigorous ELS research design typically incorporates sensitivity analyses (formal bounds on how large an unobserved confounder would need to be to overturn the estimated result, following frameworks such as Rosenbaum bounds or the more recent Oster-coefficient-stability approach) as a partial, though not fully resolving, response to this fundamental identification limitation

### The Credibility Revolution and Its Influence on Empirical Legal Studies

**Key Points**

- The broader applied-microeconomics "credibility revolution" (a term substantially associated with Angrist and Pischke's influential methodological writing) emphasized a shift away from complex, heavily-parameterized structural models resting on numerous difficult-to-verify assumptions, toward simpler, more transparent "design-based" identification strategies whose核心identifying assumptions can be more directly articulated, defended, and empirically probed (e.g., via placebo tests, pre-trend analysis in difference-in-differences designs, or covariate-balance tests around regression-discontinuity thresholds)
- ELS has substantially imported this design-based methodological orientation, with the subsequent chapter items on natural experiments, regression discontinuity, and difference-in-differences representing the specific identification-strategy toolkit this credibility-revolution orientation has popularized within legal scholarship specifically
- **Persistent critique of over-reliance on "clever" natural experiments**: a countervailing methodological concern, raised both within economics generally and within ELS specifically, holds that the credibility revolution's emphasis on finding institutionally clever sources of quasi-random variation can bias the *questions researchers ask* toward those questions happen to have available a convenient natural experiment, rather than toward the questions of greatest genuine policy importance — this is a methodological-scope critique rather than a technical flaw in any specific identification strategy, and represents an ongoing, unresolved tension in the field's overall research-agenda-setting process

### Pre-Registration, Replication, and the Credibility of Empirical Legal Findings

**Key Points**

- Following broader social-science methodological reform movements (substantially motivated by documented replication failures and concerns about publication bias and specification-search/"p-hacking" practices across empirical social science), empirical legal scholarship has increasingly adopted **pre-registration** (publicly committing to a specific research design, outcome measure, and analytical specification before observing outcome data) and **pre-analysis plans** as a methodological response intended to reduce the scope for post-hoc specification search that can inflate the apparent statistical significance and generalizability of reported findings
- **Publication bias concerns** are particularly acute in ELS given the field's frequently policy-advocacy-adjacent character, where findings supporting a particular legal-reform direction may face differential publication or citation incentives relative to null or contrary findings — this dynamic is a recognized concern across empirical social science generally but carries particular salience in ELS given the field's direct engagement with contested legal-policy debates
- **Multiple-hypothesis-testing and specification-robustness reporting**: contemporary best-practice ELS methodology increasingly expects researchers to report robustness across multiple plausible model specifications (rather than a single preferred specification), to correct statistical significance thresholds for multiple-hypothesis-testing where numerous outcome variables or subgroup analyses are examined, and to make replication data and code publicly available — norms substantially strengthened over the past decade but still unevenly and incompletely adopted across the field, an ongoing institutional-reform process rather than a fully achieved methodological standard

### Comparing Core Identification Strategies (Overview for Subsequent Chapter Items)

| Strategy | Core Source of Identifying Variation | Key Identifying Assumption | Typical Legal Application |
| --- | --- | --- | --- |
| Randomized controlled trial | Explicit random assignment | Successful randomization (balance across treatment/control) | Legal-aid intervention RCTs, court-notification-reminder experiments |
| Natural experiment / instrumental variables | Quasi-random institutional variation (e.g., random judge assignment, policy-timing quirks) | Instrument affects outcome only through treatment (exclusion restriction) | Judicial-ideology effect studies using random case assignment |
| Regression discontinuity | Sharp threshold/cutoff determining treatment assignment | No manipulation of assignment variable near threshold; comparability of units just above/below | Sentencing-guideline threshold effects, eligibility-cutoff program effects |
| Difference-in-differences | Differential timing of policy adoption across jurisdictions | Parallel pre-treatment trends between treated and comparison units absent treatment | State-level tort-reform or minimum-wage-law effect studies |
| Selection-on-observables/matching | Rich observed covariates approximating random assignment conditional on covariates | No unobserved confounders correlated with both treatment and outcome | Case-outcome studies where richer randomization-based designs are unavailable |

**Next Steps**

- Natural experiments and instrumental variables in legal research (detailed identification-strategy treatment)
- Regression discontinuity design applications in sentencing, eligibility, and threshold-based legal rules
- Difference-in-differences and event-study designs for policy-adoption timing analysis
- Randomized controlled trials in legal-services and access-to-justice research
- The replication crisis and open-science reform in empirical legal scholarship
- Judicial-decision-making empirical studies and random case-assignment identification strategies