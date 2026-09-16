## Flywheel Energy Storage

### Overview

Flywheel energy storage stores energy mechanically in the rotational kinetic energy of a spinning rotor, charging by using an electric motor to accelerate the flywheel and discharging by allowing the spinning rotor to drive the same machine in generator mode, decelerating the flywheel as kinetic energy converts back to electricity. Flywheels are characterized by very high power density, very fast response time, and exceptionally long cycle life (essentially unlimited full-depth cycling with minimal degradation, in contrast to electrochemical storage), but comparatively low energy density and significant standby (self-discharge) losses, positioning them primarily for short-duration, high-power, high-cycling grid applications rather than long-duration bulk energy storage.

### Fundamental Operating Principle

**Kinetic Energy Storage**

The energy stored in a rotating flywheel is given by:

$$E = \frac{1}{2} I \omega^2$$

Where $I$ is the rotor's moment of inertia (kg·m²) and $\omega$ is angular velocity (rad/s). For a solid cylindrical rotor, moment of inertia is:

$$I = \frac{1}{2} m r^2$$

Combining these relations shows that stored energy scales with the square of rotational speed, meaning increasing rotational speed is generally a far more effective lever for increasing energy storage than increasing rotor mass for a given rotor geometry—this quadratic speed dependence is the central design driver behind the historical trend toward higher-speed flywheel designs using advanced materials capable of withstanding the correspondingly higher mechanical stress.

```mermaid
flowchart LR
    A[Grid Electricity] --> B[Motor/Generator]
    B -->|Charging: accelerates rotor| C[Flywheel Rotor<br/>in vacuum enclosure]
    C -->|Discharging: rotor drives generator| B
    B --> D[Grid Electricity Out]
    C --- E[Magnetic Bearings]
```

### Rotor Design and Materials

**Steel (Low-Speed) Flywheels**

Traditional flywheel designs use steel rotors operating at relatively lower rotational speeds (typically up to roughly 10,000–15,000 RPM depending on rotor geometry), relying on steel's well-established material properties, manufacturability, and lower cost relative to advanced composite alternatives, generally achieving comparatively modest specific energy relative to composite designs.

**Composite (High-Speed) Flywheels**

Modern high-performance flywheel designs increasingly use carbon-fiber-reinforced composite rotors, capable of operating at substantially higher rotational speeds (commonly tens of thousands of RPM, with some designs exceeding 40,000–50,000 RPM) due to composite materials' superior strength-to-density ratio relative to steel, which is the governing material property for rotor burst safety margin at high rotational speed, since hoop stress in a spinning rotor scales with material density and the square of tip speed. This higher achievable speed, combined with the quadratic speed dependence of stored energy noted above, allows composite flywheels to achieve meaningfully higher specific energy (energy per unit mass) than steel flywheels, an important consideration for flywheel systems where footprint or mass constraints are relevant.

**Rotor Stress Limitation**

The maximum safe rotational speed for any flywheel rotor is fundamentally constrained by the material's tensile (hoop) strength, since centrifugal stress at the rotor's outer radius increases with the square of angular velocity; this relationship is the core engineering trade-off in flywheel rotor design, balancing achievable energy storage capacity against material strength, manufacturing precision, and burst-containment safety design.

### Supporting Subsystems

**Bearings**

Because flywheel rotors spin continuously at high speed for extended periods, bearing friction losses are a major factor in both achievable standby time (before energy is lost to friction) and overall round-trip efficiency:

- **Mechanical bearings:** Conventional rolling-element bearings, generally lower cost but with higher friction losses and more significant wear-related maintenance requirements than magnetic bearing alternatives, limiting their use in the highest-performance, longest-standby-time flywheel designs
- **Magnetic bearings:** Support the rotor via magnetic levitation rather than physical mechanical contact, essentially eliminating mechanical friction losses at the bearing interface (though not eliminating all parasitic losses, since magnetic bearing control systems themselves consume some power), substantially extending achievable standby time and reducing maintenance requirements relative to mechanical bearings, at higher system cost and control complexity

**Vacuum Enclosure**

High-speed flywheel rotors are typically housed within a vacuum (or near-vacuum) containment enclosure to minimize aerodynamic drag losses, since windage losses at the high rotor speeds characteristic of modern composite flywheel designs would otherwise represent a very substantial parasitic loss if the rotor were spinning in ambient atmospheric pressure air.

