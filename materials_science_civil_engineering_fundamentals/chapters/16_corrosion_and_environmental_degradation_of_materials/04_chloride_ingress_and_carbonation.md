## Chloride Ingress and Carbonation


### Overview

Chloride ingress and carbonation are the two dominant transport-and-reaction mechanisms responsible for depassivating steel reinforcement in concrete. While both ultimately trigger corrosion, they operate through fundamentally different transport physics, chemical reactions, and depassivation patterns. This entry focuses on the mass-transport, chemical, and predictive-modeling aspects of each mechanism, building on the corrosion consequences already established for reinforcement corrosion.

```mermaid
flowchart TD
    A[Aggressive Agent Exposure (svg_diagram)] --> B[Chloride Ingress: diffusion, absorption, migration]
    A --> C[Carbonation: CO2 gas diffusion and reaction]
    B --> D[Chloride threshold exceeded at rebar]
    C --> E[Carbonation front reaches rebar, pH drops]
    D --> F[Localized depassivation - pitting]
    E --> G[General depassivation - uniform corrosion]
```

### Transport Mechanisms in Concrete

Before addressing chloride and carbonation specifically, it is useful to distinguish the transport mechanisms by which aggressive agents move through the concrete pore network, since both processes are governed by combinations of these mechanisms depending on moisture state.

| Mechanism | Driving Force | Typical Zone of Dominance |
| --- | --- | --- |
| Diffusion | Concentration gradient | Saturated or near-saturated concrete (submerged, buried) |
| Capillary absorption (sorption) | Capillary suction into unsaturated pores | Surface zone subject to wetting-drying cycles (splash/tidal zones) |
| Permeation | Hydraulic pressure gradient | Structures under water pressure (retaining walls, tanks, tunnels) |
| Gas diffusion | Partial pressure gradient (for $\text{CO}_2$, $\text{O}_2$) | Unsaturated, partially dry concrete (atmospheric exposure) |

**Key Points**

- Chloride ingress is dominated by diffusion in saturated zones and capillary absorption in the near-surface unsaturated zone subject to wetting/drying
- Carbonation is fundamentally a gas diffusion process and therefore requires unsaturated pores containing air-filled voids through which $\text{CO}_2$ gas can move; fully saturated concrete essentially halts carbonation due to the much slower diffusion of dissolved $\text{CO}_2$ through water-filled pores
- The near-surface region of real structures typically experiences a superposition of multiple transport mechanisms, particularly in the tidal/splash and wetting-drying zones, making this region often the most vulnerable exposure category in codes

### Chloride Ingress

#### Sources of Chloride

- **External sources**: seawater/marine spray, deicing salts (sodium chloride, calcium chloride, magnesium chloride), soil chlorides in contact with foundations
- **Internal (built-in) sources**: chloride-contaminated mixing water, aggregates, or admixtures incorporated during construction — now generally controlled through material specification limits

#### Fick's Second Law Model

The standard simplified model treats chloride ingress as one-dimensional diffusion into a semi-infinite medium with constant surface concentration and constant diffusion coefficient:

$$\frac{\partial C}{\partial t} = D_c \frac{\partial^2 C}{\partial x^2}$$

With the closed-form solution:

$$C(x,t) = C_s \left[1 - \text{erf}\left(\frac{x}{2\sqrt{D_c t}}\right)\right]$$

Where:

- $C(x,t)$ = chloride concentration at depth $x$ and time $t$
- $C_s$ = surface chloride concentration (often assumed constant, though it typically builds up over an initial exposure period before stabilizing)
- $D_c$ = apparent (effective) chloride diffusion coefficient
- $\text{erf}$ = Gauss error function

**Refinements to the Basic Model**

[Inference] The constant-$D_c$, constant-$C_s$ assumptions of the basic Fickian model are simplifications; more refined approaches used in current durability engineering practice (such as the fib Model Code 2010 or DuraCrete methodology) commonly account for time-dependent decrease of the diffusion coefficient as continued cement hydration and pore refinement occur, expressed in forms such as:

$$D_c(t) = D_{c,ref} \left(\frac{t_{ref}}{t}\right)^{\alpha}$$

Where $D_{c,ref}$ is a reference diffusion coefficient at a reference time $t_{ref}$ (often 28 days), and $\alpha$ is an aging exponent dependent on binder type (higher for concretes with supplementary cementitious materials such as fly ash or slag, reflecting their continued pore-refining hydration).

#### Chloride Threshold Concept

