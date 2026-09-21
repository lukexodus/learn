## The Guide to the Expression of Uncertainty in Measurement


### Overview

The **Guide to the Expression of Uncertainty in Measurement (GUM)**, published by the Joint Committee for Guides in Metrology (JCGM) as JCGM 100:2008, is the internationally accepted foundational document establishing a consistent, rigorous methodology for evaluating and expressing measurement uncertainty. Originally issued in 1993 (corrected and reprinted in 1995, with the current 2008 edition), the GUM underpins virtually all modern uncertainty statements in calibration certificates, test reports, and metrology practice worldwide, and is the normative reference behind ISO/IEC 17025's uncertainty requirements.

### Purpose and Scope

**Key Points**

- Establishes general rules for evaluating and expressing uncertainty across a broad range of measurements, from industrial calibration to fundamental scientific metrology.
- Replaces the older, less consistent classical approach of separately reporting "systematic error" and "random error" (or "accuracy" as a single figure) with a unified, statistically defensible framework centered on the concept of a **probability distribution** for the true value of the measurand.
- Provides the conceptual basis for internationally harmonized uncertainty reporting, enabling meaningful comparison of measurement results between different laboratories, countries, and disciplines.

### Core Philosophy: Uncertainty as a Parameter of a Distribution

**Key Points**

- Rather than treating "error" as a single unknowable quantity, the GUM treats the measurand's true value as characterized by a probability distribution, and **uncertainty** as a parameter (specifically, a standard deviation or a multiple thereof) characterizing the dispersion of values that could reasonably be attributed to the measurand.
- This shift in perspective allows uncertainty from fundamentally different sources — repeated observations (statistical) and non-statistical information (specifications, calibration certificates, physical constants, expert judgment) — to be combined within a single coherent mathematical framework.

### Type A and Type B Evaluation

The GUM's central methodological innovation is classifying uncertainty components by *how they are evaluated*, not by whether they are "random" or "systematic" in the classical sense.

**Key Points**

- **Type A evaluation**: Evaluation of uncertainty by statistical analysis of a series of observations — e.g., the standard deviation of repeated measurements, or the standard deviation of the mean.
- **Type B evaluation**: Evaluation of uncertainty by means other than statistical analysis of repeated observations — e.g., manufacturer specifications, calibration certificate data, published reference data, physical reasoning, or expert judgment applied to assumed probability distributions.
- Both Type A and Type B components are expressed as **standard uncertainties** (equivalent to one standard deviation) and are combined identically in subsequent calculations — the classification describes the *evaluation method*, not the *nature* of the underlying error.

**Example**

Ten repeated readings of a gauge block yield a standard deviation of the mean of 0.0003 mm — a Type A evaluation. The gauge block's calibration certificate states an expanded uncertainty of 0.0005 mm at $k=2$, yielding a standard uncertainty of 0.00025 mm — a Type B evaluation, since it derives from documentary evidence rather than the operator's own repeated observations.

### The Uncertainty Evaluation Process (Step by Step)

```mermaid
flowchart TD
    A[Define the Measurand<br/>and Measurement Model<br/>Y = f(X1, X2, ..., Xn)] --> B[Identify All Input Quantities<br/>Xi Contributing to Y]
    B --> C[Evaluate Standard Uncertainty<br/>u(Xi) for Each Input]
    C --> D[Type A: Statistical Analysis<br/>of Repeated Observations]
    C --> E[Type B: Specifications, Certificates,<br/>Reference Data, Judgment]
    D --> F[Determine Sensitivity Coefficients<br/>ci = ∂f/∂Xi]
    E --> F
    F --> G[Combine via Law of<br/>Propagation of Uncertainty]
    G --> H[Combined Standard<br/>Uncertainty uc(y)]
    H --> I[Apply Coverage Factor k<br/>Typically k=2 for ~95% confidence]
    I --> J[Report Expanded<br/>Uncertainty U = k·uc(y)]
```

### The Measurement Model and Law of Propagation of Uncertainty

**Key Points**

- The GUM requires an explicit **measurement model**, $Y=f(X_1,X_2,\ldots,X_n)$, relating the output quantity $Y$ (the measurand) to the input quantities $X_i$ upon which it depends.
- The **combined standard uncertainty** $u_c(y)$ is calculated using the law of propagation of uncertainty (a first-order Taylor series approximation):

