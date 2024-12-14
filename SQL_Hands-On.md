# Oracle SQL Queries

## Table of Contents
- [Q1 - Employee Count](#q1-employee-count)
- [Q2 - Display Department Details](#q2-display-department-details)
- [Q3 - Display Non-Programmer Department Name](#q3-display-non-programmer-department-name)
- [Q4 - Department Wise Skill](#q4-department-wise-skill)
- [Q5 - Find Items Not Ordered](#q5-find-items-not-ordered)

---

## Q1 - Employee Count

**Query:**  
Write the SQL query to display the count of employees in each department, ordered by the count in descending order. If multiple departments have the same number of employees, sort them by department name.

**Solution:**

```sql
SELECT Departments.deptName, COUNT(Employees.eDeptId) 
FROM Departments 
LEFT JOIN Employees ON Departments.deptId = Employees.eDeptId 
GROUP BY Departments.deptId, Departments.deptName 
ORDER BY COUNT(Employees.eDeptId) DESC, Departments.deptName;

---

## Q2 - Display Department Details

**Query:**  
Write the SQL query to display the department ID and name of departments located on the "Ground Floor".

**Solution:**

```sql
SELECT Dept_Id, Dept_Name 
FROM Department 
WHERE Dept_Location = 'Ground Floor';

---

## Q3 - Display Non-Programmer Department Name

**Query:**  
Write the SQL query to print the names of the departments that do not have any Programmers.

**Solution:**

```sql
SELECT d.Dept_name
FROM Departments d
LEFT JOIN Employees e ON d.Dept_Id = e.Emp_Dept_Id AND e.Emp_Skill = 'Programmer'
WHERE e.Emp_Dept_Id IS NULL;

---

## Q4 - Department Wise Skill

**Query:**  
Write the SQL query to print the department-wise skills of the employees working in each department.  
If more than one employee in a department has the same skill, the skill should be printed once only.

**Solution:**

```sql
SELECT d.Dept_Name, e.Emp_Skill
FROM Departments d
JOIN Employees e ON d.Dept_Id = e.Emp_Dept_Id
GROUP BY d.Dept_Name, e.Emp_Skill
ORDER BY d.Dept_Name DESC, e.Emp_Skill ASC;

---

## Q5 - Find Items Not Ordered

**Query:**  
Write the SQL query to display the name of the item/items for which no orders have been placed.

**Solution:**

```sql
SELECT i.Item_Name
FROM Items i
LEFT JOIN Orders o ON i.Item_Id = o.Item_Id
WHERE o.Item_Id IS NULL;