## Color and Magnetism in Metal Complexes


### Overview

Color and magnetism in transition metal complexes both originate from the partially filled $d$-orbitals and their splitting under a ligand field. Color arises from electronic transitions between split $d$-orbitals (or charge-transfer transitions), while magnetism arises from the number and arrangement of unpaired electrons within those orbitals.

### Origin of Color: d-d Transitions

When ligands split degenerate $d$-orbitals into sets of different energy (e.g., $t_{2g}$ and $e_g$ in octahedral fields), electrons can be promoted between these sets by absorbing visible light. The complementary color observed is the color **not** absorbed.

$$\Delta E = h\nu = \frac{hc}{\lambda}$$

**Key Points**

- d-d transitions require $\Delta_o$ (or $\Delta_t$) to fall within the visible range (~400–700 nm, corresponding to ~170–300 kJ/mol)
- $d^0$ and $d^{10}$ configurations are typically colorless/white (no possible d-d transition) — e.g., $\text{TiO}_2$ ($d^0$), $\text{Zn}^{2+}$ complexes ($d^{10}$)
- Color intensity and position depend on $\Delta_o$, which depends on the metal, oxidation state, and ligand field strength (spectrochemical series)

**Color Wheel Relationship**

| Absorbed Wavelength (nm) | Absorbed Color | Observed (Complementary) Color |
| --- | --- | --- |
| 400–430 | Violet | Yellow-green |
| 430–490 | Blue | Orange |
| 490–560 | Green | Red |
| 560–580 | Yellow | Violet |
| 580–650 | Orange | Blue |
| 650–700 | Red | Green |

**Complementary Color Wheel (svg_diagram)**

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 400 400" font-family="Helvetica,Arial,sans-serif">
  <title>Complementary color wheel for absorbed vs observed color (svg_diagram)</title>
  <circle cx="200" cy="200" r="150" fill="none" stroke="#333" stroke-width="1" />
  <g font-size="12" text-anchor="middle">
    <path d="M200,200 L200,50 A150,150 0 0,1 330,125 Z" fill="#8B00FF" opacity="0.7" />
    <text x="255" y="90" fill="#000">Violet</text>
    <path d="M200,200 L330,125 A150,150 0 0,1 350,200 Z" fill="#0000FF" opacity="0.7" />
    <text x="330" y="160" fill="#fff">Blue</text>
    <path d="M200,200 L350,200 A150,150 0 0,1 300,320 Z" fill="#00AA00" opacity="0.7" />
    <text x="310" y="255" fill="#fff">Green</text>
    <path d="M200,200 L300,320 A150,150 0 0,1 200,350 Z" fill="#FFFF00" opacity="0.7" />
    <text x="245" y="335" fill="#000">Yellow</text>
    <path d="M200,200 L200,350 A150,150 0 0,1 100,320 Z" fill="#FFA500" opacity="0.7" />
    <text x="155" y="335" fill="#000">Orange</text>
    <path d="M200,200 L100,320 A150,150 0 0,1 50,200 Z" fill="#FF0000" opacity="0.7" />
    <text x="90" y="255" fill="#fff">Red</text>
    <path d="M200,200 L50,200 A150,150 0 0,1 200,50 Z" fill="#FFC0CB" opacity="0.7" />
    <text x="120" y="120" fill="#000">Red-Violet</text>
  </g>
  <circle cx="200" cy="200" r="4" fill="#333" />
  <text x="200" y="200" font-size="10" text-anchor="middle" dy="-160">Absorbed → Observed = opposite side</text>
