## Instrument Transformers and Metering Equipment


### Overview

Instrument transformers are precision devices that scale high-voltage/high-current primary system quantities down to standardized, safe secondary levels suitable for connection to protective relays, meters, and control equipment. They serve two purposes simultaneously: **electrical isolation** of secondary equipment and personnel from dangerous primary voltages/currents, and **accurate signal transformation** preserving the waveform characteristics needed for both revenue metering and protection.

Two families exist: **Current Transformers (CTs)**, which reproduce primary current as a proportional secondary current, and **Voltage Transformers (VTs)**, which reproduce primary voltage as a proportional secondary voltage. Both must meet accuracy and performance standards that differ substantially depending on whether they serve metering or protection functions.

### Current Transformers (CTs)

#### Operating Principle

A CT is fundamentally a transformer with the primary winding carrying full line current (often just a single pass of the busbar/cable through a toroidal core) and a secondary winding delivering a scaled-down current, standardized to either 5 A or 1 A nominal secondary at rated primary current.

$$I_{secondary} = I_{primary} \times \frac{N_1}{N_2}$$

where $N_1/N_2$ is the turns ratio (often $N_1 = 1$ for bar-primary designs).

**Critical operational rule**: A CT secondary circuit must never be open-circuited while the primary is energized. With an open secondary, all primary ampere-turns become magnetizing ampere-turns, driving the core into deep saturation and producing dangerously high secondary voltage spikes (potentially several kV), posing shock hazard and risking insulation breakdown. CT secondary terminals must be short-circuited before disconnecting any secondary-side equipment.

#### CT Construction Types

- **Wound-type**: primary winding has multiple turns, used for lower current ratings
- **Bar-type / bushing-type**: primary is a single straight conductor (bar) passing through the core, common in HV applications and often integrated into circuit breaker or transformer bushings
- **Window-type / toroidal**: core surrounds an existing conductor (busbar or cable) without a dedicated primary winding — standard configuration in GIS and many outdoor HV CTs
- **Optical/electronic CTs**: use Faraday effect (magneto-optic) sensing or Rogowski coil principles rather than iron-core magnetics, increasingly used in digital substations for direct digital output (see Emerging Tech note below)

#### CT Accuracy Classes

Two distinct duty categories with different design priorities:

**Metering CTs**: must be highly accurate near rated current (typically 1.0-1.2x rated) for correct revenue billing, but are permitted (and by design intended) to saturate at high fault currents to protect connected metering equipment from damage.

- IEC accuracy classes: 0.1, 0.2, 0.2S, 0.5, 0.5S, 1.0 (percentage error at rated conditions)
- IEEE/ANSI metering accuracy classes: 0.3, 0.6, 1.2 (designated by accuracy class and burden rating, e.g., "0.3B0.5")

**Protection CTs**: must remain reasonably accurate through very high fault currents (many times rated current) so that protective relays see a faithful, unsaturated representation of the fault for correct operation.

- IEC accuracy classes: 5P, 10P (5% or 10% composite error) followed by an Accuracy Limit Factor (ALF), e.g., "5P20" means 5% error up to 20x rated current
- IEC "PX" (formerly "X") class: defines CT performance via knee-point voltage, exciting current, and secondary resistance — used for differential and high-impedance protection schemes requiring precisely characterized, low-remanence behavior
- IEEE/ANSI protection classes: C and T classes (e.g., "C400") specifying secondary terminal voltage capability without exceeding 10% ratio error at 20x rated current
- [Inference] The continued relevance of remanence-sensitive protection CT design (particularly for high-impedance bus differential schemes) means PX/knee-point specification remains standard practice for critical protection applications, even as many general-purpose protection functions have become more tolerant of moderate CT saturation due to improved numerical relay saturation-detection algorithms.

#### Burden

