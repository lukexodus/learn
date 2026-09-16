## Units and Conversions Across Energy Carriers


### Overview

Energy economics requires working across a heterogeneous set of energy carriers — crude oil, natural gas, coal, electricity, biomass, and refined products — each historically measured in units native to its industry (barrels, cubic meters, tonnes, kilowatt-hours). Because these carriers are traded, compared, aggregated, and substituted for one another in economic analysis, a robust understanding of unit systems and conversion methodology is a foundational technical skill.

### Fundamental Energy Units

#### SI Base Unit

The International System of Units (SI) defines energy in **joules (J)**, derived as $1\text{ J} = 1\text{ kg} \cdot \text{m}^2/\text{s}^2$. In practice, the joule is too small for macro-level energy analysis, so larger multiples are used:

| Unit | Symbol | Joules |
| --- | --- | --- |
| Kilojoule | kJ | $10^3$ J |
| Megajoule | MJ | $10^6$ J |
| Gigajoule | GJ | $10^9$ J |
| Terajoule | TJ | $10^{12}$ J |
| Petajoule | PJ | $10^{15}$ J |
| Exajoule | EJ | $10^{18}$ J |

National and global energy balances (e.g., total primary energy supply) are typically reported in EJ or PJ.

#### British Thermal Unit (BTU)

Common in North American energy statistics, particularly for natural gas and heating applications:

$$1 \text{ BTU} \approx 1{,}055 \text{ J}$$

Aggregated forms include the **quad** (quadrillion BTU, $10^{15}$ BTU), used in U.S. national energy statistics.

$$1 \text{ quad} \approx 1.055 \text{ EJ}$$

#### Kilowatt-hour (kWh)

The standard unit for electricity metering and billing:

$$1 \text{ kWh} = 3.6 \times 10^6 \text{ J} = 3.6 \text{ MJ}$$

Larger multiples — MWh, GWh, TWh — are used for utility-scale generation and national electricity consumption statistics.

#### Tonne of Oil Equivalent (toe) and Barrel of Oil Equivalent (boe)

These are the standard aggregation units in international energy statistics (used by the IEA, BP Statistical Review, and OPEC), representing the approximate energy content of one tonne or one barrel of crude oil:

$$1 \text{ toe} \approx 41.87 \text{ GJ} \approx 11{,}630 \text{ kWh}$$



$$1 \text{ boe} \approx 6.12 \text{ GJ} \approx 1{,}700 \text{ kWh}$$

[Unverified] Precise toe and boe conversion factors vary slightly by source institution (IEA vs. BP vs. EIA) due to differing assumptions about average crude oil calorific value; analysts should always confirm which convention a dataset uses before combining figures from multiple sources.

### Native Units by Carrier

| Carrier | Native Unit | Approximate Energy Content |
| --- | --- | --- |
| Crude oil | Barrel (bbl) | ~5.8 MMBTU / ~6.1 GJ per barrel |
| Natural gas | Cubic foot (cf) / cubic meter (m³) | ~1,030 BTU/cf; ~38.5 MJ/m³ |
| Coal (bituminous) | Short ton / tonne | ~24–27 GJ/tonne (varies by grade) |
| LNG | Tonne | ~52 GJ/tonne |
| Electricity | Kilowatt-hour (kWh) | 3.6 MJ/kWh (by definition) |
| Biomass (wood, dry) | Tonne | ~15–18 GJ/tonne (varies by moisture, species) |

**Key Points**

- Coal and biomass energy content varies significantly by grade, moisture content, and source — these are not fixed physical constants like the kWh-to-joule conversion
- Natural gas volumes are sensitive to measurement conditions (temperature, pressure); "standard cubic feet" (scf) assumes defined reference conditions
- Crude oil barrel-to-energy conversion also varies by crude grade (API gravity), though a standardized average is used for statistical aggregation

### The Primary Energy Equivalence Problem

A major conceptual challenge in cross-carrier conversion arises when converting **non-combustion sources** (nuclear, hydro, wind, solar) into primary energy equivalents, because these sources do not "contain" chemical energy the way fossil fuels do.

Two conventions dominate international statistics:

1. **Physical Energy Content Method** (used by IEA since 2019 for renewables): Records the actual electricity output, without inflating for a hypothetical thermal input.
2. **Substitution Method** (used historically by BP and some IEA legacy series): Converts the electricity output of nuclear, hydro, wind, and solar into an equivalent amount of primary fossil fuel energy that *would have been needed* to generate that electricity in a thermal plant, typically assuming a ~33–38% conversion efficiency.

$$E_{primary,substitution} = \frac{E_{electricity}}{\eta_{thermal}}$$

[Inference] This methodological choice is not merely a technical footnote — it can materially change the reported share of renewables or nuclear in a country's primary energy mix, sometimes by a factor of nearly 3x for non-combustion sources, making the choice of convention a genuinely consequential (and sometimes contested) analytical decision rather than a matter of established consensus.

