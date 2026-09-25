## Distinguishing Root Cause from Attack Vector and Impact

### Purpose and Scope

A recurring analytical failure in security incident documentation is conflating three distinct concepts — root cause, attack vector, and impact — into a single undifferentiated narrative, which produces corrective actions that address the wrong layer of the problem. This section provides the conceptual separation needed to avoid that conflation, building on the attack-chain structuring introduced in "Root cause analysis within the incident response lifecycle."

### The Three Concepts Defined

| Concept | Definition | Answers |
| --- | --- | --- |
| Attack Vector | The specific technique or pathway the adversary used to gain access or execute an action | "How did they get in / do this?" |
| Root Cause | The systemic condition that allowed the attack vector to succeed | "Why did that technique work here?" |
| Impact | The consequence of the successful attack | "What was the result / harm?" |

These three answer fundamentally different questions, and each maps to a different category of corrective action: fixing an attack vector alone (blocking one phishing domain) does not address the root cause (no MFA enforcement, which would have stopped *any* credential-phishing vector), and neither addresses impact reduction (data segmentation that would have limited what a successful compromise could reach).

### Worked Example: Separating the Three



```
Attack Vector:
Adversary sent a phishing email containing a link to a 
credential-harvesting page; a user entered their VPN 
credentials on the fake page.

Root Cause:
The compromised account was not protected by multi-factor 
authentication, and the organization's MFA rollout policy 
exempted accounts created before a specific date rather than 
enforcing MFA organization-wide.

Impact:
The compromised account had standing local administrator 
rights on a jump host due to an overly broad privileged-access 
group assignment, enabling lateral movement to the file server 
and exfiltration of approximately 40GB of data before detection.
```

Notice that each of the three supports a different, non-overlapping corrective action:

| Layer | Corrective Action | What It Prevents |
| --- | --- | --- |
| Attack Vector | User security awareness training; email filtering rule for this campaign's indicators | This specific phishing campaign or closely similar ones |
| Root Cause | Close the MFA policy exemption; enforce MFA organization-wide regardless of account age | Any credential-theft vector against this account class, not just phishing |
| Impact | Review and reduce standing privileged-access group membership; implement just-in-time privilege elevation | The scope of harm from *any* future account compromise, regardless of initial vector |

A security RCA that documents only the attack vector (and treats "block this phishing domain" as the complete corrective action) leaves the root cause (missing MFA) and impact amplifier (excessive standing privilege) fully exploitable by the next attacker using a different vector — this is the security-domain instance of the general RCA anti-pattern of stopping at the first plausible cause rather than tracing to the systemic gap.

### Why Conflation Happens

**Key Points**

- **The attack vector is usually the most concrete and evidence-rich finding**, since it's directly observable in logs (the phishing email, the malicious file, the exploited CVE), making it tempting to treat as sufficient documentation on its own — unlike the root cause, which often requires investigating organizational policy or process decisions rather than technical logs alone.
- **Impact is often documented as a severity/scope metric rather than analyzed as a causal factor in its own right.** Data volume exfiltrated or systems affected is commonly reported purely as a magnitude ("40GB exfiltrated") without the follow-up analysis of *why* the blast radius was that large — that "why" (excessive standing privilege, flat network segmentation, absence of data loss prevention controls) is itself a distinct root-cause-style finding about impact amplification, separate from the initial-access root cause.
- **Vendor and threat-intelligence reporting conventions reinforce vector-only framing.** External threat intelligence reports and vendor incident summaries frequently describe incidents primarily by attack vector and technique (matching MITRE ATT&CK-style reporting), which is appropriate for detection-engineering purposes but can be mistakenly adopted wholesale as the organization's own internal root-cause finding without the additional "why did this work against us specifically" layer.
- **Pressure for a fast public or executive narrative favors the vector-level explanation.** "We were hit by a phishing attack" is a simpler statement than "our MFA enforcement policy had an exemption gap that a phishing-derived credential was then able to exploit," even though only the latter identifies what needs to change to prevent the next, differently-vectored incident.

### A Structured Test for Separation

A practical check for whether a security incident write-up has actually separated these three layers: for each finding, ask **"if we only fixed this, would a different attack vector achieve the same impact?"**

- If fixing the *attack vector* alone still leaves the same impact achievable via a different vector → the finding was root cause, not vector, and is likely mislabeled (or an additional root cause finding is missing).
- If fixing the *root cause* alone would have stopped this incident (and structurally similar ones using different vectors) → correctly identified as root cause.
- If fixing a finding only reduces the consequence *after* compromise, without preventing the compromise itself → correctly identified as an impact-amplification factor, not a root cause.

Applied to the worked example: blocking the specific phishing domain does not stop credential theft via a different phishing campaign or a credential-stuffing attack against the same MFA-exempt account — so "user awareness training" and "block this domain" are correctly vector-level actions, not root-cause remediation. Enforcing MFA organization-wide *would* have stopped this incident and most other credential-theft-based vectors against that account — correctly identified as root cause.

### Relationship to Attack Chain Documentation

In the kill-chain / attack-chain documentation format introduced in "Root cause analysis within the incident response lifecycle," each stage of the chain can independently contain vector, root cause, and impact-amplification findings — this is a common source of confusion when teams try to force a single root-cause statement onto a multi-stage chain:



```
Stage: Privilege Escalation
  Attack Vector:  Adversary used cached admin credentials 
                  found on the jump host to authenticate 
                  to the file server.
  Root Cause:     Jump host was configured to cache 
                  credentials beyond the organization's 
                  own hardening standard, which explicitly 
                  prohibits credential caching on 
                  internet-facing bastion hosts.
  Impact factor:  N/A at this stage (impact realized in 
                  later exfiltration stage)
```

Rather than a single organization-wide root cause statement, mature security RCA documentation often produces **one root-cause finding per relevant attack-chain stage**, since different stages frequently trace to different systemic gaps (an MFA policy gap at initial access; a credential-caching hardening violation at privilege escalation) — collapsing these into one root cause statement typically means only the most prominent or earliest-stage gap gets remediated while others persist.

### Key Points

- Attack vector, root cause, and impact are three distinct analytical layers answering "how," "why it worked," and "what resulted," respectively — each requires a different category of corrective action, and conflating them produces incomplete remediation.
- The "would a different vector achieve the same impact" test is a practical, repeatable way to verify whether a stated finding is actually a root cause or merely a vector-level observation mislabeled as one.
- Impact magnitude (volume of data, number of systems) should be followed by its own "why was the blast radius this large" analysis, since impact-amplifying factors (privilege, segmentation, DLP gaps) are themselves systemic findings independent of the initial-access root cause.
- Multi-stage attack chains frequently contain distinct root causes at different stages; a single organization-wide root-cause statement risks under-remediating stages beyond the first.
- Vendor and threat-intelligence reporting conventions (which emphasize vector/technique for detection purposes) are not a substitute for internal root-cause analysis focused on why the organization's own controls failed to prevent or limit the incident.

### Related Topics

- MITRE ATT&CK framework and per-stage technique documentation
- Privilege access management and just-in-time elevation as impact-reduction controls
- MFA policy design and exemption/exception governance
- Data loss prevention and network segmentation as blast-radius limiting controls
- Root cause analysis within the incident response lifecycle (attack-chain structuring foundation)