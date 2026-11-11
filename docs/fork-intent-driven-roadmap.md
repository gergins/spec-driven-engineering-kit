# Intent-driven engineering integration roadmap

> Status: proposed architecture, not an implementation claim.
> Baseline: fork of `github/spec-kit` at `40dd00f39763ccf653ccb18deb684d006f522176` (2026-11-11).
> Execution policy: local verification only; no GitHub Actions, merge or deployment without explicit authorization.

## Outcome

Accept a human goal, choose a proportionate method, produce linked intent/specification/plan/tasks, execute a safe vertical slice, and report evidence of actual working behavior. This fork must remain functional without other repositories or remote services.

## Reuse before building

The upstream README documents independent development, bug-fixing, and idea-assessment processes; its extension, preset, workflow, workflow overlay, bundle, catalog, artifact inventory, and project-local override mechanisms are preferred integration points.

1. Preserve the upstream CLI and license; avoid changes to core command behavior in the first milestone.
2. Experiment first with a project-local configuration, preset or opt-in extension, using the narrowest upstream mechanism capable of the outcome.
3. Treat external project intelligence, method registries, orchestration and assurance as optional adapters; absence of any one must not block local specification or task creation.
4. Keep human authorization gates around secrets, costs, production deployment, destructive operations, or security-sensitive changes. Safe, reversible work may proceed within authorized scope.
5. Preserve the upstream Git history and allow upstream sync. Keep custom artifacts namespaced and document compatibility before touching upstream-owned files.

## Milestones and acceptance evidence

| Milestone | Deliverable | Acceptance evidence |
| --- | --- | --- |
| M0: Baseline | Upstream inventory and local test baseline | Exact revision, environment, selected test commands, observed results; note gaps |
| M1: Intent capture | Machine-readable, versioned intent with outcome, constraints, uncertainty and provenance | Positive/negative local tests; old documents remain readable |
| M2: Spec Kit bridge | Deterministic intent-to-Spec-Kit specification handoff | Generated spec passes structural validation; source mapping recorded |
| M3: Adaptive method selection | Explainable selector for SDD, bugfix, idea assessment, or project-local custom workflow | Table-driven tests for selection and safe fallback; no invented process capability |
| M4: Linked tasks | Requirement-to-task references, dependency ordering and change impact | Changing a requirement flags affected tasks without modifying unrelated work |
| M5: Execution adapter | Opt-in coding-agent task execution and local preview handoff | End-to-end local fixture, run logs and exact-revision evidence; failure restores previous state |
| M6: Assurance | Independent verification adapter, accessibility/security checks and recovery state | Positive/negative tests; explicit unverified status on missing checks |
| M7: Productization | Installability, contributor guide, compatibility, distribution and operation guidance | Clean-install smoke test, upgrade/rollback example, license notices |
| M8: Learning | Feedback and improvement metrics without intrusive collection | Reproducible, opt-in measurement and evidence-backed changes |

No milestone is considered implemented simply because a document exists.

## First executable vertical slice (M1 + M2)

**Scenario:** “Build a customer support application with login, user roles, tickets, status tracking, and a dashboard.”

- Inputs: human intent plus constraints; no credentials or network access required.
- Outputs: versioned intent artifact and a Spec Kit-compatible draft specification with stable requirement identifiers.
- Verification: a valid example produces traceable acceptance criteria; missing or conflicting required fields yields an explicit diagnostic and no silently assumed security behavior.
- Evolution: edit one requirement and show the affected specification references; unrelated requirements remain unchanged.
- Execution: run focused tests locally before exposing the feature as a preset, extension, or workflow step.

## Responsibilities, not mandatory dependencies

- **spec-driven-engineering-kit:** intent/specification/task contracts and opt-in Spec Kit integration.
- **ai-app-builder:** user-facing visual workspace, preview, user approvals and execution UX.
- **engineering-knowledge-registry:** optional method knowledge and templates.
- **universal-project-intelligence:** optional context and relationship information.
- **product-engineering-operating-model:** optional operating guidance, never a blocking dependency.
- **engineering-assurance-engine:** optional independent local verification and recovery.

Adapters must fail safely and clearly while retaining project-local progress.

## Immediate next engineering steps

1. Clone the fork locally and register `github/spec-kit` as the `upstream` remote.
2. Inspect installed extension/preset/workflow schemas and examples; choose the least invasive integration path.
3. Capture a baseline with the worktree's own Python environment (Python 3.11+ and `uv` per upstream documentation).
4. Implement a minimal intent contract and deterministic tests on a feature branch.
5. Run focused local tests, then broader local checks; report pass/fail with exact commit and environment.
6. Open a draft PR for review only after reporting verified evidence; do not merge automatically.

## Guardrails

- Preserve upstream MIT copyright and license notices; separately document licenses for any added dependencies.
- Respect `AGENTS.md` and `CONTRIBUTING.md`, including Windows PowerShell 5.1 support and AI-assisted commit disclosure.
- Never claim CI success when only local tests were run.
- Prefer safe fallbacks, reversible changes, and observable outputs over new governance dependencies.
