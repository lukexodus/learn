## Rotational Kinematics


### Angular Position, Displacement, and the Radian

Rotational kinematics describes the motion of rotating objects using angular analogs of the linear quantities (position, velocity, acceleration). Angular position is measured in **radians**, the natural unit relating arc length to radius:

$$\theta = \frac{s}{r}$$

Where $s$ is arc length traveled and $r$ is the radius. One full revolution corresponds to $2\pi$ radians ($360°$).

$$\theta_{rad} = \theta_{deg}\times\frac{\pi}{180}$$

**Angular displacement** is the change in angular position:

$$\Delta\theta = \theta_f - \theta_i$$

**Key Points**

- Radians are dimensionless (a ratio of lengths), which is why they can be dropped or inserted freely in equations without unit conversion factors.
- Angular displacement is treated as a vector for infinitesimal rotations, with direction given by the right-hand rule (along the rotation axis); for finite rotations about different axes, angular displacements do not commute and are not true vectors. [Inference: this subtlety is typically introduced only in more advanced treatments; introductory courses generally treat rotation about a single fixed axis, where the vector treatment is unambiguous.]

### Angular Velocity

Angular velocity ($\omega$) is the rate of change of angular position:

$$\omega_{avg} = \frac{\Delta\theta}{\Delta t}, \qquad \omega = \frac{d\theta}{dt}$$

Units: radians per second (rad/s). Direction is along the rotation axis (right-hand rule: curl fingers in direction of rotation, thumb points along $\vec{\omega}$).

**Relation to period and frequency:**

$$\omega = \frac{2\pi}{T} = 2\pi f$$

Where $T$ is the period (time for one revolution) and $f$ is frequency (revolutions per second, Hz).

### Angular Acceleration

Angular acceleration ($\alpha$) is the rate of change of angular velocity:

$$\alpha_{avg} = \frac{\Delta\omega}{\Delta t}, \qquad \alpha = \frac{d\omega}{dt} = \frac{d^2\theta}{dt^2}$$

Units: radians per second squared (rad/s²).

**Key Points**

- Positive $\alpha$ in the same direction as $\omega$ means the rotation is speeding up; opposite signs mean it is slowing down.
- $\alpha = 0$ does not mean $\omega = 0$ — it means angular velocity is constant (uniform rotation).

### Relationship Between Linear and Angular Quantities

For a point at distance $r$ from the rotation axis:

$$s = r\theta$$



$$v = r\omega \quad \text{(tangential speed)}$$



$$a_t = r\alpha \quad \text{(tangential acceleration)}$$



$$a_c = \frac{v^2}{r} = \omega^2 r \quad \text{(centripetal acceleration)}$$

**Key Points**

- Tangential acceleration ($a_t$) changes the *speed* of the point; centripetal acceleration ($a_c$) changes the *direction* of velocity, always pointing toward the rotation axis.
- Total linear acceleration magnitude: $a = \sqrt{a_t^2 + a_c^2}$.
- All points on a rigid, rotating body share the same $\omega$ and $\alpha$, but linear speed $v$ and acceleration vary with distance $r$ from the axis.

### Tangential and Centripetal Components (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 400 400">
<title>Tangential and Centripetal Acceleration Components (svg_diagram)</title>
<rect x="0" y="0" width="400" height="400" fill="#ffffff" />
<circle cx="200" cy="200" r="120" fill="none" stroke="#999" stroke-width="1.5" stroke-dasharray="4,3" />
<circle cx="200" cy="200" r="4" fill="#333" />
<circle cx="320" cy="200" r="8" fill="#1f77b4" />
<line x1="200" y1="200" x2="320" y2="200" stroke="#333" stroke-width="1.5" />
<text x="260" y="190" font-size="12" fill="#333">r</text>
<line x1="320" y1="200" x2="320" y2="120" stroke="#d62728" stroke-width="3" marker-end="url(#arrowR)" />
<text x="330" y="150" font-size="12" fill="#d62728">a_t (tangential)</text>
<line x1="320" y1="200" x2="250" y2="200" stroke="#2ca02c" stroke-width="3" marker-end="url(#arrowG)" />
<text x="240" y="220" font-size="12" fill="#2ca02c" text-anchor="end">a_c (centripetal)</text>
</svg>

### Kinematic Equations for Constant Angular Acceleration

Directly analogous to the linear (translational) kinematic equations, with $\theta \leftrightarrow x$, $\omega \leftrightarrow v$, $\alpha \leftrightarrow a$:

$$\omega_f = \omega_i + \alpha t$$



$$\theta_f = \theta_i + \omega_i t + \frac{1}{2}\alpha t^2$$



$$\omega_f^2 = \omega_i^2 + 2\alpha(\theta_f - \theta_i)$$



$$\theta_f = \theta_i + \frac{1}{2}(\omega_i + \omega_f)t$$

**Key Points**

- These equations apply **only** when angular acceleration is constant, exactly like their linear counterparts.
- Sign conventions must be consistent: choose a positive rotational direction (commonly counterclockwise) and apply it uniformly to $\theta$, $\omega$, and $\alpha$.

### Linear-Angular Analogy Table

