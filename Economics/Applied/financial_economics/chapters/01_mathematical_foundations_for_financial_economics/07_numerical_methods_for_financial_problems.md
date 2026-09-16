## Numerical Methods for Financial Problems


### Overview and Motivation

Many problems in financial economics — pricing derivatives with path-dependent or American-style features, solving portfolio optimization with realistic constraints, estimating structural models, or characterizing equilibria without closed-form solutions — cannot be solved analytically. Numerical methods provide the computational machinery to approximate solutions to these problems. The major families covered here are: root-finding and optimization, Monte Carlo simulation, finite difference methods for partial differential equations, and numerical linear algebra as it arises in econometric and portfolio applications.

### Root-Finding Methods

Root-finding is used pervasively in finance: implied volatility extraction, yield-to-maturity computation, and solving for internal rates of return all require finding $x$ such that $g(x) = 0$.

**Bisection Method**

Given a continuous function $g$ with $g(a) \cdot g(b) < 0$ (opposite signs at the endpoints), the Intermediate Value Theorem guarantees a root in $(a,b)$. The method repeatedly bisects the interval:

1. Compute midpoint $c = (a+b)/2$.
2. If $g(a) \cdot g(c) < 0$, set $b = c$; else set $a = c$.
3. Repeat until $|b-a|$ is below a tolerance.

**Key Points**

- Guaranteed to converge given a valid bracketing interval; convergence is linear (the error halves each iteration).
- Robust but slow compared to Newton-based methods; requires only function evaluations, not derivatives.

**Newton-Raphson Method**

Given a differentiable function $g$, starting from $x_0$, iterate:

$$x_{n+1} = x_n - \frac{g(x_n)}{g'(x_n)}$$

**Key Points**

- Converges quadratically near a simple root (the number of correct digits roughly doubles each iteration) when it converges, which is markedly faster than bisection's linear convergence.
- Not guaranteed to converge globally: poor starting values, near-zero derivatives, or inflection points can cause divergence or cycling. Behavior is sensitive to the initial guess, and a good starting value from domain knowledge (e.g., an approximate closed-form formula) is standard practice.
- Requires an analytical or numerical derivative $g'(x)$; when the derivative is unavailable or costly, the **secant method** (which approximates $g'$ using a finite difference of the last two iterates) is a common substitute with superlinear (though not quite quadratic) convergence.

**Example: Implied Volatility via Newton-Raphson**

Given an observed European call price $C_{\text{mkt}}$, the implied volatility $\sigma$ solves:

$$g(\sigma) = C_{BS}(\sigma) - C_{\text{mkt}} = 0$$

where $C_{BS}(\sigma)$ is the Black-Scholes price as a function of volatility. Since $g'(\sigma) = \text{Vega}(\sigma) > 0$ (option value is monotonically increasing in volatility, a consequence of the payoff's convexity discussed under Jensen's inequality), Newton-Raphson iteration:

$$\sigma_{n+1} = \sigma_n - \frac{C_{BS}(\sigma_n) - C_{\text{mkt}}}{\text{Vega}(\sigma_n)}$$

typically converges in a handful of iterations from a reasonable starting guess (e.g., $\sigma_0 = 0.2$), because Vega is generally well-behaved (bounded away from zero) except for deep in/out-of-the-money or very short-dated options, where Vega becomes small and convergence can slow or become unstable.

### Optimization Methods

**Unconstrained Optimization: Gradient-Based Methods**

For maximizing a smooth objective $f(x)$ (e.g., a likelihood function in econometric estimation, or expected utility in portfolio choice), **gradient ascent** updates:

$$x_{n+1} = x_n + \alpha \nabla f(x_n)$$

where $\alpha$ is a step size (learning rate). **Newton's method for optimization** uses second-order (curvature) information via the Hessian $H$:

$$x_{n+1} = x_n - H(x_n)^{-1} \nabla f(x_n)$$

