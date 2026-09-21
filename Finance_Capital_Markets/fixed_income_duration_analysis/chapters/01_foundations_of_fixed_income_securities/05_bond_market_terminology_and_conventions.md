## Bond Market Terminology and Conventions


### Overview

Fixed income markets rely on a specialized vocabulary and a set of standardized conventions governing how prices, yields, dates, and cash flows are quoted and calculated. These conventions are not arbitrary — they exist to standardize comparison across instruments with different structures, and misapplying them is a common source of error in yield and duration calculations. This reference covers the core terminology and quoting/calculation conventions used throughout fixed income analysis.

### Core Bond Terminology

**Key Points**

- **Face value / Par value / Principal**: The amount repaid at maturity and the basis on which coupon payments are calculated (e.g., $1,000 or $100 per bond)
- **Coupon rate**: The stated annual interest rate paid on the face value, typically expressed as an annual percentage even when paid semiannually
- **Coupon payment**: The periodic cash interest payment, calculated as (Coupon rate ÷ payment frequency) × Face value
- **Maturity date**: The date on which the issuer repays the face value
- **Tenor**: The remaining time to maturity, often used interchangeably with "maturity" in casual usage but technically refers to time remaining rather than the original term
- **Issue date / Settlement date**: The date the bond is first sold / the date a specific transaction settles
- **Par, premium, discount**: A bond trading at par has a price equal to 100% of face value; premium bonds trade above par (coupon rate exceeds market yield); discount bonds trade below par (coupon rate is below market yield)
- **Zero-coupon bond**: A bond with no periodic coupon, issued at a discount and redeemed at par, with return entirely from price appreciation

### Price Quotation Conventions

#### Clean Price vs. Dirty Price

- **Clean price**: The quoted price excluding accrued interest; this is the price typically displayed on trading screens and used in most quoted yield calculations
- **Dirty price (full price / invoice price)**: The actual amount paid at settlement, including accrued interest

$$P_{dirty} = P_{clean} + AI$$

#### Price Quotation Format

- Corporate and municipal bonds are typically quoted as a percentage of par (e.g., 98.750 = $987.50 per $1,000 face value)
- U.S. Treasury notes and bonds are conventionally quoted in **32nds** of a point, sometimes with an additional eighth or quarter of a 32nd (e.g., "99-16" means 99 and 16/32, or 99.500; "99-16+" adds a half of 1/32)
- Money market instruments (T-bills, commercial paper) are often quoted on a **discount rate basis** rather than a price or yield-to-maturity basis, requiring conversion for direct comparison to coupon-bearing instrument yields

### Day Count Conventions

Day count conventions determine how accrued interest and time fractions are calculated between dates, directly affecting accrued interest, yield calculations, and duration formulas.

**Key Points**

| Convention | Common Notation | Typical Use | Calculation Basis |
| --- | --- | --- | --- |
| Actual/Actual | ACT/ACT (ICMA or ISDA variants) | U.S. Treasury notes/bonds | Actual days elapsed / actual days in period (or year) |
| 30/360 | 30/360 (Bond Basis) | U.S. corporate and municipal bonds | Each month treated as having 30 days, year as 360 days |
| Actual/360 | ACT/360 | Money market instruments, most floating-rate notes | Actual days elapsed / 360-day year |
| Actual/365 | ACT/365 (Fixed) | UK Gilts, some money market instruments | Actual days elapsed / 365-day year |

Accrued interest under 30/360:

$$AI = \text{Coupon} \times \frac{30 \times (M_2 - M_1) + (D_2 - D_1)}{360}$$

(with adjustments when $D_1$ or $D_2$ equals 31, per specific 30/360 sub-variants)

### Yield Terminology

- **Coupon rate**: Fixed contractual rate, does not change with market conditions
- **Current yield**: Annual coupon payment divided by current market price — a simple but incomplete yield measure that ignores capital gain/loss to maturity and time value of money

$$Y_{current} = \frac{\text{Annual Coupon}}{P_{clean}}$$

- **Yield to maturity (YTM)**: The internal rate of return that equates the present value of all future cash flows to the current dirty price, assuming the bond is held to maturity and coupons are reinvested at the YTM itself
- **Yield to call (YTC) / Yield to worst (YTW)**: YTM calculated to the call date rather than maturity; yield to worst is the lowest of all possible yield outcomes (to maturity, to each call date, to put date) and is the conservative standard for callable bond quotation
- **Bond-equivalent yield (BEY)**: Annualizes a semiannual-pay bond's yield by simple doubling of the semiannual rate, as opposed to true effective annual yield which compounds

