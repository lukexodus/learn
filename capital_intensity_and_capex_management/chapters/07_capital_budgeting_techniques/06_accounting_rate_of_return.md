## Accounting Rate of Return

### Definition and Core Concept

The Accounting Rate of Return (ARR), also known as the Average Rate of Return or Return on Investment (ROI) in some contexts, is a capital budgeting metric that measures a project's expected profitability as a percentage of the investment, using accounting income rather than cash flows. Unlike NPV, IRR, or MIRR, ARR does not discount future values and relies on accrual-based net income figures drawn directly from financial statements, making it conceptually distinct from discounted cash flow techniques.

ARR is valued primarily for its simplicity and its direct linkage to accounting metrics that appear in financial statements and are already familiar to non-finance stakeholders, such as operating managers and boards accustomed to reviewing accounting-based performance measures.

### The Accounting Rate of Return Formula

$$ARR = \frac{Average\ Annual\ Accounting\ Profit}{Average\ Investment} \times 100\%$$

Alternative formulation using initial investment:

$$ARR = \frac{Average\ Annual\ Accounting\ Profit}{Initial\ Investment} \times 100\%$$

**Average investment**, when using the average-investment version of the formula, is typically calculated as:

$$Average\ Investment = \frac{Initial\ Investment + Salvage\ Value}{2}$$

This reflects the fact that the book value of a depreciating asset declines over its life, so the average capital tied up over the project's duration is lower than the initial outlay.

### Decision Rule

- **ARR > required/target rate of return (a management-set hurdle)**: Accept the project
- **ARR < required/target rate of return**: Reject the project
- When ranking mutually exclusive projects, the project with the **higher ARR** is generally preferred under this criterion

The target ARR threshold is typically set by management policy, often benchmarked against the firm's historical ROI, industry averages, or an internally desired accounting return, rather than derived directly from the firm's cost of capital.

### Step-by-Step Calculation Process

**Key Points**

- Forecast the project's net income (after depreciation and taxes) for each year of its useful life
- Calculate the average annual accounting profit across the project's life
- Determine the initial investment or average investment (accounting for salvage value if using the average-investment method)
- Divide average annual profit by the chosen investment base
- Compare the resulting percentage against the firm's target ARR threshold

### Worked Example

A company is evaluating equipment costing $400,000 with an estimated salvage value of $40,000 at the end of its 5-year useful life. Projected net income (after depreciation and taxes) for each year is as follows:

| Year | Net Income ($) |
| --- | --- |
| 1 | 48,000 |
| 2 | 55,000 |
| 3 | 62,000 |
| 4 | 58,000 |
| 5 | 50,000 |

**Step 1: Calculate average annual accounting profit**

$$Average\ Profit = \frac{48{,}000 + 55{,}000 + 62{,}000 + 58{,}000 + 50{,}000}{5} = \frac{273{,}000}{5} = 54{,}600$$

**Step 2: Calculate average investment**

$$Average\ Investment = \frac{400{,}000 + 40{,}000}{2} = \frac{440{,}000}{2} = 220{,}000$$

**Step 3: Calculate ARR**

$$ARR = \frac{54{,}600}{220{,}000} \times 100\% = 24.8\%$$

If the firm's target ARR threshold is, for example, 15%, this project (ARR = 24.8%) would be accepted under the ARR decision rule.

### Alternative Calculation Using Initial Investment

Using the initial investment base instead of average investment:

$$ARR = \frac{54{,}600}{400{,}000} \times 100\% = 13.65\%$$

Note that the choice of denominator (initial investment vs. average investment) materially changes the resulting ARR figure. This is a key source of inconsistency in ARR application, since firms may not apply the same convention uniformly across all project evaluations.

### ARR Calculation Flow

```mermaid
graph LR
    A["Forecast annual<br/>net income"] --> B["Calculate average<br/>annual profit"]
    B --> C["Determine investment base<br/>(initial or average)"]
    C --> D["ARR = Avg Profit / Investment Base"]
    D --> E["Compare against<br/>target ARR threshold"]
```

