# SDLC Complete System - 3 Perspectives × 3 Zoom Levels

## System Overview

**3 Perspectives** (different angles):
1. **WORK FLOW** - What work happens + when + parallelism
2. **PEOPLE & AI** - Who collaborates + human-AI interaction
3. **GOVERNANCE** - What moves + who approves

**3 Zoom Levels** (same perspective, different detail):
- **HIGH** - 4-8 components (executives, 30 sec)
- **MID** - 15-25 components (managers, 5 min)
- **LOW** - 40+ components (practitioners, 20 min)

**Total: 9 diagrams**

---

# PERSPECTIVE 1: WORK FLOW

## 🔭 LEVEL HIGH (4 components)

```mermaid
graph LR
    Plan["📋 PLAN<br/><br/>Vision → Design<br/>Weeks 1-2"]
    Build["🔨 BUILD<br/><br/>Code + Tests<br/>Weeks 3-6"]
    Ship["🚀 SHIP<br/><br/>QA → Production<br/>Week 7"]
    Learn["📈 LEARN<br/><br/>Monitor → Improve<br/>Ongoing"]
    
    Plan ==> Build ==> Ship ==> Learn
    Learn -.Feedback.-> Plan
    
    style Plan fill:#4ECDC4,stroke:#00A896,stroke-width:6px
    style Build fill:#FFD93D,stroke:#F4A261,stroke-width:6px
    style Ship fill:#95E1D3,stroke:#38B000,stroke-width:6px
    style Learn fill:#AA96DA,stroke:#6A4C93,stroke-width:6px
```

---

## 🔬 LEVEL MID (16 components)

```mermaid
graph TB
    subgraph "PLAN"
        direction LR
        P1[1. Initiation]
        P2[2. Research]
        P3[3. Architecture]
        P1 --> P2 --> P3
    end
    
    subgraph "BUILD"
        direction TB
        B1[4a. Foundation]
        
        subgraph "Parallel Tracks"
            direction LR
            B2[4b. Backend]
            B3[4c. Frontend]
            B4[4d. Testing]
        end
        
        B5[4e. Integration]
        
        B1 --> B2
        B1 --> B3
        B1 --> B4
        B2 --> B5
        B3 --> B5
        B4 --> B5
    end
    
    subgraph "SHIP"
        direction LR
        S1[5. QA]
        S2[6. Deploy]
        S1 --> S2
    end
    
    subgraph "LEARN"
        direction LR
        L1[7. Monitor]
        L2[8. Retro]
        L1 --> L2
    end
    
    P3 ==> B1
    B5 ==> S1
    S2 ==> L1
    L2 -.Feedback.-> P1
    S1 -.Bugs.-> B2
    S1 -.Bugs.-> B3
    
    style P1 fill:#E6F3FF
    style B2 fill:#FFF4E6
    style B3 fill:#FFE6F9
    style S1 fill:#E6FFE6
```

---

## 🔍 LEVEL LOW (50+ components)

