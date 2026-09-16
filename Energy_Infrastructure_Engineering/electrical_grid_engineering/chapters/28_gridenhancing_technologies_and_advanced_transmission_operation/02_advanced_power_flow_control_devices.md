## Advanced Power Flow Control Devices


### Concept and Motivation

**Key Points**

- Advanced Power Flow Control (APFC) devices are a category of Grid-Enhancing Technology that actively redirect power flow across transmission network paths by modifying line impedance, injecting a controlled voltage, or otherwise altering the electrical characteristics that determine how power naturally distributes across parallel transmission paths.
- The underlying motivation is that power flow on an AC transmission network is governed by the network's impedance characteristics (following Kirchhoff's laws), which often causes power to flow disproportionately along certain "path of least impedance" corridors while parallel, lower-impedance-utilized paths remain underused — creating congestion on some lines while others carry less than their full thermal capacity.
- APFC devices allow grid operators to actively rebalance this natural flow distribution, unlocking additional usable transfer capacity across a network without new transmission line construction, in a role complementary to Dynamic Line Rating.

### Fundamental Power Flow Control Principle

**Key Points**

- Real power flow across a transmission line is approximately governed by the voltage angle difference between its two ends and the line's reactance, meaning that changing a line's effective reactance (or injecting a controlled voltage/phase shift) directly changes how much power flows on that path relative to parallel paths.
- Series-connected devices (installed in line with the conductor) primarily control power flow by modifying effective line impedance or injecting a series voltage; shunt-connected devices primarily control voltage/reactive power at a bus; combined series-shunt devices can control both simultaneously.

**Simplified power flow equation**

$$P = \frac{V_1 V_2}{X} \sin(\delta_1 - \delta_2)$$

Where $P$ is real power flow along a line, $V_1$ and $V_2$ are the voltage magnitudes at each end, $X$ is the line's series reactance, and $(\delta_1 - \delta_2)$ is the voltage angle difference between the two ends. An APFC device that effectively modifies $X$ (as with a series capacitor/reactor) or introduces a controlled angle shift (as with a phase-shifting transformer) directly changes $P$ for a given angle difference, allowing operators to redirect flow toward underutilized parallel paths.

### Categories of Advanced Power Flow Control Devices

**Key Points**

- APFC devices span a spectrum from simple, well-established electromechanical devices (phase-shifting transformers) to sophisticated power-electronics-based FACTS (Flexible AC Transmission System) devices offering continuous, fast-response control.
- FACTS devices are generally classified by connection topology: series-connected, shunt-connected, and combined series-shunt (unified) controllers.
- Distribution-level power flow control devices have also emerged more recently, addressing similar congestion and flow-balancing challenges at the distribution system level as DER penetration increases.

**Phase-Shifting Transformers (PSTs)**

PSTs introduce a controllable phase angle shift between their input and output terminals, directly influencing the power flow equation's angle-difference term. They are a mature, well-proven technology (electromechanical tap-changing or, in some designs, power-electronic-assisted) widely deployed for decades to manage parallel-path flow, particularly at interconnections between utility systems or regions with known persistent flow-sharing imbalances.

**Series FACTS devices**

- **Thyristor-Controlled Series Capacitor (TCSC)**: A series capacitor bank with a parallel thyristor-controlled reactor, allowing continuous adjustment of the effective series reactance, providing fast-response flow control and can also help damp power system oscillations.
- **Static Synchronous Series Compensator (SSSC)**: A voltage-source-converter-based series device injecting a controllable series voltage largely independent of line current magnitude, offering more flexible control characteristics than a purely impedance-based series capacitor.

**Shunt FACTS devices**

- **Static VAR Compensator (SVC)**: A thyristor-controlled shunt reactive power device providing fast, continuous voltage support at a bus by dynamically adjusting reactive power absorption/injection.
- **Static Synchronous Compensator (STATCOM)**: A voltage-source-converter-based shunt device providing similar fast reactive power/voltage support to an SVC but with generally superior performance at low voltage conditions and a more compact footprint for a given reactive power rating.

**Combined series-shunt (unified) controllers**

- **Unified Power Flow Controller (UPFC)**: Combines a shunt converter and a series converter sharing a common DC link, enabling simultaneous, independent control of voltage magnitude, line reactance (effectively), and phase angle — offering the most comprehensive flow control capability among FACTS devices, at correspondingly higher cost and complexity.

**Distribution-level power flow control**

Emerging distribution-level devices (sometimes referred to under vendor-specific or evolving industry terminology such as distributed power flow controllers) apply similar active flow-redirection principles at the distribution feeder level, addressing thermal overload and voltage management challenges arising from increasing DER interconnection and bidirectional power flow on feeders originally designed for unidirectional flow.

