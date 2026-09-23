## The Big Bang Model


### Overview

The Big Bang model is the prevailing cosmological description of the universe's evolution from an extremely hot, dense early state to its present large-scale structure. It is not a theory of an "explosion in space"; it describes the **expansion of space itself**, in which the metric scale of the universe grows with time. The model is built on general relativity, the cosmological principle, and a small set of measurable parameters, and it is confirmed by several independent lines of observational evidence.

**Key Points**

- The model describes the evolution of the universe from a hot, dense early state, not the origin of that state. The initial singularity is a feature of classical general relativity that is expected to be replaced by a quantum-gravity description.
- Expansion is a property of spacetime geometry, not motion of galaxies through a pre-existing space.
- The standard version is the $\Lambda$CDM model: a spatially flat universe dominated today by dark energy ($\Lambda$) and cold dark matter (CDM).
- The current age of the universe is approximately $13.8 \times 10^{9}$ years (value depends on the dataset and analysis used; Planck-era analyses give about $13.80 \pm 0.02$ Gyr).

### Theoretical Foundations

#### The Cosmological Principle

On sufficiently large scales (roughly $\gtrsim 100$ Mpc), the universe is:

- **Homogeneous**: the same at every location.
- **Isotropic**: the same in every direction.

These assumptions restrict the spacetime metric to the Friedmann–Lemaître–Robertson–Walker (FLRW) form.

#### The FLRW Metric

$$ds^2 = -c^2 dt^2 + a(t)^2 \left[ \frac{dr^2}{1 - k r^2} + r^2 \left( d\theta^2 + \sin^2\theta \, d\phi^2 \right) \right]$$

Where:

- $a(t)$ is the dimensionless **scale factor** (normalized so $a(t_0) = 1$ today).
- $k$ is the spatial curvature parameter: $k = +1$ (closed), $0$ (flat), $-1$ (open).
- $r$ is the comoving radial coordinate.

#### The Friedmann Equations

Applying Einstein's field equations to the FLRW metric for a perfect fluid gives:

$$\left(\frac{\dot{a}}{a}\right)^2 = H^2 = \frac{8\pi G}{3}\rho - \frac{k c^2}{a^2} + \frac{\Lambda c^2}{3}$$



$$\frac{\ddot{a}}{a} = -\frac{4\pi G}{3}\left(\rho + \frac{3p}{c^2}\right) + \frac{\Lambda c^2}{3}$$

Where:

- $H = \dot{a}/a$ is the **Hubble parameter**.
- $\rho$ is the total energy density (as mass density) and $p$ is the pressure.
- $\Lambda$ is the cosmological constant.

The **fluid (continuity) equation** follows from these:

$$\dot{\rho} + 3H\left(\rho + \frac{p}{c^2}\right) = 0$$

#### Density Parameters

Define the **critical density**:

$$\rho_c = \frac{3H^2}{8\pi G}$$

and the density parameters $\Omega_i = \rho_i / \rho_c$. The first Friedmann equation can then be written as:

$$\frac{H^2}{H_0^2} = \Omega_r a^{-4} + \Omega_m a^{-3} + \Omega_k a^{-2} + \Omega_\Lambda$$

with $\Omega_r + \Omega_m + \Omega_k + \Omega_\Lambda = 1$.

| Component | Equation of state $w = p/(\rho c^2)$ | Scaling of $\rho$ | Approximate present $\Omega$ |
| --- | --- | --- | --- |
| Radiation (photons, neutrinos while relativistic) | $1/3$ | $a^{-4}$ | $\sim 9 \times 10^{-5}$ |
| Matter (baryons + cold dark matter) | $0$ | $a^{-3}$ | $\sim 0.31$ |
| Curvature | $-1/3$ (effective) | $a^{-2}$ | $\lesssim 0.001$ (consistent with 0) |
| Dark energy (cosmological constant) | $-1$ | constant | $\sim 0.69$ |

Values are approximate, based on Planck 2018 results; they vary slightly with the combination of datasets used.

#### Solutions for Single-Component Universes

