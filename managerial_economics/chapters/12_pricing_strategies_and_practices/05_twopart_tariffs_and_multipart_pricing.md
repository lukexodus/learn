## Two-Part Tariffs and Multi-Part Pricing

### Definition and Structure

A **two-part tariff** is a pricing scheme in which customers pay a fixed fee for the right to purchase a good or service, plus a separate per-unit (usage-based) price for each unit actually consumed. The general form is:

$$T(q) = A + pq$$

where $T(q)$ is total payment, $A$ is the fixed access/membership fee, $p$ is the per-unit usage price, and $q$ is the quantity consumed. **Multi-part pricing** (or non-linear pricing more broadly) generalizes this structure to more than two components — for example, a fixed fee plus multiple usage tiers each with a different marginal price, or a fixed fee plus per-unit pricing plus additional premium add-on charges.

### Economic Rationale

**Key Points**

- A two-part tariff allows a firm with market power to extract consumer surplus through the fixed fee $A$ while still setting the usage price $p$ closer to marginal cost $MC$ to encourage efficient consumption
- This structure separates the **participation decision** (whether to buy access at all, governed by $A$) from the **consumption decision** (how much to use, governed by $p$), allowing the firm to price each margin differently
- Under classic two-part tariff theory with a single, known consumer type, the profit-maximizing solution sets $p = MC$ (efficient marginal pricing, maximizing the total surplus available) and sets $A$ equal to the entire remaining consumer surplus at that price — effectively replicating the outcome of first-degree price discrimination for a homogeneous consumer population

### Formal Model: Single Consumer Type

If a monopolist knows a representative consumer's demand curve $q(p)$ and marginal cost is constant at $MC$, the profit-maximizing two-part tariff sets:

$$p^* = MC$$



$$A^* = \text{Consumer Surplus at } p = MC = \int_{MC}^{\infty} q(p)\, dp$$

Total profit per consumer becomes:

$$\pi = A^* + (p^* - MC)q(p^*) = A^*$$

since the usage margin contributes zero profit when $p^* = MC$; all profit is extracted through the fixed fee. This result illustrates why, absent heterogeneity across consumers, a monopolist prefers to price usage efficiently and capture surplus via the entry fee rather than marking up the per-unit price.

### Formal Model: Heterogeneous Consumers

When the firm faces multiple consumer types with different demand intensities (e.g., high-demand and low-demand customers) and cannot distinguish between them, setting $A$ equal to the full surplus of the high-demand type would cause low-demand types to opt out entirely. The firm therefore faces a trade-off:

- **Set $A$ high** (capturing full surplus from the high type) and sacrifice the low type's participation, losing that segment's profit contribution entirely
- **Set $A$ lower** (equal to the low type's surplus) so that both types participate, sacrificing some rent from the high type but keeping the low type's business
- The optimal solution typically involves setting $p$ **above marginal cost** in the presence of heterogeneous consumers, because raising $p$ above $MC$ allows the firm to indirectly extract more surplus from high-demand consumers (who consume more units and are thus more sensitive to $p$) while adjusting $A$ downward to retain low-demand consumers — a form of **screening** similar in spirit to second-degree price discrimination

[Inference] The precise optimal combination of $A$ and $p$ in the heterogeneous-consumer case depends on the specific distribution of consumer types and the shape of each type's demand curve; no single "textbook" ratio between $A$ and $p$ applies universally across all such markets.

### Numeric Illustration

Suppose a fitness club has two customer types with linear demand for visits per month:

- **Type H (heavy user):** $q_H = 20 - p$
- **Type L (light user):** $q_L = 10 - p$

with $MC = \$0$ per visit and equal numbers of each type.

If the firm sets $p = 0$ (marginal cost pricing) for both types:

- Type H surplus $= \frac{1}{2}(20)(20) = \$200$
- Type L surplus $= \frac{1}{2}(10)(10) = \$50$

Setting $A = \$200$ excludes Type L entirely (profit $= \$200$ from Type H only, assuming one customer of each type: total $= \$200$).

Setting $A = \$50$ captures both types (total $= \$50 \times 2 = \$100$, but plus any usage profit if $p > 0$ is introduced).

**Example:** If the firm instead raises $p$ modestly above zero and lowers $A$, it can often achieve a higher combined total than either corner solution — this is the essence of the heavy-user/light-user tension that real gyms, mobile carriers, and utilities must solve when designing tariff structures. [Inference] The exact profit-maximizing $(A, p)$ pair for this illustrative numeric example requires solving the firm's optimization problem explicitly with a specified distribution of types; it is not derived here as a closed-form solved value, and real firms typically calibrate empirically using observed usage-price sensitivity.

### Diagrammatic Representation of the Trade-Off

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 420" font-family="Arial, sans-serif">
<text x="350" y="24" text-anchor="middle" font-size="16" font-weight="bold">Two-Part Tariff Trade-Off with Heterogeneous Demand (svg_diagram)</text>

<line x1="80" y1="360" x2="80" y2="60" stroke="black" stroke-width="1.5" />
<line x1="80" y1="360" x2="600" y2="360" stroke="black" stroke-width="1.5" />
<text x="45" y="65" font-size="12">Price (p)</text>
<text x="560" y="378" font-size="12">Quantity (q)</text>

<line x1="80" y1="90" x2="480" y2="360" stroke="#dc2626" stroke-width="2" />
<text x="485" y="360" font-size="11" fill="#dc2626">D_H (heavy user)</text>

<line x1="80" y1="220" x2="280" y2="360" stroke="#2563eb" stroke-width="2" />
<text x="285" y="360" font-size="11" fill="#2563eb">D_L (light user)</text>

<line x1="80" y1="360" x2="600" y2="360" stroke="#16a34a" stroke-width="2" stroke-dasharray="5,3" />
<text x="605" y="363" font-size="11" fill="#16a34a">MC = 0</text>

<polygon points="80,90 80,360 480,360" fill="#dc2626" fill-opacity="0.12" />
<polygon points="80,220 80,360 280,360" fill="#2563eb" fill-opacity="0.20" />

<text x="150" y="150" font-size="11" fill="`#dc2626`">CS_H (large)</text>

<text x="110" y="280" font-size="11" fill="`#2563eb`">CS_L (small)</text>

<text x="350" y="400" text-anchor="middle" font-size="11" font-style="italic">Setting A = CS_H excludes light users; setting A = CS_L forgoes rent from heavy users</text>

</svg>

### Real-World Applications

#### Membership/Club Pricing

- **Example:** Warehouse retail clubs (annual membership fee plus per-item prices at the store), golf club membership dues plus greens fees per round, amusement park season passes plus optional per-ride charges at some parks

#### Utility Pricing

- **Example:** Electricity and water bills combining a fixed monthly connection/service charge with a per-kWh or per-gallon usage rate; landline or mobile phone plans historically combining a fixed monthly fee with per-minute or per-message overage charges

#### Software and SaaS Licensing

- **Example:** A SaaS platform charging a fixed monthly subscription fee for platform access plus metered/usage-based charges for API calls, storage, or compute consumed beyond an included allotment

#### Car Rental and Equipment Leasing

- **Example:** A base daily rental rate plus a per-mile charge beyond an included mileage allowance

### Multi-Part (Block) Tariffs

Beyond the simple two-part structure, many real-world tariffs use **multiple usage blocks**, each with a different marginal price — a generalization sometimes called **block pricing** or **declining/increasing block tariffs**.

- **Declining block pricing:** Marginal price falls as consumption rises within defined blocks (e.g., the first 100 kWh priced at rate $p_1$, the next 100 kWh at a lower rate $p_2$), often used historically to encourage industrial usage or reflect genuine scale economies in supply
- **Increasing block pricing (inverted block pricing):** Marginal price rises as consumption rises, often used by utilities for water or electricity to encourage conservation, with a low "lifeline" rate for basic needs and higher rates for discretionary high-volume use
- **Example:** Many municipal water utilities charge a low per-unit rate for the first tier of monthly usage (covering basic household needs) and progressively higher per-unit rates for additional usage tiers, both to fund fixed infrastructure costs via the tiered structure and to incentivize conservation

### Two-Part Tariffs and Price Discrimination

**Key Points**

- A uniform two-part tariff (same $A$ and $p$ offered to all customers) is a form of pricing that, in the heterogeneous-consumer case, functions similarly to second-degree price discrimination: the firm cannot directly observe customer type, but the combination of fixed fee and usage price causes different types to end up paying different *effective average prices* per unit depending on how much they consume
- A **menu of two-part tariffs** (e.g., multiple SaaS plans, each with a different combination of fixed fee and included/marginal usage pricing) allows customers to self-select into the tariff structure best suited to their usage intensity — directly analogous to the versioning/self-selection logic of second-degree discrimination discussed under bundling and tiered pricing strategies

### Distinguishing Two-Part Tariffs from Related Pricing Structures

| Structure | Fixed Component | Variable Component | Example |
| --- | --- | --- | --- |
| Uniform (linear) pricing | None | Single per-unit price for all quantity | Simple retail per-item pricing |
| Two-part tariff | Fixed fee $A$ | Single per-unit price $p$ | Gym membership + per-class fee |
| Block tariff | Sometimes a fixed service charge | Multiple per-unit prices across quantity tiers | Tiered utility billing |
| Pure bundling | Full package price only | None (no separate per-unit option) | All-inclusive resort package |

### Practical Design Considerations

- **Metering costs:** Two-part tariffs require the firm to measure usage accurately (a functioning meter or usage-tracking system); where metering is costly or infeasible, firms may default to flat-fee (all-you-can-use) pricing instead
- **Consumer aversion to overage fees:** Usage-based components that generate unpredictable "surprise" bills (e.g., historic mobile data overage charges) can generate significant customer dissatisfaction and churn, a behavioral consideration alongside the pure optimization logic [Inference]
- **Competitive context:** In competitive (rather than monopolistic) markets, the ability to set $A$ significantly above zero is constrained by rival firms' offers; two-part tariff theory as presented here assumes some degree of market power, consistent with the broader price discrimination framework

### Related Topics

- Price discrimination strategies (first-, second-, and third-degree)
- Bundling and tying strategies
- Peak-load and block pricing in regulated utilities
- Menu pricing and screening under asymmetric information
- Marginal cost pricing and allocative efficiency
- SaaS and subscription-based revenue models