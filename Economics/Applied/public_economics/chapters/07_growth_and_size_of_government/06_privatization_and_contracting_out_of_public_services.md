## Privatization and Contracting Out of Public Services


### Overview

Privatization and contracting out refer to a set of policy tools that shift the production (though not necessarily the financing or regulatory oversight) of goods and services traditionally provided by government toward private-sector actors. These are among the primary policy responses motivated by the public choice critiques of government growth covered elsewhere in this chapter (Niskanen's budget-maximizing bureaucracy, the Leviathan hypothesis), and constitute a distinct set of tools within the broader debate on the efficient size and scope of government.

### Conceptual Distinctions

**Privatization vs. contracting out vs. deregulation**

These related but distinct terms are frequently conflated in casual usage:

- **Privatization** (full/asset privatization): the outright transfer of ownership of an asset or enterprise from government to private hands (e.g., selling a state-owned utility or airline to private investors) — government exits both production *and* ownership.
- **Contracting out** (outsourcing/purchase-of-service contracting): government retains ownership, financing responsibility, and ultimate accountability for a service, but purchases the actual production/delivery from a private (for-profit or non-profit) contractor via competitive bidding — government exits production but retains financing and oversight.
- **Deregulation**: removal or reduction of government regulatory constraints on private-sector activity, which may occur independently of privatization or contracting decisions (e.g., deregulating an industry that was always privately owned).

This chapter's public-choice-driven privatization/contracting discussion centers primarily on **contracting out**, since it is the mechanism most directly motivated by, and most commonly proposed in response to, the Niskanen-style critique of monopoly bureau provision — introducing competitive bidding for service delivery while government retains its financing and accountability role.

### Theoretical Rationale

**Addressing the Niskanen problem via competition**

The Niskanen model's core mechanism for bureau overexpansion relies critically on the bureau's position as a **monopoly supplier** with superior cost information relative to its legislative principal. Contracting out directly targets this mechanism: by inviting multiple potential providers to competitively bid for a service contract, the sponsoring government (or its equivalent legislative principal) gains access to **market price signals** revealing something closer to the true cost of provision — competitive bidding can force bidders to reveal cost information they would otherwise have an incentive to conceal from a sole-source monopoly bureau, at least in principle, though this benefit is contingent on genuinely competitive conditions holding (discussed under limitations below).

**Yardstick competition**

A related mechanism, particularly relevant when full competitive bidding for a single contract is impractical (e.g., natural monopoly services like water/electricity distribution, where only one provider can efficiently serve a given geographic area at a time), is **yardstick competition**: comparing the cost/performance of multiple similar jurisdictions or service providers against one another to infer relative efficiency and discipline any single provider's ability to claim costs are irreducibly high, even absent direct head-to-head competitive bidding for the same contract.

**Ownership vs. financing distinction (Savas framework)**

E.S. Savas's influential framework for privatization theory distinguishes **arranging** (deciding what service is provided and financing it — a function government can retain) from **producing** (actually delivering the service — a function that can be shifted to private, competitive provision) — this arranger/producer distinction underlies the theoretical case that government can capture efficiency gains from competitive private production while still retaining public financing, universal access guarantees, and quality/equity oversight, addressing a common political objection that contracting out necessarily abandons public accountability for outcomes.

### Empirical Evidence on Cost Savings

**General empirical pattern**

A substantial body of empirical literature, particularly concentrated in local government services (waste collection, transportation, custodial/facilities services, and similar relatively standardized, easily-specified services), has generally found **cost savings** associated with contracting out relative to in-house government provision, though the magnitude of estimated savings varies considerably across studies, service types, and time periods. [Unverified: precise average cost-savings percentages cited in various studies differ substantially by service category and methodology; treat specific numerical savings estimates as study-specific rather than a single settled parameter.]

**Sources of the estimated savings**

Where savings are found, the literature attributes them to a combination of: genuine productive efficiency gains from competitive pressure and private-sector management flexibility (fewer civil-service employment constraints, more flexible procurement), and in some cases, savings attributable to lower wages/benefits for contracted workers relative to unionized public-sector employees — a distinction with significant equity and distributional implications that is separate from the pure productive-efficiency question, since the latter source of "savings" represents a transfer (from workers to taxpayers/contractors) rather than a genuine efficiency gain in the economic sense.

### Conditions under Which Contracting Out Is More or Less Likely to Succeed

The efficiency case for contracting out is **conditional**, not universal — the theoretical literature identifies several factors that determine whether competitive contracting actually delivers the predicted efficiency gains:

**Favorable conditions**

- **Multiple credible bidders exist** (genuine competition, not a de facto sole-source situation)
- **Service quality and output are readily specifiable and verifiable** in a contract (e.g., "collect trash from X households weekly" is easy to specify and monitor; complex, judgment-intensive services are harder)
- **Contract switching costs are manageable** (government retains genuine ability to switch providers or bring service back in-house if a contractor underperforms — a credible threat, not just a nominal option)
- **The service does not raise significant public-good, externality, or public-values concerns** that are difficult to fully specify in a contract (e.g., core law-enforcement or judicial functions raise distinct debates given the state's unique coercive authority)

**Unfavorable conditions / risk factors**

- **Natural monopoly characteristics limiting the number of feasible competitors** (some services are structurally prone to having very few capable bidders, replicating rather than solving the Niskanen-style bilateral monopoly problem, just with a private rather than public monopolist)
- **Contract incompleteness and quality degradation risk**: if quality dimensions are difficult to fully specify and monitor, competitive pressure to win the contract can incentivize bidders to cut costs precisely along the *unmonitored* quality dimensions — a well-documented risk in the contracting literature, sometimes termed the "unraveling of quality" problem, especially acute for services delivered to vulnerable populations with limited capacity to detect or report quality shortfalls
- **Transition and transaction costs**: contract design, competitive bidding administration, and ongoing contract monitoring themselves consume real administrative resources, which must be netted against any gross efficiency savings to assess *net* benefit
- **Asset specificity and hold-up risk**: where service delivery requires the contractor to make large, service-specific capital investments (specialized equipment, facilities), the government may face hold-up risk from the incumbent contractor at renewal time (since few alternative bidders can credibly replicate the specific investment), potentially eroding the ongoing competitive discipline that justified contracting out in the first place — an application of transaction-cost economics (Williamson) to public contracting design

### Diagram: Contracting-Out Decision Logic

```mermaid
flowchart TD
    A["Service currently provided<br/>by public bureau/agency"] --> B{"Is service output<br/>readily specifiable<br/>& verifiable in contract?"}
    B -->|No| C["High risk of quality<br/>degradation under contracting;<br/>favor in-house provision<br/>or intensive oversight design"]
    B -->|Yes| D{"Do multiple credible<br/>competitive bidders exist?"}
    D -->|No<br/>(natural monopoly /<br/>few capable providers)| E["Risk of replicating<br/>bilateral monopoly problem<br/>with private provider;<br/>consider yardstick competition<br/>as partial substitute"]
    D -->|Yes| F{"Asset specificity /<br/>hold-up risk at<br/>contract renewal?"}
    F -->|High| G["Competitive discipline may<br/>erode over successive<br/>contract renewals"]
    F -->|Low| H["Favorable conditions for<br/>genuine competitive<br/>efficiency gains"]
    H --> I["Contract out, with<br/>government retaining<br/>arranging/financing/<br/>oversight role"]
```



```
### Political Economy of Privatization Decisions

**Interaction with public choice theories of government growth**
Contracting-out decisions themselves are not immune to the political-economy dynamics described elsewhere in this chapter — incumbent public-sector bureaus (facing the Niskanen-style incentive to protect budget/staff) can be expected to resist contracting-out proposals that threaten their resources, while private contractors, once established as incumbents, can develop their own rent-seeking incentives to entrench their position (e.g., through lobbying for favorable contract terms or specifications tailored to their capabilities) — meaning contracting out does not eliminate public-choice-style incentive problems but rather relocates and potentially reshapes them, rather than serving as a costless universal solution.

**Distributional and labor-market considerations**
Contracting-out debates frequently involve significant distributional stakes for public-sector employees (wage, benefit, and job security differences between public and contracted private employment), which are a central and often dominant feature of the real-world political conflict over contracting decisions, separate from (though often entangled with) the pure efficiency question emphasized in the economic theory above.

### Worked Example

Suppose a municipality currently collects waste via an in-house department at an annual cost of \$5 million, serving 50,000 households. Three private waste-management firms submit competitive bids for a 5-year contract to provide the identical specified service level: \$4.2 million, \$4.4 million, and \$4.6 million respectively.

**Naive comparison**: the lowest bid (\$4.2 million) suggests \$800,000 in annual savings (16%) relative to in-house provision.

**Full efficiency accounting requires netting out**:
- **Contract administration/monitoring costs**: suppose the municipality must dedicate staff time to monitor contractor performance, verify service-level compliance, and manage the bidding/renewal process, estimated at \$150,000/year — a cost that did not exist (or existed differently) under in-house provision.
- **Transition costs**: one-time costs of the transition (severance/reassignment for displaced public employees, asset transfer or lease arrangements), amortized here as \$100,000/year over the contract's 5-year term for illustration.
- **Net savings**: $800{,}000 - 150{,}000 - 100{,}000 = \$550{,}000$ annually (11% net savings), a meaningfully smaller figure than the naive headline comparison, illustrating why rigorous privatization evaluation requires accounting for the full set of transaction and oversight costs, not merely comparing the headline contract price to the prior in-house budget figure. [Inference: this worked example uses illustrative, invented figures for pedagogical purposes and does not represent an empirical finding from any actual jurisdiction.]

### Related Topics
- Niskanen model of budget-maximizing bureaucracy
- Leviathan hypothesis of government growth
- Yardstick competition and comparative regulation
- Transaction cost economics and asset specificity (Williamson)
- Public-private partnerships (PPPs)
- Tiebout model and inter-jurisdictional competition
- Principal-agent theory in public administration
- Contract theory and incomplete contracts


```