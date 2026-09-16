## Similarity Laws and Specific Speed


### Overview

Similarity laws (also called affinity laws or scaling laws) allow turbomachinery performance to be predicted across different operating speeds, sizes, or geometrically similar designs without requiring full-scale testing at every condition. Specific speed is a derived dimensionless (or dimensional) parameter that classifies turbomachines by their fundamental geometric family, independent of absolute size, enabling systematic pump/turbine/compressor selection and preliminary design. Together, these tools form the foundation of turbomachinery design scaling, model testing, and machine selection methodology.

### Dimensional Analysis Basis

Turbomachinery performance depends on several physical variables: flow rate $Q$, head $H$ (or pressure rise $\Delta P$), rotational speed $N$, power $P$, impeller/runner diameter $D$, fluid density $\rho$, and fluid viscosity $\mu$ (usually neglected for most practical scaling since Reynolds number effects are secondary for geometrically similar machines at high Reynolds numbers).

Applying the Buckingham Pi theorem to these variables yields a set of dimensionless groups (pi terms) that fully characterize turbomachine performance independent of absolute scale:

$$\Pi_1 = \frac{Q}{ND^3} \quad \text{(flow coefficient)}$$



$$\Pi_2 = \frac{gH}{N^2D^2} \quad \text{(head coefficient)}$$



$$\Pi_3 = \frac{P}{\rho N^3 D^5} \quad \text{(power coefficient)}$$

**Key Points**

- These dimensionless coefficients are the rigorous basis from which both the similarity (affinity) laws and specific speed are derived.
- Machines are considered **dynamically similar** if these dimensionless coefficients match at corresponding operating points, meaning their velocity triangles (and thus flow patterns, relative to blade geometry) are geometrically similar throughout the machine — this is the underlying physical requirement that makes scaling valid.

### Similarity (Affinity) Laws

For **the same pump/turbine** (fixed diameter $D$) operating at different speeds $N$, the affinity laws follow directly from holding the dimensionless coefficients constant:

$$\frac{Q_2}{Q_1} = \frac{N_2}{N_1}$$



$$\frac{H_2}{H_1} = \left(\frac{N_2}{N_1}\right)^2$$



$$\frac{P_2}{P_1} = \left(\frac{N_2}{N_1}\right)^3$$

For **geometrically similar machines of different diameter** operating at the same speed:

$$\frac{Q_2}{Q_1} = \left(\frac{D_2}{D_1}\right)^3$$



$$\frac{H_2}{H_1} = \left(\frac{D_2}{D_1}\right)^2$$



$$\frac{P_2}{P_1} = \left(\frac{D_2}{D_1}\right)^5$$

For the **general case** (both speed and diameter changing between similar machines):

$$\frac{Q_2}{Q_1} = \left(\frac{N_2}{N_1}\right)\left(\frac{D_2}{D_1}\right)^3$$



$$\frac{H_2}{H_1} = \left(\frac{N_2}{N_1}\right)^2\left(\frac{D_2}{D_1}\right)^2$$



$$\frac{P_2}{P_1} = \left(\frac{N_2}{N_1}\right)^3\left(\frac{D_2}{D_1}\right)^5$$

**Key Points**

