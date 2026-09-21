## Reverse Convertibles and Barrier Reverse Convertibles

### Overview

A reverse convertible note (RCN) is a yield-enhancement structured product that pays an above-market fixed coupon in exchange for the investor bearing downside equity risk in the underlying asset. Economically, it combines a fixed-income bond component with a short put position on the underlying — the investor is implicitly selling downside protection to the issuer in exchange for the enhanced coupon. A barrier reverse convertible (BRC) modifies this by adding a barrier condition that must be breached before the short-put economics activate, softening the loss profile relative to a plain (non-barrier) reverse convertible.

### Core Mechanics — Plain Reverse Convertible

The payoff at maturity is unconditional exposure to the underlying's decline, structured as:

$$\text{Maturity Payoff} = \begin{cases} \text{Par} & \text{if } S_T \geq S_0 \\ \text{Par} \times \frac{S_T}{S_0} & \text{if } S_T < S_0 \end{cases}$$

Where $S_0$ is the initial reference level (strike) and $S_T$ is the underlying level at maturity. Regardless of the outcome, the investor receives the fixed coupon throughout the note's life — the coupon is paid independent of the maturity payoff outcome, which is a key distinguishing feature versus contingent-coupon autocallables.

**Key Points**

- A plain RCN has **no barrier** — downside participation begins immediately below strike, not after a barrier breach
- This makes plain RCNs economically equivalent to: (bond paying enhanced coupon) + (investor short one at-the-money put on the underlying)
- The enhanced coupon is compensation for the premium the investor "receives" for selling this put, packaged into the note structure rather than paid as a separate premium

### Core Mechanics — Barrier Reverse Convertible

A BRC adds a barrier level $B < S_0$, converting the embedded short put into a **short down-and-in put**:

$$\text{Maturity Payoff} = \begin{cases} \text{Par} & \text{if } S_T \geq S_0 \text{ OR barrier never breached} \\ \text{Par} \times \frac{S_T}{S_0} & \text{if barrier breached AND } S_T < S_0 \end{cases}$$

The critical distinction: if the barrier is **never breached** during the observation period, the investor receives par at maturity **even if** $S_T < S_0$ (as long as $S_T \geq S_0$ is not required in some variants — see barrier style note below). In the most common BRC structure, once the barrier has not been breached, principal is protected regardless of terminal underlying level; if the barrier **has** been breached, the payoff reverts to the plain RCN formula (1:1 downside participation based on final level vs. strike).

[Inference] Exact payoff conventions at maturity when the barrier is breached vary by issuer documentation — some structures pay based on final level vs. strike once the down-and-in put is activated, while others reference performance vs. the barrier level itself; the term sheet's payoff formula must be checked precisely rather than assumed from the general "barrier reverse convertible" label.

### Barrier Style: American vs. European

This distinction is critical to BRC valuation:

- **American (continuous) barrier**: Monitored throughout the note's life — any intraday/daily close breach at any point activates the down-and-in put, even if the underlying recovers by maturity
- **European (terminal) barrier**: Observed only at maturity — the down-and-in put activates only if the underlying closes below the barrier on the final valuation date, regardless of the path taken

An American barrier is significantly more likely to be breached than an equivalent European barrier at the same level, all else equal, because it captures the running minimum of the underlying's path rather than just the terminal value. This directly affects the embedded option value and, consequently, the coupon the issuer can offer.

### Worked Example

A 1-year BRC on a single stock:

| Term | Value |
| --- | --- |
| Initial Level (Strike) | $100 |
| Barrier | $70 (70% of initial) |
| Barrier Style | American (continuous) |
| Coupon | 9.00% p.a., paid quarterly, unconditional |
| Denomination | $1,000 |

**Scenario A** — Stock never trades below $70, closes at $95 at maturity → investor receives $1,000 (par) + all coupons paid (9% total over the year)

**Scenario B** — Stock trades down to $65 intraday (barrier breached) mid-year, recovers to $95 by maturity → down-and-in put is activated; investor receives $1,000 \times \frac{95}{100} = \$950$ + all coupons paid over the year (net outcome may still be positive or negative depending on coupon vs. capital loss)

