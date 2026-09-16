## Unconstrained Optimization Techniques

### Definition and Purpose

Unconstrained optimization refers to the process of finding the maximum or minimum value of an objective function without any restrictions (constraints) on the values that the decision variable(s) may take, other than those implied by the function's natural domain. In managerial economics, unconstrained optimization is used when a decision-maker seeks the best value of a decision variable (e.g., output quantity, price, advertising expenditure) purely based on the shape of the objective function itself, without external limits such as budget caps or capacity restrictions.

This contrasts with constrained optimization, where the decision variable must also satisfy one or more explicit constraints (e.g., a fixed budget or production capacity), typically solved using Lagrange multipliers or other constrained methods.

### General Framework

Given an objective function $Y = f(X)$, the goal of unconstrained optimization is to find the value(s) of $X$ that maximize or minimize $Y$. The standard two-step process uses differential calculus:

**Step 1 — First-Order Condition (FOC)**: Find critical points by setting the first derivative equal to zero.

$$f'(X) = 0$$

**Step 2 — Second-Order Condition (SOC)**: Determine whether each critical point is a maximum, minimum, or inflection point by examining the second derivative.

$$f''(X) < 0 \Rightarrow \text{maximum at that point}$$



$$f''(X) > 0 \Rightarrow \text{minimum at that point}$$



$$f''(X) = 0 \Rightarrow \text{inconclusive — requires further investigation (possible inflection point)}$$

### Single-Variable Unconstrained Optimization

**Example: Profit Maximization**

Given the profit function:

$$\pi(Q) = -2Q^2 + 240Q - 5000$$

**Step 1 (FOC)**:

$$\frac{d\pi}{dQ} = -4Q + 240 = 0$$



$$Q = 60$$

**Step 2 (SOC)**:

$$\frac{d^2\pi}{dQ^2} = -4 < 0$$

Since the second derivative is negative, $Q = 60$ is confirmed as a profit-maximizing quantity.

**Step 3 — Compute Maximum Profit**:

$$\pi(60) = -2(60)^2 + 240(60) - 5000 = -7200 + 14400 - 5000 = 2200$$

**Result**: The firm maximizes profit at $Q = 60$ units, earning a maximum profit of $2,200.

### Multivariable Unconstrained Optimization

When the objective function depends on two or more decision variables, e.g., $Z = f(X, Y)$, the optimization process requires partial derivatives with respect to each variable.

**First-Order Conditions**:

$$\frac{\partial Z}{\partial X} = 0 \quad \text{and} \quad \frac{\partial Z}{\partial Y} = 0$$

Solving these two equations simultaneously yields the critical point(s) $(X^*, Y^*)$.

**Second-Order Conditions (Multivariable Case)**

For functions of two variables, the second-order condition uses the second-order partial derivatives and the determinant of the **Hessian matrix**:

$$H = \begin{bmatrix} \dfrac{\partial^2 Z}{\partial X^2} & \dfrac{\partial^2 Z}{\partial X \partial Y} \\[8pt] \dfrac{\partial^2 Z}{\partial Y \partial X} & \dfrac{\partial^2 Z}{\partial Y^2} \end{bmatrix}$$

The critical point is a:

- **Maximum** if $\dfrac{\partial^2 Z}{\partial X^2} < 0$, $\dfrac{\partial^2 Z}{\partial Y^2} < 0$, and $\det(H) > 0$
- **Minimum** if $\dfrac{\partial^2 Z}{\partial X^2} > 0$, $\dfrac{\partial^2 Z}{\partial Y^2} > 0$, and $\det(H) > 0$
- **Saddle point** if $\det(H) < 0$
- **Inconclusive** if $\det(H) = 0$

### Worked Example: Two-Variable Profit Maximization

**Scenario**: A firm produces two products, X and Y, with a joint profit function:

$$\pi(X, Y) = 100X + 120Y - 2X^2 - 3Y^2 - XY$$

**Step 1 — First-Order Conditions**:

$$\frac{\partial \pi}{\partial X} = 100 - 4X - Y = 0$$



$$\frac{\partial \pi}{\partial Y} = 120 - 6Y - X = 0$$

**Step 2 — Solve Simultaneously**:

From the first equation: $Y = 100 - 4X$

Substituting into the second equation:

$$120 - 6(100 - 4X) - X = 0$$



$$120 - 600 + 24X - X = 0$$



$$23X = 480$$



$$X^* \approx 20.87$$

Then:

$$Y^* = 100 - 4(20.87) \approx 16.52$$

**Step 3 — Second-Order Conditions**:

$$\frac{\partial^2 \pi}{\partial X^2} = -4, \quad \frac{\partial^2 \pi}{\partial Y^2} = -6, \quad \frac{\partial^2 \pi}{\partial X \partial Y} = -1$$



$$\det(H) = (-4)(-6) - (-1)^2 = 24 - 1 = 23 > 0$$

Since $\frac{\partial^2 \pi}{\partial X^2} < 0$, $\frac{\partial^2 \pi}{\partial Y^2} < 0$, and $\det(H) > 0$, the critical point $(X^*, Y^*) \approx (20.87, 16.52)$ is confirmed as a joint profit-maximizing combination.

**Step 4 — Maximum Profit**:

$$\pi(20.87, 16.52) = 100(20.87) + 120(16.52) - 2(20.87)^2 - 3(16.52)^2 - (20.87)(16.52)$$



$$\approx 2087 + 1982.4 - 871.0 - 819.0 - 344.8 \approx 2034.6$$

