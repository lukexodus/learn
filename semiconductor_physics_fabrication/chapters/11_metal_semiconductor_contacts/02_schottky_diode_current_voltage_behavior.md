## Schottky Diode Current-Voltage Behavior

### Introduction

The current-voltage (I-V) characteristic of a Schottky diode is governed primarily by thermionic emission of majority carriers over the metal-semiconductor barrier, in contrast to the minority-carrier diffusion mechanism that dominates p-n junction behavior. This distinction gives Schottky diodes several practically important characteristics: lower forward turn-on voltage, faster switching (no minority carrier storage), and a different temperature dependence than p-n diodes. This topic builds directly on the barrier physics established in Schottky barrier formation.

### Thermionic Emission Theory

The dominant current transport mechanism in moderately doped Schottky diodes is thermionic emission — carriers with sufficient thermal energy surmount the barrier $\phi_{Bn}$ and are collected. The current density is given by:

$$J = J_s\left(e^{qV/nkT} - 1\right)$$



$$J_s = A^*T^2 e^{-q\phi_{Bn}/kT}$$

where:

- $A^*$ is the effective Richardson constant, $A^* = \dfrac{4\pi q m^* k^2}{h^3}$, which depends on the semiconductor's effective mass $m^*$ (for free-electron mass, $A^* \approx 120$ A/(cm²·K²); actual values differ by material due to effective mass and valley degeneracy)
- $\phi_{Bn}$ is the Schottky barrier height
- $n$ is the ideality factor (ideally close to 1 for pure thermionic emission)

**Key Points**

- $J_s$ is exponentially sensitive to barrier height $\phi_{Bn}$ and to temperature $T$ — a small change in barrier height produces a large change in saturation current density.
- Unlike a p-n junction's $I_0$, which depends on minority carrier diffusion lengths and diffusion coefficients (and thus on both sides of the junction), the Schottky $J_s$ depends only on the barrier height and the semiconductor's effective mass via $A^*$.

### Forward Bias Behavior

Under forward bias ($V > 0$, metal positive relative to n-type semiconductor), the barrier from the semiconductor side is reduced, and electron injection from semiconductor to metal increases exponentially:

$$J_F \approx A^*T^2 e^{-q\phi_{Bn}/kT} \cdot e^{qV/nkT} \quad \text{for } V \gg kT/q$$

**Typical forward characteristics:**

- Turn-on voltage is significantly lower than a p-n diode of comparable material — typically 0.2-0.4 V for Si Schottky diodes versus approximately 0.6-0.7 V for Si p-n diodes, because $\phi_{Bn}$ is generally smaller than the built-in potential of a comparably doped p-n junction.
- At sufficiently high forward current, series resistance from the bulk semiconductor and contacts causes the same high-injection roll-off seen in p-n diodes (see Non-ideal diode effects), where the I-V curve bends away from the ideal exponential slope.

### Reverse Bias Behavior

Under reverse bias, thermionic emission theory predicts current saturation at $J_s$, analogous to a p-n diode's $-I_0$. However, real Schottky diodes show reverse current that increases with reverse bias magnitude rather than truly saturating, due to:

**Image-Force (Schottky) Barrier Lowering**

The applied reverse field increases the maximum electric field $E_{max}$ at the interface, which lowers the effective barrier via the image-charge interaction:

$$\Delta\phi_B = \sqrt{\frac{qE_{max}}{4\pi\varepsilon_s}}$$

Since $E_{max}$ increases with reverse bias (proportional to $\sqrt{V_{bi} + V_R}$ for a uniformly doped depletion region), the effective barrier continuously decreases with increasing reverse bias, producing a soft, gradually rising reverse leakage current rather than a hard saturation plateau.

**Edge and Perimeter Leakage**

Practical Schottky diodes often use a guard ring (a p-n junction diffusion surrounding the Schottky contact) specifically to reduce electric field crowding at the contact edge, which would otherwise dominate reverse leakage and lower the effective breakdown voltage.

```mermaid
graph LR
    A[Reverse Bias Applied] --> B[Depletion width increases]
    B --> C[Interface electric field Emax increases]
    C --> D[Image-force barrier lowering increases]
    D --> E[Effective barrier height decreases]
    E --> F[Reverse leakage current rises, does not saturate]
```

### Comparison: Schottky Diode vs. p-n Junction Diode

| Property | Schottky Diode | p-n Junction Diode |
| --- | --- | --- |
| Dominant carriers | Majority carriers (thermionic emission) | Minority carriers (diffusion) |
| Turn-on voltage (Si) | ~0.2-0.4 V | ~0.6-0.7 V |
| Switching speed | Fast (no minority carrier storage) | Slower (limited by minority carrier recombination/reverse recovery) |
| Reverse recovery | Negligible (majority-carrier device) | Significant, especially for high forward current |
| Reverse leakage | Higher, increases with bias (barrier lowering) | Lower, more saturating |
| Temperature sensitivity of $I_0$/$J_s$ | Exponential in $\phi_{Bn}$ and $T^2$ prefactor | Exponential in $E_g$ via $n_i^2$ |
| Capacitance | Depletion capacitance only (majority carrier device) | Depletion + diffusion capacitance |

### Ideality Factor and Deviations from Ideal Thermionic Emission

