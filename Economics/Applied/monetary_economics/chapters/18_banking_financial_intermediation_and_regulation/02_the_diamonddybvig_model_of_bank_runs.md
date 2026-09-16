## The Diamond-Dybvig Model of Bank Runs


### Definition and Conceptual Foundation

The Diamond-Dybvig model, introduced by Douglas Diamond and Philip Dybvig in their 1983 paper "Bank Runs, Deposit Insurance, and Liquidity," provides the canonical formal framework for understanding two intertwined phenomena: (1) why banks offering demand deposit contracts arise as a welfare-improving response to depositors' privately known, idiosyncratic liquidity needs, and (2) why this same contractual structure creates inherent vulnerability to self-fulfilling bank runs, independent of the underlying quality of the bank's assets.

The model's central achievement is demonstrating that bank runs can occur as a *rational, self-fulfilling equilibrium* — not merely as a consequence of panic, irrationality, or genuinely insolvent banks — establishing a multiple-equilibria framework in which the same fundamentals can support either a "good" equilibrium (banks function normally) or a "bad" equilibrium (a run occurs), with the outcome determined by depositor beliefs about others' behavior rather than by economic fundamentals alone.

### Model Setup

**Agents and Preferences**

The model considers a continuum of ex ante identical depositors, each endowed with one unit of a good at date 0. Depositors face uncertainty about their own consumption timing preference, realized at date 1:

$$U(c_1, c_2) = \begin{cases} u(c_1) & \text{with probability } t \text{ (Type 1: "impatient")} \\ u(c_1 + c_2) \text{ or } \rho \, u(c_2) & \text{with probability } 1-t \text{ (Type 2: "patient")} \end{cases}$$

where $t$ is the fraction of the population that turns out to be impatient (needing to consume at date 1), $u(\cdot)$ is a standard concave utility function, and $\rho$ is a discount factor. Critically, each individual's own type ($1$ or $2$) is **private information**, realized and known only to that individual at date 1 — this informational friction is what prevents depositors from writing complete contingent contracts with each other directly.

**Technology**

A single productive investment technology is available:

- 1 unit invested at date 0 yields 1 unit if liquidated at date 1 (no return, but principal preserved)
- 1 unit invested at date 0 yields $R > 1$ if held to date 2 (productive, illiquid long-term technology)

This creates the fundamental asset-liability mismatch: the productive technology is illiquid (only fully productive at date 2), while a fraction $t$ of depositors need to consume at date 1.

### The Autarky Benchmark and the Case for Risk-Sharing

**Without any intermediary or contract**, each individual would need to decide unilaterally, before knowing their type, how much to invest in the illiquid technology versus hold as a liquid reserve. Because individual liquidity needs are uncertain and privately realized, autarky (each individual self-insuring) is inefficient: an individual holding enough liquid reserves to cover the impatient-state outcome forgoes the higher return $R$ available to patient types, while an individual investing heavily in the illiquid technology risks having to liquidate at a loss if the impatient state is realized.

**The value of pooling**: If a large number of ex ante identical individuals pool their endowments, and the fraction $t$ realized as impatient is (by a law of large numbers argument) known with near-certainty *in aggregate* even though each individual's own type is private, a social planner (or a bank acting as intermediary) can achieve superior risk-sharing by investing $t$ in the liquid technology and $(1-t)$ in the illiquid technology, then offering depositors a demand deposit contract promising a fixed payment $r_1$ if they withdraw at date 1 and a (higher) payment $r_2$ if they wait until date 2:

$$r_1 = 1, \quad r_2 = \frac{R(1-t)}{1-t} = R$$

under the simplest full-pooling case, though the *optimal* (incentive-efficient) contract generally sets $1 < r_1 < r_2$, with $r_1$ set above the pure autarky value to provide superior insurance against being impatient, exploiting risk aversion: because impatient types care only about $c_1$ and patient types can achieve $c_2 > c_1$, the bank contract Pareto-dominates autarky by providing insurance against the privately known liquidity shock that individual capital markets, absent the pooling mechanism, cannot replicate.

### Diagram: Diamond-Dybvig Contract Structure

```mermaid
flowchart TD
    A["N Depositors,<br/>Each with 1 Unit Endowment"] --> B["Deposit with Bank<br/>at Date 0"]
    B --> C["Bank Invests Portfolio:<br/>Fraction in Liquid Asset,<br/>Fraction in Illiquid<br/>Long-Term Technology"]
    D["Date 1: Types Realized<br/>(Privately Known)"] --> E{"Individual is<br/>Impatient or Patient?"}
    E -->|Impatient<br/>probability t| F["Withdraw at Date 1<br/>Receive r1"]
    E -->|Patient<br/>probability 1-t| G["Choice: Withdraw<br/>Now or Wait?"]
    G -->|Wait (Good Equilibrium)| H["Receive r2 > r1<br/>at Date 2"]
    G -->|Withdraw Now<br/>(Run Equilibrium, if<br/>believes others will run)| I["Joins the Run"]
    F --> J["Bank Liquidates<br/>Illiquid Assets<br/>at a Loss if Needed"]
    I --> J
    J --> K{"Sequential Service<br/>Constraint: Assets<br/>Sufficient for All<br/>Claims?"}
    K -->|Fundamentals Sound,<br/>No Run| H
    K -->|Run Depletes Assets<br/>Before All Served| L["Late Withdrawers<br/>Receive Less or<br/>Nothing (Bank Failure)"]
```

