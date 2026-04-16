# Changelog

All notable changes to `launchpad-toolkit` are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/). During the v0.x prototype phase the plugin does **not** follow strict semver — breaking changes may occur in minor releases as methodology iterates. Strict semver compliance begins in v1.0.0.

## [Unreleased]

### Planned for v0.5
- `dojoos-api-consumer` agent — consumes the **already shipped** DojoOS OpenAPI spec at `https://docs.dojocoding.io/openapi.yaml` (via DOJ-3170 Stoplight Elements integration). Agent reads the spec to understand available endpoints and enriches skills with runtime data when endpoints are live. Note: agent can be implemented NOW against the OpenAPI spec as contract; actual endpoint availability depends on Edge Function implementation status (tracked separately per endpoint in DojoOS repo).

## [0.4.0] — 2026-04-16

### Added

- Command `/launchpad-toolkit:propose-spike` — thin wrapper sobre el skill `feature-to-spike` con defaults pre-configurados para William Ugalde (DojoOS Launchpad pillar owner):
  - Auto-assignee: William (Linear ID `8f14370d-3602-49e3-81f2-eeb05b965687`)
  - Auto-parent: DOJ-3189 (launchpad-toolkit tracking SPIKE)
  - Auto-labels: `Spike`, `Explore`, `methodology-prototype`
  - Auto-team: DojoOS; Auto-project: Launchpad; Auto-state: Triage
  - Accepts optional `$ARGUMENTS` como seed del "concrete pattern" en FTS-1
  - Direct file via Linear MCP (`mcp__linear-server__save_issue`) o fallback markdown copy-paste
- Documentation of when NOT to use the command (feature requests, bugs, plugin internals — estos van por otras vías)

### Changed

- `plugin.json` 0.3.0 → 0.4.0
- CHANGELOG v0.5 roadmap simplificado: solo `dojoos-api-consumer` agent. Descubrimiento: la OpenAPI spec YA existe en dojo-documentation/public/openapi.yaml (shipped via DOJ-3170). El agente puede implementarse contra el spec SIN depender de @garbanzo para nueva infraestructura — lo que bloquea es solo endpoint availability por-endpoint.

## [0.3.0] — 2026-04-16

### Added

- Skill `cofounder-matching` — rubric-based co-founder matching methodology con 6-axis framework (domain fit, skill complementarity, values alignment, equity expectations, time commitment, track record). Weighted scoring ajustado por stage. Genera scorecard + gap analysis + interview questions + ranked shortlist. Kill-switches override score. Standalone; sync con DojoOS API cuando el agente `dojoos-api-consumer` esté disponible.
- Skill `investor-matching` — investor fit scoring con 5-axis framework (stage fit, check size, thesis alignment, geography/vertical, value-add depth). Weighted scoring configurable por priority (fundraising-first / value-add-first / stealth-strategic). Genera fit-scorecard + intelligence notes + customized outreach + target list ranked + pipeline tracker.
- Skill `demo-day-prep` — preparation workflow para Demo Day events (YC, Techstars, etc.). 4 artefactos: application write-up, 10-slide deck outline con speaker notes, 3-min pitch script con timing markers, 50+ Q&A bank categorizado. Incluye rehearsal best practices (5-5-5 rule) y anti-patterns. Standalone; schema-compat con DojoOS Demo Day queue futuro.
- Skill `stage-tracker` — milestone tracking across the 6 DojoOS Launchpad stages (Ideation → Formation → MVP → Traction → Funded → Scaling). Exit criteria per stage + Dojo-Score-compatible 5-axis scoring (Team, Product, Traction, Market, Business Model; 0-100 total). Genera current-stage + milestones + blockers + dojo-score + history. Evidence-over-claim principle.

### Changed

- `plugin.json` version bump 0.2.0 → 0.3.0
- README updated to reflect 8 skills total (up from 4)
- Roadmap simplified: v0.4 = `dojoos-api-consumer` agent + `/propose-spike` command (v0.3 is the last "skills-only" release)

### Rationale

Previously v0.3 skills were blocked on DojoOS API via @garbanzo. Re-evaluation revealed that skills themselves are **methodology** (rubrics, scoring, workflows) — they do NOT require live API data. Only the `dojoos-api-consumer` **agent** (which fetches live data to enrich skills) is API-blocked. Skills ship as standalone; agent is v0.4 pending API.

## [0.2.0] — 2026-04-16

## [0.2.0] — 2026-04-16

### Added

- Skill `cap-table-builder` — constructor de cap table inicial para single venture. Soporta founders + option pool + advisor pool + SAFEs + convertible notes. Genera `cap-table.md` + `vesting-schedule.md` + `safe-conversion-modeling.md` con modeling de 3 scenarios (conservative/expected/optimistic) de next priced round. Cross-reference a `venture-studio-toolkit:sweat-equity-agreement` para 83(b) tratamiento diferenciado por entity type (C-Corp restricted stock / LLC profits interest / LLC capital interest).
- Skill `founder-documents` — generador de stack legal founder. 6 documentos: Founder Stock Purchase Agreement (o Operating Agreement LLC), IP Assignment, Vesting Schedule Exhibit, Advisor Agreement (FAST framework), SAFE (post-money YC standard), Term Sheet (NVCA Series Seed). Cada output incluye `[TO BE FILLED BY LAWYER]` markers y lawyer review checklist. STRONG legal disclaimer en todos los outputs.

### Changed

- `plugin.json` version bump 0.1.0 → 0.2.0
- README references updated to reflect 4 skills total (up from 2)

## [0.1.0] — 2026-04-16

### Added

- Initial scaffold ([DOJ-3221](https://linear.app/dojo-coding/issue/DOJ-3221), parent SPIKE [DOJ-3189](https://linear.app/dojo-coding/issue/DOJ-3189))
- `plugin.json` + `README.md` + BSL-1.1 `LICENSE`
- Skill `startup-intake` — AI intake interview producing `startup-profile.md` artifact, schema-compatible with DojoOS Launchpad Startup Profile
- Skill `feature-to-spike` — **differentiator** — transforms dog-food methodology learnings into Linear SPIKE issues for William Ugalde (Launchpad pillar owner)
- Reference `references/productization-workflow.md` — 5-step loop documenting methodology → SPIKE → DojoOS feature flow

### Known limitations (v0.1)

- Only 2 of 8 planned skills implemented; remaining 6 deferred to v0.2/v0.3
- `dojoos-api-consumer` agent not implemented (blocked on DojoOS API by Daniel Garbanzo)
- Bilingual output framework documented but implementation per-skill is roadmap

[Unreleased]: https://github.com/DojoCodingLabs/launchpad-toolkit/compare/v0.4.0...HEAD
[0.4.0]: https://github.com/DojoCodingLabs/launchpad-toolkit/releases/tag/v0.4.0
[0.3.0]: https://github.com/DojoCodingLabs/launchpad-toolkit/releases/tag/v0.3.0
[0.2.0]: https://github.com/DojoCodingLabs/launchpad-toolkit/releases/tag/v0.2.0
[0.1.0]: https://github.com/DojoCodingLabs/launchpad-toolkit/releases/tag/v0.1.0
