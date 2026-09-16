## True Stress and True Strain

### Overview

True stress and true strain provide a more physically accurate description of a material's mechanical response during large plastic deformation than engineering stress and strain, because they account for the continuously changing cross-sectional area and instantaneous length of a specimen as it deforms. These quantities are essential for accurate modeling of metal forming processes, constitutive material models, and interpreting material behavior beyond the onset of necking.

### Limitations of Engineering Stress and Strain

**Key Points**

- Engineering stress and strain are calculated using the *original* cross-sectional area ($A_0$) and *original* gauge length ($l_0$), which remain fixed throughout the calculation even though the specimen's actual dimensions change during loading.
- This approximation is reasonably accurate at small strains (within the elastic region and early plastic region) but becomes increasingly inaccurate as deformation progresses, especially after the onset of necking, where the engineering stress-strain curve shows a decrease in stress that does not reflect the material's actual flow behavior — it merely reflects the shrinking load-bearing area.
- True stress and true strain were developed to correct this limitation by referencing the *instantaneous* dimensions of the specimen at each point during the test.

### Definitions

**True Stress**

$$\sigma_T = \dfrac{F}{A_i}$$

Where $F$ is the instantaneous applied force and $A_i$ is the instantaneous (actual, current) cross-sectional area of the specimen — not the original area.

**True Strain**

True strain is defined incrementally, as the sum (integral) of infinitesimal length changes relative to the *current* length at each instant, rather than relative to the fixed original length:

$$\epsilon_T = \int_{l_0}^{l_i} \dfrac{dl}{l} = \ln\left(\dfrac{l_i}{l_0}\right)$$

### Relating True and Engineering Values

**Key Points**

- Up to the point of necking, and assuming the material deforms at constant volume (a standard assumption for plastic deformation of metals, since plastic flow involves negligible volume change compared to elastic deformation), true stress and true strain can be derived directly from their engineering counterparts:

$$\sigma_T = \sigma(1 + \epsilon)$$



$$\epsilon_T = \ln(1 + \epsilon)$$

- These conversion formulas are valid **only up to the onset of necking**. Once necking begins, deformation becomes localized and non-uniform along the gauge length, and the assumption of uniform cross-sectional area reduction along the gauge length (which underlies these formulas) no longer holds. Beyond this point, true stress and true strain within the neck must be computed from direct measurements of the actual, local minimum cross-sectional area at the neck, rather than from the engineering curve.

**Example**

For a specimen with engineering stress $\sigma = 400\ MPa$ and engineering strain $\epsilon = 0.10$ (prior to necking):

$$\sigma_T = 400 \times (1 + 0.10) = 440\ MPa$$



$$\epsilon_T = \ln(1 + 0.10) = \ln(1.10) \approx 0.0953$$

This shows that true stress is always slightly higher than engineering stress for a given data point (since $A_i < A_0$ under tension), while true strain is always slightly lower than engineering strain at the same point (a consequence of the logarithmic versus linear definitions).

### Shape of the True Stress-True Strain Curve

**Key Points**

- Unlike the engineering stress-strain curve, which decreases after the ultimate tensile strength due to necking, the true stress-strain curve **rises continuously and monotonically** up to fracture. This is because true stress correctly accounts for the shrinking cross-sectional area at the neck, so the material continues to show increasing flow stress (strain hardening) as deformation proceeds, right up to failure.
- This continuously rising behavior more accurately reflects the underlying strengthening mechanism (strain/work hardening via increasing dislocation density) than the apparent post-UTS softening seen on the engineering curve, which is a geometric artifact rather than a true material softening.

### Power-Law (Hollomon) Hardening Relationship

**Key Points**

- For many metals, the true stress-true strain curve in the plastic region can be approximated by a power-law relationship, commonly known as the Hollomon equation:

$$\sigma_T = K\epsilon_T^{\,n}$$

Where:

- $K$ = strength coefficient (a material constant, with units of stress)
- $n$ = strain-hardening exponent (dimensionless, typically between 0 and 1 for metals)
- A higher value of $n$ indicates a material that strain-hardens more significantly with increasing plastic strain, generally correlating with greater capacity to distribute strain uniformly and delay the onset of necking (relevant to formability in sheet metal operations).
- $K$ and $n$ are typically determined by plotting $\log \sigma_T$ versus $\log \epsilon_T$, which linearizes the power-law relationship:

$$\log \sigma_T = \log K + n \log \epsilon_T$$

The slope of this log-log plot gives $n$, and the intercept gives $\log K$.

- [Inference] Because $K$ and $n$ are empirically fitted constants specific to a given material, composition, and prior processing history (e.g., degree of cold work, heat treatment condition), published values should be treated as representative for a given material condition rather than universal constants, and verified against material-specific data sheets for critical design or simulation work.

### Necking and the Considère Criterion

**Key Points**

