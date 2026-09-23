## Target Profiling from Open-Source Information


---

### 1. Conceptual Foundation

A target profile is a structured, evidence-based document that aggregates information about a specific individual — their identity, behavior, associations, routines, vulnerabilities, and decision-making patterns — derived exclusively from information that is publicly accessible without covert access, technical intrusion, or human penetration.

The discipline is **Open-Source Intelligence (OSINT)**. In the intelligence cycle, OSINT-derived profiling serves multiple functions: it precedes and shapes collection from other disciplines, it provides the baseline against which anomalies are detected, and in many cases it is sufficient on its own to answer collection requirements without recourse to more invasive methods.

The ethical and legal status of OSINT profiling turns on a specific principle: **information that an individual has made accessible to the public, or that is accessible through public records, carries a reduced privacy expectation** relative to information obtained covertly. This principle is contested at its margins — aggregation of individually innocuous public data points can produce a profile whose invasiveness exceeds what any single data point would suggest. This is called the **aggregation problem** and is addressed in §10.

**Key Points**

- OSINT profiling uses no covert access; all sources are legally accessible
- The aggregation problem means that the ethical status of a completed profile is not simply the sum of the ethical status of its individual components
- Legal accessibility does not determine ethical permissibility; these are separate questions
- Jurisdictional variation in privacy law affects what constitutes public information in different countries [Unverified: specific legal frameworks vary and should be verified against current law in the relevant jurisdiction]

---

### 2. Profile Architecture

A complete target profile has a defined structure. Collection without structure produces data, not intelligence. The structure determines what is collected, what gaps remain, and how the profile is used.

#### 2.1 Standard Profile Components

**Identity Layer** Full name, aliases, nicknames, usernames, prior names (marriage, legal change), date and place of birth, nationality, citizenship, physical description, photographs, biometric indicators available from public sources.

**Locational Layer** Current residence, prior residences, workplace, frequently visited locations, travel history, routine movement patterns, home/work/recreation geography.

**Relational Layer** Family members (parents, siblings, spouse/partner, children), professional associates, social connections, organizational memberships, known adversaries or estranged relationships.

**Digital Layer** Online presence: social media accounts, forum participation, published content, domain registrations, email addresses, usernames across platforms, digital footprint history.

**Professional Layer** Employment history, professional credentials, published work, organizational roles, professional reputation, industry connections, financial relationships.

**Financial Layer** Property ownership, business registrations, court judgments, bankruptcy filings, disclosed income (public officials), shareholdings (disclosed), business interests.

**Behavioral Layer** Stated beliefs, public positions, patterns of decision-making visible in the record, responses to pressure, known preferences and aversions, habitual behaviors identifiable from the public record.

**Psychological Layer** [Inference: psychological assessment from public data is inferential, not confirmed; all outputs must be labeled accordingly] Communication style, emotional register in public statements, apparent values and motivations, stress responses visible in the public record, consistency or inconsistency between stated and demonstrated behavior.

**Vulnerability Layer** Contradictions between public claims and documented record, financial pressures, reputational exposures, relationships that create leverage, legal history, stated positions that conflict with private affiliations.

---

#### 2.2 The Intelligence Requirement

A profile is not produced in the abstract. It is produced to answer a specific **collection requirement** — a defined question or set of questions that the profile must address. The requirement determines:

- Which components of the profile are essential vs. peripheral
- What level of confidence is required for each data point
- When the profile is complete enough to be operationally useful

Without a defined requirement, profiling becomes collection for its own sake — producing data without analytical purpose and creating unnecessary privacy exposure without intelligence justification.

---

### 3. Source Categories

#### 3.1 Social Media

The richest single category of voluntary self-disclosure. Individuals routinely publish information across platforms that, in aggregate, constitutes a detailed behavioral and locational record.

**Platform-specific characteristics:**

|Platform|Primary Intelligence Value|
|---|---|
|Facebook|Real identity, social graph, life events, location history, family connections|
|LinkedIn|Professional history, organizational affiliations, education, professional network|
|X (Twitter)|Opinions, associations, behavioral patterns, real-time location indicators, communication style|
|Instagram|Visual location data (EXIF metadata where not stripped, background identification), routine patterns, social connections|
|TikTok|Behavioral indicators, social connections, location environment visible in video|
|YouTube|Published content, stated beliefs, organizational connections, comment behavior|
|Reddit|Pseudonymous but often linkable; detailed opinion and behavioral data; subreddit participation reveals interests and associations|
|GitHub|Technical capability, project affiliations, organizational connections, commit metadata|
|Strava / fitness apps|Precise location traces, routine patterns, home and workplace identification|

