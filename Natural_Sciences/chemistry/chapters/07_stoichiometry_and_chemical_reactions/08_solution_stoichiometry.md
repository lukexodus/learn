## Solution Stoichiometry

### Foundational Concept

Solution stoichiometry extends standard reaction stoichiometry to reactions occurring in solution, where quantities of dissolved substances are expressed through **molarity (concentration)** rather than mass alone. The central relationship linking moles, molarity, and volume is:

$$n = M \times V$$

where $n$ is moles of solute, $M$ is molarity (mol/L), and $V$ is volume in liters. This equation serves as the entry and exit point of the stoichiometric roadmap whenever a substance is described as a solution of known concentration.

### Molarity Review

$$M = \frac{n_{\text{solute}}}{V_{\text{solution}} \text{ (L)}}$$

Molarity relates the amount of dissolved solute to the total volume of solution (not solvent). This distinction matters because dissolving a solute changes the total solution volume from the pure solvent volume.

### The Solution Stoichiometry Roadmap

```mermaid
flowchart LR
    A[Volume and Molarity of Solution A] --> B[Moles of A via n = MV]
    B --> C[Moles of B using mole ratio from balanced equation]
    C --> D[Convert to desired unit for B]
    D --> E[Mass, Volume, or Molarity of B]
```

**Step-by-step method:**

**Step 1:** Write and balance the chemical equation.

**Step 2:** Convert the given volume and molarity of the known solution into moles using $n = MV$.

**Step 3:** Apply the mole ratio from the balanced equation to convert to moles of the desired species.

**Step 4:** Convert moles of the desired species into the requested unit — this may be mass ($m = nM_{molar}$), volume of a gas, or, if the desired species is also a solution, rearrange $n = MV$ to solve for $V$ or $M$ as needed.

### Worked Example 1: Solution-to-Mass

What mass of solid $AgCl$ precipitates when 75.0 mL of 0.250 M $AgNO_3$ reacts completely with excess $NaCl$ solution?

**Balanced equation:**

$$AgNO_3(aq) + NaCl(aq) \rightarrow AgCl(s) + NaNO_3(aq)$$

**Step 1 — Moles of AgNO₃:**

$$n_{AgNO_3} = M \times V = 0.250 \text{ mol/L} \times 0.0750 \text{ L} = 0.01875 \text{ mol}$$

**Step 2 — Mole ratio to AgCl:**

$$n_{AgCl} = 0.01875 \text{ mol } AgNO_3 \times \frac{1 \text{ mol } AgCl}{1 \text{ mol } AgNO_3} = 0.01875 \text{ mol}$$

**Step 3 — Convert to mass:**

$$M(AgCl) = 107.87 + 35.45 = 143.32 \text{ g/mol}$$



$$m_{AgCl} = 0.01875 \text{ mol} \times 143.32 \text{ g/mol} = 2.69 \text{ g}$$

### Worked Example 2: Solution-to-Solution (Titration)

What volume of 0.150 M $HCl$ is needed to completely neutralize 40.0 mL of 0.100 M $Ba(OH)_2$?

**Balanced equation:**

$$2HCl + Ba(OH)_2 \rightarrow BaCl_2 + 2H_2O$$

**Step 1 — Moles of Ba(OH)₂:**

$$n_{Ba(OH)_2} = 0.100 \text{ mol/L} \times 0.0400 \text{ L} = 0.00400 \text{ mol}$$

**Step 2 — Mole ratio to HCl:**

$$n_{HCl} = 0.00400 \text{ mol} \times \frac{2 \text{ mol } HCl}{1 \text{ mol } Ba(OH)_2} = 0.00800 \text{ mol}$$

**Step 3 — Solve for volume of HCl:**

$$V_{HCl} = \frac{n}{M} = \frac{0.00800 \text{ mol}}{0.150 \text{ mol/L}} = 0.0533 \text{ L} = 53.3 \text{ mL}$$

### Titration and the Neutralization Point

