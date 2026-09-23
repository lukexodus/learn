## Comparing Continuous and Periodic Review Systems

### Overview

Inventory control policies are fundamentally distinguished by *when* the system checks inventory position and *when* it triggers a replenishment decision. The two canonical review structures are continuous review (transaction-based monitoring) and periodic review (time-based monitoring). This distinction determines the mathematical form of the safety stock formula, the exposure window to demand uncertainty, and the operational infrastructure required.

### Continuous Review System (Q, R)

**Definition**

In a continuous review system, inventory position is monitored after every transaction (every withdrawal or receipt). The moment inventory position drops to or below a reorder point $R$, a fixed order quantity $Q$ is triggered immediately. This is commonly called the $(Q, R)$ policy or the reorder point/reorder quantity system.

**Key Points**

- Inventory position is tracked in real time (or near real time via perpetual inventory records)
- Order quantity $Q$ is fixed for every replenishment; only timing varies
- Order timing is variable — it depends on how fast demand depletes stock
- The relevant uncertainty window is the **lead time** $L$ only, because the system reacts instantly at $R$
- Requires perpetual inventory tracking (POS systems, barcode/RFID scanning, real-time ERP updates)

**Reorder Point Formula**

$$R = \bar{d}L + z\sigma_{d}\sqrt{L}$$

Where:

- $\bar{d}$ = average demand per period
- $L$ = lead time (in the same period units)
- $z$ = service-level factor (standard normal deviate corresponding to desired cycle-service level)
- $\sigma_d$ = standard deviation of demand per period

Safety stock isolated:

$$SS = z\sigma_{d}\sqrt{L}$$

**Order Quantity**

Typically derived from the Economic Order Quantity (EOQ) model, independent of the reorder point calculation:

$$Q^{*} = \sqrt{\frac{2D S}{H}}$$

Where $D$ = annual demand, $S$ = fixed ordering cost per order, $H$ = annual holding cost per unit.

### Periodic Review System (R, S) / (T, S)

**Definition**

In a periodic review system, inventory position is checked only at fixed review intervals $T$ (e.g., weekly, monthly). At each review, an order is placed to bring inventory position up to a target order-up-to level $S$. The order quantity therefore *varies* each cycle — it equals whatever is needed to reach $S$.

**Key Points**

- Inventory position is inspected only at discrete intervals $T$
- Order-up-to level $S$ is fixed; order quantity $Q_t = S - \text{(inventory position at review)}$ varies each cycle
- The relevant uncertainty window is $T + L$ (review period *plus* lead time), because a stockout risk exists from the moment right after a review until the next order arrives
- Does not require continuous transaction tracking — physical counts or scheduled system reviews suffice
- Naturally supports order consolidation (useful for joint replenishment across SKUs from the same supplier)

**Order-Up-To Level Formula**

$$S = \bar{d}(T + L) + z\sigma_{d}\sqrt{T + L}$$

Safety stock isolated:

$$SS = z\sigma_{d}\sqrt{T+L}$$

Note the structural difference from continuous review: the protection interval is $T+L$, not just $L$. This is the single most important mathematical distinction between the two systems.

### Side-by-Side Comparison

| Dimension | Continuous Review $(Q,R)$ | Periodic Review $(T,S)$ |
| --- | --- | --- |
| Trigger | Inventory position hits $R$ | Fixed calendar interval $T$ |
| Order quantity | Fixed $Q$ | Variable, up to $S$ |
| Order timing | Variable | Fixed |
| Protection interval | $L$ | $T + L$ |
| Safety stock (same $z$, $\sigma_d$) | Lower (shorter exposure) | Higher (longer exposure) |
| Monitoring requirement | Continuous/perpetual | Periodic snapshot |
| Infrastructure cost | Higher (real-time systems) | Lower (batch review acceptable) |
| Best fit | High-value, high-criticality SKUs (A-items) | Low-value, easily consolidated SKUs (C-items), multi-item joint orders |
| Stockout exposure pattern | Only near reorder trigger | Throughout entire review cycle |

