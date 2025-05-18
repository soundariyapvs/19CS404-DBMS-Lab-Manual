# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**

Write the SQL query that achieves the selection of all columns from the "customer" table (aliased as "c"), with a left join on the "customer_id" column and a condition filtering for orders with an order date between '2012-07-01' and '2012-07-30'.

![Screenshot 2025-04-30 205951](https://github.com/user-attachments/assets/fc17f8bf-176c-4ef7-9245-e7d3d943bb81)

```
SELECT DISTINCT c.*
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id
WHERE o.ord_date BETWEEN '2012-07-01' AND '2012-07-30';
```

**Output:**

![Screenshot 2025-04-30 210000](https://github.com/user-attachments/assets/b8f3d1bc-e3de-44cd-979e-d030caf17727)


**Question 2**

From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 

![Screenshot 2025-04-30 210017](https://github.com/user-attachments/assets/1a28273b-28ef-48d3-ac54-c32fe238c387)

```
SELECT 
    c.cust_name,
    c.city,
    c.grade,
    s.name AS Salesman,
    s.city
FROM 
    customer c
JOIN
    salesman s
ON
    c.salesman_id = s.salesman_id
WHERE
    c.grade < 300
    ORDER BY c.customer_id ASC;
```

**Output:**

![Screenshot 2025-04-30 210028](https://github.com/user-attachments/assets/28b78479-1705-470f-b77f-7b2eaf297490)


**Question 3**

write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

Sample table: salesman

![Screenshot 2025-04-30 210036](https://github.com/user-attachments/assets/2a2c2541-d386-45f2-b4b7-494224e8ece1)

```
SELECT
    s.name AS Salesman,
    c.cust_name,
    c.city
FROM 
    salesman s
JOIN
    customer c
ON
    s.city = c.city;
```

**Output:**

![Screenshot 2025-04-30 210042](https://github.com/user-attachments/assets/71174bd3-d019-40e1-b71b-85a63b0d1e1f)


**Question 4**

 From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.  

Sample table: customer

![Screenshot 2025-04-30 210049](https://github.com/user-attachments/assets/bf742d78-2a34-45e4-bf3f-63f0eaf59d39)

```
SELECT 
    c.cust_name AS 'Customer Name',
    c.city,
    s.name AS Salesman,
    s.commission
FROM
    customer c
JOIN
    salesman s
ON
    c.salesman_id = s.salesman_id
WHERE 
    s.commission > 0.12;

```

**Output:**

![Screenshot 2025-04-30 210056](https://github.com/user-attachments/assets/bf9818d8-a815-42a4-8464-843e818e5f22)


**Question 5**

From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission. 

Sample table: orders

![Screenshot 2025-04-30 210106](https://github.com/user-attachments/assets/e69f49f1-cd04-4552-b7ac-5bea405499ca)

```
SELECT
    o.ord_no,
    o.ord_date,
    o.purch_amt,
    c.cust_name AS 'Customer Name',
    c.grade,
    s.name AS Salesman,
    s.commission
FROM 
    orders o
JOIN
    customer c
ON
    o.customer_id = c.customer_id
JOIN
    salesman s
ON
    c.salesman_id = s.salesman_id;


```

**Output:**

![Screenshot 2025-04-30 210118](https://github.com/user-attachments/assets/e8f02ce9-f008-4399-9755-406e59b98a60)


**Question 6**

Write the SQL query that accomplishes the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a non-null discharge date.


![Screenshot 2025-04-30 210128](https://github.com/user-attachments/assets/28364cfa-3e79-4b18-8ae0-7b4b32dc307f)

```
SELECT
    p.first_name AS patient_name,
    d.first_name AS doctor_name
FROM
    PATIENTS AS P
JOIN
    DOCTORS AS d
ON
    p.doctor_id = d.doctor_id
WHERE 
    p.discharge_date IS NOT NULL;
```

**Output:**

![Screenshot 2025-04-30 210134](https://github.com/user-attachments/assets/2782de36-9424-462f-81e1-2dadbbfe0673)


**Question 7**

Write the SQL query that achieves the selection of all columns from the "patients" table and the specialization from the "doctors" table (aliased as "doctor_specialization"), with an inner join on the "doctor_id" column.

![Screenshot 2025-04-30 210142](https://github.com/user-attachments/assets/43624908-393d-4b60-bb83-781296d9eca4)

```
SELECT
    p.*,
    d.specialization AS doctor_specialization
FROM
    patients p
JOIN
    doctors d
ON
    p.doctor_id = d.doctor_id;
```

**Output:**

![Screenshot 2025-04-30 210152](https://github.com/user-attachments/assets/097e6835-3b7e-4faa-8251-7c21035d60c0)


**Question 8**

SQL statement to generate a report with customer name, city, order number, order date, order amount, salesperson name, and commission to determine if any of the existing customers have not placed orders or if they have placed orders through their salesman or by themselves.

![Screenshot 2025-04-30 210208](https://github.com/user-attachments/assets/0ca6b012-32d5-4180-a073-91a53feb008b)

```
SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt AS 'Order Amount',
    s.name,
    s.commission
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id
LEFT JOIN salesman s ON c.salesman_id = s.salesman_id;
```


**Output:**

![Screenshot 2025-04-30 210220](https://github.com/user-attachments/assets/0893b632-7593-44b9-81db-c106a0c03a07)


**Question 9**

Write the SQL query that achieves the selection of all columns from the "customer" table (aliased as "c"), with a left join on the "customer_id" column and a condition filtering for orders with an order date later than '2012-08-17'.

![Screenshot 2025-04-30 210229](https://github.com/user-attachments/assets/74842f45-949f-4f20-b75d-627c012e85b0)

```
SELECT c.*
FROM customer c
LEFT JOIN orders o 
  ON c.customer_id = o.customer_id
WHERE o.ord_date > '2012-08-17';
```

**Output:**

![Screenshot 2025-04-30 210241](https://github.com/user-attachments/assets/0aa6ffe9-4055-4be8-9b1a-056aaf6f7f9f)


**Question 10**

Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name"), with an inner join on the "doctor_id" column and conditions filtering for patients whose doctor has the first name 'Emily', last name 'Johnson', and a non-null discharge date.

![Screenshot 2025-04-30 210249](https://github.com/user-attachments/assets/d0cdb4b0-ba78-4018-936e-7721e99b4d4b)

```
SELECT p.first_name AS patient_name
FROM patients p
INNER JOIN doctors d
  ON p.doctor_id = d.doctor_id
WHERE d.first_name = 'Emily'
  AND d.last_name = 'Johnson'
  AND p.discharge_date IS NOT NULL;
```


**Output:**

![Screenshot 2025-04-30 210254](https://github.com/user-attachments/assets/60063670-7b4a-44f1-be07-906031328578)



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.

![image](https://github.com/user-attachments/assets/63b88840-8a36-49d4-8991-bcf3d71e27b8)

