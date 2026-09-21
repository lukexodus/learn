## DIN 8580 Six-Main-Group System Overview

### Overview

DIN 8580 is the German national standard defining manufacturing processes (*Fertigungsverfahren*), first issued in 1985 and periodically revised since (most recently reaffirmed/updated editions extending into the 2020s). It establishes a hierarchical classification of all manufacturing processes into six main groups (*Hauptgruppen*), organized around the fundamental transformation the process performs on material cohesion (*Stoffzusammenhalt* — literally "material cohesion" or "material bond"). This standard predates and substantially influenced later international harmonization efforts, including aspects of ISO process classification work.

### The Classifying Principle: Material Cohesion

DIN 8580's central organizing axis is not feedstock state, tooling type, or application, but **how the process changes the cohesion of the material** — whether cohesion is created, maintained, increased, decreased, or otherwise altered between particles/regions of the workpiece. This is a more abstract and physically fundamental axis than the "casting/forming/machining/joining" grouping common in Anglo-American textbooks, and it is what allows DIN 8580 to place all conventional manufacturing processes into exactly six mutually exclusive groups.

### The Six Main Groups

| # | German Term | English Term | Core Definition |
| --- | --- | --- | --- |
| 1 | **Urformen** | Primary Shaping | Creating a solid body from a shapeless material (liquid, powder, gas, or ionized state), establishing material cohesion for the first time |
| 2 | **Umformen** | Forming | Plastic deformation of an already-solid body while preserving mass and cohesion; only geometry changes |
| 3 | **Trennen** | Separating | Reducing material cohesion locally to remove material or divide the workpiece (includes machining, cutting, and disassembly) |
| 4 | **Fügen** | Joining | Increasing/establishing cohesion between two or more discrete workpieces or between a workpiece and formless material |
| 5 | **Beschichten** | Coating | Applying a layer of formless material onto a solid workpiece surface, establishing cohesion between the coating and the substrate |
| 6 | **Stoffeigenschaftändern** | Changing Material Properties | Altering the material's properties (e.g., microstructure, hardness) without deliberately changing its macroscopic shape or its external material connections |

### Group 1: Urformen (Primary Shaping)

**Key Points**

- Defining feature: the workpiece does not exist as a coherent solid before the process begins. Material cohesion is created for the first time from a shapeless state (molten liquid, powder, granulate, gas/vapor, or ionized state).
- Subcategories include casting (*Gießen*), powder metallurgy/sintering (*Sintern*), and — in later interpretive extensions discussed by standards commentators — additive manufacturing is frequently positioned within or adjacent to this group, since AM likewise creates a solid part from a formless feedstock (powder, resin, filament).
- [Inference] DIN 8580's original 1985 structure predates commercial AM and does not explicitly enumerate it; subsequent commentary and some regional standards discussions have proposed treating layer-based AM as a distinct subclass within Urformen (since AM creates cohesion from a formless state) rather than as a wholly separate seventh main group, which is a notable structural contrast to how ISO/ASTM 52900 ultimately chose to treat AM as an independent, co-equal framework rather than nesting it under an existing DIN group.

### Group 2: Umformen (Forming)

**Key Points**

- Defining feature: the workpiece already exists as a coherent solid; mass and material cohesion are preserved, and only shape is changed via plastic deformation.
- DIN 8582 (a sub-standard under the 8580 family) further divides forming by the state of stress applied: compressive forming (*Druckumformen*, e.g., rolling, forging, extrusion), tensile forming (*Zugumformen*, e.g., stretch forming), combined tensile-compressive forming (*Zugdruckumformen*, e.g., deep drawing), bending (*Biegeumformen*), and shear forming (*Schubumformen*).
- This stress-state-based subdivision is more granular than typical Anglo-American forming taxonomies, which often organize forming processes primarily by application (sheet metal forming vs. bulk forming) rather than by the underlying stress state.

### Group 3: Trennen (Separating)

**Key Points**

- Defining feature: material cohesion is locally reduced or eliminated, either to remove material from a workpiece or to divide a workpiece/assembly into parts.
- DIN 8589 subdivides this group extensively, covering: cutting with geometrically defined cutting edges (*Zerteilen* and machining processes like turning, milling, drilling — where the cutting edge geometry is precisely known), machining with geometrically undefined cutting edges (*Spanen mit geometrisch unbestimmter Schneide*, e.g., grinding, honing, lapping, where abrasive grain geometry is statistically distributed rather than precisely defined), and disassembly/dismantling processes.
- This geometrically-defined vs. geometrically-undefined cutting-edge distinction is a DIN-specific taxonomic refinement not always present with equal prominence in other national classification traditions, and it is one of the more frequently cited structural contributions of DIN 8580 to international machining classification discourse.

### Group 4: Fügen (Joining)

**Key Points**

