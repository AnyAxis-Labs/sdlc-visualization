# Vibe System Designing

Architecture design workflow for the Vibe system, including validation, synthesis, critique, and implementation planning.

## Level High

```mermaid
graph LR
    P1["Phase 1: PRD Validation"] --> P2["Phase 2: Synthesis"] --> P3["Phase 3: Critique"]
    P3 -.feedback.-> P2
    P3 --> P4["Phase 4: Implementation Plan Mapping"]
    P4 --> P5["Phase 5: Change Request Loop"]
    P5 -.repeat.-> P1
```

---

## Level Mid

```mermaid
graph TB
    subgraph Phase_1
        PRD["prd.md"]
        Gate["Validation (architecture-gatekeeper)"]
        PRD --> Gate
    end

    subgraph Phase_2
        Synthesis["System Design (architecture-synthesis)"]
        State["current_state.md"]
        ADRs["docs/adr/"]
        Diagrams["docs/diagrams/"]
        Synthesis --> State
        Synthesis --> ADRs
        Synthesis --> Diagrams
    end

    subgraph Phase_3
        Critique["Hardening Critique"]
        Resolutions["docs/hardening/00x_resolution.md"]
        Critique --> Resolutions
    end

    subgraph Phase_4
        Plan["Implementation Plan"]
        Map["architecture-to-implementation-mapper"]
        Plan --> Map
    end

    Gate --> Synthesis --> Critique
    Critique -.loop.-> Synthesis
    Critique --> Plan
```

---

## Level Low

```mermaid
graph TB
    subgraph Phase_1_PRD
        PRD["PRD Draft"]
        FR["Functional Requirements"]
        NFR["Non-Functional Targets"]
        Constraints["Constraints + Non-goals"]
        Gate["Gatekeeper Review"]
        Gaps["Requirement Gaps"]
        PRDRev["PRD Corrections"]
        PRD --> FR --> NFR --> Constraints --> Gate --> Gaps --> PRDRev
    end

    subgraph Phase_2_Synthesis
        Context["Context Load"]
        Draft["Synthesis Draft"]
        ADRs["ADR Drafts"]
        C4["C4 Diagrams"]
        Risks["Trade-offs + Consequences"]
        State["Update current_state.md"]
        Context --> Draft --> ADRs --> C4 --> Risks --> State
    end

    subgraph Phase_3_Critique
        Critique["Hardening Critique"]
        Security["Security Review"]
        Perf["Performance Review"]
        Response["Resolution Notes"]
        Fix["Design Updates"]
        Critique --> Security --> Perf --> Response --> Fix
    end

    subgraph Phase_4_Plan
        Plan["Implementation Plan"]
        Map["Task Mapping"]
        Dependencies["Dependency Map"]
        Review["Architecture Review Gate"]
        Plan --> Map --> Dependencies --> Review
    end

    subgraph Phase_5_Change
        CR["Change Request"]
        Impact["Impact Analysis"]
        Decision["Go/No-Go"]
        CR --> Impact --> Decision
    end

    PRDRev --> Context
    State --> Critique
    Fix -.re-synthesize.-> Draft
    Fix --> Plan
    Review --> CR
    Decision --> Gate
```
