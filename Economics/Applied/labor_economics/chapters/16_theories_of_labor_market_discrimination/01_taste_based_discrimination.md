## Taste-Based Discrimination


### Definition and Origin

Taste-based discrimination is a theory of labor market discrimination originating with Gary Becker's 1957 monograph *The Economics of Discrimination*. In this framework, discrimination arises not from informational asymmetries or productivity differences but from a **subjective preference (a "taste")** on the part of an economic agent — an employer, a coworker, or a customer — for avoiding association with members of a particular group. This "taste" is modeled formally as if it were a real cost, entering the agent's utility or profit function as a disutility term, even though it generates no direct pecuniary cost to the discriminated-against worker's actual productivity.

Becker's central and most provocative claim is that **discrimination is economically costly to the discriminator**, and that under competitive markets, taste-based discrimination should erode over time as non-discriminating firms out-compete discriminating ones. This prediction — that markets punish prejudice — remains one of the most tested and debated propositions in labor economics.

### The Discrimination Coefficient (DC)

Becker formalizes prejudice using a **discrimination coefficient**, denoted $d$, which represents the monetary value of the disutility an agent experiences from association with the disfavored group. The discriminating employer behaves *as if* the wage paid to a worker from the disfavored group is higher than the actual wage by the amount of this coefficient.

For an employer with discrimination coefficient $d_E \geq 0$ against group $B$ workers (relative to group $A$), the employer's **subjective cost** of hiring a group $B$ worker at market wage $w_B$ is:

$$w_B(1 + d_E)$$

The employer will hire group $B$ workers only if:

$$w_B(1 + d_E) \leq w_A$$

Equivalently, the employer requires a wage discount for group $B$ workers proportional to $d_E$:

$$w_B \leq \frac{w_A}{1 + d_E}$$

A non-discriminating employer has $d_E = 0$ and is indifferent between equally productive workers regardless of group, hiring strictly on the basis of $w_A$ versus $w_B$.

### Employer Discrimination Model

**Setup**: Assume two groups of workers, $A$ and $B$, who are perfect substitutes in production (identical marginal productivity, $MP_A = MP_B$). A profit-maximizing but prejudiced employer treats the two groups asymmetrically.

The firm's effective marginal cost of group $B$ labor is $w_B(1+d_E)$, so the firm equates:

$$MP_A = w_A \quad \text{and} \quad MP_B = w_B(1 + d_E)$$

Since $MP_A = MP_B$ by assumption, in equilibrium:

$$w_A = w_B(1 + d_E) \implies w_B = \frac{w_A}{1 + d_E}$$

This yields the central testable prediction: **the observed wage gap between groups reflects the magnitude of the discrimination coefficient**, not any underlying productivity difference. A firm with $d_E = 0$ earns strictly higher profits than a firm with $d_E > 0$ if both face the same wage-setting options, because the discriminating firm either (a) pays a premium to hire preferred workers or (b) forgoes the productivity of equally capable group $B$ workers at a discount, foreclosing an available profit opportunity if group $B$ workers are willing to work at $w_B < w_A$.

### Market-Level Sorting and the "Non-Discriminator's Advantage"

In a market with heterogeneous employer prejudice, Becker's model predicts an **equilibrium sorting** of workers to firms based on employer discrimination coefficients, ranked from least to most prejudiced ($d_{E,1} < d_{E,2} < \ldots < d_{E,n}$):

- Firms with $d_E = 0$ hire group $B$ workers freely whenever $w_B < w_A$, capturing a cost advantage.
- Firms with progressively higher $d_E$ require progressively larger wage discounts to hire group $B$ workers.
- In long-run competitive equilibrium, non-discriminating firms should **expand market share** relative to discriminating firms, since they access the same labor at lower effective cost. This is the mechanism behind Becker's prediction that **competition erodes discrimination** over time — a discriminating firm is, in effect, "purchasing" its prejudice at a cost to profit, and firms that decline to pay this cost outcompete it.

### Formal Wage-Gap Equilibrium Diagram (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 380">
<text x="320" y="24" text-anchor="middle" font-size="15" font-weight="bold" fill="#1a1a1a">Employer Taste Discrimination: Wage Gap Equilibrium (svg_diagram)</text>
<line x1="80" y1="320" x2="580" y2="320" stroke="#333" stroke-width="1.5" />
<line x1="80" y1="320" x2="80" y2="50" stroke="#333" stroke-width="1.5" />
<text x="330" y="350" text-anchor="middle" font-size="12" fill="#333">Employers ranked by discrimination coefficient d_E (low to high)</text>
<text x="35" y="185" text-anchor="middle" font-size="12" fill="#333" transform="rotate(-90 35 185)">Wage paid to Group B</text>

