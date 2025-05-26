# SQL_ERROR_LOG
![image](https://github.com/user-attachments/assets/7602aeb4-0851-490d-badc-1d57dc5433cc)

"Ambiguous column name 'Dnumber'" — means that both the Employee and Department tables have a column named Dnumber, and SQL doesn't know which one to use.
#✅ Solution: Use table aliases or full table names to make it clear.
Here’s the corrected version of query using aliases:

"
SELECT E.Dnumber, COUNT(*) AS EmployeeCount
FROM Employee E
JOIN Department D ON E.Dnumber = D.Dnumber
GROUP BY E.Dnumber;

"

#Explanation:
--E is an alias for Employee

--D is an alias for Department

--E.Dnumber and D.Dnumber clearly indicate which table the column is from.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------

![image](https://github.com/user-attachments/assets/be302121-b99a-41e4-bd1a-1f654fca8505)


