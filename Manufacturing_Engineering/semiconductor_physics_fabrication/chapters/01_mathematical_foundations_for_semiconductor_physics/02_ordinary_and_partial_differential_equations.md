## Ordinary and Partial Differential Equations


### Overview and Relevance to Semiconductor Physics

Differential equations are the language in which the governing physics of semiconductor devices is expressed. Carrier transport, electrostatics, heat flow, and quantum confinement are all formulated as ordinary differential equations (ODEs) or partial differential equations (PDEs). Device simulators (TCAD tools) at their core are numerical PDE solvers coupling Poisson's equation, the continuity equations, and (in quantum-corrected models) the Schrödinger equation. Understanding the classification, boundary conditions, and solution methods for these equations is prerequisite to interpreting or building any semiconductor device model.

### Ordinary Differential Equations: Fundamentals

**Key Points**

- An ODE involves derivatives of a function of a single independent variable, e.g., $\dfrac{dy}{dx} = f(x, y)$.
- Order is defined by the highest derivative present; linearity depends on whether the equation is linear in the unknown function and its derivatives.
- A **linear, constant-coefficient, homogeneous** ODE of order $n$ has a general solution built from exponentials $e^{rx}$, where $r$ are roots of the characteristic polynomial.
- Boundary value problems (BVPs) specify conditions at two (or more) points, contrasted with initial value problems (IVPs), which specify all conditions at one point.

**Example: Depletion Region Electric Field**

In the depletion approximation of a p-n junction, Poisson's equation reduces to a 1D ODE:

$$\frac{d^2\phi}{dx^2} = -\frac{\rho(x)}{\varepsilon_s}$$

With $\rho(x) = -qN_A$ in the p-side depletion region and $\rho(x) = qN_D$ in the n-side, integrating twice with the boundary conditions $\phi(-x_p) = 0$ (or a reference) and continuity of $\phi$ and $d\phi/dx$ (up to surface charge) at the junction yields the classic parabolic potential profile and triangular electric field profile of the depletion approximation.

### Second-Order Linear ODEs: The Quantum Harmonic Oscillator Pattern

A recurring ODE structure in semiconductor physics is the time-independent Schrödinger equation in 1D:

$$-\frac{\hbar^2}{2m^*}\frac{d^2\psi}{dx^2} + V(x)\psi(x) = E\psi(x)$$

This is a second-order linear ODE (eigenvalue problem in function space). For a quantum well with $V(x) = 0$ inside and $V(x) = V_0$ outside, this becomes a piecewise-constant-coefficient ODE:

- Inside the well: $\psi'' + k^2\psi = 0$, with $k = \sqrt{2m^*E}/\hbar$, giving oscillatory solutions $\sin(kx)$, $\cos(kx)$.
- Outside the well (for $E < V_0$): $\psi'' - \kappa^2\psi = 0$, with $\kappa = \sqrt{2m^*(V_0-E)}/\hbar$, giving decaying exponential solutions $e^{-\kappa|x|}$.

Matching $\psi$ and $\psi'$ at the boundaries (continuity conditions) yields a transcendental equation whose roots give the discrete confined energy levels—this is the standard finite square well problem.

### Partial Differential Equations: Classification

**Key Points**

PDEs involve derivatives with respect to multiple independent variables. The general second-order linear PDE in two variables,

$$A\frac{\partial^2 u}{\partial x^2} + B\frac{\partial^2 u}{\partial x \partial y} + C\frac{\partial^2 u}{\partial y^2} + \ldots = 0$$

is classified by the discriminant $B^2 - 4AC$:

| Type | Discriminant | Prototype Equation | Semiconductor Example |
| --- | --- | --- | --- |
| Elliptic | $B^2 - 4AC < 0$ | Laplace/Poisson: $\nabla^2\phi = -\rho/\varepsilon$ | Electrostatic potential in a device |
| Parabolic | $B^2 - 4AC = 0$ | Diffusion: $\partial u/\partial t = D\nabla^2 u$ | Dopant diffusion, minority carrier diffusion, heat equation |
| Hyperbolic | $B^2 - 4AC > 0$ | Wave equation: $\partial^2 u/\partial t^2 = c^2\nabla^2 u$ | Ballistic/wave transport, some hydrodynamic transport models |

This classification determines what boundary/initial conditions are well-posed and which numerical schemes are stable.

### Poisson's Equation (Elliptic PDE)

**Key Points**

- Governs the electrostatic potential $\phi(\mathbf{r})$ given a charge distribution: $\nabla \cdot (\varepsilon \nabla \phi) = -\rho$.
- In semiconductors, $\rho = q(p - n + N_D^+ - N_A^-)$, where $p, n$ are hole/electron concentrations and $N_D^+, N_A^-$ are ionized dopant concentrations.
- Boundary conditions: Dirichlet (fixed potential, e.g., ohmic contacts with $\phi$ set by applied bias and built-in potential) or Neumann (fixed normal field, e.g., $\partial\phi/\partial n = 0$ at insulating/symmetry boundaries).
- This is the central "electrostatics" equation self-consistently coupled to carrier equations in device simulation.

