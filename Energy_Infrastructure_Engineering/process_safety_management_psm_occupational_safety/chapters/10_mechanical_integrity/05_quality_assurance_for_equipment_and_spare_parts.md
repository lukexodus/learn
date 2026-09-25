## Quality Assurance for Equipment and Spare Parts

### Overview

Quality Assurance (QA) for equipment and spare parts is the Mechanical Integrity program element ensuring that new equipment, fabricated components, and replacement spare parts are suitable for their intended service before being installed into a covered process. This element addresses a distinct failure pathway from inspection/testing (which detects in-service degradation of existing equipment): QA prevents the introduction of a latent defect at the point of fabrication, procurement, or installation — a defect that in-service inspection programs are not designed to catch until much later, if at all.

### Regulatory Basis

**Key Points**

- OSHA PSM 1910.119(j)(6) requires that in the construction of new plants and equipment, the employer ensure that equipment as fabricated is suitable for the process application for which it will be used.
- 1910.119(j)(6)(ii) requires appropriate checks and inspections to ensure that equipment is installed properly and consistent with design specifications and the manufacturer's instructions.
- 1910.119(j)(6)(iii) requires that maintenance materials, spare parts, and equipment be suitable for the process application for which they will be used.
- Unlike the inspection-frequency requirements of (j)(4), the QA requirement of (j)(6) is a point-in-time verification obligation tied to procurement, fabrication, and installation events rather than a recurring schedule — but it is equally auditable and is a common source of PSM citations when spare parts are found to be substituted with non-equivalent materials or specifications.

### Scope: What Requires QA Verification

- **New equipment for new construction** — vessels, piping, pumps, valves, instrumentation being installed as part of a new unit or expansion.
- **Replacement equipment** — like-for-like or upgraded equipment installed to replace failed or degraded in-service equipment.
- **Fabricated components** — shop- or field-fabricated piping spools, vessel internals, structural supports built to project specifications rather than purchased as a complete unit.
- **Spare parts and maintenance materials** — gaskets, bolting, valve trim, seal components, instrumentation replacement parts, relief valve internals — anything installed during routine maintenance that could affect the pressure boundary or safety function if non-conforming.
- **Field-fabricated and repaired items** — weld repairs, in-place modifications, and field-fitted piping that do not pass through a standard receiving-inspection process the way purchased items do.

### QA Program Elements

#### 1. Design and Specification Verification

**Key Points**

- Purchase specifications must correctly translate Process Safety Information (PSI) — design pressure/temperature, material of construction, corrosion allowance, code of construction — into procurement documents.
- Material specifications must account for the specific damage mechanisms expected in service (e.g., specifying appropriate alloy for a known corrosive/erosive/high-temperature environment, consistent with API 571 damage mechanism understanding), not merely nominal pressure/temperature ratings.

#### 2. Vendor/Supplier Qualification

- Verification that fabricators and material suppliers hold applicable certifications (e.g., ASME "U" stamp for pressure vessel fabrication, National Board registration, applicable ISO 9001 quality system certification).
- Documented supplier qualification/approval process, with periodic reassessment or audit of critical suppliers for safety-critical components (e.g., relief valves, SIS final elements).

#### 3. Material Traceability and Certification

**Key Points**

- **Material Test Reports (MTRs)** / Certified Material Test Reports (CMTRs) provide documented chemical composition and mechanical property verification traceable to the actual heat/lot of material used in fabrication — the foundational document linking a specific physical component to its certified properties.
- **Positive Material Identification (PMI)** — field or shop verification (typically via X-ray fluorescence, XRF) that installed alloy components match the specified material grade, guarding against inadvertent substitution (e.g., carbon steel bolting installed where alloy steel was specified — a documented root cause in multiple industry incidents involving high-temperature/high-pressure service).
- Traceability documentation should link the component through fabrication, receipt, storage, and installation, so that if a material issue is later discovered (e.g., a supplier recall or a discovered certification fraud), affected installed components can be identified and located.

#### 4. Receiving Inspection

- Verification upon delivery that received equipment/parts match purchase order specifications (dimensional check, material marking verification, documentation completeness) before the item is released to stores or installation.
- Damage inspection to identify shipping/handling damage before installation.
- For critical spare parts (e.g., relief valve trim, SIS final elements), receiving inspection may include functional or dimensional verification beyond documentation review alone.

