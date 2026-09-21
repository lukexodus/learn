## Mechanical Comparators

### Overview

Mechanical comparators are amplifying measuring instruments used to determine dimensional deviation of a workpiece relative to a known reference (typically a gauge block or master), rather than measuring absolute dimension directly. A small mechanical displacement of a contact probe is magnified through mechanical linkages, levers, or gear trains, and displayed on a graduated scale or dial. They are a cornerstone of comparative gauging in quality control, especially for high-volume inspection and go/no-go style tolerance verification with a readable deviation value.

### Operating Principle

**Key Points**

- The instrument is first **zeroed/mastered** against a reference standard (gauge block, ring gauge, or master part) of nominal size
- The workpiece is then measured, and the comparator displays only the **deviation** from that master, not the absolute dimension
- Mechanical amplification (magnification) converts a very small plunger/spindle displacement (often sub-micrometer) into a readable pointer movement
- Comparators are inherently **relative/differential instruments** — accuracy depends heavily on the quality of the master used for zeroing

### Magnification and Amplification Mechanisms

#### Lever-and-Gear Type (Dial Comparators / Dial Indicators)

- A rack-and-pinion or lever system converts linear spindle motion into rotary pointer motion
- Typical amplification ratios range from roughly 100:1 to 1000:1 depending on gear train design
- Subject to mechanical backlash, gear train wear, and friction (stiction) affecting repeatability at very fine scales

#### Reed-Type Mechanical Comparators

- Use a thin metal reed or twisted-strip flexure instead of gears/pinions, eliminating backlash and friction from gear meshing
- A pointer is fixed to the reed; as the reed twists in response to plunger displacement, angular pointer deflection is largely proportional to the twist
- [Inference] Reed mechanisms are generally regarded as offering superior repeatability compared to rack-and-pinion dial gauges because they eliminate gear backlash, though they typically provide a more limited working range than dial-type comparators

#### Sigma/Johansson Mechanical Comparators

- A classic reed-and-lever hybrid design (originally developed by C.E. Johansson) widely used as a high-precision shop-floor comparator
- Combines a twisted-band (reed) primary amplification stage with a secondary lever stage to achieve high total magnification (commonly cited historically around 1000:1 to 5000:1, depending on model) while maintaining good linearity
- [Unverified] Specific magnification figures vary by exact model and era of manufacture; original manufacturer documentation should be consulted for a specific instrument's rated magnification

#### Optical-Mechanical Comparators

- A mechanical linkage moves a mirror or optical lever, and the amplified deflection is projected onto a scale or screen (distinguishing them from purely mechanical dial/reed types, though often grouped in the same broad comparator family)
- [Inference] Not to be confused with optical projectors/profile projectors, which are a separate shadow-projection category of instrument used for contour comparison rather than linear deviation measurement

### Key Specifications

| Parameter | Typical Range |
| --- | --- |
| Magnification (amplification ratio) | 100:1 to 5000:1+ |
| Scale graduation / resolution | 0.5 μm to 2 μm per division (dial types); finer for reed types |
| Measuring range (total travel) | Small — often ±0.05 mm to ±0.5 mm around zero |
| Measuring force | Low, typically fixed by spring/flexure design to minimize workpiece deformation and contact deflection error |
| Repeatability | Sub-micrometer for high-grade reed comparators |

[Unverified] Precise specification values are highly manufacturer- and model-dependent; the ranges above represent commonly encountered classes of mechanical comparators and should be verified against a specific instrument's datasheet.

### Mastering (Zero-Setting) Procedure

1. Select a gauge block (or master ring/plug for internal/external features) at the nominal target dimension
2. Clean the master and the comparator anvil/contact points thoroughly
3. Bring the master into contact with the comparator's measuring spindle
4. Adjust the comparator's zero-setting mechanism (typically a rotatable bezel or fine adjustment screw) until the pointer reads exactly zero
5. Remove the master, insert the workpiece, and read the deviation directly from the dial

**Example**

To inspect a shaft with a nominal diameter of 25.000 mm and a tolerance of $25.000^{+0.000}_{-0.020}$ mm, the comparator is mastered using a 25.000 mm gauge block. A production part is then measured; if the dial reads $-0.012$ mm, the actual diameter is $24.988$ mm, which falls within the specified tolerance band.

### Reading and Tolerance Zone Marking

Comparator dials are frequently fitted with **movable tolerance limit markers** (colored flags or pointers) set to the upper and lower tolerance limits relative to zero. This allows rapid visual go/no-go style judgment while still retaining a numeric deviation reading — combining the speed of limit gauging with the diagnostic value of a variable readout.

### Common Configurations

#### Bench-Mounted Comparator Stands

- The comparator head is mounted on a rigid vertical column with a fine height-adjustable carrier
- A flat or contoured anvil beneath supports the workpiece
- Used for external dimension comparison (diameters, thicknesses, step heights)

#### Snap/Caliper-Type Comparators

- Comparator mechanism integrated into a C-frame or snap-gauge body
- Enables rapid handheld comparison of external dimensions on a production line

#### Bore/Internal Comparators

- Comparator head coupled to an internal measuring probe (often via a lever or lazy-tongs mechanism) for checking internal diameters, often self-centering within the bore
- Frequently used for checking hole diameters against go/no-go tolerance bands with a numeric deviation readout

