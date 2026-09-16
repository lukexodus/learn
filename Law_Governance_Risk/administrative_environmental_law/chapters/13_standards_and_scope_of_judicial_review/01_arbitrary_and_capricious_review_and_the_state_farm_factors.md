## Arbitrary and Capricious Review and the *State Farm* Factors


### Overview

Arbitrary-and-capricious review under 5 U.S.C. § 706(2)(A) is the default, generally applicable standard for judicial review of agency action under the APA, applying whenever a more specific standard (substantial evidence, de novo review, or a statute-specific standard) does not otherwise govern. *Motor Vehicle Manufacturers Ass'n v. State Farm Mutual Automobile Insurance Co.*, 463 U.S. 29 (1983), is the foundational modern case articulating the substantive content of this standard, and its enumerated factors remain the operative checklist courts apply across virtually every area of administrative and environmental law.

### Statutory Basis

**5 U.S.C. § 706(2)(A)** directs a reviewing court to "hold unlawful and set aside agency action, findings, and conclusions found to be... arbitrary, capricious, an abuse of discretion, or otherwise not in accordance with law." This is a single statutory phrase but is typically applied as a unified inquiry into the reasonedness of agency decisionmaking, distinct from § 706(2)(E)'s "substantial evidence" standard (applicable to formal rulemaking/adjudication) and from de novo review of purely legal questions.

### The "Hard Look" Doctrine and Its Origins

Arbitrary-and-capricious review is often described as requiring courts to ensure the agency took a **"hard look"** at the relevant factors — a phrase originating in D.C. Circuit case law (notably *Greater Boston Television Corp. v. FCC*, 444 F.2d 841 (D.C. Cir. 1970)) before being substantially developed and formalized by the Supreme Court in *State Farm*. The doctrine requires courts to scrutinize whether the *agency itself* engaged in reasoned decisionmaking — it does not permit courts to substitute their own judgment on the merits, but does require more than a rubber-stamp deference to whatever conclusion the agency reached.

### *Motor Vehicle Manufacturers Ass'n v. State Farm*: Facts and Holding

- The National Highway Traffic Safety Administration (NHTSA) had required passive-restraint systems (airbags or automatic seatbelts) in new automobiles, then later rescinded that requirement, citing changed circumstances regarding the effectiveness of detachable automatic seatbelts (which most manufacturers had chosen to install rather than airbags, and which many drivers were expected to simply detach and never re-use, defeating the safety purpose).
- The Supreme Court held that the *rescission* of a rule is subject to the same arbitrary-and-capricious scrutiny as the initial promulgation of a rule — an agency changing course must supply a reasoned analysis for the change, not merely because the new policy is permissible, but because the agency's prior policy created reliance interests and the agency must acknowledge and explain its departure from its prior position.
- The Court found NHTSA's rescission arbitrary and capricious because the agency failed to adequately consider an obvious and significant alternative — requiring airbags specifically, rather than rescinding the passive-restraint requirement altogether — and failed to explain why it had disregarded record evidence supporting the effectiveness of airbags in particular, even while raising legitimate concerns about detachable seatbelts specifically.

### The *State Farm* Factors

The oft-cited formulation from *State Farm*, 463 U.S. at 43, holds that an agency's action is arbitrary and capricious if the agency:

1. **Relied on factors Congress did not intend it to consider.**
2. **Entirely failed to consider an important aspect of the problem.**
3. **Offered an explanation for its decision that runs counter to the evidence before the agency.**
4. **The explanation is so implausible that it could not be ascribed to a difference in view or the product of agency expertise.**

These four factors are not exhaustive or rigidly sequential; they function as an illustrative, overlapping checklist courts apply flexibly, and a rule can be found arbitrary and capricious on the strength of any single factor or a combination.

### Core Substantive Requirements Distilled From *State Farm* and Its Progeny

**1. Reasoned explanation connecting facts to choice**

The agency must articulate a "rational connection between the facts found and the choice made" (*State Farm*, 463 U.S. at 43, quoting *Burlington Truck Lines, Inc. v. United States*, 371 U.S. 156, 168 (1962)). Courts will not accept conclusory assertions unsupported by the agency's own record.

**2. Consideration of significant alternatives**

