# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**

Write an SQL query to add a new column email of type TEXT to the Student_details table, and ensure that this column cannot contain NULL values and make default value as 'Invalid'

![Screenshot 2025-04-30 211440](https://github.com/user-attachments/assets/30738c98-0273-4bb4-adef-0448ccdc4847)

```
ALTER TABLE Student_details
ADD COLUMN email TEXT NOT NULL DEFAULT 'Invalid';
```

**Output:**

![Screenshot 2025-04-30 211452](https://github.com/user-attachments/assets/bb76e797-a099-4883-951e-946737e167eb)


**Question 2**

Write a SQL query to add birth_date attribute as timestamp (datatype) in the table customer 

Sample table: customer

![Screenshot 2025-04-30 211502](https://github.com/user-attachments/assets/e43a6bad-3ab1-4e11-9a71-bd8d9b6f24ee)

```
ALTER TABLE customer
ADD COLUMN birth_date timestamp;
```


**Output:**

![Screenshot 2025-04-30 211512](https://github.com/user-attachments/assets/9148c6a2-2936-4fa1-9aa8-435964e4d3b8)


**Question 3**

Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.

![Screenshot 2025-04-30 211518](https://github.com/user-attachments/assets/b70fa099-a880-43df-b1a1-55405c6e805e)

```
CREATE TABLE Invoices(
InvoiceID INTEGER PRIMARY KEY,
InvoiceDate DATE,
DueDate DATE CHECK(DueDate>InvoiceDate),
Amount REAL CHECK(Amount>0));
```

**Output:**

![Screenshot 2025-04-30 211526](https://github.com/user-attachments/assets/094e48bd-0896-4055-9acf-38d4a24a271f)


**Question 4**

Insert all students from Archived_students table into the Student_details table.

![Screenshot 2025-04-30 211541](https://github.com/user-attachments/assets/f03d99d8-feb9-4946-bb67-c67c50fa2446)

```
INSERT INTO Student_details(RollNo,Name,Gender, Subject,MARKS)
SELECT RollNo,Name, Gender, Subject,MARKS 
FROM Archived_students
```

**Output:**

![Screenshot 2025-04-30 211549](https://github.com/user-attachments/assets/0119009f-6695-4958-a36f-fda0c1648947)


**Question 5**

Create a table named Customers with the following columns:

CustomerID as INTEGER
Name as TEXT
Email as TEXT
JoinDate as DATETIME

![Screenshot 2025-04-30 211602](https://github.com/user-attachments/assets/5a7129ed-9230-4d51-8431-d4c17e6b62b4)

```
CREATE TABLE Customers(CustomerID INTEGER,
Name TEXT,
Email TEXT,
JoinDate DATETIME);
```

**Output:**

![Screenshot 2025-04-30 211610](https://github.com/user-attachments/assets/03fefb4b-27e9-48bd-98ad-8f15f51d2cde)


**Question 6**

Create a new table named orders with the following specifications:
ord_id as TEXT with a length of 4.
item_id as TEXT.
ord_date as DATE.
ord_qty as INTEGER.
cost as INTEGER.
The primary key is a composite key consisting of item_id and ord_date.
ord_id and item_id should not accept NULL

![Screenshot 2025-04-30 211617](https://github.com/user-attachments/assets/9724fc6d-f253-4872-a570-fac96c6def38)

```
CREATE TABLE orders(ord_id  TEXT CHECK(LENGTH(ord_id)=4) NOT NULL,
item_id TEXT NOT NULL,
ord_date DATE,
ord_qty INTEGER ,
cost INTEGER,
PRIMARY KEY(item_id,ord_date)
);
```


**Output:**

![Screenshot 2025-04-30 211623](https://github.com/user-attachments/assets/9dca1ac7-10f5-4729-8989-24472f294f76)


**Question 7**

Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

![Screenshot 2025-04-30 211632](https://github.com/user-attachments/assets/9fdfecb3-fb67-4f4c-817a-75fd1f682633)

```
CREATE TABLE Invoices(InvoiceID INTEGER,InvoiceDate DATE,Amount REAL,DueDate DATE CHECK(DueDate>InvoiceDate),OrderID INTEGER ,
FOREIGN KEY (OrderID) REFERENCES Orders(OrderID));
```

**Output:**

![Screenshot 2025-04-30 211639](https://github.com/user-attachments/assets/0620978f-c9c3-443f-9d13-7633f83e10b2)


**Question 8**

Insert the below data into the Customers table, allowing the City and ZipCode columns to take their default values.

![Screenshot 2025-04-30 211645](https://github.com/user-attachments/assets/555c519d-515f-46df-b7d1-5df087f8b57c)

```
INSERT INTO Customers(CustomerID, Name, Address)
VALUES
(304,'Peter Parker','Spider St');
```




**Output:**

![Screenshot 2025-04-30 211653](https://github.com/user-attachments/assets/5252ff02-80bf-48f3-91aa-7712ae2d5165)


**Question 9**

Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

![Screenshot 2025-04-30 211745](https://github.com/user-attachments/assets/e56009b1-97ab-44fd-ab63-98fee17c9be5)

```
CREATE TABLE ProjectAssignments(
AssignmentID INTEGER PRIMARY KEY,
EmployeeID INTEGER,
ProjectID INTEGER,
AssignmentDate DATE NOT NULL,
FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID) 
);
```


**Output:**

![Screenshot 2025-04-30 211752](https://github.com/user-attachments/assets/90bc74c7-585d-4f90-99ad-9f9c2257c507)


**Question 10**

In the Student_details table, insert a student record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

![Screenshot 2025-04-30 211709](https://github.com/user-attachments/assets/2a6de218-94c1-44a8-af8a-4ed4c39e786e)

```
INSERT INTO Student_details (RollNo      ,Name         ,Gender      ,Subject    , MARKS)
VALUES(205,'Olivia Green','F',NULL,NULL),
(207,'Liam Smith','M','Mathematic','85'),
(208,'Sophia Johns','F','Science',NULL);
```

**Output:**

![Screenshot 2025-04-30 211715](https://github.com/user-attachments/assets/46bbfda9-17ef-4d11-8bbd-b9641650db24)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.

![Screenshot 2025-04-30 222350](https://github.com/user-attachments/assets/3e58a8a3-cd73-4646-8080-fe94588248bd)


