## Negotiating Investor Share of Depreciation and Cash Flow

### Overview

Negotiating Investor Share of Depreciation and Cash Flow addresses how sponsors and tax equity (or preferred equity) investors determine the specific percentage allocations of depreciation deductions and operating cash distributions within a partnership structure — particularly in hybrid deals where the ITC/PTC has been separated out via transfer under §6418, leaving depreciation and cash flow as the primary remaining negotiated economics. This negotiation determines the investor's effective yield, the sponsor's residual value retention, and the pacing of the eventual flip.

### Why Depreciation and Cash Flow Are Negotiated Separately from Credits

**Key Points**

- Once a credit is sold under a transfer election, it is no longer available to allocate in-kind to any partner; depreciation, by contrast, **cannot** be transferred under §6418 and must always be allocated through traditional partnership mechanics under §704(b)/§704(c).
- This makes the depreciation and cash flow allocation the primary remaining lever sponsors and investors negotiate in a combined flip/transfer deal, since the credit portion of the return may already be fixed (as cash proceeds) by the time this negotiation occurs.
- Depreciation carries different value depending on the investor's tax rate and how quickly it can use the deduction (bonus depreciation vs. standard MACRS schedules), which is why the *percentage allocated* is only part of the story — timing and investor-specific usability also matter to the final negotiated split.
- Cash flow allocation is negotiated somewhat independently of depreciation because it reflects actual project cash generation (which can differ substantially from tax depreciation timing), so investors and sponsors often use different percentage splits for the two.

### The Depreciation Allocation Negotiation

```mermaid
flowchart TD
    A[Project Depreciable Basis After Section 50(c) Reduction] --> B[MACRS / Bonus Depreciation Schedule]
    B --> C{Negotiated Investor Allocation Percentage}
    C --> D[Pre-Flip: High Investor Share, e.g. 99%]
    C --> E[Post-Flip: Reduced Investor Share, e.g. 5%]
    D --> F[Investor Tax Benefit - Rate Dependent]
    E --> G[Sponsor Retains Majority Post-Flip]
    F --> H[Contributes to Investor Target IRR]
```

**Key Points**

- Standard pre-flip depreciation allocations to tax equity investors in traditional flip deals commonly range from approximately 99% (mirroring near-total allocation of tax attributes) though the precise figure is a negotiated point reflecting the investor's overall capital contribution and risk-bearing role, not a statutory requirement.
- Section 50(c) requires basis reduction equal to 50% of the ITC amount claimed (or a different percentage for certain credits determined without regard to the transfer election, per specific transfer-related basis rules), meaning the depreciable base available for allocation is smaller than total project cost — this reduction must be modeled before negotiating percentage splits, since it affects the absolute dollar value being divided.
- Bonus depreciation percentages have been subject to a statutory phase-down schedule under §168(k) (100% bonus expired for property placed in service after 2022, phasing down in subsequent years absent further legislative action); [Unverified] the applicable bonus depreciation percentage for any specific placed-in-service date should be confirmed against current law at time of structuring, since Congress has adjusted these percentages via subsequent legislation.
- Investors with a higher marginal tax rate or larger existing taxable income base generally value each dollar of depreciation more highly, which can support a sponsor negotiating a smaller investor percentage allocation while still meeting the investor's target after-tax yield.

### The Cash Flow Allocation Negotiation

**Example**

A wind project's partnership agreement allocates 99% of depreciation and losses to the tax equity investor pre-flip, but only 20% of operating cash flow pre-flip (with the sponsor retaining 80% of cash for debt service coverage and sponsor liquidity needs), reflecting a negotiated point where the investor's return is weighted more heavily toward the tax benefit than the cash distribution during the pre-flip period. Post-flip, cash flow shifts to a 5%/95% investor/sponsor split, mirroring (though not necessarily identically to) the depreciation flip percentage.

**Key Points**

- It is common, though not universal, for cash flow and depreciation/tax allocation percentages to differ from one another pre-flip, since sponsors often need a larger share of actual cash to service project-level or back-leverage debt, even while allocating the bulk of tax benefits to the investor.
- [Inference] This divergence between cash and tax allocation percentages is a key negotiating lever: sponsors seeking more near-term liquidity will push for a lower investor cash percentage, while investors focused purely on tax benefit (rather than current cash return) may accept a lower cash share if the tax allocation and eventual flip economics still support their target IRR.
- The negotiated cash flow split directly affects the calculation of when the flip date is reached under HLBV accounting, since the investor's realized economic return (used to measure progress against target IRR) includes both cash distributions received and the tax benefit value of allocated depreciation and (if applicable) credits.

