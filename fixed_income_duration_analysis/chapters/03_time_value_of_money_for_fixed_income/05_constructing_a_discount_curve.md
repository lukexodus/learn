## Constructing a Discount Curve


### Core Concept

A discount curve is the complete set of discount factors $DF(t)$ across all relevant maturities, providing the single consistent framework needed to value any fixed income cash flow occurring at any point in time. Constructing this curve is a practical, multi-step process that synthesizes several concepts already covered — present value mechanics, day count conventions, bootstrapping, and the spot/forward rate relationship — into a coherent methodology used throughout fixed income pricing, risk management, and derivatives valuation.

### Why a Discount Curve Is Needed

A single flat yield is only ever an approximation. Real markets exhibit yield curves that are rarely flat, meaning the "correct" discount rate for a cash flow occurring in 6 months genuinely differs from the correct discount rate for a cash flow occurring in 10 years. A discount curve resolves this by providing a *specific* discount factor for *every* relevant maturity, ensuring internally consistent valuation across an entire portfolio of instruments with different maturity profiles.

### Step-by-Step Construction Methodology

**Step 1 — Select Input Instruments**

Choose the most liquid, reliable market instruments available at each maturity segment of the curve. A typical layered approach:

| Maturity Segment | Typical Input Instruments |
| --- | --- |
| Short end (0–1 year) | Money market instruments: T-bills, deposit rates, commercial paper |
| Belly (1–2 years) | Short-dated coupon bonds, or interest rate futures (e.g., Eurodollar/SOFR futures strips) |
| Long end (2+ years) | Liquid on-the-run coupon bonds (Treasuries or benchmark government bonds), interest rate swap rates |

**Step 2 — Convert All Inputs to a Consistent Basis**

Before combining instruments quoted under different conventions, all rates must be converted to a common day count convention and compounding basis (as covered under compounding frequency and rate conversions) — mixing an Actual/360 money market rate with a 30/360 bond yield without conversion introduces systematic errors into the resulting curve.

**Step 3 — Bootstrap Sequentially From Short to Long Maturities**

Using the shortest, most direct instruments first (ideally already zero-coupon, like T-bills), solve sequentially for each successive maturity's discount factor or spot rate, using previously-solved shorter discount factors to strip out known cash flows from each subsequent coupon-bearing instrument's price — exactly the bootstrapping process outlined for zero-coupon rate derivation.

**Step 4 — Interpolate for Maturities Between Input Points**

Since traded instruments exist only at discrete maturities (e.g., 1yr, 2yr, 5yr, 10yr, 30yr for Treasuries), a discount curve intended for continuous use must fill in the gaps between these points via interpolation.

### Interpolation Methods

| Method | Description | Trade-off |
| --- | --- | --- |
| Linear interpolation (on rates) | Straight-line interpolation between two known spot rates | Simple, but produces a discount curve with kinks (discontinuous first derivative) at each input node |
| Linear interpolation (on log discount factors) | Interpolates $\ln(DF(t))$ linearly, then exponentiates | Smoother forward rate implications than linear-on-rate interpolation |
| Cubic spline | Fits a smooth piecewise cubic polynomial through all input points | Produces smoother curves and forward rates; more computationally involved and can introduce oscillation ("overshoot") between widely-spaced points |
| Nelson-Siegel / Svensson parametric models | Fits a small number of parameters to a functional form describing the entire curve shape | Produces a smooth, parsimonious curve; widely used by central banks for yield curve reporting; may not perfectly reprice every input instrument exactly |

**[Inference]** No single interpolation method is universally regarded as "correct" — the choice involves a genuine trade-off between exact repricing of input instruments (favoring bootstrapping-consistent methods) and curve/forward-rate smoothness (favoring spline or parametric methods), and different institutions and use cases favor different approaches.

### Worked Example: Building a Short Discount Curve

**Given inputs:**

- 6-month T-bill: discount yield 3.8% (Actual/360, bank discount basis)
- 1-year deposit rate: 4.0% (Actual/360, simple interest)
- 2-year bond: 4.5% annual coupon, priced at par (i.e., its coupon = its yield, since it trades at par)

**Step 1 — Convert the 6-month T-bill discount yield to a spot rate (bond-equivalent basis, Actual/365):**

Using the money-market-yield conversion:

$$r_{MM} = \frac{360 \times 0.038}{360 - (182 \times 0.038)} = \frac{13.68}{353.084} = 0.03875$$



$$z_{0.5} \approx 0.03875 \times \frac{365}{360} = 0.0393 = 3.93\%$$

**Step 2 — Convert the 1-year deposit rate:**

Simple interest at 4.0% for a full year, Actual/360 basis, adjusted to Actual/365:

$$z_1 = 0.04 \times \frac{365}{360} = 0.0406 = 4.06\%$$

**Step 3 — Bootstrap the 2-year zero rate from the par bond:**

Since the 2-year bond trades at par with a 4.5% coupon:

$$100 = \frac{4.5}{(1+z_1)^1} + \frac{104.5}{(1+z_2)^2}$$



$$100 = \frac{4.5}{1.0406} + \frac{104.5}{(1+z_2)^2}$$



$$100 - 4.3244 = 95.6756 = \frac{104.5}{(1+z_2)^2}$$



$$(1+z_2)^2 = 1.09225 \implies z_2 = 0.0451 = 4.51\%$$

**Resulting bootstrapped discount curve:**

| Maturity | Zero Rate | Discount Factor |
| --- | --- | --- |
| 0.5 yr | 3.93% | $1/(1.0393)^{0.5} = 0.9809$ |
| 1.0 yr | 4.06% | $1/(1.0406)^{1} = 0.9610$ |
| 2.0 yr | 4.51% | $1/(1.0451)^{2} = 0.9159$ |

