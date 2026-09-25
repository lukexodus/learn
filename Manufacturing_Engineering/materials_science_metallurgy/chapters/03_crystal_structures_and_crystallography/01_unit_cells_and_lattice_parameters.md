## Unit Cells and Lattice Parameters

### Definition and Fundamental Concept

A **crystal structure** is the periodic, repeating three-dimensional arrangement of atoms, ions, or molecules in a crystalline solid. Because this arrangement is periodic, the entire structure can be described by specifying the geometry of a small repeat unit and the atomic arrangement within it, rather than describing the position of every atom in the material individually.

The **space lattice** is an infinite, three-dimensional array of points, each of which has identical surroundings to every other point in the array. The **unit cell** is the smallest repeating structural subdivision of this crystal lattice that, when stacked together via pure translations in three dimensions, reproduces the entire lattice. The unit cell is chosen to represent the symmetry of the crystal structure, and by convention, atom centers are positioned at the corners of the unit cell (and, depending on the specific lattice type, additional positions at face centers or the body center).

### Lattice Parameters

The geometry of a unit cell is fully specified by six **lattice parameters** (also called lattice constants):

- Three edge lengths: $a$, $b$, and $c$
- Three interaxial angles: $\alpha$ (between $b$ and $c$), $\beta$ (between $a$ and $c$), and $\gamma$ (between $a$ and $b$)

These six parameters define the shape and size of the unit cell and, by extension, the entire crystal lattice, since translation of the unit cell along its three edge directions by integer multiples of $a$, $b$, and $c$ reproduces the full lattice.

This diagram illustrates a generalized unit cell with its lattice parameters labeled:

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 420 340">
<text x="210" y="25" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Generalized Unit Cell (svg_diagram)</text>
<polygon points="100,260 100,140 180,100 180,220" fill="#dceeff" opacity="0.5" stroke="none" />
<line x1="100" y1="260" x2="280" y2="260" stroke="#1a1a1a" stroke-width="2" />
<line x1="100" y1="260" x2="100" y2="140" stroke="#1a1a1a" stroke-width="2" />
<line x1="100" y1="260" x2="180" y2="220" stroke="#1a1a1a" stroke-width="2" />
<line x1="280" y1="260" x2="280" y2="140" stroke="#1a1a1a" stroke-width="2" />
<line x1="280" y1="260" x2="360" y2="220" stroke="#1a1a1a" stroke-width="2" />
<line x1="100" y1="140" x2="280" y2="140" stroke="#1a1a1a" stroke-width="2" />
<line x1="100" y1="140" x2="180" y2="100" stroke="#1a1a1a" stroke-width="2" />
<line x1="280" y1="140" x2="360" y2="100" stroke="#1a1a1a" stroke-width="2" />
<line x1="180" y1="220" x2="360" y2="220" stroke="#1a1a1a" stroke-width="2" />
<line x1="180" y1="220" x2="180" y2="100" stroke="#1a1a1a" stroke-width="2" />
<line x1="360" y1="220" x2="360" y2="100" stroke="#1a1a1a" stroke-width="2" />
<line x1="180" y1="100" x2="360" y2="100" stroke="#1a1a1a" stroke-width="2" />
<circle cx="100" cy="260" r="5" fill="#c0392b" />
<circle cx="280" cy="260" r="5" fill="#c0392b" />
<circle cx="100" cy="140" r="5" fill="#c0392b" />
<circle cx="280" cy="140" r="5" fill="#c0392b" />
<circle cx="180" cy="220" r="5" fill="#c0392b" />
<circle cx="360" cy="220" r="5" fill="#c0392b" />
<circle cx="180" cy="100" r="5" fill="#c0392b" />
<circle cx="360" cy="100" r="5" fill="#c0392b" />
<text x="185" y="278" font-size="13" font-style="italic">a</text>
<text x="88" y="200" font-size="13" font-style="italic">c</text>
<text x="145" y="245" font-size="13" font-style="italic">b</text>
<text x="110" y="225" font-size="11" font-style="italic" fill="#2a7fd4">α</text>
<text x="115" y="150" font-size="11" font-style="italic" fill="#2a7fd4">β</text>
<text x="130" y="255" font-size="11" font-style="italic" fill="#2a7fd4">γ</text>
</svg>

### The Seven Crystal Systems

The relative magnitudes of $a$, $b$, $c$ and the values of $\alpha$, $\beta$, $\gamma$ define seven possible **crystal systems**, each representing a distinct combination of lattice parameter relationships:

| Crystal System | Axial Relationships | Interaxial Angles |
| --- | --- | --- |
| Cubic | $a = b = c$ | $\alpha = \beta = \gamma = 90°$ |
| Tetragonal | $a = b \neq c$ | $\alpha = \beta = \gamma = 90°$ |
| Orthorhombic | $a \neq b \neq c$ | $\alpha = \beta = \gamma = 90°$ |
| Rhombohedral (Trigonal) | $a = b = c$ | $\alpha = \beta = \gamma \neq 90°$ |
| Hexagonal | $a = b \neq c$ | $\alpha = \beta = 90°$, $\gamma = 120°$ |
| Monoclinic | $a \neq b \neq c$ | $\alpha = \gamma = 90° \neq \beta$ |
| Triclinic | $a \neq b \neq c$ | $\alpha \neq \beta \neq \gamma \neq 90°$ |

