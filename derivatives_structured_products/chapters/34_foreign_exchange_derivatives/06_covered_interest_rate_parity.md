## Covered Interest Rate Parity

### Overview

Covered Interest Rate Parity (CIP) is the no-arbitrage relationship linking spot exchange rates, forward exchange rates, and the interest rate differential between two currencies. It is the foundational identity underlying FX forward pricing, cross-currency basis swaps, and the entire structure of FX derivatives markets.

**Key Points**

- CIP states that the forward premium/discount on a currency pair must equal the interest rate differential between the two currencies
- "Covered" refers to the fact that FX risk is fully hedged (covered) via a forward contract, as opposed to Uncovered Interest Rate Parity (UIP), which involves unhedged expected exchange rate changes
- CIP is a replication/no-arbitrage condition, not a behavioral or equilibrium theory — it should hold mechanically absent frictions
- Since the 2008 Global Financial Crisis, persistent CIP deviations (the "cross-currency basis") have become a defining feature of FX markets, contradicting the textbook version of the theory

### The Core Formula

For two currencies, domestic (d) and foreign (f), with spot rate $S_0$ (domestic per unit foreign) and forward rate $F_T$ for maturity $T$:

$$F_T = S_0 \cdot \frac{1 + r_d \cdot T}{1 + r_f \cdot T}$$

Or in continuously-compounded form:

$$F_T = S_0 \cdot e^{(r_d - r_f)T}$$

This is identical in structure to the Garman-Kohlhagen cost-of-carry relationship, since the foreign interest rate acts as a continuous "dividend yield" on the foreign currency.

**Forward Points**

Market convention quotes the forward not as an outright rate but as **forward points** — the difference between forward and spot, typically scaled (e.g., in pips):

$$\text{Forward Points} = F_T - S_0 \approx S_0 (r_d - r_f) T$$

If $r_d > r_f$, the domestic currency has a lower relative value forward (foreign currency trades at a forward premium), and vice versa.

### No-Arbitrage Derivation

CIP is derived by constructing two portfolios that must have identical payoffs and therefore identical costs, else a riskless arbitrage exists.

**Strategy A — Domestic Investment:**

Invest 1 unit of domestic currency at the domestic rate $r_d$ for time $T$. Payoff: $(1 + r_d T)$ domestic units.

**Strategy B — Covered Foreign Investment:**

1. Convert 1 domestic unit to $1/S_0$ foreign units at spot
2. Invest the foreign amount at $r_f$ for time $T$, yielding $(1/S_0)(1 + r_f T)$ foreign units
3. Simultaneously enter a forward contract at inception to convert the foreign proceeds back to domestic currency at rate $F_T$

Payoff: $(1/S_0)(1 + r_f T) \cdot F_T$ domestic units.

Since both strategies start with the same domestic investment and are entered at $t=0$ with fully known (covered) terminal cash flows, absence of arbitrage requires the payoffs to be equal:

$$(1 + r_d T) = \frac{F_T}{S_0}(1 + r_f T) \implies F_T = S_0 \frac{1 + r_d T}{1 + r_f T}$$

**Arbitrage Mechanics if CIP Is Violated**

If $F_T > S_0(1+r_dT)/(1+r_fT)$ (forward "too expensive"), an arbitrageur would:

1. Borrow domestic currency at $r_d$
2. Convert to foreign currency at spot, invest at $r_f$
3. Sell the foreign proceeds forward at the (relatively rich) $F_T$
4. Repay the domestic loan from converted proceeds, capturing a riskless profit

The reverse trade applies if the forward is "too cheap." In a frictionless market with unlimited balance sheet capacity, such arbitrage should force $F_T$ back to the CIP-implied level instantaneously.

### CIP and the Money Market Basis

CIP can be restated in terms of the **implied foreign interest rate** derived from FX-market prices alone, without reference to the actual foreign money market rate:

$$r_f^{implied} = \left(\frac{S_0}{F_T}(1+r_dT) - 1\right)\frac{1}{T}$$

If FX and money markets are integrated, $r_f^{implied}$ should equal the actual quoted foreign money-market rate (e.g., foreign LIBOR/SOFR-equivalent or interbank rate). The difference between them is the **cross-currency basis**:

$$\text{basis} = r_f^{implied} - r_f^{market}$$

### The Cross-Currency Basis: A Major Post-2008 Market Feature

**Key Points**

- Prior to 2007–2008, CIP held closely for major currency pairs (e.g., USD/EUR, USD/JPY), consistent with textbook no-arbitrage theory
- Since the Global Financial Crisis, and especially since 2014–2015, a persistent, economically significant cross-currency basis has emerged and remained, particularly in USD funding markets
- The basis is typically **negative against the dollar** for most major currencies (EUR, JPY, GBP), meaning it is more expensive to swap into USD via FX markets than the covered interest differential alone would suggest — reflecting structural USD funding demand from non-US banks
- This is one of the most heavily researched anomalies in modern international finance, since it represents a textbook arbitrage condition failing to hold in liquid, developed markets

