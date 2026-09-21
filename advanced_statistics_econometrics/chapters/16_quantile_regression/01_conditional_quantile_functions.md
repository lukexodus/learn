## Conditional Quantile Functions

### Overview

The conditional quantile function describes how a specified quantile (percentile) of a response variable's distribution changes as a function of covariates, in contrast to conditional mean functions (as in OLS regression) which describe only the central tendency. Conditional quantile functions are the theoretical foundation underlying quantile regression, and they allow a far richer characterization of how covariates affect the entire conditional distribution of $Y$ given $X$ — not merely its average.

### Definition

**Unconditional Quantile**

For a random variable $Y$ with cumulative distribution function (CDF) $F_Y(y) = P(Y \le y)$, the $\tau$-th quantile ($\tau \in (0,1)$) is defined as:

$$Q_Y(\tau) = \inf\{y : F_Y(y) \ge \tau\}$$

For continuous, strictly increasing $F_Y$, this simplifies to $Q_Y(\tau) = F_Y^{-1}(\tau)$.

**Conditional Quantile Function**

Given covariates $X = x$, the conditional CDF is $F_{Y|X}(y \mid x) = P(Y \le y \mid X = x)$, and the conditional quantile function is:

$$Q_{Y|X}(\tau \mid x) = \inf\{y : F_{Y|X}(y \mid x) \ge \tau\}$$

This is a function of both $\tau$ and $x$: for each fixed $\tau$, it traces out a surface (or, with a single continuous regressor, a curve) describing how the $\tau$-th percentile of $Y$'s conditional distribution moves with $x$.

**Key Points**

- $\tau = 0.5$ gives the **conditional median function**
- $\tau = 0.1$ and $\tau = 0.9$ describe the lower and upper tails of the conditional distribution
- Unlike the conditional mean $E[Y \mid X=x]$, which is a single function, the conditional quantile function is a **family of functions indexed by $\tau$** — one for every percentile of interest

### Linear Conditional Quantile Model

The most common parametric specification assumes the $\tau$-th conditional quantile is linear in covariates:

$$Q_{Y|X}(\tau \mid x) = x'\beta(\tau)$$

Crucially, the coefficient vector $\beta(\tau)$ is allowed to **vary with $\tau$**. This is the central conceptual departure from OLS: rather than one $\beta$ describing the average effect, there is potentially a distinct $\beta(\tau)$ for every quantile, permitting covariates to have different effects on different parts of $Y$'s distribution (e.g., a training program might raise low-wage workers' median wage substantially but have little effect on high earners).

### Properties of Conditional Quantile Functions

**Equivariance to Monotonic Transformations**

If $h(\cdot)$ is a monotonically increasing function, then:

$$Q_{h(Y)|X}(\tau \mid x) = h\big(Q_{Y|X}(\tau \mid x)\big)$$

This is a key advantage over conditional mean functions, which do **not** commute with nonlinear transformations in general ($E[\ln Y] \ne \ln E[Y]$). Quantiles of $\ln Y$ are simply the log of the quantiles of $Y$, which is convenient in applications using log-transformed outcomes (e.g., wages, income).

**Monotonicity in $\tau$**

By construction, for $\tau_1 < \tau_2$:

$$Q_{Y|X}(\tau_1 \mid x) \le Q_{Y|X}(\tau_2 \mid x)$$

for any fixed $x$. This is the **no-crossing property** that theoretical conditional quantile functions must satisfy. **[Inference]** In finite samples, *estimated* linear quantile regression curves for different $\tau$ can cross at some values of $x$ (a well-documented practical issue, not a violation of the theoretical property itself) — this is addressed by rearrangement methods or by imposing monotonicity restrictions in estimation.

**Robustness to Outliers and Distributional Assumptions**

Conditional quantile functions do not require any distributional assumption on $Y \mid X$ (e.g., normality), and — especially near the median — are more robust to outliers in $Y$ than the conditional mean, since the quantile depends only on the ranking of observations locally around $\tau$, not on the magnitude of extreme values.

### Relationship to the Check (Pinball) Loss Function

