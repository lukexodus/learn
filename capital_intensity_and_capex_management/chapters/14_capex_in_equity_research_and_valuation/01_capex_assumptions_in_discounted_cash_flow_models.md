## Capex Assumptions in Discounted Cash Flow Models

### Overview

Capital expenditure (capex) assumptions are among the most consequential and most frequently mis-modeled inputs in a discounted cash flow (DCF) valuation. Capex directly reduces free cash flow to the firm (FCFF) or free cash flow to equity (FCFE), and it also drives the depreciation schedule that flows through the income statement and back into the tax shield calculation. Because capex projections compound over an explicit forecast period and then anchor the terminal value through the reinvestment rate, small errors in capex methodology can produce large valuation swings.

### Role of Capex in Free Cash Flow Construction

**FCFF formula:**

$$FCFF = EBIT \times (1 - t) + D\&A - Capex - \Delta NWC$$

**FCFE formula (levered):**

$$FCFE = NI + D\&A - Capex - \Delta NWC + Net\ Borrowing$$

In both formulas, capex is a direct cash outflow. Unlike D&A, which is a non-cash add-back, capex is the actual cash cost of acquiring or maintaining productive assets. Analysts must model capex as a distinct line from D&A even though the two are related, because in steady state they converge but during growth or investment cycles they diverge substantially.

### Categorizing Capex

Capex is generally decomposed into two categories for modeling purposes:

- **Maintenance capex**: spending required to sustain existing revenue-generating capacity and offset the wear/obsolescence captured by depreciation. Conceptually approximates D&A over a full cycle.
- **Growth capex (expansion capex)**: spending on new capacity, new stores, new plants, new product lines, or M&A-adjacent organic investment intended to increase future revenue or margin.

This split matters because:

- Maintenance capex is relatively insensitive to growth assumptions and should track D&A or revenue with low variance.
- Growth capex should scale with the incremental revenue or capacity the model assumes, and should decay toward maintenance levels as the company matures and growth slows in the terminal period.

[Inference] Companies rarely disclose this split explicitly; analysts typically infer it from capex-to-D&A ratios, capacity utilization commentary, and management guidance on expansion plans.

### Common Capex Modeling Methodologies

**1. Percent of Revenue Method**

$$Capex_t = Revenue_t \times Capex\ Margin_t$$

The capex margin is typically derived from a historical average (3–5 year trailing) and then faded toward an industry-appropriate steady-state level over the explicit forecast horizon. This is the most widely used method for mature, asset-intensive businesses (utilities, industrials, telecom) where capex scales roughly linearly with revenue.

**2. Capex-to-D&A Ratio Method**

$$Capex_t = D\&A_t \times Ratio_t$$

Used when the analyst wants to explicitly anchor capex to the depreciation of the existing asset base. A ratio above 1.0x implies the asset base is growing in real terms (capex exceeds the replacement of depreciating assets); a ratio of exactly 1.0x implies a steady-state, non-growing net PP&E base; a ratio below 1.0x implies the company is under-investing or harvesting the asset base. This method is common in capital-intensive sectors such as oil & gas, mining, and telecom infrastructure, where the relationship between reinvestment and the existing capital stock is a key valuation debate.

**3. Fixed Asset Turnover / Incremental Capex Method**

$$Capex_t = \frac{\Delta Revenue_t}{Incremental\ Asset\ Turnover}$$

This approach explicitly links new capex to the incremental revenue the company needs to support, useful for high-growth companies (data centers, semiconductor fabs, capacity-constrained manufacturers) where capex is lumpy and tied to discrete capacity additions rather than smooth revenue scaling.

**4. Absolute Dollar / Management Guidance Method**

For near-term years (typically Year 1–2 of the explicit forecast), many analysts simply use management's disclosed capex guidance (from earnings calls, 10-K capex outlook sections, or investor day presentations) rather than a formula-driven estimate, then transition to a formulaic approach for out-years where no guidance exists.

**5. Build-Up / Unit Economics Method**

For companies with discrete, repeatable investment units (e.g., retail stores, hotel rooms, drilling wells, cell towers), capex is built bottom-up:

