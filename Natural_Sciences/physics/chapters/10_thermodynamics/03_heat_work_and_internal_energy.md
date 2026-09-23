## Heat, Work, and Internal Energy


### Internal Energy: Definition and Physical Basis

Internal energy ($U$) is the total energy contained within a thermodynamic system due to the microscopic motion and interactions of its constituent particles. It includes:

- **Translational kinetic energy** of molecules
- **Rotational and vibrational kinetic energy** of molecules
- **Potential energy** from intermolecular forces (bonding, attraction/repulsion)

Internal energy is a **state function** — its value depends only on the current state of the system (e.g., temperature, pressure, volume, composition), not on the path taken to reach that state. For an ideal gas, internal energy depends only on temperature (and the number of moles), since intermolecular forces are assumed negligible:

$$U = n C_v T$$

where $n$ is the number of moles, $C_v$ is the molar specific heat capacity at constant volume, and $T$ is absolute temperature (K).

### Heat: Definition and Physical Basis

Heat ($Q$) is energy transferred between a system and its surroundings solely due to a temperature difference. Heat is **not** a state function — it is a **path function** (also called a process quantity), meaning the amount of heat transferred depends on the specific process by which a system changes state, not just the initial and final states.

**Sign convention** (commonly used, though conventions vary by textbook) [Unverified — sign convention is a notational choice and differs between physics and engineering texts]:

- $Q > 0$: heat added to the system
- $Q < 0$: heat removed from the system

### Work: Definition and Physical Basis

Work ($W$) in thermodynamics refers to energy transferred to or from a system via a macroscopic, organized force acting through a displacement — most commonly, work done by or on a gas through volume changes (pressure-volume work).

For a quasi-static (reversible) process, the work done **by** a gas as it expands or is compressed:

$$W = \int_{V_1}^{V_2} P\, dV$$

**Sign convention** (commonly used, consistent with the physics convention below) [Unverified — as with heat, sign convention varies by textbook and field]:

- $W > 0$: work done **by** the system (expansion)
- $W < 0$: work done **on** the system (compression)

Like heat, work is a **path function** — the value of $\int P\,dV$ depends on the specific path taken through the $P$-$V$ diagram, not just the endpoints.

### The First Law of Thermodynamics

The First Law of Thermodynamics is a statement of the conservation of energy applied to thermodynamic systems, relating changes in internal energy to heat and work:

$$\Delta U = Q - W$$

(using the physics convention where $W$ is work done **by** the system)

Equivalently, in the engineering convention (where $W$ is work done **on** the system):

$$\Delta U = Q + W$$

**Physical interpretation**: The change in a system's internal energy equals the heat added to the system minus the work done by the system on its surroundings (physics convention). Energy is conserved: it can be transferred as heat or work, or stored as internal energy, but the total is conserved.

### Common Thermodynamic Processes

**Isochoric (constant volume) process**: $dV = 0$, so $W = 0$.

$$\Delta U = Q$$

All heat added directly increases internal energy (and temperature).

**Isobaric (constant pressure) process**: $P$ = constant.

$$W = P\Delta V$$



$$\Delta U = Q - P\Delta V$$

**Isothermal (constant temperature) process**: for an ideal gas, $\Delta U = 0$ (since $U$ depends only on $T$).

$$Q = W$$

All heat added is converted entirely into work done by the system (or vice versa for compression).

For an ideal gas at constant temperature:

$$W = \int_{V_1}^{V_2} P\,dV = nRT\ln\left(\frac{V_2}{V_1}\right)$$

**Adiabatic process**: no heat exchange with surroundings, $Q = 0$.

$$\Delta U = -W$$

Any work done by the system comes entirely at the expense of internal energy (and thus temperature drops during adiabatic expansion).

For an ideal gas undergoing a reversible adiabatic process:

$$PV^\gamma = \text{constant}$$

where $\gamma = C_p/C_v$ is the heat capacity ratio.

### Example Calculation

An ideal gas expands isothermally at 300 K from a volume of 0.01 m³ to 0.03 m³, with $n = 1\text{ mol}$. Find the work done by the gas and the heat absorbed. ($R = 8.314\text{ J/(mol·K)}$)

Since the process is isothermal, $\Delta U = 0$, so $Q = W$.

$$W = nRT\ln\left(\frac{V_2}{V_1}\right) = (1)(8.314)(300)\ln\left(\frac{0.03}{0.01}\right)$$



$$W = 2494.2 \times \ln(3) = 2494.2 \times 1.0986 \approx 2740\text{ J}$$

Therefore, $Q = W \approx 2740\text{ J}$: the gas absorbs approximately 2740 J of heat, all of which is converted into work done on the surroundings during the expansion.