which converges faster (quadratically, near the optimum) than plain gradient ascent but requires computing and inverting the Hessian at each step — computationally expensive in high dimensions. **Quasi-Newton methods** (e.g., BFGS) approximate the Hessian iteratively from gradient information, balancing convergence speed against computational cost, and are the standard default in most econometric maximum-likelihood software.

**Constrained Optimization**

Portfolio optimization problems typically involve constraints (budget constraint, no-short-selling, position limits):

$$\max_{w} \; w^\top \mu - \frac{\gamma}{2} w^\top \Sigma w \quad \text{s.t.} \quad \mathbf{1}^\top w = 1, \; w \geq 0$$

For problems with only equality constraints and a quadratic objective (as in unconstrained mean-variance optimization), a closed-form solution via Lagrange multipliers exists. Once inequality constraints (e.g., $w \geq 0$) bind, the problem generally requires **quadratic programming (QP)** solvers, which use active-set or interior-point methods to identify which constraints bind at the optimum and solve the resulting equality-constrained system. [Inference] In practice, most portfolio-construction software relies on established QP or convex-optimization solvers (e.g., interior-point methods) rather than hand-coded gradient methods, because these solvers handle constraint feasibility and numerical stability more reliably than naive gradient projection at scale.

### Monte Carlo Simulation

**Core Idea**

Monte Carlo methods estimate an expectation $\mathbb{E}[h(X)]$ — such as a derivative's discounted expected payoff under the risk-neutral measure — by:

1. Simulating $N$ independent draws $X^{(1)}, \ldots, X^{(N)}$ from the relevant distribution (or stochastic process).
2. Computing the sample average: $\hat{\theta}_N = \dfrac{1}{N}\sum_{i=1}^N h(X^{(i)})$.

By the Law of Large Numbers, $\hat{\theta}_N \to \mathbb{E}[h(X)]$ as $N \to \infty$. By the Central Limit Theorem, the estimator's standard error scales as $O(1/\sqrt{N})$, meaning that quadrupling the number of simulations only halves the standard error — a key limitation motivating variance-reduction techniques.

**Simulating Sample Paths: Euler-Maruyama Discretization**

For a stochastic differential equation $dS_t = \mu(S_t)dt + \sigma(S_t)dW_t$, the Euler-Maruyama scheme discretizes time into steps of size $\Delta t$:

$$S_{t+\Delta t} = S_t + \mu(S_t)\Delta t + \sigma(S_t)\sqrt{\Delta t}\, Z, \quad Z \sim N(0,1)$$

For Geometric Brownian Motion specifically, the exact (non-discretized) transition is available in closed form:

$$S_{t+\Delta t} = S_t \exp\left[\left(\mu - \frac{\sigma^2}{2}\right)\Delta t + \sigma \sqrt{\Delta t}\, Z\right]$$

which avoids discretization bias entirely for this process, since GBM's exact distribution is known; Euler-Maruyama discretization bias becomes relevant primarily for SDEs without a known closed-form transition density (e.g., many stochastic volatility or interest rate models).

**Example: Pricing a European Call via Monte Carlo**

To price a European call with strike $K$, maturity $T$, under the risk-neutral GBM dynamics with risk-free rate $r$:

1. Simulate $N$ terminal prices $S_T^{(i)} = S_0 \exp\left[(r - \sigma^2/2)T + \sigma\sqrt{T} Z^{(i)}\right]$.
2. Compute payoffs $h^{(i)} = \max(S_T^{(i)} - K, 0)$.
3. Estimate the price as $\hat{C} = e^{-rT} \cdot \dfrac{1}{N}\sum_{i=1}^N h^{(i)}$.

This estimator is unbiased (in expectation, it equals the true discounted expected payoff), with standard error $\dfrac{e^{-rT} \, s_h}{\sqrt{N}}$ where $s_h$ is the sample standard deviation of the payoffs — providing a direct, quantifiable measure of simulation precision that closed-form or lattice methods do not naturally provide.

