## Quantity Discount Models

### Definition and Purpose

Quantity discount models are extensions of the basic Economic Order Quantity (EOQ) framework that relax the assumption of a constant unit purchase price. In practice, suppliers frequently offer reduced unit prices for orders exceeding specified quantity thresholds ("price breaks"), creating an incentive to order in larger batches than the basic EOQ would otherwise recommend. Quantity discount models provide a structured method for determining the order quantity that minimizes *total* annual cost — including purchase cost, ordering cost, and holding cost together — rather than ordering/holding cost alone, since purchase cost is no longer constant across order-quantity choices once discounts are present.

The central managerial question these models answer is: does the holding-cost penalty of ordering a larger, discount-qualifying batch outweigh the savings from the lower unit price? This requires evaluating total cost at each relevant price-break quantity rather than relying on the unconstrained EOQ formula alone.

### Total Cost Function With Purchase Price Included

$$TC(Q) = \frac{D}{Q}S + \frac{Q}{2}H + DC$$

Unlike the basic EOQ model — where the purchase cost term $DC$ is constant and drops out of the optimization — in a quantity discount model, $C$ (unit price) varies by quantity range, so $DC$ must be included explicitly in the comparison across price breaks.

A critical modeling choice is whether holding cost $H$ is a **fixed dollar amount per unit** or, more commonly, a **percentage of unit cost** ($H = iC$, where $i$ is the holding-cost rate). When $H$ depends on $C$, the EOQ itself changes at each price break, since a lower unit price reduces the holding cost per unit, which increases the price-break-specific EOQ.

### Types of Quantity Discount Schedules

1. **All-units discount**: the reduced price applies to *all* units in the order once the quantity threshold is met (the most common schedule type, and the focus of the standard solution algorithm below).
2. **Incremental (marginal) discount**: the reduced price applies only to units *above* the threshold, while units below the threshold are still charged the original price — requiring a different, piecewise total-cost calculation.

The example schedule below uses the all-units discount structure, as it is the standard case presented in most operations management curricula.

### Example Discount Schedule

| Price Break (Range) | Order Quantity Range | Unit Price ($C$) |
| --- | --- | --- |
| 1 | 0 – 999 | $10.00 |
| 2 | 1,000 – 2,499 | $9.70 |
| 3 | 2,500 and above | $9.50 |

### Standard Solution Algorithm (All-Units Discount)

```mermaid
flowchart TD
    A[Start with lowest unit price tier] --> B["Compute EOQ using that tier's price for H = iC"]
    B --> C{Is computed EOQ feasible within this tier's quantity range?}
    C -->|Yes| D[This EOQ is a candidate order quantity]
    C -->|No, EOQ falls below range| E[Adjust candidate to the minimum quantity qualifying for this tier]
    C -->|No, EOQ falls above range| F[This tier's EOQ is infeasible -- discard]
    D --> G[Move to next higher price tier and repeat]
    E --> G
    F --> G
    G --> H{All tiers evaluated?}
    H -->|No| B
    H -->|Yes| I[Compute Total Cost TC(Q) for every candidate quantity]
    I --> J[Select Q with lowest Total Cost]
```

**Step-by-step procedure:**

1. Beginning with the **lowest price** (highest discount tier), calculate the EOQ using that tier's unit price to determine $H$.
2. Check whether this EOQ value **falls within the quantity range** that actually qualifies for that price tier.
   - If yes, this EOQ is a **feasible candidate**.
   - If the EOQ is **too small** to qualify for that discount tier (falls below the tier's minimum), the candidate becomes the **minimum quantity required** to qualify for that tier (since ordering less would not achieve the assumed price, and ordering the EOQ-recommended smaller amount is infeasible at this tier's price).
   - If the EOQ **exceeds** the tier's range (relevant mainly for schedules with an upper bound on a tier), that EOQ is infeasible for this tier and is discarded.
3. Repeat for each price tier, working down to the highest-price (no-discount) tier.
4. Calculate the **total annual cost** $TC(Q)$ at every candidate quantity identified, including the purchase cost term $DC$.
5. Select the candidate quantity with the **lowest total annual cost** as the optimal order quantity.

### Worked Example

An electronics retailer purchases a component with the following parameters:

- Annual demand, $D = 5{,}000$ units/year
- Ordering cost, $S = \$50$ per order
- Holding cost rate, $i = 20\%$ of unit cost (so $H = 0.20 \times C$)
- Discount schedule as shown above (3 price tiers)

**Step 1 — Evaluate Tier 3 (lowest price, $9.50, range ≥ 2,500):**

$$H_3 = 0.20 \times 9.50 = \$1.90$$



$$Q_3^* = \sqrt{\frac{2DS}{H_3}} = \sqrt{\frac{2 \times 5{,}000 \times 50}{1.90}} = \sqrt{\frac{500{,}000}{1.90}} = \sqrt{263{,}158} \approx 513$$

Since 513 is **not within** the required range (2,500 and above) for this tier, this EOQ is infeasible at the assumed price. The candidate quantity for Tier 3 is instead adjusted to the **minimum qualifying quantity: 2,500 units**.

**Step 2 — Evaluate Tier 2 ($9.70, range 1,000–2,499):**

$$H_2 = 0.20 \times 9.70 = \$1.94$$



$$Q_2^* = \sqrt{\frac{2 \times 5{,}000 \times 50}{1.94}} = \sqrt{\frac{500{,}000}{1.94}} = \sqrt{257{,}732} \approx 508$$

Since 508 is **not within** the required range (1,000–2,499) for this tier, this candidate is also adjusted to the **minimum qualifying quantity: 1,000 units**.

**Step 3 — Evaluate Tier 1 ($10.00, range 0–999):**

