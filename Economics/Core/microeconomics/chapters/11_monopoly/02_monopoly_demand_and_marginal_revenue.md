## Monopoly Demand and Marginal Revenue

### Definition

Unlike a perfectly competitive firm, a monopolist is the sole seller of a good with no close substitutes, and therefore faces the entire market demand curve as its own demand curve. Because the monopolist is not a price taker, it must lower price to sell additional units, which causes marginal revenue to fall below price at every unit beyond the first. This wedge between price and marginal revenue is the central technical feature distinguishing monopoly analysis from perfect competition.

### Why the Monopolist Faces the Market Demand Curve

In perfect competition, an individual firm's demand curve is a horizontal line at the market price, since the firm is only one of many sellers and its output decisions have no perceptible effect on market price. A monopolist, being the *only* seller, has no such luxury: the entire downward-sloping market demand curve *is* the monopolist's demand curve.

$$P = D(Q)$$

where $D(Q)$ is the (inverse) market demand function, giving the price at which quantity $Q$ can be sold.

### Total Revenue, Average Revenue, and Marginal Revenue

**Total Revenue (TR):**

$$TR(Q) = P(Q) \times Q$$

**Average Revenue (AR):** revenue per unit sold, which is always equal to price:

$$AR(Q) = \frac{TR(Q)}{Q} = P(Q)$$

This means the demand curve is also the average revenue curve: $D = AR$.

**Marginal Revenue (MR):** the additional revenue from selling one more unit:

$$MR(Q) = \frac{d(TR)}{dQ}$$

### Deriving Why MR Lies Below Demand for a Monopolist

Because the monopolist must lower price on *all* units sold (not just the marginal unit) to sell one additional unit — assuming a single uniform price is charged to all customers — increasing quantity has two opposing effects on revenue:

1. **Output effect**: selling one more unit at the new (lower) price adds revenue.
2. **Price effect**: the price reduction applies to all previously sold units too, subtracting revenue.

$$MR = P + Q\frac{dP}{dQ}$$

Since demand curves slope downward, $\frac{dP}{dQ} < 0$, so the second term is negative. This means:

$$MR < P \quad \text{for all } Q > 0 \text{ (except the very first unit)}$$

This is the single most important distinguishing feature of monopoly (and any firm with market power) versus perfect competition, where $MR = P$ always.

### Linear Demand Example: Deriving MR Algebraically

Suppose market (inverse) demand is linear:

$$P = a - bQ$$

**Step 1 — Total Revenue:**

$$TR = P \times Q = (a - bQ)Q = aQ - bQ^2$$

**Step 2 — Marginal Revenue** (derivative of $TR$ with respect to $Q$):

$$MR = \frac{d(TR)}{dQ} = a - 2bQ$$

**Key algebraic result:** for linear demand, $MR$ has the **same vertical intercept** ($a$) as demand but **twice the slope** ($-2b$ instead of $-b$). This means the $MR$ curve bisects the horizontal distance between the price axis and the demand curve at every price level — a useful graphing shortcut.

### Diagram: Demand and Marginal Revenue for a Linear Demand Curve

<svg viewBox="0 0 700 460" xmlns="http://www.w3.org/2000/svg" font-family="Helvetica, Arial, sans-serif">
<text x="350" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Monopoly Demand and Marginal Revenue (svg_diagram)</text>
<line x1="80" y1="400" x2="650" y2="400" stroke="#333" stroke-width="2"/>
<line x1="80" y1="400" x2="80" y2="60" stroke="#333" stroke-width="2"/>
<text x="660" y="405" font-size="13" fill="#333">Q</text>
<text x="65" y="55" font-size="13" fill="#333">P</text>
<!-- Demand curve D = AR -->
<line x1="120" y1="90" x2="600" y2="380" stroke="#2980b9" stroke-width="2.5"/>
<text x="605" y="380" font-size="12" fill="#2980b9">D = AR</text>
<text x="100" y="85" font-size="11" fill="#2980b9">a</text>
<!-- MR curve: same intercept, twice the slope -->
<line x1="120" y1="90" x2="360" y2="400" stroke="#c0392b" stroke-width="2.5"/>
<text x="365" y="405" font-size="12" fill="#c0392b">MR</text>
<!-- Vertical line showing where MR = 0 (midpoint of demand) -->
<line x1="360" y1="90" x2="360" y2="400" stroke="#888" stroke-dasharray="3,3"/>
<text x="330" y="420" font-size="11" fill="#333">Q at MR = 0 (midpoint of demand)</text>
<!-- Region labels -->

