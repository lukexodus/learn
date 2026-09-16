## Modigliani-Miller Propositions With Taxes

### Definition and Conceptual Overview

In their 1963 follow-up paper "Corporate Income Taxes and the Cost of Capital: A Correction," Modigliani and Miller relaxed the no-tax assumption of their original 1958 framework to incorporate corporate income taxes. This revision produces a starkly different conclusion: **because interest expense is tax-deductible while dividend and equity payments are not, debt financing creates a genuine tax shield that increases total firm value.** Under this model, capital structure is no longer irrelevant — firm value rises monotonically with leverage, implying (in the model's own unrealistic extreme) that firms should be financed almost entirely with debt.

This creates the famous tension in capital structure theory: the with-tax M&M model predicts ever-increasing value from leverage, a conclusion clearly at odds with observed corporate behavior, motivating the later trade-off theory that reintroduces bankruptcy and financial distress costs as a counterweight.

### The Interest Tax Shield

**Key Points**

- Interest payments on debt are deductible from taxable income, reducing the firm's tax liability.
- This tax savings is called the **interest tax shield** and represents a cash flow that would not exist for an all-equity (unlevered) firm.
- The interest tax shield effectively transfers value from the government (in the form of reduced tax collection) to the firm's security holders (debt and equity combined).

**Annual Interest Tax Shield**

$$\text{Annual Tax Shield} = T \times r_d \times D$$

where:

- $T$ = corporate tax rate
- $r_d$ = cost of debt (interest rate)
- $D$ = market value of debt

### Proposition I (M&M I with Taxes): Value of the Levered Firm

**Statement**: The value of a levered firm equals the value of an otherwise identical unlevered firm plus the present value of the interest tax shield.

$$V_L = V_U + TD$$

where:

- $V_L$ = value of the levered firm
- $V_U$ = value of the unlevered (all-equity) firm
- $T$ = corporate tax rate
- $D$ = market value of debt (assumed permanent/perpetual in the standard derivation)

**Derivation Logic**: If debt is assumed to be permanent (perpetual, constant level, never repaid, refinanced indefinitely), the interest tax shield itself becomes a perpetuity. Discounting this perpetual tax shield at the cost of debt $r_d$ (reflecting the tax shield's risk, which is tied to the certainty of interest payments) gives:

$$PV(\text{Tax Shield}) = \dfrac{T \times r_d \times D}{r_d} = TD$$

This elegant simplification — the discount rate $r_d$ cancels out — is why the tax shield's present value reduces to simply $T \times D$, the tax rate multiplied by the face/market value of debt, under the perpetual debt assumption.

**Example**

An unlevered firm has a value $V_U = \$50{,}000{,}000$. It is considering recapitalizing by issuing $20,000,000 in permanent debt (using proceeds to repurchase equity). The corporate tax rate is 25%.

$$V_L = 50{,}000{,}000 + (0.25)(20{,}000{,}000) = 50{,}000{,}000 + 5{,}000{,}000 = \$55{,}000{,}000$$

The firm's value increases by $5,000,000 — the present value of the interest tax shield — simply by adding debt to its capital structure, with total invested capital (assets and operations) unchanged.

### Firm Value as a Function of Leverage

```mermaid
flowchart LR
    A["Unlevered Firm Value: V_U"] --> B["Add Debt: D"]
    B --> C["Interest Tax Shield: T x r_d x D"]
    C --> D["PV of Perpetual Tax Shield: T x D"]
    D --> E["Levered Firm Value: V_L = V_U + T x D"]
```

### Graphical Representation of M&M I with Taxes

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 400">
<text x="320" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Firm Value vs. Leverage — With Taxes (svg_diagram)</text>
<line x1="80" y1="340" x2="600" y2="340" stroke="#333" stroke-width="2" />
<line x1="80" y1="340" x2="80" y2="50" stroke="#333" stroke-width="2" />
<text x="340" y="375" text-anchor="middle" font-size="13" fill="#333">Amount of Debt (D)</text>
<text x="30" y="195" text-anchor="middle" font-size="13" fill="#333" transform="rotate(-90 30,195)">Firm Value ($)</text>
<line x1="80" y1="300" x2="600" y2="300" stroke="#999" stroke-width="1.5" stroke-dasharray="5,4" />
<text x="590" y="290" text-anchor="end" font-size="11" fill="#666">V_U (unlevered value)</text>
<line x1="80" y1="300" x2="580" y2="90" stroke="#2563eb" stroke-width="3" />
<text x="500" y="120" text-anchor="middle" font-size="12" fill="#1e40af">V_L = V_U + T·D</text>
<line x1="300" y1="300" x2="300" y2="210" stroke="#16a34a" stroke-width="1.5" stroke-dasharray="3,3" />
<text x="380" y="255" text-anchor="middle" font-size="11" fill="#166534">PV(Tax Shield) = T x D</text>
<circle cx="80" cy="300" r="4" fill="#333" />
<text x="90" y="320" font-size="11" fill="#333">D = 0: V_L = V_U</text>
</svg>

### Proposition II (M&M II with Taxes): Cost of Equity

**Statement**: The cost of equity still rises with leverage, but at a *slower rate* than in the no-tax case, because the tax deductibility of interest dampens the amplification of financial risk passed to equity holders.

$$r_e = r_U + (r_U - r_d)(1-T)\dfrac{D}{E}$$

where the $(1-T)$ term is the key modification relative to the no-tax version of M&M II.

**Example**

An unlevered firm has $r_U = 12\%$, considering debt at $r_d = 7\%$, with $D/E = 1.0$, and $T = 25\%$.

$$r_e = 12\% + (12\% - 7\%)(1 - 0.25)(1.0) = 12\% + (5\%)(0.75)(1.0) = 12\% + 3.75\% = 15.75\%$$

Compare this to the no-tax case, which would yield $r_e = 12\% + 5\% = 17\%$. The tax adjustment reduces the equity risk premium from leverage, since bondholders (and the tax shield) absorb part of the effective risk that would otherwise fall fully on equity.

### WACC Declines With Leverage (With Taxes)

**Key Points**

- Unlike the no-tax case (where WACC is constant at $r_U$ regardless of leverage), under the with-tax M&M model, **WACC declines as leverage increases**, because the after-tax cost of debt is cheaper than equity, and this benefit is not fully offset by the rising cost of equity.
- This declining WACC is mathematically consistent with the rising $V_L = V_U + TD$ relationship — more debt means lower WACC means higher firm value (for a given, unchanged expected cash flow stream).

$$WACC = \dfrac{E}{V}r_e + \dfrac{D}{V}r_d(1-T)$$

**Example — Continuing the Prior Example**

With $D/E = 1.0$: $D = E$, so $w_d = w_e = 50\%$.

$$WACC = 0.50(15.75\%) + 0.50(7\%)(1-0.25) = 7.875\% + 0.50(5.25\%) = 7.875\% + 2.625\% = 10.50\%$$

This is below $r_U = 12\%$, confirming WACC falls below the unlevered cost of capital once the tax shield is introduced — the mechanism by which increasing leverage increases $V_L$.

### WACC and Firm Value Relationship

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 380">
<text x="320" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">WACC vs. Leverage — With Taxes (svg_diagram)</text>
<line x1="80" y1="320" x2="600" y2="320" stroke="#333" stroke-width="2" />
<line x1="80" y1="320" x2="80" y2="50" stroke="#333" stroke-width="2" />
<text x="340" y="355" text-anchor="middle" font-size="13" fill="#333">Debt-to-Equity Ratio (D/E)</text>
<text x="30" y="185" text-anchor="middle" font-size="13" fill="#333" transform="rotate(-90 30,185)">Rate (%)</text>
<line x1="80" y1="200" x2="600" y2="80" stroke="#2563eb" stroke-width="2.5" />
<text x="590" y="70" text-anchor="end" font-size="12" fill="#1e40af">r_e (rises, slower slope than no-tax case)</text>
<line x1="80" y1="200" x2="600" y2="130" stroke="#16a34a" stroke-width="2.5" stroke-dasharray="7,4" />
<text x="590" y="145" text-anchor="end" font-size="12" fill="#166534">WACC (declines with leverage)</text>
<line x1="80" y1="290" x2="600" y2="290" stroke="#ca8a04" stroke-width="2" stroke-dasharray="5,3" />
<text x="590" y="280" text-anchor="end" font-size="11" fill="#854d0e">r_d(1-T) (after-tax cost of debt)</text>
</svg>

### The Extreme Implication and Its Critique

**Key Points**

- Taken to its logical extreme, $V_L = V_U + TD$ implies firm value is maximized at nearly 100% debt financing — the more debt, the higher the value, with no offsetting cost within the model.
- This prediction is not observed empirically; most firms maintain moderate, not extreme, leverage ratios.
- The theoretical resolution is the introduction of **costs of financial distress and bankruptcy** (direct costs like legal/administrative fees, and indirect costs like lost customers, suppliers, and employees due to perceived instability), which rise at an increasing rate as leverage increases and eventually offset the tax shield benefit — this extension is known as the **static trade-off theory** of capital structure. [Inference — this is the standard next step presented in essentially all corporate finance curricula following the with-tax M&M model, though the precise functional form of distress costs is a modeling choice rather than an empirically settled formula]
- Personal taxes (on interest income vs. dividend/capital gains income) were later incorporated by Miller (1977) in a further refinement, which can partially offset the corporate-level tax advantage of debt depending on relative personal tax rates on different income types. [Unverified — the exact quantitative offset depends on prevailing personal tax rates, which vary by jurisdiction and over time]

### Comparison: No-Tax vs. With-Tax M&M

| Aspect | M&M I (No Taxes) | M&M I (With Taxes) |
| --- | --- | --- |
| Firm value | $V_L = V_U$ | $V_L = V_U + TD$ |
| Optimal capital structure | Irrelevant (any mix works) | Implies maximum debt (before real-world frictions) |
| Cost of equity | $r_e = r_U + (r_U-r_d)(D/E)$ | $r_e = r_U + (r_U-r_d)(1-T)(D/E)$ |
| WACC | Constant at $r_U$ | Declines as leverage increases |
| Key mechanism | Arbitrage/homemade leverage | Interest tax deductibility |

### Practical Formula Summary

| Concept | Formula |
| --- | --- |
| M&M Proposition I (with taxes) | $V_L = V_U + TD$ |
| PV of perpetual interest tax shield | $TD$ |
| Annual interest tax shield | $T \times r_d \times D$ |
| M&M Proposition II (with taxes) | $r_e = r_U + (r_U - r_d)(1-T)(D/E)$ |
| WACC (with taxes) | $WACC = w_e r_e + w_d r_d(1-T)$ |

### Related Topics

- Modigliani-Miller Propositions without taxes (the no-tax baseline)
- Static trade-off theory of capital structure (balancing tax shields against distress costs)
- Costs of financial distress and bankruptcy (direct and indirect)
- Miller's (1977) model incorporating personal taxes
- Pecking order theory and asymmetric information
- Agency cost theory of capital structure
- Adjusted Present Value (APV) method, which explicitly separates base-case NPV from the value of financing side-effects like the tax shield