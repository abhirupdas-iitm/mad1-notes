## Lecture 1
### Models and Persistent Storage (Introduction to the M in MVC)
##### Description: Introduction to the concept of **models** in the MVC architecture. This lecture explains the need for **persistent storage**, introduces the **Gradebook example** used throughout the course, and demonstrates how structured tabular data and relationships between entities (students and courses) motivate the need for proper data models.

### 1. Models in MVC
In the **MVC (Model–View–Controller)** architecture:

- **Model** → represents data and data logic  
- **View** → presentation layer (what the user sees)  
- **Controller** → handles interactions and updates  

This lecture focuses on the **Model**, which is responsible for managing application data.
A model defines:
- how data is **stored**
- how data is **organized**
- how data is **retrieved and manipulated**
To understand models, we must first understand the concept of **persistent storage**.

### 2. Persistent Storage
Persistent storage refers to **data that survives even after a system restart or crash**.

Example problem:
If the server running our application restarts:
- all in-memory variables are lost
- all user data disappears
This is unacceptable for most applications.
Therefore we need a way to **store data permanently** so that it can be loaded again when the system restarts.

### 3. Running Example: Gradebook Application
Throughout the course, the main example used is a **student gradebook system**.
This system contains several types of data:
#### Students
Each student has information such as:
- Student ID (unique)
- Name
- Address
- Hostel
- Room number
Example:

| Name            | IDNumber |
| --------------- | -------- |
| Sunil Shashi    | MAD001   |
| Chetana Anantha | MAD002   |
Important property:
- **Student IDs must be unique**
- **Names are not guaranteed to be unique**
Two students can have the same name but **cannot have the same ID**.

#### Courses
Courses also have structured information.
Each course has:
- Course ID
- Course Name
- Department
- Academic year
Example:

| CourseID | Name                                   |
| -------- | -------------------------------------- |
| EE1001   | Introduction to Electrical Engineering |
| AM1100   | Engineering Mechanics                  |
Properties:
- Course IDs are unique
- Course names may sometimes repeat
Example:
Two different departments may both offer a course called **Calculus**, so the **course ID is the reliable identifier**.

### 4. Relationships Between Students and Courses
In the gradebook system:
- A **student can register for multiple courses**
- A **course can have multiple students**
This creates a **many-to-many relationship**.

Example questions:
- Which students are registered for course **BT1010**?
- Which courses is student **MAD001** enrolled in?

Therefore, the system must store not only:
- students
- courses

but also the **relationship between them**.

### 5. Representing Data Using Tables
The lecture introduces **tabular data representation**.
Example:
#### Student Table

| Name            | IDNumber |
| --------------- | -------- |
| Sunil Shashi    | MAD001   |
| Chetana Anantha | MAD002   |
#### Course Table

| CourseID | Name                                   |
| -------- | -------------------------------------- |
| EE1001   | Introduction to Electrical Engineering |
| AM1100   | Engineering Mechanics                  |
This form of representation resembles a **spreadsheet**.

### 6. Structured Data
This type of table represents **structured data**.
Structured data means:
- every row follows the **same format**
- each column represents a **specific attribute**
Example structure for students:

| Column   | Meaning      |
| -------- | ------------ |
| Column 1 | Student Name |
| Column 2 | Student ID   |
Every student record must follow the same pattern.
If the columns are switched randomly, the structure breaks.

### 7. Spreadsheets as a Data Representation
Spreadsheets are a natural way to represent structured data.
Key characteristics:
- Data organized in **rows and columns**
- Each cell stores a value
- Groups of cells can be treated as **ranges**
- Multiple sheets can exist within one spreadsheet

Examples of spreadsheet tools:
- Google Sheets
- Microsoft Excel
- LibreOffice Calc
Spreadsheets are powerful because they allow operations across cells and tables.

