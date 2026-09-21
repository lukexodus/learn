## Structural Models of Auctions


### Overview

Structural auction models recover bidders' underlying private valuations (or the distribution of valuations) from observed bid data, using economic theory — the equilibrium bidding strategy implied by a specific auction format and information structure — to invert observed bids into structural primitives. This enables counterfactual analysis of alternative auction designs (reserve prices, format changes, mechanism redesign) using empirically grounded valuation distributions.

### Foundational Auction Environments

**Key Points**

- **Independent Private Values (IPV)**: each bidder $i$ knows their own valuation $v_i$, drawn independently from a common distribution $F(v)$; other bidders' valuations do not affect bidder $i$'s own valuation directly
- **Common Value (CV)**: the object has a single (unknown) true value $V$ common to all bidders, and each bidder observes only a noisy private signal $s_i$ correlated with $V$ — this environment produces the **winner's curse**, where winning is informative that one's own signal was likely an overestimate
- **Affiliated Values**: a general model nesting IPV and CV as special cases, where signals are statistically affiliated (a generalized positive dependence)

### First-Price Sealed-Bid Auctions Under IPV

**Key Points**

In the symmetric IPV first-price auction with $N$ risk-neutral bidders, the equilibrium bidding strategy $\beta(v)$ solves the bidder's optimization problem, yielding the well-known closed form:

$$\beta(v) = v - \frac{\int_{\underline{v}}^{v} F(u)^{N-1}\,du}{F(v)^{N-1}}$$

Bidders shade their bids below their true valuation ($\beta(v) < v$) to balance the probability of winning against the surplus conditional on winning; the degree of shading decreases as $N$ increases (more competition compresses the bid-value gap).

### The Guerre-Perrigne-Vuong (GPV) Nonparametric Identification Approach

**Key Points**

Guerre, Perrigne, and Vuong (2000) established that the valuation distribution $F(v)$ is **nonparametrically identified** from observed bid data alone, without imposing a parametric family on $F$, under the IPV first-price auction model. The key insight inverts the first-order condition of the bidder's optimization problem:

$$v_i = b_i + \frac{1}{N-1} \cdot \frac{G(b_i)}{g(b_i)}$$

where $G(\cdot)$ and $g(\cdot)$ are the CDF and density of the **observed equilibrium bid distribution** (estimable nonparametrically from data via kernel methods), and $b_i$ is bidder $i$'s observed bid. This equation recovers each bidder's implied (pseudo-)valuation $\hat{v}_i$ directly from their observed bid and the estimated bid distribution, without ever explicitly solving the bidder's equilibrium strategy $\beta(v)$ in closed form.

**Two-Step Nonparametric Estimation Procedure**

1. **First stage**: nonparametrically estimate the bid density $g(b)$ and CDF $G(b)$ from observed bids (e.g., via kernel density estimation), separately for each auction with $N$ bidders (or controlling for $N$ via a first-stage regression if $N$ varies)
2. **Second stage**: invert the first-order condition above to construct pseudo-valuations $\hat{v}_i$ for each observed bid, then estimate the valuation density $f(v)$ nonparametrically from the pseudo-valuation sample (again via kernel methods)

### Diagram: GPV Two-Step Estimation Procedure

```mermaid
flowchart TD
    A[Observed bid data across auctions] --> B[Stage 1: Kernel-estimate bid density g(b) and CDF G(b)]
    B --> C[Apply first-order condition inversion]
    C --> D[v_i = b_i + 1/(N-1) times G(b_i)/g(b_i)]
    D --> E[Pseudo-valuations v_i_hat for each bidder]
    E --> F[Stage 2: Kernel-estimate valuation density f(v) from pseudo-valuations]
    F --> G[Structural valuation distribution F(v)]
    G --> H[Counterfactual simulation: reserve price changes, format changes]
```

### Illustration: Bid Shading Under IPV First-Price Auctions (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 300" font-family="sans-serif">
<text x="350" y="20" text-anchor="middle" font-size="16" font-weight="bold">Equilibrium Bid Function Under First-Price IPV (svg_diagram)</text>
<line x1="70" y1="250" x2="620" y2="250" stroke="#333" stroke-width="1.5" />
<line x1="70" y1="250" x2="70" y2="50" stroke="#333" stroke-width="1.5" />
<text x="345" y="280" text-anchor="middle" font-size="11">Valuation v</text>
<text x="30" y="150" text-anchor="middle" font-size="11" transform="rotate(-90 30 150)">Bid b</text>
<line x1="70" y1="250" x2="590" y2="70" stroke="#999" stroke-width="1.5" stroke-dasharray="4,3" />
<text x="560" y="60" font-size="10" fill="#666">45° line: b = v</text>
<path d="M 70 250 Q 300 220 590 110" stroke="#2b6cb0" stroke-width="2.5" fill="none" />
<text x="450" y="140" font-size="10" fill="#2b6cb0">Equilibrium bid β(v)</text>

<text x="340" y="235" text-anchor="middle" font-size="10" fill="#a00">Shading gap narrows as N increases</text>

</svg>

### Common Value Auctions and the Winner's Curse

