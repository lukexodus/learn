## Coal's Role in Electricity Generation Economics


### Overview

Coal's role in electricity generation economics concerns how coal-fired power plants are dispatched, priced, and evaluated for investment within broader electricity markets, and how coal's specific cost and operational characteristics shape its competitive position relative to alternative generation technologies. Historically the dominant global source of electricity generation, coal-fired power's economic role has evolved significantly with the emergence of competitive wholesale electricity markets, cheaper natural gas (particularly following the shale gas revolution in some markets), declining renewable energy costs, and the introduction of carbon pricing and environmental regulation in many jurisdictions.

### Cost Structure of Coal-Fired Generation

#### Capital, Fixed, and Variable Cost Components

Coal power plant economics are typically decomposed into three broad cost categories, each relevant to different decision timeframes:

| Cost Category | Nature | Examples | Relevant Decision |
| --- | --- | --- | --- |
| Capital cost (CapEx) | Sunk once incurred; recovered over plant life | Boiler, turbine, generator, emissions control equipment, cooling systems | New-build investment decision |
| Fixed operating cost | Incurred regardless of output level, but avoidable if plant is retired | Staffing, routine maintenance, insurance, property taxes | Long-run retirement/retention decision |
| Variable operating cost | Scales directly with generation output | Fuel (coal), variable O&M, emissions allowances (where applicable) | Short-run dispatch decision |

**Key Points**

- Once a coal plant is built, capital cost is sunk and does not factor into short-run dispatch decisions—only variable cost matters for determining whether the plant runs in a given hour in a competitive market
- Fixed operating costs, while not directly tied to output, must be covered over time for continued plant operation to remain economically justified, making them central to long-run retirement decisions even though they don't affect hour-to-hour dispatch
- This cost structure distinction (sunk capital vs. avoidable fixed cost vs. variable cost) is fundamental to understanding both short-run merit order dispatch and long-run investment/retirement economics

#### Heat Rate and Fuel Cost Conversion

A plant's **heat rate** measures the amount of fuel energy required to generate one unit of electricity, serving as the key link between coal price and generation variable cost:

$$\text{Variable Fuel Cost} \, (\$/\text{MWh}) = \text{Heat Rate} \, (\text{MMBtu/MWh}) \times \text{Coal Price} \, (\$/\text{MMBtu})$$

- Lower heat rate indicates higher thermal efficiency (less fuel required per unit of electricity output)
- Modern supercritical and ultra-supercritical coal plants achieve meaningfully lower heat rates (higher efficiency) than older subcritical plants, directly translating into lower variable fuel cost per MWh generated for a given coal price
- [Inference] Because heat rate directly scales fuel cost, older, less efficient coal units are generally more vulnerable to being priced out of the dispatch order during periods of high coal prices or strong competition from lower-variable-cost alternatives, which is one reason plant efficiency (vintage and technology) is a key determinant of which specific coal units remain economically competitive within a given fleet

### Merit Order Dispatch and Marginal Pricing

#### The Merit Order Concept

In competitive wholesale electricity markets, generating units are typically dispatched in ascending order of variable (short-run marginal) cost—the **merit order**—until sufficient capacity is committed to meet demand in each period.

```mermaid
flowchart LR
    A[Rank All Available Plants by Variable Cost] --> B[Stack Cumulative Capacity vs Cost]
    B --> C[Identify System Demand Level]
    C --> D[Marginal Plant = Highest-Cost Unit Needed]
    D --> E[Marginal Cost Sets Market Clearing Price in Many Market Designs]
```

**Key Points**

- Coal plants' position in the merit order depends on their variable cost, which is driven primarily by heat rate and delivered coal price (plus any applicable carbon cost)
- In markets with significant low-marginal-cost renewable generation (wind, solar, which have near-zero variable cost once built), coal plants are increasingly dispatched behind renewables in the merit order, reducing coal plant utilization (capacity factor) even where the coal plant remains technically available
- [Inference] This dynamic—renewables entering ahead of coal in the merit order due to near-zero variable cost—has been a significant factor reducing coal plant capacity factors and revenue in many markets with substantial renewable capacity growth, independent of any direct policy restriction on coal generation itself, since it reflects ordinary economic dispatch based on relative variable costs

