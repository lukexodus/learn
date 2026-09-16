## Power Factor and Power Factor Correction

### Definition and Purpose

Power factor (PF) is the ratio of real power to apparent power in an AC circuit, quantifying how effectively electrical current is converted into useful work. Power factor correction (PFC) is the deliberate addition of reactive compensation to bring the power factor closer to unity, reducing current draw, line losses, and equipment loading for a given real power delivery.

$$pf = \frac{P}{S} = \cos\phi$$

where $\phi$ is the phase angle between voltage and current.

**Key Points**

- Power factor ranges from 0 to 1 in magnitude and is qualified as **lagging** (inductive load, current lags voltage) or **leading** (capacitive load, current leads voltage)
- Utilities and grid codes typically require industrial/commercial customers to maintain $pf \geq 0.90$–0.95, with financial penalties for non-compliance
- PFC does not reduce real power consumption or the energy bill for work performed; it reduces the reactive component of current, which reduces $I^2R$ losses and frees up apparent power capacity

### Physical Origin of Poor Power Factor

Most industrial and grid loads are inductive due to motors, transformers, and fluorescent/HID lighting ballasts, causing current to lag voltage. This lagging current has two components:

$$\tilde{I} = \underbrace{I\cos\phi}_{\text{in-phase (real)}} + j\underbrace{I\sin\phi}_{\text{quadrature (reactive)}}$$

Only the in-phase component contributes to $P$; the quadrature component contributes to $Q$ and inflates the total current magnitude $I = S/V$ that lines, breakers, and transformers must carry.

(svg_diagram) Current Decomposition: Real and Reactive Components

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 420 320">
<text x="210" y="25" text-anchor="middle" font-size="16" font-family="sans-serif" font-weight="bold">Current Decomposition (svg_diagram)</text>
<line x1="60" y1="250" x2="380" y2="250" stroke="#888" stroke-width="1" />
<line x1="60" y1="250" x2="60" y2="60" stroke="#888" stroke-width="1" />
<line x1="60" y1="250" x2="300" y2="250" stroke="#c0392b" stroke-width="3" />
<text x="130" y="270" font-size="13" font-family="sans-serif" fill="#c0392b" font-weight="bold">I·cosφ (real)</text>
<line x1="300" y1="250" x2="300" y2="110" stroke="#2980b9" stroke-width="3" />
<text x="305" y="180" font-size="13" font-family="sans-serif" fill="#2980b9" font-weight="bold">I·sinφ (reactive)</text>
<line x1="60" y1="250" x2="300" y2="110" stroke="#27ae60" stroke-width="3" />
<text x="120" y="170" font-size="13" font-family="sans-serif" fill="#27ae60" font-weight="bold">I (total)</text>
<line x1="60" y1="250" x2="380" y2="250" stroke="#e67e22" stroke-width="2" stroke-dasharray="5,3" />
<text x="330" y="245" font-size="12" font-family="sans-serif" fill="#e67e22">V (reference)</text>
</svg>

### Effect on Losses and Capacity

For fixed real power delivery $P$ and voltage $V$, current scales inversely with power factor:

$$I = \frac{P}{V\cdot pf}$$

Line losses scale with the square of current:

$$P_{loss} = I^2R = \frac{P^2R}{V^2(pf)^2}$$

Improving power factor from 0.7 to 0.95 reduces required current by roughly 26%, and reduces $I^2R$ losses by roughly 45% for the same real power delivered. [Inference: exact percentages depend on the specific before/after $pf$ values; these are illustrative for the stated example.]

**Example**

A facility draws $P = 500$ kW at $pf = 0.75$ lagging, $V_{LL} = 480$ V (three-phase):

$$S = \frac{P}{pf} = \frac{500}{0.75} = 666.7\text{ kVA}$$



$$Q = \sqrt{S^2 - P^2} = \sqrt{666.7^2 - 500^2} = 441.1\text{ kVAR (lagging)}$$



$$I_L = \frac{S}{\sqrt{3}V_{LL}} = \frac{666,700}{\sqrt{3}(480)} = 801.9\text{ A}$$

To correct to $pf = 0.95$:

$$S_{new} = \frac{500}{0.95} = 526.3\text{ kVA}, \quad Q_{new} = \sqrt{526.3^2 - 500^2} = 164.3\text{ kVAR}$$



$$Q_{cap} = Q - Q_{new} = 441.1 - 164.3 = 276.8\text{ kVAR}$$

A 276.8 kVAR capacitor bank installed at the facility achieves the target power factor, reducing line current to approximately $633.1$ A — roughly a 21% reduction.

### Power Factor Correction Methods

**Shunt Capacitor Banks**

The most common and economical PFC method for lagging loads. Capacitors supply leading reactive power that cancels a portion of the inductive $Q$ demanded by the load, so the source only needs to supply the net reactive power.

$$Q_C = V^2\omega C \quad \Rightarrow \quad C = \frac{Q_C}{\omega V^2}$$

**Key Points**