```mermaid
graph TB
    Start([🎬 Project Kickoff])
    
    subgraph P1["━━━ PHASE 1: INITIATION ━━━"]
        direction TB
        I1[CEO Vision Input<br/>Voice Memo/Telegram]
        I2[OpenClaw<br/>Transcription]
        I3[Opus 4.5<br/>Analysis]
        I4[Generate<br/>Project Charter]
        I5{CEO + PO<br/>Approve?}
        
        I1 --> I2 --> I3 --> I4 --> I5
        I5 -->|No - Revise| I4
    end
    
    subgraph P2["━━━ PHASE 2: RESEARCH & PLANNING ━━━"]
        direction TB
        R1[Sisyphus<br/>Orchestrates]
        
        subgraph R_Agents["AI Research Agents"]
            R2[Librarian<br/>Doc Search]
            R3[Oracle<br/>Analysis]
            R4[Explore<br/>Codebase]
        end
        
        R5[Synthesize<br/>Findings]
        R6[Generate<br/>User Stories]
        R7[Create Artifacts:<br/>GitHub + Lark]
        R8{Dev Lead + PO<br/>Approve?}
        
        R1 --> R2
        R1 --> R3
        R1 --> R4
        R2 --> R5
        R3 --> R5
        R4 --> R5
        R5 --> R6
        R6 --> R7
        R7 --> R8
        R8 -->|No - Refine| R5
    end
    
    subgraph P3["━━━ PHASE 3: ARCHITECTURE ━━━"]
        direction TB
        A1[Gatekeeper<br/>Validate PRD]
        A2[Synthesis<br/>Generate ADRs + C4]
        A3[Hardening<br/>9 Stress Tests]
        A4{Critical<br/>Issues?}
        A5[Mapper<br/>Create Impl Plan]
        A6{Architecture<br/>Review Approve?}
        
        A1 --> A2 --> A3 --> A4
        A4 -->|Yes - Fix| A2
        A4 -->|No| A5 --> A6
        A6 -->|No - Redesign| A2
    end
    
    subgraph P4["━━━ PHASE 4: IMPLEMENTATION ━━━"]
        direction TB
        
        subgraph P4_Foundation["4a. Foundation Layer"]
            F1[Infrastructure<br/>Provision]
            F2[CI/CD<br/>Setup]
            F3[Observability<br/>Configure]
            F1 --- F2 --- F3
        end
        
        subgraph P4_Parallel["4b. Parallel Development Tracks"]
            direction LR
            
            subgraph P4_Backend["Backend Track"]
                BE1[Module 1:<br/>Auth]
                BE2[Module 2:<br/>Core Logic]
                BE3[Module 3:<br/>Data Layer]
                BE1 --> BE2 --> BE3
            end
            
            subgraph P4_Frontend["Frontend Track"]
                FE1[Framework<br/>Setup]
                FE2[Component<br/>Library]
                FE3[Page<br/>Integration]
                FE1 --> FE2 --> FE3
            end
            
            subgraph P4_Testing["Testing Track"]
                T1[Unit<br/>Tests]
                T2[Integration<br/>Tests]
                T3[Contract<br/>Tests]
                T1 --> T2 --> T3
            end
        end
        
        subgraph P4_Integration["4c. Integration & Hardening"]
            INT1[Integrator Agent<br/>E2E Wiring]
            INT2[Load Testing]
            INT3[Security Scan]
            INT1 --> INT2 --> INT3
        end
        
        F3 --> BE1
        F3 --> FE1
        F3 --> T1
        BE3 --> INT1
        FE3 --> INT1
        T3 --> INT1
    end
    
    subgraph P5["━━━ PHASE 5: QA TESTING ━━━"]
        direction TB
        
        subgraph P5_Generation["Test Generation"]
            Q1[Test Design Agent<br/>Generate Cases]
            Q2[Bug Intake Agent<br/>Evidence Packs]
        end
        
        subgraph P5_Execution["Test Execution"]
            Q3[Unit Test<br/>Execution]
            Q4[Integration Test<br/>Execution]
            Q5[System Test<br/>Execution]
            Q6[E2E Test<br/>Execution]
            Q3 --> Q4 --> Q5 --> Q6
        end
        
        subgraph P5_Validation["Validation"]
            Q7[CI Triage Agent<br/>Analyze Failures]
            Q8{Critical<br/>Bugs Found?}
            Q9{QA Engineer<br/>Sign Off?}
            Q7 --> Q8 --> Q9
        end
        
        Q1 --> Q3
        Q6 --> Q7
        Q8 -->|Yes - Create Evidence| Q2
        Q9 -->|No - Fix Required| Q2
    end
    
    subgraph P6["━━━ PHASE 6: DEPLOYMENT ━━━"]
        direction TB
        
        subgraph P6_Staging["Staging Environment"]
            D1[Build<br/>Staging]
            D2[Deploy<br/>Staging]
            D3[Validation<br/>Tests]
            D1 --> D2 --> D3
        end
        
        subgraph P6_Decision["Go/No-Go"]
            D4[Risk<br/>Assessment]
            D5{PO + DevOps<br/>Approve Deploy?}
            D4 --> D5
        end
        
        subgraph P6_Production["Production Environment"]
            D6[Deploy<br/>Production]
            D7[Health<br/>Checks]
            D8{All Systems<br/>Green?}
            D6 --> D7 --> D8
        end
        
        D3 --> D4
        D5 -->|Go| D6
        D5 -->|No-Go - Fix| Q1
        D8 -->|No - Rollback| D1
    end
    
    subgraph P7["━━━ PHASE 7: MONITORING ━━━"]
        direction TB
        
        subgraph P7_Observability["Observability Stack"]
            M1[Sentry<br/>Error Tracking]
            M2[Datadog<br/>Metrics]
            M3[ELK<br/>Log Aggregation]
        end
        
        subgraph P7_Response["Incident Response"]
            M4[Incident Sentinel<br/>Alert Routing]
            M5{Critical<br/>Incident?}
            M6[Auto-Alert<br/>On-Call]
            M7[Hotfix<br/>Workflow]
            M4 --> M5
            M5 -->|Yes| M6 --> M7
        end
        
        subgraph P7_Review["Weekly Review"]
            M8[SLA<br/>Tracking]
            M9{Performance<br/>Acceptable?}
            M8 --> M9
        end
        
        M1 --> M4
        M2 --> M4
        M3 --> M4
        M5 -->|No| M8
        M7 --> BE1
    end
    
    subgraph P8["━━━ PHASE 8: RETROSPECTIVE ━━━"]
        direction TB
        
        subgraph P8_Collection["Feedback Collection"]
            RT1[Retrospective Agent<br/>Gathers Input]
            RT2[Analyze<br/>What Worked]
            RT3[Analyze<br/>What Failed]
            RT1 --> RT2
            RT1 --> RT3
        end
        
        subgraph P8_Documentation["Documentation"]
            RT4[Lessons<br/>Learned Doc]
            RT5[Update<br/>SOPs]
            RT6[Archive<br/>Skills]
            RT2 --> RT4
            RT3 --> RT4
            RT4 --> RT5
            RT4 --> RT6
        end
        
        subgraph P8_Closure["Closure"]
            RT7{Cycle<br/>Complete?}
            RT7 -->|Yes - Next Feature| Start
        end
        
        RT6 --> RT7
    end
    
    %% Cross-phase flows
    Start --> I1
    I5 -->|Yes - Approved| R1
    R8 -->|Yes - Approved| A1
    A6 -->|Yes - Approved| F1
    INT3 --> Q1
    Q9 -->|Yes - Approved| D1
    D8 -->|Yes - Stable| M1
    M9 -->|Yes - Healthy| RT1
    
    %% Feedback loops
    Q2 -.Bug Fix.-> BE1
    Q2 -.Bug Fix.-> FE1
    
    %% Gate styling
    style I5 fill:#90EE90,stroke:#00AA00,stroke-width:3px
    style R8 fill:#90EE90,stroke:#00AA00,stroke-width:3px
    style A6 fill:#90EE90,stroke:#00AA00,stroke-width:3px
    style Q9 fill:#90EE90,stroke:#00AA00,stroke-width:3px
    style D5 fill:#90EE90,stroke:#00AA00,stroke-width:3px
    style D8 fill:#90EE90,stroke:#00AA00,stroke-width:3px
    style M9 fill:#90EE90,stroke:#00AA00,stroke-width:3px
    style RT7 fill:#90EE90,stroke:#00AA00,stroke-width:3px
    
    %% Phase styling
    style P1 fill:#FFE6E6,stroke:#CC0000,stroke-width:3px
    style P2 fill:#E6F3FF,stroke:#0066CC,stroke-width:3px
    style P3 fill:#E6FFE6,stroke:#00AA00,stroke-width:3px
    style P4 fill:#FFF4E6,stroke:#FF9900,stroke-width:3px
    style P5 fill:#FFE6F9,stroke:#CC00CC,stroke-width:3px
    style P6 fill:#F0E6FF,stroke:#6600CC,stroke-width:3px
    style P7 fill:#E6FFFF,stroke:#00CCCC,stroke-width:3px
    style P8 fill:#FFFACD,stroke:#FFD700,stroke-width:3px
```