$$H_1 = 0.20 \times 10.00 = \$2.00$$



$$Q_1^* = \sqrt{\frac{2 \times 5{,}000 \times 50}{2.00}} = \sqrt{\frac{500{,}000}{2.00}} = \sqrt{250{,}000} = 500$$

Here, 500 **is within** the valid range (0–999) for Tier 1, so this EOQ is directly **feasible** as computed: candidate quantity = 500 units.

**Step 4 — Compute total annual cost for each candidate:**

$$TC(Q) = \frac{D}{Q}S + \frac{Q}{2}H + DC$$

*Candidate A: Q = 500 (Tier 1, C = $10.00, H = $2.00)*

$$TC(500) = \frac{5{,}000}{500}(50) + \frac{500}{2}(2.00) + (5{,}000)(10.00)$$



$$TC(500) = (10)(50) + (250)(2.00) + 50{,}000 = 500 + 500 + 50{,}000 = \$51{,}000$$

*Candidate B: Q = 1,000 (Tier 2, C = $9.70, H = $1.94)*

$$TC(1{,}000) = \frac{5{,}000}{1{,}000}(50) + \frac{1{,}000}{2}(1.94) + (5{,}000)(9.70)$$



$$TC(1{,}000) = (5)(50) + (500)(1.94) + 48{,}500 = 250 + 970 + 48{,}500 = \$49{,}720$$

*Candidate C: Q = 2,500 (Tier 3, C = $9.50, H = $1.90)*

$$TC(2{,}500) = \frac{5{,}000}{2{,}500}(50) + \frac{2{,}500}{2}(1.90) + (5{,}000)(9.50)$$



$$TC(2{,}500) = (2)(50) + (1{,}250)(1.90) + 47{,}500 = 100 + 2{,}375 + 47{,}500 = \$49{,}975$$

**Step 5 — Select the minimum:**

| Candidate | Order Quantity | Total Annual Cost |
| --- | --- | --- |
| A | 500 | $51,000 |
| B | **1,000** | **$49,720** |
| C | 2,500 | $49,975 |

The lowest total annual cost occurs at **Q = 1,000 units** (Tier 2), with $TC = \$49{,}720$. Although Tier 3 offers a lower unit price ($9.50 vs. $9.70), the additional holding cost required to reach the 2,500-unit minimum ($2,375 vs. $970) outweighs the $625 in additional purchase-cost savings ($50,000 − $47,500 = $2,500 savings vs. $500 at Tier 1... more precisely, comparing B and C directly: purchase cost drops by $48,500 − $47,500 = $1,000, but holding cost rises by $2,375 − $970 = $1,405, and ordering cost drops only slightly, netting an overall cost *increase* of $255 moving from B to C).

**Conclusion:** the retailer should order 1,000 units per order, forgoing the deepest discount tier because its holding-cost penalty exceeds its purchase-price benefit.

### Incremental (Marginal) Discount Variant

In an incremental discount schedule, only units *above* each threshold receive the lower price, requiring a modified purchase-cost calculation:

$$\text{Purchase Cost} = C_1 \times q_1 + C_2 \times (q_2 - q_1) + \dots$$

where $q_1, q_2, \dots$ are the successive threshold quantities and $C_1, C_2, \dots$ are their respective marginal prices. This structure is common in energy/utility billing and some raw-material contracts, but is less frequently tested in standard operations management coursework relative to the all-units discount model above. [Inference] The incremental discount model generally produces a smoother total-cost curve than the all-units model (since price changes are marginal rather than applied retroactively to the whole order), which typically reduces the incentive to "jump" to a much larger order size purely to capture a lower average price.

### Benefits

- Provides a rigorous, total-cost-based method for evaluating whether pursuing a supplier's volume discount is actually economical once holding-cost impact is included
- Prevents the common managerial error of chasing the lowest unit price without accounting for the increased capital tied up in larger average inventory
- Directly extends the EOQ framework, making it straightforward to apply once EOQ mechanics are understood
- Explicitly quantifies the trade-off between purchase-cost savings and holding-cost increases at each price break

### Limitations and Considerations

- The standard algorithm assumes an all-units discount structure; incremental discount schedules require a different (piecewise) cost formulation
- The model assumes holding cost is proportional to unit price ($H = iC$); if holding cost is instead a fixed dollar amount per unit regardless of price, the EOQ does not shift across price tiers, simplifying (but changing) the analysis
- As with basic EOQ, the model assumes constant, known demand; under demand uncertainty, a large discount-qualifying order also carries greater obsolescence or excess-inventory risk that is not captured in the deterministic total-cost formula
- Supplier minimum order quantities, storage capacity constraints, and cash-flow limitations may override the mathematically optimal quantity identified by the model, particularly at the largest discount tiers
- [Unverified] The prevalence of all-units versus incremental discount structures varies by industry and supplier negotiating practice; no universal proportion should be assumed without a specific cited industry source.

### Key Points

- Quantity discount models minimize *total* cost (ordering + holding + purchase), not ordering-and-holding cost alone, since unit price varies with order quantity
- The standard solution procedure evaluates a candidate order quantity at each price tier — either the tier's own EOQ (if feasible) or the tier's minimum qualifying quantity (if the tier's EOQ falls outside its valid range) — then compares total cost across all candidates
- The lowest unit price does not automatically produce the lowest total cost; the holding-cost penalty of a larger order can outweigh the purchase-price savings
- All-units and incremental discount schedules require different cost formulations and should not be conflated

### Related Topics

- Economic Order Quantity (EOQ) model
- Reorder point and safety stock calculation
- ABC classification analysis
- Total cost of ownership and supplier negotiation strategy
- Economic Production Quantity (EPQ) model
- Working capital and cash-flow constraints in inventory decisions