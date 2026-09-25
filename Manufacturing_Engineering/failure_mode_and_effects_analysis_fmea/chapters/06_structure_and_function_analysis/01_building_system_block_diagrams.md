## Building System Block Diagrams

### Overview

A system block diagram is a graphical representation of a system's architecture that decomposes a product or process into its constituent elements—components, subsystems, interfaces, and their interconnections. Within Structure and Function Analysis (the first pillar of Structure-Function-Failure based FMEA methodologies, including MSR/DRBFM-aligned approaches and AIAG-VDA FMEA), the block diagram is the foundational artifact upon which the P-Diagram, function tree, and failure analysis are built. It answers the question "what does the system consist of, and how do the pieces connect?" before any failure analysis begins.

### Purpose Within FMEA

- Establishes the scope boundary of the analysis (what is in-scope vs. out-of-scope)
- Identifies all physical and logical interfaces between elements, which become sources of interface-related failure modes
- Provides the structural backbone that maps 1:1 to the Structure Tree in AIAG-VDA FMEA
- Ensures no system element is overlooked before functions and failure modes are assigned
- Creates a shared visual reference for cross-functional FMEA teams (design, manufacturing, quality, service)

### Types of Block Diagrams Used in FMEA

**Boundary Diagram**

Shows the system under analysis at the center, surrounded by neighboring systems, users, and environmental influences. Focuses on physical, energy, information, and material interfaces crossing the system boundary. Typically the first diagram built in Design FMEA.

**Functional Block Diagram**

Represents elements by their function rather than physical form, showing functional flow (energy, signal, material) between blocks rather than physical connections.

**Physical/Structural Block Diagram**

Represents actual hardware components, assemblies, and subsystems as blocks, with lines representing physical connections (mechanical, electrical, hydraulic, etc.).

**Process Flow Diagram (Process FMEA equivalent)**

For Process FMEA, the "block diagram" equivalent is the process flow diagram, showing sequential process steps as blocks connected by material/part flow.

### Core Elements of a Block Diagram

| Element | Description | Visual Convention |
| --- | --- | --- |
| Block | A system, subsystem, component, or process step | Rectangle |
| Interface line | Connection representing energy, signal, material, or information transfer | Solid line (physical), dashed line (indirect/signal) |
| Boundary | Scope limit of the analysis | Dashed rectangle enclosing in-scope blocks |
| Arrow | Direction of flow or interaction | Single-headed (one-way) or double-headed (bidirectional) |
| Interface type label | Classification of interface (E, I, M, P) | Small label near the line |

**Standard interface classification (EIMP or similar taxonomies):**

- **E** — Energy transfer (mechanical, electrical, thermal, hydraulic)
- **I** — Information/signal transfer (data, control signals)
- **M** — Material transfer (fluids, particles, physical parts)
- **P** — Physical connection (attachment, proximity, human interface)

### Step-by-Step Process for Building a System Block Diagram

**Step 1: Define System Scope and Boundary**

Determine what is included in the analysis and what is treated as "neighboring system" or environment. This scope decision directly determines FMEA depth and effort.

**Step 2: Identify Major Subsystems and Components**

Decompose the system top-down: System → Subsystem → Component → Part, consistent with the eventual Structure Tree hierarchy.

**Step 3: Draw Blocks for Each Element**

