## Geolocating Images and Tracking Movements


Geolocating images and inferring movement patterns from visual and metadata evidence is a core OSINT discipline. It requires layered analysis — metadata extraction, environmental feature recognition, cross-referencing against open-source databases, and chronological reconstruction. The methodology is systematic, not intuitive. Errors compound when analysts skip verification steps or anchor prematurely on a single indicator.

---

### Foundational Principles

- **Convergence of evidence**: No single indicator gelocates an image reliably. Confidence increases as independent signals converge on the same location.
- **Metadata is not ground truth**: EXIF data can be spoofed, stripped, or inaccurate. Treat it as a lead, not a conclusion.
- **Environmental features are persistent but not permanent**: Buildings, terrain, and vegetation change. Temporal calibration matters.
- **Absence of data is data**: A stripped image with no metadata in a context where metadata is normally present is itself a signal.

---

### Layer 1 — Metadata Extraction

#### EXIF Data

Most images captured on smartphones and cameras embed EXIF (Exchangeable Image File Format) metadata unless explicitly stripped. Fields of operational interest:

- **GPS coordinates**: Latitude, longitude, and sometimes altitude. Directly locating if present.
- **Timestamp**: Date and time of capture. Device timezone may also be embedded.
- **Device make and model**: Narrows the population of potential sources.
- **Software version**: Camera app or OS version, which may correlate with geographic markets.
- **Orientation data**: Accelerometer-derived orientation of the device at capture.

**Extraction tools:**

- **ExifTool** (Phil Harvey — verified open-source): Command-line utility, reads metadata from images, video, and documents. `exiftool filename.jpg` returns all embedded fields.
- **Jeffrey's Exif Viewer** (web-based): Extracts and maps GPS coordinates directly.
- **Metadata2go**: Browser-based alternative.

**Key Points**

Major social media platforms (Twitter/X, Facebook, Instagram, LinkedIn) strip EXIF data on upload. Images sourced from these platforms will not contain GPS coordinates. Images shared via direct messaging apps, email, or file-sharing services [Inference] more frequently retain metadata. WhatsApp strips metadata. Telegram [Unverified] behavior varies by version and sharing method.

#### Video Metadata

Video files embed equivalent metadata in container formats (MP4, MOV). Additionally:

- **Subtitle and chapter tracks** may contain embedded location references.
- **GPS tracks** in GoPro and dashcam footage are frequently embedded in a dedicated metadata stream, not the standard EXIF container. **ExifTool** reads these.
- Frame-by-frame environmental analysis applies to video identically to still images.

---

### Layer 2 — Environmental Feature Analysis

When metadata is absent or untrustworthy, the image itself becomes the primary evidence source.

#### Terrain and Vegetation

- Terrain morphology (mountain profiles, coastline shapes, river bends, valley gradients) is stable over decades and cross-referenceable against topographic databases and satellite imagery.
- Vegetation type narrows geographic region: coniferous forest, tropical canopy, savanna, alpine meadow, desert scrub. Combined with terrain, this significantly reduces the search area.
- Soil color is geographically distinctive. Red laterite soils, pale limestone, dark volcanic earth, grey clay — each correlates with specific geological regions.
- Snow cover, seasonal vegetation state, and sun angle can constrain the time of year.

#### Architecture and Infrastructure

Architecture is one of the highest-yield environmental indicators.

- **Architectural style**: Colonial, Soviet-era, Ottoman, Southeast Asian vernacular, Scandinavian timber construction — each is regionally bounded.
- **Building materials**: Fired brick, adobe, corrugated iron, concrete block, timber framing — materials correlate with economic development level and regional availability.
- **Roof types**: Flat roofs dominate arid climates. Steep-pitched roofs dominate high-snowfall regions.
- **Window and door proportions**: Vary by era and regional building tradition.
- **Signage**: Even partially visible text, logos, or numerals narrows location. Script type (Latin, Cyrillic, Arabic, Devanagari, Han characters) eliminates large regions immediately.
- **Road markings and signage conventions**: Lane marking colors (white vs. yellow centerlines), sign shapes, pedestrian crossing patterns, and traffic light configurations vary by country and sometimes by region within countries.
- **Utility infrastructure**: Overhead power line configurations, transformer types, and pole materials differ by country. Street lighting fixture types are regionally distinctive.
- **License plates**: Plate color, shape, and character format are country-specific and sometimes region-specific within countries.

#### Urban Features

- **Street furniture**: Bus shelter designs, bollard types, bench styles, and waste bin designs are often municipally specific.
- **Manhole covers**: Cast iron covers frequently bear municipal or utility company markings that are directly geocoding.
- **Curb cuts and sidewalk materials**: Tactile paving patterns for the visually impaired vary by national standard.
- **Fire hydrant design**: Dramatically different between North America, Europe, and Asia. Color coding varies by municipality in the US.

