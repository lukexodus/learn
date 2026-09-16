## Climate Modeling and Projections


### Overview

Climate models are numerical representations of the physical, chemical, and biological processes governing Earth's climate system, used to simulate past climate states, understand present-day variability, and project future climate conditions under various forcing scenarios. Climate modeling spans a hierarchy of complexity, from simple energy balance models to fully coupled Earth System Models, and underpins the scientific basis for climate risk assessment, attribution studies, and policy planning.

### The Model Hierarchy

Climate models exist along a spectrum of complexity, with each tier serving different scientific purposes.

#### Energy Balance Models (EBMs)

- The simplest class, representing Earth's climate using globally or zonally averaged energy budgets.
- Useful for conceptual understanding of climate sensitivity and radiative forcing relationships without resolving spatial or dynamical detail.

#### Radiative-Convective Models (RCMs)

- Add vertical atmospheric structure, resolving how radiative transfer and convective heat transport interact to determine atmospheric temperature profiles.
- Historically important for early estimates of CO₂ doubling sensitivity (e.g., Manabe and Wetherald's foundational 1967 studies).

#### General Circulation Models (GCMs) / Atmosphere-Ocean GCMs (AOGCMs)

- Resolve three-dimensional fluid dynamics of the atmosphere and ocean using discretized grids, solving primitive equations of motion, thermodynamics, and continuity.
- Represent the core of most modern climate projection work, coupling atmospheric and oceanic circulation.

#### Earth System Models (ESMs)

- Extend AOGCMs by incorporating biogeochemical cycles (carbon cycle, nitrogen cycle), interactive vegetation, ice sheet dynamics, and atmospheric chemistry.
- Allow for representation of feedbacks between physical climate and biological/chemical systems (e.g., how vegetation changes affect surface albedo and carbon uptake, which in turn affects atmospheric CO₂ and radiative forcing).

```mermaid
flowchart LR
    A["Energy Balance Models (svg_diagram)"] --> B["Radiative-Convective Models"]
    B --> C["General Circulation Models / AOGCMs"]
    C --> D["Earth System Models"]
    A -.->|"Increasing complexity and spatial resolution"| D
```

### Core Physical and Numerical Foundations

#### Governing Equations

GCMs numerically solve a coupled system of equations derived from fluid dynamics and thermodynamics, commonly referred to as the **primitive equations**:

1. **Conservation of momentum** (Navier-Stokes equations adapted for a rotating sphere, incorporating the Coriolis effect).
2. **Conservation of mass** (continuity equation).
3. **Conservation of energy** (thermodynamic energy equation, incorporating radiative and latent heat fluxes).
4. **Ideal gas law** (relating pressure, density, and temperature).
5. **Conservation of water substance** (accounting for vapor, liquid, and ice phases).

$$\frac{\partial \mathbf{v}}{\partial t} + (\mathbf{v} \cdot \nabla)\mathbf{v} = -\frac{1}{\rho}\nabla p - 2\mathbf{\Omega} \times \mathbf{v} + \mathbf{g} + \mathbf{F}$$

This momentum equation describes how atmospheric velocity ($\mathbf{v}$) evolves under pressure gradient forces, the Coriolis effect ($\mathbf{\Omega}$ being Earth's rotation vector), gravity, and frictional forces ($\mathbf{F}$).

#### Discretization and Grid Structure

- Models divide the atmosphere and ocean into a three-dimensional grid (horizontal resolution typically 25–250 km for global models, with multiple vertical layers).
- **Spectral methods** and **finite-volume/finite-difference methods** represent the two dominant numerical approaches to solving the governing equations across the grid.
- Behavior may vary by specific model architecture and resolution choice; higher-resolution configurations better resolve mesoscale features (e.g., individual storm systems, ocean eddies) but at substantially increased computational cost.

#### Parameterization

Many physical processes occur at scales smaller than a model's grid resolution and cannot be explicitly resolved; these are represented through **parameterizations** — simplified statistical or empirical relationships approximating their net effect on the resolved-scale variables.

**Key Points**

- **Cloud formation and microphysics** — one of the largest sources of inter-model uncertainty, since cloud processes occur at scales far below typical grid resolution.
- **Convection** (particularly cumulus convection) — parameterized in most global models due to insufficient resolution to explicitly simulate individual convective cells.
- **Boundary layer turbulence** — surface-atmosphere heat, moisture, and momentum exchange.
- **Aerosol-cloud interactions** — representing how aerosol particles affect cloud droplet formation and radiative properties.

[Inference] Parameterization schemes are a leading source of structural uncertainty and inter-model spread in climate projections, since different modeling centers make different simplifying assumptions about unresolved processes; this is distinct from, though related to, uncertainty stemming from emissions scenario choice.

### Model Coupling and Components

A modern Earth System Model integrates multiple component models, each simulating a distinct subsystem, exchanged through a coupling framework:

| Component | Represents |
| --- | --- |
| Atmospheric model (AGCM) | Atmospheric circulation, radiation, clouds, precipitation |
| Ocean model (OGCM) | Ocean circulation, heat transport, salinity |
| Sea ice model | Sea ice extent, thickness, dynamics |
| Land surface model | Soil moisture, vegetation, surface energy/water balance |
| Carbon cycle model | Terrestrial and oceanic carbon fluxes |
| Atmospheric chemistry model | Trace gas and aerosol chemistry |
| Ice sheet model | Glacier and ice sheet mass balance and dynamics |

A **coupler** synchronizes and exchanges fluxes (heat, moisture, momentum, carbon) between these components at each model timestep.

### Model Evaluation and Validation

#### Hindcasting and Historical Simulation

Models are evaluated by running historical simulations forced with observed past emissions and forcings, then comparing simulated output against the observational record (temperature, precipitation, sea ice extent, etc.) — a process sometimes referred to as **hindcasting**.

#### Model Intercomparison Projects

The **Coupled Model Intercomparison Project (CMIP)**, coordinated internationally, standardizes experimental protocols so that dozens of independently developed models from different research centers worldwide can be directly compared under identical forcing scenarios. CMIP output forms the primary basis for IPCC Assessment Report projections. [Unverified] The specific current CMIP phase and its associated scenario protocols should be verified against the latest World Climate Research Programme documentation, as intercomparison phases are periodically updated.

#### Skill Metrics

- Models are assessed on their ability to reproduce observed climatological means, variability patterns (e.g., ENSO characteristics), and trends.
- **Emergent constraints** — a technique using observed relationships between present-day climate variables and model spread to statistically narrow the range of projected quantities (e.g., climate sensitivity), based on which models best match observed real-world relationships. [Inference] This technique carries inherent statistical caveats, since a physically plausible relationship in the historical record does not guarantee predictive validity for future, potentially unprecedented forcing conditions.

### Sources of Projection Uncertainty

**Key Points**

- **Scenario uncertainty** — arises from not knowing future greenhouse gas emission trajectories, which depend on unpredictable socioeconomic, technological, and policy factors (addressed through the RCP/SSP scenario framework).
- **Model (structural) uncertainty** — arises from differences in how various models represent physical processes, parameterizations, and resolution, producing a spread of results even under identical forcing scenarios.
- **Internal variability uncertainty** — arises from the climate system's inherent chaotic variability (e.g., ENSO phase), which is irreducible on shorter timescales regardless of model quality; **initial condition ensembles** (running the same model many times with minutely perturbed starting conditions) are used to characterize this component.

$$\text{Total Projection Uncertainty} = f(\text{Scenario}, \text{Model Structure}, \text{Internal Variability})$$

[Inference] The relative contribution of each uncertainty source varies with projection timescale — internal variability dominates near-term (interannual to decadal) projection uncertainty, while scenario uncertainty tends to dominate by the latter half of the 21st century, based on standard uncertainty partitioning studies in the climate modeling literature.

### Downscaling Techniques

Global climate models typically operate at spatial resolutions too coarse (tens to hundreds of kilometers) for regional or local-scale impact assessment. **Downscaling** techniques bridge this gap:

1. **Dynamical downscaling** — Nesting a higher-resolution Regional Climate Model (RCM) within a coarser global model's output, explicitly resolving finer-scale atmospheric dynamics over a limited domain at greater computational cost.
2. **Statistical downscaling** — Applying empirical statistical relationships derived between historical large-scale climate variables and local-scale observations to translate coarse global model output into higher-resolution local projections, at lower computational cost but reliant on the assumption that historical statistical relationships remain valid under future climate conditions.

### Model Applications

**Example**

- **Detection and attribution studies** — comparing simulations with and without anthropogenic forcing to isolate the human-caused component of observed change.
- **Paleoclimate simulation** — testing model performance against reconstructed past climate states (e.g., the Last Glacial Maximum, mid-Holocene) as an independent validation exercise outside the range of the instrumental record.
- **Extreme event attribution** — using large ensembles of model simulations to estimate how anthropogenic forcing has altered the probability or intensity of a specific observed extreme event.
- **Sea level rise projection** — combining ocean thermal expansion output from AOGCMs with ice sheet model projections to generate regional and global sea level rise estimates.

### Limitations and Ongoing Challenges

**Key Points**

- Cloud feedback representation remains one of the largest persistent sources of inter-model spread in climate sensitivity estimates.
- Ice sheet dynamics (particularly rapid, nonlinear processes like marine ice sheet instability) are challenging to represent with high confidence, contributing disproportionate uncertainty to long-term sea level rise projections.
- Regional precipitation projections generally carry substantially higher uncertainty than global or regional temperature projections, due to the complex, small-scale, and often parameterized nature of precipitation-generating processes.
- Computational cost fundamentally constrains the trade-off between model resolution, ensemble size (number of simulations), and Earth system complexity (number of coupled components) achievable within a given research timeframe.

**Related Topics**

- Radiative Forcing and Climate Sensitivity
- The Carbon Cycle and Biogeochemical Feedbacks
- Paleoclimate Reconstruction and Proxy Records
- Extreme Event Attribution Methodology
- Ice Sheet Dynamics and Sea Level Rise Projections
- IPCC Assessment Report Structure and Scenario Frameworks (SSPs)
- Numerical Weather Prediction vs. Climate Modeling
- Regional Climate Downscaling Techniques