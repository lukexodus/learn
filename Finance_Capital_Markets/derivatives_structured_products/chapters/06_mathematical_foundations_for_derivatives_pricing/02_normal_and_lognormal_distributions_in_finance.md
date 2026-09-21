## Normal and Lognormal Distributions in Finance

### Overview

The normal and lognormal distributions are the two most widely used probability distributions in classical derivatives pricing. The normal distribution underlies the modeling of asset **log-returns** and appears directly in closed-form pricing formulas via the cumulative normal function; the lognormal distribution describes the resulting **price levels** under the standard geometric Brownian motion assumption. Understanding the precise relationship between these two distributions — and where the standard assumptions break down empirically — is foundational to both pricing theory and practical risk management.

### The Normal Distribution: Definition and Properties

A random variable $X \sim \mathcal{N}(\mu, \sigma^2)$ has probability density function:

$$f_X(x) = \frac{1}{\sigma\sqrt{2\pi}} \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right), \quad x \in (-\infty, \infty)$$

**Key Points**:

- Fully characterized by two parameters: mean $\mu$ (location) and variance $\sigma^2$ (spread)
- Symmetric around $\mu$; skewness $= 0$, kurtosis $= 3$ (excess kurtosis $= 0$)
- Support is the entire real line — the normal distribution assigns strictly positive probability density to arbitrarily large negative values, which is precisely why it is unsuitable as a direct model for asset **prices** (which cannot be negative), but well-suited to modeling **log-returns**, which are unbounded in both directions
- **Standard normal**: $Z \sim \mathcal{N}(0,1)$, with CDF conventionally denoted $\Phi(z) = \mathbb{P}(Z \leq z)$; any normal random variable can be standardized via $Z = (X-\mu)/\sigma$

### Why Log-Returns, Not Simple Returns

Asset log-returns, defined as $r_t = \ln(S_t / S_{t-1})$, are the standard building block for the normal-distribution assumption in finance, rather than simple returns $R_t = (S_t - S_{t-1})/S_{t-1}$.

**Key Points**:

- **Additivity across time**: Log-returns over consecutive periods sum to the log-return over the combined period: $\ln(S_T/S_0) = \sum_{t=1}^{T} \ln(S_t/S_{t-1})$. Simple returns do not have this property (compounding of simple returns is multiplicative, not additive), making log-returns far more tractable for multi-period statistical analysis and for applying the Central Limit Theorem to the sum of increments.
- **Guaranteed positivity of prices**: If log-returns are normally distributed (and hence unbounded), the resulting price $S_T = S_0 e^{\sum r_t}$ is automatically constrained to be strictly positive, since the exponential function maps the entire real line to $(0, \infty)$ — this consistency is a primary reason the log-return/lognormal-price pairing is the standard modeling choice rather than modeling simple returns as normal (which would permit negative prices).
- **Approximate equivalence for small returns**: For small returns, $\ln(1+R) \approx R$, so log-returns and simple returns are numerically close for typical daily or even monthly return magnitudes; the distinction matters more over longer horizons or during large price moves.

### The Lognormal Distribution: Definition and Properties

A random variable $X$ is lognormally distributed, $X \sim \text{LogNormal}(m, v^2)$, if $\ln X \sim \mathcal{N}(m, v^2)$. Its density is:

$$f_X(x) = \frac{1}{x \cdot v\sqrt{2\pi}} \exp\left(-\frac{(\ln x - m)^2}{2v^2}\right), \quad x > 0$$

**Key moment formulas**:

$$\mathbb{E}[X] = e^{m + v^2/2}$$



$$\text{Var}(X) = \left(e^{v^2} - 1\right) e^{2m + v^2}$$



$$\text{Median}(X) = e^m \qquad \text{Mode}(X) = e^{m - v^2}$$

**Key Points**:

- The lognormal distribution is **right-skewed** (positive skewness) — it has a long right tail and is bounded below by zero, in contrast to the normal distribution's symmetry
- Mean > Median > Mode, a direct consequence of the right-skew — this ordering is a useful diagnostic for recognizing lognormal-like behavior in data
- Support is strictly $(0, \infty)$, making it a natural candidate for modeling any quantity that cannot be negative: asset prices, interest rate levels (in some models), and time-to-default in certain credit risk contexts

