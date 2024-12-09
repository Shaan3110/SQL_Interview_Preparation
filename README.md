# SQL Interview Preparation!

## Select database

**Syntax** - use db_name

## Create table users
```
{  
	id int unsigned, -> making this always positive  
	name varchar(150),  
	password varchar(100),  
	contact varchar(150),  
	address text -> no limit over characters and no need to intialize a size,  
	dob date,  
	gender enum(“M”, ”F”, “O”),  
	status boolean -> 1 or 0  
}
```

## Two approaches for Insert

Single row  
  
Syntax - 
```
Insert into table_name ( column1, column2, column3, … ) values (value1, value2, value3 ,…);  
```
  
Multiple row  
  
Syntax - 
```
Insert into table_name ( column1, column2, column3, … ) values (value1, value2, value3 ,…), (value1, value2, value3 ,…);  
```
  
In case I am inserting all the columns then we don’t need to specify the columns as well  
  
Syntax - 
```
Insert into table_name values (value1, value2, value3 ,…), (value1, value2, value3 ,…);
```

## Different types of SQL commands?  
    

-   SELECT: Retrieves data from a database.
-   INSERT: Adds new records to a table.
-   UPDATE: Modifies existing records in a table.
-   DELETE: Removes records from a table.
-   CREATE: Creates a new database, table, or view.
-   ALTER: Modifies the existing database object structure.
-   DROP: Deletes an existing database object.

## Select Query  
      
Select column_names from table_name;  
      
With alias it would be  
      
``Select column_names as alias_name from table_name;  ``
      
For all columns  
      
``Select * from table_name;``

## Where Condition  
      
Select column_names from table_name where condition ;  
      
Conditions supported -  
    = equals  
    != not equal  
    >= greater than or equal to  
    <=less than or equal to  
    % module returning remainder  
    / divide returning the quotient  
      
Logical Operators  
    

**ALL -** TRUE if all of the subquery values meet the condition

**AND -** TRUE if all the conditions separated by AND is TRUE

**ANY -** TRUE if any of the subquery values meet the condition

**BETWEEN -** TRUE if the operand is within the range of comparisons

**EXISTS -** TRUE if the subquery returns one or more records

**IN -** TRUE if the operand is equal to one of a list of expressions

**LIKE -** TRUE if the operand matches a pattern

**NOT -** Displays a record if the condition(s) is NOT TRUE

**OR -** TRUE if any of the conditions separated by OR is TRUE

**SOME -** TRUE if any of the subquery values meet the condition

## Constraints in SQL

SQL constraints are used to specify rules for the data in a table. Constraints are used to limit the type of data that can go into a table. This ensures the accuracy and reliability of the data in the table. If there is any violation between the constraint and the data action, the action is aborted.  
  
NOT NULL  
UNiQUE  
DEFAULT  
CHECK  
FOREIGN KEY  
PRIMARY KEY  
  
Example,  
 ``` 
create table students  
{  
id INT NOT NULL unique,  
name varchar(100) not null,  
email varchar(150) not null unique,  
age tinting check(age >= 18),  
status boolean default 1  
}
```

## And, OR and Not

**And Operator:** This operator compares two expressions or conditions and returns true if both the expressions are true.  
  
**Or Operator:** This operator compares two expressions or conditions and returns true if only one or both expressions are true.  
  
**Not Operator:** This operator reverses or negative the input.

## IN Operator

Allows you to use where condition with specific multiple values. It’s a shorthand for multiple OR operators.  
  
Syntax: Select * from table_name where column_name in (“value1”, “value2”);

## Like Operator

The Like operator is used in a where clause to search for a specified pattern in a column  
  
% - represents zero, one or multiple characters  
  
_ - represents one, single character  
  
**Example:**  
  
1. _r% means column has r in second position and any number of characters after that.  
  
2. a_% means column has a at start and minimum one character after that in length

## Between and Not Between

Syntax -  
  
``Select * from table_name where column_name between value1 and value2;  ``
  
Value1 and Value2 are inclusive in such case so 1 and 5 means 1,2,3,4,5.

## Order By and Distinct

Order By is used in sql for sorting of database based on any columns on descending or ascending order.  
  
Syntax -  
  
``Select * from table_name order by column_name desc;``  
  
**Note:** By default order by sorts data in ascending order for the user.  
  
Distinct is used in sql for finding unique values out of a column  
  
``Select  distinct column_name from table_name``

## IS NULL and IS NOT NULL

IS NULL is used to filter if a column is Null or not NULL  
  
Syntax -  
  
``Select * from table_name where column_name is NULL;``

## Limit and Offset

These are used to limit or control the number of rows returned by a query.  
  
Syntax -  
  
``Select * from table_name limit 5;``  
  
Offset is used to define where to start returning data;  
  
``Select * from table_name limit 5 offset 3;``  
  
This would return 5 entries after skipping first 3 rows

