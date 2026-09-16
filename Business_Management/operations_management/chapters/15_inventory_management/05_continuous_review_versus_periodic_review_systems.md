## Continuous Review Versus Periodic Review Systems

### Definition and Purpose

Continuous review and periodic review systems are the two fundamental inventory replenishment control policies that determine *when* inventory levels are checked and *when* a replenishment order is triggered, under conditions of demand and/or lead-time uncertainty. Both systems address the same underlying question — how to manage the timing and quantity of replenishment orders to balance service level against inventory investment — but differ in their monitoring frequency, order-quantity logic, and resulting safety stock requirements.

These two policies are commonly denoted using standardized notation:

- **Continuous review system**: also called the **(Q, R) system** or **fixed-order-quantity system**, where $Q$ is a fixed order quantity and $R$ (or ROP) is the reorder point.
- **Periodic review system**: also called the **(s, S) system** or **fixed-order-interval system**, or the **"order-up-to" system**, where inventory is reviewed at fixed intervals and ordered up to a target level $S$.

### Continuous Review (Q, R) System

**Mechanism:** Inventory position is monitored continuously (in practice, updated in real time via a perpetual inventory system, e.g., triggered at each transaction in a modern WMS/ERP). Whenever inventory position drops to or below the reorder point $R$, a fixed quantity $Q$ (typically the EOQ) is ordered.

**Key characteristics:**

- Order **quantity is fixed** ($Q$); order **timing varies** based on actual demand realization
- Requires continuous or near-continuous visibility into inventory levels
- Safety stock only needs to cover the lead-time window, since the system reacts immediately once the reorder point is breached
- Historically associated with perpetual inventory record-keeping (now standard via barcode/RFID/POS-integrated systems)

**Reorder point formula:**

$$R = (d \times L) + SS$$

where $SS = z \times \sigma_d \times \sqrt{L}$ (or the combined-variability formula when both demand and lead time vary), as covered in the reorder point and safety stock topic.

### Periodic Review (s, S) / Order-Up-To System

**Mechanism:** Inventory position is reviewed only at fixed time intervals (e.g., every 2 weeks). At each review, an order is placed to bring the inventory position up to a target order-up-to level $S$, with the order quantity varying depending on how much was consumed since the last review.

**Key characteristics:**

- Review **timing is fixed** (the period $P$); order **quantity varies** based on how much inventory was depleted
- Does not require continuous inventory monitoring — well suited to manual counting or batch-processed systems
- Safety stock must cover the *protection interval*, which spans both the review period $P$ *and* the lead time $L$, because once an order is placed, the next opportunity to react to a shortfall is not until the following review
- Commonly used for coordinating joint replenishment (ordering multiple SKUs together to consolidate shipments/reduce ordering cost) and for suppliers/situations with fixed delivery schedules

**Order-up-to level formula:**

$$S = d \times (P + L) + SS$$

**Safety stock formula (protection interval extends over review period plus lead time):**

$$SS = z \times \sigma_d \times \sqrt{P + L}$$

**Order quantity placed at each review** (variable):

$$Q = S - (\text{Inventory Position at Review})$$

```mermaid
flowchart TD
    subgraph Continuous Review Q,R System
        A1[Inventory Position Monitored Continuously] --> A2{Inventory <= R?}
        A2 -->|Yes| A3[Order Fixed Quantity Q]
        A2 -->|No| A1
        A3 --> A1
    end
    subgraph Periodic Review s,S System
        B1[Wait Until Fixed Review Interval P] --> B2[Check Inventory Position]
        B2 --> B3[Order Quantity = S minus Current Position]
        B3 --> B1
    end
```

### Side-by-Side Comparison

| Dimension | Continuous Review (Q, R) | Periodic Review (s, S) |
| --- | --- | --- |
| **Monitoring** | Continuous / real-time | Fixed intervals only |
| **Order quantity** | Fixed ($Q$, typically EOQ) | Variable (up to target $S$) |
| **Order timing** | Variable (triggered by demand) | Fixed (at each review point) |
| **Protection interval for safety stock** | Lead time only ($L$) | Review period plus lead time ($P + L$) |
| **Safety stock requirement** | Lower, for equivalent service level | Higher, for equivalent service level |
| **Monitoring/administrative cost** | Higher (requires continuous tracking infrastructure) | Lower (checked only at intervals) |
| **Best suited for** | High-value (Class A) items, items with automated perpetual tracking | Lower-value (Class B/C) items, joint replenishment across multiple SKUs, suppliers with fixed delivery schedules |
| **Responsiveness to demand spikes** | Faster (reacts as soon as ROP is breached) | Slower (must wait until next review) |

### Worked Example: Same Item, Both Systems Compared

A distributor stocks an item with:

- Average daily demand, $d = 15$ units/day
- Standard deviation of daily demand, $\sigma_d = 4$ units/day
- Lead time, $L = 5$ days
- Review period (if periodic), $P = 10$ days
- Desired service level = 95% ($z = 1.645$)

**Continuous Review (Q, R) — Safety Stock:**

