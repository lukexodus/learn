## Capital Account Maintenance and Book-Ups


### Overview

Capital Account Maintenance and Book-Ups refers to the mechanics required under Treas. Reg. §1.704-1(b)(2)(iv) for tracking each partner's economic interest in a partnership over time, and the specific process — a "book-up" (or book-down) — by which the partnership revalues its assets to fair market value and adjusts partners' capital accounts accordingly upon certain triggering events. Proper capital account maintenance is a prerequisite to satisfying the general economic effect test discussed in Substantial Economic Effect Rules Under Section 704(b), and book-ups are particularly significant in tax equity flip structures because they can affect how depreciation and gain are allocated going forward.

### Core Capital Account Maintenance Rules

**Key Points**

- Treas. Reg. §1.704-1(b)(2)(iv) requires that, to have economic effect, a partnership agreement must provide for capital accounts maintained as follows: increased by (i) the amount of money contributed, (ii) the fair market value of property contributed (net of liabilities the partnership is treated as assuming), and (iii) allocations of partnership income and gain (including tax-exempt income); decreased by (i) money distributed, (ii) the fair market value of property distributed (net of liabilities the distributee is treated as assuming), and (iii) allocations of partnership loss and deduction (including nondeductible, noncapitalizable expenditures).
- Capital accounts are maintained on a **book basis**, not tax basis, for property with a difference between fair market value and adjusted tax basis at contribution — this book/tax distinction is central to how §704(c) allocations interact with capital account maintenance.
- The regulations permit certain simplifying conventions (e.g., treating syndication costs as reducing capital accounts, and specific rules for guaranteed payments), but any deviation from the core maintenance rules risks the partnership agreement failing to satisfy the economic effect safe harbor.
- Capital accounts must reflect the partnership's assets at book value (which starts at fair market value upon contribution and is adjusted for cost recovery/depreciation using book, not tax, depreciation methods) whenever there is a difference between book and tax basis in an asset.

### What a Book-Up Is and When It Occurs

```mermaid
flowchart TD
    A[Triggering Event Occurs] --> B{Permitted Revaluation Event Under Reg 1.704-1(b)(2)(iv)(f)}
    B -->|Yes| C[Partnership Revalues Assets to Fair Market Value]
    C --> D[Capital Accounts Adjusted - Book-Up or Book-Down]
    D --> E[Unrealized Gain/Loss Allocated to Existing Partners per Partnership Agreement]
    E --> F[New Book Value Becomes Basis for Future Book Depreciation and Allocations]
    B -->|No| G[No Revaluation - Capital Accounts Continue on Existing Book Basis]
```

**Key Points**

- A "book-up" (or, if value has declined, a "book-down") is a revaluation of partnership property to its then-current fair market value, with a corresponding adjustment to partners' capital accounts to reflect their share of the unrealized appreciation or depreciation inherent in that revaluation.
- Treas. Reg. §1.704-1(b)(2)(iv)(f) permits (but does not require) a book-up in connection with specific events, including: (i) the contribution of money or property by a new or existing partner in exchange for an interest in the partnership, (ii) the liquidation of the partnership or a distribution of money or property in liquidation of a partner's interest, (iii) the grant of an interest in the partnership as consideration for services, and (iv) in connection with the issuance of a "noncompensatory option" under later-added regulatory provisions.
- A book-up is **not automatic** — the partnership agreement must specifically provide for revaluation at these events, and the decision to do so (or not) is itself a structuring choice with tax consequences.
- Following a book-up, the partnership's book depreciation on the revalued asset is computed based on the new, higher (or lower) book value, which can diverge meaningfully from tax depreciation computed on the original (unadjusted) tax basis — creating a book/tax disparity that must then be addressed through "reverse §704(c)" allocations.

### Why Book-Ups Matter in Tax Equity Structures

**Key Points**

- When a tax equity investor is admitted to a partnership by contributing cash in exchange for a partnership interest (the standard structure for a flip deal), this admission is a permitted revaluation event — many partnership agreements elect to book up the partnership's assets to fair market value at that point, reflecting any appreciation in the project's value between initial formation/COD and the investor's admission.
- [Inference] Sponsors sometimes prefer to book up assets upon investor admission because doing so increases the book basis on which book depreciation is calculated going forward, which can support a cleaner allocation of book depreciation to the investor consistent with the negotiated flip percentages, even though tax depreciation (computed on the unadjusted, lower, original tax basis) continues on its own schedule.
- The resulting book/tax disparity from a book-up must be addressed via "reverse §704(c)" allocation methods (using the same traditional, curative, or remedial method framework as regular §704(c)), to ensure that any built-in gain or loss existing in the property *at the time of the book-up* is eventually allocated back to the partners who owned the interest at that time, rather than being shifted to a partner (like the newly admitted investor) who was not a partner during the period that value accrued.
- Because tax equity flip transactions frequently close shortly after or at commercial operation date, book-up decisions and their reverse §704(c) implications are a standard diligence item in flip partnership formation, with the tax opinion for the transaction typically addressing whether the revaluation and subsequent allocation methodology properly comply with the regulations.