**Variance Reduction Techniques**

| Technique | Mechanism |
| --- | --- |
| Antithetic variates | For each draw $Z$, also use $-Z$; negatively correlated pairs reduce variance of the average when the payoff function's response is monotonic |
| Control variates | Use a correlated variable with known expectation (e.g., a related option with a closed-form price) to reduce variance of the estimate |
| Importance sampling | Sample more heavily from regions that contribute most to the expectation (e.g., deep out-of-the-money payoffs), reweighting by the likelihood ratio |
| Stratified sampling | Divide the sample space into strata and sample each proportionally, reducing sampling variability across strata |

**Key Points**

- Monte Carlo methods are especially well-suited to **high-dimensional** problems (e.g., basket options on many underlyings, path-dependent payoffs), where finite difference grid methods become computationally infeasible due to the curse of dimensionality.
- Monte Carlo is naturally suited to **European-style** (path-independent, no early exercise) and path-dependent payoffs; pricing **American-style** options (with early exercise) via simulation requires more specialized techniques, notably the **Longstaff-Schwartz Least-Squares Monte Carlo** method, which uses cross-sectional regression at each time step to estimate the continuation value and determine the optimal exercise boundary.

### Finite Difference Methods for PDEs

**Motivation**

The Black-Scholes PDE for a derivative price $V(S,t)$:

$$\frac{\partial V}{\partial t} + rS\frac{\partial V}{\partial S} + \frac{1}{2}\sigma^2 S^2 \frac{\partial^2 V}{\partial S^2} - rV = 0$$

can be solved numerically by discretizing both the underlying price $S$ (into a grid $S_0, S_1, \ldots, S_M$) and time $t$ (into steps $t_0, t_1, \ldots, t_N$), approximating derivatives with finite differences.

**Explicit Finite Difference Scheme**

Approximates $\partial V/\partial t$ using a forward difference in time and the spatial derivatives using central differences at the current time step, solving directly for the next time step's grid values.

- Simple to implement; each new time-step value is computed directly from known previous-step values (no system of equations to solve).
- **Conditionally stable**: requires the time step $\Delta t$ to be sufficiently small relative to the spatial step $\Delta S$ (a stability condition analogous to the Courant-Friedrichs-Lewy, or CFL, condition in numerical PDE theory) — using too large a $\Delta t$ causes the solution to oscillate and diverge.

**Implicit Finite Difference Scheme**

Approximates the spatial derivatives at the *next* time step, requiring the solution of a system of linear equations (typically tridiagonal, solvable efficiently via the Thomas algorithm) at each time step.

- **Unconditionally stable** for any $\Delta t, \Delta S$ (for the standard Black-Scholes PDE), at the cost of greater computational effort per time step (solving a linear system rather than direct substitution).

**Crank-Nicolson Scheme**

Averages the explicit and implicit approaches (evaluating spatial derivatives as an average of current and next time step), achieving second-order accuracy in both time and space, versus first-order accuracy for the pure explicit/implicit schemes. It is unconditionally stable and is a standard default choice in production derivative-pricing PDE solvers. [Inference] Crank-Nicolson can, however, exhibit spurious oscillations near payoff discontinuities (e.g., at the strike of a digital option) unless damped with an initial fully-implicit "Rannacher smoothing" step — a refinement commonly applied in practitioner implementations though not part of the base method.

**Key Points**

- Finite difference methods handle **American-style early exercise** naturally by comparing the computed continuation value against the immediate exercise payoff at each grid point/time step, and taking the maximum — this is generally simpler to implement for American options than the Longstaff-Schwartz Monte Carlo alternative, particularly in low dimensions (one or two underlying state variables).
- Finite difference methods scale poorly to high dimensions (more than 2-3 state variables) because the grid size grows exponentially with the number of dimensions — the same curse of dimensionality that Monte Carlo methods are comparatively robust to.

