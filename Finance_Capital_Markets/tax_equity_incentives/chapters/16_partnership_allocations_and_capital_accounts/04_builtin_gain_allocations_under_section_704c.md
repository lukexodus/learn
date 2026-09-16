## Built-In Gain Allocations Under Section 704(c)


### Overview

Built-In Gain Allocations Under Section 704(c) governs how a partnership must allocate tax items with respect to property contributed by a partner when that property's fair market value differs from its adjusted tax basis at the time of contribution. In tax equity and hybrid structures, §704(c) is central whenever a sponsor contributes a developed project (with built-in gain reflecting development margin) to a partnership in exchange for a partnership interest, ensuring that pre-contribution appreciation remains allocated to the contributing sponsor rather than being shifted to the incoming tax equity investor.

### Statutory Purpose and Framework

**Key Points**

- §704(c)(1)(A) requires that income, gain, loss, and deduction with respect to contributed property be allocated among partners so as to take account of the variation between the property's adjusted tax basis and its fair market value at the time of contribution — commonly referred to as "built-in gain" (if FMV exceeds basis) or "built-in loss" (if basis exceeds FMV).
- The underlying policy goal is to prevent partners from shifting the tax burden or benefit of pre-contribution appreciation or depreciation to other partners who did not economically bear that gain or loss, which could otherwise occur simply by contributing appreciated or depreciated property to a partnership with differing allocation percentages.
- Treas. Reg. §1.704-3 provides the operative rules implementing §704(c), including the three permitted allocation methods and detailed mechanics for applying each.
- §704(c) principles are triggered not only by actual contributions of property but also, by extension, by "reverse §704(c)" situations arising from a book-up revaluation event, as discussed in Capital Account Maintenance and Book-Ups — the same three methods apply in both contexts, though the mechanics reference book value at revaluation rather than value at actual contribution.

### The Book/Tax Disparity at the Heart of Section 704(c)

```mermaid
flowchart TD
    A[Partner Contributes Developed Project] --> B[Tax Basis: Historical Development Cost]
    A --> C[Book Value: Fair Market Value at Contribution]
    B --> D[Built-In Gain = FMV minus Tax Basis]
    D --> E{Section 704(c) Allocation Method}
    E --> F[Traditional Method]
    E --> G[Traditional Method with Curative Allocations]
    E --> H[Remedial Allocation Method]
    F --> I[Built-In Gain Allocated to Contributing Partner Upon Disposition or Via Depreciation Shortfall]
    G --> I
    H --> I
```

### The Three Permitted Allocation Methods

**Key Points**

