## Components of Aggregate Demand


### Overview

**Aggregate demand (AD)** is the total quantity of domestically produced goods and services demanded across the economy at a given price level, over a given period. In the standard national-income accounting framework used in the goods-market (IS-side) building block of macroeconomics, aggregate demand is decomposed into four expenditure components, corresponding directly to the expenditure approach to GDP measurement:

$$Y^d = C + I + G + NX$$

where $Y^d$ is aggregate demand, $C$ is consumption, $I$ is investment, $G$ is government spending, and $NX = X - M$ is net exports (exports minus imports). This identity is the foundation for the **Keynesian cross**, the **IS curve**, and subsequent AD-AS analysis.

---

### The Aggregate Demand Identity

$$AD = C + I + G + (X - M)$$

**Key Points**

- This is an accounting identity in the sense that it defines how total planned expenditure is partitioned by *purchaser type* (households, firms, government, foreign sector), not a behavioral theory in itself.
- Each component has its own behavioral determinants (discussed below), and the interaction of these behavioral relationships is what generates the **IS curve** and Keynesian-cross equilibrium.
- In equilibrium, planned aggregate expenditure equals actual output: $Y = AD$. Disequilibrium (planned spending ≠ output) triggers unplanned inventory changes that push output toward equilibrium.

---

### Component 1: Consumption ($C$)

Consumption is spending by households on final goods and services (durable goods, non-durable goods, and services) and is typically the **largest component of AD** in most economies (roughly 55–70% of GDP in most advanced economies).

**Keynesian consumption function:**

$$C = C_0 + c(Y - T)$$

where:

- $C_0$ is **autonomous consumption** (consumption independent of current disposable income, e.g., financed by borrowing or dissaving)
- $c$ is the **marginal propensity to consume (MPC)**, $0 < c < 1$, the fraction of an additional unit of disposable income spent on consumption
- $Y - T$ is **disposable income** ($T$ = net taxes)

The **marginal propensity to save (MPS)** is $s = 1 - c$, since disposable income is either consumed or saved.

**Extensions and refinements** (typically covered in more advanced treatments):

- **Permanent Income Hypothesis** (Friedman, 1957): consumption depends on *permanent* (long-run expected) income rather than current income, implying smoother consumption responses to transitory income shocks.
- **Life-Cycle Hypothesis** (Modigliani and Brumberg, 1954): individuals smooth consumption over their lifetime, borrowing when young, saving during peak-earning years, and dissaving in retirement.
- **Wealth effects**: consumption also responds to household net wealth (housing, equity portfolios), not disposable income alone.

---

### Component 2: Investment ($I$)

Investment is spending by firms on **capital goods** that expand or maintain the economy's productive capacity, plus changes in inventories and residential construction. It is the **most volatile** component of AD, driving much of the business cycle.

**Categories of investment** (national accounts classification):

- **Business fixed investment**: machinery, equipment, structures, software/IP
- **Residential investment**: new housing construction
- **Inventory investment**: changes in firms' stocks of unsold goods (can be negative)

**Simple investment function:**

$$I = I_0 - b \cdot r$$

where $I_0$ is autonomous investment (driven by "animal spirits," expected future profitability), $r$ is the real interest rate, and $b > 0$ captures the sensitivity of investment to the cost of capital. Investment is **inversely related to the interest rate**: higher $r$ raises the cost of borrowing to finance capital projects and raises the opportunity cost of using retained earnings, reducing the number of profitable projects.

**Determinants of investment beyond the interest rate:**

- Business confidence and expected future demand (accelerator effects)
- Corporate tax policy and depreciation allowances
- Availability of credit / financial conditions
- Capacity utilization (firms operating near full capacity are more likely to invest in expansion)

$$\frac{\partial I}{\partial r} < 0$$

This negative relationship between investment and the interest rate is the primary channel through which monetary policy affects aggregate demand, and is the microfoundation of the **downward-sloping IS curve**.

---

### Component 3: Government Spending ($G$)

Government spending comprises government purchases of goods and services — public sector wages, infrastructure, defense, and public service provision. It **excludes transfer payments** (unemployment benefits, social security, subsidies), which are not purchases of goods/services but redistributions of income, and instead enter the model indirectly by affecting disposable income $Y - T$ (where $T$ is often modeled as *net* taxes, i.e., taxes minus transfers).

