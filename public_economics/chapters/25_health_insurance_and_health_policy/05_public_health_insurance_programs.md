## Public Health Insurance Programs


### Conceptual Overview

Public health insurance programs are government-financed and/or government-administered mechanisms for pooling health risk and subsidizing access to medical care, typically justified by the market-failure and equity rationales developed in the adverse selection and public-vs-private provision literature (asymmetric information precluding efficient private risk pooling for certain populations, externalities, and distributive concerns). This entry surveys the major structural archetypes and the leading real-world program designs used to illustrate them, with emphasis on the U.S. programs (Medicare, Medicaid, CHIP, ACA marketplace subsidies) as the canonical teaching cases in most public economics courses, supplemented by comparative international designs.

**Key Points**

- Public programs vary along the same financing/provision/regulation axes introduced in "Public versus Private Provision of Healthcare."
- Eligibility can be structured by age (categorical), income (means-tested), disability status, or universally (population-wide).
- Financing mechanisms include general taxation, dedicated payroll taxes, and premium contributions, often in combination.
- Program design must simultaneously address adverse selection, moral hazard, and target-population equity considerations.

---

### Typology of Public Health Insurance Program Design

| Design Dimension | Options | Example |
| --- | --- | --- |
| Eligibility basis | Age-based (categorical), income-based (means-tested), universal | Medicare (age/disability); Medicaid (income); NHS (universal) |
| Financing source | Payroll tax, general revenue, premiums, mixed | Medicare Part A (payroll tax); Medicaid (general revenue, federal-state match) |
| Administration | Direct government administration, contracted private plans, hybrid | Traditional Medicare (direct) vs. Medicare Advantage (private, capitated) |
| Cost-sharing structure | Premiums, deductibles, coinsurance, income-adjusted | Medicare Part B premiums income-adjusted (IRMAA) |
| Benefit scope | Comprehensive, targeted/limited | CHIP (pediatric-focused); Medicare (excludes long-term custodial care) |

---

### United States: Medicare

**Structure and financing:**

Medicare is a federal social insurance program primarily serving individuals aged 65+ and certain disabled individuals under 65, organized into distinct parts with distinct financing mechanisms:

- **Part A (Hospital Insurance)**: Covers inpatient hospital, skilled nursing facility, and hospice care. Financed primarily through a dedicated **payroll tax** (2.9% combined employer-employee rate under FICA, with an additional 0.9% Medicare surtax on high earners above statutory thresholds under the ACA). Structured as a social insurance model with intergenerational financing (current workers' payroll taxes fund current beneficiaries' claims, a pay-as-you-go structure rather than individual pre-funding).
- **Part B (Medical Insurance)**: Covers outpatient physician services, durable medical equipment, and some preventive services. Financed through a combination of **general revenue** (approximately 73-75% of costs) and **income-related monthly premiums** paid by beneficiaries (with higher-income beneficiaries paying higher premiums via Income-Related Monthly Adjustment Amounts, IRMAA) — an explicit progressivity mechanism within an otherwise near-universal program.
- **Part C (Medicare Advantage)**: An alternative to traditional fee-for-service Medicare in which beneficiaries enroll in private plans that receive a **risk-adjusted capitated payment** from the government to cover Part A and B benefits (and typically Part D). This is a direct real-world instance of the risk-adjustment mechanism discussed in the adverse selection entry, designed to neutralize private insurers' incentive to favor healthier enrollees.
- **Part D (Prescription Drug Coverage)**: Outpatient prescription drug coverage, delivered exclusively through private plans, financed through a mix of general revenue, beneficiary premiums, and (since the Inflation Reduction Act of 2022) manufacturer discounts and revised catastrophic-phase cost-sharing.

