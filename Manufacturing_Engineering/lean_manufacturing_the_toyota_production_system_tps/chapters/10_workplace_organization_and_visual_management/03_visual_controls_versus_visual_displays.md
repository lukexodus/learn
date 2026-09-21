## Visual Controls Versus Visual Displays

### Overview

Visual controls and visual displays are both forms of visual management, but they differ in a functionally important way: a visual control actively regulates behavior or process flow — it makes the correct action obvious, constrains an incorrect one, or triggers a required response — while a visual display simply presents information for someone to read and interpret at their own discretion. The distinction matters in TPS because it is easy to fill a facility with dashboards, charts, and posted metrics (visual displays) while leaving the actual mechanisms that stop defects, signal abnormalities, and guide correct action (visual controls) underdeveloped. A facility can look highly "visual" and still have weak process control if most of what's posted is display rather than control.

### Key Points

- A visual control changes what happens or what a person is physically or procedurally guided to do; a visual display only changes what a person knows, if they choose to look and interpret it
- Visual controls are tightly coupled to a specific required response (stop the line, use this bin, don't proceed); visual displays report a status or trend with no built-in required action
- Andon, kanban cards, shadow boards, and floor-marked pedestrian lanes are visual controls; a posted safety-incident chart or a monthly OEE dashboard is typically a visual display
- The same physical artifact (e.g., a chart) can function as either, depending on whether it is tied to a defined response threshold and escalation path, or simply posted for awareness
- Effective visual management systems deliberately combine both: controls to constrain and trigger action at the point of work, and displays to inform broader awareness, trend tracking, and management review

### Defining Visual Controls

A visual control is a device or signal engineered so that the correct state, correct action, or an abnormal condition is apparent without interpretation, verbal communication, or specialized expertise — and, critically, is paired with an expected response. The hallmark of a true visual control is that a defined action follows automatically or near-automatically from what is seen.

Common visual controls in TPS environments:

- **Andon lights/cords**: signal a stopped or at-risk process; the required response (team leader responds immediately) is built into the system, not left to discretion
- **Kanban cards**: signal exactly when and how much to produce or move; acting on the card is the process, not merely information about the process
- **Shadow boards**: a missing tool is visually obvious as an empty outline, and the required response (return the tool, or investigate why it's missing) is implicit in the design
- **Floor marking**: designates walkways, staging areas, and hazard zones; stepping outside a marked lane is immediately visible as a deviation
- **Min/max stock lines or bins**: the visual level of material directly indicates whether to reorder, with no calculation required
- **Color-coded gauges** (red/yellow/green zones on a pressure or temperature gauge): the needle's position relative to the marked zone directly indicates whether the process is in or out of the acceptable range, without requiring the operator to recall a numeric spec
- **Poka-yoke fixtures with visual/physical feedback**: a part that only fits one way, or a fixture that visibly won't close if a component is missing, is a visual control in the fullest sense — it doesn't just inform, it prevents the incorrect action from proceeding

### Defining Visual Displays

A visual display presents data, status, or trend information for a viewer to read, interpret, and act on using their own judgment — there is no engineered or automatic linkage between what is displayed and a specific required response.

Common visual displays:

- **Performance dashboards** (OEE, defect rate, throughput trend charts) posted in a break room or office
- **Safety statistics boards** (days since last incident, injury trend line)
- **Organizational charts, policy postings, or general announcements**
- **Historical Pareto charts** of defect types from a completed analysis, posted for reference
- **Production schedule boards** that show planned versus actual output without a built-in escalation trigger

Displays are valuable — they build shared situational awareness, support management review, and provide the data on which future kaizen or root-cause work draws — but they do not, by themselves, constrain behavior or guarantee a response.

### The Distinguishing Test

A practical test for whether a given visual artifact is functioning as a control or a display: **if the intended response does not occur, does anything in the system detect that and escalate?**

- An andon signal that goes unanswered typically has a built-in escalation (a timer, an audible alarm, a supervisor page) — this is characteristic of a control
- A defect-rate dashboard that shows a worsening trend, with no defined threshold or auto-escalation, relies entirely on someone happening to notice and choosing to act — this is characteristic of a display

Neither label is a judgment of value — a well-designed display that management consistently reviews and acts on can drive real improvement. But labeling it accurately matters, because organizations sometimes believe they have installed "control" when they have actually only installed "information," and are surprised when a clearly visible problem persists because no one was specifically triggered to respond to it.

### Comparison Table

| Dimension | Visual Control | Visual Display |
| --- | --- | --- |
| Primary function | Regulates or triggers a specific action | Informs; supports interpretation and awareness |
| Response mechanism | Built-in — action is expected, sometimes physically enforced | Discretionary — viewer decides whether/how to respond |
| Escalation on non-response | Often engineered (timer, alarm, supervisor page) | Typically absent unless separately designed |
| Timescale | Real-time or near-real-time, point of work | Often periodic — shift, daily, weekly, monthly |
| Examples | Andon, kanban, shadow boards, floor marking, poka-yoke, gauge zones | Dashboards, scoreboards, trend charts, policy postings |
| Failure mode if misused | Ignored signal with no escalation defeats its purpose entirely | Becomes "wallpaper" — accurate but unacted-upon |
| Relationship to Standardized Work | Often embedded directly into the workstation and work sequence | Usually supports management review, less tied to the immediate task |

### Why the Distinction Matters in Practice

A facility that is visually "busy" — walls covered in charts, TVs cycling through KPIs — can still have very weak actual process control if none of it is engineered to trigger a required response. Conversely, a facility with relatively few visible artifacts but a working andon system, functioning kanban, and poka-yoke at critical steps may have much stronger real-time control despite looking visually sparse.

This has direct implications for where limited implementation effort should go:

- At the **point of work** (the individual workstation), visual *controls* generally deliver more value than visual *displays*, because the operator needs an immediate, unambiguous signal of correct/incorrect state, not a trend they'd have to interpret mid-cycle
- At the **management review level** (daily tier meetings, weekly leadership reviews), visual *displays* are appropriate and valuable, because the audience has time to interpret trends and decide on a response
- A common upgrade path is converting a passive display into an active control once a pattern is well understood: a defect-rate chart (display) that reveals a recurring failure mode can lead to installing a poka-yoke device (control) that prevents that specific failure from occurring at all

### Common Failure Modes

- **Mistaking volume of visual material for control**: assuming that because an area has many posted charts, it has strong visual management, when none of the charts are tied to a defined response
- **Andon without teeth**: installing an andon system but not actually stopping the line or dispatching a responder when it's pulled, converting what should be a control into a mere display (a light that turns on and is then ignored)
- **Displays that no one reviews**: a dashboard updated diligently but never actually referenced in any meeting or decision, consuming effort with no behavioral effect
- **Controls without clear escalation**: a kanban system with no defined response when a card sits unfulfilled past its expected cycle, degrading a control into an informal display
- **Over-relying on displays for safety-critical conditions**: posting a gauge reading as a number on a screen (display) instead of a color-zoned gauge or a hard interlock (control) for a condition where the required action should not depend on someone reading and correctly interpreting a number under time pressure
- **No feedback loop from display to control**: a persistent trend visible on a dashboard for months without ever prompting investment in an actual control (poka-yoke, andon trigger) that would prevent the recurring issue

### Illustration: Control Versus Display Response Path (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 900 420" font-family="Arial, sans-serif">
<text x="450" y="30" text-anchor="middle" font-size="20" font-weight="bold">Visual Control vs. Visual Display: Response Path (svg_diagram)</text>

<text x="220" y="65" text-anchor="middle" font-size="15" font-weight="bold" fill="`#1e40af`">Visual Control</text>

<rect x="60" y="85" width="320" height="50" rx="6" fill="`#dbeafe`" stroke="`#1e40af`" stroke-width="2" />

<text x="220" y="115" text-anchor="middle" font-size="12">Abnormal condition occurs</text>

<path d="M220 135 V165" stroke="#1e40af" stroke-width="2" marker-end="url(#arrowC)" />
<rect x="60" y="165" width="320" height="50" rx="6" fill="#dbeafe" stroke="#1e40af" stroke-width="2" />
<text x="220" y="195" text-anchor="middle" font-size="12">Engineered signal fires<br />(andon, gauge zone, poka-yoke)</text>
<path d="M220 215 V245" stroke="#1e40af" stroke-width="2" marker-end="url(#arrowC)" />
<rect x="60" y="245" width="320" height="50" rx="6" fill="#dbeafe" stroke="#1e40af" stroke-width="2" />
<text x="220" y="270" text-anchor="middle" font-size="12">Required response is built-in</text>
<text x="220" y="286" text-anchor="middle" font-size="11">(stop, replace, escalate automatically)</text>
<path d="M220 295 V325" stroke="#1e40af" stroke-width="2" marker-end="url(#arrowC)" />
<rect x="60" y="325" width="320" height="50" rx="6" fill="#dcfce7" stroke="#166534" stroke-width="2" />
<text x="220" y="350" text-anchor="middle" font-size="12" font-weight="bold">Condition corrected</text>
<text x="220" y="366" text-anchor="middle" font-size="11">response guaranteed by design</text>

<text x="680" y="65" text-anchor="middle" font-size="15" font-weight="bold" fill="`#92400e`">Visual Display</text>

<rect x="520" y="85" width="320" height="50" rx="6" fill="`#fde8d0`" stroke="`#92400e`" stroke-width="2" />

<text x="680" y="115" text-anchor="middle" font-size="12">Abnormal trend occurs</text>

<path d="M680 135 V165" stroke="#92400e" stroke-width="2" marker-end="url(#arrowD)" />
<rect x="520" y="165" width="320" height="50" rx="6" fill="#fde8d0" stroke="#92400e" stroke-width="2" />
<text x="680" y="195" text-anchor="middle" font-size="12">Data updates on dashboard/chart</text>
<path d="M680 215 V245" stroke="#92400e" stroke-width="2" marker-end="url(#arrowD)" />
<rect x="520" y="245" width="320" height="50" rx="6" fill="#fde8d0" stroke="#92400e" stroke-width="2" />
<text x="680" y="270" text-anchor="middle" font-size="12">Someone must notice</text>
<text x="680" y="286" text-anchor="middle" font-size="11">and choose to interpret it</text>
<path d="M680 295 V325" stroke="#92400e" stroke-width="2" marker-end="url(#arrowD)" stroke-dasharray="5,4" />
<rect x="520" y="325" width="320" height="50" rx="6" fill="#fef2f2" stroke="#b91c1c" stroke-width="2" />
<text x="680" y="350" text-anchor="middle" font-size="12" font-weight="bold">Response NOT guaranteed</text>
<text x="680" y="366" text-anchor="middle" font-size="11">depends on review cadence &amp; attention</text>
</svg>

### Example

**Visual display**: A monthly quality dashboard shows scrap rate by defect type for the past six months, reviewed at a leadership meeting. It reveals a recurring bracket-misalignment defect that has persisted at roughly the same rate for three months. The chart accurately informs everyone in the meeting, but by itself did nothing to prevent a single defective bracket — it depended entirely on someone in the meeting deciding to act on it.

**Visual control (built from the display's insight)**: Following that meeting, engineering designs a locating pin fixture that physically will not allow the bracket to be clamped in the misaligned orientation. Now the same failure mode is prevented at the point of work — no dashboard review, no monthly meeting, and no individual judgment call is required for the defect to stop occurring. The dashboard (display) surfaced the pattern; the fixture (control) eliminated the recurrence.

### Conclusion

Visual controls and visual displays both belong in a mature visual management system, but they serve different functions and should not be treated interchangeably. A visual control is engineered to make the correct action obvious and to trigger a defined response — often automatically or near-automatically — at the point of work; a visual display presents information for a viewer's own interpretation, with no built-in guarantee that seeing it produces action. The practical discipline is to place true controls (andon, kanban, poka-yoke, shadow boards, floor marking) where an immediate, unambiguous response is required at the workstation, and to use displays (dashboards, trend charts, scoreboards) where periodic review and management judgment are the appropriate response mechanism — and to recognize when a persistent pattern on a display is signaling that it's time to engineer a real control instead.

### Related Topics

- Andon systems and escalation design
- Kanban as a visual pull-control mechanism
- Poka-yoke (error-proofing) and physical prevention devices
- Shadow boards and point-of-use tool control
- 5S Set in Order and Standardize as visual-control foundations
- Tiered daily management meetings and dashboard review cadence
- Gemba walks and real-time abnormality detection
- OEE and defect-rate dashboard design
- Escalation matrices for unresolved visual signals
- Converting recurring display trends into engineered controls