An agency need not consider every conceivable alternative, but must meaningfully engage with alternatives that are obvious, significant, and squarely raised during the rulemaking process (as with NHTSA's failure to separately consider an airbags-only mandate).

**3. No post-hoc rationalization**

Courts review the agency's *contemporaneous* reasoning as reflected in the administrative record — they cannot uphold agency action based on rationales the agency's lawyers develop for the first time during litigation (*SEC v. Chenery Corp.*, 332 U.S. 194 (1947), the foundational case for this principle, frequently cited alongside *State Farm*).

**4. Reasoned explanation for changes in position**

Where an agency reverses a prior policy, *State Farm* requires more than merely showing the new policy is permissible — the agency must display awareness that it is changing position and provide a reasoned explanation, particularly where reliance interests have developed around the prior policy (a point later substantially developed in *FCC v. Fox Television Stations, Inc.*, 556 U.S. 502 (2009), and *Department of Homeland Security v. Regents of the University of California*, 591 U.S. 1 (2020), the DACA rescission case).

**5. Data quality and methodology must be adequately explained**

Where an agency relies on technical data, models, or scientific methodology, the "hard look" requirement means the agency's reasoning connecting that data to its conclusions must be transparent and defensible on the record — directly relevant to environmental rulemaking's heavy reliance on scientific and economic modeling.

### Post-*State Farm* Refinements

**FCC v. Fox Television Stations, Inc.**, 556 U.S. 502 (2009) — clarified that an agency changing its policy need not demonstrate that the new policy is *better* than the old one by some independent showing, only that (a) the agency is aware it is changing position, and (b) it has good reasons for the new policy; the Court also held, however, that a more detailed explanation is required where the new policy rests on factual findings that contradict those underlying the prior policy, or where the prior policy engendered serious reliance interests.

**Department of Homeland Security v. Regents of the University of California**, 591 U.S. 1 (2020) — applied *State Farm*/*Fox* to hold that DHS's rescission of the DACA program was arbitrary and capricious because the agency failed to consider certain reliance interests and failed to consider whether a partial rescission (rather than complete rescission) was warranted — reinforcing the significant-alternatives and reliance-interest strands of *State Farm* doctrine in a high-profile modern application.

### The Standard's Deferential-But-Meaningful Character

Arbitrary-and-capricious review is frequently described as deferential — courts do not reweigh policy judgments committed to agency expertise, and "a court is not to substitute its judgment for that of the agency" (*State Farm*, 463 U.S. at 43). At the same time, it is not merely a rubber stamp: the "hard look" requirement demands genuine judicial scrutiny of the agency's reasoning process, data, and consideration of alternatives — this dual character (deferential to policy outcomes, exacting as to reasoning process) is the doctrine's defining and sometimes difficult-to-apply tension.

### Structural Analysis Framework

```mermaid
flowchart TD
    A[Agency rule or order challenged under Section 706(2)(A)] --> B{Did the agency rely on factors Congress did not intend it to consider?}
    B -->|Yes| C[Arbitrary and capricious]
    B -->|No| D{Did the agency entirely fail to consider an important aspect of the problem, including significant alternatives?}
    D -->|Yes| C
    D -->|No| E{Does the agency's explanation run counter to the evidence in the record?}
    E -->|Yes| C
    E -->|No| F{Is the explanation so implausible it cannot be ascribed to agency expertise or a difference in view?}
    F -->|Yes| C
    F -->|No| G{If reversing a prior policy: did the agency acknowledge the change and provide reasoned justification, including for any reliance interests?}
    G -->|No| C
    G -->|Yes| H[Agency action survives arbitrary-and-capricious review]
```

### Application in Environmental Law

Arbitrary-and-capricious review is the dominant standard governing challenges to the vast majority of EPA, Interior, and other environmental agency rulemakings and orders not otherwise subject to a more specific statutory standard:

- **Emissions and technology-based standards**: Challenges to Clean Air Act NAAQS, NSPS, and technology-based effluent limitations under the Clean Water Act frequently turn on whether EPA adequately explained its methodology, adequately considered significant alternative approaches proposed during comment, and grounded its conclusions in the administrative record rather than post-hoc litigation rationales.
- **NEPA "hard look" doctrine**: NEPA's own "hard look" requirement (requiring agencies to take a hard look at environmental consequences) is closely related to, and sometimes analytically merged with, the *State Farm* arbitrary-and-capricious framework, since a NEPA analysis that fails to adequately consider environmental impacts or significant alternatives can independently support a finding of arbitrary-and-capricious agency action under the APA.
- **Species listing and delisting decisions under the ESA**: Fish and Wildlife Service and NOAA Fisheries decisions to list, delist, or decline to list species are reviewed under *State Farm*, with litigation frequently focused on whether the agency adequately explained its scientific methodology and addressed contrary evidence in the record.
- **Deregulatory actions and policy reversals**: Environmental deregulation — rescinding or weakening a prior environmental rule — receives the same *State Farm*/*Fox*/*Regents* scrutiny as the original promulgation, requiring the agency to acknowledge the policy change, address reliance interests built up by regulated industry and other stakeholders around the prior rule, and explain why the new position is superior or otherwise justified, not merely permissible. This has been a recurring and significant battleground in environmental law given periodic shifts in environmental regulatory priorities across different administrations.

### Practical Example

EPA finalizes a rule loosening a previously stringent particulate matter emissions limit for a category of industrial sources, citing updated cost-benefit analysis showing compliance costs exceed health benefits.

1. **Factor 1 (impermissible factors)**: A challenger would examine whether EPA's cost-benefit methodology incorporated only statutorily authorized considerations, or whether it improperly weighed factors the governing Clean Air Act provision does not permit EPA to consider (e.g., certain non-health-related economic considerations under a provision that Congress intended to be health-based only).
2. **Factor 2 (failure to consider important aspects/alternatives)**: Did EPA consider an intermediate alternative — a moderately relaxed limit rather than complete rescission — or entirely fail to grapple with an obvious middle-ground approach raised during comment?
3. **Factor 3 (explanation counter to the record)**: If EPA's own technical staff analysis or peer-reviewed studies in the record showed significant health benefits from the existing limit, does EPA's stated rationale for relaxation directly contradict that record evidence without adequate explanation?
4. **Reasoned explanation for the change**: Because this is a rescission/weakening of a prior standard, EPA must acknowledge it is departing from its prior position, address the reliance interests of communities and possibly of industry participants who made compliance investments under the existing rule, and explain — with more than conclusory assertions — why its updated position is justified given the existing record.

A rule failing any of these individual inquiries would be vulnerable to vacatur or remand under § 706(2)(A), even without any court substituting its own judgment about the ideal emissions standard.

### Key Case Summary Table

| Case | Holding | Doctrinal Contribution |
| --- | --- | --- |
| *Motor Vehicle Mfrs. Ass'n v. State Farm* (1983) | Establishes the four-factor arbitrary-and-capricious framework; rescissions receive same scrutiny as promulgation | Foundational modern arbitrary-and-capricious case |
| *SEC v. Chenery Corp.* (1947) | Agency action must be upheld, if at all, on the grounds the agency itself articulated | Prohibits post-hoc litigation rationalization |
| *FCC v. Fox Television Stations, Inc.* (2009) | Policy changes require awareness of the change and good reasons; more required where reliance interests exist | Refines standard for agency policy reversals |
| *Department of Homeland Security v. Regents of the Univ. of Cal.* (2020) | DACA rescission arbitrary and capricious for failing to consider reliance interests and partial-rescission alternative | Modern high-profile application of *State Farm*/*Fox* framework |

### Practice Pointers

- When challenging a rule, systematically work through each *State Farm* factor against the administrative record — do not treat the four factors as requiring a single "best" theory; multiple factors can and often should be pled in the alternative.
- When defending a rule, ensure the administrative record contains an explicit, reasoned agency response to significant alternatives and material contrary evidence raised during comment — silence in the record on an obvious alternative is one of the most common and effective grounds for a successful *State Farm* challenge.
- For rules rescinding or weakening prior environmental standards, build the administrative record to explicitly acknowledge the policy change, address reliance interests, and explain (not merely assert) why the new position is superior, particularly where the change rests on factual findings that contradict those underlying the original rule (which triggers a more searching explanation requirement under *Fox*).
- Never rely on litigation-stage explanations or agency counsel's post-hoc rationales to defend a rule under review — per *Chenery*, only the agency's contemporaneous reasoning in the record can sustain the action.

### Related Topics

- The "hard look" doctrine and its origins in D.C. Circuit precedent
- NEPA's hard look requirement and environmental impact statement adequacy
- Substantial evidence review under Section 706(2)(E)
- Post-*Chevron* statutory interpretation and *Loper Bright Enterprises v. Raimondo*
- Reliance interests in agency policy reversals (*Fox*, *Regents*)
- The administrative record and record supplementation/extra-record evidence
- Cost-benefit analysis methodology challenges in environmental rulemaking