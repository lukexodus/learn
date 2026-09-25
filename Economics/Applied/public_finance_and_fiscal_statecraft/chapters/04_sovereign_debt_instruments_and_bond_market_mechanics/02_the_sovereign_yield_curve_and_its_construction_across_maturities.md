## The Sovereign Yield Curve and Its Construction Across Maturities

### Definition and Core Function

A **sovereign yield curve** is the set of yields-to-maturity on a state's own-currency government securities, plotted against their respective tenors at a single point in time. It answers a single question for the borrower: what does the market currently charge the sovereign to borrow for one month versus thirty years? For a finance ministry, the curve is not a passive market observation — it is the primary pricing signal used to sequence new issuance, benchmark state-owned enterprise and local-government borrowing costs, and infer market expectations about future policy rates and inflation.

The curve is distinct from a single bond's yield-to-maturity (YTM), which is the internal rate of return equating a bond's price to the present value of its cash flows. The curve is the cross-sectional map of YTMs across the maturity spectrum, constructed from a basket of instruments issued at different times but observed simultaneously.

### Why the Curve Is Not Directly Observable

A government does not typically have one bond outstanding at every possible maturity. The Philippine Bureau of the Treasury (BTr), for instance, issues Treasury bills (T-bills) at 91, 182, and 364 days, and Treasury bonds (T-bonds) at benchmark tenors (2, 3, 5, 7, 10, 20, 25 years), auctioned on a pre-announced calendar. At any given moment, the actual outstanding bonds cluster at irregular residual maturities — a "10-year" bond issued three years ago now has roughly seven years left to run. Raw market yields therefore form a scattered set of points, not a smooth curve. Construction is the technical process of converting this scatter into a continuous function $y(\tau)$, where $\tau$ is time to maturity.

### The Building Block: The Discount Function and Zero-Coupon Curve

Before fitting a curve to coupon-bearing bond yields, it is necessary to understand the theoretically cleaner underlying object: the **zero-coupon yield curve** (also called the **spot curve**), $z(\tau)$. This is the yield an investor would earn on a hypothetical bond that pays no coupons and returns only a single lump sum at maturity $\tau$.

The spot curve is related to the **discount function** $D(\tau)$, which gives the present value of one unit of currency to be received at time $\tau$:

$$D(\tau) = \frac{1}{(1 + z(\tau))^{\tau}}$$

(using annual compounding convention; continuous compounding uses $D(\tau) = e^{-z(\tau)\tau}$).

Most sovereign bonds pay semi-annual or annual coupons, not a single lump sum. A coupon bond's price is the sum of each cash flow discounted at the *spot rate corresponding to that cash flow's own date*, not at a single YTM:

$$P = \sum_{i=1}^{n} \frac{C_i}{(1+z(t_i))^{t_i}} + \frac{F}{(1+z(t_n))^{t_n}}$$

where $C_i$ are coupon payments, $F$ is face value, and $t_i$ are payment dates. The YTM is instead the single flat rate $y$ that satisfies:

$$P = \sum_{i=1}^{n} \frac{C_i}{(1+y)^{t_i}} + \frac{F}{(1+y)^{t_n}}$$

Because YTM blends discount rates across the whole cash-flow schedule, two bonds with the same maturity but different coupon rates will generally show slightly different YTMs even under an identical underlying spot curve — an effect known as **coupon effect** or **coupon bias**. This is the technical reason debt-management offices prefer to build and monitor the zero-coupon curve rather than simply connecting raw YTM observations.

### Construction Method 1: Bootstrapping

**Bootstrapping** is the sequential extraction of spot rates from a set of coupon bond prices, moving from the shortest maturity outward. Each step uses spot rates already solved for to isolate the one remaining unknown.

**Mechanics:**

1. The shortest-maturity instrument (a T-bill, which is a discount instrument with no coupon) gives the spot rate directly, since $P = F / (1+z(\tau))^{\tau}$ can be solved immediately.
2. For the next coupon bond (say, a 2-year bond with semi-annual coupons), all coupon dates before maturity are discounted using spot rates already known from step 1 (interpolating if a T-bill of exactly that tenor is unavailable). The only unknown left is the spot rate for the final, 2-year cash flow, which is solved algebraically.
3. This proceeds bond by bond up the maturity ladder, each step "bootstrapping" off the rates already recovered.

