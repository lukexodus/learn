## Weighted Average Cost of Capital


### Overview

The Weighted Average Cost of Capital (WACC) represents the blended, overall rate of return a firm must earn on its investments to satisfy all of its capital providers — debt holders, preferred shareholders, and common equity holders — in proportion to each source's share of the firm's total capital structure. WACC serves as the standard discount rate for evaluating projects and cash flows of average risk relative to the firm's existing operations, and it is the single most widely used discount rate in corporate valuation, capital budgeting, and financial decision-making.

### Core Formula

$$WACC = w_d \times r_d(1-T) + w_p \times r_p + w_e \times r_e$$

Where:

- $w_d$ = proportion of debt in the capital structure (at market value)
- $r_d$ = pre-tax cost of debt
- $T$ = marginal tax rate
- $w_p$ = proportion of preferred stock in the capital structure
- $r_p$ = cost of preferred stock
- $w_e$ = proportion of common equity in the capital structure
- $r_e$ = cost of common equity

The weights must sum to 1.0:

$$w_d + w_p + w_e = 1$$

### Determining Capital Structure Weights

**Market Value, Not Book Value**

Weights should be based on the **market value** of each capital component, not book (accounting) value, because WACC represents the current opportunity cost of capital as priced by today's market participants, not historical accounting costs.

$$w_d = \frac{MV_{debt}}{MV_{debt} + MV_{preferred} + MV_{equity}}$$



$$w_e = \frac{MV_{equity}}{MV_{debt} + MV_{preferred} + MV_{equity}}$$



$$w_p = \frac{MV_{preferred}}{MV_{debt} + MV_{preferred} + MV_{equity}}$$

**Estimating Market Values in Practice**

- **Market value of equity**: Current share price multiplied by shares outstanding (market capitalization) — always observable for publicly traded firms.
- **Market value of debt**: Ideally the current trading price of outstanding bonds multiplied by face value outstanding; if debt is not publicly traded (e.g., bank loans), book value is commonly used as a practical proxy, particularly when interest rates have not moved dramatically since the debt was issued.
- **Market value of preferred stock**: Current share price multiplied by shares outstanding, if publicly traded.

**Key Points**

