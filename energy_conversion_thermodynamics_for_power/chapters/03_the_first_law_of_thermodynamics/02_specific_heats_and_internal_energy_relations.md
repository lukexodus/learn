## Specific Heats and Internal Energy Relations

### Introduction

Specific heats provide the essential link between temperature change and the corresponding change in internal energy or enthalpy for a substance, forming the practical calculation bridge between the abstract first-law energy balance and concrete numerical results. This section develops the definitions, relationships, and correct application of specific heats for ideal gases, incompressible substances, and general property relations.

### Definition of Specific Heat

**Specific heat** is defined as the amount of energy required to raise the temperature of a unit mass of a substance by one degree. Because the amount of energy needed depends on the process path (specifically, whether volume or pressure is held constant during heating), two distinct specific heats are defined for a simple compressible substance.

**Specific heat at constant volume** ($c_v$):

$$c_v = \left(\frac{\partial u}{\partial T}\right)_v$$

**Specific heat at constant pressure** ($c_p$):

$$c_p = \left(\frac{\partial h}{\partial T}\right)_P$$

**Key Points**

- $c_v$ and $c_p$ are themselves thermodynamic properties (not process-dependent quantities), since they are defined as partial derivatives of state functions ($u$ and $h$) with respect to $T$ at fixed $v$ or $P$
- Despite the names referencing "constant volume" and "constant pressure," $c_v$ and $c_p$ can be used to compute $\Delta u$ and $\Delta h$ respectively for *any* process of an ideal gas, not just constant-volume or constant-pressure processes specifically — this is because $u$ and $h$ depend on temperature alone for an ideal gas (addressed further below)
- Units: kJ/(kg·K) or kJ/(kg·°C) (numerically identical, since these are temperature *differences*); molar basis: kJ/(kmol·K)

### Physical Interpretation

**Key Points**

- $c_v$ represents energy required to raise temperature by 1° while volume is held fixed — all the added energy goes directly into increasing internal energy (no boundary work is done, so none of the added heat is "diverted" to work output)
- $c_p$ represents energy required to raise temperature by 1° while pressure is held fixed — some of the added energy goes into internal energy, and some goes into boundary work as the substance expands against constant pressure
- Because $c_p$ must supply both the internal energy increase *and* the boundary work of expansion, $c_p > c_v$ always for any substance where volume increases with temperature at constant pressure (true for essentially all real substances in single-phase regions away from unusual anomalies)

### Specific Heats of Ideal Gases

For an ideal gas, since $u = u(T)$ only (a consequence of no intermolecular forces), the partial derivative in the $c_v$ definition simplifies to an ordinary derivative:

$$c_v(T) = \frac{du}{dT} \quad \Rightarrow \quad du = c_v(T)\,dT$$

Similarly, since $h = h(T)$ only for an ideal gas (because $h = u + Pv = u + RT$, and both $u$ and $RT$ depend on $T$ alone):

$$c_p(T) = \frac{dh}{dT} \quad \Rightarrow \quad dh = c_p(T)\,dT$$

**Key Points**

- For an ideal gas, $c_v$ and $c_p$ are functions of temperature *only* — they do not depend on pressure or specific volume, a direct consequence of $u$ and $h$ each depending on $T$ alone
- This is the specific justification for why $\Delta u = \int c_v\,dT$ and $\Delta h = \int c_p\,dT$ apply to *any* ideal gas process (not just constant-$v$ or constant-$P$ processes) — the path independence of $u$ and $h$ as state functions means the same integral applies regardless of the actual process path taken

### Mayer's Relation

For an ideal gas, differentiating the relation $h = u + RT$ with respect to temperature gives a fixed relationship between the two specific heats:

$$c_p - c_v = R$$

This is known as **Mayer's relation**. It confirms directly that $c_p > c_v$ for any ideal gas (since $R > 0$), consistent with the physical interpretation above (that $c_p$ must additionally supply boundary work).

### Specific Heat Ratio

$$k = \frac{c_p}{c_v}$$

**Key Points**

