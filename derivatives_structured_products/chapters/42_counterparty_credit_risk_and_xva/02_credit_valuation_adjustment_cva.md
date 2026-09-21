## Credit Valuation Adjustment CVA


### Overview

Credit Valuation Adjustment (CVA) is the market value of counterparty credit risk embedded in a derivatives portfolio — the amount by which a derivative's risk-free value must be reduced to reflect the possibility that the counterparty defaults before all contractual obligations are fulfilled. CVA converts the exposure profiles developed in the preceding topic (EE, PFE, EPE) into a priced adjustment by combining them with the counterparty's probability of default and expected loss given default. CVA is the foundational member of the broader XVA family (DVA, FVA, MVA, KVA) covered later in this chapter, and is the component with the longest regulatory and accounting history.

### Conceptual Definition

**Key Points**

- CVA represents the expected loss to the surviving party from counterparty default, computed as the risk-neutral expectation of exposure at default, weighted by default probability and loss severity, discounted back to today.
- Unlike a static credit spread adjustment, CVA is **exposure-path-dependent**: it requires knowing not just the counterparty's creditworthiness but the full distribution of possible future portfolio values at every point where default could occur, which is why CVA calculation builds directly on the simulation-based exposure methodology from the previous topic.
- CVA is a component of **fair value accounting** for derivatives under both IFRS 13 and US GAAP (ASC 820), meaning it is not merely a regulatory capital concept but directly affects reported P&L and balance sheet valuation of derivative positions.

### The CVA Formula

The standard (unilateral) CVA formula integrates expected exposure against the counterparty's default probability term structure:

$$CVA = (1 - R) \int_0^T EE^*(t) \, dPD(t)$$

Or in the more commonly implemented discretized form:

$$CVA = (1-R) \sum_{i=1}^{N} EE^*(t_i) \cdot [PD(t_{i-1}, t_i)] \cdot DF(t_i)$$

Where:

- $R$ = recovery rate of the counterparty (so $1-R$ = loss given default, LGD)
- $EE^*(t_i)$ = discounted expected positive exposure at time $t_i$
- $PD(t_{i-1}, t_i)$ = marginal (incremental) probability of default in the interval between $t_{i-1}$ and $t_i$, derived from the counterparty's default probability term structure
- $DF(t_i)$ = discount factor to time $t_i$ (if not already embedded in the exposure term)

**Key Points**

- The exposure term $EE^*(t)$ is exactly the risk-neutral expected exposure profile computed via the Monte Carlo simulation methodology described in the exposure measurement topic — CVA calculation does not require a separate exposure model, but consumes the output of that process directly.
- Default probabilities are typically derived from the counterparty's **credit default swap (CDS) spread curve** where liquid CDS exists (risk-neutral, market-implied PDs), or from bond spreads, or — for counterparties without traded credit instruments — proxy/mapping methodologies using rating-based or sector/region CDS index proxies.
- Recovery rate $R$ is often assumed at a standard market convention (commonly 40% for senior unsecured, i.e., LGD of 60%) unless counterparty-specific or seniority-specific information suggests otherwise; this assumption directly scales CVA linearly given the $(1-R)$ multiplier.

### Unilateral vs. Bilateral CVA

- **Unilateral CVA**: considers only the counterparty's default risk, ignoring the possibility that the calculating firm itself might default first — this was the standard approach pre-crisis and remains conceptually the "pure" CVA definition.
- **Bilateral CVA**: incorporates both the counterparty's default risk (CVA proper) and the firm's own default risk from the counterparty's perspective (giving rise to **DVA**, Debit Valuation Adjustment — covered as its own related topic), recognizing that a derivative's value to the counterparty is symmetrically affected by the firm's own credit quality.

$$\text{Bilateral CVA} = CVA - DVA$$

[Inference] The bilateral framework became more prominent in valuation practice and accounting guidance particularly following the 2008 crisis period, when both counterparty and self-credit risk symmetry received significantly more attention in fair value measurement standards (IFRS 13 explicitly requires considering both); DVA itself remains conceptually and practically debated (e.g., regarding whether a firm can realistically monetize gains from its own credit deterioration), a nuance better explored fully under the dedicated DVA topic in this chapter.

### CVA Calculation Workflow

