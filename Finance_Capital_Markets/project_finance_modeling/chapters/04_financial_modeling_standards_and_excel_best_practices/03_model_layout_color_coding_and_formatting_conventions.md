## Model Layout, Color Coding, and Formatting Conventions

### Overview

Layout, color coding, and formatting conventions are the practical implementation layer of the structural principles discussed under FAST and SMART modeling standards. While those standards articulate *why* consistency matters, this topic addresses the specific, concrete conventions practitioners apply on a cell-by-cell and sheet-by-sheet basis. In project finance specifically, these conventions are not cosmetic — they are the mechanism by which a model auditor, lender, or future model user can distinguish an assumption from a calculation, verify formula consistency, and navigate a model that may span dozens of sheets and hundreds of line items across a 20-30 year forecast horizon.

### Color Coding Conventions

The most widely adopted color coding convention in financial modeling — used across corporate finance, investment banking, and project finance — assigns font color based on the **type of content in a cell**, not its business category.

| Font Color | Cell Content Type | Example |
| --- | --- | --- |
| Blue | Hardcoded input/assumption | A tax rate typed directly into a cell: `25%` |
| Black | Formula referencing cells on the same sheet | `=B5*C5` |
| Green | Formula referencing another sheet or workbook | `='Assumptions'!B5*C5` |
| Red | Formula referencing an external/linked workbook (used less frequently in project finance, where external links are generally discouraged) | `='[OtherFile.xlsx]Sheet1'!A1` |
| Purple/Violet (some conventions) | Links to or from a different model (e.g., macro-driven inputs, VBA outputs) | Varies by firm convention |

[Inference: while blue-for-input and black-for-formula is close to a universal convention across the industry, the exact treatment of green, red, and purple varies meaningfully by firm, and some firms use only a two- or three-color scheme rather than the full five-color version shown above.]

#### Why Color Coding Matters Specifically in Project Finance

- A model auditor's first-pass review often relies heavily on scanning for color consistency — a black-font cell where a blue hardcode is expected (or vice versa) is a common and easily-spotted red flag indicating either an accidental hardcode override or a broken formula link
- Because project finance models are used operationally over many years (not just built once and discarded), color coding allows someone unfamiliar with the model's original construction — such as a new analyst managing ongoing covenant compliance reporting — to quickly distinguish what can be safely changed (blue inputs) from what should never be manually edited (black/green formulas)

### Cell Formatting Conventions

Beyond font color, several formatting conventions support model transparency and reduce error risk:

- **Consistent number formatting by unit type**: currency values formatted consistently (e.g., thousands separators, consistent decimal places), percentages formatted as percentages rather than raw decimals, and dates formatted consistently across the model
- **Negative number conventions**: parentheses for negative numbers `(1,000)` rather than a leading minus sign `-1,000`, a widely used convention that improves readability in dense financial statements, though the specific choice is a firm convention rather than a universal rule
- **Units clearly labeled**: every row should indicate its unit (e.g., "USD '000", "%", "MW") either in the row label or a dedicated units column, avoiding ambiguity about scale
- **Borders and shading used sparingly and consistently**: typically reserved for marking subtotal/total rows, section headers, or key output cells — overuse of borders and shading reduces rather than enhances readability
- **Consistent column widths and row heights**: particularly important where a model is printed or exported for lender review, ensuring a clean, professional presentation

### Sheet and Workbook Layout Conventions

#### Standard Sheet Ordering

