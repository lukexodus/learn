## Form Tolerances


### Overview

Form tolerances control the shape of an individual feature independent of any datum reference — they are among the few GD&T characteristics that never reference a datum. Per ASME Y14.5, the four form tolerances are Flatness, Straightness, Circularity (Roundness), and Cylindricity.

### Category Summary

| Characteristic | Symbol | Feature Type | Datum Reference Allowed |
| --- | --- | --- | --- |
| Straightness | ⏤ | Line elements, axis, or surface | No |
| Flatness | ⏥ | Planar surface | No |
| Circularity | ○ | Circular cross-section | No |
| Cylindricity | ⌭ | Cylindrical surface | No |

### Flatness

**Definition:** All points of a surface must lie within two parallel planes separated by the specified tolerance value.

**Key Points**

- Applies to a single surface as a whole (not a feature of size)
- No datum reference is permitted in the feature control frame
- Can be refined with the "unit basis" or "per unit area" notation for local flatness control over a specified area

**Example**

Feature control frame: `⏥ 0.05`

A $100 \times 50$ mm surface must have all points contained within two parallel planes $0.05$ mm apart, regardless of the surface's orientation to any datum.

**Measurement Method**

- Typically verified with a CMM (surface scan) or a surface plate with a dial indicator, sweeping the full surface and recording the max-min reading

### Straightness (Surface Line Elements)

**Definition:** Each line element of a surface, taken in a specified direction, must lie within two parallel lines separated by the tolerance value.

**Key Points**

- Default application is to line elements on a surface — not the derived median line/axis
- Very common on long features like shafts, rails, and edges to control bow or wave

**Example**

Feature control frame: `⏤ 0.02` applied along the length of a shaft's surface line.

Each longitudinal line element on the cylindrical surface must fit within a $0.02$ mm tolerance zone (two parallel lines in the plane of that element).

### Straightness (Axis / Derived Median Line — Rule #1 Interaction)

**Definition:** When applied to a feature of size with the diameter symbol Ø in the tolerance value and a material condition modifier, straightness controls the derived median line (axis) rather than surface elements.

**Key Points**

- This is a special case governed by Rule #2 (or explicit modifier use) and overrides Rule #1 (envelope principle) for that feature, allowing the actual local size to vary independently of the axis straightness within the Ø tolerance zone
- Commonly applied at MMC to permit bonus tolerance, enabling functional gaging with a cylindrical gage

**Example**

Feature control frame: `⏤ Ø0.1 Ⓜ` applied to a $10$ mm pin's diameter dimension.

The derived median line of the pin must lie within a cylindrical zone of $0.1$ mm diameter at MMC (pin at $\varnothing 10.0$ mm, the largest permitted size), with bonus tolerance available as the pin's actual local size departs from MMC.

### Circularity (Roundness)

**Definition:** At any cross-section perpendicular to the axis (for a cylinder/cone) or through a common center (for a sphere), all points of the circumference must lie within two concentric circles separated by the tolerance value, radially.

**Key Points**

- Evaluated independently at each cross-section — not as a 3D envelope like cylindricity
- No datum reference permitted
- Tolerance value is a radial (not diametral) zone width unless stated otherwise

**Example**

Feature control frame: `○ 0.01`

At any single cross-section along the part's length, the circular profile must fit within an annular zone bounded by two concentric circles whose radii differ by $0.01$ mm.

**Common Causes of Out-of-Roundness**

- Lobing (odd/even number of lobes) from centerless grinding or chucking distortion
- Chatter from tool vibration during turning

### Cylindricity

**Definition:** A composite 3D tolerance requiring the entire cylindrical surface to lie within two coaxial cylinders separated radially by the tolerance value.

**Key Points**

- Cylindricity simultaneously controls circularity, straightness of surface elements, and taper of the full surface in one combined zone
- It is the most restrictive/comprehensive of the four form controls and typically the most expensive to verify and hold
- No datum reference permitted

**Example**

Feature control frame: `⌭ 0.015`

The full cylindrical surface (all circular cross-sections along its length, all longitudinal elements) must fit between two coaxial cylinders whose radii differ by $0.015$ mm.

### Form Tolerance Zone Comparison (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 780 260" font-family="Arial, sans-serif">
<text x="390" y="20" text-anchor="middle" font-size="15" font-weight="bold">Form Tolerance Zones (svg_diagram)</text>

