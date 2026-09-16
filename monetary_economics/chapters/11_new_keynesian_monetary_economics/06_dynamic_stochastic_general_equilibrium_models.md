## Dynamic Stochastic General Equilibrium Models


### Overview

Dynamic Stochastic General Equilibrium (DSGE) models are the dominant class of quantitative macroeconomic models used in modern monetary economics for policy analysis, forecasting, and understanding business cycle fluctuations. They combine explicit intertemporal optimization by economic agents ("dynamic"), uncertainty from random shocks ("stochastic"), and market-clearing conditions across the entire economy ("general equilibrium"), all built on rigorous microeconomic foundations rather than reduced-form empirical relationships.

### The Three Defining Characteristics

**Key Points**

1. **Dynamic**: Agents (households, firms) make decisions over multiple time periods, optimizing intertemporally (e.g., choosing consumption and savings paths to maximize the present discounted value of lifetime utility).
2. **Stochastic**: The economy is subject to random exogenous shocks (productivity shocks, monetary policy shocks, preference shocks, cost-push shocks) that agents must form rational expectations about.
3. **General Equilibrium**: All markets (goods, labor, capital, money) clear simultaneously, and prices/quantities are jointly and consistently determined across the entire model economy, respecting all agents' budget constraints and optimization conditions.

### Historical Lineage

**Key Points**

- DSGE models descend directly from the **Real Business Cycle (RBC)** tradition (Kydland-Prescott, 1982; Long-Plosser, 1983), which explained business cycles as efficient responses to real (technology) shocks in a frictionless, flexible-price economy.
- **New Keynesian DSGE models** emerged by introducing nominal rigidities (Calvo pricing, sticky wages) and monopolistic competition into the RBC framework, allowing monetary policy to have real effects — departing from RBC's classical policy neutrality.
- Modern **medium-scale DSGE models** (e.g., Christiano-Eichenbaum-Evans 2005; Smets-Wouters 2003, 2007) added numerous additional frictions (habit formation, investment adjustment costs, variable capital utilization) to improve empirical fit to observed macro time series.

### Core Building Blocks of a New Keynesian DSGE Model

**1. Households**

- Infinitely-lived representative (or heterogeneous) households maximize expected lifetime utility over consumption and leisure, subject to a budget constraint.
- Standard utility specification:

$$E_0 \sum_{t=0}^{\infty} \beta^t \left[ \frac{C_t^{1-\sigma}}{1-\sigma} - \frac{N_t^{1+\varphi}}{1+\varphi} \right]$$

where $C_t$ is consumption, $N_t$ is labor supply, $\sigma$ is the inverse elasticity of intertemporal substitution, and $\varphi$ is the inverse Frisch elasticity of labor supply.

**2. Firms**

- Monopolistically competitive firms produce differentiated goods, face demand curves derived from household preferences over a continuum of varieties (typically Dixit-Stiglitz aggregation), and set prices subject to a nominal rigidity (usually Calvo pricing).
- Production is typically modeled with a standard production function, e.g., $Y_t = A_t N_t^{1-\alpha}$, where $A_t$ is exogenous total factor productivity.

**3. Monetary Authority**

- The central bank sets the nominal interest rate according to a policy rule (e.g., a Taylor rule) or solves for optimal policy under commitment or discretion.

**4. Market Clearing and Aggregate Resource Constraint**

- All goods, labor, and (in models with capital) capital markets clear each period, and the aggregate resource constraint (e.g., $Y_t = C_t + I_t + G_t$) must hold.

**5. Exogenous Shock Processes**

- Structural shocks (technology, preference, monetary policy, cost-push, government spending) are typically modeled as stationary AR(1) processes:

$$\log A_t = \rho_A \log A_{t-1} + \varepsilon_t^A, \quad \varepsilon_t^A \sim N(0, \sigma_A^2)$$

