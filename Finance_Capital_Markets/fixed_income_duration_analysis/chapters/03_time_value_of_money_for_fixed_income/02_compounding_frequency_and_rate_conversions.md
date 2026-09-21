## Compounding Frequency and Rate Conversions

### Core Concept

The same underlying investment return can be expressed through multiple different quoted rate conventions depending on how frequently interest compounds and how the market convention states the rate. Fixed income practitioners must be able to convert between these conventions accurately, since comparing bonds or instruments quoted under different rate bases without proper conversion produces materially incorrect comparisons — a critical, frequently tested skill distinct from, but built upon, the basic present value/future value principles.

### Nominal Rate vs. Effective Annual Rate

**Nominal (stated/quoted) annual rate:** The rate as quoted in the market, without adjustment for intra-year compounding. Also called the Annual Percentage Rate (APR) in some contexts.

**Effective Annual Rate (EAR):** The actual annualized rate of return an investor earns after accounting for the effect of compounding within the year.

$$EAR = \left(1 + \frac{r_{\text{nominal}}}{m}\right)^m - 1$$

Where $m$ = number of compounding periods per year.

**Why this distinction matters in fixed income:** A bond quoted with a 6% nominal annual rate compounded semi-annually does NOT earn 6% in a year — it earns more, because the first semi-annual coupon begins (implicitly) earning a return during the second half of the year. Comparing a semi-annual-pay bond's nominal yield directly against an annual-pay bond's nominal yield without conversion understates the semi-annual bond's true annualized return.

### Converting Between Compounding Frequencies

**General formula — nominal rate under frequency $m_1$ to equivalent nominal rate under frequency $m_2$:**

$$\left(1 + \frac{r_1}{m_1}\right)^{m_1} = \left(1 + \frac{r_2}{m_2}\right)^{m_2}$$

Solve for $r_2$:

$$r_2 = m_2 \times \left[\left(1 + \frac{r_1}{m_1}\right)^{m_1/m_2} - 1\right]$$

**Worked Example:** Convert a semi-annual-pay bond yield of 8% (compounded semi-annually) to its equivalent annual-compounding rate.

Step 1 — Find EAR:

$$EAR = \left(1 + \frac{0.08}{2}\right)^2 - 1 = (1.04)^2 - 1 = 0.0816 = 8.16\%$$

Since annual compounding ($m=1$) means the nominal rate equals the EAR directly, the equivalent annual-pay rate is **8.16%**.

**Reverse direction — Worked Example:** Convert an annually-compounded rate of 8.16% to its semi-annual-pay equivalent.

$$r_{\text{semi}} = 2 \times \left[(1.0816)^{1/2} - 1\right] = 2 \times [1.04 - 1] = 2 \times 0.04 = 0.08 = 8.00\%$$

This confirms the reciprocal relationship — the two rates describe an identical economic return, just quoted under different compounding conventions.

### Bond-Equivalent Yield (BEY) — A Critical Fixed Income Convention

**[Verified — standard market convention]** In U.S. bond markets, a semi-annual-pay bond's yield to maturity is conventionally quoted as **two times the semi-annual discount rate** — NOT as the true effective annual rate. This is known as the Bond-Equivalent Yield (BEY), or "semi-annual bond basis" yield.

$$BEY = 2 \times r_{\text{semi-annual}}$$

**Why this convention exists:** [Inference] Historical market convention in U.S. bond markets standardizes quoting on a semi-annual bond basis because most U.S. bonds pay coupons semi-annually, making direct semi-annual-period comparison straightforward across the majority of the market, even though it understates the true effective annual return.

**Practical implication:** A BEY-quoted yield is **not** directly comparable to an EAR-quoted yield or to a yield on an annual-pay Eurobond without conversion — this is one of the most common sources of yield comparison errors between U.S. domestic bonds and internationally-quoted (often annual-pay) bonds.

**Worked Example — U.S. Treasury vs. Annual-Pay Eurobond:**

A U.S. Treasury note has a BEY of 5.00% (semi-annual pay). What is its true effective annual rate, for comparison against an annual-pay bond?

$$EAR = \left(1 + \frac{0.05}{2}\right)^2 - 1 = (1.025)^2 - 1 = 0.050625 = 5.0625\%$$

An annual-pay Eurobond would need to offer a **5.0625%** yield to be economically equivalent to the Treasury's 5.00% BEY — comparing the two headline numbers (5.00% vs. 5.0625%) directly without this conversion would incorrectly suggest the Eurobond offers a materially higher return, when in fact they are equivalent.

### Money Market Rate Conventions — An Additional Layer of Complexity

