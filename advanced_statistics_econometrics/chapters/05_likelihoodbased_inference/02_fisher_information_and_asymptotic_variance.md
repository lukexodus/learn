## Fisher information and asymptotic variance

### Overview

Fisher information quantifies the amount of information a random sample carries about an unknown parameter, defined formally through the variability of the score function. It is the single quantity that governs the precision limits of estimation (via the Cramér–Rao bound), the asymptotic variance of the maximum likelihood estimator, and the sampling distributions used for likelihood-based hypothesis tests. This item consolidates the definitional and computational aspects of Fisher information and formalizes its role in asymptotic inference.

### Definition: Fisher Information (Single Observation)

For a single observation $X$ with density $f(x;\theta)$, the Fisher information is defined as the variance of the score contribution:

$$I(\theta) = \text{Var}_\theta\left[s(X;\theta)\right] = E_\theta\left[\left(\frac{\partial \log f(X;\theta)}{\partial \theta}\right)^2\right]$$

(the variance equals the second moment here because $E_\theta[s(X;\theta)] = 0$, the score's zero-mean identity).

**Second-derivative (Bartlett) identity**: Under regularity conditions permitting two differentiations under the integral sign,

$$I(\theta) = -E_\theta\left[\frac{\partial^2 \log f(X;\theta)}{\partial \theta^2}\right]$$

This equivalent form is often more convenient computationally, since it avoids squaring the score and instead uses the expected curvature (concavity) of the log-likelihood directly.

### Multiparameter Fisher Information Matrix

For $\theta = (\theta_1,\dots,\theta_k)^\top$, the Fisher information generalizes to a $k \times k$ matrix:

$$I(\theta)_{jl} = E_\theta\left[\frac{\partial \log f(X;\theta)}{\partial \theta_j}\cdot\frac{\partial \log f(X;\theta)}{\partial \theta_l}\right] = -E_\theta\left[\frac{\partial^2 \log f(X;\theta)}{\partial\theta_j\,\partial\theta_l}\right]$$

This matrix is symmetric and positive semi-definite. Its diagonal entries relate to the precision of each individual parameter; its off-diagonal entries capture how estimation precision for one parameter is affected by uncertainty about another (parameter correlation in estimation).

### Additivity Over Independent Observations

For $n$ iid observations, the total Fisher information in the sample is $n$ times the information in a single observation:

$$I_n(\theta) = n \cdot I_1(\theta)$$

This follows directly from the additivity of variances of independent, identically distributed score contributions ($\text{Var}(\sum_i s(X_i;\theta)) = \sum_i \text{Var}(s(X_i;\theta)) = n\cdot I_1(\theta)$ under independence). This additivity is the formal reason estimator precision typically improves proportionally to $n$, and standard errors shrink at rate $1/\sqrt{n}$.

**For independent but non-identically distributed observations** (e.g., regression with heterogeneous regressors $x_i$), information still adds: $I_n(\theta) = \sum_{i=1}^n I_i(\theta)$, but the individual contributions differ, which is the mathematical origin of the design-dependence of precision in regression models (e.g., why more spread-out regressor values increase precision of a slope estimate).

### Worked Examples of Fisher Information

**Bernoulli($p$)**: $\log f(x;p) = x\log p + (1-x)\log(1-p)$

$$\frac{\partial^2 \log f}{\partial p^2} = -\frac{x}{p^2} - \frac{1-x}{(1-p)^2} \quad\Rightarrow\quad I_1(p) = \frac{p}{p^2}+\frac{1-p}{(1-p)^2} = \frac{1}{p(1-p)}$$

**Poisson($\lambda$)**: $\log f(x;\lambda) = x\log\lambda - \lambda - \log(x!)$

$$\frac{\partial^2\log f}{\partial\lambda^2} = -\frac{x}{\lambda^2} \quad\Rightarrow\quad I_1(\lambda) = \frac{E[X]}{\lambda^2} = \frac{\lambda}{\lambda^2} = \frac{1}{\lambda}$$

**Normal($\mu,\sigma^2$ known)**: derived previously — $I_1(\mu) = 1/\sigma^2$.

### Asymptotic Variance of the MLE

Under standard regularity conditions (identifiability, differentiability, interchangeability of differentiation and integration, and a well-behaved parameter space), the MLE satisfies:

$$\sqrt{n}\left(\hat\theta_{MLE} - \theta_0\right) \xrightarrow{d} N\left(0,\; I_1(\theta_0)^{-1}\right)$$

equivalently, $\hat\theta_{MLE} \overset{a}{\sim} N\left(\theta_0,\; I_n(\theta_0)^{-1}\right)$ for large $n$, where $I_n(\theta_0) = n I_1(\theta_0)$.

**Sketch of the derivation** (Taylor expansion argument): Expanding the score equation $S(\hat\theta)=0$ around $\theta_0$:

$$0 = S(\hat\theta) \approx S(\theta_0) + H(\theta_0)(\hat\theta - \theta_0)$$

Rearranging: $\hat\theta - \theta_0 \approx -H(\theta_0)^{-1}S(\theta_0)$. Since $S(\theta_0) = \sum_i s(x_i;\theta_0)$ is a sum of iid mean-zero terms with variance $I_1(\theta_0)$, the Central Limit Theorem gives $\frac{1}{\sqrt n}S(\theta_0) \xrightarrow{d} N(0,I_1(\theta_0))$, and by the Law of Large Numbers $-\frac{1}{n}H(\theta_0) \xrightarrow{p} I_1(\theta_0)$. Combining via Slutsky's theorem yields the asymptotic normality result above — this is precisely the M/Z-estimator sandwich-formula derivation specialized to the case where the model is correctly specified and $A=B=I(\theta_0)$.

### Observed vs. Expected Information

Two natural estimators of $I(\theta_0)$ are available once $\hat\theta$ is computed:

- **Expected (Fisher) information**: $I_n(\hat\theta)$ — the theoretical formula evaluated at the MLE
- **Observed information**: $J(\hat\theta) = -H(\hat\theta) = -\sum_i \frac{\partial^2 \log f(x_i;\theta)}{\partial\theta^2}\Big|_{\theta=\hat\theta}$ — the actual realized curvature of the log-likelihood at the data

[Unverified] Efron and Hinkley (1978) argued that the observed information is generally preferable to the expected information for conditional inference in finite samples, though the practical difference between the two is typically small in large samples and the choice made by default in a given software package can vary.

### Fisher Information and the CRLB

Fisher information is the denominator of the Cramér–Rao Lower Bound: $\text{Var}(\hat\theta) \geq 1/I_n(\theta)$ for any unbiased estimator, and the MLE's asymptotic variance $I_1(\theta_0)^{-1}/n$ attains this bound in the limit — this is the formal statement of MLE's asymptotic efficiency.

### Standard Errors in Practice

Given $\hat\theta$ and an estimate of $I_n(\theta_0)$ (via either observed or expected information evaluated at $\hat\theta$), the standard error of $\hat\theta_j$ is:

$$\widehat{\text{SE}}(\hat\theta_j) = \sqrt{\left[I_n(\hat\theta)^{-1}\right]_{jj}}$$

These standard errors are what econometric software reports by default for MLE-based models (logit, probit, GARCH, etc.), unless robust ("sandwich") standard errors are explicitly requested to guard against model misspecification.

### Diagram: Fisher Information → Asymptotic Variance Pipeline

```mermaid
flowchart TD
    A["Score function s(x; theta)"] --> B["I(theta) = Var of score = E[s^2]"]
    A --> C["Bartlett identity: I(theta) = -E of second derivative of log f"]
    B --> D["Additivity: I_n(theta) = n * I_1(theta)"]
    D --> E["CRLB: Var(theta_hat) >= 1 / I_n(theta)"]
    D --> F["MLE Asymptotic Variance = I_1(theta0)^-1 / n"]
    F --> G["sqrt(n)(theta_hat - theta0) converges to N(0, I_1^-1)"]
    G --> H[Standard Errors via sqrt of diagonal of inverse information]
    H --> I{Observed or Expected Information?}
    I -->|Observed: -Hessian at theta_hat| J[J(theta_hat)]
    I -->|Expected: theoretical formula at theta_hat| K[I_n(theta_hat)]
```

### Relevance to Econometrics

Fisher information is the direct source of the standard errors, t-statistics, and confidence intervals reported by default for every MLE-based econometric model — logit/probit coefficients, GARCH volatility parameters, and duration model hazard parameters all inherit their inferential apparatus from $I_n(\hat\theta)^{-1}$. The information matrix equality ($A=B=I(\theta_0)$ under correct specification) is also the formal condition tested by the widely used **Information Matrix Test** (White, 1982), which checks whether the observed-information and score-outer-product estimates of the covariance matrix agree, serving as a general specification test for the assumed likelihood model.

**Related Topics**

- The likelihood function and score equations
- Cramér–Rao Lower Bound and efficiency
- Maximum likelihood estimation and asymptotic normality
- M-estimation, Z-estimation, and the sandwich variance formula
- Information Matrix Test and model specification testing
- Likelihood Ratio, Wald, and Lagrange Multiplier tests