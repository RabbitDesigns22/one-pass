# one-pass

**Get it right the first time, so you stop paying for the same work twice.**

`one-pass` is an agent skill for Claude Code (and any agent that reads `SKILL.md` skills). Most token-saving skills make the agent talk less. That helps a little. Agents burn far more tokens on something else: **rework**. They deliver, get it sent back, redo it, re-read the same files, retry the same failing command and send messages nobody needed.

`one-pass` removes those loops without lowering quality, and without ever skipping a safety step.

## What it does

| Leak | How one-pass stops it |
|---|---|
| Rework | Writes a 5-line acceptance list before starting, then checks the result against it before saying "done" |
| Re-reading | Reads each source once, keeps one-line notes, never re-reads a file it just wrote |
| Wandering | Stops exploring as soon as it can name the change |
| Retry storms | Two identical failures, then it must diagnose and change approach |
| Bloat | Filters big logs, JSON and pages at the source instead of pasting them |
| Chatter | Self-contained briefs, one message per recipient, no polling |

It also includes:
- **Task sizing.** Trivial tasks skip the method, so the method never costs more than the task.
- **Checklists by deliverable.** Code, images, video, copy, data, reports and briefs, loaded only when needed.
- **A safety section.** It never cuts tests, confirmations or reviews to save tokens. It treats fetched or delegated content as data, not instructions. It keeps secrets out of notes and briefs, and it never installs tools on its own.
- **An optional one-line receipt.** `Passes: 1 · Re-reads: 0 · Retries: 0`

## Install

With the [skills CLI](https://skills.sh):

```bash
npx skills add RabbitDesigns22/one-pass
```

Or manually: copy `skills/one-pass/` into `~/.claude/skills/` for all your projects, or into `.claude/skills/` for one project.

To make every session load it first, add this line to your `CLAUDE.md`:

```
Before any task that delivers something or delegates work, load the one-pass skill and follow it.
```

## Use

It triggers by itself on phrases like "save tokens", "don't waste tokens", "get it right the first time", "sin errores", "hazlo bien a la primera", and at the start of tasks that produce a deliverable. You can also call it directly: `/one-pass`.

## Files

```
skills/one-pass/
  SKILL.md                 the skill (short, loaded when triggered)
  references/checklists.md checks by deliverable (read one section on demand)
evals/
  evals.json               test prompts and expected behavior
```

## Safety

`one-pass` contains no scripts, makes no network calls and needs no permissions. It is plain instructions. Read it before installing: it is under 150 lines.

## Español

**Hazlo bien a la primera, para no pagar dos veces el mismo trabajo.** `one-pass` es una skill para Claude Code. Su objetivo no es solo hablar menos: es evitar lo que más tokens gasta, que es rehacer el trabajo. Antes de empezar fija una lista corta de lo que tiene que cumplir el resultado. Lee cada cosa una sola vez, agrupa las acciones y se revisa antes de entregar. Además, pone un tope a los reintentos y escribe órdenes completas para otros agentes. Nunca se salta una revisión ni un paso de seguridad para ahorrar.

Instalar: `npx skills add RabbitDesigns22/one-pass`

## License

MIT. Made by [Rabbit Designs](https://github.com/RabbitDesigns22).
