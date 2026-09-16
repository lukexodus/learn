## Synchronous Generator Construction and Operation


### Overview

The synchronous generator (alternator) is the primary electromechanical device for large-scale electric power generation, converting mechanical shaft power from a prime mover (steam turbine, gas turbine, hydro turbine, diesel engine) into three-phase AC electrical power. Its defining characteristic is that rotor speed and electrical output frequency maintain a fixed ratio determined by pole count — hence "synchronous."

### Basic Construction

#### Stator (Armature)

**Key Points**

- Laminated silicon-steel core to minimize eddy current and hysteresis losses.
- Slotted inner bore holding a distributed three-phase winding (typically double-layer, short-pitched, and distributed across multiple slots per pole per phase).
- Windings are displaced 120 electrical degrees from each other to produce balanced three-phase EMF.
- Carries the load current and is the power-output winding (also called the armature winding).

#### Rotor (Field)

Two principal rotor constructions exist, distinguished by mechanical and application requirements:

| Feature | Salient-Pole Rotor | Cylindrical (Round) Rotor |
| --- | --- | --- |
| Pole shape | Projecting poles | Smooth, distributed slots |
| Typical prime mover | Hydraulic turbines (low speed) | Steam/gas turbines (high speed) |
| Pole count | Many (4–60+) | Few (2 or 4) |
| Speed range | Low (120–600 rpm typical) | High (1800–3600 rpm) |
| Mechanical strength | Lower (centrifugal limits) | Higher, suited to high speed |
| Air gap | Non-uniform | Uniform |
| Reactance behavior | $X_d \neq X_q$ (saliency) | $X_d \approx X_q$ |

**[Inference]** The salient-pole design is favored at low speeds because the larger pole count needed for 50/60 Hz output at low rpm is only mechanically practical with discrete projecting poles rather than a smooth cylindrical rotor, which is instead optimized for the high centrifugal stresses of high-speed turbine operation.

#### Field Excitation System

The rotor winding (field winding) carries DC current to establish the rotor magnetic field. Excitation methods:

1. **Brush-type (slip ring) excitation:** DC supplied externally via brushes and slip rings from a separate DC exciter or static (thyristor/rectifier) source.
2. **Brushless excitation:** A small AC exciter with rotating armature mounted on the same shaft; its output is rectified by a rotating rectifier assembly and fed directly to the field winding, eliminating brushes and slip rings.

**Key Points**

- Brushless systems reduce maintenance (no brush wear, no sparking) and are standard in most modern medium-to-large synchronous generators.
- Excitation control regulates terminal voltage and reactive power output via an automatic voltage regulator (AVR).

### Principle of Operation

#### EMF Generation

The rotor field winding, energized by DC, produces a rotating magnetic field when the rotor is driven by the prime mover. This rotating field sweeps past the stationary armature conductors, inducing a sinusoidal EMF in each phase winding by Faraday's Law.

The generated frequency relates to rotor speed and pole count by:

$$f = \frac{P \, n_s}{120}$$

where $f$ is frequency (Hz), $P$ is the number of poles, and $n_s$ is rotor speed (rpm). Equivalently, in terms of mechanical and electrical angular velocity:

$$\omega_e = \frac{P}{2} \, \omega_m$$

**Example**

A 4-pole synchronous generator must produce 60 Hz output. Required speed:

$$n_s = \frac{120 f}{P} = \frac{120 \times 60}{4} = 1800 \text{ rpm}$$

A hydro generator producing 60 Hz with a slow 100 rpm turbine requires:

$$P = \frac{120 f}{n_s} = \frac{120 \times 60}{100} = 72 \text{ poles}$$

This illustrates why hydro units are large-diameter, many-pole salient machines while turbo-generators are small-diameter, 2- or 4-pole cylindrical machines.

#### Generated EMF Magnitude

The RMS phase EMF per winding, from Faraday's Law applied to a distributed AC winding:

$$E = 4.44\, f\, N_{ph}\, \Phi_{max}\, k_w$$

where $N_{ph}$ is series turns per phase, $\Phi_{max}$ is peak flux per pole, and $k_w = k_d \, k_p$ is the winding factor (product of distribution factor $k_d$ and pitch factor $k_p$), which accounts for the spatial distribution and fractional-pitch construction of practical windings relative to an idealized concentrated, full-pitch winding.

**[Unverified]** Exact $k_d$ and $k_p$ values depend on the specific winding layout (slots per pole per phase, coil pitch) and must be computed from the winding design, not assumed universal.

### Equivalent Circuit and Armature Reaction

#### Armature Reaction

When the generator supplies load current, the resulting armature (stator) MMF interacts with the rotor field MMF, distorting and generally weakening or strengthening the net air-gap flux depending on load power factor:

