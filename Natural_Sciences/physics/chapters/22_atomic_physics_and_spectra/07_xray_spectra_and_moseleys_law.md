## X-Ray Spectra and Moseley's Law

### Overview

X-ray spectra from atoms consist of a continuous background (bremsstrahlung) superimposed with sharp characteristic lines arising from transitions between inner (core) electron shells. Moseley's Law (1913) established the systematic relationship between the frequency of these characteristic lines and the atomic number $Z$, providing decisive experimental confirmation of the nuclear atomic model and, historically, the correct ordering of elements in the periodic table.

**Key Points**

- X-ray emission occurs when an inner-shell electron (K, L, M shell) is ejected — typically by high-energy electron bombardment or photoionization — and an outer electron falls to fill the vacancy
- The emitted photon energy corresponds to the energy difference between the two inner shells, which scales approximately as $Z^2$
- Moseley's Law: $\sqrt{\nu} \propto (Z - \sigma)$, linear in atomic number
- This provided the first unambiguous, physically grounded determination of atomic number (as opposed to atomic mass ordering)

---

### Origin of Characteristic X-Ray Lines

Unlike optical spectra (which involve valence electron transitions), X-ray spectra originate from transitions of tightly-bound **core electrons**. The process:

1. An energetic incident electron (or photon) ejects a K-shell ($n=1$) electron, creating a vacancy
2. An electron from a higher shell ($L: n=2$, $M: n=3$, etc.) falls to fill the vacancy
3. The energy difference is released as a photon in the X-ray region (keV energies)

**Nomenclature (Siegbahn notation):**

| Series | Vacancy Shell | Electron Origin | Notation |
| --- | --- | --- | --- |
| K series | $n=1$ (K) | $n=2 \to n=1$ | $K_\alpha$ |
| K series | $n=1$ (K) | $n=3 \to n=1$ | $K_\beta$ |
| L series | $n=2$ (L) | $n=3 \to n=2$ | $L_\alpha$ |
| L series | $n=2$ (L) | $n=4 \to n=2$ | $L_\beta$ |

The $K_\alpha$ line (from $L \to K$, i.e., $n=2 \to n=1$) is typically the strongest and most studied characteristic line.

---

### Screening and Effective Nuclear Charge

Moseley's key physical insight was that an inner-shell electron does not experience the full nuclear charge $Z$, but a **screened** charge $(Z - \sigma)$, where $\sigma$ is a shielding constant accounting for the repulsive effect of other electrons (particularly those in the same or inner shells).

This modifies the hydrogenic Rydberg formula:

$$\frac{1}{\lambda} = R(Z-\sigma)^2\left(\frac{1}{n_1^2} - \frac{1}{n_2^2}\right)$$

or equivalently, for frequency:

$$\nu = cR(Z-\sigma)^2\left(\frac{1}{n_1^2}-\frac{1}{n_2^2}\right)$$

where $R$ is the Rydberg constant, $n_1$ is the shell receiving the electron (vacancy shell), and $n_2$ is the shell the electron falls from.

---

### Moseley's Law

Moseley empirically found that plotting $\sqrt{\nu}$ against $Z$ for a given spectral series (e.g., $K_\alpha$ across many elements) produces a straight line:

$$\sqrt{\nu} = a(Z - \sigma)$$

where $a$ is a constant depending on the transition (shell numbers $n_1, n_2$) and $\sigma$ is the screening constant for that series.

**For the $K_\alpha$ line specifically** ($n_1=1$, $n_2=2$, with screening constant $\sigma \approx 1$, since one other K-shell electron partially screens the nucleus):

$$\nu_{K_\alpha} = \frac{3}{4}cR(Z-1)^2$$

or in terms of photon energy:

$$E_{K_\alpha} = \frac{3}{4}(13.6\ \text{eV})(Z-1)^2$$

**Key Points**

- $\sigma \approx 1$ for $K_\alpha$ reflects screening by the single remaining K-shell electron
- The $Z^2$ (approximately) scaling means X-ray transition energies grow rapidly with atomic number, moving from soft X-rays for light elements to hard X-rays for heavy elements
- This relation is far more precise than optical spectral formulas because inner-shell electrons are largely unaffected by chemical bonding or the detailed outer-electron configuration — X-ray spectra are nearly identical for an element regardless of its chemical state

---

### Moseley Plot (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 380" font-family="Helvetica, Arial, sans-serif">
<text x="320" y="25" font-size="16" text-anchor="middle" font-weight="bold">Moseley Plot: √ν vs Z for Kα Line (svg_diagram)</text>

<line x1="80" y1="320" x2="580" y2="320" stroke="black" stroke-width="1.5" />
<line x1="80" y1="320" x2="80" y2="50" stroke="black" stroke-width="1.5" />
<text x="330" y="355" font-size="13" text-anchor="middle">Atomic Number, Z</text>
<text x="35" y="185" font-size="13" text-anchor="middle" transform="rotate(-90 35 185)">√ν (arb. units)</text>

