## Wind Turbine Generator Technologies and Configurations


### Overview

Wind turbine generator technology defines how mechanical energy captured by the rotor is converted into electrical energy compatible with grid requirements. The evolution of wind turbine generator architecture has been driven largely by the need to handle variable wind speed (and hence variable rotor speed) while delivering grid-frequency-compliant, controllable electrical output. Four generator configurations, commonly designated **Type 1 through Type 4**, dominate industry classification and represent progressively greater use of power electronics to decouple mechanical rotor speed from electrical grid frequency.

### The Core Engineering Problem: Variable Speed vs. Fixed Frequency

A wind turbine rotor's optimal rotational speed for maximum aerodynamic efficiency varies with wind speed — the **tip-speed ratio** (ratio of blade tip speed to wind speed) has an optimum value for a given blade design, meaning rotor speed should ideally track wind speed to maximize energy capture.

$$\lambda = \frac{\omega_{rotor} \times R}{V_{wind}}$$

where $\lambda$ is the tip-speed ratio, $\omega_{rotor}$ is rotor angular velocity, $R$ is rotor radius, and $V_{wind}$ is wind speed.

However, the electrical grid operates at fixed frequency (50 or 60 Hz). A generator directly coupled to the grid without power electronics must spin at a speed fixed by that frequency and its pole count (synchronous speed) or very close to it (induction machine slip). This creates the fundamental tension that generator technology evolution has addressed: how to let the rotor speed vary with wind while still delivering fixed-frequency power to the grid.

### Type 1: Fixed-Speed Squirrel-Cage Induction Generator (SCIG)

The earliest widely deployed configuration, using a standard squirrel-cage induction generator connected directly to the grid (via a gearbox to step up rotor speed to generator speed) with no power electronic converter in the main power path.

- **Key Points**
  - Rotor speed variation is limited to the small slip range inherent to induction machines (typically 1-2% of synchronous speed) — effectively "fixed speed"
  - Requires a capacitor bank for reactive power (VAR) compensation, since induction generators consume reactive power for magnetization from the grid
  - A **soft-starter** (thyristor-based) is used during grid connection to limit inrush current
  - Cannot control active or reactive power independently — output is dictated directly by wind speed and grid conditions
  - Mechanical stress on the drivetrain is higher, since wind gusts translate more directly into torque/speed transients without an electrical buffer to absorb them
  - Largely obsolete for new utility-scale installations, though historically significant and still present in older wind farm fleets

### Type 2: Wound-Rotor Induction Generator with Variable Rotor Resistance (WRIG)

An evolution of Type 1 using a wound-rotor induction generator where external resistance can be inserted into (or varied within) the rotor circuit, typically via a power-electronic-controlled resistor bank mounted on the rotor.

- **Key Points**
  - Allows a limited slip range (typically up to about 10% above synchronous speed) by varying effective rotor resistance, providing modest speed variability compared to Type 1
  - Still requires external reactive power compensation (capacitor banks) since the machine remains fundamentally an induction generator
  - Provides some ability to smooth power output fluctuations during gusts by allowing limited speed change to absorb transient mechanical energy
  - Also largely superseded by Type 3 and Type 4 in current utility-scale turbine manufacture, though it represented an important intermediate step in variable-speed capability

### Type 3: Doubly-Fed Induction Generator (DFIG)

The dominant configuration in utility-scale wind turbines installed over roughly the past two decades, and still widely manufactured. Uses a wound-rotor induction generator where the stator connects directly to the grid, while the rotor circuit connects to the grid through a **partial-scale back-to-back power converter** (rotor-side converter and grid-side converter connected via a DC link).

#### Operating Principle

The power converter controls rotor current frequency and magnitude, allowing the rotor's electrical frequency to differ from the mechanical rotor speed's natural slip frequency — effectively decoupling mechanical speed from the fixed grid frequency seen at the stator, while only a fraction of total generator power (typically 25-30%) flows through the converter, since the stator (majority of power) remains directly grid-connected.

$$P_{converter} \approx s \times P_{rated}$$

