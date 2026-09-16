## Non-Transferable Utility Games


### Definition and Conceptual Overview

Non-transferable utility (NTU) games generalize the transferable utility (TU) framework by removing the assumption that value can be freely redistributed among coalition members via a common numeraire. In an NTU game, each coalition $S$ is associated not with a single number $v(S)$, but with a **set of feasible utility vectors** $V(S) \subseteq \mathbb{R}^S$ — the different combinations of utility levels that the members of $S$ can jointly achieve. This is the natural framework whenever outcomes involve non-fungible goods, individually varying utility functions over shared outcomes, or situations where side payments in a common currency are unavailable, restricted, or simply do not capture the full richness of what players value.

NTU games strictly generalize TU games: every TU game $(N,v)$ can be represented as a special NTU game where $V(S) = \{x \in \mathbb{R}^S : \sum_{i\in S} x_i \leq v(S)\}$ — a half-space defined by a single linear "budget" constraint. The NTU framework is needed precisely when this reduction to a single aggregate number is not possible or not appropriate.

**Key Points**

- An NTU game is defined by $(N, V)$, where $V(S) \subseteq \mathbb{R}^S$ is a set of achievable utility vectors for each coalition $S$, rather than a single real number
- TU games are the special case where $V(S)$ is a half-space defined by one linear budget constraint
- Standard solution concepts (Core, Shapley value) require substantial reformulation to apply to NTU games, since simple additive/averaging operations on numbers no longer make sense across non-comparable utility scales
- NTU games are the appropriate framework for many real bargaining, matching, and exchange-economy problems where interpersonal utility comparisons or transfers are not natural or feasible

### Formal Structure

**Feasible set:** For each coalition $S \subseteq N$, $V(S)$ is typically assumed to be:

- **Closed:** boundary points are included
- **Comprehensive:** if $u \in V(S)$ and $u' \leq u$ (component-wise), then $u' \in V(S)$ — utility can always be freely "thrown away," reflecting free disposal
- **Bounded above:** no coalition can achieve unboundedly large utility for its members

**Feasible outcome for the grand coalition:** An outcome is a utility vector $x \in V(N)$ specifying a feasible utility level for every player.

**Core of an NTU game:** An outcome $x \in V(N)$ is in the **NTU Core** if no coalition $S$ can achieve an alternative feasible vector $y \in V(S)$ that gives every member of $S$ strictly higher utility than $x$ does — i.e., there is no $y \in V(S)$ with $y_i > x_i$ for all $i \in S$. This generalizes the TU Core's blocking condition (no coalition can jointly do better) to the vector-valued NTU setting, replacing "sum of payoffs" comparisons with **Pareto-dominance** comparisons within the coalition.

### Why the Shapley Value Does Not Directly Generalize

The TU Shapley value relies critically on being able to add and average real numbers representing "marginal contributions" across different coalitions and orderings — an operation that presupposes a common, comparable, and transferable scale of value. In NTU games, utility for different players may not be comparable or interpersonally meaningful in the same units, so the straightforward averaging formula breaks down. Several distinct generalizations have been proposed, each making different assumptions to restore a well-defined notion of "value":

- **Shapley NTU value (Shapley, 1969):** Uses a system of weights (one per player) representing a hypothetical common utility scale, and defines the value via a fixed-point condition where the weighted combination of the vector-valued game reduces to a well-defined TU-like value; the weights themselves must be found endogenously as part of the solution.
- **Harsanyi NTU value (Harsanyi, 1963):** An alternative generalization based on a different bargaining-theoretic construction, using generalized Raiffa-Kalai-Smorodinsky-style bargaining solutions applied coalition-by-coalition.

[Unverified] These generalizations do not always coincide with each other on a given NTU game, and the choice between them can depend on which axiomatic properties (efficiency, symmetry, and their NTU analogues) are considered most important for the specific application, an area with less settled consensus than the TU Shapley value's clean uniqueness result.

### Worked Conceptual Example: Bargaining Over Heterogeneous Goods

Consider two players negotiating over how to split a bundle of distinct, non-fungible items (e.g., an apple and a concert ticket) where each player has different, non-comparable utility functions over the items (Player 1 cares much more about the concert ticket; Player 2 cares much more about the apple). Because utility cannot be freely transferred between the players via a common currency (assume no side payments are permitted), the feasible set $V(\{1,2\})$ is the set of achievable *pairs* of utility levels $(u_1, u_2)$ resulting from different possible allocations of the apple and ticket — not a simple linear budget line, but potentially a more complex curved Pareto frontier reflecting the different rates at which each player is willing to trade off the two goods.

This is structurally identical to the classic **Edgeworth box** setting from general equilibrium theory: the set of Pareto-efficient allocations traces out a **contract curve**, and the NTU Core in this two-player exchange setting corresponds precisely to the portion of the contract curve that also satisfies individual rationality for both players (each player does at least as well as their pre-trade endowment) — directly connecting NTU cooperative game theory to standard microeconomic exchange theory.

### Diagram: TU vs. NTU Feasible Sets

