## Target Profit Analysis Before Tax

### Definition

Target profit analysis extends break-even analysis by solving for the sales volume (or revenue) required to achieve a *specific pre-tax operating income goal*, rather than solving for the volume at which income equals exactly zero. Break-even is simply the special case of target profit analysis where the target is set to $0.

### Derivation from the Profit Equation

Starting from the CVP profit equation:

$$OperatingIncome=(Q\times CM_{unit})-FixedCosts$$

Instead of setting operating income to zero, set it equal to the desired pre-tax target profit and solve for $Q$:

$$TargetProfit_{pretax}=(Q\times CM_{unit})-FixedCosts$$



$$Q_{target}=\frac{FixedCosts+TargetProfit_{pretax}}{CM_{unit}}$$

The dollar-sales equivalent, using $CM\%$:

$$Sales_{target}=\frac{FixedCosts+TargetProfit_{pretax}}{CM\%}$$

**Key Points**

- The formula is structurally identical to the break-even formula, with the target profit simply added to fixed costs in the numerator — conceptually, the company must now recover fixed costs *and* generate the target profit amount from contribution margin.
- Because the numerator is larger than in the plain break-even formula, $Q_{target}$ is always greater than $Q^*$ (break-even) whenever the target profit is a positive number.
- The formula assumes the same CVP linearity and relevant-range conditions as break-even analysis (see CVP model assumptions and limitations) — it is not valid for volumes far outside the range where price and cost data were established.

### Worked Example

A company has $CM_{unit}=\$22$, Fixed Costs = $88,000, and wants to earn a pre-tax operating income of $44,000.

$$Q_{target}=\frac{\$88{,}000+\$44{,}000}{\$22}=\frac{\$132{,}000}{\$22}=6{,}000\ units$$

**Example**

Verification at 6,000 units:

- Contribution margin: $6{,}000\times\$22=\$132{,}000$
- Operating income: $\$132{,}000-\$88{,}000=\$44{,}000$ ✓ (matches the target)

Compare to break-even alone: $Q^*=\$88{,}000/\$22=4{,}000$ units. The additional 2,000 units above break-even ($6{,}000-4{,}000$) generate exactly the $44,000 target profit: $2{,}000\times\$22=\$44{,}000$ — confirming that every unit sold beyond break-even contributes its full $CM_{unit}$ directly to profit.

### Dollar-Sales Version Example

Using the same company's $CM\%=40\%$ (derived from $CM_{unit}=\$22$ on a $55 selling price, for illustration):

$$Sales_{target}=\frac{\$88{,}000+\$44{,}000}{0.40}=\frac{\$132{,}000}{0.40}=\$330{,}000$$

**Example**

Check: $6{,}000\ units\times$55/unit=$330{,}000$ — consistent with the unit-based answer above, as expected since both formulas derive from the same profit equation.

### Visual: Target Profit as an Extension of Break-Even

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 360">
<text x="320" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Break-Even vs. Target Profit Volume (svg_diagram)</text>
<line x1="80" y1="310" x2="600" y2="310" stroke="#333" stroke-width="1.5" />
<line x1="80" y1="40" x2="80" y2="310" stroke="#333" stroke-width="1.5" />
<text x="590" y="330" font-size="12" fill="#1a1a1a">Q (units)</text>
<text x="20" y="45" font-size="12" fill="#1a1a1a">$ Profit</text>
<line x1="80" y1="180" x2="600" y2="180" stroke="#ccc" stroke-dasharray="2,2" />
<line x1="80" y1="260" x2="600" y2="60" stroke="#4a90d9" stroke-width="2.5" />
<circle cx="280" cy="180" r="6" fill="#5cb85c" />
<text x="150" y="200" font-size="11" fill="#5cb85c">Break-Even (Q*): profit = $0</text>
<circle cx="440" cy="112" r="6" fill="#e07b39" />
<text x="450" y="105" font-size="11" fill="#e07b39">Target Profit Volume (Q_target)</text>
<line x1="440" y1="112" x2="440" y2="310" stroke="#999" stroke-dasharray="2,2" />
<line x1="80" y1="112" x2="440" y2="112" stroke="#999" stroke-dasharray="2,2" />
<text x="30" y="116" font-size="10" fill="#555">Target π</text>
<line x1="280" y1="180" x2="440" y2="180" stroke="#e07b39" stroke-width="1.5" marker-end="url(#arrow)" />
<text x="310" y="175" font-size="10" fill="#e07b39">Additional units = Target Profit / CM_unit</text>
</svg>

### Sensitivity of the Target Volume

**Key Points**

- **Raising the target profit** increases $Q_{target}$ proportionally by $\Delta TargetProfit/CM_{unit}$ additional units — identical in mechanism to how fixed cost increases affect break-even volume.
- **Improving $CM_{unit}$** (via price increases or variable cost reductions) *lowers* $Q_{target}$ for the same profit goal — fewer units are needed because each one contributes more.
- **Fixed cost increases** raise $Q_{target}$ by the same amount they would raise break-even volume ($\Delta FixedCosts/CM_{unit}$), since fixed costs and target profit enter the formula identically (both are added in the numerator).
- These sensitivities mean target profit volume can be hit through multiple independent levers — volume alone is not the only path to a profit goal; price, cost efficiency, and fixed cost management all shift $Q_{target}$ in predictable, calculable directions.

### Using Target Profit Analysis for Planning Decisions

**Example**

A manager is evaluating whether a new marketing initiative (cost: $15,000, a fixed cost) is worthwhile if it lets the company achieve its unchanged $44,000 profit target. The revised target volume becomes:

$$Q_{target,revised}=\frac{(\$88{,}000+\$15{,}000)+\$44{,}000}{\$22}=\frac{\$147{,}000}{\$22}\approx6{,}682\ units$$

This tells the manager the initiative must drive incremental sales of at least $6{,}682-6{,}000=682$ units beyond the original target to be worth its $15,000 fixed cost — converting a qualitative marketing decision into a concrete, testable volume threshold.

### Relationship to Break-Even (Special Case Check)

Setting $TargetProfit_{pretax}=0$ in the target profit formula collapses it exactly to the break-even formula:

$$Q_{target}\Big|_{TargetProfit=0}=\frac{FixedCosts+0}{CM_{unit}}=\frac{FixedCosts}{CM_{unit}}=Q^*$$

This confirms break-even analysis is not a separate technique but the zero-profit boundary case of the more general target profit framework.

### Common Pitfalls

- **Using an after-tax profit figure directly in the pre-tax formula** — this topic covers *pre-tax* target profit only; an after-tax target must first be grossed up by dividing by $(1-TaxRate)$ before being used here (see target profit analysis after tax).
- **Forgetting that $Q_{target}$ must be rounded up (not down) to a whole unit** when fractional results occur, since selling a fractional unit fewer than the calculated figure would fall short of the target profit.
- **Applying the formula outside the relevant range** validated for the fixed cost and $CM_{unit}$ figures used — a large target profit might imply a volume where step-fixed costs or price changes would actually apply (see CVP model assumptions and limitations).
- **Confusing target profit with target revenue** — the formula solves for the volume/revenue *required to achieve* a profit goal; it is not itself a revenue or sales target independent of the profit objective.

### Related Topics

- Break-Even Point in Units
- Target Profit Analysis After Tax
- The CVP Equation and Profit Function
- Margin of Safety
- Break-Even Point in Sales Dollars
- Operating Leverage and the Degree of Operating Leverage (DOL)