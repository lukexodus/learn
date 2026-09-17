## Current Yield and Coupon Yield

### Core Definitions

**Coupon yield** (also called the nominal yield or coupon rate) is the fixed annual interest rate stated on a bond at issuance, expressed as a percentage of face value — it never changes over the bond's life regardless of subsequent market price movements.

**Current yield** is a market-price-sensitive measure that expresses the bond's annual coupon income as a percentage of its *current market price*, rather than its face value.

$$\text{Coupon Yield} = \frac{\text{Annual Coupon Payment}}{\text{Face Value}}$$



$$\text{Current Yield} = \frac{\text{Annual Coupon Payment}}{\text{Current Market Price}}$$

### Why These Two Measures Diverge

Coupon yield is fixed by the bond's original terms and stated at issuance — it is a static, contractual figure. Current yield, by contrast, moves inversely with the bond's market price: as price falls, current yield rises (the same fixed dollar coupon divided by a smaller price produces a larger percentage); as price rises, current yield falls. This relationship directly mirrors, and is a simpler cousin of, the classification of bonds as trading at par, premium, or discount.

### Worked Example

**Bond details:** $1,000 face value, 6% annual coupon ($60 per year).

**Case 1 — Bond trading at par ($1,000):**

$$\text{Coupon Yield} = \frac{60}{1000} = 6.00\%$$



$$\text{Current Yield} = \frac{60}{1000} = 6.00\%$$

At par, coupon yield and current yield are identical, since price equals face value.

**Case 2 — Bond trading at a discount ($920):**

$$\text{Coupon Yield} = \frac{60}{1000} = 6.00\% \quad \text{(unchanged — always based on face value)}$$



$$\text{Current Yield} = \frac{60}{920} = 6.52\%$$

Current yield rises above the coupon yield because the same $60 coupon is now measured against a smaller price.

**Case 3 — Bond trading at a premium ($1,085):**

$$\text{Coupon Yield} = \frac{60}{1000} = 6.00\% \quad \text{(unchanged)}$$



$$\text{Current Yield} = \frac{60}{1085} = 5.53\%$$

Current yield falls below the coupon yield because the same $60 coupon is now measured against a larger price.

### Diagram: Current Yield vs. Coupon Yield Across Price Levels (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 720 300" font-family="Arial, sans-serif">
<text x="360" y="24" text-anchor="middle" font-size="15" font-weight="bold">Current Yield Moves Inversely With Price (svg_diagram)</text>
<line x1="80" y1="250" x2="660" y2="250" stroke="black" stroke-width="1.5" />
<line x1="80" y1="40" x2="80" y2="250" stroke="black" stroke-width="1.5" />
<text x="370" y="275" text-anchor="middle" font-size="12">Market Price →</text>
<text x="35" y="145" text-anchor="middle" font-size="12" transform="rotate(-90 35 145)">Yield</text>
<line x1="80" y1="140" x2="660" y2="140" stroke="gray" stroke-dasharray="5,3" />
<text x="665" y="144" font-size="11" fill="gray">Coupon Yield (fixed, 6.00%)</text>
<path d="M 120 90 Q 300 130, 480 155 T 620 175" fill="none" stroke="#c0392b" stroke-width="2.5" />
<text x="200" y="80" font-size="11" fill="#c0392b">Current Yield (varies with price)</text>
<circle cx="200" cy="105" r="4" fill="#c0392b" />
<text x="200" y="115" font-size="10" fill="#c0392b">Discount: CY &gt; Coupon</text>
<circle cx="370" cy="140" r="4" fill="black" />
<text x="370" y="125" font-size="10">Par: CY = Coupon</text>
<circle cx="540" cy="168" r="4" fill="#c0392b" />
<text x="540" y="185" font-size="10" fill="#c0392b">Premium: CY &lt; Coupon</text>
</svg>

### Critical Limitations of Current Yield

**[Verified — a well-documented structural limitation]** Current yield is a widely cited but analytically incomplete measure, because it ignores several factors that materially affect an investor's actual total return:

