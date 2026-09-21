## Arbitrage-Free Valuation Principles


### Core Concept

Arbitrage-free valuation is the principle that a financial instrument's price must be consistent with the prices of other instruments and rates observable in the market, such that no risk-free profit can be extracted by combining or decomposing the instrument's cash flows in alternative ways. In fixed income specifically, this means a bond should be valued as a **portfolio of individual zero-coupon cash flows**, each discounted at the spot rate matching its own maturity — any deviation from this consistent pricing creates a theoretical arbitrage opportunity that market forces should, in principle, eliminate.

### The Law of One Price

The foundational principle underlying arbitrage-free valuation is the **law of one price**: two identical cash flow streams (or portfolios that replicate one another exactly) must trade at the same price, regardless of how they are packaged or labeled. If two different combinations of instruments produce the exact same set of future cash flows but trade at different prices, an arbitrageur can buy the cheaper combination, sell the more expensive one, and lock in a riskless profit — a condition that cannot persist in a well-functioning, liquid market.

### Bonds as Portfolios of Zero-Coupon Bonds

The central application of arbitrage-free valuation to fixed income is recognizing that **any coupon-bearing bond is economically equivalent to a portfolio of individual zero-coupon bonds** — one zero-coupon bond maturing on each coupon date (sized to that coupon amount) plus one final zero-coupon bond maturing at par on the maturity date (sized to include both the final coupon and the principal).

$$P_{\text{bond}} = \sum_{t=1}^{n} CF_t \times DF(t)$$

This is identical in form to the spot curve valuation formula, but the arbitrage-free framing emphasizes *why* this must be the correct approach: if a bond's price differed from the sum of the prices of its constituent zero-coupon cash flows (valued individually using the actual, separately-observable prices of zero-coupon instruments of matching maturities), it would be possible to either strip and sell the bond's individual cash flows for more than the bond costs, or bundle equivalent zero-coupon instruments into a synthetic bond and sell it for more than it costs to assemble — either way, a riskless arbitrage.

### Historical Illustration: Treasury STRIPS

**[Verified — a real, well-documented market mechanism]** U.S. Treasury STRIPS (Separate Trading of Registered Interest and Principal of Securities) provide a direct, real-world illustration of this principle. A dealer can literally "strip" a coupon-bearing Treasury bond into its individual coupon and principal components, each trading as a separate zero-coupon instrument. If the sum of the market prices of a bond's individual STRIPS components diverges meaningfully from the price of the whole coupon bond, arbitrageurs can profit by either:

- **Stripping:** Buying the whole bond and selling its components separately (when components are collectively worth more than the whole bond), or
- **Reconstituting:** Buying the individual components and reassembling them into the whole bond (when the whole bond is worth more than the sum of its components)

This mechanism provides continuous market pressure keeping coupon bond prices consistent with the zero-coupon (spot) curve derived from their own components — a live, observable enforcement mechanism for the law of one price in fixed income markets.

### Diagram: Bond Decomposition Into Zero-Coupon Components (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 740 320" font-family="Arial, sans-serif">
<text x="370" y="24" text-anchor="middle" font-size="15" font-weight="bold">Arbitrage-Free Decomposition of a Coupon Bond (svg_diagram)</text>
<rect x="270" y="50" width="200" height="55" rx="6" fill="#e8f0fe" stroke="#1a5fb4" stroke-width="1.5" />
<text x="370" y="82" text-anchor="middle" font-size="13" font-weight="bold">3-Year Coupon Bond</text>
<line x1="370" y1="105" x2="370" y2="140" stroke="black" stroke-width="1.5" marker-end="url(#arrD)" />
<text x="400" y="125" font-size="11">"Strip" into components</text>
<rect x="60" y="150" width="180" height="55" rx="6" fill="#fdf0e8" stroke="#c0392b" stroke-width="1.5" />
<text x="150" y="172" text-anchor="middle" font-size="11">Zero-Coupon</text>
<text x="150" y="188" text-anchor="middle" font-size="11">Yr 1 Coupon (z₁)</text>
<rect x="280" y="150" width="180" height="55" rx="6" fill="#fdf0e8" stroke="#c0392b" stroke-width="1.5" />
<text x="370" y="172" text-anchor="middle" font-size="11">Zero-Coupon</text>
<text x="370" y="188" text-anchor="middle" font-size="11">Yr 2 Coupon (z₂)</text>
<rect x="500" y="150" width="180" height="55" rx="6" fill="#fdf0e8" stroke="#c0392b" stroke-width="1.5" />
<text x="590" y="172" text-anchor="middle" font-size="11">Zero-Coupon</text>
<text x="590" y="188" text-anchor="middle" font-size="11">Yr 3 + Principal (z₃)</text>
<rect x="220" y="240" width="300" height="55" rx="6" fill="#eef7ee" stroke="#27ae60" stroke-width="2" />
<text x="370" y="262" text-anchor="middle" font-size="12" font-weight="bold">Sum of component prices</text>
<text x="370" y="280" text-anchor="middle" font-size="11">MUST equal original bond price (no-arbitrage)</text>
</svg>

