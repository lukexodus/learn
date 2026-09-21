## American Welding Society Taxonomic Tradition

### Overview

The American Welding Society (AWS) taxonomic tradition refers to the systematic classification framework for joining, cutting, and allied processes codified primarily in **AWS A3.0M/A3.0**, *Standard Welding Terms and Definitions*. This document, maintained by the AWS Committee on Definitions and Symbols, establishes a hierarchical, letter-designation-based taxonomy that has become the dominant reference schema for welding process classification in North America, distinguishing itself from the ISO 4063 numeric coding tradition used more broadly internationally.

The taxonomy's core contribution is the **Master Chart of Welding and Allied Processes**, a tree-structured diagram that groups all recognized joining and cutting processes into major families, each assigned a standardized letter designation (e.g., SMAW, GMAW, GTAW) used consistently across AWS codes, drawings, procedure specifications, and welder qualification documents.

### Historical Development

**Key Points**

- Origins trace to early 20th-century AWS standardization efforts as arc and gas welding proliferated industrially, with each manufacturer and trade using inconsistent terminology.
- The first formalized terms and definitions standard emerged in the 1940s–1950s, coinciding with wartime shipbuilding and structural steel demand that required interoperable welding procedure documentation across contractors.
- AWS A3.0 has undergone multiple revisions (notably 1989, 1994, 2001, 2010, and 2020 editions), each expanding the Master Chart to accommodate new processes (e.g., friction stir welding, laser-arc hybrid welding) while preserving backward-compatible letter designations.
- The taxonomy evolved alongside AWS D1.1 (Structural Welding Code—Steel) and welder qualification standards (AWS B2.1), which reference A3.0 designations directly, embedding the taxonomy into legal and contractual welding documentation.

[Inference] The persistence of the letter-designation system, rather than migration to ISO's numeric scheme, is largely attributable to entrenched use in U.S. codes, welding procedure specifications (WPS), and decades of welder certification records that would be costly to renumber.

### Structural Logic of the Master Chart

The AWS Master Chart organizes processes into a strict genus-species hierarchy:

1. **Top-level division** — Processes are first separated into major categories based on the joining mechanism:
   - Arc Welding (AW)
   - Resistance Welding (RW)
   - Oxyfuel Gas Welding (OFW)
   - Solid-State Welding (SSW)
   - Brazing (B)
   - Soldering (S)
   - Other Welding Processes (e.g., Electron Beam Welding – EBW, Laser Beam Welding – LBW)
   - Allied Processes (thermal cutting, thermal spraying)
2. **Second-level division** — Within each family, processes are distinguished by the specific energy source or shielding mechanism. For example, under Arc Welding: Shielded Metal Arc Welding (SMAW), Gas Metal Arc Welding (GMAW), Gas Tungsten Arc Welding (GTAW), Flux Cored Arc Welding (FCAW), Submerged Arc Welding (SAW), Plasma Arc Welding (PAW).
3. **Third-level qualifiers** — Variants are appended as suffixes or modifiers, such as GMAW-S (short-circuiting transfer), GMAW-P (pulsed), or FCAW-G/FCAW-S (gas-shielded vs. self-shielded).

This produces a taxonomy that is simultaneously a **classification system** (grouping by shared physical principle) and a **naming convention** (standardized abbreviations used in WPS, procedure qualification records, and drawings).

### Comparison with ISO 4063 Taxonomy

| Dimension | AWS A3.0 Tradition | ISO 4063 Tradition |
| --- | --- | --- |
| Designation format | Alphabetic mnemonic codes (e.g., SMAW) | Numeric codes (e.g., 111 for manual metal arc) |
| Primary hierarchy driver | Energy source / equipment mechanism | Numeric grouping by process family (1xx = arc, 2xx = resistance, 3xx = gas, etc.) |
| Regional dominance | United States, and countries following U.S. codes | Europe, and ISO-aligned national standards bodies |
| Human readability | Mnemonic (letters suggest process name) | Requires lookup table; not self-descriptive |
| Extensibility | New letter combinations coined as processes emerge | New numeric subdivisions inserted within existing blocks |

[Inference] The mnemonic letter system is generally considered more intuitive for practitioners memorizing process names, while the ISO numeric system scales more systematically for database and multilingual documentation purposes, since digits are language-independent whereas English-based acronyms are not.

### Diagram: Master Chart Hierarchy (Simplified)

