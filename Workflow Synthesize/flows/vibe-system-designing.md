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
    PRD["PRD Draft"] --> Validate["Gatekeeper Review"]
    Validate --> S1["Synthesis Draft"]
    S1 --> ADRs["ADRs + C4 Diagrams"]
    ADRs --> Critique["Critique Rounds"]
    Critique --> Fix["Update Design + current_state.md"]
    Fix --> Critique
    Critique --> Plan["Implementation Plan"]
    Plan --> Change["Change Request"]
    Change --> Validate
```
