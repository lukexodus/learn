## Hospital Cost Structures and Economies of Scale


### Overview

Hospital cost analysis applies standard production and cost theory to a setting with distinctive complications: multi-product output (many service lines produced jointly), high fixed capital costs, regulatory constraints on capacity (e.g., certificate-of-need laws), and third-party payment systems that partially insulate hospitals from direct consumer price sensitivity. Understanding hospital cost structure — the relationship between output volume/mix and total cost — is foundational to hospital payment policy (prospective payment, DRG-based reimbursement), merger and antitrust analysis, and capacity planning. Central to this topic are the concepts of economies of scale (cost advantages from size), economies of scope (cost advantages from producing multiple services jointly), and the minimum efficient scale at which a hospital operates most cost-effectively.

### Key Points: Hospital Cost Function Fundamentals

**1. The Hospital as a Multi-Product Firm**

Unlike a single-product firm in standard cost theory, a hospital simultaneously produces many distinct outputs — inpatient surgical cases, emergency visits, obstetric deliveries, diagnostic imaging, outpatient clinics — that share common inputs (buildings, administrative staff, some equipment, on-call physician coverage). This requires a **multi-product cost function**:

$$TC = C(Q_1, Q_2, \dots, Q_n, w)$$

where $Q_i$ represents the volume of service line $i$ and $w$ represents input prices (wages, capital costs). This framework is necessary because single-product cost curves cannot capture cost interactions across service lines.

**2. Fixed versus Variable Costs in Hospital Production**

Hospital costs are frequently decomposed into:

- **Fixed costs**: Building depreciation, licensed bed capacity, standby emergency department staffing, certain administrative overhead — costs that do not vary with patient volume in the short run
- **Semi-fixed costs**: Nursing staffing, which is adjusted in discrete steps (staffing ratios, unit closures) rather than continuously with volume
- **Variable costs**: Pharmaceuticals, disposable supplies, and costs directly tied to each additional patient/procedure

The high proportion of fixed and semi-fixed costs in hospital cost structure is a key driver of the economies-of-scale and capacity-utilization dynamics discussed below.

**3. Short-Run versus Long-Run Cost Curves**

Standard cost theory distinctions apply directly:

- **Short-run average cost (SRAC)**: With fixed bed capacity and core staffing, average cost per case typically declines as volume rises toward capacity (fixed costs spread over more cases), then may rise sharply as the facility approaches capacity constraints (overtime staffing, overflow, quality strain).
- **Long-run average cost (LRAC)**: Represents the cost-minimizing scale choice when all inputs, including facility size, are variable — this is the curve relevant to economies-of-scale analysis and merger evaluation.

### Economies of Scale in Hospital Production

**4. Definition and Measurement**

Economies of scale exist when long-run average cost declines as hospital output increases, i.e., cost per case falls as a hospital treats more patients holding case mix and quality constant.

$$\text{Economies of Scale exist if} \quad \frac{\partial (TC/Q)}{\partial Q} < 0$$

Empirically, this is typically estimated via cost function regressions (e.g., translog cost functions) using cross-sectional hospital data, estimating a **scale elasticity** — the percentage change in total cost associated with a percentage change in output.

**5. Empirical Findings: A U-Shaped Cost Curve**

A substantial body of hospital cost function literature finds a **U-shaped long-run average cost curve**: economies of scale exist for small-to-medium hospitals (cost per case falls as volume rises, largely due to spreading fixed capital and specialized staff costs over more cases), reaching a **minimum efficient scale**, beyond which further volume growth may produce diseconomies of scale (cost per case rises again due to coordination complexity, administrative overhead growth, and bureaucratic costs in very large institutions). [Inference] The precise bed-count or volume threshold identified as minimum efficient scale varies substantially across studies, countries, time periods, and service line mix; specific numeric thresholds from any individual study should not be treated as a universal constant applicable to all hospital markets.

**6. Sources of Scale Economies**

- **Indivisibility of specialized equipment**: A single MRI scanner or cardiac catheterization lab has a large fixed cost that can be spread over more cases as volume rises, up to the equipment's capacity limit
- **Specialized staff utilization**: Larger hospitals can more efficiently utilize specialized subspecialist physicians and technicians whose skills would be underutilized in a low-volume setting
- **Statistical economies in capacity buffering**: Larger facilities can maintain a proportionally smaller "safety margin" of excess bed capacity for demand fluctuations (a statistical consequence of pooling variable, partially independent demand across more beds), improving average capacity utilization

**7. Volume-Outcome Relationship (Practice Makes Perfect / Selective Referral)**

A closely related and extensively studied empirical literature documents that hospitals performing higher volumes of certain complex procedures (e.g., cardiac surgery, pancreatic resection) tend to have better risk-adjusted outcomes (lower mortality, fewer complications) than low-volume hospitals performing the same procedure. Two competing (not mutually exclusive) explanations are debated:

- **"Practice makes perfect"**: Higher volume itself causally improves surgical team proficiency and institutional protocols
- **"Selective referral"**: Higher-quality hospitals and surgeons attract more referrals because of their pre-existing reputation for quality, meaning volume is a *consequence* of quality rather than its cause

[Inference] Disentangling these two causal directions is methodologically difficult, and the literature has not fully resolved the relative contribution of each mechanism; both are generally considered to contribute to the observed volume-outcome correlation, with the balance likely varying by procedure type.

### Economies of Scope

**8. Definition**

Economies of scope exist when it is cheaper to produce two or more service lines jointly within a single hospital than to produce them separately in specialized single-service facilities:

