## The Simple and Physical Pendulum


### The Simple Pendulum: Setup and Equation of Motion

A simple pendulum consists of an idealized point mass $m$ suspended from a fixed pivot by a massless, inextensible string of length $L$. When displaced by angle $\theta$ from vertical, gravity produces a restoring torque about the pivot.

The restoring torque about the pivot is:

$$\tau = -mgL\sin\theta$$

Applying the rotational form of Newton's second law ($\tau = I\alpha$), with $I = mL^2$ for a point mass at distance $L$:

$$mL^2\frac{d^2\theta}{dt^2} = -mgL\sin\theta$$



$$\frac{d^2\theta}{dt^2} = -\frac{g}{L}\sin\theta$$

**Key Points**

- This equation is exact for the idealized simple pendulum, but it is **not** the SHM equation, since it contains $\sin\theta$ rather than $\theta$ itself — an inherently nonlinear differential equation with no simple closed-form elementary solution.
- The negative sign confirms gravity always acts as a restoring influence, pulling the pendulum back toward the vertical equilibrium position.

### The Small-Angle Approximation

For small angular displacements (typically $\theta$ less than about $15°$–$20°$), $\sin\theta \approx \theta$ (in radians), reducing the equation of motion to the SHM form:

$$\frac{d^2\theta}{dt^2} \approx -\frac{g}{L}\theta$$

This matches the standard SHM equation $\ddot{\theta} = -\omega^2\theta$ with:

$$\omega = \sqrt{\frac{g}{L}}, \qquad T = 2\pi\sqrt{\frac{L}{g}}$$

**Key Points**

- Under the small-angle approximation, the period is independent of both mass and amplitude — a manifestation of isochronism, historically central to pendulum clock accuracy.
- The approximation's error grows with amplitude; beyond roughly $20°$, the true period increasingly diverges from this simple formula, requiring more exact treatment.
- The period depends only on $L$ and $g$ — doubling the length increases the period by a factor of $\sqrt{2}$, not by a factor of 2.

### Example: Period of a Simple Pendulum

Find the period of a simple pendulum with $L=1$ m at Earth's surface ($g=9.8$ m/s²), assuming small-angle motion.

$$T = 2\pi\sqrt{\frac{1}{9.8}} = 2\pi\sqrt{0.102} \approx 2\pi(0.320) \approx 2.01 \text{ s}$$

### Example: Using Pendulum Period to Find $g$

A pendulum of length 0.75 m is observed to complete 20 oscillations in 34.7 s. Find the local gravitational acceleration.

$$T = \frac{34.7}{20} = 1.735 \text{ s}$$



$$T = 2\pi\sqrt{\frac{L}{g}} \implies g = \frac{4\pi^2L}{T^2} = \frac{4\pi^2(0.75)}{(1.735)^2} \approx \frac{29.61}{3.01} \approx 9.84 \text{ m/s}^2$$

This experimental technique (measuring $T$ for a known $L$) is a classic method for determining local gravitational acceleration, historically important in geodesy and still used in introductory physics laboratories.

### Beyond Small Angles: Amplitude-Dependent Period

For larger amplitudes, the true period of a simple pendulum exceeds the small-angle prediction and depends on the amplitude $\theta_{max}$. A commonly cited series expansion is:

$$T \approx 2\pi\sqrt{\frac{L}{g}}\left(1+\frac{1}{16}\theta_{max}^2+\frac{11}{3072}\theta_{max}^4+\cdots\right)$$

Where $\theta_{max}$ is in radians.

**Key Points**

- The exact period involves elliptic integrals, and this series expansion is an approximation that improves in accuracy as more terms are included. [Inference: the specific numerical coefficients shown are standard results from the literature, but the practical necessity of including higher-order terms depends on the required precision for a given application.]
- Even at $\theta_{max}=20°$ ($\approx0.349$ rad), the leading correction term $\frac{1}{16}\theta_{max}^2 \approx 0.0076$ represents less than a 1% correction to the period — illustrating why the small-angle approximation remains reasonably accurate even somewhat beyond the strict "small angle" regime.

### Simple Pendulum Diagram (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 420 320">
<title>Simple Pendulum Geometry (svg_diagram)</title>
<rect x="0" y="0" width="420" height="320" fill="#ffffff" />
<circle cx="210" cy="30" r="5" fill="#333" />
<line x1="210" y1="30" x2="210" y2="250" stroke="#999" stroke-width="1" stroke-dasharray="3,3" />
<line x1="210" y1="30" x2="300" y2="230" stroke="#333" stroke-width="2" />
<circle cx="300" cy="230" r="16" fill="#1f77b4" />
<text x="255" y="130" font-size="13" fill="#333">L</text>
<path d="M 210 70 A 40 40 0 0 1 240 78" fill="none" stroke="#d62728" stroke-width="2" />
<text x="255" y="70" font-size="13" fill="#d62728">θ</text>
<line x1="300" y1="230" x2="300" y2="280" stroke="#2ca02c" stroke-width="2" marker-end="url(#arrowG)" />
<text x="310" y="270" font-size="12" fill="#2ca02c">mg</text>
</svg>

