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
-- What is the total number of appointments scheduled by each doctor?

Sample table:Appointments Table



For example:

Result
DoctorID    TotalAppointments
----------  -----------------
1           1
2           3
5           3
9           2
10          1

```sql
--SELECT DoctorID, COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DoctorID;

```

**Output:**

<img width="605" height="503" alt="image" src="https://github.com/user-attachments/assets/d0382949-5617-4324-ac5c-039868157712" />

**Question 2**
---
-- How many medical records are there for each patient?

Sample table:MedicalRecords Table



For example:

Result
PatientID   TotalRecords
----------  ------------
4           4
5           1
6           1
7           1
8           1
10          2


```sql
-- SELECT PatientID, COUNT(*) As TotalRecords
FROM MedicalRecords 
GROUP BY PatientID;

```

**Output:**

<img width="589" height="529" alt="image" src="https://github.com/user-attachments/assets/0c6a8779-aada-4c8c-9999-69581147fdcd" />

**Question 3**
---
-- How many patients have expired insurance coverage for each insurance company?

Sample table:Insurance Table



For example:

Result
InsuranceCompany  TotalExpiredPatients
----------------  --------------------
ABC Insurance     1
DEF Insurance     1
GHI Insurance     1
JKL Insurance     1
MNO Insurance     1
PQR Insurance     1
STU Insurance     1
VWX Insurance     1
XYZ Insurance     1
YZA Insurance     1


```sql
-- SELECT "InsuranceCompany", COUNT(*) AS TotalExpiredPatients
FROM  Insurance 
WHERE SUBSTR("ValidityPeriod", 14, 10) < '2025-11-02' -- Extracts the YYYY-MM-DD end date part
GROUP BY "InsuranceCompany";

```

**Output:**

<img width="703" height="604" alt="image" src="https://github.com/user-attachments/assets/bf1f800e-a52f-49b2-b684-a3627ecb922b" />

**Question 4**
---
-- Write a SQL query to find the total amount of fruits with a unit type of 'LB'.

Note: Inventory attribute contains amount of fruits

Table: fruits

name        type
----------  ----------
id          INTEGER
name        TEXT
unit        TEXT
inventory   INTEGER
price       REAL
 

For example:

Result
total
----------
225

```sql
-- SELECT SUM(inventory) AS total
FROM fruits
WHERE unit = 'LB';

```

**Output:**

<img width="440" height="344" alt="image" src="https://github.com/user-attachments/assets/9ae3b49e-c7ac-4fa0-8bd8-de70c4d2874d" />

**Question 5**
---
-- Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

For example:

Result
TOTAL
----------
17541.18


```sql
--SELECT SUM(purch_amt) AS TOTAL
FROM orders;

```

**Output:**

<img width="316" height="250" alt="image" src="https://github.com/user-attachments/assets/eef81adc-d24b-4458-96ca-514cbb8c384b" />

**Question 6**
---
-- Write a SQL query to find What is the age difference between the youngest and oldest employee in the company.

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
For example:

Result
age_difference
--------------
13

```sql
-- SELECT MAX(age) - MIN(age) AS age_difference
FROM employee;

```

**Output:**
<img width="477" height="244" alt="image" src="https://github.com/user-attachments/assets/c25e63e6-f194-408b-8b0f-55e9b66632c5" />

**Question 7**
---
--Write a SQL query to find the number of employees whose age is greater than 32.

Sample table: employee

id

name

age

address

salary

1

Paul

32

California

20000

4

Mark

25

Richtown

65000

5

David

27

Texas

85000

 

For example:

Result
COUNT
----------
5


```sql
--SELECT COUNT(*) AS COUNT
FROM employee
WHERE age > 32;

```

**Output:**

<img width="361" height="251" alt="image" src="https://github.com/user-attachments/assets/85c13fa0-2373-4199-a203-2ccc547f09c8" />

**Question 8**
---
--Write the SQL query that accomplishes the grouping of data by age, calculates the maximum income for each age group, and includes only those age groups where the maximum income is greater than 2,000,000.

Sample table: employee



For example:

Result
age         MAX(income)
----------  -----------
35          5000000


```sql
-- SELECT age, MAX(income) AS "MAX(income)"
FROM employee
GROUP BY age
HAVING MAX(income) > 2000000;

```

**Output:**

<img width="574" height="295" alt="image" src="https://github.com/user-attachments/assets/25faac68-fd1d-4b76-9074-9b4aeca3a24a" />

**Question 9**
---
-- Write an SQL query that groups the customer data into 5-year age intervals, calculates the minimum salary for each group, and excludes groups where the minimum salary is not less than 2000.

Table: customer1



For example:

Result
age_group   MIN(salary)
----------  -----------
25          1500


```sql
-- SELECT
    (age / 5) * 5 AS age_group,
    MIN(salary) AS "MIN(salary)"
FROM
    customer1
GROUP BY
    age_group
HAVING
    MIN(salary) < 2000;

```

**Output:**

<img width="509" height="259" alt="image" src="https://github.com/user-attachments/assets/83ac6956-bddc-4ada-a137-502101eb3a06" />

**Question 10**
---
--Write the SQL query that accomplishes the selection of total number of products for each category from the "products" table, and includes only those products where the minimum category ID is less than 3.

Sample table: products



For example:

Result
category_id  count(product_name)
-----------  -------------------
1            4
2            3

```sql
-- SELECT category_id, COUNT(product_name) AS "count(product_name)"
FROM products
WHERE category_id < 3
GROUP BY category_id;

```

**Output:**

<img width="637" height="281" alt="image" src="https://github.com/user-attachments/assets/7f5d3808-0351-45e3-9852-0fcfb6a4b1f9" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
