# Workshop Log: AI Incubator Meta

## Usage notes

- This project represents the AI Incubator as a built system inside its own `ideas/` directory.
- Outputs here may critique or propose changes to parent repo files, but should not directly rewrite them.
- Promote changes to parent files only after review, preferably as explicit proposed diffs.
- Keep self-review bounded: use curated snapshots and targeted files instead of ingesting the full repo recursively.

---

## 2026-06-05T05:00:32Z — bootstrap — Hermes / GPT-5.5 via OpenAI Codex

### Goal

Create the initial meta-project files so the AI Incubator can be workshopped using its own file-backed process.

### Inputs considered

- Tom's request to add `ai-incubator-meta` as an idea inside the incubator.
- Current incubator design: `ideas/<slug>/` folders, pass prompts, personas, model profiles, `run_pass.py`, `intake_idea.py`, append-only logs, and canonical-edit discipline.
- Prior design decision: represent the parent system inside an idea folder rather than making the repo root itself the idea.

### Key observations

- The incubator is now a built local system, not merely a concept.
- It needs mature-project passes that preserve current identity while finding features, markets, UX improvements, workflow improvements, and health risks.
- A meta-project boundary keeps self-improvement safe by separating analysis/proposals from parent repo edits.

### New ideas / variants

- Add `opportunity_scan` for feature, workflow, market, and distribution opportunities.
- Add `feature_brainstorm` for grounded feature expansion without generic bloat.
- Defer broader pass types like `product_health_review` and `market_expansion` until their scope has been workshopped further.
- Add a future snapshot helper that summarizes selected parent files into meta-project context.

### Risks / objections raised

- Recursive context bloat if self-review loads the entire parent repo.
- Unsafe self-modification if meta passes directly patch root files.
- Pass sprawl if mature-project workflows are over-split too early.
- Confusion if meta-project state diverges from actual parent implementation.

### Questions surfaced

- Should `opportunity_scan` or `feature_brainstorm` run first for this project?
- What narrower jobs, if any, should later split out from these two passes?
- What parent-file snapshot should be included by default in self-review?
- Should proposals live in `workshop_log.md` only, or should this project eventually have a `proposals/` folder?

### Recommended updates to brief

- Treat the incubator as a built project with self-improvement constraints.
- State explicitly that meta passes can propose parent changes but should not directly apply them.

### Recommended next action

Run `opportunity_scan` against `ai-incubator-meta`, then use `feature_brainstorm` if the opportunity scan identifies feature-level improvements worth exploring.