### Error Sources and Influencing Factors

**Key Points**

- **Cosine error**: If the measuring axis is not perfectly aligned with the direction of the dimension being measured, the reading is foreshortened by a factor of $\cos\theta$, where $\theta$ is the misalignment angle
- **Abbe offset error**: If the measurement axis and the reference/scale axis are not coincident (parallel but offset), angular deviations in the mechanism introduce additional error proportional to the offset distance
- **Contact/measuring force deflection**: The mechanical contact force compresses both the workpiece surface and the instrument's internal structure elastically, introducing small systematic offsets, especially on soft or compliant materials
- **Thermal expansion mismatch**: Differential thermal expansion between the workpiece, the master, and the comparator frame during mastering vs. measurement introduces error if not conducted at a stable, matched temperature
- **Backlash and hysteresis**: Particularly in gear/rack-based dial mechanisms, causing different readings depending on the direction of approach

$$L_{measured} = L_{true}\cos\theta$$

For small misalignment angles, the cosine error is second-order and often negligible; however, larger misalignments in poorly fixtured setups can introduce measurable systematic bias.

### Comparison: Mechanical vs. Electronic Comparators

| Aspect | Mechanical Comparator | Electronic (LVDT/Inductive) Comparator |
| --- | --- | --- |
| Amplification method | Gears, levers, reeds/flexures | Electronic signal conditioning |
| Backlash/friction | Present in gear types; minimal in reed types | Effectively none (contactless sensing element) |
| Output | Analog dial/scale | Digital display, often with data output (SPC integration) |
| Statistical process control (SPC) integration | Manual reading/recording only | Direct digital data logging |
| Robustness | Generally simpler, no power required | Requires power; more susceptible to electrical interference |
| Cost | Generally lower | Generally higher |

[Inference] Electronic comparators have largely supplanted mechanical dial/reed comparators in modern high-volume production environments due to direct SPC data logging capability, though mechanical comparators remain in service for standalone shop-floor inspection where digital connectivity is unnecessary.

### Diagram: Reed-Type Comparator Mechanism

```mermaid
flowchart LR
    A[Workpiece Contact / Spindle Displacement] --> B[Primary Lever Stage]
    B --> C[Twisted Reed / Flexure Strip]
    C --> D[Reed Twist Proportional to Displacement]
    D --> E[Pointer Fixed to Reed Tip]
    E --> F[Amplified Angular Deflection on Scale]
    G[Mastering: Zero Set Against Gauge Block] --> A
    F --> H[Deviation Reading vs. Master]
```

### Visual: Lever-Amplification Principle

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 560 320">
<text x="280" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Mechanical Comparator Lever Amplification (svg_diagram)</text>
<line x1="80" y1="220" x2="480" y2="220" stroke="#999" stroke-width="1" />
<rect x="150" y="150" width="30" height="70" fill="none" stroke="#2b6cb0" stroke-width="2" />
<text x="120" y="145" font-size="11" fill="#2b6cb0">Spindle</text>
<line x1="165" y1="150" x2="165" y2="120" stroke="#2b6cb0" stroke-width="2" />
<circle cx="165" cy="115" r="4" fill="#2b6cb0" />
<line x1="165" y1="115" x2="330" y2="130" stroke="#38a169" stroke-width="3" />
<circle cx="230" cy="118" r="4" fill="#333" />
<text x="215" y="105" font-size="10" fill="#333">Fulcrum</text>
<line x1="230" y1="118" x2="330" y2="70" stroke="#e53e3e" stroke-width="2" stroke-dasharray="4,2" />
<text x="335" y="72" font-size="11" fill="#e53e3e">Amplified pointer travel</text>
<text x="150" y="250" font-size="11" fill="#333">Small spindle displacement d</text>
<line x1="150" y1="260" x2="180" y2="260" stroke="#333" stroke-width="1.5" marker-end="url(#arrow)" />
<text x="330" y="60" font-size="11" fill="#e53e3e">Large pointer swing D = d × (lever ratio)</text>
</svg>

### Common Pitfalls

- **Using a worn or damaged master for zeroing**: Any error in the master directly transfers as a systematic offset to every subsequent measurement
- **Excessive measuring force / repeated slamming of parts**: Accelerates wear in gear-type mechanisms and can introduce surface deformation on soft workpieces
- **Neglecting thermal stabilization**: Handling parts directly before measurement introduces thermal expansion from body heat, a frequently underestimated error source in high-precision comparator work
- **Reading parallax**: On analog dial scales, viewing the pointer from an angle rather than perpendicular introduces a small but real reading error

### Standards References

- **ISO 463** — Geometrical Product Specifications (GPS) — Dimensional measuring equipment — Design and metrological characteristics of dial gauges
- **ASME B89.1.10** — Dial indicators (for comparators of dial-indicator type)
- **JJG (Chinese national verification regulations)** and **national NMI calibration procedures** — cover periodic calibration/verification requirements for mechanical comparators in various jurisdictions

**Related Topics**

- Electronic (LVDT-based) comparators
- Dial indicators and dial test indicators
- Gauge blocks and comparative mastering practice
- Air (pneumatic) comparators
- Optical comparators / profile projectors
- Abbe error and its influence on comparator accuracy
- Statistical process control (SPC) integration in dimensional gauging