</svg>
```

### Factors Affecting Δo and Absorption

**Spectrochemical series** (weak to strong field): $\text{I}^- < \text{Br}^- < \text{Cl}^- < \text{F}^- < \text{H}_2\text{O} < \text{NH}_3 < \text{en} < \text{NO}_2^- < \text{CN}^- < \text{CO}$

- Larger $\Delta_o$ → higher energy (shorter wavelength) absorption
- Increasing oxidation state on the metal increases $\Delta_o$ (stronger electrostatic attraction, shorter M–L bonds)
- Descending a group (3d → 4d → 5d) increases $\Delta_o$ substantially (~30–50% increase per row) due to greater orbital overlap with more diffuse $d$-orbitals

**Example**

$[\text{Ti(H}_2\text{O)}_6]^{3+}$ ($d^1$) is violet/purple, absorbing around 500 nm (green-yellow light) corresponding to the single $t_{2g}^1 \to e_g^1$ transition. Because there is only one $d$-electron and one possible transition, this is one of the cleanest examples of a simple d-d transition producing a single broad absorption band. [Inference: exact $\lambda_{max}$ varies slightly with concentration and solution conditions; the ~500 nm figure is a standard textbook reference value.]

### Selection Rules and Band Intensity

Two quantum mechanical selection rules govern the intensity of d-d transitions:

**Laporte Selection Rule**

Forbids transitions between orbitals of the same parity (g→g or u→u) in centrosymmetric complexes. Since all $d$-orbitals are gerade (g), pure d-d transitions in octahedral (centrosymmetric) complexes are formally Laporte-forbidden.

- Octahedral complexes: weak absorption (low molar absorptivity $\varepsilon$, typically 1–100 M⁻¹cm⁻¹) due to strict forbiddenness, partially relaxed by vibronic coupling (asymmetric vibrations momentarily breaking centrosymmetry)
- Tetrahedral complexes: lack a center of symmetry, so Laporte rule doesn't strictly apply — d-p orbital mixing allowed, giving more intense colors (ε typically 100–1000 M⁻¹cm⁻¹) than octahedral analogs

**Spin Selection Rule**

Forbids transitions that involve a change in total spin multiplicity ($\Delta S = 0$ required).

- Spin-forbidden transitions (e.g., high-spin $d^5$ complexes like $[\text{Mn(H}_2\text{O)}_6]^{2+}$) are extremely weak (ε < 1 M⁻¹cm⁻¹), often giving very pale or nearly colorless appearance despite being technically colored

**Relative Intensity Comparison**

| Transition Type | Typical ε (M⁻¹cm⁻¹) | Example |
| --- | --- | --- |
| Spin-forbidden, Laporte-forbidden | <1 | $[\text{Mn(H}_2\text{O)}_6]^{2+}$ (pale pink) |
| Spin-allowed, Laporte-forbidden (octahedral) | 1–100 | $[\text{Ti(H}_2\text{O)}_6]^{3+}$ |
| Spin-allowed, Laporte-allowed (tetrahedral, d-p mixing) | 100–1000 | $[\text{CoCl}_4]^{2-}$ |
| Charge-transfer | >1000–50,000 | $\text{MnO}_4^-$, $\text{CrO}_4^{2-}$ |

### Charge-Transfer (CT) Transitions

Distinct from d-d transitions, CT bands involve electron movement between metal and ligand orbitals, are Laporte- and spin-allowed, and are typically far more intense.

- **Ligand-to-metal charge transfer (LMCT)**: electron moves from filled ligand orbital to empty/partially filled metal $d$-orbital; common in complexes with metals in high oxidation states and π-donor ligands (e.g., $\text{MnO}_4^-$, intense purple, $d^0$ Mn(VII) — color arises entirely from LMCT since no d-d transition is possible)
- **Metal-to-ligand charge transfer (MLCT)**: electron moves from filled metal $d$-orbital to empty ligand π* orbital; common with π-acceptor ligands (e.g., $[\text{Ru(bipy)}_3]^{2+}$, intense orange-red, important in photochemistry/solar energy conversion)

### Magnetism: Origins

Magnetic behavior in coordination complexes arises primarily from unpaired electrons (paramagnetism) or their complete absence (diamagnetism).

**Diamagnetism**

- All electrons paired
- Weakly repelled by an external magnetic field
- Exhibited by $d^0$, low-spin $d^6$ (octahedral), $d^{10}$, and square planar $d^8$ complexes

**Paramagnetism**

- One or more unpaired electrons
- Attracted into an external magnetic field
- Magnitude quantified by the **spin-only magnetic moment**:

$$\mu_{s} = \sqrt{n(n+2)}\ \mu_B$$

where $n$ = number of unpaired electrons and $\mu_B$ is the Bohr magneton.

**Spin-Only Magnetic Moments Table**

| Unpaired Electrons ($n$) | $\mu_s$ (BM) | Example Configuration |
| --- | --- | --- |
| 0 | 0 | Low-spin $d^6$ |
| 1 | 1.73 | $d^1$, low-spin $d^5$ |
| 2 | 2.83 | $d^2$, low-spin $d^4$ |
| 3 | 3.87 | $d^3$, high-spin $d^7$ |
| 4 | 4.90 | High-spin $d^4$, $d^6$ |
| 5 | 5.92 | High-spin $d^5$ |

**Note**: The spin-only formula neglects orbital angular momentum contribution, which is significant for some $T$-term ground states (especially $t_{2g}$-configurations like $d^1, d^2, d^6, d^7$ in octahedral fields). Observed moments for these often exceed spin-only predictions due to spin-orbit coupling. [Inference: the magnitude of orbital contribution is system-dependent and best confirmed against experimental data for the specific complex.]

### High-Spin vs. Low-Spin Configurations

For octahedral $d^4$–$d^7$ complexes, two possible electron arrangements exist depending on the relative magnitude of $\Delta_o$ versus the pairing energy $P$:

$$\text{If } \Delta_o < P \Rightarrow \text{high-spin (weak field)}$$



$$\text{If } \Delta_o > P \Rightarrow \text{low-spin (strong field)}$$

**High-Spin vs Low-Spin d6 Filling (svg_diagram)**

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 480 260" font-family="Helvetica,Arial,sans-serif">
  <title>High spin versus low spin d6 octahedral electron filling (svg_diagram)</title>
  <text x="120" y="25" font-size="14" text-anchor="middle">High-spin d6 (weak field)</text>
  <line x1="60" y1="60" x2="100" y2="60" stroke="#333" stroke-width="2" />
  <line x1="110" y1="60" x2="150" y2="60" stroke="#333" stroke-width="2" />
  <text x="80" y="50" font-size="10" text-anchor="middle">↑</text>
  <text x="130" y="50" font-size="10" text-anchor="middle">↑</text>
  <text x="20" y="65" font-size="10">eg</text>

  <line x1="40" y1="140" x2="80" y2="140" stroke="#333" stroke-width="2" />
  <line x1="90" y1="140" x2="130" y2="140" stroke="#333" stroke-width="2" />
  <line x1="140" y1="140" x2="180" y2="140" stroke="#333" stroke-width="2" />
  <text x="60" y="130" font-size="10" text-anchor="middle">↑↓</text>
  <text x="110" y="130" font-size="10" text-anchor="middle">↑</text>
  <text x="160" y="130" font-size="10" text-anchor="middle">↑</text>
  <text x="10" y="145" font-size="10">t2g</text>
  <text x="90" y="190" font-size="11" text-anchor="middle">n = 4 unpaired, μ ≈ 4.90 BM</text>

  <text x="380" y="25" font-size="14" text-anchor="middle">Low-spin d6 (strong field)</text>
  <line x1="330" y1="60" x2="370" y2="60" stroke="#333" stroke-width="2" />
  <line x1="380" y1="60" x2="420" y2="60" stroke="#333" stroke-width="2" />
  <text x="15" y="0" font-size="1" />
  <text x="20" y="65" font-size="10" />

  <line x1="310" y1="140" x2="350" y2="140" stroke="#333" stroke-width="2" />
  <line x1="360" y1="140" x2="400" y2="140" stroke="#333" stroke-width="2" />
  <line x1="410" y1="140" x2="450" y2="140" stroke="#333" stroke-width="2" />
  <text x="330" y="130" font-size="10" text-anchor="middle">↑↓</text>
  <text x="380" y="130" font-size="10" text-anchor="middle">↑↓</text>
  <text x="430" y="130" font-size="10" text-anchor="middle">↑↓</text>
  <text x="280" y="145" font-size="10">t2g</text>
  <text x="380" y="190" font-size="11" text-anchor="middle">n = 0 unpaired, μ = 0 (diamagnetic)</text>
</svg>
```