<line x1="80" y1="90" x2="580" y2="90" stroke="#264653" stroke-width="1.5" stroke-dasharray="6,3" />
<text x="585" y="94" font-size="10" fill="#264653">w_A (market wage)</text>

<path d="M 80 100 Q 250 150 400 230 Q 500 280 580 310" fill="none" stroke="#d64550" stroke-width="2.5" />
<text x="585" y="310" font-size="10" fill="#d64550">w_B(1+d_E)=w_A</text>


<text x="140" y="130" font-size="10" fill="`#2b7a78`">Low-d_E firms:</text>

<text x="140" y="143" font-size="10" fill="`#2b7a78`">hire Group B near w_A</text>

<text x="420" y="270" font-size="10" fill="`#d64550`">High-d_E firms:</text>

<text x="420" y="283" font-size="10" fill="`#d64550`">require large wage discount,</text>

<text x="420" y="296" font-size="10" fill="`#d64550`">or refuse to hire Group B</text>

<circle cx="180" cy="112" r="4" fill="#2b7a78" />
<circle cx="380" cy="220" r="4" fill="#f2a541" />
<circle cx="540" cy="300" r="4" fill="#d64550" />

<text x="330" y="365" text-anchor="middle" font-size="9" fill="#555">Non-discriminating firms access Group B labor near market wage — a cost advantage in competitive equilibrium</text>

</svg>

### Employee (Coworker) Discrimination

A second variant of Becker's model concerns discrimination by **incumbent employees** against coworkers from a disfavored group. Prejudiced workers behave as though their disutility from working alongside group $B$ colleagues must be compensated by a wage premium — a **compensating differential** for integrated work environments.

Formally, if group $A$ workers have discrimination coefficient $d_{coworker}$, they require:

$$w_A^{integrated} = w_A^{segregated}(1 + d_{coworker})$$

**Key prediction**: Employee-based discrimination, unlike employer-based discrimination, does **not** necessarily erode under competition, because it does not directly reduce the profits of a well-organized employer. A firm can accommodate coworker prejudice at zero cost to itself by **segregating** the workplace — assigning group $A$ and group $B$ workers to separate teams, shifts, or job categories that do not require direct interaction — thereby avoiding the compensating differential entirely. This yields the empirical prediction that employee-taste discrimination manifests as **occupational or task segregation within firms**, rather than as a persistent firm-level wage gap, since segregation is a lower-cost accommodation than paying a wage premium.

### Customer Discrimination

A third variant involves **discriminatory tastes among customers**, who derive disutility from being served by group $B$ workers (or, conversely, prefer group $B$ workers in specific customer-facing roles). This is modeled as customers behaving as though the effective price of a good or service is higher when delivered by a disfavored-group worker:

$$p_{effective} = p(1 + d_{customer})$$

**Key prediction — persistence**: Unlike employer discrimination, customer discrimination is predicted to be the **most persistent** form under competitive pressure, because it operates directly through firm revenue rather than firm cost. A firm cannot arbitrage away customer prejudice by hiring "cheaper" group $B$ labor, since doing so directly reduces the price customers are willing to pay or the quantity they purchase — the discriminatory cost is borne by revenue, not avoidable through input substitution. This explains the empirical prevalence of persistent segregation in customer-facing occupations (sales, service, hospitality) even in highly competitive product markets.

### Comparative Table: Three Forms of Becker Discrimination

| Source | Cost falls on | Predicted market erosion under competition | Typical empirical manifestation |
| --- | --- | --- | --- |
| Employer | Firm profit directly (self-imposed via $d_E$) | Strong — non-discriminators gain competitive cost advantage | Firm-level wage gaps; sorting of workers to non-prejudiced firms |
| Employee (coworker) | Avoided via segregation, low cost to firm | Weak/none — segregation is a cheap workaround | Within-firm occupational segregation, not wage gaps |
| Customer | Firm revenue (cannot be arbitraged away) | Weakest — operates through demand side | Persistent segregation in customer-facing roles |

