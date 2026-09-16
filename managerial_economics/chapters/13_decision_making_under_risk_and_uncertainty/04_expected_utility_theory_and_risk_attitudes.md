## Expected Utility Theory and Risk Attitudes


### Definition and Core Concept

**Expected utility theory** provides a decision-making framework for choices under risk that improves upon raw expected monetary value analysis by evaluating outcomes in terms of a decision-maker's **utility** — a measure of subjective satisfaction or desirability — rather than in terms of dollar amounts directly. The theory allows the decision framework to account for **risk attitudes**: the systematic ways in which individuals and firms may value a certain amount of money differently from an uncertain prospect with the same expected monetary value.

- Developed formally by John von Neumann and Oskar Morgenstern, expected utility theory replaces the expected value criterion, $EV(X) = \sum p_i x_i$, with the expected utility criterion, $EU(X) = \sum p_i \, U(x_i)$, where $U(\cdot)$ is a **utility function** mapping monetary outcomes to a measure of subjective value
- This distinction matters because most individuals and firms do not evaluate uncertain prospects purely by their expected dollar value — a phenomenon most starkly illustrated by the near-universal preference for a certain $1,000 over a 50/50 gamble between $0 and $2,000, despite both having the same $1,000 expected value

### The Three Classic Risk Attitudes

**Key Points**

Risk attitude is formally characterized by the **curvature** of an individual's or firm's utility function over money:

- **Risk-averse:** The utility function is **concave** ($U''(x) < 0$), meaning marginal utility of money decreases as wealth increases. A risk-averse decision-maker prefers a certain outcome to an uncertain prospect with the same expected value, and will only accept a risky prospect if it offers a *higher* expected value than the certain alternative to compensate for the risk
- **Risk-neutral:** The utility function is **linear** ($U''(x) = 0$), meaning marginal utility of money is constant. A risk-neutral decision-maker is indifferent between a certain outcome and an uncertain prospect with the same expected value, and thus evaluates decisions purely by comparing raw expected monetary values — this is the implicit assumption underlying basic expected value analysis and standard decision tree fold-back procedures
- **Risk-seeking (risk-loving):** The utility function is **convex** ($U''(x) > 0$), meaning marginal utility of money increases as wealth increases. A risk-seeking decision-maker prefers an uncertain prospect over a certain outcome with the same expected value

### Graphical Representation of Utility Functions

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 420" font-family="Arial, sans-serif">
<text x="400" y="24" text-anchor="middle" font-size="16" font-weight="bold">Utility Function Shapes and Risk Attitudes (svg_diagram)</text>
<line x1="80" y1="360" x2="720" y2="360" stroke="black" stroke-width="1.5" />
<line x1="80" y1="360" x2="80" y2="60" stroke="black" stroke-width="1.5" />
<text x="30" y="65" font-size="12">Utility U(x)</text>
<text x="680" y="378" font-size="12">Wealth / Money (x)</text>

<path d="M 100 340 Q 300 120 700 90" fill="none" stroke="#2563eb" stroke-width="2.5" />
<text x="500" y="105" font-size="11" fill="#2563eb">Risk-averse (concave)</text>

<line x1="100" y1="340" x2="700" y2="120" stroke="#16a34a" stroke-width="2.5" />
<text x="500" y="220" font-size="11" fill="#16a34a">Risk-neutral (linear)</text>

<path d="M 100 340 Q 400 330 700 150" fill="none" stroke="#dc2626" stroke-width="2.5" />
<text x="500" y="340" font-size="11" fill="#dc2626">Risk-seeking (convex)</text>

<text x="400" y="405" text-anchor="middle" font-size="11" font-style="italic">Curvature of U(x) determines whether a certain amount is preferred to a fair gamble with equal expected value</text>

</svg>

### Formal Illustration: Risk Aversion and Jensen's Inequality

For a risk-averse decision-maker with a concave utility function, **Jensen's Inequality** formally establishes that the utility of the expected value exceeds the expected value of the utility for any genuinely uncertain prospect:

$$U(E[X]) > E[U(X)]$$

**Numeric example:** Suppose a decision-maker has utility function $U(x) = \sqrt{x}$ (a standard concave, risk-averse function) and faces a 50/50 gamble between $0 and $10,000.

$$E[X] = 0.5(0) + 0.5(10{,}000) = \$5{,}000$$



$$U(E[X]) = \sqrt{5{,}000} \approx 70.71$$



$$E[U(X)] = 0.5\sqrt{0} + 0.5\sqrt{10{,}000} = 0.5(0) + 0.5(100) = 50$$

Since $U(E[X]) = 70.71 > E[U(X)] = 50$, this decision-maker strictly prefers receiving the expected value of $5,000 with certainty over facing the actual 50/50 gamble, confirming risk-averse behavior.

### Certainty Equivalent and the Risk Premium

**Key Points**

- The **certainty equivalent (CE)** of an uncertain prospect is the certain, guaranteed amount of money that provides the decision-maker with the same utility as the uncertain prospect itself — formally, the value $CE$ such that $U(CE) = E[U(X)]$
- Continuing the numeric example: since $E[U(X)] = 50$, the certainty equivalent solves $\sqrt{CE} = 50 \Rightarrow CE = 2{,}500$. This risk-averse decision-maker values the 50/50 gamble between $0 and $10,000 (with an expected value of $5,000) as being worth only $2,500 for certain
- The **risk premium** is the difference between the expected value of the uncertain prospect and its certainty equivalent:

$$\text{Risk Premium} = E[X] - CE$$

In the example: $\text{Risk Premium} = 5{,}000 - 2{,}500 = \$2{,}500$. This represents the amount of expected value the decision-maker is willing to sacrifice in order to avoid bearing the risk of the gamble — a direct, quantifiable measure of the cost of risk aversion for this specific individual and this specific prospect.

### Common Utility Function Forms Used in Practice

| Utility Function | Form | Risk Attitude | Notes |
| --- | --- | --- | --- |
| Linear | $U(x) = a + bx$ | Risk-neutral | Equivalent to using raw expected monetary value |
| Square root / power | $U(x) = x^{\alpha}, \, 0 < \alpha < 1$ | Risk-averse | Commonly used illustrative form; degree of concavity governed by $\alpha$ |
| Logarithmic | $U(x) = \ln(x)$ | Risk-averse | Historically significant (used in the resolution of the St. Petersburg Paradox); implies constant relative risk aversion |
| Exponential | $U(x) = 1 - e^{-\theta x}$ | Risk-averse (for $\theta > 0$) | Implies constant absolute risk aversion, a property with specific analytical convenience in some financial models |
| Quadratic | $U(x) = x - bx^2$ | Risk-averse (over relevant range) | Historically used in early portfolio theory, though it implies eventually decreasing marginal utility of wealth becoming negative at high $x$, a recognized limitation |

[Inference] The choice of a specific functional form for a real decision-maker's utility function is an empirical and often subjective modeling choice; there is no single universally "correct" utility function for a given individual or firm, and different functional forms can produce different quantitative (though often qualitatively similar) risk-aversion implications.

### Measuring the Degree of Risk Aversion: Arrow-Pratt Coefficients

**Key Points**

Beyond simply classifying a decision-maker as risk-averse, risk-neutral, or risk-seeking, economists use the **Arrow-Pratt measures** to quantify the *degree* of risk aversion implied by a specific utility function:

- **Absolute risk aversion:** $A(x) = -\dfrac{U''(x)}{U'(x)}$ — measures risk aversion with respect to the absolute dollar size of a gamble, independent of the decision-maker's overall wealth level
- **Relative risk aversion:** $R(x) = -x \cdot \dfrac{U''(x)}{U'(x)}$ — measures risk aversion with respect to the size of a gamble expressed as a proportion of the decision-maker's wealth

These measures allow economists to characterize how risk aversion might change as wealth changes — for example, **decreasing absolute risk aversion** (a common empirical finding/assumption) implies that wealthier individuals are willing to risk a larger absolute dollar amount on a given gamble than poorer individuals, even if the *proportional* willingness to risk wealth remains stable or follows a different pattern. [Inference] Whether a specific individual's or firm's actual risk aversion is better characterized as constant, increasing, or decreasing in wealth is an empirical question that varies across studies, contexts, and the specific population being examined, rather than a settled universal constant.

### Application to Managerial and Firm Decision-Making

**Key Points**

- **Firms versus individuals:** A common simplifying assumption in some corporate finance and managerial economics contexts is that large, diversified, publicly-traded firms should behave approximately **risk-neutrally** with respect to project-level risks (since shareholders can diversify firm-specific risk across their own portfolios), even though individual managers within the firm, or owners of small/closely-held businesses without diversification opportunities, often exhibit genuine risk aversion. [Inference] This risk-neutral-firm assumption is a standard theoretical simplification frequently used in corporate finance pedagogy and models, but the extent to which it holds precisely for any specific real firm's actual decision-making behavior is a separate empirical question
- **Insurance and risk transfer:** Expected utility theory provides the formal justification for why risk-averse individuals and firms are willing to pay an insurance premium that exceeds the actuarially fair expected value of a loss — the premium reflects the risk premium the insured party is willing to pay to convert an uncertain large loss into a certain, smaller, predictable cost
- **Capital budgeting adjustments:** Risk-averse firms (or firms accounting for risk-averse stakeholders) may apply a risk-adjusted discount rate or use certainty-equivalent cash flow adjustments in net present value calculations, rather than relying on raw expected cash flows discounted at a risk-free rate, to appropriately price in the cost of bearing project risk

### Limitations and Critiques of Expected Utility Theory

**Key Points**

- **Empirical violations:** Behavioral economics research has documented systematic, replicable violations of expected utility theory's axioms in actual human decision-making — most famously illustrated by the **Allais Paradox**, in which many individuals' choices between certain sets of gambles violate the theory's independence axiom, revealing that real decision-making does not always conform to the theory's normative predictions
- **Reference dependence:** **Prospect theory**, developed as a descriptive alternative, proposes that decision-makers evaluate outcomes relative to a reference point (gains and losses) rather than in terms of final wealth levels, and that they exhibit loss aversion (weighting losses more heavily than equivalent gains) — findings that expected utility theory in its classical form does not capture
- **Normative versus descriptive role:** Expected utility theory is generally understood as a strong **normative** framework (describing how a fully rational decision-maker *should* choose to satisfy certain consistency axioms) more than a perfectly accurate **descriptive** model of how real individuals and firms actually behave in all circumstances; this distinction is important for correctly interpreting the theory's role and limitations in applied managerial contexts [Inference]

### Common Pitfalls and Practical Limitations

- **Assuming risk neutrality by default:** Many introductory expected-value calculations implicitly assume risk neutrality; applying such calculations uncritically to decisions involving individuals or firms with genuine, significant risk aversion (particularly for large stakes relative to their resources) can produce recommendations inconsistent with the actual decision-maker's true preferences
- **Difficulty eliciting an accurate utility function:** Constructing an individual's or firm's actual utility function in practice typically requires eliciting a series of hypothetical choices or certainty equivalents, a process that can be time-consuming, sensitive to elicitation method, and subject to the same behavioral biases (e.g., framing effects) that expected utility theory itself does not fully capture [Inference]
- **Confusing risk aversion with loss aversion:** Risk aversion (concavity of the utility function over final wealth outcomes) and loss aversion (an asymmetric sensitivity to losses versus gains relative to a reference point, per prospect theory) are related but formally distinct concepts, and conflating them can lead to conceptual errors in applying either framework correctly

### Related Topics

- Probability distributions and expected value analysis
- Decision trees for sequential decision problems
- Distinguishing risk from uncertainty
- Prospect theory and behavioral decision-making
- Insurance, hedging, and diversification as risk management tools
- Risk-adjusted discount rates in capital budgeting