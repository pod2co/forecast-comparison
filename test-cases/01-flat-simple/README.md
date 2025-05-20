# Flat

## Description

- Create a production forecast for oil.
- Add a flat segment with these parameters:
  - Start date of 01/01/2025
    - Note: intentionally *not* a leap year
  - Duration of 1 year
    - Note: if the tool doesn't allow duration to be provided in years, try provide it either as 12 months, or 365.25 days
  - Rate of 1000 bbl/d

## Results

### Baseline

We expect the volume for this segment to be calculated with:

```math
\begin{aligned}
Q_t(t) &= q_it \\
&= (1000)(365.25) \\
&= 365,250 \text{ bbl}
\end{aligned}
```

**Expected Volume: 365,250 bbl**

### ARIES

### PHDwin

### ComboCurve

(TODO: screenshot)

It seems that ComboCurve only allows whole numbers to be used as the duration for flat segments, so 365 days was used instead of 365.25 days.

This duration difference caused the volume to be different.

**Actual Volume: 365,000 bbl**

### whitson+

### Val Nav

### Mosaic

### 4cast

### Harmony
