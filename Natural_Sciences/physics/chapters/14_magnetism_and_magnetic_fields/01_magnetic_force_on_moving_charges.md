## Magnetic Force on Moving Charges

### The Lorentz Force Law

The magnetic force on a moving charged particle is given by:

$$\vec{F} = q\vec{v} \times \vec{B}$$

Where $q$ is the charge (C), $\vec{v}$ is velocity (m/s), and $\vec{B}$ is magnetic field (tesla, T).

**Key Points**

- The force is always perpendicular to both the velocity and the magnetic field, as a consequence of the cross product
- A stationary charge experiences no magnetic force, regardless of field strength, since $\vec{v} = 0$
- The complete Lorentz force, including electric field contribution, is $\vec{F} = q\vec{E} + q\vec{v}\times\vec{B}$

### Magnitude of the Magnetic Force

$$F = qvB\sin\theta$$

Where $\theta$ is the angle between $\vec{v}$ and $\vec{B}$.

**Key Points**

- Force is maximum ($F = qvB$) when velocity is perpendicular to the field ($\theta = 90°$)
- Force is zero when velocity is parallel or antiparallel to the field ($\theta = 0°$ or $180°$), since $\sin\theta = 0$ in both cases
- The SI unit of magnetic field, the tesla, is defined such that $1\,\text{T} = 1\,\dfrac{\text{N}}{\text{A}\cdot\text{m}} = 1\,\dfrac{\text{kg}}{\text{A}\cdot\text{s}^2}$

### Direction: The Right-Hand Rule

**Key Points**

- Point the fingers of the right hand in the direction of $\vec{v}$, curl them toward $\vec{B}$; the thumb points in the direction of $\vec{v}\times\vec{B}$
- For a **positive** charge, the force is in the direction of $\vec{v}\times\vec{B}$; for a **negative** charge, the force is reversed (opposite direction)
- An alternative "flat hand" version: fingers point along $\vec{v}$, curl toward $\vec{B}$, thumb gives force direction for a positive charge

### Right-Hand Rule Illustration (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 500 350">
<text x="250" y="25" text-anchor="middle" font-size="16" font-weight="bold" fill="#222">Lorentz Force Direction (svg_diagram)</text>
<line x1="100" y1="200" x2="350" y2="200" stroke="#c0392b" stroke-width="3" />
<polygon points="350,200 335,192 335,208" fill="#c0392b" />
<text x="360" y="205" font-size="14" fill="#c0392b">v</text>
<g>
<circle cx="225" cy="130" r="2" fill="#2980b9" />
<circle cx="225" cy="160" r="2" fill="#2980b9" />
<circle cx="225" cy="190" r="2" fill="#2980b9" />
<circle cx="225" cy="220" r="2" fill="#2980b9" />
<circle cx="225" cy="250" r="2" fill="#2980b9" />
<circle cx="175" cy="130" r="2" fill="#2980b9" />
<circle cx="175" cy="160" r="2" fill="#2980b9" />
<circle cx="175" cy="190" r="2" fill="#2980b9" />
<circle cx="175" cy="220" r="2" fill="#2980b9" />
<circle cx="175" cy="250" r="2" fill="#2980b9" />
<circle cx="275" cy="130" r="2" fill="#2980b9" />
<circle cx="275" cy="160" r="2" fill="#2980b9" />
<circle cx="275" cy="190" r="2" fill="#2980b9" />
<circle cx="275" cy="220" r="2" fill="#2980b9" />
<circle cx="275" cy="250" r="2" fill="#2980b9" />
</g>
<text x="380" y="130" font-size="14" fill="#2980b9">B (out of page)</text>
<line x1="225" y1="200" x2="225" y2="90" stroke="#27ae60" stroke-width="3" />
<polygon points="225,90 217,105 233,105" fill="#27ae60" />
<text x="235" y="95" font-size="14" fill="#27ae60">F (positive charge)</text>
</svg>

### Circular Motion in a Uniform Magnetic Field

When a charged particle moves perpendicular to a uniform magnetic field, the magnetic force provides centripetal acceleration, resulting in circular motion.

$$qvB = \frac{mv^2}{r}$$

Solving for the radius:

$$r = \frac{mv}{qB}$$

**Key Points**

- Since the magnetic force is always perpendicular to velocity, it changes direction but never speed, meaning the magnetic force does no work on the particle
- The period of circular motion is independent of speed: $T = \dfrac{2\pi r}{v} = \dfrac{2\pi m}{qB}$, a property exploited in cyclotron design
- The corresponding angular frequency, $\omega_c = \dfrac{qB}{m}$, is called the **cyclotron frequency**

### Worked Example: Radius of Circular Motion

**Example**

