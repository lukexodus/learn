## Metallic Crystal Structures: FCC, BCC, and HCP


### Fundamental Concept

Because metallic bonding is nondirectional, metal atoms behave, to a first approximation, like hard spheres of uniform radius packing together as efficiently as possible. This packing tendency causes the vast majority of common engineering metals to crystallize into one of three relatively simple, high-symmetry crystal structures: **face-centered cubic (FCC)**, **body-centered cubic (BCC)**, or **hexagonal close-packed (HCP)**.

### Face-Centered Cubic (FCC) Structure

In the FCC structure, lattice points (atom centers) are located at each of the 8 corners of the cubic unit cell and at the center of each of the 6 faces.

- **Atoms per unit cell**: $N = (8 \times \tfrac{1}{8}) + (6 \times \tfrac{1}{2}) = 4$
- **Coordination number**: 12
- **Atomic packing factor (APF)**: 0.74 (along with HCP, the maximum packing density achievable for equal-sized spheres)
- **Lattice parameter–radius relationship**: atoms touch along the face diagonal, giving $a = 2R\sqrt{2}$
- **Close-packed planes**: {111} family
- **Close-packed directions**: $\langle 110 \rangle$ family
- **Representative metals**: aluminum (Al), copper (Cu), gold (Au), silver (Ag), nickel (Ni), lead (Pb), $\gamma$-iron (austenite, stable at elevated temperature)

### Body-Centered Cubic (BCC) Structure

In the BCC structure, lattice points are located at each of the 8 corners of the cubic unit cell plus one additional atom at the body center.

- **Atoms per unit cell**: $N = (8 \times \tfrac{1}{8}) + 1 = 2$
- **Coordination number**: 8
- **Atomic packing factor (APF)**: 0.68
- **Lattice parameter–radius relationship**: atoms touch along the body diagonal, giving $a = \dfrac{4R}{\sqrt{3}}$
- **Close-packed directions**: $\langle 111 \rangle$ family (BCC has no truly close-packed planes, unlike FCC and HCP)
- **Representative metals**: iron ($\alpha$-ferrite, room temperature), chromium (Cr), tungsten (W), molybdenum (Mo), vanadium (V), sodium (Na)

### Hexagonal Close-Packed (HCP) Structure

The HCP unit cell is most commonly represented as a hexagonal prism. The conventional HCP unit cell (a smaller, primitive-equivalent cell used for atom counting) contains atoms at the 12 corners of the top and bottom hexagonal faces, 2 face-center atoms on the top and bottom hexagonal faces, and 3 interior atoms positioned between the top and bottom planes.

- **Atoms per unit cell**: $N = 6$ (in the full hexagonal prism representation commonly used for visualization; equivalent to $N = 2$ in the smaller primitive HCP cell)
- **Coordination number**: 12
- **Atomic packing factor (APF)**: 0.74 (identical to FCC)
- **Ideal $c/a$ ratio**: 1.633 (the theoretical ratio of unit cell height $c$ to basal edge length $a$ for ideal hard-sphere packing; real HCP metals typically deviate somewhat from this ideal value)
- **Close-packed plane**: the basal (0001) plane
- **Representative metals**: titanium (Ti), magnesium (Mg), zinc (Zn), cobalt (Co), zirconium (Zr), cadmium (Cd)

