## Elasticity and Total Revenue Relationships

### Overview

The relationship between price elasticity of demand and total revenue is one of the most practically important results in managerial economics, directly informing pricing decisions. Because total revenue ($TR = P \times Q$) depends on both price and the quantity response to that price, the *direction* in which TR moves following a price change depends entirely on the elasticity of demand at that point.

### Total Revenue Defined

$$TR = P \times Q$$

Where $P$ is price per unit and $Q$ is quantity sold at that price. Since $Q$ is itself a function of $P$ (via the demand curve), $TR$ is a function of price alone: $TR(P) = P \times Q(P)$.

### Deriving the Elasticity–Marginal Revenue Relationship

Starting from $TR = P \cdot Q$, differentiate with respect to $Q$ to find marginal revenue:

$$MR = \frac{d(TR)}{dQ} = P + Q\frac{dP}{dQ}$$

Factor out $P$:

$$MR = P\left(1 + \frac{Q}{P}\cdot\frac{dP}{dQ}\right)$$

Since $E_d = \dfrac{dQ}{dP}\cdot\dfrac{P}{Q}$, it follows that $\dfrac{Q}{P}\cdot\dfrac{dP}{dQ} = \dfrac{1}{E_d}$. Substituting:

$$MR = P\left(1 + \frac{1}{E_d}\right)$$

Since $E_d$ is negative for a normal downward-sloping demand curve, this is commonly rewritten using absolute value:

$$MR = P\left(1 - \frac{1}{|E_d|}\right)$$

**Key Points**

- This is one of the most important derived relationships in managerial economics and price theory, linking marginal revenue directly to price and elasticity
- When $|E_d| \to \infty$ (perfectly elastic demand), $MR \to P$ — consistent with the perfectly competitive firm, where price equals marginal revenue
- When $|E_d| = 1$, $MR = 0$
- When $|E_d| < 1$ (inelastic), $MR < 0$

### The Three Elasticity Regimes and Their Revenue Implications

| Elasticity Regime | Value of $\|E_d\|$ | Sign of $MR$ | Effect of Price ↑ | Effect of Price ↓ |
| --- | --- | --- | --- | --- |
| Elastic | $\|E_d\| > 1$ | $MR > 0$ | TR decreases | TR increases |
| Unit elastic | $\|E_d\| = 1$ | $MR = 0$ | TR unchanged (at maximum) | TR unchanged (at maximum) |
| Inelastic | $\|E_d\| < 1$ | $MR < 0$ | TR increases | TR decreases |

**Key Points**

- **Elastic demand**: quantity response outweighs the price change proportionally, so price and TR move in **opposite** directions
- **Inelastic demand**: quantity response is proportionally smaller than the price change, so price and TR move in the **same** direction
- **Unit elastic demand**: the point of **maximum total revenue** — the proportional increase in price is exactly offset by the proportional decrease in quantity

### Graphical Relationship: Demand, TR, and MR

<svg viewBox="0 0 620 460" xmlns="http://www.w3.org/2000/svg">
<text x="310" y="22" font-size="16" font-weight="bold" text-anchor="middle" fill="#1a1a1a">Demand, Total Revenue, and Marginal Revenue (svg_diagram)</text>
<line x1="70" y1="240" x2="70" y2="50" stroke="#333" stroke-width="2"/>
<line x1="70" y1="240" x2="420" y2="240" stroke="#333" stroke-width="2"/>
<text x="425" y="245" font-size="11" fill="#333">Quantity</text>
<text x="40" y="45" font-size="11" fill="#333">Price</text>
<text x="80" y="65" font-size="11" fill="#111">Demand (D)</text>
<line x1="90" y1="70" x2="400" y2="220" stroke="#111" stroke-width="2"/>
<line x1="90" y1="70" x2="245" y2="220" stroke="#7c3aed" stroke-width="2" stroke-dasharray="4,3"/>
<text x="250" y="215" font-size="11" fill="#7c3aed">MR</text>
<circle cx="245" cy="145" r="4" fill="#dc2626"/>
<text x="180" y="140" font-size="10" fill="#dc2626">|E|=1 (MR=0)</text>

<text x="100" y="90" font-size="10" fill="`#2563eb`">Elastic (MR>0)</text>

<text x="300" y="205" font-size="10" fill="`#16a34a`">Inelastic (MR<0)</text>

<line x1="70" y1="430" x2="70" y2="270" stroke="#333" stroke-width="2"/>
<line x1="70" y1="430" x2="420" y2="430" stroke="#333" stroke-width="2"/>
<text x="425" y="435" font-size="11" fill="#333">Quantity</text>
<text x="40" y="265" font-size="11" fill="#333">TR</text>
<path d="M 90,420 Q 245,290 400,420" stroke="#ea580c" stroke-width="2" fill="none"/>
<text x="230" y="285" font-size="10" fill="#ea580c">TR maximized where |E|=1</text>
<line x1="245" y1="430" x2="245" y2="300" stroke="#999" stroke-width="1" stroke-dasharray="3,3"/>
</svg>

**Interpretation**: The top panel shows a linear demand curve with its associated marginal revenue curve (which has twice the slope and the same vertical intercept). The bottom panel shows total revenue as a function of quantity — TR rises while $MR>0$ (elastic region), peaks where $MR=0$ (unit elastic), and falls while $MR<0$ (inelastic region).

