## The Three-Equation New Keynesian Model


### Overview

The three-equation New Keynesian model is the canonical, stripped-down analytical framework used to study monetary policy transmission, inflation-output dynamics, and optimal policy design in modern macroeconomics. It synthesizes microfounded aggregate demand, forward-looking inflation dynamics, and a monetary policy rule into a compact system that has become the workhorse for both academic analysis and central bank policy modeling.

### The Three Core Equations

**Key Points**

The model consists of:

1. **The Dynamic IS Curve** (aggregate demand, from the household's Euler equation)
2. **The New Keynesian Phillips Curve (NKPC)** (aggregate supply, from Calvo pricing)
3. **A Monetary Policy Rule** (e.g., a Taylor rule, or optimal policy under commitment/discretion)

Together, these three equations determine the joint dynamics of three endogenous variables: the output gap $\tilde{y}_t$, inflation $\pi_t$, and the nominal interest rate $i_t$.

### Equation 1: The Dynamic IS Curve

Derived by log-linearizing the representative household's consumption Euler equation around a steady state, and combining with the goods market clearing condition ($c_t = y_t$ in the simplest closed-economy case):

$$\tilde{y}_t = E_t[\tilde{y}_{t+1}] - \frac{1}{\sigma}\left(i_t - E_t[\pi_{t+1}] - r_t^n\right)$$

where:

- $\tilde{y}_t$ = output gap (deviation of output from its flexible-price "natural" level)
- $\sigma$ = coefficient of relative risk aversion (inverse of intertemporal elasticity of substitution)
- $i_t$ = nominal interest rate (policy instrument)
- $E_t[\pi_{t+1}]$ = expected inflation, so that $i_t - E_t[\pi_{t+1}]$ is the ex-ante real interest rate
- $r_t^n$ = the natural (flexible-price equilibrium) real interest rate

**Key Points**

- This is a forward-looking version of the traditional IS curve: current output gap depends on the *expected future* output gap and the *real interest rate gap* (deviation of the real rate from its natural level), not on lagged output or a static multiplier relationship.
- Monetary policy affects the output gap only through the real interest rate gap $(i_t - E_t[\pi_{t+1}] - r_t^n)$: this is the primary transmission channel in the model.
- The natural rate $r_t^n$ is a function of exogenous shocks (e.g., productivity, preference shocks) and is unobservable in real time, posing a genuine practical challenge for policymakers (related to the Wicksellian natural rate concept).

### Equation 2: The New Keynesian Phillips Curve

$$\pi_t = \beta E_t[\pi_{t+1}] + \kappa \tilde{y}_t$$

where $\beta$ is the discount factor and $\kappa$ is derived from the Calvo pricing parameter $\theta$ as:

$$\kappa = \frac{(1-\theta)(1-\beta\theta)}{\theta}$$

(See "Calvo Pricing" and "The New Keynesian Phillips Curve" for full derivation.)

**Key Points**

- Inflation depends on expected future inflation and the current output gap, reflecting forward-looking price-setting under nominal rigidity.
- This is the aggregate supply block of the model, replacing the traditional static or adaptive-expectations Phillips Curve.

### Equation 3: The Monetary Policy Rule

The third equation closes the model by specifying how the central bank sets the nominal interest rate. Two broad approaches are used:

**A. Simple Instrument Rule (Taylor Rule):**

$$i_t = r^n + \phi_\pi \pi_t + \phi_y \tilde{y}_t$$

- $\phi_\pi, \phi_y > 0$ are policy response coefficients to inflation and the output gap, respectively.
- The **Taylor Principle** requires $\phi_\pi > 1$: the nominal rate must rise more than one-for-one with inflation, ensuring the real interest rate rises when inflation increases, which is necessary for a unique, stable (non-explosive, non-sunspot) rational expectations equilibrium.

**B. Optimal Policy (Discretion or Commitment):**

- Under **discretion**, the central bank re-optimizes each period, taking private-sector expectations as given, typically resulting in an **inflationary bias** relative to the social optimum (related to the Kydland-Prescott/Barro-Gordon time-inconsistency problem).
- Under **commitment** (timeless perspective or fully optimal commitment), the central bank credibly commits to a policy rule ex ante, internalizing the effect of its promised future actions on current private-sector expectations, generally achieving superior welfare outcomes than discretion.

[Inference] The empirical validity of any specific Taylor-rule coefficient values (e.g., the frequently cited $\phi_\pi = 1.5$, $\phi_y = 0.5$ from Taylor's original 1993 paper) is time- and country-specific, and actual estimated central bank reaction functions vary considerably across studies and monetary regimes.

### Diagram: The Three-Equation System (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 760 300">
\<style\>
.box { fill: #f4f4f4; stroke: #333; stroke-width: 1.5; }
.txt { font-family: Georgia, serif; font-size: 13px; fill: #222; }
.lbl { font-family: Georgia, serif; font-size: 11px; fill: #555; }
.arrow { stroke: #333; stroke-width: 1.5; marker-end: url(#arrow3); }
\</style\>
<text x="10" y="20" class="lbl">The Three-Equation New Keynesian Model (svg_diagram)</text>
<rect x="30" y="50" width="200" height="70" rx="6" class="box" />
<text x="45" y="78" class="txt">Monetary Policy Rule</text>
<text x="45" y="96" class="txt">(sets i_t)</text>
<rect x="290" y="50" width="200" height="70" rx="6" class="box" />
<text x="305" y="78" class="txt">Dynamic IS Curve</text>
<text x="305" y="96" class="txt">(determines ỹ_t)</text>
<rect x="550" y="50" width="180" height="70" rx="6" class="box" />
<text x="565" y="78" class="txt">NKPC</text>
<text x="565" y="96" class="txt">(determines π_t)</text>
<line x1="230" y1="85" x2="285" y2="85" class="arrow" />
<line x1="490" y1="85" x2="545" y2="85" class="arrow" />
<line x1="640" y1="120" x2="640" y2="160" stroke="#333" stroke-width="1.5" />
<line x1="640" y1="160" x2="130" y2="160" stroke="#333" stroke-width="1.5" />
<line x1="130" y1="160" x2="130" y2="115" class="arrow" />
<text x="230" y="150" class="lbl">π_t feeds back into policy rule (closes the loop)</text>
<line x1="390" y1="120" x2="390" y2="200" stroke="#333" stroke-width="1.5" marker-end="url(#arrow3)" />
<text x="300" y="220" class="lbl">ỹ_t also feeds back into NKPC and policy rule</text>

<text x="10" y="260" class="lbl">Simultaneous system: i_t, ỹ_t, and π_t are jointly determined each period, with</text>

<text x="10" y="278" class="lbl">expectations of future values (E_t[ỹ_(t+1)], E_t[π_(t+1)]) feeding back into current outcomes.</text>

</svg>

### Solving the Model: Determinacy and Equilibrium

**Key Points**

- The three-equation system is a linear rational expectations model, typically solved using standard methods (e.g., the method of undetermined coefficients, or algorithms like Blanchard-Kahn or Sims' gensys).
- **Determinacy** (a unique, non-explosive rational expectations equilibrium) requires the policy rule to satisfy the **Taylor Principle** ($\phi_\pi > 1$). If violated, the model can admit multiple equilibria driven by self-fulfilling expectations ("sunspots"), a central concern in the determinacy literature (Bullard-Mitra, Woodford).
- [Unverified] The exact boundary conditions for determinacy become substantially more complex once additional features (interest rate smoothing, backward-looking terms, zero lower bound constraints) are added; the simple $\phi_\pi > 1$ condition applies cleanly only to the baseline three-equation model.

### Impulse Response Analysis: A Monetary Policy Shock

**Example**

Consider a contractionary monetary policy shock (an exogenous, unexpected increase in $i_t$ beyond what the rule prescribes):

1. The real interest rate rises (via the Fisher relation, since inflation expectations adjust more slowly than the nominal rate).
2. Via the Dynamic IS Curve, the higher real rate reduces current and expected future output gaps — households save more and consume/invest less today.
3. The lower output gap reduces marginal cost, which via the NKPC lowers current inflation (with the effect strengthened by the forward-looking expectation of lower future inflation).
4. The policy rule reacts to the resulting decline in $\pi_t$ and $\tilde{y}_t$ by gradually easing $i_t$ back toward its rule-implied path, absent further shocks.

[Inference] The pure forward-looking version of this model tends to generate output and inflation responses to policy shocks that peak immediately rather than exhibiting the hump-shaped, delayed peak commonly found in empirical VAR studies; this is one of the principal motivations for adding habit formation, adjustment costs, and hybrid NKPC indexation in richer DSGE models.

### The Output Gap-Inflation Trade-off and the "Divine Coincidence"

- In the baseline three-equation model (no cost-push shocks), stabilizing the output gap and stabilizing inflation are simultaneously achievable — the "divine coincidence" (Blanchard-Galí, 2007).
- Adding a cost-push shock term $u_t$ to the NKPC breaks this coincidence, forcing the central bank to make an explicit trade-off between inflation and output-gap stabilization, which is the central subject of optimal monetary policy analysis in this framework.

### Extensions to the Baseline Model

**Example**

- **Open-economy versions** add exchange rate dynamics, uncovered interest parity, and terms-of-trade effects (the New Keynesian Open Economy or "New Open Economy Macroeconomics" framework).
- **Zero lower bound (ZLB) analysis** modifies the policy rule to respect $i_t \geq 0$ (or an effective lower bound), fundamentally changing model dynamics during liquidity trap episodes.
- **Financial frictions** extensions (e.g., financial accelerator mechanisms) add credit spreads and balance-sheet effects, relevant to the post-2008 New Keynesian literature.
- **Medium-scale DSGE models** (e.g., Smets-Wouters, Christiano-Eichenbaum-Evans) embed the three-equation core within a richer structure including capital accumulation, habit formation, investment adjustment costs, and multiple structural shocks, primarily for quantitative fit to macro data.

### Conclusion

The three-equation New Keynesian model — comprising the dynamic IS curve, the New Keynesian Phillips Curve, and a monetary policy rule — provides the standard minimal analytical apparatus for studying how monetary policy transmits through real interest rates to affect output and, ultimately, inflation. Its tractability has made it the benchmark teaching and analytical tool in modern monetary economics, even as richer quantitative DSGE models extend its core logic to match observed macroeconomic dynamics more closely.

**Related Topics**

- Calvo pricing and staggered contracts (microfoundation of the NKPC)
- The New Keynesian Phillips Curve (detailed derivation)
- The Taylor Principle and equilibrium determinacy
- Time inconsistency and the discretion vs. commitment debate (Kydland-Prescott, Barro-Gordon)
- The natural rate of interest and its estimation challenges
- Divine coincidence and cost-push shocks
- Zero lower bound and unconventional monetary policy
- Medium-scale DSGE models (Smets-Wouters)