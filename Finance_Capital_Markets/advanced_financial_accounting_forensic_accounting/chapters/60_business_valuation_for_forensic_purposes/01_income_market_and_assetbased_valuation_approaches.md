## Income, Market, and Asset-Based Valuation Approaches


### Overview

Business valuation for forensic purposes relies on three generally recognized approaches — income, market, and asset-based — each grounded in a distinct economic theory of value. Forensic accountants and business valuators select among (or reconcile across) these approaches based on the nature of the business being valued, the purpose and standard of value applicable to the engagement (fair value, fair market value, investment value), the availability and reliability of data, and the specific legal or dispute context (divorce, shareholder dispute, damages, estate/gift tax, bankruptcy).

### The Three Approaches: Conceptual Foundation

**Key Points**

- **Income approach**: Value is a function of the present value of expected future economic benefits (cash flows or earnings) the business will generate
- **Market approach**: Value is derived by reference to actual transactions or pricing multiples observed for comparable businesses or business interests
- **Asset-based approach**: Value is derived from the fair value of the entity's underlying assets less its liabilities, reflecting the business as a collection of net assets rather than an ongoing income-generating enterprise

```mermaid
flowchart TD
    A[Determine Standard & Premise of Value] --> B{Select Applicable Approach(es)}
    B --> C[Income Approach]
    B --> D[Market Approach]
    B --> E[Asset-Based Approach]
    C --> C1[Discounted Cash Flow Method]
    C --> C2[Capitalization of Earnings/Cash Flow Method]
    D --> D1[Guideline Public Company Method]
    D --> D2[Guideline Transaction Method]
    E --> E1[Adjusted Net Asset Method]
    E --> E2[Liquidation Value Method]
    C1 --> F[Reconcile Indicated Values]
    C2 --> F
    D1 --> F
    D2 --> F
    E1 --> F
    E2 --> F
    F --> G[Apply Discounts/Premiums as Appropriate]
    G --> H[Conclude Value]
```

### The Income Approach

#### Discounted Cash Flow (DCF) Method

- Projects the business's expected future free cash flows over an explicit forecast period, plus a terminal value representing cash flows beyond that period, then discounts both to present value using a risk-appropriate discount rate

$$V = \sum_{t=1}^{n} \frac{FCF_t}{(1+r)^t} + \frac{TV_n}{(1+r)^n}$$

where terminal value is typically calculated using the Gordon Growth Model:

$$TV_n = \frac{FCF_{n+1}}{(r-g)}$$

**Key Points**

- The discount rate $r$ is often derived from the Weighted Average Cost of Capital (WACC) for enterprise-level valuations, or the cost of equity (via the Capital Asset Pricing Model or a build-up method) for equity-level valuations
- Free cash flow projections should reflect normalized, sustainable operating performance, with adjustments for non-recurring items, owner compensation normalization (particularly relevant in closely held business valuations), and non-operating assets/liabilities

#### Capitalization of Earnings/Cash Flow Method

- A simplified variant of the DCF, appropriate when the business is expected to grow at a single, stable long-term rate rather than requiring a multi-year explicit projection

$$V = \frac{CF_1}{(r-g)}$$

- Most appropriate for stable, mature businesses without significant anticipated changes in growth trajectory or capital structure

[Inference] The capitalization method is generally viewed as more appropriate for stable businesses precisely because it collapses the multi-period DCF into a single capitalization rate and growth assumption; where near-term performance is expected to differ meaningfully from a long-term steady state, the multi-period DCF is typically preferred to avoid distorting value through an oversimplified single-period model.

### The Market Approach

#### Guideline Public Company Method

- Derives valuation multiples (e.g., EV/EBITDA, Price/Earnings, EV/Revenue) from the trading prices of comparable publicly traded companies, then applies those multiples to the subject company's financial metrics

$$V = \text{Subject Company Metric} \times \text{Guideline Multiple}$$

**Key Points**

