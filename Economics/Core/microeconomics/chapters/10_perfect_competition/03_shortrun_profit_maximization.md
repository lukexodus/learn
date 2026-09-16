## Short-Run Profit Maximization

### Definition

Short-run profit maximization is the process by which a perfectly competitive firm chooses the output level that maximizes economic profit, given a fixed market price and a plant size (capital stock) that cannot be altered within the short-run time horizon. "Short run" specifically means at least one input — typically capital — is fixed, while variable inputs (e.g., labor, materials) can be adjusted.

### The Profit Function

Economic profit is the difference between total revenue and total cost, where total cost includes both explicit and implicit (opportunity) costs:

$$\pi(q) = TR(q) - TC(q)$$

For a price-taking firm, $TR(q) = P^* \cdot q$, so:

$$\pi(q) = P^*q - TC(q)$$

### The General Profit-Maximizing Rule: MR = MC

The universal condition for profit maximization across all market structures is found by setting the derivative of the profit function to zero:

$$\frac{d\pi}{dq} = MR(q) - MC(q) = 0 \quad \Rightarrow \quad MR(q^*) = MC(q^*)$$

**Intuition:** As long as the revenue gained from producing one more unit ($MR$) exceeds the cost of producing it ($MC$), profit rises with additional output. Once $MC$ exceeds $MR$, further production reduces profit. The profit-maximizing quantity is where these two marginal quantities are equal.

**Second-order condition** (ensures a maximum, not a minimum):

$$\frac{d^2\pi}{dq^2} = MR'(q^*) - MC'(q^*) < 0$$

