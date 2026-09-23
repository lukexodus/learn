## Reaction Stoichiometry Calculations


### Foundational Concept

Reaction stoichiometry is the quantitative relationship between reactants and products in a balanced chemical equation. It relies on the **mole ratio** — the ratio of coefficients in a balanced equation — as a conversion factor between the amounts of different substances involved in a reaction.

A balanced equation such as:

$$aA + bB \rightarrow cC + dD$$

provides mole ratios such as $\dfrac{c \text{ mol } C}{a \text{ mol } A}$, which allow conversion between moles of any species in the reaction and moles of any other species.

### Prerequisite: A Correctly Balanced Equation

Stoichiometric calculations are only valid when the equation is balanced (equal numbers of each atom type on both sides), since the coefficients represent the mole ratios directly. An unbalanced equation gives incorrect ratios and invalidates every downstream calculation.

**Example — balancing propane combustion:**

$$C_3H_8 + 5O_2 \rightarrow 3CO_2 + 4H_2O$$

Verification: C: 3 = 3; H: 8 = 8; O: $5(2) = 10$ on the left, $3(2) + 4(1) = 10$ on the right. Balanced.

### The General Stoichiometric Roadmap

Most stoichiometry problems follow this conversion path, regardless of the units given for the starting substance:

```mermaid
flowchart LR
    A[Mass or Volume of A] --> B[Moles of A]
    B --> C[Moles of B using mole ratio from balanced equation]
    C --> D[Mass, Volume, or Particles of B]
```

**Key idea:** conversions into and out of moles (via molar mass, molarity, or molar volume) are always performed *before or after* the mole-ratio step — the mole ratio itself only relates moles to moles.

### Step-by-Step Method

**Step 1:** Write and balance the chemical equation.

**Step 2:** Convert the given quantity of the starting substance into moles.

- From mass: $n = \dfrac{m}{M}$
- From solution volume and concentration: $n = MV$
- From gas volume at STP: $n = \dfrac{V}{22.4 \text{ L/mol}}$
- From particles: $n = \dfrac{N}{6.022 \times 10^{23}}$

**Step 3:** Use the mole ratio from the balanced equation to convert moles of the given substance to moles of the desired substance.

$$n_{\text{desired}} = n_{\text{given}} \times \frac{\text{coefficient of desired substance}}{\text{coefficient of given substance}}$$

**Step 4:** Convert moles of the desired substance into the requested unit (mass, volume, particles, concentration).

### Worked Example 1: Mass-to-Mass Stoichiometry

How many grams of $CO_2$ are produced when 44.0 g of propane ($C_3H_8$) undergoes complete combustion?

**Balanced equation:**

$$C_3H_8 + 5O_2 \rightarrow 3CO_2 + 4H_2O$$

**Step 1 — Moles of propane:**

$$M(C_3H_8) = 3(12.01) + 8(1.008) = 44.09 \text{ g/mol}$$



$$n_{C_3H_8} = \frac{44.0 \text{ g}}{44.09 \text{ g/mol}} = 0.998 \text{ mol}$$

**Step 2 — Mole ratio to CO₂:**

$$n_{CO_2} = 0.998 \text{ mol } C_3H_8 \times \frac{3 \text{ mol } CO_2}{1 \text{ mol } C_3H_8} = 2.994 \text{ mol}$$

**Step 3 — Convert to grams:**

$$M(CO_2) = 44.01 \text{ g/mol}$$



$$m_{CO_2} = 2.994 \text{ mol} \times 44.01 \text{ g/mol} = 131.8 \text{ g}$$

**Answer:** approximately 132 g of $CO_2$.

### Worked Example 2: Volume-to-Mass (Gas at STP)

What mass of iron is required to react completely with 5.60 L of chlorine gas at STP, given the reaction:

$$2Fe + 3Cl_2 \rightarrow 2FeCl_3$$

**Step 1 — Moles of Cl₂:**

$$n_{Cl_2} = \frac{5.60 \text{ L}}{22.4 \text{ L/mol}} = 0.250 \text{ mol}$$

**Step 2 — Mole ratio to Fe:**

$$n_{Fe} = 0.250 \text{ mol } Cl_2 \times \frac{2 \text{ mol } Fe}{3 \text{ mol } Cl_2} = 0.1667 \text{ mol}$$

**Step 3 — Convert to grams:**

