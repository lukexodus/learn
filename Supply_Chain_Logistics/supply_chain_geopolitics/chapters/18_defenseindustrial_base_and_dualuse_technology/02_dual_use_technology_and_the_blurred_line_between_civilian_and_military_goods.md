## Dual Use Technology and the Blurred Line Between Civilian and Military Goods


### Definitional Framework

Dual-use technology refers to goods, software, and technical information that have legitimate civilian commercial applications while also possessing military or weapons-relevant applications, creating a regulatory and supply chain security challenge distinct from either purely civilian goods (unregulated for security purposes) or purely military goods (subject to comprehensive, dedicated defense export control regimes). The dual-use category has expanded dramatically in scope and significance over recent decades as advanced civilian technologies — particularly in semiconductors, artificial intelligence, biotechnology, advanced materials, and precision manufacturing — have become simultaneously foundational to both civilian economic competitiveness and modern military capability, a convergence that renders the traditional conceptual boundary between "the defense industrial base" (covered in the prior topic) and "the general commercial technology economy" increasingly difficult to maintain in practice.

### Regulatory Architecture: How Dual-Use Goods Are Controlled

**Key Points**

- Dual-use export controls are generally administered through separate legal and institutional frameworks from purely military "munitions list" controls. In the United States, dual-use items are governed primarily through the Export Administration Regulations (EAR), administered by the Bureau of Industry and Security (BIS) within the Department of Commerce, while purely military items are governed through the International Traffic in Arms Regulations (ITAR), administered by the Department of State — a bifurcated structure reflected with variation in most major exporting countries' control regimes.
- Multilaterally, dual-use export control coordination among major exporting nations occurs primarily through the **Wassenaar Arrangement**, a voluntary, non-treaty multilateral export control regime (successor to the Cold War-era COCOM, Coordinating Committee for Multilateral Export Controls) through which 42 participating states coordinate control lists and information-sharing regarding dual-use goods and technologies, though Wassenaar decisions are not binding and require unanimous consensus among all participating states, creating a structural limitation on the regime's ability to respond rapidly to emerging technology categories or to coordinate action against specific destination countries where consensus cannot be reached (notably, this consensus requirement has limited Wassenaar's practical relevance for coordinating export restrictions specifically targeting China, since achieving unanimous multilateral agreement on China-specific controls has proven difficult, leading major exporting nations, particularly the U.S., to increasingly rely on unilateral and "minilateral" — small-group, like-minded coalition — controls instead, as seen in the AI chip export control content discussed elsewhere in this course).

### Classification Architecture

```plaintext
===MERMAID_DIAGRAM">
    A[Technology/Good in Question] --> B{Purely Civilian<br/>No Military Application}
    A --> C{Dual-Use<br/>Both Civilian and Military Application}
    A --> D{Purely Military<br/>Munitions List Item}

    B --> E[No Export Control<br/>Beyond General Trade Rules]
    C --> F[Export Administration Regulations<br/>EAR / Commerce Control List]
    D --> G[International Traffic in Arms<br/>Regulations / Munitions List]

    F --> H[Wassenaar Arrangement<br/>Multilateral Coordination - Non-binding]
    F --> I[Unilateral / Minilateral Controls<br/>e.g. US AI chip export rules]
```

Note: rendered here as a flowchart despite the truncated opening tag above — treat as an illustrative classification tree; the categories described are the substantive content.

### Historical Evolution of the Dual-Use Category

**Key Points**

- The conceptual and regulatory category of "dual-use" technology gained particular prominence during the Cold War, when COCOM coordinated Western allied restrictions on technology exports to the Soviet bloc that could enhance Soviet military-industrial capability even where the underlying technology (e.g., certain computing and machine tool technologies) had substantial civilian application within the exporting countries themselves.
- The scope of practically significant dual-use technology has expanded substantially since that era, driven by the convergence of several trends: the increasing military relevance of information technology and precision electronics (a category with obviously enormous civilian application), the rise of artificial intelligence as a technology with direct military applications (autonomous systems, intelligence analysis, targeting systems) built on largely civilian-developed AI research and largely civilian-manufactured semiconductor hardware, and advances in biotechnology and additive manufacturing (3D printing) that similarly straddle civilian and military-relevant application categories.

