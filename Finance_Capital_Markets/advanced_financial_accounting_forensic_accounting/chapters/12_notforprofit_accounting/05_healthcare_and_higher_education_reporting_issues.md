## Healthcare and Higher Education Reporting Issues


### Overview

Healthcare organizations and higher education institutions represent two specialized industry subsectors within not-for-profit (NFP) accounting, each governed by the general FASB not-for-profit framework (ASC 958) but layered with industry-specific guidance addressing their unique revenue streams, cost structures, and reporting conventions. Both sectors also frequently include **for-profit** and **governmental** entities operating side by side with NFP counterparts, so practitioners must first identify which overall reporting framework (FASB NFP, FASB business enterprise, or GASB) applies before layering on industry-specific guidance.

### Healthcare Organization Reporting (ASC 954)

#### Performance Indicator Requirement

A defining feature of NFP healthcare entity financial statements (distinct from general NFP reporting) is the required presentation of a **performance indicator** — a subtotal within the statement of operations analogous to "income from operations" in a commercial enterprise, intended to allow comparability across NFP, for-profit, and governmental healthcare providers, which otherwise use different overall statement formats.

**Structure**

$$\text{Performance Indicator} = \text{Operating Revenues} - \text{Operating Expenses} \pm \text{Certain Specified Items}$$

Items required to be presented **outside** the performance indicator (i.e., below the subtotal, even though they affect the change in net assets without donor restrictions) include:

- Equity transfers involving related entities and discontinued operations.
- Receipt of contributed capital assets (though this treatment has been an area of some diversity in practice).
- Certain unrealized gains and losses on investments not held for trading purposes (specifics vary by classification).

**Example — Simplified Healthcare Statement of Operations**

|  | Amount |
| --- | --- |
| Net patient service revenue | 45,000,000 |
| Other operating revenue | 2,500,000 |
| **Total operating revenues** | **47,500,000** |
| Operating expenses | (44,200,000) |
| **Operating income** | **3,300,000** |
| Investment income (non-operating) | 600,000 |
| **Performance indicator (excess of revenues over expenses)** | **3,900,000** |
| Net assets released from restriction for capital acquisitions | 250,000 |
| Unrealized gains on investments not classified as trading | 180,000 |
| **Increase in net assets without donor restrictions** | **4,330,000** |

**Key Point**: The performance indicator itself must be displayed with a caption clearly indicating that it is a performance indicator (e.g., "excess of revenues over expenses," "operating income"); some items flow through the statement below this line but still affect the total change in net assets without donor restrictions for the period.

#### Net Patient Service Revenue

Healthcare providers report **net patient service revenue** — gross charges based on established rates, reduced by contractual adjustments (differences between gross charges and amounts actually reimbursable under third-party payer contracts, such as Medicare, Medicaid, and commercial insurers) and implicit price concessions (amounts not expected to be collected, often from uninsured or self-pay patients, treated as an implicit price concession under ASC 606 rather than bad debt expense in most cases following the healthcare revenue recognition guidance updates).

**Example**

A hospital's gross charges for a patient's care total $50,000. Based on the payer contract, the expected reimbursable (contractual) rate is $18,000; based on historical collection patterns, the hospital estimates an additional $1,200 implicit price concession related to the patient's self-pay portion.

$$\text{Contractual Adjustment} = 50{,}000 - 18{,}000 = 32{,}000$$



$$\text{Net Patient Service Revenue} = 18{,}000 - 1{,}200 = 16{,}800$$

| Account | Debit | Credit |
| --- | --- | --- |
| Accounts Receivable | 18,000 |  |
| Net Patient Service Revenue |  | 18,000 |
| Net Patient Service Revenue (Implicit Price Concession) | 1,200 |  |
| Allowance for Implicit Price Concessions |  | 1,200 |

