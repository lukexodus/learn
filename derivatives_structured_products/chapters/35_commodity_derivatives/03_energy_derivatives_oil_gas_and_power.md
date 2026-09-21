## Energy Derivatives Oil Gas and Power


### Overview

Energy derivatives span crude oil, natural gas, and electric power markets, each with distinct physical delivery characteristics, market structures, and pricing complications relative to standard commodity derivatives theory. Power in particular departs radically from the storable-commodity framework due to the physical non-storability of electricity, requiring specialized modeling approaches.

**Key Points**

- Crude oil and natural gas are storable commodities that fit within the extended cost-of-carry framework (storage cost, convenience yield)
- Electric power is fundamentally non-storable (in bulk, at grid scale) at the point of consumption, invalidating standard cost-of-carry pricing and producing extreme, spiky price behavior
- Each energy complex has its own benchmark contracts, delivery mechanics, and dominant risk factors
- Energy derivatives markets are heavily influenced by physical infrastructure constraints (pipeline capacity, storage capacity, transmission grid constraints) in ways more pronounced than most other asset classes

### Crude Oil Derivatives

**Benchmark Contracts**

- **WTI (West Texas Intermediate)**: light, sweet crude; physically delivered at Cushing, Oklahoma; traded on CME/NYMEX; the traditional US benchmark
- **Brent**: North Sea crude; the dominant global benchmark, used to price roughly two-thirds of internationally traded crude oil; traded on ICE; cash-settled against a physical delivery/pricing mechanism combining multiple North Sea crude streams
- **Dubai/Oman**: benchmark for Middle Eastern crude sold into Asian markets, particularly relevant for term contract pricing formulas used by Gulf producers

**Contract Structures**

- **Futures**: standardized exchange-traded contracts (NYMEX WTI, ICE Brent) with monthly expiries extending out multiple years, providing the primary liquid hedging and price discovery vehicle
- **Physical forward markets**: significant volume trades in OTC physical forward markets (e.g., the Brent "cash BFOE" market, Dated Brent), which interact with and inform the exchange-traded futures curve
- **Crack spreads**: derivatives on the spread between crude oil and refined products (gasoline, heating oil/diesel), used by refiners to hedge refining margin risk — e.g., the widely quoted "3-2-1 crack spread" (3 barrels of crude yielding 2 barrels of gasoline and 1 barrel of heating oil, approximating a simplified refinery yield)
- **Differentials and basis swaps**: trade the spread between related crude grades or delivery locations (e.g., WTI-Brent spread, or location differentials like WTI Midland vs. WTI Cushing), reflecting transportation costs, quality differences, and regional supply/demand imbalances

**Key Points**

- The April 2020 negative WTI pricing episode (May 2020 contract settling at approximately -$37/barrel) illustrated the practical importance of physical storage capacity constraints at the Cushing delivery point — when storage capacity approached exhaustion amid collapsing demand, holders of expiring futures contracts with no ability to take physical delivery were forced to pay counterparties to take the oil, a vivid demonstration of how physical delivery mechanics can override simple cost-of-carry intuition
- Crude oil implied volatility and skew are heavily influenced by OPEC+ meeting outcomes, geopolitical supply disruption risk (particularly in the Middle East, Russia, and other major producing regions), and demand-side macro data
- Crude oil options are commonly priced using the Black-76 model (treating the futures price, not spot, as the underlying), consistent with the exchange-traded, futures-referenced nature of most crude oil options

### Natural Gas Derivatives

**Benchmark Contracts**

- **Henry Hub**: the primary US natural gas benchmark, a physical pipeline interchange in Louisiana; NYMEX Henry Hub futures are the dominant exchange-traded US gas contract
- **NBP (National Balancing Point)**: UK/European gas hub benchmark
- **TTF (Title Transfer Facility)**: Dutch virtual trading point, now the dominant continental European gas benchmark, particularly significant in price discovery following the post-2022 shift away from Russian pipeline gas supply to Europe
- **JKM (Japan Korea Marker)**: benchmark for LNG (liquefied natural gas) cargoes delivered into Northeast Asia

**Key Structural Features**

- **Pronounced seasonality**: natural gas demand is strongly seasonal (heating demand in winter, cooling-driven power generation demand in summer in some regions), producing a distinctive seasonal futures curve shape with winter-month premiums, layered on top of the general contango/backwardation dynamic
- **Storage-dependent pricing**: natural gas storage levels (reported weekly in the US via the EIA Weekly Natural Gas Storage Report) are a closely watched driver of near-term price and curve shape, analogous to but generally even more pronounced than the inventory-convenience-yield relationship in oil
- **Basis risk between hubs**: significant price differentials can exist between regional gas hubs due to pipeline transportation capacity constraints, particularly evident during extreme weather events when local demand spikes can cause dramatic regional price dislocations even while other hubs remain stable
- **LNG market integration**: the growth of global LNG trade has increasingly linked previously segmented regional gas markets (US Henry Hub, European TTF, Asian JKM), though full integration remains partial due to liquefaction/regasification capacity constraints and shipping logistics — regional basis differentials between these hubs are actively traded and are a key input to LNG cargo routing decisions

