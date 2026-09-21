## Reliability Terminology and Metrics


### Overview

Reliability engineering quantifies the probability that a product, component, or system will perform its intended function without failure for a specified period under specified operating conditions. In precision metrology and quality control, reliability metrics underpin calibration interval determination, gauge lifecycle management, and warranty/field-performance prediction, translating raw failure data into the probabilistic language needed for data-driven maintenance and design decisions.

**Key Points**

- Reliability is formally defined as a probability, $R(t)$, ranging from 0 to 1, and is always specified with respect to a stated time period and operating condition — "reliability" without a time reference is incomplete
- The foundational relationship connects reliability, the probability density function of failure $f(t)$, the cumulative distribution function of failure $F(t)$, and the hazard (failure rate) function $\lambda(t)$
- The Weibull distribution is the most widely used statistical model in reliability engineering due to its flexibility in modeling different failure behaviors (infant mortality, random failure, wear-out) with a single distribution family
- In metrology specifically, reliability concepts directly inform calibration interval analysis — treating "out of tolerance at next calibration" as the failure event of interest

### Core Definitions

| Term | Definition |
| --- | --- |
| **Reliability, $R(t)$** | Probability that an item performs its intended function without failure over time $t$, under stated conditions |
| **Unreliability, $F(t)$** | Probability of failure by time $t$; $F(t) = 1 - R(t)$ |
| **Failure rate, $\lambda(t)$** | Instantaneous rate of failure at time $t$, conditional on survival to that point (the hazard function) |
| **MTBF** | Mean Time Between Failures — average time between failures for a repairable system |
| **MTTF** | Mean Time To Failure — average time to failure for a non-repairable item |
| **MTTR** | Mean Time To Repair — average time required to restore a failed, repairable system to service |
| **Availability** | Proportion of time a system is operational and ready for use, combining MTBF and MTTR |

### The Reliability Function and Its Relationships

The reliability function is derived from the cumulative distribution function of the time-to-failure random variable $T$:

$$R(t) = 1 - F(t) = P(T > t)$$

The probability density function $f(t)$ and the hazard function $\lambda(t)$ relate to $R(t)$ as:

$$f(t) = -\frac{dR(t)}{dt}$$



$$\lambda(t) = \frac{f(t)}{R(t)}$$

This last relationship is central: the hazard function describes the instantaneous failure rate of items that have already survived to time $t$, distinct from $f(t)$, which describes the unconditional failure density across the entire original population.

### Mean Time Between Failures and Mean Time to Failure

$$MTBF = \int_{0}^{\infty} R(t) \, dt$$

For a constant failure rate (the exponential distribution case, common in the "useful life" phase of many components):

$$R(t) = e^{-\lambda t}, \qquad MTBF = \frac{1}{\lambda}$$

**Example**

A batch of calibrated pressure transducers is tracked for out-of-tolerance failures over a 2-year monitoring period. 40 units are tracked; 6 fail (drift out of tolerance) during the period, accumulating a total of 68,000 operating hours across all units before failure or censoring.

$$MTBF = \frac{68{,}000 \text{ hours}}{6 \text{ failures}} \approx 11{,}333 \text{ hours}$$

Note: MTBF is a population-average statistic and does not by itself indicate the underlying failure distribution shape — two populations with identical MTBF can have very different reliability profiles (e.g., one with mostly early failures, another with mostly wear-out failures), which is why the Weibull shape parameter is often reported alongside MTBF for a fuller picture.

### The Bathtub Curve

The bathtub curve is the classical conceptual model describing how hazard rate typically varies over a product's lifecycle, divided into three phases.

**Diagram: Bathtub Curve (svg_diagram)**

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 560 280">
<title>Bathtub Curve — Failure Rate vs Time (svg_diagram)</title>
<line x1="50" y1="230" x2="530" y2="230" stroke="#333" stroke-width="2" />
<line x1="50" y1="20" x2="50" y2="230" stroke="#333" stroke-width="2" />
<text x="290" y="260" font-size="12" text-anchor="middle">Time</text>
<text x="20" y="130" font-size="12" text-anchor="middle" transform="rotate(-90 20 130)">Failure Rate λ(t)</text>
<path d="M 55 60 Q 130 220 210 225" fill="none" stroke="#2b6cb0" stroke-width="3" />
<path d="M 210 225 L 380 225" fill="none" stroke="#2f855a" stroke-width="3" />
<path d="M 380 225 Q 460 225 525 40" fill="none" stroke="#c05621" stroke-width="3" />
<line x1="210" y1="30" x2="210" y2="225" stroke="#999" stroke-width="1" stroke-dasharray="4,3" />
<line x1="380" y1="30" x2="380" y2="225" stroke="#999" stroke-width="1" stroke-dasharray="4,3" />

