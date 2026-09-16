## Process Capability Indices: Cp and Cpk

### Overview

**Key Points**

- Process capability indices are statistical measures that compare the **natural variation of a process** (its "voice") against the **customer's specification limits** (the "voice of the customer") to quantify how well a process can consistently produce output within acceptable bounds.
- $C_p$ (process capability) measures potential capability — whether the process spread is narrow enough to fit within specifications, *ignoring* whether the process is centered.
- $C_{pk}$ (process capability index, centered) measures actual capability — accounting for both spread *and* how well the process mean is centered relative to the specification limits.
- Capability analysis is only statistically meaningful once the process has been confirmed to be in a **state of statistical control** (only common cause variation present), typically verified via control charts before capability indices are calculated.

### Prerequisites for Valid Capability Analysis

Before calculating $C_p$ or $C_{pk}$, the following conditions should generally hold:

1. **Statistical control**: The process must show no special cause variation (verified via X-bar/R, X-bar/S, or individuals charts).
2. **Approximate normality**: The standard $C_p$/$C_{pk}$ formulas assume the underlying process output follows an approximately normal distribution. For non-normal data, transformation methods or alternative capability metrics may be required.
3. **Sufficient sample size**: A reasonably large, representative sample (commonly cited minimums range from 30 to 100+ data points) is needed to obtain a stable estimate of $\sigma$.
4. **Defined specification limits**: An Upper Specification Limit ($USL$) and/or Lower Specification Limit ($LSL$) must be established by engineering requirements or customer needs — these are distinct from statistically derived control limits.

**Key Points**

- Calculating $C_p$/$C_{pk}$ on a process that is not in statistical control is a common and serious analytical error [Inference] — the estimated $\sigma$ would reflect an unstable, shifting distribution rather than a single consistent process state, making the resulting index unreliable and potentially misleading.

### Cp: Process Capability Index

#### Formula

$$C_p = \frac{USL - LSL}{6\sigma}$$

The numerator ($USL - LSL$) represents the width of the specification "window" — the tolerance the customer allows. The denominator ($6\sigma$) represents the natural process spread, based on the common convention that approximately 99.73% of a normal distribution falls within $\pm 3\sigma$ of the mean.

#### Interpretation

$C_p$ answers: **"If the process were perfectly centered, would its natural variation fit inside the specification limits?"** It says nothing about actual centering.

| $C_p$ Value | Interpretation |
| --- | --- |
| $C_p < 1.00$ | Process spread exceeds specification width — incapable, even if perfectly centered |
| $C_p = 1.00$ | Process spread exactly matches spec width — marginally capable, no margin for error |
| $1.00 \leq C_p < 1.33$ | Adequate but requires tight control; commonly considered marginal |
| $C_p \geq 1.33$ | Generally considered capable (traditional industry threshold) |
| $C_p \geq 1.67$ | Often required for critical characteristics (e.g., automotive, aerospace) |
| $C_p \geq 2.00$ | Associated with "Six Sigma" capability level |

[Unverified] Specific threshold conventions (1.33, 1.67, 2.00) vary by industry, customer requirements, and standard referenced (e.g., AIAG, ISO); these figures represent commonly cited industry benchmarks rather than universal statistical requirements.

### Cpk: Process Capability Index (Centered)

#### Formula

$$C_{pk} = \min\left(\frac{USL - \bar{x}}{3\sigma}, \; \frac{\bar{x} - LSL}{3\sigma}\right)$$

This calculates capability toward each specification limit separately and takes the smaller (more restrictive) value — the process is only as capable as its worst-performing side.

#### Interpretation

$C_{pk}$ answers: **"Given where the process is actually centered right now, does its variation fit inside the specification limits?"**

- $C_{pk} \leq C_p$ always holds; the two are equal only when the process mean is exactly centered between $USL$ and $LSL$.
- A large gap between $C_p$ and $C_{pk}$ signals a **centering problem**: the process has enough inherent precision to be capable, but it is off-target.
- A negative $C_{pk}$ indicates the process mean has moved *outside* one of the specification limits entirely.

### Worked Example

**Example**

A machining process cuts shaft diameters with specifications $LSL = 24.90$ mm and $USL = 25.10$ mm (a tolerance width of 0.20 mm). Sampling confirms the process is in statistical control, with:

