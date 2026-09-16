## Nonlinear Budget Constraints and Taxation


### Why Budget Constraints Become Nonlinear

The basic labor-leisure model assumes a linear budget constraint $C = wh + V$, implying a single, constant effective wage across all hours levels. In practice, tax and transfer systems make the *effective* (after-tax, after-transfer) wage vary with hours or earnings, because marginal tax rates change across income brackets, transfer programs phase in and out, and payroll tax caps or program eligibility thresholds create discrete jumps. The result is a **piecewise-linear** (or, with continuously graduated schedules, smoothly nonlinear) budget constraint in consumption-hours space, with **kinks** (changes in slope) and sometimes **notches** (discrete drops in the constraint) at specific hours or earnings levels.

### Kinks vs. Notches

- **Kink**: a point where the marginal net-of-tax wage changes discontinuously but *total* after-tax income remains continuous — e.g., crossing into a higher income tax bracket, where only income above the threshold is taxed at the higher rate, so the budget constraint's slope changes but does not jump.
- **Notch**: a point where total after-tax income itself drops discontinuously as earnings cross a threshold — e.g., a benefit that is fully lost (rather than gradually phased out) once income exceeds an eligibility cutoff, creating a segment of the budget constraint where earning slightly more actually leaves the individual strictly worse off in total consumption.

Notches generate stronger and more mechanically predictable behavioral responses than kinks, since any individual whose earnings would fall in the region just past a notch has a first-order incentive to reduce earnings back to exactly the notch point (avoiding the discontinuous loss entirely) — producing a theoretically predicted "missing mass" or hole in the earnings distribution just above the notch, with corresponding excess mass ("bunching") exactly at the notch.

### Standard Piecewise-Linear Tax Budget Constraint

Under a progressive marginal tax schedule with rates $t_1 < t_2 < \ldots < t_K$ applying to successive income brackets $[0, y_1), [y_1, y_2), \ldots$, the after-tax budget constraint is:

$$C = wh - T(wh) + V$$

where $T(\cdot)$ is the tax liability function, piecewise linear in pre-tax earnings $wh$, with the constraint's slope in each segment equal to $w(1-t_k)$ — the **net-of-tax wage** relevant to the marginal hour worked within that bracket. Because only the marginal tax rate on the last dollar earned matters for the marginal work-hours decision, while *both* the marginal rate and the average/inframarginal rates matter for the income effect (via total disposable income), the labor supply response to a progressive tax schedule cannot be summarized by the marginal rate alone.

### Convex vs. Non-Convex Budget Sets

- **Convex kinks** (e.g., standard progressive marginal tax brackets, where the net wage *decreases* at higher earnings) generate a **bunching prediction**: individuals whose interior optimum would fall exactly at the kink under smooth preferences will instead cluster (bunch) precisely at the kink point across a range of underlying preference heterogeneity, since the kink creates a range of relative prices (between the two adjoining slopes) at which the kink itself is optimal for many different indifference curve shapes.
- **Non-convex regions** (e.g., a benefit phase-out region combined with a phase-in EITC-style credit, or the interaction of multiple overlapping transfer programs) can create a **non-convex budget set** — where the set of feasible (hours, consumption) combinations is not convex — potentially generating multiple local optima and making some segments of the hours distribution theoretically undesirable for any well-behaved preferences, producing "holes" in the predicted hours distribution independent of the notch/bunching-at-a-point logic described above.

### The Earned Income Tax Credit as a Multi-Segment Example

The EITC schedule illustrates a realistic multi-kink nonlinear budget constraint with three distinct regions:

1. **Phase-in region**: the credit increases with earnings (a wage subsidy), so the effective net wage *exceeds* the market wage — creating a strong positive substitution-effect incentive to increase hours/earnings, particularly relevant to the extensive margin (entering the labor force at all).
2. **Plateau region**: the credit is constant across a range of earnings, so the effective marginal net wage in this region equals the market wage (net of any ordinary payroll/income tax), with no credit-driven marginal distortion.
3. **Phase-out region**: the credit declines with additional earnings, functioning as an *implicit marginal tax* on top of any ordinary income tax — creating a standard negative substitution-effect incentive (reduce hours) alongside a negative income effect (from the overall loss of credit value), so both effects point toward reduced hours in this segment, unlike the ambiguous-sign case of a simple wage increase.

```mermaid
graph LR
    A["Phase-In: Net Wage above Market Wage"] --> B["Plateau: Net Wage = Market Wage, Credit Constant"]
    B --> C["Phase-Out: Net Wage below Market Wage, Implicit Marginal Tax"]
    A -->|"Substitution effect: encourages entry/hours"| D["Predicted Bunching Effects at Kinks"]
    C -->|"Substitution AND income effects both reduce hours"| D
```

### Bunching Estimators

The theoretical prediction that a convex kink generates excess mass ("bunching") in the earnings distribution exactly at the kink point underlies the **bunching estimator** methodology (Saez, 2010) for recovering labor supply elasticities directly from the observed shape of the earnings distribution around a known kink, without requiring cross-sectional or panel wage variation:

$$e = \frac{\Delta h / h}{\Delta(1-t)/(1-t)}$$

estimated by comparing the observed excess mass at the kink to a counterfactual earnings density (typically estimated by fitting a smooth distribution to the earnings density away from the kink and extrapolating through the kink region). Bunching estimators have become a standard complementary tool to reduced-form quasi-experimental approaches in the tax-and-labor-supply literature, particularly valuable because they exploit variation in the tax schedule itself (which is often invariant across observed reform episodes for some parts of the income distribution) rather than requiring an actual policy change to generate identifying variation.

### Notches and the "Missing Mass" Prediction

Kleven and Waseem (2013) formalized the notch analog of the bunching estimator, showing that a notch produces both excess bunching *at* the notch and a corresponding "missing mass" — a range of earnings just above the notch that is entirely avoided — with the size of this missing-mass region providing an alternative, and under some conditions more informative, source of elasticity identification than kink-based bunching alone, since notches generate a first-order (rather than the kink's second-order) behavioral response.

### Implications for Empirical Labor Supply Estimation

Because most real-world tax and transfer systems generate genuinely nonlinear, non-convex budget sets, structural labor supply estimation (see: Structural Estimation of Labor Market Models) typically must explicitly model the full piecewise-linear or kinked constraint — using techniques such as the **discrete choice hours model** (treating hours as chosen from a finite menu of discrete options rather than a continuous margin, partly to sidestep the full complexity of optimizing over a non-convex continuous constraint) — rather than assuming a single linear wage as in the introductory labor-leisure model.

### Key Points

- Real-world tax and transfer systems generate piecewise-linear or non-convex budget constraints via kinks (slope changes) and notches (discrete drops in total income), departing from the introductory model's linear constraint.
- Convex kinks generate a theoretically predicted bunching pattern in the earnings distribution; notches generate both bunching and a "missing mass" region of avoided earnings.
- The EITC's three-region structure (phase-in, plateau, phase-out) illustrates how substitution and income effects combine differently across segments of a single realistic nonlinear constraint.
- Bunching estimators exploit these predicted distributional patterns to recover labor supply elasticities directly from cross-sectional earnings data, without requiring an observed tax reform.

**Related Topics**

- The Saez Bunching Estimator: Methodology and Assumptions
- Kleven-Waseem Notch Analysis and Missing Mass
- Discrete Choice Hours Models for Non-Convex Budget Sets
- The EITC's Effects Across Phase-In, Plateau, and Phase-Out Regions
- Optimal Marginal Tax Rates and the Elasticity of Taxable Income