## Setup of the Specific Factors Model

### Overview

The specific factors model (also called the Ricardo-Viner model, after Jacob Viner's early formulation and its later development by Jones (1971) and Samuelson (1971)) is an intermediate-run trade model that sits between the Ricardian model (all factors mobile) and the long-run Heckscher-Ohlin model (all factors mobile across sectors). Its defining feature is that some factors are **specific** (immobile, sector-locked) while one factor is **mobile** across sectors. This structure makes it especially useful for analyzing the short- and medium-run income-distribution effects of trade, since factor owners in different sectors are affected asymmetrically by price changes — unlike in H-O, where the *type* of factor (not the sector) determines gains and losses.

### Core Assumptions

**Key Points**

1. **Two goods**: The economy produces two goods, conventionally labeled $X$ (e.g., manufactures) and $Y$ (e.g., agriculture/food).
2. **Three factors**:
   - **Labor ($L$)**: mobile across both sectors, the single mobile factor.
   - **Capital ($K$)**: specific to sector $X$ (cannot move to sector $Y$).
   - **Land ($T$)**: specific to sector $Y$ (cannot move to sector $X$).
3. **Fixed total factor supplies**: $\bar{L}$, $\bar{K}$, $\bar{T}$ are exogenously given and fully employed.
4. **Perfect competition**: in both goods and factor markets.
5. **Constant returns to scale** production functions in each sector, with diminishing marginal returns to the mobile factor holding the specific factor fixed.
6. **Small open economy** (in the standard trade-theoretic version): goods prices $p_X$, $p_Y$ are taken as given by world markets (though the model is often first developed in closed-economy form to establish the wage/rent determination mechanics before introducing trade).

### Production Functions

$$Q_X = F(K, L_X)$$



$$Q_Y = G(T, L_Y)$$

where $L_X$ and $L_Y$ are the labor allocated to sectors $X$ and $Y$ respectively, subject to the full-employment constraint:

$$L_X + L_Y = \bar{L}$$

Both $F$ and $G$ exhibit:

- **Positive but diminishing marginal product of labor**: $\frac{\partial F}{\partial L_X} > 0$, $\frac{\partial^2 F}{\partial L_X^2} < 0$ (and analogously for $G$)
- **Constant returns to scale** in the two arguments jointly (so doubling both $K$ and $L_X$ doubles $Q_X$), which combined with a fixed specific factor implies diminishing returns to the variable factor alone.

### Profit Maximization and Labor Demand

Firms in each sector are price-takers in both output and labor markets. Sector $X$ maximizes:

$$\pi_X = p_X F(K, L_X) - w L_X - r_K K$$

where $w$ is the economy-wide wage and $r_K$ is the return to capital. The first-order condition for labor demand in sector $X$:

$$p_X \cdot \frac{\partial F}{\partial L_X} = w$$

Similarly for sector $Y$:

$$p_Y \cdot \frac{\partial G}{\partial L_Y} = w$$

These conditions state that each sector hires labor up to the point where the **value of the marginal product of labor (VMPL)** equals the common economy-wide wage $w$. Because labor is the mobile factor, a single wage $w$ must prevail in both sectors in equilibrium (no incentive to reallocate labor otherwise).

### Diagrammatic Representation (Description)

The standard specific-factors diagram plots the two sectors' VMPL curves against each other in a "back-to-back" box of total width $\bar{L}$:

- Horizontal axis: total labor $\bar{L}$, measured from left (origin for sector $X$) to right (origin for sector $Y$)
- Left vertical axis: $p_X \cdot MPL_X$, sector $X$'s value-marginal-product-of-labor curve, downward sloping (diminishing returns) as $L_X$ increases from the left origin
- Right vertical axis (equivalently, measured leftward from the right origin): $p_Y \cdot MPL_Y$, downward sloping as $L_Y$ increases (i.e., as we move leftward from the right origin)
- Equilibrium: the wage $w$ and labor allocation $(L_X^*, L_Y^*)$ occur where the two VMPL curves intersect — this point simultaneously clears the labor market ($L_X + L_Y = \bar{L}$) and equalizes the wage across sectors.

**Illustration (SVG, back-to-back VMPL diagram)**

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 420">
<text x="350" y="24" font-size="16" text-anchor="middle" fill="#1a1a1a" font-family="sans-serif" font-weight="bold">Specific Factors Model: Labor Allocation (svg_diagram)</text>

<line x1="80" y1="360" x2="620" y2="360" stroke="#333" stroke-width="2" />
<line x1="80" y1="360" x2="80" y2="60" stroke="#333" stroke-width="2" />
<line x1="620" y1="360" x2="620" y2="60" stroke="#333" stroke-width="2" />


<text x="80" y="385" font-size="13" text-anchor="middle" font-family="sans-serif">O_X (L_X = 0)</text>

<text x="620" y="385" font-size="13" text-anchor="middle" font-family="sans-serif">O_Y (L_Y = 0)</text>

<text x="350" y="405" font-size="13" text-anchor="middle" font-family="sans-serif">Total Labor L̄ (L_X increases →, L_Y increases ←)</text>

<text x="55" y="200" font-size="13" text-anchor="middle" font-family="sans-serif" transform="rotate(-90 55 200)">p_X · MPL_X</text>

<text x="655" y="200" font-size="13" text-anchor="middle" font-family="sans-serif" transform="rotate(90 655 200)">p_Y · MPL_Y</text>


<path d="M 80 90 Q 250 110 400 220" stroke="#2563eb" stroke-width="3" fill="none" />
<text x="200" y="105" font-size="12" fill="#2563eb" font-family="sans-serif">VMPL_X curve</text>

<path d="M 620 90 Q 450 110 400 220" stroke="#dc2626" stroke-width="3" fill="none" />
<text x="470" y="105" font-size="12" fill="#dc2626" font-family="sans-serif">VMPL_Y curve</text>

<circle cx="400" cy="220" r="5" fill="#16a34a" />
<line x1="400" y1="220" x2="400" y2="360" stroke="#16a34a" stroke-width="1.5" stroke-dasharray="4,3" />
<line x1="80" y1="220" x2="400" y2="220" stroke="#16a34a" stroke-width="1.5" stroke-dasharray="4,3" />
<text x="400" y="245" font-size="12" text-anchor="middle" fill="#16a34a" font-family="sans-serif" font-weight="bold">E (equilibrium)</text>
<text x="60" y="215" font-size="12" text-anchor="end" fill="#16a34a" font-family="sans-serif">w*</text>
<text x="400" y="378" font-size="12" text-anchor="middle" fill="#16a34a" font-family="sans-serif">L_X*</text>


<text x="200" y="340" font-size="12" text-anchor="middle" fill="#666" font-family="sans-serif">Sector X employment (L_X)</text>

<text x="510" y="340" font-size="12" text-anchor="middle" fill="#666" font-family="sans-serif">Sector Y employment (L_Y)</text>

</svg>

### Returns to the Specific Factors

Given the equilibrium wage $w^*$, the returns to the specific factors are determined as **residuals** from each sector's zero-profit (or, under CRS with pure competition, exhausted-product) condition:

$$r_K = \frac{p_X Q_X - w^* L_X^*}{K} = p_X \cdot \frac{\partial F}{\partial K}$$



$$r_T = \frac{p_Y Q_Y - w^* L_Y^*}{T} = p_Y \cdot \frac{\partial G}{\partial T}$$

Because $K$ and $T$ are fixed and sector-specific, their returns are **residual claimants** on sector revenue after paying the mobile factor its economy-wide wage — this is the structural reason their real returns respond differently to price shocks than the mobile factor's wage does.

### Comparison to Ricardian and Heckscher-Ohlin Models

| Feature | Ricardian | Specific Factors | Heckscher-Ohlin |
| --- | --- | --- | --- |
| Number of factors | 1 (labor) | 3 (labor + 2 specific factors) | 2 (fully mobile) |
| Factor mobility | Fully mobile | 1 mobile, 2 specific | Fully mobile (long run) |
| Time horizon | N/A (single factor) | Short/medium run | Long run |
| Source of comparative advantage | Technology differences | Endowments of specific factors + technology | Factor endowments |
| Income distribution effect of trade | None (single factor, all gain) | Sector-specific: specific-factor owners in export sector gain, in import sector lose; mobile factor's effect is ambiguous | Factor-specific: owners of abundant factor gain, scarce factor lose (Stolper-Samuelson) |

### Full Employment and Resource Constraints (Summary)

$$L_X + L_Y = \bar{L}, \qquad K = \bar{K} \text{ (fixed to sector } X\text{)}, \qquad T = \bar{T} \text{ (fixed to sector } Y\text{)}$$

These three constraints, together with the two labor-demand (VMPL-equalization) conditions, fully determine the equilibrium allocation $(L_X^*, L_Y^*)$, wage $w^*$, and specific-factor returns $(r_K^*, r_T^*)$ for given goods prices $(p_X, p_Y)$.

### Why the Model Matters for Trade Analysis

**Key Points**

- The specific factors setup is the natural framework for analyzing the **short-run** effects of a trade liberalization or price shock, before capital and land have had time to reallocate across sectors (which is the long-run H-O adjustment).
- It generates **sector-based**, not **factor-type-based**, distributional conflict: e.g., under an import-competing price decline, capital owners in the import-competing sector unambiguously lose in real terms, while landowners in the export sector unambiguously gain — labor's welfare change is ambiguous and depends on labor's consumption basket.
- This is frequently used to explain real-world political economy of trade: industry-specific lobbying (e.g., steel producers, textile producers) is often better explained by the specific-factors logic (owners of sector-specific capital have a direct stake in that sector's price) than by the factor-type logic of H-O/Stolper-Samuelson.

### Next Steps

- Comparative statics: effects of a change in relative goods prices ($p_X/p_Y$) on wages and specific-factor returns
- Comparative statics: effects of an increase in the specific factor endowment (analogue of Rybczynski in this model)
- Real wage effects and the ambiguity of labor's welfare outcome
- The magnification effect within the specific factors model
- Long-run convergence: how the specific factors model transitions to Heckscher-Ohlin as capital becomes mobile
- Political economy applications: lobbying, trade policy formation, and the specific factors model