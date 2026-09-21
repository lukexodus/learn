## Classical Mechanics and Lagrangian Formulation


### Overview and Relevance to Semiconductor Physics

Classical mechanics — particularly its Lagrangian and Hamiltonian reformulations — establishes the conceptual and mathematical scaffolding later inherited by quantum mechanics and semiclassical transport theory in semiconductors. The Hamiltonian formulation directly generalizes to the quantum Hamiltonian operator used in the Schrödinger equation; Hamilton's equations of motion in phase space form the basis of the semiclassical carrier transport model (velocity and force equations used in the Boltzmann transport equation and Monte Carlo device simulation); and the concept of generalized coordinates and conjugate momenta underlies crystal momentum and the effective mass approximation.

### Newtonian Mechanics: Starting Point

**Key Points**

- Newton's second law, $\mathbf{F} = m\mathbf{a} = m\ddot{\mathbf{r}}$, is a second-order ODE (or system of ODEs) in Cartesian coordinates, directly connecting to the ODE methods discussed elsewhere in this chapter.
- Newtonian mechanics becomes cumbersome for systems with constraints (e.g., motion restricted to a surface or curve) or when working in non-Cartesian coordinates, motivating the more general Lagrangian and Hamiltonian formulations.
- In semiconductor transport, the semiclassical electron acceleration theorem, $\hbar \dfrac{d\mathbf{k}}{dt} = \mathbf{F}_{ext} = -q\mathbf{E} - q\mathbf{v}\times\mathbf{B}$, is a direct analogue of Newton's second law with crystal momentum $\hbar\mathbf{k}$ replacing ordinary momentum, forming the basis of drift and Hall-effect calculations in semiconductors.

### Generalized Coordinates and Degrees of Freedom

**Key Points**

- **Generalized coordinates** $q_i$ are any set of independent parameters that fully specify a system's configuration; they need not be Cartesian and can incorporate constraints directly (e.g., an angle for constrained rotational motion), simplifying the mathematical treatment of constrained systems.
- The number of generalized coordinates equals the system's number of degrees of freedom.
- **Generalized velocities** $\dot{q}_i$ are simply the time derivatives of the generalized coordinates.

### The Lagrangian Formulation

**Key Points**

The **Lagrangian** is defined as the difference between kinetic energy $T$ and potential energy $V$:

$$L(q_i, \dot{q}_i, t) = T - V$$

The dynamics of the system are governed by the **Euler-Lagrange equations**, one for each generalized coordinate:

$$\frac{d}{dt}\left(\frac{\partial L}{\partial \dot{q}_i}\right) - \frac{\partial L}{\partial q_i} = 0$$

These equations are derived from **Hamilton's principle of least (stationary) action**: the true trajectory of a system extremizes the action integral $S = \int_{t_1}^{t_2} L\,dt$ among all possible paths connecting fixed endpoints. This variational formulation — extremizing a functional rather than directly integrating a force law — is a conceptual precursor to the variational methods used extensively in quantum mechanics (e.g., variational approximations to ground-state energies in quantum wells and molecular/solid-state electronic structure).

### Worked Example: Simple Harmonic Oscillator via Lagrangian Mechanics

**Example**

For a 1D particle of mass $m$ in a harmonic potential $V(x) = \frac{1}{2}kx^2$:

$$L = \frac{1}{2}m\dot{x}^2 - \frac{1}{2}kx^2$$

Applying the Euler-Lagrange equation:

$$\frac{\partial L}{\partial \dot{x}} = m\dot{x}, \quad \frac{d}{dt}(m\dot{x}) = m\ddot{x}, \quad \frac{\partial L}{\partial x} = -kx$$



$$m\ddot{x} - (-kx) = 0 \implies m\ddot{x} + kx = 0$$

This recovers the familiar simple harmonic oscillator equation, with the same characteristic frequency $\omega = \sqrt{k/m}$ that reappears (in quantized form, $E_n = \hbar\omega(n+1/2)$) in the quantum harmonic oscillator model used to approximate confined states near a potential minimum, such as phonon modes in a crystal lattice.

### The Hamiltonian Formulation

**Key Points**

The **Hamiltonian** is obtained from the Lagrangian via a Legendre transformation, introducing the **canonical (conjugate) momentum** $p_i = \partial L/\partial \dot{q}_i$:

