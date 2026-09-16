## Pure versus Impure Public Goods

### Defining Characteristics: Excludability and Rivalry

The classification of goods in public economics rests on two independent binary characteristics: excludability and rivalry in consumption.

**Excludability** refers to the extent to which it is technologically or legally feasible to prevent individuals who have not paid for a good from consuming it. A good is excludable if the provider can exclude non-payers; it is non-excludable if exclusion is impossible or prohibitively costly.

**Rivalry (or rivalrousness)** refers to whether one person's consumption of a unit of the good diminishes the quantity or quality available to others. A good is rival if consumption by one person reduces availability for others; it is non-rival if one person's consumption does not diminish what is available to anyone else, meaning the marginal cost of an additional consumer is zero.

These two dimensions generate a four-way taxonomy:

|  | Excludable | Non-Excludable |
| --- | --- | --- |
| **Rival** | Private Goods | Common-Pool Resources |
| **Non-Rival** | Club Goods (Impure Public Goods) | Pure Public Goods |

### Pure Public Goods: Formal Definition

A pure public good is defined by the simultaneous presence of complete non-excludability and complete non-rivalry. Formally, if $X$ is the total quantity of the public good provided and $x_i$ is the amount consumed or enjoyed by individual $i$, a pure public good satisfies:

$$x_i = X \text{ for all individuals } i$$

This is the defining feature of joint or non-rival consumption: everyone consumes the same total quantity $X$ simultaneously, in contrast to private goods where $X = \sum_i x_i$ (aggregate supply equals the sum of individual consumption shares).

Samuelson's (1954) classic formulation defines a pure public good as one for which each individual's consumption of the good leads to no subtraction from any other individual's consumption of that good. Canonical textbook examples include national defense, a lighthouse's warning signal, basic scientific knowledge, and clean air over a wide geographic area (though the last is a matter of degree, see "Degrees of Publicness" below).

### Impure Public Goods: Formal Definition

An impure public good possesses excludability and/or rivalry only partially, or exhibits congestion effects, meaning it does not satisfy both pure conditions simultaneously across the full relevant range of consumption. Impure public goods fall into two broad subcategories:

**Club Goods**: Excludable but non-rival (or only rival under congestion). A club good can be restricted to paying members, but consumption by additional members within capacity does not reduce the benefit to existing members. Examples include cable television, toll roads below congestion thresholds, satellite radio, and private swimming pools with membership fees. The theory of club goods was formalized by Buchanan (1965), who modeled the optimal club size as balancing the benefits of cost-sharing among more members against the costs of congestion as membership grows (see Chapter: Theory of Clubs for full treatment).

**Common-Pool Resources (Common Property Resources)**: Non-excludable but rival. It is difficult or costly to exclude users, yet consumption by one user does reduce the amount available to others. Examples include ocean fisheries, groundwater aquifers, and unregulated grazing land. These goods are prone to the "tragedy of the commons," a distinct market failure mechanism from the free-rider problem associated with pure public goods (see Chapter: Common Property Resources).

**Congestible Public Goods**: A good that behaves as non-rival at low utilization levels but becomes increasingly rival as usage approaches capacity. Highways, public parks, and public libraries are classic examples: below a congestion threshold, an additional user imposes no cost on others, but beyond that threshold, crowding reduces the quality of the good for all users. Formally, if $N$ is the number of users, the good is non-rival for $N \leq \bar{N}$ (the congestion threshold) but exhibits declining marginal benefit per user for $N > \bar{N}$.

### Degrees of Publicness: A Continuum, Not a Dichotomy

In practice, few goods are purely public or purely private; most fall along a continuum. Economists frequently describe goods in terms of the "degree of publicness," incorporating:

- **Geographic scope**: Local public goods (a local park, street lighting) benefit a spatially bounded population, whereas national public goods (national defense) benefit an entire country's population; this spatial dimension is central to the theory of fiscal federalism and the Tiebout model (see Chapter: Fiscal Federalism and Local Public Goods)
- **Partial excludability**: Encrypted satellite signals can technically exclude non-subscribers but at a positive cost, making the good excludable in principle but with real resource costs attached to exclusion
- **Partial rivalry**: Congestible goods, as above, blend rival and non-rival characteristics depending on utilization

