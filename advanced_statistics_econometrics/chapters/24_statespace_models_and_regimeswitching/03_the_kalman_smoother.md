## The Kalman Smoother

### Definition and Conceptual Foundation

The Kalman smoother computes the optimal estimate of a latent state vector at each time point $t$ using **all** available observations in the sample, $y_1, \dots, y_T$, including observations that occur after $t$. This contrasts directly with the Kalman filter, which produces $a_{t|t}$ using only information available up to time $t$. By exploiting future information, smoothed estimates $a_{t|T}$ are generally more precise (lower estimation variance) than the corresponding filtered estimates $a_{t|t}$, at the cost of not being available in real time — smoothing is inherently a retrospective procedure applied after the full sample has been observed.

### Relationship to the Filter

**Key Points**

- The Kalman filter's forward pass produces the sequence of filtered means and covariances $\{a_{t|t}, P_{t|t}\}_{t=1}^{T}$ and one-step-ahead predicted quantities $\{a_{t|t-1}, P_{t|t-1}\}_{t=1}^{T}$; these are the necessary inputs to any smoothing algorithm — the smoother is always run **after** a complete forward filtering pass, never independently of it.
- Three distinct state estimation problems arise naturally from a state-space model, distinguished by the information set used: **filtering** ($a_{t|t}$, using data through $t$), **prediction** ($a_{t+h|t}$ for $h\geq1$, forecasting beyond the observed sample), and **smoothing** ($a_{t|T}$, using the entire sample). Smoothing is strictly an in-sample, retrospective concept; it is not a forecasting tool.

### The Fixed-Interval Smoother (Rauch-Tung-Striebel Algorithm)

The most commonly used smoothing algorithm, applied via a **backward** recursion after the forward filtering pass is complete, moving from $t=T-1$ down to $t=1$:

$$J_t = P_{t|t} T_t' P_{t+1|t}^{-1}$$



$$a_{t|T} = a_{t|t} + J_t\left(a_{t+1|T} - a_{t+1|t}\right)$$



$$P_{t|T} = P_{t|t} + J_t\left(P_{t+1|T} - P_{t+1|t}\right)J_t'$$

initialized at $t=T$ with $a_{T|T}$ and $P_{T|T}$ (the final filtered values, which trivially equal the smoothed values at the last time point, since there is no additional future information beyond $T$).

**Key Points**

- $J_t$ is often called the smoothing gain, analogous in role to the Kalman gain $K_t$ in the forward filter, but determining how much the smoothed estimate at $t$ is adjusted based on the discrepancy between the smoothed and filtered/predicted state at $t+1$.
- The recursion moves **backward** in time: it starts from the final filtered estimate (which needs no correction, since there is no future data beyond the last observation) and works back toward $t=1$, at each step blending the filtered estimate at $t$ with information "propagated backward" from the smoothed estimate at $t+1$.
- $P_{t|T} \leq P_{t|t}$ in the positive semi-definite ordering sense (smoothed covariance is generally smaller/no larger than filtered covariance) at every interior time point, formalizing the intuition that smoothing weakly improves precision by using strictly more information.

### Why Smoothed Estimates Are More Precise

**Key Points**

