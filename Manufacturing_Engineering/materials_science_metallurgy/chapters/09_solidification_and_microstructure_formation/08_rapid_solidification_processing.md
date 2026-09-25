## Rapid Solidification Processing

### Definition and Scope

Rapid Solidification Processing (RSP) refers to a family of manufacturing techniques in which molten metal or alloy is cooled from the liquid state to full solidification at rates typically exceeding $10^3$ K/s, with many industrial and laboratory techniques reaching $10^5$–$10^{10}$ K/s. This is in sharp contrast to conventional casting, where cooling rates are on the order of $10^{-2}$ to $10^1$ K/s.

The defining consequence of RSP is a severe suppression of the time available for diffusion-controlled processes (nucleation, growth, solute partitioning) during the liquid-to-solid transformation. This produces microstructures and phase constitutions that are inaccessible via conventional solidification routes.

### Underlying Solidification Theory

**Undercooling and nucleation kinetics**

Conventional solidification proceeds close to the equilibrium liquidus temperature via heterogeneous nucleation on mold walls, inclusions, or inoculants. RSP techniques, by contrast, achieve large undercoolings ($\Delta T$) before nucleation occurs, because:

- Extremely high cooling rates outpace the kinetics of heterogeneous nucleation at low undercooling.
- Small liquid volumes (droplets, thin melt films) reduce the population of active heterogeneous nucleation sites, pushing the system toward homogeneous or near-homogeneous nucleation behavior.

The classical nucleation rate expression governs this behavior:

$$I = I_0 \exp\left(-\frac{\Delta G^*}{k_B T}\right)$$

where $\Delta G^*$ is the critical free energy barrier for nucleus formation, which scales inversely with the square of undercooling:

$$\Delta G^* \propto \frac{1}{(\Delta T)^2}$$

Larger undercooling sharply increases nucleation rate, favoring the formation of many small nuclei rather than few large ones — a first-order explanation for the grain refinement observed in RSP.

**Solute trapping and partitionless solidification**

Under equilibrium (slow) solidification, solute redistributes between solid and liquid according to the equilibrium partition coefficient $k_0 = C_S/C_L$. At high interface velocities ($V$), characteristic of RSP, the solid-liquid interface advances faster than solute atoms can diffuse away from it, leading to **solute trapping**: the effective partition coefficient $k_v$ approaches unity.

The Aziz continuous-growth model describes this velocity dependence:

$$k_v = \frac{k_0 + (V/V_D)}{1 + (V/V_D)}$$

where $V_D$ is a characteristic diffusive speed at the interface (related to atomic diffusive jump frequency). As $V \to V_D$ or beyond, $k_v \to 1$, meaning the solid inherits the liquid composition without partitioning — **partitionless solidification**. This allows solute concentrations far exceeding the equilibrium solid solubility limit to be retained in the solid, forming extended (metastable) solid solutions.

**Interface stability and the Absolute Stability criterion**

At sufficiently high growth velocity, the classical Mullins-Sekerka instability that causes dendritic/cellular breakdown of a planar interface is itself suppressed. This is the **absolute stability** regime, where the stabilizing effect of solute-induced constitutional undercooling is overwhelmed by capillarity and short diffusion times, restoring planar front growth even at high undercooling. This regime is only reached at very high velocities (often only attainable in laser or electron-beam surface melting) but is conceptually central to understanding why RSP microstructures range from highly refined dendritic to fully planar/microsegregation-free structures depending on processing conditions.

### Key Microstructural Consequences

**[Key Points]**

- **Grain refinement**: High nucleation rates and short growth times yield equiaxed grain sizes from sub-micron to a few micrometers, versus millimeter-to-centimeter scales in conventional castings.
- **Extended solid solubility**: Solute trapping permits metastable supersaturated solid solutions (e.g., extended solubility of Fe in Al beyond the equilibrium ~0.05 at%).
- **Refined or suppressed secondary phases**: Intermetallic and eutectic phases that would coarsen in slow cooling instead form as fine, well-dispersed particles, or are suppressed entirely in favor of metastable phases.
- **Reduced microsegregation**: Shorter diffusion distances and higher effective partition coefficients minimize interdendritic solute segregation.
- **Metastable and amorphous phases**: At sufficiently high cooling rates and appropriate alloy chemistry (deep eutectics, multi-component systems), the liquid can bypass crystallization entirely, forming a metallic glass (amorphous metal).
- **Metastable crystalline phases**: Quasicrystalline phases (e.g., Al-Mn) and non-equilibrium intermetallics can form when cooling rate outpaces the kinetics of equilibrium phase formation but is insufficient for full vitrification.

### Major RSP Techniques

**Melt spinning**

Molten alloy is ejected onto a rapidly rotating, water- or gas-cooled copper or copper-alloy wheel. The melt spreads into a thin ribbon (typically 20–100 μm thick) that solidifies almost instantly upon contact.

