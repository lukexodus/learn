## Profile Parameters Ra, Rq, Rz, and Rt

### Overview

Profile roughness parameters quantify the amplitude (height) characteristics of a surface's roughness profile, obtained after separating the roughness component from waviness and form using an appropriate filter (per ISO 4288 / ISO 16610). The four parameters $Ra$, $Rq$, $Rz$, and $Rt$ are among the most widely specified and reported surface texture parameters in engineering drawings and quality documentation, defined per ISO 4287 (with historical and regional variants under ASME B46.1).

### Common Definitions and Terminology

- **Sampling length ($lr$)**: the length over which a single roughness measurement is evaluated for peak/valley or averaging purposes, typically equal to the roughness cutoff wavelength $\lambda_c$.
- **Evaluation length ($ln$)**: the total length over which the surface is assessed, typically composed of multiple consecutive sampling lengths (commonly five, per ISO 4288 default practice) to obtain a statistically representative result.
- **Mean line**: the reference line about which the profile height $z(x)$ is measured, determined as the line that divides the profile such that the sum of areas above and below is equal (least-squares mean line) after filtering.

### Ra — Arithmetic Mean Deviation (Average Roughness)

#### Definition

$Ra$ is the arithmetic average of the absolute values of the profile height deviations from the mean line, measured over the evaluation length.

$$Ra = \frac{1}{l}\int_0^l |z(x)|\,dx$$

For discretely sampled data (as acquired by digital profilometers):

$$Ra = \frac{1}{n}\sum_{i=1}^{n} |z_i|$$

#### Characteristics

- **Key Points**
  - $Ra$ is the most commonly specified surface roughness parameter worldwide due to its simplicity, long history of use, and general correlation with many functional surface properties.
  - $Ra$ is an averaging parameter — it is relatively insensitive to occasional large peaks or deep scratches, since extreme values are diluted across the averaging length.
  - Two surfaces with identical $Ra$ can have substantially different actual profiles (e.g., one with uniform fine texture, another with a few deep isolated scratches on an otherwise smooth surface) — $Ra$ alone does not fully characterize surface behavior, which is why it is often supplemented with other parameters for critical applications. [Inference — the degree to which this ambiguity matters depends on the specific functional requirement of the surface in question.]

#### Example

A precision-ground bearing race might specify $Ra \le 0.2\,\mu m$; a general machined mating surface might specify $Ra \le 1.6\,\mu m$; a rough sand-cast surface (as-cast, unmachined) could exceed $Ra = 12.5\,\mu m$.

### Rq (RMS) — Root-Mean-Square Deviation

#### Definition

$Rq$ (also denoted $RMS$ in older/ASME nomenclature) is the root-mean-square average of the profile height deviations from the mean line over the evaluation length.

$$Rq = \sqrt{\frac{1}{l}\int_0^l z(x)^2\,dx}$$

Discrete form:

$$Rq = \sqrt{\frac{1}{n}\sum_{i=1}^{n} z_i^2}$$

#### Characteristics

- **Key Points**
  - $Rq$ gives greater weight to larger deviations than $Ra$ because the squaring operation amplifies the contribution of higher peaks and deeper valleys before the averaging (square-root) step is applied.
  - For a surface with a purely sinusoidal profile, $Rq \approx 1.11 \times Ra$; for real, more randomly textured surfaces, the $Rq/Ra$ ratio typically falls in a comparable range (commonly cited around 1.1–1.3), though the exact ratio depends on the specific height distribution of the surface. [Inference — the precise Rq/Ra ratio is surface-dependent and the sinusoidal-profile relationship is a theoretical reference case, not a universal conversion factor for arbitrary real surfaces.]
  - $Rq$ is preferred in some optical and precision-surface applications (e.g., optics, semiconductor wafer surfaces) because RMS-type metrics relate more directly to statistical/energy-based descriptions of surface scatter and light interaction.

#### Example

