## No Arbitrage Models Ho Lee and Hull White

### Role of No-Arbitrage Models in Term Structure Modeling

No-arbitrage short rate models are constructed specifically to be exactly consistent with the currently observed market term structure at every maturity, in contrast to equilibrium models (such as Vasicek and CIR), whose small set of constant parameters generally cannot reproduce an arbitrarily shaped observed yield curve. No-arbitrage models achieve this by allowing one or more model parameters to be time-dependent functions, calibrated so that the model's theoretical bond prices match observed market bond prices exactly at time zero. This property is essential for pricing interest rate derivatives consistently with the market prices of the underlying instruments used to hedge them.

### The Ho-Lee Model

**Stochastic Differential Equation**

$$dr(t) = \theta(t)\, dt + \sigma\, dW(t)$$

The Ho-Lee model, introduced in 1986 as the first no-arbitrage short rate model, is the simplest extension of a pure Brownian motion for the short rate, adding a time-dependent drift term $\theta(t)$ while keeping volatility $\sigma$ constant.

**Key Properties**

- **No mean reversion** — unlike Vasicek or CIR, the Ho-Lee short rate has no pull-back-toward-a-long-run-mean term; the rate follows a generalized random walk with a deterministic, time-varying drift
- **Time-dependent drift $\theta(t)$** — chosen specifically to force the model's bond prices to match the initial observed discount curve exactly, making $\theta(t)$ a function derived from market data rather than a freely estimated constant parameter
- **Gaussian distribution** — like Vasicek, the short rate is normally distributed at any future time, permitting negative rates with positive probability
- **Constant volatility** — the absolute volatility of the short rate is constant across all rate levels and maturities, meaning the model implies a flat term structure of volatility, a simplification relative to observed market volatility term structures

**Deriving $\theta(t)$ from the Initial Curve**

Given the initial instantaneous forward rate curve $f(0,T)$ observed in the market:

$$\theta(t) = \frac{\partial f(0,t)}{\partial T} + \sigma^2 t$$

This shows explicitly how the model's drift is backed out from the slope of the currently observed forward curve, plus a convexity correction term arising from the volatility.

**Closed-Form Zero-Coupon Bond Price**

$$P(t,T) = \frac{P(0,T)}{P(0,t)} \exp\left[(T-t) f(0,t) - \frac{1}{2}\sigma^2 t (T-t)^2 - (T-t) r(t)\right]$$

This formula guarantees the model reprices the initially observed discount curve exactly, since $P(0,T)$ and $P(0,t)$ are taken directly as inputs from the market rather than derived from constant model parameters.

### The Hull-White Model (Extended Vasicek)

**Stochastic Differential Equation**

$$dr(t) = \left[\theta(t) - a\, r(t)\right] dt + \sigma\, dW(t)$$

The Hull-White model, introduced in 1990, extends the Vasicek model by replacing the constant term $ab$ in the drift with a time-dependent function $\theta(t)$, while retaining Vasicek's mean-reversion structure (via the constant speed-of-reversion parameter $a$) and constant volatility $\sigma$.

**Key Properties**

- **Mean reversion retained** — the $-a\,r(t)$ term still pulls the rate toward a level implied by $\theta(t)/a$ at each instant, distinguishing Hull-White from Ho-Lee's pure random walk
- **Exact fit to the initial term structure** — $\theta(t)$ is calibrated so that the model reproduces the observed market discount curve exactly, analogous to Ho-Lee but with mean reversion included
- **Gaussian distribution** — the short rate remains normally distributed, permitting closed-form bond and option pricing, but also permitting negative rates with positive probability, the same limitation inherited from Vasicek
- **Reduces to Ho-Lee as $a \to 0$** — when the mean-reversion speed is set to zero, the Hull-White model collapses to the Ho-Lee model, making Ho-Lee a special case of the broader Hull-White framework

**Deriving $\theta(t)$ from the Initial Curve**

$$\theta(t) = \frac{\partial f(0,t)}{\partial T} + a\, f(0,t) + \frac{\sigma^2}{2a}\left(1 - e^{-2at}\right)$$

