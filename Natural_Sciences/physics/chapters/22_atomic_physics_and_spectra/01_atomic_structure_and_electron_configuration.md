## Atomic Structure and Electron Configuration


### Overview

Atomic structure describes how electrons are arranged around a nucleus in discrete quantum states, governed by the Schrödinger equation, the Pauli exclusion principle, and electron-electron interactions. Electron configuration — the specific distribution of electrons among atomic orbitals — determines an atom's chemical properties, spectroscopic behavior, and position in the periodic table, making this topic the conceptual bridge between quantum mechanics and observable chemistry/spectroscopy.

### Quantum Numbers Describing Atomic Orbitals

Each electron in an atom is described by a set of four quantum numbers:

| Quantum Number | Symbol | Allowed Values | Physical Meaning |
| --- | --- | --- | --- |
| Principal | $n$ | $1, 2, 3, \ldots$ | Energy level (shell); roughly, orbital size |
| Orbital (azimuthal) | $l$ | $0, 1, \ldots, n-1$ | Orbital angular momentum magnitude; subshell shape |
| Magnetic | $m_l$ | $-l, \ldots, +l$ | Orbital orientation ($z$-projection of angular momentum) |
| Spin magnetic | $m_s$ | $+\tfrac12, -\tfrac12$ | Electron spin projection |

Subshells are labeled spectroscopically by letter according to $l$:

$$l = 0 \to s, \quad l=1 \to p, \quad l=2 \to d, \quad l=3 \to f, \quad l=4 \to g, \ldots$$

(the letter sequence $s,p,d,f$ derives historically from spectral line descriptions: *sharp, principal, diffuse, fundamental*).

**Key Points**

- The number of orbitals in a subshell is $2l+1$ (from the allowed $m_l$ values); each orbital holds at most 2 electrons (by the Pauli exclusion principle, one for each $m_s$ value).
- Maximum electron capacity of a full shell $n$ is $2n^2$ (summing $2(2l+1)$ over $l=0$ to $n-1$).

### The Hydrogen Atom: Exact Reference Case

For hydrogen (one electron, one proton), the Schrödinger equation is exactly solvable. Energy depends **only** on $n$ (accidental degeneracy in $l$):

$$E_n = -\frac{13.6\text{ eV}}{n^2}$$

All states with the same $n$ but different $l, m_l$ are degenerate — a special feature of the pure $1/r$ Coulomb potential (this degeneracy is broken in multi-electron atoms, as discussed next).

### Multi-Electron Atoms: The Central-Field Approximation

For atoms with more than one electron, exact analytic solutions do not exist due to electron-electron repulsion terms in the Hamiltonian. The standard approximation treats each electron as moving independently in an **effective central potential** created by the nucleus plus the averaged charge distribution of all other electrons:

$$\hat{H} \approx \sum_i \left[-\frac{\hbar^2}{2m}\nabla_i^2 + V_{\text{eff}}(r_i)\right]$$

**Key Points**

- Because $V_{\text{eff}}(r)$ is no longer a pure $1/r$ potential (inner electrons partially screen the nuclear charge from outer electrons), the $n,l$ degeneracy of hydrogen is **broken**: energy now depends on both $n$ and $l$.
- Physically, for fixed $n$, lower $l$ orbitals (e.g., $s$) penetrate closer to the nucleus (higher probability density near $r=0$) and experience less screening, making them **lower in energy** than higher-$l$ orbitals of the same $n$ (e.g., $p$, $d$).

### Orbital Filling Order: The Aufbau Principle and Madelung's Rule

The **Aufbau principle** states that electrons fill available orbitals starting from the lowest energy, subject to the Pauli exclusion principle. The empirical ordering of subshell energies is captured by the **Madelung ($n+l$) rule**:

1. Subshells fill in order of increasing $n+l$.
2. For subshells with equal $n+l$, the one with **smaller $n$** fills first.

This produces the familiar filling sequence:

$$1s < 2s < 2p < 3s < 3p < 4s < 3d < 4p < 5s < 4d < 5p < 6s < 4f < 5d < 6p < 7s < \ldots$$

**Key Points**

- The famous $4s$-before-$3d$ filling order (despite $n=3 < n=4$) is a direct consequence of the Madelung rule: $4s$ has $n+l = 4+0=4$, while $3d$ has $n+l=3+2=5$, so $4s$ fills first.
- [Inference] The Madelung rule is an empirical/semi-quantitative regularity rather than an exact derivation from first principles; it correctly predicts filling order for the vast majority of elements but has known exceptions (below), reflecting the genuine complexity of many-electron energy ordering.

### Hund's Rules

When filling degenerate orbitals within the same subshell (e.g., the three $2p$ orbitals or five $3d$ orbitals), **Hund's rules** determine the lowest-energy configuration:

1. **Maximum multiplicity**: Electrons occupy separate orbitals with **parallel spins** before any pairing occurs, maximizing total spin $S$.
2. **Maximum orbital angular momentum**: Among configurations satisfying rule 1, the one with maximum total orbital angular momentum $L$ has lowest energy.
3. **Spin-orbit coupling**: For a subshell less than half-filled, the state with minimum total $J = |L-S|$ has lowest energy; for more than half-filled, maximum $J = L+S$ has lowest energy.

**Physical origin**: Rule 1 arises from the **exchange interaction** (discussed in the Identical Particles topic) — parallel-spin electrons have an antisymmetric spatial wavefunction, which reduces the probability of finding them close together, lowering Coulomb repulsion energy compared to paired (antiparallel) configurations.

### Worked Example 1: Electron Configuration of Iron (Z=26)

**Example**

Write the ground-state electron configuration of neutral iron (Fe, $Z=26$) using the Madelung filling order.

Following $1s < 2s < 2p < 3s < 3p < 4s < 3d$ and filling 26 electrons:

$$1s^2\, 2s^2\, 2p^6\, 3s^2\, 3p^6\, 4s^2\, 3d^6$$

**Verification**: $2+2+6+2+6+2+6 = 26$ ✓

**Output**

This is commonly written in shorthand using the noble gas core: $[\text{Ar}]\,4s^2\,3d^6$. Applying Hund's first rule to the six $3d$ electrons across five degenerate $d$-orbitals: the first five fill singly with parallel spin (maximizing $S$), and the sixth must pair up, giving four unpaired electrons total — consistent with iron's known paramagnetic behavior.

### Worked Example 2: Exception to the Madelung Rule — Chromium (Z=24)

**Example**

Predict the "expected" (Madelung) and actual electron configurations for chromium (Cr, $Z=24$), and explain the discrepancy.

**Naive Madelung prediction**: $[\text{Ar}]\,4s^2\,3d^4$

**Actual (experimentally observed) configuration**: $[\text{Ar}]\,4s^1\,3d^5$

**Output**

