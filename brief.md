# Idea: AI Incubator Meta

## Core

### Mission

Make the AI Incubator itself more useful, safe, and compounding by workshopping it with the same file-backed, persona-driven process it provides for other projects.

### One-liner

A meta-project inside the AI Incubator that treats the incubator as a built product/system and generates safe, reviewable improvements to its workflow, prompts, personas, scripts, configuration, and documentation.

### What value does this create?

This creates a structured way to improve the incubator without relying on scattered chat decisions or ad hoc edits. It should help identify high-leverage features, workflow bottlenecks, confusing UX, missing pass types, weak prompts, model-selection problems, and safety issues while preserving the existing system’s core architecture.

### Target user

Primary user: Tom, as the builder/operator of the AI Incubator.

Secondary future users: other builders who want a local, file-backed, semi-autonomous system for turning raw ideas and existing projects into clearer plans, experiments, and implementation proposals.

### Proposed solution

Represent the incubator as a normal idea under `ideas/ai-incubator-meta/`, but do not point the runner at the repo root directly. Instead, use this folder as the source-of-truth workspace for self-review, with outputs stored in `workshop_log.md` and proposed changes promoted to parent repo files only after review.

---

## Shape

### MVP

Create the meta-project folder with canonical project files, set its stage to `built`, and run a mature-project pass such as `opportunity_scan` or `feature_brainstorm`. Hold off on a broad `product_health_review` pass until that shape has been workshopped further.

### Weird angle

The incubator becomes self-improving without becoming recursively unsafe: it can reason about itself as a project, but it only writes inside its own idea folder unless Tom explicitly approves promotion into root files.

### Variants

- **Self-review workspace:** use this folder to collect critiques, opportunities, and proposed diffs for the incubator.
- **Productization track:** treat the incubator as a possible reusable tool for other builders and explore packaging, UX, docs, and distribution.
- **Operations track:** use this folder to track system health, pass quality, model choices, context bloat, and maintenance risks.

---

## Tensions

### Risks

- Recursive context bloat if the project tries to ingest the entire parent repository or all prior logs.
- Unsafe self-modification if passes directly rewrite `incubator.yaml`, scripts, prompts, or personas without review.
- Confusing canonical state if meta-project outputs and parent implementation files disagree.
- Feature sprawl if the incubator keeps adding pass types and knobs before the core loop is stable.
- Overfitting to Tom’s current workflow while losing the generality that makes the incubator useful across projects.

### Open questions

- What mature-project pass types should exist beyond `opportunity_scan` and `feature_brainstorm`, if any?
- Should snapshots of parent files be generated manually or by a helper script?
- Which parent files should be included in a self-review prompt by default?
- What is the safest promotion workflow from meta-project proposal to parent repo patch?
- Should this incubator eventually have a UI or remain CLI/file-backed?

---

## Built-project constraints

The incubator already exists and should not be treated as a blank-slate startup idea. Passes for this project should preserve the current file-backed architecture unless there is a strong reason to change it.

Recommended constraints for future passes:

- Prefer additive, reversible, testable improvements.
- Do not propose wholesale pivots unless evidence clearly supports it.
- Do not directly edit root files from a meta pass.
- Store proposed root changes as markdown proposals or diffs first.
- Keep global config project-agnostic.
- Avoid adding pass types unless they represent a genuinely different job.

---

## Current thesis

The AI Incubator is now useful enough to become one of its own projects. The right architecture is not to make the repo root an idea folder, but to create a represented meta-project under `ideas/ai-incubator-meta/`. That gives the system a safe workspace for self-analysis while preserving a clear promotion boundary between meta-level recommendations and actual implementation changes.