---

### Layer 3 — Sun and Shadow Analysis

Solar position at a given location and time is deterministic and calculable. This enables both temporal and geographic inference.

#### Shadow Direction and Length

- Shadow direction indicates the compass bearing of the sun at the moment of capture.
- Shadow length relative to object height indicates solar elevation angle.
- Solar elevation angle at a specific bearing is a function of latitude, date, and time of day.

**Tools:**

- **SunCalc** (suncalc.org — verified): Plots sun position, azimuth, and elevation for any location and time. Allows reverse lookup — given a shadow bearing and length, constrain latitude and time-of-day combinations.
- **Photographer's Ephemeris**: Solar and lunar position calculator with map integration.
- **NOAA Solar Calculator** (verified): US government solar position calculator.

**Key Points**

Shadow analysis produces a set of possible (latitude, date, time) combinations, not a single answer. Combined with other indicators (vegetation, architecture), the intersection narrows the solution space.

#### Sky and Weather

- Cloud type and formation altitude vary with climate zone.
- Atmospheric haze and air quality characteristics differ by region and season.
- [Inference] These are lower-confidence indicators but contribute to convergence when combined with stronger signals.

---

### Layer 4 — Satellite and Map Cross-Reference

Once candidate features are identified, cross-reference against open-source satellite and map databases.

#### Primary Tools

- **Google Earth Pro** (verified, free desktop application): Historical satellite imagery with date slider. Allows comparison of current imagery against older captures. Measurement tools for shadow analysis.
- **Google Maps Street View**: Ground-level photographic coverage of road networks globally. Cross-reference specific environmental features visible in the target image.
- **Bing Maps**: Separate satellite imagery source. Different capture dates from Google — useful when Google imagery is outdated or obscured.
- **Yandex Maps**: Strong coverage of Russia, Central Asia, and Eastern Europe. Street-level imagery independently captured.
- **Mapillary**: Crowdsourced street-level imagery. Particularly useful in areas without Google Street View coverage. Open-source, searchable.
- **OpenStreetMap (OSM)**: Community-maintained map database. Contains infrastructure, building, and landmark data often absent from commercial maps. Overpass Turbo allows complex spatial queries against OSM data.
- **Sentinel Hub** (verified): European Space Agency satellite imagery browser. Multispectral imagery, recent captures, free tier available.
- **Planet Labs**: Commercial satellite imagery provider. High temporal resolution — some areas captured daily. [Unverified] Access is commercially gated; some academic and journalist access programs exist.

#### Reverse Image Search

- **Google Lens / Google Images**: Reverse image search identifies visually similar images indexed by Google. Useful for identifying landmarks, locations previously photographed, or images that have appeared elsewhere online.
- **TinEye**: Reverse image search focused on exact and near-duplicate matching.
- **Yandex Images**: Often outperforms Google for face matching and Eastern European content.
- **Bing Visual Search**: Independent index, occasionally surfaces results others miss.

---

### Layer 5 — Linguistic and Cultural Indicators

#### Text in Images

Even partially visible text is high-value.

- **Script identification**: Immediately eliminates regions. Arabic script, for example, narrows to MENA, parts of South and Southeast Asia, and diaspora communities.
- **Language identification**: Within a script, specific language features (character combinations, diacritics) narrow further.
- **Brand and product presence**: Regional product distribution. A specific beverage brand, cigarette brand, or retail chain visible in an image may only distribute in certain countries or regions.
- **Currency**: Visible banknotes or coins are directly geocoding.
- **Pricing**: Prices in visible contexts (menus, shop windows) constrain currency and economic context.

#### Cultural Markers

- Dress codes, religious symbols, and cultural practices in the image provide regional context.
- Vehicle makes and models vary by regional market. Right-hand vs. left-hand drive is country-specific.
- Military uniform, insignia, and equipment are frequently identifiable against open-source military reference databases.

---

### Layer 6 — Movement Pattern Reconstruction

Geolocating individual images is the foundation. Reconstructing movement requires sequencing and temporal analysis across multiple images or data points.

#### Chronological Sequencing

- EXIF timestamps sequence images where metadata is present.
- Where metadata is absent, internal image content provides chronological signals: lighting changes, shadow movement, weather progression, crowd composition changes.
- Video provides continuous temporal data with frame-rate precision.

#### Travel Time Constraints

Once two locations are identified with associated timestamps, travel time between them constrains the route and mode of transport.

- Walking speed: approximately 5 km/h.
- Cycling: 15–25 km/h.
- Urban driving: highly variable, typically 20–50 km/h average.
- Rail: varies dramatically by line type.
- Air: eliminates intermediate ground-level geolocation possibilities.

