## Guaranteed Service Model for Multi-Echelon Safety Stock

### Overview

The Guaranteed Service Model (GSM) is an analytical framework for setting safety stock across a multi-echelon supply chain (network of stages — suppliers, plants, distribution centers, retailers) so that each stage guarantees a bounded replenishment time to its downstream customer, regardless of upstream demand variability. It was formalized by Simpson (1958) and extended by Graves and Willems (2000) into the widely used "stochastic-service guaranteed-service" (SSGS) model implemented in commercial supply chain design tools (e.g., Llamasoft/Coupa, Kinaxis).

The core idea: instead of computing safety stock independently per node (which double-counts or under-counts risk pooling across echelons), GSM propagates a **guaranteed service time** contractually between stages, and computes each node's safety stock from its **net replenishment time** — the portion of its lead time not already covered by service from its supplier.

### Key Points

- Each stage $j$ quotes an outbound **service time** $S_j$ (days) — the maximum time after order placement it guarantees delivery to its customer, even under demand surges.
- Each stage has an inbound service time $SI_j$, received from its immediate predecessors: $SI_j = \max_i(S_i)$ over all supplying stages $i$.
- Each stage has a deterministic **processing/production lead time** $T_j$.
- The **net replenishment time (NRT)** covered by safety stock at stage $j$ is:

$$NRT_j = SI_j + T_j - S_j$$

- Safety stock at stage $j$ is sized to cover demand uncertainty during $NRT_j$, not the full lead time — this is the mechanism by which upstream stock is "leveraged" to reduce downstream stock requirements.
- $S_j$ is a decision variable (0 ≤ $S_j$ ≤ $SI_j + T_j$) chosen by an optimization to minimize total holding cost network-wide while meeting a target customer-facing service time at end nodes.

### Assumptions

- **Bounded demand**: demand at each stage during any period is bounded (commonly modeled with a guaranteed maximum, e.g., mean plus $z$ standard deviations), not literally infinite-tailed — this is what allows "guaranteed" (as opposed to probabilistic) coverage.
- Demand is stationary or piecewise-stationary over the planning horizon; period demand mean $\mu_j$ and standard deviation $\sigma_j$ are known per stage.
- The supply chain is modeled as a directed acyclic graph (DAG) — each stage has one or more predecessors and successors; assembly and distribution structures are both supported.
- Processing times $T_j$ are deterministic (a known constant), though extensions exist for stochastic lead times.
- Each stage operates a periodic-review, base-stock (order-up-to) replenishment policy.
- 100% guaranteed coverage within $NRT_j$ is not literally assumed; rather, a service level $z_j$ (via a normal approximation) determines the safety factor, making this a **stochastic-service** variant of the original deterministic GSM.

### Safety Stock Formula

For stage $j$ with net replenishment time $NRT_j$, demand standard deviation $\sigma_j$ over one period, and target cycle service level corresponding to safety factor $z_j$:

$$SS_j = z_j \cdot \sigma_j \cdot \sqrt{NRT_j}$$

Base-stock level:

$$B_j = \mu_j \cdot (NRT_j) + SS_j$$

Where $\mu_j$ is average period demand at stage $j$ (which itself may be derived bottom-up from downstream demand in assembly/BOM structures).

**Key Points**

