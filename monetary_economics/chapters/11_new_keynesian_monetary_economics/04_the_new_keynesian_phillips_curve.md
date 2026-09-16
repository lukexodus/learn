## The New Keynesian Phillips Curve


### Overview

The New Keynesian Phillips Curve (NKPC) is the core equation linking inflation dynamics to real economic activity in modern New Keynesian macroeconomic models. Unlike the original, purely empirical Phillips Curve, the NKPC is derived explicitly from microfoundations — optimizing, forward-looking firms operating under a nominal price rigidity (typically Calvo pricing) — making it a cornerstone of DSGE-based monetary policy analysis.

### From the Original Phillips Curve to the New Keynesian Version

**Key Points**

- The original Phillips Curve (Phillips, 1958) was a purely empirical, backward-looking relationship between wage inflation and unemployment, later reframed in terms of price inflation and the unemployment gap.
- The **expectations-augmented Phillips Curve** (Friedman, Phelps, late 1960s) added adaptive inflation expectations, implying no permanent trade-off between inflation and unemployment in the long run (only in the short run, and only if expectations are not fully rational).
- The **New Keynesian Phillips Curve** replaces backward-looking adaptive expectations with **rational, forward-looking expectations** and derives the relationship from an explicit firm optimization problem under sticky prices, rather than positing it as a reduced-form empirical regularity.

### Microfoundations: Deriving the NKPC

The NKPC is typically derived under the **Calvo pricing** framework (see related topic), in which a fraction $1-\theta$ of firms reset prices optimally each period while the remaining $\theta$ keep prices unchanged.

**Derivation Steps**

1. Each firm facing a reset opportunity chooses a price $P_t^*$ to maximize the present discounted value of expected profits, given that the price may remain fixed for several future periods.
2. This yields a firm-level optimal reset price that is a forward-looking weighted average of current and expected future nominal marginal costs.
3. Aggregating across all firms (using the Calvo aggregation rule for the price level) and log-linearizing around a zero-inflation steady state yields the reduced-form NKPC.

**The Standard (Purely Forward-Looking) NKPC:**

$$\pi_t = \beta E_t[\pi_{t+1}] + \kappa \hat{mc}_t$$

where:

- $\pi_t$ = inflation rate in period $t$
- $\beta \in (0,1)$ = household's subjective discount factor
- $E_t[\pi_{t+1}]$ = rational expectation of next period's inflation, formed using all available information at time $t$
- $\hat{mc}_t$ = log-deviation of real marginal cost from its steady-state value
- $\kappa$ = slope coefficient linking marginal cost to inflation, defined as:

$$\kappa = \frac{(1-\theta)(1-\beta\theta)}{\theta}$$

### Output Gap Formulation

Real marginal cost is often assumed to be proportional to the output gap (the deviation of output from its flexible-price, "natural" level), allowing the NKPC to be rewritten as:

$$\pi_t = \beta E_t[\pi_{t+1}] + \kappa \tilde{y}_t$$

where $\tilde{y}_t = y_t - y_t^n$ is the output gap.

**Key Points**

- This form directly parallels the traditional Phillips Curve's output-inflation trade-off, but is fully forward-looking rather than adaptive.
- The relationship between marginal cost and the output gap depends on the underlying labor market and production function assumptions (e.g., the elasticity of labor supply, decreasing returns to labor).