For a flat universe dominated by one component with constant $w$:

$$a(t) \propto t^{2/(3(1+w))} \quad (w \neq -1)$$

- Radiation-dominated ($w = 1/3$): $a \propto t^{1/2}$
- Matter-dominated ($w = 0$): $a \propto t^{2/3}$
- Cosmological-constant-dominated ($w = -1$): $a \propto e^{Ht}$ (exponential expansion, de Sitter)

### Observational Evidence

#### 1. Hubble–Lemaître Law and Cosmic Expansion

Distant galaxies recede with a velocity proportional to their distance:

$$v = H_0 d$$

The **cosmological redshift** relates observed and emitted wavelengths to the scale factor:

$$1 + z = \frac{\lambda_{\text{obs}}}{\lambda_{\text{emit}}} = \frac{a(t_0)}{a(t_{\text{emit}})}$$

**Example**

A galaxy is observed with the hydrogen H-alpha line ($\lambda_{\text{emit}} = 656.3$ nm) at $\lambda_{\text{obs}} = 722.0$ nm.

$$z = \frac{722.0 - 656.3}{656.3} \approx 0.100$$

For small $z$, the recession velocity is $v \approx cz \approx 3.0 \times 10^{4}$ km/s. With $H_0 \approx 70$ km/s/Mpc:

$$d \approx \frac{v}{H_0} = \frac{3.0 \times 10^{4}}{70} \approx 430 \text{ Mpc}$$

**Output**

$$z \approx 0.100, \quad v \approx 3.0 \times 10^{4} \text{ km/s}, \quad d \approx 430 \text{ Mpc}$$

**Note on $H_0$**: Measurements of $H_0$ currently disagree. Early-universe inference (CMB, assuming $\Lambda$CDM) gives $\approx 67$ km/s/Mpc, while local distance-ladder measurements give $\approx 73$ km/s/Mpc. This is the "Hubble tension," and whether it reflects systematic error or new physics is unresolved.

#### 2. The Cosmic Microwave Background (CMB)

The CMB is relic radiation released at recombination ($z \approx 1090$, about 380,000 years after the Big Bang), when the universe cooled enough for neutral atoms to form and photons to free-stream.

Properties:

- Nearly perfect blackbody spectrum at $T_0 = 2.7255 \pm 0.0006$ K (measured by COBE/FIRAS).
- Nearly isotropic, with fractional temperature anisotropies $\Delta T / T \sim 10^{-5}$.
- A dipole anisotropy of $\sim 3.4$ mK arises from the Solar System's motion relative to the CMB frame.

Because radiation redshifts as $T \propto (1 + z)$:

$$T(z) = T_0 (1 + z)$$

**Example**

Temperature at recombination:

$$T_{\text{rec}} = 2.7255 \times (1 + 1090) \approx 2974 \text{ K} \approx 3000 \text{ K}$$

This is consistent with the temperature at which hydrogen ionization fraction drops rapidly.

**Angular power spectrum**: The CMB temperature map is decomposed into spherical harmonics with power $C_\ell$. Features of the spectrum encode cosmological parameters:

- The position of the **first acoustic peak** ($\ell \approx 220$) measures spatial curvature; its location indicates $\Omega_k \approx 0$ (flat).
- The relative heights of the peaks constrain the baryon density $\Omega_b h^2$ and the dark matter density $\Omega_c h^2$.
- Damping at high $\ell$ (Silk damping) reflects photon diffusion during recombination.

#### 3. Big Bang Nucleosynthesis (BBN)

For roughly the first few minutes ($T \sim 10^{10}$ K down to $\sim 10^{8}$ K), the universe was hot enough for nuclear fusion. BBN predicts primordial abundances of light nuclei as a function of a single parameter, the baryon-to-photon ratio $\eta$:

| Nuclide | Predicted primordial abundance (approximate) |
| --- | --- |
| $^4\text{He}$ | $\sim 24\text{–}25\%$ by mass |
| $^2\text{H}$ (D) | $\sim 2.5 \times 10^{-5}$ by number relative to H |
| $^3\text{He}$ | $\sim 10^{-5}$ by number relative to H |
| $^7\text{Li}$ | $\sim 5 \times 10^{-10}$ by number relative to H |

