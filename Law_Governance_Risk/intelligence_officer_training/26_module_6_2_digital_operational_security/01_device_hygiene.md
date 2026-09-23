## Device Hygiene


---

### Foundational Framing

Device hygiene is the discipline of managing the information your devices generate, store, transmit, and leak — intentionally and unintentionally. It is not primarily about installing software. It is about understanding the threat model specific to your situation and making deliberate, consistent decisions about device behavior across the full lifecycle of ownership: acquisition, configuration, use, and disposal.

The failure mode in most device hygiene practice is not ignorance of tools. It is inconsistency — one lapse in a otherwise disciplined pattern is frequently sufficient to compromise the pattern entirely. Metadata, behavioral patterns, and residual data are often more revealing than content.

---

### Threat Modeling First

No device hygiene practice is meaningful without a defined threat model. The appropriate measures for a journalist protecting a source differ from those for a corporate whistleblower, which differ again from those for an intelligence officer in a hostile environment.

Before selecting any measure, define:

- **Who is the adversary?** Individual, corporation, law enforcement, foreign intelligence service, or some combination. Capability level matters enormously.
- **What are they after?** Content of communications, identity of contacts, location history, behavioral patterns, or proof of a specific act.
- **What access do they have?** Physical access to devices, network-level interception capability, legal compulsion authority, or technical exploitation capability.
- **What is the consequence of failure?** Embarrassment, professional harm, legal jeopardy, physical danger.

[Inference] Measures appropriate for a low-capability adversary may be insufficient against a state-level actor with zero-day exploit capability and legal compulsion authority. No open-source hygiene practice guarantees protection against a sufficiently resourced and motivated adversary.

---

### Device Acquisition

#### Identity Separation at Purchase

The device itself is a node of identity. If the purchase is traceable to you, the device is linked to you from the moment of acquisition.

- Cash purchase from a physical retailer, without loyalty cards or surveillance camera avoidance, is not anonymous. [Inference — most retail environments have CCTV; cash transactions at point of sale do not inherently prevent identification.]
- Purchase with a card, online, or with an account creates a durable record linking your identity to the device's serial number, IMEI, and MAC address.
- Devices received as gifts or acquired secondhand carry their own prior history, which may include registered accounts, prior SIM associations, or residual data.

**Key Points**

- For a device intended to be operationally separated from your primary identity, the acquisition method is the first and one of the most durable links. It cannot be undone after the fact.
- The gap between acquisition and first use matters. A device purchased under your identity and then factory-reset is still linked to you at the point of sale.

#### Hardware Identifiers

Every device carries multiple hardware identifiers that persist regardless of software state:

- **IMEI** (International Mobile Equipment Identity): unique to the physical device, transmitted to the cellular network on connection, cannot be changed on most consumer devices without hardware modification.
- **MAC address**: unique to the network interface card. Transmitted during Wi-Fi and Bluetooth connection. Software-level MAC randomization is available on modern operating systems but implementation varies and is not always reliable across all connection types.
- **Serial number**: registered at manufacture, linked to purchase record, used in warranty and repair systems.

[Inference] A device whose IMEI has been logged by a cellular carrier in association with a SIM card registered to your identity, or used in a location you were known to be, is linked to you regardless of subsequent SIM changes or resets.

---

### Operating System and Software Baseline

#### Stock vs. Modified Operating Systems

Consumer operating systems (iOS, Android, Windows, macOS) are designed for usability and ecosystem integration, not operational security. They transmit telemetry, maintain logs, sync data to cloud services by default, and are subject to lawful access requests directed at the platform provider.

