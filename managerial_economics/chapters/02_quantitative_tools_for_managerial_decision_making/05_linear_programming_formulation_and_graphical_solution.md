## Linear Programming Formulation and Graphical Solution


### Definition and Purpose

Linear programming (LP) is a mathematical optimization technique used to find the best outcome — maximum profit or minimum cost — in a decision problem subject to a set of linear constraints. In managerial economics, LP is applied to resource allocation problems where a manager must decide how much of each product to produce, or how to allocate limited resources, given constraints on inputs such as labor, materials, and machine time.

An LP problem consists of three components:

- **Objective function**: the linear expression to be maximized or minimized.
- **Decision variables**: the unknown quantities to be determined.
- **Constraints**: linear inequalities or equations restricting feasible values of decision variables.
- **Non-negativity conditions**: decision variables cannot be negative, since negative production or resource use is economically meaningless.

### General Formulation Structure

For two decision variables $x_1$ and $x_2$, a maximization LP problem is written as:

$$\text{Maximize } Z = c_1 x_1 + c_2 x_2$$

subject to:

$$a_{11}x_1 + a_{12}x_2 \le b_1$$



$$a_{21}x_1 + a_{22}x_2 \le b_2$$



$$\vdots$$



$$a_{m1}x_1 + a_{m2}x_2 \le b_m$$



$$x_1 \ge 0,\ x_2 \ge 0$$

Where:

- $Z$ = objective function value (e.g., total profit)
- $c_1, c_2$ = profit (or cost) contribution per unit of $x_1, x_2$
- $a_{ij}$ = amount of resource $i$ required per unit of variable $j$
- $b_i$ = total available amount of resource $i$

### Steps in Formulating an LP Problem

1. **Define decision variables** clearly, with units (e.g., $x_1$ = units of Product A produced per week).
2. **Formulate the objective function** in terms of the decision variables (profit, cost, revenue).
3. **Identify constraints** — resource limits, demand limits, minimum requirements — and express each as a linear inequality/equation.
4. **Add non-negativity constraints**.
5. **Solve** using graphical method (two variables) or simplex method (more than two variables).

### Worked Example: Formulation

A firm produces two products, A and B.

- Product A yields a profit of $40/unit; Product B yields $30/unit.
- Each unit of A requires 2 hours of labor and 1 unit of raw material.
- Each unit of B requires 1 hour of labor and 2 units of raw material.
- Available labor: 100 hours/week. Available raw material: 80 units/week.

**Decision variables:**

- $x_1$ = units of Product A produced per week
- $x_2$ = units of Product B produced per week

**Objective function:**

$$\text{Maximize } Z = 40x_1 + 30x_2$$

**Constraints:**

$$2x_1 + x_2 \le 100 \quad \text{(labor)}$$



$$x_1 + 2x_2 \le 80 \quad \text{(raw material)}$$



$$x_1 \ge 0,\ x_2 \ge 0$$

### The Graphical Solution Method

The graphical method applies only to problems with **two decision variables**, since the feasible region can be plotted on a two-dimensional plane ($x_1$ vs $x_2$).

**Procedure:**

1. Treat each inequality constraint as an equality and plot the resulting line.
2. Determine the feasible side of each line (test the origin (0,0), or another convenient point, against the original inequality).
3. Identify the **feasible region** — the intersection of all constraint half-planes satisfying non-negativity.
4. Locate the **corner points (vertices)** of the feasible region, including intersections of constraint lines.
5. Evaluate the objective function $Z$ at each corner point.
6. Select the corner point yielding the maximum (or minimum) $Z$ — this is the **optimal solution**, by the **Extreme Point Theorem**: the optimum of a linear objective over a convex polygonal feasible region always occurs at a vertex.

### Solving the Worked Example

**Plotting constraint 1** ($2x_1 + x_2 = 100$): intercepts at $(50, 0)$ and $(0, 100)$.

**Plotting constraint 2** ($x_1 + 2x_2 = 80$): intercepts at $(80, 0)$ and $(0, 40)$.

**Finding the intersection of the two constraints** (solve simultaneously):

$$2x_1 + x_2 = 100$$



$$x_1 + 2x_2 = 80$$

Multiply the second equation by 2: $2x_1 + 4x_2 = 160$. Subtract the first: $3x_2 = 60 \Rightarrow x_2 = 20$. Substitute back: $x_1 = 40$.

**Corner points of the feasible region**: $(0,0)$, $(50,0)$, $(40,20)$, $(0,40)$.

**Evaluating $Z = 40x_1 + 30x_2$ at each vertex:**

