## Differential Games

### Overview

A differential game is a model of conflict or cooperation among decision-makers whose state evolves continuously over time according to a differential equation, with each player choosing controls to optimize an objective functional. Differential games generalize discrete-time dynamic games to continuous time and are the primary tool for modeling strategic interaction in physical, economic, and engineering systems where state variables (position, capital, pollution stock, etc.) change smoothly.

The theory was founded by Rufus Isaacs in the 1950s-60s, originally for pursuit-evasion problems in military applications, and was later connected rigorously to optimal control theory and viscosity solutions of partial differential equations.

### Formal Definition

A standard two-player differential game consists of:

- A **state** $x(t) \in \mathbb{R}^n$ evolving via a state equation (dynamics):

$$\dot{x}(t) = f(t, x(t), u_1(t), u_2(t)), \quad x(t_0) = x_0$$

- **Control inputs** $u_i(t) \in U_i$ chosen by player $i$ over time, where $U_i$ is the admissible control set (often compact).
- **Payoff (objective) functionals**, typically of Bolza/Mayer form:

$$J_i(u_1, u_2) = \int_{t_0}^{T} g_i(t, x(t), u_1(t), u_2(t))\, dt + h_i(x(T))$$

- A **terminal condition**: either a fixed horizon $T$, or a terminal (target) set reached at a free stopping time (as in pursuit games).
- An **information structure**: whether players observe the current state, each other's past controls, or commit to open-loop strategies.

Each player selects a control (or, more generally, a strategy mapping information to controls) to maximize (or minimize) their own $J_i$, subject to the shared dynamics.

### Classification of Strategies

**Open-loop strategies**: $u_i(t)$ depends only on time and initial state $x_0$, fixed in advance. Analyzed via the Pontryagin Maximum Principle applied jointly to all players.

**Closed-loop (feedback/Markovian) strategies**: $u_i(t) = \phi_i(t, x(t))$ depends on the current state. These are generally **subgame perfect** (time-consistent), unlike open-loop equilibria, which may not be.

**Key distinction**: Open-loop Nash equilibria and feedback Nash equilibria generally do **not** coincide except in special cases (e.g., linear-quadratic games with certain structures). Feedback equilibria are preferred in economic applications because they are credible at every point in time, not just at $t_0$.

### Solution Concepts

**Nash Equilibrium in Differential Games**

A pair of strategies $(u_1^*, u_2^*)$ is a Nash equilibrium if neither player can improve their payoff by unilaterally deviating, holding the opponent's strategy fixed — analogous to static Nash equilibrium but applied to entire trajectories.

**Zero-Sum Differential Games and the Isaacs Equation**

For two-player zero-sum games ($J_1 = -J_2 = J$), define the value function:

$$V(t, x) = \sup_{u_1} \inf_{u_2} J(t, x, u_1, u_2)$$

Under the **Isaacs condition** (existence of a saddle point in the Hamiltonian), $V$ satisfies the Hamilton-Jacobi-Isaacs (HJI) PDE:

$$-\frac{\partial V}{\partial t} = \min_{u_2 \in U_2} \max_{u_1 \in U_1} \left[ g(t,x,u_1,u_2) + \nabla_x V \cdot f(t,x,u_1,u_2) \right]$$

with boundary condition $V(T, x) = h(x)$.

[Inference] When the Isaacs condition fails (no saddle point in the Hamiltonian), the upper and lower value functions may differ, and the game's value may not exist in the classical sense — mixed or randomized strategies (or a different equilibrium notion) are then required.

**Hamilton-Jacobi-Bellman (HJB) System for Non-Zero-Sum Games**

For $N$-player non-zero-sum games with feedback Nash equilibrium, each player's value function $V_i(t,x)$ solves a **coupled** system of HJB equations:

$$-\frac{\partial V_i}{\partial t} = \max_{u_i} \left[ g_i(t,x,u_1^*,\dots,u_i,\dots,u_N^*) + \nabla_x V_i \cdot f(t,x,u_1^*,\dots,u_i,\dots,u_N^*) \right]$$

where each player optimizes holding others' equilibrium strategies $u_j^*$ fixed. This coupling (each equation depends on the others' solutions) makes non-zero-sum differential games substantially harder to solve than zero-sum ones.

### Pursuit-Evasion Games

The canonical Isaacs framework: a pursuer $P$ tries to minimize capture time (or maximize distance at a fixed time), while an evader $E$ does the opposite.

**Simple example — Homicidal Chauffeur / Pursuit game:**

State: relative position $x = x_E - x_P$. Dynamics:

$$\dot{x} = f(x, u_P, u_E)$$

Capture occurs when $x(t)$ enters a target set $\mathcal{C}$ (e.g., $\|x\| \le \epsilon$).

**Key geometric constructs:**

- **Barrier surfaces**: boundaries in state space separating regions where the pursuer can guarantee capture from regions where the evader can guarantee escape.
- **Retrogressive Path Equations (RPEs)**: Isaacs' method of solving backward from the terminal (capture) surface using the necessary conditions from the Hamiltonian.

