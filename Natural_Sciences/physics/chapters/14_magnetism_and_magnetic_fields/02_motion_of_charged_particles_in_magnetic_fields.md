## Motion of Charged Particles in Magnetic Fields


### Recap: Basic Circular Motion

A charged particle moving perpendicular to a uniform $\vec{B}$ field undergoes circular motion due to the magnetic force acting as centripetal force.

$$r = \frac{mv}{qB}, \quad \omega_c = \frac{qB}{m}, \quad T = \frac{2\pi m}{qB}$$

**Key Points**

- These relationships were derived from $qvB = mv^2/r$; see also the treatment under Magnetic Force on Moving Charges
- The period and cyclotron frequency are independent of speed and radius, depending only on the charge-to-mass ratio $q/m$ and field strength $B$
- This section extends beyond the basic circular case to more general and applied particle-motion scenarios

### General Velocity Decomposition

Any velocity can be decomposed into components parallel and perpendicular to $\vec{B}$: $\vec{v} = \vec{v}_\parallel + \vec{v}_\perp$.

**Key Points**

- $\vec{v}_\parallel$ experiences no magnetic force and remains constant, since $\vec{v}_\parallel \times \vec{B} = 0$
- $\vec{v}_\perp$ produces circular motion in the plane perpendicular to $\vec{B}$, with radius $r_\perp = mv_\perp/(qB)$
- The combined motion is a helix with constant pitch $p = v_\parallel T = \dfrac{2\pi m v_\parallel}{qB}$ when $\vec{B}$ is uniform

### Motion in Non-Uniform Magnetic Fields: The Magnetic Mirror

When a charged particle moves into a region of increasing field strength (converging field lines), it can be reflected back — a phenomenon called magnetic mirroring.

**Key Points**

- As $B$ increases along the particle's path, the perpendicular kinetic energy increases while total kinetic energy is conserved (magnetic force does no work), causing $v_\parallel$ to decrease
- If $B$ increases sufficiently, $v_\parallel$ reaches zero and reverses sign, reflecting the particle — this occurs when the particle's **pitch angle** is below a critical value relative to the **loss cone**
- The **magnetic moment** $\mu = \dfrac{\frac{1}{2}mv_\perp^2}{B}$ is an adiabatic invariant (approximately conserved) for slowly varying fields, providing the theoretical basis for mirror confinement — [Inference: "slowly varying" specifically means the field changes negligibly over one gyration period, an assumption central to the adiabatic invariance argument]

### Magnetic Mirror Diagram

```mermaid
graph LR
    A[Weak B region] --> B[Particle spirals inward]
    B --> C[Increasing B region]
    C --> D[v_parallel decreases]
    D --> E[Reflection point]
    E --> F[Particle spirals back]
```

### Magnetic Bottles and Particle Confinement

A magnetic bottle uses two regions of strong field (magnetic mirrors) at opposite ends of a weaker central field region to trap charged particles.

**Key Points**

- Particles with sufficiently large pitch angle (i.e., large $v_\perp$ relative to $v_\parallel$) bounce back and forth between the two mirror points, remaining confined
- Particles within the **loss cone** (small pitch angle, large $v_\parallel$ relative to $v_\perp$) escape through the weak-field ends rather than being reflected
- Magnetic bottles are foundational to certain magnetic confinement fusion concepts, though tokamak designs (using toroidal rather than linear mirror geometry) have become more prominent in fusion research — [Unverified: relative research emphasis and specific confinement performance figures change over time as fusion research progresses]

### Van Allen Radiation Belts (Natural Magnetic Bottle)

**Key Points**

- Earth's dipole magnetic field naturally forms a magnetic bottle configuration, trapping charged particles (primarily protons and electrons) from the solar wind and cosmic rays
- Trapped particles exhibit three characteristic motions simultaneously: rapid gyration around field lines, bouncing between magnetic mirror points near the poles, and slow longitudinal drift around Earth
- This drift arises from gradient and curvature effects in the non-uniform dipole field, distinct from the simple $E\times B$ drift described below

### Combined Electric and Magnetic Fields: $E \times B$ Drift

When uniform, mutually perpendicular electric and magnetic fields are both present, a charged particle undergoes cycloidal motion superimposed with a steady drift velocity.

$$\vec{v}_{drift} = \frac{\vec{E}\times\vec{B}}{B^2}$$

**Key Points**

- Remarkably, this drift velocity is independent of the particle's charge, mass, and initial velocity — both positive and negative charges drift in the same direction at the same speed
- This drift arises because, in the reference frame moving at $\vec{v}_{drift}$, the electric field vanishes, leaving pure circular motion in that frame — transforming back to the lab frame adds the drift velocity to the circular motion
- Applications include the velocity selector (a special case where an initial velocity exactly matching $v_{drift}$ passes through undeflected) and plasma confinement devices

