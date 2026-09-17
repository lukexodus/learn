## Discount Factors and Zero-Coupon Rates

### Core Concept

Discount factors and zero-coupon rates form the mathematical foundation for valuing *any* fixed income cash flow with full rigor — replacing the simplifying assumption of a single flat yield applied to every cash flow with a more precise framework in which each individual cash flow is discounted at the rate specifically applicable to its own maturity. This distinction becomes essential once the yield curve is not flat (the normal, real-world case), since a single YTM figure is only an approximation that blends together multiple different "true" period-specific discount rates.

### Discount Factors

**Definition:** A discount factor $DF(t)$ is the present value today of $1 to be received at time $t$, given the term structure of interest rates.

$$DF(t) = \frac{1}{(1 + z_t)^t}$$

Where $z_t$ is the zero-coupon (spot) rate for maturity $t$.

**Key properties:**

- $DF(0) = 1$ (a dollar today is worth exactly a dollar today)
- $DF(t)$ is strictly decreasing in $t$ for any positive interest rate environment (money further in the future is worth less today)
- Discount factors are the building blocks for pricing *any* cash flow stream, once the appropriate factor is known for each relevant maturity

**Pricing any bond via discount factors:**

$$P = \sum_{t=1}^{n} C_t \times DF(t)$$

This generalizes the standard bond pricing formula by allowing a *different* discount factor for each cash flow date, rather than discounting every cash flow at the same single yield $y$.

### Zero-Coupon (Spot) Rates

**Definition:** The zero-coupon rate $z_t$ (also called the spot rate) is the annualized yield on a hypothetical zero-coupon bond maturing at time $t$ — the pure time value of money for that specific horizon, uncontaminated by coupon reinvestment assumptions.

**Why zero-coupon rates are considered the "purest" rate measure:**

A coupon-paying bond's YTM is a single blended internal rate of return across all its cash flows, implicitly assuming every coupon is reinvested at that *same* rate — an assumption that is rarely literally true when the yield curve is not flat. A zero-coupon rate for a specific maturity $t$, by contrast, reflects the market's actual required return for money tied up for exactly that period, with no embedded reinvestment assumption, because there are no intermediate coupons to reinvest.

**Relationship between discount factor and zero rate:**

$$z_t = \left(\frac{1}{DF(t)}\right)^{1/t} - 1$$

### Bootstrapping the Zero-Coupon Curve

Since liquid zero-coupon bonds do not exist at every maturity in most markets, zero rates are typically derived ("bootstrapped") from the prices of coupon-bearing bonds, working sequentially from the shortest maturity outward.

**Bootstrapping logic (step-by-step):**

1. Start with the shortest-maturity bond (often already a zero-coupon instrument, like a T-bill) — its yield directly gives $z_1$.
2. For the next maturity bond (e.g., a 2-year bond paying coupons), use its market price and the *already-known* $z_1$ to solve for the *unknown* $z_2$, since the bond's first coupon can be discounted using $z_1$.
3. Repeat sequentially — each new bond's price equation has exactly one new unknown (the zero rate for its own maturity), because all earlier coupon dates' discount factors are already known from prior steps.

**Worked Example:**

Given:

- 1-year zero rate: $z_1 = 4.0\%$ (from a 1-year T-bill)
- 2-year bond: 5% annual coupon, priced at $100.9284, $100 face value

Bond pricing equation:

$$100.9284 = \frac{5}{(1.04)^1} + \frac{105}{(1+z_2)^2}$$

Step 1 — discount the first coupon using known $z_1$:

$$\frac{5}{1.04} = 4.8077$$

Step 2 — isolate the unknown term:

$$100.9284 - 4.8077 = 96.1207 = \frac{105}{(1+z_2)^2}$$

Step 3 — solve for $z_2$:

$$(1+z_2)^2 = \frac{105}{96.1207} = 1.09239$$



$$z_2 = \sqrt{1.09239} - 1 = 0.0452 = 4.52\%$$

This bootstrapped 2-year zero rate (4.52%) is higher than the 1-year zero rate (4.00%), consistent with an upward-sloping ("normal") yield curve environment.

