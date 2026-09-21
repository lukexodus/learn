## The Kanban Method in Knowledge Work Versus Manufacturing Kanban


### Overview

The term "kanban" refers to two related but distinct things that are frequently conflated: (1) **manufacturing kanban**, the physical or electronic pull-signal system developed within TPS by Taiichi Ohno to control production and inventory replenishment, and (2) **the Kanban Method**, a formalized management framework for knowledge work (particularly software and IT) developed primarily by David J. Anderson in the mid-to-late 2000s and codified in his 2010 book *Kanban: Successful Evolutionary Change for Your Technology Business*. While the Kanban Method borrows its visual board and pull-system vocabulary directly from manufacturing kanban, it is a substantially reinterpreted and more broadly scoped management approach, not merely manufacturing kanban relabeled for office use.

### Manufacturing Kanban: Core Mechanics

**Key Points**

- Manufacturing kanban is a specific, narrowly scoped pull-signal mechanism: a card, bin, or electronic signal that authorizes replenishment of a specific part or component only when downstream consumption actually occurs, preventing upstream overproduction and limiting work-in-process inventory to a deliberately constrained level.
- Operates within an already-defined, stable production process — kanban does not itself define *how* work is done (that is standardized work's function); it governs *when* and *how much* replenishment occurs within an existing process structure.
- Typically involves specific, well-defined kanban card types (production kanban, withdrawal/conveyance kanban) with precise rules governing card circulation, card quantity calculation (tied to lead time, demand rate, and safety stock considerations), and physical or visual signal placement.
- Designed for environments with relatively stable, repeatable part numbers and demand patterns, where the same "thing" (a specific component) is repeatedly replenished in a predictable pattern.

### The Kanban Method: Core Mechanics

**Key Points**

- The Kanban Method visualizes the flow of *work items* (tasks, features, tickets, stories) through a workflow represented as columns on a board, rather than physical parts through a production process — the "product" being tracked is typically a unique piece of knowledge work rather than an identical, repeatable manufactured part.
- Anderson's Kanban Method is explicitly framed as an evolutionary change management approach rather than a prescriptive process redesign: it is commonly summarized through its foundational principles (start with what you do now; agree to pursue incremental, evolutionary change; initially respect current roles, responsibilities, and job titles) and its core practices (visualize the workflow; limit work in progress; manage flow; make process policies explicit; implement feedback loops; improve collaboratively, evolve experimentally).
- Unlike manufacturing kanban's narrow replenishment-signal function, the Kanban Method encompasses a broader management system including explicit workflow policies, classes of service (different handling rules for different urgency/risk categories of work), and structured feedback/review cadences (e.g., Anderson's later-formalized STATIK — Systems Thinking Approach to Introducing Kanban — for initial rollout, and various cadenced review meetings).

```mermaid
flowchart TD
    subgraph Manufacturing Kanban
    A1[Downstream Consumption Occurs] --> A2[Kanban Card/Signal Released]
    A2 --> A3[Upstream Process Replenishes Exact Quantity Consumed]
    A3 --> A1
    end

    subgraph Kanban Method for Knowledge Work
    B1[Work Item Enters Backlog] --> B2["Column: In Progress (WIP Limit Enforced)"]
    B2 --> B3["Column: Review (WIP Limit Enforced)"]
    B3 --> B4["Column: Done"]
    B4 --> B5[Cycle Time and Flow Metrics Tracked]
    B5 --> B6[Collaborative, Evolutionary Process Improvement]
    end
```

### Key Structural Differences

| Dimension | Manufacturing Kanban | Kanban Method (Knowledge Work) |
| --- | --- | --- |
| What flows through the system | Physical parts/components, typically repeatable and identical | Unique work items (features, tasks, tickets), typically non-identical |
| Primary function | Replenishment signal within an existing stable process | Broader workflow visualization, WIP limiting, and evolutionary process management system |
| Process definition scope | Assumes an already-defined production process; governs replenishment timing only | Often used to visualize and gradually improve an evolving, sometimes previously undocumented workflow |
| Demand predictability assumption | Generally assumes relatively stable, repeatable demand patterns | Explicitly designed to accommodate variable, less predictable knowledge-work demand |
| Card/signal quantity calculation | Precisely calculated based on lead time, demand rate, and safety stock formulas | WIP limits typically set empirically/experimentally per column, refined over time based on observed flow data |
| Change management philosophy | Embedded within TPS's broader standardized-work and kaizen culture | Explicitly framed as an evolutionary, low-resistance change approach that starts from current process rather than mandating redesign |

### Classes of Service: A Kanban Method-Specific Extension

