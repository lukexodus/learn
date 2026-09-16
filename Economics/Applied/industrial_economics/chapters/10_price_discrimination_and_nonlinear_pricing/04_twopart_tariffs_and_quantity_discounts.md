## Two-Part Tariffs and Quantity Discounts

### Conceptual Foundations

Two-part tariffs and quantity discounts are forms of nonlinear pricing in which the total payment a buyer makes is not simply proportional to the quantity purchased. Unlike linear (uniform) pricing, where total expenditure $T(q) = pq$, nonlinear pricing schedules allow the firm to extract more consumer surplus by tying price to the quantity or intensity of consumption.

A **two-part tariff** decomposes payment into two components:

$$T(q) = A + pq$$

where $A$ is a fixed fee paid regardless of quantity consumed, and $p$ is a per-unit (marginal) price. The buyer pays $A$ for the right to purchase at all, then $p$ per unit consumed.

A **quantity discount** (or block pricing schedule) is a broader class of nonlinear pricing in which the average price per unit falls as quantity purchased rises — the marginal price itself may decline across successive blocks of output, rather than being constant as in the two-part tariff.

Both are used by a monopolist (or oligopolist with market power) to increase profit relative to uniform linear pricing, by capturing part of the consumer surplus that linear pricing leaves on the table. They are classic instruments in the **second-degree price discrimination** toolkit — the firm cannot directly observe buyer type, so it uses the pricing schedule itself to sort and extract surplus.

---

### Two-Part Tariffs: The Basic (Single-Consumer-Type) Model

**Setup**

Consider a monopolist facing a single consumer (or many identical consumers) with inverse demand $p(q)$ and marginal cost $c$. The firm sets:

- A fixed fee $A$ (entry fee, membership fee, subscription charge)
- A per-unit price $p$ (usage fee)

**Optimal Two-Part Tariff with Homogeneous Consumers**

If all consumers are identical, the profit-maximizing two-part tariff is:

1. Set $p = c$ (marginal price equals marginal cost)
2. Set $A$ equal to the entire consumer surplus at that price: $A = CS(p=c)$

$$A^* = \int_0^{q(c)} [p(q) - c]\, dq$$

