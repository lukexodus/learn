## Inspection and Testing Frequencies

### Overview

Inspection and testing frequencies define how often covered mechanical integrity (MI) equipment must be examined, tested, or monitored to detect degradation before it results in loss of containment. Under OSHA PSM (29 CFR 1910.119(j)(4)), frequencies must be consistent with applicable manufacturers' recommendations, good engineering practices, and — where degradation history exists — more frequent inspection than the code minimum when operating experience indicates a need. Frequency-setting is not a one-time administrative exercise; it is a risk-informed engineering decision that must be revisited as inspection data, process conditions, and damage mechanisms are better understood.

### Regulatory Basis

**Key Points**

- 1910.119(j)(4)(i) requires inspections and tests to be performed on process equipment.
- 1910.119(j)(4)(ii) requires frequency to be consistent with applicable manufacturers' recommendations and good engineering practices, and more frequently if determined necessary by prior operating experience.
- 1910.119(j)(4)(iii) requires the employer to consult applicable manufacturers' recommendations and good engineering practices until sufficient corporate/site experience exists to justify a different frequency.
- RAGAGEP (Recognized and Generally Accepted Good Engineering Practice) — principally the API inspection codes — supplies the default frequency-setting methodology industry-wide, and deviating from RAGAGEP-derived intervals without documented technical justification is a common OSHA/EPA RMP citation basis.

### Baseline Frequencies by Equipment/Code

| Equipment Category | Governing Code | Default Maximum Interval (code baseline) |
| --- | --- | --- |
| Pressure vessels — external visual | API 510 | 5 years (or per RBI, up to 10 years max) |
| Pressure vessels — internal/on-stream (UT) | API 510 | Half of remaining-life calculation, max 10 years (RBI) or code default |
| Atmospheric storage tanks — external | API 653 | 5 years (formal) / annual (routine in-service) |
| Atmospheric storage tanks — internal | API 653 | Formula-based on corrosion rate; code max 20 years |
| Piping circuits (UT thickness) | API 570 | 5 years (Class 1), 5–10 years (Class 2), 10 years (Class 3), or RBI-determined |
| Pressure relief valves | API 576 / site RAGAGEP | Typically 1–5 years depending on service severity (fouling, corrosive/clean) |
| Fired heater tubes | API 573 | Per site program; commonly tied to turnaround cycle |
| SIS / Safety Instrumented Functions | IEC 61511 / ISA 84 | Derived from SIL verification calculation (PFDavg target), not a fixed code interval |
| Pumps (vibration monitoring) | API 610 / site program | Continuous online or monthly/quarterly route-based |

These are code-default **maximums**, not recommended defaults — actual site frequency must be equal to or shorter than the code baseline unless a documented RBI or engineering justification supports extension.

### Frequency-Setting Methodologies

#### 1. Fixed/Code-Prescribed Intervals

