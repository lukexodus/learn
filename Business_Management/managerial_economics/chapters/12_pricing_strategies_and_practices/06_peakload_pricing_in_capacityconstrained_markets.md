## Peak-Load Pricing in Capacity-Constrained Markets

### Definition and Core Concept

**Peak-load pricing** is a pricing strategy in which a firm charges different prices at different points in time based on fluctuations in demand, specifically to reflect the higher effective marginal cost of serving customers during periods of peak demand when production capacity is fixed and scarce. It is a specific application of third-degree price discrimination where the segmentation variable is *time* rather than customer type, but it has a distinct economic foundation rooted in **capacity constraints** rather than purely in differing elasticities.

- Applies primarily to goods and services that **cannot be stored** (non-storable output) and where **production capacity is fixed in the short run** — classic examples include electricity, telecommunications networks, transportation, and hospitality
- The central problem: demand varies predictably across time (time of day, day of week, season), but building enough capacity to meet peak demand at the same low cost as off-peak demand would require costly excess capacity that sits idle during off-peak periods

### Why Ordinary Marginal Cost Pricing Is Insufficient

**Key Points**

- In a market with a storable good, marginal cost pricing at all times simply reflects the cost of producing one more unit
- In a capacity-constrained, non-storable market, marginal cost during **off-peak** periods is just the short-run variable cost of production (since spare capacity exists)
- During **peak** periods, once capacity is fully utilized, the true marginal cost of serving one additional unit of demand includes not just variable production cost but also the **opportunity cost of capacity** — because serving that extra peak-period customer requires either turning away another customer or, in the long run, expanding capacity
- Peak-load pricing theory therefore separates the **cost of capacity** from the **cost of variable operation**, and allocates the capacity cost specifically to peak-period users, since it is peak demand — not off-peak demand — that drives the need for that capacity in the first place

### Formal Model: Two-Period Peak-Load Pricing

Consider a firm serving two demand periods (peak and off-peak) with capacity $K$ that must be built once and used in both periods. Let:

- $b$ = short-run marginal (variable/operating) cost per unit, assumed constant in both periods
- $\beta$ = marginal capacity cost per unit of capacity (the cost of building one more unit of capacity, e.g., annualized cost of a generating plant)
- $D_p(p)$ = demand in the peak period
- $D_o(p)$ = demand in the off-peak period

**Case 1: Off-peak demand does not strain existing peak-driven capacity (the "firm peak" case)**

If off-peak demand is low enough that it does not require any additional capacity beyond what peak demand already necessitates, the efficient pricing rule is:

$$p_{peak} = b + \beta$$



$$p_{off\text{-}peak} = b$$

Peak users pay the full capacity cost $\beta$ on top of variable cost $b$, because it is peak demand alone that determines how much capacity must be built. Off-peak users pay only variable cost, since serving them requires no additional capacity — they use capacity that already exists to meet peak needs.

**Case 2: Both periods contribute to capacity needs (the "shifting peak" case)**

If off-peak demand is high enough that, after peak users are charged $p_{peak} = b + \beta$, off-peak demand at price $b$ would itself exceed available capacity, then both periods must share the capacity cost. The efficient solution requires solving simultaneously such that capacity is exactly sufficient to meet the higher of the two resulting demands, with the capacity charge $\beta$ allocated between periods according to:

$$D_p(p_{peak}) + D_o(p_{off\text{-}peak}) \text{ consistent with capacity } K$$

and typically:

$$p_{peak} = b + \beta_p, \quad p_{off\text{-}peak} = b + \beta_o, \quad \beta_p + \beta_o = \beta$$

[Inference] The exact split of $\beta$ between periods in the shifting-peak case depends on the specific demand functions in each period; there is no single universal formula independent of the demand curves, and solving it requires iterating to check which period(s) bind on capacity at the resulting equilibrium prices.

### Numeric Illustration (Firm Peak Case)

Suppose an electric utility has:

- Variable cost $b = \$0.05$ per kWh
- Capacity cost $\beta = \$0.03$ per kWh (annualized cost of generating capacity per unit)
- Peak demand: $D_p(p) = 1000 - 2000p$
- Off-peak demand: $D_o(p) = 400 - 2000p$

Setting $p_{peak} = b + \beta = 0.05 + 0.03 = \$0.08$:

$$D_p(0.08) = 1000 - 2000(0.08) = 1000 - 160 = 840 \text{ kWh}$$

Setting $p_{off\text{-}peak} = b = \$0.05$:

$$D_o(0.05) = 400 - 2000(0.05) = 400 - 100 = 300 \text{ kWh}$$

Since $300 < 840$, off-peak demand at marginal cost does not exceed the capacity of $840$ kWh already required for peak, confirming this is a firm-peak case and the pricing rule above is efficient — off-peak users free-ride on capacity built for peak demand and correctly pay only variable cost.

### Diagrammatic Representation

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 440" font-family="Arial, sans-serif">
<text x="400" y="24" text-anchor="middle" font-size="16" font-weight="bold">Peak-Load Pricing: Firm Peak Case (svg_diagram)</text>
<line x1="80" y1="380" x2="80" y2="60" stroke="black" stroke-width="1.5" />
<line x1="80" y1="380" x2="700" y2="380" stroke="black" stroke-width="1.5" />
<text x="45" y="65" font-size="12">Price</text>
<text x="660" y="398" font-size="12">Quantity</text>

<line x1="480" y1="380" x2="480" y2="70" stroke="black" stroke-width="1.5" stroke-dasharray="2,2" />
<text x="460" y="65" font-size="11">Capacity K</text>

