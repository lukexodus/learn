## Compartmented Digital Identities


---

### 1. The Core Problem

A digital identity is not a username. It is the total aggregated signal produced by a person's behavior across digital systems — device fingerprints, behavioral patterns, network signatures, linguistic style, timing rhythms, metadata, cross-platform linkages, and the accumulated inference drawn from all of these by both automated systems and human analysts.

The problem of compartmented digital identities is therefore not primarily a problem of creating fake accounts. It is the problem of **preventing the aggregation of signals across compartments** such that an analyst — human or automated — examining one compartment cannot establish linkage to another. Linkage is the failure mode. Everything else is in service of preventing it.

Two distinct threats drive the requirement:

- **Passive correlation**: automated systems that aggregate behavioral and technical signals across platforms and accounts, operated by platform companies, data brokers, and intelligence services
- **Active investigation**: a human analyst who suspects linkage and is deliberately attempting to confirm it

Defenses adequate against passive correlation are frequently inadequate against active investigation. The practitioner must know which threat they are designing against.

---

### 2. Identity Architecture

Before any technical implementation, the practitioner must design the architecture — the number of compartments, their purposes, their relationships to each other, and the permissible interactions between them.

#### 2.1 Compartment Design Principles

**Separation by purpose**: each compartment exists for a defined purpose. The purpose determines what the compartment needs to contain, what behaviors it must support, and what its exposure surface is. A compartment defined vaguely is a compartment that will expand beyond its intended scope.

**No shared infrastructure**: compartments that share any infrastructure element — device, network, account, email, phone number — are not genuinely separate. They are sub-folders. Shared infrastructure is the single most common linkage vector.

**No cross-compartment contact**: communications, files, links, and behavioral patterns must not cross compartment boundaries. A file created in one compartment and opened in another carries metadata. A link clicked in one browser and revisited in another creates a behavioral pattern. A writing style consistent across compartments is a fingerprint.

**Minimal compartments**: each additional compartment increases operational overhead and increases the surface area for error. The correct number of compartments is the minimum required for the operational requirement — not the maximum possible.

#### 2.2 Identity Layers

Each compartment contains multiple identity layers that must be internally consistent and mutually reinforcing:

|Layer|Components|
|---|---|
|Technical|Device, OS, browser fingerprint, network (IP/DNS), hardware identifiers|
|Account|Email, usernames, phone numbers, recovery contacts|
|Behavioral|Typing patterns, session timing, navigation habits, language use|
|Social|Profile content, interaction patterns, relationship network|
|Documentary|Payment methods, verification documents, address|
|Linguistic|Vocabulary, syntax, error patterns, topic focus|

Failure at any single layer can produce linkage. The weakest layer determines the overall compartment integrity.

---

### 3. Device Compartmentalization

#### 3.1 Physical Separation

The most robust compartmentalization uses **separate physical devices** for each compartment. This is non-negotiable for high-integrity requirements. A single device running multiple browsers, virtual machines, or user accounts is not compartmentalized — it is convenience with an illusion of separation.

Reasons physical separation is required:

- Hardware identifiers (MAC address, device serial number, hardware fingerprints) are accessible to sufficiently privileged software and cannot be reliably spoofed at the software level
- Cross-compartment timing correlation is possible if both identities operate on the same device — login times, session durations, and behavioral patterns can be correlated by a platform observing both accounts
- Operating system artifacts (temp files, logs, cached data) do not respect application-level compartments
- A single device compromise exposes all compartments simultaneously

**Minimum viable implementation**: a dedicated device per operational compartment, purchased without linkage to any existing identity (cash purchase, no loyalty card, no delivery to a linked address), with factory reset before first use.

#### 3.2 Device Acquisition

The device itself must not be linked to the practitioner's anchor identity or any other compartment:

- Cash purchase from a physical retailer
- No account login at point of sale (no loyalty program, no store app)
- No activation using existing Apple ID, Google account, or Microsoft account
- SIM card (if applicable) acquired separately and independently

[Inference] In jurisdictions requiring ID for SIM purchase, prepaid SIMs purchased in cash in jurisdictions without this requirement, or eSIM providers operating outside the practitioner's home jurisdiction, reduce this linkage vector — though both carry their own limitations.

#### 3.3 Operating System Selection