#### Illustration: Merit Order Stack with Coal Position (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 380">
<text x="320" y="25" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Stylized Electricity Merit Order Stack (svg_diagram)</text>
<line x1="70" y1="320" x2="590" y2="320" stroke="#333" stroke-width="2" />
<line x1="70" y1="320" x2="70" y2="60" stroke="#333" stroke-width="2" />

<text x="330" y="355" text-anchor="middle" font-size="13" fill="#333">Cumulative Capacity (MW)</text>

<text x="25" y="190" text-anchor="middle" font-size="13" fill="#333" transform="rotate(-90 25 190)">Variable Cost ($/MWh)</text>


<rect x="70" y="300" width="90" height="20" fill="#27ae60" />
<text x="115" y="314" text-anchor="middle" font-size="10" fill="white">Renewables</text>

<rect x="160" y="285" width="70" height="35" fill="#8e44ad" />
<text x="195" y="305" text-anchor="middle" font-size="10" fill="white">Nuclear</text>

<rect x="230" y="230" width="140" height="90" fill="#7f8c8d" />
<text x="300" y="278" text-anchor="middle" font-size="11" fill="white">Coal</text>

<rect x="370" y="180" width="120" height="140" fill="#e67e22" />
<text x="430" y="253" text-anchor="middle" font-size="11" fill="white">Gas Combined Cycle</text>

<rect x="490" y="100" width="90" height="220" fill="#c0392b" />
<text x="535" y="213" text-anchor="middle" font-size="10" fill="white">Gas Peakers</text>
<line x1="450" y1="60" x2="450" y2="320" stroke="#2980b9" stroke-width="2" stroke-dasharray="6,4" />
<text x="455" y="75" font-size="12" fill="#2980b9" font-weight="bold">System Demand</text>
</svg>

### Capacity Factor Economics

#### Baseload vs. Cycling Operation

Coal plants were traditionally designed and operated as **baseload** units—running at high, relatively constant output to serve the steady portion of electricity demand. However, as noted above, the entry of low-marginal-cost renewables into many electricity systems has shifted many coal units toward more variable, **cycling** operation (ramping output up and down, or shutting down and restarting, to accommodate fluctuating net demand after accounting for renewable generation).

**Key Points**

- Coal boilers and turbines are generally designed for steady baseload operation, and increased cycling can impose additional wear, reduced efficiency, and higher maintenance costs relative to the plant's original design intent
- [Inference] This transition from baseload to cycling operation represents an additional economic cost not always fully captured in simple variable-cost dispatch models, since more frequent starts/stops and ramping accelerate equipment fatigue and can increase unplanned outage risk, a factor increasingly incorporated into more sophisticated plant economic assessments
- Reduced capacity factor directly reduces the plant's ability to spread fixed costs across generation output, worsening its per-MWh all-in economics even if variable cost per MWh generated remains unchanged

#### Capacity Factor and Fixed Cost Recovery

$$\text{Average Total Cost} \, (\$/\text{MWh}) = \frac{\text{Fixed Costs (Annual)}}{\text{Capacity} \, (\text{MW}) \times 8760 \, \text{hrs} \times \text{Capacity Factor}} + \text{Variable Cost} \, (\$/\text{MWh})$$

This relationship illustrates why declining capacity factors (from reduced dispatch due to merit order position, or from being held as reserve/peaking capacity) directly raise a plant's average total cost per MWh generated, even holding fixed and variable costs themselves constant.

### Carbon Pricing and Environmental Compliance Costs

#### Carbon Cost Pass-Through to Dispatch

Where carbon pricing mechanisms (emissions trading schemes or carbon taxes) apply, coal generation's variable cost calculation must incorporate the carbon cost per unit of electricity generated:

$$\text{Variable Cost with Carbon} = (\text{Heat Rate} \times \text{Coal Price}) + (\text{Emissions Rate} \times \text{Carbon Price}) + \text{Variable O\&M}$$