```mermaid
flowchart TD
    A[Exposure Profile: EE(t) from Simulation] --> E[CVA Integration Engine]
    B[Counterparty CDS Curve or Proxy Spread] --> C[Bootstrap Default Probability Term Structure]
    C --> E
    D[Recovery Rate Assumption] --> E
    E --> F[Compute CVA = Sum over time of EE times Marginal PD times LGD]
    F --> G{Netting Set Level or Trade Level?}
    G -->|Netting Set| H[Single CVA Number per Counterparty Netting Set]
    G -->|Incremental Trade CVA| I[Marginal CVA Contribution of New Trade]
    H --> J[Feed into Fair Value Adjustment - IFRS 13 / ASC 820]
    H --> K[Feed into Regulatory Capital - CVA Capital Charge]
    I --> L[Pre-Trade Pricing Decision Support]
```

### Incremental / Marginal CVA and Pricing Application

**Key Points**

- Because CVA is generally computed at the **netting set level** (reflecting the netting benefit discussed in the exposure topic), adding a new trade to an existing netting set typically does *not* increase CVA by that trade's standalone CVA — the marginal CVA contribution depends on how the new trade interacts with the existing portfolio's exposure profile.
- A new trade that is negatively correlated with the existing netting set's exposure (reducing portfolio-level exposure) can have **negative incremental CVA**, effectively making the desk *better off* from a counterparty risk perspective by adding the trade, even though the trade's standalone CVA (computed in isolation) would be positive.
- This non-additivity is a critical desk-level pricing consideration: sales/trading desks pricing a new trade with an existing counterparty should reference incremental CVA (portfolio-level CVA with the new trade minus portfolio-level CVA without it), not standalone trade CVA, to correctly price the true marginal counterparty risk cost being added to the book.

$$\text{Incremental CVA} = CVA(\text{Portfolio} + \text{New Trade}) - CVA(\text{Portfolio})$$

### CVA Desk Function and Hedging

- Many large derivatives dealers operate a centralized **CVA desk** (or XVA desk) that: (1) charges CVA to originating trading desks as a cost of doing business with a given counterparty, effectively centralizing and pricing counterparty risk across the firm; and (2) manages the resulting aggregate CVA risk through hedging.
- **CVA hedging instruments** typically include: single-name CDS (hedging counterparty default probability risk), CDS index products (for counterparties without liquid single-name CDS, or for systematic/portfolio-level credit spread risk), and market risk hedges (interest rate, FX, equity derivatives) to hedge the exposure component's sensitivity to underlying market factor moves.
- **CVA Greeks**: analogous to standard derivative Greeks but applied to the CVA number itself — CS01 (sensitivity to counterparty credit spread moves), and sensitivities to the underlying market risk factors driving the exposure profile (e.g., CVA delta with respect to interest rates for a swap portfolio) — these drive the CVA desk's hedging program.
- [Unverified] The specific organizational structure (whether CVA/XVA desk functions are centralized, how P&L is attributed between originating desks and the XVA desk, and precise hedging mandates) varies significantly by institution and is generally a matter of internal desk structure rather than a universally standardized practice, so any specific institutional arrangement should be verified against that institution's actual operating model.

### Regulatory Capital Treatment of CVA

**Key Points**

- Following the 2008 crisis, analysis attributed a substantial portion of crisis-period derivatives losses to CVA volatility (mark-to-market losses from counterparty credit spread widening) rather than actual counterparty defaults — this observation directly motivated the introduction of a dedicated **CVA capital charge** under Basel III, distinct from the default/exposure-based counterparty credit risk capital charge covered in the exposure measurement topic.
- The CVA capital charge has evolved through several iterations: the original Basel III CVA charge (post-2010), and subsequently the **Basel Committee's revised CVA framework** (part of the broader Basel III finalization/"Basel IV" package), introducing standardized (SA-CVA) and basic (BA-CVA) approaches, with the more sophisticated internal-model-based CVA VaR approach largely phased out in the revised framework in favor of these more standardized methods.
- [Unverified] The precise implementation timeline, calibration parameters, and jurisdiction-specific adoption status of the revised CVA capital framework (SA-CVA/BA-CVA) should be verified against current Basel Committee publications and local regulatory implementing rules, since Basel framework finalization and national adoption timelines have been subject to periodic revision and jurisdictional divergence.

### CVA Sensitivity Profile Visualization (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 300">
<text x="340" y="24" text-anchor="middle" font-size="16" font-weight="bold" font-family="sans-serif">CVA as Exposure × Default Probability (svg_diagram)</text>
<g font-family="sans-serif" font-size="12">
<line x1="60" y1="250" x2="620" y2="250" stroke="#333" stroke-width="1.5" />
<line x1="60" y1="250" x2="60" y2="50" stroke="#333" stroke-width="1.5" />
<text x="330" y="280" text-anchor="middle">Time</text>



