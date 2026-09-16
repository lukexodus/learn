## Prospect Theory and Framing Effects

### Overview

Prospect theory, developed by Daniel Kahneman and Amos Tversky, is a descriptive model of decision-making under risk that systematically outperforms expected utility theory (EUT) in explaining observed choices. It replaces EUT's assumption of stable evaluation over final wealth states with a **reference-dependent** framework in which people code outcomes as gains or losses relative to a reference point, and evaluate probabilities through a nonlinear weighting function rather than treating them at face value. Closely tied to prospect theory is the study of **framing effects** — the finding that logically equivalent descriptions of the same choice problem can produce systematically different decisions, violating the standard assumption of description invariance.

### Structure of Prospect Theory

Prospect theory decomposes decision-making under risk into two phases:

1. **Editing phase**: the decision-maker simplifies and reorganizes the available prospects — coding outcomes relative to a reference point, combining probabilities of identical outcomes, and often discarding common components shared across options.
2. **Evaluation phase**: the edited prospects are evaluated using a value function $v(\cdot)$ applied to gains/losses and a probability weighting function $\pi(\cdot)$ applied to stated probabilities, combined to form an overall prospect value:

$$V = \sum_{i} \pi(p_i) \, v(x_i)$$

where $x_i$ are outcomes expressed as gains or losses relative to the reference point, and $\pi(p_i)$ is the decision weight assigned to probability $p_i$.

```mermaid
flowchart TD
    A[Present a risky prospect] --> B[Editing Phase]
    B --> C[Code outcomes relative to reference point]
    B --> D[Combine/simplify probabilities]
    C --> E[Evaluation Phase]
    D --> E
    E --> F[Apply value function v to gains/losses]
    E --> G[Apply probability weighting function pi to probabilities]
    F --> H[Compute prospect value V = sum of pi(p) * v(x)]
    G --> H
    H --> I[Choose prospect with highest V]
```

### The Value Function

The value function $v(x)$, defined over deviations from a reference point rather than absolute wealth, has three defining properties:

- **Reference dependence**: $v(0) = 0$; outcomes are evaluated relative to a reference point (often the status quo, an expectation, or an aspiration level) rather than final asset position.
- **Diminishing sensitivity**: $v$ is concave for gains ($x > 0$) and convex for losses ($x < 0$) — the marginal psychological impact of a change shrinks as the outcome moves further from the reference point in either direction, producing risk aversion over gains and risk-seeking over losses.
- **Loss aversion**: the function is steeper for losses than for gains — a loss of a given magnitude looms larger than an equally sized gain: $|v(-x)| > v(x)$ for $x > 0$.

A common functional form, from Tversky and Kahneman's 1992 cumulative prospect theory:

$$v(x) = \begin{cases} x^{\alpha} & x \geq 0 \\ -\lambda(-x)^{\beta} & x < 0 \end{cases}$$

with typical estimated parameters $\alpha, \beta \approx 0.88$ and loss-aversion coefficient $\lambda \approx 2.25$. [Unverified: these specific numeric values come from a particular experimental study and elicitation method; subsequent studies have produced a range of estimates, so they should be treated as illustrative rather than universal constants.]

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 520 400">
<text x="260" y="25" text-anchor="middle" font-size="15" font-weight="bold" fill="#222">Prospect Theory Value Function (svg_diagram)</text>
<line x1="260" y1="350" x2="260" y2="40" stroke="#333" stroke-width="2" />
<line x1="60" y1="200" x2="460" y2="200" stroke="#333" stroke-width="2" />
<text x="465" y="205" font-size="12" fill="#333">x (gain/loss)</text>
<text x="270" y="35" font-size="12" fill="#333">v(x)</text>
<path d="M 260,200 Q 350,120 460,90" fill="none" stroke="#2ca02c" stroke-width="2.5" />
<path d="M 260,200 Q 190,300 90,350" fill="none" stroke="#d62728" stroke-width="2.5" />

