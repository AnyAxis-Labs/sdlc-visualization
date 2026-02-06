# PERSPECTIVE 3: GOVERNANCE

What moves through the system as artifacts, and who approves each gate.

This version preserves the prior governance perspective (artifact lineage and approvals) while upgrading content to the latest Mermaid definitions from `files/`.

## LEVEL HIGH

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

---

## LEVEL MID

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

---

## LEVEL LOW

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
