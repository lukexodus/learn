## Stock and Flow Modeling of Grievance Accumulation and Depletion

### Formal Setup

A stock is a state variable that accumulates or depletes over time via flows; a flow is a rate variable, defined only per unit time, that changes a stock's level. Grievance is modeled as a stock $G(t)$ — an accumulated, integrated quantity of perceived injustice held by a population or subgroup — rather than as a discrete event or a fixed trait. This distinction matters mechanically: events (a massacre, an election fraud) are typically modeled as *shocks to a flow*, not as grievance itself. Grievance is the integral of net injury over time:

$$G(t) = G(0) + \int_0^t \left[ I(\tau) - R(\tau) \right] d\tau$$

where $I(\tau)$ is the inflow rate (injury/injustice accrual) and $R(\tau)$ is the outflow rate (redress/resolution). In discrete-time simulation form, used in most System Dynamics (SD) implementations:

$$G_{t+1} = G_t + \left( I_t - R_t \right)\Delta t$$

This formalism is inherited directly from Jay Forrester's System Dynamics and was applied to conflict specifically in Peter Coleman's "Dynamical Systems Theory" work on intractable conflict and in Track II conflict-modeling literature (e.g., the CASOS/Kathleen Carley school, and Forrester-derived peace-and-conflict SD models from the System Dynamics Society).

### Why Stock-Flow Structure, Not Linear Cause-Effect

A linear causal claim ("Event X caused the uprising") collapses history into a single trigger and cannot explain why *the same magnitude* of event produces war in one context and passes unnoticed in another. Stock-flow structure resolves this: the triggering event is a small flow perturbation, but the *outcome* — whether it crosses a threshold into mobilization — depends on the pre-existing stock level $G_t$. This is the standard SD critique of event-based narrative explanation: behavior is a function of accumulated state, not of the most recent input alone.

### Core Inflows to $G_t$

Each inflow is a rate variable; the sum is the gross injury rate $I_t$.

- **Repression/violence inflow**, $i_1(t)$: physical harm, arbitrary detention, extrajudicial killing. Typically modeled with high per-unit-grievance weight and near-irreversibility (see hysteresis, below).
- **Horizontal inequality inflow**, $i_2(t)$: gap between an identity group's actual share of economic/political goods and its "entitled" share, per Frances Stewart's Horizontal Inequality framework. Modeled as a flow proportional to the *gap*, not the absolute deprivation level — i.e., $i_2(t) = k \cdot \left[ E_{group} - A_{group}(t) \right]$ where $E$ is entitlement (reference-dependent) and $A$ is actual allocation.
- **Relative deprivation inflow**, $i_3(t)$: Ted Gurr's formalization — grievance is driven not by absolute welfare but by the *widening gap* between expected value position (what people believe they deserve, often extrapolated from a recent improving trend) and actual value position. This produces the well-documented "J-curve" mechanism (Davies 1962): rising expectations plus a sudden reversal in actual conditions generate a much larger grievance inflow than stagnant conditions ever would, because the flow term depends on the *derivative* of the expectation-reality gap.
- **Status/identity threat inflow**, $i_4(t)$: perceived delegitimization of group identity, language, or religious practice.
- **Narrative amplification inflow**, $i_5(t)$: a multiplier applied to raw injury flows via media, diaspora networks, or elite framing — formally a gain term, $i_5(t) = \gamma(t) \cdot \left[i_1+i_2+i_3+i_4\right]$, where $\gamma(t) > 1$ under high propaganda/elite mobilization and $\gamma(t) < 1$ under counter-narrative or fact-checking infrastructure.

### Core Outflows from $G_t$ (Redress/Depletion)

