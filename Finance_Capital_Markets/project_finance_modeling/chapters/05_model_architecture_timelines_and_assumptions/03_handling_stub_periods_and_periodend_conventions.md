## Handling Stub Periods and Period-End Conventions

### Overview

A stub period is a period in a project finance model whose length is shorter (or occasionally longer) than the model's standard periodicity, arising because a key date — financial close, COD (Commercial Operations Date), a payment date, or concession expiry — does not align with a clean calendar boundary. Period-end conventions are the rules that define exactly when a period is deemed to start and end, and how contractual dates are adjusted when they fall on non-business days. Together, these mechanics ensure that interest, revenue, and covenant calculations remain accurate at the edges of the model timeline, where most reconciliation errors originate.

### Why Stub Periods Arise

**Key Points**

- **Financial close mid-period**: Debt typically starts accruing interest from financial close, which rarely falls on the first day of a month or quarter.
- **COD mid-period**: The transition from construction to operations often occurs mid-month or mid-quarter, requiring a split between construction-phase and operations-phase treatment within a single period.
- **Concession/contract expiry mid-period**: A PPA (Power Purchase Agreement) or concession term ending mid-quarter creates a short final period.
- **Irregular first debt service payment**: Loan agreements frequently specify a first repayment date that captures more or less than a full standard period of accrued interest (a "long first coupon" or "short first coupon").
- **Leap years and month-length variation**: Even within a "standard" period, actual/actual day-count conventions cause period length to vary (28–31 days monthly, 90–92 days quarterly).

### Categories of Stub Periods

1. **Opening stub** — from financial close (or model start date) to the first standard period-end date. Usually shorter than a full period.
2. **Phase-transition stub** — from COD to the next standard period-end date, where the period must be split proportionally between construction-phase and operations-phase treatment.
3. **Closing stub** — from the last standard period-end date to contract/concession expiry or final maturity. Can be shorter or longer than standard, depending on how the final date falls.
4. **Payment-date stub** — where a debt service payment date does not align with the calculation period-end, creating a "long" or "short" first/last coupon on the debt schedule specifically (independent of the operational timeline).

### Stub Period Timeline

```mermaid
flowchart LR
    A[Financial Close: 15-Mar] -->|Opening Stub: 15-Mar to 31-Mar| B[Q1 Period-End: 31-Mar]
    B -->|Full Quarter| C[Q2 Period-End: 30-Jun]
    C -->|Full Quarter| D[Q3 Period-End: 30-Sep]
    D -->|Phase Transition Stub: COD 12-Aug splits Q3| E[COD: 12-Aug]
    D --> F[Q4 Period-End: 31-Dec]
    F -->|Full Quarters continue...| G[Last Full Period-End]
    G -->|Closing Stub: Partial Period| H[Concession Expiry: 22-Nov]
```

### Structural Approaches to Modeling Stub Periods

**Approach 1: Explicit Stub Column**

Insert a dedicated column in the timeline representing only the stub duration, distinct from the surrounding standard-length periods. This is the most transparent and auditable method.



```
Period:     Stub-1   | Q1-2027 | Q2-2027 | Q3-2027 (stub) | Q3b | Q4-2027
Start:      15-Mar    | 1-Apr   | 1-Jul   | 1-Oct          |12-Aug| ...
End:        31-Mar    | 30-Jun  | 30-Sep  | 11-Aug         |30-Sep| ...
Days:       17        | 91      | 91      | ...            | ...  | ...
```

**Approach 2: Pro-Rata Flag Within a Standard Period**

Keep the standard period column structure intact, but embed a flag row and pro-ration factor that splits the single period's cash flows/interest between two treatments (e.g., construction days vs. operating days within the same column). This keeps the model narrower but requires every downstream formula to reference the split factor.

$$\text{ProRataFactor} = \frac{\text{Days in sub-period}}{\text{Total days in period}}$$

**[Inference]** — The explicit stub-column approach is generally preferred in lender/bank-grade models because it produces an auditable one-to-one mapping between column and cash-flow driver, whereas the pro-rata-flag approach, while more compact, is more prone to formula errors when analysts forget to apply the split factor consistently across all line items.

