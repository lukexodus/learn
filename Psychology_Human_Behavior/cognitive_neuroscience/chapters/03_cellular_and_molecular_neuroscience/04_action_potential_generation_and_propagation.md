## Action Potential Generation and Propagation


### Overview

The action potential (AP) is a rapid, stereotyped, all-or-none reversal of membrane potential that serves as the primary long-distance electrical signal in neurons. It arises from the sequential, voltage-dependent opening and closing of voltage-gated ion channels, converts graded local depolarization into a regenerative and self-propagating signal, and allows information to travel over distances (up to a meter or more in some axons) without attenuation. Understanding AP mechanics is foundational to nearly all subsequent topics in cellular and systems neuroscience.

### Phases of the Action Potential

**Key Points**

- **Resting state**: membrane potential near $-65\ \text{mV}$; voltage-gated Na+ channels closed but available (closed-but-activatable), voltage-gated K+ channels closed.
- **Threshold**: the depolarization level (~$-55\ \text{mV}$ in many neurons) at which enough voltage-gated Na+ channels open that inward Na+ current exceeds outward leak current, triggering regenerative, positive-feedback depolarization.
- **Depolarization (rising phase)**: rapid opening of voltage-gated Na+ channels causes a large influx of Na+, driving membrane potential rapidly toward $E_{Na}$ (~+60 mV, though peak typically falls short of this due to imperfect selectivity and overlapping K+ activation).
- **Repolarization (falling phase)**: voltage-gated Na+ channels inactivate (a time-dependent conformational change distinct from closing), and delayed-rectifier voltage-gated K+ channels open, driving K+ efflux that returns membrane potential toward $E_K$.
- **Hyperpolarization (undershoot)**: K+ channels remain open briefly after repolarization, driving membrane potential transiently below resting level before K+ channels close and leak conductances restore baseline.
- **Refractory periods**:
  - **Absolute refractory period**: no new action potential can be triggered regardless of stimulus strength, because a sufficient fraction of Na+ channels remain inactivated.
  - **Relative refractory period**: a stronger-than-normal stimulus can trigger a new action potential, because some Na+ channels have recovered from inactivation while K+ conductance remains elevated (raising threshold).

```mermaid
flowchart LR
    A[Resting State] --> B[Threshold Reached]
    B --> C[Depolarization: Na+ channels open]
    C --> D[Peak: Na+ channels inactivate]
    D --> E[Repolarization: K+ channels open]
    E --> F[Hyperpolarization: Undershoot]
    F --> G[Return to Resting State]
    G --> A
```

### Voltage-Gated Channel Gating Kinetics

**Key Points**

- **Voltage-gated Na+ channels** have two gates: an **activation gate** (fast, opens on depolarization) and an **inactivation gate** (slower, closes shortly after activation independent of continued depolarization). The channel conducts only when activation gate is open AND inactivation gate has not yet closed.
- **Voltage-gated K+ channels** (delayed rectifier type) have slower activation kinetics than Na+ channels and do not inactivate on the same timescale, which is why K+ efflux lags Na+ influx and produces the characteristic repolarization delay.
- This kinetic offset — fast Na+ activation, faster Na+ inactivation, slower K+ activation — is the core biophysical basis of the AP waveform, originally characterized quantitatively by Hodgkin and Huxley using voltage-clamp experiments in the squid giant axon.

### The Hodgkin-Huxley Model

**Key Points**

- A quantitative, conductance-based model describing membrane current as a function of voltage-dependent and time-dependent gating variables for Na+ and K+ conductances.
- General form of the membrane current equation:

$$I_m = C_m \frac{dV_m}{dt} + \bar{g}_{Na} m^3 h (V_m - E_{Na}) + \bar{g}_K n^4 (V_m - E_K) + g_L (V_m - E_L)$$

where $C_m$ is membrane capacitance, $\bar{g}_{Na}$ and $\bar{g}_K$ are maximal conductances, $m$ and $h$ are Na+ activation and inactivation gating variables, $n$ is the K+ activation gating variable, and $g_L$/$E_L$ represent the leak conductance and its reversal potential.

- This model remains the standard framework taught for AP biophysics and underlies most modern computational neuron models, though many contemporary models add additional conductances (e.g., Ca2+ currents, various K+ subtypes) for greater biological fidelity. [Unverified: the specific additional conductances included vary by model and research application.]

### All-or-None Principle and Frequency Coding

**Key Points**

- Once threshold is crossed, the AP waveform is stereotyped in amplitude and shape regardless of stimulus strength above threshold — the **all-or-none principle**.
- Information about stimulus intensity is therefore encoded not in AP amplitude but in **firing rate (frequency coding)** and **spike timing/pattern**, since stronger stimuli produce more frequent action potentials (up to limits imposed by the refractory period).

### Propagation Along the Axon

**Key Points**

