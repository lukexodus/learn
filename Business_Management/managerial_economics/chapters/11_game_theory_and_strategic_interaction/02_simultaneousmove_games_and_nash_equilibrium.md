## Simultaneous-Move Games and Nash Equilibrium


### Overview

Simultaneous-move games are strategic interactions in which players choose their actions **at the same time**, without observing the choices of other players before making their own decision. This does not necessarily require literal chronological simultaneity — it requires only that each player must choose without knowledge of rivals' current choices, which is why such games are also called games of **imperfect information** regarding contemporaneous moves.

The central solution concept for analyzing simultaneous-move games is the **Nash equilibrium**, developed by mathematician **John Nash** (1950), which provides a rigorous definition of a "stable" outcome in strategic settings — one from which no player has an incentive to unilaterally deviate.

### Formal Characteristics of Simultaneous-Move Games

- Represented in **normal form** (a payoff matrix for games with a small number of discrete strategies).
- Each player selects a strategy from their own strategy set without observing rivals' current-period choices.
- Payoffs are determined jointly by the full **strategy profile** — the combination of all players' chosen strategies.
- Common examples in managerial economics: simultaneous price-setting (Bertrand-type), simultaneous quantity-setting (Cournot-type), and simultaneous advertising or entry decisions.

### The Nash Equilibrium: Formal Definition

A **Nash equilibrium** is a strategy profile $(s_1^*, s_2^*, \ldots, s_n^*)$ such that **no player can improve their own payoff by unilaterally changing their strategy**, given the strategies chosen by all other players:

$$\pi_i(s_i^*, s_{-i}^*) \geq \pi_i(s_i, s_{-i}^*) \quad \text{for all feasible } s_i \in S_i \text{ and for every player } i$$

where $s_{-i}^*$ denotes the equilibrium strategies of all players other than $i$.

**Key Points:**

