## Nuclear Structure and Composition


### Overview

The atomic nucleus consists of protons and neutrons (collectively nucleons) bound together by the strong nuclear force, occupying a volume roughly $10^{-15}$ m in radius — about 100,000 times smaller than the atom itself, yet containing nearly all its mass. Understanding nuclear structure requires characterizing nucleon composition, nuclear size and density, binding energy systematics, and the models developed to explain observed nuclear stability patterns and excitation spectra.

**Key Points**

- Nuclei are composed of $Z$ protons and $N$ neutrons, with mass number $A = Z+N$
- Nuclear radius scales as $R = R_0 A^{1/3}$, implying **constant nuclear density** across nuclides
- Nuclear binding arises from the short-range, strongly attractive **strong nuclear force**, which must overcome long-range Coulomb repulsion between protons
- The **liquid drop model** and **shell model** are the two principal complementary frameworks for understanding nuclear structure

---

### Basic Nuclear Composition and Notation

A nuclide is specified by:

$$^A_Z X_N$$

where $Z$ (atomic number) is the proton count, $N$ is the neutron count, $A = Z+N$ is the mass number, and $X$ is the chemical element symbol (determined by $Z$).

**Key Points**

- **Isotopes**: same $Z$, different $N$ (same element, different mass)
- **Isotones**: same $N$, different $Z$
- **Isobars**: same $A$, different $Z$ and $N$
- **Isomers**: same $Z$ and $N$, but different nuclear excitation/energy state (often long-lived metastable states, denoted with an "m" suffix, e.g., $^{99m}\text{Tc}$)

**Example**

Carbon has three naturally relevant isotopes: $^{12}_6\text{C}_6$ (stable, 98.9% abundance), $^{13}_6\text{C}_7$ (stable, 1.1%), and $^{14}_6\text{C}_8$ (radioactive, $t_{1/2}\approx5730$ years, used in radiocarbon dating).

---

### Nuclear Size and Density

Empirically, nuclear radii follow:

$$R = R_0 A^{1/3}, \qquad R_0 \approx 1.2\ \text{fm}$$

This relationship has been determined experimentally primarily through **electron scattering** experiments, which probe nuclear charge distribution via elastic form factors.

**Key Points**

- The $A^{1/3}$ scaling directly implies that nuclear **volume** scales linearly with $A$ ($V \propto R^3 \propto A$), meaning **nuclear density is approximately constant** across all nuclei (roughly $2.3\times10^{17}\ \text{kg/m}^3$) — a striking piece of evidence that nucleons behave somewhat like an incompressible fluid, packed at a nearly fixed density regardless of nuclear size
- This constant-density behavior is the direct empirical foundation of the liquid drop model
- Nuclear charge distributions are not perfectly sharp-edged; they are commonly modeled with a **Fermi (Woods-Saxon) distribution**:



  $$\rho(r) = \frac{\rho_0}{1+\exp\left(\frac{r-R}{a}\right)}$$

  with a surface "skin thickness" $a \approx 0.5$ fm characterizing the diffuseness of the nuclear edge

---

### The Strong Nuclear Force

The strong nuclear force binds nucleons together, overcoming the electrostatic (Coulomb) repulsion between protons. Its key phenomenological properties:

**Key Points**

- **Short range**: effective only over distances of order 1–2 fm, falling off rapidly (approximately exponentially) beyond this range, in contrast to the long-range $1/r^2$ Coulomb force
- **Charge independence (approximate)**: the nuclear force between any two nucleons (pp, nn, np) is approximately the same when electromagnetic effects are removed — a symmetry related to **isospin**
- **Saturation**: each nucleon interacts strongly only with its nearest neighbors, not with all other nucleons in the nucleus — this saturation property is precisely what underlies the constant nuclear density and the approximately linear ($\propto A$) scaling of total binding energy, rather than the $\propto A^2$ scaling expected for a force acting between all nucleon pairs
- **Spin dependence**: the force depends on the relative spin orientation of interacting nucleons (e.g., the deuteron is bound only in the spin-triplet, not spin-singlet, configuration)

