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

**Question 1**
--
Sample table:Appointments Table

![image](https://github.com/user-attachments/assets/d7ebb841-8a85-4c53-acdd-6b509f6a956a)


Answer: SELECT strftime('%H',AppointmentDateTime) AS HourOfDay, COUNT(*) AS TotalAppointments FROM Appointments GROUP BY strftime('%H',AppointmentDateTime) ORDER BY HourOfDay;

**Output:**

![image](https://github.com/user-attachments/assets/b65dfb92-2fef-4003-8aec-1eb0ffa4b1b6)


**Question 2**
---
How many patients are there in each age group category (e.g., under 20, 20-30, 30-40, etc.)? Sample table: Patients Table

Answer:

![image](https://github.com/user-attachments/assets/3ae6cd58-b757-4095-952c-3dbf7f14407a)

**Output:**

![image](https://github.com/user-attachments/assets/ce06755b-23af-4810-82f9-41c97d649268)


**Question 3**
---
How many prescriptions were written in each frequency category (e.g., once daily, twice daily)? Sample tablePrescriptions Table

Answer: SELECT
Frequency, COUNT(*) AS TotalPrescriptions FROM Prescriptions GROUP BY Frequency ORDER BY Frequency;

**Output:**

![image](https://github.com/user-attachments/assets/320c8e05-d6dd-400c-834a-4b33a11bbb44)


**Question 4**
---
Write a SQL query to Calculate the average income of the employees with names starting with 'A':
Table: employee

![image](https://github.com/user-attachments/assets/7b8f625b-c184-47d0-98bb-e747bbd802be)

Answer: SELECT
AVG(income) AS avg_income FROM employee WHERE name LIKE 'A%';
**Output:**

![image](https://github.com/user-attachments/assets/96f82f6e-67e0-485a-a82b-58ee844e76e4)


**Question 5**
---
Write a SQL query to calculate the total number of working hours of all employees Sample table: employee1

Answer:

SELECT
SUM(workhour) AS "Total working hours" FROM employee1;

**Output:**

![image](https://github.com/user-attachments/assets/c3088c92-b2c1-4ef4-8ea2-41cd47fc0cb0)

**Question 6**
---
Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.

Sample table: orders
![image](https://github.com/user-attachments/assets/4f76738a-abbb-42ed-a9a9-4ecb5c9ebbb5)

Answer: SELECT SUM(purch_amt) AS TOTAL FROM orders;

**Output:**

![image](https://github.com/user-attachments/assets/f7eff39a-6765-4e3f-9283-0c95e04ef9ca)

**Question 7**
---
Write a SQL query to count the number of customers. Return number of customers. Sample table: customer

![image](https://github.com/user-attachments/assets/667b0608-5a2c-4dda-8f5d-44f5baa45c91)

Answer:

SELECT COUNT(cust_name) AS COUNT FROM customer;

**Output:**

![image](https://github.com/user-attachments/assets/4feed809-1fe8-497c-942f-68ddc539715a)


**Question 8**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the minimum work hours for each date, and excludes dates where the minimum work hour is not less than 10.

Answer:

SELECT jdate,MIN(workhour) AS "MIN(workhour)" FROM employee1 GROUP BY jdate HAVING MIN(workhour)<10;

**Output:**

![image](https://github.com/user-attachments/assets/53f021e1-987c-4f3b-b62a-87f7c205b1be)


**Question 9**
---
Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the average age for each group, and excludes groups where the average age is not less than 24.

Answer:

SELECT (age -(age%5)) AS age_group, AVG(age) AS "AVG(age)" FROM customer1
GROUP BY age_group HAVING AVG(age)<=24;

**Output:**

![image](https://github.com/user-attachments/assets/94057c61-be86-43e1-9a05-a25d93bca1a7)


**Question 10**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the minimum work hours for each occupation, and excludes occupations where the minimum work hour is not greater than 8.

Answer:

SELECT occupation, MIN(workhour) AS "MIN(workhour)" FROM employee1 group by occupation having min(workhour)>8;
**Output:**
![image](https://github.com/user-attachments/assets/9cbb1f0d-5db9-4f8a-b24f-1bf8a88bbaae)



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
