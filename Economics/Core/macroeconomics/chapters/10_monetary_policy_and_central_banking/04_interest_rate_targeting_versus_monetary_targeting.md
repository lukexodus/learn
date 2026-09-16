## Interest Rate Targeting Versus Monetary Targeting

### Overview and the Core Policy Choice

Central banks implementing monetary policy must choose an **operating framework** — a specific variable they will actively steer in the short run to achieve their ultimate goals (price stability, employment, and so on). Historically, this choice has centered on two broad alternatives: targeting a short-term **interest rate** or targeting a **monetary aggregate** (the money supply, or a component of it). This choice is a specific instance of the more general **instrument problem** in monetary policy — the central bank cannot simultaneously fix both an interest rate and a monetary quantity independently, because the two are linked through the money market.

**Key Points**

- The central bank cannot pursue both targets simultaneously and independently in the short run: a given money supply level is consistent with only one equilibrium interest rate at any given level of money demand, and vice versa
- The choice between the two frameworks has historically depended on views about the relative stability of money demand (and by extension, the velocity of money) versus the reliability of interest rates as an indicator of policy stance
- Most major central banks have converged on interest rate targeting as their operational framework since the 1980s and 1990s, though monetary targeting retains historical and analytical importance and periodic renewed interest

### The Underlying Constraint: The Money Market Model

The choice between the two targets can be understood through the standard money market equilibrium diagram, where the money supply is (in simplified textbook treatment) vertical (centrally controlled) and money demand slopes downward in the interest rate:

$$M^s = M^d(i, Y)$$

If the central bank fixes the money supply at a specific level, the equilibrium interest rate is determined endogenously by the intersection with money demand — and will fluctuate as money demand shifts (due to changes in income, financial innovation, or portfolio preferences). Conversely, if the central bank fixes the interest rate, it must supply whatever quantity of money is needed to sustain that rate at any given level of money demand — and the money supply itself becomes the endogenously determined variable.

### Diagram: Money Market Under the Two Targeting Regimes

```mermaid
flowchart TD
    A[Money Demand Md = f(i, Y)] --> B{Central Bank Choice}
    B -->|Fix Money Supply Ms| C[Interest rate i determined endogenously]
    B -->|Fix Interest Rate i| D[Money Supply Ms adjusts endogenously]
    C --> E[Money demand shifts cause interest rate volatility]
    D --> F[Money demand shifts absorbed via money supply changes]
    E --> G[Monetary Targeting Regime]
    F --> H[Interest Rate Targeting Regime]
```

### Monetary Targeting

#### Definition and Rationale

Under monetary targeting, the central bank sets an explicit target growth rate (or target range) for a chosen monetary aggregate (e.g., M1 or M2) and conducts open market operations to keep actual money growth within that target path, allowing short-term interest rates to fluctuate as needed to accommodate shifts in money demand.

#### Theoretical Foundation: Monetarism and the Quantity Theory

Monetary targeting is closely associated with **monetarism**, particularly the work of Milton Friedman, which rests on the quantity theory identity:

$$MV = PY$$

If velocity ($V$) is assumed stable and predictable, controlling the growth rate of the money supply directly controls the growth rate of nominal GDP (and, given real output determined by supply-side factors in the long run, the inflation rate). This underpins Friedman's proposed **k-percent rule**: growing the money supply at a fixed, low, pre-announced rate matching the long-run growth rate of real output, removing monetary policy discretion entirely to avoid destabilizing activist intervention.

**Key Points**

- Monetary targeting's practical viability depends critically on the empirical stability of velocity/money demand — if velocity is unstable, a stable money growth target no longer reliably produces stable nominal GDP or inflation outcomes
- Historical experience (particularly the breakdown of stable US M1 velocity beginning in the early 1980s, following financial deregulation) substantially undermined confidence in monetary targeting as a practical operating framework for major advanced economy central banks
- The Bundesbank (pre-euro German central bank) and, to varying degrees, other European central banks in the 1970s–1990s pursued forms of monetary targeting with more sustained (though not unqualified) success than the US experience, partly attributed to relatively more stable German money demand during that period [Unverified: comparative assessments of relative monetary targeting success across countries and periods vary across the economic literature and depend on methodology]

