## Identifying Variables and Causal Links

### Definition and Core Concept

Identifying variables and causal links is the foundational construction step of building a Causal Loop Diagram (CLD): selecting the correct set of quantities to represent as nodes, and correctly determining, for each pair of connected nodes, both the existence and the direction/polarity of the causal relationship between them. This step precedes loop identification and loop-dominance analysis (covered in the corresponding reference materials) and is the stage at which most CLD construction errors originate, since an incorrectly specified variable or mislabeled link propagates directly into an incorrect loop classification downstream.

This is a disciplined translation task: converting an unstructured verbal description of a situation (a narrative, a complaint, a stakeholder's account of "what's going on") into a precise, testable set of variable names and directional causal claims.

### Criteria for a Well-Formed Variable

**Key Points**

- A variable must be expressible as a **quantity capable of increasing or decreasing** — it should make grammatical and conceptual sense to say "X increases" or "X decreases." This is the single most important test for variable well-formedness.
- Variables should be stated as **neutral quantities**, not as fixed states, binary conditions, or value-laden judgments. "Employee Morale" is well-formed (it can rise or fall); "Employees Are Happy" is not (it is a fixed proposition, not a quantity), and "Toxic Culture" is not (it embeds a judgment rather than naming a measurable quantity).
- Variables should be stated in **noun-phrase form** describing a quantity, not as an action or event. "Rate of Customer Churn" is well-formed; "Customers Churn" (a verb phrase describing an event) is not directly usable as a CLD node, though it can usually be reformulated into an acceptable quantity ("Customer Churn Rate").
- Variables should avoid embedding a **causal direction or mechanism in the name itself**. A variable named "Quality Decline Due to Overwork" improperly pre-supposes the causal story rather than stating a neutral, measurable quantity ("Product Quality") that a separate, explicit causal link can then relate to another variable ("Employee Workload").
- Each variable should ideally represent a **single, distinct concept** rather than a bundle of related-but-separable ideas. "Employee Morale and Retention" conflates two variables that may have different causal relationships to the rest of the diagram and should generally be split into "Employee Morale" and "Employee Retention" as separate nodes.

### Common Variable-Naming Errors and Corrections

| Poorly Formed Variable | Problem | Corrected Variable |
| --- | --- | --- |
| "Employees Are Overworked" | Fixed binary state, not a quantity | "Employee Workload" |
| "Bad Customer Service" | Value-laden judgment, not neutral | "Customer Service Quality" |
| "Company Grows" | Verb/event phrase, not a noun-phrase quantity | "Company Revenue" or "Headcount" |
| "Poor Communication Causes Delays" | Embeds a causal claim inside the variable name | Split into "Communication Quality" and "Project Delay" as separate linked nodes |
| "Marketing and Sales Effectiveness" | Bundles two potentially distinct variables | Split into "Marketing Effectiveness" and "Sales Effectiveness" |
| "Low Trust" | States a specific value/direction rather than the underlying quantity | "Trust Level" (which can then be described as low or high, rising or falling) |

### Determining Causal Link Existence: Necessary Conditions

Before assigning a polarity to a proposed link between two variables, the link's *existence* itself should satisfy several conditions, adapted from standard causal-inference criteria (Bradford Hill-style reasoning, applied qualitatively rather than statistically):

1. **Mechanistic plausibility**: is there a plausible, describable mechanism by which a change in the proposed cause variable could produce a change in the proposed effect variable? A link should be traceable to *some* stated or implied mechanism, not asserted purely from observed co-occurrence.
2. **Directionality is defensible**: for the proposed direction (A causes B, rather than B causes A, or both), is there a reason — temporal precedence, known mechanism, or structural necessity — to prefer this direction specifically? Where both directions are plausible, this is itself important information (a candidate for circular causality — see the corresponding reference material — rather than grounds for arbitrarily picking one direction).
3. **Not better explained by confounding**: as discussed in the correlation/causation reference material, an apparent direct link between A and B should be checked against the possibility that a third variable C is the actual common cause of both, in which case the correct diagram includes C as a node with links to both A and B, rather than a direct A–B link.
4. **Appropriate directness**: a link should generally represent as direct a causal step as is meaningful for the diagram's purpose; if the "cause" only affects the "effect" through several identifiable, separately meaningful intermediate variables, those intermediate variables are usually worth including explicitly (see the aggregation-level discussion below) rather than compressing several distinct causal steps into a single link.

### Assigning Link Polarity: The Ceteris Paribus Test

The standard method for correctly assigning a $+$ or $-$ polarity to a link is the **ceteris paribus** ("all else held constant") thought experiment:

$$\text{Link polarity} = \begin{cases} + & \text{if increasing the cause, holding everything else constant, increases the effect (or a decrease causes a decrease)} \\ - & \text{if increasing the cause, holding everything else constant, decreases the effect (or a decrease causes an increase)} \end{cases}$$

**Example**

For the proposed link "Interest Rate → Loan Demand": holding all else constant, does an *increase* in interest rate cause an *increase* or *decrease* in loan demand? Higher rates make borrowing more expensive, so loan demand decreases — this is a negative link. The ceteris paribus framing is essential because, without holding other variables constant, an analyst might be tempted to reason from an observed historical correlation (e.g., "rates and loan demand both rose during an economic boom") that reflects the influence of other confounding variables (economic growth) operating simultaneously, rather than the isolated causal effect of the rate-demand link itself.

### Aggregation Level: Choosing the Right Granularity

**[Inference]** There is no single universally correct level of granularity for variable selection; the appropriate level depends on the diagram's purpose and audience, but a useful general guideline is that a variable should be as granular as needed to support the distinct causal claims relevant to the analysis, and no more granular than that, since excessive disaggregation produces visual clutter that obscures the loop structure the diagram is meant to reveal.

**Example**

For a diagram diagnosing organizational strategy, "Employee Morale" may be an appropriate single node. For a diagram specifically diagnosing HR retention policy, splitting this into "Compensation Satisfaction," "Manager Relationship Quality," and "Career Growth Perception" as separate variables may be necessary, because these sub-components plausibly have different causal links to different parts of the rest of the diagram (e.g., compensation satisfaction may link primarily to a market-benchmarking loop, while manager relationship quality may link primarily to a direct-supervisor feedback loop) — collapsing them into one node would obscure causally distinct loop structures that the retention-focused analysis specifically needs to expose.

### Illustrative Example: Extracting Variables and Links from an Unstructured Narrative

**Example**

Raw stakeholder narrative: "Whenever we cut the training budget to save money, new hires take longer to become productive, so overall team output drops, and then leadership panics about the output numbers and cuts the budget further to try to control costs."

**Extraction process:**

1. Identify candidate quantities: "Training Budget," "Time to New-Hire Productivity" (or, inverted for easier polarity reading, "New-Hire Productivity Level"), "Team Output," "Perceived Cost Pressure" (leadership's reaction is a response to a perceived condition, which is itself a variable capable of increasing or decreasing).
2. Determine link directions and polarity:
   - Training Budget → New-Hire Productivity Level: increasing budget increases productivity (positive link).
   - New-Hire Productivity Level → Team Output: increasing productivity increases output (positive link).
   - Team Output → Perceived Cost Pressure: increasing output *decreases* perceived cost pressure (negative link — the narrative states dropping output causes panic, i.e., low output causes high pressure, confirming an inverse relationship).
   - Perceived Cost Pressure → Training Budget: increasing perceived cost pressure decreases the training budget (negative link — pressure drives cuts).
3. Count negative links in the closed loop: $n = 2$ (even) → **reinforcing loop**. This is a critical and non-obvious result: despite the narrative reading as leadership taking "corrective" cost-cutting action, the loop as extracted is actually self-reinforcing (a vicious cycle that will drive training budget progressively lower and output progressively lower with each iteration), not a stabilizing balancing loop — a direct illustration of why explicit variable/link extraction and polarity counting, rather than intuitive narrative reading, is necessary to correctly classify loop behavior (see also the analogous budget-freeze pitfall documented in the balancing-loop reference material).

```mermaid
flowchart LR
    TB["Training Budget"] -->|"+"| NP["New-Hire Productivity Level"]
    NP -->|"+"| TO["Team Output"]
    TO -->|"-"| CP["Perceived Cost Pressure"]
    CP -->|"-"| TB
```

### Distinguishing Links from Correlational Observations

As detailed in the correlation/causation reference material, a proposed link should reflect a defensible causal mechanism, not merely an observed statistical association during the interview or data-gathering process that preceded diagram construction. When a stakeholder reports "X and Y always move together," the correct CLD-construction response is to probe further for the *mechanism* (is it X causing Y, Y causing X, a shared confounding driver, or genuine mutual/circular causation) before committing to a specific directed link in the diagram — recording an unexamined correlation as a directed causal arrow is a common source of structurally invalid CLDs.

### Practical Elicitation Techniques

**Key Points**

- **"If X increases, what happens to Y, holding everything else fixed?"** is the standard interview question format for eliciting both link existence and polarity directly from a domain expert or stakeholder, and should be asked explicitly rather than inferred from a stakeholder's more general narrative description.
- **Working from an outcome variable backward** ("what causes changes in the problem symptom we care about?") and then continuing to ask "and what causes changes in *that*?" repeatedly is a standard technique for surfacing the intermediate variables and eventually discovering whether the chain closes into a loop.
- **Cross-checking a proposed link against multiple stakeholders or data sources** helps identify links that are contested or only locally true (valid in one part of the organization/system but not universally), which should be flagged as scope-limited or examined further rather than included as an unqualified universal link.
- **[Unverified]** Documenting the confidence level or evidentiary basis for each link (e.g., "supported by data," "expert judgment only," "disputed by some stakeholders") alongside the diagram itself is a practice used in some group-model-building contexts to preserve the diagram's epistemic status, though this level of annotation is not a universal CLD convention and its adoption varies by practitioner and context.

### Common Pitfalls

- **Skipping the ceteris paribus discipline and inferring polarity from observed correlation alone**, which risks conflating a confounded association with a genuine direct causal effect.
- **Embedding causal claims inside variable names**, which pre-judges the very causal question the diagram is meant to make explicit and testable.
- **Choosing an inconsistent level of granularity across the diagram**, mixing highly aggregated variables (e.g., "Company Performance") with highly specific ones (e.g., "Q3 Customer Support Response Time") in the same diagram, which produces links of very different conceptual scope that are difficult to compare or reason about together.
- **Treating every observed association as evidence of a direct link**, rather than considering confounding or circular causality as alternative explanations, as detailed in the correlation/causation reference material.
- **Failing to include an inverted (negatively stated) variable form when needed for polarity clarity**: choosing between stating a variable as "Product Quality" versus "Product Defect Rate" changes the polarity sign of every link touching that variable; consistency in variable framing (generally preferring the "more is more positive/desirable" framing where practical, though not mandatory) reduces the risk of arithmetic-style sign errors when later counting negative links to classify loops.

**Related Topics**

- Purpose and Uses of Causal Loop Diagrams
- Reinforcing (Positive) Feedback Loops
- Balancing (Negative) Feedback Loops
- Correlation, Causation, and Circular Causality
- Stocks and Flows as Building Blocks
- Systems Archetypes (Shifting the Burden, Fixes That Fail)
- Group Model Building and Facilitation
- Confounding Variables and Spurious Correlation