**Key Points**

- Cubic is the crystal system with the highest degree of symmetry (all edges equal, all angles 90°)
- Triclinic has the lowest symmetry (all edges and all angles different)
- Combining the seven crystal systems with lattice centering possibilities (simple, body-centered, face-centered, base-centered) generates the **14 Bravais lattices**, which represent all possible unique space lattices

### Lattice Parameters of the Cubic System

The cubic system is the simplest and most symmetric, with $a = b = c$ and $\alpha = \beta = \gamma = 90°$, so it requires only a single lattice parameter, $a$ (the cube edge length), to fully define the unit cell geometry. The three cubic Bravais lattices of primary importance in materials science are:

- **Simple cubic (SC)**: atoms at the 8 corners only
- **Body-centered cubic (BCC)**: atoms at the 8 corners plus 1 atom at the body center
- **Face-centered cubic (FCC)**: atoms at the 8 corners plus 1 atom at the center of each of the 6 faces

For these cubic structures, the lattice parameter $a$ can be related to the atomic radius $R$ through simple geometric relationships based on the assumption of hard, touching spheres along the close-packed direction of each structure:

$$a_{SC} = 2R$$



$$a_{BCC} = \frac{4R}{\sqrt{3}}$$



$$a_{FCC} = 2R\sqrt{2}$$

### Atoms per Unit Cell

Because unit cells share corner, edge, and face atoms with adjacent unit cells, only a fraction of each shared atom is formally "counted" as belonging to a given unit cell:

- **Corner atom**: shared among 8 unit cells → contributes $\frac{1}{8}$ to each
- **Face-centered atom**: shared between 2 unit cells → contributes $\frac{1}{2}$ to each
- **Edge atom**: shared among 4 unit cells → contributes $\frac{1}{4}$ to each
- **Body-centered atom**: entirely within 1 unit cell → contributes $1$ (fully)

Applying this to the cubic Bravais lattices:

$$N_{SC} = 8 \times \frac{1}{8} = 1 \text{ atom/cell}$$



$$N_{BCC} = \left(8 \times \frac{1}{8}\right) + 1 = 2 \text{ atoms/cell}$$



$$N_{FCC} = \left(8 \times \frac{1}{8}\right) + \left(6 \times \frac{1}{2}\right) = 4 \text{ atoms/cell}$$

### Coordination Number and Atomic Packing Factor

Two further parameters characterize the packing efficiency of a unit cell:

- **Coordination number (CN)**: the number of nearest-neighbor atoms directly touching a given atom
- **Atomic packing factor (APF)**: the fraction of unit cell volume occupied by atoms, assuming a hard-sphere model:

$$\text{APF} = \frac{\text{volume of atoms in unit cell}}{\text{total volume of unit cell}}$$

| Structure | Coordination Number | Atomic Packing Factor |
| --- | --- | --- |
| Simple Cubic (SC) | 6 | 0.52 |
| Body-Centered Cubic (BCC) | 8 | 0.68 |
| Face-Centered Cubic (FCC) | 12 | 0.74 |
| Hexagonal Close-Packed (HCP) | 12 | 0.74 |

FCC and HCP share the same coordination number and APF (0.74) because both represent the two possible stacking sequences (ABCABC... and ABAB..., respectively) that achieve the theoretical maximum packing density for equal-sized spheres.

### Theoretical Density from Unit Cell Data

Lattice parameters and atoms-per-cell counts allow calculation of a material's theoretical density, $\rho$:

$$\rho = \frac{n A}{V_C N_A}$$

where $n$ is the number of atoms per unit cell, $A$ is the atomic weight, $V_C$ is the unit cell volume, and $N_A$ is Avogadro's number ($6.022 \times 10^{23} \text{ atoms/mol}$).

**Example**: For BCC iron, with $a = 0.2866\ \text{nm}$, $n = 2$, and atomic weight $A = 55.85\ \text{g/mol}$:

$$V_C = a^3 = (2.866 \times 10^{-8}\ \text{cm})^3 = 2.355 \times 10^{-23}\ \text{cm}^3$$



$$\rho = \frac{(2)(55.85)}{(2.355 \times 10^{-23})(6.022 \times 10^{23})} \approx 7.87\ \text{g/cm}^3$$

This closely matches the experimentally measured density of iron. [Unverified] Small discrepancies between calculated theoretical density and experimentally measured density in real materials are generally attributed to the presence of point defects (vacancies), impurities, or measurement/rounding precision in the input lattice parameter and atomic weight values, though the exact magnitude of discrepancy varies by material and measurement method.

### Related Topics

- Metallic Crystal Structures (FCC, BCC, HCP)
- The Seven Crystal Systems and 14 Bravais Lattices
- Crystallographic Points, Directions, and Planes
- Miller Indices
- Density Computations from Crystal Structure
- Polymorphism and Allotropy
- Single Crystals versus Polycrystalline Materials
- X-Ray Diffraction and Crystal Structure Determination