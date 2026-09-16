## Regulatory Takings: Penn Central, Lucas, and Nollan and Dolan


### Constitutional Basis

The Takings Clause of the Fifth Amendment, applied to the states through the Fourteenth Amendment, provides that private property shall not "be taken for public use, without just compensation." Regulatory takings doctrine addresses when a government regulation — as opposed to a direct physical appropriation — becomes so burdensome that it is functionally equivalent to a taking, thereby triggering the compensation requirement.

$$\text{Just Compensation} = \text{Fair Market Value at time of taking}$$

The doctrine originates in *Pennsylvania Coal Co. v. Mahon*, 260 U.S. 393 (1922), where Justice Holmes articulated the foundational principle that "if regulation goes too far it will be recognized as a taking." This created the conceptual bridge between traditional eminent domain (physical takings) and the newer category of regulatory takings, where no physical invasion occurs but the regulation's economic effect approximates a taking.

### Categories of Takings

**Key Points**

- **Per se (categorical) physical takings**: Any permanent physical occupation of property, however minor, constitutes a taking requiring compensation (*Loretto v. Teleprompter Manhattan CATV Corp.*, 1982).
- **Per se (categorical) regulatory takings**: A regulation that denies all economically beneficial use of land (*Lucas*).
- **Ad hoc regulatory takings**: Evaluated under the multi-factor balancing test from *Penn Central*.
- **Exactions**: Conditions imposed on development permits, evaluated under the *Nollan/Dolan* heightened scrutiny standard.

```mermaid
flowchart TD
    A[Government Action Affecting Property (svg_diagram)] --> B{Physical Occupation?}
    B -->|Yes, permanent| C[Per Se Taking - Loretto]
    B -->|No| D{Total Economic Wipeout?}
    D -->|Yes| E[Per Se Taking - Lucas]
    D -->|No| F{Is it a Development Exaction/Condition?}
    F -->|Yes| G[Nollan/Dolan Nexus & Proportionality Test]
    F -->|No| H[Penn Central Ad Hoc Balancing Test]
    C --> I[Just Compensation Required]
    E --> J{Background Principles of Nuisance/Property Law Defense?}
    J -->|Applies| K[No Taking]
    J -->|Does Not Apply| I
    G --> L{Nexus + Rough Proportionality Satisfied?}
    L -->|Yes| M[No Taking - Valid Condition]
    L -->|No| I
    H --> N[Weigh Three Factors]
    N --> O{Taking Found?}
    O -->|Yes| I
    O -->|No| M
```

### Penn Central Transportation Co. v. City of New York (1978)

**Facts**: New York City's Landmarks Preservation Law designated Grand Central Terminal a historic landmark, which prevented Penn Central from constructing a multi-story office tower above the terminal. Penn Central argued this denied it the right to develop the airspace above the building, constituting a taking of that portion of the property.

**Holding**: The Supreme Court rejected the claim, holding that the landmark designation did not constitute a taking. The Court declined to adopt a bright-line rule and instead established a fact-intensive, ad hoc balancing test to be applied to regulations that do not involve physical invasion or total economic deprivation.

**The Three-Factor Penn Central Test**

1. **Economic impact of the regulation on the claimant** — measured against the property's value *as a whole* (the "parcel as a whole" or "denominator" problem), not merely the specific interest or portion affected.
2. **Interference with distinct investment-backed expectations** — whether the regulation upsets expectations reasonably formed at the time of acquisition or investment, considering the regulatory climate the owner knew or should have known about.
3. **Character of the governmental action** — whether the action amounts to a physical invasion or instead constitutes a public program adjusting the benefits and burdens of economic life to promote the common good; regulations resembling physical invasions weigh more heavily toward a taking than broad, generally applicable regulatory schemes.

**Example**

A city enacts a historic-district ordinance restricting facade alterations on a commercial building. The owner cannot demolish and rebuild taller, but can continue renting the existing structure at a profit. Applying *Penn Central*: (1) the owner retains substantial economic use (rental income continues), (2) the owner purchased after zoning was in effect, weakening investment-backed expectations, and (3) the ordinance is a generally applicable land-use program, not a physical intrusion. Result: no taking.

[Inference] Courts applying *Penn Central* have significant discretion in defining the "relevant parcel," and outcomes can vary substantially depending on how a court frames the denominator (e.g., air rights alone versus the entire lot and building).

### Lucas v. South Carolina Coastal Council (1992)

**Facts**: David Lucas purchased two residential beachfront lots intending to build single-family homes. Two years later, South Carolina's Beachfront Management Act barred any permanent habitable structures on the parcels to protect coastal erosion zones, rendering the lots valueless for their intended use.

**Holding**: The Supreme Court created a categorical (per se) rule: when a regulation denies *all economically beneficial or productive use* of land, it constitutes a taking without need for the *Penn Central* balancing inquiry, **unless** the proscribed use was not part of the owner's title to begin with — that is, unless background principles of the state's property or nuisance law already prohibited the use.

**The Lucas Categorical Rule**

$$\text{If } \Delta \text{Economic Value} \rightarrow -100\% \implies \text{Per Se Taking (absent background principles defense)}$$

**Background Principles Defense**

- Government may avoid compensation by showing the regulated use was **never part of the owner's bundle of rights** under pre-existing state nuisance or property law (e.g., the use would have constituted a public nuisance regardless of the new statute).
- This inquiry looks to background common law of property and nuisance as it existed independent of the challenged regulation, not to the government's post hoc justification for the regulation itself.
- On remand, South Carolina's Supreme Court found no such background principle applied, and Lucas was awarded compensation (later settled with the state purchasing the lots).

