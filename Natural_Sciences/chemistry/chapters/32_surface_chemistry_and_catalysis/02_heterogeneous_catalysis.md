## Heterogeneous Catalysis


### Overview

Heterogeneous catalysis involves a catalyst existing in a different phase from the reactants, most commonly a solid catalyst acting on gas- or liquid-phase reactants. The catalytic cycle occurs at the solid surface, making adsorption, surface diffusion, surface reaction, and desorption the fundamental elementary steps. Heterogeneous catalysts underpin the majority of large-scale industrial chemical processes, including ammonia synthesis, petroleum refining, and automotive emissions control, primarily because they are easily separated from products and can be regenerated or reused.

### The Catalytic Cycle: Elementary Steps

**Key Points**

1. **Diffusion to the surface:** reactant molecules transport from the bulk fluid phase to the external catalyst surface (external mass transfer).
2. **Pore diffusion:** for porous catalysts, reactants diffuse into internal pore structure to reach active sites (internal mass transfer).
3. **Adsorption:** reactant(s) bind to active sites on the surface (physisorption and/or chemisorption).
4. **Surface reaction:** the rate-determining chemical transformation occurs between adsorbed species (or between an adsorbed species and a gas-phase molecule).
5. **Desorption:** product(s) release from the surface.
6. **Diffusion away from the surface:** products transport out of the pore structure and back into the bulk fluid.

Any of these six steps can be rate-limiting; identifying the rate-determining step is central to catalyst and reactor design.

```mermaid
flowchart LR
    A[Bulk reactant] --> B[External diffusion to surface]
    B --> C[Pore diffusion]
    C --> D[Adsorption on active site]
    D --> E[Surface reaction]
    E --> F[Desorption of product]
    F --> G[Pore diffusion out]
    G --> H[External diffusion to bulk]
```

### Active Sites and Surface Structure

**Key Points**

- An active site is a specific location on the catalyst surface (an atom, ensemble of atoms, or defect) where the catalytic transformation occurs.
- Catalytic activity often correlates strongly with surface structure: step edges, kinks, and terraces on a metal crystal can have very different reactivity than flat terraces (structure sensitivity).
- Coordinatively unsaturated surface atoms (fewer neighboring atoms than in the bulk) tend to bind adsorbates more strongly, often making them more catalytically active but also more prone to poisoning.
- Turnover frequency (TOF) quantifies intrinsic catalytic activity per active site per unit time, allowing comparison independent of total catalyst loading.

### Langmuir–Hinshelwood and Eley–Rideal Kinetics

**Langmuir–Hinshelwood mechanism** (both reactants adsorbed before reacting):

$$rate=k\,\theta_A\theta_B=k\frac{K_AP_A}{1+K_AP_A+K_BP_B}\cdot\frac{K_BP_B}{1+K_AP_A+K_BP_B}$$

**Eley–Rideal mechanism** (one reactant adsorbed, reacts directly with a gas-phase molecule):

$$rate=k\,\theta_A\,P_B$$

**Key Points**

- At low coverage of both reactants, Langmuir–Hinshelwood kinetics reduce to a simple second-order rate law; at high coverage of one species, the rate law can become inverse-order in that species (self-inhibition).
- Determining which mechanism operates typically requires kinetic studies across a range of partial pressures combined with surface-sensitive spectroscopic evidence.

### Sabatier Principle and Volcano Plots

The Sabatier principle states that an optimal catalyst binds reactants/intermediates neither too weakly (insufficient activation/adsorption) nor too strongly (poisoned surface, slow desorption of products). Plotting catalytic activity against a descriptor of binding strength (e.g., adsorption energy of a key intermediate) typically produces a volcano-shaped curve, with maximum activity at intermediate binding strength. This principle guides rational catalyst screening and design, particularly in computational catalysis using density functional theory (DFT)-derived binding energies as descriptors.

### Rate-Limiting Regimes and Mass Transfer

**Key Points**

- **Kinetic (reaction-limited) regime:** intrinsic surface reaction rate is slower than diffusion; observed activation energy reflects the true chemical barrier.
- **Diffusion-limited regime:** at high temperature or with fast intrinsic kinetics, external or internal mass transfer becomes rate-limiting; the observed activation energy drops to roughly half the intrinsic value, and observed reaction order can shift.
- The Thiele modulus, $\phi$, compares the rate of reaction to the rate of diffusion within a porous catalyst particle:



  $$\phi=L\sqrt{\frac{k}{D_{eff}}}$$

  where $L$ is a characteristic particle length, $k$ is the intrinsic rate constant, and $D_{eff}$ is the effective diffusivity within the pores.
- The effectiveness factor $\eta$ (ratio of actual observed rate to the rate if the entire internal surface were exposed to bulk-phase concentration) approaches 1 when $\phi\ll1$ (reaction-limited) and decreases as $\phi$ increases (diffusion-limited).

### Catalyst Composition and Design