### Diagram: End-to-End Discount Curve Construction Process (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 740 340" font-family="Arial, sans-serif">
<text x="370" y="24" text-anchor="middle" font-size="15" font-weight="bold">Discount Curve Construction Pipeline (svg_diagram)</text>
<rect x="30" y="60" width="150" height="55" rx="6" fill="#e8f0fe" stroke="#1a5fb4" stroke-width="1.5" />
<text x="105" y="83" text-anchor="middle" font-size="11">1. Select input</text>
<text x="105" y="99" text-anchor="middle" font-size="11">instruments</text>
<rect x="215" y="60" width="150" height="55" rx="6" fill="#e8f0fe" stroke="#1a5fb4" stroke-width="1.5" />
<text x="290" y="83" text-anchor="middle" font-size="11">2. Convert to</text>
<text x="290" y="99" text-anchor="middle" font-size="11">common basis</text>
<rect x="400" y="60" width="150" height="55" rx="6" fill="#e8f0fe" stroke="#1a5fb4" stroke-width="1.5" />
<text x="475" y="83" text-anchor="middle" font-size="11">3. Bootstrap</text>
<text x="475" y="99" text-anchor="middle" font-size="11">short → long</text>
<rect x="585" y="60" width="150" height="55" rx="6" fill="#e8f0fe" stroke="#1a5fb4" stroke-width="1.5" />
<text x="660" y="83" text-anchor="middle" font-size="11">4. Interpolate</text>
<text x="660" y="99" text-anchor="middle" font-size="11">between nodes</text>
<line x1="180" y1="87" x2="210" y2="87" stroke="black" stroke-width="1.5" marker-end="url(#arrC)" />
<line x1="365" y1="87" x2="395" y2="87" stroke="black" stroke-width="1.5" marker-end="url(#arrC)" />
<line x1="550" y1="87" x2="580" y2="87" stroke="black" stroke-width="1.5" marker-end="url(#arrC)" />
<rect x="215" y="220" width="330" height="70" rx="6" fill="#fdf0e8" stroke="#c0392b" stroke-width="1.5" />
<text x="380" y="248" text-anchor="middle" font-size="12">Complete Discount Curve</text>
<text x="380" y="266" text-anchor="middle" font-size="11">DF(t) available for any maturity t</text>
<text x="380" y="282" text-anchor="middle" font-size="11">→ used for pricing, risk, derivatives valuation</text>
<line x1="475" y1="115" x2="380" y2="215" stroke="black" stroke-width="1.5" marker-end="url(#arrC)" />
<line x1="660" y1="115" x2="450" y2="215" stroke="black" stroke-width="1.5" marker-end="url(#arrC)" />
</svg>

### Single-Curve vs. Multi-Curve Frameworks

**[Verified — a significant post-2008 market structure development]** Prior to the 2008 global financial crisis, practitioners commonly used a single discount curve (typically derived from interbank rates like LIBOR) for both discounting cash flows and projecting floating-rate forward rates. Following the crisis, meaningful and persistent spreads emerged between different reference rates that had previously moved together closely (e.g., interbank lending rates vs. overnight index swap rates), leading to the now-standard **multi-curve framework**:

| Curve | Purpose |
| --- | --- |
| Discounting (OIS) curve | Used to discount all cash flows, typically built from overnight index swap rates, reflecting a lower-credit-risk collateralized borrowing rate |
| Forward/projection curve(s) | Used to project expected future floating-rate resets (e.g., derived from SOFR-based instruments), separate from the discounting curve |

[Inference] The specific reference rates used for both discounting and projection have continued to evolve with the broader industry-wide transition away from LIBOR toward risk-free reference rates (such as SOFR in the U.S.); practitioners should verify current market-standard reference rates rather than relying on older conventions, as this area has been subject to substantial structural change.

### Curve Quality and Validation Checks

- **Positivity of forward rates:** A well-constructed curve should generally avoid implying deeply negative forward rates unless the underlying market genuinely reflects negative-rate conditions (as has occurred in some markets, e.g., parts of Europe and Japan in past periods).
- **Smoothness of the forward curve:** Even if the spot/discount curve itself looks reasonably smooth, the *forward* rates implied by it can reveal hidden oscillation or artifacts from poor interpolation choice — forward curve smoothness is often a more sensitive diagnostic than spot curve smoothness alone.
- **Repricing accuracy:** The constructed curve should exactly (or very nearly) reprice all the input instruments used to build it — a material repricing error signals a bootstrapping or interpolation implementation issue.

### Key Points

- A discount curve provides a complete, maturity-specific discount factor for any cash flow date, superseding the simplifying single-flat-yield approximation.
- Construction requires selecting liquid input instruments, converting all rates to a consistent basis, bootstrapping sequentially from short to long maturities, and interpolating between the resulting nodes.
- Interpolation method choice (linear, log-linear, spline, parametric) involves a trade-off between exact input repricing and overall curve/forward-rate smoothness.
- Modern post-financial-crisis practice generally separates the discounting curve (often OIS-based) from the forward/projection curve(s) used for floating-rate cash flow estimation.
- Validating a constructed curve includes checking repricing accuracy against its own inputs and examining the smoothness of its *implied forward rates*, not just the spot curve itself.

**Related Topics**

- Bootstrapping the Zero-Coupon Curve from Coupon Bond Prices
- Spot Rates versus Forward Rates
- Interest Rate Swap Curve Construction and OIS Discounting
- Nelson-Siegel and Svensson Yield Curve Models
- Post-LIBOR Reference Rate Transition (SOFR and Alternatives)
- Key Rate Duration and Curve Risk Decomposition