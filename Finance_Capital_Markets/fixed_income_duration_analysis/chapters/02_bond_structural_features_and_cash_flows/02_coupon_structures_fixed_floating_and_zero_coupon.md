## Coupon Structures: Fixed, Floating, and Zero Coupon


### Overview

The coupon structure of a bond determines the pattern, timing, and rate-sensitivity of its periodic cash flows, and is one of the most fundamental drivers of a bond's interest rate risk profile. The three primary structural categories — fixed-rate, floating-rate, and zero-coupon — exhibit fundamentally different price sensitivities to interest rate changes, making coupon structure a first-order consideration in duration analysis, alongside maturity and credit quality.

### Fixed-Rate Bonds

#### Structure

A fixed-rate bond pays a constant coupon amount at regular intervals (annually, semiannually, or quarterly, depending on market convention) throughout its life, calculated as:

$$\text{Coupon Payment} = \frac{\text{Coupon Rate}}{\text{Payments per Year}} \times \text{Face Value}$$

The coupon rate is set at issuance and does not change regardless of subsequent market rate movements.

#### Price Behavior

Because future cash flows are fixed in nominal terms, the price of a fixed-rate bond moves **inversely** to market yields: when yields rise, the present value of fixed future cash flows falls, and vice versa. This inverse price-yield relationship is the foundation of duration as a risk measure.

- **Premium bond**: Coupon rate > market yield → price above par
- **Discount bond**: Coupon rate < market yield → price below par
- **Par bond**: Coupon rate = market yield → price equals par

#### Duration Characteristics

Fixed-rate bonds carry the full spectrum of interest rate risk implied by their maturity and coupon level. All else equal:

- Lower coupon → higher duration (more of the bond's value is concentrated in the distant principal repayment, increasing the weighted-average time to cash flow receipt)
- Longer maturity → higher duration
- Higher yield level → lower duration (a mathematical property of the duration formula, since higher discount rates reduce the relative weight of distant cash flows)

### Floating-Rate Notes (FRNs)

#### Structure

A floating-rate note pays a coupon that resets periodically based on a reference rate plus a fixed spread (the "quoted margin" or "spread"):

$$\text{Coupon Rate} = \text{Reference Rate} + \text{Spread}$$

Common reference rates include:

- **SOFR (Secured Overnight Financing Rate)**: The dominant USD reference rate following the transition away from LIBOR, typically compounded over the interest period for term structures
- **EURIBOR**: Common reference rate for euro-denominated FRNs
- **SONIA**: Sterling Overnight Index Average, used for GBP-denominated floaters
- Other jurisdiction-specific risk-free rates (e.g., TONA in Japan)

[Unverified: reference rate conventions and compounding methodologies continue to evolve post-LIBOR transition and specific current market standard practices should be confirmed against current issuance documentation]

Coupons typically reset at the start of each interest period (e.g., quarterly), with the payment made at the end of the period based on the rate observed/compounded during that period.

#### Price Behavior

Because the coupon resets periodically to reflect current market rates, a floating-rate note's price remains close to par between reset dates, since the coupon largely "catches up" to prevailing rates at each reset. The primary source of price volatility between resets is:

- **Credit spread risk**: If the issuer's credit spread widens (perceived credit risk increases) relative to the fixed spread set at issuance, the FRN's price will fall below par, since the fixed spread no longer compensates for the now-higher required spread
- **Basis risk between reset dates**: Minor price fluctuations can occur due to the time value of the period between the current date and the next reset

#### Duration Characteristics

Floating-rate notes have very low **interest rate duration** (typically approximated by the time to the next coupon reset date, often a fraction of a year), because the coupon adjusts to neutralize the effect of rate changes on present value beyond the current reset period. However, FRNs retain **full credit spread duration** approximately equal to their time to maturity, since the fixed spread component does not adjust for changing credit conditions.

This duration decomposition — near-zero rate duration, full-maturity spread duration — is a key distinguishing feature of floaters relative to fixed-rate bonds and is central to why floating-rate instruments are used to hedge or reduce interest rate risk while retaining credit exposure.

#### Floater Variants

- **Inverse floaters**: Coupon moves inversely to the reference rate (e.g., Coupon = Fixed Rate − Reference Rate), producing amplified interest rate sensitivity, effectively combining leveraged duration exposure with the floating structure
- **Capped/floored floaters**: Include a maximum (cap) or minimum (floor) coupon rate, introducing embedded optionality that requires effective duration analysis rather than simple approximation
- **Step-up notes**: Coupon increases according to a predetermined schedule (not market-rate-linked), often paired with issuer call options

### Zero-Coupon Bonds

#### Structure

A zero-coupon bond pays no periodic interest. It is issued at a discount to face value and redeemed at full face value at maturity, with the investor's entire return derived from this price appreciation:

$$P_0 = \frac{FV}{(1+y)^n}$$

where $FV$ is face value, $y$ is the yield, and $n$ is the number of periods to maturity.

Examples include Treasury STRIPS (Separate Trading of Registered Interest and Principal of Securities), zero-coupon municipal bonds, and original-issue discount corporate bonds.

#### Duration Characteristics

For a zero-coupon bond, **Macaulay duration equals the bond's time to maturity exactly**, since there is only a single cash flow (the face value payment) and the weighted-average time to receipt is simply that single payment date. This is the maximum possible duration for any bond of a given maturity — a zero-coupon bond has strictly higher duration than a coupon-bearing bond of the same maturity, because coupon payments received before maturity reduce the weighted-average time to cash flow receipt.

This property makes zero-coupon bonds a useful tool for:

- Precisely targeting a specific duration/maturity for liability matching (e.g., pension funds hedging a known future liability)
- Constructing the theoretical spot (zero) curve, since each zero-coupon bond's yield directly represents the spot rate for its specific maturity, without the cash-flow-timing distortions present in coupon bond yields

### Comparative Summary

**Key Points**

| Structure | Coupon Behavior | Interest Rate Duration | Credit Spread Duration | Primary Use Case |
| --- | --- | --- | --- | --- |
| Fixed-rate | Constant | Full, per maturity/coupon | Full, per maturity | Standard income, duration targeting |
| Floating-rate | Resets to reference rate + spread | Very low (~time to next reset) | Full, per maturity | Rate risk minimization, credit exposure |
| Zero-coupon | No periodic coupon | Maximum (= time to maturity) | Full, per maturity | Precise duration/liability matching |

### Coupon Structure Comparison Diagram

```mermaid
flowchart TD
    A[Coupon Structures (svg_diagram)] --> B[Fixed-Rate]
    A --> C[Floating-Rate]
    A --> D[Zero-Coupon]

    B --> B1[Constant Periodic Coupon]
    B1 --> B2[Full Interest Rate Duration per Maturity]

    C --> C1[Reference Rate + Fixed Spread]
    C1 --> C2[Periodic Reset]
    C2 --> C3[Low Interest Rate Duration]
    C1 --> C4[Full Credit Spread Duration]
    C --> C5[Variants: Inverse, Capped/Floored, Step-Up]

    D --> D1[Single Cash Flow at Maturity]
    D1 --> D2[Macaulay Duration = Time to Maturity]
    D1 --> D3[Maximum Duration for Given Maturity]
```

### Example

Consider three 10-year bonds issued by the same issuer at the same time, each with a face value of $1,000:

1. **Fixed-rate bond**, 5% semiannual coupon: Macaulay duration ≈ 7.8 years (illustrative, depends on yield level)
2. **Floating-rate note**, SOFR + 100bp, quarterly reset: Interest rate duration ≈ 0.25 years (time to next reset); credit spread duration ≈ 10 years
3. **Zero-coupon bond**: Macaulay duration = exactly 10.0 years

If market interest rates rise by 100 basis points uniformly, the zero-coupon bond experiences the largest price decline, the fixed-rate bond experiences a moderate decline, and the floating-rate note experiences a negligible price change from the rate move itself (though its price may still move if the issuer's credit spread changes independently).

### Relevance to Duration Analysis

- Coupon structure is a primary determinant of a bond's interest rate duration independent of maturity, making it a critical input alongside maturity and yield level in any duration calculation
- Floating-rate notes illustrate the necessity of **decomposing duration into interest rate duration and credit spread duration** as distinct risk factors, since a single "duration" figure can be misleading for hedging purposes if this decomposition is not made
- Zero-coupon bonds serve as the building blocks for **spot curve construction** and **key rate duration** analysis, since their yields map directly to specific points on the term structure without coupon reinvestment assumptions distorting the measurement

**Next Steps**

- **Related Topics**: Macaulay and Modified Duration Formulas, Credit Spread Duration vs. Interest Rate Duration, Yield Curve and Spot Rate Construction, SOFR and Post-LIBOR Reference Rate Transition, Key Rate Duration and Partial Duration Measures, Treasury STRIPS and Zero-Coupon Bond Markets, Capped and Floored Floating-Rate Note Analysis