The conditional quantile function can be characterized as the minimizer of an asymmetric absolute loss, the **check function** (also called pinball loss):

$$\rho_\tau(u) = u\big(\tau - \mathbb{1}(u < 0)\big) = \begin{cases} \tau \cdot u & \text{if } u \ge 0 \\ (\tau - 1) \cdot u & \text{if } u < 0 \end{cases}$$

The population conditional quantile solves:

$$Q_{Y|X}(\tau \mid x) = \arg\min_{q} \; E\big[\rho_\tau(Y - q) \mid X = x\big]$$

**Key Points**

- At $\tau = 0.5$, $\rho_{0.5}(u) = 0.5|u|$, and the minimizer is the conditional median — recovering the classical fact that the median minimizes expected absolute deviation
- For $\tau \ne 0.5$, the loss is asymmetric: underprediction and overprediction are penalized differently, weighted by $\tau$ and $1-\tau$ respectively
- This population moment condition is the theoretical basis for quantile regression estimation (Koenker and Bassett, 1978), which replaces the population expectation with its sample analog and minimizes over $\beta(\tau)$

### Distributional Decomposition via Conditional Quantiles

Because $Q_{Y|X}(\tau \mid x)$ for $\tau \in (0,1)$ fully characterizes the entire conditional distribution (not just its center), a full family of estimated conditional quantile functions across a fine grid of $\tau$ values can be used to:

- Reconstruct estimates of the entire conditional distribution function $F_{Y|X}(y \mid x)$
- Compute conditional interquantile ranges (e.g., $Q(0.9) - Q(0.1)$) as a measure of conditional dispersion, and examine how this dispersion itself varies with $X$
- Support counterfactual decomposition methods (e.g., Machado-Mata / Melly decompositions) that ask how much of an observed distributional difference between two groups is due to differing covariates versus differing conditional quantile coefficients

### Illustration: Heteroskedasticity and Quantile Functions

A textbook motivating case: suppose $Y = \beta_0 + \beta_1 X + \sigma(X)\varepsilon$ where the error variance depends on $X$ (heteroskedasticity) and $\varepsilon$ has a fixed distribution independent of $X$. Then:

$$Q_{Y|X}(\tau \mid x) = \beta_0 + \beta_1 x + \sigma(x) Q_\varepsilon(\tau)$$

Here, the *slope* of the conditional quantile function with respect to $x$ differs across $\tau$ whenever $\sigma(x)$ is a nonconstant function of $x$: the conditional mean model captures only $\beta_0 + \beta_1 x$, but the conditional quantile functions at different $\tau$ reveal how the entire **spread** of $Y$'s distribution — not just its center — changes with $x$. This is a canonical example of how quantile functions detect and characterize heteroskedasticity/distributional-shape effects invisible to mean regression alone.

### Conditional Quantile Function vs. Conditional Mean Function

| Feature | Conditional Mean $E[Y\mid X]$ | Conditional Quantile $Q_{Y\mid X}(\tau)$ |
| --- | --- | --- |
| Number of functions | One | One per $\tau \in (0,1)$ |
| Sensitivity to outliers | High (squared-error based) | Low, especially near median |
| Equivariant to monotone transforms | No | Yes |
| Captures distributional shape (spread, skew) | No | Yes, across the full range of $\tau$ |
| Standard estimator | OLS (minimizes squared loss) | Quantile regression (minimizes check loss) |
| Requires distributional assumption | No (for consistency of OLS mean) | No |

### Diagram: Conditional Quantile Functions Across τ

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 360">
<text x="320" y="24" font-size="16" font-weight="bold" text-anchor="middle" fill="#222">Conditional Quantile Functions by τ (svg_diagram)</text>
<line x1="60" y1="310" x2="600" y2="310" stroke="#333" stroke-width="2" />
<line x1="60" y1="310" x2="60" y2="50" stroke="#333" stroke-width="2" />
<text x="330" y="340" font-size="13" text-anchor="middle" fill="#333">X (covariate)</text>
<text x="25" y="180" font-size="13" text-anchor="middle" fill="#333" transform="rotate(-90 25 180)">Y</text>