**Key Points**

- Because coal generally has a higher CO2 emissions rate per MWh than natural gas combined cycle generation, carbon pricing tends to raise coal's variable cost more than gas's, all else equal, potentially shifting relative merit order position between coal and gas plants (sometimes referred to as "coal-to-gas switching" in dispatch)
- The carbon price level at which gas becomes cheaper than coal on a variable cost basis (the "switching price") depends on the specific heat rates and emissions rates of the plants being compared, as well as prevailing coal and gas prices, meaning there is no single universal switching price applicable across all plants or markets
- [Inference] In jurisdictions with meaningful carbon pricing, this dynamic has been a documented contributor to reduced coal dispatch and increased gas dispatch in short-run merit order outcomes, though the magnitude of this effect depends heavily on the specific carbon price level and the relative gas-coal price ratio prevailing at the time, both of which vary considerably across markets and over time

#### Other Environmental Compliance Costs

Beyond carbon pricing, coal plants in many jurisdictions face compliance costs related to other emissions and environmental controls:

- Sulfur dioxide (SO2) and nitrogen oxide (NOx) emissions control equipment (flue gas desulfurization, selective catalytic reduction) and associated operating costs
- Particulate matter controls (electrostatic precipitators, baghouses)
- Coal ash/residual waste management and disposal regulations
- Water use and discharge regulations for plant cooling systems

[Unverified] The specific magnitude of these compliance costs varies enormously by jurisdiction, plant vintage, and the specific control technologies already installed, so general cost figures should not be treated as broadly applicable without reference to a specific plant and regulatory context.

### Levelized Cost of Electricity (LCOE) Framework

#### LCOE Calculation Structure

Long-run investment comparisons across generation technologies commonly use the **Levelized Cost of Electricity (LCOE)** metric, which expresses all costs (capital, fixed, variable) as a single per-MWh figure over the plant's assumed operating life:

$$LCOE = \frac{\sum_{t=0}^{T} \frac{CapEx_t + FixedOM_t + VariableOM_t + Fuel_t}{(1+r)^t}}{\sum_{t=0}^{T} \frac{Q_t}{(1+r)^t}}$$

Where $Q_t$ is electricity generated in period $t$, and $r$ is the discount rate.

**Key Points**

- LCOE allows comparison of technologies with very different cost structures (e.g., high-capital/low-variable-cost renewables versus lower-capital/higher-variable-cost coal or gas plants) on a common per-MWh basis
- LCOE has well-recognized limitations for comparing intermittent renewable generation directly against dispatchable thermal generation (like coal), since it does not inherently capture the value of dispatchability, capacity contribution to system reliability, or the system integration costs associated with variable renewable output—comparisons should account for these factors separately rather than relying on LCOE alone
- [Inference] For new-build investment decisions specifically (as opposed to continued operation of existing plants), LCOE comparisons in many markets have shown new coal generation to be less cost-competitive than new-build renewables and, in many cases, new-build natural gas generation, which has been a contributing factor (alongside financing availability and policy considerations) in reduced new coal plant construction in numerous markets in recent years, though the comparison outcome depends significantly on region-specific capital costs, resource quality (for renewables), and local fuel prices

### Coal Plant Retirement Economics

#### The Retirement Decision Framework

The decision to retire an existing coal plant (versus continuing operation) is fundamentally a comparison between the plant's expected future net cash flows (revenue minus avoidable costs) if it continues operating, versus its retirement/decommissioning cost and any alternative value of the site or assets:

$$\text{Continue Operating if: } \sum_{t} \frac{(\text{Revenue}_t - \text{Avoidable Cost}_t)}{(1+r)^t} > \text{Decommissioning Cost} - \text{Salvage/Alternative Value}$$

**Key Points**

