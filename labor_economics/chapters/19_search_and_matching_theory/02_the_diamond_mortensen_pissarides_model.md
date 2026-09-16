## The Diamond Mortensen Pissarides Model


### Overview and Nobel Prize Context

The Diamond-Mortensen-Pissarides (DMP) model is the workhorse general-equilibrium framework of search-and-matching frictions in labor markets, developed across contributions by Peter Diamond (1982), Dale Mortensen, and Christopher Pissarides (Mortensen and Pissarides, 1994; Pissarides, 2000). The three shared the 2010 Nobel Memorial Prize in Economic Sciences for this body of work. Unlike the partial-equilibrium McCall search model, DMP endogenizes both sides of the market: unemployed workers search for jobs *and* firms make costly vacancy-posting decisions, with a matching function connecting aggregate search and recruiting effort to the realized flow of new hires.

The model's central achievement is providing a microfounded, equilibrium theory of **unemployment as a frictional phenomenon** — unemployment coexists with unfilled vacancies not because wages fail to clear the market in the Walrasian sense, but because matching workers to jobs is inherently time-consuming and costly, and wages are determined via bargaining rather than a competitive auctioneer.

### Core Building Blocks

**The Matching Function**

The matching function is the central technological primitive of the model, converting the stock of unemployed searchers $U$ and the stock of posted vacancies $V$ into a flow of new matches (hires) $M$:

$$M = m(U, V)$$

typically assumed to be constant-returns-to-scale and increasing in both arguments, with the widely-used Cobb-Douglas functional form:

$$M = A \cdot U^{\alpha} V^{1-\alpha}, \quad \alpha \in (0,1)$$

where $A$ is matching efficiency and $\alpha$ is the elasticity of matches with respect to unemployment.

**Labor Market Tightness**

Define labor market tightness as:

$$\theta \equiv \frac{V}{U}$$

the ratio of vacancies to unemployed searchers. Tightness is the central endogenous state variable of the model, summarizing how favorable conditions are for job-seekers (high $\theta$) versus for firms recruiting (low $\theta$).

**Job-Finding and Vacancy-Filling Rates**

Using constant-returns-to-scale of the matching function, define:

$$f(\theta) = \frac{M}{U} = m(1, \theta) \quad \text{(job-finding rate per unemployed worker)}$$



$$q(\theta) = \frac{M}{V} = m\left(\frac{1}{\theta}, 1\right) \quad \text{(vacancy-filling rate per posted vacancy)}$$

with $f(\theta) = \theta \cdot q(\theta)$ by construction. Standard assumptions imply $f'(\theta) > 0$ (tighter markets mean workers find jobs faster) and $q'(\theta) < 0$ (tighter markets mean firms fill vacancies more slowly) — the core congestion externality of the model.

### SVG Illustration: The Matching Function and Market Tightness (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 720 380">
<text x="360" y="26" text-anchor="middle" font-size="16" font-weight="bold" font-family="sans-serif">DMP Matching Technology (svg_diagram)</text>
<rect x="60" y="150" width="160" height="90" rx="8" fill="#e8f0fd" stroke="#2980b9" stroke-width="2" />
<text x="140" y="185" text-anchor="middle" font-size="14" font-weight="bold" font-family="sans-serif">Unemployed</text>
<text x="140" y="205" text-anchor="middle" font-size="16" font-family="sans-serif">U</text>
<text x="140" y="225" text-anchor="middle" font-size="11" font-family="sans-serif">(searching workers)</text>
<rect x="500" y="150" width="160" height="90" rx="8" fill="#fde8e8" stroke="#c0392b" stroke-width="2" />
<text x="580" y="185" text-anchor="middle" font-size="14" font-weight="bold" font-family="sans-serif">Vacancies</text>
<text x="580" y="205" text-anchor="middle" font-size="16" font-family="sans-serif">V</text>
<text x="580" y="225" text-anchor="middle" font-size="11" font-family="sans-serif">(posted by firms)</text>
<rect x="280" y="150" width="160" height="90" rx="8" fill="#e8fde8" stroke="#27ae60" stroke-width="2" />
<text x="360" y="185" text-anchor="middle" font-size="14" font-weight="bold" font-family="sans-serif">Matches</text>
<text x="360" y="205" text-anchor="middle" font-size="16" font-family="sans-serif">M = m(U,V)</text>
<text x="360" y="225" text-anchor="middle" font-size="11" font-family="sans-serif">new hires per period</text>
<line x1="220" y1="195" x2="280" y2="195" stroke="black" stroke-width="2" marker-end="url(#arr2)" />
<line x1="500" y1="195" x2="440" y2="195" stroke="black" stroke-width="2" marker-end="url(#arr2)" />
<text x="360" y="290" text-anchor="middle" font-size="13" font-family="sans-serif">θ = V / U (market tightness)</text>

<text x="360" y="315" text-anchor="middle" font-size="13" font-family="sans-serif">f(θ) = M/U increasing in θ | q(θ) = M/V decreasing in θ</text>

</svg>

### Firm's Vacancy-Posting Decision (Free Entry)

