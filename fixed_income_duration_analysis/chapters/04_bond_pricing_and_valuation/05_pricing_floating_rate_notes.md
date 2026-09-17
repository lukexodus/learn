## Pricing Floating Rate Notes

### Core Concept

A floating-rate note (FRN) pays a coupon that resets periodically based on a reference rate (e.g., SOFR, EURIBOR) plus a fixed spread, rather than paying a constant coupon throughout its life. This structural difference fundamentally changes the note's valuation dynamics: because the coupon itself adjusts to reflect prevailing market rates, an FRN's price remains far closer to par across a much wider range of interest rate environments than a fixed-rate bond of comparable maturity — the defining practical characteristic that makes FRNs attractive for investors seeking to minimize interest rate risk.

### Coupon Reset Mechanics

**Standard structure:**

$$\text{Coupon Rate} = \text{Reference Rate} + \text{Quoted Margin (Spread)}$$

At each reset date, the coupon for the *upcoming* period is typically set based on the reference rate observed *at the start* of that period (in arrears-set structures) or, less commonly in modern markets, based on the rate observed at the end of the period (a "compounded in arrears" approach, increasingly standard following the transition to overnight risk-free rates such as SOFR).

**Key terminology:**

| Term | Definition |
| --- | --- |
| Reference rate | The benchmark rate used for resets (e.g., SOFR, Term SOFR, EURIBOR) |
| Quoted margin | The fixed spread added to the reference rate, set at issuance based on the issuer's credit quality at that time |
| Reset frequency | How often the coupon resets (commonly quarterly or semi-annually, though other frequencies exist) |
| Cap / Floor | Optional embedded features limiting the maximum or minimum coupon rate, regardless of where the reference rate moves |

### Why FRN Prices Stay Close to Par

**Core intuition:** A fixed-rate bond's price must adjust when market yields change, because its coupon cannot adjust — the bond's *price* is the only variable left to bring its return in line with the new market yield. An FRN's coupon, by contrast, adjusts automatically at each reset date to reflect the *current* reference rate, meaning the note's income stream tracks the market rather than requiring a price change to stay competitive.

**[Inference — standard textbook simplification]** If an FRN's quoted margin remains appropriate for the issuer's credit quality (i.e., the issuer's credit risk hasn't changed since issuance) and the reference rate used for discounting matches the reference rate used for the coupon reset, the note's price should trade very close to par immediately following each reset date, since the coupon for the upcoming period is set to exactly match the current required return.

### Simplified FRN Pricing Formula (At a Reset Date)

Immediately following a coupon reset, assuming no change in credit spread since issuance, an FRN can be valued as if it were a bond maturing at the *next* reset date, since the coupon for that single period is already known and fixed:

$$P = \frac{(\text{Reference Rate} + \text{Margin}) \times F / m + F}{1 + (\text{Discount Rate})/m}$$

Where $m$ is the number of reset periods per year. This simplification reflects that an FRN can conceptually be viewed as a series of very short-maturity, known-coupon instruments strung together, with the market's uncertainty about future coupons resolved at each reset.

### Full Valuation: Discounted Cash Flow With Projected Coupons

For valuation between reset dates, or when credit spread has changed since issuance, a more complete approach discounts each expected future coupon (using forward rates implied by the current curve to project future reference rate resets) plus the final principal repayment:

$$P = \sum_{t=1}^{n} \frac{(\hat{r}_t + \text{Margin}) \times F/m}{(1+d_t)^t} + \frac{F}{(1+d_n)^n}$$

Where:

