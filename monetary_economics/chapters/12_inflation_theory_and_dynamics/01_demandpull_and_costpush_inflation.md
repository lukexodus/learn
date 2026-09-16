## Demand-Pull and Cost-Push Inflation


### Overview

Demand-pull and cost-push inflation represent the two classical causal categories used to explain sustained increases in the general price level. This distinction, originating in the Keynesian and post-Keynesian traditions, remains a standard organizing framework in monetary economics for diagnosing the source of inflationary pressure and for determining the appropriate policy response, even as modern New Keynesian models formalize both channels within a unified aggregate supply-demand structure.

### Demand-Pull Inflation

**Definition**: Demand-pull inflation occurs when aggregate demand for goods and services grows faster than the economy's productive capacity to supply them, "pulling" prices upward as excess demand bids up prices in a supply-constrained environment.

**Key Points**

- Arises when the economy is operating at or near full employment / potential output, so that further increases in aggregate demand cannot be met by increased output alone and instead spill over into higher prices.
- Commonly summarized by the phrase "too much money chasing too few goods."
- Consistent with the quantity theory of money's prediction that, once real output is at its capacity constraint, growth in the money supply beyond that needed to accommodate real growth translates into inflation.

**Common Causes**

- Expansionary fiscal policy (e.g., large government spending increases, or tax cuts, particularly when the economy is near capacity)
- Expansionary monetary policy (excessive money supply growth or interest rates held below the natural rate)
- A surge in private consumption or investment demand (e.g., pent-up demand following a recession, a wealth effect from rising asset prices)
- Strong export demand or currency depreciation boosting net exports
- Positive demand shocks combined with supply constraints (e.g., post-pandemic reopening demand surges cited in analyses of the 2021-2022 inflation episode)

**Diagrammatic Representation**: In the standard Aggregate Demand-Aggregate Supply (AD-AS) framework, demand-pull inflation is depicted as a **rightward shift of the AD curve** along a relatively steep (or vertical, near full employment) Aggregate Supply curve, raising both the price level and, to a lesser degree as capacity constraints bind, real output.

### Cost-Push Inflation

**Definition**: Cost-push inflation occurs when rising production costs — independent of the level of aggregate demand — force firms to raise prices to maintain profit margins, "pushing" the price level upward even without a corresponding increase in demand.

**Key Points**

- Can occur even during periods of weak aggregate demand or economic slack, potentially producing the combination of rising inflation and stagnant or falling output known as **stagflation**.
- Reflects a leftward or upward shift of the (short-run) Aggregate Supply curve at each level of output.

**Common Causes**

- **Supply shocks**: sudden increases in the price of key inputs, most classically oil price shocks (e.g., the 1973 and 1979 oil crises)
- **Wage-push pressures**: nominal wage increases exceeding productivity growth, raising unit labor costs (particularly relevant in economies with strong wage-bargaining institutions or wage indexation)
- **Import price shocks**: currency depreciation raising the domestic price of imported inputs
- **Markup/profit-push pressures**: firms with market power raising markups independent of cost changes (a mechanism emphasized in some post-Keynesian and more recent "greedflation" debates)
- **Supply chain disruptions**: logistics bottlenecks and input shortages (a mechanism widely cited in analyses of the 2021-2022 global inflation surge)
- **Negative productivity shocks**: reductions in total factor productivity raising the cost of producing a given level of output

**Diagrammatic Representation**: In the AD-AS framework, cost-push inflation is depicted as a **leftward (or upward) shift of the Short-Run Aggregate Supply (SRAS) curve**, raising the price level while simultaneously reducing real output — the mechanism generating stagflation.

