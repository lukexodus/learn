## Static Games and the Design of Legal Rules

### Conceptual Foundations

Game theory enters law and economics analysis wherever legal outcomes depend not on a single actor's isolated optimization problem but on the *interaction* of multiple strategic actors whose payoffs depend on each other's choices — plaintiffs and defendants deciding whether to litigate or settle, potential injurers and victims jointly determining precaution levels, competing firms deciding whether to comply with or violate regulation, legislators and interest groups bargaining over rule content. Static games — those in which players choose actions simultaneously (or effectively simultaneously, meaning without observing the other's choice before acting) and the game is played once, without repetition — provide the foundational analytical toolkit for this class of problems, prior to the added complexity of sequential moves (covered in a subsequent item) or repeated interaction.

**Key Points**

- A game in normal (strategic) form is fully specified by three elements: the set of players, the set of strategies available to each player, and the payoff function mapping every strategy combination to a payoff for each player — legal rule design operates on all three margins, since law can restrict available strategies (prohibiting certain conduct), alter payoffs (through damages, fines, or subsidies), or occasionally affect the player set itself (standing rules, joinder doctrine)
- The equilibrium concept doing the primary analytical work in static games is the **Nash equilibrium**: a strategy combination in which no player can improve their own payoff by unilaterally deviating, given the other players' strategies — legal rules are frequently designed with the explicit or implicit goal of shifting the Nash equilibrium of an underlying strategic interaction toward a socially efficient outcome
- The central law and economics insight distinguishing game-theoretic analysis from single-actor optimization (as in the basic Hand Formula or unilateral-precaution tort models) is that legal rules affecting one party's incentives generically affect the *other* party's optimal response as well — rule design must account for this strategic interdependence rather than analyzing each party's incentive in isolation

### The Prisoner's Dilemma Structure in Legal Contexts

**Key Points**

- The prisoner's dilemma — a game in which each player has a dominant strategy (a best response regardless of the other player's choice) leading to a Nash equilibrium that is Pareto-inferior to an alternative, mutually cooperative outcome both players could jointly achieve — is the single most frequently invoked static-game structure in law and economics, because it formalizes precisely the situation where individually rational behavior produces collectively inefficient outcomes, motivating a legal-rule response
- **Applied legal example: pollution and common-pool resource extraction**. Two firms sharing a common environmental resource (a river's assimilative capacity, a fishery, an aquifer) each face a dominant strategy to over-extract or over-pollute relative to the jointly efficient level, since each firm's private cost-benefit calculation does not internalize the externality imposed on the other firm (or on third parties) — the resulting Nash equilibrium is inefficient, providing the strategic-interaction-based rationale (complementing the more familiar single-actor externality analysis) for regulatory intervention (Pigouvian taxation, cap-and-trade, or property-rights allocation via a Coasean solution) that shifts the payoff structure so cooperation (efficient extraction) becomes each player's dominant strategy or equilibrium behavior

$$\begin{array}{c|cc} & \text{Firm B: Low Extraction} & \text{Firm B: High Extraction} \\ \hline \text{Firm A: Low Extraction} & (3,3) & (0,4) \\ \text{Firm A: High Extraction} & (4,0) & (1,1) \end{array}$$

In this canonical payoff structure, "High Extraction" strictly dominates "Low Extraction" for both firms (4 > 3 and 1 > 0 for Firm A regardless of Firm B's choice, symmetrically for Firm B), producing the inefficient (1,1) Nash equilibrium despite (3,3) being achievable and Pareto-superior — the formal structure underlying tragedy-of-the-commons-style regulatory justifications.

- **Applied legal example: cartel/antitrust enforcement design**. Firms in an oligopoly face a prisoner's-dilemma-structured incentive to deviate from a collusive (jointly profit-maximizing) price toward a lower, competitive-undercutting price, since each individual firm profits from unilateral deviation given the other firms' collusive pricing — antitrust leniency programs are explicitly designed as a game-theoretic intervention exploiting this same underlying dominant-strategy logic *in reverse*, restructuring the payoffs of *cartel members reporting to authorities* (rather than the underlying pricing game) to make defection from the cartel (reporting/cooperating with enforcement) a dominant strategy, directly undermining cartel stability

===MERMAID_DIAGRAM===

flowchart TD

A[Strategic Interaction: Two or More Legal Actors] --> B{Payoff Structure Type}

B -->|Dominant Strategy Leads to Inefficient Equilibrium| C[Prisoner's Dilemma Structure]

B -->|Multiple Equilibria, Coordination Needed| D[Coordination Game Structure]

B -->|One Player's Gain Is Other's Loss| E[Zero-Sum / Constant-Sum Structure]

C --> F[Example: Common-Pool Resource Overextraction]

C --> G[Example: Cartel Pricing Incentive]

D --> H[Example: Contract Default Term Selection]

D --> I[Example: Legal Standard Convention - Drive on Right vs Left]

F --> J[Legal Response: Pigouvian Tax / Cap-and-Trade Shifts Payoffs]

G --> K[Legal Response: Leniency Program Restructures Reporting Payoffs]

H --> L[Legal Response: Majoritarian Default Selects Focal Equilibrium]

### Coordination Games and the Focal-Point Function of Legal Rules

**Key Points**

- Unlike the prisoner's dilemma, **coordination games** feature multiple Nash equilibria, all or several of which may be efficient, with the strategic problem being which equilibrium players actually converge upon absent explicit communication — the canonical example is a pure convention (which side of the road to drive on), where either uniform convention is efficient but coordination failure (some drivers choosing each side) is catastrophic
- Legal rules in coordination-game contexts serve primarily a **focal-point (Schelling point) function** rather than an incentive-correction function: the rule's content matters less than the fact that it provides a shared, common-knowledge reference point around which independent actors can coordinate their expectations and behavior, resolving the multiplicity-of-equilibria problem that pure decentralized bargaining or convention-formation might resolve only slowly or unreliably
- **Default contract terms as coordination devices**: in the companion behavioral-contract-theory material, default terms were analyzed primarily through a behavioral status-quo-bias lens; a complementary, non-behavioral game-theoretic rationale for default-rule selection is that even fully rational parties benefit from a legally-supplied focal default in situations where the specific term is not the primary subject of negotiation and any reasonable default is preferable to the transaction costs of explicit negotiation over every minor term — legal default-rule design in this framing should aim to select the **majoritarian default** (the term most transacting parties would have chosen absent transaction costs), minimizing the number of parties who must incur the cost of explicitly contracting around an unwanted default
- **Statutory and regulatory standardization**: technical standards (electrical specifications, measurement units, filing formats) mandated by regulation frequently serve a pure coordination function distinct from externality-correction, since the specific standard chosen matters less than universal adoption of *some* common standard, making the legal mandate valuable primarily for its coordinating, equilibrium-selecting function

### Assurance Games and the Role of Credible Legal Commitment

**Key Points**

- Assurance games (also called stag-hunt games) differ from both the prisoner's dilemma and pure coordination games: cooperation is a Nash equilibrium and is Pareto-superior to the alternative, but a second, Pareto-inferior "safe" equilibrium also exists, and which equilibrium prevails depends on each player's confidence that the other will also cooperate rather than defect
- This structure is analytically relevant to legal contexts involving mutual investment or reliance under uncertainty about counterparty behavior — for example, relation-specific investment in long-term contracting, where each party's willingness to make efficient relationship-specific investments depends on confidence that the other party will not subsequently exploit the resulting bilateral monopoly position (the classical hold-up problem, more fully developed in transaction-cost-economics and incomplete-contract-theory treatments elsewhere in this course)
- Legal enforceability of contractual commitments functions in assurance-game contexts as a *confidence-restoring* mechanism: by making defection from the cooperative equilibrium costly (via enforceable damages or specific performance), contract law shifts players' beliefs about counterparty behavior in a way that can move the game from the inefficient "safe" equilibrium toward the efficient cooperative equilibrium — this is a distinct game-theoretic rationale for contract enforceability from the simpler mechanism (deterring unilateral breach given fixed counterparty behavior) typically emphasized in introductory contract-remedies analysis

### Mixed Strategies and Legal Enforcement Design

**Key Points**

- Where a game has no pure-strategy Nash equilibrium (a common structure in matching-pennies-type enforcement games, where one player wants to match the other's action and the other wants to avoid matching), equilibrium exists only in **mixed strategies** — probabilistic randomization over available pure strategies
- **Applied legal example: regulatory audit and inspection games**. A regulated firm chooses whether to comply with a legal standard; a regulator chooses whether to audit/inspect. If auditing is costly and compliance is costly, neither "always audit" nor "always comply" (nor their opposites) is typically a stable pure-strategy equilibrium — the regulator wants to audit only non-compliant firms (but cannot distinguish them without auditing) and the firm wants to comply only when audit probability is sufficiently high to make non-compliance's expected penalty exceed compliance cost, producing a mixed-strategy equilibrium in which both audit frequency and compliance rates are strictly between 0 and 1
- This mixed-strategy framework directly informs the economically optimal audit-probability design question: the regulator's optimal randomized audit frequency is the frequency that makes the firm indifferent between compliance and non-compliance (given the penalty level), while the resulting equilibrium compliance rate is determined by the analogous indifference condition on the regulator's side — a direct extension of the deterrence-theory material (Becker's economic model of crime and punishment) to a setting with costly, imperfect detection

$$p^* = \frac{c}{f}$$

where $p^*$ is the equilibrium audit probability, $c$ is the firm's cost of compliance, and $f$ is the penalty imposed if non-compliance is detected — illustrating the core mixed-strategy-equilibrium comparative static that higher penalties permit lower (and therefore less enforcement-cost-intensive) equilibrium audit frequencies while sustaining the same compliance incentive, a foundational result underlying optimal-enforcement-intensity design across regulatory domains.

### Comparing Static-Game Structures and Their Legal-Design Implications

| Game Structure | Defining Feature | Legal-Design Implication | Example |
| --- | --- | --- | --- |
| Prisoner's Dilemma | Dominant strategy produces inefficient equilibrium | Restructure payoffs (tax, subsidy, penalty) to make cooperation dominant or equilibrium-selecting | Common-pool resource regulation, cartel leniency programs |
| Pure Coordination | Multiple efficient equilibria; problem is which one prevails | Supply a focal point/default; content matters less than commonality | Technical standards, majoritarian contract defaults |
| Assurance/Stag Hunt | Efficient equilibrium exists but requires mutual confidence | Enforceable commitment restores confidence, shifts equilibrium selection | Relation-specific investment, contract enforceability |
| Matching/Mismatching (mixed-strategy) | No stable pure-strategy equilibrium | Design optimal randomized enforcement intensity | Regulatory audit/inspection design, tax enforcement |

### Limitations of Static Analysis and the Transition to Dynamic Games

**Key Points**

- Static (simultaneous-move, one-shot) game analysis is a foundational but incomplete toolkit for most real legal strategic interactions, which frequently involve sequential moves (one party observes and responds to another's prior action — covered in the companion sequential-games item), repeated interaction over time (enabling reputation and cooperation-sustaining mechanisms unavailable in one-shot settings), and incomplete information (players uncertain about other players' payoffs or types, requiring Bayesian equilibrium concepts beyond the complete-information Nash equilibrium emphasized here)
- Nonetheless, static-game analysis remains analytically foundational because sequential and repeated games are frequently formally decomposed into, or reduced to, static subgames at each decision node or repetition, making fluency with basic Nash-equilibrium reasoning and canonical payoff structures (prisoner's dilemma, coordination, assurance, matching games) a necessary prerequisite for the more complex dynamic-game and information-economics material that follows

**Next Steps**

- Sequential games and extension form: backward induction and subgame-perfect equilibrium in legal contexts
- Repeated games, reputation, and the folk theorem's implications for self-enforcing legal norms
- Bayesian games and incomplete information in litigation and contracting (signaling and screening revisited through a formal game-theoretic lens)
- Mechanism design and optimal legal-rule construction under private information
- Becker's economic model of crime and punishment as a foundation for the audit-game enforcement framework
- Antitrust economics and formal oligopoly models (Cournot, Bertrand) as static-game applications