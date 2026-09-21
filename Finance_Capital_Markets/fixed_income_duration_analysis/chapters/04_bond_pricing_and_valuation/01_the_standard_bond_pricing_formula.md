## The Standard Bond Pricing Formula

### Core Formula

The standard bond pricing formula computes a bond's price as the sum of the present values of all future contractual cash flows — periodic coupon payments and the final principal repayment — discounted at a single, constant required yield (the yield to maturity).

$$P = \sum_{t=1}^{n} \frac{C}{(1+y)^t} + \frac{F}{(1+y)^n}$$

Where:

- $P$ = bond price (present value)
- $C$ = periodic coupon payment ($= c \times F$, where $c$ is the coupon rate per period)
- $F$ = face value (par value)
- $y$ = required yield per period (market discount rate, matched to the coupon frequency)
- $n$ = total number of remaining periods to maturity

### Closed-Form (Annuity) Version

Since the coupon payments $C$ form an ordinary annuity, the summation term can be replaced with the closed-form present value of an annuity formula, avoiding the need to sum each individual term separately:

$$P = C \times \left[\frac{1 - (1+y)^{-n}}{y}\right] + \frac{F}{(1+y)^n}$$

This is the standard form used in practice for hand calculation or spreadsheet implementation, since it requires only $C$, $F$, $y$, and $n$ as inputs rather than iterating through every period.

### Assumptions Embedded in the Standard Formula

The standard bond pricing formula rests on several simplifying assumptions, each of which matters for correctly interpreting the resulting price:

| Assumption | Implication |
| --- | --- |
| Flat yield curve (single discount rate $y$ for all cash flow dates) | Every cash flow — near-term and far-term — is discounted at the identical rate, which is only an approximation when the true term structure is not flat |
| No embedded options | The formula assumes a straight (option-free) bond; callable, putable, or convertible bonds require option-adjusted valuation extensions |
| Coupon reinvested at $y$ | The formula's derivation implicitly assumes all coupons received are reinvested at the same rate $y$ until maturity to achieve the quoted yield — a well-known limitation of yield-to-maturity as a realized return measure |
| No default risk adjustment beyond what is embedded in $y$ | Credit risk is assumed to already be reflected in the chosen discount rate $y$, not modeled separately within the formula itself |
| Valuation on a coupon date (no accrued interest) | The raw formula produces the price *as of* a coupon payment date; valuing between coupon dates requires the additional accrued interest adjustment |

### Worked Example: Semi-Annual Coupon Bond

**Given:** $1,000 face value, 7% annual coupon rate (paid semi-annually), 5 years to maturity, required yield of 8% (annual, compounded semi-annually — i.e., a 4% semi-annual discount rate).

**Adjust inputs to the semi-annual period:**

- $C = \dfrac{0.07 \times 1000}{2} = 35$ per period
- $y = \dfrac{0.08}{2} = 0.04$ per period
- $n = 5 \times 2 = 10$ periods

**Apply the formula:**

$$P = 35 \times \left[\frac{1 - (1.04)^{-10}}{0.04}\right] + \frac{1000}{(1.04)^{10}}$$



$$P = 35 \times 8.11090 + 1000 \times 0.67556$$



$$P = 283.88 + 675.56 = \$959.45$$

This price is below par ($1,000), consistent with the coupon rate (7%) being lower than the required yield (8%) — a discount bond, as covered under par/premium/discount bond classification.

### Diagram: The Two Components of the Bond Pricing Formula (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 720 300" font-family="Arial, sans-serif">
<text x="360" y="24" text-anchor="middle" font-size="15" font-weight="bold">Bond Price = PV(Coupon Annuity) + PV(Face Value) (svg_diagram)</text>
<rect x="60" y="60" width="280" height="90" rx="6" fill="#e8f0fe" stroke="#1a5fb4" stroke-width="1.5" />
<text x="200" y="90" text-anchor="middle" font-size="13" font-weight="bold" fill="#1a5fb4">PV of Coupon Annuity</text>
<text x="200" y="112" text-anchor="middle" font-size="12">C × [1 − (1+y)⁻ⁿ] / y</text>
<text x="200" y="132" text-anchor="middle" font-size="11">= 283.88</text>

<text x="360" y="112" text-anchor="middle" font-size="22" font-weight="bold">+</text>

