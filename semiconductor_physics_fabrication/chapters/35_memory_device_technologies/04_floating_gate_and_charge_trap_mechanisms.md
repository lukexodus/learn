## Floating Gate and Charge Trap Mechanisms

### Overview

Non-volatile memory (NVM) retains stored data without continuous power by trapping charge in a physically isolated region of a MOS transistor's gate stack. The stored charge modulates the transistor's threshold voltage ($V_{th}$), and this shift encodes a logical "0" or "1." Two dominant physical mechanisms accomplish this charge storage: **floating gate (FG)** technology, which uses a continuous conductive layer, and **charge trap (CT)** technology, which uses a discontinuous dielectric layer with localized trap sites. Both underpin Flash memory (NOR and NAND), and their differences in physics drive divergent scaling behavior, reliability characteristics, and manufacturing approaches.

### Basic MOSFET Memory Cell Structure

A conventional memory cell is a MOSFET with an additional charge-storage layer inserted between the channel and the control gate:



```
Control Gate
------------
Inter-poly Dielectric (IPD) / Blocking Oxide
------------
Charge Storage Layer (Floating Gate or Charge Trap Layer)
------------
Tunnel Oxide
------------
Silicon Channel (Source — Channel — Drain)
```

The presence or absence of stored charge in the storage layer shifts $V_{th}$ of the transistor. Reading the cell means applying a gate voltage and sensing whether the transistor conducts — distinguishing a "programmed" (high $V_{th}$) state from an "erased" (low $V_{th}$) state.

### Floating Gate (FG) Mechanism

**Structure**

The floating gate is a continuous, electrically isolated layer of polysilicon (or occasionally a metal) sandwiched between the tunnel oxide and the inter-poly dielectric (IPD, often an ONO — oxide-nitride-oxide — stack). Because it is fully surrounded by insulator, any charge injected onto it is retained indefinitely under ideal conditions.

**Charge Storage Physics**

Since the floating gate is conductive, injected electrons redistribute freely across its entire area, and the entire gate behaves as a single equipotential node. The stored charge $Q_{FG}$ determines the floating gate potential $V_{FG}$:

$$V_{FG} = \frac{C_{CG}}{C_{total}} V_{CG} - \frac{Q_{FG}}{C_{total}}$$

where $C_{CG}$ is the control-gate-to-floating-gate coupling capacitance, $C_{total}$ is the total capacitance seen by the floating gate (control gate, channel, source, drain), and $V_{CG}$ is the applied control gate voltage.

**Coupling Ratio**

A critical design parameter is the **gate coupling ratio (GCR)**:

$$GCR = \frac{C_{CG}}{C_{CG} + C_{channel} + C_{source} + C_{drain}}$$

A high GCR (typically 0.5–0.7) ensures that most of the applied control gate voltage couples onto the floating gate, minimizing the programming/erase voltages required. This is why floating gate cells are typically drawn with a "wing" or wraparound geometry — to maximize $C_{CG}$ relative to parasitic capacitances.

**Programming Mechanisms**

1. **Channel Hot Electron (CHE) Injection** — used in NOR Flash. A high drain-source voltage (~4–5V) combined with a moderate gate voltage accelerates channel electrons near the drain. Some electrons gain enough energy to surmount the ~3.1 eV Si-SiO₂ tunnel oxide barrier and inject onto the floating gate.
2. **Fowler-Nordheim (FN) Tunneling** — used in NAND Flash for both program and erase. A high electric field (~8–10 MV/cm) across the thin tunnel oxide (typically 7–9 nm) allows electrons to quantum-mechanically tunnel through the triangular potential barrier:

$$J_{FN} = A E_{ox}^2 \exp\left(-\frac{B}{E_{ox}}\right)$$

where $J_{FN}$ is tunneling current density, $E_{ox}$ is the oxide electric field, and $A$, $B$ are material-dependent constants.

**Erase Mechanism**

Erase is performed via FN tunneling in the reverse direction — electrons tunnel off the floating gate into the channel or source, typically by applying a high positive voltage to the substrate/well while grounding the control gate (NAND), or via source-side erase (older NOR designs).

**Retention and the Trap-Up Problem**

Because the floating gate is a single conductive node, a single localized defect (pinhole or weak spot) in the surrounding tunnel oxide or IPD provides a leakage path for the *entire* stored charge to escape — a catastrophic, single-point-of-failure retention loss mechanism. This becomes the dominant scaling limitation for FG technology below ~20nm nodes, since thinner oxides have a statistically higher chance of containing such defects (SILC — stress-induced leakage current).

### Charge Trap (CT) Mechanism

**Structure**

The charge storage layer is replaced with a dielectric material containing a high density of localized trap states — most commonly silicon nitride (Si₃N₄) in the classic **SONOS** (Silicon-Oxide-Nitride-Oxide-Silicon) structure, or high-$\kappa$ materials (e.g., HfO₂-based, Al₂O₃) in modern variants (**TANOS**: TaN-Al₂O₃-Nitride-Oxide-Silicon).



