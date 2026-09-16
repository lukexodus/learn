## Centrifugal and Positive-Displacement Pumps


### Overview

Pumps add energy to a liquid to move it, raise its pressure, or overcome elevation and friction losses in a system. The two fundamental categories are **centrifugal (dynamic/kinetic) pumps**, which impart energy through the action of a rotating impeller accelerating the fluid, and **positive-displacement (PD) pumps**, which move fluid by trapping a fixed volume and mechanically forcing it through the system. These two families have fundamentally different performance characteristics, governing how each responds to changes in system resistance.

### Fundamental Distinction: Dynamic vs. Positive-Displacement Action

**Key Points**

- A **centrifugal pump** produces a pressure (head) that varies with flow rate according to its characteristic curve, and flow rate is determined by where this curve intersects the system resistance curve — flow is not fixed and adjusts with downstream conditions.
- A **positive-displacement pump** produces a nearly constant flow rate per revolution (or cycle) regardless of discharge pressure (up to mechanical/power limits), with discharge pressure instead rising to whatever value the system resistance demands, since the pump mechanically displaces a fixed volume per cycle.
- This distinction has a critical practical consequence: a PD pump running against a closed or blocked discharge will continue trying to displace fluid, causing pressure to rise essentially without limit until something fails (pipe rupture, seal blowout, or mechanical damage) — PD pumps therefore always require a relief valve on the discharge side, whereas a centrifugal pump running against a closed valve simply reaches a maximum ("shutoff") head and continues operating (though not indefinitely safely, due to internal recirculation heating).

### Centrifugal Pumps

#### Working Principle

Fluid enters axially near the center (eye) of a rotating **impeller**, is accelerated radially outward by centrifugal force and blade action, and exits at high velocity into a stationary **volute** or **diffuser**, where kinetic energy converts to static pressure as the flow decelerates in the expanding passage — functioning by the same fundamental principle as a centrifugal compressor, with the key distinction that the working fluid (liquid) is effectively incompressible, so specific volume/density remains essentially constant through the machine.

**Key Points**

- Because liquid is treated as incompressible, centrifugal pump performance is conventionally expressed in terms of **head** (energy per unit weight, in meters or feet of fluid column) rather than pressure ratio, since head is independent of fluid density and allows direct comparison of pump performance across different fluids.
- The relationship between head $H$ and pressure rise $\Delta P$ is:

$$\Delta P = \rho g H$$

#### Pump Performance Curve (Head-Capacity Curve)

A centrifugal pump's characteristic curve plots developed head against flow rate (capacity) at a given speed, typically showing head decreasing as flow increases (a drooping curve), intersecting with efficiency and power curves.

**Key Points**

- **Best Efficiency Point (BEP)**: The flow rate at which the pump operates at maximum efficiency; operating significantly away from BEP (either much higher or lower flow) increases internal losses, vibration, and mechanical wear, and is generally avoided in continuous-duty applications.
- **System curve**: A plot of the head required by the piping system (static lift plus friction losses, the latter increasing roughly with the square of flow rate) versus flow rate; the pump's actual operating point is where the pump curve and system curve intersect.
- **Affinity laws**: For a given pump, changes in impeller speed $N$ (or diameter $D$) relate to flow, head, and power as:

$$\frac{Q_2}{Q_1} = \frac{N_2}{N_1}, \quad \frac{H_2}{H_1} = \left(\frac{N_2}{N_1}\right)^2, \quad \frac{P_2}{P_1} = \left(\frac{N_2}{N_1}\right)^3$$

These relationships allow prediction of performance changes from speed adjustment (e.g., via VFD control) without needing a full new set of test data, and are foundational to variable-speed pump control strategies.

```mermaid
flowchart TD
    A[Centrifugal Pump and System Curves] (svg_diagram)
    A --> B[Pump Curve - Head decreases as Flow increases]
    A --> C[System Curve - Head increases with Flow squared, plus static lift]
    B --> D[Operating Point - Intersection of Pump and System Curves]
    C --> D
```

#### Cavitation and NPSH

**Key Points**

