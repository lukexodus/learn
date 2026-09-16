## Risk, Variance, and Standard Deviation

### Overview

Risk in corporate finance refers to the uncertainty surrounding the future returns of an asset or portfolio. Variance and standard deviation are the two primary statistical measures used to quantify this uncertainty, forming the mathematical foundation for modern portfolio theory, capital budgeting, and asset pricing models.

### Defining Risk in Financial Terms

In a corporate finance context, risk is the dispersion of possible outcomes around an expected value. An asset with a wide range of possible returns is considered riskier than one with a narrow range, even if both have the same expected (average) return.

**Key Points**

- Risk is not synonymous with "bad outcomes" — it captures uncertainty in both directions (upside and downside)
- Total risk can be decomposed into **systematic risk** (market-wide, non-diversifiable) and **unsystematic risk** (firm-specific, diversifiable)
- Variance and standard deviation measure **total risk**, not just downside risk

### Expected Return

Before computing variance, the expected return $E(R)$ must be established. For a discrete probability distribution of outcomes:

$$E(R) = \sum_{i=1}^{n} p_i R_i$$

Where $p_i$ is the probability of outcome $i$ and $R_i$ is the return in that outcome.

For historical (sample) data with $n$ observed periods, each assumed equally likely:

$$\bar{R} = \frac{1}{n}\sum_{i=1}^{n} R_i$$

### Variance

