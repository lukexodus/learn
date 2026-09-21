## Athena Phoenix and Twin Win Structures

### Overview

"Athena" and "Phoenix" are widely used marketing/family names (primarily in European and Asian retail structured product markets) for autocallable notes with contingent coupon and memory features. "Twin Win" is a distinct structure that allows the investor to profit from underlying moves in **either direction** — up or down — up to a barrier, converting what would normally be a one-directional downside into a source of positive return. All three are commonly built on single stocks, indices, or worst-of baskets and share the general autocallable/barrier product family, but each has a distinguishing payoff mechanic worth isolating.

### Athena Structures

"Athena" is a naming convention (most associated with French/European structuring desks, e.g., BNP Paribas legacy naming and subsequently adopted more broadly) for a standard autocallable note with:

- **Annual (typically) observation dates**, often fewer/less frequent than some other Phoenix variants
- **Flat or step-down autocall trigger**, generally starting at or near 100% of initial level
- **Coupon paid only upon autocall or at maturity if barrier conditions are met** — critically, in the classic Athena structure, coupon is often **not** paid on interim non-autocall observation dates the way a Phoenix contingent coupon is; the coupon frequently accrues and is paid as a lump sum upon triggering

$$\text{Athena Payoff at Autocall (Year } t\text{)} = \text{Par} \times (1 + \text{Coupon} \times t)$$

**Key Points**

- The core economic distinction between "Athena" and generic "autocallable" is largely naming convention and regional/desk-specific structuring habits rather than a universally standardized mechanical difference
- [Unverified] Because "Athena" is not a formally standardized term across all issuers (unlike EUSIPA/SVSP classification codes), the exact payoff mechanics under an "Athena" label should always be verified against the specific term sheet rather than assumed from the name alone

### Phoenix Structures

"Phoenix" refers to an autocallable note with a **contingent coupon paid on each observation date** (not just at autocall/maturity), typically featuring a **memory mechanism**:

$$\text{Coupon}_t = \begin{cases} c \times (1 + m_t) & \text{if } S_t \geq B_{\text{coupon}} \\ 0, \text{ but } m_{t+1} = m_t + 1 & \text{if } S_t < B_{\text{coupon}} \end{cases}$$

Where $m_t$ tracks the number of consecutive missed coupon periods, and a subsequent triggering observation pays the current coupon plus all accrued/memorized missed coupons.

**Key Points**

- Phoenix structures generally offer more frequent (monthly/quarterly) coupon observation than Athena's typically annual cadence, making the coupon barrier a live, recurring test rather than an event tied only to autocall
- The memory feature is the defining Phoenix characteristic — it substantially increases the expected coupon stream relative to a no-memory contingent coupon note, and is priced accordingly into the embedded option cost
- Phoenix and Athena are sometimes used interchangeably in casual market commentary, but a rigorous comparison requires checking: (a) coupon payment frequency, (b) presence/absence of memory feature, (c) whether coupon barrier and autocall barrier are set at the same or different levels

### Comparative Table: Athena vs. Phoenix vs. Standard Autocallable

| Feature | Athena (typical) | Phoenix (typical) | Generic Autocallable |
| --- | --- | --- | --- |
| Coupon frequency | Often annual, paid at trigger/maturity | Monthly/quarterly, independent of autocall | Varies by term sheet |
| Memory feature | Sometimes present | Commonly present | Varies |
| Coupon vs. autocall barrier | Often same level | Often different (coupon barrier lower) | Varies |
| Naming standardization | Desk/region-specific | Widely used across issuers | N/A (descriptive only) |

[Inference] These characterizations reflect common market usage patterns observed across European and Asian retail structuring desks; individual issuers may deviate from this typical mapping, and the terms are ultimately marketing labels layered on top of the mechanically defining term sheet provisions.

### Twin Win Structures

A Twin Win note is designed to generate positive returns whether the underlying rises **or** falls, up to a barrier, by combining:

1. **Upside participation** — standard positive exposure if the underlying rises above initial level
2. **Downside "flip" participation** — if the underlying falls but stays above a barrier, the decline is converted into a **positive** return via an absolute-value-style payoff
3. **Barrier knock-out** — if the underlying breaches the barrier on the downside, the "flip" feature is lost and the note reverts to standard 1:1 (or worse) downside exposure

