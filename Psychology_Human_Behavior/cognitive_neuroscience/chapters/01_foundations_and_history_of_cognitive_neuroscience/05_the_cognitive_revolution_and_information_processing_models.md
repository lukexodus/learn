## The Cognitive Revolution and Information Processing Models


### Overview

The cognitive revolution refers to the mid-20th-century shift in psychology away from behaviorism's exclusive focus on observable stimulus-response relationships and toward the scientific study of internal mental representations and processes. Its central theoretical product was the **information processing model** of mind — the framework treating cognition as a sequence of discrete stages in which information is received, encoded, stored, transformed, and retrieved, borrowing vocabulary and formal structure from computer science and information theory. This period supplied the conceptual scaffolding that cognitive neuroscience later mapped onto neural substrates.

### Background: The Behaviorist Context Being Reacted Against

**Key Points**

- Behaviorism (John B. Watson, B.F. Skinner) dominated American psychology from roughly the 1910s through the 1950s, treating the mind as a "black box" that should not be scientifically studied directly — only observable stimuli and responses were considered legitimate objects of study
- Skinner's **radical behaviorism** extended this to complex behaviors including language, proposing that verbal behavior could be fully explained through operant conditioning (reinforcement history) without reference to internal grammatical or representational structures
- The cognitive revolution is best understood not as a single discovery but as the **cumulative failure of behaviorism to account for a growing body of phenomena** — language acquisition, problem-solving, memory capacity limits, perception — that seemed to require positing internal representations and processes

### Catalyzing Developments

**Key Points**

- **Claude Shannon's information theory (1948)**: Provided a formal, quantifiable framework for describing communication as the transmission of information through a channel, introducing concepts (bits, channel capacity, noise, encoding/decoding) that psychologists adapted to describe mental processing of information from the environment
- **Norbert Wiener's cybernetics (1948)**: Introduced the concept of **feedback control** in both mechanical and biological systems, offering a model for self-regulating, goal-directed behavior without requiring a behaviorist stimulus-response account
- **Alan Turing's computational theory (1936) and the digital computer**: Provided the **Turing machine** as an abstract model of computation — a system that manipulates symbols according to formal rules — offering psychology a rigorous, mechanistic vocabulary for describing internal mental operations without appeal to unobservable, unfalsifiable inner experience
- **Noam Chomsky's review of Skinner's *Verbal Behavior* (1959)**: A highly influential critique arguing that language acquisition — particularly children's ability to produce and understand novel, grammatically correct sentences they had never heard before — could not be explained by reinforcement history alone, implying an innate, structured internal grammar (universal grammar). Widely cited as a pivotal moment catalyzing psychology's shift away from strict behaviorism.
- **George Miller's "The Magical Number Seven, Plus or Minus Two" (1956)**: Demonstrated that human short-term memory and absolute judgment show a consistent capacity limit (~7 ± 2 items/chunks), framed explicitly in information-processing terms (channel capacity, chunking as a recoding strategy) — an early, influential example of quantifying a cognitive limitation as if it were a property of an information-processing system
- **The 1956 Dartmouth Conference and early artificial intelligence**: Work by **Allen Newell and Herbert Simon** (e.g., the Logic Theorist, 1956; General Problem Solver, 1957) demonstrated that computer programs could perform tasks resembling human problem-solving, reinforcing the idea that cognition could be studied as a form of computation, implementation-independent of its physical substrate

### The Information Processing Model: Core Structure

**Key Points**

- Cognition is modeled as a **sequence of discrete processing stages**, each transforming an input representation into an output representation, broadly analogous to stages in a computer program: input → encoding → storage → retrieval/transformation → output
- Draws an explicit **computer metaphor of mind**: the brain is treated as (roughly) analogous to computer hardware, and cognitive processes as analogous to software/algorithms running on that hardware — crucially implying that cognitive processes could, in principle, be studied and modeled independently of their neural implementation
- Emphasizes **mental representations** (internal symbolic or structured encodings of information) as legitimate, measurable theoretical constructs, in direct contrast to behaviorism's rejection of unobservable internal states
- Relies heavily on **reaction time (RT) and error rate** as primary experimental dependent measures, under the assumption that the time taken to complete a task reflects the number and duration of underlying discrete processing stages (formalized in methods like Donders' subtractive method and, later, Sternberg's additive factors method)

