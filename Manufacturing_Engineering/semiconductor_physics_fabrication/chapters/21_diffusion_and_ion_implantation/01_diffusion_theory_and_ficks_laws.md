## Diffusion Theory and Fick's Laws


### Overview and Fundamental Principle

Diffusion is the thermally activated process by which dopant atoms migrate through a crystalline silicon lattice, driven by concentration gradients, to redistribute from regions of high concentration toward regions of low concentration. Fick's laws provide the mathematical framework describing this transport process, forming the theoretical foundation for predicting dopant profiles resulting from high-temperature diffusion process steps in semiconductor fabrication.

**Key Points**

- Diffusion remains fundamental to understanding dopant redistribution during any high-temperature process step, even in modern processes where ion implantation (rather than pre-deposition diffusion) is the primary dopant introduction method, since post-implant anneals inevitably involve some degree of diffusive spreading
- Fick's First Law describes the instantaneous diffusive flux in response to a concentration gradient; Fick's Second Law describes how concentration profiles evolve over time as a consequence of that flux
- Diffusion coefficients (diffusivities) are strongly temperature-dependent, following Arrhenius behavior, making process temperature the dominant lever for controlling diffusion-related dopant redistribution
- Solutions to Fick's Second Law under specific boundary conditions (constant surface concentration, limited source) yield the two classical dopant profile shapes used throughout process design: the complementary error function and the Gaussian profile

### Fick's First Law

**Key Points**

- Fick's First Law states that the diffusive flux $J$ of dopant atoms is proportional to the negative concentration gradient:

$$J = -D\frac{\partial C}{\partial x}$$

where $J$ is the flux (atoms per unit area per unit time), $D$ is the diffusion coefficient (diffusivity), and $\partial C/\partial x$ is the concentration gradient along the diffusion direction

- The negative sign reflects that flux flows in the direction of decreasing concentration, consistent with the physical picture of net atomic migration from high-concentration to low-concentration regions
- This law describes an instantaneous, steady-state relationship between flux and gradient; it does not by itself describe how the concentration profile changes over time, which requires Fick's Second Law

### Fick's Second Law

**Key Points**

- Fick's Second Law is derived by combining Fick's First Law with the continuity equation (conservation of dopant atoms), yielding the diffusion equation describing concentration evolution in time:

$$\frac{\partial C}{\partial t} = D\frac{\partial^2 C}{\partial x^2}$$

(assuming $D$ is independent of concentration and position, i.e., constant-diffusivity conditions)

- This partial differential equation, combined with appropriate initial and boundary conditions specific to a given process (e.g., constant surface concentration source, or a fixed finite dose deposited at the surface), yields the concentration-versus-depth-versus-time profiles used in process design
- For concentration-dependent diffusivity (common at high dopant concentrations, discussed below), the equation generalizes to $\partial C/\partial t = \partial/\partial x [D(C)\, \partial C/\partial x]$, requiring numerical rather than closed-form analytical solution

### Predeposition (Constant Surface Concentration) Solution

**Process Sequence (Predeposition Diffusion):**

1. The silicon surface is exposed to a dopant source (historically a gas-phase source such as POCl₃ for phosphorus, or a solid/liquid source) maintained at a level sufficient to sustain the dopant's **solid solubility limit** concentration at the surface throughout the diffusion time
2. Under this boundary condition, the resulting solution to Fick's Second Law is the **complementary error function (erfc) profile**:

$$C(x,t) = C_s \cdot \text{erfc}\left(\frac{x}{2\sqrt{Dt}}\right)$$

where $C_s$ is the constant surface concentration (solid solubility limit) and $Dt$ is the diffusion length squared parameter

3. The total dopant dose introduced into the silicon (integrated area under the concentration profile) increases with diffusion time, since the boundary condition maintains a constant, unlimited surface source throughout the process

**Key Points**

