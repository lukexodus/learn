## S-Curve Development and Interpretation


### Definition

An S-curve is a graphical plot of cumulative project values — typically Planned Value (PV), Earned Value (EV), and Actual Cost (AC) — against time. It is called an "S-curve" because cumulative progress on most projects naturally follows an S-shaped pattern: slow initial ramp-up, accelerating progress through the middle of the project, then a tapering rate of progress as the project nears completion. S-curves are the primary visual reporting tool in EVM, condensing the entire cost and schedule performance story into a single chart.

### Why the "S" Shape Occurs

The characteristic S-shape reflects the typical resource loading pattern of most projects:

- **Early phase**: planning, mobilization, and initial setup consume time with relatively low cumulative cost/value accumulation — a shallow slope
- **Middle phase**: peak execution activity (construction, development, production) drives the steepest portion of the curve as resources are fully engaged
- **Late phase**: closeout, punch-list work, and final testing/handover activities slow the rate of value accumulation again — a shallow slope returning near the top

This shape is common enough that deviations from a typical S-curve pattern (e.g., a curve that stays flat too long, or accelerates too sharply) can themselves be a diagnostic signal worth investigating.

### Constructing the S-Curve

**Step 1 — Establish the PV curve (baseline) first.** During planning, time-phase the total BAC across the project schedule, distributing budget to each period based on when the corresponding work is scheduled. This produces the cumulative PV line — the baseline against which all future performance is measured.

**Step 2 — Overlay the EV curve as the project executes.** At each reporting period, plot cumulative EV based on actual physical progress measured via the chosen EV measurement method (fixed formula, percent complete, milestones, units completed, etc.).

**Step 3 — Overlay the AC curve.** At each reporting period, plot cumulative AC from accounting/timesheet data.

**Step 4 — Extend a forecast curve (optional but common).** Many S-curve reports include a fourth, dashed or distinct line projecting forward using EAC and IEAC(t), showing the forecasted trajectory to completion alongside the historical actuals.

### Reading the Three (or Four) Lines Together

| Visual Pattern | Interpretation |
| --- | --- |
| EV line below PV line | Behind schedule (negative SV) |
| EV line above PV line | Ahead of schedule (positive SV) |
| EV line below AC line | Over budget (negative CV) |
| EV line above AC line | Under budget (positive CV) |
| Growing gap between EV and PV over time | Worsening schedule trend |
| Growing gap between AC and EV over time | Worsening cost trend |
| Converging lines | Improving performance, possibly due to corrective action |

The vertical distance between any two curves at a given point in time is the corresponding variance (SV between EV and PV; CV between EV and AC) — the S-curve makes these variances visually intuitive without requiring the viewer to read raw numbers.

### Worked Example — Interpreting a Sample S-Curve Pattern

Consider a project at month 6 of a 10-month plan, with the following cumulative figures:

| Month | PV | EV | AC |
| --- | --- | --- | --- |
| 6 | $300,000 | $260,000 | $310,000 |

Plotted on an S-curve, at month 6 the EV line sits below both the PV line (indicating $SV = 260{,}000 - 300{,}000 = -\$40{,}000$, behind schedule) and the AC line (indicating $CV = 260{,}000 - 310{,}000 = -\$50{,}000$, over budget). Visually, this appears as the EV curve tracking beneath both the PV and AC curves — the classic "worst case" quadrant pattern made immediately visible without calculation.

If a forecast line is added, extending from the current EV/AC trend using $EAC = BAC/CPI$, the forecast curve would show projected total cost exceeding BAC, with the completion point shifted later than the original planned finish month — giving stakeholders an at-a-glance view of both magnitude and direction of projected overrun/delay.

### S-Curve Variants and Extensions

