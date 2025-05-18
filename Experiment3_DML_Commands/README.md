# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```



*Question 1*

Write a SQL statement to Change the category to 'Household' where product name contains 'Detergent' in the products table.

Products Table 

![Screenshot 2025-04-30 192701](https://github.com/user-attachments/assets/ed5c78a7-dfe7-403a-9272-90711d0b0d27)

```
UPDATE Products
SET category= 'Household'
WHERE product_name LIKE '%Detergent%';
```

*Output:*

![Screenshot 2025-04-30 192711](https://github.com/user-attachments/assets/74787948-4d03-4f9b-ace6-4e74329324af)



*Question 2*

Decrease the reorder level by 30 percent where the product name contains 'cream' and quantity in stock is higher than reorder level in the products table.

PRODUCTS TABLE
![Screenshot 2025-04-30 192722](https://github.com/user-attachments/assets/a0dafb09-0bc8-4aa1-bfa0-35aa56f76ae3)

```
UPDATE PRODUCTS
SET reorder_lvl =reorder_lvl *0.7
WHERE product_name  LIKE '%cream%'
AND quantity  > reorder_lvl;
```

*Output:*

![Screenshot 2025-04-30 192732](https://github.com/user-attachments/assets/e37c7017-ee8d-48f0-944c-443cf4f11204)


*Question 3*

Write a SQL statement to Increase the selling price by 10% for all products in the 'Bakery' category in the products table.

Products table

![Screenshot 2025-04-30 192741](https://github.com/user-attachments/assets/8ef19ff3-993d-44ee-9ba9-cb856085ea25)

```
UPDATE Products
SET sell_price=sell_price*1.10
WHERE category LIKE '%Bakery%';
```

*Output:*

![Screenshot 2025-04-30 192749](https://github.com/user-attachments/assets/3d1d1b6c-0347-42ea-9f53-f5d6b21d2f7d)


*Question 4*

Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN'

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id


![Screenshot 2025-04-30 192759](https://github.com/user-attachments/assets/fd0b37b1-27c8-4e25-87a9-fc8b50d69984)

```
UPDATE Employees
SET salary=2*salary
WHERE department_id=20
AND job_id LIKE '%MAN%';
```


*Output:*

![Screenshot 2025-04-30 192807](https://github.com/user-attachments/assets/340dad5d-f2bc-48bf-bf66-77be30e28536)




*Question 5*

Write a SQL statement to change the email column of employees table with 'Unavailable' for all employees in employees table.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

![Screenshot 2025-04-30 192815](https://github.com/user-attachments/assets/cf922c4c-21bd-4bc6-9568-24e53618d8e7)

```
UPDATE Employees 
SET email='Unavailable';
```

*Output:*

![Screenshot 2025-04-30 192825](https://github.com/user-attachments/assets/1294e03e-45e8-4925-afe3-dfc7ae727a60)



*Question 6*

Write a SQL query to Delete customers from 'customer' table where 'GRADE' is greater than or equal to 2.

![Screenshot 2025-04-30 192836](https://github.com/user-attachments/assets/d407c442-52c4-4003-a626-07777a429ba3)

```
DELETE FROM Customer
WHERE Grade>=2;
```


*Output:*


![Screenshot 2025-04-30 192845](https://github.com/user-attachments/assets/de4752a4-092c-4e43-832f-cec187a02bf6)



*Question 7*
Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_country' must be 'India',

2. 'cus_city' must not be 'Chennai',


![Screenshot 2025-04-30 192858](https://github.com/user-attachments/assets/893d7fcf-4262-4829-b02f-899b319d3b9f)

```
DELETE FROM Customer
WHERE CUST_COUNTRY = 'India'
AND CUST_CITY <>'Chennai';
```


*Output:*


![Screenshot 2025-04-30 192909](https://github.com/user-attachments/assets/a71a0fac-efed-4ae7-a7b6-d6e698ef9c97)



*Question 8*

Write a SQL query to Delete customers with following conditions

'CUST_COUNTRY' is not in a list of specified countries ('UK', 'USA', 'Canada')
'GRADE' is greater than or equal to 3

![Screenshot 2025-04-30 192919](https://github.com/user-attachments/assets/4576cb84-cceb-4d22-aa93-eb4d68577a2d)

```
DELETE FROM Customer
WHERE CUST_COUNTRY NOT IN ('UK', 'USA', 'Canada')
AND GRADE >=3;
```

*Output:*

![Screenshot 2025-04-30 192942](https://github.com/user-attachments/assets/c162108f-35b4-4f23-9e98-1811e59e5348)


*Question 9*

Write a SQL query to Delete All Doctors with a NULL Specialization

![Screenshot 2025-04-30 192951](https://github.com/user-attachments/assets/221432fe-18e0-45bf-b96f-717c0ac3aa9e)

```
DELETE FROM Doctors
WHERE specialization IS NULL;
```

*Output:*


![Screenshot 2025-04-30 192957](https://github.com/user-attachments/assets/9dd053ba-470c-469e-9028-46d40dde3d37)




*Question 10*

Write a SQL query to Delete All Doctors with a NULL Last Name

![Screenshot 2025-04-30 193004](https://github.com/user-attachments/assets/a088d915-0f29-4974-9760-e5ffd7ba079f)

```
DELETE FROM Doctors
WHERE last_name IS NULL;
```

*Output:*

![Screenshot 2025-04-30 193008](https://github.com/user-attachments/assets/038721b3-0fce-40d5-91fb-c64a5d9fbca8)



## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.

![Screenshot 2025-04-30 221853](https://github.com/user-attachments/assets/b3a04ad6-8994-40fb-8043-1730cb5343a8)

