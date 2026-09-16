## Congestion Pricing and Pigouvian Road Tolls

### Conceptual Foundations

#### The Externality Problem in Road Use

Traffic congestion is a textbook case of a negative externality arising from **non-excludable, rivalrous** use of a scarce resource (road capacity). Each driver entering a congested roadway imposes delay costs on all other drivers, but considers only their own private cost of travel when deciding whether to make the trip. This wedge between private and social cost produces overconsumption of road space relative to the social optimum.

Formally, let travel demand be represented by an inverse demand curve $p(q)$, where $q$ is traffic volume (trips per unit time) and $p$ is the price (generalized cost) travelers are willing to pay. Let $c(q)$ denote the **average cost** of a trip — primarily travel time converted to money via the value of time — which is increasing in $q$ due to congestion.

#### Average Cost vs. Marginal Social Cost

The central analytical distinction is between:

- **Average (private) cost**: $AC(q) = c(q)$ — the cost experienced by each individual driver, which each driver treats as their marginal cost of travel.
- **Marginal social cost**: $MSC(q) = \dfrac{d[q \cdot c(q)]}{dq} = c(q) + q \cdot c'(q)$

The term $q \cdot c'(q)$ is the **marginal external cost (MEC)** — the additional delay imposed on all other users by one more traveler entering the road. Since $c'(q) > 0$ under congestion, $MSC(q) > AC(q)$ for all $q > 0$.

Unregulated equilibrium occurs where private demand equals average cost:

$$p(q_0) = AC(q_0)$$

The social optimum occurs where demand equals marginal social cost:

$$p(q^*) = MSC(q^*)$$

Because $MSC > AC$, the socially optimal volume $q^*$ is strictly less than the unregulated equilibrium volume $q_0$: $q^* < q_0$.

**(svg_diagram) Average Cost vs. Marginal Social Cost in Road Congestion**

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 720 460" font-family="Helvetica, Arial, sans-serif">
<rect x="0" y="0" width="720" height="460" fill="#ffffff" />
<text x="360" y="24" text-anchor="middle" font-size="15" font-weight="bold" fill="#1a1a1a">Congestion Pricing: AC, MSC, and Demand (svg_diagram)</text>

<line x1="80" y1="400" x2="660" y2="400" stroke="#333" stroke-width="1.5" />
<line x1="80" y1="400" x2="80" y2="50" stroke="#333" stroke-width="1.5" />
<text x="660" y="420" font-size="13" fill="#333">Traffic volume, q</text>
<text x="40" y="45" font-size="13" fill="#333">Price / Cost</text>

<path d="M 140 80 C 300 140, 480 260, 620 380" stroke="#1f77b4" stroke-width="2.5" fill="none" />
<text x="600" y="370" font-size="12" fill="#1f77b4">Demand p(q)</text>

<path d="M 100 360 C 300 350, 480 300, 620 160" stroke="#2ca02c" stroke-width="2.5" fill="none" />
<text x="500" y="270" font-size="12" fill="#2ca02c">AC(q) = c(q)</text>

<path d="M 100 360 C 260 345, 400 220, 520 90" stroke="#d62728" stroke-width="2.5" fill="none" />
<text x="360" y="140" font-size="12" fill="#d62728">MSC(q) = c(q) + q·c'(q)</text>

<circle cx="470" cy="248" r="4.5" fill="#000" />
<line x1="470" y1="248" x2="470" y2="400" stroke="#999" stroke-dasharray="4,3" />
<text x="455" y="416" font-size="12" fill="#000">q₀</text>

<circle cx="330" cy="175" r="4.5" fill="#000" />
<line x1="330" y1="175" x2="330" y2="400" stroke="#999" stroke-dasharray="4,3" />
<text x="315" y="416" font-size="12" fill="#000">q*</text>

<line x1="330" y1="175" x2="330" y2="255" stroke="#ff7f0e" stroke-width="2" />
<text x="340" y="220" font-size="12" fill="#ff7f0e" font-weight="bold">Optimal toll τ*</text>


<text x="380" y="300" font-size="11" fill="#666" font-style="italic">Shaded area (q* to q₀) =</text>

<text x="380" y="315" font-size="11" fill="#666" font-style="italic">deadweight loss from congestion</text>

