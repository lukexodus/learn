## Cavitation and Its Prevention


### Overview

Cavitation is the formation and subsequent violent collapse of vapor bubbles (cavities) within a liquid, occurring when local static pressure drops to or below the liquid's vapor pressure at the prevailing temperature. It is a critical failure mode and performance-limiting phenomenon across nearly all liquid-handling turbomachinery — pumps, hydraulic turbines, and propellers — causing efficiency loss, noise, vibration, and severe erosive material damage. This item consolidates and extends the cavitation concepts introduced separately for boiler feed pumps, centrifugal pumps, and hydraulic turbines into a unified treatment of the phenomenon and its prevention.

### Physical Mechanism

#### Bubble Formation

When local static pressure within a flowing liquid drops below the liquid's vapor pressure at the local temperature, the liquid locally vaporizes, forming vapor-filled cavities (bubbles). This differs fundamentally from boiling in a heated vessel: cavitation is pressure-driven (isothermal, essentially) rather than temperature-driven, occurring due to local flow acceleration (per Bernoulli's principle, velocity increases correspond to pressure decreases) in regions such as impeller eyes, blade suction surfaces, or valve throats.

$$P_{local} \leq P_{vapor}(T)$$

#### Bubble Collapse (Implosion)

As the vapor bubble is carried by the flow into a region of higher pressure (downstream of the low-pressure zone, such as past the point of minimum pressure on a blade or past an impeller eye into the higher-pressure diffuser region), the surrounding liquid pressure exceeds the vapor pressure inside the bubble, and the bubble collapses (implodes) rapidly and violently.

**Key Points**

- Bubble collapse is asymmetric when it occurs near a solid surface: the liquid on the side away from the surface accelerates inward faster than on the surface side, forming a high-velocity **micro-jet** of liquid that impacts the solid surface directly, along with an accompanying shock wave from the collapse itself.
- These micro-jet impacts and shock waves generate extremely high localized, transient pressures (reported in cavitation literature to be on the order of hundreds to thousands of MPa in some studies, though exact magnitudes depend on bubble size, collapse conditions, and measurement method) acting on a tiny area for a very short duration — repeated over millions of cycles, this causes characteristic pitting erosion damage to nearby solid surfaces (impeller blades, runner surfaces, valve seats). [Unverified — specific peak pressure magnitudes vary considerably across cavitation research literature and depend heavily on specific conditions studied.]
- The collapse process also generates broadband noise (the characteristic "gravel rattling" or crackling sound commonly associated with cavitating pumps) and can excite mechanical vibration in the affected component and connected piping/structure.

### Effects of Cavitation

**Key Points**

- **Erosion damage**: Progressive pitting and material removal from impeller vanes, runner blades, valve trim, and casing surfaces, eventually leading to structural failure if unaddressed; damage severity depends on cavitation intensity, duration, and material resistance.
- **Performance degradation**: Vapor bubbles occupying flow passages effectively reduce the flow area available for liquid, disrupting normal flow patterns and reducing head, flow capacity, and efficiency — in severe cases, this is termed "head breakdown," where developed head drops sharply.
- **Noise and vibration**: Often the first noticeable symptom of incipient cavitation, useful as a diagnostic indicator before significant damage occurs.
- **Reduced component life**: Beyond direct erosion, cavitation-induced vibration accelerates bearing wear, seal degradation, and fatigue in adjacent mechanical components.

### Net Positive Suction Head (NPSH): The Central Prevention Parameter

NPSH quantifies the margin between actual suction-side pressure conditions and the fluid's vapor pressure, serving as the primary engineering parameter for cavitation prevention across pump and turbine applications.

$$NPSH_{available} = \frac{P_{suction,abs}}{\rho g} + \frac{v_{suction}^2}{2g} - \frac{P_{vapor}}{\rho g}$$

For a pump drawing from an open or pressurized source with elevation and friction losses accounted for:

$$NPSH_{A} = \frac{P_{atm}}{\rho g} \pm z_{s} - h_{f,suction} - \frac{P_{vapor}}{\rho g}$$

