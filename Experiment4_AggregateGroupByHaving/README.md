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
What is the most common diagnosis among patients?

Sample table:MedicalRecords Table



For example:

Result
Diagnosis              DiagnosisCount
---------------------  --------------
Childhood vaccination  3


```sql
SELECT 
    Diagnosis,
    COUNT(*) AS DiagnosisCount
FROM MedicalRecords
GROUP BY Diagnosis
ORDER BY DiagnosisCount DESC
LIMIT 1;
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/8a1aa8b1-0718-4a75-a64e-c060a82f4e81" />


**Question 2**
---
How many medical records were created in each month?

Sample table:MedicalRecords Table



For example:

Result
Month       TotalRecords
----------  ------------
2023-12     2
2024-01     6
2024-02     2


```sql
SELECT 
    strftime('%Y-%m', date) AS Month,
    COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY strftime('%Y-%m', date)
ORDER BY Month;
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/02ec5881-683b-4c2a-bfb0-bcd8f0983c10" />


**Question 3**
---
What is the total number of appointments scheduled by each doctor?

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
SELECT 
    DoctorID,
    COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DoctorID
ORDER BY DoctorID;
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/759e3918-284a-4490-bc62-f7502b4916a6" />


**Question 4**
---
-- Write a SQL query to find the average length of email addresses (in characters):

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER
For example:

Result
avg_email_length
----------------
15.0


```sql
SELECT 
    AVG(LENGTH(email)) AS avg_email_length
FROM customer;
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/009db4d9-3c7e-4190-a4d6-3b39025df0a9" />


**Question 5**
---
Write a SQL query to Calculate the average income of the employees with names starting with 'A': 

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
avg_income
----------
5000000.0


```sql
SELECT 
    AVG(income) AS avg_income
FROM employee
WHERE name LIKE 'A%';
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/bbf6ebcc-59bc-4b98-a126-95cc7eac32e9" />


**Question 6**
---
Write a SQL query to find the youngest employee in the company?

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
Employee_Name  Age
-------------  ----------
Peter          32


```sql
SELECT 
    name AS Employee_Name,
    age AS Age
FROM employee
ORDER BY age ASC
LIMIT 1;

```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/860cc4b0-1042-488b-b7f9-cde0122b5973" />


**Question 7**
---
Write a SQL query that counts the number of unique salespeople. Return number of salespeople.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

 

For example:

Result
COUNT
----------
6


```sql
SELECT 
    COUNT(DISTINCT salesman_id) AS COUNT
FROM orders;
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/30b25e89-ebee-4b19-bbd7-29952afaa063" />


**Question 8**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the average work hours for each occupation, and includes only those occupations where the average work hour falls between 10 and 12.

Sample table: employee1



For example:

Result
occupation  AVG(workhour)
----------  -------------
Business    10.0
Engineer    12.0


```sql
SELECT 
    occupation,
    AVG(workhour) AS [AVG(workhour)]
FROM employee1
GROUP BY occupation
HAVING AVG(workhour) BETWEEN 10 AND 12;
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/833803a1-8610-4833-a995-ed5e49734d9a" />


**Question 9**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the minimum work hours for each occupation, and excludes occupations where the minimum work hour is not greater than 8.

Sample table: employee1



For example:

Result
occupation  MIN(workhour)
----------  -------------
Business    10
Doctor      15
Engineer    12
Teacher     9


```sql
SELECT 
    occupation,
    MIN(workhour) AS [MIN(workhour)]
FROM employee1
GROUP BY occupation
HAVING MIN(workhour) > 8;
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/cf1561c9-5c11-42ac-8548-f182acd7b59e" />


**Question 10**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the maximum work hours for each date, and excludes dates where the maximum work hour is not greater than 12.

Sample table: employee1



For example:

Result
jdate       MAX(workhour)
----------  -------------
2004.0      15
2006.0      15


```sql
SELECT 
    jdate,
    MAX(workhour) AS [MAX(workhour)]
FROM employee1
GROUP BY jdate
HAVING MAX(workhour) > 12;

```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/13b804bc-776a-46d5-9ab2-fea9ba997124" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