### Reverse Section 704(c) Allocations

**Key Points**

- "Reverse §704(c)" refers to the application of §704(c)-type principles to book-ups (as opposed to original §704(c), which applies to actual property contributions with a built-in gain/loss at the time of contribution).
- The same three allocation methods available under standard §704(c) — the traditional method, the traditional method with curative allocations, and the remedial allocation method — are generally available for reverse §704(c) purposes, chosen based on which best matches the deal's negotiated economics and the parties' tolerance for the "ceiling rule" limitation inherent in the traditional method.
- The **remedial allocation method** is common in tax equity flip structures precisely because it eliminates the ceiling rule problem (where the traditional method can fail to fully allocate book depreciation to noncontributing partners due to insufficient tax depreciation to match), instead creating notional tax items to ensure the noncontributing partner (the investor) receives book allocations matching the negotiated percentage, with offsetting notional items allocated to the partner who held the built-in gain (the sponsor).
- [Inference] Because the remedial method's use of notional tax items can be viewed by some practitioners as more aggressive or requiring more careful documentation than the traditional method, the choice of reverse §704(c) method is frequently a point of negotiation and diligence between sponsor and investor counsel, often resolved with reference to the specific facts of the built-in gain amount and the flip percentages involved.

### Section 704(c) vs. Reverse Section 704(c): Distinguishing the Two

| Feature | Section 704(c) (Contributed Property) | Reverse Section 704(c) (Book-Up) |
| --- | --- | --- |
| Trigger | Contribution of property with book/tax difference | Revaluation event (e.g., new partner admission) |
| Built-in gain/loss holder | Partner who contributed the property | Partners who held interests before the book-up |
| Purpose | Prevent shifting pre-contribution gain/loss to other partners | Prevent shifting pre-revaluation gain/loss to new/incoming partners |
| Allocation methods available | Traditional, traditional with curative, remedial | Traditional, traditional with curative, remedial (same framework) |

### Ongoing Capital Account Maintenance Through the Partnership's Life

**Key Points**

- Capital accounts must continue to be maintained accurately throughout the entire life of the partnership, not just at formation or at the point of a book-up — this includes properly reflecting all subsequent allocations of book income, gain, loss, and deduction, as well as all contributions and distributions, on an ongoing basis.
- In HLBV accounting (used by the tax equity investor for financial reporting purposes), capital account balances calculated under the §704(b) rules are a direct input, since HLBV determines the investor's claim on partnership equity by reference to what each partner's capital account would entitle them to receive upon a hypothetical liquidation at book value.
- Errors or inconsistencies in ongoing capital account maintenance (e.g., failing to properly apply book depreciation following a book-up, or misapplying the QIO or minimum gain chargeback mechanics discussed in the Section 704(b) topic) can jeopardize the economic effect safe harbor retroactively, since the regulations require accounts be maintained correctly "throughout the full term of the partnership."

### Common Pitfalls

**Key Points**

- Failing to include explicit book-up language in the partnership agreement, meaning that even where a triggering event under Treas. Reg. §1.704-1(b)(2)(iv)(f) occurs, the partnership cannot revalue its assets because the agreement did not provide for it.
- Choosing the traditional method for reverse §704(c) allocations without checking whether the "ceiling rule" will prevent the investor from receiving its full negotiated share of book depreciation, potentially undermining the intended flip economics.
- Treating capital account maintenance as a one-time drafting exercise rather than an ongoing bookkeeping obligation that must be accurately tracked for the life of the partnership to preserve the economic effect safe harbor.
- [Unverified] Assuming a book-up automatically benefits the tax equity investor; the actual effect depends on the specific reverse §704(c) method chosen and the magnitude of built-in gain at the time of book-up, and should be modeled on a deal-specific basis rather than assumed favorable.

**Next Topics**

- The Ceiling Rule Problem Under Traditional Section 704(c) Method
- Remedial Allocation Method Mechanics and Notional Tax Items
- HLBV Accounting and Its Reliance on Capital Account Balances
- Noncompensatory Options and Capital Account Revaluation
- Book Depreciation vs. Tax Depreciation Divergence After a Book-Up
- Syndication Costs and Their Capital Account Treatment