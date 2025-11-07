# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 1 million

Employee Table

name             type

------------   ---------------

id                    INTEGER

name              TEXT

age                 INTEGER

city                 TEXT

income           INTEGER

```sql
SELECT id, name, age, city, income
FROM Employee
WHERE age < (
    SELECT AVG(age)
    FROM Employee
    WHERE income > 1000000
);

```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a9e6a61e-8481-42e0-868c-a466ebc49692" />


**Question 2**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose AGE is LESS than $30

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000

```sql
SELECT *
FROM CUSTOMERS
WHERE AGE < 30;

```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9cb0eecd-5d2a-44a9-b2c2-af135a261f45" />



**Question 3**
---
Write a query to display all the customers whose ID is the difference between the salesperson ID of Mc Lyon and 2001.

salesman table

name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)

customer table

name         type
-----------  ----------
customer_id  int
cust_name    text
city         text
grade        int
salesman_id  int

```sql
SELECT *
FROM customer
WHERE customer_id = (
    (SELECT salesman_id
     FROM salesman
     WHERE name = 'Mc Lyon') - 2001
);

```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a3df103c-31ff-4248-b487-be7b133dc01d" />


**Question 4**
---
Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the maximum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)



```sql
SELECT student_name, grade
FROM GRADES g
WHERE grade = (
    SELECT MAX(grade)
    FROM GRADES
    WHERE subject = g.subject
);

```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d7d0857d-c344-459b-a271-224cd1708d91" />


**Question 5**
---
From the following tables, write a SQL query to find those salespeople who earned the maximum commission. Return ord_no, purch_amt, ord_date, and salesman_id.

salesman table

name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)

orders table

name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int
 

```sql
SELECT ord_no, purch_amt, ord_date, salesman_id
FROM orders
WHERE salesman_id = (
    SELECT salesman_id
    FROM salesman
    WHERE commission = (SELECT MAX(commission) FROM salesman)
);

```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4213b093-aa57-41e9-9d5f-e2393d6feaa3" />


**Question 6**
---
Write a SQL query to Retrieve the medications with dosages equal to the lowest dosage

Table Name: Medications (attributes: medication_id, medication_name, dosage)



```sql
SELECT medication_id, medication_name, dosage
FROM Medications
WHERE dosage = (
    SELECT MIN(dosage)
    FROM Medications
);

```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6c9c16ad-2f8a-4375-aeb4-15d6a851272f" />


**Question 7**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000

```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY < 2500;

```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/101cbbcc-be32-4327-befc-44e94c3ba1a5" />


**Question 8**
---
Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 2.5 Lakh

Employee Table

name             type

------------   ---------------

id                    INTEGER

name              TEXT

age                 INTEGER

city                 TEXT

income           INTEGER

```sql
SELECT id, name, age, city, income
FROM Employee
WHERE age < (
    SELECT AVG(age)
    FROM Employee
    WHERE income > 250000
);

```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/55f594fc-e04b-420d-bd91-165908a4dc47" />


**Question 9**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is EQUAL TO $1500.

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000

```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY = 1500;

```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a1552879-1c87-4ca2-b171-740a1b3a41d7" />


**Question 10**
---
From the following tables, write a SQL query to find all orders generated by the salespeople who may work for customers whose id is 3007. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

Table Name: orders

name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int

```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM orders o
JOIN customer c ON o.salesman_id = c.salesman_id
WHERE c.customer_id = 3007;

```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2e9b4d48-5347-4cd5-93b8-51e7acf72625" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
