## Energy in Simple Harmonic Motion

### Total Mechanical Energy in SHM

For an ideal simple harmonic oscillator (no friction or damping), total mechanical energy is conserved and continuously exchanges between kinetic and potential forms as the system oscillates.

$$E_{total} = KE + PE = \frac{1}{2}mv^2 + \frac{1}{2}kx^2$$

Substituting the SHM solutions $x(t) = A\cos(\omega t+\phi)$ and $v(t) = -A\omega\sin(\omega t+\phi)$:

$$E_{total} = \frac{1}{2}m\left[A\omega\sin(\omega t+\phi)\right]^2 + \frac{1}{2}k\left[A\cos(\omega t+\phi)\right]^2$$

Using $\omega^2 = k/m$ (so $m\omega^2 = k$), and the identity $\sin^2\theta+\cos^2\theta=1$:

$$E_{total} = \frac{1}{2}kA^2\sin^2(\omega t+\phi) + \frac{1}{2}kA^2\cos^2(\omega t+\phi) = \frac{1}{2}kA^2$$

**Key Points**

- Total energy is **constant** in time for ideal (undamped) SHM, despite kinetic and potential energy individually varying continuously.
- Total energy is proportional to the **square of the amplitude**: $E_{total} = \frac{1}{2}kA^2$ — doubling the amplitude quadruples the total energy.
- This result confirms energy conservation directly from the equations of motion, independent of any assumed conservative-force argument, though it is consistent with one (the spring force is conservative).

### Kinetic and Potential Energy as Functions of Position

At any instantaneous position $x$, kinetic and potential energy can be expressed directly in terms of $x$ (eliminating explicit time dependence) using the total energy relation:

$$PE(x) = \frac{1}{2}kx^2$$



$$KE(x) = E_{total} - PE(x) = \frac{1}{2}kA^2 - \frac{1}{2}kx^2 = \frac{1}{2}k(A^2-x^2)$$

Solving for speed as a function of position:

$$v(x) = \pm\omega\sqrt{A^2-x^2}$$

**Key Points**

- This position-based velocity formula is extremely useful for problems asking for speed at a specific displacement, without needing to solve for time first.
- The $\pm$ sign reflects that the object passes through any given position (except the turning points) twice per cycle, once moving in each direction.

### Energy Extremes

| Position | Kinetic Energy | Potential Energy | Speed |
| --- | --- | --- | --- |
| $x=0$ (equilibrium) | $KE_{max}=\frac{1}{2}kA^2$ | $PE=0$ | $v_{max}=A\omega$ |
| $x=\pm A$ (turning points) | $KE=0$ | $PE_{max}=\frac{1}{2}kA^2$ | $v=0$ |
| General $x$ | $\frac{1}{2}k(A^2-x^2)$ | $\frac{1}{2}kx^2$ | $\omega\sqrt{A^2-x^2}$ |

**Key Points**

- Maximum speed occurs exactly at equilibrium ($x=0$), where all energy is kinetic: $v_{max} = A\omega = A\sqrt{k/m}$.
- Maximum potential energy (and zero speed) occurs at the turning points ($x=\pm A$), where the object momentarily reverses direction.
- At every instant, $KE + PE = \frac{1}{2}kA^2$, providing a direct algebraic check for any SHM energy problem.

### Energy vs. Position and Energy vs. Time Graphs (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 520 300">
<title>Kinetic and Potential Energy vs Position in SHM (svg_diagram)</title>
<rect x="0" y="0" width="520" height="300" fill="#ffffff" />
<line x1="40" y1="260" x2="480" y2="260" stroke="#333" stroke-width="2" />
<line x1="260" y1="260" x2="260" y2="30" stroke="#333" stroke-width="1" stroke-dasharray="3,3" />
<text x="260" y="280" font-size="12" text-anchor="middle" fill="#333">x = 0</text>
<text x="90" y="280" font-size="12" text-anchor="middle" fill="#333">x = -A</text>
<text x="430" y="280" font-size="12" text-anchor="middle" fill="#333">x = +A</text>
<path d="M 90 50 Q 260 260 430 50" fill="none" stroke="#d62728" stroke-width="3" />
<text x="130" y="70" font-size="13" fill="#d62728">PE = ½kx²</text>
<path d="M 90 260 Q 260 50 430 260" fill="none" stroke="#1f77b4" stroke-width="3" />
<text x="360" y="80" font-size="13" fill="#1f77b4">KE = ½k(A²-x²)</text>
<line x1="40" y1="50" x2="480" y2="50" stroke="#2ca02c" stroke-width="2" stroke-dasharray="6,4" />
<text x="420" y="40" font-size="13" fill="#2ca02c">E_total = ½kA² (constant)</text>
</svg>

