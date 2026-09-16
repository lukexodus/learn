## Supplier Selection and Evaluation Criteria

### Definition and Scope

Supplier selection and evaluation is the structured process of assessing potential and existing suppliers against defined criteria to determine their fitness to fulfill an organization's procurement requirements, both at the point of initial qualification and on an ongoing basis throughout the relationship.

**Key Points**

- Selection (pre-contract) and evaluation (post-contract, ongoing) are related but distinct activities — selection determines who to award business to; evaluation monitors whether that decision continues to be justified
- Criteria weighting should vary by category (using a Kraljic-style segmentation) — a strategic supplier warrants deeper, broader evaluation than a non-critical commodity supplier
- Effective evaluation combines objective, quantifiable metrics with structured qualitative assessment to avoid both over-reliance on price and unstructured subjective judgment

---

### Core Evaluation Criteria Categories

#### 1. Cost/Price

- Unit price and total cost of ownership (TCO), not price alone
- Payment terms and their working capital impact
- Price stability/volatility history and hedging mechanisms for commodity inputs
- Cost transparency (willingness to open-book cost structures for strategic categories)

#### 2. Quality

- Historical defect rates (PPM — parts per million — or DPMO — defects per million opportunities)
- Certifications (ISO 9001, industry-specific standards such as IATF 16949 for automotive or AS9100 for aerospace)
- Quality management system maturity and process control capability ($C_{pk}$ for process capability)
- Corrective action responsiveness (CAPA — Corrective and Preventive Action — cycle time)

$$C_{pk} = \min\left(\frac{USL - \mu}{3\sigma}, \frac{\mu - LSL}{3\sigma}\right)$$

where $USL$/$LSL$ are upper/lower specification limits, $\mu$ is the process mean, and $\sigma$ is the process standard deviation — used to assess a supplier's process capability during technical qualification.

#### 3. Delivery Performance

- On-time delivery (OTD) percentage
- Order fill rate / order completeness
- Lead time and lead time variability/consistency
- Flexibility to handle demand surges or expedited requests

#### 4. Financial Stability