---

# PERSPECTIVE 2: PEOPLE & AI

## 🔭 LEVEL HIGH (6 components)

```mermaid
graph TB
    Business["🎯 BUSINESS<br/>CEO + PO"]
    Technical["⚙️ TECHNICAL<br/>Tech + Dev Lead"]
    Execution["💻 EXECUTION<br/>Devs"]
    Quality["✅ QUALITY<br/>QA + DevOps"]
    AI["🤖 AI<br/>Sisyphus + Agents"]
    
    Business --> Technical --> Execution --> Quality
    AI -.Assists.-> Business
    AI -.Assists.-> Technical
    AI -.Assists.-> Execution
    AI -.Assists.-> Quality
    Quality -.Feedback.-> Execution
    
    style Business fill:#FF6B6B,color:#FFF
    style AI fill:#FFD93D
```

---

## 🔬 LEVEL MID (20 components)

```mermaid
graph TB
    subgraph Business
        CEO[CEO]
        PO[PO]
    end
    
    subgraph Leadership
        TL[Tech Lead]
        DL[Dev Lead]
    end
    
    subgraph AI_Layer["AI Orchestration"]
        Sis[Sisyphus]
        RA[Research Agents]
        DA[Design Agents]
        DevA[Dev Agents]
    end
    
    subgraph Dev["Development"]
        BE[Backend]
        FE[Frontend]
    end
    
    subgraph Quality
        QA[QA]
        Ops[DevOps]
    end
    
    CEO <--> PO
    PO --> Sis
    Sis --> RA
    RA --> PO
    RA --> TL
    
    TL --> Sis
    Sis --> DA
    DA --> TL
    TL --> DL
    
    DL --> Sis
    Sis <--> PO
    Sis --> DevA
    DevA --> BE
    DevA --> FE
    BE <--> FE
    BE --> DL
    FE --> DL
    
    DL --> QA
    QA <--> BE
    QA <--> FE
    QA --> PO
    PO --> Ops
    Ops --> PO
    
    style CEO fill:#FF6B6B
    style Sis fill:#FFD93D
```

