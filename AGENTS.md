# Demo Inscripciones

Demo docente en Django + SQLite: alumnos se inscriben a actividades con cupo.
El vocabulario del dominio está en `GLOSSARY.md`.

## Worktrees

Cada ticket se implementa en su propio worktree: `scripts/worktree.sh <nombre> [ref-base]`
crea la rama `ticket/<nombre>` con el `.venv` del repo enlazado; `--remove <nombre>`
lo limpia.

## Agent skills

### Issue tracker

Specs y tickets se guardan como Markdown local bajo `.scratch/`. Ver `docs/agents/issue-tracker.md`.

### Triage labels

Se usan las cinco etiquetas canónicas de triage con sus nombres predeterminados. Ver `docs/agents/triage-labels.md`.

### Domain docs

El repositorio usa un único contexto de dominio. Ver `docs/agents/domain.md`.
