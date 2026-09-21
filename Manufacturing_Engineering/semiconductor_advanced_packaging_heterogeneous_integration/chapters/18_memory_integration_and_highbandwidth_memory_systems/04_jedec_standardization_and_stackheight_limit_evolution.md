## JEDEC Standardization and Stack-Height Limit Evolution


### Overview

JEDEC (Joint Electron Device Engineering Council) is the standards body responsible for defining the electrical, mechanical, and interface specifications governing High Bandwidth Memory (HBM). Each HBM generation is codified under the JESD235 family of standards, which define signaling protocols, pinout, command/address structures, and — critically for advanced packaging — the physical package height (z-height) envelope that constrains how many DRAM dies can be stacked and how thick each die and interconnect layer may be. As HBM generations have progressed (HBM, HBM2, HBM2E, HBM3, HBM3E, HBM4), stack-height limits have evolved to accommodate taller stacks (4-high through 16-high) while holding total package height roughly constant, forcing continuous innovation in die thinning, TSV scaling, and interconnect technology (microbump to hybrid bonding).

### JEDEC HBM Standards Family

**Key Points**

- JESD235: original HBM (HBM1) standard
- JESD235A: HBM2 standard
- JESD235B/C: HBM2E refinements (higher per-pin data rates, higher density options)
- JESD238: HBM3 standard
- JESD238A (or successor revisions): HBM3E refinements
- HBM4: standardized under continuing JEDEC working group efforts, with expanded interface width (2048-bit I/O, versus 1024-bit for prior generations) and formalized support for taller stack configurations and custom base die logic

[Unverified] Exact JEDEC document numbers and revision letters for HBM3E and HBM4 continue to be finalized and republished as the standard matures; readers should consult the current JEDEC JESD235/JESD238 document set for the authoritative version number in effect at time of design.

### Stack-Height Limit Evolution

**Historical Progression**

- **HBM (1st gen):** 4-high stack standard, microbump-based TSV interconnect, modest per-die capacity
- **HBM2:** Standardized up to 8-high stacks, still microbump-based, established the TSV-based base-logic-die-plus-DRAM-core architecture that persists across all subsequent generations
- **HBM2E:** Extended 8-high stacking with higher per-pin data rates and increased per-die density, still within microbump-compatible z-height budgets
- **HBM3:** Standardized 8-high and 12-high stack configurations, marking the point where microbump z-height budgets began to strain against the fixed JEDEC package height envelope, motivating early hybrid-bonding pilot production for the tallest configurations
- **HBM3E:** Continued 8-high and 12-high support with higher per-pin speeds; 12-high configurations increasingly adopted hybrid bonding to manage thermal and z-height constraints
- **HBM4:** Roadmapped to support 12-high and 16-high stacks with a doubled interface width (2048-bit), where hybrid bonding transitions from an optional advanced technique to a practically necessary interconnect for the tallest configurations

**Key Points**

- Each JEDEC generation has held total package z-height roughly constant even as stack count has increased, meaning the height budget "spent" per die-to-die interface has had to shrink continuously
- Stack-height increases (4-high → 8-high → 12-high → 16-high) directly drive die-thinning requirements, since more dies must fit within the same or similar total thickness
- JEDEC does not mandate a specific interconnect technology (microbump vs. hybrid bonding) — the standard defines electrical/mechanical envelopes and interface behavior, leaving implementation choice to manufacturers, provided the resulting stack meets signal integrity, timing, and thermal specifications

### Package Height Budget Mechanics

The JEDEC package height envelope for a given HBM generation is a fixed total thickness (encompassing the base logic die, all stacked DRAM core dies, interconnect layers between them, and the cap/mold layer). As stack count increases within a fixed or near-fixed height budget, the available height per interconnect layer must shrink proportionally.

$$H_{total} = H_{base} + \sum_{i=1}^{n} (H_{die,i} + H_{interconnect,i}) + H_{cap}$$

Where $n$ is the stack count (e.g., 8, 12, or 16), $H_{die,i}$ is individual die thickness (post-thinning), and $H_{interconnect,i}$ is the per-layer interconnect height (bump+underfill for microbump, near-zero for hybrid bonding).

**Example**

