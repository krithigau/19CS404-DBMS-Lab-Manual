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
**Question 1**
--
Write a query to fetch 3 top salaried records from the EmployeePosition table. EmpID EmpPosition DateOfJoining Salary 1 Manager 01/05/2024 500000 2 Executive 02/05/2024 75000

Answer: SELECT EmpID,EmpPosition,DateOfJoining,Salary FROM EmployeePosition ORDER BY Salary DESC LIMIT 3;

**Output:**

![image](https://github.com/user-attachments/assets/bc430df4-3b18-430d-8346-0bb0160aa205)

**Question 2**
--
Write a SQL query to Select all patients who were admitted for one day.

![{E959F211-F866-45C8-A124-737E23267EE1}](https://github.com/user-attachments/assets/13aca38f-57e5-441b-88c9-adcd6248a5fd)

Answer: SELECT patient_id,first_name,admission_date,discharge_date FROM Patients WHERE admission_date==discharge_date;
**Output:**

![image](https://github.com/user-attachments/assets/2b0bd96f-ab7a-4076-bdeb-b84e9dadd037)


**Question 3**
--
Write a SQL query to classify value2 in the Calculations table as 'Small', 'Medium', or 'Large' based on whether it is less than 10, between 10 and 50, or greater than 50, respectively.

![image](https://github.com/user-attachments/assets/9f238c3e-81f6-43a9-a770-925e0faa28d1)

Answer:

SELECT id,value2,
CASE WHEN value2<10 THEN 'Small' WHEN value2 BETWEEN 10 AND 50 THEN 'Medium' ELSE 'Large' END AS size_category FROM Calculations;
**Output:**

![image](https://github.com/user-attachments/assets/ee9be76a-4b02-4a33-b058-4634401c7564)

**Question 4**
--
Write a SQL query to find all those customers who does not have any grade. Return customer_id, cust_name, city, grade, salesman_id. Sample table: customer

![image](https://github.com/user-attachments/assets/31779556-1b76-4000-88b0-f3e379a293a8)

Answer:

SELECT customer_id, cust_name, city, grade, salesman_id FROM customer WHERE grade IS NULL;
**Output:**

![image](https://github.com/user-attachments/assets/ad12b89b-4f2d-4ccc-817c-8cff665355db)


**Question 5**
--
Write a SQL query to find customers who are either from the city 'New York' or who do not have a grade greater than 100. Return customer_id, cust_name, city, grade, and salesman_id. Sample table: customer

![image](https://github.com/user-attachments/assets/e508821b-9b94-492e-a963-d51a41f51dbb)

Answer:

SELECT customer_id, cust_name, city, grade, salesman_id FROM customer WHERE city = 'New York' OR grade <=100;
**Output:**

![image](https://github.com/user-attachments/assets/63f39970-a055-4e1b-92b4-179292ad27a0)

**Question 6**
--
Write a SQL query to identify products where the discount amount is greater than $50. Return product_id, original_price, discount_percentage, and discount_amount. Sample table: products

![image](https://github.com/user-attachments/assets/909feee8-8742-4a0d-880c-1b5347fa3a09)

Answer:

SELECT product_id, original_price,discount_percentage,original_price * discount_percentage AS discount_amount FROM products WHERE original_price * discount_percentage > 50;

**Output:**

![image](https://github.com/user-attachments/assets/53f2307f-d953-46d6-bbcb-525e21f41235)


**Question 7**
--
Write a SQL query to calculate the original price using the discount percentage and the given discounted price. Return product_id, discounted_price, discount_percentage, and original_price. Sample table: Products

![image](https://github.com/user-attachments/assets/ffeef16c-88aa-4217-83f5-35b2300b4b16)

Answer:

SELECT product_id,discounted_price,discount_percentage, discounted_price/(1 discount_percentage) AS original_price FROM Products;
**Output:**

![image](https://github.com/user-attachments/assets/ba26a970-a9b8-48d6-bc2b-fae11bdf21f0)


**Question 8**
---
Write a SQL query to find all employees along with the day of the week on which they were hired from the emp table emp table

![image](https://github.com/user-attachments/assets/c9d294cd-2bbe-43ed-a446-4ac81784e3c2)
Answer:

SELECT ename,hiredate, CASE strftime('%w',hiredate) WHEN '0' THEN 'Sunday' WHEN '1' THEN 'Monday' WHEN '2' THEN 'Tuesday' WHEN '3' THEN 'Wednesday' WHEN '4' THEN 'Thursday' WHEN '5' THEN 'Friday' WHEN '6' THEN 'Saturday' END AS day_of_week FROM emp;
**Output:**

![image](https://github.com/user-attachments/assets/1fcdfcaf-21e8-4132-8dc6-b2b5b30caae8)


**Question 9**
--
Write a SQL query to find all employees who were hired on a weekend (Saturday or Sunday) from the emp table emp table

![image](https://github.com/user-attachments/assets/7823401e-4d48-49ca-ba8f-5fea821f24ef)

Answer:

SELECT ename,hiredate, CASE strftime('%w',hiredate) WHEN '0' THEN '0' WHEN '6' THEN '6' END AS day_of_week FROM emp WHERE strftime('%w',hiredate) IN ('0','6');
**Output:**
![image](https://github.com/user-attachments/assets/0f647ea1-25e0-48ee-9866-993096e13fea)


**Question 10**
---
Write a SQL query to Concatenate the first three characters of the employee's name with the last three characters of their job title. Table name: emp

![image](https://github.com/user-attachments/assets/1ff1fcb2-28f6-4e3e-a0bf-0bf50278a876)


Answer:

SELECT ename,job,substr(ename,1,3) || substr(job,-3) AS ConcatenatedString FROM emp;
**Output:**

![image](https://github.com/user-attachments/assets/3c62d515-a077-4a0f-8d1d-e02bb7976033)


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