|Option|Compartment Integrity|Operational Ease|Notes|
|---|---|---|---|
|Standard Windows/macOS|Low|High|Extensive telemetry; account integration by design|
|Hardened Linux (Debian, Fedora)|Medium-High|Medium|Reduced telemetry; requires configuration|
|Tails OS (amnesic)|Very High|Low|No persistent state; strong for single sessions|
|Qubes OS|High|Low|Compartmentalization at OS level; steep learning curve|
|GrapheneOS (mobile)|High|Medium|Android hardening; eliminates Google Play Services dependency|

For most operational requirements, a dedicated Linux device with hardened configuration provides an adequate balance. Tails is appropriate for the highest-sensitivity single sessions where no persistence is required.

---

### 4. Network Compartmentalization

#### 4.1 The IP Address as Identity

An IP address is not merely a routing identifier — it is a persistent behavioral anchor. Platforms correlate accounts that share IP addresses across sessions. A single shared IP address across two ostensibly separate identities is frequently sufficient for automated linkage.

Network compartmentalization requires that each compartment operate from a distinct, non-linkable IP address **consistently** — not only when the practitioner remembers to activate a tool, but by design, so that unprotected access is structurally impossible.

#### 4.2 VPN

A commercial VPN replaces the practitioner's ISP-assigned IP with a VPN provider IP. This provides:

- Concealment of origin IP from destination platforms
- Concealment of traffic content from ISP

Limitations:

- The VPN provider itself sees origin IP and traffic — the trust is transferred, not eliminated
- Many commercial VPN exit IPs are known to platforms and treated as elevated-risk
- VPN connection/disconnection events are logged by some platforms
- If the same VPN server is used across compartments, the shared exit IP is a linkage vector

**Compartment-specific VPN usage**: each compartment should use a distinct VPN provider, or at minimum, a dedicated VPN account on a provider that does not log usage, paid for without linkage to the practitioner's anchor identity.

#### 4.3 Tor

Tor routes traffic through three volunteer-operated relays, encrypting between each, and exits from a relay not operated by the practitioner. This provides:

- Exit IP that is not associated with the practitioner
- No single relay sees both origin and destination
- Free at point of use

Limitations:

- Exit nodes are publicly listed and are blocked or flagged by many platforms
- Tor traffic is detectable at the network level (though not its content) — using Tor is itself a signal
- Timing correlation attacks are possible for a sufficiently resourced adversary who can observe both ends of the circuit
- Session speed is significantly reduced

[Inference] For compartments requiring account creation and sustained social interaction on mainstream platforms, Tor's exit node reputation creates significant friction. It is most appropriate for one-time or low-frequency high-sensitivity access where platform friction is acceptable.

#### 4.4 The Layered Approach

For high-integrity compartments: **VPN over Tor** or **Tor over VPN** — the distinction matters:

- **Tor over VPN**: traffic goes VPN → Tor → destination. ISP sees VPN, not Tor. VPN provider sees Tor traffic but not destination. Exit node sees destination but not origin.
- **VPN over Tor**: traffic goes Tor → VPN → destination. Tor sees VPN traffic, not destination. VPN provider sees destination and Tor exit IP.

Each has distinct trust and threat models. The correct choice depends on which party in the chain is the primary adversary.

#### 4.5 Network-Level Compartmentalization

Beyond IP address: DNS queries, WebRTC leaks, and IPv6 addressing are all independent linkage vectors that bypass VPN protection if not specifically addressed:

- Use a DNS provider that does not log, configured explicitly rather than defaulting to ISP or VPN provider DNS
- Disable WebRTC in browser configuration (it can expose local IP regardless of VPN)
- Disable IPv6 if the VPN does not provide full IPv6 protection
- Use a firewall rule that prevents any traffic from the compartment device that does not route through the designated network tool — this prevents accidental unprotected access

---

### 5. Account Architecture

#### 5.1 Email

Email is the root identity for most platform accounts. The email address used for account creation is:

- A linkage vector if the same address or provider is used across compartments
- A recovery pathway that, if linked to a real identity, exposes the account
- A metadata source (IP at registration, device fingerprint, timing) that platforms log and retain

**Compartment-specific email requirements:**

- Separate email address per compartment, ideally separate provider
- Providers with minimal logging and no identity verification: ProtonMail (with appropriate access method — not from anchor IP), Tutanota, temporary address services for low-stakes registrations
- Registration of the email account must itself occur from within the compartment's network environment — registering a compartment email from the anchor IP links them immediately

#### 5.2 Phone Numbers

Most major platforms require phone number verification. Phone numbers are among the highest-value linkage vectors:

- Carrier records associate numbers with real-world identities (in most jurisdictions)
- Platforms share phone number data across their ecosystems — a number used to verify a Facebook account is associated with that number in Meta's systems, which affects Instagram, WhatsApp, and any platform using Meta's social graph
- Number reuse across compartments creates direct linkage

