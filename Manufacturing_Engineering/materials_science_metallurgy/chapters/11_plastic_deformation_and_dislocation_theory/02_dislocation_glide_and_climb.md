## Dislocation Glide and Climb

### Definition and Fundamental Distinction

Dislocations move through a crystal lattice by two fundamentally distinct mechanisms: **glide** (also called slip) and **climb**. These mechanisms differ in whether atomic diffusion is required, in the crystallographic constraints on motion, and in the temperature regimes where each dominates.

**Glide** is the conservative motion of a dislocation within its slip plane (the plane containing both the dislocation line and its Burgers vector), requiring no net mass transport — atoms shift by small, cooperative displacements without diffusion. **Climb** is the non-conservative motion of an edge dislocation perpendicular to its slip plane, achieved by the absorption or emission of vacancies (or, less commonly, self-interstitials) at the dislocation core, and is therefore inherently diffusion-controlled and consequently thermally activated.

### Dislocation Glide

**Mechanism**

During glide, an edge dislocation moves through the lattice via sequential, localized bond breaking and reforming along the slip plane — conceptually analogous to how a ruck in a carpet can be propagated across the carpet with much less force than sliding the entire carpet at once. This is the essential reason dislocation-mediated slip requires far lower stress than the theoretical shear strength that would be needed to shear an entire perfect crystal plane simultaneously.

**[Key Points]**

- Glide is a conservative process: the dislocation moves without any net addition or removal of atoms/vacancies, meaning it can occur athermally (i.e., does not require thermal activation for the fundamental mechanism itself, although obstacle bypass along the glide path can be thermally assisted).
- Glide is restricted to the specific slip plane containing both the dislocation line and its Burgers vector — an edge dislocation can only glide within this single plane, since the geometric definition of an edge dislocation ties its Burgers vector direction (perpendicular to the dislocation line, within the slip plane) to this constraint.
- Screw dislocations, having a Burgers vector parallel to the dislocation line, do not have a uniquely defined single slip plane geometrically; they can, in principle, glide on any plane containing the dislocation line, enabling **cross-slip** (see below).
- Glide is the dominant deformation mechanism at low-to-moderate homologous temperature and is the mechanism directly responsible for macroscopically observed slip bands and the Schmid's Law/CRSS framework of crystal plasticity.

**Cross-slip**

Because a screw dislocation segment is not confined to a single slip plane, it can transfer from one slip plane to a crystallographically equivalent intersecting plane that shares the same slip direction — this is **cross-slip**. Cross-slip allows a screw dislocation to circumvent localized obstacles (precipitates, forest dislocations) that might otherwise pin it on its original plane, and is an important mechanism in work-hardening stage transitions and in the recovery/dynamic recovery processes that influence flow stress at moderate-to-elevated temperature. Cross-slip is generally easier in metals with high stacking fault energy (since a low stacking fault energy tends to widen the dissociated dislocation into partial dislocations bounding a stacking fault ribbon, which must first constrict back together before cross-slip can occur) — this is a key reason metals like aluminum (high SFE) cross-slip readily while metals like copper and austenitic stainless steels (lower SFE) show more restricted cross-slip and correspondingly different work-hardening behavior.

### Dislocation Climb

**Mechanism**

Climb involves the movement of an edge dislocation out of its original glide plane, in a direction perpendicular to the glide plane (i.e., parallel to the extra half-plane of atoms that geometrically defines an edge dislocation). This is accomplished by:

- **Positive climb**: vacancies diffuse to the dislocation core and are absorbed, effectively removing atoms from the edge of the extra half-plane, causing the dislocation to move "up" (shortening the extra half-plane).
- **Negative climb**: atoms (equivalently, vacancies are emitted from the dislocation core) are added to the edge of the extra half-plane, causing the dislocation to move "down" (lengthening the extra half-plane).

Because climb requires net vacancy transport to or from the dislocation core via bulk lattice diffusion, its rate is fundamentally governed by the vacancy diffusion coefficient, which follows Arrhenius-type thermal activation:

$$D_v = D_0 \exp\left(-\frac{Q_v}{RT}\right)$$

where $Q_v$ is the activation energy for vacancy diffusion. This direct dependence on a thermally activated diffusion coefficient is why climb is negligible at low temperature and becomes progressively more significant as temperature increases, typically becoming metallurgically significant above approximately $0.4$–$0.5\,T_m$ (homologous temperature).

**[Key Points]**

- Climb is a non-conservative process, since it requires net mass transport (vacancy flux) to or from the dislocation.
- Climb allows an edge dislocation to bypass obstacles that lie outside its original glide plane — a capability glide alone cannot provide, since glide is confined to a single plane.
- Climb rate is directly coupled to local vacancy concentration and its gradient, meaning climb is accelerated by conditions that increase vacancy concentration above equilibrium (e.g., quenching-in excess vacancies, irradiation-induced point defects) or by applied stress states that create local vacancy supersaturation/undersaturation gradients along a dislocation line.

