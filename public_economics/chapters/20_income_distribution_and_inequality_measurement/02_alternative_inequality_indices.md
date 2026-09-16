## Alternative Inequality Indices


### Overview and Conceptual Framework

While the Gini coefficient is the most widely reported inequality statistic, it is one member of a much larger family of inequality indices, each embodying different implicit value judgments about *where* in the distribution inequality matters most and *how* transfers should be weighted. This item surveys the principal alternatives — the Generalized Entropy class, the Atkinson index, and related measures — and the axiomatic framework used to compare them.

### The Axiomatic Approach to Inequality Measurement

Before cataloguing specific indices, it is useful to state the standard axioms an inequality index $I(\cdot)$ is generally required (or desired) to satisfy:

**Key Points**

- **Anonymity (Symmetry)**: $I$ depends only on the vector of incomes, not on which individual holds which income
- **Population (Replication) Invariance**: $I$ is unchanged if the population is replicated $k$ times with the same income distribution
- **Scale Invariance (Mean Independence)**: $I$ is unchanged if all incomes are scaled by the same positive constant — this reflects a normative choice that *relative* rather than absolute inequality is the object of interest (some alternative indices relax this, see "Absolute vs. Relative Inequality" below)
- **Pigou-Dalton Transfer Principle**: a mean-preserving progressive transfer (from richer to poorer, not reversing rank) strictly reduces $I$
- **Decomposability**: the ability to partition $I$ for the full population into a **within-group** component and a **between-group** component when the population is split into mutually exclusive subgroups (by region, sector, demographic category, etc.) — this axiom is *not* satisfied by all indices (notably the Gini, only imperfectly), and is often the decisive practical reason for choosing one index family over another in applied decomposition work

The **Generalized Entropy (GE)** class is specifically constructed to satisfy full additive decomposability, which the Gini does not, making it the preferred family whenever within/between decomposition is the research objective.

### The Generalized Entropy Class

The GE class is parameterized by $\alpha \in \mathbb{R}$, which governs the sensitivity of the index to different parts of the income distribution:

$$GE(\alpha) = \frac{1}{\alpha(\alpha-1)} \left[ \frac{1}{n} \sum_{i=1}^n \left( \frac{x_i}{\mu} \right)^\alpha - 1 \right], \quad \alpha \neq 0, 1$$

with limiting cases defined by continuity as $\alpha \to 0$ and $\alpha \to 1$:

$$GE(0) = \frac{1}{n} \sum_{i=1}^n \ln\left(\frac{\mu}{x_i}\right) \quad \text{(Mean Log Deviation, "Theil's L")}$$