The "burden" is the total impedance connected to the CT secondary (relay coils, meters, lead wire resistance), expressed in VA at rated secondary current or as an impedance value. Exceeding the CT's rated burden for its accuracy class degrades measurement accuracy and increases saturation risk during faults. Long secondary lead runs in large substations are a common source of burden underestimation during design.

### Voltage Transformers (VTs)

#### Electromagnetic Voltage Transformers (EVTs / "PTs")

Conventional wound transformers, similar in principle to power transformers but designed for negligible primary current draw and precise ratio accuracy across a defined voltage range (typically 80-120% of rated voltage for metering, wider for protection).

- Primary winding connects phase-to-ground (or phase-to-phase in some three-phase configurations)
- Secondary typically standardized to 120 V or 110 V line-to-neutral (varies by regional practice)
- Used across the full voltage spectrum but become physically large and costly at EHV/UHV levels due to insulation requirements for the full-voltage primary winding

#### Capacitive Voltage Transformers (CVTs / CCVTs)

At transmission and higher voltages, a capacitive divider reduces the voltage to an intermediate level before a smaller electromagnetic transformer completes the step-down to standard secondary voltage. This avoids the cost and bulk of a full electromagnetic transformer designed for the complete primary voltage.

**Construction:**

- A capacitor stack ($C_1$ in series with $C_2$) divides the primary voltage
- An intermediate voltage (typically a few kV) appears across $C_2$
- A compensating reactor and an intermediate transformer complete the step-down to standard secondary voltage, with the reactor tuned to cancel the capacitive divider's reactive impedance at power frequency

$$V_{intermediate} = V_{primary} \times \frac{C_1}{C_1 + C_2}$$

- **Key Points**
  - Economical at 145 kV and above compared to full electromagnetic VTs
  - The capacitor stack can double as a coupling capacitor for power-line carrier (PLC) communication, providing an economic secondary function
  - Exhibits transient response limitations: CVTs can produce a subsidence transient (a decaying oscillatory output) following a sudden primary voltage collapse, which can affect fast distance protection schemes — a well-documented characteristic requiring relay manufacturers to apply specific filtering/compensation algorithms
  - Ferroresonance is a known risk in CVT design, arising from interaction between the capacitor stack and the intermediate transformer's nonlinear magnetizing inductance; ferroresonance-suppression circuits are a standard design inclusion
- [Unverified] Specific subsidence transient magnitude and duration are highly dependent on individual CVT design parameters (capacitance values, compensating reactor tuning, burden), so generalized statements about transient severity should not be applied across all CVT models without manufacturer-specific data.

#### VT Accuracy Classes

Similar structural logic to CTs: metering VTs are optimized for high accuracy near rated voltage; protection VTs must maintain acceptable accuracy across a wider voltage range including depressed voltages during faults (since protection must operate correctly precisely when voltage is abnormal).

- IEC: 0.1, 0.2, 0.5, 1.0, 3.0 (metering); 3P, 6P (protection)
- IEEE/ANSI: 0.3, 0.6, 1.2 accuracy classes with defined burden ratings (W, X, Y, Z, ZZ burden designations)

### CT vs VT Summary Comparison

| Attribute | Current Transformer (CT) | Voltage Transformer (VT) |
| --- | --- | --- |
| Primary connection | In series with the line | In parallel (shunt) with the line |
| Secondary condition rule | Never open-circuit | Never short-circuit |
| Standard secondary rating | 5 A or 1 A | 120 V or 110 V (line-to-neutral, typical) |
| Failure mode if misused | Dangerous secondary overvoltage | Excessive secondary current, potential damage |
| Common HV/EHV variant | Bushing/bar-type, optical | Capacitive voltage transformer (CVT) |

### Metering Equipment

#### Revenue Metering Architecture

Utility-grade revenue meters connect to metering-class CTs and VTs (never protection-class instrument transformers, due to their differing accuracy behavior) to measure:

