# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

*Question 1*
How many prescriptions were written in each frequency category (e.g., once daily, twice daily)?

Sample tablePrescriptions Table
![Screenshot 2025-04-30 200726](https://github.com/user-attachments/assets/0171e4c9-e8d0-4f27-af88-2fff3620c673)

```
SELECT Frequency, COUNT(*) AS TotalPrescriptions
FROM Prescriptions
GROUP BY Frequency;
```


*Output:*


![Screenshot 2025-04-30 200735](https://github.com/user-attachments/assets/f9500498-c96b-4a0c-bef6-a242b9069ae4)



*Question 2*

What is the average dosage prescribed for each medication?

Sample tablePrescriptions Table

![Screenshot 2025-04-30 200749](https://github.com/user-attachments/assets/fae733df-f2ce-49d5-88f0-1817aec5d41d)

```
SELECT Medication , Avg(Dosage) AS "AvgDosage"
FROM  Prescriptions
GROUP BY Medication;
```

*Output:*

![Screenshot 2025-04-30 200805](https://github.com/user-attachments/assets/77ade200-efe0-4f58-9dd0-33581645665e)




*Question 3*
How many appointments are scheduled for each doctor?

Sample table:Appointments Table

![Screenshot 2025-04-30 200811](https://github.com/user-attachments/assets/f0ca394d-db7c-454e-af48-fb311e283618)

```
SELECT DoctorID, COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DoctorID;
```

*Output:*

![Screenshot 2025-04-30 200816](https://github.com/user-attachments/assets/9f33e948-ef91-41c1-9613-26974789c172)



*Question 4*

Write a SQL query to return the total number of rows in the 'customer' table where the city is Noida.

Sample table: customer

![Screenshot 2025-04-30 200821](https://github.com/user-attachments/assets/cb92b4fa-36ce-46d8-8170-00d2d9b6890d)

```
SELECT COUNT(*) AS COUNT
FROM customer
WHERE city='Noida';
```

*Output:*


![Screenshot 2025-04-30 200825](https://github.com/user-attachments/assets/e7b48376-050e-4869-9152-5bab22e2541a)



*Question 5*

Write a SQL query to find the number of employees who are having the same age removing the duplicate values.

Sample table: employee

![Screenshot 2025-04-30 200830](https://github.com/user-attachments/assets/3ef0377b-62ec-4d12-9ba6-73721f268568)

```
SELECT COUNT(DISTINCT age) AS COUNT
FROM employee;
```

*Output:*

![Screenshot 2025-04-30 200835](https://github.com/user-attachments/assets/f3e72793-0052-4c10-b022-1e0695236762)



*Question 6*

Write a SQL query to calculate the average purchase amount of all orders. Return average purchase amount.

Sample table: orders

![Screenshot 2025-04-30 200843](https://github.com/user-attachments/assets/8955ba44-eb3c-4f9a-a7cd-461b407dac55)

```
SELECT AVG(purch_amt) AS AVERAGE
FROM orders;
```

*Output:*

![Screenshot 2025-04-30 200848](https://github.com/user-attachments/assets/8fb501c1-1ff0-4805-b038-929552c00872)




*Question 7*

Write a SQL query to find the Fruit with the lowest available quantity.

Note: Inventory attribute contains amount of fruits

![Screenshot 2025-04-30 200851](https://github.com/user-attachments/assets/1b22b87c-3858-4082-b88c-13031a36c7bd)

```
SELECT name AS fruit_name ,inventory AS lowest_quantity
FROM fruits
ORDER BY inventory ASC
LIMIT 1;
```


*Output:*

![Screenshot 2025-04-30 200855](https://github.com/user-attachments/assets/d29dde6b-cd4a-48bb-a9cf-67a8ad33368f)


*Question 8*

Write the SQL query that achieves the grouping of data by city, calculates the total income for each city, and includes only those cities where the total income sum is greater than 200,000.

Sample table: employee

![Screenshot 2025-04-30 200901](https://github.com/user-attachments/assets/0d768ea4-3e77-4c03-8f4b-14c71c7967bd)

```
SELECT city, SUM(income) AS Income
FROM employee
Group by city
HAVING income >200000;
```

*Output:*

![Screenshot 2025-04-30 200905](https://github.com/user-attachments/assets/bdcf48ff-711c-4340-a462-a2d182d9a42d)



*Question 9*

Write the SQL query to find how many patients have more than 3 medical records?.

Sample table: MedicalRecords

![Screenshot 2025-04-30 200910](https://github.com/user-attachments/assets/89d9060d-4a14-423e-8bc0-06fba5333925)

```
SELECT PatientID, Count(*) AS TotalRecords
FROM MedicalRecords
GROUP BY PatientID
Having COUNT(*)>3;
```


*Output:*

![Screenshot 2025-04-30 200914](https://github.com/user-attachments/assets/5c9daa93-74a9-4f58-b5a7-38d4dbcf9f87)


*Question 10*

Write the SQL query that achieves the grouping of data by occupation, calculates the average work hours for each occupation, and includes only those occupations where the average work hour falls between 10 and 12.

Sample table: employee1

![Screenshot 2025-04-30 200919](https://github.com/user-attachments/assets/fcfcdf4f-dd32-42d1-9d5a-b8452ca5f852)

```
SELECT occupation , AVG(workhour)AS"AVG(workhour)"
FROM employee1
GROUP BY occupation
having avg(workhour) BETWEEN 10 AND 12;
```

*Output:*

![Screenshot 2025-04-30 200923](https://github.com/user-attachments/assets/97f887bf-cc2d-4e5e-9906-77a74318c04d)


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
![Screenshot 2025-04-30 221800](https://github.com/user-attachments/assets/e62cc684-d592-407d-a000-549ed3c69580)

