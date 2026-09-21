## Expected Shortfall and Tail Risk Measures

### Definition and Motivation

Expected Shortfall (ES), also called Conditional Value-at-Risk (CVaR) or Expected Tail Loss (ETL), measures the expected loss given that the loss exceeds the Value-at-Risk (VaR) threshold. Formally, for a confidence level $\alpha$ (e.g., 0.99):

$$ES_\alpha = E[L \mid L > VaR_\alpha]$$

where $L$ is the loss random variable. In continuous distributions, this is equivalent to the average of all losses in the tail beyond VaR:

$$ES_\alpha = \frac{1}{1-\alpha}\int_\alpha^1 VaR_u \, du$$

ES was adopted as the primary regulatory risk metric under the Basel Committee's Fundamental Review of the Trading Book (FRTB), replacing VaR for internal models capital calculations, largely because VaR fails to capture the severity of losses beyond the threshold.

### Why VaR Falls Short

VaR answers "what is the loss I won't exceed with probability $\alpha$?" but says nothing about how bad things get if that threshold is breached. Two portfolios can have identical VaR but wildly different tail behavior — one with a thin tail just past the threshold, another with catastrophic losses. VaR is also not a coherent risk measure because it fails **subadditivity**: it's possible for $VaR(A+B) > VaR(A) + VaR(B)$, meaning VaR can penalize diversification, which is economically nonsensical.

### Coherent Risk Measures

A risk measure $\rho$ is coherent (Artzner et al., 1999) if it satisfies four axioms:

1. **Monotonicity**: if $L_1 \le L_2$ always, then $\rho(L_1) \le \rho(L_2)$
2. **Subadditivity**: $\rho(L_1 + L_2) \le \rho(L_1) + \rho(L_2)$ (diversification never increases risk)
3. **Positive homogeneity**: $\rho(\lambda L) = \lambda \rho(L)$ for $\lambda > 0$
4. **Translation invariance**: $\rho(L + c) = \rho(L) + c$ for constant $c$

ES satisfies all four axioms for general loss distributions, while VaR only satisfies subadditivity under restrictive conditions (e.g., elliptical distributions like the normal). This is the core theoretical reason ES is preferred in modern risk frameworks.

### Mathematical Formulations

**Discrete/empirical formulation** (used in historical simulation):

$$ES_\alpha = \frac{1}{n(1-\alpha)}\sum_{i=1}^{n(1-\alpha)} L_{(i)}$$

where $L_{(i)}$ are losses sorted in descending order and $n(1-\alpha)$ is the number of tail observations averaged.

**Parametric (Normal) formulation**: for losses $L \sim N(\mu, \sigma^2)$:

$$ES_\alpha = \mu + \sigma \cdot \frac{\phi(\Phi^{-1}(\alpha))}{1-\alpha}$$

where $\phi$ is the standard normal PDF and $\Phi^{-1}$ is the inverse CDF (quantile function).

**Parametric (Student-t) formulation**: for a location-scale Student-t with $\nu$ degrees of freedom:

$$ES_\alpha = \mu + \sigma \cdot \frac{g_\nu(t_\alpha)}{1-\alpha} \cdot \frac{\nu + t_\alpha^2}{\nu - 1}$$

where $g_\nu$ is the Student-t PDF and $t_\alpha$ is the quantile. The Student-t is commonly preferred over normal for ES estimation because financial returns exhibit fat tails, and using a normal distribution systematically understates ES.

### Calculation Methods

**Key Points**

- **Historical Simulation**: Sort historical P&L observations, take the worst $(1-\alpha)$ fraction, average them. Simple, non-parametric, but sensitive to the historical window and sample size in the tail.
- **Parametric/Analytical**: Assume a distribution (normal, t, skewed-t) and use the closed-form ES formula. Fast but model-risk dependent — misspecifying tail thickness leads to material ES errors.
- **Monte Carlo Simulation**: Simulate many scenarios from a fitted (often multivariate) model, compute portfolio P&L for each, then take the tail average. Flexible for nonlinear instruments (options) but computationally expensive and sensitive to the number of tail scenarios.
- **Filtered Historical Simulation (FHS)**: Combine a GARCH-type volatility model with historical standardized residuals to better capture current volatility regime while preserving empirical tail shape.

### Worked Example

Suppose a portfolio has 1,000 simulated daily P&L outcomes (historical simulation), and we want $ES_{0.99}$.

