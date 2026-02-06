# SDLC Complete System - 3 Perspectives x 3 Zoom Levels

This consolidated document combines:

- The existing 3x3 storytelling structure (Work Flow, People and AI, Governance)
- The latest Mermaid logic from the updated `files/` set

If you prefer split documents, use:

- `views/01-work-flow.md`
- `views/02-people-ai.md`
- `views/03-governance.md`

---

## Quick Selector Guide

### By Role

| Your Role | Start With | Then Use | For Details |
|-----------|-----------|----------|-------------|
| CEO/Board | Perspective 1-HIGH | Perspective 3-HIGH | - |
| Product Owner | Perspective 1-MID | Perspective 2-MID | Perspective 3-MID |
| Tech Lead | Perspective 1-MID | Perspective 3-MID | Perspective 1-LOW |
| Dev Lead | Perspective 2-MID | Perspective 1-MID | Perspective 2-LOW |
| Developer | Perspective 1-MID | Perspective 2-MID | Perspective 1-LOW |
| QA Engineer | Perspective 3-MID | Perspective 1-MID | Perspective 3-LOW |
| DevOps | Perspective 1-MID | Perspective 3-MID | Perspective 3-LOW |

### By Question

| Question | Use This |
|----------|----------|
| What's the big picture? | Perspective 1-HIGH |
| What runs in parallel? | Perspective 1-MID |
| Every single step? | Perspective 1-LOW |
| Who do I work with? | Perspective 2-HIGH |
| Who owns what? | Perspective 2-MID |
| Every interaction? | Perspective 2-LOW |
| What gets approved? | Perspective 3-HIGH |
| What artifacts exist? | Perspective 3-MID |
| Complete audit trail? | Perspective 3-LOW |

---

## PERSPECTIVE 1: WORK FLOW

What work happens, when it happens, and where parallelism exists.

### LEVEL HIGH

```mermaid
graph LR
    classDef plan fill:#3B82F6,color:#fff,stroke:#2563EB,stroke-width:2px
    classDef build fill:#F59E0B,color:#000,stroke:#D97706,stroke-width:2px
    classDef ship fill:#10B981,color:#fff,stroke:#059669,stroke-width:2px
    classDef learn fill:#A855F7,color:#fff,stroke:#7C3AED,stroke-width:2px

    P["PLAN\nInitiation + Research + Architecture\nWeeks 1-3"]:::plan
    B["BUILD\nImplementation + Parallel Dev Tracks\nWeeks 3-6"]:::build
    S["SHIP\nQA + Staging + Production\nWeeks 6-7"]:::ship
    L["LEARN\nMonitoring + Retro + Improve\nOngoing"]:::learn

    P ==> B ==> S ==> L
    L -.->|"Next Feature"| P
    S -.->|"Bugs"| B
```

### LEVEL MID

```mermaid
graph TB
    classDef p1 fill:#FFE6E6,stroke:#CC0000,stroke-width:2px
    classDef p2 fill:#E6F3FF,stroke:#0066CC,stroke-width:2px
    classDef p3 fill:#E6FFE6,stroke:#00CC00,stroke-width:2px
    classDef p4 fill:#FFF4E6,stroke:#FF9900,stroke-width:2px
    classDef p5 fill:#FFE6F9,stroke:#CC00CC,stroke-width:2px
    classDef p6 fill:#F0E6FF,stroke:#6600CC,stroke-width:2px
    classDef p7 fill:#E6FFFF,stroke:#00CCCC,stroke-width:2px
    classDef p8 fill:#FFFACD,stroke:#FFD700,stroke-width:2px
    classDef gate fill:#10B981,color:#fff,stroke:#059669,stroke-width:3px

    subgraph PLAN["PLAN"]
        direction LR
        P1["P1 Initiation\nCEO Vision to Charter"]:::p1
        P2["P2 Research\nLibrarian + Oracle + Explore"]:::p2
        P3["P3 Architecture\nPRD + ADRs + C4 + Hardening"]:::p3
        P1 --> P2 --> P3
    end

    subgraph BUILD["BUILD"]
        direction TB
        P4A["P4a Foundation\nInfra + CI/CD + Observability"]:::p4
        P4B["P4b Backend Track"]:::p4
        P4C["P4c Frontend Track"]:::p4
        P4D["P4d Testing Track"]:::p4
        P4E["P4e Integration + Hardening"]:::p4
        P4A --> P4B & P4C & P4D
        P4B & P4C & P4D --> P4E
    end

    subgraph SHIP["SHIP"]
        direction LR
        P5["P5 QA Testing\nUnit + Integration + System"]:::p5
        P6["P6 Deploy\nStaging to Production"]:::p6
        P5 --> P6
    end

    subgraph LEARN["LEARN"]
        direction LR
        P7["P7 Monitor\nDashboards + Incidents"]:::p7
        P8["P8 Retro\nLessons + SOP Updates"]:::p8
        P7 --> P8
    end

    G1{"Gate 1\nCEO + PO"}:::gate
    G2{"Gate 2\nArch Review"}:::gate
    G3{"Gate 3\nQA Signoff"}:::gate
    G4{"Gate 4\nGo/No-Go"}:::gate

    P3 --> G1 --> G2 --> P4A
    P4E --> G3 --> P5
    P6 --> G4 --> P7
    P8 -.->|"Next Feature"| P1
    P5 -.->|"Bugs"| P4B
```