Observed helium and deuterium abundances agree well with predictions. The predicted $^7\text{Li}$ abundance is roughly a factor of three above observed values in old stars, known as the **cosmological lithium problem**, which remains unresolved.

**Neutron-to-proton ratio and helium fraction**

Weak interactions keep neutrons and protons in equilibrium until freeze-out at $T \approx 0.8$ MeV, where:

$$\frac{n}{p} = \exp\left(-\frac{\Delta m c^2}{k_B T}\right), \quad \Delta m c^2 = 1.293 \text{ MeV}$$

After freeze-out and some neutron decay before deuterium forms, $n/p \approx 1/7$. Nearly all neutrons end up in $^4\text{He}$, giving a helium mass fraction:

$$Y_p = \frac{2(n/p)}{1 + (n/p)} = \frac{2 \times (1/7)}{1 + 1/7} = \frac{2/7}{8/7} = \frac{1}{4} = 0.25$$

**Output**

$$Y_p \approx 0.25$$

#### 4. Large-Scale Structure and Baryon Acoustic Oscillations (BAO)

Sound waves in the photon–baryon plasma left a characteristic length scale, the **sound horizon** at the drag epoch ($r_d \approx 147$ Mpc), imprinted in both the CMB and the galaxy distribution. Measuring this "standard ruler" at various redshifts maps the expansion history.

#### 5. Type Ia Supernovae and Cosmic Acceleration

Type Ia supernovae serve as standardizable candles. In 1998, observations by two independent teams showed that distant supernovae are dimmer than expected for a decelerating universe, implying accelerated expansion. This is interpreted as evidence for dark energy, with $\Omega_\Lambda \approx 0.7$.

The deceleration parameter is:

$$q_0 = -\frac{\ddot{a} a}{\dot{a}^2}\bigg|_{t_0} = \frac{\Omega_m}{2} - \Omega_\Lambda$$

**Example**

With $\Omega_m = 0.31$ and $\Omega_\Lambda = 0.69$:

$$q_0 = \frac{0.31}{2} - 0.69 = -0.535$$

**Output**

$$q_0 \approx -0.54$$

A negative $q_0$ indicates accelerating expansion.

### Thermal History of the Universe

The temperature of the early universe scales approximately as $T \propto 1/a$, and in the radiation era, the relation between time and temperature is approximately:

$$t \approx 1.3 \text{ s} \left(\frac{T}{1 \text{ MeV}}\right)^{-2} \quad (\text{approximate, depends on } g_*)$$

The exact coefficient depends on the effective number of relativistic degrees of freedom $g_*$.

#### Timeline of Major Epochs

| Epoch | Approximate time | Approximate temperature | Key events |
| --- | --- | --- | --- |
| Planck epoch | $< 10^{-43}$ s | $\sim 10^{32}$ K | Quantum gravity regime; no established theory |
| Inflation (hypothesized) | $\sim 10^{-36}$ to $10^{-32}$ s | — | Near-exponential expansion; seeds of structure [Inference: inflation is a well-motivated but not directly confirmed paradigm] |
| Electroweak transition | $\sim 10^{-12}$ s | $\sim 10^{15}$ K | Electroweak symmetry breaking |
| Quark–hadron transition | $\sim 10^{-5}$ s | $\sim 10^{12}$ K | Quarks confined into protons and neutrons |
| Neutrino decoupling | $\sim 1$ s | $\sim 10^{10}$ K | Neutrinos cease interacting |
| Electron–positron annihilation | $\sim 10$ s | $\sim 5 \times 10^{9}$ K | Heats photons relative to neutrinos |
| Big Bang nucleosynthesis | $\sim 3$ to $20$ min | $10^{9}$ to $10^{8}$ K | Light nuclei form |
| Matter–radiation equality | $\sim 5 \times 10^{4}$ yr | $\sim 10^{4}$ K | $\rho_m = \rho_r$, at $z_{eq} \approx 3400$ |
| Recombination | $\sim 3.8 \times 10^{5}$ yr | $\sim 3000$ K | Neutral atoms form |
| Photon decoupling | $\sim 3.8 \times 10^{5}$ yr | $\sim 3000$ K | CMB released |
| Dark ages | $\sim 4 \times 10^{5}$ to $\sim 10^{8}$ yr | falling | No luminous sources |
| Reionization | $\sim 2 \times 10^{8}$ to $10^{9}$ yr | — | First stars and galaxies ionize the intergalactic medium ($z \sim 6\text{–}8$) |
| Dark-energy dominance | $\sim 9.8 \times 10^{9}$ yr | $\sim 4$ K | Acceleration begins ($z \approx 0.3$–$0.7$) |
| Present | $13.8 \times 10^{9}$ yr | $2.7255$ K | — |

