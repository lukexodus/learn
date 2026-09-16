## Time Value of Money Review


### Core Concept

The time value of money (TVM) is the principle that a given sum of money available today is worth more than the same nominal sum available at a future date, because money in hand can be invested to earn a return over time. This principle underlies virtually all capital budgeting and long-term investment analysis, since it allows cash flows occurring at different points in time to be converted to a common point in time (typically the present) for valid comparison.

**Key Points — Why Money Has Time Value**

- **Opportunity cost**: money received today can be invested to earn a return, so waiting to receive it forfeits that potential earning.
- **Inflation risk**: purchasing power of a fixed sum typically erodes over time.
- **Uncertainty/risk**: a promised future payment carries risk of non-payment or delay, so it is worth less than a certain payment today of the same nominal amount.

### Key Variables in TVM Calculations

| Symbol | Meaning |
| --- | --- |
| $PV$ | Present value — value of a cash flow (or series) at time zero |
| $FV$ | Future value — value of a cash flow (or series) at a specified future date |
| $i$ (or $r$) | Interest rate (discount rate) per period |
| $n$ | Number of compounding/discounting periods |
| $PMT$ | Periodic payment amount in an annuity |

### Future Value of a Single Sum

Future value answers: "If I invest $X today at rate $i$, what will it grow to after $n$ periods?"

$$FV = PV \times (1 + i)^n$$

**Example**: $10,000 invested today at 6% annual interest for 5 years:

$$FV = 10,000 \times (1.06)^5 = 10,000 \times 1.33823 = \$13,382.30$$

### Present Value of a Single Sum

Present value answers the reverse question: "What is a future sum worth today, given a discount rate?" This is the more heavily used direction in capital budgeting, since investment decisions require converting future project cash flows back to present-day terms.

$$PV = \frac{FV}{(1 + i)^n} = FV \times (1 + i)^{-n}$$

**Example**: The present value of $13,382.30 to be received in 5 years, discounted at 6%:

$$PV = \frac{13,382.30}{(1.06)^5} = \frac{13,382.30}{1.33823} = \$10,000.00$$

This confirms the FV and PV formulas are algebraic inverses of one another.

### Present Value and Future Value of an Annuity

An **annuity** is a series of equal periodic cash flows occurring at regular intervals. Two forms are distinguished by timing:

- **Ordinary annuity**: payments occur at the **end** of each period (most common in capital budgeting, since operating cash flows are typically assumed to occur at period-end).
- **Annuity due**: payments occur at the **beginning** of each period.

**Present Value of an Ordinary Annuity:**

$$PV_{\text{annuity}} = PMT \times \left[\frac{1 - (1+i)^{-n}}{i}\right]$$

**Future Value of an Ordinary Annuity:**

$$FV_{\text{annuity}} = PMT \times \left[\frac{(1+i)^n - 1}{i}\right]$$

**Annuity Due Adjustment**: Since annuity-due payments occur one period earlier than ordinary-annuity payments, both the PV and FV of an annuity due equal the ordinary annuity value multiplied by $(1+i)$:

$$PV_{\text{annuity due}} = PV_{\text{ordinary annuity}} \times (1+i)$$

**Example**: PV of an ordinary annuity paying $5,000 per year for 4 years at 8%:

$$PV = 5,000 \times \left[\frac{1 - (1.08)^{-4}}{0.08}\right] = 5,000 \times 3.31213 = \$16,560.65$$

### Present Value of a Perpetuity

A **perpetuity** is an annuity with no defined end date — equal periodic payments continuing indefinitely.

$$PV_{\text{perpetuity}} = \frac{PMT}{i}$$

**Example**: A perpetuity paying $2,000 annually, discounted at 10%:

$$PV = \frac{2,000}{0.10} = \$20,000$$

**Growing perpetuity** (payments grow at constant rate $g$ per period, where $g < i$):

$$PV_{\text{growing perpetuity}} = \frac{PMT_1}{i - g}$$

### Compounding Frequency

When interest compounds more frequently than annually (e.g., monthly, quarterly), the formulas adjust the rate and number of periods to match the compounding frequency:

