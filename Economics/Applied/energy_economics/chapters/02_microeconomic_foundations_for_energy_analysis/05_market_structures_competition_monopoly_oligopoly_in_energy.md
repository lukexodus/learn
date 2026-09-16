## Market Structures: Competition, Monopoly, Oligopoly in Energy


### Conceptual Foundation

Market structure analysis classifies industries by the number and size distribution of firms, barriers to entry, and product homogeneity, each producing distinct predictions for price, output, and welfare outcomes. Energy industries span nearly the entire spectrum of market structures — from competitive spot commodity markets to regulated natural monopolies to cartelized resource extraction — often within the same value chain (e.g., competitive upstream production, monopolistic pipeline transport, oligopolistic refining, competitive retail).

### The Market Structure Spectrum

| Structure | Number of Firms | Entry Barriers | Price-Setting Power | Typical Energy Example |
| --- | --- | --- | --- | --- |
| Perfect Competition | Many | Low/none | Price-taker | Spot coal markets, competitive retail electricity/gas |
| Monopolistic Competition | Many | Low | Some (differentiation) | Retail energy branding/service differentiation |
| Oligopoly | Few | High | Significant, interdependent | Refining, LNG liquefaction, large power generators |
| Cartel | Few (coordinated) | High | Coordinated market power | OPEC / OPEC+ |
| Natural Monopoly | One | Very high (economies of scale) | Full (absent regulation) | Transmission/distribution networks, pipelines |

### Perfect Competition in Energy Markets

#### Conditions and Applicability

Perfect competition requires: many small price-taking firms, homogeneous product, free entry/exit, and perfect information. Segments of energy markets approximate this reasonably well:

- **Spot commodity markets** (crude oil benchmarks like WTI/Brent, thermal coal, LNG spot cargoes) with many buyers and sellers and standardized product grades.
- **Competitive retail electricity/gas markets** in liberalized jurisdictions with restructured, unbundled generation/retail segments.

#### Equilibrium Condition

$$P = MC = MR$$

Firms are price-takers; profit maximization simply requires producing where marginal cost equals the (exogenously given) market price. Long-run competitive equilibrium drives economic profit to zero as entry continues until $P = LRAC_{min}$.

**Key Points**

- This is the reference benchmark against which market power in other energy segments is measured (e.g., via the Lerner Index, $L = (P-MC)/P$, discussed further below).
- Even markets often described as "competitive" (e.g., global crude oil) exhibit meaningful deviations due to OPEC+ coordination, making the pure competitive model an idealized baseline rather than a literal description.

### Monopoly in Energy: Natural Monopoly and Network Industries

#### Why Natural Monopoly Arises

A natural monopoly exists when a single firm can supply the entire relevant market at lower average cost than two or more firms could achieve, due to persistent economies of scale relative to market demand:

$$LRAC(Q) \text{ declining over the relevant output range}$$

This condition applies strongly to:

- **Electricity transmission and distribution networks**: duplicating parallel wire/pole infrastructure is highly wasteful: massive fixed sunk cost (right-of-way, conductors, substations) spread over throughput.
- **Natural gas pipelines and local distribution networks**: similar physical/economic logic — a single pipeline network serving a corridor is typically more efficient than parallel competing pipelines.
- **LNG regasification terminals and, in some contexts, liquefaction trains**: high capital intensity relative to regional demand can support only one or a few efficient-scale facilities.

#### Unregulated Monopoly Outcome

Absent regulation, a profit-maximizing monopolist sets output where marginal revenue equals marginal cost, rather than where price equals marginal cost:

$$MR(Q^M) = MC(Q^M), \quad P^M > MC(Q^M)$$

Producing $Q^M < Q^{competitive}$ and $P^M > P^{competitive}$, generating a deadweight loss triangle relative to the competitive/efficient benchmark.

