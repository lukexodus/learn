## Addition and Condensation Polymerization


### Overview

Polymers are macromolecules built from repeating structural units (monomers) linked by covalent bonds. The two principal mechanisms by which monomers combine into polymer chains are **addition (chain-growth) polymerization** and **condensation (step-growth) polymerization**. These mechanisms differ fundamentally in how the chain grows, whether byproducts are released, the kinetics of molecular weight buildup, and the resulting polymer architecture.

### Addition (Chain-Growth) Polymerization

**Defining Characteristics**

Addition polymerization involves the sequential addition of monomer units to a growing, reactive chain end, with no loss of atoms or small-molecule byproducts. The molecular formula of the polymer repeat unit is identical to that of the monomer. Monomers are typically unsaturated compounds — most commonly vinyl monomers containing a C=C double bond ($\text{CH}_2=\text{CHX}$) — although ring-opening polymerization of cyclic monomers also proceeds by a chain mechanism.

**General Reaction**

$$n\, \text{CH}_2=\text{CHX} \longrightarrow -[\text{CH}_2-\text{CHX}]_n-$$

**Mechanistic Stages**

1. **Initiation**: an initiator generates a reactive species (radical, cation, or anion) that adds across the monomer's double bond, creating the first active chain center.
2. **Propagation**: the active center adds successive monomer units, regenerating the reactive site at the new chain end at each step. Chain length grows rapidly once initiated.
3. **Termination**: the active chain end is destroyed, most commonly by combination (two growing chains couple), disproportionation (a hydrogen atom transfers from one chain to another, producing one saturated and one unsaturated chain end), or, in ionic mechanisms, by reaction with a counter-ion, solvent, or deliberate quenching agent.
4. **Chain transfer** (side process): the active center transfers to another molecule (monomer, solvent, or polymer chain), terminating one chain while initiating a new one — this lowers average molecular weight without stopping the overall polymerization.

**Types by Initiating Species**

- **Free-radical polymerization**: initiated by radical sources (e.g., peroxides, AIBN, or photoinitiation). Tolerant of many functional groups and water; used for polyethylene (high-pressure route), polystyrene, PVC, and PMMA. Prone to chain-transfer side reactions and branching.
- **Cationic polymerization**: initiated by strong acids or Lewis acid/co-initiator pairs (e.g., $\text{BF}_3/\text{H}_2\text{O}$). Favored by electron-donating substituents that stabilize carbocation intermediates (e.g., isobutylene for butyl rubber). Highly sensitive to trace moisture and temperature; often requires very low temperatures to suppress chain transfer.
- **Anionic polymerization**: initiated by strong nucleophiles/bases (e.g., alkyllithiums, sodium naphthalenide). Favored by electron-withdrawing substituents that stabilize carbanion intermediates (e.g., styrene, dienes, methyl methacrylate). Under rigorously purified conditions, termination can be effectively absent, giving "living" polymerization.
- **Coordination (Ziegler–Natta / metallocene) polymerization**: uses transition-metal catalysts (e.g., $\text{TiCl}_4/\text{AlEt}_3$) to coordinate and insert monomer in a stereochemically controlled manner, enabling production of linear, stereoregular polyolefins (isotactic/syndiotactic polypropylene) unattainable by radical routes.

**Living Polymerization**

A special case of chain-growth polymerization in which chain transfer and termination are essentially absent, so chains grow only as long as monomer is available and all chains initiate at approximately the same time. This produces polymers with narrow molecular weight distributions (low dispersity, $Đ$ close to 1) and permits synthesis of block copolymers by sequential monomer addition. Living anionic polymerization is the classical example; controlled/"living" radical methods (ATRP, RAFT, NMP) extend similar control to a broader range of monomers and conditions.

**Key Points**

- No small molecule is eliminated; repeat unit = monomer formula.
- Molecular weight rises rapidly early in the reaction — even at low conversion, high-molecular-weight polymer is already present alongside unreacted monomer.
- Reaction mixture at any time contains high-MW polymer, monomer, and only a small population of actively growing chains.
- Kinetic chain length and degree of polymerization depend on the ratio of propagation to termination/transfer rates.

### Condensation (Step-Growth) Polymerization

**Defining Characteristics**

