## The Kraljic Purchasing Portfolio Matrix


### Overview

The Kraljic Purchasing Portfolio Matrix is a strategic sourcing framework introduced by Peter Kraljic in his 1983 Harvard Business Review article "Purchasing Must Become Supply Management." It classifies purchased items or supplier relationships along two dimensions — **profit impact** (or business impact) and **supply risk** — to determine the appropriate procurement strategy, resource allocation, and supplier relationship model for each category. It remains one of the foundational tools in strategic sourcing and supplier segmentation.

### Core Dimensions

**Profit Impact (X-axis, sometimes Y-axis depending on rendering convention)**

Measures how significant a purchased item or category is to the buying organization's financial performance. Factors include:

- Volume/value of spend
- Percentage of total purchase cost
- Impact on product quality or business growth
- Potential for cost reduction or value addition

**Supply Risk (Y-axis)**

Measures the complexity, scarcity, and vulnerability of the supply market for that item. Factors include:

- Number of qualified suppliers (monopoly, oligopoly, fragmented market)
- Availability of substitutes
- Entry barriers for new suppliers
- Geographic or geopolitical concentration
- Lead times and logistics complexity
- Rate of technological change in the supply base

### The Four Quadrants

$$\text{Quadrant} = f(\text{Profit Impact}, \text{Supply Risk})$$

**1. Non-Critical Items (Low Profit Impact, Low Supply Risk)**

- **Key Points**: Commodity-type goods, easily sourced, low value per transaction (e.g., office supplies, standard MRO items).
- **Strategy**: Efficient processing and simplification. Minimize administrative burden through automation (e-procurement, purchase cards, catalog buying), consolidate suppliers, and reduce transaction cost rather than unit price.
- **Example**: Standard stationery, cleaning supplies, or generic fasteners procured via an automated e-catalog with minimal buyer intervention.

**2. Leverage Items (High Profit Impact, Low Supply Risk)**

- **Key Points**: High spend value but many capable suppliers exist; buyer holds negotiating power.
- **Strategy**: Exploit purchasing power. Use competitive bidding, tendering, volume consolidation, and price negotiation to capture savings. Multi-sourcing is common to preserve leverage.
- **Example**: Bulk raw materials like steel coils or packaging materials where multiple qualified mills/suppliers compete on price.

**3. Bottleneck Items (Low Profit Impact, High Supply Risk)**

- **Key Points**: Low financial value but supply is constrained (single-source, specialized, or low-volume components critical to production continuity).
- **Strategy**: Ensure supply continuity over cost optimization. Build safety stock, qualify alternative suppliers where feasible, and maintain strong relationship management despite low spend, since disruption risk outweighs cost concerns.
- **Example**: A proprietary sensor from a sole-source supplier required for a niche assembly line, where an outage would halt production.

**4. Strategic Items (High Profit Impact, High Supply Risk)**

- **Key Points**: High value and high risk — often complex, technologically advanced, or geopolitically sensitive supply chains.
- **Strategy**: Develop long-term strategic partnerships, joint development agreements, dual/multi-sourcing where possible, risk-sharing contracts, and close collaboration on forecasting, innovation, and continuity planning.
- **Example**: Semiconductor components sourced under multi-year agreements with joint capacity planning between an automotive OEM and a chip foundry.

### Diagram: The Kraljic Matrix (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 520">
<text x="320" y="24" font-size="18" font-weight="bold" text-anchor="middle" fill="#1a1a1a">The Kraljic Purchasing Portfolio Matrix (svg_diagram)</text>

<line x1="120" y1="450" x2="580" y2="450" stroke="#333" stroke-width="2" />
<line x1="120" y1="450" x2="120" y2="60" stroke="#333" stroke-width="2" />


<text x="350" y="485" font-size="14" text-anchor="middle" fill="#333">Profit Impact / Business Impact →</text>

<text x="60" y="255" font-size="14" text-anchor="middle" fill="#333" transform="rotate(-90 60 255)">Supply Risk →</text>


<line x1="350" y1="60" x2="350" y2="450" stroke="#999" stroke-dasharray="4,4" />
<line x1="120" y1="255" x2="580" y2="255" stroke="#999" stroke-dasharray="4,4" />

