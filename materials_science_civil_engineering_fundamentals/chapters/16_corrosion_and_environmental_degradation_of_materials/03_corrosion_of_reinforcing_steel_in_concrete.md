## Corrosion of Reinforcing Steel in Concrete


### Overview and Significance

Corrosion of embedded reinforcing steel is the single most common cause of premature deterioration in reinforced concrete structures worldwide, affecting bridges, parking structures, marine infrastructure, and buildings. Unlike corrosion of bare steel exposed directly to atmosphere, rebar corrosion occurs within a highly alkaline, initially protective cementitious environment, and its onset, propagation, and structural consequences are governed by a distinct set of physical and electrochemical mechanisms specific to the concrete matrix.

### Passivation of Steel in Concrete

**Mechanism**

Fresh concrete pore solution has a pH typically in the range of 12.5 to 13.5 due to dissolved calcium, sodium, and potassium hydroxides released during cement hydration. At this high pH, steel spontaneously forms a thin, dense, adherent passive oxide film (predominantly $\gamma\text{-Fe}_2\text{O}_3$/$\text{Fe}_3\text{O}_4$-type layers, only a few nanometers thick) that reduces the corrosion rate to a negligible level — often cited as roughly two to three orders of magnitude lower than the rate of unprotected steel in a similar moist environment.

**Key Points**

- Passivation is a direct consequence of the alkaline pore solution, not the physical barrier of concrete cover alone
- The passive film is stable across the normal pH range of sound, uncarbonated, chloride-free concrete
- Concrete cover serves two separate protective functions: (1) maintaining the alkaline chemical environment at the rebar surface, and (2) acting as a physical/diffusion barrier limiting ingress of aggressive agents (chlorides, $\text{CO}_2$, moisture, oxygen)
- Passivity breakdown, not the mere presence of moisture or oxygen, is the necessary precondition for active corrosion to begin

### Depassivation Mechanisms

Two principal mechanisms destroy the protective passive film and initiate active corrosion; a given structure may be affected by one or both simultaneously.

#### Chloride-Induced Corrosion

**Mechanism**

Chloride ions, whether from marine exposure, deicing salts, or contaminated raw materials, penetrate the concrete cover primarily by diffusion (and capillary absorption in the unsaturated zone). Once the chloride concentration at the rebar surface exceeds a critical **chloride threshold**, the ions locally adsorb onto and penetrate the passive film, converting it to soluble iron chloride complexes at discrete weak points rather than uniformly dissolving it.

**Key Points**

- Produces highly localized, pitting-type attack rather than general corrosion, because chloride action is site-specific at passive film flaws
- The **chloride threshold** is commonly expressed as a chloride-to-hydroxide ratio or as a total/water-soluble chloride content relative to cement mass (frequently cited around 0.2–0.4% by mass of cement for water-soluble chloride, though values vary with cement type, cover quality, and moisture condition)
- [Inference] Published chloride threshold values vary considerably across studies and codes because they depend on cement composition, degree of hydration, moisture state, and test methodology; site-specific or code-referenced values should be used for design and assessment rather than a single universal number
- Chloride penetration rate is commonly modeled using Fick's second law of diffusion:

$$C(x,t) = C_s \left[1 - \text{erf}\left(\frac{x}{2\sqrt{D_c t}}\right)\right]$$

Where $C(x,t)$ is chloride concentration at depth $x$ and time $t$, $C_s$ is the surface chloride concentration, $D_c$ is the apparent chloride diffusion coefficient, and $\text{erf}$ is the Gauss error function. [Inference] This model assumes a constant surface concentration and diffusion-dominated transport; in practice, $D_c$ is time-dependent (typically decreasing as hydration continues) and surface chloride buildup varies with exposure conditions, so refined models (e.g., time-dependent diffusion coefficients per fib Model Code or DuraCrete approaches) are often used for service-life prediction rather than the simple closed-form solution alone.

**Example:**

A reinforced concrete bridge deck subjected to annual deicing salt application develops a chloride concentration gradient from the top surface downward; once the chloride content at the top mat of rebar exceeds the threshold, localized pitting corrosion initiates at the most vulnerable points, producing the characteristic pattern of scattered rust staining and delamination often visible along deck surfaces before more widespread deterioration.

#### Carbonation-Induced Corrosion

**Mechanism**

Atmospheric carbon dioxide diffuses into the concrete pore structure and reacts with calcium hydroxide (and to a lesser extent other alkaline hydration products) according to:

$$\text{Ca(OH)}_2 + \text{CO}_2 \rightarrow \text{CaCO}_3 + \text{H}_2\text{O}$$

