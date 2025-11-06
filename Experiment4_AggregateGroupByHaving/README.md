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

<img width="1031" height="506" alt="image" src="https://github.com/user-attachments/assets/ee88848d-c0e9-41b6-b10b-63b207c7fb8f" />

**Syntax:**

```sql
SELECT PatientID, COUNT(Medications) AS AvgMedications 
FROM MedicalRecords
GROUP BY PatientID;
```

**Output:**

<img width="623" height="578" alt="image" src="https://github.com/user-attachments/assets/1aaa9305-e75c-4c00-a2b3-982425e5fb55" />

**Question 2**

<img width="1040" height="439" alt="image" src="https://github.com/user-attachments/assets/da7c2dc3-d3ab-43ac-a13f-32cbbf366bb4" />

**Syntax:**

```sql
SELECT Diagnosis, COUNT(Diagnosis) AS DiagnosisCount 
FROM MedicalRecords
GROUP BY Diagnosis
ORDER BY COUNT(Diagnosis) DESC LIMIT 1;
```

**Output:**

<img width="829" height="287" alt="image" src="https://github.com/user-attachments/assets/057a781b-868c-4080-bf5d-80880adfddcf" />

**Question 3**

<img width="993" height="568" alt="image" src="https://github.com/user-attachments/assets/b48d2f53-7219-405e-ba44-0b20c35c3490" />

**Syntax:**

```sql
SELECT Specialty, Gender, COUNT(*) AS TotalDoctors
FROM Doctors
GROUP BY Specialty, Gender
ORDER BY Specialty, Gender;
```

**Output:**

<img width="947" height="634" alt="image" src="https://github.com/user-attachments/assets/ab828259-8262-4f2b-83ec-f8ee216e4e16" />

**Question 4**

<img width="671" height="521" alt="image" src="https://github.com/user-attachments/assets/d6413f00-6200-4534-8354-16e225aaa23c" />

**Syntax:**

```sql
SELECT name AS Employee_Name, age as Age
FROM employee
ORDER BY AGE ASC LIMIT 1;
```

**Output:**

<img width="609" height="286" alt="image" src="https://github.com/user-attachments/assets/fb287312-00db-46e8-a392-c5ed0fbae3fa" />

**Question 5**

<img width="744" height="470" alt="image" src="https://github.com/user-attachments/assets/d580c52e-56c2-4b19-8039-227292d0a3c3" />

**Syntax:**

```sql
SELECT AVG(LENGTH(email)) AS avg_email_length 
FROM customer;
```

**Output:**

<img width="452" height="288" alt="image" src="https://github.com/user-attachments/assets/d44e0963-b205-428c-9054-55e35edd930c" />

**Question 6**

<img width="758" height="464" alt="image" src="https://github.com/user-attachments/assets/d7168c4c-fea8-40f5-88d9-5892333466a1" />

**Syntax:**

```sql
SELECT COUNT(*) AS COUNT
FROM employee
WHERE age > 32;
```

**Output:**

<img width="331" height="286" alt="image" src="https://github.com/user-attachments/assets/6f76c1a1-2749-4ad7-b0ab-8c494b2a2663" />

**Question 7**

<img width="661" height="513" alt="image" src="https://github.com/user-attachments/assets/338fddb2-c7f2-4ae6-a0fa-ade638432417" />

**Syntax:**

```sql
SELECT AVG(income) AS Average_Salary 
FROM employee;
```

**Output:**

<img width="452" height="285" alt="image" src="https://github.com/user-attachments/assets/ee3ea067-d5a3-4690-bc63-c856c7bd8a7c" />

**Question 8**

<img width="1192" height="534" alt="image" src="https://github.com/user-attachments/assets/cd968f42-4f80-414a-bc32-1240fbaa0601" />

**Syntax:**

```sql
SELECT occupation, MIN(workhour) 
FROM employee1
GROUP BY occupation;
```

**Output:**

<img width="596" height="460" alt="image" src="https://github.com/user-attachments/assets/bfcf3011-bc28-4d35-8fbd-623a6c91a54b" />

**Question 9**

<img width="1136" height="524" alt="image" src="https://github.com/user-attachments/assets/015e5282-8cbd-48f4-857a-dabffea31e35" />

**Syntax:**

```sql
SELECT address, SUM(salary) 
FROM customer1 
GROUP BY address
HAVING SUM(salary) > 2000;
```

**Output:**

<img width="622" height="467" alt="image" src="https://github.com/user-attachments/assets/73a23a71-575f-47b3-aabe-ec9fc99ff1ae" />

**Question 10**

<img width="1211" height="481" alt="image" src="https://github.com/user-attachments/assets/556aa9a5-faf6-4407-9812-821ba21ab10d" />

**Syntax:**

```sql
SELECT category_id, price as Price
FROM products
GROUP BY category_id 
HAVING MIN(price) < 10;
```

**Output:**

<img width="577" height="341" alt="image" src="https://github.com/user-attachments/assets/fa8beee0-2adc-4ffc-a8f8-0dbbbd1a00d0" />

![Output10](output.png)

## Module 3 SEB Completion Grades

<img width="1046" height="71" alt="image" src="https://github.com/user-attachments/assets/40263edf-d190-4187-b32a-fb6b9cc3be0a" />

<img width="1861" height="929" alt="image" src="https://github.com/user-attachments/assets/6f592522-5d6f-4092-ad33-ea562fcfa052" />

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