| Linear Quantity | Symbol | Angular Quantity | Symbol | Relation |
| --- | --- | --- | --- | --- |
| Position | $x$ | Angular position | $\theta$ | $x = r\theta$ |
| Velocity | $v$ | Angular velocity | $\omega$ | $v = r\omega$ |
| Acceleration | $a$ | Angular acceleration | $\alpha$ | $a_t = r\alpha$ |
| Mass | $m$ | Moment of inertia | $I$ | $I = \sum m_ir_i^2$ |
| Force | $F$ | Torque | $\tau$ | $\tau = rF\sin\theta$ |
| Momentum | $p$ | Angular momentum | $L$ | $L = I\omega$ |
| Kinetic energy | $\frac{1}{2}mv^2$ | Rotational KE | $\frac{1}{2}I\omega^2$ | — |

### Example: Spinning Wheel with Constant Angular Acceleration

A wheel starts at rest and accelerates uniformly to $\omega_f = 20$ rad/s in $t = 4$ s. Find $\alpha$ and the number of revolutions completed.

$$\alpha = \frac{\omega_f - \omega_i}{t} = \frac{20 - 0}{4} = 5 \text{ rad/s}^2$$



$$\theta_f = \omega_i t + \frac{1}{2}\alpha t^2 = 0 + \frac{1}{2}(5)(4)^2 = 40 \text{ rad}$$



$$\text{Revolutions} = \frac{40}{2\pi} \approx 6.37 \text{ rev}$$

### Example: Point on a Rotating Disk

A disk of radius 0.3 m rotates at a constant $\omega = 10$ rad/s. Find the tangential speed and centripetal acceleration of a point on its rim.

$$v = r\omega = (0.3)(10) = 3 \text{ m/s}$$



$$a_c = \omega^2 r = (10)^2(0.3) = 30 \text{ m/s}^2$$

Since $\omega$ is constant, $\alpha = 0$, so $a_t = 0$ and total acceleration is purely centripetal: $a = 30$ m/s², directed toward the disk's center.

### Example: Non-Uniform Angular Acceleration (Calculus-Based)

A rotating object has angular velocity given by $\omega(t) = 3t^2 - 2t$ (rad/s). Find angular acceleration at $t = 2$ s and total angular displacement from $t=0$ to $t=2$ s.

$$\alpha(t) = \frac{d\omega}{dt} = 6t - 2 \implies \alpha(2) = 6(2)-2 = 10 \text{ rad/s}^2$$



$$\theta(2) - \theta(0) = \int_0^2 (3t^2 - 2t)\, dt = \left[t^3 - t^2\right]_0^2 = (8-4) - 0 = 4 \text{ rad}$$

This demonstrates that when angular acceleration is not constant, the standard kinematic equations do not apply, and calculus (integration/differentiation) must be used directly.

### Problem-Solving Procedure

```mermaid
flowchart TD
    A[Identify known angular quantities: theta, omega, alpha, t] --> B{Is angular acceleration constant?}
    B -- Yes --> C[Select appropriate kinematic equation matching knowns/unknowns]
    B -- No --> D[Use calculus: integrate/differentiate omega(t) or alpha(t)]
    C --> E[Solve for unknown angular quantity]
    D --> E
    E --> F{Need linear quantities at a point on the body?}
    F -- Yes --> G[Apply v = r*omega, a_t = r*alpha, a_c = omega^2*r]
    F -- No --> H[Report angular result directly]
    G --> H
```

### Rolling Without Slipping

A special and common kinematic constraint relates the rotational motion of a round object to its translational motion when it rolls without slipping:

$$v_{cm} = r\omega$$



$$a_{cm} = r\alpha$$

**Key Points**

- This constraint means the contact point of the rolling object with the ground is instantaneously at rest relative to the ground.
- Rolling without slipping requires sufficient friction; if this condition is violated, the object slips or skids, and $v_{cm} \neq r\omega$.
- This relationship bridges rotational kinematics with translational motion, essential for analyzing wheels, balls, and cylinders rolling down inclines.

### Applications

**Key Points**

- **Engineering**: gear systems, flywheels, turbines, and motor shafts are analyzed using rotational kinematics to determine speed, acceleration, and displacement relationships.
- **Astronomy**: planetary rotation and orbital angular velocity calculations.
- **Vehicle dynamics**: wheel rotation rates relative to vehicle speed, tire slip analysis.
- **Sports**: analyzing spin rates of balls (baseballs, golf balls, discus) and rotational motion of gymnasts/divers.
- **Robotics**: joint and motor control systems rely on precise angular position, velocity, and acceleration tracking.

### Common Misconceptions

**Key Points**

- A constant angular speed ($\omega$) does not mean zero acceleration — centripetal acceleration is still present for any point off the rotation axis, since velocity direction is continuously changing.
- All points on a rigid rotating body share the same $\omega$ and $\alpha$, but **not** the same linear velocity or acceleration — these depend on distance from the axis ($r$).
- Radians must be used (not degrees) in the standard kinematic equations and in relations like $v = r\omega$; using degrees introduces an incorrect scaling factor.
- Rotational kinematic equations require constant angular acceleration, exactly as their linear counterparts require constant linear acceleration — they cannot be applied blindly to non-uniform rotational motion.

### Conclusion

Rotational kinematics provides a complete parallel framework to linear kinematics, describing angular position, velocity, and acceleration using directly analogous equations. The connection between angular and linear quantities via $r$ allows rotational motion to be translated into tangential and centripetal linear effects at any point on a rotating body, forming the foundation for rotational dynamics, torque, and angular momentum analysis.

**Next Steps**

- Torque and the rotational analog of Newton's second law ($\tau = I\alpha$)
- Moment of inertia calculations for various rigid body shapes
- Rotational kinetic energy and the work-energy theorem for rotation
- Angular momentum and its conservation
- Rolling motion combining translational and rotational dynamics
- Precession and gyroscopic motion (advanced topic)