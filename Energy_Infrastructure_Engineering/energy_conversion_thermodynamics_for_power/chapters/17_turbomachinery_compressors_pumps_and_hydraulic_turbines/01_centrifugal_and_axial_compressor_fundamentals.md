## Centrifugal and Axial Compressor Fundamentals


### Overview

Compressors are turbomachines that increase the pressure of a gas by adding mechanical work through rotating blades or impellers, converting shaft work into increased gas pressure and, typically, increased temperature. They are fundamental components in gas turbine engines, industrial process compression, refrigeration/HVAC systems, and pipeline transport. The two dominant architectures are **centrifugal (radial-flow)** and **axial-flow** compressors, distinguished primarily by the direction of gas flow relative to the rotor axis.

### Fundamental Thermodynamics of Compression

#### Work Input and the Euler Turbomachinery Equation

For any turbomachine, the specific work transferred between the rotor and the fluid is given by the Euler turbomachinery equation:

$$w = U_2 C_{\theta 2} - U_1 C_{\theta 1}$$

where $U$ is the blade tangential (peripheral) velocity, $C_\theta$ is the tangential component of absolute fluid velocity, and subscripts 1 and 2 denote inlet and outlet (rotor exit) conditions, respectively. For a compressor, work is done **on** the fluid, increasing its stagnation enthalpy.

#### Ideal vs. Actual Compression Work

The ideal (isentropic) work required to compress a gas from pressure $P_1$ to $P_2$ is:

$$w_{s} = \frac{\gamma}{\gamma - 1} R T_1 \left[ \left( \frac{P_2}{P_1} \right)^{\frac{\gamma-1}{\gamma}} - 1 \right]$$

where $\gamma$ is the specific heat ratio, $R$ is the specific gas constant, and $T_1$ is inlet stagnation temperature. Actual work required exceeds this ideal value due to irreversibilities (friction, flow separation, mixing losses), captured by **isentropic efficiency**:

$$\eta_{isen} = \frac{w_s}{w_{actual}} = \frac{T_{2s} - T_1}{T_2 - T_1}$$

where $T_{2s}$ is the temperature that would result from isentropic compression to the same final pressure, and $T_2$ is the actual outlet temperature.

**Key Points**

- Isentropic efficiency is the standard metric for comparing compressor performance; well-designed axial compressor stages typically achieve higher isentropic efficiencies than single centrifugal stages for a given pressure ratio, though multistage centrifugal machines can achieve high overall efficiencies as well. [Inference — general trend widely cited in turbomachinery literature; specific efficiency values are design- and application-dependent.]
- Actual compression is polytropic in nature for multistage machines; **polytropic efficiency** is often used instead of isentropic efficiency for multistage compressors since it better represents stage-by-stage performance independent of overall pressure ratio.

#### Polytropic Efficiency

$$\eta_{poly} = \frac{n-1}{n} \cdot \frac{\gamma}{\gamma - 1}$$

where $n$ is the polytropic exponent describing the actual compression process ($Pv^n = constant$). Polytropic efficiency is a more consistent metric across different pressure ratios for the same machine, since isentropic efficiency mathematically decreases with increasing pressure ratio even for a machine with constant "quality" of compression at each incremental stage. [Inference — standard turbomachinery theory explaining why polytropic efficiency is preferred for multistage comparison.]

### Centrifugal (Radial-Flow) Compressors

#### Working Principle

