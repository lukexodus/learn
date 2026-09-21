## Interest Rate Smile Modeling

### Overview

Interest rate smile modeling addresses the empirical fact that implied volatilities for interest rate options (caps/floors, swaptions) vary systematically across strike, rather than being flat as assumed under the standard lognormal (Black-76) model. This volatility surface — smile or skew — must be captured by any model used to price and risk-manage rate derivatives consistently across strikes, and it directly conflicts with the flat-volatility assumption embedded in the basic HJM and standard LIBOR market model (LMM) framework covered elsewhere in this chapter.

### The Smile Phenomenon in Rates Markets

**Key Points**

- Black-76 assumes forward rates are lognormal, implying a single volatility per maturity/tenor regardless of strike
- Empirically, implied volatilities from cap/floor and swaption markets show pronounced skew and curvature across strike
- The skew shape and steepness vary by currency, maturity, and market regime (e.g., steep skew in low-rate/negative-rate environments)
- Pre-2008, skew was moderate; post-crisis, extreme low-strike behavior (rates approaching or going negative) forced the market toward shifted-lognormal and free-boundary SABR-type models

The smile arises from several economically grounded sources: fat-tailed rate distributions relative to lognormal, stochastic volatility of rates themselves, jump risk around policy announcements, and supply/demand imbalances from hedging flows (e.g., mortgage convexity hedging).

### Why the Standard HJM/LMM Framework Fails to Capture Smile

The classical HJM framework with deterministic volatility functions $\sigma(t,T)$ produces lognormal (or Gaussian, depending on specification) forward rate dynamics, which by construction generates a flat implied volatility surface. Similarly, the standard lognormal LMM (BGM model) prices caplets consistently with Black's formula only under a single volatility per caplet — it cannot simultaneously fit the whole strike dimension without extension.

To capture smile, three broad extension strategies exist within or alongside the HJM/market model framework:

1. **Local volatility extensions** — CEV-type or displaced-diffusion dynamics where volatility is a deterministic function of the rate level
2. **Stochastic volatility extensions** — volatility itself follows a stochastic process (SABR, Heston-type, Wu-Zhang)
3. **Jump-diffusion extensions** — adding jumps to the forward rate or LIBOR dynamics

### Displaced-Diffusion and CEV Models

**Displaced-Diffusion LMM**

The forward rate process is shifted before applying lognormal dynamics:

$$d(F_i(t) + \alpha_i) = \sigma_i (F_i(t) + \alpha_i)\, dW_i(t)$$

where $\alpha_i$ is a displacement (shift) parameter. This is equivalent to modeling $F_i(t) + \alpha_i$ as lognormal, which:

- Produces a skew (negative for $\alpha_i > 0$) since the effective volatility of $F_i$ becomes $\sigma_i (F_i + \alpha_i)/F_i$
- Allows negative rates when $\alpha_i$ is chosen large enough (critical post-2008/2015 in EUR, JPY, CHF markets)
- Retains closed-form Black-like pricing with a shifted strike: $\text{Black}(F_i + \alpha_i, K + \alpha_i, \sigma_i, T_i)$

**CEV (Constant Elasticity of Variance) Model**

$$dF_i(t) = \sigma_i F_i(t)^\beta\, dW_i(t), \quad 0 \le \beta \le 1$$

- $\beta = 1$ recovers lognormal (Black); $\beta = 0$ recovers normal (Bachelier)
- $\beta < 1$ generates a downward-sloping skew (volatility rises as rate falls)
- Semi-closed-form pricing available via the noncentral chi-squared distribution, but calibration to a full smile (not just skew) is limited by the single free parameter $\beta$ per rate

**[Inference]** In practice, both displaced-diffusion and CEV alone are typically insufficient to fit market curvature (wings) accurately across the full strike range; they are often used as a base local-volatility layer under a stochastic volatility overlay.

### The SABR Model

The SABR (Stochastic Alpha Beta Rho) model, introduced by Hagan, Kumar, Lesniewski, and Woodward (2002), is the dominant industry standard for smile interpolation on individual forward rates (caplets, swaption underlyings).

