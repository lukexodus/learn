## Cournot Competition

### Definition

**Cournot Competition**: A model of oligopoly in which firms compete by **simultaneously and independently choosing output quantities**, with each firm assuming its rivals' quantities are fixed when determining its own profit-maximizing output. The market price is then determined by total industry output via the market demand curve. Named after Antoine Augustin Cournot, who introduced the model in 1838.

### Core Assumptions

**Key Points**

- A small number of firms (the model is most commonly presented with two firms — **duopoly** — but generalizes to $n$ firms).
- Firms produce either a homogeneous product or, in generalized versions, differentiated products.
- Firms choose **quantities** simultaneously and independently (not sequentially, and not prices).
- Each firm treats its rivals' output choices as *given* (fixed) when optimizing its own output — this is the model's defining behavioral assumption, often called a **Cournot conjecture**.
- The market price is determined by the inverse demand function applied to total output: $P = P(Q_1 + Q_2 + \dots + Q_n)$.
- Firms have (commonly assumed) knowledge of the market demand curve and their own cost structure.

### Basic Duopoly Setup

Consider two firms, Firm 1 and Firm 2, producing a homogeneous good with market inverse demand:

$$P = a - b(Q_1 + Q_2)$$

where $Q_1, Q_2$ are the output quantities of Firm 1 and Firm 2, respectively, and $a, b > 0$ are demand parameters. Assume constant marginal cost $c$ for both firms (no fixed costs for simplicity).

**Firm 1's profit:**

$$\pi_1 = P \cdot Q_1 - c \cdot Q_1 = [a - b(Q_1 + Q_2)]Q_1 - cQ_1$$

### Deriving the Reaction (Best-Response) Function

Firm 1 maximizes $\pi_1$ with respect to $Q_1$, treating $Q_2$ as fixed:

$$\frac{\partial \pi_1}{\partial Q_1} = a - 2bQ_1 - bQ_2 - c = 0$$

Solving for $Q_1$:

$$Q_1^* = \frac{a - c - bQ_2}{2b} = \frac{a-c}{2b} - \frac{1}{2}Q_2$$

This is Firm 1's **reaction function** (or best-response function): it specifies Firm 1's profit-maximizing output as a function of Firm 2's output. By symmetry, Firm 2's reaction function is:

$$Q_2^* = \frac{a-c}{2b} - \frac{1}{2}Q_1$$

**Key Points**

- Reaction functions in the standard linear Cournot model slope downward: if a rival produces more, the firm's own best response is to produce less. This reflects **strategic substitutes** behavior — an increase in one firm's output "crowds out" some optimal output from the other, because a higher total quantity depresses market price.

### Cournot-Nash Equilibrium

The **Cournot equilibrium** is the pair $(Q_1^*, Q_2^*)$ where both reaction functions are simultaneously satisfied — i.e., each firm's output is a best response to the other's, and neither firm has an incentive to unilaterally deviate. This is a specific application of **Nash equilibrium** to a quantity-setting game.

Solving the two reaction functions simultaneously (by symmetry, $Q_1^* = Q_2^*$):

$$Q_1^* = \frac{a-c}{2b} - \frac{1}{2}\left(\frac{a-c}{2b} - \frac{1}{2}Q_1^*\right)$$



$$Q_1^* = \frac{a-c}{3b} = Q_2^*$$

**Cournot Reaction Functions and Equilibrium (svg_diagram)**

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 550 500" font-family="sans-serif">
<text x="275" y="24" text-anchor="middle" font-size="16" font-weight="bold">Cournot Reaction Functions and Equilibrium (svg_diagram)</text>
<line x1="70" y1="440" x2="500" y2="440" stroke="black" stroke-width="1.5" />
<line x1="70" y1="440" x2="70" y2="60" stroke="black" stroke-width="1.5" />
<text x="510" y="445" font-size="12">Q1</text>
<text x="40" y="55" font-size="12">Q2</text>

<line x1="70" y1="120" x2="440" y2="440" stroke="#dc2626" stroke-width="2.5" />
<text x="330" y="380" font-size="12" fill="#dc2626">Firm 1's Reaction: R1(Q2)</text>

<line x1="130" y1="440" x2="450" y2="110" stroke="#1d4ed8" stroke-width="2.5" />
<text x="330" y="150" font-size="12" fill="#1d4ed8">Firm 2's Reaction: R2(Q1)</text>

<circle cx="290" cy="280" r="6" fill="black" />
<text x="300" y="270" font-size="12" font-weight="bold">Cournot Equilibrium (Q1*, Q2*)</text>
<line x1="290" y1="280" x2="290" y2="440" stroke="#999" stroke-dasharray="4,4" />
<line x1="290" y1="280" x2="70" y2="280" stroke="#999" stroke-dasharray="4,4" />
<text x="280" y="455" font-size="10">Q1*</text>
<text x="40" y="285" font-size="10">Q2*</text>
</svg>

**Equilibrium Total Output and Price**:

$$Q^*_{total} = Q_1^* + Q_2^* = \frac{2(a-c)}{3b}$$



$$P^* = a - b \cdot Q^*_{total} = a - \frac{2(a-c)}{3} = \frac{a + 2c}{3}$$

### Generalizing to $n$ Firms

For $n$ symmetric firms with identical constant marginal cost $c$, the Cournot-Nash equilibrium yields each firm producing:

$$Q_i^* = \frac{a-c}{b(n+1)}$$