$$FV = PV \times \left(1 + \frac{i}{m}\right)^{n \times m}$$

where $m$ is the number of compounding periods per year. More frequent compounding at the same **nominal (stated) annual rate** produces a higher **effective annual rate (EAR)**:

$$EAR = \left(1 + \frac{i}{m}\right)^m - 1$$

**Example**: A nominal 12% annual rate compounded monthly:

$$EAR = \left(1 + \frac{0.12}{12}\right)^{12} - 1 = (1.01)^{12} - 1 = 0.12683 = 12.683\%$$

### Uneven (Mixed) Cash Flow Streams

Most real-world capital budgeting projects generate cash flows that vary from year to year rather than forming a level annuity. In this case, each cash flow must be discounted individually using the single-sum PV formula, and the results summed:

$$PV_{\text{total}} = \sum_{t=1}^{n} \frac{CF_t}{(1+i)^t}$$

**Example**: A project generates cash flows of $4,000 (Year 1), $6,000 (Year 2), and $8,000 (Year 3), discounted at 10%:

| Year | Cash Flow | Discount Factor $(1.10)^{-t}$ | Present Value |
| --- | --- | --- | --- |
| 1 | $4,000 | 0.9091 | $3,636.40 |
| 2 | $6,000 | 0.8264 | $4,958.40 |
| 3 | $8,000 | 0.7513 | $6,010.40 |
| **Total** |  |  | **$14,605.20** |

This total-PV-of-uneven-cash-flows technique is the computational foundation of the **Net Present Value (NPV)** method used throughout capital budgeting.

### Timeline Diagram

```mermaid
flowchart LR
    T0["Time 0: PV (Initial Investment or Value Today)"] -->|"Compounding: FV = PV(1+i)^n"| Tn["Time n: FV"]
    Tn -->|"Discounting: PV = FV / (1+i)^n"| T0
```

### SVG Illustration — Cash Flow Timeline