$$GE(1) = \frac{1}{n} \sum_{i=1}^n \frac{x_i}{\mu} \ln\left(\frac{x_i}{\mu}\right) \quad \text{(Theil's T index)}$$

**Key Points**

- **Higher $\alpha$ values weight the index more heavily toward the top of the distribution**: $\alpha = 2$ is proportional to the (squared) coefficient of variation and is most sensitive to gaps among high incomes; **lower (including negative) $\alpha$ values weight the index more heavily toward the bottom** — $GE(0)$ (Mean Log Deviation) is particularly sensitive to low incomes because the logarithm diverges as $x_i \to 0$
- The parameter $\alpha$ therefore functions analogously to the inequality-aversion parameter in the Atkinson index (below): choosing among GE-class members is equivalent to choosing where along the distribution the researcher wants the index to be most responsive to changes
- **All members of the GE class satisfy exact additive decomposability**:

$$GE(\alpha) = GE_{\text{within}}(\alpha) + GE_{\text{between}}(\alpha)$$

where the within-group term is a population-share-and-income-share-weighted average of each subgroup's own $GE(\alpha)$, and the between-group term is the $GE(\alpha)$ that would result if every individual in a subgroup received that subgroup's mean income — this clean decomposition is the primary practical reason GE-class indices (especially Theil's $T$ and $L$) are preferred over the Gini in applied work studying, for example, the contribution of regional, sectoral, or demographic inequality to national inequality

- **Theil's T ($\alpha=1$)** is more sensitive to inequality among **high incomes**; **Theil's L / Mean Log Deviation ($\alpha=0$)** is more sensitive to inequality among **low incomes** — applied researchers often report both alongside the Gini specifically to characterize *where* in the distribution measured inequality is concentrated, since two distributions can have similar Gini coefficients but very different $GE(0)$ vs. $GE(1)$ splits, indicating different underlying shapes

**Illustration: Sensitivity of GE-Class Members Across the Distribution (svg_diagram)**

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 720 360">
<text x="360" y="25" font-size="16" font-weight="bold" text-anchor="middle" fill="#1a1a1a">Weighting Across the Distribution (svg_diagram)</text>
<line x1="90" y1="300" x2="650" y2="300" stroke="#333" stroke-width="2" />
<line x1="90" y1="60" x2="90" y2="300" stroke="#333" stroke-width="2" />
<text x="370" y="330" font-size="13" text-anchor="middle" fill="#333">Income Percentile (low to high)</text>
<text x="40" y="180" font-size="13" text-anchor="middle" fill="#333" transform="rotate(-90 40 180)">Implicit Weight</text>

<path d="M 100 90 Q 200 130 320 260 Q 450 295 620 298" fill="none" stroke="`#c62828`" stroke-width="3" />

<text x="120" y="80" font-size="12" fill="`#c62828`">GE(0) — Mean Log Deviation: bottom-sensitive</text>

<path d="M 100 270 Q 250 260 370 240 Q 500 190 620 90" fill="none" stroke="`#1e88e5`" stroke-width="3" />

<text x="420" y="80" font-size="12" fill="`#1e88e5`">GE(2): top-sensitive</text>

<path d="M 100 200 Q 300 180 370 175 Q 500 170 620 160" fill="none" stroke="`#43a047`" stroke-width="3" />

<text x="130" y="200" font-size="12" fill="`#43a047`">Gini: peaks near median</text>

</svg>

### The Atkinson Index

The Atkinson index is derived from an explicit **social welfare function** approach: assuming a symmetric, additively separable, constant-relative-inequality-aversion utility function with parameter $\epsilon \geq 0$ (the **inequality aversion parameter**), the index measures the proportional loss of welfare due to inequality relative to a fully equal distribution with the same mean.

$$A_\epsilon = 1 - \frac{y_{EDE}}{\mu}, \quad \text{where } y_{EDE} = \left[ \frac{1}{n} \sum_{i=1}^n \left(\frac{x_i}{\mu}\right)^{1-\epsilon} \right]^{\frac{1}{1-\epsilon}} \cdot \mu \;\; (\epsilon \neq 1)$$

with the limiting case $\epsilon = 1$ given by the geometric mean:

$$y_{EDE} = \exp\left[ \frac{1}{n}\sum_{i=1}^n \ln x_i \right]$$

**Key Points**

- $y_{EDE}$, the **equally-distributed-equivalent income**, is the level of income that, if given equally to everyone, would generate the same social welfare as the actual (unequal) distribution — this is the index's key normative feature: $A_\epsilon$ has a direct welfare interpretation as "the fraction of total income society would be willing to sacrifice to eliminate inequality," which the Gini and GE-class indices do not offer directly
- **$\epsilon$ is a direct, researcher-chosen parameter of inequality aversion**: at $\epsilon = 0$, the index reduces to zero regardless of distribution (no aversion to inequality — only the mean matters); as $\epsilon \to \infty$, the index converges to a **Rawlsian (maximin) criterion**, where $y_{EDE}$ approaches the minimum income in the distribution and $A_\epsilon \to 1 - x_{min}/\mu$ — the researcher's explicit choice of $\epsilon$ makes the underlying value judgment transparent in a way that is not the case for the Gini, whose implicit weighting (heaviest near the median) is a byproduct of its formula rather than a deliberately chosen ethical parameter
- The Atkinson index is a **monotonic transformation of a specific GE-class member**: for a given $\epsilon$, $A_\epsilon$ is an ordinally (and for inference purposes, near-monotonically) related transformation of $GE(1-\epsilon)$, so the two families are closely linked mathematically, but the Atkinson index's explicit welfare-function derivation makes it the preferred choice in **normative/welfare-economics applications** (e.g., computing the money-metric welfare cost of inequality, or comparing the welfare implications of alternative tax-and-transfer policies), while GE-class indices are preferred for **positive/decomposition-focused** applications
- Because $A_\epsilon$ requires taking incomes to a power (and the log for $\epsilon=1$), it is **undefined for zero or negative incomes** without ad hoc adjustment, a practical limitation shared with $GE(\alpha)$ for $\alpha \leq 0$ — relevant when applying these indices to wealth data, where negative net worth is common

### Relative versus Absolute Inequality Indices

**Key Points**

- All indices discussed above (Gini, GE class, Atkinson) are **relative** inequality indices: they satisfy scale invariance, meaning a proportional scaling of all incomes (e.g., 10% economic growth distributed proportionally) leaves measured inequality unchanged
- **Absolute inequality indices** instead satisfy **translation invariance**: adding the same absolute amount to every individual's income leaves the index unchanged, rather than a proportional scaling doing so. The canonical example is the **absolute Gini** (the standard Gini multiplied by the mean, $G_{abs} = G \cdot \mu$) and the **variance** of income levels
- The choice between relative and absolute inequality concepts is itself a **value judgment with direct policy relevance**: under a relative index, if all incomes double, measured inequality is unchanged even though the *absolute* gap between rich and poor has also doubled; an absolute index would register this as an increase in inequality. This distinction has been central to debates over whether measured global or national inequality has risen or fallen during periods of broad-based economic growth, since the relative and absolute answers can differ [Unverified — the empirical ranking of "has inequality risen" is sensitive to this choice and to the specific time period and country examined]
- **Intermediate inequality indices** (e.g., Kolm's index, or "centrist" indices interpolating between relative and absolute concepts) have been proposed in the literature to avoid committing fully to either extreme, though they see less routine applied use than the standard relative indices

### The Extended Gini and Single-Parameter Gini Family

**Key Points**

- The standard Gini coefficient can be generalized into a **single-parameter family** (the "extended" or "generalized" Gini, associated with Donaldson and Weymark, and Yitzhaki) that introduces a parameter $\nu > 0$ controlling the rank-based weighting scheme — at $\nu = 2$ this collapses to the standard Gini; other values of $\nu$ shift the implicit weighting toward the bottom ($\nu$ large) or top ($\nu$ close to $0$ or $1$) of the distribution
- This addresses the standard Gini's key limitation (median-centered sensitivity) while retaining the rank-based, Lorenz-curve-linked interpretation that GE-class and Atkinson indices lack — the extended Gini family is used less frequently in applied cross-country reporting than the standard Gini, but appears regularly in the theoretical/methodological inequality-measurement literature and in specific applications (e.g., tax-progressivity and redistribution studies building on Yitzhaki's related work on the concentration curve)

### Choosing Among Indices: Practical Guidance

**Key Points**

- **For headline/cross-country comparability reporting**: the Gini remains the dominant convention (used by the World Bank, OECD, and most national statistical agencies), primarily due to its long track record, intuitive Lorenz-curve geometric interpretation, and broad public/policy familiarity, despite its decomposition and median-sensitivity limitations
- **For within/between-group decomposition** (e.g., how much of national inequality is explained by regional, educational, or sectoral differences): a GE-class index (Theil's $T$ or $L$) is the standard choice because of exact additive decomposability
- **For explicit welfare/normative analysis** (e.g., computing the money-metric welfare loss from inequality, or ranking policy alternatives under an explicit social welfare function with a stated inequality-aversion parameter): the Atkinson index is preferred because its parameter $\epsilon$ has direct ethical interpretability and the index maps directly to an equally-distributed-equivalent income
- **For questions specifically about the bottom of the distribution**: the Mean Log Deviation ($GE(0)$) or the Atkinson index with high $\epsilon$, or dedicated poverty indices (Foster-Greer-Thorbecke class), are more appropriate than the Gini
- **For questions specifically about the top of the distribution**: top income/wealth shares computed from administrative tax-record data (rather than any single summary index) are the standard tool, since household survey data — on which Gini, GE, and Atkinson estimates are typically based — systematically under-captures top-end incomes
- **A robust methodological practice**, given that no single index is uniformly superior, is to **report multiple indices alongside the Lorenz curve itself** (or multiple percentile ratios, e.g., P90/P10, P90/P50, P50/P10) rather than relying on a single summary statistic, particularly when Lorenz curves being compared cross (see the Lorenz Dominance discussion under "Lorenz Curve and Gini Coefficient" in this chapter) and no single index can provide an unambiguous ranking without an implicit or explicit value judgment about where in the distribution inequality matters most

### Comparative Summary Table

| Index | Parameter | Decomposable? | Most Sensitive To | Welfare Interpretation |
| --- | --- | --- | --- | --- |
| Gini | — | No (approx. only) | Middle of distribution | Indirect (via Lorenz dominance) |
| Theil's T, $GE(1)$ | — | Yes | Top of distribution | None (positive measure) |
| Mean Log Deviation, $GE(0)$ | — | Yes | Bottom of distribution | None (positive measure) |
| $GE(\alpha)$, general | $\alpha$ | Yes | Tunable via $\alpha$ | None (positive measure) |
| Atkinson | $\epsilon$ | No | Tunable via $\epsilon$ | Direct (equally-distributed-equivalent income) |
| Extended Gini | $\nu$ | No | Tunable via $\nu$ | Indirect (generalized Lorenz-based) |
| Absolute Gini | — | No | Middle (in level terms) | None (positive measure) |

### Decision Workflow for Index Selection

```mermaid
flowchart TD
    A[Research question] --> B{Need within/between-group decomposition?}
    B -->|Yes| C[Use Theil T or Mean Log Deviation, GE class]
    B -->|No| D{Need explicit welfare interpretation?}
    D -->|Yes| E[Use Atkinson index, choose epsilon explicitly]
    D -->|No| F{Focus on distribution tail?}
    F -->|Bottom / poverty| G[Use GE(0), Atkinson with high epsilon, or FGT poverty indices]
    F -->|Top / concentration| H[Use tax-record top income shares]
    F -->|General/headline reporting| I[Use standard Gini coefficient]
    C --> J[Report alongside Lorenz curve and check for crossing]
    E --> J
    G --> J
    H --> J
    I --> J
```

**Related Topics**

- Lorenz Curve and Gini Coefficient (this chapter)
- Foster-Greer-Thorbecke Poverty Indices
- Top Income Shares and the Piketty-Saez-Zucman Distributional National Accounts Approach
- Social Welfare Functions and Inequality Aversion in Optimal Taxation
- Percentile Ratios (P90/P10, P90/P50, P50/P10) as Alternative Dispersion Measures
- Absolute versus Relative Inequality Concepts in Growth-Inequality Debates
- Tax-Benefit Incidence and Redistribution Decomposition Methods