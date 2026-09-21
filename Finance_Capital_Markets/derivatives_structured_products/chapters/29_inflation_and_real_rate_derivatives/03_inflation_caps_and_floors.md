## Inflation Caps and Floors

### Overview

Inflation caps and floors are the primary optional (non-linear) derivatives in the inflation market, providing convex protection against inflation exceeding or falling below a specified strike. They are the inflation-market analogue of interest rate caps/floors, and their pricing requires an explicit inflation smile framework rather than the linear no-arbitrage relations sufficient for ZCIS/YoY swaps. This item covers structure, payoff conventions, the two dominant pricing approaches (Black-76/lognormal and smile-consistent SABR-type models), and the demand drivers that shape this market.

### Structural Types

**Zero Coupon Inflation Caps/Floors**

A single optional payoff at maturity $T$ referencing the cumulative (compounded annualized) inflation over the full period:

- **Cap payoff**: $N \cdot T \cdot \max\left[\left(\dfrac{I(T)}{I(0)}\right)^{1/T} - 1 - K, \, 0\right]$
- **Floor payoff**: $N \cdot T \cdot \max\left[K - \left(\left(\dfrac{I(T)}{I(0)}\right)^{1/T} - 1\right), \, 0\right]$

Equivalently expressed as a call/put on the terminal index ratio $I(T)/I(0)$ struck at $(1+K)^T$.

**Year-on-Year Inflation Caps/Floors**

A strip of caplets/floorlets, each referencing a single period's YoY inflation rate:

- **Caplet payoff at $T_i$**: $N \cdot \max\left[\dfrac{I(T_i)}{I(T_{i-1})} - 1 - K, \, 0\right]$
- **Floorlet payoff at $T_i$**: $N \cdot \max\left[K - \left(\dfrac{I(T_i)}{I(T_{i-1})} - 1\right), \, 0\right]$

This is structurally identical to an interest rate cap/floor strip, but with the floating index being realized YoY CPI inflation rather than a LIBOR/SOFR-type rate.

### Key Structural Distinction from Rate Caps/Floors

**Key Points**

- Unlike nominal rate caplets, inflation floorlets are heavily traded and economically important — **zero-strike YoY floors** (protecting against any period of negative/deflationary YoY inflation) are a standard, liquid product, especially embedded in pension liability structures (LPI floors — Limited Price Indexation)
- Deflation protection has intrinsic economic value distinct from nominal rate floors, since realized CPI can genuinely be negative (deflation), unlike nominal rates which were historically bounded near zero but not naturally expected to be persistently negative
- **[Inference]** The high liquidity and pricing significance of zero-strike inflation floors, particularly in GBP markets via LPI structures, is a structural feature somewhat distinct from nominal-rate cap/floor markets, where zero-strike floors are comparatively less central to the market's core liquidity

### LPI (Limited Price Indexation) Floors

A UK pension-specific structure combining a floor and cap on YoY inflation, commonly "0% floor, 5% cap" (LPI 0-5) or "0% floor, 3% cap" (LPI 0-3), reflecting UK statutory minimum pension indexation requirements historically embedded in defined-benefit scheme rules:

$$\text{LPI Payoff}_i = N \cdot \min\left[\max\left(\frac{I(T_i)}{I(T_{i-1})} - 1, \, 0\right), \, K_{cap}\right]$$

This can be decomposed as a portfolio: long a zero-strike floorlet (deflation protection) plus short a cap struck at $K_{cap}$, relative to the uncapped/unfloored YoY swap — i.e., LPI $=$ YoY swap $+$ floor at $0\%$ $-$ cap at $K_{cap}$, via put-call-forward parity applied to each period.

**[Inference]** UK pension fund demand for LPI floor protection (driven by statutory indexation floors on scheme liabilities) has historically been a dominant structural driver of GBP inflation option market pricing and the shape of the inflation volatility surface at low strikes.

### Pricing Framework: Black-76 (Lognormal) Baseline

**Zero Coupon Caps/Floors**

Under the assumption that $I(T)/I(0)$ is lognormal under the $T$-forward nominal measure (as in the Jarrow-Yildirim model), the ZC cap/floor price follows a Black-76-type formula:

$$ZC\,Cap(0,T,K) = N \cdot P_{nom}(0,T)\left[F \cdot \Phi(d_1) - (1+K)^T \cdot \Phi(d_2)\right]$$



