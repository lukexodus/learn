## Microgrid Architectures and Control Hierarchies


### Foundational Definition and Classification

**Key Points**

- A microgrid is a localized group of interconnected loads and distributed energy resources within clearly defined electrical boundaries, capable of operating connected to the main grid (grid-connected mode) or independently (islanded mode).
- The U.S. Department of Energy's widely referenced definition emphasizes that a microgrid must be able to disconnect from and reconnect to the main grid, enabling it to operate autonomously as needed.
- Microgrids are classified by application context: utility/community microgrids, campus/institutional microgrids, commercial/industrial microgrids, remote/off-grid microgrids, and military/critical-facility microgrids.

**Architectural topologies**

Microgrids are commonly categorized by their electrical architecture:

1. **AC microgrids**: Resources and loads interface via a common AC bus, using conventional synchronous or inverter-based generation with standard AC protection schemes; the dominant historical architecture due to compatibility with existing utility infrastructure.
2. **DC microgrids**: Resources and loads interface via a common DC bus, avoiding repeated AC-DC-AC conversion losses for inherently DC sources (PV, batteries) and loads (LED lighting, data centers, EV charging); gaining traction in data centers and specific industrial applications.
3. **Hybrid AC/DC microgrids**: Combine both bus types connected via bidirectional interlinking converters, allowing DC-native resources to interface efficiently with the DC bus while maintaining AC compatibility for conventional loads and grid interconnection.

### Core Physical Components

**Key Points**

- A microgrid's physical layer comprises generation resources, energy storage, loads, the point of common coupling (PCC), and protection/switching equipment.
- The Point of Common Coupling is the critical interface point where the microgrid connects to the upstream utility distribution system, and where islanding/reconnection switching occurs.
- Energy storage is functionally essential (not merely optional) in most islanded-capable microgrids, providing the inertia, frequency support, and black-start capability that inverter-based generation alone typically cannot provide without storage buffering.

**Typical component inventory**

- Distributed generation: photovoltaic arrays, wind turbines, diesel/natural gas generators, combined heat and power (CHP) units, fuel cells.
- Energy storage systems: lithium-ion battery energy storage systems (BESS), flywheels (for fast frequency response), and increasingly, hydrogen-based long-duration storage.
- Point of Common Coupling (PCC) breaker/switch: the physical device executing intentional islanding and resynchronization.
- Protection and metering infrastructure: relays coordinated for both grid-connected fault current levels (higher, utility-fed) and islanded fault current levels (much lower, inverter-limited).
- Microgrid Controller: the supervisory control system coordinating all of the above (detailed in the control hierarchy section below).

### Microgrid Control Hierarchy

**Key Points**

- Microgrid control is universally structured as a three-tier hierarchy: primary, secondary, and tertiary control, mirroring the analogous hierarchy used in traditional bulk power system control but operating on much faster timescales appropriate to a smaller, more volatile system.
- Each control tier operates on a progressively slower timescale and addresses a progressively broader scope, from millisecond-level device response to minute/hour-level economic optimization.
- This hierarchical separation allows fast local stability functions to remain functional even if higher-level communication or optimization layers experience latency or failure.

**Tier 1: Primary Control**

- **Timescale**: Milliseconds to seconds.
- **Function**: Local, decentralized control operating at the individual inverter/generator level, requiring no communication with other units.
- **Key technique — droop control**: Inverter-based resources emulate the frequency and voltage droop characteristics of synchronous generators, autonomously adjusting active and reactive power output based on locally measured frequency and voltage deviations, enabling stable parallel operation of multiple inverters without a central coordinator.

$$f = f_0 - m_p (P - P_0)$$



$$V = V_0 - n_q (Q - Q_0)$$

Where $f_0$ and $V_0$ are nominal frequency and voltage setpoints, $m_p$ and $n_q$ are the droop coefficients (frequency-active power and voltage-reactive power respectively), $P$ and $Q$ are measured output power, and $P_0$, $Q_0$ are reference power setpoints.

**Tier 2: Secondary Control**