### Case Study: Semiconductors as the Paradigmatic Modern Dual-Use Technology

The semiconductor supply chain — covered in depth elsewhere in this course in the context of the Huawei dispute and AI compute geopolitics — represents perhaps the clearest contemporary illustration of dual-use technology's practical significance. Advanced semiconductor manufacturing equipment (extreme ultraviolet lithography systems produced by the Netherlands' ASML being the most concentrated and consequential example) has overwhelmingly civilian commercial application (consumer electronics, general computing) but is also the essential enabling technology for advanced military systems and, more recently, for the large-scale AI compute infrastructure increasingly recognized as having direct military-relevant application (autonomous weapons targeting, intelligence processing, military logistics optimization). This connects directly to the AI diffusion framework and BIS export control content covered earlier in this chapter: those controls are, at their technical core, dual-use export controls applied to a technology category (advanced AI accelerator chips) whose civilian commercial applications (cloud computing, consumer AI services, scientific research) vastly outnumber its direct military applications in absolute volume terms, yet whose military-relevant applications are considered sufficiently strategically significant to justify comprehensive control.

### Case Study: Biotechnology Dual-Use Concerns

**Key Points**

- Biotechnology represents a distinct and, in some respects, more ethically and technically fraught dual-use category, since techniques and equipment used in legitimate civilian biomedical research (gene synthesis technology, gain-of-function research methodologies used to study pathogen characteristics for vaccine and public health preparedness purposes) carry a documented, if generally low-probability, potential for misuse in biological weapons development, a concern often termed "dual-use research of concern" (DURC) in biosafety and biosecurity policy literature.
- This category illustrates a distinct regulatory challenge relative to semiconductors or conventional dual-use hardware: biotechnology dual-use risk often resides more in *technical knowledge and methodology* than in controllable physical hardware, making export-control-style approaches (which function most effectively for physical goods crossing a border with an inspectable customs process) less directly applicable, and requiring greater reliance on institutional biosafety review processes, publication review norms within the scientific community, and international biosecurity frameworks (such as the Biological Weapons Convention) rather than hardware-focused export licensing alone.

### Case Study: Commercial Drone and Autonomous Systems Technology

Commercial unmanned aerial vehicle (drone) technology, developed and manufactured predominantly for civilian applications (agriculture, photography, logistics, recreational use), has demonstrated significant dual-use military relevance, prominently illustrated by the extensive use of modified commercial and quasi-commercial drones for military reconnaissance and strike purposes in the Russia-Ukraine conflict. This case is particularly notable for supply chain security analysis because it demonstrates that dual-use risk can emerge from mass-market consumer technology with a low per-unit cost and extremely broad commercial distribution, a fundamentally different risk profile from the traditionally envisioned dual-use category of specialized, expensive, limited-distribution industrial equipment — meaning effective control of this category through traditional export licensing (designed around larger, more traceable industrial transactions) is significantly more difficult given the scale, low unit cost, and commercial ubiquity of the underlying hardware.

### The Compliance Burden on Civilian Technology Firms

**Key Points**

