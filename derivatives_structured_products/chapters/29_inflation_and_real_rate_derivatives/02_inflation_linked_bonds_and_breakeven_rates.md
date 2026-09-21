## Inflation Linked Bonds and Breakeven Rates

### Overview

Inflation-linked bonds (ILBs) are cash instruments whose principal and/or coupon payments are indexed to a reference CPI, providing direct real-return exposure. Alongside inflation swaps, they are the second pillar of the inflation market and the origin of the "breakeven inflation rate" concept — the market-implied inflation compensation extracted by comparing nominal and inflation-linked bond yields. This item covers ILB mechanics, the major global structures, and how breakeven rates are constructed and interpreted, including their divergence from swap-implied breakevens.

### ILB Structural Mechanics

**Capital-Indexed Bonds (dominant global structure — US TIPS, UK Gilts post-2005, most sovereign ILBs)**

- Principal accretes with the reference index: $\text{Adjusted Principal}(t) = N \times \dfrac{I(t)}{I(0)}$
- Coupons are paid at a fixed real coupon rate $c$ applied to the *adjusted* (inflation-accreted) principal: $\text{Coupon}(t) = c \times N \times \dfrac{I(t)}{I(0)}$
- At maturity, principal repaid is $\max\left(N \times \dfrac{I(T)}{I(0)}, N\right)$ for US TIPS (deflation floor on principal only — coupons are not floored), while some other sovereign ILBs (e.g., older UK structures) have no deflation floor at all

**Interest-Indexed Bonds (rare — some early Australian/UK structures)**

- Principal remains fixed at par; only the coupon is indexed to inflation
- Simpler but creates a "bullet" inflation-exposed redemption profile mismatch; largely superseded by capital-indexed structures

**Current Pay / Indexed Annuity Bonds**

- Used in some pension-driven markets; both coupon and amortizing principal are inflation-linked, common for LDI (liability-driven investment) matching

### Reference Index and Lag Convention

ILBs use the same lagged-index mechanics as inflation swaps (see prior item), typically a 3-month lag with daily linear interpolation:

$$I(t) = I_{m-3} + \frac{d-1}{D_m}\left(I_{m-2} - I_{m-3}\right)$$

**Key Points**

- The lag exists because current-month CPI is unknown in real time; bonds need a continuously quotable index for accrued-interest calculation
- US TIPS use a 3-month lag on CPI-U (non-seasonally-adjusted)
- UK index-linked gilts issued since 2005 use a 3-month lag on RPI (older gilts pre-2005 used an 8-month lag); post-2030 UK RPI is scheduled to be aligned methodologically with CPIH, a significant structural event for the UK linker market
- French OATi/OAT€i use a 3-month lag on French CPI ex-tobacco or Eurozone HICP ex-tobacco respectively

### The Deflation Floor

**Key Points**

- US TIPS: principal redemption is floored at the original par amount (100% of face), i.e., investors cannot receive less than par at maturity even under cumulative deflation over the bond's life — but coupons (paid on the *unfloored* adjusted principal) are not protected and can be lower in deflationary periods
- This floor has positive option value, embedded implicitly in the bond price — it is effectively a real zero-strike put on the cumulative inflation index
- The floor value is typically small for bonds issued when cumulative inflation expectations are solidly positive, but becomes economically significant for long-dated bonds issued in low/negative rate environments or during deflation scares
- **[Inference]** Pricing the deflation floor explicitly requires an option-pricing approach (e.g., under Jarrow-Yildirim or a simpler lognormal index assumption) rather than treating the bond as a simple linear real-yield instrument; desks sometimes strip this optionality out when computing "clean" real yields for curve-fitting purposes

### Real Yield and Pricing

An ILB's price (ignoring the deflation floor optionality, i.e., under simple linear real-coupon-bond math) is:

$$P(t) = \frac{I(t)}{I(0)} \times \left[\sum_{i} c \cdot DF_{real}(t, T_i) + DF_{real}(t, T_N)\right]$$

where $DF_{real}$ are real discount factors and the bracketed term is the "index-linked clean price factor" quoted in most markets (i.e., quotes are typically given as a real price, with the inflation accretion factor $I(t)/I(0)$ applied separately to get the cash "dirty"/settlement price). The **real yield** $y_{real}$ is the discount rate that equates the bracketed real cash flow stream to the quoted real price, solved analogously to a nominal bond yield-to-maturity.

### Breakeven Inflation Rate (BEI)

**Definition**

For a nominal bond and an inflation-linked bond of matching maturity $T$:

$$1 + BEI(T) \approx \frac{1+y_{nom}(T)}{1+y_{real}(T)}$$

or, in simple additive approximation for short horizons: $BEI(T) \approx y_{nom}(T) - y_{real}(T)$

This is the (approximate) average annual inflation rate over $[0,T]$ that would make an investor indifferent between holding the nominal bond and the inflation-linked bond, ignoring risk premia.

**Decomposition of Breakeven**

$$BEI(T) = \mathbb{E}[\text{Average Inflation over } [0,T]] + \text{Inflation Risk Premium}(T) + \text{Liquidity Premium}(T) + \text{Technical/Deflation-Floor Adjustment}(T)$$

**Key Points**

- **Inflation risk premium**: compensation nominal bond holders demand for bearing uncertain inflation (nominal bonds have no inflation protection); typically positive but can turn negative in periods where inflation is seen as a "bad state" hedge (i.e., when inflation and growth are negatively correlated, nominal bonds may be valued as recession hedges, compressing or inverting this premium)
- **Liquidity premium**: ILBs are typically less liquid than nominal government bonds, so ILB yields often carry a liquidity discount (higher yield) relative to a hypothetical perfectly liquid real bond — this depresses (i.e. reduces) the observed BEI relative to "true" expected inflation, since $y_{real}$ is pushed up by illiquidity
- **Deflation floor value**: embedded optionality in TIPS-style bonds adds value to the ILB (reduces its yield), which mechanically lowers computed $y_{real}$ and therefore inflates the naive BEI — this effect is most material for longer-dated bonds and during episodes of depressed inflation expectations
- **[Unverified]** The relative magnitude and even sign of the inflation risk premium is actively debated in the empirical asset-pricing literature and varies by regime, currency, and estimation methodology; no single "true" decomposition is uncontroversial

### Bond-Implied vs. Swap-Implied Breakeven: The Inflation Basis

Both cash ILBs and ZCIS produce a breakeven rate for the same maturity, but these frequently diverge — the difference is called the **inflation asset-swap spread** or **inflation basis**:

$$\text{Inflation Basis}(T) = BEI_{swap}(T) - BEI_{bond}(T)$$

**Sources of the Basis**

- **Asset swap dynamics**: an ILB can be converted to a floating-rate nominal instrument via an inflation asset swap (buy the ILB, pay its real+inflation cash flows into a swap, receive floating nominal), and the spread on that structure reflects funding/repo costs, not just pure breakeven divergence
- **Liquidity differential**: government bond liquidity premia differ structurally from swap market liquidity/counterparty-risk premia (swaps carry different credit/CSA considerations than government paper)
- **Repo specialness**: ILBs, particularly on-the-run issues, can trade special in repo, affecting their all-in carry and observed yield
- **Regulatory/balance-sheet demand**: swap market inflation demand (from LDI-driven pension funds and inflation-linked liability hedgers) can differ structurally from cash bond demand/supply dynamics, especially in GBP markets where pension fund demand for long-dated inflation swaps is a dominant technical driver
- **[Inference]** In UK markets, this basis has historically been persistently negative at very long maturities (swap breakevens below bond breakevens) due to strong structural pension-driven demand for long-dated inflation swap protection, though the sign and magnitude vary over time and this should be verified against current market data for any specific trading decision

### Global ILB Market Comparison

| Market | Reference Index | Lag | Deflation Floor | Notes |
| --- | --- | --- | --- | --- |
| US TIPS | CPI-U (NSA) | 3 months | Yes (principal only) | Deepest, most liquid ILB market |
| UK Index-Linked Gilts | RPI (pre-2005: 8mo lag; post-2005: 3mo lag) | 3 or 8 months (vintage-dependent) | No (older issues) / varies | RPI reform (alignment to CPIH methodology) is a major structural risk factor |
| France OATi / OAT€i | French CPI ex-tobacco / Eurozone HICP ex-tobacco | 3 months | Yes | OAT€i widely used as EUR inflation benchmark |
| Germany Bund index-linked | Eurozone HICP ex-tobacco | 3 months | Yes | Smaller, less liquid than OAT€i |
| Japan JGBi | Japan CPI (all items) | 3 months | Yes (since 2013 reissuance) | Smaller market, historically episodic issuance |

### Curve Construction from ILBs