- **Timescale**: Seconds to minutes.
- **Function**: Restores frequency and voltage to nominal values after primary droop control introduces steady-state deviation, and synchronizes the microgrid for reconnection to the main grid.
- **Key technique**: A centralized or distributed secondary controller (often implemented within the Microgrid Controller) issues small corrective signals to individual unit setpoints, eliminating the droop-induced steady-state error while maintaining proportional load sharing among generation sources.

**Tier 3: Tertiary Control**

- **Timescale**: Minutes to hours (and day-ahead planning).
- **Function**: Economic dispatch and optimization — determining the optimal operating setpoints for each resource to minimize cost, maximize renewable utilization, or achieve other objectives (demand charge management, DR participation, wholesale market bidding under FERC Order 2222 if grid-connected).
- **Key technique**: Model Predictive Control (MPC) or mixed-integer linear/nonlinear programming (MILP/MINLP) optimization, incorporating load forecasts, renewable generation forecasts, storage state-of-charge constraints, and fuel/energy cost curves.

### Control Hierarchy Timescale and Function Map (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 880 380" font-family="Arial, sans-serif">
<text x="440" y="26" font-size="17" font-weight="bold" text-anchor="middle">Microgrid Control Hierarchy (svg_diagram)</text>
<rect x="60" y="280" width="760" height="70" rx="8" fill="#dbeafe" stroke="#2563eb" stroke-width="2" />
<text x="440" y="305" font-size="14" font-weight="bold" text-anchor="middle">Tier 1 — Primary Control</text>
<text x="440" y="323" font-size="11" text-anchor="middle" fill="#333">Droop control · ms–s timescale · local, decentralized · voltage/frequency regulation</text>
<text x="440" y="340" font-size="10" text-anchor="middle" fill="#666">No inter-unit communication required</text>
<rect x="60" y="190" width="760" height="70" rx="8" fill="#fef3c7" stroke="#d97706" stroke-width="2" />
<text x="440" y="215" font-size="14" font-weight="bold" text-anchor="middle">Tier 2 — Secondary Control</text>
<text x="440" y="233" font-size="11" text-anchor="middle" fill="#333">Restoration of nominal f/V · s–min timescale · resync for reconnection</text>
<text x="440" y="250" font-size="10" text-anchor="middle" fill="#666">Centralized/distributed correction to droop offsets</text>
<rect x="60" y="100" width="760" height="70" rx="8" fill="#dcfce7" stroke="#16a34a" stroke-width="2" />
<text x="440" y="125" font-size="14" font-weight="bold" text-anchor="middle">Tier 3 — Tertiary Control</text>
<text x="440" y="143" font-size="11" text-anchor="middle" fill="#333">Economic dispatch, MPC optimization · min–hr timescale</text>
<text x="440" y="160" font-size="10" text-anchor="middle" fill="#666">Forecasts, market bidding, storage scheduling</text>
<line x1="440" y1="100" x2="440" y2="60" stroke="#333" stroke-width="1.5" marker-end="url(#up)" />
<text x="440" y="50" font-size="11" text-anchor="middle">Grid-connected: RTO/ISO or utility DERMS interface</text>
<line x1="440" y1="190" x2="440" y2="170" stroke="#333" stroke-width="1" />
<line x1="440" y1="280" x2="440" y2="260" stroke="#333" stroke-width="1" />
</svg>

### Control Architecture Paradigms

**Key Points**

- Beyond the vertical primary/secondary/tertiary hierarchy, microgrid control systems are also classified horizontally by architecture paradigm: centralized, decentralized, and distributed (hierarchical/multi-agent).
- Each paradigm trades off communication burden, single-point-of-failure risk, scalability, and optimization quality differently.

**Centralized control**

A single Microgrid Central Controller (MGCC) collects data from all resources and issues direct setpoint commands. Advantages include globally optimal dispatch and simpler coordination logic; disadvantages include a single point of failure and high communication bandwidth/latency requirements that scale poorly with microgrid size.

**Decentralized control**

Each resource makes control decisions based solely on local measurements (as in pure primary droop control) with no communication to other units or a central controller. This maximizes resilience and scalability but sacrifices system-wide optimization and coordination precision.

**Distributed (multi-agent) control**

