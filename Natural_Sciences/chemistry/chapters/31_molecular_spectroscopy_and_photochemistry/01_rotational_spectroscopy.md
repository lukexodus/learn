## Rotational Spectroscopy


### Overview

Rotational spectroscopy probes the quantized rotational energy levels of molecules, typically observed in the microwave region of the electromagnetic spectrum. It provides precise structural information — bond lengths and molecular geometry — for gas-phase molecules with a permanent dipole moment.

**Key Points**

- Rotational transitions occur in the microwave region (~0.03–3 cm⁻¹, or roughly 1–300 GHz)
- Only molecules with a permanent dipole moment show a pure rotational spectrum (microwave-active)
- Rotational constants derived from spectra yield precise bond lengths and moments of inertia
- The rigid rotor model provides the foundational quantum-mechanical treatment

### The Rigid Rotor Model

Treating a diatomic molecule as two point masses connected by a rigid, massless rod at fixed bond length $r$, the moment of inertia is:

$$I = \mu r^2, \qquad \mu = \frac{m_1m_2}{m_1+m_2}$$

where $\mu$ is the reduced mass. Solving the Schrödinger equation for this system yields quantized rotational energy levels:

$$E_J = BhcJ(J+1), \qquad J = 0, 1, 2, ...$$



$$B = \frac{h}{8\pi^2cI} \quad \text{(rotational constant, cm}^{-1}\text{)}$$

**Key Points**

- $J$ is the rotational quantum number
- Each level $J$ has degeneracy $g_J = 2J+1$, corresponding to the $2J+1$ possible orientations of angular momentum ($M_J$ values)
- The rotational constant $B$ is inversely proportional to the moment of inertia, so heavier or longer molecules have smaller $B$ and more closely spaced levels

### Selection Rules

**Key Points**

- Gross selection rule: the molecule must possess a permanent dipole moment (homonuclear diatomics like $N_2$, $O_2$, $H_2$ are microwave-inactive)
- Specific selection rule: $\Delta J = \pm 1$ for absorption/emission transitions
- The rotating dipole moment must couple to the oscillating electric field of the radiation, which requires a nonzero permanent dipole

### Transition Frequencies and Spectral Line Spacing

For the allowed transition $J \to J+1$:

$$\tilde{\nu} = E_{J+1} - E_J = 2B(J+1) \quad \text{(cm}^{-1}\text{)}$$

**Key Points**

- Successive transitions ($J=0\to1$, $J=1\to2$, $J=2\to3$, ...) occur at $2B, 4B, 6B, ...$
- The spectrum consists of a series of equally spaced lines, with spacing $2B$
- Measuring the line spacing directly yields $B$, from which $I$ and then bond length $r$ can be calculated

**Example**

For CO, the rotational spectrum shows lines spaced by 2B = 3.86 cm⁻¹, giving B = 1.93 cm⁻¹. Using $B = h/(8\pi^2cI)$:

$$I = \frac{h}{8\pi^2cB} = \frac{6.626\times10^{-34}}{8\pi^2(3\times10^{10})(1.93)} \approx 1.45\times10^{-46}\text{ kg·m}^2$$

With $\mu_{CO} = 1.139\times10^{-26}$ kg, solving $I=\mu r^2$ gives $r \approx 113$ pm, in close agreement with the accepted C-O bond length — illustrating how rotational spectroscopy provides highly precise structural data.

### Rotational Energy Level Diagram (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 560 300">
<rect x="0" y="0" width="560" height="300" fill="var(--bg,#ffffff)" />
<text x="280" y="22" text-anchor="middle" font-size="15" font-weight="bold" fill="var(--fg,#111)">Rigid Rotor Energy Levels and Transitions (svg_diagram)</text>

<line x1="80" y1="260" x2="200" y2="260" stroke="var(--fg,#333)" stroke-width="2" />
<text x="210" y="264" font-size="12" fill="var(--fg,#333)">J=0, E=0</text>
<line x1="80" y1="225" x2="200" y2="225" stroke="var(--fg,#333)" stroke-width="2" />
<text x="210" y="229" font-size="12" fill="var(--fg,#333)">J=1, E=2B</text>
<line x1="80" y1="175" x2="200" y2="175" stroke="var(--fg,#333)" stroke-width="2" />
<text x="210" y="179" font-size="12" fill="var(--fg,#333)">J=2, E=6B</text>
<line x1="80" y1="110" x2="200" y2="110" stroke="var(--fg,#333)" stroke-width="2" />
<text x="210" y="114" font-size="12" fill="var(--fg,#333)">J=3, E=12B</text>
<line x1="80" y1="60" x2="200" y2="60" stroke="var(--fg,#333)" stroke-width="2" />
<text x="210" y="64" font-size="12" fill="var(--fg,#333)">J=4, E=20B</text>

<line x1="120" y1="255" x2="120" y2="230" stroke="#2563eb" stroke-width="1.5" marker-end="url(#arr1)" />
<line x1="140" y1="220" x2="140" y2="180" stroke="#2563eb" stroke-width="1.5" marker-end="url(#arr1)" />
<line x1="160" y1="170" x2="160" y2="115" stroke="#2563eb" stroke-width="1.5" marker-end="url(#arr1)" />
<line x1="180" y1="105" x2="180" y2="65" stroke="#2563eb" stroke-width="1.5" marker-end="url(#arr1)" />
<line x1="280" y1="260" x2="540" y2="260" stroke="var(--fg,#333)" stroke-width="1" />
<line x1="300" y1="260" x2="300" y2="230" stroke="#dc2626" stroke-width="2" />
<line x1="340" y1="260" x2="340" y2="230" stroke="#dc2626" stroke-width="2" />
<line x1="380" y1="260" x2="380" y2="230" stroke="#dc2626" stroke-width="2" />
<line x1="420" y1="260" x2="420" y2="230" stroke="#dc2626" stroke-width="2" />
<text x="410" y="280" font-size="12" fill="var(--fg,#333)">Equally spaced lines (2B)</text>
</svg>