<ns0:svg xmlns:ns0="[http://www.w3.org/2000/svg" viewBox="0 0 680 260">](http://www.w3.org/2000/svg%22%3E)

<ns0:text x="340" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1f2937">Cash Flow Timeline (svg_diagram)</ns0:text>

<ns0:line x1="60" y1="140" x2="620" y2="140" stroke="#374151" stroke-width="2" />

<ns0:line x1="60" y1="130" x2="60" y2="150" stroke="#374151" stroke-width="2" />

<ns0:line x1="200" y1="130" x2="200" y2="150" stroke="#374151" stroke-width="2" />

<ns0:line x1="340" y1="130" x2="340" y2="150" stroke="#374151" stroke-width="2" />

<ns0:line x1="480" y1="130" x2="480" y2="150" stroke="#374151" stroke-width="2" />

<ns0:line x1="620" y1="130" x2="620" y2="150" stroke="#374151" stroke-width="2" />

<ns0:text x="60" y="170" text-anchor="middle" font-size="12" fill="#374151">Year 0</ns0:text>

<ns0:text x="200" y="170" text-anchor="middle" font-size="12" fill="#374151">Year 1</ns0:text>

<ns0:text x="340" y="170" text-anchor="middle" font-size="12" fill="#374151">Year 2</ns0:text>

<ns0:text x="480" y="170" text-anchor="middle" font-size="12" fill="#374151">Year 3</ns0:text>

<ns0:text x="620" y="170" text-anchor="middle" font-size="12" fill="#374151">Year 4</ns0:text>

<ns0:text x="200" y="120" text-anchor="middle" font-size="12" fill="#2563eb">+CF1</ns0:text>

<ns0:text x="340" y="120" text-anchor="middle" font-size="12" fill="#2563eb">+CF2</ns0:text>

<ns0:text x="480" y="120" text-anchor="middle" font-size="12" fill="#2563eb">+CF3</ns0:text>

<ns0:text x="620" y="120" text-anchor="middle" font-size="12" fill="#2563eb">+CF4</ns0:text>

<ns0:path d="M 200 130 Q 130 90 60 135" fill="none" stroke="#dc2626" stroke-width="1.5" marker-end="url(#arrow)" />

<ns0:path d="M 340 130 Q 200 60 60 135" fill="none" stroke="#dc2626" stroke-width="1.5" />

<ns0:path d="M 480 130 Q 270 45 60 135" fill="none" stroke="#dc2626" stroke-width="1.5" />

<ns0:path d="M 620 130 Q 340 30 60 135" fill="none" stroke="#dc2626" stroke-width="1.5" />

<ns0:text x="60" y="225" text-anchor="middle" font-size="12" fill="#dc2626">Discount Each CF Back to PV at Time 0</ns0:text>

<ns0:defs>

<ns0:marker id="arrow" markerWidth="8" markerHeight="8" refX="4" refY="4" orient="auto">

<ns0:path d="M0,0 L8,4 L0,8 Z" fill="#dc2626" />

</ns0:marker>

</ns0:defs>

</ns0:svg>

### Solving for Unknown Rate or Time

TVM formulas can be algebraically rearranged to solve for $i$ or $n$ when the other variables are known, though closed-form solutions for $i$ in annuity formulas generally require iterative (trial-and-error) or financial-calculator/spreadsheet methods rather than direct algebraic isolation.

**Solving for $n$ (single sum):**

$$n = \frac{\ln(FV/PV)}{\ln(1+i)}$$

**Example**: How long does it take $5,000 to grow to $10,000 at 7% annual interest?

$$n = \frac{\ln(10,000/5,000)}{\ln(1.07)} = \frac{\ln(2)}{\ln(1.07)} = \frac{0.6931}{0.0677} \approx 10.24 \text{ years}$$

This matches the well-known **Rule of 72** approximation, which estimates doubling time as $72 / i(\%)$: $72/7 \approx 10.3$ years, closely consistent with the precise calculation. [Inference: the Rule of 72 is a commonly cited approximation heuristic, not an exact formula; accuracy varies modestly with the interest rate used.]

### Application to Capital Budgeting

**Key Points**

- **Net Present Value (NPV)**: sums the present values of all project cash inflows and outflows at the firm's required rate of return (discount rate), directly applying the uneven-cash-flow PV technique above.
- **Internal Rate of Return (IRR)**: the discount rate at which a project's NPV equals zero — found by solving the PV equation for $i$ rather than for $PV$.
- **Payback and discounted payback**: discounted payback specifically incorporates TVM by discounting each period's cash flow before accumulating it toward recovery of the initial investment, unlike simple (undiscounted) payback.
- **Bond and lease valuation**: bond prices are the PV of coupon payments (an annuity) plus the PV of the face value (a single sum) — a direct combination of the two core TVM building blocks.
- **Equivalent Annual Annuity (EAA)/Equivalent Annual Cost (EAC)**: used to compare mutually exclusive projects with unequal lives by converting each project's NPV into an equivalent annuity, relying on the PV-of-annuity formula in reverse.

### Common Discount Rate Sources in Practice

**Key Points**

- **Weighted Average Cost of Capital (WACC)**: most commonly used as the discount rate for typical-risk capital projects
- **Risk-adjusted discount rate**: a higher rate applied to riskier projects to reflect additional required compensation for risk
- **Cost of debt or cost of equity individually**: used in specific valuation contexts (e.g., valuing a bond uses the market yield; valuing equity cash flows uses the cost of equity)

The choice of discount rate is a critical determinant of TVM-based valuations. Behavior of NPV and other TVM-based metrics may vary depending on which discount rate is selected, and the appropriateness of a given rate depends on project-specific risk characteristics that are outside the scope of the mechanical TVM formulas themselves.

### Related Topics

- Net Present Value (NPV) Method
- Internal Rate of Return (IRR) Method
- Payback Period and Discounted Payback Period
- Weighted Average Cost of Capital (WACC)
- Equivalent Annual Annuity/Cost for Unequal Project Lives
- Capital Rationing
- Sensitivity and Scenario Analysis in Capital Budgeting