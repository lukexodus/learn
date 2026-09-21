## Snowball and Accumulator Structures


### Overview

Snowball and Accumulator structures represent two distinct families of exotic payoffs unified by a common theme: **payoff accumulation contingent on repeated favorable price observations**. Snowball notes are autocallable-family instruments with escalating, memory-based coupons that compound ("snowball") with each missed-then-recovered observation. Accumulators (also called "target redemption" or, in FX/equity, "shark fin accumulators" and "TARN" — Target Accrual Redemption Notes) allow the holder (or issuer, depending on structure) to accumulate shares/units at a favorable price over a schedule, subject to knock-out conditions or a target accrual cap. Both are strongly path-dependent, discretely-monitored exotics with significant model risk concentrated in the joint distribution of periodic observations.

---

### Snowball Structures

#### Structural Definition

A Snowball is an autocallable-family note in which the coupon **escalates with each successive non-call (or missed-coupon) period**, and unpaid coupons carry forward with memory, compounding the effective yield if the note eventually autocalls or reaches maturity favorably. The name reflects the coupon's tendency to "roll up" — growing larger the longer the note survives without triggering.

The generalized coupon accrual at observation $t_i$:

$$\text{Coupon}_i = \left(C_0 + i \cdot \Delta C\right) \times \mathbb{1}\left[S_{t_i} \geq K_i^{C}\right] + \text{Memory}_i$$

where:

- $C_0$ = base coupon rate
- $\Delta C$ = per-period coupon escalation (the "snowball increment")
- $K_i^C$ = coupon/autocall barrier at $t_i$ (frequently step-down, as in standard autocalls)
- $\text{Memory}_i$ = sum of previously unpaid coupons, paid retroactively upon the first subsequent qualifying observation

Upon autocall trigger at $t_i$ (condition $S_{t_i} \geq K_i^{AC}$), the note redeems paying:

$$\text{Redemption}_i = 100\% \times N_{notional} + \sum_{m \leq i} \text{Coupon}_m^{unpaid, accrued}$$

**Key Points**

- Snowballs are structurally a **superset of the standard step-down autocallable** (see prior chapter item), with two additions: (1) an escalating rather than flat coupon rate, and (2) a memory feature that is near-universal in Snowball products (versus optional in generic autocalls).
- Popularized primarily in **Asia-Pacific retail and private banking markets** (notably mainland China, where "snowball" or "xuěqiú" (雪球) products on the CSI 500/1000 indices became a large and, at times, systemically discussed retail product category), though structurally equivalent products exist globally under other naming conventions.
- The escalating coupon schedule directly compensates the investor for **extending the effective duration risk** — each period the note fails to call, remaining exposure to the terminal downside knock-in barrier persists, so the increasing coupon is priced to offset the growing tail risk being carried.
- Most Snowball structures embed a **knock-in downside barrier** (commonly monitored continuously or daily-close, at 70-80% of initial level) that, if breached at any point during the life, converts the terminal payoff from principal-protected to directly linked to $S_T/S_0$ (frequently *without* a corresponding cap on the loss, unlike the coupon side which is capped by the escalating schedule).

#### Worked Example — Coupon Escalation with Memory

3-year Snowball, monthly observations (simplified to quarterly here for illustration), $C_0 = 12\%$ p.a., $\Delta C = 2\%$ p.a. per quarter survived, coupon/autocall barrier flat at 100% of $S_0$, continuous downside knock-in barrier at 75%.

| Quarter | Coupon Barrier | $S_{t_i}/S_0$ | Coupon Paid | Memory Carried |
| --- | --- | --- | --- | --- |
| Q1 | 100% | 97% | Missed | 12% carried |
| Q2 | 100% | 102% | 14% (base) + 12% (memory) = 26% | — |
| Q3 | 100% | 105% | **Autocall triggers**: redeem 100% + 16% coupon | — |

Total coupon realized: $26\% + 16\% = 42\%$ over 3 quarters — the memory and escalation features compound sharply once the underlying recovers above barrier, which is the defining "snowball" characteristic (accumulated potential energy released on the first qualifying observation).

**Key Points**

- The escalation schedule ($\Delta C$ per period) means the *expected value* of the coupon leg is highly convex in the underlying's realized path — long periods of near-barrier oscillation before eventual autocall maximize the memory-accrued payout, making the structure's pricing acutely sensitive to the **autocorrelation structure of the underlying's returns** (mean-reverting versus trending dynamics materially change expected accrual), not just marginal volatility.
- [Inference] Because Chinese-market Snowball products are frequently written on broad indices with embedded daily-monitored knock-in barriers, aggregate delta-hedging flow from issuing banks around clustered barrier levels has been cited in market commentary as a contributor to index-level volatility during sharp drawdowns; this is a market-structure observation about hedging flow dynamics rather than a property of the payoff formula itself, and specific episodes should be verified against contemporaneous reporting rather than treated as a standing structural fact.

#### Pricing Approach

Snowball pricing extends the autocallable backward-induction framework (see prior chapter item) with an additional state variable tracking **accrued unpaid coupon** at each node, since the payoff is no longer Markovian in spot alone:

$$V_i(S, M) = \begin{cases} 100\% + C_i(M) & \text{if } S \geq K_i^{AC} \\ e^{-r\Delta t}\,\mathbb{E}\left[V_{i+1}(S_{t_{i+1}}, M')\right] & \text{otherwise} \end{cases}$$

where $M$ is accrued memory coupon and $M'$ updates according to whether the coupon barrier was cleared at $t_i$. This expands the state space of the lattice/PDE grid by one dimension (spot × accrued memory), or, more commonly in practice, is priced via **Monte Carlo** since the memory state is naturally path-dependent and easily tracked per simulated path without discretizing a memory-value grid.

---

### Accumulator Structures

#### Structural Definition

An Accumulator (full name commonly **KODA** — Knock-Out Discount Accumulator, in equity markets; or **TARN** — Target Accrual Redemption Note, in FX/rates markets) is a structure under which the holder commits to **accumulate a fixed quantity of the underlying (or a fixed notional accrual) at a discounted forward price**, on a regular schedule (typically daily or weekly), for the life of the contract — subject to an **early knock-out** if the underlying trades above a specified level.

The generic daily/periodic accrual mechanic:

$$\text{Accrual}_i = \begin{cases} Q \times (S_{ref} - K) & \text{if } S_{t_i} \geq K \ (\text{standard accrual}) \\ 2Q \times (S_{ref} - K) & \text{if } S_{t_i} < K \ (\text{"double-down" / gearing on breach}) \\ 0, \text{contract terminates} & \text{if } S_{t_i} \geq KO \ (\text{knock-out}) \end{cases}$$

where:

- $Q$ = fixed quantity accumulated per observation
- $K$ = strike (discounted purchase/accrual price, below current spot at inception)
- $KO$ = knock-out barrier (above current spot, typically 3-10% OTM)
- $S_{ref}$ = reference/settlement price at observation $t_i$

**Key Points**

- Accumulators are **short-optionality-to-the-issuer, long-optionality-to-the-holder-with-embedded-risk** structures — the holder effectively **sells a strip of daily/weekly put options** to the counterparty bank (typically the issuing/structuring desk), receiving a discount to market price in exchange, while simultaneously being **short a call at the knock-out level**, capping upside participation.
- The "double-down" or "gearing" feature (common in KODA structures, notorious in equity accumulator products, particularly around the 2008 Asian retail "I'll Kill You Later" (a colloquial market nickname reflecting KODA's acronym and the products' notoriety) episode) obligates the holder to accumulate **double the quantity** when the underlying trades below strike — this creates strongly convex, asymmetric downside exposure: losses accelerate exactly when the underlying is falling, a structurally dangerous feature for unsophisticated holders during sharp drawdowns.
- Unlike Snowballs (autocallable-family, typically retail income products with principal protection unless a downside barrier is separately breached), Accumulators are **forward-commitment structures** — the holder has an ongoing obligation to transact (buy shares, or settle cash-equivalent) at each observation date for the life of the contract, making them economically closer to a **strip of daily forward contracts with embedded short puts and a knock-out call**, rather than a coupon-bearing note.
- Target Accrual Redemption Notes (TARN) in the interest rate/FX derivative space use a related but distinct mechanic: the note **terminates once cumulative accrued coupon reaches a target level** (rather than terminating on a knock-out spot level), converting the redemption trigger from a spot-barrier condition into a **cumulative-payoff condition**.

#### Payoff Decomposition — KODA Accumulator

Per observation date, the holder's position is equivalent to:

$$\text{Holder P\&L}_i = Q \times \max(S_{t_i} - K, 0) \ [\text{long forward-like exposure above strike, capped by knock-out}] - 2Q \times \max(K - S_{t_i}, 0) \ [\text{short leveraged put below strike}]$$

This replicates as: **long $Q$ vanilla calls struck at $K$** (extinguished at knock-out $KO$, i.e., effectively a call spread or knocked-out call) **minus short $2Q$ vanilla puts struck at $K$**, repeated across every observation date in the schedule — a strip of daily/weekly digital-notional risk reversals with an asymmetric 1:2 quantity ratio favoring the bank's short-put collection.

**Key Points**

- Because the structure is **knocked out entirely** (all future accruals cease) once $S_{t_i} \geq KO$, the total accumulated quantity is uncertain at inception — ranging from near-zero (if knocked out on day one) to the full contractual notional over the entire tenor (if the underlying stays within $[K, KO]$ for the full schedule), making **total delivered notional itself a random variable requiring simulation to characterize**, not just the payoff conditional on a fixed notional.
- Accumulators are frequently marketed as providing "discount" or "enhanced yield" access to an underlying the investor wants to acquire anyway (common in pre-IPO or concentrated-stock-position unwind contexts), but the embedded 2x geared put materially changes the risk profile versus simply buying the underlying outright or via a costless collar.

#### Structural Diagram — Accumulator Zones

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 760 300" font-family="Helvetica, Arial, sans-serif">
<text x="380" y="22" text-anchor="middle" font-size="15" font-weight="bold" fill="#1a1a1a">Accumulator (KODA) Payoff Zones (svg_diagram)</text>
<line x1="60" y1="220" x2="700" y2="220" stroke="#333" stroke-width="1.5" />
<text x="700" y="240" text-anchor="end" font-size="11" fill="#333">Underlying Price S_t</text>
<line x1="150" y1="60" x2="150" y2="220" stroke="#888" stroke-dasharray="4,3" />
<text x="150" y="245" text-anchor="middle" font-size="10" fill="#333">Strike K</text>
<line x1="560" y1="60" x2="560" y2="220" stroke="#cc3333" stroke-dasharray="4,3" />
<text x="560" y="245" text-anchor="middle" font-size="10" fill="#a01818">Knock-Out KO</text>
<rect x="60" y="60" width="90" height="160" fill="#ffd6d6" opacity="0.6" />
<text x="105" y="100" text-anchor="middle" font-size="10" fill="#a01818">Below K:</text>
<text x="105" y="115" text-anchor="middle" font-size="10" fill="#a01818">2x geared</text>
<text x="105" y="130" text-anchor="middle" font-size="10" fill="#a01818">accrual</text>
<text x="105" y="145" text-anchor="middle" font-size="10" fill="#a01818">(double-down)</text>
<rect x="150" y="60" width="410" height="160" fill="#d6ffd6" opacity="0.6" />
<text x="355" y="100" text-anchor="middle" font-size="10" fill="#2e6b2e">Between K and KO:</text>
<text x="355" y="115" text-anchor="middle" font-size="10" fill="#2e6b2e">Standard accrual</text>
<text x="355" y="130" text-anchor="middle" font-size="10" fill="#2e6b2e">at quantity Q</text>
<text x="355" y="145" text-anchor="middle" font-size="10" fill="#2e6b2e">per observation</text>
<rect x="560" y="60" width="140" height="160" fill="#e0e0e0" opacity="0.7" />
<text x="630" y="100" text-anchor="middle" font-size="10" fill="#444">Above KO:</text>
<text x="630" y="115" text-anchor="middle" font-size="10" fill="#444">Contract</text>
<text x="630" y="130" text-anchor="middle" font-size="10" fill="#444">knocked out</text>
<text x="630" y="145" text-anchor="middle" font-size="10" fill="#444">no further accrual</text>
</svg>

---

### Comparative Summary

| Dimension | Snowball | Accumulator (KODA/TARN) |
| --- | --- | --- |
| Product family | Autocallable / cliquet-coupon note | Forward-commitment / strip of geared risk reversals |
| Holder obligation | None beyond initial purchase (note) | Ongoing periodic commitment to transact |
| Coupon/accrual dynamic | Escalating, memory-based | Flat per-period, but gearing shifts with spot |
| Termination trigger | Autocall barrier cleared (favorable) | Knock-out barrier cleared (favorable, but ends upside participation) |
| Downside character | Knock-in barrier converts to linear loss at maturity | Immediate 2x geared accrual below strike, ongoing |
| Total notional at inception | Fixed (note principal) | Uncertain — depends on realized path length before knock-out |
| Typical venue | Retail/private banking notes, index-linked | Equity accumulators (single stock), FX/rates TARN |

---

### Pricing and Hedging Commonalities

**Key Points**

- Both structures require **path-dependent simulation** (Monte Carlo, typically) because payoff/accrual at each date depends on the full trajectory of prior observations (memory state for Snowball; cumulative accrued notional and knock-out status for Accumulator) — neither reduces to a closed-form or simple backward-induction lattice without expanding the state space.
- **Autocorrelation and mean-reversion sensitivity**: Both structures are more sensitive to the underlying's **path character** (trending vs. mean-reverting, clustering of returns) than plain vanilla or single-barrier exotics, since the payoff depends on the joint/sequential pattern of observations relative to the barrier, not just the terminal or single-touch distribution.
- **Delta-hedging complexity near barriers**: Both create large, discontinuous delta/gamma exposure for the issuing desk around barrier levels as observation dates approach — for Accumulators, this recurs at **every** observation date across the full schedule (daily/weekly), producing persistent, high-frequency gamma risk management burden versus the comparatively sparse observation schedule of typical Snowball/autocall notes (monthly/quarterly).
- **Skew and smile dependency**: The embedded short-put (Accumulator) or short-digital-at-barrier (Snowball) components are priced primarily off the **low-strike/low-barrier region of the volatility surface**, making both structures materially mispriced under flat-volatility assumptions and requiring a properly calibrated smile model (local volatility, stochastic-local volatility) for reliable Greeks.

**Related Topics**

- Autocall trigger mechanics and step-down barrier calibration (see prior item)
- Target Accrual Redemption Notes (TARN) in FX and interest rate derivatives
- Risk reversal and collar replication for geared accumulator structures
- Longstaff-Schwartz least-squares Monte Carlo for path-dependent state variables
- Volatility skew calibration for low-strike barrier and put-heavy exotics
- Retail structured product suitability and regulatory treatment of geared/leveraged payoffs
- Napoleon and Altiplano payoffs (comparative cliquet/barrier exotic structures)