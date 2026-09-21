## Spreader Bars and Lifting Beams

### Overview

Spreader bars and lifting beams are below-the-hook devices that convert a single crane hook attachment into two or more controlled load points, changing the geometry and internal stress state of the sling system compared to a direct multi-leg bridle. Though often used interchangeably in casual speech, the two devices load their sling legs in fundamentally opposite directions, which drives entirely different structural design requirements.

### Fundamental Distinction

**Lifting Beams (tension members)**

- Top slings run from the crane hook to the beam ends at an angle above the beam
- Bottom slings run vertically (or near-vertically) from the beam down to the load
- The beam itself is loaded primarily in **bending and compression is minimal**; top sling angle induces horizontal thrust that the beam resists axially
- Bottom slings remain vertical regardless of load width, so sling angle derating (see Shackles/Hooks module) does not apply to the lower legs

**Spreader Bars (compression members)**

- Top slings run vertically from the crane hook down to the bar ends
- Bottom slings run from the bar ends outward and downward to the load's lift points, angled outward from vertical
- The bar itself is loaded in **pure axial compression** along its length, with the vertical top slings inducing that compression
- Bottom sling angle **from vertical** must be checked against angular derating, since the bottom legs are not vertical

The core design driver: a lifting beam's top slings converge toward the hook (inward angle), while a spreader bar's bottom slings diverge away from the bar (outward angle). This is the single most important visual/structural cue for distinguishing the two on a rigging drawing.

```mermaid
flowchart TD
    subgraph LiftingBeam["Lifting Beam (svg_diagram)"]
    A1[Crane Hook] --> B1[Top Sling - Angled Inward]
    B1 --> C1[Beam - Bending Member]
    C1 --> D1[Bottom Sling - Vertical]
    D1 --> E1[Load Lift Point]
    end
    subgraph SpreaderBar["Spreader Bar (svg_diagram)"]
    A2[Crane Hook] --> B2[Top Sling - Vertical]
    B2 --> C2[Bar - Compression Member]
    C2 --> D2[Bottom Sling - Angled Outward]
    D2 --> E2[Load Lift Point]
    end
```

### Structural Design Considerations

**Spreader Bar Compression and Buckling**

Because the bar carries pure axial compression, the governing failure mode is **column buckling**, not yield. Critical buckling load follows Euler's formula:

$$P_{cr} = \frac{\pi^2 E I}{(KL)^2}$$

where $E$ is the modulus of elasticity, $I$ is the moment of inertia of the bar's cross-section, $K$ is the effective length factor (end-condition dependent), and $L$ is the unsupported bar length. Longer spreader bars require disproportionately larger cross-sections to resist buckling, which is why very long spreader bars are often trussed (built as a lattice structure) rather than solid tube, to increase $I$ without a proportional weight penalty.

**Lifting Beam Bending**

The beam is analyzed as a simply-supported (or, for some designs, cantilevered) beam under point loads at the bottom sling attachment points, with reactions at the top sling attachment points. Maximum bending moment governs section selection:

$$M_{max} = \frac{P \times a}{1}$$

for a two-point-loaded beam where $P$ is the load at each pickup point and $a$ is the distance from support to load point (varies by loading configuration — simply supported with loads inside the supports versus overhung loads).

### Sizing and Selection Criteria

- **Rated capacity** must exceed total load plus the beam/bar's own dead weight where the crane's total lift calculation requires it
- **Span/spread** must match the load's lift-point spacing; adjustable spreader bars and beams (telescoping or bolt-hole adjustable) accommodate a range of load widths but each adjustment position typically carries its own derated capacity
- **Below-the-hook engineering certification** — per ASME B30.20, spreader bars and lifting beams are classified as below-the-hook lifting devices (BTHLDs) and require design documentation, load testing, and a rated capacity marking; custom-fabricated bars/beams should be engineered and proof-tested before use, not improvised from available structural steel
- **Attachment point compatibility** — top and bottom connection points must match shackle/sling hardware pin diameters (see Shackles and Hooks module) and must be oriented to prevent side-loading of shackles

### When to Select Which Device

- **Spreader bar** — preferred when the load has widely separated lift points and low headroom clearance above the load is available, since the compression geometry keeps the overall rig height lower for a given spread
- **Lifting beam** — preferred when headroom is more generous and/or when the application benefits from a single rigid bottom attachment plane (e.g., picking a long vessel or module with fixed lift lugs at a known spacing) with less concern for bar buckling at long spans
- **Combination frames** — large heavy-lift modules (e.g., pipe racks, skid-mounted equipment) frequently use a rigid spreader/lifting frame combining both beam and bar elements in a single fabricated structure, engineered as a unit rather than assembled from separate off-the-shelf components

### Headroom and Rigging Geometry Impact

Because spreader bars keep bottom sling angles closer to vertical relative to lifting beams (for equivalent spread and headroom), they generally reduce horizontal thrust on the load's lift lugs. This matters when lift lugs or trunnions have limited resistance to side-loading — a common consideration for pressure vessels and modules where lift lugs are only rated for pure vertical pull.

### Inspection and Load Testing

- Visual inspection for weld cracking, bar/beam distortion (bowing under prior compressive overload is a classic bar-retirement indicator), and connection point wear
- Load test to 100–125% of rated capacity (jurisdiction/standard dependent) required before first use and after any repair, per ASME B30.20
- Rated capacity plate must be legible and match the current configuration (critical for adjustable-span devices, where capacity varies by span setting)
- Non-destructive testing (dye penetrant or magnetic particle) on welds for devices used in critical or repetitive heavy-lift service

### Example

A precast concrete panel, 12 m long, is lifted using a spreader bar at two pick points 10 m apart, each carrying 8 t (16 t total panel weight). Top slings are vertical from a single crane hook to the bar ends; bottom slings run from the bar ends down to embedded lift anchors at 30° from vertical.

Bottom sling tension per leg:

$$T = \frac{P}{\cos(30°)} = \frac{8}{0.866} \approx 9.2 \text{ t/leg}$$

The bar itself sees axial compression equal to the vertical component of the top slings, approximately 16 t total (8 t transmitted through each half of the bar to its respective top attachment), and the bar's engineered rated capacity — not just the sling WLL — governs whether this configuration is acceptable; a bar rated for a *narrower* span at the same total capacity may be **overstressed in buckling** at this 10 m spread even though total weight is unchanged.

**Related Topics**

- Below-the-Hook Lifting Device Design (ASME B30.20)
- Multi-Leg Bridle Sling Angle Calculations
- Shackles, Hooks, and Rigging Hardware Selection
- Lift Lug and Trunnion Design for Heavy Modules
- Proof Load Testing Procedures for Custom Rigging
- Center of Gravity Determination for Asymmetric Loads