### Linear-Quadratic Differential Games (LQDG)

The most tractable class, extending LQR to multiple players. Dynamics are linear:

$$\dot{x} = Ax + B_1 u_1 + B_2 u_2$$

Payoffs are quadratic:

$$J_i = \int_0^T \left( x^T Q_i x + u_i^T R_i u_i \right) dt + x(T)^T Q_{iT} x(T)$$

**Feedback Nash equilibrium** strategies take linear form $u_i^*(t) = -K_i(t) x(t)$, where the gain matrices $K_i(t)$ are derived from a **coupled system of Riccati differential equations**:

$$-\dot{P}_i = A^T P_i + P_i A - \sum_{j} P_i B_j R_j^{-1} B_j^T P_j + Q_i, \quad P_i(T) = Q_{iT}$$

with $K_i(t) = R_i^{-1} B_i^T P_i(t)$.

[Unverified] Unlike single-player LQR, this coupled Riccati system does not always admit a solution over the full interval $[0,T]$; finite escape times can occur even when each individual player's problem is well-posed.

### Worked Example: Pollution Game (Non-Zero-Sum, Feedback)

Two firms each choose an emission control $u_i(t) \ge 0$. Pollution stock $x(t)$ accumulates:

$$\dot{x} = u_1 + u_2 - \delta x, \quad x(0) = x_0$$

Firm $i$ minimizes:

$$J_i = \int_0^\infty e^{-rt} \left( c_i u_i^2 - d_i x \right) dt$$

(cost of abatement effort net of damage from stock $x$).

**Steps to solve:**

1. Postulate linear feedback value functions $V_i(x) = a_i x^2 + b_i x + c_i$ (guess-and-verify for infinite-horizon autonomous problems).
2. Write each player's HJB equation, substitute the guessed form, and use the first-order condition $\partial/\partial u_i$ of the Hamiltonian to get $u_i^*(x)$ in terms of $\nabla V_i$.
3. Substitute $u_i^*$ back into both HJB equations, matching coefficients of $x^2$, $x$, and constants to solve for $(a_i, b_i, c_i)$ — this yields a system of coupled algebraic (Riccati-type) equations.
4. The resulting **feedback Nash equilibrium** gives each firm's steady-state emission as a function of current pollution stock.

**Key Points**

- The steady state $x^*$ (where $\dot{x}=0$) under Nash competition is generally higher than the cooperative (jointly optimal) steady state — a differential-game analogue of the tragedy of the commons.
- Open-loop equilibria in this class of game are typically time-inconsistent: firms would want to revise strategies after seeing the state evolve, unlike feedback equilibria.

### Cooperative Differential Games

When players can commit to binding agreements, cooperative solution concepts apply:

- **Pareto-efficient trajectories**: solved via a weighted-sum optimal control problem, $\max \sum_i \lambda_i J_i$, tracing the Pareto frontier as $\lambda$ varies.
- **Time-consistency (dynamic stability)**: a cooperative agreement is time-consistent if, along the optimal cooperative trajectory, no subgroup has incentive to deviate at any intermediate time. This often requires an **imputation distribution procedure (IDP)** that reallocates payoff flows over time to sustain the agreement — a central concern absent from static cooperative game theory.
- **Characteristic function** construction (for coalition values) requires specifying what a deviating coalition can guarantee, which is itself a differential (sub)game against the complement coalition.

### Differential Games with State Constraints

When trajectories must satisfy $x(t) \in \mathcal{X}$ (feasible region) for all $t$, the HJB/HJI equations require additional boundary conditions or reformulation via viscosity solutions, since the value function may fail to be differentiable at constraint boundaries. [Inference] This is why numerical methods for constrained differential games generally rely on viscosity-solution PDE solvers rather than direct Riccati-based closed forms.

