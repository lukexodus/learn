## Accuracy, Precision, Resolution, and Sensitivity


### Overview

Accuracy, precision, resolution, and sensitivity are among the most frequently conflated terms in measurement science, yet each describes a distinct property of a measurement system. Per the *International Vocabulary of Metrology* (VIM, JCGM 200), these terms have precise formal definitions that underpin how measurement quality is specified, tested, and reported in metrology and quality control.

### Accuracy

**Trueness + Precision.** Per VIM, *measurement accuracy* is the closeness of agreement between a measured quantity value and the true value of the measurand. It is a qualitative concept — VIM explicitly states accuracy is not a quantity and is not given a numerical value; instead, a measurement is described as "more accurate" or "less accurate."

**Key Points**

- Accuracy encompasses both **trueness** (closeness of agreement between the average of many measurements and the true value — related to systematic error/bias) and **precision** (closeness of agreement between repeated measurements — related to random error).
- A system can be precise but not accurate (tightly clustered results, offset from the true value — indicating bias) or accurate on average but not precise (results scattered around the true value with large random spread).
- In practice, "accuracy" is often loosely used to mean the combination of both trueness and precision — care should be taken to specify which is meant in technical documentation.

### Precision

**Precision** is the closeness of agreement between quantity values obtained by replicate measurements on the same or similar objects under specified conditions (VIM 2.15).

**Key Points**

- Quantified statistically, typically via standard deviation, variance, or coefficient of variation of repeated measurements — *not* via comparison to a true or reference value.
- Precision is qualified by the conditions under which repeatability is assessed:
  - **Repeatability**: precision under a set of conditions that includes the same procedure, operator, instrument, location, and short time period.
  - **Intermediate precision**: conditions that include some variation (e.g., different days, different operators, same lab).
  - **Reproducibility**: precision under conditions that include different locations, operators, and/or instruments (e.g., inter-laboratory comparisons).

**Example**

Ten repeat measurements of a 25 mm gauge block yield: 25.001, 25.003, 25.002, 25.001, 25.004, 25.002, 25.003, 25.001, 25.002, 25.003 mm. The sample standard deviation, $s\approx0.001$ mm, quantifies the *precision* (repeatability) of the measurement process — independent of whether 25.002 mm (the mean) is close to the block's actual calibrated length.

### Resolution

**Resolution** is the smallest change in a quantity being measured that causes a perceptible change in the corresponding indication (VIM 4.14, formerly termed "discrimination" or "readability").

**Key Points**

- Resolution is a property of the instrument/display, not of the measurement process as a whole.
- For digital instruments, resolution is typically the value of the least significant digit; for analog instruments, it is often taken as a fraction (commonly half) of the smallest scale division.
- Resolution sets a *lower bound* on achievable precision but does not by itself guarantee good accuracy or precision — an instrument may have fine resolution yet poor repeatability due to noise, backlash, or environmental sensitivity.

**Example**

A digital caliper with a display increment of 0.01 mm has a resolution of 0.01 mm. A high-end optical encoder-based linear scale may achieve 0.1 µm resolution, though its actual measurement uncertainty (accounting for other error sources) is typically several times larger than the resolution alone.

### Sensitivity

**Sensitivity** is the quotient of the change in an instrument's indication and the corresponding change in the value of the quantity being measured (VIM 4.12):

$$S=\frac{\Delta(\text{indication})}{\Delta(\text{quantity value})}=\frac{dI}{dX}$$

**Key Points**

- Sensitivity describes the *slope* of the instrument's response curve — how much the output changes per unit change in input.
- A highly sensitive instrument produces a large output change for a small input change, which often (but not always) enables finer resolution.
- Sensitivity can vary across an instrument's measurement range if the response is nonlinear; a **sensitivity coefficient** may need to be evaluated at the specific operating point.
- Distinct from resolution: a sensor may have high sensitivity (large signal change per unit input) but be paired with a coarse-resolution digitizer, limiting overall discrimination — or vice versa.

**Example**

A strain gauge load cell outputs 2 mV/V per 1000 µε of strain. If its gauge factor and bridge excitation give an overall sensitivity of $0.5\ \mu\mathrm{V/N}$, this directly determines how finely force can be resolved by downstream signal-conditioning electronics.

### Relationships and Distinctions Summary

| Term | What it Describes | Reference Needed? | Typical Metric |
| --- | --- | --- | --- |
| Accuracy | Closeness to true value (trueness + precision) | Yes (true/reference value) | Qualitative; sometimes expressed via error limits |
| Trueness | Closeness of mean to true value | Yes | Bias, systematic error |
| Precision | Repeatability/reproducibility of results | No | Standard deviation, variance |
| Resolution | Smallest detectable change in indication | No | Scale division, LSD value |
| Sensitivity | Output change per unit input change | No | Slope (units of output/input) |

### Diagram: Accuracy vs. Precision (Target Analogy) (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 720 300">
<rect x="0" y="0" width="720" height="300" fill="#ffffff" />
<text x="360" y="24" font-size="16" font-weight="bold" text-anchor="middle" fill="#111111">Accuracy vs. Precision (svg_diagram)</text>