### Diagram: NKPC Transmission Mechanism (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 760 260">
\<style\>
.box { fill: #f4f4f4; stroke: #333; stroke-width: 1.5; }
.txt { font-family: Georgia, serif; font-size: 13px; fill: #222; }
.lbl { font-family: Georgia, serif; font-size: 11px; fill: #555; }
.arrow { stroke: #333; stroke-width: 1.5; marker-end: url(#arrow2); }
\</style\>
<text x="10" y="20" class="lbl">NKPC Transmission Chain (svg_diagram)</text>
<rect x="20" y="50" width="160" height="60" rx="6" class="box" />
<text x="35" y="75" class="txt">Monetary Policy</text>
<text x="35" y="93" class="txt">Shock (i_t)</text>
<line x1="180" y1="80" x2="230" y2="80" class="arrow" />
<rect x="230" y="50" width="160" height="60" rx="6" class="box" />
<text x="250" y="75" class="txt">Output Gap</text>
<text x="250" y="93" class="txt">(ỹ_t)</text>
<line x1="390" y1="80" x2="440" y2="80" class="arrow" />
<rect x="440" y="50" width="160" height="60" rx="6" class="box" />
<text x="455" y="75" class="txt">Real Marginal</text>
<text x="455" y="93" class="txt">Cost (mc_t)</text>
<line x1="600" y1="80" x2="650" y2="80" class="arrow" />
<rect x="650" y="50" width="100" height="60" rx="6" class="box" />
<text x="665" y="75" class="txt">Inflation</text>
<text x="670" y="93" class="txt">(π_t)</text>
<line x1="730" y1="110" x2="730" y2="150" stroke="#333" stroke-width="1.5" />
<line x1="730" y1="150" x2="120" y2="150" stroke="#333" stroke-width="1.5" marker-end="url(#arrow2)" />
<text x="250" y="145" class="lbl">Expected future inflation E_t[π_(t+1)] feeds back into current price-setting</text>

<text x="10" y="200" class="lbl">Forward-looking firms set prices based on expected future costs, not just current</text>

<text x="10" y="218" class="lbl">conditions — this is the key distinction from the traditional adaptive-expectations Phillips Curve.</text>

</svg>

### Solving the NKPC Forward

Because the NKPC is a forward-looking difference equation, it can be solved recursively by iterating forward, expressing current inflation as the present discounted value of all expected future marginal costs:

$$\pi_t = \kappa \sum_{k=0}^{\infty} \beta^k E_t[\hat{mc}_{t+k}]$$

**Key Points**

- This shows that current inflation depends on the entire expected future path of marginal cost/output gaps, not merely current conditions — a defining feature that distinguishes the NKPC from backward-looking Phillips Curve specifications.
- This forward-looking property implies inflation can respond immediately to news about future policy (a feature sometimes called the model's strong dependence on expectations management, relevant to forward guidance).

### Hybrid NKPC: Adding Inflation Persistence

The purely forward-looking NKPC has been criticized for failing to generate the **inflation persistence** and **hump-shaped output responses to monetary shocks** observed in the data. A common extension incorporates partial price indexation (e.g., Christiano-Eichenbaum-Evans, 2005; Galí-Gertler, 1999) to produce a **hybrid NKPC**:

$$\pi_t = \gamma_f E_t[\pi_{t+1}] + \gamma_b \pi_{t-1} + \kappa \hat{mc}_t$$

where $\gamma_f$ and $\gamma_b$ are the forward- and backward-looking weights (often summing to one under certain indexation assumptions), and $\pi_{t-1}$ is lagged inflation.

**Example**

- Under Calvo pricing with partial indexation to lagged inflation (rather than the pure Calvo assumption of no indexation for non-resetting firms), a fraction of firms mechanically update their price by last period's inflation rate even when they cannot fully re-optimize, generating the backward-looking term.

### Empirical Performance and the "Divine Coincidence"

**Key Points**

- Under the pure forward-looking NKPC combined with certain assumptions about the natural rate of output, stabilizing the output gap and stabilizing inflation become equivalent policy objectives — a result known as the **"divine coincidence"** (Blanchard-Galí, 2007).
- This coincidence breaks down once additional frictions (e.g., real wage rigidities, cost-push shocks) are introduced, reintroducing a genuine trade-off between output and inflation stabilization.
- The pure NKPC has faced substantial empirical criticism for its weak ability to match the observed **inertia** of inflation and the **lagged, hump-shaped response of inflation to identified monetary policy shocks** in VAR-based studies.

[Inference] The empirical shortcomings of the pure forward-looking NKPC (e.g., limited ability to generate inflation persistence) are relatively well-documented in the literature, but the appropriate fix (hybrid indexation, rule-of-thumb price setters, or alternative rational-inattention-based approaches) remains an active area of research without full consensus.

### NKPC and the Cost-Push Shock

To account for supply-side disturbances (e.g., oil price shocks) not captured by the output gap alone, the NKPC is frequently augmented with an exogenous **cost-push shock** term $u_t$:

$$\pi_t = \beta E_t[\pi_{t+1}] + \kappa \tilde{y}_t + u_t$$

**Key Points**

- $u_t$ represents disturbances to markups or marginal costs unrelated to the output gap (e.g., supply shocks, markup shocks).
- This term is central to the monetary policy trade-off literature, since it is the presence of $u_t$ that reintroduces a genuine short-run trade-off between stabilizing inflation and stabilizing the output gap, even under optimal policy.

### Role in Monetary Policy Analysis

The NKPC is one of three core equations in the canonical **New Keynesian three-equation model**, alongside:

1. The **dynamic IS curve** (derived from the household's consumption Euler equation)
2. A **monetary policy rule** (e.g., a Taylor rule or optimal policy under commitment/discretion)

Central banks and academic researchers use the NKPC to:

- Assess the trade-offs central banks face between inflation and output stabilization
- Evaluate the credibility and time-consistency of monetary policy rules
- Analyze the effects of forward guidance, given the model's reliance on expected future variables

### Conclusion

The New Keynesian Phillips Curve reformulates the classic inflation-output relationship on explicit microfoundations, deriving inflation dynamics from forward-looking, optimizing firms operating under nominal price rigidities such as Calvo pricing. While theoretically elegant and central to modern DSGE-based monetary policy analysis, its purely forward-looking form has faced persistent empirical challenges regarding inflation persistence, motivating hybrid specifications and ongoing research into more realistic price- and information-friction microfoundations.

**Related Topics**

- Calvo pricing and staggered contracts (microfoundation of the NKPC)
- Hybrid NKPC and inflation indexation (Christiano-Eichenbaum-Evans)
- The dynamic IS curve and the three-equation New Keynesian model
- Divine coincidence (Blanchard-Galí)
- Cost-push shocks and the inflation-output stabilization trade-off
- Taylor rules and optimal monetary policy under commitment vs. discretion
- Forward guidance and the forward-looking expectations channel
- Rational expectations vs. adaptive expectations in inflation dynamics