A surface with $Ra = 0.5\,\mu m$ might typically report $Rq$ in the range of approximately $0.55$–$0.65\,\mu m$, though this must be confirmed by actual measurement rather than assumed from $Ra$ alone.

### Rz — Maximum Height of Profile

#### Definition (ISO Rz — current ISO 4287 definition)

Under the current ISO 4287 definition, $Rz$ is the sum of the height of the largest profile peak height ($Zp$) and the depth of the largest profile valley depth ($Zv$) within a single sampling length, averaged over the number of sampling lengths in the evaluation length:

$$Rz = \frac{1}{m}\sum_{i=1}^{m}(Zp_i + Zv_i)$$

where $m$ is the number of sampling lengths in the evaluation length.

#### Important Note on Rz Ambiguity

- **Key Points**
  - The symbol $Rz$ has carried **different definitions historically and across standards**, which is a frequent source of confusion:
    - **Current ISO 4287 $Rz$**: average of maximum peak-to-valley heights per sampling length (as defined above) — this is the modern, standard definition.
    - **Older DIN/ISO $Rz$ (sometimes called "ten-point height," $R_{tm}$ in some older German DIN standards)**: an older convention based on averaging the five highest peaks and five deepest valleys over the evaluation length.
    - **ASME B46.1 $Rz$**: historically corresponds more closely to the ISO current definition (average maximum peak-to-valley height per sampling length) in modern editions, but practitioners should verify against the specific edition/version in force. [Unverified — exact historical correspondence between ASME and ISO Rz conventions across all editions should be confirmed against the specific standard revision cited on the relevant drawing or specification.]
  - Because of this history, engineering drawings and specifications should always reference the governing standard (e.g., "$Rz$ per ISO 4287") explicitly when specifying this parameter, to avoid ambiguity between measurement systems/software defaulting to different conventions.

#### Example

A surface might report $Rz \approx 4$–$6 \times Ra$ for many conventionally machined (turned, milled) surfaces, though this ratio is not fixed and varies considerably with the specific machining process and resulting height distribution. [Inference — commonly cited rule-of-thumb ratios between Rz and Ra are process-dependent approximations, not universal constants, and should not be relied upon in place of direct measurement.]

### Rt — Total Height of the Profile

#### Definition

$Rt$ is the total height of the roughness profile over the **entire evaluation length** — the vertical distance between the highest peak and the lowest valley across all sampling lengths combined, rather than being averaged per sampling length.

$$Rt = Zp_{\text{max}} + Zv_{\text{max}} \quad \text{(over the full evaluation length)}$$

#### Characteristics

- **Key Points**
  - $Rt$ represents the single largest peak-to-valley excursion anywhere in the entire measured evaluation length, making it the most sensitive of the four parameters to isolated defects, scratches, or unusually deep valleys.
  - By definition, $Rt \ge Rz$ (ISO current definition), since $Rz$ is an average of per-sampling-length peak-to-valley heights while $Rt$ captures the single worst excursion across the whole evaluation length.
  - $Rt$ is particularly relevant for functional requirements sensitive to the single worst-case defect (e.g., sealing surfaces where one deep scratch could create a leak path, or fatigue-critical surfaces where the deepest valley acts as a stress concentration/crack initiation site) rather than the average texture condition.

#### Example

A sealing face might specify not only $Ra \le 0.4\,\mu m$ but also $Rt \le 3\,\mu m$, ensuring that no single deep scratch or defect compromises the seal even if the average roughness is acceptable.

### Comparative Summary Table

| Parameter | Basis | Sensitivity to isolated defects | Typical relative magnitude |
| --- | --- | --- | --- |
| $Ra$ | Arithmetic mean of absolute deviations | Low (averaging) | Baseline reference |
| $Rq$ | Root-mean-square of deviations | Moderate (squaring emphasizes larger deviations) | Slightly greater than $Ra$ |
| $Rz$ (ISO) | Average of max peak-to-valley per sampling length | Moderate–high | Several times $Ra$ (process-dependent) |
| $Rt$ | Single largest peak-to-valley over entire evaluation length | Highest | Greater than or equal to $Rz$ |

