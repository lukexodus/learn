## Centroids and Moments of Inertia


### Definition and Scope

Centroids and moments of inertia are geometric properties of shapes (lines, areas, and volumes) that quantify how that geometry is distributed in space relative to a reference axis or point. In statics and subsequent mechanics of materials, these properties are essential for locating the effective point of application of distributed forces (centroids), and for quantifying a cross-section's resistance to bending and torsional deformation (moments of inertia) — making them foundational to both equilibrium analysis involving distributed loads and later structural design calculations.

### Centroids

**Definition**

The **centroid** of an area, line, or volume is the geometric center — the point at which the entire geometric "quantity" (area, length, or volume) could be considered concentrated for the purpose of computing first-moment-based properties. For a body of uniform density, the centroid coincides with the **center of mass** and (under uniform gravitational field) the **center of gravity**.

**Mathematical Definition (for an area)**

$$\bar{x} = \frac{\int x \, dA}{\int dA} = \frac{\int x \, dA}{A}, \quad \bar{y} = \frac{\int y \, dA}{A}$$

where the numerator terms $\int x\,dA$ and $\int y\,dA$ are called the **first moments of area** about the y-axis and x-axis, respectively.

**Method of Composite Shapes**

For practical engineering shapes composed of simple geometric elements (rectangles, triangles, circles, semicircles), the centroid is found by decomposing the shape into these standard elements and applying:

$$\bar{x} = \frac{\sum \bar{x}_i A_i}{\sum A_i}, \quad \bar{y} = \frac{\sum \bar{y}_i A_i}{\sum A_i}$$

where $\bar{x}_i$, $\bar{y}_i$ are the centroid coordinates of each individual composite element, and $A_i$ is each element's area (with holes/cutouts treated as **negative area**).

**Key Points:**

- This composite-shape summation approach is the standard practical method in engineering applications, avoiding direct integration for shapes that can be decomposed into tabulated standard geometries.
- **Symmetry** provides a powerful shortcut: if a shape has an axis of symmetry, the centroid must lie on that axis (this eliminates the need to compute one or both coordinates via integration/summation for symmetric shapes).

**Standard Centroid Locations (selected common shapes)**

| Shape | Centroid Location (from reference edge/point) |
| --- | --- |
| Rectangle (base $b$, height $h$) | $\bar{x} = b/2$, $\bar{y} = h/2$ (from corner) |
| Right triangle (base $b$, height $h$) | $\bar{x} = b/3$, $\bar{y} = h/3$ (from the right-angle vertex) |
| Semicircle (radius $r$) | $\bar{y} = \dfrac{4r}{3\pi}$ from the flat diameter edge |
| Quarter circle (radius $r$) | $\bar{x} = \bar{y} = \dfrac{4r}{3\pi}$ from the right-angle corner |

**Worked Example: Composite Area Centroid**

An L-shaped area is composed of a large rectangle (width 100 mm, height 200 mm) with a smaller rectangular notch (width 40 mm, height 80 mm) removed from its upper-right corner.

| Element | Area (mm²) | $\bar{x}_i$ (mm) | $\bar{y}_i$ (mm) | $A_i\bar{x}_i$ | $A_i\bar{y}_i$ |
| --- | --- | --- | --- | --- | --- |
| Full rectangle | $100 \times 200 = 20000$ | $50$ | $100$ | $1{,}000{,}000$ | $2{,}000{,}000$ |
| Notch (negative) | $-(40 \times 80) = -3200$ | $80$ (center of notch, positioned at upper right) | $160$ | $-256{,}000$ | $-512{,}000$ |
| **Total** | $16800$ |  |  | $744{,}000$ | $1{,}488{,}000$ |

$$\bar{x} = \frac{744{,}000}{16800} = 44.3 \text{ mm}, \quad \bar{y} = \frac{1{,}488{,}000}{16800} = 88.6 \text{ mm}$$

[Illustrative example; notch position coordinates assumed for demonstration — exact centroid coordinates of the notch depend on its precise positioning within the full rectangle in a given problem.]

### Center of Gravity vs. Centroid vs. Center of Mass

**Key Points:**

