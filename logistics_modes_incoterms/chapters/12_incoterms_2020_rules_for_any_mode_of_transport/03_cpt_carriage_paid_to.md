## CPT (Carriage Paid To)

### Overview

CPT (Carriage Paid To) requires the seller to contract for and pay the cost of carriage to a named destination, while risk of loss or damage transfers to the buyer much earlier — at the point the goods are handed to the first carrier. This split between where cost is paid and where risk transfers is the defining structural feature of CPT and the other Group C terms, and it is one of the most frequently misunderstood aspects of Incoterms among newer practitioners.

### Applicable Transport Mode

- CPT belongs to the "Any Mode or Modes of Transport" category, suitable for road, rail, air, sea, or multimodal combinations.

### Key Points: Obligation Summary

- **Delivery/risk transfer point**: when goods are handed over to the first carrier contracted by the seller (or, if multiple carriers are used successively, at handover to the first carrier), not at the named destination.
- **Cost responsibility**: the seller pays for carriage all the way to the named destination point, even though risk has already passed to the buyer earlier in the journey.
- **Export clearance**: the seller's responsibility.
- **Import clearance**: the buyer's responsibility.
- **Insurance**: neither party is obligated to insure under CPT itself (unlike CIP, its insurance-inclusive counterpart); each party should insure according to their own risk exposure.
- **Named destination vs. named place of delivery**: CPT contracts should ideally specify both — the place where risk transfers (handover to first carrier) and the destination to which the seller must pay carriage — since these are often different locations and a source of contract ambiguity if only one is stated.

### Article-by-Article Breakdown (Seller/Buyer)

| Article | Seller Obligation (A) | Buyer Obligation (B) |
| --- | --- | --- |
| 1. General Obligations | Provide goods and invoice per contract | Pay the price |
| 2. Delivery | Hand goods to first carrier | Take delivery from carrier at destination |
| 3. Transfer of Risk | Ends at handover to first carrier | Begins at handover to first carrier |
| 4. Carriage | Contract and pay for carriage to named destination | No obligation to contract carriage |
| 5. Insurance | No obligation | No obligation, but buyer bears transit risk from handover point |
| 6. Delivery/Transport Document | Provide transport document (e.g., waybill, multimodal transport document) | Accept conforming transport document |
| 7. Export/Import Clearance | Handle export clearance | Handle import clearance |
| 8. Checking/Packaging/Marking | Package and mark goods appropriately | No standard obligation |
| 9. Allocation of Costs | Costs up to and including carriage to named destination | Costs from arrival at destination onward, plus import duties |
| 10. Notices | Notify buyer of dispatch and delivery details | Notify seller of any buyer-controlled requirements |

### Diagram: CPT Cost/Risk Split (svg_diagram)

```mermaid
flowchart LR
    A["Seller's Location svg_diagram"] -->|Goods handed to first carrier| B["RISK TRANSFERS HERE"]
    B -->|Seller continues paying freight| C["Carriage in Transit"]
    C --> D["Named Destination"]
    D -->|Cost obligation ends here| E["Buyer takes delivery, handles import clearance"]
    style B fill:#f96,stroke:#333
    style D fill:#69f,stroke:#333
```

### Example

A seller of industrial equipment in Italy sells to a buyer in Poland under "CPT Warsaw Incoterms® 2020." The seller books and pays a trucking company to carry the goods from Milan to Warsaw. The moment the goods are handed to the trucking company in Milan, risk of loss or damage transfers to the buyer — even though the seller continues to pay the freight cost all the way to Warsaw. If the shipment is damaged in transit due to an accident, the buyer (not the seller) bears that loss and would need to pursue any recovery through their own cargo insurance, despite the seller having paid for the transport.

### Why the Cost/Risk Split Matters Commercially

- [Inference] Because the buyer bears risk during transit despite not having selected or contracted the carrier, buyers using CPT (and CIP) terms are strongly advised to obtain their own cargo insurance covering the transit period, since the seller under CPT has no insurance obligation.
- This structural split is precisely why the ICC created CIP as a companion rule — CIP retains the same cost/risk split as CPT but adds a mandatory seller insurance obligation, giving buyers a built-in insurance safety net rather than relying on their own arrangements.
- Disputes under CPT most commonly arise when parties fail to clearly distinguish the "place of delivery" (handover to first carrier, where risk transfers) from the "named destination" (where seller's cost obligation ends), particularly in multimodal shipments involving several carriers.

### CPT vs. CIP: Choosing Between Them

| Feature | CPT | CIP |
| --- | --- | --- |
| Cost of carriage to destination | Seller pays | Seller pays |
| Risk transfer point | Handover to first carrier | Handover to first carrier |
| Insurance obligation | None | Seller must procure Institute Cargo Clauses A (or equivalent) minimum coverage |
| Typical use case | Buyer has own insurance program or accepts uninsured transit risk | Buyer wants seller-arranged insurance coverage built into the transaction |

### When CPT Is Typically Used

- Multimodal shipments where the seller wants to control and pay for the transport chain but the buyer is comfortable managing its own insurance arrangements.
- Transactions where the buyer has an existing corporate cargo insurance policy covering all inbound shipments, making seller-procured insurance (as under CIP) redundant.
- B2B trade relationships with established trust where the parties do not require the additional insurance formality of CIP.

### Common Misconceptions

- **Misconception**: Under CPT, the seller bears risk until the goods reach the named destination since the seller pays for carriage that far.

  **Clarification**: Risk transfers much earlier — at handover to the first carrier — regardless of how far the seller's freight payment obligation extends.
- **Misconception**: CPT and CIP are functionally identical.

  **Clarification**: The delivery and risk-transfer mechanics are identical, but CIP additionally obligates the seller to procure cargo insurance meeting a specified minimum coverage level; CPT includes no such insurance obligation.
- **Misconception**: The "named destination" in a CPT contract is the same as the "place of delivery."

  **Clarification**: These are often different locations — the place of delivery is where risk transfers (handover to first carrier), while the named destination is simply the point to which the seller must pay for carriage; contracts should specify both clearly to avoid ambiguity.

**Key Points**

- CPT requires the seller to pay carriage to a named destination while risk transfers earlier, at handover to the first carrier — creating a cost/risk split.
- Applicable to any transport mode; commonly used in multimodal shipments.
- No insurance obligation exists under CPT; buyers bear transit risk and should arrange their own cargo insurance.
- CIP is the insurance-inclusive counterpart to CPT, sharing identical delivery and risk-transfer mechanics.

**Related Topics**

- CIP (Carriage and Insurance Paid To): Full Rule Breakdown
- CIF vs. CIP: Insurance Coverage Requirements Explained
- Cargo Insurance Considerations for Buyers Under Group C Terms
- The Four Incoterms Groups: E, F, C, and D
- Multimodal Transport Documentation Requirements
- Risk Transfer Points: A Term-by-Term Comparison Across All 11 Incoterms