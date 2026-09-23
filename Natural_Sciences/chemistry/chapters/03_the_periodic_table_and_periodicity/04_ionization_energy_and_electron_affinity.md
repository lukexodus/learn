## Ionization Energy and Electron Affinity


### Overview

Ionization energy and electron affinity are two related periodic properties that quantify an atom's tendency to lose or gain electrons, respectively. Both properties arise from the same underlying factors—effective nuclear charge, electron shielding, and atomic radius—and together they help explain and predict chemical reactivity, bonding behavior, and the classification of elements as metals or nonmetals.

### Ionization Energy: Definition

Ionization energy (IE) is the minimum energy required to remove the outermost (most loosely held) electron from a gaseous atom or ion in its ground state.

$$\text{X(g)} \rightarrow \text{X}^+\text{(g)} + e^- \qquad \Delta E = IE_1$$

**Key Points**

- Ionization energy is always a positive value (energy must be absorbed/input) because removing an electron from an atom requires overcoming the attractive force of the nucleus.
- Ionization energy is typically expressed in kilojoules per mole (kJ/mol) or electron volts (eV).
- The process must occur in the gas phase, since ionization energies measured in solution or solid states would be affected by additional intermolecular or lattice interactions.

### Successive Ionization Energies

Atoms with multiple electrons have successive ionization energies, corresponding to the removal of the first, second, third, and subsequent electrons.

$$\text{X}^+\text{(g)} \rightarrow \text{X}^{2+}\text{(g)} + e^- \qquad \Delta E = IE_2$$

**Key Points**

- Successive ionization energies always increase ($IE_1 < IE_2 < IE_3 \ldots$), because removing each additional electron occurs from an increasingly positively charged species, so the remaining electrons are held more tightly.
- A particularly large jump in successive ionization energy occurs when an electron must be removed from a full inner (core) shell after all valence electrons have been removed, since core electrons are held much more tightly and are closer to the nucleus.

**Example**

For magnesium ($1s^2 2s^2 2p^6 3s^2$):

- $IE_1 \approx 738$ kJ/mol (removes first 3s electron)
- $IE_2 \approx 1451$ kJ/mol (removes second 3s electron)
- $IE_3 \approx 7733$ kJ/mol (large jump; removes a core 2p electron)

This large jump between $IE_2$ and $IE_3$ confirms that magnesium has exactly 2 valence electrons, consistent with its Group 2 classification.

### Successive Ionization Energy Pattern Diagram

```mermaid
flowchart LR
    A["IE1: remove valence e-"] --> B["IE2: remove 2nd valence e-"]
    B --> C["IE3: LARGE JUMP - removes core e-"]
    C --> D["IE4, IE5...: continued core removal, increasingly difficult"]
```

### Ionization Energy Trends Across the Periodic Table

**Trend Across a Period (Left to Right)**: Ionization energy generally increases.

- Effective nuclear charge ($Z_{eff}$) increases across a period as protons are added while electrons remain in the same principal shell, resulting in a stronger hold on valence electrons and thus higher energy required for removal.

**Trend Down a Group (Top to Bottom)**: Ionization energy decreases.

- Valence electrons occupy increasingly higher principal energy levels, farther from the nucleus, and are more effectively shielded by additional complete inner shells, making them easier to remove.

### Exceptions to the General Ionization Energy Trend

Two systematic exceptions occur within the otherwise increasing trend across a period, both arising from extra stability associated with certain electron configurations:

**Group 2 → Group 13 dip**

Removing an electron from a Group 13 element (e.g., boron, $2s^2 2p^1$) requires less energy than from the preceding Group 2 element (e.g., beryllium, $2s^2$), because the single p electron in Group 13 is at a slightly higher energy level and experiences less shielding penetration than the paired, lower-energy s electrons.

**Group 15 → Group 16 dip**

Removing an electron from a Group 16 element (e.g., oxygen, $2s^2 2p^4$, which has one doubly-occupied p orbital) requires less energy than from the preceding Group 15 element (e.g., nitrogen, $2s^2 2p^3$, which has a stable, half-filled p subshell with three unpaired electrons), because electron-electron repulsion within the paired orbital of oxygen makes that electron comparatively easier to remove despite oxygen's higher nuclear charge.

### Ionization Energy Trend Visualization

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 600 280" font-family="sans-serif">
<text x="300" y="20" text-anchor="middle" font-size="14" font-weight="bold">First Ionization Energy Across Period 2 (svg_diagram)</text>
<line x1="60" y1="240" x2="560" y2="240" stroke="black" stroke-width="1" />
<line x1="60" y1="240" x2="60" y2="40" stroke="black" stroke-width="1" />
<text x="20" y="140" font-size="11" transform="rotate(-90 20 140)">IE (kJ/mol)</text>

<rect x="80" y="190" width="40" height="50" fill="#2980b9" opacity="0.6" />
<text x="100" y="255" text-anchor="middle" font-size="10">Li</text>
<rect x="140" y="150" width="40" height="90" fill="#2980b9" opacity="0.6" />
<text x="160" y="255" text-anchor="middle" font-size="10">Be</text>
<rect x="200" y="175" width="40" height="65" fill="#c0392b" opacity="0.6" />
<text x="220" y="255" text-anchor="middle" font-size="10">B</text>
<rect x="260" y="130" width="40" height="110" fill="#2980b9" opacity="0.6" />
<text x="280" y="255" text-anchor="middle" font-size="10">C</text>
<rect x="320" y="100" width="40" height="140" fill="#2980b9" opacity="0.6" />
<text x="340" y="255" text-anchor="middle" font-size="10">N</text>
<rect x="380" y="115" width="40" height="125" fill="#c0392b" opacity="0.6" />
<text x="400" y="255" text-anchor="middle" font-size="10">O</text>
<rect x="440" y="80" width="40" height="160" fill="#2980b9" opacity="0.6" />
<text x="460" y="255" text-anchor="middle" font-size="10">F</text>
<rect x="500" y="40" width="40" height="200" fill="#2980b9" opacity="0.6" />
<text x="520" y="255" text-anchor="middle" font-size="10">Ne</text>

