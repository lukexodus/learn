## Writing and Presenting Urban and Regional Economics Research


### Position in the Research Workflow

This is the final translation step: converting a completed empirical study — with its research question, identification strategy, and (where applicable) policy evaluation — into a written and oral form that a skeptical academic or policy audience can evaluate. The preceding chapter items build the analytical content; this item concerns the discipline-specific conventions for presenting that content persuasively and transparently. Weak presentation frequently undermines methodologically sound work, and conversely, disciplined writing structure often forces the researcher to confront gaps in the empirical design (e.g., an unstated identifying assumption) that were not obvious during analysis.

**Key Points**

- Urban and regional economics writing sits at the intersection of applied microeconometrics and spatial/policy analysis, so papers are expected to satisfy both the identification rigor conventions of applied micro *and* the institutional/geographic context-setting conventions of urban and regional fields — omitting either is a common weakness in student and early-career work.

### Standard Paper Structure

#### The Canonical Applied Micro Paper Architecture

Most published empirical papers in this field (and capstone projects modeled on them) follow a recognizable structure, though section names and emphasis vary by outlet:

1. **Introduction**: states the research question, previews the identification strategy, previews the main result, and explicitly states the paper's contribution relative to existing literature — typically in the final paragraph or two of the introduction, not buried in a literature review.
2. **Institutional background / context**: describes the policy, program, or geographic setting in enough detail that a reader unfamiliar with the specific city, region, or program can evaluate the plausibility of the identifying assumption.
3. **Data**: describes sources, construction, sample restrictions, and summary statistics — should give the reader everything needed to assess external validity and data quality.
4. **Empirical strategy**: states the estimating equation, the identifying assumption in words, and how it will be tested (pre-trends, covariate balance, placebo checks) — this section should read as a direct continuation of the design decisions documented in the "designing an original empirical study" chapter item.
5. **Results**: presents the main estimates, typically moving from a baseline/naive specification to the preferred specification, with robustness and heterogeneity results following.
6. **Robustness and validity checks**: often a dedicated section (or subsection) addressing the falsification tests and alternative specifications pre-specified during design.
7. **Discussion / policy implications**: connects results back to the motivating question and, where relevant, to a cost-benefit or welfare interpretation (per the "policy evaluation and cost-benefit analysis" chapter item) — including honest discussion of external validity limits.
8. **Conclusion**: brief; restates contribution and, typically, directions for future research.

**Key Points**

- The introduction is disproportionately important in applied economics writing — many readers (and referees) decide whether to continue reading based on the introduction alone, so it should be able to stand on its own as a compressed version of the entire paper: question, method, result, and contribution.

#### The "Roadmap Paragraph" Convention

A short paragraph at the end of the introduction outlining the structure of the remaining sections ("Section 2 describes the institutional setting... Section 3 presents the empirical strategy...") is a strong convention in economics writing specifically, distinguishing it from narrative styles in other social sciences. [Inference] Some outlets and advisors consider this convention slightly dated or mechanical and prefer it be folded more organically into the introduction's final paragraphs; practice varies by field convention and specific venue, so this is worth confirming against the target outlet's recent publications rather than treated as a fixed rule.

### Writing the Empirical Strategy Section Persuasively

#### Stating the Identifying Assumption Explicitly

A frequent weakness in applied urban/regional papers (including student work) is presenting an estimating equation without ever stating, in prose, the assumption required for the coefficient of interest to have a causal interpretation. Reviewers and readers should not have to infer the identifying assumption from the equation alone — state it directly: "the key identifying assumption is that, absent the transit line opening, treated and control tracts would have followed parallel trends in property values."

#### Anticipating and Preempting Objections

Because most identification strategies in this field (per the causal-identification chapter item) rely on quasi-experimental rather than randomized variation, a persuasive empirical strategy section anticipates the specific threats a reader familiar with the literature will raise — reverse causality, spillovers into the control group, selection into treatment — and addresses each with either a design feature (donut buffer, placebo test) or an explicit limitation acknowledgment, rather than leaving the reader to discover the threat unaddressed.

### Presenting Results: Tables and Figures

#### Regression Table Conventions

- Report **coefficient, standard error (in parentheses), and significance stars**, with a note specifying the clustering level for standard errors — omitting the clustering level is a common and consequential omission given the discussion of correct clustering in the causal-identification chapter item.
- Present results as a **progression of specifications** (columns moving from bare bivariate relationship, to adding fixed effects, to adding controls, to the full preferred specification) so the reader can see how the estimate changes as confounds are progressively addressed — a stable coefficient across this progression is itself evidence for the design's credibility.
- Report the **number of observations and number of clusters** in every specification, since power depends on the number of independent clusters, not raw observation count (per the power-consideration discussion in the study-design chapter item).

#### Event-Study and Coefficient Plots

For DiD and staggered-adoption designs, an event-study figure — coefficients on period-specific treatment indicators plotted in event time with confidence intervals — is now close to a mandatory complement to the single-coefficient table result, since it is the primary visual evidence for (or against) the parallel-trends assumption.

**(svg_diagram) Event-Study Coefficient Plot Convention**

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 380" font-family="Helvetica, Arial, sans-serif">
<rect x="0" y="0" width="700" height="380" fill="#ffffff" />
<text x="350" y="24" text-anchor="middle" font-size="15" font-weight="bold" fill="#1a1a1a">Event-Study Plot: Coefficients by Event Time (svg_diagram)</text>
<line x1="60" y1="320" x2="640" y2="320" stroke="#333" stroke-width="1.5" />
<line x1="350" y1="60" x2="350" y2="340" stroke="#999" stroke-dasharray="4,3" />
<text x="356" y="55" font-size="11" fill="#666">treatment date</text>
<line x1="60" y1="200" x2="640" y2="200" stroke="#ccc" stroke-width="1" />
<text x="30" y="204" font-size="11" fill="#666">0</text>