Condensation polymerization proceeds through stepwise reaction between functional groups on monomers (or growing oligomers) of any size, typically releasing a small molecule byproduct such as water, methanol, or HCl at each linkage. Because reaction occurs between any two species bearing complementary functional groups — monomer-monomer, monomer-oligomer, or oligomer-oligomer — high molecular weight is achieved only late in the reaction, after nearly all functional groups have reacted.

**Requirement for Chain Extension**

Monomers must be at least **bifunctional** (possess two reactive functional groups) to form linear polymers; trifunctional or higher-functionality monomers introduce branching or cross-linking (network polymers).

**Representative Examples**

- **Polyester formation** (e.g., poly(ethylene terephthalate), PET):

$$n\,\text{HOOC–C}_6\text{H}_4\text{–COOH} + n\,\text{HO–CH}_2\text{CH}_2\text{–OH} \longrightarrow -[\text{OC–C}_6\text{H}_4\text{–CO–O–CH}_2\text{CH}_2\text{–O}]_n- + (2n-1)\,\text{H}_2\text{O}$$

- **Polyamide formation** (e.g., nylon-6,6, from a diacid and diamine):

$$n\,\text{HOOC–(CH}_2\text{)}_4\text{–COOH} + n\,\text{H}_2\text{N–(CH}_2\text{)}_6\text{–NH}_2 \longrightarrow -[\text{OC–(CH}_2\text{)}_4\text{–CO–NH–(CH}_2\text{)}_6\text{–NH}]_n- + (2n-1)\,\text{H}_2\text{O}$$

- **Polycarbonate and polyurethane** formation also proceed by step-growth mechanisms, the latter via addition of diols to diisocyanates without small-molecule elimination in the classic sense — [Inference: polyurethane synthesis is sometimes classified separately as "step-growth addition polymerization" because no byproduct is lost despite the stepwise, any-chain-length-reacts-with-any-chain-length kinetics; terminology varies by textbook].

**Carothers Equation**

For step-growth polymerization, the number-average degree of polymerization $\overline{X_n}$ relates to the extent of reaction $p$ (fraction of functional groups reacted) by:

$$\overline{X_n} = \frac{1}{1-p}$$

This shows that very high conversion is required for appreciable chain length: at $p = 0.99$, $\overline{X_n} = 100$; only as $p \to 1$ does $\overline{X_n}$ grow large. This is the key kinetic distinction from chain-growth systems, where high molecular weight appears almost immediately.

For non-stoichiometric monomer ratios (functional group ratio $r < 1$) or when a monofunctional chain stopper is included, the modified Carothers equation accounts for the limiting effect on maximum attainable chain length:

$$\overline{X_n} = \frac{1+r}{1+r-2rp}$$

**Key Points**

- A small molecule byproduct is typically eliminated at each bond-forming step.
- High molecular weight is reached only near complete conversion (p → 1).
- Reaction mixture contains a broad distribution of oligomer sizes throughout the reaction — dimers, trimers, and larger species react with each other progressively.
- Functionality of monomers (2 = linear chain; ≥3 = branched/network) governs polymer architecture.

### Comparative Summary

| Feature | Addition (Chain-Growth) | Condensation (Step-Growth) |
| --- | --- | --- |
| Byproduct | None (repeat unit = monomer) | Usually yes (e.g., H₂O, HCl, MeOH) |
| Reactive species | Radical, cation, anion, or coordination complex | Complementary functional groups (–OH, –COOH, –NH₂, –NCO, etc.) |
| Molecular weight vs. conversion | High MW achieved early, even at low conversion | High MW achieved only near complete conversion |
| Reaction mixture composition | Monomer + high-MW polymer + few active chains | Broad distribution of oligomers of increasing size |
| Typical monomers | Vinyl/unsaturated compounds, cyclic monomers | Bi- or polyfunctional monomers (diacids, diols, diamines, etc.) |
| Representative polymers | Polyethylene, polystyrene, PVC, PMMA, polypropylene | Polyesters (PET), polyamides (nylon), polycarbonates, polyurethanes, phenol-formaldehyde resins |
| Kinetics | Fast propagation, short polymer "birth-to-death" time per chain | Gradual buildup of chain length throughout the reaction |

### Molecular Weight Distributions

Both mechanisms produce a distribution of chain lengths rather than a single uniform molecular weight, characterized by:

$$\bar{M}_n = \frac{\sum N_i M_i}{\sum N_i} \quad \text{(number-average)}, \qquad \bar{M}_w = \frac{\sum N_i M_i^2}{\sum N_i M_i} \quad \text{(weight-average)}$$



