## Money Creation and the Money Multiplier

### Overview

Money creation describes how the banking system expands the total money supply beyond the base money issued by the central bank. The **money multiplier** is the formal ratio linking the monetary base (M0) to broader money aggregates (M1, M2), quantifying how much new deposit money each unit of new reserves can ultimately support. This topic connects central bank operations directly to the observable stock of money circulating in the economy.

### Two Views of Money Creation

**Key Points**

- **Traditional (multiplier) view**: The central bank sets the level of reserves; banks then multiply those reserves into loans and deposits up to a limit set by the reserve ratio and behavioral leakages. Reserves are treated as the binding constraint that banks must obtain *before* lending.
- **Endogenous money view** (associated with post-Keynesian economics and increasingly acknowledged in central bank publications): Banks extend loans first, creating deposits simultaneously as a matter of double-entry accounting; banks then seek the reserves needed to settle interbank obligations and satisfy reserve requirements *afterward*, often by borrowing them from the central bank or interbank market. Under this view, reserves accommodate lending rather than constrain it in advance.
- Major central banks, including the Bank of England, have published explanations aligning more closely with the endogenous money view, noting that commercial banks create money "by extending credit," with the central bank subsequently supplying reserves as needed. [Fact, though the exact framing and emphasis differ across central bank publications and remains subject to some debate in academic macroeconomics regarding which model best describes practice at a given time.]
- Both views agree on the *outcome* — bank lending expands the money supply — but disagree on the *sequence and causal driver* of that expansion.

### Money Creation via Lending (T-Account Mechanics)

**Example**

When Bank A extends a $10,000 loan to a borrower, the transaction is recorded simultaneously on both sides of the balance sheet:

| Bank A — Assets | Bank A — Liabilities |
| --- | --- |
| Loan to Borrower: +$10,000 | Borrower's Deposit Account: +$10,000 |

No pre-existing pool of "idle savings" is transferred; the deposit is newly created by the act of lending. The bank's reserve position becomes relevant only when the borrower spends the funds and they are transferred to another bank, at which point Bank A must settle that outflow using its reserves (or borrow reserves to do so).

### The Simple Money Multiplier

**Definition**

The simple multiplier expresses the maximum ratio of deposit expansion to an initial injection of reserves, assuming the public holds no currency and banks hold no excess reserves:

$$m_{simple} = \frac{1}{rr}$$

where $rr$ is the required reserve ratio.

$$\Delta M = m_{simple} \times \Delta \text{Reserves}$$

**Example**

If $rr = 0.10$ and the central bank injects $1 million in new reserves via an open market purchase:

$$\Delta M = \frac{1}{0.10} \times \$1{,}000{,}000 = \$10{,}000{,}000$$

### The Realistic Money Multiplier

**Definition**

Incorporating two behavioral leakages — the public's preference for holding currency and banks' voluntary excess reserves — produces a more realistic multiplier:

$$m = \frac{1 + c}{rr + c + e}$$

where:

- $c = \dfrac{\text{Currency}}{\text{Deposits}}$ (currency drain ratio)
- $rr$ = required reserve ratio
- $e = \dfrac{\text{Excess Reserves}}{\text{Deposits}}$ (excess reserve ratio)

**Key Points**

- As $c$ rises (public holds more cash relative to deposits), the multiplier falls, because cash withdrawn from circulation cannot be relent by banks.
- As $e$ rises (banks hold reserves beyond the requirement — common when loan demand is weak, borrower risk is elevated, or interest on reserves makes holding them attractive), the multiplier also falls.
- The **empirically observed multiplier** is calculated directly from published data:

$$m_{observed} = \frac{M1 \text{ or } M2}{M0}$$

- During the 2008–2009 financial crisis and the 2020 pandemic period, observed multipliers in several major economies fell sharply as banks accumulated large excess reserves despite massive central bank reserve injections (quantitative easing), illustrating the gap between the simple formula and realized outcomes. [Fact regarding the general pattern; specific multiplier values are time-, country-, and dataset-dependent and should be checked against current central bank statistical releases for precision.]

### Money Creation Flow and Multiplier Effect