### Distribution Shape Comparison (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 780 440">
<text x="390" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a1a">Normal (Log-Returns) vs Lognormal (Prices) (svg_diagram)</text>
<line x1="60" y1="200" x2="380" y2="200" stroke="#333" stroke-width="1.5" />
<line x1="60" y1="60" x2="60" y2="200" stroke="#333" stroke-width="1.5" />
<text x="220" y="225" text-anchor="middle" font-size="12" fill="#333">Log-Return r</text>
<path d="M 90,190 C 150,190 190,70 220,65 C 250,70 290,190 350,190" fill="none" stroke="#1f6fd6" stroke-width="3" />
<text x="220" y="50" text-anchor="middle" font-size="13" fill="#1f6fd6" font-weight="bold">Normal(mu, sigma^2)</text>
<line x1="220" y1="60" x2="220" y2="200" stroke="#aaa" stroke-width="1" stroke-dasharray="3,3" />
<text x="220" y="215" text-anchor="middle" font-size="11" fill="#666">0</text>

<text x="220" y="255" text-anchor="middle" font-size="18" fill="#555">↓ exponentiate: S = S0·e^r ↓</text>

<line x1="440" y1="400" x2="760" y2="400" stroke="#333" stroke-width="1.5" />
<line x1="440" y1="290" x2="440" y2="400" stroke="#333" stroke-width="1.5" />
<text x="600" y="420" text-anchor="middle" font-size="12" fill="#333">Price S</text>
<path d="M 460,398 C 500,398 520,320 560,300 C 600,320 660,370 750,395" fill="none" stroke="#d6291f" stroke-width="3" />
<text x="600" y="280" text-anchor="middle" font-size="13" fill="#d6291f" font-weight="bold">LogNormal(m, v^2)</text>
</svg>

### Geometric Brownian Motion and the Terminal Price Formula

Under the standard geometric Brownian motion (GBM) assumption used in the Black-Scholes framework, the underlying price evolves as:

$$dS_t = \mu S_t \, dt + \sigma S_t \, dW_t$$

Applying Itô's lemma yields the closed-form solution for the log-price:

$$\ln S_T = \ln S_0 + \left(\mu - \frac{\sigma^2}{2}\right)T + \sigma W_T$$

Since $W_T \sim \mathcal{N}(0, T)$, this means:

$$\ln(S_T/S_0) \sim \mathcal{N}\left(\left(\mu - \frac{\sigma^2}{2}\right)T,\ \sigma^2 T\right)$$

and therefore $S_T$ is lognormally distributed with $m = \ln S_0 + (\mu - \sigma^2/2)T$ and $v^2 = \sigma^2 T$.

**The $-\sigma^2/2$ term** (sometimes called the "Itô correction" or "volatility drag") is a direct consequence of Itô's lemma applied to the exponential function and Jensen's inequality; it ensures that despite this apparent downward adjustment inside the exponent, the **expected value** of the price still grows at the full rate $\mu$:

$$\mathbb{E}[S_T] = S_0 e^{\mu T}$$

This apparent tension — a negative adjustment to the exponent's drift term, yet no reduction in expected price growth — is one of the most common sources of confusion when first encountering GBM, and is resolved by recognizing that the median of a lognormal distribution ($S_0 e^{(\mu-\sigma^2/2)T}$) is lower than its mean ($S_0 e^{\mu T}$), consistent with the general mean > median relationship for right-skewed distributions.

### Role in the Black-Scholes Formula

The Black-Scholes call price formula draws directly on the standard normal CDF:

$$C = S_0 \Phi(d_1) - Ke^{-rT}\Phi(d_2)$$



$$d_1 = \frac{\ln(S_0/K) + (r + \sigma^2/2)T}{\sigma\sqrt{T}}, \qquad d_2 = d_1 - \sigma\sqrt{T}$$

**Key Points**:

- $\Phi(d_2)$ is interpretable as the risk-neutral probability that the option expires in-the-money (under the $\mathbb{Q}$ measure, not the physical measure $\mathbb{P}$) — a direct consequence of the underlying's lognormality under GBM
- $\Phi(d_1)$ is the option's delta for a call and is related to, but not identical to, a probability — it represents the risk-neutral expectation of the terminal stock price conditional on the option finishing in the money, appropriately normalized; [Inference] a common informal shorthand describes $\Phi(d_1)$ as an approximate probability-like quantity for intuition purposes, but a precise interpretation requires the change-of-numeraire / stock-measure framework, so this shorthand should not be treated as a literal probability statement
- The entire closed-form Black-Scholes derivation depends on the lognormal-price assumption; deviations from lognormality (fat tails, skewness in the underlying's actual distribution) are precisely what the implied volatility skew/smile reflects when Black-Scholes is used as a quoting convention rather than a literal model of price dynamics

### Parameter Estimation from Market Data

**Estimating $\sigma$ (historical/realized volatility)**: Given a sample of $n$ log-returns $r_1, \ldots, r_n$ observed at some frequency (daily, weekly), the sample standard deviation:

$$\hat{\sigma}_{\text{period}} = \sqrt{\frac{1}{n-1}\sum_{i=1}^n (r_i - \bar{r})^2}$$

is annualized by scaling with the square root of the number of periods per year (a direct consequence of variance scaling linearly with time under i.i.d. increments, per the CLT/variance-additivity property discussed in the probability theory section of this chapter):

$$\hat{\sigma}_{\text{annual}} = \hat{\sigma}_{\text{period}} \times \sqrt{\text{periods per year}}$$

For daily returns, this typically means multiplying by $\sqrt{252}$ (the conventional number of trading days per year).

**Key Points**:

- This **square-root-of-time scaling** relies on the assumption of i.i.d., serially uncorrelated returns; empirically, financial returns often exhibit volatility clustering (autocorrelation in squared or absolute returns) even when returns themselves are close to uncorrelated, which can cause naive square-root scaling to misstate volatility over longer horizons
- **Implied volatility**, by contrast, is not estimated from historical data but is backed out from observed option market prices by inverting the Black-Scholes formula — it represents the market's forward-looking volatility expectation embedded in current option prices, and typically differs from historical/realized volatility, sometimes substantially around anticipated events

### Empirical Departures from Normality and Lognormality

Despite its central role in classical pricing theory, the normal/lognormal framework is well known to diverge from empirically observed asset return behavior in several specific ways:

- **Fat tails (excess kurtosis)**: Empirical return distributions typically exhibit kurtosis greater than the normal distribution's value of 3, meaning extreme moves (both up and down) occur more frequently than the normal model predicts. This is among the most robustly documented empirical features of financial return data across asset classes and time periods.
- **Negative skewness in equity returns**: Equity index returns in particular commonly exhibit negative skewness — large downside moves tend to be more frequent or severe than equivalently sized upside moves — a pattern often linked to the leverage effect (falling equity prices increase a firm's financial leverage, raising equity return volatility) and to crash risk premia.
- **Volatility clustering**: Periods of high volatility tend to be followed by further high volatility, and calm periods by more calm periods (formalized in GARCH-family models) — a violation of the i.i.d. assumption underlying the basic GBM/CLT justification for normality, even though it does not necessarily violate normality of returns conditional on the current volatility level.
- **Volatility skew/smile in options markets**: The fact that implied volatilities vary systematically by strike (and typically show a downward-sloping "skew" for equity index options, with higher implied volatility for OTM puts than OTM calls) is direct market evidence that traders do not price options as though the underlying is lognormally distributed with a single constant volatility — the skew reflects the market's pricing of fat tails and negative skewness relative to the lognormal benchmark.

[Inference] These empirical departures are the primary motivation for the extensions to the basic normal/lognormal framework covered later in this chapter and elsewhere in the curriculum — stochastic volatility models (e.g., Heston), jump-diffusion models (e.g., Merton), and local volatility models — each of which relaxes a different aspect of the constant-volatility, continuous-path, normally-distributed-increment assumption; the specific choice of extension in practice depends on which empirical feature (fat tails, skew, jumps, volatility clustering) is most material for the instrument and horizon being priced.

### Quantile Table — Standard Normal Distribution

Common reference values used throughout options pricing and risk management (Value-at-Risk, confidence intervals):

| Confidence Level | $z$-value ($\Phi^{-1}$) | Use Case |
| --- | --- | --- |
| 90% | 1.2816 | 1-sided VaR (90%) |
| 95% | 1.6449 | 1-sided VaR (95%), common regulatory threshold |
| 97.5% | 1.9600 | 2-sided 95% confidence interval bound |
| 99% | 2.3263 | 1-sided VaR (99%) |
| 99.9% | 3.0902 | Tail-risk / stress-testing threshold |

**Key Points**: These values are frequently misapplied when the underlying data exhibits fat tails — a "99% VaR" computed using the normal-distribution $z$-value of 2.3263 will generally **understate** the true tail risk of a fat-tailed distribution, since actual extreme percentiles lie further out than the normal distribution predicts.

### Worked Example — Converting Historical Volatility to a Price Distribution

**Setup**: A stock currently trades at $S_0 = \$100$. Historical daily log-return standard deviation is $0.0126$ (1.26%). Annualized: $\hat{\sigma} = 0.0126 \times \sqrt{252} \approx 0.20$ (20%). Assume $\mu = 0.08$ (8% expected annual drift) and $T = 1$ year.

**Distribution of $\ln(S_T/S_0)$**:

$$\ln(S_T/S_0) \sim \mathcal{N}\left((0.08 - 0.20^2/2) \times 1,\ 0.20^2 \times 1\right) = \mathcal{N}(0.06, 0.04)$$

So $m = \ln(100) + 0.06 = 4.6652$, $v^2 = 0.04$, $v = 0.20$.

**Median price**: $e^m = e^{4.6652} \approx \$106.18$

**Mean (expected) price**: $S_0 e^{\mu T} = 100 \times e^{0.08} \approx \$108.33$

**95% confidence interval for $\ln(S_T/S_0)$** (using $z = 1.96$): $0.06 \pm 1.96 \times 0.20 = [-0.332, 0.452]$

Exponentiating: $S_T$ range $\approx [100 \times e^{-0.332}, 100 \times e^{0.452}] \approx [\$71.75, \$157.15]$

This illustrates the right-skewed nature of the resulting price distribution: the interval is **not symmetric** around either the mean or median in price-level terms, even though the underlying log-price interval is symmetric — a direct visual consequence of exponentiating a symmetric normal interval.

### Common Pitfalls

- **Applying normal-distribution intuition directly to prices**: Symmetric confidence intervals, standard VaR shortcuts, and mean-reversion assumptions that are valid for normally distributed log-returns do not translate directly to price levels without accounting for the lognormal transformation's asymmetry.
- **Forgetting the $-\sigma^2/2$ drift adjustment**: Omitting this term when simulating GBM paths or computing expected terminal prices from the log-price formula is a common implementation error that biases simulated expected prices downward relative to the intended $\mu$.
- **Treating implied volatility as historical volatility, or vice versa**: These are conceptually distinct (backward-looking realized statistic vs. forward-looking market-implied expectation) and can diverge substantially, particularly around anticipated events — using one where the other is appropriate is a frequent source of confusion for practitioners new to the distinction.
- **Ignoring fat tails in risk calculations**: Using normal-distribution quantiles for tail-risk metrics (VaR, stress scenarios) on data known to exhibit excess kurtosis systematically understates the probability and magnitude of extreme outcomes.

**Related Topics**:

- Probability theory and random variables (this chapter, foundational)
- Stochastic processes and Brownian motion
- Itô's lemma and stochastic calculus derivations
- The Black-Scholes-Merton model in full derivation
- Implied volatility, skew, and the volatility smile
- Jump-diffusion and stochastic volatility models (Merton, Heston)
- Value-at-Risk and Expected Shortfall methodologies
- GARCH and volatility clustering models