<circle cx="120" cy="260" r="3" fill="#999" />
<circle cx="140" cy="245" r="3" fill="#999" />
<circle cx="160" cy="270" r="3" fill="#999" />
<circle cx="220" cy="230" r="3" fill="#999" />
<circle cx="250" cy="180" r="3" fill="#999" />
<circle cx="270" cy="255" r="3" fill="#999" />
<circle cx="320" cy="150" r="3" fill="#999" />
<circle cx="340" cy="230" r="3" fill="#999" />
<circle cx="360" cy="100" r="3" fill="#999" />
<circle cx="420" cy="120" r="3" fill="#999" />
<circle cx="440" cy="210" r="3" fill="#999" />
<circle cx="460" cy="80" r="3" fill="#999" />
<circle cx="510" cy="180" r="3" fill="#999" />
<circle cx="530" cy="90" r="3" fill="#999" />
<circle cx="560" cy="150" r="3" fill="#999" />

<line x1="80" y1="280" x2="580" y2="255" stroke="#1f77b4" stroke-width="2.5" />
<text x="585" y="258" font-size="11" fill="#1f77b4">Q(0.1)</text>

<line x1="80" y1="255" x2="580" y2="175" stroke="#2ca02c" stroke-width="2.5" />
<text x="585" y="178" font-size="11" fill="#2ca02c">Q(0.5)</text>

<line x1="80" y1="220" x2="580" y2="75" stroke="#d62728" stroke-width="2.5" />
<text x="585" y="78" font-size="11" fill="#d62728">Q(0.9)</text>
</svg>

*Note: the widening "fan" pattern between the $Q(0.1)$ and $Q(0.9)$ lines as $X$ increases illustrates conditional heteroskedasticity — a pattern that the conditional mean line alone would not reveal.*

### Diagram: From Distribution to Quantile Function

```mermaid
flowchart LR
    A["Conditional Distribution F(y given x) (svg_diagram)"] --> B[Invert CDF at level tau]
    B --> C["Q(tau given x) = inf y such that F(y given x) >= tau"]
    C --> D{Vary tau over 0,1}
    D --> E[Q(0.1 given x): lower tail]
    D --> F[Q(0.5 given x): median]
    D --> G[Q(0.9 given x): upper tail]
    E --> H[Family of Conditional Quantile Functions]
    F --> H
    G --> H
    H --> I[Reconstruct full conditional distribution]
    H --> J[Feed into Quantile Regression Estimation]
```

### Worked Example

Suppose modeling log wages as a function of years of education, with conditional quantile functions estimated at $\tau = 0.10, 0.50, 0.90$:

$$Q_{\ln(wage)|educ}(\tau \mid educ) = \beta_0(\tau) + \beta_1(\tau) \cdot educ$$

Suppose the estimated slopes are $\hat{\beta}_1(0.10) = 0.05$, $\hat{\beta}_1(0.50) = 0.08$, $\hat{\beta}_1(0.90) = 0.12$. The interpretation: an additional year of education is associated with a 5% increase in the 10th percentile of the conditional log-wage distribution, an 8% increase in the median, and a 12% increase in the 90th percentile — education raises wages more for already-high earners than for low earners **conditional on the same years of schooling**, a pattern of increasing returns across the conditional wage distribution invisible to a single OLS coefficient on education. **[Inference]** These specific coefficient values are illustrative for pedagogical purposes; actual empirical returns-to-education gradients across quantiles vary by dataset, time period, and country and would need to be estimated from real data.

### Related Topics

- Quantile regression estimation (linear programming formulation, Koenker-Bassett estimator)
- Check (pinball) loss function and its role as an M-estimation criterion
- Quantile crossing problem and rearrangement solutions
- Machado-Mata / Melly counterfactual distributional decomposition
- Conditional vs. unconditional quantile regression (recentered influence functions, Firpo-Fortin-Lemieux)
- Quantile regression standard errors (bootstrap methods, Powell's kernel-based sandwich estimator)
- Heteroskedasticity diagnostics via quantile slope comparisons across τ