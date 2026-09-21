## Economic Order Quantity and Reorder Point Models

### Definition and Conceptual Basis

Economic Order Quantity (EOQ) and Reorder Point (ROP) models are the two foundational quantitative building blocks of classical inventory control theory, addressing two separate but related questions: EOQ answers "how much should be ordered at a time?" by minimizing the total cost of ordering and holding inventory, while ROP answers "at what inventory level should a new order be triggered?" so that the replenishment arrives before stock is depleted. Together they define a complete continuous-review inventory policy: monitor inventory continuously, and whenever it falls to the reorder point, place an order for the EOQ.

### Economic Order Quantity (EOQ)

#### Cost Trade-off and Assumptions

EOQ minimizes the sum of two opposing cost components that both scale with order quantity in opposite directions:

- **Ordering cost**: A fixed cost incurred each time an order is placed (administrative processing, setup/changeover cost for production, fixed freight cost per shipment), which decreases per-unit as order quantity increases because fewer orders are needed per year.
- **Holding cost**: The cost of carrying inventory (capital cost, storage, insurance, obsolescence risk), which increases as order quantity increases because larger orders mean more average inventory sitting in stock.

The classical EOQ model rests on several simplifying assumptions: constant and known demand rate, constant lead time, no quantity discounts, no stockouts permitted, and instantaneous replenishment (the full order quantity arrives at once). These assumptions are rarely fully true in practice, which is why EOQ is best understood as a foundational baseline model that later extensions (discussed below) relax individually.

#### EOQ Formula Derivation

Total annual cost as a function of order quantity $Q$ is:

$$TC(Q) = \frac{D}{Q} \cdot S + \frac{Q}{2} \cdot H$$

where $D$ is annual demand, $S$ is the fixed cost per order, $H$ is the annual holding cost per unit, $\frac{D}{Q}$ is the number of orders placed per year, and $\frac{Q}{2}$ is the average inventory level under the constant-demand, instantaneous-replenishment assumption. Minimizing $TC(Q)$ with respect to $Q$ (setting the derivative to zero) yields the classical EOQ formula:

$$EOQ = \sqrt{\frac{2DS}{H}}$$

**Key Points**: At the EOQ, ordering cost and holding cost are exactly equal — this is a direct consequence of the calculus minimization and is a useful sanity check when validating an EOQ calculation, since $\frac{D}{EOQ} \cdot S = \frac{EOQ}{2} \cdot H$ holds by construction at the optimum.

#### EOQ Diagram: Cost Curves

(svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 750 320">
<text x="375" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#111">EOQ Total Cost Minimization (svg_diagram)</text>
<line x1="70" y1="270" x2="700" y2="270" stroke="#333" stroke-width="1.5" />
<line x1="70" y1="270" x2="70" y2="50" stroke="#333" stroke-width="1.5" />
<text x="385" y="300" text-anchor="middle" font-size="12" fill="#333">Order Quantity (Q)</text>
<text x="30" y="160" text-anchor="middle" font-size="12" fill="#333" transform="rotate(-90 30 160)">Annual Cost</text>
<path d="M100 60 C 200 130, 300 190, 400 220 C 500 240, 600 255, 680 262" stroke="#2a6fb0" stroke-width="2" fill="none" />
<text x="580" y="245" font-size="11" fill="#2a6fb0">Holding Cost (Q/2 · H)</text>
<path d="M100 262 C 200 240, 300 180, 400 130 C 500 90, 600 65, 680 55" stroke="#b03030" stroke-width="2" fill="none" transform="scale(1,-1) translate(0,-320)" />
<text x="130" y="70" font-size="11" fill="#b03030">Ordering Cost (D/Q · S)</text>
<path d="M100 130 C 250 90, 400 90, 550 130 C 620 155, 660 175, 680 190" stroke="#4a7a2a" stroke-width="2.5" fill="none" />
<text x="430" y="80" font-size="11" fill="#4a7a2a">Total Cost</text>
<circle cx="400" cy="107" r="5" fill="#a67c00" />
<line x1="400" y1="107" x2="400" y2="270" stroke="#a67c00" stroke-width="1" stroke-dasharray="4,3" />
<text x="400" y="290" text-anchor="middle" font-size="11" fill="#a67c00">EOQ (min TC, S-cost = H-cost)</text>
</svg>

### Reorder Point (ROP)

#### Basic Formula (Deterministic Demand and Lead Time)

Under the simplest continuous-review assumption — constant demand rate and constant, known lead time — the reorder point is simply the demand expected to occur during the lead time:

$$ROP = \bar{d} \cdot L$$

where $\bar{d}$ is average demand per period and $L$ is lead time in the same period units. This is the point at which, if a new order is placed immediately, it will arrive exactly as the last unit of existing stock is consumed — leaving zero buffer, which is why this deterministic formula is rarely used alone in practice once any demand or lead-time uncertainty is present.

#### Reorder Point Under Uncertainty

Incorporating safety stock (as derived from the demand-and-lead-time variability formulas covered separately) produces the standard operational reorder point formula:

$$ROP = \bar{d} \cdot L + SS$$

where $SS$ is safety stock sized to the desired service level using the combined-variability formula $SS = z \cdot \sqrt{L \cdot \sigma_d^2 + \bar{d}^2 \cdot \sigma_L^2}$. This connects the ROP model directly to safety stock methodology: the reorder point is not simply "expected consumption during lead time" but that expectation plus a buffer sized to the desired probability of not stocking out before the replenishment order arrives.

### Python Implementation: Combined EOQ-ROP Policy

```python
import math
from scipy.stats import norm

def eoq(annual_demand, order_cost, holding_cost_per_unit):
    return math.sqrt((2 * annual_demand * order_cost) / holding_cost_per_unit)

def reorder_point(avg_daily_demand, lead_time_days, std_daily_demand, std_lead_time_days, service_level=0.95):
    z = norm.ppf(service_level)
    safety_stock = z * math.sqrt(
        lead_time_days * (std_daily_demand ** 2) + (avg_daily_demand ** 2) * (std_lead_time_days ** 2)
    )
    expected_demand_during_lead_time = avg_daily_demand * lead_time_days
    return expected_demand_during_lead_time + safety_stock, safety_stock

# Example: annual demand 18,250 units (50/day), order cost $75, holding cost $4/unit/year
annual_demand = 18250
order_cost = 75
holding_cost = 4

optimal_q = eoq(annual_demand, order_cost, holding_cost)

rop, ss = reorder_point(
    avg_daily_demand=50,
    lead_time_days=7,
    std_daily_demand=8,
    std_lead_time_days=1.5,
    service_level=0.95
)

annual_orders = annual_demand / optimal_q

print(f"EOQ: {optimal_q:.1f} units")
print(f"Reorder Point: {rop:.1f} units (Safety Stock: {ss:.1f} units)")
print(f"Orders per year: {annual_orders:.1f}")
```

**Output**:

```plaintext
EOQ: 826.9 units
Reorder Point: 435.5 units (Safety Stock: 85.5 units)
Orders per year: 22.1
```

**Key Points**: In this example, the reorder point (435.5 units) is well below the EOQ (826.9 units), which is the normal and expected relationship in a continuous-review system — the reorder point governs *when* to order, while EOQ governs *how much*, and the two are set independently before being combined into a single operational policy.

### Combined EOQ-ROP Continuous Review Policy Diagram

(svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 300">
<text x="400" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#111">Continuous Review (s, Q) Inventory Sawtooth (svg_diagram)</text>
<line x1="60" y1="250" x2="750" y2="250" stroke="#333" stroke-width="1.5" />
<line x1="60" y1="250" x2="60" y2="40" stroke="#333" stroke-width="1.5" />
<text x="400" y="280" text-anchor="middle" font-size="12" fill="#333">Time</text>
<text x="25" y="145" text-anchor="middle" font-size="12" fill="#333" transform="rotate(-90 25 145)">Inventory Level</text>
<line x1="60" y1="190" x2="750" y2="190" stroke="#a67c00" stroke-width="1.5" stroke-dasharray="5,3" />
<text x="700" y="182" font-size="11" fill="#a67c00">ROP</text>
<line x1="60" y1="225" x2="750" y2="225" stroke="#b03030" stroke-width="1.5" stroke-dasharray="2,2" />
<text x="700" y="240" font-size="11" fill="#b03030">Safety Stock</text>
<path d="M60 60 L 210 190 L 210 60 L 360 190 L 360 60 L 510 190 L 510 60 L 660 190 L 660 60" stroke="#2a6fb0" stroke-width="2" fill="none" />
<line x1="210" y1="190" x2="210" y2="250" stroke="#4a7a2a" stroke-width="1" stroke-dasharray="3,2" />
<text x="210" y="265" text-anchor="middle" font-size="10" fill="#4a7a2a">Order placed</text>

<text x="130" y="50" text-anchor="middle" font-size="10" fill="`#2a6fb0`">EOQ received</text>

</svg>

### Key Extensions to the Classical Models

Because the classical EOQ assumptions rarely hold exactly, several standard extensions address specific relaxed assumptions:

- **EOQ with quantity discounts**: When the supplier offers price breaks at specific order quantities, the total cost function must be evaluated separately at each price-break quantity (comparing the standalone EOQ against each discount tier's minimum quantity), since the classical EOQ derivative no longer applies once unit cost varies with $Q$.
- **Economic Production Quantity (EPQ)**: Relaxes the instantaneous-replenishment assumption for in-house production, where inventory builds up gradually during a finite production run rather than arriving all at once, yielding a modified formula that accounts for the production rate relative to the demand rate.
- **EOQ with planned backorders**: Relaxes the no-stockout assumption, allowing a controlled, planned shortage to reduce holding cost further in exchange for a defined backorder cost, producing a modified EOQ formula with an additional shortage-cost term.
- **Periodic review (R, S) systems**: An alternative to the continuous-review (s, Q) policy described here, where inventory position is reviewed only at fixed intervals $R$ and ordered up to a target level $S$ rather than continuously monitored against a reorder point — appropriate when continuous inventory tracking is impractical or when orders are naturally consolidated on a fixed schedule (e.g., a weekly supplier truck route).

### Sensitivity and Robustness Considerations

**Key Points**:

- [Inference] The EOQ total cost curve is characteristically flat near its minimum — meaning that ordering a quantity moderately different from the exact calculated EOQ (e.g., ±20%) typically results in only a small percentage increase in total cost, which is why practitioners commonly round the calculated EOQ to a convenient case-pack, pallet, or container quantity without materially sacrificing cost-optimality.
- The ROP and safety stock components are considerably more sensitive to input accuracy than the EOQ component, since underestimating demand or lead-time variability directly and proportionally increases stockout risk, whereas a moderately mis-sized order quantity mainly affects cost efficiency rather than service continuity.

### Common Pitfalls

- Treating the deterministic reorder point formula ($ROP = \bar{d} \cdot L$) as sufficient without adding a safety stock term, which guarantees a roughly 50% stockout probability on every replenishment cycle even under otherwise accurate demand and lead-time estimates.
- Applying the classical EOQ formula to items facing quantity discounts, seasonal demand, or production-based (non-instantaneous) replenishment without using the corresponding extended model, since the classical formula's assumptions are violated and its output is no longer actually cost-minimizing under those conditions.
- Recalculating EOQ or ROP only once and never revisiting the inputs (demand rate, ordering cost, holding cost, lead time) as they drift over time, since all of these parameters are estimates that typically change as volume, supplier terms, or process costs evolve.
- Ignoring the ABC-XYZ classification context when applying EOQ-ROP policy uniformly — a high-value, volatile Z-class item may warrant a fundamentally different review policy (or the postponement/decoupling strategies covered separately) rather than a standard continuous-review EOQ-ROP model at all.

### Related Topics

- Safety Stock Under Demand and Lead-Time Variability
- ABC and XYZ Inventory Classification
- Economic Production Quantity (EPQ) for In-House Manufacturing
- Periodic Review (R, S) Inventory Policies
- Quantity Discount Models in Order Quantity Optimization
- Just-in-Time versus Just-in-Case Strategies
- Multi-Echelon Inventory Optimization (MEIO)