## Renegotiation Proofness

### Definition

**Renegotiation proofness** is a refinement of subgame perfect equilibrium for repeated games that addresses a specific credibility concern left unresolved by subgame perfection alone: even when a punishment phase is a mutual best response (and thus subgame perfect in the standard sense), the punishing players might, upon actually reaching that phase, **jointly prefer to abandon the punishment and renegotiate back to a more mutually beneficial continuation** — a possibility that standard subgame perfection does not rule out, since it only checks unilateral deviations, not jointly beneficial departures from the prescribed equilibrium path.

### Motivation: The Problem with Harsh Punishments

Consider grim trigger in an infinitely repeated Prisoner's Dilemma: upon a deviation, both players revert to mutual defection $(1,1)$ forever. This punishment phase is subgame perfect (mutual defection is a Nash equilibrium of the stage game, hence a best response to itself indefinitely). However, once a deviation has actually occurred and both players find themselves facing the prospect of eternal $(1,1)$ payoffs, they might reason:

> "We are both about to lock ourselves into a payoff of $1$ forever. If we could simply agree to forget the past deviation and resume cooperating at $(3,3)$, we would both be strictly better off. Since we can communicate and no external enforcement prevents us from jointly deciding to do this, why would we actually carry out the harsh punishment?"

**Key Points**

- This concern does not arise from a *unilateral* incentive to deviate (which subgame perfection already rules out) but from a **joint, mutually beneficial renegotiation** away from the prescribed continuation strategy — a fundamentally different kind of credibility problem.
- The renegotiation-proofness literature asks: can we identify a *refined* class of equilibria whose punishment phases are themselves immune to this kind of joint renegotiation, so that the threat to punish is credible not just against unilateral deviation but also against mutual re-optimization?

### Formal Idea: Internal Consistency of Punishments

A repeated-game equilibrium is (informally) **renegotiation-proof** if, for every possible history that could arise along the equilibrium path (including punishment phases), the continuation equilibrium specified from that point onward is **not Pareto-dominated by any other equilibrium continuation available to the players from that same point**. In other words, no on-path or off-path continuation phase should be a "worse deal for everyone" than some alternative equilibrium continuation that the players could switch to instead.

**Key Points**

- This is a substantially more demanding requirement than plain subgame perfection: subgame perfection asks only that no single player wants to unilaterally deviate given the continuation strategies; renegotiation proofness additionally asks that the continuation itself not be jointly dominated by another available equilibrium continuation.
- A significant technical subtlety (identified early in the literature, e.g., by Bernheim and Ray, 1989, and Farrell and Maskin, 1989) is that **renegotiation proofness is not simply "always pick the best equilibrium"**: if punishments must themselves be drawn from the set of renegotiation-proof equilibria, this creates a **self-referential, fixed-point definitional problem** — the very set of "acceptable punishments" must be consistent with itself, since a punishment that is later abandoned via renegotiation was never actually a credible punishment in the first place.

### The Farrell-Maskin Weak Renegotiation-Proofness Concept

Joseph Farrell and Eric Maskin (1989) proposed one influential formalization, **weak renegotiation-proofness (WRP)**: a set of equilibrium payoffs $E$ is weakly renegotiation-proof if no continuation payoff vector prescribed within any equilibrium in $E$ is **strictly Pareto-dominated** by another payoff vector also achievable within $E$. This creates the fixed-point structure: one must find a self-consistent set of equilibria such that no equilibrium in the set is dominated by another equilibrium *within that same set*.

**Key Points**

- [Inference] Under this definition, in the standard infinitely repeated Prisoner's Dilemma, grim trigger (with its permanently harsh $(1,1)$ punishment) generally **fails** to be renegotiation-proof for a wide range of discount factors, precisely because $(1,1)$-forever is Pareto-dominated by resuming cooperation at $(3,3)$, which both players would prefer — this is the formalization of the intuitive concern raised above.
- The Farrell-Maskin framework instead typically identifies **milder, self-consistent punishment-and-forgiveness cycles** (e.g., temporarily reverting to a less severe, but still individually costly, punishment payoff that both players find preferable to full defection but still costly enough to deter the original deviation) as sustainable renegotiation-proof equilibria.

### Bernheim-Ray's Alternative: Internally Consistent Equilibria

B. Douglas Bernheim and Debraj Ray (1989) independently developed a related but distinct formalization, sometimes emphasizing **weak perfection** and **consistency**, arriving at qualitatively similar conclusions: harsh, permanently punitive equilibria are generally not robust to renegotiation, and the renegotiation-proof equilibrium payoff set is typically **smaller** than the full (unrestricted) subgame-perfect Folk Theorem payoff set.

**Key Points**