**Scenario C** — Stock trades down to $65 and stays at $60 at maturity → down-and-in put activated; investor receives $1,000 \times \frac{60}{100} = \$600$ + coupons paid

### Reverse Convertible vs. Autocallable Comparison

| Feature | Plain RCN | Barrier RCN | Autocallable (Phoenix) |
| --- | --- | --- | --- |
| Downside protection | None | Contingent on barrier survival | Contingent on barrier survival |
| Coupon condition | Unconditional | Unconditional | Often contingent on coupon barrier |
| Early redemption | No (fixed term) | No (fixed term) | Yes (autocall feature) |
| Observation dates | Single (maturity) | Single (maturity) or path-dependent barrier | Multiple |
| Embedded option | Short ATM put | Short down-and-in put | Short down-and-in put + autocall/digital |

### Payoff Diagram (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 400">
\<style\>
.axis { stroke: #333; stroke-width: 1.5; }
.line1 { stroke: #d35400; stroke-width: 2.5; fill: none; }
.line2 { stroke: #2980b9; stroke-width: 2.5; fill: none; stroke-dasharray: 6,4; }
.lbl { font-family: sans-serif; font-size: 12px; fill: #333; }
.title { font-family: sans-serif; font-size: 14px; font-weight: bold; fill: #111; }
\</style\>
<text x="20" y="20" class="title">Reverse Convertible Payoff at Maturity (svg_diagram)</text>
<line x1="60" y1="340" x2="640" y2="340" class="axis" />
<line x1="60" y1="340" x2="60" y2="40" class="axis" />
<text x="330" y="375" class="lbl">Underlying Level at Maturity (% of Initial)</text>
<text x="20" y="200" class="lbl" transform="rotate(-90 20,200)">Payoff (% of Par)</text>
<line x1="60" y1="80" x2="380" y2="80" class="line1" />
<line x1="380" y1="80" x2="640" y2="320" class="line1" />
<text x="420" y="70" class="lbl" fill="#d35400">Plain RCN (no barrier)</text>
<line x1="60" y1="80" x2="270" y2="80" class="line2" />
<line x1="270" y1="80" x2="270" y2="340" class="line2" stroke-dasharray="2,2" stroke="#999" />
<line x1="270" y1="80" x2="640" y2="80" class="line2" />
<text x="420" y="100" class="lbl" fill="#2980b9">Barrier RCN (barrier not breached)</text>

<text x="255" y="360" class="lbl">70%</text>

<text x="375" y="360" class="lbl">100%</text>

<text x="55" y="85" class="lbl">Par</text>

</svg>

### Risk and Investor Suitability Considerations

**Key Points**

- The investor is exposed to **full downside** below the strike (RCN) or below the strike once barrier-activated (BRC), while upside is **capped at the fixed coupon** — there is no participation in underlying appreciation beyond the coupon
- This makes RCNs/BRCs a fundamentally different risk profile from participation notes: they underperform in strong rallies (capped return) and are exposed to sharp declines (uncapped downside once activated)
- The product is best understood as a yield-enhancement strategy for a neutral-to-mildly-bullish view, not a directional bullish bet
- Issuer credit risk applies throughout — coupon and principal repayment both depend on issuer solvency, as with all unsecured structured notes

### Practical Implications for Analysis

- Always confirm barrier style (American vs. European) before comparing coupons across BRC offerings — an American-barrier note with a lower headline coupon may carry less breach risk than a European-barrier note with a higher coupon at the same barrier level, or vice versa depending on structuring
- For worst-of basket BRCs (common in practice), apply the same worst-of/correlation analysis used for autocallables, since the barrier condition typically requires all constituents to remain above the barrier
- Model expected coupon income against expected capital-at-risk using historical volatility and barrier proximity, rather than evaluating the headline coupon in isolation
- Distinguish RCN/BRC issuer economics (short put premium capture) from autocallable issuer economics (short put + autocall/digital optionality), since the embedded option package differs

### Related Topics

- Barrier style (American vs. European) and its pricing impact
- Autocallable notes and trigger mechanics
- Short put replication and option-implied structured note pricing
- Worst-of basket correlation risk
- Term sheet anatomy and key terms
- Volatility skew and its effect on reverse convertible coupon levels