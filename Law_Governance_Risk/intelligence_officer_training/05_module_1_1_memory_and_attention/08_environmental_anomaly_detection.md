## Environmental Anomaly Detection


Automatic anomaly detection is not a talent. It is a perceptual habit built through deliberate schema construction, attentional training, and repeated exposure calibration. The goal of this module is to develop the capacity to detect deviation from environmental baseline without conscious effort — the way a native speaker detects a grammatical error without parsing rules explicitly.

---

### Foundational Theory

#### What "Automatic" Actually Means

In cognitive psychology, automaticity refers to the execution of a cognitive process with minimal demand on working memory and without requiring deliberate initiation. Automaticity develops through consistent, high-volume practice of a process until it is handled by procedural rather than declarative memory systems.

[Inference] Applied to anomaly detection: the goal is to shift environmental reading from a deliberate checklist operation to a pre-attentive process — where deviations surface into consciousness without the observer consciously scanning for them.

This has a well-documented basis in **pre-attentive processing** research. Certain feature contrasts — color, motion, orientation, size — are detected before focused attention is deployed. Training extends the range of features that trigger this pre-attentive response to include higher-order social and environmental patterns.

_Disclaimer: the degree to which higher-order anomaly detection can become fully automatic is [Unverified] — the research base is clearest for low-level perceptual features. For complex social anomalies, a more accurate description may be "fast and low-effort" rather than "fully automatic."_

---

#### Baseline vs. Deviation

Every anomaly is defined relative to a baseline. Without an accurate baseline model, deviation detection is noise. This is the primary failure mode of untrained observers — they react to personal unfamiliarity rather than genuine environmental deviation.

A tourist reacting to a crowded market as "chaotic" is registering personal contrast, not environmental anomaly. A trained observer in the same market has already built a baseline model of that environment's normal density, movement patterns, noise level, and behavioral register — and detects deviation within it.

**Baseline construction is therefore prior to anomaly detection.** You cannot detect what is wrong until you know what is normal — for that specific environment, time of day, population, and context.

---

#### The OODA Loop and Where Anomaly Detection Sits

John Boyd's **Observe–Orient–Decide–Act** loop is a useful framing. Anomaly detection lives at the intersection of **Observe** and **Orient**:

- _Observe_: raw sensory intake — what enters perception
- _Orient_: filtering and contextualizing against prior models — what that intake means

The untrained observer has a thin Orient stage: little stored schema to contextualize input, so most data is either missed or misread. Training builds richer Orient schemas — more detailed mental models of what environments should look like — which makes deviations more salient.

---

### Categories of Environmental Anomaly

These are the operational taxonomic categories. Each requires a distinct perceptual schema.

---

#### 1. Spatial Anomalies

Deviations in the physical arrangement or use of space.

- An object that is out of place relative to the logic of the space (a bag left against a wall in a corridor where no one waits)
- A door that is open when context dictates it should be closed (or vice versa)
- A vehicle parked in a position inconsistent with normal traffic behavior for that street and time
- Asymmetry in an otherwise symmetric environment (one blind tilted differently, one window open in a row of closed ones)
- Wear patterns inconsistent with stated use (a path worn into grass near a fence that "has no traffic")

---

#### 2. Behavioral Anomalies

Deviations in how individuals or groups occupy and move through a space.

- **Pace incongruity**: someone moving significantly slower or faster than the ambient population without a contextual explanation
- **Gaze direction anomaly**: looking away from what the ambient population looks at (e.g., facing away from a performance everyone else watches; scanning exits rather than a speaker)
- **Position incongruity**: occupying a space in a way inconsistent with its stated function (standing at a café table without ordering; sitting on a bench facing away from the view it faces)
- **Repeated presence**: same individual in the same location across time intervals that exceed random probability
- **Counter-flow**: moving against the natural directional logic of a crowd or space
- **Proxemic violation**: maintaining unusual distance — either too close or deliberately far — relative to ambient proxemic norms for that culture and context
- **Grooming and self-touch spikes**: elevated self-regulatory behavior (touching face, adjusting clothing repeatedly) that deviates from the individual's own baseline in that setting
- **Synchronized behavior without apparent connection**: two individuals who appear unrelated but whose behavior is temporally correlated

---

#### 3. Acoustic Anomalies

- Silence where ambient sound is expected
- Sound from a direction inconsistent with the visual field
- Repetition of a sound at intervals too regular to be random
- Voice volume or register inconsistent with the social context
- A conversation that stops precisely as you enter perceptual range

---

#### 4. Temporal Anomalies

- Something present that should not be there at this time (a delivery van in a residential street at 02:00; scaffolding that has not changed in three weeks)
- Something absent that should be present at this time (a usually-occupied desk empty; a shop closed at its normal operating hour)
- An action performed at the wrong phase of a process (someone exiting a building before the meeting they announced they were attending could plausibly be over)

---

#### 5. Social-Contextual Anomalies

