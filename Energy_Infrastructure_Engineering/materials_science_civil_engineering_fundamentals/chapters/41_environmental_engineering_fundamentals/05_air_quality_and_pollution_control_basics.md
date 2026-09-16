## Air Quality and Pollution Control Basics


### Overview

Air quality engineering addresses the sources, atmospheric behavior, health/environmental effects, and control of air pollutants. Civil and environmental engineers apply these principles to permitting, emissions control system design, and air quality impact assessment for construction, industrial, and transportation projects.

### Criteria Air Pollutants

**Key Points**

- Most regulatory frameworks designate a core set of "criteria" pollutants with established health-based ambient air quality standards
- These pollutants are regulated because of well-documented health and environmental effects at ambient concentrations, and serve as indicators for broader air quality management

**Common Criteria Pollutants**

| Pollutant | Primary Sources | Key Health/Environmental Concern |
| --- | --- | --- |
| Particulate Matter (PM10, PM2.5) | Combustion, dust, industrial processes | Respiratory/cardiovascular effects; PM2.5 penetrates deep into lungs |
| Ozone (O3, ground-level) | Secondary pollutant (formed from NOx + VOCs + sunlight) | Respiratory irritation, crop/vegetation damage |
| Nitrogen Dioxide (NO2) | Combustion (vehicles, power plants) | Respiratory irritation, ozone/PM precursor |
| Sulfur Dioxide (SO2) | Fossil fuel combustion (especially coal, high-sulfur fuel) | Respiratory effects, acid rain precursor |
| Carbon Monoxide (CO) | Incomplete combustion (vehicles, industrial) | Reduces oxygen-carrying capacity of blood |
| Lead (Pb) | Industrial processes, historically leaded gasoline | Neurological effects, especially in children |

