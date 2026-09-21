## Silicon Carbide and Gallium Nitride Power Device Design


### Overview

Wide-bandgap (WBG) semiconductors — primarily silicon carbide (SiC) and gallium nitride (GaN) — have emerged as the dominant successors to silicon in high-performance power conversion. Their superior material properties (larger bandgap, higher critical electric field, higher electron saturation velocity, and in GaN's case, a naturally forming two-dimensional electron gas) enable power devices with fundamentally lower conduction and switching losses, higher operating temperatures, and higher switching frequencies than silicon-based IGBTs or MOSFETs. SiC is primarily deployed as vertical power MOSFETs and diodes; GaN is primarily deployed as lateral High Electron Mobility Transistors (HEMTs).

### Material Properties Driving Device Performance

| Property | Si | 4H-SiC | GaN |
| --- | --- | --- | --- |
| Bandgap $E_g$ (eV) | 1.12 | 3.26 | 3.39 |
| Critical electric field $E_{crit}$ (MV/cm) | ~0.3 | ~2.8 | ~3.3 |
| Electron mobility (cm²/V·s) | ~1400 | ~900 (bulk) | ~2000 (2DEG) |
| Saturation velocity (cm/s) | ~1×10⁷ | ~2×10⁷ | ~2.5×10⁷ |
| Thermal conductivity (W/cm·K) | 1.5 | 3.7–4.9 | 1.3 (GaN itself; substrate-dependent) |

[Unverified: precise figures vary by source, crystal polytype, doping, and measurement conditions — the values above represent commonly cited reference ranges]

**Baliga Figure of Merit (BFOM)**

The theoretical minimum specific on-resistance for a unipolar drift region scales as:

$$R_{on,sp} = \frac{4 V_{BR}^2}{\varepsilon_s \mu_n E_{crit}^3}$$

where $V_{BR}$ is the breakdown voltage, $\varepsilon_s$ is the semiconductor permittivity, $\mu_n$ is electron mobility, and $E_{crit}$ is the critical electric field. Because $E_{crit}$ enters as a cubic term, SiC's ~9x higher critical field over silicon translates into a theoretical specific on-resistance reduction of roughly two orders of magnitude for a given blocking voltage — this is the central physical argument for WBG adoption in power electronics.

### Silicon Carbide (SiC) Device Design

**Polytype Selection**

Commercial SiC power devices almost universally use the **4H-SiC** polytype due to its higher and more isotropic electron mobility compared to 3C or 6H polytypes, along with mature substrate manufacturing.

**SiC Power MOSFET Structure**



```
       Source                Gate
|                    |
     [n+]   [n+]          [Gate Oxide - SiO2]
    -------------------------------------
|  p-well (channel region)          |
    -------------------------------------
|          n- drift region          |  <-- thin due to high E_crit
    -------------------------------------
|          n+ substrate             |
    -------------------------------------
                Drain
```

The vertical DMOS (Double-diffused MOS) or trench structure closely resembles a silicon power MOSFET, but the drift region can be roughly **10x thinner** for the same blocking voltage due to SiC's higher critical field, directly reducing drift resistance.

**Key SiC-Specific Design Challenges**

1. **SiC/SiO₂ Interface Quality**: The thermally grown oxide on SiC has a substantially higher interface trap density ($D_{it}$) than the Si/SiO₂ interface, causing reduced channel mobility (often only 5–30 cm²/V·s at the channel versus theoretical bulk values) and threshold voltage instability. Nitridation processes (NO or N₂O post-oxidation anneal) are standard mitigation techniques to passivate interface states.
2. **Trench vs Planar Gate**: Trench-gate SiC MOSFETs eliminate the JFET resistance region present in planar designs (formed between adjacent p-wells), improving channel density and reducing on-resistance, but require careful electric field management at the trench corners to avoid localized oxide breakdown, since SiC's high critical field concentrates stress at these geometric features.
3. **Body Diode Bipolar Degradation**: The intrinsic body diode of a SiC MOSFET, when conducting in bipolar mode, can inject minority carriers that recombine at basal plane dislocations (BPDs) in the substrate, causing stacking fault expansion and long-term $R_{on}$ drift. This is mitigated via epitaxial growth optimization to minimize BPD density and/or adding an external SiC Schottky diode to bypass body diode conduction.

**SiC Schottky Barrier Diodes (SBDs)**

SiC's wide bandgap permits Schottky (majority-carrier) diodes at voltage ratings (600V–3.3kV+) where silicon would require slower bipolar PiN diodes. SiC SBDs exhibit negligible reverse recovery charge ($Q_{rr} \approx 0$), eliminating a major source of switching loss and EMI in power factor correction and motor drive applications — this is historically the first and most commercially mature SiC power product category.

### Gallium Nitride (GaN) Device Design

**HEMT Structure and the 2DEG**

GaN power devices exploit a heterojunction between GaN and AlGaN grown epitaxially (typically on silicon substrates for cost reasons, or SiC/sapphire for premium RF applications). The spontaneous and piezoelectric polarization discontinuity at the AlGaN/GaN interface induces a high-density, high-mobility two-dimensional electron gas (2DEG) confined at the heterointerface — without requiring intentional doping.



```
   Source        Gate        Drain
|            |            |
  [ohmic]    [Schottky/MIS]  [ohmic]
  ------------------------------------
|         AlGaN barrier layer      |
  ------------------------------------  <-- 2DEG forms here (polarization-induced)
|           GaN buffer layer       |
  ------------------------------------
|    Nucleation/transition layers  |
  ------------------------------------
|         Si (or SiC) substrate    |
  ------------------------------------
```

**2DEG Formation**

The sheet carrier density of the 2DEG arises from polarization discontinuity:

$$n_s = \frac{\sigma_{pol}}{q} - \frac{\varepsilon(\phi_b + E_F - \Delta E_c)}{q d}$$

where $\sigma_{pol}$ is the net polarization charge, $\phi_b$ is the Schottky barrier height, $d$ is the AlGaN barrier thickness, and $\Delta E_c$ is the conduction band offset. Because the 2DEG exists without deliberate doping, electron mobility is exceptionally high (~1500–2000 cm²/V·s) and largely free of ionized impurity scattering.

**Normally-On vs Normally-Off Operation**

A standard AlGaN/GaN HEMT is inherently **depletion-mode (normally-on)** — the 2DEG conducts at zero gate bias, which is unacceptable for most power switching applications requiring fail-safe (normally-off) behavior. Three principal approaches achieve enhancement-mode (normally-off, E-mode) operation:

1. **p-GaN Gate**: A p-type GaN layer beneath the gate metal locally depletes the 2DEG at zero bias by raising the conduction band above the Fermi level under the gate region. Applying positive gate voltage forward-biases the p-GaN/2DEG junction, re-populating the 2DEG channel. This is the dominant commercial approach (e.g., GaN Systems, Infineon CoolGaN, Panasonic).
2. **Recessed Gate**: The AlGaN barrier is thinned (etched) directly beneath the gate, reducing the polarization charge locally enough to deplete the 2DEG at zero bias.
3. **Cascode Configuration**: A normally-on GaN HEMT is placed in series with a low-voltage normally-off silicon MOSFET; the combination behaves as a normally-off device at the package level, since the Si MOSFET's gate controls the effective on/off state (used by e.g., Transphorm, historically Infineon's early GaN products).