- Cavitation occurs when local pressure at the impeller eye drops below the fluid's vapor pressure, forming vapor bubbles that collapse violently as they move into higher-pressure regions downstream, causing noise, vibration, and erosive damage to impeller and casing surfaces.
- **Net Positive Suction Head (NPSH)** governs cavitation risk, following the same principle described for boiler feed pumps: $NPSH_{available}$ (a function of suction piping design, fluid vapor pressure, and elevation/pressure at the suction source) must exceed $NPSH_{required}$ (a pump-specific characteristic) with adequate margin across the operating range.
- Cavitation risk is especially significant when pumping fluids near their boiling point (e.g., boiler feedwater, hot condensate, or volatile process liquids), or when suction piping has excessive friction losses or elevation lift.

#### Centrifugal Pump Types and Classifications

- **By casing design**: Volute (single spiral casing, most common) vs. diffuser (fixed guide vanes surrounding the impeller before the casing, common in multistage designs for more uniform radial loading).
- **By staging**: Single-stage (one impeller, moderate head) vs. multistage (multiple impellers in series, used for high-head applications such as boiler feed service).
- **By impeller type**: Radial-flow (pure centrifugal action, high head/low flow), mixed-flow (combination of radial and axial flow components, moderate head/moderate-high flow), and axial-flow (propeller-type, low head/very high flow) — these represent a continuum of impeller geometries suited to different specific-speed ranges.
- **By suction configuration**: End-suction (single inlet, most common for general service), double-suction (fluid enters from both sides of the impeller, balancing axial thrust and allowing higher flow capacity for a given impeller diameter).
- **By mounting**: Horizontal, vertical (including vertical turbine pumps for deep well or wet-pit applications), and submersible designs.

### Positive-Displacement Pumps

#### Working Principle

PD pumps trap a fixed volume of fluid in a chamber and mechanically force it from the suction side to the discharge side through the physical motion of a piston, gear, screw, vane, diaphragm, or lobe, delivering a pulsed or near-continuous flow that is largely independent of discharge pressure (within the mechanical capability of the driver and pump structure).

**Key Points**

- Because flow is set by mechanical displacement per cycle (times cycle frequency), PD pumps are well suited to applications requiring precise, controllable, pressure-independent flow rates, such as metering/dosing applications.
- PD pumps generally handle higher-viscosity fluids more effectively than centrifugal pumps, since centrifugal pump performance degrades significantly with increasing viscosity (higher internal friction losses reduce head and efficiency), while PD pumps are comparatively less sensitive to viscosity (and in some designs, higher viscosity even improves volumetric efficiency by reducing internal slip/leakage). [Inference — well-established general principle in pump engineering literature; exact viscosity sensitivity varies by specific pump design.]

#### Reciprocating PD Pumps

- **Piston/plunger pumps**: A piston or plunger moves within a cylinder, drawing fluid in through a suction check valve on the intake stroke and forcing it out through a discharge check valve on the power stroke; capable of very high pressures, commonly used in high-pressure applications (e.g., hydraulic power units, high-pressure cleaning, chemical injection/dosing).
- **Diaphragm pumps**: A flexible diaphragm, driven mechanically or hydraulically, flexes back and forth to draw in and expel fluid, with the diaphragm isolating the driving mechanism from the pumped fluid — advantageous for handling corrosive, abrasive, or hazardous fluids where leak-free containment is important.

**Key Points**

- Reciprocating pumps inherently produce a **pulsating flow** (flow varies cyclically as the piston/diaphragm moves through its stroke), which can cause pressure pulsations and vibration in piping systems; multiple cylinders operated out of phase (duplex, triplex, or higher multiplex arrangements) and/or pulsation dampeners are used to smooth flow and reduce pressure fluctuation.

#### Rotary PD Pumps

- **Gear pumps**: Two (or more) meshing gears rotate within a close-clearance housing; fluid is trapped in the spaces between gear teeth and the housing wall and carried from suction to discharge side as the gears rotate. Simple, robust, and common for hydraulic fluid power and lubricating oil service.
- **Screw pumps**: One or more helical screws rotate within a close-clearance housing (or intermeshing with each other, as in twin-screw designs), continuously advancing fluid along the axis in a smooth, low-pulsation flow. Well suited to high-viscosity fluids and applications requiring gentle, low-shear handling.
- **Lobe pumps**: Similar to gear pumps but with fewer, larger lobes (typically 2–3 per rotor) that do not contact each other directly (synchronized by external timing gears), reducing shear and contamination risk — common in food, pharmaceutical, and hygienic process applications.
- **Vane pumps**: Spring-loaded or hinged vanes mounted in a rotor slide in and out as the rotor turns eccentrically within the casing, trapping and displacing fluid in the resulting variable-volume pockets; used in moderate-pressure hydraulic and fuel-handling applications.

