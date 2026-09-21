# Experiment 2: DDL Commands
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
Insert the below data into the Student_details table, allowing the Subject and MARKS columns to take their default values.

RollNo      Name          Gender      
----------  ------------  ----------  
204         Samuel Black  M          

Note: The Subject and MARKS columns will use their default values.

```sql
INSERT INTO Student_details (RollNo, Name, Gender)
VALUES (204, 'Samuel Black', 'M');

SELECT RollNo, Name, Gender 
FROM Student_details 
WHERE RollNo = 204;

```

**Output:**

<img width="1196" height="250" alt="image" src="https://github.com/user-attachments/assets/9b7bebbe-2b61-4b18-9171-8a04aa904726" />


**Question 2**
---
Insert all customers from Old_customers into Customers

Table attributes are CustomerID, Name, Address, Email

```sql

INSERT INTO Customers (CustomerID, Name, Address, Email)
SELECT CustomerID, Name, Address, Email
FROM Old_customers;

```

**Output:**

<img width="1196" height="250" alt="image" src="https://github.com/user-attachments/assets/5aac1182-a974-4b3a-a13b-3fb0d7f29f81" />


**Question 3**
---
Insert the following students into the Student_details table:
RollNo      Name        Gender      Subject     MARKS
----------  ----------  ----------  ----------  ----------
202            Ella King         F           Chemistry   87
