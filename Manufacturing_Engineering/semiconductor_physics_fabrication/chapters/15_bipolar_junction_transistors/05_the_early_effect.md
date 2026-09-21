## The Early Effect

### Overview

The Early effect, named after James M. Early who first characterized it in 1952, describes the modulation of the effective base width in a bipolar junction transistor as a function of the collector-base voltage. Physically, as the reverse bias across the collector-base junction (CBJ) increases, its depletion region widens and encroaches further into the base, reducing the neutral (quasi-neutral) base width available for minority carrier transport. Since collector current in the active region depends inversely on base width, this produces a measurable increase in collector current with increasing $V_{CE}$, even though the idealized BJT model predicts collector current should be independent of $V_{CE}$ in the active region. The Early effect is the primary source of the finite output resistance of a BJT and is essential to accurate small-signal amplifier modeling.

### Physical Origin: Base-Width Modulation

In the ideal, first-order active-region analysis, the neutral base width $W_B$ is treated as a fixed geometric quantity set purely by the metallurgical junction depths. In reality, however, both the emitter-base junction (EBJ) and collector-base junction (CBJ) each have depletion regions that extend into the (lightly doped) base region on either side. The **neutral base width** actually available for minority carrier diffusion is the metallurgical base width minus the portions consumed by these two depletion regions:

$$W_B = W_{B,metallurgical} - x_{dEB} - x_{dCB}$$

where $x_{dEB}$ and $x_{dCB}$ are the portions of the EBJ and CBJ depletion regions that extend into the base, respectively. Since the EBJ is forward-biased and held at a roughly fixed $V_{BE}$ in active operation, $x_{dEB}$ changes very little with bias. However, $x_{dCB}$ depends on the reverse bias across the CBJ, which is directly tied to $V_{CE}$ (since $V_{CB} = V_{CE} - V_{BE}$, and $V_{BE}$ is comparatively constant):

$$x_{dCB} \propto \sqrt{V_{CB} + V_{bi,CB}}$$

following the standard depletion-width relation for a one-sided step junction (with $V_{bi,CB}$ the built-in potential of the CBJ). As $V_{CE}$ (and thus $V_{CB}$) increases, $x_{dCB}$ increases, and $W_B$ correspondingly **decreases** — this is base-width modulation, the physical mechanism underlying the Early effect.

```mermaid
graph LR
    A["VCE increases"] --> B["VCB reverse bias increases<br/>(since VCB = VCE - VBE)"]
    B --> C["CBJ depletion region<br/>widens into base"]
    C --> D["Neutral base width WB<br/>decreases"]
    D --> E["Collector current IC<br/>increases slightly<br/>(inverse relation to WB)"]
```

### Effect on Collector Current

Recall from minority carrier transport analysis that collector current density in the short-base approximation is inversely proportional to the neutral base width:

$$J_C \approx \frac{qD_{nB}n_{p0}}{W_B}\exp\left(\frac{V_{BE}}{V_T}\right)$$

Since $W_B$ itself now depends on $V_{CE}$ (decreasing as $V_{CE}$ increases), $I_C$ acquires an implicit, additional dependence on $V_{CE}$ beyond the primary exponential $V_{BE}$ dependence. This is captured empirically and to good approximation by a **linear extrapolation model**, in which the active-region $I_C$-$V_{CE}$ curves, when extended backward (extrapolated) to negative $V_{CE}$, all appear to converge at a single common point on the voltage axis:

$$I_C = I_S\exp\left(\frac{V_{BE}}{V_T}\right)\left(1+\frac{V_{CE}}{V_A}\right)$$

where $V_A$ is the **Early voltage**, a device parameter (typically in the range of 15 V to 200 V for common silicon BJTs, though highly process-dependent) that quantifies the strength of the effect. A larger $V_A$ indicates a weaker Early effect (flatter output curves, higher output resistance); a smaller $V_A$ indicates a stronger effect (more sloped curves, lower output resistance).

**Key Points**