### LEVEL LOW

```mermaid
graph TB
    classDef p1 fill:#FFE6E6,stroke:#CC0000,stroke-width:2px,color:#000
    classDef p2 fill:#E6F3FF,stroke:#0066CC,stroke-width:2px,color:#000
    classDef p3 fill:#E6FFE6,stroke:#00CC00,stroke-width:2px,color:#000
    classDef p4 fill:#FFF4E6,stroke:#FF9900,stroke-width:2px,color:#000
    classDef p5 fill:#FFE6F9,stroke:#CC00CC,stroke-width:2px,color:#000
    classDef p6 fill:#F0E6FF,stroke:#6600CC,stroke-width:2px,color:#000
    classDef p7 fill:#E6FFFF,stroke:#00CCCC,stroke-width:2px,color:#000
    classDef p8 fill:#FFFACD,stroke:#FFD700,stroke-width:2px,color:#000
    classDef gate fill:#10B981,color:#fff,stroke:#059669,stroke-width:3px
    classDef ai fill:#FFD93D,color:#000,stroke:#F4A261,stroke-width:2px

    subgraph PH1["PHASE 1 - INITIATION"]
        I1["CEO Voice Memo via Telegram"]:::p1
        I2["OpenClaw Transcription"]:::p1
        I3["Opus 4.5 Analysis"]:::ai
        I4["Project Charter Draft"]:::p1
        I5["Solution Brief + PRFAQ"]:::p1
        I1 --> I2 --> I3 --> I4
        I3 --> I5
    end

    subgraph PH2["PHASE 2 - RESEARCH"]
        R0["Sisyphus Orchestrates"]:::ai
        R1["Librarian - Doc Search"]:::ai
        R2["Oracle - Architecture"]:::ai
        R3["Explore - Codebase"]:::ai
        R4["Synthesize Findings"]:::p2
        R5["Generate User Stories"]:::p2
        R6["Create GitHub Repo + AGENTS.md"]:::p2
        R7["Create Lark Workspace"]:::p2
        R0 --> R1 & R2 & R3
        R1 & R2 & R3 --> R4 --> R5
        R5 --> R6 & R7
    end

    subgraph PH3["PHASE 3 - ARCHITECTURE"]
        A1["Gatekeeper validates PRD"]:::ai
        A2["Synthesis generates ADRs"]:::ai
        A3["C4 Context + Container + Component"]:::p3
        A4["Hardening 9 stress tests"]:::ai
        A5["Resolve critiques"]:::p3
        A6["Mapper creates Impl Plan"]:::ai
        A7["API contracts defined"]:::p3
        A1 --> A2 --> A3
        A2 --> A4 --> A5 --> A2
        A3 --> A6 --> A7
    end

    subgraph PH4["PHASE 4 - IMPLEMENTATION"]
        subgraph PH4F["Foundation"]
            F1["Infrastructure Provision"]:::p4
            F2["CI/CD Pipeline"]:::p4
            F3["Observability Setup"]:::p4
        end
        subgraph PH4BE["Backend Track"]
            BE1["Auth Module"]:::p4
            BE2["Core Business Logic"]:::p4
            BE3["Data Layer + APIs"]:::p4
        end
        subgraph PH4FE["Frontend Track"]
            FE1["Framework Setup"]:::p4
            FE2["Components"]:::p4
            FE3["Integration"]:::p4
        end
        subgraph PH4T["Testing Track"]
            T1["Unit Tests"]:::p4
            T2["Integration Tests"]:::p4
            T3["Contract Tests"]:::p4
        end
        subgraph PH4I["Integration"]
            INT1["Integrator Agent"]:::ai
            INT2["Load Testing"]:::p4
            INT3["Security Scan"]:::p4
        end
        F1 & F2 & F3 --> BE1 & FE1 & T1
        BE1 --> BE2 --> BE3
        FE1 --> FE2 --> FE3
        T1 --> T2 --> T3
        BE3 & FE3 & T3 --> INT1
        INT1 --> INT2 --> INT3
    end

    subgraph PH5["PHASE 5 - QA"]
        Q1["Test Design Generator"]:::ai
        Q2["Unit Test Execution"]:::p5
        Q3["Integration Test Execution"]:::p5
        Q4["System + E2E Tests"]:::p5
        Q5["Bug Intake Agent"]:::ai
        Q6["CI Triage Agent"]:::ai
        Q7["Evidence Pack Generation"]:::p5
        Q1 --> Q2 --> Q3 --> Q4
        Q4 --> Q7
        Q5 --> Q6
    end

    subgraph PH6["PHASE 6 - DEPLOYMENT"]
        D1["Staging Deploy"]:::p6
        D2["Health Checks"]:::p6
        D3["Rollback Plan Ready"]:::p6
        D4["Production Deploy"]:::p6
        D5["Release Notes Auto-Gen"]:::ai
        D1 --> D2 --> D3 --> D4
        D4 --> D5
    end

    subgraph PH7["PHASE 7 - MONITORING"]
        M1["Error Tracking via Sentry"]:::p7
        M2["AI Severity Classification"]:::ai
        M3["Auto Bug Tickets"]:::ai
        M4["Performance Dashboards"]:::p7
        M5["Heartbeat Checks 15min"]:::p7
        M6["Incident Response"]:::p7
        M1 --> M2 --> M3
        M4 --> M5
        M5 --> M6
    end

    subgraph PH8["PHASE 8 - RETROSPECTIVE"]
        RT1["Collect Feedback"]:::p8
        RT2["Retrospective Agent"]:::ai
        RT3["Update SOPs"]:::p8
        RT4["Archive Skills Learned"]:::p8
        RT5["Roadmap Draft"]:::ai
        RT1 --> RT2 --> RT3 --> RT4
        RT2 --> RT5
    end

    G1{"Gate 1 - CEO + PO Approve"}:::gate
    G2{"Gate 2 - Architecture Review"}:::gate
    G3{"Gate 3 - QA Signoff"}:::gate
    G4{"Gate 4 - Go/No-Go"}:::gate

    I5 --> G1 --> R0
    R7 --> G2 --> A1
    A7 --> F1
    INT3 --> G3 --> Q1
    Q7 --> D1
    D4 --> G4 --> M1
    RT5 -.->|"Next Feature"| I1
    Q5 -.->|"Fix Bugs"| BE2
    M3 -.->|"Hotfix"| BE2
```

