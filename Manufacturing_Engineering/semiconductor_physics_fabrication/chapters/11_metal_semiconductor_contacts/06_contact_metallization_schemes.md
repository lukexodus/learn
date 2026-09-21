## Contact Metallization Schemes


### Overview

Contact metallization refers to the engineered stack of metal (and often metal compound) layers deposited on a semiconductor surface to form electrical contacts — either rectifying (Schottky) or non-rectifying (ohmic). Rarely is a single pure metal layer used in production devices; instead, multi-layer metallization schemes are designed to simultaneously satisfy electrical, thermal, mechanical, and chemical-stability requirements. Each layer in the stack typically serves a distinct functional role.

### Functional Layer Roles in a Metallization Stack

**Contact/Adhesion Layer**

- Directly interfaces with the semiconductor.
- Chosen to promote strong adhesion, low barrier height (for ohmic contacts) or controlled barrier height (for Schottky contacts), and chemical compatibility.
- Examples: Ti, Cr, Ni, Pd, Pt.

**Diffusion Barrier Layer**

- Prevents interdiffusion or reaction between the top conductive layer and the semiconductor (or contact layer) during subsequent high-temperature processing.
- Must remain thermally and chemically stable, typically amorphous or fine-grained to block grain-boundary diffusion paths.
- Examples: TiN, TaN, WN, Ti-W alloy.

**Conductive/Bulk Layer**

- Provides the primary low-resistance current path and mechanical bulk of the interconnect.
- Chosen for high electrical conductivity and compatibility with wire bonding, solder bumping, or further interconnect processing.
- Examples: Al, Al-Cu alloys, Cu, Au.

**Capping/Protection Layer**

- Prevents oxidation, corrosion, or contamination of the underlying conductive layer.
- Provides a bondable or solderable surface.
- Examples: Au, Pd, Ni (in Ni/Au or Ni/Pd/Au finishes).

### Representative Metallization Schemes by Semiconductor System

**Silicon: Ohmic Contacts**

- **Al on p⁺-Si or n⁺-Si**: Historically dominant; forms ohmic contact via heavy doping and post-deposition sintering (typically ~400-450°C in forming gas), which allows Al to alloy locally with Si and reduce interfacial states.
- **Ti/TiN/Al(Cu) or Ti/TiN/W**: Modern VLSI contact stack. Ti serves as the contact/adhesion layer and reacts with Si to form TiSi₂ (a low-resistivity silicide), TiN acts as a diffusion barrier against Al-Si interdiffusion (preventing "spiking"), and Al(Cu) or W fills the contact via.
- **Silicide formation**: TiSi₂, CoSi₂, and NiSi are widely used self-aligned silicide ("salicide") contacts formed by depositing the metal and annealing to react selectively with exposed Si, followed by selective wet etch of unreacted metal.

**Silicon: Schottky Contacts**

- **PtSi, Pd₂Si**: Platinum or palladium silicides formed by controlled reaction, offering well-defined, reproducible barrier heights on n-Si, used historically in Schottky diode and infrared detector applications.
- **W, Ti**: Used where moderate barrier heights and thermal stability are required.

**GaAs and III-V Compound Semiconductors: Ohmic Contacts**

- **AuGeNi (Au-Ge eutectic with Ni)**: Classic ohmic contact scheme for n-GaAs. Deposited as a layered or alloyed stack, then annealed (typically 400-450°C) to form a regrown, heavily-doped n⁺ interfacial layer via Ge diffusion, enabling tunneling-dominated conduction through the pinned Schottky barrier.
- **Pd/Ge/Au or Pd/Ge/Ti/Au**: Alternative non-Au-eutectic-based schemes offering improved surface morphology and lower contact resistance uniformity compared to AuGeNi.
- **Ti/Pt/Au**: Common p-type ohmic and general-purpose III-V metallization; Ti provides adhesion, Pt acts as diffusion barrier, Au provides low-resistance conduction and bondability.

