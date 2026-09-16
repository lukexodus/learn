## Bank Relationship and Account Structure Management

### Introduction and Strategic Context

Bank relationship management is the discipline of selecting, structuring, and maintaining an organization's relationships with its banking partners, while account structure management concerns the design of the underlying account architecture through which cash, payments, and collections flow. The two are treated together because account structure decisions are rarely made independently of banking relationships—the number and configuration of accounts a treasury maintains is directly shaped by which banks provide which services, in which jurisdictions, and under what commercial terms.

### The Banking Group: Composition and Rationale

**Relationship Bank vs. Transactional Bank**

Most corporate treasury organizations distinguish between two tiers of banking relationship:

- **Relationship banks**: Banks that provide credit facilities (revolving credit, term loans) and, typically in connection with that credit provision, a broader suite of services—cash management, FX, capital markets underwriting, advisory. The credit relationship is often the anchor that justifies allocating other ancillary business (a dynamic sometimes referred to informally as "share of wallet" expectations).
- **Transactional/product banks**: Banks engaged for a specific product or service (e.g., a specialist FX bank, a custody bank, a local cash management bank in a jurisdiction where the primary relationship banks lack strong local presence) without necessarily holding a credit relationship.

**Rationale for Multiple Banking Relationships**

[Inference] Maintaining a diversified banking group rather than concentrating with a single bank is generally motivated by several considerations, though the appropriate degree of diversification is firm-specific and involves a genuine trade-off against the benefits of concentration (described below):

- **Counterparty risk diversification**: Reducing reliance on any single bank's solvency and operational continuity, a consideration reinforced by historical bank failure episodes.
- **Credit capacity**: Large credit facilities often exceed what a single bank is willing or able to underwrite alone, necessitating a syndicate of relationship banks.
- **Geographic/product coverage**: No single global bank has uniformly strong capability in every jurisdiction and product category the organization needs.
- **Competitive pricing tension**: Maintaining multiple capable banks preserves negotiating leverage on pricing and terms across cash management, FX, and lending services.

**Rationale for Concentration**

Conversely, concentrating business with fewer banks offers benefits that must be weighed against diversification:

- **Operational simplicity**: Fewer bank connections, account structures, and reconciliation processes to maintain.
- **Relationship depth and service quality**: Banks may prioritize service quality and pricing flexibility for clients representing more significant relationship value.
- **Netting and pooling efficiency**: Cash pooling and netting structures are generally more efficient when concentrated within a single bank's network, since cross-bank pooling introduces additional operational complexity and cost.

### Bank Relationship Management Process

**Periodic Relationship Review**

Most treasury organizations conduct a formal, typically annual, bank relationship review process, assessing each relationship bank against criteria that commonly include:

1. **Credit allocation vs. ancillary business (wallet share analysis)**: Comparing the credit commitment a bank provides against the total fee/revenue business (cash management fees, FX spread, capital markets mandates) the organization directs to that bank, to assess whether the relationship is balanced from the bank's perspective—an imbalanced relationship (credit provided without commensurate ancillary business) can affect the bank's willingness to maintain or expand credit commitment at renewal.
2. **Service quality metrics**: Operational responsiveness, error rates, technology platform reliability.
3. **Credit rating and financial strength of the counterparty bank**: Particularly relevant for deposit concentration and derivative counterparty exposure limits.
4. **Pricing competitiveness**: Benchmarking fees and spreads against market and against other relationship banks.

**Request for Proposal (RFP) Processes**

Periodically (commonly every 3–5 years for major services, though this varies considerably by organization and by how satisfied treasury is with incumbent service), treasury organizations run competitive RFP processes for major banking services (primary cash management bank, credit facility syndication lead arranger, custody services) to test market pricing and service capability, even when the intent is ultimately to retain an incumbent bank—the RFP process itself provides negotiating leverage and validates that pricing remains competitive.

```mermaid
flowchart TD
    A[Define service requirements and evaluation criteria] --> B[Identify candidate banks]
    B --> C[Issue RFP / RFI]
    C --> D[Evaluate proposals: pricing, technology, service, credit strength]
    D --> E[Shortlist and conduct due diligence / reference checks]
    E --> F[Select bank(s) and negotiate final terms]
    F --> G[Implementation: account opening, technology integration, migration]
    G --> H[Post-implementation service review]
    H --> A
```

### Account Structure Design

**Core Design Principles**

Account structure design balances several, often competing, objectives:

- **Visibility and control**: Fewer, more centralized accounts generally provide better cash visibility and control, simplifying forecasting and reducing the risk of idle, unmonitored balances.
- **Operational necessity**: Local regulatory requirements, tax considerations, and operational needs (e.g., a local payroll account required by local banking practice) often necessitate maintaining accounts that a pure centralization objective would otherwise eliminate.
- **Segregation requirements**: Certain account types must be legally or contractually segregated (e.g., client money/trust accounts in regulated industries, escrow accounts, restricted-use accounts tied to specific debt covenants).

