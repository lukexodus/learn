## Bellingcat Methodology


---

### Overview

Bellingcat is an open-source intelligence (OSINT) investigative outlet founded by Eliot Higgins in 2014. It has produced verified investigations into the MH17 shootdown, chemical weapons use in Syria, the Salisbury poisoning, and numerous other high-profile events. Its methodology is documented, replicable, and explicitly designed to function without access to classified information.

Bellingcat's significance to this syllabus is twofold: it represents the most publicly documented and systematized application of OSINT methodology available, and many of its techniques are directly applicable to individual-level OSINT operations described in Phase 6.

The methodology is not proprietary. Bellingcat has published its techniques extensively, runs training programs, and maintains a public handbook. What follows draws on those public sources.

---

### Core Methodological Principles

#### Open-Source First

All evidence used must be publicly accessible and verifiable by any third party. This is both an ethical commitment and a structural discipline — it forces the investigator to build cases that do not depend on access, sources, or privileged information that cannot be scrutinized.

This principle has an important corollary: if a conclusion cannot be supported by open-source evidence alone, it is not stated as a conclusion. The evidentiary standard is explicit and enforced editorially.

#### Verification Before Publication

No claim is published without independent verification through multiple lines of evidence. Single-source claims, even from apparently reliable sources, are treated as unverified until corroborated.

#### Transparent Methodology

The investigative process is documented and published alongside conclusions. Readers can examine the reasoning chain, the evidence, and the tools used. This serves both accountability and replicability.

#### Collaborative and Distributed

Bellingcat investigations frequently involve distributed teams, public crowdsourcing of specific sub-tasks, and collaboration with journalists and researchers at other organizations. The methodology is designed to scale horizontally.

---

### The Core Investigative Toolkit

#### Geolocation

Geolocation is the process of determining the precise geographic location where a photo or video was taken, using visual evidence within the image itself.

**Method:**

1. Identify fixed landmarks within the image: buildings, terrain features, road markings, vegetation, signage, power line configurations, bridge structures
2. Cross-reference against satellite imagery (Google Earth, Bing Maps, Yandex Maps — the latter often has higher resolution for Russian and post-Soviet territory)
3. Match the spatial relationships between visible features to candidate locations
4. Confirm with shadow angle, sun position, and seasonal vegetation where applicable
5. Document the match with annotated side-by-side comparison

**Tools used:**

- Google Earth Pro (historical imagery is operationally valuable — allows matching to the date range of the image)
- Yandex Maps and Panorama (street-level imagery in regions with poor Google Street View coverage)
- Wikimapia (community-annotated satellite imagery)
- SunCalc / ShadowCalculator (for shadow-based geolocation confirmation)

**Key Points**

- Geolocation is often the first and most reliable verification step for conflict imagery because it does not depend on the provenance of the image — only its content.
- A single successfully geolocated image can refute a false narrative or confirm a location claim with high confidence, independent of who took or distributed the image.

#### Chronolocation

Chronolocation is the determination of when a photo or video was taken, using visual evidence such as:

- **Shadow length and angle** — combined with the geolocated position, sun position at a given date and time can be calculated and matched to observed shadows
- **Seasonal indicators** — vegetation state, snow cover, flood levels
- **Astronomical features** — moon phase and position, star positions (for night imagery)
- **Event-correlated features** — visible construction stages, known event timelines, dated signage

**Tools used:**

- SunCalc.org — calculates sun azimuth and elevation for any location and date/time
- Suncalc combined with Google Earth shadow simulation
- PhotoDNA and reverse image search for establishing first appearance of an image online

**Key Points**

- Chronolocation is frequently combined with geolocation to establish a specific spacetime coordinate for an image.
- [Inference] The combination of confirmed location and confirmed time can be sufficient to contradict official denial of an event, as demonstrated in Bellingcat's MH17 and Syria chemical weapons investigations.

#### Reverse Image Search and Image Provenance

Before any image is treated as depicting what it claims to depict, its provenance is established:

