## Calvo Pricing and Staggered Contracts


### Overview

Calvo pricing is a foundational modeling device in New Keynesian macroeconomics used to introduce **nominal price rigidity** into otherwise flexible-price general equilibrium models. Developed by Guillermo Calvo (1983), it provides a tractable, probabilistic alternative to earlier "time-dependent" staggered contract models (notably Taylor, 1979, 1980) for explaining why prices do not adjust instantaneously to nominal shocks, thereby giving monetary policy real effects in the short run.

### The Core Problem: Why Model Price Stickiness?

In a classical flexible-price economy, monetary shocks are neutral in the short run: a change in the money supply passes through immediately and proportionally into prices, leaving output and employment unaffected. Empirically, this is inconsistent with observed monetary non-neutrality — money shocks appear to have persistent real effects on output. New Keynesian models address this by introducing **nominal rigidities**, of which sticky prices are the primary mechanism, alongside sticky wages and information frictions.

**Key Points**

- Price stickiness breaks the classical dichotomy between nominal and real variables.
- It provides the microfoundation for a **New Keynesian Phillips Curve (NKPC)**, linking inflation to expected future inflation and real marginal cost.
- It is the central friction that gives central banks a lever to affect real output via nominal interest rate changes.

### Taylor's Staggered Contracts Model (Precursor)

Before Calvo, John Taylor (1979, 1980) modeled price/wage stickiness using **deterministic staggered contracts**:

- Firms are divided into cohorts, each of which resets its price (or wage) every $N$ periods, but not all cohorts reset simultaneously — contracts are staggered across time.
- At any point in time, only a fraction $1/N$ of firms adjust prices, while the rest keep prices fixed for the remaining duration of their contract.
- This staggering itself, even absent any single firm's stickiness, generates aggregate price-level inertia because economy-wide adjustment is spread over multiple periods.

**Limitation**: Taylor's model requires tracking a fixed, deterministic contract length $N$ for every firm, which introduces significant analytical and computational complexity, especially in models with many state variables. This complexity motivated a simpler alternative.

### The Calvo Pricing Mechanism

Calvo's (1983) key simplification replaces deterministic contract lengths with a **stochastic, memoryless reset probability**.

**Key Points**

- In each period, a firm faces a fixed probability $1-\theta$ of being allowed to reset its price, and a probability $\theta$ of being "stuck" — forced to keep its previous period's price unchanged.
- This reset opportunity arrives via a Poisson-like process independent of how long the firm has already held its current price (the process is memoryless).
- $\theta \in [0,1]$ is called the **Calvo parameter** or degree of price stickiness. A higher $\theta$ implies more firms are "stuck," hence greater aggregate price rigidity.
- The expected duration a price remains fixed is given by:

$$E[\text{duration}] = \frac{1}{1-\theta}$$

- Firms that do get to reset their price do not simply reset to the current period's frictionless optimal price; because they know they might be stuck with this price for many future periods, they set it as a forward-looking weighted average of expected future optimal prices.

