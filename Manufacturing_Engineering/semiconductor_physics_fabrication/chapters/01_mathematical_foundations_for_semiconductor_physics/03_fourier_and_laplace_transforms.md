## Fourier and Laplace Transforms


### Overview and Relevance to Semiconductor Physics

Fourier and Laplace transforms convert differential equations and spatially/temporally varying signals into algebraic problems in a conjugate domain, and they provide the natural language for periodic crystal lattices, reciprocal space, frequency-domain device response, and noise analysis. In semiconductor physics, the Fourier transform underlies Bloch's theorem and reciprocal-space band structure, X-ray diffraction analysis, and small-signal AC device models, while the Laplace transform is the standard tool for transient circuit response, RC/RLC analysis of device parasitics, and control-theoretic treatment of feedback in mixed-signal circuits.

### The Fourier Series

**Key Points**

- Any sufficiently well-behaved periodic function $f(x)$ with period $L$ can be expanded as a sum of harmonics:

$$f(x) = \sum_{n=-\infty}^{\infty} c_n e^{i 2\pi n x / L}, \quad c_n = \frac{1}{L}\int_0^L f(x)e^{-i2\pi nx/L}dx$$

- This is the direct mathematical origin of reciprocal lattice vectors: since the crystal potential $V(\mathbf{r})$ is periodic with the lattice, it can be Fourier-expanded in terms of reciprocal lattice vectors $\mathbf{G}$:

$$V(\mathbf{r}) = \sum_{\mathbf{G}} V_G e^{i\mathbf{G}\cdot\mathbf{r}}$$

- This expansion is the starting point of the empirical pseudopotential method for band structure calculation, where a finite set of $V_G$ Fourier coefficients parametrizes the entire periodic potential.

### The Fourier Transform (Continuous, Aperiodic)

**Key Points**

For non-periodic (or infinite-domain) functions, the Fourier transform pair is:

$$F(k) = \int_{-\infty}^{\infty} f(x)e^{-ikx}dx, \quad f(x) = \frac{1}{2\pi}\int_{-\infty}^{\infty} F(k)e^{ikx}dk$$

**Key properties:**

| Property | Time/Space Domain | Frequency/k-Domain |
| --- | --- | --- |
| Differentiation | $\dfrac{d}{dx}f(x)$ | $ik \cdot F(k)$ |
| Convolution | $f(x) * g(x)$ | $F(k) \cdot G(k)$ |
| Translation | $f(x-a)$ | $e^{-ika}F(k)$ |
| Scaling | $f(ax)$ | $\frac{1}{\|a\|}F(k/a)$ |

The differentiation property is central to quantum mechanics: since $\hat{p} = -i\hbar \dfrac{d}{dx}$ in position representation, the Fourier transform diagonalizes the momentum operator, i.e., momentum space is literally the Fourier-conjugate domain of position space. This is why plane waves $e^{ikx}$ are simultaneous eigenstates of momentum and (in free space) energy.

### Bloch's Theorem and Reciprocal Space

**Example**

For an electron in a periodic crystal potential, Bloch's theorem states that eigenstates take the form:

$$\psi_{n\mathbf{k}}(\mathbf{r}) = e^{i\mathbf{k}\cdot\mathbf{r}} u_{n\mathbf{k}}(\mathbf{r})$$

where $u_{n\mathbf{k}}(\mathbf{r})$ has the same periodicity as the lattice. Expanding $u_{n\mathbf{k}}(\mathbf{r})$ in a Fourier series over reciprocal lattice vectors $\mathbf{G}$:

$$u_{n\mathbf{k}}(\mathbf{r}) = \sum_{\mathbf{G}} c_{n,\mathbf{G}}(\mathbf{k}) \, e^{i\mathbf{G}\cdot\mathbf{r}}$$

substituting into the Schrödinger equation converts the PDE into a matrix eigenvalue problem in the Fourier coefficients $c_{n,\mathbf{G}}(\mathbf{k})$ — the plane-wave pseudopotential method for band structure calculation is a direct, practical application of the Fourier transform combined with eigenvalue methods.

### Fourier Transform and Diffraction

**Key Points**

- X-ray and electron diffraction patterns from a crystal are, to good approximation, the (squared magnitude of the) Fourier transform of the crystal's electron density.
- Bragg diffraction peaks occur at reciprocal lattice vectors $\mathbf{G}$ because these are exactly the spatial frequencies at which the periodic lattice has nonzero Fourier components.
- This underlies structural characterization techniques (XRD, RHEED) used to verify epitaxial layer quality, strain, and crystallinity in semiconductor wafer fabrication.