Titration is a laboratory technique that applies solution stoichiometry to determine an unknown concentration by reacting it with a solution of known concentration (the titrant) until the reaction reaches **stoichiometric equivalence** (commonly signaled by a color-change indicator or pH meter at the equivalence point).

For a simple monoprotic acid–base neutralization:

$$M_{acid} V_{acid} = M_{base} V_{base}$$

This simplified relationship holds **only when the mole ratio of acid to base in the balanced equation is 1:1**. For any other ratio, the general form must be used:

$$\frac{M_{acid} V_{acid}}{\text{coeff}_{acid}} = \frac{M_{base} V_{base}}{\text{coeff}_{base}}$$

**Worked Example 3:**

25.00 mL of $H_2SO_4$ of unknown concentration is titrated with 0.200 M NaOH, requiring 34.50 mL to reach the equivalence point. Find the molarity of the $H_2SO_4$.

**Balanced equation:**

$$H_2SO_4 + 2NaOH \rightarrow Na_2SO_4 + 2H_2O$$

**Step 1 — Moles of NaOH used:**

$$n_{NaOH} = 0.200 \text{ mol/L} \times 0.03450 \text{ L} = 0.00690 \text{ mol}$$

**Step 2 — Mole ratio to H₂SO₄:**

$$n_{H_2SO_4} = 0.00690 \text{ mol} \times \frac{1 \text{ mol } H_2SO_4}{2 \text{ mol } NaOH} = 0.00345 \text{ mol}$$

**Step 3 — Solve for molarity:**

$$M_{H_2SO_4} = \frac{n}{V} = \frac{0.00345 \text{ mol}}{0.02500 \text{ L}} = 0.138 \text{ M}$$

### Dilution Calculations (Supporting Concept)

Solutions are frequently diluted before or after a stoichiometric reaction. The dilution equation relates concentration and volume before and after dilution, since moles of solute remain constant during dilution:

$$M_1V_1 = M_2V_2$$

**Worked Example 4:**

How many mL of 12.0 M stock $HCl$ are needed to prepare 500.0 mL of 0.100 M $HCl$?

$$V_1 = \frac{M_2 V_2}{M_1} = \frac{(0.100 \text{ mol/L})(500.0 \text{ mL})}{12.0 \text{ mol/L}} = 4.17 \text{ mL}$$

This 4.17 mL of stock is diluted to a final volume of 500.0 mL with solvent.

### Limiting Reagent in Solution Reactions

When two solutions of known volume and molarity are mixed, limiting reagent analysis proceeds identically to standard stoichiometry, using $n = MV$ as the initial conversion step for each reactant before comparing mole-to-coefficient ratios.

**Worked Example 5:**

50.0 mL of 0.200 M $Pb(NO_3)_2$ is mixed with 50.0 mL of 0.300 M $KI$. Determine the limiting reagent and mass of precipitate $PbI_2$ formed.

**Balanced equation:**

$$Pb(NO_3)_2(aq) + 2KI(aq) \rightarrow PbI_2(s) + 2KNO_3(aq)$$

**Step 1 — Moles of each reactant:**

$$n_{Pb(NO_3)_2} = 0.200 \times 0.0500 = 0.0100 \text{ mol}$$



$$n_{KI} = 0.300 \times 0.0500 = 0.0150 \text{ mol}$$

**Step 2 — Divide by coefficients:**

$$Pb(NO_3)_2: \frac{0.0100}{1} = 0.0100 \qquad KI: \frac{0.0150}{2} = 0.0075$$

Since 0.0075 < 0.0100, **KI is the limiting reagent**.

**Step 3 — Moles of PbI₂ from KI:**

$$n_{PbI_2} = 0.0150 \text{ mol } KI \times \frac{1 \text{ mol } PbI_2}{2 \text{ mol } KI} = 0.00750 \text{ mol}$$

**Step 4 — Convert to mass:**

$$M(PbI_2) = 207.2 + 2(126.90) = 461.0 \text{ g/mol}$$



$$m_{PbI_2} = 0.00750 \times 461.0 = 3.46 \text{ g}$$

### Ion Concentration in Solution Stoichiometry

