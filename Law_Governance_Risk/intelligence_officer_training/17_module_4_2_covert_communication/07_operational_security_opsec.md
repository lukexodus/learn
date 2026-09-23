## Operational Security (OPSEC)


---

### What OPSEC Is

OPSEC is a systematic process for denying adversaries information that could be used to harm your mission, identity, or assets. It originated as a U.S. military doctrine (Operation PURPLE DRAGON, Vietnam era) but its principles are universally applicable to any individual or organization that has something worth protecting.

OPSEC is not secrecy for its own sake. It is the disciplined management of your information environment — what you reveal, to whom, when, and how.

The canonical five-step OPSEC process:

1. **Identify critical information**
2. **Analyze threats**
3. **Analyze vulnerabilities**
4. **Assess risk**
5. **Apply countermeasures**

---

### Step 1 — Identify Critical Information

Critical information is any data whose exposure would give an adversary an advantage or cause you measurable harm. It is defined relative to a specific threat actor and mission context, not in the abstract.

Categories to consider:

- **Identity data** — legal name, aliases, biometrics, voice, gait, face
- **Location data** — home, workplace, routine routes, frequent locations
- **Associations** — family, colleagues, contacts, networks
- **Intentions and plans** — what you are going to do, when, why
- **Capabilities** — what skills, tools, or resources you have
- **Vulnerabilities** — fears, financial stress, health conditions, leverage points
- **Communications metadata** — who you contact, how often, at what times

**Key Points**

- A piece of information that is harmless in isolation may become critical when aggregated with other data. This is the aggregation problem — the central challenge of personal OPSEC.
- Define your critical information list (CIL) before you assess anything else. Without it, you are defending everything and nothing simultaneously.

---

### Step 2 — Analyze Threats

A threat is any entity with both the **capability** and **intent** to collect your critical information and act on it adversely.

Threat modeling requires you to think adversarially. Who specifically would want this information? What can they actually do?

#### Threat Actor Categories

|Actor Type|Typical Capabilities|Typical Intent|
|---|---|---|
|Nation-state intelligence service|SIGINT, HUMINT, cyber, physical surveillance|Strategic, patient, resourced|
|Law enforcement|Legal process, OSINT, some technical capability|Investigative, procedurally constrained|
|Criminal organization|OSINT, social engineering, physical|Financial, opportunistic|
|Corporate adversary|OSINT, litigation, infiltration|Competitive advantage|
|Individual stalker/harasser|OSINT, social media, social engineering|Personal, often emotionally driven|
|Journalist|OSINT, FOIA, source cultivation|Exposure|

#### Threat Assessment Questions

- What is their collection methodology? (technical, human, open-source)
- What is their access? (physical proximity, network access, legal authority)
- What is their patience? (one-time opportunistic vs. sustained campaign)
- What triggers their interest? (your activity, associations, profile)

**Key Points**

- Not every adversary is a sophisticated state actor. Many failures come from underestimating low-sophistication but highly motivated actors.
- [Inference] A threat actor with limited technical capability but high social access (e.g., someone in your personal network) may pose a greater practical risk than a technically capable but distant actor. Each case requires individual assessment.

---

### Step 3 — Analyze Vulnerabilities

A vulnerability is a gap between your current security posture and what is required to deny a specific threat actor access to your critical information.

Vulnerabilities exist in four domains:

#### Physical

- Visible behavior patterns (predictable routes, schedules)
- Observable meetings or associations
- Documents, devices, or materials left unsecured
- Dumpster-accessible waste (discarded receipts, mail, printed documents)
- Facial or vehicle recognition exposure

#### Digital

- Metadata embedded in files (EXIF data in photos, document properties)
- Device identifiers (MAC address, IMEI, advertising ID)
- Account linkages (same username, email, or phone number across platforms)
- Browser fingerprinting
- Login timestamps and IP logs
- Cloud sync behavior
- App permissions broadcasting location, contacts, microphone

#### Communications

- Unencrypted or inadequately encrypted channels
- Communications metadata (who, when, how often — even if content is encrypted)
- Device association (calls or messages linked to a real identity via SIM or account)
- Behavioral patterns in communication (response times, active hours)

#### Human/Social

- Information shared unnecessarily in conversation
- Social media posts, check-ins, or tagged photos
- Third-party disclosure (colleagues, family, associates who do not practice OPSEC)
- Elicitation by a skilled interlocutor
- Background details visible in photos (location landmarks, whiteboards, ID badges)

**Key Points**

