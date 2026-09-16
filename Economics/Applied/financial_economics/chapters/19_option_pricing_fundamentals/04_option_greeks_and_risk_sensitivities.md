## Option Greeks and Risk Sensitivities


### Overview

The Greeks are a set of risk sensitivity measures that quantify how an option's price responds to small changes in the underlying variables that determine its value — the underlying asset's price, time, volatility, and interest rates. Derived as partial derivatives of the Black-Scholes-Merton pricing formula, the Greeks are the primary tools options traders and risk managers use to understand, hedge, and manage the risk exposure of individual options and options portfolios.

### Delta ($\Delta$)

Delta measures the sensitivity of an option's price to a small change in the underlying asset's price.

$$\Delta_{call} = \frac{\partial c}{\partial S} = e^{-qT}N(d_1), \qquad \Delta_{put} = \frac{\partial p}{\partial S} = e^{-qT}[N(d_1) - 1]$$

(for a dividend yield $q$; set $q=0$ for a non-dividend-paying underlying)

**Key Points**

- Call delta ranges from 0 to 1; put delta ranges from -1 to 0.
- Delta approximates the number of shares of the underlying needed to hedge one option contract in a delta-neutral position (also called the hedge ratio).
- At-the-money options generally have delta near 0.5 (calls) or -0.5 (puts); deep in-the-money options approach delta of 1 (calls) or -1 (puts); deep out-of-the-money options approach delta of 0.
- Delta also has a probabilistic interpretation: it is closely related to (though not exactly equal to) the risk-neutral probability that the option finishes in-the-money.

**Example**

A call option has $\Delta = 0.62$. If the underlying stock price rises by $1, the call's price is expected to rise by approximately $0.62, holding all other factors constant.

### Delta Hedging

**Key Points**

- A short option position can be hedged by holding $\Delta$ shares of the underlying per option (a "delta-neutral" position), so that small movements in the underlying price produce approximately offsetting changes in the combined position's value.
- Because delta itself changes as the underlying price moves (a property captured by gamma), a delta-neutral hedge must be periodically rebalanced — this practice is known as dynamic hedging.
- Portfolio delta is the sum of the deltas of all individual positions (weighted by position size), allowing a trader to assess and manage the net directional exposure of a complex options portfolio as a single aggregate number.

### Gamma ($\Gamma$)

Gamma measures the rate of change of delta with respect to a small change in the underlying asset's price — the second derivative of option price with respect to the underlying, and the first derivative of delta.