### 8. Representing Relationships
We must now represent the **student-course relationship**.
One incorrect approach would be storing complete information repeatedly.
Example entry:
```
Student Name
Student Address
Course ID
Course Name
Department
Marks
```
This would be repeated for every student-course pair.
This is problematic because:
- the same student name would appear many times
- the same course name would appear many times
This leads to **data redundancy**.

### 9. Avoiding Redundancy
Instead of repeating full information, we store only **identifiers**.
We create a separate table representing the relationship.
Example:

| StudentID | CourseID | Marks |
| --------- | -------- | ----- |
| MAD001    | BT1010   | 78    |
| MAD002    | EE1001   | 30    |
| MAD005    | EE1001   | 68    |
Meaning:
- student **MAD001** took course **BT1010**
- student **MAD002** took course **EE1001**
Advantages:
- compact representation
- no duplication of student names or course names
- efficient data storage
### 10. Keys
The identifiers used in these tables are called **keys**.
Examples:
Student table key:
```
StudentID
```
Course table key:
```
CourseID
```
Relationship table uses:
```
StudentID + CourseID
```
These keys uniquely identify entities and relationships.

### 11. Why IDs Are Better Than Names
Using IDs instead of names avoids several problems.

Example issue:
Two students named **Rahul Sharma**.
If names were used as identifiers:
```
Rahul Sharma → Course X
```
We would not know which Rahul Sharma.
Using IDs solves this:
```
MAD045 → Course X
MAD117 → Course X
```
IDs guarantee uniqueness.

### 12. ID Design Patterns
IDs often follow a pattern.
Example student ID:
```
MAD001
MAD002
MAD003
```
Structure:
```
MAD + 3 digit number
```
Advantages:
- easy validation
- predictable format
- easy generation
Similarly, course IDs may follow department codes:
```
EE1001
AM1100
ME1100
```

### 13. Unicode and Text Fields
While IDs usually follow strict patterns, names may contain:
- spaces
- special characters
- different alphabets
This is where **Unicode and UTF-8 encoding** become important.
In the course examples, only English characters are used for simplicity.

### 14. Relationship Table Example
A relationship table might look like:

| StudentID | CourseID | Marks |
| --------- | -------- | ----- |
| MAD001    | BT1010   | 78    |
| MAD002    | EE1001   | 30    |
Important observations:
- student IDs repeat
- course IDs repeat
- combination represents enrollment
This captures the **entire relationship efficiently**.

### 15. Core Questions Raised
The lecture ends by asking several key questions.
#### 1. How should data be stored?
Example possibilities:
- spreadsheets
- files
- databases
#### 2. How should data survive system crashes?
If a server crashes:
- memory data is lost
- we must reload saved data
This is why **persistent storage** is necessary.
#### 3. How should relationships be represented?
Possible approaches:
- repeating full records (inefficient)
- separate relationship tables (better)
#### 4. How can structured data be manipulated?
We need systems that allow:
- querying
- updating
- retrieving relationships efficiently

### Summary
This lecture introduced the concept of **models** in MVC and motivated the need for structured persistent storage.
Key ideas:
- Models manage application data
- Applications require **persistent storage**
- Data can be represented as **tables**
- Entities such as **students and courses** must be uniquely identified
- Relationships between entities must be stored separately
- IDs are used as **keys** to uniquely identify records
- Spreadsheets provide a simple conceptual model for structured data
These ideas form the foundation for the upcoming lectures on **data storage mechanisms and relational databases**.

### Notes to be taken for `Activity Question 1`
1. Microsoft Access is also a relational database management systems (RDBMS). (Question: 1)
2. One of the main disadvantages of spreadsheets compared to RDBMS is a lack of the concept of an atomic operation. (Question: 3)
---
## Lecture 2
### Mechanisms for Persistent Storage
##### Description: This lecture explores different mechanisms for storing application data persistently. It discusses Python data structures for representing relationships, introduces the concept of keys and identifiers, examines serialization methods such as pickle and CSV/TSV, and compares spreadsheets, relational databases (SQL), and NoSQL databases for managing structured and semi-structured data.

