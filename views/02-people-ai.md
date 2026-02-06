# PERSPECTIVE 2: PEOPLE AND AI

Who collaborates, how humans and AI agents interact, and where the handoffs occur.

This version merges the prior operating-model narrative with the latest role and agent definitions from `files/`.

## LEVEL HIGH

```mermaid
graph LR
    classDef exec fill:#FF6B6B,color:#fff,stroke:#DC2626,stroke-width:2px
    classDef prod fill:#4ECDC4,color:#000,stroke:#2BA8A4,stroke-width:2px
    classDef eng fill:#45B7D1,color:#fff,stroke:#2E8DAA,stroke-width:2px
    classDef qa fill:#FCBAD3,color:#000,stroke:#E890B0,stroke-width:2px
    classDef ai fill:#FFD93D,color:#000,stroke:#E6C235,stroke-width:3px
    classDef ops fill:#C5A3FF,color:#000,stroke:#A07FE0,stroke-width:2px

    EX["EXECUTIVES<br/>CEO + External Clients"]:::exec
    PO["PRODUCT<br/>PO + Stakeholders"]:::prod
    EN["ENGINEERING<br/>Tech Lead + Dev Team"]:::eng
    QA["QUALITY<br/>QA + Security"]:::qa
    OP["OPERATIONS<br/>DevOps + On-Call"]:::ops
    AI["AI AGENTS<br/>Sisyphus + 6 Subagents"]:::ai

    EX ==> PO ==> EN
    EN ==> QA ==> OP
    AI <-.->|"Augments Every Phase"| EN
    AI <-.->|"Research + Test + Monitor"| PO
    OP -.->|"Metrics"| PO
    QA -.->|"Bug Reports"| EN
```

---

## LEVEL MID

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

    G1{"Gate 1<br/>Scope"}:::gate
    G2{"Gate 2<br/>Design"}:::gate
    G3{"Gate 3<br/>Deploy"}:::gate

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

---

## LEVEL LOW

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