<rect x="120" y="255" width="230" height="195" fill="#e8f4ea" stroke="#4caf50" stroke-width="1" />
<text x="235" y="360" font-size="15" font-weight="bold" text-anchor="middle" fill="#2e7d32">Non-Critical</text>
<text x="235" y="380" font-size="11" text-anchor="middle" fill="#2e7d32">Simplify &amp; Automate</text>
<rect x="350" y="255" width="230" height="195" fill="#e3f2fd" stroke="#1976d2" stroke-width="1" />
<text x="465" y="360" font-size="15" font-weight="bold" text-anchor="middle" fill="#0d47a1">Leverage</text>
<text x="465" y="380" font-size="11" text-anchor="middle" fill="#0d47a1">Exploit Buying Power</text>
<rect x="120" y="60" width="230" height="195" fill="#fff3e0" stroke="#f57c00" stroke-width="1" />
<text x="235" y="150" font-size="15" font-weight="bold" text-anchor="middle" fill="#e65100">Bottleneck</text>
<text x="235" y="170" font-size="11" text-anchor="middle" fill="#e65100">Ensure Continuity</text>
<rect x="350" y="60" width="230" height="195" fill="#fce4ec" stroke="#c2185b" stroke-width="1" />
<text x="465" y="150" font-size="15" font-weight="bold" text-anchor="middle" fill="#880e4f">Strategic</text>
<text x="465" y="170" font-size="11" text-anchor="middle" fill="#880e4f">Partner &amp; Collaborate</text>
</svg>

### Strategic Response Framework by Quadrant

| Quadrant | Primary Objective | Sourcing Approach | Relationship Depth | Contract Type |
| --- | --- | --- | --- | --- |
| Non-Critical | Reduce process cost | Catalog/e-procurement | Transactional | Short-term, blanket POs |
| Leverage | Reduce unit price | Competitive tendering | Transactional to moderate | Annual/multi-year, price-driven |
| Bottleneck | Secure supply continuity | Dual-source, buffer stock | Moderate to high | Continuity-focused, sometimes exclusive |
| Strategic | Maximize joint value creation | Partnership/alliance | High, collaborative | Long-term, joint governance |

### Analytical Process (Implementation Steps)

**1. Classify purchased items** by spend category using ABC/Pareto analysis to estimate profit impact.

**2. Assess supply market risk** for each category using supplier count, switching cost, and market concentration indicators (e.g., a Herfindahl-Hirschman Index-style concentration check).

**3. Plot items on the 2x2 matrix.**

**4. Assign differentiated strategies** per quadrant as outlined above.

**5. Re-evaluate periodically**, since items can migrate between quadrants (e.g., a strategic item can become leverage once a second qualified supplier is developed — this migration is itself considered a strategic sourcing objective).

### Extensions and Related Models

- **Power/Interest adaptation**: Some practitioners extend Kraljic with a supplier-side "preference matrix," creating a combined buyer-supplier power analysis.
- **Reck & Long (1988)** extended Kraljic by adding an organizational maturity axis (reactive, mechanical, integrative purchasing postures).
- **Gelderman & Van Weele (2003)** contributed empirical validation studies on how firms operationalize quadrant strategies, particularly the ambiguity in classifying "bottleneck vs. strategic" boundary items. [Unverified: specific findings should be checked against the original publication for precise conclusions, as academic interpretations vary.]

### Common Pitfalls

- **Static classification**: Treating the matrix as a one-time exercise rather than a living tool that is revisited as market conditions, supplier capabilities, and internal demand change.
- **Over-reliance on spend data alone**: Profit impact should include qualitative factors (brand risk, quality criticality), not just transactional value.
- **Ignoring supplier perception**: The matrix is buyer-centric; a supplier may not prioritize a buyer who considers them "strategic" if the buyer represents low value to that supplier (addressed by supplier preference/power matrices).

### Related Topics

- Supplier Relationship Management (SRM) tiering models
- Total Cost of Ownership (TCO) analysis for leverage/strategic items
- Dual-sourcing and supply risk mitigation strategies
- Herfindahl-Hirschman Index for supply market concentration
- Category management frameworks
- Supplier preference/power matrix (reverse Kraljic)