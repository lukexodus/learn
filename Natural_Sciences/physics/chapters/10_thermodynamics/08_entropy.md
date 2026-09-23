## Entropy


### Definition and Physical Basis

Entropy ($S$) is a thermodynamic state function that quantifies the degree of energy dispersal, disorder, or the number of microscopic configurations (microstates) consistent with a system's observed macroscopic state. It is central to the Second Law of Thermodynamics, which establishes that the total entropy of an isolated system never decreases over time, providing a rigorous basis for the directionality of spontaneous natural processes.

### Classical (Thermodynamic) Definition

For a reversible process, the infinitesimal change in entropy is defined in terms of heat transfer at a given absolute temperature:

$$dS = \frac{\delta Q_{rev}}{T}$$

For a finite reversible process between states 1 and 2:

$$\Delta S = \int_1^2 \frac{\delta Q_{rev}}{T}$$

Because $S$ is a state function, this integral yields the same $\Delta S$ regardless of which reversible path is chosen to connect states 1 and 2 — and, critically, the same $\Delta S$ applies even if the *actual* process connecting these states was irreversible, since a convenient reversible path can always be constructed for calculation purposes.

Units of entropy: J/K (joules per kelvin), or J/(mol·K) for molar entropy.

### Statistical (Boltzmann) Definition

From statistical mechanics, entropy is directly related to the number of microstates $\Omega$ corresponding to a given macrostate:

$$S = k_B \ln \Omega$$

where $k_B = 1.380649 \times 10^{-23}\text{ J/K}$ is the Boltzmann constant. This formulation provides a microscopic, probabilistic interpretation: systems evolve spontaneously toward macrostates associated with the largest number of accessible microstates, because such macrostates are vastly more probable than highly ordered, low-multiplicity configurations.

**Reconciling the two definitions**: The thermodynamic and statistical definitions of entropy are consistent and can be shown to be mathematically equivalent under the framework of statistical mechanics, with the thermodynamic definition emerging as the macroscopic, ensemble-averaged consequence of the microscopic statistical definition.

### Key Properties of Entropy

- **State function**: entropy depends only on the current state of a system, not on the path taken to reach it.
- **Extensive property**: total entropy scales with the size/amount of the system (unlike intensive properties such as temperature or pressure).
- **Absolute values definable**: unlike internal energy or enthalpy (which are typically defined only up to an arbitrary reference), the Third Law of Thermodynamics allows entropy to be assigned an absolute value, with $S = 0$ defined for a perfect crystal at absolute zero temperature (0 K).

### Entropy Change Formulas for Common Processes

**Isothermal process (ideal gas)**:

$$\Delta S = nR\ln\left(\frac{V_2}{V_1}\right) = nR\ln\left(\frac{P_1}{P_2}\right)$$

**Constant volume process**:

$$\Delta S = nC_v\ln\left(\frac{T_2}{T_1}\right)$$

**Constant pressure process**:

$$\Delta S = nC_p\ln\left(\frac{T_2}{T_1}\right)$$

**General process (ideal gas, both T and V change)**:

$$\Delta S = nC_v\ln\left(\frac{T_2}{T_1}\right) + nR\ln\left(\frac{V_2}{V_1}\right)$$

**Phase change (constant temperature)**:

$$\Delta S = \frac{Q}{T} = \frac{mL}{T}$$

where $L$ is the specific latent heat of the phase transition (fusion, vaporization, sublimation).

**Mixing of ideal gases** (entropy of mixing, for $n_1$ and $n_2$ moles of two distinct ideal gases at the same $T$, $P$):

$$\Delta S_{mix} = -R\left(n_1\ln x_1 + n_2\ln x_2\right)$$

where $x_1, x_2$ are mole fractions. This is always positive, reflecting the spontaneous, irreversible nature of gas mixing.

### The Clausius Inequality

For any cyclic process (reversible or irreversible):

$$\oint \frac{\delta Q}{T} \leq 0$$

with equality holding only for a fully reversible cycle. This inequality is the mathematical foundation from which the entropy state function and the Second Law's directional constraint are formally derived, distinguishing possible (irreversible or reversible) cycles from thermodynamically impossible ones.

### Entropy and Irreversibility

For any process occurring in an isolated system:

$$\Delta S_{isolated} \geq 0$$

- Equality ($\Delta S = 0$) holds only for idealized reversible processes.
- Strict inequality ($\Delta S > 0$) holds for all real (irreversible) processes.

For a system exchanging heat with its surroundings, the relevant constraint applies to the combined system-plus-surroundings ("universe"):

$$\Delta S_{universe} = \Delta S_{system} + \Delta S_{surroundings} \geq 0$$

A system's entropy can locally decrease provided the surroundings' entropy increases by at least a compensating amount.

### Example Calculation

2 moles of an ideal gas expand isothermally at 350 K from 0.02 m³ to 0.06 m³. Find the entropy change. ($R = 8.314\text{ J/(mol·K)}$)

$$\Delta S = nR\ln\left(\frac{V_2}{V_1}\right) = (2)(8.314)\ln\left(\frac{0.06}{0.02}\right)$$



$$\Delta S = 16.628 \times \ln(3) = 16.628 \times 1.0986 \approx 18.27\text{ J/K}$$

The entropy increases as the gas occupies a larger volume, corresponding to a greater number of accessible microstates for the gas molecules.

**Example (heating at constant pressure)**: 3 moles of an ideal gas ($C_p = \frac{7}{2}R$ for a diatomic gas) are heated at constant pressure from 300 K to 450 K.