1. Reverse image search to identify the earliest known appearance of the image online
2. Identify all prior contexts in which the image has appeared
3. Determine whether the image has been previously published in a different context (recycled imagery is a common disinformation tactic)
4. Check for image manipulation indicators

**Tools:**

- Google Images reverse search
- TinEye — specialized reverse image search with historical indexing
- Yandex Images — often superior for Cyrillic-language content and Russian social media
- InVID / WeVerify — video verification toolkit, allows frame extraction and reverse search of video
- FotoForensics — JPEG error level analysis (ELA) to detect image manipulation [note: ELA has significant false positive rates and should not be used as sole evidence of manipulation — [Inference]]
- Forensically (29a.ch) — clone detection, noise analysis, metadata extraction

**EXIF Metadata:**

- Images sometimes retain embedded metadata including GPS coordinates, device model, timestamp, and software used
- Social media platforms strip EXIF on upload, so EXIF is only available from images obtained before platform processing
- When present, EXIF coordinates can directly geolocate an image

#### Social Media Archaeology

Social media platforms are primary evidence sources. Bellingcat methodology treats social media posts as primary documents subject to the same scrutiny as any other evidence.

**Techniques:**

**Caching and archiving:**

- Content is archived immediately upon discovery because social media posts are frequently deleted
- Tools: Wayback Machine (archive.org), archive.today, CachedView
- Screenshots are taken but treated as secondary to archived versions (screenshots are trivially fabricated)

**Account analysis:**

- Post history, follower network, account creation date, username history
- Cross-platform correlation (same username, photo, or phone number across platforms)
- Geographic metadata in posts (Twitter/X location data where enabled; Instagram geotags)

**Network analysis:**

- Who shares, reposts, or interacts with specific content
- Identifying clusters of coordinated behavior (inauthentic amplification networks)
- Tracing the origin and spread trajectory of a specific claim or image

**Russian-language and regional platform fluency:**

- VKontakte (VK) — Russian social network; historically less aggressive about content removal than Western platforms; significant source for conflict-related imagery from Ukraine and Syria
- Odnoklassniki — Russian social network, older demographic
- Telegram — used extensively in conflict zones; channels are often public and archivable

**Tools:**

- Maltego — network link analysis and visualization
- Social-Searcher — cross-platform social media monitoring
- Twint (archived) / Nitter — Twitter/X data collection without API restrictions [availability varies; platform changes have affected many such tools]

#### Satellite Imagery Analysis

Satellite imagery is used to:

- Confirm or refute claims about events at specific locations
- Document changes at a location over time (construction, destruction, movement of equipment, mass graves)
- Establish ground truth independent of any party's claims

**Commercial providers used by Bellingcat:**

- Planet Labs — high revisit rate (daily in some areas), medium resolution
- Maxar Technologies — high resolution (30cm), used for detailed analysis
- Airbus Defence and Space — European alternative
- Google Earth Pro — historical imagery archive, useful for timeline construction

**Analysis method:**

- Compare before/after imagery at a geolocated site
- Identify specific features: vehicle tracks, excavation, building damage, equipment signatures
- Cross-reference with other evidence streams (social media, witness accounts, official statements)

**Key Points**

- Commercial satellite imagery has become accessible enough that independent investigators can obtain and analyze it without government resources.
- [Inference] The availability of daily-revisit commercial satellite coverage has substantially reduced the ability of state actors to conduct large-scale physical operations (deployments, destruction, construction) without open-source documentation.

#### Flight and Vessel Tracking

Open-source flight and vessel tracking data is used to trace the movement of aircraft and ships relevant to investigations.

**Flight tracking:**

- ADS-B (Automatic Dependent Surveillance-Broadcast) — aircraft transponder signals captured by ground receivers and aggregated on public platforms
- FlightRadar24, FlightAware, ADS-B Exchange (the latter does not filter military or sensitive flights, which the others sometimes do)
- Historical flight data can establish routes, departure and arrival points, and timing
- [Note: military aircraft often operate with transponders off; ADS-B data is therefore more reliable for civilian and commercial aviation]

**Vessel tracking:**

