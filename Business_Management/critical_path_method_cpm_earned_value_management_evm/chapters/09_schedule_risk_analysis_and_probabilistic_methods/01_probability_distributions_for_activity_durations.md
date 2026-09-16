## Probability Distributions for Activity Durations


### Purpose in Schedule Risk Analysis

Deterministic CPM assigns a single fixed duration to each activity, producing one deterministic finish date. Probabilistic schedule risk analysis (e.g., Monte Carlo simulation) replaces fixed durations with probability distributions, capturing the natural variability in how long an activity might actually take. This enables computation of a distribution of possible project finish dates rather than a single point estimate.

**Key Points**

- Distributions represent uncertainty, not error — even well-estimated activities have inherent variability.
- The choice of distribution shape affects simulation outputs (P50, P80, contingency reserve calculations).
- Distributions are typically parameterized from three-point estimates: optimistic, most likely, pessimistic.

### Three-Point Estimating Foundation

Most activity duration distributions are built from three estimates:

- $O$ = Optimistic duration (best case, low probability)
- $M$ = Most likely duration (mode)
- $P$ = Pessimistic duration (worst case, low probability)

These feed directly into the shape parameters of the distributions below.

### Triangular Distribution

**Key Points**

- Simplest distribution requiring only $O$, $M$, $P$.
- Linear probability density rising from $O$ to $M$, then falling from $M$ to $P$.
- Commonly used when data is sparse and only expert judgment (three-point estimate) is available.

Mean:

$$\mu = \frac{O + M + P}{3}$$

Probability density function:

$$f(x) = \begin{cases} \dfrac{2(x-O)}{(P-O)(M-O)} & O \le x \le M \\[6pt] \dfrac{2(P-x)}{(P-O)(P-M)} & M < x \le P \end{cases}$$

**Example**

For an activity with $O=4$, $M=6$, $P=14$ days:

$$\mu = \frac{4+6+14}{3} = 8 \text{ days}$$

The triangular mean (8 days) is pulled toward the pessimistic tail, illustrating how skewed distributions shift the expected duration above the most-likely estimate.

### PERT (Beta) Distribution

**Key Points**

- Historically the standard in PERT (Program Evaluation and Review Technique).
- Smoother, bell-like curve compared to the triangular's sharp linear segments.
- Weights the most-likely value more heavily than triangular does.

Classic PERT mean and standard deviation approximation:

$$\mu = \frac{O + 4M + P}{6}$$



$$\sigma = \frac{P - O}{6}$$

**Example**

Using the same $O=4$, $M=6$, $P=14$:

$$\mu = \frac{4 + 4(6) + 14}{6} = \frac{42}{6} = 7 \text{ days}$$



$$\sigma = \frac{14-4}{6} = 1.67 \text{ days}$$

