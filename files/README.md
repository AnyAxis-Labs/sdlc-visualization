# SDLC 3x3 Mermaid Diagrams

Paste any file into [mermaid.live](https://mermaid.live) to render.

## File Map

| # | File | Perspective | Zoom | Nodes | Audience |
|---|------|-------------|------|-------|----------|
| 1 | `1_workflow_HIGH.mermaid` | Work Flow | HIGH | ~5 | CEO, stakeholders |
| 2 | `2_workflow_MID.mermaid` | Work Flow | MID | ~18 | PO, leads |
| 3 | `3_workflow_LOW.mermaid` | Work Flow | LOW | ~50 | Engineers, audit |
| 4 | `4_people_HIGH.mermaid` | People + AI | HIGH | ~6 | Org overview |
| 5 | `5_people_MID.mermaid` | People + AI | MID | ~22 | Team + agents |
| 6 | `6_people_LOW.mermaid` | People + AI | LOW | ~45 | Every handoff |
| 7 | `7_governance_HIGH.mermaid` | Governance | HIGH | ~8 | Artifact flow |
| 8 | `8_governance_MID.mermaid` | Governance | MID | ~25 | Artifacts + gates |
| 9 | `9_governance_LOW.mermaid` | Governance | LOW | ~55 | Full traceability |

## Color Legend

**Workflow phases:** Red=Initiation, Blue=Research, Green=Architecture, Orange=Implementation, Pink=QA, Purple=Deploy, Cyan=Monitor, Gold=Retro

**People roles:** Red=Exec, Teal=Product, Blue=Engineering, Pink=QA, Lavender=Ops, Yellow=AI Agent

**Gates:** Green diamonds = approval checkpoints

## Recommended Reading Order

- **CEO/Board:** 1 → 7 → 4
- **Product Owner:** 4 → 5 → 8
- **Tech Lead:** 2 → 8 → 3
- **Developer:** 2 → 5 → 6
- **New hire:** 1 → 4 → 2 → 5