### Basis Point and Spread Terminology

- **Basis point (bp)**: 0.01%, or 1/100th of a percentage point — the standard unit for quoting yield changes and credit spreads
- **Spread**: The yield difference between two securities, most commonly a credit bond versus a duration-matched benchmark (Treasury or swap curve)
  - **G-spread**: Spread to an interpolated point on the government (Treasury) curve
  - **I-spread**: Spread to the interpolated swap curve
  - **Z-spread (zero-volatility spread)**: The constant spread added to each point on the spot (zero-coupon) curve that equates the present value of cash flows to the bond's market price — more precise than G-spread for bonds with significant cash flow timing differences from the benchmark
  - **OAS (option-adjusted spread)**: The Z-spread adjusted to remove the value attributable to embedded options, used for callable/putable bonds and MBS

### Settlement Conventions

- **Regular-way settlement**: The standard settlement timeframe for a given market (varies by instrument and jurisdiction — commonly T+1 or T+2 for many government and corporate bond markets, though conventions have shifted over time with regulatory changes) [Unverified: current settlement cycles should be confirmed against the relevant market's current rulebook, as several major markets shortened standard settlement cycles in recent years]
- **When-issued (WI) trading**: Trading in a security after it has been announced but before it is formally issued and settled, common in Treasury auctions
- **Ex-dividend/ex-coupon date**: The date on or after which a buyer is not entitled to the next scheduled coupon payment; the seller retains that right

### Duration and Risk Terminology (Preview)

Conventions in this section set up terminology used extensively in subsequent duration-focused material:

- **Macaulay duration**: The weighted-average time (in years) to receipt of a bond's cash flows, weighted by present value
- **Modified duration**: The percentage price sensitivity to a small parallel yield change, derived from Macaulay duration
- **Effective duration**: Price sensitivity measured using a pricing model that accounts for embedded optionality (used for callable bonds, MBS)
- **Convexity**: The curvature of the price-yield relationship, capturing the second-order price sensitivity not explained by duration alone
- **DV01 / PVBP (dollar value of a basis point / price value of a basis point)**: The dollar price change for a one basis point change in yield

### Terminology Relationship Diagram

```mermaid
flowchart TD
    A[Bond Price Quote (svg_diagram)] --> B[Clean Price]
    A --> C[Dirty Price = Clean Price + Accrued Interest]
    C --> D[Accrued Interest via Day Count Convention]
    D --> D1[30/360]
    D --> D2[Actual/Actual]
    D --> D3[Actual/360]
    D --> D4[Actual/365]

    B --> E[Yield Measures]
    E --> E1[Current Yield]
    E --> E2[Yield to Maturity]
    E --> E3[Yield to Call / Yield to Worst]

    E2 --> F[Spread Measures]
    F --> F1[G-Spread]
    F --> F2[I-Spread]
    F --> F3[Z-Spread]
    F --> F4[OAS]

    E2 --> G[Duration & Risk Measures]
    G --> G1[Macaulay Duration]
    G1 --> G2[Modified Duration]
    G --> G3[Effective Duration]
    G --> G4[Convexity]
    G --> G5[DV01 / PVBP]
```

### Example

A corporate bond with a 5% annual coupon rate, paying semiannually, is quoted at a clean price of 98.500 (per 100 face value). The last coupon was paid 92 days ago, in a 182-day coupon period, under 30/360 convention.

Semiannual coupon payment: $5\% / 2 \times 100 = 2.50$

Accrued interest: $2.50 \times \dfrac{92}{182} = 1.264$

Dirty price: $98.500 + 1.264 = 99.764$

This dirty price of 99.764 (per 100 face) is the actual amount the buyer pays at settlement, forming the basis for the bond's yield-to-maturity calculation.

### Relevance to Duration Analysis

Precise application of day count and price quotation conventions is a prerequisite for accurate duration calculation: Macaulay and modified duration formulas depend on correctly time-weighted cash flows, which in turn depend on the day count convention used to measure time fractions between payment dates. Inconsistent convention application (e.g., mixing 30/360 cash flow timing with Actual/Actual year fractions) produces systematic errors in both yield and duration outputs.

**Next Steps**

- **Related Topics**: Bond Pricing and Yield Measures, Accrued Interest and Day Count Conventions in Depth, Macaulay and Modified Duration Formulas, Credit Spread Measures (G-Spread, I-Spread, Z-Spread, OAS), Yield Curve Construction and Term Structure Theories, Callable Bond Analysis and Yield to Worst, Settlement Conventions Across Global Bond Markets