### Example: Finding Amplitude from Energy

A 0.5 kg mass on a spring ($k=200$ N/m) has total mechanical energy of 4 J. Find the amplitude and maximum speed.

$$E_{total} = \frac{1}{2}kA^2 \implies A = \sqrt{\frac{2E_{total}}{k}} = \sqrt{\frac{2(4)}{200}} = \sqrt{0.04} = 0.2 \text{ m}$$



$$v_{max} = A\omega = A\sqrt{\frac{k}{m}} = 0.2\sqrt{\frac{200}{0.5}} = 0.2\sqrt{400} = 0.2(20) = 4 \text{ m/s}$$

**Verification**: $KE_{max} = \frac{1}{2}mv_{max}^2 = \frac{1}{2}(0.5)(4)^2 = 4$ J ✓ (matches total energy, confirming all energy is kinetic at $x=0$).

### Example: Energy Split at a Given Position

A 1 kg mass oscillates with $A = 0.3$ m and $k = 40$ N/m. Find the kinetic and potential energy when $x = 0.15$ m (halfway to maximum displacement).

$$E_{total} = \frac{1}{2}(40)(0.3)^2 = \frac{1}{2}(40)(0.09) = 1.8 \text{ J}$$



$$PE = \frac{1}{2}kx^2 = \frac{1}{2}(40)(0.15)^2 = \frac{1}{2}(40)(0.0225) = 0.45 \text{ J}$$



$$KE = E_{total} - PE = 1.8 - 0.45 = 1.35 \text{ J}$$

Notably, at half the maximum displacement, potential energy is only **one-quarter** of total energy (not half), since $PE \propto x^2$ — a common point requiring care, as the energy split is not linear with position.

### Example: Finding Position for Equal Energy Split

For the same system as above ($A=0.3$ m, $k=40$ N/m, $E_{total}=1.8$ J), find the position(s) where $KE = PE$ exactly.

Setting $KE = PE$ means each equals half the total energy:

$$\frac{1}{2}kx^2 = \frac{1}{2}E_{total} = 0.9 \text{ J}$$



$$x^2 = \frac{2(0.9)}{40} = 0.045 \implies x = \pm\sqrt{0.045} \approx \pm0.212 \text{ m}$$



$$\frac{x}{A} = \frac{0.212}{0.3} \approx 0.707 \approx \frac{1}{\sqrt{2}}$$

This reveals a general result: kinetic and potential energy are equal at $x = \pm A/\sqrt{2}$ for **any** SHM system, independent of the specific values of $k$, $m$, or $A$ — a useful shortcut for this common problem type.

### Time-Averaged Energy

Averaged over one complete cycle, kinetic and potential energy each contribute exactly half of the total energy:

$$\langle KE\rangle = \langle PE\rangle = \frac{1}{2}E_{total} = \frac{1}{4}kA^2$$

**Derivation basis**: since $\langle\sin^2(\omega t+\phi)\rangle = \langle\cos^2(\omega t+\phi)\rangle = \frac{1}{2}$ over a full cycle (a standard result from time-averaging trigonometric functions), each energy term averages to half the total.

**Key Points**

- This time-averaging result is distinct from the instantaneous energy split at $x=\pm A/\sqrt{2}$ (a specific position), representing instead an average over the entire motion through time.
- Time-averaged energy relationships are particularly relevant in wave physics and AC circuit analysis, where analogous SHM-like oscillations occur.

### Energy Methods for Finding Angular Frequency

Energy conservation can also be used as an alternative derivation technique for finding $\omega$ in systems where direct force analysis is more complex, by differentiating the total energy expression with respect to time and setting it to zero (since $E_{total}$ is constant):

$$\frac{dE_{total}}{dt} = mv\frac{dv}{dt} + kx\frac{dx}{dt} = 0$$



$$mva + kxv = 0 \implies ma = -kx \implies a = -\frac{k}{m}x$$

