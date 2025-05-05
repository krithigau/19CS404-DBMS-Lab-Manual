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
--
Write the SQL query that achieves the selection of all columns from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers with the name 'Fabian Johns'.

Answer: SELECT s.* FROM salesman s LEFT JOIN customer c ON s.salesman_id = c.salesman_id WHERE c.cust_name = 'Fabian Johns';

**Output:**

![image](https://github.com/user-attachments/assets/1be6c1b7-3e30-4ccb-a4aa-370a24aa7ea6)


**Question 2**
---
From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.
Sample table: customer

![image](https://github.com/user-attachments/assets/133960ff-d7a4-451e-bcc7-edcd1ae25e76)

Sample table: salesman

![image](https://github.com/user-attachments/assets/64afba75-9a0b-4cf9-ac87-a64002bd57b9)


Answer:

SELECT
c.cust_name AS "Customer Name", c.city AS "city", s.name AS "Salesman", s.city AS "city", s.commission FROM
customer c JOIN
salesman s ON c.salesman_id = s.salesman_id WHERE
c.city <> s.city AND s.commission > 0.12;

**Output:**

![image](https://github.com/user-attachments/assets/8bbbfd41-43b3-4795-943a-23aaa701c460)


**Question 3**
---
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column.

Answer: SELECT
c.cust_name,
o.ord_no,
o.ord_date,
o.purch_amt FROM
customer c LEFT JOIN
orders o
ON c.customer_id = o.customer_id;

**Output:**

![image](https://github.com/user-attachments/assets/f0f80d80-353d-4665-9dd9-7b641c87c2e8)


**Question 4**
---
Write the SQL query that accomplishes the selection of all columns from the "patients" table and the first name of doctors from the "doctors" table, with an inner join on the "doctor_id" column. PATIENTS TABLE:

![image](https://github.com/user-attachments/assets/cd052e58-efc2-4ce1-a0d3-fe8d3e817bb9)


DOCTORS TABLE:

![image](https://github.com/user-attachments/assets/8d13f922-25ee-48ea-9732-bbcb90685442)


Answer: SELECT
p.patient_id,
p.first_name AS first_name,
p.last_name AS last_name,
p.date_of_birth,
p.admission_date,
p.discharge_date,
p.doctor_id,
d.first_name AS doctor_name FROM
patients p INNER JOIN
doctors d
ON p.doctor_id = d.doctor_id;

**Output:**

![image](https://github.com/user-attachments/assets/b6fcdd9e-af4f-4523-8196-2fe633112d0e)


**Question 5**
---
From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id.
Sample table: customer

![image](https://github.com/user-attachments/assets/1ae02f7d-4e84-42d4-b1e9-ebbc01b7f91c)


Sample table: salesman

![image](https://github.com/user-attachments/assets/dbf0a286-5db8-41e3-b5f1-bd401e8f85e2)


Answer:

SELECT
c.cust_name,
c.city AS city,
c.grade,
s.name AS Salesman,
s.city AS city FROM
customer c JOIN
salesman s
ON c.salesman_id = s.salesman_id ORDER BY
c.customer_id ASC;

**Output:**

![image](https://github.com/user-attachments/assets/a765121f-dfda-446f-b486-ec3a6c0936e8)


**Question 6**
---
Write the SQL query that achieves the selection of all columns from the "patients" table and the specialization from the "doctors" table (aliased as "doctor_specialization"), with an inner join on the "doctor_id" column. PATIENTS TABLE:

![image](https://github.com/user-attachments/assets/20b09711-bab0-4047-8ae4-d1bc1958c70d)


DOCTORS TABLE:

![image](https://github.com/user-attachments/assets/7af94531-9546-423b-b8dd-d17f4b92cb0f)


Answer:

SELECT
p.*,
d.specialization AS doctor_specialization FROM
patients p INNER JOIN
doctors d
ON p.doctor_id = d.doctor_id;

**Output:**

![image](https://github.com/user-attachments/assets/404d1460-b525-4f91-8557-a3fe9e4bf5eb)


**Question 7**
---
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id.
Sample table: customer

![image](https://github.com/user-attachments/assets/d69a7a37-d920-4dcc-8894-f0f5ef803e4e)


Sample table: salesman

![image](https://github.com/user-attachments/assets/b436e536-f428-4c7f-a944-70aa1919efc2)


Answer:

SELECT
c.cust_name,
c.city AS city,
c.grade,
s.name AS Salesman,
s.city AS city FROM
customer c INNER JOIN
salesman s
ON c.salesman_id = s.salesman_id WHERE
c.grade < 300 ORDER BY
c.customer_id ASC;

**Output:**

![image](https://github.com/user-attachments/assets/71a5a470-6cd1-4833-8cf2-94843b70c7b0)


**Question 8**
---
write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city. Sample table: salesman

![image](https://github.com/user-attachments/assets/453fcb20-2b85-4c82-a352-ecd249217a94)


Sample table: customer

![image](https://github.com/user-attachments/assets/f7dbcae7-acfd-4009-81fb-bd1e6ef7063a)


Answer:

SELECT
s.name AS Salesman,
c.cust_name,
s.city FROM
salesman s INNER JOIN
customer c ON s.city = c.city;

**Output:**

![image](https://github.com/user-attachments/assets/d33d6ebe-0883-41fe-8dfa-e4d8c5bed7c9)


**Question 9**
---
Write the SQL query that accomplishes the selection of the first name from the "patients" table and all columns from the "surgeries" table, with an inner join on the "patient_id" column and a condition filtering for patients with the first name 'Alice'.

PATIENTS TABLE:

![image](https://github.com/user-attachments/assets/738ef9de-0702-470b-b886-688239aec48d)


SURGERIES TABLE:

![image](https://github.com/user-attachments/assets/acd4d1dc-82a9-4061-b595-2140ae123839)


Answer:

SELECT
p.first_name,
s.surgery_id,
s.patient_id,
s.surgeon_id,
s.surgery_date FROM
patients p INNER JOIN
surgeries s ON p.patient_id = s.patient_id WHERE
p.first_name = 'Alice';

**Output:**

![image](https://github.com/user-attachments/assets/7505dfca-8df3-4b2d-9449-f374f2d4af00)


**Question 10**
---
Write a SQL statement to join the tables salesman, customer and orders so that the same column of each table appears once and only the relational rows are returned.
Sample table: orders image

![image](https://github.com/user-attachments/assets/feac9692-7ba5-49f6-b235-f4b7dccfb725)


Sample table: customer image

![image](https://github.com/user-attachments/assets/cb226937-af59-4496-97c6-776681fbb4fe)

Sample table : salesman image

![image](https://github.com/user-attachments/assets/27817b3a-ea03-4398-b077-9c38223ebd3b)

Answer:

SELECT
o.ord_no, o.purch_amt, o.ord_date, c.cust_name, c.city AS customer_city, c.grade, s.name AS salesman_name, s.city AS salesman_city, s.commission FROM
orders o INNER JOIN
customer c ON o.customer_id = c.customer_id INNER JOIN
salesman s ON o.salesman_id = s.salesman_id;

**Output:**

![image](https://github.com/user-attachments/assets/72c91885-8523-4857-83f7-e3e144aa3bc6)


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
