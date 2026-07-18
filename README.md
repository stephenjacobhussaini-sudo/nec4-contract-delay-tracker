# NEC4 Contract Delay & Compensation Event (CE) Tracker

## 📌 Project Overview
This repository showcases an enterprise-grade contract compliance and delay analysis dashboard built in Power BI. The project simulates a major UK transit infrastructure asset: the **Greater Manchester Metrolink Expansion**. 

The primary objective of this dashboard is to digitize and automate **NEC4 Contract Management**, specifically tracking **Clause 60.1(13) Weather Delays**. By evaluating real-time weather data against strict contractual 1-in-10-year historical baselines, this tool isolates valid legal claims from standard contractor risks.

---

## 📊 Live Dashboard Preview
![NEC4 Contract Dashboard](https://github.com/stephenjacobhussaini-sudo/nec4-contract-delay-tracker/blob/main/Images/NEC4%20dashboard.JPG)

---

## 🛠️ Contractual DAX Logic Engine
I developed custom **Data Analysis Expressions (DAX)** to act as an automated contract administrator, evaluating whether weather events cross the high legal threshold required to grant a timeline extension:

*   **Rainfall CE Trigger:** Evaluates if monthly cumulative rainfall breached the 1-in-10-year baseline.
    ```dax
    Rainfall_CE_Triggered = IF(SUM('Weather_Baseline'[Actual Rainfall (mm)]) > SUM('Weather_Baseline'[1-in-10 Yr Rainfall Baseline (mm)]), "⚠️ CE TRIGGERED (Rainfall Exceeded)", "No Event")
    ```
*   **Approved Variation Expenditure:** Sums contract alterations strictly accepted by the Project Manager.
    ```dax
    Approved_CE_Spend = CALCULATE(SUM('Compensation_Events'[Cost Impact (£)]), 'Compensation_Events'[Status] = "Implemented")
    ```
*   **Critical Path Impact Analysis:** Tracks net delay durations only if they affect the project's critical path execution window.
    ```dax
    Critical_Path_Delay = CALCULATE(SUM('Compensation_Events'[Delay Impact (Days)]), 'Compensation_Events'[Critical Path?] = "Yes")
    ```

---

## 🔍 Data Insights & Commercial Value
*   **Contractual Entitlement Isolated:** The chart demonstrates a clear baseline breach in **February**, where actual rainfall hit 145mm against a 120mm baseline limitation. This visually validates the contractor’s legal entitlement to an extension of time.
*   **Risk Overexposure Flagged:** The dashboard highlights that while approved variations sit at £405K, there is an outstanding **£240K in Pending Claims** across 6 active Compensation Events, threatening an additional **63 days** of critical path delay.
*   **Prioritization Matrix:** Sorting the active registry reveals that **CE-02 (Additional Piling)** represents the largest single commercial variation risk at £280K, allowing the client to prioritize negotiation efforts.

---

## 📂 Repository Structure
*   `data/`: Master contract registry and Met Office weather baseline datasets.
*   `reports/`: Compiled Power BI dashboard file (`.pbix`).
*   `images/`: High-resolution visual captures and system documentation.

---
**Contact & Career Opportunities**  
I am a UK Master’s graduate in Engineering Project Management specializing in Digital Project Controls and Contractual Data Analytics. I am actively pursuing opportunities within the UK infrastructure sector under the **New Entrant Skilled Worker visa pathway**. 
Let's connect on [LinkedIn](https://www.linkedin.com/in/stephen-hussaini-248746371/).
