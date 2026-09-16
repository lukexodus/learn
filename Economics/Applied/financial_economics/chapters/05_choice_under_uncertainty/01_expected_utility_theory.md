## Expected Utility Theory


### Overview

Expected utility theory (EUT) is the foundational framework for modeling decision-making under uncertainty in financial economics. Developed axiomatically by von Neumann and Morgenstern (1944) and extended by Savage (1954) to subjective probability, EUT posits that rational agents facing risky choices maximize the expected value of a utility function defined over outcomes, rather than the expected value of the outcomes themselves. This distinction — between expected value and expected utility — resolves the St. Petersburg Paradox and underlies virtually all of modern asset pricing, portfolio theory, and risk management, from CAPM's mean-variance foundations to the stochastic discount factor approach in dynamic asset pricing.

### Historical Motivation: The St. Petersburg Paradox

Daniel Bernoulli's 1738 resolution of Nicolaus Bernoulli's St. Petersburg Paradox is the conceptual origin of EUT. Consider a game: a fair coin is flipped until it lands heads; the payoff is $2^n$ where $n$ is the number of flips. The expected monetary value is:

$$E[X] = \sum_{n=1}^{\infty} \frac{1}{2^n} \cdot 2^n = \sum_{n=1}^{\infty} 1 = \infty$$

Yet virtually no one would pay a large finite sum to play. Bernoulli's resolution: individuals maximize expected *utility* of wealth, not expected wealth, and utility exhibits diminishing marginal value (Bernoulli proposed $u(w) = \ln(w)$). Under logarithmic utility, the expected utility of the game is finite, resolving the paradox and establishing the core intuition of risk aversion two centuries before formal axiomatization.

### The von Neumann-Morgenstern (vNM) Axioms

EUT is derived from a small set of axioms on preferences over *lotteries* (probability distributions over outcomes), not imposed as an assumption about utility functions directly. Let $\succsim$ denote a preference relation over the set of lotteries $\mathcal{L}$.

#### Axiom 1 — Completeness

For any two lotteries $L_1, L_2 \in \mathcal{L}$, either $L_1 \succsim L_2$, $L_2 \succsim L_1$, or both (indifference). The agent can always rank any pair of lotteries.

#### Axiom 2 — Transitivity

If $L_1 \succsim L_2$ and $L_2 \succsim L_3$, then $L_1 \succsim L_3$. Preferences are internally consistent.

#### Axiom 3 — Continuity

If $L_1 \succsim L_2 \succsim L_3$, there exists some $\alpha \in [0,1]$ such that the agent is indifferent between $L_2$ and the compound lottery $\alpha L_1 + (1-\alpha) L_3$. Informally, no outcome is infinitely better or worse than another — extreme outcomes can always be "diluted" with probability to match an intermediate one.

#### Axiom 4 — Independence (the crucial, most economically substantive axiom)

For any lotteries $L_1, L_2, L_3$ and any $\alpha \in (0,1]$:

$$L_1 \succsim L_2 \iff \alpha L_1 + (1-\alpha)L_3 \succsim \alpha L_2 + (1-\alpha)L_3$$

Mixing two lotteries with a third, irrelevant lottery in identical proportions does not reverse their ranking. This axiom is what forces utility to be *linear in probabilities* and is the primary target of empirical violations (Allais Paradox, below).

#### The Representation Theorem

**Theorem.** If preferences $\succsim$ over lotteries satisfy Completeness, Transitivity, Continuity, and Independence, then there exists a function $u: X \to \mathbb{R}$ (defined over sure outcomes $X$) such that for any two lotteries $L_1, L_2$:

$$L_1 \succsim L_2 \iff \sum_{x \in X} p_1(x)u(x) \geq \sum_{x \in X} p_2(x)u(x)$$

i.e., preferences can be represented by the *expectation* of a utility function $u$, and this $u$ is unique up to positive affine transformation ($u^*(x) = a + bu(x)$, $b>0$, represents the identical preferences).

**Key Points**

- The theorem does not derive $u$ from introspection about "how much someone likes money" — it derives the *existence* of such a representation purely from consistency axioms on observable choice behavior
- Uniqueness up to positive affine transformation means only the *ordinal ranking of utility differences* is meaningful, not the level of utility or interpersonal utility comparisons
- The theorem is a representation result, not a psychological claim: agents need not consciously compute expected utilities, only behave *as if* they do