**Result**: The firm maximizes joint profit at approximately $X^* \approx 20.87$, $Y^* \approx 16.52$, yielding maximum profit of approximately $2,034.60.

### Key Points

- Unconstrained optimization uses only the first- and second-order derivative conditions of the objective function itself, without incorporating external constraints.
- In the single-variable case, the second derivative test alone confirms whether a critical point is a maximum or minimum.
- In the multivariable case, the Hessian determinant test is required in addition to the individual second-order partial derivatives to correctly classify the critical point (avoiding misidentification of saddle points as optima).

### Optimization Process Flow

```mermaid
flowchart TD
    A[Define objective function Y = f of decision variables] --> B{Single or multiple variables?}
    B -->|Single variable| C[Compute first derivative, set to zero - FOC]
    C --> D[Solve for critical value X*]
    D --> E[Compute second derivative at X*]
    E --> F{f''(X*) < 0?}
    F -->|Yes| G[Confirmed maximum]
    F -->|No| H[Confirmed minimum or inconclusive]
    B -->|Multiple variables| I[Compute partial derivatives, set each to zero - FOCs]
    I --> J[Solve system of equations for critical point]
    J --> K[Construct Hessian matrix of second partials]
    K --> L{Determinant and diagonal signs?}
    L -->|Det > 0, both diagonals negative| M[Confirmed maximum]
    L -->|Det > 0, both diagonals positive| N[Confirmed minimum]
    L -->|Det < 0| O[Saddle point - not an optimum]
```

### Diagrammatic Illustration: Single-Variable Optimization

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 420">
<text x="350" y="25" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Unconstrained Optimization: Profit Function Maximum (svg_diagram)</text>
<line x1="70" y1="370" x2="70" y2="60" stroke="#333" stroke-width="1.5" />
<line x1="70" y1="370" x2="640" y2="370" stroke="#333" stroke-width="1.5" />
<text x="355" y="400" text-anchor="middle" font-size="13" fill="#333">Output (Q)</text>
<text x="35" y="220" text-anchor="middle" font-size="13" fill="#333" transform="rotate(-90 35 220)">Profit (π)</text>

<path d="M 100 340 Q 355 60, 610 340" fill="none" stroke="#2563eb" stroke-width="2.5" />
<text x="450" y="130" font-size="12" fill="#2563eb">π(Q) = -aQ² + bQ - c</text>

<circle cx="355" cy="95" r="6" fill="#16a34a" />
<line x1="355" y1="95" x2="355" y2="370" stroke="#16a34a" stroke-width="1" stroke-dasharray="4,4" />
<line x1="70" y1="95" x2="355" y2="95" stroke="#16a34a" stroke-width="1" stroke-dasharray="4,4" />
<text x="355" y="390" text-anchor="middle" font-size="12" fill="#16a34a">Q* (FOC: dπ/dQ = 0)</text>
<text x="60" y="90" text-anchor="end" font-size="12" fill="#16a34a">π_max</text>
</svg>

### Common Applications in Managerial Economics

**Profit Maximization**: Determining the output level, price, or combination of multiple products that maximizes total profit, as illustrated above.

**Cost Minimization (Unconstrained)**: Finding the input mix or production scale that minimizes cost when no external constraint (such as a fixed budget) is imposed — e.g., minimizing average cost by finding the output level where $\frac{d(AC)}{dQ} = 0$.

**Revenue Maximization**: In firms pursuing a sales-maximization objective (as an alternative to strict profit maximization), unconstrained optimization identifies the output level where marginal revenue equals zero ($MR = 0$), since total revenue is maximized at that point.

**Optimal Advertising Expenditure**: Determining the level of advertising spending that maximizes net profit, accounting for both the diminishing marginal effectiveness of advertising on sales and its direct cost.

### Distinguishing Maxima, Minima, and Inflection Points

| Condition | First Derivative | Second Derivative | Interpretation |
| --- | --- | --- | --- |
| Maximum | $f'(X) = 0$ | $f''(X) < 0$ | Function curves downward (concave) at the point |
| Minimum | $f'(X) = 0$ | $f''(X) > 0$ | Function curves upward (convex) at the point |
| Possible Inflection | $f'(X) = 0$ | $f''(X) = 0$ | Requires higher-order derivative test or graphical inspection |

### Assumptions and Limitations

**Differentiability Requirement**: The technique requires the objective function to be continuous and twice-differentiable over the relevant domain; functions with kinks, discontinuities, or step-like behavior (common in real pricing schedules or tax structures) cannot be optimized using this method without modification.

**Global vs. Local Optima**: Standard first- and second-order conditions identify local maxima or minima. For functions with multiple critical points (e.g., higher-degree polynomials), additional analysis — such as comparing function values across all critical points and boundary behavior — is required to confirm a global optimum. [Inference: whether a local optimum is also global depends on the specific shape of the function and is not guaranteed by the FOC/SOC alone.]

**No External Constraints Considered**: Because unconstrained optimization ignores real-world limitations such as budget, capacity, or regulatory restrictions, the resulting "optimal" solution may be infeasible in practice, necessitating constrained optimization methods when such restrictions are binding.

**Behavior may vary** depending on how accurately the estimated objective function (profit, cost, or revenue function) reflects the firm's actual economic relationships, since real-world data may only approximate the assumed functional form.

**Related Topics**

- Marginal analysis using differential calculus
- Constrained optimization and Lagrange multipliers
- The equimarginal principle
- Functional relationships and economic models
- Partial derivatives and multivariable calculus applications in economics
- Profit maximization vs. alternative objectives (sales maximization, satisficing)
- Second-order conditions and the Hessian matrix in optimization theory