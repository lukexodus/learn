## Complex Numbers and Functions


### Definition and Motivation

A **complex number** extends the real number system by introducing the imaginary unit $i$, defined by $i^2 = -1$, allowing solutions to equations like $x^2+1=0$ that have no real solution. A complex number is written:

$$z = x + iy$$

where $x = \text{Re}(z)$ is the **real part** and $y = \text{Im}(z)$ is the **imaginary part** (both real numbers). Complex numbers are indispensable in physics for compactly representing oscillatory and wave phenomena, AC circuit impedance, and the quantum mechanical wavefunction, which is fundamentally complex-valued.

### The Complex Plane (Argand Diagram)

A complex number $z=x+iy$ is represented as a point $(x,y)$ in the **complex plane**, with the horizontal axis as the real axis and the vertical axis as the imaginary axis.

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 400 400">
<text x="10" y="20" font-size="14" fill="black">Complex Plane / Argand Diagram (svg_diagram)</text>
<line x1="50" y1="200" x2="370" y2="200" stroke="black" stroke-width="1.5" marker-end="url(#ax)" />
<line x1="200" y1="350" x2="200" y2="50" stroke="black" stroke-width="1.5" marker-end="url(#ax)" />
<text x="360" y="215" font-size="13">Re</text>
<text x="210" y="60" font-size="13">Im</text>
<line x1="200" y1="200" x2="320" y2="110" stroke="red" stroke-width="2.5" marker-end="url(#ax)" />
<circle cx="320" cy="110" r="3" fill="red" />
<text x="325" y="105" font-size="13" fill="red">z = x + iy</text>
<line x1="200" y1="200" x2="320" y2="200" stroke="gray" stroke-width="1" stroke-dasharray="3,3" />
<line x1="320" y1="200" x2="320" y2="110" stroke="gray" stroke-width="1" stroke-dasharray="3,3" />
<text x="255" y="215" font-size="12" fill="gray">x</text>
<text x="330" y="160" font-size="12" fill="gray">y</text>
<path d="M 240 200 A 40 40 0 0 0 232 175" fill="none" stroke="blue" stroke-width="1.5" />
<text x="245" y="185" font-size="12" fill="blue">theta</text>
</svg>

### Polar Form and Euler's Formula

Any complex number can also be written in **polar form**:

$$z = r(\cos\theta + i\sin\theta)$$

where $r=|z|=\sqrt{x^2+y^2}$ is the **modulus** (magnitude) and $\theta = \arg(z) = \tan^{-1}(y/x)$ (quadrant-checked) is the **argument** (phase angle).

**Euler's Formula** connects the exponential and trigonometric forms:

$$e^{i\theta} = \cos\theta + i\sin\theta$$

so that:

$$z = re^{i\theta}$$

**Euler's Identity**, the celebrated special case $\theta = \pi$:

$$e^{i\pi} + 1 = 0$$

This single relation links five fundamental constants ($e$, $i$, $\pi$, $1$, $0$) and is frequently cited as a hallmark of mathematical elegance.

### Complex Conjugate and Modulus

The **complex conjugate** of $z=x+iy$ is $z^* = x-iy$ (equivalently $\bar z$), obtained by flipping the sign of the imaginary part — geometrically a reflection across the real axis.

$$z z^* = (x+iy)(x-iy) = x^2+y^2 = |z|^2$$

This identity is the standard route to computing the modulus and to rationalizing complex denominators. In polar form, $z^* = re^{-i\theta}$.

### Arithmetic Operations

**Addition/subtraction** (component-wise, like vectors):

$$z_1 \pm z_2 = (x_1\pm x_2) + i(y_1\pm y_2)$$

**Multiplication** — algebraically using $i^2=-1$, or in polar form by multiplying moduli and adding arguments (the more physically transparent form):

$$z_1z_2 = r_1r_2\,e^{i(\theta_1+\theta_2)}$$

**Division**, similarly, divides moduli and subtracts arguments:

$$\frac{z_1}{z_2} = \frac{r_1}{r_2}e^{i(\theta_1-\theta_2)}$$

The polar-form multiplication/division rule is the key practical advantage of the exponential representation, especially in AC circuit analysis and wave superposition.