Chromium (along with copper, molybdenum, and several other transition metals) is a well-known **exception** to the simple Madelung rule. [Inference] The commonly cited explanation is that a half-filled ($d^5$) or fully-filled ($d^{10}$) subshell configuration provides extra stability due to enhanced exchange energy from maximized parallel-spin electrons (per Hund's rule) and more symmetric electron distribution, favoring the promotion of one $4s$ electron into the $3d$ subshell — though the precise quantitative balance of energy contributions (exchange, electron correlation, orbital relaxation) responsible for this and similar exceptions is a subtler many-body effect not fully captured by simple qualitative arguments, and is better established computationally than from any single simple rule.

### Term Symbols: Notation for Multi-Electron Atomic States

The overall angular momentum state of a multi-electron atom (particularly its outermost/valence electrons) is denoted by a **term symbol**:

$$^{2S+1}L_J$$

where $S$ is total spin, $L$ is total orbital angular momentum (denoted by capital letters $S,P,D,F,\ldots$ for $L=0,1,2,3,\ldots$), and $J$ is total angular momentum from $\mathbf{J}=\mathbf{L}+\mathbf{S}$ coupling (LS/Russell-Saunders coupling, valid for lighter atoms). The superscript $2S+1$ is the **spin multiplicity**.

**Example**

For iron's ground state (four unpaired $3d$ electrons determined above), detailed application of Hund's rules and Clebsch-Gordan coupling for the $3d^6$ configuration yields the experimentally confirmed ground term symbol $^5D_4$ — spin multiplicity 5 (consistent with $S=2$ from four unpaired spins, since a $d^6$ configuration also has one paired pair contributing zero net spin from that pair), $L=2$ ($D$ term), and $J=4$ (more-than-half-filled subshell, so $J=L+S=2+2=4$ per Hund's third rule).

### Diagram: Orbital Filling Order (Madelung Rule)

```mermaid
flowchart TD
    A["1s"] --> B["2s"] --> C["2p"] --> D["3s"] --> E["3p"] --> F["4s"] --> G["3d"] --> H["4p"] --> I["5s"] --> J["4d"] --> K["5p"] --> L["6s"] --> M["4f"] --> N["5d"] --> O["6p"] --> P["7s"]
```

### Diagram: Diagonal Rule for Subshell Filling Order (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 480 420">
<text x="240" y="25" font-size="16" font-weight="bold" text-anchor="middle" fill="#1a1a1a">Madelung (n+l) Diagonal Filling Rule (svg_diagram)</text>


<text x="60" y="55" font-size="12" text-anchor="middle" fill="#666">s (l=0)</text>

<text x="160" y="55" font-size="12" text-anchor="middle" fill="#666">p (l=1)</text>

<text x="260" y="55" font-size="12" text-anchor="middle" fill="#666">d (l=2)</text>

<text x="360" y="55" font-size="12" text-anchor="middle" fill="#666">f (l=3)</text>

<text x="60" y="85" font-size="13" text-anchor="middle" fill="`#1a1a1a`">1s</text>

<text x="60" y="120" font-size="13" text-anchor="middle" fill="`#1a1a1a`">2s</text>

<text x="160" y="120" font-size="13" text-anchor="middle" fill="`#1a1a1a`">2p</text>

<text x="60" y="155" font-size="13" text-anchor="middle" fill="`#1a1a1a`">3s</text>

<text x="160" y="155" font-size="13" text-anchor="middle" fill="`#1a1a1a`">3p</text>

<text x="260" y="155" font-size="13" text-anchor="middle" fill="`#1a1a1a`">3d</text>

<text x="60" y="190" font-size="13" text-anchor="middle" fill="`#1a1a1a`">4s</text>

<text x="160" y="190" font-size="13" text-anchor="middle" fill="`#1a1a1a`">4p</text>

<text x="260" y="190" font-size="13" text-anchor="middle" fill="`#1a1a1a`">4d</text>

<text x="360" y="190" font-size="13" text-anchor="middle" fill="`#1a1a1a`">4f</text>

<text x="60" y="225" font-size="13" text-anchor="middle" fill="`#1a1a1a`">5s</text>

<text x="160" y="225" font-size="13" text-anchor="middle" fill="`#1a1a1a`">5p</text>

<text x="260" y="225" font-size="13" text-anchor="middle" fill="`#1a1a1a`">5d</text>


<line x1="60" y1="95" x2="60" y2="110" stroke="#c0392b" stroke-width="1.5" />
<path d="M 60 130 L 160 130" stroke="#c0392b" stroke-width="1.5" fill="none" />
<line x1="60" y1="130" x2="60" y2="145" stroke="#c0392b" stroke-width="1.5" />
<path d="M 60 165 L 160 165" stroke="#c0392b" stroke-width="1.5" />
<line x1="160" y1="130" x2="160" y2="145" stroke="#c0392b" stroke-width="1.5" />
<path d="M 60 165 L 60 180" stroke="#c0392b" stroke-width="1.5" />
<path d="M 160 165 L 260 165" stroke="#c0392b" stroke-width="1.5" />

<text x="240" y="290" font-size="12" text-anchor="middle" fill="`#1a1a1a`">Diagonal arrows trace increasing n+l;</text>

<text x="240" y="310" font-size="12" text-anchor="middle" fill="`#1a1a1a`">for equal n+l, lower n fills first (e.g., 4s before 3d)</text>

<text x="240" y="340" font-size="11" text-anchor="middle" fill="#666">Exceptions occur near half-filled/filled d and f subshells (e.g., Cr, Cu)</text>

</svg>

### Common Misconceptions

- **Believing 3d always fills before 4s in energy ordering for isolated atoms**: The filling order (Aufbau) places $4s$ before $3d$; however, once occupied, $3d$ electrons are typically *more tightly bound* than $4s$ in the neutral atom, which is why $4s$ electrons are removed *first* during ionization — an apparent paradox that reflects orbital energies shifting as electron configuration changes, not an error in the filling rule itself.
- **Assuming the Madelung rule has no exceptions**: Approximately 20 elements (including Cr, Cu, Mo, Ag, Au, and several lanthanides/actinides) deviate from the naive prediction due to subtle exchange and correlation effects favoring half-filled or fully-filled subshells.
- **Confusing $l$ (orbital angular momentum quantum number, lowercase) with $L$ (total orbital angular momentum of a multi-electron atom, uppercase)**: Lowercase letters describe single-electron orbitals; uppercase term-symbol letters describe the coupled multi-electron total.
- **Neglecting Hund's rules when determining ground-state configurations for degenerate orbitals**: Simply filling the correct subshells (Aufbau/Madelung) is necessary but not sufficient — the specific arrangement of electrons *within* a partially-filled subshell (spin alignment, orbital occupation) also follows Hund's rules to determine the true ground state and term symbol.

### Conclusion

Atomic structure is organized through four quantum numbers ($n, l, m_l, m_s$) that define discrete orbitals, filled according to the Aufbau principle and the empirical Madelung ($n+l$) rule, subject to the Pauli exclusion principle and refined by Hund's rules for degenerate subshells. While hydrogen's pure Coulomb potential gives $n$-only energy dependence, multi-electron screening breaks this degeneracy, introducing $l$-dependence and occasional exceptions (Cr, Cu, and others) driven by exchange-energy stabilization of half-filled and filled subshells. This framework, culminating in term symbol notation $^{2S+1}L_J$, provides the essential foundation connecting atomic quantum mechanics to the periodic table, chemical bonding, and atomic spectroscopy.

**Related Topics**

- Term symbols and Russell-Saunders (LS) coupling in detail
- Periodic trends: ionization energy, atomic radius, electron affinity
- X-ray spectra and Moseley's law
- Spin-orbit coupling and fine structure splitting
- Zeeman effect and atomic magnetic moments
- Screening, effective nuclear charge, and Slater's rules
- Multi-electron atom energy level diagrams and spectroscopic notation