## Girsanov's Theorem and Change of Measure

### Overview

Girsanov's theorem describes how the drift of a stochastic process transforms under an equivalent change of probability measure, while leaving the diffusion (volatility) term unchanged. It is the theoretical foundation for risk-neutral pricing: it justifies replacing the real-world drift $\mu$ with the risk-free rate $r$ when valuing derivatives, and it underlies virtually every measure change used in fixed income, FX, and equity derivatives modeling (forward measures, swap measures, quanto adjustments).

### Equivalent Probability Measures

Two measures $P$ and $Q$ on the same probability space are **equivalent** if they agree on which events have zero probability:

$$P(A) = 0 \iff Q(A) = 0 \quad \text{for all } A \in \mathcal{F}$$

**Key Points**

- Equivalence (not equality) is what permits a change of measure — both measures must agree on the set of "possible" outcomes, but can assign different probabilities to those outcomes
- The Radon-Nikodym derivative $\frac{dQ}{dP}$ exists precisely because $P$ and $Q$ are equivalent; it is the random variable that reweights probabilities from $P$ to $Q$

### The Radon-Nikodym Derivative Process

Define the Radon-Nikodym derivative restricted to information up to time $t$:

$$Z_t = \frac{dQ}{dP}\bigg|_{\mathcal{F}_t} = E^P\left[\frac{dQ}{dP} \,\middle|\, \mathcal{F}_t\right]$$

**Key Points**

- $Z_t$ is a $P$-martingale: $E^P[Z_t \mid \mathcal{F}_s] = Z_s$ for $s < t$
- $Z_t > 0$ almost surely (required for equivalence)
- $Z_0 = 1$ (both measures agree on trivial information)
- For any $\mathcal{F}_t$-measurable random variable $Y$: $E^Q[Y] = E^P[Y Z_t]$

### The Girsanov (Cameron-Martin-Girsanov) Theorem

**Statement:** Let $W_t^P$ be a standard Brownian motion under measure $P$, and let $\theta_t$ be an adapted process satisfying the Novikov condition (below). Define the exponential martingale:

$$Z_t = \exp\left(-\int_0^t \theta_s \, dW_s^P - \frac{1}{2}\int_0^t \theta_s^2 \, ds\right)$$

Define a new measure $Q$ by $\frac{dQ}{dP}\Big|_{\mathcal{F}_t} = Z_t$. Then under $Q$, the process

$$W_t^Q = W_t^P + \int_0^t \theta_s \, ds$$

is a standard Brownian motion.

Equivalently, expressed as a differential:

$$dW_t^P = dW_t^Q - \theta_t \, dt$$

**Key Points**

- $\theta_t$ is called the **market price of risk** (or Girsanov kernel) — it quantifies how much the drift shifts per unit of measure change
- The diffusion coefficient is invariant under the measure change — only drift transforms. This is a direct consequence of quadratic variation being a pathwise (measure-independent) property
- The theorem is stated for a single Brownian motion here but extends to multivariate settings with a vector $\theta_t$ and vector Brownian motion

### Novikov's Condition

For $Z_t$ to be a genuine martingale (not merely a local martingale), a sufficient condition is:

$$E^P\left[\exp\left(\frac{1}{2}\int_0^T \theta_s^2 \, ds\right)\right] < \infty$$

**Key Points**

- [Inference] Practitioners often verify this condition informally for standard models (e.g., constant or bounded $\theta_t$) rather than proving it rigorously each time, since bounded market-price-of-risk processes trivially satisfy Novikov's condition
- Failure of this condition can make $Z_t$ a strict local martingale, which invalidates the equivalence of measures and can produce spurious arbitrage-like behavior in poorly specified models — a known pathology in some stochastic volatility and bubble models

### Effect on an Ito Process

Consider a process under $P$:

$$dX_t = \mu_t \, dt + \sigma_t \, dW_t^P$$

Substituting $dW_t^P = dW_t^Q - \theta_t \, dt$:

$$dX_t = (\mu_t - \sigma_t \theta_t)\, dt + \sigma_t \, dW_t^Q$$

**Example**

If $\theta_t = \theta$ is constant and $\sigma_t = \sigma$ constant, the drift shifts from $\mu$ to $\mu - \sigma\theta$. Choosing $\theta = \frac{\mu - r}{\sigma}$ (the Sharpe ratio) transforms the drift exactly to the risk-free rate $r$ — this is precisely the mechanism behind risk-neutral valuation.

### Application: Black-Scholes Risk-Neutral Measure

Under the physical measure $P$:

$$dS_t = \mu S_t \, dt + \sigma S_t \, dW_t^P$$

Define $\theta = \frac{\mu - r}{\sigma}$ (market price of risk) and $Z_t = \exp\left(-\theta W_t^P - \frac{1}{2}\theta^2 t\right)$. Under the equivalent martingale measure $Q$ defined by $Z_t$:

$$dS_t = rS_t \, dt + \sigma S_t \, dW_t^Q$$

**Key Points**

- Under $Q$, the discounted stock price $\tilde{S}_t = e^{-rt}S_t$ is a martingale — this is the defining property of an **equivalent martingale measure (EMM)**
- The First Fundamental Theorem of Asset Pricing: absence of arbitrage is (essentially) equivalent to the existence of an EMM
- The Second Fundamental Theorem of Asset Pricing: market completeness corresponds to the EMM being unique
- Girsanov's theorem is what constructively produces this EMM starting from the physical-measure dynamics

### Forward Measure and Numeraire Changes

Girsanov's theorem generalizes beyond the money-market numeraire. Changing to a **T-forward measure** $Q^T$ (using the zero-coupon bond $P(t,T)$ as numeraire) simplifies pricing of interest-rate derivatives by removing the need to model the stochastic discount factor explicitly.

**Key Points**

- General numeraire change: if $N_t$ is a new numeraire, the Radon-Nikodym derivative is $\frac{dQ^N}{dQ} = \frac{N_t / N_0}{B_t / B_0}$ where $B_t$ is the original numeraire (e.g., money-market account)
- Under the T-forward measure, forward LIBOR/SOFR rates are martingales — this is the foundation of the LIBOR Market Model (LMM) / SOFR-based term rate models
- Girsanov's theorem provides the drift adjustment needed when switching between numeraires (e.g., moving from spot to forward measure in the derivation of the Black-76 formula)

### Multivariate Girsanov's Theorem

For a vector Brownian motion $\mathbf{W}_t^P = (W_t^{1,P}, \dots, W_t^{n,P})$ and vector kernel $\boldsymbol{\theta}_t = (\theta_t^1, \dots, \theta_t^n)$:

$$Z_t = \exp\left(-\int_0^t \boldsymbol{\theta}_s^\top \, d\mathbf{W}_s^P - \frac{1}{2}\int_0^t \|\boldsymbol{\theta}_s\|^2 \, ds\right)$$



$$d\mathbf{W}_t^Q = d\mathbf{W}_t^P + \boldsymbol{\theta}_t \, dt$$

This is essential for multi-asset and multi-factor models (e.g., correlated stocks, multi-currency derivatives, multi-factor short-rate models like Heath-Jarrow-Morton).

### Diagram: Change of Measure Mechanism

```mermaid
flowchart TD
    A[Physical measure P: dXt = mu dt + sigma dWt^P] --> B[Define market price of risk theta_t]
    B --> C[Construct Radon-Nikodym derivative Zt via stochastic exponential]
    C --> D{Novikov condition satisfied?}
    D -->|Yes| E[Zt is a true P-martingale, defines equivalent measure Q]
    D -->|No/Uncertain| F[Zt may be only a local martingale - risk of measure inconsistency]
    E --> G[Girsanov: dWt^P = dWt^Q - theta_t dt]
    G --> H[Drift transforms: mu becomes mu - sigma*theta under Q]
    H --> I[Choose theta = (mu - r)/sigma]
    I --> J[Discounted asset price is Q-martingale: risk-neutral pricing]
```