**Key Points**

- Social media data requires verification — accounts may be pseudonymous, inactive, or operated by someone other than the assumed subject
- Deleted content is frequently recoverable through archiving services (Wayback Machine, cached versions)
- Cross-platform correlation of usernames, profile images, and writing style can link pseudonymous accounts to real identity

---

#### 3.2 Public Records

Government-maintained records that are legally accessible to the public. The scope of public records varies significantly by jurisdiction.

**Categories:**

**Property records:** Real estate ownership, purchase history, assessed value, mortgage liens. In most U.S. jurisdictions, property records are publicly searchable at the county assessor or recorder level. Reveals home address, property holdings, financial indicators.

**Court records:** Civil litigation, criminal history (charges and dispositions), divorce proceedings, bankruptcy filings, restraining orders. PACER (U.S. federal courts) provides access to federal case records. State court systems vary. Court filings frequently contain home addresses, financial disclosures, and detailed personal information.

**Business registrations:** Secretary of State filings identify business owners, registered agents, and officers. Reveal business interests, organizational affiliations, and potentially home addresses (if used as registered address).

**Voter registration:** In many U.S. states, voter registration records including address, party affiliation, and voting history are publicly available or purchasable by political campaigns and researchers. Availability varies by state.

**Professional licenses:** Licensing boards for attorneys, physicians, real estate agents, contractors, and other regulated professions maintain public databases including license status, disciplinary history, and sometimes address.

**UCC filings:** Uniform Commercial Code financing statements reveal secured loans and business financial relationships.

**FAA aircraft registration:** Aircraft ownership is publicly searchable. Relevant for high-net-worth targets or targets associated with aviation.

**FCC license database:** Amateur radio, commercial radio, and other FCC-licensed operators are publicly searchable with address information.

**Campaign finance records:** Federal Election Commission (FEC) and state equivalents disclose political contributions including contributor name, employer, occupation, and address for contributions above threshold amounts.

**FOIA-released documents:** Previously released FOIA responses are often archived and searchable. The subject of a profile may appear in documents obtained by others.

---

#### 3.3 News and Media Archives

Published journalism, broadcast transcripts, and media archives provide:

- Historical record of public statements and actions
- Contextual information about professional and organizational associations
- Photographs with locational and temporal metadata
- Third-party characterizations and assessments of the subject

**Tools:** LexisNexis (subscription), ProQuest, Google News archive, local newspaper archives, broadcast transcript databases.

**Key Points**

- News sources contain errors; claims require cross-verification against primary sources
- Local news archives are frequently not indexed by major search engines; direct archive searches of local outlets may be required
- Photographs in news archives provide visual identity confirmation and may contain locational data

---

#### 3.4 Academic and Professional Publications

For targets in academic, scientific, policy, or professional contexts:

- Published papers (Google Scholar, JSTOR, ResearchGate, Academia.edu)
- Conference presentations and proceedings
- Institutional affiliations and grant funding (NIH Reporter, NSF Award Search, USASpending.gov)
- Peer review activity (Publons, Reviewer Credits where public)
- Thesis and dissertation databases (ProQuest Dissertations)

Publication metadata reveals institutional affiliation, collaborator networks, research interests, and funding sources. Acknowledgment sections in papers frequently reveal personal connections not otherwise documented.

---

#### 3.5 Domain and Web Infrastructure Records

**WHOIS records:** Historical domain registration data frequently includes registrant name, organization, email, and address. Privacy protection services now obscure most current registrations, but historical WHOIS data (available through services like DomainTools, ViewDNS) may predate privacy protection adoption.

**Certificate transparency logs:** TLS certificate records (crt.sh) reveal domains registered by an organization or individual, including subdomains that may not be publicly linked.

**Reverse IP and hosting records:** Identify other domains hosted on the same infrastructure — may reveal associated projects or identities.

**Shodan / Censys:** Internet-connected device search engines. Relevant for technically sophisticated targets who operate their own infrastructure.

---

#### 3.6 Data Aggregators and People-Search Services

