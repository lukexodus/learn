## Miller Indices for Directions and Planes

### Fundamental Concept

**Miller indices** are a standardized notational system used to specify the orientation of crystallographic directions and planes within a unit cell, relative to the crystal's coordinate axes. Because crystal properties (mechanical, optical, electrical) often vary depending on crystallographic orientation — a phenomenon called **anisotropy** — a consistent, unambiguous method for identifying specific directions and planes is essential for describing structure-property relationships, slip systems, and diffraction phenomena.

### Miller Indices for Crystallographic Directions

A crystallographic direction is defined as a line vector between two points in the lattice, expressed as a set of three integer indices, conventionally written $[uvw]$, derived through the following procedure:

1. Determine the coordinates of two points that the direction vector passes through (or, more simply, subtract the coordinates of the tail point from the head point of the vector), expressed in terms of the unit cell edge lengths $a$, $b$, $c$
2. Reduce these coordinate differences to the smallest possible set of integers by clearing fractions or dividing by a common factor
3. Enclose the resulting three integers in square brackets with no commas: $[uvw]$
4. If any index is negative, indicate this with a bar over the number (e.g., $[1\bar{1}0]$ for a direction with a negative $v$ component), rather than a minus sign

**Example**: A direction vector passing through the origin $(0,0,0)$ and the point at coordinates $(1, \tfrac{1}{2}, 1)$ (in units of $a$, $b$, $c$) is first cleared of fractions by multiplying through by 2, yielding $(2, 1, 2)$, and is written as the direction $[212]$.

### Families of Equivalent Directions

Due to crystal symmetry, multiple directions with different specific indices can be **crystallographically equivalent** — meaning they have identical atomic spacing and identical properties, differing only by the choice of coordinate axis labeling. A **family of directions** groups all such equivalent directions together and is denoted with angle brackets: $\langle uvw \rangle$.

**Example**: In the cubic system, the family $\langle 100 \rangle$ includes the six individual directions $[100]$, $[010]$, $[001]$, $[\bar{1}00]$, $[0\bar{1}0]$, and $[00\bar{1}]$, all of which are equivalent by the cubic system's high symmetry.

### Miller Indices for Crystallographic Planes

A crystallographic plane is specified by three integer indices, conventionally written $(hkl)$ — in parentheses with no commas — derived through the following standard procedure:

1. Identify the intercepts of the plane with the three crystallographic axes, expressed as multiples of the unit cell edge lengths $a$, $b$, $c$ (if the plane passes through the origin, the origin must first be translated to a different corner of the unit cell)
2. Take the **reciprocals** of these three intercept values
3. Clear any fractions (without reducing to lowest integers, unlike the direction procedure) to obtain three integers
4. Enclose the resulting integers in parentheses: $(hkl)$, using a bar to indicate negative indices

**Example**: A plane intersecting the $a$, $b$, and $c$ axes at $1$, $\tfrac{1}{2}$, and $1$ (respectively, in units of the lattice parameters) has intercepts $(1, \tfrac{1}{2}, 1)$. Taking reciprocals gives $(1, 2, 1)$, which are already integers, so the plane is designated $(121)$.

A plane parallel to a given axis is considered to intercept that axis at infinity; since $\tfrac{1}{\infty} = 0$, that axis contributes an index of 0. For example, a plane parallel to the $c$-axis with intercepts at $a$ and $b$ (and infinity along $c$) has reciprocal intercepts $(1, 1, 0)$, designated $(110)$.

This diagram illustrates the (111) and (100) planes within a cubic unit cell:

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 480 300">
<text x="240" y="25" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Miller Index Planes (svg_diagram)</text>
<text x="110" y="50" text-anchor="middle" font-size="13" font-weight="bold">(100) plane</text>
<polygon points="40,220 40,100 110,70 110,190" fill="none" stroke="#1a1a1a" stroke-width="1.5" />
<line x1="40" y1="220" x2="150" y2="220" stroke="#1a1a1a" stroke-width="1.5" />
<line x1="40" y1="100" x2="150" y2="100" stroke="#1a1a1a" stroke-width="1.5" />
<line x1="110" y1="70" x2="150" y2="100" stroke="#1a1a1a" stroke-width="1.5" />
<line x1="110" y1="190" x2="150" y2="220" stroke="#1a1a1a" stroke-width="1.5" />
<line x1="150" y1="220" x2="150" y2="100" stroke="#1a1a1a" stroke-width="1.5" />
<polygon points="40,220 40,100 110,70 110,190" fill="#4a90d9" opacity="0.4" stroke="#1a4fa3" stroke-width="2" />
<text x="60" y="260" font-size="10">shaded face = (100)</text>