**Closed-Form Zero-Coupon Bond Price**

$$P(t,T) = A(t,T)\, e^{-B(t,T)\, r(t)}$$

where:

$$B(t,T) = \frac{1 - e^{-a(T-t)}}{a}$$



$$A(t,T) = \frac{P(0,T)}{P(0,t)} \exp\left[B(t,T) f(0,t) - \frac{\sigma^2}{4a}\left(1 - e^{-2at}\right) B(t,T)^2\right]$$

Note the structural similarity to the standard Vasicek closed-form bond price formula for $B(t,T)$, with $A(t,T)$ now explicitly anchored to the market-observed discount factors $P(0,T)$ and $P(0,t)$ rather than to constant model parameters $a$ and $b$.

### Comparison: Ho-Lee vs. Hull-White

| Feature | Ho-Lee | Hull-White |
| --- | --- | --- |
| Drift | $\theta(t)$ | $\theta(t) - a\,r(t)$ |
| Mean reversion | None | Yes, speed $a$ |
| Volatility | Constant $\sigma$ | Constant $\sigma$ |
| Distribution | Gaussian | Gaussian |
| Fits initial curve exactly | Yes | Yes |
| Term structure of volatility | Flat (unrealistic) | More flexible via $a$, though still limited with constant $\sigma$ |
| Special case relationship | — | Reduces to Ho-Lee when $a = 0$ |

### Illustrative Diagram: No-Arbitrage Model Calibration Workflow (svg_diagram)

```mermaid
flowchart TD
    A[Observed Market Discount Curve P(0,T)] --> B[Extract Instantaneous Forward Curve f(0,t)]
    B --> C{Model Choice}
    C -->|Ho-Lee| D[Solve theta(t) = df/dT + sigma^2 t]
    C -->|Hull-White| E[Solve theta(t) = df/dT + a f(0,t) + Convexity Term]
    D --> F[Model Exactly Reprices Initial Curve]
    E --> F
    F --> G[Calibrate a and sigma to Cap/Swaption Market Prices]
    G --> H[Use Calibrated Model to Price Exotic/Path-Dependent Derivatives]
    H --> I[Consistent Pricing vs Vanilla Hedging Instruments]
```

### Calibrating $a$ and $\sigma$ to the Volatility Market

While $\theta(t)$ is derived analytically to fit the initial discount curve, the mean-reversion speed $a$ (Hull-White only) and volatility $\sigma$ are typically calibrated separately to match market-observed prices of liquid interest rate options — caps, floors, and swaptions — using the model's closed-form (or semi-closed-form) option pricing formulas.

**Hull-White Zero-Coupon Bond Option Price**

Since Hull-White bond prices are log-normally distributed conditional on $r(t)$, European options on zero-coupon bonds have closed-form solutions analogous to Black-Scholes, which in turn allow closed-form pricing of caplets/floorlets (as options on bond prices) and, via the Jamshidian decomposition, European swaptions on a portfolio of bond options.

**Calibration Objective**

$$\min_{a, \sigma} \sum_i \left(\text{Model Price}_i(a, \sigma) - \text{Market Price}_i\right)^2$$

summed across a chosen set of liquid cap/floor or swaption instruments spanning the relevant expiries and tenors for the derivatives being priced.

### Lattice and Tree Implementation

Both models are commonly implemented via **trinomial trees** (the Hull-White trinomial tree is the standard textbook and industry implementation) rather than relying solely on closed-form formulas, particularly for pricing American-style or Bermudan-style interest rate options (e.g., callable bonds, Bermudan swaptions) where early exercise features prevent closed-form solutions.

**Trinomial Tree Construction Steps**

1. Build a tree for a simplified, non-mean-reverting auxiliary process $x(t)$ (with $x(0) = 0$) using constant branching probabilities calibrated to match the local mean and variance of the process
2. Shift each node of the tree by a deterministic function $\alpha(t)$ (analogous to $\theta(t)/a$ in continuous time) so that the tree reproduces the initial observed discount curve exactly at every time step
3. Use backward induction through the tree to value derivatives with path-dependent or early-exercise features, discounting at each node using the short rate implied at that node

