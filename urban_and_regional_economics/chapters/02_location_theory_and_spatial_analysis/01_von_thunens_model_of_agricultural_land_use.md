## Von Thünen's Model of Agricultural Land Use

### Overview and Historical Context

Johann Heinrich von Thünen presented his model in *Der isolierte Staat* ("The Isolated State," 1826), based on empirical observations from his own agricultural estate in Mecklenburg, Germany. It is widely regarded as the first rigorous spatial economic model and the direct theoretical ancestor of modern urban land use theory (via Alonso's later adaptation). Von Thünen sought to explain a pattern he observed empirically: agricultural land uses were arranged in a systematic, distance-dependent pattern around market towns, rather than being randomly distributed or determined solely by soil quality.

### Model Assumptions

Von Thünen constructed a deliberately simplified spatial economy to isolate the pure effect of transport cost on land use, holding all other factors constant:

- A single, isolated market town (the "Isolated State") sits at the center of a large, featureless plain
- The surrounding plain is agriculturally homogeneous: uniform soil fertility, climate, and terrain in all directions
- Transportation occurs overland at a constant cost per unit distance, proportional to both the weight/bulk of the good and the distance traveled (no differentiation by direction — an isotropic plain)
- Farmers are profit-maximizing and choose which crop/activity to produce based on maximizing land rent (not merely revenue)
- There is only one market (the central town) to which all produce must be transported, and all farmers are price-takers in that market
- Farmers compete for land via a land rent (bid-rent) mechanism: land is allocated to whichever use can pay the highest rent at each location

### The Core Analytical Device: Land Rent (Location Rent)

Von Thünen's central insight was to formalize the concept of **location rent** (or "Thünen rent"): the surplus a farmer can afford to pay for land at a given distance from the market, after covering production costs and transport costs, given the market price of the good.

$$R(s) = E(P - C) - E \cdot t \cdot s$$

where:

- $R(s)$ = land rent per unit area at distance $s$ from the market
- $E$ = yield per unit area (output quantity per unit land)
- $P$ = market price per unit of output
- $C$ = production cost per unit of output (excluding transport and rent)
- $t$ = transport cost per unit of output per unit distance
- $s$ = distance from the market/central town

This equation states that rent is the difference between total revenue at the market price and total costs (production plus transport), expressed on a per-unit-of-land basis. As distance $s$ increases, transport costs erode the surplus available to pay as rent, so **rent declines linearly with distance from the market**, reaching zero at the point where transport costs fully absorb the revenue-cost margin — defining the maximum extent of cultivation for that crop.

### The Rent Gradient and Bid-Rent Curves

Each crop or land use generates its own rent gradient — a straight line (under the linear transport cost assumption) with:

- **Intercept** at $s=0$: determined by $E(P-C)$, the profitability per unit of land at the market itself
- **Slope**: determined by $-E \cdot t$, i.e., steeper for crops that are costly to transport per unit of value (bulky, perishable, or low value-to-weight goods) and flatter for crops that are cheap to transport per unit of value (compact, durable, high value-to-weight goods)

Because different agricultural activities have different combinations of intercept and slope, their rent gradients cross at different distances from the center. **The equilibrium land use at each distance is determined by whichever activity has the highest rent gradient at that specific distance** — land is allocated, in effect, through a competitive auction where the highest bidder (in rent terms) wins the location.

### The Resulting Concentric Ring Pattern

Von Thünen derived a sequence of concentric rings (zones) of land use around the central market town, ordered by the interaction of transport cost sensitivity and land/labor intensity. The classic von Thünen sequence, from center outward, was:

1. **Intensive market gardening / dairying**: highly perishable and/or bulky-relative-to-value products (fresh vegetables, milk) requiring proximity to market and high land-intensity of cultivation
2. **Forestry (timber and firewood)**: surprisingly close to the center in von Thünen's original model, since wood was extremely bulky and costly to transport relative to its value in the pre-railroad era, despite low land intensity
3. **Extensive field crops with crop rotation** (e.g., grain-fallow rotation systems): moderate transport cost sensitivity, lower land intensity
4. **Ranching / livestock grazing**: lowest land-intensity, and livestock could partly transport themselves ("on the hoof"), reducing transport cost sensitivity, so this activity could locate furthest from market
5. Beyond the outermost ring: land where no agricultural activity can generate positive rent; the edge of cultivation

The overall pattern is one of **declining land-use intensity with distance from the market**, as measured by capital and labor applied per unit of land, since farmers near the market can afford to intensify production to substitute for costly land, while farmers far from market economize on land but face high per-unit transport costs, favoring low-intensity, land-extensive activities such as grazing.

### Diagram: Von Thünen Rings and Rent Gradients (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 420">
<text x="350" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#222">Von Thünen Model (svg_diagram)</text>
<g transform="translate(160,220)">
<circle r="150" fill="#f4e2b8" stroke="#333" stroke-width="1" />
<circle r="115" fill="#d9e8c4" stroke="#333" stroke-width="1" />
<circle r="80" fill="#a9c98f" stroke="#333" stroke-width="1" />
<circle r="48" fill="#7fa860" stroke="#333" stroke-width="1" />
<circle r="20" fill="#5c7f3f" stroke="#333" stroke-width="1" />
<circle r="4" fill="#222" />
<text x="0" y="-160" text-anchor="middle" font-size="11" fill="#333">Ranching/Grazing</text>
<text x="0" y="-125" text-anchor="middle" font-size="11" fill="#333">Field Crops/Rotation</text>
<text x="0" y="-90" text-anchor="middle" font-size="10" fill="#333">Forestry</text>
<text x="0" y="-55" text-anchor="middle" font-size="9" fill="#fff">Market Garden</text>
<text x="0" y="35" text-anchor="middle" font-size="9" fill="#fff">Town</text>
</g>
<g transform="translate(430,60)">
<line x1="0" y1="280" x2="230" y2="280" stroke="#333" stroke-width="1.5" />
<line x1="0" y1="280" x2="0" y2="20" stroke="#333" stroke-width="1.5" />
<text x="115" y="305" text-anchor="middle" font-size="11" fill="#333">Distance from market (s)</text>
<text x="-15" y="150" text-anchor="middle" font-size="11" fill="#333" transform="rotate(-90,-15,150)">Rent R(s)</text>



```
<line x1="0" y1="40" x2="60" y2="280" stroke="#c0392b" stroke-width="2" />
<line x1="0" y1="90" x2="120" y2="280" stroke="#e67e22" stroke-width="2" />
<line x1="0" y1="150" x2="200" y2="280" stroke="#27ae60" stroke-width="2" />

<text x="65" y="55" font-size="9" fill="#c0392b">Market garden (steep)</text>
<text x="125" y="105" font-size="9" fill="#e67e22">Field crops (medium)</text>
<text x="205" y="165" font-size="9" fill="#27ae60">Ranching (flat)</text>
```

</g>
</svg>

### Formal Determination of Ring Boundaries

The boundary between two adjacent land uses (say, activity A closer to market and activity B farther out) occurs at the distance $s^*$ where their rent gradients intersect:

$$R_A(s^*) = R_B(s^*)$$



$$E_A(P_A - C_A) - E_A t_A s^* = E_B(P_B - C_B) - E_B t_B s^*$$

Solving for $s^*$ gives the precise ring boundary. Beyond $s^*$, activity B generates higher rent than activity A and thus wins the location; before $s^*$, activity A dominates. The overall outer boundary of cultivation is determined similarly, at the point where the outermost viable activity's rent gradient reaches zero.

### Extensions and Relaxations of the Original Assumptions

Von Thünen and subsequent scholars extended the basic model to relax several simplifying assumptions:

- **Navigable rivers**: von Thünen himself noted that a navigable river reduces transport costs along its path, distorting the concentric rings into elongated, river-following zones rather than perfect circles
- **Multiple market towns**: with more than one market, competing rent gradients from each town interact, producing more complex land use boundaries (a precursor to central place theory's multi-center reasoning)
- **Non-uniform (heterogeneous) land quality**: relaxing the assumption of a featureless plain allows soil quality differences to interact with (and sometimes dominate) the pure distance effect
- **Variable transport cost functions**: allowing $t$ to vary by mode (road vs. rail vs. river) or to be non-linear in distance (e.g., reflecting fixed loading/unloading costs plus a linear haul cost) generates curved rather than straight-line rent gradients

### Significance for Later Urban Economic Theory

Von Thünen's rent-gradient logic is the direct conceptual ancestor of the modern **bid-rent function** used in urban economics. William Alonso's 1964 adaptation replaced von Thünen's agricultural crops with urban land uses (households, retail, offices, industry) and replaced "distance to the agricultural market town" with "distance to the central business district (CBD)," while retaining the identical core mechanism: different users generate different rent gradients based on their sensitivity to transport/commuting cost, and land is allocated to the highest bidder at each distance. This transplant of von Thünen's framework into an urban context underlies the Alonso-Muth-Mills monocentric city model, covered in later material in this course.

### Key Points

- Von Thünen's 1826 model is the founding work of location theory, explaining concentric rings of agricultural land use around an isolated market town using a linear transport-cost framework.
- The central analytical device is location (Thünen) rent: $R(s) = E(P-C) - Ets$, which declines linearly with distance from market.
- Land use at each distance is determined by whichever activity's rent gradient is highest there; ring boundaries occur where adjacent rent gradients intersect.
- Activities with steep rent gradients (high transport-cost sensitivity relative to value) locate close to the market; activities with flat gradients (low transport-cost sensitivity) locate farther out.
- The model's rent-gradient logic was directly transplanted into urban economics by Alonso (1964), forming the theoretical foundation of the modern monocentric city model.

### Related Topics

- The Alonso-Muth-Mills monocentric city model
- Bid-rent theory in urban land markets
- Weber's industrial location theory (least-transport-cost location)
- Central place theory (Christaller and Lösch)
- Extensions of von Thünen: rivers, multiple markets, heterogeneous land quality
- Historical applications and empirical tests of the von Thünen model
- Land rent theory in classical economics (Ricardo's differential rent, compared and contrasted)