- AIS (Automatic Identification System) — maritime equivalent of ADS-B
- MarineTraffic, VesselFinder
- Similar caveat: vessels can disable AIS; absence from tracking is not confirmation of absence from an area

**Application:**

- Bellingcat used flight tracking data extensively in the MH17 investigation to establish the trajectory of the Buk missile system transport
- Vessel tracking has been used in investigations of sanctions evasion and weapons transfers

#### Vehicle and Equipment Identification

Military equipment, vehicles, and weapons systems are identified from visual evidence using:

- **Markings and insignia** — unit markings, tactical symbols, flag elements
- **Physical characteristics** — dimensions, silhouette, specific features (antenna configurations, gun barrel profiles, hull geometry)
- **Reference databases** — Jane's Defence (subscription), Oryx (open-source conflict equipment tracking), manufacturer documentation
- **Community expertise** — Bellingcat and its community include individuals with specialist knowledge of specific weapons systems and military equipment

**Method:**

- Isolate identifying features from imagery
- Match against reference material
- Confirm with multiple independent identifying characteristics
- Document with annotated comparison images

#### Document and Insignia Analysis

Physical documents, identity documents, patches, and insignia visible in imagery are analyzed for:

- Authenticity indicators
- Unit or organizational identification
- Geographic or temporal placement

Russian military unit identification — a significant component of Bellingcat's work — relies on:

- Uniform patch identification (Russian military patches are catalogued in open-source databases)
- Vehicle plate analysis
- Cross-referencing with personnel social media posts (Russian soldiers have historically posted imagery that inadvertently identified their units and locations)

---

### The Verification Standard — Levels of Confidence

Bellingcat does not use a formally published confidence tier system in the same way intelligence agencies do, but its published investigations reflect a de facto standard:

|Level|Description|
|---|---|
|Confirmed|Multiple independent lines of evidence; geolocation and/or chronolocation verified; no credible counter-evidence|
|Highly likely|Strong convergent evidence; minor gaps that do not affect core conclusion|
|Likely|Preponderance of evidence; some uncertainty remains|
|Unconfirmed|Insufficient evidence for conclusion; reported as claim only|
|False|Evidence contradicts the claim; specific refutation documented|

Claims below "likely" are not stated as conclusions. The distinction between what the evidence shows and what the investigator infers is maintained explicitly.

---

### Investigation Architecture — The Chain of Evidence

A full Bellingcat investigation is not a collection of individual verified claims. It is a structured chain in which individual verified elements combine to support a higher-order conclusion.

**Structure:**

```
Individual verified evidence units
        ↓
Intermediate conclusions (each independently supported)
        ↓
Central investigative conclusion
        ↓
Documented methodology (published alongside conclusion)
```

**Example logic chain (MH17, simplified):**

1. Satellite imagery shows Buk missile system in specific Russian military convoy — verified by geolocation
2. Social media imagery geolocates the same convoy at multiple waypoints in Russia and eastern Ukraine — verified by geolocation and chronolocation
3. Launch site identified by crater analysis, witness accounts, and satellite imagery
4. Missile debris recovered at crash site identified as 9M38 series — consistent with Buk system
5. Buk unit identified as belonging to Russia's 53rd Anti-Aircraft Missile Brigade — verified by unit marking analysis and personnel social media
6. Conclusion: MH17 was shot down by a Buk missile system belonging to a specific Russian military unit

Each link in the chain is independently verifiable. The conclusion does not depend on any single piece of evidence.

---

### Counter-Disinformation Applications

Bellingcat methodology is applied not only to original investigation but to the analysis and refutation of disinformation.

#### False Flag and Fabricated Evidence Detection

- Reverse image search to identify recycled imagery
- Geolocation to contradict claimed locations
- Chronolocation to contradict claimed dates
- Metadata analysis to identify fabrication indicators
- Cross-referencing claimed events with satellite imagery of the site

#### Narrative Tracking

- Identifying the origin point of a false claim
- Mapping its spread and amplification network
- Identifying coordinated inauthentic behavior
- Documenting the timeline of narrative evolution (claims frequently change as they are refuted)

