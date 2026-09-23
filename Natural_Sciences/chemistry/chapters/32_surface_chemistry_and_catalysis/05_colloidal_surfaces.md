## Colloidal Surfaces


### Overview

Colloids are systems in which one substance (the dispersed phase) is distributed as fine particles throughout a continuous medium (the dispersion medium), with particle dimensions typically ranging from about 1 nm to 1 μm. At this size scale, the surface-area-to-volume ratio is extremely large, so interfacial (surface) phenomena dominate the physical and chemical behavior of colloidal systems, rather than bulk properties. Understanding colloidal surface chemistry is essential for stability control in paints, pharmaceuticals, food science, ceramics processing, and nanomaterials synthesis.

### Classification of Colloidal Systems

| Dispersed phase | Dispersion medium | Name | Example |
| --- | --- | --- | --- |
| Solid | Liquid | Sol | Gold sol, paint |
| Liquid | Liquid | Emulsion | Milk, mayonnaise |
| Gas | Liquid | Foam | Whipped cream, shaving foam |
| Solid | Gas | Solid aerosol | Smoke |
| Liquid | Gas | Liquid aerosol | Fog, aerosol spray |
| Solid | Solid | Solid sol | Colored glass, some alloys |
| Gas | Solid | Solid foam | Styrofoam |

**Key Points**

- Colloids are distinguished from true solutions (particle size < 1 nm) by their ability to scatter light (Tyndall effect) and from coarse suspensions (particle size > 1 μm) by their resistance to settling under gravity over reasonable timescales.
- Lyophilic ("solvent-loving") colloids have strong affinity between dispersed phase and medium (e.g., proteins, polymers in water) and are generally thermodynamically stable; lyophobic ("solvent-fearing") colloids (e.g., metal sols) lack this affinity and are only kinetically (not thermodynamically) stabilized.

### The Electrical Double Layer

Most colloidal particles in a polar medium (commonly water) acquire surface charge through ionization of surface groups, differential ion adsorption, or isomorphic substitution. This surface charge attracts a layer of oppositely charged counterions from solution, forming the electrical double layer.

**Key Points**

- **Stern layer:** a layer of counterions tightly bound (specifically adsorbed) close to the particle surface.
- **Diffuse layer:** counterions extend outward from the Stern layer with decreasing concentration, following a Boltzmann-type distribution, balanced against thermal diffusion.
- **Zeta potential ($\zeta$):** the electrical potential at the slipping plane (the boundary between the Stern layer and the mobile diffuse layer), measurable via electrophoretic mobility, and used as a practical proxy for surface charge and colloidal stability.
- The characteristic thickness of the diffuse layer, the Debye length $\kappa^{-1}$, decreases with increasing ionic strength:



  $$\kappa^{-1}=\sqrt{\frac{\varepsilon\varepsilon_0 k_BT}{2N_Ae^2I}}$$

  where $I$ is ionic strength, $\varepsilon$ is the medium's relative permittivity, and other symbols have their standard meanings.

```mermaid
flowchart LR
    A["Charged particle surface"] --> B["Stern layer (tightly bound counterions)"]
    B --> C["Slipping plane (zeta potential measured here)"]
    C --> D["Diffuse layer (mobile counterions, decaying concentration)"]
    D --> E["Bulk solution (electroneutral)"]
```

### DLVO Theory of Colloidal Stability

The Derjaguin–Landau–Verwey–Overbeek (DLVO) theory explains colloidal stability as the balance between two opposing interparticle forces as a function of separation distance $h$:

$$V_{total}(h)=V_{attractive}(h)+V_{repulsive}(h)$$

**Key Points**

- **Van der Waals attraction** ($V_{attractive}$): arises from induced dipole–induced dipole interactions between atoms in neighboring particles; for two spheres, approximated by:



  $$V_A(h)\approx-\frac{A_H R}{12h}$$

  where $A_H$ is the Hamaker constant (material-dependent) and $R$ is particle radius (for $h\ll R$).
- **Electrostatic (double-layer) repulsion** ($V_{repulsive}$): arises from overlap of the diffuse electrical double layers of approaching particles, decaying roughly exponentially with the Debye length.
- Summing these contributions produces a net interaction energy curve typically featuring a primary minimum (strong, often irreversible aggregation at very short range), an energy barrier (kinetic stabilization against aggregation), and sometimes a secondary minimum (weak, reversible flocculation at larger separation).
- A sufficiently high energy barrier (generally associated with $|\zeta|$ greater than roughly 30 mV as an empirical guideline [Unverified — threshold varies by system]) kinetically stabilizes a colloid against aggregation into the primary minimum, even though aggregation may be thermodynamically favorable.

### Colloidal Stabilization Mechanisms