This diagram compares the atom arrangement of the three principal metallic crystal structures:

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 500 380">
<text x="250" y="25" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">FCC, BCC, HCP Comparison (svg_diagram)</text>
<text x="90" y="55" text-anchor="middle" font-size="13" font-weight="bold">FCC</text>
<polygon points="40,220 40,120 100,90 100,190" fill="none" stroke="#1a1a1a" stroke-width="1.5" />
<line x1="40" y1="220" x2="140" y2="220" stroke="#1a1a1a" stroke-width="1.5" />
<line x1="40" y1="120" x2="140" y2="120" stroke="#1a1a1a" stroke-width="1.5" />
<line x1="100" y1="90" x2="140" y2="120" stroke="#1a1a1a" stroke-width="1.5" />
<line x1="100" y1="190" x2="140" y2="220" stroke="#1a1a1a" stroke-width="1.5" />
<line x1="140" y1="220" x2="140" y2="120" stroke="#1a1a1a" stroke-width="1.5" />
<circle cx="40" cy="220" r="7" fill="#c0392b" /><circle cx="40" cy="120" r="7" fill="#c0392b" />
<circle cx="100" cy="90" r="7" fill="#c0392b" /><circle cx="100" cy="190" r="7" fill="#c0392b" />
<circle cx="140" cy="220" r="7" fill="#c0392b" /><circle cx="140" cy="120" r="7" fill="#c0392b" />
<circle cx="90" cy="170" r="7" fill="#2a7fd4" /><circle cx="90" cy="105" r="7" fill="#2a7fd4" />
<circle cx="40" cy="170" r="7" fill="#2a7fd4" /><circle cx="140" cy="170" r="7" fill="#2a7fd4" />
<text x="90" y="255" text-anchor="middle" font-size="10">N=4, CN=12, APF=0.74</text>

<text x="250" y="55" text-anchor="middle" font-size="13" font-weight="bold">BCC</text>

<polygon points="210,220 210,120 270,90 270,190" fill="none" stroke="`#1a1a1a`" stroke-width="1.5" />

<line x1="210" y1="220" x2="310" y2="220" stroke="`#1a1a1a`" stroke-width="1.5" />

<line x1="210" y1="120" x2="310" y2="120" stroke="`#1a1a1a`" stroke-width="1.5" />

<line x1="270" y1="90" x2="310" y2="120" stroke="`#1a1a1a`" stroke-width="1.5" />

<line x1="270" y1="190" x2="310" y2="220" stroke="`#1a1a1a`" stroke-width="1.5" />

<line x1="310" y1="220" x2="310" y2="120" stroke="`#1a1a1a`" stroke-width="1.5" />

<circle cx="210" cy="220" r="7" fill="`#c0392b`" /><circle cx="210" cy="120" r="7" fill="`#c0392b`" />

<circle cx="270" cy="90" r="7" fill="`#c0392b`" /><circle cx="270" cy="190" r="7" fill="`#c0392b`" />

<circle cx="310" cy="220" r="7" fill="`#c0392b`" /><circle cx="310" cy="120" r="7" fill="`#c0392b`" />

<circle cx="260" cy="155" r="8" fill="`#27ae60`" />

<text x="260" y="255" text-anchor="middle" font-size="10">N=2, CN=8, APF=0.68</text>

<text x="420" y="55" text-anchor="middle" font-size="13" font-weight="bold">HCP</text>

<polygon points="380,120 405,105 430,120 430,150 405,165 380,150" fill="none" stroke="`#1a1a1a`" stroke-width="1.5" />

<polygon points="380,220 405,205 430,220 430,250 405,265 380,250" fill="none" stroke="`#1a1a1a`" stroke-width="1.5" />

<line x1="380" y1="120" x2="380" y2="220" stroke="`#1a1a1a`" stroke-width="1.5" />

<line x1="430" y1="120" x2="430" y2="220" stroke="`#1a1a1a`" stroke-width="1.5" />

<line x1="405" y1="105" x2="405" y2="205" stroke="`#1a1a1a`" stroke-width="1.5" />

<circle cx="380" cy="120" r="6" fill="`#c0392b`" /><circle cx="405" cy="105" r="6" fill="`#c0392b`" /><circle cx="430" cy="120" r="6" fill="`#c0392b`" />

<circle cx="380" cy="150" r="6" fill="`#c0392b`" /><circle cx="430" cy="150" r="6" fill="`#c0392b`" /><circle cx="405" cy="165" r="6" fill="`#c0392b`" />

