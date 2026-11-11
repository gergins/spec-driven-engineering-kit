# M0 integration decision and local baseline

Status: source inspection complete; runtime verification pending.

## Observed at fork baseline

- Fork `gergins/spec-driven-engineering-kit` and upstream `github/spec-kit` share main HEAD `40dd00f39763ccf653ccb18deb684d006f522176` at inspection.
- `README.md` provides SDD, opt-in bug fixing, idea assessment, extension, preset, workflow, bundle and artifact mechanisms.
- `docs/presets/overview.md`: presets change existing templates/commands/scripts, and support project-local overrides.
- `docs/extensions/overview.md`: extensions add new commands and tool integrations.
- `docs/workflows/overview.md`: YAML workflows have review gates, persisted run IDs and resume. They are **not** GitHub Actions.
- `docs/workflow-steps/developing.md`: custom Python steps are executable and must be treated as trusted code.
- `pyproject.toml`: Python >=3.11, `uv` workflow, pytest tests; CLI version 1.4.1.dev0 at the inspected commit.
- `AGENTS.md` mandates PowerShell 5.1 compatibility and local worktree interpreter; `CONTRIBUTING.md` mandates positive and negative tests for executable behavior.

## Decision

For M1, implement **a small namespaced intent-contract module with a deterministic validator and tests**, rather than rewriting CLI internals or installing an executable third-party extension.

For M2, expose a draft specification through an **opt-in extension** if it adds a new command. Use a **preset** only for changing existing templates and a **workflow** only once multiple independently verified steps need orchestration. Do not add a competing engine.

Always preserve a local-first path. An absent AI coding agent or external registry must produce an explicit handoff or limitation, not fabricated implementation success.

## Local Windows baseline instructions

In Windows PowerShell (from a normal user directory, never `C:\`):

```powershell
$project = Join-Path $HOME 'Projects\spec-driven-engineering-kit'
New-Item -ItemType Directory -Force (Split-Path $project) | Out-Null
if (-not (Test-Path (Join-Path $project '.git'))) {
  git clone https://github.com/gergins/spec-driven-engineering-kit.git $project
}
Set-Location $project
git remote -v
if (-not (git remote | Select-String '^upstream$')) {
  git remote add upstream https://github.com/github/spec-kit.git
}
git fetch origin
git switch docs/intent-driven-integration-roadmap
git pull --ff-only origin docs/intent-driven-integration-roadmap
git status --short
git rev-parse HEAD
python --version
uv --version
uv sync --extra test
.\.venv\Scripts\python.exe -m pytest tests -q
```

The tests execute repository code. Inspect the checkout before running if it is not trusted. Do not run CI. Preserve full command output and exit status as evidence. If `python` or `uv` is unavailable, report the missing dependency; do not claim successful verification.

## Remaining M0 acceptance

- [x] Source layout and upstream mechanisms inspected using GitHub API.
- [x] Exact fork/upstream source commit compared.
- [x] Non-invasive M1/M2 integration strategy chosen.
- [ ] Local checkout and full dependency environment confirmed.
- [ ] Focused and broader local tests run with exit codes.
- [ ] Exact-head baseline report recorded.

Next implementation requires passing baseline or a precisely documented blocker.
