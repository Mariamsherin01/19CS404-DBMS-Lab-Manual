<img width="433" height="407" alt="image" src="https://github.com/user-attachments/assets/6fbcd015-8f03-460c-b55e-ea67eaaa16f6" /># Experiment 6: Joins

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
-- From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
70004       110.5       2012-08-17  3009         5003
70007       948.5       2012-09-10  3005         5002
70005       2400.6      2012-07-27  3007         5001
70008       5760        2012-09-10  3002         5001
70010       1983.43     2012-10-10  3004         5006
70003       2480.4      2012-10-10  3009         5003
70012       250.45      2012-06-27  3008         5002
70011       75.29       2012-08-17  3003         5007
70013       3045.6      2012-04-25  3002         5001
For example:

Result
ord_no           purch_amt        cust_name        city
---------------  ---------------  ---------------  ---------------
70007            948.5            Graham Zusi      California
70010            1983.43          Fabian Johns     Paris


```sql
-- SELECT
  T1.ord_no,
  T1.purch_amt,
  T2.cust_name,
  T2.city
FROM orders AS T1
JOIN customer AS T2
  ON T1.customer_id = T2.customer_id
WHERE
  T1.purch_amt > 500 AND T1.purch_amt < 2000;
```

**Output:**

<img width="1110" height="439" alt="image" src="https://github.com/user-attachments/assets/b68e3bbd-1e5f-439f-843a-252f29ba5c52" />

**Question 2**
---
-- From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
70004       110.5       2012-08-17  3009         5003
70007       948.5       2012-09-10  3005         5002
70005       2400.6      2012-07-27  3007         5001
70008       5760        2012-09-10  3002         5001
70010       1983.43     2012-10-10  3004         5006
70003       2480.4      2012-10-10  3009         5003
70012       250.45      2012-06-27  3008         5002
70011       75.29       2012-08-17  3003         5007
70013       3045.6      2012-04-25  3002         5001
For example:

Result
ord_no           purch_amt        cust_name        city
---------------  ---------------  ---------------  ---------------
70007            948.5            Graham Zusi      California
70010            1983.43          Fabian Johns     Paris

```sql
--SELECT
  T1.ord_no,
  T1.purch_amt,
  T2.cust_name,
  T2.city
FROM orders AS T1
JOIN customer AS T2
  ON T1.customer_id = T2.customer_id
WHERE
  T1.purch_amt > 500 AND T1.purch_amt < 2000;
```

**Output:**

<img width="1153" height="453" alt="image" src="https://github.com/user-attachments/assets/baf70517-c02d-4a19-9042-61ee5ff1ad89" />

**Question 3**
---
-- From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id.  

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
For example:

Result
cust_name        city             grade            Salesman         city
---------------  ---------------  ---------------  ---------------  ----------
Brad Guzan       London           100              Pit Alex         London
Nick Rimando     Chennai          100              Bob Emily        New York
Jozy Altidore    Moscow           200              Paul Adam        Rome
Fabian Johns     Paris            300              Mc Lyon          Paris
Graham Zusi      California       200              Nail Knite       Paris
Brad Davis       New York         200              Bob Emily        New York
Julian Green     London           300              Nail Knite       Paris
Geoff Cameron    Berlin           100              Lauson Hen       San Jose


```sql
-- -- Selecting specific columns from the 'customer' and 'salesman' tables
SELECT a.cust_name, a.city, a.grade, 
       b.name AS "Salesman", b.city 
-- Specifying the tables to retrieve data from ('customer' as 'a' and 'salesman' as 'b')
FROM customer a 
-- Performing a left join based on the salesman_id, including unmatched rows from 'customer'
LEFT JOIN salesman b 
ON a.salesman_id = b.salesman_id 
-- Sorting the result set by customer_id in ascending order
ORDER BY a.customer_id;

```

**Output:**

<img width="1340" height="793" alt="image" src="https://github.com/user-attachments/assets/ba75ce20-0d07-4fab-97c7-2a8e66fe3548" />

**Question 4**
---
-- Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name"), with an inner join on the "patient_id" column and a condition filtering for test results with the test name 'Blood Pressure'.

PATIENTS TABLE:

ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id