$$Q^*_{total} = \frac{n(a-c)}{b(n+1)}$$



$$P^* = a - b \cdot Q^*_{total} = \frac{a + nc}{n+1}$$

**Key Points**

- As $n \to \infty$, $P^* \to c$ — the Cournot equilibrium price converges toward the perfectly competitive outcome (price equals marginal cost) as the number of firms grows large.
- As $n = 1$, the formula collapses to the standard monopoly outcome.
- This demonstrates that the Cournot model spans a continuum between monopoly ($n=1$) and perfect competition ($n \to \infty$), with oligopoly outcomes ($n$ small, finite) lying between these two benchmarks.

### Comparing Cournot Outcomes Across Market Structures

| Structure | Price | Total Quantity | Markup over MC |
| --- | --- | --- | --- |
| Monopoly ($n=1$) | Highest | Lowest | Largest |
| Cournot duopoly ($n=2$) | $\dfrac{a+2c}{3}$ | $\dfrac{2(a-c)}{3b}$ | Moderate |
| Cournot oligopoly (general $n$) | $\dfrac{a+nc}{n+1}$ | $\dfrac{n(a-c)}{b(n+1)}$ | Decreasing in $n$ |
| Perfect competition ($n \to \infty$) | $= c$ (lowest) | Highest | Zero |

**Example**

Suppose market demand is $P = 100 - Q$ and both firms have marginal cost $c = 10$ (so $a=100$, $b=1$).

- **Duopoly**: $Q_1^* = Q_2^* = \frac{100-10}{3} = 30$ each, so $Q_{total} = 60$, and $P^* = \frac{100 + 20}{3} = 40$.
- **Monopoly** (for comparison, using the standard $MR=MC$ condition with this same demand): $Q_m = 45$, $P_m = 55$.
- **Perfect competition benchmark**: $P = MC = 10$, $Q = 90$.

This confirms the ordering: $P_{monopoly} (55) > P_{Cournot} (40) > P_{perfect\ competition} (10)$, and correspondingly $Q_{monopoly} (45) < Q_{Cournot} (60) < Q_{perfect\ competition} (90)$.

### Comparison with the Bertrand Model

**Key Points**

- Cournot firms compete on **quantity**; Bertrand firms compete on **price**.
- With homogeneous goods and constant marginal cost, the Bertrand model famously predicts price collapses to marginal cost ($P = MC$) even with just two firms (the "Bertrand paradox"), whereas Cournot predicts prices above marginal cost even with many firms, converging to the competitive price only as $n \to \infty$.
- [Inference] This stark difference in predicted outcomes, despite both models describing "oligopoly," highlights that the Cournot vs. Bertrand choice of strategic variable (quantity vs. price) is not a minor modeling detail — it fundamentally changes predicted market outcomes, so selecting the appropriate model for a given real-world industry depends on which variable (capacity/output or price) firms actually commit to first and most rigidly, which is an empirical judgment about the industry's institutional features (e.g., industries with significant capacity constraints and production lead times are often argued to fit Cournot better than Bertrand).

### Strengths and Limitations of the Cournot Model

**Key Points**

*Strengths*:

- Provides a tractable, closed-form model of oligopoly that nests monopoly and perfect competition as limiting cases.
- Offers testable comparative statics: equilibrium price and quantity respond predictably to changes in the number of firms, cost structure, and demand parameters.
- Historically foundational to the development of Nash equilibrium concepts in game theory (Cournot's 1838 model is often cited as a precursor to Nash's later general formalization).

*Limitations*:

- The core behavioral assumption — that a firm treats rivals' output as fixed even after having observed how the model plays out — is sometimes criticized as behaviorally naive, since in repeated or dynamic contexts, firms may recognize and react to how rivals actually adjust output rather than treating it as truly fixed each period. [Inference] This critique concerns the model's realism, not its internal logical consistency; as a one-shot simultaneous-move game, the Cournot-Nash equilibrium is a fully consistent solution concept.
- The model assumes firms choose quantities directly, but in many real markets firms more directly set prices and let quantity be determined by demand at that price — the appropriateness of the quantity-setting assumption depends on the specific industry.
- Extensions incorporating differentiated products, asymmetric costs, capacity constraints, and repeated interaction (supporting potential tacit collusion) substantially expand the basic model's applicability but add complexity beyond the basic closed-form solution shown here.

### Common Pitfalls

- Confusing the Cournot reaction function (a firm's *output* as a function of the rival's *output*) with a general reaction to price changes — Cournot is specifically a quantity-setting model.
- Assuming Cournot equilibrium replicates the perfectly competitive outcome for any finite number of firms — it only converges to that outcome as $n$ approaches infinity; with any finite number of firms, price remains above marginal cost.
- Treating "Cournot" and "Bertrand" as interchangeable descriptions of "oligopoly" — they rest on different strategic variables and can produce dramatically different equilibrium price predictions for the same underlying market.
- Forgetting that the standard closed-form solutions shown here assume linear demand and constant (and identical) marginal costs across firms — asymmetric costs or nonlinear demand require re-deriving the reaction functions and equilibrium from the firms' first-order conditions.

**Related Topics**

- Bertrand Competition and the Bertrand Paradox
- Stackelberg Leadership Model
- Nash Equilibrium and Game Theory
- Characteristics of Oligopoly
- Reaction Functions and Best-Response Analysis
- Product Differentiation in Oligopoly Models
- Collusion and Cartel Stability