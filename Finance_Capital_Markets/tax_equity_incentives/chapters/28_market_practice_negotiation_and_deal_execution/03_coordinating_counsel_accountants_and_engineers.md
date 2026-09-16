## Coordinating Counsel, Accountants, and Engineers

### Overview

Tax equity transactions require simultaneous, coordinated input from three distinct advisor categories — legal counsel, accountants/tax advisors, and independent engineers (IEs) — each of whom operates on different professional standards, timelines, and risk frameworks. Poor coordination among these workstreams is one of the most common causes of deal delay. This topic addresses the practical mechanics of managing multi-advisor workstreams, resolving conflicting priorities, and structuring information flow so that legal documentation, tax structuring, and technical diligence converge on a single closing date.

### Key Points

- Each advisor category has a distinct "product": counsel produces binding legal documents and opinions; accountants/tax advisors produce models, opinions, and structuring advice; engineers produce technical certifications and risk assessments.
- The sponsor (or its deal lead/project finance team) typically functions as the central coordinator, since no single advisor has visibility into all three workstreams simultaneously.
- Advisor outputs are interdependent: the tax opinion depends on the LLC Agreement's final allocation provisions; the LLC Agreement depends on the IE's technology risk assessment; the model audit depends on both.
- Miscommunication or delay in one workstream cascades into the others — a classic critical-path management problem.

### The Three Advisor Roles

**1. Legal Counsel**

Most tax equity deals involve at least four separate legal teams:

- **Sponsor's counsel**: drafts or leads negotiation of the LLC Agreement, PSA/Contribution Agreement, and coordinates with EPC/offtake counsel for consents
- **Tax equity investor's counsel**: reviews and redlines the LLC Agreement (particularly allocation and distribution waterfall provisions), negotiates investor protections (consent rights, indemnities, put/call options)
- **Tax counsel** (may be same firm as transactional counsel or a separate specialist firm): drafts the tax opinion addressing partnership classification, allocation validity under §704(b) substantial economic effect regulations, and ITC/PTC eligibility
- **Lender's counsel** (if back-leverage debt is present): negotiates intercreditor and consent agreements between the tax equity investor and the debt provider

**2. Accountants and Tax Advisors**

- **Sponsor's tax advisor / Big Four or specialty accounting firm**: prepares or reviews the financial model, calculates projected ITC/PTC value, MACRS depreciation schedules, and flip point projections
- **Model auditor**: an independent third party (often a specialty firm) that stress-tests the financial model's mechanics, formula integrity, and assumptions — distinct from the tax opinion, which addresses legal sufficiency of the structure
- **Cost segregation / valuation firm**: performs the FMV appraisal supporting ITC eligible basis, particularly critical in sale-leaseback and related-party structures
- **Investor's internal tax and structuring team**: reviews sponsor's model and tax opinion, often runs parallel independent tax analysis

**3. Independent Engineers and Technical Advisors**

- **Independent Engineer (IE)**: engaged by the investor (sometimes jointly) to assess technology bankability, EPC contractor track record, resource assessment (P50/P90/P99 yield estimates), and construction budget reasonableness
- **Owner's engineer**: sponsor-side technical advisor overseeing EPC contractor performance, often distinct from the IE
- **Insurance advisor/broker**: reviews builder's risk and operational insurance adequacy
- **Environmental consultant**: Phase I/II environmental site assessments, permitting compliance review

### Coordination Diagram

```mermaid
flowchart TD
    SP[Sponsor Deal Lead - Central Coordinator (svg_diagram)]

    SP --> SC[Sponsor Counsel]
    SP --> TC[Tax Counsel]
    SP --> TA[Tax Advisor and Model Auditor]
    SP --> IE[Independent Engineer]
    SP --> ACC[Accountant and Valuation Firm]

    SC <--> IEC[Investor Counsel]
    TC --> TO[Tax Opinion]
    TA --> FM[Financial Model]
    IE --> IER[IE Report]
    ACC --> FMV[FMV Appraisal]

    TO -.depends on.-> SC
    FM -.depends on.-> TO
    FM -.depends on.-> FMV
    SC -.depends on.-> IER
    IEC -.reviews.-> SC
    IEC -.reviews.-> TO
    IEC -.reviews.-> FM
    IEC -.reviews.-> IER

    IEC --> CLOSE[Closing and Funding]
    SC --> CLOSE
```



