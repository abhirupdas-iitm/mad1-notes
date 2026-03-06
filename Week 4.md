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
1. PostgreSQL is also a relational database management systems (RDBMS). (Question: 1)
2. One of the main disadvantages of spreadsheets compared to RDBMS is a lack of the concept of an atomic operation. (Question: 3)
---