- Defining feature: material cohesion is created or increased between two or more previously separate workpieces, or between a workpiece and added formless material.
- DIN 8593 subdivides joining into six further subgroups: joining by primary shaping (*Fügen durch Urformen*), joining by forming (*Fügen durch Umformen*, e.g., press fits, crimping), joining by filling (*Füllen*), joining by pressing-in (*Anpressen*), joining by welding (*Fügen durch Schweißen*), and joining by adhesive bonding (*Kleben*).
- This subdivision structure notably classifies welding as a species of the broader Fügen category rather than as a wholly separate top-level process family, contrasting with taxonomies (including some Anglo-American ones) that treat welding as a peer category to casting/forming/machining.

### Group 5: Beschichten (Coating)

**Key Points**

- Defining feature: application of a layer of formless material onto an existing solid substrate, establishing new cohesion between coating and substrate without altering the substrate's core geometry.
- Covers processes such as electroplating, painting, thermal spraying, and vapor deposition (PVD/CVD).
- DIN 8580 explicitly separates coating from Group 1 (Urformen) even though both involve forming solid material from a formless state, because coating is defined by application to an existing substrate rather than creation of a standalone body — a distinction that becomes classificatorily important in additive manufacturing contexts where processes like Directed Energy Deposition sit near this coating/primary-shaping boundary depending on whether material is deposited onto a substrate or built up freestanding.

### Group 6: Stoffeigenschaftändern (Changing Material Properties)

**Key Points**

- Defining feature: alters internal material properties (microstructure, hardness, residual stress state, surface properties) without deliberately changing macroscopic shape or establishing/breaking external material connections.
- Covers heat treatment processes (annealing, quenching, tempering, case hardening), and property-changing processes applied to particle/fiber composites.
- This group is notable for having no direct equivalent as a standalone top-level category in most Anglo-American textbook taxonomies, where heat treatment is typically treated as a secondary or auxiliary process rather than a co-equal main classification group — one of DIN 8580's more distinctive structural choices.

### Diagram: DIN 8580 Six-Group Structure (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 900 480">
<text x="450" y="30" text-anchor="middle" font-size="18" font-weight="bold">DIN 8580 — Fertigungsverfahren (svg_diagram)</text>
<rect x="370" y="50" width="160" height="40" fill="none" stroke="black" stroke-width="2" />
<text x="450" y="75" text-anchor="middle" font-size="13">Stoffzusammenhalt</text>
<line x1="450" y1="90" x2="450" y2="120" stroke="black" stroke-width="1.5" />
<line x1="80" y1="120" x2="820" y2="120" stroke="black" stroke-width="1.5" />
<line x1="80" y1="120" x2="80" y2="150" stroke="black" stroke-width="1.5" />
<line x1="230" y1="120" x2="230" y2="150" stroke="black" stroke-width="1.5" />
<line x1="380" y1="120" x2="380" y2="150" stroke="black" stroke-width="1.5" />
<line x1="530" y1="120" x2="530" y2="150" stroke="black" stroke-width="1.5" />
<line x1="680" y1="120" x2="680" y2="150" stroke="black" stroke-width="1.5" />
<line x1="820" y1="120" x2="820" y2="150" stroke="black" stroke-width="1.5" />
<rect x="10" y="150" width="140" height="70" fill="none" stroke="black" stroke-width="1.5" />
<text x="80" y="175" text-anchor="middle" font-size="12" font-weight="bold">1. Urformen</text>
<text x="80" y="192" text-anchor="middle" font-size="10">Primary Shaping</text>
<text x="80" y="208" text-anchor="middle" font-size="9">create cohesion</text>
<rect x="160" y="150" width="140" height="70" fill="none" stroke="black" stroke-width="1.5" />
<text x="230" y="175" text-anchor="middle" font-size="12" font-weight="bold">2. Umformen</text>
<text x="230" y="192" text-anchor="middle" font-size="10">Forming</text>
<text x="230" y="208" text-anchor="middle" font-size="9">preserve cohesion</text>
<rect x="310" y="150" width="140" height="70" fill="none" stroke="black" stroke-width="1.5" />
<text x="380" y="175" text-anchor="middle" font-size="12" font-weight="bold">3. Trennen</text>
<text x="380" y="192" text-anchor="middle" font-size="10">Separating</text>
<text x="380" y="208" text-anchor="middle" font-size="9">reduce cohesion</text>
<rect x="460" y="150" width="140" height="70" fill="none" stroke="black" stroke-width="1.5" />
<text x="530" y="175" text-anchor="middle" font-size="12" font-weight="bold">4. Fügen</text>
<text x="530" y="192" text-anchor="middle" font-size="10">Joining</text>
<text x="530" y="208" text-anchor="middle" font-size="9">increase cohesion</text>
<rect x="610" y="150" width="140" height="70" fill="none" stroke="black" stroke-width="1.5" />
<text x="680" y="175" text-anchor="middle" font-size="12" font-weight="bold">5. Beschichten</text>
<text x="680" y="192" text-anchor="middle" font-size="10">Coating</text>
<text x="680" y="208" text-anchor="middle" font-size="9">add layer cohesion</text>
<rect x="750" y="150" width="140" height="70" fill="none" stroke="black" stroke-width="1.5" />
<text x="820" y="172" text-anchor="middle" font-size="11" font-weight="bold">6. Stoffeigenschaft-</text>
<text x="820" y="188" text-anchor="middle" font-size="11" font-weight="bold">ändern</text>
<text x="820" y="205" text-anchor="middle" font-size="9">change properties</text>

