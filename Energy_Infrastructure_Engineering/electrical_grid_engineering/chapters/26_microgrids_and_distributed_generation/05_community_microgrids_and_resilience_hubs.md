## Community Microgrids and Resilience Hubs


### Definitions and Distinctions

**Key Points**

- A community microgrid is a microgrid serving multiple, often unaffiliated, customers or facilities across a defined geographic area (rather than a single owner's campus or building), typically requiring the microgrid to cross public rights-of-way and interact with the local distribution utility's infrastructure and regulatory framework.
- A resilience hub is a community-serving facility — often a single building such as a library, school, or community center — that is intentionally equipped (frequently via a smaller-scale microgrid or standalone DER/storage system) to provide continuous power and habitable conditions to the public during grid outages, extreme weather, or other emergencies.
- Community microgrids and resilience hubs frequently overlap in practice: a resilience hub is often the anchor critical facility within a broader community microgrid, but a resilience hub can also exist as a standalone facility without being part of a larger multi-customer microgrid.

### Key Distinguishing Characteristics from Single-Owner Microgrids

**Key Points**

- Community microgrids typically involve multiple parcels and multiple electricity customers, raising distribution-utility ownership, tariff, and regulatory questions that single-owner (campus, industrial) microgrids largely avoid.
- Governance and cost-allocation structures are substantially more complex, since benefits (resilience, potential bill savings) and costs (capital investment, ongoing O&M) must be distributed fairly across multiple stakeholders with different risk tolerances and financial capacities.
- Interconnection with existing utility distribution infrastructure often requires the community microgrid to either be developed in partnership with the incumbent distribution utility, or to navigate a more complex third-party ownership and easement/right-of-way framework where the utility is not the primary developer.

**Ownership and business models**

Community microgrids are typically structured under one of several models:

1. **Utility-owned and operated**: The incumbent distribution utility develops, owns, and operates the community microgrid as a rate-based asset, recovering costs through customer rates (subject to state public utility commission approval).
2. **Third-party developer/ESCO model**: A private developer or energy service company designs, finances, and often operates the microgrid, contracting with participating customers and/or the utility for services and energy delivery.
3. **Public-private partnership**: Local government (often a municipality, county, or special district) partners with a private developer and/or the utility, frequently layering in state or federal grant funding (e.g., FEMA hazard mitigation grants, DOE grid resilience funding) to offset capital costs.
4. **Cooperative/municipal utility model**: In areas served by a rural electric cooperative or municipal utility, the local utility itself may develop the community microgrid as a member/ratepayer-benefiting resilience investment.

### Resilience Hub Design Principles

**Key Points**

- A resilience hub's core design objective is providing continuous, reliable power to sustain habitable conditions (heating/cooling, lighting, refrigeration for medication, device charging, communications) for the public during an extended outage, not necessarily full building-load service.
- Load prioritization and shedding capability are essential design elements, since most resilience hubs are sized to serve a defined critical load subset rather than the facility's full normal-operation load.
- Beyond electrical resilience, well-designed resilience hubs often integrate complementary passive resilience measures (building envelope efficiency, natural ventilation, water storage) to extend habitability even beyond the electrical system's endurance.

**Typical resilience hub critical load categories**

- Lighting and basic HVAC for occupant safety and comfort (often a reduced setpoint/schedule rather than full normal-operation HVAC).
- Refrigeration (particularly important for medication storage and food safety during extended outages).
- Communications equipment (Wi-Fi, cellular signal boosters, radios) enabling the hub to serve as an information and coordination point during emergencies.
- Device charging stations for community members' phones and medical equipment.
- Water pumping/treatment equipment, where the facility serves a water-dependent community function.

### Community Microgrid and Resilience Hub Architecture (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 900 460" font-family="Arial, sans-serif">
<text x="450" y="26" font-size="17" font-weight="bold" text-anchor="middle">Community Microgrid with Resilience Hub Anchor (svg_diagram)</text>
<rect x="40" y="60" width="180" height="60" rx="8" fill="#dbeafe" stroke="#2563eb" stroke-width="2" />
<text x="130" y="85" font-size="12" font-weight="bold" text-anchor="middle">Utility Distribution Feeder</text>
<text x="130" y="103" font-size="10" text-anchor="middle" fill="#666">Upstream substation</text>
<line x1="130" y1="120" x2="130" y2="170" stroke="#333" stroke-width="2" marker-end="url(#c1)" />
<rect x="40" y="170" width="180" height="50" rx="8" fill="#fee2e2" stroke="#dc2626" stroke-width="2" />
<text x="130" y="200" font-size="12" font-weight="bold" text-anchor="middle">Community PCC / Switch</text>
<line x1="220" y1="195" x2="700" y2="195" stroke="#333" stroke-width="2" />
<line x1="260" y1="195" x2="260" y2="250" stroke="#333" stroke-width="1.5" marker-end="url(#c1)" />
<rect x="180" y="250" width="160" height="60" rx="8" fill="#fef3c7" stroke="#d97706" stroke-width="2" />
<text x="260" y="275" font-size="11" font-weight="bold" text-anchor="middle">Residential Feeder</text>
<text x="260" y="292" font-size="10" text-anchor="middle" fill="#666">Multiple households</text>
<line x1="440" y1="195" x2="440" y2="250" stroke="#333" stroke-width="1.5" marker-end="url(#c1)" />
<rect x="360" y="250" width="160" height="60" rx="8" fill="#dcfce7" stroke="#16a34a" stroke-width="2" />
<text x="440" y="270" font-size="11" font-weight="bold" text-anchor="middle">Resilience Hub</text>
<text x="440" y="287" font-size="10" text-anchor="middle" fill="#666">Library / community center</text>
<text x="440" y="302" font-size="9" text-anchor="middle" fill="#666">Solar + BESS + critical loads</text>
<line x1="620" y1="195" x2="620" y2="250" stroke="#333" stroke-width="1.5" marker-end="url(#c1)" />
<rect x="540" y="250" width="160" height="60" rx="8" fill="#fef3c7" stroke="#d97706" stroke-width="2" />
<text x="620" y="275" font-size="11" font-weight="bold" text-anchor="middle">Small Business Feeder</text>
<text x="620" y="292" font-size="10" text-anchor="middle" fill="#666">Commercial customers</text>
<line x1="440" y1="310" x2="440" y2="360" stroke="#16a34a" stroke-width="2" marker-end="url(#c2)" />
<rect x="330" y="360" width="220" height="70" rx="8" fill="#ede9fe" stroke="#7c3aed" stroke-width="2" />
<text x="440" y="385" font-size="12" font-weight="bold" text-anchor="middle">Microgrid Controller</text>
<text x="440" y="403" font-size="10" text-anchor="middle" fill="#666">Islanding, load prioritization,</text>
<text x="440" y="418" font-size="10" text-anchor="middle" fill="#666">DER dispatch coordination</text>
</svg>

### Governance and Regulatory Considerations

**Key Points**

- State public utility commissions (PUCs) increasingly maintain formal community microgrid or resilience program dockets, though specific rules (tariff structures, interconnection procedures, cost recovery mechanisms) vary substantially by state and are not federally standardized.
- The question of "who serves as the microgrid operator/utility of record" during islanded operation is a critical and sometimes unresolved regulatory question, since traditional utility franchise law may not clearly address a scenario where a non-utility entity is providing electric service to multiple customers during an island event.
- Equity considerations have become a prominent design driver, with many recent community microgrid and resilience hub programs (particularly those funded through public grant programs) explicitly prioritizing underserved or historically disadvantaged communities and populations with elevated vulnerability during outages (medically dependent individuals, extreme-heat-vulnerable populations).

[Inference] Given the regulatory variation across states and the relative novelty of large-scale community microgrid deployment compared to single-owner microgrids, project development timelines for community microgrids likely remain longer and more uncertain on average due to the added regulatory and multi-stakeholder coordination burden, though this varies considerably by state regulatory maturity and specific project structure and has not been comprehensively benchmarked across the industry.

### Funding and Financing Mechanisms

**Key Points**

- Federal funding sources relevant to community microgrids and resilience hubs include DOE grid resilience and innovation partnership programs, FEMA hazard mitigation and Building Resilient Infrastructure and Communities (BRIC) grants, and USDA rural development programs for cooperative-served areas.
- State-level resilience grant programs, often funded through system benefit charges, cap-and-trade/carbon market proceeds, or dedicated state resilience bonds, have proliferated as wildfire, extreme heat, and storm-related outage risks have increased policy attention on distributed resilience solutions.
- Private financing mechanisms include power purchase agreements (PPAs) for on-site generation, energy-as-a-service models where a third party owns and operates the DER/storage assets, and green bonds or resilience bonds for larger multi-facility community deployments.

### Practical Example: Coastal Town Resilience Hub Network

Consider a coastal municipality developing a network of three resilience hubs (a library, a recreation center, and a school gymnasium) as an initial phase toward a broader community microgrid, motivated by recurring hurricane-driven multi-day outages.

1. **Site selection and load audit**: Each facility undergoes a critical load audit, identifying that the library requires approximately 40 kW for lighting, HVAC minimum service, and a public charging/communications area; the recreation center requires 60 kW to support its function as an emergency shelter (including basic refrigeration and cooking equipment); the school gymnasium requires 75 kW under a similar shelter-use scenario.
2. **DER sizing**: Each site receives a rooftop or canopy solar PV array (sized to the facility's roof/parking area) paired with a BESS sized to cover approximately 24–48 hours of critical load without solar replenishment, accounting for the seasonal solar resource during hurricane season.
3. **Interconnection and utility coordination**: The municipality partners with the incumbent investor-owned utility under a state PUC-approved resilience hub interconnection tariff, clarifying islanding rights, telemetry-sharing requirements, and utility visibility into each site's DER capacity.
4. **Phased microgrid expansion**: The three hubs are initially developed as independent, standalone islandable facilities (each with its own PCC and grid-forming BESS); a subsequent phase links the recreation center and adjacent residential blocks into a shared distribution-level community microgrid, contingent on securing a state resilience grant to fund the additional distribution infrastructure and multi-customer governance agreement.

**Output**

During a subsequent hurricane-driven multi-day outage, all three resilience hubs successfully island and sustain critical loads throughout the event, with the recreation center serving as a functioning emergency shelter for approximately 150 displaced residents — demonstrating the standalone-facility resilience hub model as a practical, lower-regulatory-complexity precursor to full multi-customer community microgrid development.

### Related Topics

- Microgrid Architectures and Control Hierarchies
- Black Start Capability from Distributed Resources
- Grid-Connected and Islanded Operating Modes
- FERC Order 2222 and Wholesale Market Participation of DERs
- Critical Load Prioritization and Load Shedding Strategy Design
- State Public Utility Commission Regulatory Frameworks for DERs
- Energy Equity and Environmental Justice in Grid Modernization Programs
- Battery Energy Storage System (BESS) Sizing for Resilience Applications