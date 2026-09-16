## Advertising and Promotional Elasticity

### Overview

Advertising elasticity of demand ($E_A$) measures the responsiveness of quantity demanded (or sales revenue) of a good to a change in advertising or promotional expenditure, holding price, income, and other demand determinants constant. It is a key metric in managerial economics for evaluating the effectiveness of marketing spend and for optimizing promotional budget allocation.

### Definition and Formula

**Percentage Formula**

$$E_A = \frac{\%\Delta Q_d}{\%\Delta A}$$

Where $A$ represents advertising/promotional expenditure (or, in some formulations, an advertising intensity index).

**Point Elasticity (Calculus-Based)**

$$E_A = \frac{\partial Q}{\partial A} \times \frac{A}{Q}$$

**Key Points**

- Advertising elasticity is normally **positive** ($E_A > 0$), since increased advertising is expected to increase (or at minimum not decrease) demand
- Unlike price elasticity, there is no natural sign-based classification scheme (positive vs. negative); instead, the focus is on the **magnitude** of $E_A$ relative to cost, to assess whether advertising spend is profitable at the margin
- Advertising elasticity is generally **much smaller** in magnitude than own-price elasticity for most consumer goods — advertising tends to be a comparatively weaker demand lever than price

### Worked Example

A firm increases its advertising budget from $200,000 to $240,000 (a 20% increase); quantity sold rises from 50,000 to 52,500 units (a 5% increase).

$$E_A = \frac{\%\Delta Q}{\%\Delta A} = \frac{5\%}{20\%} = 0.25$$

**Output**

$E_A = 0.25$: a 1% increase in advertising spend is associated with only a 0.25% increase in quantity sold — advertising demand response is **inelastic**, indicating diminishing returns to additional promotional spend at this level.

### The Dorfman-Steiner Condition

A foundational result in managerial economics linking advertising intensity, price elasticity, and advertising elasticity, developed by Robert Dorfman and Peter Steiner (1954). It characterizes the profit-maximizing ratio of advertising expenditure to sales revenue for a firm with market power.

$$\frac{A}{PQ} = \frac{E_A}{|E_d|}$$

Where $A/PQ$ is the advertising-to-sales ratio, $E_A$ is advertising elasticity, and $|E_d|$ is the absolute value of price elasticity of demand.

**Key Points**

- The condition states that a profit-maximizing firm should set its advertising-to-sales ratio equal to the ratio of advertising elasticity to (absolute) price elasticity
- **Implication**: firms facing more price-inelastic demand ($|E_d|$ low) — often due to strong brand differentiation — can profitably sustain a *higher* advertising-to-sales ratio, since the marginal profitability of demand-shifting via advertising is relatively greater when price competition is less binding
- **Implication**: firms with high advertising elasticity ($E_A$ high, meaning advertising is highly effective at shifting demand) should also allocate a higher share of revenue to advertising

**Derivation Intuition**

The condition arises from jointly optimizing price and advertising to maximize profit $\pi = PQ(P,A) - C(Q) - A$, and setting both first-order conditions ($\partial \pi/\partial P = 0$ and $\partial \pi/\partial A = 0$) equal, then combining the resulting expressions for markup and advertising intensity.

```mermaid
flowchart TD
    A[Firm Sets Price and Advertising<br/>to Maximize Profit] --> B[First-Order Condition on Price:<br/>Lerner Index / Markup Rule]
    A --> C[First-Order Condition on Advertising:<br/>Marginal Revenue of Ad Spend = Marginal Cost of Ad Spend]
    B --> D[Combine Both Conditions]
    C --> D
    D --> E["Dorfman-Steiner Condition:<br/>A/PQ = E_A / |E_d|"]
    E --> F[Higher E_A → Higher optimal<br/>ad-to-sales ratio]
    E --> G[Lower |E_d| → Higher optimal<br/>ad-to-sales ratio<br/>brand loyalty reduces price sensitivity]
```

### Advertising Response Function and Diminishing Returns

**Key Points**

- Empirical advertising response functions typically exhibit **diminishing marginal returns**: each additional unit of advertising spend generates progressively smaller increases in sales, beyond some threshold
- Some models incorporate an initial **S-shaped (threshold) region**, where very low advertising levels have negligible effect (below an awareness threshold), followed by a region of increasing then diminishing returns
- **Advertising saturation**: at sufficiently high spend levels, $E_A \to 0$, indicating the market is saturated and further spend yields negligible additional sales

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 500 340">
<text x="250" y="22" font-size="15" font-weight="bold" text-anchor="middle" fill="#1a1a1a">Advertising Response Function (svg_diagram)</text>
<line x1="70" y1="290" x2="70" y2="50" stroke="#333" stroke-width="2" />
<line x1="70" y1="290" x2="450" y2="290" stroke="#333" stroke-width="2" />
<text x="455" y="295" font-size="11" fill="#333">Advertising Spend (A)</text>
<text x="40" y="45" font-size="11" fill="#333">Sales (Q)</text>
<path d="M 90,280 Q 150,275 200,220 Q 280,120 350,90 Q 400,75 440,70" stroke="#2563eb" stroke-width="2" fill="none" />

