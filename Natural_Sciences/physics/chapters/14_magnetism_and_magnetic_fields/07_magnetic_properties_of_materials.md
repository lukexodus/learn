## Magnetic Properties of Materials


### Overview

Magnetic properties of materials describe how substances respond to and modify applied magnetic fields at the atomic and bulk level. Materials are broadly classified by the sign and magnitude of their magnetic response.

**Key Points**

- The magnetic behavior of a material arises fundamentally from the orbital motion and intrinsic spin of electrons, each acting as a tiny magnetic dipole
- Materials are classified primarily as diamagnetic, paramagnetic, or ferromagnetic, with additional categories (antiferromagnetic, ferrimagnetic) for more complex ordered structures
- The response of a material to an external field is quantified through magnetization, magnetic susceptibility, and permeability

### Atomic Origins of Magnetism

**Key Points**

- Each electron possesses an intrinsic magnetic moment associated with its spin, plus an orbital magnetic moment from its motion around the nucleus
- In most atoms, electron magnetic moments pair up and cancel due to the Pauli exclusion principle governing electron pairing in orbitals; unpaired electrons leave a net atomic magnetic moment
- The nucleus also possesses a much smaller magnetic moment, generally negligible for bulk magnetic behavior but significant in nuclear magnetic resonance (NMR) applications

### Magnetization and Auxiliary Field

When a material is placed in an external field $\vec{B}_0$, it develops a magnetization $\vec{M}$ (net magnetic dipole moment per unit volume), which contributes to the total field:

$$\vec{B} = \mu_0(\vec{H} + \vec{M})$$

Where $\vec{H}$ is the auxiliary magnetic field (related to free currents only), and $\vec{M}$ is the magnetization (related to bound/molecular currents within the material).

**Key Points**

- For linear, isotropic materials, magnetization is proportional to the applied field: $\vec{M} = \chi_m \vec{H}$, where $\chi_m$ is the magnetic susceptibility (dimensionless)
- This leads to $\vec{B} = \mu_0(1+\chi_m)\vec{H} = \mu \vec{H}$, where $\mu = \mu_0(1+\chi_m) = \mu_0\mu_r$ is the material's permeability, and $\mu_r$ is relative permeability
- $\chi_m$ can be positive (paramagnetic, weakly enhancing field) or negative (diamagnetic, weakly opposing field); ferromagnetic materials exhibit large, non-linear, history-dependent $\chi_m$

### Diamagnetism

Diamagnetism is a weak, universal magnetic response in which an applied field induces a magnetization opposing the field.

**Key Points**

