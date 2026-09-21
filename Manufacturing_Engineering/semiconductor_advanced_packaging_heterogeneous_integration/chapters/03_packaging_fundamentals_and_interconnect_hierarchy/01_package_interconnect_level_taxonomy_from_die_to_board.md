## Package Interconnect Level Taxonomy from Die to Board


### Overview

Semiconductor packaging organizes electrical and mechanical interconnects into a hierarchy of "levels," a convention originating from classic IBM packaging literature and still used across the industry to describe how a transistor's switching signal physically travels from the silicon die to the end-system board. Each level represents a distinct interconnect technology, pitch regime, and manufacturing domain, and modern heterogeneous integration has added sub-levels (0.1, 1.5, etc.) to capture interposers, bridges, and fan-out redistribution that didn't exist in the original taxonomy.

### The Classical Interconnect Level Hierarchy

**Level 0 — On-Die Interconnect**

- Metal wiring within the die itself: local, intermediate, and global routing layers (BEOL — Back-End-Of-Line)
- Pitch: tens of nanometers at lower metal layers, growing to ~1-2 μm at top metal
- Includes vias, damascene copper wiring, and increasingly, backside power delivery networks (BSPDN) in leading-edge nodes
- Not always included in "packaging" taxonomies but is the origin point of the signal chain

**Level 1 — Die-to-Package (First-Level Interconnect, FLI)**

- Connects the die's I/O pads/bumps to the package substrate or leadframe
- Technologies: wire bonding, flip-chip (C4 solder bumps, copper pillar), thermocompression bonding (TCB), hybrid bonding
- Pitch range: ~150 μm (wire bond pad pitch) down to sub-10 μm (hybrid bonding)
- This is the primary focus of most "advanced packaging" innovation today (2.5D/3D integration lives here)

**Level 2 — Package-to-PCB (Second-Level Interconnect, SLI)**

- Connects the package substrate's external terminals to the printed circuit board
- Technologies: BGA (ball grid array) solder balls, LGA (land grid array) pads, PGA (pin grid array) pins, QFN/QFP leads
- Pitch range: ~0.3-1.5 mm typical BGA pitch
- Governed by JEDEC standards for ball/pad layout and solder reflow profiles

**Level 3 — Board-to-Board / Card-to-Card**

- Connectors, edge connectors, mezzanine connectors linking daughter cards to motherboards
- Examples: PCIe edge connectors, DIMM connectors, board-to-board headers

**Level 4 — Chassis/Backplane Interconnect**

- Backplane connectors linking multiple cards or subsystems within an enclosure
- Common in servers, telecom racks, and industrial systems

**Level 5 — System-to-System / Cabling**

- Cables, cable assemblies, and external connectors linking discrete systems or racks
- Includes copper and optical interconnect (DACs, AOCs)

### Modern Sub-Level Insertions (Heterogeneous Integration Era)

The classical L0-L5 model predates chiplets and 2.5D/3D integration, so practitioners now insert intermediate designations:

**Level 0.1 — Die-to-Die (Direct, No Substrate)**

- Direct chiplet-to-chiplet bonding without an intervening package substrate at that interface
- Hybrid bonding (Cu-Cu direct bonding), micro-bump D2D links
- Pitch: <10 μm (hybrid bonding) to ~40-55 μm (micro-bump D2D, e.g., UCIe standard PHY)

**Level 1.5 — Die-to-Interposer / Die-to-Bridge**

- Die connects first to a silicon interposer, silicon bridge (e.g., EMIB), or RDL (redistribution layer) fan-out structure, which then connects to the package substrate
- This intermediate tier is where most 2.5D integration value is created
- Interposer TSVs (through-silicon vias) then carry signals from interposer top to interposer bottom, connecting to the package substrate — sometimes labeled Level 1.5 to Level 2 transition

**Level 1.75 — Interposer/RDL-to-Substrate**

- Micro-bumps or C4 bumps connecting the interposer's backside (or fan-out RDL's redistribution) to the organic/ceramic package substrate

