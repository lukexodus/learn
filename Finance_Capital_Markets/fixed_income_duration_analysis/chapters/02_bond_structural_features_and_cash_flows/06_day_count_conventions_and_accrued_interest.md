## Day Count Conventions and Accrued Interest

### Core Concept

When a bond is sold between coupon payment dates (the vast majority of secondary market transactions), the seller has earned a portion of the next coupon by holding the bond since the last payment date, but has not yet received it. **Accrued interest** compensates the seller for this earned-but-unpaid interest, and **day count conventions** define the precise rule for calculating how many days have elapsed and how many days exist in a period — a seemingly small mechanical detail that materially affects the exact cash amount exchanged in every bond trade.

### The Two Prices in a Bond Trade

| Price Type | Definition |
| --- | --- |
| Clean price (flat price) | The quoted market price, excluding accrued interest — reflects only the present value of future cash flows |
| Dirty price (full price / invoice price) | The actual cash amount paid by the buyer = Clean price + Accrued Interest |

$$\text{Dirty Price} = \text{Clean Price} + \text{AI}$$

Bond prices are quoted (and typically charted) as **clean prices** by market convention, but the buyer actually pays the **dirty price** at settlement — this distinction is essential because clean price charts would otherwise show a artificial "sawtooth" price drop on every coupon date if dirty prices were plotted instead.

### Accrued Interest Formula

$$\text{AI} = \text{Coupon per period} \times \frac{\text{Days since last coupon}}{\text{Days in coupon period}}$$

Or more explicitly:

$$\text{AI} = C \times \frac{t}{T}$$

Where:

- $C$ = the coupon payment for the full period
- $t$ = number of days elapsed since the last coupon date (per the applicable day count convention)
- $T$ = total number of days in the current coupon period (per the applicable day count convention)

The day count convention determines **both** $t$ and $T$ — different conventions can produce different accrued interest amounts for the exact same bond, settlement date, and coupon, because they count days differently.

### Major Day Count Conventions

| Convention | Notation | Day-Counting Rule | Typical Market Usage |
| --- | --- | --- | --- |
| Actual/Actual | ACT/ACT | Counts actual calendar days elapsed; actual days in the period (accounts for leap years) | U.S. Treasury notes/bonds |
| 30/360 (Bond Basis) | 30/360 | Assumes every month has 30 days and every year has 360 days | U.S. corporate bonds, U.S. municipal bonds, U.S. agency bonds |
| Actual/360 | ACT/360 | Counts actual calendar days elapsed; assumes 360-day year | Money market instruments (T-bills, commercial paper, most bank deposits) |
| Actual/365 (Fixed) | ACT/365F | Counts actual calendar days elapsed; assumes fixed 365-day year (no leap year adjustment) | Some UK Gilts, some money market instruments |
| 30E/360 (Eurobond Basis) | 30E/360 | Similar to 30/360 but with a slightly different end-of-month adjustment rule | European Eurobonds |

### 30/360 Convention — Detailed Mechanics

Under the U.S. 30/360 (Bond Basis) convention, if $D_1 = 31$, set $D_1 = 30$; if $D_2 = 31$ and $D_1 = 30$ (after adjustment), set $D_2 = 30$. Days elapsed:

$$t = 360 \times (Y_2 - Y_1) + 30 \times (M_2 - M_1) + (D_2 - D_1)$$

Where $Y_1, M_1, D_1$ is the last coupon date and $Y_2, M_2, D_2$ is the settlement date.

**[Inference]** Precise end-of-month adjustment rules vary slightly between the strict "30/360 US" convention and "30E/360" — implementers should consult the specific indenture or standard (e.g., ISDA) definitions for edge cases like February 28/29 or the 31st of a month, as small variations exist across documented standards.

### Worked Example: 30/360 vs. Actual/Actual

**Bond details:** $1,000 face, 6% annual coupon paid semi-annually ($30 per period), last coupon paid March 1, next coupon due September 1, settlement date July 15.

**Using 30/360:**

- Days elapsed ($t$): From March 1 to July 15 = $4 \text{ months} \times 30 + 14 \text{ days} = 134$ days
- Days in period ($T$): March 1 to September 1 = $6 \text{ months} \times 30 = 180$ days

$$\text{AI} = 30 \times \frac{134}{180} = \$22.33$$

**Using Actual/Actual:**

- Days elapsed ($t$): Actual calendar days from March 1 to July 15 = 136 days
- Days in period ($T$): Actual calendar days from March 1 to September 1 = 184 days

$$\text{AI} = 30 \times \frac{136}{184} = \$22.17$$