where $s$ is the slip and $P_{rated}$ is rated generator power — illustrating why only a fraction of total power needs to pass through the converter, since slip is typically constrained to roughly $\pm 30\%$ of synchronous speed in DFIG designs.

- **Key Points**
  - **Partial-scale converter** (sized for only a fraction of total turbine power) is the key cost advantage of DFIG relative to Type 4 — a smaller, less expensive converter than one rated for full turbine power
  - Provides wide variable-speed operation (typically ±30% around synchronous speed), enabling significant aerodynamic efficiency gains across a range of wind speeds compared to fixed-speed designs
  - Enables independent active and reactive power control via the rotor-side converter, allowing the turbine to provide voltage/reactive power support to the grid
  - **Critical vulnerability**: because the stator is directly grid-connected, a grid fault (voltage sag) induces very high transient currents in the rotor circuit, historically risking damage to the rotor-side converter. This drove development of **crowbar protection** circuits, which short-circuit the rotor windings during severe faults to protect the converter, temporarily sacrificing controlled operation during the fault
  - Modern DFIG designs increasingly incorporate more sophisticated fault-ride-through control (active crowbar management, series grid-side impedance, or converter current limiting strategies) to meet increasingly stringent grid code Low-Voltage-Ride-Through (LVRT) requirements without full loss of control during faults
  - Requires a gearbox (multi-stage, typically 3-stage) to step up the relatively slow rotor speed (commonly 10-20 RPM for large turbines) to the induction generator's operating speed range
- [Inference] The continued widespread manufacture of DFIG-based turbines alongside the more fully decoupled Type 4 architecture reflects an ongoing cost/performance trade-off in the industry, where DFIG's lower converter cost remains attractive for many onshore applications despite Type 4's superior fault-ride-through characteristics and grid-support flexibility; the relative market share between the two continues to evolve and varies by manufacturer, turbine class, and target market (onshore versus offshore).

### Type 4: Full-Scale Converter Generator (Permanent Magnet Synchronous Generator or Induction Generator)

The generator (commonly a permanent magnet synchronous generator, PMSG, though wound-field synchronous or induction generators are also used) connects to the grid entirely through a **full-scale back-to-back power converter**, meaning 100% of generated power passes through power electronics.

#### Key Architectural Variants