- Fixed capacitor banks provide constant compensation and are suited to steady loads
- Switched (staged) capacitor banks use contactors to add/remove stages, tracking varying load reactive demand and avoiding overcorrection (leading pf) during light-load periods
- Automatic power factor correction (APFC) relays or controllers monitor real-time $pf$ and switch capacitor stages accordingly

**Synchronous Condensers**

Synchronous motors run without mechanical load, with excitation controlled to source or sink reactive power continuously and smoothly. Historically significant at transmission substations for voltage support; largely supplemented (but not fully replaced) by power-electronic solutions in modern installations.

**Static VAR Compensators (SVC) and STATCOMs**

Power-electronic devices providing fast, continuously variable reactive power compensation:

| Device | Technology | Response Speed | Typical Application |
| --- | --- | --- | --- |
| Fixed Capacitor Bank | Passive | Slow (manual/staged) | Steady industrial loads |
| Switched Capacitor Bank | Passive + contactors | Seconds | Variable industrial/utility loads |
| Synchronous Condenser | Rotating machine | Sub-second to seconds | Transmission voltage support |
| SVC | Thyristor-controlled reactor/capacitor | Milliseconds | Transmission/large industrial (arc furnaces) |
| STATCOM | Voltage-source converter | Milliseconds | Transmission, renewable integration, flicker mitigation |

**Active Harmonic Filters / Active PFC (Electronic Loads)**

At the individual load level, switch-mode power supplies increasingly use active PFC circuitry (boost converter topology) to shape input current to track the voltage waveform, simultaneously correcting displacement power factor and reducing harmonic distortion — relevant where distorted (non-sinusoidal) current also degrades **true power factor**.

### Displacement vs. True Power Factor

$$pf_{true} = \frac{P}{S} = pf_{displacement} \times \frac{1}{\sqrt{1+\text{THD}_I^2}}$$

where $\text{THD}_I$ is the total harmonic distortion of current and $pf_{displacement} = \cos\phi_1$ refers only to the fundamental-frequency phase angle. Nonlinear loads (variable frequency drives, rectifiers, LED drivers) can have good displacement power factor but poor true power factor due to harmonic current content. Capacitor banks correct displacement power factor but do not address harmonics, and can in some configurations resonate with system inductance and amplify specific harmonics — a phenomenon requiring harmonic resonance studies before bank sizing. [Inference: resonance risk is installation-specific and depends on system short-circuit impedance and existing harmonic sources; it does not occur in every capacitor bank installation.]

### PFC Design Workflow

```mermaid
flowchart TD
    A[Measure baseline P, Q, S, pf at facility/bus] --> B[Determine target power factor]
    B --> C[Calculate required Qc = P(tanφ1 - tanφ2)]
    C --> D[Select compensation type: fixed, switched, SVC, STATCOM]
    D --> E[Perform harmonic resonance check]
    E --> F{Resonance risk?}
    F -->|Yes| G[Add detuning reactor / re-tune bank]
    F -->|No| H[Specify capacitor bank rating and switching scheme]
    G --> H
    H --> I[Install, commission, verify pf improvement]
```

### Grid-Level Significance

At the transmission and distribution system level, aggregate power factor affects:

- **Voltage regulation** — reactive power flow causes voltage drop along lines; poor aggregate pf across a feeder can cause voltage sag under heavy load
- **Transmission capacity** — every unit of $Q$ transmitted alongside $P$ consumes thermal capacity that could otherwise carry real power, effectively de-rating lines for real power transfer
- **Generator reactive capability** — generators have limited reactive power output governed by their capability curve; utilities may direct generators to absorb or supply $Q$ to support grid voltage, which interacts with system-wide power factor management
- **Renewable integration** — modern grid codes (e.g., FERC Order 827 in the U.S. context) require wind and solar plants to provide dynamic reactive power support, effectively participating in grid-wide power factor and voltage management [Unverified: specific regulatory requirements vary by jurisdiction and are subject to revision; verify current grid code requirements for the applicable region.]

### Common Pitfalls

- **Overcorrection** — adding excess capacitive compensation shifts power factor to leading, which can cause overvoltage conditions, especially during light-load periods
- **Ignoring harmonics** — sizing capacitor banks based on displacement power factor alone without checking for harmonic resonance risk
- **Static bank sizing for dynamic loads** — fixed capacitor banks cannot track loads with highly variable reactive demand (e.g., arc furnaces, welding equipment), leading to under- or over-compensation
- **Neglecting transient inrush** — capacitor bank switching produces transient inrush currents that must be managed with pre-insertion resistors or synchronous switching to avoid nuisance tripping or equipment stress

**Related Topics**

- Complex Power: Real, Reactive, and Apparent Power
- Reactive Power Compensation Devices (SVC, STATCOM, Synchronous Condensers)
- Harmonic Distortion and Total Harmonic Distortion (THD)
- Voltage Regulation and Reactive Power Flow on Transmission Lines
- Capacitor Bank Switching Transients and Mitigation
- Generator Reactive Capability Curves
- Grid Codes for Renewable Energy Reactive Power Support