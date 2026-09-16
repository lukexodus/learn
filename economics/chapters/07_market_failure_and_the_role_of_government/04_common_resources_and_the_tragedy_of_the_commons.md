## Common Resources and the Tragedy of the Commons

### Definition and Core Characteristics

Common resources (also called **common-pool resources**, CPRs) are goods characterized by two properties:

**Non-excludability**: it is difficult or costly to prevent individuals from accessing and using the resource.

**Rivalry (rivalrous consumption)**: one person's use of the resource reduces the amount available to others, unlike a pure public good.

This combination — non-excludable but rivalrous — places common resources in a distinct quadrant of the goods classification matrix, alongside private goods, public goods, and club goods.

|  | Excludable | Non-excludable |
| --- | --- | --- |
| **Rivalrous** | Private goods (food, cars) | **Common resources** (fisheries, groundwater, grazing land, congested roads, atmosphere as a carbon sink) |
| **Non-rivalrous** | Club goods (cable TV, toll roads) | Public goods (national defense, lighthouses) |

### Classic Examples

- Ocean fisheries and other wild fish stocks
- Groundwater aquifers
- Communal grazing pastures (the original "commons" of English agricultural history)
- Old-growth forests and timber stands
- Congested public roads (rivalry appears via congestion, though roads can be made excludable via tolls)
- The atmosphere's capacity to absorb greenhouse gases
- Wild animal populations (bushmeat hunting, elephant ivory)
- Radio spectrum (prior to licensing regimes)

### The Tragedy of the Commons

The **tragedy of the commons** is the tendency for a shared, rivalrous, non-excludable resource to be overused and depleted beyond the socially efficient level, because individual users bear only a fraction of the cost of their own extraction while capturing the full benefit.