---

## PERSPECTIVE 2: PEOPLE AND AI

Who collaborates, how humans and AI agents interact, and where the handoffs occur.

### LEVEL HIGH

```mermaid
graph LR
    classDef exec fill:#FF6B6B,color:#fff,stroke:#DC2626,stroke-width:2px
    classDef prod fill:#4ECDC4,color:#000,stroke:#2BA8A4,stroke-width:2px
    classDef eng fill:#45B7D1,color:#fff,stroke:#2E8DAA,stroke-width:2px
    classDef qa fill:#FCBAD3,color:#000,stroke:#E890B0,stroke-width:2px
    classDef ai fill:#FFD93D,color:#000,stroke:#E6C235,stroke-width:3px
    classDef ops fill:#C5A3FF,color:#000,stroke:#A07FE0,stroke-width:2px

    EX["EXECUTIVES\nCEO + External Clients"]:::exec
    PO["PRODUCT\nPO + Stakeholders"]:::prod
    EN["ENGINEERING\nTech Lead + Dev Team"]:::eng
    QA["QUALITY\nQA + Security"]:::qa
    OP["OPERATIONS\nDevOps + On-Call"]:::ops
    AI["AI AGENTS\nSisyphus + 6 Subagents"]:::ai

    EX ==> PO ==> EN
    EN ==> QA ==> OP
    AI <-.->|"Augments Every Phase"| EN
    AI <-.->|"Research + Test + Monitor"| PO
    OP -.->|"Metrics"| PO
    QA -.->|"Bug Reports"| EN
```