### The Physical Pendulum

A **physical pendulum** is any rigid body that oscillates about a fixed pivot under gravity, without the "point mass on massless string" idealization. Its period depends on its moment of inertia about the pivot and the distance from the pivot to its center of mass.

For small oscillations, the restoring torque about the pivot (distance $d$ from center of mass) is:

$$\tau = -Mgd\sin\theta \approx -Mgd\theta$$

Applying $\tau = I_{pivot}\alpha$:

$$I_{pivot}\ddot\theta = -Mgd\theta \implies \omega = \sqrt{\frac{Mgd}{I_{pivot}}}$$



$$T = 2\pi\sqrt{\frac{I_{pivot}}{Mgd}}$$

Where $I_{pivot}$ is the moment of inertia about the pivot axis (found via the parallel axis theorem if $I_{cm}$ is known: $I_{pivot}=I_{cm}+Md^2$), $M$ is total mass, and $d$ is the distance from the pivot to the center of mass.

**Key Points**

- The simple pendulum is a special case of the physical pendulum where all mass is concentrated at distance $d=L$ from the pivot, giving $I_{pivot}=ML^2$, which correctly reduces the physical pendulum formula to the simple pendulum formula.
- The physical pendulum period depends on the **distribution** of mass (via $I_{pivot}$), not just the distance to the center of mass — two objects with the same $M$ and $d$ but different shapes can have different periods.
- Like the simple pendulum, this result is valid only for small-angle oscillations; the same nonlinear $\sin\theta$ correction applies at larger amplitudes.

### Example: Physical Pendulum — Uniform Rod

A uniform rod of length $L$ and mass $M$ pivots about one end. Find its period of small oscillation.

Moment of inertia about the end (from the standard rod formula): $I_{pivot} = \frac{1}{3}ML^2$

Distance from pivot to center of mass: $d = L/2$

$$T = 2\pi\sqrt{\frac{I_{pivot}}{Mgd}} = 2\pi\sqrt{\frac{\frac{1}{3}ML^2}{Mg(L/2)}} = 2\pi\sqrt{\frac{2L}{3g}}$$

**Comparison**: this is shorter than the period of a simple pendulum of the same length $L$ ($T_{simple}=2\pi\sqrt{L/g}$), since the rod's mass is distributed closer to the pivot on average than a point mass at the full length $L$ would be, reducing $I_{pivot}$ relative to $MgL$ and thus reducing the period.

### Example: Physical Pendulum — Uniform Disk

