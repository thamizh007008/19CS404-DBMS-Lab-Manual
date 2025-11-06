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

<img width="712" height="229" alt="image" src="https://github.com/user-attachments/assets/1ef7d835-c8e6-4db5-a3ba-218a3d15a829" />

**Syntax:**

```sql
UPDATE products
SET availability  = availability  * 2
WHERE product_id = 1;
```

**Output:**

<img width="1189" height="183" alt="image" src="https://github.com/user-attachments/assets/1cc81747-1e9a-4d14-993a-e8b6bf32c03d" />


**Question 2**

<img width="1245" height="693" alt="image" src="https://github.com/user-attachments/assets/4d38a031-d452-43ba-87cb-9d009278fc33" />

**Syntax:**

```sql
UPDATE employees  
SET salary = CASE
    WHEN department_id = 40 THEN ROUND (salary * 1.25)
    WHEN department_id = 90 THEN ROUND (salary * 1.15)
    WHEN department_id = 110 THEN ROUND (salary * 1.10) 
    ELSE salary
END;
```

**Output:**

<img width="1204" height="215" alt="image" src="https://github.com/user-attachments/assets/c46b1757-fb79-41ce-907f-21bca0d69ca8" />


**Question 3**

<img width="1205" height="641" alt="image" src="https://github.com/user-attachments/assets/5cd27b63-affd-442f-8d58-0a0b04c745c2" />

**Syntax:**

```sql
UPDATE EMPLOYEES
SET EMAIL = 'not available',
    COMMISSION_PCT = 0.55
WHERE DEPARTMENT_ID = 110;
```

**Output:**

<img width="1269" height="284" alt="image" src="https://github.com/user-attachments/assets/9bebe57c-f4a8-47ee-9aa5-afd48c82a4f1" />


**Question 4**

<img width="880" height="314" alt="image" src="https://github.com/user-attachments/assets/714eb1a7-d31a-4d4f-8431-492af116cc6f" />

**Syntax:**

```sql
UPDATE PRODUCTS
SET QUANTITY = QUANTITY * 1.10;
```

**Output:**

<img width="1092" height="296" alt="image" src="https://github.com/user-attachments/assets/c9740a98-4ec1-4cec-84c7-42ba40d1d695" />


**Question 5**

<img width="1201" height="636" alt="image" src="https://github.com/user-attachments/assets/dce457fd-4b63-42b6-8f9a-ef207b8e92e4" />

**Syntax:**

```sql
UPDATE purchases
SET per_unit_price = 25,
    total_price = quantity * 25
WHERE purchase_date = '2022-08-15'
    AND product_id = 12;
```

**Output:**

<img width="1303" height="252" alt="image" src="https://github.com/user-attachments/assets/74cb87ff-ddb1-4de1-985a-9f3167dc7485" />


**Question 6**

<img width="1271" height="366" alt="image" src="https://github.com/user-attachments/assets/38f05b35-fd2b-4e21-b5a2-5279faa4bf6b" />

**Syntax:**

```sql
DELETE FROM Customer
WHERE (GRADE = 3 OR AGENT_CODE = 'A008')
    AND OUTSTANDING_AMT < 5000;
```

**Output:**

<img width="1080" height="128" alt="image" src="https://github.com/user-attachments/assets/26b7e75e-9a12-42d7-a1f3-8c653a76446b" />


**Question 7**

<img width="1274" height="377" alt="image" src="https://github.com/user-attachments/assets/ac6bdea9-582f-485f-9d9f-076a12701cf5" />


**Syntax:**

```sql
DELETE FROM customer
WHERE GRADE % 2 = 1;
```

**Output:**

<img width="1089" height="136" alt="image" src="https://github.com/user-attachments/assets/e6d4b247-201d-4ea9-8562-29a7a226b611" />


**Question 8**

<img width="1283" height="460" alt="image" src="https://github.com/user-attachments/assets/c512ce6c-168c-472b-90db-8ada1fa35236" />

**Syntax:**

```sql
DELETE FROM customer
WHERE cust_name LIKE '%Holmes%';
```

**Output:**

<img width="1104" height="175" alt="image" src="https://github.com/user-attachments/assets/1fcc47f3-4b1e-4856-973d-cfbdda77f658" />


**Question 9**

<img width="1277" height="378" alt="image" src="https://github.com/user-attachments/assets/991849c3-98dc-423a-8ee3-89370c5cd9dc" />

**Syntax:**

```sql
DELETE FROM customer
WHERE CUST_CITY <> 'New York'
    AND OUTSTANDING_AMT > 5000;
```

**Output:**

<img width="1112" height="194" alt="image" src="https://github.com/user-attachments/assets/d1d31407-5af8-4766-bffb-8533f407d92b" />


**Question 10**

<img width="1277" height="561" alt="image" src="https://github.com/user-attachments/assets/47d94311-ae9a-467f-8697-fc7618b92327" />

**Syntax:**

```sql
DELETE FROM customer
WHERE GRADE = 2;
```

**Output:**

<img width="723" height="568" alt="image" src="https://github.com/user-attachments/assets/295ce263-307c-4e20-b5a3-3655d23abc7b" />

**Question 11**