```
TANOS Stack Example:
TaN Metal Gate
------------
Al2O3 Blocking Layer (high-k)
------------
Si3N4 Charge Trap Layer
------------
SiO2 Tunnel Oxide
------------
Silicon Channel
```

**Charge Storage Physics**

Unlike the conductive floating gate, the nitride layer is an insulator populated with discrete, spatially localized trap states (dangling bonds, Si-Si bonds, defect states within the nitride bandgap, typically at trap depths of 1.4–1.9 eV below the conduction band). Electrons injected via tunneling become trapped at individual sites and **do not move laterally** through the layer — each trap holds charge independently.

**Programming and Erase Mechanisms**

- **Program**: FN tunneling of electrons from the channel through the thin tunnel oxide into nitride trap states (SONOS/NAND-type CT cells), or CHE injection (embedded/NOR-type CT cells like NROM).
- **Erase**: FN tunneling of holes from the channel into the nitride to recombine with trapped electrons, or reverse tunneling of electrons back to the channel/substrate.

**Retention Advantage**

Because charge is stored in spatially discrete traps rather than a single equipotential node, a localized defect in the tunnel oxide only discharges the traps in its immediate vicinity — not the entire storage node. This makes CT cells inherently more tolerant of tunnel oxide defects and enables **more aggressive tunnel oxide scaling**, which is essential for continued device scaling and 3D integration.

**2-Bit-Per-Cell Capability (NROM)**

Because charge does not migrate within the nitride layer, CT cells can localize distinct charge packets near the source and drain junctions independently, enabling storage of two separate bits per physical cell by reading in both forward and reverse directions (asymmetric sensing) — a technique exploited in NROM-type embedded Flash.

### Comparison Table

| Characteristic | Floating Gate | Charge Trap |
| --- | --- | --- |
| Storage layer | Conductive polysilicon | Insulating dielectric (SiN, high-$\kappa$) |
| Charge distribution | Delocalized (single node) | Localized (discrete traps) |
| Coupling ratio dependency | High — needs large GCR | Lower — direct field coupling |
| Defect tolerance | Poor (single defect drains all charge) | Good (defect drains only local traps) |
| Tunnel oxide thickness | Thicker (~7–9 nm) for retention | Can be thinner — better scalability |
| Cell structure complexity | More complex 3D wing geometry | Simpler planar-friendly structure |
| Multi-bit per cell (spatial) | Not inherent | Native (NROM 2-bit/cell) |
| Dominant modern application | Planar NAND/NOR (legacy, <32nm) | 3D NAND (all major vendors) |
| Endurance | Historically higher | Historically lower (nitride trap degradation), improved in modern high-$\kappa$ stacks |

### Threshold Voltage Window and Multi-Level Cell (MLC) Operation

The difference between erased and programmed $V_{th}$ defines the **read window**. Modern NAND partitions this window into multiple sub-ranges to store more than one bit per cell:

- **SLC** (Single-Level Cell): 1 bit/cell, 2 $V_{th}$ states
- **MLC**: 2 bits/cell, 4 $V_{th}$ states
- **TLC**: 3 bits/cell, 8 $V_{th}$ states
- **QLC**: 4 bits/cell, 16 $V_{th}$ states

Each additional bit per cell tightens the required $V_{th}$ distribution width, demanding finer program-verify algorithms (incremental step pulse programming, ISPP) and placing greater stress on read-margin/retention trade-offs — directly linked to the charge-loss physics described above.

### Why 3D NAND Adopted Charge Trap

The following diagram (svg_diagram) contrasts the two structures in cross-section:

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 820 380">
<text x="200" y="25" font-size="16" font-weight="bold" fill="#1a1a1a">Floating Gate vs Charge Trap Cross-Section (svg_diagram)</text>


<text x="60" y="55" font-size="13" font-weight="bold" fill="#333">Floating Gate</text>

<rect x="40" y="65" width="280" height="25" fill="`#8899aa`" stroke="#333" />

<text x="150" y="82" font-size="11" fill="#fff">Control Gate</text>

<rect x="40" y="90" width="280" height="15" fill="#c9b458" stroke="#333" />
<text x="120" y="101" font-size="9" fill="#333">IPD (ONO)</text>
<rect x="40" y="105" width="280" height="20" fill="#d97a3f" stroke="#333" />
<text x="115" y="119" font-size="10" fill="#fff">Floating Gate (poly-Si)</text>
<circle cx="90" cy="115" r="3" fill="#000" />
<circle cx="130" cy="115" r="3" fill="#000" />
<circle cx="170" cy="115" r="3" fill="#000" />
<circle cx="210" cy="115" r="3" fill="#000" />
<circle cx="250" cy="115" r="3" fill="#000" />
<circle cx="290" cy="115" r="3" fill="#000" />
<text x="60" y="140" font-size="8" fill="#555">(electrons free to move — single node)</text>
<rect x="40" y="150" width="280" height="12" fill="#aabbee" stroke="#333" />
<text x="130" y="159" font-size="9" fill="#333">Tunnel Oxide</text>
<rect x="40" y="162" width="280" height="30" fill="#cccccc" stroke="#333" />
<text x="140" y="180" font-size="10" fill="#333">Si Channel</text>