**Modeling assumption**: $G$ is typically treated as an **exogenous policy variable** set by fiscal authorities, i.e., $G = \bar{G}$, independent of current income $Y$ — reflecting that government spending decisions are set through the budgetary/legislative process rather than mechanically responding to national income in the short run.

**Fiscal policy role**: $G$ is a direct lever of **discretionary fiscal policy** — governments can raise or lower $G$ to shift aggregate demand, forming the basis of countercyclical stabilization policy.

---

### Component 4: Net Exports ($NX = X - M$)

Net exports capture the **foreign sector's** contribution to domestic aggregate demand:

- **Exports ($X$)**: foreign demand for domestically produced goods — this adds to AD for the domestic economy.
- **Imports ($M$)**: domestic demand for foreign-produced goods — this must be *subtracted* because $C$, $I$, and $G$ as measured in the national accounts include spending on imported goods, but that spending does not represent demand for *domestic* output.

**Behavioral determinants:**

$$M = M_0 + m(Y - T), \qquad 0 < m < 1$$

Imports rise with domestic disposable income (the **marginal propensity to import**, $m$), since richer households and firms buy more of everything, including foreign goods.

$$X = X_0(Y^*, \epsilon)$$

Exports depend on **foreign income** $Y^*$ (foreign demand for domestic goods) and the **real exchange rate** $\epsilon$ (competitiveness): a real depreciation ($\epsilon$ falls, i.e., domestic goods become cheaper relative to foreign goods) tends to raise exports and reduce imports, improving $NX$ — the basis of the **Marshall-Lerner condition** and expenditure-switching effects in open-economy macro.

$$NX = X_0(Y^*, \epsilon) - M_0 - m(Y - T)$$

Net exports are **decreasing in domestic income** $Y$ (via the import channel) and generally **increasing in foreign income** $Y^*$ and in a real depreciation.

---

### Autonomous vs. Induced Spending

**Key Points**

- **Autonomous spending**: the portion of each component that does *not* depend on current income — $C_0$, $I_0$ (net of interest-rate effects), $\bar{G}$, $X_0$, $-M_0$. Collectively:

$$A = C_0 + I_0 + \bar{G} + X_0 - M_0$$

- **Induced spending**: the portion that varies systematically with income — $c(Y-T)$ in consumption, $-m(Y-T)$ in net exports (via imports).

This distinction underlies the **expenditure multiplier**, since a change in autonomous spending triggers a chain of induced spending responses through the circular flow of income.

---

### The Aggregate Demand Function and the Multiplier

Combining the behavioral equations (holding $I$ fixed at $I_0$ for the basic closed-economy case, or including the open-economy import leakage):

$$AD = \underbrace{(C_0 + I_0 + \bar{G} + X_0 - M_0 - cT)}_{\text{autonomous spending}} + \underbrace{(c - m)Y}_{\text{induced spending}}$$

Equilibrium output solves $Y = AD$:

$$Y^* = \frac{1}{1-(c-m)} \left[C_0 + I_0 + \bar{G} + X_0 - M_0 - cT\right]$$

The term $\dfrac{1}{1-(c-m)}$ is the **open-economy expenditure multiplier** — larger than 1 (assuming $c > m$, i.e., some spending stays domestic), but smaller than the closed-economy multiplier $\frac{1}{1-c}$ because import leakage ($m$) dampens the multiplier's second-round effects.

**Example**: If $c = 0.8$ and $m = 0.2$, the multiplier is $\frac{1}{1-(0.8-0.2)} = \frac{1}{0.4} = 2.5$. A $100 billion increase in autonomous investment ($I_0$) raises equilibrium output by $250 billion, as the initial spending circulates through wages and profits, generating successive rounds of induced consumption (net of the portion spent on imports, which leaks out of the domestic circular flow).

---

### The Keynesian Cross

