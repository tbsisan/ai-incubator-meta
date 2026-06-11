# Schema v1: AI Incubator Meta

## Purpose

This schema defines how the `ai-incubator-meta` project should structure self-review outputs, parent-repo improvement proposals, and mature-project pass results.

The goal is to let the incubator reason about itself without uncontrolled self-modification.

## Core Record Types

### 1. System Snapshot

A bounded summary of selected parent repo state used as input to a self-review pass.

```json
{
  "snapshot_id": "2026-06-05-current-system",
  "created_at": "2026-06-05T05:00:32Z",
  "scope": "selected_files",
  "source_files": [
    "README.md",
    "incubator.yaml",
    "scripts/run_pass.py",
    "scripts/intake_idea.py",
    "prompts/idea_intake_pass.md"
  ],
  "summary": "Short description of current capabilities and known constraints.",
  "known_limitations": [
    "No mature-project pass types yet.",
    "No automated parent-file snapshot helper yet."
  ],
  "excluded_context": [
    "Full workshop logs",
    "Unrelated idea folders",
    "Secrets or credentials"
  ]
}
```

### 2. Improvement Opportunity

A candidate improvement to the incubator as a built system.

```json
{
  "opportunity_id": "opp-product-health-review-pass",
  "title": "Add product_health_review pass",
  "type": "pass_type",
  "target_area": "prompts/incubator.yaml/README",
  "user_value": "Lets built projects get grounded health audits without being treated as raw ideas.",
  "scope": "small",
  "reversibility": "high",
  "risk": "low",
  "evidence_status": "inferred_from_current_workflow",
  "validation_test": "Run the pass against ai-incubator-meta and check whether it produces concrete, non-generic recommendations.",
  "recommended_next_step": "Draft prompt and add config mapping."
}
```

### 3. Parent Change Proposal

A safe proposed change to files in the parent repo.

```json
{
  "proposal_id": "prop-model-profile-docs",
  "created_at": "2026-06-05T05:00:32Z",
  "status": "proposed",
  "target_files": [
    "README.md",
    "incubator.yaml"
  ],
  "rationale": "Explain why the change improves the incubator.",
  "change_type": "docs_and_config",
  "risk_level": "low",
  "rollback_plan": "Revert the patch in git.",
  "proposed_diff_summary": [
    "Add model profile selection docs.",
    "Add default model aliases."
  ],
  "approval_required": true
}
```

### 4. Mature Project Pass Result

Standard result shape for built/stable project passes.

```json
{
  "pass_type": "opportunity_scan",
  "project_slug": "ai-incubator-meta",
  "created_at": "2026-06-05T05:00:32Z",
  "model": "provider/model-or-profile",
  "preserve_core": [
    "File-backed project folders",
    "Append-first workflow",
    "Canonical edits require review",
    "Prompt dry-run capability"
  ],
  "findings": [
    {
      "finding": "Built projects need opportunity/feature passes that do not reset the project to zero.",
      "severity": "medium",
      "evidence": "User requested built-project brainstorming for new features and market opportunities.",
      "recommendation": "Start with opportunity_scan and feature_brainstorm; defer broader health-review pass design."
    }
  ],
  "recommended_actions": [
    {
      "action": "Run opportunity_scan pass",
      "effort": "small",
      "risk": "low",
      "expected_value": "high"
    }
  ],
  "do_not_do": [
    "Do not load the entire parent repository into every meta pass.",
    "Do not directly rewrite parent files from a meta pass."
  ]
}
```

## Controlled Vocabularies

### Opportunity Types

- `pass_type`
- `prompt_improvement`
- `persona_improvement`
- `runner_feature`
- `intake_workflow`
- `model_selection`
- `reference_library`
- `documentation`
- `safety_policy`
- `project_structure`
- `productization`
- `distribution`

### Target Areas

- `incubator.yaml`
- `scripts/run_pass.py`
- `scripts/intake_idea.py`
- `prompts/*.md`
- `personas/*.md`
- `references/`
- `templates/`
- `README.md`
- `ideas/<slug>/`
- `skills/memory`
- `external_workflow`

### Evidence Status

- `observed_in_current_system`
- `user_requested`
- `inferred_from_current_workflow`
- `hypothesis`
- `needs_test`

### Risk Levels

- `low`
- `medium`
- `high`

### Reversibility

- `high`
- `medium`
- `low`

## Promotion Policy

Meta-project outputs may propose parent repo changes, but should not directly apply them unless Tom explicitly asks.

Default lifecycle:

1. Append pass output to `ideas/ai-incubator-meta/workshop_log.md`.
2. Extract promising recommendations into a parent change proposal.
3. Review proposed target files and diff.
4. Apply approved patches to parent files.
5. Verify behavior.
6. Commit to git.

## Context Policy

Self-review should use curated context, not the entire parent directory.

Preferred context inputs:

- `brief.md`
- `scorecard.md`
- `schema-v1.md`
- relevant excerpts from parent files
- concise current-system snapshots
- selected recent workshop log entries only when needed

Avoid by default:

- full historical logs
- all `ideas/` folders
- secrets, credentials, or environment-specific files
- generated temporary output

## First Mature-Project Passes

The schema anticipates these general pass types for built/stable projects:

- `opportunity_scan` — identify feature, market, workflow, and distribution opportunities without reinventing the project.
- `feature_brainstorm` — generate constrained new-feature ideas tied to current users and architecture.
- Later/deferred: broader pass types such as `product_health_review` or `market_expansion` should be workshopped further before being added.

These should be general and usable by any built project, not just the incubator.