#### 5. Fabrication Inspection and Nondestructive Examination (NDE)

- Weld inspection per the applicable code (radiographic testing, ultrasonic testing, magnetic particle testing, liquid penetrant testing) at the frequency/coverage required by the code of construction (e.g., ASME B31.3 weld examination requirements, which vary by piping class/service severity).
- Welder/welding-procedure qualification records (WPQ/WPS) verified current and applicable to the specific joint configuration and material being welded.
- Hydrostatic or pneumatic pressure testing of fabricated pressure equipment prior to service, per the governing code.

#### 6. Installation Verification

**Key Points**

- Field verification that installation matches approved design (correct orientation, support, alignment, bolt torque per specification, gasket selection appropriate for service).
- Pre-startup checks confirming instrumentation calibration, interlock function, and correct valve positioning consistent with the design intent — often formally captured through a **Pre-Startup Safety Review (PSSR)** for new or modified equipment (1910.119(i)).
- Verification that field welds, bolted connections, and any field modifications made during installation (not originally part of the fabricated package) receive the same NDE/inspection rigor as shop fabrication.

### QA Verification Workflow (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 920 340" font-family="sans-serif" font-size="12">
<text x="460" y="20" font-size="15" font-weight="bold" text-anchor="middle">Equipment/Spare Part QA Verification Chain (svg_diagram)</text>
<rect x="20" y="50" width="150" height="50" rx="6" fill="#e8f0fe" stroke="#4472c4" />
<text x="95" y="72" text-anchor="middle">PSI-Based</text>
<text x="95" y="88" text-anchor="middle">Specification</text>
<rect x="200" y="50" width="150" height="50" rx="6" fill="#e8f0fe" stroke="#4472c4" />
<text x="275" y="72" text-anchor="middle">Vendor</text>
<text x="275" y="88" text-anchor="middle">Qualification</text>
<rect x="380" y="50" width="150" height="50" rx="6" fill="#fff2cc" stroke="#bf8f00" />
<text x="455" y="72" text-anchor="middle">Fabrication +</text>
<text x="455" y="88" text-anchor="middle">NDE / Weld QA</text>
<rect x="560" y="50" width="150" height="50" rx="6" fill="#fff2cc" stroke="#bf8f00" />
<text x="635" y="72" text-anchor="middle">MTR / PMI</text>
<text x="635" y="88" text-anchor="middle">Verification</text>
<rect x="740" y="50" width="150" height="50" rx="6" fill="#e2efda" stroke="#548235" />
<text x="815" y="72" text-anchor="middle">Receiving</text>
<text x="815" y="88" text-anchor="middle">Inspection</text>
<line x1="170" y1="75" x2="198" y2="75" stroke="#333" stroke-width="1.3" marker-end="url(#arrQ)" />
<line x1="350" y1="75" x2="378" y2="75" stroke="#333" stroke-width="1.3" marker-end="url(#arrQ)" />
<line x1="530" y1="75" x2="558" y2="75" stroke="#333" stroke-width="1.3" marker-end="url(#arrQ)" />
<line x1="710" y1="75" x2="738" y2="75" stroke="#333" stroke-width="1.3" marker-end="url(#arrQ)" />
<line x1="815" y1="100" x2="815" y2="140" stroke="#333" stroke-width="1.3" marker-end="url(#arrQ)" />
<rect x="700" y="140" width="230" height="45" rx="6" fill="#deebf7" stroke="#2e74b5" />
<text x="815" y="167" text-anchor="middle">Stores / Traceable Storage</text>
<line x1="815" y1="185" x2="815" y2="220" stroke="#333" stroke-width="1.3" marker-end="url(#arrQ)" />
<rect x="650" y="220" width="280" height="45" rx="6" fill="#fce4d6" stroke="#c55a11" />
<text x="790" y="247" text-anchor="middle">Installation Verification</text>
<line x1="650" y1="242" x2="200" y2="270" stroke="#333" stroke-width="1.3" marker-end="url(#arrQ)" />
<rect x="60" y="270" width="280" height="45" rx="6" fill="#e2efda" stroke="#548235" />
<text x="200" y="297" text-anchor="middle">Pre-Startup Safety Review (PSSR)</text>
</svg>

### Spare Parts Program Specific Requirements