- **iOS**: Closed ecosystem with strong device encryption, but significant iCloud integration by default. Apple has complied with lawful access requests for cloud data. Device-level extraction is difficult for most adversaries but not impossible for state-level actors with exploit capability.
- **Android (stock)**: Variable security depending on manufacturer and version. Google integration transmits significant behavioral data. Some manufacturers add additional telemetry layers.
- **GrapheneOS** (Android-based, open-source): Designed explicitly for security and privacy. Removes Google services by default, hardens the OS against exploitation, provides strong sandboxing. Runs on Google Pixel hardware. [This is a factual description of a publicly available project; capability claims should be verified against current documentation at grapheneos.org.]
- **Tails OS** (Linux, live boot): Designed for amnesia — leaves no trace on the host device, routes all traffic through Tor by default. Requires booting from USB; not suitable for a primary device.
- **Qubes OS** (Linux, compartmentalization architecture): Runs applications in isolated virtual machines. Strong isolation between activities. High technical overhead; steep learning curve.

**Key Points**

- The operating system choice establishes the ceiling of what hygiene measures can achieve. Hygienic behavior on a telemetry-heavy stock OS does not achieve the same outcome as equivalent behavior on a hardened OS.
- No operating system eliminates risk. Each represents a different tradeoff between usability, compatibility, and security posture.

#### Application Selection Principles

- **Minimize installed applications.** Each application is an additional attack surface, an additional telemetry source, and an additional permission holder.
- **Audit permissions.** Camera, microphone, location, contacts, and storage permissions should be granted only when necessary and revoked after use where the OS supports it.
- **Prefer open-source applications** where equivalent functionality exists. Open-source code can be audited; closed-source code cannot. [Inference — availability of source code does not guarantee the code has been audited, or audited recently, or that the compiled binary matches the source.]
- **Avoid applications that require account creation** linked to your primary identity for functions where that linkage is unnecessary.
- **Browser selection**: Browsers are among the highest-risk applications for behavioral tracking. Firefox with appropriate configuration, Tor Browser, and Brave are commonly recommended in privacy-focused open-source literature. Each has tradeoffs.

---

### Network Hygiene

#### Wi-Fi

- **Avoid open public Wi-Fi** for sensitive activity. Traffic on unencrypted networks is trivially interceptable. Even encrypted connections may be subject to man-in-the-middle attacks on hostile networks.
- **MAC address randomization** should be enabled. Most modern operating systems offer this, but implementation is inconsistent — some randomize per network, some per connection, some not at all by default.
- **Forget networks after use.** Devices broadcast probe requests for remembered networks, which can be used to identify the device's history of locations.
- **Home network**: Router firmware should be updated. Default router credentials must be changed. Guest network isolation prevents devices from accessing each other's traffic.

#### Cellular

- **IMSI catchers** (Stingrays and equivalents) are devices that simulate cell towers to intercept traffic and identify devices in an area. They are used by law enforcement in multiple jurisdictions and are available to some non-state actors. [Factual — this technology is well-documented in public court filings and journalism.] Protection against IMSI catchers is limited at the user level; some hardened Android builds include detection heuristics. [Inference — detection heuristics are not fully reliable against sophisticated implementations.]
- **SIM registration**: In most jurisdictions, SIM cards require identity registration. A SIM registered to your identity links all calls, messages, and data to that identity at the carrier level.
- **Prepaid SIMs**: In jurisdictions where unregistered prepaid SIMs are available, they reduce the direct identity link at the carrier. However, behavioral patterns, device IMEI, and location data can still link usage to an individual. [Inference — prepaid SIM purchase with cash does not produce anonymity; it reduces one specific identity link.]
- **Airplane mode**: Disabling all radios eliminates most active transmission but does not prevent logging of data for later transmission when radios are re-enabled on some platforms.

#### VPNs

VPNs shift trust from the ISP or local network to the VPN provider. They do not provide anonymity — they change who can see your traffic, not whether your traffic is visible.

- The VPN provider can log traffic, connection times, and IP addresses. Provider logging policies are self-reported and vary in verifiability. [Inference — no-log claims cannot be independently verified without third-party audit, and audits have limited scope.]
- VPNs do not protect against application-layer tracking, device fingerprinting, or behavioral analysis.
- VPNs are useful for protecting against local network interception and preventing ISP-level traffic visibility. They are not a sufficient privacy measure against a determined adversary with access to the VPN provider or upstream network infrastructure.