### Intensity Pattern and Population Effects

Line intensities in a rotational spectrum are governed by the Boltzmann population of each $J$ level, weighted by degeneracy:

$$N_J \propto (2J+1)e^{-BhcJ(J+1)/k_BT}$$

The most populated (and thus most intense transition-originating) level is found at:

$$J_{max} = \sqrt{\frac{k_BT}{2Bhc}} - \frac{1}{2}$$

**Key Points**

- Intensity increases initially with $J$ due to the $(2J+1)$ degeneracy factor, then decreases due to the exponential Boltzmann factor
- This produces a characteristic intensity envelope: lines increase, peak, then decrease as $J$ increases
- The intensity maximum position depends on temperature, shifting to higher $J$ at higher $T$

### Centrifugal Distortion

Real molecules are not perfectly rigid; bond stretching under rotation introduces a correction:

$$E_J = BhcJ(J+1) - DhcJ^2(J+1)^2$$

where $D$ is the centrifugal distortion constant (typically $D \ll B$).

**Key Points**

- Centrifugal distortion causes the bond to stretch slightly at high rotational speed, increasing $I$ and slightly lowering the effective energy relative to the rigid rotor prediction
- This effect becomes more significant at high $J$, causing measured line spacings to deviate progressively from the simple $2B$ prediction
- Fitting spectral data to include $D$ improves accuracy in bond length determination and is standard practice in precision microwave spectroscopy

### Rotational Spectroscopy of Polyatomic Molecules

| Molecule Type | Moment of Inertia | Spectral Pattern |
| --- | --- | --- |
| Linear (e.g., $HCN$, $CO_2$) | Single $I$ (perpendicular to axis) | Simple, evenly spaced lines (as diatomic) |
| Symmetric top (e.g., $NH_3$, $CH_3Cl$) | $I_{\parallel} \neq I_\perp = I_\perp$ | Characterized by two rotational constants, $A$ and $B$ |
| Spherical top (e.g., $CH_4$, $SF_6$) | $I_A = I_B = I_C$ | No permanent dipole moment (microwave-inactive) |
| Asymmetric top (e.g., $H_2O$) | $I_A \neq I_B \neq I_C$ | Complex spectrum, three distinct rotational constants |

**Key Points**

- Spherical tops possess no permanent dipole moment by symmetry and are microwave-inactive, though they can be studied via Raman rotational spectroscopy
- Symmetric tops require two rotational constants ($A$ for rotation about the unique axis, $B$ for perpendicular rotation)
- Asymmetric tops (most polyatomic molecules) require numerical diagonalization rather than simple closed-form energy expressions

### Rotational Raman Spectroscopy

For molecules lacking a permanent dipole moment, rotational transitions can still be observed via Raman scattering if the molecule has anisotropic polarizability.

**Key Points**

- Gross selection rule for rotational Raman: the molecule must have anisotropic polarizability (nearly all molecules except spherical tops satisfy this)
- Specific selection rule: $\Delta J = 0, \pm2$ (as opposed to $\pm1$ for microwave absorption), because Raman scattering is a two-photon process
- This allows rotational structure determination for homonuclear diatomics ($N_2$, $O_2$, $H_2$) that are microwave-inactive

### Applications

**Key Points**

- Precise bond length and bond angle determination for gas-phase molecules
- Astrochemistry: rotational transitions of interstellar molecules are detected via radio/microwave telescopes, enabling identification of molecular species in space
- Isotopic substitution studies: rotational constants shift with isotopic mass (reduced mass change) without altering bond length, enabling precise mass-independent structural determination

**Example**

Comparing $^{12}C^{16}O$ and $^{13}C^{16}O$ rotational spectra: the heavier isotopologue has larger reduced mass $\mu$ and thus larger moment of inertia $I$, producing a smaller rotational constant $B$ and more closely spaced spectral lines. Since bond length is essentially unchanged by isotopic substitution, this comparison provides an independent method for determining atomic masses and verifying spectroscopic assignments.

### Common Pitfalls

- Assuming all molecules are microwave-active; only those with a permanent dipole moment show pure rotational absorption spectra
- Confusing the selection rule for microwave absorption ($\Delta J = \pm1$) with that for rotational Raman ($\Delta J = 0, \pm2$)
- Neglecting centrifugal distortion when analyzing high-$J$ transitions, leading to systematic errors in derived bond lengths
- Treating rotational constant $B$ as directly proportional to bond length rather than inversely proportional to the square of bond length (via $I = \mu r^2$)

**Related Topics**

- Vibrational spectroscopy and rovibrational coupling
- The Boltzmann distribution and rotational population analysis
- Rotational Raman spectroscopy and polarizability
- Symmetric top and asymmetric top molecular structure
- Astrochemistry and radio astronomy molecular detection
- Isotope effects in molecular spectroscopy