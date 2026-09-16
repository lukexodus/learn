## Transformer Losses, Efficiency, and Thermal Loading

### Overview

Transformer losses represent the energy dissipated as heat during power transformation, arising from distinct physical mechanisms in the core and windings. These losses determine transformer efficiency, drive thermal loading limits, and govern insulation life through cumulative thermal aging. Understanding loss components, efficiency calculation, and thermal behavior is essential for equipment specification, loading practices, and life-cycle cost evaluation.

### Categories of Transformer Losses

#### No-Load (Core) Losses

**Key Points**

- Occur whenever the transformer is energized, essentially independent of load current, since they result from the alternating magnetic flux in the core
- Comprise two components: hysteresis loss and eddy current loss
- Measured directly via the open-circuit (no-load) test, as referenced in Transformer Equivalent Circuits and Per-Unit Modeling
- Relatively constant in magnitude across the transformer's loading range, making them a fixed ("standing") loss whenever the unit is energized

**Hysteresis Loss**

Caused by the energy required to repeatedly reorient magnetic domains in the core material as the applied flux alternates direction. Steinmetz's empirical formula approximates this loss:

$$P_h = k_h \cdot f \cdot B_{max}^n$$

where $k_h$ is a material-dependent hysteresis constant, $f$ is frequency, $B_{max}$ is peak flux density, and $n$ (the Steinmetz exponent) is typically in the range of 1.6–2.0 depending on core material. [Unverified] The precise exponent value depends on the specific steel grade and is generally determined empirically by the core material manufacturer rather than assumed universally.

**Eddy Current Loss**

Caused by circulating currents induced within the core laminations themselves by the alternating flux, dissipated as $I^2R$ heating in the lamination material:

$$P_e = k_e \cdot f^2 \cdot B_{max}^2 \cdot t^2$$

where $t$ is lamination thickness. Because eddy current loss scales with the square of lamination thickness, cores are constructed from thin, insulated laminations (rather than solid steel) to suppress this loss component.

#### Load Losses (Copper Losses)

**Key Points**

- Vary with the square of load current, since they result from $I^2R$ heating in the winding conductors
- Measured via the short-circuit test, as referenced in Transformer Equivalent Circuits and Per-Unit Modeling
- Comprise DC resistance loss plus additional stray losses from eddy currents induced in the windings themselves and in structural metal parts (tank walls, clamping structures) by leakage flux

$$P_{load} = I^2 R_{eq} + P_{stray}$$

**Stray Losses**

**Key Points**

- Arise from leakage flux inducing eddy currents in winding conductors (increasing effective AC resistance above DC resistance, sometimes called the "skin effect" and "proximity effect" contribution) and in nearby structural metal components
- Become proportionally more significant in larger transformers and in windings using large-cross-section conductors, motivating the use of transposed or stranded conductors to mitigate circulating current losses within parallel strands
- [Unverified] The relative magnitude of stray losses compared to DC $I^2R$ loss varies considerably with transformer design, size, and conductor construction

### Total Loss and the Loss Curve

**Key Points**

- Total transformer loss at any given loading is the sum of the (essentially constant) no-load loss and the (load-dependent) load loss
- Total loss varies parabolically with load, since load loss scales with the square of per-unit loading $L$:

$$P_{total}(L) = P_{no-load} + L^2 \cdot P_{load,rated}$$

where $L = S_{actual}/S_{rated}$ is the per-unit loading fraction.

### Efficiency Calculation

Transformer efficiency is the ratio of output power to input power, or equivalently, output power divided by output power plus losses:

$$\eta = \frac{P_{out}}{P_{in}} = \frac{P_{out}}{P_{out} + P_{no-load} + L^2 P_{load,rated}}$$

#### Maximum Efficiency Condition

**Key Points**

- Efficiency is maximized at the loading level where no-load loss equals load loss — a classical result derived by differentiating the efficiency expression with respect to loading and setting the derivative to zero
- This occurs at per-unit loading:

$$L_{max\,\eta} = \sqrt{\frac{P_{no-load}}{P_{load,rated}}}$$

**Example**

