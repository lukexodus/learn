## Social Auditing and Compliance Review


### Definition and Purpose

Social auditing and compliance review is the structured, systematic process of assessing whether a project's actual social performance and management practices conform to a defined set of standards — internal commitments, national law, lender/funder requirements, or voluntary certification schemes. Within Monitoring, Evaluation, and Adaptive Management (MEAM), it functions as a formalized, standard-referenced evaluation layer, distinct from routine outcome monitoring in that its central question is not primarily "did outcomes improve?" but "did the project do what it committed to do, in the way it committed to do it, and does that match the applicable standard?"

Compliance review often overlaps substantially with independent and third-party verification in method (document review, field checks, interviews) but is distinguished by its explicit reference to a defined standard or set of requirements against which performance is being judged, generating a compliance determination (compliant, partially compliant, non-compliant) rather than only a data-accuracy check.

### Social Audit vs. Compliance Review vs. Verification: Distinguishing the Terms

**Key Points**

| Term | Primary Question | Reference Point | Typical Output |
| --- | --- | --- | --- |
| Social audit | How well is the project performing against its social commitments and stakeholder expectations? | Project's own commitments, stakeholder standards, sometimes participatory criteria | Findings report, often with community engagement in the process itself |
| Compliance review | Does the project meet a specific defined standard or requirement? | External standard: law, lender policy (e.g., IFC Performance Standards, World Bank ESF), certification criteria | Compliance determination (compliant/non-compliant/conditions) |
| Third-party verification | Is the reported data and process accurate and credible? | The project's own reported data/claims | Confirmation, discrepancy findings, corrective recommendations |

[Inference] These terms are used inconsistently across institutions and sectors — some frameworks use "social audit" and "compliance review" interchangeably, while others draw sharper distinctions; the table above reflects a synthesized practical distinction rather than a single universally adopted taxonomy, so practitioners should confirm the specific terminology and scope expected by their applicable financier or certification scheme.

### Common Standards and Frameworks Referenced in Compliance Review

- **Lender/financier safeguard policies**: e.g., IFC Performance Standards, World Bank Environmental and Social Framework (ESF), regional development bank equivalents — typically covering labor, resettlement, indigenous peoples, community health and safety, and cultural heritage.
- **National law and regulation**: Labor codes, land acquisition and resettlement law, environmental and social impact assessment regulations, occupational health and safety law.
- **Voluntary certification schemes**: Sector-specific standards (e.g., in agriculture, forestry, or extractives) that include defined social criteria audited by accredited certification bodies.
- **International human rights and labor standards**: ILO core labor standards, UN Guiding Principles on Business and Human Rights, used as reference frameworks even where not directly legally binding on the project.
- **Internal corporate policy commitments**: Company-specific social performance standards, sometimes exceeding minimum legal or lender requirements, against which internal or external audits assess conformance.

### Compliance Review Process

```mermaid
flowchart TD
    A[Identify applicable standard(s): law, lender policy, certification, internal commitment] --> B[Develop audit protocol / compliance checklist mapped to standard requirements]
    B --> C[Document review: policies, procedures, prior monitoring and verification reports]
    C --> D[Field assessment: site visits, interviews, records sampling]
    D --> E[Score/rate each requirement: compliant, partially compliant, non-compliant, not applicable]
    E --> F{Non-compliance findings identified?}
    F -- No --> G[Issue compliance confirmation report]
    F -- Yes --> H[Classify severity: minor, major, critical non-conformance]
    H --> I[Develop corrective action plan with defined timeline]
    I --> J[Track corrective action implementation]
    J --> K[Follow-up/closure audit to confirm resolution]
    K --> L{Resolved?}
    L -- Yes --> G
    L -- No --> H
```

### Non-Conformance Classification

Most compliance review protocols use a tiered severity classification to guide the urgency and consequence of a finding:

| Severity | Definition | Typical Consequence |
| --- | --- | --- |
| Minor non-conformance | Isolated gap in documentation or process that does not indicate systemic failure or direct harm | Corrective action plan with standard timeline (e.g., 30–90 days) |
| Major non-conformance | Systemic gap or a finding indicating a pattern of non-compliance across sites or time | Time-bound corrective action plan, closer follow-up monitoring, possible reporting to oversight body |
| Critical non-conformance | Finding indicating serious harm, imminent risk to life/safety, or fundamental rights violation (e.g., evidence of forced labor, child labor, unaddressed SEA/SH) | Immediate mandatory action, often including work stoppage on the affected activity, mandatory disclosure to funders/regulators, and potentially independent investigation |

