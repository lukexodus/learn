## Selecting Strand Jacking versus Conventional Cranes


### Overview

Strand jacking and conventional (mobile or crawler) cranes represent two fundamentally different approaches to heavy lifting. Selection between them is a project-defining engineering decision driven by load magnitude, geometry, site access, ground conditions, lift height, and economics. Strand jacking systems use multiple high-tensile steel strands pulled through hydraulic jacks to lift or translate loads incrementally, while conventional cranes use a rigid boom, hoist rope, and hook to lift loads in a single continuous motion.

### Fundamental Working Principles

**Strand Jacking**

Strand jacks operate on a "pull-through" principle. A bundle of 7-wire steel strands (typically 15.2 mm or 15.7 mm diameter, similar to post-tensioning strand) passes through a hydraulic cylinder fitted with two sets of wedge grips (upper and lower anchor heads). The cylinder extends and retracts in a stroke cycle (commonly 300–500 mm per stroke), with the anchors alternately gripping and releasing the strand to "inchworm" the load upward or along a translation path. Multiple jacks are synchronized via a central hydraulic power unit (HPU) and PLC-based control system to maintain load-sharing tolerances, typically within 2–5% of rated capacity per jack.

**Conventional Cranes**

Mobile, crawler, and tower cranes lift loads via a wire rope reeved through a boom-mounted sheave system and wound onto a winch drum. Capacity is governed by a load chart that is a function of boom length, radius (distance from the pivot point to the load), configuration (main boom, luffing jib, superlift/counterweight tray), and ground bearing conditions. The lift is a continuous, single-pass operation limited by boom geometry and outrigger/crawler footprint.

### Key Points