### Velocity Selector Revisited

For a particle to pass through crossed $E$ and $B$ fields undeflected, the electric and magnetic forces must balance exactly:

$$qE = qv_0B \implies v_0 = \frac{E}{B}$$

**Example**

A velocity selector uses $E = 2\times10^4\,\text{V/m}$ and $B = 0.4\,\text{T}$. Find the selected velocity.

$$v_0 = \frac{E}{B} = \frac{2\times10^4}{0.4} = 5\times10^4\,\text{m/s}$$

Only particles moving at this exact speed pass through undeflected; faster or slower particles are deflected by the net unbalanced force and are blocked by apertures in practical designs.

### Mass Spectrometry: Combining Selection and Deflection

**Key Points**

- Ions are first accelerated through a known potential difference, then passed through a velocity selector, then deflected in a separate magnetic field region where circular motion radius depends on mass-to-charge ratio
- Combining $qV = \frac{1}{2}mv^2$ (acceleration stage) with $r = mv/(qB)$ (deflection stage) allows solving for $m/q$ given measured $r$
- This technique enables precise determination of isotopic masses and relative abundances, foundational to modern analytical chemistry and nuclear physics — [Inference: modern mass spectrometers often use more sophisticated designs, such as time-of-flight or quadrupole analyzers, but the magnetic sector design illustrates the core underlying physics]

### Worked Example: Mass Spectrometer Calculation

**Example**

An ion of charge $q = 1.6\times10^{-19}\,\text{C}$ is accelerated through a potential difference of $2000\,\text{V}$, then enters a magnetic field of $B = 0.3\,\text{T}$ and follows a circular path of radius $r = 0.15\,\text{m}$. Find the ion's mass.

From acceleration: $qV = \frac{1}{2}mv^2 \implies v = \sqrt{\dfrac{2qV}{m}}$

From circular motion: $r = \dfrac{mv}{qB} \implies v = \dfrac{rqB}{m}$

Setting these equal and solving for $m$:

$$\frac{rqB}{m} = \sqrt{\frac{2qV}{m}} \implies \frac{r^2q^2B^2}{m^2} = \frac{2qV}{m} \implies m = \frac{r^2qB^2}{2V}$$



$$m = \frac{(0.15)^2(1.6\times10^{-19})(0.3)^2}{2(2000)}$$



$$m = \frac{(0.0225)(1.6\times10^{-19})(0.09)}{4000} = \frac{3.24\times10^{-22}}{4000} \approx 8.1\times10^{-26}\,\text{kg}$$

### Relativistic Considerations at High Speed

**Key Points**

- At speeds approaching a significant fraction of the speed of light, relativistic momentum $p = \gamma m v$ (where $\gamma = 1/\sqrt{1-v^2/c^2}$) must replace classical momentum in the radius formula: $r = \gamma m v/(qB)$
- The cyclotron frequency becomes speed-dependent at relativistic speeds ($\omega_c = qB/(\gamma m)$), unlike the constant classical cyclotron frequency — this has practical implications for particle accelerator design (e.g., necessitating synchrocyclotrons or synchrotrons rather than simple fixed-frequency cyclotrons at high energy) — [Inference: the specific threshold at which relativistic corrections become significant depends on the required precision of the application]
- Kinetic energy at relativistic speeds is $KE = (\gamma - 1)mc^2$, rather than the classical $\frac{1}{2}mv^2$

### Practical Applications Summary

**Key Points**

- **Particle accelerators**: cyclotrons, synchrotrons, and related devices rely on precise control of charged particle trajectories using combined and time-varying magnetic (and electric) fields
- **Plasma physics and fusion research**: magnetic mirrors, bottles, and toroidal confinement geometries all depend on the principles of charged particle motion in non-uniform fields
- **Space physics**: Van Allen belt dynamics and auroral phenomena arise directly from charged particle motion in Earth's non-uniform magnetic field
- **Analytical instrumentation**: mass spectrometers and related devices exploit precise, predictable charged-particle trajectories for chemical and isotopic analysis

### Common Pitfalls

**Key Points**

- Assuming particle motion remains purely circular in non-uniform fields — this only holds strictly for uniform $\vec{B}$; non-uniform fields introduce drift and mirroring effects
- Forgetting that $\vec{E}\times\vec{B}$ drift velocity is independent of charge sign and magnitude, leading to the mistaken assumption that positive and negative particles would separate under this drift alone
- Neglecting relativistic corrections when analyzing high-energy particle motion, leading to inaccurate radius or frequency predictions at significant fractions of the speed of light

**Related Topics**

- Magnetic Force on Moving Charges
- Magnetic Fields Due to Currents (Biot-Savart Law)
- Plasma Confinement and Fusion Concepts
- Special Relativity and Relativistic Dynamics
- Particle Accelerator Design
- Earth's Magnetosphere and Space Weather