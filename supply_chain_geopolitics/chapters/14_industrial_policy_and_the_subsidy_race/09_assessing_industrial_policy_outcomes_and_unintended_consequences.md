## Assessing Industrial Policy Outcomes and Unintended Consequences


### Overview

Evaluating whether industrial policy interventions achieve their stated objectives — and at what cost — is methodologically difficult, given long time horizons, counterfactual ambiguity, and the multiplicity of concurrent economic forces affecting any targeted sector. This topic surveys the analytical frameworks used to assess industrial policy outcomes and catalogs the recurring categories of unintended consequences observed across the CHIPS Act, EU Chips Act, Made in China 2025, and related programs discussed elsewhere in this curriculum.

### Methodological Challenges in Evaluation

#### The Counterfactual Problem

The central evaluation challenge is establishing what would have happened absent the intervention. A semiconductor fab might have been built domestically even without subsidies (due to market demand growth), meaning the subsidy could be evaluated as producing zero net additionality if it merely accelerated or relocated an investment decision that market forces would have independently produced.

$$Additionality=Outcome_{observed}-Outcome_{counterfactual}$$

[Inference] In practice, robust counterfactual estimation for large, one-off strategic investments (a single semiconductor mega-fab) is far harder than for small-scale, high-frequency programs (e.g., SME tax credits) where comparison groups and quasi-experimental methods (difference-in-differences, matched comparison regions) are more feasible; much industrial policy evaluation therefore relies on qualitative case analysis and stated-intent tracking rather than rigorous causal inference.

#### Time Horizon Mismatch

Industrial policy outcomes (workforce development, ecosystem agglomeration effects, technological spillovers) often materialize over 5-15 year horizons, while political accountability cycles and budget evaluation windows typically operate on 1-4 year cycles — creating a structural mismatch between when programs are evaluated and when their full effects would be observable.

#### Announcement vs. Realization Gap

As discussed in the context of reshoring measurement, announced investment and job figures frequently diverge from realized outcomes. Rigorous assessment requires tracking projects through their full lifecycle (announcement → permitting → construction → hiring → production ramp) rather than treating announcement figures as outcomes.

```mermaid
flowchart LR
    A[Policy Announcement] --> B[Announced Investment/Jobs]
    B --> C[Permitting and Site Selection]
    C --> D[Construction Phase]
    D --> E[Workforce Hiring]
    E --> F[Production Ramp]
    F --> G[Realized Outcome]
    G -.compare.-> H[Counterfactual Baseline]
    H --> I[Net Additionality Estimate]
```

### Evaluation Frameworks

#### Input-Output-Outcome-Impact Chain

A standard program evaluation logic model distinguishes:

- **Inputs**: fiscal resources committed (grants, tax credits, loan guarantees)
- **Outputs**: direct, immediately measurable results (facilities built, jobs announced, funding disbursed)
- **Outcomes**: intermediate effects (employment realized, domestic production capacity added, import substitution achieved)
- **Impact**: longer-term, broader effects (supply chain resilience achieved, technological spillovers to adjacent industries, regional economic development)

Most publicly available industrial policy reporting (e.g., initial CHIPS Act and Chips Act announcements) concentrates on outputs, while rigorous assessment requires outcome- and impact-level data that typically becomes available only years later.

#### Cost-Effectiveness Metrics

Common comparative metrics include:

$$CostPerJob=\frac{TotalSubsidy}{JobsCreated_{net}}$$

[Unverified] Cost-per-job figures are frequently cited in policy debates but are highly sensitive to methodology choices — whether "jobs created" includes indirect/induced employment via multiplier effects, whether it nets out jobs that would have existed anyway (the additionality problem above), and the time horizon over which job counts are measured. Cross-program comparisons using this metric should be treated cautiously given inconsistent underlying methodologies across studies and countries.

#### Fiscal Multiplier and Spillover Analysis

Economic impact assessments often attempt to estimate broader **fiscal multipliers** (total economic activity generated per dollar of public investment) and **knowledge spillovers** (productivity or innovation benefits accruing to firms and workers beyond direct subsidy recipients, e.g., through supplier network development or worker mobility). These are among the most contested areas of industrial policy economics, since spillover magnitude is difficult to isolate empirically and estimates vary substantially across studies and sectors.

### Categories of Unintended Consequences

#### 1. Overcapacity and Market Distortion

As discussed regarding the global subsidy race, simultaneous multi-jurisdiction subsidization of the same sector (solar panels, EV batteries, and potentially semiconductors) risks aggregate capacity exceeding demand growth, leading to price collapses and capacity underutilization — an outcome that can undermine the long-run commercial viability of subsidized facilities even where the initial investment and job-creation goals were nominally achieved.

#### 2. Crowding Out and Resource Competition

Large-scale strategic-sector subsidies can compete for scarce inputs — skilled labor (engineers, construction trades), grid capacity, water resources (semiconductor fabrication is water-intensive), and even land — potentially crowding out other economic activity in the same region or driving up input costs for non-subsidized firms in adjacent sectors.