**Options:**

|Method|Linkage Risk|Availability|Notes|
|---|---|---|---|
|Prepaid physical SIM (cash, no ID)|Low-Medium|Jurisdiction-dependent|ID requirements vary; roaming SIMs from permissive jurisdictions|
|VoIP number (VOIP.ms, etc.)|Medium|High|Provider has records; payment must not link to anchor|
|SMS verification services|Low|High|Single-use; many are blocked by major platforms|
|eSIM from privacy-focused provider|Medium|Medium|Provider still has records|

[Inference] Platforms increasingly flag VoIP numbers and SMS verification service numbers at registration, prompting additional verification or rejecting them entirely. This creates an arms race in which the practitioner must find numbers that pass platform verification without linking to the anchor identity.

#### 5.3 Payment Methods

Payment is a high-value linkage vector. A payment method linked to a real identity that is used for any compartment account links that account directly to the anchor:

- Credit and debit cards carry name and billing address
- PayPal and similar services have real identity verification
- Cryptocurrency is not anonymous by default — transaction graphs are public and traceable; chain analysis is a developed discipline

**Options for unlinked payment:**

- Cash-purchased prepaid debit cards (where available without identity verification)
- Privacy.com virtual cards (US only; linked to anchor bank account — provides merchant-level privacy only, not identity privacy)
- Monero (XMR): the most practical privacy-preserving cryptocurrency for this purpose — ring signatures, stealth addresses, and confidential transactions significantly complicate chain analysis [Inference: not untraceable under all conditions, particularly if acquired through a KYC exchange]
- Bitcoin with careful coinjoin: reduces but does not eliminate traceability

---

### 6. Browser and Application Fingerprinting

#### 6.1 The Browser Fingerprint Problem

Even with a distinct IP address, browsers transmit a detailed fingerprint composed of:

- User agent string (browser version, OS)
- Screen resolution and color depth
- Installed fonts
- Browser plugins and extensions
- Canvas fingerprint (unique rendering signature)
- WebGL fingerprint
- Audio context fingerprint
- Time zone and language settings
- Hardware concurrency (CPU core count)
- Battery status (mobile)

These signals, individually common, combine to produce fingerprints that are frequently unique or near-unique. A platform observing a consistent fingerprint across sessions can link them regardless of IP address changes.

#### 6.2 Fingerprint Management

**Tor Browser**: the designed approach is **uniformity** — make all Tor Browser instances look identical, so no individual user can be singled out. This works within the Tor ecosystem; it does not work if the practitioner uses Tor Browser with platform features that require account login and behavioral correlation.

**Firefox with hardening**: `arkenfox/user.js` configuration provides substantial fingerprint reduction. Not as uniform as Tor Browser but more operationally flexible.

**Mullvad Browser**: designed by the Tor Project for non-Tor use; applies fingerprint uniformity without requiring Tor routing.

**Brave**: built-in fingerprint randomization; better than stock Chromium but not equivalent to Tor Browser.

**Chromium-based browsers**: Google maintains significant data collection infrastructure in Chromium's code; hardening is possible but requires more effort than Firefox-based alternatives.

**The key principle**: within a compartment, use a consistent browser configuration. Across compartments, use distinct configurations (or the same maximally uniform configuration accessed from distinct network environments on distinct devices).

#### 6.3 Extensions as Fingerprint Vectors

Browser extensions are themselves fingerprint components. Two browsers with identical base configurations but different extension sets are distinguishable. Within a compartment, minimize extensions to those strictly necessary. Do not use the same non-standard extension set across compartments.

---

### 7. Behavioral Fingerprinting

Technical measures address technical linkage vectors. Behavioral fingerprinting addresses the practitioner themselves — the consistent patterns in how they interact with systems that persist regardless of technical configuration.

#### 7.1 Typing Patterns (Keystroke Dynamics)

Typing rhythm — the timing between keystrokes, dwell time on individual keys, error and correction patterns — is individually distinctive and measurable passively through browser JavaScript. This is an active area of development in fraud detection and account security.

[Inference] Mainstream platforms are not currently deploying keystroke dynamics at scale for identity correlation, but the capability exists and is used in specific high-security contexts. For most operational requirements, this is a secondary concern; for high-adversary contexts, it is a genuine vector.

Mitigation: deliberate alteration of typing pace within compartments; use of different input methods across compartments.

#### 7.2 Session Timing