---

### Nuclear Binding Energy

The binding energy $B$ of a nucleus is the energy required to separate it into individual free nucleons, related to the mass defect via Einstein's mass-energy relation:

$$B(A,Z) = \left[Zm_p + Nm_n - M(A,Z)\right]c^2$$

where $M(A,Z)$ is the measured nuclear mass. The **binding energy per nucleon**, $B/A$, is the standard measure of nuclear stability.

**Key Points**

- $B/A$ rises sharply for light nuclei, peaks near $A \approx 56$ (iron/nickel region) at approximately 8.8 MeV/nucleon, then gradually decreases for heavier nuclei
- This curve shape directly explains both **nuclear fusion** (energy released combining light nuclei toward the peak) and **nuclear fission** (energy released splitting heavy nuclei toward the peak)
- The gradual decline for heavy nuclei reflects the growing long-range Coulomb repulsion (scaling as $\sim Z^2/A^{1/3}$, growing faster than the short-range, saturating nuclear attraction) as nuclei become larger

---

### Binding Energy per Nucleon Curve (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 380" font-family="Helvetica, Arial, sans-serif">
<text x="320" y="22" font-size="15" text-anchor="middle" font-weight="bold">Binding Energy per Nucleon vs. Mass Number (svg_diagram)</text>
<line x1="70" y1="330" x2="600" y2="330" stroke="black" stroke-width="1.5" />
<line x1="70" y1="330" x2="70" y2="50" stroke="black" stroke-width="1.5" />
<text x="330" y="360" font-size="12" text-anchor="middle">Mass Number, A</text>
<text x="30" y="200" font-size="12" text-anchor="middle" transform="rotate(-90 30 200)">B/A (MeV/nucleon)</text>


<path d="M 90,320 C 120,180 150,110 190,90 C 230,75 280,68 330,66 C 400,68 470,80 550,120" fill="none" stroke="`#c0392b`" stroke-width="2.5" />


<circle cx="330" cy="66" r="4" fill="#2980b9" />
<text x="330" y="55" font-size="11" text-anchor="middle">Fe/Ni, A≈56 (peak, ~8.8 MeV)</text>


<text x="140" y="300" font-size="11" fill="`#27ae60`">Fusion region</text>

<text x="130" y="315" font-size="10" fill="`#27ae60`">(light nuclei)</text>



<text x="480" y="150" font-size="11" fill="`#8e44ad`">Fission region</text>

<text x="470" y="165" font-size="10" fill="`#8e44ad`">(heavy nuclei)</text>



<text x="90" y="345" font-size="10">1</text>

<text x="330" y="345" font-size="10">56</text>

<text x="580" y="345" font-size="10">238</text>

</svg>

---

### The Semi-Empirical Mass Formula (Liquid Drop Model)

The **liquid drop model** treats the nucleus as an incompressible, charged fluid drop, leading to the semi-empirical mass formula (Weizsäcker formula) for total binding energy:

$$B(A,Z) = a_V A - a_S A^{2/3} - a_C\frac{Z(Z-1)}{A^{1/3}} - a_A\frac{(A-2Z)^2}{A} + \delta(A,Z)$$

| Term | Physical Origin | Sign |
| --- | --- | --- |
| $a_V A$ | Volume term: bulk binding from short-range saturation | $+$ |
| $-a_S A^{2/3}$ | Surface term: nucleons at the surface are under-bound (fewer neighbors) | $-$ |
| $-a_C Z(Z-1)/A^{1/3}$ | Coulomb term: electrostatic repulsion between protons | $-$ |
| $-a_A(A-2Z)^2/A$ | Asymmetry term: quantum (Pauli) penalty for unequal proton/neutron numbers | $-$ |
| $\delta(A,Z)$ | Pairing term: extra stability for even-even nuclei | $\pm$ or $0$ |

**Key Points**

