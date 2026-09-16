## Shutdown Decision and Shutdown Point

### Definition

The shutdown decision is the short-run choice a perfectly competitive firm faces between producing its profit-maximizing quantity (where $P = MC$) or producing zero output entirely, when the market price is too low to cover average total cost. The **shutdown point** is the specific price and quantity combination — the minimum point on the average variable cost (AVC) curve — below which the firm is better off producing nothing at all.

This decision is distinct from the long-run **exit decision**, which concerns whether a firm should permanently leave the industry.

### Why the Decision Exists: Fixed vs. Variable Costs in the Short Run

In the short run, total cost splits into two components:

$$TC(q) = TFC + TVC(q)$$

$TFC$ (total fixed cost) must be paid **regardless of output level**, including at $q = 0$ — it is unavoidable in the short run. $TVC(q)$ is avoidable: producing zero output means incurring zero variable cost.

This asymmetry is the entire basis of the shutdown rule: because $TFC$ is unavoidable and effectively sunk over the short-run horizon, it should play no role in the produce-or-not decision (see the sunk cost principle). The only relevant comparison is whether revenue covers the *avoidable* costs.

### Deriving the Shutdown Rule

The firm's profit at its optimal output $q^*$ (found via $P = MC$) is:

$$\pi(q^*) = TR(q^*) - TFC - TVC(q^*)$$

Compare this to the loss from shutting down entirely ($q=0$, so $TR = 0$ and $TVC = 0$):

$$\pi(0) = -TFC$$

The firm should **continue operating** at $q^*$ rather than shut down if:

$$\pi(q^*) > \pi(0)$$



$$TR(q^*) - TFC - TVC(q^*) > -TFC$$



$$TR(q^*) > TVC(q^*)$$



$$P^* \cdot q^* > TVC(q^*)$$

Dividing both sides by $q^*$:

$$P^* > \frac{TVC(q^*)}{q^*} = AVC(q^*)$$

This yields the formal **shutdown rule**:

$$\boxed{\text{Continue producing at } q^* \text{ if } P \geq AVC(q^*); \quad \text{shut down } (q=0) \text{ if } P < AVC(q^*)}$$

### The Shutdown Point Defined

The **shutdown point** is the specific point on the marginal cost curve corresponding to the **minimum of the AVC curve** — i.e., where $MC = AVC$ at its lowest value:

$$\text{Shutdown point: } (q_{sd}, P_{sd}) \text{ where } P_{sd} = \min\big(AVC(q)\big) \text{ and } MC(q_{sd}) = AVC(q_{sd})$$

This point is mathematically significant because $MC$ always intersects $AVC$ (and $ATC$) exactly at their respective minimums — a standard property of the relationship between marginal and average curves: when marginal cost is below average cost, average cost is falling; when marginal cost is above average cost, average cost is rising; therefore they must be equal precisely at the average curve's minimum.

### Three Zones of Short-Run Behavior

| Price Range | Behavior | Rationale |
| --- | --- | --- |
| $P > \min(ATC)$ | Produce at $P = MC$; earn positive economic profit | Revenue exceeds all costs |
| $\min(AVC) \leq P \leq \min(ATC)$ | Produce at $P = MC$; incur a loss but continue | Revenue covers all variable costs and part of fixed costs — smaller loss than shutting down |
| $P < \min(AVC)$ | Shut down; produce $q = 0$ | Revenue would not even cover variable costs; producing adds to the loss beyond $-TFC$ |

The upward-sloping segment of $MC$ **above** the shutdown point (i.e., above minimum $AVC$) constitutes the firm's short-run supply curve; below that point, quantity supplied is zero at every price.

### Diagram: Shutdown Point and Firm Supply Curve (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 600 400">
<text x="300" y="20" font-size="15" font-weight="bold" text-anchor="middle" fill="#1a1a1a">Shutdown Point: MC = min(AVC) (svg_diagram)</text>
<line x1="70" y1="350" x2="70" y2="50" stroke="#333" stroke-width="1.5" />
<line x1="70" y1="350" x2="560" y2="350" stroke="#333" stroke-width="1.5" />
<text x="45" y="60" font-size="12" fill="#333">$</text>
<text x="565" y="355" font-size="12" fill="#333">q</text>

<path d="M 110 300 Q 180 340 240 280 Q 320 190 460 90" stroke="#dc2626" stroke-width="2" fill="none" />
<text x="465" y="85" font-size="11" fill="#dc2626">MC</text>

<path d="M 110 330 Q 230 220 330 210 Q 420 218 470 250" stroke="#7c3aed" stroke-width="2" fill="none" />
<text x="475" y="250" font-size="11" fill="#7c3aed">ATC</text>

<path d="M 110 340 Q 220 260 280 255 Q 380 262 460 290" stroke="#0891b2" stroke-width="2" fill="none" />
<text x="465" y="294" font-size="11" fill="#0891b2">AVC</text>