Gas enters axially near the center (eye) of a rotating **impeller** and is turned radially outward, accelerated by centrifugal force and impeller blade action, exiting at the impeller tip with high velocity and increased static pressure. This high-velocity gas then passes through a stationary **diffuser**, where kinetic energy is converted into further static pressure rise as velocity decreases (per the diffuser's increasing flow area).

**Key Points**

- A single centrifugal stage can achieve a substantially higher pressure ratio than a single axial stage, since the combination of centrifugal force and the large radius change (impeller eye to tip) provides much greater energy addition per stage — single centrifugal stage pressure ratios commonly range from roughly 2:1 to 8:1 or higher depending on design (particularly for high-speed, high pressure-ratio industrial designs), compared to typical axial stage pressure ratios in the range of roughly 1.1:1 to 1.4:1. [Inference — general order-of-magnitude industry knowledge; exact figures vary significantly by specific design, tip speed, and application.]
- This makes centrifugal compressors attractive where high pressure ratio is needed in a compact, mechanically robust package with fewer stages.

#### Centrifugal Compressor Components

- **Inducer**: The initial curved section of the impeller blades that turns incoming axial flow into the radial direction with minimal incidence loss.
- **Impeller (rotor)**: The rotating component that does work on the gas; may be **open** (unshrouded, blades exposed) or **shrouded** (covered on the outer edge), with open impellers generally tolerating higher tip speeds and shrouded impellers offering somewhat better efficiency at lower speeds due to reduced tip leakage losses. [Inference — general design tradeoff cited in turbomachinery references.]
- **Diffuser**: Stationary passage downstream of the impeller that decelerates flow, converting kinetic energy to static pressure; may be **vaned** (fixed guide vanes controlling flow angle, generally higher efficiency but narrower stable operating range) or **vaneless** (simple annular passage, broader operating range but somewhat lower peak efficiency). [Inference — standard tradeoff documented in compressor design literature.]
- **Volute (scroll) casing**: Collects diffused gas from the full circumference and directs it to a single discharge pipe, with a gradually increasing cross-sectional area designed to maintain roughly uniform velocity as flow accumulates around the circumference.
- **Return channel/crossover** (multistage machines): Directs flow from one stage's diffuser exit back to the next stage's impeller eye, including deswirl vanes to remove residual tangential velocity before it re-enters the next impeller.

```mermaid
flowchart LR
    A[Axial Inlet Flow] --> B[Impeller Eye / Inducer]
    B --> C[Impeller - Radial Acceleration]
    C --> D[Vaned or Vaneless Diffuser]
    D --> E[Volute / Scroll Casing]
    E --> F[Discharge]
```

#### Velocity Triangles (Centrifugal Impeller Exit)

At the impeller tip, the relationship between blade velocity $U_2$, relative velocity $W_2$, and absolute velocity $C_2$ follows standard velocity triangle decomposition:

$$\vec{C_2} = \vec{U_2} + \vec{W_2}$$

**Key Points**

- **Backward-swept blades** (blade exit angle leaning against rotation direction) are common in modern centrifugal compressor design, offering a more stable pressure-flow characteristic (wider stable operating range, reduced susceptibility to surge) at some cost in maximum achievable pressure ratio per stage, compared to radial or forward-swept blades. [Inference — well-established design principle in centrifugal compressor literature.]
- **Slip factor** accounts for the fact that actual gas flow does not perfectly follow the blade curvature at exit (due to the inertia of the fluid relative to the rotating blade passage), reducing actual tangential velocity (and thus actual work input) below the idealized value predicted by blade geometry alone; various empirical correlations (e.g., Stodola, Stanitz) are used to estimate slip factor in design calculations.

### Axial-Flow Compressors

#### Working Principle

Gas flows generally parallel to the rotor axis through alternating rows of rotating **rotor blades** and stationary **stator vanes**, with each rotor-stator pair constituting one **stage**. The rotor blades add kinetic energy (increasing both tangential velocity and, through blade shape, some static pressure rise), and the following stator row decelerates the flow (converting kinetic energy to further static pressure rise) while also redirecting flow angle to the correct incidence for the next rotor row.

**Key Points**

- Because each stage produces only a modest pressure ratio, achieving high overall pressure ratios (common in jet engines and large industrial gas turbines, sometimes 15:1 to 40:1 or higher) requires many stages in series. [Inference — general order-of-magnitude figures widely cited for modern gas turbine compressors; exact stage counts and ratios are engine/design-specific.]
- Axial compressors generally achieve higher efficiency and higher mass flow capacity per unit frontal area than centrifugal compressors of comparable duty, making them the preferred choice for large gas turbines and jet engines where minimizing frontal area (drag) and maximizing efficiency across many stages is paramount. [Inference — standard comparative reasoning in gas turbine/turbomachinery literature.]

#### Axial Compressor Components

- **Rotor blades**: Aerofoil-shaped blades mounted on the rotating drum/disk, doing work on the flow.
- **Stator vanes**: Stationary aerofoil blades mounted to the casing, redirecting flow angle and diffusing velocity to pressure.
- **Inlet guide vanes (IGVs)**: An optional stationary row upstream of the first rotor stage, pre-swirling the incoming flow to the optimal angle for the first rotor row; often made **variable** (VIGVs) to adjust flow angle across different operating conditions, particularly for off-design/part-load operation and surge margin control.
- **Variable stator vanes (VSVs)**: In modern multistage compressors, several of the early-stage stator rows are often made variable (adjustable angle) to maintain acceptable flow incidence and surge margin across a wide operating speed range, since fixed-geometry compressors optimized for one operating point can experience mismatched flow angles at off-design conditions.
- **Casing**: May incorporate abradable seal coatings opposite blade tips to minimize tip clearance losses while tolerating minor rotor-to-casing contact without catastrophic damage.

```mermaid
flowchart LR
    A[Inlet Guide Vanes - IGV] --> B[Rotor Stage 1]
    B --> C[Stator Stage 1]
    C --> D[Rotor Stage 2]
    D --> E[Stator Stage 2]
    E --> F[... Additional Stages ...]
    F --> G[Compressor Discharge]
```

#### Velocity Triangles and Stage Loading (Axial)

For an axial compressor stage, work input per stage relates to the change in tangential velocity across the rotor:

$$w_{stage} = U (C_{\theta 2} - C_{\theta 1})$$

where $U$ is blade speed (assumed constant through a constant-mean-radius stage) and $C_{\theta 1}$, $C_{\theta 2}$ are tangential velocity components at rotor inlet and exit.

**Key Points**

- **Degree of reaction** describes the proportion of static enthalpy (pressure) rise occurring in the rotor versus the stator within a stage; a 50% reaction design (common in many axial compressors) splits static pressure rise roughly evenly between rotor and stator, often chosen for favorable blade loading and efficiency characteristics. [Inference — standard turbomachinery design convention; exact optimal reaction varies by specific design objectives.]
- Diffusion factor and de Haller number are common empirical criteria used to limit blade loading per stage and avoid excessive flow diffusion (deceleration) that would trigger boundary layer separation on blade surfaces, since axial compressor blades operate as diffusing (adverse pressure gradient) aerofoils, which are inherently more prone to separation than the accelerating (favorable pressure gradient) blading found in turbines.

### Comparison: Centrifugal vs. Axial Compressors

| Characteristic | Centrifugal | Axial |
| --- | --- | --- |
| Flow direction | Radial (turns 90° from axial inlet) | Parallel to shaft axis |
| Pressure ratio per stage | High (~2:1 to 8:1+) | Low (~1.1:1 to 1.4:1) |
| Stages needed for high overall ratio | Few | Many |
| Efficiency (typical) | Good, often slightly lower per-stage than axial | Generally higher, especially at large scale |
| Frontal area / flow capacity | Larger frontal area per unit flow | More compact, higher flow per frontal area |
| Operating range (surge margin) | Generally wider | Generally narrower, especially at high pressure ratio |
| Mechanical robustness | Simpler, fewer parts, tolerant of some fouling | More complex, many precision blade rows |
| Typical applications | Industrial gas compression, turbochargers, small gas turbines, refrigeration | Jet engines, large industrial gas turbines, large process compressors |

### Compressor Performance Maps and Operating Limits

**Key Points**

- Compressor performance is characterized by a **map** plotting pressure ratio against corrected mass flow rate, with superimposed constant-speed lines and efficiency contours (islands), used for both design point selection and off-design operational analysis.
- **Surge**: A dynamic flow instability occurring when flow through the compressor drops below a critical minimum (surge line on the map) at a given pressure ratio, causing a sudden, often violent flow reversal and pressure oscillation; surge can cause severe mechanical damage from rapid flow/thrust reversals and is a critical operational limit that control systems (anti-surge valves/logic) are specifically designed to avoid.
- **Stall (rotating stall)**: A related but distinct instability where flow separates from blades in localized regions that propagate circumferentially around the annulus, which can occur before full surge and may or may not be self-sustaining depending on severity and compressor design; can be a precursor to surge if conditions worsen.
- **Choke**: The opposite operating limit, occurring at high flow rates when velocity approaches sonic conditions (Mach 1) at some point in the flow path (typically the narrowest passage), fundamentally limiting further mass flow increase regardless of further downstream pressure reduction.

```mermaid
flowchart TD
    A[Compressor Map - Pressure Ratio vs Corrected Flow] (svg_diagram)
    A --> B[Surge Line - left boundary, low flow instability]
    A --> C[Choke Line - right boundary, sonic flow limit]
    A --> D[Constant Speed Lines - N1, N2, N3...]
    A --> E[Efficiency Islands - contours of constant efficiency]
```

**Example**

A gas turbine compressor operating near its surge line during a rapid load rejection (sudden loss of downstream demand causing flow to drop while the compressor continues rotating near design speed) may trigger anti-surge control logic, which rapidly opens a recirculation/blow-off valve to maintain sufficient flow through the compressor and avoid entering the surge region, protecting the machine from potential blade and bearing damage that could result from an actual surge event.

**Next Steps**

- Compressor Surge and Anti-Surge Control Systems
- Multistage Axial Compressor Stacking and Stage Matching
- Variable Geometry (VIGV/VSV) Control Strategies
- Centrifugal Compressor Diffuser Design (Vaned vs. Vaneless)
- Compressor Performance Testing and Map Generation
- Gas Turbine Compressor Integration and Off-Design Operation
- Tip Clearance Effects and Casing Treatment for Efficiency/Stall Margin