- Credit ratings and financial statement analysis (liquidity, leverage, profitability ratios)
- Revenue concentration risk (is the supplier over-dependent on one or few customers, or vice versa — is the buyer a small fraction of the supplier's revenue, reducing priority?)
- Bankruptcy/going-concern risk indicators

#### 5. Capacity and Scalability

- Current utilization rate and available headroom
- Ability to scale production for growth or seasonal peaks
- Redundancy across multiple production sites (single-site risk)

#### 6. Technical Capability and Innovation

- Engineering/R&D capability relevant to the category
- Track record of collaborative product/process improvement
- Technology roadmap alignment with buyer's future needs

#### 7. Risk and Compliance

- Geopolitical and geographic concentration risk
- Regulatory compliance (labor law, environmental, industry-specific regulation)
- Cybersecurity posture (increasingly critical given supply chain cyberattack vectors)
- Business continuity/disaster recovery planning

#### 8. Sustainability and Social Responsibility (ESG)

- Environmental footprint and reduction commitments
- Labor practices and human rights due diligence (especially in extended, multi-tier supply chains)
- Diversity, equity, and inclusion sourcing goals (e.g., supplier diversity programs)

---

### Weighted Scoring Model

The most common formal selection method assigns weights to each criterion category based on strategic priority, then scores each candidate supplier:

$$\text{Total Score}_j = \sum_{i=1}^{n} w_i \cdot s_{ij}$$

where $w_i$ is the weight for criterion $i$ (with $\sum w_i = 1$) and $s_{ij}$ is supplier $j$'s score on criterion $i$ (typically on a 1–5 or 1–10 scale).

**Example**

A manufacturer evaluating three candidate suppliers for a strategic (Kraljic "strategic item") component uses the following weighted model:

| Criterion | Weight | Supplier A | Supplier B | Supplier C |
| --- | --- | --- | --- | --- |
| Quality (score /5) | 0.30 | 4.5 | 3.5 | 4.0 |
| Cost/TCO (score /5) | 0.25 | 3.0 | 4.5 | 3.5 |
| Delivery reliability (score /5) | 0.20 | 4.0 | 3.5 | 4.5 |
| Financial stability (score /5) | 0.15 | 4.0 | 2.5 | 4.0 |
| Innovation/tech capability (score /5) | 0.10 | 5.0 | 3.0 | 3.5 |

$$\text{Score}_A = (0.30)(4.5) + (0.25)(3.0) + (0.20)(4.0) + (0.15)(4.0) + (0.10)(5.0) = 3.95$$



$$\text{Score}_B = (0.30)(3.5) + (0.25)(4.5) + (0.20)(3.5) + (0.15)(2.5) + (0.10)(3.0) = 3.575$$



$$\text{Score}_C = (0.30)(4.0) + (0.25)(3.5) + (0.20)(4.5) + (0.15)(4.0) + (0.10)(3.5) = 3.925$$

**Output**: Supplier A scores highest (3.95), narrowly ahead of Supplier C (3.925), with Supplier B trailing primarily due to weaker financial stability and quality scores despite the most competitive price — illustrating why price-only comparison would have misleadingly favored Supplier B.

---

### Supplier Selection Process Workflow

```mermaid
flowchart TD
    A[1. Define Requirements and Specifications] --> B[2. Identify Candidate Suppliers]
    B --> C[3. Pre-Qualification Screening<br/>financial, compliance, capability]
    C --> D[4. Issue RFI/RFP to Qualified Candidates]
    D --> E[5. Evaluate Proposals Against<br/>Weighted Criteria]
    E --> F[6. Conduct Site Visits/Audits<br/>for Strategic Categories]
    F --> G[7. Negotiate Terms with<br/>Finalist(s)]
    G --> H[8. Award Contract and Onboard]
    H --> I[9. Ongoing Performance Monitoring<br/>Scorecards]
    I -.periodic reassessment.-> C
```

---

### Ongoing Supplier Evaluation: Scorecards

Post-award, suppliers are typically monitored via a recurring (often quarterly) **supplier scorecard** combining the same criteria categories into a tracked performance trend rather than a one-time gate:

| Metric | Target | Measurement Frequency |
| --- | --- | --- |
| On-Time Delivery % | ≥ 95% | Monthly |
| Quality (PPM defect rate) | ≤ 500 PPM | Monthly |
| Responsiveness to corrective action requests | ≤ 10 business days | Per incident |
| Cost competitiveness vs. market | Benchmarked annually | Annual |
| Compliance audit results | Pass/no critical findings | Annual or per-contract-term |

Scorecard results typically feed into tiered supplier classifications (e.g., Preferred, Approved, Conditional, Disqualified), which in turn affect future business allocation and whether a supplier is invited to bid on new opportunities.

```mermaid
flowchart LR
    Preferred[Preferred Supplier] -->|Performance decline| Approved[Approved Supplier]
    Approved -->|Performance decline| Conditional[Conditional - Improvement Plan Required]
    Conditional -->|No improvement| Disqualified[Disqualified]
    Conditional -->|Improvement achieved| Approved
    Approved -->|Sustained excellence| Preferred
```

---

### Site Audits and Technical Qualification

For strategic or high-risk categories, desk-based evaluation is typically supplemented with on-site audits assessing:

- Physical facility capacity, condition, and equipment maintenance
- Quality management system implementation (not just certification on paper)
- Working conditions and labor compliance (especially relevant for global/multi-tier supply chains)
- Process control documentation and traceability systems

**Common Pitfalls**

- Over-weighting price relative to total cost of ownership, quality, and risk factors, leading to hidden downstream costs
- Relying solely on supplier self-reported data without independent verification (audits, reference checks, third-party certifications)
- Applying the same rigorous, resource-intensive evaluation process uniformly across all spend categories rather than scaling rigor to strategic importance (Kraljic segmentation)
- Treating selection as a one-time gate rather than maintaining ongoing evaluation, allowing supplier performance to degrade undetected between major sourcing events
- Insufficient supplier financial due diligence, resulting in exposure to supply disruption if a supplier becomes financially distressed
- Failing to involve cross-functional stakeholders (quality, engineering, finance) in criteria weighting, producing a model that reflects only procurement's priorities

[Inference — specific numeric scorecard targets (e.g., 95% OTD, 500 PPM) shown above are illustrative benchmarks commonly referenced in operations practice; actual targets vary substantially by industry, product complexity, and criticality, and should be set based on the specific organization's requirements and historical baseline]

---

**Related Topics**

- Kraljic Portfolio Matrix and category-differentiated sourcing strategy
- Total Cost of Ownership (TCO) modeling
- Supplier Relationship Management (SRM) programs
- Statistical Process Control (SPC) and process capability ($C_{pk}$, $C_p$)
- Supplier risk management and business continuity planning
- ESG and sustainable procurement practices
- RFx (RFI/RFP/RFQ) process design
- Quality management systems and certifications (ISO 9001, IATF 16949)