- Cooling rates: approximately $10^5$–$10^7$ K/s.
- Product form: continuous ribbon, useful for amorphous alloy production (e.g., Fe-Si-B soft magnetic ribbons, Metglas-type alloys).
- Governing heat transfer is dominated by contact conduction into the wheel; ribbon thickness is inversely related to wheel surface speed.

**Gas atomization**

A molten metal stream is disintegrated into fine droplets by high-velocity inert gas jets (Ar, N₂, He). Droplets solidify in flight before collection as powder.

- Cooling rates: approximately $10^2$–$10^5$ K/s, strongly dependent on droplet diameter ($d$), following approximately $\dot{T} \propto 1/d^2$ for conduction-limited cooling of small spheres.
- Product form: spherical powders (typically 10–150 μm), the feedstock basis for powder metallurgy and, notably, for metal additive manufacturing (laser powder bed fusion, electron beam melting).
- Finer powders cool faster and show greater microstructural refinement/solute retention than coarse powders from the same atomization run — a routinely observed powder-size-dependent effect.

**Water atomization**

Similar principle to gas atomization but uses high-pressure water jets, achieving even faster quenching due to water's higher heat extraction capacity, at the cost of powder sphericity and increased oxidation (relevant mainly to ferrous and less oxygen-sensitive systems).

**Splat quenching / piston-anvil quenching**

A molten droplet is impacted between two rapidly closing conductive surfaces (or a single piston against an anvil), flattening it into a thin foil.

- Cooling rates: among the highest achievable, up to approximately $10^6$–$10^8$ K/s.
- Historically the technique that first produced metallic glasses (Au-Si system, Duwez, 1960).
- Primarily a laboratory-scale technique; limited to small, discontinuous samples.

**Laser surface melting and remelting (LSM)**

A high-energy laser beam locally melts a thin surface layer of a bulk substrate, which then self-quenches via conduction into the surrounding cold bulk material — no external quench medium is required.

- Cooling rates: approximately $10^6$–$10^9$ K/s, among the highest for bulk-attached processing.
- Used for surface hardening, refining as-cast surface microstructures, and producing metastable surface alloys/coatings without altering bulk properties.
- Closely related to selective laser melting (SLM/LPBF) in metal additive manufacturing, where each melt pool experiences RSP-like cooling rates layer by layer.

**Electron beam and plasma processing**

Analogous to laser processing but using electron beams (requiring vacuum) or plasma arcs; used for surface modification and specialty alloy consolidation.

**Chill block melt spinning variants and jet casting**

Includes planar flow casting (a variant of melt spinning optimizing ribbon width/uniformity via a closely-held nozzle) used industrially for producing wide amorphous ribbon for transformer cores.

### Comparative Summary

| Technique | Typical Cooling Rate (K/s) | Product Form | Typical Application |
| --- | --- | --- | --- |
| Melt spinning | $10^5$–$10^7$ | Continuous ribbon | Amorphous soft magnetic alloys |
| Gas atomization | $10^2$–$10^5$ | Spherical powder | AM feedstock, PM parts |
| Water atomization | $10^3$–$10^5$ | Irregular powder | Ferrous PM (lower cost) |
| Splat quenching | $10^6$–$10^8$ | Thin foil (discontinuous) | Research, early glass alloys |
| Laser surface melting | $10^6$–$10^9$ | Surface layer on bulk | Surface hardening, coatings |

### Process Schematic

===MERMAID_DIAGRAM===

flowchart LR

A["Molten alloy (superheated liquid)"] --> B{Heat extraction method}

B --> C["Contact with rotating<br/>cold wheel (melt spinning)"]

B --> D["Gas jet disintegration<br/>(atomization)"]

B --> E["Piston/anvil impact<br/>(splat quenching)"]

B --> F["Laser/e-beam local melt<br/>+ substrate self-quench"]

C --> G["High undercooling ΔT"]

D --> G

E --> G

F --> G

G --> H["Suppressed diffusion,<br/>solute trapping (k_v → 1)"]

H --> I{Cooling rate regime}

I -->|Moderate, ~10^2-10^5 K/s| J["Refined dendritic/cellular<br/>grains, extended solubility"]

I -->|High, ~10^6-10^8 K/s| K["Nanocrystalline or<br/>metastable phases"]

I -->|Very high + glass-forming composition| L["Amorphous metallic glass"]