<text x="330" y="105" font-size="10" fill="`#2ca02c`">Concave over gains (risk-averse)</text>

<text x="80" y="325" font-size="10" fill="`#d62728`">Convex over losses, steeper slope (risk-seeking, loss-averse)</text>

<line x1="290" y1="200" x2="290" y2="150" stroke="#999" stroke-dasharray="3,2" />
<line x1="230" y1="200" x2="230" y2="270" stroke="#999" stroke-dasharray="3,2" />
<text x="150" y="230" font-size="9" fill="#555">Equal-magnitude loss produces</text>
<text x="150" y="242" font-size="9" fill="#555">larger |v| than equal-magnitude gain</text>
</svg>

### The Probability Weighting Function

Rather than using objective probabilities $p$ directly, prospect theory applies a **decision weight** $\pi(p)$ derived from a nonlinear weighting function $w(p)$ with these regularities:

- **Overweighting of small probabilities**: rare events are given disproportionately high decision weight relative to their objective probability (this is used to explain both lottery-ticket purchases and demand for low-probability catastrophic-loss insurance).
- **Underweighting of moderate-to-large probabilities**: probabilities in the middle-to-high range are given less decision weight than their objective value.
- **Subcertainty**: $w(p) + w(1-p) < 1$ for most $p$ — the sum of weights on complementary events is less than one.
- **Overweighting of certainty**: outcomes with probability exactly 1 are typically weighted precisely at 1, creating a discontinuity near certainty known as the **certainty effect** — a large psychological difference between "certain" and "almost certain" that is disproportionate to the small change in probability.

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 500 400">
<text x="250" y="25" text-anchor="middle" font-size="15" font-weight="bold" fill="#222">Probability Weighting Function (svg_diagram)</text>
<line x1="70" y1="350" x2="70" y2="40" stroke="#333" stroke-width="2" />
<line x1="70" y1="350" x2="450" y2="350" stroke="#333" stroke-width="2" />
<text x="455" y="355" font-size="11" fill="#333">Objective p</text>
<text x="40" y="40" font-size="11" fill="#333">Weight w(p)</text>
<line x1="70" y1="350" x2="450" y2="70" stroke="#999" stroke-width="1.5" stroke-dasharray="4,3" />
<text x="380" y="90" font-size="10" fill="#999">45° line (w(p)=p)</text>
<path d="M 70,350 Q 150,220 220,190 Q 300,160 380,110 L 450,70" fill="none" stroke="#1f77b4" stroke-width="2.5" />

<text x="90" y="260" font-size="10" fill="`#1f77b4`">Overweighted (low p)</text>

<text x="290" y="200" font-size="10" fill="`#1f77b4`">Underweighted (mid-high p)</text>

</svg>

### The Certainty Effect and the Allais Paradox

The certainty effect refers to the disproportionate weight given to outcomes that go from probable to certain, relative to comparable improvements at lower probability levels — this directly explains the **Allais Paradox**, a classic violation of expected utility theory's independence axiom:

- Most people prefer a certain payoff over a lottery with a slightly higher expected value but any risk of receiving nothing.
- Yet when a common, small probability of the "nothing" outcome is introduced into *both* options in a modified version of the same choice, preferences often reverse — inconsistent with any expected-utility representation, but consistent with prospect theory's overweighting of the shift from uncertainty to certainty.

### Framing Effects

A **framing effect** occurs when logically equivalent descriptions of a decision problem lead to different choices, violating the *description invariance* assumption of rational choice theory. Framing effects follow directly from prospect theory's reference-dependent value function, since different frames imply different reference points and different gain/loss codings for the same underlying outcomes.

#### The Asian Disease Problem (Classic Illustration)

A hypothetical disease outbreak is expected to kill 600 people. Two equivalent programs are described using different frames:

- **Gain frame**: "Program A saves 200 people for certain; Program B has a 1/3 probability of saving all 600 and a 2/3 probability of saving no one." Most respondents choose the certain option (A), exhibiting **risk aversion** — consistent with a concave value function over gains.
- **Loss frame**: "Program C results in 400 deaths for certain; Program D has a 1/3 probability that no one dies and a 2/3 probability that all 600 die." Most respondents choose the risky option (D), exhibiting **risk-seeking** — consistent with a convex value function over losses.

Programs A and C are outcome-identical to B and D respectively, differing only in whether the same 200-saved/400-dead outcome is framed as a gain or a loss. This reversal of risk attitude based purely on framing is among the most replicated findings in behavioral decision research.

| Frame | Description | Modal Choice | Risk Attitude Revealed |
| --- | --- | --- | --- |
| Gain (lives saved) | 200 saved for certain vs. 1/3 chance all 600 saved | Certain option | Risk-averse |
| Loss (deaths) | 400 die for certain vs. 1/3 chance no one dies | Risky option | Risk-seeking |

#### Other Common Framing Manifestations

- **Attribute framing**: describing the same product attribute in positive vs. negative terms (e.g., "90% fat-free" vs. "10% fat") changes evaluations even though the information is identical.
- **Goal framing**: describing the consequence of an action (or inaction) as either achieving a gain or avoiding a loss changes persuasive impact, even for logically identical outcomes.
- **Temporal/reference framing in pricing**: labeling a price difference as a "surcharge" (a loss relative to a reference price) rather than a "discount" (a gain relative to a higher reference price) changes consumer acceptance, even when the final price is identical.

### Endowment Effect and Loss Aversion in Ownership

A well-documented application of loss aversion is the **endowment effect**: individuals who own a good typically demand a substantially higher price to give it up (willingness to accept, WTA) than they would be willing to pay to acquire the identical good if they did not already own it (willingness to pay, WTP). Standard theory predicts WTA ≈ WTP absent income effects or transaction costs; prospect theory explains the empirically observed gap (WTA > WTP) as a consequence of the reference point shifting to include current ownership, making relinquishment coded as a loss.

### Applications

- **Insurance and lottery demand coexisting**: overweighting of small probabilities explains simultaneous purchase of both insurance (protection against a small-probability large loss) and lottery tickets (chance at a small-probability large gain) by the same individual — a pattern difficult to reconcile with a single consistent risk-aversion parameter under EUT.
- **Marketing and pricing**: strategic framing of discounts as gains, surcharges as losses, and reference-price anchoring to shift the perceived gain/loss coding of a transaction.
- **Public health and policy communication**: framing health messages in terms of losses avoided vs. gains achieved measurably changes behavioral uptake (e.g., screening or vaccination messaging).
- **Retirement and default policy design**: understanding loss aversion and the endowment effect informs default-option design in choice architecture (e.g., automatic enrollment exploits status quo bias, itself linked to loss aversion around the current default).

### Common Pitfalls

- Confusing the probability weighting function $\pi(p)$ with a subjective belief about the *likelihood* of an event — it is a decision weight applied to already-known objective probabilities, not an estimate of probability itself.
- Assuming prospect theory implies universal risk aversion or universal risk-seeking — the model predicts risk aversion over gains but risk-seeking over losses (the "reflection effect"), so the predicted attitude depends on which side of the reference point the outcome falls.
- Treating specific parameter estimates ($\alpha, \beta \approx 0.88$, $\lambda \approx 2.25$) as fixed universal constants rather than estimates specific to a particular study design and population.
- Overlooking that framing effects require an identifiable, often implicit or manipulable, reference point — without specifying the reference point, predictions about gain/loss coding (and thus risk attitude) cannot be made.

### Related Topics

- Consumer choice under risk and uncertainty (expected utility theory baseline)
- Behavioral economics: bounded rationality and heuristics
- Endowment effect and willingness-to-pay/willingness-to-accept gap
- Allais and Ellsberg paradoxes
- Choice architecture and nudge theory
- Mental accounting
- Intertemporal choice and hyperbolic discounting