<text x="220" y="170" font-size="9" fill="`#c0392b`">↓dip</text>

<text x="400" y="110" font-size="9" fill="`#c0392b`">↓dip</text>

</svg>

[Unverified] The relative bar heights shown are illustrative approximations of the established trend pattern; precise numerical IE values should be verified against a standard reference table for exact figures.

### Electron Affinity: Definition

Electron affinity (EA) is the energy change that occurs when a neutral gaseous atom gains an electron to form a negative ion (anion).

$$\text{X(g)} + e^- \rightarrow \text{X}^-\text{(g)} \qquad \Delta E = EA$$

**Key Points**

- Unlike ionization energy, electron affinity values can be either negative (energy released, exothermic, indicating the anion is more stable) or positive (energy absorbed, endothermic, indicating the anion is less stable than the neutral atom).
- A more negative electron affinity indicates a stronger attraction for an additional electron and a more stable resulting anion.
- Sign conventions for electron affinity vary between sources: some define EA as the energy released (making favorable EA positive), while others define it as the enthalpy change of the process (making favorable EA negative). [Unverified] Because of this convention inconsistency across textbooks, it is important to check which sign convention a specific source uses when interpreting electron affinity values.

### Electron Affinity Trends Across the Periodic Table

**Trend Across a Period (Left to Right)**: Electron affinity generally becomes more negative (more favorable/exothermic), following the same increasing $Z_{eff}$ logic as ionization energy.

**Trend Down a Group (Top to Bottom)**: Electron affinity generally becomes less negative (less favorable), as the added electron occupies a shell farther from the nucleus and experiences greater shielding.

**Key Points**

- Electron affinity trends are notably less regular and more prone to exceptions than ionization energy trends.
- **Noble gases** have electron affinities near zero or positive, since an added electron would need to occupy a new, higher-energy principal shell (all existing subshells being completely filled).
- **Group 15 elements** (e.g., nitrogen, phosphorus) have electron affinities that are less negative (less favorable) than expected based on the general trend, because their half-filled p subshell configuration is already relatively stable, making the addition of an extra electron (which would force pairing) energetically less favorable.
- **Group 2 elements** (alkaline earth metals) also show less negative electron affinities than expected, since their filled s subshell provides comparative stability, making electron addition to a new p subshell less favorable.

### Halogens: Highest Electron Affinities

Halogens (Group 17) generally have the most negative (most favorable) electron affinities of any group, since adding a single electron completes their valence octet, forming a highly stable anion configuration.

**Example**

Chlorine has one of the most negative electron affinity values among all elements (approximately -349 kJ/mol under standard convention), reflecting the strong thermodynamic favorability of forming Cl⁻ and completing a stable noble-gas-like electron configuration.

### Ionization Energy vs. Electron Affinity: Conceptual Comparison

| Aspect | Ionization Energy | Electron Affinity |
| --- | --- | --- |
| Process | Removing an electron | Adding an electron |
| Resulting species | Cation | Anion |
| Sign convention | Always positive (energy required) | Can be negative (favorable) or positive (unfavorable) |
| Period trend (L→R) | Increases (with exceptions) | Generally more negative (with exceptions) |
| Group trend (top→bottom) | Decreases | Generally less negative |
| Highest values | Noble gases | Halogens (most negative/favorable) |
| Lowest/most irregular | Alkali metals (lowest IE) | Noble gases, Group 2, Group 15 |

### Connection to Chemical Reactivity

Both properties directly inform how elements behave chemically:

- Elements with **low ionization energy** (alkali and alkaline earth metals) readily lose electrons, favoring cation formation and metallic, reducing behavior.
- Elements with **highly negative electron affinity** (halogens, and to a lesser extent other nonmetals) readily gain electrons, favoring anion formation and nonmetallic, oxidizing behavior.
- The combination of low ionization energy in one element and highly negative electron affinity in another drives ionic bond formation, as seen in the transfer of an electron from sodium (low IE) to chlorine (very negative EA) to form NaCl.

### Worked Example: Predicting Relative Ionization Energy

**Example**

Compare the first ionization energy of sulfur and phosphorus.

Phosphorus ($3s^2 3p^3$) has a stable, half-filled 3p subshell, making electron removal comparatively difficult. Sulfur ($3s^2 3p^4$) has one paired 3p orbital, and the repulsion within that pair makes electron removal comparatively easier, despite sulfur having a higher nuclear charge. Consequently, sulfur's first ionization energy is slightly lower than phosphorus's, representing the Group 15→16 exception to the general increasing trend.

### Common Mistakes to Avoid

- Assuming ionization energy can be negative; by definition, it is always a positive quantity, representing energy that must be input.
- Confusing electron affinity's sign convention; always check whether a given source reports EA as energy released or as an enthalpy change, since this affects whether "favorable" corresponds to a negative or positive value.
- Overlooking successive ionization energy jumps as diagnostic evidence for the number of valence electrons an element possesses.
- Forgetting the two standard exceptions (Group 2→13 and Group 15→16) to the otherwise increasing ionization energy trend across a period.
- Assuming electron affinity trends are as regular and predictable as ionization energy trends; electron affinity has more frequent and pronounced exceptions.

### Related Topics

- Periodic trends arising from atomic structure
- Trends in atomic and ionic radius
- Electronegativity and bond polarity
- Ionic bonding and electron transfer
- Electron configuration and valence electrons
- Effective nuclear charge and shielding