<text x="80" y="250" text-anchor="middle" font-size="9">casting,</text>

<text x="80" y="263" text-anchor="middle" font-size="9">sintering,</text>

<text x="80" y="276" text-anchor="middle" font-size="9">(AM discussed)</text>

<text x="230" y="250" text-anchor="middle" font-size="9">rolling, forging,</text>

<text x="230" y="263" text-anchor="middle" font-size="9">extrusion,</text>

<text x="230" y="276" text-anchor="middle" font-size="9">deep drawing</text>

<text x="380" y="250" text-anchor="middle" font-size="9">turning, milling,</text>

<text x="380" y="263" text-anchor="middle" font-size="9">grinding,</text>

<text x="380" y="276" text-anchor="middle" font-size="9">disassembly</text>

<text x="530" y="250" text-anchor="middle" font-size="9">welding, adhesive</text>

<text x="530" y="263" text-anchor="middle" font-size="9">bonding, press</text>

<text x="530" y="276" text-anchor="middle" font-size="9">fitting</text>

<text x="680" y="250" text-anchor="middle" font-size="9">electroplating,</text>

<text x="680" y="263" text-anchor="middle" font-size="9">painting,</text>

<text x="680" y="276" text-anchor="middle" font-size="9">PVD/CVD</text>

<text x="820" y="250" text-anchor="middle" font-size="9">annealing,</text>

<text x="820" y="263" text-anchor="middle" font-size="9">quenching,</text>

<text x="820" y="276" text-anchor="middle" font-size="9">case hardening</text>

<rect x="10" y="320" width="880" height="140" fill="none" stroke="black" stroke-width="1" stroke-dasharray="4,3" />
<text x="450" y="345" text-anchor="middle" font-size="12" font-weight="bold">Distinctive DIN 8580 Structural Choices</text>
<text x="30" y="370" font-size="10">• Welding classified as a Fügen subgroup, not a top-level category (contrasts with some Anglo-American schemes)</text>
<text x="30" y="390" font-size="10">• Heat treatment (Group 6) is a co-equal main group — rare among international taxonomies</text>
<text x="30" y="410" font-size="10">• Machining split by cutting-edge geometry: geometrically defined vs. undefined (DIN 8589)</text>
<text x="30" y="430" font-size="10">• Classifying axis is material cohesion change, not feedstock state or application purpose</text>
</svg>

### Comparison to Anglo-American Four-Family Taxonomy

| DIN 8580 Group | Closest Anglo-American Equivalent | Structural Difference |
| --- | --- | --- |
| Urformen | Casting/Molding | DIN also includes powder metallurgy and (per later commentary) AM under the same cohesion-creation logic |
| Umformen | Forming/Deformation | Broadly equivalent; DIN's stress-state subdivision (DIN 8582) is more granular |
| Trennen | Machining/Material Removal | DIN explicitly separates geometrically defined vs. undefined cutting edges as a first-order distinction |
| Fügen | Joining | DIN nests welding, adhesive bonding, and mechanical joining under one cohesion-based logic rather than treating welding as separate |
| Beschichten | (often folded into "joining" or treated as a specialty topic) | DIN elevates coating to a full co-equal main group |
| Stoffeigenschaftändern | (typically not a top-level category) | DIN's most structurally distinctive group; usually absent as a peer category elsewhere |

### Relevance to Additive Manufacturing Classification (Cross-Reference)

As discussed in this chapter's earlier historical material, ISO/ASTM 52900 ultimately classified AM as an independent, co-equal framework (parallel to, rather than nested within, subtractive/forming/joining superclasses). DIN 8580's cohesion-based logic offers an alternative interpretive lens: since AM creates material cohesion from a formless feedstock, it arguably fits the *conceptual* definition of Urformen (Primary Shaping) more naturally than it fits any Anglo-American "casting" category. [Inference] This suggests DIN 8580's abstract cohesion-based axis may have been structurally better positioned to absorb AM without requiring a new top-level group than the feedstock/application-based Anglo-American four-family model was — though DIN 8580 itself has not been formally revised to explicitly reclassify AM as an Urformen subtype in a way that fully supersedes the ISO/ASTM 52900 independent-framework approach, so this remains an interpretive observation rather than settled standards text.

**Related Topics**

- DIN 8582 (forming process subdivision by stress state)
- DIN 8589 (separating/machining process subdivision, geometrically defined vs. undefined cutting edges)
- DIN 8593 (joining process subdivision, six subgroups)
- Comparison of DIN 8580 against ISO 3002/ISO 513 machining classification
- Structural comparison: DIN 8580 six-group model vs. ISO/ASTM 52900 AM-as-independent-framework model
- Heat treatment classification as a standalone main group vs. auxiliary process