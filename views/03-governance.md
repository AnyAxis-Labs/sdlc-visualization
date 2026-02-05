# PERSPECTIVE 3: GOVERNANCE

What moves through the system as artifacts, and who approves each gate.

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
