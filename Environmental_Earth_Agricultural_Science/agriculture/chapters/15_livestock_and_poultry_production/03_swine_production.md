## Swine Production


### Overview

Swine production is the systematic raising of pigs for meat, organized around a segmented production flow that mirrors the species' rapid reproductive cycle and growth rate. Modern commercial swine operations typically specialize into distinct phases — breeding/farrowing, nursery, and grow-finish — each requiring tailored facilities, nutrition, and health management, though smaller operations may integrate all phases on a single site (farrow-to-finish).

**Key Points**

- Swine are highly prolific and fast-growing relative to cattle, enabling intensive, multi-phase production systems with short generation intervals.
- Production is typically divided into farrow-to-wean, nursery (wean-to-feeder), and grow-finish phases, often across separate sites for disease control (multi-site production).
- Sow productivity (litters per year, pigs weaned per sow per year) is the central efficiency metric driving breeding herd management.
- Environmental control (temperature, ventilation, air quality) is critical at every phase due to swine's sensitivity to thermal stress and respiratory disease.

---

### Production System Structure

```mermaid
flowchart LR
    A[Breeding/Gestation] --> B[Farrowing]
    B --> C[Nursery: Wean to ~25kg]
    C --> D[Grow-Finish: to Market Weight]
    D --> E[Harvest/Processing]
    B -->|Gilts retained| A
```

#### Farrow-to-Wean (Breeding Herd)

Maintains the sow/gilt breeding herd through breeding, gestation, and farrowing (birthing) through to weaning, at which point piglets exit to nursery facilities.

#### Nursery (Wean-to-Feeder)

Houses weaned piglets (commonly weaned at 3–4 weeks of age, though this varies by system and regulatory context) through the vulnerable post-weaning transition period until they reach approximately 20–30 kg, at which point they move to grow-finish. This phase demands precise environmental and nutritional management due to the piglet's immature digestive and immune systems at weaning.

#### Grow-Finish

Final growth phase from nursery exit to market weight, focused on maximizing lean growth efficiency and controlling feed cost per unit of gain, the largest single input cost in swine production.

#### Multi-Site Production

Many commercial operations separate these phases across geographically distinct sites (e.g., "three-site production": breeding/farrowing, nursery, grow-finish as separate locations) specifically to break disease transmission cycles between age groups, since younger and older pigs have different pathogen exposure histories and immune status.

---

### Reproductive Management

#### Estrous Cycle and Breeding

Sows are polyestrous with a cycle of approximately 21 days; estrus itself lasts roughly 48–72 hours, with ovulation typically occurring in the middle-to-late portion of the estrus period. Breeding (natural service or AI) is generally timed to coincide with standing heat, often using a "boar exposure" stimulus (fenceline or direct contact) to aid heat detection given sows' sometimes subtle behavioral estrus signs.

#### Gestation and Farrowing

- **Gestation length** – approximately 114 days (colloquially remembered as "3 months, 3 weeks, 3 days")
- **Litter size** – highly prolific relative to most livestock, with modern genetics commonly producing litters in the low-to-mid teens of piglets born, though survival to weaning depends heavily on farrowing management and sow mothering ability
- **Farrowing crates/pens** – many commercial systems use farrowing crates that restrict sow movement to reduce piglet crushing risk, a practice that has become a significant animal welfare discussion point, with some jurisdictions and markets shifting toward group/loose farrowing housing systems [Inference — reflects an active area of ongoing regulatory and market evolution rather than a settled universal standard]

#### Weaning and Rebreeding Cycle

- **Lactation length** – commonly 3–4 weeks in commercial systems (longer in some systems for improved piglet/sow outcomes, shorter in others to maximize sow throughput)
- **Weaning-to-estrus interval (WEI)** – sows typically return to estrus within about a week after weaning, since lactation (via suckling-induced hormonal suppression) is the primary driver of the sow's postpartum anestrus period
- **Sow productivity metric** – Pigs Weaned per Sow per Year (PWSY) is a key benchmark integrating litter size, litters per year, and pre-weaning mortality

$$\text{PWSY} = \text{Litters per Sow per Year} \times \text{Pigs Weaned per Litter}$$



---

### Nutrition Across Production Phases

#### Phase Feeding Principle

Swine diets are formulated in successive "phases" that track the animal's rapidly changing nutrient requirements relative to body weight, since a diet appropriate for a 10 kg pig would be nutritionally inadequate (or wastefully over-formulated) for a 100 kg pig.