$$H(q_i, p_i, t) = \sum_i p_i \dot{q}_i - L$$

For most physical systems (kinetic energy quadratic in velocities, potential energy velocity-independent), $H = T + V$, the total mechanical energy. The equations of motion take the symmetric first-order form known as **Hamilton's equations**:

$$\dot{q}_i = \frac{\partial H}{\partial p_i}, \quad \dot{p}_i = -\frac{\partial H}{\partial q_i}$$

This formulation is of central importance to semiconductor physics because the **quantum Hamiltonian operator** used throughout this course (e.g., $\hat{H} = -\dfrac{\hbar^2}{2m}\nabla^2 + V(\mathbf{r})$ in the Schrödinger equation) is constructed by direct analogy with — and via canonical quantization of — the classical Hamiltonian $H(q,p)$, replacing $p \to -i\hbar\nabla$.

### Canonical Momentum and Crystal Momentum

**Key Points**

- For a charged particle in an electromagnetic field, the canonical momentum is $\mathbf{p} = m\mathbf{v} + q\mathbf{A}$ (not simply $m\mathbf{v}$), where $\mathbf{A}$ is the vector potential — this distinction becomes important when analyzing electron dynamics in a magnetic field (e.g., cyclotron motion, quantum Hall effect) in semiconductors.
- **Crystal momentum** $\hbar\mathbf{k}$, introduced via Bloch's theorem, is conceptually and mathematically analogous to canonical momentum: it is conserved (up to reciprocal lattice vectors) in a periodic potential precisely because the periodic potential possesses discrete translational symmetry, an application of **Noether's theorem** (continuous/discrete symmetries correspond to conserved quantities) inherited directly from the Lagrangian/Hamiltonian framework.
- The semiclassical group velocity of an electron in a band, $\mathbf{v}_g = \dfrac{1}{\hbar}\nabla_{\mathbf{k}} E(\mathbf{k})$, is the direct semiconductor-physics analogue of Hamilton's equation $\dot{q} = \partial H/\partial p$, with crystal momentum $\hbar\mathbf{k}$ playing the role of canonical momentum and the band energy $E(\mathbf{k})$ playing the role of the Hamiltonian.

### Phase Space and Liouville's Theorem

**Key Points**

- **Phase space** is the space of all $(q_i, p_i)$ pairs; a system's state at any instant is a single point in phase space, and its time evolution traces a trajectory governed by Hamilton's equations.
- **Liouville's theorem** states that the phase-space volume occupied by an ensemble of trajectories is conserved under Hamiltonian time evolution (phase-space flow is incompressible), a foundational result for classical statistical mechanics.
- This concept underlies the **semiclassical Boltzmann transport equation** used to model carrier transport in semiconductors, which describes the evolution of a carrier distribution function $f(\mathbf{r}, \mathbf{k}, t)$ in the phase space of position and crystal momentum, with the collisionless (drift) term structurally derived from Liouville's theorem applied to crystal-momentum phase space.

### Poisson Brackets and the Correspondence to Quantum Commutators

**Key Points**

The **Poisson bracket** of two classical dynamical variables $f(q,p)$ and $g(q,p)$ is defined as:

$$\{f,g\} = \sum_i \left(\frac{\partial f}{\partial q_i}\frac{\partial g}{\partial p_i} - \frac{\partial f}{\partial p_i}\frac{\partial g}{\partial q_i}\right)$$

The fundamental Poisson bracket relation $\{q_i, p_j\} = \delta_{ij}$ is the classical precursor to the quantum canonical commutation relation $[\hat{q}_i, \hat{p}_j] = i\hbar\delta_{ij}$, obtained via the **canonical quantization** correspondence $\{f,g\} \to \dfrac{1}{i\hbar}[\hat{f},\hat{g}]$. This correspondence is the formal mathematical bridge connecting classical mechanics (this topic) to the quantum mechanical formalism used throughout the rest of the semiconductor physics curriculum.

### Constrained Systems and Lagrange Multipliers

**Key Points**

- For systems with explicit constraints $g(q_i) = 0$ (e.g., motion confined to a surface), the constrained Euler-Lagrange equations are obtained by introducing a **Lagrange multiplier** $\lambda$ and extremizing the modified Lagrangian $L' = L + \lambda g(q_i)$.
- This mathematical technique (Lagrange multipliers for constrained extremization) reappears directly in quantum mechanical variational methods, such as enforcing wavefunction normalization ($\int|\psi|^2 = 1$) as a constraint while minimizing the energy expectation value in variational or Hartree-Fock/DFT self-consistent field calculations — a direct methodological inheritance from classical Lagrangian mechanics.

