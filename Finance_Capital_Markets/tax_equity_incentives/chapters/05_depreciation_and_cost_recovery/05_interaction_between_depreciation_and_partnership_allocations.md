## Interaction Between Depreciation and Partnership Allocations


### Overview

Depreciation is frequently the single largest tax attribute allocated among partners in a renewable energy tax equity partnership, and the mechanics governing how it is allocated — and to whom — are among the most heavily negotiated provisions in a partnership flip agreement. Because MACRS depreciation on 5-year energy property is accelerated (and, under current 100% bonus depreciation, often front-loaded almost entirely into the placed-in-service year), the allocation of depreciation deductions largely determines how much taxable loss is available to shelter each partner's income in the early years of the partnership's life. This chapter item addresses the substantive tax law governing partnership allocations of depreciation and how it interacts with the specific mechanics of tax equity structuring.

### Statutory and Regulatory Framework: Section 704(b)

**Key Points**

- IRC §704(a) permits partners to allocate income, gain, loss, deduction, and credit among themselves as they agree in the partnership agreement, but §704(b) overrides this flexibility where an allocation lacks "substantial economic effect."
- If an allocation lacks substantial economic effect, the IRS may reallocate the item in accordance with the partners' interests in the partnership (PIP), determined based on all facts and circumstances — a standard tax equity structures are specifically designed to avoid triggering, since it introduces significant uncertainty.
- The Treasury Regulations under §704(b) establish a detailed safe harbor framework (the "economic effect" test) requiring, among other things: maintenance of partner capital accounts in accordance with specified rules, liquidation of the partnership in accordance with positive capital account balances, and either an unconditional deficit restoration obligation (DRO) or inclusion of a "qualified income offset" (QIO) provision combined with allocations that do not create or increase a capital account deficit beyond specified limits.
- Depreciation allocations, because they reduce capital accounts, are subject to these same economic effect rules; an allocation of 99% of depreciation to a tax equity investor is respected under §704(b) only if the underlying capital account mechanics and liquidation provisions satisfy the regulatory safe harbor (or, alternatively, if the allocation can be shown to be in accordance with the partners' interests in the partnership under the facts-and-circumstances test).

### Capital Account Maintenance and Depreciation

**Key Points**

- Under the §704(b) capital account rules, each partner's capital account is increased by capital contributions and allocated income/gain, and decreased by distributions and allocated loss/deduction — including depreciation.
- Because depreciation is a non-cash deduction, it can drive a partner's capital account into negative territory even though no cash has changed hands; this is precisely the situation the DRO/QIO framework is designed to address.
- In typical wind and solar partnership flip structures, the tax equity investor lacks an unconditional deficit restoration obligation (investors are generally unwilling to commit to restore a capital account deficit with unlimited personal liability); instead, the partnership agreement relies on the qualified income offset alternative, combined with allocation limitations (often called a "loss allocation limitation" or "stop-loss" provision) that cap the investor's allocated losses (including depreciation) at the point the investor's capital account would otherwise go negative beyond a permitted threshold.
- Because of this stop-loss mechanic, depreciation allocations to the tax equity investor in later years of the partnership term are frequently curtailed, with any "excess" depreciation reallocated to the sponsor — a dynamic that must be modeled carefully since it directly affects both partners' after-tax cash flow projections.

```mermaid
flowchart TD
    A[Partnership Agreement Allocation Provisions] --> B{Does Allocation Have Substantial Economic Effect?}
    B -->|Yes - Safe Harbor Met| C[Capital Accounts Maintained per Section 704(b) Regs]
    C --> D[Liquidation per Positive Capital Account Balances]
    D --> E{DRO or QIO?}
    E -->|Unconditional DRO| F[Investor Allocated Losses Without Cap]
    E -->|Qualified Income Offset| G[Loss Allocation Limitation / Stop-Loss Applies]
    G --> H[Excess Depreciation Reallocated to Sponsor]
    B -->|No - Lacks Economic Effect| I[IRS May Reallocate per Partners Interest in Partnership - PIP Standard]
```

### The Investor's 99% Allocation and HLBV Accounting

**Key Points**

- A common (though not universal) structural feature of wind and solar partnership flips is allocating a disproportionately large share (often around 99%) of tax items, including depreciation, to the tax equity investor prior to the "flip point," reflecting the investor's disproportionate contribution of capital relative to its share of cash distributions.
- For financial reporting (not tax) purposes, sponsors and investors typically use the Hypothetical Liquidation at Book Value (HLBV) method to determine each partner's share of book income or loss for GAAP purposes, which is a distinct computation from the tax depreciation allocation under §704(b) and should not be conflated with it — HLBV drives book/GAAP results, while §704(b) capital accounts and the partnership agreement's tax allocation provisions drive the actual tax return (Schedule K-1) reporting.
- [Inference] The specific percentage allocated to the investor (99%, or another negotiated split) is a matter of deal-specific negotiation rather than a fixed statutory or regulatory requirement; what the Regulations require is that whatever percentage is used be supportable under the substantial economic effect safe harbor or the alternative facts-and-circumstances PIP standard.

### Section 704(c) and Built-In Gain/Loss on Contributed Property

**Key Points**

- Where a partner contributes property (rather than cash) to the partnership — for example, a sponsor contributing a developed project with an existing tax basis that differs from its fair market value at the time of contribution — §704(c) requires that built-in gain or loss be allocated back to the contributing partner, including through the "reverse §704(c)" mechanics that can apply to depreciation on contributed property.
- §704(c) allocation methods (traditional method, traditional method with curative allocations, or remedial method) affect how depreciation on contributed property is allocated between the contributing partner and other partners, and the choice of method is itself a negotiated partnership agreement provision with tax consequences for both parties.
- This is particularly relevant in "drop-down" partnership structures where a sponsor develops a project in one entity and then contributes it to a tax equity partnership, creating built-in gain (if fair market value at contribution exceeds tax basis) that has downstream depreciation allocation consequences.

### Interaction with Section 743(b) and Section 754 Elections

**Key Points**

- Where a partnership has a §754 election in effect, a transfer of a partnership interest (such as a tax equity investor's exit sale, or admission of a new investor via a secondary purchase) triggers a basis adjustment under §743(b) specific to the transferee partner, potentially creating additional depreciation (or negative adjustments) allocable solely to that transferee.
- This transferee-specific basis adjustment is layered on top of the "common basis" depreciation otherwise allocated under the general partnership agreement provisions, meaning two partners holding economically identical interests in the same partnership can have different depreciation allocations if one acquired its interest via a secondary transfer with a §743(b) step-up and the other did not.
- Tax equity secondary market transactions (sales of an existing investor's partnership interest to a new investor) frequently involve a §754 election specifically to generate this basis step-up, since the incoming investor typically wants depreciation based on its purchase price rather than the seller's historical (often already substantially depreciated) basis.

### Minimum Gain Chargeback and Nonrecourse Depreciation Deductions

**Key Points**

- Where a partnership's property is financed with nonrecourse debt (common in leveraged tax equity structures and back-leveraged holding company financings), depreciation deductions attributable to the nonrecourse-debt-financed portion of basis are subject to special §704(b) "minimum gain chargeback" rules under Treasury Regulation §1.704-2.
- Partnership nonrecourse deductions (which includes depreciation funded by nonrecourse debt in excess of the property's book value) must generally be allocated in a manner reasonably consistent with allocations of some other significant partnership item attributable to the property, and any allocation of nonrecourse deductions must be respected under a distinct safe harbor from the general economic effect test, since nonrecourse deductions by definition do not have "economic effect" in the traditional sense (no partner bears the economic burden of nonrecourse debt in the same way as recourse debt).
- If minimum gain is later realized (e.g., upon a decrease in the nonrecourse debt or disposition of the property), a minimum gain chargeback provision requires allocating partnership income equal to that partner's share of the decrease in minimum gain, reversing the benefit of the earlier nonrecourse deductions — a mechanic tax equity documents must include to preserve respect for depreciation allocations funded partly by back-leverage or other nonrecourse project-level debt.

### Interaction with the At-Risk Rules and Passive Activity Loss Limitations

**Key Points**

- Even where a partnership agreement validly allocates a large share of depreciation to the tax equity investor under §704(b), that investor's ability to currently *use* the allocated loss on its own tax return is separately constrained by the at-risk rules under §465 and the passive activity loss rules under §469.
- The at-risk rules generally limit a partner's deductible losses to the amount the partner has economically at risk in the partnership (contributed capital plus certain qualified nonrecourse financing), which is a distinct limitation from the §704(b) capital account mechanics governing whether the allocation itself is respected.
- The passive activity loss rules under §469 generally treat a tax equity investor's interest in the partnership as a passive activity (absent material participation), limiting the investor's ability to use allocated losses (including depreciation) against non-passive income, though this limitation is why many institutional tax equity investors specifically seek partnerships with income (from other passive investments) or engage in structures designed to generate usable passive income to absorb the losses.
- [Inference] The interplay between §704(b) allocation validity, §465 at-risk limitations, and §469 passive loss limitations means that a depreciation allocation can be simultaneously "valid" for partnership tax return (Form 1065 and Schedule K-1) reporting purposes while being partially or wholly unusable by a specific partner in a given year due to these separate limitations; investor-level usability modeling is therefore a distinct analytical step from partnership-level allocation validity.

### Depreciation Allocation Changes at the Flip Point

**Key Points**

- Partnership flip agreements typically specify a "flip point" — either a target date or a target after-tax IRR threshold for the tax equity investor — after which the allocation percentages for both cash distributions and tax items (including depreciation) shift substantially, commonly to a 5%/95% split favoring the sponsor.
- Because MACRS depreciation on energy property (especially under 100% bonus depreciation) is heavily front-loaded, by the time a typical flip point occurs (often 5-10 years post-COD), a substantial majority of total project depreciation has often already been claimed, meaning the post-flip depreciation allocation shift affects a comparatively smaller remaining pool of deductions — though this varies significantly by deal structure, technology, and whether bonus depreciation or standard MACRS was used.
- The flip mechanics must be drafted to work in conjunction with the capital account maintenance and stop-loss provisions discussed above, since a change in allocation percentage at the flip point is itself an allocation change that must independently satisfy the §704(b) substantial economic effect requirements (or PIP standard) for the post-flip period.

### Common Pitfalls

- Conflating HLBV book allocations (used for GAAP financial reporting) with §704(b) tax capital account allocations (used for the actual tax return), which are computed under different methodologies and can produce materially different results.
- Drafting a disproportionate depreciation allocation to the investor without corresponding capital account maintenance, DRO/QIO, and liquidation provisions sufficient to satisfy the substantial economic effect safe harbor.
- Overlooking transferee-specific §743(b) basis adjustments when a secondary sale of a partnership interest occurs, resulting in incorrect depreciation allocation to the incoming investor.
- Failing to draft adequate minimum gain chargeback provisions where nonrecourse (including back-leverage) debt finances a portion of depreciable basis.
- Assuming a valid §704(b) allocation automatically means the investor can currently use the allocated depreciation loss, without separately analyzing §465 at-risk and §469 passive activity loss limitations at the investor level.
- Failing to independently test the post-flip-point allocation percentages against the substantial economic effect requirements, rather than assuming the pre-flip structure's validity carries forward automatically.

**Related Topics**

- Substantial Economic Effect Safe Harbor Under Treasury Regulation Section 1.704-1(b)
- Qualified Income Offset and Deficit Restoration Obligation Provisions
- Hypothetical Liquidation at Book Value (HLBV) Accounting for Tax Equity
- Section 704(c) Built-In Gain Allocation Methods
- Section 754 Elections and Section 743(b) Basis Adjustments in Secondary Transfers
- Minimum Gain Chargeback and Nonrecourse Deduction Allocation (Treasury Regulation Section 1.704-2)
- At-Risk Rules (Section 465) and Passive Activity Loss Limitations (Section 469) for Tax Equity Investors
- Partnership Flip Structures: Flip Point Mechanics and Post-Flip Allocation Shifts