### 1. Need for Persistent Storage
Applications must store information in such a way that it can be **retrieved later**, even if:
- the program stops
- the server restarts
- the system crashes
Therefore we need **persistent storage mechanisms**.
Before thinking about saving data to disk, we first need to consider **how the data is represented in memory**.

### 2. Representing Data in Python
Data in applications can initially be represented using **Python data structures**.

Example representation:
```
students = ["Alice", "Bob", "Charlie"]
courses = ["Introduction to EE", "Applied Mechanics", "Calculus"]
```

```
relationships = [
("Alice", "Introduction to EE"),
("Bob", "Calculus"),
("Alice", "Calculus"),
("Charlie", "Applied Mechanics")
]
```
Each tuple represents a relationship:
```
(Student Name, Course Name)
```
Example:
```
("Alice", "Introduction to EE")
```
means:
Alice has taken the course Introduction to EE.

### 3. Problems With Direct Name-Based Relationships
Using full names directly creates several issues.
### Typing Errors
Long names increase the chance of mistakes.
Example:
```
"Introduction to EE"
"Introduction to Ee"
```
Even small differences cause inconsistencies.

#### Duplicate Names
Two people may share the same name.
Example:
```
Alice
Alice
```
The system cannot determine which student is being referenced.

#### Poor Scalability
Repeatedly storing long strings consumes more storage and increases the probability of human error.

### 4. Using Keys Instead of Names
A better approach is to use **unique identifiers (keys)**.

Example:
```
students = {
0 : "Alice",
1 : "Bob",
2 : "Charlie"
}

courses = {
0 : "Introduction to EE",
1 : "Applied Mechanics",
2 : "Calculus"
}

relationships = [
(0,0),
(1,2),
(0,2),
(2,1)
]
```
Meaning:
```
(0,0) → Alice took Introduction to EE
(1,2) → Bob took Calculus
```

### 5. Benefits of Keys
Using keys provides several advantages.
#### Reduced Typing Errors
Numbers are easier to enter correctly than long names.

#### Guaranteed Uniqueness
Keys are designed to be unique.
Even if two people have the same name:
```
Alice → ID 10
Alice → ID 24
```
the system can distinguish them.

#### Efficient Storage
Relationships can now be stored compactly using small numeric values.

### 6. Dictionaries as Key-Value Storage
Python dictionaries provide a natural way to represent key-value mappings.
Example:
```
students = {
0 : "Alice",
1 : "Bob",
2 : "Charlie"
}
```
A dictionary can be viewed as:
```
key → value
```
This allows direct lookup.
Example:
```
students[0] → "Alice"
```

### 7. Using Classes to Structure Data
Instead of simple dictionaries, Python classes can provide better structure.
Example concept:
class Student:
- name
- id
The class constructor initializes a student object.
Example idea:
```
class Student:

    idnext = 0

    def __init__(self, name):
        self.name = name
        self.id = Student.idnext
        Student.idnext += 1
```
This creates **automatic unique IDs**.

### 8. Class Variables vs Instance Variables
In the previous example:
```
idnext
```
is a **class variable**.
Meaning:
- shared by all instances of the class
- not specific to one student
Example:
Student creation sequence:
```
Student 1 → id = 0  
Student 2 → id = 1  
Student 3 → id = 2  
```
The class variable keeps track of the next available ID.

### 9. Limitations of Program-Level ID Generation
Generating IDs within the program has limitations.
If multiple programs run simultaneously:
- they may generate the same ID
- data conflicts may occur
For this reason, **databases usually handle ID generation automatically**.

### 10. Advantages of Class-Based Data Models
Using classes allows additional functionality.
Examples:
#### Getter Functions
Functions that retrieve stored values.
Example:
```
get_full_name()
```

#### Setter Functions
Functions that modify stored values.
Example:
```
set_profile_photo()
```