```
### Worked Example: Estimating Ribbon Cooling Rate in Melt Spinning

For a melt-spun ribbon of thickness $h$ in contact with a cold wheel, a simplified lumped-capacitance estimate of the average cooling rate is:

$$\dot{T} \approx \frac{h_c (T_m - T_w)}{\rho c_p h}$$

where $h_c$ is the interfacial heat transfer coefficient, $T_m$ is the melt temperature, $T_w$ is the wheel temperature, $\rho$ is density, $c_p$ is specific heat, and $h$ is ribbon thickness.

**[Example]** For a Fe-based ribbon with $h_c \approx 10^5$ W/m²K, $(T_m - T_w) \approx 1000$ K, $\rho \approx 7000$ kg/m³, $c_p \approx 600$ J/kgK, and $h = 30\ \mu\text{m}$:

$$\dot{T} \approx \frac{10^5 \times 1000}{7000 \times 600 \times 30\times10^{-6}} \approx \frac{10^8}{1.26\times10^2} \approx 8 \times 10^5 \ \text{K/s}$$

This order-of-magnitude result ($\sim 10^5$–$10^6$ K/s) is consistent with reported melt-spinning cooling rates. [Inference: the specific numerical result depends strongly on assumed $h_c$, which is sensitive to wheel surface condition, atmosphere, and contact quality, and varies significantly across reported experimental studies.]

### Alloy Design Considerations for RSP

- **Glass-forming ability (GFA)**: Alloys with deep eutectics, large negative heats of mixing between constituents, and significant atomic size mismatch (empirical rules from Inoue and others) favor amorphous phase formation under RSP. Multi-component "confusion principle" alloys (e.g., Zr-Ti-Cu-Ni-Be bulk metallic glasses) exploit this to achieve glass formation even at comparatively lower cooling rates.
- **Reduced glass transition temperature** $T_{rg} = T_g/T_l$ (ratio of glass transition to liquidus temperature) is commonly used as an empirical GFA indicator; higher $T_{rg}$ correlates with easier glass formation. [Inference: this is a widely used heuristic correlation rather than a strict physical law, and exceptions exist across alloy families.]
- **Powder metallurgy alloys** (e.g., rapidly solidified Al-Fe-Ce, Al-Cr-Zr aerospace alloys) exploit RSP to retain high solute contents of elements with very low equilibrium solubility (Fe, Ce, Cr), enabling dispersion-strengthened microstructures unattainable via ingot metallurgy.

### Applications

- **Amorphous and nanocrystalline soft magnetic materials**: Transformer cores, magnetic sensors (Fe-Si-B, Fe-Co-B-based ribbons) exploiting low coercivity and low core losses from the absence of crystalline anisotropy.
- **Aerospace-grade rapidly solidified aluminum alloys**: Improved elevated-temperature strength and thermal stability via fine dispersoids from RSP powder consolidated by extrusion/HIP.
- **Additive manufacturing feedstock**: Gas-atomized powders (Ti-6Al-4V, Inconel 718, AlSi10Mg) rely on RSP-controlled powder microstructure and sphericity for consistent melt pool behavior in LPBF/EBM.
- **Bulk metallic glasses (BMGs)**: Structural and functional components (sporting goods, precision gears, MEMS) leveraging high strength, elastic limit, and corrosion resistance from the amorphous state.
- **Surface engineering**: Laser surface melting for wear- and corrosion-resistant refined surface layers on cast components without full bulk heat treatment.

### Characterization Methods

- **X-ray diffraction (XRD)**: Detection of amorphous halo (broad diffuse peak) versus sharp crystalline reflections; used to confirm glass formation or identify metastable crystalline phases.
- **Differential scanning calorimetry (DSC)**: Identification of glass transition ($T_g$), crystallization exotherms ($T_x$), and melting endotherms in amorphous or metastable ribbons/powders.
- **Transmission electron microscopy (TEM)**: Direct imaging of nanocrystalline grain sizes, dendrite arm spacings at sub-micron scale, and metastable precipitate morphology.
- **Electron probe microanalysis (EPMA) / APT**: Quantification of retained supersaturated solute concentrations to verify solute trapping.

### Limitations and Practical Constraints

- **Product geometry constraints**: Most RSP techniques inherently produce thin sections (ribbons, foils, powders) because rapid heat extraction requires a high surface-area-to-volume ratio; producing bulk RSP components generally requires secondary consolidation (powder metallurgy routes: HIP, extrusion, spark plasma sintering).
- **Consolidation challenges**: Retaining the metastable, fine-grained, or amorphous microstructure through consolidation requires strict thermal control, since reheating can trigger crystallization or coarsening, negating the RSP benefit. [Behavior may vary depending on specific consolidation temperature-time paths and alloy stability.]
- **Cost and scale**: Atomization and melt spinning are industrially mature and scalable; splat quenching and many laser-based methods remain limited to research or niche surface-treatment scales.

### Related Topics
- Metallic glasses and bulk metallic glass (BMG) alloy design
- Powder metallurgy and hot isostatic pressing (HIP) consolidation
- Selective laser melting / laser powder bed fusion process fundamentals
- Constitutional undercooling and the Mullins-Sekerka instability
- Solute trapping and non-equilibrium partition coefficients
- Dendritic growth theory (KGT/LKT models) and dendrite arm spacing scaling laws
- Nanocrystalline and quasicrystalline alloy formation
- Dispersion-strengthened rapidly solidified aluminum alloys


```