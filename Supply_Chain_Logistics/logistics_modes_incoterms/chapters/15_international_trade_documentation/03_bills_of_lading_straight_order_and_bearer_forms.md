## Bills of Lading: Straight, Order, and Bearer Forms

### Definition

A bill of lading (B/L) is a transport document issued by a carrier (or its agent) acknowledging receipt of goods for shipment and setting out the terms of carriage. Bills of lading are classified by their negotiability and consignee designation into three principal forms — straight, order, and bearer — each carrying distinct legal implications for who may claim the goods and how the document may be transferred.

### Key Points

- **Three core forms**: Straight (non-negotiable, consigned to a named party), order (negotiable, consigned "to order" and transferable by endorsement), and bearer (negotiable, transferable by mere physical possession/delivery, without endorsement).
- **Negotiability is the key differentiator**: Negotiability determines whether the document of title can be transferred to a new holder during transit, enabling sale or pledge of the goods while still at sea — a critical feature for trade finance and commodity trading.
- **Document of title function**: An order or bearer B/L functions as a document of title — possession of the properly endorsed document generally entitles the holder to claim the goods from the carrier, independent of the underlying sale contract.
- **Straight B/L limitation**: A straight bill of lading names a specific consignee and is not transferable by endorsement; only the named consignee (or their authorized agent) may claim the goods, making it unsuitable where the seller intends to retain control over the goods via a negotiable document (e.g., under a letter of credit) or where the buyer may wish to resell goods in transit.
- **Order B/L default form for LC transactions**: Because letters of credit typically require the ability to transfer control of the goods to the bank as security, an order bill of lading — often "to order of shipper" and endorsed in blank or to the bank — is the standard form used in documentary credit transactions.
- **Bearer B/L risk profile**: A bearer bill of lading carries the highest transfer risk, since whoever physically possesses the document can typically claim the goods, without any endorsement or verification chain — banks and prudent traders generally avoid bearer B/Ls due to this risk.
- **Conversion between forms**: An order bill of lading endorsed in blank (i.e., signed without naming a specific endorsee) effectively functions like a bearer instrument until a subsequent holder further endorses it to a named party, reverting it to order form.

### Form Comparison

| Feature | Straight B/L | Order B/L | Bearer B/L |
| --- | --- | --- | --- |
| Consignee designation | Named party specifically | "To order" (of shipper, consignee, or bank) | No named party / "to bearer" |
| Negotiable | No | Yes | Yes |
| Transfer method | Not transferable (or only by assignment under local law) | By endorsement (blank or special) | By physical delivery alone |
| Document of title | Limited/disputed in some jurisdictions | Yes | Yes |
| Common use case | Direct sales, no resale-in-transit intent | Letter of credit transactions, trade finance | Rare; commodity trades in some markets |
| Risk if lost/stolen | Low (only named consignee can claim) | Moderate (requires endorsement chain) | High (holder can claim without verification) |
| Carrier's delivery obligation | Deliver only to named consignee | Deliver to whoever holds a properly endorsed original | Deliver to whoever presents the document |

### Negotiability and Transfer Diagram (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 820 320">
<text x="410" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Bill of Lading Forms: Transfer Mechanics (svg_diagram)</text>
<rect x="40" y="50" width="230" height="230" rx="8" fill="#d6eaf8" stroke="#2980b9" stroke-width="2" />
<text x="155" y="75" text-anchor="middle" font-size="12" font-weight="bold" fill="#1a5276">Straight B/L</text>
<circle cx="155" cy="120" r="6" fill="#2980b9" />
<text x="155" y="145" text-anchor="middle" font-size="10" fill="#1a5276">Named Consignee</text>
<text x="155" y="160" text-anchor="middle" font-size="10" fill="#1a5276">ONLY this party</text>
<text x="155" y="175" text-anchor="middle" font-size="10" fill="#1a5276">can claim goods</text>
<text x="155" y="200" text-anchor="middle" font-size="10" fill="#1a5276">No transfer chain</text>
<text x="155" y="215" text-anchor="middle" font-size="10" fill="#1a5276">possible</text>
<rect x="295" y="50" width="230" height="230" rx="8" fill="#d5f5e3" stroke="#27ae60" stroke-width="2" />
<text x="410" y="75" text-anchor="middle" font-size="12" font-weight="bold" fill="#1e8449">Order B/L</text>
<circle cx="410" cy="110" r="5" fill="#27ae60" />
<text x="410" y="128" text-anchor="middle" font-size="10" fill="#1e8449">Shipper "to order"</text>
<line x1="410" y1="116" x2="410" y2="150" stroke="#27ae60" stroke-width="2" marker-end="url(#arrow2)" />
<circle cx="410" cy="160" r="5" fill="#27ae60" />
<text x="410" y="178" text-anchor="middle" font-size="10" fill="#1e8449">Endorsed to Bank</text>
<line x1="410" y1="166" x2="410" y2="200" stroke="#27ae60" stroke-width="2" marker-end="url(#arrow2)" />
<circle cx="410" cy="210" r="5" fill="#27ae60" />
<text x="410" y="228" text-anchor="middle" font-size="10" fill="#1e8449">Endorsed to Buyer</text>
<text x="410" y="250" text-anchor="middle" font-size="10" fill="#1e8449">Transfer via endorsement</text>
<rect x="550" y="50" width="230" height="230" rx="8" fill="#fadbd8" stroke="#c0392b" stroke-width="2" />
<text x="665" y="75" text-anchor="middle" font-size="12" font-weight="bold" fill="#922b21">Bearer B/L</text>
<circle cx="665" cy="120" r="6" fill="#c0392b" />
<text x="665" y="145" text-anchor="middle" font-size="10" fill="#922b21">Whoever Holds</text>
<text x="665" y="160" text-anchor="middle" font-size="10" fill="#922b21">the Physical Document</text>
<text x="665" y="185" text-anchor="middle" font-size="10" fill="#922b21">Transfer by mere</text>
<text x="665" y="200" text-anchor="middle" font-size="10" fill="#922b21">delivery - no</text>
<text x="665" y="215" text-anchor="middle" font-size="10" fill="#922b21">endorsement needed</text>
</svg>

