## Cramer-Rao lower bound and efficiency

### Overview

The Cramér–Rao Lower Bound (CRLB) establishes a theoretical floor on the variance achievable by any unbiased estimator of a parameter $\theta$. It formalizes the intuitive idea that there is a fundamental limit to estimation precision imposed by the amount of "information" the data carries about $\theta$. Efficiency is the property of an estimator that attains this floor.

### Fisher Information

The Fisher information $I(\theta)$ quantifies the amount of information a single observation $X$ carries about $\theta$, based on the curvature of the log-likelihood function:

$$I(\theta) = E\left[\left(\frac{\partial}{\partial \theta}\log f(X;\theta)\right)^2\right]$$

Under regularity conditions permitting differentiation under the integral sign, this is equivalent to the negative expected second derivative (curvature) of the log-likelihood:

$$I(\theta) = -E\left[\frac{\partial^2}{\partial \theta^2}\log f(X;\theta)\right]$$

**Interpretation**: A sharply peaked log-likelihood (high curvature, large $I(\theta)$) means small changes in $\theta$ produce large changes in likelihood — the data strongly discriminates between nearby parameter values, so precise estimation is possible. A flat log-likelihood (low $I(\theta)$) means the data is uninformative about $\theta$.

**Additivity for iid samples**

For $n$ iid observations, information accumulates linearly:

$$I_n(\theta) = n \cdot I_1(\theta)$$

where $I_1(\theta)$ is the information from a single observation. This is the formal reason why estimator variance typically shrinks at rate $1/n$.

### Regularity Conditions

The CRLB requires:

1. The support of $f(x;\theta)$ does not depend on $\theta$ (rules out e.g. Uniform($0,\theta$))
2. $f(x;\theta)$ is differentiable in $\theta$, and differentiation under the integral sign is valid
3. $I(\theta) > 0$ and is finite

[Unverified] Distributions violating condition 1 (parameter-dependent support) can have estimators whose variance decreases faster than $1/n$ and falls below the nominal CRLB expression, since the theorem's derivation does not apply in that setting.

### The Cramér–Rao Inequality

For any unbiased estimator $\hat{\theta}$ of $\theta$ based on a sample of size $n$:

$$\text{Var}(\hat{\theta}) \geq \frac{1}{I_n(\theta)} = \frac{1}{n \cdot I_1(\theta)}$$

**For a biased estimator** with bias $b(\theta) = E[\hat{\theta}] - \theta$, the bound generalizes to:

