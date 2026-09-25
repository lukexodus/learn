## Facility Location Decisions and Capacity


### Overview

Facility location decisions determine *where* new capacity should be built, expanded, or consolidated, and they are inseparable from *how much* capacity should be built at each site — location choice affects input costs, transportation costs, access to labor and markets, and the ability to serve demand reliably, all of which feed directly back into the sizing, timing, and economic justification of the capacity itself. Location decisions are typically among the most consequential and least reversible capacity decisions an organization makes, given the long time horizons, large capital commitments, and high switching costs involved.

### Why Location and Capacity Decisions Are Interlinked

**Key Points**

- Location determines the input cost structure (labor rates, energy costs, raw material access, real estate) that feeds directly into the fixed and variable cost figures used in break-even, CVP, and NPV analysis covered earlier in this curriculum.
- Location determines transportation and logistics cost to reach markets, which interacts with economies of scale: a single large, centrally-located facility may capture more production-side scale economies but incur higher aggregate transportation costs than several smaller, geographically distributed facilities serving local markets — directly echoing the diseconomies-of-scale logistics effect discussed earlier.
- Location affects the achievable capacity itself: local labor market size and skill availability, utility/energy capacity, land availability, and regulatory maximums can all cap how much capacity a given site can realistically support, regardless of financial willingness to invest further.
- The number and size of facilities is a joint decision with location: choosing "one large centralized facility" versus "several smaller regional facilities" is simultaneously a capacity-sizing decision (interacting with minimum efficient scale) and a location decision (interacting with market proximity and logistics cost).

### Key Factors in Facility Location Decisions

| Factor Category | Specific Considerations |
| --- | --- |
| **Market proximity** | Distance to major demand centers, transportation/shipping cost and time, service-level requirements for delivery speed |
| **Input/supply proximity** | Distance to raw material sources, supplier networks, component availability |
| **Labor** | Availability, cost, skill level, unionization, labor market depth for the required workforce size |
| **Infrastructure** | Transportation networks (road, rail, port, air), utility capacity (power, water, telecommunications/network bandwidth for IT facilities), site development readiness |
| **Regulatory and tax environment** | Zoning, environmental regulations, tax incentives/abatements, trade agreements and tariffs, permitting timelines |
| **Risk factors** | Political stability, natural disaster exposure (seismic, flood, hurricane zones), climate considerations (relevant for both facility risk and, for data centers, cooling costs) |
| **Cost of living and quality of life** | Affects ability to attract and retain skilled workforce, particularly relevant for facilities requiring specialized talent |
| **Strategic considerations** | Proximity to competitors or complementary businesses (clustering effects), currency exposure for international operations, supply chain diversification/resilience goals |

### Location Decision Frameworks

#### 1. Factor Rating (Weighted Scoring) Method

A widely used, straightforward technique that scores candidate locations against multiple weighted criteria to produce a comparable composite score.

$$\text{Composite Score}_i = \sum_{j} w_j \times s_{ij}$$

where $w_j$ is the weight assigned to factor $j$ (weights typically summing to 1 or 100), and $s_{ij}$ is location $i$'s score on factor $j$ (often rated on a common scale, e.g., 1–100).

**Example factor rating table:**

| Factor | Weight | Location A Score | Location B Score | Location C Score |
| --- | --- | --- | --- | --- |
| Labor cost/availability | 0.25 | 80 | 65 | 90 |
| Market proximity | 0.20 | 90 | 70 | 60 |
| Infrastructure quality | 0.20 | 75 | 85 | 70 |
| Tax/regulatory environment | 0.15 | 60 | 90 | 75 |
| Risk (disaster/political) | 0.10 | 85 | 80 | 60 |
| Expansion potential | 0.10 | 70 | 75 | 85 |
| **Weighted Total** |  | **77.75** | **76.75** | **74.5** |

```python
factors = {
    "labor": {"weight": 0.25, "A": 80, "B": 65, "C": 90},
    "market_proximity": {"weight": 0.20, "A": 90, "B": 70, "C": 60},
    "infrastructure": {"weight": 0.20, "A": 75, "B": 85, "C": 70},
    "tax_regulatory": {"weight": 0.15, "A": 60, "B": 90, "C": 75},
    "risk": {"weight": 0.10, "A": 85, "B": 80, "C": 60},
    "expansion": {"weight": 0.10, "A": 70, "B": 75, "C": 85},
}

locations = ["A", "B", "C"]
scores = {loc: sum(f["weight"] * f[loc] for f in factors.values()) for loc in locations}
print(scores)
```