### The Free-Rider Problem in Pure Public Goods

Non-excludability in pure public goods creates the free-rider problem: because individuals cannot be prevented from consuming the good regardless of whether they contribute to its financing, each individual has an incentive to understate their true valuation or contribute nothing, hoping others will provide the good instead. This leads to systematic underprovision relative to the social optimum under voluntary private provision.

The efficient provision condition for a pure public good is given by the Samuelson Condition, which requires that the sum of individual marginal rates of substitution (marginal willingness to pay) equal the marginal rate of transformation (marginal cost of provision):

$$\sum_{i=1}^{n} MRS_i = MRT$$

This contrasts with the efficiency condition for private goods, where each individual's MRS must separately equal the MRT ($MRS_i = MRT$ for each $i$), because private goods are consumed exclusively rather than jointly. The vertical summation of individual demand curves (rather than horizontal summation, as with private goods) to derive aggregate willingness to pay is the graphical counterpart of the Samuelson Condition (see Chapter: Efficient Provision of Public Goods for the full derivation and diagrammatic treatment).

Because voluntary contribution mechanisms induce free-riding, the market-determined quantity of a pure public good, $X^{market}$, is generically less than the Pareto-efficient quantity, $X^*$, that would satisfy the Samuelson Condition:

$$X^{market} < X^*$$

Impure public goods are less susceptible to free-riding to the extent that excludability is present (club goods can charge admission or subscription fees, internalizing at least part of the financing problem) or capable of being managed through access institutions that limit rivalry (common-pool resources can, in principle, be managed via well-defined property rights, quotas, or Ostrom-style community governance, though these solutions require overcoming their own collective action problems).

### Diagram: Taxonomy of Goods by Excludability and Rivalry (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 720 420">
<text x="360" y="28" font-size="18" font-weight="bold" text-anchor="middle" fill="#1a1a1a">Taxonomy of Goods (svg_diagram)</text>
<line x1="150" y1="60" x2="150" y2="390" stroke="#333" stroke-width="1.5" />
<line x1="150" y1="390" x2="700" y2="390" stroke="#333" stroke-width="1.5" />

<text x="90" y="120" font-size="13" text-anchor="middle" fill="#333">Rival</text>

<text x="90" y="300" font-size="13" text-anchor="middle" fill="#333">Non-Rival</text>

<text x="290" y="410" font-size="13" text-anchor="middle" fill="#333">Excludable</text>

<text x="550" y="410" font-size="13" text-anchor="middle" fill="#333">Non-Excludable</text>

<rect x="170" y="70" width="240" height="150" fill="#4a7fa5" opacity="0.85" />
<text x="290" y="130" font-size="14" font-weight="bold" fill="white" text-anchor="middle">Private Goods</text>
<text x="290" y="152" font-size="11" fill="white" text-anchor="middle">Food, clothing,</text>
<text x="290" y="168" font-size="11" fill="white" text-anchor="middle">personal vehicles</text>
<rect x="420" y="70" width="240" height="150" fill="#c0392b" opacity="0.85" />
<text x="540" y="130" font-size="14" font-weight="bold" fill="white" text-anchor="middle">Common-Pool</text>
<text x="540" y="148" font-size="14" font-weight="bold" fill="white" text-anchor="middle">Resources</text>
<text x="540" y="170" font-size="11" fill="white" text-anchor="middle">Fisheries, aquifers,</text>
<text x="540" y="186" font-size="11" fill="white" text-anchor="middle">grazing land</text>
<rect x="170" y="230" width="240" height="150" fill="#27632a" opacity="0.85" />
<text x="290" y="290" font-size="14" font-weight="bold" fill="white" text-anchor="middle">Club Goods</text>
<text x="290" y="308" font-size="11" fill="white" text-anchor="middle">(Impure Public Goods)</text>
<text x="290" y="326" font-size="11" fill="white" text-anchor="middle">Cable TV, toll roads,</text>
<text x="290" y="342" font-size="11" fill="white" text-anchor="middle">membership clubs</text>
<rect x="420" y="230" width="240" height="150" fill="#2c5f8a" opacity="0.85" />
<text x="540" y="290" font-size="14" font-weight="bold" fill="white" text-anchor="middle">Pure Public Goods</text>
<text x="540" y="312" font-size="11" fill="white" text-anchor="middle">National defense,</text>
<text x="540" y="328" font-size="11" fill="white" text-anchor="middle">basic research,</text>
<text x="540" y="344" font-size="11" fill="white" text-anchor="middle">lighthouse signal</text>
</svg>

