## Equipment Covered Under Mechanical Integrity Programs


### Overview

Mechanical Integrity (MI) is the PSM element (OSHA 29 CFR 1910.119(j)) requiring that equipment used to process, contain, or control highly hazardous chemicals (HHCs) is designed, fabricated, installed, and maintained to operate safely throughout its service life. The regulation enumerates specific equipment categories subject to MI, and correctly scoping "what is covered" is foundational — equipment incorrectly excluded from the MI program creates a gap in inspection, testing, and preventive maintenance (ITPM) coverage that can directly enable loss of containment.

### Regulatory Text — Covered Equipment List

**Key Points**

OSHA 1910.119(j)(1) explicitly lists the following equipment as covered by mechanical integrity provisions:

1. Pressure vessels and storage tanks
2. Piping systems (including piping components such as valves)
3. Relief and vent systems and devices
4. Emergency shutdown systems
5. Controls (including monitoring devices and sensors, alarms, and interlocks)
6. Pumps

This list is not exhaustive of all plant equipment — it is exhaustive of the *categories* OSHA requires at minimum. Any equipment whose failure could result in the release of a highly hazardous chemical is properly considered part of the MI universe, even if it does not fall cleanly into one of the six enumerated categories (e.g., compressors, agitators/mixers, and rotating equipment in HHC service are broadly treated as covered by consensus industry practice even though "compressors" is not separately named).

### Scoping Methodology: Determining Coverage

**Key Points**

- MI coverage is triggered by the equipment's role relative to a covered process (a process involving a threshold quantity of an OSHA-listed HHC, or a process with flammable liquids/gases above threshold quantities per Appendix A, unless an exemption applies).
- The determining question is not the equipment's category but whether its failure could result in a release of, or loss of control over, an HHC.
- Scoping is typically performed via a **Process Safety Information (PSI)**-driven boundary review: P&IDs are walked down to identify every component within the covered process boundary, from the point HHC enters the unit to the point it exits (or is neutralized/converted below threshold).

**Typical MI Boundary Definition Process**

1. Identify the covered process(es) and their PSI-defined boundaries (battery limits).
2. Walk down current P&IDs to enumerate all equipment, piping, and instrumentation within the boundary.
3. Classify each item into an MI equipment category (vessel, piping, relief device, ESD, control/instrument/alarm/interlock, pump, or "other covered equipment").
4. Assign each item to an applicable inspection/test code, standard, or internal ITPM program.
5. Document inclusion/exclusion decisions with rationale (critical for OSHA audit defensibility — undocumented exclusions are a common citation basis).
6. Feed the resulting equipment list into the CMMS/EAM asset hierarchy for scheduling.

### Detailed Equipment Category Breakdown

#### 1. Pressure Vessels and Storage Tanks

- **Scope:** Reactors, columns/towers, drums, separators, heat exchangers (shell-side and tube-side pressure boundary), atmospheric and pressurized storage tanks, spheres, bullets.
- **Governing codes/standards:** ASME Boiler and Pressure Vessel Code (BPVC) Section VIII (Divisions 1, 2, 3) for design; **API 510** (Pressure Vessel Inspection Code) for in-service inspection; **API 653** for atmospheric storage tanks; **API 620/650** for tank design.
- **Key integrity concerns:** Corrosion (general, localized, under-insulation), erosion, fatigue, creep (high-temperature service), brittle fracture risk, cladding/lining integrity.
- **Typical ITPM activities:** External visual inspection, internal inspection (opened for entry), thickness (UT) surveys at Condition Monitoring Locations (CMLs), remaining-life calculations, Risk-Based Inspection (RBI) interval determination.

#### 2. Piping Systems (Including Components Such as Valves)

- **Scope:** Process piping, piping specialty items, block valves, control valves (mechanical/pressure-boundary aspects), check valves, strainers, flanges, gaskets, expansion joints.
- **Governing codes/standards:** ASME B31.3 (Process Piping) for design; **API 570** (Piping Inspection Code) for in-service inspection; ASME B16.5/B16.34 for flanges and valves.
- **Key integrity concerns:** Wall thinning from corrosion/erosion, flow-accelerated corrosion at elbows/tees, external corrosion under insulation (CUI), fatigue at vibration-prone small-bore connections, dead-leg corrosion.
- **Typical ITPM activities:** Circuit-based UT thickness monitoring, visual inspection, CUI inspection programs, small-bore piping vibration assessment.

#### 3. Relief and Vent Systems and Devices