**Motor-Generator**

A single electrical machine (commonly a permanent magnet synchronous machine, given the high efficiency and power density such machines can achieve) operating as a motor during charging (accelerating the rotor) and as a generator during discharging (decelerating the rotor while extracting electrical output), analogous in functional role to the reversible pump-turbine's dual-mode operation in pumped-hydro storage.

**Containment Structure**

A robust containment housing designed to safely contain rotor fragments in the unlikely event of a catastrophic rotor failure (burst) at high rotational speed, an important safety engineering consideration given the very substantial kinetic energy stored in a high-speed composite rotor.

### Performance Characteristics

**High Power Density, Fast Response**

Flywheels can charge and discharge at very high power relative to their energy capacity, with response times to power commands on the order of milliseconds, comparable to or faster than battery storage and substantially faster than pumped-hydro or CAES, making flywheels particularly well-suited to applications requiring rapid, precise, and frequent power adjustment.

**Very High Cycle Life**

Because flywheel energy storage relies on a purely mechanical rotational process rather than electrochemical reactions, flywheels can typically sustain a very large number of full-depth charge/discharge cycles (often cited in the range of hundreds of thousands to over a million cycles) with minimal capacity degradation over the system's operational life, in sharp contrast to the cycle-life-limited degradation characteristic of electrochemical battery storage.

**Standby Losses (Self-Discharge)**

A significant limitation relative to most other storage technologies: even with magnetic bearings and vacuum enclosure, flywheels experience continuous, meaningful energy loss from residual friction, windage, and bearing/control system parasitic power draw while spinning in a charged (standby) state, resulting in comparatively rapid self-discharge (commonly losing a significant fraction of stored energy over a period of hours if left unused) relative to the very low self-discharge rates characteristic of pumped-hydro, CAES, or even most battery chemistries over comparable timeframes. This characteristic strongly shapes flywheel applications toward short-duration, frequently-cycled use cases rather than long-duration or infrequent-use bulk energy storage.

**Low Energy Density Relative to Power Density**

Flywheels are generally characterized by comparatively low energy-to-power ratio (short discharge duration at rated power, typically seconds to minutes for most grid-scale flywheel installations) relative to batteries or pumped-hydro, reflecting the fundamental design trade-off in flywheel systems, which excel at power-intensive, short-duration applications rather than bulk energy storage over hours.

### Comparative Summary

| Characteristic | Flywheel | Lithium-Ion Battery | Pumped Hydro |
| --- | --- | --- | --- |
| Typical discharge duration | Seconds to minutes | 1–4+ hours | Hours to days |
| Response time | Milliseconds | Milliseconds to seconds | Minutes |
| Cycle life | Very high (100,000+ cycles) | Thousands of cycles | Effectively unlimited (mechanical) |
| Round-trip efficiency | ~85–95% (excluding standby losses) | ~85–95% | ~70–85% |
| Standby/self-discharge losses | High relative to duration | Low | Very low |
| Energy density | Low | Moderate-high | High (site-dependent) |
| Best-suited application | Fast frequency regulation, power quality | Arbitrage, capacity, frequency regulation | Bulk long-duration storage |

### Key Applications

**Frequency Regulation**

The dominant grid-scale application for flywheel storage, exploiting the technology's very fast response time and, critically, its ability to sustain extremely high cycling rates (many full charge/discharge cycles per day, effectively continuous regulation duty) without the cycle-life-driven degradation concern that would affect battery storage subjected to comparably intensive cycling.

**Uninterruptible Power Supply (UPS) and Power Quality**

Flywheels are used in data center and critical facility UPS applications to bridge short-duration power interruptions (seconds, until backup generators start and stabilize, or until the interruption resolves), leveraging flywheels' fast response and high power capability for this brief but critical bridging role.

**Rail and Transit Regenerative Braking Capture**

Trackside or vehicle-mounted flywheel systems in rail transit applications to capture regenerative braking energy from decelerating trains and return it during subsequent acceleration, exploiting flywheels' fast response and high cycle life to handle the frequent, high-power charge/discharge cycles characteristic of transit braking/acceleration patterns.

**Grid Inertia Emulation**