- A coal plant facing declining capacity factor (due to merit order displacement by renewables or cheaper gas) generates less revenue to cover its fixed costs, which can push the plant toward an economic retirement decision even absent any direct regulatory retirement mandate
- Required environmental compliance investments (e.g., a major emissions control system upgrade needed to continue legal operation) can trigger retirement decisions when the required capital investment is not justified by the plant's expected remaining revenue-generating capability, particularly for older or smaller units
- [Inference] This combination of declining merit-order dispatch revenue and periodic large compliance capital requirements has been a recurring pattern associated with coal plant retirement decisions in a number of markets, though the specific timing and pace of retirements in any given jurisdiction depends on plant-specific economics, local market design, and regulatory/policy context that vary considerably by location

### Capacity Markets and Reliability Value

In electricity market designs that include separate capacity markets or resource adequacy mechanisms (distinct from energy-only markets), coal plants may earn revenue for their **capacity value**—their contribution to meeting system reliability requirements—independent of how often they are actually dispatched for energy.

**Key Points**

- Capacity payments can provide meaningful revenue to coal plants that have low capacity factors under energy-only merit order dispatch, since they compensate the plant for being available when needed (e.g., during extreme demand or low-renewable-output periods) rather than for actual energy produced
- [Inference] The presence and design of a capacity market can materially affect whether continued coal plant operation is economically viable at a given renewables penetration level, since capacity payments can offset revenue shortfalls from reduced energy dispatch, meaning retirement economics cannot be assessed purely from energy market revenue in markets that include such mechanisms

### Worked Example

**Example**

A coal plant has the following characteristics:

- Heat rate: 10,000 Btu/kWh (equivalent to 10 MMBtu/MWh)
- Delivered coal price: $2.20/MMBtu
- Variable O&M: $3.00/MWh
- No applicable carbon price in this scenario

Variable fuel cost:

$$10 \times 2.20 = \$22.00/\text{MWh}$$

Total variable cost:

$$22.00 + 3.00 = \$25.00/\text{MWh}$$

If a competing gas combined-cycle plant has a heat rate of 7,000 Btu/kWh and a delivered gas price of $3.50/MMBtu:

$$\text{Gas variable fuel cost} = 7 \times 3.50 = \$24.50/\text{MWh}$$

Assuming similar variable O&M, the gas plant's variable cost ($27.50/MWh assuming $3.00 O&M) would actually be higher in this specific scenario, so the coal plant would dispatch ahead of the gas plant in the merit order. [Inference] If a carbon price of $30/tonne CO2 were introduced, and the coal plant's emissions rate (approximately 1.0 tCO2/MWh for a typical subcritical unit, illustratively) is roughly double the gas plant's (approximately 0.4 tCO2/MWh for a modern combined cycle unit, illustratively), the coal plant's variable cost would rise by roughly $30/MWh versus roughly $12/MWh for the gas plant, which would reverse the relative merit order position in this example—illustrating how carbon pricing can shift dispatch order even when it doesn't apply the same absolute cost increase to both technologies.

### Common Analytical Pitfalls

- Using LCOE alone to compare intermittent renewables against dispatchable coal generation without separately accounting for dispatchability and system integration cost differences
- Assuming capital cost (sunk once built) is relevant to short-run dispatch decisions, when only variable cost determines merit order position for an existing plant
- Ignoring capacity market revenue when assessing coal plant retirement economics in markets where such mechanisms exist, since energy market revenue alone can understate total plant economics
- Treating declining coal capacity factor purely as a policy-driven outcome, when much of the effect in many markets reflects ordinary economic dispatch response to falling renewable and gas variable costs
- Applying a single universal "coal-to-gas switching price" for carbon costs, when the actual switching price is specific to the heat rates and emissions rates of the particular plants being compared

**Related Topics**

- Merit order dispatch modeling and wholesale electricity market design
- Capacity markets and resource adequacy mechanisms
- Carbon pricing mechanisms and coal-to-gas fuel switching dynamics
- Levelized Cost of Electricity (LCOE) methodology and its limitations for dispatchable vs. intermittent technologies
- Coal plant retirement economics and stranded asset risk
- Renewable energy integration costs and their effect on thermal plant capacity factors
- Flue gas desulfurization and other emissions control technology economics