- Attire inconsistent with the environment, weather, or apparent activity — not based on fashion judgment but functional logic (wearing a coat that is too heavy for the weather; gloves indoors)
- Group composition that does not fit the context (three people in business attire in a laundromat at midday)
- Affect inconsistent with context (calm in a situation with ambient stress; distress in a situation with ambient ease)
- A person whose stated role and behavior are misaligned (a maintenance worker who does not touch any equipment)

---

#### 6. Informational Anomalies

- Signage that is inconsistent with the environment's actual use patterns
- A story with internal inconsistency (person claims to be waiting for someone; checks phone but faces away from the entrance)
- Documents or materials visible in a context where they do not belong
- Discrepancy between what someone says they are doing and what the physical environment implies

---

### The Mechanism of Schema Construction

Schema construction is the cognitive infrastructure that makes automatic detection possible.

A **schema** is a mental model of what a given environment, person, or situation normally looks like. The richer and more granular the schema, the more sensitive it is to deviation — and the faster deviation registers.

---

#### Schema Dimensions to Build

For any environment you want to develop automatic detection in, build a schema across these dimensions:

**Physical layout:**

- Entry and exit points, their normal traffic volume and direction
- Fixed furniture and object positions
- Lighting conditions at different times of day
- Zones of visibility and concealment

**Population baseline:**

- Typical demographic composition for this environment and time
- Typical density and clustering patterns
- Typical movement speed and directionality
- Typical noise level and register

**Temporal patterns:**

- Peak and low-density periods
- Typical duration of occupancy
- Recurring events and their associated behavioral signatures

**Behavioral register:**

- What activities normally occur here
- What level of attention people normally pay to their surroundings
- What normal social interaction looks like (eye contact norms, proxemics, group formation)

---

#### Schema Granularity and Signal-to-Noise

A schema that is too coarse generates false positives — everything deviates. A schema that is too granular generates false negatives — only extreme deviations register.

[Inference] The functional target is a schema calibrated to the _variance range_ of the environment: fine enough to detect meaningful deviations, coarse enough to filter out normal within-range variation.

This calibration comes from repeated exposure. A single visit builds a rough schema. Ten visits build a calibrated one.

---

### Training Methods

These are the primary methods for building automatic anomaly detection. They are ordered from foundational to advanced.

---

#### Method 1 — Baseline Logging

**Procedure:** Select a fixed environment you visit regularly (café, transit stop, office floor, park). For the first two weeks, spend 5 minutes after each visit writing a structured log:

- Approximate population count and composition
- Movement patterns
- Any objects or configurations that struck you as unusual (whether or not they were actually anomalous)
- What you were uncertain about

Do not attempt to detect anomalies yet. The sole purpose is schema construction. Anomaly detection without schema is guessing.

After two weeks, review your logs for variance patterns. Identify what is within normal range for that environment.

---

#### Method 2 — Attentional Scanning Protocol

This is a deliberate scanning routine to be practiced consciously until it becomes habitual.

Upon entering any new space, execute the following sequence within the first 60 seconds:

1. **Perimeter scan**: identify all exits and their current state (open/closed/obstructed)
2. **Population read**: estimate count, composition, density relative to space capacity
3. **Occupancy logic check**: does each person's position make sense given what the space is for?
4. **Object audit**: are there any objects present that lack an obvious owner or purpose?
5. **Acoustic baseline**: register ambient sound level and source directions
6. **Movement pattern read**: what is the dominant directionality and pace?

Initially this takes 60–90 seconds of conscious attention. With consistent practice across varied environments, [Inference] the sequence compresses and partially automatizes — though full automaticity at this level of complexity is not guaranteed.

---

#### Method 3 — Kim's Game (Structured Variant)

The standard Kim's Game tests object memory. The structured variant trains anomaly detection specifically.

**Procedure:** Photograph a real-world scene (your desk, a room, a street view). Study it for 90 seconds. After a 10-minute interval, look at the same scene with one deliberate modification introduced by a second person (or by you after enough time that you have forgotten the change). Detect the modification.

Progress through increasing complexity:

|Stage|Modifications|Scene Complexity|
|---|---|---|
|1|1 object removed|Static indoor scene|
|2|1 object added, 1 moved|Static indoor scene|
|3|Multiple changes|Outdoor or crowd scene|
|4|Behavioral change in a video clip|Dynamic scene|

---

#### Method 4 — Public Space Observation Sessions

**Procedure:** Sit in a public space for 30 minutes with no phone and no reading material. The sole task is observation.

Divide the session into three phases:

**Phase A (0–10 min):** Build baseline only. Do not evaluate. Simply catalog what is present and how people are behaving.

**Phase B (10–20 min):** Apply the occupancy logic check to every individual in view. Does their behavior fit the context? Flag incongruities without judging them — note them.

**Phase C (20–30 min):** Hold the baseline model built in Phase A and look for anything that has changed or does not fit. Note what changed, when, and what the change implies.

Write a brief log immediately after. Over time, compare logs across sessions in the same location.

---

#### Method 5 — The Anomaly Ledger

Carry a small notebook or use a text file. Each day, record a minimum of three anomalies you noticed in any environment. An anomaly here means: anything that deviated from what you expected based on context.

The discipline of the ledger forces retrospective conscious attention onto moments that might otherwise be discarded. Over weeks, it also reveals your **personal blind spots** — categories of anomaly you consistently fail to log are categories your attention is not reaching.

