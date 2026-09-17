## Adjustments for Private Company Valuation


### Overview

Adjustments for private company valuation encompass the specific normalization, structural, and risk-related modifications required when valuing a business that lacks the public market data, standardized reporting, and third-party governance oversight of a publicly traded company. Private company valuation begins with the same core methods used for public companies (DCF, comparable companies, precedent transactions) but requires a distinct layer of adjustments to make private company financials comparable, to select appropriate inputs absent direct market data, and to reflect risks and rights not present in public equity.

### Why Private Companies Require Distinct Adjustments

Public companies are subject to standardized GAAP/IFRS reporting, SEC or equivalent regulatory oversight, independent audits, arm's-length compensation-setting through public boards and compensation committees, and continuous market pricing of their equity. Private companies typically lack some or all of these features, which creates specific valuation challenges:

- Financial statements may not be audited, or may be prepared primarily for tax minimization rather than economic accuracy.
- Owner compensation, related-party transactions, and personal expenses run through the business are common and require normalization.
- No observable market price exists, so discount rates, multiples, and control/marketability adjustments must be derived indirectly from public or transaction proxies.
- Capital structures are often simpler (less complex derivative instruments) but ownership structures can be more complex (family trusts, multiple classes with differing rights, buy-sell agreements).

### Category 1: Normalizing Adjustments to Financial Statements

**1. Owner Compensation Normalization**

Private company owners frequently set their own compensation at levels above or below fair market value for the role, for tax planning or personal preference reasons rather than reflecting what an arm's-length manager would be paid.

$$\text{Normalized EBITDA} = \text{Reported EBITDA} + (\text{Owner Compensation} - \text{Market-Rate Compensation for the Role})$$

If an owner draws $500,000 in salary and bonus but a market-rate general manager for a business of that size and complexity would command $250,000, EBITDA should be increased by $250,000 to reflect the true economic earning power available to a new owner who would need to pay only the market rate (or decreased, in the less common scenario where an owner is underpaid relative to market).

**2. Related-Party Transaction Adjustments**

- Above- or below-market rent paid to an entity owned by the same shareholder (a common structure where the operating company leases real estate from a related real estate holding entity) should be adjusted to reflect market rental rates.
- Above- or below-market pricing on transactions with other related entities (suppliers, customers, or service providers under common ownership) should be normalized to arm's-length terms.

**3. Discretionary and Personal Expenses**

Add-backs for expenses that reflect personal benefit to the owner rather than legitimate business operating costs — personal vehicle expenses, travel, family member salaries for non-working or under-working relatives, personal use of company assets, and similar items. Each add-back should be specifically identified and documented rather than applied as a blanket percentage, since aggressive or unsupported add-backs are a frequent point of dispute in transactions and disputes alike.

**4. Non-Recurring and One-Time Items**

- Litigation settlements, one-time restructuring costs, unusual gains/losses on asset sales, and similar non-operating or non-recurring items should be removed to arrive at a normalized, sustainable earnings base.
- Careful judgment is required to distinguish genuinely non-recurring items from recurring costs that merely appear infrequently but reflect an ongoing pattern of business risk (e.g., recurring litigation in a litigious industry may not be appropriate to fully add back).

**5. Accounting Method Normalization**

- Private companies sometimes use accounting methods selected for tax efficiency (e.g., cash-basis or modified cash-basis accounting, accelerated depreciation, LIFO inventory) that can distort period-to-period comparability or comparability to public company peers reporting on an accrual/GAAP basis; conversion to a consistent accrual basis is often necessary before applying market-derived multiples.

### Category 2: Discount Rate Adjustments

**1. Company-Specific Risk Premium (Build-Up Method)**

Because private companies generally lack a directly observable beta, a common approach (the "build-up method") constructs the cost of equity from additive components:

$$k_e = R_f + ERP + \text{Size Premium} + \text{Company-Specific Risk Premium} + \text{Industry Risk Premium (if used)}$$

Where the company-specific risk premium is a subjective adjustment intended to capture risks not otherwise reflected — including some of the same factors discussed in key person, concentration, and complexity discount analysis — added directly into the discount rate rather than as a standalone post-valuation discount. This is one of several places company-specific risk can be reflected, and as with other discount categories, care should be taken not to double-count the same risk elsewhere in the model.

**2. Size Premium**

Empirical research (e.g., data historically compiled in sources such as the Duff & Phelps/Kroll Cost of Capital data, building on earlier academic work including studies associated with Ibbotson/SBBI-style size decile analysis) has documented that smaller companies have historically exhibited higher returns (and by extension, are assigned higher required returns/discount rates) than larger companies, even after controlling for beta, a phenomenon commonly incorporated as an additive size premium in private company discount rate build-ups. [Unverified: the precise magnitude of size premiums by decile or size band changes as underlying datasets are updated, and the theoretical basis for why a size premium exists beyond what beta already captures remains subject to some academic debate; any specific size premium percentage should be sourced from a current, specific dataset rather than assumed static.]

**3. Private Company Illiquidity Premium in the Discount Rate (as an Alternative to a Separate DLOM)**

Some practitioners embed an illiquidity premium directly into the discount rate as an alternative to (rather than in addition to) applying a separate DLOM after the DCF calculation — this is a methodological choice that must be disclosed clearly, since applying both would double-count the same underlying risk.

### Category 3: Comparable Selection and Multiple Adjustments

**1. Private Company Discount When Using Public Comparables**