Timings for early epochs are model-dependent and approximate; behavior in the pre-BBN era relies on extrapolated particle physics.

```mermaid
flowchart LR
    A[Planck Epoch] --> B[Inflation]
    B --> C[Reheating and Quark-Gluon Plasma]
    C --> D[Hadron Formation]
    D --> E[Neutrino Decoupling]
    E --> F[Big Bang Nucleosynthesis]
    F --> G[Matter-Radiation Equality]
    G --> H[Recombination and CMB]
    H --> I[Dark Ages]
    I --> J[First Stars and Reionization]
    J --> K[Galaxy and Structure Formation]
    K --> L[Dark Energy Dominance]
    L --> M[Present Day]
```

### Age and Horizon Calculations

#### Age of the Universe

$$t_0 = \int_0^1 \frac{da}{a H(a)} = \frac{1}{H_0} \int_0^1 \frac{da}{\sqrt{\Omega_r a^{-2} + \Omega_m a^{-1} + \Omega_k + \Omega_\Lambda a^2}}$$

For a flat, matter-plus-$\Lambda$ universe (neglecting radiation), this has the closed-form solution:

$$t_0 = \frac{2}{3 H_0 \sqrt{\Omega_\Lambda}} \sinh^{-1}\left(\sqrt{\frac{\Omega_\Lambda}{\Omega_m}}\right)$$

**Example**

With $H_0 = 67.7$ km/s/Mpc, $\Omega_m = 0.31$, $\Omega_\Lambda = 0.69$:

The Hubble time is:

$$\frac{1}{H_0} = \frac{977.8}{67.7} \text{ Gyr} \approx 14.44 \text{ Gyr}$$



$$\sqrt{\Omega_\Lambda/\Omega_m} = \sqrt{2.226} \approx 1.492, \quad \sinh^{-1}(1.492) \approx 1.2$$



$$t_0 \approx \frac{2}{3 \times 0.831} \times 1.2 \times 14.44 \text{ Gyr} \approx 13.9 \text{ Gyr}$$

**Output**

$$t_0 \approx 13.9 \text{ Gyr}$$

This agrees to within rounding with the value of about 13.8 Gyr obtained when radiation and precise parameter values are included.

#### The Particle Horizon

The comoving distance light could have traveled since the beginning:

$$\chi_{\text{hor}} = c \int_0^{t_0} \frac{dt}{a(t)} = c \int_0^{1} \frac{da}{a^2 H(a)}$$

The present particle horizon radius is approximately $46$ billion light-years (about $14{,}200$ Mpc). This exceeds $c t_0 \approx 13.8$ billion light-years because space expanded while light traveled.

#### The Hubble Radius

$$R_H = \frac{c}{H_0} \approx 4.4 \text{ Gpc} \approx 14 \text{ billion light-years}$$

The Hubble radius marks where the recession speed equals $c$. It is **not** the edge of the observable universe.

### Conceptual Problems and Their Resolutions

#### Horizon Problem

Regions of the CMB sky separated by more than about $2^\circ$ were never in causal contact in a pure radiation- and matter-dominated model, yet they share nearly identical temperatures.