### Endorsement and Claim Process

```mermaid
flowchart TD
    A[Carrier Issues Bill of Lading] --> B{Which Form?}

    B -->|Straight| C[Named Consignee Identified on Face of B/L]
    C --> D[Only Named Consignee May Claim Goods at Destination]

    B -->|Order| E["Consigned To Order of Shipper/Bank"]
    E --> F[Shipper Endorses B/L - Blank or Special]
    F --> G{Further Negotiated?}
    G -->|Yes| H[Subsequent Holder Endorses Again]
    H --> G
    G -->|No, Final Holder| I[Final Endorsee Presents B/L to Claim Goods]

    B -->|Bearer| J[No Named Consignee - "To Bearer"]
    J --> K[Document Physically Transferred Without Endorsement]
    K --> L[Whoever Presents Original Document Claims Goods]

    D --> M[Carrier Releases Cargo]
    I --> M
    L --> M
```

### Example

A seller in South Korea ships electronics to a buyer in Germany under a letter of credit arrangement. The carrier issues an order bill of lading "to order of [Seller's Bank]." The seller endorses the B/L to the bank as security for financing, and once the buyer's bank confirms payment under the LC, the original bank endorses the B/L over to the buyer (or the buyer's bank), who then presents the properly endorsed original to the carrier at the destination port to claim the goods. Had the parties instead used a straight bill of lading naming the buyer directly as consignee, the bank would have had no ability to use the B/L as loan security or control the goods during the financing period, since a straight B/L cannot be endorsed to a third party — illustrating why order B/Ls are the standard choice in LC-financed transactions.

### Common Pitfalls

- **Using a straight B/L when resale-in-transit is anticipated**: If the buyer or an intermediate trader wishes to resell the goods while still at sea (common in commodity trading), a straight B/L prevents this since it names a fixed consignee with no transfer mechanism.
- **Assuming all "to order" bills are equally negotiable**: An order B/L "to order of a named consignee" (rather than "to order of shipper") requires that specific consignee's endorsement to become negotiable further — the exact "to order of" language affects the negotiation chain.
- **Losing or mishandling a bearer B/L**: Because bearer bills transfer by mere possession, loss or theft of the physical document creates substantial risk that an unauthorized party could claim the goods; this is a primary reason bearer B/Ls are used sparingly in modern practice.
- **Incomplete endorsement chains on order B/Ls**: A break or ambiguity in the chain of endorsements on an order B/L can create disputes over rightful title, particularly problematic if the carrier or a bank refuses delivery/financing pending resolution.
- **Confusing negotiability with title transfer under the sales contract**: Possession of a negotiable B/L generally entitles the holder to claim the goods from the carrier, but this is legally distinct from (though closely related to) transfer of ownership title under the underlying sales contract, which may be governed separately by applicable sales law.
- **Assuming electronic bills of lading follow identical rules**: Electronic or "eB/L" systems, increasingly used in modern trade, replicate these negotiability concepts but rely on specific technological/legal frameworks (e.g., platform-based title registries) rather than physical document possession, and their legal recognition varies by jurisdiction.

**Related Topics**

- Bill of Lading as a Document of Title
- The FCA Bill of Lading Option for Documentary Credits
- Documentary Credits and UCP 600
- Commercial Invoice and Packing List
- Electronic Bills of Lading (eB/L)
- Sea Waybills vs. Bills of Lading