### Advantages of Accounting Rate of Return

- **Simplicity and ease of understanding**: does not require discounting, making it accessible to stakeholders without a finance background
- **Uses readily available accounting data**: draws directly from projected income statements, which are already prepared for other planning purposes
- **Consistency with performance measurement**: since many firms evaluate divisional or managerial performance using accounting-based ROI, ARR provides a capital budgeting metric that aligns with how project outcomes will later be measured and reported
- **Considers the entire project life**: unlike simple payback period, ARR incorporates profitability across the full duration of the project, not just the recovery period

### Limitations of Accounting Rate of Return

**Key Points**

- **Ignores the time value of money**: ARR does not discount future profits, treating income earned in year 1 the same as income earned in year 10
- **Relies on accounting profit rather than cash flow**: net income includes non-cash items (depreciation, amortization, accruals) and can be distorted by accounting policy choices (e.g., depreciation method, inventory valuation), whereas cash flow-based methods (NPV, IRR) better reflect actual economic value
- **No standardized definition**: different firms compute ARR using different profit measures (net income, operating income, EBIT) and different investment bases (initial vs. average investment), reducing comparability across organizations and even across projects within the same firm if conventions are applied inconsistently
- **Ignores cash flow timing**: two projects with identical average profit but very different profit distribution over time (e.g., front-loaded vs. back-loaded earnings) will show the same ARR despite having different true economic value
- **Target rate is arbitrary**: unlike IRR, which is compared against a theoretically grounded cost of capital, the ARR threshold is typically a management-chosen benchmark without a rigorous theoretical basis
- **Does not directly measure shareholder value creation**: a project can show an attractive ARR while generating a negative NPV, particularly if profits are concentrated in later years and discounting would meaningfully reduce their present value

### Accounting Rate of Return vs. Other Capital Budgeting Techniques

| Technique | Basis | Time Value of Money | Output Type | Primary Weakness |
| --- | --- | --- | --- | --- |
| ARR | Accounting profit | No | Percentage | Ignores TVM and cash flow timing |
| Payback Period | Cash flow | No (simple version) | Time | Ignores post-payback cash flows |
| NPV | Cash flow | Yes | Dollar value | Requires discount rate estimation |
| IRR | Cash flow | Yes | Percentage | Reinvestment assumption, multiple roots |
| MIRR | Cash flow | Yes | Percentage | Requires two rate assumptions |
| Profitability Index | Cash flow | Yes | Ratio | Can conflict with NPV ranking |

### Why ARR Diverges from Discounted Cash Flow Methods

Because ARR is based on accounting net income (which includes non-cash depreciation charges and follows accrual accounting conventions) rather than actual cash flows, and because it does not discount future amounts, ARR can produce conclusions that conflict with NPV, IRR, or MIRR for the same project. A project with strong early cash flows but modest accounting profits (due to heavy upfront depreciation) might show a low ARR despite a strong NPV, while a project with earnings concentrated in later years might show an attractive ARR despite a comparatively weaker NPV once those later profits are properly discounted.

[Inference] Because of this divergence, many corporate finance practitioners regard ARR as a secondary or supplementary metric — useful for aligning capital budgeting evaluation with subsequent accounting-based performance tracking — rather than as a primary investment decision tool, though the degree to which ARR is emphasized varies across industries and organizations.

### Application in Capital Intensity and Capex Management

In capital-intensive industries, ARR carries specific relevance and specific risks:

- **Depreciation method sensitivity**: Capital-intensive assets (plant, machinery, infrastructure) often use accelerated depreciation methods for tax purposes, which can significantly distort the ARR calculation depending on which depreciation basis (book vs. tax) is used in the profit forecast
- **Long asset lives amplify timing distortions**: Since ARR does not discount cash flows, capital-intensive projects with useful lives spanning 15–30 years are especially prone to ARR misrepresenting true economic value, since it treats profit earned in year 25 identically to profit earned in year 1
- **Alignment with performance reporting**: Capital-intensive firms that evaluate plant or divisional managers using accounting-based ROI metrics may use ARR in the initial capital budgeting stage specifically to ensure the projected project outcome aligns with how performance will later be measured and reported internally
- **Secondary role in formal capital allocation**: [Inference] Most capital-intensive organizations rely on NPV and IRR/MIRR as primary decision criteria for major capex commitments, with ARR serving a supporting role — particularly for smaller or lower-risk capital requests where the cost of a full discounted cash flow analysis may not be justified, though specific thresholds for when ARR alone suffices vary by company policy

### ARR vs. IRR Divergence Illustration (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 720 300">
<text x="360" y="26" font-family="Arial, sans-serif" font-size="17" font-weight="bold" text-anchor="middle" fill="#1a1a1a">ARR vs. IRR Divergence Illustration (svg_diagram)</text>

<text x="180" y="55" font-family="Arial" font-size="13" font-weight="bold" text-anchor="middle" fill="`#1a1a1a`">Project A: Back-loaded profits</text>

<line x1="60" y1="220" x2="330" y2="220" stroke="`#5f6368`" stroke-width="1.5" />

<rect x="80" y="200" width="30" height="20" fill="`#fbbc04`" />

<rect x="130" y="180" width="30" height="40" fill="`#fbbc04`" />

<rect x="180" y="150" width="30" height="70" fill="`#fbbc04`" />

<rect x="230" y="110" width="30" height="110" fill="`#fbbc04`" />

<rect x="280" y="70" width="30" height="150" fill="`#fbbc04`" />

<text x="195" y="245" font-family="Arial" font-size="11" text-anchor="middle" fill="`#5f6368`">High ARR, lower NPV</text>

<text x="540" y="55" font-family="Arial" font-size="13" font-weight="bold" text-anchor="middle" fill="`#1a1a1a`">Project B: Front-loaded profits</text>

<line x1="420" y1="220" x2="690" y2="220" stroke="`#5f6368`" stroke-width="1.5" />

<rect x="440" y="70" width="30" height="150" fill="`#34a853`" />

<rect x="490" y="110" width="30" height="110" fill="`#34a853`" />

<rect x="540" y="150" width="30" height="70" fill="`#34a853`" />

<rect x="590" y="180" width="30" height="40" fill="`#34a853`" />

<rect x="640" y="200" width="30" height="20" fill="`#34a853`" />

<text x="555" y="245" font-family="Arial" font-size="11" text-anchor="middle" fill="`#5f6368`">Same avg. ARR, higher NPV</text>

<text x="360" y="280" font-family="Arial" font-size="11" text-anchor="middle" fill="`#5f6368`">Identical average profit, but timing differences produce different NPV/IRR — ARR cannot distinguish them</text>

</svg>

### Best Practice Recommendation

1. Use ARR only as a supplementary metric alongside NPV and IRR/MIRR, never as the sole basis for a major capital investment decision
2. Standardize the ARR formula (profit measure and investment base) consistently across all projects within the organization to preserve comparability
3. Be explicit about which depreciation method and profit definition underlie the ARR calculation when presenting results to stakeholders
4. Recognize that ARR is most defensible for smaller, low-risk, or short-lived capital requests where the cost and complexity of full discounted cash flow analysis may not be proportionate to the decision's significance

### Related Topics

- Net Present Value (NPV) analysis
- Internal Rate of Return (IRR) and its limitations
- Modified Internal Rate of Return (MIRR)
- Payback period and discounted payback period
- Depreciation methods and their effect on accounting profit
- Return on Investment (ROI) as a performance measurement tool
- Divisional performance evaluation and capital budgeting alignment
- Cash flow forecasting vs. accrual accounting in project evaluation