1. $1 - \alpha = 0.01$, so we average the worst $1{,}000 \times 0.01 = 10$ losses.
2. Sort the 1,000 losses in descending order of magnitude.
3. Suppose the 10 worst losses (in $ thousands) are: 850, 820, 795, 780, 760, 745, 730, 715, 700, 690.
4. $ES_{0.99} = \frac{850+820+795+780+760+745+730+715+700+690}{10} = \frac{7585}{10} = 758.5$

So $ES_{0.99} = \$758{,}500$, versus $VaR_{0.99}$, which would simply be the 10th worst loss, $690,000. This illustrates that ES $\ge$ VaR always, and the gap widens with tail fatness.

### Comparison: VaR vs. ES

| Property | VaR | Expected Shortfall |
| --- | --- | --- |
| Interpretation | Threshold loss not exceeded with prob. $\alpha$ | Average loss beyond that threshold |
| Coherence | Not generally coherent | Coherent |
| Tail sensitivity | Ignores magnitude beyond threshold | Captures full tail severity |
| Backtestability | Well-established (Kupiec, Christoffersen tests) | Historically harder ([Inference] elicitability debate — see below) |
| Regulatory status (post-FRTB) | Used for validation/exceptions | Primary capital metric (97.5% ES) |
| Estimation stability | More stable (needs fewer tail points) | Noisier (small tail sample) |

### Elicitability and Backtesting Challenges

A well-known technical debate (Gneiting, 2011) is that ES is not **elicitable** — there is no scoring function whose minimization uniquely recovers ES as a point forecast, unlike VaR (a quantile), which is elicitable. This complicates direct backtesting of ES in isolation. In practice, this is addressed via:

- **Joint elicitability of (VaR, ES)**: Fissler and Ziegel (2016) showed the pair (VaR, ES) is jointly elicitable, enabling comparative backtests via scoring functions that penalize both jointly.
- **Basel's approach**: regulators sidestep the elicitability issue by backtesting VaR at multiple confidence levels (97.5% and 99%) as a proxy, while still using ES for capital calculation.
- **Exceedance residual tests**: compare realized losses in VaR-exceedance days against the model's predicted ES.

[Inference] The elicitability limitation is a genuinely debated area among quantitative risk practitioners and academics, and different institutions may adopt different backtesting conventions in response.

### FRTB and Regulatory Context

Under FRTB (Basel Committee, finalized standards), banks using the Internal Models Approach (IMA) must calculate market risk capital using **ES at the 97.5% confidence level** over a base horizon (10-day, with liquidity horizon scaling), replacing the Basel II.5 99% VaR standard. Key FRTB-specific features:

- **Liquidity horizons**: different risk factors are scaled to different horizons (10, 20, 40, 60, 120 days) based on how liquid they are, then aggregated.
- **Non-Modellable Risk Factors (NMRFs)**: risk factors lacking sufficient real price observations are excluded from the ES model and capitalized separately via a stressed scenario approach.
- **Stressed calibration**: ES must be calibrated partly to a period of significant financial stress, not just current market conditions.

### Other Tail Risk Measures

**Key Points**

- **Spectral Risk Measures**: generalize ES by applying a weighting function $\phi(u)$ to the quantile function, allowing the risk manager to specify arbitrary risk-aversion weighting across the loss distribution: $M_\phi = \int_0^1 \phi(u) VaR_u \, du$. ES is the special case where $\phi(u)$ is a uniform weight over $[\alpha, 1]$.
- **Expectiles**: an alternative to quantile-based risk measures, defined via asymmetric least-squares minimization. Expectiles are elicitable (unlike ES) and have been proposed as risk measures, though less regulatory adoption exists to date.
- **Tail Value-at-Risk (TVaR)**: often used synonymously with ES for continuous distributions, though technically defined slightly differently at discrete jump points in the CDF.
- **Extreme Value Theory (EVT) tail measures**: use the Generalized Pareto Distribution (GPD) to model exceedances over a high threshold via the Peaks-Over-Threshold (POT) method, providing more robust tail extrapolation than empirical methods when data beyond the threshold is sparse. The GPD-based ES formula is:

$$ES_\alpha = VaR_\alpha \cdot \left(\frac{1}{1-\xi} + \frac{\beta - \xi u}{(1-\xi)VaR_\alpha}\right)$$