---

## 🔍 LEVEL LOW (45+ components)

```mermaid
graph TB
    subgraph HUMAN["━━━━━━━━━━━━━━ HUMAN TEAM ━━━━━━━━━━━━━━"]
        direction TB
        
        subgraph H_Business["Business Leadership"]
            CEO[CEO<br/>Vision + Budget]
            Client[Client<br/>Requirements]
            PO[Product Owner<br/>Scope + Priorities]
        end
        
        subgraph H_Technical["Technical Leadership"]
            TL[Tech Lead<br/>Architecture Authority]
            DL[Dev Lead<br/>Code Quality Gate]
            AR[Architecture Reviewer<br/>Senior Devs]
        end
        
        subgraph H_Development["Development Team"]
            BE1[Backend Dev 1<br/>API + DB]
            BE2[Backend Dev 2<br/>Services]
            FE1[Frontend Dev 1<br/>UI Components]
            FE2[Frontend Dev 2<br/>Integration]
        end
        
        subgraph H_Quality["Quality & Operations"]
            QA[QA Engineer<br/>Manual + Auto Testing]
            Sec[Security Reviewer<br/>Audits]
            Ops[DevOps Engineer<br/>Deploy + Infrastructure]
        end
    end
    
    subgraph AI["━━━━━━━━━━━━━━ AI AGENT LAYER ━━━━━━━━━━━━━━"]
        direction TB
        
        subgraph AI_Master["Master Orchestration"]
            Sis[🤖 SISYPHUS<br/>Master Orchestrator<br/>Claude Opus 4.5]
        end
        
        subgraph AI_P2["Phase 2: Research Agents"]
            Lib[Librarian<br/>Doc Search<br/>Sonnet 4.5]
            Ora[Oracle<br/>Analysis<br/>GPT-5.2]
            Exp[Explore<br/>Codebase<br/>Grok]
        end
        
        subgraph AI_P3["Phase 3: Design Agents"]
            GK[Gatekeeper<br/>Validate PRD]
            Syn[Synthesis<br/>Generate Design<br/>Ultrabrain]
            Hard[Hardening<br/>9 Stress Tests]
            Map[Mapper<br/>Create Tasks]
        end
        
        subgraph AI_P4["Phase 4: Development Agents"]
            Imp[Implementer<br/>Code Gen<br/>Oracle/Ultrabrain]
            Tst[Test Engineer<br/>Test Gen]
            Int[Integrator<br/>E2E Wiring]
            Adv[Adversarial<br/>Security Review]
            FEA[Frontend Engineer<br/>UI Gen<br/>Gemini 3 Pro]
        end
        
        subgraph AI_P5["Phase 5: Quality Agents"]
            TD[Test Design<br/>Generator]
            Bug[Bug Intake<br/>Evidence Packs]
            Tri[CI Triage<br/>Failure Routing]
        end
        
        subgraph AI_P7["Phase 7: Operations Agents"]
            Inc[Incident Sentinel<br/>Alert Routing]
        end
        
        subgraph AI_P8["Phase 8: Learning Agents"]
            Ret[Retrospective<br/>Agent<br/>Feedback Synthesis]
        end
    end
    
    %% Phase 1: Initiation
    Client -.Submit Requirements.-> CEO
    CEO -->|Project Request| PO
    PO -->|Draft Charter| CEO
    CEO -->|Review & Approve| PO
    
    %% Phase 2: Research
    PO -->|Research Request| Sis
    Sis -->|Delegate Workload| Lib
    Sis -->|Delegate Workload| Ora
    Sis -->|Delegate Workload| Exp
    Lib -->|Research Findings| Sis
    Ora -->|Analysis Report| Sis
    Exp -->|Codebase Context| Sis
    Sis -->|Synthesized Report| PO
    Sis -->|Tech Analysis| TL
    PO <-->|Scope Discussion| TL
    
    %% Phase 3: Architecture
    TL -->|Design Request| Sis
    Sis -->|PRD Validation| GK
    GK -->|Validated PRD| Syn
    Syn -->|Draft Design| Hard
    Hard -->|Critique Feedback| Syn
    Syn -->|Final ADRs + C4| Map
    Map -->|Implementation Plan| TL
    TL -->|Submit for Review| AR
    AR -->|Architecture Feedback| TL
    TL -->|Approved Design| DL
    
    %% Phase 4: Implementation - Setup
    DL -->|Task Assignment| Sis
    Sis <-->|Clarify Requirements| PO
    
    %% Phase 4: Contract Signing
    Sis -->|Draft Interface Contract| Imp
    Sis -->|Draft Interface Contract| Tst
    Imp <-->|Sign scratchpad.md| Tst
    
    %% Phase 4: Code Generation
    Sis -->|Backend Tasks| Imp
    Imp -->|Generated Code| BE1
    Imp -->|Generated Code| BE2
    
    Sis -->|Frontend Tasks| FEA
    FEA -->|Generated Components| FE1
    FEA -->|Generated Components| FE2
    
    %% Phase 4: Test Generation
    Sis -->|Test Tasks| Tst
    Tst -->|Unit Tests| BE1
    Tst -->|Unit Tests| BE2
    Tst -->|UI Tests| FE1
    Tst -->|UI Tests| FE2
    
    %% Phase 4: Developer Collaboration
    BE1 <-->|API Contracts| FE1
    BE2 <-->|API Contracts| FE2
    
    %% Phase 4: Code Review
    BE1 -->|Pull Request| DL
    BE2 -->|Pull Request| DL
    FE1 -->|Pull Request| DL
    FE2 -->|Pull Request| DL
    
    %% Phase 4: Security Review
    Sis -->|Security Check Request| Adv
    Adv -->|Security Audit| Sec
    Sec -->|Security Findings| DL
    
    %% Phase 4: Integration
    Sis -->|E2E Integration| Int
    Int -->|Integration Results| DL
    
    %% Phase 5: QA
    DL -->|Ready for QA| QA
    QA -->|Request Test Cases| TD
    TD -->|Generated Test Cases| QA
    
    QA <-->|Test Execution| BE1
    QA <-->|Test Execution| BE2
    QA <-->|Test Execution| FE1
    QA <-->|Test Execution| FE2
    
    QA -->|CI Test Failures| Tri
    Tri -->|Routed Bugs| Bug
    Bug -->|Bug Evidence Packs| BE1
    Bug -->|Bug Evidence Packs| BE2
    Bug -->|Bug Evidence Packs| FE1
    
    QA -->|Test Report + Signoff| PO
    
    %% Phase 6: Deployment
    PO -->|Go Decision| Ops
    Ops <-->|Deployment Issues| BE1
    Ops <-->|Deployment Issues| FE1
    Ops -->|Deploy Status| PO
    
    %% Phase 7: Monitoring
    Ops -->|Production Active| Inc
    Inc -->|Critical Alerts| Ops
    Ops -->|Hotfix Request| BE1
    Ops -->|Metrics Dashboard| PO
    Ops -->|Incident Reports| DL
    
    %% Phase 8: Retrospective
    PO -->|Retro Request| Ret
    Ret -->|Gather Feedback| BE1
    Ret -->|Gather Feedback| BE2
    Ret -->|Gather Feedback| FE1
    Ret -->|Gather Feedback| FE2
    Ret -->|Gather Feedback| QA
    Ret -->|Gather Feedback| Ops
    Ret -->|Lessons Report| PO
    PO -->|Process Updates| TL
    TL -->|Archive Skills| Sis
    
    %% Daily Coordination
    TL <-.Architecture Sync.-> DL
    DL <-.Daily Standup.-> BE1
    DL <-.Daily Standup.-> BE2
    DL <-.Daily Standup.-> FE1
    DL <-.Daily Standup.-> FE2
    
    %% Styling
    style HUMAN fill:#F5F5F5,stroke:#333333,stroke-width:4px
    style AI fill:#FFFACD,stroke:#FFD700,stroke-width:4px
    
    style H_Business fill:#FFE6E6,stroke:#CC0000,stroke-width:2px
    style H_Technical fill:#E6FFE6,stroke:#00AA00,stroke-width:2px
    style H_Development fill:#E6F3FF,stroke:#0066CC,stroke-width:2px
    style H_Quality fill:#FFE6F9,stroke:#CC00CC,stroke-width:2px
    
    style AI_Master fill:#FFD93D,stroke:#F4A261,stroke-width:3px
    style AI_P2 fill:#E6F3FF,stroke:#0066CC,stroke-width:2px
    style AI_P3 fill:#E6FFE6,stroke:#00AA00,stroke-width:2px
    style AI_P4 fill:#FFF4E6,stroke:#FF9900,stroke-width:2px
    style AI_P5 fill:#FFE6F9,stroke:#CC00CC,stroke-width:2px
    style AI_P7 fill:#E6FFFF,stroke:#00CCCC,stroke-width:2px
    style AI_P8 fill:#FFFACD,stroke:#FFD700,stroke-width:2px
    
    style CEO fill:#FF6B6B,color:#FFF
    style PO fill:#4ECDC4
    style TL fill:#95E1D3
    style Sis fill:#FFD93D,stroke:#F4A261,stroke-width:3px
    style BE1 fill:#F38181
    style FE1 fill:#AA96DA
    style QA fill:#FCBAD3
    style Ops fill:#C5A3FF
```