### Applications and Practical Use

- **Pricing callable and putable bonds** — the embedded option requires a tree or Monte Carlo implementation under a calibrated Hull-White (or Ho-Lee) model to value the optionality consistently with the issuer's or holder's exercise incentives
- **Bermudan swaption valuation** — since Bermudan swaptions require handling optimal exercise across multiple dates, Hull-White trees (or more advanced models) are standard tools for this valuation, extending the simpler closed-form European swaption formulas
- **Mortgage-backed securities and prepayment modeling** — the negative convexity from prepayment optionality is frequently modeled using a calibrated short rate tree combined with a prepayment model overlay
- **Counterparty credit risk (CVA/DVA) simulation** — Hull-White is commonly used to simulate future interest rate paths for exposure profile calculation in counterparty credit risk frameworks, due to its computational tractability at scale across many Monte Carlo paths

### Worked Example: Hull-White $\theta(t)$ at a Point in Time

Given a Hull-White model with $a = 0.10$, $\sigma = 0.012$, and the market-observed instantaneous forward rate curve at $t = 2$ years given by $f(0,2) = 4.20\%$ with an estimated local slope $\frac{\partial f(0,t)}{\partial T}\Big|_{t=2} = 0.15\%$ per year (i.e., 0.0015):

Step 1 — Compute the convexity adjustment term:

$$\frac{\sigma^2}{2a}\left(1 - e^{-2 \times 0.10 \times 2}\right) = \frac{0.012^2}{0.20}\left(1 - e^{-0.4}\right) = 0.00072 \times 0.3297 \approx 0.000237$$

Step 2 — Assemble $\theta(2)$:

$$\theta(2) = 0.0015 + 0.10 \times 0.042 + 0.000237 = 0.0015 + 0.0042 + 0.000237 \approx 0.00594$$

This value of $\theta(t)$ at the 2-year point is the deterministic drift adjustment the model requires at that instant to remain consistent with the observed forward curve, incorporating both the curve's local slope and the volatility-driven convexity correction.

### Practical Considerations and Limitations

- **Negative rates permitted** — both models retain the Gaussian short rate assumption inherited from Vasicek, meaning negative interest rates carry positive probability at any horizon; this has been treated as more acceptable in practice following observed negative-rate regimes in several major currencies, but remains a modeling choice to weigh against alternatives (e.g., shifted lognormal or CIR-based no-arbitrage variants) depending on the currency and period modeled
- **Single-factor limitation** — like Vasicek and CIR, both Ho-Lee and Hull-White in their standard form use a single Brownian motion driver, implying perfectly correlated movements across all points on the curve; multi-factor Hull-White extensions exist but add calibration complexity
- **Constant volatility term structure (Ho-Lee) or limited flexibility (Hull-White)** — matching the full market-observed term structure of implied volatility (not just the discount curve) generally requires either time-dependent $\sigma(t)$ extensions or moving to richer frameworks (e.g., the Libor Market Model), since a single constant $\sigma$ and single mean-reversion parameter $a$ cannot simultaneously fit volatility skew and term structure with full flexibility [Inference — the degree of residual calibration error depends on how much curvature and skew exists in the specific market volatility surface being fit]
- Behavior and stability of calibrated $a$ and $\sigma$ parameters may vary considerably across calibration instrument sets (cap-based vs. swaption-based calibration) and across market volatility regimes

**Related Topics**

- Short Rate Models Vasicek and Cox Ingersoll Ross
- Trinomial Tree Construction for Interest Rate Derivatives
- Jamshidian Decomposition for Swaption Pricing on Coupon Bonds
- Heath-Jarrow-Morton (HJM) Framework and Forward Rate Modeling
- LIBOR Market Model (LMM) / SOFR Market Model
- Bermudan Swaption Valuation Methods
- Counterparty Credit Risk Exposure Simulation (CVA/PFE)
- Callable Bond and Mortgage-Backed Security Optionality Valuation