**Documented Drivers of the Basis (widely cited in the academic and central-bank literature)**

1. **Balance sheet costs and regulation**: Post-Basel III capital and leverage ratio requirements make it costly for banks to expand balance sheets to exploit the arbitrage, even when profitable in unconstrained terms. This converts a theoretical arbitrage into one requiring costly regulatory capital, so it persists.
2. **Differential USD demand**: Non-US banks and corporates have structural USD funding needs (USD-denominated assets, trade financing, USD debt issuance) that exceed natural USD funding supply via local deposits, creating persistent one-directional demand to swap into dollars.
3. **Limited arbitrage capacity of dealers**: Even where the basis represents a "free" arbitrage pre-2008, few institutions now have both the balance sheet capacity and risk appetite to scale into it at size, especially around quarter-end and year-end regulatory reporting dates when the basis often spikes.
4. **Quarter-end/year-end dynamics**: The basis frequently widens sharply around bank reporting dates due to temporary balance-sheet-shrinking ("window dressing") by dealer banks, then reverts.

**[Inference]** The magnitude and even the sign of the cross-currency basis for any given currency pair varies meaningfully over time and across the yield curve tenor, so while the negative-basis-against-USD pattern for major currencies has been persistent and widely documented, citing a specific numerical basis level for a given pair requires checking current market data rather than relying on a fixed historical figure.

### Cross-Currency Basis Swaps

The basis is directly observable and traded via **cross-currency basis swaps (XCCY basis swaps)**, which exchange floating-rate cash flows in two currencies (e.g., 3M USD SOFR vs. 3M EURIBOR-equivalent), with a spread added to one leg (conventionally the non-USD leg) to make the swap fair value at inception. This spread is the market-quoted cross-currency basis.

**Structure of a EUR/USD Basis Swap (illustrative)**

- Notional exchange at inception (EUR notional for USD notional at spot)
- Floating EUR leg pays EURIBOR + basis spread
- Floating USD leg pays SOFR (flat, no spread — USD conventionally the flat leg)
- Re-exchange of notionals at maturity at the *original* spot rate (not the prevailing spot), which reintroduces FX risk on the notional exchange unless separately hedged — though this is standard market convention and does not undermine the swap's core rate-differential function

### CIP vs. Uncovered Interest Rate Parity (UIP)

| Aspect | CIP | UIP |
| --- | --- | --- |
| FX risk | Fully hedged via forward | Unhedged; relies on expected future spot |
| Basis | No-arbitrage identity (mechanical) | Behavioral/expectational hypothesis |
| Empirical validity (pre-2008) | Held closely for major pairs | Widely rejected empirically ("forward premium puzzle") |
| Empirical validity (post-2008) | Persistent basis deviations documented | Still widely rejected; unrelated failure mode |

UIP posits:

$$E[S_T] = S_0 \cdot \frac{1 + r_d T}{1 + r_f T}$$

i.e., that the forward rate is an unbiased predictor of the future spot rate. This has been extensively rejected empirically — the **forward premium puzzle** (Fama, 1984) documents that currencies with higher interest rates tend to *appreciate* rather than depreciate as UIP would predict, the opposite sign to the naive prediction, motivating the enormous FX carry trade literature. This is a separate and independent phenomenon from CIP basis deviations — CIP concerns hedged, riskless relationships; UIP concerns unhedged, risk-bearing expectations.

### Relationship to FX Forward Pricing in Practice

**Key Points**

- In practice, dealers do not compute forwards from first-principle interest rates; forward points are themselves directly quoted, liquid market instruments (especially for major pairs), often more liquid than the underlying money-market instruments
- The implied deposit/repo rate backed out from FX forward points is frequently used as a proxy for offshore funding costs in a given currency, particularly for currencies with less liquid or restricted onshore money markets (e.g., CNY, where CNH forward points are a key funding-cost signal)
- For emerging market currencies, forward points can reflect not just interest differentials but also capital controls, convertibility risk, and NDF (non-deliverable forward) market segmentation

### Non-Deliverable Forwards (NDFs) and CIP

For currencies with capital controls or limited convertibility (e.g., historically CNY, INR, KRW, BRL), **Non-Deliverable Forwards** settle in cash (typically USD) based on the difference between the contracted forward rate and a fixing rate at maturity, rather than physical currency exchange. Because NDF markets are offshore and segmented from onshore money markets, CIP-implied rates from NDF points can diverge meaningfully from onshore interest rates — this divergence is itself a traded and monitored signal of capital control effectiveness and offshore currency sentiment.

