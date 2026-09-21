## Funding Valuation Adjustment FVA


### Overview

Funding Valuation Adjustment (FVA) captures the cost (or benefit) to a derivatives dealer arising from the funding requirements of an uncollateralized or imperfectly collateralized derivatives position. Where CVA and DVA (covered in the previous two topics) price counterparty and own default risk respectively, FVA prices a distinct economic friction: the fact that hedging and running a derivatives book requires actual cash funding, and that funding is not obtained at the risk-free rate — it is obtained at the dealer's own funding spread, which itself reflects the dealer's credit quality and market funding conditions. FVA is among the most conceptually contested members of the XVA family, precisely because of its documented overlap with DVA flagged in the prior topic.

### Conceptual Origin: Why Funding Matters for Derivatives

**Key Points**

- In a textbook Black-Scholes-style world with a single risk-free rate for both borrowing and lending, funding is frictionless and irrelevant to derivative valuation — discounting at the risk-free rate is sufficient.
- In practice, a dealer hedging a derivatives position (e.g., delta-hedging an option, or posting/receiving variation margin on a swap) must fund the cash flows required by that hedge — buying the underlying, posting collateral, or covering negative MTM swings — and this funding is sourced at the dealer's **actual funding rate**, not the risk-free rate.
- The gap between the dealer's funding rate and the risk-free (or OIS) rate is the **funding spread**, and FVA is, in essence, the present value of the expected funding cost (or benefit) arising from this spread applied to the expected future funding requirement of the position over its life.
- This became a first-order valuation concern industry-wide particularly following the 2008 crisis, when the historically negligible spread between unsecured interbank funding rates (e.g., LIBOR) and secured/risk-free rates (e.g., OIS) widened materially and persistently, making the funding cost of uncollateralized derivatives economically significant rather than a rounding error.

### The FVA Formula

FVA is generally decomposed into a **Funding Cost Adjustment (FCA)** for expected positive exposure requiring funding, and a **Funding Benefit Adjustment (FBA)** for expected negative exposure providing a funding benefit:

$$FVA = FCA - FBA$$



$$FCA = \int_0^T EE^*(t) \cdot s_{funding}(t) \, dt$$



$$FBA = \int_0^T ENE^*(t) \cdot s_{funding}(t) \, dt$$

Where:

- $EE^*(t)$ = discounted expected positive exposure (the same exposure profile input used for CVA)
- $ENE^*(t)$ = discounted expected negative exposure in magnitude (the same input used for DVA)
- $s_{funding}(t)$ = the dealer's funding spread over the risk-free/OIS rate at time $t$

**Key Points**

- Notice the structural parallel: FCA uses the same $EE(t)$ exposure profile as CVA, and FBA uses the same $ENE(t)$ profile as DVA — this shared dependency on identical exposure inputs, differing only in whether the multiplying spread is a default-probability-derived term (CVA/DVA) or a funding-spread term (FCA/FBA), is precisely the structural source of the FVA/DVA overlap debate discussed below.
- Where a position is fully collateralized under a well-specified CSA with cash collateral and no threshold, funding cost is largely eliminated (collateral received directly funds the hedge), meaning FVA is primarily a phenomenon of **uncollateralized or partially collateralized** trades — reinforcing why FVA became particularly significant for corporate/end-user derivatives relationships (which are frequently uncollateralized) relative to interbank/cleared trades (which are typically fully collateralized).

### The FVA/DVA Overlap Debate

This is the most actively debated conceptual issue in the XVA literature and a natural continuation of the DVA topic's controversy discussion.

**Key Points**