### The Laplace Transform

**Key Points**

The Laplace transform generalizes the Fourier transform for functions defined on $t \geq 0$, using a complex frequency variable $s = \sigma + i\omega$:

$$F(s) = \int_0^\infty f(t)e^{-st}dt$$

It is especially suited to transient and causal systems because it naturally incorporates initial conditions and guarantees convergence for functions that grow (but not too fast) at large $t$, unlike the Fourier transform.

**Key properties:**

| Property | Time Domain | s-Domain |
| --- | --- | --- |
| Differentiation | $f'(t)$ | $sF(s) - f(0)$ |
| Second derivative | $f''(t)$ | $s^2F(s) - sf(0) - f'(0)$ |
| Convolution | $f(t)*g(t)$ | $F(s)G(s)$ |
| Integration | $\int_0^t f(\tau)d\tau$ | $F(s)/s$ |

The differentiation property directly converts linear ODEs with initial conditions into algebraic equations in $s$, which is why the Laplace transform is the standard tool for transient circuit analysis.

### Application: RC Transient Response in Device Parasitics

**Example**

A simplified small-signal model of a diode or MOSFET terminal often reduces to an RC network. For a series resistance $R$ charging a capacitance $C$ (e.g., junction capacitance) from a step voltage $V_0$, the governing ODE is:

$$RC\frac{dv_C}{dt} + v_C = V_0, \quad v_C(0) = 0$$

Taking the Laplace transform:

$$RC(sV_C(s) - 0) + V_C(s) = \frac{V_0}{s}$$



$$V_C(s) = \frac{V_0}{s(1+sRC)} = \frac{V_0}{s} - \frac{V_0}{s+1/RC}$$

Inverse transforming (using standard transform pair tables) gives the familiar exponential charging response:

$$v_C(t) = V_0\left(1 - e^{-t/RC}\right)$$

This same Laplace-domain approach extends directly to more complex parasitic networks (series resistance, junction capacitance, and substrate coupling) used in compact SPICE models of semiconductor devices.

### Transfer Functions and the s-Domain

**Key Points**

