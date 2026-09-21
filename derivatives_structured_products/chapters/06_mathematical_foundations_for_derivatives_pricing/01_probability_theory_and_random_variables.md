## Probability Theory and Random Variables


### Overview

Probability theory provides the mathematical language for describing uncertainty in derivatives pricing — from the distribution of future underlying asset prices to the likelihood of default events. Random variables formalize the notion of an uncertain quantity as a mathematical object, and the machinery built around them (distributions, expectations, moments, convergence theorems) forms the foundation upon which stochastic calculus, option pricing models, and risk management frameworks are constructed.

### Probability Spaces

A **probability space** is formally defined as a triple $(\Omega, \mathcal{F}, \mathbb{P})$:

- $\Omega$: the **sample space**, the set of all possible outcomes
- $\mathcal{F}$: a **sigma-algebra** (or sigma-field) on $\Omega$ — a collection of subsets of $\Omega$ (called events) that is closed under complementation and countable unions, representing the set of events to which probabilities can be meaningfully assigned
- $\mathbb{P}$: a **probability measure**, a function $\mathcal{F} \to [0,1]$ satisfying $\mathbb{P}(\Omega) = 1$ and countable additivity: for disjoint events $A_1, A_2, \ldots$, $\mathbb{P}\left(\bigcup_i A_i\right) = \sum_i \mathbb{P}(A_i)$

**Key Points**:

- In derivatives pricing, $\Omega$ often represents the set of all possible paths a price process could take over some horizon, and $\mathcal{F}$ (or more precisely, a filtration $\{\mathcal{F}_t\}$) represents the information available at each point in time
- The distinction between the **physical (real-world) probability measure** $\mathbb{P}$ and the **risk-neutral measure** $\mathbb{Q}$ is central to derivatives pricing (covered in depth in the risk-neutral valuation section of this chapter) — both are valid probability measures on the same space, differing in how they weight outcomes

### Random Variables

A **random variable** $X$ is a measurable function $X: \Omega \to \mathbb{R}$ (or $\mathbb{R}^n$ for vector-valued cases), mapping outcomes in the sample space to real numbers. "Measurable" means that for any Borel set $B \subseteq \mathbb{R}$, the preimage $X^{-1}(B) = \{\omega \in \Omega : X(\omega) \in B\}$ belongs to $\mathcal{F}$ — this technical condition ensures probabilities like $\mathbb{P}(X \leq x)$ are well-defined.

**Discrete random variables** take values in a countable set (e.g., number of defaults in a credit portfolio, up/down outcomes in a binomial tree). Characterized by a **probability mass function (PMF)**:

$$p_X(x) = \mathbb{P}(X = x), \quad \sum_x p_X(x) = 1$$

**Continuous random variables** take values in an uncountable set (e.g., a stock price, an interest rate). Characterized by a **probability density function (PDF)** $f_X(x)$ such that:

$$\mathbb{P}(a \leq X \leq b) = \int_a^b f_X(x)\,dx, \quad \int_{-\infty}^{\infty} f_X(x)\,dx = 1$$

**Cumulative distribution function (CDF)**, defined for both discrete and continuous cases:

$$F_X(x) = \mathbb{P}(X \leq x)$$

For continuous random variables, $f_X(x) = \frac{d}{dx}F_X(x)$ wherever the derivative exists.

### Key Distributions in Derivatives Pricing

**Normal (Gaussian) distribution**, $X \sim \mathcal{N}(\mu, \sigma^2)$:

$$f_X(x) = \frac{1}{\sigma\sqrt{2\pi}} \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right)$$

The **standard normal**, $Z \sim \mathcal{N}(0,1)$, with CDF conventionally denoted $\Phi(z)$, appears directly in the Black-Scholes formula and throughout risk management (Value-at-Risk calculations, Greeks). Log-returns of asset prices are commonly modeled as normally distributed under geometric Brownian motion, which implies asset **prices** (not returns) follow a lognormal distribution.

**Lognormal distribution**: If $\ln X \sim \mathcal{N}(\mu, \sigma^2)$, then $X$ is lognormally distributed, with:

$$f_X(x) = \frac{1}{x\sigma\sqrt{2\pi}} \exp\left(-\frac{(\ln x - \mu)^2}{2\sigma^2}\right), \quad x > 0$$

This is the standard assumption for underlying asset prices in the Black-Scholes framework, ensuring prices remain strictly positive (unlike a normal distribution, which assigns positive probability to negative values).

