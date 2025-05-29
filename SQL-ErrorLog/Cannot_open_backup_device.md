## 💡 SQL Server Backup Error: "Cannot open backup device"

When attempting to back up a SQL Server database using the following command:

```sql
BACKUP DATABASE TrainingDB TO DISK = 'C:\Backups\TrainingDB_Full.bak';


✅ Solution
This error occurs because the specified folder path (C:\Backups\) does not exist or SQL Server does not have permission to access it.

To resolve the issue:

1. Create the Directory
Ensure the directory C:\Backups\ exists on your system. You can create it manually using File Explorer or with a command like:

powershell
Copy
Edit
mkdir C:\Backups
2. Verify Permissions
Make sure the SQL Server service account has write access to the folder.

You can check the service account in SQL Server Configuration Manager under SQL Server Services → Log On As.

3. Alternatively, Use an Existing Writable Folder
Update the BACKUP DATABASE command to use a folder that is already writable, such as:

sql
Copy
Edit
BACKUP DATABASE TrainingDB TO DISK = 'C:\Temp\TrainingDB_Full.bak';
Ensure the C:\Temp folder exists.