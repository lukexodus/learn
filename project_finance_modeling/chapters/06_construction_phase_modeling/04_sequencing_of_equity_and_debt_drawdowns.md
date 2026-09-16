## Sequencing of Equity and Debt Drawdowns

### Overview

Drawdown sequencing defines the specific order and proportion in which equity, subordinated debt, and senior debt are contributed to fund construction spend over time. While the Sources of Funds establishes the total quantum of each capital instrument, sequencing determines the period-by-period mechanics of how those instruments are actually drawn — a structural choice with direct consequences for lender risk exposure, sponsor equity IRR, and total capitalized interest cost.

### The Three Core Sequencing Methodologies

**Key Points**

- **Equity-first (front-loaded equity)**: 100% of committed equity (and typically subordinated debt) is drawn and spent before any senior debt drawdown begins.
- **Pro-rata drawdown**: Equity and debt are drawn simultaneously in fixed proportion to their respective shares of total funding, in every period throughout construction.
- **Debt-first (back-ended equity)**: Senior debt is drawn first, with equity injected later in the construction period or at/near COD.

### Why Sequencing Is Contractually Significant

**Key Points**

- Lenders generally prefer equity-first or pro-rata sequencing because it demonstrates sponsor commitment early and reduces lender exposure in the event of an early-stage construction failure or sponsor default — the sponsor's capital is "at risk" before the lender's.
- **[Unverified]** — Whether a specific transaction mandates equity-first, pro-rata, or another sequencing methodology is a negotiated term set out in the common terms agreement or facility agreement, and market practice varies by sector, lender group risk appetite, and jurisdiction; no default sequencing convention should be assumed without confirming the term sheet.
- Sequencing directly affects total Interest During Construction (IDC): later debt drawdown (equity-first) means the debt balance is outstanding for a shorter average period, generally reducing total capitalized interest relative to pro-rata or debt-first sequencing, all else equal.

### Sequencing Comparison Diagram

```mermaid
flowchart TD
    subgraph EquityFirst["Equity-First Sequencing (svg_diagram)"]
    direction LR
    A1[Month 1-8: 100% Equity Drawn] --> A2[Month 9-24: 100% Debt Drawn]
    end
    subgraph ProRata["Pro-Rata Sequencing (svg_diagram)"]
    direction LR
    B1[Every Month: Fixed % Equity + Fixed % Debt] --> B2[Ratio held constant throughout]
    end
    subgraph DebtFirst["Debt-First Sequencing (svg_diagram)"]
    direction LR
    C1[Month 1-16: 100% Debt Drawn] --> C2[Month 17-24: 100% Equity Drawn]
    end
```

### Modeling Equity-First Sequencing

**Example**



```
Period:                        M1      M2      M3      M4      M5
Period Capex Requirement:      15,000  20,000  25,000  30,000  30,000
Total Equity Commitment:       98,200

Equity Drawn this Period:      15,000  20,000  25,000  30,000  8,200
Cumulative Equity Drawn:       15,000  35,000  60,000  90,000  98,200

Debt Drawn this Period:        0       0       0       0       21,800
Cumulative Debt Drawn:         0       0       0       0       21,800
```

Formula pattern (Excel-style):



```
Equity Draw = MIN(PeriodCapexRequirement, TotalEquityCommitment - CumulativeEquityDrawn_PriorPeriod)
Debt Draw   = PeriodCapexRequirement - Equity Draw
```

### Modeling Pro-Rata Sequencing

**Example**



```
Target Gearing: 70% Debt / 30% Equity

Period:                        M1      M2      M3      M4      M5
Period Capex Requirement:      15,000  20,000  25,000  30,000  30,000
Equity Drawn (30%):            4,500   6,000   7,500   9,000   9,000
Debt Drawn (70%):              10,500  14,000  17,500  21,000  21,000
```

Formula pattern (Excel-style):



```
Equity Draw = PeriodCapexRequirement × EquityPercentage
Debt Draw   = PeriodCapexRequirement × DebtPercentage
```

**Key Points**

- Pro-rata sequencing is generally simpler to model and produces a smoother, more predictable IDC accrual profile than equity-first, but requires an explicit true-up mechanism if actual gearing drifts from target due to rounding or timing mismatches across periods.

### Modeling Debt-First Sequencing

**Example**



```
Period:                        M1      M2      M3      M18     M19
Period Capex Requirement:      15,000  20,000  25,000  20,000  15,000
Debt Drawn this Period:        15,000  20,000  25,000  20,000  0
Cumulative Debt Drawn:         15,000  35,000  60,000  ...     338,000

Equity Drawn this Period:      0       0       0       0       15,000
Cumulative Equity Drawn:       0       0       0       0       98,200
```