$$m_{Fe} = 0.1667 \text{ mol} \times 55.85 \text{ g/mol} = 9.31 \text{ g}$$

### Worked Example 3: Solution Stoichiometry (Titration-Type)

What volume of 0.500 M NaOH is required to completely neutralize 25.0 mL of 0.200 M $H_2SO_4$?

**Balanced equation:**

$$2NaOH + H_2SO_4 \rightarrow Na_2SO_4 + 2H_2O$$

**Step 1 — Moles of H₂SO₄:**

$$n_{H_2SO_4} = M \times V = 0.200 \text{ mol/L} \times 0.0250 \text{ L} = 0.00500 \text{ mol}$$

**Step 2 — Mole ratio to NaOH:**

$$n_{NaOH} = 0.00500 \text{ mol} \times \frac{2 \text{ mol } NaOH}{1 \text{ mol } H_2SO_4} = 0.0100 \text{ mol}$$

**Step 3 — Solve for volume:**

$$V_{NaOH} = \frac{n}{M} = \frac{0.0100 \text{ mol}}{0.500 \text{ mol/L}} = 0.0200 \text{ L} = 20.0 \text{ mL}$$

### Limiting Reagent Calculations

When quantities of **two or more reactants** are given, one reactant will be fully consumed before the others — this is the **limiting reagent**, and it determines the maximum amount of product formed. Any reactant remaining afterward is the **excess reagent**.

**Method to identify the limiting reagent:**

1. Convert all given reactant masses/volumes to moles.
2. Divide each reactant's available moles by its coefficient in the balanced equation.
3. The reactant with the **smallest** resulting value is the limiting reagent.

Alternatively: calculate the theoretical yield of a common product from each reactant separately; the reactant that produces the **least** amount of product is limiting.

### Worked Example 4: Limiting Reagent

Given the reaction:

$$N_2 + 3H_2 \rightarrow 2NH_3$$

If 28.0 g of $N_2$ reacts with 6.00 g of $H_2$, determine the limiting reagent and the mass of $NH_3$ produced.

**Step 1 — Convert to moles:**

$$n_{N_2} = \frac{28.0}{28.02} = 0.999 \text{ mol}$$



$$n_{H_2} = \frac{6.00}{2.016} = 2.976 \text{ mol}$$

**Step 2 — Divide by coefficients:**

$$N_2: \frac{0.999}{1} = 0.999 \qquad H_2: \frac{2.976}{3} = 0.992$$

Since 0.992 < 0.999, **$H_2$ is the limiting reagent**.

**Step 3 — Calculate NH₃ from the limiting reagent:**

$$n_{NH_3} = 2.976 \text{ mol } H_2 \times \frac{2 \text{ mol } NH_3}{3 \text{ mol } H_2} = 1.984 \text{ mol}$$



$$m_{NH_3} = 1.984 \text{ mol} \times 17.03 \text{ g/mol} = 33.8 \text{ g}$$

**Excess reagent remaining:**

$$n_{N_2 \text{ used}} = 1.984 \text{ mol } NH_3 \times \frac{1 \text{ mol } N_2}{2 \text{ mol } NH_3} = 0.992 \text{ mol}$$



$$n_{N_2 \text{ excess}} = 0.999 - 0.992 = 0.007 \text{ mol} \Rightarrow m_{N_2 \text{ excess}} \approx 0.20 \text{ g}$$

### Theoretical Yield, Actual Yield, and Percent Yield

- **Theoretical yield** — the maximum amount of product calculated stoichiometrically from the limiting reagent (assumes 100% conversion, no side reactions or losses).
- **Actual yield** — the amount of product actually obtained experimentally; always ≤ theoretical yield in practice due to side reactions, incomplete reactions, or mechanical losses during purification/isolation. [This variance reflects real experimental behavior and may differ across lab conditions.]
- **Percent yield** quantifies reaction efficiency:

$$\%\text{yield} = \frac{\text{actual yield}}{\text{theoretical yield}} \times 100\%$$

**Worked Example 5:**

Using the theoretical yield of 33.8 g $NH_3$ calculated above, if the actual laboratory yield obtained is 29.5 g, find the percent yield.

$$\%\text{yield} = \frac{29.5}{33.8} \times 100\% = 87.3\%$$

### Stoichiometry Involving Gases (Non-STP Conditions)

When gas volumes are given at conditions other than STP, the ideal gas law is used to find moles before applying the mole ratio:

