# MVP Requirements

## Scope

The MVP covers only Phase 1: understanding a small selection of
StatsBomb Open Data. It is a local, reproducible exploration exercise,
not a complete match-analysis product.

## Goal

The MVP must make it possible to inspect the structure and contents of a
selected set of StatsBomb Open Data and produce a basic descriptive
report about that selection.

## Functional Requirements

### Dataset selection

- The user must be able to identify the StatsBomb Open Data files being
  explored.
- The selected dataset must be small enough to inspect and process
  locally.
- The report must record the selection used so that the result can be
  reproduced.

### Data loading

- The MVP must load competition, match, lineup, and event data when
  those files are present in the selected dataset.
- It must preserve the source data values needed for the report.
- It must handle optional or missing fields without silently treating
  them as observed values.
- Invalid or unreadable files must produce a clear error.

### Descriptive report

The report must include, for the selected dataset:

- number of competitions and seasons;
- number of matches;
- number of teams;
- number of players when player data is available;
- number of events;
- counts by event type;
- a per-match summary identifying the participating teams and available
  score information;
- a basic indication of missing or incomplete data.

### Reproducibility

- The same input files and the same documented process must produce the
  same report.
- The report must identify the date or version information available for
  the input data.
- The process must be executable on a local development environment.

## Quality Requirements

- The data exploration process must be understandable to a developer who
  is learning data analysis.
- Important assumptions about the source data must be documented.
- The process must distinguish source observations from values derived
  by counting or grouping.
- The project must use only free data and local execution for this MVP.
- The MVP must include tests for the report's counting and grouping
  logic, using small representative examples.

## Out of Scope

The MVP must not include:

- calculated football or tactical performance metrics;
- possession reconstruction;
- tactical interpretation or tactical rankings;
- predictive or causal statistical models;
- machine learning;
- counterfactual scenarios;
- match simulation;
- real-time data;
- commercial APIs or paid services;
- multi-user accounts or cloud deployment;
- a separate production frontend and backend;
- Docker, Kubernetes, microservices, MCP, or specialised agents.

## Completion Criteria

The MVP is complete when:

1. A documented, small StatsBomb dataset can be selected locally.
2. The data can be loaded or the process fails with a useful error.
3. The descriptive report contains all required counts and summaries.
4. Missing or optional data is identified rather than hidden.
5. The same inputs reproduce the same output.
6. Tests pass for the report logic and its representative edge cases.