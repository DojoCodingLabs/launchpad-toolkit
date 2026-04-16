# launchpad-toolkit

> **Methodology prototype laboratory** para el pillar **DojoOS Launchpad** — AI intake, cap table, co-founder matching, investor matching, demo day prep, stage tracker.

Plugin de Claude Code complementario a [`business-model-toolkit`](https://github.com/DojoCodingLabs/business-model-toolkit) (single-venture lifecycle), [`ux-research-toolkit`](https://github.com/DojoCodingLabs/ux-research-toolkit) (user research) y [`venture-studio-toolkit`](https://github.com/DojoCodingLabs/venture-studio-toolkit) (MACRO portfolio management).

**Posición en el ecosistema**:

| Plugin | Scope | Owner DojoOS alineado |
|---|---|---|
| `business-model-toolkit` | Single venture lifecycle (21 fases) | — |
| `ux-research-toolkit` | User research maps + personas | — |
| `venture-studio-toolkit` | MACRO — portfolio, studio, legal structures | Daniel Garbanzo |
| **`launchpad-toolkit`** | **MICRO — single venture launchpad journey** | **William Ugalde** |

## Propósito dual

Este plugin sirve **dos audiencias al mismo tiempo**, y esto es **por diseño** — no es overlap accidental:

### 1. External — founders sin DojoOS

Founders individuales que necesitan:
- Intake interview estructurado → startup profile artifact
- Cap table builder + vesting calculator para primer grant
- Founder documents (agreements, SAFE, term sheet) basados en templates
- Investor matching para early fundraising
- Demo day application prep
- Stage tracker por milestones (Ideation → Formation → MVP → Traction → Funded → Scaling)

### 2. Internal — laboratorio metodológico para DojoOS Launchpad

**William Ugalde** es el owner del pillar Launchpad en DojoOS. Este plugin replica las features del Launchpad product de DojoOS como **prototipos metodológicos** que:

- Validan UX/flows antes de comprometer código en DojoOS
- Reducen productization risk (ya sabés qué funciona antes de implementar)
- Alimentan SPIKE issues en Linear para William via el skill `feature-to-spike`

**Duplicar funcionalidad DojoOS acá NO es error — es el diseño**. El loop metodología → dog-food → SPIKE → feature DojoOS está explicado en [`references/productization-workflow.md`](./references/productization-workflow.md).

## Estado actual

**v0.4.0 — propose-spike command**

Sub-issue de ejecución bootstrap: [DOJ-3221](https://linear.app/dojo-coding/issue/DOJ-3221) ✓ Done (parent SPIKE: [DOJ-3189](https://linear.app/dojo-coding/issue/DOJ-3189)).

### Skills completos (8 — todos los del scope original)

**Core (v0.1)**:
- **`startup-intake`** — AI intake interview que produce un `startup-profile.md` compatible schema-wise con DojoOS Startup Profile
- **`feature-to-spike`** — **Differentiator del plugin**. Transforma learnings del dog-food en Linear SPIKE issues formateados para William

**Founder setup (v0.2)**:
- **`cap-table-builder`** — cap table inicial para single venture: founders + option pool + advisor pool + SAFEs + convertible notes + vesting + SAFE conversion modeling
- **`founder-documents`** — stack legal founder: FSPA, IP Assignment, Vesting Exhibit, Advisor (FAST), SAFE (YC post-money), Term Sheet (NVCA)

**Matching + fundraising + tracking (v0.3)**:
- **`cofounder-matching`** — rubric 6-axis (domain / skill / values / equity / time / track record) con weighted scoring ajustado por stage. Kill-switches override score.
- **`investor-matching`** — 5-axis scoring (stage / check / thesis / geography / value-add) con priority configurable. Pipeline tracker incluido.
- **`demo-day-prep`** — 4 artefactos: application, 10-slide deck outline, 3-min script, 50+ Q&A bank. Rehearsal best practices 5-5-5.
- **`stage-tracker`** — 6 stages (Ideation → Scaling) con exit criteria + Dojo Score (5-axis, 0-100). Evidence-over-claim principle.

### Commands (v0.4)

- **`/launchpad-toolkit:propose-spike`** — wrapper command over `feature-to-spike` skill con auto-assignee William + auto-parent DOJ-3189 + auto-labels + optional direct file via Linear MCP. Acepta `$ARGUMENTS` como seed del concrete pattern.

### Reference docs (1)

- **`productization-workflow.md`** — Cómo fluye methodology → SPIKE → DojoOS feature

### NO incluido en v0.4 (roadmap v0.5)

| Artifact | Estado |
|---|---|
| `dojoos-api-consumer` agent | 🔜 v0.5 — implementable contra el spec OpenAPI YA shipped en [docs.dojocoding.io/openapi.yaml](https://docs.dojocoding.io/openapi.yaml) (via DOJ-3170). Agent reads the spec; endpoint availability tracked separately per endpoint in DojoOS repo. |

### Unblocking histórica

Originalmente v0.3/v0.4 scope estaba marcado "blocked on @garbanzo's DojoOS API". Re-evaluación reveló 2 flawed assumptions:

1. Los **skills** son metodología (rubrics, scoring, workflows), no data fetching — shippable sin API
2. La **OpenAPI spec YA existe** en dojo-documentation (DOJ-3170 closed 2026-04-14) — el agente puede implementarse contra contract, no needs new infrastructure from @garbanzo

Solo quedan los endpoints individuales del Edge Function layer, tracked separately per endpoint en DojoOS repo.

Agente pendiente:

- `dojoos-api-consumer` — consume DojoOS API para matching; blocked en implementación de API por Daniel Garbanzo

Command pendiente:

- `/launchpad-toolkit:propose-spike` — wrapper para `feature-to-spike` que genera issue listo para Linear CLI/MCP

## Instalación

```bash
claude plugin add DojoCodingLabs/launchpad-toolkit
```

⚠️ **Stability disclaimer**: v0.x marca **early prototype** — scope mínimo viable para evaluación por William antes de expandir al scope completo de 8 skills. Breaking changes esperables en v0.x. Strict semver compliance arranca en v1.0.0.

## Fuentes metodológicas

- **DojoOS Launchpad current spec**: `dojo-documentation/content/docs/product/launchpad/startup-flows.md`
- **Pillar ownership** (Slack 2026-04-10 `#C0AKTN24C91`): @juan + @daniel asignaron Launchpad a @william
- **Plan file**: `~/.claude/plans/cheeky-tinkering-rain.md` (Phase 2)

## Plugins complementarios del ecosistema DojoCoding Labs

- [`business-model-toolkit`](https://github.com/DojoCodingLabs/business-model-toolkit) — single venture lifecycle
- [`ux-research-toolkit`](https://github.com/DojoCodingLabs/ux-research-toolkit) — user research maps
- [`venture-studio-toolkit`](https://github.com/DojoCodingLabs/venture-studio-toolkit) — MACRO portfolio + legal structures

## Licencia

Business Source License 1.1 (BSL-1.1). Ver [LICENSE](./LICENSE) para detalles.