### Why Periodic Review Requires More Safety Stock

Since safety stock scales with $\sqrt{\text{protection interval}}$, and periodic review's protection interval ($T+L$) is always greater than continuous review's ($L$ alone), periodic review systems require strictly more safety stock to hit the same cycle-service level, all else equal.

**Example**

Given: $\bar{d} = 50$ units/day, $\sigma_d = 10$ units/day, $L = 4$ days, $T = 7$ days, target service level 95% ($z = 1.645$).

Continuous review safety stock:

$$SS_{CR} = 1.645 \times 10 \times \sqrt{4} = 1.645 \times 10 \times 2 = 32.9 \approx 33 \text{ units}$$

Periodic review safety stock:

$$SS_{PR} = 1.645 \times 10 \times \sqrt{4+7} = 1.645 \times 10 \times 3.317 = 54.5 \approx 55 \text{ units}$$

The periodic system needs roughly **67% more safety stock** to achieve the identical 95% cycle-service level, purely as a consequence of the longer exposure window — this is not an inefficiency to "fix," it is a structural cost of infrequent review.

### Hybrid: (s, S) Policy

A middle-ground structure exists: review inventory position periodically (every $T$), but only place an order if position has fallen to or below a reorder point $s$; if so, order up to $S$. This combines periodic monitoring cadence with a conditional trigger, reducing unnecessary small orders compared to pure $(T,S)$ while still not requiring continuous tracking. This is frequently the practical default in modern ERP/MRP systems that run nightly or shift-based inventory jobs rather than true real-time triggers.

### Decision Framework (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 760 420" font-family="Helvetica, Arial, sans-serif">
<text x="380" y="30" text-anchor="middle" font-size="18" font-weight="bold" fill="#1a1a1a">Continuous vs Periodic Review — Decision Flow (svg_diagram)</text>
<rect x="300" y="55" width="160" height="50" rx="8" fill="#e8eef7" stroke="#3b5b8c" stroke-width="1.5" />
<text x="380" y="85" text-anchor="middle" font-size="13" fill="#1a1a1a">Item Classification</text>
<line x1="380" y1="105" x2="380" y2="135" stroke="#555" stroke-width="1.5" marker-end="url(#arrow)" />
<polygon points="380,135 470,175 380,215 290,175" fill="#fff4e0" stroke="#b8860b" stroke-width="1.5" />
<text x="380" y="172" text-anchor="middle" font-size="12">Is it high-value /</text>
<text x="380" y="188" text-anchor="middle" font-size="12">high criticality (A-item)?</text>
<line x1="290" y1="175" x2="140" y2="175" stroke="#555" stroke-width="1.5" marker-end="url(#arrow)" />
<text x="215" y="165" text-anchor="middle" font-size="11" fill="#333">Yes</text>
<rect x="40" y="150" width="200" height="55" rx="8" fill="#e0f2e9" stroke="#2e7d32" stroke-width="1.5" />
<text x="140" y="172" text-anchor="middle" font-size="12" font-weight="bold">Continuous Review (Q,R)</text>
<text x="140" y="190" text-anchor="middle" font-size="11">Tight control, low SS overhead</text>
<line x1="470" y1="175" x2="620" y2="175" stroke="#555" stroke-width="1.5" marker-end="url(#arrow)" />
<text x="545" y="165" text-anchor="middle" font-size="11" fill="#333">No</text>
<rect x="520" y="150" width="200" height="55" rx="8" fill="#fdeaea" stroke="#b03a2e" stroke-width="1.5" />
<text x="620" y="172" text-anchor="middle" font-size="12" font-weight="bold">Periodic Review (T,S)</text>
<text x="620" y="190" text-anchor="middle" font-size="11">Consolidate, accept higher SS</text>
<line x1="620" y1="205" x2="620" y2="235" stroke="#555" stroke-width="1.5" marker-end="url(#arrow)" />
<polygon points="620,235 700,265 620,295 540,265" fill="#fff4e0" stroke="#b8860b" stroke-width="1.5" />
<text x="620" y="262" text-anchor="middle" font-size="12">Multiple SKUs</text>
<text x="620" y="278" text-anchor="middle" font-size="12">same supplier?</text>
<line x1="540" y1="265" x2="400" y2="265" stroke="#555" stroke-width="1.5" marker-end="url(#arrow)" />
<text x="470" y="255" text-anchor="middle" font-size="11" fill="#333">Yes</text>
<rect x="290" y="240" width="180" height="50" rx="8" fill="#e8eef7" stroke="#3b5b8c" stroke-width="1.5" />
<text x="380" y="262" text-anchor="middle" font-size="12" font-weight="bold">Pure (T,S) Policy</text>
<text x="380" y="278" text-anchor="middle" font-size="11">Joint replenishment fit</text>
<line x1="700" y1="265" x2="700" y2="320" stroke="#555" stroke-width="1.5" marker-end="url(#arrow)" />
<text x="715" y="300" text-anchor="middle" font-size="11" fill="#333">No</text>
<rect x="600" y="320" width="180" height="50" rx="8" fill="#f2e8f7" stroke="#7d3c98" stroke-width="1.5" />
<text x="690" y="342" text-anchor="middle" font-size="12" font-weight="bold">Hybrid (s,S) Policy</text>
<text x="690" y="358" text-anchor="middle" font-size="11">Batch review, conditional order</text>
</svg>

