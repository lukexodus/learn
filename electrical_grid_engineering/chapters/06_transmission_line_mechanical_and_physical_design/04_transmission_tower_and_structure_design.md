## Transmission Tower and Structure Design


### Overview

Transmission tower and structure design encompasses the selection of structure type, material, and configuration needed to support conductors, insulators, and ground/shield wires at appropriate heights and spacings while withstanding all applicable mechanical loads. Structure design integrates directly with the conductor selection (Conductor Types and Selection Criteria), sag-tension behavior (Sag-Tension Calculations), and insulator selection (Insulator Types and Selection) already covered, since these upstream decisions determine the loads that structures must ultimately resist.

### Structure Types by Material

#### Lattice Steel Towers

**Key Points**

- Constructed from steel angle members (or, less commonly, tubular members) bolted or riveted together in a triangulated lattice framework, providing high strength-to-weight efficiency for a given structural height and loading
- The dominant structure type for higher-voltage transmission lines and longer spans historically, due to their proven strength, adaptability to a wide range of loading conditions, and manufacturability in standardized, modular components
- Galvanization (hot-dip zinc coating) is standard practice for corrosion protection of steel lattice tower members, given decades-long expected service life in outdoor environments

#### Steel Poles (Tubular)

**Key Points**

- Single tapered steel pole (or occasionally multiple pole configurations) providing a more compact visual footprint than lattice towers, often preferred in urban, environmentally sensitive, or aesthetically constrained corridors
- Generally requires a larger-diameter foundation and more substantial single-point foundation design compared to the multi-leg foundation arrangement of lattice towers, since all loading concentrates through the single pole shaft
- [Unverified] Cost comparison between steel pole and lattice tower designs depends heavily on specific voltage class, loading conditions, height requirements, and regional material/labor costs, making generalized cost statements imprecise without project-specific analysis

#### Wood Poles

**Key Points**

- Historically widely used for lower-voltage transmission and sub-transmission lines, and remains common for many distribution and lower-voltage transmission applications, offering low cost, ease of handling, and natural insulating properties
- Generally limited to lower height and loading capacity compared to steel structures, making wood pole construction less common for higher-voltage, longer-span transmission applications, though H-frame (two-pole) configurations extend wood's practical application range for higher voltage classes
- Requires periodic inspection and treatment (preservative treatment against decay and insect damage) as part of ongoing structure maintenance programs

#### Concrete Poles

**Key Points**

- Prestressed or reinforced concrete poles offer an alternative to steel and wood, providing good corrosion resistance and structural durability, particularly favored in certain environments (coastal, high-humidity) where steel corrosion or wood decay present greater long-term maintenance concerns
- [Unverified] Regional adoption of concrete pole structures varies considerably; usage is more prevalent in some countries/utilities than others based on historical practice, material availability, and cost factors

### Structure Configurations by Function

#### Tangent (Suspension) Structures

**Key Points**

- Used at points where the line runs in a straight line (or with only minor angle deviation), supporting conductors via suspension insulator strings (as discussed in Insulator Types and Selection) that hang essentially vertically under the conductor's transverse weight
- Represent the majority of structures along a typical transmission line route, since most of a line's length typically consists of straight or gently curved sections rather than sharp angle points
- Generally subject to lower longitudinal loading than angle or dead-end structures, since suspension insulators allow the conductor to swing somewhat freely to accommodate minor imbalances, reducing (though not eliminating) direct transfer of longitudinal tension differences to the structure

#### Angle Structures

**Key Points**

- Used where the transmission line changes direction, requiring the structure to resist the resultant net horizontal force from the two adjacent conductor spans meeting at an angle
- The severity of angle loading increases with the sharpness of the line angle; structures are generally categorized by angle range (e.g., light angle, medium angle, heavy angle) with correspondingly increased structural strength requirements
- May use either suspension or strain (dead-end type) insulator configurations depending on the specific angle magnitude, with larger angles typically requiring strain insulator configurations given the substantial net tension component involved

#### Dead-End (Termination) Structures

**Key Points**

- Used at line termination points (substations, or specific points requiring a full mechanical break in the line, such as very large angle changes or sectionalizing points) and must withstand the full, unbalanced tension of the conductor on one side with no counterbalancing tension from the opposite side
- Represent the most heavily loaded structure type from a longitudinal loading perspective, given the complete absence of tension balance from an adjacent span
- Always employ strain (dead-end) insulator configurations rather than suspension configurations, consistent with the discussion in Insulator Types and Selection