- Requires careful selection of truly comparable companies (industry, size, growth profile, risk characteristics)
- Multiples derived from public companies typically require adjustment (e.g., a discount for lack of marketability) when applied to closely held/private companies, given the inherent liquidity differences

#### Guideline Transaction Method

- Uses actual acquisition transaction data for comparable companies (private or public) to derive pricing multiples, rather than public trading multiples

**Key Points**

- Transaction multiples often already embed a control premium (since acquisitions typically involve a change of control), which must be considered when valuing a minority, non-controlling interest
- Data availability and comparability can be more limited than for guideline public companies, particularly for smaller private-company transactions

### The Asset-Based Approach

#### Adjusted Net Asset Method

- Restates the business's balance sheet to fair value (rather than historical cost/book value) for each asset and liability, with the difference representing the indicated equity value

$$V_{equity} = \text{Fair Value of Assets} - \text{Fair Value of Liabilities}$$

**Key Points**

- Requires appraisal of individual asset categories (real estate, equipment, intangible assets, inventory) which may differ substantially from book value
- Most appropriate for asset-holding companies, real estate entities, investment holding companies, or businesses with minimal ongoing operating earnings (where income-based value would understate true worth)
- Generally considered a value floor for an operating business, since a rational owner would not continue operating (or sell) a business for less than its net asset value in liquidation, absent other constraints

#### Liquidation Value Method

- Estimates the net proceeds available to owners if all assets were sold and liabilities settled, under either orderly liquidation (reasonable time to sell) or forced liquidation (immediate sale) assumptions

**Key Points**

- Forced liquidation values are typically materially lower than orderly liquidation values due to compressed sale timelines and reduced buyer pools
- Most relevant in bankruptcy, insolvency, or dissolution contexts rather than as a primary approach for going-concern businesses

### Approach Selection Considerations

| Business Characteristic | Approach(es) Most Likely Relevant |
| --- | --- |
| Established, profitable operating company | Income approach (primary), Market approach (corroborating) |
| Early-stage/pre-revenue company | Market approach (comparable transactions), asset-based (limited utility) |
| Asset-holding/real estate entity | Asset-based approach (primary) |
| Company in financial distress/near insolvency | Asset-based (liquidation value), income approach with distress-adjusted assumptions |
| Company with abundant public comparables | Market approach (guideline public company) |
| Recently sold/acquired comparable companies available | Market approach (guideline transaction method) |

[Inference] While professional valuation standards generally recommend considering all three approaches and reconciling the results, practical application often weights one approach as primary based on the specific facts, with the others serving a corroborative or reasonableness-check function; the appropriate weighting is a matter of professional judgment applied to the specific engagement.

### Reconciling Multiple Approaches

**Key Points**

- Where more than one approach produces a reliable indication of value, professional standards generally require reconciliation rather than mechanical averaging
- Reconciliation should consider the relative reliability of each approach's underlying data and assumptions given the specific facts of the subject company, not simply split the difference between methods
- Significant divergence between approach-indicated values often signals a data or assumption issue warranting further investigation before finalizing a conclusion

### Standard and Premise of Value: Foundational Prerequisites

| Concept | Description |
| --- | --- |
| **Standard of value** | The type of value being measured — fair market value (hypothetical willing buyer/seller), fair value (often statutorily defined for shareholder disputes), investment value (value to a specific buyer), intrinsic value |
| **Premise of value** | The underlying assumption about the business's use — going concern vs. liquidation |

[Unverified] The applicable standard of value in forensic and litigation contexts is frequently dictated by statute or case law specific to the type of proceeding (e.g., many U.S. states apply a "fair value" standard distinct from fair market value in shareholder oppression/dissent cases), and can vary significantly by jurisdiction; the correct standard should be confirmed with counsel before selecting valuation methodology.

### Discounts and Premiums Applied After Approach-Level Value

**Key Points**

