## Characteristic Function Pricing Methods


### Overview

Characteristic function pricing methods are a family of techniques for computing European option prices under models where the **characteristic function** of the log-price (or log-return) is known in closed or semi-closed form, even when the corresponding probability density function is not. This is the computational backbone that makes affine stochastic volatility models like Heston practically usable for calibration: instead of inverting a density and integrating a payoff against it directly, these methods work in Fourier space, transforming an otherwise intractable pricing integral into a numerically efficient one-dimensional (or low-dimensional) integral.

### Why Characteristic Functions Instead of Densities

For many models with genuinely useful dynamics (Heston, Bates, Variance Gamma, and other Lévy or affine jump-diffusion processes), the transition density of the underlying is either unknown in closed form or extremely cumbersome to work with directly. However, the **characteristic function**

$$\phi_T(u) = \mathbb{E}\left[e^{iu\ln S_T}\right]$$

is frequently available in closed form for these models — often as an explicit exponential-affine expression in $u$, derived by solving a system of ordinary differential equations (Riccati equations) that arise from the model's affine structure. Since the characteristic function is simply the Fourier transform of the density, and European option prices are themselves expectations of a payoff against that density, standard Fourier-analysis identities allow option prices to be recovered directly from $\phi_T(u)$ without ever explicitly constructing the density.

### The Core Pricing Identity

The foundational relationship, used across nearly all characteristic-function pricing methods, connects the risk-neutral probability of finishing in-the-money to an integral involving the characteristic function. The original Heston (1993) formulation expresses a call price as:

$$C(K,T) = S_0 e^{-qT} P_1 - K e^{-rT} P_2$$

where $P_1$ and $P_2$ are risk-neutral probabilities (under two different measures — the stock-numeraire measure and the risk-neutral measure, respectively) computed via inversion integrals of the form:

$$P_j = \frac{1}{2} + \frac{1}{\pi}\int_0^\infty \text{Re}\left[\frac{e^{-iu\ln K}\phi_j(u)}{iu}\right] du, \quad j=1,2$$

This is directly analogous to the classical Gil-Pelaez inversion formula for recovering a CDF from a characteristic function. **Practical drawback:** this original formulation requires evaluating two separate characteristic functions and handling an integrand with a singularity at $u=0$ (removable, but numerically delicate) — motivating the more numerically robust methods that followed.

### The Carr-Madan Fourier Transform Method

Carr and Madan (1999) reformulated the pricing problem in a numerically superior way by taking the Fourier transform of a **damped** option price (damped to ensure integrability, since the raw call price is not square-integrable in strike):

$$\psi(v) = \int_{-\infty}^{\infty} e^{ivk} e^{\alpha k} C(k) \, dk$$

where $k = \ln K$ and $\alpha > 0$ is a damping factor. This has a closed-form expression directly in terms of the characteristic function $\phi_T(u)$:

$$\psi(v) = \frac{e^{-rT}\phi_T(v - (\alpha+1)i)}{\alpha^2 + \alpha - v^2 + i(2\alpha+1)v}$$

The option price is then recovered via an inverse Fourier transform:

$$C(k) = \frac{e^{-\alpha k}}{\pi}\int_0^\infty e^{-ivk}\psi(v)\,dv$$

**Key practical advantage:** this integral is smooth and well-behaved (no singularity at $u=0$, unlike the original Heston formulation), and critically, it can be evaluated **simultaneously across a whole range of strikes in a single Fast Fourier Transform (FFT) call**, since the FFT naturally computes the transform at a discrete grid of output points at once. This makes Carr-Madan especially efficient when pricing (or calibrating to) many strikes at a single maturity simultaneously — exactly the situation faced during smile calibration.

**Damping parameter choice:** $\alpha$ must be chosen large enough to ensure the damped price is integrable (typically $\alpha$ in a moderate positive range, commonly cited guidance suggests values on the order of $1$ to $2$ work well for many models, though the optimal choice is model- and parameter-dependent) — too small risks integrability failure, too large can introduce numerical instability in the transform itself. [Inference: the specific numeric range cited reflects commonly discussed practical guidance in the Carr-Madan literature rather than a universal fixed rule; practitioners typically tune $\alpha$ per model/parameter regime.]