### Risk Aversion and Utility Function Curvature

#### Definitions via Certainty Equivalents

For a lottery $\tilde{w}$ with $E[\tilde{w}] = \bar{w}$, define the certainty equivalent $CE$ as the sure amount satisfying $u(CE) = E[u(\tilde{w})]$, and the risk premium $\pi = \bar{w} - CE$.

- **Risk averse**: $u$ concave ($u'' < 0$); by Jensen's inequality, $E[u(\tilde{w})] < u(E[\tilde{w}])$, so $CE < \bar{w}$ and $\pi > 0$
- **Risk neutral**: $u$ linear; $CE = \bar{w}$, $\pi = 0$
- **Risk seeking**: $u$ convex ($u'' > 0$); $CE > \bar{w}$, $\pi < 0$

#### Arrow-Pratt Risk Aversion Measures

**Absolute risk aversion:**

$$A(w) = -\frac{u''(w)}{u'(w)}$$

Measures aversion to risking a fixed dollar amount, as a function of wealth level $w$.

**Relative risk aversion:**

$$R(w) = -\frac{w \, u''(w)}{u'(w)} = w \cdot A(w)$$

Measures aversion to risking a *proportion* of wealth.

For small risks, the risk premium can be approximated via Taylor expansion (Pratt 1964):

$$\pi \approx \frac{1}{2} A(\bar{w}) \sigma^2$$

where $\sigma^2$ is the variance of the lottery — this is the theoretical bridge connecting expected utility to mean-variance analysis for small or approximately normal risks.

**Behavioral classifications:**

| Property | Definition | Implication |
| --- | --- | --- |
| DARA | $A'(w) < 0$ | Wealthier agents take on more absolute risk (dollar amount in risky assets rises with wealth) |
| CARA | $A'(w) = 0$ | Dollar amount held in risky assets is independent of wealth |
| IARA | $A'(w) > 0$ | Wealthier agents take on less absolute risk (empirically rejected as a general property) |
| DRRA / CRRA / IRRA | Analogous for $R(w)$ | CRRA implies portfolio *shares* (not dollar amounts) are wealth-independent |

Most empirical work assumes DARA and CRRA jointly, consistent with observed household portfolio behavior.

### Common Utility Function Families

**CARA (exponential):**

$$u(w) = -e^{-\gamma w}, \quad \gamma > 0 \implies A(w) = \gamma \text{ (constant)}$$

Analytically convenient — pairs with normally distributed returns to produce closed-form portfolio solutions (mean-variance equivalence under normality) — but implies implausible constant absolute dollar risk-taking regardless of wealth.

**CRRA (power/isoelastic):**

$$u(w) = \frac{w^{1-\gamma}}{1-\gamma}, \quad \gamma > 0, \gamma \neq 1; \quad u(w) = \ln(w) \text{ if } \gamma = 1$$



$$R(w) = \gamma \text{ (constant)}$$

The dominant workhorse in macro-finance and asset pricing (consumption-based CAPM, Lucas tree models) because CRRA is consistent with balanced growth — portfolio shares stay constant as the economy grows.

**Quadratic:**

$$u(w) = w - \frac{b}{2}w^2$$

Generates mean-variance preferences exactly (not just as an approximation) for any return distribution, which is why quadratic utility historically justified Markowitz mean-variance optimization directly. Major drawback: exhibits *increasing* absolute risk aversion and satiation (marginal utility eventually turns negative), both empirically implausible.

**HARA (Hyperbolic Absolute Risk Aversion)**: the general class nesting CARA, CRRA, and quadratic utility as special cases, with linear risk tolerance $1/A(w) = a + bw$.

### Expected Utility Maximization: The Portfolio Choice Problem

**Example**

An investor with CRRA utility $u(w) = \frac{w^{1-\gamma}}{1-\gamma}$ allocates wealth $w_0$ between a risk-free asset (return $r_f$) and a risky asset (return $\tilde{r}$, with $E[\tilde{r}] > r_f$). Let $\alpha$ be the fraction in the risky asset. Terminal wealth:

$$\tilde{w} = w_0[(1-\alpha)(1+r_f) + \alpha(1+\tilde{r})] = w_0[(1+r_f) + \alpha(\tilde{r} - r_f)]$$

The investor solves:

$$\max_\alpha E\left[\frac{\tilde{w}^{1-\gamma}}{1-\gamma}\right]$$

First-order condition:

$$E\left[\tilde{w}^{-\gamma}(\tilde{r} - r_f)\right] = 0$$

This is the Euler equation underlying consumption-based asset pricing: the marginal utility-weighted expected excess return must be zero at the optimum. For small risk premia and approximately normal or lognormal returns, this yields the approximate closed-form:

$$\alpha^* \approx \frac{E[\tilde{r}] - r_f}{\gamma \sigma^2}$$

— the classic mean-variance portfolio share, decreasing in risk aversion $\gamma$ and return variance $\sigma^2$, increasing in the equity premium. [Inference — this closed form is an approximation valid under normality or via second-order Taylor expansion of expected utility, not an exact solution for general CRRA with general return distributions]

### Diagram: Utility, Certainty Equivalent, and Risk Premium (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 420">
<text x="350" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#111">Concave Utility and Risk Premium (svg_diagram)</text>
<line x1="70" y1="360" x2="650" y2="360" stroke="#333" stroke-width="1.5" />
<line x1="70" y1="360" x2="70" y2="50" stroke="#333" stroke-width="1.5" />
<text x="660" y="365" font-size="12" fill="#333">Wealth (w)</text>
<text x="45" y="45" font-size="12" fill="#333">u(w)</text>
<path d="M 90 340 Q 250 120 620 70" fill="none" stroke="#3b5bdb" stroke-width="2.5" />
<text x="480" y="100" font-size="12" fill="#3b5bdb">u(w) concave</text>
<line x1="180" y1="360" x2="180" y2="270" stroke="#888" stroke-width="1" stroke-dasharray="4" />
<circle cx="180" cy="270" r="3" fill="#e8590c" />
<text x="150" y="378" font-size="11" fill="#333">w_low</text>
<line x1="480" y1="360" x2="480" y2="90" stroke="#888" stroke-width="1" stroke-dasharray="4" />
<circle cx="480" cy="90" r="3" fill="#e8590c" />
<text x="460" y="378" font-size="11" fill="#333">w_high</text>
<line x1="330" y1="360" x2="330" y2="185" stroke="#888" stroke-width="1" stroke-dasharray="4" />
<circle cx="330" cy="185" r="4" fill="#0ca678" />
<text x="300" y="378" font-size="11" fill="#333">E[w]</text>
<text x="335" y="180" font-size="11" fill="#0ca678">E[u(w)] chord midpoint</text>
<line x1="70" y1="185" x2="330" y2="185" stroke="#0ca678" stroke-width="1" stroke-dasharray="3" />
<line x1="180" y1="270" x2="480" y2="90" stroke="#e8590c" stroke-width="1.5" stroke-dasharray="2" />
<circle cx="260" cy="223" r="4" fill="#d6336c" />
<line x1="260" y1="360" x2="260" y2="223" stroke="#d6336c" stroke-width="1" stroke-dasharray="4" />
<text x="200" y="378" font-size="11" fill="#d6336c">CE</text>
<text x="270" y="218" font-size="11" fill="#d6336c">u(CE) = E[u(w)]</text>
<line x1="260" y1="185" x2="330" y2="185" stroke="#000" stroke-width="2" />
<text x="255" y="150" font-size="11" font-weight="bold" fill="#000">risk premium (pi = E[w] - CE)</text>
</svg>

### Empirical Violations of Expected Utility Theory

Despite its axiomatic elegance, EUT is systematically violated in laboratory and field settings, motivating an extensive behavioral finance literature.

#### The Allais Paradox

Allais (1953) constructed choice pairs violating the Independence axiom directly.

**Problem 1**: Choose between

- $A$: $1M with certainty
- $B$: $1M with probability 0.89, $5M with probability 0.10, $0 with probability 0.01

**Problem 2**: Choose between

- $C$: $1M with probability 0.11, $0 with probability 0.89
- $D$: $5M with probability 0.10, $0 with probability 0.90

Most subjects choose $A$ over $B$ (certainty is heavily preferred) but $D$ over $C$. This pattern is *inconsistent* with any expected utility representation: choosing $A \succ B$ implies (via Independence, subtracting the common 0.89 probability weight on $1M/$0) that $C \succ D$ should hold too, but observed choices reverse this. This "common consequence effect" or "certainty effect" was among the first systematic empirical refutations of EUT.

#### The Ellsberg Paradox

Ellsberg (1961) demonstrated a related but distinct violation involving *ambiguity* (unknown probabilities) rather than risk (known probabilities), showing people prefer known-probability bets over equally-favorable ambiguous ones — a violation more fundamentally challenging Savage's subjective probability framework than the vNM axioms per se.

#### Other Documented Anomalies

- **Common ratio effect**: preference reversals when probabilities are scaled by a common factor
- **Reflection effect**: risk aversion over gains often flips to risk-seeking over equivalent-magnitude losses
- **Reference dependence**: evaluations appear to depend on gains/losses relative to a reference point, not final wealth levels — the empirical basis of Prospect Theory (Kahneman-Tversky 1979)

**Behavioral note**: the practical materiality of these violations for asset pricing (versus laboratory choice experiments) remains an active empirical question, and EUT continues to be the dominant modeling default in mainstream finance despite these known limitations. [Unverified as a comparative claim — the relative empirical performance of EUT versus behavioral alternatives (prospect theory, rank-dependent utility) in explaining real market prices is contested across the literature rather than settled]

### Extensions Beyond Standard EUT

**Key Points**

- **Rank-Dependent Utility (RDU)** (Quiggin 1982): replaces linear probability weighting with a nonlinear probability weighting function, relaxing Independence while retaining much of EUT's tractability
- **Prospect Theory** (Kahneman & Tversky 1979): utility defined over gains/losses relative to a reference point, with loss aversion (losses loom larger than equivalent gains) and probability weighting
- **Disappointment Aversion** (Gul 1991): agents weight outcomes below a certainty-equivalent-like reference point more heavily
- **Ambiguity-averse preferences** (maxmin expected utility, smooth ambiguity models): address Ellsberg-type violations by relaxing the assumption of a single, known probability distribution
- **Recursive/Epstein-Zin preferences**: separate risk aversion from the elasticity of intertemporal substitution — a single parameter conflates both under standard CRRA, which is restrictive for dynamic asset pricing calibration

### Applications in Financial Economics

- **Portfolio choice**: the mean-variance and CRRA portfolio problems above are the direct application to optimal asset allocation
- **CAPM derivation**: quadratic utility or normally distributed returns combined with EUT yields the mean-variance efficient frontier underlying the Capital Asset Pricing Model
- **Consumption-based asset pricing (CCAPM)**: the Euler equation from CRRA expected utility maximization is the foundation of the stochastic discount factor approach and the equity premium puzzle literature
- **Insurance and risk management**: EUT concavity explains willingness to pay actuarially unfair premiums for insurance
- **Executive compensation and agency theory**: risk-averse agents (managers) versus risk-neutral principals (diversified shareholders) creates the risk-sharing tension underlying optimal contract design

### Common Pitfalls

- Treating EUT as a descriptive claim about how people actually think, rather than an axiomatic *as-if* representation of consistent choice behavior
- Conflating risk aversion (concave utility over outcomes) with loss aversion (asymmetric treatment of gains/losses relative to a reference point) — these are distinct concepts from different theoretical frameworks
- Using CARA utility with non-normal return distributions and expecting portfolio shares to behave realistically with wealth
- Misapplying the Arrow-Pratt approximation to large, non-marginal risks, where the underlying Taylor expansion breaks down
- Ignoring that expected utility is unique only up to positive affine transformation — computing or comparing "utility levels" across agents or contexts is not meaningful

**Related Topics**

- Stochastic dominance (first-order and second-order) as a utility-function-free ranking criterion
- The equity premium puzzle (Mehra-Prescott 1985) and its relation to CRRA calibration
- Epstein-Zin recursive utility and the separation of risk aversion from intertemporal substitution
- Prospect theory and cumulative prospect theory in behavioral asset pricing
- Stochastic discount factors and the Euler equation approach to asset pricing
- Mean-variance analysis and the Markowitz portfolio frontier
- Ambiguity aversion and Knightian uncertainty in portfolio theory