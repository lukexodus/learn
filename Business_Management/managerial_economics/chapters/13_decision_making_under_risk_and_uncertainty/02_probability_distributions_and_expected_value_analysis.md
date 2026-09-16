## Probability Distributions and Expected Value Analysis


### Definition and Core Concept

A **probability distribution** specifies, for a random variable representing the possible outcomes of an uncertain event, either the probability of each individual outcome (for a **discrete** random variable) or the density of probability across a continuous range of outcomes (for a **continuous** random variable). **Expected value analysis** uses this distribution to compute a single summary measure — the probability-weighted average of all possible outcomes — which serves as the central decision-making criterion under conditions of measurable risk, as distinguished from true uncertainty.

- Expected value analysis presumes the decision-maker is operating under **risk** rather than **Knightian uncertainty** — that is, the set of possible outcomes and their associated probabilities are known or can be reliably estimated
- This framework underlies a large share of formal quantitative decision-making tools used in managerial economics, including decision trees, capital budgeting under risk, and expected utility theory

### Discrete Probability Distributions

For a discrete random variable $X$ that can take values $x_1, x_2, \dots, x_n$ with associated probabilities $p_1, p_2, \dots, p_n$, a valid probability distribution requires:

$$\sum_{i=1}^{n} p_i = 1, \quad \text{and} \quad 0 \le p_i \le 1 \text{ for all } i$$

**Example:** A firm evaluating a new product launch might assign a discrete probability distribution over three demand scenarios:

| Scenario | Probability | Profit Outcome |
| --- | --- | --- |
| High demand | 0.30 | $500,000 |
| Moderate demand | 0.50 | $200,000 |
| Low demand | 0.20 | -$100,000 |

Note that $0.30 + 0.50 + 0.20 = 1$, satisfying the requirement for a valid discrete probability distribution.

### Expected Value: Formula and Calculation

The **expected value** (or expected monetary value, EMV) of a discrete random variable is:

$$E(X) = \sum_{i=1}^{n} p_i x_i$$

Applying this to the product-launch example above:

$$E(\text{Profit}) = (0.30)(500{,}000) + (0.50)(200{,}000) + (0.20)(-100{,}000)$$



$$E(\text{Profit}) = 150{,}000 + 100{,}000 - 20{,}000 = \$230{,}000$$

**Key Points**

- Expected value represents the **long-run average outcome** if the same probabilistic situation were repeated a very large number of times — it is a statistical average, not a guarantee of the actual outcome in any single instance
- A decision-maker using the **expected value criterion** (also called the Bayes criterion in some decision-theory contexts) selects the action with the highest expected value among available alternatives, implicitly treating a dollar of expected gain as equally desirable regardless of the variability/riskiness of the distribution that produces it

### Continuous Probability Distributions

When outcomes can take any value within a continuous range rather than a small discrete set (e.g., an uncertain future price, demand level, or return on investment measured on a continuous scale), a **probability density function (PDF)**, $f(x)$, is used instead of a list of discrete probabilities. The expected value of a continuous random variable is:

$$E(X) = \int_{-\infty}^{\infty} x \, f(x) \, dx$$

- The most commonly applied continuous distribution in managerial and financial decision-making is the **normal distribution**, characterized fully by its mean $\mu$ and standard deviation $\sigma$, due to its mathematical tractability and its frequent (though not universal) applicability as an approximation for aggregated or averaged real-world quantities, per the Central Limit Theorem
- **Example:** A firm might model uncertain annual sales revenue as approximately normally distributed with mean $\mu = \$2{,}000{,}000$ and standard deviation $\sigma = \$300{,}000$, allowing it to compute not just the expected value ($\$2{,}000{,}000$) but also probabilities of falling within various ranges around that mean using standard normal distribution tables or software

### Variance and Standard Deviation as Measures of Risk

**Key Points**

- Expected value alone does not capture the **dispersion** or **riskiness** of a distribution — two very different distributions can share the same expected value while differing substantially in how spread out their possible outcomes are
- **Variance** measures the average squared deviation of outcomes from the expected value:

$$\text{Var}(X) = \sum_{i=1}^{n} p_i (x_i - E(X))^2$$

- **Standard deviation** is the square root of variance, expressed in the same units as the original variable (unlike variance, which is in squared units), making it more directly interpretable as a measure of typical deviation from the expected value:

$$\sigma = \sqrt{\text{Var}(X)}$$

**Numeric illustration continuing the product-launch example:**

$$\text{Var}(\text{Profit}) = 0.30(500{,}000 - 230{,}000)^2 + 0.50(200{,}000 - 230{,}000)^2 + 0.20(-100{,}000 - 230{,}000)^2$$



$$= 0.30(270{,}000)^2 + 0.50(-30{,}000)^2 + 0.20(-330{,}000)^2$$



$$= 0.30(72{,}900{,}000{,}000) + 0.50(900{,}000{,}000) + 0.20(108{,}900{,}000{,}000)$$



$$= 21{,}870{,}000{,}000 + 450{,}000{,}000 + 21{,}780{,}000{,}000 = 44{,}100{,}000{,}000$$



$$\sigma = \sqrt{44{,}100{,}000{,}000} \approx \$210{,}000$$

This standard deviation of approximately $210,000, relative to an expected value of $230,000, indicates substantial dispersion around the expected outcome — information that a decision-maker relying solely on expected value would miss entirely.

### Diagrammatic Representation

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 420" font-family="Arial, sans-serif">
<text x="400" y="24" text-anchor="middle" font-size="16" font-weight="bold">Expected Value and Dispersion: Two Distributions Compared (svg_diagram)</text>
<line x1="80" y1="360" x2="720" y2="360" stroke="black" stroke-width="1.5" />
<line x1="80" y1="360" x2="80" y2="60" stroke="black" stroke-width="1.5" />
<text x="30" y="65" font-size="12">Probability density</text>
<text x="680" y="378" font-size="12">Outcome value</text>