### Glide vs. Climb: Comparative Summary

| Characteristic | Glide | Climb |
| --- | --- | --- |
| Motion direction | Within the slip plane | Perpendicular to the slip plane |
| Mass transport required | None (conservative) | Yes — vacancy diffusion (non-conservative) |
| Temperature dependence | Weak (fundamentally athermal, though obstacle-bypass can be thermally assisted) | Strong (Arrhenius, diffusion-controlled) |
| Dominant regime | Low-to-moderate T (cold/warm working) | Elevated T (typically > 0.4–0.5 T_m) |
| Dislocation type | Edge, screw, or mixed | Edge only (screw dislocations cannot climb, as they have no extra half-plane) |
| Governs | Room-temperature plastic deformation, Schmid's Law/CRSS framework | High-temperature creep, recovery, dislocation network rearrangement |

### Glide and Climb Mechanism Diagram

===MERMAID_DIAGRAM===

flowchart TD

A["Edge dislocation"] --> B{"Motion mode"}

B --> C["Glide<br/>(within slip plane)"]

B --> D["Climb<br/>(perpendicular to slip plane)"]

C --> E["Conservative:<br/>no mass transport"]

C --> F["Athermal fundamental mechanism<br/>(dominant at low/moderate T)"]

D --> G["Non-conservative:<br/>requires vacancy diffusion"]

G --> H["Positive climb:<br/>vacancy absorption"]

G --> I["Negative climb:<br/>vacancy emission"]

D --> J["Thermally activated (Arrhenius)<br/>(dominant at high T, creep)"]

E["Screw dislocation"] -.-> K["Can cross-slip<br/>(no unique glide plane)"]

E -.-> L["Cannot climb<br/>(no extra half-plane)"]



