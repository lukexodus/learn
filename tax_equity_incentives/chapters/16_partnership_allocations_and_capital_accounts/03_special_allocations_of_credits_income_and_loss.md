## Special Allocations of Credits, Income, and Loss


### Overview

Special Allocations of Credits, Income, and Loss refers to partnership agreement provisions that allocate specific tax items — most notably the ITC, PTC, depreciation, and ordinary income or loss — disproportionately relative to partners' overall capital or profit-sharing percentages. This is the drafting mechanism that makes the entire tax equity flip model possible: without the ability to specially allocate the ITC and depreciation almost entirely to the investor (99%) while the sponsor retains a smaller nominal share, the flip structures discussed throughout this syllabus could not exist in their current form.

### Statutory and Regulatory Basis for Special Allocations

**Key Points**

- §704(a) permits partners to agree to allocate income, gain, loss, deduction, and credit in the partnership agreement in whatever proportions they choose, rather than requiring allocations to mirror capital contribution percentages.
- These special allocations are only respected for tax purposes if they satisfy the Substantial Economic Effect (SEE) framework under §704(b) (or, failing that, reflect the partners' interest in the partnership) — meaning a special allocation is a *drafting choice* that must be independently validated against the SEE tests covered in Substantial Economic Effect Rules Under Section 704(b).
- Tax credits present a unique wrinkle within the special allocation framework: unlike income, gain, loss, and deduction (which directly affect capital accounts), tax credits themselves do **not** affect capital accounts under the general capital account maintenance rules, since credits are not "book items" in the way income or expense are.

### The Distinct Treatment of Credit Allocations

```mermaid
flowchart TD
    A[Partnership Generates Tax Items] --> B[Income, Gain, Loss, Deduction]
    A --> C[Investment Tax Credit / Production Tax Credit]
    B --> D[Allocated per Partnership Agreement - Subject to Section 704(b) SEE Test]
    D --> E[Directly Affects Capital Accounts]
    C --> F[Allocated per Partnership Agreement - Generally Follows Partners Interest in Partnership for Credit Property]
    F --> G[Does Not Directly Affect Capital Accounts]
    C --> H[Section 46(e)/Section 50(c) - ITC Allocation Tied to Partners Interest in Partnership Property]
```

**Key Points**

- Because credits do not affect capital accounts, the SEE framework (built around capital account mechanics) does not directly apply to credit allocations the same way it applies to income and loss — instead, the allocation of the ITC specifically has historically been governed by rules tying the credit allocation to each partner's interest in the underlying "partnership item" (i.e., the credit property), as informed by former Reg. §1.46-3(f) principles (under the historic investment credit rules) and subsequent guidance.
- For the ITC specifically, allocations are generally respected if they are proportionate to the partners' shares of the *depreciation* attributable to that property, reflecting the historical linkage between credit eligibility and depreciable basis in the underlying energy property.
- For the PTC, which is generated based on electricity production and sale over a 10-year period rather than tied to a single placed-in-service credit base, allocation follows the general partnership allocation framework for the income/deduction items associated with the underlying production activity, since PTC amounts are computed and claimed by the owner of the qualified facility (here, the partnership) and allocated per the partnership agreement.
- [Inference] Because credit allocation authority derives from a different regulatory lineage than the core §704(b) capital-account-based SEE rules, practitioners drafting flip partnership agreements typically address credit allocation provisions as a related but analytically distinct section from the core profit/loss/capital allocation provisions, often cross-referencing the depreciation allocation percentage to establish the credit allocation percentage.

### Structuring the "Flip" Through Special Allocations

**Key Points**

- The defining feature of a partnership flip is a special allocation schedule that provides one percentage split (e.g., 99% investor / 1% sponsor) for income, loss, depreciation, and credit prior to the investor achieving its target IRR ("flip date"), followed by an entirely different split (e.g., 5% investor / 95% sponsor) after that date.
- This shift is not a single retroactive reallocation — it is a **prospective** change in the allocation percentages specified in the partnership agreement, triggered by the achievement of a defined economic hurdle (commonly a target IRR, though sometimes a fixed date or other metric), and must be drafted so that each period's allocations independently satisfy the SEE requirements for that period.
- Because the flip date itself is frequently defined by reference to the investor achieving a specified after-tax IRR (calculated using the actual allocated tax benefits and cash distributions), there is an inherent circularity in modeling: the allocations (which the model needs to calculate returns) also determine when the allocations change (the flip trigger) — this is resolved through iterative HLBV-based financial modeling rather than a simple closed-form calculation.
- [Inference] Because the flip trigger and the allocation percentages are interdependent, partnership agreements typically include detailed mechanical provisions (often with illustrative numerical examples in an appendix) specifying exactly how the flip date is measured and calculated, to minimize the risk of dispute between sponsor and investor about whether or when the flip has occurred.

### Special Allocations Involving Nonrecourse Debt

**Key Points**

- As discussed in the SEE topic, deductions attributable to nonrecourse partnership debt require a separate analytical framework (Treas. Reg. §1.704-2) because no partner bears the economic risk of loss for nonrecourse liabilities by definition, meaning ordinary economic effect principles cannot apply to those specific deductions.
- Special allocations of nonrecourse deductions to the tax equity investor (common where the project is financed partly with back-leverage or construction-period nonrecourse debt) must be limited by, and structured consistently with, the partnership minimum gain chargeback mechanics to be respected.
- Special allocations of "partner nonrecourse deductions" (attributable to debt from a partner or a party related to a partner) require an even more specific allocation to the partner bearing the economic risk of loss for that particular debt, under Treas. Reg. §1.704-2(i), rather than the general flip percentage.

### Special Allocations and Section 704(c)/Reverse Section 704(c) Property

**Key Points**

- Where the sponsor contributes previously-developed project assets with built-in gain (common at deal formation), the general special allocation percentages agreed to in the partnership agreement must operate consistently with the mandatory §704(c) allocation of that built-in gain back to the contributing sponsor, as discussed in Capital Account Maintenance and Book-Ups.
- Following any book-up event, the same interplay applies to reverse §704(c) allocations, meaning the "special allocation" the partnership agreement describes for ordinary post-formation income, loss, and depreciation must be layered on top of (and not conflict with) the separate §704(c)/reverse §704(c) allocation of pre-existing or pre-revaluation built-in gain or loss.

### Practical Drafting Considerations

**Example**

A partnership agreement for a solar flip specifies: (1) depreciation, ITC, and net losses are allocated 99% to the investor and 1% to the sponsor from formation until the flip date; (2) net income (to the extent any exists during this period) is allocated in the same 99%/1% ratio, subject to the QIO provision requiring reallocation of income to cure any impermissible capital account deficit; (3) upon the investor achieving its target 8% after-tax IRR (as calculated under the agreement's defined methodology), allocations shift prospectively to 5% investor / 95% sponsor for all subsequent periods; and (4) nonrecourse deductions attributable to project-level debt are allocated consistent with the general 99%/1% split, subject to the minimum gain chargeback provision limiting the investor's cumulative nonrecourse deduction allocation to available partnership minimum gain.

**Key Points**

- Special allocation provisions are typically drafted with substantial precision regarding the calculation methodology for the flip trigger (defined IRR calculation inputs, timing conventions, treatment of specific cash flow items) since ambiguity here is a frequent source of post-closing dispute between sponsor and investor.
- Tax opinions obtained in connection with flip partnership formation typically address whether the special allocation provisions (including the shift at the flip date) satisfy SEE both before and after the flip, since each period's allocation scheme must independently pass the test.
- [Unverified] Market-standard flip percentages and IRR targets vary by technology, deal size, and prevailing capital market conditions at the time of structuring; specific percentages referenced in this material are illustrative only and should not be assumed to reflect current market terms without independent verification.

### Common Pitfalls

**Key Points**

- Drafting credit allocation provisions as if they were automatically governed by the same capital-account-based SEE test that applies to income and loss, without recognizing the distinct (and less capital-account-dependent) framework historically applied to credit allocations.
- Failing to ensure that both the pre-flip and post-flip allocation schemes independently satisfy the SEE requirements, since a partnership agreement that only addresses SEE compliance for the pre-flip period risks having post-flip allocations challenged.
- Structuring special allocations of nonrecourse deductions without a properly drafted minimum gain chargeback provision, risking a finding that those allocations lack economic effect.
- Ambiguous or incomplete drafting of the flip trigger's IRR calculation methodology, creating room for sponsor/investor disputes about whether and when the flip has actually occurred.

**Next Topics**

- Historical ITC Allocation Rules Under Former Treasury Regulation 1.46-3(f)
- Modeling the Flip Trigger: Circularity Between Allocations and IRR Calculation
- Partner Nonrecourse Deductions and Economic Risk of Loss Determination
- Tax Opinion Scope for Pre-Flip and Post-Flip Allocation Compliance
- Qualified Income Offset Drafting for Special Allocation Structures
- PTC Allocation Mechanics Over the 10-Year Credit Period