**Key Points**

Under common values, the winner's bid conveys information about the highest (most optimistic) signal among all bidders. Rational bidders **shade their bids to correct for the winner's curse**, adjusting their bid downward relative to their own raw signal to account for the fact that winning implies their signal was likely an overestimate of the true common value $V$. Structural estimation in CV settings (e.g., Hendricks-Porter for offshore oil lease auctions) requires modeling this signal-correction explicitly, and identification generally relies on additional structure (e.g., observing ex-post realized values, or exploiting cross-auction variation) beyond what pure bid data alone can deliver in the pure CV case, since bid data alone often cannot separately identify signal precision from the common value distribution without further assumptions.

### Ascending (English) and Second-Price Auctions

**Key Points**

Under IPV, the **second-price sealed-bid auction** has a dominant strategy: bid one's true valuation, $\beta(v) = v$, making the mapping from bids to valuations direct (no inversion needed) — considerably simplifying structural estimation relative to first-price auctions. The **English (ascending) auction** under IPV is strategically equivalent to the second-price auction in the standard button-auction model (dropout price reveals valuation), though real-world ascending auction data (e.g., jump bidding, minimum bid increments) can complicate this equivalence in practice.

### Auctions with Asymmetric Bidders

**Key Points**

When bidders draw valuations from different distributions $F_i(v)$ (e.g., strong vs. weak bidders, as in some procurement or government contract settings), the equilibrium bidding strategies differ by bidder type, and nonparametric identification/estimation must be conducted separately by bidder type or bidder class, substantially increasing data requirements. Asymmetric auction models are central to some applications (e.g., set-aside programs favoring small businesses in government procurement) where the researcher wants to quantify how asymmetry affects revenue and efficiency.

### Auctions with Unobserved Heterogeneity

**Key Points**

A key practical challenge: auction-level characteristics observed by bidders but not by the econometrician (e.g., unobserved item quality) create **unobserved heterogeneity** across auctions, which can bias naive GPV estimates if ignored (an omitted variable correlated with both bids and the implied valuation distribution). Common corrections include:

- Controlling for observable auction/item characteristics as flexibly as possible
- Exploiting auctions with multiple bids per auction-level unobservable (e.g., using within-auction bid ratios, which can difference out a multiplicative unobserved auction effect under specific functional form assumptions — Haile-Kitamura-style approaches)

### Reserve Prices and Optimal Auction Design

**Key Points**

Once $F(v)$ is recovered, the researcher can compute the **optimal reserve price** under a revenue-maximizing objective (Myerson's optimal auction theory), or simulate counterfactual revenue and bidder surplus under alternative reserve price policies — a primary practical motivation for structural auction estimation in applications like timber, spectrum, and procurement auctions. Myerson's virtual valuation:

$$\psi(v) = v - \frac{1 - F(v)}{f(v)}$$

determines the revenue-maximizing mechanism; the seller optimally excludes bidders with $\psi(v) < 0$, implying a strictly positive optimal reserve price above the seller's own valuation whenever $F$ has an increasing virtual valuation (regularity condition).

### Parametric vs. Nonparametric Approaches

| Aspect | Parametric | Nonparametric (GPV) |
| --- | --- | --- |
| Flexibility | Requires assuming a parametric family for $F(v)$ | No distributional assumption on $F(v)$ |
| Data requirements | Can work with smaller samples | Requires larger samples for reliable kernel estimation, especially in the tails |
| Estimation method | MLE or GMM matching moments of the bid distribution to the parametric model | Two-step kernel inversion (GPV) |
| Risk of misspecification | High if the parametric family is wrong | Low — nonparametric by construction |
| Tail behavior | Well-behaved even with limited data | Kernel estimates can be unreliable in the tails without adequate data density |

### Practical Estimation Challenges

[Inference] Nonparametric GPV estimation is known to perform poorly in small samples, particularly in estimating the boundary/tail behavior of the valuation distribution, which matters directly for optimal reserve price calculations — a widely noted practical limitation, though the precise severity depends on sample size and the number of bidders per auction in the specific dataset.

**Next Steps**

1. Identify the auction format (first-price, second-price/ascending) and information structure (IPV vs. CV) most consistent with the institutional setting
2. For first-price IPV auctions, apply GPV two-step nonparametric estimation; for second-price/ascending IPV auctions, use observed bids/dropout prices directly as valuations
3. Test for and correct unobserved auction-level heterogeneity before interpreting the recovered valuation distribution
4. Assess whether asymmetric bidder types are present and, if so, estimate separately by bidder class
5. Use the recovered valuation distribution to compute Myerson virtual valuations and simulate counterfactual reserve price or format changes

### Related Topics

- Myerson's Optimal Auction Theory and Virtual Valuations
- Winner's Curse and Common Value Auction Identification (Hendricks-Porter)
- Unobserved Heterogeneity Corrections in Auction Data (Haile-Kitamura)
- Asymmetric Bidder Models in Procurement Auctions
- Multi-Unit and Combinatorial Auction Identification
- Kernel Density Estimation and Bandwidth Selection in Nonparametric Econometrics