| Limitation | Explanation |
| --- | --- |
| Ignores capital gain/loss at maturity | A discount bond will experience price appreciation toward par as it approaches maturity (the "pull to par" effect); current yield captures none of this expected gain |
| Ignores time value of money | Current yield is a simple ratio, not a discounted, time-weighted measure — it treats a coupon received today identically to one received in year 10 |
| Ignores reinvestment of coupons | Current yield says nothing about the rate at which received coupons can be reinvested over the bond's remaining life |
| Not comparable across different maturities on a consistent basis | Two bonds with identical current yields but very different maturities can have very different total return profiles, since current yield does not account for the timing or certainty of the return of principal |

**Practical consequence:** Because it ignores the capital gain (for discount bonds) or capital loss (for premium bonds) embedded in the pull-to-par effect, current yield systematically *understates* the true expected return of a discount bond and *overstates* the true expected return of a premium bond relative to a more complete measure like yield to maturity.

### Relative Positioning: Coupon Yield, Current Yield, and Yield to Maturity

This three-way relationship, first introduced under par/premium/discount classification, is worth restating explicitly here since current yield's position in this ordering is precisely what reveals its incompleteness as a standalone measure:

| Bond Type | Coupon Yield | Current Yield | Yield to Maturity |
| --- | --- | --- | --- |
| Discount bond | Lowest | Middle | Highest |
| Par bond | Equal | Equal | Equal |
| Premium bond | Highest | Middle | Lowest |

**Why current yield always sits between coupon yield and YTM:** For a discount bond, current yield already captures *some* of the yield uplift from buying below face value (since it divides the coupon by the lower price), but it does not capture the *additional* uplift from the capital gain earned as the bond pulls to par — YTM captures both effects, so YTM exceeds current yield, which in turn exceeds the coupon yield. The mirror-image logic applies to premium bonds.

### Coupon Yield's Narrow but Legitimate Uses

Despite current yield's limitations as a total-return proxy, coupon yield itself remains meaningful for specific, narrower purposes:

- **Identifying the bond's original contractual terms** at issuance, independent of subsequent market price movement.
- **Categorizing bonds by coupon structure** (e.g., "high-coupon" vs. "low-coupon" issues) for portfolio construction or tax-related discussions (e.g., market discount and premium amortization rules often reference the original coupon rate as a fixed input).
- **A component of current yield and other yield calculations**, serving as the fixed numerator input.

### When Current Yield Is Still a Useful Quick Metric

**[Inference]** Despite its limitations, current yield retains practical value in specific contexts:

- **Quick income-focused screening:** For an investor primarily interested in near-term cash income (e.g., certain income-oriented retail investors) rather than total return, current yield provides an immediate, easily-computed sense of the coupon income relative to the price actually paid.
- **Simplicity for non-quantitative communication:** Current yield requires no assumptions about reinvestment rates or precise time-value-of-money calculations, making it easier to explain and calculate by hand compared to yield to maturity.
- **A first-pass screening filter** before applying more rigorous yield to maturity or total return analysis to a shortlist of candidate bonds.

### Key Points

- Coupon yield is the fixed annual coupon divided by face value, set at issuance and unchanged thereafter; current yield is the annual coupon divided by the *current market price*, moving inversely with price.
- At par, coupon yield equals current yield; for discount bonds current yield exceeds coupon yield; for premium bonds current yield falls below coupon yield.
- Current yield ignores capital gains/losses from the pull-to-par effect, the time value of money, and reinvestment of coupons — making it a structurally incomplete total-return measure compared to yield to maturity.
- Current yield always sits between coupon yield and YTM for both discount and premium bonds, reflecting that it captures only part of the total yield uplift or reduction relative to face value.
- Despite its limitations, current yield remains a useful, easily-calculated first-pass screening tool for income-focused analysis, distinct from — and not a substitute for — full yield to maturity analysis.

**Related Topics**

- Yield to Maturity: Definition, Calculation, and Assumptions
- Par, Premium, and Discount Bonds
- Pull-to-Par Price Convergence Mechanics
- Yield to Call and Yield to Worst for Callable Bonds
- Total Return Analysis and Reinvestment Rate Assumptions
- Bond-Equivalent Yield and Rate Convention Conversions