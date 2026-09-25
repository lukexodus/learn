## True Stress and True Strain

### Definition and Motivation

Engineering stress and strain are calculated using the original (undeformed) specimen dimensions, which become progressively less representative of the actual local stress and strain state as a specimen deforms substantially, particularly once necking begins. True stress and true strain are defined instead using the instantaneous (current) dimensions of the specimen, providing a more physically accurate description of the material's actual stress and deformation state at any point during loading.

### True Stress

**Definition**

True stress ($\sigma_T$) is defined as the applied force divided by the instantaneous (current) cross-sectional area:

$$\sigma_T = \frac{F}{A_i}$$

where $A_i$ is the actual cross-sectional area at the instant the force $F$ is applied — a continuously changing quantity during plastic deformation, in contrast to engineering stress, which uses the fixed original area $A_0$.

### True Strain

**Definition**

True strain ($\varepsilon_T$), also called logarithmic strain or natural strain, is defined as the integral of incremental length change relative to the instantaneous length:

$$\varepsilon_T = \int_{l_0}^{l} \frac{dl}{l} = \ln\left(\frac{l}{l_0}\right)$$

This integral (rather than simple $\Delta l/l_0$) is used because strain increments during large deformation should be measured relative to the current length at each instant, not the fixed original length — true strain thereby correctly accumulates the actual sequence of infinitesimal deformation increments.

### Conversion Between Engineering and True Values

For uniaxial tension prior to the onset of necking, and assuming the material deforms plastically at constant volume (a standard, well-supported approximation for metals, since elastic volume change is negligible compared to plastic strain in this regime):

$$\sigma_T = \sigma(1 + \varepsilon)$$



$$\varepsilon_T = \ln(1 + \varepsilon)$$

**Derivation of the strain relationship:**

$$\varepsilon_T = \ln\left(\frac{l}{l_0}\right) = \ln\left(\frac{l_0 + \Delta l}{l_0}\right) = \ln\left(1 + \frac{\Delta l}{l_0}\right) = \ln(1+\varepsilon)$$

**Derivation of the stress relationship (constant volume assumption):**

Constant volume requires $A_0 l_0 = A_i l$, so:

$$A_i = A_0\frac{l_0}{l} = \frac{A_0}{1+\varepsilon}$$

Substituting into the true stress definition:

$$\sigma_T = \frac{F}{A_i} = \frac{F}{A_0}(1+\varepsilon) = \sigma(1+\varepsilon)$$

**[Key Points]**

- These conversion formulas are valid **only up to the point of necking (UTS)**, where deformation remains uniform along the gauge length. Beyond necking, deformation localizes, the cross-sectional area at the neck is no longer related to overall elongation by the simple constant-volume/uniform-strain assumption, and true stress-strain must instead be computed from direct measurement of the actual neck cross-sectional area (or corrected via methods such as the Bridgman correction, which accounts for the triaxial stress state induced by neck curvature).
- At small strains (typically $\varepsilon < 0.05$–$0.1$), true and engineering values are numerically close, since $\ln(1+\varepsilon) \approx \varepsilon$ for small $\varepsilon$; the distinction becomes practically significant primarily at larger plastic strains.

### Key Numerical Comparison

| Engineering Strain (ε) | True Strain, ln(1+ε) | % Difference |
| --- | --- | --- |
| 0.01 | 0.00995 | ~0.5% |
| 0.05 | 0.0488 | ~2.4% |
| 0.10 | 0.0953 | ~4.7% |
| 0.20 | 0.1823 | ~8.9% |
| 0.50 | 0.4055 | ~18.9% |
| 1.00 | 0.6931 | ~30.7% |

This table illustrates why the engineering-true distinction is often negligible in the small-strain elastic regime but becomes substantial in the large-strain plastic regime relevant to metal forming analysis.

### Why True Stress Continues to Rise After UTS

**[Key Points]**

On an engineering stress-strain curve, stress decreases after reaching the UTS (necking onset) because engineering stress is normalized by the fixed original area $A_0$, while the actual load-bearing cross-section at the neck is shrinking faster than the material is strain hardening. On a true stress-true strain curve, however, stress continues to *increase* monotonically until fracture, because true stress is normalized by the actual (reduced) area, correctly reflecting that the material within the neck is still strain hardening even as the engineering curve shows an apparent stress drop. This is a frequently misunderstood distinction: the "decrease" seen in engineering curves past UTS is a geometric (area-normalization) artifact, not evidence that the material itself is softening.

### True Stress-Strain Behavior Diagram

===MERMAID_DIAGRAM===

flowchart TD

A["Engineering stress-strain curve"] --> B["Uses fixed A₀, l₀"]

B --> C["Shows apparent stress drop<br/>after UTS (necking)"]

D["True stress-strain curve"] --> E["Uses instantaneous A_i, l_i"]

E --> F["Stress continues rising<br/>to fracture (real hardening)"]

G["Conversion (valid only<br/>before necking)"] --> H["σ_T = σ(1+ε)"]

G --> I["ε_T = ln(1+ε)"]

C -.same underlying data,<br/>different normalization.-> F



