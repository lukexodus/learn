## Full Reorder Point Formula Combining Lead Time Demand and Safety Stock

### Definition and Purpose

The reorder point (ROP) is the inventory level at which a new replenishment order must be triggered so that the order arrives before stock is depleted, while still covering demand uncertainty and lead time variability. The full reorder point formula synthesizes two components: expected demand during the lead time window, and a buffer (safety stock) sized to protect against variability in both demand and lead time.

$$ROP = d_L + SS$$

Where $d_L$ is lead time demand and $SS$ is safety stock.

### Lead Time Demand Component

Lead time demand represents the expected quantity consumed between the moment an order is placed and the moment it is received.

$$d_L = \bar{d} \times L$$

- $\bar{d}$: average demand per period (e.g., units/day)
- $L$: average lead time, expressed in the same period units

**Example**

If average daily demand is 40 units and average supplier lead time is 12 days:

$$d_L = 40 \times 12 = 480 \text{ units}$$

### Safety Stock Component

Safety stock buffers against two independent sources of uncertainty: variability in demand rate and variability in lead time duration. The standard formulation assumes both are normally distributed and statistically independent, combining their variances under the square-root-of-sum-of-squares rule.

$$SS = Z \times \sigma_{d_L}$$

Where $Z$ is the service-level factor (standard normal z-score) and $\sigma_{d_L}$ is the standard deviation of demand during lead time.

**Combined variability formula (variable demand and variable lead time):**

$$\sigma_{d_L} = \sqrt{L \times \sigma_d^2 + \bar{d}^2 \times \sigma_L^2}$$

- $\sigma_d$: standard deviation of demand per period
- $\sigma_L$: standard deviation of lead time (same units as $L$)
- $\bar{d}$: average demand per period
- $L$: average lead time

This is the general-case formula. Two simplified variants are common depending on which source of variability dominates.

#### Case 1: Lead Time is Constant (No Lead Time Variability)

When $\sigma_L = 0$, the formula collapses to:

$$\sigma_{d_L} = \sigma_d \times \sqrt{L}$$



$$SS = Z \times \sigma_d \times \sqrt{L}$$

#### Case 2: Demand is Constant (No Demand Variability)

When $\sigma_d = 0$, the formula collapses to:

$$\sigma_{d_L} = \bar{d} \times \sigma_L$$



$$SS = Z \times \bar{d} \times \sigma_L$$

### The Complete Formula

Substituting the safety stock expression into the base ROP equation gives the full reorder point formula:

$$ROP = (\bar{d} \times L) + Z \times \sqrt{L \times \sigma_d^2 + \bar{d}^2 \times \sigma_L^2}$$

**Key Points**

- The formula assumes demand and lead time are statistically independent random variables.
- $Z$ is drawn from the standard normal distribution corresponding to the target cycle service level (e.g., $Z = 1.65$ for 95%, $Z = 2.33$ for 99%).
- Units must be consistent: if $\bar{d}$ is daily, $L$ and $\sigma_L$ must also be in days.
- [Inference] In practice, many ERP/MRP systems default to the constant-lead-time simplification (Case 1) because lead time variance data is harder to obtain reliably than demand variance data, even though this understates true risk when supplier lead times fluctuate materially.

### Worked Example

**Inputs:**

- Average daily demand: $\bar{d} = 40$ units
- Standard deviation of daily demand: $\sigma_d = 8$ units
- Average lead time: $L = 12$ days
- Standard deviation of lead time: $\sigma_L = 2$ days
- Target service level: 95% ($Z = 1.65$)

**Step 1 — Lead time demand:**

$$d_L = 40 \times 12 = 480 \text{ units}$$

**Step 2 — Combined standard deviation of demand during lead time:**

$$\sigma_{d_L} = \sqrt{12 \times 8^2 + 40^2 \times 2^2}$$



$$\sigma_{d_L} = \sqrt{12 \times 64 + 1600 \times 4} = \sqrt{768 + 6400} = \sqrt{7168} \approx 84.66$$

**Step 3 — Safety stock:**

$$SS = 1.65 \times 84.66 \approx 139.7 \text{ units} \rightarrow 140 \text{ units (rounded up)}$$

**Step 4 — Reorder point:**

$$ROP = 480 + 140 = 620 \text{ units}$$

**Interpretation:** When on-hand inventory (plus any already-open orders, in the inventory-position variant below) drops to 620 units, a new order should be placed. This covers the expected 480 units consumed during the 12-day lead time, plus a 140-unit buffer sized to achieve a 95% probability of not stocking out during that window.

### Inventory Position vs. On-Hand Stock

In multi-echelon or systems with outstanding purchase orders, the reorder trigger should compare against **inventory position**, not raw on-hand stock, to avoid duplicate ordering:

$$IP = OH + OO - BO$$

- $OH$: on-hand inventory
- $OO$: on-order (open POs not yet received)
- $BO$: backorders (committed but unfulfilled demand)

The reorder rule becomes: place a new order when $IP \leq ROP$.

### Non-Normal Demand Considerations

- [Inference] When lead time demand is better modeled by a skewed distribution (e.g., intermittent/lumpy demand common in spare parts), the normal-distribution $Z$-score approach can under- or over-state safety stock; practitioners often substitute empirical percentiles, Poisson, or negative binomial models in that case.
- For intermittent demand, methods such as Croston's method or the Syntetos-Boylan Approximation are frequently used instead of the standard normal safety stock formula, since $\sigma_d$ is unstable when demand periods contain many zeros.