#### Source Credibility Assessment

- Account history analysis
- Cross-platform consistency
- Track record of prior claims
- Network associations (accounts that consistently amplify each other's false claims)

---

### Limitations and Methodological Constraints

These are documented or explicitly acknowledged by Bellingcat and the broader OSINT community:

**Coverage gaps:**

- Events in areas with no social media penetration, no satellite coverage, or active information suppression are significantly harder to investigate
- State actors with sophisticated information management can reduce the open-source footprint of operations

**Imagery manipulation:**

- Sophisticated deepfake and image manipulation technology increases the burden on verification
- ELA and standard forensic tools are increasingly insufficient against high-quality manipulation [Inference; the field is in active development]

**Platform degradation:**

- Social media platforms change their APIs, restrict data access, and alter content moderation policies in ways that reduce OSINT capability over time
- Tools built on platform APIs frequently become non-functional

**Legal and ethical constraints:**

- Some OSINT techniques raise legal questions in specific jurisdictions (scraping, data aggregation)
- Privacy considerations apply — Bellingcat has explicit editorial policies about publishing personal information of private individuals vs. public figures and combatants

**Confirmation bias:**

- Open-source investigators, like all investigators, are subject to confirmation bias
- The transparent methodology requirement is a partial structural mitigation, but it does not eliminate the risk

**Key Points**

- [Inference] Bellingcat methodology is most reliable when multiple independent evidence streams converge. It is weakest when relying on a limited number of evidence types in a single domain. This mirrors general intelligence analysis principles.
- The methodology does not require advanced technical skills for most techniques. The primary requirements are systematic patience, source fluency, and disciplined verification habits.

---

### Tools Reference — Consolidated

|Category|Tool|Notes|
|---|---|---|
|Satellite imagery|Google Earth Pro|Historical imagery; free|
|Satellite imagery|Sentinel Hub|ESA; free tier available|
|Satellite imagery|Planet Labs|Subscription; high revisit rate|
|Geolocation|SunCalc.org|Sun position by location/date/time|
|Reverse image|TinEye|Indexed historical appearances|
|Reverse image|Yandex Images|Strong for Russian-language content|
|Video verification|InVID / WeVerify|Frame extraction, reverse search|
|Image forensics|FotoForensics|ELA; use with caution|
|Image forensics|Forensically (29a.ch)|Multiple analysis tools|
|Flight tracking|ADS-B Exchange|Unfiltered; includes military|
|Vessel tracking|MarineTraffic|AIS data|
|Archiving|archive.today|Manual archiving of web pages|
|Archiving|Wayback Machine|Automated crawl archive|
|Network analysis|Maltego|Link analysis; community edition free|
|Social monitoring|Social-Searcher|Cross-platform|
|Maps|Yandex Panorama|Street-level; post-Soviet regions|
|Maps|Wikimapia|Community-annotated satellite|

---

### Application to Individual OSINT Practice

The Bellingcat methodology scales down to individual-level OSINT operations with minimal modification. The core discipline transfers directly:

- Apply the same verification standard to information about individuals or organizations as Bellingcat applies to conflict events
- Build evidence chains rather than relying on single-source conclusions
- Archive evidence immediately — content is deleted
- Maintain explicit separation between what is verified and what is inferred
- Document methodology as you work, not retrospectively

[Inference] The primary difference at the individual level is resource scope — satellite imagery subscriptions and large investigative teams are not typically available. The methodological principles, however, are platform-independent and resource-independent at their core.

---

**Conclusion**

Bellingcat methodology is a systematized, publicly documented OSINT discipline that demonstrates the investigative depth achievable without classified access. Its core components — geolocation, chronolocation, image verification, social media archaeology, and structured evidence chaining — are individually learnable skills that collectively constitute a rigorous investigative capability. The methodology's strength derives not from any single technique but from the convergence of multiple independent evidence streams, each verified to an explicit standard, assembled into a transparent and reproducible chain of reasoning.

---

