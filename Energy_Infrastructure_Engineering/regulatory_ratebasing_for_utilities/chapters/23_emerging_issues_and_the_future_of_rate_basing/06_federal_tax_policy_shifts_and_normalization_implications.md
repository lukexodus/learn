## Federal Tax Policy Shifts and Normalization Implications


### Overview

Federal tax policy directly shapes rate-basing outcomes through two primary channels: (1) the corporate income tax rate, which flows into the revenue requirement's tax component and the after-tax weighted average cost of capital calculation, and (2) tax depreciation rules (particularly bonus depreciation and the pace of cost recovery), which interact with the federal **normalization** requirement — a statutory constraint on how utilities may reflect accelerated tax depreciation in ratemaking. Recent federal legislation has materially changed the depreciation landscape, making this a genuinely active, dated area rather than a static conceptual topic.

### The Normalization Requirement: Statutory Basis

The core rule is codified at IRC §168(i)(9)(A). To use accelerated tax depreciation methods (rather than being limited to slower ADS-equivalent methods), a utility must, for ratemaking purposes, use a method of depreciation for public utility property that is the same as, and a depreciation period that is not shorter than, the method and period used to compute regulatory depreciation expense for cost-of-service purposes. [Tax Notes](https://www.taxnotes.com/research/federal/irs-private-rulings/letter-rulings-technical-advice/utilitys-rate-base-adjustments-wont-violate-normalization-rules/2b690)

- If tax depreciation under §168 produces a different (larger, earlier) deduction than the regulatory books would show under §167-based methods, the utility must make adjustments to a reserve reflecting the deferral of taxes resulting from that difference — this reserve is the **Accumulated Deferred Income Tax (ADIT)** balance [Tax Notes](https://www.taxnotes.com/research/federal/irs-private-rulings/letter-rulings-technical-advice/utilitys-rate-base-adjustments-wont-violate-normalization-rules/2b690)
- Violating normalization is a significant compliance risk: a utility found to violate §168(i)(9) can lose its right to use accelerated depreciation for tax purposes on the affected property going forward, which is a materially adverse tax outcome, not merely a regulatory disagreement

### Why Normalization Exists in Rate-Basing Terms

- **Key Points**
  - Accelerated tax depreciation creates a timing difference: the utility deducts more depreciation for tax purposes early in an asset's life than it reflects in regulatory book depreciation, generating a tax benefit before the corresponding book expense is recognized
  - Without normalization, a commission could "flow through" this tax timing benefit immediately to ratepayers via lower near-term rates, effectively front-loading the tax benefit into current rates rather than spreading it over the asset's life to match book depreciation
  - Congress views this as a federal tax policy interest (preserving the intended investment incentive of accelerated depreciation) rather than purely a state ratemaking matter, which is why the requirement is embedded in the Internal Revenue Code itself rather than left to state discretion
  - The ADIT reserve created under normalization functions as a rate base offset (a cost-free source of capital contributed implicitly by ratepayers through deferred tax collection), directly affecting the rate base calculation

### ADIT as a Rate Base Component

$$\text{Rate Base} = \text{Gross Plant} - \text{Accumulated Depreciation} - \text{ADIT} + \text{Working Capital} + \text{Other Additions}$$

- ADIT is typically subtracted from rate base because it represents deferred tax collections from ratepayers that the utility has not yet remitted to the IRS, functioning similarly to zero-cost debt financing
- Errors or disputes in ADIT calculation — including from major tax law changes — have direct, often substantial, rate base and revenue requirement effects, making this a frequently litigated technical area in rate cases following any significant federal tax legislation

### Federal Tax Policy Shift: The 2025 One Big Beautiful Bill Act (OBBBA)

The most significant recent federal tax development affecting utility rate-basing is the One Big Beautiful Bill Act, which materially changed the bonus depreciation landscape:

- The Act, enacted July 4, 2025, permanently extends 100% bonus depreciation under Section 168(k) and introduces a new elective 100% depreciation allowance under Section 168(n) for qualified production property [PwC](https://www.pwc.com/us/en/services/tax/library/pwc-ob3-provides-bonus-depreciation-qualified-production-property.html)[PwC](https://www.pwc.com/us/en/services/tax/library/pwc-ob3-provides-bonus-depreciation-qualified-production-property.html)
- The OBBBA makes permanent 100% bonus depreciation for most property acquired after January 19, 2025, reversing what had been a scheduled phase-down [RSM US](https://rsmus.com/insights/services/business-tax/obba-tax-bonus-depreciation.html)
- Prior law (under the 2017 Tax Cuts and Jobs Act) had set bonus depreciation on a declining schedule — the deduction was set to phase out by 20% annually from 2023 through 2026, reaching 0% in 2027, with the rate standing at 40% for tax year 2025 before OBBBA intervened [Warren Averett](https://warrenaverett.com/insights/one-big-beautiful-bill-bonus-depreciation/)
- The OBBBA eliminates the phaseout schedule entirely, restoring 100% bonus depreciation for qualifying property placed in service after January 19, 2025, and marks the first time Congress has made 100% bonus depreciation continuously ongoing rather than a temporary provision subject to future expiration [Comerica](https://www.comerica.com/insights/commercial-banking/assorted-commercial/bonus-depreciation.html)[Comerica](https://www.comerica.com/insights/commercial-banking/assorted-commercial/bonus-depreciation.html)

**Important normalization caveat**: Bonus depreciation under §168(k) is generally treated as public utility property-ineligible or subject to specific normalization-consistent treatment in many contexts — historically, public utility property has often been excluded from or specially treated under bonus depreciation provisions precisely because of interaction with the normalization requirement. [Unverified] The precise current interaction between the OBBBA's 100% bonus depreciation provisions and the public utility property exclusion/normalization treatment under §168(k)(9) and related regulations was not confirmed in the sources reviewed for this content; practitioners should verify the current applicability of bonus depreciation specifically to public utility property against current IRS guidance and normalization consistency rules, since this is a technically detailed area where general bonus depreciation commentary (aimed at non-utility taxpayers) may not directly translate to utility rate-basing treatment.

### Corporate Tax Rate: Stable, Not a Current Shift Driver

Unlike depreciation rules, the federal corporate income tax rate itself has not changed recently:

- As of 2026, the federal corporate income tax rate remains 21%, the flat rate established under the 2017 Tax Cuts and Jobs Act [SmartAsset](https://smartasset.com/taxes/corporate-tax-rate-per-state)
- The federal C corporation rate remains fixed at 21% under TCJA and is unchanged by OBBBA as of tax year 2026 [Corporatetaxadvisors](https://corporatetaxadvisors.com/corporate-tax-planning-in-2026-strategies-law-changes-and-practical-steps-for-businesses/)

This matters for rate-basing because the corporate tax rate is a direct input to the revenue requirement's tax allowance and the after-tax cost of capital calculation:

$$\text{After-Tax WACC} = \left(\frac{E}{V}\right) \times r_e + \left(\frac{D}{V}\right) \times r_d \times (1 - T_c)$$

Since $T_c$ (the statutory corporate rate) has remained stable at 21% since 2018, the primary federal tax "shift" affecting current rate cases is depreciation-driven (ADIT dynamics), not rate-driven — a distinction that matters because the 2017 TCJA rate cut (35% to 21%) previously triggered a large, one-time wave of "excess ADIT" refund proceedings across nearly every state, and the current OBBBA depreciation change is mechanically different (affecting the pace of future ADIT accrual rather than requiring a one-time revaluation of an existing ADIT stock).

### Distinguishing the 2017 TCJA Rate-Cut Precedent From the 2025 OBBBA Depreciation Change

| Aspect | 2017 TCJA (Rate Cut) | 2025 OBBBA (Bonus Depreciation) |
| --- | --- | --- |
| Mechanism | Reduced statutory rate from 35% to 21% | Restored/made permanent 100% bonus depreciation |
| Immediate rate-basing effect | Created "excess ADIT" — previously accrued deferred tax reserves calculated at 35% became excessive at the new 21% rate | Affects the pace of future ADIT accrual on newly acquired property; does not revalue existing ADIT stock |
| Typical regulatory response | Amortization of excess ADIT back to ratepayers, often via IRS-mandated Average Rate Assumption Method (ARAM) for protected (normalized) excess ADIT | Primarily affects prospective rate case ADIT projections and cash flow/tax timing assumptions |
| Litigation intensity | High — nearly every state utility commission processed excess ADIT proceedings following TCJA | [Inference] Likely to generate normalization-consistency and prudence questions in prospective rate cases as utilities update ADIT forecasting methodology, though the nature of the dispute differs structurally from a rate-cut revaluation event |

### Excess/Deficient ADIT and the Average Rate Assumption Method (ARAM)

Because this remains a relevant reference point for understanding how future federal tax rate changes would be processed:

- Normalization rules under §168(i)(9) and Treasury Regulation §1.167(l)-1 govern the scope of deferred tax normalization requirements and the appropriate methodology for reduction of ADIT balances when circumstances (such as a statutory rate change or a net operating loss carryforward) affect the ADIT calculation [Tax Notes](https://www.taxnotes.com/research/federal/irs-private-rulings/letter-rulings-technical-advice/irs-rules-on-utilitys-issues-under-normalization-requirements/2c83n)
- The IRS-prescribed Average Rate Assumption Method (ARAM) is generally required for amortizing "protected" excess ADIT associated with public utility property back to ratepayers over the remaining book life of the underlying assets, rather than allowing accelerated flow-back, which would itself violate normalization principles
- [Inference] Should Congress enact a future corporate rate change, the ARAM-based amortization framework established through TCJA-era precedent would likely serve as the template for regulatory treatment, though this is inference from precedent rather than a guaranteed outcome, since Congress could in principle alter the applicable normalization statute itself in future legislation.

### Practical Example: Capital Expenditure Timing Under OBBBA Bonus Depreciation

**Example**

> A utility planning a large grid modernization capital program must now incorporate permanent 100% bonus depreciation (where applicable to the specific asset class and subject to normalization-consistent treatment) into its multi-year tax and cash flow forecasting, replacing the prior planning assumption of a declining bonus percentage phasing to zero by 2027.
>
> Rate case testimony addressing ADIT projections filed after mid-2025 should reflect the OBBBA's permanent extension rather than the prior TCJA phase-down schedule; testimony or forecasts still assuming a declining bonus depreciation percentage toward 2027 would be based on superseded law and would likely draw challenge from opposing parties or commission staff during discovery.

### Regulatory Process Flow for Federal Tax Law Changes

```mermaid
flowchart TD
    A[Federal Tax Legislation Enacted] --> B{Type of Change}
    B -->|Corporate Rate Change| C[Revalue Existing ADIT Stock]
    B -->|Depreciation Method/Bonus Change| D[Adjust Prospective ADIT Accrual Rate]
    C --> E[Identify Protected vs Unprotected Excess/Deficient ADIT]
    E --> F[Protected ADIT: ARAM Amortization Required]
    E --> G[Unprotected ADIT: Commission Discretion on Flow-Back Timing]
    D --> H[Update Rate Case Tax Forecasting Methodology]
    F --> I[File ADIT Amortization Schedule in Rate Case or Compliance Filing]
    G --> I
    H --> I
    I --> J[Commission Review for Normalization Consistency]
    J --> K{Consistent with IRC 168(i)(9)?}
    K -->|Yes| L[Approved - Reflected in Rate Base and Revenue Requirement]
    K -->|No| M[Risk of Normalization Violation - Loss of Accelerated Depreciation Eligibility]
```

### Consistency Requirement Nuances

The normalization consistency requirement applies with some methodological flexibility, as clarified in IRS guidance on utility-specific ratemaking calculations:

- The consistency requirement under §168(i)(9)(B) applies separately to each component of the projected revenue requirement, meaning different methodologies can potentially be used for different components (e.g., point-in-time balances versus forecasted additions) without violating normalization, provided each component is internally consistent [Tax Notes](https://www.taxnotes.com/research/federal/irs-private-rulings/letter-rulings-technical-advice/irs-rules-on-utilitys-compliance-with-normalization-rules/7dbmt)
- This component-level flexibility is relevant to utilities using forward-looking or partially forecasted test years, a ratemaking approach that has become more common as commissions seek to reduce regulatory lag (see Multi-Year Rate Plans)

### Interaction With Other Emerging Rate-Basing Topics

Federal tax policy shifts intersect with several other emerging rate-basing issues covered elsewhere in this material:

- **Grid modernization and electrification investment**: Permanent 100% bonus depreciation (where applicable) changes the tax cash flow profile of large capital programs, potentially affecting utility financing strategy and, indirectly, cost of capital assumptions in rate cases
- **Affordability pressure**: Tax normalization disputes and ADIT calculation errors can have material, sometimes multi-million-dollar, rate base impacts, making accurate tax modeling a meaningful (if technical and low-visibility) affordability factor
- **Securitization mechanisms**: Tax treatment of securitized debt and associated ADIT implications is a specialized sub-area often addressed through separate IRS private letter rulings specific to the securitization structure used

### Related Topics

- Cost of Capital and Return on Equity Determination
- Accumulated Deferred Income Tax (ADIT) Calculation Methodologies
- Excess/Deficient ADIT and the Average Rate Assumption Method (ARAM)
- Multi-Year Rate Plans and Forward-Looking Test Year Methodology
- Grid Modernization and Resilience Investment Recovery
- Storm Cost Recovery and Securitization Mechanisms
- Prudence Review Standards in Capital Cost Recovery
- IRS Private Letter Rulings on Utility Normalization Compliance
- State Tax Conformity and Decoupling From Federal Depreciation Rules
- Working Capital and Rate Base Component Analysis