<path d="M 300 360 Q 350 100 400 100 Q 450 100 500 360" fill="#2563eb" fill-opacity="0.15" stroke="#2563eb" stroke-width="2" />
<text x="380" y="90" font-size="11" fill="#2563eb">Low-variance distribution</text>

<path d="M 150 360 Q 250 220 400 220 Q 550 220 650 360" fill="#dc2626" fill-opacity="0.12" stroke="#dc2626" stroke-width="2" />
<text x="500" y="210" font-size="11" fill="#dc2626">High-variance distribution</text>

<line x1="400" y1="360" x2="400" y2="90" stroke="black" stroke-width="1" stroke-dasharray="4,2" />
<text x="405" y="80" font-size="11">Same E(X) for both</text>

<text x="400" y="405" text-anchor="middle" font-size="11" font-style="italic">Both distributions share the same expected value but differ substantially in dispersion (risk)</text>

</svg>

### Coefficient of Variation

To compare risk across distributions with **different** expected values (where standard deviation alone is not directly comparable), the **coefficient of variation (CV)** normalizes standard deviation by the mean:

$$CV = \frac{\sigma}{E(X)}$$

**Example:** Comparing two investment options — Option A with $E(X) = \$100{,}000$ and $\sigma = \$20{,}000$ (CV = 0.20), versus Option B with $E(X) = \$500{,}000$ and $\sigma = \$80{,}000$ (CV = 0.16) — shows that Option B, despite having a much larger absolute standard deviation, is actually *relatively* less risky per dollar of expected return than Option A, a distinction that comparing raw standard deviations alone would obscure.

### Expected Value as a Decision Criterion: Strengths and Limitations

**Key Points**

- **Strength:** Expected value provides a single, tractable, and additive summary statistic that allows straightforward ranking of alternatives and is consistent with long-run average outcomes across many repeated similar decisions
- **Limitation — ignores risk attitude:** Pure expected value maximization treats a decision-maker as **risk-neutral**, ignoring the well-documented reality that most individuals and firms exhibit **risk aversion** (a preference for a certain outcome over an uncertain outcome with the same expected value) in many contexts, particularly for large stakes relative to available resources — this limitation motivates the use of **expected utility theory** rather than raw expected monetary value in many applications, covered as a related topic
- **Limitation — single-instance decisions:** Expected value's justification rests on a long-run, repeated-trials interpretation; for a genuinely one-off, high-stakes decision that will not be repeated many times, the "long-run average" interpretation is less directly applicable, and the specific realized outcome (rather than the average across hypothetical repetitions) is what actually occurs [Inference]
- **Limitation — requires valid probability estimates:** As distinguished under the risk-versus-uncertainty framework, expected value analysis presumes that the underlying probability distribution is reasonably reliable; applying it to situations of genuine Knightian uncertainty, where the probability inputs are essentially fabricated guesses, risks producing a misleadingly precise-looking number that does not reflect genuine confidence in the underlying estimate

### Common Probability Distributions Used in Managerial Applications

| Distribution | Type | Typical Managerial Application |
| --- | --- | --- |
| Binomial | Discrete | Modeling a fixed number of independent yes/no trials (e.g., number of defective units in a batch) |
| Poisson | Discrete | Modeling the number of rare events in a fixed interval (e.g., customer arrivals, equipment failures) |
| Normal | Continuous | Modeling aggregated/averaged continuous quantities (e.g., sales revenue, investment returns) |
| Uniform | Continuous or discrete | Modeling outcomes with no reason to expect any value more likely than another within a range |
| Triangular | Continuous | Modeling expert-judgment estimates using a minimum, most-likely, and maximum value, common in project risk analysis |

[Inference] The appropriateness of any specific distributional assumption for a real managerial forecasting problem depends on the underlying data-generating process and should generally be checked against available historical data or domain expertise rather than assumed by default.

### Practical Application in Decision Trees and Capital Budgeting

Expected value analysis forms the computational core of **decision tree analysis** (folding back a tree by computing expected value at each chance node) and **expected net present value (ENPV)** calculations in capital budgeting under risk, where cash flows in future periods are treated as random variables with estimated probability distributions rather than known certain values. These applications are addressed in greater depth as related, more specialized topics within this chapter.

### Common Pitfalls and Practical Limitations

- **Overreliance on point estimates:** Reporting only the expected value without also reporting variance/standard deviation or the full distribution can mislead decision-makers into underestimating the actual risk involved in a decision
- **Garbage-in, garbage-out risk:** Expected value calculations are only as reliable as the underlying probability estimates; poorly justified or overly precise-seeming probability inputs can produce a false sense of analytical rigor [Inference]
- **Ignoring correlation across outcomes:** In multi-period or multi-variable analyses, treating outcomes as independent when they are actually correlated (e.g., assuming next year's demand is independent of this year's demand) can produce systematically biased expected value and variance estimates
- **Conflating expected value with the most likely outcome:** In skewed distributions, the expected value can differ substantially from the mode (most probable single outcome) or median, and decision-makers sometimes mistakenly treat the expected value as "what will most likely happen" rather than as a probability-weighted average

### Related Topics

- Distinguishing risk from uncertainty
- Expected utility theory and risk attitudes (risk aversion, risk neutrality, risk-seeking)
- Decision trees and sequential decision-making under risk
- Decision criteria under uncertainty (maximin, maximax, minimax regret)
- Capital budgeting and net present value under risk
- Sensitivity analysis and Monte Carlo simulation