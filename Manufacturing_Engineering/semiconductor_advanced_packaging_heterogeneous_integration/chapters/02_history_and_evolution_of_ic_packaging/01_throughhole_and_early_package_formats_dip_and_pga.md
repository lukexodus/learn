## Through-Hole and Early Package Formats: DIP and PGA

### Overview

Through-hole packaging represents the earliest widely adopted semiconductor packaging format, mounting components onto printed circuit boards (PCBs) via leads inserted through drilled holes and soldered on the opposite side. Dual In-line Package (DIP) and Pin Grid Array (PGA) formats dominated IC packaging from the 1960s through the 1980s, establishing foundational concepts — lead frames, cavity/cap construction, pin-count scaling — that inform the conceptual lineage of modern advanced packaging, even as surface-mount and area-array technologies have since superseded them for most high-density applications.

### Dual In-line Package (DIP)

**Structure and Construction**

DIP packages feature two parallel rows of leads extending from a rectangular package body, with lead pitch standardized at 0.1 inch (2.54 mm) — a spacing that became a de facto industry standard influencing PCB design for decades.

**Key Points**

- **Package body materials**: ceramic (CERDIP, using a glass-frit sealed ceramic cavity) for hermetic, high-reliability applications, or injection-molded plastic (PDIP) for lower-cost commercial applications.
- **Die attach and wire bonding**: the die is attached to a lead frame paddle (die pad) using conductive or non-conductive adhesive, then electrically connected to the lead frame fingers via wire bonding (typically gold or aluminum wire, thermosonic or ultrasonic bonding).
- **Pin counts**: typically ranged from 8 to 64 pins, with 14-pin and 16-pin DIPs especially common for logic ICs (e.g., 7400-series TTL logic).
- **Lead frame role**: the lead frame serves simultaneously as the die attach platform, wire bond target, and external electrical interface — a unified structural-electrical element that later evolved into more complex multi-layer substrate concepts in advanced packaging.

**Limitations**

[Inference] DIP packaging's fundamental limitation was I/O scaling: because leads were confined to two parallel edges, pin count scaled linearly with package length rather than with package area, making DIP impractical for the higher pin counts (100+) demanded by increasingly complex ICs — the core motivation for area-array formats like PGA and, later, ball grid array (BGA).

### Pin Grid Array (PGA)

**Structure and Construction**

PGA packages arrange pins in a two-dimensional grid across the underside of the package (rather than along two edges), enabling substantially higher pin counts within a given package footprint by using package area rather than perimeter for I/O.

**Key Points**

- **Area-array advantage**: pin count scales with the square of linear package dimension (area) rather than linearly with perimeter, enabling pin counts from roughly 100 to 300+ in packages that would be impractically long as a DIP.
- **Package materials**: ceramic PGA (CPGA) was common for high-performance and military/aerospace applications requiring hermeticity and high thermal conductivity; plastic PGA (PPGA) served lower-cost commercial segments.
- **Pin insertion mounting**: like DIP, PGA pins insert through PCB through-holes and are wave- or hand-soldered, requiring precise pin alignment and PCB drilling registration across potentially hundreds of pins.
- **Notable historical applications**: PGA was widely used for early microprocessors (e.g., early Intel and AMD x86 CPU packages) where pin counts exceeded practical DIP limits but before surface-mount area-array alternatives (BGA, later LGA) matured.

**Zero Insertion Force (ZIF) Sockets**

High pin-count PGA packages, particularly microprocessors, commonly used ZIF sockets — mechanical sockets with a lever mechanism that widens contact spacing during insertion, then clamps down to establish contact — reducing insertion force and mechanical stress on the many fragile pins compared to direct friction-fit insertion.

### DIP vs. PGA Comparison

| Aspect | DIP | PGA |
| --- | --- | --- |
| Lead arrangement | Two parallel rows (perimeter) | 2D grid (area array) |
| Typical pin count | 8–64 | 100–300+ |
| Pin count scaling | Linear with package length | Quadratic with package area |
| Mounting | Through-hole, wave solder | Through-hole, socket or solder |
| Common materials | Ceramic (CERDIP), plastic (PDIP) | Ceramic (CPGA), plastic (PPGA) |
| Typical era of dominance | 1960s–1980s | 1970s–1990s |
| Successor technology | SOIC, QFP (surface mount) | BGA, LGA (area-array surface mount) |

### Diagram: DIP vs. PGA Lead/Pin Arrangement (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 300">
<text x="150" y="20" font-size="14" font-weight="bold" text-anchor="middle" fill="#000">DIP: Perimeter Leads (svg_diagram)</text>
<rect x="80" y="40" width="140" height="180" fill="#d9d9d9" stroke="#000" stroke-width="2" />
<text x="150" y="135" font-size="12" text-anchor="middle" fill="#000">Die Cavity</text>

<line x1="40" y1="55" x2="80" y2="55" stroke="#333" stroke-width="3" />
<line x1="40" y1="80" x2="80" y2="80" stroke="#333" stroke-width="3" />
<line x1="40" y1="105" x2="80" y2="105" stroke="#333" stroke-width="3" />
<line x1="40" y1="130" x2="80" y2="130" stroke="#333" stroke-width="3" />
<line x1="40" y1="155" x2="80" y2="155" stroke="#333" stroke-width="3" />
<line x1="40" y1="180" x2="80" y2="180" stroke="#333" stroke-width="3" />
<line x1="40" y1="205" x2="80" y2="205" stroke="#333" stroke-width="3" />

