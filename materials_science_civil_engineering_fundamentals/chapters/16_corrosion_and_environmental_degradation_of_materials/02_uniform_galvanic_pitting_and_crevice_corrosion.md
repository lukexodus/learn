## Uniform, Galvanic, Pitting, and Crevice Corrosion


### Overview and Classification

Corrosion is commonly classified by its **morphology** — the physical form of metal loss on the surface — rather than solely by mechanism. Morphological classification matters in civil engineering because inspection strategy, risk assessment, and remaining-service-life prediction differ substantially between a uniformly thinning member and one with hidden, localized penetration. The eight classical Fontana categories include uniform, galvanic, crevice, pitting, intergranular, selective leaching, erosion-corrosion, and stress-corrosion; this entry covers the four most relevant to structural and infrastructure materials.

```mermaid
flowchart TD
    C[Corrosion Morphology (svg_diagram)] --> U[Uniform - even surface loss]
    C --> G[Galvanic - dissimilar metal coupling]
    C --> P[Pitting - localized penetration]
    C --> CR[Crevice - occluded geometry attack]
```

### Uniform (General) Corrosion

**Definition and Mechanism**

Uniform corrosion proceeds essentially at the same rate over the entire exposed metal surface, with anodic and cathodic sites continuously shifting position at a microscopic scale (microcell corrosion). It is the most common form of corrosion by total tonnage of metal affected and results in relatively even thinning.

**Key Points**

- Occurs when the metal surface is chemically and metallurgically homogeneous and exposure conditions (moisture, oxygen, temperature, pollutants) are uniform across the surface
- Predictable and quantifiable using mass-loss or thickness-loss rate (mm/year, mpy)
- Governs design allowances such as **corrosion allowance** thickness in steel structures, pipelines, and tanks
- Generally the least dangerous corrosion form because failure is gradual and detectable through routine thickness measurement

**Example:**

An unprotected steel bridge girder exposed to normal atmospheric conditions loses thickness fairly evenly across its surface over decades; engineers can measure loss with an ultrasonic thickness gauge and predict remaining service life using a linear or power-law corrosion rate model.

**Prediction and Modeling**

$$d(t) = A \cdot t^{B}$$

Where $d(t)$ is depth of penetration at time $t$, $A$ is a material/environment constant, and $B$ is an empirical exponent (often less than 1, reflecting the protective, if imperfect, effect of accumulating corrosion products slowing diffusion of reactants to the metal surface over time). [Inference] Exponent $B$ values are empirically derived from field or laboratory exposure data and vary by alloy, atmosphere classification (e.g., ISO 9223 categories), and pollutant levels, so a generic exponent should not be applied without site-specific or standard-referenced calibration.

**Control Methods**

- Protective coatings (paint systems, galvanizing, metallizing)
- Cathodic protection
- Corrosion allowance in design thickness
- Material selection (weathering steel, stainless alloys)
- Environmental control (dehumidification, ventilation)

### Galvanic Corrosion

**Definition and Mechanism**

Galvanic corrosion (also called bimetallic or dissimilar-metal corrosion) occurs when two electrically connected dissimilar metals or alloys are exposed to the same electrolyte. A potential difference between the two materials drives current flow, accelerating corrosion of the more active (anodic) metal while suppressing corrosion of the more noble (cathodic) metal.

**The Galvanic Series**

Unlike the standard EMF series (measured under idealized single-ion-activity conditions), the **galvanic series** ranks real alloys by measured corrosion potential in a specific practical electrolyte (commonly flowing seawater), accounting for passive films.

| Relative Position | Representative Materials |
| --- | --- |
| Active (anodic, corrodes preferentially) | Magnesium, Zinc, Galvanized steel, Aluminum alloys, Cast iron, Carbon steel |
| Intermediate | Lead, Tin, Brass, Bronze, Copper, Nickel (active) |
| Noble (cathodic, protected) | Nickel (passive), Stainless steel (passive), Titanium, Graphite, Gold, Platinum |

**Factors Governing Severity**

1. **Potential difference** — larger separation in the galvanic series generally produces higher driving force (though passive film behavior can override simple ranking)
2. **Area ratio** — an unfavorable area ratio (small anode, large cathode) is the single most damaging configuration, since the total cathodic current is concentrated onto a small anodic area, producing intense localized attack. A favorable ratio (large anode, small cathode) dilutes the effect.
3. **Electrolyte conductivity and composition** — higher conductivity electrolytes (seawater) extend the effective distance over which galvanic effects occur; low-conductivity electrolytes confine the effect near the metal junction
4. **Distance from the junction** — galvanic attack is generally most severe near the contact point and diminishes with distance