### Numerical Linear Algebra in Financial Econometrics

**Matrix Decompositions**

- **Cholesky decomposition**: factors a positive-definite covariance matrix $\Sigma = LL^\top$ (with $L$ lower triangular). Used to simulate correlated random variables: given independent standard normal draws $Z$, $LZ$ has covariance $\Sigma$. This is the standard technique for simulating correlated asset paths in multi-asset Monte Carlo pricing.
- **Eigenvalue decomposition**: used in Principal Component Analysis (PCA) of yield curves or asset returns, decomposing the covariance matrix into orthogonal factors ordered by variance explained — commonly applied to reduce the dimensionality of interest rate curve models (e.g., level, slope, curvature factors).
- **Singular Value Decomposition (SVD)**: a generalization used for non-square matrices, relevant in factor model estimation and in regularizing ill-conditioned regression problems.

**Key Points**

- Covariance matrix estimates from limited sample sizes (especially when the number of assets approaches or exceeds the number of time observations) can be poorly conditioned or not positive-definite due to estimation noise, which can cause numerical instability in portfolio optimization (e.g., extreme, unstable optimal weights). Regularization techniques (shrinkage estimators, factor models) are standard responses to this issue.
- Numerical behavior of matrix operations (conditioning, stability of inversion) depends on the specific data and implementation; results should be checked for sensitivity to small perturbations in the input data when working with near-singular matrices.

### Summary Comparison of Method Families

| Method family | Best suited for | Limitation |
| --- | --- | --- |
| Root-finding (Newton-Raphson, bisection) | Single-equation problems (implied vol, YTM) | Only solves scalar or low-dimensional root problems |
| Gradient/Newton optimization | Smooth objective functions (MLE, mean-variance) | Local optima only; sensitive to starting values in non-convex cases |
| Monte Carlo simulation | High-dimensional, path-dependent payoffs | Slow convergence ($O(1/\sqrt{N})$); early exercise requires extensions |
| Finite difference (PDE) methods | Low-dimensional problems, American options | Curse of dimensionality beyond 2-3 state variables |

### Illustrative Diagram: Choosing a Numerical Method

```mermaid
flowchart TD
    A["Financial numerical problem"] --> B{"Type of problem?"}

    B -->|Solve single equation g(x)=0| C["Root-finding: Bisection or Newton-Raphson"]
    B -->|Maximize/minimize an objective| D["Optimization: Gradient, Newton, Quasi-Newton, or QP"]
    B -->|Price a derivative or evaluate expectation| E{"How many state variables / dimensions?"}

    E -->|Low dimension 1-2| F{"Early exercise feature?"}
    E -->|High dimension 3+| G["Monte Carlo simulation"]

    F -->|No, European-style| H["Finite difference PDE or closed-form"]
    F -->|Yes, American-style| I["Finite difference with early-exercise check"]

    G --> J{"Early exercise feature?"}
    J -->|No| K["Standard Monte Carlo + variance reduction"]
    J -->|Yes| L["Longstaff-Schwartz Least-Squares Monte Carlo"]
```

### Related Topics

- Value function iteration and dynamic programming (link to fixed-point theorems)
- Longstaff-Schwartz Least-Squares Monte Carlo for American options
- Binomial and trinomial lattice methods as discrete-time alternatives to PDE and Monte Carlo approaches
- Quasi-Monte Carlo methods and low-discrepancy sequences (Sobol, Halton)
- Maximum likelihood estimation and numerical optimization in econometrics
- Quadratic programming and convex optimization for portfolio construction
- Copula-based simulation for modeling dependence beyond linear correlation
- Calibration of stochastic volatility and interest rate models to market data
- Greeks estimation via finite differences versus pathwise/likelihood-ratio Monte Carlo methods
- Numerical stability, conditioning, and regularization in covariance matrix estimation