### HLBV and the Interaction Between Allocations and Flip Timing

**Key Points**

- Hypothetical Liquidation at Book Value (HLBV) accounting is used to determine each partner's claim on partnership equity at any point in time, based on what each partner would receive if the partnership were liquidated at book value — this method underlies both GAAP equity method accounting for the investor and the practical tracking of progress toward the flip.
- Because HLBV reflects the actual negotiated percentages for depreciation, income/loss, and cash flow (as well as any retained credit or transfer proceeds allocation), changes to any one of these percentages during negotiation directly affect the modeled timing of the flip date and the investor's realized IRR at each measurement point.
- [Inference] Sponsors and investors typically iterate through several allocation scenarios in a financial model before finalizing percentages, testing how different depreciation/cash flow splits affect flip timing under multiple sensitivity cases (e.g., production variance for wind, degradation assumptions for solar) to ensure the negotiated allocation produces an acceptable and achievable target IRR path for the investor without excessively delaying sponsor residual value capture.

### Factors Sponsors Weigh in Negotiation

**Key Points**

- **Debt service coverage needs**: If the project carries back-leverage debt at the sponsor level, the sponsor typically needs a larger share of cash flow (even at the expense of a higher investor tax allocation) to service that debt without shortfall.
- **Investor's cost of capital**: A higher required investor return (reflecting the investor's own cost of capital and risk assessment of the specific project/technology) generally necessitates either a larger allocation percentage, a longer allocation period before flip, or both.
- **Post-flip residual value**: Sponsors negotiate to reach the flip date as early as feasible (without triggering IRS anti-abuse concerns about artificially compressed flip periods) since post-flip cash flow and depreciation revert predominantly to the sponsor.
- **Technology-specific risk premiums**: Newer or less-proven technologies typically command higher investor allocation percentages or longer flip periods to compensate for the perceived higher operating risk, compared to well-established solar or wind projects with long performance track records.

### Common Structuring Terms Affecting the Negotiation

**Key Points**

- **Minimum gain chargeback and qualified income offset provisions**: Standard §704(b) safe harbor provisions required to support the economic allocations agreed upon; these must be properly drafted regardless of the specific percentages chosen; without a partner-level Deficit Restoration Obligation (DRO), the investor's loss allocation is generally limited by these safe-harbor mechanics (in particular the minimum gain chargeback), rather than being unconstrained by the negotiated headline percentage.
- **Curative or corrective allocations**: Used to true-up allocations if actual results diverge from projections in ways that would otherwise cause the negotiated economic percentages to fail the primary §704(b) tests.
- **Buy-sell and put/call options**: Often negotiated alongside the depreciation/cash flow split, giving the sponsor a call option to buy out the investor's interest after the flip (and/or the investor a put option to exit), which interacts with the overall economics since the option pricing typically references the negotiated allocation percentages and resulting projected returns.

### Common Pitfalls

**Key Points**

- Negotiating depreciation and cash flow percentages in isolation from the Section 50(c) basis reduction calculation, leading to allocation percentages applied against an incorrect depreciable base.
- Failing to model how a divergence between cash flow percentage and depreciation percentage affects the HLBV-calculated flip date, potentially causing the flip to occur later (or earlier) than either party anticipated.
- Assuming a single "market standard" percentage split exists across all deals; [Unverified] actual negotiated percentages vary substantially by technology, investor type, project risk profile, and prevailing market conditions, and should not be assumed static from prior transactions without current market confirmation.
- Under-addressing minimum gain chargeback and DRO mechanics, which can cause the investor's actual usable loss allocation in a given year to fall short of the headline negotiated percentage if the safe harbor provisions are not properly structured.

**Next Topics**

- Section 50(c) Basis Reduction Calculation Mechanics
- HLBV Accounting Methodology for Partnership Flip Structures
- Minimum Gain Chargeback and Deficit Restoration Obligations
- Bonus Depreciation Phase-Down Schedule and Placed-in-Service Timing
- Put/Call Option Structuring at Partnership Flip Exit
- Back-Leverage Debt Sizing and Its Effect on Cash Flow Allocation Negotiations