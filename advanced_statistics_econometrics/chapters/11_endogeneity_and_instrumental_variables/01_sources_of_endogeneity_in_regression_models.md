## Sources of Endogeneity in Regression Models

### Definition

Endogeneity occurs when an explanatory variable $X$ in a regression model is correlated with the error term $\varepsilon$, formally:

$$\text{Cov}(X, \varepsilon) \neq 0$$

This violates the exogeneity assumption required by the classical linear regression model (CLRM), specifically $E[\varepsilon \mid X] = 0$. When endogeneity is present, Ordinary Least Squares (OLS) estimators become **biased and inconsistent**, meaning the bias does not vanish even as sample size $n \to \infty$.

### Consequences of Endogeneity

- **Bias**: $E[\hat{\beta}] \neq \beta$ in finite samples
- **Inconsistency**: $\text{plim}(\hat{\beta}) \neq \beta$ as $n \to \infty$
- **Invalid inference**: Standard errors, t-statistics, and confidence intervals are unreliable, even asymptotically
- **Misleading causal interpretation**: Coefficients can no longer be interpreted as causal effects, only as correlational associations at best

### The Four Primary Sources of Endogeneity

#### 1. Omitted Variable Bias (OVB)

Occurs when a variable $Z$ that affects the dependent variable $Y$ is excluded from the model, and $Z$ is correlated with an included regressor $X$.

**Illustration:**

Suppose the true model is:

$$Y = \beta_0 + \beta_1 X + \beta_2 Z + u$$

But the estimated model omits $Z$:

$$Y = \beta_0 + \beta_1 X + \varepsilon, \quad \text{where } \varepsilon = \beta_2 Z + u$$

If $\text{Cov}(X, Z) \neq 0$, then $\text{Cov}(X, \varepsilon) \neq 0$, and $\hat{\beta}_1$ picks up part of $Z$'s effect.

**Direction and magnitude of bias:**

$$\text{plim}(\hat{\beta}_1) = \beta_1 + \beta_2 \cdot \frac{\text{Cov}(X, Z)}{\text{Var}(X)}$$

**Example**: Estimating the return to education on wages while omitting "ability." Ability affects both wages (directly) and education (more able individuals pursue more schooling), so the education coefficient is biased upward — it partially captures the ability effect.

#### 2. Simultaneity (Reverse Causality)

Arises when $Y$ and $X$ are jointly determined — $X$ causes $Y$, but $Y$ also causes $X$, creating a feedback loop.

**Illustration (classic supply-demand example):**

$$Q_d = \alpha_0 + \alpha_1 P + \varepsilon_d \quad \text{(demand)}$$



$$Q_s = \beta_0 + \beta_1 P + \varepsilon_s \quad \text{(supply)}$$

Price $P$ and quantity $Q$ are determined simultaneously in market equilibrium, so $P$ is correlated with both error terms — neither equation can be estimated consistently by OLS in isolation.

**Example**: Regressing crime rate on police staffing. More police may reduce crime, but higher crime also causes cities to hire more police — the coefficient conflates both causal directions.

#### 3. Measurement Error (Errors-in-Variables)

Occurs when the regressor $X$ is measured with error, so the observed variable $X^*$ differs from the true value $X$:

$$X^* = X + v$$

Substituting into the true model $Y = \beta_0 + \beta_1 X + u$ gives:

$$Y = \beta_0 + \beta_1 X^* + (u - \beta_1 v)$$

Since $X^* = X + v$, and $v$ is now part of the composite error, $\text{Cov}(X^*, \varepsilon) \neq 0$.

**Key result — attenuation bias**: When only the regressor is measured with **classical** (mean-zero, independent) error, the bias is *always* toward zero:

$$\text{plim}(\hat{\beta}_1) = \beta_1 \cdot \frac{\sigma_X^2}{\sigma_X^2 + \sigma_v^2}$$

This ratio is strictly less than 1, so $\hat{\beta}_1$ is attenuated (biased toward zero). [Inference: if the dependent variable $Y$ is measured with error instead — and that error is classical and uncorrelated with $X$ — it inflates the error variance but does not bias $\hat{\beta}_1$; it only reduces efficiency and $R^2$.]

**Example**: Using self-reported income as a proxy for true income in a consumption regression — reporting error attenuates the estimated marginal propensity to consume.

#### 4. Sample Selection Bias

Arises when the sample is not randomly drawn from the population of interest, and the selection mechanism is correlated with the error term.

**Illustration (Heckman-type selection):**

$$Y_i = X_i\beta + u_i \quad \text{(outcome equation, observed only if } S_i = 1\text{)}$$



$$S_i^* = Z_i\gamma + v_i, \quad S_i = \mathbb{1}(S_i^* > 0) \quad \text{(selection equation)}$$

If $\text{Corr}(u_i, v_i) \neq 0$, estimating the outcome equation only on the selected subsample ($S_i = 1$) yields:

$$E[u_i \mid X_i, S_i = 1] \neq 0$$

**Example**: Estimating wage equations using only employed individuals. If unobserved factors that raise wages also raise the probability of employment, the OLS wage regression on the employed subsample is biased — this is the standard motivation for the Heckman two-step correction.

### Related but Distinct Source: Model Misspecification

