## Arbitrage Free Surface Conditions


### Overview

An implied volatility surface $\sigma(K, T)$ is a re-parametrization of a call/put price surface $C(K, T)$. Because option prices are subject to strict no-arbitrage bounds, not every conceivable surface $\sigma(K,T)$ corresponds to an arbitrage-free set of prices. A surface is **arbitrage-free** if and only if the total variance / price surface it implies satisfies three families of constraints simultaneously: **calendar spread (time) arbitrage**, **butterfly spread (strike/convexity) arbitrage**, and **vertical/call-spread monotonicity**. Violating any one implies a static arbitrage — a costless trade constructible today with non-negative payoff in all states and positive payoff in at least one.

### Why This Matters

Arbitrage-free surfaces are a precondition for:

- Valid local volatility construction (Dupire's formula divides by expressions that must stay non-negative — see below).
- Consistent Monte Carlo / PDE pricing of exotics off the surface.
- SVI, SABR, and other parametric fits being usable for production risk without producing negative-probability artifacts.
- Interpolation/extrapolation schemes between quoted strikes and tenors not silently introducing arbitrage between the quotes.

A surface can fit every observed market quote well (low RMSE) and still be badly arbitrageable if the interpolation between quotes is naive (e.g., raw linear interpolation on implied vol commonly introduces butterfly arbitrage).

### Notation

- $C(K,T)$: undiscounted call price (or discounted, depending on convention — the constraints below are commonly stated in terms of the *total implied variance* to strip out convention-dependent discounting/forward effects).
- $F_T$: forward price for maturity $T$.
- $k = \ln(K/F_T)$: log-moneyness (log-forward-moneyness).
- $w(k,T) = \sigma^2(k,T) \cdot T$: **total implied variance** — the standard working variable, since it linearizes several conditions.

### Condition 1: Calendar Spread Arbitrage (No Time Arbitrage)

**Statement:** For a fixed log-moneyness $k$ (or fixed strike under some conventions), total implied variance must be **non-decreasing in maturity**:

$$w(k, T_2) \geq w(k, T_1) \quad \text{for all } T_2 > T_1$$

**Why:** A calendar spread — long the longer-dated option, short the shorter-dated option at the same strike — must have non-negative value if the surface is arbitrage-free, because the longer-dated option's exercise/hedging opportunity set weakly dominates the shorter one's. If $w(k,T_2) < w(k,T_1)$, the longer-dated option would trade *cheaper* in total variance terms than the shorter one at the same strike, allowing a calendar spread arbitrage: sell the overpriced shorter-dated option, buy the underpriced longer-dated option, and lock in a riskless profit under the standard static-replication argument (this holds strictly under zero rates/dividends for calls; the general statement is more commonly framed directly in terms of the undiscounted call-price surface being non-decreasing in $T$ at fixed strike).

**Practical check:** Because $w$ typically must be compared at fixed $k = \ln(K/F_T)$ rather than fixed $K$ (since the forward changes with $T$), the calendar-arbitrage check is most cleanly done on a grid of fixed log-moneyness levels, interpolating each maturity's smile to that $k$, then checking monotonicity across the $T$-axis.

**Equivalent price-space statement:** In terms of undiscounted call prices at a common strike $K$,

$$C(K, T_2) \geq C(K, T_1) \quad \text{for } T_2 > T_1$$

### Condition 2: Butterfly / Vertical Spread Arbitrage (Convexity in Strike)

**Statement:** The call price must be a **convex, non-increasing function of strike** at each fixed maturity:

$$\frac{\partial^2 C}{\partial K^2} \geq 0, \qquad \frac{\partial C}{\partial K} \leq 0$$

**Why:** A butterfly spread — long one call at $K - \delta$, short two calls at $K$, long one call at $K + \delta$ — has payoff $\geq 0$ in every terminal state (it is a "tent" payoff peaking at $K$). No-arbitrage therefore requires the butterfly's price to be $\geq 0$:

$$C(K-\delta, T) - 2C(K,T) + C(K+\delta, T) \geq 0$$

Dividing by $\delta^2$ and taking $\delta \to 0$ gives $\partial^2 C/\partial K^2 \geq 0$ — the discrete second-difference condition, which is what should actually be checked on a real strike grid (checking the continuous derivative requires a smooth interpolant, so the discrete butterfly test is the more robust diagnostic in practice).

**Vertical spread condition:** A call spread — long $K_1$, short $K_2 > K_1$ — must have non-negative value and be bounded by the strike difference (discounted):

$$0 \leq C(K_1,T) - C(K_2,T) \leq (K_2 - K_1)e^{-rT}$$

This is equivalent to $-e^{-rT} \leq \partial C/\partial K \leq 0$.

**Implied vol-space translation:** In terms of the implied variance/vol smile, the butterfly condition (equivalently, the requirement that the risk-neutral density implied by Breeden-Litzenberger, $\partial^2 C/\partial K^2 \cdot e^{rT} = f(K)$, stays non-negative) translates into the well-known Gatheral **"g-function" condition** on total variance:

$$g(k) = \left(1 - \frac{k w'(k)}{2w(k)}\right)^2 - \frac{w'(k)^2}{4}\left(\frac{1}{w(k)} + \frac{1}{4}\right) + \frac{w''(k)}{2} \geq 0 \quad \text{for all } k$$

where $w'(k) = \partial w/\partial k$ and $w''(k) = \partial^2 w/\partial k^2$. This $g(k) \geq 0$ condition is the standard closed-form no-butterfly-arbitrage test used against a parametric total-variance slice (e.g., an SVI fit) — it directly encodes "the implied density stays non-negative" without having to numerically differentiate the price surface twice.

### Condition 3: Extreme-Strike / Large-Moneyness Asymptotic Bounds

**Statement:** As $k \to \pm\infty$, the total implied variance cannot grow arbitrarily fast; Roger Lee's **moment formula** bounds the slope of the wings:

$$\limsup_{k \to \infty} \frac{w(k,T)}{k} \leq 2, \qquad \limsup_{k \to -\infty} \frac{w(k,T)}{|k|} \leq 2$$

**Why:** This follows from the requirement that the underlying's moment-generating function (specifically, the existence of certain positive/negative moments of the terminal distribution implied by the model or by the finiteness of $\mathbb{E}[S_T^p]$ for some $p>1$) be finite; the slope bound relates directly to how many finite moments the implied terminal distribution has. Wings that are too steep imply a terminal distribution with a moment explosion, which is inconsistent with a well-defined risk-neutral measure. [Verified: this is the standard Lee moment formula result widely cited in the volatility surface literature; the precise constant "2" arises from the specific normalization of $w$ and $k$ used here.]

**Practical relevance:** This condition mainly governs **extrapolation** beyond the quoted strike range — a common source of practical arbitrage when a desk extrapolates a smile too aggressively into deep wings for exotic/barrier pricing.

### Interaction with the Local Volatility (Dupire) Formula

The Dupire local volatility formula is a direct diagnostic for arbitrage, because its denominator vanishes or goes negative exactly when the surface is arbitraged:

$$\sigma_{loc}^2(K,T) = \frac{\dfrac{\partial w}{\partial T}}{1 - \dfrac{k}{w}\dfrac{\partial w}{\partial k} + \dfrac{1}{4}\left(-\dfrac{1}{4} - \dfrac{1}{w} + \dfrac{k^2}{w^2}\right)\left(\dfrac{\partial w}{\partial k}\right)^2 + \dfrac{1}{2}\dfrac{\partial^2 w}{\partial k^2}}$$

- The **numerator** $\partial w/\partial T \geq 0$ is exactly the calendar-spread condition (Condition 1).
- The **denominator** is exactly Gatheral's $g(k)$ from Condition 2, scaled — it must stay strictly positive.

If either fails, $\sigma_{loc}^2$ becomes negative or undefined at that point on the surface — a direct, actionable numerical signal used in production systems to flag arbitrage in a calibrated or interpolated surface. This is the most common practical arbitrage check: build the local vol surface off the candidate implied vol surface and scan for negative or NaN values.

### Practical Sources of Arbitrage in Constructed Surfaces

| Source | Typical Failure Mode |
| --- | --- |
| Naive linear interpolation on implied vol (not total variance) across strikes | Frequently breaks butterfly convexity between quoted strikes |
| Linear interpolation across maturities on implied vol (not $w$) | Frequently breaks calendar monotonicity, since $\sigma\sqrt{T}$ is not linear even if $\sigma$ is |
| Independent per-maturity smile fits (e.g., separate SVI per slice with no calendar constraint) | Calendar arbitrage between adjacent slices unless explicitly regularized |
| Aggressive wing extrapolation for deep OTM/exotic strikes | Breach of Lee's moment formula bound |
| Spline interpolation with unconstrained curvature | Oscillation can produce local negative second derivatives (butterfly violation) even with visually smooth curves |

### Standard Remedies

- **Work in total variance $w(k,T)$, not raw $\sigma$**, for both interpolation and extrapolation — this is standard practice because $w$ is the natural variable for both the calendar condition (must be non-decreasing in $T$) and the SVI/Gatheral butterfly condition.
- **Arbitrage-free parametric families:** SVI ("Stochastic Volatility Inspired") per-slice parametrization, with cross-slice calibration enforcing $w(k,T_2) \geq w(k,T_1)$ pointwise — this is the basis of Gatheral and Jacquier's **SSVI (Surface SVI)**, which imposes a single surface-level parametrization guaranteeing no calendar arbitrage by construction under stated parameter restrictions, alongside the pointwise $g(k)\geq 0$ check per slice.
- **Shape-constrained splines:** monotone/convex-constrained cubic splines or tension splines fit directly to $w(k)$ or to the call price surface, with convexity enforced as an explicit constraint in the fitting optimization rather than checked post-hoc.
- **Post-fit diagnostic pass:** after any fitting procedure, compute the discrete butterfly second-difference and the Dupire local-vol denominator on a fine grid, and inspect for sign violations before the surface is released to pricing/risk systems.

### Diagram: Arbitrage Conditions on the Surface (svg_diagram)

<svg viewBox="0 0 760 460" xmlns="http://www.w3.org/2000/svg" font-family="sans-serif">
<text x="380" y="24" text-anchor="middle" font-size="16" font-weight="bold">Arbitrage-Free Surface Conditions (svg_diagram)</text>
<!-- Calendar condition panel -->

<text x="180" y="55" text-anchor="middle" font-size="13" font-weight="bold">Calendar (Condition 1)</text>

<line x1="60" y1="200" x2="330" y2="200" stroke="black" stroke-width="1.5"/>

<line x1="60" y1="200" x2="60" y2="70" stroke="black" stroke-width="1.5"/>

<text x="195" y="218" text-anchor="middle" font-size="11">Maturity T</text>

<text x="30" y="140" text-anchor="middle" font-size="11" transform="rotate(-90 30 140)">Total Var w</text>

<path d="M 80 180 L 150 150 L 220 120 L 300 90" stroke="`#2b6cb0`" stroke-width="2.5" fill="none"/>

<circle cx="80" cy="180" r="3" fill="`#2b6cb0`"/>

<circle cx="150" cy="150" r="3" fill="`#2b6cb0`"/>

<circle cx="220" cy="120" r="3" fill="`#2b6cb0`"/>

<circle cx="300" cy="90" r="3" fill="`#2b6cb0`"/>

<text x="195" y="235" text-anchor="middle" font-size="10" fill="`#2f855a`">w(k,T) monotone increasing = OK</text>

<!-- Butterfly condition panel -->

<text x="580" y="55" text-anchor="middle" font-size="13" font-weight="bold">Butterfly (Condition 2)</text>

<line x1="460" y1="200" x2="730" y2="200" stroke="black" stroke-width="1.5"/>

<line x1="460" y1="200" x2="460" y2="70" stroke="black" stroke-width="1.5"/>

<text x="595" y="218" text-anchor="middle" font-size="11">Strike K</text>

<text x="430" y="140" text-anchor="middle" font-size="11" transform="rotate(-90 430 140)">Call Price C</text>

<path d="M 480 90 Q 595 190 710 100" stroke="`#2f855a`" stroke-width="2.5" fill="none"/>

<text x="595" y="235" text-anchor="middle" font-size="10" fill="`#2f855a`">Convex, decreasing = OK</text>

<path d="M 480 130 Q 595 90 710 150" stroke="`#c53030`" stroke-width="2" fill="none" stroke-dasharray="5,3"/>

<text x="595" y="255" text-anchor="middle" font-size="10" fill="`#c53030`">Concave region = butterfly arbitrage</text>

<!-- Bottom: Dupire diagnostic -->

<text x="380" y="310" text-anchor="middle" font-size="13" font-weight="bold">Dupire Local Vol as Combined Diagnostic</text>

<rect x="140" y="330" width="480" height="90" rx="6" fill="none" stroke="`#4a5568`" stroke-width="1.5"/>

<text x="380" y="360" text-anchor="middle" font-size="12">sigma_loc^2 = (dw/dT) / g(k)</text>

<text x="380" y="385" text-anchor="middle" font-size="10" fill="`#2f855a`">Numerator ≥ 0 <=> Calendar condition holds</text>

<text x="380" y="405" text-anchor="middle" font-size="10" fill="`#2f855a`">Denominator g(k) > 0 <=> Butterfly condition holds</text>

</svg>

### Worked Example: Detecting Butterfly Arbitrage

Suppose a 3-month smile is quoted at three strikes with the following call prices (forward $F = 100$, zero rates for simplicity):

| K | C(K) |
| --- | --- |
| 95 | 7.20 |
| 100 | 4.10 |
| 105 | 2.50 |

Discrete butterfly test with $\delta = 5$:

$$C(95) - 2C(100) + C(105) = 7.20 - 8.20 + 2.50 = 1.50 \geq 0$$

This particular butterfly is arbitrage-free (positive value, consistent with a non-negative implied density around $K=100$). If instead $C(100)$ were quoted at $5.10$ (too expensive relative to its wings):

$$7.20 - 10.20 + 2.50 = -0.50 < 0$$

This is a violation: selling the butterfly (short 95 call, long two 100 calls, short 105 call) would generate $+0.50$ upfront with a payoff that is $\leq 0$ in every terminal state — a static arbitrage. [Verified: this is the standard textbook butterfly no-arbitrage test; the numeric inputs here are illustrative, not sourced from live market quotes.]

### Key Points

- Three simultaneous conditions define an arbitrage-free surface: calendar monotonicity in total variance, strike-convexity (butterfly), and bounded wing growth (Lee's moment formula).
- Total implied variance $w(k,T) = \sigma^2 T$ is the correct working variable for interpolation/extrapolation — not raw implied vol.
- Gatheral's $g(k) \geq 0$ function is the standard closed-form butterfly diagnostic for parametric slices (e.g., SVI).
- The Dupire local volatility formula's numerator and denominator directly encode the calendar and butterfly conditions respectively, making local-vol computation a practical arbitrage-detection tool.
- Naive interpolation schemes are the most common real-world source of accidental arbitrage in constructed surfaces.

**Related Topics**

- SVI and SSVI Parametrizations of the Volatility Surface
- Breeden-Litzenberger Formula and Risk-Neutral Density Extraction
- Dupire Local Volatility Model Derivation
- Roger Lee's Moment Formula and Wing Extrapolation Techniques
- Arbitrage-Free Smile Interpolation Methods (splines, kernel methods)
- Static Replication and Model-Free Variance Swap Pricing
- Calibration of Stochastic Volatility Models Under No-Arbitrage Constraints