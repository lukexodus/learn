## Stochastic Dominance


### Definition and Motivation

Stochastic dominance provides a way to rank risky prospects (lotteries, random variables, probability distributions) without requiring full specification of a decision-maker's utility function. Where expected utility comparisons require assuming a specific $u(w)$, stochastic dominance criteria establish an ordering that holds for an entire *class* of utility functions satisfying weak, economically meaningful restrictions (e.g., "any increasing utility function" or "any increasing and concave utility function"). If one prospect stochastically dominates another under a given criterion, then *every* decision-maker whose preferences fall in that class will prefer the dominant prospect, regardless of the precise curvature of their utility.

This makes stochastic dominance a robust tool for ranking distributions under uncertainty: it identifies orderings that are preference-free within a class, rather than being contingent on a specific functional form or risk-aversion parameter.

### First-Order Stochastic Dominance (FOSD)

**Definition.** Let $F(x)$ and $G(x)$ be the cumulative distribution functions (CDFs) of two random variables (e.g., asset returns or wealth outcomes) with common support. $F$ **first-order stochastically dominates** $G$, written $F \succeq_{FOSD} G$, if:

$$F(x) \leq G(x) \quad \text{for all } x$$

with strict inequality for at least one $x$. Graphically, the CDF of the dominant distribution lies everywhere at or below the CDF of the dominated distribution — equivalently, $F$ assigns weakly more probability mass to higher outcomes at every threshold $x$.

**Equivalent utility characterization.** $F \succeq_{FOSD} G$ if and only if:

$$\int u(x)\, dF(x) \geq \int u(x)\, dG(x)$$

for **every non-decreasing (weakly increasing) utility function** $u$, with strict inequality for at least one strictly increasing $u$. This is the key result: FOSD requires no assumption about risk aversion at all — only that the agent prefers more to less (monotonicity of preferences). It applies equally to risk-averse, risk-neutral, and risk-loving agents.

**Alternative characterization (coupling).** $F \succeq_{FOSD} G$ if and only if there exist random variables $\tilde{X} \sim F$ and $\tilde{Y} \sim G$ defined on a common probability space such that $\tilde{X} \geq \tilde{Y}$ almost surely. Intuitively, $F$ can be obtained from $G$ by shifting probability mass toward higher outcomes.

**Mean implication.** If $F \succeq_{FOSD} G$, then $E_F[x] \geq E_G[x]$ — the dominant distribution has a weakly higher mean. However, a higher mean alone does **not** imply FOSD; FOSD is a strictly stronger, pointwise condition on the entire distribution, not merely a statement about the first moment.

### Second-Order Stochastic Dominance (SOSD)

**Definition (integral condition).** $F$ **second-order stochastically dominates** $G$ (both with the same mean, or more generally without requiring equal means for the general definition), written $F \succeq_{SOSD} G$, if:

$$\int_{-\infty}^{x} F(t)\, dt \leq \int_{-\infty}^{x} G(t)\, dt \quad \text{for all } x$$

with strict inequality for at least one $x$. This compares the *areas under the CDFs* up to every point $x$, rather than the CDFs themselves pointwise.

**Equivalent utility characterization.** $F \succeq_{SOSD} G$ if and only if:

$$\int u(x)\, dF(x) \geq \int u(x)\, dG(x)$$

for **every non-decreasing and concave utility function** $u$ (i.e., every risk-averse expected-utility maximizer who also prefers more to less), with strict inequality for at least one strictly concave $u$. SOSD thus ranks prospects for the entire class of risk-averse agents, without requiring agreement on the specific degree of risk aversion (i.e., without requiring a specific value of $A(w)$ or $R(w)$).

