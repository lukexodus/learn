## Partially Linear Models

### Overview

Partially linear models (PLM) specify a regression function that is linear in some covariates but leaves the functional form for others fully unrestricted:

$$Y=X'\beta+g(Z)+\varepsilon$$

where $X$ enters parametrically (with coefficient vector $\beta$, the primary object of interest) and $Z$ enters through an unknown, nonparametrically estimated function $g(\cdot)$. This structure, introduced by Robinson (1988), balances interpretability and inferential tractability for the parameters of central interest ($\beta$) against flexibility for controlling nuisance covariates ($Z$) whose functional relationship with $Y$ is not of direct interest.

### Identification and Motivation

**Key Points**

- The model is most useful when a researcher has a **specific causal or structural parameter of interest** ($\beta$, e.g., a treatment effect or price elasticity) but wants to **flexibly control for confounders** ($Z$) without committing to a parametric functional form that could be misspecified and bias $\hat\beta$.
- This directly parallels the motivation for the **partially linear model (PLR)** in the DML framework — indeed, Chernozhukov et al.'s (2018) partially linear regression specification is precisely Robinson's classical PLM, updated with modern ML-based estimation of $g(Z)$ and orthogonalized/cross-fitted inference.
- Identification of $\beta$ requires that $X$ and $Z$ are **not perfectly collinear** even after accounting for $g(Z)$'s flexibility — intuitively, there must be variation in $X$ that is not fully explained by $Z$, since otherwise $\beta$ cannot be separated from the nonparametric component.

### Robinson's Partialling-Out Estimator

The classical estimation strategy avoids having to explicitly estimate the potentially high-dimensional or nonlinear $g(Z)$ jointly with $\beta$. Instead:

1. Regress $Y$ nonparametrically on $Z$ alone: obtain $\hat{E}[Y\mid Z]$.
2. Regress $X$ nonparametrically on $Z$ alone: obtain $\hat{E}[X\mid Z]$.
3. Compute residuals: $\tilde{Y}=Y-\hat{E}[Y\mid Z]$, $\tilde{X}=X-\hat{E}[X\mid Z]$.
4. Estimate $\beta$ via OLS of $\tilde{Y}$ on $\tilde{X}$ (no intercept, or a Frisch-Waugh-Lovell-style partialling-out regression).