$$\bar{x} = 25.03 \text{ mm}, \qquad \sigma = 0.025 \text{ mm}$$

**Step 1 — Calculate $C_p$:**

$$C_p = \frac{25.10 - 24.90}{6 \times 0.025} = \frac{0.20}{0.15} = 1.33$$

This suggests that *if perfectly centered*, the process would be considered capable by the traditional 1.33 threshold.

**Step 2 — Calculate $C_{pk}$:**

$$C_{pk} = \min\left(\frac{25.10 - 25.03}{3 \times 0.025}, \; \frac{25.03 - 24.90}{3 \times 0.025}\right) = \min\left(\frac{0.07}{0.075}, \; \frac{0.13}{0.075}\right) = \min(0.933, \; 1.733) = 0.933$$

**Interpretation**: Despite $C_p = 1.33$ suggesting adequate potential capability, $C_{pk} = 0.933$ reveals the process is actually **not capable** as currently centered — it is shifted too close to the upper specification limit. The gap between $C_p$ (1.33) and $C_{pk}$ (0.933) is diagnostic: it points to a **centering issue**, not a precision (spread) issue. The corrective action here is to re-center the process mean closer to the midpoint (25.00 mm) — for example, adjusting a machine offset — rather than trying to reduce variation.

### Visualizing Cp vs Cpk (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 720 380">
<text x="360" y="22" text-anchor="middle" font-size="15" font-weight="bold" fill="#1a1a1a">Cp vs Cpk: Spread and Centering (svg_diagram)</text>


<text x="20" y="55" font-size="12" font-weight="bold" fill="`#1a1a1a`">Off-center process: Cp high, Cpk low</text>

<line x1="70" y1="130" x2="680" y2="130" stroke="#333" stroke-width="1" />

<line x1="150" y1="60" x2="150" y2="140" stroke="`#c0392b`" stroke-width="1.5" />

<text x="130" y="55" font-size="10" fill="`#c0392b`">LSL</text>

<line x1="450" y1="60" x2="450" y2="140" stroke="`#c0392b`" stroke-width="1.5" />

<text x="440" y="55" font-size="10" fill="`#c0392b`">USL</text>

<path d="M 330 130 C 340 60, 400 60, 410 130 Z" fill="`#3498db`" opacity="0.4" stroke="`#2c3e50`" stroke-width="1.5" />

<line x1="370" y1="130" x2="370" y2="65" stroke="#555" stroke-width="1" stroke-dasharray="3,2" />

<text x="355" y="60" font-size="9" fill="#555">x̄</text>



<text x="20" y="200" font-size="12" font-weight="bold" fill="`#1a1a1a`">Centered process: Cp ≈ Cpk (both good)</text>

<line x1="70" y1="270" x2="680" y2="270" stroke="#333" stroke-width="1" />

<line x1="150" y1="200" x2="150" y2="280" stroke="`#c0392b`" stroke-width="1.5" />

<text x="130" y="195" font-size="10" fill="`#c0392b`">LSL</text>

<line x1="450" y1="200" x2="450" y2="280" stroke="`#c0392b`" stroke-width="1.5" />

<text x="440" y="195" font-size="10" fill="`#c0392b`">USL</text>

<path d="M 250 270 C 260 200, 340 200, 350 270 Z" fill="`#27ae60`" opacity="0.4" stroke="`#2c3e50`" stroke-width="1.5" />

<line x1="300" y1="270" x2="300" y2="205" stroke="#555" stroke-width="1" stroke-dasharray="3,2" />

<text x="285" y="200" font-size="9" fill="#555">x̄</text>



<text x="20" y="335" font-size="12" font-weight="bold" fill="`#1a1a1a`">Incapable process: Cp low (spread too wide)</text>

<line x1="70" y1="360" x2="680" y2="360" stroke="#333" stroke-width="1" />

<line x1="150" y1="290" x2="150" y2="370" stroke="`#c0392b`" stroke-width="1.5" />

<line x1="450" y1="290" x2="450" y2="370" stroke="`#c0392b`" stroke-width="1.5" />

<path d="M 100 360 C 130 290, 470 290, 500 360 Z" fill="`#e74c3c`" opacity="0.3" stroke="`#2c3e50`" stroke-width="1.5" />

