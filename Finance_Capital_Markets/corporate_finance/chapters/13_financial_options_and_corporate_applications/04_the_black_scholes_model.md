## The Black Scholes Model


### Overview

The Black-Scholes-Merton (BSM) model provides a closed-form analytical solution for pricing European options, representing one of the most significant developments in financial economics. Developed by Fischer Black and Myron Scholes (with foundational contributions from Robert Merton), it derives an option's fair value as a function of five observable/estimable inputs, without requiring knowledge of the underlying asset's expected return — a result made possible by the risk-neutral valuation principle also underlying the binomial model.

### The Black-Scholes Formula

For a European call option on a non-dividend-paying stock:

$$C_0 = S_0 N(d_1) - Ke^{-rT}N(d_2)$$

For a European put option (via put-call parity or direct derivation):

$$P_0 = Ke^{-rT}N(-d_2) - S_0N(-d_1)$$

Where:

$$d_1 = \frac{\ln(S_0/K) + (r + \sigma^2/2)T}{\sigma\sqrt{T}}$$



$$d_2 = d_1 - \sigma\sqrt{T}$$

**Variable definitions**

- $S_0$ = current price of the underlying asset
- $K$ = strike price
- $r$ = risk-free interest rate (continuously compounded, annualized)
- $T$ = time to expiration (in years)
- $\sigma$ = annualized volatility (standard deviation) of the underlying asset's returns
- $N(\cdot)$ = cumulative standard normal distribution function

### The Five Inputs and Their Effect on Option Value

| Input | Effect on Call Value | Effect on Put Value |
| --- | --- | --- |
| Underlying price ($S_0$) ↑ | Increases | Decreases |
| Strike price ($K$) ↑ | Decreases | Increases |
| Time to expiration ($T$) ↑ | Increases | Generally increases |
| Volatility ($\sigma$) ↑ | Increases | Increases |
| Risk-free rate ($r$) ↑ | Increases | Decreases |

**Key Points**

- Both call and put values increase with volatility, since higher volatility increases the probability of large favorable payoffs while the option holder's downside is fixed (limited to the premium paid) — options have asymmetric payoffs, so increased uncertainty is unambiguously valuable to the holder.
- The relationship between time to expiration and put value is not always strictly monotonic for European puts on non-dividend-paying stocks in all parameter ranges; **[Inference]** this is a known technical subtlety in the model but is a second-order effect not typically emphasized outside of advanced derivatives coursework.

### Worked Example

**Given**: $S_0 = \$100$, $K = \$100$, $r = 5\%$ (continuously compounded), $\sigma = 25\%$, $T = 1$ year.

**Step 1: Compute $d_1$**

$$d_1 = \frac{\ln(100/100) + (0.05 + 0.25^2/2)(1)}{0.25\sqrt{1}} = \frac{0 + (0.05 + 0.03125)}{0.25} = \frac{0.08125}{0.25} = 0.325$$

**Step 2: Compute $d_2$**

$$d_2 = 0.325 - 0.25\sqrt{1} = 0.325 - 0.25 = 0.075$$

**Step 3: Look up cumulative normal values**

$$N(0.325) \approx 0.6273 \qquad N(0.075) \approx 0.5299$$

**Step 4: Compute call price**

$$C_0 = 100(0.6273) - 100 \cdot e^{-0.05(1)}(0.5299)$$



$$= 62.73 - 100(0.9512)(0.5299) = 62.73 - 50.41 = \$12.32$$

**Step 5: Compute put price (via put-call parity)**

$$P_0 = C_0 + Ke^{-rT} - S_0 = 12.32 + 95.12 - 100 = \$7.44$$

### The Option Greeks

The Greeks measure the sensitivity of an option's price to changes in each underlying input, and are widely used for risk management of option positions.

**Delta ($\Delta$)**: Sensitivity to changes in the underlying price.

$$\Delta_{\text{call}} = N(d_1) \qquad \Delta_{\text{put}} = N(d_1) - 1$$

Interpreted as the approximate change in option price per $1 change in the underlying, and as the hedge ratio (shares of stock needed to delta-hedge one option).

**Gamma ($\Gamma$)**: Sensitivity of delta to changes in the underlying price (the rate of change of delta itself); identical for calls and puts with the same strike and expiration.

**Vega ($\nu$)**: Sensitivity to changes in volatility. Always positive for both calls and puts (consistent with the volatility relationship noted above).

**Theta ($\Theta$)**: Sensitivity to the passage of time (time decay). Generally negative for long option positions, reflecting the erosion of time value as expiration approaches.

**Rho ($\rho$)**: Sensitivity to changes in the risk-free rate. Positive for calls, negative for puts.