This is the classic **Oi (1971)** result (Walter Oi's "Disneyland dilemma" paper). Setting $p = c$ maximizes total surplus (efficient quantity is purchased), and the fixed fee then transfers the entire surplus to the firm. This achieves **first-best efficiency** with **full surplus extraction** — the firm captures 100% of the total surplus as profit, identical to perfect (first-degree) price discrimination, despite using only two instruments.

**Why This Works**

With homogeneous consumers, the firm faces no information problem: everyone has the same demand curve, so there is no adverse selection risk in setting $A$ too high. The firm simply prices usage at marginal cost (maximizing the total pie) and then charges an entry fee equal to the buyer's willingness to pay for entry (taking the entire pie).

**Graphical Intuition (svg_diagram)**

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 420">
<text x="320" y="24" font-size="16" font-weight="bold" text-anchor="middle">Optimal Two-Part Tariff, Single Consumer Type (svg_diagram)</text>
<line x1="70" y1="360" x2="600" y2="360" stroke="black" stroke-width="2" />
<line x1="70" y1="360" x2="70" y2="40" stroke="black" stroke-width="2" />
<text x="605" y="365" font-size="13">q</text>
<text x="55" y="40" font-size="13">p</text>
<line x1="70" y1="80" x2="520" y2="360" stroke="#1f77b4" stroke-width="2" />
<text x="500" y="345" font-size="12" fill="#1f77b4">Demand p(q)</text>
<line x1="70" y1="260" x2="600" y2="260" stroke="#d62728" stroke-width="2" stroke-dasharray="4,3" />
<text x="530" y="255" font-size="12" fill="#d62728">p = c (marginal cost)</text>
<line x1="374" y1="260" x2="374" y2="360" stroke="gray" stroke-dasharray="3,3" />
<text x="365" y="378" font-size="12">q* (efficient quantity)</text>
<polygon points="70,80 374,260 70,260" fill="#2ca02c" fill-opacity="0.35" />
<text x="140" y="200" font-size="13" fill="#1a6b1a">Consumer surplus at p=c</text>
<text x="140" y="218" font-size="12" fill="#1a6b1a">= Fixed fee A* (fully extracted)</text>
</svg>

**Two-Part Tariffs with Heterogeneous Consumers**

When consumers differ in demand intensity (e.g., high-demand type H and low-demand type L), the firm faces a genuine screening problem. Setting $A$ equal to the surplus of the low-demand consumer at $p = c$ under-extracts from high-demand consumers; setting $A$ equal to the high-demand consumer's surplus excludes low-demand consumers entirely.

Two strategic options emerge:

**Option 1 — Serve Only High-Demand Consumers**

Set $p = c$, $A = CS_H(c)$. Exclude low-demand consumers (their surplus at this $A$ would be negative). Profitable only if the high-demand segment is large/valuable enough relative to the excluded low-demand segment.

**Option 2 — Serve Both Types (Screening Tariff)**

Set $A$ equal to the *low-demand* consumer's surplus at the chosen $p$, and raise $p$ above marginal cost ($p > c$) to increase the effective surplus gap that can be extracted from high-demand consumers without violating their participation constraint. This trades off:

- **Efficiency loss**: raising $p$ above $c$ distorts quantity choice downward (deadweight loss on the margin)
- **Extraction gain**: a higher $p$ increases the *difference* in consumer surplus between high and low types (since $\partial CS/\partial p$ is more negative for higher-demand types), which can be captured via a larger effective payment from H-types (indirectly, since $A$ itself is capped by the L-type's participation constraint, but H-types now pay more in total via usage)

Formally, this is a special, restricted case of the broader nonlinear pricing / mechanism design problem (see **Related Topics**). The firm's problem is:

$$\max_{A, p} \; \lambda_L (A) + \lambda_H (A + (p-c) q_H(p))$$

subject to:

- **Participation (IR) constraint** for L-type: $CS_L(p) \geq A$
- **Incentive compatibility** implicitly handled since both types face the same $(A, p)$ menu (a pure two-part tariff, unlike a full nonlinear tariff, does not offer a menu of tariffs — this is its key limitation)

[Inference] In many textbook treatments, the profit-maximizing two-part tariff with two consumer types typically sets $A$ at (or near) the low type's full consumer surplus and $p$ strictly between $c$ and the monopoly price, with the exact interior solution depending on the relative population shares and demand elasticities of each type — the precise formula requires specifying functional forms for demand.

---

### Quantity Discounts and Block Pricing

**Definition**

A quantity discount schedule charges a *declining marginal (or average) price* as the quantity purchased increases. Formally, a **block tariff** partitions consumption into blocks $[0, q_1), [q_1, q_2), \dots$ with per-unit prices $p_1 > p_2 > p_3 > \dots$ applied to each successive block ("declining block pricing").

**Relationship to Two-Part Tariffs**

A two-part tariff is a special case of a two-block declining tariff where the first "block" is a single fixed payment (infinitely high marginal price interpretation at $q=0$, then constant $p$ thereafter) rather than a smoothly declining schedule. More generally, quantity discounts are the continuous/multi-block generalization of the two-part tariff — as the number of blocks increases toward infinity, the block tariff converges to a fully nonlinear (continuous) price schedule $T(q)$, i.e., **general nonlinear pricing** or the **Mussa–Rosen (1978)** / **Maskin–Riley (1984)** screening framework.

**Why Quantity Discounts Arise: The Screening Rationale**

With a continuum (or multiple discrete types) of consumers differing in a taste/type parameter $\theta$ (higher $\theta$ = higher marginal valuation), the firm designs a menu of (quantity, total payment) bundles $\{(q(\theta), T(\theta))\}$ to screen types via self-selection. The classic results (Mussa-Rosen; Maskin-Riley) show:

1. **"No distortion at the top"**: the highest type receives the efficient (surplus-maximizing) quantity, where marginal price equals marginal cost
2. **Downward distortion for all other types**: all types below the highest receive *less than* the efficient quantity — marginal price exceeds marginal cost for them, and the marginal price declines with $\theta$ (since higher-$\theta$ consumers get closer to the efficient, higher quantity, they face progressively lower per-unit implicit prices)
3. **Informational rents**: all types except the lowest receive positive surplus (rent) above their participation constraint, needed to keep them from mimicking lower types
4. **Lowest type gets zero surplus** (binding IR constraint) and typically the most severely distorted (lowest) quantity — in extreme cases, may be excluded ("bunching at zero")

This produces exactly the observed empirical pattern of **quantity discounts**: the *average* price per unit declines as $q(\theta)$ rises with $\theta$, because higher-quantity buyers face a schedule that is closer to marginal cost at the margin.

**Formal Sketch (Continuous Type, One-Dimensional Screening)**

Let $\theta \in [\theta_L, \theta_H]$ with density $f(\theta)$, gross utility $u(q,\theta)$ increasing and concave in $q$, increasing in $\theta$, with $u_{q\theta} > 0$ (single-crossing / Spence-Mirrlees condition). The firm's mechanism design problem (via the revelation principle, restricting to direct mechanisms) is:

$$\max_{q(\theta), T(\theta)} \int_{\theta_L}^{\theta_H} [T(\theta) - c\, q(\theta)]\, f(\theta)\, d\theta$$

subject to:

- **IC**: $\theta \in \arg\max_{\hat\theta} \; u(q(\hat\theta), \theta) - T(\hat\theta)$
- **IR**: $u(q(\theta), \theta) - T(\theta) \geq 0$

Using the envelope theorem and standard techniques, the solution characterizes $q(\theta)$ via a pointwise virtual-surplus maximization:

$$u_q(q(\theta), \theta) = c + \frac{1 - F(\theta)}{f(\theta)} \cdot \frac{\partial}{\partial \theta}\left(\frac{u_\theta(q(\theta),\theta)}{1}\right)^{-1}\!\!\!\text{(informational rent term)}$$

[Inference] The exact algebraic form of the distortion term depends on the specific utility and distribution assumptions; the general qualitative results (no distortion at top, downward distortion elsewhere, monotonic quantity discount) are the standard, widely reproduced results from Mussa and Rosen (1978) and Maskin and Riley (1984).

---

### Worked Numerical Example: Two-Part Tariff, Two Types

**Setup**

- Two consumer types: High (H) and Low (L), equal proportions ($\lambda_H = \lambda_L = 0.5$)
- Linear demand: $q_H(p) = 20 - p$, $q_L(p) = 10 - p$
- Marginal cost: $c = 2$

**Step 1 — Efficient (first-best) benchmark**

At $p = c = 2$:

- $q_H = 18$, $q_L = 8$
- $CS_H(2) = \frac{1}{2}(18)(18) = 162$
- $CS_L(2) = \frac{1}{2}(8)(8) = 32$

**Step 2 — Option A: Serve only H-type**

$A = CS_H(2) = 162$, $p = 2$. Profit per H consumer $= 162$. Total profit (only half the market buys) $= 0.5 \times 162 = 81$.

**Step 3 — Option B: Serve both types, screening tariff**

Try $p = 6$ (above cost):

- $q_H(6) = 14$, $q_L(6) = 4$
- $CS_L(6) = \frac{1}{2}(4)(4) = 8$; set $A = 8$
- $CS_H(6) = \frac{1}{2}(14)(14) = 98$; H-type still participates since $98 > 8 \geq 0$

Profit per L consumer: $A + (p-c)q_L = 8 + (6-2)(4) = 8 + 16 = 24$

Profit per H consumer: $A + (p-c)q_H = 8 + (6-2)(14) = 8 + 56 = 64$

Total profit $= 0.5(24) + 0.5(64) = 12 + 32 = 44$

**Step 4 — Compare**

Serving only H-types (Option A, profit = 81) dominates serving both at $p=6$ (Option B, profit = 44) in this example. [Inference] The optimal choice between excluding low-demand consumers versus serving both segments is sensitive to the relative population weights, demand slopes/intercepts, and the chosen $p$ in the screening tariff — a full optimization over $p$ (not just $p=6$) would be required to identify the true best two-part tariff serving both types before concluding exclusion dominates in general; this example illustrates the trade-off mechanism, not a universal ranking.

---

### Comparison: Two-Part Tariff vs. Pure Quantity Discount vs. Linear Pricing

| Feature | Linear Pricing | Two-Part Tariff | Full Nonlinear (Quantity Discount) Schedule |
| --- | --- | --- | --- |
| Instruments | Single price $p$ | Fixed fee $A$ + single $p$ | Continuum of (price, quantity) bundles |
| Surplus extraction | Lowest | Higher (especially homogeneous consumers) | Highest, among second-degree PD instruments |
| Efficiency (homogeneous consumers) | Inefficient (markup above $c$) | Efficient ($p=c$) | Efficient |
| Efficiency (heterogeneous, both served) | Inefficient uniformly | Distorted for excluded or higher-$p$ segment | "No distortion at top," distorted elsewhere |
| Implementation complexity | Trivial | Simple (two numbers) | Complex; requires full type distribution knowledge |
| Common real-world form | Per-unit pricing | Membership + usage fee | Tiered/declining block tariffs |

---

### Real-World Applications

- **Utilities (electricity, water, natural gas)**: fixed monthly connection/service charge plus per-unit consumption charge; often combined with **declining block rates** for large industrial users, or **increasing block rates** for residential conservation policy (the reverse — used for demand management/equity rather than pure profit extraction)
- **Telecommunications**: subscription/line-rental fee plus per-minute or per-GB usage charge; "unlimited" plans represent the limiting case where the marginal price effectively becomes zero within a cap
- **Amusement parks and clubs (the original "Disneyland dilemma")**: entry fee (A) plus per-ride or per-use charge (p); many parks have since shifted to pure fixed-fee ("all-you-can-ride") pricing, effectively setting $p \to 0$ for the marginal ride, which is optimal when marginal cost of an additional ride is near zero and crowding/congestion externalities are limited
- **Wholesale and B2B purchasing**: bulk/volume discounts, common in raw materials, industrial inputs, and distribution contracts — directly reflects the screening logic (large buyers, often more price-elastic or lower-value-per-unit, self-select into higher-quantity blocks with lower marginal prices)
- **Software and SaaS licensing**: base subscription tier plus usage-based overage charges (API calls, storage, compute)
- **Warehouse clubs (Costco, Sam's Club)**: annual membership fee ($A$) plus near-marginal-cost pricing on goods ($p \approx c$), closely approximating the Oi (1971) homogeneous-consumer optimum

---

### Welfare and Antitrust Considerations

- Two-part tariffs with $p = c$ (homogeneous consumers) are **allocatively efficient** — total surplus is maximized — but distributionally regressive from the consumer's standpoint, since the firm captures the entire surplus. Total welfare is unchanged relative to perfect competition; only the *distribution* between firm and consumer shifts.
- When consumers are heterogeneous and some are excluded (Option A style outcomes), there is a genuine **efficiency loss**: total welfare falls short of the first-best because some consumers who would have purchased under marginal-cost pricing are priced out entirely.
- Quantity discounts that produce **exclusionary effects** — e.g., discounts calibrated so that only a dominant firm's largest, most valuable customers can meet a rebate threshold, effectively foreclosing rivals — raise antitrust concerns distinct from ordinary second-degree price discrimination. This is analytically related to but distinct from predatory pricing and loyalty rebate case law. [Unverified] Specific case outcomes and legal standards vary substantially by jurisdiction and are not treated here in detail; consult competition law sources for jurisdiction-specific tests (e.g., EU "as-efficient-competitor" tests for loyalty rebates).
- [Inference] In markets with **resale/arbitrage** possibility, two-part tariffs and quantity discounts face similar constraints to other forms of price discrimination — consumers facing a high fixed fee might contract to jointly purchase and resell, undermining the schedule's ability to extract per-type surplus, unless resale is costly or contractually prohibited.

---

### Mermaid Diagram: Decision Logic for Choosing a Tariff Structure

```mermaid
flowchart TD
    A[Firm has market power over buyers] --> B{Are consumers homogeneous?}
    B -- Yes --> C[Set p = marginal cost c]
    C --> D[Set fixed fee A = full consumer surplus at p=c]
    D --> E[Result: efficient quantity, full surplus extraction]
    B -- No, heterogeneous types --> F{Can firm observe buyer type directly?}
    F -- Yes --> G[Use first-degree/perfect price discrimination: personalized T per type]
    F -- No, must screen --> H{Choose instrument}
    H --> I[Simple two-part tariff: single A, single p]
    H --> J[Full nonlinear tariff / quantity discount menu]
    I --> K{Serve all types or exclude low types?}
    K -- Exclude low types --> L[Set p=c, A = CS of served high type]
    K -- Serve all types --> M[Raise p above c, set A = CS of lowest served type]
    J --> N[Design menu q(theta), T(theta) via IC and IR constraints]
    N --> O[No distortion at top type; downward distortion below; declining marginal price = quantity discount]
```

---

### Key Points

- Two-part tariffs combine a fixed fee and a per-unit price; with homogeneous consumers, setting price at marginal cost and the fee at total consumer surplus achieves full surplus extraction with no efficiency loss.
- With heterogeneous consumers, a firm restricted to a single two-part tariff faces a trade-off between excluding low-demand types (efficient pricing for served types, zero revenue from excluded types) and serving all types (requires raising price above cost, distorting the low type's consumption downward).
- Quantity discounts (block/declining-price schedules) generalize the two-part tariff into a richer menu, allowing the firm to screen a continuum of types via self-selection, governed by incentive compatibility and participation constraints.
- The Mussa-Rosen/Maskin-Riley results — no distortion at the top, downward distortion elsewhere, informational rents for all but the lowest type — explain why observed real-world quantity discount schedules have declining marginal prices as a function of the buyer's revealed demand intensity.
- These tools sit within the broader second-degree price discrimination category: the firm cannot observe type directly and must rely on the pricing schedule itself to induce self-selection.

---

**Related Topics**

- Mussa-Rosen and Maskin-Riley nonlinear pricing / screening models (full derivation)
- Bundling and mixed bundling as alternative second-degree price discrimination tools
- Versioning and product-line design as a screening mechanism
- Third-degree price discrimination (group pricing) versus second-degree (self-selection) methods
- Peak-load pricing and time-of-use tariffs as a related nonlinear pricing application
- Loyalty rebates, all-units discounts, and antitrust treatment of exclusionary quantity discounts
- Multi-product nonlinear pricing and tariff design under multidimensional consumer heterogeneity
- Resale and arbitrage constraints on nonlinear pricing schemes
- Two-part tariffs under oligopoly / imperfect competition (rather than monopoly)
- Empirical estimation of nonlinear tariffs from utility/telecom consumption data