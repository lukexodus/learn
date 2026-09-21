## Transconductance and Output Conductance

### Overview

Transconductance ($g_m$) and output conductance ($g_{ds}$ or $g_o$) are the two small-signal parameters that characterize a MOSFET's behavior as an amplifying/switching element. They describe how the drain current responds to small perturbations in gate voltage and drain voltage, respectively, and together they determine gain, bandwidth, and analog performance limits of a MOSFET-based circuit.

Both parameters are derived from the large-signal drain current equation $I_D(V_{GS}, V_{DS})$ by partial differentiation:

$$g_m = \frac{\partial I_D}{\partial V_{GS}}\bigg|_{V_{DS}=\text{const}}, \qquad g_{ds} = \frac{\partial I_D}{\partial V_{DS}}\bigg|_{V_{GS}=\text{const}}$$

### Small-Signal Equivalent Circuit Context

In the small-signal model, the MOSFET is represented as a voltage-controlled current source with a finite output resistance:

$$i_d = g_m v_{gs} + g_{ds} v_{ds}$$

```mermaid
graph LR
    G["Gate (vgs)"] -->|controls| CCCS["gm * vgs<br/>Current Source"]
    CCCS --> D["Drain"]
    D --- Rout["rds = 1/gds"]
    Rout --- S["Source"]
    CCCS --- S
```

This representation is the foundation of all MOSFET small-signal analysis, from single-transistor amplifiers to full analog IC design.

### Transconductance in the Triode (Linear) Region

The triode-region drain current is:

$$I_D = \mu_n C_{ox}\frac{W}{L}\left[(V_{GS}-V_T)V_{DS} - \frac{V_{DS}^2}{2}\right]$$

Differentiating with respect to $V_{GS}$ at fixed $V_{DS}$:

$$g_m = \mu_n C_{ox}\frac{W}{L}V_{DS}$$

**Key Points**

- $g_m$ in triode is directly proportional to $V_{DS}$
- At very small $V_{DS}$ (deep triode/linear region used for switches), $g_m$ becomes small since the device behaves as a voltage-controlled resistor rather than a current source
- This region is generally not used for voltage amplification because gain is poor; it is primarily used for switches and passive mixers

### Transconductance in Saturation

Using the square-law saturation current model (long-channel approximation):

$$I_D = \frac{1}{2}\mu_n C_{ox}\frac{W}{L}(V_{GS}-V_T)^2(1+\lambda V_{DS})$$

Differentiating with respect to $V_{GS}$ (holding $V_{DS}$, hence the $(1+\lambda V_{DS})$ factor, constant):

$$g_m = \mu_n C_{ox}\frac{W}{L}(V_{GS}-V_T)(1+\lambda V_{DS}) \approx \mu_n C_{ox}\frac{W}{L}(V_{GS}-V_T)$$

This is commonly rewritten using the overdrive voltage $V_{ov} = V_{GS}-V_T$:

$$g_m = \mu_n C_{ox}\frac{W}{L}V_{ov}$$

**Alternative Forms of $g_m$**

Since $I_D = \frac{1}{2}k'\frac{W}{L}V_{ov}^2$ (where $k' = \mu_n C_{ox}$), $g_m$ can be expressed equivalently as:

$$g_m = \sqrt{2k'\frac{W}{L}I_D} = \frac{2I_D}{V_{ov}}$$

These three equivalent forms are used depending on which variables are held fixed in a given design problem — e.g., the $\sqrt{I_D}$ form is used when comparing devices at fixed bias current, while the $2I_D/V_{ov}$ form is used when optimizing for a fixed overdrive budget.

### Output Conductance and Channel Length Modulation

In an ideal long-channel MOSFET, saturation-region current would be completely independent of $V_{DS}$, giving zero output conductance and infinite output resistance. In real devices, **channel length modulation** causes $I_D$ to increase slightly with $V_{DS}$ because the effective channel length shrinks as the pinch-off point moves toward the source with increasing $V_{DS}$.

Differentiating the saturation current with respect to $V_{DS}$:

$$g_{ds} = \frac{\partial I_D}{\partial V_{DS}} = \frac{1}{2}\mu_n C_{ox}\frac{W}{L}V_{ov}^2 \cdot \lambda \approx \lambda I_D$$

The output resistance is the reciprocal:

$$r_{ds} = \frac{1}{g_{ds}} \approx \frac{1}{\lambda I_D} = \frac{V_A}{I_D}$$

where $V_A = 1/\lambda$ is the **Early voltage** analog for MOSFETs (borrowed terminology from BJT theory). A larger $V_A$ (smaller $\lambda$) indicates a flatter $I_D$-$V_{DS}$ curve and higher intrinsic gain.

**Physical Dependence of $\lambda$**

$\lambda$ is inversely related to channel length:

$$\lambda \propto \frac{1}{L}$$

This is why long-channel devices are preferred in analog design for high output resistance, while short-channel devices (preferred for speed and density in digital logic) exhibit substantially higher $g_{ds}$ and thus lower intrinsic voltage gain per stage.

### Intrinsic Gain

The single most important figure of merit combining $g_m$ and $g_{ds}$ is the **intrinsic (self) gain** of a single transistor:

$$A_v = g_m r_{ds} = \frac{g_m}{g_{ds}}$$

Substituting the saturation expressions:

$$A_v = \frac{\mu_n C_{ox}\frac{W}{L}V_{ov}}{\lambda I_D} = \frac{2}{\lambda V_{ov}} = \frac{2V_A}{V_{ov}}$$

This shows that intrinsic gain improves with lower overdrive voltage (operating closer to threshold, i.e., in weak/moderate inversion) and with longer channel length (higher $V_A$). This tradeoff — gain versus speed/bandwidth — is central to analog amplifier design, since lower $V_{ov}$ increases gain but reduces the bandwidth achievable at a given bias current.

### Short-Channel Effects on gm and gds

**Key Points**

- **Velocity saturation**: In short-channel devices, carrier velocity saturates at high lateral electric fields, causing $I_D$ to become more linear in $V_{ov}$ rather than quadratic. This changes $g_m$ from $\propto V_{ov}$ toward $g_m \propto \text{constant}$ (velocity-saturated regime), since:



  $$I_{D,sat} \approx W C_{ox} v_{sat}(V_{GS}-V_T)$$



  $$g_m \approx W C_{ox} v_{sat}$$
- **DIBL (Drain-Induced Barrier Lowering)**: In short-channel devices, the drain voltage influences the source-side potential barrier directly (not just through channel length modulation), causing $g_{ds}$ to be substantially higher than the simple $\lambda I_D$ model predicts. This is a dominant leakage and output-conductance-degradation mechanism in deep-submicron nodes. [Inference: exact quantitative DIBL contribution to $g_{ds}$ is highly process- and geometry-dependent and cannot be captured by the basic square-law model.]
- **Mobility degradation**: Vertical electric fields from the gate reduce effective mobility ($\mu_{eff}$) at high $V_{GS}$, which reduces $g_m$ growth at high overdrive compared to the ideal square-law prediction.

### Weak Inversion (Subthreshold) Transconductance

Below threshold, drain current follows an exponential law:

$$I_D \approx I_{D0}\exp\left(\frac{V_{GS}}{nV_T}\right)$$

where $V_T$ here is the thermal voltage ($kT/q$, not threshold voltage) and $n$ is the subthreshold slope factor (typically 1.0-1.5). Differentiating:

$$g_m = \frac{I_D}{nV_T}$$

This gives the maximum possible $g_m/I_D$ ratio (transconductance efficiency) of any bias region, making subthreshold/weak-inversion operation attractive for ultra-low-power analog design, at the cost of much lower absolute current drive and bandwidth.

### gm/ID as a Design Methodology

**Example**

The ratio $g_m/I_D$ is a widely used figure of merit that spans all inversion regions smoothly and is bias-point independent in a way that's useful for design:

| Region | Typical $g_m/I_D$ (1/V) | Characteristic |
| --- | --- | --- |
| Strong inversion (square-law) | 5–10 | $g_m/I_D = 2/V_{ov}$ |
| Moderate inversion | 10–20 | Transition zone |
| Weak inversion (subthreshold) | up to $1/(nV_T) \approx 25$–38 | Maximum efficiency |

A designer selecting a target $g_m/I_D$ effectively selects the inversion level, from which required $W/L$ and bias current follow — this is the basis of the "gm/ID design methodology," an alternative to the traditional square-law hand-calculation approach, especially valuable in modern short-channel processes where the square-law model is inaccurate. [Unverified: exact numerical $g_m/I_D$ ranges vary by process node and must be confirmed against a given technology's simulation models (e.g., BSIM) rather than assumed universally.]

### Frequency-Domain Relevance

Transconductance directly sets the unity-gain frequency of a MOSFET when combined with parasitic capacitances:

$$f_T = \frac{g_m}{2\pi(C_{gs}+C_{gd})}$$

Output conductance, in contrast, primarily affects DC/low-frequency gain and has comparatively little direct impact on $f_T$, but it strongly affects the achievable gain-bandwidth tradeoff in feedback amplifier stages, since gain is bounded by $g_m r_{ds}$ at low frequencies even if bandwidth is set mostly by capacitances.

### Worked Numerical Example

**Example**

Given: NMOS device with $\mu_n C_{ox} = 200\ \mu\text{A/V}^2$, $W/L = 10$, $V_{ov} = 0.2\ \text{V}$, $\lambda = 0.05\ \text{V}^{-1}$.

Step 1 — Drain current:

$$I_D = \frac{1}{2}(200\times10^{-6})(10)(0.2)^2 = 40\ \mu\text{A}$$

Step 2 — Transconductance:

$$g_m = \mu_n C_{ox}\frac{W}{L}V_{ov} = (200\times10^{-6})(10)(0.2) = 400\ \mu\text{A/V} = 400\ \mu\text{S}$$

Step 3 — Output conductance and resistance:

$$g_{ds} = \lambda I_D = (0.05)(40\times10^{-6}) = 2\ \mu\text{S}$$



$$r_{ds} = \frac{1}{g_{ds}} = 500\ \text{k}\Omega$$

Step 4 — Intrinsic gain:

$$A_v = g_m r_{ds} = (400\times10^{-6})(500\times10^3) = 200 \text{ (V/V)}$$

This 200 V/V intrinsic gain is representative of a long-channel device at moderate overdrive; short-channel devices in advanced nodes typically show single-digit to low-double-digit intrinsic gain due to much higher $\lambda$ (or DIBL-dominated $g_{ds}$). [Inference: this comparison to advanced-node behavior is a general trend, not a specific numeric claim about any particular foundry process.]

### I-V Curve Illustrating gm and gds Extraction (SVG)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 420">
<title>MOSFET Output Characteristics: gm and gds Graphical Extraction (svg_diagram)</title>
<rect x="0" y="0" width="700" height="420" fill="#ffffff" />
<line x1="70" y1="370" x2="650" y2="370" stroke="#333" stroke-width="2" />
<line x1="70" y1="370" x2="70" y2="30" stroke="#333" stroke-width="2" />
<text x="360" y="405" font-size="15" fill="#333" text-anchor="middle">V_DS (V)</text>
<text x="25" y="200" font-size="15" fill="#333" text-anchor="middle" transform="rotate(-90 25 200)">I_D (A)</text>
<path d="M 70 370 Q 140 130 220 120 L 620 90" fill="none" stroke="#1f77b4" stroke-width="3" />
<text x="230" y="115" font-size="12" fill="#1f77b4">VGS3 (highest)</text>
<path d="M 70 370 Q 130 200 200 190 L 620 165" fill="none" stroke="#2ca02c" stroke-width="3" />
<text x="230" y="185" font-size="12" fill="#2ca02c">VGS2</text>
<path d="M 70 370 Q 120 280 180 270 L 620 250" fill="none" stroke="#d62728" stroke-width="3" />
<text x="230" y="265" font-size="12" fill="#d62728">VGS1 (lowest)</text>
<line x1="220" y1="370" x2="220" y2="120" stroke="#999" stroke-width="1" stroke-dasharray="3,3" />
<text x="220" y="385" font-size="11" fill="#666" text-anchor="middle">Vov3</text>
<line x1="450" y1="90" x2="450" y2="165" stroke="#000" stroke-width="1" />
<text x="460" y="130" font-size="11" fill="#000">ΔID (gm: vertical spacing between curves at fixed VDS)</text>
<line x1="400" y1="100" x2="600" y2="92" stroke="#000" stroke-width="1" />
<text x="420" y="80" font-size="11" fill="#000">Slope = gds (within one curve, saturation region)</text>
</svg>

### Related Topics

- Small-signal MOSFET model and hybrid-$\pi$ equivalent circuit
- Channel length modulation and the Early voltage analogy
- $g_m/I_D$ design methodology for analog circuit sizing
- Velocity saturation and short-channel current models (BSIM overview)
- Drain-induced barrier lowering (DIBL) and short-channel output conductance degradation
- Cascode topologies for output resistance boosting
- Unity-gain frequency ($f_T$) and high-frequency MOSFET figures of merit