| Vertex | $x_1$ | $x_2$ | $Z = 40x_1 + 30x_2$ |
| --- | --- | --- | --- |
| $(0,0)$ | 0 | 0 | 0 |
| $(50,0)$ | 50 | 0 | 2,000 |
| $(40,20)$ | 40 | 20 | 2,200 |
| $(0,40)$ | 0 | 40 | 1,200 |

**Optimal solution**: $x_1 = 40$, $x_2 = 20$, with maximum profit $Z = \$2{,}200$ per week. This means the firm should produce 40 units of Product A and 20 units of Product B, fully using both labor and raw material.

### Diagram: Feasible Region (Graphical Method)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 480">
<text x="320" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">LP Graphical Solution: Feasible Region and Optimum (svg_diagram)</text>
<line x1="70" y1="420" x2="580" y2="420" stroke="#333" stroke-width="2" />
<line x1="70" y1="420" x2="70" y2="60" stroke="#333" stroke-width="2" />
<text x="325" y="450" text-anchor="middle" font-size="13" fill="#333">x1 (Product A units)</text>
<text x="30" y="240" text-anchor="middle" font-size="13" fill="#333" transform="rotate(-90 30 240)">x2 (Product B units)</text>

<line x1="70" y1="70" x2="320" y2="420" stroke="#dc2626" stroke-width="2" />
<text x="335" y="90" font-size="12" fill="#dc2626">2x1 + x2 = 100 (labor)</text>

<line x1="70" y1="210" x2="500" y2="420" stroke="#2563eb" stroke-width="2" />
<text x="380" y="200" font-size="12" fill="#2563eb">x1 + 2x2 = 80 (material)</text>

<polygon points="70,420 320,420 250,315 70,210" fill="#22c55e" fill-opacity="0.25" stroke="none" />

<circle cx="70" cy="420" r="5" fill="#111" />
<text x="55" y="438" font-size="11" fill="#111">(0,0)</text>
<circle cx="320" cy="420" r="5" fill="#111" />
<text x="300" y="438" font-size="11" fill="#111">(50,0)</text>
<circle cx="250" cy="315" r="6" fill="#16a34a" />
<text x="255" y="308" font-size="12" fill="#16a34a" font-weight="bold">Optimum (40,20) Z=2200</text>
<circle cx="70" cy="210" r="5" fill="#111" />
<text x="30" y="205" font-size="11" fill="#111">(0,40)</text>

<text x="130" y="380" font-size="12" fill="`#166534`">Feasible Region</text>

</svg>

### Minimization Problems (Graphical Method Variant)

For minimization problems (e.g., minimizing cost subject to minimum requirement constraints of the form $\ge$), the feasible region is typically **unbounded above**, and the procedure identifies the vertex of the feasible region closest to the origin that satisfies all $\ge$ constraints — evaluated the same way, by comparing $Z$ at each relevant corner point.

### Special Cases in Graphical LP

- **Multiple optimal solutions**: occurs when the objective function line is parallel to a binding constraint — an entire edge of the feasible region yields the same optimal $Z$.
- **Infeasibility**: occurs when constraints conflict and no region satisfies all of them simultaneously (empty feasible region).
- **Unboundedness**: occurs when the feasible region is not closed in the direction of improvement (e.g., a maximization problem with no upper limit constraint), so $Z$ can increase without bound.
- **Redundant constraints**: a constraint that does not affect the shape of the feasible region because it is dominated by another constraint.

### Shadow Price Interpretation (Link to Managerial Decisions)

[Inference] Although formally derived via sensitivity analysis (often introduced alongside or after the simplex method), the graphical solution can illustrate the *shadow price* concept intuitively: at the optimal vertex $(40,20)$, both labor and raw material constraints are binding, meaning each additional unit of labor or material has positive marginal value to the firm, since relaxing either constraint would allow $Z$ to increase.

### Key Points

- LP formulation requires clearly defined decision variables, a linear objective function, and linear constraints with non-negativity conditions.
- The graphical method is limited to two-variable problems; three or more variables require the simplex method or software solvers.
- The optimal solution always lies at a corner point (vertex) of the feasible region — never in the interior.
- Binding constraints (those satisfied with equality at the optimum) reveal which resources are fully utilized and economically scarce.
- Special cases — multiple optima, infeasibility, unboundedness — carry managerial interpretations about the structure of the decision problem.

### Next Steps

- Simplex method for LP problems with more than two decision variables
- Sensitivity analysis and shadow prices (dual values) in LP
- Duality theory in linear programming
- Integer programming and mixed-integer LP for indivisible decision variables
- Application of LP to production planning, product mix, and transportation problems
- Using solver tools (Excel Solver, Python PuLP/SciPy) for LP computation