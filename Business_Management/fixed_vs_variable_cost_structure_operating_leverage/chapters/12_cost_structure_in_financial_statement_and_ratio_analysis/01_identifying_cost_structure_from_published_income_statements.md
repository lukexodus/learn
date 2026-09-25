## Identifying Cost Structure from Published Income Statements


### Conceptual Foundation

Published financial statements — prepared under standard accounting frameworks such as GAAP or IFRS — do not directly disclose which costs are fixed and which are variable. Income statements are organized by function (e.g., cost of goods sold, selling expenses, general and administrative expenses) or by nature (e.g., depreciation, salaries, materials), not by cost behavior relative to volume. This creates a genuine analytical challenge: an external analyst seeking to estimate a firm's operating leverage, breakeven point, or cost structure must infer fixed-versus-variable classification from limited, imperfect external disclosures, using a combination of statement format knowledge, statistical techniques, and industry judgment.

**Key Points**

- Standard income statement formats (multi-step, by nature) do not label costs as fixed or variable — this must be inferred by the analyst.
- Historical financial data across multiple periods allows statistical estimation of the fixed-variable split, most commonly via regression or the high-low method applied to reported cost and revenue data.
- Industry knowledge and business model understanding are essential complements to statistical technique, since reported cost categories often blend fixed and variable elements (mixed/semi-variable costs).
- The reliability of externally-derived cost structure estimates is inherently lower than internally-available cost accounting data, and should be treated with appropriate caution regarding precision.

---

### Income Statement Formats and What They Reveal

**Multi-step income statement (functional classification):**

$$\text{Revenue} - \text{COGS} = \text{Gross Profit}$$



$$\text{Gross Profit} - \text{Operating Expenses (SG\&A, R\&D)} = \text{Operating Income (EBIT)}$$

This format groups costs by business function rather than by cost behavior. COGS often contains a mix of variable costs (direct materials, direct labor tied to production) and some fixed elements (factory overhead allocated into COGS under absorption costing). Operating expenses (SG&A) similarly blend fixed elements (salaried administrative staff, base rent) with variable elements (sales commissions, some marketing spend).

**Single-step income statement:** groups all revenues together and all expenses together, providing even less functional detail than the multi-step format, making cost structure inference more difficult without supplementary disclosure.

**Segment reporting (where available):** larger public companies often disclose segment-level revenue and operating income, which can provide a partial view into the cost structure of distinct business lines — though even segment disclosures typically do not separate fixed from variable costs explicitly.

---

### Statistical Approaches to Estimating Fixed and Variable Costs

**1. High-Low Method**

Using the highest and lowest activity (typically revenue or unit volume) periods from historical data, and their associated total cost:

$$V = \frac{\text{Cost}_{high} - \text{Cost}_{low}}{\text{Activity}_{high} - \text{Activity}_{low}}$$



$$F = \text{Cost}_{high} - V \times \text{Activity}_{high}$$

**Worked Example:**

An analyst examines a company's reported total operating expenses across eight quarters, identifying the highest and lowest revenue quarters:

|  | High Quarter | Low Quarter |
| --- | --- | --- |
| Revenue | $12,000,000 | $7,500,000 |
| Total operating expenses | $8,400,000 | $6,150,000 |

$$V = \frac{8{,}400{,}000 - 6{,}150{,}000}{12{,}000{,}000 - 7{,}500{,}000} = \frac{2{,}250{,}000}{4{,}500{,}000} = 0.50$$

This suggests variable operating expenses run at approximately 50% of revenue.

$$F = 8{,}400{,}000 - (0.50 \times 12{,}000{,}000) = 8{,}400{,}000 - 6{,}000{,}000 = \$2{,}400{,}000$$

**Interpretation:** the high-low method estimates fixed operating expenses of approximately $2,400,000 per quarter, with variable expenses running at roughly 50% of revenue. **Key limitation:** this method relies on only two data points, making it highly sensitive to whether those two periods are representative of normal cost behavior, or whether either period contained unusual, non-recurring items that would distort the estimate.