**Mean-preserving spread interpretation.** The canonical special case: if $F$ and $G$ have the **same mean**, then $F \succeq_{SOSD} G$ if and only if $G$ can be obtained from $F$ by a sequence of **mean-preserving spreads** (Rothschild-Stiglitz). A mean-preserving spread takes probability mass from the center of a distribution and spreads it to the tails without changing the mean — formally, it increases variance (and more generally, dispersion in the sense of second-order stochastic dominance) while holding $E[x]$ fixed. Every risk-averse agent (in the expected-utility sense) prefers the distribution with *less* mean-preserving spread, i.e., the less dispersed one, when means are equal.

**Variance implication (equal-mean case).** If $F$ and $G$ have equal means and $F \succeq_{SOSD} G$, then $\text{Var}_F[x] \leq \text{Var}_G[x]$. Note the converse does **not** hold in general: a lower variance does not by itself imply SOSD, because SOSD is a condition on the entire distribution shape (accounting for all moments and the full concavity restriction), not merely the second moment. Two distributions can have the same mean and variance yet fail to be SOSD-ranked at all (if their CDFs cross in a way inconsistent with the integral condition) — in that case they are simply not comparable under SOSD.

### Relationship Between FOSD and SOSD

FOSD is a strictly stronger condition than SOSD in the following sense: if $F \succeq_{FOSD} G$, then $F \succeq_{SOSD} G$ as well, because every non-decreasing and concave function is a special case of a non-decreasing function — so a ranking that holds for *all* increasing utility functions also holds for the *subset* of increasing and concave ones. The converse is false: two distributions can be SOSD-ranked without being FOSD-ranked (e.g., $F$ has a higher mean but is also more spread out in a way that lower-tail-sensitive agents might not universally prefer, yet risk-averse agents with concave utility still rank $F$ above $G$ because the reduced dispersion effect dominates).

**Summary of preference-class scope:**

| Dominance criterion | Preference class covered | What it restricts |
| --- | --- | --- |
| FOSD | All agents with $u' \geq 0$ | Monotonicity only (more is better) |
| SOSD | All risk-averse agents with $u' \geq 0$, $u'' \leq 0$ | Monotonicity + risk aversion (concavity) |
| Third-order (briefly) | Agents with $u' \geq 0$, $u'' \leq 0$, $u''' \geq 0$ (non-increasing absolute risk aversion / prudence) | Adds a restriction on skewness preference (downside risk aversion) |

**[Unverified]** Whether decision-makers in practice satisfy the monotonicity and concavity restrictions implied by FOSD/SOSD rankings — as opposed to exhibiting behavior better described by non-expected-utility models (e.g., probability weighting under prospect theory) — is an empirical and theoretical question outside the scope of the pure stochastic dominance framework itself.

### Worked Numerical Example

Consider two simple discrete lotteries over wealth outcomes:

**Lottery $F$:** wealth = 100 with probability 0.5, wealth = 200 with probability 0.5. $E_F[w] = 150$.

**Lottery $G$:** wealth = 50 with probability 0.5, wealth = 250 with probability 0.5. $E_G[w] = 150$.

Both lotteries share the same mean (150), so this is a natural setting for a mean-preserving spread comparison. $G$ is a mean-preserving spread of $F$: probability mass has moved from the center (100 and 200) to more extreme values (50 and 250) while preserving the mean. Therefore $F \succeq_{SOSD} G$: every risk-averse expected-utility maximizer weakly prefers $F$ to $G$.

Checking with log utility, $u(w) = \ln(w)$:

$$E_F[u] = 0.5\ln(100) + 0.5\ln(200) = 0.5(4.605) + 0.5(5.298) = 4.952$$



$$E_G[u] = 0.5\ln(50) + 0.5\ln(250) = 0.5(3.912) + 0.5(5.521) = 4.716$$

Since $E_F[u] = 4.952 > E_G[u] = 4.716$, the risk-averse log-utility agent indeed prefers $F$, consistent with the SOSD ranking.