Represent each subsystem/component as a labeled rectangle. Keep the hierarchy level consistent within a single diagram (don't mix system-level and part-level blocks in the same diagram without a clear hierarchy indicator).

**Step 4: Identify and Draw Interfaces**

For every pair of blocks that interact, draw a connecting line. Label the interface with its type (E/I/M/P) and, if useful, a brief description (e.g., "12V DC power," "CAN bus signal," "coolant flow").

**Step 5: Classify Interface Significance**

Common convention (per AIAG-VDA and boundary diagram best practice):

- **+ (plus)** — Beneficial/necessary interface
- **– (minus)** — Adverse or unwanted interface
- **0 (neutral)** — No significant effect
- **? (unknown)** — Interface effect not yet understood, requiring further investigation

**Step 6: Validate with Cross-Functional Team**

Review the diagram with design, manufacturing, and systems engineers to confirm completeness and correctness before proceeding to function analysis.

**Step 7: Link to Structure Tree**

Convert the block diagram hierarchy into the formal Structure Tree used in the FMEA worksheet, ensuring every block has a corresponding node.

### Example: Automotive Power Window System

**System boundary:** Power Window Subsystem (door-mounted)

**Key blocks:** Window Switch, Body Control Module (BCM), Window Motor, Regulator Mechanism, Glass Pane, Door Wiring Harness, Vehicle Battery (external), Door Frame (external/interfacing)

**Key interfaces:**

- Switch → BCM: electrical signal (I)
- BCM → Motor: electrical power + control signal (E, I)
- Motor → Regulator: mechanical torque (E)
- Regulator → Glass: mechanical linear force (E)
- Glass → Door Frame: physical sliding contact (P)
- Battery → BCM/Motor: electrical power (E)

### SVG Diagram: Power Window Boundary Diagram

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 780 460" font-family="Arial, sans-serif">
<title>Power Window System Boundary Diagram (svg_diagram)</title>
<rect x="0" y="0" width="780" height="460" fill="#ffffff" />
<text x="390" y="28" font-size="16" font-weight="bold" text-anchor="middle" fill="#1a1a1a">Power Window System Boundary Diagram (svg_diagram)</text>
<rect x="150" y="70" width="480" height="300" rx="6" fill="none" stroke="#555555" stroke-width="2" stroke-dasharray="8,5" />
<text x="390" y="60" font-size="13" text-anchor="middle" fill="#555555">System Boundary</text>
<rect x="180" y="100" width="130" height="55" rx="4" fill="#dbeafe" stroke="#1d4ed8" stroke-width="1.5" />
<text x="245" y="132" font-size="12" text-anchor="middle">Window Switch</text>
<rect x="180" y="200" width="130" height="55" rx="4" fill="#dbeafe" stroke="#1d4ed8" stroke-width="1.5" />
<text x="245" y="232" font-size="12" text-anchor="middle">BCM</text>
<rect x="360" y="200" width="130" height="55" rx="4" fill="#dbeafe" stroke="#1d4ed8" stroke-width="1.5" />
<text x="425" y="225" font-size="12" text-anchor="middle">Window Motor</text>
<rect x="360" y="300" width="130" height="55" rx="4" fill="#dbeafe" stroke="#1d4ed8" stroke-width="1.5" />
<text x="425" y="325" font-size="12" text-anchor="middle">Regulator</text>
<text x="425" y="340" font-size="12" text-anchor="middle">Mechanism</text>
<rect x="180" y="300" width="130" height="55" rx="4" fill="#dbeafe" stroke="#1d4ed8" stroke-width="1.5" />
<text x="245" y="332" font-size="12" text-anchor="middle">Glass Pane</text>
<rect x="30" y="200" width="110" height="55" rx="4" fill="#fef3c7" stroke="#b45309" stroke-width="1.5" />
<text x="85" y="225" font-size="12" text-anchor="middle">Vehicle</text>
<text x="85" y="240" font-size="12" text-anchor="middle">Battery</text>
<rect x="640" y="300" width="110" height="55" rx="4" fill="#fef3c7" stroke="#b45309" stroke-width="1.5" />
<text x="695" y="325" font-size="12" text-anchor="middle">Door</text>
<text x="695" y="340" font-size="12" text-anchor="middle">Frame</text>
<line x1="245" y1="155" x2="245" y2="200" stroke="#1a1a1a" stroke-width="1.5" marker-end="url(#arrow)" />
<text x="255" y="180" font-size="10">I, +</text>
<line x1="310" y1="227" x2="360" y2="227" stroke="#1a1a1a" stroke-width="1.5" marker-end="url(#arrow)" />
<text x="318" y="220" font-size="10">E/I, +</text>
<line x1="425" y1="255" x2="425" y2="300" stroke="#1a1a1a" stroke-width="1.5" marker-end="url(#arrow)" />
<text x="432" y="280" font-size="10">E, +</text>
<line x1="360" y1="327" x2="310" y2="327" stroke="#1a1a1a" stroke-width="1.5" marker-end="url(#arrow)" />
<text x="318" y="318" font-size="10">E, +</text>
<line x1="140" y1="227" x2="180" y2="227" stroke="#1a1a1a" stroke-width="1.5" marker-end="url(#arrow)" />
<text x="145" y="220" font-size="10">E, +</text>
<line x1="310" y1="327" x2="640" y2="327" stroke="#1a1a1a" stroke-width="1.5" stroke-dasharray="4,3" marker-end="url(#arrow)" />
<text x="470" y="318" font-size="10">P, ?</text>
<text x="390" y="410" font-size="11" fill="`#555555`" text-anchor="middle">Legend: E = Energy, I = Information, P = Physical | + beneficial, – adverse, ? unknown</text>

<text x="390" y="430" font-size="11" fill="`#555555`" text-anchor="middle">Solid line = direct interface, Dashed line = indirect/friction interface</text>

</svg>

### Diagramming Conventions and Best Practices

- **Consistent abstraction level:** Avoid mixing subsystem-level blocks with individual fastener-level detail in the same diagram
- **Limit block count per diagram:** Typically 5–15 blocks per diagram for readability; decompose further into child diagrams for complex systems
- **Bidirectional interfaces:** Use double-headed arrows only when interaction truly flows both ways (e.g., data handshake); otherwise use directional arrows
- **Color coding:** Common convention uses distinct colors for energy (red/orange), signal (blue), material (green), and physical (gray) interfaces
- **Numbering:** Assign unique interface IDs (e.g., IF-01, IF-02) for traceability into the FMEA worksheet's interface analysis column
- **External elements:** Systems, users, or environmental factors outside the boundary should be visually distinguished (e.g., different fill color, placed outside the dashed boundary line)

### Process Flow Diagram Example (Process FMEA Context)

```mermaid
flowchart LR
    A[Receive Raw Material] --> B[Incoming Inspection]
    B --> C[CNC Machining]
    C --> D[Deburring]
    D --> E[Surface Treatment]
    E --> F[Dimensional Inspection]
    F --> G[Assembly]
    G --> H[Functional Test]
    H --> I[Packaging]
    I --> J[Shipment]
```

Each block in this process flow becomes a process step in the Process FMEA structure tree, with sub-elements (machine, material, method, man, environment — the 4M/5M) analyzed for each step.

### Common Pitfalls

- **Skipping the boundary diagram** and jumping directly to failure modes, resulting in missed interface-related failure modes (a leading cause of field failures in complex systems)
- **Omitting indirect/adverse interfaces** such as vibration, heat radiation, or EMI, which are non-obvious but often safety-critical
- **Inconsistent hierarchy** between the block diagram and the later Structure Tree, causing traceability gaps in the FMEA worksheet
- **Treating the diagram as a one-time artifact** rather than a living document updated as design changes occur
- [Inference] Teams that skip formal interface classification (E/I/M/P) tend to under-identify interface failure modes during the subsequent Function and Failure Analysis steps, though the magnitude of this effect is not independently benchmarked and will vary by team maturity and system complexity.

### Tools Commonly Used

- Microsoft Visio, Lucidchart, draw.io — general-purpose diagramming
- Dedicated FMEA software (APIS IQ-FMEA, PTC Windchill FMEA, Plato e1ns) — often auto-links block diagrams to the Structure Tree
- SysML Block Definition Diagrams (BDD) / Internal Block Diagrams (IBD) — for organizations using Model-Based Systems Engineering (MBSE) integration with FMEA

**Related Topics**

- Boundary diagrams and interface analysis
- P-Diagrams (Parameter Diagrams)
- Structure Trees in AIAG-VDA FMEA
- Function trees and function analysis
- Interface failure modes and classification (E/I/M/P)
- Process flow diagrams for Process FMEA
- Linking structure analysis to failure mode identification