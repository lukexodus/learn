## Bottom-Up versus Top-Down Estimating


### Definition

Bottom-up and top-down estimating represent two opposing directional philosophies for developing project duration and cost estimates. **Bottom-up estimating** builds the total estimate by summing detailed estimates for individual work package or activity-level components. **Top-down estimating** derives the total estimate first, at a high level, then allocates it downward across phases or deliverables—often using analogous or parametric techniques applied to the project as a whole rather than to its individual pieces.

### Bottom-Up Estimating

#### Methodology

1. Decompose the project into a detailed Work Breakdown Structure (WBS) down to the work package or activity level
2. Estimate duration and cost for each individual activity independently, using the most appropriate technique per activity (analogous, parametric, or expert judgment)
3. Aggregate (roll up) individual estimates through the WBS hierarchy to produce phase-level and total project figures
4. Add contingency reserves at the appropriate level (activity, work package, or project)

#### Formula (Aggregation)

$$Total\ Estimate = \sum_{i=1}^{n} Activity\ Estimate_{i}$$

**Example**

A renovation project WBS decomposes into 40 individual activities. Each activity is estimated independently:

- Demolition: 15 activities totaling 320 labor-hours, $28,000
- Framing: 10 activities totaling 480 labor-hours, $65,000
- MEP (Mechanical/Electrical/Plumbing): 12 activities totaling 600 labor-hours, $110,000
- Finishes: 3 activities totaling 200 labor-hours, $42,000

$$Total\ Cost = 28{,}000 + 65{,}000 + 110{,}000 + 42{,}000 = \$245{,}000$$



$$Total\ Labor\ Hours = 320 + 480 + 600 + 200 = 1{,}600\ \text{hours}$$

**Key Points**

- Generally the most accurate technique because it is grounded in detailed, specific scope knowledge
- Requires a fully or near-fully decomposed WBS before it can be performed
- Time-intensive and resource-intensive to produce compared to top-down methods
- Errors at the individual activity level tend to average out somewhat across a large number of activities (statistical smoothing), though systematic biases (e.g., consistently optimistic estimators) do not cancel out

### Top-Down Estimating

#### Methodology

1. Establish a total project estimate using historical data from comparable whole projects (analogous) or a high-level parametric relationship
2. Allocate the total downward across major phases or deliverables, typically using historical percentage splits (e.g., "design is typically 12% of total construction cost")
3. Refine allocations as more scope detail becomes available, progressively replacing top-down splits with bottom-up detail

#### Example: Percentage Allocation

A historical benchmark indicates commercial building projects typically break down as:

- Design: 10%
- Site work: 15%
- Structure: 35%
- MEP: 25%
- Finishes: 15%

For a total top-down estimate of $4,000,000:

$$Design = 4{,}000{,}000 \times 0.10 = \$400{,}000$$



$$Structure = 4{,}000{,}000 \times 0.35 = \$1{,}400{,}000$$

**Key Points**

- Fast to produce, requiring minimal scope detail
- Well-suited to early feasibility studies, screening decisions, and initial budget authorization requests
- Lower accuracy since it relies on historical proportional relationships that may not match the specific project's actual composition
- Closely related to (and often implemented via) analogous or parametric estimating techniques applied at the whole-project level

### Comparative Analysis

| Aspect | Bottom-Up | Top-Down |
| --- | --- | --- |
| Direction of calculation | Individual activities → aggregated total | Total project → allocated to components |
| Required scope detail | High (detailed WBS needed) | Low (conceptual scope sufficient) |
| Typical accuracy | High (-5% to +10%, definitive-class) [Unverified — specific percentage ranges are commonly cited industry heuristics and vary by source/domain] | Low to moderate (-25% to +75%, ROM-class) [Unverified — same caveat applies] |
| Time/effort to produce | High | Low |
| Best project phase | Detailed planning, execution readiness | Initiation, feasibility, screening |
| Estimator input needed | Many SMEs across disciplines | Few senior estimators/experts |
| Sensitivity to WBS quality | Very high — poor WBS decomposition directly degrades accuracy | Lower — not dependent on detailed decomposition |
| Common techniques used | Bottom-up itself, sometimes parametric per activity | Analogous, parametric (whole-project level) |