Now consider FOSD: is $F$ FOSD-dominant over $G$? Check the CDFs. At $x=75$: $F(75) = 0$ (no mass below 75 in $F$... actually $F$ has no mass at or below 75, so $F(75)=0$), while $G(75) = 0.5$ (mass at 50 is below 75). Since $F(75) = 0 \leq G(75) = 0.5$, this point is consistent with FOSD. But at $x = 150$: $F(150) = 0.5$ (mass at 100 is below 150) and $G(150) = 0.5$ (mass at 50 is below 150) — tied. At $x=225$: $F(225) = 1$ (both 100 and 200 are below 225) while $G(225) = 0.5$ (only the 50 outcome is below 225, since 250 > 225). Here $F(225) = 1 > G(225) = 0.5$, which **violates** the FOSD condition $F(x) \leq G(x)$ for all $x$. Hence $F$ does **not** first-order stochastically dominate $G$ — confirming that a risk-*loving* agent (convex, increasing utility) could prefer $G$ over $F$ due to its higher upside (250 versus 200), even though every risk-*averse* agent prefers $F$. This illustrates precisely why FOSD is the stronger, preference-class-agnostic criterion while SOSD is specific to risk-averse agents.

### Visualizing FOSD and SOSD

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 900 480" font-family="Helvetica, Arial, sans-serif">
<text x="450" y="28" text-anchor="middle" font-size="18" font-weight="bold" fill="#1a1a1a">First- vs. Second-Order Stochastic Dominance (svg_diagram)</text>

<g>
<text x="200" y="55" text-anchor="middle" font-size="14" font-weight="bold" fill="#333">FOSD: F(x) ≤ G(x) everywhere</text>
<line x1="60" y1="380" x2="60" y2="70" stroke="#333" stroke-width="1.5" />
<line x1="60" y1="380" x2="380" y2="380" stroke="#333" stroke-width="1.5" />
<text x="220" y="405" text-anchor="middle" font-size="12" fill="#333">Outcome x</text>
<text x="30" y="220" text-anchor="middle" font-size="12" fill="#333" transform="rotate(-90 30 220)">CDF value</text>



```

<path d="M 70 375 L 150 375 L 150 260 L 250 260 L 250 130 L 340 130 L 340 80" fill="none" stroke="#2563eb" stroke-width="2.5" />
<text x="345" y="75" font-size="11" fill="#2563eb" font-weight="bold">F(x)</text>


<path d="M 70 340 L 110 340 L 110 210 L 200 210 L 200 100 L 300 100 L 300 78 L 340 78" fill="none" stroke="#dc2626" stroke-width="2.5" stroke-dasharray="6,3" />
<text x="345" y="95" font-size="11" fill="#dc2626" font-weight="bold">G(x)</text>

<text x="200" y="425" text-anchor="middle" font-size="10" fill="#333">F(x) never above G(x): F dominates G for ALL increasing u</text>
```

</g>

<g transform="translate(460,0)">
<text x="200" y="55" text-anchor="middle" font-size="14" font-weight="bold" fill="#333">SOSD: G is a mean-preserving spread of F</text>
<line x1="60" y1="380" x2="60" y2="70" stroke="#333" stroke-width="1.5" />
<line x1="60" y1="380" x2="380" y2="380" stroke="#333" stroke-width="1.5" />
<text x="220" y="405" text-anchor="middle" font-size="12" fill="#333">Outcome x</text>
<text x="30" y="220" text-anchor="middle" font-size="12" fill="#333" transform="rotate(-90 30 220)">Density</text>



```

<path d="M 90 370 Q 150 370 190 260 Q 220 180 240 180 Q 260 180 290 260 Q 330 370 380 370" fill="none" stroke="#2563eb" stroke-width="2.5" />
<text x="220" y="160" text-anchor="middle" font-size="11" fill="#2563eb" font-weight="bold">F: less dispersed</text>


<path d="M 75 375 Q 130 300 190 290 Q 220 285 250 290 Q 310 300 365 375" fill="none" stroke="#dc2626" stroke-width="2.5" stroke-dasharray="6,3" />
<text x="300" y="270" text-anchor="middle" font-size="11" fill="#dc2626" font-weight="bold">G: more dispersed</text>

<line x1="220" y1="380" x2="220" y2="70" stroke="#999" stroke-dasharray="2,2" />
<text x="220" y="395" text-anchor="middle" font-size="10" fill="#333">same mean</text>
```

