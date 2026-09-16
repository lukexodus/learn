## Option Terminology and Payoff Diagrams


### Overview

Financial options are contracts granting the holder a right, but not an obligation, to buy or sell an underlying asset at a specified price within a specified time. In corporate finance, options theory extends beyond traded equity options to value corporate decisions with option-like characteristics (real options, embedded securities). Understanding basic terminology and payoff structures is the foundation for both financial option pricing and corporate applications.

### Core Terminology

**Key Points**

- **Call option**: Grants the holder the right to *buy* the underlying asset at a specified price.
- **Put option**: Grants the holder the right to *sell* the underlying asset at a specified price.
- **Strike price (exercise price)**, $K$: The price at which the underlying asset can be bought (call) or sold (put) if the option is exercised.
- **Expiration date**: The date after which the option can no longer be exercised.
- **European option**: Can only be exercised on the expiration date itself.
- **American option**: Can be exercised at any time up to and including the expiration date.
- **Premium**: The price paid by the option buyer to the option seller (writer) for the option contract.
- **Underlying asset**: The security or asset on which the option's value is based (stock, index, commodity, currency, or in real options, a project or asset).

### Long vs. Short Positions

**Key Points**

- **Long a call**: Holds the right to buy; profits if the underlying rises above the strike plus premium paid.
- **Short a call (writing a call)**: Obligated to sell if the holder exercises; profits limited to premium received, with theoretically unlimited loss potential if the underlying rises sharply.
- **Long a put**: Holds the right to sell; profits if the underlying falls below the strike minus premium paid.
- **Short a put (writing a put)**: Obligated to buy if the holder exercises; profits limited to premium received, with substantial loss potential if the underlying falls sharply (bounded by the underlying falling to zero).

### Moneyness

Describes the relationship between the current price of the underlying asset, $S$, and the strike price, $K$:

| Moneyness | Call Option | Put Option |
| --- | --- | --- |
| In-the-money (ITM) | $S > K$ | $S < K$ |
| At-the-money (ATM) | $S = K$ | $S = K$ |
| Out-of-the-money (OTM) | $S < K$ | $S > K$ |

**[Inference]** Moneyness reflects intrinsic value only and does not by itself determine whether early exercise (for American options) is optimal, since time value considerations also factor into that decision.

### Intrinsic Value and Time Value

An option's premium can be decomposed into two components:

$$\text{Option Premium} = \text{Intrinsic Value} + \text{Time Value}$$

**Intrinsic value**:

$$\text{Call Intrinsic Value} = \max(0, S - K)$$



$$\text{Put Intrinsic Value} = \max(0, K - S)$$

**Time value** represents the additional premium attributable to the possibility that the option will become more valuable before expiration, driven primarily by time to expiration and volatility of the underlying. Time value decays to zero at expiration (a phenomenon known as **time decay** or **theta decay**).

### Call Option Payoff Diagrams

**At Expiration — Long Call**

$$\text{Payoff}_{\text{long call}} = \max(0, S_T - K)$$



$$\text{Profit}_{\text{long call}} = \max(0, S_T - K) - C_0$$

Where $S_T$ is the underlying price at expiration and $C_0$ is the premium paid.

**Example**: A call option with strike $K = \$50$, premium $C_0 = \$5$.

- If $S_T = \$40$: Payoff $= \max(0, 40-50) = 0$; Profit $= 0 - 5 = -\$5$ (maximum loss, limited to premium paid).
- If $S_T = \$50$: Payoff $= 0$; Profit $= -\$5$.
- If $S_T = \$60$: Payoff $= \max(0, 60-50) = \$10$; Profit $= 10 - 5 = \$5$.
- If $S_T = \$55$ (breakeven): Payoff $= \$5$; Profit $= 5 - 5 = \$0$.

**Breakeven for long call**: $S_T = K + C_0 = 50 + 5 = \$55$.

**Key Points**

- Maximum loss for the long call holder is limited to the premium paid.
- Maximum gain is theoretically unlimited as $S_T$ rises.
- Short call position is the mirror image: maximum gain limited to premium received, maximum loss theoretically unlimited.

### Put Option Payoff Diagrams

**At Expiration — Long Put**

$$\text{Payoff}_{\text{long put}} = \max(0, K - S_T)$$



$$\text{Profit}_{\text{long put}} = \max(0, K - S_T) - P_0$$

**Example**: A put option with strike $K = \$50$, premium $P_0 = \$4$.

- If $S_T = \$60$: Payoff $= \max(0, 50-60) = 0$; Profit $= 0 - 4 = -\$4$ (maximum loss).
- If $S_T = \$50$: Payoff $= 0$; Profit $= -\$4$.
- If $S_T = \$40$: Payoff $= \max(0, 50-40) = \$10$; Profit $= 10 - 4 = \$6$.
- If $S_T = \$46$ (breakeven): Payoff $= \$4$; Profit $= 4 - 4 = \$0$.

**Breakeven for long put**: $S_T = K - P_0 = 50 - 4 = \$46$.

**Key Points**

