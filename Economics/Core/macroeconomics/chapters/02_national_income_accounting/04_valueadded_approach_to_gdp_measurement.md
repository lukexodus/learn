## Value-Added Approach to GDP Measurement

### Definition

The value-added approach (also called the production or output approach) measures GDP by summing the **value added** at each stage of production across all industries in the economy, rather than summing final expenditures or factor incomes. Value added at each stage is defined as:

$$\text{Value Added} = \text{Value of Output} - \text{Value of Intermediate Inputs}$$

By construction, summing value added across every firm and industry in the economy automatically avoids double-counting, since the cost of intermediate inputs purchased from other firms is subtracted out at each stage.

$$GDP = \sum_{i=1}^{n} \text{Value Added}_i$$

where the sum runs over all producing units $i$ in the economy.

### Key Points

- This approach measures GDP from the **production/supply side**, industry by industry (agriculture, manufacturing, services, etc.), making it the natural basis for computing each sector's contribution to GDP.
- It is the method used to construct **GDP by industrial origin** or **GDP by kind of economic activity**, a standard breakdown published by statistical agencies (e.g., Philippine PSA's Gross Value Added by industry).
- It is mathematically and conceptually equivalent to the expenditure and income approaches, since the total value added economy-wide must equal both total final expenditure and total factor income generated.
- The approach directly solves the double-counting problem inherent in a naive "sum of all transactions" measure, without needing to identify which goods are "final" versus "intermediate" at the point of sale — value added is calculated at every stage regardless of the good's ultimate use.

### Calculating Value Added: Worked Example

Consider a simplified three-stage production chain for bread:

| Stage | Producer | Output Sold | Sale Value | Cost of Intermediate Inputs | Value Added |
| --- | --- | --- | --- | --- | --- |
| 1 | Farmer | Wheat | $1.00 | $0.00 (assume no purchased inputs) | $1.00 |
| 2 | Miller | Flour | $2.50 | $1.00 (wheat) | $1.50 |
| 3 | Baker | Bread | $4.00 | $2.50 (flour) | $1.50 |
| **Total** |  |  | $7.50 |  | **$4.00** |

$$GDP_{contribution} = 1.00 + 1.50 + 1.50 = 4.00$$

This matches exactly the final-goods value of the bread ($4.00), confirming the equivalence between the "count only final goods" rule and the "sum value added at every stage" rule. The naive sum of all transactions ($7.50) is not GDP — it double- and triple-counts the wheat's value (embedded in flour) and the flour's value (embedded in bread).

### Why This Approach Is Necessary in Practice

In real economies, it is often difficult for a statistical agency to observe, at the point of sale, whether a given unit of output is a "final" good (purchased by an end user) or an "intermediate" good (purchased by another firm for further processing) — the same good (e.g., a ream of paper, a truck, a can of paint) can be either, depending on the buyer. The value-added method sidesteps this ambiguity entirely: it is applied uniformly to every firm and industry, deducting each firm's purchased inputs from its own sales/output, regardless of what the buyer intends to do with the firm's output.

### Value Added by Industrial Sector

National accounts conventionally decompose total value added into major industrial sectors, allowing analysis of each sector's contribution to GDP and to GDP growth:

- **Primary sector**: Agriculture, forestry, fishing, mining, and quarrying.
- **Secondary sector**: Manufacturing, construction, utilities (electricity, gas, water).
- **Tertiary sector**: Services (trade, transport, finance, real estate, public administration, and other services).

$$GDP = VA_{primary} + VA_{secondary} + VA_{tertiary}$$

[Inference] The precise industry classification system used (e.g., ISIC, NAICS, or a national equivalent like the Philippine Standard Industrial Classification) affects how granular this sectoral breakdown can be, and cross-country comparisons of sectoral GDP shares should account for classification differences.

### Illustrative Diagram: Value-Added Approach Structure

```mermaid
flowchart LR
    Farmer["Farmer<br/>Output: 1.00<br/>Inputs: 0.00<br/>VA: 1.00"] -->|sells wheat| Miller["Miller<br/>Output: 2.50<br/>Inputs: 1.00<br/>VA: 1.50"]
    Miller -->|sells flour| Baker["Baker<br/>Output: 4.00<br/>Inputs: 2.50<br/>VA: 1.50"]
    Baker -->|sells bread| Consumer[Final Consumer]

    Farmer -.VA 1.00.-> Sum["Sum of Value Added = GDP Contribution = 4.00"]
    Miller -.VA 1.50.-> Sum
    Baker -.VA 1.50.-> Sum
```

### Treatment of Government and Non-Market Output

For sectors without observable market sale prices — chiefly general government services and, in some accounting treatments, non-profit institutions serving households — value added cannot be measured as (output value − intermediate input cost) in the normal market sense, because there is no market sale of the output. Convention values the output of these sectors at **cost of production**:

$$VA_{government} \approx \text{Compensation of Government Employees} + \text{Consumption of Fixed Capital} + \text{Other Operating Costs} - \text{Intermediate Purchases}$$

This is a recognized simplification: it implicitly assumes that the value of a government service to society equals its production cost, with no separately measured "profit" or market-determined markup. [Inference] This convention is a long-standing feature of national accounting systems (e.g., the UN System of National Accounts) rather than a claim that government output should have zero economic profit; it exists because no better market-based alternative valuation is generally available.

### Reconciling with GDP at Market Prices

The sum of value added across all industries yields GDP at **basic prices** or **factor cost**. To reconcile with GDP at market prices (the figure reported in the expenditure approach), the same adjustment used in the income approach applies:

$$GDP_{market\ price} = \sum VA_i + \text{Net Indirect Taxes (Taxes on Products} - \text{Subsidies on Products)}$$

This is because value added at each production stage is typically measured net of the taxes/subsidies embedded specifically in that stage's output price, and these must be added back to match the market-price total used elsewhere in the accounts.

### Common Points of Confusion

- **Value added is not profit.** Value added includes wages, rent, interest, depreciation, and profit all together — it is the total new value created at that stage, which is then distributed among all factors of production involved (including labor), not just the residual claimed by the firm's owner.
- **A firm's "sales revenue" is not its value added.** Revenue must be reduced by the cost of purchased intermediate inputs (raw materials, components, purchased services) — but **not** by wages, rent, interest, or depreciation, since those are the very factor payments that value added is meant to fund.
- **Capital goods purchased by a firm from another firm are not "intermediate inputs" to be netted out.** A machine bought by a factory is treated as investment ($I$) in the expenditure approach and is *not* subtracted as an intermediate cost in the value-added calculation of the buying firm, since it is a final good in this context (a capital good, not embedded/consumed within the current period's output).
- **Inventory changes matter here too.** Value added includes goods produced but not yet sold in the current period (i.e., that year's addition to inventory), consistent with the expenditure approach's treatment of $\Delta \text{Inventories}$ within $I$.

### Relationship to Other Approaches

The value-added approach is the conceptual bridge that justifies the "final goods only" rule used in the expenditure approach and the "factor income" totals used in the income approach — all three are alternative but numerically equivalent ways of measuring the same underlying flow of production. In practice, national accounts often use the value-added/production approach as the primary basis for compiling GDP because it can be cross-checked industry by industry against firm-level output and input data, with the expenditure and income approaches serving as independent validation.

**Related Topics**

- Expenditure approach to GDP measurement
- Income approach to GDP measurement
- Gross Domestic Product concept and definition
- GDP by industrial origin / sectoral composition of GDP
- Intermediate goods vs. final goods vs. capital goods
- Gross Value Added (GVA) vs. GDP at market prices
- Input-output analysis and inter-industry linkages
- National Income, Personal Income, and Disposable Personal Income