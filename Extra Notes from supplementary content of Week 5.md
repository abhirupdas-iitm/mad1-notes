### Week 5 Extra Lecture 1  
#### Introduction to SQLite and Relational Database Exploration  
##### Description: Explains how to create and explore a relational database using SQLite. Covers differences between SQLite and client-server databases, database file structure, using GUI tools, creating tables, constraints, relationships, and executing basic SQL queries.

### 1. Introduction to Relational Databases
Relational databases store data in the form of **tables**.
Common relational database systems:
- PostgreSQL  
- MySQL  
- MariaDB  

These typically follow a **client-server model**:
- A server process manages the database  
- Clients connect to the server to perform operations  

### 2. What is SQLite?
SQLite is a **self-contained, embedded relational database**.
Key characteristics:
- No client-server architecture  
- Runs inside the application itself  
- No separate server process required  
- Entire database stored as a **single file**

This makes SQLite:
- Lightweight  
- Easy to use  
- Zero-configuration  

### 3. SQLite Database File
SQLite stores everything in one file:
- Tables  
- Data  
- Indexes  
- Schema definitions  
Common file extensions:
- `.db`  
- `.sqlite`  
- `.sqlite3`  
Operations on the database = operations on the file:
- Copy file → backup database  
- Delete file → delete database  
- Move file → move database  

### 4. Development Environment
Tools required:
- Browser (Chrome, etc.)  
- Terminal  
- SQLite installed  
- GUI tool (optional but recommended)
Project setup example:
`experiment-sqlitedb/`

### 5. SQLite Client Options
#### 1. Command Line Client
Tool: `sqlite3`
Check installation:
which sqlite3
#### 2. GUI Tools
Examples:
- DBeaver  
- SQLite Studio  
- DB Browser for SQLite  
Used in this lecture:
DB Browser for SQLite

### 6. Creating a Database
Steps:
1. Open DB Browser  
2. Click New Database  
3. Choose location  
4. Enter filename:
`testdb.sqlite3  `
Database is created as a file.

### 7. Creating Tables
Example: `user` table
Columns:
- user_id → integer, primary key, auto increment  
- username → text, unique  
- email → text, unique  
Constraints:
- Primary Key → uniquely identifies rows  
- Auto Increment → automatic ID generation  
- Unique → prevents duplicates  
Save using:
Write Changes (commit)

### 8. Inserting Data
Example:
- username: Thejesh  
- email: i@thejeshgn.com  
### 9. Constraints in Action
If a field is unique:
- Duplicate values are not allowed  
Ensures:
Data integrity

### 10. Creating Another Table
Example: `article`
Columns:
- article_id → primary key  
- title  
- content  
### 11. Relationships Between Tables
Relational databases use **foreign keys**.
Example:
- One article → many authors  
- One user → many articles  
### 12. Many-to-Many Relationship Table
Table: `article_authors`
Columns:
- article_id  
- user_id  
Properties:
- Both are foreign keys  
- Combined → composite primary key  
Purpose:
Link users and articles

### 13. Inserting Relationship Data
Example:
- article_id = 1  
- user_id = 1  
Meaning:
User 1 is an author of Article 1  

### 14. Querying Data (JOIN)
Goal:
Get all authors of an article  
Approach:
- Combine user + article_authors  
- Match using user_id  
Uses:
- JOIN  
- Alias (AS)

Result:
List of usernames

### 15. Key Concepts Demonstrated
- Database as a file  
- Table creation  
- Constraints  
- Data insertion  
- Relationships  
- JOIN queries  

### 16. Advantages of SQLite
- Lightweight  
- No setup  
- Easy experimentation  
- Zero configuration  

### 17. SQLite vs Production Databases
Typical workflow:
- Development → SQLite  
- Production → MySQL / PostgreSQL  

### 18. Key Takeaways
SQLite is:
- Embedded  
- File-based  
- Serverless  
Core ideas:
- Tables  
- Constraints  
- Relationships  
- Joins  
All concepts apply to larger databases.

---