The **critical chloride threshold** ($C_{crit}$) is the chloride concentration at the rebar surface (commonly expressed as total or acid/water-soluble chloride content relative to cement mass, or as a chloride-to-hydroxide molar ratio) above which passive film breakdown becomes likely.

**Key Points**

- Commonly cited ranges are approximately 0.2–0.4% chloride by mass of cement for water-soluble chloride content, though [Unverified] specific numeric thresholds vary substantially by source, cement type, and test method, and design codes specify their own applicable limits that should be used in place of generic literature values
- Threshold values are influenced by cement type (blended cements with fly ash, slag, or silica fume generally exhibit different threshold behavior than plain portland cement), degree of carbonation (carbonation can free bound chlorides back into the pore solution, effectively lowering the practical threshold), and moisture/oxygen availability at the rebar
- Some chlorides become chemically bound within the cement hydration products (forming Friedel's salt, $\text{3CaO·Al}_2\text{O}_3\text{·CaCl}_2\text{·10H}_2\text{O}$) or physically adsorbed onto pore surfaces, reducing the free chloride concentration available to attack the passive film; binding capacity depends strongly on aluminate ($\text{C}_3\text{A}$) content of the cement

#### Chloride Migration Testing

Rapid laboratory assessment of chloride resistance commonly uses **migration tests** (applying an external electric field to accelerate chloride movement through a specimen), such as the Rapid Chloride Migration (RCM) test or the Rapid Chloride Permeability Test (RCPT, measuring charge passed, e.g., per ASTM C1202). [Inference] RCPT charge-passed results correlate with chloride permeability in a general sense but can be influenced by pore solution conductivity independent of actual chloride diffusivity (particularly for concretes containing certain supplementary cementitious materials or conductive admixtures), so results are generally interpreted alongside other durability indicators rather than in isolation.

### Carbonation

#### Chemical Mechanism

Atmospheric carbon dioxide gas diffuses into the unsaturated pore network of concrete, dissolves into the pore water film to form carbonic acid, and reacts with the alkaline hydration products:

$$\text{CO}_2 + \text{H}_2\text{O} \rightarrow \text{H}_2\text{CO}_3$$



$$\text{Ca(OH)}_2 + \text{H}_2\text{CO}_3 \rightarrow \text{CaCO}_3 + 2\text{H}_2\text{O}$$

Calcium silicate hydrate (C-S-H) and other hydration products also carbonate at a slower rate once free calcium hydroxide is substantially consumed, releasing additional calcium for carbonate formation but further reducing the pore solution's buffering alkalinity.

**Consequence**: pore solution pH drops from approximately 12.5–13.5 in sound concrete to below approximately 9 in fully carbonated concrete, a level insufficient to maintain the stability of the iron passive film.

#### Carbonation Depth Prediction

The most widely used simplified predictive relationship is:

$$x_c = k\sqrt{t}$$

Where $x_c$ is carbonation depth, $t$ is exposure time, and $k$ is an empirical carbonation coefficient combining material and environmental effects. More detailed models express $k$ as a function of:

$$k = f(w/c \text{ ratio}, \text{cement type}, \text{curing}, \text{RH}, \text{CO}_2 \text{ concentration}, \text{cover quality})$$

**Key Points**

- Carbonation rate increases with higher water-cement ratio (coarser, more interconnected pore structure allows easier gas diffusion)
- Carbonation rate is maximized at intermediate relative humidity, commonly cited around 50–70% RH; below this range insufficient pore water limits the carbonic acid reaction, while above this range water-filled pores impede \text{CO}_2}
   gas diffusion
- Indoor, sheltered concrete elements (protected from direct rain but exposed to normal indoor humidity and atmospheric $\text{CO}_2$) are often at elevated carbonation risk precisely because indoor RH frequently sits within this most-aggressive intermediate range
- Adequate curing duration significantly reduces near-surface permeability and therefore the carbonation coefficient $k$, since early-age moisture loss before sufficient hydration leaves a more porous, carbonation-susceptible cover zone
- Supplementary cementitious materials (fly ash, slag) can reduce permeability (lowering $k$) but also reduce the calcium hydroxide reserve available to buffer against carbonation ingress, so the net effect on carbonation resistance depends on replacement level, curing, and mix proportioning

#### Carbonation Depth Field Testing

The standard field/laboratory test applies a phenolphthalein indicator solution to a freshly exposed (broken or cored) concrete surface:

- **Pink/magenta color** — indicates pH above approximately 9–9.5 (uncarbonated, still-alkaline concrete)
- **No color change (colorless)** — indicates pH below the phenolphthalein transition range (carbonated concrete)