$$d_{1,2} = \frac{\ln\left(F/(1+K)^T\right) \pm \tfrac{1}{2}\sigma_I^2 T}{\sigma_I \sqrt{T}}$$

where $F = \mathbb{E}^T[I(T)/I(0)]$ is the forward index ratio (derived from the ZCIS breakeven curve) and $\sigma_I$ is the (Black-implied) volatility of the terminal index ratio.

**YoY Caps/Floors**

Each caplet is priced analogously to an interest rate caplet under Black-76, using the (convexity-adjusted) forward YoY rate $f_i$ and a per-period implied volatility $\sigma_i$:

$$Caplet_i = N \cdot P_{nom}(0,T_i)\left[f_i \Phi(d_1) - K\Phi(d_2)\right] \cdot \Delta_i$$

with $d_{1,2}$ defined analogously to standard Black caplet pricing, using $f_i$ (the JY-convexity-adjusted forward, not the naive ZC-implied forward) as the underlying.

### The Inflation Volatility Smile

**Key Points**

- Market-observed implied volatilities for inflation caps/floors vary by strike, exhibiting smile/skew just as in the rates and equity markets
- The **skew direction is typically the reverse of typical rate markets**: inflation skew is often such that low-strike (deflation-protection) volatilities are elevated relative to at-the-money, reflecting strong structural demand for deflation floors (particularly zero-strike) pushing up their implied vol — this reflects genuine tail-risk pricing plus the technical demand/supply imbalance from pension-driven floor buying
- **[Unverified]** The specific skew shape and its persistence vary significantly by currency and regime; this generalization should be checked against current quoted inflation option surfaces for any specific market before being relied upon in a pricing or trading context
- Standard smile-modeling techniques from the rates world are adapted: SABR-type stochastic volatility extensions, and JY-model extensions with stochastic index volatility, are the primary frameworks used to fit the observed inflation smile

### Smile-Consistent Extensions

**SABR-Style Inflation Smile**

The forward YoY (or ZC terminal ratio) can be given SABR-type dynamics analogous to the interest rate case:

$$df(t) = \sigma(t) f(t)^\beta dW_1(t), \qquad d\sigma(t) = \nu \sigma(t) dW_2(t), \qquad dW_1 dW_2 = \rho\, dt$$

with Hagan's asymptotic formula (see prior HJM chapter item on Interest Rate Smile Modeling) applied directly to back out Black-implied volatilities across strike, calibrated to observed inflation cap/floor market quotes.

**Extended Jarrow-Yildirim with Stochastic Volatility**

A more structurally consistent (but more complex) approach adds a stochastic volatility process directly to the inflation index dynamics within the JY three-factor framework:

$$\frac{dI(t)}{I(t)} = (r_n(t) - r_r(t))\,dt + \sqrt{v(t)}\, dW_I(t), \qquad dv(t) = \kappa(\theta - v(t))\,dt + \xi\sqrt{v(t)}\,dW_v(t)$$

(a Heston-type variance process bolted onto the JY inflation index dynamics), allowing joint consistent pricing of ZCIS, YoY swaps, and the full smile surface within a single arbitrage-free model, at the cost of significantly higher calibration complexity (requires fitting $\kappa, \theta, \xi$, and correlation parameters against the full cap/floor volatility cube).

### Market Structure and Demand Drivers

| Driver | Effect on Market |
| --- | --- |
| UK pension LPI liability hedging | Dominant driver of GBP zero-strike floor demand and skew |
| Insurance company inflation-linked annuity hedging | Similar floor-demand dynamics in other markets (EUR, to lesser extent) |
| Structured note issuance (inflation-linked retail notes) | Can create cap-selling flow from issuers hedging embedded caps sold to retail |
| Real asset / inflation-linked liability matching | Long-dated cap/floor demand from asset-liability management desks |
| Central bank inflation-targeting credibility | Affects perceived tail risk and therefore wing-strike implied vols |

### Curve and Surface Construction Workflow

1. Bootstrap the ZC breakeven curve and derive JY-convexity-adjusted YoY forwards (as in prior items)
2. Collect market quotes for ZC and/or YoY caps/floors across available strikes and maturities (often sparser and less liquid than rate cap/floor markets, particularly outside GBP/EUR/USD)
3. Back out Black-implied volatilities per quote using the Black-76-type formulas above
4. Fit a smile model (SABR or stochastic-volatility JY extension) per maturity bucket to the implied volatility points
5. Interpolate/extrapolate across the maturity dimension, checking for calendar-spread and butterfly arbitrage as in the rates smile case
6. Use the calibrated surface to price bespoke strikes/structures (LPI floors, custom-strike caps, digital inflation options) consistently