| Phase | Approx. Weight Range | Key Nutritional Focus |
| --- | --- | --- |
| Pre-starter/Starter | Weaning to ~25 kg | Highly digestible ingredients, often specialty proteins, to bridge the transition from sow's milk to solid feed |
| Grower | ~25–60 kg | Balanced protein/amino acid diet for lean tissue accretion |
| Finisher | ~60 kg to market weight | Adjusted energy/protein ratio as growth rate shifts toward more fat deposition relative to lean |
| Gestation | Breeding to pre-farrowing | Moderate energy to maintain body condition without excessive fetal overgrowth |
| Lactation | Farrowing to weaning | Very high energy/protein demand to support milk production, often the highest-density diet in the system |

#### Amino Acid Balancing

Swine diets are commonly formulated using the **ideal protein concept**, balancing amino acids (particularly lysine as the primary limiting amino acid, alongside methionine, threonine, and tryptophan) relative to energy content, rather than relying on crude protein percentage alone, to improve nitrogen utilization efficiency and reduce nitrogen excretion.

#### Feed Efficiency Metrics

$$\text{Feed Conversion Ratio (FCR)} = \frac{\text{Feed Intake}}{\text{Weight Gain}}$$

Swine generally exhibit more favorable feed conversion than ruminants for lean tissue growth due to differences in digestive physiology, though exact FCR benchmarks vary substantially by genetics, health status, and production phase. [Inference — general comparative physiological point; specific FCR figures are system- and genetics-dependent]

---

### Housing and Environmental Management

#### Facility Types by Phase

- **Farrowing rooms** – individual crates/pens with supplemental heat sources (heat lamps/mats) for piglets, since neonatal piglets have limited thermoregulatory capacity and require a warmer microclimate than the sow
- **Nursery rooms** – small-group pens with elevated ambient temperature (progressively reduced as pigs age) and often specialized flooring (e.g., plastic slatted) suited to small body size
- **Grow-finish barns** – larger group pens, typically with slatted or partially slatted flooring over manure pits, and mechanical ventilation systems

#### Environmental Control Priorities

- **Temperature** – swine lack functional sweat glands and are highly sensitive to heat stress; ventilation and cooling (fans, sprinklers/drip cooling) are critical in grow-finish and breeding herd facilities, while young piglets require supplemental warmth
- **Air quality** – ventilation systems manage ammonia, humidity, and dust levels, all linked to respiratory disease risk
- **All-in/all-out flow** – widely used at the room or barn level to allow complete cleaning/disinfection between groups, a cornerstone of swine disease control given the species' susceptibility to numerous production-limiting respiratory and enteric pathogens

---

### Health Management

#### Key Production-Limiting Disease Complexes

- **Porcine Reproductive and Respiratory Syndrome (PRRS)** – viral disease causing reproductive failure in sows and respiratory disease in growing pigs; a major economic concern in many swine-producing regions, controlled through biosecurity, vaccination, and herd health protocols
- **Porcine Epidemic Diarrhea (PED)** – highly contagious viral enteric disease, particularly devastating in neonatal piglets, controlled via strict biosecurity given the virus's high environmental persistence and transmissibility
- **Swine respiratory disease complex** – multifactorial, involving pathogens such as *Mycoplasma hyopneumoniae*, PRRS virus, and secondary bacterial agents, often exacerbated by poor ventilation/air quality
- **Enteric disease in nursery pigs** – post-weaning diarrhea linked to the abrupt dietary and immunological transition at weaning

#### Biosecurity Emphasis

Given the intensity and scale of modern swine production and the severe economic impact of diseases like PRRS and PED, swine operations typically implement rigorous biosecurity protocols including controlled site access, vehicle/equipment sanitation, downtime requirements between farm visits for personnel, and strict incoming animal health testing.

---

### Growth Performance and Carcass Characteristics

#### Key Growth Metrics

- **Average Daily Gain (ADG)** – growth rate benchmark tracked across grow-finish
- **Days to market** – total time from birth to slaughter weight, a key throughput metric for facility utilization
- **Backfat thickness and loin depth** – ultrasound or grading-line measurements used to estimate carcass lean percentage

#### Carcass Value Determinants

