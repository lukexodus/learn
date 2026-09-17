## Combining Duration and Convexity for Price Estimation

### Overview

Combining duration and convexity produces a second-order Taylor series approximation of a bond's price change in response to a change in yield. Duration alone provides a first-order (linear) estimate; adding the convexity term corrects for the curvature of the true price-yield relationship, substantially improving accuracy — particularly for larger yield changes. This combined approach is the standard practical formula used across fixed income risk management for estimating price impacts without requiring a full cash-flow revaluation for every scenario.

### The Combined Formula

Starting from the second-order Taylor expansion of price with respect to yield:

$$\Delta P \approx \left(\frac{dP}{dy}\right)\Delta y + \frac{1}{2}\left(\frac{d^2P}{dy^2}\right)(\Delta y)^2$$

Dividing by $P_0$ and substituting the standard duration and convexity definitions:

$$\frac{\Delta P}{P_0} \approx \left[-D_{mod} \times \Delta y\right] + \left[\frac{1}{2} \times C \times (\Delta y)^2\right]$$

Or, solved explicitly for the estimated new price:

$$P_{new} \approx P_0 \left[1 - D_{mod} \times \Delta y + \frac{1}{2} \times C \times (\Delta y)^2\right]$$

**Component roles**:

- The duration term, $-D_{mod} \times \Delta y$, captures the direction and dominant magnitude of the price change — it is the linear, first-order effect.
- The convexity term, $\frac{1}{2} \times C \times (\Delta y)^2$, is always non-negative when $C > 0$ (regardless of the sign of $\Delta y$) and corrects the linear estimate toward the true curved price-yield relationship.

### Step-by-Step Worked Example

Consider a bond with the following characteristics:

- Current price: $P_0 = 98.50$
- Modified duration: $D_{mod} = 6.8$
- Convexity: $C = 55$
- Yield change: $\Delta y = +0.0150$ (a 150 bp increase)

**Step 1 — Compute the duration-only (linear) effect**:

$$\text{Duration effect} = -D_{mod} \times \Delta y = -6.8 \times 0.0150 = -0.1020 \text{ (i.e., } -10.20\%\text{)}$$

**Step 2 — Compute the convexity correction**:

$$\text{Convexity effect} = \frac{1}{2} \times C \times (\Delta y)^2 = \frac{1}{2} \times 55 \times (0.0150)^2 = \frac{1}{2} \times 55 \times 0.000225 = 0.0061875 \text{ (i.e., } +0.619\%\text{)}$$

**Step 3 — Combine both effects**:

$$\frac{\Delta P}{P_0} \approx -0.1020 + 0.0061875 = -0.0958125 \text{ (i.e., } -9.581\%\text{)}$$

**Step 4 — Apply to the current price**:

$$\Delta P = -0.0958125 \times 98.50 = -9.4375$$



$$P_{new} = 98.50 - 9.4375 = 89.0625$$

**Comparison**:

| Method | Estimated $\Delta P$ | Estimated $P_{new}$ |
| --- | --- | --- |
| Duration only | $-0.1020 \times 98.50 = -10.047$ | 88.453 |
| Duration + Convexity | $-9.4375$ | 89.0625 |

The convexity-adjusted estimate predicts a smaller loss (89.0625 vs. 88.453) — a difference of roughly 0.61 points, or about 0.7% of the bond's price, purely attributable to the second-order correction. For a 150 bp move, this is a non-trivial refinement; the gap would be roughly four times smaller for a 75 bp move and roughly four times larger for a 300 bp move, since the convexity term scales with $(\Delta y)^2$.

### Visual: Decomposing the Total Price Estimate (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 380">
<text x="350" y="25" text-anchor="middle" font-size="16" font-weight="bold" fill="#1a1a2e">Duration + Convexity Price Estimate Decomposition (svg_diagram)</text>

<line x1="90" y1="330" x2="630" y2="330" stroke="#333" stroke-width="1.5" />
<line x1="90" y1="330" x2="90" y2="60" stroke="#333" stroke-width="1.5" />
<text x="360" y="360" text-anchor="middle" font-size="12" fill="#333">Yield Change (Δy)</text>
<text x="45" y="195" text-anchor="middle" font-size="12" fill="#333" transform="rotate(-90 45 195)">Price</text>

<path d="M 130 300 Q 330 120 590 90" stroke="#4472C4" stroke-width="3" fill="none" />
<text x="480" y="100" font-size="11" fill="#2a4a8a">True price-yield curve</text>

<line x1="150" y1="270" x2="580" y2="140" stroke="#ED7D31" stroke-width="2" stroke-dasharray="5,4" />
<text x="480" y="160" font-size="11" fill="#c65a11">Duration-only estimate</text>

<path d="M 150 270 Q 360 175 580 118" stroke="#548235" stroke-width="2.5" stroke-dasharray="2,2" />
<text x="440" y="205" font-size="11" fill="#375623">Duration + Convexity estimate</text>

<circle cx="360" cy="192" r="5" fill="#1a1a2e" />
<text x="368" y="185" font-size="11">P0</text>