**Key Points**

- The factor rating method's main strength is transparency and the ability to incorporate qualitative and quantitative factors side by side on a common scale — its main weakness is the subjectivity inherent in both weight assignment and factor scoring, which can be manipulated (consciously or not) to favor a predetermined preference.

#### 2. Center of Gravity Method

A quantitative technique for finding the geographically optimal single-facility location that minimizes total transportation cost/distance to a set of demand points, weighted by the volume shipped to each point.

$$C_x = \frac{\sum_i d_{ix} \cdot W_i}{\sum_i W_i} \qquad C_y = \frac{\sum_i d_{iy} \cdot W_i}{\sum_i W_i}$$

where $d_{ix}, d_{iy}$ are the coordinates of demand point $i$, and $W_i$ is the volume/weight shipped to or from that point.

**Example**: Three demand centers with coordinates and volumes:

| Demand Center | X-coordinate | Y-coordinate | Volume (units/year) |
| --- | --- | --- | --- |
| City 1 | 200 | 300 | 4,000 |
| City 2 | 500 | 100 | 6,000 |
| City 3 | 350 | 450 | 3,000 |

$$C_x = \frac{(200 \times 4{,}000) + (500 \times 6{,}000) + (350 \times 3{,}000)}{4{,}000+6{,}000+3{,}000} = \frac{800{,}000 + 3{,}000{,}000 + 1{,}050{,}000}{13{,}000} = \frac{4{,}850{,}000}{13{,}000} \approx 373.1$$



$$C_y = \frac{(300 \times 4{,}000) + (100 \times 6{,}000) + (450 \times 3{,}000)}{13{,}000} = \frac{1{,}200{,}000 + 600{,}000 + 1{,}350{,}000}{13{,}000} = \frac{3{,}150{,}000}{13{,}000} \approx 242.3$$

The volume-weighted center of gravity is approximately (373, 242), suggesting a facility located near this point would minimize aggregate weighted transportation distance across the three demand centers.

```python
demand_points = [
    {"x": 200, "y": 300, "volume": 4000},
    {"x": 500, "y": 100, "volume": 6000},
    {"x": 350, "y": 450, "volume": 3000},
]

total_volume = sum(p["volume"] for p in demand_points)
cx = sum(p["x"] * p["volume"] for p in demand_points) / total_volume
cy = sum(p["y"] * p["volume"] for p in demand_points) / total_volume
print(f"Center of gravity: ({cx:.1f}, {cy:.1f})")
```

**Key Points**

- The center-of-gravity method minimizes total weighted distance, not total cost — it assumes transportation cost is roughly proportional to distance and volume, which is a simplification that may not hold precisely if transportation rates vary by mode, route, or region.
- The method identifies a single optimal point assuming one facility serves all demand; it does not directly solve the more complex multi-facility location problem (how many facilities to build and where), though it can be applied iteratively or combined with clustering techniques as a starting point for multi-facility analysis.

#### 3. Transportation/Location-Allocation Models

For decisions involving multiple facilities and multiple demand points, more sophisticated optimization models (transportation problem formulations, mixed-integer programming) determine both the optimal number and location of facilities and how demand should be allocated across them, minimizing total cost (facility fixed costs plus transportation costs) subject to capacity constraints at each candidate site.

$$\min \sum_{j} F_j y_j + \sum_{i,j} c_{ij} x_{ij}$$

subject to demand satisfaction and capacity constraints, where $y_j$ is a binary decision variable (whether to build at candidate site $j$), $F_j$ is the fixed cost of building at site $j$, $x_{ij}$ is the quantity shipped from facility $j$ to demand point $i$, and $c_{ij}$ is the per-unit transportation cost.

```mermaid
flowchart TD
    A[Candidate facility sites with fixed costs] --> B[Demand points with volumes]
    B --> C[Transportation cost matrix between sites and demand points]
    C --> D[Optimization model:<br/>minimize total fixed + transportation cost (svg_diagram)]
    D --> E[Output: which sites to build, and demand allocation to each]
```

[Unverified] The specific solution technique (exact mixed-integer programming versus heuristic approaches) used in practice depends heavily on problem scale — very large multi-facility, multi-product location problems are often computationally intensive and may require heuristic or metaheuristic solution methods rather than guaranteed-optimal exact solutions.

### Location Decisions in IT and Data Center Capacity

Facility location logic applies directly to data center and cloud infrastructure siting, with some domain-specific factors added to the general framework:

| General Location Factor | Data Center-Specific Analogue |
| --- | --- |
| Market proximity | Network latency to end users; proximity to internet exchange points |
| Input/supply proximity | Access to reliable, low-cost power generation; fiber connectivity |
| Infrastructure | Redundant power grid access, water availability for cooling, network backbone connectivity |
| Regulatory environment | Data sovereignty/residency requirements, energy regulations, tax incentives for data center investment |
| Risk factors | Natural disaster exposure, grid reliability, political/regulatory stability for data governance |
| Climate | Ambient temperature and humidity affecting cooling costs (cooler climates can reduce cooling energy requirements) |

**Example**: A cloud provider selecting a new data center region typically weighs network latency to target user populations (a market-proximity factor) against power availability and cost, cooling climate advantages, land cost, and data sovereignty regulations relevant to the customers expected to use that region — directly mirroring the factor-rating approach used in traditional manufacturing facility siting, with domain-specific factors substituted in.

### Single Large Facility vs. Multiple Distributed Facilities

This decision directly connects location strategy back to the economies of scale, diseconomies of scale, and economies of scope concepts covered earlier in this curriculum:

| Consideration | Favors Single Large Facility | Favors Multiple Distributed Facilities |
| --- | --- | --- |
| Production-side scale economies | Yes — concentrates volume for maximum scale benefit | No — splits volume, potentially below MES at each site |
| Transportation/logistics cost | No — longer average shipping distance to dispersed markets | Yes — shorter distances to regional markets |
| Risk/resilience | No — single point of failure | Yes — diversifies risk across sites |
| Demand pooling across regions | Yes — aggregates regional demand variability into one larger, smoother pool | No — each site faces its own regional demand variability independently |
| Responsiveness/service level to local markets | Lower — greater distance/lead time to some markets | Higher — closer proximity supports faster service |
| Coordination complexity | Lower — single site to manage | Higher — multiple sites require more coordination (diseconomies of scale/complexity) |

### Practical Facility Location Workflow

```mermaid
flowchart TD
    A[Define capacity requirement from demand forecast] --> B[Determine single vs multi-facility strategy]
    B --> C[Identify candidate locations/regions]
    C --> D[Screen candidates against critical/must-have factors]
    D --> E[Apply center of gravity or optimization model for quantitative siting]
    E --> F[Apply factor rating for qualitative/strategic factors]
    F --> G[Combine quantitative and qualitative analysis]
    G --> H[Validate against break-even/NPV analysis using location-specific cost structure]
    H --> I[Select location(s) and finalize capacity sizing at each site]
```

### Common Pitfalls

- **Optimizing location purely on cost while ignoring risk concentration** — selecting a single, minimum-cost location without considering the resilience value of geographic diversification, particularly relevant given supply chain disruption risk.
- **Underestimating regulatory/permitting timelines** in the overall capacity delivery lead time, which directly affects the capacity gap and lead-time considerations covered in demand forecasting and S&OP topics earlier in this curriculum.
- **Treating location as independent of capacity sizing** rather than jointly optimizing both — a location's labor market depth, utility capacity, or land availability can effectively cap the feasible facility size, meaning location and capacity decisions should be evaluated together rather than sequentially.
- **Applying center-of-gravity or factor-rating results mechanically** without validating that the underlying cost and volume assumptions remain accurate, particularly for long-lived facility decisions where demand patterns and transportation costs may shift substantially over the facility's operating life.

**Conclusion**

Facility location and capacity decisions are fundamentally intertwined: where a facility is sited determines its cost structure, achievable scale, transportation economics, and risk profile, all of which feed directly into the financial analysis techniques (break-even, CVP, NPV) covered earlier in this curriculum, while capacity requirements and single-versus-multi-facility strategy simultaneously shape which locations are viable candidates in the first place. Structured techniques — factor rating for multi-criteria qualitative and quantitative comparison, center-of-gravity analysis for transportation-cost-minimizing siting, and formal location-allocation optimization for multi-facility problems — provide a disciplined basis for this decision, but must be complemented by judgment about risk concentration, regulatory timelines, and the joint nature of the location-and-capacity-sizing decision.

**Related Topics**

- Economies of scale and minimum efficient scale
- Diseconomies of scale and complexity costs
- Net present value and capital budgeting for capacity
- Demand variability and its capacity implications (risk pooling across regions)
- Supply chain resilience and geographic diversification
- Data center site selection and cloud region strategy
- Long-term capacity expansion timing and strategy