- Using book value weights when market values are available and diverge significantly (common when a firm's equity has appreciated substantially, or when interest rates have shifted materially since debt issuance) will produce a distorted WACC.
- For a firm with a rapidly rising stock price, using book value equity weights will overstate the debt weight and understate the equity weight, typically understating the true WACC, since equity is generally more expensive than debt.
- Target (long-run intended) capital structure weights, rather than current weights, are sometimes used instead — particularly when a firm's current capital structure is considered temporarily unrepresentative of its long-term financing policy (e.g., immediately following a large debt-funded acquisition, or during a period of unusually depressed equity market pricing).

### Comprehensive Worked Example

A firm has the following capital structure and cost estimates:

- Common shares outstanding: 10 million, current price $45/share
- Preferred shares outstanding: 500,000, current price $80/share
- Debt: Book value $300 million, market value (based on YTM analysis) $310 million
- Cost of debt (pre-tax, from YTM): 6.0%
- Cost of preferred stock: 7.5%
- Cost of equity (from CAPM): 11.5%
- Marginal tax rate: 25%

**Step 1 — Compute market values of each component**

$$MV_{equity} = 10{,}000{,}000 \times 45 = 450{,}000{,}000$$



$$MV_{preferred} = 500{,}000 \times 80 = 40{,}000{,}000$$



$$MV_{debt} = 310{,}000{,}000$$

**Step 2 — Compute total capital and weights**

$$Total = 450{,}000{,}000 + 40{,}000{,}000 + 310{,}000{,}000 = 800{,}000{,}000$$



$$w_e = \frac{450{,}000{,}000}{800{,}000{,}000} = 0.5625$$



$$w_p = \frac{40{,}000{,}000}{800{,}000{,}000} = 0.0500$$



$$w_d = \frac{310{,}000{,}000}{800{,}000{,}000} = 0.3875$$

**Step 3 — Apply the after-tax cost of debt**

$$r_d(1-T) = 6.0\% \times (1 - 0.25) = 6.0\% \times 0.75 = 4.50\%$$

**Step 4 — Compute WACC**

$$WACC = (0.3875 \times 4.50\%) + (0.0500 \times 7.5\%) + (0.5625 \times 11.5\%)$$



$$WACC = 1.7438\% + 0.3750\% + 6.4688\% = 8.5875\% \approx 8.59\%$$

This 8.59% represents the minimum return the firm's overall asset base must generate, on average, to satisfy all three classes of capital providers.

### Marginal WACC vs. Historical/Average WACC

**Key Points**

- WACC should conceptually represent the **marginal** cost of raising the *next* dollar of capital, not necessarily the average cost of capital already raised historically, since capital budgeting decisions involve new financing at current market rates.
- As a firm raises progressively larger amounts of new capital, its marginal cost of capital can rise (e.g., due to flotation costs kicking in beyond internally generated funds, or due to credit spread widening as leverage increases) — this is captured in the concept of the **Marginal Cost of Capital (MCC) schedule**, which plots WACC as an increasing step function against the total amount of new capital raised.
- For most standard capital budgeting applications, a single "current" WACC computed from prevailing market weights and costs is used as a reasonable approximation of marginal cost of capital, unless the firm anticipates raising unusually large amounts of capital relative to its existing size.

### When WACC Should NOT Be Used

WACC is only the appropriate discount rate for projects of **similar risk** to the firm's existing overall operations and **similar financing mix** to the firm's target capital structure. It should not be applied indiscriminately to every project a firm considers.

**Key Points**

- A project in a different business line or industry than the firm's core operations carries different systematic risk, and should be discounted using a risk-adjusted rate reflecting that project's own risk (often estimated via the pure-play or comparable-company beta method), not the firm's blended WACC.
- Applying a single firm-wide WACC to all projects regardless of risk creates a systematic bias: it causes the firm to **over-invest in high-risk projects** (since their true required return exceeds the applied WACC) and **under-invest in low-risk projects** (since their true required return is below the applied WACC) — a classic capital budgeting pitfall.
- Divisional or project-specific costs of capital are the correct remedy when a firm operates multiple business segments with materially different risk profiles.

### Flotation Costs and WACC

When new capital is being raised specifically to fund a project, flotation costs are sometimes incorporated. Two common treatment methods exist:

**Method 1 — Adjust the Cost of Capital Component**

Increase the cost of the specific capital source (as shown in the cost of preferred stock and cost of equity topics) to reflect flotation costs, then use this adjusted cost within the standard WACC formula.

**Method 2 — Adjust the Initial Investment (Preferred by Most Modern Practitioners)**

Treat flotation costs as an upfront cash outflow added directly to the project's initial investment, rather than embedding them in the discount rate.

$$Adjusted\ Initial\ Investment = Initial\ Investment + Flotation\ Costs$$

[Inference] Method 2 is generally considered more theoretically sound because flotation costs are a one-time cash outflow rather than a permanent, recurring increase to the cost of capital, and embedding a one-time cost into a perpetual discount rate (Method 1) can distort the valuation of a project's later-year cash flows; however, both methods appear in practice and in various academic treatments.

### Sensitivity of NPV to WACC Estimation Errors

**Key Points**

- Because WACC compounds over the life of a multi-year project, even small estimation errors in WACC (e.g., 50-100 basis points) can produce economically significant swings in a project's NPV, particularly for long-lived projects with cash flows concentrated in later years.
- This sensitivity is a primary reason capital budgeting practice often pairs a WACC-based NPV calculation with the sensitivity and scenario analysis techniques covered separately, explicitly testing how NPV and the accept/reject decision change across a plausible range of WACC estimates.

### Process Flow Diagram

```mermaid
flowchart TD
    A[Identify All Capital Structure Components: Debt, Preferred, Equity] --> B[Estimate Market Value of Each Component]
    B --> C[Compute Capital Structure Weights: wd, wp, we]
    D[Estimate Cost of Debt via YTM or Rating Approach] --> E[Apply Tax Shield: rd x 1-T]
    F[Estimate Cost of Preferred Stock: Dp/P0] --> G[No Tax Adjustment]
    H[Estimate Cost of Equity via CAPM or DGM] --> I[No Tax Adjustment]
    C --> J[Combine: WACC = wd x rd(1-T) + wp x rp + we x re]
    E --> J
    G --> J
    I --> J
    J --> K{Is Project Risk Similar to Firm's Overall Risk?}
    K -->|Yes| L[Use Firm WACC as Discount Rate]
    K -->|No| M[Use Project-Specific or Divisional Cost of Capital Instead]
```

### Common Errors to Avoid

**Key Points**

- Using book value weights instead of market value weights, particularly for equity, where the divergence from book value is often substantial.
- Forgetting to apply the tax shield to the cost of debt component while correctly leaving preferred stock and equity components untaxed.
- Applying a single company-wide WACC to a project with materially different risk than the firm's core business (e.g., a manufacturing firm evaluating a technology startup investment).
- Confusing the marginal cost of raising new capital with the historical, sunk cost of capital already raised — WACC-based capital budgeting decisions should be forward-looking.
- Mixing nominal and real costs of capital, or mixing costs of capital estimated in different currencies, inconsistently with the cash flows being discounted (see inflation-adjusted capital budgeting for the related consistency principle).

### Related Topics

- Cost of debt estimation
- Cost of preferred stock
- Cost of equity using CAPM and dividend growth approaches
- Marginal cost of capital schedule and the investment opportunity schedule
- Divisional and project-specific costs of capital; pure-play beta method
- Optimal capital structure and Modigliani-Miller propositions
- Inflation adjusted capital budgeting
- Sensitivity, scenario, and break-even analysis
- Flotation cost treatment in capital budgeting