- At 8-high with microbump interconnect, a die thickness of roughly 30–50 $\mu m$ combined with a ~15–20 $\mu m$ interconnect layer per interface remains within typical JEDEC height budgets for HBM2E/HBM3
- At 12-high, maintaining the same total height budget while adding four more die-interconnect pairs forces either further die thinning (increasing fragility and warpage risk) or a switch to hybrid bonding to reclaim the height otherwise consumed by microbump standoff and underfill
- At 16-high (HBM4 roadmap), [Inference] hybrid bonding is likely to become the default interconnect approach rather than an optional one, since microbump z-height budgets at this stack count would require die thinning beyond practical mechanical handling limits for standard DRAM core die processes

### Stack Height and Interconnect Technology Correlation (Mermaid Diagram)

```mermaid
flowchart LR
    A[HBM1: 4-high] -->|Microbump| B[HBM2: 8-high]
    B -->|Microbump| C[HBM2E: 8-high]
    C -->|Microbump| D[HBM3: 8/12-high]
    D -->|Microbump transitioning to Hybrid Bonding at 12-high| E[HBM3E: 8/12-high]
    E -->|Hybrid Bonding increasingly standard| F[HBM4: 12/16-high]

    style A fill:#a3c9f1
    style B fill:#a3c9f1
    style C fill:#a3c9f1
    style D fill:#f4c05a
    style E fill:#f4c05a
    style F fill:#a3d9a5
```

### JEDEC's Role Beyond Height: Electrical and Thermal Specifications

**Key Points**

- JEDEC standards define per-pin data rate targets for each generation (e.g., HBM3's per-pin data rate exceeds HBM2E's, HBM3E further increases this), which indirectly pressure interconnect technology choice since higher data rates demand lower parasitic interconnects (favoring hybrid bonding's finer pitch and lower capacitance)
- JEDEC defines thermal test methods and reference conditions for HBM stacks, though actual thermal solution design (heat spreaders, TIM selection, system-level cooling) remains the responsibility of the module/package integrator, not JEDEC itself
- JEDEC does not standardize the base-die logic architecture in detail beyond interface compliance, which has left room for HBM4's introduction of customizable base die logic (allowing memory vendors and accelerator vendors to co-design base die functionality) while maintaining interface-level interoperability

### Why Stack Height Matters for System Design

**Key Points**

- Taller stacks (12-high, 16-high) increase per-stack DRAM capacity without increasing the HBM stack's footprint on the interposer or substrate, which is critical since interposer area is a scarce and expensive resource in 2.5D/3D packaging
- Higher stack counts within the same JEDEC-defined footprint directly increase total system memory capacity for a fixed number of HBM sites around a compute die (relevant for AI accelerators with 4, 6, or 8 HBM stacks per package)
- Stack height evolution is therefore not purely a packaging curiosity — it is a primary lever for total addressable memory capacity in AI training/inference accelerators, alongside per-die density scaling

### Standardization Challenges as Stack Height Increases

**Key Points**

- Signal integrity budgets tighten as TSV channel counts and stack heights increase, requiring JEDEC's electrical specifications to account for cumulative channel loss and crosstalk across more layers
- Test and repair standardization becomes more complex at higher stack counts, since a single defective die in a 16-high stack risks a larger yield loss than in a 4-high stack, increasing the importance of standardized TSV redundancy and repair schemes within the JEDEC framework
- [Speculation] Future JEDEC revisions beyond HBM4 may need to formally standardize hybrid-bonding-specific test methods and reliability qualification criteria, given that current qualification methodologies were originally developed around microbump/solder-joint failure modes rather than Cu-Cu diffusion bond failure modes

**Conclusion**

JEDEC's HBM standards have evolved generation over generation to accommodate increasing stack heights (4-high through the 16-high configurations targeted by HBM4) while holding overall package height envelopes roughly constant. This has created continuous downward pressure on per-layer interconnect height, driving the packaging industry's shift from microbump stacking toward hybrid bonding at the tallest stack configurations. JEDEC itself remains interconnect-agnostic, defining electrical and mechanical compliance envelopes rather than mandating a specific bonding technology, leaving implementation choices to manufacturers provided JEDEC's signal integrity, timing, and height specifications are met.

**Related Topics**

- Microbump versus hybrid-bonded memory stacking trade-offs (interconnect technology detail)
- TSV redundancy and repair schemes for tall HBM stacks
- HBM4 custom base die logic and JEDEC interface compliance boundaries
- Die thinning process limits and wafer handling for sub-30 $\mu m$ DRAM core dies
- 2.5D/3D interposer HBM site placement and footprint constraints
- Thermal qualification methods for multi-tier HBM stacks under JEDEC reference conditions
- Signal integrity budgeting across cumulative TSV channel loss in 12-high and 16-high stacks