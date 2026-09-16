## The Expectations-Augmented Phillips Curve


### Overview

The expectations-augmented Phillips Curve, developed independently by Milton Friedman (1968) and Edmund Phelps (1967), is the pivotal theoretical innovation that reconciled the original empirical Phillips Curve with the classical proposition of long-run monetary neutrality. By introducing inflation expectations as an explicit variable, it explained why the observed inflation-unemployment trade-off is only temporary, fundamentally reshaping macroeconomic theory and monetary policy design for decades that followed.

### Motivation: The Problem with the Original Phillips Curve

**Key Points**

- The original Phillips Curve (1958) and its Samuelson-Solow policy-menu reinterpretation (1960) treated the inflation-unemployment relationship as a **stable, exploitable, permanent trade-off**.
- Friedman and Phelps objected on theoretical grounds: a purely nominal variable (the inflation rate) should not have a permanent effect on a real variable (the unemployment rate) once all economic agents fully adjust their behavior — a manifestation of the broader **classical dichotomy** and monetary neutrality principle.
- They argued the apparent trade-off in the data reflected a **temporary, expectations-driven illusion** rather than a stable structural relationship.

### The Core Equation

The expectations-augmented Phillips Curve is typically written as:

$$\pi_t = \pi_t^e - \alpha(u_t - u_n) + \nu_t$$

where:

- $\pi_t$ = actual inflation rate in period $t$
- $\pi_t^e$ = expected inflation rate (formed prior to period $t$)
- $u_t$ = actual unemployment rate
- $u_n$ = the **natural rate of unemployment** (NRU)
- $\alpha > 0$ = a parameter measuring the sensitivity of inflation to the unemployment gap
- $\nu_t$ = a supply shock term (e.g., oil price shocks)

**Key Points**

- The term $(u_t - u_n)$ is the **unemployment gap**: when actual unemployment falls below the natural rate, this exerts upward pressure on inflation beyond what is already expected.
- Rearranging, the equation states that actual inflation equals expected inflation, adjusted by the (negative) unemployment gap and any supply shocks — a form directly analogous to the modern New Keynesian Phillips Curve's structure, but with expected inflation entering with a coefficient of one and unemployment (rather than the output gap) as the real-activity variable.

### The Natural Rate of Unemployment

**Key Points**

- The **natural rate of unemployment** is the unemployment rate that would prevail if inflation expectations were fully realized (i.e., $\pi_t = \pi_t^e$), determined by real (non-monetary) structural features of the labor market.
- Determinants of $u_n$ include: labor market frictions and search costs, the generosity and duration of unemployment insurance, minimum wage laws, unionization and collective bargaining institutions, demographic composition of the labor force, and the efficiency of job-matching processes.
- Crucially, $u_n$ is determined by **real, structural factors**, not by monetary policy or the inflation rate — this is the theoretical basis for the claim that monetary policy cannot permanently influence unemployment.
- [Unverified] The natural rate is not directly observable and must be estimated (e.g., via statistical filtering methods or structural models); estimates vary across time, methodology, and country, and specific numerical values should be checked against current research rather than assumed to be a fixed constant.

### The Expectations-Formation Mechanism: Adaptive Expectations

Friedman and Phelps's original formulation typically assumed **adaptive expectations**, in which agents form expected inflation based on an extrapolation of recently observed actual inflation:

$$\pi_t^e = \pi_{t-1}^e + \lambda(\pi_{t-1} - \pi_{t-1}^e)$$

or, in the simplest special case (assuming $\lambda = 1$):

$$\pi_t^e = \pi_{t-1}$$

**Key Points**

- Under adaptive expectations, agents' expectations adjust gradually, with a lag, to actual observed inflation — they are systematically "surprised" whenever the actual inflation rate deviates from its recent past.
- This lagged adjustment is what generates a genuine **short-run** trade-off: policymakers can temporarily push unemployment below $u_n$ by engineering inflation surprises that expectations have not yet caught up to.
- This mechanism was later criticized by the rational expectations school (Lucas, Sargent) as theoretically inconsistent, since it implies agents make systematic, persistent forecasting errors even when a better forecasting rule (incorporating the known policy process) is available to them.

### The Short-Run vs. Long-Run Distinction

**Short Run:**

- If the central bank engineers an unexpected monetary expansion, actual inflation $\pi_t$ rises above expected inflation $\pi_t^e$ (which is anchored to past, lower inflation).
- Firms and workers, seeing rising nominal prices/wages but not yet fully recognizing the general price level increase, may mistake this for a favorable relative price or real wage change, prompting increased output and employment — moving unemployment temporarily below $u_n$.
- This produces a temporary movement **along** a short-run Phillips Curve associated with the given (now outdated) level of expected inflation.

**Long Run:**

- As agents observe sustained higher inflation, they gradually revise $\pi_t^e$ upward (via the adaptive mechanism).
- As expectations catch up ($\pi_t^e \to \pi_t$), the unemployment gap term vanishes, and unemployment returns to $u_n$ — but now at a **permanently higher inflation rate**.
- The short-run Phillips Curve itself **shifts upward** to reflect the new, higher level of expected inflation.
- Connecting the resulting long-run equilibrium points (one for each possible expected inflation rate, all with $u_t = u_n$) traces out a **vertical long-run Phillips Curve** at the natural rate of unemployment.