### Diagram: AD-AS Comparison (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 760 340">
\<style\>
.txt { font-family: Georgia, serif; font-size: 13px; fill: #222; }
.lbl { font-family: Georgia, serif; font-size: 11px; fill: #555; }
.axis { stroke: #333; stroke-width: 1.5; }
.curve1 { stroke: #333; stroke-width: 2; fill: none; }
.curve2 { stroke: #888; stroke-width: 2; stroke-dasharray: 5,3; fill: none; }
\</style\>
<text x="10" y="20" class="lbl">Demand-Pull vs. Cost-Push Inflation in the AD-AS Model (svg_diagram)</text>


<text x="60" y="45" class="txt">Demand-Pull</text>

<line x1="60" y1="180" x2="60" y2="50" class="axis" />

<line x1="60" y1="180" x2="330" y2="180" class="axis" />

<text x="15" y="60" class="lbl">Price</text>

<text x="280" y="200" class="lbl">Output</text>

<path d="M100,170 Q200,120 300,60" class="curve1" />

<text x="230" y="70" class="lbl">AS</text>

<path d="M80,170 Q130,120 160,70" class="curve1" />

<text x="110" y="90" class="lbl">AD1</text>

<path d="M120,170 Q170,120 200,70" class="curve2" />

<text x="185" y="60" class="lbl">AD2</text>

<text x="60" y="220" class="lbl">AD shifts right → Price↑, Output↑</text>



<text x="450" y="45" class="txt">Cost-Push</text>

<line x1="450" y1="180" x2="450" y2="50" class="axis" />

<line x1="450" y1="180" x2="720" y2="180" class="axis" />

<text x="405" y="60" class="lbl">Price</text>

<text x="670" y="200" class="lbl">Output</text>

<path d="M480,170 Q580,120 680,60" class="curve1" />

<text x="600" y="150" class="lbl">AS1</text>

<path d="M460,170 Q570,110 660,50" class="curve2" />

<text x="580" y="90" class="lbl">AS2</text>

<path d="M470,170 Q550,140 620,70" class="curve1" />

<text x="520" y="175" class="lbl">AD</text>

<text x="450" y="220" class="lbl">SRAS shifts left → Price↑, Output↓ (stagflation)</text>

</svg>

### Formalizing Both Channels in the New Keynesian Phillips Curve

Modern monetary economics unifies both concepts within the augmented NKPC framework:

$$\pi_t = \beta E_t[\pi_{t+1}] + \kappa \tilde{y}_t + u_t$$

**Key Points**

- The term $\kappa \tilde{y}_t$ (the output gap term) captures **demand-pull** pressure: a positive output gap (demand exceeding potential output) directly raises inflation.
- The exogenous term $u_t$ (the cost-push shock) captures **cost-push** pressure: markup or cost shocks unrelated to the level of demand, which shift inflation independently of the output gap.
- [Inference] This formalization implies that, from a pure model-consistent standpoint, demand-pull and cost-push inflation are not fundamentally different economic phenomena but rather different sources feeding into the same underlying price-setting mechanism (marginal cost); the classical distinction is more a matter of diagnostic and policy convenience than a claim of structurally separate inflation-generating processes.

### Policy Implications: Why the Distinction Matters

**Key Points**

- **Demand-pull inflation** is generally addressed by **contractionary monetary or fiscal policy** (raising interest rates, reducing government spending) to cool aggregate demand back toward potential output — a relatively less painful policy response since it does not require accepting a simultaneous decline in output as a necessary trade-off (output typically falls together with the reduction in inflation, both moving back toward potential).
- **Cost-push inflation** presents a genuine **policy dilemma**: tightening monetary policy to combat inflation risks further depressing an already-weakening economy (compounding the output loss from the original supply shock), while accommodating the shock (not tightening) risks entrenching higher inflation expectations and potential wage-price spirals.
- This dilemma is central to the **cost-push shock / divine coincidence breakdown** discussed in New Keynesian monetary policy analysis: cost-push shocks are precisely what forces central banks to make an explicit trade-off between output and inflation stabilization, unlike demand shocks, where stabilizing one typically stabilizes the other.

### Example: Diagnosing an Inflation Episode

**Example**

- **1970s U.S. stagflation**: Widely attributed to a combination of cost-push forces (the 1973 and 1979 oil price shocks) interacting with accommodative monetary policy and unanchored inflation expectations, producing a sustained wage-price spiral.
- **Late-1960s U.S. inflation**: More commonly characterized as demand-pull, driven by expansionary fiscal policy (Vietnam War spending, Great Society programs) combined with accommodative monetary policy, occurring alongside a tightening labor market.
- **2021-2022 global inflation surge**: [Inference] Widely analyzed by central banks and academic economists as reflecting a combination of both channels — pandemic-related fiscal stimulus and pent-up demand (demand-pull) interacting with supply chain disruptions and energy price shocks (cost-push) — though the relative weight assigned to each channel varies across studies and remains a subject of ongoing empirical research and debate.

### The Wage-Price Spiral

A related concept bridging both categories:

**Key Points**

- A **wage-price spiral** describes a self-reinforcing dynamic in which rising prices lead workers to demand higher nominal wages to preserve real purchasing power, and the resulting higher wage costs lead firms to raise prices further, potentially perpetuating inflation independent of the original triggering shock.
- This mechanism can transform an initial cost-push or demand-pull shock into persistent, self-sustaining inflation, particularly if inflation expectations become "unanchored" (workers and firms begin expecting continued high inflation and build it into wage and price-setting behavior).
- The likelihood and severity of a wage-price spiral is generally considered to depend on labor market institutions (e.g., prevalence of formal wage indexation, union bargaining power) and, critically, on the central bank's credibility in anchoring long-run inflation expectations.

### Limitations of the Demand-Pull/Cost-Push Dichotomy

[Inference] While pedagogically useful, the demand-pull/cost-push classification has been critiqued in the academic literature for being a somewhat imprecise reduced-form characterization that can be difficult to cleanly apply to real-world inflation episodes, since observed inflation is typically driven by an empirically difficult-to-disentangle combination of both demand and supply forces operating simultaneously, along with the endogenous response of monetary policy itself.

### Conclusion

Demand-pull and cost-push inflation describe two distinct causal pathways to a rising price level: excess aggregate demand relative to productive capacity, versus rising production costs independent of demand conditions. While modern New Keynesian models formalize both as components feeding into a single price-setting/marginal-cost mechanism (via the output gap and cost-push shock terms in the augmented NKPC), the classical distinction remains valuable for diagnosing the likely source of an inflationary episode and for anticipating the policy trade-offs — particularly the more difficult output-inflation dilemma that cost-push shocks, unlike demand shocks, impose on monetary authorities.

**Related Topics**

- The New Keynesian Phillips Curve and cost-push shock terms
- Stagflation and the 1970s oil shocks
- The wage-price spiral and inflation expectations anchoring
- The Divine Coincidence and its breakdown under supply shocks
- Aggregate Demand-Aggregate Supply (AD-AS) model
- The Phillips Curve and the unemployment-inflation trade-off
- Monetary policy responses to supply shocks
- Inflation expectations formation (adaptive vs. rational)