monopoly_deadweight_loss_diagram (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 440" font-family="Helvetica, Arial, sans-serif">
<rect x="0" y="0" width="700" height="440" fill="#ffffff" />
<text x="350" y="28" text-anchor="middle" font-size="18" font-weight="bold" fill="#1a1a1a">Unregulated Natural Monopoly Outcome (svg_diagram)</text>
<line x1="90" y1="380" x2="640" y2="380" stroke="#333" stroke-width="2" />
<line x1="90" y1="380" x2="90" y2="50" stroke="#333" stroke-width="2" />
<text x="645" y="385" font-size="13" fill="#333">Quantity</text>
<text x="45" y="55" font-size="13" fill="#333">Price</text>

<path d="M 150 90 L 580 370" stroke="#1f6feb" stroke-width="2.5" fill="none" />
<text x="500" y="355" font-size="12" fill="#1f6feb" font-weight="bold">Demand</text>

<path d="M 150 90 L 365 370" stroke="#8250df" stroke-width="2.5" fill="none" stroke-dasharray="6,4" />
<text x="370" y="365" font-size="12" fill="#8250df" font-weight="bold">MR</text>

<line x1="120" y1="280" x2="620" y2="280" stroke="#2ea043" stroke-width="2.5" />
<text x="560" y="272" font-size="12" fill="#2ea043" font-weight="bold">MC = AC</text>

<circle cx="300" cy="280" r="5" fill="#111" />
<line x1="300" y1="280" x2="300" y2="380" stroke="#888" stroke-width="1" stroke-dasharray="3,3" />
<line x1="300" y1="280" x2="90" y2="280" stroke="#888" stroke-width="1" stroke-dasharray="3,3" />

<circle cx="300" cy="205" r="5" fill="#d1242f" />
<line x1="300" y1="205" x2="90" y2="205" stroke="#d1242f" stroke-width="1" stroke-dasharray="3,3" />
<text x="35" y="209" font-size="11" fill="#d1242f">P_M</text>
<text x="35" y="284" font-size="11" fill="#333">MC</text>
<text x="305" y="398" font-size="11" fill="#333">Q_M</text>

<path d="M 300 280 L 300 205 L 460 280 Z" fill="#f0b429" fill-opacity="0.4" stroke="#f0b429" stroke-width="1.5" />
<text x="330" y="255" font-size="11" fill="#7d5a00">DWL</text>

<text x="100" y="415" font-size="12" fill="#555">Unregulated monopolist restricts output to Q_M (where MR=MC), charging P_M &gt; MC, creating deadweight loss.</text>

</svg>

#### Regulatory Responses

Because unregulated natural monopoly produces this welfare loss, network energy segments are typically subject to economic regulation:

- **Rate-of-return (cost-of-service) regulation**: regulator sets allowed revenue to cover operating costs plus a permitted return on regulatory asset base (RAB): $Revenue_{allowed} = OpEx + (RAB \times WACC) + Depreciation$.
- **Price-cap (incentive) regulation**: regulator sets a price ceiling that adjusts over time by a formula such as $RPI - X$ (retail price index growth minus an efficiency factor $X$), intended to incentivize cost efficiency since the firm retains cost savings between price reviews.
- **Yardstick competition**: regulator benchmarks a network firm's costs against comparable firms in other regions, reducing information asymmetry between regulator and regulated firm.

**Key Points**

- Rate-of-return regulation is documented in the literature as potentially inducing the **Averch-Johnson effect**: an incentive toward capital over-investment (gold-plating) if the allowed rate of return exceeds the true cost of capital, since the firm earns a return on a larger asset base. [Inference: the theoretical mechanism is well established; the empirical magnitude of this distortion in specific modern regulatory regimes is disputed and regime-dependent.]
- Price-cap regulation shifts risk toward the regulated firm (cost overruns are not automatically passed through) but can create incentives to under-invest in quality/reliability if not paired with explicit service-quality standards.

### Oligopoly in Energy Markets

#### Characteristics

Oligopoly describes markets with a small number of large firms whose strategic decisions are mutually interdependent — each firm's optimal choice depends on rivals' expected responses. This describes several important energy segments:

- **Refining**: concentrated in many regional markets due to high capital costs and economies of scale in refinery construction.
- **LNG liquefaction and long-term supply contracting**: a relatively small number of large integrated players (national oil companies, supermajors) dominate global capacity.
- **Large-scale power generation** in many national/regional wholesale electricity markets, where a handful of firms may own a large share of dispatchable capacity.

#### Cournot (Quantity) Competition

Firms choose output levels simultaneously, each taking rivals' output as given. For $n$ symmetric firms facing linear demand $P = a - bQ$ (where $Q = \sum q_i$), the Cournot-Nash equilibrium price approaches the competitive price as $n \to \infty$ and approaches the monopoly price as $n \to 1$:

$$P^{Cournot} = \frac{a + n \cdot MC}{n+1}$$

**Key Points**

- The Cournot model is widely used in electricity market power analysis because generation capacity decisions function similarly to quantity commitments over short operational horizons.
- Market concentration under Cournot competition is commonly summarized via the **Herfindahl-Hirschman Index (HHI)**: $HHI = \sum_i s_i^2 \times 10{,}000$ (where $s_i$ is firm $i$'s market share), with regulators in many jurisdictions treating HHI thresholds (e.g., above 2,500 commonly flagged as "highly concentrated" in various merger guideline frameworks) as screening criteria for market power concern. [Inference: specific numeric thresholds and their regulatory application vary by jurisdiction and have been revised over time; treat cited figures as illustrative of the general approach rather than a universal fixed rule.]

#### Bertrand (Price) Competition

Firms compete on price rather than quantity; with homogeneous products and no capacity constraints, even two-firm Bertrand competition can drive price down to marginal cost (the "Bertrand paradox"), since either firm can capture the entire market by undercutting the rival marginally.

**Key Points**

- Pure Bertrand outcomes are rarely observed in energy markets because capacity constraints are usually binding (a generator or refiner cannot serve unlimited demand at a given price), leading to **Bertrand-Edgeworth** models where price competition is tempered by capacity limits, often producing outcomes between the pure Bertrand (competitive) and Cournot (more concentrated) predictions.
- Electricity wholesale markets are frequently modeled with **supply function equilibrium (SFE)** approaches, an extension recognizing that generators submit entire bid curves (price-quantity pairs) rather than a single price or quantity, better reflecting actual market/auction design in most liberalized electricity markets.

#### Strategic Interdependence and Withholding

In concentrated wholesale electricity markets, generators with market power can exercise it through:

- **Economic withholding**: bidding capacity at a price above true marginal cost, effectively removing low-cost capacity from the merit order to raise the market clearing price.
- **Physical withholding**: declaring a unit unavailable (e.g., for "maintenance") to reduce available supply and raise price, distinct from and generally more difficult to detect/prove than economic withholding.

**Key Points**

- Market monitors in most organized wholesale electricity markets (independent system operators/regional transmission organizations) conduct routine screens for these behaviors, often using conduct-and-impact tests examining both the bidding pattern and its price effect. [Inference: specific screening methodologies and enforcement mechanisms are market/jurisdiction-specific and evolve over time.]

### Cartel Behavior: OPEC and OPEC+

#### Cartel Theory Basics

A cartel is a group of otherwise-independent producers who coordinate output/price decisions to jointly emulate monopoly outcomes and increase aggregate profit above the competitive level. OPEC (Organization of the Petroleum Exporting Countries) and the broader OPEC+ coalition represent the most prominent real-world cartel example in energy economics.

$$\max_{\{q_i\}} \sum_i \pi_i \quad \text{s.t. joint output constraint}$$

**Key Points**

- Cartels face an inherent **stability problem**: each individual member has a unilateral incentive to cheat (produce beyond its allocated quota) since the marginal member captures the full benefit of extra output while bearing only a fraction of the resulting price decline (borne collectively). This is a standard prisoner's-dilemma-like structure in cartel theory.
- OPEC+ compliance with announced production quotas has varied considerably over time and across member states; monitoring, enforcement, and spare-capacity dynamics are central features of the applied literature analyzing cartel durability. [Inference: general characterization consistent with the cartel-stability literature; the state of compliance at any given time requires current reporting rather than a fixed inference. Recommend a targeted search for latest OPEC+ production and compliance data if a current assessment is needed.]
- Cartel effectiveness depends on factors including: the elasticity of non-cartel ("fringe") supply, demand elasticity (as discussed in the elasticity chapter), and the availability of spare capacity among core members to enforce discipline or respond to demand shocks.

#### Dominant Firm / Competitive Fringe Model

A commonly used applied framework treats OPEC (or a subset of "swing producers") as a dominant firm facing a competitive fringe of smaller non-cartel producers:

$$Q_{fringe} = S_{fringe}(P), \quad Q_{dominant} = Q_{demand}(P) - Q_{fringe}(P)$$

The dominant firm sets output/price accounting for the residual demand curve remaining after fringe supply response, rather than facing total market demand directly.

**Key Points**

- This framework explains why growth in non-OPEC supply (e.g., U.S. shale production growth over the 2010s) is commonly analyzed in the literature as eroding OPEC's effective market power by expanding the competitive fringe and flattening the residual demand curve facing the cartel. [Inference: qualitative direction well supported in the literature; precise quantitative erosion of market power is an ongoing empirical question requiring current data.]

### Market Structure Across the Energy Value Chain

```mermaid
flowchart LR
    A["Upstream Extraction"] -->|"Cartel / Oligopoly<br/>(OPEC+, Majors)"| B["Midstream Transport"]
    B -->|"Natural Monopoly<br/>(Pipelines, Terminals)"| C["Processing/Refining"]
    C -->|"Oligopoly<br/>(Concentrated Refiners)"| D["Wholesale Distribution"]
    D -->|"Oligopoly/Competitive<br/>(Generators, Traders)"| E["Retail Supply"]
    E -->|"Monopolistic Competition<br/>(Branded Retailers)<br/>or Regulated Monopoly<br/>(Utility Service Territory)"| F["End Consumer"]
```

**Key Points**

- A single energy value chain frequently spans multiple market structures simultaneously — this segmentation (rather than a single characterization of "the energy market") is essential for accurate competition-policy and regulatory analysis.
- Vertical relationships between segments (e.g., an integrated firm operating both competitive generation and monopoly transmission) raise distinct **vertical market power** concerns, including the potential to leverage monopoly control of a network bottleneck to disadvantage rivals in an adjacent competitive segment — a central issue in electricity/gas market restructuring and unbundling policy.

### Measuring and Comparing Market Power: Summary Table

| Metric | Formula | Interpretation |
| --- | --- | --- |
| Lerner Index | $L = (P-MC)/P = -1/E_d$ | Price-cost margin; 0 under perfect competition |
| HHI | $\sum_i s_i^2 \times 10{,}000$ | Market concentration; higher values indicate more concentrated structure |
| Residual Demand Elasticity | Elasticity of demand net of fringe supply response | Basis for dominant-firm/fringe modeling (e.g., OPEC) |
| Conduct-and-Impact Test | Bid price vs. cost + price impact threshold | Used in electricity market monitoring for withholding detection |

### Applied Example: Comparing Structures with a Common Demand Curve

**Example**

Given market demand $P = 100 - Q$ and constant marginal cost $MC = 20$ across all firms:

**Perfect competition:** $P = MC \Rightarrow 100 - Q = 20 \Rightarrow Q^{PC} = 80$, $P^{PC} = 20$

**Monopoly:** $MR = 100 - 2Q$; set $MR = MC \Rightarrow 100-2Q=20 \Rightarrow Q^M = 40$, $P^M = 60$

**Cournot duopoly ($n=2$):** Using $P^{Cournot} = \frac{a+n \cdot MC}{n+1} = \frac{100 + 2(20)}{3} = \frac{140}{3} \approx 46.7$; total output $Q^{Cournot} = 100 - 46.7 = 53.3$

**Output**

- Competitive outcome: highest output (80), lowest price (20) — efficient benchmark.
- Monopoly outcome: lowest output (40), highest price (60) — largest welfare loss.
- Cournot duopoly: intermediate outcome (Q≈53.3, P≈46.7) — illustrating how market structure between the two extremes produces intermediate price/output/welfare results, consistent with the general prediction that outcomes converge toward competitive levels as the number of independent competing firms increases. [Note: illustrative numeric example with simplified linear demand/constant MC assumptions, not calibrated to any specific real-world energy market.]

### Common Pitfalls in Market Structure Analysis

- Treating "the energy market" as a single homogeneous structure, when in practice different segments of the same value chain exhibit fundamentally different competitive conditions requiring distinct analytical frameworks.
- Applying the pure Bertrand (price-equals-marginal-cost) prediction to capacity-constrained energy markets without the Bertrand-Edgeworth capacity adjustment, which can materially understate sustainable price-cost margins.
- Assuming static cartel behavior/compliance levels without verifying current conditions, since OPEC+ quota agreements, membership, and compliance evolve over time and require up-to-date data for any current assessment.
- Overlooking vertical market power concerns when a firm operates across both competitive and natural-monopoly segments of the value chain, which can require different regulatory remedies (structural or functional unbundling) than horizontal concentration alone.
- Assuming rate-of-return regulation and price-cap regulation produce identical investment incentives; the two frameworks create materially different capital-investment and cost-control incentives that should be modeled distinctly. Behavior under either规 regime may vary by jurisdiction-specific implementation details. [Inference]

### **Related Topics**

- Rate-of-return vs. price-cap regulation and the Averch-Johnson effect
- Cournot, Bertrand-Edgeworth, and supply function equilibrium models in electricity markets
- OPEC+ dominant-firm/competitive-fringe modeling and cartel stability theory
- Herfindahl-Hirschman Index and merger analysis in energy sector competition policy
- Vertical market power and unbundling policy in electricity/gas restructuring
- Economic and physical withholding detection in wholesale electricity market monitoring
- Learning curves and technological disruption of cartel/oligopoly market power (shale supply growth)
- Yardstick competition and benchmarking regulation for natural monopoly networks