- The filtered estimate $a_{t|t}$ at an interior time point uses only past and current information, discarding the informative signal contained in observations $y_{t+1}, \dots, y_T$ about the state at time $t$ (since the state process is serially dependent, future observations carry information about earlier states through the transition equation's persistence).
- This precision gain is generally most pronounced for time points in the **middle** of the sample (which benefit from a long history of both past and future data) and least pronounced near the **end** of the sample (where filtered and smoothed estimates converge, since there is little or no future information beyond the very last observations) — this produces the characteristic pattern where smoothed and filtered series nearly coincide near the sample's endpoint but diverge more in the interior.

### Alternative Smoothing Algorithms

**Fixed-point smoothing**: Computes $a_{t|\tau}$ for a single, fixed time point $t$ as $\tau$ increases (i.e., as more future data becomes available), useful when interest centers on refining the estimate at one specific historical date as new data arrives, rather than smoothing the entire sample path.

**Fixed-lag smoothing**: Computes $a_{t|t+L}$ for a fixed lag $L$, producing a smoothed estimate that incorporates a bounded window of future information — a practical compromise between full-sample smoothing (which requires waiting for the entire dataset) and pure filtering, useful in near-real-time applications where a short delay is acceptable in exchange for improved precision.

**Disturbance smoothing**: A related but distinct algorithm (also due to de Jong, 1988, 1989, and Koopman, 1993) that smooths the underlying **disturbance terms** ($\varepsilon_t$, $\eta_t$) rather than the state itself, useful for diagnostic checking and for certain simulation-based estimation approaches (e.g., simulation smoothing for Bayesian state-space estimation).

### Practical Application Workflow

**Example**

Step 1: Estimate the state-space model's unknown parameters via maximum likelihood, using the Kalman filter's prediction error decomposition (as in standard state-space estimation practice).

Step 2: With the maximum-likelihood parameter estimates fixed, run the Kalman filter forward through the entire sample, storing all filtered $\{a_{t|t}, P_{t|t}\}$ and predicted $\{a_{t|t-1}, P_{t|t-1}\}$ quantities.

Step 3: Initialize the backward smoothing recursion at $t=T$ with $a_{T|T}$, $P_{T|T}$.

Step 4: Iterate the Rauch-Tung-Striebel backward recursion from $t=T-1$ down to $t=1$, computing $J_t$, $a_{t|T}$, and $P_{t|T}$ at each step.

Step 5: Report and/or plot the smoothed state path $\{a_{t|T}\}_{t=1}^{T}$ (and associated confidence bands from $P_{t|T}$) as the final retrospective estimate of the latent process — e.g., a smoothed trend/cycle decomposition of a macroeconomic series for historical analysis and publication.

**Output**

For a local linear trend model applied to a macroeconomic series, the smoothed trend component typically appears visibly less erratic than the filtered trend, since revisions from later data have been incorporated throughout the sample; smoothed confidence intervals around the trend are correspondingly narrower than filtered confidence intervals at most interior points, with the two converging near the most recent observations. [Inference: the specific magnitude of precision improvement depends on the estimated signal-to-noise ratios in the fitted model and is series-specific.]

### Applications of Smoothing

**Key Points**

- **Historical decomposition and structural analysis**: Producing a final, published decomposition of a time series into trend, cycle, seasonal, and irregular components (as in structural time series models) is a canonical smoothing application, since the goal is the best possible retrospective characterization of history, not real-time signal extraction.
- **Business cycle dating and output gap estimation**: Smoothed estimates of an unobserved cyclical/output-gap component are standard in central bank and academic macroeconomic analysis, since these applications are inherently retrospective (assessing where the economy has been) rather than real-time.
- **EM algorithm for state-space parameter estimation**: The Expectation-Maximization (EM) algorithm, an alternative to direct numerical maximization of the prediction-error-decomposition likelihood, requires smoothed state estimates (and smoothed cross-moments) as an intermediate step in its E-step, making the smoother a computational building block for this class of estimation methods as well.
- **Simulation smoothing for Bayesian estimation**: MCMC-based Bayesian estimation of state-space models (e.g., stochastic volatility, time-varying parameter models) typically requires drawing simulated state paths from their conditional (smoothed) distribution given the data and current parameter draw — the "simulation smoother" (de Jong and Shephard, 1995; Durbin and Koopman, 2002) is the standard algorithm for this.

### Common Pitfalls

- **Using smoothed estimates in real-time or pseudo-out-of-sample contexts**: Smoothed values incorporate future information not actually available at the historical point in question; using them for forecast evaluation or any application requiring genuinely real-time information sets introduces look-ahead bias and overstates apparent predictive accuracy.
- **Confusing filtering, prediction, and smoothing terminology**: These are distinct concepts differentiated purely by information set ($t$, $t+h$ for $h>0$, and $T$ respectively); loosely using "filtered" and "smoothed" interchangeably in reporting can materially mislead readers about what information the reported estimates actually reflect.
- **Applying the standard fixed-interval smoother recursion incorrectly at boundary conditions**: Errors in properly initializing $a_{T|T}$, $P_{T|T}$ or in correctly propagating the backward recursion (e.g., off-by-one indexing errors between $t$ and $t+1$ quantities) are a common implementation pitfall when coding the algorithm manually rather than using established software.
- **Overlooking the smoother's dependence on correctly estimated parameters**: Since smoothing is always conditional on a fixed set of model parameters (typically the maximum likelihood estimates), the reported smoothed state uncertainty ($P_{t|T}$) generally does **not** account for parameter estimation uncertainty itself, understating total uncertainty in the final smoothed estimates unless additional correction (e.g., a fully Bayesian treatment) is applied.

### Filtering vs. Smoothing Information Set Diagram

```mermaid
flowchart TD
    subgraph filter_vs_smoother Filtering vs Smoothing Information Sets (svg_diagram)
    A["Full sample: y_1, y_2, ..., y_T"] --> B["Forward Kalman filter pass"]
    B --> C["Filtered estimates a_t given t: use info through time t only"]
    B --> D["Store predicted and filtered means, covariances at every t"]
    D --> E["Backward RTS smoother recursion, from t=T-1 down to t=1"]
    E --> F["Smoothing gain J_t = P_t given t times T_t' times P_t+1 given t inverse"]
    F --> G["Smoothed estimate a_t given T: uses full sample info, all T periods"]
    C --> H["Appropriate for: real-time signal extraction, forecast evaluation"]
    G --> I["Appropriate for: historical decomposition, output gap, EM algorithm E-step"]
    end
```

### Software Implementation Notes

- **R**: `KFAS::KFS()` (returns both filtered and smoothed output in one call), `dlm::dlmSmooth()`.
- **Python**: `statsmodels.tsa.statespace` models provide `.smooth()` methods (e.g., `UnobservedComponents().smooth()`) alongside `.filter()`, returning smoothed state and disturbance estimates.
- **MATLAB**: Econometrics Toolbox `ssm` objects' `smooth()` method, run after (or combined with) the corresponding `filter()` call.

[Unverified: exact function/method names and default output conventions (e.g., whether smoothed disturbances are returned alongside smoothed states by default) vary by package and version; verify against current documentation before implementation.]

**Related Topics**

- The Kalman filter
- State-space representation of time series
- Regime-switching and Markov-switching models
- EM algorithm for state-space parameter estimation
- Simulation smoothing and Bayesian state-space estimation
- Output gap and business cycle decomposition
- Dynamic factor models