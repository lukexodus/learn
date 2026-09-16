## Chemical Fundamentals for Environmental Systems


### Conceptual Framework

Environmental chemistry applies core chemical principles — atomic structure, bonding, thermodynamics, kinetics, and equilibrium — to understand the behavior, transport, and transformation of substances in air, water, and soil systems. This foundational chapter establishes the chemical toolkit used throughout environmental science: interpreting pollutant fate, biogeochemical cycling, and reaction pathways in natural and engineered systems.

### Atomic Structure and Periodicity Relevant to Environmental Chemistry

**Key Points**

- **Electron configuration** determines an element's reactivity and bonding behavior, governing whether it forms ionic, covalent, or metallic bonds relevant to environmental speciation
- **Electronegativity trends** (increasing across periods, decreasing down groups) predict bond polarity, which governs solubility behavior and reactivity of environmental contaminants
- **Redox-active elements** (Fe, Mn, S, N) exhibit multiple oxidation states of direct environmental significance — e.g., Fe²⁺/Fe³⁺ cycling in wetland soils, Mn²⁺/Mn⁴⁺ in sediment diagenesis, and the nitrogen oxidation states spanning $NH_4^+$ (-3) to $NO_3^-$ (+5)
- **Isotopes and radioactivity**: Stable isotope ratios (e.g., $\delta^{18}O$, $\delta^{13}C$) serve as tracers for water source, biological processes, and pollutant origin tracking; radioactive isotopes are relevant to both natural background radiation and anthropogenic contamination assessment

### Chemical Bonding and Molecular Structure

**Ionic bonding** governs behavior of dissolved salts in aqueous environmental systems (e.g., $Na^+$, $Cl^-$, $Ca^{2+}$, $SO_4^{2-}$), controlling solubility, ionic strength, and electrical conductivity of natural waters.

**Covalent bonding** underlies the structure of organic pollutants, greenhouse gases, and biomolecules. Bond polarity (determined by electronegativity difference) directly influences:

- **Solubility**: Polar covalent molecules (e.g., ethanol) tend toward water solubility; nonpolar molecules (e.g., many hydrocarbons) tend toward hydrophobicity and partitioning into organic matter or lipids
- **Volatility**: Molecular polarity and intermolecular forces (hydrogen bonding, van der Waals forces) influence vapor pressure and thus atmospheric partitioning behavior

**Hydrogen bonding** is of particular environmental significance due to water's unique properties (high boiling point relative to molecular weight, high heat capacity, high surface tension), all of which underpin water's role as Earth's dominant environmental solvent and thermal buffer.

### Thermodynamics in Environmental Systems

**Gibbs free energy** determines reaction spontaneity:

$$\Delta G = \Delta H - T\Delta S$$

A reaction proceeds spontaneously (under constant temperature and pressure) when $\Delta G < 0$. This principle underlies prediction of which environmental reactions (mineral weathering, organic matter decomposition, redox transformations) will proceed under given conditions, though [Inference] thermodynamic favorability does not guarantee observable reaction rate — kinetic barriers frequently prevent thermodynamically favorable reactions from proceeding at environmentally relevant timescales without catalysis (often microbially mediated in natural systems).

**Enthalpy and environmental energy balance**

Enthalpy changes ($\Delta H$) associated with phase transitions (evaporation, condensation, freezing) underlie the energy dynamics of the hydrologic cycle and atmospheric heat transport.

**Entropy considerations**

The second law of thermodynamics ($\Delta S_{universe} \geq 0$) underlies the natural tendency toward dispersal of pollutants and energy degradation, relevant to understanding why concentrated contamination sources tend toward dilution/dispersion absent containment.

### Chemical Kinetics

Reaction rate for a simple elementary reaction is expressed as:

$$\text{Rate} = k[A]^m[B]^n$$

where $k$ is the rate constant, and $m$, $n$ are reaction orders determined empirically (not necessarily equal to stoichiometric coefficients for non-elementary reactions).

**Environmental relevance of kinetics**

- **Pollutant degradation rates**: Often modeled as first-order decay, $C_t = C_0 e^{-kt}$, used to estimate half-lives ($t_{1/2} = \ln(2)/k$) of contaminants in soil, water, and air
- **Temperature dependence**: The Arrhenius equation, $k = Ae^{-E_a/RT}$, describes how reaction rates (including biodegradation and chemical weathering rates) increase with temperature, relevant to climate change impacts on contaminant persistence and biogeochemical cycling rates
- **Catalysis**: Enzymatic catalysis by microorganisms substantially accelerates otherwise kinetically limited environmental reactions (e.g., nitrification, sulfate reduction), often by many orders of magnitude relative to abiotic rates