$$\text{Twin Win Payoff} = \begin{cases} \text{Par} \times \left(1 + \text{Participation} \times \frac{S_T - S_0}{S_0}\right) & \text{if } S_T \geq S_0 \\ \text{Par} \times \left(1 + \text{Participation} \times \left|\frac{S_T - S_0}{S_0}\right|\right) & \text{if } B \leq S_T < S_0 \\ \text{Par} \times \frac{S_T}{S_0} & \text{if } S_T < B \end{cases}$$

Where $B$ is the downside barrier below which the "twin win" flip feature is knocked out and the note reverts to simple linear downside exposure (or, in some variants, principal is capped at a floor even below the barrier — term sheet specific).

**Example:**

A 2-year Twin Win note with 100% upside participation, 100% downside "flip" participation, and a 70% barrier:

- Underlying up 15% at maturity → investor receives $115\%$ of par (standard upside participation)
- Underlying down 10% at maturity, never breached barrier → investor receives $110\%$ of par (decline converted to gain via absolute-value mechanic)
- Underlying down 35% at maturity, breached 70% barrier intraday → flip feature knocked out; investor receives approximately $65\%$ of par (standard 1:1 downside loss)

### Twin Win Payoff Diagram (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 420">
\<style\>
.axis { stroke: #333; stroke-width: 1.5; }
.line1 { stroke: #16a085; stroke-width: 2.5; fill: none; }
.line2 { stroke: #c0392b; stroke-width: 2; fill: none; stroke-dasharray: 5,4; }
.lbl { font-family: sans-serif; font-size: 12px; fill: #333; }
.title { font-family: sans-serif; font-size: 14px; font-weight: bold; fill: #111; }
\</style\>
<text x="20" y="20" class="title">Twin Win Payoff Structure (svg_diagram)</text>
<line x1="60" y1="360" x2="640" y2="360" class="axis" />
<line x1="350" y1="360" x2="350" y2="40" class="axis" />
<text x="280" y="395" class="lbl">Underlying Return at Maturity</text>
<line x1="350" y1="180" x2="640" y2="60" class="line1" />
<text x="450" y="90" class="lbl" fill="#16a085">Upside participation</text>
<line x1="230" y1="180" x2="350" y2="180" class="line1" />
<text x="150" y="170" class="lbl" fill="#16a085">Flip: decline = gain</text>
<line x1="60" y1="330" x2="230" y2="180" class="line2" />
<text x="65" y="320" class="lbl" fill="#c0392b">Barrier breached: linear loss</text>
<line x1="230" y1="40" x2="230" y2="360" stroke="#999" stroke-dasharray="2,3" />
<text x="200" y="378" class="lbl">Barrier (70%)</text>
<text x="340" y="378" class="lbl">Initial (100%)</text>
</svg>

### Twin Win Risk Considerations

**Key Points**

- Twin Win notes cap the "win from decline" benefit only within the barrier range — a severe decline that breaches the barrier eliminates the flip benefit entirely and can result in substantial principal loss, potentially worse psychologically for investors expecting only upside scenarios
- Upside participation and downside flip participation rates are frequently **not equal** — issuers may set unequal participation rates (e.g., 100% upside, 70% downside flip) depending on volatility skew and funding considerations, so headline "Twin Win" branding does not guarantee symmetric economics
- Because Twin Win embeds a barrier shift option (a combination of a call and a down-and-out put with reversed payoff sign below strike), pricing is sensitive to skew — the relative implied volatility of downside vs. upside strikes — making Twin Win economics particularly dependent on the issuer's skew assumptions

### Practical Implications for Analysis

- When evaluating an "Athena" or "Phoenix" labeled note, immediately check coupon observation frequency and memory feature presence rather than relying on the family name to infer mechanics
- For Twin Win notes, explicitly compare the upside participation rate against the downside flip participation rate — asymmetry here is common and directly affects expected value under different market scenarios
- All three structures (Athena, Phoenix, Twin Win) share barrier-style sensitivity (American vs. European) as a critical valuation input — confirm this before assuming any headline barrier level translates directly into probability of breach
- Recognize that family names are structuring/marketing conventions layered on the same underlying option-pricing toolkit (autocall triggers, contingent coupons, memory features, barrier knock-ins/outs) — the payoff formula, not the product name, is authoritative

### Related Topics

- Autocallable notes and trigger mechanics
- Barrier reverse convertibles
- Volatility skew and its effect on structured note pricing
- Structured product naming conventions
- Worst-of basket correlation risk
- Down-and-out / down-and-in barrier option mechanics