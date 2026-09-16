## Social Welfare Functions


### Overview

A social welfare function (SWF) is a mapping from the utility levels (or well-being) of individuals in society to a single aggregate measure of social welfare. Where Pareto efficiency identifies a *set* of allocations on the utility possibility frontier without ranking among them, a social welfare function resolves the equity question by imposing a specific value judgment about how individual utilities should be weighted and combined, enabling the selection of a unique socially optimal point.

### Formal Definition

A social welfare function is a function:

$$W = W(u_1, u_2, \ldots, u_n)$$

mapping the utility levels of $n$ individuals to a real-valued measure of social welfare $W$. The social planner's problem is then:

$$\max_{x \in \text{Feasible Set}} W(u_1(x), u_2(x), \ldots, u_n(x))$$

Combined with the constraint that $x$ lies on the utility possibility frontier (UPF), this problem selects a unique point — the **social optimum** — from among the infinitely many Pareto efficient allocations.

**Key Points**

- An SWF is fundamentally a **normative construct** — it encodes ethical/political judgments about interpersonal comparisons of utility and distributive justice, not a positive/descriptive claim about how societies behave.
- The Pareto criterion is a *partial* ordering (many allocations are non-comparable); an SWF imposes a *complete* ordering by resolving those comparisons via explicit weights or functional form.

### Bergson-Samuelson Social Welfare Function

**Key Points**

- The **Bergson-Samuelson SWF** is the general class $W(u_1, \ldots, u_n)$ satisfying minimal regularity conditions (typically increasing in each $u_i$ — the **Pareto principle**: if everyone is better off, social welfare increases).
- It is agnostic about functional form and interpersonal weighting — those choices are left to whichever ethical framework the analyst adopts (utilitarian, Rawlsian, etc.), which are then treated as special cases.
- Bergson (1938) and Samuelson (1947) developed this to formalize welfare comparisons *without* requiring interpersonal utility comparisons to be "scientifically" derived — the SWF itself is the vehicle through which any desired ethical weighting is expressed.

### Major Functional Forms

**1. Utilitarian (Classical/Benthamite) SWF**

$$W_{util} = \sum_{i=1}^n u_i = u_1 + u_2 + \cdots + u_n$$

- Maximizes the unweighted sum of individual utilities.
- Implies each individual's utility counts equally at the margin, and social welfare is indifferent to *how* a given total is distributed among individuals.
- Under diminishing marginal utility of income (a common assumption), a utilitarian planner will tend to favor *some* redistribution from rich to poor because a marginal dollar generates more utility for a poorer person — but only up to the point where marginal utilities are fully equalized, not necessarily full equality.

**2. Weighted Utilitarian SWF**

$$W_{weighted} = \sum_{i=1}^n \alpha_i u_i, \quad \alpha_i > 0$$

- Generalizes the classical case by allowing different social weights $\alpha_i$ on each individual's utility, reflecting explicit value judgments (e.g., higher weight on the disadvantaged).

**3. Rawlsian (Maximin) SWF**

$$W_{Rawls} = \min(u_1, u_2, \ldots, u_n)$$

- Social welfare equals the utility of the **worst-off** individual only.
- Implies the planner should choose the allocation that maximizes the minimum utility in society — the "maximin" criterion.
- Derived from John Rawls's "veil of ignorance" thought experiment: a rational individual designing social institutions without knowing their own position in society would be infinitely risk-averse and would maximize the floor.
- Implies **zero weight** on utility gains to anyone above the minimum, unless those gains also raise the minimum (e.g., via incentive effects that grow the total pie).

**4. Nash Social Welfare Function**

$$W_{Nash} = \prod_{i=1}^n u_i = u_1 \times u_2 \times \cdots \times u_n$$

- Derived from Nash's axiomatic bargaining solution; balances efficiency and equity — sensitive to both the level and distribution of utility, more egalitarian than pure utilitarianism but less extreme than Rawlsian maximin.

**5. CES (Constant Elasticity of Substitution) / Atkinson-style SWF**

$$W_{CES} = \left(\sum_{i=1}^n u_i^{1-\varepsilon}\right)^{\frac{1}{1-\varepsilon}}, \quad \varepsilon \geq 0$$

- A flexible family nesting the other cases as special/limiting values of the **inequality aversion parameter** $\varepsilon$:
  - $\varepsilon = 0$: reduces to utilitarian (no aversion to inequality in utility).
  - $\varepsilon \to \infty$: converges to Rawlsian maximin (extreme aversion to inequality).
  - Intermediate $\varepsilon$: partial inequality aversion — commonly used in applied optimal-tax and inequality research (related to the **Atkinson index** of inequality measurement).

### Diagram: SWF Indifference Curves and the Social Optimum

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 440" font-family="sans-serif">
<text x="320" y="24" text-anchor="middle" font-size="16" font-weight="bold">Social Welfare Optimum on the UPF (svg_diagram)</text>
<line x1="80" y1="380" x2="580" y2="380" stroke="#333" stroke-width="2" />
<line x1="80" y1="380" x2="80" y2="50" stroke="#333" stroke-width="2" />
<text x="590" y="385" font-size="13">u_A</text>
<text x="65" y="45" font-size="13">u_B</text>
<path d="M 100 360 Q 300 340 420 250 Q 500 180 520 80" stroke="#c0392b" stroke-width="2.5" fill="none" />
<text x="430" y="240" font-size="12" fill="#c0392b">Utility Possibility Frontier (UPF)</text>
<path d="M 150 340 Q 300 260 420 150" stroke="#2980b9" stroke-width="1.5" fill="none" stroke-dasharray="4,3" />
<path d="M 200 370 Q 350 280 460 190" stroke="#2980b9" stroke-width="1.5" fill="none" stroke-dasharray="4,3" />
<text x="470" y="185" font-size="11" fill="#2980b9">W indifference curves</text>
<circle cx="392" cy="222" r="5" fill="#8e44ad" />
<text x="400" y="215" font-size="12" fill="#8e44ad" font-weight="bold">Social Optimum (tangency)</text>
<path d="M 100 360 L 520 80" stroke="#27ae60" stroke-width="1.5" stroke-dasharray="2,2" />
<text x="440" y="100" font-size="11" fill="#27ae60">45° line (equal utility, illustrative)</text>
</svg>