$$Capex_t = (\#\ New\ Units_t \times Cost\ per\ Unit) + Maintenance\ Capex_t$$

This is the most granular and most defensible method when the company discloses unit-level economics, and is standard practice in retail, hospitality, and energy E&P equity research.

### Capex and the Terminal Value Problem

The terminal value typically represents 60–80% of total enterprise value in a standard two-stage DCF, which makes the terminal-year capex assumption disproportionately important. [Inference] The exact proportion varies widely by discount rate, growth rate, and forecast horizon length. The standard terminal-year constraint is:

$$Capex_{terminal} = D\&A_{terminal}$$

This equality reflects the steady-state assumption that a mature, non-growing (or growing at the rate of inflation/GDP) firm reinvests exactly enough to replace depreciating assets, with no incremental capacity growth. Setting terminal capex materially above or below terminal D&A implicitly assumes indefinite real asset-base growth or shrinkage, which is inconsistent with a perpetuity assumption and will distort the terminal value.

A more rigorous formulation ties terminal capex to the terminal growth rate via the reinvestment rate:

$$Reinvestment\ Rate = \frac{Capex - D\&A + \Delta NWC}{EBIT(1-t)}$$



$$g = ROIC \times Reinvestment\ Rate$$

Rearranging, terminal capex net of D&A should be sized so that the implied reinvestment rate, combined with the assumed return on invested capital (ROIC), produces the terminal growth rate used in the Gordon Growth terminal value formula. This is the single most common internal-consistency check analysts fail to perform, and its absence is a frequent critique in fundamental equity research review.

### Depreciation Schedule Linkage

Capex assumptions must roll forward into a PP&E and depreciation schedule to maintain balance sheet and income statement consistency:

$$Net\ PP\&E_t = Net\ PP\&E_{t-1} + Capex_t - D\&A_t$$

Depreciation itself is frequently modeled as a function of the beginning or average gross/net PP&E balance and an assumed useful life or depreciation rate, rather than a flat percent of revenue, particularly in models built for asset-heavy sectors where the fixed asset roll-forward is scrutinized by clients (e.g., utilities, REITs, airlines).

### Sector-Specific Capex Considerations

| Sector | Dominant Capex Driver | Typical Modeling Approach |
| --- | --- | --- |
| Utilities | Regulatory rate base growth | Percent of rate base / regulatory capex plan |
| Oil & Gas E&P | Reserve replacement, well economics | Unit build-up ($/well, $/boe) |
| Telecom | Network/spectrum buildout | Capex-to-revenue with technology cycle overlay (e.g., 5G rollout) |
| Retail | Store count growth | Unit build-up ($ per new store + maintenance/store) |
| Software/SaaS | Low capex intensity, capitalized software | Percent of revenue, often <5% |
| Airlines | Fleet renewal | Discrete aircraft delivery schedules |
| Manufacturing | Capacity utilization | Fixed asset turnover / incremental capex |

### Capitalized Software and R&D Adjustments

For technology and software companies, analysts increasingly adjust standard capex definitions:

- **Capitalized software development costs** appear within capex or as a separate investing line and should be forecast based on engineering headcount growth or as a percent of R&D spend, not simply revenue.
- Some equity research practitioners **capitalize R&D** for analytical purposes (treating a portion of R&D as an economic investment similar to capex) to normalize ROIC and reinvestment rate comparisons across companies with different accounting treatments (expensed R&D vs. capitalized capex). This is an analytical adjustment, not a GAAP/IFRS requirement, and treatment varies by analyst and by firm methodology. [Unverified: specific capitalization rates and useful-life assumptions used by any given practitioner are not standardized across the industry.]

### Common Modeling Errors

- **Static capex margin held flat through explosive revenue growth**, understating cash outflows during the buildout phase.
- **Failing to fade growth capex toward maintenance levels** as the explicit forecast approaches the terminal year, causing terminal capex to be materially disconnected from the terminal growth assumption.
- **Ignoring lumpiness**: capex-intensive businesses (e.g., shipping, airlines, semiconductor fabs) often have multi-year capex cycles tied to discrete asset deliveries; smoothing this into a constant percent-of-revenue distorts near-term free cash flow timing, which matters for NPV given time-value discounting.
- **Inconsistent capex/D&A ratio in the terminal year**, breaking the reinvestment-rate-to-growth-rate identity described above.
- **Not reconciling capex per the cash flow statement with capex implied by PP&E roll-forward**, particularly when M&A, asset disposals, or foreign currency translation affect the PP&E balance independent of organic capex.

### Sensitivity and Scenario Analysis

Because capex assumptions are a primary lever for both near-term free cash flow and terminal value, equity research models typically stress-test:

- Capex margin +/- 100–200 bps versus base case, showing the resulting swing in price target.
- Bull/base/bear scenarios tying capex intensity to differing growth trajectories (e.g., aggressive capacity expansion vs. capital discipline/harvest scenarios).
- Terminal reinvestment rate sensitivity, since this interacts multiplicatively with the ROIC assumption to determine sustainable terminal growth.

### Illustrative Capex Buildup (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 780 380">
\<style\>
.box{fill:#f4f6f8;stroke:#333;stroke-width:1.5;}
.hdr{fill:#dbe7f5;stroke:#333;stroke-width:1.5;}
.txt{font-family:Arial,Helvetica,sans-serif;font-size:13px;fill:#111;}
.lbl{font-family:Arial,Helvetica,sans-serif;font-size:12px;fill:#333;}
.arrow{stroke:#333;stroke-width:1.5;marker-end:url(#arrow);fill:none;}
\</style\>
<text x="390" y="24" text-anchor="middle" font-family="Arial" font-size="16" font-weight="bold" fill="#111">Capex Assumptions in DCF — Data Flow (svg_diagram)</text>

<rect x="20" y="50" width="160" height="55" class="hdr" />
<text x="100" y="72" text-anchor="middle" class="txt" font-weight="bold">Revenue Forecast</text>
<text x="100" y="90" text-anchor="middle" class="lbl">Explicit period drivers</text>
<rect x="220" y="50" width="180" height="55" class="box" />
<text x="310" y="72" text-anchor="middle" class="txt" font-weight="bold">Capex Methodology</text>
<text x="310" y="90" text-anchor="middle" class="lbl">% Rev / Capex-D&amp;A / Unit build</text>
<rect x="440" y="50" width="160" height="55" class="hdr" />
<text x="520" y="72" text-anchor="middle" class="txt" font-weight="bold">Capex ($)</text>
<text x="520" y="90" text-anchor="middle" class="lbl">Annual forecast</text>
<rect x="640" y="50" width="120" height="55" class="box" />
<text x="700" y="72" text-anchor="middle" class="txt" font-weight="bold">FCFF/FCFE</text>
<text x="700" y="90" text-anchor="middle" class="lbl">Cash outflow</text>
<rect x="220" y="150" width="180" height="55" class="hdr" />
<text x="310" y="172" text-anchor="middle" class="txt" font-weight="bold">PP&amp;E Roll-Forward</text>
<text x="310" y="190" text-anchor="middle" class="lbl">Beg PP&amp;E + Capex - D&amp;A</text>
<rect x="440" y="150" width="160" height="55" class="box" />
<text x="520" y="172" text-anchor="middle" class="txt" font-weight="bold">Depreciation (D&amp;A)</text>
<text x="520" y="190" text-anchor="middle" class="lbl">Feeds EBIT and add-back</text>
<rect x="220" y="250" width="380" height="55" class="hdr" />
<text x="410" y="272" text-anchor="middle" class="txt" font-weight="bold">Reinvestment Rate = (Capex - D&amp;A + ΔNWC) / EBIT(1-t)</text>
<text x="410" y="290" text-anchor="middle" class="lbl">Links capex to ROIC and growth</text>
<rect x="260" y="330" width="300" height="40" class="box" />
<text x="410" y="355" text-anchor="middle" class="txt" font-weight="bold">Terminal Value (g = ROIC × Reinvestment Rate)</text>
<path d="M180,77 L220,77" class="arrow" />
<path d="M400,77 L440,77" class="arrow" />
<path d="M600,77 L640,77" class="arrow" />
<path d="M520,105 L520,150" class="arrow" />
<path d="M310,105 L310,150" class="arrow" />
<path d="M400,177 L440,177" class="arrow" />
<path d="M310,205 L310,250" class="arrow" />
<path d="M520,205 L520,250" class="arrow" />
<path d="M410,305 L410,330" class="arrow" />
</svg>

### Capex-D&A Convergence Toward Terminal Year (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 350">
\<style\>
.axis{stroke:#333;stroke-width:1.5;}
.gridline{stroke:#ddd;stroke-width:1;}
.capexline{stroke:#c0392b;stroke-width:2.5;fill:none;}
.daline{stroke:#2874a6;stroke-width:2.5;fill:none;}
.txt{font-family:Arial,Helvetica,sans-serif;font-size:12px;fill:#111;}
.lbl{font-family:Arial,Helvetica,sans-serif;font-size:13px;fill:#111;font-weight:bold;}
\</style\>
<text x="350" y="24" text-anchor="middle" font-family="Arial" font-size="15" font-weight="bold" fill="#111">Capex vs D&amp;A Convergence to Terminal Year (svg_diagram)</text>
<line x1="70" y1="280" x2="650" y2="280" class="axis" />
<line x1="70" y1="280" x2="70" y2="50" class="axis" />
<text x="30" y="285" class="txt">$0</text>
<text x="360" y="310" class="txt">Forecast Year (1 → Terminal)</text>
<text x="30" y="60" class="txt">$ mm</text>
<line x1="70" y1="230" x2="650" y2="230" class="gridline" />
<line x1="70" y1="180" x2="650" y2="180" class="gridline" />
<line x1="70" y1="130" x2="650" y2="130" class="gridline" />
<line x1="70" y1="80" x2="650" y2="80" class="gridline" />
<path d="M100,90 L200,110 L300,140 L400,165 L500,185 L600,195" class="capexline" />
<path d="M100,220 L200,210 L300,200 L400,192 L500,196 L600,195" class="daline" />
<circle cx="600" cy="195" r="5" fill="#111" />
<text x="560" y="215" class="txt">Terminal: Capex = D&amp;A</text>
<rect x="450" y="55" width="14" height="14" fill="#c0392b" />
<text x="470" y="66" class="txt">Growth Capex (fading)</text>
<rect x="450" y="75" width="14" height="14" fill="#2874a6" />
<text x="470" y="86" class="txt">D&amp;A (rising with asset base)</text>
</svg>

### Reinvestment Rate to Growth Linkage (Mermaid)

```mermaid
flowchart LR
    A[EBIT x (1-t)] --> B[Reinvestment Rate]
    C[Capex] --> D[Capex - D&A + Delta NWC]
    E[D&A] --> D
    F[Delta NWC] --> D
    D --> B
    B --> G[g = ROIC x Reinvestment Rate]
    H[ROIC] --> G
    G --> I[Terminal Growth Rate]
    I --> J[Gordon Growth Terminal Value]
```

### Worked Example

Assume a mature industrial company in Year 5 (terminal year) of an explicit DCF forecast:

- Revenue: $2,000mm
- EBIT margin: 18% → EBIT = $360mm
- Tax rate: 25% → EBIT(1-t) = $270mm
- Target terminal growth rate (g): 2.5%
- Assumed ROIC: 10%

Solve for required reinvestment rate:

$$Reinvestment\ Rate = \frac{g}{ROIC} = \frac{2.5\%}{10\%} = 25\%$$

Required net reinvestment dollars:

$$0.25 \times \$270mm = \$67.5mm = (Capex - D\&A + \Delta NWC)$$

If $\Delta NWC$ is assumed to be $10mm, then:

$$Capex - D\&A = \$57.5mm$$

If D&A is projected at $140mm (based on the PP&E roll-forward), terminal capex should be set at:

$$Capex_{terminal} = \$140mm + \$57.5mm = \$197.5mm$$

This is the internally consistent terminal capex figure — notably above the naive "Capex = D&A" simplification, because it reflects the fact that a 2.5% terminal growth rate still requires modest net reinvestment above pure replacement, not a strict Capex = D&A equality. [Inference] Many practitioner models default to the simpler Capex = D&A heuristic for terminal year as an approximation, sacrificing this precision for simplicity; the choice between the two is a modeling judgment call, not a settled convention.

**Related Topics:**

- Reinvestment rate and its relationship to ROIC and sustainable growth
- Terminal value methodologies (Gordon Growth vs. exit multiple) and their sensitivity to capex assumptions
- Working capital modeling and its interaction with capex in free cash flow build
- Capitalization of R&D and software development costs in valuation adjustments
- Sector-specific capex cycles (semiconductor capex cycles, telecom spectrum auctions, airline fleet orders)
- Free cash flow conversion analysis and capex intensity benchmarking across peer sets
- Sensitivity and scenario modeling techniques in DCF construction
- Depreciation methodologies (straight-line vs. declining balance) and their capex feedback effects