### Diagram: Parameter Extraction from a Profile Trace

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 760 340">
<title>Roughness Profile Showing Ra, Rq, Rz, and Rt Reference Regions (svg_diagram)</title>
\<style\>
text { font-family: Arial, sans-serif; font-size: 13px; fill: #1a1a1a; }
.label { font-size: 12px; }
\</style\>
<rect x="0" y="0" width="760" height="340" fill="#ffffff" />
<line x1="40" y1="170" x2="720" y2="170" stroke="#888" stroke-width="1" stroke-dasharray="4,3" />
<text x="600" y="165" class="label">Mean line</text>

<path d="M40,170 C55,150 65,190 80,160 C95,140 105,195 120,165 C135,145 145,90 160,175 C175,150 185,200 200,165 C215,145 225,185 240,160 C255,140 265,195 280,165 C295,150 305,185 320,160 C335,145 345,60 360,180 C375,150 385,195 400,165 C415,145 425,185 440,160 C455,140 465,195 480,165 C495,150 505,185 520,160 C535,145 545,190 560,165 C575,150 585,185 600,160 C615,145 625,195 640,165 C655,150 665,185 680,160 C695,145 705,190 720,165" stroke="`#2f6fab`" stroke-width="1.5" fill="none" />


<line x1="345" y1="60" x2="345" y2="200" stroke="#c46a1e" stroke-width="1.5" stroke-dasharray="3,2" />
<text x="350" y="75" font-weight="bold" fill="#c46a1e">Rt: max peak-to-valley, full length</text>

<line x1="200" y1="230" x2="200" y2="260" stroke="#999" />
<line x1="360" y1="230" x2="360" y2="260" stroke="#999" />
<line x1="520" y1="230" x2="520" y2="260" stroke="#999" />
<text x="60" y="250" class="label">Sampling length 1</text>
<text x="220" y="250" class="label">Sampling length 2</text>
<text x="380" y="250" class="label">Sampling length 3 (Rz averages peak-valley per length)</text>
<rect x="40" y="290" width="680" height="40" fill="#f7f7f7" stroke="#999" />
<text x="50" y="315" class="label">Ra: mean of |deviations|; Rq: RMS of deviations; Rz: avg(peak+valley) per sampling length; Rt: single max peak-to-valley over full evaluation length</text>
</svg>

### Selection Guidance for Specification

- **Key Points**
  - $Ra$ remains the default general-purpose choice for most commercial/industrial drawing callouts due to widespread instrument support and historical convention.
  - $Rq$ is preferred where a statistically weighted (RMS-based) descriptor better correlates with the functional physics involved (e.g., optical scatter, contact mechanics models that use RMS roughness).
  - $Rz$ and $Rt$ are added as supplementary requirements when isolated defects or peak/valley extremes are functionally critical (sealing, fatigue, coating thickness uniformity over peaks) and an average parameter like $Ra$ alone would not adequately control the risk.
  - Combining $Ra$ (or $Rq$) with $Rz$ or $Rt$ on critical drawings provides both an average-condition control and a worst-case-excursion control, which is common practice for high-reliability sealing and fatigue-critical surfaces. [Inference — the specific combination and limit values appropriate for a given application depend on the functional failure mode being controlled and are typically established through application-specific engineering analysis or historical field performance data.]

### Related Topics

- Roughness, waviness, and lay (the broader texture decomposition these parameters are extracted from)
- Filtering standards for roughness isolation (ISO 4288, ISO 16610 Gaussian filters)
- Areal (3D) surface parameters ($Sa$, $Sq$, $Sz$) per ISO 25178 as extensions of profile parameters
- Stylus profilometry measurement procedure and sampling/evaluation length selection
- Surface texture symbols and drawing indication per ISO 1302 / ASME Y14.36
- Skewness ($Rsk$) and kurtosis ($Rku$) as complementary height-distribution shape parameters
- Correlating roughness parameters to functional performance (friction, sealing, fatigue)