**Distinction from Bad Debt Expense**: Under current guidance (aligned with ASC 606), amounts a provider never expected to collect from the outset (based on the patient's financial circumstances, assessed at the point of service) are treated as an **implicit price concession** reducing revenue, not as bad debt expense. Bad debt expense is reserved for amounts the provider *did* expect to collect (a legitimate receivable existed) but that subsequently prove uncollectible due to the patient's unanticipated inability or unwillingness to pay — a narrower category under current guidance than in prior healthcare accounting practice.

#### Charity Care

Services provided to patients who meet the organization's charity care policy criteria (typically based on income relative to federal poverty guidelines) are **never recognized as revenue** because the provider never intended to bill and collect for that care from the outset — charity care is fundamentally different from a price concession or bad debt, since no expectation of payment exists at all. Instead, charity care is disclosed in the notes, typically including the level of charity care provided measured at cost (or another reasonable method) and, if used, the ratio of cost to charges.

**Example**

A hospital provides $300,000 of services (at established gross charge rates) to patients qualifying under its charity care policy, with an estimated cost of $140,000 (based on a cost-to-charge ratio).

No revenue is recognized for the $300,000 in charges. The note disclosure would present the level of charity care provided, typically at estimated cost ($140,000), along with the method used to estimate that cost, rather than including any amount in the statement of operations.

#### Malpractice and Self-Insurance Considerations

Healthcare entities often carry significant contingent liabilities for professional/general liability claims, requiring actuarially determined loss reserves for both reported claims and incurred-but-not-reported (IBNR) claims, following general loss contingency recognition principles (ASC 450) layered with healthcare-specific actuarial practice. [Inference] The specific actuarial methodologies and discounting conventions for malpractice reserves can vary by organization and actuarial firm practice; organizations typically engage qualified actuaries for these estimates rather than applying a single standardized formula.

### Higher Education Reporting Issues

Colleges and universities may be organized as NFP entities (following FASB ASC 958), governmental entities (following GASB, common for public/state universities), or for-profit entities (following general FASB business guidance) — the applicable framework depends on the institution's governmental status, not merely its educational mission.

#### Tuition and Fee Revenue Recognition

Tuition and fees are generally **exchange transactions** (the student receives commensurate educational services), recognized under ASC 606 as the institution satisfies its performance obligation — typically ratably over the academic term as instruction is delivered, rather than at the point of billing or cash receipt.

**Example**

A university bills $4,000,000 in tuition for a semester running September through December (4 months), collected in advance in August.

Upon initial billing/receipt:

| Account | Debit | Credit |
| --- | --- | --- |
| Cash | 4,000,000 |  |
| Deferred Revenue (or Contract Liability) |  | 4,000,000 |

As the semester progresses, revenue is recognized ratably (e.g., $1,000,000/month as instruction is delivered):

| Account | Debit | Credit |
| --- | --- | --- |
| Deferred Revenue | 1,000,000 |  |
| Tuition Revenue |  | 1,000,000 |

#### Scholarship Allowances and Discounts

Institutional financial aid (scholarships funded by the institution's own unrestricted resources) is generally presented as a **reduction of tuition revenue** (a contra-revenue "discount," reported net) rather than as a separate scholarship expense, when the aid does not involve an actual disbursement of cash to or on behalf of the student for services rendered by the student (i.e., not a payment for services, which would instead be compensation expense).

**Example**

Gross tuition charges of $4,000,000 are reduced by $600,000 of institutionally funded scholarships awarded based on merit or need.

$$\text{Net Tuition Revenue} = 4{,}000{,}000 - 600{,}000 = 3{,}400{,}000$$

| Account | Debit | Credit |
| --- | --- | --- |
| Tuition Discounts and Allowances (contra-revenue) | 600,000 |  |
| Accounts Receivable — Student |  | 600,000 |

**Distinction**: If a scholarship instead represents payment for services the student performs for the institution (e.g., a graduate teaching assistantship where the "scholarship" is functionally compensation for teaching duties), the appropriate treatment may instead be salary/compensation expense rather than a tuition discount — this requires evaluating the substance of the arrangement, not merely its label.

#### Auxiliary Enterprises

Self-supporting activities that furnish goods/services to students, faculty, or staff for a fee directly related to (though not necessarily equal to) the cost of the goods/services — common examples include housing/residence halls, dining services, bookstores, and athletics. These are typically reported as exchange transaction revenue (not contributions), often disclosed as a distinct revenue category given their materiality and self-supporting nature at many institutions.

#### Government Grants and Contracts (Research Funding)

Higher education institutions, especially research universities, receive substantial government and foundation grant funding for sponsored research. As discussed under contribution recognition guidance, the determination of whether such funding constitutes a **contribution** (non-reciprocal, subject to conditional/unconditional analysis) or an **exchange transaction** (the government or foundation receives commensurate value, such as a specific deliverable/technology the resource provider will use) requires careful evaluation of the ASU 2018-08 indicators on a grant-by-grant basis, since research funding arrangements vary considerably in structure.

**Example**

A federal research grant of $800,000 requires the university to conduct a specific research study, with unspent funds returnable to the government if research milestones are not met (a measurable performance barrier with a right of return) — this is a **conditional contribution**, recognized only as milestones are achieved, recorded as a refundable advance until then.

### Diagram: Healthcare Performance Indicator Structure

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 240" font-family="Arial, sans-serif">
<text x="320" y="24" font-size="16" font-weight="bold" text-anchor="middle">Healthcare Statement of Operations Structure (svg_diagram)</text>
<rect x="40" y="45" width="560" height="40" fill="#dbeafe" stroke="#1e40af" />
<text x="320" y="70" font-size="12" text-anchor="middle">Operating Revenues (Net Patient Service Revenue + Other) − Operating Expenses</text>
<text x="320" y="102" font-size="16" text-anchor="middle">↓ equals</text>
<rect x="150" y="115" width="340" height="40" fill="#fef3c7" stroke="#b45309" />
<text x="320" y="140" font-size="12" font-weight="bold" text-anchor="middle">Performance Indicator (mandatory subtotal)</text>
<text x="320" y="172" font-size="16" text-anchor="middle">+ items required to be reported below the indicator</text>
<rect x="40" y="185" width="560" height="40" fill="#dcfce7" stroke="#15803d" />
<text x="320" y="210" font-size="12" text-anchor="middle">Total Increase in Net Assets Without Donor Restrictions</text>
</svg>

### Common Pitfalls (Exam Focus)

- Treating charity care the same as a bad debt or implicit price concession — charity care is never recognized as revenue at all, since no expectation of collection ever existed, while bad debt/price concessions involve amounts that were or could reasonably have been expected to be collected.
- Reporting the performance indicator without clearly labeling it as such, or improperly including items (like certain unrealized gains or equity transfers) that GASB/FASB healthcare guidance requires to appear below the indicator.
- Recognizing tuition revenue entirely at the point of billing rather than ratably as instructional services are delivered over the academic term.
- Reporting institutional scholarships as an expense rather than as a contra-revenue (discount) against tuition, when the aid does not represent compensation for services performed.
- Defaulting to classifying all government research grants as exchange transactions (or all as contributions) without applying the ASU 2018-08 commensurate-value and conditional/unconditional analysis on a grant-specific basis.
- Applying FASB NFP guidance to a public state university that is actually a governmental entity subject to GASB — the applicable framework depends on governmental status, not educational mission alone.

**Related Topics**

- Contribution recognition and conditional promises to give
- Statement of activities and functional expense reporting
- Net asset classification with and without donor restrictions
- Revenue recognition under ASC 606 for exchange transactions
- Government-wide financial statements (for public higher education institutions under GASB)
- Endowments and split-interest agreements