### Diagram: Calvo Reset Mechanism (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 760 240">
\<style\>
.txt { font-family: Georgia, serif; font-size: 13px; fill: #222; }
.lbl { font-family: Georgia, serif; font-size: 11px; fill: #555; }
.box { fill: #f4f4f4; stroke: #333; stroke-width: 1.5; }
.stuck { fill: #ddd; stroke: #333; stroke-width: 1.5; }
\</style\>
<text x="10" y="20" class="lbl">Firm-Level Price Path Under Calvo Pricing (svg_diagram)</text>

<text x="10" y="55" class="txt">Firm A:</text>

<rect x="80" y="40" width="90" height="30" class="box" /><text x="95" y="60" class="txt">Reset</text>

<rect x="180" y="40" width="90" height="30" class="stuck" /><text x="195" y="60" class="txt">Stuck</text>

<rect x="280" y="40" width="90" height="30" class="stuck" /><text x="295" y="60" class="txt">Stuck</text>

<rect x="380" y="40" width="90" height="30" class="box" /><text x="395" y="60" class="txt">Reset</text>

<rect x="480" y="40" width="90" height="30" class="stuck" /><text x="495" y="60" class="txt">Stuck</text>

<text x="10" y="105" class="txt">Firm B:</text>

<rect x="80" y="90" width="90" height="30" class="stuck" /><text x="95" y="110" class="txt">Stuck</text>

<rect x="180" y="90" width="90" height="30" class="box" /><text x="195" y="110" class="txt">Reset</text>

<rect x="280" y="90" width="90" height="30" class="stuck" /><text x="295" y="110" class="txt">Stuck</text>

<rect x="380" y="90" width="90" height="30" class="stuck" /><text x="395" y="110" class="txt">Stuck</text>

<rect x="480" y="90" width="90" height="30" class="box" /><text x="495" y="110" class="txt">Reset</text>

<text x="10" y="155" class="txt">Firm C:</text>

<rect x="80" y="140" width="90" height="30" class="stuck" /><text x="95" y="160" class="txt">Stuck</text>

<rect x="180" y="140" width="90" height="30" class="stuck" /><text x="195" y="160" class="txt">Stuck</text>

<rect x="280" y="140" width="90" height="30" class="box" /><text x="295" y="160" class="txt">Reset</text>

<rect x="380" y="140" width="90" height="30" class="stuck" /><text x="395" y="160" class="txt">Stuck</text>

<rect x="480" y="140" width="90" height="30" class="stuck" /><text x="495" y="160" class="txt">Stuck</text>

<text x="10" y="195" class="lbl">Each period, each firm independently draws a reset opportunity with probability (1-θ),</text>

<text x="10" y="212" class="lbl">regardless of how long its current price has been in effect (memoryless property).</text>

</svg>

### Aggregate Price Level Under Calvo Pricing

Since only a random fraction $1-\theta$ of firms reset each period while the rest ($\theta$) retain last period's price, the aggregate price level is a weighted average:

$$P_t = \left[ \theta P_{t-1}^{1-\epsilon} + (1-\theta)(P_t^*)^{1-\epsilon} \right]^{\frac{1}{1-\epsilon}}$$

where $P_t^*$ is the optimal reset price chosen by adjusting firms in period $t$, and $\epsilon$ is the elasticity of substitution across differentiated goods.

### Deriving the New Keynesian Phillips Curve

A log-linear approximation around a zero-inflation steady state yields the standard **New Keynesian Phillips Curve (NKPC)**:

$$\pi_t = \beta E_t[\pi_{t+1}] + \kappa \hat{mc}_t$$

where:

- $\pi_t$ is inflation in period $t$
- $\beta$ is the household's subjective discount factor
- $\hat{mc}_t$ is the log-deviation of real marginal cost from its steady-state value
- $\kappa$ is a composite slope coefficient, typically expressed as:

$$\kappa = \frac{(1-\theta)(1-\beta\theta)}{\theta}$$

**Key Points**

- $\kappa$ is decreasing in $\theta$: greater price stickiness (higher $\theta$) flattens the Phillips Curve, meaning inflation responds less to changes in marginal cost/output gap.
- The forward-looking $E_t[\pi_{t+1}]$ term reflects that price-setters, when given the chance to reset, must forecast future economic conditions since they may be stuck with the chosen price for several periods.
- Under a common assumption that real marginal cost is proportional to the output gap, the NKPC is often rewritten as:

$$\pi_t = \beta E_t[\pi_{t+1}] + \kappa \tilde{y}_t$$

where $\tilde{y}_t$ is the output gap.

### Calvo vs. Taylor: Comparison

| Feature | Taylor Staggered Contracts | Calvo Pricing |
| --- | --- | --- |
| Contract length | Deterministic, fixed $N$ periods | Stochastic, geometric distribution |
| Tractability | Complex with many state variables | Highly tractable; single parameter $\theta$ |
| Reset timing | Known in advance | Random, memoryless |
| Aggregation | Requires tracking cohort vintages | Simple recursive aggregation |
| Realism | Mimics real-world fixed-length contracts | Abstracts from actual contract structure |

[Inference] Calvo pricing's popularity in the literature stems primarily from its analytical tractability rather than a claim that it more accurately describes firms' actual price-setting behavior; empirical microdata on price adjustment frequency (e.g., studies using CPI microdata) are generally used to calibrate $\theta$ rather than to validate the memoryless assumption itself.

### Calibration and Empirical Estimates

- $\theta$ is typically calibrated so that the implied average price duration matches empirical evidence on price-change frequency.
- Commonly cited calibrations in DSGE models set $\theta$ such that prices are fixed for approximately 4 quarters on average (implying $\theta \approx 0.75$), though this varies by study, sector, and time period.

[Unverified] Precise empirical values for $\theta$ vary substantially across studies (e.g., Bils and Klenow's microdata-based estimates versus earlier survey-based estimates), and figures should be checked against the specific empirical source being cited rather than treated as a single universally agreed-upon constant.

### Criticisms and Extensions

**Example**

- **Calvo-Yun model**: A common variant assumes that firms unable to optimally reset their price still partially index it to lagged or steady-state inflation, rather than leaving it perfectly unchanged — this generates inflation persistence absent in the pure Calvo model.
- **State-dependent pricing models** (e.g., menu cost models such as Golosov-Lucas) are an alternative class in which firms choose when to adjust prices based on the size of the gap between actual and optimal price, rather than via an exogenous random draw. These models can generate different, often more selective, aggregate adjustment dynamics than Calvo's time-dependent framework.
- Critics note that the Calvo model implies a constant hazard rate of price adjustment regardless of how long a price has been fixed, which is inconsistent with some empirical evidence suggesting adjustment hazards vary with price duration (a mixed and debated empirical literature).

### Role in DSGE and Monetary Policy Analysis

Calvo pricing is a standard building block in medium-scale **New Keynesian DSGE models** (e.g., the Smets-Wouters framework), where it interacts with:

- Sticky wages (an analogous Calvo mechanism applied to the labor market)
- Habit formation in consumption
- Investment adjustment costs
- Monetary policy rules (e.g., Taylor rules) that respond to the inflation and output gap generated by the NKPC

**Conclusion**

Calvo pricing provides the dominant tractable microfoundation for nominal price rigidity in modern New Keynesian models, replacing Taylor's deterministic staggered-contract framework with a simpler stochastic reset mechanism. Its central contribution is enabling closed-form derivation of the New Keynesian Phillips Curve, linking inflation dynamics to expected future inflation and real marginal cost, and thereby formalizing the channel through which monetary policy has real short-run effects.

**Related Topics**

- New Keynesian Phillips Curve (NKPC) derivation and micro-foundations
- Calvo-Yun model with partial indexation
- Menu cost models and state-dependent pricing (Golosov-Lucas)
- Sticky wages and the Erceg-Henderson-Levin framework
- Taylor rule and optimal monetary policy under sticky prices
- Smets-Wouters DSGE model
- Empirical estimation of price adjustment frequency (Bils-Klenow, Nakamura-Steinsson)
- Divine coincidence and the output gap-inflation trade-off