- **Institutional redress flow**, $r_1(t)$: functioning courts, reparations, truth commissions, electoral turnover — mechanisms that formally acknowledge and process the grievance claim.
- **Time decay flow**, $r_2(t)$: a first-order decay term $r_2(t) = \delta \cdot G(t)$, representing generational forgetting, absent active reinforcement. $\delta$ is usually small (multi-year to multi-decade half-life) relative to $r_1$.
- **Reconciliation/apology flow**, $r_3(t)$: symbolic acknowledgment; empirically weaker as a pure outflow unless paired with $r_1$ (material redress) — a well-documented finding in transitional justice literature is that apology without material redress produces only shallow, reversible depletion.
- **Outmigration/exit flow**, $r_4(t)$: grievance leaves the system stock via emigration of the aggrieved population rather than being resolved — this is a boundary condition change (Hirschman's "exit" option), not true resolution, and can mask $G(t)$ in national-level data while leaving it undiminished at the diaspora level.

$$R_t = r_1(t) + r_2(t) + r_3(t) + r_4(t)$$

### Threshold Dynamics and Mobilization

Grievance stock alone is necessary but not sufficient for conflict onset — this is the standard rebuttal to naive "grievance theory" and the empirical basis of the Collier-Hoeffler "greed vs. grievance" debate, which found grievance measures to be poor standalone predictors of civil war onset relative to opportunity/feasibility structures (state capacity, terrain, primary commodity dependence). The stock-flow resolution: $G(t)$ is a necessary state variable, but mobilization $M(t)$ is a separate stock gated by a threshold function requiring both grievance *and* organizational capacity $C(t)$ (Tilly's mobilization theory) and low state repressive capacity $S(t)$:

$$M(t) = f\big(G(t) - G^*\big) \cdot g\big(C(t)\big) \cdot h\big(S(t)\big)$$

where $G^*$ is a threshold and $f$ is typically a sigmoid or step function, not linear — small changes in $G(t)$ near $G^*$ produce disproportionate changes in $M(t)$, while the same-sized change far from $G^*$ produces negligible effect. This is the formal reason "grievance was always there" narratives feel unsatisfying: the stock had been near-threshold for years, and the proximate trigger was a small flow perturbation on top of a state that was already close to critical.

### Hysteresis and Irreversibility

A key departure from simple stock-flow accounting: certain inflows (mass violence, genocide-adjacent repression) are modeled with **asymmetric flow coefficients** — the outflow required to offset a unit of violence-inflow grievance is far larger than the inflow itself, and in the limit some SD conflict models treat a subclass of $G(t)$ as a **ratchet**, i.e., $R_t$ cannot act on it at all without an exogenous structural intervention (regime change, third-party enforcement). This produces path dependence: two societies with identical *current* injury flows can have wildly different $G(t)$ trajectories depending on integrated history, and no feasible near-term $R_t$ returns $G(t)$ to its pre-shock baseline. [Inference] The precise functional form of this asymmetry (magnitude of the ratchet, whether it is truly absorbing or merely slow-decaying) is model-dependent and not empirically pinned down to a single canonical value across cases.

### Feedback Loop Structure

**Reinforcing loop (R1) — Repression-Grievance Spiral:**

$G(t) \uparrow \rightarrow$ mobilization risk $\uparrow \rightarrow$ state repression $i_1(t) \uparrow \rightarrow$ $G(t) \uparrow$ further. This is a classic escalatory reinforcing loop and the formal skeleton of the security-dilemma-adjacent "repression backfires" literature (Francisco, Lichbach): repression intended to suppress mobilization instead adds to the grievance inflow that drives future mobilization, unless repression is severe enough to also suppress $C(t)$ (organizational capacity) faster than it adds to $G(t)$ — the empirically contested "repression works" threshold.

**Balancing loop (B1) — Institutional Absorption:**

$G(t) \uparrow \rightarrow$ political/social pressure $\uparrow \rightarrow$ institutional redress $r_1(t) \uparrow \rightarrow$ $G(t) \downarrow$. This loop only closes if the institution has both the *capacity* to process claims and the *legitimacy* for the aggrieved group to accept the redress channel as genuine — a legitimacy failure decouples the loop, leaving $G(t)$ to keep rising even as nominal redress mechanisms operate.

```mermaid
flowchart LR
    subgraph Inflows
        i1[Repression/Violence]
        i2[Horizontal Inequality Gap]
        i3[Relative Deprivation J-curve]
        i4[Identity/Status Threat]
        i5[Narrative Amplification x gamma]
    end
    subgraph Stock
        G[("Grievance Stock G(t)")]
    end
    subgraph Outflows
        r1[Institutional Redress]
        r2[Time Decay]
        r3[Apology/Reconciliation]
        r4[Outmigration/Exit]
    end
    i1 --> G
    i2 --> G
    i3 --> G
    i4 --> G
    i5 --> G
    G --> r1
    G --> r2
    G --> r3
    G --> r4
    G -->|threshold G*| M[Mobilization M(t)]
    M -->|state response| i1
    r1 -.balancing loop B1.-> G
    i1 -.reinforcing loop R1.-> M
```

### Design Implication: What Peace Engineering Targets

Given this structure, peace-engineering interventions decompose cleanly by which term they act on:

- **Reduce inflow slope** ($\partial I/\partial t < 0$): power-sharing arrangements, quota systems targeting horizontal inequality (closing the $E - A$ gap directly rather than raising $A$ in absolute terms, since relative deprivation responds to the *gap*, not the level).
- **Increase outflow capacity** ($r_1$): truth and reconciliation commissions, functioning courts, reparations — designed specifically to raise the ceiling on how much grievance stock can be processed per unit time.
- **Break the R1 reinforcing loop**: security sector reform that decouples "mobilization risk" from automatic repressive response, converting a positive feedback loop into a neutral or balancing one.
- **Raise $G^*$ or dampen $f(\cdot)$**: cross-cutting cleavages, economic interdependence, and elite pacts that raise the effective threshold for mobilization even at constant $G(t)$ — this is the formal logic behind consociational power-sharing design (Lijphart), though consociationalism has a separate, well-documented failure mode of freezing identity categories and thereby indirectly sustaining $i_4(t)$.

**Key Points**

- Grievance must be modeled as a stock (accumulated state), not inferred directly from a single triggering flow event.
- Relative deprivation's inflow term depends on the *derivative* of the expectation-reality gap, formally explaining the J-curve pattern of revolutions following reversed improvement, not just sustained deprivation.
- Grievance stock is necessary but not sufficient for conflict onset; mobilization requires a joint threshold condition over $G(t)$, organizational capacity, and state repressive capacity — this is the formal resolution of the greed-vs-grievance empirical puzzle.
- Some grievance inflows (mass violence) are effectively asymmetric or ratcheted; peace engineering cannot rely on symmetric decay to undo them.
- Design intervention points map directly onto specific terms in the flow equations: inflow-gap closure, outflow-capacity expansion, and reinforcing-loop decoupling.

**Related Topics**

- Relative deprivation and the J-curve model of revolution (Davies, Gurr)
- Greed vs. grievance and civil war onset econometrics (Collier-Hoeffler)
- Security dilemma dynamics as a separate stock-flow system (arms/threat perception)
- Consociational power-sharing design and the frozen-cleavage failure mode
- Truth and reconciliation commissions as institutional outflow mechanisms
- System Dynamics modeling method (Forrester) applied to social/political systems