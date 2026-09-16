## Limited Liability Company and Partnership Operating Agreements


### Overview

The operating agreement (for an LLC taxed as a partnership) or partnership agreement (for a state-law partnership) is the foundational legal document governing a tax equity transaction. It translates the negotiated economic deal — the allocation of tax credits, taxable income and loss, and cash distributions between the sponsor and tax equity investor — into binding contractual and tax-law-compliant provisions. This document is simultaneously a corporate governance instrument, a tax allocation mechanism under Subchapter K, and the source document for the HLBV and PAM accounting analyses covered elsewhere in this course.

### Purpose and Legal Function

**Key Points**

- Governs the **relationship between members/partners**, including capital contributions, allocations, distributions, governance rights, transfer restrictions, and dissolution/liquidation mechanics.
- Establishes the entity's classification for U.S. federal tax purposes as a **partnership** (pass-through), which is essential to achieving the sharing of tax credits and depreciation between sponsor and investor — a corporation could not pass through ITC/PTC and depreciation to its shareholders in the same manner.
- Provides the **liquidation waterfall** referenced directly in HLBV accounting — the actual liquidation provisions in this document are what an equity method investor applies each period to compute its hypothetical liquidation claim.
- Documents the **partnership flip mechanics**: the specific allocation percentages before and after the flip point, the definition of the flip point itself (e.g., investor reaching a target after-tax IRR, or a fixed date, or the earlier/later of the two), and any true-up or catch-up provisions.

### Core Structural Provisions

**Key Points**

1. **Capital contributions** — timing, amount, and conditions precedent for the tax equity investor's capital contribution(s), often structured in multiple tranches tied to construction milestones or the placed-in-service date.
2. **Capital accounts** — maintenance of Section 704(b) capital accounts for each member, which must be maintained in accordance with Treasury Regulation requirements to support the validity of special (non-pro-rata) allocations.
3. **Allocations of income, loss, and tax credits** — the specific percentage splits for taxable income/loss and tax credits, which are often **different** from the cash distribution percentages, especially before and after the flip.
4. **Distributions** — the cash distribution waterfall, which may differ from the tax allocation waterfall (a structural feature that itself contributes to the HLBV vs. tax model reconciliation complexity).
5. **Management and governance** — designation of the managing member (typically the sponsor) with day-to-day operational authority, together with **major decision / consent rights** reserved to the investor (e.g., approval over budgets exceeding a threshold, removal of the managing member for cause, admission of new members, and amendments to the agreement).
6. **Transfer restrictions** — restrictions on transfer of membership interests, particularly important because a transfer exceeding certain thresholds can trigger ITC recapture under the ownership-change rules.
7. **Indemnification provisions** — sponsor indemnification obligations to the investor for tax-related losses, including recapture events, structural challenge by the IRS, and breaches of representations and warranties.
8. **Buyout / put-call options** — mechanics for the sponsor's post-flip buyout of the investor's residual interest (often structured as a **fair market value purchase option** rather than a fixed-price call, to avoid recharacterization risk).
9. **Dissolution and liquidation** — the terms governing wind-down of the entity, including the final liquidating distribution waterfall (directly relevant to HLBV).

### Diagram: Key Operating Agreement Provisions and Their Downstream Effects

```mermaid
flowchart TD
    A[Operating / Partnership Agreement] --> B[Capital Account Maintenance Provisions]
    A --> C[Income, Loss, and Tax Credit Allocation Provisions]
    A --> D[Cash Distribution Waterfall]
    A --> E[Liquidation Waterfall]
    A --> F[Governance and Consent Rights]
    A --> G[Transfer Restrictions]
    A --> H[Buyout / Put-Call Option Mechanics]
    B --> I[Section 704(b) Substantial Economic Effect Analysis]
    C --> J[Tax Model - Flip Point and IRR Calculation]
    D --> J
    E --> K[HLBV Accounting - Hypothetical Liquidation Claim]
    F --> L[VIE Consolidation Analysis under ASC 810]
    G --> M[ITC Recapture Risk - Ownership Change Rules]
    H --> N[Step Transaction / Recharacterization Risk Analysis]
```

### Substantial Economic Effect and Section 704(b)

**Key Points**

- Special (non-pro-rata) allocations of income, loss, and credits are only respected for tax purposes if they have **"substantial economic effect"** under Treasury Regulation Section 1.704-1(b), or are otherwise in accordance with the partners' interests in the partnership.
- The regulations generally require: (a) capital accounts maintained in accordance with the regulations, (b) liquidating distributions made in accordance with positive capital account balances, and (c) a partner who has a deficit capital account balance following liquidation must be **unconditionally obligated to restore that deficit**, OR the agreement must contain a **"qualified income offset"** provision.
- Because tax equity investors generally do **not** provide a deficit restoration obligation (DRO) in typical structures (or provide only a limited DRO), the agreement instead relies on a **qualified income offset (QIO)** combined with allocation limitations tied to the investor's capital account, to satisfy the alternate economic effect test.
- **Minimum gain chargeback provisions** are also standard, addressing the allocation consequences when nonrecourse debt exceeds the tax basis of partnership property (relevant in leveraged tax equity structures).

[Inference] The specific combination of QIO, minimum gain chargeback, and capital account restoration provisions used varies by deal and by counsel's approach to satisfying the substantial economic effect safe harbor; the general framework described is standard practice, but the precise drafting language is negotiated and reviewed by tax counsel on a deal-specific basis.