TEST_RESULT TABLES:

ATTRIBUTES - result_id, patient_id, test_name, result, test_date



For example:

Result
patient_name
---------------
Alice


```sql
--SELECT
  T1.first_name AS patient_name
FROM patients AS T1
JOIN test_results AS T2
  ON T1.patient_id = T2.patient_id
WHERE
  T2.test_name = 'Blood Pressure';
```

**Output:**

<img width="539" height="401" alt="image" src="https://github.com/user-attachments/assets/74fc9658-99b8-478a-bf61-7def1b4b5d99" />

**Question 5**
---
-- Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name"), with an inner join on the "patient_id" column and a condition filtering for test results with the test name 'Blood Pressure'.

PATIENTS TABLE:

ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id



TEST_RESULT TABLES:

ATTRIBUTES - result_id, patient_id, test_name, result, test_date



For example:

Result
patient_name
---------------
Alice


```sql
-- SELECT
  T1.first_name AS patient_name
FROM patients AS T1
JOIN test_results AS T2
  ON T1.patient_id = T2.patient_id
WHERE
  T2.test_name = 'Blood Pressure';
```

**Output:**

<img width="380" height="385" alt="image" src="https://github.com/user-attachments/assets/f1c55fea-89d0-4bb8-89b9-3de70ca220fa" />

**Question 6**
---Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "appointments" table (aliased as "a"), with an inner join on the "patient_id" column.

PATIENTS TABLE:

ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id



APPOINTMENTS TABLE:

ATTRIBUTES - appointment_id, patient_id, doctor_id, appointment_date



For example:

Result
patient_name     appointment_id   patient_id       doctor_id        appointment_date
---------------  ---------------  ---------------  ---------------  -------------------
Alice            1                1                1                2024-01-05 10:00:00
Bob              2                2                2                2024-02-20 14:30:00
Charlie          3                3                3                2024-03-15 09:15:00

--  

```sql
-- SELECT
  P.first_name AS patient_name,
  A.*
FROM patients AS P
JOIN appointments AS A
  ON P.patient_id = A.patient_id;
```

**Output:**

<img width="441" height="507" alt="image" src="https://github.com/user-attachments/assets/cd211b37-e3e5-47eb-accf-89fe6438408d" />

**Question 7**
---
-- Write a SQL statement to join the tables salesman, customer and orders so that the same column of each table appears once and only the relational rows are returned. 

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
70004       110.5       2012-08-17  3009         5003
70007       948.5       2012-09-10  3005         5002
70005       2400.6      2012-07-27  3007         5001
70008       5760        2012-09-10  3002         5001
70010       1983.43     2012-10-10  3004         5006
70003       2480.4      2012-10-10  3009         5003
70012       250.45      2012-06-27  3008         5002
70011       75.29       2012-08-17  3003         5007
70013       3045.6      2012-04-25  3002         5001
Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table : salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
For example:

Result
ord_no           purch_amt        ord_date         cust_name        customer_city  grade       salesman_name  salesman_city  commission
---------------  ---------------  ---------------  ---------------  -------------  ----------  -------------  -------------  ----------
70001            150.5            2012-10-05       Graham Zusi      California     200         Nail Knite     Paris          0.13
70009            270.65           2012-09-10       Brad Guzan       London         100         Pit Alex       London         0.11
70002            65.26            2012-10-05       Nick Rimando     Chennai        100         Bob Emily      New York       0.15
70004            110.5            2012-08-17       Geoff Cameron    Berlin         100         Lauson Hen     San Jose       0.12
70007            948.5            2012-09-10       Graham Zusi      California     200         Nail Knite     Paris          0.13
70005            2400.6           2012-07-27       Brad Davis       New York       200         Bob Emily      New York       0.15
70008            5760.0           2012-09-10       Nick Rimando     Chennai        100         Bob Emily      New York       0.15
70010            1983.43          2012-10-10       Fabian Johns     Paris          300         Mc Lyon        Paris          0.14
70003            2480.4           2012-10-10       Geoff Cameron    Berlin         100         Lauson Hen     San Jose       0.12
70012            250.45           2012-06-27       Julian Green     London         300         Nail Knite     Paris          0.13
70011            75.29            2012-08-17       Jozy Altidore    Moscow         200         Paul Adam      Rome           0.13
70013            3045.6           2012-04-25       Nick Rimando     Chennai        100         Bob Emily      New York       0.15

