## Spot Rates versus Forward Rates

### Core Concept

Spot rates and forward rates are two related but distinct interest rate concepts derived from the same underlying term structure. A **spot rate** is the rate applicable to a single cash flow received *starting today* and maturing at a specific future date. A **forward rate** is an implied rate applicable to a period that begins at some point *in the future*, not today — it is not directly observed in the market but is mathematically embedded in, and derivable from, the current spot rate curve under the assumption of arbitrage-free pricing.

### Spot Rates — Recap and Formal Definition

The spot rate $z_t$ (or zero-coupon rate) for maturity $t$ is the annualized yield on a hypothetical zero-coupon instrument purchased today and maturing at time $t$, with no intervening cash flows.

$$DF(t) = \frac{1}{(1+z_t)^t}$$

Spot rates form the full **spot curve** (or zero-coupon yield curve) — a rate for every observable/bootstrapped maturity point, from which all bond pricing and forward rate calculations are derived.

### Forward Rates — Formal Definition

A forward rate $f_{a,b}$ represents the interest rate, implied by today's spot curve, applicable to a period starting $a$ years from today and lasting $b$ years (i.e., ending at time $a+b$).

**Notation convention (commonly used):** $f_{a,b}$ = the $b$-year rate, $a$ years forward.

**No-arbitrage relationship linking spot and forward rates:**

Investing for $(a+b)$ years at the spot rate must produce the same total return as investing for $a$ years at the spot rate and then reinvesting for $b$ more years at the forward rate implied today — otherwise, an arbitrage opportunity would exist.

$$(1 + z_{a+b})^{a+b} = (1 + z_a)^a \times (1 + f_{a,b})^b$$

Solving for the forward rate:

$$f_{a,b} = \left[\frac{(1+z_{a+b})^{a+b}}{(1+z_a)^a}\right]^{1/b} - 1$$

### Why the No-Arbitrage Condition Must Hold

**Intuition:** Suppose the implied forward rate were *not* consistent with this equation — say, the actual forward rate available via a forward-rate-locking transaction were higher than what the spot curve implies. An arbitrageur could:

1. Borrow at the shorter spot rate $z_a$ for $a$ years
2. Simultaneously lock in the (higher-than-implied) forward rate for the subsequent $b$-year period
3. Invest the proceeds at the longer spot rate $z_{a+b}$ for the full $(a+b)$ years

This would generate a riskless profit with no net capital outlay — a violation of the no-arbitrage principle that underpins nearly all fixed income relative value theory. Market forces (arbitrageurs exploiting exactly this mispricing) drive forward rates observed in derivatives markets (like forward rate agreements) back toward consistency with the spot curve.

### Worked Example: Computing a Forward Rate from the Spot Curve

Given a spot curve:

- $z_1 = 4.00\%$ (1-year spot rate)
- $z_2 = 4.52\%$ (2-year spot rate)
- $z_3 = 5.00\%$ (3-year spot rate)

**Calculate the 1-year rate, 1 year forward ($f_{1,1}$) — i.e., the implied rate for year 2 alone:**

$$f_{1,1} = \frac{(1+z_2)^2}{(1+z_1)^1} - 1 = \frac{(1.0452)^2}{1.04} - 1 = \frac{1.09244}{1.04} - 1 = 0.0504 = 5.04\%$$

**Calculate the 1-year rate, 2 years forward ($f_{2,1}$) — i.e., the implied rate for year 3 alone:**

$$f_{2,1} = \frac{(1+z_3)^3}{(1+z_2)^2} - 1 = \frac{(1.05)^3}{(1.0452)^2} - 1 = \frac{1.157625}{1.09244} - 1 = 0.0599 = 5.99\%$$

**Calculate the 2-year rate, 1 year forward ($f_{1,2}$) — i.e., the implied 2-year rate starting in year 2:**

$$f_{1,2} = \left[\frac{(1+z_3)^3}{(1+z_1)^1}\right]^{1/2} - 1 = \left[\frac{1.157625}{1.04}\right]^{1/2} - 1 = (1.11310)^{0.5} - 1 = 0.0550 = 5.50\%$$

These implied forward rates (5.04%, 5.99%) rising above the spot rates (4.00%, 4.52%, 5.00%) is a direct algebraic consequence of the *upward-sloping* spot curve in this example.

### Diagram: Spot Curve vs. Implied Forward Rates (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 740 320" font-family="Arial, sans-serif">
<text x="370" y="24" text-anchor="middle" font-size="15" font-weight="bold">Spot Rates vs. Implied Forward Rates (svg_diagram)</text>
<line x1="80" y1="270" x2="660" y2="270" stroke="black" stroke-width="1.5" />
<line x1="80" y1="40" x2="80" y2="270" stroke="black" stroke-width="1.5" />
<text x="370" y="295" text-anchor="middle" font-size="12">Maturity / Period (years)</text>
<text x="35" y="155" text-anchor="middle" font-size="12" transform="rotate(-90 35 155)">Rate (%)</text>
<circle cx="160" cy="230" r="4" fill="#1a5fb4" />
<circle cx="330" cy="200" r="4" fill="#1a5fb4" />
<circle cx="500" cy="170" r="4" fill="#1a5fb4" />
<path d="M 160 230 L 330 200 L 500 170" fill="none" stroke="#1a5fb4" stroke-width="2.5" />
<text x="600" y="165" font-size="11" fill="#1a5fb4">Spot curve (z₁, z₂, z₃)</text>

