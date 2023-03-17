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

  <img src="https://github.com/dev18-kapadiaa/PostgreSQL-DB-Assessment/blob/main/Query-1.png">
  <hr>
  
  (2) Write a query to retrieve the first four characters of  EmpLname from the EmployeeInfo table.
 >SELECT SUBSTRING(EmpLname,1,4) AS "QUERY-2-OUTPUT" FROM EmployeeInfo;
 <br>
 Here we have used SUBSTRING function to slice the Last name. <br>
 <i>substring(str_pos , ext_char) 
 <pre> Where str_pos : Start position of string that is to be extracted, Index By default starts with 1.
       ext_char : Number of characters to be extracted. </pre></i>
  Here for first four characters of each Last name we have seclected each EmpLname column and corresponding last names one by one, and for each tuples applied SUBSTRING() function, which will be essentially slice last name to first 4 characters. 
  Hence, SUBSTRING(EmpLname ,1,4) will extract first 1 to 4 characters in the EmpLname one by one.
  
<b> Query Output : </b>

![Query-2](https://user-images.githubusercontent.com/125430631/225828386-ad30526d-48a0-4aed-ad20-5777cb2d583f.png)

(3) Write a query to find all the employees whose salary is between 50000 to 100000.
>SELECT * FROM EmployeeInfo NATURAL JOIN EmployeePosition WHERE Salary BETWEEN 50000 AND 100000;  <br>
><b>Alternative-2</b>   <br>
>SELECT * FROM EmployeeInfo INNER JOIN EmployeePosition USING(EmpID) WHERE Salary BETWEEN 50000 AND 100000;  <br>

Here we can use NATURAL JOIN and INNER JOIN both. NATURAL JOIN doesn't require to mention common columns on which join is supposed to apply.It by default takes common columns among both tables and join them accordingly.Here already EmpID is common in both tables.In INNER JOIN clause Joining field is required to mention using USING cluase or ON clause.
<p> Between is used to find all Values which resides between other two. </p>

<b> Query Output : </b>
<img src="https://github.com/dev18-kapadiaa/PostgreSQL-DB-Assessment/blob/main/Query-3.png">

(4) Write a query to find the names of employees that begin with ‘S’.

>SELECT EmpFname FROM EmployeeInfo WHERE EmpFname LIKE 'S%';
<p> Here we will use LIKE operator. Which is similar to the comparing string patterns through which data retrieal is takes place.
  <pre>
 The percent sign (%) represents zero, one, or multiple characters
 The underscore sign (_) represents one, single character</pre>
 
 Hence,To find employees name starts with S we will use S% which will essentially fetch EmpFname which starts with S. 
 
 <b> Query Output : </b>
 
