## Fragmentation of Production Across National Borders


### Overview

Fragmentation of production refers to the disintegration of a formerly vertically integrated production process — one previously conducted within a single firm and often within a single location — into geographically separated production blocks, each performed wherever it can be executed most efficiently, and subsequently linked back together via trade in intermediate inputs. This phenomenon underlies the modern **Global Value Chain (GVC)** system and is a central organizing concept for understanding contemporary international trade patterns, distinct from the "old trade" model in which countries traded predominantly finished goods.

The theoretical treatment of fragmentation draws on international trade theory, the theory of the firm (transaction cost economics), and international business/FDI theory, since fragmentation decisions determine both *where* production stages are located and *whether* they are conducted within the firm (via FDI) or outsourced to independent suppliers (via arm's-length trade).

### Conceptual Distinction: Fragmentation vs. Traditional Trade Theory

Classical and neoclassical trade theory (Ricardian, Heckscher-Ohlin) typically models trade in **final, finished goods** produced entirely within one country, based on that country's comparative advantage in producing the *whole* good. Fragmentation theory instead recognizes that comparative advantage can be exploited at the level of individual **production stages or tasks** within a good's value chain, rather than only at the level of the finished product itself.

This shift is sometimes described in the literature as a move from "trade in goods" to **"trade in tasks"** (a framing closely associated with economists Grossman and Rossi-Hansberg): rather than asking "which country should produce this entire good," the relevant question becomes "which country should perform this specific task or production stage within the good's value chain."

### Necessary Preconditions for Fragmentation

Fragmentation of production only becomes economically viable, and expands, when specific conditions are met:

#### 1. Falling "Service Link" / Coordination Costs

Fragmenting production incurs additional costs of coordinating and linking dispersed production blocks — termed **service link costs** in the seminal fragmentation literature (associated with Ronald Jones and Henryk Kierzkowski). These include:

- **Transport costs**: physically moving intermediate inputs between production locations
- **Communication and coordination costs**: managing specifications, quality control, and scheduling across dispersed sites
- **Trade policy costs**: tariffs and non-tariff barriers applied each time a good crosses a border (which, in a fragmented supply chain, may occur multiple times as a product moves through successive stages — sometimes called "tariff cascading" or the compounding of tariffs across a value chain)

Fragmentation expands specifically because **technological improvements in transport and communication** (e.g., containerization, jet freight, and especially advances in information and communication technology, ICT) have driven a secular decline in these service link costs over recent decades, making it profitable to geographically separate production blocks that would previously have needed to be co-located.

#### 2. Sufficient Factor Price Differences Across Locations

Fragmentation is economically worthwhile only if the cost savings from relocating a specific task to a lower-cost location exceed the additional service link costs of coordinating across the fragmented structure. This requires sufficiently large cross-country differences in the cost of the factors most intensively used in that particular task (e.g., large wage differentials for labor-intensive assembly tasks).

#### 3. "Slicing" Feasibility of the Production Process

Not all production processes can be feasibly divided into geographically separable stages. Fragmentation is more feasible where:

- Production stages are **technologically separable** (can be physically performed at different locations without requiring simultaneous, tightly-coupled interaction)
- Intermediate outputs are **transportable** at reasonable cost relative to their value
- Quality and specifications can be **codified** and communicated across the fragmented stages (as opposed to requiring uncodifiable tacit, face-to-face coordination)

### Formal Framework: The Fragmentation Decision

A simplified formalization, drawing on the Jones-Kierzkowski "service link" framework, considers a firm deciding whether to keep production integrated at home or fragment a specific stage abroad.

Let the total unit cost of production, if kept integrated at home, be:

$$C_{integrated} = w_H \cdot a_H$$

where $w_H$ is the home wage rate and $a_H$ is the labor input coefficient for the full process at home.

If the firm fragments a labor-intensive stage to a foreign location with lower wage $w_F < w_H$, the fragmented unit cost becomes:

$$C_{fragmented} = w_H \cdot a_H^{remaining} + w_F \cdot a_F^{stage} + SL$$

where $a_H^{remaining}$ is the reduced home labor coefficient (for stages retained at home), $a_F^{stage}$ is the foreign labor coefficient for the offshored stage, and $SL$ represents the service link cost (transport, coordination, tariffs) of connecting the two production blocks.

Fragmentation is profitable when:

$$C_{fragmented} < C_{integrated}$$



$$w_F \cdot a_F^{stage} + SL < w_H \cdot (a_H - a_H^{remaining})$$

This condition makes explicit the central tradeoff: the wage savings from offshoring the labor-intensive stage (right-hand side) must exceed the sum of the foreign production cost plus the service link cost (left-hand side). As $SL$ falls over time (due to transport/ICT improvements), fragmentation becomes profitable across a widening range of tasks and country-pairs, even where wage differentials are moderate.

### Modes of Fragmentation: Offshoring vs. Outsourcing

Fragmentation decisions involve two analytically separable dimensions, often represented as a 2x2 matrix in the GVC/international business literature:

|  | **Produced In-House** | **Produced by Independent Firm** |
| --- | --- | --- |
| **Domestic Location** | Domestic in-house production | Domestic outsourcing |
| **Foreign Location** | Offshoring (via FDI / captive offshoring) | Offshore outsourcing |

- **Offshoring**: relocating a production stage to a foreign country, regardless of whether it remains within the firm's ownership boundary
- **Outsourcing**: contracting a production stage to an independent (non-affiliated) supplier, regardless of location
- **Captive offshoring** (a form of vertical/efficiency-seeking FDI, connecting directly to the OLI paradigm discussed under MNE theory): the firm relocates the stage abroad *and* retains ownership/control via a foreign affiliate
- **Offshore outsourcing (arm's-length)**: the firm relocates the stage abroad but contracts with an *independent* foreign supplier rather than owning the facility itself

The choice between captive offshoring and offshore outsourcing is governed by the same **Internalization (I)** logic from the OLI paradigm: firms internalize (choose captive offshoring/FDI) when arm's-length contracting with an independent foreign supplier would expose them to significant contracting hazards — such as difficulty specifying and enforcing quality standards, risk of technology/IP leakage, or hold-up problems in relationship-specific investment.

### Diagram: Fragmentation Decision Matrix (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 420">
\<style\>
.title { font: bold 18px sans-serif; fill: #1a1a1a; }
.axis { font: bold 13px sans-serif; fill: #1a1a1a; }
.cell { font: bold 14px sans-serif; fill: #ffffff; }
.sub { font: 11px sans-serif; fill: #ffffff; }
.box { stroke: #333333; stroke-width: 1.5; }
\</style\>
<text x="400" y="30" text-anchor="middle" class="title">Fragmentation Modes: Location x Ownership (svg_diagram)</text>

<text x="400" y="65" text-anchor="middle" class="axis">Governance Mode</text>

<text x="220" y="90" text-anchor="middle" class="axis">In-House (Own)</text>

<text x="580" y="90" text-anchor="middle" class="axis">Independent Supplier</text>

<text x="60" y="200" text-anchor="middle" class="axis" transform="rotate(-90 60 200)">Location</text>

<text x="90" y="170" class="axis">Domestic</text>

<text x="90" y="330" class="axis">Foreign</text>

<rect x="130" y="110" width="220" height="140" rx="8" fill="#2c5f8a" class="box" />
<text x="240" y="150" text-anchor="middle" class="cell">Domestic</text>
<text x="240" y="170" text-anchor="middle" class="cell">In-House</text>
<text x="145" y="200" class="sub">Traditional vertically</text>
<text x="145" y="220" class="sub">integrated production</text>
<rect x="420" y="110" width="220" height="140" rx="8" fill="#3a7a3a" class="box" />
<text x="530" y="150" text-anchor="middle" class="cell">Domestic</text>
<text x="530" y="170" text-anchor="middle" class="cell">Outsourcing</text>
<text x="435" y="200" class="sub">Contracted to local</text>
<text x="435" y="220" class="sub">independent supplier</text>
<rect x="130" y="270" width="220" height="140" rx="8" fill="#8a4a2c" class="box" />
<text x="240" y="310" text-anchor="middle" class="cell">Captive</text>
<text x="240" y="330" text-anchor="middle" class="cell">Offshoring (FDI)</text>
<text x="145" y="360" class="sub">Vertical/efficiency-seeking</text>
<text x="145" y="380" class="sub">FDI; internalized (OLI: I)</text>
<rect x="420" y="270" width="220" height="140" rx="8" fill="#6a3a8a" class="box" />
<text x="530" y="310" text-anchor="middle" class="cell">Offshore</text>
<text x="530" y="330" text-anchor="middle" class="cell">Outsourcing</text>
<text x="435" y="360" class="sub">Arm's-length contract</text>
<text x="435" y="380" class="sub">with foreign supplier</text>
</svg>

### Measurement: Trade in Intermediate Inputs and Value-Added Trade

Standard gross trade statistics substantially **overstate** the domestic value-added content embodied in trade flows once production is fragmented, because they record the full gross value of a good each time it crosses a border, potentially multiple times across successive fragmented stages.

This has motivated development of **Trade in Value Added (TiVA)** accounting frameworks, and specific metrics used in the GVC literature:

- **Vertical Specialization (VS)**: the *imported* intermediate input content embodied in a country's exports (i.e., how much of what a country exports was itself previously imported)
- **Domestic Value-Added (DVA) share of exports**: the complement of VS — the portion of gross export value that reflects value genuinely added domestically
- **GVC participation index**: typically decomposed into "backward participation" (foreign value-added embodied in a country's own exports) and "forward participation" (a country's domestically produced value-added that is embodied in *other* countries' exports, i.e., used as an input further down the chain)

**Illustrative measurement distortion**: A now widely-cited example in the GVC literature is the "value capture" case of a mobile phone assembled in one country, where component inputs are sourced from many other countries, and the assembling country's *gross* export value for the finished phone dramatically overstates the *value-added* that country actually contributed (which may be limited largely to low-cost final assembly), with the bulk of value captured by countries supplying high-value components, design, and branding services.

### Fragmentation and the "Smile Curve"

A widely used stylized concept describing how value-added is distributed **across stages** of a fragmented value chain: value-added tends to be highest at the pre-production (R&D, design, branding) and post-production (marketing, distribution, after-sales service) ends of the chain, and lowest in the middle physical-manufacturing/assembly stage — producing a curve resembling a smile when value-added is plotted against production stage sequence.

**[Inference]** The smile curve is best understood as a stylized, illustrative heuristic rather than a universally verified empirical law; the specific shape and the location of the value-added trough vary considerably by industry, product, and the specific firms involved, and some empirical work has questioned how uniformly this pattern holds across all sectors.

### Diagram: Production Fragmentation and Trade Flow (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 900 380">
\<style\>
.title { font: bold 18px sans-serif; fill: #1a1a1a; }
.stage { font: bold 13px sans-serif; fill: #ffffff; }
.item { font: 11px sans-serif; fill: #1a1a1a; }
.box { stroke: #333333; stroke-width: 1.5; }
.arrow { stroke: #333333; stroke-width: 2; marker-end: url(#ah3); fill: none; }
\</style\>
<text x="450" y="30" text-anchor="middle" class="title">Fragmented Production Chain Across Countries (svg_diagram)</text>
<rect x="20" y="80" width="160" height="90" rx="8" fill="#2c5f8a" class="box" />
<text x="100" y="105" text-anchor="middle" class="stage">Country A</text>
<text x="35" y="130" class="item">R&amp;D / Design</text>
<text x="35" y="150" class="item">(High value-added)</text>
<rect x="230" y="80" width="160" height="90" rx="8" fill="#8a4a2c" class="box" />
<text x="310" y="105" text-anchor="middle" class="stage">Country B</text>
<text x="245" y="130" class="item">Component</text>
<text x="245" y="150" class="item">Manufacturing</text>
<rect x="440" y="80" width="160" height="90" rx="8" fill="#3a7a3a" class="box" />
<text x="520" y="105" text-anchor="middle" class="stage">Country C</text>
<text x="455" y="130" class="item">Final Assembly</text>
<text x="455" y="150" class="item">(Lower value-added)</text>
<rect x="650" y="80" width="160" height="90" rx="8" fill="#6a3a8a" class="box" />
<text x="730" y="105" text-anchor="middle" class="stage">Country D</text>
<text x="665" y="130" class="item">Marketing /</text>
<text x="665" y="150" class="item">Distribution</text>
<path d="M 180 125 L 230 125" class="arrow" />
<path d="M 390 125 L 440 125" class="arrow" />
<path d="M 600 125 L 650 125" class="arrow" />

<text x="450" y="220" text-anchor="middle" class="item" style="font-weight:bold;">Value-Added by Stage ("Smile Curve" pattern)</text>

<path d="M 60 320 Q 100 250 310 300 Q 500 350 520 320 Q 600 250 730 250" stroke="`#d4a017`" stroke-width="3" fill="none" />

<text x="100" y="245" class="item">High</text>

<text x="500" y="345" class="item">Low</text>

<text x="730" y="245" class="item">High</text>

</svg>

### Implications for International Trade Theory and Policy

- **Comparative advantage at the task level**: fragmentation implies that a country need not have comparative advantage in an entire product category to participate in its production — it need only have comparative advantage in the *specific tasks* it performs, substantially widening the scope for gains from trade even for countries with narrow specialized capabilities
- **Amplified sensitivity to trade costs**: because intermediate inputs may cross multiple borders during fragmented production, tariffs and non-tariff barriers have a **compounding effect** across a fragmented value chain (tariffs applied at each border crossing), making fragmented production networks disproportionately sensitive to trade policy changes and trade cost increases relative to trade in finished goods produced entirely in one country
- **"Bystander effects" of trade policy**: a tariff imposed by Country X on inputs from Country Y can indirectly harm Country Z if Z's exports incorporate those tariffed inputs — a phenomenon increasingly relevant given the dense web of GVC linkages
- **Reshaping of the gains-from-trade distribution**: fragmentation changes not only *how much* trade occurs but *who benefits* within each country, since offshoring specific labor-intensive tasks can generate distributional effects resembling those predicted by the Stolper-Samuelson theorem, but at the level of *tasks* rather than *sectors* — potentially explaining wage/employment effects on specific occupational groups (e.g., routine-task workers) that cut across traditional industry classifications

### Recent Developments: Reshoring, Nearshoring, and Supply Chain Resilience

**[Inference]** Following a series of disruptive shocks (including the COVID-19 pandemic's supply chain disruptions and heightened geopolitical tensions among major economies), there has been increased policy and corporate attention to **supply chain resilience**, sometimes producing pressure toward:

- **Reshoring**: bringing previously offshored production stages back to the home country
- **Nearshoring**: relocating offshored stages to geographically or politically closer countries rather than reversing fragmentation entirely
- **Friend-shoring** (or "ally-shoring"): reorganizing supply chains to concentrate fragmented production stages among geopolitically aligned countries

**[Unverified]** The extent to which these trends represent a genuine, large-scale reversal of the decades-long fragmentation trend (as opposed to more limited, sector-specific adjustments concentrated in strategically sensitive industries such as semiconductors) remains a subject of ongoing empirical assessment and is best evaluated against current trade and FDI flow data rather than treated as an established structural shift.

### Common Misconceptions

- **Misconception**: "Fragmentation is the same phenomenon as outsourcing." Fragmentation is the broader geographic/organizational phenomenon (splitting production into stages performed in different locations); outsourcing is one specific *governance mode* of fragmentation (using independent suppliers rather than in-house/affiliate production) — fragmentation can occur entirely within firm boundaries via captive offshoring/FDI.
- **Misconception**: "A country's gross export value reflects the value it actually created." As illustrated by the mobile-phone example above, gross export statistics can substantially overstate a country's genuine domestic value-added contribution once inputs are fragmented and sourced internationally; value-added trade measures are necessary to correct for this.
- **Misconception**: "Fragmentation only benefits low-wage developing countries seeking assembly work." **[Inference]** The smile-curve pattern suggests high-income countries specializing in pre-production (design, R&D) and post-production (branding, marketing) stages often capture disproportionately large shares of total value-added, meaning fragmentation's distributional benefits are not straightforwardly tilted toward the countries performing the physically visible manufacturing stage.

### Related Topics

- Trade in Tasks framework (Grossman and Rossi-Hansberg)
- Jones-Kierzkowski service-link fragmentation model
- Global Value Chain (GVC) governance types (Gereffi's typology: market, modular, relational, captive, hierarchy)
- Trade in Value Added (TiVA) accounting and OECD-WTO TiVA database
- Vertical specialization and backward/forward GVC participation indices
- Stolper-Samuelson theorem and task-based trade models of wage inequality
- Reshoring, nearshoring, and friend-shoring: empirical trends and measurement
- Tariff cascading effects in multi-stage global value chains
- Foreign Direct Investment as a governance mode for fragmented production (linking to OLI paradigm)
- Semiconductor supply chain fragmentation as a case study in strategic industry policy