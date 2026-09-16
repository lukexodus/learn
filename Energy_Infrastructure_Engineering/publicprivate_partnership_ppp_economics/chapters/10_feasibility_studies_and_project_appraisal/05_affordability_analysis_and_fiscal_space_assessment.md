## Affordability Analysis and Fiscal Space Assessment


### Definition and Purpose

Affordability Analysis and Fiscal Space Assessment is the component of PPP feasibility studies that determines whether the public sector can sustainably meet the financial obligations a project will generate over its full contract life, without compromising other fiscal priorities or breaching fiscal responsibility limits. It answers a question distinct from, but complementary to, Value for Money (VfM) analysis: VfM asks "is a PPP the best procurement route for this project," while affordability asks "regardless of procurement route, can the government actually pay for this."

Affordability failure is one of the most common causes of PPP project cancellation, renegotiation, or fiscal distress after signature, because governments frequently underestimate the long-term budgetary claim created by user-fee shortfalls, availability payments, guarantees, and contingent liabilities embedded in PPP contracts.

### Position Within the PPP Project Cycle

Affordability assessment typically occurs at three checkpoints:

1. **Pre-feasibility screening** — a coarse test of whether the project concept is fiscally plausible before detailed technical and financial work is commissioned.
2. **Feasibility study stage** — detailed affordability and fiscal space modeling run alongside technical design, demand forecasting, and financial structuring.
3. **Pre-financial-close validation** — a final affordability check against the negotiated contract terms, since risk allocation and payment mechanisms often shift materially during negotiation.

```mermaid
flowchart LR
    A[Project Concept] --> B[Preliminary Affordability Screening]
    B --> C[Detailed Feasibility Study]
    C --> D[Fiscal Space Assessment]
    D --> E[Payment Mechanism Design]
    E --> F[Contingent Liability Quantification]
    F --> G[Medium-Term Fiscal Framework Integration]
    G --> H[Pre-Financial-Close Affordability Validation]
    H --> I[Financial Close]
    I --> J[Ongoing Fiscal Risk Monitoring]
```

### Core Components of Affordability Analysis

#### 1. Identifying the Government's Financial Exposure

PPP contracts create several distinct categories of government financial obligation, which must each be separately identified and quantified:

- **Direct payments** — availability payments, shadow tolls, or subsidy payments made regardless of, or based on, service performance rather than direct user charges.
- **Direct guarantees** — minimum revenue guarantees (MRGs), exchange rate guarantees, or debt guarantees extended to the private partner or its lenders.
- **Indirect/contingent liabilities** — termination payments, compensation for events of default by the grantor, force majeure compensation, or change-in-law compensation.
- **Implicit liabilities** — obligations governments may feel politically compelled to honor even absent a legal requirement (e.g., bailing out a failing PPP providing an essential public service).

**Key Points:**

- Direct payments are relatively straightforward to model and budget for.
- Contingent and implicit liabilities are harder to quantify but are frequently the larger long-term fiscal risk, since they are "off-budget" until triggered and can arrive as large, lumpy cash calls precisely when government finances are already under stress (e.g., during a macroeconomic downturn that also triggers a minimum revenue guarantee payout).

#### 2. Affordability Analysis Proper

Affordability analysis tests whether projected government payment obligations under the PPP are consistent with the government's medium-term budget and fiscal rules. It typically involves:

**a. Budget Line Affordability**

Comparing the projected annual payment stream (availability payments, subsidies) against the relevant sectoral budget ceiling or Medium-Term Expenditure Framework (MTEF) allocation, expressed as a percentage of that sector's budget or of total government revenue.

**b. Debt and Fiscal Rule Compliance**

Testing whether committing to the PPP's payment stream, when added to existing debt service and other commitments, keeps the government within statutory or policy-based fiscal rules such as:

$$\text{Debt-to-GDP Ratio} = \frac{\text{Total Public Debt (incl. PPP commitments)}}{\text{GDP}}$$



$$\text{Fiscal Deficit Ratio} = \frac{\text{Total Expenditure} - \text{Total Revenue}}{\text{GDP}}$$

Many countries and multilateral frameworks (e.g., IMF debt sustainability guidance) recommend that the *net present value of committed PPP payment obligations* be included in public debt calculations for fiscal rule purposes, even though PPP debt is often held off the sovereign balance sheet in accounting terms — this is a key point of divergence between fiscal accounting treatment and fiscal risk reality.

**c. PPP Portfolio Ceiling Analysis**

