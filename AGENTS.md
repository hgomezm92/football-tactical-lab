# Football Tactical Lab - Agent Instructions

## Project Context
Personal project for learning AI-assisted development while building a
local football analysis tool using **StatsBomb Open Data**. Planned MVP: a
local Streamlit application with one metric (`recovery height`) for one
team, competition, and season.

## Key Documentation (read these first)
- `docs/architecture.md` — MVP architecture, data flow, recommended stack (Python/pandas/Streamlit/Plotly/pytest)
- `docs/requirements.md` — functional/non-functional requirements, acceptance criteria
- `docs/metrics/recovery-height.md` — provisional metric definition,
  calculation rules, and limitations
- `.github/copilot-instructions.md` — **authoritative** development principles, conventions, and working methods

## Current State
- No code implemented yet (planning phase)
- No test suite, no dependencies installed
- Data: local StatsBomb JSON files (not yet in repo)

## Architecture Notes
- Python stack: pandas, Streamlit, Plotly, pytest, venv
- Local-only execution, no external services
- Separate responsibilities for data loading and validation, metric
	calculations, analysis and aggregation, and interface presentation
- Traceability: source IDs preserved through transformations

Follow `.github/copilot-instructions.md` for general development, testing,
documentation, language, Git, and communication conventions.

## Metric Guidance

`recovery height` is a provisional MVP metric. Its event definition and
calculation must be confirmed against the selected StatsBomb data before
implementation. It must not be treated as a direct measurement of
pressing height.

## When Code Exists (update this file)
- Exact commands (venv setup, run app, run tests, lint/typecheck if added)
- Entry points and module structure
- Test organization and how to run focused tests