### LEVEL MID

```mermaid
graph TB
    classDef exec fill:#FF6B6B,color:#fff,stroke:#DC2626,stroke-width:2px
    classDef prod fill:#4ECDC4,color:#000,stroke:#2BA8A4,stroke-width:2px
    classDef eng fill:#45B7D1,color:#fff,stroke:#2E8DAA,stroke-width:2px
    classDef qa fill:#FCBAD3,color:#000,stroke:#E890B0,stroke-width:2px
    classDef ai fill:#FFD93D,color:#000,stroke:#E6C235,stroke-width:2px
    classDef ops fill:#C5A3FF,color:#000,stroke:#A07FE0,stroke-width:2px
    classDef gate fill:#10B981,color:#fff,stroke:#059669,stroke-width:3px

    subgraph BIZ["BUSINESS LAYER"]
        CEO["CEO"]:::exec
        CL["External Clients"]:::exec
        PO["Product Owner"]:::prod
        CL --> CEO --> PO
    end

    subgraph TECH["TECHNICAL LAYER"]
        TL["Tech Lead"]:::eng
        DL["Dev Lead"]:::eng
        AR["Arch Reviewer"]:::eng
        PO --> TL
        TL --> DL
        TL --> AR
    end

    subgraph DEV["DEVELOPMENT LAYER"]
        BE1["Backend Dev 1"]:::eng
        BE2["Backend Dev 2"]:::eng
        FE1["Frontend Dev 1"]:::eng
        FE2["Frontend Dev 2"]:::eng
        DL --> BE1 & BE2 & FE1 & FE2
    end

    subgraph QUAL["QUALITY LAYER"]
        QAE["QA Engineer"]:::qa
        SEC["Security"]:::qa
        OPS["DevOps"]:::ops
    end

    subgraph AILAYER["AI AGENT LAYER"]
        SIS["Sisyphus Orchestrator"]:::ai
        LIB["Librarian"]:::ai
        ORA["Oracle"]:::ai
        IMP["Implementer"]:::ai
        TST["Test Engineer"]:::ai
        INTG["Integrator"]:::ai
        RET["Retrospective"]:::ai
    end

    G1{"Gate 1\nScope"}:::gate
    G2{"Gate 2\nDesign"}:::gate
    G3{"Gate 3\nDeploy"}:::gate

    PO --> G1 --> TL
    AR --> G2 --> DL
    QAE --> G3 --> OPS

    SIS <-.-> PO
    SIS --> LIB & ORA & IMP & TST & INTG & RET
    IMP <-.-> BE1 & FE1
    TST <-.-> QAE
    OPS -.->|"Metrics"| PO
    SEC -.->|"Audit"| TL
```

### LEVEL LOW

