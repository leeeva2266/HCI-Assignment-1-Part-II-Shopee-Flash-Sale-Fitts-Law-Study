# HCI-Assignment-1-Part-II-Shopee-Flash-Sale-Fitts-Law-Study

## Experiment Demo Video

https://github.com/user-attachments/assets/b234d4c1-b946-4a15-8310-87482408b5a1

---

## 1. Scenario
This experiment stems from the everyday frustration of trying and failing to grab flash-sale deals under extreme time pressure (such as Shopee's 11.11 limited-quantity sale for AirPods Pro 2 at $999). In a typical shopping cart interface, the user must first select the item checkbox and then immediately sweep the cursor across the canvas to click the primary "Checkout" button located in the bottom-right corner. People often assume that missing out on flash deals is simply due to slow hand speed. I designed this experiment to investigate whether checkout delays are primarily caused by excessive cursor travel distance or tiny, hard-to-click target buttons.

---

## 2. Innovation
Compared to the standard two-column red-bar test in the CS Field Guide, this project introduces several practical design changes:
* **Realistic E-Commerce Reciprocal Workflow:** Instead of abstract bars, the test uses a functional cart UI where users continuously alternate between an upper product checkbox (Start/Reset Node) and the bottom-right checkout button (Target Node).
* **Proportional Bidirectional Scaling:** In earlier iterations, only the checkout button was resized, which made the small checkbox an artificial bottleneck. Both the checkbox and the checkout button now scale simultaneously across three proportional size tiers (Small, Medium, Large), ensuring symmetric motor tolerance in both travel directions.
* **First-Click Exclusion (ISO 9241-9 Standard):** Each condition requires 11 successful clicks. The first click serves solely to position the cursor at the starting point and is excluded from timing calculations. Only the subsequent 10 steady reciprocal strokes are averaged, filtering out initial visual orientation and hesitation delays.
* **Calibrated Ergonomic Distances:** Traversal distances are constrained between 200px and 480px, matching natural wrist and finger sweeping arcs on a desktop and avoiding awkward mouse clutching or lifting artifacts.

---

## 3. Application
### Why this design was chosen:
  During high-stakes checkout rushes, users easily rush their movements and overshoot small interface elements. Symmetrically enlarging both the checkbox and the checkout button provides sufficient motor tolerance without disrupting the store page's visual hierarchy.
  
### Real-World Problem Solved:
  The experiment clarifies whether distance or button dimensions dominate checkout speed. The empirical results show that expanding the button width from 45px to 200px cut movement time from over 700ms down to roughly 440ms (an improvement of nearly 40%). This confirms that widening interactive click zones on key checkout elements is far more effective at reducing user drop-off than simply relying on users to click faster.

---

## 4. Empirical Dataset & Custom Formula
### Collected Trial Data
| Trial | Distance A (pixels) | Btn Width (pixels) | Btn Height (pixels) | Checkbox Size (pixels) | Index of Difficulty (bits) | Average Time (milliseconds) |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| 1 | 480 | 45 | 24 | 16 | 3.54 | 728.20 |
| 2 | 200 | 45 | 24 | 16 | 2.44 | 670.50 |
| 3 | 480 | 100 | 36 | 28 | 2.54 | 649.50 |
| 4 | 480 | 200 | 54 | 44 | 1.77 | 471.90 |
| 5 | 200 | 100 | 36 | 28 | 1.58 | 483.40 |
| 6 | 200 | 200 | 54 | 44 | 1.00 | 457.80 |
| 7 | 340 | 45 | 24 | 16 | 3.10 | 780.50 |
| 8 | 340 | 100 | 36 | 28 | 2.14 | 588.90 |
| 9 | 340 | 200 | 54 | 44 | 1.43 | 437.50 |

### Linear Regression Results
Linear regression across the 9 empirical conditions (MT = a + b * ID) yielded:
* Intercept a = 267.19 ms
* Slope b = 146.55 ms/bit
* Pearson correlation r = 0.9379
* Coefficient of Determination R² = 0.8797
* Human Information Throughput (TP = 1/b) ≈ 6.82 bits/s

### Empirical Fitts' Law Equation
MT = 267.19 + 146.55 * log2(A / W + 1)

*(where A is the center-to-center distance in pixels, W is the button width in pixels, and MT is the average movement time in milliseconds)*

---

## 5. Regression Scatter Plot

<img width="1600" height="1100" alt="Code_Generated_Image" src="https://github.com/user-attachments/assets/c93a7645-b998-490e-a490-2a37a8ba2e56" />


*(The plot displays the 9 empirical trial conditions mapping Index of Difficulty (ID, bits) on the x-axis against Average Movement Time (MT, ms) on the y-axis, overlaid with the linear regression trendline and R² score.)*

---

## 6. Parameter Analysis
* **Intercept (a = 267.19 ms):** 
  The intercept represents baseline non-motor reaction time when task difficulty is zero. This latency consists of basic visual recognition (processing target state changes, ~150–200ms), cognitive task-switching between item confirmation and purchase triggers (~50–70ms), and mouse switch actuation micro-delays (~20–30ms). A value of 267.19ms closely matches standard physiological visual reaction times (200–300ms), confirming that the reciprocal protocol cleanly isolated pure motor latency from visual search hesitation.
* **Slope (b = 146.55 ms/bit):** 
  The slope reflects the additional movement time required per bit of task difficulty, translating to a throughput of 6.82 bits/s. A slope of 146.55 ms/bit is relatively low and indicates high motor efficiency. Because targets alternated along a predictable diagonal axis, the participant could execute smooth ballistic trajectories without excessive corrective adjustments near the button boundaries.
* **Coefficient of Determination (R² = 0.8797):** 
  An R² of 0.8797 (p < 0.001) shows that roughly 88% of the variance in movement time is directly accounted for by Fitts' Law. The remaining 12% is attributable to minor hand jitter or brief lapses in focus. This high goodness-of-fit confirms that target size and placement distance reliably govern checkout performance under high time pressure.