- Maximum loss for the long put holder is limited to the premium paid.
- Maximum gain is bounded (not unlimited), since the underlying price cannot fall below zero: maximum payoff $= K$, maximum profit $= K - P_0$.
- Short put position: maximum gain limited to premium received; maximum loss occurs if $S_T$ falls to zero, bounded at $K - P_0$ loss.

### Payoff Diagram (SVG)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 900 480" font-family="Arial, sans-serif">
<text x="450" y="25" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Option Payoff Diagrams at Expiration (svg_diagram)</text>

<g>
<text x="200" y="55" text-anchor="middle" font-size="13" font-weight="bold" fill="#1a1a1a">Long Call (K=50, Premium=5)</text>
<line x1="60" y1="200" x2="380" y2="200" stroke="#333" stroke-width="1.5" />
<line x1="220" y1="80" x2="220" y2="320" stroke="#333" stroke-width="1.5" />
<text x="385" y="204" font-size="11" fill="#333">S_T</text>
<text x="205" y="75" font-size="11" fill="#333">Profit</text>

<polyline points="80,220 220,220 340,100" fill="none" stroke="#c0392b" stroke-width="3" />
<line x1="60" y1="220" x2="380" y2="220" stroke="#999" stroke-width="1" stroke-dasharray="4,3" />
<text x="65" y="235" font-size="10" fill="#666">-5 (max loss)</text>
<line x1="260" y1="80" x2="260" y2="320" stroke="#2980b9" stroke-width="1" stroke-dasharray="4,3" />
<text x="262" y="315" font-size="10" fill="#2980b9">Breakeven=55</text>
<line x1="220" y1="80" x2="220" y2="320" stroke="#27ae60" stroke-width="1" stroke-dasharray="2,2" />
<text x="180" y="330" font-size="10" fill="#27ae60">K=50</text>
</g>

<g>
<text x="650" y="55" text-anchor="middle" font-size="13" font-weight="bold" fill="#1a1a1a">Long Put (K=50, Premium=4)</text>
<line x1="510" y1="200" x2="830" y2="200" stroke="#333" stroke-width="1.5" />
<line x1="670" y1="80" x2="670" y2="320" stroke="#333" stroke-width="1.5" />
<text x="835" y="204" font-size="11" fill="#333">S_T</text>
<text x="655" y="75" font-size="11" fill="#333">Profit</text>

<polyline points="530,100 670,220 790,220" fill="none" stroke="#8e44ad" stroke-width="3" />
<line x1="510" y1="220" x2="830" y2="220" stroke="#999" stroke-width="1" stroke-dasharray="4,3" />
<text x="795" y="235" font-size="10" fill="#666">-4 (max loss)</text>
<line x1="630" y1="80" x2="630" y2="320" stroke="#2980b9" stroke-width="1" stroke-dasharray="4,3" />
<text x="560" y="315" font-size="10" fill="#2980b9">Breakeven=46</text>
<line x1="670" y1="80" x2="670" y2="320" stroke="#27ae60" stroke-width="1" stroke-dasharray="2,2" />
<text x="675" y="330" font-size="10" fill="#27ae60">K=50</text>
</g>

<line x1="60" y1="200" x2="380" y2="200" stroke="#333" stroke-width="0" />
<text x="30" y="204" font-size="10" fill="#333">0</text>
<text x="480" y="204" font-size="10" fill="#333">0</text>
</svg>

### Put-Call Parity

A fundamental no-arbitrage relationship linking European call and put prices with the same strike and expiration:

$$C_0 + \frac{K}{(1+r)^T} = P_0 + S_0$$

Where $C_0$ is the call premium, $P_0$ is the put premium, $S_0$ is the current underlying price, $K$ is the strike price, $r$ is the risk-free rate, and $T$ is time to expiration.

**Key Points**

- Put-call parity holds strictly only for European options on non-dividend-paying underlying assets in frictionless markets; adjustments are needed for dividends and for American-style early exercise.
- Deviations from parity create arbitrage opportunities, which market forces act to eliminate — this is why the relationship is described as a no-arbitrage condition rather than an empirical regularity.

### Combined Option Strategies (Brief Reference)

**Key Points**

- **Protective put**: Long stock + long put; caps downside risk while retaining upside, functioning like portfolio insurance.
- **Covered call**: Long stock + short call; generates income (premium) but caps upside potential.
- **Straddle**: Long call + long put at the same strike; profits from large price movement in either direction, loses if the underlying stays near the strike.
- **[Inference]** These combined strategies are typically taught as building blocks for understanding option-based risk management and are directly analogous to how corporations use options embedded in securities (e.g., convertible bonds combine a bond with an embedded call option on the issuer's stock) — a connection developed further under corporate applications of option pricing.

**Related Topics**

- Option pricing models (Black-Scholes-Merton, binomial model)
- Real options analysis in capital budgeting (expansion, abandonment, timing options)
- Convertible securities and warrants as embedded corporate options
- The determinants of option value (volatility, time to expiration, interest rates)
- Employee stock options and executive compensation design