**GaAs and III-V: Schottky Contacts**

- **Ti/Pt/Au or Al**: Standard Schottky gate metallization for GaAs MESFETs and HEMTs, chosen for well-controlled barrier height and thermal stability under operating bias.
- **WSiN or refractory metal gates**: Used in self-aligned gate processes requiring high-temperature stability during subsequent anneals.

**Wide-Bandgap Semiconductors (SiC, GaN)**

- **Ohmic contacts on n-SiC**: Ni or Ni/Ti stacks annealed at high temperature (~950-1050°C) to form conductive Ni-silicide/carbon-rich interfacial layers.
- **Ohmic contacts on p-SiC**: Al/Ti or Al/Ni stacks, generally requiring higher anneal temperatures and more process optimization due to higher intrinsic barrier heights on p-type material.
- **GaN ohmic contacts**: Ti/Al/Ni/Au multilayer stacks annealed at ~800-900°C; Ti reacts with the GaN surface to promote nitrogen vacancy formation (n⁺-like behavior) enabling tunneling conduction, Al prevents Au-Ti intermixing, Ni/Au caps for oxidation resistance and bonding.
- **GaN Schottky/gate contacts**: Ni/Au or Pt-based stacks for high barrier height and thermal stability in HEMT gate applications.

### Process Considerations

**Deposition Techniques**

- Physical Vapor Deposition (PVD): sputtering and e-beam evaporation, most common for metallization stacks due to good thickness control and compatibility with lift-off patterning.
- Chemical Vapor Deposition (CVD): used for conformal diffusion barrier and fill layers (e.g., CVD W plugs).
- Atomic Layer Deposition (ALD): increasingly used for ultra-thin diffusion barriers (TiN, TaN) in advanced nodes requiring precise thickness control and conformality in high-aspect-ratio contacts.

**Post-Deposition Annealing (Rapid Thermal Annealing, RTA)**

- Critical for silicide/ohmic contact formation, activating dopants, and relieving interfacial stress.
- Must be carefully controlled: insufficient thermal budget yields incomplete reaction and high contact resistance; excessive thermal budget causes unwanted interdiffusion, agglomeration, or junction spiking (particularly in shallow junctions).

**Patterning**

- Lift-off process: photoresist patterning followed by metal deposition and resist removal; suited for research-scale and III-V processes.
- Etch-based patterning: metal blanket deposition followed by photolithography and dry/wet etch; standard for high-volume Si CMOS due to superior dimensional control.

**Failure Modes Addressed by Multilayer Design**

- **Junction spiking**: Al directly contacting shallow Si junctions can locally dissolve Si and penetrate through the junction; mitigated by TiN/TiW barrier layers.
- **Electromigration**: Current-induced metal atom migration, particularly in Al interconnects; addressed via Cu adoption (with dedicated barrier/liner schemes such as Ta/TaN) and alloying (Al-Cu).
- **Kirkendall voiding**: Asymmetric interdiffusion at bimetallic interfaces (e.g., Au-Al), causing void formation and mechanical/electrical failure; mitigated by diffusion barrier insertion and material selection.

### Metallization Stack Cross-Section (Generic VLSI Contact)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 380" font-family="Arial, sans-serif">
<text x="350" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#222">Generic Multilayer Contact Stack (svg_diagram)</text>

<rect x="150" y="300" width="400" height="50" fill="#d9d2c5" stroke="#333" />
<text x="350" y="330" text-anchor="middle" font-size="12" fill="#333">Si substrate (n+/p+ diffusion region)</text>

<rect x="230" y="280" width="240" height="20" fill="#e8b04b" stroke="#333" />
<text x="350" y="294" text-anchor="middle" font-size="10" fill="#333">TiSi2 / silicide (contact layer)</text>