**Key Points**

- **Supported metal catalysts:** small metal nanoparticles (Pt, Pd, Ni, Ru, etc.) dispersed on a high-surface-area support (alumina, silica, carbon) to maximize the fraction of exposed, catalytically active metal atoms (dispersion).
- **Zeolites:** microporous crystalline aluminosilicates with well-defined pore architectures that provide shape-selective catalysis (reactant, product, or transition-state selectivity based on pore/cavity dimensions); Brønsted acid sites arise from framework Al substitution.
- **Metal oxides:** used both as catalysts themselves (e.g., V₂O₅ for SO₂ oxidation) and as supports; can provide acid–base or redox functionality.
- **Bimetallic and alloy catalysts:** combining two metals can tune electronic (ligand) and geometric (ensemble) effects to modify binding energies of intermediates relative to either pure metal.
- **Single-atom catalysts:** isolated metal atoms anchored on a support, maximizing atom-economy and often exhibiting distinct selectivity compared to nanoparticle catalysts [Inference — an active and rapidly developing research area; generalizations about stability and scope should be treated cautiously].

### Catalyst Deactivation

| Mechanism | Description |
| --- | --- |
| Poisoning | Strong, often irreversible adsorption of impurities (S, CO, Pb, etc.) that block active sites |
| Fouling/coking | Physical deposition of carbonaceous material (coke) blocking sites and pores |
| Sintering | Thermally driven agglomeration of metal nanoparticles, reducing active surface area/dispersion |
| Thermal degradation | Loss of support surface area or phase transformation at high temperature |
| Leaching | Loss of active component into a liquid-phase reaction medium (relevant especially in liquid-phase catalysis) |
| Vapor-phase compound formation | Reaction of the active phase with a component of the feed or reactor to form a volatile, inactive compound |

Regeneration strategies (oxidative coke burn-off, reduction treatments, re-dispersion) can restore some catalysts, though sintering is generally difficult to reverse.

### Industrial Examples

**Key Points**

- **Haber–Bosch process:** N₂ + 3H₂ ⇌ 2NH₃ over an iron-based catalyst (promoted with K₂O, Al₂O₃), requiring dissociative chemisorption of N₂ as the rate-determining step.
- **Contact process:** 2SO₂ + O₂ ⇌ 2SO₃ over a V₂O₅ catalyst, a key step in sulfuric acid manufacture.
- **Catalytic converters:** Pt/Pd/Rh catalysts on a ceramic monolith support simultaneously oxidize CO and unburned hydrocarbons while reducing NOₓ in automotive exhaust (three-way catalysis).
- **Fluid catalytic cracking (FCC):** zeolite-based catalysts crack heavy petroleum fractions into lighter, more valuable hydrocarbons.
- **Fischer–Tropsch synthesis:** CO + H₂ converted to hydrocarbons over Fe- or Co-based catalysts, relevant to gas-to-liquids and syngas conversion technologies.

### Characterization Techniques

**Key Points**

- Chemisorption/physisorption measurements (BET surface area, H₂ or CO chemisorption for metal dispersion)
- Temperature-programmed reduction/desorption/oxidation (TPR/TPD/TPO) for characterizing reducibility and site strength distributions
- X-ray diffraction (XRD) for bulk crystal structure and phase identification
- X-ray photoelectron spectroscopy (XPS) for surface elemental composition and oxidation states
- Transmission electron microscopy (TEM) for nanoparticle size, morphology, and dispersion
- In-situ/operando spectroscopy (DRIFTS, in-situ XRD, XAS) for observing the catalyst under real reaction conditions, increasingly important for connecting structure to function under working conditions rather than relying solely on ex-situ characterization

### Example

Ammonia synthesis over an iron catalyst (simplified elementary steps):

$$N_2(g) \rightleftharpoons N_2(ads)$$



$$N_2(ads) \rightarrow 2N(ads)\quad\text{(rate-determining step)}$$



$$H_2(g) \rightleftharpoons H_2(ads) \rightarrow 2H(ads)$$



$$N(ads)+H(ads)\rightarrow NH(ads)$$



$$NH(ads)+H(ads)\rightarrow NH_2(ads)$$



$$NH_2(ads)+H(ads)\rightarrow NH_3(ads)$$



$$NH_3(ads)\rightarrow NH_3(g)$$

The dissociative chemisorption of N₂ has a high activation barrier and is generally accepted as rate-limiting, which is why promoters and specific iron surface facets that facilitate N₂ dissociation are central to catalyst optimization.

**Related Topics**

- Adsorption isotherms and surface coverage models (Langmuir, BET)
- Zeolite structure and shape-selective catalysis
- Computational catalysis and DFT-based descriptor screening
- Catalyst deactivation and regeneration strategies
- Homogeneous vs. heterogeneous catalysis comparison
- Mass transfer effects in porous catalyst particles
- Operando spectroscopic methods for catalyst characterization