- $k$ (sometimes denoted $\gamma$) is dimensionless and varies by gas type, primarily depending on molecular structure (monatomic, diatomic, polyatomic)
- Monatomic gases (He, Ar, Ne): $k \approx 1.667$ (theoretical value $5/3$ from kinetic theory, since only translational degrees of freedom store energy)
- Diatomic gases (N₂, O₂, air): $k \approx 1.4$ (theoretical value $7/5$, since rotational degrees of freedom also store energy at typical temperatures)
- Polyatomic gases (CO₂, H₂O vapor): $k$ typically ranges from about 1.29 to 1.35, reflecting additional vibrational degrees of freedom
- $k$ appears directly in isentropic process relations ($Pv^k = \text{constant}$) and in compressible flow relations (nozzle/diffuser analysis, speed of sound)

### Temperature Dependence of Specific Heats

**Key Points**

- Real specific heats generally *increase* with temperature for polyatomic gases, since additional vibrational modes become thermally active at higher temperature — this effect is small for monatomic gases and more pronounced for complex molecules
- **Cold-air-standard assumption**: specific heats are treated as constant, evaluated at room temperature (approximately 300 K) — a common simplification providing reasonable accuracy for moderate temperature ranges and is standard in introductory air-standard power cycle analysis
- **Variable specific heat approach**: uses tabulated $u(T)$ and $h(T)$ values (ideal gas tables) directly, or polynomial curve-fit correlations for $c_p(T)$, providing higher accuracy over wide temperature ranges (e.g., combustion gas temperatures in gas turbines)
- A typical polynomial curve-fit form: $$c_p(T) = a + bT + cT^2 + dT^3$$ with substance-specific coefficients $a, b, c, d$ determined by regression against experimental data

### Two Approaches to Computing $\Delta u$ and $\Delta h$ for Ideal Gases

```mermaid
flowchart TD
    A[Need Delta u or Delta h for an ideal gas process] --> B{Temperature range and accuracy needed?}
    B -->|Small range, or moderate accuracy acceptable| C[Constant specific heat approach]
    C --> C1["Delta u = cv,avg times (T2 - T1)"]
    C --> C2["Delta h = cp,avg times (T2 - T1)"]
    B -->|Large temperature range, high accuracy needed| D[Variable specific heat approach]
    D --> D1[Look up u(T1) and u(T2) from ideal gas tables directly]
    D --> D2[Look up h(T1) and h(T2) from ideal gas tables directly]
    D1 --> E["Delta u = u(T2) - u(T1)"]
    D2 --> F["Delta h = h(T2) - h(T1)"]
```

### Worked Example 1: Constant Specific Heat Approach

**Problem:** Air is heated from 300 K to 600 K. Determine $\Delta u$ and $\Delta h$ per unit mass, using constant specific heats at room temperature ($c_v = 0.718$, $c_p = 1.005$ kJ/(kg·K)).

**Solution:**

$$\Delta u = c_v(T_2-T_1) = 0.718(600-300) = 0.718(300) = 215.4 \text{ kJ/kg}$$



$$\Delta h = c_p(T_2-T_1) = 1.005(600-300) = 1.005(300) = 301.5 \text{ kJ/kg}$$

### Worked Example 2: Variable Specific Heat Approach

**Problem:** Repeat the previous example using ideal gas air tables, where $u(300\text{K}) = 214.07 \text{ kJ/kg}$, $u(600\text{K}) = 434.78 \text{ kJ/kg}$, $h(300\text{K}) = 300.19 \text{ kJ/kg}$, $h(600\text{K}) = 607.32 \text{ kJ/kg}$ [Unverified: illustrative table values consistent with commonly published ideal-gas air table formats; consult a current reference table for precise figures].

**Solution:**

$$\Delta u = u(600) - u(300) = 434.78 - 214.07 = 220.71 \text{ kJ/kg}$$



$$\Delta h = h(600) - h(300) = 607.32 - 300.19 = 307.13 \text{ kJ/kg}$$

