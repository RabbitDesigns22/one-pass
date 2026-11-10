# one-pass

**Get it right the first time, so you stop paying for the same work twice.**

`one-pass` is an agent skill for Claude Code (and any agent that reads `SKILL.md` skills). Most token-saving skills make the agent talk less. That helps a little. Agents burn far more tokens on something else: **rework**. They deliver, get it sent back, redo it, re-read the same files, retry the same failing command and send messages nobody needed.

`one-pass` removes those loops without lowering quality, and without ever skipping a safety step.

## See the difference

> **You:** Make the 1080x1350 post for the cleaning company.

**Without the skill:** it designs at the wrong size, you send it back, it re-reads the same files, retries a failing export four times and redoes the post.

**With the skill:** it writes a 5-line acceptance list first (size, text, logo, colors, file), checks the finished file against that list and delivers once.

**Skip it if** the task is one line. The skill tells the agent to skip its own method on trivial tasks.

**Status:** in daily use in the author's own setup. Plain instructions, no scripts, no network calls. MIT. Issues and suggestions welcome.

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

## More skills from the same setup

These come from one real workflow: a small agency run with 15+ Claude Code sessions in parallel. Each skill fixes one problem that kept happening there.

| Skill | What it fixes |
|---|---|
| [hora-exacta](https://github.com/RabbitDesigns22/hora-exacta) | real date and time in every message, so nothing lands on the wrong day |
| [hands-on](https://github.com/RabbitDesigns22/hands-on) | the agent does what it can and only asks you for codes, keys and payments |
| [easy-for-them](https://github.com/RabbitDesigns22/easy-for-them) | steps people actually follow: direct link, one action per line |
| [one-answer](https://github.com/RabbitDesigns22/one-answer) | one thought-through answer instead of plan, fix, new plan |
| [never-twice](https://github.com/RabbitDesigns22/never-twice) | a shared error log so no session repeats a known mistake |
| [report-now](https://github.com/RabbitDesigns22/report-now) | status checked live this minute, stamped with the time |
| [sort-me-out](https://github.com/RabbitDesigns22/sort-me-out) | one ordered list of what is urgent, waiting and forgotten |
| [in-the-loop](https://github.com/RabbitDesigns22/in-the-loop) | a live board so parallel sessions know what the others changed |
| [study-first](https://github.com/RabbitDesigns22/study-first) | reads everything in full and answers point by point, no invented details |
| [session-watchdog](https://github.com/RabbitDesigns22/session-watchdog) | wakes the sessions that got stuck mid-task, leaves the rest alone |
| [skill-harvest](https://github.com/RabbitDesigns22/skill-harvest) | reads your sessions and finds the skills you are missing |
| [small-budget-ads](https://github.com/RabbitDesigns22/small-budget-ads) | Meta Ads rules for 1-5 USD a day ad sets |
| [whatsapp-closer](https://github.com/RabbitDesigns22/whatsapp-closer) | evidence-ranked rules for a WhatsApp sales assistant that closes |
| [whatsapp-number-onboarding](https://github.com/RabbitDesigns22/whatsapp-number-onboarding) | connect a number to the WhatsApp Cloud API in the safe order |
| [proposal-pdf](https://github.com/RabbitDesigns22/proposal-pdf) | short PDF proposals with every price checked against its source |
| [published-vs-planned](https://github.com/RabbitDesigns22/published-vs-planned) | says "published" only for what it saw live on the public page, Facebook and Instagram checked apart |
| [source-every-fact](https://github.com/RabbitDesigns22/source-every-fact) | every price, phone and name on a post traced to its source, nothing added |
| [only-what-was-asked](https://github.com/RabbitDesigns22/only-what-was-asked) | "pause only Google Ads" pauses only Google Ads, and proves the rest did not move |

If one of them saved you a redo, a star helps other people find it.

## License

MIT. Made by [Rabbit Designs](https://github.com/RabbitDesigns22).