### Interest Accrual on Stub Periods

Interest during a stub period must use the same day-count basis as the full-period convention but applied to the actual (shorter or longer) day count:

$$\text{Interest}_{\text{stub}} = \text{Principal} \times \text{Rate} \times \frac{\text{Days}_{\text{stub}}}{\text{Basis}}$$

Where $\text{Basis}$ is 360 or 365 depending on the governing loan agreement — **not** automatically adjusted just because the period is short. A common modeling error is hard-coding a "full quarter" interest formula (e.g., Rate/4) that silently misstates interest in the opening and closing stub periods.

### Period-End Date Conventions (Business Day Adjustment)

When a contractual period-end or payment date falls on a weekend or holiday, financing agreements specify an adjustment convention:

| Convention | Rule | Effect |
| --- | --- | --- |
| Following | Move forward to next business day | May push into a new month |
| Modified Following | Move forward, unless it crosses into the next month, then move backward | Keeps date within the same month |
| Preceding | Move backward to prior business day | Never crosses into next month |
| No Adjustment | Date is used as-is regardless of business day status | Used for pure calculation dates, not payment dates |

**[Unverified]** — The applicable convention (Following, Modified Following, etc.) is always specified in the credit agreement or bond indenture and must be confirmed against source documentation; it is not inferable from periodicity alone.

**Key Points**

- Business day adjustment conventions affect the actual **payment date** (cash movement) but frequently do **not** change the **interest accrual period-end date** — these two dates can diverge, requiring the model to track them as separate rows.
- Adjusting a payment date without adjusting the corresponding accrual date is a common source of small but persistent reconciliation breaks between the debt schedule and the cash flow waterfall.

### Practical Example: Modeling an Opening Stub

**Example**

Assume financial close on 15-Mar-2027, with a quarterly model starting Q1 (calendar quarter-end 31-Mar):



```
Financial Close:        15-Mar-2027
First Period-End:       31-Mar-2027
Stub Length:            17 days (16-Mar through 31-Mar, or per accrual convention)
Debt Balance:           $100,000,000
Interest Rate:          6.00% p.a.
Day-Count Basis:        Actual/360

Stub Interest = $100,000,000 × 6.00% × (17/360) = $283,333
```

This stub interest amount then feeds into the first period's debt service and IDC (Interest During Construction) capitalization schedule, distinct from the full-quarter interest calculation applied from Q2 onward.

### Closing Stub and Final Maturity

At the tail end of the model, the closing stub often coincides with:

- Final debt repayment (bullet or final sculpted amortization payment)
- Release of remaining reserve account balances (DSRA — Debt Service Reserve Account)
- Terminal value or residual asset value recognition (if applicable)
- Final equity distribution

**[Inference]** — Models frequently force the final period to absorb any residual balancing amounts (e.g., true-up of accrued-but-unpaid interest, rounding differences from the day-count convention) to ensure the debt balance reaches exactly zero at maturity; this "plug" mechanic should be explicitly labeled and auditable rather than silently embedded in a generic formula.

### Common Errors and Review Checklist

**Key Points**

- Confirm interest accrual basis (360 vs. 365) is applied consistently, including within stub periods.
- Verify that construction-to-operations phase-transition stubs correctly allocate revenue, opex, and IDC between the two phases.
- Check that business-day-adjusted payment dates do not inadvertently alter the interest accrual calculation dates.
- Ensure the sum of all stub and full-period day counts reconciles exactly to the total number of calendar days between financial close and final maturity (no gaps or overlaps).
- Confirm the final period's debt balance nets to zero (or to the contractually expected balloon/bullet amount).

### Related Topics

- Monthly, Quarterly, and Annual Periodicity Conventions
- Interest During Construction (IDC) Capitalization Mechanics
- Debt Sizing, Sculpting, and Amortization Schedules
- Day-Count Conventions in Loan and Bond Documentation
- Debt Service Reserve Account (DSRA) Mechanics
- Circularity Management in Interest and Cash Sweep Calculations