## Physical and Mechanical Properties of Aggregates


### Overview and Significance

Physical and mechanical properties of aggregates directly govern the fresh-state behavior, strength, and long-term durability of the concrete and asphalt mixtures in which they are used. Building on the geological and classification framework already established, this entry addresses the specific quantifiable properties — specific gravity, absorption, gradation, strength/toughness, and durability-related characteristics — that are measured through standardized test methods and incorporated into mix design and material acceptance decisions.

```mermaid
flowchart TD
    A[Aggregate Properties (svg_diagram)] --> B[Density and Absorption]
    A --> C[Gradation and Particle Size Distribution]
    A --> D[Strength and Toughness]
    A --> E[Durability-Related Properties]
    A --> F[Surface Characteristics]
```

### Specific Gravity and Density

**Definitions**

$$G_s = \frac{\rho_{aggregate}}{\rho_{water}}$$

**Specific gravity (relative density)** expresses aggregate particle density relative to water density, used primarily in mix design volumetric calculations (converting between mass and absolute volume of aggregate in a concrete mixture).

Per ASTM C127 (coarse aggregate) and ASTM C128 (fine aggregate), three distinct specific gravity values are determined:

- **Bulk specific gravity (oven-dry, OD)** — based on oven-dry particle mass, including both permeable and impermeable internal voids within the particle volume
- **Bulk specific gravity (saturated surface-dry, SSD)** — based on saturated surface-dry particle mass (all permeable pores filled with water, surface free of visible moisture), the condition most commonly used as the reference basis in mix design calculations since it represents aggregate condition that neither absorbs from nor contributes water to the mix
- **Apparent specific gravity** — based on oven-dry mass and the volume of only the solid particle material, excluding permeable void volume

**Absorption**

$$\text{Absorption (\%)} = \frac{W_{SSD} - W_{OD}}{W_{OD}} \times 100$$

Where $W_{SSD}$ is saturated surface-dry mass and $W_{OD}$ is oven-dry mass. Absorption quantifies the water an aggregate can absorb into its permeable pore structure, a property essential for accurate mix design water content control.

**Key Points**

- Aggregate moisture condition at batching (which may be air-dry, damp, or wetter than SSD) requires adjustment of both batch water and aggregate mass in mix design calculations, since aggregate moisture state directly affects the effective water-cement ratio of the resulting concrete
- Higher absorption values generally correlate with higher aggregate porosity, which frequently (though not universally) correlates with reduced strength, reduced freeze-thaw durability, and reduced abrasion resistance, making absorption a commonly used general durability screening indicator
- Recycled concrete aggregate (RCA) and some lightweight aggregates typically exhibit substantially higher and more variable absorption than conventional natural aggregate, requiring particular attention to batching moisture control and mix design adjustment

### Unit Weight and Voids

**Unit Weight (Bulk Density)**

Per ASTM C29, the mass of aggregate that fills a container of unit volume, including both the solid aggregate particles and the void spaces between particles, measured under either **loose** (uncompacted) or **rodded/compacted** (per specified compaction procedure) conditions.

**Voids Content**

$$\text{Voids (\%)} = \frac{(G_s \times \rho_w) - M}{G_s \times \rho_w} \times 100$$

Where $G_s$ is bulk specific gravity, $\rho_w$ is the density of water, and $M$ is the measured unit weight, quantifying the percentage of the total volume occupied by air space between particles rather than solid aggregate.

**Key Points**

- Rodded unit weight is used in mix design methods (such as the ACI absolute volume method) to estimate coarse aggregate content per unit volume of concrete
- Lower void content (denser particle packing) generally reduces the cement paste volume required to fill voids and coat particle surfaces for a given workability, an important consideration in optimizing aggregate gradation for economical mix design

### Gradation (Particle Size Distribution)

**Sieve Analysis Procedure**

Per ASTM C136, a representative aggregate sample is passed through a stacked series of standard sieves with progressively smaller openings, and the mass retained on each sieve is recorded, from which cumulative percent passing at each sieve size is calculated and typically plotted as a gradation curve.

**Fineness Modulus**

$$FM = \frac{\sum \text{cumulative \% retained on standard sieves}}{100}$$