<circle cx="380" cy="220" r="6" fill="`#c0392b`" /><circle cx="405" cy="205" r="6" fill="`#c0392b`" /><circle cx="430" cy="220" r="6" fill="`#c0392b`" />

<circle cx="380" cy="250" r="6" fill="`#c0392b`" /><circle cx="430" cy="250" r="6" fill="`#c0392b`" /><circle cx="405" cy="265" r="6" fill="`#c0392b`" />

<circle cx="405" cy="175" r="6" fill="`#2a7fd4`" />

<text x="405" y="300" text-anchor="middle" font-size="10">N=6, CN=12, APF=0.74</text>

</svg>

### Comparative Summary Table

| Property | FCC | BCC | HCP |
| --- | --- | --- | --- |
| Atoms per unit cell | 4 | 2 | 6 (hexagonal prism) |
| Coordination number | 12 | 8 | 12 |
| Atomic packing factor | 0.74 | 0.68 | 0.74 |
| $a$–$R$ relationship | $a = 2R\sqrt{2}$ | $a = 4R/\sqrt{3}$ | $a = 2R$ (basal edge) |
| Close-packed plane(s) | {111} | None (not truly close-packed) | (0001) basal |
| Close-packed direction | $\langle 110 \rangle$ | $\langle 111 \rangle$ | $\langle \bar{1}2\bar{1}0 \rangle$ (basal) |
| Slip systems (typical) | 12 (many) | 48 (many, but higher critical resolved shear stress) | Few (basal plane dominant) |
| General ductility | High | Moderate | Often lower (limited slip systems) |
| Stacking sequence | ABCABC... | — | ABAB... |

### Close-Packed Stacking: FCC vs. HCP

Both FCC and HCP achieve the maximum theoretical packing density (APF = 0.74) for equal-sized hard spheres, but differ in their **stacking sequence** of close-packed atomic planes:

- **FCC**: stacking sequence **ABCABC...**, where each of the three distinct layer positions (A, B, C) alternates in a three-layer repeat, corresponding to close-packing along the {111} planes
- **HCP**: stacking sequence **ABAB...**, where only two distinct layer positions (A, B) alternate in a two-layer repeat, corresponding to close-packing along the basal (0001) plane

[Inference] This structural distinction — despite identical packing efficiency — is generally understood to be the primary reason for differences in mechanical behavior (particularly ductility and the number of independent slip systems) between FCC and HCP metals, since the three-dimensional symmetry of the ABCABC stacking in FCC provides multiple equivalent close-packed plane orientations for dislocation slip, whereas the two-layer HCP stacking restricts easy slip predominantly to the single basal plane family.

### Influence on Mechanical Properties

- **FCC metals** (Cu, Al, Ni, Au, Ag) are generally highly **ductile**, owing to the large number of close-packed {111} planes and $\langle 110 \rangle$ slip directions available, which together provide numerous independent slip systems
- **BCC metals** (Fe, Cr, W, Mo) typically show **good strength** and can be ductile, but frequently exhibit a pronounced **ductile-to-brittle transition** with decreasing temperature, since dislocation slip in the absence of true close-packed planes requires higher stress (higher Peierls-Nabarro stress) and becomes more difficult at low temperature
- **HCP metals** (Ti, Mg, Zn, Co) often show comparatively limited ductility at room temperature, due to the small number of independent slip systems available on the basal plane alone, though some HCP metals (notably titanium and zirconium alloys) can achieve useful ductility through activation of additional (prismatic and pyramidal) slip systems and mechanical twinning

### Related Topics

- Unit Cells and Lattice Parameters
- The Seven Crystal Systems and Fourteen Bravais Lattices
- Crystallographic Points, Directions, and Planes
- Miller Indices and Miller-Bravais Indices
- Linear and Planar Atomic Densities
- Polymorphism and Allotropy
- Slip Systems and Plastic Deformation
- Density Computations from Crystal Structure