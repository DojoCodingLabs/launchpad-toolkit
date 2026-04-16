---
description: Generate a Linear SPIKE issue for William Ugalde (DojoOS Launchpad pillar owner) from a methodology learning discovered while dog-fooding launchpad-toolkit. Wraps the `feature-to-spike` skill with auto-assignee, auto-parent-issue (DOJ-3189), auto-labels, and optional direct filing via Linear MCP. Accepts an optional short description of the learning as `$ARGUMENTS`.
---

# /launchpad-toolkit:propose-spike

Genera un Linear SPIKE issue formateado para **William Ugalde** (owner del pillar DojoOS Launchpad) desde un learning metodológico descubierto dog-fooding este plugin.

**Thin wrapper** sobre la skill `feature-to-spike` con defaults pre-configurados:
- **Assignee**: William Ugalde (Slack `U09A1C9V24A`; email `william@dojocoding.io`; Linear ID `8f14370d-3602-49e3-81f2-eeb05b965687`)
- **Parent issue**: [DOJ-3189](https://linear.app/dojo-coding/issue/DOJ-3189) — tracking SPIKE del plugin
- **Labels**: `Spike`, `Explore`, `methodology-prototype`
- **Team**: DojoOS (Linear team `c654288d-8e5b-45e6-877c-0f68131f9626`)
- **Project**: Launchpad (Linear project `836b095b-386a-4713-8468-5ae7bfad3af8`)
- **State inicial**: `Triage` (William lo mueve a In Progress cuando decide scope)
- **Priority default**: `Normal` (3) — el user puede ajustar a `High` (2) / `Urgent` (1) / `Low` (4)

## Uso

```bash
# Con learning context inline
claude /launchpad-toolkit:propose-spike "startup-intake flow mejora cuando preguntamos problem antes de solution"

# Sin argumentos — arranca el flujo feature-to-spike desde cero
claude /launchpad-toolkit:propose-spike
```

El `$ARGUMENTS` (si hay) se usa como **seed del "concrete pattern"** en FTS-1 del skill `feature-to-spike`. Si vacío, arranca el flujo completo preguntando el pattern.

## Flujo

1. **Invocar skill `feature-to-spike`** con el argument (si hay) como primer input
2. **Ejecutar los 7 pasos** de FTS-1 hasta FTS-7 del skill:
   - FTS-1: Concrete pattern identification (seeded con `$ARGUMENTS` si existe)
   - FTS-2: Evidence gathering
   - FTS-3: Productization hypothesis
   - FTS-4: Acceptance criteria
   - FTS-5: Priority + scope
   - FTS-6: Generate SPIKE draft
   - FTS-7: Offer direct filing via Linear MCP
3. **Draft en disco**: `./launchpad/spikes/YYYY-MM-DD-{spike-slug}.md` (generado por el skill)
4. **Direct file opcional**: Si Linear MCP (`mcp__linear-server__save_issue`) está disponible Y el user aprueba:
   - Auto-apply defaults (assignee, parent, labels, team, project, state)
   - Crear el issue
   - Attachear links a artifacts relevantes (startup-profile.md, cap-table.md, etc.)
   - Update `./launchpad/spikes/YYYY-MM-DD-{spike-slug}-filed.md` con el Linear issue URL
5. **Fallback**: Si Linear MCP NO está disponible o user prefiere file manual:
   - Output: markdown ready to copy-paste en Linear web UI
   - O: `gh` CLI command con título + body + assignee para crear como GitHub issue y sincronizar a Linear via integration
6. **Report al user**: link al Linear issue creado (o al draft file) + next step expectations

## Auto-defaults aplicados

Cuando se usa este command (vs. invocar `feature-to-spike` directamente):

| Campo Linear | Default command | Override? |
|---|---|---|
| Assignee | William (ID `8f14370d-...`) | Solo si user explícitamente pide otro |
| Team | DojoOS | No — launchpad-toolkit SPIKEs siempre van a DojoOS team |
| Project | Launchpad | No — productization target del plugin |
| Parent | DOJ-3189 | No — mantiene trazabilidad |
| Labels | Spike + Explore + methodology-prototype | Adicionales OK; NO remover estos |
| State | Triage | No — William move a In Progress cuando decide |
| Priority | Normal (3) | User ajusta en FTS-5 |

## Cuándo NO usar este command

Use this command **only** when:
- El learning viene explícitamente del dog-food de launchpad-toolkit
- El pattern es concrete + tiene evidence (ver `feature-to-spike` — 4 criterios de good SPIKE)
- El pattern es candidato real para productization en DojoOS Launchpad

NO use este command para:
- **Feature requests genéricos** sobre DojoOS — use Linear directamente, asignar al pillar owner correspondiente
- **Bug reports** — usar labels `Bug` y estructura distinta
- **Strategic product decisions** — esas van a SPIKEs top-level, NO sub-issue del plugin
- **Launchpad-toolkit internal improvements** (e.g., mejorar una skill del plugin) — abrir issue en el repo GitHub, NO en DojoOS Launchpad product

## Integración con plugin ecosystem

- **`feature-to-spike` skill**: el command es wrapper — skill es donde vive la lógica + template del SPIKE
- **`startup-intake`, `cofounder-matching`, etc.**: typical source de learnings que generan SPIKEs
- **Linear MCP** (`mcp__linear-server__save_issue`): si configurado, enables direct file; requerido para full autopilot
- **GitHub Actions** (future): potentially auto-trigger este command desde `feature-to-spike` output durante dog-food sessions

## Ejemplo de salida

Al completar el flujo:

```
✓ SPIKE creado:

  ID: DOJ-3XXX
  Title: "SPIKE: Reorder intake form sections — Traction before Competitive"
  Assignee: William Ugalde
  Parent: DOJ-3189
  State: Triage
  URL: https://linear.app/dojo-coding/issue/DOJ-3XXX

  Linked artifacts:
  - ./launchpad/acme-inc/startup-profile.md
  - ./launchpad/spikes/2026-04-16-reorder-intake-sections-filed.md

Next step: William triage cuando tenga queue disponible. No action requerida por tu parte.
```

## Recursos

- **`feature-to-spike` skill** (`skills/feature-to-spike/SKILL.md`) — lógica + template del SPIKE body
- **`references/productization-workflow.md`** — 5-step loop methodology → SPIKE → DojoOS feature
- **Linear MCP docs** — `mcp__linear-server__save_issue` para direct file
- **DojoOS Launchpad pillar ownership** (Slack 2026-04-10 `#C0AKTN24C91`): @juan + @daniel → @william
