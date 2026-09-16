## Scientific Writing and Technical Reporting


### Overview

Scientific writing and technical reporting in geospatial and environmental science is the discipline of translating research design, data, methods, and findings into structured documents that meet the evidentiary and reproducibility standards of the scientific community, while remaining usable by secondary audiences such as policymakers, engineers, and the public. Unlike general technical writing, geospatial/environmental scientific writing carries domain-specific obligations: georeferenced data provenance, coordinate reference system (CRS) documentation, uncertainty quantification, and often regulatory or policy framing (e.g., environmental impact statements).

The discipline spans several document genres — peer-reviewed journal articles, technical reports, environmental impact assessments (EIAs), grant proposals, and data/metadata documentation — each with distinct structural conventions but shared underlying principles of clarity, precision, and reproducibility.

### Core Principles

#### The IMRaD Structure

Most scientific articles and many technical reports follow the IMRaD convention:

- **I**ntroduction — establishes the research problem, reviews relevant literature, and states the objective/hypothesis
- **M**ethods — describes data sources, instruments, spatial/temporal extent, processing workflows, and analytical techniques in sufficient detail for replication
- **R**esults — presents findings without interpretation, typically via tables, maps, and figures
- **a**nd
- **D**iscussion — interprets results in the context of the stated objective, addresses limitations, and situates findings within the broader literature

[Inference] IMRaD is the dominant structure in empirical environmental science journals, though purely methodological papers (e.g., introducing a new GIS algorithm) more often follow a Problem–Method–Evaluation structure instead.

#### Precision and Hedging Language

Scientific writing distinguishes between claims of varying certainty using calibrated hedging language:

| Certainty Level | Example Phrasing |
| --- | --- |
| High confidence (established fact) | "demonstrates," "confirms," "shows" |
| Moderate confidence (supported inference) | "suggests," "indicates," "is consistent with" |
| Low confidence (speculative) | "may," "could potentially," "it is plausible that" |

Overstating certainty (e.g., using "proves" for a single correlational study) is a common reviewer critique in environmental science manuscripts, where causal claims from observational spatial data are rarely fully justified without controlled experimental design or robust causal inference methods.

#### Reproducibility Requirements Specific to Geospatial Work

Geospatial methods sections carry reporting obligations beyond generic scientific method sections:

- **Coordinate Reference System (CRS)** — explicit statement of datum, projection, and EPSG code for all spatial data used and produced
- **Spatial and temporal resolution** — pixel size for raster data, sampling interval for time series, minimum mapping unit for vector data
- **Data provenance** — source, acquisition date, and version of all datasets (e.g., "Landsat 8 OLI, Collection 2 Level-2, acquired 2023-06-14, USGS EarthExplorer")
- **Software and algorithm versioning** — package versions, model parameters, and random seeds where stochastic methods are used, to support computational reproducibility

### Document Genres and Structural Conventions

#### Peer-Reviewed Journal Articles

Structured per IMRaD with journal-specific variations (e.g., *Remote Sensing of Environment* requires a Study Area section separate from Methods; many journals now mandate a Data Availability Statement).

#### Technical Reports (Agency/Consulting Context)

Typically structured as:

1. Executive Summary
2. Background/Objectives
3. Study Area and Data
4. Methodology
5. Findings/Results
6. Recommendations
7. Appendices (raw data, extended tables, metadata)

[Unverified] The inclusion and prominence of an Executive Summary as a standalone, non-technical section distinguishes agency/consulting technical reports from academic journal articles, though practice varies by organization and funding requirements.

#### Environmental Impact Assessments (EIAs/EISs)

Follow jurisdiction-specific regulatory templates (e.g., in the U.S., NEPA-mandated Environmental Impact Statements require Purpose and Need, Alternatives Analysis, Affected Environment, and Environmental Consequences sections). These documents must explicitly address cumulative impacts and often require GIS-based spatial overlay analysis to demonstrate impact extent.

#### Metadata and Data Documentation

Increasingly treated as a first-class deliverable rather than an appendix, following standards such as:

- **FGDC (Federal Geographic Data Committee)** Content Standard for Digital Geospatial Metadata
- **ISO 19115** — international standard for geographic information metadata
- **Dublin Core** — simpler, discipline-agnostic metadata schema, sometimes used for lightweight dataset description

