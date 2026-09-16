## Inflation Persistence and Hysteresis


### Overview

Inflation persistence and hysteresis describe two related but distinct phenomena concerning why economic variables — inflation itself, and unemployment following inflation-related disturbances — fail to return quickly to their prior levels after a shock. Understanding these dynamics is critical for monetary policy design, since they directly affect the costs of disinflation, the credibility required to anchor expectations, and the appropriate policy horizon for achieving inflation targets.

### Inflation Persistence: Definition

**Definition**: Inflation persistence refers to the tendency of inflation to remain elevated (or depressed) for an extended period following a shock, rather than returning quickly to its pre-shock level or target — formally, the degree of positive serial correlation in the inflation process.

**Key Points**

- Persistence is commonly measured by the **sum of autoregressive coefficients** in an estimated inflation equation (e.g., $\pi_t = \sum_i \rho_i \pi_{t-i} + \text{shocks}$); a sum close to 1 indicates high persistence (inflation shocks have long-lasting effects), while a sum close to 0 indicates inflation quickly reverts to its mean.
- High inflation persistence implies that once inflation rises, it tends to stay elevated for many periods even after the initiating shock has dissipated, requiring a more prolonged and costly policy response to bring it back down.
- Persistence is empirically distinct from, but related to, the **volatility** of inflation — an inflation series can be highly persistent yet have low volatility, or vice versa.

### Why the Pure New Keynesian Phillips Curve Struggles to Generate Persistence

**Key Points**

- The baseline, purely forward-looking NKPC,

$$\pi_t = \beta E_t[\pi_{t+1}] + \kappa \tilde{y}_t$$

implies that inflation should respond to the **entire discounted path of expected future marginal costs**, and, absent persistence in the output gap or marginal cost process itself, generates very little intrinsic inflation persistence and typically produces impulse responses that peak on impact rather than displaying the gradual, hump-shaped rise observed empirically following monetary policy shocks.

- This has been a major empirical criticism of the baseline NKPC, since VAR-based empirical studies of monetary policy shocks (e.g., Christiano-Eichenbaum-Evans) typically find that inflation responds only gradually and persistently to shocks, rising to a peak several quarters after the shock rather than immediately.

### Sources of Inflation Persistence

**1. Intrinsic (Structural) Persistence**

- Arises from features of the price- and wage-setting process itself.
- **Backward-looking indexation**: In the **hybrid NKPC**, a fraction of firms unable to fully re-optimize their price mechanically index it to lagged inflation (rather than leaving it entirely unchanged, as in the pure Calvo model), directly injecting a backward-looking term:

$$\pi_t = \gamma_f E_t[\pi_{t+1}] + \gamma_b \pi_{t-1} + \kappa \hat{mc}_t$$