$$PV = nRT \quad \Rightarrow \quad n = \frac{PV}{RT}$$

where $R = 0.08206 \text{ L·atm/(mol·K)}$ (or the equivalent value matching the pressure units used), and $T$ is in kelvin.

This value of $n$ is then substituted into the standard stoichiometric roadmap (Step 3 onward) exactly as with any other mole quantity.

### Sequential/Multi-Step Stoichiometry

Many real reactions occur in a series of steps (e.g., industrial processes, multi-step syntheses). The stoichiometric approach chains mole ratios across each balanced equation in sequence, converting moles of the initial reactant all the way to moles of the final product.

**General pattern for two sequential reactions:**

$$A \xrightarrow{\text{Eq. 1}} B \xrightarrow{\text{Eq. 2}} C$$



$$n_C = n_A \times \left(\frac{\text{coeff. } B}{\text{coeff. } A}\right)_{\text{Eq. 1}} \times \left(\frac{\text{coeff. } C}{\text{coeff. } B}\right)_{\text{Eq. 2}}$$

This is functionally the same single-step method applied twice in succession, with the moles of the intermediate species (B) canceling out algebraically.

### Common Pitfalls

- **Forgetting to balance the equation first** — using unbalanced coefficients invalidates the entire calculation.
- **Applying mole ratios to masses directly** — mole ratios only relate moles to moles; masses of different substances cannot be directly cross-multiplied using equation coefficients because molar masses differ.
- **Neglecting limiting reagent analysis** when quantities of multiple reactants are given — assuming the reactant with the larger mass is automatically in excess is incorrect, since molar mass and stoichiometric coefficients affect which reactant runs out first.
- **Confusing percent yield with percent composition or percent error** — these are distinct concepts despite similar terminology.
- **Rounding intermediate values too early**, which compounds error through multi-step calculations; carry extra significant figures until the final step.

### Stoichiometry Roadmap Summary Diagram (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 260">
\<style\>
.box { fill: #f0f4f8; stroke: #2b6cb0; stroke-width: 2; }
.label { font-family: Arial, sans-serif; font-size: 13px; fill: #1a202c; }
.title { font-family: Arial, sans-serif; font-size: 13px; fill: #2b6cb0; font-weight: bold; }
.arrow { stroke: #2b6cb0; stroke-width: 2; marker-end: url(#arrowhead2); }
\</style\>
<text x="340" y="20" text-anchor="middle" class="title">General Stoichiometric Conversion Path (svg_diagram)</text>
<rect x="20" y="60" width="140" height="55" rx="8" class="box" />
<text x="90" y="92" text-anchor="middle" class="label">Mass/Volume of A</text>
<line x1="160" y1="87" x2="220" y2="87" class="arrow" />
<text x="190" y="77" text-anchor="middle" class="label">÷M or MV</text>
<rect x="220" y="60" width="120" height="55" rx="8" class="box" />
<text x="280" y="92" text-anchor="middle" class="label">Moles of A</text>
<line x1="340" y1="87" x2="400" y2="87" class="arrow" />
<text x="370" y="70" text-anchor="middle" class="label" font-size="11">×(coeff B /</text>
<text x="370" y="82" text-anchor="middle" class="label" font-size="11">coeff A)</text>
<rect x="400" y="60" width="120" height="55" rx="8" class="box" />
<text x="460" y="92" text-anchor="middle" class="label">Moles of B</text>
<line x1="520" y1="87" x2="580" y2="87" class="arrow" />
<text x="550" y="77" text-anchor="middle" class="label">×M or /M</text>
<rect x="580" y="60" width="80" height="55" rx="8" class="box" />
<text x="620" y="92" text-anchor="middle" class="label">Mass of B</text>
<rect x="140" y="160" width="400" height="70" rx="8" class="box" />
<text x="340" y="185" text-anchor="middle" class="label">Limiting Reagent: compare (n / coefficient)</text>
<text x="340" y="205" text-anchor="middle" class="label">for each reactant — smallest value limits the reaction</text>
</svg>

**Related Topics**

- Empirical and molecular formulas
- Limiting reagent problems (extended, multi-reactant scenarios)
- Percent yield and reaction efficiency
- Molarity and solution stoichiometry
- Ideal gas law applications in stoichiometry
- Titration calculations
- Thermochemical stoichiometry (enthalpy per mole of reaction)
- Balancing complex redox equations