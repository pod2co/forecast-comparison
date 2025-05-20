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
Q_t(t) &= \frac{t(q_i+q_f)}{2}\\
Q_f &= \frac{365.25(2000+1000)}{2}\\
&=547,875 \text{ bbl}
\end{aligned}
```

**Expected Volume: 547,875 bbl**

Let's also calculate the slope and decline rate for completeness, because some tools provide those as outputs.

```math
\begin{aligned}
m &= \frac{q_f - q_i}{t}\\
&= \frac{1000 - 2000}{365.25}\\
&\approx -2.737850787 \text{ bbl/d/d}\\
a_i &= \frac{-m}{q_i}\\
&\approx \frac{2.737850787 \text{ bbl/d/d}}{2000 \text{ bbl/d}}*\frac{365.25 \text{ d}}{\text{yr}}*100\%\\
&\approx 50 \text{ \%/yr}
\end{aligned}
```

**Expected Slope: approximately -2.73785 bbl/d/d**

**Expected Decline Rate: approximately 50 %/yr**

### ARIES

### PHDwin

### ComboCurve

(TODO: screenshot)

It seems that ComboCurve only allows whole numbers to be used as the duration for flat segments, so 365 days was used instead of 365.25 days.

If we use 365 days to re-calculate the equation used in the baseline, the result is $(365)(2000+1000)/2=547,500$ as expected, so the change in duration is the only reason for the variance.

**Actual Volume: 547,500 bbl**

ComboCurve's slope calculation seems to use a duration that is off by one day compared to the baseline (even if we use 365 days as the duration).

Using inputs with duration of 365 days, initial rate of 2000 bbl/d, and final rate of 1000 bbl/d, ComboCurve calculates the slope as -2.74725. This seems to be using 364 as the duration (e.g., $(1000 - 2000)/364 = -2.74725$) which wasn't expected.

**Actual Slope (using rounded duration): -2.74725 bbl/d/d**

ComboCurve calculates "Di Eff-Sec" to be ~50.17 %/yr, which seems to be expected based on the slope $a_i = -(-2.74725)*365.25*1000/2000 \approx -50.1717032967$. The difference compared to the expected 50 %/yr seems to be caused by the different slope.

**Actual Decline Rate (using rounded duration): 50.1717032967 %/yr**

We also tried to use the slope as an input to try to workaround the differences, but because duration rounding, the final rate would be automatically updated too.

### whitson+

### Val Nav

### Mosaic

### 4cast

### Harmony
