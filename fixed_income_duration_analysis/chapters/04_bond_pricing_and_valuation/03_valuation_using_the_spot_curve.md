## Valuation Using the Spot Curve

### Core Concept

Spot curve (or zero-curve) valuation prices a bond by discounting each individual cash flow at the spot rate specifically matched to its own maturity, rather than applying a single blended yield to maturity (YTM) across every cash flow. This method produces a theoretically more precise, arbitrage-consistent valuation whenever the term structure of interest rates is not flat — which is the normal, real-world condition — and forms the analytical foundation for identifying relative value mispricing between bonds.

### Why Spot Curve Valuation Differs From Standard YTM-Based Pricing

The standard bond pricing formula discounts every cash flow — near-term and far-term alike — at the same single rate $y$ (the bond's own YTM). This is a convenient simplification, but it implicitly treats a coupon received in 6 months and a coupon received in 9 years as deserving the identical discount rate, which is inconsistent with the reality that short-term and long-term money generally carry different required returns. Spot curve valuation removes this simplification by applying a maturity-specific rate to each cash flow individually.

$$P_{\text{spot curve}} = \sum_{t=1}^{n} \frac{CF_t}{(1+z_t)^t}$$

Where $z_t$ is the zero-coupon (spot) rate specific to maturity $t$, and $CF_t$ is the cash flow due at time $t$ (coupon, or coupon plus principal at final maturity).

### Step-by-Step Valuation Process

**Step 1 — Obtain (or bootstrap) the spot curve** for all relevant maturities matching the bond's cash flow dates (see discount factor/zero rate construction methodology).

**Step 2 — Identify each individual cash flow** and its exact payment date/maturity.

**Step 3 — Discount each cash flow at its own maturity-matched spot rate** — not a single blended rate.

**Step 4 — Sum all discounted cash flows** to arrive at the theoretical (arbitrage-free) spot-curve-implied price.

### Worked Example

**Given:** A 3-year bond, $1,000 face value, 6% annual coupon, and the following spot curve:

| Maturity | Spot Rate |
| --- | --- |
| 1 year | 4.00% |
| 2 years | 4.52% |
| 3 years | 5.00% |

**Cash flows:** $60 (Year 1), $60 (Year 2), $1,060 (Year 3)

**Step-by-step discounting:**

$$PV_1 = \frac{60}{(1.04)^1} = 57.69$$



$$PV_2 = \frac{60}{(1.0452)^2} = 54.95$$



$$PV_3 = \frac{1060}{(1.05)^3} = 915.85$$



$$P_{\text{spot curve}} = 57.69 + 54.95 + 915.85 = \$1{,}028.49$$

### Comparing Against a Single-Yield (YTM) Approximation

If instead this same bond were priced using a single flat YTM — say the market observes this exact bond trading at $1,028.49 and solves for its implied YTM — that single YTM figure would necessarily sit *somewhere between* the underlying 1-year, 2-year, and 3-year spot rates, acting as a cash-flow-weighted blend of them. **[Inference]** The precise blended YTM depends on the cash flow timing and size distribution of that specific bond, meaning two bonds with different coupon structures but the same maturity can have different YTMs even when priced off the identical underlying spot curve — a key reason spot curve valuation is considered more analytically rigorous than YTM comparison for relative value purposes.

### Diagram: Single-Yield vs. Spot Curve Discounting (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 740 320" font-family="Arial, sans-serif">
<text x="370" y="24" text-anchor="middle" font-size="15" font-weight="bold">Single YTM Discounting vs. Spot Curve Discounting (svg_diagram)</text>

<text x="200" y="55" text-anchor="middle" font-size="13" font-weight="bold" fill="`#1a5fb4`">Standard YTM Approach</text>

<line x1="70" y1="100" x2="70" y2="140" stroke="black" stroke-width="1.5" />

<text x="70" y="155" text-anchor="middle" font-size="10">Yr 1: $60</text>

<line x1="70" y1="100" x2="330" y2="100" stroke="`#1a5fb4`" stroke-width="2" stroke-dasharray="4,3" />

<text x="200" y="90" text-anchor="middle" font-size="10" fill="`#1a5fb4`">Discount ALL at same y</text>

<line x1="200" y1="100" x2="200" y2="140" stroke="black" stroke-width="1.5" />

<text x="200" y="155" text-anchor="middle" font-size="10">Yr 2: $60</text>

<line x1="330" y1="100" x2="330" y2="140" stroke="black" stroke-width="1.5" />

<text x="330" y="155" text-anchor="middle" font-size="10">Yr 3: $1,060</text>

<text x="550" y="55" text-anchor="middle" font-size="13" font-weight="bold" fill="`#c0392b`">Spot Curve Approach</text>

<line x1="420" y1="100" x2="420" y2="140" stroke="black" stroke-width="1.5" />

<text x="420" y="155" text-anchor="middle" font-size="10">Yr 1: $60</text>

<text x="420" y="115" text-anchor="middle" font-size="9" fill="`#c0392b`">z₁=4.00%</text>

<line x1="550" y1="100" x2="550" y2="140" stroke="black" stroke-width="1.5" />
<text x="550" y="155" text-anchor="middle" font-size="10">Yr 2: $60</text>
<text x="550" y="115" text-anchor="middle" font-size="9" fill="#c0392b">z₂=4.52%</text>
<line x1="680" y1="100" x2="680" y2="140" stroke="black" stroke-width="1.5" />
<text x="680" y="155" text-anchor="middle" font-size="10">Yr 3: $1,060</text>
<text x="680" y="115" text-anchor="middle" font-size="9" fill="#c0392b">z₃=5.00%</text>
<rect x="150" y="200" width="440" height="70" rx="6" fill="#eef7ee" stroke="#27ae60" stroke-width="2" />
<text x="370" y="228" text-anchor="middle" font-size="12" font-weight="bold">Both sum to the same total price ($1,028.49)</text>
<text x="370" y="248" text-anchor="middle" font-size="11">but spot curve pricing is the more rigorous, decomposable method</text>
</svg>

### Identifying Relative Value: Rich/Cheap Analysis

**Core application:** By computing a bond's theoretical price off the spot curve (built from *other* liquid benchmark bonds) and comparing it to the bond's actual observed market price, an analyst can determine whether the specific bond is trading rich (overpriced) or cheap (underpriced) relative to the broader curve.

| Comparison Result | Interpretation |
| --- | --- |
| Market price > Spot-curve theoretical price | Bond is trading "rich" (expensive) relative to the curve — commands a lower yield than curve-implied fair value |
| Market price < Spot-curve theoretical price | Bond is trading "cheap" (inexpensive) relative to the curve — offers a higher yield than curve-implied fair value |
| Market price ≈ Spot-curve theoretical price | Bond is fairly valued relative to the curve |

**[Inference]** In practice, small persistent deviations between market price and spot-curve theoretical price are common and can reflect genuine liquidity differences, specific supply/demand technical factors, tax treatment differences, or idiosyncratic credit considerations — not necessarily an exploitable arbitrage opportunity, since transaction costs and financing considerations can absorb small theoretical mispricings.

### Z-Spread: Quantifying the Deviation

The **zero-volatility spread (Z-spread)** is the constant spread that, when added uniformly to every point on the benchmark spot curve, makes the discounted cash flows of a bond exactly equal its observed market price.

$$P_{\text{market}} = \sum_{t=1}^{n} \frac{CF_t}{(1+z_t+Z)^t}$$

Where $Z$ is the Z-spread, solved for iteratively (or via a root-finding method) such that the equation holds exactly.

**Interpretation:** A larger Z-spread indicates the bond requires a greater compensation (over the risk-free/benchmark curve) to justify its market price — commonly interpreted as reflecting the bond's credit risk, liquidity risk, and any embedded structural features not otherwise captured by the base curve, though the Z-spread itself does not decompose these components individually.

### Extending to Bonds With Embedded Options

**[Verified — standard extension]** For bonds with embedded options (callable, putable), spot curve valuation alone is insufficient, since it assumes fixed, certain cash flows. These require an **option-adjusted spread (OAS)** framework, which models multiple possible interest rate paths (typically via a binomial or trinomial interest rate tree calibrated to the spot curve) and accounts for the probability-weighted effect of the embedded option being exercised under different rate scenarios. The OAS is conceptually the Z-spread adjusted to remove the value attributable to optionality, isolating the "pure" credit/liquidity spread component.

### Practical Applications Beyond Individual Bond Pricing

- **New issue pricing:** Underwriters use spot-curve-implied pricing (adjusted for an appropriate new-issue spread) as the starting framework for setting coupon and price on newly issued bonds.
- **Portfolio-level relative value screening:** Systematically comparing many bonds' Z-spreads against a common benchmark curve to identify the richest/cheapest names within a sector or credit tier.
- **Derivatives and structured product valuation:** Spot-curve-based discounting is the standard foundation for valuing swaps, forward rate agreements, and other cash-flow-based instruments, extending well beyond plain bond pricing.

### Key Points

- Spot curve valuation discounts each individual cash flow at its own maturity-matched spot rate, rather than a single blended YTM applied uniformly to all cash flows.
- This method is more theoretically rigorous when the yield curve is not flat, and forms the basis for identifying rich/cheap relative value between bonds.
- The Z-spread quantifies the constant spread over the benchmark spot curve required to exactly match a bond's observed market price, commonly interpreted as compensation for credit and liquidity risk.
- Bonds with embedded options require the further extension to an option-adjusted spread (OAS) framework, since simple spot curve discounting assumes certain, fixed cash flows.
- Spot curve-based discounting underlies not just individual bond valuation but also swap pricing, new issue pricing, and portfolio-level relative value analysis.

**Related Topics**

- Discount Factors and Zero-Coupon Rates
- Z-Spread and Option-Adjusted Spread (OAS) Calculation
- Option-Adjusted Spread and Binomial Interest Rate Trees
- Constructing a Discount Curve
- Relative Value Analysis and Rich/Cheap Bond Screening
- Credit Spread Decomposition and Liquidity Premium Estimation