<line x1="220" y1="55" x2="260" y2="55" stroke="#333" stroke-width="3" />
<line x1="220" y1="80" x2="260" y2="80" stroke="#333" stroke-width="3" />
<line x1="220" y1="105" x2="260" y2="105" stroke="#333" stroke-width="3" />
<line x1="220" y1="130" x2="260" y2="130" stroke="#333" stroke-width="3" />
<line x1="220" y1="155" x2="260" y2="155" stroke="#333" stroke-width="3" />
<line x1="220" y1="180" x2="260" y2="180" stroke="#333" stroke-width="3" />
<line x1="220" y1="205" x2="260" y2="205" stroke="#333" stroke-width="3" />

<text x="480" y="20" font-size="14" font-weight="bold" text-anchor="middle" fill="#000">PGA: Area-Array Pins</text>

<rect x="400" y="40" width="160" height="160" fill="`#d9d9d9`" stroke="#000" stroke-width="2" />

<g fill="#333">

<circle cx="420" cy="60" r="4" /><circle cx="440" cy="60" r="4" /><circle cx="460" cy="60" r="4" /><circle cx="480" cy="60" r="4" /><circle cx="500" cy="60" r="4" /><circle cx="520" cy="60" r="4" /><circle cx="540" cy="60" r="4" />

<circle cx="420" cy="80" r="4" /><circle cx="440" cy="80" r="4" /><circle cx="460" cy="80" r="4" /><circle cx="480" cy="80" r="4" /><circle cx="500" cy="80" r="4" /><circle cx="520" cy="80" r="4" /><circle cx="540" cy="80" r="4" />

<circle cx="420" cy="100" r="4" /><circle cx="440" cy="100" r="4" /><circle cx="460" cy="100" r="4" /><circle cx="480" cy="100" r="4" /><circle cx="500" cy="100" r="4" /><circle cx="520" cy="100" r="4" /><circle cx="540" cy="100" r="4" />

<circle cx="420" cy="120" r="4" /><circle cx="440" cy="120" r="4" /><circle cx="460" cy="120" r="4" /><circle cx="480" cy="120" r="4" /><circle cx="500" cy="120" r="4" /><circle cx="520" cy="120" r="4" /><circle cx="540" cy="120" r="4" />

<circle cx="420" cy="140" r="4" /><circle cx="440" cy="140" r="4" /><circle cx="460" cy="140" r="4" /><circle cx="480" cy="140" r="4" /><circle cx="500" cy="140" r="4" /><circle cx="520" cy="140" r="4" /><circle cx="540" cy="140" r="4" />

<circle cx="420" cy="160" r="4" /><circle cx="440" cy="160" r="4" /><circle cx="460" cy="160" r="4" /><circle cx="480" cy="160" r="4" /><circle cx="500" cy="160" r="4" /><circle cx="520" cy="160" r="4" /><circle cx="540" cy="160" r="4" />

<circle cx="420" cy="180" r="4" /><circle cx="440" cy="180" r="4" /><circle cx="460" cy="180" r="4" /><circle cx="480" cy="180" r="4" /><circle cx="500" cy="180" r="4" /><circle cx="520" cy="180" r="4" /><circle cx="540" cy="180" r="4" />

</g>

<text x="150" y="250" font-size="11" text-anchor="middle" fill="#333">I/O scales linearly with perimeter</text>

<text x="480" y="250" font-size="11" text-anchor="middle" fill="#333">I/O scales with area (rows x columns)</text>

</svg>

### Legacy and Transition to Modern Packaging

**Key Points**

- **Surface-mount transition**: through-hole formats were progressively displaced by surface-mount technology (SMT) — SOIC and QFP succeeded DIP; BGA and LGA succeeded PGA — driven by the need for smaller footprints, automated assembly (pick-and-place), and higher I/O density without PCB drilling constraints.
- **Conceptual lineage to advanced packaging**: the area-array principle pioneered by PGA (I/O scaling with area rather than perimeter) directly foreshadows the area-array bump/ball arrangements used in flip-chip BGA, and ultimately micro-bump and hybrid-bond arrays in today's 2.5D/3D packages.
- **Wire bonding continuity**: the wire-bond die-attach technique used in DIP and PGA remains in use today for many standard packages, though advanced packaging has increasingly shifted toward flip-chip and direct-bond interconnects for higher density and better electrical performance.
- **Persistence in niche applications**: [Inference] DIP and PGA packages likely remain in limited use today primarily for prototyping (DIP sockets on breadboards), legacy system maintenance, and certain high-reliability/radiation-hardened aerospace applications where qualified heritage designs are preferred over newer, less field-proven packaging technologies.

### Design Implications for Advanced Packaging

- **Area-array principle inheritance**: modern BGA, micro-bump, and hybrid-bond interconnect strategies conceptually descend from PGA's area-array approach to overcoming perimeter-limited I/O scaling.
- **Pitch standardization precedent**: DIP's 0.1-inch pitch standardization illustrates how mechanical/electrical standardization enables ecosystem-wide interoperability — a principle echoed in modern chiplet interconnect standardization efforts (e.g., UCIe).
- **Thermal and mechanical simplicity vs. modern demands**: through-hole packages had relatively simple thermal paths (lead frame conduction, natural convection) adequate for low power densities of their era, contrasting sharply with the multi-physics co-design required for today's high-power 2.5D/3D packages.

### Related Topics

- Surface-mount technology (SMT) transition: SOIC, QFP, and leadless packages
- Ball grid array (BGA) and area-array surface-mount evolution
- Wire bonding fundamentals and lead frame design
- Flip-chip interconnect: origins and displacement of wire bonding
- Chiplet interconnect standardization (UCIe) and pitch/pin-map conventions
- Hermetic ceramic packaging for high-reliability and aerospace applications
- Pick-and-place assembly and the shift from through-hole to SMT manufacturing