<text x="200" y="200" font-size="11" fill="`#2980b9`" opacity="0.8">Elastic (MR > 0)</text>

<text x="450" y="330" font-size="11" fill="`#c0392b`" opacity="0.8">Inelastic (MR < 0)</text>

</svg>

**How to read this diagram:** The $MR$ curve starts at the same price-axis intercept as demand but falls twice as steeply, crossing the quantity axis exactly at the midpoint of the demand curve's horizontal span. To the left of this midpoint, demand is elastic and $MR > 0$; to the right, demand is inelastic and $MR < 0$.

### The Relationship Between MR, Price, and Price Elasticity of Demand

Marginal revenue can be expressed directly in terms of the price elasticity of demand ($\epsilon_d$, using the convention where $\epsilon_d$ is reported as a negative number, or $|\epsilon_d|$ for its absolute value):

$$MR = P\left(1 + \frac{1}{\epsilon_d}\right) = P\left(1 - \frac{1}{|\epsilon_d|}\right)$$

This relationship reveals several important facts:

- **When demand is elastic** ($|\epsilon_d| > 1$): $MR > 0$. A price decrease increases total revenue, since the percentage increase in quantity demanded exceeds the percentage decrease in price.
- **When demand is unit elastic** ($|\epsilon_d| = 1$): $MR = 0$. Total revenue is at its maximum; a small price change leaves $TR$ unchanged (to a first-order approximation).
- **When demand is inelastic** ($|\epsilon_d| < 1$): $MR < 0$. A price decrease reduces total revenue, since the percentage increase in quantity demanded is smaller than the percentage decrease in price.

**Critical implication:** A profit-maximizing monopolist will **never** choose to produce in the inelastic region of its demand curve, because $MR < 0$ there means the firm could increase revenue *and* reduce total cost (by producing less) simultaneously — an unambiguous improvement in profit. Therefore, a profit-maximizing monopolist always operates where demand is elastic or unit elastic, i.e., $|\epsilon_d| \geq 1$.

### Numerical Example

Suppose market demand facing a monopolist is:

$$P = 100 - 2Q$$

**Step 1 — Total Revenue:**

$$TR = PQ = (100 - 2Q)Q = 100Q - 2Q^2$$

**Step 2 — Marginal Revenue:**

$$MR = \frac{d(TR)}{dQ} = 100 - 4Q$$

**Step 3 — Find quantity where MR = 0** (revenue-maximizing quantity, marking the elastic/inelastic boundary):

$$100 - 4Q = 0 \implies Q = 25$$

**Step 4 — Verify against demand curve midpoint:** the demand curve's quantity intercept (where $P = 0$) is found from $0 = 100 - 2Q \implies Q = 50$. The midpoint of $[0, 50]$ is $Q = 25$, confirming the algebraic shortcut that $MR$ crosses zero at exactly half the demand curve's quantity intercept.

**Step 5 — Calculate MR at a specific quantity, e.g., Q = 10:**

$$MR(10) = 100 - 4(10) = 60$$



$$P(10) = 100 - 2(10) = 80$$

Confirms $MR (60) < P (80)$ at this quantity, as expected for a downward-sloping demand curve.

### Total Revenue, Marginal Revenue, and Elasticity — Combined View