The term was popularized by ecologist **Garrett Hardin** in his 1968 *Science* article "The Tragedy of the Commons," though the underlying economic logic predates Hardin and is closely related to earlier analyses of open-access fisheries by economists such as H. Scott Gordon (1954). [Unverified: attribution priority between Hardin and earlier resource economists is a matter of some historical debate in the literature, though Hardin's framing is the one most commonly cited in introductory economics.]

### Formal Economic Logic

Consider a resource (e.g., a fishery) where each additional unit of extraction by any individual imposes a cost on all other users by depleting the shared stock — this is a **negative externality** internal to the group of users.

Define:

- $MPB$ = marginal private benefit to an individual user of one more unit of extraction
- $MSC$ = marginal social cost of that extraction, which includes both the individual's private cost and the externality imposed on other users (the depletion cost)

Efficient use requires:

$$MPB = MSC$$

But each individual user, ignoring the externality they impose on others, extracts up to the point where:

$$MPB = MPC$$

where $MPC$ (marginal private cost) is strictly less than $MSC$ because it excludes the externality. Since $MPC < MSC$, individually rational extraction continues **past** the socially efficient quantity $Q^*$, leading to a resource stock level below the social optimum — overexploitation.

**Key Points**

- The tragedy of the commons is structurally a **negative externality problem** applied to a shared, depletable resource — it is a special case of the general divergence between private and social cost.
- It differs from the free-rider problem: free-riding involves under-contribution to a non-rivalrous public good; the tragedy of the commons involves over-extraction from a rivalrous common resource. Both are market failures rooted in the absence of well-defined, enforceable property rights, but the direction of the inefficiency (under-provision vs. over-consumption) is opposite.
- Open-access conditions (no restrictions on entry or extraction) tend to push resource use toward the point where average — not marginal — private benefit equals average private cost, potentially dissipating the entire resource rent (this is the classic result in **bioeconomic fishery models**, e.g., the Gordon-Schaefer model).

### Diagram: Divergence Between Private and Social Optimum

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 380" font-family="sans-serif">
<text x="320" y="24" text-anchor="middle" font-size="16" font-weight="bold">Overextraction in an Open-Access Common Resource (svg_diagram)</text>
<line x1="80" y1="330" x2="580" y2="330" stroke="black" stroke-width="2" />
<line x1="80" y1="330" x2="80" y2="50" stroke="black" stroke-width="2" />
<text x="580" y="350" font-size="13">Extraction Quantity (Q)</text>
<text x="20" y="55" font-size="13">$/Marginal Value</text>
<line x1="80" y1="90" x2="560" y2="290" stroke="#2563eb" stroke-width="2" />
<text x="560" y="285" font-size="12" fill="#2563eb">MPB (demand for extraction)</text>
<line x1="80" y1="300" x2="560" y2="130" stroke="#7c3aed" stroke-width="2" stroke-dasharray="5,3" />
<text x="450" y="165" font-size="12" fill="#7c3aed">MPC (private cost)</text>
<line x1="80" y1="260" x2="480" y2="70" stroke="#dc2626" stroke-width="2.5" />
<text x="380" y="90" font-size="12" fill="#dc2626" font-weight="bold">MSC (private + externality)</text>
<circle cx="330" cy="210" r="4" fill="black" />
<line x1="330" y1="210" x2="330" y2="330" stroke="black" stroke-dasharray="3,3" />
<text x="315" y="345" font-size="12" font-weight="bold">Q_market</text>
<circle cx="235" cy="163" r="4" fill="black" />
<line x1="235" y1="163" x2="235" y2="330" stroke="black" stroke-dasharray="3,3" />
<text x="205" y="345" font-size="12" font-weight="bold">Q* (efficient)</text>
<path d="M235,163 L330,163 L330,210 Z" fill="#fca5a5" fill-opacity="0.5" />
<text x="250" y="145" font-size="11" fill="#991b1b">Deadweight loss from</text>
<text x="250" y="158" font-size="11" fill="#991b1b">overextraction</text>
</svg>

The market/open-access equilibrium occurs where $MPB = MPC$, at quantity $Q_{market}$, which lies to the right of the socially efficient quantity $Q^*$ where $MPB = MSC$. The shaded region represents the welfare loss from resource units extracted where the marginal social cost exceeds the marginal benefit.

### The Bioeconomic Model (Fisheries Application)

A widely used formalization is the **Gordon-Schaefer model** of an open-access fishery, which relates the biological growth of a fish stock to the economic incentives of harvesters.

The stock's natural growth is often modeled as **logistic growth**:

$$\frac{dX}{dt} = rX\left(1 - \frac{X}{K}\right) - H$$

where $X$ is the current stock size, $r$ is the intrinsic growth rate, $K$ is the carrying capacity, and $H$ is the harvest rate.

Under open access, entry continues until total revenue equals total cost (economic profit driven to zero), which typically results in a stock level **below** the level that would maximize sustainable yield or economic rent — the hallmark bioeconomic signature of the tragedy of the commons. [Inference: the precise equilibrium stock level depends on functional-form assumptions (harvest production function, cost structure) and real fisheries show substantial deviation from the stylized model due to regulation, technology change, and stock uncertainty.]

### Government and Institutional Responses

**Government regulation (command-and-control)**:

- Catch limits / quotas (Total Allowable Catch, TAC)
- Licensing and permit systems restricting entry
- Seasonal closures and harvest bans
- Technology restrictions (net size, gear type)

**Assignment of property rights**:

- **Individual Transferable Quotas (ITQs)**: tradable rights to harvest a fixed share of the total allowable catch, converting an open-access resource into something closer to a private-property regime, aligning individual incentives with sustainable extraction.
- **Privatization**: converting communal grazing land or forest into individually owned parcels, internalizing the previously external costs of overuse.

**Pigouvian correction**:

- Extraction taxes set so that $MPC + \text{tax} = MSC$, inducing individually rational actors to extract at the socially efficient rate without requiring direct property assignment.

**Community-based / self-governance solutions**:

- **Elinor Ostrom's** research (for which she was awarded the Nobel Memorial Prize in Economic Sciences in 2009) documented numerous historical and contemporary cases where communities successfully managed common-pool resources through self-organized institutions — without either full privatization or centralized government control — by developing locally enforced rules, monitoring, and graduated sanctions.

Ostrom identified a set of institutional design principles associated with durable, successful commons governance, commonly summarized as:

```mermaid
flowchart TD
    A[Ostrom's Design Principles<br/>for Commons Governance (illustrative)] --> B[Clearly defined<br/>resource boundaries]
    A --> C[Rules matched to<br/>local conditions]
    A --> D[Collective-choice<br/>arrangements for users]
    A --> E[Effective monitoring<br/>by or accountable to users]
    A --> F[Graduated sanctions<br/>for rule violators]
    A --> G[Accessible conflict-<br/>resolution mechanisms]
    A --> H[Government recognition<br/>of self-governance rights]
    A --> I[Nested governance for<br/>larger-scale commons]
```

[Unverified: the exact wording and count of Ostrom's principles vary slightly across her publications and secondary summaries; the diagram above reflects the commonly cited eight-principle synthesis from *Governing the Commons* (1990).]

### Worked Numerical Example

A communal fishing lake is used by many independent fishers. Each fisher's private cost of an additional day of fishing is $50 (private cost: boat fuel, time). Each additional day of fishing yields the fisher $70 in caught fish (their $MPB$).

However, each day of fishing also depletes the shared fish stock, imposing an estimated $30 externality cost on all other fishers combined (reduced future catch for everyone), which is not reflected in the individual fisher's decision.

- **Individual private decision rule**: Fish as long as $MPB > MPC$: $70 > 50$, so the individual keeps fishing.
- **Socially efficient rule**: Fish as long as $MPB > MSC$, where $MSC = MPC + \text{externality} = 50 + 30 = 80$. Since $70 < 80$, the socially efficient choice would be to **not** take this additional fishing day.

The gap between individually rational behavior (keep fishing, since $70 > 50$) and socially efficient behavior (stop, since $70 < 80$) is the tragedy of the commons in miniature. A corrective tax of $30 per fishing day would raise the fisher's effective private cost to $80, aligning private incentives with the social optimum.

### Distinguishing Related Concepts

**Tragedy of the commons vs. free-rider problem**: Both stem from non-excludability and the absence of enforceable property rights, but the free-rider problem concerns under-provision of a non-rivalrous public good, while the tragedy of the commons concerns over-extraction of a rivalrous common resource.

**Tragedy of the commons vs. negative externalities generally**: The tragedy of the commons is a specific instance of negative externalities where the externality is generated and borne by members of the *same* user group extracting from a *shared, depletable* resource, rather than imposed on unrelated third parties (e.g., factory pollution affecting nearby residents).

**Common resources vs. club goods**: If exclusion technology becomes available or affordable (e.g., fencing grazing land, licensing fishing access), a common resource can be converted into either a private good or a club good, which typically resolves the overuse problem by realigning private and social incentives — this is the essence of the "privatization" and "ITQ" solutions above.

**Related Topics**

- Public Goods and the Free-Rider Problem
- Externalities and Pigouvian taxation
- Coase Theorem and transaction-cost limits on private bargaining solutions
- Elinor Ostrom's institutional economics and polycentric governance
- Individual Transferable Quotas (ITQs) and cap-and-trade systems
- Bioeconomic fishery modeling (Gordon-Schaefer model, maximum sustainable yield)
- Climate change as a global tragedy of the commons (atmospheric carbon sink)
- Property rights theory and the economics of institutions