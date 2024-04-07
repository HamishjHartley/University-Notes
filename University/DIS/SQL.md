### 1. Implementing an ERD
`CREATE TABLE <name> (`
	`<col-def-1>,`
	`<col-def-2>,`
	`.`
	`.`
	`<col-def-n>,`
	`<constraint-1>,`
	`.`
	`.`
	`<constraint-k>`
`);`

For this ERD:
![](_attachments/Pasted%20image%2020240329152203.png)
`CREATE TABLE item(`
	`ID int NOT NULL,`
	`Description varchar(100),`
	`CONSTRAINT pkItem PRIMARY KEY(ID)`
`);`


Another ERD:
![](_attachments/Pasted%20image%2020240329152527.png)
`CREATE TABLE dept(`
`deptID int NOT NULL,`
`deptName varchar(100),`
`CONSTRAINT pkDept PRIMARY KEY(deptID)`
`);`

`CREATE TABLE emp(`
`empID int NOT NULL,`
`deptID int,`
`empName varchar(100),`
`CONSTRAINT pkemp PRIMARY KEY (empID),`
`CONSTRAINT fkemp FOREIGN KEY (deptID) REFERENCES dept(deptID)`
`);`

### 2. SQL: INSERT, UPDATE and DELETE

#### 2.1 INSERT
Following statements show INSERT into existing Dept table

| DeptID | DeptName |
| ------ | -------- |
| 1      | CS       |

`INSERT INTO Dept`
`(ID, Name)`
`VALUES (2, 'Phys')`

`INSERT INTO Dept`
`(Name, ID)`
`VALUES ('Mary', 2)`

`INSERT INTO Dept`
`VALUES (2, 'Phys')`

| DeptID | DeptName |
| ------ | -------- |
| 1      | CS       |
| 2      | Phys     |

#### 2.2 UPDATE

| DeptID | DeptName |
| ------ | -------- |
| 1      | CS       |
| 2      | Phys     |

`UPDATE dept`
`SET deptName = 'CSS'`
`WHERE deptID = '2';`

| DeptID | DeptName |
| ------ | -------- |
| 1      | CS       |
| 2      | CSS      |

`UPDATE dept`
`SET deptName = ''`
`WHERE deptID = '2';`

| DeptID | DeptName |
| ------ | -------- |
| 1      | CS       |
| 2      |          |

#### 2.3 DELETE
`DELETE FROM Dept`
`WHERE DeptID = 2;`

| DeptID | DeptName |
| ------ | -------- |
| 1      | CS       |

### 3. SQL: SELECT
#### 3.1 Syntax:
`SELECT`
	`[DISTINCT | ALL] <column-list>`
	`FROM <table-names>`
	`[WHERE <condition>]`
	`[ORDER BY <column-list>]`
	`[GROUP BY <column-list>]`
	`[HAVING <condition>]`
#### 3.2 Example
##### 1. List all the employee names who are working in Dept number 1
`SELECT empName`
`FROM emp`
`WHERE deptID =1;`
##### 2. List All the employee names who are working in the department 'CS'
`SELECT empName`
`FROM emp, dept`
`WHERE emp.deptID = dept.deptID AND dept.deptName = 'CS';`