**Weather Derivatives**

A related but distinct instrument class: weather derivatives (heating degree day/cooling degree day-based contracts) allow energy companies and utilities to hedge volumetric risk (demand driven by weather) separately from price risk, since a mild winter reduces both gas demand and typically gas prices, compounding revenue impact for producers/utilities in a way that a pure price hedge does not address.

### Power (Electricity) Derivatives

**Key Points**

- Electric power is **non-storable at grid scale** (with limited exceptions like pumped hydro storage and, increasingly, grid-scale batteries, which remain a small fraction of total grid capacity relative to demand) — supply and demand must be balanced continuously and in real time
- This non-storability fundamentally breaks the standard cost-of-carry pricing framework: there is no meaningful "convenience yield of holding electricity" because electricity cannot be held at all in bulk; instead, power prices are driven by the real-time marginal cost of generation, which can vary enormously and instantaneously
- Power markets exhibit extreme price spikes (sometimes orders of magnitude above typical levels) during periods of tight supply-demand balance (extreme weather, generation outages, transmission constraints), followed by rapid mean reversion once conditions normalize

**Market Structure**

- **Day-ahead and real-time (spot) markets**: most organized power markets (e.g., PJM, ERCOT, CAISO in the US; various ISO/RTO structures elsewhere) clear a day-ahead market based on bids/offers for the following day, with a real-time balancing market settling any deviations
- **Forward and futures markets**: standardized power futures/forwards trade for delivery over future months, quarters, and years, typically referencing a specific delivery hub or zone within a grid
- **Financial Transmission Rights (FTRs) / Congestion Revenue Rights (CRRs)**: instruments that hedge the risk of locational price differences (congestion) arising from transmission constraints between two points on the grid — since power prices can differ significantly by location due to transmission bottlenecks, these instruments are essential for market participants with location-specific generation or load exposure

**Power Price Modeling**

Standard Black-Scholes-style geometric Brownian motion is a poor fit for power prices due to extreme spikes and mean reversion. Common modeling approaches include:

- **Mean-reverting jump-diffusion models**: combine a mean-reverting base process (reflecting normal supply-demand equilibrium dynamics) with a jump component (capturing sudden spikes from outages, extreme weather, or transmission constraints):

$$dP = \kappa(\theta - \ln P)P\,dt + \sigma P\,dW + J\,dq$$

where $\kappa$ is the mean-reversion speed, $\theta$ the long-run log-price level, $J$ the jump size (often modeled with a separate, typically right-skewed distribution reflecting the asymmetric nature of price spikes — spikes up are far more common and extreme than spikes down), and $dq$ a Poisson jump process

- **Regime-switching models**: allow the price process to switch between "normal" and "spike" regimes with different dynamics in each, often better capturing the empirically observed clustering of spike events
- **Structural/fundamental models**: directly model the relationship between power price and the marginal generating unit's cost (the "merit order" — the ordering of generation sources from cheapest to most expensive marginal cost, with the most expensive unit needed to meet demand at any moment setting the clearing price), linking power price behavior to fuel costs (especially natural gas, which is frequently the marginal fuel in many grids) and renewable generation output

**[Inference]** The specific choice among these modeling approaches in practice varies substantially by market, use case (short-term trading vs. long-term asset valuation), and the degree of renewable penetration in a given grid (higher renewable penetration tends to increase price volatility and spike frequency due to weather-dependent, non-dispatchable generation, an increasingly important and actively researched modeling consideration as renewable penetration has grown across many major grids).

### Illustration: Storable vs. Non-Storable Energy Commodity Price Behavior

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 380" font-family="sans-serif">
<text x="350" y="25" text-anchor="middle" font-size="16" font-weight="bold">Price Path Comparison: Crude Oil vs. Power (svg_diagram)</text>
<line x1="60" y1="340" x2="640" y2="340" stroke="black" stroke-width="1.5" />
<line x1="60" y1="340" x2="60" y2="50" stroke="black" stroke-width="1.5" />
<text x="650" y="345" font-size="12">Time</text>
<text x="20" y="45" font-size="12">Price</text>


<path d="M 80,220 C 130,210 160,240 200,230 C 250,215 290,235 340,225 C 390,210 430,230 480,220 C 530,205 570,225 610,215" fill="none" stroke="`#2980b9`" stroke-width="2.5" />

