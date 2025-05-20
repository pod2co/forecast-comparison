# Forecast Comparison

A comparison of forecast methodology and results across several tools:

- ARIES
- PHDwin
- ComboCurve
- Mosaic
- Val Nav
- whitson+
- 4cast
- Harmony

## Introduction

This analysis compares how various tools solve and calculate forecasts (e.g., Arps) and ratios.

The purpose is to compare the results of each tool against a baseline in order to understand how to replicate the calculation. This also enables a better understanding of conversions between tools (e.g., how to convert an ARIES forecast to PHDwin without changing the volume of a segment).

Several test cases are provided that are run in each tool. These test cases and results are saved and used for comparison.

## Test Cases

Although many tools use approximately the same equations to calculate forecasts, there are plenty of ways that differences can be introduced, including (but not limited to):

- Differences in precision on inputs and outputs (e.g., floating-point precision, rounding)
- Confusion about decline rate type: nominal vs. secant effective vs. tangent effective (e.g., treatment of final decline rate for hyperbolic segments)
- Different techniques when solving unknown parameters in Arps equations (e.g., whether unknown durations are rounded to month boundaries)
- Results summarized as actual calendar months vs. average months (e.g., why February often has the greatest variance across tools)
- Differences in average day/month/year duration (e.g., 365 average days/year vs. 365.25 average days/year and the affect on forecasts)

The test cases aim to test this behaviors so they're visible in the results from each tool.

Sometimes relatively extreme parameters (e.g., unrealistic for typical wells) will be used in some cases to make the variance more obvious and easier to compare.

## Results

Results will be added here as they are available. Each of the test cases has detailed breakdowns where possible to understand the variances.

1. [Flat Simple](./test-cases/01-flat-simple/README.md)
2. [Linear Simple](./test-cases/02-linear-simple/README.md)

## Contributing

GitHub Issues will be used to coordinate creation of additional test cases and collecting results in each tool. If you'd like to help, please feel free to comment on any issue to claim the parts you're interested in.
