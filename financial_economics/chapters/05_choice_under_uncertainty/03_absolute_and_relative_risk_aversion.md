## Absolute and Relative Risk Aversion

### Definition and Motivation

Risk aversion measures how an economic agent's utility function curves relative to wealth, capturing the intuition that most individuals dislike uncertainty in outcomes and would prefer a certain payoff to a risky one with the same expected value. Given a von Neumann-Morgenstern utility function $u(w)$ defined over wealth $w$, risk aversion is characterized locally by the curvature of $u$, specifically its second derivative $u''(w)$. A risk-averse agent has $u''(w) < 0$ (concave utility), a risk-neutral agent has $u''(w) = 0$ (linear utility), and a risk-loving agent has $u''(w) > 0$ (convex utility).

Raw curvature $u''(w)$ is not by itself a useful measure of risk aversion because it is not invariant to positive affine transformations of utility (i.e., $v(w) = a + bu(w)$ for $b>0$ represents the same preferences as $u(w)$ but has different $u''$). Arrow and Pratt independently solved this by normalizing the second derivative by the first derivative, producing measures that are invariant to such transformations and that directly predict behavior (risk premia, portfolio shares, insurance demand).

### Absolute Risk Aversion (ARA)

**Definition.** The Arrow-Pratt coefficient of absolute risk aversion is defined as:

$$A(w) = -\frac{u''(w)}{u'(w)}$$

This measures risk aversion with respect to absolute changes in wealth (i.e., a fixed monetary gamble, such as "win or lose $100," regardless of the level of $w$).

**Interpretation via the risk premium.** Consider a small, actuarially fair gamble $\tilde{\varepsilon}$ with $E[\tilde{\varepsilon}] = 0$ and variance $\sigma^2_\varepsilon$, added to wealth $w$. The risk premium $\pi$ is the amount the agent would pay to avoid the gamble, defined implicitly by:

$$u(w - \pi) = E[u(w + \tilde{\varepsilon})]$$

A second-order Taylor expansion around $w$ gives the Arrow-Pratt approximation:

$$\pi \approx \frac{1}{2} A(w) \, \sigma^2_\varepsilon$$

This shows $A(w)$ directly scales the premium an agent demands to bear a small, fixed-size, additive risk. A higher $A(w)$ means the agent is more averse to a given dollar-denominated gamble at wealth level $w$.

**Behavior of $A(w)$ across wealth.** Three canonical classifications describe how absolute risk aversion changes as wealth increases:

- **DARA (Decreasing Absolute Risk Aversion):** $A'(w) < 0$. Wealthier agents demand a smaller premium for a fixed-size gamble and are willing to hold more dollars in risky assets as wealth rises. This is the empirically favored case: wealthy individuals typically hold larger absolute (dollar) amounts of risky assets than poorer individuals.
- **CARA (Constant Absolute Risk Aversion):** $A'(w) = 0$. The dollar amount invested in risky assets is invariant to wealth changes.
- **IARA (Increasing Absolute Risk Aversion):** $A'(w) > 0$. Wealthier agents hold fewer dollars in risky assets as wealth rises — generally considered empirically implausible for most asset classes.

**[Unverified]** Whether real-world investors actually exhibit strict DARA over their entire wealth range, versus some other locally-varying pattern, is an empirical question that is not settled uniformly across all populations and asset classes; DARA is a widely used *assumption* consistent with typical portfolio behavior, not a universally validated law.

### Relative Risk Aversion (RRA)

**Definition.** The Arrow-Pratt coefficient of relative risk aversion is defined as:

$$R(w) = -\frac{w \, u''(w)}{u'(w)} = w \cdot A(w)$$

This measures risk aversion with respect to *proportional* changes in wealth (i.e., a gamble specified as a percentage of current wealth, such as "win or lose 10% of your wealth").

**Interpretation via the risk premium.** Consider a proportional gamble $w(1+\tilde{\varepsilon})$, where $\tilde{\varepsilon}$ has $E[\tilde{\varepsilon}]=0$ and variance $\sigma^2_\varepsilon$. Define the proportional risk premium $\rho$ (as a fraction of wealth) by $u(w(1-\rho)) = E[u(w(1+\tilde{\varepsilon}))]$. The analogous second-order approximation gives:

$$\rho \approx \frac{1}{2} R(w) \, \sigma^2_\varepsilon$$

$R(w)$ thus governs the fraction of wealth an agent would sacrifice to avoid a proportional risk, making it the natural measure for questions about portfolio *shares* (the fraction of wealth allocated to risky assets) rather than dollar amounts.

**Behavior of $R(w)$ across wealth.**

- **DRRA (Decreasing Relative Risk Aversion):** $R'(w) < 0$. The optimal *share* of wealth in risky assets rises as wealth increases.
- **CRRA (Constant Relative Risk Aversion):** $R'(w) = 0$. The optimal portfolio share in risky assets is invariant to the level of wealth — a widely used simplifying assumption in macroeconomics and asset pricing because it is consistent with balanced growth (portfolio shares do not trend as the economy grows).
- **IRRA (Increasing Relative Risk Aversion):** $R'(w) > 0$. The optimal risky-asset share falls as wealth rises.

**[Unverified]** Empirical estimates of whether RRA is roughly constant, decreasing, or increasing in wealth vary across studies, datasets, and estimation methods; CRRA is best understood as a tractable benchmark rather than an empirically undisputed fact.

### Canonical Utility Functions and Their ARA/RRA

| Utility function | $u(w)$ | $A(w)$ | $R(w)$ | Classification |
| --- | --- | --- | --- | --- |
| Quadratic | $w - \frac{b}{2}w^2$ | $\frac{b}{1-bw}$ | $\frac{bw}{1-bw}$ | IARA, IRRA |
| Exponential (CARA) | $-e^{-\alpha w}$ | $\alpha$ (constant) | $\alpha w$ | CARA, IRRA |
| Power (CRRA) | $\frac{w^{1-\gamma}}{1-\gamma}$, $\gamma \neq 1$ | $\frac{\gamma}{w}$ | $\gamma$ (constant) | DARA, CRRA |
| Logarithmic | $\ln(w)$ | $\frac{1}{w}$ | $1$ | DARA, CRRA (special case of power with $\gamma=1$) |
| HARA (general) | see below | $\frac{1}{\frac{a}{1-\gamma} + \frac{w}{1-\gamma}}$ (form varies) | linear in $w$ under standard parameterization | Nests CARA, CRRA as special cases |

**Quadratic utility** is a special, cautionary case: it exhibits IARA everywhere, meaning richer agents are modeled as holding *fewer* dollars in risky assets, which contradicts typical empirical portfolio behavior. It is used primarily for its analytical convenience (it depends only on mean and variance, underlying the mean-variance framework) rather than for its realism regarding risk-aversion dynamics. It is also only defined (increasing) up to the bliss point $w = 1/b$, beyond which $u'(w) < 0$.

**Exponential (CARA) utility**, $u(w) = -e^{-\alpha w}$ with $\alpha > 0$ the constant absolute risk aversion coefficient, is widely used because it implies a demand for risky assets in *dollar* terms that does not depend on the level of wealth — convenient for models with normally distributed returns (mean-variance analysis under CARA-normal setups), and for keeping the analysis of insurance and hedging demand independent of the wealth distribution.

**Power (CRRA) utility**, $u(w) = \frac{w^{1-\gamma}}{1-\gamma}$ for $\gamma > 0$, $\gamma \neq 1$, is the standard workhorse in macroeconomics, asset pricing, and life-cycle finance because CRRA implies portfolio shares in risky assets are independent of wealth level, consistent with balanced economic growth. As $\gamma \to 1$, this converges to $\ln(w)$.

**HARA (Hyperbolic Absolute Risk Aversion)** utility is the general class:

$$u(w) = \frac{1-\gamma}{\gamma}\left(\frac{aw}{1-\gamma} + b\right)^{\gamma}$$

for appropriate parameter restrictions, and it nests CARA, CRRA, and quadratic utility as special/limiting cases. It is used when researchers want a flexible functional form whose $A(w)$ is a linear (hyperbolic) function of wealth, allowing for a "subsistence level" of wealth below which risk aversion becomes very large.

### Relationship Between ARA and RRA

Since $R(w) = w \cdot A(w)$, the two measures are mechanically linked but respond differently to gamble framing:

- $A(w)$ answers: "How much would you pay to avoid a **fixed-dollar** risk at this wealth level?"
- $R(w)$ answers: "How much (as a **percentage of wealth**) would you pay to avoid a **proportional** risk at this wealth level?"

A useful worked numerical example: suppose $u(w) = \ln(w)$ (log utility), so $A(w) = 1/w$ and $R(w) = 1$ (CRRA with $\gamma=1$). At $w = \$100{,}000$:

- $A(100{,}000) = 0.00001$ — a very small coefficient, appropriate for evaluating a gamble of, say, $\pm\$1{,}000$.
- $R(100{,}000) = 1$ — this dimensionless value directly says the agent is exactly log-utility risk averse regardless of wealth level, so the fractional risk premium for a proportional gamble with variance $\sigma_\varepsilon^2$ is approximately $\frac{1}{2}\sigma_\varepsilon^2$, unaffected by whether wealth is $10,000 or $10,000,000.

This illustrates why $R(w)$, not $A(w)$, is preferred when comparing risk attitudes across agents or time periods with different wealth levels: $A(w)$ mechanically shrinks as $w$ grows even if the agent's "true" aversion to proportional risk is unchanged, whereas $R(w)$ can remain stable.

### Application 1: Portfolio Choice

Consider an agent allocating wealth $w$ between a risk-free asset (return $r_f$) and a risky asset (return $r_f + \tilde{x}$, where $E[\tilde{x}] = \mu > 0$). Let $\theta$ denote the dollar amount invested in the risky asset. Maximizing $E[u(w(1+r_f) + \theta\tilde{x})]$ and taking a second-order approximation around the risk-free outcome yields the approximate optimal dollar holding:

$$\theta^* \approx \frac{\mu}{\sigma_x^2} \cdot \frac{1}{A(w)}$$

- Under **CARA**, $A(w) = \alpha$ is constant, so $\theta^*$ is independent of wealth — an agent who becomes richer holds the *same dollar amount* in risky assets, not the same share (implying the risky-asset share falls as wealth rises).
- Under **CRRA**, the risky asset *share* $\theta^*/w \approx \frac{\mu}{\sigma_x^2 R(w)}$ is constant in $w$ since $R(w) = \gamma$ is constant — an agent's portfolio share does not change with wealth, though dollar holdings scale up proportionally.

This is the central mechanism by which ARA and RRA map into empirically testable predictions about household portfolio behavior across the wealth distribution.

### Application 2: Insurance Demand

For full or partial insurance against a random loss $\tilde{L}$, the willingness to pay a premium above the actuarially fair value is governed by $A(w)$ (for a fixed-dollar loss) via the same $\pi \approx \frac{1}{2}A(w)\sigma_L^2$ approximation. Under DARA, wealthier individuals require a smaller loading (markup over fair premium) to purchase full insurance against a fixed-dollar loss, predicting that insurance demand for fixed-value risks (e.g., a fixed deductible policy) should decline somewhat as wealth increases, all else equal. **[Inference]** This is a standard theoretical prediction of the DARA framework; the magnitude and even direction of such effects in specific insurance markets can be confounded by other factors (income effects, adverse selection, liquidity constraints) not captured by the simple expected-utility model.

### Relationship to Certainty Equivalent

The certainty equivalent $CE$ of a gamble $\tilde{w}$ satisfies $u(CE) = E[u(\tilde{w})]$, and the risk premium is $\pi = E[\tilde{w}] - CE$. Both $A(w)$ and $R(w)$ are local (small-risk) approximations to how far $CE$ falls below expected wealth; for larger, non-marginal gambles, the *exact* risk premium must be computed directly from $u$ rather than via the Taylor approximation, since the approximation error grows with the size and skewness of the gamble.

### Visualizing the Concepts

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 900 480" font-family="Helvetica, Arial, sans-serif">
<text x="450" y="28" text-anchor="middle" font-size="18" font-weight="bold" fill="#1a1a1a">Absolute vs. Relative Risk Aversion (svg_diagram)</text>

<g>
<text x="200" y="55" text-anchor="middle" font-size="14" font-weight="bold" fill="#333">Concave Utility and Risk Premium</text>
<line x1="60" y1="380" x2="60" y2="70" stroke="#333" stroke-width="1.5" />
<line x1="60" y1="380" x2="380" y2="380" stroke="#333" stroke-width="1.5" />
<text x="220" y="410" text-anchor="middle" font-size="12" fill="#333">Wealth (w)</text>
<text x="30" y="220" text-anchor="middle" font-size="12" fill="#333" transform="rotate(-90 30 220)">Utility u(w)</text>



```

<path d="M 70 360 Q 180 300 240 220 Q 290 150 360 90" fill="none" stroke="#2563eb" stroke-width="2.5" />


<line x1="130" y1="380" x2="130" y2="320" stroke="#999" stroke-dasharray="3,3" />
<line x1="320" y1="380" x2="320" y2="105" stroke="#999" stroke-dasharray="3,3" />
<line x1="225" y1="380" x2="225" y2="228" stroke="#999" stroke-dasharray="3,3" />

<circle cx="130" cy="320" r="3.5" fill="#dc2626" />
<circle cx="320" cy="105" r="3.5" fill="#dc2626" />
<circle cx="225" cy="228" r="3.5" fill="#059669" />


<line x1="130" y1="320" x2="320" y2="105" stroke="#dc2626" stroke-width="1.5" stroke-dasharray="5,3" />


<circle cx="225" cy="212" r="3.5" fill="#dc2626" />
<line x1="225" y1="228" x2="225" y2="212" stroke="#f59e0b" stroke-width="2.5" />

<text x="130" y="398" text-anchor="middle" font-size="10" fill="#333">w-ε</text>
<text x="320" y="398" text-anchor="middle" font-size="10" fill="#333">w+ε</text>
<text x="225" y="398" text-anchor="middle" font-size="10" fill="#333">E[w]</text>
<text x="140" y="220" font-size="10" fill="#059669">CE = u⁻¹(E[u(w̃)])</text>
<text x="228" y="205" font-size="10" fill="#f59e0b">π (risk premium)</text>
<text x="230" y="120" font-size="10" fill="#dc2626">E[u(w̃)]</text>
```

</g>

<g transform="translate(460,0)">
<text x="200" y="55" text-anchor="middle" font-size="14" font-weight="bold" fill="#333">DARA with Constant RRA (Power Utility)</text>
<line x1="60" y1="380" x2="60" y2="70" stroke="#333" stroke-width="1.5" />
<line x1="60" y1="380" x2="380" y2="380" stroke="#333" stroke-width="1.5" />
<text x="220" y="410" text-anchor="middle" font-size="12" fill="#333">Wealth (w)</text>
<text x="30" y="220" text-anchor="middle" font-size="12" fill="#333" transform="rotate(-90 30 220)">Coefficient value</text>



```

<path d="M 75 100 Q 140 220 220 300 Q 280 340 360 355" fill="none" stroke="#2563eb" stroke-width="2.5" />
<text x="300" y="300" font-size="11" fill="#2563eb" font-weight="bold">A(w) = γ/w</text>
<text x="300" y="315" font-size="10" fill="#2563eb">(DARA, falling)</text>


<line x1="75" y1="230" x2="360" y2="230" stroke="#059669" stroke-width="2.5" />
<text x="300" y="222" font-size="11" fill="#059669" font-weight="bold">R(w) = γ</text>
<text x="300" y="248" font-size="10" fill="#059669">(CRRA, constant)</text>
```

</g>
</svg>

### Decision Flow: Choosing a Utility Function by Risk-Aversion Property

```mermaid
flowchart TD
    A[Modeling problem: need to specify u(w)] --> B{Is portfolio share or dollar holding<br/>expected to be stable across wealth?}
    B -->|Dollar amount in risky asset<br/>should be wealth-invariant| C[Use CARA: u(w) = -e^(-alpha*w)<br/>A(w) = alpha constant]
    B -->|Share of wealth in risky asset<br/>should be wealth-invariant| D[Use CRRA / Power: u(w) = w^(1-gamma)/(1-gamma)<br/>R(w) = gamma constant]
    D --> E{Is gamma = 1?}
    E -->|Yes| F[Reduces to log utility: u(w) = ln(w)]
    E -->|No| G[General power utility, gamma != 1]
    B -->|Need flexible subsistence level<br/>or nesting of CARA and CRRA| H[Use HARA family]
    C --> I[Check empirical fit:<br/>CARA implies IRRA - share falls as wealth rises]
    D --> J[Check empirical fit:<br/>CRRA implies DARA - dollar amount rises with wealth]
```

### Common Pitfalls and Clarifications

- Confusing $A(w)$ and $R(w)$ when the gamble in question is not clearly specified as fixed-dollar versus proportional; the correct measure depends entirely on how the risk scales with wealth.
- Assuming quadratic utility is a good "default" choice for risk-aversion analysis: it is analytically convenient for mean-variance portfolio theory but carries the behaviorally awkward implication of IARA and IRRA (risk aversion rising in both absolute and relative terms with wealth), and has a satiation (bliss) point beyond which marginal utility turns negative.
- Treating the Arrow-Pratt formulas as exact rather than local (second-order Taylor) approximations; for large gambles, the approximation $\pi \approx \frac{1}{2}A(w)\sigma^2$ can diverge meaningfully from the exact risk premium computed from $u(w-\pi) = E[u(w+\tilde\varepsilon)]$.
- Forgetting that $A(w)$ and $R(w)$ are properties of a *specific* utility representation but are *invariant* to which positive affine transformation of that utility function is used — unlike $u''(w)$ alone, which is not.

**Next Steps**

- Certainty equivalents and the exact (non-approximated) risk premium
- Stochastic dominance (first-order and second-order) as an alternative, distribution-based ordering of risky prospects
- Mean-variance analysis and its relationship to quadratic utility / normally distributed returns
- The equity premium puzzle and estimated coefficients of relative risk aversion in asset pricing
- Prudence and the coefficient of absolute/relative prudence (third derivative of utility, precautionary saving)
- Comparative risk aversion across agents (Pratt's theorem on "more risk averse")
- Habit formation and non-expected-utility alternatives (e.g., Epstein-Zin preferences) that separate risk aversion from intertemporal substitution