- The **surface term** is analogous to surface tension in a liquid drop, penalizing the higher surface-area-to-volume ratio of smaller nuclei
- The **asymmetry term** reflects the Pauli exclusion principle: since protons and neutrons occupy separate quantum energy-level systems, excessive imbalance between $Z$ and $N$ forces nucleons into higher-energy states, disfavoring highly asymmetric nuclei
- The **pairing term** $\delta$ is positive for even-even nuclei (both $Z,N$ even), zero for odd-$A$ nuclei, and negative for odd-odd nuclei — reflecting the extra binding from paired nucleon spins, and explaining why stable odd-odd nuclei are rare (only a handful exist, e.g., $^2$H, $^6$Li, $^{10}$B, $^{14}$N)
- Typical parameter values (in MeV): $a_V \approx 15.8$, $a_S \approx 18.3$, $a_C \approx 0.71$, $a_A \approx 23.2$; [Inference] exact best-fit values vary somewhat depending on the specific dataset and fitting procedure used

---

### The Nuclear Shell Model

While the liquid drop model successfully explains bulk binding energy trends, it fails to explain certain sharp stability anomalies — particularly the enhanced stability of nuclei with specific "magic numbers" of protons or neutrons: **2, 8, 20, 28, 50, 82, 126**.

The **shell model** treats nucleons as independently moving in an average potential well (similar in spirit to the atomic central-field approximation), with energy levels grouped into shells. Crucially, incorporating a strong **spin-orbit coupling** term (much stronger, relatively, than the atomic case) correctly reproduces the observed magic numbers — a major triumph of the model (Mayer and Jensen, 1949).

**Key Points**

- Nuclei with magic numbers of protons or neutrons (or both — "doubly magic," e.g., $^4$He, $^{16}$O, $^{40}$Ca, $^{208}$Pb) show markedly enhanced binding energy, larger first-excited-state energies, and greater natural abundance compared to neighboring nuclei
- The shell model successfully predicts nuclear spins and parities of ground states (especially for nuclei with one nucleon outside a closed shell, or one hole below a closed shell) using simple single-particle level filling
- Just as atomic electron shell structure explains chemical periodicity, nuclear shell structure explains the "nuclear periodicity" seen in binding energy, decay systematics, and reaction cross-sections

---

### Complementary Models Summary

| Model | Core Assumption | Successfully Explains | Limitations |
| --- | --- | --- | --- |
| Liquid Drop | Nucleus as incompressible charged fluid | Bulk binding energy trend, fission mechanism | Cannot explain magic number anomalies |
| Shell Model | Nucleons in independent-particle mean-field potential | Magic numbers, ground-state spins/parities | Struggles with collective phenomena (deformation, rotation/vibration) far from closed shells |
| Collective Model | Combines liquid-drop-like collective motion with shell effects | Nuclear deformation, rotational/vibrational excited states | More complex; parameter-dependent |

[Inference] No single nuclear model is universally sufficient; modern nuclear structure theory typically combines elements of both mean-field (shell-model-like) and collective approaches, refined further by ab initio many-body methods for light and medium-mass nuclei.

---

### Nuclear Spin, Parity, and Magnetic Moments

- Each nucleon carries intrinsic spin $\tfrac{1}{2}$; total nuclear spin $I$ results from coupling of individual nucleon orbital and spin angular momenta
- Even-even nuclei universally have ground-state spin-parity $0^+$ — a direct consequence of nucleon pairing, in which paired nucleons couple their angular momenta to zero
- Odd-$A$ nuclei have half-integer spin, often well-predicted by the shell model as arising from the single unpaired nucleon
- Nuclear magnetic moments, measured via techniques like nuclear magnetic resonance (NMR), provide sensitive probes of single-particle versus collective nuclear structure effects

---

### Related Topics

- Nuclear Binding Energy and the Semi-Empirical Mass Formula
- The Nuclear Shell Model and Magic Numbers
- Nuclear Fission and Fusion
- Radioactive Decay and Half-Life
- The Strong Nuclear Force and Isospin Symmetry
- Nuclear Reactions and Cross-Sections
- Collective Nuclear Models: Rotation and Vibration
- Electron Scattering and Nuclear Charge Distributions