When no private company transaction data is available and public company multiples must be used as a proxy, a downward adjustment is often applied to reflect the private company discount — capturing some blend of DLOM, DLOC (if valuing a minority interest), size differences, and reduced analyst scrutiny relative to the public peer set — again requiring explicit disclosure of which specific risks the adjustment is meant to address to avoid overlap with separately-applied DLOC/DLOM discounts.

**2. Private Transaction Multiples**

Where available, multiples derived from private company M&A transactions (via databases such as GF Data, Pratt's Stats/DealStats, or similar private deal databases) provide a more directly comparable benchmark than public company multiples, though private transaction data is typically less transparent, less standardized in reporting, and has a smaller sample size than public market data.

**3. Size-Based Multiple Adjustments**

Smaller private companies (particularly those in the lower middle market) have empirically tended to transact at lower EV/EBITDA multiples than larger companies in the same industry, reflecting greater perceived risk, less management depth, and more limited strategic buyer interest; multiples derived from larger public peers or larger precedent transactions often require downward adjustment to be appropriately applied to a smaller private target.

### Category 4: Capital Structure and Ownership Structure Adjustments

**1. Normalizing to a Market-Based Capital Structure**

Private companies often have capital structures driven by owner preference, available financing, or tax planning rather than an optimal or industry-typical structure; WACC calculations frequently use a target/industry-typical capital structure rather than the company's actual (often idiosyncratic) structure.

**2. Adjusting for Non-Operating Assets and Liabilities**

Private companies frequently hold non-operating assets on the balance sheet (excess cash, real estate not used in operations, loans to shareholders, life insurance policies) that should be valued separately and added to (or liabilities subtracted from) the operating business valuation, rather than embedded within an EBITDA-multiple-based enterprise value that assumes only operating assets.

$$\text{Total Equity Value} = \text{Operating Enterprise Value} - \text{Debt} + \text{Non-Operating Assets} - \text{Non-Operating Liabilities}$$

**3. Multiple Classes of Equity and Special Rights**

Private companies (particularly venture-backed companies) often have multiple classes of preferred and common stock with differing liquidation preferences, conversion rights, anti-dilution provisions, and participation rights, requiring specialized allocation methodologies (discussed further under venture-backed company valuation topics) rather than a simple pro-rata equity value split.

### Category 5: Governance and Documentation-Related Adjustments

**1. Limited Financial Statement Reliability**

Unaudited or compiled (rather than audited or reviewed) financial statements carry higher inherent risk of misstatement; valuations relying on such statements should disclose this limitation and, where material, consider additional diligence or a wider valuation range to reflect this uncertainty.

**2. Governing Document Constraints**

Buy-sell agreements, shareholder agreements, and operating agreements may contain specific valuation formulas, restrictions on transfer, or mandatory valuation methodologies that override or constrain a purely market-based valuation approach — a private company valuation prepared for a specific contractual purpose (e.g., a triggering buyout event) must be reconciled against any such governing document provisions.

### Illustrative Consolidated Example

| Adjustment Category | Reported Figure | Adjustment | Normalized Figure |
| --- | --- | --- | --- |
| EBITDA (reported) | $3,200,000 |  |  |
| Owner compensation add-back |  | +$400,000 |  |
| Related-party rent adjustment (above-market rent paid) |  | +$150,000 |  |
| Personal vehicle/travel add-backs |  | +$60,000 |  |
| One-time litigation settlement add-back |  | +$200,000 |  |
| **Normalized EBITDA** |  |  | **$4,010,000** |

Applying a private-market-derived multiple of 5.5x (already reflecting a size-based downward adjustment from a larger public peer average of 7.5x) yields an operating enterprise value of approximately $22.06 million, before any subsequent DLOC/DLOM adjustments if a non-controlling or illiquid interest is being separately valued.

### Common Pitfalls

- **Aggressive or unsupported add-backs**: Add-backs that lack clear documentation or that reclassify genuinely necessary business expenses as "discretionary" invite scrutiny in transactions, disputes, and tax contexts alike.
- **Double-counting risk across the discount rate, multiples, and standalone discounts**: Applying a company-specific risk premium in the discount rate, a downward size/private-company adjustment to the multiple, and a separate post-valuation DLOM/DLOC without clear documentation of which specific risk each adjustment addresses.
- **Using public company multiples without any size or liquidity adjustment**: Directly applying a large-cap public peer multiple to a small private company without downward adjustment overstates value.
- **Failing to normalize accounting basis before applying market multiples**: Comparing a cash-basis private company's EBITDA to accrual-basis public peer multiples without conversion introduces a comparability error.
- **Ignoring governing document constraints**: Producing a pure fair-market-value analysis when the actual valuation purpose (e.g., a buy-sell trigger) is governed by a specific contractual formula that differs from open-market fair value.
- **Treating normalization as one-directional**: Assuming all adjustments increase EBITDA (add-backs); in some cases, normalization should decrease reported earnings (e.g., an underpaid owner, or a related party being charged below-market rates that would increase costs if normalized to arm's-length terms).

**Related Topics**

- Discount for Lack of Control (DLOC)
- Discount for Lack of Marketability (DLOM)
- Key Person and Concentration Discounts
- Company-Specific Risk Premium in the Build-Up Method
- Small Business and Professional Practice Valuation
- Venture-Backed Company Valuation and Liquidation Preferences
- Buy-Sell Agreement Valuation Mechanisms