## Crystal Field Theory


### Overview

Crystal field theory (CFT) is an electrostatic model that explains how the energies of a transition metal's $d$ orbitals split when surrounded by ligands, treated as point negative charges (or dipoles) generating an electric field around the metal center. Despite its simplified electrostatic assumptions — ligands are not literally point charges, and covalent metal–ligand interactions are neglected — CFT successfully accounts for many observed properties of coordination complexes: color, magnetism, geometric preferences, and relative thermodynamic/kinetic stability.

### Origin of $d$-Orbital Splitting

**Free Ion vs. Spherical Field**

In an isolated (gaseous) transition metal ion, all five $d$ orbitals ($d_{xy}$, $d_{xz}$, $d_{yz}$, $d_{x^2-y^2}$, $d_{z^2}$) are degenerate (equal in energy). If a hypothetical spherically symmetric field of negative charge were placed around the ion, all five orbitals would be raised in energy equally (due to electron-electron repulsion between the metal's $d$ electrons and the surrounding negative field) but would remain degenerate with one another, since a spherical field does not distinguish between orbital orientations.

**Effect of an Octahedral Field**

In a real octahedral complex, six ligands approach the metal along the $\pm x$, $\pm y$, and $\pm z$ axes. This is not a spherically symmetric arrangement: the $d_{x^2-y^2}$ and $d_{z^2}$ orbitals (collectively termed the $e_g$ set) point directly along the coordinate axes, directly toward the approaching ligands, and thus experience stronger electrostatic repulsion (higher energy); the $d_{xy}$, $d_{xz}$, and $d_{yz}$ orbitals (collectively termed the $t_{2g}$ set) point between the axes, away from the ligands, and experience comparatively weaker repulsion (lower energy). This differential repulsion splits the originally degenerate five $d$ orbitals into two energy levels.

### Octahedral Field Splitting

**The Splitting Parameter, $\Delta_o$**

The energy gap between the higher-energy $e_g$ set and lower-energy $t_{2g}$ set in an octahedral field is termed $\Delta_o$ (or $10Dq$ in an alternative notation). By convention and consistent with the "center of gravity" (barycenter) rule — the average orbital energy is preserved relative to the hypothetical spherical field — the $e_g$ orbitals are raised by $+0.6\Delta_o$ (or $+\frac{3}{5}\Delta_o$) and the $t_{2g}$ orbitals are lowered by $-0.4\Delta_o$ (or $-\frac{2}{5}\Delta_o$) relative to the spherical-field baseline.

**Factors Affecting $\Delta_o$ Magnitude**

- **Ligand identity (spectrochemical series)**: different ligands produce different field strengths, empirically ranked in the spectrochemical series (approximately, from weak to strong field): $\text{I}^- < \text{Br}^- < \text{Cl}^- < \text{F}^- < \text{OH}^- < \text{H}_2\text{O} < \text{NH}_3 < \text{en} < \text{NO}_2^- < \text{CN}^- \approx \text{CO}$. Stronger-field ligands produce a larger $\Delta_o$ splitting.
- **Metal oxidation state**: higher metal oxidation state generally increases $\Delta_o$, since a higher positive charge draws ligands closer, increasing the electrostatic interaction and orbital splitting.
- **Metal identity and period**: $\Delta_o$ generally increases down a transition metal group (3d < 4d < 5d), attributed primarily to the larger radial extent of $4d$/$5d$ orbitals allowing greater orbital overlap with ligand orbitals.

### High-Spin vs. Low-Spin Complexes

**The Pairing Energy Competition**

For octahedral complexes with $d^4$ through $d^7$ configurations, electrons filling the $d$ orbitals face a competition between two energetic factors: pairing energy ($P$, the energy cost of placing two electrons in the same orbital, due to electron-electron repulsion) and the crystal field splitting energy ($\Delta_o$, the energy cost of placing an electron in the higher-energy $e_g$ set rather than the lower-energy $t_{2g}$ set).

- **Weak-field (high-spin) complexes**: when $\Delta_o < P$, it is energetically cheaper to place electrons in the higher-energy $e_g$ orbitals (following Hund's rule, maximizing unpaired electrons) than to pair them within the lower $t_{2g}$ set, resulting in the maximum possible number of unpaired electrons for the given $d^n$ configuration.
- **Strong-field (low-spin) complexes**: when $\Delta_o > P$, it is energetically cheaper to pair electrons within the lower-energy $t_{2g}$ set before populating the higher-energy $e_g$ set, resulting in fewer unpaired electrons than the corresponding high-spin arrangement.

This distinction is only relevant for $d^4$–$d^7$ configurations; $d^1$–$d^3$ and $d^8$–$d^{10}$ configurations give only a single possible electron arrangement regardless of field strength, since there is no ambiguity in orbital filling for these electron counts.

**Example: $d^6$ Octahedral Complexes**

- High-spin $d^6$: $t_{2g}^4 e_g^2$, giving 4 unpaired electrons.
- Low-spin $d^6$: $t_{2g}^6 e_g^0$, giving 0 unpaired electrons (diamagnetic).

$[\text{Fe(H}_2\text{O})_6]^{2+}$ (weak-field ligand, high-spin, paramagnetic) and $[\text{Fe(CN)}_6]^{4-}$ (strong-field ligand, low-spin, diamagnetic) are commonly cited illustrative examples of this contrast for the same $d^6$ metal ion, $\text{Fe}^{2+}$.

### Crystal Field Stabilization Energy (CFSE)

**Definition and Calculation**

Crystal field stabilization energy quantifies the net energetic stabilization gained by a particular $d$-electron configuration relative to the hypothetical unsplit (spherical field) baseline:

$$\text{CFSE} = (-0.4 \times n_{t_{2g}} + 0.6 \times n_{e_g}) \, \Delta_o + n_{\text{pairs}} \, P$$

where $n_{t_{2g}}$ and $n_{e_g}$ are the number of electrons in each set. This quantity correlates with (though does not exclusively determine) the observed thermodynamic stability, lattice/hydration energies, and certain kinetic properties (e.g., substitution reaction rates) of transition metal complexes across a series.

### Tetrahedral and Square Planar Fields

**Tetrahedral Splitting**

In a tetrahedral field (four ligands at alternating corners of a cube surrounding the metal), the splitting pattern is inverted relative to octahedral: the orbitals pointing more directly at the ligands ($d_{xy}$, $d_{xz}$, $d_{yz}$, now labeled $t_2$) are raised in energy, while $d_{x^2-y^2}$ and $d_{z^2}$ (labeled $e$) are lowered. The overall splitting magnitude $\Delta_t$ is smaller than $\Delta_o$ for comparable metal/ligand systems — as a general approximation, $\Delta_t \approx \frac{4}{9}\Delta_o$ — because there are fewer ligands (four rather than six) and none point directly along the orbital lobe axes, reducing the maximum possible orbital-ligand electrostatic interaction. Because $\Delta_t$ is almost always smaller than the pairing energy $P$, essentially all tetrahedral complexes are high-spin.

**Square Planar Splitting**

Square planar geometry (commonly adopted by $d^8$ metal ions with strong-field ligands, e.g., $\text{Pt}^{2+}$, $\text{Pd}^{2+}$, low-spin $\text{Ni}^{2+}$) can be conceptually derived by removing the two axial ligands from an octahedral arrangement, causing further splitting of both the $e_g$ and $t_{2g}$ sets into four distinct energy levels, with the $d_{x^2-y^2}$ orbital (pointing directly at the four remaining in-plane ligands) raised to the highest energy.

### Comparative Splitting Diagram

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 600 350">
<text x="150" y="20" font-size="14" font-weight="bold">Octahedral vs. Tetrahedral d-Orbital Splitting (svg_diagram)</text>
<line x1="60" y1="300" x2="60" y2="60" stroke="black" stroke-width="1.5" />
<text x="20" y="180" font-size="12" transform="rotate(-90 20 180)">Energy</text>
<text x="100" y="320" font-size="13" font-weight="bold">Octahedral</text>
<line x1="90" y1="130" x2="180" y2="130" stroke="blue" stroke-width="3" />
<text x="190" y="135" font-size="12">eg (+0.6Δo)</text>
<line x1="90" y1="220" x2="140" y2="220" stroke="red" stroke-width="3" />
<line x1="140" y1="220" x2="180" y2="220" stroke="red" stroke-width="3" />
<text x="190" y="225" font-size="12">t2g (-0.4Δo)</text>
<line x1="90" y1="175" x2="180" y2="175" stroke="gray" stroke-dasharray="2,2" />
<text x="190" y="178" font-size="11" fill="gray">barycenter</text>
<text x="350" y="320" font-size="13" font-weight="bold">Tetrahedral</text>
<line x1="340" y1="160" x2="380" y2="160" stroke="blue" stroke-width="3" />
<line x1="380" y1="160" x2="420" y2="160" stroke="blue" stroke-width="3" />
<text x="430" y="165" font-size="12">t2 (+0.4Δt)</text>
<line x1="340" y1="200" x2="420" y2="200" stroke="red" stroke-width="3" />
<text x="430" y="205" font-size="12">e (-0.6Δt)</text>
<line x1="340" y1="180" x2="420" y2="180" stroke="gray" stroke-dasharray="2,2" />
</svg>

### Worked Example

**Example**

Calculate the CFSE (in units of $\Delta_o$) for high-spin and low-spin octahedral $d^6$ $\text{Fe}^{2+}$ complexes, ignoring pairing energy contributions for a first comparison, and explain the implication for relative stability.

**High-spin $d^6$** ($t_{2g}^4 e_g^2$):

$$\text{CFSE} = (4 \times -0.4 + 2 \times 0.6)\Delta_o = (-1.6 + 1.2)\Delta_o = -0.4\,\Delta_o$$

**Low-spin $d^6$** ($t_{2g}^6 e_g^0$):

$$\text{CFSE} = (6 \times -0.4 + 0 \times 0.6)\Delta_o = -2.4\,\Delta_o$$

The low-spin configuration provides substantially greater crystal field stabilization ($-2.4\Delta_o$ vs. $-0.4\Delta_o$) purely from orbital occupation energy. However, achieving the low-spin arrangement requires pairing two additional sets of electrons within the $t_{2g}$ orbitals relative to the high-spin case, each pairing costing energy $P$. Whether the low-spin configuration is actually favored overall depends on whether the crystal-field stabilization gain ($2.0\,\Delta_o$ difference between the two cases) exceeds the total additional pairing energy cost incurred — precisely the $\Delta_o$ vs. $P$ competition described above, and the reason $[\text{Fe(CN)}_6]^{4-}$ (strong-field $\text{CN}^-$, large $\Delta_o$) adopts the low-spin arrangement while $[\text{Fe(H}_2\text{O})_6]^{2+}$ (weak-field $\text{H}_2\text{O}$, small $\Delta_o$) adopts the high-spin arrangement.

### Applications

- **Predicting and explaining color**: $d$-$d$ electronic transitions between split $d$ orbital sets absorb specific wavelengths of visible light, with the absorbed wavelength directly related to $\Delta_o$ — larger $\Delta_o$ (stronger-field ligands) shifts absorption toward higher energy (shorter wavelength), directly explaining the characteristic and often vivid colors of transition metal complexes.
- **Predicting magnetism**: number of unpaired electrons (determined by high-spin vs. low-spin configuration) directly predicts paramagnetic vs. diamagnetic behavior, testable experimentally via magnetic susceptibility measurements.
- **Explaining geometric preferences**: strong-field $d^8$ ions preferentially adopt square planar geometry (as in many platinum and palladium catalysts) due to the substantial additional stabilization available in that specific splitting pattern.
- **Rationalizing thermodynamic/kinetic trends**: CFSE trends across a transition metal series help explain patterns in hydration energies, lattice energies, and ligand substitution reaction rates (e.g., the comparatively high kinetic inertness of low-spin $d^6$ octahedral complexes such as $[\text{Co(NH}_3)_6]^{3+}$).

### Common Pitfalls and Misconceptions

- Assuming crystal field theory accounts for covalent bonding contributions in metal-ligand interactions — CFT is a purely electrostatic (ionic) model; the related but more sophisticated ligand field theory (incorporating molecular orbital concepts) is needed to properly account for covalency, and is generally more accurate for strong-field, highly covalent ligands such as CO and CN⁻.
- Confusing the direction of splitting between octahedral and tetrahedral fields — the $e_g$/$t_{2g}$ (octahedral) and $e$/$t_2$ (tetrahedral) labels refer to different orbital sets with inverted relative energy ordering, and applying octahedral splitting logic directly to a tetrahedral complex without adjustment leads to incorrect predictions.
- Assuming high-spin vs. low-spin ambiguity applies to all $d^n$ configurations — this distinction is meaningful only for $d^4$ through $d^7$ octahedral complexes; other configurations have only one possible ground-state electron arrangement.
- Overlooking that essentially all tetrahedral complexes are high-spin, since $\Delta_t$ is characteristically much smaller than typical pairing energies — low-spin tetrahedral complexes are exceptionally rare and not a typical consideration in introductory treatments.

**Related Topics**

- Electron configurations of transition metals ($d^n$ notation as the CFT starting point)
- Coordination compounds and ligand types (spectrochemical series origin)
- Ligand field theory and molecular orbital treatments of coordination bonding
- Color and electronic spectroscopy of coordination complexes
- Magnetism: paramagnetism and diamagnetism in transition metal chemistry
- Isomerism in coordination compounds
- Jahn–Teller distortion and its relation to unevenly filled $e_g$/$t_{2g}$ sets