where $\xi$ is the shape parameter, $\beta$ is the scale parameter, and $u$ is the threshold.

### Diagram: Tail Risk Measures Relationship (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 760 420">
<text x="380" y="25" text-anchor="middle" font-size="16" font-weight="bold">Loss Distribution: VaR vs Expected Shortfall (svg_diagram)</text>
<line x1="60" y1="350" x2="700" y2="350" stroke="black" stroke-width="1.5" />
<line x1="60" y1="350" x2="60" y2="50" stroke="black" stroke-width="1.5" />
<text x="380" y="390" text-anchor="middle" font-size="13">Loss (L)</text>
<text x="25" y="200" text-anchor="middle" font-size="13" transform="rotate(-90 25 200)">Density</text>
<path d="M 70 340 C 150 340, 200 100, 300 90 C 400 100, 480 320, 560 345 C 610 348, 660 349, 690 350" fill="none" stroke="#2c6fbb" stroke-width="2.5" />
<line x1="500" y1="60" x2="500" y2="350" stroke="#c0392b" stroke-width="2" stroke-dasharray="6,4" />
<text x="500" y="45" text-anchor="middle" font-size="12" fill="#c0392b" font-weight="bold">VaR(alpha)</text>
<path d="M 500 335 L 560 345 C 610 348, 660 349, 690 350 L 690 350 L 500 350 Z" fill="#e67e22" fill-opacity="0.45" stroke="none" />
<text x="600" y="330" text-anchor="middle" font-size="12" fill="#a04000" font-weight="bold">Tail beyond VaR</text>
<line x1="595" y1="345" x2="595" y2="350" stroke="#7d3c98" stroke-width="3" />
<circle cx="595" cy="343" r="4" fill="#7d3c98" />
<text x="595" y="325" text-anchor="middle" font-size="12" fill="#7d3c98" font-weight="bold">ES(alpha) = mean of tail</text>
<text x="150" y="150" font-size="12" fill="#2c6fbb">1 - alpha mass</text>
<line x1="150" y1="160" x2="500" y2="330" stroke="#2c6fbb" stroke-width="1" stroke-dasharray="2,3" />
</svg>

### Diagram: ES Calculation Workflow

```mermaid
flowchart TD
    A[Collect historical or simulated P&L data] --> B{Choose method}
    B -->|Historical Simulation| C[Sort losses descending]
    B -->|Parametric| D[Fit distribution: Normal / t / skewed-t]
    B -->|Monte Carlo| E[Simulate scenarios from fitted model]
    B -->|EVT / POT| F[Fit GPD to exceedances over threshold]
    C --> G[Average worst n*(1-alpha) losses]
    D --> H[Apply closed-form ES formula]
    E --> G
    F --> I[Apply GPD-based ES formula]
    G --> J[Report ES at confidence level alpha]
    H --> J
    I --> J
    J --> K[Backtest jointly with VaR / Fissler-Ziegel scoring]
    K --> L[Use in FRTB capital calculation]
```

### Practical Implementation Considerations

- **Sample size sensitivity**: because ES averages only the tail observations, it requires larger historical windows or simulation counts than VaR for stable estimates — a 99% ES from 250 daily observations averages only ~2-3 data points, which is noisy. [Inference] Many practitioners therefore favor at least 1-2 years of data or simulation-based augmentation.
- **Fat tails matter**: using a normal distribution assumption typically understates ES relative to empirical or Student-t based estimates, since real asset returns exhibit excess kurtosis.
- **Correlation/tail dependence**: for portfolios, ES calculation must account for tail dependence between risk factors (not just linear correlation), since correlations often increase during stress periods — copula-based or historical/Monte Carlo approaches capture this better than variance-covariance methods.
- **Model risk disclosure**: because ES depends heavily on model choice and tail assumptions, risk reports typically disclose the methodology and stress-period calibration alongside the number itself.

**Related Topics**

- Value-at-Risk (VaR): Parametric, Historical, and Monte Carlo Methods
- Extreme Value Theory and the Peaks-Over-Threshold Method
- FRTB Standardized Approach vs. Internal Models Approach
- Backtesting Frameworks for Market Risk Models (Kupiec, Christoffersen, Fissler-Ziegel)
- Copulas and Tail Dependence Modeling
- Stress Testing and Scenario Analysis
- GARCH Models for Volatility Forecasting in Filtered Historical Simulation