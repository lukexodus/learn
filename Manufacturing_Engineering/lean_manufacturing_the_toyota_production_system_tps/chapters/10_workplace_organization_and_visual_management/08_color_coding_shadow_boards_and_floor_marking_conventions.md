## Color Coding, Shadow Boards, and Floor Marking Conventions

### Overview

Color coding, shadow boards, and floor marking are the concrete physical implementations through which management by sight and 5S's Set in Order principle become real on the shop floor. Where "management by sight" describes the philosophy and "5S" describes the broader organizational discipline, this topic covers the specific, practical conventions — which colors mean what, how a shadow board is built, how floor tape is laid out and what each pattern signifies — that make a workplace's normal condition and correct locations instantly recognizable to anyone present. Consistency of these conventions, both within a facility and increasingly across a company or industry, is what allows a new operator, a visiting auditor, or an emergency responder to correctly interpret the workplace without instruction.

### Key Points

- Color meaning should be assigned deliberately and used consistently across an entire facility — the same color meaning something different in different areas defeats the "understood at a glance" purpose these conventions exist to serve
- Shadow boards make a missing tool visible as an obvious empty space, converting "is anything missing?" from a question requiring a mental checklist into a fact visible in under a second
- Floor marking conventions typically distinguish at minimum: walkways/pedestrian paths, staging/storage locations, hazard or restricted zones, and equipment footprints — with color and line style carrying the distinction
- There is no single universal global standard that mandates exact colors for every purpose — many organizations follow common industry conventions (often influenced by ANSI/OSHA-adjacent practice in the U.S., or ISO-informed practice elsewhere) but final assignments are typically set at the facility level and documented
- These conventions only function as intended when they are actually standardized and audited (tying back to 5S's Standardize and Sustain phases) — an inconsistently applied color scheme is often worse than none, because it teaches people to distrust the visual signal

### Color Coding Conventions

**General principle**: colors should map to a small, stable set of meanings, applied the same way everywhere in the facility, so a person doesn't need area-specific knowledge to interpret them correctly.

**Commonly used color meanings in lean/5S environments** (facility-specific conventions vary; the following reflects widely observed practice rather than a single mandatory standard):

| Color | Typical meaning | Common applications |
| --- | --- | --- |
| Red | Danger, stop, defect, abnormal/out-of-spec | Andon "line stopped" state, defective-parts bins, emergency stop buttons, fire safety equipment locations |
| Yellow | Caution, attention needed, in-progress/borderline | Andon "help requested" state, caution zones, gauge caution ranges, red-tag holding areas sometimes marked yellow |
| Green | Normal, running correctly, go/clear | Andon "running normally" state, gauge normal-operating ranges, clear/available floor zones |
| Orange | Warning, particular hazard classes | Physical hazard zones (moving machinery, pinch points), some material-handling equipment |
| Blue | Informational, mandatory action markers | Mandatory PPE signage, informational signage not tied to a hazard |
| Black/white (stripes) | Physical hazard boundary, general demarcation | Boundary striping around fixed hazards, general floor demarcation not covered by a more specific code |

[Inference] These specific color-to-meaning mappings reflect commonly observed convention in lean and safety-management practice, influenced in varying degrees by ANSI Z535 (US) and comparable regional standards, but are not a single universally mandated scheme — organizations define and document their own facility-specific color legend, and the exact palette in use should always be confirmed against the specific facility's documented standard rather than assumed from general convention.

**Design principles for color coding**:

- Limit the palette to as few distinct meanings as practical — a scheme with a dozen subtly different colors defeats instant recognizability
- Post the legend visibly (a color-key reference) in areas where the scheme is used, especially during initial rollout, though the long-term goal is that the meaning becomes intuitive without needing to consult the legend
- Apply the same color meaning consistently across all applications within the facility — if red means "stopped/abnormal" on an andon board, it should not simultaneously mean "high-priority but running fine" on a different board type in the same facility
- Consider color-vision-deficiency accessibility: relying on color alone (especially red/green distinctions, the most common form of color blindness) without a secondary cue (shape, position, text, pattern) can make signals invisible to a portion of any workforce

### Shadow Boards

A shadow board is a tool storage panel with each tool's outline (its "shadow") pre-marked at its designated location, so the tool's presence or absence is visible without reading a label or checking a list.

**Construction approaches**:

- **Painted/drawn outline**: the tool's silhouette is traced or stenciled directly onto a pegboard or panel background, often in a contrasting color to the panel
- **Foam cutout / shadow foam**: a foam insert is cut to the exact shape of each tool, so the tool nests into its own cavity — commonly used in toolboxes and drawer systems, providing both visual and physical location control
- **Labeled outline with tool name/number**: combining the silhouette with a printed label reduces ambiguity for tools with similar outlines and assists less experienced operators or temporary staff

**Design principles**:

- **One tool, one location, one shadow** — avoid ambiguous shared spaces where multiple tools could plausibly belong, which reintroduces the "where does this actually go" uncertainty the board exists to eliminate
- **Position by frequency of use** — tools used most often should occupy the most accessible positions, directly informed by the same motion-waste analysis that shapes Standardized Work and general Set in Order layout
- **Group logically** — tools used together in the same task sequence are often positioned adjacently, reducing motion during a multi-tool operation
- **Make the empty state loud** — a strong color contrast between the panel background and the tool color (and the empty silhouette) ensures a missing tool reads as obviously wrong, not as a subtle gap someone might overlook
- **Tie to accountability, not just tidiness** — an empty shadow board silhouette should have a clear expected response (return the tool immediately, or investigate why it's out and for how long), otherwise the board functions as decoration rather than a visual control

### Floor Marking Conventions

Floor marking uses tape, paint, or permanent striping to define zones and paths on the plant floor, making spatial organization visible from a distance and at eye level (unlike labels or signs, which require looking at a specific point).

**Common floor marking categories and typical conventions**:

- **Walkways/pedestrian paths**: often marked with continuous lines (commonly white or yellow, per facility convention) defining the boundary pedestrians should stay within, separating foot traffic from vehicle and equipment paths
- **Staging/WIP areas**: rectangular outlines (often yellow or white) marking exactly where a pallet, cart, or bin of material should sit — oversized or missing material relative to the marked outline is immediately visible
- **Equipment footprints**: outlines marking the fixed location of mobile equipment (carts, tool stands) when not in use, so their absence from the marked spot is visible just as a shadow board makes a missing tool visible
- **Hazard/restricted zones**: often striped (commonly black/yellow or red/white diagonal striping) to indicate an area requiring caution or restricted access — swing radius of equipment, electrical panel clearance zones, pinch points
- **Red-tag holding areas**: a marked zone (often distinctly colored from general staging) where items awaiting Sort-phase disposition are held pending a decision
- **Quality hold / quarantine zones**: a distinctly marked and often physically separated area for suspect or nonconforming material, preventing accidental co-mingling with conforming stock
- **Kanban/inventory zones**: floor marking sometimes incorporates min/max lines directly on the floor or shelf, so material stacked above the "max" line or below the "min" line is a visible signal without counting

**Design principles**:

- **Line style should carry meaning, not just color** — solid lines, dashed lines, and diagonal striping can each be assigned distinct meanings (e.g., solid = fixed boundary, dashed = flexible/temporary zone, diagonal stripe = hazard) to add information density without adding more colors
- **Widths and consistency matter for recognizability** — using a consistent tape width and line style for the same purpose across the facility helps the pattern become instantly recognizable rather than requiring area-specific interpretation
- **Keep marking current** — floor marking degrades with foot and equipment traffic; a maintenance/reapplication schedule (often tied into the broader 5S audit cadence) prevents markings from becoming faded or misleading
- **Avoid marking overload** — too many zones, colors, and line types in a small area can make the floor as hard to interpret as no marking at all; marking should be proportional to the complexity that actually needs to be communicated

### Illustration: Common Floor Marking Legend (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 900 380" font-family="Arial, sans-serif">
<text x="450" y="30" text-anchor="middle" font-size="20" font-weight="bold">Common Floor Marking Conventions (svg_diagram)</text>
<rect x="40" y="60" width="120" height="14" fill="none" stroke="#eab308" stroke-width="4" />
<text x="180" y="72" font-size="13">Pedestrian walkway boundary (solid line)</text>
<rect x="40" y="100" width="120" height="50" fill="none" stroke="#f5f5f5" stroke-width="3" stroke-dasharray="8,5" />
<rect x="40" y="100" width="120" height="50" fill="#fafafa" opacity="0.3" stroke="#a1a1aa" stroke-width="2" />
<text x="180" y="130" font-size="13">Staging/WIP area (dashed outline)</text>
<g transform="translate(40,170)">
<rect width="120" height="40" fill="url(#hazardStripe)" stroke="#000" stroke-width="1" />
</g>
<text x="180" y="195" font-size="13">Hazard/restricted zone (diagonal stripe)</text>
<rect x="40" y="230" width="120" height="40" fill="#fde68a" stroke="#92400e" stroke-width="2" />
<text x="180" y="255" font-size="13">Red-tag holding area</text>
<rect x="40" y="290" width="120" height="40" fill="#fecaca" stroke="#b91c1c" stroke-width="2" />
<text x="180" y="315" font-size="13">Quality hold / quarantine zone</text>
<g transform="translate(480,95)">
<rect x="0" y="0" width="150" height="120" rx="6" fill="#e5e7eb" stroke="#374151" stroke-width="2" />
<ellipse cx="40" cy="35" rx="18" ry="8" fill="none" stroke="#6b7280" stroke-width="2" stroke-dasharray="3,2" />
<rect x="80" y="55" width="50" height="12" rx="2" fill="none" stroke="#6b7280" stroke-width="2" stroke-dasharray="3,2" />
<rect x="25" y="80" width="14" height="30" fill="none" stroke="#6b7280" stroke-width="2" stroke-dasharray="3,2" />
<text x="75" y="-8" text-anchor="middle" font-size="12" font-weight="bold">Shadow Board (partial)</text>
</g>
<text x="555" y="235" text-anchor="middle" font-size="12">Empty silhouettes = missing tools,</text>
<text x="555" y="252" text-anchor="middle" font-size="12">visible instantly without a checklist</text>
</svg>

### Common Failure Modes

- **Inconsistent color meaning across areas**: red meaning "stopped" on one line's andon and "high-priority-but-fine" on another department's board, forcing anyone moving between areas to relearn the scheme
- **Faded or damaged floor marking never reapplied**: markings that degrade below clear visibility silently lose their function, and without a maintenance schedule this decay often goes unnoticed until an audit specifically checks for it
- **Ambiguous shadow board layout**: multiple similarly shaped tools sharing a poorly differentiated space, reintroducing the "which one goes where" uncertainty the board was meant to eliminate
- **Color-only signals with no secondary cue**: relying purely on red/green distinction without shape, position, or text backup excludes operators with red-green color vision deficiency from reliably reading the signal
- **Marking installed without operator input**: floor zones drawn based on an idealized layout rather than actual material flow, resulting in markings operators route around rather than use, undermining the whole scheme's credibility
- **No documented legend**: relying on informal, orally transmitted knowledge of what each color or marking means, so new hires, temporary staff, or visitors cannot correctly interpret the floor without being told
- **Treating marking as purely cosmetic**: applying floor tape without tying it to an actual standard (correct staging quantity, correct walkway boundary enforcement), producing marking that looks organized but carries no real control function

### Roles and Responsibilities

- **5S Champion / Continuous Improvement Facilitator**: documents the facility-wide color legend and floor marking convention, ensures consistency is maintained across areas, and coordinates updates when conventions change
- **Team Leader**: designs and maintains shadow boards and localized floor marking for their area, in line with the facility-wide legend rather than inventing area-specific meanings
- **Safety/EHS function**: typically owns hazard-related color and marking conventions specifically, ensuring alignment with applicable regulatory guidance and consistent application across the facility
- **Operators**: provide input on shadow board tool placement and floor zone practicality based on actual task flow, and are expected to maintain marked conditions (returning tools, respecting zone boundaries) as part of daily Sustain discipline
- **Maintenance/Facilities**: executes floor marking reapplication on a defined schedule, typically triggered by 5S audit findings of faded or damaged marking

### Example

A machine shop standardizes its floor marking legend facility-wide: solid yellow lines for pedestrian walkways, dashed white outlines for staging areas, black/yellow diagonal striping for machine swing-radius hazard zones, and a distinctly colored (light blue) zone for quality-hold material, chosen specifically to be visually distinct from the red-tag holding area's yellow. Each machining cell receives a shadow board built with foam cutouts for hand tools, positioned so the most frequently used tools (calipers, deburring tools) sit at the most accessible height and location, informed by a brief motion-time observation of the operator's actual task sequence.

During the facility's first cross-functional 5S audit, an auditor unfamiliar with a specific cell can nonetheless immediately identify a missing measuring tool (empty foam cutout), correctly interpret a piece of material sitting on the quality-hold blue zone as suspect rather than ready-to-use, and recognize the diagonal-striped zone around a robotic arm as a hazard boundary — none of which required asking a local operator for explanation, because the conventions were applied identically to what the auditor had already learned from a different area of the same facility.

### Conclusion

Color coding, shadow boards, and floor marking are the tangible mechanisms that convert the abstract principle of management by sight into a physically navigable workplace: a consistent, small, deliberately assigned color palette; tool boards that make absence as visible as presence; and floor conventions that distinguish walkways, staging, hazards, and hold areas without requiring a label to be read up close. Their effectiveness rests entirely on consistency and maintenance — the same color or marking pattern must mean the same thing everywhere in the facility, and degraded or faded markings must be refreshed on a defined schedule — because an inconsistently or carelessly maintained visual scheme actively teaches people to stop trusting what they see, undermining the exact instant-recognizability these conventions exist to provide.

### Related Topics

- Management by sight and abnormality detection
- 5S: Set in Order (Seiton) and Standardize (Seiketsu) phases
- Visual controls versus visual displays
- Andon color-coding conventions and escalation signals
- Point-of-use storage and motion-waste reduction
- Red-tag technique and disposition holding areas
- Quality hold/quarantine procedures and material segregation
- Safety signage standards (ANSI Z535, ISO 7010, and regional equivalents)
- Kanban min/max visual stock indicators
- 5S audit checklists and floor-marking maintenance cadence