[Inference] The specific thresholds distinguishing minor, major, and critical findings are protocol-specific rather than universally standardized; different certification schemes and lender frameworks define these tiers with varying precision, and some critical-category triggers (e.g., child labor, forced labor, credible SEA/SH allegations) are treated as automatic "zero-tolerance" findings requiring immediate escalation regardless of the broader audit's overall compliance rating.

### Audit Methodology Components

**Document and record review**: Policies, procedures, training records, consultation logs, compensation records, grievance logs (see grievance data tracking), and prior monitoring/verification reports, checked for both existence and actual implementation evidence (a policy existing on paper is not evidence it is followed in practice).

**Site observation**: Direct observation of working conditions, resettlement site conditions, community facility functionality, and safety practices, since some compliance dimensions (e.g., actual PPE use, actual grievance box accessibility) can only be confirmed through physical presence rather than document review alone.

**Worker and community interviews**: Structured or semi-structured interviews conducted, where possible, away from management presence and with confidentiality assurances, since interviewees' candor about sensitive compliance issues (labor conditions, harassment, coercion) is strongly affected by whether they believe their responses could reach the party being audited — directly paralleling the non-retaliation and confidentiality safeguards relevant to a project's own GRM.

**Sampling strategy**: Similar to verification practice, compliance audits typically combine risk-based sampling (prioritizing higher-risk sites, worker categories, or activities) with random sampling for broader assurance, since full-population review is rarely feasible within audit timeframes and budgets.

**Triangulation**: Cross-checking findings across document review, observation, and interviews — a compliance rating based on a single source (e.g., management-provided documentation alone) is considered substantially weaker evidence than one supported by convergent findings across multiple independent sources.

### Illustration: Compliance Rating Structure Across Standard Domains

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 880 460" font-family="Helvetica, Arial, sans-serif">
<text x="440" y="28" font-size="18" font-weight="bold" text-anchor="middle" fill="#1a1a1a">Compliance Review Domain Ratings (svg_diagram)</text>

<rect x="620" y="45" width="14" height="14" fill="#2f9e5c" />
<text x="640" y="57" font-size="10" fill="#333">Compliant</text>
<rect x="620" y="65" width="14" height="14" fill="#c98a1e" />
<text x="640" y="77" font-size="10" fill="#333">Partial/Minor</text>
<rect x="620" y="85" width="14" height="14" fill="#c94a4a" />
<text x="640" y="97" font-size="10" fill="#333">Major/Critical</text>


<text x="60" y="130" font-size="12" fill="#333">Labor conditions</text>

<rect x="220" y="115" width="500" height="22" fill="`#2f9e5c`" rx="4" />

<text x="60" y="170" font-size="12" fill="#333">Community consultation</text>

<rect x="220" y="155" width="380" height="22" fill="`#2f9e5c`" rx="4" />

<rect x="600" y="155" width="120" height="22" fill="`#c98a1e`" rx="4" />

<text x="60" y="210" font-size="12" fill="#333">Grievance mechanism</text>

<rect x="220" y="195" width="300" height="22" fill="`#2f9e5c`" rx="4" />

<rect x="520" y="195" width="200" height="22" fill="`#c98a1e`" rx="4" />

<text x="60" y="250" font-size="12" fill="#333">Resettlement compensation</text>

<rect x="220" y="235" width="200" height="22" fill="`#2f9e5c`" rx="4" />

<rect x="420" y="235" width="150" height="22" fill="`#c98a1e`" rx="4" />

<rect x="570" y="235" width="150" height="22" fill="`#c94a4a`" rx="4" />

<text x="60" y="290" font-size="12" fill="#333">Health and safety</text>

<rect x="220" y="275" width="480" height="22" fill="`#2f9e5c`" rx="4" />

<rect x="700" y="275" width="20" height="22" fill="`#c98a1e`" rx="4" />

<text x="60" y="330" font-size="12" fill="#333">Indigenous peoples/FPIC</text>