<text x="500" y="195" font-size="12" fill="`#2980b9`">Crude Oil (storable, smoother)</text>



<path d="M 80,310 L 120,305 L 140,300 L 160,90 L 175,300 L 220,295 L 250,290 L 270,120 L 285,290 L 340,285 L 380,280 L 400,60 L 415,280 L 470,275 L 520,270 L 540,150 L 555,270 L 610,265" fill="none" stroke="`#c0392b`" stroke-width="2" />

<text x="420" y="80" font-size="12" fill="`#c0392b`">Power (spikes on tight supply/demand)</text>

<text x="80" y="330" font-size="11" fill="`#7f8c8d`">Both driven by fundamentals, but power lacks storage to smooth shocks</text>

</svg>

### Comparative Summary Table

| Characteristic | Crude Oil | Natural Gas | Power |
| --- | --- | --- | --- |
| Storability | Storable (tanks, pipelines) | Storable (underground storage) | Effectively non-storable at scale |
| Primary benchmark(s) | WTI, Brent | Henry Hub, TTF, JKM | Hub/zone-specific (e.g., PJM West) |
| Dominant curve driver | Global supply/demand, OPEC+, geopolitics | Seasonality, storage levels | Weather, generation mix, transmission constraints |
| Typical volatility character | Moderate, occasional large moves | Seasonal + event-driven spikes | Extreme spikes, fast mean reversion |
| Standard option model | Black-76 | Black-76 | Mean-reverting jump-diffusion / regime-switching |
| Key structural risk | Storage capacity constraints (e.g., Cushing) | Pipeline/hub basis, storage capacity | Transmission congestion, generation outages |

### Cross-Commodity Relationships and Spread Products

**Key Points**

- **Spark spread**: the spread between power price and the cost of natural gas required to generate that power (accounting for a generator's heat rate — the efficiency of converting fuel to electricity), used by power generators to hedge or value gas-fired generation assets; a key input to valuing generation capacity as a real option on the spark spread
- **Dark spread**: analogous spread for coal-fired generation (power price minus coal cost, adjusted for plant efficiency)
- **Crack spread** (as noted above): refining margin spread between crude oil and refined products
- These spread products are central to how energy companies value and hedge physical assets (power plants, refineries) as effectively being long optionality on the relevant spread, since a generator can choose not to run when the spread is unprofitable — motivating the common treatment of generation/refining assets as real options in valuation models

### Regulatory and Market Structure Considerations

**Key Points**

- Power markets are typically organized under Independent System Operator (ISO) or Regional Transmission Organization (RTO) structures with centralized market clearing, distinct from the more decentralized OTC-plus-exchange structure common in oil and gas
- Position limits, reporting requirements, and market manipulation surveillance (e.g., under Dodd-Frank/CFTC oversight in the US for energy derivatives) are particularly significant in energy markets given historical episodes of manipulation (e.g., the Enron-era California power crisis of 2000–2001, and subsequent regulatory reforms)
- Physical settlement obligations and delivery mechanics (pipeline nomination procedures for gas, physical delivery logistics for oil, real-time grid balancing for power) introduce operational complexity in energy derivatives that is less prominent in purely cash-settled financial derivatives markets

### Worked Example: Spark Spread

A gas-fired power plant with a heat rate of 7.5 MMBtu/MWh (i.e., it requires 7.5 million BTU of natural gas to generate one megawatt-hour of electricity) is evaluating whether to run given:

- Power price: $45/MWh
- Natural gas price: $4.00/MMBtu

**Spark spread calculation**:

$$\text{Spark Spread} = P_{power} - (\text{Heat Rate} \times P_{gas}) = 45 - (7.5 \times 4.00) = 45 - 30 = \$15/\text{MWh}$$

A positive spark spread of $15/MWh indicates the plant can profitably run (covering fuel costs with a positive margin before other variable costs). If natural gas prices rose to $7.00/MMBtu with power price unchanged, the spark spread would turn negative ($45 - 52.5 = -\$7.50$/MWh), and a rational operator would choose not to dispatch the plant — illustrating the real-option character of generation assets, where the plant operator holds the right (not obligation) to convert fuel into power only when economically favorable.

### Related Topics

**Related Topics**

- Storage Cost and Convenience Yield in Commodity Pricing
- Commodity Futures Curves: Contango and Backwardation
- Black-76 Model for Commodity and Energy Options
- Mean-Reverting Jump-Diffusion Models for Power Price Simulation
- Financial Transmission Rights and Congestion Risk Management
- Weather Derivatives and Volumetric Risk Hedging
- Real Option Valuation of Generation and Refining Assets