- Your personal OPSEC is only as strong as the OPSEC of the people around you. Third-party exposure is a structural vulnerability that countermeasures cannot fully eliminate. [Inference]
- The most common vulnerabilities are not technical. They are behavioral — habitual, unconscious, and therefore persistent.

---

### Step 4 — Assess Risk

Risk = Likelihood of exploitation × Consequence of exposure

This is a prioritization step. Not all vulnerabilities are equally exploitable, and not all exposures have equal consequences.

#### Risk Matrix (simplified)

|Vulnerability|Threat Capability to Exploit|Consequence if Exploited|Priority|
|---|---|---|---|
|Home address linked to legal name|High (OSINT)|High (physical access)|Critical|
|Username reuse across platforms|High (OSINT)|Medium (profile linkage)|High|
|Email metadata exposed|Medium|Medium|Medium|
|Laptop webcam unsecured|Low (requires proximity or compromise)|High|Medium|

#### Prioritization Principles

- Address high-likelihood, high-consequence vulnerabilities first.
- Do not expend resources on low-likelihood, low-consequence risks at the expense of critical ones.
- Revisit risk assessment when your threat model changes — a new role, a new adversary, a new operation.

---

### Step 5 — Apply Countermeasures

Countermeasures are actions or controls that reduce the probability that a threat actor can collect your critical information through a known vulnerability.

#### Identity Compartmentalization

The core discipline of personal OPSEC is identity separation — creating and maintaining distinct personas or operational identities that cannot be linked to each other or to your true identity.

**Compartment design principles:**

- Each compartment has its own: email address, phone number or VoIP, usernames, payment method, devices (where feasible), and behavioral profile
- No crossover between compartments: never log into a cover account from a device or network linked to your real identity
- Legend consistency: a cover identity must be internally coherent and historically plausible

[Inference] The difficulty of maintaining compartmentalization scales with the number of compartments and the frequency of operational activity. Breakdowns typically occur under time pressure or fatigue.

#### Digital Countermeasures

**Device hygiene:**

- Separate devices for separate operational purposes where the threat level justifies it
- Full-disk encryption on all devices
- Physical camera/microphone covers when not in use
- Firmware-level awareness: some persistent threats survive OS reinstallation [Unverified for consumer hardware in most contexts — documented for high-value targets]

**Network:**

- Tor for high-anonymity requirements (with awareness of its limitations: exit node exposure, traffic correlation attacks, operational slowness)
- VPN as a basic countermeasure, not an anonymity solution — a VPN shifts trust from your ISP to the VPN provider; it does not eliminate tracking
- Public Wi-Fi with MAC address randomization for activities requiring network separation
- DNS-over-HTTPS or DNS-over-TLS to reduce ISP-level metadata exposure

**Accounts and identifiers:**

- Unique, randomized usernames per compartment
- Email aliases (e.g., SimpleLogin, AnonAddy) to prevent email address aggregation
- Temporary/burner phone numbers for SMS verification (VoIP services: Google Voice, MySudo, JMP.chat)
- Password manager with strong, unique passwords — credential reuse is one of the most exploited vulnerabilities in account security
- Hardware security keys (FIDO2/WebAuthn) for high-value accounts

**File and metadata hygiene:**

- Strip EXIF from photos before sending (tools: ExifTool, MAT2)
- Use document formats that do not embed author metadata, or scrub them before sharing
- Be aware that PDFs, DOCX files, and images can contain hidden tracking pixels or unique steganographic markers in some commercial contexts [Unverified as a widespread operational threat in most civilian contexts]

#### Communications Security

**Encryption:**

- Signal for mobile messaging — end-to-end encrypted, minimal metadata retained, disappearing messages available
- [Inference] Signal's security properties are well-documented and audited, but no tool's behavior under all adversarial conditions can be guaranteed
- Email encryption (PGP/GPG) for high-sensitivity content — note that email metadata (sender, recipient, timestamp, subject line) is not encrypted by standard PGP
- Avoid SMS for sensitive communications — SMS is transmitted in plaintext and is accessible to carriers and law enforcement without significant barrier

**Metadata discipline:**

- Even with encrypted content, communications metadata is often more operationally revealing than content
- Minimize communication frequency patterns that allow behavioral fingerprinting
- Avoid communicating from predictable locations (home, office) for sensitive matters

**Anonymity networks:**

- Tor Browser for web browsing requiring anonymity — understand its threat model: it is designed to resist traffic analysis, not endpoint compromise
- Tails OS (live OS booting from USB, leaves no trace on host machine) for high-sensitivity sessions

