## Viscoelastic Behavior


### Definition and Physical Basis

Viscoelastic behavior describes materials that exhibit a combination of elastic (solid-like, energy-storing) and viscous (liquid-like, energy-dissipating) response when deformed. Unlike a purely elastic (Hookean) solid, whose stress depends only on instantaneous strain, or a purely viscous (Newtonian) fluid, whose stress depends only on strain rate, a viscoelastic material's stress response depends on the entire history of deformation and is inherently time-, rate-, and temperature-dependent.

Physically, viscoelasticity arises predominantly in polymers (and, to a lesser but relevant degree, in some metals at elevated temperature) from molecular-scale relaxation processes: polymer chain segments require finite time to reorient, slide past one another, or disentangle in response to an applied stress, so the material's response lags behind the applied load.

### Key Manifestations of Viscoelastic Behavior

**[Key Points]**

- **Creep**: time-dependent increase in strain under a constant applied stress.
- **Stress relaxation**: time-dependent decrease in stress under a constant applied strain.
- **Hysteresis**: energy dissipation during cyclic loading, visible as a loop (rather than a single line) when stress is plotted against strain over a load-unload cycle.
- **Rate/frequency dependence**: the apparent stiffness and damping of the material change with the rate or frequency of applied loading.
- **Time-temperature dependence**: viscoelastic response is strongly temperature-sensitive, since molecular mobility (and hence relaxation time scales) is thermally activated.

### Creep Behavior

Under a constant applied stress $\sigma_0$, strain in a viscoelastic material increases over time according to a time-dependent compliance function $J(t)$:

$$\varepsilon(t) = \sigma_0 \, J(t)$$

Creep curves typically show three characteristic stages, particularly evident in polymers and metals at high homologous temperature ($T/T_m$):

1. **Primary (transient) creep**: decreasing strain rate as initial rapid deformation mechanisms exhaust themselves.
2. **Secondary (steady-state) creep**: approximately constant minimum creep rate, often the longest-duration and most design-relevant stage.
3. **Tertiary creep**: accelerating strain rate leading to eventual rupture, associated with internal damage accumulation (void formation, necking, or microcracking).

### Stress Relaxation

Under a constant applied strain $\varepsilon_0$, stress in a viscoelastic material decreases over time according to a time-dependent relaxation modulus $E(t)$:

$$\sigma(t) = \varepsilon_0 \, E(t)$$

This behavior is of direct engineering significance in applications such as bolted joints, gaskets, and seals, where a sustained clamping strain is required — stress relaxation over time reduces the effective clamping force even though the assembled geometry (strain) has not changed, necessitating periodic retightening or relaxation-resistant material selection in critical applications.

### Rheological (Mechanical Analog) Models

**[Key Points]**

Simple spring-dashpot combinations are used as conceptual and mathematical models to capture basic viscoelastic response, though real materials generally require more elaborate multi-element models for quantitative accuracy.

**Maxwell model** (spring and dashpot in series):

$$\frac{d\varepsilon}{dt} = \frac{1}{E}\frac{d\sigma}{dt} + \frac{\sigma}{\eta}$$

Under constant strain, this model predicts exponential stress relaxation:

$$\sigma(t) = \sigma_0 \, e^{-t/\tau}$$

where $\tau = \eta/E$ is the relaxation time ($\eta$ = dashpot viscosity, $E$ = spring modulus). The Maxwell model captures stress relaxation reasonably well but does not capture bounded (finite, recoverable) creep — it instead predicts unbounded, linearly increasing strain under constant stress, an unrealistic result for many real solid polymers at typical laboratory time scales.

**Kelvin-Voigt model** (spring and dashpot in parallel):

$$\sigma = E\varepsilon + \eta\frac{d\varepsilon}{dt}$$

Under constant stress, this model predicts bounded, exponentially approaching (retarded) creep:

$$\varepsilon(t) = \frac{\sigma_0}{E}\left(1 - e^{-t/\tau}\right)$$

The Kelvin-Voigt model captures bounded creep well but does not capture instantaneous elastic response or stress relaxation, since the dashpot in parallel prevents any instantaneous strain jump.

**Standard Linear Solid (SLS) / Zener model**

