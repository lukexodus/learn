## Time Value of Money and Discounted Cash Flow Analysis


### Definition and Core Concept

The **time value of money (TVM)** is the foundational financial principle that a given sum of money available today is worth more than the same nominal sum available at a future date, because money available now can be invested to earn a return, is not subject to the risk of not being received at all, and (in most economic environments) tends to lose purchasing power over time due to inflation. **Discounted cash flow (DCF) analysis** is the systematic application of this principle to evaluate investment decisions, converting cash flows occurring at different points in time into a single common, comparable measure — typically their equivalent value at the present moment.

- TVM and DCF analysis form the analytical foundation for capital budgeting: without a method to make cash flows occurring at different times comparable, a decision-maker cannot meaningfully compare an investment's upfront cost against the stream of benefits it generates over subsequent years
- The **discount rate** used in DCF analysis reflects both the pure time value of money (what a risk-free dollar today is worth relative to a risk-free dollar in the future) and, in most practical applications, a premium for the risk associated with the specific cash flows being discounted

### Future Value and Present Value

**Key Points**

The two foundational calculations of TVM are **future value (FV)**, which projects a present sum forward in time at a given interest/growth rate, and **present value (PV)**, which is the inverse operation — expressing a future sum in terms of its equivalent value today.

**Future Value (single sum, compounded annually):**

$$FV = PV \times (1 + r)^n$$

where $PV$ is the present sum, $r$ is the periodic interest/discount rate, and $n$ is the number of periods.

**Present Value (single sum, discounted from the future):**

$$PV = \frac{FV}{(1 + r)^n}$$

**Numeric example:** $10,000 invested today at an annual rate of 8% for 5 years grows to:

$$FV = 10{,}000 \times (1.08)^5 = 10{,}000 \times 1.4693 \approx \$14{,}693$$

Conversely, $14,693 expected 5 years from now, discounted at 8% annually, has a present value of:

$$PV = \frac{14{,}693}{(1.08)^5} \approx \$10{,}000$$

confirming the FV and PV formulas are exact inverses of one another under the same rate and time horizon.

### Present Value of a Series of Cash Flows

Most real capital budgeting decisions involve multiple cash flows occurring across several future periods rather than a single sum. The present value of a **series of cash flows** is simply the sum of the present values of each individual cash flow:

$$PV = \sum_{t=1}^{n} \frac{CF_t}{(1+r)^t}$$

where $CF_t$ is the cash flow occurring at the end of period $t$.

**Numeric example:** A project generates cash flows of $5,000 (Year 1), $6,000 (Year 2), and $7,000 (Year 3), discounted at 10%:

$$PV = \frac{5{,}000}{(1.10)^1} + \frac{6{,}000}{(1.10)^2} + \frac{7{,}000}{(1.10)^3}$$



$$= 4{,}545.45 + 4{,}958.68 + 5{,}259.20 \approx \$14{,}763.33$$

### Present Value of an Annuity

**Key Points**

An **annuity** is a series of equal cash flows occurring at regular intervals over a fixed period — a common structure for loan payments, lease payments, and certain simplified project cash flow assumptions. The present value of an ordinary annuity (payments occurring at the *end* of each period) has a closed-form formula:

$$PV_{\text{annuity}} = CF \times \left[\frac{1 - (1+r)^{-n}}{r}\right]$$

where $CF$ is the constant periodic cash flow, $r$ is the periodic discount rate, and $n$ is the number of periods.

**Numeric example:** An annuity paying $8,000 per year for 6 years, discounted at 9%:

$$PV = 8{,}000 \times \left[\frac{1 - (1.09)^{-6}}{0.09}\right] = 8{,}000 \times \left[\frac{1 - 0.5963}{0.09}\right] = 8{,}000 \times 4.4859 \approx \$35{,}887$$

A **perpetuity** (an annuity with no end date, continuing indefinitely) has a further-simplified formula, $PV = CF / r$, used in certain specialized valuation contexts (such as some terminal value calculations), though this simplification requires the assumption of genuinely indefinite, constant cash flows, which is a strong assumption for most real projects. [Inference] The practical applicability of the perpetuity formula to any specific real valuation depends on how reasonable the indefinite-constant-cash-flow assumption is for that specific context.

