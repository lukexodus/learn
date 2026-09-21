## Funding Levels and Issuer Economics

### Overview

Funding level and issuer economics describe how an issuer of structured products (typically a bank or broker-dealer) prices, hedges, and profits from a note. The "funding level" is the internal cost (or benefit) the issuer's treasury desk assigns to raising money via structured note issuance relative to its standard unsecured borrowing curve. This spread — between structured note funding and vanilla senior unsecured debt — is a primary, and often underappreciated, driver of investor payoff economics.

### The Issuer as a Borrower

When an issuer sells a structured note, it is economically equivalent to:

1. Issuing a zero-coupon or coupon-bearing bond to the investor
2. Simultaneously entering a derivative (option, swap) with an internal trading desk to create the payoff

$$\text{Note Proceeds} = \text{Bond Component (PV)} + \text{Derivative Premium (funded internally)}$$

The issuer's treasury function treats the note as a funding source. Because structured notes are typically less liquid and harder to hedge/replicate for the investor than a plain bond, issuers can often raise funds at a rate *cheaper* than their standard unsecured curve — this saved cost is the "funding spread" or "funding benefit."

### Funding Curve vs. Secondary Market Curve

Two distinct curves matter:

- **Issuance (funding) curve**: The rate the issuer credits internally when a note is issued — used for initial pricing
- **Secondary (trading) curve**: The rate used by the desk to mark-to-market and unwind outstanding notes

These curves diverge, particularly post-2008, since regulators require issuers to disclose this. A widening funding spread between issuance and secondary curves at trade date directly reduces the economic value delivered to the investor, even at "par."

**Example:**

An issuer's 5-year senior unsecured bonds trade at SOFR + 60 bps. For a 5-year structured note, the treasury desk credits the structuring desk funding at SOFR + 130 bps (i.e., the issuer treats the note as cheaper financing). This 70 bps differential is retained as issuer economics — it does not flow to the investor's payoff.

### Components of Issuer Economics

**Key Points**

- **Funding spread capture**: Difference between the note's assumed funding rate and the issuer's actual cost of vanilla debt
- **Structuring margin**: Markup embedded in the option/derivative pricing beyond fair (mid-market) value
- **Hedging cost/slippage**: Bid-offer paid when the desk executes offsetting hedges in the market (vol surface, rates, correlation)
- **Distribution fee**: Compensation paid to selling agents/brokers, often 1–3% for retail-distributed notes, embedded in issue price
- **Ongoing hedging P&L**: Residual gains/losses from dynamic hedging over the note's life (gamma, vega, correlation drift)

### Fair Value vs. Issue Price

$$\text{Issue Price} = \text{Fair Value (Bond + Derivative)} - \text{Funding Spread PV} + \text{Fees and Margin}$$

Where:

- **Fair Value**: What the bond-plus-option package is worth using market-observable curves and mid-market vol/correlation
- **Funding Spread PV**: Present value of the difference between issuer's actual funding cost and the elevated internal funding rate used to price the note (this *increases* issuer profit, and is disclosed in US offering documents as the "estimated value" gap)
- **Fees/Margin**: Distribution and structuring markup

Regulatory disclosure (e.g., under FINRA guidance in the US) requires issuers to publish an "estimated value" on the cover page of prospectus supplements, distinct from the public offering price — the gap between these two numbers is largely attributable to funding spread and fees.

### Worked Numerical Example

A 3-year autocallable note on a single stock:

