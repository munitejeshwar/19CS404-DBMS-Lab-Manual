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
<img width="467" height="515" alt="image" src="https://github.com/user-attachments/assets/c8a51953-d4f5-40c7-a48f-f0a0cbec12c0" />


```sql
SELECT
    InsuranceCompany,
    COUNT(PatientID) AS TotalPatients
FROM Insurance
GROUP BY InsuranceCompany
ORDER BY InsuranceCompany;
```

**Output:**

<img width="659" height="544" alt="image" src="https://github.com/user-attachments/assets/8478444c-9469-48a9-be5f-fde45f3bf19e" />


**Question 2**
---
<img width="806" height="407" alt="image" src="https://github.com/user-attachments/assets/3475a323-93d9-4bfa-8da9-ab2010f00695" />


```sql
SELECT
    CASE
        WHEN (strftime('%Y','now') - strftime('%Y',DateOfBirth)
              - (strftime('%m-%d','now') < strftime('%m-%d',DateOfBirth))) BETWEEN 20 AND 30 THEN '20-30'
        WHEN (strftime('%Y','now') - strftime('%Y',DateOfBirth)
              - (strftime('%m-%d','now') < strftime('%m-%d',DateOfBirth))) BETWEEN 31 AND 40 THEN '31-40'
        WHEN (strftime('%Y','now') - strftime('%Y',DateOfBirth)
              - (strftime('%m-%d','now') < strftime('%m-%d',DateOfBirth))) BETWEEN 41 AND 50 THEN '41-50'
        ELSE 'Above 50'
    END AS AgeGroup,
    COUNT(*) AS TotalPatients
FROM Patients
GROUP BY AgeGroup
ORDER BY
CASE AgeGroup
    WHEN '20-30' THEN 1
    WHEN '31-40' THEN 2
    WHEN '41-50' THEN 3
    ELSE 4
END;
```

**Output:**

<img width="545" height="397" alt="image" src="https://github.com/user-attachments/assets/e5bca155-f6c4-435c-8e6e-2bcfc4ff97d5" />


**Question 3**
---
<img width="798" height="517" alt="image" src="https://github.com/user-attachments/assets/e2581419-3b63-4860-bbe4-71051147f2d8" />


```sql
SELECT Medication, AVG(Dosage) AS AvgDosage
FROM Prescriptions
GROUP BY Medication;
```

**Output:**

<img width="561" height="636" alt="image" src="https://github.com/user-attachments/assets/78503047-3a80-497c-9963-18fa5798606d" />


**Question 4**
---
<img width="670" height="378" alt="image" src="https://github.com/user-attachments/assets/784c9500-1e23-4fca-bb42-3746a5559c3c" />


```sql
SELECT name, max(income)
FROM employee
WHERE city = 'California';
```

**Output:**

<img width="525" height="282" alt="image" src="https://github.com/user-attachments/assets/29d01f7c-8eec-4498-9b51-c50b62c2deba" />


**Question 5**
---
<img width="546" height="400" alt="image" src="https://github.com/user-attachments/assets/552a4fc3-50ab-4305-acfc-b99382680c3c" />


```sql
SELECT AVG(income) AS Average_Salary
FROM employee;
```

**Output:**

<img width="472" height="274" alt="image" src="https://github.com/user-attachments/assets/4ec41a6c-d5c6-410a-bf64-011bb60e0f87" />


**Question 6**
---
<img width="650" height="372" alt="image" src="https://github.com/user-attachments/assets/dbd8d677-6ebd-4925-a1c7-2159aa3d4c9a" />


```sql
SELECT COUNT(DISTINCT city) AS unique_cities
FROM customer;
```

**Output:**

<img width="396" height="277" alt="image" src="https://github.com/user-attachments/assets/2f41b3a0-b6eb-43db-b39e-93427c328e8a" />

**Question 7**
---
<img width="625" height="411" alt="image" src="https://github.com/user-attachments/assets/56a8d20f-cfdc-4722-ac2e-c7e375d340cd" />


```sql
SELECT COUNT(*) AS COUNT
FROM customer;
```

**Output:**

<img width="429" height="282" alt="image" src="https://github.com/user-attachments/assets/151aed4d-b9db-44da-b309-e3a50e920022" />

**Question 8**
---
<img width="978" height="477" alt="image" src="https://github.com/user-attachments/assets/cc13842e-ca97-46c5-875b-9aafddc32d5d" />


```sql
SELECT
    (age/ 5) * 5  AS age_group,
    MAX(salary)
FROM customer1
GROUP BY (age / 5) * 5
HAVING MAX(salary) > 8000;
```

**Output:**

<img width="551" height="317" alt="image" src="https://github.com/user-attachments/assets/a31a56b3-247a-4c23-8513-39142fb4d300" />


**Question 9**
---
<img width="974" height="439" alt="image" src="https://github.com/user-attachments/assets/e7c2ed7a-bc48-4a87-9134-d049daac77a1" />


```sql
SELECT
    age,
    MIN(Income) AS Income
FROM employee
GROUP BY age
HAVING MIN(Income) < 1000000;
```

**Output:**

<img width="573" height="391" alt="image" src="https://github.com/user-attachments/assets/2c882332-a822-4a16-8701-cd10b7689bd7" />


**Question 10**
---
<img width="970" height="412" alt="image" src="https://github.com/user-attachments/assets/b0a4b3d0-e339-4fd1-ba5e-6b120afb8fae" />


```sql
SELECT jdate, SUM(workhour)
FROM employee1
GROUP BY jdate
HAVING SUM(workhour) > 40;
```

**Output:**

<img width="611" height="337" alt="image" src="https://github.com/user-attachments/assets/55156e4f-798f-4ba2-a66d-deb7bca19882" />

**Final Grades:**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/91d75723-be72-4e86-b742-f145b032d8db" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