[Unverified: The classic PERT formula is a widely used approximation of the Beta distribution's mean/variance under specific shape assumptions; it does not exactly match a general Beta distribution fit and its accuracy varies with the degree of skew.]

### Beta Distribution (General Form)

The full Beta distribution allows explicit shape parameters $\alpha$ and $\beta$ rather than relying on the PERT approximation, giving finer control over skewness and kurtosis. Scheduling software (e.g., Primavera Risk Analysis, @RISK) often implements a "Beta-PERT" variant, using $O$, $M$, $P$ plus a shape/confidence factor $\lambda$ (default typically 4, matching classic PERT) to derive $\alpha$ and $\beta$:

$$\alpha = 1 + \lambda \cdot \frac{M - O}{P - O}$$



$$\beta = 1 + \lambda \cdot \frac{P - M}{P - O}$$

Increasing $\lambda$ concentrates probability mass more tightly around $M$, reducing variance; decreasing $\lambda$ widens the spread.

### Normal (Gaussian) Distribution

**Key Points**

- Used when duration variability is believed to be symmetric around the mean with no hard bounds.
- Less common for individual activities (durations can't go below zero) but often used at the aggregate/summary level, or when historical data supports it.
- Defined fully by $\mu$ and $\sigma$.

$$f(x) = \frac{1}{\sigma\sqrt{2\pi}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}$$

**Key Points**

- Risk: unbounded tails can generate negative durations in simulation unless truncated.
- Central Limit Theorem justifies using Normal distributions for summed durations across many independent activities, even if individual activity distributions are non-Normal.

### Uniform Distribution

**Key Points**

- All durations between a minimum and maximum are equally likely.
- Used when there is genuinely no basis to favor any duration within a range (high uncertainty, no historical precedent).

$$f(x) = \frac{1}{b-a}, \quad a \le x \le b$$



$$\mu = \frac{a+b}{2}$$

### Lognormal Distribution

**Key Points**

- Right-skewed, bounded at zero — appropriate for durations that cannot be negative and have a long tail of potential delay (common in construction, permitting, procurement).
- Often better represents real-world activity delay behavior than Normal, since schedule overruns are typically larger in magnitude than schedule underruns.

$$f(x) = \frac{1}{x\sigma\sqrt{2\pi}} e^{-\frac{(\ln x - \mu)^2}{2\sigma^2}}, \quad x > 0$$

### Comparative Shape Diagram

```mermaid
flowchart TB
    subgraph Distributions Comparison (svg_diagram)
    T["Triangular: linear rise/fall<br/>O, M, P only"]
    B["Beta/PERT: smooth curve<br/>weighted toward M"]
    N["Normal: symmetric bell<br/>unbounded tails"]
    U["Uniform: flat probability<br/>a to b"]
    L["Lognormal: right-skewed<br/>bounded at zero"]
    end
    T -->|"more data/confidence"| B
    N -->|"truncate at zero"| L
```

### Selecting a Distribution

| Distribution | Best Used When | Data Requirement |
| --- | --- | --- |
| Triangular | Quick estimates, limited data, expert judgment | O, M, P |
| PERT/Beta | Standard risk analysis practice, smoother realism than triangular | O, M, P (+ optional $\lambda$) |
| Normal | Symmetric variability, aggregate/summary level durations | $\mu$, $\sigma$ |
| Uniform | No informative basis for preferring any value in a range | min, max |
| Lognormal | Durations with long right tail, cannot go negative | $\mu$, $\sigma$ of underlying normal |

### Application in Monte Carlo Simulation

**Key Points**

- Each activity in the network is assigned a distribution and parameters.
- Simulation software runs thousands of iterations, sampling a random duration for each activity per iteration according to its distribution.
- Each iteration performs a full CPM forward/backward pass, producing one possible project finish date.
- Aggregating all iterations yields a probability distribution (S-curve) of possible finish dates, from which percentiles (P50, P80, P90) and contingency durations are derived.

**Example**

An activity modeled with PERT($O=4, M=6, P=14$) contributes a randomly sampled value (e.g., 6.8 days in one iteration, 9.2 in another) each simulation run, rather than a fixed 6 days, allowing the simulation to capture the compounding effect of variability across the whole network — including which paths become critical under different sampled outcomes ("criticality index").

### Common Pitfalls

**Key Points**

- **Merge bias**: Paths converging at a merge point tend to push the successor's start later than the simple average would suggest, because the merge activity must wait for the *latest* of all predecessors — this effect is captured by simulation but missed by deterministic CPM.
- **Ignoring correlation**: Treating all activity durations as statistically independent understates risk when common-cause factors (weather, labor productivity, a shared supplier) affect multiple activities simultaneously.
- **Overconfidence in point estimates**: Using overly narrow $O$–$P$ ranges collapses the simulated distribution toward the deterministic CPM date, defeating the purpose of the analysis.
- **Misapplied Normal distribution**: Applying unbounded Normal distributions to short-duration activities can produce nonsensical negative-duration samples if not truncated.

[Inference] The relative accuracy of triangular vs. PERT/Beta distributions in a specific project depends on how closely the underlying uncertainty matches each distribution's shape assumptions; neither is universally superior across all activity types.

### Related Topics

- Monte Carlo simulation methodology and iteration count selection
- Three-point estimating techniques and estimator bias
- Correlation and common-cause risk modeling between activities
- Criticality Index and Schedule Sensitivity Index
- Contingency reserve derivation from simulation percentiles (P50/P80)
- Merge bias and its effect on near-critical paths
- Software tools for schedule risk analysis (Primavera Risk Analysis, @RISK, Safran Risk)