- **Active energy (kWh)**: real power consumption over time
- **Reactive energy (kVARh)**: reactive power consumption, relevant for power factor billing and grid reactive support compensation
- **Demand (kW, kVA)**: peak power draw over defined intervals, often the basis for demand charges in commercial/industrial billing
- **Power quality parameters**: voltage sag/swell events, harmonic content, flicker — increasingly captured by modern meters for both billing disputes and grid diagnostics

#### Modern Metering Trends

- **Revenue-grade digital meters**: replace electromechanical (induction disk) meters with solid-state designs offering higher accuracy classes (0.2S, 0.1S), remote communication, and multi-parameter logging
- **Advanced Metering Infrastructure (AMI)**: two-way communicating meters enabling remote read, outage detection, and time-of-use billing — a major utility modernization theme globally, including in Philippine distribution utility contexts where AMI rollout supports both revenue protection and grid visibility objectives
- **Revenue metering accuracy verification**: periodic on-site testing using portable reference standards to confirm meter and instrument transformer combination accuracy remains within tariff-mandated tolerances

### Emerging Technology: Non-Conventional Instrument Transformers (NCITs)

Digital substation architectures (per IEC 61850-9-2, "Sampled Values") increasingly employ non-conventional instrument transformers that digitize the measured quantity close to the primary conductor and transmit data via fiber-optic Ethernet rather than analog copper wiring to the control building.

- **Rogowski coils**: air-core current sensors (no iron core, hence no saturation) producing an output proportional to the *derivative* of primary current, requiring integration (analog or digital) to recover the current waveform
- **Optical CTs**: exploit the Faraday magneto-optic effect, where polarized light passing through a sensing fiber wound around the conductor experiences a rotation proportional to the enclosed current
- **Capacitive/resistive divider-based optical VTs**: combine a conventional divider principle with fiber-optic transmission of the digitized signal

**Advantages:**

- Elimination of CT saturation and ferroresonance risk (for non-iron-core designs)
- Reduced copper wiring, weight, and installation complexity in the substation yard
- Inherent electrical isolation via fiber optic signal transmission (no metallic path for ground potential rise to travel)

**Adoption considerations:**

- Requires compatible IEC 61850-9-2 Sampled Values-capable protective relays and merging units
- Represents a still-maturing technology relative to century-old electromagnetic CT/VT practice, with utility adoption proceeding cautiously and often via pilot installations before broad fleet-wide deployment
- [Speculation] The pace and extent of NCIT adoption relative to conventional electromagnetic instrument transformers varies substantially by utility, region, and substation voltage class; while digital substation architectures are an active industry direction, conventional CTs/VTs remain the dominant installed base globally as of this writing, and the timeline for any broader displacement is not established.

### Instrument Transformer Signal Path (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 300" font-family="sans-serif">
<text x="340" y="24" text-anchor="middle" font-size="16" font-weight="bold">CT/VT Signal Path to Relay and Meter (svg_diagram)</text>

<line x1="40" y1="80" x2="640" y2="80" stroke="#333" stroke-width="4" />
<text x="40" y="65" font-size="12">Primary Conductor (HV)</text>

<circle cx="200" cy="80" r="22" fill="none" stroke="#c0392b" stroke-width="2.5" />
<text x="200" y="115" text-anchor="middle" font-size="10">CT (series)</text>

<g transform="translate(400,80)">
<line x1="0" y1="0" x2="0" y2="40" stroke="#2b6de0" stroke-width="2.5" />
<circle cx="0" cy="55" r="14" fill="none" stroke="#2b6de0" stroke-width="2" />
<circle cx="0" cy="80" r="14" fill="none" stroke="#2b6de0" stroke-width="2" />
<text x="0" y="105" text-anchor="middle" font-size="10">VT (shunt)</text>
</g>

<line x1="200" y1="102" x2="200" y2="180" stroke="#c0392b" stroke-width="1.5" stroke-dasharray="4,2" />
<line x1="400" y1="94" x2="400" y2="180" stroke="#2b6de0" stroke-width="1.5" stroke-dasharray="4,2" />

