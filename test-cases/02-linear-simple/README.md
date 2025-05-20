# Linear

## Description

Test how simple linear segments are calculated across each tool. This tests a declining segment where the final rate is lower than the initial rate.

- Create a production forecast for oil.
- Add a linear segment with these parameters:
  - Start date of 01/01/2025
  - Duration ($t$t) of 1 year
    - Note: if the tool doesn't allow duration to be provided in years, try to provide it either as 12 months, or 365.25 days
  - Initial rate ($q_i$) of 2000 bbl/d
    - Note: this rate is intentionally extreme so we can spot small variances in slope/decline rate calculations
  - Final rate ($q_f$) of 1000 bbl/d

## Results

### Baseline

We expect the volume for this segment to be calculated with:

```math
\begin{aligned}
Q_t(t) &= \frac{t}{2}(q_i+q_f)\\
Q_f &= \frac{365.25}{2}(2000+1000)\\
&=547,875 \text{ bbl}
\end{aligned}
```

**Expected Volume: 547,875 bbl**

### ARIES

### PHDwin

### ComboCurve

(TODO: screenshot)

It seems that ComboCurve only allows whole numbers to be used as the duration for flat segments, so 365 days was used instead of 365.25 days.

If we use 365 days to re-calculate the equation used in the baseline, the result is $(365/2)(2000+1000)=547,500$ as expected, so the change in duration is the only reason for the variance.

**Actual Volume: 547,500 bbl**

### whitson+

### Val Nav

### Mosaic

### 4cast

### Harmony