### Additive Valuation and Value Preservation

A core corollary of arbitrage-free pricing is that **value is additive**: the value of a portfolio of separate cash flows equals the sum of the individual present values of each cash flow, and, conversely, the value of any single security should equal the sum of the present values of the individual cash flows it comprises. This additivity property is what permits the "bond as portfolio of zeros" decomposition and is the same principle that underlies forward rate consistency (covered under spot versus forward rates) — the entire spot curve itself must be internally arbitrage-free before it is useful as a valuation tool, since inconsistent spot rates would themselves imply arbitrage across different maturities.

### The Role of the No-Arbitrage Assumption in Model Building

Arbitrage-free principles extend beyond simple bond pricing into more advanced fixed income modeling contexts:

| Application | How Arbitrage-Free Logic Applies |
| --- | --- |
| Binomial interest rate trees (for option-adjusted valuation) | Constructed so that the tree, when used to price the benchmark bonds used to calibrate it, exactly reproduces their observed market prices — ensuring the tree itself is arbitrage-free relative to the input curve |
| Forward rate derivation | Forward rates are derived precisely so that investing at the spot rate for a longer period yields an identical result to investing at the spot rate for a shorter period and reinvesting at the implied forward rate — a direct application of no-arbitrage |
| Swap and derivative pricing | Discounting and valuation curves used for derivatives must be arbitrage-consistent with the underlying cash bond and money market curves, particularly in the modern multi-curve framework |
| Bond futures and cash-and-carry arbitrage | The theoretical futures price is derived from the no-arbitrage relationship between the cash bond price, financing cost, and coupon income earned over the delivery period |

### Limits and Practical Caveats to Pure Arbitrage-Free Theory

**[Inference]** While arbitrage-free valuation provides the theoretically correct framework, real-world markets exhibit persistent, non-trivial deviations from perfectly arbitrage-free pricing due to several practical frictions:

- **Transaction costs:** Bid-ask spreads and trading costs can make theoretically identifiable arbitrage opportunities unprofitable to actually execute.
- **Financing costs and constraints:** Exploiting an arbitrage typically requires financing (e.g., via repo markets), and financing costs, availability, or balance-sheet constraints on market participants can prevent theoretical arbitrages from being fully closed.
- **Liquidity differences:** Two instruments with theoretically identical cash flows may still trade at different prices if one is significantly more or less liquid than the other, reflecting a genuine liquidity premium rather than a pure arbitrage.
- **Tax and regulatory differences:** Different tax treatments or regulatory capital requirements across instruments or investor types can justify persistent price differences that are not true arbitrage opportunities once these frictions are accounted for.

[Unverified as a precise quantitative claim] The exact magnitude of typical persistent deviations from pure arbitrage-free pricing varies significantly by market, time period, and instrument liquidity, and is not something that can be stated as a single general figure.

### Why This Principle Matters for Practitioners

- **Curve construction validation:** A properly bootstrapped spot curve should be internally arbitrage-free by construction — testing this (e.g., verifying no negative or economically implausible discount factors) is a standard sanity check.
- **Relative value identification:** Deviations from arbitrage-free pricing (after accounting for reasonable transaction costs, liquidity, and financing frictions) are the basis for genuine relative value trading strategies, distinguishing a real opportunity from a mere accounting artifact.
- **Model risk awareness:** Any valuation model (option-adjusted spread models, binomial trees, swap curve construction) that is not calibrated to be arbitrage-free relative to its own input instruments will produce systematically unreliable outputs when used for pricing or risk purposes.

### Key Points

- Arbitrage-free valuation rests on the law of one price: identical cash flow streams must be priced identically regardless of how they are packaged.
- A coupon bond can be decomposed into a portfolio of individual zero-coupon cash flows, each discounted at its maturity-matched spot rate; the sum must equal the bond's price under no-arbitrage.
- Treasury STRIPS provide a real, observable market mechanism (stripping and reconstitution) that enforces this consistency between coupon bonds and their zero-coupon components.
- Arbitrage-free logic extends into forward rate derivation, binomial tree calibration, swap curve construction, and futures pricing — it is a foundational principle across virtually all fixed income valuation techniques, not a standalone bond-pricing rule.
- Real-world markets exhibit persistent, non-arbitrage deviations due to transaction costs, financing constraints, liquidity differences, and tax/regulatory factors — pure arbitrage-free theory is the benchmark, not a literal description of all observed prices at all times.

**Related Topics**

- Discount Factors and Zero-Coupon Rates
- Valuation Using the Spot Curve
- Treasury STRIPS: Mechanics of Stripping and Reconstitution
- Binomial Interest Rate Trees and Model Calibration
- Bond Futures Pricing and Cash-and-Carry Arbitrage
- Repo Markets and Financing Costs in Arbitrage Strategies