$$C(Q_1, Q_2) < C(Q_1, 0) + C(0, Q_2)$$

**9. Sources of Scope Economies in Hospitals**

- Shared diagnostic infrastructure (laboratory, imaging) used across multiple clinical service lines
- Shared emergency department and on-call physician coverage supporting multiple specialties
- Case-mix complementarities where treating patients with multiple comorbidities benefits from co-located specialty services (e.g., a cardiac patient with renal complications benefiting from on-site nephrology)

**10. The Diseconomy-of-Scope Counter-Case: Specialty Hospitals**

Physician-owned specialty hospitals (e.g., dedicated orthopedic or cardiac surgical hospitals) represent an empirical test of the scope-economies hypothesis: if broad general hospitals truly benefit from strong scope economies, focused specialty facilities should be at a cost disadvantage. Evidence on this question is mixed — some studies find specialty hospitals achieve lower costs per case for their focused procedures through standardization and reduced case-mix complexity (a "focused factory" effect), suggesting that at least for certain procedures, scope economies are smaller than scale/focus advantages, while general hospitals argue that specialty hospital cost advantages partly reflect patient selection (healthier, less complex patients) rather than true production efficiency. [Unverified] The net welfare effect of specialty hospital growth — weighing focused-factory efficiency gains against potential cream-skimming of profitable, low-complexity cases away from general hospitals — remains actively debated and is sensitive to the specific market and regulatory context studied.

### Illustration: Hospital Long-Run Average Cost Curve

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 320">
<text x="320" y="24" font-size="14" font-weight="bold" text-anchor="middle" fill="#222">Hospital Long-Run Average Cost Curve (svg_diagram)</text>
<line x1="70" y1="270" x2="600" y2="270" stroke="#333" stroke-width="1.5" />
<line x1="70" y1="270" x2="70" y2="50" stroke="#333" stroke-width="1.5" />
<text x="335" y="300" font-size="12" text-anchor="middle" fill="#333">Output (Q) - Patient Volume</text>
<text x="30" y="160" font-size="12" text-anchor="middle" fill="#333" transform="rotate(-90 30 160)">Average Cost per Case</text>
<path d="M 100 240 Q 220 90 340 100 Q 460 108 560 190" fill="none" stroke="#3b6fb6" stroke-width="2.5" />
<line x1="340" y1="270" x2="340" y2="100" stroke="#999" stroke-width="1" stroke-dasharray="4,3" />
<text x="340" y="290" font-size="10" text-anchor="middle" fill="#666">Minimum Efficient Scale</text>

<text x="180" y="150" font-size="11" fill="`#1a5e2a`">Economies of Scale</text>

<text x="180" y="164" font-size="10" fill="`#1a5e2a`">(AC falling)</text>

<text x="450" y="150" font-size="11" fill="`#8a3a1e`">Diseconomies of Scale</text>

<text x="450" y="164" font-size="10" fill="`#8a3a1e`">(AC rising)</text>

<circle cx="340" cy="100" r="4" fill="#c94f1e" />
</svg>

### Policy and Payment Implications

**11. Prospective Payment and Cost-Based Incentives**

Under prospective payment systems (e.g., Diagnosis-Related Group-based reimbursement, where hospitals receive a fixed payment per case regardless of actual cost incurred), hospitals bear the full marginal cost of inefficiency, creating a direct financial incentive to operate near the minimum efficient scale point and to pursue scope economies where genuine cost savings exist — in contrast to cost-plus reimbursement systems, which historically weakened this incentive.

**12. Hospital Merger Analysis**

Scale and scope economy evidence is directly relevant to antitrust evaluation of hospital mergers: merging parties often justify consolidation by citing projected cost savings from economies of scale/scope, while antitrust authorities weigh these claims against the risk of increased market concentration and pricing power. [Inference] Empirical merger retrospective studies have frequently found that realized cost savings from hospital mergers are smaller than projected pre-merger, while post-merger price increases are more consistently documented — but this finding should not be assumed to apply uniformly to every merger, as results vary by specific market circumstances.

### Practical Example

Consider a small rural hospital (60 beds) evaluating whether to merge with a larger regional hospital system (400 beds):

1. **Scale argument for merger**: The rural hospital's costly, low-volume specialized equipment (e.g., its MRI scanner, used only a few hours daily) could be consolidated or better utilized at higher volume post-merger, spreading fixed capital costs over more cases and moving the combined system closer to minimum efficient scale for that service line.
2. **Scope argument**: Shared administrative functions (billing, IT, procurement) across the merged system could reduce per-case overhead through economies of scope, since these functions have high fixed costs largely independent of the specific service line mix.
3. **Counter-consideration**: If the rural hospital's remaining inpatient services are subsequently reduced or consolidated into the larger system's main campus, local access for the rural population may decline even if system-wide average cost falls — illustrating the standard tension in rural hospital merger and closure policy between cost efficiency and geographic access.
4. **Antitrust concern**: If the merger substantially reduces the number of competing hospital systems in the regional market, negotiated prices with commercial insurers may rise post-merger even if some cost savings are realized, a pattern regulators specifically scrutinize during merger review.

### Related Topics

- Multi-product cost function estimation (translog cost functions)
- Volume-outcome relationship and selective referral literature
- Diagnosis-Related Group (DRG) based prospective payment systems
- Certificate-of-need laws and hospital capacity regulation
- Hospital merger retrospective studies and antitrust analysis
- Rural hospital closures and critical access hospital designation
- Physician-owned specialty hospitals and the "focused factory" model
- Capacity utilization and queuing theory in hospital bed management
- Nonprofit versus for-profit hospital cost behavior