**Example:**

A steel structural bracket fastened with copper alloy bolts in a humid, marine-exposed environment: the steel becomes the anode (small anode if bolt area is large relative to steel, though typically bolt area is small — in this configuration, steel being anodic with a *large* anode area relative to the copper bolts is comparatively less severe than the reverse case). Conversely, a small steel fastener holding a large copper sheet member represents the dangerous "small anode/large cathode" configuration and would corrode rapidly.

**Control Methods**

- Electrical isolation (dielectric bushings, gaskets, isolating washers) to break the metallic path
- Avoid unfavorable anode-to-cathode area ratios
- Apply coatings preferentially to the cathodic (noble) member — coating only the anode is counterproductive, since any coating holiday concentrates attack onto a very small exposed anodic area
- Select metals close together in the galvanic series
- Use sacrificial spacers or replaceable anodic inserts at unavoidable dissimilar-metal joints

### Pitting Corrosion

**Definition and Mechanism**

Pitting is a highly localized form of corrosion producing small-diameter cavities or holes while the surrounding surface remains largely unaffected. It is considered one of the most insidious corrosion forms because material section loss and structural risk are disproportionate to the visible surface damage and total mass loss.

**Initiation Mechanism**

Pitting typically initiates at a local breakdown of a passive film — often at a metallurgical heterogeneity (inclusion, grain boundary, mechanical scratch) or, in chloride environments, when aggressive chloride ions locally penetrate and destabilize the oxide film once a critical **pitting potential** ($E_{pit}$) or local chloride threshold is exceeded.

**Autocatalytic Propagation**

Once initiated, pit growth becomes self-sustaining through a well-documented autocatalytic mechanism:

1. Metal dissolution inside the pit ($\text{Fe} \rightarrow \text{Fe}^{2+} + 2e^-$) produces excess positive charge
2. Chloride ions migrate into the pit to maintain electrical neutrality, forming metal chlorides
3. Metal chlorides hydrolyze: $\text{Fe}^{2+} + 2\text{H}_2\text{O} \rightarrow \text{Fe(OH)}_2 + 2\text{H}^+$, producing hydrogen ions and lowering local pH
4. The increasingly acidic, chloride-rich occluded environment inside the pit further accelerates dissolution, while the pit mouth (in contact with bulk, oxygenated electrolyte) acts as the cathode
5. Oxygen depletion inside the pit reinforces the separation between anodic (pit interior) and cathodic (external surface) zones — an oxygen concentration cell superimposed on the chloride attack

```mermaid
flowchart TD
    A[Pit Interior - Anode (svg_diagram)] -->|Fe2+ dissolves| B[Cl- migrates in, hydrolysis lowers pH]
    B --> C[Autocatalytic acceleration]
    D[Pit Mouth / External Surface - Cathode] -->|O2 + 2H2O + 4e- to 4OH-| D
    A -.electron flow through metal.-> D
```

**Assessment Metrics**

- **Pitting factor** = deepest pit penetration ÷ average penetration calculated from uniform mass loss (values significantly greater than 1 indicate dangerous localization)
- **Pitting potential ($E_{pit}$)** determined via cyclic polarization testing (e.g., ASTM G61) — the potential above which stable pits initiate and grow
- **Critical Pitting Temperature (CPT)** — for stainless alloys, the temperature above which pitting initiates in a standard chloride test solution (relevant to alloy selection in marine and chemical-exposure structures)

**Example:**

A stainless steel handrail post embedded in a chloride-contaminated concrete base at a coastal boardwalk may exhibit only a small surface discoloration while an internal pit has already penetrated a significant fraction of the wall thickness, with the risk of sudden, unpredicted section failure under load.

**Control Methods**

- Select alloys with higher **Pitting Resistance Equivalent Number (PREN)**, calculated approximately as $\text{PREN} = \%\text{Cr} + 3.3(\%\text{Mo}) + 16(\%\text{N})$, for stainless and duplex stainless steels
- Reduce chloride exposure (drainage design, deicing salt management, protective barriers)
- Maintain adequate passivation conditions (high pH cover in concrete, clean smooth surface finish free of inclusions/scratches)
- Cathodic protection to suppress potential below the pitting potential

### Crevice Corrosion

**Definition and Mechanism**