### Diagram: Measure Change and Drift Shift (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 280">
<text x="320" y="24" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a2e">Measure Change and Drift Shift (svg_diagram)</text>
<line x1="60" y1="240" x2="580" y2="240" stroke="#333" stroke-width="1.5" />
<text x="580" y="258" font-size="11" fill="#333">time</text>
<path d="M 60 200 C 150 150, 250 90, 340 60 S 500 30, 580 20" fill="none" stroke="#4338ca" stroke-width="2.5" />
<text x="420" y="45" font-size="12" fill="#4338ca" font-weight="bold">Path under P (drift = mu)</text>
<path d="M 60 200 C 150 180, 250 150, 340 145 S 500 130, 580 120" fill="none" stroke="#b45309" stroke-width="2.5" stroke-dasharray="6,4" />
<text x="420" y="145" font-size="12" fill="#b45309" font-weight="bold">Same path under Q (drift = r)</text>
<circle cx="60" cy="200" r="4" fill="#1a1a2e" />
<text x="30" y="205" font-size="11" fill="#1a1a2e">S0</text>
<rect x="60" y="60" width="260" height="26" fill="#eef2ff" stroke="#4338ca" opacity="0.85" />
<text x="70" y="78" font-size="11" fill="#1a1a2e">Zt reweights path probabilities,</text>
<rect x="60" y="90" width="330" height="20" fill="#eef2ff" stroke="none" opacity="0.85" />
<text x="70" y="105" font-size="11" fill="#1a1a2e">not the paths themselves (sigma unchanged)</text>
</svg>

### State-Price Density and the Stochastic Discount Factor

The Radon-Nikodym process $Z_t$ combined with the discount factor $e^{-rt}$ forms the **state-price density** (stochastic discount factor) $\xi_t = e^{-rt}Z_t$, satisfying:

$$\text{Price}_0 = E^P[\xi_T \cdot \text{Payoff}_T]$$

**Key Points**

- This connects Girsanov's theorem directly to the consumption-based asset pricing framework, where $\xi_t$ plays the role of the marginal utility of wealth (up to a constant)
- The equivalence between the martingale-measure approach and the state-price-density approach is a standard result in asset pricing theory (Cochrane, Duffie)

### Common Pitfalls

**Key Points**

- Assuming any drift-shifting transformation is valid — Girsanov's theorem requires equivalence of measures and (typically) Novikov's condition; not every $\theta_t$ produces a legitimate measure change
- Forgetting that the diffusion coefficient never changes under Girsanov — only drift terms transform. Errors often arise from incorrectly altering $\sigma$ when switching measures
- Confusing the market price of risk $\theta_t$ with the risk premium $\mu - r$ directly, rather than the normalized ratio $\theta_t = \frac{\mu - r}{\sigma}$
- In models with unbounded or highly explosive $\theta_t$ (e.g., certain stochastic volatility specifications), the martingale property of $Z_t$ can fail; this is a genuine modeling subtlety, not a mere technicality — [Unverified] the specific threshold at which failure occurs depends on the model's parameter regime and is typically checked case by case in the literature

### Conclusion

Girsanov's theorem is the formal machinery that makes risk-neutral pricing rigorous: it shows precisely how and why a drift can be "removed" or shifted by reweighting probabilities via an equivalent martingale measure, while preserving the volatility structure of the underlying process. Every application of risk-neutral valuation — Black-Scholes, interest-rate models, forward and swap measure techniques — rests on a specific instance of this theorem.

**Related Topics**

- First and Second Fundamental Theorems of Asset Pricing
- Equivalent martingale measures and market completeness
- Numeraire changes and the forward measure (T-forward, swap measure)
- Feynman-Kac theorem and PDE-martingale duality
- LIBOR Market Model / SOFR term rate models
- Stochastic discount factors and consumption-based asset pricing
- Local martingales vs true martingales (Novikov's condition edge cases)
- Heath-Jarrow-Morton framework for forward rate dynamics