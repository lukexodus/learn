## Bounded Rationality and Satisficing

### Definition and Origin

Bounded rationality is the concept that decision-makers' rationality is limited by the information they have, the cognitive limitations of their minds, and the finite time available to make decisions. It was introduced by Herbert Simon in the 1950s as a direct challenge to the neoclassical assumption of full, unbounded rationality (the "rational choice" model), in which agents are assumed to possess complete information, unlimited computational capacity, and stable, well-ordered preferences that allow them to identify and select the utility-maximizing option from all available alternatives.

Simon argued that this idealization does not describe how actual human decision-makers behave, because real agents operate under three binding constraints:

- **Limited information**: Agents rarely have complete knowledge of all available alternatives, their consequences, and their probabilities.
- **Limited cognitive processing capacity**: Even with complete information, agents have finite memory, attention, and computational ability to evaluate all options.
- **Limited time**: Decisions often must be made under time pressure, precluding exhaustive search and evaluation.

Given these constraints, Simon proposed that agents do not optimize; they **satisfice** — a portmanteau of "satisfy" and "suffice" — meaning they search through available alternatives only until they find one that meets a minimum acceptable threshold (an "aspiration level"), and then select it, rather than continuing to search for the theoretically optimal choice.

### Satisficing: Formal Structure

Satisficing can be represented as a sequential search process with a stopping rule defined by an aspiration level, in contrast to optimization, which requires evaluating the full choice set.

Let $S$ be the set of feasible alternatives, $u(s)$ the (unknown or costly-to-discover) value of alternative $s \in S$, and $a$ the decision-maker's aspiration level. Under a satisficing rule, the agent searches sequentially through alternatives $s_1, s_2, \ldots$ and stops at the first $s_i$ such that:

$$u(s_i) \geq a$$

This contrasts with the optimization rule, which requires identifying:

$$s^* = \arg\max_{s \in S} u(s)$$

The aspiration level $a$ is not fixed exogenously; Simon proposed that it adjusts dynamically based on experience — rising when good options are found easily (signaling a richer environment) and falling when search proves difficult (signaling a leaner environment). This adaptive-aspiration mechanism allows satisficing behavior to remain responsive to the actual difficulty of the decision environment without requiring full environmental knowledge in advance.

### Distinguishing Satisficing from Optimization

| Dimension | Optimization (Standard Model) | Satisficing (Bounded Rationality) |
| --- | --- | --- |
| Information requirement | Complete information on all alternatives | Partial, sequentially discovered information |
| Search process | Exhaustive evaluation of full choice set | Sequential search, stopped at first acceptable option |
| Stopping rule | Global maximum identified | Local threshold (aspiration level) met |
| Computational demand | Unbounded | Bounded by cognitive and time constraints |
| Outcome | Theoretically optimal | "Good enough," acceptable |
| Adaptivity | Static once information is known | Aspiration level adjusts with search experience |

An important clarification: satisficing is not itself framed by Simon as an error or a bias to be corrected. It is presented as a **rational adaptation** to an environment where the costs of continued search (in time, cognitive effort, or foregone opportunities) can exceed the expected benefit of finding a marginally better alternative. This positions bounded rationality as a theory of adaptive behavior under real-world constraints rather than a catalogue of mistakes.

### The Scissors Metaphor: Mind and Environment

Simon's most cited conceptual device is the "scissors" metaphor: human rational behavior is shaped by two blades — the cognitive limitations of the mind, and the structure of the environment in which decisions are made. Understanding a decision, he argued, requires analyzing both blades jointly rather than attributing outcomes solely to the properties of the mind. A heuristic or satisficing rule that appears crude in the abstract may in fact be well-matched to the statistical structure of the environment in which it is deployed, producing decisions that are functionally near-optimal despite requiring far less computation. This idea directly anticipates later "ecological rationality" research (e.g., Gigerenzer and colleagues), which argues that many heuristics perform well precisely because they exploit real regularities in natural task environments.

### Mechanisms of Bounded Rationality

Bounded rationality manifests through several interacting mechanisms, which later research programs elaborated in different directions:

- **Procedural rationality**: Simon distinguished "substantive rationality" (choosing the objectively best action given the goal) from "procedural rationality" (following a reasonable decision-making procedure given cognitive constraints). Bounded rationality evaluates decisions by the reasonableness of the procedure, not solely by the optimality of the outcome.
- **Sequential search with costly information acquisition**: Because gathering and processing information is costly, agents rationally truncate search once expected marginal benefits fall below marginal costs — a link later formalized in the economics of information (e.g., Stigler's search theory) and integrated with satisficing behavior.
- **Heuristic substitution**: When exact computation is infeasible, agents substitute simplified decision rules (heuristics) for the formally optimal procedure. This became the seed of the later heuristics-and-biases program (Kahneman and Tversky), though that program emphasizes systematic errors produced by heuristics, whereas Simon's original framing emphasized their adaptive, resource-conserving function.
- **Bounded memory and attention**: Limits on working memory and selective attention constrain how much of the available information can be simultaneously processed, reinforcing the need for simplified, sequential decision procedures.

### Practical Example: Job Search and Apartment Hunting

**Example**: Consider a person searching for an apartment in an unfamiliar city.

Under the optimizing model, the person would need to know the complete distribution of available apartments, their prices, locations, and amenities, evaluate all of them, and select the single best option — a task requiring effectively unlimited information and time.

Under a satisficing model, the person instead sets an aspiration level in advance based on prior experience or advice (e.g., "under $1,200/month, within 30 minutes of work, at least one bedroom"). They then view apartments sequentially and accept the first one that clears this threshold, rather than continuing to search the entire market for a theoretically superior unit. If early apartments viewed are unexpectedly good, the person may raise their aspiration level (holding out for something better); if the search proves difficult, the aspiration level falls (becoming more willing to accept a previously rejected feature, such as a longer commute).

This example illustrates the central satisficing dynamic: search is sequential and finite, the stopping rule is threshold-based rather than exhaustive, and the threshold itself adapts to the perceived difficulty of the search environment.

### Behavioral Economics Applications and Extensions

Bounded rationality and satisficing underpin a substantial portion of subsequent behavioral economics research, including:

- **Rational inattention**: A modern formalization (associated with Christopher Sims) in which agents optimally choose to process only a limited subset of available information due to information-processing costs, generating a tractable, information-theoretic model of bounded attention.
- **Heuristics-and-biases research**: Kahneman and Tversky's program can be read as a direct descendant of Simon's bounded rationality, empirically documenting specific heuristics (representativeness, availability, anchoring) and the systematic biases they produce relative to normative probability theory.
- **Behavioral industrial organization**: Models of firm search behavior, pricing under bounded rationality, and consumer search in markets with price dispersion draw directly on satisficing-style stopping rules.
- **Organizational decision-making theory**: Simon's original work (with James March) was substantially concerned with organizational and administrative behavior, arguing that firms and bureaucracies satisfice with respect to goals (e.g., "adequate profit," "fair market share") rather than maximizing a single objective function.

### Diagram: Satisficing Search Process

```mermaid
flowchart TD
    A[Set aspiration level a] --> B[Encounter next alternative s_i]
    B --> C{Does u(s_i) >= a?}
    C -- No --> D[Reject alternative]
    D --> E{Search cost/time exceeded?}
    E -- No --> B
    E -- Yes --> F[Lower aspiration level a]
    F --> B
    C -- Yes --> G[Accept alternative s_i]
    G --> H[Stop search]
```

### Visual: The Scissors Metaphor (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 320" font-family="Helvetica, Arial, sans-serif">
<text x="350" y="26" text-anchor="middle" font-size="16" font-weight="bold" fill="#222">Simon's Scissors Metaphor: Mind and Environment (svg_diagram)</text>
<circle cx="350" cy="170" r="34" fill="#fff6e0" stroke="#c98a1a" stroke-width="2" />
<text x="350" y="175" text-anchor="middle" font-size="12" fill="#5c3d0a">Rational</text>
<text x="350" y="190" text-anchor="middle" font-size="12" fill="#5c3d0a">behavior</text>
<line x1="350" y1="170" x2="150" y2="90" stroke="#3b5bdb" stroke-width="4" />
<rect x="60" y="55" width="180" height="70" rx="8" fill="#e8f0fe" stroke="#3b5bdb" stroke-width="1.5" />
<text x="150" y="82" text-anchor="middle" font-size="12" fill="#1a2b6d">Blade 1:</text>
<text x="150" y="98" text-anchor="middle" font-size="11" fill="#1a2b6d">Cognitive limits</text>
<text x="150" y="112" text-anchor="middle" font-size="11" fill="#1a2b6d">(memory, attention, time)</text>
<line x1="350" y1="170" x2="150" y2="250" stroke="#1f9d55" stroke-width="4" />
<rect x="60" y="215" width="180" height="70" rx="8" fill="#eafaf1" stroke="#1f9d55" stroke-width="1.5" />
<text x="150" y="242" text-anchor="middle" font-size="12" fill="#0f5c30">Blade 2:</text>
<text x="150" y="258" text-anchor="middle" font-size="11" fill="#0f5c30">Environmental</text>
<text x="150" y="272" text-anchor="middle" font-size="11" fill="#0f5c30">structure (task demands)</text>
<line x1="384" y1="170" x2="600" y2="170" stroke="#888" stroke-width="2" stroke-dasharray="5,4" />
<rect x="600" y="135" width="90" height="70" rx="8" fill="#f0f0f0" stroke="#555" stroke-width="1.5" />
<text x="645" y="162" text-anchor="middle" font-size="11" fill="#222">Observed</text>
<text x="645" y="178" text-anchor="middle" font-size="11" fill="#222">satisficing</text>
<text x="645" y="194" text-anchor="middle" font-size="11" fill="#222">choice</text>
</svg>

### Key Points

- Bounded rationality (Herbert Simon) holds that decision-makers are constrained by limited information, limited cognitive capacity, and limited time, making full optimization infeasible in most real decisions.
- Satisficing is the corresponding decision rule: search sequentially through alternatives and select the first one that meets or exceeds an aspiration level, rather than searching for the global optimum.
- The aspiration level is adaptive, rising or falling based on the perceived ease or difficulty of the search process.
- Simon distinguished procedural rationality (a reasonable decision process given constraints) from substantive rationality (an objectively optimal outcome); bounded rationality is evaluated on the former.
- The "scissors" metaphor emphasizes that rational behavior emerges from the joint interaction of cognitive limits and environmental structure, not from cognitive limits alone.
- Bounded rationality is the conceptual ancestor of later research programs including heuristics-and-biases theory, rational inattention, and ecological rationality, though these programs diverge in whether they treat resulting behavior as adaptive or biased.

**Related Topics**

- Herbert Simon's procedural versus substantive rationality
- Aspiration-level theory and adaptive goal-setting
- Ecological rationality and the "fast and frugal heuristics" program (Gigerenzer)
- Rational inattention and information-processing costs (Sims)
- Heuristics and biases: representativeness, availability, and anchoring
- Search theory and optimal stopping problems (Stigler)
- Organizational decision-making and the behavioral theory of the firm (Simon and March)
- Dual-process theories of cognition (System 1 / System 2) as a successor framework