**Dynamics**

$$dF(t) = \sigma(t)\, F(t)^\beta\, dW_1(t)$$



$$d\sigma(t) = \nu\, \sigma(t)\, dW_2(t)$$



$$dW_1(t)\, dW_2(t) = \rho\, dt$$

- $F(t)$: forward rate
- $\sigma(t)$: stochastic volatility (initial level $\alpha = \sigma(0)$)
- $\beta$: CEV-type exponent controlling backbone shape (skew of the underlying ATM level dynamics)
- $\nu$: volatility of volatility ("vol-of-vol"), controlling smile curvature
- $\rho$: correlation between rate and volatility, controlling smile skew/slope

**Hagan's Asymptotic Implied Volatility Formula**

For strike $K$ and forward $F$, Hagan's approximation gives the Black implied volatility:

$$\sigma_B(K,F) = \frac{\alpha}{(FK)^{(1-\beta)/2}\left[1 + \frac{(1-\beta)^2}{24}\ln^2(F/K) + \frac{(1-\beta)^4}{1920}\ln^4(F/K)\right]} \cdot \frac{z}{x(z)} \cdot \left[1 + \left(\frac{(1-\beta)^2\alpha^2}{24(FK)^{1-\beta}} + \frac{\rho\beta\nu\alpha}{4(FK)^{(1-\beta)/2}} + \frac{2-3\rho^2}{24}\nu^2\right)T\right]$$

where

$$z = \frac{\nu}{\alpha}(FK)^{(1-\beta)/2}\ln(F/K), \qquad x(z) = \ln\left(\frac{\sqrt{1-2\rho z + z^2} + z - \rho}{1-\rho}\right)$$

For the at-the-money case ($F = K$), this simplifies to:

$$\sigma_{ATM} = \frac{\alpha}{F^{1-\beta}}\left[1 + \left(\frac{(1-\beta)^2\alpha^2}{24F^{2-2\beta}} + \frac{\rho\beta\nu\alpha}{4F^{1-\beta}} + \frac{2-3\rho^2}{24}\nu^2\right)T\right]$$

**Parameter Roles (Calibration Intuition)**

- $\alpha$: sets the overall ATM volatility level
- $\beta$: typically fixed exogenously (0.5 for rates is common, or estimated from historical rate/vol regression); jointly with $\alpha$ determines the backbone
- $\rho$: primarily controls the skew (slope of smile) — negative $\rho$ produces the typical downward skew seen in rates
- $\nu$: primarily controls the smile curvature (convexity/wings)

**[Unverified]** The common practice of fixing $\beta$ a priori (e.g., $\beta = 0.5$) rather than calibrating it jointly is a pragmatic choice since $\alpha$ and $\beta$ are poorly separately identified from a single smile snapshot; conventions vary by desk and currency.

### SABR Extensions for Low/Negative Rates

The original SABR formula breaks down (or becomes undefined) as $F \to 0$ or under negative rates because of the $F^\beta$ term. Two principal fixes:

1. **Shifted SABR** — apply a shift $s$ so the dynamics operate on $F + s$:



   $$dF(t) = \sigma(t)(F(t)+s)^\beta\, dW_1(t)$$

   This is the most widely used practical fix, directly analogous to displaced-diffusion LMM.
2. **Free (Normal) SABR / Zero-Boundary SABR** — use $\beta = 0$ (normal backbone) which is naturally well-defined for negative rates without a shift, since $F^0$-type dynamics don't restrict sign. Hagan et al. and subsequent authors (Antonov, Konikov, Spector) developed "free boundary SABR" formulations with absorbing/reflecting conditions at zero to handle the normal/CEV boundary rigorously.

**[Inference]** Post-2015, as EUR and JPY short rates went negative, shifted SABR with $\beta$ close to 0 or normal-SABR variants became the market standard for those currencies, while USD markets historically retained higher $\beta$ conventions closer to lognormal.

### SABR and the HJM/LMM Framework