- **Load capacity scaling**: Strand jacking scales near-linearly by adding jack units and strands; a single strand jack unit can range from ~30 tons to over 500 tons per jack, and arrays can be combined to lift several thousand tons. Conventional cranes are limited by a single machine's rated maximum capacity (largest crawler cranes reach approximately 3,000–3,200 tons at minimum radius) [Unverified — model-specific and subject to manufacturer updates].
- **Headroom and overhead clearance**: Strand jacking requires minimal overhead clearance since jacks can be mounted on low-profile support towers, gantries, or the structure itself. Conventional cranes require substantial vertical clearance for the boom, making them unsuitable under existing structures, near overhead power lines, or in confined vertical spaces (e.g., inside process plants, under bridges).
- **Ground bearing and footprint**: Strand jack support towers and anchor points distribute load over a smaller, engineered footprint (often onto the permanent structure's foundation or purpose-built temporary steel). Cranes require large, stable, level ground areas capable of resisting high point loads through outriggers or crawler tracks — often demanding extensive ground improvement (mats, piling, compacted fill).
- **Lift speed**: Cranes lift substantially faster (meters per minute) versus strand jacks (typically 3–15 m/hour depending on stroke rate and load). This makes cranes more economical for high-cycle, repetitive lifts.
- **Precision and control**: Strand jacking offers highly controlled, slow-speed movement with sub-millimeter position feedback in synchronized systems, valuable for delicate alignment (e.g., bridge girder placement, skid-in of process modules). Cranes rely on operator skill and rigging for positioning, which is faster but less inherently precise for fine tolerance work.
- **Mobility**: Cranes are self-propelled or can be transported and set up relatively quickly. Strand jack systems require significant engineering, temporary works design, and setup/mobilization time (support towers, anchor points, hydraulic hose runs), making them less suited for one-off, quick lifts.
- **Load path flexibility**: Cranes lift and swing through an arc, offering flexible load repositioning. Strand jacks typically move loads along a fixed, pre-engineered path (vertical lift or defined skid/translation trajectory), which is less flexible but more predictable and controllable for critical alignments.

### Comparative Technical Parameters

| Parameter | Strand Jacking | Conventional Crane |
| --- | --- | --- |
| Typical capacity range | 30–5,000+ tons (array-dependent) | Up to ~3,000 tons (largest crawlers) [Unverified] |
| Lift speed | ~3–15 m/hr | Tens of meters/min |
| Overhead clearance needed | Minimal | Significant (boom length + angle) |
| Ground footprint | Small, engineered support points | Large, requires bearing capacity across swing radius |
| Positional accuracy | Sub-mm to mm with synchronized control | Rigging/operator dependent, typically cm-level |
| Mobilization time | High (temporary works, anchors) | Low to moderate |
| Best suited load path | Fixed vertical or translation path | Arc/radius-based, flexible |
| Redundancy | High (multi-jack array; single jack failure is manageable) | Low (single point of failure at hook/boom) |

### Selection Criteria Framework

**1. Load Magnitude vs. Available Crane Capacity**

If the load exceeds the practical capacity of available cranes at the required radius and height — or exceeds what is economically justifiable to mobilize (e.g., largest crawler cranes require weeks of assembly and hundreds of truckloads) — strand jacking becomes the default heavy-lift solution.

**2. Site Access and Congestion**

Confined or congested sites (retrofits, brownfield plants, urban environments, offshore platforms) that cannot accommodate crane outriggers/tracks or boom swing radius favor strand jacking or skidding systems, which can be engineered around existing obstructions.

**3. Vertical Clearance Constraints**

Lifts beneath existing structures, under power transmission lines, inside enclosed buildings, or near flight paths with height restrictions favor strand jacking due to its low-profile support towers.

**4. Ground Bearing Capacity**

Poor soil conditions, soft ground, or the presence of buried utilities that cannot support crane mat loading may necessitate strand jacking with distributed, engineered foundations, or ground improvement, whichever proves more cost-effective.

**5. Lift/Move Precision Requirements**

Applications requiring incremental, closely monitored movement — such as bridge deck launching, offshore module mating, or precision equipment setting with tight tolerance — favor strand jacking's controlled, synchronized movement.

**6. Project Schedule and Lift Frequency**

High-frequency, repetitive lifts (e.g., precast panel erection, steel member placement across many similar lifts) favor cranes due to cycle speed. Single, critical heavy lifts favor strand jacking despite longer per-lift duration, because mobilization cost is amortized over one major operation.

**7. Redundancy and Risk Tolerance**

Strand jacking systems' multi-strand, multi-jack redundancy reduces single-point-of-failure risk, which is often preferred for extremely high-value or safety-critical lifts (e.g., nuclear components, offshore topsides).

**8. Cost**

[Inference] Mobilization and engineering costs for strand jacking are typically higher on a per-project basis due to custom temporary works design, but the per-ton cost advantage improves as load magnitude increases and crane options become scarcer or require extraordinary mobilization. Actual comparative costs are highly project- and region-specific and should be verified through vendor quotations and detailed engineering studies.

### Decision Flow (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 900 640" font-family="Arial, sans-serif">
<text x="450" y="30" font-size="18" font-weight="bold" text-anchor="middle">Strand Jacking vs Conventional Crane — Decision Flow (svg_diagram)</text>
<rect x="350" y="50" width="200" height="50" rx="8" fill="#e8f0fe" stroke="#4285f4" stroke-width="2" />
<text x="450" y="80" font-size="13" text-anchor="middle">Start: Define Lift</text>
<line x1="450" y1="100" x2="450" y2="130" stroke="#333" stroke-width="2" marker-end="url(#arrow)" />
<rect x="330" y="130" width="240" height="60" rx="8" fill="#fff3cd" stroke="#e6a817" stroke-width="2" />
<text x="450" y="155" font-size="12" text-anchor="middle">Load exceeds max available</text>
<text x="450" y="172" font-size="12" text-anchor="middle">crane capacity at radius?</text>
<line x1="450" y1="190" x2="450" y2="220" stroke="#333" stroke-width="2" marker-end="url(#arrow)" />
<text x="465" y="210" font-size="11">No</text>
<rect x="330" y="220" width="240" height="60" rx="8" fill="#fff3cd" stroke="#e6a817" stroke-width="2" />
<text x="450" y="245" font-size="12" text-anchor="middle">Sufficient overhead</text>
<text x="450" y="262" font-size="12" text-anchor="middle">clearance for boom?</text>
<line x1="450" y1="280" x2="450" y2="310" stroke="#333" stroke-width="2" marker-end="url(#arrow)" />
<text x="465" y="300" font-size="11">Yes</text>
<rect x="330" y="310" width="240" height="60" rx="8" fill="#fff3cd" stroke="#e6a817" stroke-width="2" />
<text x="450" y="335" font-size="12" text-anchor="middle">Ground bearing capacity</text>
<text x="450" y="352" font-size="12" text-anchor="middle">adequate for crane setup?</text>
<line x1="450" y1="370" x2="450" y2="400" stroke="#333" stroke-width="2" marker-end="url(#arrow)" />
<text x="465" y="390" font-size="11">Yes</text>
<rect x="330" y="400" width="240" height="60" rx="8" fill="#fff3cd" stroke="#e6a817" stroke-width="2" />
<text x="450" y="425" font-size="12" text-anchor="middle">Precision/incremental</text>
<text x="450" y="442" font-size="12" text-anchor="middle">movement required?</text>
<line x1="450" y1="460" x2="450" y2="490" stroke="#333" stroke-width="2" marker-end="url(#arrow)" />
<text x="465" y="480" font-size="11">No</text>
<rect x="320" y="490" width="260" height="55" rx="8" fill="#d4edda" stroke="#28a745" stroke-width="2" />
<text x="450" y="522" font-size="13" font-weight="bold" text-anchor="middle">Select Conventional Crane</text>
<line x1="570" y1="160" x2="720" y2="160" stroke="#333" stroke-width="2" marker-end="url(#arrow)" />
<text x="600" y="150" font-size="11">Yes</text>
<line x1="570" y1="250" x2="720" y2="250" stroke="#333" stroke-width="2" marker-end="url(#arrow)" />
<text x="600" y="240" font-size="11">No</text>
<line x1="570" y1="340" x2="720" y2="340" stroke="#333" stroke-width="2" marker-end="url(#arrow)" />
<text x="600" y="330" font-size="11">No</text>
<line x1="570" y1="430" x2="720" y2="430" stroke="#333" stroke-width="2" marker-end="url(#arrow)" />
<text x="600" y="420" font-size="11">Yes</text>
<line x1="720" y1="160" x2="720" y2="470" stroke="#333" stroke-width="2" />
<line x1="720" y1="250" x2="720" y2="470" stroke="#333" stroke-width="0" />
<line x1="720" y1="470" x2="720" y2="490" stroke="#333" stroke-width="2" marker-end="url(#arrow)" />
<rect x="600" y="490" width="240" height="55" rx="8" fill="#cce5ff" stroke="#004085" stroke-width="2" />
<text x="720" y="512" font-size="13" font-weight="bold" text-anchor="middle">Select Strand Jacking</text>
<text x="720" y="530" font-size="11" text-anchor="middle">(or skidding/SPMT hybrid)</text>
<line x1="450" y1="545" x2="450" y2="570" stroke="#333" stroke-width="2" marker-end="url(#arrow)" />
<rect x="300" y="570" width="300" height="55" rx="8" fill="#f8d7da" stroke="#dc3545" stroke-width="2" />
<text x="450" y="592" font-size="12" text-anchor="middle">Validate with detailed lift study,</text>
<text x="450" y="609" font-size="12" text-anchor="middle">rigging engineer sign-off</text>
</svg>

### Synchronized Multi-Jack Load Sharing

For heavy modules lifted at multiple points, synchronization accuracy is critical to avoid overloading individual jacks due to uneven load distribution from structural stiffness variation. Control systems typically monitor:

- **Load cell feedback** at each jack (strain-gauge or hydraulic pressure-based)
- **Stroke position** via linear encoders or draw-wire sensors
- **PLC synchronization logic** that adjusts individual jack stroke rate to maintain relative elevation within tolerance (commonly ±5–10 mm across the array, project-specific)

A simplified load-sharing constraint for an $n$-jack system can be expressed as:

$$\sum_{i=1}^{n} F_i = W_{total}$$

where each individual jack force $F_i$ must remain within its safe working load:

$$F_i \leq SWL_i \quad \forall i \in \{1, ..., n\}$$

[Inference] Actual synchronization tolerances, load cell configurations, and control algorithms vary by manufacturer (e.g., Enerpac, ALE Heavylift, Mammoet) and should be confirmed against the specific system's technical documentation.

### Example: Bridge Girder Installation Scenario

**Scenario**: Installing a 450-ton steel bridge girder over an active highway with a 6-meter vertical clearance restriction due to overhead utility crossings, on soft alluvial soil unsuitable for heavy crane mats.

**Analysis**:

- A conventional crawler crane capable of a 450-ton pick at the required radius would need a boom configuration exceeding available overhead clearance — disqualifying it outright.
- Ground conditions would require extensive matting or piling to support crane ground-bearing pressure, adding significant cost and schedule risk.
- A strand jacking system mounted on temporary steel towers founded on spread footings or micropiles at each pier location can lift and skid the girder into final position with minimal overhead profile and a smaller, more manageable foundation footprint.

**Outcome**: Strand jacking (potentially combined with skid beams for horizontal translation into final span position) is selected as the technically viable and lower-risk option, despite a longer lift duration compared to a hypothetical unconstrained crane lift.

### Common Failure Modes and Risk Considerations

- **Strand jacking**: Strand fatigue from repeated cyclic loading, anchor wedge slippage, hydraulic system pressure loss, foundation/support tower instability under eccentric loading, synchronization control failure leading to uneven load distribution.
- **Conventional cranes**: Ground instability/outrigger punch-through, exceeding load chart at radius (tip-over risk), boom-to-obstruction contact, wire rope failure, wind loading exceeding rated limits for boom configuration.

[Behavior may vary based on specific equipment models, control system firmware, manufacturer specifications, and site-specific engineering — always verify against current OEM documentation and a certified lift plan before execution.]

### Regulatory and Standards Context

Both methods are typically governed by project-specific lift plans reviewed by a professional engineer, informed by standards such as:

- ASME B30.1 (general lifting standards, U.S. context) [Unverified — applicability varies by jurisdiction]
- DNV or relevant international heavy-lift guidelines for marine/offshore strand jacking operations
- Local occupational safety regulations governing critical lift classification (lifts exceeding 75–90% of rated capacity, or involving personnel, typically require enhanced engineering review)

[Inference] Specific regulatory citations should be verified against the applicable jurisdiction for the project location, as heavy-lift regulatory frameworks differ significantly between countries and industries (construction, offshore, nuclear, etc.).

### Related Topics

- Skidding systems and skid shoe/track design fundamentals
- Self-Propelled Modular Transporters (SPMTs) and their integration with strand jacking for lift-and-carry operations
- Temporary works design for strand jack support towers and anchor foundations
- Hydraulic power unit (HPU) sizing and synchronization control architecture
- Critical lift planning and rigging engineering documentation requirements
- Load monitoring instrumentation: load cells, strain gauges, and real-time telemetry systems
- Wind loading limits and environmental constraints for heavy lift operations
- Case studies: offshore module mating, bridge launching, power plant module installation