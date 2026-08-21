# Recovery Height

## Status

Initial MVP metric. This definition must be validated against the selected
StatsBomb dataset before being treated as stable.

## Question

Where does a team recover possession during the selected matches when the
source event includes usable spatial information?

## Interpretation

Recovery height is a descriptive measure of recovery location. It is not a
direct measure of pressing height, defensive line height, or tactical
intention. A recovery may follow a pressure, interception, duel, error, or
another event.

## Unit of Analysis

The primary result is one value per team and match. The result must also
include the number of qualifying recoveries used to calculate it.

The MVP may show an overall team summary, but the match-level values and
their observation counts remain the main evidence.

## Required Data

- Match identifier.
- Team identifier.
- Event type or event attributes identifying a qualifying recovery.
- Recovery location coordinates.
- Sufficient match context to identify the competition, season, teams, and
  attacking direction.

The exact qualifying event set must be confirmed by inspecting the selected
StatsBomb data. It must not be assumed from the metric name alone.

## Calculation Rules

The implementation must document and apply the following rules:

1. Select only events that meet the documented recovery definition.
2. Exclude recoveries without usable location coordinates.
3. Express coordinates consistently along the team's attacking direction,
   or report that direction could not be normalised.
4. Calculate the match-level summary using the documented location statistic,
   initially a mean unless inspection shows that a different summary is more
   appropriate.
5. Preserve the number of included and excluded observations.

The coordinate scale, field orientation, summary statistic, and any
exclusions must be recorded once the source data has been inspected.

## Missing Data

Missing coordinates must not be replaced with zero or another location.
Matches with no qualifying recoveries must be reported as unavailable rather
than assigned a meaningful value. The result should make the number of
excluded or unavailable observations visible.

## Validation

The metric must be checked at three levels:

- **Data validity:** the required events and coordinates exist and are
  interpreted correctly.
- **Calculation validity:** hand-checked examples produce the expected
  values, including orientation and missing-data cases.
- **Practical validity:** a small sample of matches is reviewed to assess
  whether the results are plausible. This does not prove that the metric
  measures pressing or tactical intent.

## Limitations

- Event data may not record every recovery or defensive action.
- Recovery location does not identify why possession was recovered.
- Results may be affected by opponent, score, game state, and event coverage.
- A mean can hide variation and can be unstable with few observations.
- Comparisons are meaningful only when data coverage and definitions are
  sufficiently comparable.

## Valid and Invalid Claims

Valid initial claim:

> In this selected sample, the team recovered possession at locations that
> were, on average, more or less advanced according to this definition.

Invalid claim:

> The team presses high and therefore creates more expected goals.

The second claim requires a different measure, broader context, and
statistical analysis that are outside the MVP.