#### Tor

Tor routes traffic through a series of volunteer-operated relays, encrypting each layer, so that no single relay knows both the origin and destination of traffic.

- Provides stronger anonymity than a VPN against network-level adversaries.
- Does not protect against application-layer deanonymization (logging into an account, browser fingerprinting, behavioral patterns).
- Exit node traffic is unencrypted — the exit node can see destination and content if the connection is not additionally encrypted (HTTPS).
- Tor Browser is the recommended client for web browsing over Tor; configuring another browser to use the Tor network without the Tor Browser's additional protections produces a weaker result.
- [Inference] Tor provides meaningful protection against passive network surveillance but is not guaranteed against a global adversary capable of correlating traffic at both entry and exit points. This is a known theoretical limitation documented in the academic literature.

---

### Communication Security

#### Messaging

- **End-to-end encryption (E2EE)** ensures that only the communicating parties can read message content. The service provider cannot decrypt messages in transit.
- **Signal**: Open-source, E2EE by default for all messages and calls, minimal metadata retention, disappearing messages available. Widely regarded in security research as the current standard for secure messaging. Requires a phone number for registration — this is a linkage point.
- **Metadata**: E2EE protects content, not metadata. Who communicated with whom, when, how frequently, and for how long is often retained at the provider level and is accessible under legal compulsion even when content is not. Signal retains minimal metadata by design; other E2EE platforms vary.
- **SMS and standard calls** are not encrypted in transit. They are accessible to the carrier and, under compulsion, to law enforcement. Treat them accordingly.

#### Email

Email is structurally insecure. Headers contain routing metadata. Most providers retain full content. Encryption requires coordination between sender and receiver.

- **PGP/GPG encryption** encrypts email content end-to-end. Requires both parties to have and correctly use keys. Metadata (sender, recipient, timestamp, subject line) remains unencrypted.
- **ProtonMail and Tutanota** offer E2EE between users of the same service and have stronger privacy policies than major commercial providers. End-to-end encryption does not apply when communicating with users of non-encrypted services.
- [Inference] Email is a structurally difficult medium to secure fully. For sensitive communication, a purpose-built messaging application with E2EE is preferable to encrypted email in most threat models.

#### Voice Calls

- Standard cellular calls are accessible to carriers and, under legal compulsion, to law enforcement.
- Signal calls are E2EE.
- VOIP calls vary by provider; most are not E2EE by default.

---

### Physical Device Security

#### Full-Disk Encryption

Full-disk encryption (FDE) protects data on a device against physical access by someone who does not have the decryption key (typically the device PIN/passphrase).

- iOS encrypts by default when a passcode is set.
- Android encryption behavior varies by manufacturer and version; verify it is enabled.
- On desktop systems (Windows, macOS, Linux), FDE must typically be explicitly configured.

**Key Points**

- FDE protects data at rest. It does not protect data while the device is unlocked and in use.
- A strong passphrase or PIN is required. Biometric unlocking (fingerprint, face) is convenient but may be compellable under legal authority in some jurisdictions — a passcode is more resistant to compelled disclosure in jurisdictions where the right against self-incrimination applies to knowledge rather than physical attributes. [Inference — legal treatment of biometric vs. passcode compulsion varies by jurisdiction and is an evolving area of law.]

#### Screen Lock and Auto-Lock

- Auto-lock should be configured for the shortest acceptable interval.
- A strong PIN (6+ digits, non-sequential, non-birthdate) or passphrase is preferable to a 4-digit PIN or pattern unlock.
- Biometric unlock is acceptable for convenience-level threats; reassess for higher threat models.

#### Physical Access

- An unlocked device left unattended is fully compromised regardless of all other measures.
- A device submitted for repair may be accessed beyond the stated purpose. [Inference — this is a documented risk; the frequency and targeting of such access by repair personnel varies and cannot be generalized.]
- Devices crossing borders are subject to physical search and potential imaging. In some jurisdictions, border agents have authority to compel device access. Device imaging at a border crossing can produce a complete copy of all data on the device at that moment.