```mermaid
flowchart TD
    A["Central Bank Reserve Injection (ΔReserves)"] --> B[Bank receives reserves]
    B --> C{Allocate reserves}
    C -->|Required reserves: rr × Deposit| D[Held as Reserves]
    C -->|Excess: (1-rr) × Deposit| E[Available to Lend]
    E --> F[New Loan Extended = New Deposit Created]
    F --> G{Borrower spends funds}
    G -->|Some retained as cash: leakage c| H[Currency Drain - reduces multiplier]
    G -->|Remainder redeposited| I[New Deposit at Another Bank]
    I --> B
    D --> J{Bank holds more than required?}
    J -->|Yes: excess e| K[Excess Reserves - reduces multiplier]
    J -->|No| L[Fully Loaned Reserves]
```

### Deriving the Multiplier Formula

**Step-by-step derivation**

Starting from the definitions of the monetary base and broad money in terms of currency ($C$) and deposits ($D$):

$$M0 = C + R \quad \text{(currency + total reserves)}$$



$$M1 = C + D \quad \text{(currency + deposits)}$$

Total reserves consist of required reserves plus excess reserves:

$$R = rr \times D + e \times D = (rr + e)D$$

Substituting into M0:

$$M0 = C + (rr + e)D$$

Dividing M1 by M0:

$$\frac{M1}{M0} = \frac{C + D}{C + (rr+e)D}$$

Dividing numerator and denominator by $D$, and using $c = C/D$:

$$m = \frac{M1}{M0} = \frac{c + 1}{c + rr + e}$$

This confirms the multiplier formula presented earlier, derived directly from the accounting identities of the two aggregates.

### Worked Numerical Example

**Example**

Given the following data for an economy:

- Required reserve ratio, $rr = 0.10$
- Currency-to-deposit ratio, $c = 0.20$
- Excess-reserve-to-deposit ratio, $e = 0.05$

Compute the money multiplier:

$$m = \frac{1 + 0.20}{0.10 + 0.20 + 0.05} = \frac{1.20}{0.35} \approx 3.43$$

If the central bank increases the monetary base by $5 billion:

$$\Delta M1 = 3.43 \times \$5\text{B} \approx \$17.15\text{B}$$

Compare this to the simple multiplier ($1/rr = 10$), which would have implied a far larger $50 billion expansion — illustrating how behavioral leakages substantially dampen real-world money creation relative to the textbook maximum.

### Limits on Money Creation

**Key Points**

- **Regulatory capital requirements**: Even with ample reserves, banks cannot expand lending indefinitely without sufficient capital to absorb potential loan losses (Basel III capital adequacy rules).
- **Loan demand**: Money creation via lending requires creditworthy borrowers willing to take on debt; reserves alone do not create loans without corresponding demand.
- **Interest on reserves**: When central banks pay competitive interest on reserve balances, banks may prefer holding reserves over expanding risk-bearing loans, dampening the multiplier.
- **Risk assessment and underwriting standards**: Banks' internal risk management and regulatory stress-testing constrain how aggressively they expand credit, independent of reserve availability.

### Quantitative Easing and the Multiplier

**Key Points**

- Quantitative easing (QE) expands M0 by having the central bank purchase assets (typically government bonds) from banks or the public, crediting the sellers' bank reserve accounts.
- QE does **not** mechanically produce a proportional increase in M1/M2; the actual effect depends on whether banks lend out the resulting reserves or simply hold them.
- Post-2008 experience across multiple advanced economies showed large-scale QE accompanied by comparatively modest M2 growth and low realized multipliers, prompting revisions to how economists model the transmission from base money to broad money. [Fact regarding the general pattern observed across several QE episodes; precise multiplier and growth figures vary by country and period and should be verified against contemporaneous central bank data if cited for a specific case.]

### Common Pitfalls

- Treating the simple multiplier ($1/rr$) as an accurate real-world estimate rather than a theoretical ceiling.
- Assuming reserves must exist *before* a bank can make a loan (the "loanable funds" framing), when many central bank descriptions of modern banking place deposit creation and lending as simultaneous, with reserve-seeking occurring afterward.
- Ignoring the currency drain ($c$) and excess reserves ($e$) terms, both of which materially move the multiplier away from $1/rr$ in observed data.
- Assuming QE-driven reserve expansion automatically causes proportional inflation or M2 growth, without accounting for bank lending behavior as the actual transmission channel.

**Related Topics**

- Money Supply Definitions: M0, M1, M2
- The Banking System and Fractional Reserve Banking
- Central Bank Tools: Open Market Operations, Reserve Requirements, Interest on Reserves
- Quantitative Easing: Mechanics and Transmission Channels
- Endogenous Money Theory vs. Loanable Funds Theory
- The Quantity Theory of Money and the Equation of Exchange
- Basel III Capital Adequacy and Its Effect on Credit Creation