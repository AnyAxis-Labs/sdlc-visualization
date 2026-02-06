# AI Testing Lifecycle

Testing lifecycle from unit to reporting, with AI assistance and human review gates.

## Level High

```mermaid
graph LR
    Unit["Unit Testing"] --> Integration["Integration Testing"] --> System["System Testing"]
    System --> Plan["Test Plan"] --> Design["Test Design"] --> Execution["Test Execution"]
    Execution --> Reporting["Results Analysis & Reporting"] --> Improve["Continuous Improvement"]
```

---

## Level Mid

```mermaid
graph TB
    subgraph Inputs
        PRD["PRD + Acceptance Criteria"]
        Data["Test Data Recipe"]
        Env["Env + Feature Flags"]
    end

    subgraph Phases
        Unit["Unit Testing"]
        Integration["Integration Testing"]
        System["System Testing"]
        Plan["Test Plan"]
        Design["Test Design"]
        Execution["Test Execution"]
        Reporting["Results Analysis & Reporting"]
    end

    subgraph AI_Modules
        UnitAI["Unit Test Copilot"]
        IntegrationAI["Integration Contract Agent"]
        SystemAI["System Readiness Agent"]
        PlanAI["Test Plan Architect"]
        DesignAI["Test Design Generator"]
        ExecAI["Execution Orchestrator"]
        ReportAI["Quality Insights & Reporter"]
        EvidenceAI["Evidence Pack + Bug Intake"]
    end

    Human["Human Review Gate"]

    PRD --> Plan
    Data --> Design
    Env --> System

    Unit --> Integration --> System --> Plan --> Design --> Execution --> Reporting

    UnitAI -.assists.-> Unit
    IntegrationAI -.assists.-> Integration
    SystemAI -.assists.-> System
    PlanAI -.assists.-> Plan
    DesignAI -.assists.-> Design
    ExecAI -.assists.-> Execution
    ReportAI -.assists.-> Reporting
    EvidenceAI -.assists.-> Execution

    Human --> Plan
    Human --> Execution
    Reporting --> Human
```

---

## Level Low

```mermaid
graph TB
    subgraph Inputs
        PRD["PRD + Acceptance Criteria"]
        Risk["Risk Triage + Critical Flows"]
        Contracts["API/Contract Specs"]
        Data["Test Data Recipe"]
        Env["Env + Feature Flags"]
        Policy["AI Data Policy + Redaction"]
    end

    subgraph Unit_Phase
        UnitSpec["Unit Scope + Coverage Targets"]
        Conventions["Test Conventions + Naming"]
        UnitAI["Unit Test Copilot"]
        Skeleton["Test Skeletons"]
        Mocks["Mock Strategy"]
        UnitTests["Unit Test Suite"]
        UnitCI["Unit CI Gate"]
        UnitCov["Coverage Report"]
        Gaps["Coverage Gaps"]
        UnitSpec --> Conventions --> UnitAI --> Skeleton --> Mocks --> UnitTests --> UnitCI --> UnitCov --> Gaps
    end

    subgraph Integration_Phase
        IntSpec["Contract Matrix"]
        Schema["Schema Validation"]
        Idem["Idempotency + Retries"]
        IntAI["Integration Contract Agent"]
        IntData["Seed/Fixtures"]
        IntRun["Integration Runs"]
        Flake["Flake Handling"]
        IntTriage["Failure Triage"]
        IntSpec --> Schema --> Idem --> IntAI --> IntData --> IntRun --> Flake --> IntTriage
    end

    subgraph System_Phase
        Staging["Staging Deploy"]
        Deps["Dependency Health"]
        Reset["Data Reset/Seed"]
        Readiness["Readiness Checks"]
        Smoke["Smoke Suite"]
        Blockers["Blocker Triage"]
        EnvFix["Env Fixes"]
        Staging --> Deps --> Reset --> Readiness --> Smoke --> Blockers --> EnvFix
    end

    subgraph Plan_Design
        PlanDraft["Test Plan Draft"]
        Scope["Scope + Entry/Exit"]
        RACI["RACI + Owners"]
        Trace["Traceability Matrix"]
        Design["Test Cases"]
        DataMatrix["Data Matrix"]
        AutoPick["Automation Candidates"]
        DesignGate["Design Review"]
        PlanDraft --> Scope --> RACI --> Trace --> Design --> DataMatrix --> AutoPick --> DesignGate
    end

    subgraph Execution
        SuiteSelect["Suite Selection"]
        Order["Run Order Optimizer"]
        ExecAI["Execution Orchestrator"]
        Runs["Smoke/Targeted/Regression"]
        Parallel["Parallel Runs"]
        Artifacts["Logs + Screens + Video"]
        Evidence["Evidence Pack"]
        SuiteSelect --> Order --> ExecAI --> Runs --> Parallel --> Artifacts --> Evidence
    end

    subgraph Bugs
        Intake["Bug Intake"]
        Severity["Severity + SLA"]
        Assign["Owner Assignment"]
        Repro["Repro Steps"]
        Fix["Fix + Verification"]
        ReRun["Targeted Re-run"]
        Intake --> Severity --> Assign --> Repro --> Fix --> ReRun
    end

    subgraph Reporting
        Report["Release/Weekly Report"]
        KPI["Quality KPIs"]
        GoNoGo["Go/No-Go Gate"]
        RCA["RCA Summary"]
        Backlog["Improvement Backlog"]
        Report --> KPI --> GoNoGo --> RCA --> Backlog
    end

    PRD --> Risk --> UnitSpec
    Contracts --> IntSpec
    Data --> IntData
    Env --> Staging
    Policy --> UnitSpec

    Gaps --> IntSpec
    IntTriage --> Staging
    EnvFix --> PlanDraft
    DesignGate --> SuiteSelect
    Evidence --> Intake
    ReRun --> Report
    Backlog -.next cycle.-> Risk
```