Individual "agent" controllers (often one per resource or feeder segment) communicate with a limited set of neighboring agents (rather than a central authority) to achieve consensus on system-wide variables (such as average frequency deviation or proportional load sharing), commonly implemented using consensus algorithms. This paradigm is increasingly favored in modern research and emerging commercial systems as a middle ground offering good scalability, fault tolerance (no single point of failure), and near-optimal coordination.

### Control Architecture Comparison

| Attribute | Centralized | Decentralized | Distributed (Multi-Agent) |
| --- | --- | --- | --- |
| Communication requirement | High (all-to-one) | None | Moderate (neighbor-to-neighbor) |
| Single point of failure | Yes (MGCC) | No | No |
| Optimization quality | Highest (global optimum) | Lowest (local only) | Near-optimal (consensus-based) |
| Scalability | Poor for large microgrids | Excellent | Good |
| Typical implementation | Small/simple microgrids | Primary droop layer (universal) | Emerging in academic/advanced commercial systems |

### Islanding, Grid Synchronization, and Black Start

**Key Points**

- Islanding transition (intentional or unintentional) requires the microgrid to rapidly shift from grid-following control (where inverters synchronize to an externally imposed grid voltage/frequency reference) to grid-forming control (where at least one resource must establish and maintain the voltage/frequency reference autonomously).
- Grid-forming inverters (as opposed to conventional grid-following inverters) are essential for microgrids intended to island, since without a synchronous generator or grid-forming inverter, there is no voltage/frequency reference for other resources to follow once disconnected from the utility.
- Resynchronization requires matching voltage magnitude, frequency, and phase angle across the PCC breaker before reclosing, to avoid a damaging out-of-phase reconnection transient.

**Black start capability**

For a microgrid to recover from a complete de-energization (a full blackout within the microgrid boundary), at least one resource must be capable of black start — energizing the system from a zero-voltage condition without relying on an external grid reference. This is typically provided by a diesel/gas generator with self-excitation capability or a battery energy storage system configured with grid-forming inverter control.

### Practical Example: Campus Microgrid Islanding Sequence

Consider a university campus microgrid with 2 MW solar PV, a 3 MW / 6 MWh BESS, one 2.5 MW diesel generator, and critical/non-critical load segregation.

1. **Trigger detection**: An upstream utility fault is detected via loss-of-voltage/frequency-excursion sensing at the PCC, or the microgrid controller receives a planned-islanding command ahead of forecasted severe weather.
2. **Load shedding (if needed)**: If total available generation is insufficient for full campus load, the tertiary control layer sheds pre-designated non-critical load segments (e.g., non-essential HVAC, decorative lighting) based on a pre-configured priority table.
3. **PCC breaker opening**: The PCC breaker opens, electrically isolating the microgrid.
4. **Grid-forming transition**: The BESS inverter (pre-configured as the primary grid-forming resource) immediately establishes local voltage and frequency reference; the diesel generator and PV inverters transition to grid-following relative to this new internal reference.
5. **Secondary control stabilization**: Within seconds, secondary control corrects any droop-induced frequency/voltage offset back to nominal (or a slightly adjusted islanded-mode nominal).
6. **Tertiary re-optimization**: The economic dispatch layer re-solves the optimization problem under islanded constraints, prioritizing PV utilization and managing BESS state-of-charge to sustain critical loads for the anticipated outage duration.

**Output**

The critical loads (data center, hospital/health-center building, emergency operations center) remain continuously energized throughout the utility outage, with the campus microgrid operating autonomously until utility service is restored and a synchronized reconnection sequence is executed by the secondary control layer.

### Related Topics

- Grid-Forming vs. Grid-Following Inverter Control
- Droop Control Design and Parameter Tuning
- Model Predictive Control (MPC) for Microgrid Economic Dispatch
- Protection Coordination Challenges in Low-Fault-Current Islanded Systems
- Black Start Procedures and Resource Sequencing
- DC Microgrid Bus Voltage Regulation Standards
- Multi-Agent Consensus Algorithms for Distributed Energy Control
- Microgrid Resilience Metrics and Critical Load Prioritization Frameworks