### Interconnect Pitch and Density Comparison

| Level | Interconnect Type | Typical Pitch | I/O Density Class |
| --- | --- | --- | --- |
| 0.1 (D2D hybrid bond) | Cu-Cu direct bond | 1-10 μm | >10,000 I/O/mm² |
| 0.1 (D2D micro-bump) | Cu pillar / micro-bump | 25-55 μm | ~400-1,600 I/O/mm² |
| 1 (Flip-chip C4) | Solder bump | 80-150 μm | ~50-150 I/O/mm² |
| 1 (Wire bond) | Au/Cu wire | 35-50 μm pad pitch | Perimeter-limited |
| 1.5 (TSV, interposer) | Cu-filled TSV | 4-10 μm diameter | Array-dependent |
| 2 (BGA) | Solder ball | 300-1,000 μm | ~1-10 I/O/mm² |
| 2 (LGA) | Land pad | 400-1,000 μm | Similar to BGA |
| 3 (Connector) | Pin/blade contact | 0.5-1 mm | Low |

### Visual: Level Hierarchy Signal Path (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 900 620">
\<style\>
.box{fill:#eef4fb;stroke:#2c5f8a;stroke-width:2;}
.lvl0{fill:#ffe9d6;stroke:#b9631f;}
.lvl1{fill:#dff0d8;stroke:#3c8c3c;}
.lvl15{fill:#f6e3f7;stroke:#8c3ca0;}
.lvl2{fill:#fff5cc;stroke:#b8960b;}
.lvl3{fill:#dbe9ff;stroke:#2c5f8a;}
text{font-family:Arial, sans-serif;font-size:14px;fill:#222;}
.tt{font-size:13px;font-weight:bold;}
.lbl{font-size:12px;fill:#444;}
line{stroke:#555;stroke-width:2;marker-end:url(#arrow);}
\</style\>
<text x="300" y="30" class="tt" font-size="18">Die-to-Board Interconnect Hierarchy (svg_diagram)</text>
<rect x="350" y="50" width="200" height="50" rx="6" class="box lvl0" />
<text x="450" y="80" text-anchor="middle" class="tt">Level 0: On-Die BEOL</text>
<line x1="450" y1="100" x2="450" y2="140" />
<rect x="330" y="140" width="240" height="50" rx="6" class="box lvl1" />
<text x="450" y="165" text-anchor="middle" class="tt">Level 0.1: Die-to-Die</text>
<text x="450" y="182" text-anchor="middle" class="lbl">Hybrid bond / micro-bump D2D</text>
<line x1="450" y1="190" x2="450" y2="230" />
<rect x="300" y="230" width="300" height="50" rx="6" class="box lvl1" />
<text x="450" y="255" text-anchor="middle" class="tt">Level 1: Die-to-Package (FLI)</text>
<text x="450" y="272" text-anchor="middle" class="lbl">Flip-chip C4, wire bond, TCB</text>
<line x1="450" y1="280" x2="450" y2="320" />
<rect x="280" y="320" width="340" height="50" rx="6" class="box lvl15" />
<text x="450" y="345" text-anchor="middle" class="tt">Level 1.5: Interposer / Bridge / RDL</text>
<text x="450" y="362" text-anchor="middle" class="lbl">TSV interposer, EMIB, fan-out RDL</text>
<line x1="450" y1="370" x2="450" y2="410" />
<rect x="300" y="410" width="300" height="50" rx="6" class="box lvl2" />
<text x="450" y="435" text-anchor="middle" class="tt">Level 2: Package-to-PCB (SLI)</text>
<text x="450" y="452" text-anchor="middle" class="lbl">BGA, LGA, QFN</text>
<line x1="450" y1="460" x2="450" y2="500" />
<rect x="330" y="500" width="240" height="50" rx="6" class="box lvl3" />
<text x="450" y="525" text-anchor="middle" class="tt">Level 3: Board-to-Board</text>
<text x="450" y="542" text-anchor="middle" class="lbl">Edge connectors, DIMM slots</text>
<line x1="450" y1="550" x2="450" y2="590" />
<text x="450" y="608" text-anchor="middle" class="lbl">Level 4/5: Backplane, Cabling, System-to-System</text>
</svg>

### Manufacturing Domain Transitions

Each level boundary typically corresponds to a change in fabrication ownership and process class:

- **L0 → L1**: Wafer fab (FEOL/BEOL) hands off to OSAT (Outsourced Semiconductor Assembly and Test) or IDM back-end
- **L1 → L1.5**: Advanced packaging facility (interposer fab may be a separate foundry process, e.g., TSMC CoWoS interposer fab distinct from logic fab)
- **L1.5/L2 → L3**: Substrate/package house hands off to PCB assembly (SMT line, reflow oven)
- **L3 → L4/L5**: System integrator/OEM assembly

### Signal Integrity and Electrical Implications by Level

As signals cross from Level 0 to Level 5, characteristic impedance, parasitic inductance, and achievable bandwidth change by orders of magnitude:

$$Z_0 \approx \sqrt{\frac{L}{C}}$$

- **Level 0-1**: Low parasitic inductance (pH range for hybrid bonds), enabling very high-bandwidth, low-power D2D links (e.g., UCIe-Advanced targeting >1 TB/s per mm of shoreline at sub-pJ/bit energy)
- **Level 1.5**: TSV parasitic inductance and RC delay become significant; interposer routing resistance drives IR-drop concerns in power delivery
- **Level 2**: BGA ball inductance (~0.3-1 nH per ball) begins to dominate; return-path discontinuities at the package-to-board transition are a common SI failure point
- **Level 3+**: Connector and via inductance/reflection dominate; requires impedance-controlled PCB stackups and via stub minimization

[Inference] Exact bandwidth and energy-per-bit figures for emerging D2D standards (UCIe, BoW, XSR) continue to evolve rapidly across successive specification revisions, so cited figures should be checked against the latest published spec revision.

### Example: Tracing a Signal Path in a 2.5D GPU Package

1. Signal originates in GPU compute die BEOL metal (Level 0)
2. Exits die through micro-bump at ~40 μm pitch onto silicon interposer (Level 0.1/1)
3. Routes laterally through interposer RDL metal layers to reach HBM stack location (Level 1.5)
4. Passes through interposer TSV to interposer backside micro-bump array
5. Interposer assembly flip-chip bonded to organic package substrate via C4 bumps (Level 1.75/2 boundary)
6. Package substrate BGA balls solder-reflowed onto PCB (Level 2)
7. PCB routes to PCIe edge connector or board-to-board connector (Level 3)
8. Card plugs into server backplane (Level 4)
9. System connects via optical/copper cabling to rack-level fabric (Level 5)

### Key Points

- The die-to-board taxonomy is a mental model for assigning ownership, cost, and performance budgets across the interconnect chain, not a rigid physical standard
- Advanced packaging (2.5D/3D, chiplets) has compressed traditional Level 1 and Level 2 boundaries by inserting interposers, bridges, and hybrid bonding, shifting where the majority of bandwidth/power value is captured
- Each level transition is also a thermal and mechanical stress boundary (CTE mismatch, warpage) in addition to an electrical one
- Standards bodies (JEDEC for L2 BGA, UCIe/OCP for L0.1/L1 die interfaces) govern different levels independently, so a full-stack design requires reconciling multiple standards domains

### Related Topics

- First-level vs. second-level interconnect (FLI/SLI) design rules and reliability testing
- Through-silicon via (TSV) fabrication and reveal processes
- Hybrid bonding (Cu-Cu direct bonding) process flow and yield challenges
- UCIe (Universal Chiplet Interconnect Express) PHY layer specification
- BGA/LGA package-to-board reliability: solder joint fatigue and board-level drop test
- CoWoS, InFO, and EMIB as competing 2.5D integration architectures
- Warpage and CTE mismatch across interconnect levels
- Power delivery network (PDN) design from die to board