```mermaid
graph TB
    classDef exec fill:#FF6B6B,color:#fff,stroke:#DC2626,stroke-width:2px
    classDef prod fill:#4ECDC4,color:#000,stroke:#2BA8A4,stroke-width:2px
    classDef eng fill:#45B7D1,color:#fff,stroke:#2E8DAA,stroke-width:2px
    classDef qa fill:#FCBAD3,color:#000,stroke:#E890B0,stroke-width:2px
    classDef ai fill:#FFD93D,color:#000,stroke:#E6C235,stroke-width:2px
    classDef ops fill:#C5A3FF,color:#000,stroke:#A07FE0,stroke-width:2px
    classDef gate fill:#10B981,color:#fff,stroke:#059669,stroke-width:3px

    subgraph EXEC_ZONE["EXECUTIVE ZONE"]
        CL["External Clients"]:::exec
        CEO["CEO"]:::exec
        CHARTER["Charter Approval"]:::exec
        CL -->|"Requirements"| CEO
        CEO -->|"Vision + Budget"| CHARTER
    end

    subgraph PRODUCT_ZONE["PRODUCT ZONE"]
        PO["Product Owner"]:::prod
        PRD["PRD Document"]:::prod
        BACKLOG["Lark Backlog"]:::prod
        METRICS["Metrics - Latency, Accuracy, Cost"]:::prod
        TESTPLAN["Test Plan"]:::prod
        CHARTER --> PO
        PO --> PRD & BACKLOG & TESTPLAN
        METRICS --> PO
    end

    subgraph ENG_ARCH["ARCHITECTURE"]
        SA["System Architect"]:::eng
        ADR["ADRs"]:::eng
        C4["C4 Diagrams"]:::eng
        MSEL["Model Selection Doc"]:::eng
        SA --> ADR & C4 & MSEL
    end

    subgraph ENG_DEV["DEVELOPMENT"]
        DL["Dev Lead"]:::eng
        BE1["Backend Dev 1 - FastAPI"]:::eng
        BE2["Backend Dev 2 - Data Pipelines"]:::eng
        FE1["Frontend Dev 1 - TG Bot"]:::eng
        FE2["Frontend Dev 2 - Web Dashboard"]:::eng
        DL --> BE1 & BE2 & FE1 & FE2
        BE1 <--> FE1
        BE2 <--> FE2
    end

    subgraph ENG_OPS["OPERATIONS"]
        DEVOPS["DevOps Engineer"]:::ops
        DOCKER["Docker + CI/CD"]:::ops
        HEALTH["Health Checks"]:::ops
        DEVOPS --> DOCKER & HEALTH
    end

    subgraph AI_QUERY["AI - QUERY TIME"]
        SIS["Sisyphus Orchestrator - Claude Opus"]:::ai
        IMP["Implementer Agent"]:::ai
        TST["Test Engineer Agent"]:::ai
        INTG["Integrator Agent"]:::ai
        ADV["Adversarial Agent"]:::ai
    end

    subgraph AI_RESEARCH["AI - RESEARCH"]
        LIB["Librarian - Claude Sonnet"]:::ai
        ORA["Oracle - GPT-5.2"]:::ai
        EXP["Explore - Grok Code"]:::ai
    end

    subgraph AI_QA["AI - QUALITY"]
        TDG["Test Design Generator"]:::ai
        BUG["Bug Intake Agent"]:::ai
        CIT["CI Triage Agent"]:::ai
        RET["Retrospective Agent"]:::ai
    end

    subgraph AI_UI["AI - FRONTEND + DESIGN"]
        FEAI["Frontend Engineer - Gemini 3 Pro"]:::ai
        UB["Ultrabrain - Claude Opus"]:::ai
        MM["Multimodal Looker"]:::ai
    end

    subgraph USER_ZONE["END USERS"]
        U1["Dev Team Member"]:::qa
        U2["PO as User"]:::prod
        U3["Researcher"]:::qa
        U4["New Hire"]:::qa
    end

    G1{"G1 Scope"}:::gate
    G2{"G2 Design"}:::gate
    G3{"G3 Deploy"}:::gate
    G4{"G4 Weekly Review"}:::gate

    PO --> G1 --> SA
    SA --> G2 --> DL
    QAE["QA Engineer"]:::qa
    QAE --> G3 --> DEVOPS
    HEALTH --> G4

    SIS --> IMP & TST & INTG & ADV
    SIS --> LIB & ORA & EXP
    SIS --> TDG
    SIS <-.-> PO
    IMP <-.-> BE1
    IMP <-.-> FE1
    TST <-.-> QAE
    ADV <-.-> SA
    BUG --> QAE
    CIT --> DL
    FEAI <-.-> FE2
    UB <-.-> SA

    U1 & U2 & U3 & U4 -.->|"Feedback"| PO
    G4 -.->|"Improve"| PO
    G4 -.->|"Model Tuning"| SA
    RET -.->|"Skills Archive"| SIS
```

---

## PERSPECTIVE 3: GOVERNANCE

What moves through the system as artifacts, and who approves each gate.

### LEVEL HIGH