**Dynamic On-Resistance (Current Collapse)**

A defining reliability and design challenge unique to GaN HEMTs is **dynamic $R_{on}$** (also called current collapse): electrons trapped in surface states or buffer layer traps during high-voltage off-state stress are released slowly during subsequent turn-on, temporarily reducing 2DEG density and increasing on-resistance above its DC-measured value.

$$R_{on,dynamic}(t) = R_{on,DC} \left(1 + \Delta \cdot e^{-t/\tau_{detrap}}\right)$$

Mitigation involves surface passivation (SiN caps), field plates to redistribute peak electric fields away from trap-dense regions, and carbon-doped buffer layer optimization to control trap density and time constants.

**Field Plates**

Both gate-connected and source-connected field plates are standard structural elements that spread the peak lateral electric field across the drift region between gate and drain, raising breakdown voltage and suppressing trap-related current collapse by lowering the peak field at the gate edge.

### Comparative Design Trade-offs: SiC vs GaN

| Aspect | SiC (Vertical MOSFET) | GaN (Lateral HEMT) |
| --- | --- | --- |
| Device topology | Vertical, unipolar drift region | Lateral, 2DEG channel |
| Typical voltage range | 650V–3.3kV+ (extending to 10kV+ in development) | 15V–650V (900V+ emerging) |
| Body diode | Intrinsic (bipolar, degradation risk) | None (or diode-less reverse conduction via 2DEG) |
| Switching speed | Fast | Extremely fast (lowest $Q_G$, no minority carrier storage) |
| Threshold voltage stability | Bias-temperature instability from oxide traps | Gate stability challenges from p-GaN or recessed-gate structure |
| Dominant reliability concern | Gate oxide reliability, body diode degradation | Dynamic $R_{on}$ / current collapse |
| Typical application space | EV traction inverters, solar inverters, industrial motor drives | Fast chargers, data center PSUs, RF power, high-frequency DC-DC |