### Worked Numerical Example

Linear demand: $P = 100 - 2Q$

**Step 1: Total Revenue function**

$$TR = P \times Q = (100 - 2Q)Q = 100Q - 2Q^2$$

**Step 2: Marginal Revenue function**

$$MR = \frac{d(TR)}{dQ} = 100 - 4Q$$

**Step 3: Find quantity where TR is maximized (MR = 0)**

$$100 - 4Q = 0 \Rightarrow Q = 25$$



$$P = 100 - 2(25) = 50$$

**Step 4: Verify unit elasticity at this point**

$$E_d = \frac{dQ}{dP} \times \frac{P}{Q} = \left(-\frac{1}{2}\right) \times \frac{50}{25} = -1$$

**Output**

At $Q = 25$, $P = 50$: $|E_d| = 1$ exactly, confirming TR is at its maximum ($TR = 50 \times 25 = 1250$) precisely where demand is unit elastic.

**Verification at nearby points**

| Q | P | TR | $E_d$ | Elasticity Zone |
| --- | --- | --- | --- | --- |
| 15 | 70 | 1050 | $-70/30 = -2.33$ | Elastic |
| 25 | 50 | 1250 | $-1.00$ | Unit elastic (TR max) |
| 35 | 30 | 1050 | $-30/70 = -0.43$ | Inelastic |

Note TR rises from Q=15 to Q=25 (elastic region, price falling raises TR) and falls from Q=25 to Q=35 (inelastic region, price falling now reduces TR) — confirming the TR-maximizing point sits exactly at unit elasticity.

```mermaid
flowchart TD
    A[Price Change] --> B{Elasticity Regime at Current Price}
    B -->|Elastic: |E|>1| C[Price ↓ → TR ↑<br/>Price ↑ → TR ↓]
    B -->|Unit Elastic: |E|=1| D[TR at Maximum<br/>Small price changes: TR unchanged]
    B -->|Inelastic: |E|<1| E[Price ↑ → TR ↑<br/>Price ↓ → TR ↓]
    C --> F[Managerial Implication:<br/>Cut price to boost revenue]
    E --> G[Managerial Implication:<br/>Raise price to boost revenue]
    D --> H[Managerial Implication:<br/>Revenue-maximizing price point]
```

### Managerial Pricing Implications

**Key Points**

- A profit-maximizing (not merely revenue-maximizing) firm with positive marginal cost will **never** knowingly operate in the inelastic region of demand — since $MR<0$ there, a firm could increase both revenue and reduce output/costs simultaneously by raising price, unambiguously increasing profit
- This yields the **rule of thumb**: rational monopolists and firms with market power always price in the elastic portion of their demand curve
- For a firm considering a price change, elasticity provides the direct decision rule:
  - If demand is **elastic** at the current price → lowering price increases total revenue
  - If demand is **inelastic** at the current price → raising price increases total revenue
  - If demand is **unit elastic** → the firm is at (or near) the revenue-maximizing price point

### Distinguishing Total Revenue Maximization from Profit Maximization

**Key Points**

- The TR-maximizing quantity (where $MR=0$) is generally **not** the same as the profit-maximizing quantity (where $MR=MC$), unless marginal cost happens to be zero
- Profit-maximizing firms with positive marginal costs will produce **less** than the TR-maximizing quantity, since profit maximization requires $MR=MC>0$, which occurs at a point where demand is still elastic (to the left of the TR peak)
- This distinction is critical in managerial economics: pursuing revenue maximization as a proxy for profit maximization can lead to overproduction relative to the profit-optimal output level

### Application Across Market Structures

**Key Points**

- **Perfect competition**: firms face a perfectly elastic (horizontal) demand curve at the market price, so $MR = P$ always; the total revenue-elasticity relationship collapses to a special case since $|E_d| \to \infty$
- **Monopoly and monopolistic competition**: since the firm faces the entire downward-sloping market/segment demand curve, the elasticity-TR relationship is central to output and pricing decisions
- **Price discrimination**: firms exploit differences in elasticity across customer segments — charging higher prices to less elastic (inelastic) segments and lower prices to more elastic segments — directly leveraging this TR relationship to increase overall revenue and profit beyond single-price outcomes

### Common Pitfalls and Clarifications

**Key Points**

- A common student error is to assume price and TR always move in the same direction — this only holds under inelastic demand; under elastic demand, they move in **opposite** directions
- Elasticity is **not constant along a linear demand curve** — a firm cannot assume a single elasticity value applies at all prices; the TR-maximizing point must be found using the specific functional form of demand
- $MR=0$ identifies the revenue-maximizing quantity only when the demand curve is well-behaved (downward sloping, single-peaked TR); this does not generalize automatically to more complex, non-standard demand curves without re-derivation

### Related Topics

- Price Elasticity of Demand and Its Determinants
- Marginal Revenue and Marginal Cost: Profit Maximization Rule
- Monopoly Pricing and the Elasticity-Based Markup Rule (Lerner Index)
- Price Discrimination Strategies (First, Second, Third Degree)
- Cross-Price and Income Elasticity of Demand
- Revenue Management and Dynamic Pricing