## Rolling Motion


### Overview: Rolling as Combined Translation and Rotation

Rolling motion describes objects (wheels, balls, cylinders) that simultaneously translate (their center of mass moves through space) and rotate (about their own center of mass). The defining kinematic feature of **rolling without slipping** is that the contact point between the object and the surface is instantaneously at rest relative to that surface.

**Key Points**

- Rolling motion combines two independently analyzable components: translational motion of the center of mass and rotational motion about the center of mass.
- "Rolling without slipping" is a kinematic *constraint*, not automatically satisfied — it requires sufficient static friction to prevent relative sliding at the contact point.
- If the constraint is violated, the object either slips (skids, as when a car wheel spins on ice) or the analysis must account for kinetic friction instead.

### The Rolling Without Slipping Constraint

The fundamental kinematic relationship linking translational and rotational quantities for rolling without slipping:

$$v_{cm} = R\omega$$



$$a_{cm} = R\alpha$$

Where $R$ is the radius of the rolling object.

**Derivation logic**: the contact point's velocity is the vector sum of the center of mass velocity (translation) and the rotational velocity of that point about the center of mass. For the contact point to be instantaneously at rest:

$$v_{contact} = v_{cm} - R\omega = 0 \implies v_{cm} = R\omega$$

**Key Points**

- This constraint applies at every instant during rolling without slipping, linking linear and angular kinematics throughout the motion.
- The constraint does *not* imply the entire object is at rest — only the single instantaneous contact point has zero velocity relative to the ground.

### Instantaneous Velocity Distribution in Rolling

A rolling object exhibits a characteristic velocity pattern across different points:

- **Contact point**: $v = 0$ (instantaneously at rest)
- **Center of mass**: $v = v_{cm} = R\omega$
- **Top point**: $v = 2v_{cm} = 2R\omega$ (twice the center-of-mass speed)

This can be understood by viewing rolling as **pure rotation about the instantaneous contact point** (the "instantaneous axis of rotation"), where every point's speed is $v = r'\omega$, with $r'$ being that point's distance from the contact point.

### Velocity Distribution Diagram (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 480 280">
<title>Velocity Distribution in Rolling Motion (svg_diagram)</title>
<rect x="0" y="0" width="480" height="280" fill="#ffffff" />
<line x1="20" y1="240" x2="460" y2="240" stroke="#555" stroke-width="3" />
<circle cx="240" cy="150" r="90" fill="#dbe9f6" stroke="#1f77b4" stroke-width="2" />
<circle cx="240" cy="150" r="4" fill="#333" />
<circle cx="240" cy="240" r="4" fill="#d62728" />
<text x="240" y="260" font-size="12" text-anchor="middle" fill="#d62728">Contact: v = 0</text>
<line x1="240" y1="150" x2="330" y2="150" stroke="#2ca02c" stroke-width="3" marker-end="url(#arrowC)" />
<text x="335" y="145" font-size="12" fill="#2ca02c">v_cm</text>
<line x1="240" y1="60" x2="420" y2="60" stroke="#9467bd" stroke-width="3" marker-end="url(#arrowT)" />
<text x="345" y="50" font-size="12" fill="#9467bd">v_top = 2·v_cm</text>
</svg>

### Energy Methods for Rolling Motion

Total kinetic energy of a rolling object combines translational and rotational contributions:

$$KE_{total} = \frac{1}{2}Mv_{cm}^2 + \frac{1}{2}I_{cm}\omega^2$$

Applying the rolling constraint $\omega = v_{cm}/R$:

$$KE_{total} = \frac{1}{2}Mv_{cm}^2\left(1 + \frac{I_{cm}}{MR^2}\right)$$

For an object rolling down an incline of height $h$ from rest, energy conservation gives:

$$Mgh = \frac{1}{2}Mv_{cm}^2\left(1+\frac{I_{cm}}{MR^2}\right) \implies v_{cm} = \sqrt{\frac{2gh}{1+I_{cm}/(MR^2)}}$$

**Key Points**

- Static friction does **no work** on a rolling-without-slipping object, since the contact point has zero velocity — the friction force acts, but through zero displacement at each instant, so energy conservation (excluding friction losses) applies directly.
- Objects with smaller $I_{cm}/(MR^2)$ ratios convert more gravitational PE to translational KE and reach the bottom of an incline faster, independent of mass or radius.

### Dynamics of Rolling Down an Incline (Force/Torque Method)

An alternative to energy methods uses Newton's second law (translational) combined with the rotational equation about the center of mass. For an object of mass $M$, radius $R$, moment of inertia $I_{cm}$, rolling down an incline of angle $\theta$:

**Translational equation** (along incline, taking down-slope as positive):