### The Multiple Equilibria Result

The model's core theoretical contribution is showing that the simple demand deposit contract described above supports (at least) two Nash equilibria under a **sequential service constraint** (deposits are served on a first-come, first-served basis until the bank's assets are exhausted):

**Equilibrium 1 — The "Good" (No-Run) Equilibrium**: Each patient-type depositor believes all other patient-type depositors will wait until date 2 to withdraw. Given this belief, waiting is individually optimal (since $r_2 > r_1$), the bank's illiquid assets are held to maturity and generate the full return $R$, and the allocation achieves the intended risk-sharing improvement over autarky.

**Equilibrium 2 — The "Bad" (Run) Equilibrium**: Each patient-type depositor believes that *all other* depositors (patient and impatient alike) will attempt to withdraw at date 1. Given this belief, it becomes individually rational for a patient-type depositor to also withdraw immediately at date 1, *even though they have no genuine liquidity need*, because:

$$\text{Expected payoff from waiting (if others run)} < r_1 \text{ (payoff from joining the run now)}$$

The logic is a coordination-failure/bank-run externality: if a depositor believes the bank's assets will be exhausted by other withdrawals before they get served (due to the sequential service constraint and premature liquidation of illiquid assets at a loss), their best response is to withdraw immediately rather than risk receiving nothing (or a reduced pro-rata amount) at date 2. This is a **self-fulfilling prophecy**: the belief that a run will occur makes it individually rational to participate in the run, which in turn causes the run to occur — entirely independent of whether the bank's underlying assets, if held to maturity without a run, would have been sufficient to honor all claims.

$$\text{Panic-based run: } \Pi_{run} \text{ triggered by beliefs alone, not by } R \text{ or asset quality}$$

### Formal Payoff Structure Under Sequential Service

Under the sequential service constraint, if $f$ depositors (a fraction exceeding $t$) attempt to withdraw at date 1, the bank must liquidate illiquid assets prematurely (at the date-1 liquidation value of 1 per unit rather than the date-2 value $R$) to meet these claims. Because premature liquidation destroys value (foregoing $R - 1$ per unit liquidated early), if the run is severe enough, the bank's remaining assets become insufficient to pay even $r_1$ to all who demand it, and depositors served later in the queue receive strictly less — creating the "race to the bank" incentive structure once a run begins.

### Policy Interventions Within the Model

**1. Deposit Insurance**

Diamond and Dybvig's own analysis identifies government-provided deposit insurance as a policy capable of eliminating the bad equilibrium entirely. If depositors are guaranteed to receive the promised $r_1$ or $r_2$ regardless of others' withdrawal behavior (funded, if necessary, by taxation), the incentive to run purely out of fear of others running is removed, since a patient-type depositor's payoff no longer depends on the queue position or others' actions:

$$\text{With full deposit insurance: only the "good" equilibrium survives as a dominant strategy}$$

This result — that deposit insurance can be run-preventing at essentially zero cost *in equilibrium* (since if it successfully deters runs, the insurance fund is never actually called upon in the "good" equilibrium) — is frequently cited as the theoretical foundation for deposit insurance systems such as the FDIC in the United States.

**2. Suspension of Convertibility**

An alternative mechanism analyzed in the original paper: the bank commits ex ante to suspend withdrawals once a pre-specified fraction of deposits (corresponding to the known fraction $t$ of genuinely impatient depositors) has been withdrawn. Since patient-type depositors know that withdrawing after the suspension threshold would be futile (the bank will not honor withdrawals beyond that point until date 2), this removes their incentive to run alongside impatient depositors, though [Inference] this mechanism has the practical limitation of requiring the bank (or regulator) to know the true fraction $t$ accurately in advance, and does not distinguish between illiquidity and genuine insolvency-driven withdrawal demand at the point suspension is triggered.

**3. Central Bank as Lender of Last Resort**

Though not the primary mechanism analyzed in the original 1983 paper, a widely drawn implication of the model is that a central bank willing to lend against the illiquid assets at their fundamental (date-2) value, rather than forcing fire-sale liquidation, can achieve a broadly similar run-prevention effect to deposit insurance, connecting the model directly to the classical Bagehot (1873) lender-of-last-resort doctrine of lending freely against good collateral at a penalty rate during a panic.

### Extensions to the Basic Model

**Global Games and Equilibrium Selection**

