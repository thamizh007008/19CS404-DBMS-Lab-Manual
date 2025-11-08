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

<img width="1263" height="455" alt="image" src="https://github.com/user-attachments/assets/378d07b9-1556-4c18-acdd-d4fabc3b3f28" />

**Syntax:**

```sql
SELECT 
    s.name,
    c.cust_name,
    c.city,
    c.grade,
    c.salesman_id
FROM salesman s
LEFT JOIN customer c
    ON s.salesman_id = c.salesman_id
WHERE c.salesman_id IN (
    SELECT salesman_id
    FROM customer
    GROUP BY salesman_id
    HAVING COUNT(customer_id) > 1
)
ORDER BY c.grade;
```

**Output:**

<img width="1276" height="485" alt="image" src="https://github.com/user-attachments/assets/363a703c-d70a-453d-8a17-637cf6b24bb4" />

**Question 2**

<img width="1054" height="899" alt="image" src="https://github.com/user-attachments/assets/b4f23efd-03b9-4bee-bd66-fc26b0d62f5c" />

**Syntax:**

```sql
SELECT s.name AS Salesman, c.cust_name, c.city
FROM salesman s, customer c
WHERE s.city = c.city;
```

**Output:**

<img width="1129" height="673" alt="image" src="https://github.com/user-attachments/assets/b37c88f8-a858-488d-9bee-00275d9784d9" />

**Question 3**

<img width="1261" height="698" alt="image" src="https://github.com/user-attachments/assets/c424659d-7513-40c1-a102-4d27e44faa8d" />

**Syntax:**

```sql
SELECT p.first_name AS patient_name
FROM patients p
INNER JOIN doctors d
    ON p.doctor_id = d.doctor_id
WHERE d.first_name = 'Emily' and d.last_name = 'Johnson' and p.discharge_date IS NOT NULL;
```

**Output:**

<img width="420" height="380" alt="image" src="https://github.com/user-attachments/assets/bbbd27e2-1660-45e5-812c-a40f89ae19bc" />

**Question 4**

<img width="1226" height="374" alt="image" src="https://github.com/user-attachments/assets/27c121d9-8a25-4127-9483-6e41d4d5ea15" />

**Syntax:**

```sql
SELECT DISTINCT s.name 
FROM Salesman s
LEFT JOIN Customer c
    ON s.salesman_id = c.salesman_id 
WHERE c.city = 'London';
```

**Output:**

<img width="433" height="455" alt="image" src="https://github.com/user-attachments/assets/6439b968-e6c6-44e5-a004-d665d1a5d3b1" />

**Question 5**

<img width="1240" height="832" alt="image" src="https://github.com/user-attachments/assets/5791fead-a493-4881-9898-0d14389a6894" />

**Syntax:**

```sql
SELECT p.admission_date, s.surgery_date 
FROM patients p
INNER JOIN surgeries s
    ON p.patient_id = s.patient_id;
```

**Output:**

<img width="730" height="531" alt="image" src="https://github.com/user-attachments/assets/2ea8490b-8277-4eaa-9811-2dc8d2c313f0" />

**Question 6**

<img width="1248" height="789" alt="image" src="https://github.com/user-attachments/assets/9da564b8-f1cb-4839-8dc1-83b54e4d45cb" />

**Syntax:**

```sql
SELECT p.first_name, s.surgery_id, s.patient_id, s.surgeon_id, s.surgery_date
FROM patients p
INNER JOIN surgeries s
    ON p.patient_id = s.patient_id
WHERE p.date_of_birth > '1990-01-01';
```

**Output:**

<img width="1286" height="307" alt="image" src="https://github.com/user-attachments/assets/e49b6c55-fdc4-4254-9096-5dd267a957f2" />

**Question 7**

<img width="1259" height="896" alt="image" src="https://github.com/user-attachments/assets/9bcfd2b8-6089-43ab-81dd-47a069bf67ca" />

**Syntax:**

```sql
SELECT c.cust_name AS 'Customer Name', c.city, s.name AS Salesman, s.city, s.commission
FROM customer c
JOIN salesman s
    ON c.salesman_id = s.salesman_id
WHERE c.city <> s.city and s.commission > 0.12;
```

**Output:**

<img width="1275" height="479" alt="image" src="https://github.com/user-attachments/assets/f5bc0c91-6064-49b3-ad2f-6dc29ac4efad" />

**Question 8**

<img width="938" height="976" alt="image" src="https://github.com/user-attachments/assets/49a43077-3890-4256-8552-fc9d32ea9624" />

**Syntax:**

```sql
SELECT o.ord_no, o.ord_date, o.purch_amt, c.cust_name AS 'Customer Name', c.grade , s.name AS 'Salesman', s.commission
FROM orders o
JOIN customer c
    ON o.customer_id = c.customer_id
JOIN salesman s
    ON o.salesman_id = s.salesman_id;
```

**Output:**

<img width="1325" height="798" alt="image" src="https://github.com/user-attachments/assets/471c4335-54d5-4128-95d9-0e20df10b9c2" />

**Question 9**

<img width="1228" height="955" alt="image" src="https://github.com/user-attachments/assets/677a3c4a-530c-4458-8b32-5e1d612f76af" />

**Syntax:**

```sql
SELECT o.ord_no, o.purch_amt, c.cust_name, c.city
FROM customer c
JOIN orders o
    ON c.customer_id = o.customer_id
WHERE o.purch_amt > 500 and o.purch_amt < 2000;
```

**Output:**

<img width="1244" height="405" alt="image" src="https://github.com/user-attachments/assets/0380cd60-e2a9-495c-9fa5-fb379651af91" />

**Question 10**

<img width="1207" height="947" alt="image" src="https://github.com/user-attachments/assets/86dcb213-3a01-4477-9106-dd3b340bfb71" />

**Syntax:**

```sql
SELECT c.cust_name AS 'Customer Name', c.city, s.name AS 'Salesman', s.commission
FROM customer c
JOIN salesman s
    ON c.salesman_id = s.salesman_id
WHERE s.commission > 0.12;
```

**Output:**

<img width="1227" height="673" alt="image" src="https://github.com/user-attachments/assets/d6ee2e42-405b-4dbd-9778-b1a2b380da31" />

## Module 5 SEB Completion Grades

<img width="1150" height="58" alt="image" src="https://github.com/user-attachments/assets/d27e971f-ff64-4d8a-81eb-919e9f4732ac" />
<img width="1881" height="969" alt="image" src="https://github.com/user-attachments/assets/ce745b1c-e672-4dd5-bde3-0ffdb7d203b8" />

## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