```mermaid
graph LR
    classDef art fill:#3B82F6,color:#fff,stroke:#2563EB,stroke-width:2px
    classDef gate fill:#10B981,color:#fff,stroke:#059669,stroke-width:3px
    classDef evid fill:#F59E0B,color:#000,stroke:#D97706,stroke-width:2px
    classDef feed fill:#A855F7,color:#fff,stroke:#7C3AED,stroke-width:2px

    IN["INPUT\nVision + Requirements"]:::art
    PLAN["PLANNING ARTIFACTS\nCharter + PRD + ADRs"]:::art
    G1{"GATE\nScope + Design Approval"}:::gate
    CODE["CODE ARTIFACTS\nSource + Tests + Docs"]:::art
    EVID["EVIDENCE\nTest Reports + Metrics"]:::evid
    G2{"GATE\nQA + Deploy Approval"}:::gate
    PROD["PRODUCTION\nLogs + Dashboards"]:::art
    LEARN["LEARNING\nRetro + SOP Updates"]:::feed

    IN ==> PLAN ==> G1 ==> CODE ==> EVID ==> G2 ==> PROD ==> LEARN
    LEARN -.->|"Improve Process"| PLAN
    EVID -.->|"Fix Bugs"| CODE
```

### LEVEL MID

```mermaid
graph TB
    classDef p1 fill:#FFE6E6,stroke:#CC0000,stroke-width:2px,color:#000
    classDef p2 fill:#E6F3FF,stroke:#0066CC,stroke-width:2px,color:#000
    classDef p3 fill:#E6FFE6,stroke:#00CC00,stroke-width:2px,color:#000
    classDef p4 fill:#FFF4E6,stroke:#FF9900,stroke-width:2px,color:#000
    classDef p5 fill:#FFE6F9,stroke:#CC00CC,stroke-width:2px,color:#000
    classDef p6 fill:#F0E6FF,stroke:#6600CC,stroke-width:2px,color:#000
    classDef p7 fill:#E6FFFF,stroke:#00CCCC,stroke-width:2px,color:#000
    classDef p8 fill:#FFFACD,stroke:#FFD700,stroke-width:2px,color:#000
    classDef gate fill:#10B981,color:#fff,stroke:#059669,stroke-width:3px

    subgraph INPUT["INPUT ARTIFACTS"]
        VM["CEO Voice Memo"]:::p1
        CR["Client Requirements"]:::p1
    end

    subgraph PLANNING["PLANNING ARTIFACTS"]
        CH["Project Charter"]:::p1
        SB["Solution Brief"]:::p1
        US["User Stories"]:::p2
        PRD["PRD.md + PRD.json"]:::p3
        ADR["ADRs - Architecture Decisions"]:::p3
        C4D["C4 Diagrams"]:::p3
        IP["Implementation Plan"]:::p3
    end

    subgraph DEVELOPMENT["DEVELOPMENT ARTIFACTS"]
        SC["scratchpad.md - Interface Contract"]:::p4
        SRC["Source Code - Backend + Frontend"]:::p4
        TESTS["Test Suite - Unit + Integration"]:::p4
        API["API Contracts"]:::p4
        BENCH["Benchmarks"]:::p4
    end

    subgraph EVIDENCE["EVIDENCE ARTIFACTS"]
        TR["Test Reports"]:::p5
        COV["Coverage Metrics"]:::p5
        BEP["Bug Evidence Packs"]:::p5
        PROG["Progress.txt - Evidence Log"]:::p5
    end

    subgraph PRODUCTION["PRODUCTION ARTIFACTS"]
        LOGS["Application Logs"]:::p7
        DASH["Metrics Dashboards"]:::p7
        INC["Incident Reports"]:::p7
        SLA["SLA Reports"]:::p7
    end

    subgraph LEARNING["LEARNING ARTIFACTS"]
        LES["Lessons Learned"]:::p8
        SOPU["SOP Updates"]:::p8
        SKILLS["Skills_Learned.md"]:::p8
        ROAD["Roadmap Draft"]:::p8
    end

    G1{"Gate 1\nCEO + PO"}:::gate
    G2{"Gate 2\nArch Review"}:::gate
    G3{"Gate 3\nQA Signoff"}:::gate
    G4{"Gate 4\nGo/No-Go"}:::gate
    G5{"Gate 5\nWeekly Review"}:::gate

    VM & CR --> CH & SB
    CH --> G1
    G1 --> US --> PRD
    PRD --> ADR & C4D
    ADR --> G2
    G2 --> IP --> SC --> SRC
    SRC --> TESTS --> API
    TESTS --> TR & COV
    TR --> G3
    G3 --> BEP
    BENCH --> G4
    G4 --> LOGS & DASH
    LOGS --> INC --> SLA
    SLA --> G5
    G5 --> LES --> SOPU & SKILLS
    SOPU -.->|"Improve"| CH
    BEP -.->|"Fix"| SRC
    ROAD -.->|"Next Feature"| VM
```