Many countries impose an explicit ceiling on the aggregate stock of PPP payment commitments, commonly expressed as a percentage of total revenue or GDP (a frequently cited international benchmark range is approximately 5–10% of the annual government budget for total outstanding PPP payment obligations, though [Unverified] the specific threshold applied by any given country should be confirmed against that country's current PPP fiscal responsibility framework, as thresholds and the frameworks themselves vary and are periodically revised).

**Example — Simplified Budget Line Affordability Test:**

| Year | Projected Availability Payment (local currency, millions) | Sector Budget Ceiling | Ratio |
| --- | --- | --- | --- |
| 1 | 120 | 2,400 | 5.0% |
| 5 | 145 | 2,650 | 5.5% |
| 10 | 165 | 3,100 | 5.3% |
| 15 | 180 | 3,500 | 5.1% |

If the sector or PPP-portfolio ceiling is set at, for example, 8%, this project would pass the affordability test in isolation — but the assessment must also account for the cumulative effect of *all* existing and pipeline PPP commitments in the same sector or across government, not just this single project viewed in isolation.

#### 3. Fiscal Space Assessment

Fiscal space is the budgetary room available to a government to commit resources to a purpose (such as a new PPP) without jeopardizing fiscal sustainability or crowding out other essential spending. Fiscal space assessment for PPPs typically examines:

- **Existing commitments** — debt service, recurrent expenditure, and prior PPP/concession obligations already locked in.
- **Revenue trajectory** — projected government revenue growth under baseline and stressed macroeconomic scenarios.
- **Fiscal buffers** — reserves, stabilization funds, or contingency budget lines available to absorb shocks.
- **Macro-fiscal risk factors** — exchange rate volatility (particularly relevant where PPP payments or debt service are foreign-currency denominated), commodity price dependence, and contingent liability exposure from other sources (state-owned enterprises, natural disaster risk, pension obligations).

**Fiscal space** can be conceptually expressed as:

$$\text{Fiscal Space} = \text{Fiscal Sustainability Ceiling} - \text{Existing Committed Obligations}$$

where the "fiscal sustainability ceiling" reflects the maximum sustainable level of debt and spending consistent with the country's macro-fiscal framework, rather than a single universally-defined figure.

#### 4. Whole-of-Government / Portfolio-Level View

A single PPP project may appear affordable in isolation while the aggregate PPP portfolio pushes the government beyond sustainable fiscal limits. Robust practice requires:

- **A centralized PPP fiscal commitment register**, tracking direct and contingent liabilities across all active and pipeline PPPs government-wide.
- **Stress-testing the portfolio**, not just the individual project, against combined shock scenarios (e.g., simultaneous currency depreciation and demand shortfall across multiple projects).
- **Institutional gatekeeping**, typically via a Ministry of Finance PPP unit with authority to reject or require restructuring of a fiscally unaffordable project, independent of the sector ministry's enthusiasm for the project.

```mermaid
flowchart TD
    A[Individual Project Affordability Test (svg_diagram)] --> B{Passes in Isolation?}
    B -->|Yes| C[Add to PPP Fiscal Commitment Register]
    C --> D[Aggregate Portfolio Exposure]
    D --> E{Portfolio Within Fiscal Ceiling?}
    E -->|Yes| F[Proceed to Structuring]
    E -->|No| G[Reject, Defer, or Restructure Project]
    B -->|No| G
```

### Quantifying Contingent Liabilities

Because contingent liabilities are probabilistic rather than certain, several techniques are used to bring them into affordability analysis:

- **Expected value approach** — estimating the probability-weighted expected cost of a contingent liability crystallizing (e.g., probability of triggering a minimum revenue guarantee × expected payout if triggered).
- **Value-at-Risk (VaR) / stochastic modeling** — Monte Carlo simulation of macroeconomic and demand variables to generate a distribution of possible government payment outcomes, from which a percentile (e.g., 95th percentile "worst reasonable case") can be used for fiscal risk budgeting.
- **Contingent liability provisioning** — some fiscal frameworks require governments to set aside a budgeted contingency reserve (sometimes benchmarked as a percentage of the guarantee's face value) against the expected cost of guarantees extended.

[Inference] The choice between expected-value and percentile-based (VaR-style) provisioning approaches materially affects how conservative the resulting affordability assessment appears, and the appropriate approach depends on the government's risk tolerance and the specific fiscal risk management framework in use — this is a judgment call rather than a settled universal standard.

### Payment Mechanism Design and Its Affordability Implications

The choice of payment mechanism directly shapes the affordability profile:

| Mechanism | Affordability Characteristic |
| --- | --- |
| Pure user-pays (toll/tariff) | No direct budget line item, but government may still face demand-risk-related contingent guarantee exposure |
| Availability payment | Predictable, budgetable fixed/formula-based obligation; full exposure to budget regardless of usage |
| Shadow toll | Budget exposure varies with usage, introducing demand-forecast risk into the fiscal projection |
| Viability Gap Funding (VGF) | One-time or phased capital subsidy; affordability test focuses on upfront/medium-term capital budget rather than long-tenor recurrent exposure |
| Hybrid annuity | Combines partial upfront government payment with deferred annuity payments, spreading fiscal exposure across construction and operational phases |

**Key Points:**

- Availability payments shift demand risk to government and away from the private party, which improves financeability (lower cost of capital) but increases the certainty and typically the scale of the long-term budget commitment.
- Pure user-pays structures minimize direct budget exposure but often require government to still absorb residual risk through guarantees to make the project bankable, which can reintroduce fiscal exposure through the back door of contingent liabilities.

### Affordability Gap and Viability Gap Funding

Where a project is technically and socially justified but the user-pays revenue stream alone cannot support commercial financing, an **affordability/viability gap** exists:

$$\text{Viability Gap} = \text{Total Project Cost (NPV)} - \text{NPV of Sustainable User Revenue}$$

Governments address this gap through Viability Gap Funding (VGF) — typically capped (in many VGF frameworks, around 20–40% of total project cost, though [Unverified] specific caps are jurisdiction- and program-specific and should be verified against the applicable VGF scheme's current rules) — provided competitively to minimize the subsidy while still making the project bankable.

### Debt Sustainability Analysis (DSA) Linkage

Affordability assessment for PPPs is increasingly required to feed into, or be consistent with, the government's broader Debt Sustainability Analysis, particularly where:

- PPP payment obligations are large relative to GDP or total revenue.
- The government has recent or ongoing engagement with the IMF or World Bank debt sustainability frameworks.
- PPP debt, even if off the sovereign balance sheet under national accounting standards, is treated by rating agencies or the IMF/World Bank Debt Sustainability Framework as a quasi-fiscal liability that should be captured in public and publicly guaranteed (PPG) debt figures.

[Inference] Rating agencies and multilateral lenders increasingly scrutinize the "hidden debt" dimension of PPP portfolios, meaning a project structured to appear affordable through off-balance-sheet accounting treatment may still attract sovereign credit rating or debt sustainability concerns; the degree of scrutiny and specific accounting treatment applied varies by institution and over time.

### Institutional Framework for Affordability Oversight

Effective affordability and fiscal space assessment typically requires:

- **A dedicated PPP Unit within the Ministry of Finance**, with technical capacity to review and challenge affordability assumptions submitted by sector ministries or contracting authorities.
- **Mandatory affordability certification** as a gate before a project can proceed to market/procurement (common in many national PPP frameworks).
- **Legislative or Cabinet-level approval thresholds** for PPPs above a certain size or fiscal commitment level.
- **Periodic re-certification** of affordability at key decision points (approval, tender award, financial close) since costs, demand forecasts, and macro conditions evolve over the multi-year preparation period.

### Worked Example: Availability-Payment Hospital PPP

**Example:**

A government is considering a 25-year availability-payment PPP for a new regional hospital, with projected annual availability payments of $18 million once operational, rising with an inflation-indexation clause.

- **Budget line test:** The health ministry's current capital and facility-operations budget for the region is $450 million/year. At $18 million, the payment represents 4% of the relevant budget line — within the ministry's internal affordability guideline of 6%.
- **Fiscal space test:** The Ministry of Finance's medium-term fiscal framework projects revenue growth of 3–5% annually; existing PPP commitments across all sectors currently total 6.5% of total revenue against a national ceiling of 10%. Adding this project's projected 0.4% of total revenue keeps the portfolio at 6.9%, within the ceiling.
- **Contingent liability quantification:** A termination-for-convenience clause exposes government to a potential lump-sum payment (calculated as outstanding senior debt plus a negotiated equity return) estimated via Monte Carlo simulation at an expected value of $6 million (low probability, high impact), which is added to the government's contingent liability register and provisioned for in the annual budget's contingency reserve line at a fraction of that amount.
- **Payment mechanism sensitivity:** Because the payment is availability-based rather than usage-based, the fiscal exposure is treated as near-certain (subject only to performance deductions), making it a higher-priority item for medium-term budget locking than a comparable shadow-toll structure would be.
- **Outcome:** The project passes both budget-line and portfolio-level affordability tests and proceeds to procurement, with the contingent liability formally logged in the national PPP fiscal risk register for ongoing monitoring.

### Common Pitfalls in Practice

- Assessing a single project's affordability in isolation without reference to the aggregate PPP portfolio's fiscal commitments.
- Excluding contingent liabilities (guarantees, termination payments) from affordability calculations because they are not immediate cash outflows.
- Using overly optimistic demand or macroeconomic growth assumptions in the underlying revenue and fiscal projections, which understate future payment obligations (particularly relevant for shadow tolls and minimum revenue guarantees).
- Treating off-balance-sheet accounting classification as equivalent to genuine fiscal affordability, rather than as a presentation choice that does not eliminate the underlying economic obligation.
- Failing to re-test affordability after contract negotiation, when risk allocation and payment terms frequently shift from the original feasibility study assumptions.
- Weak institutional capacity or independence in the reviewing Ministry of Finance PPP unit, allowing politically favored projects to bypass rigorous affordability scrutiny.

### Related Topics

- Value for Money (VfM) Analysis and the Public Sector Comparator
- Contingent Liability Management and Fiscal Risk Registers
- Payment Mechanism Design in PPP Contracts
- Debt Sustainability Analysis and Public and Publicly Guaranteed (PPG) Debt
- Viability Gap Funding Schemes and Design
- Risk Allocation Matrices in PPP Contracts
- Medium-Term Expenditure Frameworks and Budget Integration
- Environmental and Social Impact Assessment