### Process Flow Diagram

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 900 460" font-family="Helvetica, Arial, sans-serif">
<text x="450" y="30" text-anchor="middle" font-size="18" font-weight="bold" fill="#1a1a1a">Reorder Point Calculation Flow (svg_diagram)</text>
<rect x="40" y="70" width="220" height="60" rx="8" fill="#e8f0fe" stroke="#4285f4" stroke-width="2" />
<text x="150" y="95" text-anchor="middle" font-size="13" fill="#1a1a1a">Average Demand (d̄)</text>
<text x="150" y="113" text-anchor="middle" font-size="13" fill="#1a1a1a">Demand Std Dev (σd)</text>
<rect x="340" y="70" width="220" height="60" rx="8" fill="#e8f0fe" stroke="#4285f4" stroke-width="2" />
<text x="450" y="95" text-anchor="middle" font-size="13" fill="#1a1a1a">Average Lead Time (L)</text>
<text x="450" y="113" text-anchor="middle" font-size="13" fill="#1a1a1a">Lead Time Std Dev (σL)</text>
<rect x="640" y="70" width="220" height="60" rx="8" fill="#fef7e0" stroke="#f9ab00" stroke-width="2" />
<text x="750" y="95" text-anchor="middle" font-size="13" fill="#1a1a1a">Target Service Level</text>
<text x="750" y="113" text-anchor="middle" font-size="13" fill="#1a1a1a">→ Z-score</text>
<line x1="150" y1="130" x2="150" y2="190" stroke="#5f6368" stroke-width="2" marker-end="url(#arrow)" />
<line x1="450" y1="130" x2="450" y2="190" stroke="#5f6368" stroke-width="2" marker-end="url(#arrow)" />
<rect x="60" y="190" width="220" height="55" rx="8" fill="#e6f4ea" stroke="#34a853" stroke-width="2" />
<text x="170" y="222" text-anchor="middle" font-size="13" fill="#1a1a1a">d_L = d̄ × L</text>
<rect x="330" y="190" width="260" height="70" rx="8" fill="#fce8e6" stroke="#ea4335" stroke-width="2" />
<text x="460" y="215" text-anchor="middle" font-size="12" fill="#1a1a1a">σ_dL = √(L·σd² + d̄²·σL²)</text>
<text x="460" y="235" text-anchor="middle" font-size="11" fill="#5f6368">(combined variability)</text>
<line x1="450" y1="130" x2="460" y2="190" stroke="#5f6368" stroke-width="2" marker-end="url(#arrow)" />
<line x1="150" y1="130" x2="400" y2="190" stroke="#5f6368" stroke-width="2" marker-end="url(#arrow)" />
<line x1="750" y1="130" x2="500" y2="290" stroke="#5f6368" stroke-width="2" marker-end="url(#arrow)" />
<line x1="460" y1="260" x2="500" y2="290" stroke="#5f6368" stroke-width="2" marker-end="url(#arrow)" />
<rect x="380" y="290" width="240" height="55" rx="8" fill="#fef7e0" stroke="#f9ab00" stroke-width="2" />
<text x="500" y="322" text-anchor="middle" font-size="13" fill="#1a1a1a">SS = Z × σ_dL</text>
<line x1="170" y1="245" x2="380" y2="370" stroke="#5f6368" stroke-width="2" marker-end="url(#arrow)" />
<line x1="500" y1="345" x2="470" y2="370" stroke="#5f6368" stroke-width="2" marker-end="url(#arrow)" />
<rect x="290" y="370" width="320" height="60" rx="8" fill="#d2e3fc" stroke="#1a73e8" stroke-width="3" />
<text x="450" y="397" text-anchor="middle" font-size="14" font-weight="bold" fill="#1a1a1a">ROP = d_L + SS</text>
<text x="450" y="417" text-anchor="middle" font-size="11" fill="#3c4043">Trigger reorder when Inventory Position ≤ ROP</text>
</svg>

### Sensitivity Behavior

| Parameter Increase | Effect on ROP | Reason |
| --- | --- | --- |
| Average demand ($\bar{d}$) | Increases | Higher $d_L$ directly, plus higher $\bar{d}^2\sigma_L^2$ term |
| Average lead time ($L$) | Increases | Higher $d_L$ directly, plus higher $L\sigma_d^2$ term |
| Demand variability ($\sigma_d$) | Increases | Larger $\sigma_{d_L}$ raises safety stock |
| Lead time variability ($\sigma_L$) | Increases | Larger $\sigma_{d_L}$ raises safety stock, scaled by $\bar{d}^2$ |
| Service level target | Increases | Higher $Z$ score directly raises safety stock |

[Inference] Because $\sigma_L$ is scaled by $\bar{d}^2$ (squared) rather than $\bar{d}$ linearly, lead time variability tends to have an outsized impact on required safety stock for high-volume SKUs compared to low-volume ones — this is a common driver of excess safety stock in fast movers with unreliable suppliers.

### Related Topics

- Service level types: cycle service level vs. fill rate vs. ready rate
- Z-score derivation and the standard normal loss function for fill-rate-based safety stock
- Safety stock under non-normal (Poisson, gamma, empirical) demand distributions
- Multi-echelon reorder point propagation and lead time variance aggregation
- Periodic review (order-up-to / min-max) systems vs. continuous review (Q, R) systems
- Forecast error measurement (MAD, MSE, RMSE) as inputs to $\sigma_d$
- Supplier lead time variability tracking and statistical process control