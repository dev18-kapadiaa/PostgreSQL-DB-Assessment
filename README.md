# PostgreSQL-DB-Assessment

## Table Creation 


(i) <b>EmployeeInfo Table :</b>


>CREATE TABLE EmployeeInfo( <br>
>EmpID SERIAL NOT NULL,   <br>
>EmpFname VARCHAR(100), <br>
>EmpLname VARCHAR(100) , <br>
>Department VARCHAR(100), <br>
>Project VARCHAR(50),   <br>
>Address VARCHAR(200),   <br>
>DOB DATE,           <br>
>Gender CHAR   <br>
> );
>
>
> INSERT into EmployeeInfo (EmpFname,EmpLname,Department,Project,Address,DOB,Gender) VALUES ('Sanjay','Mehra','HR','P1','Hyderabad(HYD)','1-12-1976' , 'M'); <br>
>INSERT into EmployeeInfo (EmpFname,EmpLname,Department,Project,Address,DOB,Gender) VALUES ('Ananya','Mishra','Admin','P2','Delhi(DEL)','02-05-1968', 'F');  <br>
>insert into EmployeeInfo (EmpFname,EmpLname,Department,Project,Address,DOB,Gender) VALUES ('Rohan','Diwan','Account','P3','Mumbai(BOM)','01-01-1980', >'M');  <br>
>insert into EmployeeInfo (EmpFname,EmpLname,Department,Project,Address,DOB,Gender) VALUES ('Sonia','Kulkarni','HR','P1','Hyderabad(HYD)','02-05-1992', > 'F');  <br>
>insert into EmployeeInfo (EmpFname,EmpLname,Department,Project,Address,DOB,Gender) VALUES ('Ankit','Kapoor','Admin','P2','Delhi(DEL)','03-07-1994', 'M');

<b>Query Output :</b>
![Table_creation_employeeInfo](https://user-images.githubusercontent.com/125430631/225819092-5f69f6aa-829b-469a-a778-37aea2db290d.png)

(ii) <b>EmployeePosition Table </b>

>CREATE TABLE EmployeePosition(   <br>
>  EmpID INTEGER ,                 <br>
>  EmpPosition VARCHAR(50) ,    <br>
>  DateOfJoining DATE,    <br>
>  Salary NUMERIC,   <br>
>  FOREIGN KEY(EmpID) REFERENCES EmployeeInfo(EmpID)  <br>
>  );   <br> 
>INSERT INTO EmployeePosition(EmpID,EmpPosition,DateOfJoining,Salary) VALUES(1,'Manager','01-05-2022',500000);   <br>
>INSERT INTO EmployeePosition(EmpID,EmpPosition,DateOfJoining,Salary) VALUES(2,'Executive','02-05-2022',75000);   <br>
>INSERT INTO EmployeePosition(EmpID,EmpPosition,DateOfJoining,Salary) VALUES(3,'Manager','01-05-2022',90000);   <br>
>INSERT INTO EmployeePosition(EmpID,EmpPosition,DateOfJoining,Salary) VALUES(4,'Lead','02-05-2022',85000);  <br>
>INSERT INTO EmployeePosition(EmpID,EmpPosition,DateOfJoining,Salary) VALUES(5,'Executive','01-05-2022',300000);  <br>
>SELECT * FROM EmployeePosition 

<b> Query Output : </b>
![Table_creation_employeePosition](emp_position.png)


## Queries:
(1) Write a query to fetch the number of employees working in the department ‘Admin’. <br>
> SELECT COUNT(*) query_one_output FROM EmployeeInfo WHERE Department='Admin';

<br>
<p> Here COUNT(*) will fetch all the rows Where Department name is "Admin" and field is renames as "query_one_output".<p>