$$\Gamma = \frac{\partial \Delta}{\partial S} = \frac{\partial^2 c}{\partial S^2} = \frac{e^{-qT} N'(d_1)}{S_0 \sigma \sqrt{T}}$$

where $N'(\cdot)$ is the standard normal probability density function.

**Key Points**

- Gamma is identical for a call and a put with the same strike, expiration, and underlying (a direct consequence of put-call parity, since the underlying's delta component is linear).
- Gamma is always positive for both long calls and long puts, meaning delta increases as the underlying price rises and decreases as it falls, for a long option position.
- Gamma is highest for at-the-money options and options close to expiration, and lowest for deep in-the-money or deep out-of-the-money options, or options with a long time to expiration.
- A high-gamma position requires more frequent delta-hedge rebalancing, since its delta changes rapidly with small moves in the underlying — this rebalancing need is sometimes described as the cost of gamma exposure.

**Example**

An option has $\Delta = 0.50$ and $\Gamma = 0.08$. If the underlying rises by $2, the new approximate delta is:

$$\Delta_{new} \approx \Delta + \Gamma \times \Delta S = 0.50 + 0.08 \times 2 = 0.66$$

### Delta-Gamma Approximation of Price Changes

Combining delta and gamma provides a second-order (quadratic) approximation of an option's price change for a given move in the underlying, analogous to the duration-convexity approximation for bonds:

$$\Delta c \approx \Delta \times \Delta S + \frac{1}{2}\Gamma \times (\Delta S)^2$$

**Key Points**

- This approximation improves on a delta-only (linear) estimate for larger moves in the underlying, since it captures the curvature of the option price with respect to the underlying price.
- The gamma term is always non-negative (adding to the estimated price change) for long option positions, mirroring how positive convexity in bonds always benefits the holder for a given change in yield.

### Theta ($\Theta$)

Theta measures the sensitivity of an option's price to the passage of time, holding all else constant — often referred to as time decay.

$$\Theta_{call} = -\frac{S_0 e^{-qT} N'(d_1) \sigma}{2\sqrt{T}} - rKe^{-rT}N(d_2) + qS_0e^{-qT}N(d_1)$$

**Key Points**

- Theta is generally negative for long option positions (both calls and puts), reflecting that, all else equal, an option loses value as time passes and less time remains for the underlying to move favorably.
- Theta is typically expressed as the dollar change in option value per day (dividing the annualized formula by 365 or by the number of trading days in a year, depending on convention).
- Time decay is not linear: theta accelerates (becomes more negative in magnitude) as expiration approaches, particularly for at-the-money options, meaning an option loses time value at an increasing rate in its final weeks.
- Theta is generally positive for the option writer (seller), meaning time decay works in favor of short option positions, all else equal — a key motivation for premium-selling strategies like covered calls.

**Example**

An option has $\Theta = -0.045$ (expressed as daily decay). Holding all other factors constant, the option's price is expected to fall by approximately $0.045 per calendar day due to time decay alone.

### Vega ($\nu$)

Vega measures the sensitivity of an option's price to a small change in the underlying asset's volatility.

$$\nu = \frac{\partial c}{\partial \sigma} = S_0 e^{-qT} N'(d_1) \sqrt{T}$$

**Key Points**

- Vega is identical for a call and a put with the same strike, expiration, and underlying (again a consequence of put-call parity).
- Vega is always positive for both long calls and long puts, since higher volatility increases the value of optionality — a wider range of potential outcomes increases the value of the right (without obligation) to benefit from favorable moves while limiting losses on unfavorable ones.
- Vega is highest for at-the-money options and options with longer time to expiration, and lowest for deep in-the-money/out-of-the-money options or options very close to expiration.
- Vega is technically not a Greek letter (the term is used by convention in options markets, sometimes alternatively labeled "kappa" or "lambda" in some academic texts), but it is universally included alongside the true Greek-letter sensitivities in standard practice.

**Example**

An option has $\nu = 0.18$ (often quoted per 1 percentage point change in volatility). If implied volatility rises from 25% to 27% (a 2-point increase), the option's price is expected to rise by approximately $0.18 \times 2 = \$0.36$, holding other factors constant.

### Rho ($\rho$)

Rho measures the sensitivity of an option's price to a small change in the risk-free interest rate.

$$\rho_{call} = KTe^{-rT}N(d_2), \qquad \rho_{put} = -KTe^{-rT}N(-d_2)$$

**Key Points**

- Rho is generally positive for calls (rising rates increase call value, since a higher discount rate reduces the present value of the strike price paid at exercise, benefiting the call holder) and negative for puts (rising rates reduce put value by the analogous logic, since the put holder eventually receives the strike, whose present value falls as rates rise).
- Rho is generally considered the least significant Greek for most short-to-medium-dated options, since interest rate changes typically have a smaller impact on option value relative to changes in the underlying price or volatility over such horizons; however, rho becomes more material for longer-dated options (e.g., LEAPS) and in environments with larger interest rate moves. [Inference: the relative materiality of rho compared to the other Greeks depends on the specific option's maturity and the interest rate environment at hand, and can vary meaningfully across market conditions.]

### Summary Table of the Greeks

| Greek | Measures Sensitivity To | Sign for Long Call | Sign for Long Put | Highest When |
| --- | --- | --- | --- | --- |
| Delta | Underlying price | Positive (0 to 1) | Negative (-1 to 0) | Deep ITM |
| Gamma | Delta (2nd deriv. of price) | Positive | Positive | At-the-money, near expiration |
| Theta | Time passage | Generally negative | Generally negative | At-the-money, near expiration |
| Vega | Volatility | Positive | Positive | At-the-money, longer time to expiration |
| Rho | Interest rate | Positive | Negative | Longer time to expiration |

### Greeks Across Moneyness and Time

**(svg_diagram) Delta and Gamma Profiles by Moneyness**

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 620 380">

<text x="310" y="24" text-anchor="middle" font-size="15" font-weight="bold" fill="`#1a1a2e`">Delta and Gamma vs. Moneyness (svg_diagram)</text>

<line x1="70" y1="330" x2="580" y2="330" stroke="#333" stroke-width="1.5" />

<line x1="70" y1="330" x2="70" y2="50" stroke="#333" stroke-width="1.5" />

<text x="325" y="360" text-anchor="middle" font-size="13" fill="#333">Underlying Price (S)</text>

<line x1="325" y1="50" x2="325" y2="330" stroke="#999" stroke-width="1" stroke-dasharray="4,4" />

<text x="325" y="345" text-anchor="middle" font-size="11" fill="#333">K (strike)</text>

<path d="M 90 300 Q 200 290 325 190 Q 450 90 560 70" fill="none" stroke="`#2266cc`" stroke-width="3" />

<text x="470" y="65" font-size="12" fill="`#2266cc`" font-weight="bold">Call Delta (0 to 1)</text>

<path d="M 90 320 Q 220 300 325 100 Q 430 300 560 320" fill="none" stroke="`#cc3333`" stroke-width="3" />

<text x="420" y="90" font-size="12" fill="`#cc3333`" font-weight="bold">Gamma (peaks at K)</text>

<text x="30" y="190" text-anchor="middle" font-size="13" fill="#333" transform="rotate(-90 30 190)">Sensitivity</text>

</svg>

### Portfolio-Level Greeks and Risk Management

**Key Points**

- Portfolio-level Greeks are computed by summing the individual Greeks of each position (weighted by the number of contracts and, where relevant, the multiplier), providing an aggregate risk profile for the entire options book.
- **Delta-neutral portfolios**: Constructed so total portfolio delta is approximately zero, eliminating first-order directional exposure to the underlying while retaining exposure to gamma, vega, and other higher-order risks.
- **Gamma and vega exposure management**: Since delta-neutral hedging alone does not address gamma or vega risk, traders often construct more sophisticated hedges (e.g., delta-gamma-neutral, or delta-gamma-vega-neutral positions) using combinations of options and the underlying to manage multiple risk dimensions simultaneously.
- Market makers, in particular, rely heavily on real-time aggregated Greek exposures across their entire book to manage risk efficiently, since manually assessing the risk of hundreds or thousands of individual option positions would be impractical.

### Higher-Order and Cross Greeks

Beyond the primary five Greeks, several second-order and cross-partial sensitivities are used in more sophisticated risk management contexts:

**Key Points**

- **Vanna**: Sensitivity of delta to a change in volatility (or equivalently, sensitivity of vega to a change in the underlying price); relevant for portfolios with significant volatility exposure combined with directional exposure.
- **Volga (vomma)**: Sensitivity of vega to a change in volatility (the "convexity" of vega); relevant for assessing how an option's volatility exposure itself changes as volatility moves.
- **Charm**: Sensitivity of delta to the passage of time (sometimes called "delta decay"); relevant for understanding how a hedge ratio will drift purely due to time passing, even without any move in the underlying.
- These higher-order Greeks are primarily used by professional derivatives desks managing large, complex options books, particularly around events with significant volatility risk (e.g., earnings announcements, macroeconomic data releases). [Inference: the practical importance of these higher-order Greeks in day-to-day risk management varies by the specific trading desk's strategy, position complexity, and risk tolerance.]

### Practical Applications of the Greeks

**Key Points**

- **Delta**: Used to determine hedge ratios for delta-neutral trading strategies and to assess directional exposure of a position or portfolio at a glance.
- **Gamma**: Used to anticipate how frequently a delta hedge will need rebalancing, and to assess "pin risk" near expiration for options close to the strike price.
- **Theta**: Used by premium-selling strategies (e.g., covered calls, credit spreads) to quantify expected time-decay income, and by option buyers to understand the cost of holding a position over time.
- **Vega**: Used to assess and hedge a portfolio's exposure to changes in implied volatility, particularly important around scheduled events (earnings, central bank announcements) where volatility itself is expected to change materially.
- **Rho**: Used primarily in the management of longer-dated options portfolios or interest-rate-sensitive derivatives where changes in the discount rate meaningfully affect valuation.

### Common Pitfalls

**Key Points**

- Treating delta as a static hedge ratio without accounting for gamma, which causes the hedge to become increasingly mismatched as the underlying price moves away from the level at which the hedge was established.
- Assuming theta decay is linear over an option's life; in reality, time decay accelerates as expiration approaches, particularly for at-the-money options.
- Confusing vega (sensitivity to volatility) with gamma (sensitivity of delta to the underlying price) — both are typically largest for at-the-money options, but they measure fundamentally different risk dimensions.
- Ignoring portfolio-level Greek aggregation and instead assessing each option position's risk in isolation, which can obscure important offsetting or compounding exposures across a complex book.
- Assuming the Greeks themselves remain constant between rebalancing periods; in fact, all Greeks change continuously as the underlying price, time to expiration, and implied volatility evolve, requiring ongoing monitoring for effective risk management.

### Related Topics

- The Black-Scholes-Merton model (source of the closed-form Greek formulas)
- Option payoff structures and put-call parity
- The binomial option pricing model (numerical alternative for computing Greeks, especially for American options)
- Delta-neutral and gamma-scalping trading strategies
- Implied volatility, the volatility smile, and vega risk management
- Higher-order Greeks (vanna, volga, charm) in professional derivatives risk management
- Options portfolio hedging and risk aggregation techniques