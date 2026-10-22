# Aegis Research Workflow

A written operating system for running **real literature-research projects with several AI
agents**: who does what, in which order, with which gates, and what counts as done.

It is documentation, not code. There is nothing to install — you copy these files into a
project and follow them.

## What it covers

- **Eight-stage pipeline** — research scope → literature discovery → corpus construction →
  evidence matrix → framework review → drafting → citation audit → final review, each with
  an owner and — where it matters — a gate. Simple projects are explicitly allowed to merge
  stages.
- **Four roles with routing rules** — a coordinator (Hermes), a design/review agent
  (Claude Code), an execution agent for bulk/mechanical work (Pi), and an implementation
  agent for code and local operations (Codex). Routing is by "who is best suited", not
  "who is available".
- **Three-level acceptance** — `AGENT_PASS` ≠ `STAGE_PASS` ≠ `PROJECT_PASS`. The
  coordinator must verify real artifacts; an agent's own claim of success is not evidence.
- **Evidence policy** — how literature claims must be verifiable (source, date, DOI/URL),
  how to mark contested findings, and what an "evidence package" handed to a reviewer must
  contain so the reviewer does not invent numbers.
- **Cost and context rules** — quota/retry/fallback behaviour, when to compact a session,
  and why project files (not the chat log) are the source of truth.
- **Task batching and dispatch checks** — when to merge several small tasks into one batch
  for a worker instead of micromanaging it step by step.

## Tech stack

Plain Markdown. No scripts, no dependencies, no service. Designed to sit in a repository
next to a research project and be read by both humans and agents.

## Files

| File | Purpose |
| --- | --- |
| `WORKFLOW.md` | Eight stages, phase gates, context management |
| `AGENT_ROUTING.md` | Role split, routing judgement, task batching, dispatch check |
| `QUALITY_GATES.md` | Stage acceptance and the three-level PASS model |
| `EVIDENCE_POLICY.md` | Claim verification and the evidence package |
| `COST_QUOTA_CONTEXT.md` | Quota, retry, fallback, context and cost rules |
| `RESEARCH_TASK_TEMPLATE.md` | Work order template for an execution agent |
| `DECISIONS.md` | The decisions behind v0.2 / v0.2.1 and why they were made |
| `TEST_PLAN.md` | The v0.2 validation baseline (kept as recorded) |
| `FUTURE_OBSERVATIONS.md` | Recognised but deliberately unhandled improvements |

## How to use it

1. Read `WORKFLOW.md` and `AGENT_ROUTING.md` first.
2. Copy `RESEARCH_TASK_TEMPLATE.md` for each unit of work you hand to a worker.
3. At the end of every substantial stage, write a checkpoint and update the project state
   file — the chat is not the database.
4. Before declaring a project finished, walk `QUALITY_GATES.md` and produce your own
   `PROJECT_PASS` from the real artifacts.

## Current limitations

- **It is a process spec, not an automation.** Nothing here runs itself; enforcement is a
  human/coordinator discipline.
- **Validated on one real project so far.** The v0.2 baseline comes from a single
  scaled-down review-scheduling test (2026-09-11), recorded in `TEST_PLAN.md`. v0.2.1 is a
  maintenance patch on top of that and **has not yet been re-validated** on a new project.
- **Role names assume a specific local setup** (Hermes as coordinator, Claude Code / Pi /
  Codex as workers). The reasoning transfers; the tool names do not.
- **No metrics.** Cost/quality gains are argued from observation, not measured across
  projects.
- **Chinese-language document.** The workflow is written in Chinese; terminology is
  consistent with that environment.

## Verification status

`TEST_PLAN.md` records what was actually observed in the v0.2 test run: Claude Code joined
for upfront design and review, Pi built the corpus and evidence matrix (artifacts checked by
hand), Codex was legitimately not needed, and two failure modes were found and written into
the rules — the designer mis-assigning executors, and a worker bridge reporting `status=ERROR`
while its artifacts were in fact correct. Those findings are the reason "verify artifacts,
not status" is a rule rather than a preference.

Nothing in this repository claims more than that single validated run.

## License

No license has been declared for this repository yet, which means all rights are reserved by
default. Ask before reusing it.
