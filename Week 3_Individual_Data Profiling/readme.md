# Week 3 - Individual - Data Profiling
**Author:** Yash Annapure

## Submission Report

### Q. Decide the pipeline context:
1. In ETL, where would profiling happen?
2. In ELT, where would profiling happen?
3. Which approach is better for this dataset and why?

---

#### 1. ETL (Extract, Transform, Load)
**Where profiling happens:** Profiling happens early, immediately after extraction, and transformation (cleaning) happens before the data is loaded into the final data warehouse. Tableau Prep is a visual ETL tool.

#### 2. ELT (Extract, Load, Transform)
**Where profiling happens:** The messy, raw data is loaded directly into a data lake or cloud warehouse first. Profiling and transformation happen inside the database using SQL.

#### 3. Which approach is better for this dataset?
For this specific dataset, ETL is the better approach. The data is small, highly messy, and contains structural errors (like wrong data types and currency symbols). It is safer to profile and transform this data using an ETL tool (like Tableau Prep) before it enters a core database, preventing bad data types from causing database upload failures. ELT is better suited for massive datasets where you need the power of cloud computing to do the heavy lifting.

---

### Workflow Screenshot
<img width="1920" height="1080" alt="Screenshot (411)" src="https://github.com/user-attachments/assets/c8f74aa1-ed0e-471f-99fe-b141e830c53c" />