$$\Delta S = nC_p\ln\left(\frac{T_2}{T_1}\right) = (3)\left(\frac{7}{2}\times 8.314\right)\ln\left(\frac{450}{300}\right)$$



$$\Delta S = (3)(29.10)\ln(1.5) = 87.29 \times 0.4055 \approx 35.4\text{ J/K}$$

**Example (vaporization)**: Find the entropy change when 0.5 kg of water vaporizes at 100°C (373.15 K). ($L_{vap} = 2{,}260{,}000\text{ J/kg}$)

$$\Delta S = \frac{mL}{T} = \frac{(0.5)(2{,}260{,}000)}{373.15} \approx 3028\text{ J/K}$$

The large entropy increase reflects the dramatic increase in molecular disorder and accessible configurations as liquid water transitions to steam.

### Entropy and Gibbs Free Energy

Entropy combines with enthalpy to determine the spontaneity of processes at constant temperature and pressure via the **Gibbs free energy**:

$$\Delta G = \Delta H - T\Delta S$$

A process is spontaneous at constant $T$, $P$ if $\Delta G < 0$. This shows that even an entropy-decreasing process ($\Delta S < 0$ for the system) can be spontaneous if it is sufficiently exothermic ($\Delta H$ sufficiently negative) to outweigh the unfavorable entropy term.

### Diagram: Entropy and Microstate Multiplicity (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 480 260">
<text x="240" y="25" font-size="16" text-anchor="middle" font-weight="bold">Entropy and Microstates (svg_diagram)</text>
<rect x="40" y="60" width="150" height="150" fill="none" stroke="#333" stroke-width="2" />
<circle cx="115" cy="135" r="8" fill="#2980b9" />
<text x="115" y="230" font-size="12" text-anchor="middle">Low entropy: Omega = 1</text>
<text x="115" y="245" font-size="10" text-anchor="middle">(ordered, few microstates)</text>
<rect x="290" y="60" width="150" height="150" fill="none" stroke="#333" stroke-width="2" />
<circle cx="320" cy="90" r="6" fill="#c0392b" />
<circle cx="380" cy="100" r="6" fill="#c0392b" />
<circle cx="340" cy="140" r="6" fill="#c0392b" />
<circle cx="400" cy="160" r="6" fill="#c0392b" />
<circle cx="310" cy="180" r="6" fill="#c0392b" />
<circle cx="420" cy="80" r="6" fill="#c0392b" />
<text x="365" y="230" font-size="12" text-anchor="middle">High entropy: Omega greater than 1</text>
<text x="365" y="245" font-size="10" text-anchor="middle">(disordered, many microstates)</text>
</svg>

### Diagram: Entropy Calculation Decision Flow

```mermaid
flowchart TD
    A[Identify the process type] --> B{Constant temperature, ideal gas?}
    B -- Yes --> C[Delta S = nR ln(V2/V1)]
    B -- No --> D{Constant volume?}
    D -- Yes --> E[Delta S = n Cv ln(T2/T1)]
    D -- No --> F{Constant pressure?}
    F -- Yes --> G[Delta S = n Cp ln(T2/T1)]
    F -- No --> H{Phase change at constant T?}
    H -- Yes --> I[Delta S = Q/T = mL/T]
    H -- No --> J[General process: integrate delta Q_rev / T along reversible path]
```

### Applications

- **Chemical reaction spontaneity**: entropy is a key term in the Gibbs free energy criterion for determining whether reactions proceed spontaneously under given conditions.
- **Heat engine and refrigeration performance**: entropy generation quantifies the irreversibility (and thus inefficiency) of real engines and refrigeration cycles relative to idealized reversible limits.
- **Materials science**: entropy of mixing governs alloy formation, solid solution behavior, and phase diagrams in metallurgy and materials engineering.
- **Biochemistry and molecular biology**: entropy considerations are essential to understanding protein folding, ligand binding, and the thermodynamics of biomolecular interactions.
- **Information theory**: Shannon entropy, used to quantify information content and channel capacity, is mathematically structurally analogous to thermodynamic entropy, though the physical versus purely mathematical depth of this connection remains debated in some contexts. [Unverified — the strength of the physical analogy, as opposed to a shared mathematical formalism, is an area of ongoing discussion]

### Common Misconceptions

- Entropy is not simply "disorder" in an everyday visual sense; the precise definition concerns the number of microscopic configurations consistent with a macrostate, which does not always correspond intuitively to visual messiness or randomness.
- A decrease in a system's entropy does not violate the Second Law, provided the entropy of the surroundings increases by an equal or greater amount, keeping the total (universe) entropy change non-negative.
- Entropy is not a form of energy; it has units of energy per temperature (J/K), and while it plays a central role in determining the direction and spontaneity of energy transformations, it is not itself a conserved or transferable energy quantity in the same sense as heat or work.
- Absolute entropy (zero-point defined by the Third Law) applies strictly to perfect crystalline solids at 0 K; residual entropy can exist in real substances with structural disorder (e.g., certain glasses or crystals with orientational disorder) even as $T \to 0$. [Unverified — residual entropy phenomena are material-specific and represent deviations from the idealized Third Law limit]

**Related Topics**:

- Second Law of Thermodynamics
- Third Law of Thermodynamics and Absolute Zero
- Gibbs Free Energy and Chemical Spontaneity
- Statistical Mechanics and the Boltzmann Distribution
- Heat Engines and Efficiency
- Entropy and Information Theory