For strong electrolytes, it is often necessary to track the concentration of individual ions rather than the formula unit, since dissociation multiplies the effective ion concentration by the stoichiometric subscript in the formula.

**Example:** For 0.100 M $Ba(NO_3)_2$, which fully dissociates:

$$Ba(NO_3)_2(aq) \rightarrow Ba^{2+}(aq) + 2NO_3^-(aq)$$



$$[Ba^{2+}] = 0.100 \text{ M} \qquad [NO_3^-] = 2 \times 0.100 = 0.200 \text{ M}$$

This distinction is essential in precipitation reactions and net ionic equation analysis, where the reacting species is the ion, not the neutral formula unit.

### Common Pitfalls

- **Confusing solution volume with solvent volume** — molarity is defined using total solution volume, not the volume of water added.
- **Forgetting to convert mL to L** before applying $n = MV$, since molarity is defined per liter.
- **Applying $M_1V_1 = M_2V_2$ to a chemical reaction** — this equation applies only to dilution (same solute, no reaction), not to titration between two different reactants unless the mole ratio is exactly 1:1.
- **Neglecting dissociation** when a problem asks for ion concentration rather than formula unit concentration.
- **Mixing up "moles of solute" with "moles of ions"** in polyprotic acids or salts with multiple ions per formula unit.

### Solution Stoichiometry Roadmap Diagram (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 240">
\<style\>
.box { fill: #f0f4f8; stroke: #2b6cb0; stroke-width: 2; }
.label { font-family: Arial, sans-serif; font-size: 13px; fill: #1a202c; }
.title { font-family: Arial, sans-serif; font-size: 13px; fill: #2b6cb0; font-weight: bold; }
.arrow { stroke: #2b6cb0; stroke-width: 2; marker-end: url(#arrowhead3); }
\</style\>
<text x="340" y="20" text-anchor="middle" class="title">Solution Stoichiometry Conversion Path (svg_diagram)</text>
<rect x="10" y="60" width="150" height="55" rx="8" class="box" />
<text x="85" y="85" text-anchor="middle" class="label">Volume + Molarity</text>
<text x="85" y="102" text-anchor="middle" class="label">of Solution A</text>
<line x1="160" y1="87" x2="215" y2="87" class="arrow" />
<text x="187" y="77" text-anchor="middle" class="label" font-size="11">n = MV</text>
<rect x="215" y="60" width="110" height="55" rx="8" class="box" />
<text x="270" y="92" text-anchor="middle" class="label">Moles of A</text>
<line x1="325" y1="87" x2="390" y2="87" class="arrow" />
<text x="357" y="70" text-anchor="middle" class="label" font-size="11">×(coeff B /</text>
<text x="357" y="82" text-anchor="middle" class="label" font-size="11">coeff A)</text>
<rect x="390" y="60" width="110" height="55" rx="8" class="box" />
<text x="445" y="92" text-anchor="middle" class="label">Moles of B</text>
<line x1="500" y1="87" x2="560" y2="87" class="arrow" />
<text x="530" y="77" text-anchor="middle" class="label" font-size="11">V=n/M</text>
<rect x="560" y="60" width="110" height="55" rx="8" class="box" />
<text x="615" y="85" text-anchor="middle" class="label">Mass, Volume,</text>
<text x="615" y="102" text-anchor="middle" class="label">or Molarity of B</text>
<rect x="140" y="150" width="400" height="60" rx="8" class="box" />
<text x="340" y="175" text-anchor="middle" class="label">Dilution (no reaction): M1V1 = M2V2</text>
<text x="340" y="195" text-anchor="middle" class="label">Titration (reaction): use mole ratio, not M1V1=M2V2</text>
</svg>

**Related Topics**

- Molarity and concentration calculations
- Reaction stoichiometry calculations
- Acid–base titration curves and equivalence points
- Dilution and serial dilution techniques
- Net ionic equations and spectator ions
- Precipitation reactions and solubility rules
- Standardization of solutions
- Limiting reagent analysis in multi-reactant systems