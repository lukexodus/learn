## Prepayment Risk and Modeling


### Overview

Prepayment risk is the uncertainty in the *timing* of principal repayment on amortizing collateral — most prominently mortgages, but also relevant to auto loans, equipment leases, and other installment receivables — arising from a borrower's option to repay principal ahead of the contractual schedule. Unlike credit risk, prepayment risk does not affect the ultimate amount an investor receives on performing collateral, but it materially affects *when* that principal is returned, which drives duration, convexity, and reinvestment risk for the security holder. This entry consolidates the modeling frameworks used to quantify and price prepayment risk, extending the product-specific prepayment discussion introduced in the MBS structures entry.

### Sources of Prepayment

**Key Points**

- **Refinancing**: borrowers repay an existing loan by taking out a new loan, typically motivated by a decline in prevailing interest rates relative to their existing loan's rate — the dominant, most rate-sensitive component of prepayment behavior for mortgages
- **Housing turnover / asset sale**: borrowers sell the underlying collateral (a home, vehicle, or equipment) and repay the loan from sale proceeds as part of relocation, upgrading, or other life-cycle events — generally less interest-rate-sensitive than refinancing, driven more by demographic, economic, and seasonal factors
- **Curtailment**: partial voluntary prepayment of principal without full loan payoff, common in some consumer loan types
- **Default-related prepayment**: payoff resulting from a defaulted loan's liquidation/insurance proceeds, which is sometimes modeled jointly with, or separately from, voluntary prepayment depending on the modeling framework (this is credit-driven principal return, distinct from voluntary prepayment, but has similar cash-flow-timing effects on the investor)

### Prepayment Conventions: PSA, CPR, and SMM

**Key Points**

- **CPR (Conditional Prepayment Rate)**: the annualized percentage of the remaining pool principal balance expected to prepay in a given period, assuming that rate persists — the standard "headline" prepayment speed convention
- **SMM (Single Monthly Mortality)**: the monthly-equivalent prepayment rate, related to CPR by:

$$SMM = 1-(1-CPR)^{1/12}$$

- **PSA (Public Securities Association) Standard Prepayment Model**: a benchmark seasoning ramp assuming CPR rises linearly from 0% at loan age 0 to 6% at loan age 30 months, then holds flat at 6% CPR thereafter — this benchmark is referred to as "100% PSA," with other speeds expressed as multiples (e.g., "150% PSA" scales every point on the ramp by 1.5x, "50% PSA" by 0.5x)
- The PSA convention specifically reflects *seasoning* effects (newer loans prepay more slowly, partly reflecting the time needed for relocation-driven or refinancing-driven turnover to build) independent of interest rate level — it is a base-case seasoning curve, not itself a full behavioral prepayment model

```mermaid
flowchart LR
    A[Loan Age 0 months] --> B[CPR ramps 0% to 6% linearly]
    B --> C[Loan Age 30 months: CPR reaches 6%]
    C --> D[CPR holds flat at 6% thereafter]
    D --> E[This is the 100% PSA benchmark curve]
```

### Behavioral Prepayment Models

**Key Points**

- Production prepayment models used by dealers, agencies, and analytics vendors extend beyond the simple PSA seasoning ramp to incorporate multiple behavioral drivers simultaneously:
  - **Refinancing incentive**: typically modeled as a function of the spread between the borrower's existing note rate and prevailing current mortgage rates — the larger the incentive, the higher the modeled refinancing-driven prepayment speed, often via an S-curve relationship (prepayment response is muted for small incentives, accelerates sharply past a threshold, then plateaus as most "in the money" borrowers have already refinanced)
  - **Burnout**: the empirically observed phenomenon that prepayment speeds for a given refinancing incentive level *decline* over time as a pool is repeatedly exposed to that incentive, since the more rate-sensitive/opportunistic borrowers within the pool have already refinanced, leaving a residual population that is systematically less responsive (due to credit constraints, inertia, or other frictions)
  - **Seasonality**: housing turnover exhibits seasonal patterns (typically higher in spring/summer months in many markets), modeled as a multiplicative seasonal adjustment factor
  - **Home price appreciation / equity**: borrower ability to refinance or sell can depend on accumulated home equity, particularly relevant for distinguishing prepayment behavior across vintages experiencing different home price environments
  - **Loan-specific characteristics**: loan size (larger loans often prepay faster, since the absolute dollar refinancing savings is larger for a given rate incentive), loan age, geography, and borrower credit profile all contribute to observed prepayment heterogeneity across a pool

**S-Curve Refinancing Response (Illustrative)**

**Example**

A typical S-curve relationship between refinancing incentive (current note rate minus prevailing market rate) and modeled CPR might behave as follows:

1. At a small or negative incentive (borrower's rate is at or below market), modeled CPR stays near the base "housing turnover" speed (e.g., 6–8% CPR), since there is little financial benefit to refinancing
2. As incentive rises past roughly 50–100 basis points, CPR accelerates sharply, reflecting the point at which refinancing costs are outweighed by rate savings for an increasing share of borrowers
3. At very high incentive levels (e.g., 200+ basis points), CPR approaches a plateau/ceiling, since even highly rate-sensitive borrowers have already been captured, and remaining non-prepaying borrowers reflect credit constraints, inertia, or other frictions unlikely to be overcome by further rate incentive

[Unverified] The specific incentive thresholds and plateau CPR levels illustrated above are for conceptual purposes only; actual model calibration varies by vendor, vintage, and current market conditions, and should be sourced from a specific production prepayment model's documentation for any actual analytical application.

### Option-Adjusted Spread (OAS) and Prepayment-Embedded Valuation

**Key Points**

- Because mortgage prepayment is fundamentally a borrower option (economically similar to a callable bond, where the "call" is exercised via refinancing), MBS/CMO valuation requires an **option-adjusted** framework rather than simple static cash flow discounting at a single prepayment speed assumption
- **OAS analysis** simulates many interest rate paths (via a term structure model, e.g., a short-rate or forward-rate model with appropriate volatility calibration), applies the prepayment model's rate-path-dependent prepayment projection along each simulated path, discounts the resulting cash flows along each path, and averages across paths to obtain a model price; the OAS is the constant spread added to the discounting curve that reconciles this model price to the security's observed market price
- OAS therefore isolates the compensation the market is providing for risks *beyond* the modeled prepayment optionality itself (credit risk for non-agency collateral, liquidity premium, model risk, and any mispricing relative to the specific prepayment model used) — a materially different quantity from simple nominal spread, since nominal spread does not account for the value embedded in the prepayment option

$$Price_{model} = \frac{1}{N}\sum_{i=1}^{N}\sum_{t}\frac{CF_{i,t}}{(1+r_{i,t}+OAS)^t}$$

where the sum is over $N$ simulated interest rate paths $i$, with path-specific discount rates $r_{i,t}$ and path-specific (prepayment-model-dependent) cash flows $CF_{i,t}$; OAS is solved for such that $Price_{model}$ equals the observed market price.

### Negative Convexity and Duration Effects

**Key Points**

- Prepayment-sensitive securities exhibit **negative convexity**: as rates fall, prepayments accelerate (borrowers refinance), shortening the security's effective duration exactly when a longer duration would have been more valuable; as rates rise, prepayments slow (extension), lengthening effective duration exactly when a shorter duration would have been preferable
- **Effective duration** and **effective convexity** for prepayment-sensitive securities must be computed via the OAS/simulation framework described above (bumping rates up and down and re-running the full prepayment-path valuation), rather than via simple analytical duration formulas that assume fixed cash flows, since the cash flows themselves change with the rate scenario
- This negative convexity is the fundamental reason IO strips, most pass-throughs, and many CMO tranches require active hedging (often using interest rate options or dynamically-adjusted hedges) to manage duration drift as rates move, in contrast to fixed-cash-flow bonds where duration changes are comparatively small and predictable

### Non-Mortgage Prepayment Modeling: Auto and Equipment Leases

**Key Points**

- Auto loan and equipment lease prepayment is generally **less interest-rate-sensitive** than mortgage prepayment, since the dollar savings from refinancing a smaller-balance, shorter-term auto loan are typically less economically compelling relative to the effort involved, compared to a large-balance, long-term mortgage
- Auto/equipment ABS prepayment modeling instead emphasizes **turnover-driven prepayment** (vehicle trade-in/sale, lease-end return/buyout decisions) and **default-related payoff**, often modeled via an **ABS (Absolute Prepayment Speed)** convention — expressing prepayment as a percentage of the *original* pool balance per period, rather than CPR's percentage of the *remaining* balance — reflecting the more level, less rate-driven prepayment pattern typical of amortizing installment collateral
- [Inference] The lower rate sensitivity of auto/equipment prepayment relative to mortgages is a broadly accepted market characterization reflecting the smaller absolute economic incentive to refinance small-balance, short-tenor loans, though the degree of rate sensitivity can still vary by lender, loan size, and prevailing consumer refinancing product availability.

### Model Risk in Prepayment Assumptions

**Key Points**

- Prepayment models are calibrated to historical borrower behavior, which may not persist unchanged into future periods if underlying drivers shift — e.g., changes in refinancing origination costs/frictions, shifts in mortgage servicing technology affecting refinancing ease, or structural changes in housing/credit markets can all alter the realized prepayment response to a given rate incentive relative to historical calibration
- **Model risk** in this context specifically refers to the risk that the *behavioral relationship itself* (not just the future path of interest rates) differs from what the model assumes — a risk distinct from, and additive to, ordinary interest rate risk
- Differences across vendor prepayment models (e.g., differing burnout specifications, differing S-curve calibrations, differing treatment of loan-level heterogeneity) can produce materially different OAS and duration outputs for the *same* security and the *same* assumed rate scenario set, meaning OAS comparisons across market participants using different models require care in interpretation

### Conclusion

**Conclusion**

Prepayment risk arises from the embedded borrower option to repay principal ahead of schedule, and its quantification requires moving beyond simple deterministic speed assumptions (PSA/CPR) toward full behavioral models capturing refinancing incentive, burnout, seasonality, and loan-level heterogeneity, integrated within an option-adjusted, multi-path interest rate simulation framework. The resulting negative convexity — duration shortening exactly when rates fall and extending exactly when rates rise — is the defining risk characteristic distinguishing prepayment-sensitive collateral from fixed-cash-flow instruments, and the model risk inherent in calibrating borrower behavioral response remains a distinct, additive risk layered on top of ordinary interest rate uncertainty.

**Related Topics**

- Mortgage Backed Securities Structures: CMO Tranching of Prepayment Risk
- Option-Adjusted Spread (OAS) Methodology and Interest Rate Path Simulation
- Negative Convexity and Duration Hedging Strategies for MBS
- Asset Backed Securities and Collateral Pools: ABS Convention and Turnover-Driven Prepayment
- Burnout Modeling and Loan-Level Heterogeneity in Prepayment Forecasting
- Term Structure Models for Interest Rate Path Simulation
- IO/PO Strip Valuation Under Competing Prepayment Model Assumptions