**Binomial distribution**, $X \sim \text{Binomial}(n, p)$: models the number of "successes" (e.g., up-moves) in $n$ independent trials each with success probability $p$.

$$\mathbb{P}(X = k) = \binom{n}{k} p^k (1-p)^{n-k}$$

Foundational to the binomial option pricing model (Cox-Ross-Rubinstein), where the underlying's price evolves via discrete up/down moves at each time step.

**Poisson distribution**, $X \sim \text{Poisson}(\lambda)$: models the count of rare events over a fixed interval.

$$\mathbb{P}(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}$$

Used in jump-diffusion models (e.g., Merton's jump-diffusion model) to represent the arrival of sudden price jumps, and in credit risk models for default event counting.

**Exponential distribution**: models waiting times between events, closely related to the Poisson process; used to model time-to-default in reduced-form credit models via a hazard rate.

### Distribution Shapes (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 780 420">
<text x="390" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Normal vs Lognormal Density (svg_diagram)</text>
<line x1="80" y1="360" x2="740" y2="360" stroke="#333" stroke-width="1.5" />
<line x1="80" y1="60" x2="80" y2="360" stroke="#333" stroke-width="1.5" />
<text x="410" y="395" text-anchor="middle" font-size="13" fill="#333">x</text>
<text x="30" y="210" text-anchor="middle" font-size="13" fill="#333" transform="rotate(-90 30 210)">Density f(x)</text>
<line x1="410" y1="60" x2="410" y2="360" stroke="#ccc" stroke-width="1" stroke-dasharray="2,2" />

<path d="M 150,350 C 250,350 320,100 410,90 C 500,100 570,350 670,350" fill="none" stroke="#1f6fd6" stroke-width="3" />
<text x="500" y="115" font-size="13" fill="#1f6fd6" font-weight="bold">Normal (symmetric)</text>

<path d="M 200,358 C 280,358 320,150 380,110 C 440,140 550,300 700,350" fill="none" stroke="#d6291f" stroke-width="3" />
<text x="500" y="200" font-size="13" fill="#d6291f" font-weight="bold">Lognormal (right-skewed)</text>

<text x="80" y="375" text-anchor="middle" font-size="11" fill="#555">0</text>

</svg>

### Expectation and Moments

**Expectation (mean)** of a random variable, the probability-weighted average value:

Discrete: $\mathbb{E}[X] = \sum_x x \cdot p_X(x)$

Continuous: $\mathbb{E}[X] = \int_{-\infty}^{\infty} x \cdot f_X(x)\,dx$

**Variance**, measuring dispersion around the mean:

$$\text{Var}(X) = \mathbb{E}[(X - \mathbb{E}[X])^2] = \mathbb{E}[X^2] - (\mathbb{E}[X])^2$$

**Standard deviation** $\sigma_X = \sqrt{\text{Var}(X)}$ — in derivatives pricing, this is precisely the quantity referred to as **volatility** when applied to asset log-returns.

**Higher moments**:

- **Skewness**: $\mathbb{E}\left[\left(\frac{X-\mu}{\sigma}\right)^3\right]$ — measures asymmetry. Equity return distributions commonly exhibit negative skewness (larger, more frequent extreme negative moves than positive), a pattern closely related to the volatility skew observed in options markets.
- **Kurtosis**: $\mathbb{E}\left[\left(\frac{X-\mu}{\sigma}\right)^4\right]$ — measures tail heaviness relative to a normal distribution (which has kurtosis $= 3$, or "excess kurtosis" $= 0$). Financial return distributions typically exhibit **excess kurtosis** (fat tails), meaning extreme moves occur more frequently than a normal distribution would predict — a well-documented empirical property of financial returns often referred to as a leptokurtic distribution.

**Moment generating function (MGF)**: $M_X(t) = \mathbb{E}[e^{tX}]$, useful for deriving moments via differentiation ($\mathbb{E}[X^n] = M_X^{(n)}(0)$) and for characterizing distributions. The **characteristic function** $\phi_X(t) = \mathbb{E}[e^{itX}]$ is the Fourier-transform analog, used extensively in advanced option pricing methods (e.g., Fourier-based pricing under stochastic volatility models like Heston).

### Joint Distributions, Covariance, and Correlation

For two random variables $X, Y$, the **joint density** $f_{X,Y}(x,y)$ describes their combined behavior. **Covariance**:

$$\text{Cov}(X,Y) = \mathbb{E}[(X-\mathbb{E}[X])(Y-\mathbb{E}[Y])] = \mathbb{E}[XY] - \mathbb{E}[X]\mathbb{E}[Y]$$

**Correlation coefficient**, normalized to $[-1, 1]$:

$$\rho_{X,Y} = \frac{\text{Cov}(X,Y)}{\sigma_X \sigma_Y}$$

**Key Points**:

- Correlation is central to multi-asset derivatives pricing (basket options, spread options, correlation swaps) and to portfolio risk aggregation
- $X$ and $Y$ **independent** implies $\text{Cov}(X,Y) = 0$, but the converse is not generally true — zero correlation does not imply independence except under special cases (e.g., jointly normal random variables, where zero covariance does imply independence)
- The **multivariate normal distribution** is the standard workhorse for modeling correlated asset returns in portfolio contexts, parameterized by a mean vector and a covariance matrix, due to its analytical tractability

### Conditional Probability and Conditional Expectation

**Conditional probability**: $\mathbb{P}(A \mid B) = \dfrac{\mathbb{P}(A \cap B)}{\mathbb{P}(B)}$, for $\mathbb{P}(B) > 0$.

**Conditional expectation** $\mathbb{E}[X \mid \mathcal{G}]$, where $\mathcal{G}$ is a sub-sigma-algebra representing partial information, is the cornerstone concept for defining **martingales** — a stochastic process $\{X_t\}$ is a martingale with respect to a filtration $\{\mathcal{F}_t\}$ if:

$$\mathbb{E}[X_{t+s} \mid \mathcal{F}_t] = X_t \quad \text{for all } s \geq 0$$

**Key Points**:

- Under the risk-neutral measure $\mathbb{Q}$, discounted asset prices are constructed to be martingales — this is the mathematical essence of risk-neutral valuation and the fundamental theorem of asset pricing (developed further elsewhere in this chapter)
- The **tower property** of conditional expectation, $\mathbb{E}[\mathbb{E}[X \mid \mathcal{G}] \mid \mathcal{H}] = \mathbb{E}[X \mid \mathcal{H}]$ for $\mathcal{H} \subseteq \mathcal{G}$, is used extensively in pricing derivations involving iterated expectations across time

### Limit Theorems

**Law of Large Numbers (LLN)**: For i.i.d. random variables $X_1, \ldots, X_n$ with finite mean $\mu$, the sample average converges to the true mean as $n \to \infty$:

$$\bar{X}_n = \frac{1}{n}\sum_{i=1}^n X_i \xrightarrow{\text{a.s. or in probability}} \mu$$

**Central Limit Theorem (CLT)**: For i.i.d. random variables with finite mean $\mu$ and variance $\sigma^2$, the standardized sample sum converges in distribution to a standard normal, regardless of the underlying distribution's shape:

$$\frac{\bar{X}_n - \mu}{\sigma/\sqrt{n}} \xrightarrow{d} \mathcal{N}(0,1)$$

**Key Points**:

- The CLT provides a foundational justification for the normal (and by extension, lognormal) distribution assumption used throughout classical derivatives pricing: the aggregate effect of many small, independent random price innovations tends toward normality, even if individual innovations are not themselves normal
- [Inference] This justification is commonly cited as a theoretical rationale for the lognormal price assumption underlying Black-Scholes, though it does not by itself explain empirically observed features of real markets (fat tails, volatility clustering, jumps) that diverge from the i.i.d. normal-increment assumption — these divergences motivated the extensions covered in later sections of this chapter (jump-diffusion, stochastic volatility)
- Monte Carlo pricing methods (covered elsewhere in this chapter) rely directly on the LLN: the average payoff across a large number of simulated paths converges to the true expected payoff under the specified probability measure

### Random Variables in the Binomial-to-Continuous Limit

The binomial distribution's role in derivatives pricing is closely tied to a limiting argument: as the number of time steps $n \to \infty$ in a binomial tree (with appropriately scaled up/down move sizes and probabilities), the distribution of the terminal underlying price converges to the lognormal distribution assumed in the continuous-time Black-Scholes model. This is a direct application of the CLT to the sum of many small, independent binary log-return increments.

```mermaid
flowchart LR
    A["Binomial model:
    n discrete up/down
    steps, each Bernoulli"] --> B["Sum of n i.i.d.
    log-return increments"]
    B --> C["Apply Central
    Limit Theorem
    as n to infinity"]
    C --> D["Terminal log-price
    converges to
    Normal distribution"]
    D --> E["Terminal price
    converges to
    Lognormal distribution"]
    E --> F["Recovers continuous-time
    Black-Scholes
    price dynamics"]
```

### Change of Measure: A First Look

The **Radon-Nikodym derivative** provides the formal machinery for changing between probability measures (e.g., from the physical measure $\mathbb{P}$ to a risk-neutral measure $\mathbb{Q}$), a technique developed fully in this chapter's stochastic calculus and risk-neutral valuation sections:

$$\frac{d\mathbb{Q}}{d\mathbb{P}} = Z$$

where $Z$ is a positive random variable with $\mathbb{E}^{\mathbb{P}}[Z] = 1$, such that for any event $A$: $\mathbb{Q}(A) = \mathbb{E}^{\mathbb{P}}[Z \cdot \mathbb{1}_A]$. **Girsanov's theorem** (covered later in this chapter) formalizes this change of measure specifically for Brownian motion, showing how a drift adjustment corresponds to a specific choice of $Z$.

### Worked Example — Computing Moments of a Lognormal Distribution

If $S_T = S_0 e^{(\mu - \sigma^2/2)T + \sigma\sqrt{T}Z}$ with $Z \sim \mathcal{N}(0,1)$ (the standard geometric Brownian motion terminal price formula), then $\ln(S_T/S_0) \sim \mathcal{N}\left((\mu - \sigma^2/2)T, \sigma^2 T\right)$.

Using the standard lognormal moment formula, if $\ln X \sim \mathcal{N}(m, v^2)$, then:

$$\mathbb{E}[X] = e^{m + v^2/2}$$

Applying this with $m = (\mu - \sigma^2/2)T$ and $v^2 = \sigma^2 T$:

$$\mathbb{E}[S_T] = S_0 \cdot e^{(\mu - \sigma^2/2)T + \sigma^2 T/2} = S_0 e^{\mu T}$$

This confirms that despite the $-\sigma^2/2$ drift adjustment inside the exponent (needed so that $\ln S_T$ has the correct distribution), the **expected value** of the lognormally distributed price still grows at rate $\mu$ — the $-\sigma^2/2$ term is a **convexity/Jensen's inequality correction** ensuring consistency between the median log-price growth and the mean price growth, not a reduction in expected return itself.

### Worked Example — Central Limit Theorem in a Binomial Tree

**Setup**: A binomial tree with $n = 4$ steps, up-factor $u$, down-factor $d$, risk-neutral up-probability $q$. The terminal log-price is a sum of 4 i.i.d. Bernoulli-scaled log-return increments. As $n$ increases (holding total time $T$ fixed, with $u, d, q$ rescaled appropriately per step), the distribution of the sum of these $n$ increments progressively approximates a normal distribution by the CLT, and the model converges toward the continuous-time lognormal-price Black-Scholes framework — the basis for the well-known result that binomial tree option prices converge to the Black-Scholes price as $n \to \infty$.

### Common Pitfalls and Misapplications

- **Confusing physical and risk-neutral probabilities**: A probability derived from historical return data (physical measure $\mathbb{P}$) is not the same as the probability implied by option prices (risk-neutral measure $\mathbb{Q}$); using one where the other is required is a frequent source of pricing errors.
- **Assuming normality of returns without checking**: Financial log-returns frequently violate the normality assumption via fat tails and skewness; risk measures (e.g., Value-at-Risk) computed under a normal assumption can materially understate tail risk.
- **Misinterpreting zero correlation as independence**: Particularly relevant in multi-asset derivatives and risk aggregation, where nonlinear dependence (e.g., tail dependence, captured by copulas) can exist even when linear correlation is low or zero.
- **Conflating variance of log-returns with variance of price levels**: Because the lognormal distribution's variance formula involves both $\mu$ and $\sigma^2$ terms in a non-trivial way, naively applying normal-distribution variance intuition directly to price levels rather than log-prices can produce errors.

**Next Steps**:

- Stochastic processes and Brownian motion
- Martingales and the fundamental theorem of asset pricing
- Risk-neutral valuation and change of measure (Girsanov's theorem)
- Itô calculus and stochastic differential equations
- Monte Carlo methods for derivatives pricing
- Copulas and dependence modeling beyond linear correlation
- Jump-diffusion and stochastic volatility models
- Value-at-Risk and Expected Shortfall under non-normal distributions