Commercial services that aggregate public records into searchable databases:

- Spokeo, Whitepages, BeenVerified, Intelius, PeopleFinder
- These services compile property records, phone numbers, addresses, relatives, and associated individuals
- Data quality varies; verification against primary sources is required
- Some services require subscription; others provide basic results free

**Key Points**

- Aggregator data is frequently outdated or incorrect
- The value is in leads and correlation, not confirmed facts — every data point from an aggregator requires independent verification before inclusion in a profile

---

#### 3.7 Image and Video Analysis

**Reverse image search:** Google Images, TinEye, Yandex Images (the most capable for facial similarity). Reverse image search of a profile photograph may reveal other accounts, prior publications, or different name associations for the same individual.

**EXIF metadata:** Photographs taken on smartphones and cameras contain embedded metadata including GPS coordinates, timestamp, device model, and sometimes software version. EXIF data is often stripped by social media platforms before public display but may survive in directly shared images or older uploads.

**Background analysis:** Images published by the subject may contain identifiable location information in the background — street signs, distinctive architecture, vehicle license plates, business signage. This is sometimes called **geolocation from image background**.

**Video metadata and environment:** Published video may contain audio cues (ambient noise, language, accents), visual location indicators, and behavioral data not intended for disclosure.

---

#### 3.8 Leaked and Breached Data

Data from security breaches is publicly circulated and indexed by services including:

- **HaveIBeenPwned** — email address presence in known breaches (does not provide breach content)
- **Dehashed, Snusbase** — breach data search services (legal and ethical status varies by jurisdiction and use)
- **Pastebin and similar** — credential dumps and leaked documents are frequently posted

**Key Points**

- Use of breached data raises legal questions that vary by jurisdiction; this is not a settled area of law [Unverified: consult jurisdiction-specific legal sources]
- Breached data may be inaccurate, outdated, or fabricated; it requires verification
- The ethical status of using breach data in OSINT profiling is contested in the practitioner community

---

### 4. Collection Methodology

#### 4.1 Structured Collection Process

Collection without structure produces incomplete and unverifiable profiles. A defined process:

**Step 1 — Seed identification** The minimum initial data: full name, approximate location, one known affiliation (employer, school, organization). The seed is the starting point from which collection branches.

**Step 2 — Identity confirmation** Before collecting against a named individual, confirm that the subject of collection is the correct person with that name. Common names produce false matches; collection against the wrong individual wastes resources and may constitute an error with consequences.

Confirmation requires at minimum two independent data points that are consistent with known information about the correct subject.

**Step 3 — Systematic platform enumeration** Methodically search each source category. Do not rely on search engine results alone — they index a fraction of the accessible public record. Direct searches of platform-specific tools, court systems, property databases, and professional registries are required.

**Step 4 — Pivot on discovered identifiers** Each discovered data point is a potential pivot to new collection. An email address found in one source may appear in domain registrations, forum accounts, or breach data. A username used on one platform may be reused on others. A business address may link to additional registrations.

**Pivot categories:**

- Email address → domain registration, forum accounts, breach data, account recovery
- Phone number → carrier lookup, reverse directory, associated accounts
- Username → cross-platform search (Sherlock, Maigret, WhatsMyName)
- Profile photograph → reverse image search
- Address → property records, business registrations, associated individuals
- IP address (if available) → geolocation, associated domains, hosting records

**Step 5 — Verification and source attribution** Every data point in the completed profile must have a documented source. Unverified data points are labeled as such. Data points confirmed by multiple independent sources are rated higher confidence than single-source data.

**Step 6 — Gap analysis** What collection requirements remain unmet? What profile components are absent or low-confidence? Gap analysis drives additional collection or flags the limits of what OSINT can establish.

---

#### 4.2 Search Operator Techniques

Standard search engines support operators that significantly expand collection capability:

|Operator|Function|Example|
|---|---|---|
|`"exact phrase"`|Returns only results containing exact string|`"John Smith" "Mariano Marcos"`|
|`site:`|Restricts results to a specific domain|`site:linkedin.com "John Smith"`|
|`filetype:`|Returns specific file types|`filetype:pdf "John Smith"`|
|`inurl:`|Searches within URLs|`inurl:profile "johnsmith"`|
|`intitle:`|Searches within page titles|`intitle:"John Smith" resume`|
|`before:` / `after:`|Date range filtering|`"John Smith" after:2020-01-01`|
|`-term`|Excludes results containing term|`"John Smith" -basketball`|
|`OR`|Returns results with either term|`"John Smith" OR "J. Smith"`|
|`*`|Wildcard within phrase|`"John * Smith"`|

