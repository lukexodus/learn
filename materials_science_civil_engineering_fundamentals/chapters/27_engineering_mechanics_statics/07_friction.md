## Friction


### Definition and Scope

Friction is the resistive force that develops tangent to two surfaces in contact, opposing relative sliding motion (or the tendency toward relative sliding) between them. In statics, friction is treated primarily through the **Coulomb (dry) friction model**, which provides a simplified, empirically-based relationship between the normal force pressing two surfaces together and the maximum tangential force the surfaces can resist before slipping occurs. Friction analysis extends the standard equilibrium framework by introducing an additional force component at contact surfaces that was previously idealized as frictionless in earlier topics.

### Coulomb Friction Model

**Static Friction**

When two surfaces are in contact but not sliding relative to each other, the friction force $F$ is whatever value is necessary to maintain equilibrium, up to a maximum limiting value:

$$F \leq F_{max} = \mu_s N$$

where $\mu_s$ is the **coefficient of static friction** (a dimensionless, empirically determined property of the specific surface pair) and $N$ is the normal (perpendicular) contact force between the surfaces.

**Key Points:**

- Static friction is **self-adjusting**: below the limiting value, the actual friction force is determined by the equilibrium requirements of the problem (i.e., whatever value satisfies $\sum F = 0$), not automatically equal to $\mu_s N$ unless the body is on the verge of slipping.
- **Impending motion** describes the critical condition where the body is on the verge of sliding, at which point $F = F_{max} = \mu_s N$ exactly — this is the condition typically analyzed in statics problems asking for the maximum load, angle, or force before slipping begins.

**Kinetic (Sliding) Friction**

Once relative sliding motion has actually begun, the friction force is given by:

$$F_k = \mu_k N$$

where $\mu_k$ is the **coefficient of kinetic friction**.

**Key Points:**

- Empirically, $\mu_k$ is generally somewhat lower than $\mu_s$ for the same surface pair — meaning it typically takes slightly more force to initiate sliding than to sustain it once already moving, a widely observed characteristic of the Coulomb friction model. [Inference: the specific magnitude of the difference between $\mu_s$ and $\mu_k$ varies considerably by material pair and surface condition; some material combinations show only a small or negligible difference.]
- Both $\mu_s$ and $\mu_k$ are **empirical properties** dependent on the specific pair of materials in contact, surface roughness, cleanliness, and (in some cases) the presence of lubrication or contamination — they are not intrinsic properties of a single material alone, but of the specific interface between two particular surfaces.

### Angle of Friction and Friction Cone

At the point of impending motion, the resultant of the normal force $N$ and the limiting friction force $F_{max}$ makes an angle $\phi_s$ (the **angle of static friction**) with the normal to the surface:

$$\tan\phi_s = \mu_s$$

**Key Points:**

- This geometric interpretation is useful for graphical/vector-based friction problems: the resultant contact force must lie within a cone (in 3D) or a wedge (in 2D) of half-angle $\phi_s$ measured from the surface normal, for the body to remain in equilibrium without slipping.
- If an applied force's resultant direction (combined with gravity/other loads) would require the contact reaction to lie **outside** this friction cone/wedge, slipping must occur — this provides an alternative geometric solution method to the standard algebraic equilibrium-plus-friction-inequality approach.

### Standard Problem Types

**1. Block on a Horizontal or Inclined Surface**

The most fundamental friction problem: determining whether a block remains stationary under an applied force, or finding the minimum/maximum force or angle at which slipping begins.

**Worked Example: Block on Horizontal Surface**

A block of weight $W = 200$ N rests on a horizontal surface with $\mu_s = 0.35$. A horizontal force $P$ is applied. Find the maximum $P$ before the block begins to slide.

$$\sum F_y = 0: \quad N - W = 0 \implies N = 200 \text{ N}$$



$$F_{max} = \mu_s N = 0.35 \times 200 = 70 \text{ N}$$

At impending motion, $\sum F_x = 0: \quad P - F_{max} = 0 \implies P_{max} = 70 \text{ N}$