- The transfer function $H(s) = V_{out}(s)/V_{in}(s)$ characterizes a linear time-invariant (LTI) system's response to any input via $V_{out}(s) = H(s)V_{in}(s)$.
- Poles of $H(s)$ (roots of the denominator) determine the system's characteristic time constants/frequencies and stability: poles in the left half of the complex $s$-plane correspond to stable, decaying responses, while poles in the right half-plane indicate instability.
- Zeros and poles of transfer functions derived from small-signal semiconductor device models (e.g., a MOSFET's frequency response including gate capacitance and channel resistance) determine bandwidth limits such as the $f_T$ (unity current-gain frequency) and $f_{max}$ figures of merit.

### Fourier Transform in AC Small-Signal Device Analysis

**Key Points**

- Small-signal AC analysis of semiconductor devices (e.g., the diode or MOSFET admittance $Y(\omega)$) is obtained by setting $s = i\omega$ in the device's transfer function, connecting Laplace-domain circuit analysis directly to Fourier-domain frequency response.
- Capacitance-voltage (C-V) and conductance-voltage (G-V) characterization techniques used to extract interface trap density and doping profiles are fundamentally frequency-domain (Fourier) measurements.
- Noise power spectral density (e.g., thermal noise, shot noise, flicker/1/f noise in semiconductor devices) is defined via the Fourier transform of the autocorrelation function (Wiener-Khinchin theorem), making the Fourier transform essential to semiconductor noise analysis.

### Convolution Theorem and Its Physical Significance

**Key Points**

- The convolution theorem ($\mathcal{F}\{f*g\} = F\cdot G$) means that convolution in real space/time (common in impulse response calculations, line-shape broadening, and instrument response functions) becomes simple multiplication in the transform domain.
- In semiconductor spectroscopy (e.g., photoluminescence or absorption spectra), an intrinsic lineshape is often convolved with an instrumental broadening function; deconvolution via Fourier methods is used to recover the intrinsic lineshape.
- In device modeling, the impulse response of an RC network convolved with an arbitrary input signal gives the output; Laplace-domain multiplication of $H(s)$ with the input's transform avoids explicit time-domain convolution integrals.

### Discrete and Fast Fourier Transform (Numerical Context)

**Key Points**

- Numerical simulations (e.g., extracting a device's frequency response from time-domain SPICE simulation, or computing structure factors from finite lattice simulations) use the Discrete Fourier Transform (DFT), efficiently computed via the Fast Fourier Transform (FFT) algorithm with $O(N\log N)$ complexity.
- Plane-wave DFT (density functional theory) electronic structure codes rely heavily on FFTs to switch between real-space and reciprocal-space representations of wavefunctions and potentials at each self-consistency iteration.
- [Inference] Numerical artifacts such as spectral leakage and aliasing can arise from finite sampling windows and discretization; appropriate windowing and sampling rate (satisfying the Nyquist criterion) are typically required to avoid distorted frequency-domain results, though specific mitigation strategies depend on the software/tool used.

### Diagram: Transform Domains and Their Semiconductor Applications

```mermaid
flowchart LR
    A[Real space: crystal potential V(r)] -- Fourier transform --> B[Reciprocal space: V_G, k-space band structure]
    C[Time domain: device transient v(t)] -- Laplace transform --> D[s-domain: transfer function H(s)]
    D -- set s = i*omega --> E[Frequency domain: AC admittance Y(omega), noise PSD]
    B -- Bloch theorem --> F[Band structure E(k)]
    C -- Fourier transform, s = i*omega only --> E
```

### Illustration: Fourier Transform Pair (Real Space vs. Reciprocal Space)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 620 320" font-family="sans-serif">
<text x="310" y="25" font-size="16" text-anchor="middle" fill="#222">Periodic Potential and Its Fourier Spectrum (svg_diagram)</text>


<text x="150" y="55" font-size="13" text-anchor="middle" fill="#333">Real space: V(x)</text>

<line x1="40" y1="180" x2="280" y2="180" stroke="#333" stroke-width="1" />

<path d="M 40 180 Q 60 140 80 180 Q 100 140 120 180 Q 140 140 160 180 Q 180 140 200 180 Q 220 140 240 180 Q 260 140 280 180" stroke="`#1a5fb4`" stroke-width="2.5" fill="none" />

<text x="150" y="200" font-size="11" text-anchor="middle" fill="#333">x</text>


<line x1="300" y1="140" x2="360" y2="140" stroke="#222" stroke-width="2" />
<polygon points="360,135 372,140 360,145" fill="#222" />
<text x="330" y="125" font-size="11" text-anchor="middle" fill="#222">FT</text>


<text x="480" y="55" font-size="13" text-anchor="middle" fill="#333">Reciprocal space: V(G)</text>

<line x1="380" y1="180" x2="600" y2="180" stroke="#333" stroke-width="1" />

<line x1="440" y1="180" x2="440" y2="80" stroke="`#c01c28`" stroke-width="3" />

<line x1="490" y1="180" x2="490" y2="110" stroke="`#c01c28`" stroke-width="3" />

<line x1="540" y1="180" x2="540" y2="150" stroke="`#c01c28`" stroke-width="3" />

<text x="440" y="195" font-size="10" text-anchor="middle" fill="#333">G1</text>

<text x="490" y="195" font-size="10" text-anchor="middle" fill="#333">G2</text>

<text x="540" y="195" font-size="10" text-anchor="middle" fill="#333">G3</text>

<text x="480" y="200" font-size="11" text-anchor="middle" fill="#333">G</text>

</svg>

### Common Pitfalls and Clarifications

**Key Points**

- Confusing angular frequency $\omega$ (rad/s) with ordinary frequency $f$ (Hz), related by $\omega = 2\pi f$; convention differences ($e^{-i\omega t}$ vs $e^{+i\omega t}$) between physics and engineering texts can flip the sign of imaginary parts in impedance/admittance expressions.
- Applying the Fourier transform to non-causal or non-decaying functions without care: the Laplace transform's region of convergence (ROC) must be specified for the inverse transform to be uniquely defined, particularly when poles lie on or near the imaginary axis.
- Treating the discrete/finite-lattice reciprocal space sum as a true continuous Fourier transform: real crystals have finite extent, so diffraction peaks have finite width (related to crystallite size via the Scherrer equation), not true delta functions as the ideal infinite-lattice Fourier transform would predict.
- Overlooking that convolution theorem simplification only strictly applies to linear, time-invariant systems; semiconductor devices operating in strongly nonlinear regimes (e.g., large-signal switching) require different analysis techniques (e.g., harmonic balance, time-domain simulation).

### Related Topics

- Linear algebra and eigenvalue problems
- Ordinary and partial differential equations
- Reciprocal lattice and Brillouin zones
- Bloch's theorem and band structure
- X-ray diffraction and structural characterization
- Small-signal AC device modeling and SPICE parameter extraction
- Noise analysis in semiconductor devices (thermal, shot, 1/f noise)
- Complex analysis and contour integration