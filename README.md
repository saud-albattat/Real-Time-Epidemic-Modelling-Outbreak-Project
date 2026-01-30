# São Vicente Paramyxovirus Outbreak: Real-Time Epidemiological Modeling

## Project Context
This project simulates a real-time epidemiological response to a fictional outbreak of a novel paramyxovirus in São Vicente, a Cape Verdean Island with a population of 80,000. The epidemic spanned 40 weeks, characterized by flu-like symptoms ranging from fever to paranesthesia.

The analysis was conducted in four stages (Weeks 1-4), mirroring a real-world response where modelers must translate accumulating surveillance data into mechanistic insights and actionable policy recommendations.

## Project Aims
* **Estimate Parameters:** Calculate key transmission and disease characteristics from available data.
* **Evaluate Fit:** Assess how accurately different modeling approaches represent observed incidence.
* **Scenario Modeling:** Adapt models to real-time control measures (quarantine, self-isolation) and events (carnivals).
* **Decision Support:** Translate model outputs into actionable metrics to support policy creation.

## Project Timeline & Methodological Evolution

### Week 1: Early Detection & Calibration
* **Data:** Weeks 1-6 (49 total cases).
* **Model:** Deterministic **SEIIR** (Susceptible-Exposed-Infectious-Recovered) differentiating mild and severe infections.
* **Method:** Calibrated using **Sum of Squared Errors (SSE)** to identify best-fit parameters.
* **Outcome:** Initial projections indicated a high R0 (9.78) and potential exponential growth due to sparse early data.

### Week 2: Intervention Analysis (Quarantine & Carnival)
* **Data:** Weeks 1-12 (189 total cases).
* **Model:** Simplified **SEIR** model to align with standard outbreak practice.
* **Scenarios:**
    * **Baseline:** Projected peak of ~1,800 weekly cases.
    * **Quarantine:** Modeled as a 30% reduction in transmission.
    * **Mass Gathering (Carnival):** Modeled as a 20% transmission increase due to crowd density.
* **Outcome:** Demonstrated that quarantine could significantly reduce peak incidence, though unmodeled superspreading events caused divergence.

### Week 3: Complex Dynamics & Self-Isolation
* **Data:** Weeks 1-28 (1,136 total cases).
* **Model:** Time-varying SEIR with retrospective updates.
* **Intervention:** Introduction of **Self-Isolation** (20% transmission reduction from Week 28 onwards).
* **Optimization:** Iterative grid searches used to fit parameters (R0, initial exposed/infectious).
* **Outcome:** Capturing the mid-phase rebound in cases required adapting the model to account for behavioral shifts.

### Week 4: Statistical Refinement & Epidemic Resolution
* **Data:** Weeks 1-40 (Epidemic conclusion).
* **Model:** Enhanced time-varying SEIR using **Piecewise Transmission Rates** for baseline, quarantine, and self-isolation phases.
* **Optimization:** Shifted from SSE to **Maximum Likelihood Estimation (MLE)** for higher precision.
* **Resolution Criteria:** Defined the end of the epidemic using dual thresholds:
    1.  Effective Reproduction Number (Re) < 1.
    2.  Fewer than 5 weekly cases for three consecutive weeks.
* **Outcome:** The model correctly identified epidemic resolution between Weeks 40 and 41.

## Technologies & Methods
* **Language:** R
* **Modeling Frameworks:** `odin` for Ordinary Differential Equations.
* **Optimization Algorithms:** `optim` (L-BFGS-B), Grid Search, SSE, and Poisson-based MLE.
* **Key Metrics:** Effective Reproduction Number (Re), Incidence Projections.

## How to Run
1.  Clone this repository.
2.  Open the `.Rmd` file in RStudio.
3.  Ensure the following packages are installed:
    ```r
    install.packages("odin")
    install.packages("ggplot2")
    ```

## 📊 View the Analysis
[Click here to view the full model analysis and graphs](./Outbreak.md)