</svg>

### Relationship Between Cp, Cpk, and Process Yield

Assuming normality, capability indices relate directly to expected nonconformance rates (defects outside specification):

| $C_{pk}$ | Approx. Defect Rate (one-sided) | Approx. DPMO (one-sided) |
| --- | --- | --- |
| 0.67 | ~2.28% | ~22,700 |
| 1.00 | ~0.135% | ~1,350 |
| 1.33 | ~0.0032% | ~32 |
| 1.67 | ~0.00003% | ~0.3 |
| 2.00 | ~0.0000001% | ~0.002 |

[Inference] These figures assume a perfectly normal distribution with no long-term process drift; the well-known "1.5 sigma shift" adjustment used in Six Sigma methodology (where long-term $C_{pk}$ of 1.5 is treated as equivalent to 3.4 DPMO, i.e., "Six Sigma quality") accounts for realistic drift over time and produces different DPMO figures than the pure short-term normal distribution calculation shown above.

### Related and Extended Indices

| Index | Formula | Distinguishing Feature |
| --- | --- | --- |
| $C_p$ | $\dfrac{USL-LSL}{6\sigma}$ | Potential capability; ignores centering |
| $C_{pk}$ | $\min\left(\dfrac{USL-\bar{x}}{3\sigma}, \dfrac{\bar{x}-LSL}{3\sigma}\right)$ | Actual capability; accounts for centering |
| $P_p$ | $\dfrac{USL-LSL}{6s}$ | "Performance" version using overall (long-term) sample standard deviation $s$ instead of within-subgroup $\sigma$ |
| $P_{pk}$ | Same as $C_{pk}$ formula, using overall $s$ | Long-term performance, centering included |
| $C_{pm}$ | $\dfrac{USL-LSL}{6\sqrt{\sigma^2 + (\bar{x}-T)^2}}$ | "Taguchi index"; penalizes deviation from a target value $T$, not just from the spec limits |

**Key Points**

- The distinction between $C_p$/$C_{pk}$ (using **within-subgroup** variation, estimated typically via $\bar{R}/d_2$ from control chart data) and $P_p$/$P_{pk}$ (using **overall** sample standard deviation across all data) is a frequent source of confusion: $C_p$/$C_{pk}$ represent short-term, potential capability, while $P_p$/$P_{pk}$ represent long-term, actual performance including between-subgroup variation.
- When a process is well-controlled with minimal shift over time, $C_{pk}$ and $P_{pk}$ converge; a large divergence suggests instability between subgroups even if each subgroup individually looks fine.

### Common Pitfalls

- **One-sided specifications**: When only $USL$ or only $LSL$ applies (not both), $C_p$ cannot be calculated in its standard two-sided form; a one-sided capability index ($C_{pu}$ or $C_{pl}$) is used instead:

$$C_{pu} = \frac{USL - \bar{x}}{3\sigma}, \qquad C_{pl} = \frac{\bar{x} - LSL}{3\sigma}$$

- **Non-normal data**: Applying the standard formulas to skewed or non-normal distributions (common in cycle-time, particle-count, or failure-rate data) can produce misleading capability estimates. [Inference] Common remedies include applying a normalizing transformation (e.g., Box-Cox) before calculating indices, or using distribution-specific capability metrics designed for the actual underlying distribution.
- **Confusing control limits with specification limits**: Control limits ($UCL$/$LCL$ on a control chart) are calculated *from the process itself* and describe what the process naturally does; specification limits ($USL$/$LSL$) are set *externally* by customer or engineering requirements and describe what is desired. A process can be in perfect statistical control while still being incapable of meeting specifications.

### Next Steps

- Process performance indices: $P_p$ and $P_{pk}$ (long-term vs. short-term capability)
- Taguchi's loss function and the $C_{pm}$ index
- Non-normal process capability analysis (Box-Cox transformation, distribution fitting)
- Six Sigma DPMO and sigma level calculations, including the 1.5-sigma shift convention
- Measurement system analysis (Gage R&R) as a prerequisite for trustworthy capability studies
- Determining appropriate sample size and sampling strategy for a capability study
- Relationship between control charts, process stability, and capability analysis in the SPC workflow