### Illustration: CIP No-Arbitrage Relationship

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 380" font-family="sans-serif">
<text x="350" y="25" text-anchor="middle" font-size="16" font-weight="bold">Covered Interest Rate Parity: Two Equivalent Paths (svg_diagram)</text>

<rect x="40" y="60" width="160" height="50" rx="6" fill="#eaf2f8" stroke="#2980b9" stroke-width="1.5" />
<text x="120" y="90" text-anchor="middle" font-size="13">1 unit Domestic</text>
<rect x="500" y="60" width="160" height="50" rx="6" fill="#eaf2f8" stroke="#2980b9" stroke-width="1.5" />
<text x="580" y="82" text-anchor="middle" font-size="13">(1 + r_d T)</text>
<text x="580" y="98" text-anchor="middle" font-size="11">Domestic units</text>
<line x1="200" y1="85" x2="500" y2="85" stroke="#2980b9" stroke-width="2" marker-end="url(#arrow1)" />
<text x="350" y="75" text-anchor="middle" font-size="12" fill="#2980b9">Invest at r_d for T</text>

<rect x="40" y="260" width="160" height="50" rx="6" fill="#fdedec" stroke="#c0392b" stroke-width="1.5" />
<text x="120" y="282" text-anchor="middle" font-size="13">1/S₀ units Foreign</text>
<text x="120" y="298" text-anchor="middle" font-size="11">(convert at spot S₀)</text>
<rect x="270" y="260" width="160" height="50" rx="6" fill="#fdedec" stroke="#c0392b" stroke-width="1.5" />
<text x="350" y="282" text-anchor="middle" font-size="13">(1/S₀)(1 + r_f T)</text>
<text x="350" y="298" text-anchor="middle" font-size="11">Foreign units</text>
<rect x="500" y="260" width="160" height="50" rx="6" fill="#fdedec" stroke="#c0392b" stroke-width="1.5" />
<text x="580" y="282" text-anchor="middle" font-size="13">× F_T (forward)</text>
<text x="580" y="298" text-anchor="middle" font-size="11">→ Domestic units</text>
<line x1="120" y1="260" x2="120" y2="115" stroke="#7f8c8d" stroke-width="1.5" stroke-dasharray="3,3" />
<line x1="200" y1="285" x2="270" y2="285" stroke="#c0392b" stroke-width="2" marker-end="url(#arrow2)" />
<text x="235" y="275" text-anchor="middle" font-size="11" fill="#c0392b">Invest at r_f</text>
<line x1="430" y1="285" x2="500" y2="285" stroke="#c0392b" stroke-width="2" marker-end="url(#arrow2)" />
<text x="465" y="275" text-anchor="middle" font-size="10" fill="#c0392b">Forward @ t=0</text>

<line x1="580" y1="115" x2="580" y2="255" stroke="black" stroke-width="1.5" stroke-dasharray="5,5" />
<text x="600" y="185" font-size="16" font-weight="bold">=</text>
<text x="350" y="210" text-anchor="middle" font-size="13" font-weight="bold" fill="black">No-arbitrage forces equal terminal payoffs</text>
</svg>

### Worked Example

Given:

- Spot EUR/USD: $S_0 = 1.0850$ (USD per EUR)
- USD rate ($r_d$, e.g., SOFR-based): $5.30\%$
- EUR rate ($r_f$, e.g., €STR-based): $3.65\%$
- Maturity: $T = 0.5$ years (6 months)

CIP-implied forward:

$$F_T = 1.0850 \times \frac{1 + 0.0530 \times 0.5}{1 + 0.0365 \times 0.5} = 1.0850 \times \frac{1.0265}{1.01825} \approx 1.0938$$

Forward points $\approx 1.0938 - 1.0850 = 0.0088$, or roughly $88$ pips (using standard 4-decimal EUR/USD pip convention), reflecting the USD's higher interest rate — EUR trades at a forward premium against USD, consistent with the higher domestic ($r_d$, USD) rate relative to the foreign ($r_f$, EUR) rate.

If the actual market-quoted forward were instead $1.0955$, the implied EUR funding rate embedded in the FX market would be lower than the quoted €STR-based rate, revealing a negative cross-currency basis — it would be "cheaper" (in implied-rate terms) to fund EUR via the FX swap market than via a direct EUR deposit, a pattern consistent with the well-documented structural USD demand described above.

### Related Topics

**Related Topics**

- Uncovered Interest Rate Parity and the Forward Premium Puzzle
- Cross-Currency Basis Swaps: Structure, Quoting Conventions, and Risk
- FX Forward and Swap Points: Market Conventions and Quoting
- Non-Deliverable Forwards (NDFs) and Offshore Currency Markets
- FX Carry Trade Strategies and Risk Premia
- Multi-Curve Discounting Frameworks (OIS Discounting, Collateral CSA Impact on Forward Pricing)
- Regulatory Capital Impact on Dealer Balance Sheets (Basel III Leverage Ratio, SLR)