```
### Workflow Interdependencies

**Legal counsel depends on engineering output** — the LLC Agreement's technology risk allocation provisions (e.g., performance guarantees, curtailment risk allocation, EPC warranty pass-through) cannot be finalized until the IE report identifies material technical risks.

**Tax counsel depends on legal counsel** — the tax opinion's partnership classification analysis and allocation validity conclusions depend on final LLC Agreement language, meaning tax opinions are typically drafted iteratively alongside document negotiation rather than after it.

**Model audit depends on both tax and legal** — the model auditor needs final LLC Agreement waterfall provisions and final tax opinion conclusions (on ITC basis, depreciation method) to validate the model's mechanics.

**FMV appraisal depends on engineering** — valuation firms rely on the IE's technical assessment of equipment condition, remaining useful life, and performance data as inputs to their valuation methodology.

### Practical Coordination Mechanisms

**1. Weekly (or twice-weekly) all-advisor status calls**

Standard practice during the definitive documentation phase — typically led by the sponsor's deal lead or outside deal counsel, with representatives from each workstream reporting open items, blockers, and target dates.

**2. Master closing checklist**

A shared document tracking every deliverable, responsible party, dependency, and status. Typically maintained by sponsor's counsel and circulated to all parties.

**Example checklist structure:**

| Item | Responsible Party | Depends On | Target Date | Status |
|---|---|---|---|---|
| IE Report (final) | Independent Engineer | EPC contract, site data | Week 6 | In progress |
| LLC Agreement (execution version) | Sponsor/Investor Counsel | IE Report, Tax Opinion | Week 12 | Blocked on IE |
| Tax Opinion (final) | Tax Counsel | LLC Agreement | Week 13 | Draft circulated |
| Model Audit Sign-off | Model Auditor | LLC Agreement, Tax Opinion | Week 14 | Not started |
| FMV Appraisal | Valuation Firm | IE Report | Week 10 | Complete |

**3. Data room management**

A centralized virtual data room (VDR) ensures all advisors work from the same document versions — critical because engineers, accountants, and lawyers often need overlapping documents (EPC contract reviewed by both IE and counsel; interconnection agreement reviewed by both engineer and tax counsel for PIS timing implications).

**4. Issues log with escalation protocol**

Cross-functional issues (e.g., an IE-flagged technology risk that changes the tax opinion's basis conclusion) require an escalation path directly to the sponsor's deal lead rather than being resolved unilaterally within one workstream.

### Common Coordination Failures

- **Sequential rather than parallel engagement**: engaging the IE only after legal documentation is substantially complete, forcing late-stage re-negotiation of risk allocation provisions
- **Tax opinion drafted in isolation**: tax counsel finalizing the opinion before the LLC Agreement is final, requiring costly revisions
- **Model and legal documents diverging**: the financial model and LLC Agreement waterfall provisions drift out of sync during negotiation, caught only at model audit
- **Duplicate diligence requests**: engineers, accountants, and lawyers independently requesting the same documents from the sponsor without a shared data room, creating unnecessary sponsor burden
- **Advisor scope gaps**: ambiguity over whether tax counsel or the accountant is responsible for confirming FMV appraisal methodology compliance with IRS guidance

**[Inference]** Deals with repeat sponsor/investor pairings and standardized advisor teams tend to experience fewer coordination failures because working relationships and document templates are already established.

### Example: Escalation Scenario

If the IE's report (delivered in Week 6) identifies a previously unassessed curtailment risk from the interconnecting utility, this triggers a cascading review:

1. Sponsor's deal lead flags the issue on the next all-advisor call
2. Sponsor counsel and investor counsel revisit LLC Agreement risk allocation language (who bears curtailment-related revenue shortfall risk)
3. Tax advisor reassesses whether the risk affects the financial model's flip date projection
4. Tax counsel confirms the revised allocation does not jeopardize partnership tax classification
5. Model auditor incorporates the revised assumption before final sign-off

This sequential dependency chain illustrates why a single technical finding can extend the timeline by 1-3 weeks if not identified early.

### Next Steps

- **Master Closing Checklists and Data Room Best Practices**
- **Independent Engineer Reports and Technical Due Diligence Standards**
- **Tax Opinion Standards: "Should," "Will," and "More Likely Than Not"**
- **Model Audits: Scope, Methodology, and Common Findings**
- **Deal Timeline from Term Sheet to Funding**
- **EPC Contractor Consents and Step-In Rights Negotiation**
- **Role of the Sponsor's Deal Lead / Project Finance Team**


```