### Diagrammatic Representation of Discounting

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 380" font-family="Arial, sans-serif">
<text x="400" y="24" text-anchor="middle" font-size="16" font-weight="bold">Discounting Future Cash Flows to Present Value (svg_diagram)</text>
<line x1="80" y1="320" x2="720" y2="320" stroke="black" stroke-width="1.5" />
<text x="670" y="340" font-size="12">Time (years)</text>

<line x1="150" y1="315" x2="150" y2="325" stroke="black" />
<text x="145" y="345" font-size="11">Year 0</text>
<line x1="300" y1="315" x2="300" y2="325" stroke="black" />
<text x="295" y="345" font-size="11">Year 1</text>
<line x1="450" y1="315" x2="450" y2="325" stroke="black" />
<text x="445" y="345" font-size="11">Year 2</text>
<line x1="600" y1="315" x2="600" y2="325" stroke="black" />
<text x="595" y="345" font-size="11">Year 3</text>

<rect x="285" y="270" width="30" height="50" fill="#16a34a" fill-opacity="0.5" />
<text x="270" y="260" font-size="10">CF1</text>
<rect x="435" y="250" width="30" height="70" fill="#16a34a" fill-opacity="0.5" />
<text x="420" y="240" font-size="10">CF2</text>
<rect x="585" y="230" width="30" height="90" fill="#16a34a" fill-opacity="0.5" />
<text x="570" y="220" font-size="10">CF3</text>

<path d="M 300 260 Q 220 180 155 130" fill="none" stroke="#2563eb" stroke-width="1.5" stroke-dasharray="4,2" marker-end="url(#arrow)" />
<path d="M 450 230 Q 300 130 155 110" fill="none" stroke="#dc2626" stroke-width="1.5" stroke-dasharray="4,2" />
<path d="M 600 210 Q 380 90 155 90" fill="none" stroke="#f97316" stroke-width="1.5" stroke-dasharray="4,2" />
<rect x="120" y="70" width="70" height="70" fill="#9333ea" fill-opacity="0.3" />
<text x="125" y="60" font-size="11" font-weight="bold">Sum = PV</text>

<text x="400" y="370" text-anchor="middle" font-size="11" font-style="italic">Each future cash flow is discounted back to Year 0 and summed to obtain total present value</text>

</svg>

### Compounding and Discounting Frequency

**Key Points**

- When interest or discounting occurs **more frequently than annually** (e.g., monthly, quarterly), the formulas above must be adjusted to reflect the periodic rate and the corresponding number of compounding periods: if $r$ is the stated *annual* rate compounded $m$ times per year over $t$ years, the future value formula becomes:

$$FV = PV \times \left(1 + \frac{r}{m}\right)^{mt}$$

- More frequent compounding at the same stated annual rate produces a higher effective annual return, since interest earned in earlier sub-periods itself begins earning interest sooner — this distinction between a stated ("nominal") annual rate and the **effective annual rate (EAR)** is important for correctly comparing financial instruments or loan terms that compound at different frequencies:

$$EAR = \left(1 + \frac{r}{m}\right)^{m} - 1$$

### The Discount Rate: What It Represents

**Key Points**

Selecting an appropriate discount rate is one of the most consequential and often most judgment-intensive steps in DCF analysis, since the discount rate typically reflects several distinct components bundled together:

- **Pure time preference / risk-free rate:** the baseline return required simply to compensate for delaying consumption or investment access, often approximated using a government bond yield of comparable maturity
- **Inflation expectations:** if cash flows are estimated in nominal terms, the discount rate should be a nominal rate incorporating expected inflation; if cash flows are estimated in real (inflation-adjusted) terms, a real discount rate (net of inflation) should be used instead — mismatching nominal cash flows with a real discount rate, or vice versa, is a common and consequential analytical error
- **Risk premium:** compensation for the uncertainty of the specific cash flows being discounted, connecting directly to the risk-attitude and risk-premium concepts covered under decision-making under risk — riskier projected cash flow streams generally warrant a higher discount rate (or, alternatively, a certainty-equivalent cash flow adjustment at the risk-free rate, as discussed under certainty equivalents)
- In corporate finance applications, the discount rate is frequently approximated using the firm's **weighted average cost of capital (WACC)**, reflecting the blended required return of the firm's debt and equity holders, though the appropriateness of using a single firm-wide WACC for a specific project depends on whether that project's risk profile is representative of the firm's overall risk profile [Inference]

### The Relationship Between DCF Analysis and Net Present Value

**Key Points**

Discounted cash flow analysis provides the essential computational machinery for **net present value (NPV)**, the standard capital budgeting decision criterion (treated as a related, more specialized topic in its own right):

$$NPV = \sum_{t=1}^{n} \frac{CF_t}{(1+r)^t} - \text{Initial Investment}$$

NPV simply extends the present-value-of-a-cash-flow-series calculation shown above by explicitly subtracting the upfront investment cost, producing a single figure representing the net wealth created (or destroyed) by undertaking the project, expressed in today's dollars. A positive NPV indicates the project's discounted benefits exceed its cost; a negative NPV indicates the reverse.

### Practical Applications

- **Example — loan and mortgage amortization:** Determining the periodic payment on a loan uses the present-value-of-annuity formula, solving for the constant $CF$ that makes the loan's present value equal to the amount borrowed
- **Example — capital equipment purchase decisions:** Comparing the total discounted cost of purchasing equipment (upfront cost) against the discounted value of leasing it over time (a stream of periodic lease payments), requiring both to be expressed in comparable present-value terms before a valid comparison can be made
- **Example — bond valuation:** A bond's price is the present value of its future coupon payments (an annuity) plus the present value of its final principal repayment (a single future sum), both discounted at the market's required yield
- **Example — comparing investment options with different time horizons:** DCF analysis, potentially combined with techniques such as equivalent annual annuity or common time-horizon adjustments, allows meaningful comparison of investment alternatives that generate cash flows over different numbers of years

### Common Pitfalls and Practical Limitations

- **Nominal/real mismatch:** Discounting nominal cash flows at a real discount rate (or the reverse) systematically distorts the resulting present value, and is one of the most common practical errors in applied DCF analysis
- **Discount rate selection sensitivity:** Because the discount rate appears in the denominator raised to increasingly large powers for cash flows further in the future, NPV and other DCF-based metrics can be highly sensitive to the specific discount rate chosen, particularly for long-lived projects — a consideration directly connecting to the importance of sensitivity analysis covered as a related topic
- **Terminal value and perpetuity assumption risk:** Valuations that rely on a terminal value calculated using the perpetuity formula implicitly assume cash flows continue indefinitely at a constant (or constantly growing) rate beyond the explicit forecast period — an assumption that should be scrutinized carefully rather than accepted as a default convenience, since terminal value often constitutes a large share of total estimated present value in long-horizon valuations [Inference]
- **Ignoring the reinvestment rate assumption implicit in compounding:** The standard FV/PV formulas implicitly assume that any interim cash flows are reinvested at the same rate $r$ used for discounting; if this assumption does not hold in a specific real context, the standard formulas may not accurately reflect the investor's actual achievable return [Inference]
- **Treating point-estimate cash flows as certain:** Basic DCF analysis, as presented here, uses single point-estimate cash flows for each future period; incorporating the genuine uncertainty of those future cash flows (via risk-adjusted discount rates, certainty equivalents, decision trees, or Monte Carlo simulation) is necessary for a fuller treatment of investment decisions under risk, as covered under the related topics in this chapter

### Related Topics

- Net present value and capital budgeting decision rules
- Internal rate of return and its limitations
- Certainty equivalents and risk premiums
- Weighted average cost of capital and risk-adjusted discount rates
- Payback period and other capital budgeting metrics
- Real options analysis in capital budgeting