#### Physical Countermeasures

**Pattern of life discipline:**

- Vary routes, schedules, and venues deliberately
- Avoid predictable behaviors that allow a surveillance team to anticipate your location
- Counter-surveillance awareness — see Phase 4 for detail, but the foundation is: know what normal looks like so you can detect anomalies

**Document and material security:**

- Shred or burn sensitive documents — cross-cut shredding at minimum; micro-cut for high sensitivity
- Do not leave devices unattended in environments where physical access is possible
- Be aware of shoulder surfing in public spaces

**Social exposure:**

- Do not discuss operational matters in uncontrolled environments
- Brief those in your personal circle on what not to share and with whom — though this has limits, as you cannot fully control their behavior [Inference]

#### The OPSEC Mindset — Continuous Assessment

Countermeasures are not deployed once. OPSEC is a practice, not a configuration. The discipline requires:

- Regular review of your critical information list as context changes
- Assumption that your threat model will evolve
- Incident awareness — recognizing when a potential compromise has occurred and knowing how to respond
- Proportionality — applying countermeasures commensurate with actual threat level, not maximum paranoia; over-security creates friction that degrades operational effectiveness and sustainability

---

### Common OPSEC Failures — Pattern Analysis

These are documented or widely observed failure modes, not speculation:

|Failure Type|Mechanism|Example|
|---|---|---|
|Aggregation failure|Individual data points seem harmless; combined, they identify or expose|Posting gym selfies + neighborhood photos + daily coffee check-in = home location triangulation|
|Persona bleed|Cover identity bleeds into real identity or vice versa|Logging into a cover account from a home IP|
|Third-party exposure|An associate discloses without awareness|Family member posts a photo tagging your location|
|Metadata leakage|Technical metadata reveals what content does not|A photo timestamped and geotagged by default camera settings|
|Habitual behavior|Predictable patterns exploited by surveillance|Leaving work at the same time, same route, every day|
|Overconfidence in tools|Trusting a tool beyond its actual security properties|Assuming a VPN makes you anonymous|
|Verbal disclosure under social pressure|Elicitation succeeds because the target is unprepared|Oversharing in conversation with a seemingly friendly interlocutor|

---

### Operational Security vs. Privacy

These are related but distinct concepts.

- **Privacy** is the right to control access to personal information; it is primarily a legal and social framework.
- **OPSEC** is the operational practice of actively denying specific information to specific adversaries; it is a behavioral and technical discipline.

Privacy measures may support OPSEC, but OPSEC goes further: it is adversarial, threat-modeled, and mission-specific. A privacy tool that satisfies a legal standard may be entirely insufficient against an active human intelligence operation.

---

### Threat Modeling Frameworks — Reference

Two structured frameworks applicable here:

**STRIDE** (originally for software threat modeling, adaptable to personal OPSEC):

- Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege

**PASTA** (Process for Attack Simulation and Threat Analysis):

- A seven-stage risk-centric framework that begins with defining business/mission objectives and ends with residual risk analysis

[Inference] Both frameworks were designed for organizational security contexts. Adapting them to individual operational security requires re-scoping the "asset" and "adversary" definitions, but the analytical logic transfers.

---

### Tools Reference (Open-Source / Publicly Available)

|Purpose|Tool|Notes|
|---|---|---|
|EXIF stripping|ExifTool, MAT2|Command-line; widely used|
|Secure messaging|Signal|Audited, open-source protocol|
|Anonymous browsing|Tor Browser|Maintained by Tor Project|
|Amnesic OS|Tails|Live OS, no persistence by default|
|Password management|Bitwarden, KeePassXC|Open-source options|
|Email aliasing|SimpleLogin, AnonAddy|Open-source backends available|
|VPN (with caveats noted)|Mullvad, ProtonVPN|No-log policies, but trust-dependent|
|Full-disk encryption|VeraCrypt, BitLocker, FileVault|Platform-dependent|
|DNS privacy|NextDNS, Quad9|DoH/DoT support|

---

**Conclusion**

OPSEC is not a product or a setting. It is a continuous analytical discipline: identify what matters, model who threatens it, find where you are exposed, assess what is worth protecting against what cost, and implement countermeasures proportionate to actual risk. The most sophisticated technical toolkit fails without behavioral discipline, and behavioral discipline without threat modeling is unfocused effort. The integration of all five steps — applied iteratively — is what constitutes functional OPSEC.

---