### De Moivre's Theorem and Roots of Complex Numbers

From repeated application of Euler's formula:

$$z^n = r^n e^{in\theta} = r^n(\cos n\theta + i\sin n\theta) \qquad \text{(De Moivre's Theorem)}$$

The $n$ distinct $n$th roots of a complex number are given by:

$$z^{1/n} = r^{1/n}\exp\left[i\left(\frac{\theta + 2\pi k}{n}\right)\right], \quad k=0,1,\ldots,n-1$$

**Example** — the cube roots of $z=8$ (i.e., $r=8,\theta=0$):

$$z^{1/3} = 2\exp\left(i\frac{2\pi k}{3}\right), \; k=0,1,2 \;\Rightarrow\; 2,\; 2e^{i2\pi/3},\; 2e^{i4\pi/3}$$

corresponding to $2$, $-1+i\sqrt{3}$, and $-1-i\sqrt{3}$ — the three roots are evenly spaced by $120°$ around a circle of radius 2 in the complex plane.

### Physical Application: Oscillations and Phasors

Simple harmonic motion is frequently represented using complex exponentials because differentiation of $e^{i\omega t}$ is algebraic (multiplication by $i\omega$) rather than requiring trigonometric identities:

$$x(t) = \text{Re}\left[Ae^{i\omega t}\right] = A\cos(\omega t)$$

A **phasor** represents an oscillating quantity as a complex number (or rotating vector in the complex plane) whose real part gives the physical, measurable quantity. This technique converts differential equations into algebraic ones — central to solving driven oscillator and AC circuit problems efficiently.

```mermaid
graph LR
    A["Physical oscillation: x(t) = A cos(omega t + phi)"] --> B["Represent as phasor: z(t) = A exp(i(omega t + phi))"]
    B --> C["Differentiate algebraically: dz/dt = i*omega*z"]
    C --> D["Solve algebraic equation for amplitude/phase"]
    D --> E["Take real part to recover physical solution"]
```

### Physical Application: AC Circuit Impedance

In AC circuit analysis, resistors, capacitors, and inductors are assigned complex **impedances**:

$$Z_R = R, \qquad Z_C = \frac{1}{i\omega C}, \qquad Z_L = i\omega L$$

allowing Ohm's Law $V=IZ$ to be applied to AC circuits exactly as in DC circuits, with the phase relationship between voltage and current encoded in the complex phase of $Z$ (e.g., $Z_L = i\omega L$ carries a $90°$ phase advance of voltage over current, since $i = e^{i\pi/2}$).

### Complex Functions and the Wavefunction

A **complex-valued function** $f(z)$ or $\Psi(x,t)$ maps complex (or real) inputs to complex outputs. In quantum mechanics, the wavefunction $\Psi(x,t)$ is intrinsically complex; physically observable quantities are obtained via $|\Psi|^2 = \Psi^*\Psi$ (a real, non-negative probability density), never from $\Psi$ directly.

**Key Points**

- The requirement that probability densities be real and non-negative is precisely why quantum mechanics is built on complex-valued wavefunctions combined with the modulus-squared operation — a purely real wave theory cannot simultaneously encode both amplitude and phase information in the way $\Psi^*\Psi$ does. [Inference: the depth of this quantum connection depends on course sequencing relative to a dedicated quantum mechanics unit.]

**Common Errors and Misconceptions**

- Forgetting to take the real part when converting a phasor/complex-exponential solution back to a physical quantity
- Treating $\sqrt{z}$ as single-valued; complex roots are inherently multi-valued (an $n$th root has exactly $n$ distinct values)
- Confusing modulus $|z|$ (a real, non-negative number) with the complex number $z$ itself
- Adding or comparing complex numbers as if the imaginary part could be discarded arbitrarily, rather than treating real and imaginary parts as independent quantities

**Related Topics**

- Vectors and Vector Algebra
- Ordinary Differential Equations (complex exponential solutions)
- Simple Harmonic Motion and Oscillations
- Alternating Current Circuits and Impedance
- Introduction to Quantum Mechanics (the complex wavefunction)
- Fourier Analysis (complex exponential basis functions)