This recovers the SHM equation of motion directly from energy conservation, confirming $\omega = \sqrt{k/m}$ without needing to separately invoke Newton's second law — a technique generalizable to more complex oscillatory systems (e.g., using Lagrangian methods) where writing the potential energy is more straightforward than directly analyzing forces. [Inference: this energy-based derivation technique becomes increasingly valuable in more advanced treatments of oscillatory systems, such as coupled oscillators or systems with non-Cartesian coordinates, though introductory courses typically use it as a supplementary rather than primary method.]

### Problem-Solving Procedure

```mermaid
flowchart TD
    A[Identify known SHM parameters: k, m, A, or E_total] --> B{What is being asked?}
    B -- Speed/KE at a given position x --> C[Use E_total = ½kA² = ½mv² + ½kx²; solve for v or KE]
    B -- Amplitude from given energy --> D[Use A = sqrt(2*E_total/k)]
    B -- Position where KE = PE --> E[Use shortcut: x = ±A/sqrt(2)]
    B -- Maximum speed --> F[Use v_max = A*omega = A*sqrt(k/m)]
    C --> G[Report numerical result with correct sign/direction interpretation]
    D --> G
    E --> G
    F --> G
```

### Energy in Other SHM Systems (Pendulum)

For a simple pendulum (small-angle approximation), the energy relationships are directly analogous, with gravitational PE replacing spring PE:

$$E_{total} = \frac{1}{2}mv_{max}^2 = mgh_{max}$$

Where $h_{max}$ is the maximum height risen above the lowest point of the swing, related to angular amplitude $\theta_{max}$ by $h_{max} = L(1-\cos\theta_{max})$.

**Key Points**

- The same qualitative energy exchange pattern applies: maximum KE at the lowest point (equilibrium), maximum PE (and zero KE) at the extremes of the swing.
- For small angles, this reduces to a form directly analogous to the mass-spring case, with an effective "spring constant" related to $mg/L$.

### Applications

**Key Points**

- **Vibration energy harvesting**: engineering devices that convert mechanical oscillation energy into electrical energy rely on SHM energy principles to estimate available power at given amplitudes and frequencies.
- **Seismic engineering**: energy stored in oscillating structures during ground motion is analyzed using SHM-based energy methods as a foundational model.
- **Molecular and atomic physics**: vibrational energy levels in the quantum harmonic oscillator model (the quantized analog of classical SHM energy) underlie infrared spectroscopy and understanding of chemical bond strength. [Inference: the classical energy treatment presented here is the foundation for, but distinct from, the quantum mechanical treatment, which introduces quantized energy levels not present in classical SHM.]
- **Acoustic and audio engineering**: energy in vibrating systems (speaker cones, musical instrument strings) is often first modeled using SHM energy relationships before incorporating damping and driving forces.

### Common Misconceptions

**Key Points**

- Kinetic and potential energy are **not** equal at half the maximum displacement ($x=A/2$) — this is a very common error; they are actually equal at $x=A/\sqrt{2}\approx0.707A$, since $PE\propto x^2$ rather than $x$.
- Total energy in SHM is conserved and constant in time for an ideal (undamped, frictionless) system — energy is *not* lost or gained over each cycle, only continuously exchanged between kinetic and potential forms.
- Doubling the amplitude does not double the total energy — it **quadruples** it, since $E_{total}\propto A^2$, a frequently overlooked quadratic relationship.
- Maximum speed depends on both amplitude and angular frequency ($v_{max}=A\omega$) — a larger amplitude alone does not guarantee higher speed if $\omega$ (via $k$ and $m$) is not also considered.

### Conclusion

Energy in simple harmonic motion continuously exchanges between kinetic and potential forms while total mechanical energy remains constant, proportional to the square of the amplitude ($E_{total}=\frac{1}{2}kA^2$). This energy-based framework provides an efficient alternative to purely kinematic analysis for finding speeds, positions, and amplitudes in SHM problems, and generalizes directly to other SHM systems such as pendulums, while forming a conceptual foundation for more advanced topics including damped oscillations, quantum harmonic oscillators, and wave energy.

**Next Steps**

- Damped harmonic motion: energy dissipation and amplitude decay over time
- Driven (forced) oscillations and resonance: energy input and steady-state amplitude
- The physical pendulum and torsional oscillators: energy methods extended
- Quantum harmonic oscillator: quantized energy levels (conceptual bridge to quantum mechanics)
- Coupled oscillators and energy transfer between normal modes
- Wave energy and intensity as an extension of oscillatory energy principles