**Key Points**

- Google, Bing, and DuckDuckGo index different portions of the web; the same query on multiple engines produces different results
- Yandex frequently returns results not indexed by Western search engines, particularly for image search
- Search engine results are personalized; use private/incognito mode and consider searching from multiple locations or through anonymizing infrastructure to reduce personalization effects

---

#### 4.3 Username Enumeration Tools

**Sherlock** (command-line, open-source): Searches hundreds of platforms simultaneously for a given username. Returns URLs where the username is found.

**Maigret** (extended from Sherlock): Broader platform coverage; returns additional account metadata where available.

**WhatsMyName** (web-based): Community-maintained platform list; searches for username presence.

**Key Points**

- Username enumeration tools generate false positives; each result requires manual verification
- Platforms may return a positive result for any username query regardless of account existence; this is called a **false positive site** and reputable tools maintain lists of these
- Username reuse across platforms is common but not universal; a match requires verification before attribution

---

### 5. Behavioral and Psychological Profiling from Public Data

#### 5.1 Communication Style Analysis

Public writing — social media posts, published articles, forum comments, emails included in public records — provides a sample of communication behavior that can be analyzed for:

**Linguistic patterns:**

- Vocabulary complexity and register (educational background indicators)
- Syntactic preferences (sentence structure, punctuation habits)
- Characteristic phrases or expressions
- Language switching in multilingual subjects

**Stylometric attribution:** Sufficiently large samples of writing can be analyzed to identify an unknown author or to confirm that a pseudonymous account is operated by a known individual. Stylometric analysis tools include JGAAP (open-source) and commercial alternatives. [Inference: stylometric attribution has known error rates and should not be treated as definitive without corroborating evidence]

**Temporal patterns:**

- Times of day when posts are published (indicates timezone, sleep schedule, work patterns)
- Days of week with activity gaps (may indicate work schedule or religious practice)
- Activity spikes correlated with external events (reveals what events the subject monitors and responds to)

---

#### 5.2 Stated vs. Demonstrated Behavior

A profile that records only stated positions is less valuable than one that compares stated positions with demonstrated behavior across the record.

**Analytical targets:**

- Consistency between public statements at different times (has position changed? under what circumstances?)
- Consistency between stated values and documented actions (financial records, organizational affiliations, voting record where public)
- Responses to pressure or criticism visible in the public record
- Behavior during known stress periods (litigation, financial difficulty, public controversy)

**Key Points**

- Inconsistencies between stated and demonstrated behavior are analytically significant but require careful interpretation — they may reflect genuine hypocrisy, changed circumstances, context-specific behavior, or errors in the record
- All behavioral inferences must be labeled [Inference] and treated as hypotheses requiring additional evidence, not conclusions

---

#### 5.3 Network and Relational Analysis

The subject's connections — professional, social, familial, organizational — are as analytically valuable as direct information about the subject.

**Relational mapping:**

- First-degree connections: directly documented relationships
- Second-degree connections: relationships of the subject's known associates
- Organizational affiliations: membership in groups, boards, committees
- Event co-attendance: individuals who appear together in photographs, event records, or news coverage

**Network analysis questions:**

- Who influences the subject? (Whose positions does the subject echo, cite, or defer to?)
- Who does the subject influence?
- What relationships are undisclosed or downplayed?
- What does the network topology suggest about the subject's access, loyalties, and vulnerabilities?

**Tools:** Maltego (commercial, with free community edition) provides link analysis visualization. Manual mapping in a graph tool (yEd, Gephi) is also common.

---

#### 5.4 Routine and Pattern Analysis

Behavioral routines visible in the public record:

- **Location patterns:** Check-ins, tagged photographs, event attendance, transit card data (if publicly disclosed), fitness tracking (Strava public activities)
- **Temporal patterns:** When does the subject typically post, travel, attend events?
- **Habitual associations:** Who does the subject consistently appear with? At what locations?
- **Predictable events:** Scheduled appearances, recurring events, annual patterns