### Conversion Workflow (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 320">
<text x="400" y="28" font-size="17" font-weight="bold" text-anchor="middle" fill="#1a1a1a">Cross-Carrier Energy Conversion Workflow (svg_diagram)</text>
<rect x="30" y="70" width="150" height="55" rx="8" fill="#2c5f7c" />
<text x="105" y="93" font-size="12" fill="#fff" text-anchor="middle">Native Unit</text>
<text x="105" y="110" font-size="11" fill="#fff" text-anchor="middle">(bbl, m³, tonne, kWh)</text>
<rect x="230" y="70" width="150" height="55" rx="8" fill="#3f7d5c" />
<text x="305" y="93" font-size="12" fill="#fff" text-anchor="middle">Calorific Value</text>
<text x="305" y="110" font-size="11" fill="#fff" text-anchor="middle">(GCV or NCV basis)</text>
<rect x="430" y="70" width="150" height="55" rx="8" fill="#8a5a2c" />
<text x="505" y="93" font-size="12" fill="#fff" text-anchor="middle">Common Unit</text>
<text x="505" y="110" font-size="11" fill="#fff" text-anchor="middle">(GJ, toe, or MWh)</text>
<rect x="630" y="70" width="150" height="55" rx="8" fill="#6b4c9a" />
<text x="705" y="93" font-size="12" fill="#fff" text-anchor="middle">Aggregated</text>
<text x="705" y="110" font-size="11" fill="#fff" text-anchor="middle">Energy Balance</text>
<line x1="180" y1="97" x2="225" y2="97" stroke="#333" stroke-width="2" marker-end="url(#arrow)" />
<line x1="380" y1="97" x2="425" y2="97" stroke="#333" stroke-width="2" marker-end="url(#arrow)" />
<line x1="580" y1="97" x2="625" y2="97" stroke="#333" stroke-width="2" marker-end="url(#arrow)" />
<rect x="130" y="180" width="540" height="100" rx="8" fill="#f4f0e8" stroke="#999" />
<text x="400" y="205" font-size="12.5" fill="#333" text-anchor="middle">Special handling required for non-combustion sources:</text>
<text x="400" y="225" font-size="12" fill="#333" text-anchor="middle">Nuclear / Hydro / Wind / Solar electricity output</text>
<text x="400" y="245" font-size="12" fill="#333" text-anchor="middle">→ Physical Content Method (direct kWh)</text>
<text x="400" y="263" font-size="12" fill="#333" text-anchor="middle">→ Substitution Method (÷ thermal efficiency ~33–38%)</text>
</svg>

### Gross vs. Net Calorific Value

A frequently overlooked but economically significant distinction is between:

- **Gross Calorific Value (GCV)** / Higher Heating Value (HHV): includes the latent heat of water vapor produced during combustion
- **Net Calorific Value (NCV)** / Lower Heating Value (LHV): excludes this latent heat, reflecting usable energy in most industrial applications

$$GCV > NCV$$

The difference between the two can be several percent, and mixing GCV-based and NCV-based figures without adjustment is a common source of error in cross-country energy comparisons, since some countries (e.g., the U.S.) report on a GCV basis while others (e.g., much of Europe) report on an NCV basis.

### Practical Example

Suppose an economist needs to compare the energy content of a country's annual imports: 2 million tonnes of coal, 500 million m³ of natural gas, and 10 TWh of imported electricity.

1. Convert coal: $2{,}000{,}000 \text{ tonnes} \times 25 \text{ GJ/tonne} = 50{,}000{,}000 \text{ GJ} = 50 \text{ PJ}$
2. Convert natural gas: $500{,}000{,}000 \text{ m}^3 \times 38.5 \text{ MJ/m}^3 \approx 19{,}250{,}000{,}000 \text{ MJ} \approx 19.25 \text{ PJ}$
3. Convert electricity: $10 \text{ TWh} \times 3.6 \times 10^6 \text{ MJ/GWh conversion chain} = 36{,}000{,}000 \text{ MJ per GWh} \rightarrow 10{,}000 \text{ GWh} \times 3{,}600 \text{ GJ/GWh} = 36 \text{ PJ}$
4. Total: $50 + 19.25 + 36 = 105.25 \text{ PJ}$

This aggregation allows the economist to compare total energy import dependence on a single, consistent basis, regardless of the physical form each carrier originally took.

### Common Pitfalls in Practice

**Key Points**

- Confusing GCV and NCV bases when merging datasets from different national statistical agencies
- Applying a generic coal or biomass calorific value without accounting for grade/moisture variation
- Mixing physical-content and substitution-method primary energy figures for renewables/nuclear without noting the methodological switch
- Failing to distinguish "cubic feet" from "standard cubic feet" in natural gas volumetric reporting
- Treating boe/toe conversion factors as universal constants across all reporting institutions

### Conclusion

Unit and conversion literacy is not a peripheral technical detail in energy economics — it is a prerequisite for any credible cross-carrier or cross-country analysis. Because energy carriers differ fundamentally in physical form (solid, liquid, gas, electromagnetic flow) and measurement convention, converting them into a common energy basis (typically joules, toe, or kWh-equivalents) requires care regarding calorific value basis, the treatment of non-combustion sources, and the specific conventions used by the data source in question.

**Related Topics**

- Primary energy balances and IEA/EIA statistical methodology
- Substitution method vs. physical content method for renewables and nuclear accounting
- Calorific value determination and fuel quality variation
- Energy intensity and cross-country energy comparisons
- Levelized cost of energy (LCOE) and its unit basis
- Natural gas measurement standards (scf, Nm³) and LNG trade conversion