<line x1="120" y1="90" x2="600" y2="380" stroke="#dc2626" stroke-width="2" />
<text x="605" y="380" font-size="11" fill="#dc2626">D_peak</text>

<line x1="80" y1="230" x2="330" y2="380" stroke="#2563eb" stroke-width="2" />
<text x="335" y="380" font-size="11" fill="#2563eb">D_off-peak</text>

<line x1="80" y1="330" x2="700" y2="330" stroke="#16a34a" stroke-width="2" stroke-dasharray="5,3" />
<text x="705" y="333" font-size="11" fill="#16a34a">b (variable cost)</text>

<line x1="80" y1="200" x2="700" y2="200" stroke="#9333ea" stroke-width="2" stroke-dasharray="5,3" />
<text x="705" y="203" font-size="11" fill="#9333ea">b + β (peak price)</text>

<circle cx="480" cy="200" r="4" fill="#dc2626" />
<circle cx="330" cy="330" r="4" fill="#2563eb" />

<text x="400" y="420" text-anchor="middle" font-size="11" font-style="italic">Peak users pay b + β and consume exactly at capacity; off-peak users pay only b</text>

</svg>

### Real-World Applications

#### Electricity Pricing

- **Example:** Time-of-use (TOU) electricity rates charging higher per-kWh prices during afternoon/early-evening peak demand hours and lower rates overnight; critical-peak pricing programs that impose sharply elevated prices on a small number of forecasted highest-demand days per year
- Utility regulators in many jurisdictions have promoted TOU and dynamic pricing programs partly on peak-load pricing efficiency grounds, though implementation details, rate structures, and regulatory frameworks vary substantially by jurisdiction and change over time [Unverified — specific current program details should be checked against the relevant utility or regulator]

#### Transportation

- **Example:** Airlines' fare differentials tied partly to time-of-booking and travel-date proximity to holidays (though this overlaps with elasticity-based third-degree discrimination); public transit systems charging higher fares during weekday rush-hour periods than off-peak or weekend periods; congestion pricing/road tolls that vary by time of day (e.g., higher tolls during morning and evening commute windows)

#### Telecommunications

- **Example:** Historic long-distance telephone pricing with lower rates during evening and weekend "off-peak" hours when network capacity utilization was lower

#### Hospitality and Leisure

- **Example:** Hotel room rates that rise during high-occupancy seasons or event weekends when the fixed number of rooms constrains supply; movie theater matinee pricing reflecting lower afternoon demand relative to evening peak demand

#### Ride-Sharing "Surge" Pricing

- **Example:** Dynamic per-trip pricing that rises when the ratio of ride requests to available drivers increases sharply, functioning as a real-time analog of peak-load pricing by allocating a scarce, non-storable capacity (available driver-time) to the highest-value trips during a demand spike

### Distinguishing Peak-Load Pricing from General Third-Degree Discrimination

| Feature | Peak-Load Pricing | General Third-Degree Discrimination |
| --- | --- | --- |
| Segmentation basis | Time period (peak vs. off-peak) | Any observable group characteristic |
| Underlying cost driver | Capacity scarcity at peak times | Not necessarily cost-related; based on elasticity |
| Storable good? | Typically non-storable output | Can apply to storable or non-storable goods |
| Efficiency framing | Often argued to be allocatively efficient (aligns price with true marginal cost including capacity) | Ambiguous welfare effect relative to uniform pricing |

### Welfare and Efficiency Considerations

**Key Points**

- Because peak-load pricing (in its idealized form) charges each period a price equal to the true marginal cost of serving that period — including the capacity cost attributable to peak demand — it is often presented in the economics literature as **allocatively efficient**, in contrast to general third-degree discrimination, which has ambiguous welfare effects
- Efficient peak-load pricing sends the correct signal for **long-run capacity investment decisions**: if peak demand grows enough that $\beta$ revenue collected from peak users justifies building additional capacity, the firm (or regulator, in regulated industries) has the correct price signal to expand capacity
- [Inference] Real-world peak-load pricing schemes rarely implement the idealized two-period model exactly; actual tariff design must account for metering costs, customer comprehension and acceptance, regulatory constraints, and the administrative complexity of multi-period rate structures, all of which can cause deviations from the theoretically efficient prices derived above

### Common Pitfalls and Practical Limitations

- **Demand forecasting error:** The model assumes the firm can accurately predict peak and off-peak demand curves in advance to size capacity correctly; forecasting errors can lead to under- or over-investment in capacity
- **Consumer acceptance and comprehension:** Time-varying prices can be confusing or perceived as unfair by consumers accustomed to flat-rate pricing, generating political and regulatory resistance in some contexts, particularly in essential-service markets like electricity and water [Inference]
- **Metering/technology requirements:** Effective peak-load pricing requires the ability to measure consumption by time period (e.g., smart meters for electricity), which entails infrastructure investment not required under flat-rate billing
- **Shifting-peak complexity:** In the shifting-peak case, if pricing successfully shifts enough demand from peak to off-peak, the off-peak period can itself become the new binding constraint on capacity, requiring iterative or dynamic re-optimization of the price structure over time

### Related Topics

- Price discrimination strategies (first-, second-, and third-degree)
- Two-part tariffs and multi-part pricing
- Marginal cost pricing and short-run vs. long-run cost curves
- Capacity planning and investment decisions under demand uncertainty
- Congestion pricing and externalities in transportation economics
- Dynamic/algorithmic pricing systems