$$\text{Var}(\hat{\theta}) \geq \frac{[1+b'(\theta)]^2}{I_n(\theta)}$$

**Multiparameter case**

For a vector parameter $\theta \in \mathbb{R}^k$, the bound is matrix-valued: the covariance matrix of an unbiased estimator $\hat{\theta}$ satisfies

$$\text{Cov}(\hat{\theta}) - I_n(\theta)^{-1} \succeq 0$$

(positive semi-definite), where $I_n(\theta)$ is the Fisher information matrix with entries $I_{jk}(\theta) = E\left[\frac{\partial \log f}{\partial \theta_j}\frac{\partial \log f}{\partial \theta_k}\right]$.

### Derivation Sketch

The result follows from the Cauchy–Schwarz inequality applied to the score function $S(\theta) = \frac{\partial}{\partial\theta}\log f(X;\theta)$ and the estimator $\hat{\theta}$:

1. Since $E[S(\theta)] = 0$ (a standard score identity), $\text{Cov}(\hat{\theta}, S(\theta)) = E[\hat{\theta}\, S(\theta)]$
2. Using unbiasedness, $\frac{\partial}{\partial\theta}E[\hat{\theta}] = 1$, and differentiating under the integral shows this covariance equals exactly 1
3. Cauchy–Schwarz gives $1 = \text{Cov}(\hat{\theta},S(\theta))^2 \leq \text{Var}(\hat{\theta})\cdot\text{Var}(S(\theta)) = \text{Var}(\hat{\theta}) \cdot I(\theta)$
4. Rearranging yields $\text{Var}(\hat{\theta}) \geq 1/I(\theta)$

### Efficiency

**Definition**: An unbiased estimator $\hat{\theta}$ is **efficient** if it attains the CRLB with equality: $\text{Var}(\hat{\theta}) = 1/I_n(\theta)$.

**Relative efficiency** between two unbiased estimators is defined as:

$$\text{eff}(\hat{\theta}_1,\hat{\theta}_2) = \frac{\text{Var}(\hat{\theta}_2)}{\text{Var}(\hat{\theta}_1)}$$

**Asymptotic efficiency**: Under standard regularity conditions, the MLE $\hat{\theta}_{MLE}$ is asymptotically efficient — it attains the CRLB as $n\to\infty$ even when it does not attain it exactly in finite samples:

$$\sqrt{n}\left(\hat{\theta}_{MLE} - \theta\right) \xrightarrow{d} N\left(0,\, I_1(\theta)^{-1}\right)$$

This is one of the principal theoretical justifications for using MLE over alternatives like the method of moments in large-sample econometric applications.

### Worked Example: Normal Mean

For $X_1,\dots,X_n \overset{iid}{\sim} N(\mu,\sigma^2)$ with $\sigma^2$ known, the log-likelihood contribution of one observation is $\log f(x;\mu) = -\frac{1}{2}\log(2\pi\sigma^2) - \frac{(x-\mu)^2}{2\sigma^2}$.

$$\frac{\partial \log f}{\partial \mu} = \frac{x-\mu}{\sigma^2}, \qquad \frac{\partial^2 \log f}{\partial \mu^2} = -\frac{1}{\sigma^2}$$

So $I_1(\mu) = \frac{1}{\sigma^2}$, giving $I_n(\mu) = \frac{n}{\sigma^2}$ and CRLB $= \frac{\sigma^2}{n}$. The sample mean $\bar{X}$ has $\text{Var}(\bar{X}) = \sigma^2/n$ exactly — the CRLB is attained with equality, so $\bar{X}$ is an efficient (in fact, exact finite-sample efficient) estimator of $\mu$.

### Connection to Sufficiency: When the Bound Is Attained

An unbiased estimator attains the CRLB exactly (in finite samples, not just asymptotically) if and only if the score function factors as:

$$\frac{\partial}{\partial\theta}\log f(x;\theta) = I(\theta)\big[T(x) - \theta\big]$$

for some statistic $T(x)$, which is precisely the condition satisfied by estimators of the natural parameter in an **exponential family**. This is why efficient finite-sample estimators (like $\bar{X}$ for the Normal mean) tend to arise in exponential-family models, linking this topic directly to sufficiency and the exponential family structure.

### Diagram: CRLB Logic Flow

```mermaid
flowchart TD
    A[Likelihood function f of x given theta] --> B[Score function: derivative of log f wrt theta]
    B --> C["Fisher Information I(theta) = Var of score"]
    C --> D["CRLB = 1 / I(theta) for single obs"]
    D --> E["CRLB for n iid obs = 1 / (n * I(theta))"]
    F[Unbiased Estimator theta_hat] --> G{Var of theta_hat equals CRLB?}
    G -->|Yes| H[Estimator is Efficient]
    G -->|No, but ratio to n goes to CRLB as n grows| I[Asymptotically Efficient - e.g. MLE]
    G -->|No| J[Inefficient unbiased estimator]
    H --> K[Score factors as I(theta) times T(x) minus theta]
    K --> L[Exponential Family natural parameter estimators]
```

### Relevance to Econometrics

The CRLB provides the benchmark against which the asymptotic variance of MLE-based econometric estimators (logit, probit, GARCH, discrete choice models) is judged: the asymptotic covariance matrix reported by econometric software as $[I_n(\hat\theta)]^{-1}$ (the inverse of the observed or expected information matrix) is exactly the CRLB evaluated at the estimated parameter, and standard errors are derived from its square root. [Inference] In finite samples with moderate $n$, the observed information matrix (Hessian-based) and expected information matrix (Fisher-based) can yield somewhat different standard error estimates, and the choice between them is sometimes an implementation-specific detail across statistical packages.

**Related Topics**

- Maximum likelihood estimation: derivation and asymptotic properties
- Sufficiency, exponential families, and score function factorization
- Asymptotic normality and the delta method
- Observed vs. expected Fisher information in practice
- Rao-Blackwell theorem and UMVUE construction
- Information matrix equality and robust (sandwich) standard errors