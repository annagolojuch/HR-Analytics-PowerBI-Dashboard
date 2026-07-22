<img width="1344" height="749" alt="2" src="https://github.com/user-attachments/assets/4b2eba5e-8301-4364-aa64-ec6e8e04442a" />
<img width="1345" height="750" alt="1" src="https://github.com/user-attachments/assets/0eac8b48-fc37-43c3-a517-da6682924b0d" />
# HR Analytics Dashboard - Talent Acquisition & Attrition Insights

## 📌 Project Overview
This project focuses on building an interactive HR Analytics Dashboard using **Power BI** based on the realistic "Human Resources Data Set" by Dr. Rich Huebner. The goal of this analysis is to provide the HR Director and Executive Team with actionable insights regarding employee attrition, recruitment channel efficiency, and talent acquisition costs.

The dashboard consists of two main analytical areas:
1. **Talent Acquisition & Attrition Insights**: Focuses on workforce demographics, current employee status, and core attrition metrics.
2. **Recruitment Cost Analysis**: Focuses on budget distribution and financial efficiency of hiring sources (*Cost per Hire*).

---

## 🛠️ Key Metrics & DAX Formulas Created
To build this dashboard, I designed a custom data model and implemented several core HR metrics using **DAX (Data Analysis Expressions)** and **Power Query**:

*   **Headcount / Total Employees**: 
    ```DAX
    Liczba Pracownikow = DISTINCTCOUNT('HRDataset'[EmpID])
    ```
*   **Total Terminations**: Tracks employees who left the organization.
    ```DAX
    LiczbaOdejsc = SUM('HRDataset'[Termd])
    ```
*   **Turnover / Attrition Rate (%)**: The percentage of employees who left the company relative to total hires.
    ```DAX
    Attrition Rate = DIVIDE([LiczbaOdejsc], COUNT('HRDataset'[EmpID]), 0)
    ```
*   **Average Employee Age**: Uses individual birth dates to dynamically calculate the average workforce age.
    ```DAX
    Average Age = AVERAGEX('HRDataset', YEARFRAC('HRDataset'[DOB], TODAY(), 1))
    ```
*   **Cost per Hire (CPH)**: Calculates the average financial cost to recruit a single employee.
    ```DAX
    Cost per Hire = DIVIDE([Total Recruitment Cost], COUNT('HRDataset'[EmpID]), 0)
    ```

---

## 📈 Key Business Insights From the Data
*   **High Attrition Warning**: The company has a historic attrition rate of **33.4%**, which is significantly high. 
*   **Recruitment Channel Efficiency**: While *LinkedIn* and *Indeed* bring in the highest volume of candidates and consume the largest portion of the budget ($15.2K and $13.1K respectively), certain niche channels like *On-line Web applications* show an alarming **100% attrition rate**, meaning every employee hired from that source eventually left.
*   **Workforce Seniority**: The average age of the workforce is **47.8 years**, indicating a mature organizational structure that may require future pipeline planning for younger generations (Gen Z/Millennials).

---

## 💻 Tech Stack Used
*   **Power BI Desktop**: Data modeling, DAX engineering, and UI/UX dashboard design.
*   **Power Query**: Data transformation, handling American date formats (`MM/DD/YY`) using Locale settings, and column optimization.
