## Extensions to Currency and Futures Options

### Overview

The Black-Scholes-Merton framework extends naturally to options on currencies (FX options) and options on futures contracts through modifications to the cost-of-carry term. The **Garman-Kohlhagen model** handles FX options by treating the foreign interest rate analogously to a continuous dividend yield, while the **Black-76 model** prices options on futures by eliminating the drift term entirely, since futures prices are already risk-neutral expected values under the appropriate measure.

### Garman-Kohlhagen Model (FX Options)

#### Conceptual Basis

A currency option gives the right to exchange one currency for another at a fixed rate. The underlying "asset" (foreign currency) earns interest at the **foreign risk-free rate** $r_f$, which plays exactly the role that a continuous dividend yield $q$ plays for equities — the holder of the option does not earn this foreign interest, so it must be subtracted from the drift.

**Key Points**

- Domestic currency = "cash" (discounted at domestic rate $r_d$)
- Foreign currency = "underlying asset" (discounted at foreign rate $r_f$, analogous to dividend yield)
- The spot exchange rate $S_0$ is quoted as domestic currency per unit of foreign currency (e.g., USD per EUR)

#### Formulas

$$C = S_0 e^{-r_f T} N(d_1) - K e^{-r_d T} N(d_2)$$



$$P = K e^{-r_d T} N(-d_2) - S_0 e^{-r_f T} N(-d_1)$$



$$d_1 = \frac{\ln(S_0/K) + (r_d - r_f + \sigma^2/2)T}{\sigma\sqrt{T}}$$



$$d_2 = d_1 - \sigma\sqrt{T}$$

**Variable Definitions**

- $S_0$ — current spot exchange rate (domestic per foreign unit)
- $K$ — strike exchange rate
- $r_d$ — domestic risk-free rate
- $r_f$ — foreign risk-free rate
- $\sigma$ — volatility of the exchange rate
- $T$ — time to expiration

**Key Points**

- This is structurally identical to the continuous dividend-yield BSM extension, with $q \to r_f$ and $r \to r_d$
- Put-call symmetry in FX options reflects the fact that a call to buy foreign currency is equivalent to a put to sell domestic currency from the foreign counterparty's perspective — this is the basis of the **FX put-call duality**: a call on EUR/USD is a put on USD/EUR (with appropriately transformed strike and notional)

#### Worked Example

**Example**

Price a 6-month European call option to buy EUR with USD:

- $S_0 = 1.0800$ (USD per EUR)
- $K = 1.1000$
- $r_d = 5\%$ (USD rate)
- $r_f = 3\%$ (EUR rate)
- $\sigma = 10\%$
- $T = 0.5$ years

Step 1 — Compute $d_1$:

$$d_1 = \frac{\ln(1.08/1.10) + (0.05 - 0.03 + 0.005)(0.5)}{0.10\sqrt{0.5}} = \frac{-0.01835 + 0.0125}{0.0707} \approx -0.0827$$

Step 2 — Compute $d_2$:

$$d_2 = -0.0827 - 0.0707 \approx -0.1534$$

Step 3 — Normal CDF values: $N(d_1) \approx 0.4670$, $N(d_2) \approx 0.4390$

Step 4 — Compute call price:

$$C = 1.08 \, e^{-0.03(0.5)}(0.4670) - 1.10 \, e^{-0.05(0.5)}(0.4390)$$



$$C = 1.08(0.9851)(0.4670) - 1.10(0.9753)(0.4390)$$

**Output**

$$C \approx 0.4971 - 0.4710 \approx 0.0261 \text{ USD per EUR}$$

The call option is worth approximately **$0.0261** per EUR of notional.

### Black-76 Model (Options on Futures)

#### Conceptual Basis

Futures prices are already **martingales under the risk-neutral measure** (assuming zero correlation between the futures price and the money-market account, which holds under standard assumptions with daily marking-to-market). This means the futures price has **zero drift** under the risk-neutral measure — there is no need to subtract a cost-of-carry term, because the carry cost is already embedded in how the futures price relates to spot.

**Key Points**

- Black-76 is used to price options on futures/forwards for commodities, interest rate futures, bond futures, and index futures
- The model discounts the *entire* payoff at the risk-free rate, since there is no upfront cost to enter a futures position (unlike buying the spot asset)
- $F_0$ replaces $S_0$, and **no separate discounting of the underlying term is needed** — only the final payoff is discounted

#### Formulas

$$C = e^{-rT}[F_0 N(d_1) - K N(d_2)]$$



$$P = e^{-rT}[K N(-d_2) - F_0 N(-d_1)]$$



$$d_1 = \frac{\ln(F_0/K) + (\sigma^2/2)T}{\sigma\sqrt{T}}$$



$$d_2 = d_1 - \sigma\sqrt{T}$$

**Variable Definitions**

- $F_0$ — current futures/forward price
- $K$ — strike price
- $r$ — risk-free rate (used only for discounting, not in the drift)
- $\sigma$ — volatility of the futures price
- $T$ — time to expiration

**Key Points**