**Example (adiabatic process)**: The same gas ($n=1\text{ mol}$, monatomic, $C_v = \frac{3}{2}R$) undergoes an adiabatic expansion from 300 K to 250 K.

$$\Delta U = nC_v \Delta T = (1)\left(\frac{3}{2}\times 8.314\right)(250 - 300) = (12.471)(-50) \approx -623.6\text{ J}$$

Since $Q = 0$ for an adiabatic process:

$$W = -\Delta U = 623.6\text{ J}$$

The gas does approximately 623.6 J of work on its surroundings, entirely at the expense of its own internal energy, causing the temperature to drop.

### P-V Diagram Representation

Thermodynamic processes are commonly visualized on a pressure-volume ($P$-$V$) diagram, where the work done by the system corresponds to the area under the process curve between the initial and final volumes. Different paths between the same two states (e.g., isobaric-then-isochoric vs. isothermal) enclose different areas, demonstrating that work (and correspondingly heat, via the First Law) is path-dependent even when $\Delta U$ is identical.

### Diagram: First Law Energy Balance (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 480 260">
<text x="240" y="25" font-size="16" text-anchor="middle" font-weight="bold">First Law of Thermodynamics (svg_diagram)</text>
<rect x="160" y="90" width="160" height="100" fill="#cfe8f7" stroke="#2a6f97" stroke-width="2" />
<text x="240" y="145" font-size="14" text-anchor="middle">System</text>
<text x="240" y="165" font-size="12" text-anchor="middle">Internal Energy U</text>
<line x1="60" y1="110" x2="155" y2="110" stroke="#c0392b" stroke-width="3" marker-end="url(#harrow)" />
<text x="105" y="100" font-size="13" fill="#c0392b">Q (heat in)</text>
<line x1="325" y1="170" x2="420" y2="170" stroke="#2980b9" stroke-width="3" marker-end="url(#harrow)" />
<text x="370" y="195" font-size="13" fill="#2980b9">W (work out)</text>
<text x="240" y="230" font-size="13" text-anchor="middle">delta U = Q - W</text>
</svg>

### Diagram: Process Type Analysis Flow

```mermaid
flowchart TD
    A[Identify constraint held constant during the process] --> B{Constant volume?}
    B -- Yes --> C[Isochoric: W = 0, delta U = Q]
    B -- No --> D{Constant pressure?}
    D -- Yes --> E[Isobaric: W = P delta V, delta U = Q - P delta V]
    D -- No --> F{Constant temperature, ideal gas?}
    F -- Yes --> G[Isothermal: delta U = 0, Q = W = nRT ln(V2/V1)]
    F -- No --> H{No heat exchange, Q = 0?}
    H -- Yes --> I[Adiabatic: delta U = -W, PV^gamma = constant]
```

### Applications

- **Heat engines**: internal combustion engines, steam turbines, and gas turbines rely on cyclic thermodynamic processes converting heat input into net work output, analyzed via First Law energy balances over each cycle.
- **Refrigeration and HVAC systems**: heat pumps and refrigerators use work input to move heat from a cold reservoir to a hot reservoir, against the natural direction of spontaneous heat flow.
- **Atmospheric science**: adiabatic cooling and heating of air parcels as they rise or descend (adiabatic lapse rate) governs cloud formation and weather phenomena.
- **Compressors and pumps**: work input increases the internal energy and pressure of a working fluid in industrial and HVAC compression systems.
- **Calorimetry and chemical thermodynamics**: heat released or absorbed during reactions (enthalpy changes) is measured using First Law principles under constant-pressure or constant-volume conditions.

### Common Misconceptions

- Heat and work are not properties "contained" within a system — only internal energy is a state property; heat and work exist only as energy *in transit* during a process and cannot be said to be stored in a system.
- A system does not need to lose internal energy to do work in all cases — in an isothermal expansion, work is done entirely using heat absorbed from the surroundings, with no net change in internal energy.
- Adiabatic does not mean "no temperature change" — it means no heat exchange; temperature can still change substantially due to work done by or on the system (e.g., adiabatic cooling during rapid gas expansion).
- $\Delta U = 0$ does not imply that $Q = 0$ and $W = 0$ individually — it only implies $Q = W$ (physics convention), as in the isothermal ideal gas case.

**Related Topics**:

- Zeroth Law of Thermodynamics and Temperature
- Specific Heat Capacity and Heat Capacity Ratios ($C_p$, $C_v$)
- Ideal Gas Law and Kinetic Theory of Gases
- Thermodynamic Cycles: Carnot, Otto, Diesel, Rankine
- Second Law of Thermodynamics and Entropy
- Enthalpy and Constant-Pressure Processes