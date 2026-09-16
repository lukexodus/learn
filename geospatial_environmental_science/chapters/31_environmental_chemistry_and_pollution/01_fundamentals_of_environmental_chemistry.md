## Fundamentals of Environmental Chemistry


### Definition and Scope

Environmental chemistry is the study of the chemical processes occurring in air, water, soil, and living systems, and how anthropogenic and natural inputs alter these processes. It applies core chemical principles—thermodynamics, kinetics, equilibrium, and reaction mechanisms—to understand the sources, transport, transformation, and fate of substances in the environment, forming the scientific foundation for pollution assessment, remediation, and environmental policy.

### Core Chemical Principles Applied to the Environment

**Chemical Equilibrium in Natural Systems**

Environmental systems are rarely at true thermodynamic equilibrium but are often usefully approximated as such over relevant timescales. Equilibrium constants describe the partitioning of substances between phases and species:

$$K_{eq} = \frac{[\text{products}]}{[\text{reactants}]}$$

Key environmental equilibria include acid-base speciation, mineral solubility (solubility product, $K_{sp}$), and gas-liquid partitioning (Henry's Law).

**Henry's Law and Air-Water Partitioning**

Henry's Law describes the equilibrium partitioning of a volatile compound between the gas phase and aqueous solution:

$$C_g = K_H \, C_{aq}$$

or in dimensionless form:

$$K_H' = \frac{C_g}{C_{aq}}$$

where $K_H$ is the Henry's Law constant (units vary by convention, e.g., atm·m³/mol). Compounds with high $K_H$ (e.g., many chlorinated solvents) volatilize readily from water, an important consideration for groundwater remediation and air-water exchange of pollutants.

**Acid-Base Chemistry and pH**

pH governs speciation of countless environmental contaminants and nutrients. The relationship is defined as:

$$\text{pH} = -\log_{10}[\text{H}^+]$$

**Carbonate System**: The carbonate equilibrium system buffers natural water pH and is central to ocean acidification chemistry:

$$\text{CO}_2(g) \rightleftharpoons \text{CO}_2(aq) + \text{H}_2\text{O} \rightleftharpoons \text{H}_2\text{CO}_3 \rightleftharpoons \text{H}^+ + \text{HCO}_3^- \rightleftharpoons 2\text{H}^+ + \text{CO}_3^{2-}$$

Increasing atmospheric $\text{CO}_2$ shifts this equilibrium, lowering ocean pH and reducing carbonate ion availability, which impairs calcification in marine organisms (shellfish, corals). [Inference: ecological impact magnitude is species- and region-dependent]

**Redox Chemistry**

Reduction-oxidation reactions govern the fate of metals, nutrients, and many organic contaminants, especially in soils, sediments, and groundwater. Redox conditions are characterized by the redox potential $E_h$ or the related parameter $pe$ (negative log of electron activity):

$$pe = \frac{E_h}{0.0592}$$ (at 25°C, in volts)

Environmental redox sequences follow a predictable thermodynamic hierarchy as an environment becomes progressively more reducing (e.g., in waterlogged soils or subsurface sediments): oxygen reduction, then nitrate reduction (denitrification), manganese reduction, iron reduction, sulfate reduction, and finally methanogenesis. This sequence reflects the order of decreasing free energy yield per electron transferred. [Inference: microbially mediated, actual sequence can vary with substrate availability and microbial community]

### Solubility and Mineral Equilibria

The solubility product governs the precipitation/dissolution of mineral phases, which is critical for understanding metal mobility and mineral scaling:

$$K_{sp} = [\text{M}^{n+}]^a[\text{X}^{m-}]^b$$

For example, for calcite: $\text{CaCO}_3 \rightleftharpoons \text{Ca}^{2+} + \text{CO}_3^{2-}$, with $K_{sp} \approx 3.3 \times 10^{-9}$ at 25°C. [Unverified: exact value varies with temperature, ionic strength, and polymorph]

**Saturation Index**: Used to predict whether water is undersaturated, saturated, or supersaturated with respect to a mineral phase:

$$SI = \log_{10}\left(\frac{IAP}{K_{sp}}\right)$$

where $IAP$ is the ion activity product. $SI < 0$ indicates undersaturation (dissolution favored); $SI > 0$ indicates supersaturation (precipitation favored).

### Sorption and Partitioning Processes

**Organic Carbon Partitioning**

Hydrophobic organic contaminants partition between water and organic matter in soil/sediment, described by the organic carbon-water partition coefficient:

$$K_{oc} = \frac{C_{sorbed,oc}}{C_{aq}}$$

$K_{oc}$ correlates strongly with the octanol-water partition coefficient $K_{ow}$ (or its log form $\log K_{ow}$), a standard measure of a compound's hydrophobicity, via empirical linear free-energy relationships such as:

$$\log K_{oc} = a \log K_{ow} + b$$

where $a$ and $b$ are compound-class-specific regression coefficients. [Inference: coefficients vary substantially by chemical class]

**Sorption Isotherms**

- **Linear isotherm**: $C_s = K_d C_{aq}$, where $K_d$ is the distribution coefficient; valid at low concentrations.
- **Freundlich isotherm**: $C_s = K_f C_{aq}^{1/n}$, an empirical nonlinear relationship widely used for heterogeneous sorbent surfaces.
- **Langmuir isotherm**: $C_s = \dfrac{Q_{max} K_L C_{aq}}{1 + K_L C_{aq}}$, derived from an assumption of finite, homogeneous sorption sites reaching saturation ($Q_{max}$).

### Reaction Kinetics in Environmental Systems

Environmental transformation reactions (biodegradation, hydrolysis, photolysis) are commonly modeled using first-order kinetics for a given contaminant concentration $C$:

$$\frac{dC}{dt} = -kC \quad \Rightarrow \quad C_t = C_0 e^{-kt}$$

The half-life is derived as:

$$t_{1/2} = \frac{\ln 2}{k} \approx \frac{0.693}{k}$$

First-order approximation is widely used for regulatory and screening purposes, though actual degradation kinetics may follow more complex forms (e.g., Monod kinetics for microbially mediated processes at high concentrations, or biphasic kinetics reflecting multiple sorption/degradation compartments). [Inference: model choice depends on concentration range and system complexity]

**Arrhenius Temperature Dependence**

Reaction rate constants generally increase with temperature following the Arrhenius equation:

$$k = A \, e^{-E_a/RT}$$

where $E_a$ is activation energy, $R$ is the gas constant, and $T$ is absolute temperature. This underlies observed seasonal variation in contaminant degradation and biogeochemical cycling rates.

### Photochemistry

**Direct and Indirect Photolysis**

- **Direct photolysis**: A molecule directly absorbs light and undergoes transformation.
- **Indirect (sensitized) photolysis**: Light is absorbed by a separate chromophore (e.g., dissolved organic matter, nitrate), generating reactive intermediates—hydroxyl radicals ($\cdot\text{OH}$), singlet oxygen ($^1\text{O}_2$), or other reactive oxygen species—that subsequently react with the target compound.

**Tropospheric Photochemistry and Smog Formation**

Photolysis of nitrogen dioxide initiates the photochemical smog cycle:

$$\text{NO}_2 + h\nu \rightarrow \text{NO} + \text{O}$$



$$\text{O} + \text{O}_2 \rightarrow \text{O}_3$$

In the presence of volatile organic compounds (VOCs), this cycle is perturbed such that $\text{NO}$ is oxidized back to $\text{NO}_2$ by peroxy radicals rather than by $\text{O}_3$, allowing ground-level ozone to accumulate—the core mechanism of photochemical smog formation.

**Stratospheric Ozone Chemistry**

Stratospheric ozone is formed and destroyed in a natural catalytic cycle (Chapman cycle), but anthropogenic halogen compounds (chlorofluorocarbons, halons) catalytically destroy ozone via chlorine and bromine radical cycles:

$$\text{Cl} + \text{O}_3 \rightarrow \text{ClO} + \text{O}_2$$



$$\text{ClO} + \text{O} \rightarrow \text{Cl} + \text{O}_2$$

A single chlorine radical can destroy many thousands of ozone molecules before being sequestered into a reservoir species, which is the chemical basis for the Montreal Protocol's regulation of ozone-depleting substances.

### Biogeochemical Cycling

**Nutrient Cycles**

- **Nitrogen cycle**: Involves nitrogen fixation ($\text{N}_2 \rightarrow \text{NH}_3$), nitrification ($\text{NH}_4^+ \rightarrow \text{NO}_2^- \rightarrow \text{NO}_3^-$), denitrification ($\text{NO}_3^- \rightarrow \text{N}_2$), and assimilation, mediated largely by microbial processes.
- **Phosphorus cycle**: Lacks a significant atmospheric phase; dominated by weathering release, biological uptake, and sedimentary burial; a key limiting nutrient in many freshwater systems, driving eutrophication when anthropogenically enriched.
- **Carbon cycle**: Encompasses atmospheric $\text{CO}_2$ exchange, photosynthesis/respiration, ocean-atmosphere gas exchange, and long-term burial as fossil carbon or carbonate rock.
- **Sulfur cycle**: Includes natural volcanic/biogenic emissions and anthropogenic $\text{SO}_2$ emissions, oxidation to sulfate, and acid deposition.

### Environmental Chemical Measurement Concepts

**Concentration Units**

Common environmental concentration expressions include mg/L, µg/L, ppm, ppb, and mol/L, with conversions dependent on solution density (approximated as 1 for dilute aqueous solutions) and molar mass:

$$\text{ppm} \approx \text{mg/L (for dilute aqueous solutions, } \rho \approx 1 \text{ kg/L)}$$

For gases, ppm by volume relates to mass concentration via the ideal gas law and molar mass, requiring temperature and pressure correction.

**Analytical Detection Concepts**

- **Method Detection Limit (MDL)**: The minimum concentration that can be reliably distinguished from a blank with a defined statistical confidence.
- **Limit of Quantification (LOQ)**: The minimum concentration that can be quantified with acceptable precision, typically 3–5× the MDL. [Inference: exact multiplier varies by regulatory framework and laboratory protocol]

### Biogeochemical Cycle and Redox Sequence Diagram

```mermaid
flowchart TD
    A[Atmosphere: O2, CO2, N2, pollutant gases] <--> B[Hydrosphere: dissolved species, particulates]
    B <--> C[Pedosphere/Sediment: sorbed species, mineral phases]
    C <--> D[Biosphere: uptake, transformation, degradation]
    D <--> A

    subgraph RedoxLadder["Redox Sequence with Decreasing Eh"]
        E1[O2 Reduction] --> E2[NO3- Reduction/Denitrification]
        E2 --> E3[Mn(IV) Reduction]
        E3 --> E4[Fe(III) Reduction]
        E4 --> E5[SO4 2- Reduction]
        E5 --> E6[Methanogenesis]
    end

    C -.controls.-> RedoxLadder
```

### Worked Example

**Problem**: A groundwater sample has a measured concentration of trichloroethylene (TCE) of 500 µg/L at time zero. First-order biodegradation rate constant $k = 0.015 \, \text{day}^{-1}$. Calculate the concentration after 90 days and the half-life.

**Solution**:

$$C_t = C_0 e^{-kt} = 500 \times e^{-0.015 \times 90} = 500 \times e^{-1.35} \approx 500 \times 0.2592 \approx 129.6 \, \mu\text{g/L}$$



$$t_{1/2} = \frac{0.693}{0.015} \approx 46.2 \, \text{days}$$

This calculation assumes constant first-order kinetics under stable environmental conditions (temperature, microbial activity, redox state); actual field degradation rates commonly deviate from this idealized model due to changing subsurface conditions. [Inference]

### Applied Contexts

- **Water treatment chemistry**: Coagulation, chlorination, and advanced oxidation processes rely directly on acid-base, redox, and photochemical principles.
- **Contaminant fate and transport modeling**: $K_{oc}$, $K_H$, and degradation rate constants are core inputs to regulatory fate-and-transport models (e.g., EPA's BIOSCREEN, MODFLOW-coupled reactive transport codes).
- **Air quality regulation**: Photochemical smog and ozone depletion chemistry underlie regulatory frameworks such as the Clean Air Act and the Montreal Protocol.
- **Climate chemistry**: Carbonate equilibrium chemistry underlies ocean acidification monitoring and greenhouse gas budget accounting.
- **Site remediation design**: Redox zonation concepts guide engineered approaches such as permeable reactive barriers and enhanced bioremediation strategies.

### Key Points

- Environmental chemistry applies core physical chemistry principles (equilibrium, kinetics, thermodynamics) to explain the distribution and transformation of substances across air, water, soil, and biota.
- Partitioning coefficients ($K_H$, $K_{oc}$, $K_{ow}$, $K_d$) are the fundamental quantitative tools for predicting where a contaminant will reside and how mobile it will be.
- Redox chemistry, structured as a predictable thermodynamic sequence, governs the fate of metals, nutrients, and organic contaminants in soils and sediments.
- Photochemical reactions drive both tropospheric pollution (smog, ozone formation) and stratospheric ozone depletion through distinct but related radical mechanisms.
- First-order kinetics provides a standard, widely applicable approximation for contaminant degradation, though it is a simplification of more complex underlying processes.

**Related Topics**

- Water quality parameters and standards (BOD, COD, dissolved oxygen)
- Heavy metal speciation and bioavailability
- Persistent organic pollutants (POPs) and bioaccumulation
- Atmospheric chemistry and air pollutant formation mechanisms
- Soil chemistry and cation exchange capacity
- Environmental toxicology and dose-response relationships
- Remediation technologies (bioremediation, chemical oxidation, phytoremediation)
- Analytical methods in environmental chemistry (GC-MS, ICP-MS, spectrophotometry)
- Climate chemistry and greenhouse gas cycling
- Regulatory frameworks (Clean Water Act, Clean Air Act, REACH)