### Diagram: From Classical Mechanics to Semiconductor Transport

```mermaid
flowchart TD
    A[Lagrangian L = T - V] -- Legendre transform --> B[Hamiltonian H = T + V]
    B -- canonical quantization, p to -i*hbar*grad --> C[Quantum Hamiltonian operator: Schrodinger equation]
    B -- Hamilton's equations --> D[Classical phase space q(t), p(t)]
    D -- Bloch theorem, crystal momentum hbar*k --> E[Semiclassical carrier dynamics: v_g = 1/hbar * dE/dk]
    D -- Liouville theorem --> F[Boltzmann transport equation: f(r,k,t)]
    A -- Lagrange multipliers, constrained extremization --> G[Variational methods: wavefunction normalization constraint]
```

### Illustration: Action Extremization Among Candidate Paths

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 560 320" font-family="sans-serif">
<text x="280" y="25" font-size="16" text-anchor="middle" fill="#222">Stationary Action Principle (svg_diagram)</text>

<line x1="60" y1="270" x2="500" y2="270" stroke="#333" stroke-width="1.5" />
<line x1="60" y1="270" x2="60" y2="50" stroke="#333" stroke-width="1.5" />
<text x="280" y="295" font-size="12" text-anchor="middle" fill="#333">time t</text>
<text x="30" y="160" font-size="12" text-anchor="middle" fill="#333" transform="rotate(-90 30 160)">q(t)</text>

<circle cx="100" cy="230" r="5" fill="#222" />
<circle cx="460" cy="120" r="5" fill="#222" />
<text x="100" y="250" font-size="10" text-anchor="middle" fill="#333">t1, q1</text>
<text x="460" y="105" font-size="10" text-anchor="middle" fill="#333">t2, q2</text>

<path d="M 100 230 Q 280 130 460 120" stroke="#1a5fb4" stroke-width="3" fill="none" />
<text x="330" y="140" font-size="11" fill="#1a5fb4">True path (stationary S)</text>

<path d="M 100 230 Q 280 80 460 120" stroke="#c01c28" stroke-width="1.5" fill="none" stroke-dasharray="5,4" />
<path d="M 100 230 Q 280 200 460 120" stroke="#c01c28" stroke-width="1.5" fill="none" stroke-dasharray="5,4" />
<text x="330" y="70" font-size="10" fill="#c01c28">Varied paths (higher/lower S)</text>
</svg>

### Common Pitfalls and Clarifications

**Key Points**

- Confusing canonical momentum with ordinary kinetic momentum: in the presence of a vector potential (magnetic field), these differ by $q\mathbf{A}$, and using the wrong one in quantization or in Hamilton's equations produces incorrect results, particularly relevant to semiconductor magnetotransport and quantum Hall physics.
- Assuming the Hamiltonian always equals total energy $T+V$: this holds only when the generalized coordinates are time-independent and kinetic energy is a purely quadratic function of velocities; in more general or moving-frame formulations, $H$ can differ from the total mechanical energy.
- Misapplying Noether's theorem: a conserved quantity arises from a continuous symmetry of the *Lagrangian* (or action), not merely a symmetry of the potential alone; correctly identifying the relevant symmetry (e.g., discrete lattice translation leading to crystal momentum conservation up to a reciprocal lattice vector) requires care.
- Treating the classical-to-quantum correspondence (Poisson bracket to commutator) as a strict derivation: [Inference] canonical quantization is generally understood as a heuristic correspondence rather than a rigorous derivation, and can be ambiguous (ordering ambiguities) for classical expressions involving products of non-commuting quantum operators, requiring additional physical input to resolve in general.

### Related Topics

- Quantum mechanics postulates and the Schrödinger equation
- Electromagnetism and Maxwell's equations
- Crystal momentum and Bloch's theorem
- Boltzmann transport equation and semiclassical transport
- Variational methods in quantum mechanics
- Statistical mechanics and phase-space distribution functions
- Ordinary and partial differential equations
- Cyclotron motion and the quantum Hall effect