<line x1="110" y1="300" x2="550" y2="70" stroke="#c0392b" stroke-width="2" />

<circle cx="130" cy="285" r="4" fill="#2980b9" />
<text x="130" y="300" font-size="10" text-anchor="middle">Al (13)</text>
<circle cx="230" cy="240" r="4" fill="#2980b9" />
<text x="230" y="255" font-size="10" text-anchor="middle">Fe (26)</text>
<circle cx="340" cy="190" r="4" fill="#2980b9" />
<text x="340" y="205" font-size="10" text-anchor="middle">Cu (29)</text>
<circle cx="450" cy="130" r="4" fill="#2980b9" />
<text x="450" y="145" font-size="10" text-anchor="middle">Mo (42)</text>
<circle cx="530" cy="80" r="4" fill="#2980b9" />
<text x="530" y="65" font-size="10" text-anchor="middle">Ag (47)</text>

<line x1="100" y1="315" x2="100" y2="325" stroke="black" stroke-width="1" />
<text x="100" y="340" font-size="10" text-anchor="middle">Z=σ≈1</text>
</svg>

---

### Historical and Physical Significance

- **Resolved periodic table ambiguities**: Before Moseley's work, elements were ordered by atomic mass, which produced known inconsistencies (e.g., Ar/K, Co/Ni, Te/I pairs appeared "out of order" by mass). Moseley's linear relationship with $Z$ confirmed that atomic number — not atomic mass — is the correct fundamental ordering variable
- **Predicted missing elements**: Gaps in the Moseley plot indicated undiscovered elements; this helped guide the discovery of elements such as technetium ($Z=43$), promethium ($Z=61$), hafnium ($Z=72$), and rhenium ($Z=75$)
- **Confirmed the nuclear model**: The clean $Z^2$-type dependence was strong evidence for Rutherford's nuclear atom and the Bohr model's quantized shell structure, since it showed X-ray energies scale in a manner directly derivable from hydrogenic energy levels with a screening correction

---

### Example: Calculating $K_\alpha$ Energy for Copper

**Example**

For copper ($Z=29$), using $\sigma \approx 1$:

$$E_{K_\alpha} = \frac{3}{4}(13.6\ \text{eV})(29-1)^2 = \frac{3}{4}(13.6)(784)$$



$$E_{K_\alpha} \approx 8{,}000\ \text{eV} = 8.0\ \text{keV}$$

This closely matches the experimentally measured copper $K_\alpha$ energy of approximately 8.05 keV (corresponding to $\lambda \approx 1.54\ \text{Å}$), a wavelength widely used as the standard source in X-ray diffraction crystallography.

---

### Departures from the Simple Moseley Formula

- **Fine structure splitting**: The $K_\alpha$ line is actually a closely spaced doublet ($K_{\alpha_1}$, $K_{\alpha_2}$) due to spin-orbit splitting of the $L$-shell ($2p_{3/2}$ and $2p_{1/2}$ levels), becoming increasingly resolved at higher $Z$ due to the $Z^4$ scaling of fine-structure splitting
- **Screening constant variation**: $\sigma$ is not perfectly constant across all $Z$; more refined treatments (e.g., using Slater's rules or Hartree-Fock calculations) give $Z$-dependent corrections, especially important for heavier elements and for $L$ and $M$ series where screening from multiple shells is more complex
- **Relativistic corrections**: For very heavy elements ($Z \gtrsim 50$–$60$), inner-shell electron velocities become a significant fraction of $c$, requiring relativistic (Dirac equation) treatment rather than the non-relativistic Bohr-based formula. [Inference] The exact $Z$ threshold at which relativistic corrections become non-negligible depends on the precision required and the specific shell involved, rather than a single sharp cutoff

---

### Applications

- **X-ray fluorescence (XRF) spectroscopy**: Elemental identification and quantification in materials science, geology, and archaeology, based directly on characteristic line energies predicted by Moseley's Law
- **X-ray diffraction (XRD)**: Copper and molybdenum $K_\alpha$ sources are standard due to their well-characterized, narrow-linewidth emission
- **Electron microprobe analysis**: Used in mineralogy and metallurgy for spatially resolved elemental composition
- **Medical and industrial radiography**: Underlying physics of X-ray tube characteristic emission spectra

---

### Related Topics

- Bohr Model and the Rydberg Formula
- Bremsstrahlung and the Continuous X-Ray Spectrum
- Auger Effect and Fluorescence Yield
- Fine Structure and Spin-Orbit Coupling
- Slater's Rules for Screening Constants
- Periodic Table Structure and Electron Shell Filling
- X-Ray Diffraction and Bragg's Law
- Photoelectric Effect and Inner-Shell Ionization