</svg>

### The Pigouvian Toll

#### Definition and Derivation

A **Pigouvian tax** (here, a road toll) corrects an externality by setting the price faced by users equal to the marginal external cost they impose at the socially optimal quantity. The optimal toll is:

$$\tau^* = MSC(q^*) - AC(q^*) = q^* \cdot c'(q^*)$$

Charging $\tau^*$ per trip shifts the effective price faced by drivers from $AC(q)$ to $AC(q) + \tau^*$, which — if $\tau^*$ is correctly calibrated — makes the new private equilibrium coincide with $q^*$, the social optimum. The toll does not eliminate congestion; it internalizes the externality so that only trips whose value exceeds their true social cost are made.

**Key Points**

- The toll equals the marginal external cost *at the optimum*, not at the current (unregulated) volume.
- Revenue collected is $\tau^* \cdot q^*$, a transfer from users to whoever controls toll revenue (government, private concessionaire), not a resource cost — this matters for welfare accounting.
- The efficiency gain is the **reduction in deadweight loss**: triangle area between $MSC$ and demand curves from $q^*$ to $q_0$.

#### Static Bottleneck Model (Vickrey 1969)

William Vickrey's bottleneck model is the canonical microfoundation for time-varying congestion tolls. A single bottleneck has fixed capacity $s$ (vehicles/hour). Commuters choose departure time $t$ to minimize:

$$\text{Total cost} = \alpha \cdot T(t) + \beta \cdot \max(0, t^* - t - T(t)) + \gamma \cdot \max(0, t + T(t) - t^*)$$

where $T(t)$ is queuing delay at departure time $t$, $t^*$ is the preferred arrival time, $\beta$ is the unit cost of arriving early, and $\gamma$ is the unit cost of arriving late (typically $\gamma > \beta$, reflecting schedule-cost asymmetry).

In user equilibrium, commuters distribute their departures such that generalized cost is equalized across all used departure times — this produces a queue that builds and dissipates in a predictable triangular pattern. The **optimal time-varying toll** replicates the schedule-delay cost with zero queuing: it eliminates the deadweight physical waiting time while preserving the schedule-cost distribution across commuters. This is the theoretical basis for **dynamic/variable pricing** (tolls that rise during peak intervals and fall off-peak) as opposed to a flat toll.

**(svg_diagram) Vickrey Bottleneck Model: Toll and Queue Delay Profile**

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 420" font-family="Helvetica, Arial, sans-serif">
<rect x="0" y="0" width="700" height="420" fill="#ffffff" />
<text x="350" y="24" text-anchor="middle" font-size="15" font-weight="bold" fill="#1a1a1a">Vickrey Bottleneck: Queue Delay vs. Optimal Toll Profile (svg_diagram)</text>
<line x1="70" y1="360" x2="650" y2="360" stroke="#333" stroke-width="1.5" />
<line x1="70" y1="360" x2="70" y2="60" stroke="#333" stroke-width="1.5" />
<text x="600" y="382" font-size="13" fill="#333">Time of day</text>
<text x="30" y="55" font-size="13" fill="#333">Cost</text>

<path d="M 150 360 L 360 130 L 570 360 Z" fill="none" stroke="#1f77b4" stroke-width="2.5" />
<text x="330" y="115" font-size="12" fill="#1f77b4">Queuing delay T(t), no toll</text>

<path d="M 150 360 L 360 200 L 570 360" fill="none" stroke="#d62728" stroke-width="2.5" stroke-dasharray="6,3" />
<text x="380" y="190" font-size="12" fill="#d62728">Optimal toll τ(t), zero queue</text>

<line x1="360" y1="360" x2="360" y2="130" stroke="#999" stroke-dasharray="3,3" />
<text x="352" y="378" font-size="12" fill="#000">t* (preferred arrival)</text>

<text x="90" y="340" font-size="11" fill="#666">Early departures</text>

<text x="480" y="340" font-size="11" fill="#666">Late departures</text>

</svg>

### Second-Best and Practical Considerations

#### Why "First-Best" Tolling Is Rarely Implemented