#### Derived Values
Some values can be computed instead of stored.
Example:
```
full_name = first_name + last_name
```

### 11. Extending Objects With New Fields
One advantage of classes is flexibility.
Suppose we want to store **hostel information** for a student.
We simply extend the class constructor:
```
Student(name, hostel)
```
and assign:
```
self.hostel = hostel
```
Older parts of the system can still work.
New objects simply include the additional field.

### 12. Problem: Memory Storage is Temporary
Python data structures exist **only in memory**.
If:
- the program stops
- the server restarts
all stored information disappears.
Therefore data must be **saved to disk**.

### 13. Object Serialization
Python provides tools to convert data structures into storable formats.
One such tool is the **pickle module**.
Serialization means:
```
Object in memory → byte representation → stored on disk
```
Later:
```
Stored data → reconstructed object
```
The object can be restored exactly as it was.

### 14. CSV and TSV File Formats
Another method for storing tabular data is text-based formats.
#### CSV
Comma Separated Values
Example:
```
Alice,Introduction to EE
Bob,Calculus
```

#### TSV
Tab Separated Values
Example:
```
Alice    Introduction to EE
Bob      Calculus
```
TSV avoids issues caused by commas appearing in text fields.

### 15. Spreadsheets and Tabular Storage
Spreadsheets represent data in tables.
Each sheet corresponds to a **table**.
Rows represent records.
Columns represent attributes.
Spreadsheets can often be **exported as CSV files**.
However, CSV has limitations:
- cannot store relationships between sheets
- limited formatting capabilities
- no advanced data logic

### 16. Limitations of Spreadsheets
Spreadsheets are convenient but have drawbacks.
#### Difficult Cross-Referencing
Looking up values across multiple sheets can become complicated.
Example:
- students sheet
- courses sheet
- enrollment sheet
Finding relationships requires complex formulas.

#### Lack of Advanced Operations
Spreadsheets do not support advanced database features.
Examples:
- stored procedures
- optimized queries
- structured relationships

#### No Atomic Operations
Databases guarantee **atomic operations**.
Meaning:
A group of changes either:
```
completes fully
OR
does not occur at all
```
This prevents partial updates.
Example problem:
Deleting a student but failing to delete related entries.
Spreadsheets do not guarantee such consistency.

### 17. Relational Databases
To address spreadsheet limitations, **relational databases** are used.
Relational databases store data in **tables**.
Each table contains:
- columns (fields)
- rows (records)
Relationships between tables are defined using **keys**.
SQL (Structured Query Language) is the standard language used to interact with relational databases.
SQL was originally developed at **IBM in the 1970s**.

### 18. Structure of Relational Databases
Relational databases require a **schema**.
Schema defines:
- table structure
- column names
- data types
Example table schema:
Students
`| ID | Name | Hostel |`
Every row must follow the same schema.

### 19. Limitations of Strict Schemas
Structured schemas can sometimes become restrictive.
Example scenario:
Students may belong to different categories.
```
Hosteller → needs mess information  
Day scholar → needs local address  
Exchange student → needs foreign university
```
A rigid schema requires columns for all possible fields.
This leads to many empty columns.

### 20. NoSQL Databases
NoSQL databases solve this issue by supporting **semi-structured data**.
Features:
- flexible schema
- different records may contain different fields
- easier to store heterogeneous data

Example:
Student A:
```
name
roll number
mess facility
```
Student B:
```
name
roll number
local address
```
Student C:
```
name
roll number
foreign university
```

### 21. Advantages of NoSQL
NoSQL systems provide:
- flexible data models
- easier schema changes
- ability to store arbitrary data
Examples of NoSQL databases:
- MongoDB
- CouchDB

### 22. Trade-offs of NoSQL
Flexibility comes with trade-offs.
Compared to relational databases:
- validation may be weaker
- queries may be slower
- data consistency may be harder to enforce