### Foundational Information-Processing Models

**Key Points**

- **Broadbent's Filter Model of Attention (1958)**: One of the earliest formal information-processing models, proposing that sensory information passes through a capacity-limited "bottleneck," with a selective filter early in processing allowing only attended information through for further (semantic) processing — based on dichotic listening experiments
- **Atkinson-Shiffrin Multi-Store Model of Memory (1968)**: Proposed discrete memory stores — a brief, high-capacity **sensory register**, a limited-capacity, limited-duration **short-term store**, and a durable, high-capacity **long-term store** — with control processes (rehearsal, encoding strategies) governing the transfer of information between stores. This became the dominant memory framework for decades and directly informed later neuroscientific work distinguishing short-term/working memory systems from long-term declarative memory systems (e.g., relevant to interpreting patient H.M.'s dissociations).
- **Sternberg's Additive Factors Method (1969)**: A methodological contribution proposing that if two experimental factors affect reaction time additively (their combined effect equals the sum of their individual effects), they influence separate, serial processing stages; if they interact, they influence a shared stage — providing an inferential tool for identifying the discrete stages posited by information-processing theory purely from behavioral RT data, without any direct physiological measurement

### The Cognitive Revolution's Relationship to Early Cognitive Neuroscience

**Key Points**

- Critically, most cognitive revolution-era models were developed and tested using purely **behavioral** methods (reaction time, accuracy, verbal report); they were largely **agnostic about neural implementation** — Marr's later tri-level framework (1982) explicitly formalized this by separating the *computational* and *algorithmic* levels of analysis from the *implementational* (neural) level, legitimizing cognitive-level theorizing without requiring immediate neural grounding
- The transition from **cognitive psychology** to **cognitive neuroscience** occurred when researchers began asking how these information-processing stages and stores map onto actual neural structures and circuits — driven by converging evidence from lesion studies (e.g., H.M. dissociating short-term from long-term memory stores), split-brain research, and eventually functional neuroimaging
- **[Inference]** The information processing framework's assumption of discrete, serial stages has been substantially revised by later cognitive neuroscience findings showing that many neural processes operate in parallel, are graded rather than discrete, and involve continuous, cascading, or recurrent information flow rather than strictly sequential stages — though the framework's core methodological legacy (positing internal representations, using RT/accuracy to infer processing structure) remains foundational to the field's experimental logic.

### Diagram: Basic Information Processing Sequence

```mermaid
flowchart LR
    A["Environmental Stimulus"] --> B["Sensory Register<br/>(brief, high capacity)"]
    B --> C["Selective Attention<br/>(Broadbent's filter)"]
    C --> D["Short-Term / Working Store<br/>(limited capacity, ~7±2 items)"]
    D --> E["Encoding / Rehearsal"]
    E --> F["Long-Term Store<br/>(durable, high capacity)"]
    F --> G["Retrieval"]
    G --> H["Behavioral Output / Response"]
```

### Diagram: Intellectual Convergence Enabling the Cognitive Revolution

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 900 420" font-family="Helvetica, Arial, sans-serif">
<text x="450" y="28" text-anchor="middle" font-size="17" font-weight="bold" fill="#1a1a1a">Convergent Origins of the Cognitive Revolution (svg_diagram)</text>
<rect x="30" y="60" width="180" height="65" rx="8" fill="#d9e8f4" stroke="#357" />
<text x="120" y="86" text-anchor="middle" font-size="12" font-weight="bold">Information Theory</text>
<text x="120" y="104" text-anchor="middle" font-size="10">Shannon (1948)</text>
<rect x="240" y="60" width="180" height="65" rx="8" fill="#f4d9d9" stroke="#a33" />
<text x="330" y="86" text-anchor="middle" font-size="12" font-weight="bold">Computation Theory</text>
<text x="330" y="104" text-anchor="middle" font-size="10">Turing; Newell &amp; Simon</text>
<rect x="450" y="60" width="180" height="65" rx="8" fill="#d9f4df" stroke="#3a7" />
<text x="540" y="86" text-anchor="middle" font-size="12" font-weight="bold">Cybernetics</text>
<text x="540" y="104" text-anchor="middle" font-size="10">Wiener (1948)</text>
<rect x="660" y="60" width="200" height="65" rx="8" fill="#f4ecd9" stroke="#a83" />
<text x="760" y="86" text-anchor="middle" font-size="12" font-weight="bold">Linguistic Nativism</text>
<text x="760" y="104" text-anchor="middle" font-size="10">Chomsky (1959)</text>
<line x1="120" y1="125" x2="380" y2="220" stroke="#666" stroke-width="1.5" />
<line x1="330" y1="125" x2="400" y2="220" stroke="#666" stroke-width="1.5" />
<line x1="540" y1="125" x2="440" y2="220" stroke="#666" stroke-width="1.5" />
<line x1="760" y1="125" x2="470" y2="220" stroke="#666" stroke-width="1.5" />
<rect x="300" y="220" width="300" height="70" rx="8" fill="#e0d9f4" stroke="#66a" />
<text x="450" y="248" text-anchor="middle" font-size="13" font-weight="bold">Information Processing Model</text>
<text x="450" y="268" text-anchor="middle" font-size="10">Broadbent, Atkinson-Shiffrin, Miller</text>
<line x1="450" y1="290" x2="450" y2="330" stroke="#666" stroke-width="2" marker-end="url(#arrow3)" />
<rect x="330" y="330" width="240" height="65" rx="8" fill="#f4d9ec" stroke="#a37" />
<text x="450" y="358" text-anchor="middle" font-size="12" font-weight="bold">Cognitive Neuroscience</text>
<text x="450" y="376" text-anchor="middle" font-size="10">Neural grounding of processing stages</text>
</svg>

### Example: Applying the Additive Factors Method

Suppose reaction time is measured across a task manipulating **stimulus quality** (clear vs. degraded) and **set size** (number of items to search through):

$$RT = t_{encoding} + t_{search} + t_{response}$$

- If degrading stimulus quality slows RT by a fixed amount **regardless of set size**, and increasing set size slows RT by a fixed amount **regardless of stimulus quality**, their effects are **additive** — implying they affect *separate* serial stages (e.g., encoding vs. search)
- If the two factors **interact** (e.g., stimulus quality matters more at larger set sizes), this implies they affect a **shared** underlying stage

This logic allowed cognitive psychologists to infer the existence and structure of unobservable internal stages purely from behavioral timing data, a methodological approach that predates and is logically independent of neuroimaging.

### Comparative Table: Behaviorism vs. Cognitive Information Processing

| Dimension | Behaviorism | Information Processing / Cognitivism |
| --- | --- | --- |
| Object of study | Observable stimulus-response relationships | Internal mental representations and processes |
| Core method | Conditioning experiments | Reaction time, accuracy, verbal report |
| Model of mind | "Black box" (unstudiable) | Computer-like system with discrete stages |
| Treatment of language | Learned via reinforcement | Structured, partly innate (generative grammar) |
| Relation to neuroscience | Largely irrelevant/unaddressed | Initially agnostic; later actively integrated |

**Related Topics**

- George Miller's working memory capacity findings
- Atkinson-Shiffrin multi-store memory model
- Broadbent's filter theory of attention
- Chomsky's critique of behaviorism and universal grammar
- David Marr's tri-level framework of analysis
- Reaction time methodology (subtractive and additive factors methods)
- Emergence of cognitive neuroscience as a distinct discipline