**Key Points**

- Routine analysis from public data is limited by what the subject chooses to disclose; sophisticated individuals leave fewer public traces
- Gaps in the public record are themselves data points — a subject who was publicly active and then went quiet warrants analytical attention
- Route and timing patterns derived from public data can, in combination with physical observation, support surveillance planning [Note: physical surveillance beyond public observation raises separate legal and ethical questions outside the scope of OSINT]

---

### 6. Geolocation from Public Sources

Determining physical location from publicly available information is a core OSINT profiling skill.

#### 6.1 Direct Location Disclosure

- Explicit address in public records (property, voter registration, professional license)
- Tagged location in social media posts
- Foursquare / Swarm check-ins (if public profile)
- Google Maps reviews or contributions with reviewer profile linked to subject identity
- Event RSVPs and attendance records

#### 6.2 Indirect Location Indicators

- **Image background analysis:** Identification of location from visible elements in published photographs. Technique involves identification of architectural styles, street furniture, signage, vegetation, and terrain. The Bellingcat open-source investigation community has published extensively on this technique.
- **Timezone inference:** Post timestamps, if in local time, constrain timezone. Combining multiple timestamps with content context narrows location.
- **IP geolocation:** If the subject has published their IP address (in forum metadata, email headers from personal servers), IP geolocation provides city-level location. [Inference: IP geolocation accuracy varies significantly; treat as approximate]
- **Language and cultural indicators:** Spelling conventions, cultural references, and slang may indicate national or regional origin

#### 6.3 Tools

- **Google Street View / Maps:** Ground-level visual confirmation of identified locations
- **Sentinel Hub / Google Earth:** Satellite imagery for location confirmation
- **SunCalc:** Sun position analysis to date and locate photographs by shadow direction
- **GeoGuessr techniques:** Pattern recognition of infrastructure, vegetation, and road markings to identify country or region

---

### 7. Financial Profile Construction

Financial information is frequently the most analytically significant component of a profile, as it reveals actual behavior independent of stated positions.

#### 7.1 Publicly Accessible Financial Information

**Property records:** Purchase price, outstanding liens, assessed value, transfer history. Available at county assessor and recorder offices in most U.S. jurisdictions.

**Business filings:** Annual reports, dissolved business records, officer and director information (SEC EDGAR for public companies; Secretary of State for private businesses).

**SEC disclosures:** For public company officers and directors: Form 4 (insider trading disclosures), DEF 14A (proxy statements with executive compensation), 13D/13G (significant shareholdings). Searchable via EDGAR.

**Campaign finance:** FEC database; state equivalents. Employment and occupation data in contribution records frequently corroborates or contradicts other profile data.

**Bankruptcy filings:** PACER (federal). Contain detailed financial disclosures including assets, liabilities, creditors, and income history.

**Judgment and lien records:** Court judgments and tax liens are public records in most jurisdictions. Available through county recorder or court systems.

**Government salary databases:** Many states publish salary databases for public employees. Ballotpedia, state comptroller websites, and similar resources compile this data.

**Grant and contract databases:** USASpending.gov, SAM.gov, NIH Reporter — identify individuals or entities receiving federal funding.

---

### 8. Profile Documentation and Management

#### 8.1 Source Documentation

Every data point must be documented with:

- Source (URL, database, document title)
- Date accessed (web sources change)
- Date of the underlying information (when was this information current?)
- Confidence level (based on source reliability and corroboration)

A data point in the profile without a documented source is not intelligence — it is an unverified claim.

#### 8.2 Confidence Rating System

A simple rating system for each data point:

|Rating|Meaning|
|---|---|
|Confirmed|Multiple independent sources; high reliability|
|Probable|Single reliable source or multiple lower-reliability sources|
|Possible|Single lower-reliability source; plausible but unverified|
|Speculative|Inferred from indirect evidence; not directly documented|

All speculative content must be labeled [Inference] or [Speculation] in the profile document.

#### 8.3 Version Control and Dating

Profiles degrade over time as circumstances change. Each profile should carry:

- Date of initial production
- Date of most recent update
- Data currency indicators (when each data point was last verified)

An undated profile with no currency indicators is operationally unreliable.

---

### 9. Tools Reference