Therefore developers must choose carefully between:
- **structured relational databases**
- **flexible NoSQL databases**

### Summary
This lecture explored various mechanisms for storing application data persistently.
Key ideas:
- Python data structures can represent relationships in memory
- Keys and identifiers help avoid duplication and errors
- Classes allow structured object representations
- Data must be serialized to survive program termination
- CSV and TSV formats store tabular data
- Spreadsheets have limitations for complex data relationships
- Relational databases provide structured storage using SQL
- NoSQL databases support flexible, semi-structured data
These concepts lay the groundwork for understanding **database-backed models in modern web applications**.

### Notes to be taken for `Activity Question 2`
Nothing! Got them all correct!

---
## Lecture 3
### Relationships in Databases and ER Diagrams
##### Description: This lecture explains how databases represent relationships between different types of data. It introduces common relationship types such as one-to-one, one-to-many, and many-to-many, and explains how Entity-Relationship (ER) diagrams and Crow’s Foot notation are used to visually model database structures and relationships.

### 1. Purpose of Databases
The primary purpose of a database is to **store data**.
However, the real strength of databases lies in their ability to **represent relationships between different pieces of data**.
For example, in the Gradebook system:
- students exist
- courses exist
- relationships exist between students and courses
A database must efficiently capture these relationships.

### 2. Tabular Representation of Data
Databases typically store data in **tables**.
A table consists of:
- **columns** → represent attributes
- **rows** → represent individual records
Example: Course Table

| CourseID | CourseName                             |
| -------- | -------------------------------------- |
| EE1001   | Introduction to Electrical Engineering |
| AM1100   | Engineering Mechanics                  |
Properties:
- CourseID acts as a **unique identifier**
- CourseName describes the course

### 3. Student Table Example
Similarly, student information can be stored in another table.

| Name      | IDNumber |
| --------- | -------- |
| Student A | MAD001   |
| Student B | MAD002   |
Important characteristics:
- IDNumber is unique
- Names may repeat
Therefore the **IDNumber becomes the primary identifier**.

### 4. Relationship Table (Joining Data)
To represent which students take which courses, a **relationship table** is used.
Example:

| StudentID | CourseID | Marks |
| --------- | -------- | ----- |
| MAD001    | BT1010   | 78    |
| MAD002    | EE1001   | 65    |
Interpretation:
Student **MAD001** enrolled in **BT1010** and obtained **78 marks**.
This table connects the **students table** and the **courses table**.

### 5. Important Clarification About “Join”
The lecture mentions the word **joining tables**, but this should not be confused with SQL joins.
Two meanings exist:
Conceptual join:
- representing relationships using another table
SQL join:
- combining tables dynamically during queries
Both involve relationships but operate differently.

### 6. Types of Relationships
Databases support several types of relationships between entities.
The three main types are:
1. One-to-One
2. One-to-Many
3. Many-to-Many

### 7. One-to-One Relationship
A **one-to-one relationship** means:
Each entity in table A corresponds to exactly one entity in table B.
Example:
Student ↔ Roll Number

Properties:
- each student has one roll number
- each roll number identifies exactly one student
Another example:
Email ↔ Message ID
Each email message has a **unique message identifier**.

### 8. Example: Email Systems
Email clients like:
- Outlook
- Thunderbird
store emails with a **unique message ID**.
Properties:
- every email has exactly one ID
- each ID refers to exactly one email
This forms a **one-to-one mapping**.

### 9. One-to-Many Relationship
In a **one-to-many relationship**:
One entity corresponds to many entities in another table.

Example:
Hostel ↔ Students
- one hostel contains many students
- each student belongs to one hostel

Thus:
Hostel → many students  
Student → one hostel

### 10. Folder-Email Example
Another example appears in email systems.
Emails can be stored in folders.
Example folders:
- Work
- Courses
- Family
- Games

Properties:
- one folder contains many emails
- each email belongs to exactly one folder
This represents a **one-to-many relationship**.

