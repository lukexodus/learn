## Reserves, Excess Reserves, and Interbank Markets


### Overview

Bank reserves — balances that commercial banks hold at the central bank — sit at the operational core of the banking system's liquidity management and the central bank's implementation of monetary policy. The distinction between required and excess reserves, together with the interbank market where banks trade reserves among themselves, determines short-term interest rates and the day-to-day transmission of policy actions into the wider financial system.

### Required vs. Excess Reserves

**Key Points**

- **Required reserves ($RR$)**: the minimum balance a bank must hold, calculated as the required reserve ratio ($r_r$) multiplied by a specified deposit base: $RR = r_r \times D$
- **Excess reserves ($ER$)**: any reserve balances held above the required minimum, held voluntarily by the bank
- Total reserves: $R = RR + ER$

[Unverified] Reserve requirement frameworks differ substantially by country and have shifted considerably over time — for example, the U.S. Federal Reserve reduced reserve requirement ratios to zero for all deposit tiers in March 2020, effectively eliminating binding reserve requirements in that jurisdiction, while other central banks maintain positive reserve requirements; readers should verify the specific framework in force for any jurisdiction and time period of interest.

### Why Banks Hold Excess Reserves

**Key Points**

Banks may hold reserves beyond the legal minimum for several reasons:

1. **Precautionary liquidity management**: to meet unexpected deposit withdrawals or payment obligations without resorting to costly emergency borrowing
2. **Interest on reserves**: when the central bank pays interest on reserve balances (interest on excess reserves, IOER, or interest on reserve balances, IORB), holding reserves earns a safe, riskless return, reducing the opportunity cost of not lending the funds out
3. **Regulatory liquidity requirements**: modern prudential frameworks (e.g., the Basel III Liquidity Coverage Ratio) may separately require banks to hold high-quality liquid assets, of which central bank reserves qualify, creating demand for reserves independent of traditional reserve requirements
4. **Uncertainty about loan quality/demand**: in periods of economic uncertainty or credit market stress, banks may prefer the safety of reserves over extending new loans, even when required reserves are minimal or zero

### The Interbank Market

**Key Points**

- The interbank market (in the U.S., the **federal funds market**; internationally, various overnight unsecured or secured lending markets) is where banks with reserve surpluses lend to banks with reserve deficits, typically on an overnight basis
- Banks with excess reserves beyond their own needs can earn interest by lending to banks that are short, rather than leaving funds idle (if reserves are unremunerated) or facing a shortfall penalty
- The interest rate that emerges from this market — the **federal funds rate** in the U.S., or analogous overnight rates elsewhere (e.g., SONIA in the UK, €STR in the Eurozone) — is a key operational target for many central banks' monetary policy

### Determination of the Interbank Rate

**Key Points**

- In a simple reserve-market model, the interbank rate is determined by the supply and demand for reserves:
  - **Demand for reserves**: downward-sloping in the interbank rate — as the rate rises, the opportunity cost of holding excess reserves increases, so banks demand fewer reserves beyond their requirement
  - **Supply of reserves**: determined by the central bank's balance sheet operations (largely a vertical/fixed supply at a given point in time, set via open market operations)
- Equilibrium occurs where reserve demand equals the reserve supply set by the central bank

### Diagrammatic Representation: Reserve Market Equilibrium (SVG)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 600 400">
<text x="300" y="25" font-size="16" font-weight="bold" text-anchor="middle" fill="#1a1a1a">Reserve Market Equilibrium (svg_diagram)</text>

<line x1="80" y1="340" x2="550" y2="340" stroke="#333" stroke-width="2" />
<line x1="80" y1="340" x2="80" y2="50" stroke="#333" stroke-width="2" />

<text x="315" y="375" font-size="14" text-anchor="middle" fill="`#1a1a1a`">Quantity of Reserves</text>

<text x="35" y="195" font-size="14" text-anchor="middle" fill="`#1a1a1a`" transform="rotate(-90 35 195)">Interbank Rate</text>


<path d="M 130 70 L 480 300" fill="none" stroke="#2563eb" stroke-width="2.5" />
<text x="440" y="290" font-size="12" fill="#2563eb" font-style="italic">Reserve Demand</text>

<line x1="330" y1="60" x2="330" y2="340" stroke="#dc2626" stroke-width="2.5" />
<text x="340" y="80" font-size="12" fill="#dc2626" font-style="italic">Reserve Supply (set by CB)</text>