```mermaid
flowchart LR
    A[PD Pump Family] (svg_diagram)
    A --> B[Reciprocating]
    A --> C[Rotary]
    B --> D[Piston / Plunger]
    B --> E[Diaphragm]
    C --> F[Gear]
    C --> G[Screw]
    C --> H[Lobe]
    C --> I[Vane]
```

#### PD Pump Protection: Relief Valves

**Key Points**

- Because PD pumps generate pressure without inherent self-limiting behavior (unlike a centrifugal pump's shutoff head), a **relief (safety) valve** on the discharge line is a mandatory protective device, set to open and recirculate (or vent) flow if discharge pressure exceeds a safe threshold, preventing pipe rupture, seal failure, or driver overload/stall.
- This is a fundamental design difference from centrifugal pump protection philosophy, where a closed discharge valve is undesirable (causing internal recirculation heating and potential vaporization) but not inherently destructive in the same immediate, high-pressure-rupture sense as a blocked PD pump discharge.

### Comparison: Centrifugal vs. Positive-Displacement Pumps

| Characteristic | Centrifugal | Positive-Displacement |
| --- | --- | --- |
| Flow vs. pressure relationship | Flow varies with discharge pressure/system resistance | Flow largely independent of discharge pressure |
| Behavior at blocked discharge | Reaches shutoff head, flow approaches zero | Pressure rises until failure — relief valve mandatory |
| Viscosity sensitivity | High — performance degrades significantly with viscosity | Low — often tolerates or benefits from higher viscosity |
| Flow smoothness | Continuous, smooth | Pulsating (reciprocating) or smooth (rotary/screw) |
| Typical applications | General water/process transfer, boiler feed, circulating water | Metering/dosing, hydraulic fluid power, viscous fluid transfer, high-pressure injection |
| Flow control method | Throttling valve, speed variation (VFD) | Stroke length/speed variation (flow directly proportional) |
| Efficiency at low flow | Poor (operating away from BEP) | Generally maintains efficiency across flow range |

### Selection Considerations

**Key Points**

- **Fluid viscosity**: High-viscosity fluids favor PD pumps (especially screw or gear types); low-viscosity fluids (like water) are well served by centrifugal pumps.
- **Flow precision/metering needs**: Applications requiring precise, controllable flow independent of pressure fluctuations (chemical dosing, fuel injection) favor PD pumps.
- **Flow rate and head requirements**: Centrifugal pumps dominate high-flow, moderate-head applications (cooling water, general process transfer); PD pumps are often preferred for high-pressure, lower-flow applications or where flow must remain constant regardless of pressure variation.
- **Solids/abrasives handling**: Certain PD types (diaphragm, some rotary designs) handle abrasive or solids-laden fluids well; centrifugal pumps can also be adapted (e.g., slurry pump designs with hardened components) depending on application.
- **NPSH sensitivity**: Both pump families are subject to cavitation risk, though the underlying mechanism and design mitigation approaches (impeller/suction design for centrifugal vs. valve/chamber design for PD) differ.

**Example**

A power plant might use large centrifugal pumps for circulating water service (high flow, moderate head, low viscosity — cooling water) and boiler feed service (high head, moderate flow), while using small positive-displacement metering pumps (diaphragm or piston type) for precise chemical dosing (e.g., oxygen scavenger, pH-control amines, or biocide injection into the feedwater or cooling water systems), since these dosing applications require accurate, pressure-independent flow control of small volumes rather than the high flow capacity centrifugal pumps provide.

**Next Steps**

- Pump Affinity Laws and Variable-Speed Pump Control
- Cavitation Damage Mechanisms and NPSH Margin Design
- Multistage Centrifugal Pump Design (Boiler Feed Service)
- PD Pump Metering and Dosing System Design
- Pump Selection via Specific Speed and Performance Charts
- Slurry and Abrasive-Service Pump Design Considerations