<circle cx="110" cy="195" r="4" fill="#1f77b4" />
<line x1="110" y1="180" x2="110" y2="210" stroke="#1f77b4" />
<circle cx="180" cy="205" r="4" fill="#1f77b4" />
<line x1="180" y1="190" x2="180" y2="220" stroke="#1f77b4" />
<circle cx="250" cy="198" r="4" fill="#1f77b4" />
<line x1="250" y1="182" x2="250" y2="214" stroke="#1f77b4" />
<circle cx="320" cy="202" r="4" fill="#1f77b4" />
<line x1="320" y1="186" x2="320" y2="218" stroke="#1f77b4" />

<circle cx="390" cy="160" r="4" fill="#d62728" />
<line x1="390" y1="140" x2="390" y2="180" stroke="#d62728" />
<circle cx="460" cy="120" r="4" fill="#d62728" />
<line x1="460" y1="95" x2="460" y2="145" stroke="#d62728" />
<circle cx="530" cy="100" r="4" fill="#d62728" />
<line x1="530" y1="72" x2="530" y2="128" stroke="#d62728" />
<circle cx="600" cy="95" r="4" fill="#d62728" />
<line x1="600" y1="65" x2="600" y2="125" stroke="#d62728" />

<text x="130" y="340" font-size="11" fill="`#1f77b4`">Pre-period: flat near zero</text>

<text x="480" y="340" font-size="11" fill="`#d62728`">Post-period: effect emerges</text>

<text x="670" y="325" font-size="12" fill="#333">Event time</text>

</svg>

#### Spatial/Map Figures

Given the field's subject matter, maps are a standard and often expected visual element — choropleth maps of treatment intensity, spatial distribution of the outcome, or the geography of the identification strategy itself (e.g., a map showing treated vs. control boundary areas). A well-constructed map should include a clear legend, a scale/projection note where relevant, and should visually communicate the identification logic (e.g., shading treated and control zones distinctly around a boundary discontinuity) rather than serving as decorative context.

### Presenting Research Orally

#### Seminar and Conference Presentation Structure

Oral presentation structure differs from the written paper in pacing and emphasis:

- **Front-load the question and result**: unlike a written introduction that can spend a paragraph on literature positioning before the finding, an oral presentation typically states the question and headline result within the first few minutes, since audience attention and interruption patterns (particularly in traditional economics seminars, where interruptions during the talk are common) reward getting to the punchline early.
- **Spend disproportionate time on identification, not on results mechanics**: audiences in applied micro/urban economics seminars are typically more interested in probing the identifying assumption than in the point estimates themselves — anticipate and prepare for questions on the specific threats discussed in the empirical strategy writing section above.
- **Prepare backup slides**: for anticipated questions on alternative specifications, robustness checks, or data construction details that would clutter the main flow but that a prepared presenter should be able to produce immediately if asked.

#### Poster and Short-Format Presentation

For capstone poster sessions or short-format presentations, the structure compresses further: a single clear research question and result should be identifiable within a few seconds of viewing, typically requiring one dominant visual (an event-study plot, a map, or a simple bar/line chart of the headline result) rather than dense text or full regression tables.

### Writing Style Conventions Specific to Applied Economics

- **Active voice and direct claims about identification**: "we exploit variation in X to identify Y" rather than passive constructions that obscure what the researcher actually did.
- **Precision about causal vs. descriptive language**: reserving causal verbs ("increases," "causes," "reduces") for results the identification strategy actually supports, and using descriptive/associative language ("is associated with," "correlates with") for results that do not clear that bar — a distinction that referees in this field police closely.
- **Quantitative framing of magnitudes**: reporting effect sizes in economically interpretable units (percentage change, dollar terms, standard deviations of the outcome) rather than only reporting statistical significance, since a precisely estimated but economically negligible effect is a substantively different finding from a large, policy-relevant effect.
- **Explicit limitations paragraph**: rather than omitting or minimizing weaknesses, a dedicated paragraph (often in the discussion/conclusion) stating what the design cannot rule out is now a standard and expected component, not an admission of failure — reviewers view its absence as a red flag rather than its presence as a weakness.

### Common Pitfalls

- **Introduction that summarizes literature before stating the contribution**: burying the paper's own finding and contribution under an extended literature review delays the reader's ability to evaluate relevance.
- **Regression tables without clustering-level documentation**: a frequent and easily avoidable omission that undermines the reader's ability to assess inference validity.
- **Presenting only the preferred specification**: omitting the progression from naive to preferred specification removes evidence that would otherwise support the design's credibility.
- **Causal language unsupported by the design**: using "effect" or "causes" language when the underlying design only supports an associative claim, a common source of adverse referee reaction.
- **Oral presentations that spend too long on institutional background before reaching the result**: loses audience engagement in fields where norms favor early disclosure of the headline finding.
- **Omitting a limitations discussion**: an unstated assumption or threat to validity that the researcher clearly should have anticipated (e.g., failing to discuss spillovers into the control group, given how central this issue is in spatial applications) reads as a lack of awareness rather than the absence of a problem.

### Related Topics

- Literature review structure and positioning a paper's contribution against existing work
- Referee report response and revision strategy for applied economics journals
- Constructing effective regression tables (booktabs/LaTeX conventions common in economics)
- Event-study estimation and visualization in staggered adoption settings (deepened technical treatment)
- GIS mapping conventions and choropleth map construction for spatial economics figures
- Seminar presentation norms and handling interruption-heavy Q&A in economics seminars
- Preparing a capstone defense: anticipated identification questions and backup analysis
- Data and code replication packages: standards for applied economics journals