- **Cumulative vs. incremental (period) curves**: cumulative S-curves show total-to-date trends; incremental/period bar overlays (often combined as a combo chart) show period-by-period performance, useful for spotting recent improvement or deterioration that cumulative totals can mask
- **Resource/labor-hour S-curves**: some organizations plot S-curves in labor-hours rather than currency, particularly useful when currency fluctuation or rate changes would distort a cost-based view
- **Multiple work-package S-curves**: for large, multi-workstream projects, individual S-curves per major WBS element or phase can reveal where problems concentrate, which a single project-level curve might average out and obscure
- **Contract milestone overlay**: adding vertical markers for key contractual milestones or deliverable dates onto the S-curve helps tie EVM performance directly to contractual risk points

### Common Pitfalls in S-Curve Development and Reading

- **Poorly time-phased PV baseline**: if the original PV curve doesn't accurately reflect realistic resource loading (e.g., linear distribution when actual work is naturally S-shaped), variances calculated against it will be systematically misleading from the start
- **Inconsistent measurement methods feeding EV**: mixing subjective percent-complete estimates with objective milestone-based measurement across different WBS elements can create an EV curve with inconsistent reliability at different points
- **Reading only the endpoint gap, ignoring trend shape**: two projects can have the same current-month variance but very different trend trajectories (one improving, one worsening) — the shape of the curve over time matters as much as the current snapshot
- **Omitting a forecast line**: an S-curve showing only historical data requires the viewer to mentally extrapolate; adding an explicit forecast curve makes the likely outcome immediately visible
- **Using S-curves as the sole reporting tool without supporting root cause narrative**: the visual shows *that* and *how much* variance exists, but not *why* — S-curves should be paired with variance analysis reports for complete decision support

### Visual: S-Curve Structure (Conceptual)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 420">
<title>S-Curve: Cumulative PV, EV, and AC Over Time (svg_diagram)</title>
<rect x="0" y="0" width="700" height="420" fill="#ffffff" />
<line x1="70" y1="370" x2="670" y2="370" stroke="#333333" stroke-width="2" />
<line x1="70" y1="370" x2="70" y2="30" stroke="#333333" stroke-width="2" />
<text x="370" y="405" font-size="14" text-anchor="middle" fill="#333333">Time (Reporting Periods)</text>
<text x="25" y="200" font-size="14" text-anchor="middle" fill="#333333" transform="rotate(-90 25 200)">Cumulative Value ($)</text>
<path d="M 70 370 C 150 365, 250 300, 350 180 C 450 100, 550 55, 670 45" stroke="#1f77b4" stroke-width="3" fill="none" />
<text x="600" y="55" font-size="13" fill="#1f77b4">PV (Baseline)</text>
<path d="M 70 370 C 150 368, 250 330, 340 230 C 420 150, 480 110, 540 90" stroke="#2ca02c" stroke-width="3" fill="none" />
<text x="500" y="105" font-size="13" fill="#2ca02c">EV (Earned)</text>
<path d="M 70 370 C 150 366, 250 310, 345 210 C 435 130, 500 90, 560 70" stroke="#d62728" stroke-width="3" fill="none" />
<text x="500" y="150" font-size="13" fill="#d62728">AC (Actual Cost)</text>
<path d="M 540 90 C 580 75, 620 60, 660 50" stroke="#2ca02c" stroke-width="2" stroke-dasharray="6,4" fill="none" />
<path d="M 560 70 C 590 55, 620 40, 650 25" stroke="#d62728" stroke-width="2" stroke-dasharray="6,4" fill="none" />
<text x="450" y="20" font-size="12" fill="#666666">Dashed = Forecast (EAC trend)</text>
<line x1="345" y1="30" x2="345" y2="370" stroke="#999999" stroke-width="1" stroke-dasharray="3,3" />
<text x="350" y="385" font-size="12" fill="#666666">Report Date</text>
</svg>

### Related Topics

- Time-phased budgeting and PV curve development
- Cost Variance (CV) and Schedule Variance (SV) visual interpretation
- Estimate at Completion (EAC) forecast overlay
- Earned Schedule (ES) as a companion time-based analytical tool
- Performance measurement baseline (PMB) construction
- Executive dashboard design for EVM reporting