**Comparison:** The variable specific heat result ($\Delta u = 220.71$) differs from the constant specific heat result ($\Delta u = 215.4$) by roughly 2.5%, illustrating the modest but non-negligible error introduced by assuming constant specific heats over a 300 K temperature span — the discrepancy grows for larger temperature ranges or for gases with more strongly temperature-dependent specific heats.

### Specific Heats of Incompressible Substances (Solids and Liquids)

For **incompressible substances** (solids and most liquids, where specific volume is approximately constant), a significant simplification applies: since $v \approx \text{constant}$, there is effectively no distinction between "constant volume" and "constant pressure" heating in terms of the energy required, because negligible boundary work occurs regardless of the pressure path (since $dv \approx 0$).

$$c_v \approx c_p = c \quad \text{(single specific heat value)}$$



$$du \approx c(T)\,dT, \qquad \Delta u \approx c_{avg}(T_2-T_1)$$

**Enthalpy change for an incompressible substance**, accounting for the (typically small) pressure-dependent term:

$$\Delta h = \Delta u + v\Delta P \approx c_{avg}\Delta T + v\Delta P$$

**Key Points**

- For an incompressible substance undergoing a process without pressure change (or where $v\Delta P$ is negligible compared to $c\Delta T$), $\Delta h \approx \Delta u \approx c\Delta T$ — a very common and useful simplification for liquid-phase and solid-phase energy calculations
- The $v\Delta P$ term becomes significant primarily in processes with large pressure changes at nearly constant temperature (e.g., pump work calculations in the Rankine cycle, where the liquid undergoes a substantial pressure rise with minimal temperature change)
- Typical values: liquid water $c \approx 4.18 \text{ kJ/(kg·K)}$; ice $c \approx 2.11 \text{ kJ/(kg·K)}$; many common metals have $c$ in the range 0.13–0.90 kJ/(kg·K)

### Worked Example 3: Incompressible Substance Heating

**Problem:** Determine the heat required to raise the temperature of 5 kg of liquid water from 20°C to 80°C at approximately constant pressure.

**Solution:**

$$Q = \Delta U = mc\Delta T = (5)(4.18)(80-20) = (5)(4.18)(60) = 1254 \text{ kJ}$$

### General Property Relations (Beyond Ideal Gas)

For a general (non-ideal) simple compressible substance, $u$ and $h$ depend on *both* temperature and specific volume (or pressure), requiring more general partial-derivative relations:

$$du = c_v\,dT + \left[T\left(\frac{\partial P}{\partial T}\right)_v - P\right]dv$$



$$dh = c_p\,dT + \left[v - T\left(\frac{\partial v}{\partial T}\right)_P\right]dP$$

**Key Points**

- These general relations reduce exactly to the simplified ideal-gas forms ($du = c_v\,dT$, $dh = c_p\,dT$) when the ideal gas equation of state is substituted in, since the bracketed correction terms vanish identically for an ideal gas
- For real gases and liquids near the saturation region, these correction terms are non-negligible, which is precisely why real-substance property tables (steam tables) are needed rather than simple $c_v\Delta T$ / $c_p\Delta T$ calculations
- This general relation also confirms mathematically why $c_p = c_v$ exactly only for an idealized incompressible substance (where $(\partial v/\partial T)_P \to 0$) or approximately for real liquids/solids where thermal expansion is small