Variance measures the average squared deviation of each possible outcome from the expected return. Squaring the deviations serves two purposes: it eliminates negative signs (so deviations don't cancel out) and it penalizes larger deviations more heavily than smaller ones.

#### Population Variance (Probability-Weighted)

$$\sigma^2 = \sum_{i=1}^{n} p_i \left(R_i - E(R)\right)^2$$

#### Sample Variance (Historical Data)

When working with a sample of historical returns rather than a full probability distribution, Bessel's correction is applied, dividing by $n-1$ instead of $n$ to produce an unbiased estimator of population variance:

$$s^2 = \frac{1}{n-1}\sum_{i=1}^{n} \left(R_i - \bar{R}\right)^2$$

**Key Points**

- Variance is expressed in squared units (e.g., squared percentage returns), which makes it difficult to interpret intuitively
- A variance of zero implies a risk-free, certain return
- Larger variance indicates greater dispersion of outcomes around the mean, i.e., higher risk

### Standard Deviation

Standard deviation is simply the square root of variance, which converts the measure back into the same units as the original returns (e.g., percent), making it far more interpretable.

$$\sigma = \sqrt{\sigma^2}$$

For a sample:

$$s = \sqrt{s^2}$$

Standard deviation is the most widely quoted measure of an asset's volatility or total risk in corporate finance and investment analysis.

### Worked Example

Consider a stock with the following probability distribution of annual returns:

| Scenario | Probability ($p_i$) | Return ($R_i$) |
| --- | --- | --- |
| Recession | 0.25 | -10% |
| Normal | 0.50 | 12% |
| Boom | 0.25 | 30% |

**Step 1 — Expected Return**

$$E(R) = 0.25(-0.10) + 0.50(0.12) + 0.25(0.30) = -0.025 + 0.06 + 0.075 = 0.11$$

$E(R) = 11\%$

**Step 2 — Variance**

$$\sigma^2 = 0.25(-0.10 - 0.11)^2 + 0.50(0.12 - 0.11)^2 + 0.25(0.30 - 0.11)^2$$



$$\sigma^2 = 0.25(0.0441) + 0.50(0.0001) + 0.25(0.0361)$$



$$\sigma^2 = 0.011025 + 0.00005 + 0.009025 = 0.0201$$

**Step 3 — Standard Deviation**

$$\sigma = \sqrt{0.0201} \approx 0.1418$$

$\sigma \approx 14.18\%$

**Output**

- Expected Return: 11%
- Standard Deviation: ≈14.18%

This means the stock's actual return is expected to typically deviate from its 11% average by roughly 14.18 percentage points in either direction, under a normal-distribution assumption.

### Historical (Sample-Based) Example

Suppose a stock had the following annual returns over 4 years: 8%, -4%, 15%, 9%.

**Step 1 — Sample Mean**

$$\bar{R} = \frac{8 - 4 + 15 + 9}{4} = \frac{28}{4} = 7\%$$

**Step 2 — Sample Variance**

$$s^2 = \frac{(8-7)^2 + (-4-7)^2 + (15-7)^2 + (9-7)^2}{4-1}$$



$$s^2 = \frac{1 + 121 + 64 + 4}{3} = \frac{190}{3} \approx 63.33$$

**Step 3 — Sample Standard Deviation**

$$s = \sqrt{63.33} \approx 7.96\%$$

### Visualizing Dispersion

```mermaid
graph LR
    A["Possible Returns"] --> B["Deviation from Mean<br/>(R_i - E(R))"]
    B --> C["Squared Deviation<br/>(R_i - E(R))^2"]
    C --> D["Probability-Weighted Sum<br/>= Variance"]
    D --> E["Square Root<br/>= Standard Deviation"]
```

### Normal Distribution Interpretation

When returns are assumed to follow a normal distribution, standard deviation allows construction of confidence intervals around the expected return:

- Approximately 68% of outcomes fall within $E(R) \pm 1\sigma$
- Approximately 95% of outcomes fall within $E(R) \pm 2\sigma$
- Approximately 99.7% of outcomes fall within $E(R) \pm 3\sigma$

Using the first example ($E(R) = 11\%$, $\sigma = 14.18\%$):

- 68% confidence range: -3.18% to 25.18%
- 95% confidence range: -17.36% to 39.36%

[Inference] This interpretation relies on the assumption that returns are normally distributed, which is a simplification; empirical asset returns often exhibit fat tails and skewness relative to a true normal distribution.

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 600 300" font-family="Arial, sans-serif">
<text x="300" y="20" text-anchor="middle" font-size="14" font-weight="bold">Normal Distribution of Returns (svg_diagram)</text>
<line x1="50" y1="250" x2="550" y2="250" stroke="black" stroke-width="1" />
<path d="M 50 250 Q 150 250 200 150 Q 250 60 300 50 Q 350 60 400 150 Q 450 250 550 250" fill="none" stroke="#2c6fbb" stroke-width="2" />
<line x1="300" y1="50" x2="300" y2="250" stroke="#888" stroke-dasharray="4,4" />
<text x="300" y="270" text-anchor="middle" font-size="12">E(R) = 11%</text>
<line x1="200" y1="150" x2="200" y2="250" stroke="#c0392b" stroke-dasharray="2,2" />
<line x1="400" y1="150" x2="400" y2="250" stroke="#c0392b" stroke-dasharray="2,2" />
<text x="200" y="270" text-anchor="middle" font-size="11" fill="#c0392b">-1σ (-3.2%)</text>
<text x="400" y="270" text-anchor="middle" font-size="11" fill="#c0392b">+1σ (25.2%)</text>
<text x="300" y="290" text-anchor="middle" font-size="11" font-style="italic">≈68% of outcomes within ±1σ</text>
</svg>

### Coefficient of Variation

When comparing the relative risk of two assets with different expected returns, standard deviation alone can be misleading. The coefficient of variation (CV) standardizes risk per unit of expected return:

$$CV = \frac{\sigma}{E(R)}$$

A lower CV indicates a more favorable risk-return trade-off, holding other factors constant.

### Portfolio Context: Why Variance Doesn't Simply Add

When combining assets into a portfolio, the portfolio variance depends not only on the individual variances but also on the covariance (or correlation) between asset returns:

$$\sigma_p^2 = w_A^2\sigma_A^2 + w_B^2\sigma_B^2 + 2w_Aw_B\rho_{A,B}\sigma_A\sigma_B$$

Where $w_A, w_B$ are portfolio weights, $\sigma_A, \sigma_B$ are individual standard deviations, and $\rho_{A,B}$ is the correlation coefficient between assets A and B. This relationship underpins the diversification benefit central to Modern Portfolio Theory.

### Limitations of Variance and Standard Deviation

**Key Points**

- Treats upside and downside deviations symmetrically, even though investors typically fear downside risk more
- Assumes returns are (or can be approximated as) normally distributed; real-world return distributions often show skewness and kurtosis
- Sensitive to outliers, since deviations are squared
- Backward-looking when calculated from historical data — [Inference] past volatility is not a guaranteed predictor of future volatility
- Alternative measures such as semi-variance, downside deviation, and Value at Risk (VaR) are sometimes used to address the symmetry limitation

### Applications in Corporate Finance

- **Cost of Capital**: Standard deviation of returns informs the risk premium demanded by investors, feeding into models like CAPM
- **Capital Budgeting**: Project risk assessment uses variance/standard deviation of projected cash flows to evaluate investment viability (e.g., via scenario or sensitivity analysis)
- **Portfolio Management**: Used to construct efficient frontiers and optimize risk-adjusted returns
- **Performance Evaluation**: Standard deviation is the denominator in risk-adjusted performance metrics such as the Sharpe Ratio

$$\text{Sharpe Ratio} = \frac{E(R_p) - R_f}{\sigma_p}$$

Where $R_f$ is the risk-free rate.

**Next Steps**

- Covariance and correlation between asset returns
- Portfolio diversification and the efficient frontier
- Capital Asset Pricing Model (CAPM) and systematic risk (beta)
- Semi-variance and downside risk measures
- Value at Risk (VaR) and Conditional VaR (CVaR)
- Sharpe Ratio, Treynor Ratio, and other risk-adjusted performance metrics
- Skewness and kurtosis in return distributions