The Pigouvian toll derived above is a **first-best** policy assuming: (1) tolls can be perfectly differentiated by location, time, and vehicle type; (2) no other distorting taxes exist elsewhere in the transport network; (3) revenue is used efficiently (lump-sum or welfare-neutral redistribution); (4) no pre-existing distortions in related markets (e.g., labor supply, since commuting costs affect labor-leisure choice via the "tax interaction effect").

In practice, most implemented schemes are **second-best**:

- **Cordon pricing**: a flat or time-varying charge for crossing a boundary into a defined zone (London, Stockholm, Milan), rather than continuous congestion-based pricing on every link.
- **Facility-based tolling**: HOT (High-Occupancy/Toll) lanes on specific highway segments (widespread in the U.S. — I-95 Express, SR-91), leaving parallel untolled lanes as an alternative.
- **Area/zone pricing with coarse time bands**: peak/off-peak flat rates rather than continuous dynamic pricing (Singapore's original ALS/ERP tiers).

Second-best tolls trade off implementation simplicity against efficiency loss, since they cannot perfectly track marginal external cost at every point in space and time. The theory of second-best (Lipsey-Lancaster) implies that partial tolling of a network — tolling only some links — need not improve welfare and can, in some configurations, worsen it if traffic diverts onto more congested untolled routes.

#### Distributional and Equity Concerns

A frequently raised objection is that flat per-trip tolls are regressive: the monetary charge is a larger share of income for lower-income drivers, even though the *time cost* of congestion (foregone under tolling) matters relatively more to higher-value-of-time (often higher-income) travelers. Key empirical and policy responses:

- **Value of time (VOT) heterogeneity**: since $\beta, \gamma$, and the value of travel time vary across the population, uniform tolls do not equalize welfare gains; higher-VOT travelers benefit disproportionately from time savings.
- **Revenue recycling**: welfare and equity outcomes depend heavily on how toll revenue is used — funding transit alternatives, direct rebates, or general tax reduction can offset regressivity. [Inference] The equity outcome of any specific scheme depends on local income distribution, alternative mode availability, and the chosen recycling mechanism, so blanket claims that congestion pricing is regressive or progressive are context-dependent rather than a fixed theoretical result.
- **HOT lanes as a partial solution**: by leaving an untolled option, HOT lanes let low-VOT travelers opt out rather than bear a mandatory charge, at the cost of the network not reaching the full first-best optimum.

#### Behavioral and General Equilibrium Responses

Static average-cost/marginal-cost analysis assumes fixed demand and route/mode choice. Real-world responses to congestion pricing include:

- **Route diversion**: traffic shifts to untolled parallel roads, potentially congesting residential streets (documented in evaluations of several cordon schemes).
- **Mode substitution**: shift to transit, cycling, or walking, contingent on availability of substitutes — the elasticity of this response is central to forecasting a scheme's traffic and revenue impact.
- **Temporal shifting**: peak-spreading, where travelers shift departure time rather than reduce trips, consistent with the Vickrey bottleneck logic above.
- **Land use and long-run effects**: [Inference] Sustained congestion pricing can, over a longer horizon, influence firm and household location decisions and urban form, since it changes the relative accessibility cost of central versus peripheral locations — this is a general-equilibrium effect that is harder to identify empirically than short-run traffic responses and is not fully settled in the literature.

### Case Studies

#### Singapore (Area Licensing Scheme, 1975; Electronic Road Pricing, 1998–present)

Singapore's scheme is widely treated as the longest-running real-world implementation of congestion-responsive tolling. It began as a manual Area Licensing Scheme charging vehicles entering the central business district during peak hours, then transitioned to Electronic Road Pricing (ERP) using gantries with **dynamic rates adjusted periodically** (historically quarterly, later moved toward more frequent/real-time adjustment) based on measured traffic speeds, explicitly implementing the theoretical link between observed congestion and toll level.

#### London Congestion Charge (2003–present)

A flat daily charge for entering a central cordon zone during operating hours. Widely credited with an initial reduction in traffic volumes and improvement in bus reliability within the zone; subsequent evaluations note some erosion of initial gains over time (partly attributed to changes in curb allocation, increased private hire vehicle activity, and construction activity), illustrating that a static charge level can lose effectiveness as baseline conditions evolve. [Unverified] Precise long-run percentage effects vary across evaluation studies and time horizons and should be checked against current Transport for London data if being cited for specific figures.

#### Stockholm Congestion Tax (2006 trial, 2007 permanent)

Notable for a **time-varying charge structure** (higher during peak periods, absent at night/weekends) and for being introduced first as a trial with a subsequent referendum — a rare case where public opinion shifted from opposition before implementation to majority support after residents experienced the reduced congestion, often cited in political-economy discussions of policy salience and status quo bias.

#### New York City Congestion Pricing (Central Business District Tolling Program)

A cordon-based charge for Manhattan south of 60th Street, notable as a major U.S. implementation combining federal environmental review, extensive stakeholder litigation, and revenue earmarked for transit capital investment (MTA). [Unverified] Given the program's recency and evolving legal/political status, current operational details, rate schedule, and revenue figures should be verified against current MTA/NYC DOT sources rather than relied upon from prior training data.

### Worked Example

Suppose inverse demand for a road segment is $p(q) = 20 - 0.02q$ (dollars, in value-of-time-equivalent terms), and average cost (travel time cost per trip) is $AC(q) = 4 + 0.01q$.

**Step 1 — Marginal social cost:**

$$MSC(q) = \frac{d[q(4 + 0.01q)]}{dq} = \frac{d[4q + 0.01q^2]}{dq} = 4 + 0.02q$$

**Step 2 — Unregulated equilibrium** ($p = AC$):

$$20 - 0.02q_0 = 4 + 0.01q_0 \implies 16 = 0.03q_0 \implies q_0 = 533.3$$

**Step 3 — Social optimum** ($p = MSC$):

$$20 - 0.02q^* = 4 + 0.02q^* \implies 16 = 0.04q^* \implies q^* = 400$$

**Step 4 — Optimal toll:**

$$\tau^* = MSC(q^*) - AC(q^*) = (4 + 0.02 \cdot 400) - (4 + 0.01 \cdot 400) = 12 - 8 = 4$$

**Step 5 — Toll revenue and welfare gain:**

- Toll revenue: $\tau^* \cdot q^* = 4 \times 400 = 1{,}600$
- Deadweight loss eliminated: the triangular area between $MSC$ and demand from $q^*=400$ to $q_0=533.3$, computable as $\frac{1}{2} \times (533.3 - 400) \times [MSC(533.3) - AC(533.3)]$, since at $q_0$ the vertical gap between $MSC$ and $AC$ (evaluated along the demand curve) represents the marginal uninternalized externality — numerically this evaluates to approximately $\frac{1}{2} \times 133.3 \times 5.33 \approx 355$ in the same cost units.

**Key Points**

- The optimal toll ($4) is *less* than the marginal external cost evaluated at the unregulated volume $q_0$ (which would be $q_0 \cdot c'(q_0) = 533.3 \times 0.01 = 5.33$) — a common source of confusion, since the toll must be evaluated at the *optimal*, not current, quantity, per the fixed-point nature of the equilibrium condition.

### Common Pitfalls

- **Confusing average and marginal cost curves**: treating the private cost curve $AC(q)$ as if it already reflects social marginal cost is the single most common conceptual error in problem sets on this topic.
- **Assuming the optimal toll is set at current traffic levels**: as shown in the worked example, $\tau^*$ must be solved simultaneously with $q^*$, not evaluated at $q_0$.
- **Ignoring revenue disposition in welfare comparisons**: toll revenue is a transfer, not a resource cost; failing to net it out (or account for its use) when comparing tolling to alternatives like capacity expansion leads to incorrect welfare rankings.
- **Treating first-best formulas as directly applicable to real cordon/HOT schemes**: second-best tolling instruments have different, generally smaller, optimal welfare gains than the idealized single-link Pigouvian formula suggests.

### Related Topics

- Vickrey's bottleneck model in full (departure time scheduling equilibrium, step tolls vs. continuous tolls)
- HOT lanes and value pricing mechanism design
- Fuel taxes vs. distance-based tolls vs. cordon pricing as imperfect substitutes for first-best congestion pricing
- Parking pricing and cruising-for-parking externalities (Shoup's model)
- Induced demand and the fundamental law of road congestion
- Public transit subsidy as a second-best complement to road pricing
- Political economy of toll implementation (status quo bias, Stockholm referendum case)
- Interaction between congestion pricing and the "tax interaction effect" in optimal tax theory