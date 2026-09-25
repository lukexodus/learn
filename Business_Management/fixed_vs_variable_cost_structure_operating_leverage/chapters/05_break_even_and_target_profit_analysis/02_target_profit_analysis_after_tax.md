## Target Profit Analysis After Tax

### Definition

After-tax target profit analysis solves for the sales volume (or revenue) required to achieve a specific *after-tax* net income goal. Because taxes are calculated on pre-tax operating income, an after-tax target must first be converted ("grossed up") to its pre-tax equivalent before it can be used in the standard CVP target profit formula.

### Why the Conversion Is Necessary

The CVP profit equation produces **pre-tax operating income** directly:

$$OperatingIncome_{pretax}=(Q\times CM_{unit})-FixedCosts$$

Net income (after-tax) is derived from pre-tax income by applying the tax rate:

$$NetIncome_{aftertax}=OperatingIncome_{pretax}\times(1-TaxRate)$$

If a manager states a goal in after-tax terms (e.g., "we need $70,000 in net income"), that figure cannot be substituted directly into the pre-tax CVP equation — doing so would understate the actual pre-tax profit (and therefore the volume) required, since it ignores the portion of pre-tax income that taxes will consume.

### The Gross-Up Formula

Solving the net income equation for the required pre-tax profit:

$$OperatingIncome_{pretax}=\frac{NetIncome_{aftertax}}{1-TaxRate}$$

This grossed-up pre-tax figure is then substituted into the standard target profit formula:

$$Q_{target}=\frac{FixedCosts+\left(\dfrac{NetIncome_{aftertax}}{1-TaxRate}\right)}{CM_{unit}}$$



$$Sales_{target}=\frac{FixedCosts+\left(\dfrac{NetIncome_{aftertax}}{1-TaxRate}\right)}{CM\%}$$

**Key Points**

- The term $1/(1-TaxRate)$ is the "gross-up factor" — at a 30% tax rate, this factor is $1/0.70\approx1.4286$, meaning $1 of after-tax profit requires roughly $1.43 of pre-tax profit.
- A higher tax rate requires a larger gross-up, meaning more pre-tax profit — and therefore more volume — is needed to deliver the same after-tax dollar result.
- Break-even itself is unaffected by taxes: at $OperatingIncome_{pretax}=0$, there is no tax liability (no income to tax), so break-even volume is identical whether computed pre-tax or "after-tax" — the tax effect only becomes relevant once a nonzero profit target enters the calculation. [Inference: this assumes a simplified tax model with no minimum tax, tax credits, or loss-carryforward provisions that could alter the relationship at exactly zero income; standard introductory CVP treatment assumes a flat tax rate applied only to positive income.]

### Worked Example

A company has $CM_{unit}=\$25$, Fixed Costs = $100,000, a tax rate of 25%, and wants **after-tax net income of $90,000**.

**Step 1 — Gross up the after-tax target to pre-tax:**

$$OperatingIncome_{pretax}=\frac{\$90{,}000}{1-0.25}=\frac{\$90{,}000}{0.75}=\$120{,}000$$

**Step 2 — Solve for target volume using the pre-tax figure:**

$$Q_{target}=\frac{\$100{,}000+\$120{,}000}{\$25}=\frac{\$220{,}000}{\$25}=8{,}800\ units$$

**Example**

Verification at 8,800 units:

- Contribution margin: $8{,}800\times\$25=\$220{,}000$
- Pre-tax operating income: $\$220{,}000-\$100{,}000=\$120{,}000$
- Tax expense: $\$120{,}000\times0.25=\$30{,}000$
- After-tax net income: $\$120{,}000-\$30{,}000=\$90{,}000$ ✓ (matches the target)

### Visual: The Gross-Up Conversion Path

```mermaid
flowchart LR
    A[After-Tax Net Income Target] --> B[Divide by (1 - Tax Rate)]
    B --> C[Pre-Tax Operating Income Required]
    C --> D[Add Fixed Costs]
    D --> E[Divide by CM per unit or CM Ratio]
    E --> F[Target Volume in Units or Sales Dollars]
```

### Sensitivity to the Tax Rate

The table below shows how the same $90,000 after-tax target requires different pre-tax income (and therefore different volume) at different tax rates, holding $CM_{unit}=\$25$ and Fixed Costs = $100,000 constant:

| Tax Rate | Gross-Up Factor | Pre-Tax Income Required | Target Volume |
| --- | --- | --- | --- |
| 15% | 1/0.85 ≈ 1.176 | $105,882 | 8,235 units |
| 25% | 1/0.75 ≈ 1.333 | $120,000 | 8,800 units |
| 35% | 1/0.65 ≈ 1.538 | $138,462 | 9,538 units |

**Key Points**

- As the tax rate rises, the volume required to hit the same after-tax dollar target increases — a higher tax rate means each unit's after-tax contribution to the target shrinks, even though $CM_{unit}$ (a pre-tax figure) is unchanged.
- This relationship is why after-tax profit goals are more sensitive to tax rate assumptions than pre-tax goals — a change in the assumed tax rate alone can shift the target volume by hundreds or thousands of units without any change to prices, costs, or fixed costs.
- Because the gross-up factor grows non-linearly as the tax rate approaches 100%, the volume increase required per percentage point of additional tax rate is larger at higher tax rates than at lower ones. [Inference: this follows mathematically from the $1/(1-TaxRate)$ form of the gross-up factor, which has an increasing derivative as $TaxRate$ increases; it is a direct property of the formula rather than an empirical claim.]

### Dollar-Sales Version Example

Using $CM\%=40\%$ (consistent with $CM_{unit}=\$25$ on a $62.50 price) and the same 25% tax rate and $90,000 after-tax target:

$$Sales_{target}=\frac{\$100{,}000+\$120{,}000}{0.40}=\frac{\$220{,}000}{0.40}=\$550{,}000$$

**Example**

Check: $8{,}800\ units\times$62.50/unit=$550{,}000$ — consistent with the unit-based answer, confirming both forms of the formula agree once the same grossed-up pre-tax figure is used.

### Common Pitfalls

- **Substituting the after-tax target directly into the standard target profit formula without grossing it up first** — this is the single most common error in after-tax CVP problems, and it understates the true volume required.
- **Applying the tax rate to fixed costs or to contribution margin directly**, rather than to the final pre-tax operating income figure — taxes apply to the *net* pre-tax profit, not to any intermediate line item in the CVP equation.
- **Using an average or blended effective tax rate inconsistently** — if a company's effective tax rate differs from its statutory rate (due to credits, deductions, or multi-jurisdictional effects), the rate used in the gross-up formula should match the rate actually expected to apply to the incremental income being targeted. [Unverified: the appropriate rate to use in a specific real-world scenario is a tax and financial-planning judgment call outside the scope of the CVP formula itself.]
- **Forgetting that break-even volume itself does not require gross-up** — only nonzero profit targets need the tax conversion; a break-even calculation should not have a tax adjustment applied to it.

### Related Topics

- Target Profit Analysis Before Tax
- The CVP Equation and Profit Function
- Break-Even Point in Units
- Margin of Safety
- Operating Leverage and the Degree of Operating Leverage (DOL)
- Sensitivity Analysis in CVP Modeling