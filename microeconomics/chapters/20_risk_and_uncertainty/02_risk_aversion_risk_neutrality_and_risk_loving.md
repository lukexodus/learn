## Risk Aversion, Risk Neutrality, and Risk Loving


### Definition and Core Concept

Risk aversion, risk neutrality, and risk loving (risk-seeking) are the three fundamental classifications of an economic agent's attitude toward uncertain outcomes, defined formally through the curvature of the agent's utility function over wealth or outcomes within the expected utility framework. These classifications determine how an agent compares a certain outcome to an uncertain prospect with the same expected value, and they underpin virtually all economic analysis of insurance, portfolio choice, contracting under uncertainty, and gambling behavior.

**Key Points**

- **Risk-averse**: prefers a certain outcome to a risky prospect with the same expected value (concave utility function)
- **Risk-neutral**: indifferent between a certain outcome and a risky prospect with the same expected value (linear utility function)
- **Risk-loving (risk-seeking)**: prefers a risky prospect to a certain outcome with the same expected value (convex utility function)
- These attitudes are formalized precisely via **Jensen's Inequality** applied to the expected utility of a lottery versus the utility of its expected value

### Formal Definitions via Utility Function Curvature

Consider a risky prospect (lottery) $X$ with expected value $E[X]$, and an agent with a von Neumann–Morgenstern utility function $u(\cdot)$ defined over wealth or outcomes. The three risk attitudes are defined by comparing $E[u(X)]$ — the expected utility of the lottery — to $u(E[X])$ — the utility of receiving the expected value with certainty:

| Risk Attitude | Mathematical Condition | Utility Function Curvature | Behavioral Implication |
| --- | --- | --- | --- |
| Risk-averse | $E[u(X)] < u(E[X])$ | Concave: $u''(x) < 0$ | Prefers certain $E[X]$ over the lottery $X$ |
| Risk-neutral | $E[u(X)] = u(E[X])$ | Linear: $u''(x) = 0$ | Indifferent between certain $E[X]$ and the lottery $X$ |
| Risk-loving | $E[u(X)] > u(E[X])$ | Convex: $u''(x) > 0$ | Prefers the lottery $X$ over certain $E[X]$ |

This relationship is a direct application of **Jensen's Inequality**, which states that for a concave function, the expectation of the function is less than or equal to the function of the expectation, with the inequality reversing for a convex function and holding with equality for a linear function.

**(svg_diagram)**

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 460">
<text x="320" y="24" font-size="16" font-weight="bold" text-anchor="middle" fill="#1a1a1a">Three Utility Function Shapes and Risk Attitudes (svg_diagram)</text>
<line x1="60" y1="150" x2="220" y2="150" stroke="#333" stroke-width="1" />
<line x1="60" y1="150" x2="60" y2="60" stroke="#333" stroke-width="1" />
<path d="M 65 145 C 100 100, 150 70, 215 65" stroke="#2980b9" stroke-width="2.5" fill="none" />
<text x="140" y="175" font-size="12" font-weight="bold" text-anchor="middle" fill="#2980b9">Risk-Averse (Concave)</text>
<line x1="260" y1="150" x2="420" y2="150" stroke="#333" stroke-width="1" />
<line x1="260" y1="150" x2="260" y2="60" stroke="#333" stroke-width="1" />
<path d="M 265 145 L 415 65" stroke="#27ae60" stroke-width="2.5" fill="none" />
<text x="340" y="175" font-size="12" font-weight="bold" text-anchor="middle" fill="#27ae60">Risk-Neutral (Linear)</text>
<line x1="460" y1="150" x2="620" y2="150" stroke="#333" stroke-width="1" />
<line x1="460" y1="150" x2="460" y2="60" stroke="#333" stroke-width="1" />
<path d="M 465 145 C 530 140, 580 110, 615 65" stroke="#c0392b" stroke-width="2.5" fill="none" />
<text x="540" y="175" font-size="12" font-weight="bold" text-anchor="middle" fill="#c0392b">Risk-Loving (Convex)</text>
<line x1="60" y1="330" x2="620" y2="330" stroke="#333" stroke-width="1.5" />
<line x1="60" y1="330" x2="60" y2="220" stroke="#333" stroke-width="1.5" />
<text x="30" y="215" font-size="11" fill="#333">u(x)</text>
<path d="M 70 320 C 250 260, 400 225, 600 215" stroke="#2980b9" stroke-width="2.5" fill="none" />
<line x1="100" y1="313" x2="100" y2="380" stroke="#999" stroke-dasharray="3,3" />
<line x1="500" y1="225" x2="500" y2="380" stroke="#999" stroke-dasharray="3,3" />
<line x1="100" y1="380" x2="500" y2="380" stroke="#999" stroke-dasharray="3,3" />
<circle cx="300" cy="380" r="4" fill="#333" />
<text x="300" y="400" font-size="11" text-anchor="middle" fill="#333">E[X]: midpoint of the two outcomes on the x-axis</text>
<line x1="300" y1="380" x2="300" y2="255" stroke="#c0392b" stroke-width="1" stroke-dasharray="3,3" />
<circle cx="300" cy="255" r="4" fill="#c0392b" />
<text x="380" y="250" font-size="11" fill="#c0392b">u(E[X])</text>
<line x1="100" y1="313" x2="500" y2="225" stroke="#e67e22" stroke-width="1" stroke-dasharray="3,3" />
<circle cx="300" cy="269" r="4" fill="#e67e22" />
<text x="310" y="290" font-size="11" fill="#e67e22">E[u(X)]: chord midpoint, below the curve</text>
<text x="70" y="440" font-size="11" fill="#555">Concave curve lies above its chord: u(E[X]) &gt; E[u(X)] — the defining condition for risk aversion</text>
</svg>