- The Early voltage $V_A$ is extracted graphically by plotting $I_C$ vs. $V_{CE}$ for a fixed $I_B$ (or $V_{BE}$) in the active region, then linearly extrapolating the resulting nearly-straight curve backward until it crosses the $V_{CE}$ axis; the (negative) intercept value is $-V_A$.
- All curves in a family of $I_C$-$V_{CE}$ characteristics (for different fixed $I_B$ values) ideally extrapolate to approximately the **same** intercept point on the negative $V_{CE}$ axis — this common-convergence-point behavior is a hallmark experimental signature used to verify the Early effect model and extract $V_A$ from measured device data.

### Illustration: Output Characteristics and Early Voltage Extraction (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 400" font-family="Helvetica, Arial, sans-serif">
<text x="350" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">IC-VCE Curves and Early Voltage Extraction (svg_diagram)</text>

<line x1="220" y1="340" x2="650" y2="340" stroke="#333" stroke-width="1.5" />
<text x="620" y="365" font-size="12" fill="#333">VCE</text>
<line x1="220" y1="60" x2="220" y2="340" stroke="#333" stroke-width="1.5" />
<text x="150" y="200" text-anchor="middle" font-size="12" fill="#333" transform="rotate(-90 150 200)">IC</text>

<line x1="60" y1="340" x2="220" y2="340" stroke="#888" stroke-width="1" stroke-dasharray="3,3" />
<circle cx="60" cy="340" r="4" fill="#8a1f1f" />
<text x="60" y="360" text-anchor="middle" font-size="11" fill="#8a1f1f">-VA</text>
<text x="220" y="360" text-anchor="middle" font-size="11" fill="#333">0</text>

<line x1="60" y1="340" x2="640" y2="160" stroke="#c0392b" stroke-width="2" />
<line x1="60" y1="340" x2="640" y2="220" stroke="#2e6b2e" stroke-width="2" />
<line x1="60" y1="340" x2="640" y2="270" stroke="#1f4a8a" stroke-width="2" />
<line x1="60" y1="340" x2="640" y2="310" stroke="#8a5a1f" stroke-width="2" />


<text x="600" y="155" font-size="10" fill="`#c0392b`">IB4 (highest)</text>

<text x="600" y="215" font-size="10" fill="`#2e6b2e`">IB3</text>

<text x="600" y="265" font-size="10" fill="`#1f4a8a`">IB2</text>

<text x="600" y="305" font-size="10" fill="`#8a5a1f`">IB1 (lowest)</text>


<rect x="220" y="60" width="30" height="280" fill="#f2d675" opacity="0.4" />
<text x="235" y="70" text-anchor="middle" font-size="9" fill="#5c4a10" transform="rotate(-90 235 70)" />
<text x="200" y="55" text-anchor="middle" font-size="10" fill="#5c4a10">Sat.</text>

<text x="435" y="345" text-anchor="middle" font-size="10" fill="#333">Active region (extrapolated slopes converge at -VA)</text>

</svg>

### Impact on Small-Signal Model: Output Resistance $r_o$

In the hybrid-$\pi$ small-signal model of the BJT, the Early effect manifests as a finite output resistance $r_o$ connected between collector and emitter, in parallel with the dependent current source $g_m v_{be}$. This resistance is derived by differentiating the Early-effect-modified $I_C$ expression with respect to $V_{CE}$:

$$\frac{1}{r_o} = \frac{\partial I_C}{\partial V_{CE}}\bigg|_{V_{BE}} = \frac{I_S\exp(V_{BE}/V_T)}{V_A} \approx \frac{I_C}{V_A}$$



$$r_o \approx \frac{V_A}{I_C}$$

This relation is one of the most widely used approximate design equations in analog BJT amplifier design: output resistance is inversely proportional to the DC bias collector current, for a fixed Early voltage. It directly determines the maximum achievable voltage gain of a single common-emitter stage (in the absence of external load resistances smaller than $r_o$):

$$|A_{v,max}| = g_m r_o = \frac{I_C/V_T}{V_A/I_C} \quad\Rightarrow\quad |A_{v,max}| = \frac{V_A}{V_T}$$

This result — that the intrinsic maximum voltage gain of a single BJT stage depends only on the Early voltage and thermal voltage, independent of bias current — is a fundamental and widely cited figure of merit in analog IC design, since $g_m \propto I_C$ while $r_o \propto 1/I_C$, causing the current dependence to cancel.

**Key Points**

