## Constrained Optimization and Lagrange Multipliers

### Definition and Purpose

Constrained optimization is the process of finding the maximum or minimum value of an objective function subject to one or more explicit constraints that restrict the feasible values of the decision variables. In managerial economics, decision-makers rarely operate without limitations — budgets, production capacity, resource availability, and regulatory requirements all impose boundaries on the choices available. Constrained optimization provides the mathematical framework to find the best possible outcome within these limitations.

The **method of Lagrange multipliers** is the primary technique for solving constrained optimization problems with equality constraints. It transforms a constrained problem into an equivalent unconstrained problem by introducing a new variable — the Lagrange multiplier ($\lambda$) — that captures the marginal value of relaxing the constraint.

### General Framework

Consider the problem of optimizing an objective function $Z = f(X, Y)$ subject to a constraint $g(X, Y) = c$, where $c$ is a fixed constant.

**Step 1 — Form the Lagrangian Function**:

$$L(X, Y, \lambda) = f(X, Y) - \lambda \left[ g(X, Y) - c \right]$$

**Step 2 — First-Order Conditions**: Take partial derivatives of $L$ with respect to each decision variable and $\lambda$, and set each equal to zero.

$$\frac{\partial L}{\partial X} = \frac{\partial f}{\partial X} - \lambda \frac{\partial g}{\partial X} = 0$$



$$\frac{\partial L}{\partial Y} = \frac{\partial f}{\partial Y} - \lambda \frac{\partial g}{\partial Y} = 0$$



$$\frac{\partial L}{\partial \lambda} = -\left[ g(X, Y) - c \right] = 0 \quad \Rightarrow \quad g(X, Y) = c$$

**Step 3 — Solve the System of Equations**: The three first-order conditions form a system of simultaneous equations solved for $X^*$, $Y^*$, and $\lambda^*$.

### Economic Interpretation of the Lagrange Multiplier

The value of $\lambda$ at the optimum represents the **shadow price** of the constraint — the marginal change in the objective function's optimal value resulting from a one-unit relaxation of the constraint. Formally:

$$\lambda^* = \frac{\partial f^*}{\partial c}$$

For example, if the constraint is a budget limit and the objective is utility or profit, $\lambda^*$ indicates approximately how much additional utility or profit would result from one additional unit of budget. This makes $\lambda$ a valuable decision-making metric independent of the specific values of $X^*$ and $Y^*$.

### Worked Example: Utility Maximization Subject to a Budget Constraint

**Scenario**: A consumer has a utility function $U(X, Y) = XY$ and a budget constraint of $100, with the price of good X at $4 and the price of good Y at $5. Maximize utility subject to the budget constraint.

**Step 1 — Set Up the Problem**:

$$\max \; U(X,Y) = XY \quad \text{subject to} \quad 4X + 5Y = 100$$

**Step 2 — Form the Lagrangian**:

$$L = XY - \lambda(4X + 5Y - 100)$$

**Step 3 — First-Order Conditions**:

$$\frac{\partial L}{\partial X} = Y - 4\lambda = 0 \quad \Rightarrow \quad \lambda = \frac{Y}{4}$$



$$\frac{\partial L}{\partial Y} = X - 5\lambda = 0 \quad \Rightarrow \quad \lambda = \frac{X}{5}$$



$$\frac{\partial L}{\partial \lambda} = -(4X + 5Y - 100) = 0 \quad \Rightarrow \quad 4X + 5Y = 100$$

**Step 4 — Solve the System**:

Setting the two expressions for $\lambda$ equal:

$$\frac{Y}{4} = \frac{X}{5} \quad \Rightarrow \quad 5Y = 4X \quad \Rightarrow \quad Y = 0.8X$$

Substituting into the budget constraint:

$$4X + 5(0.8X) = 100$$



$$4X + 4X = 100$$



$$8X = 100$$



$$X^* = 12.5$$

Then:

$$Y^* = 0.8(12.5) = 10$$

**Step 5 — Solve for $\lambda^*$**:

$$\lambda^* = \frac{X^*}{5} = \frac{12.5}{5} = 2.5$$

**Step 6 — Maximum Utility**:

$$U(12.5, 10) = 12.5 \times 10 = 125$$

**Result**: The consumer maximizes utility at $X^* = 12.5$, $Y^* = 10$, achieving maximum utility of 125 utils. The multiplier $\lambda^* = 2.5$ indicates that one additional dollar of budget would increase maximum utility by approximately 2.5 utils.