#### 3. Rent-Seeking and Firm Behavior Distortion

Subsidy programs can incentivize firms to optimize for **subsidy eligibility criteria** rather than genuine commercial or technological objectives — for example, structuring investment announcements, domestic content ratios, or facility siting decisions primarily to maximize available incentives rather than to reflect underlying commercial logic. [Inference] This is a well-documented risk category in public finance literature on investment incentives generally, though quantifying its prevalence for any specific current program (e.g., CHIPS Act awards) requires firm-level data disclosure that is not always publicly available.

#### 4. Sunk-Cost Political Lock-In

Once large sums are politically committed to a strategic sector, there can be pressure to continue supporting the sector even as evidence of underperformance emerges, since acknowledging program failure carries political costs distinct from the underlying economic merits of continuation — a dynamic recognized broadly in public choice theory as relevant to large discretionary spending programs.

#### 5. Trade Retaliation and Diplomatic Friction

As covered in relation to WTO subsidy enforcement, large industrial subsidies frequently provoke countervailing duty investigations or diplomatic friction from trading partners, potentially triggering retaliatory measures that impose costs on unrelated export sectors — an economy-wide cost not captured in narrow sector-specific cost-benefit analysis.

#### 6. Talent and Capital Reallocation Effects

Subsidized mega-projects can draw skilled labor and capital away from other productive uses within the same economy (a general-equilibrium effect distinct from simple crowding-out at the local level), meaning the net national benefit may be smaller than the gross sector-specific benefit if the reallocated resources would have been similarly or more productively employed elsewhere absent the subsidy.

#### 7. Ecosystem Incompleteness ("White Elephant" Risk)

As discussed regarding the limits of full supply chain relocation, subsidizing a single node of a supply chain (e.g., final assembly or a fab) without corresponding investment in the surrounding supplier ecosystem, specialized workforce, and logistics infrastructure can produce facilities that underperform relative to projections due to persistent reliance on imported inputs or components — sometimes termed "white elephant" risk in development economics literature.

### Illustrative Comparative Assessment Table

| Program | Stated Goal | Documented Strength | Documented/Cited Concern |
| --- | --- | --- | --- |
| US CHIPS Act | Reshoring advanced semiconductor fabrication | Substantial disbursed grants/loans; major fab announcements (Intel, TSMC Arizona, Samsung) | [Unverified] Construction delays and cost overruns reported at multiple flagship projects; labor availability constraints cited in industry reporting |
| EU Chips Act | Double EU global chip market share to 20% by 2030 | Established competence centres across all Member States; pilot line infrastructure | Court of Auditors found only ~€4.5B of the ~€86B envelope directly Commission-managed; state aid approved (~€13.75B) well below original ambition |
| Made in China 2025 | Technological self-sufficiency across 10 sectors | Strong outcomes in EVs, batteries, high-speed rail | Overcapacity in EVs/solar/steel triggering trade disputes; limited progress in leading-edge semiconductors post-export-controls |

### Best-Practice Elements Cited in Evaluation Literature

- **Sunset clauses and periodic review requirements**: building automatic reassessment points into subsidy program design to counter sunk-cost political lock-in.
- **Conditionality tied to outcomes rather than inputs**: structuring subsidy disbursement in tranches conditional on verified milestones (hiring targets met, production ramp achieved) rather than releasing full funding on announcement.
- **Transparency and firm-level disclosure requirements**: enabling independent researcher access to disaggregated outcome data, which several analysts have identified as a persistent gap limiting rigorous ex-post evaluation of major programs.
- **Complementary ecosystem investment**: pairing headline capital subsidies with workforce training, supplier development, and infrastructure investment to mitigate ecosystem-incompleteness risk.

### Key Points

- Rigorous industrial policy evaluation is constrained by the counterfactual/additionality problem and a structural mismatch between political and economic time horizons
- Cost-per-job and multiplier metrics are commonly cited but highly sensitive to methodological assumptions, warranting caution in cross-program comparison
- Recurring unintended consequences include overcapacity, resource crowding-out, rent-seeking behavior, political lock-in, trade retaliation, and ecosystem-incompleteness ("white elephant") risk
- Comparative assessment across the US CHIPS Act, EU Chips Act, and Made in China 2025 reveals highly sector- and program-specific outcomes rather than uniform success or failure
- Evaluation best practices emphasize outcome-conditional disbursement, sunset/review clauses, and transparency to enable independent assessment

### Related Topics

- Additionality and counterfactual estimation methods in public program evaluation
- Global overcapacity dynamics in solar, EV batteries, and potential semiconductor risk
- Public choice theory and sunk-cost political dynamics in large discretionary spending programs
- Semiconductor fab construction timelines, cost overruns, and skilled labor constraints
- Comparative case study: US CHIPS Act flagship project progress tracking (Intel, TSMC Arizona, Samsung)
- Development economics literature on "white elephant" infrastructure and industrial projects