- $\sqrt{NRT_j}$ reflects the standard square-root-of-time scaling under the assumption of i.i.d. period demand.
- If $NRT_j = 0$ (stage fully covered by supplier's service time plus its own processing adds nothing net), $SS_j = 0$ — the stage carries no safety stock and relies entirely on guaranteed upstream/production coverage.
- Because $S_j$ is optimized jointly across the network, the model naturally identifies **strategic stock-holding points** — nodes where it is cost-effective to decouple variability (often called "risk pooling points" or the placement of decoupling buffers).

### Network Optimization Problem

The overarching problem is to choose $S_j$ for every stage $j$ to minimize total safety stock holding cost:

$$\min \sum_j h_j \cdot z_j \cdot \sigma_j \cdot \sqrt{SI_j + T_j - S_j}$$

subject to:

- $0 \le S_j \le SI_j + T_j$ for all $j$
- $SI_j = \max_{i \in \text{pred}(j)} S_i$
- Demand-facing (customer-facing) stages must satisfy a maximum promised service time $S_j \le S_j^{max}$

Where $h_j$ is the holding cost per unit at stage $j$ (often echelon holding cost — incremental value added at that stage, not full product cost).

**Solution approaches:**

- **Dynamic programming** on spanning trees (original Graves-Willems approach) — exact for tree-structured (non-converging) networks, exploits the separable, piecewise-concave structure of the square-root cost function.
- **Mixed-integer / piecewise-linear approximation**: because $\sqrt{x}$ is concave, it's linearized via tangent-line or secant approximations to embed in an MILP solver for general DAGs (including assembly points with multiple predecessors).
- Heuristic/iterative improvement algorithms for large-scale industrial networks (thousands of SKU-location combinations) where exact DP is computationally prohibitive.

### Worked Example

Consider a 3-stage serial chain: Supplier → Plant → Distribution Center (DC) → Customer.

| Stage | $T_j$ (days) | $\sigma_j$ (units/day) | $z_j$ |
| --- | --- | --- | --- |
| Supplier | 5 | 20 | 1.65 |
| Plant | 3 | 20 | 1.65 |
| DC | 2 | 20 | 1.65 |

Suppose the optimization determines:

- Supplier quotes $S_{sup} = 3$ (holds stock to guarantee 3-day service despite a 5-day production lead)
- Plant quotes $S_{plant} = 2$
- DC must guarantee $S_{DC} = 0$ (immediate/next-day fulfillment to customer)

**Net replenishment times:**

- Supplier: $NRT = 0 + 5 - 3 = 2$ days
- Plant: $NRT = 3 + 3 - 2 = 4$ days ($SI_{plant} = S_{sup} = 3$)
- DC: $NRT = 2 + 2 - 0 = 4$ days ($SI_{DC} = S_{plant} = 2$)

**Safety stock:**

- Supplier: $SS = 1.65 \times 20 \times \sqrt{2} \approx 46.7$ units
- Plant: $SS = 1.65 \times 20 \times \sqrt{4} = 66.0$ units
- DC: $SS = 1.65 \times 20 \times \sqrt{4} = 66.0$ units

Total network safety stock ≈ 178.7 units — compare against the naive "each stage covers its full lead time independently" case ($NRT_j = T_j$ everywhere), which would give $SS_{sup}=1.65 \cdot 20 \cdot \sqrt5\approx73.8$, $SS_{plant}=1.65\cdot20\cdot\sqrt3\approx57.2$, $SS_{DC}=1.65\cdot20\cdot\sqrt2\approx46.7$ — total ≈ 177.7, illustrating that the benefit of GSM comes primarily from *where* the optimizer places service times relative to structure, not a guaranteed universal reduction; the gain is typically much larger in networks with convergent/assembly structures or shared components across products.

### Guaranteed Service Model vs. Stochastic-Service Model

| Aspect | GSM | Pure Stochastic (e.g., METRIC-type) |
| --- | --- | --- |
| Demand bound | Bounded/guaranteed within service time | Probabilistic, potentially unbounded stockout risk |
| Coupling between stages | Explicit contractual service times | Implicit via fill-rate/backorder propagation |
| Tractability at scale | Efficient (DP/MILP on tree structures) | Often requires simulation or complex recursive approximations |
| Typical use | Strategic network design, tactical safety stock setting | Spare parts (repairable inventory), field service networks |
| Software | SAP IBP, Kinaxis, LLamasoft, o9 | SIMUL8, custom simulation, some APS spare-parts modules |

### Network Topology (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 760 260">
<text x="380" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Guaranteed Service Model — Serial Chain (svg_diagram)</text>
<rect x="40" y="90" width="140" height="70" rx="8" fill="#dbeafe" stroke="#1d4ed8" stroke-width="2" />
<text x="110" y="118" text-anchor="middle" font-size="13" font-weight="bold">Supplier</text>
<text x="110" y="136" text-anchor="middle" font-size="11">T=5, S=3</text>
<text x="110" y="152" text-anchor="middle" font-size="11">NRT=2, SS≈46.7</text>
<rect x="300" y="90" width="140" height="70" rx="8" fill="#dcfce7" stroke="#15803d" stroke-width="2" />
<text x="370" y="118" text-anchor="middle" font-size="13" font-weight="bold">Plant</text>
<text x="370" y="136" text-anchor="middle" font-size="11">T=3, S=2</text>
<text x="370" y="152" text-anchor="middle" font-size="11">NRT=4, SS≈66.0</text>
<rect x="560" y="90" width="140" height="70" rx="8" fill="#fef9c3" stroke="#a16207" stroke-width="2" />
<text x="630" y="118" text-anchor="middle" font-size="13" font-weight="bold">DC</text>
<text x="630" y="136" text-anchor="middle" font-size="11">T=2, S=0</text>
<text x="630" y="152" text-anchor="middle" font-size="11">NRT=4, SS≈66.0</text>
<line x1="180" y1="125" x2="298" y2="125" stroke="#333" stroke-width="2" marker-end="url(#arrow)" />
<text x="239" y="115" text-anchor="middle" font-size="11">S=3 days</text>
<line x1="440" y1="125" x2="558" y2="125" stroke="#333" stroke-width="2" marker-end="url(#arrow)" />
<text x="499" y="115" text-anchor="middle" font-size="11">S=2 days</text>
<line x1="700" y1="125" x2="750" y2="125" stroke="#333" stroke-width="2" marker-end="url(#arrow)" />
<text x="725" y="105" text-anchor="middle" font-size="10">S=0</text>
<text x="725" y="145" text-anchor="middle" font-size="10">Customer</text>
<text x="380" y="220" text-anchor="middle" font-size="11" fill="#555">Safety stock sized on NRT = SI + T − S, not on full lead time T alone</text>

</svg>

### Algorithmic Flow

```mermaid
flowchart TD
    A[Model supply chain as DAG: stages, T_j, sigma_j, holding cost h_j] --> B[Define candidate service times S_j per stage]
    B --> C{Tree-structured network?}
    C -->|Yes| D[Exact Dynamic Programming over spanning tree]
    C -->|No, converging/general DAG| E[Piecewise-linear approx of sqrt cost + MILP solve]
    D --> F[Compute optimal S_j* for every stage]
    E --> F
    F --> G[Derive SI_j = max of predecessor S_i]
    G --> H[Compute NRT_j = SI_j + T_j - S_j]
    H --> I[Compute SS_j = z_j * sigma_j * sqrt(NRT_j)]
    I --> J[Set base-stock B_j = mu_j*NRT_j + SS_j]
    J --> K[Validate customer-facing S_j against contractual SLA]
    K --> L[Deploy safety stock targets to ERP/APS system]
```

### Common Pitfalls

- **Confusing $NRT_j$ with $T_j$**: applying full lead-time coverage at every node re-introduces the double-counting GSM is designed to eliminate.
- **Ignoring the DAG structure at assembly points**: $SI_j$ must be the *maximum*, not sum or average, over predecessor service times — a single slow-service component upstream drives the whole assembly's inbound service time.
- **Non-stationary demand**: applying the $\sqrt{NRT}$ scaling with seasonal or trending demand without re-estimating $\sigma_j$ per period understates required stock during peaks. [Inference — this is a standard caveat noted across GSM literature when demand stationarity is violated, though exact magnitude of error is context-dependent.]
- **Treating $S_j = 0$ nodes as risk-free**: a zero guaranteed outbound service time only means the node buffers all downstream variability itself; it does not mean upstream risk is eliminated network-wide.
- **Cost inputs using full product cost instead of echelon (incremental) holding cost**, which overstates the cost of holding stock early in the chain relative to holding finished goods.

### Related Topics

- Graves-Willems dynamic programming algorithm for spanning trees
- Piecewise-linearization techniques for concave cost functions in MILP
- Guaranteed service model extensions for stochastic (non-deterministic) lead times
- Multi-echelon inventory optimization software (Kinaxis RapidResponse, SAP IBP, LLamasoft)
- Risk pooling and decoupling point placement strategy
- Comparison with the Clark-Scarf stochastic multi-echelon model
- Bill-of-materials (BOM) demand propagation for assembly networks
- Service-driven vs. cost-driven safety stock policy design