An electron ($q = 1.6\times10^{-19}\,\text{C}$, $m = 9.11\times10^{-31}\,\text{kg}$) moves at $v = 2\times10^6\,\text{m/s}$ perpendicular to a magnetic field of $B = 0.5\,\text{T}$. Find the radius of its circular path.

$$r = \frac{mv}{qB} = \frac{(9.11\times10^{-31})(2\times10^6)}{(1.6\times10^{-19})(0.5)}$$



$$r = \frac{1.822\times10^{-24}}{8\times10^{-20}} \approx 2.28\times10^{-5}\,\text{m}$$

This is approximately $22.8\,\mu\text{m}$, illustrating the very tight curvature typical of electron trajectories in laboratory-scale magnetic fields.

### Helical Motion

When velocity has a component both parallel and perpendicular to $\vec{B}$, the resulting motion is helical.

**Key Points**

- The parallel velocity component is unaffected by the magnetic force (since $\sin\theta = 0$ along that component), producing uniform motion along the field direction
- The perpendicular component produces circular motion, as described above
- The combination produces a helical path with constant pitch, tracing a spiral around the field lines — this behavior underlies the trapping of charged particles in magnetic mirror configurations and Earth's Van Allen radiation belts

### Force on a Current-Carrying Wire

For a current-carrying conductor in a magnetic field, treating the aggregate effect of many moving charges:

$$\vec{F} = I\vec{L} \times \vec{B}$$

Where $I$ is current, and $\vec{L}$ is a vector along the wire in the direction of conventional current flow, with magnitude equal to the wire's length in the field.

$$F = BIL\sin\theta$$

**Key Points**

- This follows directly from summing the Lorentz force over all charge carriers in the wire: $F = nqv_dAL \cdot B\sin\theta = I L B \sin\theta$, using $I = nqv_dA$
- Maximum force occurs when the wire is perpendicular to the field; zero force occurs when the wire is parallel to the field
- This principle underlies the operation of electric motors, loudspeakers, and galvanometers

### Worked Example: Force on a Wire

**Example**

A straight wire of length $0.5\,\text{m}$ carries a current of $3\,\text{A}$, oriented perpendicular to a magnetic field of $0.2\,\text{T}$.

$$F = BIL\sin(90°) = (0.2)(3)(0.5)(1) = 0.3\,\text{N}$$

### The Hall Effect

When a current-carrying conductor is placed in a magnetic field perpendicular to the current, charge carriers experience a sideways deflecting force, creating a measurable transverse voltage (the Hall voltage).

$$V_H = \frac{IB}{nqt}$$

Where $t$ is the conductor's thickness and $n$ is charge carrier density.

**Key Points**

- The Hall effect provides a method for determining the sign of majority charge carriers in a material (electrons vs. holes), which is particularly important in semiconductor characterization
- Hall effect sensors are widely used in practical applications: current sensors, position and speed sensors, and magnetic field measurement devices
- The polarity of the Hall voltage reverses depending on whether charge carriers are positive or negative, providing a direct experimental method to distinguish carrier type

### Applications of Magnetic Force on Charges

**Key Points**

- **Mass spectrometers**: use the radius of circular motion in a known magnetic field to determine the mass-to-charge ratio of ions, enabling chemical and isotopic analysis
- **Cyclotrons and particle accelerators**: exploit the speed-independent period of circular motion to accelerate charged particles using a synchronized alternating electric field across successive orbits
- **Velocity selectors**: combine perpendicular electric and magnetic fields such that their forces balance only for a specific velocity ($qE = qvB$, giving $v = E/B$), allowing selection of particles with a specific speed
- **Cathode ray tubes and magnetic lenses**: use magnetic fields to steer and focus electron beams, historically important in older television and oscilloscope displays, and still used in electron microscopy

### Common Pitfalls

**Key Points**

- Forgetting that the magnetic force does no work on a charged particle, since it is always perpendicular to velocity — this means kinetic energy (and speed) remain constant under a purely magnetic force
- Misapplying the right-hand rule for negative charges — the force direction must be reversed relative to what the right-hand rule gives directly for $\vec{v}\times\vec{B}$
- Confusing the cyclotron radius formula's dependence on momentum ($mv$) rather than velocity alone, which matters when comparing particles of different mass or when relativistic effects become significant — [Inference: at speeds approaching the speed of light, relativistic momentum $\gamma m v$ must replace classical momentum in the radius formula]

**Next Steps**

- Magnetic Fields Due to Currents (Biot-Savart Law)
- Ampère's Law and Applications
- Electromagnetic Induction and Faraday's Law
- Motors and Generators
- The Hall Effect in Semiconductor Physics
- Charged Particle Motion in Combined Fields