<text x="130" y="45" font-size="11" text-anchor="middle" fill="`#1a365d`" font-weight="bold">Infant Mortality</text>

<text x="130" y="58" font-size="9" text-anchor="middle" fill="`#1a365d`">(decreasing λ)</text>

<text x="295" y="200" font-size="11" text-anchor="middle" fill="`#1c4532`" font-weight="bold">Useful Life</text>

<text x="295" y="213" font-size="9" text-anchor="middle" fill="`#1c4532`">(constant λ)</text>

<text x="450" y="45" font-size="11" text-anchor="middle" fill="`#652b19`" font-weight="bold">Wear-Out</text>

<text x="450" y="58" font-size="9" text-anchor="middle" fill="`#652b19`">(increasing λ)</text>

</svg>

- **Infant mortality (decreasing $\lambda$)**: early failures caused by manufacturing defects, installation errors, or latent material flaws; addressed through burn-in testing or screening
- **Useful life (constant $\lambda$)**: random failures unrelated to age, well-modeled by the exponential distribution; this is the phase where MTBF-based calculations are most valid
- **Wear-out (increasing $\lambda$)**: failures driven by accumulated degradation, fatigue, or wear; addressed through preventive replacement or condition-based maintenance rather than run-to-failure

[Inference: the bathtub curve is a widely taught conceptual model rather than a universal empirical law — actual failure rate profiles vary substantially by component type and failure mechanism, and many components (particularly electronic components without moving parts) exhibit little to no observable wear-out phase within their practical service life.]

### The Weibull Distribution in Reliability Analysis

The Weibull distribution is the most common statistical model for reliability data, because its shape parameter $\beta$ can represent all three bathtub curve phases within a single distribution family.

$$R(t) = e^{-(t/\eta)^{\beta}}$$

where $\eta$ is the scale parameter (characteristic life) and $\beta$ is the shape parameter.

| Shape Parameter $\beta$ | Interpretation |
| --- | --- |
| $\beta < 1$ | Decreasing failure rate — infant mortality phase |
| $\beta = 1$ | Constant failure rate — equivalent to the exponential distribution, useful life phase |
| $\beta > 1$ | Increasing failure rate — wear-out phase |

### Availability

$$Availability = \frac{MTBF}{MTBF + MTTR}$$

This metric is distinct from OEE's Availability component (which measures scheduled-time utilization) but shares conceptual roots — both express the proportion of time a system is usable, one from a reliability/maintainability perspective and one from a production-scheduling perspective.

### Application to Calibration Interval Analysis

**Example**

A metrology lab applies reliability concepts to determine an appropriate calibration interval for a gauge family. Historical calibration records show 15 of 200 gauges were found out-of-tolerance at their most recent calibration event, after an average interval of 12 months. Treating "found out of tolerance" as the failure event:

$$\hat{R}(12 \text{ months}) = 1 - \frac{15}{200} = 0.925 \; (92.5\%)$$

If the lab's target reliability (proportion of gauges expected to remain in-tolerance through the interval) is 95%, this result indicates the current 12-month interval is too long for this gauge family, and a shorter interval — or investigation into a specific root cause of the drift — is warranted. This reliability-based approach (related to the S2 method referenced in calibration interval analysis literature) provides a statistically defensible basis for interval adjustment, rather than relying on manufacturer default recommendations alone.

### Mermaid: Reliability Metric Relationships

```mermaid
flowchart TD
    A[Collect failure/censoring<br/>data over time] --> B[Fit distribution:<br/>Weibull, exponential, etc.]
    B --> C[Derive R(t), F(t), f(t), λ(t)]
    C --> D[Calculate MTBF/MTTF]
    D --> E{Repairable<br/>system?}
    E -->|Yes| F[Combine with MTTR<br/>to compute Availability]
    E -->|No| G[Use MTTF for<br/>replacement planning]
    C --> H[Apply to calibration<br/>interval analysis]
```

### Common Pitfalls

- Reporting MTBF without the underlying distribution shape — a high MTBF can mask a population with a meaningful early-failure subgroup if the shape parameter is not also considered
- Applying the constant-failure-rate (exponential) assumption to wear-out-dominated failure data, which understates near-term risk and overstates long-term reliability
- Treating MTBF as a guaranteed minimum lifetime rather than a population-average statistic; individual unit lifetimes vary substantially around the mean, particularly under non-constant hazard rates
- Confusing MTBF (repairable systems, time between successive failures) with MTTF (non-repairable items, time to first and only failure) — the two are calculated and interpreted differently and are not interchangeable terms

**Related Topics**

- Weibull analysis and life data analysis
- Calibration interval analysis
- Failure mode and effects analysis
- Preventive and predictive maintenance
- Statistical Process Control (SPC)
- Total Productive Maintenance (TPM)
- Accelerated life testing