<path d="M 60 115 L 300 115" stroke="#c00" stroke-width="1.5" stroke-dasharray="3,2" marker-end="url(#arrow)" />
<text x="330" y="118" font-size="9" fill="#c00">defect drains all Q</text>


<text x="480" y="55" font-size="13" font-weight="bold" fill="#333">Charge Trap (SONOS)</text>

<rect x="460" y="65" width="280" height="25" fill="`#8899aa`" stroke="#333" />

<text x="570" y="82" font-size="11" fill="#fff">Control Gate</text>

<rect x="460" y="90" width="280" height="15" fill="#c9b458" stroke="#333" />
<text x="540" y="101" font-size="9" fill="#333">Blocking Oxide</text>
<rect x="460" y="105" width="280" height="20" fill="#5a8f5a" stroke="#333" />
<text x="555" y="119" font-size="10" fill="#fff">Si3N4 Trap Layer</text>
<circle cx="500" cy="112" r="2.5" fill="#000" />
<circle cx="520" cy="118" r="2.5" fill="#000" />
<circle cx="545" cy="110" r="2.5" fill="#000" />
<circle cx="620" cy="119" r="2.5" fill="#000" />
<circle cx="670" cy="113" r="2.5" fill="#000" />
<circle cx="695" cy="117" r="2.5" fill="#000" />
<text x="475" y="140" font-size="8" fill="#555">(electrons localized at discrete traps)</text>
<rect x="460" y="150" width="280" height="12" fill="#aabbee" stroke="#333" />
<text x="550" y="159" font-size="9" fill="#333">Tunnel Oxide</text>
<rect x="460" y="162" width="280" height="30" fill="#cccccc" stroke="#333" />
<text x="560" y="180" font-size="10" fill="#333">Si Channel</text>
<path d="M 500 112 L 545 110" stroke="#0a0" stroke-width="1.5" stroke-dasharray="3,2" />
<text x="560" y="230" font-size="9" fill="#0a0">defect drains only local traps</text>
<text x="40" y="260" font-size="11" fill="#333" font-weight="bold">Implication for 3D NAND:</text>

<text x="40" y="280" font-size="10" fill="#333">Vertical channel etch through 64–232+ stacked layers unavoidably introduces</text>

<text x="40" y="296" font-size="10" fill="#333">sidewall defects. Charge trap's localized storage tolerates these defects,</text>

<text x="40" y="312" font-size="10" fill="#333">while floating gate's single-node storage would fail catastrophically —</text>

<text x="40" y="328" font-size="10" fill="#333">making CT (TANOS-type) the mechanism of choice for all modern 3D NAND (e.g., Samsung V-NAND, Micron/SK Hynix, YMTC Xtacking).</text>

</svg>

### Reliability Mechanisms Common to Both

- **Program/Erase (P/E) Cycling Endurance Degradation**: Repeated FN tunneling generates interface traps and bulk oxide traps in the tunnel oxide via bond-breaking, progressively increasing $SILC$ and degrading both $V_{th}$ window and retention. [Unverified: exact endurance cycle counts vary significantly by vendor, node, and cell type — typical published ranges are ~10⁵–10⁶ for SLC-class cells and ~10³ for TLC/QLC-class cells]
- **Data Retention Loss**: Thermally activated detrapping and tunnel-assisted charge leakage cause $V_{th}$ to drift toward the erased state over time; elevated temperature accelerates this via an Arrhenius-type relationship.
- **Read Disturb**: Repeated read operations apply small stress voltages to unselected cells sharing a bit line/word line, causing gradual unintended charge gain over millions of read cycles.
- **Program Disturb**: Cells sharing a word line with a cell being programmed experience partial field stress, risking unintended $V_{th}$ shift.

### Key Points

- Floating gate: conductive, delocalized charge storage; requires high coupling ratio; vulnerable to single-defect catastrophic leakage; historically dominant in planar NAND/NOR.
- Charge trap: insulating, localized charge storage in discrete traps; more defect-tolerant; enables thinner tunnel oxides and 3D vertical scaling; now standard in 3D NAND via TANOS-type stacks.
- Both rely fundamentally on Fowler-Nordheim tunneling and/or hot-carrier injection for program/erase, governed by the same tunneling current physics, differing primarily in what happens to the electron once it crosses the tunnel oxide.

### Related Topics

- Fowler-Nordheim tunneling and hot-carrier injection physics in detail
- 3D NAND architecture (V-NAND, BiCS, Xtacking) and vertical channel formation
- ONO and high-$\kappa$ blocking layer engineering (Al₂O₃, HfO₂)
- NAND vs NOR Flash array architecture and sensing schemes
- MLC/TLC/QLC programming algorithms (ISPP, program-verify)
- Retention and endurance modeling; SILC and trap-assisted tunneling
- Emerging NVM: MRAM, RRAM, PCM, FeFET as Flash scaling alternatives
- NROM and 2-bit-per-cell embedded charge-trap memory