### Relationship to Progressive Elaboration

Most mature project management practice does not treat bottom-up and top-down as mutually exclusive one-time choices, but as sequential stages within **progressive elaboration**:

```mermaid
flowchart LR
    A[Concept/Initiation<br/>Top-Down ROM Estimate] --> B[Preliminary Planning<br/>Top-Down Parametric Refinement]
    B --> C[Detailed Planning<br/>WBS Decomposition Complete]
    C --> D[Bottom-Up Estimate<br/>Definitive Budget]
    D --> E[Baseline Approved<br/>Performance Measurement Baseline]
    E --> F[Execution & EVM Tracking]

    style A fill:#ffd580,stroke:#cc8400
    style D fill:#a8c8f0,stroke:#2c5f9e
    style E fill:#a8d5ba,stroke:#3a7d5c
```

**Key Points**

- A project typically starts with a top-down ROM estimate for initial approval/funding gates
- As the WBS matures and scope is decomposed, the estimate transitions to bottom-up for the definitive control budget
- Reconciliation between the two is a common project control checkpoint—large discrepancies between the original top-down estimate and the emerging bottom-up total should trigger a scope or assumption review, not automatic acceptance of the new number

### Application to CPM

- **Bottom-up** duration estimating populates individual activity nodes directly, since each activity's duration is independently derived (often from parametric productivity rates or resource-loaded calculations) before the network diagram's forward/backward pass is run
- **Top-down** duration estimating is typically used only for very early schedule feasibility checks—e.g., "similar projects took 18 months end-to-end"—and is rarely granular enough to support meaningful critical path or float calculations at the activity level
- A detailed CPM network schedule, by its nature, requires bottom-up activity-level durations; top-down figures serve primarily as sanity checks or milestone targets against which the bottom-up schedule is validated

### Application to EVM

- The **Performance Measurement Baseline (PMB)** and **Budget at Completion (BAC)** are ideally built bottom-up, since EVM's core mechanics (Earned Value calculated per work package based on percent complete against a specific budgeted amount) require budget granularity at the control account or work package level
- Top-down estimates may establish the initial funding ceiling or Management Reserve boundary, but control accounts used for EVM performance measurement are generally expected to be bottom-up derived for auditability and traceability
- A purely top-down budget allocated by percentage split, without underlying work package detail, generally cannot support meaningful EVM metrics (CPI, SPI) because there is no granular basis for objective percent-complete measurement

### Hybrid Approaches

**Key Points**

- Many organizations use a hybrid: top-down for the overall project ceiling and high-level phase allocations, combined with bottom-up detail for high-risk, high-cost, or high-uncertainty work packages specifically
- Rolling wave planning is a related concept: near-term work is planned and estimated bottom-up in detail, while distant future work remains at a top-down/placeholder level until it approaches execution
- This hybrid reduces upfront estimating effort while preserving accuracy where it matters most (imminent, high-value work)

### Diagram: Estimating Direction Illustration

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 320" font-family="Arial, sans-serif">
<text x="320" y="20" text-anchor="middle" font-size="14" font-weight="bold">Bottom-Up vs. Top-Down Estimating Flow (svg_diagram)</text>

<text x="150" y="50" text-anchor="middle" font-size="12" font-weight="bold">Bottom-Up</text>

<rect x="70" y="230" width="50" height="30" fill="`#a8c8f0`" stroke="`#2c5f9e`" />

<rect x="130" y="230" width="50" height="30" fill="`#a8c8f0`" stroke="`#2c5f9e`" />

<rect x="190" y="230" width="50" height="30" fill="`#a8c8f0`" stroke="`#2c5f9e`" />

<text x="90" y="250" font-size="9" text-anchor="middle">Act. 1</text>

<text x="150" y="250" font-size="9" text-anchor="middle">Act. 2</text>

<text x="210" y="250" font-size="9" text-anchor="middle">Act. 3</text>