### The Certainty Equivalent and Risk Premium

Two central derived concepts quantify risk attitudes in monetary terms:

**Certainty equivalent (CE)**: The certain amount of money that yields the same utility as the expected utility of a given risky prospect:

$$u(CE) = E[u(X)]$$

**Risk premium (RP)**: The gap between the expected value of the lottery and its certainty equivalent:

$$RP = E[X] - CE$$

| Risk Attitude | Certainty Equivalent vs. E[X] | Risk Premium |
| --- | --- | --- |
| Risk-averse | $CE < E[X]$ | $RP > 0$ (positive) |
| Risk-neutral | $CE = E[X]$ | $RP = 0$ |
| Risk-loving | $CE > E[X]$ | $RP < 0$ (negative) |

The risk premium represents, in monetary terms, how much a risk-averse agent is willing to sacrifice, on average, to eliminate uncertainty. A risk-loving agent, by contrast, has a *negative* risk premium — they would need to be *compensated* to give up the risky prospect in favor of its certain expected value, since they derive positive value from the variance itself.

### The Arrow-Pratt Measures of Risk Aversion

Kenneth Arrow and John Pratt independently developed formal measures to quantify the *intensity* of risk aversion, allowing comparison not just of the sign (averse/neutral/loving) but the magnitude of risk aversion across agents or across wealth levels for the same agent.

**Absolute Risk Aversion (ARA)**, also called the **Arrow-Pratt coefficient**:

$$A(x) = -\frac{u''(x)}{u'(x)}$$

This measures risk aversion with respect to gambles of a *fixed dollar amount*, independent of wealth level.

**Relative Risk Aversion (RRA)**:

$$R(x) = -\frac{x \, u''(x)}{u'(x)} = x \cdot A(x)$$

This measures risk aversion with respect to gambles defined as a *proportion of wealth*, which is often considered more relevant for questions like optimal portfolio share allocation regardless of the investor's absolute wealth level.

#### Behavior of ARA and RRA with Respect to Wealth

| Property | Definition | Economic Interpretation |
| --- | --- | --- |
| Decreasing Absolute Risk Aversion (DARA) | $A'(x) < 0$ | Willingness to hold a fixed dollar amount of risky assets increases with wealth |
| Constant Absolute Risk Aversion (CARA) | $A'(x) = 0$ | Willingness to hold a fixed dollar amount of risky assets is independent of wealth |
| Increasing Absolute Risk Aversion (IARA) | $A'(x) > 0$ | Willingness to hold a fixed dollar amount of risky assets decreases with wealth |
| Decreasing Relative Risk Aversion (DRRA) | $R'(x) < 0$ | The proportion of wealth allocated to risky assets increases with wealth |
| Constant Relative Risk Aversion (CRRA) | $R'(x) = 0$ | The proportion of wealth allocated to risky assets is independent of wealth |
| Increasing Relative Risk Aversion (IRRA) | $R'(x) > 0$ | The proportion of wealth allocated to risky assets decreases with wealth |

**[Inference]** DARA is widely regarded in the applied economics literature as the empirically and intuitively most plausible property (wealthier individuals are typically observed and expected to be willing to risk larger absolute dollar amounts), and it is a standard assumption in much of finance and insurance theory. CRRA is also very widely used, particularly in macroeconomics and finance, largely for its tractability in producing scale-invariant, wealth-independent portfolio share predictions, though the degree to which it accurately describes actual risk-taking behavior across different wealth levels remains an active area of empirical inquiry.

### Common Utility Function Specifications

| Utility Function | Formula | Risk Property |
| --- | --- | --- |
| Linear | $u(x) = a + bx$ | Risk-neutral ($A(x) = 0$ for all $x$) |
| Quadratic | $u(x) = x - \frac{b}{2}x^2$ | Risk-averse, but exhibits IARA (a generally viewed as less realistic property) |
| Exponential (CARA) | $u(x) = -e^{-\alpha x}$, $\alpha > 0$ | Constant absolute risk aversion, $A(x) = \alpha$ |
| Power (CRRA) | $u(x) = \frac{x^{1-\gamma}}{1-\gamma}$, $\gamma \neq 1$ | Constant relative risk aversion, $R(x) = \gamma$ |
| Logarithmic | $u(x) = \ln(x)$ | Special case of CRRA with $\gamma = 1$; exhibits DARA |
| Convex power | $u(x) = x^\gamma$, $\gamma > 1$ | Risk-loving |

```mermaid
flowchart TD
    A[Utility Function u(x)] --> B{Second derivative sign}
    B -->|u'' less than 0| C[Concave: Risk-Averse]
    B -->|u'' equals 0| D[Linear: Risk-Neutral]
    B -->|u'' greater than 0| E[Convex: Risk-Loving]
    C --> F[Positive risk premium; buys insurance]
    D --> G[Zero risk premium; maximizes expected value]
    E --> H[Negative risk premium; pays to gamble]
```

### Applications by Risk Attitude

#### Risk Aversion Applications

**Insurance demand**: A risk-averse individual is willing to pay a premium *exceeding* the actuarially fair value of coverage (i.e., exceeding their expected loss) in exchange for eliminating uncertainty, which is the fundamental economic rationale for the existence of the insurance industry. Insurers, typically operating at a larger scale and with diversified risk pools (approaching risk-neutral behavior via the law of large numbers), can profitably offer coverage at a premium below what a risk-averse individual would be willing to pay, while still exceeding the expected payout.

**Example**

A risk-averse homeowner facing a 1% chance of a \$200,000 loss from fire has an expected loss of \$2,000. Because they are risk-averse, they may be willing to pay an insurance premium of, say, \$2,500 — exceeding the actuarially fair value by \$500 — to eliminate the risk of the much larger, uncertain loss, since the utility cost of bearing that risk exceeds the \$500 premium in expected-utility terms. This willingness to pay above the actuarially fair price is precisely the risk premium in monetary form.

**Portfolio diversification**: Risk-averse investors hold diversified portfolios rather than concentrating wealth in a single risky asset, since diversification reduces overall portfolio variance without proportionally reducing expected return (given imperfect correlation across assets) — a direct consequence of risk aversion combined with the statistical properties of a diversified asset pool.

#### Risk Neutrality Applications

**Firm behavior in competitive markets**: Firms, particularly large, diversified, publicly-traded firms with many shareholders holding diversified portfolios, are frequently modeled as risk-neutral with respect to project-level risk, since idiosyncratic project risk can be diversified away at the shareholder-portfolio level, leaving expected value maximization (e.g., net present value maximization) as the appropriate decision criterion.

**Expected-value cost-benefit analysis**: Government policy evaluation and public project appraisal frequently employ risk-neutral, expected-value-based cost-benefit analysis, on the argument that the government, by pooling risks across a very large number of citizens and projects, is well-approximated as risk-neutral even when individual citizens are risk-averse.

#### Risk-Loving (Risk-Seeking) Applications

**Gambling**: Recreational gambling with a negative expected value (as virtually all commercial gambling activities have, by design, given the "house edge") is consistent with risk-loving preferences over that specific class of small-stakes prospects — an individual willing to pay *more* than the actuarially fair price for a chance at a large prize exhibits convex utility (or, alternatively, may be explained by prospect theory's probability weighting function, which overweights small probabilities, rather than by literal risk-loving utility over final wealth).

**Lottery ticket purchases**: Similarly explained via either risk-loving utility in a narrow domain or via prospect-theory-style overweighting of small probabilities, lottery ticket purchases represent a canonical example of apparently risk-seeking behavior for small-probability, large-payout gambles.

**[Inference]** Many economists now favor the prospect-theory probability-weighting explanation over a literal risk-loving utility function specifically for gambling and lottery behavior, since individuals who purchase lottery tickets often simultaneously purchase insurance (a risk-averse behavior) — a combination that is difficult to reconcile with a single, globally convex or globally concave utility function over final wealth, but which is directly and more parsimoniously accommodated by prospect theory's asymmetric treatment of small versus large/moderate probabilities.

### Mixed Risk Attitudes: Friedman-Savage Utility

Milton Friedman and Leonard Savage (1948) proposed a utility function with **both concave and convex segments** specifically to reconcile the simultaneous observation of insurance purchase (risk-averse behavior, typically over losses near current wealth) and gambling/lottery purchase (risk-seeking behavior, typically over the prospect of large wealth gains) within a single expected-utility framework.

**(svg_diagram)**

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 340">
<text x="320" y="24" font-size="16" font-weight="bold" text-anchor="middle" fill="#1a1a1a">Friedman-Savage Utility Function (svg_diagram)</text>
<line x1="70" y1="290" x2="580" y2="290" stroke="#333" stroke-width="1.5" />
<line x1="70" y1="290" x2="70" y2="50" stroke="#333" stroke-width="1.5" />
<text x="580" y="312" font-size="13" text-anchor="end" fill="#333">Wealth (x)</text>
<text x="45" y="45" font-size="12" text-anchor="middle" fill="#333">u(x)</text>
<path d="M 90 270 C 200 180, 280 130, 340 120 C 400 110, 480 140, 560 70" stroke="#8e44ad" stroke-width="2.5" fill="none" />
<text x="130" y="200" font-size="12" fill="#2980b9">Concave region (lower/current wealth)</text>
<text x="130" y="220" font-size="12" fill="#2980b9">→ risk-averse: buys insurance</text>
<text x="380" y="180" font-size="12" fill="#c0392b">Convex region (potential upper wealth)</text>
<text x="400" y="200" font-size="12" fill="#c0392b">→ risk-loving: buys lottery tickets</text>
<line x1="340" y1="290" x2="340" y2="120" stroke="#999" stroke-dasharray="3,3" />
<text x="345" y="310" font-size="11" fill="#555">Inflection point</text>
</svg>

**[Inference]** While the Friedman-Savage utility function successfully accommodates the joint observation of insurance-buying and gambling within an expected-utility framework, it has been criticized on grounds including the somewhat ad hoc placement of the inflection point and specific implications about behavior at intermediate wealth levels that have not always been strongly supported empirically; prospect theory is frequently cited as an alternative, and in some respects more parsimonious, explanation for the same joint behavioral pattern.

### Common Misconceptions

- **Risk aversion means avoiding all risk.** Risk aversion describes a specific mathematical property of preferences over a certain outcome versus a risky prospect of *equal expected value* — a risk-averse agent may still rationally accept risky gambles if the expected value is sufficiently favorable relative to the risk involved (e.g., positive-expected-value investments).
- **All individuals are risk-averse in all domains.** The Friedman-Savage framework and subsequent behavioral evidence (including prospect theory's reflection effect, where the same individual is risk-averse for gains but risk-seeking for losses) demonstrate that a single individual's risk attitude can vary systematically across domains, wealth levels, and even the framing of the decision.
- **Risk-neutral and risk-loving agents behave identically.** They are distinct: a risk-neutral agent is indifferent between a certain amount and a lottery of equal expected value, while a risk-loving agent strictly prefers the lottery and would require compensation to accept the certain amount instead.

### Related Topics

- Expected utility theory and the von Neumann–Morgenstern axioms
- Arrow-Pratt measures of absolute and relative risk aversion
- Insurance demand and the economics of risk pooling
- Prospect theory as an alternative account of mixed gambling/insurance behavior
- Friedman-Savage utility and the coexistence of gambling and insurance
- Portfolio theory and optimal risk-asset allocation
- Diversification and the reduction of idiosyncratic risk
- Probability weighting functions and their role in gambling behavior