### Illustration: Inflation Smile vs. Typical Rate Smile Skew Direction

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 400">
<text x="350" y="24" font-size="15" text-anchor="middle" font-family="sans-serif" font-weight="bold">Inflation Smile: Elevated Low-Strike (Deflation) Vol (svg_diagram)</text>
<line x1="60" y1="350" x2="650" y2="350" stroke="#333" stroke-width="1.5" />
<line x1="60" y1="60" x2="60" y2="350" stroke="#333" stroke-width="1.5" />
<text x="355" y="380" font-size="13" text-anchor="middle" font-family="sans-serif">Strike (K, YoY inflation %)</text>
<text x="25" y="205" font-size="13" text-anchor="middle" font-family="sans-serif" transform="rotate(-90 25 205)">Implied Vol</text>
<line x1="355" y1="60" x2="355" y2="350" stroke="#999" stroke-width="1" stroke-dasharray="4,3" />
<text x="355" y="365" font-size="11" text-anchor="middle" font-family="sans-serif">ATM</text>
<path d="M 90 130 Q 250 230 355 250 Q 470 260 620 230" stroke="#d62728" stroke-width="2.5" fill="none" />
<text x="90" y="118" font-size="11" font-family="sans-serif" fill="#d62728">Elevated deflation-floor vol</text>

<text x="80" y="340" font-size="10" font-family="sans-serif">0% (floor)</text>

<text x="610" y="340" font-size="10" font-family="sans-serif">High K</text>

</svg>

### Risk Sensitivities

**Key Points**

- **Inflation vega**: sensitivity to the level of the inflation implied volatility surface, distinct from delta (breakeven level) risk; particularly concentrated at low strikes for floor-heavy books
- **Skew/smile risk**: sensitivity to changes in the relative pricing across strikes, relevant for risk-reversal and butterfly-style inflation option structures
- **Convexity-adjustment model risk**: since YoY caplet pricing depends on the JY-derived convexity adjustment to the forward, model parameter uncertainty (correlations, volatility assumptions) directly affects fair value, distinct from pure market-implied-volatility risk
- **Cross-gamma with nominal/real rates**: because the JY framework couples inflation index dynamics with nominal and real rate processes, inflation option books carry correlated exposure to rate volatility, not purely isolable inflation risk

### Worked Example: ZC Inflation Floor (Deflation Protection)

10Y ZC inflation floor, notional $N = 10{,}000{,}000$, strike $K = 0\%$ (pure deflation protection), forward index ratio $F = (1+2.30\%)^{10} \approx 1.2551$, implied vol $\sigma_I = 0.85\%$ (annualized, applied to the terminal ratio — illustrative, low due to the ZC/compounded nature), $T = 10$.

Using Black-76 put formula on the index ratio (struck at $(1+0)^{10} = 1$):

$$d_1 = \frac{\ln(1.2551/1) + 0.5 \times 0.0085^2 \times 10}{0.0085\sqrt{10}}, \qquad d_2 = d_1 - 0.0085\sqrt{10}$$

Given $F \gg K$ (forward is far in-the-money for the floor's opposite side, i.e., deeply out-of-the-money for the floor holder under this stylized flat-vol assumption), the floor value under this naive flat-vol input would be small — illustrating why in practice zero-strike floor pricing is dominated by smile/skew effects (elevated implied vol at the low strike) rather than by the ATM-level volatility used in this simplified illustration.

**[Inference]** This example uses illustrative rather than live market parameters and simplifies away the smile adjustment that materially drives actual zero-strike floor premiums in practice; real desk pricing would apply the strike-specific implied volatility from the calibrated smile, not a single flat $\sigma_I$.

### Related Topics

- Interest Rate Smile Modeling (SABR, displaced-diffusion) — methodology directly ported to inflation
- Jarrow-Yildirim model and stochastic-volatility extensions
- Zero Coupon and Year-on-Year Inflation Swaps — underlying forwards for cap/floor pricing
- LPI (Limited Price Indexation) structures and UK pension liability hedging
- Inflation volatility surface construction and arbitrage checking
- Digital and exotic inflation-linked structures (inflation-linked range accruals, best-of structures)