<circle cx="330" cy="188" r="4" fill="#1a1a1a" />
<line x1="80" y1="188" x2="330" y2="188" stroke="#999" stroke-width="1" stroke-dasharray="3,3" />
<text x="65" y="192" font-size="12" text-anchor="end" fill="#1a1a1a">i*</text>

<line x1="80" y1="270" x2="550" y2="270" stroke="#059669" stroke-width="2" stroke-dasharray="6,4" />
<text x="500" y="264" font-size="11" fill="#059669" font-style="italic">IOER Floor</text>
</svg>

### Corridor and Floor Systems of Rate Control

**Key Points**

Central banks typically implement short-term rate targets using one of two broad frameworks:

**1. Corridor System**

- The central bank sets a **ceiling** (typically a lending facility rate at which banks can always borrow from the central bank) and a **floor** (a deposit facility rate at which banks can always deposit surplus reserves with the central bank)
- The interbank rate is expected to trade within this corridor, since no bank would borrow above the ceiling rate (it can always borrow from the central bank instead) or lend below the floor rate (it can always deposit with the central bank instead)
- Requires the central bank to manage reserve supply relatively precisely (via OMOs) to keep the market rate near the desired target within the corridor

**2. Floor System**

- [Inference] Under a floor system, the central bank supplies reserves abundantly (well beyond what banks need for precautionary or regulatory purposes) and relies on the interest rate paid on reserves (IOER/IORB) to set a floor below which banks have no incentive to lend in the interbank market, since they can earn the same or better return risk-free at the central bank — this approach has been adopted by several major central banks (including the U.S. Federal Reserve since the aftermath of the 2008 financial crisis) as balance sheets expanded significantly through quantitative easing, though implementation details vary by jurisdiction and have evolved with changing reserve levels

### Worked Example: Reserve Shortfall and Interbank Borrowing

**Example**

Bank X ends the day with reserves of $40 million but a required reserve level of $50 million (a $10 million shortfall). Bank Y ends the day with reserves of $70 million against a requirement of $50 million (a $20 million surplus).

Bank X borrows $10 million overnight from Bank Y in the interbank market at the prevailing rate (say 4.25% annualized). The overnight interest cost:

$$\text{Interest} = \$10\text{m} \times \frac{0.0425}{365} \approx \$1{,}164$$

Bank X meets its reserve requirement without needing to borrow from the central bank's (typically more expensive, penalty-priced) discount window; Bank Y earns a return on reserves that would otherwise sit idle (or earn only the IOER rate, if lower than the interbank rate).

### Reserves and the Money Multiplier Connection

**Key Points**

- The reserve-deposit ratio ($rr = r_r + e$, combining required and excess reserve ratios) is a direct input into the money multiplier formula (see Money Multiplier Model), meaning fluctuations in banks' excess-reserve-holding behavior directly affect how much broad money is generated from a given monetary base
- Periods of elevated excess reserve holding (such as during and after the 2008 financial crisis and subsequent QE episodes in several major economies) have historically corresponded with a lower observed money multiplier, as a larger share of the expanded base was held as reserves rather than being lent out and redeposited through the banking system

### Comparison: Reserve Regimes

| Feature | Corridor System | Floor System |
| --- | --- | --- |
| Reserve supply | Scarce, closely managed | Abundant/ample |
| Rate-setting mechanism | Bounded by lending/deposit facility rates | Set primarily by IOER/IORB rate |
| Precision of OMO required | High (frequent fine-tuning) | Lower (large buffer of reserves) |
| Typical association | Pre-crisis conventional policy | Post-QE, large balance sheet environments |

### Criticisms and Practical Complications

- [Inference] The simple reserve supply-and-demand diagram assumes a well-functioning, frictionless interbank market with free arbitrage between reserves and the policy rate; in practice, segmented markets, counterparty credit risk considerations, and balance-sheet costs (e.g., regulatory leverage ratio constraints under Basel III) can cause the effective interbank rate to deviate from the simple textbook equilibrium, as has been documented in various market-stress episodes (e.g., repo market disruptions such as the September 2019 U.S. repo rate spike)
- The transition from corridor to floor systems (and any future reversal as central bank balance sheets normalize) has significant implications for how monetary policy is technically implemented, an area of ongoing evolution in central banking practice that may change further after this material's knowledge cutoff

**Related Topics**

- The money multiplier model
- Central bank balance sheet mechanics
- Interest on excess reserves (IOER/IORB) and its role in rate control
- Corridor vs. floor systems of monetary policy implementation
- Repo markets and short-term secured funding
- Basel III liquidity and capital requirements affecting bank reserve behavior