SABR itself models a *single* forward rate's marginal distribution (it is not, by itself, a full term-structure or multi-rate model). To integrate SABR-style smile dynamics into an arbitrage-free multi-factor framework:

- **SABR-LMM**: each forward LIBOR rate $F_i(t)$ is given its own SABR dynamics, with a stochastic volatility process $\sigma_i(t)$, requiring careful specification of correlations between different $F_i$, between different $\sigma_i$, and cross rate-volatility correlations. This significantly increases the factor count and calibration complexity (Rebonato's SABR-LMM, Henry-Labordère's approach).
- **Markov-functional models**: an alternative that directly specifies terminal rate distributions consistent with the observed smile, then constructs a low-dimensional Markov process to match those marginals, avoiding full stochastic-volatility state-space explosion.
- **HJM with stochastic volatility**: the instantaneous forward rate volatility function $\sigma(t,T)$ is itself driven by an auxiliary stochastic factor (e.g., CIR-type variance process), producing smile-consistent dynamics for the whole curve rather than rate-by-rate.

### Alternative Smile Frameworks

**Local Volatility (Dupire-style, adapted to rates)**

A deterministic function $\sigma_{loc}(F,t)$ is backed out from the market smile surface such that a one-factor diffusion exactly reproduces all quoted European option prices at time $t$. Limitations: the forward smile dynamics implied by local volatility are typically inconsistent with observed dynamics (smile flattens over time unrealistically), making it poor for exotics sensitive to forward smile (e.g., Bermudan swaptions, CMS options).

**Stochastic-Volatility Jump-Diffusion (SVJD)**

Adds jump components to capture short-dated smile steepness (particularly around central bank meetings) that pure diffusion stochastic volatility struggles to fit without unrealistically high vol-of-vol.

**Quadratic Gaussian / Cheyette-type Models**

Extensions of Gaussian HJM (Cheyette model — a low-dimensional Markovian reformulation of HJM) with quadratic or local-volatility state-dependence to generate smile while retaining the computational tractability of Markovian short-rate-type models.

### Calibration Workflow (Practical)

1. Collect market quotes: cap/floor volatilities (or prices) across strikes and maturities; swaption volatilities across strike, expiry, and tenor
2. Strip caplet volatilities from cap prices (bootstrapping, since caps are sums of caplets)
3. For each caplet/swaption expiry-tenor pair, calibrate SABR parameters $(\alpha, \rho, \nu)$ (with $\beta$ fixed or slowly varying) by least-squares fit to Hagan's formula against market-implied vols
4. Interpolate/extrapolate smile parameters across the expiry-tenor grid (often with parametric or spline smoothing to avoid arbitrage in the wings)
5. Embed the calibrated smile into the pricing model (SABR-LMM, local-vol overlay, or Markov-functional mapping) for exotic pricing
6. Validate: recover vanilla market prices to within tolerance; check absence of static arbitrage (calendar spread, butterfly) in the fitted surface

### Arbitrage Considerations in Smile Construction

**Key Points**

- Butterfly arbitrage: the implied density $\partial^2 C/\partial K^2$ must remain non-negative — naive polynomial or spline fits to implied vol can violate this in the wings
- Calendar spread arbitrage: total variance $\sigma^2(K,T) \cdot T$ must be non-decreasing in $T$ for fixed strike (or moneyness under some conventions)
- Hagan's original SABR formula is an asymptotic expansion and can produce negative implied densities for extreme strikes/long maturities, especially at high $\nu$ or extreme $\rho$ — practitioners apply arbitrage-checked alternatives (e.g., Andreasen-Huge stochastic collocation, or Antonov's exact/mixture SABR formulas) for robustness