**Example**

A wetlands regulation prohibits all fill and construction on a parcel that was previously dry, buildable land, leaving it with no viable economic use. Under *Lucas*, this is a categorical taking unless the state can show that filling wetlands was already actionable as a common-law nuisance (e.g., due to flooding neighboring properties) independent of the new statute.

[Inference] *Lucas* claims are relatively rare in practice because total wipeouts of *all* economic value are uncommon; most regulations leave *some* residual value, pushing the analysis back into *Penn Central*'s ad hoc framework. *Palazzolo v. Rhode Island* (2001) clarified that post-regulation acquisition of title does not automatically bar a *Lucas* claim.

### Nollan v. California Coastal Commission (1987)

**Facts**: The Nollans sought a permit to rebuild their beachfront home. The California Coastal Commission conditioned approval on the Nollans granting a public easement across their beach to connect two public beaches on either side of their property.

**Holding**: The Court held the condition was an unconstitutional taking because there was no **essential nexus** between the permit condition (public beach access easement) and the legitimate state interest asserted (visual/psychological access to the beach from the road). The condition served a different governmental purpose than the one used to justify denying the permit outright.

**The Nexus Requirement**

The government must show a logical connection between the condition imposed and the impact of the proposed development that the permit denial itself could otherwise address. If the government could have denied the permit outright to serve the stated interest, it can only condition approval on an exaction that substantially advances that *same* interest.

### Dolan v. City of Tigard (1994)

**Facts**: Dolan sought a permit to expand her plumbing/electric supply store and pave a parking lot. The city conditioned approval on Dolan dedicating a portion of her property for a public greenway/floodplain and a pedestrian/bicycle pathway.

**Holding**: The Court held that even where a nexus exists (here, flood control and traffic mitigation were legitimately related to the development's impacts), the government must also show **rough proportionality** between the exaction and the specific impact of the proposed development. The city failed to make an individualized determination that the pathway dedication was roughly proportional to the traffic impact generated by the expanded store.

**The Nollan/Dolan Two-Part Test**

| Element | Standard | Burden |
| --- | --- | --- |
| Essential Nexus | Condition must be logically connected to a legitimate state interest tied to the development's impact | Government |
| Rough Proportionality | Exaction must be roughly proportional in nature and extent to the impact of the proposed development | Government (individualized determination required, not generalized findings) |

**Example**

A developer applies for a permit to build a 50-unit apartment complex. The city conditions approval on dedicating land for a public park equal to 40% of the site. Under *Nollan/Dolan*: (1) nexus may exist if increased density creates need for recreational space, but (2) the city must individually justify why 40% — rather than a smaller, impact-proportional dedication — is roughly proportional to the specific burden this development creates on park capacity.

**Extension to Monetary Exactions**: *Koontz v. St. Johns River Water Management District* (2013) extended *Nollan/Dolan* scrutiny to permit conditions requiring monetary payments (impact fees) and to permit *denials* conditioned on refusal to accept an exaction, not merely to permit grants.

### Comparative Framework

```mermaid
flowchart LR
    subgraph Physical (svg_diagram)
    A[Loretto: Any permanent physical occupation = per se taking]
    end
    subgraph Total Wipeout
    B[Lucas: 100% economic loss = per se taking, subject to background principles defense]
    end
    subgraph Partial Regulatory Burden
    C[Penn Central: 3-factor ad hoc balancing - economic impact, investment expectations, character of action]
    end
    subgraph Development Conditions
    D[Nollan: essential nexus required]
    D --> E[Dolan: rough proportionality required]
    end
```

### Applying the Doctrines in Practice

**Output**

A practitioner analyzing a potential regulatory takings claim should proceed sequentially:

1. Determine whether there is a **permanent physical occupation** → if yes, apply *Loretto* per se rule.
2. If no physical occupation, determine whether the regulation **eliminates all economically beneficial use** → if yes, apply *Lucas*, then check the background principles defense.
3. If some economic use remains, determine whether the action is a **development permit condition/exaction** → if yes, apply *Nollan/Dolan* nexus and rough proportionality.
4. If none of the above categorical frameworks apply, default to the **Penn Central** ad hoc balancing test.

### Distinguishing Doctrinal Nuances

- *Penn Central* remains the **default, most frequently applied** test because most regulations do not produce total wipeouts and are not development-permit exactions.
- *Lucas* is narrow and categorical — a bright-line rule reserved for the rare case of total deprivation.
- *Nollan/Dolan* apply specifically to the **exactions context** (permit conditions), not general land-use regulation, and impose a heightened, government-favors-less standard reflecting concern about leveraging permit power to extract unrelated concessions.
- [Unverified] The precise contours of "rough proportionality" and how courts quantify proportionality (monetary versus in-kind exactions) continue to be litigated and may vary by jurisdiction and factual record.

### Related Topics

- *Pennsylvania Coal Co. v. Mahon* and the origins of regulatory takings doctrine
- *Loretto v. Teleprompter Manhattan CATV Corp.* — per se physical takings
- *Palazzolo v. Rhode Island* — notice of pre-existing regulation and takings claims
- *Koontz v. St. Johns River Water Management District* — exactions and monetary conditions
- The "parcel as a whole" (denominator) problem in takings analysis
- State environmental review statutes (e.g., wetlands, coastal zone management) and takings exposure
- Inverse condemnation actions and procedural mechanics for asserting a takings claim
- *Murr v. Wisconsin* — defining the relevant parcel across contiguous lots
- Exhaustion and ripeness requirements for federal takings claims (*Knick v. Township of Scott*)