$$u_c^2(y)=\sum_{i=1}^{n}\left(\frac{\partial f}{\partial X_i}\right)^2u^2(x_i)+2\sum_{i=1}^{n-1}\sum_{j=i+1}^{n}\frac{\partial f}{\partial X_i}\frac{\partial f}{\partial X_j}u(x_i,x_j)$$

- The partial derivative terms $c_i=\partial f/\partial X_i$ are called **sensitivity coefficients**, quantifying how strongly the output $Y$ responds to a small change in each input $X_i$.
- The second term accounts for **correlation** between input quantities (via covariance $u(x_i,x_j)$); when inputs are uncorrelated, this term vanishes, simplifying to a root-sum-of-squares combination.

**Example**

For the simple case of density $\rho=m/V$, with uncorrelated inputs mass $m$ and volume $V$:

$$u_c(\rho)=\rho\sqrt{\left(\frac{u(m)}{m}\right)^2+\left(\frac{u(V)}{V}\right)^2}$$

illustrating how relative uncertainties combine in quadrature for a simple product/quotient model.

### Coverage Factor and Expanded Uncertainty

**Key Points**

- The **combined standard uncertainty** $u_c(y)$ corresponds to approximately a 68% confidence level (one standard deviation), assuming an approximately normal distribution — generally considered too low a confidence level for most practical reporting purposes.
- The **expanded uncertainty** $U$ is obtained by multiplying the combined standard uncertainty by a **coverage factor** $k$:

$$U=k\cdot u_c(y)$$

- $k=2$ is the most commonly used coverage factor, corresponding to approximately a 95% confidence level under a normal (Gaussian) distribution assumption; $k=3$ corresponds to approximately 99%.
- For cases where the effective degrees of freedom are low (few observations contributing to Type A components) or the combined distribution deviates significantly from normal, the **Welch-Satterthwaite formula** is used to compute effective degrees of freedom, and a Student's t-distribution value is used in place of the simple $k=2$ approximation for rigorous confidence-level determination.

### Common Type B Probability Distribution Assumptions

| Information Available | Assumed Distribution | Standard Uncertainty Formula |
| --- | --- | --- |
| Instrument resolution, ± half-width $a$ | Rectangular | $u=a/\sqrt{3}$ |
| Manufacturer spec, ± limits with no further info | Rectangular | $u=a/\sqrt{3}$ |
| Calibration certificate, expanded uncertainty $U$ at coverage factor $k$ | (typically Normal) | $u=U/k$ |
| Triangular-shaped confidence (e.g., sum of two uniform effects) | Triangular | $u=a/\sqrt{6}$ |

**Key Points**

- The choice of assumed distribution shape reflects the *state of knowledge* about the input quantity, not necessarily its true underlying physical distribution — this is a Bayesian-influenced aspect of the GUM's philosophy.
- Where only upper and lower bounds are known with no additional information favoring any value within that range, a **rectangular (uniform) distribution** is the standard, conservative default assumption.

### Diagram: Combining Uncertainty Components (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 300">
<rect x="0" y="0" width="700" height="300" fill="#ffffff" />
<text x="350" y="24" font-size="16" font-weight="bold" text-anchor="middle" fill="#111111">Combined Standard Uncertainty from Multiple Sources (svg_diagram)</text>
<rect x="30" y="60" width="140" height="50" rx="5" fill="#e8f0fe" stroke="#4285f4" />
<text x="100" y="80" font-size="10" text-anchor="middle" fill="#111111">Type A: u(x₁)</text>
<text x="100" y="95" font-size="9" text-anchor="middle" fill="#333333">Repeatability study</text>
<rect x="190" y="60" width="140" height="50" rx="5" fill="#fef7e0" stroke="#f9ab00" />
<text x="260" y="80" font-size="10" text-anchor="middle" fill="#111111">Type B: u(x₂)</text>
<text x="260" y="95" font-size="9" text-anchor="middle" fill="#333333">Calibration certificate</text>
<rect x="350" y="60" width="140" height="50" rx="5" fill="#fce8e6" stroke="#ea4335" />
<text x="420" y="80" font-size="10" text-anchor="middle" fill="#111111">Type B: u(x₃)</text>
<text x="420" y="95" font-size="9" text-anchor="middle" fill="#333333">Resolution (rectangular)</text>
<rect x="510" y="60" width="140" height="50" rx="5" fill="#f3e8fd" stroke="#a142f4" />
<text x="580" y="80" font-size="10" text-anchor="middle" fill="#111111">Type B: u(x₄)</text>
<text x="580" y="95" font-size="9" text-anchor="middle" fill="#333333">Environmental effect</text>
<rect x="220" y="160" width="260" height="60" rx="6" fill="#e6f4ea" stroke="#34a853" />
<text x="350" y="185" font-size="11" font-weight="bold" text-anchor="middle" fill="#111111">Combined Standard Uncertainty</text>
<text x="350" y="203" font-size="10" text-anchor="middle" fill="#333333">uc(y) = √(Σ ci²u²(xi))</text>
<line x1="100" y1="110" x2="300" y2="160" stroke="#999999" stroke-width="1" />
<line x1="260" y1="110" x2="330" y2="160" stroke="#999999" stroke-width="1" />
<line x1="420" y1="110" x2="380" y2="160" stroke="#999999" stroke-width="1" />
<line x1="580" y1="110" x2="420" y2="160" stroke="#999999" stroke-width="1" />
<rect x="250" y="250" width="200" height="40" rx="6" fill="#fef7e0" stroke="#f9ab00" />
<text x="350" y="275" font-size="10" text-anchor="middle" fill="#111111">Expanded Uncertainty: U = k·uc(y)</text>
<line x1="350" y1="220" x2="350" y2="250" stroke="#999999" stroke-width="1" />
</svg>

