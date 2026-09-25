## The Lever Rule and Phase Composition

### Definition and Physical Basis

The lever rule is a mathematical relationship used to determine the relative amounts (mass fractions or mole fractions) of coexisting phases in a two-phase region of a binary phase diagram, given the overall alloy composition and the compositions of the individual phases at equilibrium.

The rule derives its name from an analogy to a mechanical lever balanced at a fulcrum: the overall composition point acts as the fulcrum, and the phase compositions act as the points where masses are suspended. Just as a lever balances when the products of mass and distance are equal on both sides, the phase fractions balance according to their compositional "distance" from the overall alloy composition.

### Derivation from Mass Balance

Consider a binary alloy system with two components, $A$ and $B$, existing as two phases, $\alpha$ and $\beta$, at a given temperature within a two-phase field.

**Definitions:**

- $C_0$ = overall (nominal) composition of the alloy (mass % of $B$)
- $C_\alpha$ = composition of the $\alpha$ phase (mass % of $B$)
- $C_\beta$ = composition of the $\beta$ phase (mass % of $B$)
- $W_\alpha$ = mass fraction of $\alpha$ phase
- $W_\beta$ = mass fraction of $\beta$ phase

**Conservation of mass principles:**

Total mass fraction must sum to unity:

$$W_\alpha + W_\beta = 1$$

Conservation of solute $B$: the total mass of $B$ in the system equals the sum of $B$ contributed by each phase:

$$W_\alpha C_\alpha + W_\beta C_\beta = C_0$$

**Solving the system:**

Substituting $W_\beta = 1 - W_\alpha$ into the solute balance:

$$W_\alpha C_\alpha + (1 - W_\alpha) C_\beta = C_0$$



$$W_\alpha (C_\alpha - C_\beta) = C_0 - C_\beta$$



$$W_\alpha = \frac{C_0 - C_\beta}{C_\alpha - C_\beta} = \frac{C_\beta - C_0}{C_\beta - C_\alpha}$$

By symmetry:

$$W_\beta = \frac{C_0 - C_\alpha}{C_\beta - C_\alpha}$$

**Standard lever rule formulas (the form most commonly memorized):**

$$W_\alpha = \frac{C_\beta - C_0}{C_\beta - C_\alpha}$$



$$W_\beta = \frac{C_0 - C_\alpha}{C_\beta - C_\alpha}$$

Each phase fraction equals the length of the opposite arm of the tie-line divided by the total tie-line length — this is the "inverse lever arm" property that gives the rule its name.

### Geometric Interpretation on the Phase Diagram

At a given temperature, a horizontal line drawn across a two-phase region is called a **tie-line** (or isotherm). It intersects the phase boundaries (solidus/solvus on one side, liquidus/solvus on the other) at points representing $C_\alpha$ and $C_\beta$.

The vertical line at $C_0$ intersects this tie-line at some point between $C_\alpha$ and $C_\beta$, dividing it into two segments:

- Left arm length: $C_0 - C_\alpha$
- Right arm length: $C_\beta - C_0$

The mass fraction of a given phase is proportional to the length of the arm on the **opposite** side of the overall composition — this inverse relationship is the defining geometric feature of the lever rule.

(svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 420">

<rect x="0" y="0" width="700" height="420" fill="`#ffffff`" />

<text x="350" y="25" font-size="16" font-weight="bold" text-anchor="middle" fill="#111">Lever Rule Construction on a Binary Tie-Line (svg_diagram)</text>


<line x1="80" y1="350" x2="620" y2="350" stroke="#333" stroke-width="2" />
<line x1="80" y1="60" x2="80" y2="350" stroke="#333" stroke-width="2" />
<text x="350" y="385" font-size="14" text-anchor="middle" fill="#111">Composition (wt% B) →</text>
<text x="40" y="205" font-size="14" text-anchor="middle" fill="#111" transform="rotate(-90 40,205)">Temperature →</text>

<path d="M 140 100 Q 300 180 350 220" fill="none" stroke="#1a5fb4" stroke-width="2.5" />
<text x="150" y="90" font-size="13" fill="#1a5fb4">Liquidus / β boundary</text>
<path d="M 560 100 Q 420 180 350 220" fill="none" stroke="#c01c28" stroke-width="2.5" />
<text x="470" y="90" font-size="13" fill="#c01c28">Solidus / α boundary</text>

<line x1="200" y1="220" x2="480" y2="220" stroke="#222" stroke-width="2" stroke-dasharray="6,3" />

<circle cx="200" cy="220" r="5" fill="#1a5fb4" />
<circle cx="480" cy="220" r="5" fill="#c01c28" />
<circle cx="320" cy="220" r="6" fill="#111" />

<line x1="320" y1="220" x2="320" y2="350" stroke="#555" stroke-width="1.5" stroke-dasharray="3,3" />
<line x1="200" y1="220" x2="200" y2="350" stroke="#1a5fb4" stroke-width="1" stroke-dasharray="2,2" />
<line x1="480" y1="220" x2="480" y2="350" stroke="#c01c28" stroke-width="1" stroke-dasharray="2,2" />


<text x="200" y="368" font-size="13" text-anchor="middle" fill="`#1a5fb4`">C_α</text>

<text x="320" y="368" font-size="13" text-anchor="middle" fill="#111" font-weight="bold">C_0</text>

<text x="480" y="368" font-size="13" text-anchor="middle" fill="`#c01c28`">C_β</text>


<line x1="200" y1="240" x2="320" y2="240" stroke="#1a5fb4" stroke-width="1.5" />
<line x1="200" y1="235" x2="200" y2="245" stroke="#1a5fb4" stroke-width="1.5" />
<line x1="320" y1="235" x2="320" y2="245" stroke="#1a5fb4" stroke-width="1.5" />
<text x="260" y="258" font-size="12" text-anchor="middle" fill="#1a5fb4">arm = C_0 − C_α (→ W_β)</text>
<line x1="320" y1="270" x2="480" y2="270" stroke="#c01c28" stroke-width="1.5" />
<line x1="320" y1="265" x2="320" y2="275" stroke="#c01c28" stroke-width="1.5" />
<line x1="480" y1="265" x2="480" y2="275" stroke="#c01c28" stroke-width="1.5" />
<text x="400" y="288" font-size="12" text-anchor="middle" fill="#c01c28">arm = C_β − C_0 (→ W_α)</text>


<text x="140" y="200" font-size="13" font-style="italic" fill="#333">L (liquid)</text>

<text x="540" y="200" font-size="13" font-style="italic" fill="#333">α (solid)</text>

<text x="300" y="200" font-size="13" font-style="italic" fill="#333">L + α</text>


<path d="M 312 224 L 328 224 L 320 236 Z" fill="#111" />
</svg>

**Key Points**

- The point representing the overall composition $C_0$ acts as the fulcrum of the lever.
- The fraction of phase $\alpha$ is proportional to the arm length on the $\beta$ side (far side), and vice versa — this is the inverse relationship.
- The lever rule applies only within a two-phase (or multi-phase, with extensions) region; it is invalid in single-phase fields since there is no tie-line to construct.
- The rule is strictly valid only for equilibrium conditions where tie-lines connect true equilibrium phase compositions.

### Worked Example: Binary Isomorphous System

Consider a hypothetical Cu-Ni alloy at a given temperature within the $L + \alpha$ two-phase region:

- Overall composition: $C_0 = 35 \text{ wt\% Ni}$
- Liquidus composition at this temperature: $C_L = 32 \text{ wt\% Ni}$
- Solidus composition at this temperature: $C_\alpha = 43 \text{ wt\% Ni}$

**Calculating mass fraction of solid ($\alpha$):**

$$W_\alpha = \frac{C_0 - C_L}{C_\alpha - C_L} = \frac{35 - 32}{43 - 32} = \frac{3}{11} \approx 0.273$$

**Calculating mass fraction of liquid ($L$):**

$$W_L = \frac{C_\alpha - C_0}{C_\alpha - C_L} = \frac{43 - 35}{43 - 32} = \frac{8}{11} \approx 0.727$$

**Verification:**

$$W_\alpha + W_L = 0.273 + 0.727 = 1.000 \checkmark$$



$$W_\alpha C_\alpha + W_L C_L = (0.273)(43) + (0.727)(32) = 11.74 + 23.26 = 35.0 \text{ wt\%} \checkmark$$

This confirms mass conservation: approximately 27.3% of the alloy (by mass) exists as solid $\alpha$ phase (43 wt% Ni), and 72.7% exists as liquid (32 wt% Ni), which combine to reproduce the overall 35 wt% Ni composition.

### Application to a Eutectic System

The lever rule applies identically in eutectic-type systems, including in regions bounded by solvus lines (solid-solid two-phase fields) and at the eutectic isotherm itself (three-phase invariant reaction), with appropriate care at invariant points.

**Example — Pb-Sn system at a hypocutectic composition:**

For an alloy of $C_0 = 40 \text{ wt\% Sn}$ cooled to just above the eutectic temperature (183 °C), where:

- $\alpha$ phase composition: $C_\alpha = 18.3 \text{ wt\% Sn}$
- Eutectic liquid composition: $C_L = 61.9 \text{ wt\% Sn}$

**Primary $\alpha$ fraction:**

$$W_\alpha = \frac{C_L - C_0}{C_L - C_\alpha} = \frac{61.9 - 40}{61.9 - 18.3} = \frac{21.9}{43.6} \approx 0.502$$

**Liquid fraction (which transforms to eutectic microconstituent upon further cooling):**

$$W_L = \frac{C_0 - C_\alpha}{C_L - C_\alpha} = \frac{40 - 18.3}{43.6} \approx 0.498$$

This liquid fraction, upon cooling through the eutectic isotherm, freezes into the eutectic microconstituent ($\alpha + \beta$ lamellae), and the lever rule can be reapplied at temperatures just below the eutectic to separately compute total $\alpha$ (primary + eutectic) and total $\beta$ fractions using the extended solvus tie-line.

### Distinguishing Phase Fraction vs. Microconstituent Fraction

A frequently confused distinction in eutectic and eutectoid systems: the lever rule computed across the **full two-phase tie-line** just below the eutectic temperature gives **total phase fractions** ($W_\alpha^{total}$, $W_\beta^{total}$), treating the microstructure only in terms of its two constituent phases regardless of morphology.

A **separate application** of the lever rule using only the liquidus/eutectic segment (from $C_\alpha$ to $C_{eutectic}$) gives the fraction of **primary (proeutectic) phase** versus the fraction of material that was liquid at the eutectic temperature and transformed into the **eutectic microconstituent**.

$$W_{\text{proeutectic } \alpha} = \frac{C_{eutectic} - C_0}{C_{eutectic} - C_\alpha}$$



$$W_{\text{eutectic microconstituent}} = \frac{C_0 - C_\alpha}{C_{eutectic} - C_\alpha}$$

These two calculations (total phase amount vs. microconstituent amount) use different endpoint compositions and answer different metallurgical questions — total phase fraction concerns composition/thermodynamics, while microconstituent fraction concerns microstructural morphology relevant to mechanical properties.

### Extension: The Lever Rule in Mole Fraction vs. Mass Fraction

The lever rule as derived above uses mass (weight) fractions and mass-percent compositions, which is the standard convention in metallurgical phase diagrams. An equivalent form exists using mole fractions, applicable when working with molar thermodynamic quantities (e.g., Gibbs free energy composition diagrams):

$$X_\alpha = \frac{X_\beta^{diagram} - X_0}{X_\beta^{diagram} - X_\alpha^{diagram}}$$

where $X$ denotes mole fraction. Converting between mass fraction and mole fraction requires the atomic/molecular weights of the components:

$$X_i = \frac{(W_i / M_i)}{\sum_j (W_j / M_j)}$$

[Inference] Some texts apply the lever rule directly to Gibbs free energy–composition curves at a common tangent construction to determine equilibrium phase fractions thermodynamically, which is mathematically equivalent to the geometric tie-line method but derived from chemical potential equality rather than direct mass balance.

### Limitations and Validity Conditions

The lever rule carries several important constraints:

1. **Equilibrium assumption**: Valid only under conditions of complete thermodynamic (or local) equilibrium — i.e., the phase diagram tie-line compositions reflect true equilibrium solubility limits at that temperature. Under non-equilibrium (fast) cooling, actual phase compositions deviate (e.g., coring/microsegregation in cast alloys), and the lever rule as applied to equilibrium diagrams will not accurately predict actual phase fractions.
2. **Binary system restriction**: The simple two-point tie-line form applies strictly to binary (two-component) systems. For ternary and higher-order systems, the direct analog is the tie-triangle method or requires more complex mass-balance constructions on isothermal sections.
3. **Two-phase field only**: Cannot be applied within single-phase regions (undefined, since no tie-line exists) or directly at three-phase invariant points without decomposing the problem into separate two-phase segments (as shown in the eutectic microconstituent example above).
4. **Behavior may vary** with the accuracy of the underlying phase diagram data (e.g., CALPHAD-derived vs. experimentally determined boundaries), and small errors in reading solidus/liquidus compositions from a diagram propagate directly into fraction calculations, particularly problematic when $C_\alpha$ and $C_\beta$ are close together (long tie-lines give more accurate results than short ones).

### Relationship to the Gibbs Phase Rule

The lever rule operates within the degrees-of-freedom framework established by the Gibbs phase rule ($F = C - P + 1$ for condensed binary systems at constant pressure). Within a two-phase field ($P = 2$) of a binary system ($C = 2$), $F = 1$, meaning that once temperature is fixed, both phase compositions are uniquely determined by the phase boundaries — this is precisely what permits the tie-line (and hence lever rule) construction to be well-defined at any given temperature.

### Common Errors in Application

**Key Points**

- Inverting the lever arms (using the near arm instead of the far arm) is the most frequent calculation error — always remember phase fraction is proportional to the **opposite** arm.
- Using compositions read at the wrong temperature (not matching the tie-line for the stated condition).
- Applying the lever rule across a two-phase gap when the alloy composition actually lies within a single-phase or three-phase region at that temperature.
- Confusing weight percent and atomic percent axes when the diagram provides both scales.
- Forgetting to distinguish total phase fraction from microconstituent fraction in eutectic/eutectoid analyses (see above).

**Related Topics**

- Phase diagrams: isomorphous, eutectic, eutectoid, and peritectic systems
- Tie-lines and degrees of freedom (Gibbs phase rule)
- Coring and microsegregation under non-equilibrium solidification (Scheil equation)
- Microconstituent identification (proeutectoid ferrite/cementite, pearlite fraction calculations in Fe-Fe₃C)
- Ternary phase diagrams and the tie-triangle mass-balance method
- CALPHAD methods and computed phase diagrams
- Common tangent construction on Gibbs free energy–composition curves