---

# PERSPECTIVE 3: GOVERNANCE

## 🔭 LEVEL HIGH (6 components)

```mermaid
graph LR
    Vision["📝 VISION<br/>Ideas"]
    Design["🏗️ DESIGN<br/>Architecture"]
    Code["💾 CODE<br/>Software"]
    Prod["🚀 PRODUCTION<br/>Live"]
    Learn["📚 LESSONS<br/>Improve"]
    
    Vision ==>|Gate:<br/>CEO+PO| Design
    Design ==>|Gate:<br/>Arch Review| Code
    Code ==>|Gate:<br/>QA+DevOps| Prod
    Prod ==>|Gate:<br/>Weekly| Learn
    Learn -.Next.-> Vision
    
    style Vision fill:#FFB6C1,stroke:#CC0066,stroke-width:4px
    style Design fill:#E6FFE6,stroke:#00AA00,stroke-width:4px
    style Code fill:#FFF4E6,stroke:#FF9900,stroke-width:4px
    style Prod fill:#90EE90,stroke:#008800,stroke-width:4px
    style Learn fill:#FFFACD,stroke:#FFD700,stroke-width:4px
```

---

## 🔬 LEVEL MID (22 components)

```mermaid
graph TB
    subgraph Input
        Vis[Vision]
        Req[Requirements]
    end
    
    subgraph Planning
        Ch[Charter]
        St[Stories]
        PR[PRD]
    end
    
    subgraph Design
        AD[ADRs]
        C4[C4]
        IP[Impl Plan]
    end
    
    subgraph Development
        Co[Code]
        Te[Tests]
        Ct[Contracts]
    end
    
    subgraph Quality
        TR[Test Reports]
        Bu[Bugs]
        Cv[Coverage]
    end
    
    subgraph Deploy
        St[Staging]
        Pr[Production]
    end
    
    subgraph Ops
        Lo[Logs]
        Me[Metrics]
        In[Incidents]
    end
    
    subgraph Learning
        Le[Lessons]
        SO[SOPs]
    end
    
    Vis --> Ch
    Req --> Ch
    Ch -->|G1| St
    St --> PR
    PR --> AD
    AD --> C4
    C4 -->|G2| IP
    IP --> Ct
    Ct --> Co
    Ct --> Te
    Co -->|G3| TR
    Te --> TR
    TR --> Bu
    TR -->|G4| St
    St --> Pr
    Pr -->|G5| Lo
    Lo --> Me
    Me --> In
    In -->|G6| Le
    Le --> SO
    
    Bu -.Fix.-> Co
    In -.Hotfix.-> Co
    SO -.Next.-> Vis
    
    style Ch fill:#FFE6E6
    style AD fill:#E6FFE6
    style Co fill:#FFF4E6
    style Pr fill:#90EE90
```

