# Changelog

All notable changes to `launchpad-toolkit` are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/). During the v0.x prototype phase the plugin does **not** follow strict semver — breaking changes may occur in minor releases as methodology iterates. Strict semver compliance begins in v1.0.0.

## [Unreleased]

### Planned for v0.3
- `cofounder-matching` skill (blocked on DojoOS API by @garbanzo)
- `investor-matching` skill (blocked on DojoOS API by @garbanzo)
- `demo-day-prep` skill
- `stage-tracker` skill
- `dojoos-api-consumer` agent
- `/launchpad-toolkit:propose-spike` command

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

[Unreleased]: https://github.com/DojoCodingLabs/launchpad-toolkit/compare/v0.2.0...HEAD
[0.2.0]: https://github.com/DojoCodingLabs/launchpad-toolkit/releases/tag/v0.2.0
[0.1.0]: https://github.com/DojoCodingLabs/launchpad-toolkit/releases/tag/v0.1.0
