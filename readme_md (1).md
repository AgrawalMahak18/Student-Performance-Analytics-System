# Student Performance Analytics System

An end-to-end Python data analysis pipeline designed to evaluate student academic performance, track attendance trends, and perform subject-level metrics aggregation across academic departments using **Pandas** and **NumPy**.

## 📋 Table of Contents

* [Project Overview](#-project-overview)

* [Dataset Architecture](#-dataset-architecture)

* [System Architecture & Workflow](#-system-architecture--workflow)

* [Key Performance Metrics](#-key-performance-metrics)

* [Subject Performance Breakdown](#-subject-performance-breakdown)

* [Tech Stack](#-tech-stack)

* [Installation & Getting Started](#-installation--getting-started)

* [Project Output Preview](#-project-output-preview)

##  Project Overview

The **Student Performance Analytics System** processes student dataset records to perform automated data validation, feature engineering, statistical analysis, and performance categorizations.

### Key Capabilities

* **Data Validation & Integrity Verification**: Automated detection of missing values, duplicate records, and logical boundary violations (e.g., negative marks or percentages $>100\%$).

* **Feature Engineering**: Dynamic calculation of total student marks, letter grades based on Cumulative Grade Point Average (CGPA), and pass/fail statuses.

* **Department & Subject Aggregation**: Cross-department performance indexing to identify subject-level baseline metrics.

* **Automated Executive Reporting**: Generation of clear terminal/notebook summary reports.

## 📊 Dataset Architecture

The pipeline evaluates **20 student records** distributed across three engineering departments: **CSE**, **IT**, and **AIML**.

| Field Name | Data Type | Constraint / Range | Description | 
| ----- | ----- | ----- | ----- | 
| `Student_ID` | `String` | `STU001` – `STU020` | Unique identifier for each student | 
| `Name` | `String` | Non-null | Full name of the student | 
| `Department` | `Categorical` | `CSE`, `IT`, `AIML` | Academic department assignment | 
| `Python_Marks` | `Integer` | $0 - 100$ | Score obtained in Python programming | 
| `SQL_Marks` | `Integer` | $0 - 100$ | Score obtained in SQL database management | 
| `Maths_Marks` | `Integer` | $0 - 100$ | Score obtained in Mathematics | 
| `Attendance_Percentage` | `Integer` | $0\% - 100\%$ | Attendance record percentage | 
| `CGPA` | `Float` | $0.00 - 10.00$ | Cumulative Grade Point Average | 

## 🔍 System Architecture & Workflow

1. **Ingestion & Data Sanitization**

   * Verification of dataset dimensions `(20, 8)` and schema validation.

   * Comprehensive checks ensuring zero missing entries or out-of-bounds parameters.

2. **Feature Engineering Rules**

   * **Total Score Computation**:
     

     $$
     \text{Total Marks} = \text{Python\_Marks} + \text{SQL\_Marks} + \text{Maths\_Marks}
     $$

   * **Academic Grade Allocation**:

     * **A+**: $\text{CGPA} \ge 9.0$

     * **A**: $8.0 \le \text{CGPA} < 9.0$

     * **B**: $7.0 \le \text{CGPA} < 8.0$

     * **C**: $6.0 \le \text{CGPA} < 7.0$

     * **D**: $5.0 \le \text{CGPA} < 6.0$

     * **F**: $\text{CGPA} < 5.0$

   * **Pass/Fail Evaluation**:
     

     $$
     \text{Status} = \begin{cases} \text{Pass}, & \text{if } \text{CGPA} \ge 4.0 \\ \text{Fail}, & \text{if } \text{CGPA} < 4.0 \end{cases}
     $$

3. **Analytics & Aggregation**

   * Compute central tendency metrics (Mean, Min, Max) for all score metrics.

   * Assess class engagement levels relative to attendance thresholds.

## 📈 Key Performance Metrics

Below is a summary of the core analytics generated from the dataset:

| Metric Category | Calculated Result | 
| ----- | ----- | 
| **Total Enrolled Students** | $20$ | 
| **Class Average CGPA** | $6.81$ | 
| **Top Performer** | **Ishita Kulkarni** ($\text{CGPA} = 9.30$, AIML) | 
| **Lowest Performer** | **Yash Thakur** ($\text{CGPA} = 3.17$, CSE) | 
| **Passing Percentage** | $90.0\%$ ($18$ Students) | 
| **Failing Percentage** | $10.0\%$ ($2$ Students) | 
| **Class Average Attendance** | $81.25\%$ ($\text{Range}: 55\% - 98\%$) | 
| **Highest Performing Subject** | **Mathematics** ($\text{Average Score} = 70.20$) | 

## 📚 Subject Performance Breakdown

| Subject | Maximum Score | Minimum Score | Mean Score | Standard Evaluation | 
| ----- | ----- | ----- | ----- | ----- | 
| **Python** | $95$ | $28$ | $67.05$ | Satisfactory | 
| **SQL** | $93$ | $29$ | $67.00$ | Satisfactory | 
| **Mathematics** | $95$ | $31$ | $70.20$ | Optimal | 

## 🛠️ Tech Stack

* **Core Language**: Python 3.8+

* **Data Manipulation**: `pandas`, `numpy`

* **Execution Environment**: Jupyter Notebook / Google Colab / VS Code

## 🚀 Installation & Getting Started

### Prerequisites

Ensure you have Python installed on your system along with `pip`.

```
# Clone the repository
git clone https://github.com/your-username/student-performance-analytics.git

# Navigate to project directory
cd student-performance-analytics

# Install required packages
pip install pandas numpy notebook

```

### Execution

1. Place the `student data_set.csv` file into the root directory.

2. Launch the Jupyter Notebook environment:

   ```
   jupyter notebook student_analytics.ipynb
   
   ```

3. Run all cells sequentially to view data checks and output analysis.

## 📜 Project Output Preview

```
------------------ STUDENT PERFORMANCE ANALYTICS SYSTEM ------------------
Total Students         : 20
Class Average CGPA     : 6.81
Highest CGPA           : 9.30 (Ishita Kulkarni)
Lowest CGPA            : 3.17 (Yash Thakur)
Passing Students       : 18 (90.0%)
Failing Students       : 2  (10.0%)
Top Performing Subject : Mathematics
------------------------ PROCESS COMPLETED SUCCESSFULLY ------------------

```