### Diagram: Short-Run vs. Long-Run Phillips Curves (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 600 380">
\<style\>
.txt { font-family: Georgia, serif; font-size: 13px; fill: #222; }
.lbl { font-family: Georgia, serif; font-size: 11px; fill: #555; }
.axis { stroke: #333; stroke-width: 1.5; }
.srpc { stroke: #333; stroke-width: 2; fill: none; }
.lrpc { stroke: #888; stroke-width: 2; stroke-dasharray: 6,3; fill: none; }
\</style\>
<text x="10" y="20" class="lbl">Expectations-Augmented Phillips Curve: SR vs LR (svg_diagram)</text>
<line x1="90" y1="330" x2="90" y2="50" class="axis" />
<line x1="90" y1="330" x2="550" y2="330" class="axis" />
<text x="20" y="60" class="lbl">Inflation (π)</text>
<text x="480" y="350" class="lbl">Unemployment (u)</text>
<line x1="280" y1="330" x2="280" y2="60" class="lrpc" />
<text x="290" y="70" class="lbl">LRPC (vertical at u_n)</text>
<path d="M120,280 Q280,240 440,180" class="srpc" />
<text x="440" y="175" class="lbl">SRPC (π_e = π_low)</text>
<path d="M120,180 Q280,140 440,80" class="srpc" />
<text x="440" y="75" class="lbl">SRPC (π_e = π_high)</text>
<circle cx="280" cy="240" r="4" fill="#333" />
<text x="290" y="240" class="lbl">A: u = u_n, π = π_low (initial LR equilibrium)</text>
<circle cx="200" cy="210" r="4" fill="#333" />
<text x="60" y="205" class="lbl">B: u below u_n (short-run, expansion)</text>
<circle cx="280" cy="140" r="4" fill="#333" />
<text x="290" y="140" class="lbl">C: u = u_n, π = π_high (new LR equilibrium)</text>

<text x="90" y="370" class="lbl">Path: A → B (short-run trade-off) → C (expectations catch up, u returns to u_n)</text>

</svg>

### Policy Implications: The Accelerationist Hypothesis

**Key Points**

- A direct corollary is the **accelerationist hypothesis**: if a central bank persistently attempts to hold unemployment below $u_n$, it must generate ever-increasing (accelerating) inflation, since each attempt only works temporarily until expectations adjust, requiring an even larger inflation surprise next time to repeat the effect.
- This is closely related to the concept of the **Non-Accelerating Inflation Rate of Unemployment (NAIRU)**: the unemployment rate at which inflation neither accelerates nor decelerates, conceptually very close to (and often used interchangeably with, though not always technically identical to) the natural rate of unemployment.
- The policy conclusion: monetary policy has **no long-run ability to reduce unemployment below its natural rate**; attempts to do so only produce persistently rising inflation without any lasting employment benefit — a foundational argument for central bank focus on price stability and against activist demand-management policy aimed at target unemployment rates below $u_n$.

### Empirical Vindication and the 1970s

**Key Points**

- The 1970s stagflation episode — simultaneous high inflation and high unemployment — was widely interpreted as strong empirical support for the Friedman-Phelps framework, since it directly contradicted the naive stable trade-off implied by the original, non-augmented Phillips Curve.
- Friedman's 1968 American Economic Association presidential address explicitly predicted that persistent attempts to exploit the Phillips Curve trade-off would eventually produce accelerating inflation without permanent unemployment gains — a prediction many economists viewed as subsequently borne out by events.

### Critique: The Rational Expectations Extension

**Key Points**

- Lucas, Sargent, and others later argued that the adaptive expectations mechanism itself was theoretically unsatisfactory, since it implies agents persistently fail to use all available information (including their understanding of the central bank's policy rule) when forming expectations.
- Under **rational expectations**, if a monetary expansion is **systematic and anticipated** (i.e., consistent with a known policy rule), agents incorporate it into $\pi_t^e$ immediately, eliminating even the short-run trade-off — only genuinely **unanticipated** policy shocks can move unemployment away from $u_n$, and only temporarily.
- This refinement (Sargent-Wallace's Policy Ineffectiveness Proposition) represents a further tightening of the Friedman-Phelps framework's already-limited scope for exploitable monetary policy trade-offs.

### Relationship to the Modern New Keynesian Phillips Curve

[Inference] The expectations-augmented Phillips Curve is often described in textbooks as a direct historical and conceptual precursor to the modern New Keynesian Phillips Curve; both feature an expected-inflation term and a real-activity gap term, though the NKPC replaces adaptive expectations with rational, model-consistent forward-looking expectations and derives its coefficients explicitly from firm price-setting microfoundations (e.g., Calvo pricing) rather than positing the relationship as a reduced-form empirical specification.

### Conclusion

The expectations-augmented Phillips Curve resolved the central theoretical inconsistency of the original Phillips Curve by distinguishing between a temporary, expectations-driven short-run trade-off and a fundamental long-run vertical relationship at the natural rate of unemployment. By formalizing the role of inflation expectations and introducing the concept of a structurally-determined natural rate, Friedman and Phelps provided the theoretical foundation for the view that sustained monetary expansion cannot permanently reduce unemployment — only raise inflation — a proposition subsequently reinforced by the rational expectations revolution and empirically substantiated by the 1970s stagflation experience.

**Related Topics**

- The Phillips Curve and its historical evolution
- The Natural Rate of Unemployment and NAIRU
- Adaptive expectations vs. rational expectations
- The Lucas Critique and Policy Ineffectiveness Proposition
- The New Keynesian Phillips Curve
- Stagflation and the 1970s oil shocks
- The accelerationist hypothesis
- Central bank credibility and time-consistent monetary policy