<rect x="380" y="60" width="280" height="90" rx="6" fill="#fdf0e8" stroke="#c0392b" stroke-width="1.5" />
<text x="520" y="90" text-anchor="middle" font-size="13" font-weight="bold" fill="#c0392b">PV of Face Value</text>
<text x="520" y="112" text-anchor="middle" font-size="12">F / (1+y)ⁿ</text>
<text x="520" y="132" text-anchor="middle" font-size="11">= 675.56</text>
<line x1="200" y1="150" x2="360" y2="210" stroke="black" stroke-width="1" />
<line x1="520" y1="150" x2="360" y2="210" stroke="black" stroke-width="1" />
<rect x="260" y="210" width="200" height="55" rx="6" fill="#eef7ee" stroke="#27ae60" stroke-width="2" />
<text x="360" y="235" text-anchor="middle" font-size="13" font-weight="bold" fill="#27ae60">Bond Price = 959.45</text>
<text x="360" y="252" text-anchor="middle" font-size="11">(Discount bond)</text>
</svg>

### The Price-Yield Function and Its Shape

Plotting bond price $P$ against required yield $y$, holding coupon, face value, and maturity constant, produces a curved (convex) downward-sloping relationship — not a straight line — which is the geometric origin of **convexity** as a bond risk measure.

$$\frac{\partial P}{\partial y} < 0, \qquad \frac{\partial^2 P}{\partial y^2} > 0$$

The first condition ($\partial P/\partial y < 0$) confirms the fundamental inverse price-yield relationship; the second condition ($\partial^2 P/\partial y^2 > 0$) confirms the curve is convex (curves upward when viewed from below), meaning price gains from a yield decrease exceed price losses from an equivalent-sized yield increase — a property fully developed under convexity analysis.

### Generalizing to Non-Annual and Irregular Periods

**For a bond with $m$ coupon payments per year:**

$$P = \sum_{t=1}^{n} \frac{C/m}{\left(1+\frac{y}{m}\right)^t} + \frac{F}{\left(1+\frac{y}{m}\right)^n}$$

**For valuation between coupon dates (full/dirty price):**

$$P_{\text{dirty}} = \sum_{t=1}^{n} \frac{C}{(1+y)^{t-f}} + \frac{F}{(1+y)^{n-f}}$$

Where $f$ is the fraction of the current coupon period that has already elapsed (per the applicable day count convention) — raising the discounting exponent by $(t-f)$ rather than a whole integer $t$ reflects that the next cash flow is now less than a full period away.

### Sensitivity of Price to Each Input Variable

| Input Variable | Effect of an Increase (holding others constant) |
| --- | --- |
| Coupon rate ($c$) | Price increases (more cash returned per period) |
| Required yield ($y$) | Price decreases (inverse relationship) |
| Time to maturity ($n$), for a discount bond | Price generally decreases further from par [Inference: pattern is more nuanced for premium bonds, where price moves toward par as maturity shortens — see par/premium/discount pull-to-par dynamics] |
| Face value ($F$) | Price increases proportionally (formula scales linearly in $F$, all else equal) |

### Key Points

- The standard bond pricing formula computes price as the present value of a coupon annuity plus the present value of a single lump-sum face value repayment, both discounted at a single yield $y$.
- The formula assumes a flat discount rate across all cash flow dates, no embedded options, and reinvestment of coupons at the same yield $y$ — a set of simplifications relaxed by more advanced valuation techniques (zero-curve discounting, option-adjusted models).
- Semi-annual (or other non-annual) coupon frequencies require adjusting both the coupon amount and the discount rate to match the compounding period before applying the formula.
- The price-yield relationship is inherently non-linear (convex), which is the foundational geometric fact underlying convexity as a risk measure.
- Valuing a bond between coupon dates requires incorporating the elapsed fraction of the current period, connecting this formula directly to accrued interest and day count convention mechanics.

**Related Topics**

- Yield to Maturity: Definition, Calculation, and Assumptions
- Macaulay Duration and Modified Duration Derivation
- Convexity and the Non-Linear Price-Yield Relationship
- Discount Factors and Zero-Coupon Rates (Curve-Based Pricing)
- Day Count Conventions and Accrued Interest
- Par, Premium, and Discount Bond Classification