- **Unity PF:** Cross-magnetizing effect (distorts flux distribution)
- **Lagging PF (inductive load):** Demagnetizing effect (reduces net flux, requires increased excitation to hold voltage)
- **Leading PF (capacitive load):** Magnetizing effect (increases net flux, can cause over-voltage if excitation isn't reduced)

#### Per-Phase Equivalent Circuit (Round Rotor / Cylindrical)

The combined effect of armature reaction and actual leakage reactance is modeled as **synchronous reactance** $X_s$:

$$X_s = X_{ar} + X_l$$

where $X_{ar}$ is the armature-reaction reactance and $X_l$ is the leakage reactance. Terminal voltage equation per phase:

$$\vec{E}_A = \vec{V}_\phi + I_A(R_A + jX_s)$$

where $E_A$ is the internally generated EMF, $V_\phi$ is terminal phase voltage, $I_A$ is armature current, and $R_A$ is armature resistance (often neglected relative to $X_s$ in large machines).

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 520 200" font-family="sans-serif">
<text x="260" y="20" font-size="14" text-anchor="middle" font-weight="bold">Per-Phase Equivalent Circuit — Round Rotor (svg_diagram)</text>
<circle cx="60" cy="110" r="28" fill="none" stroke="black" stroke-width="1.5" />
<text x="60" y="115" font-size="13" text-anchor="middle">E_A</text>
<line x1="88" y1="110" x2="140" y2="110" stroke="black" stroke-width="1.5" />
<rect x="140" y="95" width="45" height="30" fill="none" stroke="black" stroke-width="1.5" />
<text x="162" y="115" font-size="12" text-anchor="middle">R_A</text>
<line x1="185" y1="110" x2="215" y2="110" stroke="black" stroke-width="1.5" />
<path d="M 215 110 q 8 -12 16 0 q 8 -12 16 0 q 8 -12 16 0 q 8 -12 16 0" stroke="black" stroke-width="1.5" fill="none" />
<text x="247" y="90" font-size="12" text-anchor="middle">jX_s</text>
<line x1="279" y1="110" x2="330" y2="110" stroke="black" stroke-width="1.5" />
<line x1="330" y1="80" x2="330" y2="140" stroke="black" stroke-width="1.5" />
<text x="345" y="80" font-size="12">+</text>
<text x="345" y="145" font-size="12">−</text>
<text x="330" y="165" font-size="13" text-anchor="middle">V_φ (load)</text>
<line x1="60" y1="138" x2="60" y2="170" stroke="black" stroke-width="1.5" />
<line x1="60" y1="170" x2="330" y2="170" stroke="black" stroke-width="1.5" />
<line x1="330" y1="140" x2="330" y2="170" stroke="black" stroke-width="1.5" />
<text x="200" y="100" font-size="11" text-anchor="middle">I_A →</text>
</svg>

**Key Points**

- For salient-pole machines, $X_s$ splits into direct-axis ($X_d$) and quadrature-axis ($X_q$) synchronous reactance due to the non-uniform air gap; this is the basis of the **two-reaction theory**, generally treated as a distinct, more advanced analysis item.
- The synchronous reactance is typically far larger than armature resistance in machines above a few kW, so $R_A$ is frequently neglected for quick calculations, though this simplification degrades accuracy for efficiency and loss studies.

### Power and Torque Relationships

For a round-rotor generator connected to an infinite bus (constant $V_\phi$), neglecting $R_A$, the real power output per phase is:

$$P = \frac{E_A V_\phi}{X_s} \sin\delta$$

where $\delta$ is the torque angle (power angle) between $E_A$ and $V_\phi$. Reactive power output:

$$Q = \frac{E_A V_\phi \cos\delta - V_\phi^2}{X_s}$$

**Key Points**

- $\delta$ increases with mechanical power input from the prime mover; the generator "pulls ahead" of the terminal voltage phasor as more power is delivered.
- Maximum theoretical power transfer (steady-state stability limit) occurs at $\delta = 90°$: $P_{max} = E_A V_\phi / X_s$. Real machines operate well below this limit to maintain a stability margin.
- Excitation (field current) primarily controls $E_A$, and thus reactive power/terminal voltage, while prime-mover torque primarily controls $\delta$ and real power — these two control axes are largely decoupled in normal operation.

**Example**

A round-rotor generator: $E_A = 1.2$ pu, $V_\phi = 1.0$ pu, $X_s = 1.0$ pu, operating at $\delta = 25°$.

$$P = \frac{(1.2)(1.0)}{1.0}\sin(25°) = 1.2 \times 0.4226 \approx 0.507 \text{ pu}$$



$$Q = \frac{(1.2)(1.0)\cos(25°) - (1.0)^2}{1.0} = 1.2(0.9063) - 1 \approx 0.088 \text{ pu}$$

Both $P$ and $Q$ are positive, indicating the machine delivers real power and supplies (lagging/inductive-type) reactive power to the system at this operating point.

### Open-Circuit and Short-Circuit Characteristics

Two standard tests characterize generator performance:

1. **Open-Circuit Characteristic (OCC):** Terminal voltage vs. field current with the armature open — reveals the magnetization curve and saturation behavior of the machine, analogous to the core B–H curve reflected into terminal quantities.
2. **Short-Circuit Characteristic (SCC):** Armature current vs. field current with terminals short-circuited — typically linear (armature reaction dominates, keeping the core unsaturated) since the internal EMF is largely consumed by the (mostly reactive) short-circuit impedance drop.

The unsaturated synchronous reactance can be approximated from these curves:

$$X_{s,unsat} = \frac{V_{OC,rated}}{I_{SC} \text{ (at same } I_F\text{)}}$$

**[Unverified]** This ratio gives the unsaturated value; the saturated (adjusted) synchronous reactance used for accurate operating-point calculations typically requires correction via the short-circuit ratio (SCR) and air-gap line construction, a standard machine-testing procedure.

### Voltage Regulation

Voltage regulation quantifies terminal voltage rise from full load to no load at constant field current and speed:

$$VR = \frac{|E_A| - |V_\phi|}{|V_\phi|} \times 100\%$$

**Key Points**

- Lagging PF loads produce the highest (positive) voltage regulation — voltage drops most under load, requiring the field current to be highest at full load.
- Leading PF loads can produce **negative** voltage regulation — no-load voltage can be lower than full-load voltage, because the leading current's magnetizing armature reaction effectively adds to the field excitation.
- Voltage regulation is a static, steady-state figure of merit and does not describe dynamic/transient voltage behavior during faults or load steps.

### Parallel Operation and Synchronization

Before connecting a generator to a live bus/grid, the **synchronization conditions** must be satisfied:

1. Equal RMS voltage magnitude (generator vs. bus)
2. Equal frequency
3. Same phase sequence
4. Phase angles aligned (typically verified via synchroscope or synchronizing lamps)

**Key Points**

- Synchronizing out of phase or at mismatched frequency causes severe transient currents and mechanical torque shock, risking damage to the winding and shaft/coupling.
- Once synchronized (paralleled) to a large grid ("infinite bus"), the generator's terminal voltage and frequency are effectively fixed by the system; the operator controls real power via prime-mover torque/throttle and reactive power via field excitation.

### Losses and Efficiency

**Key Points**

- **Copper losses:** $I^2R$ in armature and field windings.
- **Core losses:** Hysteresis and eddy current losses in the laminated stator core.
- **Mechanical losses:** Friction and windage (bearings, cooling fans, rotor windage).
- **Stray load losses:** Additional losses from load current effects not captured in the above categories (leakage flux-induced eddy currents in structural parts, etc.).

$$\eta = \frac{P_{out}}{P_{out} + P_{losses}} \times 100\%$$

**[Unverified]** Typical utility-scale synchronous generator efficiencies are very high (commonly cited in the mid-to-high 90% range), but the exact figure depends strongly on machine rating, cooling method, and load point, and should be taken from manufacturer test data rather than assumed.

### Cooling Methods

Large synchronous generators require active cooling to manage $I^2R$ and core losses:

| Cooling Method | Typical Application |
| --- | --- |
| Air (open/closed-air circuit) | Small to medium machines |
| Hydrogen gas | Large turbo-generators (low windage loss, high thermal conductivity) |
| Direct water cooling (stator conductors) | Very large turbo-generators |

**[Inference]** Hydrogen cooling is used in large units specifically because hydrogen's low density reduces windage friction losses and its high thermal conductivity improves heat removal relative to air, at the cost of requiring sealed enclosures and explosion-safety systems.

### Common Pitfalls

**Key Points**

- Confusing salient-pole and round-rotor reactance models — applying single $X_s$ analysis to a salient machine ignores the reluctance-torque component from $X_d \neq X_q$.
- Treating field excitation as a real-power control — excitation primarily governs reactive power and terminal voltage, not real power, in grid-connected operation.
- Neglecting armature resistance is only a valid simplification for large machines/system-level studies; it is inappropriate for detailed loss or small-machine analysis.
- Assuming voltage regulation is always positive — leading power-factor loads can invert the sign.

### Related Topics

- Two-reaction theory and salient-pole $X_d$/$X_q$ analysis
- Parallel operation, load sharing, and governor droop characteristics
- Synchronous generator transient and subtransient reactance (fault analysis)
- Automatic voltage regulators (AVR) and excitation control systems
- Power system stability and the swing equation
- Synchronous motor operation (generator/motor duality)
- Per-unit system for machine and power system analysis
- Generator protection schemes (differential, loss-of-excitation, out-of-step)