- **Discount for Lack of Control (DLOC)**: Applied when valuing a non-controlling interest, reflecting the inability to direct company decisions
- **Discount for Lack of Marketability (DLOM)**: Applied to reflect the reduced liquidity of an interest in a privately held company compared to a freely tradable public security
- **Control premium**: The inverse of DLOC, applied when converting a minority-interest-derived value (e.g., from guideline public company data) to a controlling-interest value
- These discounts/premiums are applied after the base approach-level value is determined and are themselves frequently contested elements in forensic valuation disputes

### Common Analytical Pitfalls

**Key Points**

- Applying public company or transaction multiples without adequate comparability adjustment for size, growth, and risk differences
- Failing to normalize earnings for owner compensation, related-party transactions, or non-recurring items in closely held business valuations
- Mechanically averaging results from multiple approaches rather than performing a reasoned reconciliation
- Misapplying discounts/premiums (e.g., applying both a control premium and treating the result as already representing a minority interest)
- Using an asset-based approach for a profitable operating business where the approach may understate true going-concern value, without adequate justification

### Illustrative Approach Reconciliation

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 850 260" font-family="Arial, sans-serif">
<text x="425" y="22" font-size="16" font-weight="bold" text-anchor="middle">Valuation Approach Reconciliation (svg_diagram)</text>
<rect x="60" y="60" width="200" height="60" fill="#e8f0fe" stroke="#4285f4" />
<text x="160" y="85" font-size="11" text-anchor="middle">Income Approach</text>
<text x="160" y="100" font-size="11" font-weight="bold" text-anchor="middle">$8.2M</text>
<rect x="320" y="60" width="200" height="60" fill="#fef7e0" stroke="#fbbc04" />
<text x="420" y="85" font-size="11" text-anchor="middle">Market Approach</text>
<text x="420" y="100" font-size="11" font-weight="bold" text-anchor="middle">$7.8M</text>
<rect x="580" y="60" width="200" height="60" fill="#e6f4ea" stroke="#34a853" />
<text x="680" y="85" font-size="11" text-anchor="middle">Asset Approach</text>
<text x="680" y="100" font-size="11" font-weight="bold" text-anchor="middle">$5.1M (floor)</text>
<line x1="160" y1="120" x2="380" y2="180" stroke="gray" stroke-dasharray="3" />
<line x1="420" y1="120" x2="400" y2="180" stroke="gray" stroke-dasharray="3" />
<line x1="680" y1="120" x2="420" y2="180" stroke="gray" stroke-dasharray="3" />
<rect x="300" y="180" width="200" height="50" fill="#f3e8fd" stroke="#a142f4" />
<text x="400" y="200" font-size="10" text-anchor="middle">Reconciled Value</text>
<text x="400" y="215" font-size="11" font-weight="bold" text-anchor="middle">≈ $8.0M</text>
</svg>

### Conclusion

Income, market, and asset-based valuation approaches provide complementary lenses for estimating business value, each resting on a distinct economic rationale — earning power, market-observed pricing, and net asset worth, respectively. Effective forensic valuation practice requires matching the selected approach(es) to the specific characteristics of the subject business, the applicable standard and premise of value, and the quality of available data, followed by a reasoned reconciliation rather than mechanical averaging when multiple approaches yield differing indications. Because approach selection, normalization adjustments, and subsequent discounts/premiums are frequently the focus of opposing expert critique, transparent documentation of the rationale behind each methodological choice is essential to a defensible valuation conclusion.

**Related Topics**

- Discounted cash flow modeling and terminal value estimation in depth
- Discount for lack of marketability (DLOM) quantification methods
- Discount for lack of control and control premium studies
- Earnings normalization adjustments in closely held business valuations
- Guideline public company and transaction multiple selection criteria
- Standard of value and premise of value determination by proceeding type
- Business valuation in divorce and shareholder dispute contexts
- Weighted average cost of capital and build-up method discount rate derivation
- Rebuttal analysis and critique of opposing valuation reports
- Valuation standards (AICPA SSVS, ASA, NACVA, USPAP) and compliance requirements