```mermaid
flowchart TD
    A[Welding and Allied Processes (svg_diagram)] --> B[Arc Welding - AW]
    A --> C[Resistance Welding - RW]
    A --> D[Oxyfuel Gas Welding - OFW]
    A --> E[Solid-State Welding - SSW]
    A --> F[Brazing - B]
    A --> G[Soldering - S]
    A --> H[Allied Processes]

    B --> B1[SMAW]
    B --> B2[GMAW]
    B --> B3[GTAW]
    B --> B4[FCAW]
    B --> B5[SAW]
    B --> B6[PAW]

    B2 --> B2a[GMAW-S]
    B2 --> B2b[GMAW-P]
    B4 --> B4a[FCAW-G]
    B4 --> B4b[FCAW-S]

    C --> C1[RSW - Spot]
    C --> C2[RSEW - Seam]
    C --> C3[UW - Upset]

    E --> E1[FRW - Friction]
    E --> E2[FSW - Friction Stir]
    E --> E3[USW - Ultrasonic]

    H --> H1[Thermal Cutting]
    H --> H2[Thermal Spraying]
```

### Letter Designation Logic

**Example**

The designation **GTAW** decomposes as:

- **G**as **T**ungsten **A**rc **W**elding

This mnemonic pattern (descriptive-word initials + "Arc Welding" or "Welding" suffix) is applied consistently:

- **G**as **M**etal **A**rc **W**elding → GMAW
- **S**hielded **M**etal **A**rc **W**elding → SMAW
- **F**lux **C**ored **A**rc **W**elding → FCAW
- **S**ubmerged **A**rc **W**elding → SAW (drops the redundant "arc" placement for readability)

This internal consistency is a defining trait of the AWS tradition: once a practitioner learns the pattern, most process names become decodable without memorization, in contrast to the arbitrary sequential numbering of ISO 4063.

### Integration into Downstream Standards

**Key Points**

- **AWS D1.1/D1.1M (Structural Welding Code – Steel)** references A3.0 process designations directly within Welding Procedure Specification (WPS) requirements.
- **AWS B2.1 (Specification for Welding Procedure and Performance Qualification)** uses the same letter codes to define qualification limits (e.g., a welder qualified in SMAW is not automatically qualified in GMAW).
- **ASME Boiler and Pressure Vessel Code, Section IX** independently maintains process abbreviations that largely mirror the AWS taxonomy, reflecting cross-pollination between AWS and ASME committees, though ASME is not formally bound to AWS revisions.
- Welding symbols per **AWS A2.4** do not encode process letters directly on the symbol but rely on the WPS-referenced AWS designation for process specificity in tail notations.

[Unverified] The precise degree of committee overlap between AWS A3.0 and ASME Section IX process-list maintenance is not something publicly documented in granular detail; the alignment is observable in output but the administrative coordination mechanism is not fully transparent from public standard text alone.

### Taxonomic Tensions and Edge Cases

- **Hybrid processes**: Laser-arc hybrid welding does not fit cleanly into a single Master Chart branch, as it combines an "Other Welding Process" (Laser Beam Welding) with an Arc Welding process. AWS has addressed this through compound or supplementary designations rather than restructuring the chart itself.
- **Allied vs. welding processes**: Thermal spraying and thermal cutting are classified as "allied processes" rather than welding processes proper, since they do not join two base materials via coalescence in the AWS definitional sense — a distinction that is definitional/legal rather than physical, and can be a source of confusion in curricula that treat all thermal joining/separation operations as a single category.
- **Solid-state process growth**: Since the 1990s, the Solid-State Welding (SSW) branch has expanded substantially (friction stir welding, linear friction welding, magnetic pulse welding), reflecting an area of active industrial growth that stresses a taxonomy originally built around fusion-dominant 20th-century processes.

### Practical Application: Reading a WPS Against the Taxonomy

**Example**

A Welding Procedure Specification header stating:



```
Process: FCAW-G
Base Metal: A36
Filler Metal: E71T-1
```

is immediately traceable through the AWS taxonomy as:

- Family: Arc Welding (AW)
- Process: Flux Cored Arc Welding (FCAW)
- Variant: Gas-shielded (G), meaning external shielding gas supplements the flux-generated shield

This traceability — from a two-letter code on a shop-floor document back to a specific node in the Master Chart — is the practical payoff of the taxonomic tradition: it allows procedure qualification, welder certification scope, and code compliance to all reference a single, unambiguous classification node rather than free-text process descriptions.

### Related Topics

- ISO 4063 Numeric Process Classification System
- AWS D1.1 Structural Welding Code Process Requirements
- ASME Section IX Welding Procedure Qualification
- Solid-State Welding Process Family Taxonomy
- Welding Symbol Standards (AWS A2.4) and Process Notation
- Comparative Analysis: AWS vs. DIN/EN Welding Terminology
- Welder Performance Qualification Scope Rules by Process Designation