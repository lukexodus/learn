## Category-Specific Dual Sourcing Considerations

### Overview

Dual sourcing is not a universal policy applied at a fixed ratio across all spend. Its rationale, structure, and cost tolerance differ sharply depending on the Kraljic category a given item falls into. Applying a one-size-fits-all dual sourcing mandate ("always maintain two suppliers") ignores the fact that the *reason* for dual sourcing — and therefore its optimal design — is category-dependent.

### Why Category Matters for Dual Sourcing Design

$$\text{Dual Sourcing Justification} = f(\text{Supply Risk}, \text{Switching Cost}, \text{Volume Split Feasibility})$$

The same nominal decision ("use two suppliers") answers a completely different problem in each quadrant: in Strategic items it's insurance against catastrophic disruption; in Leverage items it's a price-competition mechanism; in Bottleneck items it's risk coverage at minimal volume; in Non-Critical items it's usually unjustified.

```mermaid
quadrantChart
    title Dual Sourcing Rationale by Category (svg_diagram)
    x-axis Low Supply Risk --> High Supply Risk
    y-axis Low Profit Impact --> High Profit Impact
    quadrant-1 Strategic: Risk Insurance
    quadrant-2 Bottleneck: Continuity Coverage
    quadrant-3 Non-Critical: Rarely Justified
    quadrant-4 Leverage: Price Competition
```

### Strategic Items: Risk-Driven Dual Sourcing

**Key Points**

- Primary driver: catastrophic disruption risk, not price. A single-source failure in a Strategic category can halt production entirely.
- Volume split is typically asymmetric and stable (e.g., 70/30 or 80/20) rather than competitively rebalanced — the secondary supplier exists for continuity, not price pressure.
- Requires joint qualification investment: both suppliers must pass the same technical/quality validation, which is often the largest cost of dual sourcing here.
- Contractual structure: long-term agreements with both suppliers, often with capacity reservation clauses guaranteeing the secondary source can scale up if the primary fails.
- Cost tolerance: organizations accept a price premium (secondary suppliers rarely match the primary's economies of scale) as insurance cost.

**Example**

An automotive OEM dual-sources a safety-critical semiconductor, qualifying both a primary fab (80% of volume, lowest cost) and a secondary fab (20% of volume, higher unit cost) specifically to survive a single-fab outage, accepting the blended cost premium as risk mitigation spend.

### Bottleneck Items: Continuity-Focused Dual Sourcing

**Key Points**

- Primary driver: identical risk-avoidance logic to Strategic items, but at far lower spend volume — this makes the qualification cost of a second supplier proportionally expensive.
- Common alternative to full dual sourcing: qualify a secondary supplier but keep them "dormant" (approved but not actively ordering) until triggered by primary-supplier failure, avoiding ongoing dual-supplier management overhead.
- Volume split, when active, is often heavily skewed (90/10 or a pure backup arrangement) since the category's low profit impact doesn't justify the transactional cost of managing two active relationships.
- [Inference] Because Bottleneck items are frequently niche or proprietary, true dual sourcing may be technically infeasible (patent-protected components, single certified manufacturer) — in these cases risk mitigation shifts to inventory buffering and long-term supply agreements rather than a second source.

**Example**

A manufacturer sources a specialty gasket from a single certified supplier. True dual sourcing is infeasible due to certification cost relative to spend, so the mitigation strategy instead combines a qualified-but-dormant backup supplier with 120 days of buffer inventory.

### Leverage Items: Competition-Driven Dual (or Multi) Sourcing

**Key Points**

- Primary driver: maintaining negotiating leverage and price competition, not disruption risk — supply risk is already low by definition in this quadrant.
- Volume split is actively and periodically rebalanced based on competitive performance (price, quality, delivery scorecards), often quarterly or annually.
- Structure: shorter contract terms deliberately preserve the ability to shift volume, unlike the long-term commitments typical of Strategic dual sourcing.
- Three-or-more supplier splits are common here (multi-sourcing rather than strict dual sourcing) since the goal is maximizing competitive tension rather than managing risk exposure.

**Example**

A packaging buyer splits corrugated box volume 50/50 between two qualified suppliers, shifting the split to 65/35 each quarter based on RFQ results, using the threat of volume loss as continuous price pressure rather than as insurance against supply failure.

### Non-Critical Items: Dual Sourcing Rarely Justified

**Key Points**

- The administrative cost of managing two supplier relationships typically exceeds any savings or risk benefit for low-spend, low-risk categories.
- Standard approach: single-source or consolidate to one preferred supplier/catalog to minimize transaction cost, the opposite instinct of Strategic/Bottleneck categories.
- Exception: [Inference] categories with a very large supplier base and negligible switching cost sometimes use light dual sourcing purely for catalog price benchmarking, though this is a minor optimization rather than a risk or leverage strategy.

### Comparative Framework

| Category | Dual Sourcing Driver | Volume Split Pattern | Contract Length | Cost Tolerance |
| --- | --- | --- | --- | --- |
| Strategic | Disruption risk | Asymmetric, stable (e.g. 80/20) | Long-term | Accepts premium |
| Bottleneck | Continuity | Skewed or dormant backup | Variable | Accepts qualification cost |
| Leverage | Price competition | Rebalanced periodically | Short-to-medium | Cost-neutral/savings-seeking |
| Non-Critical | Rarely justified | N/A — typically single-source | Short | Minimizes admin cost |

### Common Cross-Category Pitfalls

- Applying Leverage-quadrant logic (frequent rebalancing, short contracts) to Strategic items — this undermines the long-term qualification investment needed for true risk continuity.
- Applying Strategic-quadrant logic (long-term premium-tolerant dual sourcing) to Leverage items — this forfeits the competitive tension that is the entire point of dual sourcing in that quadrant.
- Mandating dual sourcing uniformly regardless of category, inflating supplier management overhead in Non-Critical and low-spend Bottleneck categories without a proportional risk or cost benefit.

### Practical Application Workflow

**Steps to design category-appropriate dual sourcing:**

1. Confirm Kraljic classification for the category before designing a dual sourcing structure — the classification determines the *purpose* of dual sourcing, not just whether to use it.
2. For Strategic items, prioritize joint qualification and capacity-reservation clauses over volume competition.
3. For Bottleneck items, evaluate dormant/backup qualification and inventory buffering as lower-cost alternatives to full active dual sourcing.
4. For Leverage items, design short contract cycles with scorecard-driven volume rebalancing to sustain competitive pressure.
5. For Non-Critical items, default to single-sourcing/consolidation unless a specific, quantified exception applies.

**Related Topics**

- Kraljic Matrix classification methodology (prerequisite framework)
- Supplier qualification and dual-source validation processes
- Capacity reservation clause design for Strategic contracts
- Volume allocation and scorecard-driven rebalancing mechanics
- Buffer inventory sizing for Bottleneck category risk mitigation