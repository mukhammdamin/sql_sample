# sql_sample
A collection of my sample SQL files and Projects

# SQL Aggregate functions
-To combine multiple entries into a single ,summarised result
-Also here it is best if the database does this for us
## For this,we can tell the databese to aggregate the result
-Counting All entries (COUNT(*)):
### SELECT COUNT (*) FROM students

## Additional aggregate functions: 
▶ Maximum: SELECT MAX(age) FROM students
▶ Minimum: SELECT MIN(age) FROM students 
▶ Sum: SELECT SUM(age) FROM students 
▶ Average: SELECT AVG(age) FROM students

## Filtering with LIKE
▶ So far, we could only filter by an exact value 
▶ Sometimes, we want to perform a more complex search 
- For this, we can use the LIKE clause: 
▶ ... WHERE [column] LIKE [pattern] 
▶ Available placeholders in the pattern: 
▶ %: Represents zero, one or multiple characters 
▶ _: Represents exactly one character: 
- Example: 
▶ Can we find all students whose email addresses end with @gmail.com? 
▶ SELECT * FROM students WHERE email LIKE '%@gmail.com' 
▶ How many students do we have in our database, whose name starts with 'M'? 
▶ SELECT COUNT(*) FROM students WHERE firstname LIKE 'M%' 
▶ How many students do we have in our database, whose name starts with 'M', followed 
by exactly 2 more characters? 
▶ SELECT COUNT(*) FROM students WHERE firstname LIKE 'M__'

# THE BIG 6 IN SQL

### The Big 6 are the foundation clasuses in SQL queries

## SELECT grade_level ,AVG(gpa) AS avg_gpa  > Columns to display
## FROM students > Table to pull data from
## WHERE school_lunch = "Yes" > Criteria to filter the rows by
## GR0UP BY grade_level > Column to group the rows by
## HAVING avg_gpa < 3.3 > Criteria to filter the grouded rows by
## ORDER BY grade level; > Column to sort values