### Illustration: Smile Shape Mechanics

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 420">
<text x="350" y="24" font-size="16" text-anchor="middle" font-family="sans-serif" font-weight="bold">SABR Parameter Effects on Implied Vol Smile (svg_diagram)</text>
<line x1="60" y1="370" x2="650" y2="370" stroke="#333" stroke-width="1.5" />
<line x1="60" y1="60" x2="60" y2="370" stroke="#333" stroke-width="1.5" />
<text x="355" y="400" font-size="13" text-anchor="middle" font-family="sans-serif">Strike (K)</text>
<text x="25" y="215" font-size="13" text-anchor="middle" font-family="sans-serif" transform="rotate(-90 25 215)">Implied Vol</text>
<line x1="355" y1="60" x2="355" y2="370" stroke="#999" stroke-width="1" stroke-dasharray="4,3" />
<text x="355" y="385" font-size="11" text-anchor="middle" font-family="sans-serif">ATM (F)</text>
<path d="M 80 220 Q 355 150 630 220" stroke="#1f77b4" stroke-width="2.5" fill="none" />
<text x="640" y="220" font-size="11" font-family="sans-serif" fill="#1f77b4">base (ρ=0)</text>
<path d="M 80 130 Q 355 150 630 300" stroke="#d62728" stroke-width="2.5" fill="none" />
<text x="640" y="300" font-size="11" font-family="sans-serif" fill="#d62728">ρ &lt; 0 (skew)</text>
<path d="M 80 260 Q 355 100 630 260" stroke="#2ca02c" stroke-width="2.5" fill="none" />
<text x="640" y="260" font-size="11" font-family="sans-serif" fill="#2ca02c">high ν (curvature)</text>

<text x="80" y="410" font-size="11" font-family="sans-serif">Low K</text>

<text x="610" y="410" font-size="11" font-family="sans-serif">High K</text>

</svg>

### Model Selection Summary

| Model | Handles Negative Rates | Fits Skew | Fits Curvature | Full Term Structure | Computational Cost |
| --- | --- | --- | --- | --- | --- |
| Black-76 (flat vol) | No | No | No | No | Very Low |
| Displaced-Diffusion LMM | Yes (with shift) | Yes | Limited | Yes | Low |
| CEV | Only with shift | Yes | Limited | No (single rate) | Low |
| SABR | With shift/free-boundary variants | Yes | Yes | No (single rate) | Low-Medium |
| SABR-LMM | Yes | Yes | Yes | Yes | High |
| Local Volatility | Yes | Yes | Yes | Depends | Medium |
| Markov-Functional | Yes | Yes | Yes | Yes | Medium-High |

### Worked Example: SABR ATM Volatility Sensitivity

Consider a 5-year forward swap rate $F = 3.00\%$, calibrated SABR parameters $\alpha = 0.25$, $\beta = 0.5$, $\rho = -0.30$, $\nu = 0.40$, $T = 5$.

Using the ATM formula:

$$\sigma_{ATM} = \frac{\alpha}{F^{1-\beta}}\left[1 + \left(\frac{(1-\beta)^2\alpha^2}{24F^{2-2\beta}} + \frac{\rho\beta\nu\alpha}{4F^{1-\beta}} + \frac{2-3\rho^2}{24}\nu^2\right)T\right]$$

With $F^{1-\beta} = 0.03^{0.5} \approx 0.1732$:

- Base term: $0.25 / 0.1732 \approx 1.4434$
- Correction bracket terms (illustrative order of magnitude): the $\rho\beta\nu\alpha$ cross-term is negative (since $\rho < 0$), pulling ATM vol down slightly relative to the pure $\alpha/F^{1-\beta}$ base, while the $\nu^2$ term pushes it up

**[Inference]** This example is illustrative of the mechanics rather than a market-calibrated quote; actual $\alpha$ values are jointly solved with $\beta$ against a real market smile via numerical optimization, not selected independently.

### Related Topics

- SABR-LMM joint calibration and correlation structure
- Markov-functional model construction for Bermudan swaptions
- CMS convexity adjustments under smile-consistent models
- Arbitrage-free SABR (Andreasen-Huge, Antonov exact formulas)
- Negative rates: shifted vs. free-boundary model conventions
- Volatility cube construction (expiry × tenor × strike) for swaptions
- Forward smile dynamics and their impact on exotic rate derivatives pricing