Calculated for fine aggregate using a specified standard sieve series (typically No. 4, 8, 16, 30, 50, 100), the fineness modulus provides a single numerical index of overall fineness/coarseness useful for mix proportioning and production consistency monitoring; ASTM C33 specifies an acceptable fineness modulus range (commonly cited as approximately 2.3 to 3.1) for fine aggregate intended for concrete use.

**Key Points**

- **Well-graded** aggregate contains a continuous, well-distributed range of particle sizes, generally producing dense particle packing, reduced void content, and reduced paste demand
- **Gap-graded** aggregate is missing one or more intermediate size fractions, which can be used deliberately in certain specialized mix designs (e.g., some exposed-aggregate architectural finishes) but generally requires careful mix design attention to avoid workability and segregation problems
- **Uniformly-graded (single-size)** aggregate, common in some drainage and asphalt friction course applications, deliberately maximizes void content and permeability rather than minimizing it, illustrating that "good" gradation is application-dependent rather than a single universal target
- Maximum aggregate size affects required cement paste volume, water demand, and (in structural applications) minimum spacing requirements relative to reinforcement; ASTM C33 specifies standard gradation envelope requirements for each nominal maximum size designation

### Strength-Related Properties

**Aggregate Crushing Value (ACV) and Related Indices**

Various international standards (particularly BS/EN methods more common outside North America) quantify aggregate resistance to crushing under gradually applied compressive load, expressed as a percentage of fines produced relative to the original sample mass — lower values indicating greater resistance to crushing and generally higher-quality aggregate for structural applications.

**Los Angeles (LA) Abrasion Test**

Per ASTM C131/C535, aggregate is tumbled in a rotating steel drum along with steel spheres for a specified number of revolutions, and the percentage mass loss (material passing a specified sieve after tumbling relative to original mass) quantifies resistance to abrasion and mechanical degradation.

$$\text{LA Abrasion Loss (\%)} = \frac{M_{original} - M_{retained}}{M_{original}} \times 100$$

**Key Points**

- LA abrasion loss values are widely specified as an acceptance criterion for aggregate used in concrete pavement, asphalt pavement, and base course applications, since aggregate degradation during handling, mixing, placement, and in-service traffic loading directly affects long-term pavement performance
- [Inference] Specific maximum allowable LA abrasion loss values vary by governing specification and application (e.g., differing limits for wearing course asphalt aggregate versus base course aggregate versus structural concrete aggregate), so the applicable project or agency specification should be consulted rather than assuming a single universal threshold

### Durability-Related Properties

**Soundness Testing**

Per ASTM C88, aggregate samples are subjected to repeated cycles of immersion in a saturated sodium or magnesium sulfate solution followed by oven drying, simulating the disruptive internal stresses of natural freeze-thaw weathering through analogous salt crystal growth within pore structures. Percentage mass loss after a specified number of cycles indicates resistance to weathering-induced degradation.

**Freeze-Thaw Resistance (Direct Testing)**

Some standards provide direct freeze-thaw cycling test methods for aggregate durability evaluation, complementing the sulfate soundness test's accelerated simulation approach with more directly analogous freeze-thaw exposure conditions.

**Deleterious Substances**

Per ASTM C33 and related standards, aggregates are screened for limits on deleterious constituents including:

- **Clay lumps and friable particles** — soft, weak material that can break down during mixing or in service
- **Material passing the No. 200 sieve** — excessive fine material (clay, silt) can interfere with cement paste-aggregate bond and increase water demand
- **Lightweight particles (coal, lignite)** — can pop out at exposed surfaces or contribute to surface staining/popouts
- **Organic impurities** — can interfere with cement hydration; commonly screened using a colorimetric test (ASTM C40) as an initial screening indicator

**Alkali-Silica and Alkali-Carbonate Reactivity**

As previously detailed under weathering and durability degradation mechanisms, reactive aggregate mineralogy screened via petrographic examination (ASTM C295) and accelerated expansion testing (ASTM C1260 mortar bar method, ASTM C1293 concrete prism method) represents a critical durability property distinct from the mechanical strength/abrasion properties above, since a mechanically strong and abrasion-resistant aggregate can still pose severe long-term expansive reactivity risk.

### Particle Shape and Texture Testing

**Flat and Elongated Particles**

Per ASTM D4791, quantifies the percentage of coarse aggregate particles exceeding a specified length-to-width or width-to-thickness ratio, since excessive flat/elongated particle content is associated with reduced workability, potential preferential orientation planes of weakness, and reduced compaction quality, particularly significant in asphalt mixture performance.