<text x="160" y="248" text-anchor="middle" font-size="10">4.00%</text>

<text x="330" y="218" text-anchor="middle" font-size="10">4.52%</text>

<text x="500" y="188" text-anchor="middle" font-size="10">5.00%</text>

<line x1="245" y1="150" x2="245" y2="150" stroke="none" />
<circle cx="245" cy="145" r="4" fill="#c0392b" />
<text x="245" y="130" text-anchor="middle" font-size="10" fill="#c0392b">f₁,₁ = 5.04%</text>
<circle cx="415" cy="115" r="4" fill="#c0392b" />
<text x="415" y="100" text-anchor="middle" font-size="10" fill="#c0392b">f₂,₁ = 5.99%</text>
<path d="M 245 145 L 415 115" fill="none" stroke="#c0392b" stroke-width="2" stroke-dasharray="5,3" />
<text x="600" y="118" font-size="11" fill="#c0392b">Implied forward rates</text>

<text x="160" y="290" text-anchor="middle" font-size="10">Year 1</text>

<text x="330" y="290" text-anchor="middle" font-size="10">Year 2</text>

<text x="500" y="290" text-anchor="middle" font-size="10">Year 3</text>

</svg>

### Interpreting Forward Rates: What They Do (and Do Not) Represent

**[Unverified — a matter of ongoing theoretical debate]** A central and historically contested question in fixed income theory is whether forward rates represent unbiased *predictions* of future spot rates, or whether they primarily reflect a **term/liquidity premium** unrelated to genuine rate expectations. Major term structure theories offer different answers:

| Theory | Interpretation of Forward Rates |
| --- | --- |
| Pure Expectations Theory | Forward rates are unbiased predictors of future spot rates; the curve's shape reflects only market expectations of future rates |
| Liquidity Preference Theory | Forward rates overstate expected future spot rates by an embedded liquidity/term premium, since investors demand compensation for holding longer-maturity instruments |
| Market Segmentation Theory | Forward rates reflect supply/demand within distinct maturity "habitats," with little to no direct relationship to genuine future rate expectations |
| Preferred Habitat Theory | A hybrid — investors have preferred maturity ranges but will shift outside them if sufficiently compensated, meaning forward rates embed a habitat-driven premium that varies by maturity segment |

[Inference] No single theory is universally accepted as fully descriptive of observed real-world term structure behavior; most practitioners treat forward rates as a blend of expectations and risk/liquidity premium, with the exact decomposition being empirically difficult to isolate.

### Practical Uses of Forward Rates

- **Forward Rate Agreements (FRAs) and interest rate swaps:** Forward rates derived from the spot curve are the theoretical no-arbitrage foundation for pricing these derivatives; deviations from implied forward rates in traded FRA markets can signal relative value opportunities or reflect risk premia not captured in a simple spot-curve bootstrap.
- **"Riding the yield curve" strategies:** [Inference] A common fixed income trading strategy involves purchasing a longer-maturity bond than an investor's actual holding period horizon, betting that if realized future spot rates come in *below* what the current forward curve implies, the bond can be sold later at a price above what a no-change assumption would suggest — profiting from the difference between implied forward rates and (hoped-for) actual future rates. This strategy's profitability depends entirely on the actual path of future rates versus the forward-implied path, which is inherently uncertain.
- **Testing curve consistency:** Forward rates provide a check on whether a set of quoted spot rates (or the coupon bonds used to bootstrap them) are internally consistent and arbitrage-free.

### Spot Curve Shape and Its Effect on Forward Rates — General Pattern

| Spot Curve Shape | General Forward Rate Pattern |
| --- | --- |
| Upward-sloping (normal) | Forward rates lie *above* corresponding spot rates |
| Downward-sloping (inverted) | Forward rates lie *below* corresponding spot rates |
| Flat | Forward rates approximately equal spot rates |

This pattern follows mechanically from the no-arbitrage formula: for the longer-horizon spot rate to be a "blend" that incorporates a higher (or lower) forward-implied segment, that later segment's implied rate must pull the average up (or down) relative to the shorter spot rate.

### Key Points

- A spot rate applies to a cash flow starting today and maturing at a given future date; a forward rate applies to a future period that has not yet begun.
- Forward rates are not directly observed but are mathematically implied by the current spot curve under a no-arbitrage condition.
- The no-arbitrage relationship $(1+z_{a+b})^{a+b} = (1+z_a)^a \times (1+f_{a,b})^b$ is the foundational equation linking the two.
- An upward-sloping spot curve implies forward rates above corresponding spot rates; an inverted curve implies the reverse.
- Whether forward rates represent unbiased expectations of future spot rates or primarily reflect term/liquidity premia remains a debated question across competing term structure theories.

**Related Topics**

- Term Structure Theories: Expectations, Liquidity Preference, Segmentation, Preferred Habitat
- Forward Rate Agreements (FRAs) and Interest Rate Swap Pricing
- Bootstrapping the Zero-Coupon Curve from Coupon Bond Prices
- Riding the Yield Curve: Strategy Mechanics and Risk
- Yield Curve Shape Analysis (Steepening, Flattening, Inversion)
- Key Rate Duration and Curve Risk Decomposition