### 11. Many-to-Many Relationship
A **many-to-many relationship** occurs when both entities can have multiple connections.
Example: Students and Courses
Properties:
- one student can take many courses
- one course can have many students

Therefore:
Students ↔ Courses
Many on both sides.

### 12. Gmail Label Example

Gmail uses **labels instead of folders**.
Properties:
- one email can have multiple labels
- one label can be applied to many emails

Example:
An email may have labels:
- Work
- Project
- Home
This creates a **many-to-many relationship**.

### 13. Importance of Relationship Modeling

Databases become powerful when they can:
- store entities
- represent relationships between entities
- allow efficient querying of those relationships
Without relationship modeling, databases would simply store isolated tables.

### 14. Entity-Relationship (ER) Diagrams
To visualize database structures, **ER diagrams** are used.
ER diagrams show:
- entities
- attributes
- relationships between entities
These diagrams provide a clear overview of database structure.

### 15. Crow’s Foot Notation
One popular ER diagram style is **Crow’s Foot notation**.
It represents relationship types visually.
Symbols:
Single line → one
Three branching lines → many
The three-branch symbol resembles a bird’s foot, which is why it is called **Crow’s Foot**.

### 16. Relationship Indicators
Crow’s Foot notation also indicates optionality.
Symbols may represent:
```
Exactly one  
Zero or one  
One or many  
Zero or many
```
These indicators clarify relationship constraints.

### 17. Example: E-commerce System
Consider an e-commerce system similar to Amazon.
Entities:
```
Customer  
Order  
Shipment
```
Each entity represents a different table.

### 18. Customer Entity
xample fields:
```
customer_id → Primary Key  
customer_name
```
Primary Key (PK):
- uniquely identifies each row
- cannot be NULL
- typically an integer
Primary keys ensure each record can be uniquely referenced.

### 19. Order Entity
Example fields:
```
order_id → Primary Key  
order_date  
customer_id → Foreign Key
```
Foreign Key (FK):
A field referencing another table’s primary key.
In this case:
customer_id refers to the **Customer table**.

### 20. Customer-Order Relationship
Crow’s Foot notation shows:
One order → exactly one customer
Meaning:
Every order must belong to a customer.
However:
One customer → zero or many orders.
A customer might:
- place many orders
- place no orders at all

### 21. Shipment Entity
Another entity is **Shipment**.
Example fields:
```
shipment_id → Primary Key  
order_id → Foreign Key
```
This connects shipments to orders.

### 22. Order-Shipment Relationship
Relationship rules:
One shipment → exactly one order
But:
One order → zero or many shipments
Example scenario:
A customer orders 10 books.
Possible shipping outcomes:
`1 shipment (all items shipped together)`
OR
multiple shipments:
```
2 books today  
3 books tomorrow  
5 books later
```

### 23. Advantages of ER Diagrams
ER diagrams provide several benefits.
They:
- visually summarize database structure
- show relationships clearly
- help design database schemas
- assist communication between developers
Many tools can even convert ER diagrams into database schemas automatically.

### 24. Tools for Creating ER Diagrams
One recommended tool is:
`app.diagrams.net`
Features:
- open-source
- supports ER diagram templates
- easy drag-and-drop interface

However, many other tools can also be used, such as:
- PowerPoint
- Visio
- draw.io
- diagramming software

### 25. Summary
This lecture introduced how databases represent relationships between data.
Key ideas:
- databases store tabular data
- relationships connect different tables
- three major relationship types exist:
  - one-to-one
  - one-to-many
  - many-to-many
- ER diagrams visualize these relationships
- Crow’s Foot notation represents cardinality and optionality
- primary keys uniquely identify records
- foreign keys link tables together
These concepts form the basis for designing relational database schemas used in modern applications.