In grids with declining synchronous generator inertia (due to increasing inverter-based renewable generation displacing conventional synchronous generation), flywheels have been explored as a source of fast-responding synthetic inertia, helping arrest grid frequency deviations in the critical first seconds following a disturbance, a role that leverages the technology's inherent rotational kinetic energy and fast response characteristics.

### Worked Example

**Given:** A composite flywheel rotor has a moment of inertia $I = 8\ \text{kg·m}^2$, operating between a maximum speed of 40,000 RPM and a minimum usable speed of 20,000 RPM (below which the power electronics can no longer efficiently extract useful power).

**Convert speeds to angular velocity (rad/s):**

$$\omega_{max} = 40{,}000 \times \frac{2\pi}{60} \approx 4{,}189\ \text{rad/s}$$



$$\omega_{min} = 20{,}000 \times \frac{2\pi}{60} \approx 2{,}094\ \text{rad/s}$$

**Energy at maximum speed:**

$$E_{max} = \frac{1}{2} \times 8 \times (4{,}189)^2 = \frac{1}{2} \times 8 \times 1.755\times10^7 \approx 7.02\times10^7\ \text{J} \approx 19.5\ \text{kWh}$$

**Energy at minimum usable speed:**

$$E_{min} = \frac{1}{2} \times 8 \times (2{,}094)^2 = \frac{1}{2} \times 8 \times 4.385\times10^6 \approx 1.754\times10^7\ \text{J} \approx 4.87\ \text{kWh}$$

**Usable energy capacity (between max and min operating speed):**

$$E_{usable} = 19.5 - 4.87 \approx 14.6\ \text{kWh}$$

This illustrates a key practical design consideration in flywheel sizing: because power electronics generally cannot efficiently extract power all the way down to zero rotational speed, and because stored energy scales with the square of speed, a substantial fraction of the theoretical total stored energy at maximum speed (here, roughly 25%, corresponding to the energy remaining at the minimum usable speed) is effectively unusable, meaning usable energy capacity must be calculated as the difference between maximum and minimum operating speed states rather than simply the total kinetic energy at maximum speed.

### Flywheel System Schematic (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 380" font-family="sans-serif">
<text x="320" y="24" font-size="16" text-anchor="middle" fill="#222">Flywheel Energy Storage Unit (svg_diagram)</text>
<rect x="180" y="60" width="280" height="260" fill="none" stroke="#333" stroke-width="2" stroke-dasharray="5,3" />
<text x="320" y="80" font-size="10" text-anchor="middle">Vacuum Enclosure</text>
<ellipse cx="320" cy="190" rx="110" ry="30" fill="#c07840" stroke="#333" stroke-width="2" />
<text x="320" y="196" font-size="11" text-anchor="middle" fill="#fff">Composite Rotor</text>
<rect x="300" y="130" width="40" height="30" fill="#888" stroke="#333" />
<text x="320" y="150" font-size="8" text-anchor="middle" fill="#fff">Upper</text>
<rect x="300" y="230" width="40" height="30" fill="#888" stroke="#333" />
<text x="320" y="250" font-size="8" text-anchor="middle" fill="#fff">Lower</text>
<text x="240" y="145" font-size="8" text-anchor="middle">Magnetic Bearing</text>
<text x="240" y="260" font-size="8" text-anchor="middle">Magnetic Bearing</text>
<rect x="480" y="160" width="90" height="60" fill="#e0c68c" stroke="#333" stroke-width="2" />
<text x="525" y="185" font-size="9" text-anchor="middle">Motor/</text>
<text x="525" y="197" font-size="9" text-anchor="middle">Generator</text>
<line x1="460" y1="190" x2="480" y2="190" stroke="#333" stroke-width="3" />
<line x1="570" y1="190" x2="620" y2="190" stroke="#333" stroke-width="2" />
<text x="595" y="180" font-size="8" text-anchor="middle">Grid</text>
</svg>

**Related Topics**

- Composite rotor burst containment design
- Magnetic bearing control systems
- Flywheel arrays for frequency regulation market participation
- Synthetic inertia provision from fast-responding storage
- Regenerative braking energy capture in rail transit
- Comparative round-trip efficiency accounting including standby losses
- High-speed permanent magnet motor-generator design
- UPS system design integrating flywheel bridging power