$$Mg\sin\theta - f = Ma_{cm}$$

**Rotational equation** (about center of mass, friction provides the torque):

$$fR = I_{cm}\alpha = I_{cm}\frac{a_{cm}}{R}$$

Solving these two equations simultaneously (eliminating $f$):

$$a_{cm} = \frac{g\sin\theta}{1 + I_{cm}/(MR^2)}$$



$$f = \frac{I_{cm}/(MR^2)}{1+I_{cm}/(MR^2)}Mg\sin\theta$$

**Key Points**

- Friction is essential to rolling without slipping down an incline — without it, the object would simply slide without rotating (frictionless case), and $a_{cm} = g\sin\theta$ instead.
- The required friction force depends on the object's moment of inertia distribution; objects with larger $I_{cm}/(MR^2)$ require more friction to maintain rolling without slipping.
- This is **static** friction (assuming no slipping occurs), and it does no work — it does not dissipate energy, unlike kinetic friction in a slipping scenario.

### Example: Rolling Cylinder Down an Incline

A solid cylinder ($I_{cm} = \frac{1}{2}MR^2$) rolls without slipping down a $30°$ incline. Find its acceleration and the minimum coefficient of static friction required.

$$a_{cm} = \frac{g\sin\theta}{1+1/2} = \frac{g\sin(30°)}{1.5} = \frac{(9.8)(0.5)}{1.5} \approx 3.27 \text{ m/s}^2$$



$$f = \frac{1/2}{1.5}Mg\sin\theta = \frac{1}{3}Mg\sin(30°) = \frac{1}{3}(0.5)Mg \approx 0.167Mg$$

Normal force: $N = Mg\cos\theta = Mg\cos(30°) \approx 0.866Mg$

$$\mu_{min} = \frac{f}{N} = \frac{0.167Mg}{0.866Mg} \approx 0.192$$

Any coefficient of static friction at or above approximately 0.192 will maintain rolling without slipping for this cylinder at this incline angle.

### Comparing Rolling Objects (Race Down an Incline)

For objects with the same mass and radius but different $I_{cm}/(MR^2)$ ratios released simultaneously from the same height:

| Object | $I_{cm}/(MR^2)$ | $a_{cm} = g\sin\theta/(1+I_{cm}/MR^2)$ | Relative rank (fastest to slowest) |
| --- | --- | --- | --- |
| Solid sphere | 2/5 | $\frac{5}{7}g\sin\theta$ | 1st |
| Solid cylinder | 1/2 | $\frac{2}{3}g\sin\theta$ | 2nd |
| Thin spherical shell | 2/3 | $\frac{3}{5}g\sin\theta$ | 3rd |
| Thin hoop | 1 | $\frac{1}{2}g\sin\theta$ | 4th (slowest) |

**Key Points**

- The result is **independent of mass and radius** — only the shape (via $I_{cm}/(MR^2)$) determines relative rolling acceleration.
- This is a frequently demonstrated result in physics classrooms: a solid sphere always outraces a hollow sphere, cylinder, or hoop down an incline, regardless of their individual sizes or masses (assuming rolling without slipping throughout).

### Rolling With Slipping