### Practical Example: Structuring a Methods Section for a Remote Sensing Study

#### Weak Version (Insufficient for Reproducibility)

> We used satellite imagery to classify land cover and compared it to previous years to detect change.

This fails to specify sensor, resolution, classification algorithm, accuracy assessment method, or CRS — a reviewer would justifiably request major revisions.

#### Strengthened Version

> Land cover classification was performed using Sentinel-2 Level-2A surface reflectance imagery (10 m spatial resolution, bands 2–4 and 8) acquired for the 2019 and 2023 dry seasons (June–August) over the study area (EPSG:32651, UTM Zone 51N). A random forest classifier (`scikit-learn` v1.3.0, 500 trees, default hyperparameters) was trained on 450 ground-truth points collected via field survey (n = 150 per class: forest, agriculture, built-up) and validated using a 70/30 stratified train-test split. Classification accuracy was assessed using a confusion matrix, reporting overall accuracy and per-class user's/producer's accuracy. Land cover change between 2019 and 2023 was quantified via post-classification comparison, and a transition matrix was generated to characterize change trajectories.

**Key Points** illustrated by the revision: sensor and resolution stated, temporal window defined, CRS explicit, algorithm and software version specified, sample design and validation strategy described, and the analytical output (transition matrix) named — each addressing a specific reproducibility requirement.

### Reporting Uncertainty and Accuracy

#### Classification Accuracy Reporting

For thematic (categorical) map products, standard reporting includes a confusion matrix with:

$$\text{Overall Accuracy} = \frac{\sum_{i} n_{ii}}{n}$$

where $n_{ii}$ is the number of correctly classified samples for class $i$ and $n$ is total samples.

$$\text{Kappa Coefficient} = \frac{p_o - p_e}{1 - p_e}$$

where $p_o$ is observed agreement and $p_e$ is expected agreement by chance. [Inference] The Kappa coefficient has fallen out of favor in some remote sensing literature in recent years, with some methodologists arguing it is redundant with or inferior to reporting per-class user's and producer's accuracy directly, though it remains widely reported in practice and is still requested by many journal reviewers.

#### Uncertainty in Continuous (Regression) Outputs

For continuous predictions (e.g., biomass estimation, pollutant concentration modeling), standard metrics include:

$$RMSE = \sqrt{\frac{1}{n}\sum_{i=1}^{n}(y_i - \hat{y}_i)^2}$$



$$R^2 = 1 - \frac{\sum(y_i - \hat{y}_i)^2}{\sum(y_i - \bar{y})^2}$$

Reporting should include the validation strategy (e.g., k-fold cross-validation, spatial cross-validation to account for spatial autocorrelation) since naive random cross-validation on spatial data can overestimate model performance due to spatial dependence between training and test samples.

### Figure and Table Conventions

- **Figure captions** are self-contained: a reader should understand a map or chart's content, data source, and date from the caption alone, without needing to read the body text
- **Map elements required for publication-quality cartographic figures**: north arrow, scale bar, coordinate grid or graticule (where relevant), legend, data source/attribution, and projection statement
- **Table formatting**: numeric alignment (decimal-aligned), consistent significant figures, units stated in column headers rather than repeated in every cell
- **Referencing figures/tables in text** — every figure and table must be explicitly referenced and discussed in the body text; orphaned figures (included but never discussed) are a common revision request

### Citation and Data Attribution Practices

- **Dataset citation** — increasingly expected to follow the same rigor as literature citation, including DOI where available (e.g., via data repositories like Zenodo, PANGAEA, or agency-specific portals)
- **Software citation** — citing the specific software/package and version used for analysis (e.g., "QGIS Development Team, 2024, QGIS Geographic Information System, version 3.34")
- **Basemap/imagery attribution** — required by most providers' terms of use (e.g., "Imagery ©2024 Maxar Technologies" or "Contains modified Copernicus Sentinel data [2023]")

