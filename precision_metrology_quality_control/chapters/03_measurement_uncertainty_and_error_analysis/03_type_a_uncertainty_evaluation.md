## Type A Uncertainty Evaluation


### Overview

**Type A evaluation** is one of two methods defined by the GUM (JCGM 100:2008) for evaluating a standard uncertainty component, characterized specifically by the use of **statistical analysis of a series of observations**. It is the method most directly connected to classical statistics — computing standard deviations, standard deviations of the mean, and, where regression is involved, standard errors of fitted parameters — applied to repeated measurements obtained under defined conditions.

### Formal Definition

Per the GUM, Type A evaluation is the method of evaluating a standard uncertainty by the statistical analysis of a series of observations. It contrasts directly with Type B evaluation, which uses means other than statistical analysis of repeated observations (covered separately).

**Key Points**

- Requires *actual repeated measurements* under the relevant conditions — it is not a method one can apply from a specification sheet or calibration certificate alone.
- The underlying assumption is that random variations in repeated observations of the same measurand, under the same conditions, follow a probability distribution (most commonly modeled as approximately normal) whose parameters can be estimated from the sample data.
- Because it is grounded in observed data, Type A evaluation is often considered to carry a degree of empirical directness that Type B evaluation (relying on external information, judgment, or assumed distributions) does not.

### The Basic Statistical Procedure

**Step 1 — Sample mean**: For $n$ independent repeated observations $q_1,q_2,\ldots,q_n$ of a quantity $q$, the best estimate of the quantity's value is the arithmetic mean:

$$\bar{q}=\frac{1}{n}\sum_{k=1}^{n}q_k$$

**Step 2 — Experimental standard deviation**: The dispersion of individual observations about the mean is quantified by the **experimental standard deviation** $s(q_k)$:

$$s(q_k)=\sqrt{\frac{1}{n-1}\sum_{k=1}^{n}(q_k-\bar{q})^2}$$

**Step 3 — Standard uncertainty of the mean**: Since $\bar{q}$, not an individual $q_k$, is typically used as the measurement result, the relevant standard uncertainty is the **experimental standard deviation of the mean**:

$$u(\bar{q})=s(\bar{q})=\frac{s(q_k)}{\sqrt{n}}$$

**Key Points**

- $u(\bar{q})$, not $s(q_k)$ itself, is the Type A standard uncertainty contribution to be used in the combined uncertainty calculation, since it is the mean value that serves as the best estimate of the measurand.
- $u(\bar{q})$ decreases as $1/\sqrt{n}$ — doubling the number of observations reduces this uncertainty component by a factor of $\sqrt{2}\approx1.41$, illustrating diminishing returns from simply increasing $n$.

**Example**

Ten repeated measurements of a gauge block's length (in mm) are: 25.0011, 25.0009, 25.0013, 25.0010, 25.0012, 25.0008, 25.0011, 25.0010, 25.0009, 25.0012.

- Mean: $\bar{q}=25.00105$ mm
- Experimental standard deviation: $s(q_k)\approx0.00151$ mm
- Standard uncertainty of the mean: $u(\bar{q})=0.00151/\sqrt{10}\approx0.00048$ mm

### Degrees of Freedom

**Key Points**

- The **degrees of freedom** $\nu$ associated with a Type A evaluation from $n$ independent observations is $\nu=n-1$.
- Degrees of freedom quantify the reliability of the estimated standard deviation itself — a Type A evaluation based on very few observations (small $n$, low $\nu$) produces a less reliable estimate of $u(\bar{q})$ than one based on many observations.
- Degrees of freedom are essential input to the **Welch-Satterthwaite formula**, used to compute the effective degrees of freedom of the combined uncertainty when multiple uncertainty components (Type A and Type B) with different reliabilities are combined, which in turn determines the appropriate Student's t-value for computing expanded uncertainty at low sample sizes.

### When Repeated Observations Are Correlated or Limited

**Key Points**

- The basic formula above assumes the $n$ observations are **statistically independent**. If observations are correlated (e.g., consecutive readings affected by a slowly drifting environmental condition), the simple $s(q_k)/\sqrt{n}$ formula can understate the true uncertainty, and more advanced techniques (e.g., accounting for autocorrelation) may be needed.
- Where only a very limited number of observations is practical (e.g., $n=2$ or $n=3$), the resulting Type A estimate has very low degrees of freedom and correspondingly high statistical unreliability — in such cases, a **pooled estimate of standard deviation**, using a larger historical dataset from the same or a similar measurement process (established via a prior, more extensive characterization study), is often preferred over a Type A evaluation from the limited current dataset alone.
- **Pooled standard deviation** across $m$ prior data sets, each with $n_i$ observations and standard deviation $s_i$:

$$s_{pooled}=\sqrt{\frac{\sum_{i=1}^{m}(n_i-1)s_i^2}{\sum_{i=1}^{m}(n_i-1)}}$$

with substantially higher effective degrees of freedom than any single small dataset, improving the reliability of the resulting Type A-derived uncertainty estimate.

### Diagram: Type A Evaluation Workflow