### Protection Interval Timing Comparison (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 760 260" font-family="Helvetica, Arial, sans-serif">
<text x="380" y="25" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Exposure Window Comparison (svg_diagram)</text>

<text x="20" y="65" font-size="12" font-weight="bold">Continuous Review</text>

<line x1="20" y1="80" x2="700" y2="80" stroke="#ccc" stroke-width="2" />

<line x1="500" y1="70" x2="500" y2="90" stroke="`#2e7d32`" stroke-width="2" />

<text x="500" y="65" text-anchor="middle" font-size="10" fill="`#2e7d32`">Order Triggered at R</text>

<rect x="500" y="75" width="120" height="10" fill="`#a8d5ba`" />

<line x1="620" y1="70" x2="620" y2="90" stroke="`#2e7d32`" stroke-width="2" />

<text x="560" y="105" text-anchor="middle" font-size="11" fill="`#2e7d32`">Exposure = L only</text>

<text x="20" y="150" font-size="12" font-weight="bold">Periodic Review</text>

<line x1="20" y1="165" x2="700" y2="165" stroke="#ccc" stroke-width="2" />

<line x1="100" y1="155" x2="100" y2="175" stroke="`#b03a2e`" stroke-width="2" />

<text x="100" y="145" text-anchor="middle" font-size="10" fill="`#b03a2e`">Review at T</text>

<rect x="100" y="160" width="250" height="10" fill="`#f5b7b1`" />

<line x1="350" y1="155" x2="350" y2="175" stroke="`#b03a2e`" stroke-width="2" />

<text x="230" y="200" text-anchor="middle" font-size="11" fill="`#b03a2e`">Exposure = T + L (longer)</text>

<text x="380" y="235" text-anchor="middle" font-size="11" fill="#555">Longer exposure window → higher variance in demand-over-window → higher required safety stock</text>

</svg>

### Related Topics

- Economic Order Quantity (EOQ) derivation and sensitivity analysis
- Determining optimal review period $T$ via total cost trade-off
- Cycle-service level vs. fill rate as safety stock targets
- Multi-echelon safety stock allocation under periodic review
- ABC/XYZ classification for assigning review policy by SKU segment
- Joint replenishment and can-order policies for periodic systems
- Demand variability estimation methods (moving average vs. exponential smoothing for $\sigma_d$)