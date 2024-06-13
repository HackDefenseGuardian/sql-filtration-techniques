## Applying Filters to SQL Queries

[Complete Document](https://docs.google.com/document/d/1e0LF6zXJu_1757crjKKQwSq4M2aOFzTSAAcFfEagxUM/edit?usp=sharing)

This document explores how SQL filtering empowers security investigations and targeted employee updates.

### Project Overview

Our organization prioritizes robust security. SQL filtering plays a crucial role by allowing for focused analyses of login attempts and efficient employee updates.

### Filtering Login Attempts

* **After Hours:** To investigate suspicious after-hours activity, we filtered login attempts based on two conditions in the WHERE clause:
    * `TIME(login_time) > '18:00'`: Extracts and compares only the time portion, focusing on attempts after 6:00 PM.
    * `success = FALSE`: Filters for unsuccessful login attempts.
* **Specific Dates:** To examine activity on specific dates (e.g., May 8th and 9th, 2022), the WHERE clause utilized the OR operator:
    * `login_date = '2022-05-09' OR login_date = '2022-05-08'`: Targets login attempts from those two days.
* **Geographic Location:**  To investigate login attempts outside of Mexico, the WHERE clause used NOT and LIKE with a wildcard (%):
    * `NOT country LIKE 'MEX%'`: Excludes login attempts with country codes starting with "MEX" (including "MEX" and "MEXICO").

### Filtering Employees for Updates

* **Marketing Department:**  To pinpoint Marketing department machines for updates, the WHERE clause in the employees table had two conditions:
    * `department = 'Marketing'`: Filters for employees belonging to the Marketing department.
    * `office LIKE 'East%'`:  Leverages LIKE with a wildcard (%) to include offices starting with "East" (e.g., 'East-170' or 'East-320').
* **Finance or Sales Departments:**  To target Finance and Sales departments for separate security updates, the WHERE clause used the OR operator:
    * `department = 'Finance' OR department = 'Sales'`: Captures employees in either department.
* **Excluding IT Department:**  To exclude the IT department from a general security update rollout, the WHERE clause used NOT:
    * `department <> 'Information Technology'`: Ensures only employees outside the IT department are included.

### Summary

SQL filtering empowers security investigations and streamlines targeted updates. We used various operators (AND, OR, NOT, LIKE with wildcard %) to filter data from login_attempts and employees tables. This approach provided valuable security insights and efficient updates.