- **Rule-of-thumb price/wage setters** (Galí-Gertler, 1999): a fraction of firms set prices using a simple backward-looking rule (e.g., last period's average reset price adjusted for lagged inflation) rather than fully optimizing, generating persistence without requiring formal indexation contracts.
- **Staggered wage contracts** (in addition to staggered prices) can compound persistence, since real wage rigidities slow the adjustment of marginal costs themselves.

**2. Expectations-Driven (Extrinsic) Persistence**

- If inflation expectations are formed adaptively, or if agents are only gradually learning about the true underlying inflation process (adaptive learning), persistence in expectations themselves feeds directly into persistent actual inflation via the expectations term in the Phillips Curve.
- Even under rational expectations, if the underlying driving forces (output gap, marginal cost, or shock processes) are themselves highly persistent (e.g., a highly autocorrelated productivity or demand shock), the resulting inflation process will inherit persistence from these fundamentals, even absent any intrinsic persistence in the price-setting mechanism itself.

**3. Imperfect Central Bank Credibility**

- If the central bank's commitment to its inflation target is not fully credible, agents may only gradually revise their long-run inflation expectations toward the announced target following a disinflationary policy shift, generating persistence in the transition process itself (related to the concept of "expectations anchoring").

### Diagram: Sources of Inflation Persistence (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 300">
\<style\>
.box { fill: #f4f4f4; stroke: #333; stroke-width: 1.5; }
.txt { font-family: Georgia, serif; font-size: 13px; fill: #222; }
.lbl { font-family: Georgia, serif; font-size: 11px; fill: #555; }
\</style\>
<text x="10" y="20" class="lbl">Sources of Inflation Persistence (svg_diagram)</text>
<rect x="30" y="50" width="600" height="40" rx="6" class="box" />
<text x="45" y="75" class="txt">Observed Persistent Inflation Process</text>
<rect x="30" y="120" width="180" height="80" rx="6" class="box" />
<text x="40" y="145" class="txt">Intrinsic / Structural</text>
<text x="40" y="163" class="lbl">Indexation, rule-of-thumb</text>
<text x="40" y="178" class="lbl">price/wage setters,</text>
<text x="40" y="193" class="lbl">staggered wage contracts</text>
<rect x="260" y="120" width="180" height="80" rx="6" class="box" />
<text x="270" y="145" class="txt">Extrinsic / Expectations</text>
<text x="270" y="163" class="lbl">Adaptive expectations,</text>
<text x="270" y="178" class="lbl">adaptive learning,</text>
<text x="270" y="193" class="lbl">persistent shock processes</text>
<rect x="490" y="120" width="180" height="80" rx="6" class="box" />
<text x="500" y="145" class="txt">Credibility-Based</text>
<text x="500" y="163" class="lbl">Imperfect central bank</text>
<text x="500" y="178" class="lbl">credibility, gradual</text>
<text x="500" y="193" class="lbl">anchoring of expectations</text>
<line x1="120" y1="120" x2="150" y2="90" stroke="#333" stroke-width="1.5" />
<line x1="350" y1="120" x2="330" y2="90" stroke="#333" stroke-width="1.5" />
<line x1="580" y1="120" x2="500" y2="90" stroke="#333" stroke-width="1.5" />

<text x="10" y="240" class="lbl">Empirical inflation persistence is generally understood to reflect a combination</text>

<text x="10" y="258" class="lbl">of these channels rather than any single mechanism in isolation.</text>

</svg>

### Hysteresis: Definition and Distinction from Persistence

**Definition**: Hysteresis refers to a stronger, qualitatively different phenomenon in which a **temporary shock has a permanent (or extremely long-lasting) effect** on the equilibrium level of a variable — most classically, unemployment — rather than merely a persistent but eventually fading effect on the deviation of a variable from a fixed equilibrium.

**Key Points**

- The concept, borrowed from physics/materials science (where it describes systems whose current state depends on their history, not just current conditions), was introduced into unemployment economics primarily by Blanchard and Summers (1986) in the context of persistently high European unemployment following the 1970s-80s recessions.
- Under hysteresis, the **natural rate of unemployment itself is not a fixed structural constant** but can be pushed upward (or downward) by the history of actual unemployment — a temporary recession can permanently raise the natural/equilibrium rate, rather than unemployment simply returning to an unchanged natural rate once the shock passes.
- This directly contrasts with the standard Friedman-Phelps natural rate framework, which treats $u_n$ as determined by fixed structural labor market factors, independent of the recent history of actual unemployment.

### Mechanisms Generating Hysteresis

**Example**

- **Skill atrophy and human capital depreciation**: Long-term unemployed workers lose job-relevant skills and become less employable over time, reducing effective labor supply and potentially raising the equilibrium unemployment rate even after aggregate demand recovers.
- **Insider-outsider dynamics**: Employed "insiders" (with wage-bargaining power) have limited incentive to moderate wage demands to help unemployed "outsiders" find jobs, since insiders do not fully internalize the costs borne by outsiders — a mechanism that can perpetuate elevated unemployment.
- **Employer statistical discrimination against the long-term unemployed**: Firms may use unemployment duration as a screening signal, making it progressively harder for the long-term unemployed to be re-hired even when demand conditions improve, entrenching a higher unemployment rate.
- **Reduced job search intensity and discouraged-worker effects**: Extended unemployment spells can reduce active job search effort, further entrenching non-employment.

### Hysteresis and Inflation Dynamics: The Interaction

**Key Points**

- Hysteresis interacts directly with inflation dynamics through the Phillips Curve mechanism: if a demand-driven recession causes hysteresis (permanently raising the natural rate of unemployment), a given inflation rate becomes consistent with a permanently higher unemployment rate than before the shock — meaning the Phillips Curve itself effectively "resets" around a new, worse equilibrium.
- This has significant implications for monetary policy: if hysteresis effects are present, a central bank facing a demand shortfall has a stronger justification for aggressive stabilization policy (to prevent temporary unemployment from becoming permanent via hysteresis channels), rather than "looking through" a temporary downturn on the assumption that unemployment will naturally revert to its unchanged natural rate.
- [Inference] The empirical importance and prevalence of hysteresis effects remain actively debated; while some evidence (e.g., from persistently elevated unemployment in several European economies following the 1970s-80s recessions, and renewed interest following the 2008 financial crisis and its aftermath) is often cited as consistent with hysteresis, isolating hysteresis effects from alternative explanations (such as a genuinely fixed but simply high natural rate, or slow but eventually complete convergence) is empirically challenging, and conclusions vary across studies, countries, and time periods.

### Policy Implications

**Key Points**

- **For inflation persistence**: high measured persistence implies that disinflation requires a sustained period of tight policy (holding the output gap negative for an extended period) to bring inflation down, since backward-looking or slowly-adjusting elements in the inflation process do not respond instantly to a change in policy stance — this underlies the concept of the **sacrifice ratio** (the cumulative output loss required to achieve a given permanent reduction in inflation).
- **For hysteresis**: the existence of hysteresis strengthens the case for **asymmetric or aggressive policy response to negative demand shocks**, since allowing a recession to persist risks permanently damaging labor market capacity — a rationale frequently invoked in discussions of post-2008 and post-pandemic monetary and fiscal policy design, including arguments for "running the economy hot" to reverse prior hysteresis-induced damage.
- Both concepts complicate simple, mechanical rule-based policy (e.g., a basic Taylor rule assuming a fixed, exogenous natural rate) and motivate more state-dependent, historically-aware policy frameworks.

### Empirical Measurement Challenges

[Unverified] Distinguishing genuine structural hysteresis from a simply very high degree of inflation/unemployment persistence, or from mismeasurement of the time-varying natural rate itself, is a substantial econometric challenge; different identification strategies and model specifications in the empirical literature can yield materially different conclusions about the presence and magnitude of hysteresis in any specific historical episode, and claims about specific countries or periods should be verified against current research.

### Conclusion

Inflation persistence and hysteresis both describe departures from the simple assumption that macroeconomic variables quickly and fully revert to fixed equilibrium levels following a shock, but they operate through distinct mechanisms: inflation persistence reflects gradual, backward-looking or expectations-driven adjustment dynamics in the inflation process itself, while hysteresis describes a more fundamental phenomenon in which temporary shocks permanently alter the underlying equilibrium (particularly the natural rate of unemployment). Both concepts significantly complicate monetary policy design, reinforcing the case for policy frameworks that account for the potentially long-lasting and path-dependent consequences of both inflationary shocks and demand-driven recessions.

**Related Topics**

- Hybrid New Keynesian Phillips Curve and inflation indexation
- The natural rate of unemployment and NAIRU
- The sacrifice ratio and costs of disinflation
- Insider-outsider labor market models
- Adaptive learning and expectations anchoring
- Blanchard-Summers hysteresis hypothesis
- Rule-of-thumb price setters (Galí-Gertler)
- Central bank credibility and disinflation strategy