- The erfc profile is characterized by a fixed surface concentration $C_s$ (set by the dopant's solid solubility at the process temperature, an intrinsic material property) with concentration decreasing monotonically into the depth of the substrate
- Historically used in predeposition steps of two-step diffusion processes (predeposition followed by drive-in), though largely superseded by ion implantation for dose control precision in modern processes
- The characteristic diffusion length $\sqrt{Dt}$ determines the junction depth for a given background substrate doping level, since junction depth is defined where $C(x_j, t)$ equals the background concentration

### Drive-In (Limited Source/Gaussian) Solution

**Process Sequence (Drive-In Diffusion):**

1. Following predeposition (or, in modern processes, following ion implantation), a fixed, finite quantity of dopant (dose $Q$, atoms per unit area) resides within a thin surface layer of the silicon
2. A subsequent high-temperature anneal (drive-in) redistributes this fixed dose deeper into the substrate without introducing additional dopant from an external source
3. Under this limited-source boundary condition, the resulting solution to Fick's Second Law is the **Gaussian profile**:

$$C(x,t) = \frac{Q}{\sqrt{\pi Dt}}\exp\left(-\frac{x^2}{4Dt}\right)$$

where $Q$ is the fixed total dose per unit area

**Key Points**

- Unlike the erfc profile, the Gaussian profile's peak surface concentration decreases as the drive-in proceeds (since the fixed dose spreads over an increasing depth), rather than remaining fixed at a solubility-limited value
- The Gaussian profile is the standard model describing post-implant anneal redistribution of ion-implanted dopant profiles, since implantation deposits a well-defined, finite dose at a controlled depth, closely matching the limited-source boundary condition assumption
- Total dose $Q$ is conserved throughout drive-in (in the idealized model, neglecting surface segregation or outdiffusion losses), meaning the area under the Gaussian profile remains constant while its width increases and peak height decreases with increasing $Dt$

### Diffusion Profile Comparison Diagram (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 360">
<text x="320" y="24" font-size="15" font-family="sans-serif" text-anchor="middle" font-weight="bold">erfc vs. Gaussian Diffusion Profiles (svg_diagram)</text>

<line x1="80" y1="300" x2="580" y2="300" stroke="#000" stroke-width="1.5" />
<line x1="80" y1="300" x2="80" y2="60" stroke="#000" stroke-width="1.5" />
<text x="330" y="335" font-size="12" text-anchor="middle" font-family="sans-serif">Depth (x)</text>
<text x="30" y="180" font-size="12" text-anchor="middle" font-family="sans-serif" transform="rotate(-90 30 180)">Concentration C(x)</text>

<path d="M 80 90 Q 200 100 300 200 Q 380 260 500 290" fill="none" stroke="#2980b9" stroke-width="3" />
<text x="150" y="80" font-size="10" font-family="sans-serif" fill="#2980b9" font-weight="bold">erfc (Predeposition)</text>

<path d="M 80 150 Q 150 155 220 220 Q 300 280 400 295 L 580 298" fill="none" stroke="#c0392b" stroke-width="3" />
<text x="150" y="140" font-size="10" font-family="sans-serif" fill="#c0392b" font-weight="bold">Gaussian (Drive-in)</text>

<line x1="80" y1="280" x2="580" y2="280" stroke="#666" stroke-width="1" stroke-dasharray="5,3" />
<text x="550" y="275" font-size="9" font-family="sans-serif" fill="#666">Background doping</text>

<line x1="300" y1="280" x2="300" y2="300" stroke="#000" stroke-width="1" stroke-dasharray="2,2" />
<text x="300" y="315" font-size="9" text-anchor="middle" font-family="sans-serif">x_j</text>
</svg>

### Temperature Dependence of Diffusivity

**Key Points**

- Diffusivity $D$ follows Arrhenius temperature dependence:

$$D = D_0\exp\left(-\frac{E_A}{k_BT}\right)$$

where $D_0$ is a pre-exponential factor and $E_A$ is the activation energy for diffusion, both dopant-species-specific and dependent on the underlying atomic diffusion mechanism

- Different dopant species exhibit substantially different diffusivities and activation energies in silicon: boron and phosphorus generally diffuse via similar interstitial-mediated mechanisms with broadly comparable diffusivities, while arsenic and antimony diffuse more slowly, largely via a vacancy-mediated mechanism, making them preferred for applications requiring shallow, well-controlled junctions
- The strong (exponential) temperature dependence of diffusivity means that even modest process temperature variations produce significant changes in resulting junction depth, making precise furnace/anneal temperature control a critical process requirement

### Diffusion Mechanisms in Silicon

**Key Points**

- **Vacancy-mediated diffusion**: Dopant atoms occupying substitutional lattice sites migrate by exchanging position with an adjacent vacancy (missing lattice atom); this mechanism dominates for larger substitutional dopants such as antimony
- **Interstitial-mediated diffusion (interstitialcy mechanism)**: Dopant atoms migrate via a kick-out or interstitialcy mechanism involving silicon self-interstitials, believed to be the dominant mechanism for boron and, to a significant degree, phosphorus
- **Interstitial diffusion (direct)**: Some species (though generally not the common substitutional dopants) can diffuse directly through interstitial lattice sites without displacing a lattice atom, generally exhibiting much higher diffusivity than substitutional mechanisms when applicable
- The specific diffusion mechanism for a given dopant directly determines its coupling to point defect concentrations (vacancies and interstitials) present in the silicon lattice, which is the physical basis for point-defect-mediated anomalous diffusion effects such as transient enhanced diffusion following ion implantation

### Concentration-Dependent Diffusivity

**Key Points**

- At sufficiently high dopant concentrations (typically approaching or exceeding the intrinsic carrier concentration at the diffusion temperature), diffusivity becomes concentration-dependent rather than constant, since the local point defect (vacancy/interstitial) concentration is itself influenced by the Fermi level position, which shifts with dopant concentration
- This effect causes high-concentration diffusion profiles to deviate from the idealized erfc or Gaussian shapes, typically exhibiting steeper ("box-like") profiles at high concentration with more gradual tailing at lower concentration where the diffusivity reverts toward its intrinsic (concentration-independent) value
- Concentration-dependent diffusion effects are particularly relevant for heavily doped source/drain and emitter regions, requiring numerical process simulation (rather than closed-form analytical solutions) for accurate profile prediction in these regimes

### Transient Enhanced Diffusion (Link to Ion Implantation)

**Key Points**

- Ion implantation introduces a high concentration of excess silicon self-interstitials as a byproduct of the implant damage, since the implanted ion's collision cascade displaces silicon lattice atoms
- These excess interstitials dramatically (transiently) enhance the diffusivity of interstitial-mediated dopants (notably boron) during the initial phase of post-implant annealing, an effect known as **Transient Enhanced Diffusion (TED)**, which can cause substantially greater dopant spreading than would be predicted by equilibrium diffusivity values alone
- TED is a critical consideration in advanced CMOS process design, since it can compromise the shallow junction depths required for scaled transistor architectures if not properly accounted for in anneal process design (e.g., via rapid thermal annealing to minimize total thermal budget exposure during the TED-active period)
- This phenomenon illustrates the important distinction between idealized Fick's-law equilibrium diffusion theory and the more complex point-defect-coupled diffusion behavior relevant to real ion-implanted process flows

### Comparison: erfc vs. Gaussian Diffusion Profiles

| Attribute | erfc (Predeposition/Constant Source) | Gaussian (Drive-in/Limited Source) |
| --- | --- | --- |
| Boundary condition | Constant surface concentration ($C_s$, solubility-limited) | Fixed finite dose $Q$, no external source |
| Surface concentration behavior | Remains constant at $C_s$ throughout process | Decreases over time as profile spreads |
| Total dose behavior | Increases with time (source continuously supplies dopant) | Conserved (fixed at initial dose $Q$) |
| Typical process context | Historical predeposition diffusion step | Post-implant anneal, drive-in step |
| Profile shape | Monotonic decrease from surface | Peaked at or near surface, symmetric-tailed decay |

### Process Design Application

**Example**

For a drive-in anneal following ion implantation with known dose $Q$, a process engineer selects anneal temperature $T$ and time $t$ to achieve a target junction depth $x_j$ (where the diffused profile concentration equals the background substrate doping $C_B$). Using the Gaussian solution:

$$x_j = 2\sqrt{Dt}\sqrt{\ln\left(\frac{Q}{C_B\sqrt{\pi Dt}}\right)}$$

This transcendental relationship is typically solved iteratively or via process simulation software, since $x_j$ appears on both sides implicitly through the $Dt$ product; the engineer selects $D$ (via temperature, using the Arrhenius relationship) and $t$ jointly to satisfy both junction depth and total thermal budget constraints imposed by the overall process flow.

**Key Points**

- Thermal budget (the cumulative time-temperature exposure across all high-temperature process steps in a flow) is a critical overall process design constraint, since diffusion occurring during any subsequent high-temperature step (even ones not intended as dedicated diffusion steps) also contributes to net dopant redistribution
- Modern advanced CMOS processes favor rapid thermal annealing (RTA) and spike annealing techniques specifically to minimize total thermal budget and thereby limit unwanted diffusion, particularly important given the diffusivity enhancement effects (TED) associated with implant damage

### Next Steps

- **Ion Implantation Fundamentals: Range, Straggle, and Damage Profiles**
- **Transient Enhanced Diffusion and Point Defect Engineering**
- **Rapid Thermal Annealing and Spike Annealing Process Design**
- **Solid Solubility Limits of Common Dopants in Silicon**
- **Concentration-Dependent Diffusion Modeling and Process Simulation**
- **Junction Depth and Doping Profile Characterization Techniques (SIMS, SRP)**
- **Point Defect Mechanisms: Vacancies, Interstitials, and Dopant Coupling**
- **Thermal Budget Management Across a Complete Process Flow**