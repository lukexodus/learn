## Taylor's Principle of Gauge Design

### Statement of the Principle

Taylor's principle (formulated by W. Taylor, 1905) states that a limit gauge intended to check a dimension should be designed so that:

- The **GO gauge** should be designed to check the maximum-material condition of the feature and should check as many related dimensions (size and form) as possible simultaneously, in a single application — i.e., it should embody the full mating envelope of the feature.
- The **NO-GO gauge** should be designed to check the minimum-material condition of the feature and should check only one dimension at a time, at a single point of contact, avoiding any check of form.

This is often summarized as: **"GO gauge checks maximum material limit and form; NO-GO gauge checks minimum material limit and size only."**

### Rationale

- **Key Points**
  - The purpose of the GO gauge is to simulate the mating (assembly) condition of the part — since an actual mating component will engage the full length/circumference of the feature, the GO gauge must do the same to guarantee assemblability. A GO gauge that only checks a single point could pass a tapered, oval, or bent feature that would not actually assemble correctly.
  - The purpose of the NO-GO gauge is only to reject parts that are too large (hole) or too small (shaft) at any single point. If the NO-GO gauge were made to check full form as well, it could incorrectly reject a part that is within tolerance at most points but has a localized form error — which is not the function a NO-GO gauge is meant to serve; size violation at even one point is sufficient grounds for rejection, so a single-point contact is both necessary and sufficient.
  - Applying full-form checking on the GO side and point/single-axis checking on the NO-GO side together ensures that both size limits and functional (assembly) form requirements are verified using the minimum number of gauge elements.

### Application to Different Gauge Types

#### Plug Gauges (Holes)

- **GO plug**: made to the minimum hole diameter (maximum material limit for a hole is the smallest permissible hole), and constructed as a full-length cylindrical plug that engages the entire length of the hole in one insertion — checking diameter, straightness, and taper simultaneously.
- **NO-GO plug**: made to the maximum hole diameter (minimum material limit), constructed as a short plug or a stepped/reduced-diameter member behind the GO section, contacting the bore only over a short length so it checks diameter at effectively one cross-section without assessing straightness or taper along the bore.

#### Ring Gauges (Shafts)

- **GO ring**: made to the maximum shaft diameter (maximum material limit for a shaft), bored as a full ring that must pass over the entire length of the shaft, checking diameter and straightness/roundness along the engagement length.
- **NO-GO ring**: made to the minimum shaft diameter (minimum material limit); in strict Taylor's-principle practice this would also ideally check only a limited engagement, though in practice full rings are commonly used for both members and the size-only intent is achieved by the tight axial engagement typical of ring gauge use. [Inference — practical ring gauge design often diverges partially from strict Taylor form due to manufacturing convenience; the size-checking intent of the NO-GO member remains the governing design goal.]

#### Snap Gauges (Shafts, Open Frame)

- **GO anvils**: ideally spaced/shaped to check the shaft over as much of its circumference and length as practicable, though a snap gauge's open-jaw geometry inherently checks only two diametrically opposed points rather than the full circumference — a known practical departure from ideal full-form Taylor gauging.
- **NO-GO anvils**: narrow, point-contact anvils checking a single diametral measurement only.