Carcass value in most modern grading/marketing systems is driven primarily by **lean meat percentage** (favoring leaner, more muscled carcasses) alongside overall carcass weight, with grid-based pricing systems in many markets rewarding producers for hitting target weight and leanness specifications. Exact grading criteria and pricing grid structures vary by country/processor. [Unverified — confirm specific grading criteria against the relevant regional/processor grid]

---

### Practical Example: Structuring an All-In/All-Out Nursery Flow

**Scenario:** A wean-to-feeder nursery operation wants to reduce post-weaning disease incidence through improved flow management.

**Steps:**

1. **Room-level cohorting** – group piglets from a defined weaning event (similar age/source) into a single room, avoiding continuous trickle-fill of pigs from multiple weaning dates into the same airspace.
2. **Environmental step-down** – set initial room temperature high (appropriate for newly weaned pig thermal needs) and progressively reduce it on a schedule as pigs mature and generate more of their own body heat.
3. **Diet transition** – provide a highly digestible pre-starter diet immediately post-weaning, stepping down through subsequent phase diets as intake and digestive capacity increase.
4. **Health monitoring** – daily observation for scours (diarrhea), lethargy, or reduced feed intake, which are early indicators of enteric or respiratory issues in this vulnerable phase.
5. **Full room turnout** – move the entire cohort to grow-finish together once target nursery exit weight is reached.
6. **Cleaning and disinfection** – empty, wash, disinfect, and allow the room to dry completely before the next weaning group enters, breaking the disease transmission cycle between successive groups.
7. **Downtime enforcement** – maintain a minimum vacancy period between groups sufficient for effective pathogen die-off, calibrated to the specific disease risks relevant to the operation.

This all-in/all-out flow, combined with phase-appropriate nutrition and environmental step-down, directly addresses the two dominant risk factors in nursery pig health: immune/digestive immaturity and cross-group pathogen transmission.

---

### Swine Production Flow Diagram

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 300" font-family="sans-serif">
<text x="320" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#333">Swine Multi-Site Production Flow (svg_diagram)</text>
<rect x="20" y="80" width="150" height="70" rx="8" fill="#d9a3c2" stroke="#7a3e5c" stroke-width="2" />
<text x="95" y="108" text-anchor="middle" font-size="11" fill="#3d1e2e">Breeding/</text>
<text x="95" y="122" text-anchor="middle" font-size="11" fill="#3d1e2e">Farrowing</text>
<text x="95" y="138" text-anchor="middle" font-size="9" fill="#333">Site 1</text>
<line x1="170" y1="115" x2="210" y2="115" stroke="#555" stroke-width="2" marker-end="url(#arrow4)" />
<rect x="210" y="80" width="150" height="70" rx="8" fill="#a3c2d9" stroke="#3e5c7a" stroke-width="2" />
<text x="285" y="115" text-anchor="middle" font-size="11" fill="#1e2e3d">Nursery</text>
<text x="285" y="130" text-anchor="middle" font-size="9" fill="#333">Site 2</text>
<line x1="360" y1="115" x2="400" y2="115" stroke="#555" stroke-width="2" marker-end="url(#arrow4)" />
<rect x="400" y="80" width="150" height="70" rx="8" fill="#c2d9a3" stroke="#5c7a3e" stroke-width="2" />
<text x="475" y="115" text-anchor="middle" font-size="11" fill="#2e3d1e">Grow-Finish</text>
<text x="475" y="130" text-anchor="middle" font-size="9" fill="#333">Site 3</text>
<line x1="550" y1="115" x2="580" y2="115" stroke="#555" stroke-width="2" marker-end="url(#arrow4)" />
<text x="605" y="120" text-anchor="middle" font-size="9" fill="#333">Market</text>

<text x="320" y="200" text-anchor="middle" font-size="10" fill="#555">Site separation limits disease transmission between age groups</text>

</svg>

---

**Related Topics**

- Sow productivity metrics and breeding herd benchmarking (PWSY analysis)
- Phase feeding and ideal protein ration formulation for swine
- PRRS and PED biosecurity and control programs
- Farrowing housing systems and sow welfare considerations
- Ventilation system design for confinement swine facilities
- All-in/all-out flow management and multi-site production planning
- Weaning age effects on piglet health and post-weaning performance
- Carcass grading and grid-based marketing systems
- Manure management and nutrient handling in confinement swine operations
- Antibiotic stewardship and alternatives in swine nursery diets