---

## 🔍 LEVEL LOW (55+ components)

```mermaid
graph TB
    subgraph INPUT["━━━ INPUT ARTIFACTS ━━━"]
        VM[CEO Voice Memo]
        CR[Client Requirements]
    end
    
    subgraph P1_ART["━━━ PHASE 1: INITIATION ARTIFACTS ━━━"]
        Trans[Transcription<br/>OpenClaw Output]
        Opus[Opus Analysis]
        Ch1[Charter v1]
        Ch2[Charter v2<br/>After CEO Review]
        SB[Solution Brief]
        PRFAQ[PRFAQ Doc]
    end
    
    subgraph P2_ART["━━━ PHASE 2: RESEARCH ARTIFACTS ━━━"]
        LR[Librarian<br/>Report]
        OA[Oracle<br/>Analysis]
        SR[Synthesized<br/>Research]
        US[User<br/>Stories]
        GH[GitHub<br/>Repo]
        LA[Lark<br/>Project]
    end
    
    subgraph P3_ART["━━━ PHASE 3: ARCHITECTURE ARTIFACTS ━━━"]
        direction TB
        PRD[prd.md]
        
        subgraph ADR_Group["ADR Documents"]
            ADR1[ADR-001]
            ADR2[ADR-002]
            ADRN[ADR-00N]
        end
        
        subgraph C4_Group["C4 Diagrams"]
            C4C[C4 Context]
            C4Co[C4 Container]
            C4Cp[C4 Component]
        end
        
        CS1[current_state v1]
        HC[Hardening<br/>Critiques]
        CS2[current_state v2<br/>Final]
        IMP[Implementation<br/>Plan]
    end
    
    subgraph P4_ART["━━━ PHASE 4: IMPLEMENTATION ARTIFACTS ━━━"]
        direction TB
        Scr[scratchpad.md<br/>Contracts]
        
        subgraph Code_Group["Source Code"]
            BEC[Backend<br/>Code]
            FEC[Frontend<br/>Code]
            API[API<br/>Contracts]
        end
        
        subgraph Test_Group["Test Suite"]
            UT[Unit<br/>Tests]
            IT[Integration<br/>Tests]
            ET[E2E<br/>Tests]
        end
        
        subgraph Evidence_Group["Evidence"]
            Bench[Benchmarks]
            Prog[Progress.txt]
            ProgSum[progress<br/>summary.md]
        end
    end
    
    subgraph P5_ART["━━━ PHASE 5: QA ARTIFACTS ━━━"]
        direction TB
        TC[Test<br/>Cases]
        
        subgraph Reports_Group["Test Reports"]
            UTR[Unit<br/>Reports]
            ITR[Int<br/>Reports]
            STR[System<br/>Reports]
            LTR[Load<br/>Reports]
        end
        
        COV[Coverage<br/>Report]
        
        subgraph Bugs_Group["Bug Evidence"]
            BE1[Bug Pack 1]
            BE2[Bug Pack 2]
            BEN[Bug Pack N]
        end
    end
    
    subgraph P6_ART["━━━ PHASE 6: DEPLOYMENT ARTIFACTS ━━━"]
        STG[Staging<br/>Build]
        Val[Validation<br/>Report]
        PRO[Production<br/>Build]
        Run[Deployment<br/>Runbook]
        Roll[Rollback<br/>Plan]
        Health[Health<br/>Checks]
    end
    
    subgraph P7_ART["━━━ PHASE 7: OPERATIONS ARTIFACTS ━━━"]
        direction TB
        
        subgraph Logs_Group["Logs & Metrics"]
            AppLog[App<br/>Logs]
            ErrLog[Error<br/>Logs]
            MetDash[Metrics<br/>Dashboard]
        end
        
        subgraph Inc_Group["Incidents"]
            IR1[Incident 1]
            IR2[Incident 2]
            IRN[Incident N]
        end
        
        SLA[SLA<br/>Report]
    end
    
    subgraph P8_ART["━━━ PHASE 8: LEARNING ARTIFACTS ━━━"]
        RM[Retro<br/>Notes]
        Les[Lessons<br/>Learned]
        SOPU[Updated<br/>SOPs]
        Ski[Skills<br/>Archive]
    end
    
    %% Forward flow with gates
    VM --> Trans
    CR --> Trans
    Trans --> Opus
    Opus --> Ch1
    Ch1 -->|G1A: PO| Ch2
    Ch2 -->|G1B: CEO| SB
    SB --> PRFAQ
    
    Ch2 --> LR
    Ch2 --> OA
    LR --> SR
    OA --> SR
    SR --> US
    SR --> GH
    SR --> LA
    US -->|G2: Dev+PO| PRD
    
    PRD --> ADR1
    PRD --> ADR2
    PRD --> ADRN
    ADR1 --> C4C
    ADR2 --> C4C
    ADRN --> C4C
    C4C --> C4Co
    C4Co --> C4Cp
    C4Cp --> CS1
    CS1 --> HC
    HC --> CS2
    CS2 -->|G3: Arch Review| IMP
    
    IMP --> Scr
    Scr --> BEC
    Scr --> FEC
    Scr --> API
    BEC --> UT
    FEC --> UT
    BEC --> IT
    FEC --> IT
    BEC --> ET
    FEC --> ET
    BEC --> Bench
    BEC --> Prog
    Prog --> ProgSum
    
    BEC -->|G4A: PR| TC
    FEC -->|G4B: PR| TC
    
    TC --> UTR
    UT --> UTR
    IT --> ITR
    ET --> STR
    ET --> LTR
    UTR --> COV
    UTR --> BE1
    ITR --> BE1
    STR --> BE2
    LTR --> BEN
    
    UTR -->|G5: QA| STG
    ITR -->|G5: QA| STG
    STR -->|G5: QA| STG
    COV -->|G5: QA| STG
    
    STG --> Val
    Val --> Run
    Val --> Roll
    Val -->|G6: Go/NoGo| PRO
    PRO --> Health
    Health --> AppLog
    
    AppLog --> ErrLog
    AppLog --> MetDash
    ErrLog --> IR1
    MetDash --> IR2
    IR2 --> SLA
    SLA -->|G7: Weekly| RM
    
    RM --> Les
    Les --> SOPU
    Les --> Ski
    
    %% Feedback loops
    BE1 -.Fix Bugs.-> BEC
    BE2 -.Fix Bugs.-> FEC
    BEN -.Fix Bugs.-> BEC
    IR1 -.Hotfix.-> BEC
    IR2 -.Hotfix.-> BEC
    Ski -.Next Project.-> VM
    SOPU -.Improve.-> Trans
    
    %% Reuse references
    ADR1 -.Referenced by.-> BEC
    ADR2 -.Referenced by.-> FEC
    ADRN -.Referenced by.-> BEC
    CS2 -.Guides.-> IMP
    US -.Traced to.-> ET
    
    %% Styling
    style INPUT fill:#FFB6C1,stroke:#CC0066,stroke-width:3px
    style P1_ART fill:#FFE6E6,stroke:#CC0000,stroke-width:3px
    style P2_ART fill:#E6F3FF,stroke:#0066CC,stroke-width:3px
    style P3_ART fill:#E6FFE6,stroke:#00AA00,stroke-width:3px
    style P4_ART fill:#FFF4E6,stroke:#FF9900,stroke-width:3px
    style P5_ART fill:#FFE6F9,stroke:#CC00CC,stroke-width:3px
    style P6_ART fill:#F0E6FF,stroke:#6600CC,stroke-width:3px
    style P7_ART fill:#E6FFFF,stroke:#00CCCC,stroke-width:3px
    style P8_ART fill:#FFFACD,stroke:#FFD700,stroke-width:3px
    
    style ADR_Group fill:#D5F4E6,stroke:#00AA00,stroke-width:2px
    style C4_Group fill:#D5F4E6,stroke:#00AA00,stroke-width:2px
    style Code_Group fill:#FFF9E6,stroke:#FF9900,stroke-width:2px
    style Test_Group fill:#FFF9E6,stroke:#FF9900,stroke-width:2px
    style Evidence_Group fill:#FFF9E6,stroke:#FF9900,stroke-width:2px
    style Reports_Group fill:#FFE6F9,stroke:#CC00CC,stroke-width:2px
    style Bugs_Group fill:#FFE6F9,stroke:#CC00CC,stroke-width:2px
    style Logs_Group fill:#D5F4F4,stroke:#00CCCC,stroke-width:2px
    style Inc_Group fill:#D5F4F4,stroke:#00CCCC,stroke-width:2px
```