### Notes to be taken for `Activity Question 3`
1. In DBMS, the condition where several pieces of the same data occur in different tables and contradict each other is called Data Inconsistency. (Question: 5)
2. The Auto Increment field provides a unique number, that is generated automatically whenever a new record is inserted in the database or the table. (Question: 7)
---
## Lecture 4
### Introduction to SQL (Structured Query Language)
##### Description: This lecture introduces SQL, the language used to interact with relational databases. It explains how data is organized in relational databases, the roles of primary and foreign keys, and how SQL queries retrieve information. It also demonstrates concepts such as joins, filtering, and Cartesian products, and concludes with a summary of how models fit into the MVC architecture.

### 1. Why SQL is Important
Relational databases store data in structured tables.
However, simply storing data is not enough.
The real purpose of a database is to **retrieve and manipulate data efficiently**.
This is where **SQL (Structured Query Language)** is used.
SQL allows us to:
- search data
- filter records
- combine multiple tables
- retrieve specific information

### 2. Role of SQL in Application Development
In application development:
- databases store the data
- SQL retrieves the data

In this course, we will often use **framework wrappers** around SQL rather than writing raw SQL directly.
However, understanding SQL is still useful because it explains:
- how queries work internally
- how databases process data

### 3. Relational Databases
Relational databases were developed in the **1970s at IBM**.
They are based on the idea of **tabular data**.
A relational database consists of tables.
Each table contains:
```
Rows → records  
Columns → fields
```
Example:
Students table

| ID     | Name  |
| ------ | ----- |
| MAD001 | Alice |
| MAD002 | Bob   |
Here:
- rows represent individual students
- columns represent attributes

### 4. Terminology in Relational Databases
Different terms are used to describe database structures.

| Database Term | Meaning               |
| ------------- | --------------------- |
| Row           | Record                |
| Column        | Field                 |
| Table         | Collection of records |

### 5. Primary Keys
Each table must contain a **primary key**.
A primary key:
- uniquely identifies a row
- ensures that no two rows are identical
- allows fast lookup
Example:
Student table

| ID     | Name  |
| ------ | ----- |
| MAD001 | Alice |
Here:
`ID` is the primary key.

### 6. Why Primary Keys Improve Performance
Primary keys make searching faster.
Without a primary key:
The system must search through all rows.
With a primary key:
The system can directly locate the row using indexing.

Example:
Searching by name requires string matching.
Searching by numeric ID is much faster.

### 7. Foreign Keys
Foreign keys connect **two tables**.
A foreign key is a field in one table that refers to the primary key of another table.
Example:
Orders table

| order_id | customer_id |
|---|---|
Here:
`customer_id` is a foreign key referencing the **customer table**.
Foreign keys allow relationships between tables.

### 8. Purpose of SQL Queries
Databases become powerful when we can query data.
Examples of queries:
Find all students whose names begin with A
Find all courses offered in 2021
Find all students who joined in 2018
Find all EE department students graduating this year
These queries allow extracting meaningful information from stored data.

### 9. Indexing
Databases often create **indexes** on fields.
Indexes improve search speed.
Common indexed fields:
- primary keys
- frequently searched columns
Indexing allows efficient lookup even in very large databases.

### 10. SQL Syntax
SQL is designed to resemble English.
Example structure:
```
SELECT column  
FROM table  
WHERE condition
```
Example:
```
SELECT name  
FROM students  
WHERE name LIKE 'A%'
```
This query finds students whose names start with A.

### 11. SQL Joins
SQL joins combine data from multiple tables.
Joins are used when related data exists across different tables.
Example:
Students table  
Hostels table
If the student table contains:
`hostel_id` we can join it with the hostel table.

### 12. Example Tables
Students table

| Name | IDNumber | HostelID |
|---|---|---|
Hostels table

| HostelID | HostelName | Capacity |
|---|---|---|
Each student references a hostel through **HostelID**.

### 13. Inner Join Example
Goal:
Find the hostel name for each student.