**Fine Aggregate Angularity**

Per AASHTO T304 (or equivalent standardized methods), quantifies fine aggregate particle angularity through measurement of uncompacted void content, since higher angularity (higher uncompacted voids) generally correlates with improved mechanical interlock relevant to asphalt mixture rutting resistance and, to a lesser extent, concrete strength development.

**Coarse Aggregate Angularity**

Assessed through methods evaluating the percentage of crushed particle faces present on a coarse aggregate sample, particularly relevant to asphalt mixture specification where minimum crushed face percentage requirements are common for surface course applications.

### Comparative Summary of Key Properties and Tests

| Property | Test Method (Representative) | Primary Engineering Relevance |
| --- | --- | --- |
| Specific gravity (bulk SSD) | ASTM C127 (coarse), C128 (fine) | Mix design volumetric proportioning |
| Absorption | ASTM C127/C128 | Batch water adjustment, general durability indicator |
| Unit weight (bulk density) | ASTM C29 | Mix proportioning (absolute volume method) |
| Gradation / fineness modulus | ASTM C136 | Workability, paste demand, mix consistency |
| LA abrasion resistance | ASTM C131/C535 | Resistance to degradation during handling/service |
| Soundness (sulfate) | ASTM C88 | Resistance to freeze-thaw-analogous weathering |
| Deleterious substances | ASTM C33 (limits), various specific tests | Screening for weak/harmful constituents |
| Alkali-silica reactivity | ASTM C1260/C1293, C295 | Long-term expansive reaction risk |
| Flat and elongated particles | ASTM D4791 | Workability, compaction quality, weakness planes |
| Fine/coarse aggregate angularity | AASHTO T304 and related | Asphalt rutting resistance, mechanical interlock |

### Interrelationship Between Properties

**Example:**

A crushed limestone coarse aggregate source being evaluated for a new highway pavement project would typically undergo a battery of these tests together rather than any single test in isolation: specific gravity and absorption for mix design proportioning, gradation for compliance with the specified size number, LA abrasion for resistance to degradation under paver and traffic action, sulfate soundness for freeze-thaw durability screening, and petrographic/ASR expansion testing given that some regional limestone sources contain dolomitic phases with alkali-carbonate reactivity potential — illustrating that comprehensive aggregate qualification requires the combined evaluation of physical, mechanical, and durability properties rather than reliance on any single indicator.

**Key Points**

- No single property reliably predicts overall aggregate performance; specifications typically require simultaneous compliance across multiple independent property categories (gradation, strength/abrasion, soundness, deleterious substance limits, and reactivity screening where applicable)
- Properties can sometimes present conflicting considerations in aggregate selection: for example, highly angular, rough-textured aggregate may improve mechanical interlock and bond strength while simultaneously reducing workability, requiring mix design adjustments (additional paste volume, water-reducing admixtures) to balance these competing effects

### Common Misconceptions

- Passing the LA abrasion resistance test does **not** independently confirm freeze-thaw durability or absence of reactive mineralogy; abrasion resistance, soundness, and reactivity are distinct properties governed by different underlying mechanisms and require separate, specific testing.
- Aggregate absorption is **not** simply an inconvenient batching adjustment factor; while it does require water/mass correction in mix design, elevated absorption is also a broader durability indicator often correlating with increased porosity and reduced resistance to freeze-thaw and other degradation mechanisms.
- A well-graded aggregate blend is **not** universally the correct target for every application; uniformly-graded, high-void aggregate is deliberately specified for drainage layers and certain asphalt friction course applications where permeability, not density, is the design objective.
- High fineness modulus or specific gravity values are **not** inherently "better" or "worse" in isolation; these are descriptive index values used within a broader mix design context, and their appropriateness depends on the specific mix design method and target concrete properties rather than representing an absolute quality scale.

### Related Topics

- Sources and Classification of Aggregates
- Aggregate Gradation Requirements and Mix Design Proportioning
- Alkali-Silica Reaction and Aggregate Reactivity Testing
- Freeze-Thaw Resistance and Air-Entrainment Design
- Asphalt Mixture Design and Aggregate Angularity Requirements
- Concrete Mix Design Methods (Absolute Volume Method)
- Recycled Concrete Aggregate Quality Screening
- Standard Test Methods and Specifications (ASTM C09 Committee Standards)