## FOB (Free On Board)

### Overview

FOB (Free On Board) requires the seller to deliver goods by loading them on board the vessel nominated by the buyer at the named port of shipment. FOB is one of the oldest and most commercially recognized Incoterms rules, historically the default term for international sea trade, though modern practice has shifted toward FCA for containerized shipments due to a well-documented risk-transfer ambiguity.

### Applicable Transport Mode

- FOB belongs to the "Sea and Inland Waterway Transport" category exclusively. It is not appropriate for containerized cargo delivered to a terminal in advance of vessel loading, or for any non-vessel-based transport mode.

### Key Points: Obligation Summary

- **Delivery point**: on board the vessel nominated by the buyer, at the named port of shipment.
- **Risk transfer**: occurs when the goods are loaded on board the vessel — historically described as passing "the ship's rail," though the 2010 and 2020 editions clarified this as simply "on board," removing the older, more ambiguous rail-crossing concept.
- **Loading onto vessel**: the seller's responsibility, cost, and risk up to and including placing goods on board.
- **Export clearance**: the seller's responsibility.
- **Import clearance**: the buyer's responsibility.
- **Carriage**: the buyer arranges and pays for the ocean carriage from the port of shipment onward; the seller has no carriage obligation.
- **Insurance**: neither party is obligated to insure under FOB itself.

### Article-by-Article Breakdown (Seller/Buyer)

| Article | Seller Obligation (A) | Buyer Obligation (B) |
| --- | --- | --- |
| 1. General Obligations | Provide goods and invoice per contract | Pay the price |
| 2. Delivery | Load goods on board vessel nominated by buyer | Take delivery once on board |
| 3. Transfer of Risk | Ends when goods on board the vessel | Begins at same point |
| 4. Carriage | No obligation to contract carriage | Contract and pay for carriage from port of shipment |
| 5. Insurance | No obligation | No obligation, but buyer bears risk from on-board point |
| 6. Delivery/Transport Document | Provide proof of on-board delivery (e.g., mate's receipt, bill of lading) | Accept conforming document |
| 7. Export/Import Clearance | Handle export clearance | Handle import clearance |
| 8. Checking/Packaging/Marking | Package and mark goods appropriately | No standard obligation |
| 9. Allocation of Costs | Costs up to loading goods on board | Carriage and costs from that point onward |
| 10. Notices | Notify buyer once goods loaded on board | Notify seller of vessel name, loading point, and required delivery time |

### Diagram: FOB Delivery and Risk Transfer Point (svg_diagram)

```mermaid
flowchart LR
    A["Seller's Location svg_diagram"] -->|Seller transports and clears goods for export| B["Port of Shipment"]
    B -->|Seller loads goods on board nominated vessel| C["RISK TRANSFERS HERE - On Board"]
    C -->|Buyer arranges and pays ocean carriage| D["Port of Destination"]
    style C fill:#f96,stroke:#333
```

### Example

A coffee bean exporter in Colombia sells to a roaster in the Netherlands under "FOB Cartagena Incoterms® 2020." The seller transports the beans to the port, handles Colombian export clearance, and loads the beans on board the vessel nominated by the buyer's freight forwarder. Risk transfers to the buyer the moment the beans are on board. The buyer arranges and pays for ocean freight to Rotterdam, handles Dutch import clearance, and bears risk of any loss or damage occurring during the ocean voyage.

### The Containerization Problem: Why FCA Is Often Preferred

- **Key Points**
  - FOB's risk-transfer point ("on board the vessel") was designed for an era when cargo was loaded piece-by-piece directly from dockside into a ship's hold — a process where the seller retained physical control of the goods right up until loading.
  - Modern containerized shipping does not work this way: containers are typically delivered by the seller's trucker to a container terminal or container freight station days *before* the vessel arrives and is loaded, meaning the seller loses physical control of the goods well before the FOB risk-transfer point (on board) technically occurs.
  - [Inference] This creates a documented "gap" period during which the seller nominally still bears risk under a strict reading of FOB, despite having no practical ability to monitor, protect, or control the goods once they are handed to the terminal operator — a mismatch between legal risk allocation and practical control that has led international trade bodies and legal commentators to recommend FCA for container shipments.
  - The ICC's own guidance notes accompanying the Incoterms 2020 rules explicitly caution against using FOB (and CFR/CIF) for containerized cargo for this reason, recommending FCA (and CPT/CIP) instead.

### FOB vs. FAS: Key Distinction

| Feature | FOB | FAS |
| --- | --- | --- |
| Delivery/risk transfer point | Goods loaded on board vessel | Goods placed alongside vessel |
| Loading onto vessel | Seller's risk and cost | Buyer's risk (loading occurs after FAS delivery) |
| Typical cargo | Bulk/break-bulk loaded directly aboard | Bulk/break-bulk requiring dockside positioning before loading |

### Persistent Commercial Use Despite Container Risk

- [Inference] Despite the ICC's guidance favoring FCA for containers, FOB remains extremely widely used in commercial practice — including for containerized cargo — due to long-standing market familiarity, historical convention in letters of credit and trade finance documentation, and inertia in standard-form contracts across many industries.
- Practitioners should recognize that while FOB continues to be commercially prevalent, its use for containerized cargo carries the documented risk-transfer ambiguity described above, and parties who want precise risk allocation aligned with physical control may prefer explicitly switching to FCA.

### When FOB Is Typically Used

- Bulk commodity trade (grain, coal, oil, ore) where cargo is loaded directly onto the vessel without container handling.
- Long-standing trade relationships or industries where FOB is the deeply entrenched market convention, even for some containerized trades.
- Situations where trade finance documentation (letters of credit) specifically requires FOB terminology due to bank or industry practice.

### Common Misconceptions

- **Misconception**: FOB is the best or most precise term for any ocean container shipment.

  **Clarification**: The ICC's own guidance recommends FCA over FOB for containerized cargo, since FOB's on-board risk-transfer point creates a documented gap between physical control and legal risk allocation for containers delivered to a terminal in advance.
- **Misconception**: Under FOB, risk transfers once goods cross the "ship's rail."

  **Clarification**: The ship's rail concept was removed in the 2010 and 2020 editions; risk now transfers simply when goods are placed "on board" the vessel, a clarification intended to eliminate ambiguity about the exact moment of crossing an imaginary vertical plane at the ship's side.
- **Misconception**: FOB and FAS are interchangeable terms.

  **Clarification**: They differ in whether the seller's obligation includes loading onto the vessel (FOB) or ends once goods are positioned alongside the vessel (FAS) — a meaningful difference in risk allocation during the loading operation.

**Key Points**

- FOB requires the seller to deliver goods by loading them on board the vessel nominated by the buyer at the named port of shipment; risk transfers upon loading.
- Restricted to sea and inland waterway transport; historically the default term for bulk/break-bulk ocean cargo.
- The ICC recommends FCA over FOB for containerized cargo due to a documented risk-transfer gap when containers are delivered to a terminal before vessel loading.
- Despite this guidance, FOB remains commercially prevalent across many industries and trade finance practices.

**Related Topics**

- FCA (Free Carrier): The Recommended Alternative for Containerized Cargo
- FAS (Free Alongside Ship): Full Rule Breakdown
- CFR (Cost and Freight): Full Rule Breakdown
- Classification by Mode of Transport
- Letters of Credit and Traditional FOB Documentation Practice
- Bulk Commodity Trading Practices and Incoterms Selection