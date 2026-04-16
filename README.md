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

**v0.2.0 — cap table + founder documents**

Sub-issue de ejecución bootstrap: [DOJ-3221](https://linear.app/dojo-coding/issue/DOJ-3221) ✓ Done (parent SPIKE: [DOJ-3189](https://linear.app/dojo-coding/issue/DOJ-3189)).

### Skills completos (4)

- **`startup-intake`** (v0.1) — AI intake interview que produce un `startup-profile.md` compatible schema-wise con DojoOS Startup Profile
- **`feature-to-spike`** (v0.1) — **Differentiator del plugin**. Transforma learnings del dog-food en Linear SPIKE issues formateados para William, con criterios de aceptación + links a artefactos generados
- **`cap-table-builder`** (v0.2) — Constructor del cap table inicial para single venture: founders + option pool + advisor pool + SAFEs + convertible notes + vesting schedule + SAFE conversion modeling (3 scenarios)
- **`founder-documents`** (v0.2) — Generador del stack legal founder: Founder Stock Purchase Agreement (o Operating Agreement LLC), IP Assignment, Vesting Schedule Exhibit, Advisor Agreement (FAST), SAFE (post-money YC), Term Sheet (NVCA Series Seed)

### Reference docs (1)

- **`productization-workflow.md`** — Cómo fluye methodology → SPIKE → DojoOS feature

### NO incluido en v0.2 (roadmap)

| Skill | DojoOS Launchpad feature que prototiparía | Estado |
|---|---|---|
| `cofounder-matching` | Co-Founder Matching + Dojo-Score | 🔜 v0.3 (pending DojoOS API by @garbanzo) |
| `investor-matching` | Investor fit scoring | 🔜 v0.3 (pending DojoOS API) |
| `demo-day-prep` | Demo Day applications + pitch prep | 🔜 v0.3 |
| `stage-tracker` | Milestone tracking (Ideation → Scaling) | 🔜 v0.3 |

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