**2. Regression Analysis**

A more statistically robust approach regresses total cost against a chosen activity measure (typically revenue, or units sold if disclosed) across all available historical periods:

$$\text{Total Cost} = a + b \times \text{Activity}$$

Where the regression intercept ($a$) estimates fixed cost and the slope coefficient ($b$) estimates variable cost per unit of activity. Using all available data points (rather than just the two extremes used in the high-low method) generally produces a more reliable estimate, and the regression's R-squared statistic provides a useful indication of how well a simple linear fixed-variable model actually fits the observed cost behavior — a low R-squared would signal that the assumed linear cost structure is a poor approximation of actual cost behavior, warranting caution in relying on the resulting estimates.

**Practical consideration:** regression requires enough historical periods (typically a minimum of 8-12 quarters, more preferred) to produce statistically meaningful estimates, and assumes the underlying cost structure has been reasonably stable over the period examined — a structural change (e.g., a major automation investment, entry into a new business line) partway through the sample period would distort the regression estimate unless explicitly accounted for. [Inference: minimum sample size guidance is a general statistical practice consideration rather than a fixed rule, and the appropriate sample size depends on the specific data's variability and the precision required]

---

### Complementary Qualitative Approaches

Because statistical techniques applied to aggregated, externally-reported data have inherent limitations, analysts typically supplement them with qualitative business model understanding:

1. **Industry benchmarking.** Comparing a firm's estimated cost structure against known characteristics of its industry (e.g., recognizing that an airline should exhibit high fixed costs per the general pattern established under airline and transportation cost structures) provides a sanity check against statistically-derived estimates.
2. **Notes to financial statements.** Depreciation and amortization schedules, lease commitment disclosures (particularly under current lease accounting standards requiring most operating leases to be recognized on the balance sheet), and segment disclosures can provide direct evidence of the scale of certain fixed cost categories, supplementing the indirect statistical inference.
3. **Management commentary (MD&A).** Management's discussion and analysis sections often provide qualitative or even quantitative commentary on cost drivers, capacity utilization, or the fixed/variable nature of specific cost lines, which can corroborate or refine statistical estimates.
4. **Understanding the business model.** A qualitative understanding of how the company generates revenue (e.g., subscription-based recurring revenue vs. per-unit product sales vs. project-based billing) provides essential context for interpreting which reported cost categories are likely to behave as fixed versus variable, informing which statistical results are plausible.

---

### Comparative Summary of Estimation Approaches

| Approach | Data Requirement | Strengths | Limitations |
| --- | --- | --- | --- |
| High-low method | Two data points (highest/lowest activity periods) | Simple, quick to apply | Highly sensitive to whether the two chosen periods are representative; ignores all other available data |
| Regression analysis | Multiple periods (ideally 8-12+) | Uses all available data; provides goodness-of-fit statistic (R-squared) | Assumes linear cost behavior and structural stability over the sample period; requires sufficient historical data |
| Industry benchmarking | Qualitative industry knowledge | Provides plausibility check; useful when limited company-specific data is available | Individual company cost structure can deviate meaningfully from industry norms |
| Notes/MD&A review | Access to full financial statement disclosures | Provides some direct, non-inferred evidence (e.g., depreciation schedules) | Disclosures are rarely granular enough to fully resolve the fixed/variable split on their own |

---

### Practical Workflow for External Analysts

1. **Gather historical quarterly or annual data** for revenue and relevant cost line items across as many periods as available and reasonably comparable (i.e., without major structural business changes mid-sample).
2. **Apply regression analysis** as the primary quantitative technique, using the high-low method only as a supplementary sanity check or when insufficient data exists for meaningful regression.
3. **Review the regression's goodness of fit** (R-squared) to assess whether a simple linear fixed-variable model is a reasonable approximation of the actual cost behavior observed.
4. **Cross-reference with qualitative disclosures** (notes, MD&A, segment reporting) and industry knowledge to sanity-check the statistical results against what is known about the company's business model and industry.
5. **Apply appropriate caution in the resulting DOL, breakeven, or leverage estimates**, recognizing that externally-derived cost structure estimates carry meaningfully more uncertainty than internally-available management accounting data, and should generally be presented as approximate ranges rather than precise point estimates. [Inference]

---

### Diagram: External Cost Structure Estimation Workflow (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 760 380" font-family="Arial, sans-serif">
<text x="380" y="26" text-anchor="middle" font-size="17" font-weight="bold">Estimating Cost Structure from Published Statements (svg_diagram)</text>
<line x1="80" y1="340" x2="700" y2="340" stroke="black" stroke-width="2" />
<line x1="80" y1="340" x2="80" y2="60" stroke="black" stroke-width="2" />
<text x="390" y="365" text-anchor="middle" font-size="13">Revenue (Activity Measure)</text>
<text x="30" y="200" text-anchor="middle" font-size="13" transform="rotate(-90 30 200)">Total Reported Cost</text>

<circle cx="150" cy="290" r="4" fill="#3498db" />
<circle cx="200" cy="270" r="4" fill="#3498db" />
<circle cx="280" cy="240" r="4" fill="#3498db" />
<circle cx="340" cy="220" r="4" fill="#3498db" />
<circle cx="410" cy="190" r="4" fill="#3498db" />
<circle cx="480" cy="165" r="4" fill="#3498db" />
<circle cx="560" cy="130" r="4" fill="#3498db" />
<circle cx="630" cy="105" r="4" fill="#3498db" />

<line x1="80" y1="315" x2="700" y2="80" stroke="#c0392b" stroke-width="2" stroke-dasharray="6,3" />
<text x="600" y="95" font-size="12" fill="#c0392b">Fitted regression line</text>

<text x="90" y="330" font-size="11" fill="#555">Intercept ≈ Fixed Cost (F)</text>

<text x="500" y="340" text-anchor="start" font-size="11" fill="#555">Slope ≈ Variable Cost Rate (V)</text>

</svg>

---

### Analytical Workflow

```mermaid
flowchart TD
    A["Gather historical revenue and cost data
    across multiple comparable periods"] --> B{Sufficient periods available
    for regression (8-12+)?}
    B -->|Yes| C["Run regression: Total Cost = a + b x Revenue"]
    B -->|No| D["Apply high-low method as
    a lower-confidence alternative"]
    C --> E["Review R-squared for
    goodness of fit"]
    D --> E
    E --> F["Cross-reference with notes,
    MD&A, and segment disclosures"]
    F --> G["Compare against industry
    benchmark expectations"]
    G --> H["Derive approximate DOL/breakeven
    estimates with appropriate
    uncertainty caveats"]
```

---

### Common Analytical Pitfalls

- **Treating externally-derived fixed/variable estimates as precise**, when in reality they are approximations subject to meaningful estimation error, especially when based on limited historical data or a low-R-squared regression fit.
- **Ignoring structural changes within the sample period** (mergers, divestitures, major automation or outsourcing initiatives) that would invalidate the assumption of a stable, linear cost structure across the entire historical window used for estimation.
- **Relying solely on the high-low method** when sufficient data exists for a more robust regression approach, discarding potentially valuable information from the periods not selected as the extremes.
- **Failing to cross-check statistical results against industry and business model knowledge**, potentially accepting an implausible fixed-variable split that a basic qualitative sanity check would have flagged as inconsistent with the company's known business model. [Inference]

---

### Related Topics

- Degree of Operating Leverage (DOL) — formula and derivation
- High-low method and regression-based cost estimation techniques
- Flexible Budgeting and Cost Structure (a related application of fixed/variable cost separation)
- Industry-specific cost structure archetypes (manufacturing, airlines, SaaS, retail, professional services)
- Lease accounting standards and their effect on fixed cost visibility in financial statements
- Segment reporting analysis and its use in external financial analysis
- Financial statement analysis and ratio interpretation more broadly