Similar to p-n diodes, real Schottky diodes show $n$ slightly greater than 1 (typically 1.02-1.2 for well-fabricated diodes) due to:

- Image-force barrier lowering's voltage dependence, which effectively modifies the exponential slope
- Interface state effects and non-uniform barrier height across the contact area (barrier inhomogeneity), where local low-barrier "patches" dominate current at low bias, artificially raising the extracted ideality factor
- Series resistance effects at higher forward current, which bend the semi-log I-V curve exactly as described for p-n diodes

**Barrier Inhomogeneity**

Real Schottky contacts are rarely perfectly uniform; local variations in barrier height (from interface defects, grain boundaries in polycrystalline metal films, or non-uniform interfacial oxide) mean that current is dominated by the lowest-barrier regions at low forward bias, while higher-barrier regions contribute more as bias increases. This is often modeled with a Gaussian distribution of barrier heights, producing an apparent ideality factor and apparent barrier height that both depend on temperature — a widely used diagnostic for detecting barrier inhomogeneity in Schottky diode characterization via temperature-dependent I-V-T measurements.

### Extraction of Diode Parameters from Measured Data

**Key Points**

- **Barrier height $\phi_{Bn}$:** extracted from the intercept of $\ln(J_s/T^2)$ vs. $1/T$ (Richardson plot), using the slope to obtain $\phi_{Bn}$ and the intercept to obtain $A^*$.
- **Ideality factor $n$:** extracted from the slope of $\ln(I)$ vs. $V$ in the linear (mid-bias) region of the forward semi-log plot.
- **Series resistance $R_s$:** extracted using the same high-current deviation methods used for p-n diodes (e.g., Cheung method), since the underlying resistive voltage drop mechanism is identical.
- Because $J_s$ depends exponentially on $\phi_{Bn}$ but only as $T^2$ on temperature, Richardson plot analysis is highly sensitive to accurate barrier height determination and is a standard technique for characterizing new metal-semiconductor material systems.

### Worked Example

**Example**

Consider a Si Schottky diode ($n$-type, $\phi_{Bn} = 0.65$ eV) at $T = 300$ K with $A^* = 110$ A/(cm²·K²).

Saturation current density:

$$J_s = A^*T^2 e^{-q\phi_{Bn}/kT} = 110 \times (300)^2 \times e^{-0.65/0.02585}$$



$$J_s = 110 \times 9\times10^4 \times e^{-25.14} \approx 9.9\times10^6 \times 1.2\times10^{-11} \approx 1.2 \times 10^{-4} \text{ A/cm}^2$$

At forward bias $V = 0.3$ V (ideality factor $n = 1.05$, room temperature $kT/q \approx 0.02585$ V):

$$J_F = J_s\left(e^{qV/nkT} - 1\right) \approx 1.2\times10^{-4} \times e^{0.3/(1.05 \times 0.02585)}$$



$$J_F \approx 1.2\times10^{-4} \times e^{11.06} \approx 1.2\times10^{-4} \times 6.4\times10^{4} \approx 7.7 \text{ A/cm}^2$$

This illustrates the characteristic low turn-on voltage: significant current density is reached at only 0.3 V forward bias, well below the ~0.6-0.7 V typical of an equivalent Si p-n diode.

### Applications Exploiting Schottky I-V Characteristics

- **RF and microwave detectors/mixers:** low turn-on voltage and negligible minority carrier storage enable high-frequency rectification
- **Power rectifiers:** fast switching with no reverse recovery loss makes Schottky diodes preferred in switch-mode power supplies, at the cost of higher reverse leakage and lower reverse breakdown voltage than comparable p-n diodes
- **Solar cell / photodetector Schottky junctions:** exploit the same barrier physics for photocurrent generation
- **Clamping diodes:** used to prevent transistor saturation in TTL logic (Schottky-clamped transistors) by exploiting the low forward voltage drop

### Common Pitfalls

- Assuming Schottky diode reverse current truly saturates like an ideal p-n diode — image-force barrier lowering makes this generally not the case, particularly at higher reverse bias.
- Using a single-temperature I-V measurement to extract $\phi_{Bn}$ and assuming it fully characterizes the diode — barrier inhomogeneity means single-temperature extraction can give a value that differs from the "true" mean barrier height, and full I-V-T analysis is generally needed for accurate characterization.
- Neglecting series resistance when extracting ideality factor from high forward-current data, which inflates the apparent $n$.

### Conclusion

Schottky diode I-V behavior is fundamentally governed by thermionic emission of majority carriers over the barrier established at the metal-semiconductor interface, producing characteristically lower turn-on voltages and faster switching than p-n junction diodes. Reverse-bias behavior deviates from ideal saturation due to image-force barrier lowering, and real devices show a range of non-idealities — barrier inhomogeneity, series resistance, edge leakage — that are diagnosed using the same ideality-factor and temperature-dependent analysis techniques developed for p-n junctions, adapted to the thermionic emission framework.

**Related Topics**

- Richardson plot analysis and effective Richardson constant extraction
- Guard ring structures for edge field reduction
- Schottky diode reverse recovery and comparison to p-n switching losses
- Barrier inhomogeneity and Gaussian barrier distribution models
- RF mixer and detector diode design
- Schottky-clamped bipolar transistor logic (TTL)