**[Inference]** In practice, options traders and risk managers rely heavily on the Greeks (particularly delta and vega) for hedging and portfolio risk management, since they translate the abstract pricing formula into actionable exposure measures; precise numerical values depend on the specific parameter inputs and are typically computed via software rather than hand calculation.

### Key Assumptions of the Black-Scholes Model

**Key Points**

1. The underlying asset's returns follow a **lognormal distribution** (equivalently, log-returns are normally distributed), implying continuous, geometric Brownian motion price paths with no jumps.
2. **Constant volatility** ($\sigma$) over the life of the option.
3. **Constant risk-free rate** over the life of the option.
4. **No dividends** paid during the option's life (in the basic model; extensions exist for dividend-paying assets).
5. **European exercise only** — no early exercise feature.
6. **Frictionless markets**: no transaction costs, no taxes, and assets are perfectly divisible.
7. **No arbitrage opportunities** exist in the market.
8. **Continuous trading** is possible, allowing continuous delta-hedging.

### Known Limitations and Empirical Departures

**Key Points**

- **Volatility smile/skew**: Empirically, implied volatilities backed out of observed market option prices vary systematically across different strike prices for the same expiration, contradicting the model's constant-volatility assumption. This pattern is well-documented in equity index options markets, particularly since the 1987 crash.
- **Fat tails**: Actual asset return distributions tend to exhibit more extreme outcomes than the lognormal distribution predicts (leptokurtosis), meaning the model can underprice deep out-of-the-money options that would benefit from large, rare price moves.
- **Constant volatility assumption**: Volatility is empirically time-varying (volatility clustering), motivating extensions such as stochastic volatility models (e.g., Heston model) and GARCH-based approaches.
- **No early exercise**: The model cannot directly price American options; approximations (e.g., Barone-Adesi-Whaley) or numerical methods (binomial trees, finite difference methods) are used instead.

**[Fact]** Despite these known limitations, the Black-Scholes framework remains the standard reference point in both academic and practitioner contexts, largely because of its tractability, and market convention has adapted around it — for instance, options are frequently quoted in terms of "implied volatility" (the volatility input that makes the model price match the observed market price) rather than in dollar premiums, effectively using the model as a translation device even where its assumptions are known to be imperfect.

### Dividend-Adjusted Black-Scholes

For a continuous dividend yield $q$:

$$C_0 = S_0 e^{-qT}N(d_1) - Ke^{-rT}N(d_2)$$



$$d_1 = \frac{\ln(S_0/K) + (r - q + \sigma^2/2)T}{\sigma\sqrt{T}}$$

The dividend yield reduces the effective forward value of the stock, lowering the call price and raising the put price relative to the non-dividend case, consistent with the intuition that dividend payments reduce the stock price without benefiting the option holder.

### Black-Scholes Inputs and Outputs Flow

```mermaid
flowchart TD
    A[Underlying Price S0] --> F[Compute d1 and d2]
    B[Strike Price K] --> F
    C[Risk-Free Rate r] --> F
    D[Time to Expiration T] --> F
    E[Volatility sigma] --> F
    F --> G[Look Up N(d1) and N(d2) - Cumulative Normal Distribution]
    G --> H[Call Price: C0 = S0*N(d1) - K*e^-rT*N(d2)]
    G --> I[Put Price: P0 = K*e^-rT*N(-d2) - S0*N(-d1)]
    H --> J[Compute Greeks: Delta, Gamma, Vega, Theta, Rho]
    I --> J
    J --> K[Risk Management / Hedging Decisions]
```

### Corporate Finance Applications

**Key Points**

- **Employee stock option valuation**: Firms use Black-Scholes (often with adjustments for vesting, forfeiture, and expected life shorter than contractual maturity) to value stock options for financial reporting purposes under accounting standards requiring option expense recognition.
- **Warrant valuation**: Similar mechanics apply to corporate warrants, with adjustments for the dilutive effect of warrant exercise on shares outstanding.
- **Merton model of credit risk**: Applies Black-Scholes logic to model corporate equity as a call option on firm assets (strike price equal to the face value of debt), providing a market-based approach to estimating default probability and credit spreads.
- **Real options valuation**: While the binomial model is often preferred for real options due to its flexibility with early-exercise and discrete decision points, Black-Scholes-style closed-form approximations are sometimes used for simpler real option valuations (e.g., a straightforward expansion option with European-like exercise timing).

**Related Topics**

- Binomial option pricing and its convergence to Black-Scholes
- Put-call parity as a consistency check on Black-Scholes outputs
- Implied volatility and the volatility smile/skew
- The Merton model of corporate credit risk (equity as a call option on firm assets)
- Real options analysis in capital budgeting