## Differentiation and Integration for Physics


### Purpose in Physics

Calculus provides the language for describing how physical quantities change. **Differentiation** extracts instantaneous rates of change (velocity from position, force from potential energy), while **integration** accumulates quantities over continuous intervals (displacement from velocity, work from force, mass from density). Nearly every physical law linking two quantities that vary continuously is expressed as a differential or integral relationship.

### Differentiation: Core Rules

For functions $f(x)$ and $g(x)$ with derivatives $f'(x)$, $g'(x)$:

$$\frac{d}{dx}[f \pm g] = f' \pm g' \qquad \text{(Sum Rule)}$$



$$\frac{d}{dx}[fg] = f'g + fg' \qquad \text{(Product Rule)}$$



$$\frac{d}{dx}\left[\frac{f}{g}\right] = \frac{f'g - fg'}{g^2} \qquad \text{(Quotient Rule)}$$



$$\frac{d}{dx}f(g(x)) = f'(g(x))\cdot g'(x) \qquad \text{(Chain Rule)}$$

**Standard derivatives used throughout physics:**

$$\frac{d}{dx}x^n = nx^{n-1}, \qquad \frac{d}{dx}\sin x = \cos x, \qquad \frac{d}{dx}\cos x = -\sin x$$



$$\frac{d}{dx}e^x = e^x, \qquad \frac{d}{dx}\ln x = \frac{1}{x}, \qquad \frac{d}{dx}\tan x = \sec^2 x$$

### Physical Interpretation of the Derivative

The derivative is the instantaneous rate of change — geometrically, the slope of the tangent line; kinematically, the limit of average rate of change over vanishing time intervals:

$$v(t) = \frac{dx}{dt} = \lim_{\Delta t \to 0}\frac{x(t+\Delta t)-x(t)}{\Delta t}$$



$$a(t) = \frac{dv}{dt} = \frac{d^2x}{dt^2}$$

This differentiation chain (position → velocity → acceleration) is the most common application sequence in introductory mechanics. Higher derivatives also appear: **jerk** ($da/dt$) in engineering contexts, though rarely in introductory physics.

### Partial Derivatives

When a physical quantity depends on more than one variable — e.g., temperature $T(x,y,z,t)$ or potential energy $U(x,y,z)$ — the **partial derivative** measures the rate of change with respect to one variable while holding the others fixed:

$$\frac{\partial f}{\partial x}\bigg|_{y,z \text{ fixed}}$$

**Key physics application** — force from potential energy in 3D:

$$\mathbf{F} = -\nabla U = -\left(\frac{\partial U}{\partial x}\hat{i} + \frac{\partial U}{\partial y}\hat{j} + \frac{\partial U}{\partial z}\hat{k}\right)$$

**Total differential**, used in thermodynamics extensively:

$$dU = \frac{\partial U}{\partial x}dx + \frac{\partial U}{\partial y}dy + \frac{\partial U}{\partial z}dz$$

### Taylor Series and Linear Approximation

The **Taylor series** expands a function about a point $x_0$:

$$f(x) = f(x_0) + f'(x_0)(x-x_0) + \frac{f''(x_0)}{2!}(x-x_0)^2 + \cdots$$

**Small-angle and small-displacement approximations**, ubiquitous in physics (e.g., simple pendulum, small oscillations):

$$\sin\theta \approx \theta, \qquad \cos\theta \approx 1 - \frac{\theta^2}{2}, \qquad (1+x)^n \approx 1 + nx \quad (x \ll 1)$$

**Key Points**

- The small-angle approximation for $\sin\theta$ is valid to within about 1% error up to roughly $\theta \approx 0.244$ rad ($\approx 14°$); beyond this the linear approximation breaks down and higher-order terms become necessary. [Unverified: exact error threshold depends on the tolerance specification used.]

### Integration: Core Concepts

Integration is the inverse operation of differentiation (Fundamental Theorem of Calculus) and geometrically represents the area under a curve.