Crevice corrosion is a localized attack occurring within or immediately adjacent to a narrow, shielded gap (crevice) formed between two mating surfaces — metal-to-metal joints, metal-to-nonmetal contacts (gaskets, washers, fasteners), or beneath deposits, biofouling, and debris. It shares the same fundamental autocatalytic acidification mechanism as pitting but is initiated primarily by a geometric/diffusion restriction rather than passive-film breakdown at a metallurgical defect.

**Mechanism Sequence**

1. Initially, corrosion (if any) proceeds at the same low rate inside and outside the crevice
2. Restricted electrolyte exchange within the crevice leads to **oxygen depletion** inside the confined space, since consumed oxygen cannot be replenished by diffusion fast enough
3. The oxygen-depleted crevice interior becomes anodic; the well-aerated external surface becomes cathodic (a classic **oxygen concentration cell**)
4. As in pitting, chloride ion migration into the anodic crevice and subsequent metal chloride hydrolysis progressively acidifies the occluded solution, sustaining and accelerating attack
5. The small anode (crevice) to large cathode (external surface) area ratio intensifies localized penetration

**Distinguishing Crevice Corrosion from Pitting**

| Aspect | Pitting | Crevice Corrosion |
| --- | --- | --- |
| Initiation site | Passive film defect, inclusion | Geometric occlusion (gap, deposit, joint) |
| Threshold potential/chloride level required | Typically higher | Typically lower (crevice geometry pre-establishes oxygen depletion) |
| Common locations | Open, exposed surfaces | Bolted joints, gasket interfaces, under washers, beneath marine growth or deposits |
| Onset conditions | Requires local film breakdown event | Requires only sufficiently narrow, stagnant gap plus electrolyte |

**Example:**

A bolted steel splice connection on a marine pier, where the faying surfaces between the connected plates trap moisture and exclude oxygen, is a classic crevice corrosion site — often producing significant hidden section loss at the joint interface long before surface corrosion elsewhere on the same members becomes severe.

**Control Methods**

- Design detailing to eliminate or minimize crevices (welded joints instead of bolted/riveted where feasible, sealed joints, drainage to prevent standing water/debris accumulation)
- Use of solid, non-absorbent gasket materials, or eliminating gaskets where practical
- Select crevice-resistant alloys (higher PREN, as with pitting resistance) for unavoidable occluded geometries
- Regular removal of deposits, marine fouling, and debris from joints during maintenance
- Cathodic protection, though effectiveness inside deep or tight crevices can be limited due to restricted current/ion access

[Inference] The relative effectiveness of cathodic protection specifically at crevice sites is limited by current and electrolyte access into the occluded geometry, so field verification of protection potentials at representative crevice locations is generally recommended rather than assuming uniform protection across a structure from bulk potential readings alone.

### Comparative Summary

| Corrosion Type | Distribution | Detectability | Typical Structural Risk |
| --- | --- | --- | --- |
| Uniform | Even, whole surface | High (routine thickness survey) | Predictable, manageable via allowance |
| Galvanic | At/near dissimilar-metal junctions | Moderate (visible at joints) | High if area ratio unfavorable |
| Pitting | Discrete, scattered, deep | Low (small surface indication) | High — hidden penetration, stress concentration |
| Crevice | Confined to occluded geometry | Very low (hidden inside joint) | High — hidden penetration at load-critical connections |

### Common Misconceptions

- A small amount of surface rust does **not** indicate the true severity of underlying pitting or crevice corrosion — visual surface condition can significantly underestimate actual section loss.
- Galvanic corrosion severity is **not** determined by potential difference alone — area ratio is frequently the dominant factor in practical structural failures.
- Stainless steel is **not** inherently immune to localized corrosion; its passive film is specifically vulnerable to chloride-induced pitting and crevice attack despite excellent resistance to uniform corrosion.
- Crevice corrosion is **not** limited to metal-to-metal contacts; nonmetallic gaskets, coatings, marine growth, and sediment deposits create equally effective occluded geometries.

### Next Steps

- Electrochemical Principles of Corrosion (foundational mechanisms and thermodynamics)
- Stress-Corrosion Cracking and Corrosion Fatigue
- Intergranular Corrosion and Sensitization in Stainless Steels
- Erosion-Corrosion and Cavitation Damage
- Cathodic Protection System Design (Sacrificial and Impressed Current)
- Pitting Resistance Equivalent Number (PREN) and Alloy Selection Criteria
- Chloride-Induced Reinforcement Corrosion in Concrete Structures
- Corrosion Testing Standards (ASTM G48, G61, G78 for pitting and crevice evaluation)
- Design Detailing to Mitigate Crevice Formation in Structural Connections