- **Local circuit currents**: depolarization at one point on the membrane spreads passively (electrotonically) to adjacent membrane regions, bringing them to threshold and triggering a new, full-amplitude AP there — this regenerative process is what allows the AP to propagate without decrement (loss of amplitude), unlike passive electrotonic spread alone.
- **Unidirectional propagation**: under normal physiological conditions, the AP travels away from the axon hillock toward the terminals, because the refractory region just traversed cannot be immediately re-excited, preventing backward propagation.
- **Continuous conduction**: occurs in unmyelinated axons, where the AP regenerates at every adjacent patch of membrane; relatively slow (typically well under 10 m/s, depending on axon diameter).
- **Saltatory conduction**: occurs in myelinated axons, where myelin's insulating properties prevent current leak along internodes, and the AP effectively "jumps" from one **node of Ranvier** to the next, where voltage-gated Na+ channels are densely clustered. This dramatically increases conduction velocity (up to ~100+ m/s in large myelinated fibers) while reducing metabolic cost, since active regeneration occurs only at nodes rather than continuously.
- **Conduction velocity determinants**: increases with axon diameter (reduced internal resistance) and with myelination; these two strategies represent alternative evolutionary solutions to increasing speed, with myelination being far more space- and energy-efficient than diameter increases alone. [Inference: comparative efficiency claims are well-supported in general biophysical terms, but exact quantitative trade-offs vary by species and fiber type.]

### Diagram: Saltatory vs. Continuous Conduction

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 660 300" font-family="Arial, sans-serif">
<text x="330" y="25" text-anchor="middle" font-size="16" font-weight="bold" fill="#222">Continuous vs. Saltatory Conduction (svg_diagram)</text>


<text x="330" y="60" text-anchor="middle" font-size="12" fill="#333" font-weight="bold">Unmyelinated Axon (Continuous Conduction)</text>

<line x1="60" y1="90" x2="600" y2="90" stroke="#333" stroke-width="3" />

<g fill="`#c0392b`">

<circle cx="100" cy="90" r="6" />

<circle cx="200" cy="90" r="6" opacity="0.6" />

<circle cx="300" cy="90" r="6" opacity="0.3" />

</g>

<text x="330" y="115" text-anchor="middle" font-size="10" fill="#555">AP regenerates at every adjacent membrane patch — slower</text>



<text x="330" y="160" text-anchor="middle" font-size="12" fill="#333" font-weight="bold">Myelinated Axon (Saltatory Conduction)</text>

<line x1="60" y1="190" x2="600" y2="190" stroke="#333" stroke-width="3" />

<g fill="`#f9e79f`" stroke="`#b7950b`" stroke-width="1.5">

<rect x="80" y="180" width="70" height="20" rx="8" />

<rect x="180" y="180" width="70" height="20" rx="8" />

<rect x="280" y="180" width="70" height="20" rx="8" />

<rect x="380" y="180" width="70" height="20" rx="8" />

<rect x="480" y="180" width="70" height="20" rx="8" />

</g>

<g fill="`#c0392b`">

<circle cx="160" cy="190" r="6" />

<circle cx="260" cy="190" r="6" opacity="0.7" />

<circle cx="360" cy="190" r="6" opacity="0.4" />

</g>

<text x="160" y="215" text-anchor="middle" font-size="8" fill="#333">Node</text>

<text x="260" y="215" text-anchor="middle" font-size="8" fill="#333">Node</text>

<text x="360" y="215" text-anchor="middle" font-size="8" fill="#333">Node</text>

<text x="330" y="245" text-anchor="middle" font-size="10" fill="#555">AP "jumps" node to node — much faster, more energy-efficient</text>

</svg>

### Role of Axon Diameter and the Cable Properties

**Key Points**

- Axons behave as leaky electrical cables; the **length constant** ($\lambda$) describes how far a passive depolarization spreads before decaying substantially, and the **time constant** ($\tau$) describes how quickly membrane potential changes in response to current:

$$\lambda = \sqrt{\frac{r_m}{r_i}}, \qquad \tau = r_m c_m$$

where $r_m$ is membrane resistance, $r_i$ is internal (axial) resistance, and $c_m$ is membrane capacitance.

- Larger diameter reduces $r_i$, increasing $\lambda$ and allowing faster passive spread between nodes — this is why larger-diameter axons (myelinated or not) conduct faster, all else being equal.
- Myelin increases effective $r_m$ and decreases effective $c_m$ along internodes, further increasing $\lambda$ and reducing the time needed to charge the membrane to threshold at the next node.

### Clinical and Research Relevance

**Key Points**

- **Local anesthetics** (e.g., lidocaine) block voltage-gated Na+ channels, preventing AP initiation and propagation in sensory (and eventually motor) fibers — the primary mechanism of local nerve block anesthesia.
- **Demyelinating diseases** (e.g., multiple sclerosis, Guillain-Barré syndrome) disrupt saltatory conduction, causing conduction slowing or block and the corresponding sensory/motor deficits.
- **Channelopathies**: mutations in voltage-gated Na+ or K+ channel genes underlie various inherited episodic disorders, including certain epilepsy syndromes and periodic paralyses.
- **Nerve conduction studies (NCS)**: a standard clinical electrophysiological tool that measures conduction velocity, directly reflecting the biophysical principles of myelination and axon diameter discussed above; reduced velocity is a hallmark finding in demyelinating neuropathies. [Behavior in specific clinical presentations may vary by underlying etiology and should be interpreted alongside full clinical context.]

### Related Topics

- Resting membrane potential and ion channel biophysics
- Hodgkin-Huxley voltage-clamp methodology
- Synaptic transmission and postsynaptic potential summation
- Myelination biology (oligodendrocytes and Schwann cells)
- Channelopathies and clinical electrophysiology
- Cable theory and passive membrane properties
- Computational and compartmental neuron modeling