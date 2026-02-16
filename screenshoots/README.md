# <span style="color:#1F77B4">Oracle Pluggable Database Assignment II</span>

## <span style="color:#FF7F0E">Student Information</span>

Name: Winny Nakunda

Student ID: 27959

Course: Database Development with PL/SQL (INSY 8311)

---

### <span style="color:#2CA02C">Tasks Completed:</span>
1. Creating a PDB
2. Switching between containers
3. Managing users inside a PDB
4. Opening and dropping a PDB
5. Basic database monitoring

---








## <span style="color:#D62728">Oracle Environment</span>

| Property | Details |
|----------|---------|
| **Oracle Version** | Oracle 21c |
| **Operating System** | Windows 10 |
| **Container Database** | ORCL21 |
| **Storage Location** | C:\oracle21c\oradata\ORCL21 |

---

## <span style="color:#9467BD">Task Explanations</span>

### <span style="color:#1F77B4">Task 1: PDB Creation</span>

1. Creation of a New PDB

A new pluggable database named wi_pdb_27959 was created inside the root container.
An administrative user was defined during the creation process.

CREATE PLUGGABLE DATABASE wi_pdb_27959
ADMIN USER winny_plsqlauca_27959 IDENTIFIED BY Nankunda12@
FILE_NAME_CONVERT = (
'C:\oracle21c\oradata\ORCL21\pdbseed',
'C:\oracle21c\oradata\ORCL21\wi_pdb_27959');


This step confirmed my understanding of how Oracle clones the seed database to generate a new PDB.
![Task 1 Screenshot](https://github.com/Winny-Nankunda/oracle_pdb_ass_ll_27959_winny/blob/main/screenshoots/1.%20db_created.PNG)

2. Switching to the Created PDB

After creating the PDB, I changed the session container and confirmed the active database.

ALTER SESSION SET CONTAINER = wi_pdb_27959;
SHOW CON_NAME;


This ensured that all next operations were executed inside the correct pluggable database.

![Task 1 Screenshot](https://github.com/Winny-Nankunda/oracle_pdb_ass_ll_27959_winny/blob/main/screenshoots/2.%20db_created.PNG)

3. Verifying the Admin User

To confirm that the administrative user was successfully created, I queried the DBA_USERS table.

SELECT username 
FROM dba_users
WHERE username = 'WINNY_PLSQLAUCA_27959';


The result verified that the user exists and has been properly configured inside the PDB.

![Task 1 Screenshot](https://github.com/Winny-Nankunda/oracle_pdb_ass_ll_27959_winny/blob/main/screenshoots/3.%20check_user_existance.PNG)

4. Creating a Temporary PDB for Testing

To demonstrate full lifecycle management, I created another PDB intended for testing and deletion.

ALTER SESSION SET CONTAINER = CDB$ROOT;

CREATE PLUGGABLE DATABASE wi_to_delete_pdb_27959
ADMIN USER tempadmin IDENTIFIED BY Temp123@
FILE_NAME_CONVERT = (
'C:\oracle21c\oradata\ORCL21\pdbseed',
'C:\oracle21c\oradata\ORCL21\wi_to_delete_pdb_27959');


This showed that I can work from the root container and manage multiple PDBs.
![Task 1 Screenshot](https://github.com/Winny-Nankunda/oracle_pdb_ass_ll_27959_winny/blob/main/screenshoots/4.%20temp_db_created.PNG)
 
5. Opening and Verifying the Temporary PDB
ALTER PLUGGABLE DATABASE wi_temp_pdb_27959 OPEN;
SHOW PDBS;

![Task 1 Screenshot](https://github.com/Winny-Nankunda/oracle_pdb_ass_ll_27959_winny/blob/main/screenshoots/5.%20prove_temp_db_created.PNG)

The output displayed all available PDBs, confirming successful creation and activation.

6. Dropping the Temporary PDB

After verification, I removed the temporary PDB including its datafiles.

ALTER PLUGGABLE DATABASE wi_temp_pdb_27959 CLOSE IMMEDIATE;

DROP PLUGGABLE DATABASE wi_temp_pdb_27959 INCLUDING DATAFILES;

SHOW PDBS;


![Task 1 Screenshot](https://github.com/Winny-Nankunda/oracle_pdb_ass_ll_27959_winny/blob/main/screenshoots/6.%20temp_pdb_deleted.PNG)

This step demonstrates proper cleanup and database resource management.

### <span style="color:#1F77B4">Task 7: Oracle Enterprise Manager (OEM)</span>

Demonstrates access to Oracle Enterprise Manager console for centralized database administration and monitoring.

![Task 7 Screenshot](./screenshoots/final_img.PNG)

---
Student Name: Winny Nakunda
Date: February 2026
