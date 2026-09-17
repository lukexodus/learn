## Clean Price versus Dirty Price

### Core Definitions

**Clean price** (also called the flat price or quoted price) is the price of a bond excluding accrued interest — it reflects only the present value of the bond's remaining future cash flows as of the settlement date, stripped of any adjustment for interest earned since the last coupon payment. **Dirty price** (also called the full price or invoice price) is the actual total cash amount a buyer pays to a seller at settlement, equal to the clean price plus accrued interest.

$$P_{\text{dirty}} = P_{\text{clean}} + AI$$



$$P_{\text{clean}} = P_{\text{dirty}} - AI$$

Where $AI$ is accrued interest, calculated according to the applicable day count convention.

### Why Two Prices Exist

Bond markets universally quote and display **clean prices** as the standard convention, but the actual cash transferred at settlement is always the **dirty price**. This separation exists for a specific practical reason: if bonds were quoted at their dirty price, the quoted price would exhibit an artificial "sawtooth" discontinuity — rising steadily as accrued interest builds up between coupon dates, then dropping sharply on the payment date itself (as the accrued portion resets to zero) — making it difficult to visually or analytically distinguish a genuine market price movement (driven by yield/credit changes) from the purely mechanical effect of interest accrual.

### Diagram: Clean Price vs. Dirty Price Over a Coupon Cycle (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 740 320" font-family="Arial, sans-serif">
<text x="370" y="24" text-anchor="middle" font-size="15" font-weight="bold">Clean vs. Dirty Price Across Coupon Periods (svg_diagram)</text>
<line x1="70" y1="270" x2="680" y2="270" stroke="black" stroke-width="1.5" />
<line x1="70" y1="40" x2="70" y2="270" stroke="black" stroke-width="1.5" />
<text x="375" y="295" text-anchor="middle" font-size="12">Time →</text>
<text x="30" y="155" text-anchor="middle" font-size="12" transform="rotate(-90 30 155)">Price</text>
<line x1="70" y1="150" x2="680" y2="150" stroke="#1a5fb4" stroke-width="2.5" />
<text x="120" y="140" font-size="11" fill="#1a5fb4">Clean price (smooth, reflects yield/credit only)</text>
<path d="M 70 150 L 250 100" fill="none" stroke="#c0392b" stroke-width="2.5" />
<line x1="250" y1="100" x2="250" y2="150" stroke="#c0392b" stroke-width="1.5" stroke-dasharray="4,3" />
<path d="M 250 150 L 430 100" fill="none" stroke="#c0392b" stroke-width="2.5" />
<line x1="430" y1="100" x2="430" y2="150" stroke="#c0392b" stroke-width="1.5" stroke-dasharray="4,3" />
<path d="M 430 150 L 610 100" fill="none" stroke="#c0392b" stroke-width="2.5" />
<line x1="610" y1="100" x2="610" y2="150" stroke="#c0392b" stroke-width="1.5" stroke-dasharray="4,3" />

<text x="600" y="90" font-size="11" fill="`#c0392b`">Dirty price (sawtooth, includes accrued interest)</text>

<line x1="250" y1="145" x2="250" y2="155" stroke="black" stroke-width="2" />
<text x="250" y="175" text-anchor="middle" font-size="11">Coupon Date 1</text>
<line x1="430" y1="145" x2="430" y2="155" stroke="black" stroke-width="2" />
<text x="430" y="175" text-anchor="middle" font-size="11">Coupon Date 2</text>
<line x1="610" y1="145" x2="610" y2="155" stroke="black" stroke-width="2" />
<text x="610" y="175" text-anchor="middle" font-size="11">Coupon Date 3</text>
</svg>

### Calculating Both Prices in Practice

**Worked Example:** A bond has a clean (quoted) price of $98.50 (per $100 face value), annual coupon of 6% ($6.00 per $100 face), last coupon paid 90 days ago, and the current coupon period is 360 days (30/360 convention).

**Step 1 — Calculate accrued interest:**

$$AI = 6.00 \times \frac{90}{360} = \$1.50$$

**Step 2 — Calculate dirty price:**

$$P_{\text{dirty}} = 98.50 + 1.50 = \$100.00$$