### Illustrative Diagram: Taylor's Principle Applied to Plug and Ring Gauges

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 780 380">
<title>Taylor's Principle: Full-Form GO vs Point-Contact NO-GO Gauging (svg_diagram)</title>
\<style\>
text { font-family: Arial, sans-serif; font-size: 13px; fill: #1a1a1a; }
.label { font-size: 12px; }
\</style\>
<rect x="0" y="0" width="780" height="380" fill="#ffffff" />


<text x="40" y="30" font-size="15" font-weight="bold">Hole: GO Plug (Full Form)</text>

<rect x="60" y="50" width="120" height="180" fill="none" stroke="#333" stroke-width="2" />

<rect x="75" y="55" width="90" height="170" fill="`#cfe8ff`" stroke="`#2f6fab`" stroke-width="2" />

<text x="65" y="245" class="label">GO plug engages full length</text>

<text x="65" y="262" class="label">-&gt; checks diameter + straightness + taper</text>



<text x="260" y="30" font-size="15" font-weight="bold">Hole: NO-GO Plug (Point)</text>

<rect x="280" y="50" width="120" height="180" fill="none" stroke="#333" stroke-width="2" />

<rect x="315" y="55" width="30" height="40" fill="`#ffd9b3`" stroke="`#c46a1e`" stroke-width="2" />

<text x="285" y="245" class="label">NO-GO plug: short engagement</text>

<text x="285" y="262" class="label">-&gt; checks diameter only, one section</text>



<text x="500" y="30" font-size="15" font-weight="bold">Shaft: GO Ring (Full Form)</text>

<rect x="530" y="70" width="180" height="60" fill="`#cfe8ff`" stroke="`#2f6fab`" stroke-width="2" />

<rect x="500" y="50" width="230" height="14" fill="none" />

<rect x="500" y="70" width="230" height="60" fill="none" stroke="#333" stroke-width="2" />

<text x="505" y="150" class="label">GO ring slides over full shaft length</text>

<text x="505" y="167" class="label">-&gt; checks diameter + roundness</text>



<text x="500" y="210" font-size="15" font-weight="bold">Shaft: NO-GO Snap (Point)</text>

<line x1="500" y1="260" x2="560" y2="260" stroke="#333" stroke-width="4" />

<line x1="700" y1="260" x2="740" y2="260" stroke="#333" stroke-width="4" />

<line x1="560" y1="260" x2="560" y2="300" stroke="#333" stroke-width="4" />

<line x1="700" y1="260" x2="700" y2="300" stroke="#333" stroke-width="4" />

<line x1="560" y1="300" x2="600" y2="300" stroke="`#c46a1e`" stroke-width="4" />

<line x1="700" y1="300" x2="660" y2="300" stroke="`#c46a1e`" stroke-width="4" />

<text x="505" y="320" class="label">NO-GO anvils: single diametral contact</text>

<text x="505" y="337" class="label">-&gt; checks diameter at one point/axis only</text>

</svg>

### Consequences of Violating Taylor's Principle

- **Key Points**
  - If a GO gauge is made too short (point-contact only) instead of full-form, it may pass a hole that is barrel-shaped, tapered, or bell-mouthed — such a hole would fail to accept a full-length mating shaft in actual assembly, even though the GO gauge indicated acceptance.
  - If a NO-GO gauge is made full-form instead of point-contact, it may incorrectly reject a part with a localized minor waviness or a hole that is within tolerance everywhere except at one small region — an outcome that is overly conservative relative to the function the NO-GO gauge is meant to serve, and can unnecessarily inflate scrap/rework rates.
  - Both violations reduce the reliability of the GO/NO-GO decision relative to true functional (assembly) fit, which is the underlying purpose Taylor's principle protects.

### Practical Deviations from Taylor's Principle

- **Key Points**
  - **Progressive plug/snap gauges**: combine GO and NO-GO on the same gauge body for faster single-motion inspection; the NO-GO member is still short/point-contact, so the principle is largely preserved, only the arrangement (not the form-checking logic) differs from the classical double-ended layout.
  - **Segmental or "not-go" plug/ring gauges of reduced length**: sometimes used instead of full-length GO members for very long or very large bores/shafts due to manufacturing/cost/weight constraints, deliberately sacrificing full Taylor compliance on the GO side for practicality.
  - **Air (pneumatic) plug and ring gauges**: often check only a specific cross-section or a small number of axial positions rather than the full length in a strict mechanical-contact sense, representing another common departure driven by gauge design economics and part accessibility. [Inference — the acceptability of these deviations in a given application depends on the criticality of the feature's form and is typically governed by process capability data and applicable gauge design standards rather than by Taylor's principle alone.]
  - Standards bodies and gauge design texts generally treat Taylor's principle as the ideal reference case against which such practical deviations are evaluated and risk-justified, rather than as an absolute mandatory rule enforced in every gauge design.

### Relationship to Functional Gauging Philosophy

- Taylor's principle is the theoretical foundation of **functional gauging**: gauges are designed to simulate the actual mating/functional condition of a part rather than to perform a laboratory-style dimensional measurement.
- This differentiates limit gauging (attribute, accept/reject, function-simulating) from variable/comparator-based measurement (which yields an actual numeric deviation but does not inherently simulate assembly fit unless multiple points/axes are measured and analyzed).

### Summary Table

| Gauge member | Material condition checked | Form/length engagement | Primary intent |
| --- | --- | --- | --- |
| GO gauge | Maximum material limit (MML) | Full form/length (as much as practicable) | Simulate mating/assembly condition |
| NO-GO gauge | Minimum material limit (LML) | Single point/short engagement | Detect size violation only, no form check |

### Related Topics

- Plug, ring, and snap limit gauges (practical implementations of Taylor's principle)
- Maximum material condition (MMC) and least material condition (LMC) in geometric dimensioning
- Gauge tolerance and wear allowance standards (ISO 1938, BS 969)
- Functional gauging vs. dimensional (variable) measurement philosophies
- Progressive and segmental gauge design trade-offs
- Geometric form errors (straightness, roundness, taper) and their detection limitations in point-contact gauging
- Statistical justification for practical departures from strict Taylor compliance in high-volume gauge design