$$\hat\beta=(\tilde{X}'\tilde{X})^{-1}\tilde{X}'\tilde{Y}$$

```mermaid
flowchart TD
    A[Data: Y, X of interest, Z nuisance covariates] --> B[Nonparametrically regress Y on Z: get E-hat(Y|Z)]
    A --> C[Nonparametrically regress X on Z: get E-hat(X|Z)]
    B --> D[Residualize: Y_tilde = Y - E-hat(Y|Z)]
    C --> E[Residualize: X_tilde = X - E-hat(X|Z)]
    D --> F[OLS of Y_tilde on X_tilde]
    E --> F
    F --> G[beta_hat: estimate of parametric effect of X on Y]
    G --> H[Standard errors: robust/sandwich, accounting for first-stage estimation]
```

**Key Points**

- This is exactly the **Frisch-Waugh-Lovell (FWL) theorem**, generalized: in standard linear OLS, FWL shows that a coefficient can be obtained by first partialling out other regressors via *linear* regression; Robinson's estimator generalizes this by partialling out $Z$ via **nonparametric** regression instead.
- The nonparametric first-stage regressions (Steps 1–2) can use **any consistent nonparametric estimator**: kernel regression, series/sieve estimation, or modern machine learning methods — this flexibility is precisely what makes the PLM framework a natural bridge to DML's partially linear regression (PLR) model.
- Under regularity conditions (including sufficiently fast convergence of the nonparametric first-stage estimates), $\hat\beta$ is $\sqrt{N}$-consistent and asymptotically normal — a **parametric rate of convergence for $\beta$ despite the presence of a fully nonparametric nuisance component** $g(Z)$, which is the central appeal of the partially linear structure.

### Why Partialling-Out Achieves Orthogonality

**Key Points**

- Robinson's residual-on-residual construction is a **Neyman-orthogonal moment condition** by construction: small errors in estimating $E[Y\mid Z]$ or $E[X\mid Z]$ have only second-order effects on $\hat\beta$, precisely the property exploited in the DML/orthogonality framework more broadly.
- This is the direct historical antecedent of the **R-learner** approach used in heterogeneous treatment effect estimation (Nie and Wager 2021) — the R-learner's "residualize $Y$ against $X$-covariates, residualize $D$ against $X$-covariates, then regress residual-on-residual" procedure for estimating a *heterogeneous* $\tau(x)$ is a direct generalization of Robinson's *constant* $\beta$ partialling-out estimator.

### Relationship to Double/Debiased Machine Learning

| Aspect | Classical Robinson PLM | DML Partially Linear Regression (PLR) |
| --- | --- | --- |
| Nonparametric first stage | Kernel or series regression | Any ML method (lasso, forest, boosting) |
| Cross-fitting | Not originally emphasized | Standard/required |
| Rate requirements | Specific to kernel/series convergence theory | General product-rate condition, ML-compatible |
| Target parameter | Constant linear effect $\beta$ | Same: constant linear effect $\theta$ |

**Key Points**

- DML's PLR model is, in essence, **Robinson's classical partially linear model updated for the machine learning era**: replacing kernel/series nonparametric regression with modern ML methods for the first-stage nuisance functions, and adding formal cross-fitting to control the additional overfitting bias that flexible ML introduces beyond what classical nonparametric smoothers exhibited.
- This connection illustrates that DML is not an entirely novel statistical idea but rather a **rigorous extension of a well-established semiparametric estimation principle** (partialling-out/orthogonalization) to accommodate modern high-dimensional ML nuisance estimation.

### Extensions

**Key Points**

- **Partially linear models with endogenous $X$**: when $X$ is endogenous (correlated with $\varepsilon$), the partialling-out framework extends to incorporate instruments, yielding **partially linear instrumental variables (PLIV)** models — another standard DML model class, paralleling the PLR-to-PLIV extension for the fully parametric IV case.
- **Partially linear models with heterogeneous $\beta(Z)$**: relaxing the constant-coefficient assumption to allow $\beta$ to vary with $Z$ moves the model toward a **varying-coefficient model**, a distinct but related semiparametric specification.
- **Panel/longitudinal partially linear models**: incorporating fixed effects or dynamic structure into the partially linear framework, relevant for panel-data applications where $g(Z)$ might flexibly capture time-varying or unit-specific nonlinear confounding.

### Practical Example (R, `np` / `DoubleML`)

```r
# Classical kernel-based Robinson estimator via np package
library(np)

# First stage: nonparametric regressions on Z
bw_y <- npregbw(Y ~ Z, regtype = "ll")
Ey_given_z <- fitted(npreg(bws = bw_y))

bw_x <- npregbw(X ~ Z, regtype = "ll")
Ex_given_z <- fitted(npreg(bws = bw_x))

# Partialling-out / residual regression
Y_tilde <- Y - Ey_given_z
X_tilde <- X - Ex_given_z
beta_hat <- lm(Y_tilde ~ X_tilde - 1)
summary(beta_hat)

# Modern ML-based version via DoubleML (PLR model)
library(DoubleML)
library(mlr3learners)

dml_data <- DoubleMLData$new(df, y_col = "Y", d_cols = "X", x_cols = "Z")
dml_plr <- DoubleMLPLR$new(
  dml_data,
  ml_l = lrn("regr.ranger"),  # E[Y|Z]
  ml_m = lrn("regr.ranger"),  # E[X|Z]
  n_folds = 5
)
dml_plr$fit()
dml_plr$summary()
```

### Practical Example (Python, `doubleml`)

```python
import doubleml as dml
from doubleml import DoubleMLData
from sklearn.ensemble import RandomForestRegressor

dml_data = DoubleMLData(df, y_col="Y", d_cols="X", x_cols=["Z"])

dml_plr = dml.DoubleMLPLR(
    dml_data,
    ml_l=RandomForestRegressor(n_estimators=300),  # E[Y|Z]
    ml_m=RandomForestRegressor(n_estimators=300),  # E[X|Z]
    n_folds=5
)

dml_plr.fit()
print(dml_plr.summary)
```

### Visualizing the Partialling-Out Logic (SVG)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 300">
<text x="320" y="20" font-size="14" text-anchor="middle" font-family="sans-serif" font-weight="bold">Robinson Partialling-Out Estimator (svg_diagram)</text>
<rect x="60" y="50" width="200" height="50" fill="#fef08a" stroke="#333" />
<text x="160" y="80" font-size="11" text-anchor="middle" font-family="sans-serif">E[Y|Z]: nonparametric</text>
<rect x="380" y="50" width="200" height="50" fill="#bfdbfe" stroke="#333" />
<text x="480" y="80" font-size="11" text-anchor="middle" font-family="sans-serif">E[X|Z]: nonparametric</text>
<line x1="160" y1="100" x2="160" y2="150" stroke="#333" />
<line x1="480" y1="100" x2="480" y2="150" stroke="#333" />
<rect x="60" y="150" width="200" height="50" fill="#fde68a" stroke="#333" />
<text x="160" y="180" font-size="11" text-anchor="middle" font-family="sans-serif">Y_tilde = Y - E-hat[Y|Z]</text>
<rect x="380" y="150" width="200" height="50" fill="#93c5fd" stroke="#333" />
<text x="480" y="180" font-size="11" text-anchor="middle" font-family="sans-serif">X_tilde = X - E-hat[X|Z]</text>
<line x1="260" y1="175" x2="380" y2="175" stroke="#333" stroke-width="1" />
<rect x="220" y="230" width="200" height="45" fill="#bbf7d0" stroke="#333" />
<text x="320" y="257" font-size="11" text-anchor="middle" font-family="sans-serif">OLS: Y_tilde ~ X_tilde -&gt; beta_hat</text>
<line x1="160" y1="200" x2="280" y2="230" stroke="#333" />
<line x1="480" y1="200" x2="360" y2="230" stroke="#333" />
</svg>

### Common Pitfalls

- **Using linear first-stage regressions of $Y$ and $X$ on $Z$** (rather than genuinely nonparametric/flexible ones), which defeats the purpose of the partially linear structure and simply reduces to a standard fully linear model, reintroducing the functional-form misspecification risk the PLM was meant to avoid.
- **Omitting cross-fitting when the first-stage nonparametric regressions use flexible ML methods** — the same overfitting-bias concern from DML applies directly here, since Robinson's classical asymptotic theory did not originally account for this (it assumed classical nonparametric smoothers under specific rate conditions, which differ from generic ML convergence behavior).
- **Assuming $\beta$ is constant across $Z$ when true heterogeneity exists**: if the actual relationship between $X$ and $Y$ varies with $Z$ (rather than $Z$ only affecting $Y$ additively), the partially linear model is misspecified — a varying-coefficient or fully interactive model (e.g., R-learner/causal forest) may be more appropriate.
- **Ignoring endogeneity of $X$**: if $X$ is correlated with $\varepsilon$ (unobserved confounding not captured by $Z$), Robinson's estimator remains biased for the causal effect of $X$ — the partially linear IV (PLIV) extension, incorporating a valid instrument, is required in that setting.
- **Treating $g(Z)$'s estimation quality as unimportant** because it is a "nuisance" component — poor nonparametric fit for $E[Y\mid Z]$ or $E[X\mid Z]$ still degrades the precision (and, absent orthogonality/cross-fitting safeguards, the validity) of $\hat\beta$, even though $g(Z)$ itself is not the parameter of interest.

**Next Steps**

- Double/Debiased Machine Learning
- Neyman Orthogonality and Cross-Fitting
- Heterogeneous Treatment Effect Estimation (R-Learner)
- Nonparametric Regression
- Instrumental Variables Estimation
- Semiparametric Single-Index Models
- Varying-Coefficient Models