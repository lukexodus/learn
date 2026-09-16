## Short-run Supply Curve of the Firm

### Definition

The short-run supply curve of a perfectly competitive firm shows the quantity of output the firm is willing to produce at each possible market price, holding at least one input (typically capital/plant size) fixed. It is derived directly from the firm's short-run marginal cost curve.

### Underlying Profit-Maximization Rule

A perfectly competitive firm is a price taker, so price ($P$) equals marginal revenue ($MR$) and average revenue ($AR$):

$$P = MR = AR$$

The firm maximizes profit by producing the quantity where:

$$MR = MC$$

Since $MR = P$ for a competitive firm, the profit-maximizing condition becomes:

$$P = MC$$

This means the firm's marginal cost curve tells us how much the firm will supply at each price — which is precisely the definition of a supply curve.

### Why the Supply Curve Is the MC Curve Above AVC

Not the entire $MC$ curve qualifies as the supply curve. Two additional conditions must hold:

**1. Second-Order Condition (Rising MC)**

For $P = MC$ to represent a *maximum* (not a minimum) profit point, marginal cost must be rising at that quantity. The $MC$ curve is U-shaped due to the law of diminishing marginal returns, so it has both a downward-sloping and an upward-sloping segment. Only the upward-sloping (rising) portion satisfies the second-order condition for profit maximization.

**2. Shutdown Condition (Price Must Cover Average Variable Cost)**

In the short run, fixed costs are sunk and must be paid regardless of the output level, even if output is zero. The firm's decision to produce or shut down depends only on variable costs.

- If $P \geq AVC_{min}$: the firm continues to produce, even if it is making a loss, because it is covering all variable costs and at least part of fixed costs.
- If $P < AVC_{min}$: the firm shuts down (produces zero output), because operating would mean losing money on every unit produced *plus* still bearing fixed costs — shutting down and only losing the fixed cost is preferable.
- If $P = AVC_{min}$: the firm is indifferent between producing at that quantity and shutting down; this point is called the **shutdown point**.

**Conclusion:** The firm's short-run supply curve is the segment of the marginal cost curve that lies *at or above* the minimum point of the average variable cost curve. Below $AVC_{min}$, the supply curve coincides with the vertical (price) axis at zero output.

$$\text{Supply Curve} = MC \text{ curve, for all } P \geq AVC_{min}$$

### Relationship to AVC and ATC

- **Shutdown Point**: where $MC$ intersects $AVC$ at its minimum. Below this price, quantity supplied is zero.
- **Break-even Point**: where $MC$ intersects $ATC$ (average total cost) at its minimum. Between the shutdown point and the break-even point, the firm produces but incurs an economic loss (though it is minimizing that loss by covering all variable costs plus part of fixed costs). Above the break-even point, the firm earns positive economic profit.

### Diagram: Short-run Supply Curve Derivation

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 720 480" font-family="Helvetica, Arial, sans-serif">
<text x="360" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Short-run Supply Curve of the Firm (svg_diagram)</text>

<line x1="80" y1="420" x2="680" y2="420" stroke="#333" stroke-width="2" />
<line x1="80" y1="420" x2="80" y2="50" stroke="#333" stroke-width="2" />
<text x="690" y="425" font-size="13" fill="#333">Q</text>
<text x="65" y="45" font-size="13" fill="#333">P, C</text>


<path d="M 140 380 C 220 260, 300 210, 360 195 C 420 185, 500 190, 620 100" fill="none" stroke="`#c0392b`" stroke-width="2.5" />

<text x="625" y="95" font-size="13" fill="`#c0392b`" font-weight="bold">MC</text>



<path d="M 160 340 C 240 260, 320 235, 400 240 C 460 245, 540 270, 600 310" fill="none" stroke="`#2980b9`" stroke-width="2.5" />

<text x="605" y="315" font-size="13" fill="`#2980b9`" font-weight="bold">AVC</text>



<path d="M 190 400 C 260 300, 340 265, 420 268 C 480 270, 560 300, 610 350" fill="none" stroke="`#27ae60`" stroke-width="2.5" />

<text x="615" y="355" font-size="13" fill="`#27ae60`" font-weight="bold">ATC</text>


<circle cx="335" cy="237" r="5" fill="#2c3e50" />
<line x1="335" y1="237" x2="335" y2="420" stroke="#888" stroke-dasharray="4,3" />
<line x1="80" y1="237" x2="335" y2="237" stroke="#888" stroke-dasharray="4,3" />
<text x="230" y="230" font-size="12" fill="#2c3e50">Shutdown point</text>
<text x="60" y="241" font-size="11" fill="#2c3e50">P₁</text>

<circle cx="435" cy="267" r="5" fill="#2c3e50" />
<line x1="435" y1="267" x2="435" y2="420" stroke="#888" stroke-dasharray="4,3" />
<line x1="80" y1="267" x2="435" y2="267" stroke="#888" stroke-dasharray="4,3" />
<text x="440" y="262" font-size="12" fill="#2c3e50">Break-even point</text>
<text x="60" y="271" font-size="11" fill="#2c3e50">P₂</text>


<path d="M 335 237 C 420 185, 500 190, 620 100" fill="none" stroke="`#8e44ad`" stroke-width="5" stroke-linecap="round" opacity="0.55" />