This method requires a sufficiently dense and liquid set of on-the-run (most recently auctioned, most actively traded) bonds at each tenor bucket. In markets with thin secondary trading at certain maturities — common for sovereigns without a fully developed benchmark bond program — gaps force reliance on interpolation or parametric fitting instead.

### Construction Method 2: Parametric Curve Fitting (Nelson-Siegel and Extensions)

Where bond data is sparse, noisy, or where a smooth analytically tractable curve is preferred for policy communication and modeling, debt offices and central banks fit a parsimonious functional form directly to observed yields, rather than bootstrapping point by point.

The most widely used specification is the **Nelson-Siegel model**, which expresses the instantaneous forward rate as a combination of a constant, an exponentially decaying term, and a hump-shaped term, integrated to yield the spot curve:

$$z(\tau) = \beta_0 + \beta_1\left(\frac{1-e^{-\tau/\lambda}}{\tau/\lambda}\right) + \beta_2\left(\frac{1-e^{-\tau/\lambda}}{\tau/\lambda} - e^{-\tau/\lambda}\right)$$

Each parameter has an economically interpretable role:

- $\beta_0$ — the **level** factor: the long-run asymptotic yield as $\tau \to \infty$, closely tied to long-run inflation and policy-rate expectations.
- $\beta_1$ — the **slope** factor: governs the spread between short and long rates; a negative $\beta_1$ produces the normal upward-sloping curve.
- $\beta_2$ — the **curvature** factor: controls the pronouncedness of a hump or trough at medium maturities.
- $\lambda$ — governs the maturity at which the curvature term peaks, and the decay rate of the exponential terms.

The **Nelson-Siegel-Svensson (NSS) extension** adds a second curvature term with its own decay parameter $\lambda_2$, giving the model enough flexibility to fit curves with two humps — common when a sovereign's short end is distorted by monetary-policy operations while the long end reflects separate fiscal-risk pricing. Many debt management offices and central banks (the European Central Bank's published euro-area curve is a public example of the method, not the institution being cited as authority here) use NSS-family models precisely because a handful of parameters compress an entire curve into a form usable for forecasting and stress-testing.

Parameters are typically estimated by nonlinear least squares, minimizing the sum of squared deviations between model-implied prices (or yields) and observed market prices (or yields) across all available bonds simultaneously — in contrast to bootstrapping's sequential, exact-fit approach.

### Construction Method 3: Spline-Based Fitting