The times at which a compartment account is active are a behavioral fingerprint. If two compartments are consistently active during the same hours, consistently inactive during the same hours, and their patterns correlate over weeks, a passive correlation analysis will identify them as likely the same person.

This is among the most underappreciated linkage vectors. It requires no technical access — it requires only observation of login timestamps, which are available to the platform and, in many cases, to other users.

**Mitigation**: establish distinct activity windows for distinct compartments, with genuine separation. Where operationally possible, use scheduled or automated posting to distribute activity across times that would not be natural for a single individual.

#### 7.3 Linguistic Fingerprinting (Stylometry)

Writing style is one of the most persistent and robust behavioral fingerprints. Stylometric analysis can identify authorship with significant accuracy from:

- Vocabulary richness and range
- Function word frequency (the, a, and, but — these are highly consistent within individuals)
- Sentence length distribution
- Punctuation habits
- Paragraph structure
- Error types and correction patterns
- Topic associations and reference patterns
- Idiosyncratic phrases or constructions

Stylometry is robust enough that it has been used in academic, legal, and intelligence contexts to attribute authorship where other identifying information was absent.

**Mitigation options:**

- **Register shift**: writing in a substantially different register across compartments (formal vs. casual, technical vs. general) — this reduces but does not eliminate stylometric signal
- **Language shift**: operating different compartments in different languages — highly effective but operationally constraining
- **AI-assisted rewriting**: passing text through a language model for stylistic transformation before posting — reduces stylometric distinctiveness but introduces the language model's own stylistic signature [Inference: effectiveness depends on the model and the analysis methodology]
- **Minimal writing**: compartments designed to produce minimal original text reduce stylometric exposure surface
- **Deliberate style adoption**: explicitly modeling writing style on a specific external source, adopted consistently within the compartment — labor-intensive and imperfect

No mitigation fully eliminates stylometric signal across extended text production. The practitioner who writes at length within multiple compartments accepts some residual stylometric linkage risk.

#### 7.4 Topic and Interest Fingerprinting

What a person searches for, reads, links to, and engages with constitutes a content fingerprint. Two accounts with identical interest profiles — even with no shared follows, no shared contacts, and no technical linkage — can be correlated by content behavior analysis.

**Mitigation**: each compartment should have a defined and plausible interest profile that is genuinely distinct from others. The interests do not need to be exhaustive, but they should be internally consistent and should not mirror the anchor identity's actual interest pattern.

---

### 8. Social Graph Isolation

#### 8.1 The Social Graph as Linkage Vector

Social connections are among the most powerful identity correlators available to platform analytics. Two accounts that:

- Follow the same unusual combination of accounts
- Are followed by the same unusual combination of accounts
- Interact with the same content at similar times
- Join the same niche communities

...are flagged as likely the same person by social graph analysis, regardless of all other technical measures.

**Mitigation:**

- Compartment social graphs must be genuinely distinct — not the anchor identity's network accessed under a different name, but a different network with different composition
- Seed follows should be plausible for the compartment persona, not simply the anchor's network minus identifying accounts
- Avoid simultaneous interaction with the same content across compartments

#### 8.2 Contact Importation

Many platforms prompt users to import phone contacts, email contacts, or connect social accounts to "find people you know." This feature, if used in any compartment, creates linkage between that compartment and every contact in the imported list — including contacts that exist only in the anchor identity.

**This feature must never be used in any compartment under any circumstances.**

#### 8.3 Device Contact Lists

Platforms with mobile applications frequently request access to the device contact list as part of their permission model. If a compartment device contains any contact information linked to the anchor identity or other compartments, and the platform is granted contact access, linkage is created.

Compartment devices should contain no contact information outside the compartment.

---

### 9. Metadata and File Hygiene

#### 9.1 Document Metadata

Files created in standard applications carry embedded metadata: author name, organization, software version, creation timestamp, edit history, and sometimes geolocation. A document created under the anchor identity's software license and shared within a compartment carries the anchor identity in its metadata.

**Mitigation:**

- Use compartment-specific software installations, not shared across compartments
- Strip metadata before sharing files across compartment boundaries or externally (ExifTool, MAT2)
- Prefer plain text formats (Markdown, plain .txt) which carry minimal metadata

#### 9.2 Image Metadata

Images captured by camera or smartphone embed EXIF data: device model, GPS coordinates, timestamp, lens parameters. An image shared within a compartment that contains GPS data links the compartment to a physical location. An image whose device model matches the anchor identity's known device creates a technical fingerprint.

**Mitigation:**