**Verification — Equimarginal Condition**: This result satisfies the equimarginal principle:

$$\frac{MU_X}{P_X} = \frac{Y}{4} = \frac{10}{4} = 2.5, \qquad \frac{MU_Y}{P_Y} = \frac{X}{5} = \frac{12.5}{5} = 2.5$$

Both ratios equal $\lambda^* = 2.5$, confirming consistency with the equimarginal principle derived earlier in this chapter sequence.

### Key Points

- The Lagrangian method converts a constrained optimization problem into a system of first-order conditions by introducing a multiplier for each constraint.
- The Lagrange multiplier $\lambda^*$ has direct economic meaning as the shadow price — the marginal value of relaxing the constraint by one unit.
- The equimarginal principle emerges naturally as a special case of the Lagrangian first-order conditions when the objective involves allocating a resource across multiple uses.

### Worked Example: Cost Minimization Subject to an Output Constraint

**Scenario**: A firm has a production function $Q = 10L^{0.5}K^{0.5}$ and wants to minimize cost $C = 20L + 30K$ subject to producing a target output of $Q = 200$.

**Step 1 — Form the Lagrangian**:

$$L_{ag} = 20L + 30K - \lambda(10L^{0.5}K^{0.5} - 200)$$

Note: minimizing cost subject to an output constraint is mathematically equivalent to a Lagrangian setup, though the objective here is minimized rather than maximized; the first-order condition procedure is identical.

**Step 2 — First-Order Conditions**:

$$\frac{\partial L_{ag}}{\partial L} = 20 - \lambda(5L^{-0.5}K^{0.5}) = 0$$



$$\frac{\partial L_{ag}}{\partial K} = 30 - \lambda(5L^{0.5}K^{-0.5}) = 0$$



$$\frac{\partial L_{ag}}{\partial \lambda} = -(10L^{0.5}K^{0.5} - 200) = 0$$

**Step 3 — Divide the First Two Conditions** to eliminate $\lambda$:

$$\frac{20}{30} = \frac{5L^{-0.5}K^{0.5}}{5L^{0.5}K^{-0.5}} = \frac{K}{L}$$



$$\frac{2}{3} = \frac{K}{L} \quad \Rightarrow \quad K = \frac{2}{3}L$$

**Step 4 — Substitute into the Output Constraint**:

$$10L^{0.5}\left(\frac{2}{3}L\right)^{0.5} = 200$$



$$10L^{0.5} \cdot \left(\frac{2}{3}\right)^{0.5} L^{0.5} = 200$$



$$10L \sqrt{\frac{2}{3}} = 200$$



$$L \approx \frac{200}{10 \times 0.8165} \approx 24.5$$

Then:

$$K^* = \frac{2}{3}(24.5) \approx 16.3$$

**Result**: The cost-minimizing input combination is approximately $L^* \approx 24.5$, $K^* \approx 16.3$. This illustrates that the same Lagrangian technique applies symmetrically to cost-minimization-subject-to-output problems, not only utility- or profit-maximization problems.

### Diagrammatic Illustration: Tangency Condition

The Lagrangian solution corresponds geometrically to the point where the objective function's level curve (e.g., an indifference curve or isoquant) is tangent to the constraint line (e.g., a budget line or isocost line) — the point where their slopes are equal.

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 420">
<text x="350" y="25" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Constrained Optimum: Tangency Condition (svg_diagram)</text>
<line x1="70" y1="370" x2="70" y2="60" stroke="#333" stroke-width="1.5" />
<line x1="70" y1="370" x2="640" y2="370" stroke="#333" stroke-width="1.5" />
<text x="355" y="400" text-anchor="middle" font-size="13" fill="#333">Good X (or Input L)</text>
<text x="35" y="220" text-anchor="middle" font-size="13" fill="#333" transform="rotate(-90 35 220)">Good Y (or Input K)</text>

<line x1="100" y1="90" x2="580" y2="340" stroke="#16a34a" stroke-width="2.5" />
<text x="500" y="330" font-size="12" fill="#16a34a">Constraint line: g(X,Y) = c</text>

<path d="M 150 340 Q 340 180, 560 130" fill="none" stroke="#2563eb" stroke-width="2.5" />
<text x="480" y="115" font-size="12" fill="#2563eb">Objective level curve: f(X,Y) = k</text>