#### Flatness Problem

The curvature contribution scales as $|\Omega - 1| \propto 1/(a^2 H^2)$, which grows during decelerated expansion. To have $\Omega \approx 1$ today requires $|\Omega - 1| \lesssim 10^{-60}$ at the Planck time.

#### Monopole Problem

Grand unified theories predict superheavy magnetic monopoles produced in the early universe, none of which have been observed.

#### Inflation as a Proposed Resolution

Inflation is a hypothesized period of accelerated expansion, $\ddot{a} > 0$, driven by a scalar field with near-constant potential energy. The condition for inflation is:

$$\rho + \frac{3p}{c^2} < 0$$

A sufficient duration of inflation, about $N \gtrsim 60$ $e$-folds, would:

- Stretch initially causally connected regions to super-horizon scales (horizon problem).
- Drive $\Omega \to 1$ exponentially (flatness problem).
- Dilute any relic monopoles (monopole problem).
- Convert quantum fluctuations into nearly scale-invariant density perturbations, matching the observed spectral index $n_s \approx 0.965$.

[Inference: Inflation is supported by the observed near-scale-invariant, adiabatic, Gaussian perturbations and flatness, but the inflaton field and the specific model have not been directly identified, and alternatives have been proposed.]

### Dark Matter and Dark Energy in the Model

#### Cold Dark Matter

Evidence includes galaxy rotation curves, gravitational lensing, the CMB peak structure, and structure-formation simulations. Dark matter must be non-baryonic (BBN and CMB constrain $\Omega_b \approx 0.049$) and effectively collisionless and non-relativistic at the time of structure formation. Its particle identity is unknown; candidates include WIMPs, axions, and sterile neutrinos.

#### Dark Energy

The simplest description is a cosmological constant with $w = -1$. Observations are consistent with $w \approx -1$ within uncertainties, but some recent analyses (for example, combined BAO and supernova datasets) have reported mild hints of time-varying dark energy. [Unverified: these hints have not reached consensus-level statistical significance and depend on dataset combinations.]

### Worked Numerical Examples

#### Example 1: Matter–Radiation Equality Redshift

Setting $\Omega_r a^{-4} = \Omega_m a^{-3}$:

$$1 + z_{eq} = \frac{\Omega_m}{\Omega_r}$$

With $\Omega_m = 0.31$ and $\Omega_r = 9.1 \times 10^{-5}$ (including neutrinos):

$$1 + z_{eq} = \frac{0.31}{9.1 \times 10^{-5}} \approx 3400$$

**Output**

$$z_{eq} \approx 3400$$

#### Example 2: Redshift of Matter–Dark Energy Equality

$$\Omega_m (1+z)^3 = \Omega_\Lambda \implies (1+z)^3 = \frac{0.69}{0.31} = 2.226$$



$$1 + z = 2.226^{1/3} \approx 1.305$$

**Output**

$$z \approx 0.30$$

Acceleration of expansion begins slightly earlier, at $z \approx 0.6$–$0.7$, when $q(z) = 0$.

#### Example 3: Photon Number Density Today

For a blackbody at $T_0 = 2.7255$ K:

$$n_\gamma = \frac{2\zeta(3)}{\pi^2}\left(\frac{k_B T_0}{\hbar c}\right)^3 \approx 411 \text{ cm}^{-3}$$

Using $\Omega_b h^2 \approx 0.0224$, the baryon-to-photon ratio is:

$$\eta = \frac{n_b}{n_\gamma} \approx 6.1 \times 10^{-10}$$

**Output**

$$n_\gamma \approx 411 \text{ cm}^{-3}, \quad \eta \approx 6.1 \times 10^{-10}$$

#### Example 4: Scale Factor Evolution in a Matter-Dominated Flat Universe

From $a \propto t^{2/3}$ and $H = \dot{a}/a = 2/(3t)$:

$$t = \frac{2}{3H}$$

At $z = 1$ ($a = 0.5$), with pure matter dominance and $H_0 = 70$ km/s/Mpc:

$$H(z=1) = H_0 (1+z)^{3/2} = 70 \times 2.83 \approx 198 \text{ km/s/Mpc}$$

**Output**

$$H(z=1) \approx 198 \text{ km/s/Mpc} \quad (\text{matter-only approximation})$$

With dark energy included, $H(z=1) \approx 120 \text{ km/s/Mpc}$ for $\Omega_m = 0.31$, $\Omega_\Lambda = 0.69$, illustrating how the dark-energy component slows the growth of $H$ with redshift.

### Numerical Computation Example

The following Python script integrates the Friedmann equation to compute cosmic age and the Hubble parameter as a function of redshift. Behavior of numerical integrators may vary with library version and tolerances.

```python
import numpy as np
from scipy.integrate import quad

# Cosmological parameters (approximate Planck 2018 values)
H0 = 67.7            # km/s/Mpc
Omega_m = 0.31
Omega_r = 9.1e-5
Omega_L = 1.0 - Omega_m - Omega_r   # enforce flatness

# Convert 1/H0 to Gyr
H0_inv_Gyr = 977.8 / H0

def E(a):
    """Dimensionless Hubble parameter H(a)/H0 for a flat universe."""
    return np.sqrt(Omega_r / a**4 + Omega_m / a**3 + Omega_L)

def age_of_universe():
    """Integrate dt = da / (a H) from a=0 to a=1."""
    integrand = lambda a: 1.0 / (a * E(a))
    result, _ = quad(integrand, 1e-8, 1.0)
    return H0_inv_Gyr * result

def hubble_at_z(z):
    a = 1.0 / (1.0 + z)
    return H0 * E(a)

def lookback_time(z):
    a_emit = 1.0 / (1.0 + z)
    integrand = lambda a: 1.0 / (a * E(a))
    result, _ = quad(integrand, a_emit, 1.0)
    return H0_inv_Gyr * result

if __name__ == "__main__":
    print(f"Age of universe: {age_of_universe():.2f} Gyr")
    for z in [0.5, 1.0, 2.0, 1090.0]:
        print(f"z = {z:7.1f}:  H = {hubble_at_z(z):9.2f} km/s/Mpc,  "
              f"lookback = {lookback_time(z):6.2f} Gyr")
```

**Output** (approximate)



```
Age of universe: 13.79 Gyr
z =     0.5:  H =     85.47 km/s/Mpc,  lookback =   5.16 Gyr
z =     1.0:  H =    120.83 km/s/Mpc,  lookback =   7.70 Gyr
z =     2.0:  H =    203.71 km/s/Mpc,  lookback =  10.32 Gyr
z =  1090.0:  H = 1.33e+06 km/s/Mpc,  lookback =  13.79 Gyr
```

### Scale Factor Evolution

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 400" role="img" aria-label="Schematic of scale factor versus time for different cosmological eras">
<title>Scale Factor Evolution by Era (svg_diagram)</title>
<rect x="0" y="0" width="640" height="400" fill="#ffffff" stroke="#cccccc" />
<text x="320" y="28" text-anchor="middle" font-family="sans-serif" font-size="16" font-weight="bold">Scale Factor a(t) by Era (svg_diagram)</text>
<line x1="70" y1="340" x2="600" y2="340" stroke="#000" stroke-width="2" />
<line x1="70" y1="340" x2="70" y2="55" stroke="#000" stroke-width="2" />
<text x="335" y="385" text-anchor="middle" font-family="sans-serif" font-size="13">Cosmic time t (not to scale)</text>
<text x="22" y="200" text-anchor="middle" font-family="sans-serif" font-size="13" transform="rotate(-90 22 200)">Scale factor a(t)</text>
<path d="M 70 340 Q 110 300 160 270" fill="none" stroke="#c0392b" stroke-width="3" />
<path d="M 160 270 Q 250 190 350 165" fill="none" stroke="#2874a6" stroke-width="3" />
<path d="M 350 165 Q 440 140 490 105 T 590 60" fill="none" stroke="#1e8449" stroke-width="3" />
<line x1="160" y1="340" x2="160" y2="270" stroke="#888" stroke-dasharray="4,4" />
<line x1="350" y1="340" x2="350" y2="165" stroke="#888" stroke-dasharray="4,4" />
<text x="115" y="325" text-anchor="middle" font-family="sans-serif" font-size="12" fill="#c0392b">Radiation</text>
<text x="115" y="311" text-anchor="middle" font-family="sans-serif" font-size="12" fill="#c0392b">a ∝ t^(1/2)</text>
<text x="255" y="235" text-anchor="middle" font-family="sans-serif" font-size="12" fill="#2874a6">Matter</text>
<text x="255" y="221" text-anchor="middle" font-family="sans-serif" font-size="12" fill="#2874a6">a ∝ t^(2/3)</text>
<text x="510" y="140" text-anchor="middle" font-family="sans-serif" font-size="12" fill="#1e8449">Dark energy</text>
<text x="510" y="126" text-anchor="middle" font-family="sans-serif" font-size="12" fill="#1e8449">a ∝ e^(Ht)</text>
<text x="160" y="358" text-anchor="middle" font-family="sans-serif" font-size="11">Equality (z≈3400)</text>
<text x="350" y="358" text-anchor="middle" font-family="sans-serif" font-size="11">Λ takeover (z≈0.3)</text>
</svg>