- The expansion of dual-use control scope has imposed a growing compliance burden on civilian technology companies that may not consider themselves part of the defense industrial base at all, requiring export control classification determinations, end-user and end-use screening, and licensing processes for products whose primary market and design intent is entirely civilian commercial.
- This creates a distinct supply chain security dynamic from the traditional defense industrial base structure discussed in the prior topic: companies newly drawn into dual-use compliance obligations (semiconductor firms, cloud service providers, AI model developers, advanced materials manufacturers) often lack the mature export control compliance infrastructure that traditional defense primes have developed over decades of ITAR/EAR experience, creating a documented compliance capability gap precisely in the sectors where dual-use control scope has most rapidly expanded (a dynamic explicitly referenced in the AI compute geopolitics content regarding data center operators facing new compliance obligations under evolving BIS rules).
- This dynamic also creates innovation-policy tension: overly broad or unpredictable dual-use control scope risks imposing compliance costs and market access restrictions on civilian technology development and commercial competitiveness in the name of a security rationale that may, for many specific product applications, have limited practical military relevance, while overly narrow control scope risks failing to capture genuinely militarily significant technology transfer — a calibration challenge that becomes more difficult as the pace of civilian technology innovation (particularly in AI) outstrips the traditional multi-year update cycles of formal control list revision processes.

### Comparative Table: Dual-Use Technology Categories and Control Approaches

| Technology Category | Primary Civilian Application | Primary Military Relevance | Control Approach Challenge |
| --- | --- | --- | --- |
| Advanced semiconductors/AI chips | Cloud computing, consumer electronics, AI services | Autonomous systems, intelligence processing, weapons guidance | Physical good, controllable via manufacturing equipment chokepoint (ASML) |
| Biotechnology/gene synthesis | Vaccine development, medical research | Biological weapons potential (low probability, high consequence) | Knowledge/methodology-based risk, poorly suited to hardware export control |
| Commercial drones/UAS | Agriculture, photography, logistics | Reconnaissance, modified strike platforms | Mass-market scale defeats traditional licensing approaches |
| Advanced materials/additive manufacturing | Aerospace, automotive, medical devices | Precision weapons components, restricted-technology replication | Design file/software control complexity (files, not just physical goods) |
| Cryptography/cybersecurity tools | Commercial data security, financial systems | Military communications security, offensive cyber capability | Long-standing category with mature but contested control framework |

### Systemic Lessons

**Conclusion**

Dual-use technology represents the conceptual bridge connecting this chapter's defense industrial base content to nearly every other technology supply chain topic covered in this course, since the semiconductor, AI compute, telecommunications, and even certain biotechnology and cybersecurity supply chains discussed throughout are, from a regulatory and strategic perspective, fundamentally dual-use categories rather than purely civilian or purely military domains. The central structural challenge is that the traditional regulatory and institutional architecture for managing dual-use risk — export licensing regimes designed around discrete, traceable, moderate-volume industrial transactions, coordinated multilaterally through consensus-based frameworks like Wassenaar — is increasingly poorly matched to the actual character of the most strategically significant contemporary dual-use technologies, which are frequently mass-market, software-embedded, rapidly evolving, and produced by civilian commercial firms with limited defense-sector compliance experience. This mismatch is driving the same shift observed in the AI compute geopolitics content — away from slow, consensus-based multilateral coordination and toward faster-moving unilateral and minilateral control mechanisms — a trend likely to continue as the pace of civilian dual-use-relevant innovation continues to outstrip the institutional capacity of traditional export control frameworks to classify and respond to emerging technology categories in real time.

**Next Steps**

- Wassenaar Arrangement structure, consensus requirement, and comparison to Cold War-era COCOM
- EAR versus ITAR jurisdictional boundaries and classification determination processes
- Dual-use research of concern (DURC) policy frameworks and the Biological Weapons Convention
- Commercial drone/UAS proliferation and battlefield use in the Russia-Ukraine conflict
- Export control compliance capability gaps among non-traditional dual-use firms (AI, cloud, biotech)
- Additive manufacturing (3D printing) design file control and digital proliferation risk
- Minilateral export control coalitions as an alternative to consensus-based multilateral regimes
- Comparative analysis: dual-use semiconductor controls versus dual-use biotechnology governance
- Cryptography export control history as a precedent for contemporary AI dual-use debates