<circle cx="280" cy="255" r="5" fill="#000" />
<text x="230" y="245" font-size="11" fill="#000" font-weight="bold">Shutdown point</text>
<line x1="70" y1="255" x2="280" y2="255" stroke="#666" stroke-dasharray="4,3" />
<text x="40" y="259" font-size="11" fill="#333">P_sd</text>
<line x1="280" y1="255" x2="280" y2="350" stroke="#666" stroke-dasharray="4,3" />
<text x="272" y="365" font-size="11" fill="#333">q_sd</text>

<path d="M 280 255 Q 320 190 460 90" stroke="#16a34a" stroke-width="3.5" fill="none" stroke-dasharray="0" />
<text x="465" y="115" font-size="10" fill="#16a34a">Firm supply</text>
<text x="465" y="128" font-size="10" fill="#16a34a">curve (bold)</text>
</svg>

### Why Continuing to Operate at a Loss Can Be Rational

This is the most conceptually challenging part of the topic. If $AVC(q^*) < P < ATC(q^*)$, the firm loses money either way — but it loses **less** by producing than by shutting down.

**Numerical illustration:**

Suppose $TFC = \$500$. At the profit-maximizing $q^* = 100$, $TVC(100) = \$3{,}000$, and $P^* = \$32$.

- $TR = 32 \times 100 = \$3{,}200$
- $TC = 500 + 3{,}000 = \$3{,}500$
- $\pi(q^*) = 3{,}200 - 3{,}500 = -\$300$

If instead the firm shuts down:

- $\pi(0) = -TFC = -\$500$

Producing yields a loss of $300, versus a loss of $500 from shutting down — a $200 improvement, because revenue exceeds variable cost by exactly that margin ($3{,}200 - 3{,}000 = 200$), which is applied to offset part of the fixed cost. The firm continues operating despite the loss.

**Contrast**, if instead $P^* = \$28$ (below $AVC = TVC/q = 3{,}000/100 = \$30$):

- $TR = 28 \times 100 = \$2{,}800 < TVC = \$3{,}000$

Here producing generates a loss even larger than $-TFC$ alone, so the firm should shut down and limit its loss strictly to $-\$500$.

### Shutdown vs. Exit: A Critical Distinction

| Feature | Shutdown Decision | Exit Decision |
| --- | --- | --- |
| Time horizon | Short run | Long run |
| Fixed costs | Sunk (cannot be avoided) | Avoidable (lease can end, capital sold) |
| Relevant cost benchmark | $AVC$ | $ATC$ (since all costs are variable long run) |
| Rule | Produce if $P \geq AVC$; else shut down | Stay in industry if $P \geq ATC$; else exit |
| Nature | Temporary — firm retains its plant and may resume production | Permanent — firm leaves the market entirely |

A firm can shut down temporarily (e.g., during an off-season) while still fully intending to resume operations once price recovers, since its fixed costs and capital remain in place. Exit, by contrast, means liquidating fixed assets because even $\min(ATC)$ cannot be covered even in the long run.

### Common Misconceptions

- **"A firm facing a loss should always shut down."** False — the correct comparison is against $AVC$, not $ATC$; a firm can rationally operate at a loss as long as $P \geq AVC$.
- **"Fixed costs should be included in the shutdown comparison to see the 'true' cost of production."** Incorrect — fixed costs are identical (and unavoidable) whether the firm produces or not in the short run, so per the sunk cost principle they are irrelevant to the shutdown/produce comparison.
- **"Shutdown and exit are the same thing."** They differ in time horizon and in which costs are avoidable; shutdown is reversible and short-run, exit is a permanent long-run decision.
- **"The shutdown point is where profit becomes zero."** The zero-economic-profit point occurs at $\min(ATC)$ (the break-even point), not at $\min(AVC)$. The shutdown point specifically marks where the firm becomes indifferent between producing and not producing — not where profit is zero.

### Key Points

- Fixed costs are sunk in the short run and therefore irrelevant to the produce-or-shutdown decision.
- The shutdown rule: produce if $P \geq AVC(q^*)$; shut down if $P < AVC(q^*)$.
- The shutdown point is located at $\min(AVC)$, where $MC = AVC$.
- The firm's short-run supply curve is the portion of $MC$ lying above the shutdown point; below it, quantity supplied is zero.
- Shutdown (temporary, short run) is distinct from exit (permanent, long run), which compares price to $ATC$ instead of $AVC$.

**Related Topics**

- Sunk costs and their irrelevance to decisions
- Deriving the short-run firm and market supply curves
- Short-run profit maximization ($P = MC$ rule)
- Long-run equilibrium and the exit decision
- Break-even point and zero economic profit
- Relationship between marginal cost and average cost curves
- Producer surplus and its measurement below the supply curve