An alternative to a single global parametric function is **spline fitting** — most commonly cubic splines or the **Fama-Bliss** or **McCulloch** cubic-spline methodologies — in which the discount function is represented as a piecewise polynomial with continuity and smoothness constraints (matching value and first/second derivatives) imposed at a set of **knot points** along the maturity axis. Splines offer more local flexibility than Nelson-Siegel (a pricing anomaly at the 7-year point does not distort the fit at the 20-year point) but are more prone to overfitting and oscillation (Runge's phenomenon) if knots are too dense relative to available data points. Regulatory and academic literature on curve-fitting philosophy: while central banks can choose spline-based models due to their higher local flexibility, they can also choose parsimonious function-based models due to their easier economic interpretation, ability to smooth idiosyncratic variations, and the fact that they typically involve estimating fewer parameters.

### Worked Example: Constructing a Simplified Philippine Peso Curve

Assume the BTr has three benchmark instruments trading, quoted as annualized YTMs on a common valuation date:

| Instrument | Tenor | Type | YTM |
| --- | --- | --- | --- |
| 91-day T-bill | 0.25y | discount | 5.50% |
| 2-year T-bond | 2y | 6% semi-annual coupon | 6.10% |
| 5-year T-bond | 5y | 6.25% semi-annual coupon | 6.45% |

**Step 1 (T-bill spot rate):** Since the T-bill has no coupon, its YTM *is* its spot rate directly: $z(0.25) = 5.50\%$.

**Step 2 (2-year bootstrap):** The 2-year bond pays four semi-annual coupons of ₱3.00 per ₱100 face (6%/2), plus ₱100 principal at maturity. Discount the first three coupon dates using spot rates interpolated between the T-bill point and the (still-unknown) 2-year point — in practice this requires either an initial interpolation assumption or a denser input set with a 1-year instrument. With a 1-year point available (assume $z(1) = 5.85\%$, itself bootstrapped from a 1-year bill), solve:

$$100 = \frac{3}{(1.0575)^{0.5}} + \frac{3}{(1.0585)^{1}} + \frac{3}{(1+z(1.5))^{1.5}} + \frac{103}{(1+z(2))^{2}}$$

Solving sequentially for each unknown spot rate in turn, $z(2)$ typically comes out marginally above the 2-year bond's own YTM (6.10%) when the curve is upward-sloping, because coupons paid before maturity are discounted at lower short-end rates, requiring the terminal discount rate to rise slightly to match the observed price.

**Step 3 (5-year bootstrap):** Repeat using all previously solved spot rates ($z(0.25)$ through $z(2)$, interpolated as needed for interim coupon dates) to isolate $z(5)$ from the 5-year bond's price.

The resulting curve — five to seven solved spot-rate points — would then typically be fed into a Nelson-Siegel or spline fit to produce a continuous function usable for pricing any arbitrary maturity, including off-the-run bonds and new LGU or GOCC (government-owned and controlled corporation) issuance benchmarked off the sovereign curve.

### Curve Shapes and Their Borrower-Side Interpretation

- **Normal (upward-sloping) curve**: long yields exceed short yields, reflecting a positive **term premium** — compensation investors demand for duration and inflation risk over a longer horizon. This is the typical shape and the one under which a debt manager's classic trade-off applies: short-tenor issuance is cheaper on a running-cost basis but concentrates **rollover risk** (the risk that debt must be refinanced at an unknown future rate, or that market access itself is impaired at the refinancing date).
- **Inverted curve**: short yields exceed long yields, usually signaling that markets expect the central bank's current tight policy stance to ease, or pricing near-term recession risk. For a sovereign issuer, an inverted curve makes long-tenor issuance temporarily cheap relative to short-tenor rollover, incentivizing debt managers to lock in longer average maturity — directly extending the state's **weighted average maturity (WAM)** of the debt stock and reducing rollover risk, at the cost of higher immediate coupon expense compared to further curve-shortening.
- **Flat or humped curve**: often reflects genuine market uncertainty about the medium-term policy path, or technical distortion from a specific benchmark tenor being oversupplied or undersupplied relative to investor demand (e.g., pension-fund driven demand concentrated at the 10–20 year point in many emerging markets, "pulling down" yields at that segment independent of macro fundamentals).

### Sovereign Curve vs. Risk-Free Curve: The Credit and Liquidity Overlay

For an emerging-market sovereign borrowing partly in foreign currency, the *local-currency* government curve is not automatically the risk-free curve for that currency — but conventionally, for the domestic-currency-denominated curve, the sovereign is treated as the closest available proxy for risk-free, since it is the only entity with unrestricted currency-issuance authority (a distinction that matters more for eurozone members, which do not control their own currency, than for the Philippines, which retains monetary sovereignty over the peso). Foreign-currency sovereign bonds — e.g., US-dollar-denominated **Republic of the Philippines (ROP) global bonds** — trade at a spread *above* the US Treasury curve, and that spread (often benchmarked via **credit default swap (CDS)** premia or the **EMBI (Emerging Markets Bond Index) spread**) is a direct, continuously updated market read on perceived sovereign credit risk, separate from the peso curve's own construction.

### Mermaid Diagram: Curve Construction Pipeline

```mermaid
flowchart TD
    A[Raw traded bond prices and YTMs, multiple tenors] --> B{Sufficient density at each tenor?}
    B -->|Yes, liquid benchmark ladder| C[Bootstrapping: sequential spot-rate extraction]
    B -->|No, sparse or noisy data| D[Parametric fit: Nelson-Siegel / NSS]
    B -->|Moderate density, local flexibility desired| E[Spline fit: cubic / Fama-Bliss]
    C --> F[Zero-coupon spot curve z(tau)]
    D --> F
    E --> F
    F --> G[Discount function D(tau)]
    G --> H[Price off-the-run bonds and new issuance]
    G --> I[Benchmark LGU / GOCC borrowing spreads]
    G --> J[Infer market policy-rate and inflation expectations]
```

### SVG Illustration: Stylized Yield Curve Shapes (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 420">
\<style\>
.ax{stroke:#333;stroke-width:2;}
.lbl{font-family:sans-serif;font-size:13px;fill:#222;}
.ttl{font-family:sans-serif;font-size:15px;fill:#111;font-weight:bold;}
.normal{stroke:#1a7a3c;stroke-width:3;fill:none;}
.inverted{stroke:#c0392b;stroke-width:3;fill:none;}
.flat{stroke:#7d6608;stroke-width:3;fill:none;}
\</style\>
<text x="20" y="25" class="ttl">Sovereign Yield Curve Shapes (svg_diagram)</text>
<line x1="70" y1="360" x2="650" y2="360" class="ax" />
<line x1="70" y1="360" x2="70" y2="50" class="ax" />
<text x="340" y="400" class="lbl">Maturity (years) →</text>
<text x="20" y="200" class="lbl" transform="rotate(-90 20 200)">Yield (%)</text>
<text x="90" y="378" class="lbl">0.25</text>
<text x="200" y="378" class="lbl">2</text>
<text x="330" y="378" class="lbl">5</text>
<text x="460" y="378" class="lbl">10</text>
<text x="600" y="378" class="lbl">25</text>
<path d="M 90 320 C 200 260, 330 200, 460 150 S 600 110, 620 100" class="normal" />
<path d="M 90 130 C 200 170, 330 230, 460 280 S 600 320, 620 330" class="inverted" />
<path d="M 90 220 C 200 210, 330 215, 460 210 S 600 205, 620 200" class="flat" />
<circle cx="620" cy="100" r="4" fill="#1a7a3c" />
<text x="500" y="90" class="lbl" fill="#1a7a3c">Normal (upward-sloping)</text>
<circle cx="620" cy="330" r="4" fill="#c0392b" />
<text x="500" y="348" class="lbl" fill="#c0392b">Inverted</text>
<circle cx="620" cy="200" r="4" fill="#7d6608" />
<text x="500" y="192" class="lbl" fill="#7d6608">Flat / humped</text>
</svg>

### Practical Implications for Debt Management Offices

The constructed curve feeds directly into two core debt-management instruments: the **Medium-Term Debt Management Strategy (MTDS)**, which uses the curve to model cost-risk trade-offs across alternative issuance strategies (e.g., front-loading short tenors versus extending WAM), and the **auction pricing process** itself, where the secondary-market curve on the trading day prior to an auction sets the reference yield around which primary dealers bid. A persistently steep curve raises the **weighted average interest cost** of extending maturity, creating direct political-economy pressure to over-rely on short-tenor issuance — the mechanism underlying many emerging-market **rollover-risk crises**, where a state's own curve-driven cost-minimization incentives at each individual auction cumulatively produce a dangerously short average maturity profile at the portfolio level. [Inference: the general rollover-risk dynamic is well-established in DSA and MTDS literature; the specific magnitude of this effect for any single country's curve requires current primary-dealer and auction-result data.]

**Related Topics**

- Debt sustainability analysis (DSA) methodology and stress-testing frameworks
- Weighted average maturity and the Medium-Term Debt Management Strategy (MTDS)
- Collective action clauses and sovereign debt restructuring mechanics
- Local-currency versus foreign-currency debt composition and currency mismatch risk
- The EMBI spread and CDS-implied sovereign credit risk pricing
- Primary dealer systems and government securities auction design