- **The core tension**: DVA (from the prior topic) already prices the benefit the firm receives from its own default risk on negative-MTM positions. FBA (the funding benefit component of FVA) *also* derives a benefit from negative-MTM positions, on the argument that negative MTM effectively provides the dealer with cheap funding (akin to receiving a loan at a rate related to the dealer's own credit spread). Critics argue these two effects are measuring substantially the same underlying economic phenomenon — the dealer's own credit spread — through two different adjustment mechanisms, risking double-counting.
- **One resolution view**: some practitioners and academics argue that DVA and FVA should not both be applied to the same funding-driven component simultaneously — that once a dealer's own funding spread is used to discount/adjust negative exposure via FVA, DVA (using the dealer's own default-probability-derived spread) becomes at least partially redundant, since under many modeling assumptions the dealer's CDS-implied credit spread and its unsecured funding spread are closely related (though not identical, given basis effects between CDS and cash funding markets).
- **An alternative resolution view**: treats DVA and FVA as addressing genuinely distinct economic questions — DVA relates to fair value measurement under accounting standards (a point-in-time market value question incorporating the entity's own non-performance risk per IFRS 13/ASC 820), while FVA relates to the *actual funding cost* incurred by the treasury/funding desk in running the hedging book (an operational, cash-flow-driven cost) — arguing the two need not be netted against each other because they answer different questions for different purposes (accounting fair value vs. economic/funding pricing).
- [Unverified] There is no single, universally agreed resolution to this debate in the academic or practitioner literature as of the available information; specific institutional treatment (whether DVA and FVA are applied additively, with an offset, or with one subsumed into the other) varies by firm and has been the subject of ongoing quantitative finance research and industry working group discussion, so any specific claim about "the" correct treatment should be understood as one perspective among competing views rather than a settled consensus.

### FVA Calculation Workflow

```mermaid
flowchart TD
    A[Exposure Profile: EE(t) and ENE(t) from Simulation] --> D[FVA Calculation Engine]
    B[Dealer's Own Funding Spread Curve] --> D
    C[Collateralization Status: CSA Terms per Netting Set] --> D
    D --> E{Position Collateralized?}
    E -->|Fully Collateralized, No Threshold| F[FVA Approximately Zero]
    E -->|Uncollateralized or Partial| G[Compute FCA from EE and Funding Spread]
    E -->|Uncollateralized or Partial| H[Compute FBA from ENE and Funding Spread]
    G --> I[FVA = FCA - FBA]
    H --> I
    I --> J{Overlap Adjustment Policy}
    J -->|Netted Against DVA| K[Combined DVA-FVA Adjustment]
    J -->|Applied Independently| L[Separate FVA Line Item]
    K --> M[Feed into Total XVA / Fair Value]
    L --> M
```

### Funding Spread Sources and Curve Construction

**Key Points**

- The dealer's funding spread is typically derived from the institution's own **unsecured wholesale funding curve** — reflecting the actual rate at which the dealer's treasury function can raise unsecured funds across various tenors, which in turn reflects the dealer's own credit quality (linking back to the DVA topic's own-CDS discussion) plus a funding-market liquidity/supply-demand component distinct from pure credit risk.
- Some institutions distinguish between an **internal funds transfer pricing (FTP) curve** (used for internal cost allocation between the derivatives desk and treasury) and a **market-observable funding proxy curve** (e.g., derived from the dealer's own senior unsecured bond spreads or CDS-bond basis-adjusted curves) — the choice of curve source is a significant driver of FVA magnitude and a common source of cross-institutional inconsistency in reported FVA figures.
- [Inference] Because funding spread curves are inherently institution-specific (reflecting each dealer's own credit standing and funding market access) rather than a single observable market rate, FVA calculations are generally understood to be less standardized across institutions than CVA (which references relatively more observable counterparty CDS markets), contributing to why FVA remains more contested in application than CVA, which by contrast has a more settled market-consensus methodology.

### FVA and Central Clearing

- Centrally cleared derivatives, settled through a central counterparty (CCP) with daily variation margin and mandatory initial margin, substantially reduce (though do not necessarily eliminate) the funding cost profile relative to bilateral uncollateralized trades, since the CCP's collateral requirements themselves generate funding needs (covered more specifically under the related MVA topic) even as they eliminate the *uncollateralized* funding gap that FVA specifically targets.
- This dynamic has been cited as one of several economic incentives (alongside regulatory capital treatment differences) favoring central clearing over bilateral uncollateralized trading post-crisis, since a dealer facing a CCP generally has a more standardized, and often lower, funding cost profile relative to an equivalent uncollateralized bilateral trade with a corporate end-user.

### FVA Cost/Benefit Profile Visualization (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 300">
<text x="340" y="24" text-anchor="middle" font-size="16" font-weight="bold" font-family="sans-serif">FVA: Funding Cost vs Funding Benefit (svg_diagram)</text>
<g font-family="sans-serif" font-size="12">
<line x1="60" y1="170" x2="620" y2="170" stroke="#333" stroke-width="1.5" />
<line x1="60" y1="40" x2="60" y2="290" stroke="#333" stroke-width="1" />
<text x="330" y="310" text-anchor="middle">Time</text>



```
<path d="M 60 170 C 180 100, 300 80, 380 85 C 460 90, 560 130, 620 170" fill="#c62828" fill-opacity="0.2" stroke="#c62828" stroke-width="2.5" />
<text x="180" y="95" fill="#c62828" font-weight="bold">FCA: Cost from EE(t)</text>

<path d="M 60 170 C 180 220, 300 250, 380 245 C 460 240, 560 200, 620 170" fill="#2e7d32" fill-opacity="0.2" stroke="#2e7d32" stroke-width="2.5" />
<text x="180" y="270" fill="#2e7d32" font-weight="bold">FBA: Benefit from ENE(t)</text>

<text x="30" y="105" font-size="11">Owed to firm</text>
<text x="30" y="245" font-size="11">Owed by firm</text>
```

</g>
</svg>

### Accounting vs. Pricing Treatment of FVA

**Key Points**

- Unlike CVA and DVA, which have relatively explicit accounting standard grounding (IFRS 13/ASC 820 non-performance risk requirements, as discussed in the DVA topic), FVA's accounting treatment has historically been less uniformly codified — some institutions incorporate FVA into reported fair value, others treat it primarily as an internal pricing/funding cost allocation tool without a formal balance sheet fair value adjustment, reflecting the unresolved DVA/FVA overlap debate discussed above playing out differently across institutional accounting policy choices.
- [Unverified] The current state of accounting standard guidance specifically addressing FVA (as distinct from the more established DVA/CVA guidance) and its consistency or divergence across major accounting frameworks should be verified against current authoritative accounting literature (IFRS/FASB pronouncements) for any specific financial reporting application, given this is an area where practice has been described as less settled than for CVA/DVA.

### Common Implementation Failure Modes

- **Double-counting DVA and FVA without an explicit netting policy**: applying both adjustments in full without a documented institutional policy on how the overlap is resolved, potentially overstating the funding-benefit-driven component of fair value.
- **Using an inappropriate funding curve for the trade's actual funding profile**: applying a generic institutional FTP curve to a trade with genuinely different funding characteristics (e.g., a trade funded via a specific secured facility rather than general unsecured wholesale funding), mismatching the funding cost assumption to actual economic funding reality.
- **Ignoring collateralization nuances**: treating a partially collateralized trade (e.g., with a non-zero threshold or one-way CSA favoring only the counterparty) as either fully funded or fully unfunded, when the actual funding profile sits between these extremes and requires the same threshold/MTA-aware simulation refinement discussed for exposure measurement generally.
- **Static funding spread assumptions**: using a point-in-time funding spread rather than a term structure that can evolve, understating FVA volatility particularly during funding market stress periods (echoing the historical 2008-era widening that originally motivated FVA's prominence).
- **Failing to distinguish FTP/internal transfer pricing from external fair value reporting**: conflating internal desk-level funding cost allocation (a management accounting/pricing tool) with external financial statement fair value adjustments, which may legitimately follow different conventions for different purposes.

### Worked Example

Continuing the running swap example: suppose the same uncollateralized 5-year swap has an average expected positive exposure (EE) of approximately $3 million (as used in the CVA topic) and an average expected negative exposure (ENE) of approximately $4 million (as used in the DVA topic), and the dealer's own funding spread over OIS is approximately 0.80% (80 basis points) across the relevant tenor.

- **FCA** (cost from funding the positive-exposure periods): approximately $\$3\text{ million} \times 0.80\% \times 5\text{ years (illustrative time-weighted approximation)} \approx \$120{,}000$.
- **FBA** (benefit from the funding relief during negative-exposure periods): approximately $\$4\text{ million} \times 0.80\% \times 5\text{ years} \approx \$160{,}000$.
- **FVA** = FCA − FBA ≈ $120,000 − $160,000 ≈ **−$40,000** (a net funding *benefit* in this illustrative scenario, since the negative-exposure funding benefit outweighs the positive-exposure funding cost).
- If the institution's policy nets FVA against DVA (per the overlap debate above) rather than applying both independently, this FBA-driven benefit would need to be reconciled against the DVA benefit already computed in the prior topic (~$72,000) to avoid double-counting the same underlying own-credit-spread-driven economic effect — a concrete illustration of why institutional policy on this overlap materially affects the final reported XVA figure for an identical trade.

**Next Steps**

- Margin Valuation Adjustment (MVA) and initial margin funding costs
- KVA (Capital Valuation Adjustment) and regulatory capital cost pricing
- Funds transfer pricing (FTP) curve construction methodologies
- Central clearing funding cost comparison vs. bilateral uncollateralized trading
- Academic literature on the FVA/DVA double-counting debate
- CSA threshold/MTA impact on partial collateralization funding profiles
- Total XVA aggregation and consistent cross-adjustment netting policy design