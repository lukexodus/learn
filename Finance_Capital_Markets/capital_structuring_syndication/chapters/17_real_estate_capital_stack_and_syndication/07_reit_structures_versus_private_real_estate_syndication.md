## REIT Structures versus Private Real Estate Syndication


### Overview

Real Estate Investment Trusts (REITs) and private real estate syndications represent two fundamentally different vehicles for pooling capital to invest in real property. Both allow investors to gain real estate exposure without direct property management responsibility, but they differ substantially in legal structure, regulatory regime, liquidity, tax treatment, minimum investment thresholds, and investor control. Understanding the distinction is foundational to positioning a syndication offering relative to public market alternatives and to advising investors on which vehicle fits their objectives.

### Legal and Structural Definition

**REIT**

A REIT is not a distinct legal entity type but rather a **tax election** made by a corporation, trust, or association that satisfies specific requirements under Internal Revenue Code Section 856-860. A qualifying entity elects REIT status on its federal tax return, which allows it to deduct dividends paid to shareholders, effectively eliminating entity-level corporate income tax on distributed earnings — a significant departure from standard C-corporation double taxation.

**Private Syndication**

A syndication is a **transaction-specific pooling structure**, typically a single-purpose LLC or Limited Partnership formed to acquire one property or a small portfolio, governed by a Limited Partnership Agreement or Operating Agreement (see the GP/LP Structures item in this chapter). It relies on Regulation D or similar securities exemptions rather than a specific tax election, and its existence is tied to the life of the specific asset(s) it holds.

### REIT Qualification Requirements (IRC §856)

To maintain REIT tax status, an entity must satisfy annual tests including:

- **Asset Test**: At least 75% of total assets must be real estate, cash, or government securities
- **Income Test**: At least 75% of gross income must derive from real property rents, mortgage interest, or gains from real property sales; at least 95% must derive from these sources plus dividends, interest, and other passive sources
- **Distribution Requirement**: Must distribute at least 90% of taxable income annually to shareholders as dividends
- **Ownership Test**: Must have at least 100 shareholders after its first year, and no more than 50% of shares may be held by five or fewer individuals during the last half of the tax year (the "5/50 rule")
- **Entity Structure**: Must be taxable as a corporation, managed by a board of directors or trustees, and have transferable shares (or transferable certificates of interest for a trust)

### REIT Categories

- **Publicly Traded (Listed) REITs**: Shares trade on national exchanges (NYSE, Nasdaq); highly liquid, subject to full SEC reporting obligations (10-K, 10-Q, proxy statements) as public companies
- **Public Non-Traded REITs**: SEC-registered and subject to periodic reporting, but shares do not trade on an exchange; liquidity is typically provided through periodic (often quarterly) share repurchase programs at the REIT's discretion, frequently with caps and gates during market stress
- **Private REITs**: Not registered with the SEC (relying on Reg D or similar exemptions), not publicly traded, generally limited to accredited or institutional investors — functionally closer to a syndication in investor access but retaining REIT tax treatment

### Comparative Analysis

| Dimension | Publicly Traded REIT | Private Syndication |
| --- | --- | --- |
| Legal structure | Corporation/trust electing REIT tax status | Single-purpose LLC or LP |
| Regulatory regime | Full SEC registration and reporting (Exchange Act) | Reg D exemption (506(b)/506(c)) — limited disclosure |
| Liquidity | High — traded daily on public exchanges | Low — illiquid, typically locked for 3-10 year hold period |
| Minimum investment | Cost of one share (often under $100) | Typically $25,000-$100,000+ |
| Investor eligibility | Open to any public investor | Generally accredited investors only (506(b)/(c)) |
| Diversification | Portfolio of many properties, often diversified by geography/sector | Typically single-asset or small portfolio concentration |
| Control/voting rights | Shareholder voting on major corporate matters | LP consent rights typically limited to enumerated major decisions |
| Valuation | Continuous market pricing (can trade at premium/discount to NAV) | Valued at cost/appraisal; no market-clearing daily price |
| Tax treatment | Ordinary dividend income (often taxed as ordinary rates, with Section 199A QBI deduction for 20% of REIT dividends) | Pass-through K-1 income with direct depreciation allocation to investors |
| Fee transparency | Disclosed via public filings, generally lower expense ratios | GP fees embedded in PPM: acquisition, asset management, disposition fees plus promote |
| Volatility | Correlated with broader public equity market sentiment | Valuation is not market-priced day-to-day; performance realized primarily at refinance/exit events |
| Management influence over price | None — market sets price | N/A — no secondary market pricing mechanism |

### Tax Treatment Differences

**REIT Shareholder Taxation**