### Diagram: Bootstrapping Process (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 740 300" font-family="Arial, sans-serif">
<text x="370" y="24" text-anchor="middle" font-size="15" font-weight="bold">Sequential Bootstrapping of Zero Rates (svg_diagram)</text>
<rect x="40" y="60" width="170" height="60" rx="6" fill="#e8f0fe" stroke="#1a5fb4" stroke-width="1.5" />
<text x="125" y="85" text-anchor="middle" font-size="12">1-Year T-Bill</text>
<text x="125" y="103" text-anchor="middle" font-size="12" font-weight="bold">z₁ = 4.00% (known)</text>
<rect x="285" y="60" width="190" height="60" rx="6" fill="#fdf0e8" stroke="#c0392b" stroke-width="1.5" />
<text x="380" y="85" text-anchor="middle" font-size="12">2-Year Coupon Bond</text>
<text x="380" y="103" text-anchor="middle" font-size="12" font-weight="bold">Solve for z₂ = 4.52%</text>
<rect x="550" y="60" width="170" height="60" rx="6" fill="#eef7ee" stroke="#27ae60" stroke-width="1.5" />
<text x="635" y="85" text-anchor="middle" font-size="12">3-Year Coupon Bond</text>
<text x="635" y="103" text-anchor="middle" font-size="12" font-weight="bold">Solve for z₃ (next)</text>
<line x1="210" y1="90" x2="280" y2="90" stroke="black" stroke-width="1.5" marker-end="url(#arrB)" />
<line x1="475" y1="90" x2="545" y2="90" stroke="black" stroke-width="1.5" marker-end="url(#arrB)" />
<text x="245" y="80" text-anchor="middle" font-size="10">uses z₁</text>
<text x="510" y="80" text-anchor="middle" font-size="10">uses z₁, z₂</text>

<text x="370" y="180" text-anchor="middle" font-size="12" font-style="italic">Each step has exactly one new unknown: the current maturity's zero rate</text>

</svg>

### Spot Rates vs. Par Rates vs. Forward Rates — Distinguishing the Three Curve Types

| Rate Type | Definition | Derived From |
| --- | --- | --- |
| Par rate | The coupon rate at which a bond of a given maturity would price exactly at par | Directly observable from market prices of coupon bonds trading near par |
| Spot (zero) rate | The discount rate for a single cash flow at a specific future date, with no coupons | Bootstrapped from par rates/coupon bond prices |
| Forward rate | An implied future short-term rate, consistent with the current spot curve, applicable to a period beginning at some future date | Derived algebraically from the ratio of adjacent spot rates |

**Forward rate relationship (illustrative, 1-year forward rate one year from now, $f_{1,1}$):**

$$(1+z_2)^2 = (1+z_1)^1 \times (1+f_{1,1})^1$$



$$f_{1,1} = \frac{(1+z_2)^2}{(1+z_1)^1} - 1 = \frac{1.09239}{1.04} - 1 = 0.0504 = 5.04\%$$

This says: the market's current pricing is consistent with an implied 1-year rate of 5.04% applicable to money invested from year 1 to year 2 — a rate not directly observable today, but embedded in and derivable from today's zero-coupon curve.

### Using Zero Rates for More Accurate Bond Valuation

Any coupon bond can be more precisely valued by discounting each individual cash flow at the zero rate matching its own maturity, rather than a single blended YTM:

**Example — 3-year, 6% annual coupon bond, $1,000 face, given a zero curve of $z_1=4.0\%$, $z_2=4.52\%$, $z_3=5.00\%$:**

$$P = \frac{60}{(1.04)^1} + \frac{60}{(1.0452)^2} + \frac{1060}{(1.05)^3}$$



$$P = 57.69 + 54.95 + 915.85 = \$1{,}028.49$$

This price reflects the true term structure, whereas discounting all three cash flows at a single flat YTM (even one carefully solved to match this price) would only be an average approximation that masks the curve's actual shape.

### Practical Applications

- **Relative value analysis:** Comparing a bond's actual market price to its theoretical value computed from the zero curve reveals whether the bond is cheap or rich relative to the broader curve (the basis for identifying arbitrage or relative value trading opportunities).
- **Derivatives pricing:** Interest rate swaps, forward rate agreements, and other derivatives are priced using bootstrapped discount curves as a standard foundational input.
- **Option-adjusted spread models:** Valuing bonds with embedded options (callable, putable) over a full term structure — rather than a single flat yield — requires exactly this zero-curve/discount-factor framework as the starting input for constructing interest rate lattices.

### Key Points

- A discount factor $DF(t)$ represents the present value of $1 received at time $t$, given the current term structure.
- Zero-coupon (spot) rates are the "pure," reinvestment-assumption-free rate applicable to a single cash flow at a specific maturity, distinguishing them from a blended YTM.
- Bootstrapping sequentially derives the zero-coupon curve from observed coupon-bond prices, solving for one new unknown rate at each successive maturity.
- Forward rates are implied future rates consistent with today's spot curve, derived algebraically from the ratio of adjacent zero rates.
- Discounting each cash flow at its maturity-specific zero rate produces a more precise valuation than a single flat-yield approximation whenever the yield curve is not flat.

**Related Topics**

- Yield Curve Shapes and Term Structure Theories (Expectations, Liquidity Preference, Segmentation)
- Forward Rate Agreements and Their Relationship to the Spot Curve
- Option-Adjusted Spread (OAS) and Binomial Interest Rate Trees
- Par Curve Construction and Its Relationship to the Spot Curve
- Key Rate Duration and Non-Parallel Yield Curve Shifts
- Arbitrage-Free Bond Pricing and Relative Value Analysis