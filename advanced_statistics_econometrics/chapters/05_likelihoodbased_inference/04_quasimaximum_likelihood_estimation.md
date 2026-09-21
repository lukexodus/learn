## Quasi-maximum likelihood estimation

### Overview

Quasi-Maximum Likelihood Estimation (QMLE) applies the maximum likelihood machinery — maximizing a log-likelihood-shaped objective function — while explicitly acknowledging that the assumed distributional family may be misspecified. Rather than requiring the postulated density to be correct, QMLE relies on weaker conditions (typically correct specification of the conditional mean, or another low-order moment) to retain consistency, at the cost of requiring robust ("sandwich") standard errors rather than the standard information-matrix-based ones. This makes QMLE one of the most widely applied estimation frameworks in modern econometrics.

### Motivation

Classical MLE theory (consistency, asymptotic normality, efficiency) is derived under the assumption that the assumed parametric family $f(y;\theta)$ is the **true** data-generating density. In practice, researchers often specify a convenient distribution (Normal, Poisson) primarily to define an estimating objective, without believing the distributional assumption holds exactly. QMLE formalizes when this practice remains statistically valid.

### Formal Setup

Let the **quasi-likelihood** be built from an assumed (possibly incorrect) density $g(y;\theta)$, referred to as the "working" density, distinguishing it from the unknown true density $f_0(y)$ generating the data. The QML estimator is:

$$\hat\theta_{QMLE} = \arg\max_\theta \; \frac{1}{n}\sum_{i=1}^n \log g(y_i;\theta)$$

This is structurally identical to standard MLE — it is an M-estimator with $m(y_i;\theta) = \log g(y_i;\theta)$ — but the interpretation and asymptotic justification differ because $g$ need not equal $f_0$.

### Key Consistency Condition

QMLE remains **consistent** for the parameters governing the correctly specified part of the model (typically the conditional mean function) provided the assumed density belongs to the **linear exponential family** (LEF) and the conditional mean is correctly specified, even if higher moments (variance, skewness) are misspecified. This result, formalized by Gourieroux, Monfort, and Trognon (1984), is the theoretical foundation of QMLE's widespread use.

**Intuition**: For linear exponential family densities, the score equation's zero-mean property at the true parameter depends only on the conditional mean being correctly specified — the score function's expectation involves only first-moment terms, so misspecifying the variance/higher moments does not bias the mean-parameter estimating equation, though it does affect its variance.

### Canonical Example: Poisson QMLE for Count Data

The Poisson distribution assumes **equidispersion**: $\text{Var}(Y\mid X) = E(Y\mid X) = \exp(X\beta)$. Real count data (e.g., number of patents filed by a firm, number of insurance claims) very often exhibit **overdispersion** ($\text{Var}(Y\mid X) > E(Y\mid X)$), violating this Poisson variance assumption.

**QMLE result**: Provided the conditional mean is correctly specified as $E(Y\mid X) = \exp(X\beta)$, maximizing the Poisson log-likelihood

$$\ell(\beta) = \sum_{i=1}^n \left[y_i x_i^\top\beta - \exp(x_i^\top\beta) - \log(y_i!)\right]$$

yields a **consistent** estimator $\hat\beta_{QMLE}$ even when the true data-generating process is overdispersed (e.g., Negative Binomial) — because the Poisson density is a linear exponential family member and only the mean specification matters for consistency. However, the naive Poisson-based standard errors (derived from the Poisson information matrix, which assumes equidispersion) are **incorrect** — generally too small — under overdispersion, and must be replaced with robust standard errors.

### Asymptotic Theory: The QMLE Sandwich Formula

Because QMLE is a special case of M-estimation, its asymptotic variance follows the general sandwich formula (see M-estimation and Z-estimation):

$$\sqrt{n}(\hat\theta_{QMLE} - \theta_0) \xrightarrow{d} N\left(0,\; A(\theta_0)^{-1}B(\theta_0)A(\theta_0)^{-1}\right)$$

where:

- $A(\theta_0) = E\left[-\frac{\partial^2 \log g(Y;\theta_0)}{\partial\theta\partial\theta^\top}\right]$ — the expected Hessian under the assumed (working) model
- $B(\theta_0) = E\left[\frac{\partial \log g(Y;\theta_0)}{\partial\theta}\frac{\partial \log g(Y;\theta_0)}{\partial\theta^\top}\right]$ — the true variance of the score, computed under the true (possibly different) data-generating process

Under correct specification, the **information matrix equality** $A(\theta_0)=B(\theta_0)$ holds and the sandwich collapses to the standard MLE variance $A(\theta_0)^{-1}$; under misspecification, $A \neq B$ in general, and only the full sandwich formula gives valid standard errors.

**QMLE standard errors in practice**: Estimated using sample analogues, $\widehat{\text{Var}}(\hat\theta) = \frac{1}{n}\hat A^{-1}\hat B\hat A^{-1}$ — these are precisely what econometric software reports as "robust" or "QML" standard errors after Poisson, Negative Binomial (in its QMLE form), or other exponential-family-based regressions.

### QMLE in Financial Econometrics: GARCH Models

QMLE is the dominant estimation method for **GARCH** (Generalized Autoregressive Conditional Heteroskedasticity) models, since financial return data typically exhibit heavier tails than the Normal distribution assumed for computational convenience in the (Quasi-)likelihood. Gaussian QMLE for GARCH models remains consistent for the conditional variance parameters under fairly general conditions on the true error distribution (finite fourth moments are typically required for the standard asymptotic normality result to hold), even though the true innovation distribution is not Normal — a result central to the practical applicability of GARCH modeling in risk management and volatility forecasting.

### Distinguishing QMLE from Related Concepts

| Concept | Distributional assumption | Consistency requirement |
| --- | --- | --- |
| MLE | Fully correct | Correct full distribution |
| QMLE | Working density (possibly wrong) | Correct conditional mean (LEF case) |
| GMM | None (moment conditions only) | Correct moment conditions |
| M-estimation | General objective function | Correct identification condition on population objective |

QMLE sits conceptually between full MLE (strongest assumptions, most efficient if correct) and GMM (weakest assumptions, most general), often described as exploiting "as much of the likelihood structure as is safely usable" given the researcher's actual confidence in the assumed distribution.

### Diagram: QMLE Consistency and Inference Logic

```mermaid
flowchart TD
    A[True data-generating process f0 - possibly unknown] --> B[Assume working density g of y given theta]
    B --> C["Maximize: average of log g(yi, theta)"]
    C --> D{Is g in Linear Exponential Family AND conditional mean correct?}
    D -->|Yes| E[theta_hat_QMLE is consistent for mean parameters]
    D -->|No| F[Consistency not guaranteed]
    E --> G{Higher moments (e.g. variance) also correctly specified?}
    G -->|Yes| H[Standard MLE information-based SEs valid]
    G -->|No, e.g. overdispersion| I[Must use Sandwich / Robust Standard Errors]
    I --> J["Var = A^-1 * B * A^-1 (A from working model Hessian, B from true score variance)"]
```

### Relevance to Econometrics

QMLE is the standard justification for using Poisson regression on overdispersed count data (patent counts, trip counts, insurance claims) with robust standard errors rather than switching to a more complex Negative Binomial specification, and is the standard estimation method for GARCH and other conditional volatility models in financial econometrics, where Gaussian QMLE is used routinely despite well-documented fat tails in financial return data. [Inference] The choice between reporting QMLE-robust standard errors versus fully respecifying the likelihood (e.g., moving from Poisson to Negative Binomial, or from Gaussian to Student-t GARCH innovations) often depends on whether the researcher's primary interest is in consistent point estimates of mean/conditional-mean parameters (where QMLE suffices) or in fully characterizing the conditional distribution (where correct likelihood specification matters more), and practice varies across subfields.

**Related Topics**

- M-estimation, Z-estimation, and the sandwich variance formula
- Maximum likelihood estimation and the score equation
- Generalized Method of Moments (GMM)
- Poisson and Negative Binomial regression for count data
- GARCH models and volatility estimation
- Robust (heteroskedasticity-consistent) standard errors