- The affinity laws are strictly valid only for a single, unchanged pump geometry at varying speed, or between truly geometrically similar (scaled) machines — applying them across dissimilar designs, or across very large speed/diameter ratios where Reynolds number effects or cavitation behavior change significantly, introduces increasing error. [Inference — well-established caveat in turbomachinery engineering practice.]
- Efficiency is assumed approximately constant between the compared operating points in the ideal affinity law derivation; in practice, small efficiency changes do occur (particularly for large speed changes or scale-up from small models to full-size machines), and empirical correction factors (e.g., Moody's scale-up formulas for hydraulic turbines) are sometimes applied for greater accuracy at large scale ratios. [Inference — standard practical refinement noted in hydraulic machinery literature.]
- These laws are foundational to variable-speed pump/fan control (predicting performance at reduced speed from a known full-speed curve) and to model testing of large turbines/pumps at reduced scale before full-size manufacture.

### Specific Speed

Specific speed is a single dimensionless (or, in common engineering practice, dimensional) parameter derived by combining the flow, head, and speed coefficients to eliminate the diameter term, yielding a parameter that characterizes a machine's fundamental geometric shape/type independent of its absolute size.

#### Pump Specific Speed

$$N_s = \frac{N\sqrt{Q}}{H^{3/4}}$$

where $N$ is rotational speed, $Q$ is flow rate at the best efficiency point, and $H$ is head at the best efficiency point. The exact numerical value and its "typical" ranges depend on the unit convention used (rpm/gpm/ft in US customary units; rpm/m³s⁻¹/m in metric units; or fully dimensionless forms), so specific speed values are only meaningful when the convention is specified.

**Key Points**

- Low specific speed (low flow, high head) corresponds to **radial-flow** pump designs (narrow, high-head impellers).
- Medium specific speed corresponds to **mixed-flow** pump designs.
- High specific speed (high flow, low head) corresponds to **axial-flow** (propeller-type) pump designs.
- This progression directly parallels the impeller geometry continuum described for centrifugal/axial pumps — specific speed is the quantitative tool used to select the appropriate geometric family for a given duty point during preliminary design.

#### Turbine Specific Speed

$$N_s = \frac{N\sqrt{P}}{H^{5/4}}$$

where $P$ is power output (rather than flow rate, as used for pumps — turbine specific speed conventionally uses power since it's the primary output of interest for turbines).

**Key Points**

- Low specific speed corresponds to Pelton (impulse) turbines, suited to high-head, low-flow conditions.
- Medium specific speed corresponds to Francis (mixed-flow reaction) turbines.
- High specific speed corresponds to Kaplan/propeller (axial-flow reaction) turbines.
- This mirrors the turbine selection framework by head/flow described previously, with specific speed serving as the quantitative selection parameter that consolidates head, flow (via power), and speed into a single design-guiding number.

```mermaid
flowchart TD
    A[Specific Speed Spectrum] (svg_diagram)
    A --> B[Low Ns: High Head, Low Flow]
    A --> C[Medium Ns: Medium Head, Medium Flow]
    A --> D[High Ns: Low Head, High Flow]
    B --> E[Pumps: Radial-Flow Impellers]
    B --> F[Turbines: Pelton]
    C --> G[Pumps: Mixed-Flow Impellers]
    C --> H[Turbines: Francis]
    D --> I[Pumps: Axial-Flow Impellers]
    D --> J[Turbines: Kaplan / Propeller]
```

#### Suction Specific Speed

A related but distinct parameter, **suction specific speed** ($N_{ss}$), characterizes a pump's cavitation/NPSH susceptibility rather than its overall geometric family:

$$N_{ss} = \frac{N\sqrt{Q}}{(NPSH_R)^{3/4}}$$

**Key Points**

- Suction specific speed uses $NPSH_R$ (required NPSH) in place of total head $H$, providing a scale-independent parameter for comparing pump designs' cavitation resistance and for setting suction-side design guidelines.
- High suction specific speed designs generally have narrower acceptable operating ranges near BEP with respect to cavitation risk, and pumps with very high suction specific speed values may be more susceptible to suction recirculation damage at off-BEP flow conditions. [Inference — recognized practical consideration in pump engineering literature.]

### Practical Applications of Similarity Laws and Specific Speed

**Key Points**

- **Model testing**: Large hydraulic turbines are frequently tested first as scaled-down physical models in a laboratory, with results scaled up to predict full-size prototype performance using the similarity laws (and empirical scale-up corrections for efficiency) — this is standard practice for large, expensive, custom-engineered hydro turbines where full-scale prototype testing before commitment is impractical. [Inference — well-established industry practice, e.g., per IEC model acceptance testing standards.]
- **Pump/turbine family selection**: Specific speed is calculated early in the design process from the required duty point (head, flow, speed) to determine which broad geometric family (radial, mixed, axial for pumps; Pelton, Francis, Kaplan for turbines) is appropriate, narrowing the design space before detailed hydraulic design begins.
- **Variable-speed operation prediction**: The affinity laws allow prediction of a pump's or fan's head-flow-power curve at a different (typically reduced) operating speed from a known reference curve, essential for VFD-controlled pump/fan system design and energy savings analysis.
- **Impeller trimming**: A common field/manufacturing practice where a pump impeller's outer diameter is machined down (trimmed) to reduce head/flow output to match a specific system requirement without needing a different pump casing; the diameter-based affinity laws (approximately, since trimming isn't a perfectly geometrically similar scaling) are used to predict the resulting performance change. [Inference — trimming affinity law application is a widely used industry approximation, though it is technically an approximation since trimming changes only the impeller's outer diameter, not fully preserving geometric similarity throughout the machine, so it is more accurate over modest trim ranges than large ones.]

### Cordier Diagram

**Key Points**

- The **Cordier diagram** is an empirically developed chart plotting specific speed against specific diameter, representing the locus of specific speed/diameter combinations at which well-designed turbomachines (compiled from a wide historical dataset of successful designs) tend to achieve peak efficiency — serving as an empirical preliminary design guide for selecting impeller/runner diameter once specific speed is known from duty point requirements.
- This provides a practical bridge from a duty point's specific speed (a machine-family classifier) to actual physical impeller sizing, complementing the more theoretical similarity/affinity law framework.

**Example**

A design engineer needing a pump for a duty point of 500 m³/h flow, 20 m head, at 1450 rpm would calculate the pump specific speed to determine that a mixed-flow (rather than purely radial or purely axial) impeller geometry is the appropriate family for this duty, then use affinity laws to predict how the selected pump's performance would change if driven by a variable-frequency drive at 1200 rpm instead of the nameplate 1450 rpm, before finalizing detailed impeller design. [Inference — illustrative representative example of the design workflow; not a specific documented case.]

**Next Steps**

- Turbomachinery Model Testing and Scale-Up Corrections (IEC Standards)
- Impeller Trimming Practice and Limitations
- Cavitation and Suction Specific Speed Design Guidelines
- Variable-Speed Drive Applications in Pump/Fan Systems
- Cordier Diagram Application in Preliminary Turbomachinery Design
- Dimensional Analysis and the Buckingham Pi Theorem in Fluid Machinery