<rect x="220" y="315" width="250" height="22" fill="`#2f9e5c`" rx="4" />

<rect x="470" y="315" width="150" height="22" fill="`#c98a1e`" rx="4" />

<rect x="620" y="315" width="100" height="22" fill="`#c94a4a`" rx="4" />

<text x="440" y="400" font-size="12" font-weight="bold" text-anchor="middle" fill="`#8a2323`">Resettlement compensation and Indigenous peoples/FPIC domains show</text>

<text x="440" y="418" font-size="12" font-weight="bold" text-anchor="middle" fill="`#8a2323`">critical findings requiring immediate corrective action</text>

</svg>

### Example: Compliance Review of a Resettlement Component Against Lender Standards

**Example**

A compliance review is commissioned ahead of a scheduled loan disbursement milestone, assessing the resettlement component against the applicable lender's involuntary resettlement performance standard.

1. **Standard mapping**: The audit protocol is built directly from the specific clauses of the applicable performance standard (e.g., requirements on replacement-cost compensation, livelihood restoration planning, grievance access, vulnerable group identification).
2. **Document review**: The resettlement action plan, compensation records, and livelihood restoration monitoring data (see baseline-referenced outcome monitoring) are reviewed against the standard's specific requirements.
3. **Field assessment**: Auditors visit a risk-based sample of resettled households, prioritizing those flagged in prior grievance data as having disputed compensation amounts.
4. **Finding**: The audit identifies that a subset of vulnerable households (femaleheaded households) were not systematically identified through a formal vulnerability screening process as required by the standard, resulting in some of these households not receiving the additional support measures the standard specifies for vulnerable groups — classified as a **major non-conformance** given its systemic (not isolated) pattern.
5. **Corrective action plan**: The project commits to (a) retroactively screening all resettled households against the vulnerability criteria, (b) providing additional support to households newly identified as vulnerable, and (c) revising the intake process for any future resettlement phases to include mandatory vulnerability screening — with a defined 90-day timeline and a scheduled follow-up audit to confirm closure.
6. **Reporting**: The finding, corrective action plan, and follow-up audit results are documented in the compliance report shared with the lender as part of the disbursement condition, illustrating the direct link between compliance review findings and the adaptive management/corrective action process.

### Relationship to the Broader MEAM System

Social auditing and compliance review does not operate in isolation — it draws on and feeds into the other MEAM functions:

- It **draws on** grievance data, baseline-referenced monitoring results, and participatory monitoring findings as evidence inputs, rather than generating all its evidence independently from scratch.
- It **feeds into** adaptive management, since compliance findings — particularly major and critical non-conformances — are a primary trigger category for formal corrective action processes.
- It **reinforces** independent verification's credibility function, and the two are sometimes combined into a single audit engagement, though they remain conceptually distinct (verification checks data accuracy; compliance review checks standard conformance).

### Common Pitfalls

- **Checklist compliance without substantive assessment**: Confirming that a required document or policy exists without verifying it reflects actual practice on the ground, producing a false compliance rating.
- **Standard-shopping**: Selecting or interpreting the least stringent applicable standard when multiple overlapping standards (national law, lender policy, internal commitment) apply, rather than applying whichever is most protective as is generally expected practice.
- **Auditor scope narrowing under management influence**: Allowing the audited party to define or narrow the audit scope in ways that exclude known problem areas from review.
- **Severity under-classification**: Downgrading findings that meet major or critical non-conformance criteria to "minor" to avoid triggering mandatory escalation or disclosure requirements.
- **Corrective action without follow-up verification**: Accepting a corrective action plan as sufficient without a scheduled follow-up audit to confirm the corrective action was actually implemented and effective, rather than merely documented.
- **Treating compliance as a one-time gate**: Conducting compliance review only at fixed milestones (e.g., disbursement triggers) rather than as a recurring practice, missing compliance drift that occurs between scheduled reviews.

### Related Topics

- Independent and third-party verification
- Adaptive management and course correction
- Non-retaliation and confidentiality safeguards
- Grievance data tracking, analysis, and reporting
- Vulnerable group identification and differentiated support planning
- External compliance reporting under environmental and social frameworks
- Corrective action governance and funder disclosure requirements