- [Inference] A general and important finding across this literature is that **imposing renegotiation-proofness typically shrinks the set of sustainable cooperative payoffs** relative to the full Folk Theorem set: harsher, more effective deterrents (like grim trigger's permanent breakdown) are precisely the punishments most vulnerable to being renegotiated away, so requiring renegotiation-proofness limits how severe (and hence how effective) available punishments can be, which in turn limits how much cooperation can be sustained at a given discount factor $\delta$.

### Diagram: Subgame Perfection vs. Renegotiation Proofness

```mermaid
flowchart TD
    A["Deviation occurs"] --> B["Grim trigger prescribes:<br/>defect forever, both get (1,1)"]
    B --> C{"Is (1,1)-forever Pareto-dominated<br/>by some other available<br/>equilibrium continuation?"}
    C -->|Yes, e.g. by resuming<br/>cooperation at (3,3)| D["NOT renegotiation-proof:<br/>players would jointly<br/>abandon the punishment"]
    C -->|No dominating<br/>alternative exists| E["Renegotiation-proof:<br/>punishment survives<br/>joint reoptimization"]
```

### Worked Example: A Simple Illustration of the Tension

Suppose, in the repeated Prisoner's Dilemma, we try to replace grim trigger's harsh punishment with a milder scheme: upon deviation, both players play mutual defection for exactly **one round**, then automatically resume cooperation.

**Step 1 — Check the punishment's own credibility**: during the single punishment round, is mutual defection still a best response? Yes, trivially, since it is the stage-game Nash equilibrium.

**Step 2 — Check whether resuming cooperation afterward is itself consistent**: this is exactly the ordinary cooperative continuation, which is fine as long as the original sustainability inequality holds.

**Step 3 — Check for renegotiation vulnerability**: is there any point at which the players, having reached the punishment round, would jointly prefer some *other* available equilibrium continuation over "one round of $(1,1)$, then resume cooperation"? [Inference] If "immediately resume cooperation with no punishment at all" is itself an available equilibrium continuation in the relevant equilibrium set, the one-round-punishment scheme could also be vulnerable, since skipping the punishment round strictly Pareto-dominates enduring it — this illustrates why constructing a genuinely renegotiation-proof equilibrium set is a delicate, self-referential exercise rather than simply "pick a milder punishment," and typically requires the more careful fixed-point constructions of Farrell-Maskin or Bernheim-Ray rather than ad hoc weakening of the punishment.

**Key Points**

- This example demonstrates why merely softening a punishment does not automatically solve the renegotiation problem: the *existence* of an even milder, mutually preferable alternative continuation is what must be ruled out, which requires reasoning about the entire equilibrium set self-consistently, not just the single punishment scheme in isolation.

### Relationship to the Folk Theorem and Other Refinements

| Concept | Requirement | Typical Effect on Sustainable Payoff Set |
| --- | --- | --- |
| Nash Equilibrium | No unilateral deviation from any single player, on path only | Largest set (weakest refinement) |
| Subgame Perfect Equilibrium | No unilateral deviation, in every subgame (on- and off-path) | Smaller than Nash; rules out non-credible threats |
| Renegotiation-Proof Equilibrium | No jointly Pareto-improving departure from any continuation | Smaller still; rules out punishments vulnerable to joint re-optimization |

**Key Points**

- Renegotiation proofness sits as a further refinement *within* the broader landscape of subgame perfect equilibria established by the Folk Theorem — it does not expand the equilibrium set beyond what the Folk Theorem allows, but rather narrows it to a subset considered more behaviorally and institutionally plausible in settings where players can freely communicate and jointly agree to deviate from a prescribed harsh continuation.

### Applications and Real-World Relevance

- **Labor and relational contracts**: informal workplace norms rarely rely on genuinely permanent breakdowns of cooperation following a single infraction; observed real-world "punishment then forgiveness" dynamics (e.g., temporary reduced trust followed by relationship repair) are often better modeled using renegotiation-proof, milder punishment schemes than by literal grim trigger.
- **International agreements and diplomacy**: nations that violate a treaty are rarely punished with genuinely permanent trade or diplomatic breakdown; the frequent observation of negotiated "return to normal relations" after a period of sanctions is consistent with renegotiation-proof rather than grim-trigger dynamics.
- **Organizational design**: the theory offers a caution to institutional designers: a nominally harsh, deterrence-maximizing punishment rule (e.g., in a formal contract or organizational policy) may be undermined in practice if the parties retain the practical ability to jointly renegotiate around it once the triggering event occurs — a consideration relevant to contract design and mechanism design more broadly.

### Common Pitfalls

- **Assuming any subgame perfect equilibrium is behaviorally robust**: subgame perfection alone does not guard against jointly beneficial renegotiation; a strategy profile can be perfectly rational to follow unilaterally yet still be practically unstable if the players can communicate and jointly agree to abandon it.
- **Treating "milder punishment" as automatically solving the problem**: as the worked example shows, weakening a punishment does not by itself guarantee renegotiation-proofness; the correct construction requires the fixed-point-consistent equilibrium-set reasoning of the formal literature (Farrell-Maskin, Bernheim-Ray), not ad hoc adjustment.
- **Overlooking the reduced cooperative capacity**: a common oversight is to assume renegotiation-proofness is a "free" refinement with no cost; in fact, it generally **shrinks** the sustainable payoff set relative to the unrestricted Folk Theorem, since the harshest and most effective punishments are usually the ones most vulnerable to renegotiation.
- **Behavior may vary**: whether real-world parties actually behave in a renegotiation-proof manner (versus committing credibly to harsh punishments via external enforcement, reputational costs of reneging, or other institutional features) is an empirical and context-dependent question, not something the theory alone resolves.

**Related Topics**

- The Folk Theorem
- Trigger Strategies and Punishment
- Subgame Perfect Equilibrium
- Abreu's Optimal Penal Codes
- Reputation Effects
- Contract Theory and Relational Contracts
- Equilibrium Selection and Focal Points