**Example: 1D Poisson in a Simple Capacitor-like Region**

For a uniform charge density $\rho_0$ between two grounded plates at $x=0$ and $x=L$:

$$\varepsilon\frac{d^2\phi}{dx^2} = -\rho_0$$

Integrating twice: $\phi(x) = -\dfrac{\rho_0}{2\varepsilon}x^2 + C_1 x + C_2$. Applying $\phi(0)=0$ gives $C_2=0$; applying $\phi(L)=0$ gives $C_1 = \dfrac{\rho_0 L}{2\varepsilon}$, yielding the parabolic potential profile $\phi(x) = \dfrac{\rho_0}{2\varepsilon}x(L-x)$.

### Continuity Equations and the Diffusion Equation (Parabolic PDE)

**Key Points**

Carrier transport in the drift-diffusion framework combines the continuity equation with the drift-diffusion current relation. For electrons:

$$\frac{\partial n}{\partial t} = \frac{1}{q}\nabla \cdot J_n + G - R$$



$$J_n = q\mu_n n E + qD_n \nabla n$$

Combining these (and using the Einstein relation $D_n = \mu_n k_B T / q$) yields a parabolic PDE for $n(\mathbf{r}, t)$ that reduces, in field-free regions, to the classic diffusion equation:

$$\frac{\partial n}{\partial t} = D_n \nabla^2 n + G - R$$

**Example: Minority Carrier Diffusion in Steady State**

In the quasi-neutral region of a p-n diode under steady-state, low-injection conditions with no generation, the excess minority electron concentration $\delta n(x)$ in the p-region satisfies:

$$D_n \frac{d^2 \delta n}{dx^2} - \frac{\delta n}{\tau_n} = 0$$

This is a linear, constant-coefficient, second-order ODE (steady-state reduces the PDE to an ODE in space). The general solution is:

$$\delta n(x) = A e^{-x/L_n} + B e^{x/L_n}, \quad L_n = \sqrt{D_n \tau_n}$$

where $L_n$ is the **diffusion length**. With boundary conditions $\delta n(0) = \delta n(0)$ (junction edge value from the law of the junction) and $\delta n(\infty) \to 0$ (long-base diode), $B=0$, giving the standard exponentially decaying minority carrier profile that underlies the ideal diode equation derivation.

### The Wave Equation and Hyperbolic Transport (Hyperbolic PDE)

**Key Points**

- Relevant to hydrodynamic and ballistic transport models where inertia of the carrier "fluid" is retained (unlike drift-diffusion, which neglects momentum relaxation dynamics).
- Also underlies the time-dependent Schrödinger equation's propagative character: $i\hbar \dfrac{\partial \psi}{\partial t} = \hat{H}\psi$, which, despite being first-order in time, exhibits wave-like propagation due to the imaginary unit coupling real and imaginary parts of $\psi$.
- Hyperbolic equations propagate information at finite speed along characteristic curves, relevant when transit-time effects or high-frequency response cannot be neglected (e.g., RF/mmWave device modeling).

### Time-Independent vs. Time-Dependent Schrödinger Equation

**Key Points**

| Equation | Type | Role |
| --- | --- | --- |
| $\hat{H}\psi = E\psi$ | Eigenvalue ODE/PDE (elliptic-like) | Stationary states, energy levels, band structure |
| $i\hbar \partial\psi/\partial t = \hat{H}\psi$ | First-order-in-time PDE | Time evolution, wave packet dynamics, transient quantum transport |

The time-independent equation is obtained from the time-dependent one via separation of variables $\psi(\mathbf{r},t) = \psi(\mathbf{r})e^{-iEt/\hbar}$, converting a PDE in space and time into a spatial eigenvalue ODE/PDE plus a trivial temporal phase factor—directly connecting this topic to eigenvalue problems.

### Boundary and Initial Conditions in Device Physics

**Key Points**

- **Dirichlet conditions**: value of the function fixed at the boundary (e.g., potential fixed at ohmic contacts, wavefunction $\psi=0$ at an infinite barrier).
- **Neumann conditions**: derivative (flux) fixed at the boundary (e.g., zero current flow at an insulating boundary, $\partial\phi/\partial n = 0$ at a symmetry plane).
- **Robin (mixed) conditions**: a linear combination of value and derivative (e.g., surface recombination velocity boundary condition: $D_n \dfrac{d(\delta n)}{dx}\Big|_{surface} = S_n \,\delta n(surface)$).
- Well-posedness (existence, uniqueness, stability of the solution) depends on matching the correct type and number of conditions to the PDE's classification.

### Numerical Solution Methods

**Key Points**

Analytical solutions exist only for idealized/simplified geometries and material profiles; real device simulation requires discretization:

- **Finite Difference Method (FDM)**: approximates derivatives with difference quotients on a structured grid; straightforward for simple (often rectangular) domains such as 1D depletion approximations or simple quantum well structures.
- **Finite Element Method (FEM)**: discretizes the domain into elements (triangles/tetrahedra) with local basis functions; handles complex device geometries and is standard in commercial TCAD tools.
- **Finite Volume Method (FVM)**: enforces conservation laws (like continuity equations) exactly over discrete control volumes; widely used for drift-diffusion carrier transport because it naturally preserves current continuity.
- Discretizing a PDE via any of these methods converts it into either a linear system $A\mathbf{x}=\mathbf{b}$ (for linear PDEs like Poisson's equation) or an eigenvalue problem $H\mathbf{v} = \lambda\mathbf{v}$ (for the Schrödinger equation), directly connecting this topic to linear algebra methods.

[Inference] The specific choice of discretization scheme and its stability properties (e.g., Scharfetter-Gummel discretization for drift-diffusion current terms) can depend on the device regime and simulator implementation; results may vary across tools.

### The Self-Consistent Schrödinger-Poisson System

**Example**

In quantum-confined structures (quantum wells, nanowire channels, MOSFET inversion layers), the electrostatic potential and the quantum-mechanical carrier distribution are coupled:

1. Solve the Schrödinger equation (elliptic eigenvalue PDE) for wavefunctions $\psi_i(x)$ and energies $E_i$ given a trial potential $\phi(x)$.
2. Compute carrier density $n(x) = \sum_i |\psi_i(x)|^2 \cdot (\text{occupation via Fermi-Dirac statistics})$.
3. Solve Poisson's equation (elliptic PDE) for an updated $\phi(x)$ using this $n(x)$.
4. Iterate until self-consistency (convergence) is reached.

This iterative loop is the standard method for simulating quantum confinement effects in modern MOSFET inversion layers and quantum well/quantum dot heterostructures.

**Diagram: Self-Consistent Schrödinger-Poisson Loop**

```mermaid
flowchart TD
    A[Initial guess: potential phi(x)] --> B[Solve Schrodinger equation: eigenvalue PDE]
    B --> C[Obtain wavefunctions psi_i and energies E_i]
    C --> D[Compute carrier density n(x) via Fermi-Dirac occupation]
    D --> E[Solve Poisson equation: elliptic PDE for updated phi(x)]
    E --> F{Converged?}
    F -->|No| B
    F -->|Yes| G[Final self-consistent potential and carrier profile]
```

### Illustration: ODE Boundary Value Problem in a Depletion Region

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 600 340" font-family="sans-serif">
<text x="300" y="25" font-size="16" text-anchor="middle" fill="#222">Depletion Region Field and Potential (svg_diagram)</text>

<line x1="60" y1="290" x2="560" y2="290" stroke="#333" stroke-width="1.5" />
<line x1="310" y1="290" x2="310" y2="50" stroke="#999" stroke-width="1" stroke-dasharray="3,3" />
<text x="300" y="310" font-size="12" text-anchor="middle" fill="#333">x</text>
<text x="150" y="310" font-size="11" text-anchor="middle" fill="#333">p-side (-xp)</text>
<text x="470" y="310" font-size="11" text-anchor="middle" fill="#333">n-side (xn)</text>


<text x="120" y="60" font-size="12" fill="`#1a5fb4`">E(x)</text>

<path d="M 120 200 L 310 110 L 500 200" stroke="`#1a5fb4`" stroke-width="2.5" fill="none" />

<line x1="120" y1="200" x2="500" y2="200" stroke="`#1a5fb4`" stroke-width="1" stroke-dasharray="4,3" />



<text x="120" y="255" font-size="12" fill="`#c01c28`">phi(x)</text>

<path d="M 120 270 Q 310 230 310 190 Q 310 150 500 105" stroke="`#c01c28`" stroke-width="2.5" fill="none" />


<line x1="120" y1="200" x2="120" y2="290" stroke="#666" stroke-width="1" stroke-dasharray="2,2" />
<line x1="500" y1="200" x2="500" y2="290" stroke="#666" stroke-width="1" stroke-dasharray="2,2" />
</svg>

### Common Pitfalls and Clarifications

**Key Points**

- Conflating the steady-state (time-independent) and transient (time-dependent) forms of the continuity/diffusion equations: setting $\partial n/\partial t = 0$ converts a PDE into a spatial-only ODE, valid only under steady-state assumptions.
- Applying drift-diffusion (parabolic, non-inertial) models in regimes where carrier transit times are comparable to momentum relaxation times, where hyperbolic/hydrodynamic or ballistic (Boltzmann transport equation) models are more appropriate—an important limitation for nanoscale devices.
- Mismatched boundary conditions (e.g., specifying two Dirichlet conditions for a first-order ODE, or omitting a needed condition at infinity) render the problem ill-posed or non-unique.
- The linear approximation of Poisson's equation near equilibrium is only valid for small perturbations; large-bias or high-injection conditions require the fully nonlinear, self-consistently coupled Poisson-continuity system, typically solved with Newton-Raphson iteration in TCAD tools.

### Related Topics

- Linear algebra and eigenvalue problems
- Fourier analysis and reciprocal space methods
- Numerical methods: finite difference and finite element methods
- Drift-diffusion and hydrodynamic transport models
- Schrödinger-Poisson self-consistent simulation
- Boltzmann transport equation and semiclassical transport
- Perturbation theory and variational methods
- Boundary value problems in electrostatics