For a price-taking firm ($MR' = 0$), this reduces to requiring $MC'(q^*) > 0$ — marginal cost must be rising at the chosen quantity.

### Specialization for the Perfectly Competitive Firm: P = MC

Since a competitive firm is a price taker, $MR = P^*$ for all $q$. Substituting into the general rule:

$$P^* = MC(q^*)$$

This holds **only on the upward-sloping segment of the MC curve** — the downward-sloping segment (where MC is falling) never satisfies the second-order condition for a maximum.

### Diagram: Short-Run Profit Maximization (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 600 380">
<text x="300" y="20" font-size="15" font-weight="bold" text-anchor="middle" fill="#1a1a1a">Short-Run Profit Maximization: P = MC (svg_diagram)</text>
<line x1="70" y1="330" x2="70" y2="50" stroke="#333" stroke-width="1.5" />
<line x1="70" y1="330" x2="560" y2="330" stroke="#333" stroke-width="1.5" />
<text x="45" y="60" font-size="12" fill="#333">$</text>
<text x="565" y="335" font-size="12" fill="#333">q</text>

<path d="M 100 300 Q 200 100 500 70" stroke="#dc2626" stroke-width="2" fill="none" />
<text x="505" y="70" font-size="11" fill="#dc2626">MC</text>

<path d="M 100 260 Q 260 160 500 220" stroke="#7c3aed" stroke-width="2" fill="none" />
<text x="505" y="220" font-size="11" fill="#7c3aed">ATC</text>

<path d="M 100 290 Q 260 210 500 260" stroke="#ea580c" stroke-width="2" fill="none" />
<text x="505" y="260" font-size="11" fill="#ea580c">AVC</text>

<line x1="70" y1="150" x2="540" y2="150" stroke="#16a34a" stroke-width="2" />
<text x="545" y="153" font-size="11" fill="#16a34a">P* = d = MR</text>

<line x1="330" y1="150" x2="330" y2="330" stroke="#666" stroke-dasharray="4,3" />
<text x="322" y="345" font-size="11" fill="#333">q*</text>
<circle cx="330" cy="150" r="4" fill="#000" />

<circle cx="330" cy="185" r="4" fill="#7c3aed" />
<line x1="70" y1="185" x2="330" y2="185" stroke="#7c3aed" stroke-dasharray="3,3" />
<text x="35" y="189" font-size="10" fill="#7c3aed">ATC(q*)</text>

<rect x="70" y="150" width="260" height="35" fill="#16a34a" fill-opacity="0.15" stroke="none" />
<text x="150" y="172" font-size="11" fill="#166534">Profit</text>
</svg>

The shaded rectangle represents total economic profit: the area bounded by $P^*$ above, $ATC(q^*)$ below, and width $q^*$.

$$\pi^* = [P^* - ATC(q^*)] \times q^*$$

### The Three Possible Short-Run Outcomes

Depending on where $P^*$ falls relative to the firm's cost curves, three distinct short-run outcomes are possible:

| Condition | Outcome | Profit Formula |
| --- | --- | --- |
| $P^* > ATC(q^*)$ | Positive economic profit | $\pi = (P^* - ATC) \times q^* > 0$ |
| $P^* = ATC(q^*)$ | Zero economic profit (breakeven) | $\pi = 0$ |
| $AVC(q^*) < P^* < ATC(q^*)$ | Economic loss, but firm continues operating | $\pi = (P^* - ATC) \times q^* < 0$ |
| $P^* < AVC(q^*)$ | Shutdown (produce $q = 0$) | $\pi = -TFC$ |

**Why a firm operates even at a loss when $AVC < P < ATC$:** In the short run, fixed costs are sunk and must be paid regardless of the output decision. As long as price covers average variable cost, each unit produced contributes something toward covering fixed costs, so producing loses less than shutting down entirely (where the firm would still lose the full amount of fixed costs).

$$\text{Loss from producing: } (P^* - ATC(q^*)) \times q^* \quad \text{vs.} \quad \text{Loss from shutting down: } -TFC$$

Producing is preferred whenever the loss from producing is smaller in magnitude than $TFC$, which algebraically reduces to $P^* \geq AVC(q^*)$.

### Worked Example: Three Scenarios

Given cost function $TC(q) = q^2 + 20q + 144$, so:

$$MC(q) = 2q + 20, \quad AVC(q) = q + 20, \quad ATC(q) = q + 20 + \frac{144}{q}$$

Minimum of $AVC$ occurs at $q = 0$ (linear, increasing from 20), so $AVC_{\min} = 20$.

Minimum of $ATC$: set $\frac{d\,ATC}{dq} = 1 - \frac{144}{q^2} = 0 \Rightarrow q = 12$, giving $ATC(12) = 12 + 20 + 12 = 44$.

**Scenario A: $P^* = 60$ (profit case)**

$$60 = 2q + 20 \Rightarrow q^* = 20$$



$$ATC(20) = 20 + 20 + \frac{144}{20} = 47.2$$



$$\pi = (60 - 47.2)(20) = 256 \quad \text{(positive profit)}$$

**Scenario B: $P^* = 44$ (breakeven case)**

$$44 = 2q + 20 \Rightarrow q^* = 12$$



$$ATC(12) = 44 \Rightarrow \pi = (44 - 44)(12) = 0 \quad \text{(zero economic profit)}$$

**Scenario C: $P^* = 30$ (operate-at-a-loss case)**

$$30 = 2q + 20 \Rightarrow q^* = 5$$



$$AVC(5) = 25, \quad ATC(5) = 5 + 20 + 28.8 = 53.8$$

Since $AVC(5) = 25 < 30 < 53.8 = ATC(5)$, the firm continues operating despite a loss:

$$\pi = (30 - 53.8)(5) = -119$$

**Scenario D: $P^* = 18$ (shutdown case)**

Since $18 < AVC_{\min} = 20$ at every quantity, the firm shuts down and produces $q = 0$, incurring a loss equal to total fixed costs only ($TFC = 144$), rather than a larger loss from operating.

### Numerical Approach vs. Calculus Approach

For discrete production tables (common in introductory problem sets without continuous cost functions), the equivalent method compares total revenue and total cost directly at each integer quantity, or compares $MR$ and $MC$ unit-by-unit:

$$\text{Produce the marginal unit if } MR \geq MC \text{ for that unit}$$



$$\text{Stop at the last quantity where } MR \geq MC \text{ still holds}$$

This unit-by-unit comparison is mathematically equivalent to the calculus-based $MR = MC$ condition, converging to it as the unit size shrinks toward continuous output.

### Common Misconceptions

- **"Firms should always shut down if they are making a loss."** False — a firm should shut down only if price falls below *average variable cost*, not merely below average total cost. Operating at a loss above $AVC$ minimizes losses relative to shutting down.
- **"Maximizing revenue is the same as maximizing profit."** These generally differ: revenue continues rising with output as long as $MR > 0$, but profit is maximized specifically where $MR = MC$, which typically occurs at a lower quantity than revenue maximization (since $MC > 0$).
- **"Zero economic profit means the firm is failing."** Zero *economic* profit still includes a normal return covering all opportunity costs, including the opportunity cost of the owner's capital and labor — it is consistent with the firm earning a normal accounting profit.

### Key Points

- The universal profit-maximizing rule is $MR = MC$; for a price-taking firm, this simplifies to $P = MC$.
- The second-order condition restricts the solution to the upward-sloping portion of the $MC$ curve.
- Three short-run outcomes are possible: economic profit, breakeven, or loss-with-continued-operation — determined by comparing $P^*$ to $ATC$ and $AVC$.
- The shutdown rule is governed by $AVC$, not $ATC$, because fixed costs are sunk in the short run.
- Total profit or loss can be read graphically as a rectangle bounded by $P^*$, $ATC(q^*)$, and $q^*$.

**Related Topics**

- The shutdown decision and derivation of the short-run supply curve
- Long-run adjustment: entry, exit, and zero economic profit
- Sunk costs and their irrelevance to decisions
- Deriving marginal cost from total cost and variable cost functions
- Producer surplus and its relationship to profit
- Break-even and shutdown points as specific points on the MC curve
- Comparative statics: effect of a market price change on firm output