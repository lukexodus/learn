## Fatigue Mechanisms and S-N Curves


### Overview

Fatigue is the progressive, localized structural damage that occurs when a material is subjected to cyclic (repeated) loading, ultimately leading to fracture at stress levels well below the material's static tensile strength — often below even its yield strength. Fatigue is responsible for a substantial proportion of in-service mechanical and structural failures, making an understanding of its mechanisms and characterization methods (particularly the S-N curve) essential to structural design involving repeated or cyclic loads.

### Nature and Significance of Fatigue

**Key Points**

- Fatigue failure can occur under cyclic stresses substantially lower than a material's ultimate tensile strength or even its yield strength, distinguishing it fundamentally from static overload failure.
- Fatigue failures typically occur with little or no gross plastic deformation prior to final fracture, giving fatigue-cracked components a deceptively brittle appearance even in otherwise ductile materials.
- Cyclic loading relevant to fatigue arises in numerous civil and structural contexts: traffic loading on bridges, wind and wave loading on offshore/tall structures, machinery vibration, thermal cycling, and repeated live-load application on building floor systems.

### The Three Stages of Fatigue Failure

**Key Points**

1. **Crack initiation**: fatigue cracks typically nucleate at a point of local stress concentration — a surface flaw, inclusion, machining mark, corrosion pit, weld toe, or geometric discontinuity — where localized cyclic plastic strain accumulates even though the nominal applied stress may be within the elastic range.
2. **Crack propagation (stable crack growth)**: once initiated, the crack grows incrementally with each load cycle, often leaving characteristic "beach marks" or "striations" on the fracture surface that record successive positions of the crack front (striations, visible at high magnification, correspond to individual load cycles; beach marks are typically visible at macroscopic scale and correspond to changes in loading condition or crack growth rate).
3. **Final fracture**: once the crack has grown to a size at which the remaining (uncracked) cross-section can no longer support the applied load, rapid final fracture occurs — often exhibiting ductile or brittle characteristics depending on the material and loading conditions at that final stage.

### Characteristic Fatigue Fracture Surface

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 600 380">
<text x="300" y="25" font-size="16" font-weight="bold" text-anchor="middle" fill="#1a1a1a">Fatigue Fracture Surface Features (svg_diagram)</text>
<ellipse cx="300" cy="210" rx="180" ry="140" fill="#f2f2f2" stroke="#1a1a1a" stroke-width="2" />
<circle cx="180" cy="150" r="5" fill="#c0392b" />
<text x="130" y="130" font-size="11" fill="#c0392b">Initiation site</text>
<path d="M 180 150 Q 230 175 280 200 Q 330 225 370 255" stroke="#0057b7" stroke-width="1" fill="none" />
<path d="M 190 165 Q 240 190 285 215 Q 335 240 375 268" stroke="#0057b7" stroke-width="1" fill="none" />
<path d="M 200 180 Q 250 205 290 228 Q 340 253 380 280" stroke="#0057b7" stroke-width="1" fill="none" />
<text x="220" y="200" font-size="11" fill="#0057b7">Beach marks (stable crack growth)</text>
<path d="M 380 260 L 420 300 L 400 330 L 440 320 L 410 350" stroke="#c0392b" stroke-width="1.5" fill="none" />
<text x="400" y="300" font-size="11" fill="#c0392b">Final fracture</text>
<text x="405" y="315" font-size="10" fill="#c0392b">(rapid, rough)</text>
</svg>

### The S-N Curve (Wöhler Curve)

**Key Points**

- The **S-N curve** (stress amplitude, S, versus number of cycles to failure, N) is the primary characterization tool for fatigue behavior, obtained by testing multiple specimens of the same material at different applied stress amplitudes and recording the number of cycles to failure at each stress level.
- N is conventionally plotted on a logarithmic scale (given the very large range of cycle counts involved, often spanning several orders of magnitude), while S may be plotted linearly or logarithmically depending on convention.
- For many ferrous metals (notably steels), the S-N curve exhibits a **fatigue limit** (or endurance limit), $\sigma_e$ — a stress amplitude below which the material can theoretically endure an essentially infinite number of cycles without fatigue failure. This produces a curve that flattens to a horizontal asymptote at large N.
- For many non-ferrous metals (e.g., aluminum alloys) and some other material classes, no true fatigue limit exists; instead, the S-N curve continues to slope downward indefinitely (though at a decreasing rate), meaning fatigue strength is often instead reported as a **fatigue strength at a specified number of cycles** (e.g., fatigue strength at $10^7$ or $10^8$ cycles), rather than as a true, unconditional endurance limit.
- [Inference] Because materials without a true fatigue limit will eventually fail under cyclic loading given sufficient cycles regardless of stress amplitude (in principle), fatigue design for such materials typically relies on a specified design life (target number of cycles) with an associated allowable stress, rather than assuming an infinite-life stress threshold as is sometimes done for steels operated below their fatigue limit.