$$Đ = \frac{\bar{M}_w}{\bar{M}_n} \quad \text{(dispersity / polydispersity index)}$$

Step-growth polymerization at high conversion approaches a "most probable" (Flory) distribution with $Đ \to 2$ as $p \to 1$. Conventional free-radical chain-growth polymerization typically gives $Đ$ in the range of 1.5–2.5 or higher depending on the relative contributions of transfer and termination, while living chain-growth methods can achieve $Đ$ close to 1.0. [Inference: exact dispersity values are strongly dependent on specific reaction conditions, termination mode, and reactor type, so these ranges should be treated as typical rather than absolute.]

### Worked Example

**Example**

A step-growth polyesterification reaches 98% conversion of functional groups ($p = 0.98$). Calculate the number-average degree of polymerization.

Using the Carothers equation:

$$\overline{X_n} = \frac{1}{1-p} = \frac{1}{1-0.98} = \frac{1}{0.02} = 50$$

On average, each polymer chain contains 50 repeat units at this conversion. To reach $\overline{X_n} = 200$, conversion would need to increase to $p = 0.995$ — illustrating why step-growth polymerizations must be driven to very high conversion (often via removal of the volatile byproduct, e.g., water, under vacuum or with entrainment) to obtain useful, high-molecular-weight material.

### Diagram: Chain-Growth vs. Step-Growth Molecular Weight Buildup

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 520 320">
<text x="90" y="20" font-size="14" font-weight="bold">MW vs. Conversion (svg_diagram)</text>
<line x1="60" y1="270" x2="480" y2="270" stroke="black" stroke-width="1.5" />
<line x1="60" y1="270" x2="60" y2="40" stroke="black" stroke-width="1.5" />
<text x="250" y="300" font-size="12">Conversion (p)</text>
<text x="15" y="160" font-size="12" transform="rotate(-90 15 160)">Molecular Weight</text>
<path d="M 60 265 L 90 60 L 480 55" stroke="blue" stroke-width="2" fill="none" />
<text x="330" y="45" font-size="11" fill="blue">Chain-growth (addition)</text>
<path d="M 60 270 C 200 268, 350 250, 420 150 C 450 110, 465 70, 475 50" stroke="red" stroke-width="2" fill="none" />
<text x="300" y="270" font-size="11" fill="red">Step-growth (condensation)</text>
<text x="470" y="285" font-size="11">1.0</text>
<text x="55" y="285" font-size="11">0</text>
</svg>

### Applications

- **Addition polymers**: packaging films and containers (PE, PP), pipes and siding (PVC), insulation and disposable products (PS), acrylic sheeting (PMMA), synthetic rubbers (polybutadiene, polyisoprene, butyl rubber).
- **Condensation polymers**: textile and bottle-grade PET fibers/resin, nylon fibers and engineering plastics, polycarbonate lenses and glazing, polyurethane foams and coatings, phenolic and melamine thermosetting resins, silicone polymers (via condensation of silanols).

### Common Pitfalls and Misconceptions

- Assuming all polymers with C=C-derived monomers are "addition" and all others are "condensation" — some ring-opening and certain step-growth-kinetics-but-no-byproduct systems (e.g., polyurethanes) blur this classification; the more rigorous distinction is chain-growth vs. step-growth kinetics rather than presence/absence of a byproduct alone.
- Confusing degree of polymerization with molecular weight directly — $\overline{X_n}$ must be multiplied by the repeat unit's molar mass to obtain $\bar{M}_n$.
- Expecting condensation polymerizations to reach high molecular weight quickly — because $\overline{X_n}$ depends on $\frac{1}{1-p}$, even small amounts of unreacted functional groups or stoichiometric imbalance dramatically cap the attainable chain length.
- Overlooking the role of monomer functionality: introducing even a small fraction of trifunctional monomer shifts a step-growth system from linear polymer toward gelation and network (thermoset) formation.

**Related Topics**

- Copolymerization (random, alternating, block, graft architectures)
- Controlled/living radical polymerization (ATRP, RAFT, NMP)
- Ring-opening polymerization (ROP) of cyclic monomers (lactones, lactams, epoxides)
- Cross-linking and thermosetting network polymers
- Polymer molecular weight characterization (GPC/SEC, light scattering)
- Stereoregularity and tacticity in vinyl polymers
- Biodegradable and biobased polymers (PLA, PHA)