If Location A is identified at Time 1 and Location B at Time 2, the interval defines a maximum distance radius from each point. The intersection of those radii defines where the subject could plausibly have been during the interval.

#### Pattern of Life Analysis

Repeated geolocations across multiple days or events reveal:

- **Home base**: Most frequent origin point of morning activity.
- **Work location**: Sustained midday presence.
- **Routine nodes**: Recurring locations (gym, café, place of worship, transit hub).
- **Social network geography**: Locations co-occurring with specific individuals.
- **Anomalies**: Deviations from established pattern that may indicate operational significance.

[Inference] Pattern of life analysis requires sufficient data density. Sparse or irregular image sets produce low-confidence inferences. Over-interpreting sparse data is a primary analytical error in this domain.

---

### Layer 7 — Crowd-Sourced and Community Verification

#### Bellingcat Methodology

Bellingcat (verified open-source investigative outlet) has published and demonstrated geolocation methodology extensively. Their documented approach emphasizes:

- Multi-source convergence before any location claim.
- Public verification — publishing methodology so others can challenge or confirm.
- Explicit uncertainty quantification rather than false precision.

Their publicly available guides on geolocation are verified reference material.

#### GeoGuessr as Training

GeoGuessr (commercial game) presents random Street View imagery and requires location identification. [Inference] Sustained practice builds environmental feature recognition, regional visual vocabulary, and rapid hypothesis generation. It is not operationally equivalent to real geolocation work but develops the perceptual substrate.

#### Community Resources

- **Bellingcat Discord and online community**: Active geolocation community with ongoing collaborative verification.
- **Reddit r/whereisthis** and **r/whatsthislocation**: Crowd-sourced identification communities. Useful for understanding what environmental features are distinctive to non-specialist observers.

---

### Counter-Geolocation — Operational Awareness

Understanding the attack surface is necessary for both offensive (OSINT) and defensive (OPSEC) application.

#### Metadata Stripping

- **ExifTool**: `exiftool -all= filename.jpg` strips all metadata.
- **MAT2** (Metadata Anonymisation Toolkit 2 — verified open-source): Batch metadata removal across multiple file types.
- Verify stripping was successful before transmission. Re-check the output file.

#### Environmental Sanitization

- Photographs taken in or near operational locations should avoid distinctive background features: unique architecture, visible signage, utility infrastructure, terrain profiles.
- Reflective surfaces (windows, mirrors, glasses, phone screens) in images can reveal the photographer's location or identity.
- Window views in indoor photographs expose external terrain and urban features.

#### Temporal Sanitization

- Timestamp manipulation is trivial with ExifTool: `exiftool -DateTimeOriginal="2023:01:01 00:00:00" filename.jpg`
- Introduced false timestamps are detectable if they conflict with other internal evidence (shadow angle inconsistent with stated time, seasonal vegetation inconsistent with stated date).
- [Inference] A sophisticated analyst will check timestamp plausibility against environmental indicators rather than accepting EXIF timestamps at face value.

#### Behavioral

- Images shared online from a personal device retain device fingerprints even after metadata stripping in some platforms. [Unverified] Specific platform behavior varies and changes with software updates.
- Posting patterns (time of day, frequency, content type) constitute behavioral metadata independent of image content.
- Sequential image posting that allows movement reconstruction should be avoided if operational security requires location concealment.

---

### Analytical Error Modes

- **Premature closure**: Anchoring on the first plausible location identified and stopping verification. A image may contain features present in multiple locations; only convergence across independent indicators justifies confidence.
- **Confirmation bias in satellite cross-reference**: Searching satellite imagery for features that confirm a hypothesis rather than testing alternative hypotheses.
- **Temporal conflation**: Assuming an image was taken when it was posted rather than when it was captured. Significant delays between capture and posting are common.
- **Metadata trust**: Treating GPS coordinates in EXIF as ground truth without corroborating against environmental evidence.
- **Resolution overconfidence**: Satellite imagery resolution varies. Features that appear to match at low resolution may not match at ground level.

---

**Conclusion**

Image geolocation and movement reconstruction are systematic disciplines requiring layered evidence convergence. Metadata provides leads, not conclusions. Environmental feature analysis — terrain, architecture, vegetation, shadow, text, and cultural markers — constitutes the primary analytical substrate when metadata is absent or unreliable. Movement reconstruction requires temporal sequencing, travel time constraint analysis, and pattern of life inference across sufficient data density. The same methodology that enables offensive OSINT defines the counter-geolocation discipline: understanding what leaks, from where, and how it is analyzed is the prerequisite for suppressing it.****

---

