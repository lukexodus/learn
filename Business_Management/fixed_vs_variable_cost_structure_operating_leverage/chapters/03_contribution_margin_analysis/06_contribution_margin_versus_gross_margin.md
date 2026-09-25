## Contribution Margin versus Gross Margin

### Definitions

**Contribution margin (CM)** is sales revenue minus *all variable costs* (manufacturing and non-manufacturing), regardless of whether those costs relate to production or to selling/administrative activity.

$$CM=Sales-VariableCosts_{total}$$

**Gross margin (gross profit)** is sales revenue minus *cost of goods sold (COGS)*, where COGS is a mix of both fixed and variable manufacturing costs under absorption costing.

$$GrossMargin=Sales-COGS$$

The two metrics classify costs along entirely different axes: CM classifies by **behavior** (fixed vs. variable); gross margin classifies by **function** (manufacturing/production vs. non-manufacturing).

### The Core Structural Difference

| Cost Category | Included in Variable Costs (→ affects CM) | Included in COGS (→ affects Gross Margin) |
| --- | --- | --- |
| Direct materials | Yes | Yes |
| Direct labor | Yes | Yes |
| Variable manufacturing overhead | Yes | Yes |
| **Fixed manufacturing overhead** | **No** | **Yes** |
| Variable selling expenses (e.g., commissions, shipping) | **Yes** | **No** |
| Fixed selling expenses | No | No |
| Variable administrative expenses | **Yes** | **No** |
| Fixed administrative expenses | No | No |

Two costs cause the two margins to diverge in opposite directions:

- **Fixed manufacturing overhead** is in COGS (lowers gross margin) but excluded from variable costs (does not lower CM) — this pulls gross margin *below* CM.
- **Variable selling/administrative costs** are excluded from COGS (do not lower gross margin) but included in variable costs (lower CM) — this pulls CM *below* gross margin.

The net direction of the gap between CM and gross margin depends on which effect dominates for a given company. [Inference: there is no universal rule for which margin is larger; it depends entirely on the relative size of fixed manufacturing overhead versus variable selling/admin costs in that company's specific cost structure.]

### Worked Example

Assume: Sales $400,000; Direct materials + labor + variable MOH $150,000; Fixed manufacturing overhead $60,000; Variable selling expenses $30,000; Fixed selling & admin $50,000.

**Gross Margin Calculation**

$$COGS=\$150{,}000+\$60{,}000=\$210{,}000$$



$$GrossMargin=\$400{,}000-\$210{,}000=\$190{,}000$$

**Contribution Margin Calculation**

$$VariableCosts_{total}=\$150{,}000+\$30{,}000=\$180{,}000$$



$$CM=\$400{,}000-\$180{,}000=\$220{,}000$$

**Example**

Here, CM ($220,000) exceeds gross margin ($190,000) by $30,000. This gap equals: fixed MOH excluded from CM's cost base (+$60,000 favorable to CM) minus variable selling expenses excluded from gross margin's cost base (−$30,000 favorable to gross margin) = net +$30,000 in favor of CM. Both figures are internally consistent; they simply answer different questions about the same underlying transactions.

### Visual: Where Each Margin Draws Its Line

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 360">
<text x="320" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Contribution Margin vs. Gross Margin: Cost Inclusion (svg_diagram)</text>

<text x="20" y="55" font-size="12" font-weight="bold" fill="`#1a1a1a`">Cost Category</text>

<text x="380" y="55" font-size="12" font-weight="bold" fill="`#1a1a1a`">→ Gross Margin</text>

<text x="510" y="55" font-size="12" font-weight="bold" fill="`#1a1a1a`">→ Contribution Margin</text>

<line x1="10" y1="65" x2="630" y2="65" stroke="#333" stroke-width="1" />

<text x="20" y="90" font-size="12" fill="`#1a1a1a`">Direct Materials / Labor</text>

<circle cx="410" cy="86" r="6" fill="`#5cb85c`" />

<circle cx="560" cy="86" r="6" fill="`#5cb85c`" />

<text x="20" y="120" font-size="12" fill="`#1a1a1a`">Variable Mfg. Overhead</text>

<circle cx="410" cy="116" r="6" fill="`#5cb85c`" />

<circle cx="560" cy="116" r="6" fill="`#5cb85c`" />

<text x="20" y="150" font-size="12" fill="`#c9302c`" font-weight="bold">Fixed Mfg. Overhead</text>

<circle cx="410" cy="146" r="6" fill="`#5cb85c`" />

<circle cx="560" cy="146" r="6" fill="#eee" stroke="#999" />

<text x="20" y="180" font-size="12" fill="`#e07b39`" font-weight="bold">Variable Selling/Admin</text>

<circle cx="410" cy="176" r="6" fill="#eee" stroke="#999" />

<circle cx="560" cy="176" r="6" fill="`#5cb85c`" />

<text x="20" y="210" font-size="12" fill="`#1a1a1a`">Fixed Selling/Admin</text>

<circle cx="410" cy="206" r="6" fill="#eee" stroke="#999" />

<circle cx="560" cy="206" r="6" fill="#eee" stroke="#999" />

<text x="20" y="250" font-size="11" fill="#555">Green = included in cost base (reduces the margin). Gray = excluded (does not reduce it).</text>

<text x="20" y="270" font-size="11" fill="#555">Red/orange labels mark the two costs that cause the margins to diverge.</text>

</svg>

### Practical Implications

**Key Points**

- **CM is the correct metric for CVP analysis, break-even, and volume-based profit forecasting**; gross margin is not, because it mixes fixed costs (which don't change with volume) into a per-unit-looking figure.
- **Gross margin is the correct metric for external reporting and cross-company comparability** under GAAP/IFRS; CM is a managerial construct with no standardized definition enforced across companies, which limits its comparability *between* companies (though it remains valid for internal period-over-period analysis).
- **A company with high fixed manufacturing overhead relative to variable selling costs** will typically show CM meaningfully higher than gross margin, since fixed MOH is excluded from CM's cost base. [Inference: this follows directly from the mechanics above but assumes variable selling/admin costs are not unusually large relative to fixed MOH for that company.]
- **A company with a commission-heavy, low-fixed-manufacturing-overhead cost structure** (e.g., certain service or distribution businesses) may show gross margin higher than CM, since variable selling costs are excluded from COGS but included in CM's cost base.

### Common Pitfalls

- **Using gross margin percentage in a break-even or target-profit formula** in place of CM ratio — this silently omits variable selling/admin costs from the "variable cost" side and includes fixed MOH, producing an incorrect break-even point.
- **Assuming gross margin and CM will always move in the same direction** when costs change — a change in fixed MOH allocation affects gross margin but not CM; a change in sales commission structure affects CM but not gross margin.
- **Comparing CM ratios across companies as if they were standardized** — unlike gross margin (built on GAAP-defined COGS), CM's variable/fixed cost split is an internal managerial judgment call and may not be computed identically across organizations.
- **Treating a rising gross margin as evidence of improving unit economics** without checking CM — gross margin can rise simply from producing more units (spreading fixed MOH over a larger base under absorption costing) even if underlying variable cost efficiency and CM per unit are unchanged.

### Related Topics

- The Contribution Margin Concept and Formula
- Variable Costing versus Absorption Costing
- The Contribution Margin Income Statement Format
- The Contribution Margin Ratio
- Cost-Volume-Profit (CVP) Analysis and the CVP Graph
- Segment Margin and Traceable vs. Common Fixed Costs