A widely used ordering convention (reflecting FAST's "Structured" principle) organizes sheets to follow the logical flow of the model:

```mermaid
flowchart LR
    A["Cover / Instructions"] --> B["Assumptions"]
    B --> C["Construction"]
    C --> D["Operations"]
    D --> E["Debt Sizing & Schedule"]
    E --> F["Tax & Depreciation"]
    F --> G["Financial Statements"]
    G --> H["Cash Flow Waterfall"]
    H --> I["Covenants & Ratios"]
    I --> J["Returns"]
    J --> K["Sensitivities / Outputs / Dashboard"]
```

- **Cover/Instructions sheet**: often includes model version control information, key contact details, a summary of key outputs, and navigation instructions
- **Assumptions sheet(s)**: centralizes all hardcoded inputs, grouped logically (macro assumptions, operating assumptions, financing assumptions, tax assumptions)
- **Calculation sheets**: organized in the order cash flows naturally through the model (construction → operations → debt → financial statements → waterfall)
- **Output/Dashboard sheet**: typically the only sheet a senior reviewer or lender needs to open for a summary view, pulling key outputs (DSCR profile, equity IRR, sensitivities) from throughout the model

#### Consistent Time-Period Orientation

- Time periods should run consistently in one direction (typically left to right, one column per period) across every calculation sheet in the model
- Period labeling (date, period number, phase indicator such as "Construction Year 2" or "Operating Year 5") should be consistent and cross-referenced from a single master period/date row, rather than independently re-entered on each sheet
- Mixed granularity (e.g., monthly during construction, semi-annual during operations) requires particularly careful handling to avoid misalignment — often addressed through a separate monthly and semi-annual/annual sheet structure with clearly defined linking/aggregation logic between them

#### Naming Conventions

- **Sheet names**: short, descriptive, and consistently ordered (e.g., "1. Assumptions", "2. Construction", "3. Operations") — numeric prefixes help maintain visual ordering in the sheet tab bar regardless of how sheets are physically arranged
- **Named ranges**: used judiciously for key assumptions or frequently referenced cells (e.g., naming a cell "Target_DSCR" rather than referencing it only by cell address), improving formula readability — though over-use of named ranges can itself reduce transparency if a reviewer cannot easily see which physical cell a name refers to
- **Row labels**: descriptive and consistent in terminology across sheets — e.g., always referring to "Cash Flow Available for Debt Service" by the same label and abbreviation (CFADS) throughout the model, not alternating with unlabeled synonyms

### Structural Conventions Supporting Auditability

| Convention | Rationale |
| --- | --- |
| One row = one calculation concept | Avoids combining unrelated calculations in a single row, which obscures individual logic |
| Formulas consistent across each row | A formula in period 5 should have the identical structure to period 6, just shifted references — inconsistency signals a likely error |
| No hidden rows/columns containing live calculations | Hidden cells used to bury working calculations undermine transparency; if hidden, they should only be housekeeping/reference rows, not core mechanics |
| Check rows / error flags | Dedicated rows that flag balance sheet imbalances, negative cash balances, or covenant breaches with a visible TRUE/FALSE or 0/1 indicator, typically aggregated into a single "Model Checks" summary |
| Clear section headers/dividers | Visual separation between assumption categories or calculation blocks, aiding navigation without requiring cell-by-cell inspection |

### Example: Model Checks Row Implementation

A well-formatted project finance model typically includes a dedicated **checks row or checks sheet** aggregating all internal consistency tests into a single visible location:

| Check | Formula Logic | Status |
| --- | --- | --- |
| Balance sheet balances | `=IF(ROUND(Assets-Liabilities-Equity,0)=0,"OK","ERROR")` | OK |
| Cash balance never negative | `=IF(MIN(Cash_Row)>=0,"OK","ERROR")` | OK |
| DSCR covenant not breached | `=IF(MIN(DSCR_Row)>=Covenant_Threshold,"OK","BREACH")` | OK |
| Circularity switch engaged correctly | `=IF(Circularity_Switch=1,"Active","Broken")` | Active |
| Waterfall fully allocates available cash | `=IF(ROUND(Cash_Available-SUM(Waterfall_Uses),0)=0,"OK","ERROR")` | OK |

Consolidating these checks into a single, prominently formatted (often color-flagged, e.g., red highlighting for any "ERROR" or "BREACH" result) location allows a reviewer to instantly confirm model integrity without manually re-deriving every formula — directly supporting the "Transparent" principle from the FAST standard and materially reducing model audit time.

### Common Formatting Pitfalls in Practice

- **Inconsistent color coding after ad hoc edits**: a hardcode accidentally typed over a formula cell, left in black font, silently breaking the intended input/calculation separation
- **Merged cells**: commonly discouraged in financial models because they interfere with formula referencing, copy-paste operations, and can cause unpredictable behavior when rows/columns are inserted or deleted
- **Excessive use of decorative formatting**: heavy use of colors, borders, or fonts unrelated to the input/formula/link convention, which dilutes the signal value of the standard color coding scheme
- **Inconsistent decimal precision across related figures**: displaying some percentages to zero decimal places and others to two, making cross-comparison harder
- **Orphaned formatting from copy-paste**: formatting (borders, colors) copied along with formulas into cells where it is no longer appropriate, cluttering the visual structure over time

### Key Points

- The blue-input/black-formula/green-link color coding convention is the most widely recognized standard in financial modeling and directly supports rapid visual auditing, particularly valuable given the long operational life of project finance models
- Sheet ordering and naming conventions should reflect the logical flow of cash through the model (assumptions → construction → operations → debt → statements → outputs), aiding navigation for reviewers unfamiliar with the specific model's construction
- Consistent formula structure across each row is one of the single most effective error-prevention and error-detection techniques, since inconsistency is immediately visible on visual inspection
- A dedicated, consolidated model checks row or sheet — flagging balance sheet integrity, cash balance, and covenant compliance — significantly reduces the effort required for both internal review and independent lender-side model audit
- Formatting conventions are not cosmetic preferences in project finance; they directly affect model audit cost, error detection speed, and the ability of future users to safely operate and update the model over its multi-decade operational life

### Related Topics

- FAST and SMART Modeling Standards
- Core Principles of Project Finance Financial Modeling
- Circularity Management Techniques in Excel Financial Models
- Independent Model Audit Process and Common Findings
- Documentation and Model Handover Practices in Project Finance
- Scenario and Sensitivity Analysis Design
- Version Control and Model Change Management