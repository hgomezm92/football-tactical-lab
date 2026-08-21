# MVP Requirements

## Project Goal

Football Tactical Lab is a local, educational application for learning
how football can be analysed from event data.

The MVP must transform a documented selection of StatsBomb Open Data into
an understandable profile of one team in one competition and season. It
must begin with one transparent metric: **recovery height**.

Recovery height describes where a team recovers possession when usable
spatial information is available. It must not be presented as a direct
measurement of pressing height or as evidence of a causal effect on match
outcomes.

The MVP prioritises understanding, reproducibility, and validation over
breadth of coverage or predictive power.

## Product Evolution

This document defines the current MVP, not the complete product vision.
The requirements should evolve after each phase has produced a validated
result.

Later phases may extend the application to:

- additional documented metrics;
- comparisons between teams and across matches;
- player-level analysis where the data supports it;
- more competitions and seasons;
- statistical analysis of relationships between metrics.

Each new metric or analysis must have its own definition, data
requirements, limitations, and tests before it becomes part of the
product. The current MVP provides the workflow and evidence needed to
extend the application safely; it is not intended to limit the final
number of metrics, teams, or players.

## Target Users

### Primary user

The project owner, who is learning software development, football data
analysis, metric design, and basic statistical reasoning.

### Possible future users

Football analysts, coaches, researchers, or advanced fans may use the
application later. Their needs must not expand the MVP scope.

## Core Use Cases

The primary user must be able to:

1. Select a documented StatsBomb competition and season.
2. Select a team from that dataset.
3. Inspect the available matches and data quality for the selection.
4. View the team's recovery height by match.
5. Understand how the metric is defined, calculated, and limited.
6. Use tables and basic charts to inspect the metric's variation.
7. Re-run the same analysis and obtain the same result.

## Functional Requirements

### Dataset selection and provenance

- The application must support a small, documented selection of StatsBomb
  Open Data.
- The selection must identify the competition, season, source files, and
  matches included.
- The analysis must record available source version or date information.
- The application must report missing, optional, or incomplete data.

### Data loading and validation

- The application must load the competition, match, lineup, and event data
  needed by the selected analysis.
- It must preserve the source identifiers and values needed to interpret
  the results.
- It must handle optional or missing fields explicitly.
- Invalid or unreadable input files must produce a clear, useful error.
- The analysis must not silently treat missing values as observed values.

### Team selection and context

- The user must be able to select one team from the selected competition
  and season.
- The team view must identify the matches included in the analysis.
- It must show available opponents and score information.
- It must show the number of matches and observations used for the metric.

### Recovery height metric

- The MVP must calculate recovery height for the selected team and each
  included match where the required data is available.
- The metric must use only qualifying recoveries with usable coordinates.
- The calculation must account for the attacking direction or document why
  direction cannot be normalised for the selected data.
- The metric definition must state its unit of analysis, included events,
  exclusions, missing-data handling, and limitations.
- The application must distinguish recovery height from pressure height.

### Results and explanation

- The team view must show recovery height by match in a table.
- It must show at least one basic visual summary of the metric's variation.
- It must show the number of recoveries used alongside metric values.
- It must explain what the metric can and cannot support as an
  interpretation.
- Results must distinguish observed source data from derived values.

### Reproducibility

- The same input files, selection, and documented process must produce the
  same results.
- The analysis must be executable in a local development environment.
- The selected inputs and relevant assumptions must be traceable from the
  result.

### Tests

- The metric logic must have tests using small, representative examples.
- Tests must cover normal input, missing coordinates, field orientation,
  empty input, and invalid or incomplete events.
- Tests must verify both calculated values and observation counts.

## Important Non-Functional Requirements

- **Understandability:** A developer learning data analysis must be able
  to follow the analysis and understand the metric.
- **Transparency:** Definitions, assumptions, transformations, and
  limitations must be visible rather than hidden behind a single score.
- **Reproducibility:** Repeated analyses with the same inputs must be
  deterministic.
- **Traceability:** Results must retain links to source identifiers and
  clearly separate observations from calculations.
- **Data quality visibility:** Missing or incomplete data must be reported.
- **Maintainability:** The solution must remain small, readable, and easy
  to extend with another metric later.
- **Local usability:** The MVP must run on a local development environment
  without external services.

## Constraints

- Use StatsBomb Open Data as the initial data source.
- Use only free data and local execution for the MVP.
- Start with one well-documented competition, season, and team.
- Support only the data fields required by the selected analysis.
- Keep the application simple enough to inspect and understand while
  learning.
- Do not assume that event data captures every tactical action or context.

## Assumptions

- At least one StatsBomb competition and season provides enough match,
  lineup, and event data for a useful case study.
- Relevant recovery events and coordinates are available for part of the
  selected sample.
- The source data's coordinate system and event semantics can be inspected
  and documented before the metric is finalised.
- A recovery location is a useful first approximation for studying where a
  team regains possession, but it is not a complete measure of pressing.
- A single team case study is sufficient to validate the first version of
  the data and metric workflow.
- Manual review of a small number of matches can provide an initial sanity
  check, but cannot prove tactical validity.

These assumptions must be revised if inspection of the selected data
shows that they are false.

## Explicitly Out of Scope

The MVP must not include:

- a complete tactical identity or style score for a team or player;
- presenting recovery height as pressure height;
- a weighted index combining several tactical metrics;
- a second metric unless it is required to validate the first workflow;
- broad support for all StatsBomb competitions and seasons;
- player profiles beyond basic data needed for context;
- causal claims such as proving that higher pressing causes more xG;
- predictive models or machine learning;
- counterfactual scenarios, tactical recommendations, or match simulation;
- statistical modelling of relationships between metrics;
- additional commercial or paid data sources;
- real-time data, user accounts, collaboration, or public deployment;
- complex databases, Docker, Kubernetes, microservices, MCP, or specialised
  agents.

## Acceptance Criteria

The MVP is complete when:

1. A documented competition, season, team, and set of source files can be
   selected locally.
2. The application loads the required data or returns a clear error.
3. The selected team and its analysed matches are identifiable.
4. Data quality issues and missing metric inputs are visible.
5. Recovery height is calculated per match using the documented definition.
6. Each result includes the number of recoveries used.
7. The team view includes a table and a basic visual summary.
8. The application explains the metric's meaning and limitations.
9. Tests pass for the metric's main cases and relevant edge cases.
10. Re-running the analysis with the same inputs produces the same results.
11. A small sample of matches has been manually reviewed as an initial
    sanity check, with the limitations of that review documented.