Incorrect functional form (e.g., omitting a quadratic term when the true relationship is nonlinear, or misspecifying the link function) can also induce correlation between regressors and the error term. This is sometimes treated as a special case of omitted variable bias (an omitted nonlinear transformation of an included variable).

### Diagnostic Overview

| Source | Root Cause | Bias Direction | Common Detection |
| --- | --- | --- | --- |
| Omitted variable | Missing correlated regressor | Sign of $\beta_2 \cdot \text{Cov}(X,Z)$ | Theory, RESET test, sensitivity analysis (Oster's $\delta$) |
| Simultaneity | Joint determination of $X$ and $Y$ | Ambiguous, depends on structure | Hausman test, economic theory on system structure |
| Measurement error (in $X$) | Noisy regressor | Toward zero (attenuation) | Compare with validation/instrument data |
| Sample selection | Non-random sample inclusion | Depends on $\text{Corr}(u,v)$ | Heckman's $\lambda$ significance test |

### Formal Diagnostic Test: Durbin-Wu-Hausman Test

Used to test $H_0: \text{Cov}(X, \varepsilon) = 0$ (exogeneity) against $H_1: \text{Cov}(X, \varepsilon) \neq 0$ (endogeneity), given a valid set of instruments $Z$.

**Procedure:**

1. Regress the suspected endogenous variable $X$ on all instruments and exogenous regressors; obtain residuals $\hat{v}$
2. Include $\hat{v}$ as an additional regressor in the original structural equation
3. Test the significance of $\hat{v}$'s coefficient via a standard t-test (or F-test for multiple suspected endogenous variables)

$$Y = \beta_0 + \beta_1 X + \beta_2 \hat{v} + u$$

If $\hat{\beta}_2$ is statistically significant, the null of exogeneity is rejected — $X$ is endogenous, and IV/2SLS estimation is warranted over OLS.

### Diagrammatic Summary

```mermaid
flowchart TD
    A[Endogeneity: Cov(X, epsilon) != 0] --> B[Omitted Variable Bias]
    A --> C[Simultaneity / Reverse Causality]
    A --> D[Measurement Error in X]
    A --> E[Sample Selection Bias]
    B --> B1[Missing confounder Z correlated with X and Y]
    C --> C1[X and Y jointly determined by a system]
    D --> D1[Observed X* = true X + noise v]
    E --> E1[Non-random inclusion correlated with error]
    B1 --> F[OLS biased and inconsistent]
    C1 --> F
    D1 --> F
    E1 --> F
    F --> G[Remedy: Instrumental Variables / 2SLS / Heckman correction]
```

### Illustrative Diagram — Omitted Variable Bias Path (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 260">
<text x="320" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Omitted Variable Bias Path (svg_diagram)</text>
<circle cx="120" cy="150" r="45" fill="#e8f0fe" stroke="#3355aa" stroke-width="2" />
<text x="120" y="155" text-anchor="middle" font-size="16" fill="#1a1a1a">X</text>
<circle cx="520" cy="150" r="45" fill="#e8f0fe" stroke="#3355aa" stroke-width="2" />
<text x="520" y="155" text-anchor="middle" font-size="16" fill="#1a1a1a">Y</text>
<circle cx="320" cy="60" r="45" fill="#fde8e8" stroke="#aa3333" stroke-width="2" />
<text x="320" y="65" text-anchor="middle" font-size="16" fill="#1a1a1a">Z</text>
<text x="320" y="20" text-anchor="middle" font-size="12" fill="#aa3333" font-style="italic">(omitted, in error term)</text>
<line x1="165" y1="150" x2="475" y2="150" stroke="#333" stroke-width="2" marker-end="url(#arrow)" />
<text x="320" y="140" text-anchor="middle" font-size="13" fill="#333">$\beta_1$ (estimated, biased)</text>
<line x1="290" y1="95" x2="150" y2="120" stroke="#aa3333" stroke-width="2" marker-end="url(#arrow)" />
<line x1="350" y1="95" x2="490" y2="120" stroke="#aa3333" stroke-width="2" marker-end="url(#arrow)" />
<text x="200" y="100" text-anchor="middle" font-size="12" fill="#aa3333">Cov(X,Z)≠0</text>
<text x="440" y="100" text-anchor="middle" font-size="12" fill="#aa3333">$\beta_2$</text>
</svg>

### Remedies

- **Instrumental Variables (IV) / Two-Stage Least Squares (2SLS)**: requires an instrument $Z$ satisfying relevance ($\text{Cov}(Z,X) \neq 0$) and exclusion ($\text{Cov}(Z,\varepsilon) = 0$)
- **Panel data methods**: fixed effects to difference out time-invariant omitted variables
- **Heckman two-step correction**: for sample selection bias specifically
- **Proxy variables**: partial mitigation of omitted variable bias when a good proxy for the unobserved factor exists
- **Natural experiments / quasi-experimental designs**: difference-in-differences, regression discontinuity, when valid instruments are unavailable

**Related Topics**

- Instrumental variables: relevance and exclusion restrictions
- Two-Stage Least Squares (2SLS) estimation mechanics
- Weak instruments and the weak instrument problem
- Durbin-Wu-Hausman test in detail
- Heckman selection model (two-step and MLE variants)
- Panel data fixed effects vs. random effects as endogeneity remedies
- Difference-in-differences and regression discontinuity as quasi-experimental identification strategies
- Control function approach to endogeneity correction