Money market instruments (T-bills, commercial paper, bankers' acceptances) introduce yet another convention layer:

| Convention | Basis | Typical Instruments |
| --- | --- | --- |
| Discount Yield (Bank Discount Basis) | Actual/360, based on face value | U.S. T-bills |
| Money Market Yield (CD Equivalent Yield) | Actual/360, based on purchase price | Commercial paper, CDs |
| Bond-Equivalent Yield (money market context) | Actual/365, based on purchase price | Used to compare money market instruments to coupon bonds |

**Discount Yield formula (T-bills):**

$$r_{BD} = \frac{F - P}{F} \times \frac{360}{t}$$

Where $F$ = face value, $P$ = purchase price, $t$ = days to maturity.

**[Inference — well-documented market quirk] Why Discount Yield understates true return:** Because it divides the dollar discount by *face value* rather than the *actual amount invested* ($P$), and annualizes using a 360-day year rather than 365, the bank discount yield is structurally lower than the bond-equivalent yield for the same instrument.

**Money Market Yield (converts discount yield to an investment/purchase-price basis):**

$$r_{MM} = \frac{360 \times r_{BD}}{360 - (t \times r_{BD})}$$

**Bond-Equivalent Yield conversion (from discount yield, for money market comparison to bonds):**

$$BEY \approx r_{MM} \times \frac{365}{360}$$

[Unverified as universally exact] Some conventions apply a more precise adjustment depending on whether the instrument's maturity is under or over 182 days (affecting whether simple or compounded semi-annual adjustment is used); the approximation above holds well for short maturities but exact formulas can vary by reference source.

### Diagram: Rate Conversion Pathways (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 740 320" font-family="Arial, sans-serif">
<text x="370" y="24" text-anchor="middle" font-size="15" font-weight="bold">Rate Convention Conversion Map (svg_diagram)</text>
<rect x="40" y="60" width="160" height="50" rx="6" fill="#e8f0fe" stroke="#1a5fb4" stroke-width="1.5" />
<text x="120" y="90" text-anchor="middle" font-size="12">Discount Yield (Bank Basis)</text>
<rect x="290" y="60" width="160" height="50" rx="6" fill="#e8f0fe" stroke="#1a5fb4" stroke-width="1.5" />
<text x="370" y="82" text-anchor="middle" font-size="12">Money Market</text>
<text x="370" y="98" text-anchor="middle" font-size="12">Yield (CD Basis)</text>
<rect x="540" y="60" width="160" height="50" rx="6" fill="#e8f0fe" stroke="#1a5fb4" stroke-width="1.5" />
<text x="620" y="82" text-anchor="middle" font-size="12">Bond-Equivalent</text>
<text x="620" y="98" text-anchor="middle" font-size="12">Yield (BEY)</text>
<line x1="200" y1="85" x2="285" y2="85" stroke="black" stroke-width="1.5" marker-end="url(#arr1)" />
<line x1="450" y1="85" x2="535" y2="85" stroke="black" stroke-width="1.5" marker-end="url(#arr1)" />
<rect x="290" y="200" width="160" height="50" rx="6" fill="#fdf0e8" stroke="#c0392b" stroke-width="1.5" />
<text x="370" y="222" text-anchor="middle" font-size="12">BEY (Semi-Annual</text>
<text x="370" y="238" text-anchor="middle" font-size="12">Bond Basis, 2×)</text>
<rect x="540" y="200" width="160" height="50" rx="6" fill="#fdf0e8" stroke="#c0392b" stroke-width="1.5" />
<text x="620" y="222" text-anchor="middle" font-size="12">Effective Annual</text>
<text x="620" y="238" text-anchor="middle" font-size="12">Rate (EAR)</text>
<line x1="450" y1="225" x2="535" y2="225" stroke="black" stroke-width="1.5" marker-end="url(#arr1)" />
<text x="490" y="215" text-anchor="middle" font-size="10">(1+r/2)² − 1</text>
</svg>

### Comprehensive Conversion Summary Table

| From → To | Formula |
| --- | --- |
| Nominal rate ($m$ periods) → EAR | $EAR = (1 + r/m)^m - 1$ |
| EAR → Nominal rate ($m$ periods) | $r = m \times [(1+EAR)^{1/m} - 1]$ |
| Semi-annual BEY → EAR | $EAR = (1 + BEY/2)^2 - 1$ |
| EAR → Semi-annual BEY | $BEY = 2 \times [(1+EAR)^{1/2} - 1]$ |
| Discount Yield → Money Market Yield | $r_{MM} = \dfrac{360 \times r_{BD}}{360 - (t \times r_{BD})}$ |
| Money Market Yield → Bond-Equivalent Yield | $BEY \approx r_{MM} \times \dfrac{365}{360}$ |

### Practical Significance in Portfolio and Relative Value Analysis

- **Cross-market comparison:** Comparing a U.S. corporate bond (semi-annual BEY), a European Eurobond (annual pay), and a U.S. T-bill (discount yield) requires converting all three to a common basis (typically EAR or a common BEY) before any valid relative value judgment can be made.
- **Model inputs:** Discounted cash flow models, duration calculations, and portfolio-level yield aggregation all require consistent rate bases — mixing BEY inputs with EAR-based discount factors without conversion introduces systematic pricing errors.
- **Regulatory/reporting standards:** [Inference] Many jurisdictions' bond disclosure standards specify which yield convention must be quoted for retail-facing bond disclosures, though the specific required convention depends on the applicable regulatory regime and is outside the scope of a purely technical/quantitative treatment.

### Key Points

- Nominal (quoted) rates and Effective Annual Rates (EAR) differ whenever compounding occurs more than once per year; EAR reflects the true annualized return.
- U.S. bond markets conventionally quote yields on a semi-annual Bond-Equivalent Yield (BEY) basis — twice the semi-annual periodic rate — which understates the true effective annual return.
- Money market instruments add further convention layers (discount yield, money market yield, BEY) that must be converted before valid comparison to coupon-bearing bonds.
- Failing to convert between rate conventions before comparing instruments is one of the most common sources of relative-value analysis error in fixed income.
- All conversions ultimately reduce to correctly applying the compounding formula $(1 + r/m)^m$ and solving for the desired equivalent rate basis.

**Related Topics**

- Yield to Maturity: Definition, Calculation, and Assumptions
- U.S. Treasury Bill Pricing and Discount Yield Mechanics
- Cross-Currency and Cross-Market Bond Yield Comparison
- Term Structure of Interest Rates and the Yield Curve
- Floating-Rate Note Pricing and Reference Rate Reset Conventions
- Total Return Analysis and Reinvestment Rate Assumptions