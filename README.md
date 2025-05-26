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

🛠️ Error Report: Scalar Function CheckStudentName
📄 File: Sql Functions Demo.sql
🧪 Function: dbo.CheckStudentName


❌ Error Message:
Msg 455, Level 16, State 2, Procedure CheckStudentName, Line 18
The last statement included within a function must be a return statement.

🧩 Root Cause:
SQL Server scalar functions must end with a RETURN statement. The error was triggered because there was likely a trailing statement or a missing RETURN clause in the function logic.

✅ Fix Implemented:
The function was corrected by ensuring that every conditional branch ends in a RETURN statement, and that no executable code remains after the final RETURN.


    CREATE FUNCTION dbo.CheckStudentName(@StudentID INT)
    RETURNS VARCHAR(100)
    AS
    BEGIN
        DECLARE @FirstName NVARCHAR(50), @LastName NCHAR(10)

    SELECT @FirstName = St_Fname, @LastName = St_Lname
    FROM Student
    WHERE St_Id = @StudentID

    IF @FirstName IS NULL AND @LastName IS NULL
        RETURN 'First name & last name are null'
    ELSE IF @FirstName IS NULL
        RETURN 'First name is null'
    ELSE IF @LastName IS NULL
        RETURN 'Last name is null'
    ELSE
        RETURN 'First name & last name are not null'
    END;
    
📝 Notes:
Ensure no print/debug statements or logic exist after the final RETURN in scalar functions.

Always test your scalar functions in isolation to catch syntax/logic errors early.
