## Stoichiometric and Actual Combustion

### Overview

Combustion is a rapid exothermic chemical reaction between a fuel and an oxidizer (typically atmospheric oxygen) producing heat and combustion products. Stoichiometric combustion refers to the theoretical, chemically-exact reaction in which the fuel reacts with precisely the amount of oxidizer needed for complete combustion, with no excess oxidizer and no unreacted fuel remaining. Actual combustion in real equipment virtually always deviates from this ideal, requiring careful analysis to quantify air requirements, excess air, and resulting product composition — foundational calculations for boiler/furnace design, emissions estimation, and combustion efficiency analysis.

### Stoichiometric Combustion Fundamentals

The stoichiometric (or theoretical) air requirement is the exact amount of air needed to supply sufficient oxygen for complete combustion of a given fuel, with all carbon converted to CO₂, all hydrogen converted to H₂O, and all sulfur (if present) converted to SO₂, with no excess oxygen remaining in the products.

**General Combustion Reaction for a Hydrocarbon Fuel:**

For a generic hydrocarbon fuel $C_xH_y$, the stoichiometric combustion reaction with air (approximated as 21% O₂, 79% N₂ by volume, giving a molar ratio of 3.76 mol N₂ per mol O₂) is:

$$C_xH_y + a(O_2 + 3.76N_2) \rightarrow xCO_2 + \frac{y}{2}H_2O + 3.76aN_2$$

where the stoichiometric coefficient $a$ (moles of O₂ required per mole of fuel) is determined by balancing oxygen atoms:

$$a = x + \frac{y}{4}$$

**Key Points:**

- Nitrogen is treated as inert in this basic stoichiometric balance (passing through the reaction unchanged), though at actual flame temperatures some nitrogen does react to form NOx — this is addressed separately under emissions/NOx formation topics, not within the basic stoichiometric mass balance.
- For fuels containing oxygen, sulfur, or other elements (common in coal, biomass, and some liquid fuels), the ultimate analysis (elemental composition) is used to perform a more detailed atom balance accounting for each element's combustion products.

### Air-Fuel Ratio (AFR)

The air-fuel ratio expresses the mass (or molar) amount of air supplied per unit of fuel:

$$AFR = \frac{m_{air}}{m_{fuel}}$$

**Stoichiometric Air-Fuel Ratio** is the AFR corresponding to exact, complete combustion with no excess air. Typical stoichiometric AFR values (mass basis) for common fuels:

| Fuel | Approximate Stoichiometric AFR (mass basis) |
| --- | --- |
| Methane (CH₄) | ~17.2:1 |
| Gasoline (octane, C₈H₁₈, representative) | ~15.1:1 |
| Diesel fuel (representative) | ~14.5:1 |
| Bituminous coal (representative, varies by coal analysis) | ~10-11:1 |