Firms post vacancies at a flow cost $c$ per period. Under free entry, firms post vacancies until the expected value of a vacancy is driven to zero. The value of a filled job to the firm, $J$, and the value of a vacancy, $V_{vac}$, satisfy:

$$r \cdot V_{vac} = -c + q(\theta)[J - V_{vac}]$$

Free entry (zero expected profit from posting, $V_{vac} = 0$) yields the **job creation condition**:

$$\frac{c}{q(\theta)} = J$$

i.e., the expected cost of filling a vacancy (cost per period divided by the probability of filling it, giving expected total posting cost) equals the value of a filled job. This equation is the demand-side analog of a firm's optimality condition and pins down one relationship between $\theta$ and the wage.

### Wage Determination: Nash Bargaining

Wages in the DMP model are not set unilaterally by firms (as in monopsony) nor determined by a Walrasian auctioneer, but instead determined via **generalized Nash bargaining** between the matched worker and firm over the surplus created by the match, with worker bargaining power $\beta \in (0,1)$:

$$w = \arg\max_{w} (W - U_{val})^{\beta} (J - V_{vac})^{1-\beta}$$

where $W$ is the value of being employed at wage $w$ and $U_{val}$ is the value of unemployment. The first-order condition of this bargaining problem yields the **wage curve**:

$$W - U_{val} = \beta \cdot (J - V_{vac} + W - U_{val})$$

which, combined with the surplus-splitting logic, produces the well-known reduced-form wage equation:

$$w = \beta(z + c\theta) + (1-\beta) b$$

**Key Points**

- Here $z$ denotes worker productivity, $b$ is the flow value of unemployment (leisure/home production plus UI benefits, as in the McCall model), and $c\theta$ is a term capturing the value of the firm's outside option (the cost savings from not having to keep searching, scaled by market tightness). [Note: exact algebraic form of the wage equation varies slightly across textbook presentations depending on discounting and separation-rate assumptions — the qualitative structure (a weighted average of productivity and the unemployment flow value, weighted by bargaining power) is the standard, well-established result.]
- Higher worker bargaining power $\beta$ shifts more of the match surplus to the worker, raising wages for any given $\theta$.
- Higher market tightness $\theta$ raises wages through the $c\theta$ term, reflecting that a tighter labor market improves the firm's outside-option cost of continued vacancy-posting, which under Nash bargaining translates into higher equilibrium wages — this is the theoretical microfoundation for procyclical wage behavior in the model.

### Equilibrium Determination: The Beveridge Curve and Job Creation Curve

Combining the job creation condition (from free entry) with the Nash bargaining wage equation yields a single equation in $\theta$ alone, pinning down the equilibrium market tightness. Graphically, equilibrium is often depicted at the intersection of:

- **The Beveridge curve**: The steady-state relationship between unemployment $u$ and vacancies $v$ implied by the flow-balance condition (inflow into unemployment from job destruction equals outflow via job-finding), typically downward-sloping in $(u,v)$ space.
- **The job creation curve**: The locus of $(u,v)$ combinations consistent with the free-entry zero-profit condition for firms, typically depicted as an upward-sloping ray from the origin in $(u,v)$ space (since $\theta = v/u$ is pinned down as a single equilibrium value).

The steady-state unemployment rate satisfies the flow-balance (Beveridge) condition:

$$s(1-u) = f(\theta) \cdot u$$

where $s$ is the exogenous job separation rate. Solving for $u$:

$$u = \frac{s}{s + f(\theta)}$$

**Example**

Suppose the monthly job separation rate is $s = 0.03$ (3% of employed workers separate each month) and, given the equilibrium market tightness $\theta$, the job-finding rate is $f(\theta) = 0.45$ (45% of unemployed workers find jobs each month — a figure broadly in the range of typical U.S. estimates). Then steady-state unemployment is:

$$u = \frac{0.03}{0.03 + 0.45} = \frac{0.03}{0.48} \approx 0.0625$$

implying a steady-state unemployment rate of roughly 6.25%, illustrating how the model maps two flow parameters (separation and finding rates) directly into the stock unemployment rate — the fundamental flow-accounting identity underlying virtually all subsequent applied DMP work.

### Mermaid Diagram: DMP Model Equilibrium Structure

```mermaid
flowchart TD
    A[Firms post vacancies V] --> C[Matching function M = m of U,V]
    B[Unemployed workers search U] --> C
    C --> D[Job-finding rate f of theta = M/U]
    C --> E[Vacancy-filling rate q of theta = M/V]
    D --> F[Flow into employment]
    E --> G[Firm free-entry condition: c/q of theta = J]
    F --> H[Nash bargaining over match surplus]
    G --> H
    H --> I[Equilibrium wage w]
    I --> J[Value of filled job J]
    J --> G
    F --> K[Steady-state unemployment: u = s / (s + f of theta)]
```

### The Hosios Condition and Efficiency

**Key Points**

