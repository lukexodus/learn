## Three-Phase Transformer Connections and Vector Groups

### Overview

Three-phase power transformers can be constructed from three single-phase units or as a single three-phase core unit, with windings arranged in various connection configurations — primarily wye (star) and delta, with zigzag as a specialized variant. The chosen winding connection determines the transformer's voltage/current transformation characteristics, phase-shift behavior, and zero-sequence impedance path, all of which are formally captured by the transformer's vector group designation. Vector groups are essential for parallel operation, protection scheme design, and interconnection compatibility.

### Basic Three-Phase Winding Connections

#### Wye (Star) Connection

**Key Points**

- Three windings connected with one end of each joined at a common neutral point, the other ends brought out as line terminals
- Line-to-line voltage is $\sqrt{3}$ times the phase (winding) voltage: $V_{LL} = \sqrt{3} \, V_{phase}$
- Line current equals phase (winding) current: $I_{line} = I_{phase}$
- Provides an accessible neutral point, which can be grounded (solidly, through resistance, or through reactance) — important for system grounding and zero-sequence current paths

#### Delta Connection

**Key Points**

- Three windings connected end-to-end in a closed loop, with line terminals brought out at each junction
- Line-to-line voltage equals phase (winding) voltage: $V_{LL} = V_{phase}$
- Line current is $\sqrt{3}$ times phase (winding) current: $I_{line} = \sqrt{3} \, I_{phase}$
- No accessible neutral point; provides a closed path for triplen harmonic (particularly third-harmonic) circulating currents, which suppresses their appearance in the line current and helps maintain a more sinusoidal flux waveform

#### Zigzag Connection

**Key Points**

- Each phase winding is split into two half-windings wound on different core legs and connected in a specific series arrangement to create a phase shift within the winding itself
- Commonly used for grounding transformers, providing a low-impedance path to ground for zero-sequence current while presenting high impedance to positive/negative-sequence (balanced) currents
- Less common for general power transformation compared to wye and delta, but standard for neutral grounding applications

### Common Connection Combinations

| Connection | Primary | Secondary | Typical Application |
| --- | --- | --- | --- |
| Yy | Wye | Wye | Same-voltage-class transmission; requires attention to third-harmonic/zero-sequence behavior |
| Dd | Delta | Delta | Distribution and some transmission; no neutral available either side |
| Yd | Wye | Delta | Step-down from transmission to sub-transmission; delta suppresses harmonics |
| Dy | Delta | Wye | Step-up from generation, or distribution step-down with grounded secondary neutral |
| Yz | Wye | Zigzag | Grounding/neutral-forming applications |

### Phase Shift and Vector Group Notation

#### Purpose of Vector Groups

**Key Points**

- Vector group notation standardizes the description of a transformer's winding connections and the resulting phase-angle relationship between primary and secondary voltages
- Essential for ensuring transformers can be operated in parallel (matching phase shift is a prerequisite) and for correctly modeling phase relationships in protection and fault studies

#### Notation Structure (IEC-Style)

The standard notation (as used in IEC 60076-1) consists of:

1. A capital letter for the higher-voltage winding connection: **Y** (wye), **D** (delta), **Z** (zigzag)
2. A lowercase letter for the lower-voltage winding connection: **y**, **d**, **z**
3. Optionally, **N**/**n** appended if the wye (or zigzag) neutral is brought out (grounded or accessible)
4. A clock-hour number (0–11) indicating the phase displacement of the low-voltage winding relative to the high-voltage winding, in multiples of 30°

**Example**

A **Dyn11** designation indicates: delta-connected high-voltage winding, wye-connected low-voltage winding with neutral brought out, and a phase displacement of 11 × 30° = 330° (equivalently, -30°, meaning the low-voltage phasor leads the high-voltage phasor by 30° in the common clock convention, though the precise leading/lagging sign convention depends on the reference standard used). [Inference] The exact sign convention (LV leading vs. lagging) can differ between regional standards and textbook treatments, so the clock-hour figure should always be interpreted alongside an explicit phasor diagram from the equipment documentation when precision matters.

#### Clock Notation Convention

**Key Points**

- The high-voltage winding phasor is conventionally treated as the "minute hand," fixed at 12 o'clock (0°)
- The low-voltage winding phasor position on the clock face indicates the phase displacement, with each "hour" representing 30°
- Common groups include 0 (0° shift, e.g., Yy0, Dd0), 6 (180° shift, e.g., Yy6), and 11 or 1 (±30° shift, e.g., Dyn11, Yd1)

### Vector Group Phasor Diagram (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 340">
<text x="320" y="20" text-anchor="middle" font-size="14" font-weight="bold">Vector Group Clock Notation — Example Dyn11 (svg_diagram)</text>
<circle cx="200" cy="180" r="100" fill="none" stroke="black" stroke-width="1.5" />
<text x="190" y="70" font-size="12">12</text>
<text x="290" y="185" font-size="12">3</text>
<text x="190" y="295" font-size="12">6</text>
<text x="95" y="185" font-size="12">9</text>
<line x1="200" y1="180" x2="200" y2="90" stroke="#1a5276" stroke-width="2.5" />
<text x="140" y="100" font-size="11" fill="#1a5276">HV Phasor (12 o'clock ref)</text>
<line x1="200" y1="180" x2="155" y2="97" stroke="#c0392b" stroke-width="2.5" />
<text x="60" y="90" font-size="11" fill="#c0392b">LV Phasor (11 o'clock, -30°)</text>
<text x="450" y="150" font-size="12">Each hour = 30°</text>
<text x="450" y="175" font-size="12">Hour 11 = 330° = -30°</text>
</svg>

### Zero-Sequence Impedance and Grounding Path Behavior

**Key Points**

- The presence and connection of a delta winding significantly affects zero-sequence impedance: a delta winding (anywhere in the transformer) provides a circulating path for zero-sequence (and third-harmonic) currents, trapping them within the delta and preventing their propagation to the other winding's line
- A grounded-wye winding provides a path to ground for zero-sequence current on that side; an ungrounded wye or delta winding does not
- This behavior is fundamental to system grounding design and ground fault current calculations — the vector group and grounding configuration together determine where ground fault current can flow

### Common Application-Driven Choices

#### Generator Step-Up (GSU) Transformers

**Key Points**

- Frequently connected Delta (generator side) – Wye grounded (system side), commonly designated Dyn (or Dy, depending on grounding treatment)
- Delta on the generator side prevents generator zero-sequence current contribution from circulating into the high-voltage system, while the grounded wye provides a system grounding point

#### Distribution Transformers

**Key Points**

- Often Dyn11 (or regional equivalent) to provide a grounded neutral for single-phase/three-phase mixed loads on the low-voltage side while using delta on the primary
- The specific standard vector group used varies by region/utility practice and applicable national/regional standards

### Parallel Operation Requirements

**Key Points**

- Transformers intended for parallel operation must have matching or compatible vector groups (identical phase displacement) — connecting transformers with mismatched phase shift creates a voltage difference that drives large circulating currents even under no-load conditions
- Beyond matching vector group, parallel operation also requires matching (or closely matched) per-unit impedance, voltage ratio, and, ideally, similar impedance angle (X/R ratio) to ensure proper load sharing between units
- [Unverified] Acceptable tolerance bands for voltage ratio and impedance mismatch in parallel operation are typically governed by utility engineering standards or IEC/IEEE guidance rather than a single universal numeric threshold

### IEC vs. ANSI/IEEE Naming Conventions

**Key Points**

- IEC 60076-1 uses the letter-plus-clock-hour vector group notation described above
- North American (ANSI/IEEE) practice historically has been less standardized around explicit vector group labeling on nameplates, often instead specifying connection type (e.g., "Delta-Wye") and relying on phasor diagrams or polarity markings for phase relationship documentation
- [Unverified] Practice varies significantly by utility, manufacturer, and equipment vintage in North America; the IEC vector group system has seen increasing adoption for clarity in multinational engineering documentation

### Related Topics

- Symmetrical components and sequence networks for transformers
- Zero-sequence circuit modeling and system grounding design
- Transformer differential protection and vector group compensation
- Grounding transformers and zigzag winding applications
- Parallel transformer operation: impedance and ratio matching criteria
- Generator step-up transformer design considerations
- Harmonic behavior in three-phase transformer banks
- Autotransformer three-phase connections and tertiary windings