The **social optimum** is the point of tangency between the highest attainable social welfare indifference curve and the utility possibility frontier. This point simultaneously satisfies:

$$MRS_{u_A, u_B}^{W} = \text{slope of the UPF}$$

The shape of the SWF's indifference curves determines *where* on the UPF the optimum lands: straight lines (utilitarian) are tangent wherever weighted marginal utilities equalize; L-shaped curves (Rawlsian) push the tangency toward the point of equal utility, regardless of the UPF's curvature.

### Worked Example: Choosing Between Two Allocations

**Setup**: Two feasible allocations on the UPF:

| Allocation | $u_A$ | $u_B$ |
| --- | --- | --- |
| $x_1$ | 100 | 20 |
| $x_2$ | 70 | 65 |

**Utilitarian evaluation**:

$$W(x_1) = 100 + 20 = 120, \quad W(x_2) = 70 + 65 = 135$$

Utilitarian SWF prefers $x_2$ (higher total).

**Rawlsian evaluation**:

$$W(x_1) = \min(100, 20) = 20, \quad W(x_2) = \min(70, 65) = 65$$

Rawlsian SWF also prefers $x_2$ here (higher minimum) — in this example both criteria agree, but they diverge sharply in cases where the trade-off between total and equality is more severe (e.g., a hypothetical $x_3 = (150, 5)$ would be utilitarian-preferred to $x_2$ but Rawlsian-inferior).

### Arrow's Impossibility Theorem: A Foundational Challenge

**Key Points**

- **Arrow's Impossibility Theorem** (1951) shows that no social welfare *ordering function* (aggregating individual *preference rankings*, not cardinal utilities) can simultaneously satisfy all of: (1) unrestricted domain, (2) Pareto principle, (3) independence of irrelevant alternatives, (4) non-dictatorship — for three or more alternatives and individuals.
- This theorem technically concerns **social choice functions** based on ordinal preference rankings, which is a related but distinct concept from the cardinal Bergson-Samuelson SWF used in standard welfare economics (which presumes cardinal, interpersonally comparable utility).
- [Inference] The practical resolution used throughout applied welfare economics is to *assume* cardinal, interpersonally comparable utility (explicitly a value judgment, not a "given") in order to escape Arrow's impossibility result and construct a workable Bergson-Samuelson SWF — a move that is philosophically contested but standard in applied optimal tax and welfare analysis.

### Applications in Public Economics

**Key Points**

- **Optimal taxation**: The Mirrlees model of optimal income taxation explicitly maximizes a social welfare function (often utilitarian or with an inequality-aversion parameter) subject to incentive-compatibility and government revenue constraints.
- **Cost-benefit analysis with distributional weights**: Some CBA frameworks apply differential weights to costs/benefits accruing to different income groups, effectively embedding a non-utilitarian SWF into project evaluation.
- **Inequality measurement**: The **Atkinson index** of inequality is explicitly derived from a CES-type SWF, defining the "equally distributed equivalent income" that would generate the same social welfare as the actual, unequal distribution.
- **Poverty and welfare program design**: Rawlsian-influenced criteria motivate policies focused on raising the floor (minimum income guarantees, safety nets) rather than maximizing aggregate output.

### Comparison Table: SWF Types

| SWF Type | Formula | Inequality Aversion | Policy Tendency |
| --- | --- | --- | --- |
| Utilitarian | $\sum u_i$ | None (at margin) | Maximize total; redistributes only via diminishing marginal utility |
| Weighted Utilitarian | $\sum \alpha_i u_i$ | Set by $\alpha_i$ weights | Explicit distributional preference |
| Rawlsian (Maximin) | $\min(u_i)$ | Infinite | Maximize the worst-off individual's utility |
| Nash | $\prod u_i$ | Moderate | Balance of level and equality |
| CES/Atkinson | $(\sum u_i^{1-\varepsilon})^{1/(1-\varepsilon)}$ | Tunable via $\varepsilon$ | Flexible; nests utilitarian and Rawlsian as limits |

### Critiques and Limitations

**Key Points**

- **Interpersonal comparability problem**: Cardinal utility comparisons across individuals cannot be empirically verified — any SWF requires an *assumed* basis for comparison (equal capacity for utility, equal marginal utility of income, etc.), which is a philosophical rather than empirical choice.
- **Aggregation obscures individual rights/liberties concerns**: Purely welfarist SWFs (based only on utility) can conflict with rights-based or capability-based (Sen) theories of justice that resist reducing all social value to utility aggregates.
- **Sensitivity to functional form**: Policy conclusions (e.g., optimal top marginal tax rates) can be highly sensitive to the choice of $\varepsilon$ or SWF functional form, making the choice of SWF a first-order determinant of "optimal" policy recommendations — not merely a technical detail.

**Related Topics**

- Pareto Efficiency and the Utility Possibility Frontier
- Arrow's Impossibility Theorem and Social Choice Theory
- Optimal Income Taxation (Mirrlees Model)
- Atkinson Index and Inequality Measurement
- Rawlsian Justice and the Veil of Ignorance
- Cost-Benefit Analysis with Distributional Weights
- Amartya Sen's Capability Approach