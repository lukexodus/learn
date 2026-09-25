## Templates for Recurring RCA Documentation

### Purpose and Scope

Recurring RCA documentation templates standardize how organizations capture root cause analysis for incidents that follow predictable patterns — production outages, manufacturing defects, customer escalations, or safety events. A template enforces consistent data capture across analyses, which enables trend analysis across multiple RCAs, reduces time-to-document during high-stress incidents, and ensures no critical field (timeline, impact, causal chain, verification) is skipped under pressure.

Templates differ from one-off RCA reports in that they are designed for repeated use by different authors across different incidents, so field definitions must be unambiguous and self-explanatory without relying on tribal knowledge.

### Core Template Structure

A recurring RCA template typically contains these sections, in order:

**1. Header / Metadata Block**

| Field | Description |
| --- | --- |
| RCA ID | Unique identifier (e.g., `RCA-2026-0142`) for cross-referencing |
| Title | Short, specific description of the problem |
| Date of Incident | When the problem occurred |
| Date of RCA | When the analysis was conducted |
| Author(s) | Person(s) who led the RCA |
| Severity / Priority | Classification (e.g., SEV1–SEV4, or Critical/High/Medium/Low) |
| Status | Draft / Under Review / Approved / Closed |
| Related Tickets | Links to incident tickets, JIRA IDs, support cases |

**2. Problem Statement**

A single, precise sentence describing what went wrong, stated without assuming cause. This section resists scope creep by fixing the boundary of investigation before the "5 Whys" begins.

Example: "Between 14:02 and 14:47 UTC, 38% of API write requests to the `/v1/orders` endpoint returned HTTP 503."

**3. Impact Summary**

Quantified consequences: duration, users/customers affected, revenue impact, SLA breaches, downstream systems affected. This section justifies the RCA's priority and is often what stakeholders read first.

**4. Timeline of Events**

A chronological, timestamped log of detection, escalation, mitigation, and resolution. This is factual and observational — no causal interpretation belongs here.

| Time (UTC) | Event | Source |
| --- | --- | --- |
| 14:02 | Error rate alert fires | Datadog monitor |
| 14:05 | On-call engineer paged | PagerDuty |
| 14:18 | Root service identified as `orders-writer` | Engineer investigation |
| 14:47 | Rollback completed, errors cleared | Deploy log |

**5. 5 Whys Analysis Block**

The core causal-chain section. Each "Why" should be a discrete, falsifiable statement supported by evidence, not speculation.



```
Why 1: Why did API write requests return 503?
→ Because the orders-writer service pool exhausted available connections.

Why 2: Why did the connection pool become exhausted?
→ Because a recent deploy introduced a query that held connections open longer than expected.

Why 3: Why did that query hold connections open longer?
→ Because it performed a full table scan instead of using the indexed lookup path.

Why 4: Why was the query not using the index?
→ Because a schema migration silently dropped the composite index it depended on.

Why 5: Why did the migration drop the index without detection?
→ Because the CI pipeline's migration review step does not diff index changes,
   and no post-migration query performance check exists.
```

Templates should include a field for **evidence per Why** (log excerpt, metric snapshot, code diff link) so each causal link is auditable rather than asserted.

**6. Root Cause Statement**

A single, synthesized statement — distinct from the last "Why" — that names the systemic gap. In the example above, the root cause is not "the index was dropped" but "the migration review and deployment pipeline lacks automated safeguards against unreviewed index changes."

**7. Contributing Factors**

Secondary conditions that worsened impact or delayed detection but were not the causal root — e.g., "alert threshold was set too high, delaying detection by 12 minutes."

**8. Corrective and Preventive Actions (CAPA)**

| Action | Type | Owner | Due Date | Status |
| --- | --- | --- | --- | --- |
| Add index-diff check to migration CI step | Preventive | @jsmith | 2026-10-08 | Open |
| Lower error-rate alert threshold for orders-writer | Corrective | @adoe | 2026-10-01 | Done |
| Add automated post-migration query plan check | Preventive | @jsmith | 2026-10-15 | Open |

Distinguishing **corrective** (fixes this instance) from **preventive** (prevents recurrence class-wide) actions is a common field in mature templates, since organizations often fix the symptom but skip the systemic fix.

**9. Verification / Follow-up**

A field completed after the corrective actions are implemented, confirming the fix was effective — often a scheduled follow-up date rather than filled in at RCA creation time.

**10. Lessons Learned / Knowledge Base Tag**

Free-text summary plus categorical tags (e.g., `database`, `ci-cd`, `migration-safety`) that allow the RCA to be indexed and retrieved when similar incidents recur — this is what makes "recurring" templates valuable as an aggregate dataset, not just individual reports.

### Template Design Principles

**Key Points**

- Separate observation from interpretation: the Timeline section must contain only verifiable facts; causal reasoning is confined to the 5 Whys block.
- Use structured fields (tables, dropdowns, tags) over free text wherever the field will later be aggregated or searched — severity, category, and status fields should be constrained to a fixed vocabulary.
- Require evidence links per causal step; an RCA template without an evidence field tends to produce reports that are internally consistent but unverifiable.
- Version the template itself. As an organization matures its RCA process, template fields change (e.g., adding a "blast radius" field after a multi-service incident); keep a template version number in the metadata so historical RCAs can be interpreted against the schema they were written under.
- Make the root cause field distinct from the final Why. Many teams that skip this step end up over-indexing on the technical trigger rather than the systemic gap, weakening the CAPA section. [Inference — this is a commonly cited failure mode in RCA process literature, not a universal law]

### Template as Structured Data (Machine-Readable Variant)

For organizations building an RCA knowledge base or dashboard, templates are often defined as structured schemas (YAML/JSON) rather than prose documents, enabling automated aggregation across RCAs.

```yaml
rca_id: RCA-2026-0142
title: "orders-writer 503 spike"
severity: SEV2
status: closed
timeline:
  - time: "2026-09-14T14:02:00Z"
    event: "Error rate alert fired"
    source: "Datadog"
five_whys:
  - level: 1
    statement: "API writes returned 503"
    evidence: "datadog-alert-8821.png"
  - level: 2
    statement: "Connection pool exhausted"
    evidence: "pool-metrics-14-05.csv"
root_cause: "Migration CI lacks index-diff safeguards"
capa:
  - action: "Add index-diff check to migration CI"
    type: preventive
    owner: "jsmith"
    due: "2026-10-08"
    status: open
tags: [database, ci-cd, migration-safety]
```

This structure allows tooling to answer aggregate questions such as "how many RCAs in the last quarter trace to a migration-related root cause," which a purely prose-based template cannot support without manual re-reading.

### Template Governance

**Next Steps**

- A **review cadence** field (e.g., "reviewed quarterly by SRE lead") keeps the template current as failure modes evolve.
- A **template retirement/deprecation policy** avoids silent drift where different teams use divergent, incompatible copies.
- Access control on the "Root Cause" and "CAPA" fields (requiring sign-off before status moves to "Approved") is common in regulated environments (e.g., ISO 9001, SOC 2) where RCA documentation is audited.

### Related Topics

- The "5 Whys" methodology and its failure modes (stopping too early, single-cause bias)
- Fishbone (Ishikawa) diagrams as a complementary causal-mapping technique
- Blameless postmortem culture and its relationship to RCA documentation quality
- RCA knowledge base design and tagging taxonomies
- Metrics for RCA program maturity (time-to-RCA, CAPA closure rate, recurrence rate)