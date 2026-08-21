# MVP Roadmap

The MVP is delivered through four sequential phases. Each phase produces
an independently useful result and reduces a specific risk before the next
phase begins.

The roadmap stops after the first validated team metric and local app. More
metrics, teams, players, competitions, statistical relationships, and
counterfactual analysis require a later roadmap revision.

## Phase 1: Validate the Dataset

### Objective

Choose a small StatsBomb competition and season and understand whether its
files contain the data required for the MVP.

### Expected Outcome

A reproducible local data report describing the selected files, matches,
teams, players, event types, available coordinates, and data-quality gaps.

### Dependencies

- StatsBomb Open Data files.
- A working local Python environment.

### Major Tasks

- Confirm the selected competition and season.
- Inspect competition, match, lineup, and event file structures.
- Identify relevant identifiers, event attributes, and coordinate fields.
- Record source files and available version or date information.
- Produce basic counts and per-match summaries.
- Identify whether recovery events and attacking-direction information are
  available.

### Tests or Verification

- Load representative files successfully.
- Report a clear error for an unreadable or malformed file.
- Verify counts and groupings with small hand-checked examples.
- Confirm that missing fields are reported rather than treated as data.
- Re-run the report with the same files and compare the output.

### Decisions That May Be Required

- Which competition and season provide the best first case study?
- Which files are included in the MVP dataset?
- Which event records qualify as recoveries?
- Can field direction be normalised reliably for this data?

### Definition of Done

- The selected dataset is documented and stored locally.
- The data report is reproducible.
- Required fields and known gaps are recorded.
- The dataset is either suitable for `recovery height` or the metric
  definition is revised before implementation.

## Phase 2: Define and Calculate Recovery Height

### Objective

Turn the first tactical question into a transparent, tested descriptive
metric.

### Expected Outcome

A documented calculation that returns recovery height per team and match,
with the number of observations used and explicit unavailable-data cases.

### Dependencies

- Phase 1 dataset report.
- Confirmed event semantics and coordinate availability.
- The metric definition in `docs/metrics/recovery-height.md`.

### Major Tasks

- Finalise the qualifying recovery event definition.
- Finalise coordinate scale and attacking-direction treatment.
- Define exclusions and missing-data behaviour.
- Calculate the match-level value and observation count.
- Preserve source identifiers needed for traceability.
- Write a short manual validation record for selected matches.

### Tests or Verification

- Test normal recoveries and expected values.
- Test missing coordinates and empty input.
- Test invalid or incomplete events.
- Test both field orientations.
- Test observation counts and unavailable results.
- Compare selected outputs with manually calculated examples.

### Decisions That May Be Required

- Mean, median, or another summary statistic.
- Minimum observation threshold for displaying a summary.
- Whether the metric should be called `recovery height` for the selected
  event definition.

### Definition of Done

- The metric has a written definition and limitations.
- The calculation is independent of the user interface.
- Tests cover its main cases and relevant edge cases.
- A small manually reviewed sample produces plausible results without
  being presented as proof of tactical validity.

## Phase 3: Build the Local Team Analysis App

### Objective

Make the validated analysis usable without changing source code for each
selection.

### Expected Outcome

A local app where the user selects a competition, season, and team and sees
the team's match-level recovery-height results.

### Dependencies

- Phase 1 data loading and validation.
- Phase 2 metric calculation.
- A local Python environment with the chosen app and chart dependencies.

### Major Tasks

- Add controls for competition, season, and team selection.
- Show team matches, opponents, scores, and data-quality information.
- Show recovery height and observation count per match.
- Add one basic chart showing metric variation.
- Display the metric definition and limitations in the team view.
- Keep presentation separate from loading and calculation logic.

### Tests or Verification

- Start the app locally with the documented command.
- Select the documented case-study team and verify its matches appear.
- Verify that unavailable data is visible and not displayed as zero.
- Compare displayed values with Phase 2 outputs.
- Check that the app handles an invalid or incomplete selection clearly.

### Decisions That May Be Required

- The simplest useful table and chart for the metric.
- Whether the app should show only the case-study dataset or allow a small
  set of documented selections.
- How much source provenance should be visible in the initial interface.

### Definition of Done

- The app runs locally.
- A user can select the documented competition, season, and team.
- The team view shows context, match-level results, observation counts,
  one chart, and metric limitations.
- The app does not contain metric formulas or data-loading logic in its
  presentation code.

## Phase 4: Reproduce and Review the MVP

### Objective

Confirm that the complete MVP is understandable, reproducible, and useful
for learning from the selected case study.

### Expected Outcome

A documented end-to-end workflow that another developer can run locally
and use to inspect the first team metric.

### Dependencies

- Completed Phases 1 to 3.
- Documented local setup and execution steps.

### Major Tasks

- Document how to obtain or place the StatsBomb files.
- Document how to run the app and tests.
- Review the metric explanation for clarity.
- Perform a final manual review of a small match sample.
- Record known limitations and unresolved questions.
- Check that the requirements and implementation still agree.

### Tests or Verification

- Run the complete automated test suite.
- Run the app from a clean local environment or documented setup.
- Re-run the same analysis and compare results.
- Verify the MVP acceptance criteria in `docs/requirements.md`.
- Ask whether a learner can distinguish observed data from derived values.

### Decisions That May Be Required

- Whether the metric is sufficiently useful to justify a second metric.
- Which limitation must be resolved before expanding the dataset.
- Whether the next increment should add another team, another metric, or
  better validation.

### Definition of Done

- The MVP acceptance criteria are satisfied.
- The workflow is reproducible and documented.
- The first metric's interpretation and limitations are explicit.
- No future feature has been added without a concrete validated need.

## Later Roadmap Revision

After Phase 4, revise the roadmap using evidence from the MVP. Possible
next increments include additional metrics, comparison across teams,
player-level views, or broader competition coverage. Statistical
relationships and counterfactual scenarios must remain separate decisions
with their own data and validation requirements.