- The Kanban Method introduces Classes of Service — different handling policies for different categories of work based on urgency and cost-of-delay characteristics (commonly: Standard, Expedite, Fixed Date, Intangible) — a concept without a direct equivalent in classic manufacturing kanban, which generally assumes relatively uniform handling priority for a given part number's replenishment signal.
- [Inference] Classes of Service reflect knowledge work's typically much higher variability in urgency and risk profile across different work items compared to manufacturing's more uniform part-level replenishment needs, representing one of the more clearly identifiable Kanban Method innovations built specifically to address a knowledge-work-specific problem rather than a direct import from manufacturing practice.

### Flow Metrics: Cycle Time, Lead Time, and Cumulative Flow Diagrams

- The Kanban Method places heavy emphasis on empirical flow metrics — cycle time (time a work item spends actively being worked, from start to finish) and lead time (total time from request to delivery, including queue time) — tracked and used to forecast future delivery timing probabilistically, a more overtly statistical/data-driven approach than classic manufacturing kanban's card-count-based replenishment logic.
- Cumulative Flow Diagrams (CFDs), which visualize the accumulation of work items in each workflow stage over time, are a Kanban Method-specific analytical tool without a direct manufacturing kanban equivalent, used to identify bottlenecks (widening bands in the diagram indicate accumulating WIP at a specific stage) and to monitor whether WIP limits are being effectively maintained.

### WIP Limits: Shared Principle, Different Calculation Approach

**Key Points**

- Both systems share the underlying principle that limiting work-in-process prevents overproduction-equivalent waste and improves overall flow — this is the most directly shared conceptual core between manufacturing kanban and the Kanban Method.
- Manufacturing kanban's WIP limit is implicit in the total number of kanban cards in circulation for a given part, typically calculated using a formula incorporating replenishment lead time, average demand rate, and a safety factor.
- Kanban Method WIP limits are typically set per workflow column (e.g., "no more than 3 items In Progress") and are commonly determined more empirically — starting with an initial estimate and adjusting based on observed flow performance — reflecting the more variable, less precisely quantifiable nature of knowledge-work item size and duration compared to manufacturing part replenishment cycles.

### Relationship to Scrum and Other Frameworks

- Unlike Scrum, which prescribes fixed-length Sprints and specific roles (Product Owner, Scrum Master), the Kanban Method does not mandate fixed iterations or specific roles, instead supporting continuous flow with work pulled individually as capacity allows — this makes it comparatively more flexible to layer onto an existing team structure without requiring the more substantial role and cadence changes Scrum adoption typically involves.
- "Scrumban" is a commonly referenced hybrid approach blending Scrum's cadences (sprint planning, retrospectives) with Kanban Method's continuous-flow visualization and WIP limits, though [Inference] Scrumban is not a formally trademarked or singularly standardized framework in the way Scrum and the Kanban Method each have more defined originating sources, and specific Scrumban implementations vary across organizations.

### Common Points of Confusion

**Key Points**

- **Assuming "using a kanban board" means practicing manufacturing kanban principles.** Many software teams that adopt a visual board with columns do not necessarily implement WIP limits, flow metrics, or the Kanban Method's broader evolutionary change principles — visualizing work alone, without WIP limits actively enforced, captures only a fraction of either system's actual waste-reduction benefit.
- **Treating the Kanban Method as simply "manufacturing kanban for software."** As detailed above, the Kanban Method's Classes of Service, empirical flow-metric-driven WIP limit tuning, and evolutionary change management philosophy represent substantial original contributions beyond a direct transplant of manufacturing kanban mechanics, reflecting knowledge work's fundamentally different variability and process-maturity starting conditions.
- **Conflating the Kanban Method with Agile/Scrum broadly.** Because Kanban boards are also commonly used within Scrum teams and other Agile contexts, practitioners sometimes treat "Kanban" as simply a visualization tool within Agile rather than recognizing the Kanban Method as a distinct management framework with its own originating philosophy, principles, and practices independent of the Agile Manifesto.

### Related Topics

- David J. Anderson's Kanban Method: full principle and practice set
- STATIK (Systems Thinking Approach to Introducing Kanban) rollout methodology
- Classes of Service and cost-of-delay-based work prioritization
- Cumulative Flow Diagrams: construction and bottleneck interpretation
- Cycle time and lead time forecasting using Monte Carlo simulation
- Scrumban: blending Scrum cadences with Kanban Method flow practices
- CONWIP systems as a manufacturing-adjacent bridge between the two kanban traditions
- WIP limit calculation methods: manufacturing formula-based vs. knowledge-work empirical tuning