**Indefinite integral** (antiderivative family):

$$\int f(x)\,dx = F(x) + C, \quad \text{where } F'(x) = f(x)$$

**Definite integral** (accumulated quantity between limits):

$$\int_a^b f(x)\,dx = F(b) - F(a)$$

**Standard integrals used in physics:**

$$\int x^n\,dx = \frac{x^{n+1}}{n+1} + C \, (n \neq -1), \qquad \int \frac{1}{x}\,dx = \ln|x| + C$$



$$\int \sin x\,dx = -\cos x + C, \qquad \int \cos x\,dx = \sin x + C, \qquad \int e^x\,dx = e^x + C$$

**Integration techniques**: substitution (reverse chain rule), integration by parts ($\int u\,dv = uv - \int v\,du$), and partial fractions — each has direct physics applications (e.g., integration by parts appears in deriving the work-energy theorem in variable-force problems).

### Physical Interpretation of the Integral

Integrating velocity over time recovers displacement; integrating force over displacement recovers work:

$$\Delta x = \int_{t_1}^{t_2} v(t)\,dt, \qquad W = \int_{x_1}^{x_2} F(x)\,dx$$

This reverses the differentiation chain: position ← velocity ← acceleration, via successive integration with respect to time, each step introducing a constant of integration fixed by initial conditions.

```mermaid
graph LR
    Pos["Position x(t)"] -->|differentiate| Vel["Velocity v(t)"]
    Vel -->|differentiate| Acc["Acceleration a(t)"]
    Acc -->|integrate + IC| Vel
    Vel -->|integrate + IC| Pos
```

### Line, Surface, and Volume Integrals

**Line integral** — work done along a path $C$:

$$W = \int_C \mathbf{F}\cdot d\mathbf{r}$$

**Surface integral** — flux through a surface $S$, central to Gauss's Law:

$$\Phi = \int_S \mathbf{E}\cdot d\mathbf{A}$$

**Volume integral** — total mass from a density distribution:

$$M = \int_V \rho(\mathbf{r})\,dV$$

These multi-dimensional integrals require choosing an appropriate coordinate system (Cartesian, cylindrical, spherical) and corresponding differential element, connecting directly to coordinate transformation techniques.

### Differential Equations in Physics

Many fundamental physics laws are expressed as **differential equations** relating a function to its derivatives:

$$m\frac{d^2x}{dt^2} = -kx \qquad \text{(Simple Harmonic Motion, from Hooke's Law)}$$



$$\frac{dN}{dt} = -\lambda N \qquad \text{(Radioactive Decay)}$$

**Example**

Solving the radioactive decay equation by separation of variables:

$$\frac{dN}{N} = -\lambda\,dt \;\Rightarrow\; \int_{N_0}^{N}\frac{dN'}{N'} = -\lambda\int_0^t dt' \;\Rightarrow\; \ln\left(\frac{N}{N_0}\right) = -\lambda t \;\Rightarrow\; N(t) = N_0 e^{-\lambda t}$$

This separation-of-variables method is the most common technique for solving first-order differential equations encountered in introductory and intermediate physics.

**Common Errors and Misconceptions**

- Confusing average rate of change (secant slope) with instantaneous rate of change (tangent slope, the true derivative)
- Forgetting the constant of integration $C$, which is physically fixed by boundary or initial conditions, not arbitrary in a real problem
- Misapplying the chain rule when a physical quantity depends on time only implicitly through another variable (e.g., $\frac{d}{dt}[x^2] = 2x\dot{x}$, not $2x$)
- Treating partial derivatives as ordinary derivatives when multiple variables are actually changing simultaneously

**Related Topics**

- Vectors and Vector Algebra
- Coordinate Systems and Transformations
- Ordinary Differential Equations: Analytical Solution Methods
- Gradient, Divergence, and Curl
- Simple Harmonic Motion and Oscillations
- Multivariable Calculus and Multiple Integrals
- Series Expansions and Approximation Methods in Physics