### Mixed and Ambiguous Cases

Certain real-world goods resist clean classification and are often described as "mixed goods" or goods with public and private components:

**Education**: Basic education generates substantial positive externalities (an informed, productive citizenry benefits society broadly, which has public-good-like characteristics), yet the direct consumption of educational services is excludable (tuition, enrollment caps) and rival (a seat in a classroom, an instructor's attention), making education fundamentally a private good with positive externalities rather than a pure or impure public good in the strict Samuelson sense. [Inference: whether education is best modeled as a public good with externalities versus a merit good is a matter of some disciplinary debate and depends on the specific margin being analyzed.]

**Radio and Broadcast Television**: The original economic analysis by Samuelson used broadcasting as a canonical example of a pure public good (non-rival because one household's reception does not diminish another's, and historically non-excludable over open airwaves). The advent of encryption and subscription technology (cable, satellite) converted this into an excludable club good, illustrating how technological change can shift a good's position within the taxonomy over time.

**Knowledge and Intellectual Property**: Basic scientific knowledge is inherently non-rival (one person's understanding of a theorem does not diminish another's ability to understand it) and, absent legal intervention, non-excludable once published. Patent and copyright systems are policy interventions that artificially impose excludability on an otherwise pure public good, trading off reduced static efficiency (excludability creates deadweight loss by pricing above zero marginal cost) against dynamic efficiency (excludability restores the private incentive to invest in costly innovation). This tension is central to the economics of intellectual property (see Chapter: Public Goods and Innovation Policy).

### Provision Mechanisms Across the Taxonomy

| Good Type | Typical Provision Mechanism | Primary Failure Mode |
| --- | --- | --- |
| Private Goods | Competitive markets | None (efficient under standard conditions) |
| Club Goods | Membership fees, user charges, private clubs | Suboptimal club size, potential market power |
| Common-Pool Resources | Property rights, quotas, community governance (Ostrom), regulation | Tragedy of the commons, overexploitation |
| Pure Public Goods | Government provision financed by taxation, voluntary contribution (often insufficient) | Free-riding, underprovision |

### Policy Design Implications

The pure/impure distinction carries direct implications for the appropriate policy instrument:

- **Pure public goods** generally justify direct government provision or compulsory financing through taxation, since exclusion-based pricing (user fees) cannot solve the underlying free-rider problem when exclusion itself is infeasible
- **Club goods** can often be left to private or quasi-private provision (homeowners' associations, private toll operators, subscription services) because excludability allows the standard price mechanism to fund provision and ration access
- **Congestible public goods** may warrant congestion pricing (as in road pricing/tolling) once utilization crosses the threshold at which the good transitions from non-rival to rival, aligning marginal private cost with the marginal social cost of congestion
- **Common-pool resources** require either the assignment of property rights (privatization, individual transferable quotas) or non-market institutional solutions (Ostrom's polycentric governance frameworks) to prevent overexploitation, since standard public-goods financing tools (taxation) do not directly address the rivalry-driven overuse problem

**Related Topics**

- The Samuelson Condition and Efficient Provision of Public Goods
- Theory of Clubs and Optimal Club Size (Buchanan Model)
- The Free-Rider Problem and Voluntary Contribution Mechanisms
- Common Property Resources and the Tragedy of the Commons
- Congestion Pricing and Local Public Goods
- Fiscal Federalism and the Tiebout Model
- Public Goods and Intellectual Property Policy
- Lindahl Pricing and Preference Revelation Mechanisms