# 🏢 Employee System | SQL DQL Analysis Dashboard

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![SQL](https://img.shields.io/badge/SQL-Data_Query_Language-336791?style=for-the-badge&logo=database&logoColor=white)

> **An interactive, browser-based execution environment designed to visualize and practice advanced SQL Data Query Language (DQL) statements on a relational corporate database.**

## 📖 Overview

This project serves as an educational and portfolio dashboard demonstrating proficiency in extracting business intelligence from a relational database. It focuses entirely on **Data Query Language (DQL)**, answering 8 specific business constraints ranging from employee role tracking to departmental financial expenditures.

Instead of static code snippets, this repository features a **Single-Page Application (SPA)** with an integrated "Execution Engine" that simulates database latency and renders the exact result tables for each query.

---

## 🗄️ Database Schema

The queries in this dashboard operate on a 4-table relational database modeling an Employee-Project allocation system:

* **Department:** `Num_S` (PK), `Label`, `Manager_Name`
* **Employee:** `Num_E` (PK), `Name`, `Position`, `Salary`, `Department_Num_S` (FK)
* **Project:** `Num_P` (PK), `Title`, `Start_Date`, `End_Date`, `Department_Num_S` (FK)
* **Employee_Project:** `Employee_Num_E` (PK/FK), `Project_Num_P` (PK/FK), `Role` *(Associative/Bridging Table)*

---

## 🧠 SQL Concepts Demonstrated

The dashboard executes 8 unique business queries that showcase the following SQL competencies:

1.  **Many-to-Many Traversal:** Chaining multiple `INNER JOIN` statements to bridge `Employee` and `Project` via the `Employee_Project` table.
2.  **Data Aggregation:** Utilizing `SUM()` for financial totals and `COUNT()` for headcounts.
3.  **Advanced Filtering:** Using the `HAVING` clause to filter aggregated groups (e.g., finding employees assigned to strictly > 1 project).
4.  **Outer Joins:** Implementing `LEFT JOIN` to ensure projects with zero assigned employees still appear in headcount reports.
5.  **Data Sorting & Limiting:** Using `ORDER BY` and `LIMIT` (or `TOP`) to isolate extreme values, such as identifying the largest department.

---

## 🚀 Quick Start

This dashboard is built entirely with frontend technologies. No local database server (like MySQL or SQL Server) is required to view the code and execution results.

1.  Clone or download this repository.
2.  Locate the `employee_dql_analysis.html` file.
3.  **Double-click** to open it in any modern web browser (Chrome, Edge, Firefox, Safari).
4.  Navigate using the sidebar and click **"▶ Run Query"** on any tab to simulate execution and view the data outputs.

---

## 💻 Sample Query Highlight

**Objective:** *Retrieve a summary of roles employees have across different projects, including the employee name, project title, and role.*

```sql
SELECT E.Name AS Employee_Name, P.Title AS Project_Title, EP.Role
FROM Employee E
JOIN Employee_Project EP ON E.Num_E = EP.Employee_Num_E
JOIN Project P ON EP.Project_Num_P = P.Num_P
ORDER BY P.Title, E.Name;