<circle cx="120" cy="140" r="80" fill="none" stroke="#cccccc" />
<circle cx="120" cy="140" r="55" fill="none" stroke="#cccccc" />
<circle cx="120" cy="140" r="30" fill="none" stroke="#cccccc" />
<circle cx="120" cy="140" r="6" fill="none" stroke="#cccccc" />
<g fill="#34a853">
<circle cx="122" cy="138" r="4" />
<circle cx="119" cy="141" r="4" />
<circle cx="121" cy="143" r="4" />
<circle cx="118" cy="139" r="4" />
</g>
<text x="120" y="240" font-size="11" text-anchor="middle" fill="#111111">High Accuracy</text>
<text x="120" y="255" font-size="11" text-anchor="middle" fill="#111111">High Precision</text>

<circle cx="300" cy="140" r="80" fill="none" stroke="#cccccc" />
<circle cx="300" cy="140" r="55" fill="none" stroke="#cccccc" />
<circle cx="300" cy="140" r="30" fill="none" stroke="#cccccc" />
<circle cx="300" cy="140" r="6" fill="none" stroke="#cccccc" />
<g fill="#ea4335">
<circle cx="355" cy="110" r="4" />
<circle cx="352" cy="113" r="4" />
<circle cx="357" cy="115" r="4" />
<circle cx="354" cy="108" r="4" />
</g>
<text x="300" y="240" font-size="11" text-anchor="middle" fill="#111111">Low Accuracy</text>
<text x="300" y="255" font-size="11" text-anchor="middle" fill="#111111">High Precision</text>

<circle cx="480" cy="140" r="80" fill="none" stroke="#cccccc" />
<circle cx="480" cy="140" r="55" fill="none" stroke="#cccccc" />
<circle cx="480" cy="140" r="30" fill="none" stroke="#cccccc" />
<circle cx="480" cy="140" r="6" fill="none" stroke="#cccccc" />
<g fill="#4285f4">
<circle cx="500" cy="115" r="4" />
<circle cx="460" cy="165" r="4" />
<circle cx="495" cy="170" r="4" />
<circle cx="465" cy="110" r="4" />
</g>
<text x="480" y="240" font-size="11" text-anchor="middle" fill="#111111">High Accuracy</text>
<text x="480" y="255" font-size="11" text-anchor="middle" fill="#111111">Low Precision</text>

<circle cx="640" cy="140" r="80" fill="none" stroke="#cccccc" />
<circle cx="640" cy="140" r="55" fill="none" stroke="#cccccc" />
<circle cx="640" cy="140" r="30" fill="none" stroke="#cccccc" />
<circle cx="640" cy="140" r="6" fill="none" stroke="#cccccc" />
<g fill="#f9ab00">
<circle cx="690" cy="90" r="4" />
<circle cx="600" cy="190" r="4" />
<circle cx="670" cy="180" r="4" />
<circle cx="610" cy="100" r="4" />
</g>
<text x="640" y="240" font-size="11" text-anchor="middle" fill="#111111">Low Accuracy</text>
<text x="640" y="255" font-size="11" text-anchor="middle" fill="#111111">Low Precision</text>
</svg>

### Application to Precision Metrology & QC

- **Instrument selection**: Choosing a measurement device for a QC application requires matching resolution and sensitivity to the tolerance being controlled — a common rule of thumb (the "10:1 rule" or Test Accuracy Ratio) recommends instrument resolution/uncertainty be at least 10 times finer than the tolerance band, though 4:1 (TAR) or %Gauge R&R-based criteria are also widely used.
- **Gauge R&R studies**: Measurement Systems Analysis (MSA) formally separates repeatability (equipment variation) and reproducibility (appraiser variation) as components of precision, both essential inputs to a Gauge R&R study used to qualify a measurement system for production use.
- **Calibration certificates**: A calibration certificate documents *trueness* (via bias/correction against a reference standard) and often *precision* (via repeatability data), together contributing to the reported measurement uncertainty — accuracy alone is not a reportable numerical quantity per VIM.
- **Sensor specification sheets**: Datasheets typically separate resolution (finest displayable increment) from accuracy specification (e.g., "±0.5% of reading ±2 digits") — engineers must not assume resolution equals accuracy when specifying instrumentation.

### Common Pitfalls

- Using "accuracy" and "precision" interchangeably in technical reports — VIM formally distinguishes them, and doing so can misstate what a stated tolerance or specification actually guarantees.
- Assuming a device with fine resolution (e.g., a 6-digit display) is inherently accurate — resolution only defines the smallest displayable increment, not the correctness or repeatability of the measurement.
- Reporting a single repeated-measurement standard deviation as the *total* measurement uncertainty without also accounting for systematic/trueness contributions (calibration bias, environmental effects) — repeatability alone typically understates the full uncertainty budget.
- Confusing sensitivity with resolution when specifying sensors: a highly sensitive transducer paired with a low-resolution ADC (analog-to-digital converter) may still yield coarse overall measurement steps.

### Related Topics

- Measurement Uncertainty and the GUM Law of Propagation of Uncertainty
- Gauge Repeatability and Reproducibility (Gauge R&R) Studies
- Systematic Error, Bias, and Correction
- Repeatability, Intermediate Precision, and Reproducibility Conditions
- Instrument Selection and the 10:1 Test Accuracy Ratio Rule
- International Vocabulary of Metrology (VIM) Terminology