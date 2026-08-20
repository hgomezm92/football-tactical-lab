# Project Roadmap

Football Tactical Lab will evolve from a small, understandable data
exploration tool into a progressively more advanced football analysis
laboratory. Each phase should produce a useful result before the next
phase begins.

## Phase 1: Understand the Data

**Objective:** Explore a small selection of StatsBomb Open Data and
understand what it records.

**Learn:** JSON structures, nested data, descriptive analysis, and data
quality checks.

**Functionality:** Load competitions, matches, teams, players, and event
types; produce basic descriptive summaries.

**Data needed:** StatsBomb Open Data competition, match, lineup, and
event files.

**Difficulty:** Low.

**Done when:** A reproducible local report can state how many matches,
teams, players, events, and event types are present in the selected data.

## Phase 2: Import and Store the Data

**Objective:** Make the source data available in a consistent,
queryable local form.

**Learn:** Data modelling, identifiers, relationships, import processes,
and idempotency.

**Functionality:** Import matches and events, retain source identifiers,
avoid duplicate imports, and report malformed or incomplete files.

**Data needed:** The StatsBomb files used in Phase 1.

**Difficulty:** Low to medium.

**Done when:** The basic information for an imported match can be
reconstructed from the local stored data, and the import can be safely
run again.

## Phase 3: Build Descriptive Metrics

**Objective:** Calculate transparent, reproducible football metrics.

**Learn:** Aggregations, metric definitions, edge cases, and focused
automated testing.

**Functionality:** Calculate passing, shooting, scoring, recovery, and
loss-of-possession summaries by match, team, player, and period.

**Data needed:** Stored events, match metadata, and score information.

**Difficulty:** Medium.

**Done when:** Every metric has a written definition, known examples,
and tests covering its main cases and relevant edge cases.

## Phase 4: Explore the Results Visually

**Objective:** Make common questions answerable without changing code.

**Learn:** Interactive visualisation, filtering, spatial data, and
communicating analytical results.

**Functionality:** Provide match, team, and player filters; show tables,
comparisons, event timelines, and basic pass or shot maps.

**Data needed:** Metrics and event coordinates where available.

**Difficulty:** Medium.

**Done when:** A user can inspect a selected match and investigate a
small set of predefined questions through the local interface.

## Phase 5: Define Tactical Metrics

**Objective:** Study collective patterns using explicit and limited
definitions.

**Learn:** Units of analysis, temporal aggregation, domain assumptions,
and the limits of event data.

**Functionality:** Explore approximate progression, possession sequences,
territorial patterns, recoveries followed by attacks, and behaviour
under different score contexts.

**Data needed:** Event data with coordinates and any additional open
data that can support the definitions.

**Difficulty:** Medium to high.

**Done when:** The metrics are documented, tested with examples, and
their limitations are visible to anyone interpreting the results.

## Phase 6: Apply Basic Statistics

**Objective:** Study relationships between context, actions, and
outcomes without treating associations as causal conclusions.

**Learn:** Samples, variation, correlation, uncertainty, regression,
confounding factors, and validation.

**Functionality:** Compare groups of matches, include relevant context,
quantify uncertainty, and evaluate models on data not used to fit them.

**Data needed:** A sufficiently broad collection of matches across
competitions, seasons, teams, and contexts.

**Difficulty:** High.

**Done when:** Each analysis explains its assumptions, uncertainty,
limitations, and the difference between association and causation.

## Phase 7: Experiment with Counterfactual Scenarios

**Objective:** Explore hypothetical changes under explicit assumptions.

**Learn:** Simulation, uncertainty, causal reasoning, and model
validation.

**Functionality:** Modify simplified tactical variables, generate
hypothetical scenarios, and compare outcome distributions rather than
claiming exact predictions.

**Data needed:** A large historical dataset and validated models that
justify the chosen scenarios.

**Difficulty:** Very high.

**Done when:** A scenario is a reproducible experiment with documented
assumptions and uncertainty, rather than an unsupported claim about what
would have happened.

## Guiding Boundaries

- StatsBomb Open Data and other free sources remain the initial data
  boundary.
- The project should stay local and simple until a concrete requirement
  justifies additional infrastructure.
- A complete football simulator is not a prerequisite for the earlier
  phases.
- Observed data, calculated metrics, inferred variables, and hypotheses
  must remain clearly distinguished.