```mermaid
flowchart TD
    A[Take n Repeated Observations<br/>Under Defined Conditions] --> B[Calculate Sample Mean q̄]
    B --> C[Calculate Experimental<br/>Standard Deviation s(qk)]
    C --> D{Sufficient n<br/>for reliable estimate?}
    D -->|Yes, n reasonably large| E[Calculate Standard Uncertainty<br/>of the Mean: u(q̄) = s(qk)/√n]
    D -->|No, n very small| F[Consider Pooled Standard Deviation<br/>from Historical/Larger Dataset]
    F --> E
    E --> G[Degrees of Freedom: ν = n-1]
    G --> H[Use as Type A Component<br/>in Combined Uncertainty Budget]
```

### Diagram: Effect of Sample Size on Uncertainty of the Mean (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 320">
<rect x="0" y="0" width="680" height="320" fill="#ffffff" />
<text x="340" y="24" font-size="16" font-weight="bold" text-anchor="middle" fill="#111111">u(q̄) Decreases as 1/√n (svg_diagram)</text>
<line x1="60" y1="260" x2="620" y2="260" stroke="#333333" stroke-width="1.5" />
<line x1="60" y1="260" x2="60" y2="50" stroke="#333333" stroke-width="1.5" />
<text x="340" y="295" font-size="11" text-anchor="middle" fill="#111111">Number of observations, n</text>
<text x="25" y="155" font-size="11" text-anchor="middle" fill="#111111" transform="rotate(-90 25 155)">u(q̄)</text>
<path d="M 80,60 Q 150,140 250,190 T 420,225 T 600,240" fill="none" stroke="#4285f4" stroke-width="2.5" />
<circle cx="100" cy="75" r="4" fill="#ea4335" />
<text x="100" y="60" font-size="9" text-anchor="middle" fill="#111111">n=2</text>
<circle cx="220" cy="175" r="4" fill="#ea4335" />
<text x="220" y="160" font-size="9" text-anchor="middle" fill="#111111">n=10</text>
<circle cx="400" cy="220" r="4" fill="#ea4335" />
<text x="400" y="205" font-size="9" text-anchor="middle" fill="#111111">n=30</text>
<circle cx="580" cy="238" r="4" fill="#ea4335" />
<text x="580" y="223" font-size="9" text-anchor="middle" fill="#111111">n=100</text>

<text x="340" y="315" font-size="9" text-anchor="middle" fill="`#666666`">Diminishing returns: doubling n only reduces u(q̄) by factor √2</text>

</svg>

### Type A vs. Type B: A Direct Comparison

| Aspect | Type A | Type B |
| --- | --- | --- |
| Basis | Statistical analysis of repeated observations | Any other valid means (spec sheets, certificates, judgment) |
| Requires new data collection? | Yes | No — often uses existing documented information |
| Typical formula | $u(\bar{q})=s(q_k)/\sqrt{n}$ | Depends on assumed distribution (rectangular, triangular, normal) |
| Degrees of freedom | $\nu=n-1$ (finite, quantifiable) | Often treated as $\nu\to\infty$ unless otherwise justified |
| Example source | Ten repeat gauge block readings | Manufacturer's stated accuracy specification |

### Application to Precision Metrology & QC

- **Repeatability studies**: The most direct application of Type A evaluation is quantifying instrument or process repeatability — a series of repeated measurements on a stable reference item under fixed conditions, directly yielding a Type A standard uncertainty component.
- **Calibration laboratory practice**: When a calibration procedure specifies a minimum number of repeat readings at each calibration point (common in ISO/IEC 17025-accredited procedures), the resulting standard deviation of the mean is reported as a Type A component in the certificate's overall uncertainty budget.
- **Gauge R&R linkage**: While Gauge R&R (MSA) studies use their own dedicated ANOVA methodology, the underlying repeatability and reproducibility standard deviations they produce are conceptually Type A evaluations and can be incorporated into a broader GUM-based uncertainty analysis.
- **Process capability studies**: Statistical process control and process capability analysis rely on the same underlying statistical machinery (sample mean, standard deviation) as Type A uncertainty evaluation, though applied to process output variation rather than strictly to measurement system uncertainty.

### Common Pitfalls

- Using the experimental standard deviation $s(q_k)$ of individual observations, rather than the standard deviation of the mean $u(\bar{q})=s(q_k)/\sqrt{n}$, as the Type A uncertainty contribution — this is a very common error that substantially overstates the reported measurement uncertainty when the mean of multiple readings is the reported result.
- Performing a Type A evaluation with too few observations (e.g., $n=2$ or $3$) and treating the resulting estimate as equally reliable as one derived from a larger, well-established dataset — low degrees of freedom should be explicitly propagated through the Welch-Satterthwaite calculation rather than ignored.
- Assuming repeated observations are always statistically independent — if a slowly varying environmental effect (e.g., gradual temperature drift during a measurement session) correlates successive readings, the simple standard-deviation-of-the-mean formula can understate the true random uncertainty.
- Conflating a Type A evaluation of repeatability (short-term, same conditions) with a full characterization of reproducibility (varying operators, instruments, or time) — a Type A evaluation strictly reflects the conditions under which the repeated observations were actually taken.

### Related Topics

- The Guide to the Expression of Uncertainty in Measurement (GUM)
- Type B Uncertainty Evaluation
- Repeatability and Reproducibility
- Sources of Measurement Error
- Welch-Satterthwaite Formula and Effective Degrees of Freedom
- Gauge Repeatability and Reproducibility (Gauge R&R) Studies