**Worked Example: Block on Inclined Plane (Impending Slip)**

A block rests on a plane inclined at angle $\theta$ to the horizontal, with $\mu_s = 0.30$. Find the angle $\theta$ at which the block is on the verge of sliding down the incline under its own weight alone (no other applied force).

Resolving weight into components parallel and perpendicular to the incline:

$$\sum F_{\perp} = 0: \quad N - W\cos\theta = 0 \implies N = W\cos\theta$$



$$\sum F_{\parallel} = 0 \text{ (at impending slip)}: \quad W\sin\theta - \mu_s N = 0$$

Substituting:

$$W\sin\theta = \mu_s W\cos\theta \implies \tan\theta = \mu_s$$



$$\theta = \tan^{-1}(0.30) = 16.7°$$

**Key Points:** This result — that the impending-slip angle on an incline under self-weight alone equals $\tan^{-1}(\mu_s)$ — is identical in form to the angle of static friction $\phi_s$ derived above, illustrating that these two concepts (limiting incline angle and friction angle) are geometrically and physically equivalent expressions of the same underlying friction limit.

**2. Wedges**

Wedges are simple machines relying on friction (combined with a shallow angle) to hold a load in place or to provide mechanical advantage in lifting/adjusting heavy objects. Wedge analysis typically involves drawing separate FBDs for the wedge and the object it supports, applying equilibrium to each while accounting for friction at each contact surface (which may involve two or more friction surfaces simultaneously, e.g., a wedge sliding between a fixed surface and a load).

**Key Points:** A wedge is described as **self-locking** if it remains in place under load without requiring a continuously applied force to prevent it from sliding back out — this occurs when the wedge angle is sufficiently shallow relative to the friction angle at its contact surfaces, following the same $\tan\theta \leq \mu_s$-type relationship as the inclined block case, applied to the wedge's specific geometry.

**3. Screws (Square-Threaded)**

A square-threaded screw (as used in jacks, clamps, and power screws) can be analyzed as a special case of the wedge/inclined-plane principle "wrapped" around a cylinder, where the thread's helix angle plays the role of the incline angle.

$$M = Fr\tan(\phi_s + \alpha) \quad \text{(tightening, raising a load)}$$



$$M = Fr\tan(\phi_s - \alpha) \quad \text{(loosening, lowering a load, if } \phi_s > \alpha\text{)}$$

where $M$ is the applied moment/torque, $F$ is the axial load, $r$ is the mean thread radius, $\alpha$ is the helix (lead) angle of the thread, and $\phi_s = \tan^{-1}(\mu_s)$ is the friction angle at the thread surface.

**Key Points:** A screw is **self-locking** (will not loosen/back out under load without an actively applied loosening torque) when $\phi_s \geq \alpha$ — i.e., when the friction angle at the thread surface is at least as large as the thread's helix angle, directly analogous to the self-locking wedge condition.

**4. Belt Friction**

For a flexible belt, rope, or cable wrapped around a fixed cylindrical drum or pulley (as in belt drives, hoisting systems, or a rope wrapped around a post/capstan), the ratio of tension on the "tight side" to the "slack side" at impending slip is governed by the belt friction equation:

$$\frac{T_1}{T_2} = e^{\mu_s \beta}$$

where $T_1$ is the larger tension (tight side, at impending slip toward that side), $T_2$ is the smaller tension (slack side), $\mu_s$ is the coefficient of static friction between the belt and drum, and $\beta$ is the total **angle of wrap** (contact angle) expressed in **radians**.

**Key Points:**

- The exponential relationship means that even a modest coefficient of friction, combined with sufficient wrap angle, can produce an enormous ratio between the two tensions — this is the physical principle behind a capstan or belaying device holding a very large load with a relatively small applied restraining force, simply by wrapping the rope around the post/drum multiple times.
- The equation applies specifically at the condition of **impending slip**; for a belt/rope not on the verge of slipping, the actual tension ratio can be anywhere between 1 and $e^{\mu_s\beta}$, analogous to the self-adjusting nature of static friction generally.