```
### Climb Geometry Illustration (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 400">
  <text x="320" y="24" text-anchor="middle" font-size="16" font-family="sans-serif" font-weight="bold">Edge Dislocation Climb (svg_diagram)</text>
  <text x="160" y="55" text-anchor="middle" font-size="13" font-family="sans-serif" font-weight="bold">Positive climb</text>
  <text x="480" y="55" text-anchor="middle" font-size="13" font-family="sans-serif" font-weight="bold">Negative climb</text>
  <line x1="60" y1="340" x2="260" y2="340" stroke="black" stroke-width="1" />
  <line x1="60" y1="300" x2="260" y2="300" stroke="black" stroke-width="1" />
  <line x1="60" y1="220" x2="260" y2="220" stroke="black" stroke-width="1" />
  <line x1="60" y1="180" x2="260" y2="180" stroke="black" stroke-width="1" />
  <line x1="160" y1="180" x2="160" y2="260" stroke="#d62728" stroke-width="4" />
  <text x="170" y="270" font-size="11" font-family="sans-serif" fill="#d62728">extra half-plane</text>
  <text x="145" y="255" font-size="20" fill="#d62728">⊥</text>
  <line x1="160" y1="150" x2="160" y2="180" stroke="#2ca02c" stroke-width="2" marker-end="url(#arrow1)" />
  <text x="90" y="140" font-size="11" font-family="sans-serif" fill="#2ca02c">vacancies absorbed →</text>
  <text x="90" y="125" font-size="11" font-family="sans-serif" fill="#2ca02c">dislocation climbs up</text>
  <line x1="380" y1="340" x2="580" y2="340" stroke="black" stroke-width="1" />
  <line x1="380" y1="300" x2="580" y2="300" stroke="black" stroke-width="1" />
  <line x1="380" y1="220" x2="580" y2="220" stroke="black" stroke-width="1" />
  <line x1="380" y1="180" x2="580" y2="180" stroke="black" stroke-width="1" />
  <line x1="480" y1="220" x2="480" y2="320" stroke="#d62728" stroke-width="4" />
  <text x="490" y="330" font-size="11" font-family="sans-serif" fill="#d62728">extended half-plane</text>
  <line x1="480" y1="340" x2="480" y2="365" stroke="#1f77b4" stroke-width="2" marker-end="url(#arrow2)" />
  <text x="400" y="380" font-size="11" font-family="sans-serif" fill="#1f77b4">vacancies emitted →</text>
  <text x="400" y="395" font-size="11" font-family="sans-serif" fill="#1f77b4">dislocation climbs down</text>
  </svg>

### Worked Example: Estimating Vacancy Diffusivity's Role in Climb Rate

**[Example]** Compare the relative ease of dislocation climb in a nickel-based superalloy at two service temperatures, 650°C and 950°C, given a self-diffusion activation energy for Ni of approximately $Q_v \approx 280$ kJ/mol (a representative literature value for Ni self-diffusion, relevant to vacancy-mediated climb).

Using the Arrhenius relationship, the ratio of diffusion coefficients (and hence approximate relative climb rate) is:

$$\frac{D_{950°C}}{D_{650°C}} = \exp\left[-\frac{Q_v}{R}\left(\frac{1}{T_2}-\frac{1}{T_1}\right)\right]$$

Converting to Kelvin: $T_1 = 923\ \text{K}$ (650°C), $T_2 = 1223\ \text{K}$ (950°C).

$$\frac{1}{T_2}-\frac{1}{T_1} = \frac{1}{1223}-\frac{1}{923} = 8.176\times10^{-4} - 1.0834\times10^{-3} = -2.658\times10^{-4}\ \text{K}^{-1}$$

$$\frac{D_{950°C}}{D_{650°C}} = \exp\left[-\frac{280{,}000}{8.314}\times(-2.658\times10^{-4})\right] = \exp\left[33{,}677\times2.658\times10^{-4}\right] = \exp(8.95) \approx 7{,}700$$

This result indicates that vacancy diffusivity — and by extension, the characteristic rate of diffusion-controlled dislocation climb — increases by roughly **3–4 orders of magnitude** between 650°C and 950°C for this representative activation energy. This dramatic sensitivity to temperature is the central reason creep-related climb mechanisms become design-critical specifically in high-temperature service (turbine components, high-pressure steam piping) and are essentially negligible at typical room-temperature or moderate-temperature structural service conditions. [Inference: the specific numerical activation energy used is a representative literature value for nickel; actual climb-controlling diffusion in a specific superalloy depends on the relevant diffusing species and matrix/precipitate composition, which can shift the effective activation energy somewhat from the pure-metal self-diffusion value used here.]

### Role in High-Temperature Creep

**[Key Points]**
- **Climb-controlled (dislocation) creep**: at elevated temperature and moderate-to-high stress, creep rate is frequently limited by the rate at which climbing dislocations can bypass obstacles (precipitates, forest dislocations) that block glide alone — this regime is described by power-law creep relationships of the form $\dot{\varepsilon} \propto \sigma^n \exp(-Q_c/RT)$, where the stress exponent $n$ (commonly in the range of 3–8 for many metals and alloys) and activation energy $Q_c$ (often close to the self-diffusion activation energy) reflect the climb-and-glide combined mechanism.
- **Climb as a recovery mechanism**: climb allows dislocations of opposite sign on parallel glide planes to annihilate or rearrange into lower-energy configurations (e.g., polygonization into low-angle subgrain boundaries), which is the atomic-scale basis of dynamic and static recovery processes that reduce dislocation density and flow stress during and after high-temperature deformation.
- **Precipitate bypass in superalloys**: in precipitation-strengthened nickel superalloys, dislocation climb around (rather than shearing through) coherent or semi-coherent precipitates (Orowan-climb bypass) becomes an important creep-resistance mechanism at elevated temperature, and alloy/microstructure design (precipitate size, coherency, volume fraction) is deliberately tailored to influence the relative ease of climb bypass versus shearing.

### Engineering and Metallurgical Significance

- **Creep-resistant alloy design**: because climb is diffusion-controlled, reducing the relevant diffusion coefficient (via solid-solution alloying that lowers diffusivity, or via stable precipitate/particle dispersions that pin dislocations and require climb for bypass) is a central strategy in designing creep-resistant alloys for turbine blades, boiler tubing, and other elevated-temperature structural applications.
- **Recrystallization and recovery annealing**: climb-mediated dislocation rearrangement and annihilation is a key mechanism underlying recovery (the partial restoration of properties and reduction of stored energy prior to full recrystallization) during annealing of cold-worked metals.
- **Hot working process design**: hot working operations (forging, rolling above the recrystallization temperature) rely on dynamic recovery (climb-assisted) and/or dynamic recrystallization to prevent excessive strain hardening and cracking during large-strain deformation at elevated temperature — a direct practical exploitation of climb kinetics in manufacturing process design.
- **Diffusion bonding and sintering**: vacancy flux considerations relevant to dislocation climb are conceptually related to (though mechanistically distinct from) the vacancy/atomic diffusion processes underlying diffusion bonding and solid-state sintering densification.

### Related Topics
- Dislocation theory: edge, screw, and mixed dislocation geometry
- Slip systems and critical resolved shear stress (Schmid's Law)
- Creep deformation mechanisms and power-law creep
- Recovery, recrystallization, and grain growth
- Stacking fault energy and its influence on cross-slip/work hardening
- Precipitation strengthening and Orowan bypass mechanisms
- Diffusion in solids (vacancy mechanism, Arrhenius behavior)


```