```mermaid
graph TD
    A[Coalition S considers cooperating] --> B{Is utility freely transferable via common numeraire?}
    B -->|Yes| C[TU game: V(S) is a half-space, sum of payoffs less than or equal to v(S)]
    B -->|No| D[NTU game: V(S) is a general feasible set, possibly curved Pareto frontier]
    C --> E[Solution concepts: Core, Shapley value, Nucleolus via real-number arithmetic]
    D --> F[Solution concepts require vector comparisons: Pareto dominance, generalized bargaining solutions]
    F --> G[Shapley NTU value, Harsanyi NTU value, generalized Core]
```

### Diagram: NTU Feasible Set and Core Region (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 320">
<text x="320" y="24" font-size="16" text-anchor="middle" font-weight="bold">NTU Feasible Set: Pareto Frontier vs. Linear TU Boundary (svg_diagram)</text>
<line x1="80" y1="280" x2="80" y2="60" stroke="black" stroke-width="1.5" />
<line x1="80" y1="280" x2="560" y2="280" stroke="black" stroke-width="1.5" />
<text x="40" y="70" font-size="12">u2</text>
<text x="570" y="295" font-size="12">u1</text>
<path d="M 100,260 Q 250,240 350,180 Q 450,120 500,80" fill="none" stroke="#059669" stroke-width="2.5" />
<text x="480" y="65" font-size="11" fill="#059669">NTU Pareto frontier (curved)</text>
<line x1="120" y1="250" x2="480" y2="90" stroke="#2563eb" stroke-width="2" stroke-dasharray="6,3" />
<text x="480" y="105" font-size="11" fill="#2563eb">TU linear boundary</text>
<circle cx="200" cy="140" r="4" fill="#dc2626" />
<text x="205" y="135" font-size="10" fill="#dc2626">Disagreement / status quo point</text>

<text x="320" y="310" font-size="11" text-anchor="middle" fill="#555">NTU Core allocations must lie on the curved frontier, Pareto-undominated by any coalition</text>

</svg>

### The NTU Core and Balancedness

An NTU analogue of the Bondareva-Shapley theorem exists: the **Scarf theorem** (Scarf, 1967) provides sufficient conditions for the non-emptiness of the NTU Core, using a generalized notion of **balancedness** applied to the vector-valued feasible sets $V(S)$. Scarf's theorem shows that if the NTU game is balanced (in the generalized sense) and each $V(S)$ is closed, comprehensive, and convex, then the NTU Core is non-empty — extending the TU balancedness result to the substantially more general vector-valued setting.

[Unverified] The convexity requirement on $V(S)$ in Scarf's theorem is a real restriction not automatically satisfied by all economically meaningful NTU games; games with non-convex feasible sets (e.g., arising from indivisibilities or non-convex preferences) may have empty Cores even when a naive balancedness-style condition might suggest otherwise, and establishing non-emptiness in such cases typically requires case-specific analysis.

### Comparison: TU Games vs. NTU Games

| Dimension | TU Games | NTU Games |
| --- | --- | --- |
| Coalition value representation | Single real number $v(S)$ | Set of feasible utility vectors $V(S) \subseteq \mathbb{R}^S$ |
| Interpersonal transfers | Assumed freely possible | Not assumed; may be impossible or restricted |
| Core definition | Sum-of-payoffs comparison | Pareto-dominance comparison |
| Shapley value | Unique, closed-form combinatorial formula | Multiple competing generalizations (Shapley NTU value, Harsanyi NTU value), not always coinciding |
| Existence theorem for Core | Bondareva-Shapley theorem | Scarf's theorem (requires convexity of feasible sets) |
| Canonical application | Cost-sharing, voting power, profit allocation | Exchange economies, matching markets, bargaining over heterogeneous goods |

### Applications

- **General equilibrium and exchange economies:** The NTU Core generalizes the classical **Edgeworth box** and connects cooperative game theory directly to competitive equilibrium theory — the Core of a large exchange economy has been shown (via the **Edgeworth conjecture / Debreu-Scarf theorem**) to shrink toward the set of competitive equilibrium allocations as the number of agents grows large.
- **Matching markets:** Stable matching problems (e.g., the marriage problem, college admissions) are naturally NTU settings, since utility from a match is typically not transferable between the matched parties without further structural assumptions; solution concepts here connect to the Gale-Shapley stable matching framework.
- **International relations and treaty negotiation:** Bargaining over multi-dimensional, non-monetary outcomes (territorial claims, policy commitments, non-fungible concessions) is often modeled using NTU frameworks, since side payments across all dimensions of the negotiation are frequently unavailable or politically infeasible.
- **Household and family bargaining models:** Economic models of intra-household resource allocation often use NTU bargaining frameworks, since utility across household members is not simply transferable via a common budget in the way firm profit-sharing might be.

**Related Topics**

- Transferable Utility Games and Characteristic Functions
- The Core and the Scarf Non-Emptiness Theorem
- The Shapley Value: NTU Generalizations (Shapley NTU Value, Harsanyi NTU Value)
- Edgeworth Box and General Equilibrium Exchange Economies
- Stable Matching and the Gale-Shapley Algorithm
- Nash Bargaining Solution and Kalai-Smorodinsky Bargaining Solution
- Debreu-Scarf Theorem and Core Convergence to Competitive Equilibrium