- Strip EXIF data from all images before use within compartments (ExifTool)
- Prefer images obtained from external sources (with appropriate licensing and no linking metadata) over images produced on personal devices
- Compartment devices used for photography should not be associated with the anchor identity

#### 9.3 PDF and Office Document Metadata

PDFs retain creation software, author, and modification history. Office documents retain more: edit time, number of revisions, named authors, template sources. These must be stripped or compartment-specific tools must be used for all document creation.

---

### 10. Operational Security Practices

#### 10.1 The Strict Separation Rule

The single most important operational practice: **never access a compartment from within the anchor identity's environment, and never access the anchor identity from within a compartment's environment.**

This means:

- No compartment account accessed on the anchor device, even once, even briefly
- No anchor account accessed on a compartment device
- No compartment activity conducted from the anchor network location without the full network stack active
- No anchor activity conducted from a compartment network configuration

One violation of this rule, at any point, retroactively links the compartment to the anchor for any platform that logged both sessions.

#### 10.2 Compartment Activation Protocols

Each compartment should have an explicit activation sequence — the ordered set of steps taken before any compartment activity begins:

1. Compartment device only
2. Network tool (VPN/Tor) active and verified before any other network activity
3. Browser with correct configuration loaded
4. Compartment-specific accounts accessed only after steps 1–3 confirmed

The sequence must be executed in full every time. The failure mode is the practitioner who is confident enough in their habits to skip the verification step — and who, on the one occasion the network tool failed to activate automatically, conducts compartment activity from an unprotected connection.

#### 10.3 IP Leak Verification

Before any compartment activity, verify the active IP address against an independent check service (not the VPN provider's own tool). This is a 30-second step that catches the most common failure mode: network tool active but leaking real IP due to configuration error or DNS leak.

#### 10.4 Compartment Inventory

Maintain a private, encrypted record of:

- All compartment accounts, platforms, usernames
- Associated email addresses and phone numbers
- Payment methods used
- Account creation dates and IP addresses used (if known)
- Current status

This is an operational security document. It must not exist on any device that bridges compartments, and it must be encrypted at rest. Its purpose is twofold: operational memory (the practitioner can track what exists where) and decommissioning (knowing what must be closed when a compartment is retired).

#### 10.5 Compartment Retirement

Compartments that are no longer operationally required must be actively retired, not abandoned:

- Delete accounts rather than leaving them dormant — dormant accounts continue to exist as linkage points and are subject to platform data handling practices
- Revoke any permissions granted to third-party applications
- Ensure associated email addresses are also decommissioned or retained only within the compartment if the compartment is partially maintained

---

### 11. Threat Model Calibration

No compartmentalization is absolute. The correct question is not "is this perfect?" but "is this adequate against my actual adversary?"

|Adversary|Capabilities|Required Defense Level|
|---|---|---|
|Platform automated systems|Behavioral/technical correlation, social graph analysis|Moderate — distinct devices, networks, accounts, behavioral profiles|
|Commercial data broker|Cross-platform data aggregation, identity resolution|Moderate-High — payment hygiene, email hygiene, minimal data provision|
|Law enforcement (domestic)|Legal process to platforms, ISP records, device seizure|High — no-log providers, physical device security, warrant canaries|
|Intelligence service (domestic)|All of the above plus network-level monitoring, endpoint compromise|Very High — Tails/Qubes, Tor, air-gapped where possible, assumes endpoint compromise risk|
|Intelligence service (foreign, sophisticated)|All of the above plus supply chain, SIGINT, human sources|Near-impossible to fully defend — reduce attack surface, accept residual risk|

[Inference] The practitioner who designs against a sophisticated intelligence service adversary while their actual adversary is platform automated systems is spending operational resources that do not improve their actual security posture. Threat model accuracy is as important as defense depth.

---

**Key Points**

- Digital identity is the total aggregated signal produced by behavior across systems — the problem is preventing signal aggregation across compartments, not simply creating separate accounts
- Physical device separation is the foundational requirement; software-level compartmentalization on a shared device does not provide genuine separation
- Network compartmentalization must be structural — enforced by configuration so that unprotected access is impossible, not dependent on the practitioner remembering to activate tools
- Behavioral fingerprinting — session timing, linguistic style, content interests, social graph composition — is as capable of producing linkage as technical fingerprinting, and is frequently underestimated
- One violation of strict separation — one login of a compartment account from the anchor environment — retroactively links the compartment at that platform for all logged sessions
- Threat model calibration determines appropriate defense depth; over-engineering against the wrong adversary wastes resources; under-engineering against the actual adversary produces exposure

---

