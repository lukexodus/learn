## Input-Output Analysis for Energy and Emissions Accounting


### Overview

Input-output (IO) analysis models the interdependencies between economic sectors, tracing how output in one sector requires inputs from others. Applied to energy and emissions, IO analysis quantifies the direct and indirect (embodied) energy use and emissions associated with production and final consumption — a foundational tool for carbon footprinting, life-cycle emissions accounting, and structural decomposition of energy demand drivers.

### Theoretical Foundations

#### Leontief Input-Output Model

The core IO framework, developed by Wassily Leontief, represents an economy as a system of linear equations in which each sector's output is used partly as intermediate input to other sectors and partly as final demand:

$$x = Ax + y$$

Where $x$ is the vector of total sectoral output, $A$ is the technical coefficient matrix (direct input requirements per unit of output), and $y$ is the vector of final demand. Solving for $x$:

$$x = (I - A)^{-1} y$$

Where $(I-A)^{-1}$ is the **Leontief inverse**, capturing both direct and indirect input requirements throughout the full supply chain.

#### Technical Coefficients

Each element $a_{ij}$ of matrix $A$ represents the input from sector $i$ required per unit of output from sector $j$:

$$a_{ij} = \frac{z_{ij}}{x_j}$$

Where $z_{ij}$ is the intermediate flow from sector $i$ to sector $j$, and $x_j$ is total output of sector $j$.

### Energy and Emissions Extension

#### Direct Energy/Emissions Intensity Vector

To extend the basic IO model to energy or emissions, a direct intensity vector $f$ is defined, giving energy use (or emissions) per unit of sectoral output:

$$f_j = \frac{E_j}{x_j}$$

Where $E_j$ is direct energy consumption (or emissions) of sector $j$.

#### Total (Embodied) Energy/Emissions Intensity

Total embodied intensity — direct plus indirect, accounting for the full upstream supply chain — is calculated as:

$$e = f (I - A)^{-1}$$

Where $e$ is the row vector of total energy/emissions intensity per unit of final demand across all sectors. This is the standard basis for embodied carbon and energy footprint calculations.

**Key Points**

- **Direct emissions**: emitted at the point of production within a given sector
- **Indirect (embodied) emissions**: emissions occurring upstream in the supply chain, attributed to the final consuming sector or product
- **Total emissions footprint**: direct plus indirect, representing the full life-cycle emissions embodied in a unit of final demand

### Environmentally Extended Input-Output (EEIO) Models

EEIO models formally integrate physical environmental accounts (energy, emissions, water, land) alongside the standard monetary IO table.

```mermaid
flowchart TD
    A[Monetary IO Table: Sector-by-Sector Transactions] --> D[Technical Coefficient Matrix A]
    B[Physical Energy/Emissions Accounts by Sector] --> E[Direct Intensity Vector f]
    D --> F[Leontief Inverse: (I-A)^-1]
    F --> G[Total Embodied Intensity: f times Leontief Inverse]
    E --> G
    C[Final Demand Vector y] --> H[Embodied Energy/Emissions by Final Demand Category]
    G --> H
```

**Key Points**

- **Single-region EEIO**: applies national/regional technical coefficients uniformly, ignoring where imported intermediate inputs were actually produced
- **Multi-Regional Input-Output (MRIO)**: explicitly tracks bilateral trade flows between regions/countries, allowing accurate attribution of emissions embodied in imports/exports — essential for consumption-based (vs. production-based/territorial) emissions accounting
- Common MRIO databases include EXIOBASE, GTAP, WIOD, and Eora [Unverified — specific database coverage, sector classifications, and update schedules change over time; consult current documentation]

### Production-Based vs. Consumption-Based Accounting

**Key Points**

- **Production-based (territorial) accounting**: attributes emissions to the country/sector where they are physically emitted; the standard basis for UNFCCC national inventory reporting
- **Consumption-based accounting**: attributes emissions to the final consumer of goods and services, regardless of where in the supply chain emissions occurred; requires MRIO to trace imported embodied emissions
- The difference between the two is often termed the **carbon trade balance** — countries that are net importers of emissions-intensive goods typically show higher consumption-based than production-based emissions, and vice versa for net exporters
- [Inference] this pattern is well documented empirically for many developed importing economies but is not a universal rule and depends on each country's specific trade structure

### Structural Decomposition Analysis (SDA)

SDA decomposes changes in energy use or emissions over time into contributing factors using the IO framework, commonly separating:

$$\Delta E = \Delta f \cdot L \cdot y + f \cdot \Delta L \cdot y + f \cdot L \cdot \Delta y$$

Where $L = (I-A)^{-1}$ is the Leontief inverse.

**Key Points**

- **Emission/energy intensity effect** ($\Delta f$): change due to cleaner/dirtier production technology within sectors
- **Structural effect** ($\Delta L$): change due to shifts in inter-sectoral linkages (input-output structure)
- **Final demand effect** ($\Delta y$): change due to growth in scale or shifts in composition of final demand
- SDA is closely related to, but methodologically distinct from, index decomposition analysis (IDA, e.g., LMDI), which typically works with aggregate rather than full inter-sectoral data

### Hybrid Life-Cycle Assessment (Hybrid LCA)

**Key Points**

- **Process-based LCA**: bottom-up, highly detailed for specific products/processes but subject to truncation error (upstream supply chain boundaries must be cut off somewhere)
- **IO-based LCA**: comprehensive economy-wide coverage (no truncation) but coarse sectoral resolution
- **Hybrid LCA**: combines process-level detail for key components with IO-based background data to capture the remainder of the supply chain, addressing truncation error while retaining process specificity

### Data Requirements and Construction

**Key Points**

- **Monetary IO table**: sourced from national statistical offices (supply-use tables, symmetric IO tables) or international harmonized databases
- **Physical energy accounts**: sourced from energy balances (IEA, EIA, national energy agencies), converted to consistent units and matched to IO sector classifications
- **Emission factors**: applied to physical energy use by fuel type and sector to derive $CO_2$ (and other GHG) accounts, often using IPCC default factors or national inventory-consistent factors
- Sector classification harmonization between monetary IO tables and physical energy/emissions data is a common practical challenge, since classification schemes (ISIC, NAICS, national schemes) rarely align perfectly across sources

### Worked Example: Embodied Carbon Calculation

**Example**

Consider a simplified 2-sector economy: Electricity (Sector 1) and Manufacturing (Sector 2).

Technical coefficient matrix:

$$A = \begin{bmatrix} 0.10 & 0.30 \\ 0.05 & 0.20 \end{bmatrix}$$

Direct emissions intensity (tCO2 per $M output): $f = [0.80, \; 0.15]$

The Leontief inverse $(I-A)^{-1}$ is computed, then total embodied intensity $e = f(I-A)^{-1}$ gives emissions per dollar of final demand for each sector, incorporating manufacturing's indirect electricity use.

**Output** (illustrative arithmetic, not from real data)

$$(I - A) = \begin{bmatrix} 0.90 & -0.30 \\ -0.05 & 0.80 \end{bmatrix}$$

Solving for the inverse and multiplying by $f$ yields a total emissions intensity for manufacturing output *higher* than its direct-only intensity (0.15), since it inherits embodied emissions from its electricity input — a standard illustrative result of how IO-based accounting captures indirect emissions that direct/territorial accounting alone would miss.

### Software and Implementation Tools

**Key Points**

- **Python**: `pymrio` (widely used for MRIO analysis, EXIOBASE/WIOD/Eora integration), `numpy`/`pandas` for custom matrix algebra implementations
- **R**: `leontief` and various institution-specific packages for IO/SDA analysis
- Matrix inversion for large MRIO tables (thousands of sector-region combinations) requires efficient sparse-matrix numerical methods; computational approach and default numerical tolerances may vary by software package and version

### Applications in Energy Economics

- National and corporate carbon footprint accounting (Scope 3 / value-chain emissions)
- Consumption-based emissions inventories as a complement to territorial reporting
- Trade and "carbon leakage" analysis in climate policy design
- Energy intensity benchmarking across sectors and countries
- Decomposition of historical energy/emissions trends into technology, structural, and demand-driven components
- Input data foundation for hybrid LCA and some CGE model calibration

### Related Topics

- Multi-Regional Input-Output (MRIO) databases and construction methods
- Structural Decomposition Analysis vs. Index Decomposition Analysis (LMDI)
- Consumption-based vs. production-based emissions accounting
- Hybrid Life-Cycle Assessment methodology
- Social Accounting Matrices as an extension of IO tables (link to CGE modeling)
- Scope 1/2/3 corporate emissions accounting frameworks
- Carbon leakage and trade-embodied emissions analysis
- Supply-use table construction and national accounts methodology