<g>
<text x="90" y="45" text-anchor="middle" font-size="12" font-weight="bold">Flatness</text>
<line x1="30" y1="80" x2="150" y2="65" stroke="#333" stroke-width="2" />
<line x1="30" y1="110" x2="150" y2="95" stroke="#333" stroke-width="2" />
<path d="M40,75 Q90,100 140,80" stroke="#c0392b" stroke-width="2" fill="none" />
<text x="90" y="135" text-anchor="middle" font-size="10">two parallel planes</text>
</g>

<g>
<text x="290" y="45" text-anchor="middle" font-size="12" font-weight="bold">Straightness</text>
<line x1="230" y1="70" x2="350" y2="70" stroke="#333" stroke-width="2" />
<line x1="230" y1="100" x2="350" y2="100" stroke="#333" stroke-width="2" />
<path d="M235,90 Q290,72 345,88" stroke="#c0392b" stroke-width="2" fill="none" />
<text x="290" y="135" text-anchor="middle" font-size="10">two parallel lines</text>
</g>

<g>
<text x="490" y="45" text-anchor="middle" font-size="12" font-weight="bold">Circularity</text>
<circle cx="490" cy="95" r="45" stroke="#333" stroke-width="2" fill="none" />
<circle cx="490" cy="95" r="35" stroke="#333" stroke-width="2" fill="none" />
<path d="M490,60 Q525,80 520,95 Q515,120 480,128 Q455,120 460,90 Q465,65 490,60" stroke="#c0392b" stroke-width="2" fill="none" />
<text x="490" y="150" text-anchor="middle" font-size="10">concentric circles</text>
</g>

<g>
<text x="670" y="45" text-anchor="middle" font-size="12" font-weight="bold">Cylindricity</text>
<ellipse cx="670" cy="70" rx="50" ry="14" stroke="#333" stroke-width="2" fill="none" />
<ellipse cx="670" cy="70" rx="38" ry="10" stroke="#333" stroke-width="2" fill="none" />
<line x1="620" y1="70" x2="620" y2="120" stroke="#333" stroke-width="2" />
<line x1="720" y1="70" x2="720" y2="120" stroke="#333" stroke-width="2" />
<line x1="632" y1="74" x2="632" y2="118" stroke="#333" stroke-width="2" />
<line x1="708" y1="74" x2="708" y2="118" stroke="#333" stroke-width="2" />
<ellipse cx="670" cy="120" rx="50" ry="14" stroke="#333" stroke-width="2" fill="none" />
<ellipse cx="670" cy="118" rx="38" ry="10" stroke="#333" stroke-width="2" fill="none" />
<text x="670" y="155" text-anchor="middle" font-size="10">coaxial cylinders</text>
</g>

<text x="390" y="240" text-anchor="middle" font-size="10" fill="#555">Red line = actual measured surface/profile within tolerance zone boundaries</text>

</svg>

### Verification Methods Summary

- **Flatness:** CMM surface scan, optical flat (for high-precision), surface plate + indicator sweep
- **Straightness:** CMM line scan, straightedge + feeler gauge, laser interferometry (for very tight tolerances)
- **Circularity:** Roundness tester (rotating table with high-resolution probe), V-block + indicator (approximate method)
- **Cylindricity:** Roundness tester with axial traverse, CMM with dense point cloud sampling

[Inference] Roundness testers generally provide the most repeatable circularity/cylindricity data because they isolate the measurement from datum-induced setup error, though results can still be affected by spindle error motion and fixturing.

### Relationship to Rule #1 (Envelope Principle)

- Per Rule #1, the form of an individual feature of size is implicitly controlled by its size limits alone — a feature produced at MMC must have a perfect form at that size (Taylor Principle / envelope requirement)
- Explicit form tolerances (flatness, straightness, circularity, cylindricity) are used when a **tighter** form control than what Rule #1 implicitly provides is functionally required, since Rule #1's implicit control only becomes meaningful at MMC and relaxes as the feature departs toward LMC

**Related Topics**

- Rule #1 (Envelope Principle) and Rule #2
- Orientation tolerances (perpendicularity, parallelism, angularity)
- Runout tolerances and their relationship to form/circularity
- Surface texture vs. form tolerance distinction
- Datum feature simulators and their role in form-independent measurement
- GD&T tolerance zone hierarchy (form → orientation → location → runout)