**Key Points**

- High-spin/low-spin ambiguity only occurs for octahedral $d^4$ through $d^7$ configurations
- $d^1$–$d^3$ and $d^8$–$d^{10}$ have only one possible ground-state filling regardless of field strength
- Tetrahedral complexes are almost always high-spin because $\Delta_t \approx \frac{4}{9}\Delta_o$ is rarely large enough to exceed pairing energy

### Measuring Magnetic Moments

**Gouy Balance / Evans Balance Method**

Measures the change in apparent weight of a sample when placed in a magnetic field; paramagnetic samples are drawn into the field (weight increase), diamagnetic samples are repelled (weight decrease). Molar magnetic susceptibility $\chi_M$ is converted to the effective magnetic moment via:

$$\mu_{eff} = 2.828\sqrt{\chi_M T}$$

where $T$ is absolute temperature.

**SQUID Magnetometry**

Superconducting Quantum Interference Device magnetometry provides highly sensitive, temperature-dependent magnetic susceptibility measurements, essential for studying spin-crossover complexes and magnetic exchange coupling in polynuclear complexes.

### Spin-Crossover Complexes

Some $d^4$–$d^7$ octahedral complexes sit near the crossover point between high-spin and low-spin, allowing thermally, optically, or pressure-induced switching between states. This is an active research area in molecular switches and memory devices. [Inference: specific transition temperatures and mechanisms are highly compound-dependent and require literature verification.]

### Relationship Between Color and Magnetism

Both properties trace back to $d$-orbital occupation and splitting, but they are not directly correlated in a simple way — a complex can be intensely colored and diamagnetic (e.g., $\text{MnO}_4^-$, CT-based color, $d^0$ so no unpaired electrons) or weakly colored and highly paramagnetic (e.g., $[\text{Mn(H}_2\text{O)}_6]^{2+}$, pale due to spin-forbidden transitions, but $\mu \approx 5.92$ BM from 5 unpaired electrons).

**Conclusion**

Color in transition metal complexes results from d-d transitions (modulated by Laporte and spin selection rules) and charge-transfer transitions, both governed by ligand field splitting magnitude. Magnetism results directly from the number of unpaired $d$-electrons, determined by high-spin/low-spin electron configuration, itself dependent on the same $\Delta_o$ versus pairing energy competition. Together, these properties provide powerful diagnostic tools for elucidating electronic structure, oxidation state, and coordination geometry.

**Related Topics**

- Spectrochemical series and factors controlling Δo
- Tanabe-Sugano diagrams for multi-electron term splitting
- Ligand field theory and molecular orbital bonding
- Spin-crossover complexes and molecular switches
- Jahn-Teller distortion effects on electronic spectra
- Charge-transfer complexes and photochemistry ($[\text{Ru(bipy)}_3]^{2+}$)
- Curie and Curie-Weiss law in magnetochemistry
- Antiferromagnetic and ferromagnetic coupling in polynuclear complexes