### Chemical Equilibrium

For a generic reversible reaction $aA + bB \rightleftharpoons cC + dD$, the equilibrium constant is:

$$K_{eq} = \frac{[C]^c[D]^d}{[A]^a[B]^b}$$

**Environmental applications of equilibrium concepts**

- **Solubility product ($K_{sp}$)**: Governs precipitation/dissolution of mineral phases controlling metal ion concentrations in natural waters (e.g., carbonate mineral equilibria controlling water hardness and buffering capacity)
- **Acid-base equilibria ($K_a$, $K_b$)**: Governs speciation of weak acids/bases in environmental systems (e.g., carbonic acid system controlling ocean and freshwater pH buffering)
- **Distribution/partition coefficients ($K_d$, $K_{ow}$)**: Describe equilibrium partitioning of contaminants between phases (soil-water, octanol-water as a proxy for lipid-water), central to predicting bioaccumulation potential and environmental mobility
- **Le Chatelier's Principle**: Predicts directional shift of equilibrium systems in response to perturbation (concentration, temperature, pressure changes), applied to understanding buffering responses in natural water and atmospheric systems

### Acid-Base Chemistry

$$pH = -\log_{10}[H^+]$$

pH governs speciation of numerous environmentally relevant compounds (metal solubility, ammonia/ammonium equilibrium, nutrient bioavailability) and is a primary parameter in water quality assessment.

**Buffering systems**

Natural water buffering, particularly the carbonate-bicarbonate-carbonic acid system, resists pH change upon addition of acids or bases:

$$CO_2 + H_2O \rightleftharpoons H_2CO_3 \rightleftharpoons H^+ + HCO_3^- \rightleftharpoons 2H^+ + CO_3^{2-}$$

This system underlies both freshwater alkalinity buffering and the ocean's capacity to absorb atmospheric $CO_2$, with the latter's declining buffering efficiency under sustained $CO_2$ loading being the chemical basis of **ocean acidification**.

**Acid rain chemistry**

Atmospheric $SO_2$ and $NO_x$ emissions undergo oxidation and hydrolysis to form sulfuric and nitric acid:

$$SO_2 + \tfrac{1}{2}O_2 \rightarrow SO_3 \quad ; \quad SO_3 + H_2O \rightarrow H_2SO_4$$



$$2NO_2 + H_2O \rightarrow HNO_3 + HNO_2$$

These strong acids lower precipitation pH below the natural baseline (~5.6, itself set by equilibrium with atmospheric $CO_2$), driving soil and freshwater acidification impacts.

### Oxidation-Reduction (Redox) Chemistry

Redox reactions involve electron transfer, quantified by **redox potential ($E_h$)**, measured relative to the standard hydrogen electrode. Environmental redox sequences (in order of declining energy yield, and thus the order in which they are thermodynamically favored as electron acceptors become depleted) proceed approximately as:

$$O_2 \text{ reduction} > NO_3^- \text{ reduction} > Mn^{4+} \text{ reduction} > Fe^{3+} \text{ reduction} > SO_4^{2-} \text{ reduction} > CO_2 \text{ reduction (methanogenesis)}$$

This sequence explains vertical zonation of redox processes in stratified environments such as lake sediments, wetland soils, and groundwater aquifers, and underlies the biogeochemistry of nutrient cycling (denitrification, sulfate reduction) and contaminant mobility (e.g., arsenic mobilization under reducing conditions via Fe-oxide reductive dissolution).

### Organic Chemistry Fundamentals for Environmental Contaminants

**Key Points**

- **Functional groups** (hydroxyl, carboxyl, amine, halogen substituents) determine reactivity, polarity, and persistence of organic pollutants
- **Persistent Organic Pollutants (POPs)**: Characterized by high chemical stability, low water solubility, high lipid solubility, and resistance to biodegradation, leading to bioaccumulation and biomagnification through food webs
- **Halogenated organics** (e.g., organochlorine pesticides, PCBs, PFAS): Carbon-halogen bonds confer chemical stability and environmental persistence, a structural basis for these compounds' long environmental half-lives
- **Biodegradability factors**: Molecular branching, halogenation, and ring structure complexity generally reduce microbial degradation rates, while linear structures and common functional groups (esters, simple alcohols) are typically more readily biodegraded

### Reaction Stoichiometry and Mass Balance

Environmental systems analysis relies fundamentally on mass balance accounting:

$$\text{Accumulation} = \text{Inputs} - \text{Outputs} + \text{Generation} - \text{Consumption}$$

