## Rotational Spectra of Molecules

### Overview

Rotational spectroscopy probes the quantized rotational energy levels of molecules, typically observed via absorption/emission in the microwave and far-infrared regions. It provides extremely precise measurements of molecular geometry (bond lengths, bond angles) and is grounded in modeling the molecule as a rigid rotor, with corrections for centrifugal distortion and vibration-rotation coupling.

**Key Points**

- Requires a **permanent electric dipole moment** for pure rotational transitions to be dipole-allowed
- The simplest model treats the molecule as a **rigid rotor**, giving quantized rotational energy levels
- Selection rule for linear/diatomic rigid rotors: $\Delta J = \pm 1$
- Real molecules require corrections for centrifugal distortion and rotation-vibration coupling

---

### The Rigid Rotor Model

For a diatomic molecule (or any linear molecule) treated as two point masses at fixed separation $R_e$, the classical rotational kinetic energy is:

$$E_{\text{rot}} = \frac{L^2}{2I}$$

where $I = \mu R_e^2$ is the moment of inertia and $\mu = \dfrac{m_1 m_2}{m_1+m_2}$ is the reduced mass.

Quantum mechanically, $L^2$ is replaced by the angular momentum operator with eigenvalues $\hbar^2 J(J+1)$:

$$E_J = \frac{\hbar^2}{2I}J(J+1) = hBJ(J+1), \qquad J = 0,1,2,\ldots$$

where $B$ is the **rotational constant**:

$$B = \frac{\hbar}{4\pi I} = \frac{h}{8\pi^2 I} \quad \text{(units of Hz)}$$

(often also expressed in wavenumbers, $B = \dfrac{h}{8\pi^2 cI}$, units cm⁻¹)

**Key Points**

- Each rotational level $J$ has degeneracy $2J+1$ (from the $M_J$ magnetic sublevels), which is important for computing thermal populations and line intensities
- $B$ is inversely proportional to $I$ (and hence to $\mu R_e^2$), so heavier molecules or longer bonds give smaller rotational constants and more closely spaced rotational levels

---

### Selection Rules and the Rotational Spectrum

For electric dipole transitions in a rigid rotor:

$$\Delta J = \pm 1, \qquad \Delta M_J = 0,\pm 1$$

with the additional requirement of a nonzero permanent dipole moment $\mu \neq 0$ (homonuclear diatomics such as $N_2$, $O_2$, $H_2$ have no pure rotational spectrum, since $\mu=0$ by symmetry).

The transition frequency for $J \to J+1$:

$$\nu_{J\to J+1} = \frac{E_{J+1}-E_J}{h} = 2B(J+1)$$

**Key Points**

- This produces a rotational spectrum consisting of **equally spaced lines** separated by $2B$ — a hallmark signature immediately recognizable in microwave spectra
- Measuring the line spacing directly yields $B$, and hence the moment of inertia $I$, and hence the bond length $R_e$ — rotational spectroscopy is one of the most precise methods for determining molecular bond lengths (accuracy often to $10^{-4}$ Å or better)

---

### Rigid Rotor Energy Levels and Allowed Transitions (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 380" font-family="Helvetica, Arial, sans-serif">
<text x="320" y="25" font-size="16" text-anchor="middle" font-weight="bold">Rigid Rotor Energy Levels (svg_diagram)</text>
<line x1="90" y1="340" x2="90" y2="50" stroke="black" stroke-width="1.5" />
<text x="55" y="195" font-size="12" text-anchor="middle" transform="rotate(-90 55 195)">Energy = hBJ(J+1)</text>

<line x1="120" y1="330" x2="320" y2="330" stroke="black" stroke-width="3" />
<text x="330" y="335" font-size="12">J=0, E=0</text>

<line x1="120" y1="290" x2="320" y2="290" stroke="black" stroke-width="3" />
<text x="330" y="295" font-size="12">J=1, E=2hB</text>

<line x1="120" y1="230" x2="320" y2="230" stroke="black" stroke-width="3" />
<text x="330" y="235" font-size="12">J=2, E=6hB</text>

<line x1="120" y1="150" x2="320" y2="150" stroke="black" stroke-width="3" />
<text x="330" y="155" font-size="12">J=3, E=12hB</text>

<line x1="120" y1="60" x2="320" y2="60" stroke="black" stroke-width="3" />
<text x="330" y="65" font-size="12">J=4, E=20hB</text>

<line x1="150" y1="330" x2="150" y2="290" stroke="#c0392b" stroke-width="1.5" marker-end="url(#arr)" />
<text x="155" y="315" font-size="10">2B</text>
<line x1="180" y1="290" x2="180" y2="230" stroke="#c0392b" stroke-width="1.5" marker-end="url(#arr)" />
<text x="185" y="265" font-size="10">4B</text>
<line x1="210" y1="230" x2="210" y2="150" stroke="#c0392b" stroke-width="1.5" marker-end="url(#arr)" />
<text x="215" y="195" font-size="10">6B</text>
<line x1="240" y1="150" x2="240" y2="60" stroke="#c0392b" stroke-width="1.5" marker-end="url(#arr)" />
<text x="245" y="110" font-size="10">8B</text>
</svg>

---

### Population Distribution and Spectral Line Intensity

Because rotational levels have $(2J+1)$-fold degeneracy and are thermally populated according to the Boltzmann distribution, the relative population of level $J$ is:

