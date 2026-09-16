## Economic Effects of Zoning Restrictions

### Analytical Framework

Zoning restrictions affect urban economic outcomes through several distinct but interacting channels: housing supply elasticity, land price capitalization, spatial sorting of households by income, labor market access, and aggregate productivity via agglomeration constraints. This section treats each channel systematically, distinguishing well-established theoretical mechanisms from empirically contested magnitudes.

### Channel 1: Supply Elasticity and Price Effects

**Mechanism**: Binding zoning constraints (height limits, FAR caps, minimum lot sizes, density ceilings) place a ceiling on the quantity of housing units producible on a given land area, independent of market demand. This flattens the long-run housing supply curve at lower quantities than an unconstrained market would produce.

Standard urban housing supply model:

$$Q_s = f(P, K, L, Z)$$

where $Q_s$ is housing quantity supplied, $P$ is price, $K$ is capital input, $L$ is land, and $Z$ is the binding regulatory constraint. When $Z$ binds below the unconstrained equilibrium quantity $Q^*$, the market clears at a higher price $P_1 > P^*$ and lower quantity $Q_1 < Q^*$.

**Graphical representation (described)**: An inward-shifted or steepened supply curve intersecting an unchanged demand curve produces a new equilibrium with higher price and lower quantity than the unconstrained case; the vertical distance between the constrained equilibrium price and the marginal cost of construction at that quantity represents the implicit regulatory tax, often denoted $Z$ in the literature (Glaeser, Gyourko, and Saks, 2005; Gyourko and Molloy, 2015).

$$Z = P_{market} - MC_{construction}$$

[Inference] Empirically estimated values of $Z$ vary widely by metro area, time period, and methodology (e.g., comparing land price per unit of buildable floor area against physical construction cost, or using "regulatory index" survey instruments like the Wharton Residential Land Use Regulatory Index). Specific dollar or percentage figures from any single study should be treated as time-bound estimates, not structural constants.

**Elasticity terminology**:

- **Housing supply elasticity** ($\epsilon_s$): the percentage change in quantity supplied per percentage change in price. Highly regulated metros (e.g., coastal California cities) are consistently found in the literature to exhibit lower $\epsilon_s$ than less-regulated metros (e.g., much of the Sun Belt), meaning demand shocks translate more into price appreciation than quantity expansion.

$$\epsilon_s = \frac{\%\Delta Q_s}{\%\Delta P}$$

### Channel 2: Land Value Capitalization

Zoning restrictions capitalize into land value because development rights themselves become the scarce, tradable asset rather than a byproduct of raw land value. This produces observable phenomena:

- **Discontinuous land value at zoning boundaries**: A parcel zoned for high-density multi-family use is empirically found to command a substantially higher per-square-foot land price than an observationally similar adjacent parcel zoned single-family only, holding location constant — this "zoning boundary" price gap is a standard empirical technique (regression discontinuity design) used to estimate the value of relaxed development rights.
- **Air rights and FAR markets**: In jurisdictions with transferable development rights (TDR) programs (e.g., New York City), unused floor-area entitlements themselves become a distinct, separately priced asset, evidencing that the FAR restriction — not merely the physical land — carries independent economic value.

### Channel 3: Household Sorting and Segregation