- Notice the drift term in $d_1$ contains **no $r$** — this is the defining feature distinguishing Black-76 from standard BSM
- The entire bracketed payoff is multiplied by $e^{-rT}$, rather than discounting the strike term alone as in standard BSM
- Black-76 is the standard model underlying interest rate caps/floors (via Black's formula for caplets/floorlets) and swaptions, in addition to commodity and index futures options

#### Worked Example

**Example**

Price a European call option on a crude oil futures contract:

- $F_0 = \$75.00$
- $K = \$78.00$
- $r = 4\%$
- $\sigma = 35\%$
- $T = 0.25$ years (3 months)

Step 1 — Compute $d_1$:

$$d_1 = \frac{\ln(75/78) + (0.35^2/2)(0.25)}{0.35\sqrt{0.25}} = \frac{-0.03922 + 0.01531}{0.175} \approx -0.1366$$

Step 2 — Compute $d_2$:

$$d_2 = -0.1366 - 0.175 = -0.3116$$

Step 3 — Normal CDF: $N(d_1) \approx 0.4457$, $N(d_2) \approx 0.3777$

Step 4 — Compute call price:

$$C = e^{-0.04(0.25)}[75(0.4457) - 78(0.3777)]$$



$$C = 0.9900[33.43 - 29.46] = 0.9900(3.97)$$

**Output**

$$C \approx \$3.93$$

### Comparison of the Three Model Variants

| Model | Underlying | Drift Term in $d_1$ | Discounting |
| --- | --- | --- | --- |
| Standard BSM (no dividends) | Stock | $r + \sigma^2/2$ | Strike discounted at $r$ |
| Merton (dividend yield) | Dividend-paying stock | $r - q + \sigma^2/2$ | Strike discounted at $r$; spot scaled by $e^{-qT}$ |
| Garman-Kohlhagen | FX rate | $r_d - r_f + \sigma^2/2$ | Strike discounted at $r_d$; spot scaled by $e^{-r_f T}$ |
| Black-76 | Futures/forward price | $\sigma^2/2$ (no rate term) | Entire payoff discounted at $r$ |

**Key Points**

- All four models share the same fundamental $N(d_1)$, $N(d_2)$ structure — they differ only in how the drift and discounting terms incorporate the cost-of-carry
- This reveals the unifying principle: BSM-family models are fundamentally about correctly identifying the **risk-neutral drift** of the underlying and the appropriate **discount factor(s)** for each leg of the replicating portfolio

### Put-Call Parity Across Variants

**Garman-Kohlhagen parity:**

$$C - P = S_0 e^{-r_f T} - K e^{-r_d T}$$

**Black-76 parity:**

$$C - P = e^{-rT}(F_0 - K)$$

### Relationship Between Black-76 and Spot BSM via Cost-of-Carry

Since futures/forward prices relate to spot via the cost-of-carry relationship $F_0 = S_0 e^{(r-q)T}$ (for a continuous dividend yield $q$), substituting this into Black-76 recovers the dividend-adjusted BSM formula exactly — confirming Black-76 and Merton's dividend-yield model are two equivalent ways of expressing the same no-arbitrage price, just parameterized differently (in terms of spot vs. futures price).

$$F_0 = S_0 e^{(r-q)T} \implies \text{Black-76 with } F_0 \equiv \text{Merton model with } S_0, q$$

### Visualizing the Model Family Relationships

```mermaid
flowchart TD
    A[Standard Black-Scholes: No Dividends] --> B[Add Continuous Dividend Yield q]
    B --> C[Merton Dividend-Adjusted Model]
    C --> D[Replace q with Foreign Interest Rate rf]
    D --> E[Garman-Kohlhagen FX Option Model]
    C --> F[Substitute Cost-of-Carry: F0 = S0 * e^((r-q)T)]
    F --> G[Black-76 Futures Option Model]
    G -->|Equivalent under no-arbitrage| C
```

### Application Domains Summary

**Key Points**

- **Garman-Kohlhagen**: interbank FX options, corporate FX hedging, currency risk management
- **Black-76**: commodity futures options (oil, gold, agricultural), interest rate caps/floors and swaptions (via Black's formula), bond futures options, equity index futures options
- Both models retain the same core BSM limitations discussed previously (constant volatility, lognormal dynamics, no transaction costs) — practitioners overlay volatility smiles/skews onto both models in practice, exactly as with equity options
- Behavior of these models near expiration or under extreme rate differentials (for Garman-Kohlhagen) can diverge from theoretical predictions; real-world FX and futures markets exhibit their own smile/skew dynamics that vary by currency pair and commodity **[Inference]**

**Conclusion**

The Garman-Kohlhagen and Black-76 models demonstrate the flexibility of the Black-Scholes-Merton framework: by correctly reinterpreting the cost-of-carry term (foreign interest rate for FX, zero drift for futures), the same fundamental option pricing logic extends cleanly across asset classes. Both remain special cases of the same no-arbitrage argument, differing only in how the underlying's risk-neutral drift and discounting are structured.

**Related Topics**

- Black's Formula for Interest Rate Caps, Floors, and Swaptions
- Cost-of-Carry Relationships and Forward Pricing
- FX Volatility Smile and Risk Reversals/Butterflies (25-delta conventions)
- Covered Interest Rate Parity and FX Forward Pricing
- Options on Bond Futures and the Delivery/CTD Mechanism
- Quanto Options and Cross-Currency Derivatives
- Margining and Daily Settlement Effects on Futures Options Pricing
- Volatility Surface Construction for Commodity and FX Markets