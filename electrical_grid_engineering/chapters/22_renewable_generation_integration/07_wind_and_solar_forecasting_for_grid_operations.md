## Wind and Solar Forecasting for Grid Operations


### Overview

Wind and solar forecasting provides system operators and market participants with predicted power output from variable renewable generation across multiple time horizons, enabling unit commitment, economic dispatch, reserve procurement, and grid stability planning in the presence of inherently uncertain, weather-driven generation. Unlike conventional dispatchable generation, wind and solar output cannot be scheduled to a desired value — forecasting exists to characterize and reduce the *uncertainty* system operators must otherwise manage through reserves and operational margin, rather than to control the resource itself.

### Why Forecasting Matters for Grid Operations

As renewable penetration increases, forecast accuracy directly affects several operational and economic outcomes:

- **Reserve requirements**: system operators must hold sufficient operating reserves to cover forecast error, so improved forecast accuracy allows reserves to be sized more efficiently rather than conservatively oversized
- **Unit commitment**: day-ahead and multi-day forecasts inform which conventional generating units are committed (started up) to cover expected net load (load minus renewable output) across the coming operating day(s)
- **Economic dispatch and market clearing**: short-term forecasts feed into real-time and day-ahead electricity market clearing processes in many restructured markets
- **Curtailment and congestion management**: forecasts help operators anticipate when renewable output may exceed transmission capacity or system flexibility, informing proactive curtailment or transmission switching decisions
- **Ramp management**: forecasting significant upward or downward ramps in aggregate renewable output (e.g., a large solar fleet's output dropping rapidly at sunset, or a wind ramp associated with a frontal passage) allows operators to pre-position conventional generation to cover the transition

### Forecasting Time Horizons

Different operational decisions require forecasts at different time horizons, each typically served by different modeling approaches:

| Horizon | Typical Range | Primary Use | Dominant Modeling Approach |
| --- | --- | --- | --- |
| Very short-term (nowcasting) | Minutes to ~1 hour | Real-time balancing, ramp alerts | Statistical/persistence models, satellite/sky imagery |
| Short-term | 1-6 hours | Intra-day dispatch, reserve adjustment | Numerical weather prediction (NWP) + statistical correction |
| Day-ahead | 1-3 days | Unit commitment, day-ahead market clearing | NWP-based, often ensemble methods |
| Medium-term | 3-10 days | Maintenance scheduling, extended outlook | Ensemble NWP |
| Long-term | Weeks to seasonal | Resource/capacity planning | Climatological/statistical, seasonal NWP ensembles |

```mermaid
flowchart LR
    A[Nowcasting: minutes-1hr] --> B[Short-term: 1-6hr]
    B --> C[Day-ahead: 1-3 days]
    C --> D[Medium-term: 3-10 days]
    D --> E[Long-term: weeks-seasonal]
    A -.->|Real-time balancing| OPS[Grid Operations]
    B -.->|Intra-day dispatch| OPS
    C -.->|Unit commitment| OPS
    D -.->|Maintenance planning| OPS
    E -.->|Resource planning| OPS
```

### Wind Forecasting Methodology

#### Numerical Weather Prediction (NWP) Foundation

Wind power forecasting fundamentally depends on forecasting wind speed and direction at turbine hub height, derived from NWP models that solve atmospheric physics equations (fluid dynamics, thermodynamics) over a discretized three-dimensional grid covering the region of interest.

- **Global models**: broader coverage, coarser spatial resolution (commonly tens of kilometers), providing boundary conditions for finer-resolution regional models
- **Mesoscale/regional models**: finer spatial resolution (commonly a few kilometers or less), better capturing local terrain effects, coastal transitions, and other features significantly affecting wind resource at turbine hub height — particularly important given that most global model resolutions are too coarse to resolve individual wind farm terrain characteristics directly

#### Power Curve Conversion

Forecasted wind speed must be converted to forecasted power output via the turbine's power curve — a nonlinear relationship between wind speed and electrical output specific to each turbine model, complicated in practice by:

- **Wake effects**: turbines within a wind farm partially shadow downwind turbines' effective wind speed, requiring wake modeling to translate a single forecasted ambient wind speed into farm-aggregate power output
- **Power curve uncertainty**: actual turbine power curves can deviate from manufacturer nameplate curves due to air density variation, blade icing/soiling, and turbine control system behavior, introducing additional forecast error beyond pure wind speed forecast error

$$P_{turbine} = f_{power curve}(V_{hub height}, \rho_{air})$$

where $\rho_{air}$ (air density) affects the power curve since aerodynamic power extraction scales with air density, requiring density correction particularly relevant at high-altitude or significantly temperature-varying sites.

#### Statistical/Machine Learning Post-Processing

Raw NWP-derived power forecasts are commonly improved through statistical post-processing techniques that learn systematic biases and correction patterns from historical forecast-versus-actual performance data at the specific site:

- **Model Output Statistics (MOS)**: statistical relationships correcting known NWP model biases based on historical performance
- **Machine learning approaches**: increasingly common, including gradient boosting methods and neural network architectures, trained on historical NWP output alongside actual measured power output to learn site-specific correction patterns
- **Ensemble forecasting**: combining multiple NWP model runs (either different models, or the same model with perturbed initial conditions) to characterize forecast uncertainty explicitly, producing probabilistic forecasts (e.g., a forecast power range with associated confidence levels) rather than a single deterministic value
- [Inference] Machine learning-based post-processing methods have become increasingly prevalent in commercial wind and solar forecasting services over the past decade, reflecting broader industry trends in applying data-driven methods to time-series prediction problems; however, the specific algorithms, architectures, and relative performance advantages are largely proprietary to individual forecasting service providers and academic research continues to actively compare different approaches, so no single method should be assumed universally superior across all sites and conditions.

### Solar Forecasting Methodology

#### Irradiance Forecasting as the Core Input

Analogous to wind speed forecasting for wind power, solar power forecasting fundamentally depends on forecasting **irradiance** (the solar power incident on a surface, typically Global Horizontal Irradiance, GHI, and/or Plane-of-Array irradiance accounting for panel tilt) at the specific plant location.

**Key irradiance forecasting approaches by horizon:**

- **Sky imagery / ground-based cameras**: for very short-term (minutes) nowcasting, cameras tracking cloud position and motion provide localized, high-temporal-resolution cloud shading predictions — particularly valuable for detecting rapidly moving cumulus cloud fields that can cause sharp, localized irradiance drops not well captured by coarser NWP models
- **Satellite-derived irradiance and cloud motion vectors**: for short-term forecasting (up to a few hours), satellite imagery-derived cloud motion is extrapolated forward to predict near-term cloud cover and resulting irradiance impact over a broader area than ground-based cameras can cover
- **NWP-based irradiance forecasting**: for day-ahead and longer horizons, NWP models' cloud cover and atmospheric transmission predictions are converted to irradiance forecasts, similar in structural approach to wind speed-to-power conversion

#### Clear-Sky Model as a Normalization Reference

Solar forecasting commonly uses a **clear-sky model** — a calculation of the theoretical maximum irradiance achievable at a given location, time, and date under cloudless conditions (a deterministic astronomical/atmospheric calculation, not itself a forecast) — as a normalization reference. Forecasting then focuses on predicting the **clear-sky index** (ratio of actual-to-clear-sky irradiance), which isolates the cloud-cover-driven variability that is the primary forecasting challenge, from the fully predictable astronomical solar geometry component.

$$k_t = \frac{GHI_{actual}}{GHI_{clear-sky}}$$

where $k_t$ is the clear-sky index, bounded between near-zero (heavy overcast) and slightly above 1 (some cloud-enhancement effects can briefly exceed clear-sky irradiance under specific partial-cloud conditions).

#### PV System Model Conversion

Forecasted irradiance (and forecasted ambient temperature, since PV module efficiency decreases with rising cell temperature) must be converted to forecasted AC power output via a PV system performance model, accounting for:

- Module temperature coefficient effects on efficiency
- Inverter efficiency curve and any clipping (DC/AC ratio oversizing causing inverter-limited output during high-irradiance periods)
- System losses (soiling, wiring, availability/outage assumptions)
- **Key Points**
  - Solar forecasting is generally considered to have a more predictable underlying deterministic component (solar geometry) than wind forecasting, but the cloud-cover-driven variability component can be highly localized and rapidly changing, particularly challenging for very short-term forecasting of individual sites or small-area distributed PV fleets
  - Distributed (rooftop) PV forecasting presents additional challenges relative to utility-scale plant forecasting, since aggregate distributed PV output must often be estimated indirectly (as a component embedded within net load measurements at the distribution level) rather than directly metered at each individual site, complicating both forecasting and the broader task of net load forecasting for system operators

### Forecast Aggregation and Smoothing Effects

A single wind or solar plant's forecast error is generally larger (as a percentage of capacity) than the aggregate forecast error across many geographically dispersed plants, because individual plant-level forecast errors are not perfectly correlated across a region — a phenomenon sometimes referred to as the **smoothing effect** or **geographic diversity benefit**.

- **Key Points**
  - System operators generally care most about aggregate (system-wide or balancing-area-wide) renewable forecast accuracy for reserve-sizing and unit commitment purposes, rather than individual plant-level forecast accuracy, since it is aggregate net load that must be balanced
  - The degree of smoothing benefit depends on the geographic dispersion of the renewable fleet and the spatial correlation scale of the underlying weather phenomena (e.g., a widespread frontal weather system affecting wind forecast errors similarly across a large region provides less smoothing benefit than more spatially localized convective cloud cover affecting solar forecast errors)

### Probabilistic Forecasting and Uncertainty Quantification

Because deterministic (single-value) forecasts inherently omit information about forecast confidence, many system operators and forecasting services increasingly emphasize **probabilistic forecasting**, providing a full predicted probability distribution (or a set of specified percentile values, e.g., 10th/50th/90th percentile) rather than a single expected value.

- **Key Points**
  - Probabilistic forecasts allow system operators to make risk-informed reserve and commitment decisions — e.g., committing sufficient reserves to cover a specified percentile of potential forecast error rather than only the median expected outcome
  - Ensemble NWP methods (running multiple perturbed simulations) are a common technical foundation for generating probabilistic renewable power forecasts, since the spread across ensemble members provides a direct measure of forecast uncertainty at a given horizon
  - Forecast accuracy is commonly evaluated using metrics such as Mean Absolute Error (MAE), Root Mean Square Error (RMSE), and for probabilistic forecasts, metrics like the Continuous Ranked Probability Score (CRPS) that assess the full predicted distribution's quality rather than only a point forecast

### Solar Forecast Horizon and Technique Applicability (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 300" font-family="sans-serif">
<text x="340" y="24" text-anchor="middle" font-size="16" font-weight="bold">Solar Forecasting Technique by Horizon (svg_diagram)</text>
<line x1="60" y1="200" x2="620" y2="200" stroke="#333" stroke-width="2" />
<text x="60" y="220" font-size="10">0 min</text>
<text x="220" y="220" font-size="10">30 min</text>
<text x="380" y="220" font-size="10">6 hr</text>
<text x="580" y="220" font-size="10">Day-ahead+</text>
<rect x="60" y="150" width="140" height="35" fill="#f0d6d6" stroke="#333" stroke-width="1.5" />
<text x="130" y="172" text-anchor="middle" font-size="10">Sky imagery / cameras</text>
<rect x="200" y="150" width="180" height="35" fill="#d6e4f0" stroke="#333" stroke-width="1.5" />
<text x="290" y="172" text-anchor="middle" font-size="10">Satellite cloud motion</text>
<rect x="380" y="150" width="240" height="35" fill="#e0d6f0" stroke="#333" stroke-width="1.5" />
<text x="500" y="172" text-anchor="middle" font-size="10">NWP-based irradiance forecast</text>
<rect x="60" y="100" width="560" height="30" fill="#d6f0e0" stroke="#333" stroke-width="1.5" />
<text x="340" y="120" text-anchor="middle" font-size="10">Statistical/ML post-processing and ensemble methods applied across all horizons</text>
</svg>

### Practical Example: Day-Ahead Unit Commitment Using Wind and Solar Forecasts

Scenario: A system operator preparing the next operating day's unit commitment schedule receives probabilistic wind and solar forecasts for its balancing area.

1. Forecasting service delivers hourly median (50th percentile) forecasts alongside 10th and 90th percentile bounds for both wind and solar fleet aggregate output across the coming 24-hour period
2. System operator calculates forecasted net load (total load forecast minus median renewable forecast) for each hour of the operating day
3. Unit commitment software determines which conventional generating units must be started to meet forecasted net load plus required reserve margin, with reserve margin sized in part based on the forecast uncertainty band (wider 10th-90th percentile spread implies greater reserve requirement for that hour)
4. Hours with forecasted rapid renewable output transitions (e.g., a sharp evening solar ramp-down coinciding with rising evening load) are flagged for additional operational attention, potentially requiring specific fast-start or flexible generation resources to be committed to cover the transition
5. As the operating day approaches and updated short-term forecasts become available, the operator refines dispatch decisions intra-day, with the day-ahead unit commitment decisions (which units are online) generally fixed while economic dispatch (how much each online unit produces) continues to adjust based on the latest forecast information
6. Post-event, actual renewable output is compared against the day-ahead forecast to evaluate forecast performance and inform ongoing forecast service evaluation/improvement

**Conclusion**

Wind and solar forecasting transforms inherently uncertain, weather-driven renewable generation into structured, actionable information for grid operations across time horizons ranging from minutes to seasons. While the underlying meteorological science (NWP models, satellite/sky imagery, clear-sky irradiance modeling) provides the foundation, the conversion from forecasted weather variables to forecasted power output — through power curves, wake modeling, and PV system performance models — introduces its own layer of engineering modeling challenges, further refined through statistical and machine learning post-processing calibrated to site-specific historical performance. As renewable penetration grows, the industry emphasis has shifted from simple deterministic point forecasts toward probabilistic forecasting that explicitly quantifies uncertainty, enabling system operators to make more risk-informed reserve and commitment decisions rather than defaulting to conservative, inefficient operational margins.

**Related Topics**

- Grid codes for renewable interconnection (curtailment and active power control capability)
- Battery energy storage systems and their role in managing forecast error/ramp events
- Unit commitment and economic dispatch in systems with high renewable penetration
- Numerical weather prediction (NWP) model fundamentals
- Ancillary services markets and reserve requirement determination
- Net load forecasting and the distributed PV visibility challenge
- Wind farm wake modeling and micrositing considerations
- Curtailment strategies and transmission congestion management for variable generation