- **Centroid**: A purely geometric property, dependent only on shape, independent of material or mass distribution.
- **Center of mass**: Accounts for non-uniform density — coincides with the centroid only when density is uniform throughout the body.
- **Center of gravity**: The point at which the total weight of a body may be considered to act — coincides with the center of mass under a uniform gravitational field (a valid assumption for virtually all terrestrial civil engineering applications, since gravitational field variation across a structure's dimensions is negligible).

### Moments of Inertia (Second Moments of Area)

**Definition**

The **moment of inertia of an area** (also called the second moment of area) about a given axis quantifies how the area is distributed relative to that axis, weighted by the *square* of the distance from the axis — making it especially sensitive to material located far from the reference axis.

$$I_x = \int y^2 \, dA, \quad I_y = \int x^2 \, dA$$

**Key Points:**

- Despite the name "moment of inertia" (borrowed from dynamics, where it relates to rotational mass distribution), the area moment of inertia in statics/mechanics of materials is a purely geometric property with units of length to the fourth power (e.g., mm⁴, m⁴, in⁴) — it carries no mass or force dimension.
- Physical significance: a cross-section's moment of inertia directly governs its resistance to bending deformation (via the flexure formula $\sigma = My/I$, covered in mechanics of materials) — a larger $I$ about the bending axis means greater resistance to bending for a given applied moment, which is why structural sections (I-beams, wide-flange shapes) concentrate material far from the centroidal axis to maximize $I$ for a given cross-sectional area.

**Standard Moments of Inertia (about centroidal axes, selected common shapes)**

| Shape | $I_{\bar{x}}$ (about centroidal horizontal axis) |
| --- | --- |
| Rectangle (base $b$, height $h$) | $\dfrac{bh^3}{12}$ |
| Circle (radius $r$) | $\dfrac{\pi r^4}{4}$ |
| Triangle (base $b$, height $h$) | $\dfrac{bh^3}{36}$ |
| Semicircle (radius $r$, about its own centroidal axis) | $\left(\dfrac{\pi}{8} - \dfrac{8}{9\pi}\right)r^4 \approx 0.1098\,r^4$ |

### Parallel Axis Theorem

For a composite shape built from elements whose individual centroids do not coincide with the composite shape's overall centroid, the **parallel axis theorem** transfers each element's known centroidal moment of inertia to the common reference axis:

$$I = \bar{I} + Ad^2$$

where $\bar{I}$ is the moment of inertia about the element's **own centroidal axis**, $A$ is the element's area, and $d$ is the perpendicular distance between the element's centroidal axis and the reference axis about which the composite moment of inertia is being computed.

**Key Points:**

- This theorem is essential for computing the moment of inertia of any composite cross-section (built-up shapes, standard structural sections like I-beams composed of flange and web rectangles) about the overall composite centroidal axis, since individual elements' own centroids are generally offset from the composite centroid.
- The procedure requires **two steps**: (1) locate the overall composite centroid first (using the composite centroid formula above), then (2) apply the parallel axis theorem to transfer each element's moment of inertia to that composite centroidal axis, and sum.

**Worked Example: Parallel Axis Theorem Application**

For a T-shaped cross-section composed of a flange (200 mm wide × 20 mm thick, on top) and a web (20 mm wide × 180 mm tall, centered below the flange):

**Step 1 — Composite centroid** (measuring $y$ upward from the bottom of the web):

| Element | Area (mm²) | $\bar{y}_i$ (mm) | $A_i\bar{y}_i$ |
| --- | --- | --- | --- |
| Flange | $200 \times 20 = 4000$ | $180 + 10 = 190$ | $760{,}000$ |
| Web | $20 \times 180 = 3600$ | $90$ | $324{,}000$ |
| **Total** | $7600$ |  | $1{,}084{,}000$ |

$$\bar{y} = \frac{1{,}084{,}000}{7600} = 142.6 \text{ mm (from bottom of web)}$$

**Step 2 — Parallel axis theorem for each element:**

Flange: $\bar{I}_{flange} = \dfrac{200(20)^3}{12} = 133{,}333 \text{ mm}^4$; $d_{flange} = 190 - 142.6 = 47.4$ mm

$$I_{flange} = 133{,}333 + 4000(47.4)^2 = 133{,}333 + 8{,}989{,}056 = 9{,}122{,}389 \text{ mm}^4$$

Web: $\bar{I}_{web} = \dfrac{20(180)^3}{12} = 9{,}720{,}000 \text{ mm}^4$; $d_{web} = 142.6 - 90 = 52.6$ mm

$$I_{web} = 9{,}720{,}000 + 3600(52.6)^2 = 9{,}720{,}000 + 9{,}964{,}944 = 19{,}684{,}944 \text{ mm}^4$$

**Total composite moment of inertia:**

$$I_{\bar{x}} = 9{,}122{,}389 + 19{,}684{,}944 = 28{,}807{,}333 \text{ mm}^4 \approx 28.8 \times 10^6 \text{ mm}^4$$

### Polar Moment of Inertia

$$J_O = \int r^2 \, dA = \int (x^2+y^2)\,dA = I_x + I_y$$

**Key Points:**

- Quantifies resistance to **torsional** deformation about an axis perpendicular to the plane of the area (relevant for circular shafts in torsion, covered in mechanics of materials).
- For a circular cross-section, $J_O = I_x + I_y = \dfrac{\pi r^4}{4} + \dfrac{\pi r^4}{4} = \dfrac{\pi r^4}{2}$.

### Product of Inertia

$$I_{xy} = \int xy \, dA$$

**Key Points:**

- Unlike $I_x$ and $I_y$ (always positive, since they involve squared distances), the product of inertia $I_{xy}$ can be positive, negative, or zero.
- $I_{xy} = 0$ automatically whenever the shape has an axis of symmetry coinciding with either the x- or y-axis — a useful shortcut avoiding unnecessary calculation for symmetric sections.
- The product of inertia becomes relevant for **unsymmetric bending** analysis and for finding **principal axes** of inertia (the orientation of axes about which the product of inertia is zero and the moments of inertia reach their maximum/minimum values) via Mohr's circle for moments of inertia — a technique directly analogous to Mohr's circle for stress/strain transformation in mechanics of materials.

### Radius of Gyration

$$k_x = \sqrt{\frac{I_x}{A}}, \quad k_y = \sqrt{\frac{I_y}{A}}$$

**Key Points:** The radius of gyration represents the distance from the reference axis at which the entire area could be concentrated as a thin strip while producing the same moment of inertia as the actual distributed area — this quantity appears directly in **column buckling** analysis (slenderness ratio $L/k$, covered in mechanics of materials/structural design), making it a practically important derived property beyond its purely geometric definition.

### Illustration: Parallel Axis Theorem Concept

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 500 280">
<title>Parallel Axis Theorem (svg_diagram)</title>
<rect width="500" height="280" fill="#ffffff" />
<rect x="150" y="80" width="200" height="60" fill="#dbeafe" stroke="#1a56db" stroke-width="2" />
<line x1="100" y1="110" x2="400" y2="110" stroke="#1a56db" stroke-width="2" stroke-dasharray="5,3" />
<text x="405" y="115" fill="#1a56db" font-size="13" font-family="sans-serif">centroidal axis (I-bar)</text>
<line x1="100" y1="220" x2="400" y2="220" stroke="#c81e1e" stroke-width="2" stroke-dasharray="5,3" />
<text x="405" y="225" fill="#c81e1e" font-size="13" font-family="sans-serif">reference axis</text>
<line x1="120" y1="110" x2="120" y2="220" stroke="#0f7a3d" stroke-width="2" />
<polygon points="120,220 114,205 126,205" fill="#0f7a3d" />
<text x="130" y="170" fill="#0f7a3d" font-size="14" font-family="sans-serif">d</text>
<text x="180" y="55" fill="#333" font-size="14" font-family="sans-serif">I = I-bar + A·d²</text>
</svg>

### Applications in Statics and Beyond

**Key Points:**

- **In statics directly**: centroids locate the resultant of distributed loads (replacing a distributed load with an equivalent point load at the load diagram's centroid, for computing external support reactions — see Free Body Diagrams), and centroids of submerged surfaces are essential for computing resultant hydrostatic forces on dams, retaining structures, and submerged gates.
- **Looking ahead to mechanics of materials**: moments of inertia are directly required in the flexure formula ($\sigma = Mc/I$) for bending stress, the shear formula ($\tau = VQ/Ib$) for shear stress, and deflection calculations (via $EI$, the flexural rigidity) — making accurate computation of cross-sectional moment of inertia a prerequisite for essentially all subsequent beam design and analysis.
- **In structural design**: radius of gyration and moment of inertia about the weak axis directly govern a compression member's buckling capacity, making cross-sectional shape selection (maximizing $I$ for a given area, as in I-beams and hollow sections) a central structural efficiency consideration.

### Related Topics

- Free Body Diagrams
- Equilibrium of Particles and Rigid Bodies
- Distributed Loads and Hydrostatic Force Resultants
- Flexure Formula and Bending Stress (Mechanics of Materials)
- Shear Stress in Beams (Mechanics of Materials)
- Buckling of Compression Members
- Mohr's Circle for Moments of Inertia and Principal Axes