[Values are representative approximations for typical fuel compositions; actual stoichiometric AFR depends on the specific fuel's exact elemental/molecular composition and should be calculated from ultimate/proximate analysis for precise engineering work.]

### Equivalence Ratio and Excess Air

**Equivalence Ratio ($\phi$):**

$$\phi = \frac{(AFR)_{stoichiometric}}{(AFR)_{actual}} = \frac{(FAR)_{actual}}{(FAR)_{stoichiometric}}$$

where FAR is the fuel-air ratio (inverse of AFR).

**Key Points:**

- $\phi = 1$: stoichiometric (exact) combustion.
- $\phi < 1$: fuel-lean mixture (excess air present, more air than stoichiometrically required).
- $\phi > 1$: fuel-rich mixture (insufficient air, less than stoichiometrically required; leads to incomplete combustion, CO and unburned hydrocarbon formation).

**Percent Excess Air:**

$$\%\ Excess\ Air = \frac{(AFR)_{actual} - (AFR)_{stoichiometric}}{(AFR)_{stoichiometric}} \times 100\%$$

**Percent Theoretical Air** (equivalent alternative expression):

$$\%\ Theoretical\ Air = \frac{(AFR)_{actual}}{(AFR)_{stoichiometric}} \times 100\%$$

**Key Points:**

- 100% theoretical air corresponds to exactly stoichiometric combustion (0% excess air); 120% theoretical air means 20% excess air.
- Nearly all practical combustion equipment operates with some excess air (fuel-lean, $\phi < 1$) to ensure complete combustion of the fuel, since perfect, instantaneous mixing of fuel and air at exactly stoichiometric proportions is not achievable in real equipment — insufficient mixing at exactly $\phi=1$ would leave fuel-rich pockets producing CO and unburned hydrocarbons.

### Why Actual Combustion Deviates from Stoichiometric

**Key Points:**

- **Imperfect mixing:** Real burners cannot achieve perfectly uniform, molecular-level mixing of fuel and air instantaneously; some excess air compensates for locally fuel-rich or fuel-lean pockets, ensuring overall complete combustion.
- **Flame stability and turndown requirements:** Some equipment requires excess air across a range of operating loads to maintain stable combustion and avoid flame-out at reduced firing rates.
- **Emissions trade-offs:** Excess air level affects NOx formation (generally, insufficient excess air can lead to CO/unburned fuel emissions, while excessive excess air can lower flame temperature but also increase NOx in ways that depend on the specific temperature/mixing regime, and always increases sensible heat loss up the stack) — see combustion emissions topics for a fuller treatment of NOx formation mechanisms.
- **Practical safety margins:** Operating with a controlled excess air margin provides operational buffer against fuel composition variability and equipment/control imprecision, reducing the risk of unburned fuel accumulation (a safety hazard in enclosed combustion spaces).

### Typical Excess Air Levels by Equipment/Fuel Type

| Combustion Equipment / Fuel | Typical Excess Air Range |
| --- | --- |
| Gas-fired boilers | 5-20% |
| Oil-fired boilers | 10-20% |
| Pulverized coal boilers | 15-30% |
| Stoker-fired coal boilers | 20-60% (less precise mixing than pulverized firing) |
| Gas turbines | Very high (often 200-400%+ excess air, since excess air also serves as a turbine cooling/dilution medium, not solely for complete combustion) |

[Ranges are commonly cited approximate industry figures; actual optimal excess air for a given unit is determined by combustion tuning/testing specific to that equipment and fuel.]

**Key Points:**

- Gas turbines are a notable exception to the general "minimize excess air for efficiency" principle: their very high excess air levels are driven primarily by the need to limit turbine inlet temperature to material-safe levels and provide cooling air for turbine blades, not by combustion completeness requirements alone.

### Combustion Efficiency and Excess Air Trade-off

**Key Points:**

- Insufficient excess air (approaching or below stoichiometric) risks incomplete combustion, producing CO and unburned hydrocarbons — a direct loss of chemical energy (unburned fuel represents wasted heating value) and a safety/emissions concern.
- Excessive excess air, while ensuring complete combustion, increases the mass of hot flue gas leaving the stack, carrying away more sensible heat and reducing overall boiler/furnace thermal efficiency (this is often called the **stack loss** or **dry flue gas loss**).
- There is therefore a practical optimum excess air level for any given combustion system — enough to ensure complete combustion with margin for real-world mixing imperfections, but not so much as to unnecessarily increase stack heat losses. Combustion tuning (using flue gas O₂ and CO analyzers) is the standard practical method for identifying and maintaining this optimum in operating equipment.

### Excess Air vs. Efficiency/Emissions Trade-off Diagram

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 850 460" font-family="sans-serif">
<text x="425" y="25" font-size="18" text-anchor="middle" font-weight="bold">Excess Air Trade-off Curve (svg_diagram)</text>
<line x1="90" y1="400" x2="780" y2="400" stroke="#333" stroke-width="2" />
<line x1="90" y1="400" x2="90" y2="60" stroke="#333" stroke-width="2" />
<text x="430" y="435" text-anchor="middle" font-size="13">Excess Air (%)</text>
<text x="35" y="230" text-anchor="middle" font-size="13" transform="rotate(-90 35 230)">Relative Level</text>

<polyline points="150,90 220,180 300,280 400,350 500,375 650,385 750,390" fill="none" stroke="#c0392b" stroke-width="3" />
<text x="180" y="110" font-size="11" fill="#c0392b">CO / Unburned Fuel</text>

<polyline points="150,370 300,350 450,310 600,250 750,170" fill="none" stroke="#2980b9" stroke-width="3" />
<text x="600" y="230" font-size="11" fill="#2980b9">Stack Heat Loss</text>

<line x1="330" y1="60" x2="330" y2="400" stroke="#27ae60" stroke-width="2" stroke-dasharray="6,4" />
<text x="330" y="50" font-size="11" fill="#27ae60" text-anchor="middle">Practical Optimum Zone</text>

<text x="150" y="415" font-size="11" text-anchor="middle">0% (Stoich.)</text>

<text x="750" y="415" font-size="11" text-anchor="middle">High Excess Air</text>

</svg>

### Practical Example 1: Stoichiometric Air Requirement for Methane

**Given:** Determine the stoichiometric air-fuel ratio (mass basis) for methane (CH₄) combustion.

**Solution:**

Balanced stoichiometric reaction:

$$CH_4 + 2(O_2 + 3.76N_2) \rightarrow CO_2 + 2H_2O + 7.52N_2$$

(Here $a = x + y/4 = 1 + 4/4 = 2$ mol O₂ per mol fuel.)

Molar mass basis: 1 mol CH₄ = 16 kg/kmol; air required = 2 mol O₂ + 7.52 mol N₂ = 2(32) + 7.52(28) = 64 + 210.6 = 274.6 kg air per kmol fuel (using approximate air composition by mass).

$$AFR_{stoich} = \frac{274.6\ \text{kg air}}{16\ \text{kg fuel}} \approx 17.2$$

This matches the commonly cited value of approximately 17.2:1 for methane, confirming the calculation.

### Practical Example 2: Excess Air Calculation

**Given:** A gas-fired boiler burns methane with an actual air-fuel ratio of $AFR_{actual} = 20.6$ (mass basis).

**Find:** Percent excess air.

**Solution:**

$$\%\ Excess\ Air = \frac{AFR_{actual} - AFR_{stoich}}{AFR_{stoich}} \times 100\% = \frac{20.6 - 17.2}{17.2} \times 100\% \approx 19.8\%$$

**Interpretation:** This boiler is operating with approximately 20% excess air, a typical and reasonable value for a gas-fired boiler, providing margin for complete combustion while limiting stack heat losses to a moderate level.

### Combustion Products and Flue Gas Composition

**Key Points:**

- **Complete combustion** (adequate excess air, good mixing) yields flue gas composed primarily of CO₂, H₂O (vapor), excess O₂, and N₂ (plus SO₂ if sulfur is present in the fuel).
- **Incomplete combustion** (insufficient air or poor mixing) produces CO, unburned hydrocarbons, and potentially soot/particulate matter (visible smoke) in addition to (or instead of) some of the complete-combustion products, representing both an efficiency loss and a safety/emissions concern (CO is toxic and represents unrecovered chemical energy).
- **Flue gas analysis** (measuring O₂, CO₂, and CO concentrations in the exhaust, typically via continuous emissions monitoring or portable combustion analyzers) is the standard practical tool for verifying actual excess air level and combustion completeness in operating equipment, since these measured concentrations can be related back to the equivalence ratio and excess air via mass balance calculations.

### Dew Point and Condensation Considerations

**Key Points:**

- Water vapor formed during combustion will condense if flue gas is cooled below its **water dew point** (dependent on the partial pressure of water vapor in the flue gas, itself dependent on fuel hydrogen content and excess air level); this is exploited intentionally in **condensing boilers** to recover additional latent heat (approaching HHV-based efficiency) but must be avoided in conventional equipment not designed for condensing operation, where condensation can cause corrosion.
- If sulfur is present in the fuel, the **acid dew point** (where sulfuric acid vapor condenses, at a higher temperature than the pure water dew point) is a critical design constraint for minimum allowable stack/heat-exchanger surface temperatures, as referenced in HRSG design considerations.

### Related Topics

- Fuel Types: Solid, Liquid, and Gaseous Fuels
- Higher and Lower Heating Value Calculations
- Flue Gas Emissions Control (SOx, NOx, Particulates)
- Combustion Efficiency and Boiler Heat Loss Analysis
- Adiabatic Flame Temperature
- NOx Formation Mechanisms in Combustion
- Condensing Boiler Design and Dew Point Recovery
- Flue Gas Analysis and Combustion Tuning