REIT dividends are generally **not** eligible for the lower qualified dividend tax rate available to standard corporate dividends, because the REIT itself does not pay entity-level tax on distributed income. Instead, REIT dividends are typically taxed as ordinary income, though under the Tax Cuts and Jobs Act, individual investors may deduct 20% of qualified REIT dividend income under **Section 199A**, effectively reducing the top marginal rate applicable to that income. REIT dividends may also include a **return of capital** component (reducing the shareholder's cost basis rather than being immediately taxed) when distributions exceed taxable earnings and profits, which is common due to depreciation.

**Syndication Investor Taxation**

Syndication investors receive a **Schedule K-1** annually, reflecting their pro-rata share of the partnership's taxable income, deductions, and credits — critically including **depreciation**, which often shelters a substantial portion of cash distributions from current taxation (frequently allowing distributions to be received tax-deferred in early years, with taxation typically arising as depreciation recapture at sale, or as the investor's basis is reduced). This direct depreciation pass-through is one of syndication's most significant tax advantages relative to REIT ownership, where the REIT entity — not the shareholder — absorbs depreciation before computing distributable taxable income.

$$\text{K-1 Taxable Income} = \text{Pro-Rata NOI} - \text{Pro-Rata Depreciation} - \text{Pro-Rata Interest Expense}$$

[Inference: the magnitude of tax-deferral benefit varies significantly based on asset type, cost segregation study usage, bonus depreciation elections, and the investor's individual tax situation — this is a general structural distinction, not a guaranteed outcome for any specific investor.]

### Liquidity and Valuation Mechanics

**REITs** benefit from continuous price discovery via public markets, meaning an investor can generally exit a position within a trading day (subject to normal settlement), though the traded price may deviate meaningfully from underlying **Net Asset Value (NAV)** based on market sentiment, interest rate expectations, and sector rotation.

**Syndications** have no secondary market by default. Some LPAs include a **right of first refusal (ROFR)** or GP-facilitated transfer process allowing an LP to sell its interest to another investor or back to the GP, but such transfers are illiquid, require GP consent, and rarely have an efficient pricing mechanism. A small but growing secondary market exists for syndication LP interests, typically transacted at a discount to reported NAV due to illiquidity risk. [Unverified: secondary market discount magnitude is highly deal- and market-specific and not standardized; general secondary market activity for private syndication interests remains comparatively thin relative to institutional fund secondaries markets.]

### Investor Suitability Considerations

**REITs tend to suit investors who:**

- Require liquidity or the ability to rebalance a portfolio quickly
- Want diversification across many properties/sectors within a single security
- Prefer standardized, publicly available financial disclosure
- Are investing amounts too small to meet syndication minimums

**Syndications tend to suit investors who:**

- Can tolerate multi-year illiquidity in exchange for potentially higher targeted returns and direct depreciation tax benefits
- Meet accredited investor thresholds and syndication minimum investment requirements
- Want concentrated exposure to a specific asset, business plan, or sponsor track record
- Value the ability to select individual deals and sponsors rather than accepting a diversified, professionally-selected portfolio

### Structural Comparison Diagram

```mermaid
flowchart TB
    subgraph REIT["Publicly Traded REIT"]
        A1[Public Shareholders] -->|Buy/Sell Shares on Exchange| A2[REIT Corporation]
        A2 -->|90%+ of Taxable Income| A1
        A2 --> A3[Diversified Property Portfolio]
    end
    subgraph SYN["Private Syndication"]
        B1[Accredited LP Investors] -->|Capital Contribution, Illiquid| B2[Single-Purpose LLC/LP]
        B3[GP/Sponsor] -->|Manages, Co-Invests| B2
        B2 -->|Waterfall Distribution + K-1| B1
        B2 --> B4[Single Asset or Small Portfolio]
    end
```

### Hybrid Consideration: Private REITs and Non-Traded REITs

Some sponsors structure offerings as **private REITs**, combining REIT tax treatment (entity-level tax elimination on distributed income) with Reg D-style investor access restrictions, effectively narrowing the gap between the two vehicle types. This is common in institutional non-traded REIT platforms that pool capital across multiple properties while still restricting distribution to accredited investors and imposing periodic (rather than daily) liquidity via share repurchase programs. Such structures inherit REIT qualification complexity (the tests described above) in exchange for entity-level tax efficiency and a degree of built-in diversification not present in single-asset syndications.

### Key Points

- REIT status is a tax election under IRC §856-860 requiring ongoing compliance with asset, income, distribution, and ownership tests; syndication status derives from securities exemption compliance (typically Reg D), not a tax election
- Publicly traded REITs offer daily liquidity and market-based pricing; syndications are illiquid with valuation typically fixed at cost/appraisal until a liquidity event
- REIT dividends are generally taxed as ordinary income (with a partial Section 199A deduction); syndication K-1 income benefits from direct depreciation pass-through, often deferring taxation on distributions
- Syndications typically require significantly higher minimum investments and accredited investor status; REITs are broadly accessible to any public investor
- Private REITs and non-traded REITs occupy a middle ground, combining REIT tax treatment with syndication-like investor access restrictions

### Related Topics

- REIT Qualification Tests: Asset, Income, and Distribution Requirements in Detail
- Section 199A Qualified Business Income Deduction for REIT Dividends
- Depreciation Recapture and Basis Adjustment in K-1 Reporting
- Non-Traded REIT Share Repurchase Program Mechanics and Liquidity Gates
- Secondary Market Transfer Mechanisms for Syndication LP Interests
- UPREIT Structures and Section 721 Exchanges as a Syndication-to-REIT Bridge