**Electrostatic (Charge) Stabilization**

Surface charge and the resulting double-layer repulsion, as described by DLVO theory, prevent particles from approaching closely enough to aggregate via van der Waals attraction.

**Steric Stabilization**

Adsorbed or grafted polymer chains (or surfactant tails) on particle surfaces create a physical barrier: as two sterically stabilized particles approach, the polymer layers begin to overlap, producing both an osmotic (entropic) repulsion from increased local segment concentration and an elastic (entropic) repulsion from restricted chain conformations.

**Electrosteric Stabilization**

Combines electrostatic and steric mechanisms, common with charged polymer (polyelectrolyte) stabilizers, often providing more robust stability across a wider range of ionic strength and pH than either mechanism alone.

### Destabilization: Coagulation and Flocculation

**Key Points**

- **Coagulation:** addition of electrolyte compresses the diffuse double layer (reducing $\kappa^{-1}$), lowering the energy barrier and allowing particles to aggregate into the primary minimum, typically producing dense, often irreversible aggregates.
- **Schulze–Hardy rule:** the coagulating power of an ion increases dramatically with its charge (approximately as the sixth power of counterion valence for the critical coagulation concentration, in simple DLVO treatments), explaining why trivalent ions (e.g., Al³⁺) are far more effective coagulants than monovalent ions.
- **Flocculation:** aggregation into looser, often reversible clusters (flocs), which can occur in the secondary minimum or be induced by bridging flocculation, where a long-chain polymer adsorbs onto multiple particles simultaneously, linking them together.
- **Depletion flocculation:** non-adsorbing polymer or small particles in the continuous medium create an osmotic pressure imbalance that effectively draws larger colloidal particles together.

### Rheology and Colloidal Interactions

**Key Points**

- The bulk rheological behavior (viscosity, yield stress, viscoelasticity) of concentrated colloidal dispersions is strongly influenced by interparticle forces, particle shape, and volume fraction.
- Flocculated/gelled networks typically exhibit yield stress and shear-thinning behavior, while well-dispersed, stable colloids tend toward simpler viscous flow behavior at comparable concentration.

### Characterization Techniques

**Key Points**

- Dynamic light scattering (DLS): measures particle size (hydrodynamic diameter) and size distribution from fluctuations in scattered light intensity due to Brownian motion.
- Electrophoretic light scattering / zeta potential measurement: determines particle surface charge behavior via particle migration in an applied electric field.
- Static/multi-angle light scattering: provides information on particle size, shape, and molecular weight (for polymeric colloids).
- Transmission/scanning electron microscopy (TEM/SEM), atomic force microscopy (AFM): direct imaging of particle size, shape, and aggregation state.
- Ultracentrifugation and sedimentation analysis: assess particle size distribution and stability against gravitational settling.

### Surface Chemistry of Specific Colloidal Systems

**Emulsions**

Stabilized by surfactants or amphiphilic polymers adsorbed at the oil–water interface, reducing interfacial tension and providing steric/electrostatic barriers to droplet coalescence; the hydrophilic–lipophilic balance (HLB) of a surfactant predicts whether it favors oil-in-water or water-in-oil emulsions.

**Foams**

Stabilized by surfactants at the gas–liquid interface; film drainage, Ostwald ripening (gas diffusion from smaller to larger bubbles driven by Laplace pressure differences), and coalescence are the primary destabilization mechanisms.

**Pickering Emulsions/Foams**

Stabilized by solid particles adsorbed at the interface rather than molecular surfactants, with particle wettability (contact angle) determining which phase preferentially wets the particle and thus the emulsion type.

### Example

Coagulation of a negatively charged gold nanoparticle sol by addition of electrolyte:

1. As-synthesized citrate-capped Au nanoparticles carry a negative surface charge, producing electrostatic (double-layer) repulsion that maintains colloidal stability (characteristic red color from surface plasmon resonance in the dispersed, non-aggregated state).
2. Adding increasing concentrations of NaCl progressively screens the surface charge, compressing the diffuse double layer.
3. Beyond a critical coagulation concentration, the energy barrier in the DLVO interaction curve is sufficiently lowered that particles aggregate into the primary minimum.
4. Aggregation is visually apparent as a color shift (red to blue/purple) due to plasmon coupling between adjacent nanoparticles, and can be monitored quantitatively by UV-Vis extinction spectroscopy.

**Related Topics**

- DLVO theory and interparticle potential energy curves
- Zeta potential measurement and electrophoretic mobility
- Surfactant self-assembly and micelle formation
- Adsorption isotherms at solid–liquid and liquid–liquid interfaces
- Rheology of complex fluids and gelation
- Nanoparticle synthesis and surface functionalization
- Pickering emulsions and particle-stabilized interfaces