### Diagram: DSGE Model Architecture (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 760 320">
\<style\>
.box { fill: #f4f4f4; stroke: #333; stroke-width: 1.5; }
.txt { font-family: Georgia, serif; font-size: 13px; fill: #222; }
.lbl { font-family: Georgia, serif; font-size: 11px; fill: #555; }
.arrow { stroke: #333; stroke-width: 1.5; marker-end: url(#arrow4); }
\</style\>
<text x="10" y="20" class="lbl">DSGE Model Architecture (svg_diagram)</text>
<rect x="30" y="50" width="180" height="60" rx="6" class="box" />
<text x="45" y="75" class="txt">Households</text>
<text x="45" y="93" class="txt">(C, N optimization)</text>
<rect x="290" y="50" width="180" height="60" rx="6" class="box" />
<text x="305" y="75" class="txt">Firms</text>
<text x="305" y="93" class="txt">(pricing, production)</text>
<rect x="550" y="50" width="180" height="60" rx="6" class="box" />
<text x="560" y="75" class="txt">Monetary Authority</text>
<text x="565" y="93" class="txt">(policy rule)</text>
<line x1="210" y1="80" x2="285" y2="80" class="arrow" />
<line x1="470" y1="80" x2="545" y2="80" class="arrow" />
<rect x="200" y="150" width="380" height="60" rx="6" class="box" />
<text x="230" y="175" class="txt">Market Clearing / General Equilibrium</text>
<text x="230" y="193" class="txt">(goods, labor, capital markets)</text>
<line x1="120" y1="110" x2="250" y2="150" stroke="#333" stroke-width="1.5" marker-end="url(#arrow4)" />
<line x1="380" y1="110" x2="390" y2="150" stroke="#333" stroke-width="1.5" marker-end="url(#arrow4)" />
<line x1="640" y1="110" x2="530" y2="150" stroke="#333" stroke-width="1.5" marker-end="url(#arrow4)" />
<rect x="290" y="250" width="180" height="50" rx="6" class="box" />
<text x="305" y="280" class="txt">Exogenous Shocks (ε_t)</text>
<line x1="390" y1="250" x2="390" y2="215" stroke="#333" stroke-width="1.5" marker-end="url(#arrow4)" />
</svg>

### Solving DSGE Models

**Key Points**

- Most DSGE models have no closed-form analytical solution once they include more than a handful of variables/frictions, so they are solved numerically.
- The standard approach:
  1. Derive first-order (optimality) conditions for each agent type.
  2. Compute a non-stochastic steady state.
  3. Log-linearize (or use higher-order perturbation methods) the model equations around the steady state.
  4. Solve the resulting linear rational expectations system using algorithms such as Blanchard-Kahn, Sims' `gensys`, or Klein's QZ decomposition method.
  5. Obtain policy functions expressing endogenous variables as functions of the state variables and shocks.
- Common software implementations include **Dynare** (a widely used MATLAB/Octave/Julia toolbox), as well as custom implementations in Python, Julia (e.g., using packages built around perturbation or projection methods), and specialized central bank modeling platforms.

[Inference] The choice between log-linearization (first-order perturbation) and higher-order/nonlinear solution methods (e.g., for models with an occasionally binding zero lower bound constraint) depends on the specific research question; log-linear methods are standard for computational tractability but can be inaccurate for analyzing large shocks or binding constraints, which is why specialized nonlinear or piecewise-linear solution techniques (e.g., OccBin) have been developed for such cases.

### Estimation Methods

**Key Points**

- **Calibration**: Parameters are set to match long-run averages or ratios observed in the data (e.g., capital share $\alpha$, discount factor $\beta$ implied by steady-state real interest rates), often drawing on microeconomic evidence.
- **Bayesian estimation**: The dominant modern approach (particularly following Smets-Wouters), combining prior distributions over structural parameters (informed by microeconomic studies or previous research) with the likelihood of the observed data (via the Kalman filter, since DSGE models are typically cast in state-space form) to obtain posterior parameter distributions, typically via Markov Chain Monte Carlo (MCMC) methods.
- **Maximum likelihood estimation** is also used, though less commonly than Bayesian methods in the modern literature, partly due to identification and small-sample issues that Bayesian priors help mitigate.

### Model Evaluation

**Example**

- **Impulse response functions (IRFs)**: showing how endogenous variables respond over time to a one-time shock (e.g., output and inflation dynamics following a monetary policy shock).
- **Variance decomposition**: quantifying what share of the forecast error variance in each variable is attributable to each structural shock.
- **Historical shock decomposition**: attributing observed historical fluctuations in a variable to the estimated sequence of underlying structural shocks.
- **Out-of-sample forecasting comparisons**: assessing DSGE model forecast accuracy relative to simpler benchmarks (e.g., Bayesian VARs, random walk models).

### Prominent DSGE Models in the Literature

| Model | Key Features |
| --- | --- |
| RBC (Kydland-Prescott, 1982) | Flexible prices, real shocks only, no monetary non-neutrality |
| Basic 3-equation NK model | Calvo pricing, monopolistic competition, simple IS/NKPC/rule |
| Christiano-Eichenbaum-Evans (2005) | Habit formation, investment adjustment costs, sticky wages, indexation |
| Smets-Wouters (2003, 2007) | Medium-scale, estimated on Euro Area/US data, multiple frictions and shocks |
| New Keynesian Open Economy models | Exchange rates, UIP, terms of trade, international spillovers |
| HANK (Heterogeneous Agent New Keynesian) | Household heterogeneity and incomplete markets replacing the representative agent |

### Criticisms of DSGE Models

**Key Points**

- **The Lucas Critique compliance claim**: DSGE models are marketed as immune to the Lucas Critique because their parameters are structural (preferences, technology) rather than reduced-form, though critics note that many "structural" parameters (e.g., the Calvo parameter $\theta$) are themselves reduced-form approximations of deeper, potentially policy-dependent, price-setting behavior.
- **Representative agent assumption**: Standard DSGE models often abstract from household heterogeneity and distributional effects, a limitation addressed by the more recent Heterogeneous Agent New Keynesian (HANK) literature.
- **2008 Financial Crisis critique**: Standard pre-crisis DSGE models largely lacked a financial sector with meaningful frictions, limiting their ability to predict or explain the financial crisis and its transmission — spurring the development of DSGE models with financial accelerator mechanisms and banking sectors.
- **Complexity vs. transparency trade-off**: Medium- and large-scale DSGE models, while empirically richer, can become difficult to interpret intuitively compared to the stripped-down three-equation model.

[Unverified] The degree to which any specific DSGE model outperforms simpler statistical benchmarks (e.g., Bayesian VARs) in out-of-sample forecasting is an actively contested empirical question, and results vary by model, sample period, and forecast horizon; claims of DSGE superiority or inferiority should be verified against the specific comparative study being referenced.

### Role in Central Bank Policy-Making

**Key Points**

- Major central banks (e.g., the Federal Reserve, European Central Bank, Bank of England, and many others) maintain and regularly update DSGE models as part of their policy analysis and forecasting toolkits, typically alongside other model types (VARs, semi-structural models, judgmental forecasts).
- DSGE models are particularly used for **counterfactual and scenario analysis** — e.g., simulating the effects of alternative policy rules or the consequences of specific structural shocks — given their explicit welfare-theoretic foundations, which allow for formal optimal policy analysis (something purely statistical models cannot provide).

### Conclusion

DSGE models represent the synthesis of rigorous microeconomic optimization, rational expectations under uncertainty, and general equilibrium market clearing into a unified quantitative macroeconomic framework. Evolving from the flexible-price RBC tradition into rich New Keynesian and medium-scale estimated models, DSGE models remain the primary analytical tool for studying monetary policy transmission and conducting welfare-based policy evaluation, notwithstanding ongoing debates about representative-agent assumptions, financial-sector modeling, and empirical performance relative to simpler alternatives.

**Related Topics**

- Real Business Cycle (RBC) theory and its critique
- The three-equation New Keynesian model
- Calvo pricing and staggered contracts
- Bayesian estimation of macroeconomic models
- Smets-Wouters model and medium-scale DSGE frameworks
- Heterogeneous Agent New Keynesian (HANK) models
- The Lucas Critique and structural vs. reduced-form modeling
- Financial frictions and the financial accelerator mechanism