**Common Account Types in a Corporate Structure**

| Account Type | Purpose | Typical Characteristics |
| --- | --- | --- |
| Master/concentration account | Top-level account receiving swept balances from subsidiary accounts | Usually held at the primary relationship bank |
| Operating/collection accounts | Local entity-level accounts for receiving customer payments | Often zero-balanced (swept daily to concentration account) |
| Disbursement accounts | Local entity-level accounts for making payments (payroll, AP) | May be funded via sweep from concentration account or pre-funded |
| Zero-balance accounts (ZBAs) | Sub-accounts automatically swept to/from a master account to maintain a target (often zero) balance | Core mechanism enabling physical cash concentration |
| Escrow accounts | Segregated funds held pending satisfaction of contractual conditions | Typically restricted, often requiring dual counterparty authorization |
| Trust/client money accounts | Segregated client or fiduciary funds, legally distinct from company's own funds | Subject to specific regulatory segregation requirements in regulated industries |

**Cash Concentration Mechanisms**

- **Physical (zero-balance) sweeping**: Actual funds are physically transferred between accounts (typically overnight) to concentrate balances at a master account, with sub-accounts maintained at a target balance (often zero).
- **Notional pooling**: No physical movement of funds occurs; instead, the bank calculates interest on the combined (net) balance across a group of accounts as if they were pooled, while each account retains its actual legal balance. Notional pooling avoids the intercompany loan/deposit relationships that physical sweeping can create (with associated transfer pricing and thin capitalization considerations) but is not available in all jurisdictions and is subject to varying regulatory treatment.
- **Multi-currency notional pooling**: An extension of notional pooling across accounts in different currencies, with the bank calculating an effective combined position after applying FX conversion, offering interest optimization benefits without requiring FX conversion of underlying balances.

(svg_diagram) Zero-Balance Account Sweeping Structure

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 760 400">
<text x="380" y="30" text-anchor="middle" font-size="18" font-weight="bold" fill="#1a1a1a">Zero-Balance Account Sweep Structure (svg_diagram)</text>
<rect x="270" y="60" width="220" height="70" rx="8" fill="#2b6cb0" />
<text x="380" y="90" text-anchor="middle" font-size="13" font-weight="bold" fill="#ffffff">Master / Concentration</text>
<text x="380" y="110" text-anchor="middle" font-size="11" fill="#e2e8f0">Account (target: interest-optimized balance)</text>
<rect x="60" y="200" width="160" height="70" rx="6" fill="#eaf2fb" stroke="#2b6cb0" stroke-width="1.5" />
<text x="140" y="228" text-anchor="middle" font-size="11" fill="#1a365d">Collection ZBA</text>
<text x="140" y="246" text-anchor="middle" font-size="10" fill="#2d3748">Target balance: \$0</text>
<text x="140" y="260" text-anchor="middle" font-size="9" fill="#4a5568">Excess swept up nightly</text>
<rect x="300" y="200" width="160" height="70" rx="6" fill="#eaf2fb" stroke="#2b6cb0" stroke-width="1.5" />
<text x="380" y="228" text-anchor="middle" font-size="11" fill="#1a365d">Disbursement ZBA</text>
<text x="380" y="246" text-anchor="middle" font-size="10" fill="#2d3748">Target balance: \$0</text>
<text x="380" y="260" text-anchor="middle" font-size="9" fill="#4a5568">Funded from master as needed</text>
<rect x="540" y="200" width="160" height="70" rx="6" fill="#eaf2fb" stroke="#2b6cb0" stroke-width="1.5" />
<text x="620" y="228" text-anchor="middle" font-size="11" fill="#1a365d">Payroll ZBA</text>
<text x="620" y="246" text-anchor="middle" font-size="10" fill="#2d3748">Target balance: \$0</text>
<text x="620" y="260" text-anchor="middle" font-size="9" fill="#4a5568">Funded on payroll dates</text>
<line x1="140" y1="200" x2="330" y2="130" stroke="#2f855a" stroke-width="2" />
<text x="220" y="170" font-size="10" fill="#2f855a">sweep up ↑</text>
<line x1="380" y1="200" x2="380" y2="130" stroke="#c53030" stroke-width="2" />
<text x="390" y="170" font-size="10" fill="#c53030">fund down ↓</text>
<line x1="620" y1="200" x2="430" y2="130" stroke="#c53030" stroke-width="2" />
<text x="500" y="170" font-size="10" fill="#c53030">fund down ↓</text>

<text x="380" y="330" text-anchor="middle" font-size="11" fill="`#718096`">Sub-accounts settle to a zero target balance each cycle via automated sweep</text>