A uniform disk of radius $R$ and mass $M$ pivots about a point on its rim (perpendicular to the disk's face). Find its period of small oscillation.

Moment of inertia about the center: $I_{cm}=\frac{1}{2}MR^2$. Using the parallel axis theorem with $d=R$ (rim to center):

$$I_{pivot} = I_{cm}+Md^2 = \frac{1}{2}MR^2+MR^2 = \frac{3}{2}MR^2$$



$$T = 2\pi\sqrt{\frac{I_{pivot}}{Mgd}} = 2\pi\sqrt{\frac{\frac{3}{2}MR^2}{MgR}} = 2\pi\sqrt{\frac{3R}{2g}}$$

### The Equivalent Simple Pendulum Length

Any physical pendulum has an **equivalent simple pendulum length** $L_{eq}$ — the length of a simple pendulum that would share the same period:

$$L_{eq} = \frac{I_{pivot}}{Md}$$

**Key Points**

- This concept allows physical pendulum problems to be related directly back to the simpler, more intuitive simple pendulum framework.
- $L_{eq}$ is always greater than $d$ (the pivot-to-center-of-mass distance) for any physical pendulum, since $I_{pivot} = I_{cm}+Md^2 > Md^2$, meaning $L_{eq} = I_{cm}/(Md) + d > d$.

### The Radius of Gyration Connection

Using the radius of gyration about the center of mass ($k_{cm}$, defined by $I_{cm}=Mk_{cm}^2$), the physical pendulum period can be rewritten as:

$$T = 2\pi\sqrt{\frac{k_{cm}^2+d^2}{gd}}$$

**Key Points**

- This form highlights an interesting feature: for a fixed $k_{cm}$, the period as a function of $d$ has a **minimum** at $d=k_{cm}$, meaning there is an optimal pivot distance that minimizes the oscillation period for a given rigid body shape. [Inference: this minimum-period property is a standard mathematical result following from calculus applied to the period formula, though it is more commonly explored in intermediate/advanced mechanics treatments than introductory courses.]
- This relationship also underlies the reversible (Kater's) pendulum, a historically important precision instrument for measuring $g$ that exploits the symmetry of period-vs-pivot-distance around this minimum. [Inference: specific historical and design details of Kater's pendulum are noted here for context; deep familiarity with this specific instrument is more specialized than typical introductory syllabus coverage.]

### Comparison Table: Simple vs. Physical Pendulum

| Feature | Simple Pendulum | Physical Pendulum |
| --- | --- | --- |
| Mass distribution | Point mass | Extended rigid body |
| Governing formula | $T=2\pi\sqrt{L/g}$ | $T=2\pi\sqrt{I_{pivot}/(Mgd)}$ |
| Key parameter | Length $L$ | Moment of inertia $I_{pivot}$, distance $d$ |
| Depends on shape? | No (idealized point mass) | Yes, via $I_{pivot}$ |
| Small-angle requirement | Yes | Yes |
| Special case relationship | — | Reduces to simple pendulum when $I_{pivot}=Md^2$ |

### Problem-Solving Procedure

```mermaid
flowchart TD
    A[Identify pendulum type: simple point-mass or extended rigid body?] --> B{Simple pendulum?}
    B -- Yes --> C[Use T = 2*pi*sqrt(L/g) for small angles]
    B -- No, physical pendulum --> D[Find I_pivot: use table value or parallel axis theorem from I_cm]
    D --> E[Find d: distance from pivot to center of mass]
    E --> F[Apply T = 2*pi*sqrt(I_pivot / (Mgd))]
    C --> G{Amplitude within small-angle range?}
    F --> G
    G -- Yes --> H[Report period as calculated]
    G -- No --> I[Apply amplitude correction series or note SHM approximation breaks down]
```

### Applications

**Key Points**

- **Timekeeping**: pendulum clocks historically relied on the isochronous, small-angle behavior of simple/physical pendulums for consistent timekeeping accuracy.
- **Geophysics**: pendulum period measurements have historically been used (and Kater's reversible pendulum specifically) for precise determination of local gravitational acceleration, relevant to geodesy and gravimetric surveys.
- **Structural engineering**: physical pendulum principles inform the analysis of swinging or oscillating structural elements, such as tuned mass dampers used to reduce building sway.
- **Biomechanics**: walking gait analysis sometimes models limb swing using physical pendulum approximations, treating a leg as a physical pendulum pivoting about the hip. [Inference: this is one of several simplified models used in gait analysis literature; actual human locomotion involves additional muscular control not captured by a passive pendulum model alone.]
- **Museum/science demonstrations**: Foucault pendulums demonstrate Earth's rotation using long, precisely constructed pendulums, relying on consistent, predictable simple-pendulum-like periodic behavior over extended observation times.

### Common Misconceptions

**Key Points**

- The period of a pendulum (simple, small-angle) does not depend on the mass of the bob — a frequent point of confusion, since heavier objects might intuitively be expected to swing differently; mass cancels out of the governing equation entirely.
- A physical pendulum's period is **not** simply determined by the distance from the pivot to its center of mass alone — the full moment of inertia (mass distribution) about the pivot must be used, not just $d$.
- The small-angle approximation is not automatically valid for any "reasonable-looking" pendulum swing — amplitude must genuinely be small (typically under about $15°$–$20°$) for the simple $T=2\pi\sqrt{L/g}$ (or physical pendulum equivalent) formula to hold with good accuracy.
- The equivalent simple pendulum length $L_{eq}$ is a mathematical convenience for matching periods, not a statement that a physical pendulum's mass acts as if concentrated at that specific location for all purposes (e.g., it does not correctly predict the physical pendulum's center of mass or other properties).

### Conclusion

The simple pendulum, exact only in the point-mass, small-angle idealization, provides a foundational model for periodic motion with period $T=2\pi\sqrt{L/g}$, while the physical pendulum generalizes this to any rigid body via its moment of inertia about the pivot, $T=2\pi\sqrt{I_{pivot}/(Mgd)}$. Both models share the essential small-angle SHM approximation and the mass-independence of period, forming a bridge between idealized point-particle mechanics and the rotational dynamics of extended rigid bodies, with applications spanning timekeeping, geophysics, and structural engineering.

**Next Steps**

- Damped and driven pendulum motion: energy loss and resonance effects
- Large-amplitude pendulum motion and elliptic integral solutions (advanced)
- Torsional pendulums and rotational SHM analogs
- Moment of inertia review for physical pendulum applications
- Kater's reversible pendulum and precision gravimetry (historical/advanced)
- Coupled pendulums and normal mode analysis