```
### The Hollomon Relationship in True Stress-Strain Space

Beyond yielding and up to necking, many metals follow the power-law (Hollomon) hardening relationship when plotted in true stress-true strain coordinates:

$$\sigma_T = K\varepsilon_T^{\,n}$$

where $K$ is the strength coefficient (the extrapolated true stress at $\varepsilon_T = 1$) and $n$ is the strain-hardening exponent. This relationship is typically identified by plotting $\log\sigma_T$ vs. $\log\varepsilon_T$, which yields a straight line of slope $n$ and intercept $\log K$ for material behavior that follows the power law — a standard technique for extracting $K$ and $n$ from tensile test data.

**Considère's criterion**, which defines the onset of necking, is naturally expressed in true stress-strain terms:

$$\frac{d\sigma_T}{d\varepsilon_T} = \sigma_T$$

For a material following the Hollomon relationship, this condition occurs precisely at $\varepsilon_T = n$, providing a direct link between the measurable strain-hardening exponent and the true strain at which uniform elongation ends.

### Worked Example: Converting Engineering to True Values Before Necking

**[Example]** A tensile test on an aluminum alloy records an engineering stress of $\sigma = 280$ MPa at an engineering strain of $\varepsilon = 0.08$ (this point is confirmed to be before the UTS/necking point). Calculate the corresponding true stress and true strain.

**True strain:**
$$\varepsilon_T = \ln(1+\varepsilon) = \ln(1.08) = 0.0770$$

**True stress:**
$$\sigma_T = \sigma(1+\varepsilon) = 280 \times 1.08 = 302.4\ \text{MPa}$$

At this pre-necking data point, true stress (302.4 MPa) is measurably higher than engineering stress (280 MPa), and true strain (0.0770) is slightly lower than engineering strain (0.08) — consistent with the general pattern that $\sigma_T > \sigma$ and $\varepsilon_T < \varepsilon$ throughout the plastic deformation regime prior to necking.

### Worked Example: Extracting Hollomon Parameters from Two Data Points

**[Example]** A material's true stress-true strain data shows $\sigma_T = 350$ MPa at $\varepsilon_T = 0.05$, and $\sigma_T = 480$ MPa at $\varepsilon_T = 0.20$. Determine $K$ and $n$, assuming Hollomon behavior.

Taking the ratio of the two Hollomon equations:

$$\frac{480}{350} = \left(\frac{0.20}{0.05}\right)^n$$

$$1.371 = 4^n$$

$$n = \frac{\ln(1.371)}{\ln(4)} = \frac{0.3155}{1.3863} \approx 0.228$$

Solving for $K$ using the first data point:

$$K = \frac{\sigma_T}{\varepsilon_T^{\,n}} = \frac{350}{(0.05)^{0.228}}$$

$$(0.05)^{0.228} = e^{0.228\ln(0.05)} = e^{0.228\times(-2.996)} = e^{-0.683} \approx 0.505$$

$$K = \frac{350}{0.505} \approx 693\ \text{MPa}$$

Verification with the second data point: $\sigma_T = 693 \times (0.20)^{0.228}$. Computing $(0.20)^{0.228} = e^{0.228\times\ln(0.20)} = e^{0.228\times(-1.609)} = e^{-0.367} \approx 0.693$, giving $\sigma_T \approx 693 \times 0.693 \approx 480$ MPa — confirming consistency with the given data.

By Considère's criterion, necking is predicted to initiate at $\varepsilon_T = n \approx 0.228$ for this material.

### Behavior Beyond Necking: The Bridgman Correction

**[Key Points]**

Once necking begins, the neck region develops a complex triaxial stress state due to the curvature of the neck profile (radial and circumferential stress components superimpose on the axial stress), meaning the simple uniaxial true stress calculation ($F/A_i$) overestimates the *equivalent uniaxial flow stress* actually representative of the material's plastic behavior. The **Bridgman correction** provides a geometric correction factor based on the measured neck radius of curvature and the minimum neck diameter to estimate the equivalent uniaxial true stress from the measured axial load and the reduced area:

$$\sigma_{eq} = \frac{\sigma_{axial}}{\left(1 + \frac{2R}{a}\right)\ln\left(1 + \frac{a}{2R}\right)}$$

where $a$ is the minimum neck radius and $R$ is the radius of curvature of the neck profile at the minimum cross-section. Applying this correction requires continuous or in-situ measurement of neck geometry (e.g., via digital image correlation or profile tracking during the test), which is more experimentally demanding than standard tensile testing. [Inference: the practical accuracy of the Bridgman correction depends on precise neck-geometry measurement and becomes progressively more approximate as necking severity increases toward final fracture.]

### Applications and Significance

- **Metal forming simulation**: true stress-true strain data (specifically the Hollomon $K$ and $n$ parameters, or full tabulated flow curves) are essential inputs to finite element models of forming processes (stamping, forging, extrusion), since these processes routinely involve strains well beyond the small-strain regime where engineering and true values coincide.
- **Constitutive model calibration**: rate- and temperature-dependent flow stress models (Johnson-Cook, Zerilli-Armstrong, etc.) are formulated in true stress-true strain space, since this representation correctly isolates actual material hardening behavior from specimen-geometry artifacts.
- **Fracture strain characterization**: true strain at fracture (often estimated from $\%RA$ via $\varepsilon_{T,f} = \ln\left(\frac{A_0}{A_f}\right) = \ln\left(\frac{1}{1-\%RA/100}\right)$) provides a geometry-consistent measure of ductility that can be compared more rigorously across different specimen gauge lengths than engineering $\%EL$.
- **Strain-hardening exponent as a formability indicator**: higher $n$ values correlate with better resistance to localized necking during sheet forming operations, making $n$ a standard input parameter in sheet-metal formability assessments (e.g., forming limit diagrams).

### Related Topics
- Stress-strain relationships and the engineering tensile test
- Strain hardening and the Hollomon power-law relationship
- Considère's criterion and necking instability analysis
- Bridgman correction for post-necking true stress determination
- Constitutive flow stress models (Johnson-Cook, Zerilli-Armstrong)
- Sheet metal formability and forming limit diagrams
- Toughness, resilience, and ductility


```