# Experiment 9: PL/SQL – Procedures and Functions

## AIM
To understand and implement procedures and functions in PL/SQL for performing various operations such as calculations, decision-making, and looping.

---

## THEORY

PL/SQL (Procedural Language/SQL) extends SQL by adding procedural constructs like variables, conditions, loops, procedures, and functions. Procedures and functions are subprograms that help modularize the code and improve reusability.

### **Procedure**
A PL/SQL **procedure** is a subprogram that performs a specific action. It does not return a value directly but can return values using `OUT` parameters.

**Syntax:**
```sql
CREATE OR REPLACE PROCEDURE procedure_name (parameters)
IS
BEGIN
   -- statements
END;
```

To call the procedure

```sql
EXEC procedure_name(arguments);
```

### **Function**
A PL/SQL **function** is a subprogram that returns a single value using the RETURN keyword.

```sql
CREATE OR REPLACE FUNCTION function_name (parameters)
RETURN datatype
IS
BEGIN
   -- statements
   RETURN value;
END;
```

To call the function:

```sql
SELECT function_name(arguments) FROM DUAL;
```

Key Differences:

-A procedure does not return a value, whereas a function must return a value.
-Functions can be called from SQL queries, procedures cannot (in most cases).

## 1. Write a PL/SQL Procedure to Find the Square of a Number

### Steps:
- Create a procedure named `find_square`.
- Declare a parameter to accept a number.
- Inside the procedure, compute the square of the input number.
- Use `DBMS_OUTPUT.PUT_LINE` to display the result.
- Call the procedure with a number as input.

**Expected Output:**  
Square of 6 is 36

-- Enable output display
SET SERVEROUTPUT ON;

-- Create the procedure
CREATE OR REPLACE PROCEDURE find_square(num IN NUMBER) AS
    result NUMBER;
BEGIN
    result := num * num;
    DBMS_OUTPUT.PUT_LINE('Square of ' || num || ' is ' || result);
END;


-- Execute the procedure
BEGIN
    find_square(6);
END;


# OUTPUT 
<img width="884" height="406" alt="image" src="https://github.com/user-attachments/assets/a0ca076d-66c7-4529-b018-4d8533819ffb" />

---

## 2. Write a PL/SQL Function to Return the Factorial of a Number

### Steps:
- Create a function named `get_factorial`.
- Declare a parameter to accept a number.
- Use a loop to calculate the factorial.
- Return the result using the `RETURN` statement.
- Call the function using a `SELECT` statement or in an anonymous block.

**Expected Output:**  
Factorial of 5 is 120


-- Enable output display
SET SERVEROUTPUT ON;

-- Create the function
CREATE OR REPLACE FUNCTION get_factorial(num IN NUMBER)
RETURN NUMBER AS
    fact NUMBER := 1;
BEGIN
    FOR i IN 1..num LOOP
        fact := fact * i;
    END LOOP;
    RETURN fact;
END;
-- Call the function inside an anonymous block
DECLARE
    n NUMBER := 5;
    result NUMBER;
BEGIN
    result := get_factorial(n);
    DBMS_OUTPUT.PUT_LINE('Factorial of ' || n || ' is ' || result);
END;

# OUTPUT 
<img width="865" height="401" alt="image" src="https://github.com/user-attachments/assets/d465d3c2-6364-45bc-a0fb-c46f30d553f5" />


---

## 3. Write a PL/SQL Procedure to Check Whether a Number is Even or Odd

### Steps:
- Create a procedure named `check_even_odd`.
- Accept an input parameter.
- Use the `MOD` function to check if the number is divisible by 2.
- Display whether it is Even or Odd using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
12 is Even


-- Enable output display
SET SERVEROUTPUT ON;

-- Create the procedure
CREATE OR REPLACE PROCEDURE check_even_odd(num IN NUMBER) AS
BEGIN
    IF MOD(num, 2) = 0 THEN
        DBMS_OUTPUT.PUT_LINE(num || ' is Even');
    ELSE
        DBMS_OUTPUT.PUT_LINE(num || ' is Odd');
    END IF;
END;


-- Execute the procedure
BEGIN
    check_even_odd(12);
END;


# OUTPUT 
<img width="727" height="381" alt="image" src="https://github.com/user-attachments/assets/f1b3c9d1-96a6-44e7-91fb-baae6727a7b3" />


---

## 4. Write a PL/SQL Function to Return the Reverse of a Number

### Steps:
- Create a function named `reverse_number`.
- Accept an input number as parameter.
- Use a loop to reverse the digits of the number.
- Return the reversed number.
- Call the function and display the output.

**Expected Output:**  
Reversed number of 1234 is 4321

-- Enable output display
SET SERVEROUTPUT ON;

-- Create the function
CREATE OR REPLACE FUNCTION reverse_number(num IN NUMBER)
RETURN NUMBER AS
    rev NUMBER := 0;
    rem NUMBER;
    n NUMBER := num;
BEGIN
    WHILE n > 0 LOOP
        rem := MOD(n, 10);
        rev := (rev * 10) + rem;
        n := FLOOR(n / 10);
    END LOOP;
    RETURN rev;
END;


-- Call the function inside an anonymous block
DECLARE
    n NUMBER := 1234;
    result NUMBER;
BEGIN
    result := reverse_number(n);
    DBMS_OUTPUT.PUT_LINE('Reversed number of ' || n || ' is ' || result);
END;

# OUTPUT 
<img width="878" height="402" alt="image" src="https://github.com/user-attachments/assets/8d5102c3-dded-45c0-9ad7-9af2198ea36c" />

---

## 5. Write a PL/SQL Procedure to Display the Multiplication Table of a Number

### Steps:
- Create a procedure named `print_table`.
- Accept an input number.
- Use a loop from 1 to 10 to multiply the input number.
- Display the multiplication results using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Multiplication table of 5:  
5 x 1 = 5  
5 x 2 = 10  
5 x 3 = 15  
...  
5 x 10 = 50


-- Enable output display
SET SERVEROUTPUT ON;

-- Create the procedure
CREATE OR REPLACE PROCEDURE print_table(num IN NUMBER) AS
BEGIN
    DBMS_OUTPUT.PUT_LINE('Multiplication table of ' || num || ':');
    FOR i IN 1..10 LOOP
        DBMS_OUTPUT.PUT_LINE(num || ' x ' || i || ' = ' || (num * i));
    END LOOP;
END;


-- Execute the procedure
BEGIN
    print_table(5);
END;

# OUTPUT 
<img width="878" height="402" alt="image" src="https://github.com/user-attachments/assets/07e6b79a-e678-4727-8872-25e3673a8021" />


## RESULT
Thus, the PL/SQL programs using procedures and functions were written, compiled, and executed successfully.
