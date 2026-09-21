## Safety Stock Under Demand and Lead-Time Variability

### Definition and Conceptual Basis

Safety stock is the buffer inventory held above expected demand during lead time, sized to protect against the risk of stockout caused by uncertainty in either how much customers demand or how long replenishment takes to arrive. It is a direct hedge against variability: if demand and lead time were perfectly deterministic, no safety stock would be required, and inventory would simply track expected consumption. Because both demand and lead time are almost always random variables in practice, safety stock sizing has to account for their individual variances and, when both vary simultaneously, their combined effect on the variance of total demand during the replenishment window.

### The Core Sizing Formula

The standard formula for safety stock under demand variability alone, assuming a fixed lead time $L$ and a target service level, is:

$$SS = z \cdot \sigma_d \cdot \sqrt{L}$$

where $z$ is the standard normal $z$-score corresponding to the desired cycle service level, $\sigma_d$ is the standard deviation of demand per period, and $L$ is the lead time expressed in the same period units as $\sigma_d$. The $\sqrt{L}$ term arises because variance is additive across independent periods, so the standard deviation of cumulative demand over $L$ periods scales with the square root of $L$, not $L$ itself.

### Combined Demand and Lead-Time Variability

When lead time itself is also a random variable — a common and often underestimated reality in real supply chains — the safety stock formula must incorporate both sources of uncertainty jointly. The standard combined formula, derived from the variance of a sum of a random number of random variables, is:

$$SS = z \cdot \sqrt{L \cdot \sigma_d^2 + \bar{d}^2 \cdot \sigma_L^2}$$

where $\bar{d}$ is the average demand per period, $\sigma_L$ is the standard deviation of lead time, and the remaining terms are as defined above. This formula is well established in inventory theory (derived from the variance decomposition of demand during a stochastic lead time) and is the standard reference formula used in production and inventory management texts (e.g., APICS/ASCM body of knowledge).

**Key Points**:

- The first term, $L \cdot \sigma_d^2$, captures the risk contributed by demand variability alone, scaled by the lead time.
- The second term, $\bar{d}^2 \cdot \sigma_L^2$, captures the risk contributed by lead-time variability alone, scaled by the square of average demand.
- Because the second term scales with $\bar{d}^2$ rather than $\bar{d}$, lead-time variability becomes disproportionately costly to buffer against for high-volume items — a supplier with unreliable lead times imposes a much larger safety stock penalty on a fast-moving SKU than on a slow-moving one, for the same relative lead-time variability.
- [Inference] In practice, lead-time variability is frequently the dominant driver of required safety stock once a supply chain has more than one or two tiers, since lead-time distributions in multi-tier chains tend to have heavier tails (congestion, customs delays, capacity contention) than demand distributions, though this varies by industry and specific supplier reliability.

### Service Level and the Z-Score

The $z$-score translates a target cycle service level (the probability of not stocking out during a single replenishment cycle) into a number of standard deviations of buffer. Common reference values:

| Cycle Service Level | z-score |
| --- | --- |
| 90% | 1.28 |
| 95% | 1.65 |
| 97.5% | 1.96 |
| 99% | 2.33 |
| 99.9% | 3.09 |

**Key Points**: Cycle service level (probability of no stockout per cycle) is distinct from fill rate (percentage of units demanded that are satisfied from stock) — the two are related but not numerically identical, and confusing them is a common source of under- or over-stocking when translating a business service-level target into a $z$-score.

### Non-Normal Demand Distributions

The formulas above assume demand (and often lead time) follow, or can be reasonably approximated by, a normal distribution. This assumption breaks down for slow-moving, intermittent-demand items — common in spare parts, MRO inventory, and long-tail SKUs — where demand is frequently zero and occasionally spikes. For such items:

- **Poisson demand models** are used when demand arrives as discrete, infrequent units, replacing the normal-distribution $z$-score approach with Poisson or compound-Poisson quantiles.
- **Croston's method** and its variants (Syntetos-Boylan Approximation) are used to forecast intermittent demand by separately modeling the size and interval of non-zero demand occurrences, then deriving safety stock from the resulting compound distribution rather than a simple normal approximation.
- **Empirical/simulation-based safety stock** — computing the safety stock quantile directly from the empirical distribution of historical demand-during-lead-time observations — is used when the true distribution is materially skewed or multimodal and no standard parametric form fits well.

### Worked Example

Given: average demand $\bar{d} = 50$ units/day, demand standard deviation $\sigma_d = 8$ units/day, average lead time $L = 10$ days, lead-time standard deviation $\sigma_L = 2$ days, target service level 95% ($z = 1.65$).

$$SS = 1.65 \cdot \sqrt{10 \cdot 8^2 + 50^2 \cdot 2^2}$$



