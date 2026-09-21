## Measuring Reshoring Through Job and Investment Data

### Overview

Measuring reshoring activity requires triangulating across multiple imperfect data sources, since no single government dataset directly labels a job or facility as "reshored." Analysts combine private-sector tracking initiatives, official trade and investment statistics, employment data, and corporate disclosures to approximate the scale and direction of manufacturing relocation back to a home country (or to nearshore/friend-shore locations).

### Core Data Sources

#### Reshoring Initiative Data (Private Sector)

- The **Reshoring Initiative** (a US-based nonprofit) is the most widely cited source for US reshoring metrics.
- Methodology: aggregates company announcements (press releases, news reports, trade publications) of reshored or FDI-driven job creation, then cross-validates against BLS and Commerce data.
- Produces an annual "jobs announced" figure, distinguishing:
  - **Reshoring**: production moved from a foreign location back to the US by a domestic firm
  - **FDI (Foreign Direct Investment) job announcements**: foreign firms opening/expanding US facilities
- [Unverified] Announcement-based counts can overstate actual realized employment, since not all announced projects reach full hiring or completion on schedule.

#### Trade Data as a Proxy

- **Import substitution analysis**: a decline in imports from a specific country/region alongside a rise in domestic production or imports from an alternate ally is used as indirect evidence of nearshoring/friend-shoring.
- Key datasets:
  - US Census Bureau **USA Trade Online** (bilateral trade by HS code)
  - **UN Comtrade** for global bilateral trade flows
  - Formula often used to compute import concentration shifts:

$$HHI=\sum_{i=1}^{n}s_i^2$$

where $s_i$ is the import share from source country $i$; a falling Herfindahl-Hirschman Index (HHI) concentrated in one country (e.g., China) alongside a rising HHI in nearshore partners (e.g., Mexico, Vietnam) suggests diversification consistent with friend-shoring.

#### Foreign Direct Investment (FDI) Statistics

- **BEA (Bureau of Economic Analysis)** tracks inbound and outbound FDI flows and positions by country and industry.
- **fDi Markets** (Financial Times database) tracks greenfield FDI project announcements globally, useful for cross-country nearshoring comparisons (e.g., Mexico's manufacturing FDI inflows post-2018).
- Key metric: **greenfield investment value** and **capital expenditure announced**, segmented by sector (semiconductors, EVs, pharmaceuticals are common reshoring-heavy sectors).

#### Employment and Labor Statistics

- **Bureau of Labor Statistics (BLS)**:
  - Manufacturing employment (CES series) as a baseline, though it captures net employment change, not the *cause* (automation, demand shifts, and reshoring are conflated).
  - **Quarterly Census of Employment and Wages (QCEW)** allows county-level manufacturing employment tracking, useful for correlating with specific reshoring project locations.
- **Job Openings and Labor Turnover Survey (JOLTS)**: manufacturing sector openings/hires as a leading indicator.

#### Corporate Disclosures and Supply Chain Filings

- 10-K/annual report language analysis: searching for terms like "reshoring," "nearshoring," "supply chain diversification," "China+1" using NLP/text-mining on SEC EDGAR filings.
- Earnings call transcript analysis (e.g., via Bloomberg, FactSet) to track sentiment and frequency of supply-chain-relocation language over time as a leading qualitative indicator.

### Composite Index Construction

A practical composite reshoring index blends multiple signals:

$$RI_t=w_1\cdot\Delta E_t+w_2\cdot\Delta FDI_t+w_3\cdot\Delta M_t+w_4\cdot A_t$$

Where:

- $\Delta E_t$ = normalized change in domestic manufacturing employment
- $\Delta FDI_t$ = normalized change in inbound manufacturing FDI
- $\Delta M_t$ = normalized change (decline) in imports from the offshoring-origin country
- $A_t$ = normalized count of reshoring-related corporate announcements
- $w_1,\dots,w_4$ = analyst-assigned weights

[Inference] This weighting approach is a common analytical construction in trade-policy think tank literature but is not a standardized government methodology; weights vary significantly by researcher and introduce subjectivity into cross-study comparisons.

### Methodological Challenges

**Attribution problem**: Rising domestic manufacturing employment could stem from automation-driven productivity gains, general economic growth, or currency effects — not exclusively reshoring.

**Announcement vs. realization gap**: Companies announce reshoring for public relations or policy-signaling purposes; actual capital deployment and hiring may lag by 2-5 years or be scaled down/cancelled. [Unverified] Cancellation rates for announced projects.

**Nearshoring vs. reshoring conflation**: Trade diversion to Mexico or Vietnam is often mislabeled as "reshoring" in media coverage when it is technically nearshoring or friend-shoring — precise terminology matters for accurate measurement.

**Lag in official statistics**: BEA and BLS data typically release with a 1-2 quarter lag, making real-time tracking dependent on the faster (but less rigorous) private announcement trackers.

### Example: Semiconductor Sector Case Illustration

```mermaid
flowchart LR
    A[CHIPS Act Announcement] --> B[Corporate Capex Announcement]
    B --> C[BEA FDI Inflow Recorded]
    B --> D[Reshoring Initiative Tracks Job Count]
    C --> E[Construction Phase - Employment Lag]
    D --> E
    E --> F[BLS QCEW Employment Realized]
    F --> G[Composite Reshoring Index Update]
```

In this flow, an announcement (e.g., a fab investment) generates parallel signals in FDI statistics and private trackers, but the BLS employment data—the most rigorous confirmation—only reflects the change after a multi-year construction lag.

### Key Limitations Summary

- **Reshoring Initiative data**: timely but announcement-based, private methodology, US-centric
- **BEA/Census trade & FDI data**: rigorous and official, but lagged and doesn't isolate "reshoring" as a distinct category
- **BLS employment data**: granular and reliable, but causally ambiguous
- **Corporate filings/NLP sentiment**: useful leading indicator, but qualitative and susceptible to PR framing

### Related Topics

- China+1 diversification strategies and measurement
- Friend-shoring policy frameworks (e.g., US-Mexico-Canada Agreement trade flow shifts)
- CHIPS Act and Inflation Reduction Act investment tracking methodologies
- Automation's confounding effect on manufacturing employment statistics
- Supply chain resilience indices (e.g., Kearney Reshoring Index methodology)
- Using satellite/night-light data as an alternative proxy for industrial activity shifts