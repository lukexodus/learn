## Feed-in Tariffs and Feed-in Premium Design

### Definition and Core Concept

A feed-in tariff (FIT) is a renewable energy support policy under which eligible generators are guaranteed a fixed price per unit of electricity (typically expressed in $/MWh or currency/kWh) for output delivered to the grid, generally under a long-term contract (commonly 15–20 years), regardless of prevailing wholesale market prices. A feed-in premium (FIP) is a related but structurally distinct mechanism in which generators sell their output into the wholesale electricity market at the prevailing market price and receive an additional fixed or variable premium payment on top, rather than a single administratively set price replacing the market price entirely.

Both instruments are price-based support mechanisms, in contrast to quantity-based mechanisms such as renewable portfolio standards (RPS) with tradable renewable energy certificates (RECs) or competitive auctions, which fix a target quantity and let the market determine price. FITs and FIPs instead fix the price (or a price component) and let deployment quantity respond endogenously to that price signal.

### Basic FIT Mechanics

**Key Points**

- The generator receives a guaranteed price $P_{FIT}$ for every unit of electricity delivered, typically set administratively by a regulator or legislature, often differentiated by technology, project size, and sometimes resource quality or vintage (date of interconnection).
- Payment obligation is usually placed on the incumbent utility or grid operator, with the incremental cost recovered from all ratepayers through a surcharge on retail electricity bills (a mechanism often called a "renewable energy surcharge" or similar).
- FITs typically include **priority/guaranteed grid access** and **priority dispatch**, meaning FIT-supported generation is dispatched ahead of conventional generation regardless of its bid price, insulating the generator from short-run market price risk and dispatch risk entirely.
- Revenue for the generator under a pure FIT is:

$$R_{FIT} = P_{FIT} \times Q$$

where $Q$ is metered output, with essentially zero exposure to wholesale price volatility.

### Feed-in Premium Mechanics

Under a feed-in premium, the generator sells output at the market price $P_{market}(t)$, which varies over time, and receives a premium $\Pi$ on top. Revenue is:

$$R_{FIP} = \left[P_{market}(t) + \Pi\right] \times Q(t)$$

**Fixed premium (constant premium)**: $\Pi$ is a constant amount added to the market price regardless of its level, so total revenue per unit still varies with market price — the generator retains full exposure to market price volatility, but at an elevated average level.

**Sliding (variable) premium**: $\Pi$ is adjusted so that total revenue per unit approximates a target reference price $P_{ref}$, typically calculated as:

$$\Pi(t) = \max(0, P_{ref} - P_{market}(t))$$

This structure — common in several European "Contracts for Difference" (CfD)-style FIP implementations — largely replicates the price-certainty feature of a FIT while still requiring the generator to physically sell into the wholesale market and be exposed to its dispatch and balancing responsibilities, distinguishing it from a pure FIT primarily in market integration rather than in ultimate price risk.

**Capped/floored premium**: Some designs impose a cap on the maximum premium payable and/or a floor guaranteeing minimum total revenue, bounding both ratepayer cost exposure and generator downside risk simultaneously.

```mermaid
flowchart TD
    subgraph FIT["Feed-in Tariff (svg_diagram equivalent structure)"]
        A1[Generator Output] --> B1[Grid Operator / Utility]
        B1 -->|Fixed Price P_FIT per unit, regardless of market| A1
        B1 --> C1[Wholesale Market -- generator not directly exposed]
    end

    subgraph FIP["Feed-in Premium"]
        A2[Generator Output] --> C2[Wholesale Market]
        C2 -->|Market Price P_market t| A2
        D2[Premium Administrator] -->|Premium Payment Pi t| A2
        A2 -.exposed to market price signals, dispatch, balancing.-> C2
    end
```

### Comparative Economics: FIT vs. FIP vs. Other Support Mechanisms

| Dimension | Feed-in Tariff | Feed-in Premium (fixed) | Feed-in Premium (sliding/CfD-style) | RPS + Tradable Certificates | Competitive Auctions |
| --- | --- | --- | --- | --- | --- |
| Price risk borne by generator | Minimal | Moderate to high (full market exposure plus premium) | Low to moderate | High (certificate price volatility) | Depends on auction design (often low, fixed-price PPA outcome) |
| Market price signal exposure | None (fully insulated) | Full | Partial (revenue smoothed toward reference price) | Full | Varies |
| Incentive to respond to price signals/forecast demand | Weak (dispatch guaranteed) | Strong | Moderate | Strong | Varies |
| Administrative complexity | Low to moderate | Moderate | Moderate to high | High (certificate market design/monitoring) | High (auction design, prequalification) |
| Typical cost discovery mechanism | Administrative price-setting (often with periodic degression) | Market-determined base + administratively set premium | Market-determined base + calculated variable premium | Certificate market clears price | Competitive bidding reveals price |
| Common criticism | Risk of overpayment/underpayment due to administrative mispricing; ratepayer cost escalation if uptake exceeds forecasts | Weaker investor certainty than FIT; can still require substantial premium calibration | More complex to administer; can create negative-price incentive distortions | Certificate price volatility increases financing costs (higher risk premium) | Risk of unrealistic/non-completing bids; potential for insufficient competition in thin markets |