This framework underlies pollutant fate and transport modeling, nutrient budget calculations (e.g., watershed nitrogen budgets), and biogeochemical cycle quantification, forming a conceptual bridge between chemical fundamentals and systems-level environmental analysis covered elsewhere in the curriculum.

### Concentration Units and Conversions in Environmental Chemistry

Environmental chemistry employs several concentration conventions, each suited to different contexts:

- **Molarity ($mol/L$)**: Standard for equilibrium and kinetic calculations
- **Parts per million/billion (ppm, ppb)**: Common in air quality and trace contaminant reporting; for dilute aqueous solutions, $1\ ppm \approx 1\ mg/L$ (an approximation valid when solution density is close to $1\ g/mL$)
- **Mass concentration ($mg/L$, $\mu g/m^3$)**: Standard in regulatory water and air quality standards

Conversion between molar and mass-based units requires molecular weight:

$$C_{mg/L} = C_{mol/L} \times MW_{g/mol} \times 1000$$

### Foundational Concepts Diagram: Chemical Principles Feeding Environmental Processes (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 340">
<text x="320" y="24" text-anchor="middle" font-size="15" font-weight="bold" fill="#222">Chemical Fundamentals to Environmental Processes (svg_diagram)</text>
<rect x="20" y="50" width="140" height="50" fill="#a8d5a2" stroke="#333" />
<text x="90" y="80" text-anchor="middle" font-size="11" fill="#222">Thermodynamics</text>
<rect x="180" y="50" width="140" height="50" fill="#a2c4d5" stroke="#333" />
<text x="250" y="80" text-anchor="middle" font-size="11" fill="#222">Kinetics</text>
<rect x="340" y="50" width="140" height="50" fill="#d5c9a2" stroke="#333" />
<text x="410" y="80" text-anchor="middle" font-size="11" fill="#222">Equilibrium</text>
<rect x="500" y="50" width="120" height="50" fill="#e4b5c9" stroke="#333" />
<text x="560" y="80" text-anchor="middle" font-size="11" fill="#222">Redox</text>
<line x1="90" y1="100" x2="320" y2="170" stroke="#666" stroke-width="1.5" />
<line x1="250" y1="100" x2="320" y2="170" stroke="#666" stroke-width="1.5" />
<line x1="410" y1="100" x2="320" y2="170" stroke="#666" stroke-width="1.5" />
<line x1="560" y1="100" x2="320" y2="170" stroke="#666" stroke-width="1.5" />
<rect x="200" y="170" width="240" height="50" fill="#e8b566" stroke="#333" />
<text x="320" y="200" text-anchor="middle" font-size="12" fill="#222">Contaminant Fate and Transport</text>
<line x1="320" y1="220" x2="320" y2="260" stroke="#666" stroke-width="1.5" />
<rect x="140" y="260" width="140" height="50" fill="#c9b5e4" stroke="#333" />
<text x="210" y="290" text-anchor="middle" font-size="11" fill="#222">Water Quality</text>
<rect x="360" y="260" width="140" height="50" fill="#b5e4c9" stroke="#333" />
<text x="430" y="290" text-anchor="middle" font-size="11" fill="#222">Atmospheric Chemistry</text>
</svg>

### Common Misconceptions

**Key Points**

- Thermodynamic spontaneity ($\Delta G < 0$) does not imply a reaction occurs rapidly; kinetics, not thermodynamics, determines observed reaction rate
- pH and acidity are not synonymous with "harmful" — pH is a measure of hydrogen ion activity, and both high and low extremes, as well as deviation from an ecosystem's natural baseline, determine ecological impact
- Persistent Organic Pollutants are not defined solely by toxicity; persistence, bioaccumulation potential, and long-range transport capacity are the defining structural/chemical criteria, independent of acute toxicity level

### Conclusion

A working foundation in atomic structure, bonding, thermodynamics, kinetics, equilibrium, and redox chemistry provides the essential analytical toolkit for interpreting environmental chemical processes, from pollutant fate and transport to biogeochemical cycling. These principles recur throughout environmental chemistry as the mechanistic basis explaining observed patterns in water quality, atmospheric composition, and soil chemistry.

**Related Topics**

- Biogeochemical cycles (carbon, nitrogen, phosphorus, sulfur)
- Water quality parameters and pollutant fate/transport modeling
- Atmospheric chemistry and air pollution formation mechanisms
- Ocean acidification chemistry
- Persistent Organic Pollutants (POPs) and bioaccumulation
- Acid rain formation and ecosystem impacts
- Redox zonation in soils, sediments, and groundwater
- Analytical methods in environmental chemistry (spectroscopy, chromatography)