<line x1="200" y1="180" x2="140" y2="220" stroke="#c0392b" stroke-width="1.5" />
<line x1="200" y1="180" x2="260" y2="220" stroke="#c0392b" stroke-width="1.5" />
<line x1="400" y1="180" x2="340" y2="220" stroke="#2b6de0" stroke-width="1.5" />
<line x1="400" y1="180" x2="460" y2="220" stroke="#2b6de0" stroke-width="1.5" />
<rect x="90" y="220" width="100" height="40" fill="#f9e0e0" stroke="#333" stroke-width="1.5" />
<text x="140" y="244" text-anchor="middle" font-size="10">Protection CT core</text>
<rect x="210" y="220" width="100" height="40" fill="#e0eaf9" stroke="#333" stroke-width="1.5" />
<text x="260" y="244" text-anchor="middle" font-size="10">Metering CT core</text>
<rect x="290" y="220" width="100" height="40" fill="#f9e0e0" stroke="#333" stroke-width="1.5" />
<text x="340" y="244" text-anchor="middle" font-size="10">Protection VT winding</text>
<rect x="410" y="220" width="100" height="40" fill="#e0eaf9" stroke="#333" stroke-width="1.5" />
<text x="460" y="244" text-anchor="middle" font-size="10">Metering VT winding</text>

<text x="140" y="280" text-anchor="middle" font-size="10">→ Protective Relay</text>

<text x="460" y="280" text-anchor="middle" font-size="10">→ Revenue Meter</text>

</svg>

### Practical Example: CT Sizing for a Bus Differential Scheme

Scenario: A 34.5 kV bus differential protection scheme requires CTs on each of four feeder/transformer positions to be matched for accurate differential comparison.

1. Determine the maximum through-fault current the bus could experience (e.g., 25 kA symmetrical)
2. Select a common CT ratio across all four positions (matching ratios is mandatory for simple percentage differential schemes; ratio-matching auxiliary CTs or software ratio compensation is required if physical ratios cannot be matched)
3. Specify PX class (or equivalent) CTs with a knee-point voltage sufficiently high to remain unsaturated through the maximum through-fault current, accounting for secondary lead resistance and relay burden
4. Calculate required knee-point voltage using the manufacturer's or scheme's specified formula, typically incorporating the maximum fault current, CT ratio, and total secondary loop resistance
5. Verify all four CTs share consistent magnetizing characteristics (minimizing spill current during external faults) — critical for high-impedance differential scheme stability
6. Document CT nameplate ratios, accuracy class, and knee-point voltage in the protection setting record for future commissioning verification

**Conclusion**

Instrument transformers are the sensory foundation of both revenue metering and protective relaying — their accuracy class, burden capacity, and saturation behavior directly determine whether downstream equipment sees a trustworthy representation of system conditions. The metering/protection accuracy-class distinction reflects fundamentally different design priorities: metering CTs/VTs must be precise near normal operating conditions and are permitted to saturate during faults, while protection CTs/VTs must sacrifice some near-rated precision to remain usably accurate during the very fault conditions protection schemes exist to detect. The ongoing shift toward optical and Rogowski-coil-based non-conventional instrument transformers in digital substations represents a fundamental rethinking of this century-old measurement architecture, though conventional electromagnetic designs remain the dominant installed technology.

**Related Topics**

- Protective relay coordination and differential protection schemes
- Circuit breaker technologies and interrupting media
- Gas-insulated switchgear (GIS) integration of CTs/VTs
- IEC 61850 digital substation architecture and Sampled Values (9-2LE)
- Power quality monitoring and harmonic analysis
- Ferroresonance phenomena in transformer-capacitor circuits
- High-impedance bus differential protection design
- Advanced Metering Infrastructure (AMI) and smart grid metering