The buyer actually pays $100.00 per $100 face value at settlement, even though the bond is quoted (and would appear on a screen or in a price chart) as $98.50.

### Deriving Clean Price From the Full Pricing Formula

The full (dirty) price of a bond between coupon dates, using the standard present value approach, is:

$$P_{\text{dirty}} = \sum_{t=1}^{n} \frac{C}{(1+y)^{t-f}} + \frac{F}{(1+y)^{n-f}}$$

Where $f$ is the fraction of the current coupon period already elapsed. The clean price is then obtained by subtracting the accrued interest:

$$P_{\text{clean}} = P_{\text{dirty}} - (C \times f)$$

**Note on the two ways accrued interest is embedded:** [Inference] Different bond math implementations sometimes use a simple linear ($C \times f$) accrual assumption versus a full present-value-consistent accrual definition; for most standard bond markets and day count conventions the simple linear method is the market-standard approach, though practitioners should confirm which convention a specific market or system uses when reconciling to the last cent.

### Practical Trading and Settlement Context

| Context | Which Price Applies |
| --- | --- |
| Price quoted on a trading screen / exchange | Clean price |
| Price charted historically for trend analysis | Clean price (to avoid the artificial sawtooth pattern) |
| Actual cash exchanged at settlement (invoice amount) | Dirty price |
| Yield to maturity calculation input | Dirty price (the true amount invested) is used as the present value input, even though the clean price is what's quoted |
| Bond index return calculations | [Inference] Total return indices typically incorporate the effect of coupon accrual and reinvestment, effectively capturing dirty-price economics over time, even if the index level itself is often reported on a clean-price-equivalent basis; exact index construction methodology varies by provider |

### Common Point of Confusion: YTM and Clean Price

A frequent source of error is treating the *quoted clean price* as the amount actually invested when computing yield to maturity. In fact, the correct present value input for a YTM calculation is the **dirty price** (the true amount paid), since that is the actual cash outlay the investor makes and the actual amount whose future cash flows must equate in present value terms. Using the clean price directly as the YTM input, without adding back accrued interest, produces a systematically incorrect (typically overstated) yield figure.

### Relationship to Negative Accrued Interest (Ex-Dividend Markets)

In markets that employ an ex-dividend period (such as certain government bond markets), a bond sold shortly before a coupon date but after the ex-dividend date entitles the *seller* — not the buyer — to the upcoming coupon. In this scenario:

$$P_{\text{dirty}} = P_{\text{clean}} - AI_{\text{negative}}$$

The dirty price is *lower* than the clean price during this window, since the buyer must be compensated for the coupon income they will not receive despite settling before the payment date.

### Comparative Summary Table

| Attribute | Clean Price | Dirty Price |
| --- | --- | --- |
| Includes accrued interest? | No | Yes |
| What is typically quoted/displayed | Clean price | Not typically displayed as the headline quote |
| What is actually paid at settlement | N/A (informational only) | Full invoice amount |
| Chart/time-series behavior | Smooth (reflects only yield/credit changes) | Sawtooth pattern across each coupon cycle |
| Used as YTM calculation input | No (must be converted to dirty first) | Yes |

### Key Points

- Clean price excludes accrued interest and is the standard quoted/displayed market price; dirty price includes accrued interest and is the actual amount paid at settlement.
- Dirty price = Clean price + Accrued interest (with a sign reversal possible in ex-dividend markets, producing negative accrued interest).
- The sawtooth pattern in dirty price over a coupon cycle is precisely why markets quote clean prices for charting and quoting purposes — to isolate genuine price movement from mechanical interest accrual.
- Yield to maturity calculations must use the dirty price as the true present value/investment amount, not the clean price, to avoid systematically distorted yield figures.
- The distinction connects directly to day count conventions (which determine the exact accrued interest amount) and to the standard bond pricing formula's between-coupon-date extension.

**Related Topics**

- Day Count Conventions and Accrued Interest
- Yield to Maturity: Definition, Calculation, and Assumptions
- The Standard Bond Pricing Formula
- Ex-Dividend Trading Conventions in Government Bond Markets
- Bond Index Construction and Total Return Methodology
- Settlement Mechanics and Trade Date vs. Settlement Date Conventions