### Simplified GaN E-HEMT Turn-On Band Diagram Concept

```mermaid
graph LR
    A[Gate Voltage below Vth] --> B[p-GaN raises conduction band under gate]
    B --> C[2DEG locally depleted beneath gate - OFF state]
    D[Gate Voltage above Vth] --> E[p-GaN/2DEG junction forward biased]
    E --> F[2DEG channel restored beneath gate - ON state]
    C -.->|apply Vgs greater than Vth| D
```

### Packaging and System-Level Design Considerations

- **Parasitic Inductance Sensitivity**: The extremely fast switching edges (dV/dt, dI/dt) of both SiC and GaN devices make package and PCB parasitic inductance a first-order design concern — even nH-scale loop inductance can generate significant voltage overshoot and ringing, driving adoption of low-inductance packages (e.g., GaN's chip-scale/LGA packages, SiC's kelvin-source TO-247-4 pin packages).
- **Gate Drive Requirements**: SiC MOSFETs typically require a negative gate turn-off bias (e.g., -5V) to ensure robust off-state noise immunity given their lower threshold voltage margins; GaN p-GaN devices have a narrow positive gate voltage window (often limited to ~6V max) due to the forward-biased p-GaN/2DEG gate diode conduction at higher $V_{GS}$.
- **Thermal Design**: SiC's higher thermal conductivity substrate supports higher power density in vertical device packaging; GaN-on-Si devices face thermal resistance challenges from the silicon substrate and buffer layer stack, driving interest in GaN-on-SiC for high-power RF/power applications.
- **EMI**: The very fast switching transitions of both technologies generate higher dV/dt and broadband EMI compared to silicon IGBTs, requiring careful gate drive slew-rate control, layout optimization, and filtering.

### Key Points

- Both SiC and GaN exploit wide bandgap and high critical electric field to achieve substantially lower specific on-resistance and faster switching than silicon, per the Baliga figure of merit.
- SiC devices are vertical, unipolar MOSFETs/diodes targeting medium-to-high voltage (650V+) applications; principal challenges are SiC/SiO₂ interface trap density and body diode bipolar degradation.
- GaN devices are lateral HEMTs exploiting a polarization-induced 2DEG; principal challenges are achieving normally-off operation (commonly via p-GaN gate) and managing dynamic $R_{on}$/current collapse from trapping effects.
- System design for both technologies is dominated by parasitic inductance management and gate drive precision due to their exceptionally fast switching speeds.

### Related Topics

- IGBT physics and structure (for baseline silicon power device comparison)
- Power MOSFET $R_{DS(on)}$ scaling and superjunction technology
- GaN cascode configuration design and commercial implementations
- SiC epitaxial growth and basal plane dislocation reduction techniques
- Power device packaging: parasitic inductance minimization, double-pulse testing
- High-frequency magnetics design enabled by WBG switching frequencies
- EMI mitigation techniques for fast-switching power devices

### Next Steps

- Vertical GaN device architectures (emerging alternative to lateral HEMTs)
- Ultra-wide-bandgap materials: Ga₂O₃, diamond, AlN for next-generation power devices
- Reliability testing standards (JEDEC JC-70) specific to WBG power semiconductors