$$N_J \propto (2J+1)\exp\left(-\frac{hBJ(J+1)}{k_BT}\right)$$

**Key Points**

- This produces a rotational spectrum with an intensity envelope that rises, peaks at some $J_{\max}$, then falls — not a monotonic decrease — since the degeneracy factor $(2J+1)$ initially outpaces the Boltzmann suppression
- The most intense line occurs approximately at:



  $$J_{\max} \approx \sqrt{\frac{k_BT}{2hB}} - \frac{1}{2}$$
- This intensity pattern is directly useful for temperature determination in astrophysical and combustion diagnostics via rotational spectroscopy

---

### Centrifugal Distortion Correction

Real molecular bonds are not perfectly rigid; as $J$ increases, faster rotation stretches the bond slightly (centrifugal effect), lowering the effective rotational constant. This is captured by adding a correction term:

$$E_J = hBJ(J+1) - hDJ^2(J+1)^2$$

where $D$ is the **centrifugal distortion constant**, typically many orders of magnitude smaller than $B$ ($D/B \sim 10^{-4}$–$10^{-6}$ for typical diatomics), related to the vibrational force constant $k$ by:

$$D \approx \frac{4B^3}{\omega_e^2}$$

**Key Points**

- The correction becomes increasingly important at high $J$, where the $J^2(J+1)^2$ term grows faster than the linear $J(J+1)$ term
- Weakly bound molecules (small $k$, small $\omega_e$) show proportionally larger centrifugal distortion effects than strongly bound, stiff molecules

---

### Rotational Constants for Polyatomic Molecules

For nonlinear polyatomic molecules, three principal moments of inertia $I_A \leq I_B \leq I_C$ (about orthogonal principal axes) generalize the single moment of inertia of a diatomic:

| Molecular Type | Moment of Inertia Relation | Example |
| --- | --- | --- |
| Linear | $I_A = 0,\ I_B=I_C$ | $CO_2$, $HCN$ |
| Spherical top | $I_A = I_B = I_C$ | $CH_4$, $SF_6$ |
| Symmetric top | $I_A \neq I_B = I_C$ | $NH_3$, $CH_3Cl$ |
| Asymmetric top | $I_A \neq I_B \neq I_C$ | $H_2O$, most polyatomics |

**Key Points**

- Symmetric top molecules require two rotational constants and an additional quantum number $K$ (projection of angular momentum on the symmetry axis), giving energy levels $E_{J,K} = BJ(J+1) + (A-B)K^2$
- Asymmetric tops (like water) have no simple closed-form energy expression and require numerical diagonalization; their rotational spectra are considerably more complex, with allowed transitions governed by molecular symmetry (point group selection rules)
- Spherical tops (e.g., $CH_4$) have **zero permanent dipole moment by symmetry** and consequently show **no pure rotational spectrum**, despite having well-defined rotational energy levels

---

### Vibration-Rotation Interaction

In practice, rotational spectra are often observed superimposed on vibrational transitions (rovibrational spectra), since pure rotational transitions occur in the same molecule undergoing vibrational motion. The effective rotational constant depends on vibrational state:

$$B_v = B_e - \alpha_e\left(v+\frac{1}{2}\right)$$

where $B_e$ is the equilibrium rotational constant and $\alpha_e$ is the vibration-rotation coupling constant (reflecting that the average bond length increases slightly with vibrational excitation due to anharmonicity).

**Example**

For CO ($\mu \approx 6.857$ u, $R_e \approx 1.128$ Å), the moment of inertia is:

$$I = \mu R_e^2 \approx (6.857 \times 1.6605\times10^{-27}\ \text{kg})(1.128\times10^{-10}\ \text{m})^2 \approx 1.446\times10^{-46}\ \text{kg·m}^2$$

giving a rotational constant:

$$B = \frac{h}{8\pi^2 I} \approx 57.6\ \text{GHz} \approx 1.92\ \text{cm}^{-1}$$

matching well with the experimentally observed CO rotational transition spacing, which is a standard calibration line in radio astronomy (the CO $J=1\to0$ transition at $\approx 115$ GHz is one of the most widely used tracers of molecular gas in the interstellar medium).

---

### Applications

- **Radio astronomy**: Rotational transitions of interstellar molecules (CO, HCN, NH₃, and many others) are primary tracers of molecular cloud density, temperature, and kinematics
- **Precision bond length determination**: Microwave rotational spectroscopy remains among the most accurate techniques for gas-phase structural determination
- **Isotope effects**: Since $B \propto 1/\mu$, isotopic substitution (e.g., $^{12}$C vs $^{13}$C) shifts rotational line positions measurably, enabling isotope ratio determination and isotopic labeling studies
- **Atmospheric and environmental monitoring**: Microwave/millimeter-wave rotational spectroscopy is used to detect and quantify trace atmospheric gases

---

### Related Topics

- Selection Rules for Transitions
- The Born-Oppenheimer Approximation
- Molecular Bonding: Ionic and Covalent
- Vibrational Spectra of Diatomic Molecules
- Rovibronic Spectra and the Franck-Condon Principle
- Symmetric and Asymmetric Top Molecules
- Microwave Spectroscopy Techniques
- Molecular Astrophysics and Interstellar Medium Tracers