Combines elements of both Maxwell and Kelvin-Voigt arrangements (e.g., a Maxwell element in parallel with an additional spring) to capture both an instantaneous elastic response and bounded, finite creep and relaxation behavior — a more physically realistic minimal model, though still a simplification of the continuous spectrum of relaxation times present in real polymeric materials.

### Rheological Model Comparison Diagram

===MERMAID_DIAGRAM===

flowchart TD

A["Viscoelastic mechanical models"] --> B["Maxwell model<br/>(spring + dashpot, series)"]

A --> C["Kelvin-Voigt model<br/>(spring + dashpot, parallel)"]

A --> D["Standard Linear Solid<br/>(combined elements)"]

B --> E["Good: stress relaxation<br/>Poor: unbounded creep"]

C --> F["Good: bounded creep<br/>Poor: no instant elasticity,<br/>no stress relaxation"]

D --> G["Captures both instantaneous<br/>elasticity and bounded<br/>creep/relaxation"]



```
### Dynamic Mechanical Analysis: Storage and Loss Modulus

Under oscillatory (sinusoidal) loading at angular frequency $\omega$, a viscoelastic material's strain response lags the applied stress by a phase angle $\delta$ (for stress-controlled testing; equivalently stress lags strain in strain-controlled testing). The complex modulus is decomposed as:

$$E^* = E' + iE''$$

where:
- $E'$ (**storage modulus**) represents the in-phase, elastic (energy-storing) component of the response.
- $E''$ (**loss modulus**) represents the out-of-phase, viscous (energy-dissipating) component.
- $\tan\delta = E''/E'$ (**loss tangent** or damping factor) quantifies the relative degree of energy dissipation versus energy storage, widely used as a practical damping/vibration-isolation performance metric.

**[Key Points]**
- Below the glass transition temperature ($T_g$), polymers behave in a glassy state with high $E'$ and low $\tan\delta$ (stiff, low damping).
- Near $T_g$, $\tan\delta$ typically shows a pronounced peak as molecular segmental motion becomes thermally activated at the test frequency, corresponding to maximum energy dissipation — this peak is a standard experimental method (Dynamic Mechanical Analysis, DMA) for precisely determining $T_g$.
- Above $T_g$ (rubbery plateau region), $E'$ drops substantially (often by orders of magnitude) and the material becomes markedly more compliant and rate-dependent.

### Time-Temperature Superposition

**[Key Points]**

Because viscoelastic relaxation processes are thermally activated, increasing temperature has an effect on measured mechanical response qualitatively similar to decreasing the loading rate (or increasing the observation time) — both allow more time (in an effective sense) for molecular relaxation processes to occur. This equivalence underlies the **time-temperature superposition (TTS) principle**, which allows short-time, high-temperature data to be shifted along the time/frequency axis to construct a long-time (or low-frequency) "master curve" at a chosen reference temperature, using a horizontal shift factor $a_T$.

For many amorphous polymers above $T_g$, the shift factor follows the empirical **Williams-Landel-Ferry (WLF) equation**:

$$\log a_T = \frac{-C_1(T-T_{ref})}{C_2 + (T-T_{ref})}$$

where $C_1$ and $C_2$ are material-specific empirical constants (often cited as approximately universal values $C_1 \approx 17.4$, $C_2 \approx 51.6$ K when $T_{ref} = T_g$, though these "universal" values are approximations and material-specific fitted constants generally provide better accuracy). [Inference: applicability of TTS and the accuracy of universal WLF constants can vary meaningfully between different polymer chemistries and is most reliably established through direct experimental verification for a given material.]

### Worked Example: Maxwell Model Stress Relaxation

**[Example]** A polymer is modeled as a Maxwell element with spring modulus $E = 2.0$ GPa and dashpot viscosity $\eta = 5\times10^{10}$ Pa·s. It is subjected to a constant strain of $\varepsilon_0 = 0.01$. Calculate the initial stress and the stress after 30 seconds.

**Relaxation time:**
$$\tau = \frac{\eta}{E} = \frac{5\times10^{10}}{2.0\times10^9} = 25\ \text{s}$$

**Initial stress** (instantaneous elastic response, $t=0$):
$$\sigma_0 = E\varepsilon_0 = (2.0\times10^9)(0.01) = 2.0\times10^7\ \text{Pa} = 20\ \text{MPa}$$

**Stress at t = 30 s:**
$$\sigma(t) = \sigma_0\,e^{-t/\tau} = 20\times e^{-30/25} = 20\times e^{-1.2} = 20\times0.3012 \approx 6.02\ \text{MPa}$$

The stress has relaxed to approximately 30% of its initial value after 30 seconds, illustrating the characteristic exponential decay predicted by the Maxwell model, with the relaxation time $\tau$ setting the characteristic time scale of this decay.

### Worked Example: Kelvin-Voigt Model Creep Response

**[Example]** A viscoelastic material modeled as a Kelvin-Voigt element has $E = 500$ MPa and $\eta = 2\times10^{10}$ Pa·s. A constant stress of $\sigma_0 = 10$ MPa is applied. Determine the strain at $t = 40$ s.

**Relaxation (retardation) time:**
$$\tau = \frac{\eta}{E} = \frac{2\times10^{10}}{5\times10^8} = 40\ \text{s}$$

**Strain at t = 40 s:**
$$\varepsilon(t) = \frac{\sigma_0}{E}\left(1-e^{-t/\tau}\right) = \frac{10}{500}\left(1-e^{-40/40}\right) = 0.02\times(1-e^{-1})$$

$$= 0.02\times(1-0.3679) = 0.02\times0.6321 \approx 0.01264$$

At $t = 40$ s (one retardation time constant), the material has reached approximately 63.2% of its eventual equilibrium creep strain ($\sigma_0/E = 0.02$), consistent with the characteristic exponential-approach behavior of the Kelvin-Voigt model.

### Relevance to Metals: Elevated-Temperature Viscoelastic-Like Behavior

**[Key Points]**
- Most structural metals at room temperature behave in a predominantly elastic (non-viscoelastic) manner under typical loading rates, since thermally activated relaxation processes are slow at low homologous temperature ($T/T_m$).
- At elevated temperature (typically $T/T_m > 0.4$–$0.5$), metals exhibit pronounced time-dependent deformation (creep) governed by diffusion-mediated mechanisms (dislocation climb, grain boundary sliding, Nabarro-Herring/Coble diffusional creep) — behaviorally analogous in some respects to polymer viscoelasticity (time-dependent, thermally activated) but mechanistically distinct (governed by atomic diffusion and dislocation mechanisms rather than polymer chain segmental motion).
- **Anelasticity** in metals — a small, fully recoverable but time-dependent elastic strain component distinct from viscoelastic flow — arises from mechanisms such as stress-induced short-range atomic ordering (Snoek and Zener relaxation effects) and grain boundary relaxation, and is generally a much smaller-magnitude effect than polymer viscoelasticity but is measurable via internal friction (damping) testing.

### Applications and Engineering Significance

- **Polymer component design**: creep and stress relaxation data are essential design inputs for polymer components under sustained load (pipe systems, structural polymer components, gaskets, seals) since short-term tensile test data alone significantly overestimates long-term load-bearing capability.
- **Vibration damping and isolation**: materials with high loss tangent ($\tan\delta$) near the operating frequency and temperature are deliberately selected or engineered (viscoelastic damping polymers, elastomeric mounts) for vibration and noise control applications.
- **Adhesives and sealants**: viscoelastic response governs peel strength, creep resistance under sustained load, and temperature-dependent performance windows of structural and pressure-sensitive adhesives.
- **Biomedical and tissue-mimicking materials**: viscoelastic characterization is used extensively in soft-material and biomaterial contexts (though this extends beyond metallurgy) where time-dependent mechanical response is functionally critical.
- **Constitutive modeling for FEA**: accurate finite element simulation of polymer or polymer-matrix composite components under realistic service conditions requires viscoelastic material models (e.g., Prony series representations of the relaxation modulus) rather than simple linear-elastic assumptions, particularly for long-duration or elevated-temperature service.

### Related Topics
- Creep deformation mechanisms in metals (dislocation climb, diffusional creep)
- Glass transition temperature and polymer thermal transitions
- Dynamic mechanical analysis (DMA) and complex modulus measurement
- Anelasticity and internal friction in metals (Snoek and Zener relaxation)
- Time-temperature superposition and the WLF equation
- Stress relaxation in bolted joints and gasket design
- Polymer-matrix composite mechanical characterization


```