```mermaid
flowchart LR
    A[Tangent Structure: minor/no angle] -->|Line continues straight| B[Tangent Structure]
    B -->|Line changes direction| C[Angle Structure: light/medium/heavy]
    C -->|Line continues| D[Tangent Structure]
    D -->|Line terminates at substation or sectionalizing point| E[Dead-End Structure: full unbalanced tension]
```

### Loading Categories in Structure Design

#### Vertical Loads

**Key Points**

- Include conductor weight (plus ice loading where applicable), insulator string weight, structure self-weight, and any additional attached equipment (e.g., OPGW splice enclosures, communication equipment)
- Vertical load calculations draw directly on the sag-tension analysis discussed in Sag-Tension Calculations, since conductor weight per unit length (including ice) and span length determine the vertical load transferred to each supporting structure

#### Transverse Loads

**Key Points**

- Include wind loading on conductors, structure members, and insulators, along with the transverse component of conductor tension at angle structures
- Wind loading calculations follow applicable design standards (varying by region, e.g., ASCE Manual of Practice documents in the United States, or equivalent regional/national standards elsewhere), which specify design wind speeds, gust factors, and drag coefficients appropriate to conductor and structure geometry

#### Longitudinal Loads

**Key Points**

- Include the unbalanced tension effects at angle and dead-end structures already discussed, as well as broken-conductor (differential tension) loading scenarios used as a design contingency case in many structural design standards
- Broken-wire loading criteria typically specify a scenario where one (or a specified subset of) conductors is assumed broken, requiring the structure to withstand the resulting unbalanced longitudinal load without progressive/cascading failure — an important consideration for overall line reliability and cascade failure prevention

#### Combined Load Cases

**Key Points**

- Structural design standards specify combinations of vertical, transverse, and longitudinal loads (e.g., simultaneous wind and ice loading, or broken-wire loading combined with reduced wind) representing realistic worst-case scenarios the structure must withstand without exceeding allowable stress or deflection limits
- [Unverified] Specific load combination factors and required design load cases vary by applicable national/regional structural standard and utility-specific design criteria

### Foundation Design

**Key Points**

- Foundation type and sizing depend on structure type (multi-leg lattice tower foundations distribute load across several separate footings, while single-shaft steel/concrete pole foundations concentrate all loading through one larger foundation), soil conditions, and applicable loading
- Common foundation types include spread footings, drilled pier (caisson) foundations, pile foundations (for poor soil conditions), and grillage foundations (steel grillage embedded in concrete, historically common for lattice tower legs)
- Geotechnical investigation (soil borings, bearing capacity assessment) is a standard prerequisite for foundation design, since soil properties directly govern foundation type selection and sizing for a given structural loading

### Tower Configuration and Circuit Arrangement

**Key Points**

- **Single-circuit towers**: support one three-phase circuit, with conductor arrangement (horizontal, vertical, or delta configuration on the crossarms) selected based on right-of-way width constraints, electrical clearance requirements, and aesthetic/environmental considerations
- **Double-circuit towers**: support two separate three-phase circuits on a single structure, offering right-of-way efficiency (two circuits in one corridor) at the cost of shared structural vulnerability — a single structure failure or common-mode event (e.g., a direct lightning strike causing simultaneous flashover) can potentially affect both circuits simultaneously, a consideration relevant to overall system reliability planning
- Phase conductor arrangement on double-circuit towers (e.g., using specific phase orderings across the two circuits) can be optimized to reduce mutual coupling effects and improve certain electrical performance characteristics, though this is a secondary design consideration relative to the primary mechanical/clearance requirements

### Structure Type Comparison Table

| Structure Type | Typical Material | Governing Load Type | Common Application |
| --- | --- | --- | --- |
| Tangent (Suspension) | Lattice steel, steel pole, wood | Vertical + moderate transverse | Straight-line sections, majority of route |
| Light/Medium Angle | Lattice steel, steel pole | Transverse + moderate longitudinal | Minor route direction changes |
| Heavy Angle / Dead-End | Lattice steel, steel pole, concrete | Full unbalanced longitudinal | Sharp turns, substations, sectionalizing points |

### Related Topics

- Sag-Tension Calculations
- Conductor Types and Selection Criteria
- Insulator Types and Selection
- Foundation design and geotechnical investigation methods
- Wind and ice loading standards (ASCE Manual of Practice, regional equivalents)
- Broken-wire and cascade failure prevention design criteria
- Overhead ground wires, shield wires, and OPGW structural attachment
- Right-of-way design and double-circuit versus single-circuit corridor planning