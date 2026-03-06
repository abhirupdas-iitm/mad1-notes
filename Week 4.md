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
