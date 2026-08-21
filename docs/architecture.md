# MVP Architecture

## Purpose

This document describes the smallest technical architecture that supports
the current MVP. It is intentionally local and should evolve only when a
concrete requirement makes the current design insufficient.

## Main Components

### Raw data

Local StatsBomb Open Data files containing competitions, matches, lineups,
and events. The source files remain unchanged so results can be traced
back to the original data.

### Data loading and validation

Reads the selected JSON files, checks that they are readable, validates the
fields required by the analysis, and reports missing or incomplete data.
It does not calculate metrics or render the interface.

### Normalised analysis data

Represents the selected matches, teams, events, coordinates, and source
identifiers in structures that are easier to analyse than the original
nested JSON. Normalisation must retain enough information to trace derived
values to their source events.

### Metric calculations

Calculates `recovery height` from validated analysis data. Metric logic is
independent of the user interface so it can be tested and reused later.

### Analysis and aggregation

Filters by competition, season, and team; groups results by match; and
combines metric values with opponents, scores, observation counts, and data
quality warnings.

### Local interface

Provides the selection controls, team context, match table, basic chart,
metric explanation, and data quality information.

## Main Data Flow

```text
Local StatsBomb JSON
    -> load and validate
    -> normalise selected data
    -> filter competition, season, and team
    -> calculate recovery height
    -> aggregate by match
    -> display table, chart, and explanations
```

Invalid files or insufficient metric inputs must produce a clear error or
visible warning. They must not silently become zero-valued results.

## Recommended Stack

- Python for data loading, analysis, and application code.
- Python's standard `json` library for the initial source inspection.
- pandas for tabular filtering and aggregation when it provides clear
  value.
- Streamlit for the local interface.
- Plotly for the basic visualisation.
- pytest for automated tests.
- A Python virtual environment for reproducible local setup.

This stack avoids a separate frontend, backend API, database, and remote
service, none of which is required by the MVP.

## Responsibility Boundaries

- Data loading does not know about the interface.
- Metric calculations do not depend on Streamlit or Plotly.
- Aggregation combines validated data and metric results.
- The interface presents results but does not implement metric formulas.
- Tests verify data handling, calculations, and observable analysis output.

## Deliberately Deferred Decisions

The MVP does not require decisions about a database schema, public API,
cloud deployment, authentication, multiple data sources, or a plugin system
for metrics. Those decisions should be revisited only when a later phase
creates a concrete need.
