## Multiple testing corrections and false discovery rate

### Overview

When many hypothesis tests are conducted simultaneously, the probability of obtaining at least one false positive by chance alone grows rapidly with the number of tests, even when every null hypothesis being tested is true. Multiple testing corrections adjust significance thresholds or p-values to control an appropriately defined aggregate error rate across the full set of tests, rather than controlling the error rate of each individual test in isolation.

### The Multiple Testing Problem

If $m$ independent hypothesis tests are each conducted at significance level $\alpha$, and all $m$ null hypotheses are true, the probability of **at least one false rejection** grows with $m$:

$$P(\text{at least one false rejection}) = 1-(1-\alpha)^m$$

For $\alpha=0.05$ and $m=20$ independent tests, this probability is $1-0.95^{20} \approx 0.64$ — a roughly 64% chance of at least one spurious "significant" finding purely by chance, even though every null hypothesis is true. This escalation is the core motivation for multiple testing corrections.

### The Family-Wise Error Rate (FWER)

The **Family-Wise Error Rate** is the probability of making **at least one** Type I error (false rejection) among all $m$ tests:

$$FWER = P(\text{at least one false rejection among all } m \text{ tests})$$

Controlling FWER at level $\alpha$ means ensuring $FWER \leq \alpha$ across the entire family of tests, a considerably stricter requirement than controlling each individual test's Type I error rate at $\alpha$.

**Bonferroni Correction**: The simplest and most conservative FWER-controlling procedure — reject the $i$-th hypothesis if its p-value satisfies:

$$p_i \leq \frac{\alpha}{m}$$

By Boole's inequality (the union bound), this guarantees $FWER \leq \alpha$ regardless of the dependence structure among the tests, making it broadly applicable but often overly conservative (sacrificing substantial statistical power), especially as $m$ grows large.

**Holm–Bonferroni (step-down) procedure**: A uniformly more powerful FWER-controlling alternative. Order p-values $p_{(1)} \leq p_{(2)} \leq \dots \leq p_{(m)}$; reject $H_{(1)},\dots,H_{(k)}$ where $k$ is the largest index such that $p_{(i)} \leq \frac{\alpha}{m-i+1}$ for all $i \leq k$. Holm's procedure controls FWER under no additional assumptions (like Bonferroni) while rejecting at least as many hypotheses, dominating simple Bonferroni in power.

**Šidák correction**: $p_i \leq 1-(1-\alpha)^{1/m}$, slightly less conservative than Bonferroni, but requires an independence (or a specific positive dependence) assumption among the tests to guarantee exact FWER control.

### The False Discovery Rate (FDR)

Benjamini and Hochberg (1995) introduced a fundamentally different, less conservative error criterion better suited to settings with a very large number of tests (common in genomics and, increasingly, in economics with large administrative datasets): the **False Discovery Rate**, defined as the *expected proportion* of false positives **among all rejected (declared significant) hypotheses**:

$$FDR = E\left[\frac{V}{\max(R,1)}\right]$$

where $V$ is the number of false rejections (true nulls incorrectly rejected) and $R$ is the total number of rejections. Unlike FWER (which bounds the probability of *any* false positive at all), FDR bounds the *expected fraction* of false positives among the discoveries, a substantially weaker (and hence more powerful, less conservative) requirement.

### The Benjamini–Hochberg (BH) Procedure

To control $FDR \leq q$ (the desired FDR level):

1. Order the $m$ p-values: $p_{(1)} \leq p_{(2)} \leq \dots \leq p_{(m)}$
2. Find the largest $k$ such that $p_{(k)} \leq \dfrac{k}{m}q$
3. Reject all hypotheses $H_{(1)},\dots,H_{(k)}$ corresponding to the $k$ smallest p-values

**Validity**: The BH procedure controls $FDR \leq q$ exactly under independence of the test statistics, and (with a modified threshold, the Benjamini–Yekutieli correction) under arbitrary dependence structures as well.

**BH vs. Bonferroni comparison**: Because FDR control is a weaker requirement than FWER control, the BH procedure is uniformly less conservative — it rejects at least as many (typically strictly more) hypotheses than Bonferroni at comparable nominal levels, translating directly into higher statistical power to detect true effects, at the cost of tolerating a controlled (rather than near-zero) proportion of false discoveries among the rejected hypotheses.

### q-values

Analogous to how a p-value is the smallest $\alpha$ at which a single test would be rejected, the **q-value** of a given hypothesis is the smallest FDR threshold $q$ at which that hypothesis would be included among the BH-procedure rejections — providing a per-hypothesis summary statistic for multiple-testing-adjusted significance, directly comparable across hypotheses in the same way p-values are compared within a single test.

### Choosing Between FWER and FDR Control

| Criterion | Definition | Typical use case |
| --- | --- | --- |
| FWER | $P(\text{at least one false rejection})$ | Small number of tests; each false positive is individually costly (e.g., confirmatory clinical trials, small number of pre-specified confirmatory hypotheses) |
| FDR | $E[\text{proportion of false rejections among all rejections}]$ | Large number of exploratory tests; some false positives are tolerable if the overall discovery rate is controlled (e.g., genomics, large-scale exploratory data mining) |

### Diagram: Multiple Testing Correction Framework

```mermaid
flowchart TD
    A["Conduct m hypothesis tests, obtain p1,...,pm"] --> B{Which error rate to control?}
    B -->|FWER: P(any false rejection)| C[Bonferroni: reject if p_i <= alpha/m]
    B -->|FWER, more powerful| D["Holm step-down procedure"]
    B -->|FDR: expected proportion of false rejections| E["Benjamini-Hochberg procedure"]
    C --> F[Very conservative, low power at large m]
    D --> G[Dominates Bonferroni, still controls FWER exactly]
    E --> H["Order p-values, find largest k where p_(k) <= (k/m)*q"]
    H --> I[Reject k smallest p-values]
    I --> J[Higher power than FWER methods, tolerates some false discoveries]
```

### Relevance to Econometrics

Multiple testing corrections have become increasingly important in applied economics as datasets and the number of candidate outcomes, subgroups, or specifications examined in a single study have grown (e.g., program evaluation studies testing treatment effects across many outcome variables or many pre-specified subgroups, or "multiple hypothesis testing" in event studies examining many event windows). List (2019) and related work in applied microeconometrics have specifically advocated FDR-based or family-wise-error-controlled corrections (e.g., Romano–Wolf stepdown procedures, which additionally account for the dependence structure across correlated outcome variables) as standard practice when a study reports treatment effects across multiple outcomes. [Inference] The choice between FWER and FDR control in applied economic research often reflects the study's framing — confirmatory pre-registered analyses with a small number of primary outcomes tend toward FWER control, while broader exploratory analyses across many secondary outcomes more often use FDR-based approaches — though the specific convention adopted varies by subfield, journal, and study design.

**Related Topics**

- p-values and statistical significance
- The Neyman-Pearson framework and Type I/Type II errors
- Pre-registration and pre-analysis plans in applied economics
- Romano–Wolf and Westfall–Young stepdown resampling procedures
- Publication bias and the replication crisis
- Data mining and specification search ("p-hacking")