### Diagram: Technical Report Structure and Review Flow (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 900 380" font-family="sans-serif">
<text x="450" y="25" font-size="16" font-weight="bold" text-anchor="middle">Technical Report Development Flow (svg_diagram)</text>
<rect x="30" y="60" width="160" height="50" rx="6" fill="#e8f0fe" stroke="#4285f4" />
<text x="110" y="90" font-size="12" text-anchor="middle">Draft: Methods</text>
<rect x="230" y="60" width="160" height="50" rx="6" fill="#e8f0fe" stroke="#4285f4" />
<text x="310" y="90" font-size="12" text-anchor="middle">Draft: Results</text>
<rect x="430" y="60" width="160" height="50" rx="6" fill="#e8f0fe" stroke="#4285f4" />
<text x="510" y="90" font-size="12" text-anchor="middle">Draft: Discussion</text>
<rect x="630" y="60" width="200" height="50" rx="6" fill="#fef7e0" stroke="#fbbc04" />
<text x="730" y="90" font-size="12" text-anchor="middle">Internal QA / Co-author Review</text>
<line x1="190" y1="85" x2="230" y2="85" stroke="#555" stroke-width="2" marker-end="url(#a2)" />
<line x1="390" y1="85" x2="430" y2="85" stroke="#555" stroke-width="2" marker-end="url(#a2)" />
<line x1="590" y1="85" x2="630" y2="85" stroke="#555" stroke-width="2" marker-end="url(#a2)" />
<rect x="230" y="160" width="400" height="60" rx="6" fill="#e6f4ea" stroke="#34a853" />
<text x="430" y="185" font-size="12" text-anchor="middle">Reproducibility Check</text>
<text x="430" y="203" font-size="11" text-anchor="middle">CRS stated? Data provenance? Software versions? Sample design?</text>
<line x1="730" y1="110" x2="430" y2="160" stroke="#555" stroke-width="2" marker-end="url(#a2)" />
<rect x="230" y="260" width="400" height="60" rx="6" fill="#fce8e6" stroke="#ea4335" />
<text x="430" y="285" font-size="12" text-anchor="middle">Peer / Editorial Review</text>
<text x="430" y="303" font-size="11" text-anchor="middle">Accuracy metrics, hedging language, figure/table self-containment</text>
<line x1="430" y1="220" x2="430" y2="260" stroke="#555" stroke-width="2" marker-end="url(#a2)" />
<rect x="330" y="340" width="200" height="30" rx="6" fill="#f3e8fd" stroke="#a142f4" />
<text x="430" y="360" font-size="12" text-anchor="middle">Publication / Submission</text>
<line x1="430" y1="320" x2="430" y2="340" stroke="#555" stroke-width="2" marker-end="url(#a2)" />
</svg>

### Common Pitfalls

- **Vague methods language** — phrases like "high-resolution imagery" or "advanced classification techniques" without specifying resolution, sensor, or algorithm name
- **Missing CRS/projection information** — a frequent cause of desk rejection or major revision requests in geospatial journals, since it prevents replication of spatial analysis
- **Conflating correlation with causation** — especially common in environmental studies linking spatial patterns (e.g., land use and disease incidence) without controlling for confounding spatial variables
- **Inconsistent significant figures** — reporting coordinates or measurements with false precision (e.g., a GPS reading with 8 decimal degrees when device accuracy is ±5 m)
- **Passive voice overuse** — while passive voice is traditional in some methods sections ("samples were collected"), excessive passive voice throughout a manuscript reduces readability; many style guides (e.g., *Nature*, *Science*) now favor selective active voice for clarity

### Style Guides and Standards Reference

- **CSE (Council of Science Editors) Manual** — widely used in life and environmental sciences
- **APA 7th Edition** — common in interdisciplinary environmental/social science work
- **Journal-specific author guidelines** — always authoritative over general style guides when in conflict
- **Plain Language guidelines** (e.g., U.S. plainlanguage.gov) — increasingly required for public-facing environmental reports and EIAs to ensure accessibility to non-technical stakeholders

**Next Steps**

- Grant Proposal Writing and Budget Justification for Environmental Research
- Peer Review Process and Responding to Reviewer Comments
- Metadata Standards for Geospatial Data (FGDC, ISO 19115)
- Environmental Impact Assessment (EIA/EIS) Regulatory Frameworks
- Spatial Autocorrelation and Its Implications for Statistical Validity
- Data Repositories and DOI Assignment for Geospatial Datasets (Zenodo, PANGAEA)
- Accuracy Assessment Methods for Thematic Maps