| Component | Value |
| --- | --- |
| Public Offering Price | $1,000.00 |
| Fair Value of Bond Component (issuer's actual curve) | $850.00 |
| Fair Value of Embedded Options (mid-market vol) | $110.00 |
| **Sum (true economic fair value)** | **$960.00** |
| Distribution Fee | $25.00 |
| Structuring Margin | $10.00 |
| Funding Spread Benefit to Issuer | $5.00 |
| **Estimated Value (disclosed)** | **$960.00** |
| **Issuer's Embedded Economics** | **$40.00 (4.0%)** |

[Inference] The exact bond-component discount rate used by any specific issuer for internal funding is proprietary and not publicly disclosed with precision; the disclosed "estimated value" is a range-bound approximation, typically produced by an internal model validated against a third-party or independent pricing function.

### Why Funding Level Matters for Investors

- A higher assumed funding rate (issuer benefit) means a **lower bond floor**, which mechanically requires **richer optionality** (higher coupons, lower barriers) to keep the note at par — so funding levels indirectly shape headline terms
- Notes from issuers with wider credit spreads (weaker credit, higher funding cost) can offer more attractive headline coupons purely from the bond discount, *not* from superior derivative structuring — an investor must disentangle credit risk from real optionality value
- Funding spread advantage tends to be larger for structured notes than plain vanilla bonds because of reduced investor price transparency and limited secondary liquidity, which reduces competitive pressure on pricing

### Funding Level and Product Design Interaction

Issuers actively use funding spread as a lever in product design:

- **Callable notes**: Issuer's call option effectively lets them refinance if funding levels move in their favor — embedded call optionality has value tied to funding curve volatility, not just rates
- **Long-dated notes**: Funding benefit compounds over tenor, making 10–30 year notes disproportionately profitable from the funding line alone, independent of derivative margin
- **Principal-protected notes**: The zero-coupon bond floor is the dominant component; funding spread on this large bond position is often the single largest profit source, dwarfing option structuring margin

### Diagram: Issue Price Waterfall (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 760 420">
\<style\>
.lbl { font-family: sans-serif; font-size: 13px; fill: #1a1a1a; }
.val { font-family: sans-serif; font-size: 12px; fill: #444; }
.title { font-family: sans-serif; font-size: 15px; font-weight: bold; fill: #111; }
\</style\>
<text x="20" y="25" class="title">Issue Price Waterfall (svg_diagram)</text>
<rect x="40" y="60" width="120" height="300" fill="#4a7fb5" />
<text x="45" y="210" class="lbl" fill="white">Bond</text>
<text x="45" y="226" class="lbl" fill="white">Component</text>
<text x="45" y="245" class="val" fill="white">$850</text>
<rect x="180" y="240" width="120" height="120" fill="#6fa8dc" />
<text x="185" y="295" class="lbl" fill="white">Options</text>
<text x="185" y="311" class="val" fill="white">$110</text>
<rect x="320" y="205" width="120" height="35" fill="#e69138" />
<text x="325" y="228" class="val" fill="white">Distribution $25</text>
<rect x="320" y="240" width="120" height="20" fill="#f1c232" />
<text x="325" y="255" class="val" fill="#333">Structuring $10</text>
<rect x="320" y="260" width="120" height="15" fill="#93c47d" />
<text x="325" y="272" class="val" fill="#333">Funding Bfn $5</text>
<rect x="460" y="60" width="120" height="300" fill="#38761d" />
<text x="465" y="205" class="lbl" fill="white">Public</text>
<text x="465" y="221" class="lbl" fill="white">Offer</text>
<text x="465" y="240" class="val" fill="white">$1000</text>
<line x1="160" y1="360" x2="180" y2="360" stroke="#333" stroke-width="1.5" />
<line x1="300" y1="360" x2="320" y2="360" stroke="#333" stroke-width="1.5" />
<line x1="440" y1="275" x2="460" y2="275" stroke="#333" stroke-width="1.5" />
<text x="600" y="230" class="val">Sum = $1000</text>
<text x="600" y="248" class="val">(par issuance)</text>

<text x="40" y="400" class="val">Fair Value = $960 | Issuer Economics = $40 (4.0%)</text>

</svg>

### Regulatory and Disclosure Context

- **US**: FINRA Regulatory Notice 12-03 requires member firms to disclose "estimated value" for structured products distinct from offer price
- **EU/UK**: PRIIPs KID regulation mandates cost disclosure including "entry costs," which functionally captures similar embedded margin
- [Unverified] The precise methodology (e.g., specific discount curve source, vol surface provider) used to compute "estimated value" varies by issuer and is not uniformly standardized across the industry, though third-party model validation is common practice

### Practical Implications for Analysis

- Always compare an issuer's disclosed "estimated value" to the offer price when evaluating a note — the gap is a direct, quantifiable measure of embedded issuer economics
- Compare coupon/barrier terms across issuers with similar credit ratings to isolate structuring competitiveness from credit-driven funding differences
- Longer-dated and principal-protected structures warrant closer scrutiny of the bond floor discount rate, since funding spread economics scale with duration and notional held in the bond component
- Behavior of issuer funding spreads can shift with credit cycles, issuer-specific credit events, and structured note market volume — disclosed estimated values and embedded costs may not be static across time or across an issuer's own note families

### Related Topics

- Bond floor construction and discount curve selection
- FINRA 12-03 and PRIIPs KID disclosure frameworks
- Credit spread risk in structured note valuation (issuer default risk)
- Secondary market bid-offer and note liquidation mechanics
- Autocallable note structuring and coupon barrier design
- Dynamic hedging P&L attribution (gamma/vega/correlation)