where $z_s$ is the static elevation of the liquid source relative to the pump suction (positive if the source is above pump suction/flooded suction, negative if the pump must lift liquid), and $h_{f,suction}$ is the friction head loss in the suction piping.

**Key Points**

- $NPSH_{available}$ is a property of the **system** (suction piping design, source elevation/pressure, fluid properties, temperature) — it describes what the installation provides.
- $NPSH_{required}$ is a property of the **pump/turbine itself** (determined by manufacturer testing, dependent on impeller/runner design, speed, and flow rate) — it describes what the machine needs at its suction/low-pressure internal points to avoid cavitation.
- The governing prevention criterion is always:

$$NPSH_{available} > NPSH_{required} + \text{margin}$$

A margin (commonly cited guidance suggests at least 0.5–1 m or a percentage-based margin depending on application and criticality) above the bare minimum is standard practice to accommodate uncertainties in required NPSH testing, system aging, and operating point variation. [Inference — general safety margin practice cited across pump engineering literature; exact required margin varies by standard (e.g., Hydraulic Institute guidelines) and application criticality.]

- $NPSH_{required}$ increases with flow rate for a given pump (since higher flow means higher velocity, and thus lower local pressure, at the impeller eye per Bernoulli's principle) — this is why cavitation risk is often greatest at high flow rates significantly above the best efficiency point, in addition to certain low-flow recirculation-driven cavitation risks at very low flow.

### Factors That Reduce NPSH Available (Increasing Cavitation Risk)

**Key Points**

- **High fluid temperature**: Vapor pressure rises sharply with temperature, directly reducing available NPSH margin — this is why hot liquid handling (boiler feedwater near saturation, hot condensate, hot process fluids) is particularly cavitation-prone and requires careful suction system design (as discussed for deaerator elevation and boiler feed pump NPSH).
- **Elevated suction lift**: Drawing liquid from below pump suction level (a "suction lift" condition) directly subtracts from available NPSH; flooded suction (source above pump centerline) is preferred wherever practical for cavitation-sensitive services.
- **Excessive suction piping friction losses**: Long suction runs, small pipe diameter, excessive fittings/valves, or clogged strainers all increase friction losses, directly reducing NPSH available at the pump suction flange.
- **Low atmospheric/system pressure**: For open systems, higher altitude installations (lower atmospheric pressure) reduce available NPSH; for closed systems, insufficient system/vessel pressure has the same effect.
- **Entrained air or dissolved gas release**: Air or gas coming out of solution in low-pressure regions can compound cavitation-like symptoms (sometimes termed "gaseous cavitation" or "aeration," distinct from true vapor cavitation but with similar practical performance/noise effects).

### Types of Cavitation Encountered in Turbomachinery

**Key Points**

- **Suction (inlet) cavitation**: Classic NPSH-driven cavitation at the impeller eye/inlet, caused by insufficient NPSH margin as described above; the most common and directly addressed form.
- **Discharge (recirculation) cavitation**: Occurs at low flow rates (well below BEP) due to internal flow recirculation within the pump, creating localized low-pressure vortex regions distinct from simple inlet starvation; can occur even with adequate bulk NPSH margin, since the mechanism is internal flow pattern breakdown rather than overall suction pressure deficiency.
- **Vane passing/blade cavitation**: Localized cavitation on the low-pressure (suction) surface of impeller or runner blades due to local pressure minima from blade curvature and loading, distinct from bulk inlet conditions.
- **Internal recirculation cavitation**: Related to discharge recirculation, occurring at both suction and discharge sides of an impeller during off-BEP low-flow operation.

### Prevention and Mitigation Strategies

#### Design-Stage Prevention

- **Adequate NPSH margin in system design**: Sizing suction piping generously (larger diameter, minimal fittings, short runs), positioning pump/turbine at appropriate elevation relative to the liquid source, and accounting for worst-case (highest temperature, lowest source level) operating conditions.
- **Booster/inducer stages**: A low-head axial "inducer" stage placed immediately upstream of the main impeller can raise local pressure sufficiently to suppress cavitation at the main impeller eye, commonly used in high-speed pumps (e.g., some boiler feed pumps and rocket propellant pumps) where NPSH available is inherently limited relative to the pump's demanding operating requirements. [Inference — well-established design technique in high-energy-density pump applications.]
- **Cavitation-resistant materials**: Selecting materials with higher resistance to erosive pitting (certain stainless steel alloys, cobalt-based alloys, or specialized coatings) for components in high-risk locations, extending service life even where some cavitation cannot be entirely eliminated.
- **Runner/impeller setting elevation** (hydraulic turbines): As described via the Thoma cavitation coefficient, setting the turbine runner at an appropriate height relative to tailwater level to maintain adequate margin against local pressure minima in the runner and draft tube.

#### Operational Prevention

- **Operating near best efficiency point (BEP)**: Minimizing both inlet cavitation risk (avoiding excessive flow rates that increase NPSH required) and recirculation cavitation risk (avoiding excessively low flow rates), since NPSH required and internal flow pattern stability are both most favorable near BEP.
- **Suction strainer/piping maintenance**: Preventing progressive fouling or blockage of suction strainers and piping that would gradually increase friction losses and erode NPSH margin over time.
- **Avoiding excessive suction lift or elevation changes**: Operational procedures that maintain adequate liquid level in supply tanks/vessels, avoiding conditions that temporarily reduce effective NPSH available (e.g., low tank level alarms tied to pump protection logic).
- **Temperature management**: Where process conditions allow, avoiding unnecessarily high fluid temperatures at pump suction reduces vapor pressure and improves NPSH margin.

```mermaid
flowchart TD
    A[Cavitation Risk Factors] (svg_diagram)
    A --> B[High Fluid Temperature]
    A --> C[Suction Lift / Low Source Elevation]
    A --> D[Suction Piping Friction Losses]
    A --> E[Operating Away from BEP]
    B --> F[Reduced NPSH Available]
    C --> F
    D --> F
    E --> G[Increased NPSH Required or Recirculation]
    F --> H[NPSH Available less than NPSH Required]
    G --> H
    H --> I[Cavitation Onset]
```

### Detection and Monitoring

**Key Points**

- **Acoustic/vibration monitoring**: Cavitation produces characteristic broadband high-frequency noise and vibration signatures that can be detected via accelerometers or acoustic sensors, often before visible damage occurs — used in condition-monitoring programs for early cavitation detection.
- **Performance monitoring**: Tracking developed head, flow, and efficiency against expected pump/turbine curves; a sudden or progressive drop in head at constant flow (or vice versa) can indicate cavitation-related performance degradation, particularly useful for detecting the "head breakdown" condition associated with severe cavitation.
- **Visual/borescope inspection**: During scheduled maintenance, inspecting impeller/runner surfaces for characteristic pitting patterns confirms cavitation has occurred and helps assess severity/progression trends between inspection intervals.
- **NPSH margin verification**: Periodic recalculation of NPSH available (accounting for any changes in suction piping condition, fluid temperature, or source level) compared against the pump's tested $NPSH_R$ curve, ensuring adequate margin is maintained as operating conditions or equipment condition change over time.

**Example**

A boiler feed pump operating with feedwater near saturation temperature experiences intermittent crackling noise and a gradual decline in developed head at its normal operating flow rate. Investigation reveals that a partially fouled suction strainer has increased suction-side friction losses, reducing NPSH available below the margin required at that flow rate. Cleaning the strainer restores adequate NPSH margin, and the cavitation symptoms (noise, head deficit) resolve — illustrating how a seemingly unrelated maintenance issue (strainer fouling) can directly cause cavitation through its effect on NPSH available.

**Next Steps**

- NPSH Testing Standards and Manufacturer Curve Interpretation
- Inducer Design for High-Speed Pump Applications
- Cavitation-Resistant Materials and Coatings
- Vibration-Based Condition Monitoring for Rotating Equipment
- Thoma Cavitation Coefficient and Hydraulic Turbine Setting Elevation
- Water Hammer and Transient Pressure Effects on Cavitation Risk