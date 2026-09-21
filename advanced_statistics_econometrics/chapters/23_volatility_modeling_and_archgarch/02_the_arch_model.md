## The ARCH Model

### Definition and Conceptual Foundation

The Autoregressive Conditional Heteroskedasticity (ARCH) model, introduced by Robert Engle (1982) in his seminal analysis of UK inflation uncertainty, was the first formal econometric model to allow the conditional variance of a time series to change over time as a function of past information, rather than assuming constant (homoskedastic) variance. Engle received the 2003 Nobel Memorial Prize in Economic Sciences in part for this contribution. ARCH directly addresses the volatility clustering stylized fact: rather than treating time-varying variance as a nuisance to be corrected via heteroskedasticity-robust standard errors, ARCH models the conditional variance itself as an object of interest with its own dynamic structure.

### Model Specification

Consider a time series $r_t$ (e.g., a return series) decomposed into a conditional mean and an innovation:

$$r_t = \mu_t + \varepsilon_t$$

where $\mu_t$ is the conditional mean (often modeled via a low-order ARMA or simply a constant), and $\varepsilon_t$ is the innovation. The ARCH(q) model specifies:

$$\varepsilon_t = \sigma_t z_t, \quad z_t \overset{\text{i.i.d.}}{\sim} (0, 1)$$



$$\sigma_t^2 = \omega + \sum_{i=1}^{q} \alpha_i \varepsilon_{t-i}^2$$

