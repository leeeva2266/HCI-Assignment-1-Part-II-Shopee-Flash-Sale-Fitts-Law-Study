# HCI-Assignment-1-Part-II-Shopee-Flash-Sale-Fitts-Law-Study

## 1. Scenario
This experiment simulates a real-world, high-stakes e-commerce checkout workflow under extreme time pressure (e.g., Shopee 11.11 Flash Sale for AirPods Pro 2 at $999). In the cart interface, the user must first select the discounted item via a checkbox (Start Node) and then immediately navigate the cursor across the canvas to acquire and click the primary "Checkout" button located in the bottom-right corner.

## 2. Innovation
Compared to standard Fitts' Law evaluation setups (such as the reciprocal circular tapping task in CS Field Guide), this experiment introduces the following distinctive features:
* **Discrete Pointing Paradigm:** Replaces continuous reciprocal tapping with a realistic single-stroke initiation-to-target workflow, isolating non-motor reaction latency from the movement trajectory.
* **Adaptive Target Expansion (Poka-Yoke Innovation):** Incorporates an intelligent target affordance mechanism. When the cursor approaches within 110px of the checkout button, the button dynamically expands its horizontal width by 25% with visual luminance feedback, simulating an error-proofing (Poka-Yoke) affordance that reduces terminal deceleration overhead.
* **Systematic Geometric Modulation:** Features 9 controlled conditions systematically varying distance (A: 280 to 760px) and nominal button width (W: 70, 130, 220px), with 5 repetitions averaged per condition to filter stochastic motor noise.

## 3. Application
* **Why this design was chosen:**
  In competitive checkout scenarios, users face a severe Speed-Accuracy Trade-Off (SATO). While enlarged buttons prevent misclicks, keeping all call-to-action (CTA) buttons permanently massive ruins visual aesthetics, mobile responsiveness, and layout hierarchy.
* **Real-world HCI problem solved:**
  This design validates the efficacy of dynamic software affordances (Bubble Cursor / Expanding Target). By dynamically expanding the target's effective width (We) only upon user intent, it shortens the closed-loop corrective submovement phase and reduces hesitation delay without cluttering the interface.

## 4. Custom Formula
Linear regression analysis across the 9 empirical conditions (MT = a + b * ID) yielded:
* Intercept a = 91.95 ms
* Slope b = 269.25 ms/bit
* Coefficient of Determination R² = 0.6273

The complete empirical Fitts' Law equation is:
MT = 91.95 + 269.25 * log2(A / W + 1)

(where A denotes the distance from the checkbox to the checkout button in pixels, W represents the nominal width of the checkout button in pixels, and MT is the movement time in milliseconds)

## 5. Parameter Analysis
* **Intercept (a = 91.95 ms):** 
  The intercept represents the baseline non-motor reaction time, comprising visual recognition, cognitive planning, and motor initiation before physical cursor displacement begins. In this e-commerce task, the relatively compact intercept (91.95 ms) indicates that users experienced minimal decision latency once the checkbox was clicked, immediately initiating the ballistic stroke toward the prominent checkout button.
* **Slope (b = 269.25 ms/bit):** 
  The slope reflects the movement time required per additional bit of task difficulty, which is inversely related to human information processing bandwidth (Throughput = 1/b ≈ 3.71 bits/s). A slope of 269.25 ms/bit falls well within standard desktop mouse pointing performance (typically 150–300 ms/bit), demonstrating stable hand-eye coordination during target traversal.
* **Impact of Adaptive Expansion:** 
  Although the regression model was plotted against nominal widths (W), the physical acquisition process was actively facilitated by the 25% dynamic expansion. This adaptive mechanism mitigated the steep movement time penalties typically observed at high Index of Difficulty (ID) levels, validating how dynamic software affordances can stabilize motor performance under high speed-accuracy constraints.