This reaction progressively consumes the pore solution's alkalinity reserve, reducing pH from approximately 13 down to below 9 within the **carbonated zone**. Once the carbonation front reaches the rebar depth, the passive film becomes thermodynamically unstable and depassivates essentially uniformly across the exposed bar surface.

**Key Points**

- Produces more general, uniform-type corrosion along the affected bar length, in contrast to the localized pitting typical of chloride attack
- Carbonation depth is commonly modeled with a square-root-of-time relationship:

$$x_c = k\sqrt{t}$$

Where $x_c$ is carbonation depth, $t$ is time, and $k$ is a carbonation rate coefficient dependent on concrete quality (permeability, water-cement ratio), curing, and exposure environment (relative humidity, $\text{CO}_2$ concentration)

- Carbonation rate is maximized at intermediate relative humidity (roughly 50–70%); very dry conditions limit $\text{CO}_2$ dissolution into pore water, while fully saturated conditions restrict gaseous $\text{CO}_2$ diffusion
- Lower water-cement ratio, adequate curing, and sufficient cover depth are the primary mitigating design factors, since they directly reduce concrete permeability and the rate coefficient $k$

**Example:**

An older reinforced concrete building with substandard cover and a high water-cement ratio, exposed to urban atmospheric $\text{CO}_2$ over several decades, may develop carbonation-induced corrosion appearing as broadly distributed cracking and spalling along exposed structural members, rather than the isolated pitting pattern typical of chloride attack.

### Two-Stage Service Life Model (Tuutti Model)

The most widely referenced conceptual framework for reinforced concrete durability divides the corrosion process into two distinct phases:

```mermaid
flowchart LR
    A[Time Zero - Construction] --> B[Initiation Period: chloride/CO2 ingress, no active corrosion yet]
    B --> C[Depassivation Threshold Reached (svg_diagram)]
    C --> D[Propagation Period: active corrosion, section loss, cracking]
    D --> E[Serviceability/Limit State Reached]
```

**Initiation Period**

The time required for aggressive agents (chlorides or carbonation front) to penetrate the cover and reach the depassivation threshold at the rebar surface. No significant corrosion occurs during this phase; it is governed primarily by diffusion-controlled transport processes and can be extended through cover depth, low-permeability concrete mix design, and supplementary cementitious materials.

**Propagation Period**

The period following depassivation during which active corrosion proceeds, consuming steel section and generating expansive corrosion products until a defined limit state is reached (e.g., first visible cracking, unacceptable section loss, or loss of bond/structural capacity). Propagation rate depends on available moisture, oxygen access, temperature, and electrical resistivity of the concrete.

**Design Implication**

$$t_{service} = t_{initiation} + t_{propagation}$$

Most current durability design codes (e.g., fib Model Code, various national standards) focus design effort primarily on extending $t_{initiation}$, since propagation-phase behavior is comparatively harder to predict reliably and is generally treated as a smaller, sometimes neglected, allowance in design service life calculations. [Inference] The relative weighting of initiation versus propagation life in a specific design depends on the governing code and owner-specified serviceability criteria, so the assumption of a negligible propagation period should be verified against the applicable design standard rather than treated as universal.

### Consequences of Active Corrosion

**Volumetric Expansion and Cracking**

Iron corrosion products (various iron oxides/hydroxides) occupy substantially greater volume than the original metallic iron consumed — commonly cited as approximately 2 to 6+ times greater volume depending on the specific oxide/hydroxide phase formed. This expansion generates radial tensile stresses in the surrounding concrete that:

1. Initiate cracking parallel to the rebar (longitudinal cracks along the bar line)
2. Propagate to the concrete surface as cover-parallel cracks widen
3. Eventually cause **delamination** (a subsurface horizontal crack plane at the rebar depth) and **spalling** (loss of the concrete cover layer)

**Structural Consequences**

- **Reduction in steel cross-sectional area**, directly reducing flexural and shear capacity
- **Loss of bond** between rebar and surrounding concrete due to interfacial cracking and loss of mechanical interlock from rib degradation
- **Reduced ductility**, particularly in cases of localized pitting, since a corroded bar can exhibit brittle-like fracture behavior at the pit root despite the bulk material remaining ductile steel
- In severe cases, **complete loss of composite action** between reinforcement and concrete, effectively converting a reinforced section toward unreinforced behavior at the affected location

**Example:**

A parking structure column with corroding rebar due to chloride-laden runoff will typically first exhibit rust staining, followed by fine longitudinal cracks along the bar lines, progressing to spalled cover exposing corroded, section-reduced bars — each visible stage corresponding to advancing propagation-phase section loss that can be approximately correlated to elapsed time using regional deterioration models.

### Influencing Factors Summary