- **Scope:** Pressure relief valves (PRVs), rupture disks, relief headers/flare systems, vent stacks, vacuum breakers, conservation vents on storage tanks.
- **Governing codes/standards:** API 520 (Sizing, Selection, and Installation of Pressure-Relieving Devices), **API 576** (Inspection of Pressure-Relieving Devices), API 521 (Pressure-Relieving and Depressuring Systems), ASME BPVC Section VIII (relief device certification).
- **Key integrity concerns:** Set-pressure drift, seat leakage, fouling/plugging (especially in polymerizing or fouling services), chatter, inlet/outlet piping pressure-drop compliance.
- **Typical ITPM activities:** Bench testing (pop testing) on a defined frequency, as-found/as-left documentation, inspection for corrosion/fouling on removal, backup device or run-time strategy for units that cannot be taken offline.

#### 4. Emergency Shutdown Systems

- **Scope:** Emergency shutdown (ESD) valves, blowdown valves, fire and gas detection systems tied to automatic shutdown actions, manual ESD pushbuttons/stations, ESD logic solvers.
- **Overlap note:** ESD systems that meet the definition of a Safety Instrumented System (SIS) are also governed by IEC 61511/ISA 84 functional safety lifecycle requirements in addition to MI ITPM.
- **Key integrity concerns:** Fail-safe action verification (fail-closed/fail-open per design intent), stroke time, actuator function, partial stroke test (PST) coverage for valves that cannot be fully cycled online.
- **Typical ITPM activities:** Functional testing at a frequency justified by SIL/LOPA credit taken, partial stroke testing, full-stroke testing during turnarounds.

#### 5. Controls (Monitoring Devices, Sensors, Alarms, Interlocks)

- **Scope:** Process transmitters (pressure, temperature, level, flow), analyzers, safety-critical alarms (per alarm rationalization), interlock logic (whether hardwired or in a Basic Process Control System/BPCS or SIS), critical control loops whose failure could cause a hazardous deviation.
- **Distinction:** BPCS controls are covered under MI for the instrumentation/monitoring aspect, while safety-instrumented functions carry the additional SIL-based proof-test regime.
- **Key integrity concerns:** Calibration drift, sensor fouling, common-cause failure exposure (e.g., shared impulse lines), alarm/interlock bypass management.
- **Typical ITPM activities:** Calibration verification on a defined frequency, functional testing of interlocks, SIF proof testing, bypass/override tracking and time-limited authorization.

#### 6. Pumps

- **Scope:** Centrifugal and positive-displacement pumps in HHC service, including seals, bearings, couplings, and the immediate pressure-boundary casing.
- **Governing codes/standards:** API 610 (Centrifugal Pumps for Petroleum, Petrochemical, and Natural Gas Industries) for design; site-specific vibration and condition-monitoring programs for in-service assessment.
- **Key integrity concerns:** Mechanical seal failure (a leading cause of fugitive HHC releases), bearing degradation, cavitation, casing corrosion/erosion.
- **Typical ITPM activities:** Vibration analysis, seal-pot/flush-plan monitoring, thermography, oil analysis, seal replacement history tracking.

### Equipment Commonly Added Beyond the Literal List (Industry Practice)

While not separately enumerated in 1910.119(j)(1), the following are broadly treated as covered "other process equipment" by consensus industry practice and CCPS/API guidance whenever their failure could release an HHC:

- Compressors (reciprocating, centrifugal, screw) — API 618/API 617 design; site-specific vibration and integrity programs.
- Agitators and mixers with pressure-boundary or seal penetrations into HHC service.
- Heat exchangers as rotating/static equipment beyond the pressure-boundary aspect already under API 510 (e.g., tube bundle integrity, fouling management).
- Fired equipment (furnaces, heaters, boilers) where tube failure could release process fluid — governed by API 573 (Fired Heaters).
- Rotating equipment couplings, gearboxes, and drivers where failure could propagate to a pressure-containing failure.
- Fireproofing, structural supports, and foundations for equipment in HHC service, to the extent their failure could cause equipment collapse and loss of containment (a frequent RAGAGEP interpretation point).

**Example**

A hydroprocessing unit reactor feed/effluent heat exchanger train would be scoped into MI as: (1) a pressure vessel under API 510 for the shell/head/nozzles, (2) piping under API 570 for the inlet/outlet spool pieces, (3) relief devices under API 576 for the associated PRVs, and (4) instrumentation under the controls category for the differential-pressure and temperature transmitters used for fouling monitoring — four separate MI sub-programs converging on a single physical asset.

### Excluded / Boundary Cases

- Equipment in utility or non-HHC service that does not connect to, or could not credibly release into, the covered process boundary is generally outside MI scope, though it may still be subject to routine (non-PSM) preventive maintenance.
- Equipment downstream of a point where the HHC has been definitively removed, diluted below threshold, or the process stream no longer meets the covered-process definition, is typically outside the MI boundary — the specific boundary point should be documented and defensible.
- [Inference] Ambiguous cases (e.g., a utility steam system that also serves as a quench medium injected directly into an HHC-containing vessel) are common sources of scoping disagreement and should be resolved via a documented boundary determination reviewed by process safety and inspection SMEs, since the correct answer depends on site-specific configuration rather than a universal rule.