</g>
</svg>

### Decision Flow: Applying Stochastic Dominance to Rank Two Prospects

```mermaid
flowchart TD
    A[Two distributions F and G to compare] --> B{Does F(x) <= G(x)<br/>for all x?}
    B -->|Yes, strictly for some x| C[F FOSD-dominates G:<br/>preferred by ALL agents with increasing utility<br/>-- risk-averse, risk-neutral, risk-loving]
    B -->|No, CDFs cross| D{Do F and G have the<br/>same mean?}
    D -->|Yes| E{Is integral of F CDF<br/>less than or equal to integral of G CDF<br/>at every point?}
    D -->|No| H[General SOSD integral test:<br/>compare cumulative integrals of F and G directly]
    E -->|Yes| F[F SOSD-dominates G:<br/>G is a mean-preserving spread of F<br/>preferred by ALL risk-averse agents]
    E -->|No| G[F and G are NOT dominance-ranked:<br/>ranking depends on the specific utility function chosen]
    H --> I{Integral condition holds?}
    I -->|Yes| F
    I -->|No| G
```

### Applications in Financial Economics

- **Portfolio selection screening.** Stochastic dominance criteria are used to eliminate dominated assets or strategies from consideration before applying a specific utility-based optimization, since any prospect that is FOSD- or SOSD-dominated by another is never optimal for the relevant class of agents.
- **Evaluating fund performance.** SOSD comparisons of return distributions across investment funds or strategies provide a robust ranking that does not require assuming a specific coefficient of risk aversion, useful when comparing performance across investors with heterogeneous (but risk-averse) preferences.
- **Insurance contract design.** FOSD is used to establish that certain insurance arrangements (e.g., adding coverage that weakly improves outcomes in every state) are preferred by all monotone-preference agents, while SOSD analysis is used to compare risk-sharing arrangements that reduce dispersion.
- **Welfare comparisons of income/wealth distributions.** SOSD (via the mean-preserving-spread / Lorenz-curve connection) underlies comparisons of income inequality: a distribution that Lorenz-dominates another, given equal means, corresponds to an SOSD ranking, connecting the concept to inequality measurement.

### Common Pitfalls and Clarifications

- Concluding that a higher-mean distribution is preferred by "everyone" — this is only guaranteed under FOSD, not simply from comparing means, since FOSD is a much stronger (pointwise CDF) condition than a mean comparison.
- Applying the mean-preserving-spread intuition for SOSD when the two distributions do **not** have equal means; the general SOSD definition (via the integrated CDF condition) still applies, but the intuitive "spread implies dominated" story specifically requires equal means (Rothschild-Stiglitz form).
- Assuming that failing FOSD or SOSD means the two prospects are "equally good" — in fact, when neither dominance condition holds, the prospects are simply **not comparable** by that criterion, and the ranking depends on the decision-maker's specific utility function.
- Treating a lower-variance distribution as automatically SOSD-dominant when means are unequal, or without checking the full CDF-integral condition — variance alone is an incomplete summary of second-order dominance except in the exact equal-mean, mean-preserving-spread case.

**Next Steps**

- Rothschild-Stiglitz mean-preserving spreads and their formal measures of "more risky"
- Third-order stochastic dominance and downside risk / prudence
- The link between SOSD and the Lorenz curve in income-inequality measurement
- Absolute and relative risk aversion (Arrow-Pratt measures) as the utility-based counterpart to stochastic dominance
- Almost stochastic dominance (relaxations of FOSD/SOSD for empirical/finite-sample testing)
- Applications to portfolio performance evaluation and asset pricing anomalies