### Allocation of Tax Credits Specifically

**Key Points**

- ITC allocation follows the **"ITC allocation percentage"** as defined in Treasury Regulation Section 1.46-3(f) (as historically applied, and referenced in current practice) — generally, a partner's ITC allocation must correspond to that partner's share of the basis of the ITC-eligible property, which in practice tracks the partner's overall profit-sharing percentage in the partnership at the time the property is placed in service.
- PTC allocation, by contrast, follows the **partnership's allocation of gross income** attributable to electricity production, since PTC is a per-kilowatt-hour credit tied to production and sale of electricity, and is allocated consistent with how that income is allocated among partners.
- The agreement must carefully define these allocation mechanics because a **mismatch** between the stated allocation percentage and the requirements of the applicable ITC/PTC allocation regulations can jeopardize the tax equity investor's ability to claim the credits as intended.

[Unverified] The specific regulatory citations and their current interaction with subsequent IRS guidance (including any updates addressing partnership flip structures specifically) should be verified against current Treasury Regulations and any applicable IRS guidance in effect at the time of the transaction, as this is a technically detailed and periodically updated area of tax law.

### The Flip Point Definition

**Key Points**

The flip point is one of the most heavily negotiated provisions in the agreement. Common formulations include:

- **IRR-based flip**: the flip occurs when the investor's cumulative after-tax IRR first reaches the target rate (e.g., the investor's negotiated target yield), calculated using an agreed methodology (see the earlier module on managing circularity in flip-date determination).
- **Fixed-date flip**: the flip occurs on a specified calendar date, regardless of achieved IRR (less common as a sole trigger, but sometimes used as a backstop or minimum holding period).
- **Earlier-of / later-of formulations**: e.g., "the earlier of the date the investor achieves its target IRR or [fixed outside date]," or conversely "the later of," each shifting risk between sponsor and investor regarding how quickly the flip can occur.
- **True-up mechanics**: many agreements include a **"flip true-up"** provision addressing situations where the flip is later determined (e.g., upon audit or model correction) to have occurred earlier or later than originally calculated, with corresponding retroactive reallocation of items.

### Representations, Warranties, and Indemnities

**Key Points**

- Sponsor representations typically cover: title to the project assets, accuracy of the tax model and eligible basis calculations, compliance with prevailing wage and apprenticeship requirements (where relevant to credit rate adders under current law), environmental compliance, and absence of undisclosed liabilities.
- **Tax indemnification provisions** specifically address recapture events, disallowance of credits, and IRS challenges to the partnership's tax treatment, often coordinated with any tax credit insurance policy the parties have procured (see the earlier recapture risk module).
- **"Bad boy" guarantees** or **environmental indemnities** from the sponsor or its parent may be required to backstop specific risks the investor is unwilling to bear through the partnership structure alone.

### Governance and Consent Rights Table

**Example**

A representative (illustrative, not universal) consent rights allocation:

| Decision | Managing Member (Sponsor) Authority | Investor Consent Required? |
| --- | --- | --- |
| Day-to-day operations and maintenance | Yes, sole authority | No |
| Annual budget within approved parameters | Yes | No |
| Budget deviations above threshold (e.g., 10-15%) | No | Yes |
| Sale or encumbrance of project assets | No | Yes |
| Admission of new members | No | Yes |
| Amendment of the operating agreement | No | Yes |
| Removal of managing member for cause | N/A | Yes (investor-initiated right) |
| Refinancing of project-level debt | No | Yes |

[Inference] This table illustrates a common general pattern of governance rights allocation in tax equity partnership agreements; actual thresholds, consent rights, and their scope are heavily negotiated and vary significantly by deal size, sponsor track record, and investor risk tolerance.

### Interaction with Accounting Consolidation Analysis

**Key Points**

- The specific **governance and consent rights** documented in the operating agreement are the primary evidentiary basis for the ASC 810 VIE consolidation analysis (see earlier module) — whether the sponsor's day-to-day authority, combined with the investor's protective (rather than participating) consent rights, supports the conclusion that the sponsor holds the power to direct the VIE's most significant activities.
- Drafting choices that blur the line between "protective rights" (which do not affect consolidation) and "participating rights" (which can affect the power criterion) require close coordination between deal counsel and the parties' accounting advisors during negotiation, since a governance structure that inadvertently grants the investor more than protective rights could alter the consolidation conclusion.

### Common Negotiation Points

**Key Points**

- **DRO scope**: whether the investor provides any deficit restoration obligation, and if so, how limited/capped it is.
- **Buyout option pricing methodology**: fair market value determination mechanics (appraisal process, dispute resolution) for the post-flip sponsor buyout option.
- **Casualty and condemnation provisions**: how insurance/condemnation proceeds are applied (rebuild vs. distribute) and the resulting recapture risk allocation.
- **Change of control restrictions**: limitations on sponsor parent-level changes of control that could indirectly trigger investor consent rights or recapture concerns.
- **Cure periods**: for covenant breaches or compliance failures, negotiated cure periods before triggering default or indemnification remedies.

### Related Topics

- Modeling Compliance and Recapture Risk Scenarios
- Managing Circular References in Tax Equity Models
- Hypothetical Liquidation at Book Value (HLBV) Method
- VIE Consolidation Analysis under ASC 810 for Tax Equity Structures
- Capital Account Maintenance and Section 704(b) Allocations
- Tax Credit Insurance Policy Structuring
- Purchase and Sale Agreements in Tax Equity Transactions