**Tiebout sorting interaction**: [Inference — a well-established theoretical extension of Tiebout's 1956 model, though its predictive precision for any specific jurisdiction is an empirical question] Under a Tiebout framework, households sort across jurisdictions based on preferred bundles of local public goods and tax rates. Exclusionary zoning (large-lot minimums, prohibition of multi-family and manufactured housing) raises the minimum entry cost to a jurisdiction, filtering out lower-income households regardless of their preferences for that jurisdiction's public goods bundle. This converts a preference-based sorting mechanism into an income-based exclusion mechanism.

**Consequences documented in the empirical literature**:

- Income and racial segregation across municipal boundaries within metro areas, exceeding what preference heterogeneity alone would predict
- Reduced intergenerational economic mobility in metro areas with more fragmented, restrictively zoned jurisdictions (Chetty and Hendren's "Opportunity Atlas" research is frequently cited in this context, though causal attribution specifically to zoning versus broader neighborhood effects remains an active research question) [Inference]
- School quality stratification, since school funding is frequently tied to local property tax bases in the U.S. context, and zoning-driven income sorting concentrates tax base disparities geographically

### Channel 4: Labor Market and Agglomeration Effects

**Spatial mismatch and commuting costs**: Restrictive zoning near high-productivity employment centers pushes lower- and middle-income workers into longer commutes, imposing both direct transportation costs and time costs (with associated opportunity cost of foregone labor or leisure).

**Aggregate output effects**: [Inference — this is a prominent but debated finding in the urban/regional economics literature, sensitive to model specification] Hsieh and Moretti (2019) estimate that housing supply constraints in high-productivity U.S. cities (particularly New York, San Francisco, San Jose) caused substantial U.S. aggregate GDP losses by preventing labor from relocating to its most productive geographic use, as workers priced out of high-wage/high-productivity metros instead locate in lower-productivity metros. Their central estimate suggested aggregate growth could have been materially higher (some estimates cited in the low double-digit percentage range over decades) absent these constraints — however, this finding rests on specific assumptions about labor mobility elasticity and production function specification, and subsequent literature has debated the magnitude.

The underlying mechanism can be represented as a spatial equilibrium condition:

$$w_i - r_i - c_i = \bar{u}$$

where $w_i$ is the nominal wage in city $i$, $r_i$ is housing cost, $c_i$ is commuting/amenity cost, and $\bar{u}$ is the reservation utility level equalized across cities in equilibrium. When $r_i$ is artificially inflated by supply constraints in high-wage cities, fewer workers migrate there than the unconstrained productivity-maximizing allocation would imply, since the equalizing condition is reached through under-migration rather than through supply-driven price adjustment.

### Channel 5: Fiscal and Public Finance Effects

**Property tax base effects**: Zoning that favors detached single-family housing over multi-family development produces lower assessed value per acre than denser development, given typical valuation methods, reducing the property tax revenue a jurisdiction can extract from a given land area — a consideration increasingly cited in municipal finance analyses of "fiscal productivity" of different zoning patterns (e.g., work associated with Strong Towns and related municipal finance literature). [Unverified as a universal claim — highly dependent on local assessment methodology and market conditions; some high-value single-family districts generate substantial per-acre tax revenue due to high land values, so this is not a strict ranking across all contexts]

**Infrastructure cost effects**: Low-density zoning mandates (large lot minimums) increase the linear feet of roads, water, and sewer infrastructure required to serve a given population, raising per-capita infrastructure capital and maintenance costs — a widely cited empirical regularity in municipal infrastructure cost studies, though exact multipliers are context-dependent. [Inference for specific multipliers]

### Summary Table: Directional Effects of Restrictive Zoning

| Outcome variable | Effect of tighter restriction | Confidence level |
| --- | --- | --- |
| Housing price level | Increase | Well-established |
| Housing supply elasticity | Decrease | Well-established |
| Land value per buildable unit | Increase (development rights become scarce asset) | Well-established |
| Income segregation across jurisdictions | Increase | Well-established, moderate-to-strong empirical support |
| Commute times for lower-income workers | Increase | Moderate empirical support |
| Aggregate metro/national productivity | Decrease (in high-productivity constrained metros) | Debated magnitude, directionally supported |
| Property tax base per acre | Ambiguous/context-dependent | Mixed evidence |
| Homeownership rate among incumbent residents | Increase (via price appreciation/wealth effect) | Moderate support, but distributionally uneven |

### Distributional Considerations

The economic effects of zoning restriction are not distributionally neutral:

- **Incumbent homeowners** in restrictively zoned areas benefit from asset appreciation, creating a political-economy feedback loop in which homeowner-majority local electorates have a financial incentive to maintain restrictive zoning (sometimes termed "homevoter hypothesis," associated with William Fischel's work).
- **Renters and prospective entrants** bear the cost of higher prices without offsetting capital gains, and are disproportionately affected by supply constraints since they cannot substitute into ownership-based wealth accumulation.
- **Low-income and minority households** are disproportionately affected by both the direct price effects and the historical legacy of exclusionary zoning design discussed in the linked zoning ordinance topic.

### Illustrative Diagram: Supply-Demand Effect of Binding Zoning Constraint (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 600 420">
<text x="300" y="25" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Effect of Binding Zoning Constraint on Housing Market (svg_diagram)</text>

<line x1="80" y1="370" x2="560" y2="370" stroke="#333" stroke-width="2" />
<line x1="80" y1="370" x2="80" y2="50" stroke="#333" stroke-width="2" />
<text x="320" y="400" text-anchor="middle" font-size="13" fill="#333">Quantity of Housing (Q)</text>
<text x="30" y="210" text-anchor="middle" font-size="13" fill="#333" transform="rotate(-90 30 210)">Price (P)</text>

<line x1="140" y1="340" x2="480" y2="90" stroke="#2166ac" stroke-width="2.5" />
<text x="490" y="85" font-size="12" fill="#2166ac" font-weight="bold">S (unconstrained)</text>

<line x1="150" y1="80" x2="480" y2="330" stroke="#b2182b" stroke-width="2.5" />
<text x="490" y="335" font-size="12" fill="#b2182b" font-weight="bold">D</text>

<line x1="300" y1="370" x2="300" y2="60" stroke="#4d9221" stroke-width="2.5" stroke-dasharray="6,4" />
<text x="305" y="65" font-size="12" fill="#4d9221" font-weight="bold">Zoning Cap (Z)</text>

<circle cx="345" cy="205" r="5" fill="#333" />
<text x="352" y="200" font-size="11" fill="#333">E* (unconstrained)</text>
<line x1="345" y1="205" x2="345" y2="370" stroke="#999" stroke-width="1" stroke-dasharray="3,3" />
<line x1="80" y1="205" x2="345" y2="205" stroke="#999" stroke-width="1" stroke-dasharray="3,3" />
<text x="345" y="385" text-anchor="middle" font-size="11" fill="#333">Q*</text>
<text x="65" y="209" text-anchor="end" font-size="11" fill="#333">P*</text>

<circle cx="300" cy="245" r="5" fill="#4d9221" />
<text x="240" y="240" font-size="11" fill="#4d9221">E1 (constrained)</text>
<line x1="300" y1="245" x2="80" y2="245" stroke="#999" stroke-width="1" stroke-dasharray="3,3" />
<text x="65" y="249" text-anchor="end" font-size="11" fill="#333">P1</text>
<text x="300" y="385" text-anchor="middle" font-size="11" fill="#333">Q1</text>

<line x1="300" y1="245" x2="300" y2="205" stroke="#000" stroke-width="3" />
<text x="320" y="228" font-size="11" fill="#000" font-weight="bold">Implicit</text>
<text x="320" y="240" font-size="11" fill="#000" font-weight="bold">zoning tax (Z)</text>
</svg>

### Worked Example: Estimating the Implicit Zoning Tax

**Scenario**: A regression discontinuity study compares land parcels on either side of a zoning boundary in an otherwise homogeneous neighborhood.

**Key Points**:

- Parcel A (zoned for 4-unit multi-family): land value = $800,000, buildable units = 4 → $200,000/unit land cost
- Parcel B (zoned single-family only, otherwise identical location): land value = $500,000, buildable units = 1 → $500,000/unit land cost
- If physical construction cost per unit is approximately $150,000 in both cases, the implicit zoning tax on Parcel B's unit is: $500,000 + $150,000 = $650,000 total cost, versus a market-clearing owner-occupied price benchmark elsewhere in the region (say $400,000) — the gap indicates the restriction's binding value

**Conclusion**: This type of boundary-discontinuity estimation is a standard applied technique for isolating the causal price effect of a specific zoning restriction, netting out unobserved neighborhood quality that would otherwise confound simple cross-sectional price comparisons.

[Inference] Figures above are constructed for pedagogical illustration; real RD estimates from the literature (e.g., studies using Chicago, Los Angeles, or Cambridge MA zoning boundaries) report actual coefficients and standard errors specific to their datasets.

### Related Topics

- Housing supply elasticity estimation (Saiz 2010 geographic constraints methodology)
- Land value taxation as an alternative/complement to zoning
- Regression discontinuity design in urban economics
- Tiebout model and local public finance
- Spatial equilibrium models of city systems (Rosen-Roback framework)
- Homevoter hypothesis and local political economy of land use
- Housing filtering and the economics of the existing housing stock
- Rent control interactions with zoning-constrained supply