| Factor | Effect on Corrosion Risk |
| --- | --- |
| Water-cement ratio | Lower ratio reduces permeability, slows both chloride ingress and carbonation |
| Concrete cover depth | Greater cover extends initiation period for both mechanisms |
| Supplementary cementitious materials (fly ash, slag, silica fume) | Generally reduce permeability and chloride diffusion coefficient; may alter carbonation resistance and alkalinity reserve depending on replacement level |
| Concrete resistivity | Higher resistivity limits ionic current flow, reducing propagation-phase corrosion rate |
| Relative humidity / moisture cycling | Governs oxygen and ion mobility; intermediate moisture levels often most aggressive for propagation |
| Crack width (structural cracks) | Wider surface cracks can provide direct, accelerated pathways for chloride and $\text{CO}_2$ ingress to rebar |
| Temperature | Higher temperature generally accelerates diffusion and electrochemical reaction kinetics |

### Diagnostic and Assessment Methods

- **Half-cell potential mapping (ASTM C876)** — maps electrochemical potential across a structure's surface using a reference electrode to identify zones with elevated probability of active corrosion
- **Concrete resistivity measurement** — assesses ease of ionic current flow, correlating with likely corrosion propagation rate
- **Linear polarization resistance (LPR)** — provides a quantitative estimate of instantaneous corrosion current density ($i_{corr}$) at tested locations
- **Chloride profiling** — sampling concrete powder at incremental depths and laboratory titration to establish the chloride concentration profile against depth, used to back-calculate diffusion coefficients and predict future initiation timelines
- **Carbonation depth testing** — spraying a freshly broken/cored concrete surface with phenolphthalein indicator solution; the uncarbonated (high-pH) zone turns pink/magenta while the carbonated zone remains colorless, giving a direct visual carbonation depth measurement
- **Visual condition survey** — cataloging rust staining, cracking patterns, delamination (commonly detected by chain drag or hammer sounding), and spalling extent

### Protection and Mitigation Strategies

**Design-Stage Strategies**

- Adequate concrete cover per exposure classification (e.g., ACI 318 exposure categories, Eurocode 2 exposure classes)
- Low permeability concrete mix design (low water-cement ratio, appropriate supplementary cementitious materials)
- Corrosion-resistant reinforcement: epoxy-coated rebar, galvanized rebar, stainless steel rebar, or fiber-reinforced polymer (FRP) bars for the most aggressive exposures
- Corrosion inhibiting admixtures (e.g., calcium nitrite, which raises the effective chloride threshold)
- Proper detailing to manage drainage and minimize ponding/direct salt-laden water exposure on critical members

**Existing Structure Mitigation**

- Cathodic protection (impressed current or sacrificial anode systems) applied to existing reinforcement networks
- Electrochemical chloride extraction and re-alkalization treatments
- Concrete patch repair combined with corrosion inhibitor application or migrating corrosion inhibitors
- Application of surface treatments/sealers to reduce further moisture and chloride/$\text{CO}_2$ ingress
- Supplemental reinforcement or section enlargement where structural capacity has been compromised

### Common Misconceptions

- Concrete cover does **not** protect steel purely as a physical shield; the high-pH chemical environment it maintains is equally, if not more, fundamental to passivation.
- Carbonation and chloride attack are **not** mutually exclusive; combined exposure (carbonated cover plus chloride ingress) can produce accelerated depassivation compared to either mechanism alone. [Inference] The degree of interaction and acceleration from combined exposure is condition-specific and best evaluated through structure-specific assessment rather than assuming a fixed combined effect.
- Visible surface cracking or rust staining does **not** necessarily indicate the full extent of underlying section loss, particularly for chloride-induced pitting, where surface symptoms may lag significantly behind actual structural section reduction.
- Epoxy-coated rebar reduces but does **not** eliminate corrosion risk; coating damage during handling/placement, combined with chloride ingress through inevitable holidays or cracks, can still lead to corrosion, sometimes with disbondment effects that complicate assessment.

### Related Topics

- Electrochemical Principles of Corrosion (foundational mechanisms)
- Uniform, Galvanic, Pitting, and Crevice Corrosion
- Chloride Diffusion Modeling and Service Life Prediction (Fick's Law, fib Model Code approaches)
- Carbonation of Concrete: Mechanisms and Rate Prediction
- Cathodic Protection of Reinforced Concrete Structures
- Corrosion-Resistant Reinforcement (Epoxy-Coated, Galvanized, Stainless, FRP Rebar)
- Concrete Durability Design and Exposure Classification (ACI 318, Eurocode 2)
- Non-Destructive Evaluation of Reinforced Concrete Condition
- Repair and Rehabilitation Strategies for Corrosion-Damaged Concrete