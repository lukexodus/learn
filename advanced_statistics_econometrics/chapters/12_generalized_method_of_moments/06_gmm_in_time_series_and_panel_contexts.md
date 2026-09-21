## GMM in Time Series and Panel Contexts

### Overview

Generalized Method of Moments (GMM) extends naturally from cross-sectional settings into time series and panel data, but the temporal and cross-sectional dependence structures introduce distinct estimation challenges: serial correlation in moment conditions, weak instrument problems from persistent series, and the need for dynamic panel-specific instrument construction. This chapter covers GMM estimation for time series models (particularly linear and nonlinear rational expectations models) and dynamic panel data models (Arellano-Bond, Arellano-Bover/Blundell-Bond).

### GMM in Time Series: Foundations

**Setup**

Consider a time series model where economic theory implies a set of orthogonality (moment) conditions:

$$E[g(w_t, \theta_0)] = 0$$

where $w_t$ is a vector of observed variables at time $t$, $\theta_0$ is the true parameter vector, and $g(\cdot)$ is a vector-valued function of dimension $q \geq k$ (number of moments at least as large as number of parameters).

The sample analog is:

$$g_T(\theta) = \frac{1}{T}\sum_{t=1}^{T} g(w_t, \theta)$$

The GMM estimator minimizes the quadratic form:

$$\hat{\theta}_{GMM} = \arg\min_{\theta} \, g_T(\theta)' W_T \, g_T(\theta)$$

where $W_T$ is a positive semi-definite weighting matrix.

**Key Time Series Complication: Serial Correlation**

Unlike i.i.d. cross-sectional data, $g(w_t, \theta_0)$ in time series contexts is frequently serially correlated. This arises naturally in rational expectations models where $g(w_t,\theta_0) = z_t \cdot u_t(\theta_0)$, and the error term $u_t$ may be a moving-average process (e.g., in models with overlapping forecast horizons) even under correctly specified expectations.

Because of this, the efficient weighting matrix must account for the entire autocovariance structure of the moment process, not merely its contemporaneous variance.

### The Optimal Weighting Matrix: HAC Estimation

The asymptotically efficient GMM weighting matrix is the inverse of the long-run variance-covariance matrix of the moment conditions:

$$S = \sum_{j=-\infty}^{\infty} E[g(w_t,\theta_0) \, g(w_{t-j},\theta_0)']$$

Since this involves infinite lags, in practice $S$ is estimated using a **Heteroskedasticity and Autocorrelation Consistent (HAC)** estimator, most commonly the **Newey-West estimator**:

$$\hat{S} = \hat{\Gamma}_0 + \sum_{j=1}^{L} k(j,L)\left(\hat{\Gamma}_j + \hat{\Gamma}_j'\right)$$

where:

- $\hat{\Gamma}_j = \frac{1}{T}\sum_{t=j+1}^{T} \hat{g}_t \hat{g}_{t-j}'$ is the sample autocovariance at lag $j$
- $k(j,L)$ is a kernel weighting function (Bartlett kernel: $k(j,L) = 1 - j/(L+1)$)
- $L$ is the bandwidth/truncation lag, which must grow with $T$ (e.g., $L = O(T^{1/3})$) for consistency

**[Inference]** The choice of bandwidth $L$ and kernel involves a bias-variance trade-off: larger $L$ reduces bias from truncated autocovariances but increases estimator variance; this trade-off is why automatic bandwidth selection procedures (Andrews 1991; Newey-West 1994) are commonly used in applied work, though the "optimal" choice remains sensitive to the underlying DGP.

**Alternative kernels** include the Parzen kernel and Quadratic Spectral (QS) kernel, the latter being asymptotically MSE-optimal among a broad class but not guaranteeing positive semi-definiteness in finite samples without care (the QS kernel does produce PSD estimates by construction when implemented correctly, unlike naive truncated estimators).

### Two-Step Efficient GMM Procedure

1. **Step 1**: Obtain a consistent (but inefficient) estimate $\hat{\theta}^{(1)}$ using $W_T = I$ (identity matrix) or another simple positive-definite weight matrix.
2. **Compute residuals**: Use $\hat{\theta}^{(1)}$ to compute $\hat{g}_t = g(w_t, \hat{\theta}^{(1)})$.
3. **Estimate $\hat{S}$**: Apply the HAC estimator (Newey-West) to $\{\hat{g}_t\}$.
4. **Step 2**: Re-estimate with efficient weight matrix $W_T = \hat{S}^{-1}$:

$$\hat{\theta}_{GMM} = \arg\min_\theta \, g_T(\theta)'\hat{S}^{-1} g_T(\theta)$$

This can be iterated (iterated GMM) or extended to continuously-updating GMM (CUE), where $S(\theta)$ is re-estimated at every value of $\theta$ during optimization:

$$\hat{\theta}_{CUE} = \arg\min_\theta \, g_T(\theta)' \hat{S}(\theta)^{-1} g_T(\theta)$$

**[Inference]** CUE is often preferred in finite samples for reducing the bias associated with using $\hat{\theta}^{(1)}$-based weighting, though it is computationally more demanding and its optimization surface can be less well-behaved.

### Application: Hansen-Singleton Euler Equation Estimation

The canonical time series GMM application is estimating rational expectations Euler equations from consumption-based asset pricing models (Hansen and Singleton, 1982). The stochastic Euler equation:

$$E_t\left[\beta \left(\frac{C_{t+1}}{C_t}\right)^{-\gamma} R_{t+1} - 1\right] = 0$$

implies, for any variable $z_t$ in the time-$t$ information set:

$$E\left[\left(\beta \left(\frac{C_{t+1}}{C_t}\right)^{-\gamma} R_{t+1} - 1\right) z_t\right] = 0$$

This generates moment conditions using **instruments dated $t$ or earlier** (lagged consumption growth, lagged returns, constants), because rational expectations imply the forecast error is orthogonal to the time-$t$ information set. GMM estimates $(\beta, \gamma)$ using these orthogonality conditions, with HAC weighting to account for potential serial correlation in the pricing errors (which can arise from time aggregation or measurement issues even under the null).

### Weak Instruments and Persistence in Time Series GMM

**[Inference]** A well-documented issue in time series GMM (e.g., estimating Euler equations, DSGE Euler/New Keynesian Phillips Curve parameters) is that instruments constructed from highly persistent (near-unit-root) series carry little information about the endogenous regressor's innovations, leading to weak-instrument bias and unreliable inference — this is a recurring finding across the empirical macro-finance literature rather than a universal law, and severity is model- and dataset-dependent.

Diagnostics and remedies mirror the cross-sectional GMM/IV weak-instrument toolkit:

- Cragg-Donald / Kleibergen-Paap statistics adapted for time series
- Stock-Yogo-style critical values (with caution, since these are derived under i.i.d. assumptions)
- Limited-information alternatives and identification-robust inference (Anderson-Rubin type statistics extended to GMM settings)

### GMM in Panel Data: Overview

Panel GMM adds a cross-sectional dimension $(i = 1, \ldots, N)$ to the time dimension $(t = 1, \ldots, T)$, and is dominant in **dynamic panel data models**:

$$y_{it} = \alpha y_{i,t-1} + x_{it}'\beta + \eta_i + \varepsilon_{it}$$

where $\eta_i$ is a time-invariant individual fixed effect and $\varepsilon_{it}$ is idiosyncratic error.

**The core problem**: OLS on this equation is biased because $y_{i,t-1}$ is mechanically correlated with $\eta_i$. Within (fixed-effects) transformation removes $\eta_i$ but induces a different correlation: after first-differencing,

$$\Delta y_{it} = \alpha \Delta y_{i,t-1} + \Delta x_{it}'\beta + \Delta \varepsilon_{it}$$

$\Delta y_{i,t-1} = y_{i,t-1} - y_{i,t-2}$ is correlated with $\Delta \varepsilon_{it} = \varepsilon_{it} - \varepsilon_{i,t-1}$ through the shared $y_{i,t-1}$/$\varepsilon_{i,t-1}$ term — this is the **Nickell bias** (Nickell, 1981), which is $O(1/T)$ and does not vanish as $N \to \infty$ with fixed $T$.

### Arellano-Bond (Difference GMM)

**Solution**: Instrument the differenced lagged dependent variable with **deeper lags of the level** of $y$, which are uncorrelated with $\Delta \varepsilon_{it}$ under the assumption that $\varepsilon_{it}$ is not serially correlated.

For period $t$, valid instruments are $y_{i,t-2}, y_{i,t-3}, \ldots, y_{i,1}$ (all lags 2 periods or more back), since these predate the differenced error term.

**Moment conditions**:

$$E[y_{i,t-s} \cdot \Delta\varepsilon_{it}] = 0 \quad \text{for } s \geq 2$$

This generates an expanding instrument set as $t$ increases — a distinctive **"GMM-style" instrument matrix** where each time period has its own valid instrument set, structured in a block-diagonal pattern:

$$Z_i = \begin{bmatrix}
y_{i1} & 0 & 0 & \cdots \\
0 & y_{i1}, y_{i2} & 0 & \cdots \\
0 & 0 & y_{i1}, y_{i2}, y_{i3} & \cdots \\
\vdots & & & \ddots
\end{bmatrix}$$

The full set of moment conditions is stacked and estimated via two-step GMM with a weighting matrix based on $E[Z_i' \Delta\varepsilon_i \Delta\varepsilon_i' Z_i]$.

**Windmeijer (2005) finite-sample correction**: Because the two-step weighting matrix is itself estimated from first-step residuals, two-step Arellano-Bond standard errors are severely downward-biased in finite samples. The Windmeijer correction adjusts the standard errors to account for this estimation uncertainty and is now standard practice (implemented by default in most modern software, e.g., Stata's `xtabond2`, R's `plm`/`pgmm`).

### Arellano-Bover / Blundell-Bond (System GMM)

**Motivation**: Difference GMM instruments perform poorly when $y_{it}$ is highly persistent (near unit root), because lagged levels are then weak instruments for differenced variables (the same weak-instrument logic as in time series GMM above).

**Solution**: Augment the difference equations with **level equations**, instrumented by **lagged differences**:

$$E[\Delta y_{i,t-1} \cdot (\eta_i + \varepsilon_{it})] = 0$$

This condition holds under an additional assumption of **mean stationarity**: that deviations of initial conditions from their long-run means are uncorrelated with the fixed effect.

**System GMM** stacks the difference equations (instrumented with levels) and the level equations (instrumented with differences) into one system, jointly estimated by GMM. This substantially improves efficiency and reduces weak-instrument bias relative to difference GMM alone, particularly for persistent series and short panels ($T$ small relative to $N$).

### Instrument Proliferation

**[Inference]** A well-known practical problem: because the Arellano-Bond/Blundell-Bond instrument count grows quadratically with $T$, GMM panel estimators with many time periods can produce an instrument count that exceeds or rivals $N$, causing:

- Overfitting of the endogenous variable (weakening the Hansen J-test's power to detect misspecification — with many instruments the J-test can spuriously fail to reject)
- Biased coefficient estimates toward the (biased) within/OLS estimates
- Numerically singular or near-singular weighting matrices

**Standard remedies**:

1. **Collapse the instrument matrix**: restrict to one instrument per lag distance rather than per lag-time pair, reducing instrument count from quadratic to linear in $T$ (Roodman, 2009)
2. **Limit lag depth**: use only a subset of available lags (e.g., $t-2$ and $t-3$ only) rather than the full history
3. **Principal components** of the instrument set to reduce dimensionality

### Specification Testing in Panel GMM

**Hansen J-test (overidentification test)**: Tests the joint validity of the overidentifying moment conditions.

$$J = T \cdot g_T(\hat\theta)' \hat{S}^{-1} g_T(\hat\theta) \sim \chi^2_{q-k}$$

**[Inference]** A failure to reject is necessary but not sufficient evidence of instrument validity, and — as noted above — the test loses power when instrument count is large relative to $N$, so a "passing" J-test in an instrument-proliferated specification should not be treated as strong validation.

**Arellano-Bond AR(1)/AR(2) serial correlation tests**: Since the identification strategy assumes $\varepsilon_{it}$ is not serially correlated, these tests check the differenced residuals $\Delta\hat\varepsilon_{it}$ for autocorrelation:

- AR(1) in differences is **expected** to reject (since $\Delta\varepsilon_{it}$ and $\Delta\varepsilon_{i,t-1}$ mechanically share $\varepsilon_{i,t-1}$)
- AR(2) in differences should **not** reject; rejection here signals that the original $\varepsilon_{it}$ is serially correlated, invalidating the lag-2-and-beyond instrument strategy

**Difference-in-Hansen test**: Tests the validity of the subset of additional moment conditions introduced by System GMM (the level-equation instruments) versus the Difference GMM baseline.

### Worked Comparison: Difference vs. System GMM Diagnostics

| Diagnostic | Difference GMM | System GMM |
| --- | --- | --- |
| Instrument source | Lagged levels for differenced equation | Lagged levels + lagged differences |
| Key identifying assumption | No serial correlation in $\varepsilon_{it}$ | Above + mean stationarity |
| Performance with persistent $y$ | Weak instruments, biased toward within estimator | More robust, higher efficiency |
| Overidentification test | Hansen J-test | Hansen J-test + Difference-in-Hansen |
| Typical software | `xtabond` (Stata), `pgmm` (R, `transformation="d"`) | `xtabond2` (Stata), `pgmm` (R, `transformation="ld"`) |

### Diagram: Panel GMM Estimation Workflow (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 900 620" font-family="Helvetica, Arial, sans-serif">
<text x="450" y="30" font-size="18" font-weight="bold" text-anchor="middle">Dynamic Panel GMM Estimation Workflow (svg_diagram)</text>
<rect x="330" y="55" width="240" height="50" rx="6" fill="#e8f0fe" stroke="#2255aa" stroke-width="1.5" />
<text x="450" y="85" font-size="13" text-anchor="middle">Level equation:
y_it = α y_i,t-1 + x'β + η_i + ε_it</text>
<line x1="450" y1="105" x2="450" y2="135" stroke="#333" stroke-width="1.5" marker-end="url(#arrow)" />
<rect x="330" y="140" width="240" height="55" rx="6" fill="#fdf3d9" stroke="#a67c00" stroke-width="1.5" />
<text x="450" y="162" font-size="13" text-anchor="middle">First-difference to remove η_i</text>
<text x="450" y="180" font-size="12" text-anchor="middle">Δy_it = α Δy_i,t-1 + Δx'β + Δε_it</text>
<line x1="450" y1="195" x2="450" y2="225" stroke="#333" stroke-width="1.5" marker-end="url(#arrow)" />
<rect x="290" y="230" width="320" height="55" rx="6" fill="#fde8e8" stroke="#aa2222" stroke-width="1.5" />
<text x="450" y="252" font-size="13" text-anchor="middle">Problem: Δy_i,t-1 correlated with Δε_it</text>
<text x="450" y="270" font-size="12" text-anchor="middle">(shares ε_i,t-1 term — Nickell bias)</text>
<line x1="450" y1="285" x2="450" y2="315" stroke="#333" stroke-width="1.5" marker-end="url(#arrow)" />
<rect x="80" y="320" width="330" height="90" rx="6" fill="#e8f8ec" stroke="#227744" stroke-width="1.5" />
<text x="245" y="342" font-size="13" font-weight="bold" text-anchor="middle">Arellano-Bond (Difference GMM)</text>
<text x="245" y="362" font-size="12" text-anchor="middle">Instrument Δy_i,t-1 with</text>
<text x="245" y="378" font-size="12" text-anchor="middle">y_i,t-2, y_i,t-3, ... (levels, lag≥2)</text>
<text x="245" y="396" font-size="11" font-style="italic" text-anchor="middle">Weak if y is highly persistent</text>
<rect x="490" y="320" width="330" height="90" rx="6" fill="#eee8fa" stroke="#5522aa" stroke-width="1.5" />
<text x="655" y="342" font-size="13" font-weight="bold" text-anchor="middle">Blundell-Bond (System GMM)</text>
<text x="655" y="362" font-size="12" text-anchor="middle">Add level equation instrumented by</text>
<text x="655" y="378" font-size="12" text-anchor="middle">Δy_i,t-1 (requires mean stationarity)</text>
<text x="655" y="396" font-size="11" font-style="italic" text-anchor="middle">More efficient, robust to persistence</text>
<line x1="245" y1="410" x2="245" y2="440" stroke="#333" stroke-width="1.5" marker-end="url(#arrow)" />
<line x1="655" y1="410" x2="655" y2="440" stroke="#333" stroke-width="1.5" marker-end="url(#arrow)" />
<rect x="80" y="445" width="740" height="55" rx="6" fill="#f0f0f0" stroke="#555" stroke-width="1.5" />
<text x="450" y="468" font-size="13" text-anchor="middle" font-weight="bold">Two-Step GMM Estimation with Windmeijer-Corrected Standard Errors</text>
<text x="450" y="486" font-size="12" text-anchor="middle">Weighting matrix W = [Z'ΔεΔε'Z]⁻¹ (or collapsed instrument set to limit proliferation)</text>
<line x1="450" y1="500" x2="450" y2="530" stroke="#333" stroke-width="1.5" marker-end="url(#arrow)" />
<rect x="150" y="535" width="600" height="70" rx="6" fill="#fff5e6" stroke="#cc7700" stroke-width="1.5" />
<text x="450" y="557" font-size="13" font-weight="bold" text-anchor="middle">Specification Diagnostics</text>
<text x="450" y="575" font-size="12" text-anchor="middle">Hansen J-test · AR(1) [expect reject] · AR(2) [expect no reject]</text>
<text x="450" y="592" font-size="12" text-anchor="middle">Difference-in-Hansen (System GMM only)</text>
</svg>

### Software Implementation Notes

- **R**: `plm` package (`pgmm` function) supports both one-step/two-step, difference and system transformations, and collapsed instruments via `transformation = "ld"` and `collapse = TRUE`
- **Stata**: `xtabond` (difference GMM only), `xtabond2` (user-written, supports both difference and system GMM, collapsing, and Windmeijer correction)
- **Python**: `linearmodels` package provides `IVGMM` for general time series/cross-sectional GMM; dynamic panel GMM support is less mature than R/Stata equivalents as of general availability **[Unverified — check current package documentation for latest panel GMM support]**

### Practical Guidance on Model Selection

- Use **Difference GMM** when $T$ is small, instrument proliferation risk is low, and the dependent variable is not highly persistent
- Use **System GMM** when the series is highly persistent (autoregressive parameter near 1) and initial-condition mean-stationarity is plausible
- Always report both AR(2) and Hansen/Diff-in-Hansen tests; a specification that fails either should not be reported as the primary result
- Always collapse instruments or restrict lag depth when $T$ is moderate-to-large relative to $N$, and report the instrument count relative to $N$ as a robustness signal

**Next Steps**

- Continuously-Updated GMM (CUE) and its finite-sample properties relative to two-step GMM
- Weak identification-robust inference in GMM (Stock-Wright S-statistic, GMM-Anderson-Rubin)
- Nonlinear GMM and simulated method of moments (SMM) for models without closed-form moments
- Spatial and cross-sectional dependence in panel GMM (beyond the standard $N \to \infty$, fixed-$T$ asymptotics)
- Bias-corrected fixed effects estimators (Kiviet correction) as an alternative to GMM for dynamic panels
- Nickell bias derivation and its relationship to instrument validity conditions