<img width="1141" height="478" alt="image" src="https://github.com/user-attachments/assets/1c36833d-7bdf-45e7-a45d-7865bd6ff94b" />


**Syntax:**

```sql
SELECT *
FROM salesman
WHERE name LIKE 'N__l%';
```

**Output:**

<img width="1157" height="319" alt="image" src="https://github.com/user-attachments/assets/50fe7645-5f52-4691-b9a9-d31923ee0eb7" />

**Question 12**

<img width="1134" height="511" alt="image" src="https://github.com/user-attachments/assets/57af5b83-34b1-4231-a343-73c476123546" />

**Syntax:**

```sql
SELECT*
FROM EmployeeInfo1 
WHERE Department IS NULL;
```

**Output:**
<img width="1288" height="132" alt="image" src="https://github.com/user-attachments/assets/61b563f4-f36d-4ea2-9603-5d6258f5a13a" />

**Question 13**

<img width="984" height="604" alt="image" src="https://github.com/user-attachments/assets/1688f983-0b0e-4fdd-b291-f8cf1b2ea2a0" />

**Syntax:**

```sql
SELECT 
    id,
    base,
    CASE
        WHEN base IS NOT NULL THEN 'Provided'
        ELSE 'Not Provided'
    END AS base_status
FROM
    Calculations;
```

**Output:**

<img width="897" height="461" alt="image" src="https://github.com/user-attachments/assets/de1ed423-fb9c-4566-b93d-ad78fb234ad8" />

**Question 14**

<img width="1220" height="661" alt="image" src="https://github.com/user-attachments/assets/a919c49e-51de-4862-80c2-1cae2568b66f" />

**Syntax:**

```sql
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE purch_amt < 200
    OR (ord_date > '2012-02-10' AND customer_id >= 3009);
```

**Output:**

<img width="1200" height="399" alt="image" src="https://github.com/user-attachments/assets/db0591ab-ba70-44ef-a75a-41c8164309e6" />

**Question 15**

<img width="941" height="599" alt="image" src="https://github.com/user-attachments/assets/81c17115-4d3e-48f7-8994-ae786f70a00c" />

**Syntax:**

```sql
SELECT name, city
FROM salesman
WHERE LOWER (city) in ('london', 'rome');
```

**Output:**

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/d26763cf-869f-40a3-928d-2a9443390c4b" />

**Question 16**

<img width="1217" height="387" alt="image" src="https://github.com/user-attachments/assets/0cd9b13b-1c89-4257-95d3-28d4ab050b61" />

**Syntax:**
```sql
SELECT 
    product_id,
    original_price,
    discount_percentage,
    original_price * (1 - discount_percentage) AS discounted_price,
    CAST(CAST(1 - discount_percentage) * 100 AS INT) AS TEXT) || '%' AS discounted_price_percentage
FROM
    products;
```

**Output:**

<img width="1260" height="461" alt="image" src="https://github.com/user-attachments/assets/d5dc474a-9cda-4e04-8d67-a06eb20ed675" />

**Question 17**

<img width="1108" height="508" alt="image" src="https://github.com/user-attachments/assets/eac4b2b3-a097-4bf1-a432-58c886a1843c" />

**Syntax:**

```sql
SELECT
    product_id,
    original_price,  
    discount_percentage,  
    original_price * discount_percentage AS discount_amount 
FROM
    products;
```

**Output:**

<img width="1203" height="227" alt="image" src="https://github.com/user-attachments/assets/d3081331-edc8-4d5c-83e9-9807fbd19115" />

**Question 18**

<img width="841" height="597" alt="image" src="https://github.com/user-attachments/assets/48f997a5-0d2b-425c-9784-ad9a44623d6f" />

**Syntax:**

```sql
SELECT *
FROM emp
WHERE hiredate > '2020-01-01';
```

**Output:**

<img width="1292" height="214" alt="image" src="https://github.com/user-attachments/assets/fa93b6e8-2690-4a66-89a1-e62a47c6a7e6" />

**Question 19**

<img width="913" height="627" alt="image" src="https://github.com/user-attachments/assets/c549e208-f65d-406e-91d4-4f83d9c4c022" />

**Syntax:**

```sql
SELECT *
FROM emp
WHERE strftime("%Y", hiredate) = '2022';
```

**Output:**

<img width="1280" height="218" alt="image" src="https://github.com/user-attachments/assets/70b04244-921a-4117-8ebe-3f2b5256c68c" />

**Question 20**

<img width="1049" height="544" alt="image" src="https://github.com/user-attachments/assets/449b2f6b-7d19-4a37-aaff-8156fc95fdbb" />

**Syntax:**

```sql
SELECT*
FROM emp
WHERE ename LIKE'__r%';
```

**Output:**

<img width="1284" height="216" alt="image" src="https://github.com/user-attachments/assets/d09c8118-bfec-4c88-b730-4d7011ee8448" />

## Module 2 SEB Completion Grades

<img width="1164" height="73" alt="image" src="https://github.com/user-attachments/assets/d9b6b6fa-d246-45a7-b588-8ea9845a7ee0" />

<img width="1867" height="921" alt="image" src="https://github.com/user-attachments/assets/f4030864-544a-4257-8cc4-fe42874fa144" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