<circle cx="355" cy="212" r="6" fill="#dc2626" />
<line x1="355" y1="212" x2="355" y2="370" stroke="#dc2626" stroke-width="1" stroke-dasharray="4,4" />
<line x1="70" y1="212" x2="355" y2="212" stroke="#dc2626" stroke-width="1" stroke-dasharray="4,4" />
<text x="355" y="390" text-anchor="middle" font-size="12" fill="#dc2626">X*</text>
<text x="55" y="216" text-anchor="end" font-size="12" fill="#dc2626">Y*</text>
</svg>

### Solution Process Flow

```mermaid
flowchart TD
    A[Define objective function f and constraint g = c] --> B[Form Lagrangian: L = f - lambda times (g - c)]
    B --> C[Take partial derivatives with respect to each decision variable and lambda]
    C --> D[Set all partial derivatives equal to zero - FOCs]
    D --> E[Solve system of equations for X*, Y*, lambda*]
    E --> F[Interpret lambda* as shadow price of the constraint]
    F --> G[Verify second-order conditions - bordered Hessian - for true optimum]
    G --> H[Substitute X*, Y* into objective function for optimal value]
```

### Second-Order Conditions in Constrained Optimization

Unlike unconstrained optimization, confirming a maximum or minimum in the constrained case requires examining the **bordered Hessian** matrix, which incorporates the constraint's derivatives alongside the second-order partial derivatives of the Lagrangian. For a maximum with two choice variables and one constraint, the bordered Hessian determinant must be positive; a full treatment of the bordered Hessian is a standard but more advanced extension typically covered alongside this technique. [Inference: the specific sign conditions for the bordered Hessian vary with the number of variables and constraints, and are addressed in more advanced optimization treatments beyond the two-variable, single-constraint case shown here.]

### Applications in Managerial Economics

**Consumer Utility Maximization**: Determining the optimal consumption bundle given a fixed income and prevailing prices, as illustrated in the worked example above.

**Cost-Minimizing Input Combination**: Determining the least-cost combination of labor and capital required to produce a specified output level, as illustrated in the second worked example.

**Constrained Profit Maximization**: Maximizing profit subject to a production capacity constraint, a raw material availability limit, or a regulatory output cap.

**Portfolio Allocation**: Maximizing expected return subject to a total investment budget constraint or a risk-tolerance constraint, allocating funds across multiple assets.

**Multi-Product Output Allocation**: Allocating a firm's limited production capacity across multiple product lines to maximize total revenue or profit, subject to the capacity constraint.

### Constrained vs. Unconstrained Optimization

| Aspect | Unconstrained Optimization | Constrained Optimization |
| --- | --- | --- |
| Restrictions on decision variables | None (beyond function domain) | One or more explicit constraints (equality or inequality) |
| Solution method | First- and second-order derivative conditions directly on the objective function | Lagrangian function combining objective and constraint(s) |
| Key output | Optimal value(s) of decision variable(s) | Optimal value(s) plus the shadow price ($\lambda$) of each constraint |
| Typical use case | Profit maximization with no capacity or budget limit | Utility maximization under a budget; cost minimization under an output target |

### Assumptions and Limitations

**Equality Constraints Only (Basic Lagrangian)**: The classical Lagrangian method as presented here applies to equality constraints ($g(X,Y) = c$). Problems involving inequality constraints (e.g., $g(X,Y) \leq c$) require the **Kuhn-Tucker (Karush-Kuhn-Tucker) conditions**, an extension of the Lagrangian approach that accounts for the possibility that a constraint may not bind at the optimum.

**Differentiability and Smoothness**: The technique requires that both the objective function and the constraint function be continuous and differentiable, which may not hold for constraints involving discrete choices or non-smooth boundaries.

**Interior Solutions Assumed**: The basic Lagrangian method assumes an interior optimum where all decision variables take strictly positive values; corner solutions (where one variable equals zero) require additional analysis, typically via the Kuhn-Tucker framework.

**Behavior may vary** in applied settings depending on whether the estimated objective and constraint functions accurately represent the real economic relationships being modeled, since real-world utility, cost, and production relationships are approximations derived from data.

**Related Topics**

- The equimarginal principle
- Unconstrained optimization techniques
- Marginal analysis using differential calculus
- Utility theory and indifference curve analysis
- Isoquants, isocost lines, and least-cost input combinations
- Kuhn-Tucker conditions for inequality-constrained optimization
- Shadow prices and their role in resource allocation decisions