- Typical values of $V_A/V_T$ for silicon BJTs (with $V_A$ in the tens to low hundreds of volts and $V_T \approx 0.026\,\text{V}$) yield intrinsic single-stage gains on the order of several hundred to several thousand — far higher than typically achievable in a single MOSFET stage at comparable bias, which is one reason BJTs are often favored in certain high-gain analog design contexts. [Inference: relative gain comparison to MOSFET stages depends heavily on the specific MOSFET technology, channel length, and bias point used for comparison, and should not be taken as a universal, technology-independent statement.]
- The Early effect also introduces a small dependency of $\beta$ on $V_{CE}$ (since base width modulation slightly affects $\alpha_T$ as well as $I_C$), though this secondary effect on $\beta$ is typically much smaller in practice than the direct effect on $I_C$/$r_o$, and is often neglected in basic hand analysis.

### Design and Process Dependencies of $V_A$

Several device structural parameters influence the magnitude of the Early voltage:

- **Base doping concentration**: Higher base doping reduces the fractional penetration of the CBJ depletion region into the base for a given reverse bias (since depletion width scales inversely with the square root of the lighter-doped side's concentration in an asymmetric junction, and the base is typically the lighter-doped side relative to a heavily doped collector implant region, though the *overall* CBJ is usually more one-sided toward the lightly doped collector epitaxial layer) — generally, increasing base doping tends to increase $V_A$, though at the cost of reduced emitter injection efficiency (via the $\gamma$ relation) if the emitter-to-base doping ratio is not adjusted accordingly.
- **Base width**: A thicker metallurgical base width means a given depletion region encroachment represents a smaller *fractional* change in neutral base width, improving $V_A$ — but this directly trades off against base transport factor $\alpha_T$ and base transit time (high-frequency performance), both of which favor a thin base. This represents one of the classic design trade-offs in bipolar transistor engineering.
- **Collector doping**: Lower collector doping (as in a lightly doped epitaxial collector region used to support high breakdown voltage) allows the CBJ depletion region to extend more into the collector side and correspondingly less into the base side for a given total depletion width, which can help preserve a higher $V_A$ even with high collector-base breakdown voltage requirements. [Inference: the precise dependence involves the full one-sided/two-sided junction asymmetry analysis and is quantitatively process-specific.]

### Example

A silicon BJT has $I_S = 5\times10^{-15}\,\text{A}$, $V_A = 80\,\text{V}$, and is biased at $V_{BE} = 0.68\,\text{V}$. Compute $I_C$ at $V_{CE} = 2\,\text{V}$ and at $V_{CE} = 10\,\text{V}$:

$$I_{C,base} = I_S\exp\left(\frac{0.68}{0.026}\right) = 5\times10^{-15}\times\exp(26.15) \approx 1.15\,\text{mA}$$

At $V_{CE} = 2\,\text{V}$: $I_C = 1.15\,\text{mA}\times\left(1+\dfrac{2}{80}\right) = 1.15\,\text{mA}\times1.025 \approx 1.179\,\text{mA}$

At $V_{CE} = 10\,\text{V}$: $I_C = 1.15\,\text{mA}\times\left(1+\dfrac{10}{80}\right) = 1.15\,\text{mA}\times1.125 \approx 1.294\,\text{mA}$

This represents roughly a 9.7% increase in $I_C$ across this $V_{CE}$ range at fixed $V_{BE}$ — a modest but non-negligible deviation from ideal constant-current behavior, illustrating why $r_o$ must be included for accurate gain and output impedance calculations in precision analog design, even though it is often reasonably neglected in first-pass DC bias-point calculations.

Output resistance at the $V_{CE}=2\,\text{V}$ bias point: $r_o \approx V_A/I_C \approx 80/1.179\,\text{mA} \approx 67.9\,\text{k}\Omega$.

**Related Topics**

- Hybrid-$\pi$ small-signal model and output resistance $r_o$
- Gummel-Poon model integration of base-width modulation
- Common-emitter amplifier gain limits and intrinsic gain ($g_m r_o$)
- CBJ depletion width and one-sided junction approximations
- Kirk effect (base push-out) as a high-current complement to the Early effect
- Breakdown voltage ($BV_{CEO}$, $BV_{CBO}$) trade-offs with base and collector doping
- Punch-through as an extreme (destructive) limit of base-width modulation
- MOSFET channel-length modulation as an analogous short-channel effect