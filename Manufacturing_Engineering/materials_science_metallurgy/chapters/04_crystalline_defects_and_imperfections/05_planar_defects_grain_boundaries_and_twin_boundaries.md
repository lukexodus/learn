## Planar Defects: Grain Boundaries and Twin Boundaries

### Fundamental Concept

**Planar (interfacial) defects** are two-dimensional crystalline imperfections that constitute boundaries between two regions of a material possessing different crystal structures and/or crystallographic orientations. Unlike point defects (localized to single sites) or line defects (extending as dislocations through the crystal), planar defects extend across a surface within the microstructure. The principal planar defects of interest in materials science are **grain boundaries**, **twin boundaries**, **stacking faults**, and **phase boundaries**.

### Grain Boundaries

A **grain boundary** is the interface separating two adjoining grains (individual crystals) of different crystallographic orientation within a polycrystalline material. Because the crystallographic orientation changes abruptly across this interface, atoms at the grain boundary occupy a somewhat disordered, transitional configuration that accommodates the orientational mismatch between the two neighboring grains.

**Classification by misorientation angle**:

- **Low-angle grain boundaries**: the misorientation angle between adjacent grains is small (conventionally, less than approximately 10–15°). These boundaries can be described as an organized, periodic array of dislocations:
  - A **tilt boundary** (a specific type of low-angle boundary) can be represented as a simple linear array of parallel edge dislocations
  - A **twist boundary** can be represented as an array of screw dislocations
- **High-angle grain boundaries**: the misorientation angle exceeds approximately 10–15°, and the atomic structure at the boundary is considerably more disordered than at a low-angle boundary; high-angle boundaries cannot be conveniently described in terms of a simple dislocation array

This diagram illustrates the general concept of a low-angle tilt boundary formed by an array of edge dislocations:

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 400 260">
<text x="200" y="25" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Low-Angle Tilt Boundary (svg_diagram)</text>
<line x1="200" y1="50" x2="200" y2="230" stroke="#c0392b" stroke-width="1" stroke-dasharray="3,3" />
<g stroke="#333" stroke-width="1">
<line x1="60" y1="70" x2="60" y2="100" stroke="#1a1a1a" stroke-width="3" />
<line x1="100" y1="70" x2="100" y2="100" stroke="#1a1a1a" stroke-width="3" />
<line x1="140" y1="70" x2="140" y2="100" stroke="#1a1a1a" stroke-width="3" />
<line x1="180" y1="70" x2="180" y2="100" stroke="#1a1a1a" stroke-width="3" />
<line x1="220" y1="70" x2="220" y2="100" stroke="#1a1a1a" stroke-width="3" />
<line x1="260" y1="70" x2="260" y2="100" stroke="#1a1a1a" stroke-width="3" />
<line x1="300" y1="70" x2="300" y2="100" stroke="#1a1a1a" stroke-width="3" />
<line x1="340" y1="70" x2="340" y2="100" stroke="#1a1a1a" stroke-width="3" />
</g>
<g stroke="#333" stroke-width="1">
<line x1="60" y1="180" x2="60" y2="210" stroke="#1a1a1a" stroke-width="3" />
<line x1="100" y1="180" x2="100" y2="210" stroke="#1a1a1a" stroke-width="3" />
<line x1="140" y1="180" x2="140" y2="210" stroke="#1a1a1a" stroke-width="3" />
<line x1="180" y1="180" x2="180" y2="210" stroke="#1a1a1a" stroke-width="3" />
<line x1="220" y1="180" x2="220" y2="210" stroke="#1a1a1a" stroke-width="3" />
<line x1="260" y1="180" x2="260" y2="210" stroke="#1a1a1a" stroke-width="3" />
<line x1="300" y1="180" x2="300" y2="210" stroke="#1a1a1a" stroke-width="3" />
<line x1="340" y1="180" x2="340" y2="210" stroke="#1a1a1a" stroke-width="3" />
</g>
<line x1="200" y1="110" x2="200" y2="130" stroke="#c0392b" stroke-width="4" />
<line x1="240" y1="115" x2="240" y2="135" stroke="#c0392b" stroke-width="4" />
<line x1="160" y1="140" x2="160" y2="160" stroke="#c0392b" stroke-width="4" />
<text x="205" y="105" font-size="10" fill="#c0392b">extra half-planes</text>
<text x="100" y="250" font-size="11">Grain 1 (orientation A)</text>
<text x="230" y="250" font-size="11" fill="#555">↑ boundary</text>
</svg>

### Grain Boundary Energy and Interaction with Dislocations

The atomic disorder at a grain boundary means the boundary possesses an interfacial (surface) energy, comparable in nature to the surface energy at a free surface, but generally somewhat lower in magnitude since a grain boundary interfaces two crystals rather than a crystal and a vacuum. This grain boundary energy has significant consequences:

- Grain boundaries represent thermodynamically higher-energy regions than the interior of a grain, providing a driving force for **grain growth** at elevated temperature (larger grains, with proportionally less total grain boundary area per unit volume, are thermodynamically favored over many small grains)
- Grain boundaries act as effective **barriers to dislocation motion**, since a dislocation gliding within one grain must change its slip direction (and often its slip system entirely) to continue propagating into an adjacent, differently-oriented grain — this obstruction is the physical basis of **Hall-Petch strengthening**, in which yield strength, $\sigma_y$, increases with decreasing average grain diameter, $d$, according to the empirical relationship:

$$\sigma_y = \sigma_0 + k_y d^{-1/2}$$

where $\sigma_0$ and $k_y$ are material-specific constants.

- Grain boundaries are preferential sites for solid-state diffusion (grain boundary diffusion is generally faster than bulk lattice diffusion, due to the more open, disordered atomic packing at the boundary) and for the nucleation of new phases during phase transformations

### Twin Boundaries

A **twin boundary** is a specific, highly symmetric type of planar defect across which the crystal lattice on one side is a **mirror image** of the lattice on the other side, with the twin boundary itself serving as the mirror plane.

**Formation mechanisms**:

- **Mechanical (deformation) twins**: produced by mechanical shear forces during plastic deformation, typically observed in BCC and HCP metals subjected to rapid loading (e.g., shock loading) or at low temperature, where twinning can supplement limited dislocation slip as an alternative deformation mechanism
- **Annealing twins**: produced during recrystallization or grain growth following prior plastic deformation, particularly common in FCC metals with relatively low stacking-fault energy (e.g., copper, brass, austenitic stainless steel) — these twins typically appear as straight-sided bands within grains when viewed under an optical microscope

**Key Points**

- The twin boundary itself is a highly ordered, low-energy interface (lower energy than a typical high-angle grain boundary), since the mirror-symmetric atomic arrangement across a twin boundary produces comparatively little atomic disorder
- Mechanical twinning contributes to plastic deformation both directly (by reorienting a portion of the crystal, changing local slip system favorability) and indirectly (by subdividing grains, thereby providing additional barriers to subsequent dislocation motion, similar in effect to grain refinement)
- Annealing twins are microstructurally significant primarily as a metallurgical fingerprint of certain FCC alloys and generally have a comparatively modest direct effect on bulk mechanical properties compared to mechanical twins

### Stacking Faults

A **stacking fault** is a planar defect representing a localized interruption or error in the normal stacking sequence of close-packed atomic planes. As established in the discussion of close-packed structures, FCC crystals follow the stacking sequence ABCABC..., while HCP crystals follow ABAB...; a stacking fault occurs when this regular sequence is locally disrupted (for example, a local ...ABCAB**A**BCABC... sequence in an otherwise FCC crystal, introducing a brief local region resembling HCP stacking).

[Inference] Stacking faults are generally understood to be bounded by partial dislocations (dislocations with a Burgers vector smaller than a full unit lattice translation), and the energy associated with a stacking fault (the **stacking fault energy**) is a material-specific property that significantly influences deformation behavior — materials with low stacking fault energy (e.g., austenitic stainless steels, brass) tend to exhibit wide dislocation dissociation and correspondingly limited cross-slip capability, which is associated with pronounced strain hardening and a greater propensity for annealing twin formation, while materials with high stacking fault energy (e.g., aluminum) exhibit narrower dislocation dissociation and comparatively easier cross-slip.

### Phase Boundaries

A **phase boundary** is a planar interface separating two regions of differing chemical composition and/or crystal structure (i.e., two distinct phases) within a multiphase material, such as the ferrite-cementite interfaces present throughout pearlitic steel microstructures. Phase boundaries share some characteristics with grain boundaries (interfacial energy, barrier to dislocation motion) but additionally involve a compositional discontinuity, distinguishing them from grain boundaries (which separate differently-oriented but chemically identical crystals).

### Comparative Summary of Planar Defects

| Defect Type | Nature of the Interface | Relative Interfacial Energy | Key Role |
| --- | --- | --- | --- |
| Low-angle grain boundary | Organized dislocation array | Low | Minor barrier to slip |
| High-angle grain boundary | Disordered atomic transition | High | Major barrier to slip; Hall-Petch strengthening; diffusion pathway |
| Twin boundary | Mirror-symmetric lattice | Low | Deformation mechanism (mechanical twins); microstructural feature (annealing twins) |
| Stacking fault | Local stacking sequence error | Low to moderate (material-dependent) | Governs dislocation dissociation and cross-slip behavior |
| Phase boundary | Compositional/structural discontinuity | Variable | Separates distinct phases in multiphase microstructures |

### Key Points Summary

- Planar defects are two-dimensional interfaces between crystallographically or compositionally distinct regions of a material
- Grain boundaries are classified as low-angle (dislocation-array-like) or high-angle (disordered), and act as barriers to slip, enabling Hall-Petch strengthening
- Twin boundaries are mirror-symmetric interfaces, formed mechanically (deformation twins) or thermally (annealing twins during recrystallization)
- Stacking faults represent local interruptions in the normal ABCABC (FCC) or ABAB (HCP) stacking sequence, bounded by partial dislocations
- Phase boundaries additionally involve a change in chemical composition and/or crystal structure

### Related Topics

- Single Crystals versus Polycrystalline Materials
- Line Defects: Edge and Screw Dislocations
- Burgers Vector and Dislocation Motion
- Close Packed Structures and Coordination Number
- Grain Boundaries and Hall-Petch Strengthening
- Recrystallization and Grain Growth
- Strain Hardening (Cold Working)