#### Advantages of Monetary Targeting

- **Rapid data availability**: Monetary aggregate data is typically available with a very short lag (often weekly), compared to output and price data that may be available only monthly or quarterly with additional revision lags
- **Reduces discretion, supports credibility**: A pre-announced, rule-based money growth target can, in principle, reduce time-inconsistency-driven inflationary bias by constraining discretionary intervention
- **Clear intermediate target for accountability**: The public and markets can readily verify whether the central bank is meeting its stated money growth objective

#### Disadvantages of Monetary Targeting

- **Requires stable velocity/money demand**: The central mechanism fails if velocity is volatile or subject to structural breaks, as demonstrated by the US M1 experience in the 1980s
- **Choice of aggregate is contestable**: Different monetary aggregates (M1, M2, M3) can send conflicting signals about the appropriate policy stance at the same point in time, undermining the framework's clarity
- **Interest rate volatility as a side effect**: Strict adherence to a money growth target, allowing interest rates to fluctuate freely to accommodate money demand shifts, can produce substantial and potentially destabilizing interest rate volatility

### Interest Rate Targeting

#### Definition and Modern Predominance

Under interest rate targeting, the central bank sets an explicit target level (or narrow target range) for a specific short-term interest rate (e.g., the federal funds rate in the United States, the main refinancing rate in the Eurozone) and conducts open market operations as needed to keep the actual market rate at or near that target, allowing the money supply to expand or contract endogenously as required.

**Key Points**

- This is the dominant operational framework among virtually all major advanced economy central banks today (Federal Reserve, European Central Bank, Bank of England, Bank of Japan, and most inflation-targeting central banks globally)
- Interest rate targets are typically set and reviewed at regularly scheduled policy meetings (e.g., FOMC meetings roughly every six weeks in the US), providing a clear, communicable, and market-observable signal of the current policy stance
- Since the 2008 crisis, most such central banks have operated under an "ample reserves" framework in which the interest rate target is achieved primarily via administered rates (interest on reserve balances, overnight facilities) rather than active reserve scarcity management, but the target variable remains the interest rate rather than a monetary quantity

#### Advantages of Interest Rate Targeting

- **Interest rates are directly observable and easily communicated**: Financial markets and the public can readily interpret a stated interest rate target, supporting policy transparency and communication
- **More directly tied to spending decisions**: Consumption and investment decisions (mortgage borrowing, business capital expenditure) are influenced more directly and immediately by prevailing interest rates than by the level of a monetary aggregate
- **Avoids the interest rate volatility that pure monetary targeting can generate**: By construction, interest rate targeting stabilizes short-term rates directly, rather than allowing them to fluctuate as a byproduct of a fixed money growth path
- **Does not require money demand/velocity stability**: This framework sidesteps the central vulnerability of monetary targeting, since it does not rely on a stable relationship between the money supply and nominal income

#### Disadvantages of Interest Rate Targeting

- **Requires distinguishing nominal from real rates**: A given nominal interest rate target can represent very different real policy stances depending on inflation expectations; failing to adjust the nominal target appropriately as inflation expectations shift can lead to inadvertently loose or tight real policy (a phenomenon closely related to historical criticisms of 1970s US monetary policy, where the Federal Reserve arguably kept nominal rates too low relative to rising inflation expectations, resulting in a persistently negative or insufficiently positive real policy rate)
- **Data/measurement lags in judging the "correct" rate**: Setting the appropriate interest rate level requires real-time judgment about the natural/neutral rate of interest, output gaps, and inflation expectations, all of which are estimated with uncertainty and subject to revision
- **Potential for delayed recognition of a shift in the underlying policy stance**: Since money supply changes are absorbed passively, this framework can obscure information about whether the actual policy stance is becoming more or less accommodative in real terms, without careful, ongoing analytical judgment by the central bank

### The Nominal vs. Real Interest Rate Distinction

A critical technical point in evaluating interest rate targeting is the distinction between the nominal target rate and the underlying real rate, given by the (approximate) Fisher equation:

$$i \approx r + \pi^e$$

Where $i$ is the nominal interest rate, $r$ is the real interest rate, and $\pi^e$ is expected inflation.

**Example**

If the central bank holds the nominal policy rate constant at 5% while inflation expectations rise from 2% to 4%, the real policy rate falls from approximately 3% to approximately 1% — representing an unintended loosening of the actual real policy stance, even though the nominal target has not changed. This mechanism is a commonly cited explanation for how nominal interest rate targeting, if not actively adjusted for shifting inflation expectations, can inadvertently amplify rather than dampen inflationary pressure.

**Key Points**

- This distinction underlies the modern practice (and the logic of the Taylor rule and similar policy guides) of adjusting the nominal policy rate more than one-for-one with changes in inflation, to ensure the real rate moves in the intended stabilizing direction — a principle sometimes referred to as satisfying the "Taylor principle"
- Effective interest rate targeting in practice therefore requires continuous judgment about the evolving real rate implications of a given nominal target, rather than simple mechanical rate-setting

### Historical Practice: The US Case Study

The Federal Reserve's operational history illustrates the practical evolution between these frameworks:

- Through the 1970s, the Federal Reserve nominally emphasized monetary aggregate targets (partly under legislative pressure following high inflation), though implementation in practice often blended interest rate smoothing objectives with monetary targets
- From October 1979 to October 1982, under Chairman Paul Volcker, the Federal Reserve adopted a more explicit non-borrowed reserves/monetary targeting operating procedure, deliberately allowing federal funds rate volatility to rise substantially in pursuit of disinflation — a notable historical episode of prioritizing monetary control over interest rate stability
- Since the early-to-mid 1980s, and particularly following the breakdown of stable M1 velocity, the Federal Reserve has operated with the federal funds rate as its primary explicit operating target, a framework that has persisted (with technical implementation changes, notably the post-2008 shift to an ample reserves framework) through the present [Unverified: specific historical dating and characterization of transitional periods can vary somewhat across monetary history sources]

### Comparison Summary

| Dimension | Monetary Targeting | Interest Rate Targeting |
| --- | --- | --- |
| Target variable | Money supply growth rate | Short-term interest rate level |
| Endogenous variable | Interest rate | Money supply |
| Key vulnerability | Requires stable velocity/money demand | Requires distinguishing nominal from real rates |
| Data timeliness | Very rapid (often weekly) | Rapid, but appropriate target level requires judgment about unobservable variables (natural rate, output gap) |
| Modern prevalence among major central banks | Rare as a primary operational target | Dominant |
| Communicability to markets/public | Moderate (requires understanding of monetary aggregates) | High (single, easily interpreted number) |

### Contemporary Relevance and Ongoing Debate

- Interest rate targeting's dominance does not mean monetary aggregates are ignored entirely; central banks continue to monitor money and credit growth as one of many indicators informing overall policy judgment, particularly for gauging financial stability risks or unusual credit expansion
- The extraordinarily rapid M2 growth during 2020–2021, followed by a subsequent slowdown, renewed public and some academic debate about whether monetary aggregates deserve a more prominent role in policy analysis, though the mainstream operational framework among major central banks has not shifted back toward explicit monetary targeting [Inference: the ultimate influence of this renewed debate on future central bank operating framework design is not yet resolved and remains a matter of ongoing academic and policy discussion]
- Some economists continue to advocate monetary-aggregate-informed policy rules as a complement to, rather than a replacement for, interest rate targeting, particularly as a cross-check against pure interest-rate-based approaches during periods of unusual financial conditions [Unverified: the extent of practical adoption of such complementary approaches varies by central bank and is not standardized]

### Next Steps

- The Taylor rule and systematic interest rate policy guides
- Velocity of money and its historical stability/instability
- The Volcker disinflation and 1979–1982 monetary targeting episode
- Fisher equation and the nominal-real interest rate distinction
- Ample reserves operating framework and administered policy rates
- Money demand theories underlying the quantity theory framework
- Central bank communication and forward guidance under interest rate targeting