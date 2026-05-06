# Week 3 - Individual - Tableau Preb Scripts - Tabpy

**Author:** Yash Annapure

## 1. Objective
The goal of this exercise was to demonstrate the integration of Python scripts within a Tableau Prep workflow using the TabPy analytics extension. The specific task required processing an employee dataset (`employee_tableau_prep_python_sample.csv`) to filter records based on departmental criteria while simultaneously computing and appending organization-wide metrics.

## 2. Dataset Overview
The dataset consisted of 15 employee records containing the following columns:
*   `Employee_ID` (String)
*   `Employee_Name` (String)
*   `Department` (String)
*   `Age` (Integer)
*   `Salary` (Integer)
*   `Hire_Date` (Date/String)
*   `City` (String)

A preliminary profile of the raw data revealed no missing values. The dataset included employees from various departments such as IT, Finance, HR, and Marketing.

## 3. Workflow Configuration and Execution
To accomplish the tasks, a local TabPy server was initiated via the command line on port `9004`. Tableau Prep was then configured to connect to this analytics extension. 

<img width="1920" height="1080" alt="Screenshot (412)" src="https://github.com/user-attachments/assets/dd291caf-5c93-446c-b1dc-0ced5ae0d36d" />


### The Python Script
A Python script (`prep_employee_script.py`) was developed utilizing the `pandas` library to perform the required transformations. The script contained two primary functions:
1.  **`get_output_schema()`**: This function defined the expected structure of the output DataFrame for Tableau Prep, ensuring data types were mapped correctly (e.g., `prep_string()`, `prep_int()`, `prep_decimal()`).
2.  **`process_employee_data(df)`**: This core function executed the required logic:
    *   **Metric Calculation:** It computed the average salary across the entire dataset using `df['Salary'].mean()`.
    *   **Identification:** It identified the oldest employee company-wide by locating the maximum value in the `Age` column and extracting the associated `Employee_Name` and `Department`.
    *   **Filtering:** It filtered the main DataFrame to retain only employees where `Department == 'IT'`.
    *   **Column Appending:** It appended the calculated metrics (`Average_Salary_All_Employees`, `Oldest_Employee_Name`, `Oldest_Employee_Department`) as new columns to the filtered IT department DataFrame.

## 4. Results and Output
The execution of the TabPy script within Tableau Prep successfully transformed the data. The expected and achieved outputs aligned perfectly:

*   **Row Filtering:** The dataset was successfully reduced from 15 total rows to only those individuals working in the IT department. 
*   **Calculated Columns:** Three new columns were successfully appended to every remaining row:
    *   `Average_Salary_All_Employees`: Displayed the computed average salary of all 15 original employees.
    *   `Oldest_Employee_Name`: Successfully identified the oldest individual in the company prior to filtering.
    *   `Oldest_Employee_Department`: Successfully identified the department of that oldest individual.

## 5. Conclusion
This activity successfully demonstrated how TabPy can be leveraged to extend the native capabilities of Tableau Prep. While Tableau Prep excels at standard cleaning tasks, integrating Python allows for complex, multi-step logic—such as calculating global metrics before applying row-level filters—to be executed seamlessly within a single Script Step. The final dataset is correctly formatted, filtered, and enriched with new data points, ready for downstream visualization in Tableau Desktop.