|Tool|Function|Access|
|---|---|---|
|Maltego|Link analysis and visualization|Commercial (community free)|
|Sherlock|Username enumeration|Open-source (GitHub)|
|Maigret|Extended username enumeration|Open-source (GitHub)|
|SpiderFoot|Automated OSINT aggregation|Open-source / commercial|
|theHarvester|Email, subdomain, name harvesting|Open-source|
|Recon-ng|Modular OSINT framework|Open-source|
|OSINT Framework|Categorized tool directory|osintframework.com|
|IntelTechniques|Search tools by category|inteltechniques.com|
|Wayback Machine|Archived web content|web.archive.org|
|crt.sh|Certificate transparency logs|crt.sh|
|ViewDNS|Historical WHOIS, DNS tools|viewdns.info|
|Shodan|Internet-connected device search|shodan.io|
|HaveIBeenPwned|Breach presence check|haveibeenpwned.com|
|SunCalc|Sun position for photo dating|suncalc.org|
|Bellingcat toolkit|Compiled geolocation resources|bellingcat.com|

---

### 10. The Aggregation Problem

The aggregation problem is the central ethical issue specific to OSINT profiling. It states that the combination of individually innocuous public data points may produce a profile whose invasiveness exceeds what any individual data point would generate.

**Example:** A subject's name is public. Their employer is public. Their general neighborhood is public. Their physical description is visible in published photographs. Their daily departure time is inferable from public social media posts. Their routine transit route is identifiable from fitness app data they have set to public. No single one of these facts is sensitive; together they constitute a detailed pattern-of-life profile that could support physical surveillance, targeted harassment, or worse.

**Analytical implications:**

- The ethical question is not only "is each source public?" but "what does the aggregated profile enable?"
- A profile that enables physical harm, harassment, or coercion may be ethically impermissible regardless of the public status of its components
- This is why collection requirement and end-use matter: the same profile has different ethical status depending on its purpose and the actor producing it

**Legal status:** The aggregation problem is not currently resolved in most legal frameworks. Privacy torts, stalking statutes, and harassment law may apply to the use of aggregated information in certain circumstances, but the production of an aggregated profile from public sources is not clearly prohibited in most jurisdictions. [Unverified: jurisdiction-specific legal analysis is required; this is not legal advice]

---

### 11. Operational Security in Profiling Activity

Collection activity itself produces a digital footprint that may be detectable by a sophisticated subject or a service monitoring for reconnaissance behavior.

**Passive indicators of collection:**

- Profile views on LinkedIn (visible to the subject on standard accounts)
- Repeated searches of the same name on people-search services
- Multiple visits to the same social media profile
- Account creation on platforms solely to view restricted profiles

**Mitigation:**

- Use LinkedIn in private mode (disables view notification; also disables ability to see who views your profile)
- Access social media profiles through anonymizing infrastructure (Tor, VPN) to prevent IP-based correlation
- Use sock puppet accounts (cover accounts with no linkage to real identity) for platform access where registration is required
- Vary collection timing and approach to avoid generating a detectable pattern
- Use archiving services (Wayback Machine, archive.today) to capture content without direct access to the live page

**Key Points**

- A subject who detects reconnaissance activity may alter their digital behavior, delete accounts, or initiate counter-profiling
- Operational security in collection is therefore not only a personal security concern but a collection effectiveness concern
- The creation of false-identity accounts for collection purposes may violate platform terms of service and, in some jurisdictions, computer fraud statutes [Unverified: legal status varies; jurisdiction-specific analysis required]

---

### 12. Summary of Principles

|Principle|Operationalization|
|---|---|
|Requirement-driven collection|Profile components are determined by the intelligence requirement, not by what is available|
|Identity verification first|Confirm correct subject before collecting; common names produce false matches|
|Structured pivoting|Each discovered identifier is a potential pivot to new collection|
|Source documentation|Every data point carries a documented source and confidence rating|
|Verification over aggregation|Single-source data is a lead, not a confirmed fact|
|Gap analysis|Identify what the profile does not know, not only what it does|
|Aggregation awareness|Evaluate the profile as a whole for invasiveness, not only component by component|
|Collection OPSEC|Collection activity leaves traces; manage them to preserve both security and collection effectiveness|
|Behavioral inference labeling|All psychological and behavioral assessments are [Inference] until corroborated by documented behavior|
|Currency management|Profiles degrade; date all data and update on a defined schedule|

---