<text x="380" y="350" text-anchor="middle" font-size="11" fill="`#718096`">Concentration account holds the group's consolidated, interest-bearing position</text>

</svg>

### Cross-Border Considerations

**Regulatory and Capital Control Constraints**

[Inference] Account structure and cash concentration design is materially constrained in many jurisdictions by capital controls, currency convertibility restrictions, and local regulatory requirements governing intercompany cash movement—physical cross-border sweeping that is straightforward between, for example, two Eurozone entities may be significantly more complex, restricted, or entirely infeasible between entities in jurisdictions with capital controls (historically and to varying degrees over time, examples cited in treasury practice include China, India, and various other emerging markets, though specific rules change and should be verified against current local regulation rather than assumed static).

**Intercompany Loan and Transfer Pricing Considerations**

Physical cash sweeping across legal entities generally creates intercompany loan or deposit relationships (the subsidiary whose cash was swept up has, in effect, lent that cash to the entity holding the concentration account), which has both:

- **Transfer pricing implications**: Tax authorities in many jurisdictions require intercompany loans (including those arising from cash pooling) to bear an arm's-length interest rate, requiring treasury to establish and document appropriate intercompany interest rates, often with transfer pricing specialist input.
- **Thin capitalization considerations**: Some jurisdictions apply thin capitalization or interest deductibility limitation rules that can affect the tax treatment of intercompany loan balances arising from pooling structures, depending on the debt-to-equity or interest-to-EBITDA ratios involved.

[Unverified] Specific transfer pricing and thin capitalization rules vary significantly by jurisdiction and are subject to ongoing legislative change (including BEPS-related reforms adopted at different paces across jurisdictions); this is a specialist tax area where treasury typically relies on dedicated tax/transfer pricing advisory input rather than in-house treasury expertise alone, and any general statement here should not be treated as current guidance for a specific jurisdiction.

### Bank Account Administration and Governance

**Bank Account Management (BAM) as a Discipline**

Larger treasury organizations often formalize bank account administration as a distinct sub-function (sometimes supported by dedicated bank account management modules within a TMS), addressing:

- **Account opening/closing governance**: Formal approval workflows for opening new bank accounts (preventing unauthorized or unnecessary account proliferation, a common finding in treasury process audits) and timely closure of dormant accounts.
- **Signatory management**: Maintaining accurate, current records of authorized signatories across the account portfolio, with periodic review to remove departed employees and reflect authority changes—a control area frequently cited in internal audit findings when not actively maintained.
- **Account inventory and documentation**: A centralized, current inventory of all bank accounts (a surprisingly common control gap in decentralized or post-M&A organizations, where legacy accounts from acquired entities may persist without central treasury's full knowledge, representing both an operational risk and an inefficiency).

**Key Points**

- Bank account proliferation—the gradual, often undocumented accumulation of bank accounts over time (through M&A, legacy local practice, or ad hoc local needs)—is a commonly cited treasury organizational challenge; periodic account rationalization projects are a standard treasury initiative to reduce this administrative and control burden.
- KYC (Know Your Customer) and AML (Anti-Money Laundering) documentation requirements imposed by banks on corporate clients have generally increased over time, making account opening and periodic re-documentation a more resource-intensive administrative process than in prior decades, a trend widely observed across the industry following intensified global AML/KYC regulatory focus.

### Fee Analysis and Bank Relationship Economics

**Account Analysis Statements**

Banks typically provide corporate clients with an **account analysis statement**, itemizing transaction volumes and associated fees (per-item fees for wires, ACH transactions, checks processed, etc.) alongside an **earnings credit rate (ECR)**—an offset against fees based on the account's average balance, functioning economically similarly to interest but structured as a fee offset rather than interest income (a distinction that can carry tax and accounting treatment differences).

**Key Points**

- Treasury organizations periodically audit account analysis statements against contracted pricing to identify billing errors, which industry practitioners note are not infrequent given the complexity and volume of line-item fee categories involved.
- The choice between maintaining compensating balances (to generate earnings credits offsetting fees) versus paying fees directly while investing surplus cash elsewhere is a quantitative decision depending on the relative earnings credit rate offered versus available short-term investment yields, and shifts in relative attractiveness as interest rate environments change.

### Related Topics

- Cash pooling structures: physical vs. notional pooling mechanics and jurisdictional availability
- Transfer pricing considerations for intercompany loans arising from cash concentration
- KYC/AML documentation requirements and their operational impact on account administration
- Credit facility syndication and the relationship between credit allocation and ancillary banking business
- Treasury management system bank connectivity: SWIFT, host-to-host, and API-based models
- Post-merger bank account rationalization and treasury integration planning
- Multi-currency notional pooling structures and FX optimization