### Design Parameters and Economic Trade-offs

#### Tariff Level Setting

FIT/FIP levels are typically set with reference to the levelized cost of electricity (LCOE) of the target technology plus a target rate of return, following the general form:

$$P_{FIT} = LCOE + \text{margin}$$



$$LCOE = \frac{\sum_{t=0}^{T} \frac{C_t}{(1+r)^t}}{\sum_{t=0}^{T} \frac{Q_t}{(1+r)^t}}$$

where $C_t$ is total cost (capital and operating) in year $t$, $Q_t$ is energy output in year $t$, and $r$ is the discount rate. Setting $P_{FIT}$ too high relative to actual achievable LCOE results in windfall profits for developers and excess ratepayer cost; setting it too low fails to attract investment. This calibration challenge — requiring the regulator to estimate a private cost structure it cannot directly observe — is a central practical weakness of administratively set price mechanisms relative to auction-based price discovery.

#### Degression Mechanisms

To account for anticipated technology cost declines over time and avoid locking in outdated, excessively generous tariff levels, most modern FIT schemes incorporate **tariff degression**: scheduled or automatic reductions in the tariff offered to newly interconnecting projects, either on a fixed calendar schedule or dynamically linked to observed deployment volumes (a "corridor" or "responsive degression" approach, where faster-than-target deployment triggers steeper tariff cuts for subsequent cohorts, and slower deployment triggers smaller cuts).

#### Technology and Size Differentiation

Tariffs are commonly tiered by technology (solar PV, onshore wind, offshore wind, biomass, small hydro) and by project size (residential rooftop vs. utility-scale), reflecting differing cost structures and, in earlier FIT scheme generations, an explicit policy objective of technology diversification rather than pure least-cost renewable deployment.

#### Contract Duration and Grandfathering

Long contract durations (commonly 15–20 years) are designed to match the useful life of the underlying asset and provide revenue certainty sufficient to secure project financing at favorable debt terms; existing contracted generators are typically "grandfathered" at their original tariff level even as tariffs for new entrants decline, preserving the certainty of already-committed investments while allowing the overall scheme to adjust to changing costs.

### Fiscal and Cost-Recovery Mechanisms

**Key Points**

- **Ratepayer surcharge (levy) financing**: The most common approach; the incremental cost of FIT/FIP payments above the avoided wholesale market cost is spread across all retail electricity consumers via a per-kWh surcharge, sometimes called a "renewable energy levy" or similar (e.g., historically the EEG-Umlage in Germany under its Renewable Energy Sources Act).
- **General taxation financing**: Less common; used in some jurisdictions to avoid placing the full cost burden on electricity ratepayers, or to shield energy-intensive industries via specific exemption mechanisms.
- **Exemptions for energy-intensive, trade-exposed industries**: Many schemes include reduced surcharge obligations for large industrial consumers to preserve international competitiveness, which increases the surcharge burden on remaining (typically residential) ratepayers — a distributional design choice with significant equity implications.

The total ratepayer-borne cost in a given period can be approximated as:

$$\text{Total Surcharge Cost} = \sum_{i} \left(P_{FIT,i} - P_{avoided}\right) \times Q_i$$

summed across all contracted generators $i$, where $P_{avoided}$ is the wholesale market price that would otherwise have been paid (the "avoided cost"). This formulation makes explicit that FIT/FIP costs to ratepayers are driven not just by the tariff level itself but by the gap between the tariff and prevailing wholesale prices — a gap that narrows automatically as wholesale prices rise (e.g., during fossil fuel price spikes) and widens as wholesale prices fall, creating countercyclical fiscal exposure for the support scheme.

### Known Design Failures and Corrective Responses

- **Boom-bust cycles from mispriced tariffs**: Several early national FIT schemes (notably Spain's solar PV FIT in the mid-2000s and Germany's early solar FIT) offered tariffs that, combined with rapidly falling module costs, generated returns well above the intended target, triggering deployment booms far exceeding policy forecasts, followed in some cases by retroactive tariff cuts or scheme suspensions that damaged investor confidence in subsequent renewable policy credibility. [Inference] The precise magnitude of investor confidence effects from retroactive changes is difficult to measure directly and is typically inferred from subsequent financing cost and deployment trends rather than observed as a directly quantified parameter.
- **Merit-order effect and negative wholesale price interactions**: Because FIT-supported generation (especially wind and solar) typically has near-zero marginal cost and is dispatched with priority, high FIT/RES penetration can depress wholesale market prices (the "merit-order effect"), which — under a pure FIT — does not directly affect generator revenue, but under a FIP raises the required premium to maintain the target reference price, increasing the fiscal cost of the support mechanism precisely when the underlying technology has succeeded in penetrating the market.
- **Negative pricing incentive distortion under sliding premiums**: If a sliding premium guarantees a fixed reference price regardless of market conditions, generators may lack any incentive to reduce output even when wholesale prices turn negative (i.e., when supply exceeds demand and system costs of accepting additional output are negative), a documented design flaw that some jurisdictions have addressed by suspending premium payments during negative-price periods.
- **Transition toward auction-based price-setting**: In response to the price-discovery weaknesses of purely administrative tariff-setting, many jurisdictions (including the EU under state-aid guideline reforms) have shifted from administratively determined FITs/FIPs toward competitive auctions in which developers bid for the tariff or premium level, retaining the FIP structural mechanism while replacing administrative price-setting with market-based price discovery — a hybrid model sometimes termed "auction-based FIP."