---

#### Method 6 — Adversarial Pairing

With a partner, take turns introducing deliberate anomalies into a shared space. The observer must identify them within a fixed time. The introducer scores what was missed.

This is [Inference] the most effective method for calibrating schema granularity, because the adversarial dynamic reveals the boundary between detectable and undetectable deviation for your current perceptual level. Without a partner, progress on this dimension is slower.

---

#### Method 7 — Analytical Reconstruction

After leaving any significant environment, reconstruct it from memory in writing or sketch:

- Where were the exits?
- Who was present and where were they positioned?
- Were there any objects you cannot account for?
- Was anyone's behavior inconsistent with the environment's logic?

This is not a memory test — it is a gap analysis. The gaps reveal which categories your attention is not capturing. Systematic gaps across multiple reconstructions indicate a schema deficiency in that category.

---

### Cognitive Pitfalls and Failure Modes

---

#### Baseline Contamination

Applying a schema from one environment to a different environment — e.g., treating a market in one city as having the same behavioral baseline as a market in another. This generates both false positives (flagging normal local behavior as anomalous) and false negatives (failing to detect deviations that are normal in the new environment and therefore not noticed as deviation).

**Corrective:** When entering an unfamiliar environment, explicitly suspend prior schema and run a fresh baseline-building phase before attempting anomaly detection.

---

#### Attentional Tunneling

Over-allocating attention to one category of anomaly (typically visual-spatial) while auditory, temporal, and social-contextual channels are ignored. This is especially common under stress or time pressure.

**Corrective:** Deliberately rotate attentional focus across sensory channels during practice sessions. The scanning protocol above is designed to enforce this.

---

#### Confirmation Bias in Anomaly Reading

Once a potential anomaly is noticed, the observer tends to interpret subsequent data as confirming it — even ambiguous data. A person who "looks suspicious" then has everything they do reread as confirmation.

**Corrective:** After flagging a potential anomaly, actively generate at least two alternative explanations for the behavior or object. Commit to no conclusion until you have a convergence of independent signals.

---

#### Personal Unfamiliarity vs. Genuine Deviation

Flagging things as anomalous because they are unfamiliar to you personally, not because they deviate from the environment's own baseline. This is the most common failure mode in cross-cultural or high-novelty environments.

**Corrective:** Ask: _is this unusual for this environment, or is it unusual for me?_ If you cannot answer because you lack sufficient baseline data, treat the read as [Unverified] until more exposure corrects it.

---

#### Over-detection Fatigue

Sustained conscious scanning is cognitively expensive. Attempting to maintain deliberate anomaly-detection vigilance continuously produces attention fatigue and paradoxically reduces detection quality.

**Corrective:** Train in bounded sessions rather than attempting continuous vigilance. The goal of automaticity is to reduce the cost of detection, not to eliminate the need for session structure during training.

---

### Measuring Progress

|Metric|How to Measure|
|---|---|
|Detection rate|In adversarial pairing: % of planted anomalies detected|
|False positive rate|In adversarial pairing: # of flagged non-anomalies per session|
|Scan speed|Time to complete the scanning protocol in a new environment|
|Schema depth|Quality and granularity of analytical reconstruction logs over time|
|Category coverage|Review anomaly ledger: which of the 6 anomaly categories appear consistently? Which are absent?|

---

### Operational Integration Notes

**On cover and concealment:** [Inference] A trained observer who knows their own detection process is better positioned to construct effective cover, because they understand what an observing counterpart is likely to notice. This is addressed in Phase 4 (Surveillance/Counter-Surveillance) but the foundation is built here.

**On stress degradation:** Detection quality degrades under acute stress due to attentional narrowing (the Easterbrook hypothesis). Training in low-stakes environments builds the schema but does not inoculate against stress-induced degradation. This is addressed in Phase 5. Note that schema robustness under stress is [Unverified] to transfer automatically from calm-state training — deliberate stress-condition practice is a separate requirement.

**On cultural context:** Behavioral anomaly detection is meaningless without cultural baseline knowledge. What constitutes a proxemic violation, a suspicious gaze pattern, or an incongruent affect varies significantly across cultural contexts. Phase 2 (Language and Cultural Fluency) directly supports the cultural grounding that makes behavioral anomaly detection valid in non-home environments.

---

**Key Points**

- Anomaly detection is schema-dependent. Detection training without baseline construction first is inversion of the correct sequence.
- The six anomaly categories — spatial, behavioral, acoustic, temporal, social-contextual, and informational — require distinct attentional modes. Proficiency in one does not transfer automatically to others.
- The anomaly ledger and analytical reconstruction are the highest-leverage daily practices because they force attention onto what was missed, not just what was caught.
- False positive control is as operationally important as detection rate. An observer who flags everything is as degraded as one who flags nothing.
- Full automaticity at the level of complex social anomaly detection is [Inference] achievable for experienced practitioners but is [Unverified] as a guaranteed training outcome. The realistic target is fast, low-effort, low-working-memory-cost detection — which is functionally sufficient.

---