```sql
-- SELECT
  T1.ord_no,
  T1.purch_amt,
  T1.ord_date,
  T2.cust_name,
  T2.city AS customer_city,
  T2.grade,
  T3.name AS salesman_name,
  T3.city AS salesman_city,
  T3.commission
FROM orders AS T1
JOIN customer AS T2
  ON T1.customer_id = T2.customer_id
JOIN salesman AS T3
  ON T1.salesman_id = T3.salesman_id;
```

**Output:**

<img width="1313" height="639" alt="image" src="https://github.com/user-attachments/assets/f92791bd-840b-4521-8c4a-191b279a458a" />

**Question 8**
---
-- From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.  

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
For example:

Result
Customer Name    city             Salesman         city             commission
---------------  ---------------  ---------------  ---------------  ----------
Nick Rimando     Chennai          Bob Emily        New York         0.15
Graham Zusi      California       Nail Knite       Paris            0.13
Julian Green     London           Nail Knite       Paris            0.13
Jozy Altidore    Moscow           Paul Adam        Rome             0.13


```sql
-- SELECT
  T1.cust_name AS "Customer Name",
  T1.city AS city,
  T2.name AS Salesman,
  T2.city AS city,
  T2.commission
FROM customer AS T1
JOIN salesman AS T2
  ON T1.salesman_id = T2.salesman_id
WHERE
  T1.city <> T2.city
  AND T2.commission > 0.12;
```

**Output:**

<img width="1101" height="523" alt="image" src="https://github.com/user-attachments/assets/d2e152d1-d6be-408d-8ba0-5540c9b74597" />

**Question 9**
---
-- Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column.

Customer Table: (customer_id, cust_name, city, grade, salesman_id)

Salesman Table: (salesman_id, name, city, commission)

For example:

Result
name             cust_name        city             grade            salesman_id
---------------  ---------------  ---------------  ---------------  -----------
Bob Emily        Brad Davis       New York         200              5001
Bob Emily        Nick Rimando     Chennai          100              5001
Nail Knite       Graham Zusi      California       200              5002
Nail Knite       Julian Green     London           300              5002
Pit Alex         Brad Guzan       London           100              5005
Mc Lyon          Fabian Johns     Paris            300              5006
Paul Adam        Jozy Altidore    Moscow           200              5007
Lauson Hen       Geoff Cameron    Berlin           100              5003


```sql
-- SELECT
  S.name,
  C.cust_name,
  C.city,
  C.grade,
  C.salesman_id
FROM salesman AS S
LEFT JOIN customer AS C
  ON S.salesman_id = C.salesman_id;
```

**Output:**

<img width="1303" height="678" alt="image" src="https://github.com/user-attachments/assets/7f344c16-8cd8-4fce-a29e-ee215fd544ee" />

**Question 10**
---
-- Write an SQL query that retrieves all columns from the 'customer' table (using the alias 'c'), performs a LEFT JOIN with the 'orders' table on the 'customer_id' column, and includes only those orders with an order date after '2012-08-17'.

'customer' Table: (customer_id, cust_name, city, grade, salesman_id)

'orders' Table: (ord_no, purch_amt, ord_date, customer_id, salesman_id)

For example:

Result
customer_id      cust_name        city             grade            salesman_id
---------------  ---------------  ---------------  ---------------  -----------
3005             Graham Zusi      California       200              5002
3001             Brad Guzan       London           100              5005
3002             Nick Rimando     Chennai          100              5001
3005             Graham Zusi      California       200              5002
3002             Nick Rimando     Chennai          100              5001
3004             Fabian Johns     Paris            300              5006
3009             Geoff Cameron    Berlin           100              5003


```sql
-- SELECT
  T1.*
FROM customer AS T1
JOIN orders AS T2
  ON T1.customer_id = T2.customer_id
WHERE
  T2.ord_date > '2012-08-17';
```

**Output:**

![Uploading image.png…]()


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