The two conventions produce a $0.16 difference on a single $1,000 bond for this period — a small amount per bond, but material in aggregate across institutional-sized positions and critical for exact settlement reconciliation.

### Diagram: Coupon Period and Accrued Interest Timeline (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 720 260" font-family="Arial, sans-serif">
<text x="360" y="24" text-anchor="middle" font-size="15" font-weight="bold">Accrued Interest Within a Coupon Period (svg_diagram)</text>
<line x1="80" y1="140" x2="640" y2="140" stroke="black" stroke-width="2" />
<line x1="100" y1="130" x2="100" y2="150" stroke="black" stroke-width="2" />
<text x="100" y="170" text-anchor="middle" font-size="12">Last Coupon</text>
<text x="100" y="186" text-anchor="middle" font-size="11">(March 1)</text>
<line x1="620" y1="130" x2="620" y2="150" stroke="black" stroke-width="2" />
<text x="620" y="170" text-anchor="middle" font-size="12">Next Coupon</text>
<text x="620" y="186" text-anchor="middle" font-size="11">(September 1)</text>
<line x1="380" y1="115" x2="380" y2="165" stroke="#c0392b" stroke-width="2" />
<text x="380" y="102" text-anchor="middle" font-size="12" fill="#c0392b">Settlement Date</text>
<text x="380" y="118" text-anchor="middle" font-size="11" fill="#c0392b">(July 15)</text>
<rect x="100" y="200" width="280" height="18" fill="#1a5fb4" opacity="0.75" />
<text x="240" y="213" text-anchor="middle" font-size="11" fill="white">Accrued Interest (t days) — seller's earned share</text>
<rect x="380" y="200" width="240" height="18" fill="#cccccc" />
<text x="500" y="213" text-anchor="middle" font-size="11">Remaining period — buyer's earned share</text>

<text x="360" y="240" text-anchor="middle" font-size="12">Full coupon period = T days</text>

</svg>

### Ex-Dividend / Ex-Coupon Dates

Many bond markets (particularly UK Gilts and some other government bond markets) use an **ex-dividend date** shortly before the coupon payment date. If a bond is sold *after* the ex-dividend date but before the coupon date, the **seller** (not the buyer) retains the right to receive the upcoming coupon, and accrued interest calculations flip sign — this is referred to as trading with **negative accrued interest**, since the buyer must be compensated (via a lower dirty price) for coupon income they will not receive despite holding the bond up to the payment date.

[Unverified as universally applicable] Ex-dividend conventions and their precise mechanics vary meaningfully by market; not all bond markets use this convention (e.g., most U.S. corporate and Treasury markets settle without an ex-dividend period, using straightforward accrued interest to the settlement date).

### Impact on Yield Calculations

Because the buyer pays the **dirty price** but yield-to-maturity calculations are typically run against this same full price paid, day count convention choice directly affects the derived YTM — using a different day count convention (e.g., mistakenly applying 30/360 to a bond that trades on Actual/Actual) will produce a subtly incorrect accrued interest figure, and consequently an incorrect YTM if reconciled against a quoted clean price.

### Comparative Summary Table

| Convention | Numerator (days elapsed) | Denominator (days in year/period) | Leap Year Sensitivity |
| --- | --- | --- | --- |
| Actual/Actual | Real calendar count | Real calendar count | Yes — automatically reflected |
| 30/360 | Standardized 30-day months | Standardized 360-day year | No — fully normalized |
| Actual/360 | Real calendar count | Fixed 360 | No (numerator varies, denominator fixed) |
| Actual/365F | Real calendar count | Fixed 365 | No — ignores Feb 29 entirely |

### Key Points

- Accrued interest compensates the seller for interest earned but not yet paid at the time of a bond's sale between coupon dates.
- Dirty price (what the buyer actually pays) = Clean price (quoted market price) + Accrued interest.
- Day count conventions (Actual/Actual, 30/360, Actual/360, Actual/365F) determine exactly how $t$ (days elapsed) and $T$ (days in period) are counted, and different conventions yield different accrued interest amounts for identical dates.
- Government bonds commonly use Actual/Actual; U.S. corporate bonds commonly use 30/360; money market instruments commonly use Actual/360.
- Ex-dividend conventions (where applicable) can flip accrued interest to a negative adjustment when trading shortly before a coupon date.

**Related Topics**

- Bond Settlement Mechanics (T+1, T+2 Conventions)
- Clean Price vs. Dirty Price in Yield-to-Maturity Calculations
- Money Market Instrument Pricing (Discount Yield vs. Bond-Equivalent Yield)
- Ex-Dividend Trading Conventions in Government Bond Markets
- Repo Market Accrued Interest and Collateral Valuation
- ISDA Day Count Fraction Definitions for Derivatives