---

# QUICK SELECTOR GUIDE

## By Role

| Your Role | Start With | Then Use | For Details |
|-----------|-----------|----------|-------------|
| **CEO/Board** | Perspective 1-HIGH | Perspective 3-HIGH | - |
| **Product Owner** | Perspective 1-MID | Perspective 2-MID | Perspective 3-MID |
| **Tech Lead** | Perspective 1-MID | Perspective 3-MID | Perspective 1-LOW |
| **Dev Lead** | Perspective 2-MID | Perspective 1-MID | Perspective 2-LOW |
| **Developer** | Perspective 1-MID | Perspective 2-MID | Perspective 1-LOW |
| **QA Engineer** | Perspective 3-MID | Perspective 1-MID | Perspective 3-LOW |
| **DevOps** | Perspective 1-MID | Perspective 3-MID | Perspective 3-LOW |

## By Question

| Question | Use This |
|----------|----------|
| "What's the big picture?" | Perspective 1-HIGH |
| "What runs in parallel?" | Perspective 1-MID |
| "Every single step?" | Perspective 1-LOW |
| "Who do I work with?" | Perspective 2-HIGH |
| "Who owns what?" | Perspective 2-MID |
| "Every interaction?" | Perspective 2-LOW |
| "What gets approved?" | Perspective 3-HIGH |
| "What artifacts exist?" | Perspective 3-MID |
| "Complete audit trail?" | Perspective 3-LOW |

## By Use Case

| Use Case | Diagrams Needed |
|----------|----------------|
| **Executive Briefing** | 1-HIGH, 3-HIGH |
| **Sprint Planning** | 1-MID, 2-MID |
| **Team Onboarding** | 1-MID, 2-MID, 3-MID |
| **Compliance Audit** | 3-MID, 3-LOW |
| **Process Improvement** | 1-LOW, 2-LOW |
| **Detailed Training** | All 9 diagrams |

---

# SUMMARY

**9 Total Diagrams:**
- Perspective 1 (Work): HIGH (4), MID (16), LOW (50+)
- Perspective 2 (People): HIGH (6), MID (20), LOW (45+)
- Perspective 3 (Governance): HIGH (6), MID (22), LOW (55+)

**Always start HIGH. Graduate to MID. Use LOW only when needed.**

**Test in Mermaid Live:** https://mermaid.live