- Nash equilibrium is a condition of **mutual best responses**: every player's equilibrium strategy is a best response to every other player's equilibrium strategy, simultaneously, for all players.
- It does **not** require that the outcome be efficient, fair, or even mutually beneficial — only that no single player, acting alone, could improve their own position by deviating.
- A game may have **zero, one, or multiple** Nash equilibria in pure strategies; if no pure-strategy equilibrium exists, a **mixed-strategy Nash equilibrium** can generally be found (per Nash's existence theorem, at least one Nash equilibrium — pure or mixed — exists in any finite game).

### Finding Nash Equilibrium: The Best-Response Method

The standard technique for identifying pure-strategy Nash equilibria in a payoff matrix is to find each player's **best response** to every possible strategy the other player might choose, then identify the cell(s) where **both** players are simultaneously playing a best response to each other.

**Example: Identifying Nash equilibrium in a payoff matrix**

|  | Firm B: Advertise | Firm B: Don't Advertise |
| --- | --- | --- |
| **Firm A: Advertise** | (30, 30) | (60, 10) |
| **Firm A: Don't Advertise** | (10, 60) | (40, 40) |

**Step 1 — Find Firm A's best response to each of Firm B's choices:**

- If B Advertises: A gets 30 (Advertise) vs. 10 (Don't Advertise) → A's best response is **Advertise**.
- If B Doesn't Advertise: A gets 60 (Advertise) vs. 40 (Don't Advertise) → A's best response is **Advertise**.

Since A's best response is "Advertise" regardless of B's choice, **Advertise is a dominant strategy for Firm A**.

**Step 2 — Find Firm B's best response to each of Firm A's choices:**

- If A Advertises: B gets 30 (Advertise) vs. 10 (Don't Advertise) → B's best response is **Advertise**.
- If A Doesn't Advertise: B gets 60 (Advertise) vs. 40 (Don't Advertise) → B's best response is **Advertise**.

Since B's best response is "Advertise" regardless of A's choice, **Advertise is also a dominant strategy for Firm B**.

**Step 3 — Identify the Nash equilibrium**: Since both firms' best responses converge on (Advertise, Advertise), this cell is the unique Nash equilibrium, yielding payoffs **(30, 30)**.

Note that both firms would be strictly better off at (Don't Advertise, Don't Advertise), earning (40, 40) — but this outcome is **not** a Nash equilibrium, because each firm has a unilateral incentive to deviate to "Advertise" given the other stays at "Don't Advertise." This illustrates the same underlying logic as the **Prisoner's Dilemma**.

### Multiple Equilibria: The Coordination Game

Not all games have a unique Nash equilibrium. **Coordination games** typically feature multiple pure-strategy Nash equilibria.

**Example: Choosing a technology standard**

|  | Firm B: Standard X | Firm B: Standard Y |
| --- | --- | --- |
| **Firm A: Standard X** | (50, 50) | (0, 0) |
| **Firm A: Standard Y** | (0, 0) | (40, 40) |

Here, **both (Standard X, Standard X) and (Standard Y, Standard Y) are Nash equilibria** — in each case, neither firm can improve its payoff by unilaterally switching, given the other firm's choice. Game theory alone (without additional refinements like **payoff dominance**, historical precedent, or explicit communication/coordination devices) cannot predict which equilibrium will actually be selected — this is known as the **equilibrium selection problem**.

**Key Points:**

- (Standard X, Standard X) **Pareto-dominates** (Standard Y, Standard Y), since both players are strictly better off (50 > 40) — but Pareto dominance alone doesn't guarantee it will be the equilibrium reached without coordination.
- Coordination games are frequently used to model industry standard-setting, technology adoption, and network-effect markets.

### Mixed-Strategy Nash Equilibrium

When no pure-strategy Nash equilibrium exists — typically in games with conflicting interests and no dominant strategies, such as matching-pennies-type games — players may play a **mixed strategy**, randomizing across pure strategies with specific probabilities.

**Example: A simple matching game**

|  | Player B: Left | Player B: Right |
| --- | --- | --- |
| **Player A: Up** | (1, -1) | (-1, 1) |
| **Player A: Down** | (-1, 1) | (1, -1) |

No pure-strategy Nash equilibrium exists here (check each cell: at least one player always wants to deviate). The mixed-strategy equilibrium is found by making each player **indifferent** between their own pure strategies, based on the opponent's mixing probabilities.

Let Player B play "Left" with probability $q$ and "Right" with probability $(1-q)$. Player A's expected payoff from "Up" must equal the expected payoff from "Down" for A to be willing to mix:

$$E[\pi_A|\text{Up}] = q(1) + (1-q)(-1) = q - (1-q) = 2q - 1$$



$$E[\pi_A|\text{Down}] = q(-1) + (1-q)(1) = -q + (1-q) = 1 - 2q$$

Setting these equal:

$$2q - 1 = 1 - 2q \implies 4q = 2 \implies q = 0.5$$

By symmetry, Player A also mixes 50/50 between Up and Down. The mixed-strategy Nash equilibrium is $(0.5, 0.5)$ for both players, yielding an expected payoff of $0$ to each.

### Best-Response Function Diagram

```mermaid
graph LR
    A["Player A's strategy set (svg_diagram)"] -->|Best response function BR_A(s_B)| B["Player A's optimal choice given B's strategy"]
    C["Player B's strategy set"] -->|Best response function BR_B(s_A)| D["Player B's optimal choice given A's strategy"]
    B --> E{"Do BR_A and BR_B intersect?"}
    D --> E
    E -->|Yes| F["Nash Equilibrium found at intersection"]
    E -->|No pure intersection| G["Solve for mixed-strategy equilibrium instead"]
```

### Applications in Managerial Economics

| Application | Simultaneous Decision | Typical Equilibrium Concept |
| --- | --- | --- |
| Cournot oligopoly | Output quantities chosen simultaneously | Cournot-Nash equilibrium (intersection of reaction functions) |
| Bertrand oligopoly | Prices chosen simultaneously | Bertrand-Nash equilibrium (price = marginal cost under homogeneous goods) |
| Entry decisions | Multiple firms decide whether to enter a market simultaneously | Nash equilibrium in entry/no-entry strategies |
| Advertising competition | Firms set advertising budgets simultaneously | Nash equilibrium in advertising levels |
| R&D investment races | Firms choose R&D spending simultaneously | Nash equilibrium in innovation effort |

### Existence and Properties of Nash Equilibrium

**[Inference]** Nash's existence theorem guarantees that every finite game (finite number of players, each with a finite number of pure strategies) has **at least one Nash equilibrium**, possibly requiring mixed strategies — this is a foundational mathematical result relying on fixed-point theorems (specifically, Kakutani's fixed-point theorem), though the proof mechanics are typically beyond the scope of introductory managerial economics treatment.

**Important caveats:**

- Nash equilibrium is a **static** solution concept describing a stable outcome, not a description of the dynamic process by which players might arrive at that outcome.
- Multiple equilibria (as in coordination games) mean Nash equilibrium alone may have limited predictive power without additional refinements or contextual assumptions (e.g., focal points, historical convention, communication).
- Nash equilibrium assumes **common knowledge of rationality** and the game's structure — deviations from this assumption (e.g., bounded rationality, incomplete information about payoffs) require extensions such as **Bayesian Nash equilibrium**.

### Nash Equilibrium vs. Dominant Strategy Equilibrium

| Concept | Definition | Relationship |
| --- | --- | --- |
| Dominant strategy equilibrium | Each player's strategy is optimal regardless of others' choices | A stronger condition; always a Nash equilibrium if it exists |
| Nash equilibrium | Each player's strategy is optimal given others' actual equilibrium choices | A weaker, more general condition; does not require strategies to be dominant |

**Key Points:**

- Every dominant-strategy equilibrium is automatically a Nash equilibrium, but not every Nash equilibrium involves dominant strategies (as shown in the coordination game example, where best responses depend entirely on what the rival is expected to do).
- Nash equilibrium is the more broadly applicable concept, since many real strategic interactions (like the technology-standard example) do not feature dominant strategies at all.

**Related Topics:**

- Cournot and Bertrand oligopoly models as applications of Nash equilibrium
- Dominant and dominated strategies
- Mixed-strategy equilibria and randomization
- Coordination games and focal points (Schelling points)
- Sequential-move games and subgame perfect equilibrium
- Bayesian Nash equilibrium under incomplete information
- The Prisoner's Dilemma