A transformer with rated load loss of 100 kW and no-load loss of 25 kW reaches maximum efficiency at $L = \sqrt{25/100} = 0.5$, i.e., at 50% of rated load. [Illustrative numeric example; actual optimal loading point depends on the specific unit's measured loss values from factory test reports.]

Since power transformers rarely operate continuously at a single fixed load, "all-day efficiency" (energy-weighted efficiency over a typical daily load cycle) is sometimes used as a more representative metric than efficiency at a single loading point, particularly for distribution transformers with cyclical daily load profiles.

$$\eta_{all-day} = \frac{\sum \text{Energy Output (kWh)}}{\sum \text{Energy Output} + \sum \text{Losses (kWh)}}$$

### Thermal Loading and Temperature Rise

#### Insulation Class and Temperature Limits

**Key Points**

- Transformer insulation systems are rated by thermal class (e.g., Class A, Class F, Class H in older terminology, or by specific hot-spot temperature limits in modern standards), defining the maximum continuous operating temperature the insulation can withstand for its rated life
- Standard mineral-oil-filled power transformers are commonly designed for a 65°C average winding temperature rise above a specified ambient reference (historically also 55°C rise designs existed), with a hot-spot temperature typically some margin above the average rise value
- [Unverified] Specific rise values and reference ambient temperatures are governed by the applicable design standard (e.g., IEEE C57.12.00, IEC 60076) and can vary by transformer class and regional practice

#### Hot-Spot Temperature

**Key Points**

- The hot-spot is the highest temperature point within the winding, typically located near the top of the winding where heated oil accumulates and local flux/current concentration may be highest
- Hot-spot temperature, rather than average winding temperature, is the primary driver of insulation aging, since thermal degradation reactions accelerate strongly with the highest local temperature
- Hot-spot temperature is generally estimated (via thermal models or embedded fiber-optic sensors in modern installations) rather than directly measured by simple methods, since it occurs at an inaccessible internal location

### Thermal Aging and the Arrhenius Relationship

**Key Points**

- Cellulose-based insulation (paper, pressboard) degrades chemically over time, with the rate of degradation approximately following an Arrhenius-type relationship — the rate of thermally driven chemical reactions increases exponentially with temperature
- A widely referenced rule of thumb (derived from IEEE loading guide relationships) suggests that insulation life is approximately halved for every 6–8°C increase in hot-spot temperature above the rated reference value, though this is a simplified approximation of a more complex underlying equation
- [Unverified] The precise "halving temperature" and underlying aging acceleration factor equation vary between standards (e.g., IEEE C57.91 uses a specific aging acceleration factor formula) and should be taken from the applicable loading guide rather than assumed as a universal fixed number

$$F_{AA} = \exp\left(\frac{15000}{383} - \frac{15000}{\theta_H + 273}\right)$$

where $F_{AA}$ is the aging acceleration factor and $\theta_H$ is hot-spot temperature in °C, per the commonly cited IEEE C57.91 relationship for 65°C-rise insulation systems. [Unverified — this specific constant set applies to a particular insulation reference system per IEEE C57.91; different insulation systems or standard editions may specify different constants.]

### Loss vs. Loading Diagram (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 380">
<text x="320" y="20" text-anchor="middle" font-size="14" font-weight="bold">Transformer Losses and Efficiency vs. Loading (svg_diagram)</text>
<line x1="70" y1="320" x2="580" y2="320" stroke="black" stroke-width="1.5" />
<line x1="70" y1="320" x2="70" y2="40" stroke="black" stroke-width="1.5" />
<text x="580" y="340" font-size="12">Load (pu)</text>
<text x="20" y="45" font-size="12">Loss (kW)</text>
<line x1="70" y1="280" x2="580" y2="280" stroke="#1a5276" stroke-width="2.5" />
<text x="460" y="270" font-size="11" fill="#1a5276">No-Load Loss (constant)</text>
<path d="M 70 320 Q 300 320 450 200 T 580 60" fill="none" stroke="#c0392b" stroke-width="2.5" />
<text x="380" y="150" font-size="11" fill="#c0392b">Load Loss (I^2 scaling)</text>
<path d="M 70 280 Q 300 260 450 130 T 580 45" fill="none" stroke="#117864" stroke-width="2" stroke-dasharray="4,3" />
<text x="330" y="100" font-size="11" fill="#117864">Total Loss</text>
<line x1="300" y1="320" x2="300" y2="40" stroke="gray" stroke-dasharray="2,3" />
<text x="240" y="335" font-size="11">Max Efficiency Point</text>
</svg>

### Cooling Classes and Thermal Rating

**Key Points**

- Cooling method designations (per IEC 60076-2 / IEEE standards) indicate the internal cooling medium, circulation method, external cooling medium, and external circulation method — e.g., ONAN (Oil Natural, Air Natural), ONAF (Oil Natural, Air Forced), OFAF (Oil Forced, Air Forced), ODAF (Oil Directed, Air Forced)
- Multiple cooling stages allow a single transformer nameplate to specify different MVA ratings at each cooling stage (e.g., ONAN/ONAF/ONAF2 ratings), with fans and pumps activated as load and temperature increase
- Higher cooling stages (with forced air/oil circulation) allow higher continuous MVA ratings from the same core/winding assembly by improving heat dissipation efficiency, though core and load losses at a given loading remain governed by the same underlying loss curve

### Emergency and Short-Term Overload Loading

**Key Points**

- Loading guides (e.g., IEEE C57.91, IEC 60076-7) provide methodology for calculating permissible short-term and long-term emergency overload capability beyond nameplate rating, trading accelerated insulation aging against operational flexibility
- Overload capability depends on pre-loading history, ambient temperature, and the transformer's thermal time constant (larger units generally have longer thermal time constants, providing more thermal "inertia" against rapid overload-driven temperature rise)
- [Inference] Overload loading practices are generally applied as planned/emergency contingency measures rather than routine operation, given the associated accelerated insulation aging — specific utility practices and risk tolerances vary

### Loss Evaluation in Procurement

**Key Points**

- Utilities commonly apply capitalized loss evaluation factors ($/kW for no-load loss and $/kW for load loss) when comparing competing transformer bids, converting lifetime energy loss cost into an equivalent upfront capital cost for fair bid comparison
- Because no-load losses are incurred continuously (24/7) regardless of loading, while load losses vary with the (often lower, time-averaged) actual loading, the capitalized $/kW rate for no-load loss is typically higher than for load loss in most loss evaluation methodologies
- [Unverified] Specific evaluation factors are utility- and procurement-specific financial parameters, not standardized engineering constants

### Related Topics

- Transformer Equivalent Circuits and Per-Unit Modeling
- Cooling classes and forced cooling system design (ONAN, ONAF, OFAF, ODAF)
- Dissolved gas analysis (DGA) and transformer condition monitoring
- IEEE C57.91 / IEC 60076-7 loading guides and overload methodology
- Insulation aging mechanisms and moisture/oxygen effects on cellulose degradation
- Hot-spot temperature estimation methods and fiber-optic sensor monitoring
- Core material selection (grain-oriented silicon steel, amorphous metal cores) and loss reduction
- Life-cycle cost analysis and capitalized loss evaluation in transformer procurement