- Search externalities in the DMP model create a potential wedge between the decentralized equilibrium and the socially efficient allocation: each additional searcher makes it marginally harder for other searchers to find jobs (congestion externality on workers), and each additional vacancy makes it marginally harder for other vacancies to be filled (congestion externality on firms), while simultaneously each side's search effort generates a positive externality on the other side (a searching worker helps some firm fill its vacancy).
- The **Hosios condition** (Hosios, 1990) states that the decentralized equilibrium is constrained-efficient if and only if the worker's Nash bargaining power $\beta$ equals the matching function's elasticity of matches with respect to unemployment, $\alpha$ (i.e., $\beta = \alpha$ under the Cobb-Douglas matching function above).
- When $\beta \neq \alpha$, the equilibrium features either excessive or insufficient vacancy creation relative to the social optimum, providing a theoretical rationale for labor market policy interventions (hiring subsidies, UI-financed search subsidies) calibrated to restore efficiency — though whether real-world $\beta$ and $\alpha$ satisfy Hosios is an empirical question without a clean consensus answer. [Inference — empirical estimates of both parameters are imprecise enough that testing Hosios directly is difficult in practice]

### The "Unemployment Volatility Puzzle" (Shimer Puzzle)

**Key Points**

- Shimer (2005) documented that the standard calibrated DMP model, when subjected to empirically realistic labor productivity shocks, generates far less volatility in unemployment and vacancies than observed in U.S. data — the model's predicted cyclical amplification is an order of magnitude too small relative to the data, a finding now commonly called the **Shimer puzzle** or unemployment volatility puzzle.
- The core mechanical reason is that under standard Nash bargaining calibrations, wages are highly flexible and absorb most of a productivity shock, leaving little of the shock to pass through into the firm's vacancy-posting incentive (since the job creation condition depends on the *surplus* $J$, which barely moves if wages track productivity closely).
- **Proposed resolutions** include: Hall (2005) and Hall and Milgrom (2008) proposing wage rigidity (rule-of-thumb or alternating-offer bargaining rather than static Nash bargaining) to dampen wage responsiveness and amplify vacancy responses; Hagedorn and Manovskii (2008) recalibrating the flow value of unemployment $b$ to be much closer to productivity $z$ (raising the "profitability" sensitivity of the surplus to productivity shocks); and various search-and-matching extensions incorporating fixed matching costs, on-the-job search, or endogenous separation. [Inference — no single resolution has become the unambiguous consensus; the calibration debate over $b/z$ remains actively contested in the literature]

### Extensions and Applications

- **Endogenous job destruction**: Mortensen and Pissarides (1994) extend the baseline model to allow firms to endogenously destroy matches when idiosyncratic productivity falls below an endogenously determined reservation productivity threshold, generating a richer theory of job destruction alongside job creation.
- **On-the-job search**: Incorporating employed-worker search (connecting to Burdett-Mortensen-style wage-posting) generates job-to-job transitions and a richer wage-tenure/wage-dispersion structure within the DMP framework.
- **Directed search**: An alternative to random matching, directed search models (Moen, 1997; Shi, 2001) have workers and firms coordinate via posted wages/prices that direct search, generating competitive-search equilibria that automatically satisfy an efficiency condition analogous to Hosios without requiring the coincidental parameter restriction.
- **New Keynesian DSGE integration**: DMP-style labor market frictions have been incorporated into medium-scale New Keynesian DSGE models (e.g., the Smets-Wouters tradition extended with search frictions) used for monetary policy analysis, connecting labor search theory directly to central bank macro modeling practice.
- **Sectoral and multi-sector extensions**: Extending the matching framework to allow for occupation- or sector-specific matching functions and mismatch, used to study the "mismatch unemployment" channel (e.g., Şahin, Song, Topa, and Violante, 2014) that decomposes how much of cyclical unemployment reflects aggregate demand shortfall versus allocative mismatch across sectors.

### Empirical Calibration and Estimation

**Key Points**

- Matching function elasticities ($\alpha$) are typically estimated via aggregate or regional time-series regressions of hires on unemployment and vacancy stocks; estimates commonly cluster around $\alpha \approx 0.5$ to $0.7$ for the U.S., though estimates vary by data source (JOLTS-based vacancy data versus help-wanted-index-based historical proxies) and time period. [Inference — precise elasticity estimates are sensitive to specification and sample period, and there is no single universally agreed value]
- Discount-rate, separation-rate, and bargaining-power parameters are typically calibrated from steady-state moments (average unemployment duration, job-to-job flow rates, labor share of income) rather than estimated via a single reduced-form regression, following standard DSGE calibration practice.
- The JOLTS (Job Openings and Labor Turnover Survey) dataset, published by the U.S. Bureau of Labor Statistics beginning in 2000, is the primary modern empirical counterpart to the model's vacancy stock $V$, enabling direct construction of empirical Beveridge curves and market tightness measures ($V/U$) for U.S. labor market analysis.

### Related Topics

- The McCall Search Model and Optimal Stopping
- Burdett-Mortensen Equilibrium Search and Wage Dispersion
- The Beveridge Curve and Labor Market Tightness
- The Shimer Puzzle and Wage Rigidity in Search Models
- Endogenous Job Destruction and Match Quality
- Directed Search and Competitive Search Equilibrium
- Mismatch Unemployment and Sectoral Reallocation
- New Keynesian DSGE Models with Search Frictions