<text x="100" y="270" font-size="9" fill="#555">Threshold region</text>

<text x="220" y="180" font-size="9" fill="#555">Increasing returns</text>

<text x="340" y="105" font-size="9" fill="#555">Diminishing returns / saturation</text>

</svg>

### Types of Advertising Effects on Demand

**Key Points**

- **Demand-expanding (informative) advertising**: increases total market demand by informing consumers of a product's existence, features, or benefits — common for new product categories or markets with low awareness
- **Combative (persuasive) advertising**: primarily shifts market share between competing brands within an existing market rather than expanding total market size — common in mature, saturated markets (e.g., soft drinks, telecom carriers)
- **Reminder/reinforcement advertising**: maintains brand salience and loyalty among existing customers, often exhibiting lower measured elasticity since it targets retention rather than acquisition

### Distinguishing Short-Run versus Long-Run (Carryover) Effects

**Key Points**

- Advertising often has a **carryover (lagged) effect**, where current spend continues to influence sales in subsequent periods (captured in econometric models via distributed-lag or Koyck transformation specifications)
- Short-run advertising elasticity (immediate-period sales response) is typically **smaller** than cumulative long-run elasticity, once carryover effects are included
- **[Inference]** Because of this carryover effect, evaluating advertising effectiveness using only same-period (contemporaneous) sales data risks understating the true return on advertising investment; most rigorous marketing-mix modeling studies account for lagged effects, though the appropriate lag structure varies substantially by product category and media channel.

### Empirical Estimation Approaches

**Key Points**

- **Log-log regression**: $\ln Q = \alpha + \beta \ln A + \gamma \ln P + \varepsilon$, where $\hat\beta$ estimates advertising elasticity directly (constant-elasticity specification)
- **Koyck/distributed lag models**: incorporate lagged advertising terms to capture carryover effects and estimate cumulative long-run elasticity
- **Marketing-mix modeling (MMM)**: modern applied approach using multivariate regression or machine-learning methods across multiple media channels (TV, digital, social, etc.) to estimate channel-specific elasticities and optimize budget allocation
- Estimation faces similar **identification challenges** as price elasticity estimation — advertising spend is often endogenously set in response to anticipated demand (e.g., firms may increase ad spend precisely when they expect strong seasonal demand), requiring careful econometric controls or natural experiments (e.g., geographic ad spend holdouts) for credible causal estimates

### Applications in Managerial Decision-Making

**Key Points**

- **Optimal advertising budget determination**: using the Dorfman-Steiner condition (or empirically estimated response functions) to set advertising spend at the level where marginal revenue from additional advertising equals its marginal cost
- **Media mix allocation**: comparing advertising elasticities across channels (television, digital, social media, print) to allocate budget toward the highest-return channels
- **Brand equity building versus short-term sales promotion trade-off**: firms must balance advertising aimed at long-run brand equity (often lower immediate measured elasticity) against short-term promotional tactics (discounts, coupons) that may show higher immediate elasticity but can erode brand value or train consumers to wait for deals
- **Competitive advertising response**: in oligopolistic markets, a firm's advertising elasticity estimates must account for the likelihood of competitive retaliation (rival firms increasing their own advertising in response), which can dampen the net market-share effect of any single firm's advertising increase

### Promotional (Price-Based) Elasticity: A Related but Distinct Concept

**Key Points**

- **Promotional elasticity** (sometimes called deal elasticity) specifically measures the sales response to temporary price promotions (discounts, coupons, "buy-one-get-one" offers), which is conceptually related to but distinct from pure advertising elasticity
- Promotional/deal elasticity is typically **substantially larger in magnitude** than baseline own-price elasticity, since temporary price cuts often induce stockpiling, brand-switching, and purchase acceleration effects beyond a simple permanent price change
- Firms distinguish between "base" sales (attributable to regular price/advertising) and "incremental" sales (attributable specifically to a promotional event) when evaluating promotional ROI

### Comparison of Elasticity Types in Managerial Decision-Making

| Elasticity Type | Typical Magnitude | Primary Managerial Use |
| --- | --- | --- |
| Price elasticity | Often larger, more immediate | Pricing strategy, revenue optimization |
| Advertising elasticity | Typically smaller, subject to carryover | Long-run brand building, budget allocation |
| Promotional/deal elasticity | Often very large but short-lived | Short-term sales spikes, inventory clearance, competitive response |

### Related Topics

- Price Elasticity of Demand and Its Determinants
- Dorfman-Steiner Condition and Optimal Advertising Intensity
- Elasticity and Total Revenue Relationships
- Monopolistic Competition and Non-Price Competition
- Marketing-Mix Modeling and Media Attribution
- Brand Equity and Long-Run versus Short-Run Marketing Strategy