1. Collect clean real prices/yields for available ILB maturities
2. Strip embedded deflation-floor optionality where material (particularly relevant for TIPS, using an option-adjusted approach) to obtain "clean" real yields
3. Bootstrap a real zero-coupon discount curve $P_{real}(0,T)$ from these clean real yields (analogous to nominal curve bootstrapping from coupon bonds)
4. Combine with the nominal OIS/government curve to derive bond-implied breakevens at each maturity: $BEI_{bond}(T) = \left(P_{real}(0,T)/P_{nom}(0,T)\right)^{1/T} - 1$
5. Compare against swap-implied ZCIS breakevens to monitor the inflation basis for relative value

### Illustration: Breakeven Decomposition

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 380">
<text x="350" y="24" font-size="16" text-anchor="middle" font-family="sans-serif" font-weight="bold">Breakeven Inflation Rate Decomposition (svg_diagram)</text>
<rect x="80" y="60" width="540" height="50" fill="#1f77b4" opacity="0.85" />
<text x="350" y="90" font-size="13" text-anchor="middle" fill="white" font-family="sans-serif">Expected Average Inflation E[π]</text>
<rect x="80" y="120" width="140" height="50" fill="#2ca02c" opacity="0.85" />
<text x="150" y="150" font-size="12" text-anchor="middle" fill="white" font-family="sans-serif">+ Risk Premium</text>
<rect x="230" y="120" width="180" height="50" fill="#d62728" opacity="0.85" />
<text x="320" y="150" font-size="12" text-anchor="middle" fill="white" font-family="sans-serif">- Liquidity Premium</text>
<rect x="420" y="120" width="200" height="50" fill="#ff7f0e" opacity="0.85" />
<text x="520" y="150" font-size="12" text-anchor="middle" fill="white" font-family="sans-serif">+ Deflation Floor Value</text>
<line x1="80" y1="200" x2="620" y2="200" stroke="#333" stroke-width="1.5" />
<rect x="150" y="220" width="400" height="50" fill="#9467bd" opacity="0.85" />
<text x="350" y="250" font-size="13" text-anchor="middle" fill="white" font-family="sans-serif">= Observed Bond-Implied BEI</text>

<text x="350" y="300" font-size="12" text-anchor="middle" font-family="sans-serif">Swap-Implied BEI differs further by the Inflation Basis</text>

<text x="350" y="320" font-size="11" text-anchor="middle" font-family="sans-serif" fill="#555">(funding, repo, CSA, and structural demand differences)</text>

</svg>

### Risk Sensitivities of ILB Positions

**Key Points**

- **Real rate duration**: primary sensitivity is to real yield changes, analogous to nominal duration for nominal bonds but measured against the real curve
- **Inflation carry**: holding an ILB earns accrual on the inflation-accreted principal even without any real yield movement — realized carry depends on actual realized CPI prints versus what was priced in
- **Index lag risk**: because of the 2-3 month lag, near-maturity or near-coupon-date ILB valuations are sensitive to already-known-but-not-yet-fully-indexed CPI prints ("carry" from the lag structure is a distinct, quantifiable component often called "indexation carry")
- **Deflation floor convexity**: for TIPS-style bonds, extreme deflation scenarios introduce positive convexity from the floor, relevant for tail-risk scenario analysis
- **Cross hedging basis risk**: hedging ILB inflation exposure with inflation swaps introduces the inflation basis as an active risk factor, distinct from pure inflation-level risk

### Worked Example: Deriving Bond-Implied Breakeven

Given: 10Y nominal government bond yield $y_{nom} = 4.10\%$; 10Y TIPS real yield $y_{real} = 1.95\%$ (assume deflation floor value already stripped for simplicity).

$$1 + BEI = \frac{1.0410}{1.0195} \approx 1.02109$$



$$BEI \approx 2.109\%$$

If the corresponding 10Y ZCIS swap breakeven is quoted at $2.30\%$, the inflation basis is:

$$\text{Basis} = 2.30\% - 2.109\% = +0.191\% \, (\approx 19\text{bp})$$

**[Inference]** A positive basis of this magnitude would typically be interpreted as the swap market pricing higher inflation compensation than the cash bond market — potentially reflecting stronger structural demand for inflation protection via swaps (e.g., pension fund liability hedging flows) relative to bond market technicals, though a full attribution would require decomposing repo, liquidity, and CSA-driven funding effects specific to the prevailing market conditions.

### Related Topics

- Jarrow-Yildirim model for joint real/nominal/index dynamics
- Zero Coupon and Year-on-Year inflation swaps (prior item) and the swap-bond basis
- Inflation asset swaps: structure and spread interpretation
- TIPS deflation floor option valuation methodologies
- LDI (liability-driven investment) and pension-driven inflation swap demand
- UK RPI reform and its impact on legacy index-linked gilt valuation
- Real yield curve construction and real-rate risk management