**[Inference]** — Debt-first sequencing is comparatively uncommon in traditional limited-recourse project finance specifically because it increases lender exposure ahead of demonstrated sponsor commitment; where it does appear, it is more often associated with structures where sponsors have separately provided strong completion guarantees or other credit support that substitutes for early equity injection as a risk mitigant.

### Interaction with Interest During Construction (IDC)

Because IDC accrues only on the **drawn debt balance**, sequencing has a direct, quantifiable effect on total capitalized interest:

$$\text{Total IDC} = \sum_{t=1}^{T} \text{DebtBalance}_t \times r_t$$

Where $\text{DebtBalance}_t$ is the outstanding drawn debt balance in period $t$ and $r_t$ is the period interest rate. Equity-first sequencing minimizes $\text{DebtBalance}_t$ in early periods (holding total debt drawn constant), which reduces the cumulative sum and therefore total IDC relative to pro-rata or debt-first sequencing over an identical construction schedule.

**Example**



```
Illustrative comparison, same $338,000 total debt, same 24-month construction period, 6.5% p.a. rate:

Equity-First Sequencing:    Total IDC ≈ $19,800,000  (debt drawn mostly in months 9-24)
Pro-Rata Sequencing:        Total IDC ≈ $28,100,000  (debt drawn proportionally throughout)
Debt-First Sequencing:      Total IDC ≈ $34,500,000  (debt drawn mostly in months 1-16)
```

**[Inference]** — These illustrative figures demonstrate the direction and rough magnitude of the effect rather than a universal ratio; the actual difference in any specific transaction depends on the interest rate, total construction duration, and the shape of the underlying spend S-curve, and should be calculated directly from the transaction's own assumptions rather than assumed from a generic benchmark.

### Equity Bridge Loans as a Sequencing Variant

**Key Points**

- An equity bridge loan (EBL) allows the project company to draw against a *committed* equity amount without the sponsor actually contributing cash until later (often at or near COD), effectively achieving the funding-timing benefit of debt-first sequencing for the sponsor's cash flow while the *model* still records the funding source as equity-first from the project company's balance sheet perspective.
- This distinction matters when modeling: the "Sources of Funds" allocation (equity vs. debt) may show equity-first sequencing, while the sponsor's own cash IRR calculation reflects a deferred contribution enabled by the EBL — these are two related but distinct sequencing questions that should not be conflated within the model architecture.

### True-Up Mechanisms for Sequencing Precision

**Key Points**

- Rounding, minimum drawdown thresholds (many facility agreements specify a minimum drawdown amount per request), and timing mismatches between cost incurrence and cash payment can cause actual cumulative gearing to drift slightly from the target ratio in a pro-rata mechanism.
- A **true-up formula** at COD (or at each drawdown date) compares actual cumulative equity/debt percentages against the target and adjusts the final drawdown(s) to bring the ratio back into exact alignment by financial completion.

### Validation and Error-Checking

**Key Points**

- **Sequencing consistency check**: Confirm the modeled drawdown mechanism matches exactly the methodology specified in the term sheet/facility agreement — a common review step in lender due diligence.
- **Cumulative total reconciliation**: Confirm cumulative equity drawn plus cumulative debt drawn equals cumulative total spend in every period, not just at the final COD total.
- **Minimum drawdown compliance check**: Where the facility agreement specifies a minimum drawdown amount, confirm no modeled period draw falls below this threshold (which would be operationally infeasible in practice).
- **Gearing convergence check**: For pro-rata sequencing, confirm the final cumulative debt/equity ratio at COD matches the target gearing ratio exactly, accounting for any true-up adjustment.

### Common Pitfalls

**Key Points**

- Assuming pro-rata sequencing as a default without confirming the actual term sheet requirement, materially misstating IDC and peak funding requirement calculations.
- Failing to model minimum drawdown thresholds, producing a theoretically precise but operationally unrealistic drawdown schedule with many small, sub-threshold draws.
- Conflating the equity bridge loan mechanism (sponsor cash-flow timing) with the project company's Sources of Funds sequencing (accounting/funding-source classification), leading to double-counting or omission of the EBL as a distinct financing instrument.
- Neglecting to build a true-up mechanism for pro-rata sequencing, leaving the model with a persistent small gearing mismatch that compounds into a reconciliation break at COD.

### Related Topics

- Sources of Funds and the Financing Plan
- Drawdown Schedules and S-Curve Modeling
- Interest During Construction (IDC) Capitalization Mechanics
- Equity Bridge Loan Mechanics
- Circularity Management in Construction-Phase Models
- Debt Sizing, Sculpting, and Gearing Constraints