### Diagram: Solution Structure of a Two-Player Differential Game (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 760 460" font-family="Arial, sans-serif">
<title>Solution Structure of a Two-Player Differential Game (svg_diagram)</title>
<rect x="0" y="0" width="760" height="460" fill="#ffffff" />
<rect x="20" y="20" width="720" height="60" rx="8" fill="#e8f0fe" stroke="#3b5bdb" stroke-width="1.5" />
<text x="380" y="45" text-anchor="middle" font-size="16" font-weight="bold" fill="#1c2b4a">Differential Game</text>
<text x="380" y="65" text-anchor="middle" font-size="12" fill="#333">Dynamics ẋ = f(t,x,u₁,u₂), Payoffs Jᵢ(u₁,u₂)</text>
<line x1="380" y1="80" x2="200" y2="130" stroke="#666" stroke-width="1.5" />
<line x1="380" y1="80" x2="560" y2="130" stroke="#666" stroke-width="1.5" />
<rect x="90" y="130" width="220" height="55" rx="8" fill="#fff3bf" stroke="#e8a917" stroke-width="1.5" />
<text x="200" y="152" text-anchor="middle" font-size="13" font-weight="bold" fill="#5c4b00">Open-Loop Strategies</text>
<text x="200" y="170" text-anchor="middle" font-size="11" fill="#5c4b00">Pontryagin Maximum Principle</text>
<rect x="450" y="130" width="220" height="55" rx="8" fill="#d3f9d8" stroke="#2f9e44" stroke-width="1.5" />
<text x="560" y="152" text-anchor="middle" font-size="13" font-weight="bold" fill="#1b4620">Feedback Strategies</text>
<text x="560" y="170" text-anchor="middle" font-size="11" fill="#1b4620">State-dependent, subgame perfect</text>
<line x1="560" y1="185" x2="560" y2="220" stroke="#666" stroke-width="1.5" />
<rect x="420" y="220" width="280" height="55" rx="8" fill="#ffe3e3" stroke="#c92a2a" stroke-width="1.5" />
<text x="560" y="242" text-anchor="middle" font-size="13" font-weight="bold" fill="#7a0d0d">Coupled HJB System</text>
<text x="560" y="260" text-anchor="middle" font-size="11" fill="#7a0d0d">One PDE per player, mutually dependent</text>
<line x1="560" y1="275" x2="560" y2="305" stroke="#666" stroke-width="1.5" />
<polygon points="560,315 545,300 575,300" fill="#666" />
<rect x="230" y="315" width="240" height="55" rx="8" fill="#e5dbff" stroke="#7048e8" stroke-width="1.5" />
<text x="350" y="337" text-anchor="middle" font-size="13" font-weight="bold" fill="#3c1e70">Zero-Sum Case</text>
<text x="350" y="355" text-anchor="middle" font-size="11" fill="#3c1e70">Single HJI equation, value V(t,x)</text>
<rect x="490" y="315" width="240" height="55" rx="8" fill="#d0ebff" stroke="#1971c2" stroke-width="1.5" />
<text x="610" y="337" text-anchor="middle" font-size="13" font-weight="bold" fill="#0b3d63">Non-Zero-Sum Case</text>
<text x="610" y="355" text-anchor="middle" font-size="11" fill="#0b3d63">Feedback Nash Equilibrium</text>
<line x1="350" y1="370" x2="230" y2="405" stroke="#666" stroke-width="1.5" />
<rect x="60" y="405" width="260" height="45" rx="8" fill="#f1f3f5" stroke="#495057" stroke-width="1.5" />
<text x="190" y="432" text-anchor="middle" font-size="12" fill="#212529">Pursuit-Evasion / Barrier Surfaces</text>
<line x1="610" y1="370" x2="610" y2="405" stroke="#666" stroke-width="1.5" />
<rect x="480" y="405" width="260" height="45" rx="8" fill="#f1f3f5" stroke="#495057" stroke-width="1.5" />
<text x="610" y="432" text-anchor="middle" font-size="12" fill="#212529">Linear-Quadratic Games (Riccati ODEs)</text>
</svg>

### Applications

- **Military/aerospace**: missile pursuit-evasion, aircraft dogfighting, drone interception.
- **Economics**: dynamic oligopoly with capital accumulation, resource extraction races (e.g., common-pool fisheries, groundwater), advertising competition (Lanchester-type models).
- **Environmental economics**: transboundary pollution control, climate negotiation games.
- **Finance**: adversarial trading/predatory trading models, principal-agent contracting in continuous time.
- **Robotics/multi-agent systems**: reachability analysis for safety-critical control (e.g., collision avoidance formulated as pursuit-evasion using HJI reachability).

### Relationship to Other Frameworks

- **Optimal control theory**: a differential game reduces to a single-player optimal control problem when there is one decision-maker; the Isaacs equation reduces to the standard HJB equation.
- **Repeated/stochastic games**: differential games are the continuous-time, continuous-state analogue of discrete-time stochastic games (see chapter context); adding Brownian noise to the state equation yields **stochastic differential games**, solved via second-order (Isaacs/HJB) PDEs with a diffusion term.
- **Mean-field games**: when the number of players $N \to \infty$ with symmetric interactions, differential games approximate mean-field games, replacing pairwise coupling with coupling through a population distribution.

### Common Pitfalls

- Conflating open-loop and feedback Nash equilibria — they generally differ and have different time-consistency properties.
- Assuming a value function exists for non-zero-sum games without recognizing this requires solving a *coupled* system, not a single equation.
- Ignoring the Isaacs condition in zero-sum games, which can invalidate the direct HJI approach.
- [Speculation] Numerically, naive discretization of coupled Riccati or HJB systems can be unstable near singular surfaces or state constraints; practitioners often report needing specialized solvers (e.g., level-set methods for HJI reachability) though robustness depends heavily on problem structure.

**Related Topics**

- Stochastic Differential Games
- Mean-Field Games
- Pontryagin Maximum Principle
- Hamilton-Jacobi-Bellman Equation
- Linear-Quadratic Regulator (LQR) and Riccati Equations
- Repeated Games and Folk Theorems
- Viscosity Solutions of PDEs
- Dynamic Programming in Continuous Time
- Pursuit-Evasion and Reachability Analysis
- Time Consistency in Dynamic Games