- **Traditional method** (Treas. Reg. §1.704-3(b)): Tax depreciation, gain, and loss are allocated using the same conventions applied for book purposes, to the extent possible, with the contributing partner generally allocated less tax depreciation than book depreciation (since tax depreciation is computed on the lower historical basis) — this method is subject to the "ceiling rule," which caps the total tax depreciation allocable to noncontributing partners at the amount actually available for tax purposes, potentially leaving noncontributing partners with less tax depreciation than their book allocation would suggest.
- **Traditional method with curative allocations** (Treas. Reg. §1.704-3(c)): Addresses distortions caused by the ceiling rule by allocating other partnership tax items (e.g., additional ordinary income or a different depreciable asset's depreciation) to compensate the party disadvantaged by the ceiling rule limitation, without resorting to notional items.
- **Remedial allocation method** (Treas. Reg. §1.704-3(d)): Eliminates the ceiling rule problem entirely by creating notional tax items of income, gain, loss, or deduction as needed so that the noncontributing partner receives an allocation matching its book allocation, with an offsetting notional item allocated to the contributing partner — this method does not require an actual corresponding economic item elsewhere in the partnership, distinguishing it from the curative method.
- The remedial method is frequently the preferred choice in tax equity and hybrid flip structures specifically because the ceiling rule (unaddressed by the traditional method, or only partially addressed by curative allocations if suitable offsetting items are unavailable) could otherwise prevent the tax equity investor from receiving its full negotiated share of tax depreciation.

### The Ceiling Rule Problem Illustrated

**Example**

A sponsor contributes a solar project with a fair market value of $50 million and an adjusted tax basis of $30 million (reflecting a $20 million built-in gain from development margin and any prior depreciation). Under the traditional method, book depreciation is computed on the full $50 million book value, while tax depreciation is computed on only the $30 million tax basis. If the partnership agreement allocates 99% of book depreciation to the investor, the traditional method attempts to allocate 99% of the *available tax* depreciation to the investor as well — but because total tax depreciation is smaller than total book depreciation (reflecting the lower basis), the investor's tax depreciation allocation is "capped" at the total tax depreciation actually available, i.e., the ceiling rule prevents the investor from receiving tax depreciation exceeding the partnership's total tax depreciation for that period, even though its book allocation would imply a larger number.

**Key Points**

- The ceiling rule is not itself an anti-abuse penalty; it reflects a mathematical impossibility (the partnership cannot allocate more tax depreciation in total than actually exists), but its practical effect is to potentially disadvantage the noncontributing partner (typically the investor in a tax equity deal) relative to what its book/economic allocation percentage would otherwise produce.
- [Inference] This is precisely why the remedial method is common in tax equity structuring: by creating notional depreciation deductions (allocated to the investor) offset by notional income (allocated to the sponsor), the partnership can honor the negotiated 99% book depreciation allocation to the investor in full, without being constrained by the actual, lower amount of real tax depreciation available under the traditional method.

### Interaction with Reverse Section 704(c)

**Key Points**

- When a book-up occurs (e.g., upon admission of the tax equity investor as a new partner), any built-in gain existing in partnership property *at that time* becomes subject to reverse §704(c) principles, requiring that gain be allocated back to the partners who held interests before the book-up (i.e., the sponsor), using the same three-method framework.
- This means a single project can have **two layers** of §704(c)-type built-in gain to track: (1) original §704(c) built-in gain from the sponsor's initial contribution of the developed project to the partnership, and (2) reverse §704(c) built-in gain arising from any subsequent book-up upon the investor's admission — both must be separately identified, tracked, and allocated using the chosen method(s) for the life of the partnership.
- [Inference] Given this layering, practitioners drafting flip partnership agreements typically specify, with precision, which method applies to each distinct layer of built-in gain, since the two layers can, in principle, use different methods if the partnership agreement so provides, adding to the complexity of the allocation waterfall documentation.

### Anti-Abuse Considerations

**Key Points**

- Treas. Reg. §1.704-3(a)(10) contains a general anti-abuse rule providing that an allocation method (even one nominally among the three permitted methods) will not be respected if used with a view to shifting the tax consequences of built-in gain or loss among partners in a manner inconsistent with the purpose of §704(c).
- This anti-abuse standard means the mere selection of, e.g., the remedial method, does not automatically insulate a structure from scrutiny if the specific application appears designed primarily to achieve an inappropriate tax-shifting result rather than to reasonably approximate the economic arrangement of the parties.
- [Inference] In tax equity practice, the remedial method's use to address ceiling rule problems arising from genuine, arm's-length negotiated flip percentages is generally viewed as consistent with the regulations' purpose (ensuring the noncontributing partner receives its negotiated economic allocation), which is part of why it has become the dominant method in this asset class, though it remains subject to the general anti-abuse standard on its specific facts.

### Practical Application and Diligence

**Key Points**

- Identifying and quantifying built-in gain requires a clear valuation of the contributed project's fair market value at the time of contribution (or at book-up), compared against its adjusted tax basis — this valuation is often addressed through appraisal or other valuation support as part of deal diligence, since it directly drives the magnitude of the §704(c)/reverse §704(c) allocation.
- Tax opinions delivered in connection with tax equity flip closings typically address the selected §704(c) (and, where applicable, reverse §704(c)) method and confirm that its application is consistent with the regulations and does not run afoul of the anti-abuse rule.
- Ongoing partnership tax return preparation must track built-in gain amortization/recognition under the selected method for the life of the partnership (or until the built-in gain is fully accounted for), requiring specialized tax compliance software or detailed manual tracking given the complexity of remedial method notional items.

### Common Pitfalls

**Key Points**

- Selecting the traditional method without modeling whether the ceiling rule will materially shortfall the investor's expected tax depreciation allocation relative to the negotiated flip percentage.
- Failing to separately identify and track original §704(c) built-in gain (from contribution) versus reverse §704(c) built-in gain (from a subsequent book-up), leading to compliance errors in later tax return preparation.
- Applying the remedial method's notional items in a manner not clearly tied to a genuine economic allocation difference, risking challenge under the general anti-abuse rule.
- [Unverified] Assuming a specific built-in gain valuation will not be challenged; the fair market value determination at contribution or book-up is a factual question subject to IRS scrutiny, and adequate valuation support should be obtained and retained as part of deal diligence.

**Next Topics**

- Remedial Allocation Method Notional Item Mechanics in Detail
- Fair Market Value Determination and Appraisal Practice at Contribution
- Section 704(c) Anti-Abuse Rule Application to Tax Equity Structures
- Layering Original and Reverse Section 704(c) Built-In Gain Tracking
- Tax Compliance Software and Reporting for Remedial Method Allocations
- Interaction Between Section 704(c) Methods and the Flip Trigger Calculation