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

<img width="1045" height="635" alt="image" src="https://github.com/user-attachments/assets/c7deb834-2c0a-4398-a6f7-4996463ca31c" />

**Syntax**

```sql
SELECT *
FROM CUSTOMERS
WHERE AGE < 30 and ADDRESS = 'Delhi'
ORDER BY ID;
```

**Output:**

<img width="1225" height="340" alt="image" src="https://github.com/user-attachments/assets/a12a6db6-04ac-40ce-a254-abd3ff845b8e" />

**Question 2**

<img width="1243" height="832" alt="image" src="https://github.com/user-attachments/assets/bef402a4-3621-4a57-a810-3d98665f519f" />

**Syntax**

```sql
SELECT ord_no, purch_amt, ord_date, o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.commission = (
    SELECT MAX(commission)
    FROM salesman
);
```

**Output:**

<img width="1007" height="457" alt="image" src="https://github.com/user-attachments/assets/01cf3f86-11b7-4eaf-9025-ffcdcbb948c5" />

**Question 3**

<img width="1181" height="751" alt="image" src="https://github.com/user-attachments/assets/8e4f0c4d-48c0-463e-ac4f-31279aa4bb22" />

**Syntax**

```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM orders o
JOIN salesman s
    ON o.salesman_id = s.salesman_id
WHERE city = 'London';
```

**Output:**

<img width="1223" height="394" alt="image" src="https://github.com/user-attachments/assets/405b4e47-5929-453b-bd3c-2ac7518d25ed" />

**Question 4**

<img width="1201" height="840" alt="image" src="https://github.com/user-attachments/assets/b8395b28-89d1-49e0-ba1f-c5254f41f449" />

**Syntax**

```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM orders o
JOIN salesman s
    ON o.salesman_id = s.salesman_id
WHERE city = 'New York'
```

**Output:**

<img width="1230" height="439" alt="image" src="https://github.com/user-attachments/assets/54f27a55-0549-4af4-88c5-8c46aa9555a2" />

**Question 5**

<img width="1129" height="456" alt="image" src="https://github.com/user-attachments/assets/c89eee88-3d7e-4905-848e-f163479c81f6" />

**Syntax**

```sql
SELECT department_id , department_name
FROM Departments
WHERE LENGTH(department_name) > (
    SELECT AVG(LENGTH(department_name))
    FROM Departments
);
```

**Output:**

<img width="547" height="377" alt="image" src="https://github.com/user-attachments/assets/07725f72-aee1-487e-9b0c-1f8a36865c7c" />

**Question 6**

<img width="1184" height="801" alt="image" src="https://github.com/user-attachments/assets/fc48abc2-6bc8-455d-ae82-279e5e882c94" />

**Syntax**

```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM orders o
JOIN salesman s 
    ON o.salesman_id = s.salesman_id
WHERE city = 'New York';
```

**Output:**

<img width="1226" height="464" alt="image" src="https://github.com/user-attachments/assets/f9ef37b5-db3b-4209-934c-910249409b14" />

**Question 7**

<img width="987" height="673" alt="image" src="https://github.com/user-attachments/assets/257ab5b8-b74c-486e-b1b3-edd3a080e8d0" />

**Syntax**

```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY > 4500;
```

**Output:**

<img width="1189" height="414" alt="image" src="https://github.com/user-attachments/assets/546cefc7-8fad-4678-891e-c75fb46c02f3" />

**Question 8**

<img width="922" height="618" alt="image" src="https://github.com/user-attachments/assets/5f6df1be-24b1-493b-b9b5-c95b01ececbb" />

**Syntax**

```sql
SELECT *
FROM CUSTOMERS
WHERE ADDRESS = 'Delhi';
```

**Output:**

<img width="1211" height="309" alt="image" src="https://github.com/user-attachments/assets/809f9934-0f95-4932-b6bd-b95a837b531f" />

**Question 9**

<img width="983" height="491" alt="image" src="https://github.com/user-attachments/assets/b78378ee-a148-47b3-9c97-6c0eee81540b" />

**Syntax**

```sql
SELECT medication_id, medication_name, dosage
FROM Medications
WHERE dosage = (
    SELECT MAX(dosage)
    FROM Medications
);
```

**Output:**

<img width="871" height="373" alt="image" src="https://github.com/user-attachments/assets/81032604-ced6-4412-8c32-5b5f124ef142" />

**Question 10**

<img width="1242" height="566" alt="image" src="https://github.com/user-attachments/assets/e8a29045-a121-498d-b922-e543a4ade4fb" />

**Syntax**

```sql
SELECT *
FROM orders
WHERE salesman_id = (
    SELECT salesman_id
    FROM orders
    WHERE customer_id = 3007
);
```

**Output:**

<img width="1231" height="421" alt="image" src="https://github.com/user-attachments/assets/72dc44c7-d49c-4597-a418-f5883b798908" />

## Module 4 SEB Completion Grades

<img width="1037" height="68" alt="image" src="https://github.com/user-attachments/assets/2e2fdc43-1858-48d1-959a-a83504652d5b" />

<img width="1483" height="936" alt="image" src="https://github.com/user-attachments/assets/35c53624-3ed6-4fe0-a8df-63cb6a44978f" />

## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