$$SS_{continuous} = z \times \sigma_d \times \sqrt{L} = 1.645 \times 4 \times \sqrt{5} = 1.645 \times 4 \times 2.236 \approx 14.7 \text{ units}$$

Reorder point:

$$R = (15 \times 5) + 14.7 = 75 + 14.7 = 89.7 \approx 90 \text{ units}$$

**Periodic Review (s, S) — Safety Stock:**

$$SS_{periodic} = z \times \sigma_d \times \sqrt{P + L} = 1.645 \times 4 \times \sqrt{10 + 5} = 1.645 \times 4 \times 3.873 \approx 25.5 \text{ units}$$

Order-up-to level:

$$S = d \times (P + L) + SS = 15 \times 15 + 25.5 = 225 + 25.5 = 250.5 \approx 251 \text{ units}$$

**Comparison:** for the *identical item and identical 95% service level*, the periodic review system requires approximately 25.5 units of safety stock versus approximately 14.7 units for continuous review — roughly 73% more safety stock. This difference arises entirely from the longer protection interval ($P + L = 15$ days vs. $L = 5$ days) that the periodic system must cover, since a periodic review order, once placed, cannot be adjusted again until the following review point.

### The Fundamental Trade-Off

The comparison illustrates the central trade-off between the two systems:

- **Continuous review reduces safety stock and inventory holding cost** but requires the infrastructure (perpetual inventory systems, real-time tracking) to monitor inventory continuously — a monitoring/administrative cost.
- **Periodic review reduces monitoring/administrative cost and enables coordinated ordering** (e.g., consolidating multiple SKUs from the same supplier into a single periodic shipment to save on transportation/ordering cost) but requires more safety stock to cover the longer, fixed protection interval.

Modern ERP/WMS systems with barcode, RFID, or POS-integrated perpetual inventory tracking have substantially lowered the cost of continuous review, which is part of why continuous review (or hybrid variants) has become more prevalent for Class A items even in contexts that historically relied on periodic physical counts.

### Hybrid and Variant Systems

- **(s, Q) system**: a hybrid where inventory is reviewed continuously, but ordering also incorporates elements of both fixed reorder point ($s$) and fixed order quantity ($Q$) — functionally similar to the standard (Q, R) system, differing mainly in notation convention across textbooks.
- **Optional replenishment / (s, S) with min-max**: a periodic review variant where an order is placed at each review *only if* inventory has fallen below a minimum threshold $s$, and if so, is brought up to $S$ — combining periodic review's lower monitoring cost with a triggering condition that avoids placing very small, inefficient orders.
- **Base-stock system**: a continuous review variant where $Q = 1$ conceptually (used for made-to-order or single-unit-demand contexts), ordering one replenishment unit each time one unit is consumed, common in certain kanban-based pull systems.

### Benefits and Selection Criteria

**Choose continuous review when:**

- The item is high-value (Class A) and warrants tight inventory control
- Perpetual inventory tracking infrastructure is already in place
- Demand is volatile enough that faster reaction time meaningfully reduces required safety stock

**Choose periodic review when:**

- Multiple SKUs from the same supplier can be jointly ordered to consolidate shipments and reduce total ordering/transportation cost
- The item is lower-value (Class C) and the administrative savings from infrequent review outweigh the extra safety stock cost
- The supplier or delivery schedule imposes a fixed review/delivery cadence regardless of the retailer's internal system (e.g., a weekly delivery route)

### Limitations and Considerations

- Both models, as presented, assume demand follows a normal distribution; for intermittent or highly lumpy demand, alternative statistical approaches are more appropriate (as with the reorder point topic generally)
- [Inference] The "extra" safety stock required by periodic review is sometimes partially offset in practice by ordering-cost savings from joint replenishment (consolidating multiple SKUs into a single periodic order), so a full cost comparison between the two systems should include ordering-cost effects, not safety-stock cost alone, when the periodic system is used specifically to enable order consolidation.
- Real-world implementations often blend the two approaches (e.g., continuously monitored inventory that is reviewed and acted upon only at scheduled intervals for administrative convenience), making the pure (Q, R) vs. (s, S) distinction somewhat idealized relative to actual ERP configuration practices.

### Key Points

- Continuous review (Q, R) fixes the order quantity and varies order timing based on real-time inventory monitoring; periodic review (s, S) fixes the review interval and varies order quantity
- Periodic review requires more safety stock than continuous review for an equivalent service level, because its protection interval spans the review period plus lead time rather than lead time alone
- Continuous review suits high-value items and situations with real-time inventory visibility; periodic review suits joint replenishment scenarios and lower-value items
- The choice between systems is a trade-off between inventory holding cost (favoring continuous review) and monitoring/ordering administrative cost (favoring periodic review)

### Related Topics

- Reorder point and safety stock calculation
- Economic Order Quantity (EOQ) model
- ABC classification analysis (differentiated system selection by item class)
- Joint replenishment and multi-item ordering coordination
- Perpetual inventory systems and real-time inventory tracking technology
- Kanban and pull-based replenishment systems
- Multi-echelon inventory optimization