### Specific Heat Relationship Summary Diagram (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 740 400" font-family="Arial, sans-serif">
<text x="370" y="26" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Specific Heat Relations by Substance Type (svg_diagram)</text>
<rect x="40" y="60" width="200" height="120" rx="8" fill="#eaf2f8" stroke="#2c5f8a" stroke-width="1.5" />
<text x="140" y="85" text-anchor="middle" font-size="13" font-weight="bold" fill="#1a1a1a">Ideal Gas</text>
<text x="140" y="110" text-anchor="middle" font-size="11" fill="#333">u = u(T) only</text>
<text x="140" y="128" text-anchor="middle" font-size="11" fill="#333">h = h(T) only</text>
<text x="140" y="146" text-anchor="middle" font-size="11" fill="#333">cp - cv = R</text>
<text x="140" y="164" text-anchor="middle" font-size="11" fill="#333">cp &gt; cv always</text>
<rect x="270" y="60" width="200" height="120" rx="8" fill="#eafaf1" stroke="#27ae60" stroke-width="1.5" />
<text x="370" y="85" text-anchor="middle" font-size="13" font-weight="bold" fill="#1a1a1a">Incompressible (solid/liquid)</text>
<text x="370" y="110" text-anchor="middle" font-size="11" fill="#333">v ≈ constant</text>
<text x="370" y="128" text-anchor="middle" font-size="11" fill="#333">cp ≈ cv = c</text>
<text x="370" y="146" text-anchor="middle" font-size="11" fill="#333">Δu ≈ cΔT</text>
<text x="370" y="164" text-anchor="middle" font-size="11" fill="#333">Δh ≈ cΔT + vΔP</text>
<rect x="500" y="60" width="200" height="120" rx="8" fill="#fdf2e9" stroke="#e67e22" stroke-width="1.5" />
<text x="600" y="85" text-anchor="middle" font-size="13" font-weight="bold" fill="#1a1a1a">General Real Substance</text>
<text x="600" y="110" text-anchor="middle" font-size="11" fill="#333">u = u(T, v)</text>
<text x="600" y="128" text-anchor="middle" font-size="11" fill="#333">h = h(T, P)</text>
<text x="600" y="146" text-anchor="middle" font-size="11" fill="#333">Correction terms</text>
<text x="600" y="164" text-anchor="middle" font-size="11" fill="#333">needed (see general relations)</text>

<text x="370" y="230" text-anchor="middle" font-size="12" fill="#555">Ideal gas and incompressible relations are limiting simplifications</text>

<text x="370" y="248" text-anchor="middle" font-size="12" fill="#555">of the general real-substance property relations</text>

</svg>

### Common Errors in Applying Specific Heats

**Key Points**

- Using $c_p$ to compute $\Delta u$ (or $c_v$ to compute $\Delta h$) for an ideal gas — the correct pairing is always $c_v \leftrightarrow \Delta u$ and $c_p \leftrightarrow \Delta h$, regardless of the actual process type
- Assuming $c_p \approx c_v$ for gases (this approximation is valid for incompressible substances only, not for gases, where the difference $R$ is often substantial relative to the specific heat values themselves)
- Applying constant specific heat values across very large temperature ranges (e.g., combustion or gas turbine exhaust temperatures) without checking whether the variable specific heat approach is warranted for the required accuracy
- Using specific heat data for the wrong gas or wrong molar mass basis (confusing kJ/(kg·K) with kJ/(kmol·K) without proper conversion via molar mass)
- Neglecting the $v\Delta P$ term when computing $\Delta h$ for an incompressible substance in a high-pressure-change process (e.g., pump work in a Rankine cycle), where this term is not negligible despite being small in most other contexts

### Relevance to Power and Energy Systems

**Key Points**

- Gas turbine (Brayton cycle) combustor and turbine analysis at high temperature commonly requires variable specific heat data (or ideal gas tables) for accurate efficiency and work predictions, since the cold-air-standard assumption introduces significant error at combustion temperatures
- Feedwater pump work calculations in the Rankine cycle rely on the incompressible-substance enthalpy relation ($\Delta h \approx v\Delta P$ for a nearly isothermal, high-pressure-rise process) as a standard simplification for estimating pump work without full compressed-liquid property tables
- Air-standard Otto and Diesel cycle analysis for internal combustion engines standardly uses either cold-air-standard (constant $c_v$, $c_p$) or variable specific heat (air tables) approaches, with the choice affecting predicted thermal efficiency and peak temperatures
- Heat exchanger sizing and thermal storage system design (e.g., sensible heat storage using water, rock, or molten salt) directly apply the incompressible-substance specific heat relation to compute required storage mass and volume for a target energy capacity

### Related Topics

- Energy Balance for Closed Systems
- The Ideal Gas Equation of State
- Enthalpy: Definition and Physical Significance
- Air-Standard Otto and Diesel Cycles
- The Rankine Cycle and Feedwater Pump Work
- Property Relations and Maxwell Relations for Real Substances