```
<path d="M 60 250 C 180 130, 300 100, 380 110 C 460 120, 560 200, 620 250" fill="none" stroke="#1565c0" stroke-width="2.5" fill-opacity="0.1" />
<text x="200" y="115" fill="#1565c0" font-weight="bold">Expected Exposure EE(t)</text>

<path d="M 60 250 L 620 90" fill="none" stroke="#c62828" stroke-width="2" stroke-dasharray="5,3" />
<text x="480" y="120" fill="#c62828" font-weight="bold">Cumulative PD(t)</text>

<path d="M 60 250 C 150 235, 250 190, 380 195 C 480 200, 560 230, 620 250" fill="#2e7d32" fill-opacity="0.35" stroke="#2e7d32" stroke-width="2" />
<text x="330" y="215" fill="#1b5e20" font-weight="bold" text-anchor="middle">CVA Contribution (product)</text>
```

</g>
</svg>

### CVA and the Structured Products Connection

**Key Points**

- For structured products (per the earlier chapter's topics), CVA is directly relevant on two levels: (1) the **hedge-side CVA** the issuing bank faces on its own hedging derivatives with its trading counterparties, feeding into the bank's internal cost of manufacturing the product; and (2) more directly relevant to the retail investor, the issuer's own credit risk (captured in the KID's CRM/SRI components, discussed in the disclosure topic) is conceptually the *investor-facing analog* of CVA — the investor is effectively bearing an uncollateralized, unilateral CVA-like exposure to the note issuer, without the benefit of netting, collateral, or CDS-based hedging available to institutional counterparties.
- This asymmetry — institutional counterparties can observe, price, and hedge CVA via CDS markets and CSA collateralization, while retail note investors generally cannot — is part of the economic rationale for the enhanced disclosure requirements (KID credit risk section) and suitability scrutiny (complexity/credit risk tiering) covered earlier in this document set.

### Common Implementation Failure Modes

- **Using standalone trade CVA for pricing decisions**: ignoring netting-set-level incremental CVA effects, leading to systematic overpricing (or occasionally underpricing) of new trades relative to their true marginal counterparty risk contribution.
- **Stale or illiquid CDS curve inputs**: for counterparties without actively traded CDS, using outdated proxy spreads or inappropriate sector/rating mappings can materially misstate default probability inputs, particularly problematic during periods of rapid credit deterioration.
- **Recovery rate assumption insensitivity**: treating the standard 40% recovery assumption as universally applicable without adjusting for seniority, jurisdiction, or counterparty-type-specific recovery expectations, understating CVA for genuinely subordinated or unsecured exposure structures.
- **Inconsistent exposure and CVA discounting curves**: using mismatched discounting conventions between the exposure simulation (often requiring OIS/risk-free discounting post-crisis) and the CVA integration step, introducing basis errors into the final CVA figure.
- **Ignoring wrong-way risk in CVA calculation**: computing CVA under an assumption of independence between exposure and counterparty credit quality when a genuine wrong-way risk relationship exists (as flagged in the exposure measurement topic), materially understating true CVA for affected counterparties/trade types.

### Worked Example

Continuing the 5-year receive-fixed swap example from the exposure measurement topic (notional $100 million, corporate counterparty):

- Suppose the simulation produces a discretized expected exposure profile that averages approximately $3 million across the life of the trade (reflecting the hump-shaped EE profile), and the counterparty's CDS-implied cumulative default probability over 5 years is approximately 8%, with a standard 40% recovery assumption (60% LGD).
- A simplified approximation (ignoring the full time-integration granularity): $CVA \approx 0.60 \times \$3\text{ million (average EE)} \times 0.08 \approx \$144{,}000$.
- This CVA figure would be booked as a fair value reduction against the swap's otherwise risk-free valuation, charged by the CVA desk to the originating trading desk as the cost of counterparty risk, and would feed into the netting-set-level regulatory CVA capital charge calculation.
- If the bank subsequently adds a second, offsetting trade with the same counterparty (e.g., a pay-fixed swap reducing net portfolio exposure), the incremental CVA of that second trade would likely be *negative* relative to its standalone CVA, since it reduces the netting set's aggregate expected exposure — illustrating the netting-driven non-additivity discussed above.

**Next Steps**

- Debit Valuation Adjustment (DVA) and bilateral CVA mechanics
- Funding Valuation Adjustment (FVA) and its relationship to CVA/DVA
- Margin Valuation Adjustment (MVA) for initial-margin-driven funding costs
- SA-CVA and BA-CVA regulatory capital calculation mechanics
- CDS curve bootstrapping and default probability term structure construction
- Wrong-way risk modeling within CVA calculation frameworks
- CVA desk hedging strategy and CVA Greeks (CS01, exposure delta)