[Unverified: the specific list of regulated criteria pollutants and their numeric ambient standards vary by jurisdiction — e.g., US EPA NAAQS, EU Air Quality Directive, or national standards such as the Philippine Clean Air Act's ambient standards; designers must reference the applicable local regulatory framework]

### Primary vs Secondary Pollutants

**Key Points**

- Primary pollutants are emitted directly from a source; secondary pollutants form in the atmosphere through chemical reactions between primary pollutants
- Ground-level ozone is the most significant secondary pollutant of regulatory concern, requiring precursor (not direct ozone) emissions control

**Formation of Ground-Level Ozone (Secondary Pollutant)**

$$NO_x + VOC + \text{sunlight} \rightarrow O_3 + \text{other photochemical products}$$

This reaction is why ozone control strategies target NOx and VOC (volatile organic compound) precursor emissions rather than ozone itself, which is not directly emitted in significant quantities from most sources.

### Emission Sources

**Key Points**

- Sources are broadly classified by their spatial characteristics and regulatory treatment
- Classification affects the modeling and control approach applied

**Source Classification**

| Source Type | Description | Example |
| --- | --- | --- |
| Point source | Single, identifiable, stationary emission location | Power plant stack, industrial facility |
| Area source | Distributed over a region, individually small | Residential heating, small commercial sources aggregated |
| Mobile source | Vehicles and other transportation emissions | Cars, trucks, aircraft, marine vessels |
| Fugitive source | Uncontrolled/unconfined emissions, not through a stack | Construction dust, storage pile wind erosion |

### Atmospheric Dispersion

**Key Points**

- Pollutant concentration at a receptor depends on emission rate, atmospheric stability, wind conditions, and distance/geometry from source
- The Gaussian plume model is the classical analytical basis for estimating downwind concentrations from point sources

**Gaussian Plume Equation (Ground-Level Concentration, Centerline)**

$$C(x,0,0,H) = \frac{Q}{\pi u \sigma_y \sigma_z}\exp\left[-\frac{1}{2}\left(\frac{H}{\sigma_z}\right)^2\right]$$

where $C$ is concentration at downwind distance $x$ along the plume centerline, $Q$ is emission rate, $u$ is wind speed, $\sigma_y$ and $\sigma_z$ are horizontal and vertical dispersion coefficients (functions of downwind distance and atmospheric stability class), and $H$ is effective stack height (physical height plus plume rise).

**Atmospheric Stability Classes**

Dispersion coefficients $\sigma_y$, $\sigma_z$ depend on atmospheric stability, commonly classified via the Pasquill-Gifford scheme (Classes A through F, unstable to stable), which depends on wind speed, solar insolation (daytime), and cloud cover (nighttime).

| Stability Class | Condition |
| --- | --- |
| A–B (unstable) | Strong solar heating, light wind — enhanced vertical mixing/dispersion |
| D (neutral) | Overcast or strong wind — moderate, commonly used as a conservative planning assumption |
| E–F (stable) | Clear night, light wind — suppressed vertical mixing, poor dispersion (higher ground-level concentrations for elevated sources at some distances) |

**Diagram: Gaussian Plume Dispersion Concept (svg_diagram)**

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 300">
<rect x="0" y="0" width="700" height="300" fill="#ffffff" />
<text x="350" y="22" text-anchor="middle" font-size="15" font-weight="bold" fill="#1a1a1a">Gaussian Plume Dispersion Concept (svg_diagram)</text>
<rect x="80" y="150" width="20" height="120" fill="#57534e" />
<text x="30" y="280" font-size="10" fill="#1a1a1a">Stack (height H)</text>
<path d="M 100 150 Q 200 150 300 165 Q 450 185 600 210" stroke="#9ca3af" stroke-width="2" fill="none" stroke-dasharray="4,3" />
<text x="400" y="150" font-size="10" fill="#4b5563">Plume centerline</text>
<ellipse cx="200" cy="160" rx="10" ry="20" fill="#fca5a5" opacity="0.6" />
<ellipse cx="350" cy="180" rx="18" ry="40" fill="#fca5a5" opacity="0.5" />
<ellipse cx="500" cy="200" rx="28" ry="65" fill="#fca5a5" opacity="0.4" />
<text x="480" y="270" font-size="10" fill="#dc2626">Expanding Gaussian<br />concentration profile</text>
<line x1="0" y1="270" x2="700" y2="270" stroke="#78350f" stroke-width="3" />
<text x="600" y="290" font-size="10" fill="#1a1a1a">Ground level (receptor)</text>
<line x1="100" y1="150" x2="600" y2="150" stroke="#3b82f6" stroke-width="1" marker-end="url(#a3)" />
<text x="620" y="145" font-size="10" fill="#3b82f6">Wind direction, u</text>
</svg>

### Particulate Matter Control Technologies

**Key Points**

- Selection depends on particle size distribution, required removal efficiency, gas stream characteristics, and cost
- Different technologies target different particle size ranges with varying efficiency

**Common PM Control Devices**

| Device | Mechanism | Typical Application |
| --- | --- | --- |
| Cyclone separator | Centrifugal force separates larger particles | Pre-cleaner for coarser particles, lower cost/efficiency |
| Baghouse (fabric filter) | Filtration through fabric media | High efficiency across wide particle size range |
| Electrostatic precipitator (ESP) | Electrically charges particles, collects on oppositely charged plates | High efficiency, large gas volumes (power plants) |
| Wet scrubber | Particle capture via liquid droplet contact | Effective for both particulates and some gaseous pollutants simultaneously |

**Collection Efficiency**

$$\eta = \frac{C_{in}-C_{out}}{C_{in}} \times 100\%$$

where $C_{in}$ and $C_{out}$ are inlet and outlet pollutant concentrations across the control device.

### Gaseous Pollutant Control Technologies

**Key Points**

- Gas-phase pollutants require different control approaches than particulates, typically based on absorption, adsorption, or chemical conversion

**Common Gaseous Control Methods**

| Method | Mechanism | Typical Application |
| --- | --- | --- |
| Wet scrubbing (absorption) | Pollutant transfers from gas to liquid phase | SO2 removal (flue gas desulfurization) |
| Activated carbon adsorption | Pollutant adheres to carbon surface | VOC control, odor control |
| Selective Catalytic Reduction (SCR) | Catalytic conversion of NOx to N2 and water using a reducing agent (typically ammonia/urea) | NOx control at combustion sources |
| Thermal/catalytic oxidation | High-temperature combustion of VOCs to CO2 and water | Industrial VOC-laden exhaust streams |

### Flue Gas Desulfurization (Example Reaction)

$$SO_2 + CaCO_3 + \frac{1}{2}O_2 \rightarrow CaSO_4 + CO_2$$

(limestone-based wet scrubbing, a common SO2 control approach at coal-fired power plants)

### Mobile Source Emissions Control

**Key Points**

- Vehicle emissions are controlled through a combination of fuel quality standards, engine design, and exhaust after-treatment
- Transportation-related air quality is a significant consideration in urban planning and transportation engineering

**Common Vehicle Emission Control Technologies**

| Technology | Target Pollutant |
| --- | --- |
| Catalytic converter | CO, NOx, unburned hydrocarbons |
| Diesel particulate filter (DPF) | Particulate matter from diesel engines |
| Exhaust gas recirculation (EGR) | NOx reduction via combustion temperature control |
| Evaporative emission control (charcoal canister) | Fuel vapor VOC emissions |

### Ambient Air Quality Monitoring and Indices

**Key Points**

- Ambient monitoring networks measure pollutant concentrations to assess compliance with air quality standards and inform public health advisories
- Air Quality Index (AQI) systems translate multiple pollutant concentrations into a simplified public communication scale

**General AQI Concept**

Most AQI frameworks calculate a sub-index for each monitored pollutant relative to its health-based concentration breakpoints, with the overall reported AQI being the maximum (worst) sub-index among pollutants at that time/location. [Unverified: specific AQI breakpoints, pollutant sets, and calculation formulas vary by country/agency (e.g., US EPA AQI vs. other national indices) and should be referenced from the applicable local system]

### Construction-Related Air Quality Considerations

**Key Points**

- Construction activities generate fugitive dust and equipment exhaust emissions requiring management, particularly relevant to civil engineering project permitting and execution
- Best management practices (BMPs) are the primary control approach, given the temporary and distributed nature of construction emissions

**Common Construction Dust Control BMPs**

- Water spraying/application on exposed soil and haul roads
- Covering stockpiles and truck loads during transport
- Minimizing disturbed area and revegetating/stabilizing completed areas promptly
- Equipment maintenance and idling restrictions to reduce exhaust emissions

### Common Pitfalls

- Confusing primary and secondary pollutants when designing control strategies — ozone control requires precursor (NOx/VOC) management, not direct ozone emission control
- Applying Gaussian plume dispersion modeling outside its valid assumptions (e.g., complex terrain, near-field/building downwash effects, non-steady meteorological conditions) without appropriate model modification or use of more advanced dispersion models
- Selecting PM control technology without considering the specific particle size distribution of the target emission stream, resulting in inadequate removal efficiency
- Neglecting fugitive dust emissions from construction or material handling operations, which are often significant but less visible than stack emissions
- Assuming a single global set of numeric air quality standards applies universally, when criteria pollutant standards and AQI systems are jurisdiction-specific

**Next Steps**

- Water Quality Parameters and Standards (foundational review)
- Solid Waste Management (foundational review)
- Environmental Impact Assessment Fundamentals
- Industrial Emissions Permitting and Compliance
- Climate Change and Greenhouse Gas Accounting
- Indoor Air Quality Fundamentals