- Directly applies the maximum interval stated in the governing API code (e.g., API 510's 10-year internal inspection ceiling).
- Simplest to administer; does not account for equipment-specific degradation rate, so it can be conservative for benign service and non-conservative for aggressive/localized corrosion mechanisms if applied uniformly.

#### 2. Remaining-Life (Corrosion Rate) Calculation

- Interval = function of **measured corrosion rate**, **current wall thickness**, and **minimum required thickness (t-min)** per the design code.

$$t_{\text{interval}} = \frac{t_{\text{actual}} - t_{\text{min}}}{CR}$$

where $CR$ is the established corrosion rate (long-term or short-term, whichever governs). The next inspection interval is typically set at half the calculated remaining life (API 510/570 "half-life" rule), subject to the code's stated maximum.

**Example**

A carbon steel piping circuit has $t_{actual} = 0.280$ in, $t_{min} = 0.140$ in (per B31.3 pressure design calc), and an established corrosion rate of $CR = 0.010$ in/yr.

$$\text{Remaining life} = \frac{0.280 - 0.140}{0.010} = 14 \text{ years}$$

Half-life interval = 7 years. Since API 570 Class 2 piping allows a maximum interval of 10 years, the controlling (shorter) interval of 7 years applies.

#### 3. Risk-Based Inspection (RBI)

- Combines **Probability of Failure (PoF)** — driven by active damage mechanisms, materials of construction, and process conditions — with **Consequence of Failure (CoF)** — driven by inventory, toxicity/flammability, and location factors — to calculate a quantitative risk ranking per API 580/581.
- High-risk equipment receives shorter, more intensive inspection intervals and techniques; low-risk equipment can be extended (up to code-permitted maximums) with resources reallocated to higher-risk items.
- RBI is a living program: intervals are recalculated whenever new inspection data, process changes (via MOC), or damage mechanism findings become available.

#### 4. Condition-Based / Predictive Monitoring

- Uses continuous or high-frequency data (vibration analysis, thermography, corrosion probes, acoustic emission, online UT sensors) to trigger inspection or intervention based on actual measured trend rather than a fixed calendar interval.
- Common for rotating equipment (pumps, compressors) where vibration signatures provide earlier and more specific failure warning than periodic manual rounds.

### Frequency Determination Workflow (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 920 300" font-family="sans-serif" font-size="12">
<text x="460" y="20" font-size="15" font-weight="bold" text-anchor="middle">Inspection Frequency Determination (svg_diagram)</text>
<rect x="20" y="50" width="170" height="50" rx="6" fill="#e8f0fe" stroke="#4472c4" />
<text x="105" y="70" text-anchor="middle">Identify governing</text>
<text x="105" y="86" text-anchor="middle">code / RAGAGEP</text>
<rect x="225" y="50" width="170" height="50" rx="6" fill="#e8f0fe" stroke="#4472c4" />
<text x="310" y="70" text-anchor="middle">Determine active</text>
<text x="310" y="86" text-anchor="middle">damage mechanism(s)</text>
<rect x="430" y="50" width="170" height="50" rx="6" fill="#e8f0fe" stroke="#4472c4" />
<text x="515" y="70" text-anchor="middle">Calculate corrosion</text>
<text x="515" y="86" text-anchor="middle">rate / remaining life</text>
<rect x="635" y="50" width="170" height="50" rx="6" fill="#fff2cc" stroke="#bf8f00" />
<text x="720" y="70" text-anchor="middle">Apply RBI risk</text>
<text x="720" y="86" text-anchor="middle">ranking (PoF × CoF)</text>
<line x1="190" y1="75" x2="223" y2="75" stroke="#333" stroke-width="1.3" marker-end="url(#arrM)" />
<line x1="395" y1="75" x2="428" y2="75" stroke="#333" stroke-width="1.3" marker-end="url(#arrM)" />
<line x1="600" y1="75" x2="633" y2="75" stroke="#333" stroke-width="1.3" marker-end="url(#arrM)" />
<line x1="720" y1="100" x2="720" y2="140" stroke="#333" stroke-width="1.3" marker-end="url(#arrM)" />
<rect x="600" y="140" width="240" height="50" rx="6" fill="#e2efda" stroke="#548235" />
<text x="720" y="160" text-anchor="middle">Select interval = MIN(calculated,</text>
<text x="720" y="176" text-anchor="middle">code maximum, prior experience)</text>
<line x1="600" y1="165" x2="330" y2="165" stroke="#333" stroke-width="1.3" marker-end="url(#arrM)" />
<rect x="90" y="140" width="240" height="50" rx="6" fill="#fce4d6" stroke="#c55a11" />
<text x="210" y="160" text-anchor="middle">Document rationale in</text>
<text x="210" y="176" text-anchor="middle">MI/RBI program record</text>
<line x1="210" y1="190" x2="210" y2="230" stroke="#333" stroke-width="1.3" marker-end="url(#arrM)" />
<rect x="90" y="230" width="700" height="45" rx="6" fill="#deebf7" stroke="#2e74b5" />
<text x="440" y="257" text-anchor="middle">Schedule in CMMS/EAM → Execute → Update interval upon new inspection results</text>
</svg>

### Interval Adjustment Triggers

**Key Points**

- **Adverse inspection findings** — pitting, localized thinning, or an unexpected corrosion rate found during an inspection generally shortens the next interval, regardless of what the prior calculation predicted.
- **Process changes via MOC** — a change in feedstock, operating temperature/pressure, or chemistry that introduces or accelerates a damage mechanism (e.g., switching to higher-sulfur crude introducing naphthenic acid corrosion) requires re-evaluation of affected equipment intervals.
- **Near-miss or incident history** — a leak, failure, or precursor event on similar equipment (site-specific or industry-wide, e.g., CSB findings) should trigger an interval review, consistent with 1910.119(j)(4)(ii)'s "prior operating experience" requirement.
- **New damage mechanism identification** — API 571 (Damage Mechanisms Affecting Fixed Equipment) findings from a Corrosion/Damage Mechanism Review can reveal a previously unconsidered mechanism (e.g., high-temperature hydrogen attack, stress corrosion cracking) requiring both new inspection techniques and a shortened interval.
- **Inspection technique limitations** — if a prior inspection technique (e.g., spot UT) is later found inadequate to detect a localized mechanism, the interval and/or technique must be revised, not merely repeated.

### Relief Device Test Frequency Considerations

- Frequency for pressure relief valve (PRV) bench testing is set primarily by **service severity**: clean, non-fouling, non-corrosive service typically supports longer intervals (up to 5 years or more under a documented program); fouling, polymerizing, or corrosive service requires shorter intervals, sometimes annual.
- As-found test results (set-pressure deviation, seat leakage) directly feed the next-interval decision — a documented history of passing "as-found" tests within tolerance can support interval extension under API 510/576-based programs; failures require interval shortening and/or root-cause investigation.
- For PRVs that cannot be removed without a process shutdown, in-situ testing methods or a documented "run to failure with monitoring" justification must be supported by engineering analysis and often a spare/redundant relief path.

### SIS/SIF Proof-Test Interval Determination

- Unlike passive equipment, SIF proof-test frequency is derived analytically from the **target Probability of Failure on Demand (PFDavg)** established during SIL verification, not from a fixed API code table.
- The relationship (simplified, for a single-channel architecture) is approximately:

$$PFD_{avg} \approx \frac{\lambda_{DU} \times TI}{2}$$

where $\lambda_{DU}$ is the dangerous undetected failure rate of the component and $TI$ is the proof-test interval. Shortening $TI$ reduces $PFD_{avg}$; the required $TI$ is back-calculated to meet the SIL target allocated during LOPA/SIL determination.

- Partial stroke testing (PST) can be used between full proof tests to provide partial diagnostic coverage and effectively extend the full-test interval while maintaining the target PFDavg — subject to documented coverage-factor justification.

### Documentation Requirements for Frequency Decisions

- Each equipment item's MI record should show: governing code, baseline code interval, calculated interval (corrosion rate/RBI), selected interval, and the technical rationale if the selected interval differs from the code default.
- Frequency changes (especially extensions) require documented technical justification traceable to inspection data or an approved RBI methodology — undocumented extensions are a frequent finding in PSM compliance audits and OSHA National Emphasis Program (NEP) inspections.
- Frequency records must be retrievable and auditable to demonstrate 1910.119(j)(4) compliance during OSHA inspections or EPA RMP program audits.

### Common Pitfalls

- **Treating code maximums as defaults** — applying the longest permitted interval without a corrosion-rate or RBI basis, rather than treating it as a ceiling.
- **Static RBI assessments** — performing an RBI study once and never updating it as new inspection data or process changes accumulate, causing the assessed risk (and interval) to drift from actual condition. [Inference — the degree of drift is data- and service-dependent and should be evaluated against the specific RBI reassessment cadence in use, typically every 5 years or upon significant new information.]
- **Ignoring short-term vs. long-term corrosion rate divergence** — using only a long-term average rate when a recent inspection shows an accelerating short-term rate can understate risk and over-extend the interval.
- **Decoupling relief device and SIF intervals from process changes** — failing to re-evaluate PRV set pressure/capacity or SIF proof-test intervals when a MOC alters overpressure scenarios or demand rate.

### Related Topics

- Risk-Based Inspection (RBI) per API 580/581
- Corrosion Rate Calculation and Remaining Life Assessment
- API 571 Damage Mechanisms Affecting Fixed Equipment
- Safety Instrumented Function (SIF) Proof Testing and SIL Verification
- Pressure Relief Valve Testing and As-Found/As-Left Documentation
- Management of Change Interfaces with Inspection Programs
- CMMS/EAM Scheduling for Mechanical Integrity
- Turnaround/Shutdown Planning and Inspection Scope Integration
- Corrosion Under Insulation (CUI) Program Frequencies
- Deficiency Correction Timelines (1910.119(j)(5))