<line x1="90" y1="230" x2="150" y2="150" stroke="#333" stroke-width="1.5" />
<line x1="150" y1="230" x2="150" y2="150" stroke="#333" stroke-width="1.5" />
<line x1="210" y1="230" x2="150" y2="150" stroke="#333" stroke-width="1.5" />
<rect x="105" y="110" width="90" height="40" fill="#a8d5ba" stroke="#3a7d5c" />
<text x="150" y="135" text-anchor="middle" font-size="10">Total Project</text>
<polygon points="150,105 145,115 155,115" fill="#2c5f9e" />

<text x="470" y="50" text-anchor="middle" font-size="12" font-weight="bold">Top-Down</text>

<rect x="425" y="110" width="90" height="40" fill="`#a8d5ba`" stroke="`#3a7d5c`" />

<text x="470" y="135" text-anchor="middle" font-size="10">Total Project</text>

<line x1="470" y1="150" x2="410" y2="230" stroke="#333" stroke-width="1.5" />
<line x1="470" y1="150" x2="470" y2="230" stroke="#333" stroke-width="1.5" />
<line x1="470" y1="150" x2="530" y2="230" stroke="#333" stroke-width="1.5" />
<rect x="390" y="230" width="50" height="30" fill="#a8c8f0" stroke="#2c5f9e" />
<rect x="445" y="230" width="50" height="30" fill="#a8c8f0" stroke="#2c5f9e" />
<rect x="505" y="230" width="50" height="30" fill="#a8c8f0" stroke="#2c5f9e" />
<text x="415" y="250" font-size="9" text-anchor="middle">Phase A</text>
<text x="470" y="250" font-size="9" text-anchor="middle">Phase B</text>
<text x="530" y="250" font-size="9" text-anchor="middle">Phase C</text>
<polygon points="470,225 465,215 475,215" fill="#2c5f9e" />

<text x="150" y="290" text-anchor="middle" font-size="10" fill="#666">Detail → Total</text>

<text x="470" y="290" text-anchor="middle" font-size="10" fill="#666">Total → Allocated Detail</text>

</svg>

### Advantages and Limitations Summary

**Key Points — Bottom-Up Advantages**

- Highest achievable accuracy given sufficient scope definition
- Provides granular traceability supporting EVM control accounts
- Surfaces scope gaps or omissions during the decomposition process itself

**Key Points — Bottom-Up Limitations**

- Requires significant time, resources, and mature WBS before it can begin
- Impractical for early-stage decisions where speed matters more than precision
- Risk of "estimating fatigue" or inconsistent rigor across a large number of individual activity estimates

**Key Points — Top-Down Advantages**

- Fast, low-cost, ideal for early screening and go/no-go decisions
- Useful for sanity-checking bottom-up totals once they are developed
- Requires only senior-level expertise rather than broad SME involvement

**Key Points — Top-Down Limitations**

- Lower accuracy, unsuitable as the basis for a contractual or definitive control budget in most cases
- Historical percentage splits may not reflect the specific project's unique scope composition
- Provides insufficient granularity to support detailed EVM performance measurement

### Best Practices

**Key Points**

- Match the estimating direction to the project phase: top-down for initiation/feasibility, bottom-up for the control baseline
- Use top-down estimates as a reasonableness check against the emerging bottom-up total, investigating significant variances rather than automatically discarding either figure
- Ensure the WBS used for bottom-up estimating follows the 100% rule (all in-scope work is captured, with no gaps or overlaps) to avoid systematic underestimation
- Document which technique was used for each estimate in the estimating basis documentation, since mixing techniques without disclosure undermines auditability
- For EVM readiness, plan for bottom-up estimating to mature to the control account level before baseline approval

### Related Topics

- Work Breakdown Structure (WBS) decomposition and the 100% rule
- Analogous and parametric estimating techniques
- Rolling wave planning and progressive elaboration
- Rough Order of Magnitude (ROM) vs. Definitive estimate classifications
- Performance Measurement Baseline (PMB) development
- Control accounts and work package budgeting in EVM
- Contingency reserve determination by estimating technique