### Critiques and the Competitive-Erosion Puzzle

The most significant empirical challenge to Becker's model is the observation that **discrimination and wage gaps persist over long periods even in seemingly competitive labor markets**, contrary to the model's core prediction of erosion. Several responses have been proposed in the literature:

1. **Imperfect competition / search frictions**: If labor markets exhibit monopsony-like features (search costs, limited outside options), discriminating employers can persist because non-discriminating competitors do not instantaneously bid away all mispriced labor. Search-and-matching extensions of Becker's model (in the spirit of Black (1995) and later monopsony-discrimination literature) show that with frictions, employer discrimination can persist in steady-state equilibrium without being fully competed away, since workers cannot costlessly relocate to the least-discriminatory employer.
2. **Slow adjustment / long-run vs. short-run**: Becker's prediction is explicitly a long-run competitive-equilibrium result; critics note that "long run" may be empirically very long, and observed persistence may simply reflect an incomplete adjustment process rather than a failure of the theory.
3. **Statistical discrimination as an alternative/complementary explanation**: Arrow (1973) and Phelps (1972) proposed that apparent "taste" discrimination may actually reflect **statistical discrimination** — employers using group membership as a proxy for unobserved productivity under imperfect information — which does not necessarily erode under competition since it can be a rational (non-prejudiced) response to costly information acquisition. Distinguishing taste-based from statistical discrimination empirically remains a central methodological challenge (see correspondence/audit study literature, e.g., Bertrand and Mullainathan's resume-callback studies).
4. **Behavioral and implicit bias extensions**: Some contemporary work models discriminatory tastes as arising from unconscious or automatic cognitive processes (implicit bias) rather than deliberate, rational-choice-consistent preferences, which can weaken the assumption that $d_E$ is a stable, well-defined parameter subject to standard utility-maximization logic. [Inference: the degree to which implicit-bias-driven discrimination behaves according to Becker's comparative statics is an active and unsettled area of research.]
5. **Market structure and profit non-maximization**: In markets with substantial market power (oligopoly, or firms not under intense profit pressure — e.g., some public-sector or regulated-industry employers), the cost of indulging a taste for discrimination may be absorbable without competitive consequence, weakening the erosion mechanism.

### Empirical Testing Strategies

- **Audit/correspondence studies**: Sending matched, equally qualified fictitious applicants differing only in a group-signaling characteristic (name, resume detail) to measure callback-rate gaps. These studies test for discrimination broadly but generally cannot cleanly distinguish taste-based from statistical discrimination.
- **Market structure comparisons**: Testing whether wage gaps are smaller in more competitive industries/markets, consistent with Becker's erosion prediction (e.g., studies of discrimination and product market competition, including work examining Major League Baseball wage-performance gaps by market competitiveness).
- **Firm survival and profitability tests**: Testing whether historically discriminating firms exhibit lower survival rates or profitability, as in classic studies of racial wage gaps and firm performance in the segregation-era U.S. South.
- **Customer-facing vs. non-customer-facing occupation comparisons**: Testing whether discrimination measures (wage gaps, segregation indices) are larger in customer-facing roles, consistent with the customer-discrimination persistence prediction.

### Key Points

- Taste-based discrimination (Becker, 1957) models prejudice as a subjective utility cost, quantified via the discrimination coefficient $d$.
- Employer discrimination predicts firm-level wage gaps that should erode under competition as non-discriminating firms gain a cost advantage.
- Employee (coworker) discrimination predicts occupational segregation within firms rather than wage gaps, since segregation is a low-cost accommodation.
- Customer discrimination is predicted to be the most persistent form, since it operates through revenue and cannot be arbitraged away via cheaper input substitution.
- The central empirical puzzle is the persistence of discrimination despite competitive-market predictions of erosion; search frictions, statistical discrimination, and slow long-run adjustment are the leading explanations.
- Distinguishing taste-based from statistical discrimination remains a core identification challenge in the empirical discrimination literature.

**Related Topics**

- Statistical discrimination theory (Arrow, Phelps)
- Audit and correspondence study methodology in labor economics
- Monopsony models of the labor market and discrimination persistence
- Occupational segregation indices (Duncan Dissimilarity Index)
- Compensating wage differentials theory
- Implicit bias and behavioral economics extensions to discrimination models
- Comparable worth and pay equity policy
- Human capital theory as an alternative explanation for wage gaps