$$SS = 1.65 \cdot \sqrt{10 \cdot 64 + 2500 \cdot 4} = 1.65 \cdot \sqrt{640 + 10000} = 1.65 \cdot \sqrt{10640} \approx 1.65 \cdot 103.15 \approx 170.2$$

**Output**: Required safety stock ≈ 171 units. Note that the demand-variability term alone ($640$) contributes only about 6% of the total variance under the square root, while the lead-time-variability term ($10000$) contributes roughly 94% — illustrating the disproportionate impact of lead-time variability described above for this parameter set.

### Python Implementation

```python
import math
from scipy.stats import norm

def safety_stock(avg_demand, std_demand, avg_lead_time, std_lead_time, service_level):
    z = norm.ppf(service_level)
    variance = avg_lead_time * (std_demand ** 2) + (avg_demand ** 2) * (std_lead_time ** 2)
    return z * math.sqrt(variance)

# Example usage
ss = safety_stock(
    avg_demand=50,
    std_demand=8,
    avg_lead_time=10,
    std_lead_time=2,
    service_level=0.95
)
print(f"Safety Stock: {ss:.1f} units")
# Output: Safety Stock: 170.2 units
```

**Key Points**: `norm.ppf` (percent-point function, the inverse of the CDF) is the standard SciPy method for converting a target service level probability directly into a $z$-score, avoiding the need to hardcode a lookup table.

### Variance Contribution Diagram

(svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 300">
<text x="400" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#111">Sources of Safety Stock Variance (svg_diagram)</text>
<rect x="60" y="60" width="300" height="180" fill="none" stroke="#333" stroke-width="1.5" />
<text x="210" y="50" text-anchor="middle" font-size="12" fill="#333">Total Variance Under Sqrt</text>
<rect x="70" y="220" width="280" height="10" fill="#dceeff" stroke="#2a6fb0" />
<text x="210" y="255" text-anchor="middle" font-size="11" fill="#2a6fb0">Demand variability: L·σd² (~6% in example)</text>
<rect x="70" y="70" width="280" height="140" fill="#ffd6d6" stroke="#b03030" />
<text x="210" y="145" text-anchor="middle" font-size="12" fill="#b03030">Lead-time variability</text>
<text x="210" y="163" text-anchor="middle" font-size="11" fill="#b03030">d̄²·σL² (~94% in example)</text>

<text x="450" y="120" font-size="12" fill="#555">SS = z · √(Total Variance)</text>

<line x1="440" y1="150" x2="620" y2="150" stroke="#333" stroke-width="1" />

<text x="450" y="170" font-size="12" fill="#555">z fixed by target</text>

<text x="450" y="188" font-size="12" fill="#555">service level</text>

<text x="400" y="280" text-anchor="middle" font-size="10" fill="#555" font-style="italic">
Lead-time variance term scales with mean demand squared — disproportionate for high-volume SKUs
</text>
</svg>

### Multi-Echelon Considerations

**Key Points**:

- In a multi-echelon chain, safety stock sized independently at each tier using only that tier's local demand variability tends to over-stock the system in aggregate, because it ignores risk pooling and the correlation structure between tiers' demand signals.
- Multi-Echelon Inventory Optimization (MEIO) models size safety stock jointly across tiers, accounting for the fact that upstream tiers see a smoothed and partially pooled version of downstream demand variability (subject to the bullwhip amplification discussed separately), and can therefore often carry proportionally less safety stock per unit of downstream variance than an independently-optimized calculation would suggest.
- Guaranteed-service and stochastic-service multi-echelon models (e.g., the Graves-Willems framework) are the standard analytical approaches for computing echelon-appropriate safety stock allocation rather than applying the single-stage formula independently at every node.

### Common Pitfalls

- Applying the demand-only formula ($SS = z \cdot \sigma_d \cdot \sqrt{L}$) when lead time is known to be variable, which systematically under-buffers the system since the lead-time-variance term is entirely omitted.
- Using a point estimate of average lead time without ever measuring $\sigma_L$ from actual receipt data, since supplier-quoted lead times are frequently understated relative to observed variability.
- Assuming normality for demand distributions that are actually intermittent or highly skewed (common in spare parts and long-tail SKUs), which can produce z-score-based safety stock levels that are severely mis-calibrated relative to the true stockout probability.
- Failing to re-derive $z$ from the actual desired probability metric (cycle service level vs. fill rate vs. ready rate) being targeted by the business, since these metrics require different translation logic and are not interchangeable.

### Related Topics

- Multi-Echelon Inventory Optimization (MEIO) and the Graves-Willems Guaranteed-Service Model
- Croston's Method and Intermittent Demand Forecasting
- Cycle Service Level vs. Fill Rate: Definitions and Conversion
- Risk Pooling and Its Effect on Aggregate Safety Stock Requirements
- Reorder Point (ROP) and (s, S) Inventory Policy Design
- Supplier Lead Time Reliability Measurement and Its Cost Impact
- Inventory Positioning and Decoupling Points