- $\hat{r}_t$ = the projected reference rate for period $t$, typically derived from the forward curve (see spot vs. forward rate mechanics)
- $\text{Margin}$ = the note's fixed quoted margin
- $d_t$ = the appropriate discount rate for period $t$ (which may itself embed a current market-required spread, distinct from the note's own fixed quoted margin)

### Worked Example — Simplified At-Reset Valuation

**Given:** An FRN with $1,000 face value, quarterly resets, reference rate (3-month SOFR) currently at 4.20%, quoted margin of 0.50%, and the note has just reset. Assume the market-required discount rate for this issuer's credit quality remains unchanged at reference rate + margin (i.e., 4.70% annualized).

**Coupon for the upcoming quarter:**

$$C = (0.0420 + 0.0050) \times \frac{1000}{4} = 0.0470 \times 250 = \$11.75$$

**Since the discount rate exactly matches the coupon rate (no change in required spread), the note prices at par:**

$$P = \frac{11.75 + 1000}{1 + 0.0470/4} = \frac{1011.75}{1.01175} = \$1{,}000.00$$

This confirms the theoretical result: immediately after a reset, with no change in credit spread, an FRN prices at exactly par.

### Diagram: FRN Coupon Reset and Price Behavior (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 740 300" font-family="Arial, sans-serif">
<text x="370" y="24" text-anchor="middle" font-size="15" font-weight="bold">FRN Price Behavior Across Reset Dates (svg_diagram)</text>
<line x1="70" y1="240" x2="670" y2="240" stroke="black" stroke-width="1.5" />
<line x1="70" y1="60" x2="70" y2="240" stroke="black" stroke-width="1.5" />
<text x="370" y="265" text-anchor="middle" font-size="12">Time (quarterly reset dates)</text>
<text x="35" y="150" text-anchor="middle" font-size="12" transform="rotate(-90 35 150)">Price</text>
<line x1="70" y1="150" x2="670" y2="150" stroke="gray" stroke-dasharray="5,3" />
<text x="675" y="154" font-size="11" fill="gray">Par</text>
<path d="M 70 150 Q 130 130, 190 150" fill="none" stroke="#1a5fb4" stroke-width="2.5" />
<path d="M 190 150 Q 250 165, 310 150" fill="none" stroke="#1a5fb4" stroke-width="2.5" />
<path d="M 310 150 Q 370 135, 430 150" fill="none" stroke="#1a5fb4" stroke-width="2.5" />
<path d="M 430 150 Q 490 160, 550 150" fill="none" stroke="#1a5fb4" stroke-width="2.5" />
<line x1="190" y1="145" x2="190" y2="155" stroke="black" stroke-width="2" />
<text x="190" y="200" text-anchor="middle" font-size="10">Reset 1</text>
<line x1="310" y1="145" x2="310" y2="155" stroke="black" stroke-width="2" />
<text x="310" y="200" text-anchor="middle" font-size="10">Reset 2</text>
<line x1="430" y1="145" x2="430" y2="155" stroke="black" stroke-width="2" />
<text x="430" y="200" text-anchor="middle" font-size="10">Reset 3</text>

<text x="370" y="90" text-anchor="middle" font-size="11" fill="`#1a5fb4`">Small deviations between resets; price pulls back to par at each reset</text>

</svg>

### Why FRN Prices Still Deviate Slightly From Par

Despite the strong pull toward par, real-world FRN prices are rarely exactly at par at all times, for several reasons:

| Factor | Effect on Price |
| --- | --- |
| Credit spread changes since issuance | If the issuer's credit quality deteriorates (requiring a higher spread than the note's fixed quoted margin), the note trades below par, and vice versa if credit quality improves |
| Time between reset dates | Between resets, the coupon is fixed for that period even though the reference rate may be moving, creating a small "fixed-rate-like" exposure for the remainder of the current period |
| Cap/floor features | Embedded caps or floors introduce option-like value components that can cause persistent deviation from a simple par-pricing assumption, particularly if the reference rate approaches the cap or floor level |
| Reset lag / rate-setting convention | Structures using an averaging or lookback period, or an "in arrears" versus "in advance" reset convention, introduce a small basis between the coupon actually paid and the "pure" prevailing rate at any instant |

### Discount Margin — The FRN Analogue to Yield Spread

**Definition:** The **discount margin (DM)** is the spread that, when added to the current reference rate and used to discount an FRN's projected cash flows, produces a present value exactly equal to the note's current market price.

$$P_{\text{market}} = \sum_{t=1}^{n} \frac{(\hat{r}_t + \text{Quoted Margin}) \times F/m}{\left(1+\frac{\hat{r}_t + DM}{m}\right)^t} + \frac{F}{\left(1+\frac{\hat{r}_n + DM}{m}\right)^n}$$

**Interpretation:**

- If $DM$ = the note's quoted margin, the note trades at par.
- If $DM$ > the note's quoted margin, the note trades at a discount (the market now requires more spread compensation than the note's fixed contractual margin provides — typically reflecting credit deterioration or a wider market-required spread environment).
- If $DM$ < the note's quoted margin, the note trades at a premium (the market requires less spread than the note contractually pays).

### Comparison: FRN vs. Fixed-Rate Bond Interest Rate Sensitivity

| Attribute | Fixed-Rate Bond | Floating-Rate Note |
| --- | --- | --- |
| Coupon behavior | Constant throughout life | Resets periodically to track reference rate |
| Price sensitivity to general rate level changes | High (full bond duration) | Very low (duration approximately equal to time to next reset) |
| Price sensitivity to issuer credit spread changes | Reflected fully in price movement | Also reflected in price movement (since only the *reference rate* component resets, not the credit spread component) |
| Effective duration | Approximately equal to Macaulay duration of the full cash flow schedule | Approximately equal to the time remaining until the next coupon reset date |

**[Inference]** This last point — that an FRN's effective duration approximates only the time to the next reset — is the standard simplified textbook treatment; more precise duration measures for FRNs with caps, floors, or credit spread risk require more detailed option-adjusted or spread-duration frameworks that separate general interest rate sensitivity from credit spread sensitivity.

### Key Points

- An FRN's coupon resets periodically to a reference rate plus a fixed quoted margin, causing its price to track much closer to par across changing rate environments than a fixed-rate bond.
- Immediately following a reset, assuming no change in required credit spread, an FRN theoretically prices at exactly par.
- Persistent deviations from par arise primarily from changes in the issuer's credit spread since issuance, embedded caps/floors, and the natural fixed-rate-like exposure during the period between resets.
- The discount margin (DM) is the FRN-specific analogue to yield spread — the spread over the reference rate that equates discounted projected cash flows to the observed market price.
- FRN effective duration is dramatically shorter than a comparable fixed-rate bond, approximating only the time to the next coupon reset, making FRNs a common tool for managing interest rate risk exposure.

**Related Topics**

- Discount Margin Calculation and Interpretation
- Effective Duration for Floating-Rate and Option-Embedded Instruments
- Reference Rate Transition: SOFR, Compounding-in-Arrears Conventions
- Credit Spread Risk versus Interest Rate Risk Decomposition
- Interest Rate Swaps and Floating-Rate Leg Valuation
- Capped and Floored Floating-Rate Notes: Embedded Option Analysis