**Worked Example: Belt Friction (Capstan)**

A rope is wrapped $1.5$ full turns ($\beta = 1.5 \times 2\pi = 9.42$ rad) around a capstan with $\mu_s = 0.25$. Find the maximum load $T_1$ that can be held by an applied holding force $T_2 = 100$ N.

$$T_1 = T_2 \, e^{\mu_s \beta} = 100 \times e^{0.25 \times 9.42} = 100 \times e^{2.356} = 100 \times 10.55 = 1055 \text{ N}$$

This demonstrates the substantial mechanical advantage achievable via belt/rope friction wrapped around a fixed drum.

### Illustration: Friction Cone / Angle of Friction

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 480 260">
<title>Angle of Friction and Impending Motion (svg_diagram)</title>
<rect width="480" height="260" fill="#ffffff" />
<line x1="50" y1="200" x2="430" y2="200" stroke="#333" stroke-width="2" />
<line x1="240" y1="200" x2="240" y2="60" stroke="#555" stroke-width="2" stroke-dasharray="4,3" />
<text x="245" y="65" fill="#555" font-size="13" font-family="sans-serif">N (normal)</text>
<line x1="240" y1="200" x2="330" y2="200" stroke="#c81e1e" stroke-width="2" stroke-dasharray="4,3" />
<text x="335" y="205" fill="#c81e1e" font-size="13" font-family="sans-serif">F (friction, at max)</text>
<line x1="240" y1="200" x2="300" y2="90" stroke="#0f7a3d" stroke-width="3" />
<polygon points="300,90 282,98 292,106" fill="#0f7a3d" />
<text x="305" y="90" fill="#0f7a3d" font-size="13" font-family="sans-serif">Resultant R</text>
<path d="M 240 160 A 45 45 0 0 1 275 168" fill="none" stroke="#333" stroke-width="1.5" />
<text x="250" y="155" fill="#333" font-size="13" font-family="sans-serif">phi_s</text>
</svg>

### Illustration: Belt Friction Wrap Angle Concept

```mermaid
flowchart LR
    A[Small holding force T2] --> B[Rope wrapped angle beta around fixed drum]
    B --> C[Friction along entire wrap accumulates exponentially]
    C --> D[Large held load T1 = T2 * e^ mu_s*beta ]
```

### Practical Engineering Relevance

**Key Points:**

- Friction analysis directly underlies design and safety checks for retaining wall base sliding resistance, slope stability (soil friction angle governs the same $\tan^{-1}\mu$ relationship in geotechnical contexts, though soil friction involves additional considerations like cohesion beyond the pure Coulomb dry-friction model covered here), belt and chain drive system design, bolted/clamped connection slip-critical design, and bearing/pivot design where friction losses matter for machine efficiency. [Inference: the specific extension of these dry-friction statics principles to soil mechanics (which includes cohesion and other factors) is a related but distinct topic covered more fully in geotechnical engineering coursework, mentioned here only to note the conceptual connection.]
- In many real design codes, a **factor of safety** is applied against the theoretical impending-slip friction limit, since actual coefficients of friction can vary from published/tabulated values due to surface condition, moisture, contamination, and wear — meaning $\mu_s$ and $\mu_k$ values from reference tables should be treated as representative/nominal values for design guidance rather than exact, universally fixed physical constants for a given material pair. [Unverified: specific coefficient values vary by source, surface preparation, and environmental condition; designers should consult project-specific testing or applicable design code tables rather than a single universal reference figure.]

### Related Topics

- Equilibrium of Particles and Rigid Bodies
- Free Body Diagrams
- Analysis of Frames and Machines
- Force Systems and Vector Operations
- Slope Stability and Soil Shear Strength (Geotechnical Engineering)
- Bolted and Slip-Critical Connection Design (Structural Design)
- Belt and Chain Drive Mechanical Systems