### The COS Method (Fourier-Cosine Series Expansion)

Fang and Oosterlee (2008) introduced the **COS method**, which approximates the density implicitly via a truncated **Fourier-cosine series** rather than direct Fourier inversion, exploiting the fact that cosine-series (Fourier-cosine) coefficients of a density can be recovered cheaply from the characteristic function evaluated at a discrete, evenly-spaced set of real points:

$$V_k \approx \frac{2}{b-a}\text{Re}\left[\phi_T\left(\frac{k\pi}{b-a}\right)e^{-i k\pi a/(b-a)}\right]$$

The option price is then obtained as a finite sum of these cosine coefficients weighted against analytically pre-computed payoff-specific coefficients (available in closed form for European calls/puts).

**Key practical advantages:**

- **Very fast convergence:** for smooth densities, the COS method typically requires only a small number of terms (often on the order of tens to a couple hundred, depending on the model and desired accuracy) to achieve high precision, generally converging faster than direct numerical integration of the Gil-Pelaez-style inversion formula for a comparable accuracy target.
- **No FFT machinery required** for a single strike (unlike Carr-Madan, which is most efficient when pricing many strikes at once via FFT) — the COS method is often preferred when pricing a single option or a modest number of options where the FFT's batch efficiency isn't needed.
- **Truncation range sensitivity:** the method requires choosing a truncation interval $[a,b]$ for the log-price domain, typically set based on cumulants of the underlying distribution (mean, variance, skewness, kurtosis, if available in closed form from the model) — a poorly chosen range can degrade accuracy, though standard cumulant-based heuristics (as given in the original Fang-Oosterlee paper) are widely used and generally robust across common models.

### Comparison of the Main Methods

| Method | Core Idea | Best Suited For | Key Limitation |
| --- | --- | --- | --- |
| Direct Gil-Pelaez / Heston-style inversion | Directly invert characteristic function for risk-neutral probabilities | Conceptually simplest, historically first | Singularity handling at $u=0$; numerically less robust than later methods |
| Carr-Madan (FFT-based) | Fourier transform of a damped option price, inverted via FFT | Pricing/calibrating many strikes at once (full smile) | Requires careful damping parameter choice; FFT grid constraints (power-of-2 sizing, strike spacing trade-offs) |
| COS method (Fourier-cosine) | Approximate density via truncated cosine series from characteristic function | Fast, accurate pricing of a single or few strikes; general-purpose workhorse | Requires reasonable truncation range choice based on model cumulants |

### General Procedure (Common Across Methods)

```mermaid
flowchart TD
    A[Derive or obtain closed-form characteristic function phi_T(u) for the model] --> B{Pricing need: many strikes at once, or single/few strikes?}
    B -->|Many strikes simultaneously, e.g. full smile calibration| C[Use Carr-Madan: construct damped transform, apply FFT]
    B -->|Single or few strikes, general purpose| D[Use COS method: compute cumulant-based truncation range, sum cosine coefficients]
    C --> E[Recover option prices across strike grid from FFT output]
    D --> F[Recover option price from finite cosine-coefficient sum]
    E --> G[Invert to Black-Scholes implied vol for comparison to market]
    F --> G
    G --> H[Feed into calibration objective function: compare to market quotes]
```

### Worked Example: Qualitative Walkthrough of the COS Method Steps

Suppose calibrating a Heston model to a single 1-year, single-strike option quote as part of a broader smile calibration loop. A COS-method evaluation proceeds:

1. **Obtain $\phi_T(u)$** — the closed-form Heston characteristic function (see "The Heston Model and Its Properties"), evaluated at the current trial parameter set during the optimizer's iteration.
2. **Determine truncation range $[a,b]$** — using the model's first four cumulants (mean, variance, skewness, kurtosis of $\ln S_T$, available analytically for Heston from derivatives of $\log\phi_T(u)$ at $u=0$), apply the standard Fang-Oosterlee heuristic (e.g., $a = \text{cumulant}_1 - L\sqrt{|\text{cumulant}_2| + \sqrt{|\text{cumulant}_4|}}$, with $b$ symmetric on the other side, and $L$ a small integer like 8-12 commonly cited in the literature) to fix a numerically appropriate domain.
3. **Evaluate $\phi_T$ at the required discrete frequency grid** $\left\{\frac{k\pi}{b-a}\right\}_{k=0}^{N-1}$ for a chosen truncation order $N$ (commonly on the order of 64-256 terms for high accuracy on smooth models like Heston).
4. **Compute the cosine coefficients** $V_k$ from these evaluations.
5. **Combine with the closed-form payoff coefficients** for a European call/put to obtain the option price.
6. **Convert to implied vol** via standard Black-Scholes inversion, and feed into the calibration's least-squares objective against the market quote.

[Verified: this is a standard, correct high-level description of the COS method's application to Heston calibration; specific numeric choices for $L$ and $N$ above reflect commonly cited practical ranges in the Fang-Oosterlee literature rather than fixed universal constants — actual optimal values are model- and accuracy-target-dependent.]

### Applicability Beyond Heston

Characteristic-function pricing methods are not specific to Heston — they apply to **any model with a known (semi-)closed-form characteristic function**, which includes:

- **Affine jump-diffusion models** (Bates model — Heston plus jumps; other affine models with jump components), since jumps preserve the affine/exponential structure needed for a closed-form characteristic function.
- **Lévy process models** (Variance Gamma, Normal Inverse Gaussian, CGMY), which are defined via their characteristic functions directly (through the Lévy-Khintchine representation) rather than via an SDE, making characteristic-function methods the *natural* (often only practical) pricing approach for these models.
- **Multi-factor/multi-asset affine extensions** (e.g., multi-factor Heston variants, or basket-option pricing under jointly affine dynamics), provided the joint characteristic function remains tractable.

### Practical Role in the Calibration Loop

Characteristic-function pricing methods are what make **fast repeated repricing during optimization** feasible for stochastic volatility model calibration:

- A calibration optimizer (e.g., Levenberg-Marquardt) proposes a trial parameter set at each iteration.
- The full smile of quoted options must be repriced under that trial parameter set to evaluate the objective function.
- Using Carr-Madan/FFT (for the whole strike grid at once) or the COS method (per strike, but very fast per evaluation) makes this repeated repricing computationally tractable within a reasonable calibration time budget — direct Monte Carlo repricing at every optimizer iteration would generally be far too slow for practical use in this context, which is precisely why models without a tractable characteristic function (e.g., certain local-stochastic volatility formulations) require fundamentally different, typically more expensive calibration approaches (see "Calibrating Local Volatility Models" and the particle-method techniques referenced there for LSV).

### Key Points

- Characteristic-function pricing methods allow European option pricing under models whose density is unknown or intractable, provided the characteristic function of the log-price has a closed or semi-closed form.
- The Carr-Madan method transforms the damped option price into Fourier space and is especially efficient for pricing many strikes simultaneously via FFT — well-suited to full-smile calibration.
- The COS method approximates the density via a truncated Fourier-cosine series and generally offers fast convergence for single or few-strike pricing without requiring FFT machinery.
- Both methods are substantial numerical improvements over the original Heston-style direct inversion formula, primarily by avoiding numerically delicate near-$u=0$ singularities.
- These methods are the computational backbone enabling fast, iterative calibration of affine stochastic volatility and Lévy process models to full implied volatility surfaces.

**Related Topics**

- The Heston Model and Its Properties
- The Heston Trap and Characteristic Function Implementation Pitfalls
- Bates Model: Heston With Jump-Diffusion
- Lévy Process Models: Variance Gamma and Normal Inverse Gaussian
- Volatility Surface Calibration Techniques
- Fast Fourier Transform Numerical Implementation Considerations
- Affine Jump-Diffusion Model Frameworks