SQL query:
```
SELECT students.name, hostels.name  
FROM students  
INNER JOIN hostels  
ON students.hostelID = hostels.ID
```
Explanation:
1. Two tables are joined
2. The join condition matches hostel IDs
3. The result displays student names with hostel names

### 14. Result of the Join
Output might look like:

| Student | Hostel  |
| ------- | ------- |
| Alice   | Cauvery |
| Bob     | Krishna |
The database matches hostel IDs and retrieves hostel names.

### 15. SQL Joins and Performance
Joins are powerful but can be expensive.
Complex joins may slow down queries if:
- tables are large
- multiple joins are chained together
Therefore query design must be done carefully.

### 16. Cartesian Product
Another database concept is the **Cartesian product**.
If:
```
Table A has N rows  
Table B has M rows
```
The Cartesian product produces:
`N × M combinations`
Example:
3 students  
4 courses
Result:
12 combinations.

This can create extremely large datasets.
Therefore Cartesian products must be used carefully.

### 17. Example Query Problem
Consider this question:
Find all students who are taking **Calculus**.
Data structure:
```
Students table  
Courses table  
StudentCourses relationship table
```

### 18. Steps Required to Answer the Query
1. Find the course ID for Calculus
2. Find entries in the StudentCourses table with that course ID
3. Retrieve the corresponding student IDs
4. Use those IDs to retrieve student names
SQL allows all these steps to be written in a **single query**.

### 19. Example SQL Query
```
SELECT s.name  
FROM students s  
JOIN student_courses sc ON s.IDNumber = sc.studentID  
JOIN courses c ON sc.courseID = c.IDNumber  
WHERE c.name = 'Calculus'
```
Explanation:
1. Filter courses where name = Calculus
2. Match course ID with student_courses table
3. Match student IDs with students table
4. Output student names

### 20. Power of SQL Queries
SQL can express complex queries concisely.
Operations that might require multiple programming steps can often be written as **one SQL statement**.
This makes databases extremely powerful tools for data processing.

### 21. Summary of the Model Component
The **model** in MVC represents application data.
Key properties of models:
- store application data
- support persistent storage
- allow structured data representation
- support queries for retrieving information

### 22. Storage Mechanisms
Several mechanisms can store persistent data:
CSV files  
Spreadsheets  
Relational databases (SQL)  
NoSQL databases
Internally, applications may represent data using:
```
arrays  
dictionaries  
classes
```

### 23. Entities and Relationships
Data models are built around:
Entities → objects such as students or courses
Relationships → connections between entities
Example:
Students ↔ Courses
Understanding these relationships is central to database design.

### 24. Separation of Model and View
A critical concept in MVC is **separation of concerns**.
The model deals only with:
- storing data
- retrieving data

It does **not handle presentation**.
No HTML or UI logic exists inside the model.

### 25. Interaction Between MVC Components
In MVC:
View → displays data  
Controller → handles user input  
Model → stores and retrieves data

Workflow:
1. View sends user action to controller
2. Controller updates the model
3. Model updates stored data
4. View queries the model for updated information

### 26. Benefits of Model Separation
Separating models from views provides flexibility.
The same database can support:
- web applications
- desktop applications
- mobile applications
The underlying storage system can also change:
MySQL → SQLite → NoSQL
without affecting the rest of the application.

### Summary
This lecture introduced SQL and its role in relational databases.
Key ideas:
- relational databases store tabular data
- SQL retrieves and manipulates data
- primary keys uniquely identify records
- foreign keys link related tables
- joins combine information from multiple tables
- SQL queries allow complex data retrieval
- models store and manage persistent application data
- MVC architecture separates data storage from presentation
Understanding SQL and relational data models is essential for building scalable modern applications.

### Notes to be taken for `Activity Question 4`
1. The correct way to give single line comment in SQL is `--this is my comment`. (Question: 1)
2. Truncate command only deletes the data, but the schema/structure is preserved. (Question: 3)
---
[[Extra Notes from supplementary content of Week 4]]