**The "donut hole" / coverage gap [structure subject to ongoing legislative revision]:** Historically, Part D contained a coverage gap in which beneficiaries faced a jump in cost-sharing responsibility after an initial coverage phase and before catastrophic coverage began. The Inflation Reduction Act of 2022 restructured Part D cost-sharing, including phasing out the traditional "donut hole" structure and introducing a $2,000 annual out-of-pocket cap (effective 2025) for Part D enrollees, along with allowing Medicare to negotiate prices for a defined set of high-expenditure drugs beginning with initial negotiated prices effective 2026. [Given the recency and legislative complexity of these provisions, treat specific dollar thresholds and phase-in dates as subject to verification against current CMS guidance, since implementation details have continued to be refined through rulemaking.]

**Managed care / risk adjustment mechanics (Medicare Advantage):**

$$\text{Capitated Payment}_i = \text{Base Rate} \times \text{Risk Score}_i$$

where the risk score is derived from the CMS Hierarchical Condition Category (HCC) model, using diagnosis codes and demographic factors to predict expected relative cost, directly operationalizing the risk-adjustment policy instrument discussed as a response to adverse selection.

**Documented empirical concern — Medicare Advantage favorable selection/upcoding:** A substantial empirical literature has found evidence that Medicare Advantage enrollees tend to be somewhat healthier than observably-similar traditional Medicare beneficiaries (favorable/advantageous selection into MA plans) and that MA plans have incentives to maximize documented diagnosis codes ("upcoding") to increase risk-adjusted payments, a distinct principal-agent problem arising from the risk-adjustment mechanism itself. [Inference: the magnitude of upcoding's net fiscal cost to Medicare is an actively debated empirical question, with estimates varying by study methodology and time period.]

---

### United States: Medicaid

**Structure and financing:**

Medicaid is a means-tested public insurance program jointly financed by federal and state governments, administered by states within federal minimum standards, primarily serving low-income individuals, pregnant women, children, elderly, and disabled individuals meeting state-specific income/asset eligibility thresholds.

**Federal Medical Assistance Percentage (FMAP):** The federal government reimburses a state-specific share of Medicaid expenditures, calculated via a formula inversely related to state per-capita income (poorer states receive a higher federal matching rate, ranging from a statutory floor of 50% up to a considerably higher percentage for the lowest-income states), an explicit fiscal-federalism mechanism embedding equalization across states with differing fiscal capacity.

$$\text{FMAP}_s = 1 - 0.45 \times \left(\frac{\text{State per capita income}_s}{\text{National per capita income}}\right)^2$$

(This is the statutory formula structure; the resulting FMAP is bounded between statutory floor and ceiling values set in federal law.)

**ACA Medicaid Expansion:** The Affordable Care Act (2010) provided for expansion of Medicaid eligibility to adults up to 138% of the Federal Poverty Level, with the federal government initially covering 100% of expansion costs, phasing down to a 90% permanent federal matching rate for the expansion population — a substantially more generous match than the traditional FMAP formula. The 2012 Supreme Court decision in *NFIB v. Sebelius* held that the federal government could not condition a state's *existing* Medicaid funding on accepting the expansion, effectively making expansion optional at state discretion — resulting in a "coverage gap" in non-expansion states for adults with incomes too high for traditional Medicaid eligibility but too low for ACA marketplace subsidy eligibility (which begins at 100% FPL). [This state-adoption landscape has continued to evolve since 2014 as individual states have adopted or debated expansion; verify current state adoption status against current KFF/CMS tracking if precise up-to-date state counts are needed.]

**Managed care in Medicaid:** The large majority of Medicaid enrollees nationally are enrolled in Medicaid managed care organizations (MCOs) receiving capitated payments from states, analogous in structure to Medicare Advantage, again embedding a risk-adjustment/capitation design responding to the same underlying selection and cost-control considerations.

---

### United States: CHIP (Children's Health Insurance Program)

Established in 1997, CHIP is a federal-state program targeting children in families with incomes modestly above Medicaid eligibility thresholds but below levels typically able to afford private coverage — a targeted "gap-filling" design addressing a specific population segment identified as falling between the means-tested and private-market coverage margins. Financed through an enhanced federal matching rate (higher than standard Medicaid FMAP) as an incentive for state participation, reflecting the political economy consideration that state fiscal capacity constraints could otherwise limit program uptake even where a federal equity rationale for coverage exists.

---

### United States: ACA Marketplace Subsidies

The Affordable Care Act established income-related premium tax credits for individuals purchasing private insurance through state or federal marketplaces (exchanges), structured as a sliding-scale subsidy capping the required premium contribution as a percentage of income, with the subsidy amount calculated as the difference between this capped contribution and the premium of a benchmark (second-lowest-cost Silver) plan.

$$\text{Subsidy} = \text{Benchmark Premium} - (\text{Applicable Percentage} \times \text{Household Income})$$

This is a direct real-world application of the "income-based subsidy" adverse-selection policy instrument discussed previously — designed to keep lower-income (often lower-risk-correlated, though not risk-targeted per se) individuals within the risk pool despite community-rated pricing. [Note: the specific applicable percentage schedule and subsidy cliff/enhancement provisions have been modified by subsequent legislation, including temporary enhancements under the American Rescue Plan Act (2021) and Inflation Reduction Act (2022); current subsidy generosity and expiration dates should be verified against current federal guidance given the legislative volatility of this specific provision.]

---

### Comparative International Public Health Insurance Models

#### United Kingdom — National Health Service (NHS)

Financed almost entirely through general taxation, with care provided predominantly by public sector employees and public hospital trusts — the paradigmatic Beveridge-model integration of public financing and public provision. Access is universal and (for most services) free at the point of use, with rationing occurring primarily through waiting lists and NICE (National Institute for Health and Care Excellence) cost-effectiveness-based coverage determinations rather than price.

#### Canada — Medicare (Canadian)

A single-payer, publicly-financed system (financed through general provincial/federal taxation) operating under the Canada Health Act's five principles (public administration, comprehensiveness, universality, portability, accessibility), but with care *delivered* predominantly by private (though largely not-for-profit) providers and physicians in private practice — the paradigmatic National Health Insurance model illustrating that single-payer financing does not require public provision.

#### Germany — Statutory Health Insurance (Gesetzliche Krankenversicherung, GKV)

The canonical Bismarck-model social health insurance system: mandatory membership in competing, nonprofit "sickness funds" (Krankenkassen), financed through income-related payroll contributions split between employer and employee, with a risk-adjustment mechanism (the Risikostrukturausgleich) transferring funds among sickness funds to neutralize risk-selection incentives — again a direct real-world instance of the risk-adjustment policy response to adverse selection, operating at the level of competing quasi-public insurers rather than a single payer.

#### Singapore — Medisave/Medishield/Medifund ("3M" System)

A distinctive hybrid model combining mandatory individual medical savings accounts (Medisave, funded through mandatory payroll contributions to personal accounts), catastrophic public insurance (MediShield Life), and a means-tested safety-net fund for those unable to afford care (Medifund) — designed explicitly to preserve individual cost-consciousness (addressing moral hazard directly through the savings-account mechanism, since spending draws down one's own account balance) while providing catastrophic risk pooling and a means-tested equity backstop. [Frequently cited as a case study in moral-hazard-conscious public system design, given its explicit theoretical grounding in consumer cost-sharing incentives.]

---

### Diagrammatic Summary: U.S. Public Program Eligibility Landscape

<svg viewBox="0 0 640 380" xmlns="http://www.w3.org/2000/svg" font-family="Helvetica, Arial, sans-serif">
<text x="320" y="24" text-anchor="middle" font-size="15" font-weight="bold">U.S. Public Coverage by Age and Income (svg_diagram)</text>
<line x1="90" y1="330" x2="600" y2="330" stroke="black" stroke-width="1.5"/>
<line x1="90" y1="330" x2="90" y2="50" stroke="black" stroke-width="1.5"/>
<text x="600" y="352" font-size="12" text-anchor="end">Age</text>
<text x="55" y="45" font-size="12">Income (% FPL)</text>
<!-- Medicaid block: low income, all ages -->
<rect x="90" y="260" x="90" width="510" height="70" fill="#2b6cb0" fill-opacity="0.35"/>
<text x="300" y="300" font-size="12" fill="#1a365d" text-anchor="middle">Medicaid (low income, all ages, expansion states to 138% FPL)</text>
<!-- CHIP block -->
<rect x="90" y="200" width="180" height="60" fill="#38a169" fill-opacity="0.35"/>
<text x="180" y="235" font-size="11" fill="#22543d" text-anchor="middle">CHIP (children,<br/>modest income)</text>
<text x="180" y="245" font-size="10" fill="#22543d" text-anchor="middle">above Medicaid threshold</text>
<!-- Marketplace subsidy zone -->
<rect x="90" y="120" width="510" height="80" fill="#d69e2e" fill-opacity="0.3"/>
<text x="300" y="165" font-size="12" fill="#7b341e" text-anchor="middle">ACA Marketplace subsidies (100%-400%+ FPL, non-elderly)</text>
<!-- Medicare block: age 65+, all incomes -->
<rect x="480" y="50" width="120" height="280" fill="#c05621" fill-opacity="0.3"/>
<text x="540" y="80" font-size="12" fill="#7b341e" text-anchor="middle">Medicare</text>
<text x="540" y="95" font-size="10" fill="#7b341e" text-anchor="middle">(age 65+ or disabled,</text>
<text x="540" y="108" font-size="10" fill="#7b341e" text-anchor="middle">all income levels)</text>

<text x="95" y="345" font-size="10">0</text>

<text x="470" y="345" font-size="10">65</text>

<text x="65" y="335" font-size="10">0%</text>

<text x="65" y="55" font-size="10">400%+</text>

</svg>

---

### Cost Containment Mechanisms Across Public Programs

| Program | Primary Cost-Control Lever |
| --- | --- |
| Medicare traditional FFS | Administered pricing (fee schedules, e.g., Physician Fee Schedule RVU-based rates), DRG-based hospital prospective payment |
| Medicare Advantage | Capitation shifting risk to private plans, subject to risk-adjustment |
| Medicaid | State-level FFS rate-setting (often below Medicare rates) and managed care capitation |
| NHS (UK) | Global budgets, NICE cost-effectiveness thresholds (QALY-based) for coverage decisions |
| Germany GKV | Negotiated collective contracts between sickness fund associations and provider associations |
| Singapore | Individual account cost-consciousness plus government subsidy tiers (means-tested "Subsidised" vs. "Private" ward classes) |

---

### Political Economy and Fiscal Sustainability Considerations

Public health insurance programs, particularly age-based entitlements like Medicare, face a distinct **long-run fiscal sustainability** analytical dimension not present in most private-market discussions: pay-as-you-go financing structures are directly exposed to demographic shifts (dependency ratio changes as populations age), and projected program cost growth relative to dedicated financing (e.g., Medicare Part A trust fund solvency projections published annually by the CMS Office of the Actuary/Medicare Trustees) is a recurring subject of public economics and fiscal policy analysis distinct from the insurance-design questions discussed above. [This is a rapidly-updating empirical area; current trust fund depletion-date projections should be verified against the most recent Medicare Trustees Report rather than relied upon from training-data-era figures.]

---

### Related Topics / Next Steps

- Adverse Selection in Health Insurance (risk-adjustment mechanisms as applied policy tool)
- Moral Hazard and Health Insurance Design (Singapore Medisave as applied case study)
- Public versus Private Provision of Healthcare (financing/provision matrix applied to these programs)
- Medicare Trust Fund Solvency and Long-Run Fiscal Projections
- Medicaid Managed Care: Capitation Rate-Setting and Risk Adjustment
- ACA Marketplace Design: Risk Corridors, Reinsurance, and Risk Adjustment (3Rs)
- Comparative Health System Financing: Bismarck vs. Beveridge vs. National Health Insurance Models
- Prescription Drug Pricing Policy: Medicare Negotiation under the Inflation Reduction Act
- Social Health Insurance Risk Equalization (Germany's Risikostrukturausgleich in Detail)
- Cost-Effectiveness Analysis and QALY-Based Coverage Determination (NICE Methodology)