<rect x="230" y="255" width="240" height="25" fill="#8899aa" stroke="#333" />
<text x="350" y="271" text-anchor="middle" font-size="10" fill="#fff">TiN (diffusion barrier)</text>

<rect x="230" y="150" width="240" height="105" fill="#b7c7e0" stroke="#333" />
<text x="350" y="205" text-anchor="middle" font-size="11" fill="#222">W plug / Al(Cu) fill</text>
<text x="350" y="222" text-anchor="middle" font-size="10" fill="#333">(bulk conductive layer)</text>

<rect x="150" y="150" width="80" height="130" fill="#eef1f5" stroke="#333" />
<rect x="470" y="150" width="80" height="130" fill="#eef1f5" stroke="#333" />
<text x="190" y="220" text-anchor="middle" font-size="9" fill="#555" transform="rotate(-90 190 220)">SiO2 ILD</text>
<text x="510" y="220" text-anchor="middle" font-size="9" fill="#555" transform="rotate(-90 510 220)">SiO2 ILD</text>

<rect x="150" y="120" width="400" height="30" fill="#9fb8d9" stroke="#333" />
<text x="350" y="140" text-anchor="middle" font-size="11" fill="#222">Metal 1 interconnect (Al-Cu / Cu)</text>


<text x="600" y="290" font-size="9" fill="#555">← low-resistivity ohmic contact</text>

<text x="600" y="267" font-size="9" fill="#555">← blocks interdiffusion</text>

<text x="600" y="200" font-size="9" fill="#555">← main current path</text>

</svg>

### Barrier Height and Contact Resistivity Summary Table

| System | Contact Type | Common Metallization | Typical Anneal | Primary Role of Each Layer |
| --- | --- | --- | --- | --- |
| n-Si | Ohmic | Ti/TiN/W or Al(Cu) | ~450–700°C (silicide/spike-free) | Ti: silicide/adhesion; TiN: barrier; W/Al: fill |
| Si | Schottky | PtSi, Pd2Si | Controlled silicidation anneal | Defined barrier height, thermal stability |
| n-GaAs | Ohmic | AuGeNi or Pd/Ge/Au | ~400–450°C | Ge: n+ regrowth/tunneling; Au: conduction |
| GaAs | Schottky | Ti/Pt/Au | None (as-deposited) | Ti: barrier control; Pt: barrier diffusion block; Au: cap |
| n-SiC | Ohmic | Ni or Ni/Ti | ~950–1050°C | Ni-silicide/carbon layer formation |
| n-GaN | Ohmic | Ti/Al/Ni/Au | ~800–900°C | Ti: N-vacancy/tunneling; Al: barrier vs Au-Ti reaction; Ni/Au: cap |

### Key Points

- Practical contacts use multilayer metallization stacks, not single metals, to separately optimize adhesion/barrier height, diffusion resistance, conductivity, and oxidation protection.
- Silicide formation (TiSi₂, NiSi, CoSi₂) is central to modern Si ohmic and Schottky contacts.
- III-V contacts (GaAs, GaN) commonly rely on alloyed/annealed stacks that create a heavily doped interfacial region enabling tunneling conduction through an otherwise pinned Schottky barrier.
- Wide-bandgap semiconductors (SiC, GaN) require significantly higher anneal temperatures for ohmic contact formation than Si or GaAs.
- Diffusion barrier layers (TiN, TaN, Pt) are essential to prevent junction spiking, electromigration-related failures, and Kirkendall voiding.

### Related Topics

- Silicide formation kinetics and phases (C49/C54 TiSi2, NiSi vs NiSi2)
- Specific contact resistivity measurement (TLM, Cox-Strack methods)
- Electromigration mechanisms in Cu and Al interconnects
- Rapid thermal annealing (RTA) process optimization
- Contact resistance scaling challenges in advanced CMOS nodes
- Ohmic contact formation on wide-bandgap semiconductors (SiC, GaN)
- Damascene and dual-damascene Cu interconnect processing