- **Direct-drive PMSG**: eliminates the gearbox entirely, using a large-diameter, multi-pole permanent magnet generator that rotates at the same low speed as the rotor. Reduces drivetrain mechanical complexity and eliminates gearbox failure modes (a historically significant source of wind turbine downtime), at the cost of a physically larger, heavier generator
- **Geared PMSG or induction generator with full-scale converter**: retains a gearbox (often fewer stages than a DFIG's multi-stage gearbox) but still uses a full-scale converter, balancing generator size against drivetrain complexity

#### Advantages of Full Decoupling

- Complete electrical isolation between the generator and the grid via the DC link means grid faults do not directly stress the generator windings — dramatically simplifying fault-ride-through design compared to DFIG's crowbar-based approach
- Full independent control of active power, reactive power, and voltage support across the entire operating range, since the grid-side converter fully controls the grid-facing electrical interface
- Rotor speed range is essentially unconstrained by grid frequency considerations (limited only by mechanical/aerodynamic design), enabling optimal tip-speed-ratio tracking across the widest practical wind speed range
- Full-scale converters also enable more advanced grid-support functions increasingly required by modern grid codes: synthetic inertia response, fast reactive current injection during faults, and flexible power factor control
- **Key Points**
  - Higher power electronics cost than DFIG (converter rated for 100% of turbine power rather than ~30%), historically the primary cost disadvantage
  - Dominant in most new offshore wind turbine designs and increasingly common in new onshore designs, reflecting both improving power electronics cost trends and offshore projects' greater emphasis on reliability (favoring direct-drive designs that eliminate gearbox failure risk in hard-to-access offshore locations)
  - Direct-drive PMSG designs eliminate a major maintenance item (gearbox oil changes, bearing wear) but introduce their own considerations around large generator size/weight (relevant to tower-top mass and transport logistics) and permanent magnet material supply chain considerations (rare-earth elements such as neodymium)

### Comparative Summary

| Type | Generator | Converter | Speed Range | Gearbox | Grid Fault Behavior | Status |
| --- | --- | --- | --- | --- | --- | --- |
| Type 1 | Squirrel-cage induction | None | ~Fixed (1-2% slip) | Yes (multi-stage) | Direct exposure, no ride-through control | Largely obsolete |
| Type 2 | Wound-rotor induction | Rotor resistance control (no grid-connected converter) | Limited (~0-10% above sync) | Yes | Direct exposure, limited mitigation | Largely obsolete |
| Type 3 (DFIG) | Wound-rotor induction | Partial-scale (~25-30% of rating) | Wide (±30% of sync) | Yes (multi-stage) | Vulnerable; requires crowbar/active protection | Widely deployed, still manufactured |
| Type 4 | PMSG or induction | Full-scale (100% of rating) | Very wide (design-limited) | Optional (direct-drive eliminates it) | Fully decoupled, inherently robust | Dominant for new offshore, growing onshore share |

### Wind Turbine Power Conversion Chain (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 300" font-family="sans-serif">
<text x="350" y="24" text-anchor="middle" font-size="16" font-weight="bold">Type 3 (DFIG) vs Type 4 (Full Converter) Power Path (svg_diagram)</text>


<text x="20" y="80" font-size="12" font-weight="bold">Type 3 DFIG</text>

<rect x="90" y="60" width="70" height="40" fill="`#d6e4f0`" stroke="#333" stroke-width="1.5" />

<text x="125" y="84" text-anchor="middle" font-size="10">Rotor</text>

<line x1="160" y1="80" x2="200" y2="80" stroke="#333" stroke-width="2" />

<rect x="200" y="60" width="80" height="40" fill="`#f0e6d6`" stroke="#333" stroke-width="1.5" />

<text x="240" y="84" text-anchor="middle" font-size="10">Gearbox</text>

<line x1="280" y1="80" x2="320" y2="80" stroke="#333" stroke-width="2" />

<rect x="320" y="60" width="90" height="40" fill="`#e0d6f0`" stroke="#333" stroke-width="1.5" />

<text x="365" y="78" text-anchor="middle" font-size="9">WRIG</text>

<text x="365" y="90" text-anchor="middle" font-size="9">Stator</text>

<line x1="410" y1="70" x2="500" y2="70" stroke="#27ae60" stroke-width="3" />
<text x="455" y="62" text-anchor="middle" font-size="9" fill="#27ae60">Direct (~70-75%)</text>
<line x1="365" y1="100" x2="365" y2="130" stroke="#333" stroke-width="2" />
<rect x="320" y="130" width="90" height="30" fill="#f0d6d6" stroke="#333" stroke-width="1.5" />
<text x="365" y="150" text-anchor="middle" font-size="9">Partial Converter (~25-30%)</text>
<line x1="410" y1="145" x2="500" y2="145" stroke="#c0392b" stroke-width="2" />
<rect x="500" y="55" width="90" height="100" fill="#eee" stroke="#333" stroke-width="1.5" />
<text x="545" y="110" text-anchor="middle" font-size="10">Grid</text>


<text x="20" y="220" font-size="12" font-weight="bold">Type 4 PMSG</text>

<rect x="90" y="200" width="70" height="40" fill="`#d6e4f0`" stroke="#333" stroke-width="1.5" />

<text x="125" y="224" text-anchor="middle" font-size="10">Rotor</text>

<line x1="160" y1="220" x2="200" y2="220" stroke="#333" stroke-width="2" />

<text x="180" y="212" text-anchor="middle" font-size="8">(direct-drive:</text>

<text x="180" y="222" text-anchor="middle" font-size="8">no gearbox)</text>

<rect x="200" y="200" width="90" height="40" fill="`#e0d6f0`" stroke="#333" stroke-width="1.5" />

<text x="245" y="224" text-anchor="middle" font-size="10">PMSG</text>

<line x1="290" y1="220" x2="330" y2="220" stroke="#333" stroke-width="2" />

<rect x="330" y="200" width="110" height="40" fill="`#f0d6d6`" stroke="#333" stroke-width="1.5" />

<text x="385" y="224" text-anchor="middle" font-size="9">Full-Scale Converter (100%)</text>

<line x1="440" y1="220" x2="500" y2="220" stroke="`#c0392b`" stroke-width="3" />

<rect x="500" y="195" width="90" height="50" fill="#eee" stroke="#333" stroke-width="1.5" />

<text x="545" y="224" text-anchor="middle" font-size="10">Grid</text>

</svg>

### Grid Code Compliance Considerations

Modern grid codes (varying by jurisdiction/system operator) increasingly require wind turbines to provide grid-supportive behavior comparable to conventional synchronous generation:

- **Low-Voltage-Ride-Through (LVRT)/Fault-Ride-Through (FRT)**: remaining connected and, where possible, providing reactive current support during defined voltage sag depths and durations rather than tripping offline
- **Frequency response**: some grid codes require synthetic inertia emulation or governor-like frequency droop response, requiring the converter control system to temporarily extract additional kinetic energy from the rotor during a frequency event
- **Reactive power/power factor control**: ability to operate at a specified power factor range or provide voltage regulation at the point of interconnection
- **Ramp rate limiting**: constraining how quickly turbine output can change, relevant for grid stability during rapid wind speed changes
- [Inference] Type 4 (full-scale converter) architectures generally offer more flexible and robust means of meeting increasingly stringent grid code requirements than Type 3 (DFIG), since the full decoupling from the grid removes the fault-current exposure that DFIG's crowbar protection must manage, though DFIG turbines with modern active crowbar and enhanced control strategies can also meet many current grid code requirements — the specific compliance capability depends on the individual turbine model's control system design rather than generator type alone.

### Practical Example: Fault-Ride-Through Behavior Comparison

Scenario: A grid fault causes a voltage sag to 20% of nominal for 150 ms at the point of interconnection of a wind farm.

**DFIG (Type 3) response:**

1. Stator voltage collapse induces a large transient EMF in the rotor circuit due to direct magnetic coupling
2. Rotor-side converter current rises rapidly, approaching or exceeding converter current rating
3. Crowbar protection activates, short-circuiting rotor windings to protect the converter, temporarily surrendering torque/reactive power control
4. Once fault clears and voltage recovers, crowbar is deactivated and normal rotor-side converter control resumes
5. Modern designs may instead use active crowbar timing or series rotor-side impedance to minimize the duration of lost control, improving compliance with reactive current injection requirements during the fault

**Type 4 full-converter response:**

1. Generator remains electrically isolated from the grid disturbance by the DC link; generator-side converter continues normal operation largely unaffected by the grid fault
2. Grid-side converter current is limited by its own control system to stay within safe limits during the voltage sag, without requiring a crowbar-type protective short-circuit
3. Grid-side converter can inject reactive current to support voltage recovery throughout the fault duration, per grid code requirements
4. DC link voltage is managed (potentially with a chopper/braking resistor) to absorb the temporary power imbalance between generator-side power in and reduced grid-side power out during the sag

**Conclusion**

The Type 1 through Type 4 classification captures the wind industry's progressive adoption of power electronics to solve the fundamental variable-speed-rotor/fixed-frequency-grid problem. DFIG (Type 3) achieved wide variable-speed operation at a fraction of full-power converter cost by exploiting the induction machine's slip characteristics, becoming the dominant architecture for roughly two decades, while full-scale converter (Type 4) designs — particularly direct-drive PMSG — trade higher power electronics cost for complete grid decoupling, superior fault-ride-through characteristics, and simplified (or eliminated) gearbox requirements, driving their growing dominance in offshore and increasingly onshore applications where reliability and grid-support flexibility are prioritized.

**Related Topics**

- Wind farm collector system design and medium-voltage collection networks
- Grid code compliance and Low-Voltage-Ride-Through (LVRT) requirements
- Power electronic converter topologies for renewable integration
- Reactive power compensation and STATCOM/SVC applications in wind farms
- Wind turbine drivetrain and gearbox reliability considerations
- Offshore wind substation and HVDC export system design
- Synthetic inertia and frequency response from converter-interfaced generation
- Solar PV inverter technologies and grid-forming vs grid-following control