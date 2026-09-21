## Stress and Adhesion in Deposited Films


### Overview

Stress and adhesion are two closely related mechanical properties of deposited thin films that critically determine device reliability, yield, and long-term performance. Film stress arises from a combination of thermal mismatch and intrinsic growth-related mechanisms and can cause wafer bowing, cracking, or delamination if not controlled, while adhesion describes the strength of the bond between a film and its underlying substrate or adjacent layer, with poor adhesion leading to blistering, peeling, or delamination during subsequent processing or device operation. Both properties must be carefully engineered and characterized throughout a deposition process, since a film that is otherwise electrically and chemically ideal can render a device non-functional or unreliable if its mechanical stress or adhesion is inadequate.

### Types of Film Stress

**Key Points**

Total film stress is generally decomposed into two contributing components:

$$\sigma_{total} = \sigma_{thermal} + \sigma_{intrinsic}$$

**Thermal (Extrinsic) Stress**

Arises from the mismatch in coefficient of thermal expansion (CTE) between the deposited film and the substrate, combined with the temperature change experienced between the deposition temperature and the temperature at which the film is subsequently used or measured (commonly room temperature). As the film-substrate system cools from deposition temperature, the film and substrate attempt to contract by different amounts due to their differing CTE values, and since they remain bonded together, this mismatch generates stress:

$$\sigma_{thermal} = \frac{E_f}{1-\nu_f}(\alpha_f - \alpha_s)\Delta T$$

where $E_f$ is the film's Young's modulus, $\nu_f$ is the film's Poisson's ratio, $\alpha_f$ and $\alpha_s$ are the film and substrate CTE values respectively, and $\Delta T$ is the temperature change from deposition to measurement.

**Intrinsic Stress**

Arises from the film's growth mechanism itself, independent of any thermal cycling — a purely kinetic/structural consequence of how atoms arrange themselves during deposition. Sources of intrinsic stress include:

- **Grain boundary formation and coalescence**: As isolated islands (from the nucleation process) grow and coalesce into a continuous film, grain boundary formation can generate tensile stress as adjacent islands are pulled together to eliminate surface energy at their boundary.
- **Adatom peening/densification**: Energetic arriving species (particularly relevant in sputtering and ion-assisted deposition, where adatoms arrive with higher kinetic energy than in simple thermal evaporation) can compact the growing film structure, generally producing compressive stress.
- **Impurity incorporation and point defects**: Incorporated impurities (e.g., hydrogen in PECVD films) or point defects can distort the local lattice/structure, contributing additional stress depending on the specific defect type and concentration.
- **Phase transformations and grain growth during or after deposition**: Structural changes occurring during deposition or subsequent thermal processing can introduce additional stress contributions as the film's microstructure evolves.

### Tensile vs. Compressive Stress

**Key Points**