### Common Misconceptions

| Misconception | Correction |
| --- | --- |
| The Big Bang was an explosion at a point in space | It was an expansion of all space; there is no center in the observable universe |
| Galaxies fly apart through space | Galaxies are carried apart by the expansion of space; peculiar velocities are small by comparison |
| The universe expands into something | The FLRW model requires no external space; expansion is intrinsic |
| Bound systems (atoms, galaxies) expand | Local gravitational and electromagnetic binding overwhelms the cosmic expansion |
| The Big Bang explains the origin of the universe | The model describes evolution from an early hot state; the origin (or lack of one) is outside its scope |
| Recession faster than $c$ violates relativity | Special relativity limits local motion; the expansion of space is not bound by this limit |

### Limitations and Open Questions

- **Initial singularity**: Classical general relativity predicts $a \to 0$ with diverging density; a quantum-gravity theory is required for the earliest moments.
- **Nature of dark matter and dark energy**: Together they account for about 95% of the energy budget, yet neither is understood at a fundamental level.
- **Baryon asymmetry**: The excess of matter over antimatter ($\eta \approx 6 \times 10^{-10}$) requires baryogenesis satisfying the Sakharov conditions; the mechanism is unknown.
- **Hubble tension**: The disagreement between early- and late-universe values of $H_0$ persists at roughly the $4\text{–}5\sigma$ level in some analyses.
- **Cosmological lithium problem**: Predicted $^7\text{Li}$ exceeds observations.
- **Cosmological constant problem**: Quantum field theory estimates of vacuum energy exceed the observed $\Lambda$ by many orders of magnitude (up to $\sim 10^{120}$ in naive estimates).
- **Inflation**: The specific mechanism, inflaton field, and initial conditions remain undetermined.

### Conclusion

The Big Bang model, in its $\Lambda$CDM form, provides a quantitatively successful account of cosmic expansion, the CMB, light-element abundances, and the growth of large-scale structure using roughly six free parameters. Its predictions have been tested across more than ten orders of magnitude in time and remain consistent with high-precision data. At the same time, its dominant ingredients (dark matter, dark energy, and the physics of inflation) are inferred from gravitational effects rather than directly detected, and tensions such as the Hubble discrepancy indicate that the model may require refinement.

**Related Topics**

- Cosmic Inflation and Slow-Roll Dynamics
- The Cosmic Microwave Background Power Spectrum
- Big Bang Nucleosynthesis and Light-Element Abundances
- Dark Matter Evidence and Candidates
- Dark Energy and the Cosmological Constant
- Baryon Acoustic Oscillations
- Structure Formation and the Matter Power Spectrum
- The Hubble Tension
- Reionization and the First Stars
- Alternatives and Extensions to $\Lambda$CDM