<text x="360" y="50" text-anchor="middle" font-size="13" font-weight="bold">(111) plane</text>

<polygon points="290,220 290,100 360,70 360,190" fill="none" stroke="`#1a1a1a`" stroke-width="1.5" />

<line x1="290" y1="220" x2="400" y2="220" stroke="`#1a1a1a`" stroke-width="1.5" />

<line x1="290" y1="100" x2="400" y2="100" stroke="`#1a1a1a`" stroke-width="1.5" />

<line x1="360" y1="70" x2="400" y2="100" stroke="`#1a1a1a`" stroke-width="1.5" />

<line x1="360" y1="190" x2="400" y2="220" stroke="`#1a1a1a`" stroke-width="1.5" />

<line x1="400" y1="220" x2="400" y2="100" stroke="`#1a1a1a`" stroke-width="1.5" />

<polygon points="290,100 400,100 290,220" fill="`#c0392b`" opacity="0.4" stroke="`#8e2e1f`" stroke-width="2" />

<text x="310" y="260" font-size="10">shaded plane = (111)</text>

</svg>

### Families of Equivalent Planes

Similarly to directions, symmetrically equivalent planes are grouped into a **family of planes**, denoted with curly braces: $\{hkl\}$.

**Example**: In the cubic system, the family $\{100\}$ includes the six faces $(100)$, $(010)$, $(001)$, $(\bar{1}00)$, $(0\bar{1}0)$, and $(00\bar{1})$.

### The Relationship Between Directions and Planes (Cubic System Only)

**[Inference — cubic-specific relationship]** For crystals belonging to the cubic system only, a direction $[hkl]$ is always **perpendicular** to the plane $(hkl)$ having the same indices. This convenient relationship does **not** generally hold for non-cubic crystal systems, where the geometric relationship between a direction and the plane of the same index depends on the specific axial lengths and angles of that crystal system.

### Miller-Bravais Indices for Hexagonal Crystals

Because the hexagonal crystal system has a unique three-fold (or six-fold) symmetry about the $c$-axis that is not well described by only three indices, a modified four-index system called **Miller-Bravais indices** is used for hexagonal crystals, denoted $(hkil)$ for planes and $[uvtw]$ for directions. Three of the four indices ($h$, $k$, $i$ for planes) refer to three axes in the basal plane spaced 120° apart, while the fourth ($l$) refers to the vertical $c$-axis. The third basal-plane index is redundant with (and calculable from) the first two, according to the relationship:

$$i = -(h + k)$$

This redundant fourth index ensures that crystallographically equivalent planes related by the hexagonal symmetry have Miller-Bravais indices that are simple permutations of one another, which is not the case with the three-index Miller system applied to hexagonal crystals.

### Applications of Miller Indices

Miller indices are foundational to several key areas of materials science:

- **Slip systems**: plastic deformation in crystalline solids occurs preferentially on specific close-packed planes along specific close-packed directions, together defined by a Miller index plane/direction combination (e.g., $\{111\}\langle110\rangle$ slip in FCC metals)
- **X-ray diffraction**: Bragg's law relates the diffraction angle to the interplanar spacing $d_{hkl}$ of a specific $(hkl)$ plane family, allowing crystal structure determination
- **Anisotropy of properties**: elastic modulus, electrical conductivity, and other properties can vary with crystallographic direction in single crystals, described using Miller index notation
- **Interplanar spacing calculation**: for the cubic system, the spacing between adjacent $(hkl)$ planes is given by:

$$d_{hkl} = \frac{a}{\sqrt{h^2 + k^2 + l^2}}$$

### Key Points

- Directions: $[uvw]$ (specific), $\langle uvw \rangle$ (family) — derived from coordinate differences, reduced to integers, brackets with no commas
- Planes: $(hkl)$ (specific), $\{hkl\}$ (family) — derived from reciprocal intercepts, cleared of fractions (not reduced), parentheses with no commas
- Negative indices use an overbar, not a minus sign
- In cubic crystals only, $[hkl] \perp (hkl)$
- Hexagonal crystals require four-index Miller-Bravais notation, $(hkil)$ and $[uvtw]$, due to unique axial symmetry

### Related Topics

- Unit Cells and Lattice Parameters
- Metallic Crystal Structures (FCC, BCC, HCP)
- Linear and Planar Atomic Densities
- X-Ray Diffraction and Bragg's Law
- Slip Systems and Plastic Deformation
- Anisotropy in Single Crystals
- The Seven Crystal Systems and Fourteen Bravais Lattices