- **Tensile stress**: The film "wants" to contract relative to its as-deposited dimensions but is constrained by the substrate, pulling the substrate to bow concave (toward the film side) — commonly associated with certain LPCVD films (e.g., stoichiometric LPCVD silicon nitride is a classic example of a highly tensile film) and with grain-boundary-formation-dominated intrinsic stress mechanisms.
- **Compressive stress**: The film "wants" to expand relative to its as-deposited dimensions but is constrained by the substrate, bowing the substrate convex (away from the film side) — commonly associated with energetic-deposition-dominated processes (e.g., certain sputtered films with significant adatom peening) and with some PECVD films depending on specific plasma conditions.
- Film stress is commonly reported in units of dynes/cm² or Pascals (with tensile stress conventionally positive and compressive stress conventionally negative, though sign conventions can vary by source), and is frequently measured via wafer curvature (Stoney's equation, discussed below) rather than direct mechanical testing.

### Measuring Stress: Stoney's Equation

**Key Points**

The most common practical method for measuring thin-film stress uses the change in substrate curvature induced by the deposited film, related through **Stoney's equation**:

$$\sigma_f = \frac{E_s t_s^2}{6(1-\nu_s)t_f}\left(\frac{1}{R}-\frac{1}{R_0}\right)$$

where $E_s$ and $\nu_s$ are the substrate's Young's modulus and Poisson's ratio, $t_s$ is substrate thickness, $t_f$ is film thickness, and $R$, $R_0$ are the substrate radius of curvature after and before film deposition, respectively.

This technique is widely used precisely because it is non-destructive and relatively simple to implement (measuring wafer bow via optical or capacitive curvature-sensing tools before and after deposition), avoiding the need for direct mechanical testing of the (often very thin and mechanically fragile) film itself.

### Consequences of Excessive Film Stress

**Key Points**

- **Wafer bowing**: Sufficiently high film stress, especially on thin substrates or with thick films, can bow the wafer enough to interfere with subsequent lithography (focus/alignment issues on steppers/scanners) or wafer handling in automated equipment.
- **Film cracking**: Excessive tensile stress, if it exceeds the film's fracture strength, can cause cracking, particularly problematic in brittle dielectric films.
- **Delamination**: Excessive stress (either tensile or compressive) can exceed the adhesive strength of the film-substrate (or film-film) interface, causing the film to separate/peel, discussed further below in the context of adhesion.
- **Stress-induced voiding**: In metal interconnect lines, particularly narrow copper or aluminum lines under significant thermal or intrinsic stress, stress can drive vacancy migration and void formation within the metal line over time — a distinct reliability mechanism (stress migration) from electromigration, though both are stress/mass-transport-related interconnect failure mechanisms.

### Adhesion Fundamentals

**Key Points**

Adhesion describes the strength of the interfacial bond holding a deposited film to its underlying surface. Strong adhesion generally requires:

- **Chemical bonding at the interface**: Formation of actual chemical bonds (rather than purely weak physical/van der Waals attraction) between film and substrate atoms at the interface, often achieved through interfacial reaction, interdiffusion, or the use of a dedicated adhesion-promoting layer.
- **Mechanical interlocking**: Surface roughness at the atomic-to-nanometer scale can provide additional mechanical interlocking between film and substrate, contributing to adhesion strength beyond pure chemical bonding alone.
- **Absence of interfacial contamination**: Any contamination layer (native oxide, adsorbed organic residue, particulates) present at the substrate surface before deposition can act as a weak interfacial layer, dramatically reducing effective adhesion regardless of the intrinsic bonding capability of the film material itself — making substrate surface preparation (cleaning, pre-deposition surface treatment) a critical practical determinant of adhesion in real processes.

### Adhesion Layers

**Key Points**

Many important metal-on-dielectric (or metal-on-metal) interfaces in semiconductor processing exhibit intrinsically poor adhesion between the desired functional material and the underlying surface, motivating the deliberate insertion of a thin adhesion-promoting layer:

- **Titanium (Ti) or Chromium (Cr) adhesion layers**: Commonly used beneath gold or other noble metal films (which otherwise adhere poorly to oxide/dielectric surfaces due to their chemical inertness), since Ti/Cr readily forms strong chemical bonds (often through interfacial oxide formation) with the underlying dielectric while also alloying/bonding well with the subsequently deposited noble metal.
- **Titanium/Titanium Nitride (Ti/TiN) stacks**: Widely used in interconnect and contact metallization both for adhesion promotion and as a diffusion barrier, serving a dual role in modern interconnect stacks.
- The choice and thickness of adhesion layer material is a well-established area of process engineering specific to the particular film-substrate material pair in question. [Inference: specific adhesion layer material and thickness recommendations vary by the exact process integration scheme and should be verified against established process specifications for a given technology rather than generalized.]

### Adhesion Testing Methods

**Key Points**

- **Tape test (peel test)**: A qualitative/semi-quantitative test in which adhesive tape is applied to and then peeled from the film surface (often following a scribed cross-hatch pattern through the film per standardized test methods such as ASTM D3359), with the fraction of film removed by the tape indicating relative adhesion quality — simple and widely used for rapid qualitative screening, though it provides only limited quantitative discrimination between moderately-to-well-adhered films.
- **Scratch testing**: A stylus of controlled, increasing load is drawn across the film surface, and the critical load at which film delamination/failure is observed (detected via acoustic emission, friction force changes, or microscopic inspection) provides a semi-quantitative adhesion strength metric.
- **Pull-off (stud pull) testing**: A stud is bonded to the film surface with adhesive, and the force required to pull the stud (and attached film) away from the substrate is measured directly, providing a more quantitative adhesion strength value in units of force per unit area, though sample preparation and adhesive bonding introduce their own experimental variability.
- **Four-point bend testing**: Used particularly for measuring interfacial fracture energy/toughness of buried interfaces (relevant for multilayer interconnect stack reliability assessment), providing a more rigorous fracture-mechanics-based quantitative adhesion metric than simpler peel or scratch tests.

[Inference: the specific choice of adhesion test method and acceptance criteria depends on the particular application, film system, and reliability requirements, and should follow established relevant industry standards (e.g., ASTM methods) rather than a single universally applicable test.]

### Stress and Adhesion Interaction

**Key Points**

Stress and adhesion are not independent properties — high film stress directly increases the driving force for delamination at a given interface, since the stored elastic strain energy in a stressed film provides thermodynamic driving force for interfacial crack propagation once a critical flaw or edge defect is present. This means:

- A film with excellent intrinsic adhesion but very high stress can still delaminate under sufficient stored strain energy, particularly at edges, corners, or pre-existing defects where stress concentration is highest.
- Conversely, even moderately stressed films can survive reliably if interfacial adhesion is sufficiently strong to resist the stress-driven delamination driving force.
- Process engineers therefore typically must jointly optimize both stress (via deposition condition tuning — temperature, pressure, plasma power, precursor chemistry) and adhesion (via surface preparation and adhesion layer engineering) rather than treating them as separable, independently solvable problems.

### Stress Engineering Techniques

**Key Points**

- **Deposition temperature adjustment**: Changing deposition temperature directly affects the thermal stress component (via $\Delta T$ in Stoney's-equation-related analysis) and can also affect intrinsic stress through its influence on film microstructure and growth kinetics.
- **Plasma power/bias adjustment** (for PECVD/sputtering): Adjusting ion bombardment energy at the growing film surface can shift intrinsic stress between more tensile and more compressive character, since adatom peening/densification effects are directly tied to bombarding ion energy and flux.
- **Multilayer/stress-compensating stacks**: Deliberately alternating tensile and compressive layers within a multilayer stack can be used to achieve a desired net stress (including near-zero net stress) across the composite structure, a technique used in various interconnect and MEMS structural applications where precise net stress control is critical.
- **Post-deposition annealing**: Can relax certain intrinsic stress components (particularly those associated with non-equilibrium point defect concentrations or metastable microstructure) though it can also introduce additional thermal stress upon subsequent cooling, requiring careful net-effect evaluation for a given film/process combination.

### Worked Conceptual Example

**Example**

Consider a 500 nm LPCVD silicon nitride film, known to typically exhibit high intrinsic tensile stress (often cited in the range of roughly 1 GPa for stoichiometric LPCVD nitride), deposited on a standard silicon wafer. [Unverified: this specific stress magnitude is a commonly cited representative literature value for stoichiometric LPCVD silicon nitride; actual stress for a specific deposition tool and recipe should be confirmed via direct wafer curvature measurement rather than assumed from a general literature figure.]

Such a highly tensile film, if deposited as a blanket layer over a sufficiently large area without any patterning or stress-relief features, could produce measurable wafer bow, and — if the film's fracture strength is exceeded locally (e.g., at a sharp underlying topographic step or pre-existing substrate defect) — could crack rather than simply bow uniformly. This is a well-recognized general reliability consideration in LPCVD nitride process integration, which has historically motivated the use of lower-stress nitride variants (e.g., silicon-rich, non-stoichiometric LPCVD nitride, which can achieve significantly reduced tensile stress at some cost to other film properties like wet-etch resistance) for applications where the standard stoichiometric film's stress level would pose an unacceptable reliability risk. [Inference: the specific trade-off magnitude between stress reduction and other properties (etch resistance, dielectric constant, density) for silicon-rich nitride variants is process-recipe-specific and should be evaluated against the specific application's requirements.]

### Related Topics

- Film nucleation and step coverage (intrinsic stress origins during growth)
- Chemical vapor deposition variants (LPCVD/PECVD stress characteristics)
- Electromigration and stress migration in interconnects
- Wafer bow and warpage metrology
- MEMS structural film stress engineering
- Adhesion layer materials in interconnect metallization
- Chemical-mechanical planarization (CMP) and its interaction with underlying film stress