The measured colorless depth from the exposed surface is taken as the carbonation depth at that location and time, commonly used together with the square-root-of-time model to extrapolate future carbonation front progression and estimate remaining initiation-period service life.

### Interaction Between Chloride Ingress and Carbonation

Although presented separately, the two mechanisms interact in ways relevant to combined-exposure structures (e.g., coastal urban infrastructure exposed to both marine chlorides and atmospheric/urban $\text{CO}_2$):

- Carbonation reduces pore solution pH and consumes calcium hydroxide, which can **release previously chemically bound chlorides** (from Friedel's salt) back into free solution, effectively lowering the practical chloride threshold in carbonated zones
- Carbonation may **densify surface porosity** slightly due to calcium carbonate precipitation, in some cases marginally reducing near-surface permeability, though [Inference] this densification effect is generally considered secondary compared to the depassivation risk introduced by pH reduction and chloride release, and should not be relied upon as a net protective effect
- Combined carbonation-chloride exposure is frequently associated with accelerated depassivation timelines compared to either mechanism acting alone, though the degree of acceleration is structure- and mix-specific

### Comparative Summary

| Aspect | Chloride Ingress | Carbonation |
| --- | --- | --- |
| Transport mechanism | Diffusion (saturated), capillary absorption (unsaturated near-surface) | Gas diffusion (requires unsaturated, air-filled pores) |
| Governing model | Fick's second law (with time-dependent $D_c$ refinements) | Square-root-of-time ($x_c = k\sqrt{t}$) |
| Depassivation pattern | Localized (pitting-type) | General/uniform along carbonated depth |
| Key material property | Chloride diffusion coefficient, binding capacity | Permeability, calcium hydroxide reserve |
| Worst-case exposure zone | Tidal/splash zone, deicing salt splash zone | Sheltered, intermediate-humidity atmospheric exposure |
| Field test | Chloride profiling and titration | Phenolphthalein indicator spray test |
| Primary mitigation | Low permeability mix, adequate cover, corrosion-resistant reinforcement | Low water-cement ratio, adequate curing, adequate cover |

### Design and Mitigation Implications

**Example:**

A coastal parking structure exposed to both deicing salts (chloride ingress) and normal atmospheric $\text{CO}_2$ under a partially sheltered garage environment (favorable for carbonation) is a common real-world combined-exposure case. Effective design response typically involves specifying a low water-cement ratio mix incorporating supplementary cementitious materials for reduced chloride diffusivity, adequate curing to minimize near-surface carbonation susceptibility, sufficient cover per the governing exposure classification, and consideration of corrosion-resistant reinforcement or inhibitors in the most severe splash/spray zones.

**Design Standards Reference**

Most modern durability design codes (ACI 318 exposure categories, Eurocode 2 exposure classes per EN 206, fib Model Code for service life design) specify minimum cover, maximum water-cement ratio, and minimum compressive strength/cementitious content requirements differentiated by exposure category (e.g., separate classes for carbonation-induced and chloride-induced corrosion risk, often further subdivided by exposure severity such as splash/tidal/atmospheric marine zones).

### Common Misconceptions

- Higher humidity is **not** always worse for carbonation; fully saturated concrete actually slows carbonation due to restricted gas diffusion, with intermediate humidity being most aggressive.
- A low water-cement ratio mix that resists chloride ingress well does **not** automatically guarantee equivalent carbonation resistance improvement, though the two properties are often correlated through overall permeability reduction; specific mix design verification for both mechanisms is generally warranted for combined-exposure structures.
- Carbonation is **not** an instantaneous surface phenomenon; it progresses as a moving front over years to decades, and its depth must be measured relative to actual concrete cover at the time of assessment, not assumed as a fixed condition.
- Supplementary cementitious materials do **not** universally improve durability performance for both mechanisms simultaneously; some replacement levels that improve chloride resistance may increase carbonation susceptibility due to reduced calcium hydroxide reserve, requiring balanced mix design consideration.

### Related Topics

- Corrosion of Reinforcing Steel in Concrete
- Electrochemical Principles of Corrosion
- Fick's Law Diffusion Modeling and Service Life Prediction Methods (fib Model Code, DuraCrete)
- Concrete Permeability and Pore Structure (Water-Cement Ratio, Supplementary Cementitious Materials)
- Curing Practices and Their Effect on Durability
- Durability Design and Exposure Classification (ACI 318, Eurocode 2 / EN 206)
- Chloride Binding Capacity and Friedel's Salt Formation
- Non-Destructive and Semi-Destructive Testing for Chloride and Carbonation Assessment
- Corrosion Inhibitors and Their Effect on Chloride Threshold