#### Camera and Microphone

- Cameras and microphones can be accessed by malicious applications or, at higher threat levels, by exploit-implanted spyware (e.g., commercial spyware in the class of Pegasus). [Pegasus is publicly documented through research by Citizen Lab and Amnesty International's Security Lab.]
- Physical camera covers exist for laptops. Microphone disabling at the hardware level is not straightforwardly achievable on most consumer devices.
- At lower threat levels, rigorous application permission management reduces risk. At higher threat levels, assume that a networked device with a microphone is a potential listening device when sensitive conversations are occurring.

---

### Data Minimization

#### What Is Not Stored Cannot Be Disclosed

Data minimization — storing the least data necessary for the least time necessary — reduces the surface area of what can be extracted, compelled, or compromised.

- **Disappearing messages**: Configure Signal and equivalent applications to auto-delete after the shortest interval consistent with operational need.
- **Browser history**: Clear regularly, or use private/incognito mode for sensitive browsing (noting that incognito mode does not prevent server-side logging, ISP visibility, or network-level interception — it only prevents local history storage).
- **Cloud backups**: Automatic cloud backup of a device backs up all data on that device to a server subject to the provider's access policies and legal compulsion. For sensitive devices, disable automatic backup or use an E2EE backup solution.
- **Photos and files**: Metadata embedded in photos (EXIF data) includes GPS coordinates, timestamp, device model, and sometimes lens and settings data. Strip EXIF data before sharing images if location or device information is sensitive.

#### Retention Discipline

Define retention rules for categories of data:

- Communication content: deleted after X days
- Location history: disabled entirely or cleared on defined schedule
- Application data: audited periodically and unnecessary data deleted
- Accounts: deactivated when no longer operationally necessary rather than left dormant

Dormant accounts with accumulated history represent a persistent data store accessible under compulsion or compromise even when not actively used.

---

### Behavioral Patterns as Data

Device hygiene is not only about what data is stored — it is about what behavioral patterns the data reveals.

- **Location patterns**: Regular appearance at the same location at the same time is identifiable even from anonymized location data. Research has demonstrated re-identification of individuals from ostensibly anonymous location datasets. [This is documented in academic research, including work by de Montjoye and colleagues on location data re-identification.]
- **Usage patterns**: Time of activity, application usage sequences, typing rhythm (keystroke dynamics), and browsing behavior all constitute behavioral fingerprints that can identify individuals across accounts and sessions.
- **Contact graph**: Who you communicate with, how frequently, and at what times reveals your social and operational network even when content is encrypted.
- **Search behavior**: Search queries constitute a detailed record of interests, concerns, and activities. Search history on major platforms is retained and accessible under compulsion.

**Key Points**

- Compartmentalization of devices and accounts must extend to behavioral pattern separation. Using a supposedly separate operational device at the same times, from the same locations, and in the same sequences as your primary device partially defeats the separation.
- True behavioral separation requires deliberate pattern discipline, not just technical separation.

---

### Device Disposal and Sanitization

A discarded device is a data source unless properly sanitized.

- **Factory reset alone is insufficient** on many devices. Residual data recovery from reset devices is documented. [Factual — this is established in digital forensics literature.]
- **Secure erase**: Most modern iOS devices perform cryptographic erase on factory reset (the encryption key is destroyed, rendering data unrecoverable without the key). Android behavior varies by manufacturer and version.
- **Physical destruction** is the most reliable method for high-sensitivity devices. Destruction of storage media specifically (not just the device casing) is necessary.
- **Before disposal**: Remove and separately dispose of SIM and SD cards. Deregister the device from all linked accounts. Remove all accounts before factory reset so account association does not survive the reset.

---

### Operational Device Separation

For individuals managing multiple identities or operational contexts, device separation is a foundational principle.

- **One device per identity context.** A device used under your primary identity should never be used for activity associated with a separated operational identity, and vice versa.
- **No physical colocation patterns.** Devices associated with different identities that are routinely in the same location simultaneously can be correlated by location data alone, defeating identity separation.
- **No cross-contamination of accounts.** Logging into a primary identity account on an operational device, or accessing operational accounts from a primary device, creates a durable linkage.
- **No shared networks.** Connecting both devices to the same home Wi-Fi network links their MAC addresses to the same router, which may be logged by the ISP.

[Inference] Complete operational device separation is demanding to maintain consistently. A single cross-contamination event may be sufficient to defeat the separation, depending on the adversary's capability and the data they have access to.

---

### Patch Management and Update Discipline

- **Keep operating systems and applications updated.** The majority of successful device compromises exploit known vulnerabilities for which patches exist but have not been applied. [This is consistently reported in security incident analyses across sectors.]
- **Enable automatic updates** where the device and threat model permit, or establish a fixed update review schedule.
- **End-of-life devices** no longer receiving security updates should be considered compromised against any adversary with knowledge of unpatched vulnerabilities. Continued use represents a persistent and growing exposure.

---

### Spyware and Commercial Exploit Threats

At elevated threat levels, conventional hygiene measures may be insufficient against commercial spyware (Pegasus, Predator, and equivalents) that exploit zero-day vulnerabilities — vulnerabilities unknown to the vendor and therefore unpatched.

- These tools have been documented targeting journalists, activists, lawyers, and political figures. [Documented by Citizen Lab, Amnesty International Security Lab, and others in publicly available research.]
- They can access device content, activate camera and microphone, intercept communications before encryption, and operate without any user interaction in some implementations (zero-click exploits).
- Defense against zero-day exploits is limited at the device level. Measures that reduce the attack surface — minimizing installed applications, using hardened operating systems, enabling Lockdown Mode on iOS (which restricts functionality to reduce exploit surface) — reduce but do not eliminate risk.
- **Lockdown Mode** (iOS 16+): Explicitly designed to reduce attack surface for high-risk users. Restricts link previews, certain attachment types, wired connections, and other features. [Factual — documented by Apple.]

[Inference] Against a state-level adversary deploying current zero-day exploits, no consumer device hygiene practice guarantees protection. The appropriate response at this threat level involves operational design choices beyond device configuration — including the assumption that devices may be compromised and planning communication and behavior accordingly.

---

### Skill Development Practices

- **Audit current devices**: Review all installed applications, granted permissions, active accounts, and enabled sync services. Remove what is not necessary. This is not a one-time task — schedule it quarterly.
- **Threat model documentation**: Write a current threat model for your actual situation. Revisit it when your operational context changes.
- **Practice device separation**: Establish and maintain behavioral separation between two device contexts for a defined period. Assess where the separation holds and where it fails.
- **EXIF audit**: Review the metadata embedded in recently taken photos using an EXIF viewer. Assess what that data reveals.
- **Network traffic observation**: Use a network monitoring application to observe what your device is transmitting when idle. [Inference — interpreting network traffic requires technical knowledge; results may not be self-explanatory without background in network protocols.]
- **Sanitization drill**: Practice the full disposal procedure on a non-sensitive device. Confirm what the procedure actually achieves on your specific hardware.

---

### Integration with Adjacent Modules

- **OSINT** — Device hygiene determines what digital traces are available for open-source collection against you. The data minimization and behavioral pattern disciplines here directly reduce OSINT exposure.
- **Digital OPSEC** — Device hygiene is the hardware and software layer of digital OPSEC. Account discipline, identity separation, and communication security extend the same principles to the account and behavior layers.
- **Covert Communication** — The communication security section here provides the device-level foundation; the covert communication module addresses protocol, tradecraft, and operational communication discipline built on top of this foundation.
- **Cover and Legend** — A device that is inconsistent with a cover identity — containing contacts, applications, or behavioral patterns incompatible with the legend — is a vulnerability. Device selection and configuration must be coherent with the cover being maintained.

---

