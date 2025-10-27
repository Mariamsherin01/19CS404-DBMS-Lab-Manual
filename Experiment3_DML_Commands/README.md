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
Write a SQL statement to Increase quantity of all products by 10% to adjust for surplus stock counted

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```sql
UPDATE products
SET quantity = quantity * 1.10;
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f8669b56-7944-4d5e-920d-0d454ab76e56" />


**Question 2**
---
Write a SQL statement to Increase the selling price per unit by 5% for product ID 15 who's sale is on '2023-01-31'.

sales(sale_id,sale_date,product_id,quantity,sell_price,total_sell_price)

For example:

Test	Result
select changes();
changes()
----------
3

```sql
UPDATE sales
SET sell_price = sell_price * 1.05
WHERE product_id = 15 AND sale_date = '2023-01-31';
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/29a41279-53f9-464a-a123-e44b6cc3a15b" />


**Question 3**
---
Write a SQL statement to Increase the salary by 500 and email as 'updated' for employees with job ID 'SA_REP' and commission percentage greater than 0.15

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

```sql
UPDATE employees
SET salary = salary + 500,
    email = 'updated'
WHERE job_id = 'SA_REP'
  AND commission_pct > 0.15;
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a2b17c63-2f9f-4b35-bab2-b461128ecc34" />


**Question 4**
---
Write a SQL statement to Change the category to 'Household' where product name contains 'Detergent' in the products table.

Products Table 

name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lvl    INT        
quantity       INT        
supplier_id    INT      

```sql
UPDATE products
SET category = 'Household'
WHERE product_name LIKE '%Detergent%';
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e53fa8d8-6295-402d-8328-3f7d8bc941d1" />


**Question 5**
---
Write a SQL statement to update the product_name as 'Grapefruit' whose product_id is 4 in the products table.

products table

---------------
product_id
product_name
category_id
availability

```sql
UPDATE products
SET product_name = 'Grapefruit'
WHERE product_id = 4;
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c42e28f4-496d-4c04-8e41-90d3dcddb491" />


**Question 6**
---
Write a SQL query to Delete All Doctors whose ID ranges from 2 to 4.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
DELETE FROM doctors
WHERE doctor_id BETWEEN 2 AND 4;
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/375d05d5-8a21-4d10-b0fe-4eb96c87a8c0" />


**Question 7**
---
Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_city' should begin with the letter 'L',

Sample table: Customer

```sql
DELETE FROM customer
WHERE cust_city LIKE 'L%';
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c21d8b1d-07d8-409c-b43a-c9f0b22712e6" />


**Question 8**
---
Write a SQL query to Delete All Doctors with a NULL Last Name

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
DELETE FROM doctors
WHERE last_name IS NULL;
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/dd43004c-5e70-4918-ba02-fdfea4b3f261" />


**Question 9**
---
Write a SQL query to Delete customers whose 'GRADE' is greater than 2 and have a 'PAYMENT_AMT' less than the average 'PAYMENT_AMT' for all customers, or whose 'OUTSTANDING_AMT' is greater than 8000:

Sample table: Customer

```sql
DELETE FROM customer
WHERE (grade > 2 AND payment_amt < (SELECT AVG(payment_amt) FROM customer))
   OR outstanding_amt > 8000;
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/613c16bf-c757-4b20-9970-ee91fdcd80fe" />


**Question 10**
---
Write a SQL query to delete a doctor from Doctors table whos specialization is 'Cardiology'

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
DELETE FROM doctors
WHERE specialization = 'Cardiology';
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/18d0a361-3309-477d-ad18-dec04edf0269" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