**(svg_diagram)**

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 480" font-family="Helvetica, Arial, sans-serif">
<text x="350" y="26" text-anchor="middle" font-size="17" font-weight="bold" fill="#1a1a1a">The Keynesian Cross: AD = Y Equilibrium (svg_diagram)</text>
<line x1="70" y1="420" x2="650" y2="420" stroke="#1a1a1a" stroke-width="2" />
<line x1="70" y1="420" x2="70" y2="50" stroke="#1a1a1a" stroke-width="2" />
<text x="660" y="425" font-size="13" fill="#1a1a1a">Output, Income (Y)</text>
<text x="20" y="45" font-size="13" fill="#1a1a1a">Planned</text>
<text x="10" y="60" font-size="13" fill="#1a1a1a">Expenditure (AD)</text>
<line x1="70" y1="420" x2="600" y2="70" stroke="#666" stroke-width="1.5" stroke-dasharray="5,3" />
<text x="605" y="70" font-size="12" fill="#666">45° line (AD = Y)</text>
<line x1="70" y1="330" x2="600" y2="120" stroke="#1d4ed8" stroke-width="2.5" />
<text x="610" y="118" font-size="12" fill="#1d4ed8" font-weight="bold">AD = C+I+G+NX</text>
<line x1="70" y1="220" x2="600" y2="10" stroke="#1d4ed8" stroke-width="2.5" stroke-dasharray="6,3" />
<text x="480" y="30" font-size="12" fill="#1d4ed8" font-weight="bold">AD' (after ΔI₀ &gt; 0)</text>
<line x1="320" y1="420" x2="320" y2="204" stroke="#b91c1c" stroke-dasharray="3,3" stroke-width="1.5" />
<line x1="70" y1="204" x2="320" y2="204" stroke="#b91c1c" stroke-dasharray="3,3" stroke-width="1.5" />
<circle cx="320" cy="204" r="6" fill="#b91c1c" />
<text x="300" y="440" font-size="12" fill="#1a1a1a">Y₀</text>
<line x1="480" y1="420" x2="480" y2="90" stroke="#7e22ce" stroke-dasharray="3,3" stroke-width="1.5" />
<line x1="70" y1="90" x2="480" y2="90" stroke="#7e22ce" stroke-dasharray="3,3" stroke-width="1.5" />
<circle cx="480" cy="90" r="6" fill="#7e22ce" />
<text x="460" y="440" font-size="12" fill="#1a1a1a">Y₁</text>

<text x="330" y="460" font-size="11" fill="`#1a1a1a`" font-style="italic">ΔY = Y₁ − Y₀ &gt; ΔI₀ (multiplier effect, slope = c−m)</text>

</svg>

The equilibrium level of output occurs where the **AD line** (with slope $c - m$, flatter than the 45° line since $0 < c-m < 1$) intersects the **45° line** representing $AD = Y$. A rise in any autonomous component shifts the AD line upward, and the new equilibrium output rises by *more* than the initial spending injection — the multiplier effect.

---

### Aggregate Demand and the Price Level (Link to AD-AS Framework)

While the Keynesian-cross/IS treatment above holds the price level fixed, the same expenditure components underlie the downward-sloping **AD curve** in $(Y, P)$ space used in short-run AD-AS analysis. A higher price level $P$ reduces AD through three standard channels:

- **Real balance (Pigou/wealth) effect**: higher $P$ reduces the real value of money holdings, reducing $C$.
- **Interest rate (Keynes) effect**: higher $P$ raises money demand for a given nominal money supply, raising $r$, which reduces $I$.
- **Exchange rate (Mundell-Fleming) effect**: higher $P$ makes domestic goods relatively more expensive, appreciating the real exchange rate and reducing $NX$.

$$P \uparrow \Rightarrow C\downarrow, I \downarrow, NX \downarrow \Rightarrow AD \downarrow$$

This is distinct from *shifts* in the AD curve (caused by changes in autonomous $C_0, I_0, \bar{G}, T, X_0$, or the money supply), which move the entire curve rather than tracing movement along it.

---

### Distinguishing Shifts vs. Movements Along AD

| Change | Effect |
| --- | --- |
| Change in price level $P$ | Movement **along** the AD curve |
| Change in $\bar{G}$, $T$ (fiscal policy) | **Shifts** AD curve |
| Change in money supply / interest rate policy (monetary policy) | **Shifts** AD curve |
| Change in consumer/business confidence ($C_0$, $I_0$) | **Shifts** AD curve |
| Change in foreign income $Y^*$ or exchange rate $\epsilon$ | **Shifts** AD curve |

---

### Related Topics

- The Keynesian cross and derivation of the expenditure multiplier
- Deriving the IS curve from the goods-market equilibrium condition
- The Marshall-Lerner condition and expenditure-switching in open economies
- Permanent Income and Life-Cycle Hypotheses of consumption
- The accelerator model and investment volatility over the business cycle
- Automatic stabilizers and the role of net taxes $T$ in dampening the multiplier
- The IS-LM model and joint goods-money market equilibrium
- Short-run AD-AS framework and the distinction between demand-side and supply-side shocks
- Mundell-Fleming model: AD determination under fixed vs. floating exchange rates