where $z_t$ is a standardized i.i.d. innovation (commonly assumed standard normal, Student's-t, or generalized error distributed), and $\sigma_t^2$ is the conditional variance, which depends on the squared values of the $q$ most recent innovations.

**Key Points**

- $\varepsilon_t$ is conditionally heteroskedastic (its variance $\sigma_t^2$ changes over time, driven by recent shock magnitudes) but is unconditionally (marginally) homoskedastic under covariance stationarity, since $E[\sigma_t^2]$ is constant across $t$ when the process is stationary.
- Large $|\varepsilon_{t-i}|$ values (large past shocks, regardless of sign) increase the current conditional variance $\sigma_t^2$, directly capturing volatility clustering: a big move today raises expected volatility tomorrow.
- The model treats *positive and negative* shocks of equal magnitude symmetrically, since only $\varepsilon_{t-i}^2$ enters the variance equation — the ARCH(q) specification does not capture the leverage effect (asymmetric volatility response) without extension.

### Parameter Restrictions

**Key Points**

- **Non-negativity constraints**: $\omega > 0$ and $\alpha_i \geq 0$ for all $i = 1, \dots, q$ are required to ensure $\sigma_t^2 > 0$ almost surely (a variance cannot be negative). These constraints must be imposed during estimation, typically via constrained maximum likelihood.
- **Stationarity (covariance/weak stationarity) condition**: $\sum_{i=1}^{q} \alpha_i < 1$ is required for the unconditional variance to exist and be finite, in which case:

$$\text{Var}(\varepsilon_t) = \frac{\omega}{1 - \sum_{i=1}^{q}\alpha_i}$$

- If $\sum \alpha_i \geq 1$, the process is not covariance stationary (the unconditional variance is infinite or undefined), though the process can still be strictly stationary under weaker conditions in some cases.

### The ARCH(1) Case

The simplest and most illustrative case is ARCH(1):

$$\sigma_t^2 = \omega + \alpha_1 \varepsilon_{t-1}^2, \quad \omega > 0, \; 0 \leq \alpha_1 < 1$$

**Key Points**

- A single lagged squared innovation drives the conditional variance; larger $\alpha_1$ implies a stronger, more immediate response of current variance to the most recent shock.
- The unconditional variance is $\text{Var}(\varepsilon_t) = \omega / (1 - \alpha_1)$.
- ARCH(1) implies the conditional variance decays back toward the unconditional variance geometrically at rate $\alpha_1$ following a shock, in the absence of further shocks — a relatively fast, single-parameter decay pattern that is often too restrictive to match the empirically observed slow decay in volatility persistence (motivating GARCH, which allows richer, more parsimonious persistence structures).

### Estimation via Maximum Likelihood

**Example**

Step 1: Specify the conditional mean equation (e.g., $r_t = \mu + \varepsilon_t$, or a low-order ARMA if serial correlation is present in the mean).

Step 2: Specify the ARCH(q) variance equation and the conditional distribution of $z_t$ (commonly Gaussian for a baseline model, given fat tails, Student's-t is often preferred in practice).

Step 3: Write the conditional log-likelihood. For Gaussian $z_t$, the log-likelihood contribution at time $t$ is:

$$\ell_t = -\frac{1}{2}\ln(2\pi) - \frac{1}{2}\ln(\sigma_t^2) - \frac{\varepsilon_t^2}{2\sigma_t^2}$$

and the full sample log-likelihood is $L = \sum_{t=q+1}^{T} \ell_t$ (or with pre-sample values initialized, e.g., at the unconditional variance).

Step 4: Maximize $L$ numerically over $(\omega, \alpha_1, \dots, \alpha_q)$ subject to the non-negativity constraints, typically via numerical optimization (e.g., BHHH, BFGS) since no closed-form solution exists.

Step 5: Check convergence, verify constraints are not binding in a way that suggests misspecification (e.g., an estimated $\alpha_i$ pinned exactly at 0 for higher-order lags may suggest a lower-order ARCH or a GARCH specification is more appropriate), and examine standardized residuals $\hat{z}_t = \hat{\varepsilon}_t / \hat{\sigma}_t$ for remaining ARCH effects.

**Output**

A typical fitted ARCH(1) model on daily equity returns might yield $\hat{\omega} = 0.000015$, $\hat{\alpha}_1 = 0.15$ (statistically significant, $p < 0.01$), implying an unconditional daily variance of $\hat{\omega}/(1-\hat{\alpha}_1) \approx 0.0000176$, corresponding to an unconditional daily volatility of roughly 1.3%. In practice, fitted $\alpha_1$ coefficients for ARCH(1) on daily financial returns are often found to be too low to fully capture persistence, and diagnostic tests frequently indicate that a higher-order ARCH(q) or, more commonly, a GARCH(1,1) specification fits better. [Inference: the specific coefficient values above are illustrative, not drawn from a specific dataset.]

### Testing for ARCH Effects

**Engle's ARCH-LM test** (Lagrange Multiplier test) is the standard pre-estimation diagnostic to determine whether ARCH modeling is warranted:

Step 1: Estimate the conditional mean model (e.g., via OLS or ARMA) and obtain residuals $\hat{\varepsilon}_t$.

Step 2: Regress $\hat{\varepsilon}_t^2$ on a constant and $q$ lags of itself: $\hat{\varepsilon}_t^2 = \gamma_0 + \gamma_1\hat{\varepsilon}_{t-1}^2 + \cdots + \gamma_q\hat{\varepsilon}_{t-q}^2 + u_t$.

Step 3: Compute the test statistic $LM = T \cdot R^2$ from this auxiliary regression, which is asymptotically $\chi^2(q)$ under the null of no ARCH effects ($H_0: \gamma_1 = \cdots = \gamma_q = 0$).

Step 4: Reject $H_0$ if $LM$ exceeds the critical value, indicating significant ARCH effects and motivating ARCH/GARCH modeling of the conditional variance.

### Limitations of the ARCH Model

**Key Points**

- **Parameter proliferation**: Capturing the slow, persistent decay in volatility observed empirically (the long-memory-like pattern in Fact 6 of the stylized facts) often requires a high ARCH order $q$, leading to many parameters to estimate and reduced parsimony/statistical efficiency.
- **No asymmetry**: As noted, ARCH(q) treats positive and negative shocks symmetrically, missing the well-documented leverage effect.
- **Estimation difficulty with many lags**: With large $q$, imposing all non-negativity constraints simultaneously during numerical optimization becomes increasingly cumbersome, and convergence can be problematic.
- These limitations directly motivated Bollerslev's (1986) generalization to GARCH, which achieves comparable or superior fit with far fewer parameters by allowing lagged conditional variance itself (not just lagged squared shocks) into the variance equation.

### ARCH Model Structure Diagram

```mermaid
flowchart TD
    subgraph arch_model_structure ARCH(q) Model Structure (svg_diagram)
    A["Return r_t = mu_t + epsilon_t"] --> B["Innovation epsilon_t = sigma_t times z_t"]
    B --> C["z_t iid, mean 0, variance 1"]
    B --> D["Conditional variance: sigma_t^2 = omega + sum alpha_i epsilon_t-i^2, i=1..q"]
    D --> E["Large past squared shock => higher current variance"]
    E --> F["Volatility clustering reproduced"]
    D --> G["Constraints: omega greater than 0, alpha_i greater or equal 0"]
    D --> H["Stationarity: sum alpha_i less than 1"]
    H --> I["Unconditional variance = omega / (1 - sum alpha_i)"]
    end
```

### Software Implementation Notes

- **R**: `fGarch::garchFit()` (can specify pure ARCH via `garch(q,0)` argument), `rugarch::ugarchspec()` with `variance.model = list(model="sGARCH", garchOrder=c(q,0))`.
- **Python**: `arch` package, `arch_model(returns, vol='ARCH', p=q)`.
- **EViews/Stata**: Both provide native ARCH/GARCH estimation commands (`arch` command in Stata; ARCH/GARCH equation specification in EViews) with straightforward order specification.

[Unverified: exact default optimizer, convergence criteria, and pre-sample variance initialization conventions vary by package and version; verify against current documentation before implementation.]

**Related Topics**

- The GARCH model and its generalization of ARCH
- Stylized facts of financial time series
- EGARCH and GJR-GARCH asymmetric extensions
- Engle's ARCH-LM test for conditional heteroskedasticity
- Maximum likelihood estimation under non-Gaussian conditional distributions
- FIGARCH and long-memory volatility models
- Value-at-Risk estimation using conditional volatility models