### S-N Curve Diagram

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 380">
<text x="350" y="25" font-size="16" font-weight="bold" text-anchor="middle" fill="#1a1a1a">S-N Curve (svg_diagram)</text>
<line x1="80" y1="330" x2="640" y2="330" stroke="#1a1a1a" stroke-width="2" />
<line x1="80" y1="330" x2="80" y2="60" stroke="#1a1a1a" stroke-width="2" />
<text x="360" y="360" font-size="14" text-anchor="middle" fill="#1a1a1a">Cycles to Failure, N (log scale)</text>
<text x="30" y="200" font-size="14" text-anchor="middle" fill="#1a1a1a" transform="rotate(-90 30 200)">Stress Amplitude, S</text>
<path d="M 110 90 Q 200 150 300 220 Q 400 270 500 285 L 620 285" stroke="#0057b7" stroke-width="3" fill="none" />
<line x1="500" y1="285" x2="620" y2="285" stroke="#2e7d32" stroke-width="2" stroke-dasharray="5,3" />
<text x="530" y="270" font-size="11" fill="#2e7d32">Fatigue limit (σe) — ferrous metals</text>
<path d="M 110 90 Q 200 150 300 220 Q 400 260 500 275 Q 570 282 620 288" stroke="#c0392b" stroke-width="2" stroke-dasharray="6,4" fill="none" />
<text x="450" y="310" font-size="11" fill="#c0392b">Continues sloping — non-ferrous metals</text>
</svg>

### Key Fatigue Loading Parameters

**Key Points**

- Cyclic loading is characterized by several standard parameters:

$$\sigma_{mean} = \dfrac{\sigma_{max} + \sigma_{min}}{2} \qquad \sigma_a = \dfrac{\sigma_{max} - \sigma_{min}}{2}$$



$$R = \dfrac{\sigma_{min}}{\sigma_{max}}$$

Where $\sigma_{mean}$ is mean stress, $\sigma_a$ is stress amplitude, and $R$ is the stress ratio.

- Fully reversed loading (equal magnitude tension and compression, $R = -1$) is a common laboratory test condition, but many real structural loading scenarios involve a non-zero mean stress, which generally reduces fatigue life compared to fully reversed loading at the same stress amplitude.
- Various empirical relationships (e.g., the Goodman, Gerber, and Soderberg relations) are used to account for the combined effect of mean stress and stress amplitude on fatigue life, since a fatigue limit or S-N curve obtained under fully reversed loading does not directly apply when a mean stress is present.

### Factors Affecting Fatigue Life

**Key Points**

- **Surface finish and condition**: rougher surfaces, machining marks, and surface defects act as local stress concentrators and crack initiation sites, generally reducing fatigue life; polished surfaces generally improve fatigue performance compared to as-machined or as-rolled surfaces.
- **Stress concentrations (design geometry)**: notches, holes, fillets, and abrupt section changes concentrate stress and are common fatigue crack initiation sites, making careful attention to geometric detailing critical in fatigue-sensitive design.
- **Residual stresses**: compressive residual stresses at a surface (e.g., introduced by shot peening or certain cold-working processes) generally improve fatigue life by counteracting applied tensile stresses at the surface, where fatigue cracks most commonly initiate; tensile residual stresses (e.g., from certain welding processes) generally reduce fatigue life.
- **Corrosive environment**: simultaneous exposure to a corrosive environment during cyclic loading (**corrosion fatigue**) generally reduces fatigue life compared to the same cyclic loading in a benign environment, and can also eliminate the fatigue limit behavior otherwise seen in some ferrous metals under benign conditions.
- **Temperature**: elevated temperature generally reduces fatigue life and can introduce interaction with creep mechanisms (creep-fatigue interaction) in high-temperature service.

### Civil Engineering Application: Fatigue Design of Steel Bridges

**Example**

Fatigue is a governing design consideration for steel highway and railway bridges subject to repeated traffic loading:

- **Fatigue detail categories**: bridge design codes classify structural details (e.g., welded connections, bolted splices, various weld geometries) into fatigue categories, each associated with its own S-N curve (often expressed with a defined fatigue category and constant-amplitude fatigue threshold), reflecting the significant influence of local geometric stress concentration and weld quality on fatigue performance, independent of the base material's fatigue properties.
- **Stress range** (rather than mean stress or stress ratio alone) is generally the primary parameter used in structural fatigue design of welded steel details, since welded connections typically contain high tensile residual stresses that make the applied mean stress relatively unimportant to fatigue behavior at the weld.
- **Variable-amplitude loading**: real bridge traffic produces variable-amplitude stress cycles rather than the constant-amplitude cycling used in most laboratory S-N testing; cumulative fatigue damage under variable-amplitude loading is commonly estimated using **Miner's rule** (linear cumulative damage summation), though this is a widely used engineering approximation rather than an exact physical model.
- [Unverified] Specific fatigue detail categories, associated S-N curves, and design fatigue life requirements are defined by the governing bridge design code/specification and should be confirmed against the applicable code for a given project.

### Comparative Summary Table

| Concept | Description |
| --- | --- |
| Crack initiation | Nucleates at surface flaws, stress concentrations, inclusions |
| Crack propagation | Incremental growth per cycle; produces beach marks/striations |
| Final fracture | Rapid failure once remaining section cannot carry the load |
| Fatigue (endurance) limit | Stress below which "infinite" life is theoretically possible (some ferrous metals) |
| Fatigue strength at N cycles | Stress corresponding to a specified finite life (materials without a true limit) |
| Stress ratio, $R$ | $\sigma_{min}/\sigma_{max}$; characterizes mean stress condition |
| Miner's rule | Linear cumulative damage model for variable-amplitude loading |

**Next Steps**

- Ductile Versus Brittle Fracture
- Fracture Mechanics and Stress Concentration
- Fatigue Crack Growth and the Paris Law
- Factors Affecting Fatigue Life (Surface Finish, Residual Stress)
- Fatigue Design of Welded Steel Connections
- Creep Behavior and Creep-Fatigue Interaction
- Miner's Rule and Cumulative Fatigue Damage Analysis