### Illustrative Revenue Comparison Diagram

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 760 400" font-family="Helvetica, Arial, sans-serif">
<text x="380" y="26" text-anchor="middle" font-size="17" font-weight="bold" fill="#1a1a1a">Generator Revenue per MWh: FIT vs. Fixed FIP vs. Sliding FIP (svg_diagram)</text>
<line x1="70" y1="340" x2="720" y2="340" stroke="#333" stroke-width="2" />
<line x1="70" y1="340" x2="70" y2="50" stroke="#333" stroke-width="2" />
<text x="380" y="375" text-anchor="middle" font-size="13" fill="#333">Wholesale Market Price (Time-Varying)</text>
<text x="30" y="195" font-size="13" fill="#333" transform="rotate(-90 30 195)">Generator Revenue (\$/MWh)</text>
<path d="M70,150 L720,150" stroke="#2980b9" stroke-width="3" fill="none" />
<text x="600" y="140" font-size="12" fill="#2980b9" font-weight="bold">FIT: Flat Revenue (Fully Insulated)</text>
<path d="M70,300 Q 250,220 380,150 T 720,60" stroke="#c0392b" stroke-width="3" fill="none" stroke-dasharray="6,3" />
<text x="560" y="90" font-size="12" fill="#c0392b" font-weight="bold">Fixed FIP: Market Price + Constant Premium</text>
<path d="M70,155 Q 250,152 380,150 T 720,148" stroke="#27ae60" stroke-width="3" fill="none" stroke-dasharray="2,2" />
<text x="480" y="175" font-size="12" fill="#27ae60" font-weight="bold">Sliding FIP: Revenue Smoothed Toward P_ref</text>
<line x1="70" y1="340" x2="70" y2="50" stroke="#999" stroke-width="1" stroke-dasharray="2,2" />
<line x1="700" y1="340" x2="700" y2="50" stroke="#999" stroke-width="1" stroke-dasharray="2,2" />
<text x="90" y="330" font-size="11" fill="#666">Low Market Price</text>
<text x="620" y="330" font-size="11" fill="#666">High Market Price</text>
</svg>

### Policy Effectiveness Considerations

- **Deployment effectiveness**: FITs have historically demonstrated strong effectiveness at rapidly scaling renewable deployment in numerous jurisdictions (Germany, Spain, and others in the 2000s–2010s) precisely because they minimize investor risk, which lowers the cost of capital (weighted average cost of capital, WACC) required to finance projects — an effect increasingly emphasized in the literature as economically significant given the capital-intensive, low-operating-cost structure of most renewable technologies. [Inference] The magnitude of the WACC-reduction effect and its consequent impact on total system cost varies by study and financing environment, and precise cross-country comparisons are sensitive to methodology.
- **Market integration critique**: A central critique of pure FITs (relative to FIPs and market-based mechanisms) is that full insulation from market price signals removes any incentive for generators to respond to system needs — for example, to avoid producing during periods of oversupply or negative prices, or to co-locate with storage to shift output toward higher-value periods — a concern that has driven the broader European Union policy shift toward FIPs and auction-based FIP hybrids as renewable penetration has increased and market integration has become a more central policy objective.
- **Distributional and equity considerations**: Ratepayer-surcharge-financed schemes are generally regressive in incidence (surcharges as a share of income are higher for lower-income households) unless offset by targeted rebates or progressive rate design, a consideration increasingly incorporated into subsequent scheme reforms in several jurisdictions.

### Related Topics

- **Renewable portfolio standards and tradable renewable energy certificates (RECs)**
- **Competitive renewable energy auctions**: design parameters and price discovery mechanisms
- **Contracts for Difference (CfD) as a specific sliding feed-in premium implementation**
- **Merit-order effect of renewable generation on wholesale electricity prices**
- **Levelized cost of electricity (LCOE) methodology and its policy applications**
- **Cost of capital (WACC) implications of renewable support scheme design**
- **Negative electricity pricing and curtailment economics**
- **Distributional and equity analysis of energy policy cost-recovery mechanisms**
- **EU state-aid guidelines and the transition from FIT to auction-based FIP schemes**