- Necking initiates at the point where the increase in true stress due to strain hardening can no longer compensate for the decrease in cross-sectional area, causing deformation to localize rather than continue uniformly along the gauge length.
- This condition is captured mathematically by the **Considère criterion**, which states that necking begins when:

$$\dfrac{d\sigma_T}{d\epsilon_T} = \sigma_T$$

- For a material following the Hollomon power-law relationship, this condition can be shown to occur when the true strain equals the strain-hardening exponent:

$$\epsilon_T = n$$

- [Inference] This relationship implies that materials with a higher strain-hardening exponent $n$ can sustain more uniform plastic strain before necking begins, which is a key reason why $n$ is often used as a practical indicator of sheet metal formability.

### Diagram: Engineering vs. True Stress-Strain Curves

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 420">
<text x="350" y="25" font-size="16" font-weight="bold" text-anchor="middle" fill="#1a1a1a">Engineering vs. True Stress-Strain Curves (svg_diagram)</text>
<line x1="80" y1="370" x2="650" y2="370" stroke="#1a1a1a" stroke-width="2" />
<line x1="80" y1="370" x2="80" y2="50" stroke="#1a1a1a" stroke-width="2" />
<text x="360" y="400" font-size="14" text-anchor="middle" fill="#1a1a1a">Strain</text>
<text x="30" y="210" font-size="14" text-anchor="middle" fill="#1a1a1a" transform="rotate(-90 30 210)">Stress</text>
<path d="M 80 370 L 190 220" stroke="#0057b7" stroke-width="3" fill="none" />
<path d="M 190 220 Q 260 185 330 165" stroke="#0057b7" stroke-width="3" fill="none" />
<path d="M 330 165 Q 420 130 480 120" stroke="#0057b7" stroke-width="3" fill="none" />
<path d="M 480 120 Q 550 145 600 200" stroke="#0057b7" stroke-width="3" fill="none" />
<text x="605" y="200" font-size="12" fill="#0057b7">Engineering</text>
<path d="M 80 370 L 190 220" stroke="#c0392b" stroke-width="3" stroke-dasharray="6,3" fill="none" />
<path d="M 190 220 Q 260 185 330 155" stroke="#c0392b" stroke-width="3" stroke-dasharray="6,3" fill="none" />
<path d="M 330 155 Q 420 105 480 80" stroke="#c0392b" stroke-width="3" stroke-dasharray="6,3" fill="none" />
<path d="M 480 80 Q 540 65 580 55" stroke="#c0392b" stroke-width="3" stroke-dasharray="6,3" fill="none" />
<text x="500" y="50" font-size="12" fill="#c0392b">True</text>
<circle cx="480" cy="120" r="4" fill="#1a1a1a" />
<text x="420" y="105" font-size="11" fill="#1a1a1a">Necking begins (curves diverge)</text>
</svg>

### Civil Engineering and Materials Processing Relevance

**Example**

True stress-strain relationships are particularly important in contexts involving large plastic deformation:

- **Metal forming simulations** (e.g., finite element analysis of rolled or cold-formed structural steel sections, such as cold-formed steel framing members) rely on true stress-strain input data (often via the Hollomon relationship) to accurately capture material flow behavior during forming, since engineering stress-strain data would misrepresent the material response at the large strains involved in forming operations.
- **Reinforcing steel behavior in extreme deformation scenarios** (e.g., seismic analysis models requiring large post-yield strain response, or progressive collapse analysis) may require a true stress-strain material model rather than the simpler engineering bilinear model to accurately predict ductile capacity near ultimate deformation states.
- [Inference] For typical elastic-range structural design and code-based serviceability checks, the distinction between engineering and true stress-strain is negligible (since strains remain very small), so most conventional structural design continues to use engineering stress and strain; true stress-strain becomes relevant specifically when analysis involves strains large enough for the two measures to diverge meaningfully.

### Comparative Summary Table

| Quantity | Engineering | True |
| --- | --- | --- |
| Stress definition | $F/A_0$ (constant reference area) | $F/A_i$ (instantaneous area) |
| Strain definition | $\Delta l / l_0$ (linear, constant reference length) | $\ln(l_i/l_0)$ (logarithmic, incremental) |
| Curve shape after UTS | Decreases (geometric artifact of necking) | Continues to rise (reflects true hardening) |
| Validity post-necking | Formulas below remain usable for reporting nominal design values | Direct conversion formulas invalid; requires local area measurement |
| Typical use | Design allowables, standard reporting | Forming simulations, constitutive modeling, large-strain analysis |

**Next Steps**

- The Tensile Test and Stress-Strain Curve
- Yielding, Ductility, and Toughness
- Strain Hardening Mechanisms and Dislocation Density
- The Considère Criterion and Necking Behavior
- Constitutive Material Models for Finite Element Analysis
- Cold-Formed Steel Behavior and Forming-Induced Strain Effects
- Formability of Sheet Metals