### FACTS Device Classification (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 880 400" font-family="Arial, sans-serif">
<text x="440" y="26" font-size="17" font-weight="bold" text-anchor="middle">FACTS Device Classification by Connection Type (svg_diagram)</text>
<rect x="30" y="60" width="250" height="300" rx="8" fill="#dbeafe" stroke="#2563eb" stroke-width="2" />
<text x="155" y="90" font-size="13" font-weight="bold" text-anchor="middle">Series-Connected</text>
<rect x="55" y="110" width="200" height="50" rx="6" fill="#fff" stroke="#2563eb" />
<text x="155" y="140" font-size="11" text-anchor="middle">TCSC</text>
<rect x="55" y="175" width="200" height="50" rx="6" fill="#fff" stroke="#2563eb" />
<text x="155" y="205" font-size="11" text-anchor="middle">SSSC</text>
<rect x="55" y="240" width="200" height="50" rx="6" fill="#fff" stroke="#2563eb" />
<text x="155" y="270" font-size="11" text-anchor="middle">Phase-Shifting Transformer</text>
<text x="155" y="340" font-size="10" text-anchor="middle" fill="#555">Controls effective reactance / angle</text>
<rect x="315" y="60" width="250" height="300" rx="8" fill="#fef3c7" stroke="#d97706" stroke-width="2" />
<text x="440" y="90" font-size="13" font-weight="bold" text-anchor="middle">Shunt-Connected</text>
<rect x="340" y="110" width="200" height="50" rx="6" fill="#fff" stroke="#d97706" />
<text x="440" y="140" font-size="11" text-anchor="middle">SVC</text>
<rect x="340" y="175" width="200" height="50" rx="6" fill="#fff" stroke="#d97706" />
<text x="440" y="205" font-size="11" text-anchor="middle">STATCOM</text>
<text x="440" y="340" font-size="10" text-anchor="middle" fill="#555">Controls bus voltage / reactive power</text>
<rect x="600" y="60" width="250" height="300" rx="8" fill="#dcfce7" stroke="#16a34a" stroke-width="2" />
<text x="725" y="90" font-size="13" font-weight="bold" text-anchor="middle">Combined Series-Shunt</text>
<rect x="625" y="110" width="200" height="50" rx="6" fill="#fff" stroke="#16a34a" />
<text x="725" y="140" font-size="11" text-anchor="middle">UPFC</text>
<text x="725" y="340" font-size="10" text-anchor="middle" fill="#555">Independent V, X, angle control</text>
</svg>

### Device Comparison Table

| Device | Connection | Primary Control | Response Speed | Relative Complexity/Cost |
| --- | --- | --- | --- | --- |
| Phase-Shifting Transformer | Series | Phase angle | Slower (mechanical tap-changing, if not power-electronic-assisted) | Moderate |
| TCSC | Series | Effective series reactance | Fast (thyristor-controlled) | Moderate-High |
| SSSC | Series | Series-injected voltage | Fast (VSC-based) | High |
| SVC | Shunt | Reactive power / voltage | Fast (thyristor-controlled) | Moderate |
| STATCOM | Shunt | Reactive power / voltage | Very fast (VSC-based) | Moderate-High |
| UPFC | Series + Shunt | Voltage, reactance, angle (independent) | Very fast (VSC-based) | Highest |

### Application Selection and Planning Considerations

**Key Points**

- Device selection depends on the specific problem being addressed: pure thermal congestion redistribution across parallel paths favors series devices (PST, TCSC, SSSC), while voltage support and reactive power management favor shunt devices (SVC, STATCOM), and complex multi-objective needs may justify a UPFC's higher cost.
- Power system studies (power flow, transient stability, and often sub-synchronous resonance screening for series capacitive devices near certain generator types) are required to properly size and site any APFC device, since an improperly designed series compensation scheme can introduce new stability risks even while solving the original congestion problem.
- APFC devices are frequently evaluated as a lower-cost, faster-to-deploy alternative to new transmission line construction for relieving specific, well-characterized congestion points, making them an increasingly prominent element of FERC's ongoing Grid-Enhancing Technology and transmission planning reform discussions.

### Practical Example: Relieving Parallel-Path Congestion with a TCSC

Consider a transmission system with two parallel 345 kV paths between two regional load centers — Path A (shorter, lower impedance) and Path B (longer, higher impedance) — where Path A is chronically congested near its thermal limit while Path B carries substantially less than its thermal capacity, purely as a consequence of the natural impedance-driven flow split.

1. **Problem characterization**: Power flow studies confirm that Path A's lower impedance causes it to carry a disproportionate share of the total transfer, reaching its thermal limit and forcing costly redispatch or curtailment actions, while Path B has significant unused thermal headroom.
2. **TCSC sizing and siting**: Engineers size a TCSC for installation on Path A, calculating the additional effective series reactance needed to shift a target amount of flow from Path A onto Path B under typical and stressed operating conditions.
3. **Stability screening**: Sub-synchronous resonance screening studies are conducted given the presence of series capacitive compensation, confirming no adverse interaction with nearby generating units' shaft torsional modes.
4. **Installation and operational integration**: The TCSC is installed and integrated with the operator's EMS, allowing either automatic flow-based control or operator-adjusted reactance setpoints to actively manage the flow split between the two paths in real time as system conditions change.

**Output**

Following TCSC installation, the operator can actively rebalance flow between Path A and Path B in response to changing system conditions, reducing the frequency and severity of Path A congestion events and the associated redispatch costs — unlocking Path B's previously underutilized thermal capacity without new transmission line construction, at a fraction of the cost and lead time a new parallel line would have required.

### Related Topics

- Dynamic Line Rating
- Topology Optimization for Transmission Congestion Management
- Power System Stability and Sub-Synchronous Resonance
- Grid-Forming vs. Grid-Following Inverter Control
- Transmission Congestion Management in RTO/ISO Markets
- Reconductoring with High-Temperature Low-Sag (HTLS) Conductors
- FERC Transmission Planning Reform and Grid-Enhancing Technology Policy
- Voltage Stability and Reactive Power Management in Transmission Systems