### Reporting Requirements

**Key Points**

- A complete GUM-compliant measurement result reports the value, the expanded uncertainty, the coverage factor used, and the approximate confidence level, in a form such as: "$L=(100.021\pm0.010)$ mm, where the reported uncertainty is an expanded uncertainty calculated using a coverage factor $k=2$, providing a level of confidence of approximately 95%."
- Related documents extend or complement the core GUM: **JCGM 101** (Supplement 1, Monte Carlo method for uncertainty propagation, useful for nonlinear models or non-normal distributions), **JCGM 102** (Supplement 2, models with multiple output quantities), and the **VIM** (JCGM 200), which provides the vocabulary underpinning GUM terminology.

### Application to Precision Metrology & QC

- **Calibration certificates**: Virtually all modern calibration certificates from accredited laboratories report expanded uncertainty computed per GUM methodology, as required by ISO/IEC 17025.
- **Conformity assessment**: GUM-derived uncertainty values feed directly into pass/fail decision rules (e.g., per ISO 14253-1) for determining whether a measured value demonstrates conformance to a specification, accounting for the risk introduced by measurement uncertainty near tolerance boundaries.
- **Gauge R&R and MSA integration**: While Gauge R&R studies use a distinct ANOVA/Average-Range statistical framework, their output (repeatability and reproducibility standard deviations) can be incorporated as Type A uncertainty components within an overall GUM uncertainty budget.
- **Laboratory accreditation**: ISO/IEC 17025 explicitly requires laboratories to identify all significant components of uncertainty and evaluate them using either Type A or Type B methods consistent with GUM principles, making GUM literacy a core competency for calibration and testing laboratory personnel.

### Common Pitfalls

- Treating Type A as synonymous with "random error" and Type B as synonymous with "systematic error" — the GUM classification concerns *evaluation method*, not error nature; a Type B evaluation can characterize what would classically be called a random effect (e.g., resolution), and vice versa.
- Applying $k=2$ universally without checking whether the effective degrees of freedom are sufficiently large (typically requiring the Welch-Satterthwaite calculation and a Student's t-value for small sample sizes) — using $k=2$ with very few Type A observations can understate the true 95% confidence interval.
- Omitting correlation/covariance terms between input quantities when they are not actually independent (e.g., the same reference standard used to calibrate two different input measurements), leading to an incorrect combined uncertainty.
- Confusing the standard uncertainty $u(x_i)$ (one standard deviation) with the expanded uncertainty $U$ (typically two standard deviations) when combining components — all inputs to the law of propagation of uncertainty must be expressed as standard uncertainties, not expanded uncertainties.

### Related Topics

- Sources of Measurement Error
- Systematic, Random, and Gross Errors
- Type A and Type B Uncertainty Evaluation
- Measurement Decision Risk and Conformity Assessment (ISO 14253-1)
- International Vocabulary of Metrology (VIM)
- Monte Carlo Methods for Uncertainty Propagation (JCGM 101)