<line x1="500" y1="60" x2="500" y2="330" stroke="#999" stroke-width="1" stroke-dasharray="3,3" />
<text x="505" y="345" font-size="11" fill="#666">Evaluation yield</text>

<circle cx="500" cy="128" r="4" fill="#4472C4" />
<circle cx="500" cy="151" r="4" fill="#548235" />
<circle cx="500" cy="163" r="4" fill="#ED7D31" />
<text x="515" y="132" font-size="10" fill="#2a4a8a">True price</text>
<text x="515" y="155" font-size="10" fill="#375623">Duration+Convexity (close)</text>
<text x="515" y="178" font-size="10" fill="#c65a11">Duration-only (further off)</text>
</svg>

The diagram shows the progression of approximation quality: the duration-only tangent line diverges from the true curve most rapidly, the duration-plus-convexity parabola tracks the true curve far more closely across a wider range, and both approximations coincide exactly with the true price only at the original point of tangency ($P_0$, $\Delta y = 0$).

### Accuracy Characteristics of the Combined Estimate

- **Exact at $\Delta y = 0$**: Both the linear and quadratic terms vanish, and the estimate trivially equals $P_0$.
- **High accuracy for small to moderate yield changes**: For yield shifts in the range of roughly 25–150 bp, the duration-plus-convexity estimate is typically very close to the true repriced value for option-free bonds, since third-order and higher terms remain small.
- **Degrading accuracy for very large yield changes**: For extreme moves (300+ bp), even the second-order approximation can diverge meaningfully from the true price, because higher-order terms (third derivative and beyond) become non-negligible. In such cases, full repricing via discounted cash flow or an option-pricing model is preferred over the Taylor approximation.
- **Reduced reliability for negatively convex instruments**: For callable bonds or MBS, the convexity input itself must be the *effective* (option-adjusted) convexity rather than the analytical closed-form value, and even effective convexity is only a local approximation — if the yield change is large enough to move the instrument across a regime boundary (e.g., from call-irrelevant to call-imminent), a single convexity value computed at the starting yield may not represent the curve's behavior accurately across the entire range of the shock.

### Practical Application: Portfolio-Level Estimation

Duration and convexity combine additively (in dollar or weighted terms) across a portfolio of bonds, making the combined formula highly practical for estimating aggregate portfolio price sensitivity without repricing every individual holding:

$$\frac{\Delta P_{portfolio}}{P_{portfolio}} \approx -D_{mod,portfolio} \times \Delta y + \frac{1}{2} \times C_{portfolio} \times (\Delta y)^2$$

where $D_{mod,portfolio}$ and $C_{portfolio}$ are the market-value-weighted averages of the individual bonds' modified durations and convexities, respectively:

$$D_{mod,portfolio} = \sum_{i} w_i \times D_{mod,i}, \qquad C_{portfolio} = \sum_{i} w_i \times C_i$$

with $w_i$ representing each bond's market-value weight in the portfolio. This weighted aggregation is a standard technique for rapid, top-down portfolio-level stress testing (e.g., estimating the impact of a 100 bp parallel shift on total portfolio value) without requiring a full instrument-by-instrument revaluation engine.

### Common Pitfalls

- **Sign errors in the convexity term**: Because the convexity term is added regardless of the direction of $\Delta y$ (due to the squared term), a common implementation error is subtracting the convexity contribution when $\Delta y$ is negative — the term must always be added for $C > 0$.
- **Using the wrong duration measure**: The formula requires *modified duration* (or effective duration for option-embedded instruments), not Macaulay duration, which must first be converted via $D_{mod} = \frac{D_{Mac}}{1 + y/m}$ before use in this framework.
- **Mismatched convexity convention**: As noted under convexity calculation methods, some systems define convexity with the $\frac{1}{2}$ factor already embedded in $C$ itself, while others expect it applied separately in the price estimation formula. Using a convexity figure from one convention within a formula built for the other convention will produce a doubled or halved convexity correction.
- **Applying analytical convexity to option-embedded bonds**: As with convexity calculation generally, the combined price estimation formula requires effective duration and effective convexity — not their closed-form analytical counterparts — for any instrument where cash flows can change in response to yield movements.
- **Treating the estimate as exact for large shocks**: The combined formula remains an approximation; for scenario analysis involving very large rate shocks or portfolios with material optionality, full repricing is the more reliable (if more computationally expensive) approach. [Inference] The practical threshold at which the approximation error becomes material for a given portfolio depends on the specific convexity profile and shock size, and is generally best confirmed empirically by comparing the Taylor estimate against full repricing for a representative range of scenarios.

**Related Topics:**

- Convexity Concept and Geometric Intuition
- Calculating Bond Convexity (Analytical vs. Effective Methods)
- Positive versus Negative Convexity
- Third-Order (Skew) Corrections Beyond the Duration-Convexity Approximation
- Portfolio-Level Duration and Convexity Aggregation Techniques
- Scenario Analysis and Stress Testing Using Taylor Series Approximations
- Full Repricing vs. Analytical Approximation Trade-offs in Risk Systems