### Equipment-to-Program Mapping (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 920 340" font-family="sans-serif" font-size="12">
<text x="460" y="22" font-size="15" font-weight="bold" text-anchor="middle">MI Equipment Categories → Governing Programs (svg_diagram)</text>
<g>
<rect x="20" y="50" width="180" height="40" rx="5" fill="#e8f0fe" stroke="#4472c4" />
<text x="110" y="74" text-anchor="middle">Pressure Vessels / Tanks</text>
<line x1="200" y1="70" x2="330" y2="70" stroke="#333" stroke-width="1.3" />
<rect x="330" y="50" width="200" height="40" rx="5" fill="#fce4d6" stroke="#c55a11" />
<text x="430" y="74" text-anchor="middle">API 510 / 653 / 620 / 650</text>



```
<rect x="20" y="105" width="180" height="40" rx="5" fill="#e8f0fe" stroke="#4472c4" />
<text x="110" y="129" text-anchor="middle">Piping Systems</text>
<line x1="200" y1="125" x2="330" y2="125" stroke="#333" stroke-width="1.3" />
<rect x="330" y="105" width="200" height="40" rx="5" fill="#fce4d6" stroke="#c55a11" />
<text x="430" y="129" text-anchor="middle">API 570 / B31.3</text>

<rect x="20" y="160" width="180" height="40" rx="5" fill="#e8f0fe" stroke="#4472c4" />
<text x="110" y="184" text-anchor="middle">Relief &amp; Vent Systems</text>
<line x1="200" y1="180" x2="330" y2="180" stroke="#333" stroke-width="1.3" />
<rect x="330" y="160" width="200" height="40" rx="5" fill="#fce4d6" stroke="#c55a11" />
<text x="430" y="184" text-anchor="middle">API 520 / 521 / 576</text>

<rect x="20" y="215" width="180" height="40" rx="5" fill="#e8f0fe" stroke="#4472c4" />
<text x="110" y="239" text-anchor="middle">Emergency Shutdown</text>
<line x1="200" y1="235" x2="330" y2="235" stroke="#333" stroke-width="1.3" />
<rect x="330" y="215" width="200" height="40" rx="5" fill="#fce4d6" stroke="#c55a11" />
<text x="430" y="239" text-anchor="middle">IEC 61511 / ISA 84</text>

<rect x="20" y="270" width="180" height="40" rx="5" fill="#e8f0fe" stroke="#4472c4" />
<text x="110" y="294" text-anchor="middle">Controls / Alarms / Interlocks</text>
<line x1="200" y1="290" x2="330" y2="290" stroke="#333" stroke-width="1.3" />
<rect x="330" y="270" width="200" height="40" rx="5" fill="#fce4d6" stroke="#c55a11" />
<text x="430" y="294" text-anchor="middle">ISA 18.2 / SIF Proof Test</text>

<rect x="620" y="160" width="180" height="40" rx="5" fill="#e8f0fe" stroke="#4472c4" />
<text x="710" y="184" text-anchor="middle">Pumps</text>
<line x1="560" y1="180" x2="618" y2="180" stroke="#333" stroke-width="1.3" />
<rect x="330" y="160" width="0" height="0" />
<rect x="620" y="160" width="0" height="0" />
<text x="710" y="220" text-anchor="middle" fill="#333">API 610 / Vibration Program</text>
```

</g>
</svg>

### Documentation and Traceability Requirements

- Each covered equipment item must have a unique asset identifier linking PSI (design basis), P&ID location, applicable inspection code, ITPM schedule/frequency, and inspection/test history.
- OSHA and API 510/570/653 auditors expect a defensible **equipment inclusion list** with documented rationale, not just an implicit CMMS asset list — gaps between the "as-documented" MI universe and the "as-built" plant are a recurring citation finding.
- Changes to equipment scope (new equipment, decommissioned equipment, process boundary changes) must flow through **Management of Change (MOC)** to keep the MI equipment list current.

### Related Topics

- API 510/570/653/576 Inspection Code Requirements
- Risk-Based Inspection (RBI) Methodology
- Safety Instrumented System (SIS) Proof Testing and SIL Verification
- Quality Assurance for New/Replacement Equipment (1910.119(j)(3))
- Deficiency Correction and MI Deficiency Management (1910.119(j)(5))
- RAGAGEP (Recognized and Generally Accepted Good Engineering Practice) Application
- Management of Change (MOC) Interfaces with Mechanical Integrity
- CMMS/EAM Asset Hierarchy Design for PSM Compliance
- Corrosion Under Insulation (CUI) Inspection Programs
- Fugitive Emissions and Mechanical Seal Reliability Programs