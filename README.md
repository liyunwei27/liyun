# liyun
# Tremor-Aware Fitts' Law Tapping Test

**Live demo:** https://liyunwei27.github.io/liyun/
**Screen-recording video:** https://youtu.be/Hp1j-ndcHPU?si=3uGx_vDJeA9NBknb

---

## Scenario

This experiment targets an **older adult (65+) using a smartphone**, particularly someone
with mild hand tremor or age-related motor slowing (e.g. essential tremor or early-stage
Parkinsonism). The user is performing everyday, sometimes time-critical, phone tasks —
confirming a medication reminder, replying to a family member's message, or calling an
emergency contact.

Standard touch-target sizing guidelines are typically validated with younger, motorically
stable users. For an older adult with reduced fine motor control, the same targets can
require multiple attempts or produce mis-taps — a risk that becomes serious in high-stakes
contexts like medication confirmation or emergency dialing.

## Innovation

Beyond the classic Fitts' Law manipulation of **Distance (A)** and **Width (W)**, this
application adds a **cursor-jitter layer** that simulates hand tremor:

- The on-screen cursor is displaced from the real pointer position by a combination of a
  slow sinusoidal drift and random noise, with an adjustable amplitude (0–20 px).
- The *visible* cursor jitters, but the actual click is still registered at the real pointer
  position — so the participant has to compensate for a visual–motor mismatch, similar to
  what a person with tremor experiences when trying to align their hand with what they see.
- Distance and width are varied systematically across 9 conditions (3 distances × 3
  widths), each repeated multiple times in a reciprocal (left–right) tapping task, so
  Index of Difficulty (ID) spans a wide range.

## Application

A single-file HTML/JS web app built with AI-assisted prototyping. It presents two
alternating circular targets; the active target is highlighted, the participant clicks it
as fast and accurately as possible, and Movement Time (MT) is recorded from target
activation to the correct click. After the session, results (Distance, Width, ID, MT, Hit)
export directly as a CSV file for analysis.

## Why this design

Touch-target and spacing standards in mobile HCI guidelines are largely derived from
studies with motorically typical users. This experiment makes the cost of tremor-induced
imprecision directly measurable: by comparing Movement Time and error rate across
different target sizes under a simulated-tremor condition, it becomes possible to argue,
empirically, for larger minimum touch targets and wider spacing in accessibility-focused
interface guidelines — directly addressing the real-world HCI problem of designing mobile
interfaces that are safe and usable for older or motor-impaired users.

## Empirical Results

Data were collected across 9 A×W conditions (repeated tapping), yielding **45 valid trials**.

**Derived Fitts' Law formula:**

```
MT = 296.5 + 207.6 × ID
```

- **a (intercept) = 296.5 ms** — the estimated fixed cost of a movement (visual
  confirmation, reaction time, and movement initiation) at zero difficulty.
- **b (slope) = 207.6 ms/bit** — for every additional bit of difficulty (greater distance
  or smaller width), Movement Time increased by roughly 208 ms — notably steeper than
  typical non-impaired Fitts' Law slopes (often ~100–150 ms/bit), consistent with the
  added cost of compensating for simulated hand tremor.
- **R² = 0.522** — a moderate fit; the added jitter injects trial-to-trial variability at
  every difficulty level, which is expected given the random-noise component of the
  tremor simulation.

![](fitts_law_scatter_regression.png)

## Data & Materials

- [fitts_law_tremor_trial_data (1).csv](fitts_law_tremor_trial_data(1).csv) — raw trial data
- [<img width="377" height="269" alt="image" src="https://github.com/user-attachments/assets/1140b180-b499-41b7-934c-2950d15655dd" />](fitts_law_scatter_regression.png) — regression plot
- Screen-recording of the data-collection session: `video`(https://youtu.be/Hp1j-ndcHPU?si=UtBOoPvj_LKck64J)