A significant critique of the original Diamond-Dybvig framework is that it does not explain *which* equilibrium (good or bad) will actually be selected or what triggers a shift between them — the model is silent on the coordination mechanism itself. Morris and Shin's (2003) global games approach resolves this indeterminacy by introducing a small amount of noise in depositors' private signals about fundamentals, which yields a **unique equilibrium** in which a run occurs if and only if fundamentals fall below a specific threshold — providing a theory of *when* runs occur based on underlying conditions, rather than treating the run/no-run outcome as a matter of unexplained sunspot beliefs.

**Information-Based (Fundamentals-Driven) Runs**

An alternative and complementary strand (e.g., Jacklin and Bhattacharya, 1988; Gorton, 1988) models runs as driven by depositors receiving genuine adverse information about the bank's asset quality, rather than purely self-fulfilling panic — in this view, runs serve an information-revealing or disciplining function, occurring precisely when fundamentals genuinely deteriorate, in contrast to the pure sunspot mechanism of the original model.

[Unverified] The empirical literature on historical bank run episodes has found some support for both mechanisms depending on the specific episode studied (e.g., panic-driven contagion in some cases versus fundamentals-correlated selective runs in others such as during the U.S. banking panics of the Great Depression), and the two mechanisms are not viewed as mutually exclusive.

### Practical Example: Applying the Model to Modern Wholesale Funding Runs

The Diamond-Dybvig logic has been extended well beyond traditional retail demand deposits to explain run dynamics in modern wholesale, short-term funding markets:

1. **Repo market runs (2008 financial crisis)**: Short-term repurchase agreement funding of investment banks exhibited run-like dynamics as counterparties refused to roll over funding amid uncertainty about underlying collateral quality, analogous to the sequential-service/first-mover-advantage logic of the original model, despite the absence of traditional retail demand deposits
2. **Money market fund runs**: Institutional investors in prime money market funds exhibited rapid, run-like redemption behavior during the 2008 crisis (notably following the Reserve Primary Fund "breaking the buck") and again briefly in March 2020, prompting emergency central bank backstop facilities functioning analogously to deposit insurance/lender-of-last-resort mechanisms in the original model's policy toolkit

**Key Points:**

- These modern applications illustrate why the theoretical framework, though originally developed for retail bank deposits, is considered broadly applicable to any financial arrangement exhibiting the core structural features: illiquid underlying assets, demandable/short-term liabilities, and a first-come-first-served (or economically equivalent) payoff structure
- This generalization is central to the "shadow banking" and systemic risk literature's argument that runs are not a phenomenon unique to traditionally regulated, deposit-insured banks, but can emerge in any functionally similar liquidity-transformation arrangement lacking equivalent safeguards

### Comparison of Run-Prevention Mechanisms

| Mechanism | How It Eliminates the Bad Equilibrium | Key Limitation |
| --- | --- | --- |
| Deposit insurance | Removes dependence of individual payoff on others' actions | Introduces moral hazard in bank risk-taking |
| Suspension of convertibility | Makes running futile once threshold reached | Requires accurate knowledge of true liquidity demand $t$; doesn't distinguish illiquidity from insolvency |
| Lender of last resort | Provides liquidity against illiquid assets at fundamental value | Requires central bank ability to value collateral accurately; classic "too big to fail" and moral hazard concerns apply |
| Narrow banking / 100% reserve proposals | Eliminates maturity transformation entirely | Sacrifices the liquidity-insurance welfare gain that motivated intermediation in the first place |

### Critiques and Limitations

- **Equilibrium selection indeterminacy**: The original model does not explain what triggers a shift from the good to the bad equilibrium, a gap substantially addressed by the subsequent global games literature but representing a genuine limitation of the base framework taken alone
- **Abstraction from asset quality**: The model's stark separation between panic-driven and fundamentals-driven runs is a simplification; most real-world episodes plausibly involve elements of both, complicating clean empirical tests of the pure sunspot mechanism
- **Static, three-date structure**: The model's simplicity (three dates, a single asset technology, homogeneous depositors ex ante) is a deliberate abstraction that omits dynamic re-contracting, heterogeneous depositor beliefs evolving over time, and richer asset-side risk, motivating a large subsequent literature of extensions
- **Deposit insurance moral hazard trade-off**: As emphasized in the broader theory of financial intermediation, the model's own preferred solution (deposit insurance) is not costless — it shifts the model's demonstrated fragility problem into the separately significant challenge of managing the risk-taking incentives deposit insurance generates, requiring complementary capital regulation

**Related Topics:**

- Theory of financial intermediation and delegated monitoring (Diamond, 1984)
- Global games and equilibrium selection in coordination failures (Morris-Shin)
- Deposit insurance design and moral hazard
- Lender of last resort doctrine (Bagehot's principles)
- Shadow banking and wholesale funding run dynamics
- Bank capital regulation as a complement to deposit insurance
- Historical banking panics (U.S. National Banking Era, Great Depression)
- Sovereign debt crises and self-fulfilling run dynamics (parallel applications, e.g., Cole-Kehoe)