<svg viewBox="0 0 700 480" xmlns="http://www.w3.org/2000/svg" font-family="Helvetica, Arial, sans-serif">
<text x="350" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">TR, MR, and Elasticity Regions (svg_diagram)</text>
<!-- Top panel: TR curve (inverted U) -->
<line x1="80" y1="180" x2="650" y2="180" stroke="#333" stroke-width="1.5"/>
<line x1="80" y1="180" x2="80" y2="60" stroke="#333" stroke-width="1.5"/>
<text x="60" y="55" font-size="12" fill="#333">TR</text>
<path d="M 100 170 C 250 90, 450 90, 600 170" fill="none" stroke="#8e44ad" stroke-width="2.5"/>
<text x="605" y="175" font-size="11" fill="#8e44ad">TR(Q)</text>
<line x1="350" y1="90" x2="350" y2="180" stroke="#888" stroke-dasharray="3,3"/>
<text x="330" y="200" font-size="10" fill="#333">Q at max TR</text>
<!-- Bottom panel: MR crossing zero at same Q -->
<line x1="80" y1="400" x2="650" y2="400" stroke="#333" stroke-width="1.5"/>
<line x1="80" y1="400" x2="80" y2="280" stroke="#333" stroke-width="1.5"/>
<text x="660" y="405" font-size="13" fill="#333">Q</text>
<text x="60" y="275" font-size="12" fill="#333">MR</text>
<line x1="80" y1="340" x2="650" y2="340" stroke="#555" stroke-width="1"/>
<text x="655" y="344" font-size="10" fill="#555">0</text>
<line x1="100" y1="300" x2="600" y2="395" stroke="#c0392b" stroke-width="2.5"/>
<text x="605" y="398" font-size="11" fill="#c0392b">MR(Q)</text>
<line x1="350" y1="280" x2="350" y2="400" stroke="#888" stroke-dasharray="3,3"/>

<text x="140" y="320" font-size="11" fill="`#2980b9`">Elastic region: MR > 0</text>

<text x="420" y="380" font-size="11" fill="`#c0392b`">Inelastic region: MR < 0</text>

</svg>

**How to read this diagram:** The top panel shows total revenue rising, peaking, then falling as $Q$ increases. The bottom panel shows $MR$ — the slope of $TR$ — starting positive, crossing zero exactly where $TR$ peaks, then turning negative. The vertical dashed line aligns the $TR$-maximizing quantity with the $MR = 0$ point, illustrating that $MR$ is literally the derivative (slope) of $TR$.

### Non-linear Demand: General Derivation

For demand curves that are not linear, the same principle applies but requires calculus on the specific functional form. For a general inverse demand function $P = D(Q)$:

$$TR(Q) = D(Q) \cdot Q$$



$$MR(Q) = D(Q) + Q \cdot D'(Q)$$

**Example — constant elasticity demand:** $Q = AP^{-\epsilon}$ (where $\epsilon > 0$ is the constant elasticity), which inverts to $P = (Q/A)^{-1/\epsilon}$. For this functional form, it can be shown that $MR = P(1 - 1/\epsilon)$ holds exactly at every quantity, illustrating that the elasticity-MR relationship above is a general one, not specific to linear demand.

### Marginal Revenue Under First-Degree (Perfect) Price Discrimination — Brief Note

The wedge between $P$ and $MR$ described above assumes the monopolist must charge a **single uniform price** to all buyers. If the monopolist can instead engage in perfect (first-degree) price discrimination — charging each customer their exact maximum willingness to pay for each unit — then the firm does not need to lower price on inframarginal units to sell an additional unit. In that special case:

$$MR = P \quad \text{(under perfect price discrimination)}$$

This is a preview of the price discrimination topic and highlights that the $P > MR$ result specifically stems from the uniform-pricing assumption, not from monopoly power itself.

### Common Misconceptions

- A frequent error is assuming $MR = P$ for a monopolist, mechanically transferring the perfectly competitive firm's condition. This is only true under perfect price discrimination; under standard (uniform-price) monopoly, $MR < P$ for all $Q > 0$.
- Students sometimes think a monopolist would want to operate at maximum total revenue (where $MR = 0$). In fact, profit maximization requires $MR = MC$, and since marginal cost is typically positive, the profit-maximizing quantity is *less* than the revenue-maximizing quantity — the monopolist stops short of maximizing revenue because doing so would require producing units whose marginal cost exceeds their marginal revenue.
- The claim "$MR$ is always below demand" is sometimes overgeneralized to say $MR$ is always positive-but-lower. In fact, $MR$ can become negative in the inelastic region, even though a profit-maximizing firm with positive marginal cost would never actually choose to operate there.

### Related Topics

- Monopoly profit maximization: $MR = MC$ and price/output determination
- Price elasticity of demand and its relationship to total revenue
- Deadweight loss under monopoly
- Price discrimination (first, second, and third degree)
- Sources and barriers to entry
- The markup formula (Lerner Index) and pricing power
- Multi-plant monopoly and marginal cost aggregation