### LEVEL LOW

```mermaid
graph TB
    classDef p1 fill:#FFE6E6,stroke:#CC0000,stroke-width:2px,color:#000
    classDef p2 fill:#E6F3FF,stroke:#0066CC,stroke-width:2px,color:#000
    classDef p3 fill:#E6FFE6,stroke:#00CC00,stroke-width:2px,color:#000
    classDef p4 fill:#FFF4E6,stroke:#FF9900,stroke-width:2px,color:#000
    classDef p5 fill:#FFE6F9,stroke:#CC00CC,stroke-width:2px,color:#000
    classDef p6 fill:#F0E6FF,stroke:#6600CC,stroke-width:2px,color:#000
    classDef p7 fill:#E6FFFF,stroke:#00CCCC,stroke-width:2px,color:#000
    classDef p8 fill:#FFFACD,stroke:#FFD700,stroke-width:2px,color:#000
    classDef gate fill:#10B981,color:#fff,stroke:#059669,stroke-width:3px
    classDef wg fill:#1E293B,color:#94A3B8,stroke:#334155

    subgraph INP["INPUT"]
        VM["CEO Voice Memo"]:::p1
        CR["Client Feature Requests"]:::p1
        TG["Telegram Messages"]:::p1
    end

    subgraph PH1_ART["PHASE 1 ARTIFACTS"]
        TRANS["OpenClaw Transcription"]:::p1
        OPUS["Opus 4.5 Analysis Output"]:::p1
        CH1["Project Charter v1"]:::p1
        CH2["Project Charter v2 after review"]:::p1
        SB["Solution Brief"]:::p1
        PRFAQ["PRFAQ Draft"]:::p1
    end

    subgraph PH2_ART["PHASE 2 ARTIFACTS"]
        LREP["Librarian Research Report"]:::p2
        OANL["Oracle Architecture Analysis"]:::p2
        EFND["Codebase Analysis Findings"]:::p2
        SYNTH["Synthesized Research"]:::p2
        US["User Stories"]:::p2
        GHREPO["GitHub Repo + AGENTS.md"]:::p2
        LARK["Lark Workspace + Templates"]:::p2
    end

    subgraph PH3_ART["PHASE 3 ARTIFACTS"]
        subgraph ADR_GRP["ADR Documents"]
            ADR1["ADR-001"]:::p3
            ADR2["ADR-002"]:::p3
            ADRN["ADR-00N"]:::p3
        end
        subgraph C4_GRP["C4 Diagrams"]
            C4X["C4 Context"]:::p3
            C4CO["C4 Container"]:::p3
            C4CP["C4 Component"]:::p3
        end
        PRDMD["PRD.md"]:::p3
        PRDJ["PRD.json with acceptance tests"]:::p3
        CS1["current_state.md v1"]:::p3
        HARD["Hardening Critiques"]:::p3
        CS2["current_state.md v2"]:::p3
        IMP["Implementation Plan"]:::p3
    end

    subgraph PH4_ART["PHASE 4 ARTIFACTS"]
        subgraph CONTRACT["Interface Contract"]
            SCRATCH["scratchpad.md"]:::p4
            SIGNED["SIGNED by Impl + Tester"]:::p4
        end
        subgraph CODE_GRP["Source Code"]
            BEC["Backend Code - FastAPI"]:::p4
            FEC["Frontend Code"]:::p4
            APIC["API Contracts"]:::p4
        end
        subgraph TEST_GRP["Test Suite"]
            UT["Unit Tests"]:::p4
            IT["Integration Tests"]:::p4
            ET["E2E Tests"]:::p4
        end
        BENCH["Benchmarks"]:::p4
        PROG1["Progress.txt per task"]:::p4
    end

    subgraph PH5_ART["PHASE 5 ARTIFACTS"]
        subgraph REPORTS["Test Reports"]
            UTR["Unit Test Report"]:::p5
            ITR["Integration Report"]:::p5
            STR["System Test Report"]:::p5
        end
        subgraph BUGS["Bug Evidence"]
            BEP["Bug Evidence Packs"]:::p5
            COV["Coverage Metrics"]:::p5
            PERF["Performance Baseline"]:::p5
        end
    end

    subgraph PH6_ART["PHASE 6 ARTIFACTS"]
        RUNBOOK["Deployment Runbook"]:::p6
        ROLLBACK["Rollback Procedure"]:::p6
        RNOTES["Release Notes auto-gen"]:::p6
        HCHECK["Health Check Results"]:::p6
    end

    subgraph PH7_ART["PHASE 7 ARTIFACTS"]
        subgraph LOGS_GRP["Logs and Metrics"]
            APPLOG["Application Logs"]:::p7
            ERRLOG["Error Tracking via Sentry"]:::p7
            MDASH["Metrics Dashboard"]:::p7
        end
        subgraph INC_GRP["Incidents"]
            IR["Incident Reports"]:::p7
            PM["Post-Mortems"]:::p7
            SLA["SLA Compliance Reports"]:::p7
        end
    end

    subgraph PH8_ART["PHASE 8 ARTIFACTS"]
        LES["Lessons Learned Doc"]:::p8
        SOPU["SOP Updates"]:::p8
        SKILLS["Skills_Learned.md"]:::p8
        EFFLOG["Efficiency_Log.md"]:::p8
        RETROLOG["Retrospective_Log.md"]:::p8
        ROAD["AI Roadmap Draft"]:::p8
    end

    subgraph WGRAPH["WORKGRAPH SYSTEM"]
        WGJ["WorkGraph.json - task graph"]:::wg
        WGLOCK["Lock per agent"]:::wg
        WGPROG["progress_summary.md - RAM"]:::wg
        WGARCH["archive - cold storage"]:::wg
    end

    G1{"G1 CEO + PO"}:::gate
    G2{"G2 Arch Review"}:::gate
    G3{"G3 QA Signoff"}:::gate
    G4{"G4 Go/No-Go"}:::gate
    G5{"G5 Weekly SLA"}:::gate

    VM & CR & TG --> TRANS --> OPUS --> CH1 --> CH2
    CH2 --> SB & PRFAQ
    SB --> G1

    G1 --> LREP & OANL & EFND
    LREP & OANL & EFND --> SYNTH --> US
    US --> GHREPO & LARK
    GHREPO --> G2

    G2 --> PRDMD & PRDJ
    PRDMD --> ADR1 & ADR2 & ADRN
    PRDMD --> C4X --> C4CO --> C4CP
    ADR1 --> CS1 --> HARD --> CS2 --> IMP

    IMP --> SCRATCH --> SIGNED
    SIGNED --> BEC & FEC & APIC
    BEC --> UT
    FEC --> IT
    APIC --> ET
    UT & IT & ET --> BENCH

    BENCH --> G3
    G3 --> UTR & ITR & STR
    UTR & ITR & STR --> BEP & COV & PERF

    COV --> RUNBOOK --> ROLLBACK
    RUNBOOK --> RNOTES
    ROLLBACK --> G4
    G4 --> HCHECK

    HCHECK --> APPLOG & ERRLOG & MDASH
    ERRLOG --> IR --> PM --> SLA
    SLA --> G5

    G5 --> LES --> SOPU & SKILLS & EFFLOG & RETROLOG
    LES --> ROAD

    ROAD -.->|"Next Feature"| VM
    BEP -.->|"Fix Bugs"| BEC
    IR -.->|"Hotfix"| BEC
    SOPU -.->|"Improve Process"| PRDMD
    ADR1 -.->|"Referenced by"| BEC
    US -.->|"Traced to"| ET
    PRDJ -.->|"Verified against"| STR
    WGJ -.->|"Tracks"| PROG1
```

---

Test Mermaid locally: https://mermaid.live