<text x="440" y="150" font-size="13" fill="`#8e44ad`" font-weight="bold">Supply curve = MC above AVC min</text>


<line x1="80" y1="237" x2="80" y2="420" stroke="#8e44ad" stroke-width="5" opacity="0.55" stroke-linecap="round" />


<text x="335" y="440" font-size="12" fill="#333" text-anchor="middle">Q₁</text>

<text x="435" y="440" font-size="12" fill="#333" text-anchor="middle">Q₂</text>

</svg>

**How to read this diagram:** The bold purple segment traces the firm's actual supply curve. Below the shutdown point ($P_1$), quantity supplied collapses to zero (the vertical purple segment on the price axis). From the shutdown point upward, the supply curve is identical to the $MC$ curve. Between $P_1$ and $P_2$, the firm produces but operates at a loss (price is below $ATC$ but above $AVC$). Above $P_2$, the firm earns positive economic profit.

### Numerical Example

Suppose a firm's short-run total cost function is:

$$TC(Q) = 100 + 4Q^2$$

where 100 is total fixed cost ($TFC$) and $4Q^2$ is total variable cost ($TVC$).

**Step 1 — Derive MC:**

$$MC = \frac{d(TC)}{dQ} = 8Q$$

**Step 2 — Derive AVC:**

$$AVC = \frac{TVC}{Q} = \frac{4Q^2}{Q} = 4Q$$

**Step 3 — Find the shutdown price:**

$AVC$ is minimized as $Q \to 0$ in this simplified linear case (in more realistic cubic-cost specifications, $AVC$ has an interior minimum). Here, $AVC = 4Q$ is monotonically increasing from zero, so technically $AVC_{min} = 0$ at $Q = 0$, meaning the firm will supply positive output at any positive price. This illustrates that the *shape* of the shutdown condition depends on the specific cost function used — most textbook treatments use a cubic $TVC$ (e.g., $TVC = Q^3 - aQ^2 + bQ$) specifically so that $AVC$ has a well-defined interior minimum.

**Step 4 — Using a market price to find quantity supplied:**

If $P = \$40$, set $P = MC$:

$$40 = 8Q \implies Q = 5$$

The firm supplies 5 units at a price of $40. Check the shutdown condition: $AVC$ at $Q = 5$ is $4(5) = \$20$, and since $P = \$40 > AVC = \$20$, the firm indeed produces (it is covering variable costs and contributing toward fixed costs).

### Individual Supply Curve as a Function

The firm's short-run supply function can be written piecewise as:

$$Q_S(P) = \begin{cases} 
MC^{-1}(P) & \text{if } P \geq AVC_{min} \\
0 & \text{if } P < AVC_{min}
\end{cases}$$

where $MC^{-1}(P)$ is the inverse of the marginal cost function, solved for $Q$.

### From Firm Supply to Market Supply

The short-run market supply curve is the **horizontal summation** of all individual firms' short-run supply curves in the industry (assuming a fixed number of firms in the short run):

$$Q_S^{Market}(P) = \sum_{i=1}^{n} Q_{S,i}(P)$$

At each price, add up the quantities each firm is willing to supply. This is why the market supply curve tends to be flatter (more elastic) than any single firm's supply curve — more firms contribute more total quantity at each price point.

### Shifts vs. Movements Along the Supply Curve

- **Movement along the curve**: caused only by a change in market price (a change in quantity supplied).
- **Shift of the curve**: caused by changes in the underlying cost structure, such as:
  - Input price changes (wages, raw materials, rent)
  - Technological improvements (shifts $MC$ and $AVC$ downward)
  - Changes in the price of related outputs (in multi-product firms)
  - Taxes or subsidies per unit of output
  - Expectations about future prices (in some short-run models with storable output)

A decrease in variable input costs shifts both $MC$ and $AVC$ downward, shifting the supply curve to the right (more output supplied at every price) and typically lowering the shutdown price.

### Key Points

- The short-run supply curve of a competitive firm is the portion of its $MC$ curve at or above minimum $AVC$.
- Profit maximization requires $P = MC$ on the rising portion of $MC$.
- The shutdown point ($P = AVC_{min}$) determines the lower bound below which the firm supplies zero output.
- Fixed costs are irrelevant to the shutdown decision because they are sunk in the short run.
- Market supply is the horizontal sum of individual firm supply curves at a given number of firms.

### Common Misconceptions

- **[Unverified — student-level heuristic, not a formal claim]** A common error is assuming firms shut down whenever they are making an accounting loss. In fact, a firm continues operating as long as $P \geq AVC$, even while incurring an economic loss, because shutting down would forfeit the contribution toward fixed costs.
- Confusing the shutdown point ($MC = AVC$) with the break-even point ($MC = ATC$) — these are distinct thresholds with different economic implications (zero output vs. zero economic profit).
- Treating the entire $MC$ curve as the supply curve, ignoring both the second-order (rising segment) and shutdown conditions.

### Related Topics

- Long-run supply curve of the firm and the industry
- Producer surplus and its relationship to the supply curve
- Shutdown decision vs. exit decision (short run vs. long run)
- Perfectly competitive market equilibrium (short run vs. long run)
- Elasticity of supply and its determinants
- Cost curves: derivation of $MC$, $AVC$, $ATC$, $AFC$ from total cost functions
- Zero economic profit condition in long-run competitive equilibrium