- Diamagnetism arises from the field-induced modification of electron orbital motion (via Lenz's Law acting at the atomic scale), and is present in all materials, though often masked by stronger paramagnetic or ferromagnetic effects when present
- Diamagnetic susceptibility is small and negative (typically $\chi_m \sim -10^{-5}$), meaning diamagnetic materials are weakly repelled from strong field regions
- Examples include bismuth, copper, water, and most organic compounds; superconductors exhibit perfect diamagnetism ($\chi_m = -1$), completely expelling magnetic fields (the Meissner effect)

### Paramagnetism

Paramagnetism occurs in materials with unpaired electrons, where atomic magnetic moments align (partially) with an applied field, enhancing it slightly.

**Key Points**

- In the absence of an applied field, thermal agitation randomizes the orientation of atomic magnetic moments, resulting in zero net magnetization
- Applying an external field causes partial alignment, producing a small positive magnetization; paramagnetic susceptibility is small and positive (typically $\chi_m \sim 10^{-3}$ to $10^{-5}$)
- Susceptibility generally decreases with increasing temperature, following the **Curie Law**: $\chi_m = \dfrac{C}{T}$, where $C$ is the material-specific Curie constant and $T$ is absolute temperature — [Inference: this simple inverse-temperature relationship holds well for many paramagnetic materials but can break down at very low temperatures or in materials with more complex magnetic interactions]
- Examples include aluminum, platinum, and oxygen (notably, liquid oxygen is visibly attracted to strong magnets)

### Ferromagnetism

Ferromagnetism produces strong, permanent magnetic effects due to cooperative alignment of atomic magnetic moments over extended regions.

**Key Points**

- Ferromagnetic materials (iron, cobalt, nickel, and various alloys) exhibit spontaneous magnetization within small regions called **magnetic domains**, even without an external field, due to strong quantum mechanical exchange interactions between neighboring atomic moments
- In an unmagnetized sample, domains point in random directions, canceling at the macroscopic scale; applying an external field causes domain walls to move and domains to reorient, aligning with the field and producing strong net magnetization
- Ferromagnetic susceptibility is large and positive (often $\chi_m \sim 100$ to $10^5$), and critically, non-linear and history-dependent (hysteresis)

### Magnetic Domains Diagram (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 500 320">
<text x="250" y="25" text-anchor="middle" font-size="16" font-weight="bold" fill="#222">Magnetic Domains (svg_diagram)</text>
<text x="130" y="55" text-anchor="middle" font-size="13" fill="#333">Unmagnetized</text>
<rect x="40" y="70" width="180" height="150" fill="none" stroke="#333" stroke-width="2" />
<line x1="60" y1="110" x2="90" y2="110" stroke="#c0392b" stroke-width="3" /><polygon points="90,110 82,105 82,115" fill="#c0392b" />
<line x1="120" y1="90" x2="120" y2="130" stroke="#2980b9" stroke-width="3" /><polygon points="120,90 115,98 125,98" fill="#2980b9" />
<line x1="60" y1="180" x2="60" y2="150" stroke="#27ae60" stroke-width="3" /><polygon points="60,150 55,158 65,158" fill="#27ae60" />
<line x1="150" y1="150" x2="180" y2="150" stroke="#8e44ad" stroke-width="3" /><polygon points="180,150 172,145 172,155" fill="#8e44ad" />
<line x1="150" y1="190" x2="120" y2="190" stroke="#c0392b" stroke-width="3" /><polygon points="120,190 128,185 128,195" fill="#c0392b" />

<text x="380" y="55" text-anchor="middle" font-size="13" fill="#333">Magnetized (field applied)</text>

<rect x="290" y="70" width="180" height="150" fill="none" stroke="#333" stroke-width="2" />

<line x1="310" y1="110" x2="360" y2="110" stroke="`#c0392b`" stroke-width="3" /><polygon points="360,110 352,105 352,115" fill="`#c0392b`" />

<line x1="310" y1="150" x2="360" y2="150" stroke="`#c0392b`" stroke-width="3" /><polygon points="360,150 352,145 352,155" fill="`#c0392b`" />

<line x1="310" y1="190" x2="360" y2="190" stroke="`#c0392b`" stroke-width="3" /><polygon points="360,190 352,185 352,195" fill="`#c0392b`" />

<line x1="400" y1="110" x2="450" y2="110" stroke="`#c0392b`" stroke-width="3" /><polygon points="450,110 442,105 442,115" fill="`#c0392b`" />

<line x1="400" y1="150" x2="450" y2="150" stroke="`#c0392b`" stroke-width="3" /><polygon points="450,150 442,145 442,155" fill="`#c0392b`" />

<line x1="400" y1="190" x2="450" y2="190" stroke="`#c0392b`" stroke-width="3" /><polygon points="450,190 442,185 442,195" fill="`#c0392b`" />

</svg>

### Hysteresis

Ferromagnetic materials exhibit a lagging response to changing applied fields, traced out as a hysteresis loop when plotting $B$ (or $M$) against $H$.

**Key Points**

- **Remanence** ($B_r$): the residual magnetization remaining when the external field is reduced to zero, responsible for permanent magnets
- **Coercivity** ($H_c$): the reverse field strength required to bring the magnetization back to zero
- The area enclosed by the hysteresis loop represents energy dissipated as heat per unit volume, per cycle of magnetization reversal — a key consideration in AC transformer core design

### Hysteresis Loop Diagram (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 500 400">
<text x="250" y="25" text-anchor="middle" font-size="16" font-weight="bold" fill="#222">Hysteresis Loop (svg_diagram)</text>
<line x1="60" y1="200" x2="440" y2="200" stroke="#333" stroke-width="2" />
<line x1="250" y1="360" x2="250" y2="40" stroke="#333" stroke-width="2" />
<text x="420" y="220" font-size="13" fill="#333">H</text>
<text x="260" y="55" font-size="13" fill="#333">B</text>
<path d="M250,200 C300,190 350,120 380,80 C400,55 420,50 430,50" fill="none" stroke="#c0392b" stroke-width="3" />
<path d="M430,50 C400,80 350,100 250,110 C180,120 130,150 100,200" fill="none" stroke="#2980b9" stroke-width="3" />
<path d="M100,200 C130,250 180,280 250,290 C350,300 400,320 430,350" fill="none" stroke="#27ae60" stroke-width="3" />
<path d="M430,350 C400,320 350,300 250,200" fill="none" stroke="#8e44ad" stroke-width="3" stroke-dasharray="5,3" />
<circle cx="250" cy="110" r="4" fill="#333" /><text x="180" y="105" font-size="11" fill="#333">+Br (remanence)</text>
<circle cx="100" cy="200" r="4" fill="#333" /><text x="30" y="230" font-size="11" fill="#333">-Hc</text>
<circle cx="250" cy="290" r="4" fill="#333" /><text x="180" y="310" font-size="11" fill="#333">-Br</text>
<circle cx="400" cy="200" r="4" fill="#333" /><text x="405" y="230" font-size="11" fill="#333">+Hc</text>
</svg>

### Hard vs Soft Ferromagnetic Materials

| Property | Soft Ferromagnetic | Hard Ferromagnetic |
| --- | --- | --- |
| Coercivity | Low | High |
| Hysteresis loop area | Narrow (low energy loss) | Wide (high energy retention) |
| Typical use | Transformer cores, electromagnets, motor cores | Permanent magnets |
| Examples | Soft iron, certain silicon-steel alloys | Alnico, ferrite, neodymium-iron-boron (NdFeB) |

**Key Points**

- Soft materials magnetize and demagnetize easily, minimizing energy loss in applications with rapidly alternating fields (AC transformers, motors)
- Hard materials retain strong magnetization after the external field is removed, making them suitable for permanent magnets, but require large reverse fields to demagnetize
- Material selection for a given application balances coercivity, remanence, saturation magnetization, temperature stability, and cost — [Inference: specific alloy compositions are continually refined by materials science research to optimize these tradeoffs for particular applications]

### The Curie Temperature

Above a critical temperature called the **Curie temperature** ($T_C$), ferromagnetic materials lose their spontaneous magnetization and become paramagnetic.

**Key Points**

- Thermal agitation above $T_C$ overcomes the exchange interaction responsible for domain alignment, disrupting the ordered magnetic structure
- Above $T_C$, susceptibility follows the **Curie-Weiss Law**: $\chi_m = \dfrac{C}{T-T_C}$, a modification of the simple paramagnetic Curie Law accounting for the residual exchange interaction
- Curie temperatures vary significantly by material: iron ($\approx 770°\text{C}$), cobalt ($\approx 1115°\text{C}$), nickel ($\approx 355°\text{C}$) — [Unverified: precise values depend on sample purity and measurement methodology, and readers should consult authoritative materials references for precision applications]

### Antiferromagnetism and Ferrimagnetism

**Key Points**

- **Antiferromagnetic** materials have neighboring atomic magnetic moments aligned antiparallel due to exchange interactions, resulting in zero net spontaneous magnetization; above a critical temperature (the Néel temperature), they become paramagnetic
- **Ferrimagnetic** materials also have antiparallel neighboring moments, but of unequal magnitude, resulting in a net spontaneous magnetization similar in character to ferromagnetism, though generally weaker
- Ferrites (ferrimagnetic ceramic compounds) are widely used in high-frequency applications (transformer cores, inductors) due to their combination of useful magnetic properties and high electrical resistivity, which reduces eddy current losses compared to metallic ferromagnets

### Eddy Currents in Magnetic Materials

**Key Points**

- Changing magnetic fields within a conducting ferromagnetic core induce circulating eddy currents, which dissipate energy as heat (via $I^2R$ losses) and oppose the very field changes that create them (per Lenz's Law)
- Eddy current losses increase with frequency and are mitigated in practical transformer and motor cores by using thin laminated sheets (reducing the cross-sectional area available for circulating currents) or by using ferrite materials with inherently high electrical resistivity
- Total core loss in AC magnetic devices typically comprises both hysteresis loss (from the B-H loop area) and eddy current loss, both of which increase with operating frequency

### Applications of Magnetic Materials

**Key Points**

- **Permanent magnets** (hard ferromagnets): motors, generators, magnetic sensors, loudspeakers, magnetic storage media, and magnetic resonance imaging (MRI) magnet assemblies
- **Soft magnetic cores**: transformer laminations, inductor and motor cores, magnetic shielding
- **Data storage**: historically, magnetic hard drives and tapes exploit the hysteresis (bistable magnetization states) of ferromagnetic thin films to store binary information — [Inference: newer storage technologies have increasingly incorporated alternative physical mechanisms alongside or instead of traditional magnetic recording, though specifics evolve with ongoing technology development]
- **Magnetic shielding**: high-permeability soft ferromagnetic materials (e.g., mu-metal) redirect magnetic field lines around a shielded region, protecting sensitive electronics from external fields

### Common Pitfalls

**Key Points**

- Confusing magnetic susceptibility $\chi_m$ (a material property describing response to field) with permeability $\mu$ (which additionally incorporates the vacuum permeability $\mu_0$) — the two are related but not interchangeable
- Assuming all magnetic materials follow a simple linear $B$-$H$ relationship — this holds for diamagnetic and paramagnetic materials but fails dramatically for ferromagnetic materials due to hysteresis and saturation effects
- Overlooking that ferromagnetism is fundamentally a quantum mechanical, cooperative many-body phenomenon (exchange interaction), not merely a stronger version of classical paramagnetic alignment

**Related Topics**

- Ampère's Law and Applications
- Electromagnetic Induction and Faraday's Law
- Inductors, Transformers, and Core Losses
- Magnetic Dipoles and Dipole Moments
- Superconductivity
- Magnetic Data Storage Technologies