If insufficient friction is available (or the object is given an initial spin/slide that doesn't match $v=R\omega$), the object slips, and **kinetic friction** applies instead of static friction:

$$f_k = \mu_kN$$

In this regime, $v_{cm} \neq R\omega$ initially, and kinetic friction acts to bring the object toward the rolling-without-slipping condition over time (friction decelerates translational slipping and simultaneously changes $\omega$ via torque) until $v_{cm} = R\omega$ is eventually satisfied, after which the object rolls without slipping (if friction remains sufficient) or continues slipping (if it does not).

**Key Points**

- During slipping, kinetic friction **does** do work (nonzero relative sliding at the contact point), dissipating mechanical energy as heat — unlike the no-slip case.
- A classic example is a bowling ball initially sliding (thrown with no spin) that gradually begins to roll purely due to friction, eventually reaching pure rolling motion partway down the lane.
- Spinning wheels on ice, or a car "burning rubber," are situations where kinetic friction dominates due to insufficient traction for rolling without slipping.

### Example: Ball Thrown with No Initial Spin

A ball of radius $R$, moment of inertia $I_{cm} = \frac{2}{5}MR^2$, is thrown onto a surface with initial velocity $v_0$ and zero initial angular velocity ($\omega_0 = 0$). Kinetic friction $f_k = \mu_k Mg$ acts until rolling without slipping begins. Find the velocity when pure rolling begins.

**Translational**: $Ma = -f_k \implies a = -\mu_kg$, so $v(t) = v_0 - \mu_kgt$

**Rotational**: $I_{cm}\alpha = f_kR \implies \alpha = \frac{\mu_kMgR}{\frac{2}{5}MR^2} = \frac{5\mu_kg}{2R}$, so $\omega(t) = \frac{5\mu_kg}{2R}t$

Rolling without slipping begins when $v(t) = R\omega(t)$:

$$v_0 - \mu_kgt = R\cdot\frac{5\mu_kg}{2R}t = \frac{5\mu_kg}{2}t$$



$$v_0 = \mu_kgt\left(1+\frac{5}{2}\right) = \frac{7}{2}\mu_kgt \implies t = \frac{2v_0}{7\mu_kg}$$



$$v_{roll} = v_0 - \mu_kg\cdot\frac{2v_0}{7\mu_kg} = v_0 - \frac{2v_0}{7} = \frac{5v_0}{7}$$

The ball's velocity decreases to $\frac{5}{7}v_0$ once pure rolling begins, with the remaining kinetic energy having been converted between translational and rotational forms (with some dissipated as heat during the slipping phase).

### Problem-Solving Procedure

```mermaid
flowchart TD
    A[Determine if rolling without slipping is assumed or given] --> B{Rolling without slipping confirmed?}
    B -- Yes --> C{Energy conservation applicable? No other energy losses?}
    C -- Yes --> D[Use KE_total = ½Mv_cm² + ½I_cm*omega² with v_cm = R*omega]
    C -- No / need forces --> E[Use Newton's 2nd law translational + rotational equations simultaneously]
    B -- No, slipping occurs --> F[Use kinetic friction f_k = mu_k*N; solve v(t) and omega(t) separately]
    D --> G[Solve for final speed or height]
    E --> G
    F --> H[Find time/condition when v_cm = R*omega for transition to rolling]
    H --> G
```

### Rolling and Angular Momentum About the Contact Point

An alternative approach uses angular momentum about the (instantaneous) contact point, which can simplify problems by eliminating the unknown friction force from torque equations (since friction acts at the contact point itself, producing zero torque about that point):

$$\tau_{contact} = \frac{dL_{contact}}{dt}$$

Using $L_{contact} = I_{cm}\omega + Mv_{cm}R$ (parallel axis theorem applied to angular momentum) and $\tau_{contact} = MgR\sin\theta$ (gravity's torque about the contact point), this method yields the same acceleration result as the combined translational-rotational approach, often with less algebra. [Inference: this technique is a standard simplification in intermediate mechanics courses; its use may vary depending on curriculum level and problem complexity.]

### Applications

**Key Points**

- **Vehicle dynamics**: tire rolling resistance, traction control, and anti-lock braking systems rely on distinguishing rolling-without-slipping from slipping conditions.
- **Sports**: bowling ball dynamics transitioning from sliding to rolling; ball sports involving rolling balls (billiards, golf putting).
- **Mechanical engineering**: rollers, bearings, and gear systems are designed around rolling-without-slipping principles to minimize frictional energy loss.
- **Robotics**: wheeled robot locomotion and odometry calculations depend on the rolling constraint $v = R\omega$ to relate wheel rotation to distance traveled.
- **Railway engineering**: train wheel-rail interaction analysis, including flange contact and rolling resistance.

### Common Misconceptions

**Key Points**

- Rolling without slipping does not mean there is no friction — static friction is typically present and necessary to maintain the constraint, even though it does no work.
- The contact point having zero velocity does not mean the whole object is momentarily stationary — only that single point, at that single instant, has zero velocity relative to the ground.
- A rolling object does not necessarily have the same acceleration as a frictionless sliding object down the same incline — rolling objects always accelerate more slowly due to the diversion of energy into rotational KE.
- "No slipping" is a kinematic assumption that must be verified (via the required friction not exceeding $\mu_sN$) — it cannot simply be assumed valid for any friction coefficient or incline angle without checking.

### Conclusion

Rolling motion combines translational motion of an object's center of mass with rotation about that center of mass, linked by the kinematic constraint $v_{cm}=R\omega$ when no slipping occurs. Both energy methods and combined Newton's-law/torque methods provide consistent tools for analyzing rolling dynamics, revealing that an object's moment of inertia distribution (not its mass or size) determines its rolling acceleration down an incline — a principle with wide-ranging applications from vehicle engineering to sports science.

**Next Steps**

- Angular momentum conservation and its role in rolling/collision transitions
- Moment of inertia review for various rolling object geometries
- Gyroscopic motion and precession (advanced rotational topic)
- Torque and rotational equilibrium in static rolling scenarios
- Rotational kinetic energy and the work-energy theorem for rotation
- Combined rolling and collision problems (e.g., billiard ball dynamics)