## Aggregate Functions ( Min, Max, Avg, Count and Sum )

**Count:** Returns the number of rows in database tables  
  
**Sum:** Returns the sum of a numeric column  
  
**Avg:** Calculates the average of a set of values  
  
**Min:** Returns the lowest value in a set of non-NULL values  
  
**Max:** Returns the greatest value in a set of non-NULL values

## Primary Key

It is a unique identifier for each record in a table. It ensures that each row in the table has a distinct and non-null value in the primary key column. Primary keys enforce data integrity and create relationships between tables

## Delete vs Truncate  
  
The DELETE command is used by professionals to remove particular rows from a table based on a condition, allowing you to selectively delete records. TRUNCATE, on the other hand, removes all rows from a table without specifying conditions. TRUNCATE is faster and uses fewer system resources than DELETE but does not log individual row deletions.

## Update Query and Delete Query  
  
```
Update table_name  
set field1 = newvalue1,  
field2 = newvalue2 where condition;  
```
  
`Delete from table_name where condition;`

## Commit and Rollback  
  
Transaction - start -> commit -> rollback

## Rank 2nd highest max_salary from employees table  
  
```
WITH RankedEmployees AS (  
SELECT  
employee_id,  
salary,  
ROW_NUMBER() OVER (ORDER BY salary DESC) AS salary_rank  
FROM employees  
)  
SELECT salary  
FROM RankedEmployees  
WHERE salary_rank = 2;  
```
  
Or,  
  
`Select salary from ck_employees order by salary limit 1 offset 1;`

## Query Question

Query an alphabetically ordered list of all names in **OCCUPATIONS**, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).  
  
Query the number of ocurrences of each occupation in **OCCUPATIONS**. Sort the occurrences in ascending order, and output them in the following format:  
  
There are a total of [occupation_count] [occupation]s.  
  
  
where [occupation_count] is the number of occurrences of an occupation in **OCCUPATIONS** and [occupation] is the lowercase occupation name. If more than one Occupation has the same [occupation_count], they should be ordered alphabetically.  
  
**Query:**  
  
```Select Concat(Name,'(',Left(Occupation,1),')') from OCCUPATIONS order by Name;  
  
Select Concat('There are a total of ', Count(Occupation), ' ', Lower(Occupation), 's.') from occupations group by occupation order by count(occupation); 
``` 
  
Using Union it would be  
  
`Select Concat(Name, '(', Left(Occupation, 1), ')') from OCCUPATIONS ` 
  
UNION ALL  
  
`Select Concat('There are a total of ', Count(Occupation), ' ', Lower(Occupation), 's.') from OCCUPATIONS group by Occupation ORDER BY 1;  `
  
Link: [https://www.hackerrank.com/challenges/the-pads/problem?isFullScreen=true](https://www.hackerrank.com/challenges/the-pads/problem?isFullScreen=true)

## Ranking 

Ranking is a technique used in SQL to assign a numerical rank to rows based on their values in a specific column. This is often useful for identifying top or bottom performers, sorting data based on rank, or creating leaderboards.  
      
      
Common Ranking Functions:  

-   **ROW_NUMBER()**: Assigns a sequential row number to each row within a partition, starting from 1.
-   **RANK()**: Assigns a rank to each row within a partition, with ties sharing the same rank.
-   **DENSE_RANK()**: Assigns a dense rank to each row within a partition, with ties sharing the same rank and no gaps between ranks.

## Normalization 

Normalization is the process of organizing data in a database to minimize redundancy and dependency. It helps to ensure data integrity, consistency, and efficiency.  
      
Why Normalize?  

-   **Reduces data redundancy:** Avoids storing the same data multiple times.
-   **Enhances data integrity:** Ensures data consistency and accuracy.
-   **Improves database performance:** Reduces the amount of data that needs to be stored and retrieved.
-   **Facilitates database maintenance:** Makes it easier to modify and update the database schema.  
      
    **Normalization Forms:**  
      
    There are several normalization forms, each with its own set of rules:  
    

1.  **First Normal Form (1NF):**

-   Each column in a table should contain atomic values (not repeating groups).
-   Avoid storing multiple values in a single column.  
    

3.  **Second Normal Form (2NF):**

-   The table should be in 1NF.
-   All non-key attributes should be fully dependent on the primary key.  
    

5.  **Third Normal Form (3NF):**

-   The table should be in 2NF.
-   No non-key attribute should be transitively dependent on the primary key.  
    

7.  **Boyce-Codd Normal Form (BCNF):**

-   The table should be in 3NF.
-   Every determinant should be a superkey.

## Views in SQL  
  
Views are a kind of virtual table. A view also has rows and columns as they are on a real table in the database. We can create a view by selecting fields from one or more tables present in the database. A View can either have all the rows of a table or specific rows based on certain conditions.  
  
```CREATE VIEW view_name AS  
SELECT column1, column2.....  
FROM table_name  
WHERE condition;
```