**Key Points**

- **Critical spares identification** — safety-critical spares (relief valve trim, SIS final elements, gaskets/bolting for high-consequence service) should be specifically identified and tracked, distinct from general stores inventory, to ensure correct specification is maintained through the procurement and storage lifecycle.
- **Storeroom bin/label integrity** — a common real-world failure mode is correct material being ordered but incorrectly binned, labeled, or substituted at the storeroom level; QA extends to storeroom controls (unique part numbers tied to specification, physical segregation of look-alike/non-interchangeable parts, e.g., different pressure-class flanges or gasket materials that appear visually similar).
- **"Will-fit" substitution control** — a documented engineering review and approval process must govern any proposed substitution of a spare part that is not an exact like-for-like match, ensuring the substitute meets the original design basis (this substitution decision is itself frequently a trigger for Management of Change).
- **Shelf-life and storage condition management** — elastomeric seals, gaskets, and certain instrumentation have finite shelf life or storage condition requirements (temperature, humidity); QA programs should track and enforce these limits to prevent installation of degraded stock.

### Interface with Management of Change (MOC)

- Any equipment or spare part that is not an exact replacement-in-kind (different material, different manufacturer, different design rating) must be evaluated through MOC before installation — QA verification and MOC are complementary controls: MOC evaluates whether a *different* item is acceptable from a process safety standpoint, while QA verifies that whatever item is installed (replacement-in-kind or MOC-approved alternative) actually conforms to its specification.
- Emergency/urgent replacement situations create particular risk: pressure to restore operation quickly can compress or bypass QA verification steps; a documented emergency-MOC and expedited-but-not-eliminated QA process should be defined in advance rather than improvised under time pressure.

### Documentation and Audit Trail

- QA records (MTRs, PMI results, NDE reports, receiving inspection records, installation verification/PSSR sign-off) should be retained and linked to the specific equipment's asset record, supporting both PSM audit defensibility and future root-cause investigation if the component later fails.
- Traceability should be sufficient to answer, for any installed safety-critical component: what specification was required, what was actually procured/received, who verified conformance, and when/how it was installed and verified — a chain that OSHA and API auditors commonly test by sampling specific components and tracing the documentation backward.

**Example**

A refinery replaces a pressure relief valve during a turnaround. The QA/spare-parts chain for this single component includes: the original design specification (set pressure, capacity, materials) traceable to the unit's PSI; a purchase order to a qualified relief-valve vendor referencing that specification; an MTR for the valve body and trim materials; receiving inspection confirming the tag number, set pressure stamping, and documentation match the PO; storage in a controlled area prior to installation; installation verification confirming correct orientation and torque on flanged connections; and a bench-test certificate confirming as-left set pressure before return to service — each link independently auditable and traceable to the original design basis.

### Common Implementation Pitfalls

- **Documentation gaps for field-fabricated items** — shop-fabricated packages often have strong QA documentation while field welds and on-site modifications receive less rigorous NDE/inspection tracking.
- **Storeroom substitution without MOC** — stores personnel substituting a "close enough" part (different gasket material, different bolting grade) without engineering review, often under production-pressure conditions.
- **PMI program gaps** — relying solely on paperwork/MTR review without physical verification (PMI) for alloy components in services where a material mix-up has historically caused high-consequence incidents (e.g., high-temperature hydrogen service, sour service requiring specific low-hardness steels).
- **Emergency procurement bypassing QA rigor** — expedited emergency spare-part sourcing from non-qualified suppliers without the standard vendor qualification and material certification steps, particularly under production-loss pressure.
- **Shelf-life expiration going undetected** — installing elastomeric or perishable components past their qualified storage life due to inadequate storeroom date-tracking.

### Related Topics

- Positive Material Identification (PMI) Program Design
- Pre-Startup Safety Review (PSSR) Requirements (1910.119(i))
- Management of Change (MOC) Interface with Equipment Substitution
- Material Test Reports and Traceability Documentation
- Welding Procedure and Welder Qualification (WPS/WPQ)
- Critical Spare Parts Identification and Inventory Control
- Vendor/Supplier Qualification Programs
- API 510/570 New Construction and Repair/Alteration Requirements
- Fitness-for-Service Assessment for Field-Discovered Defects
- Emergency Maintenance Procurement Controls