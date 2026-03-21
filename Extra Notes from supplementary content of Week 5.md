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
### Week 5 Extra Lecture 2  
#### Connecting and Querying Databases using SQLAlchemy (ORM)  
##### Description: Introduces Object Relational Mapping (ORM) using SQLAlchemy. Covers connecting to SQLite database, defining models, relationships, querying data, sessions, and transactions.

### 1. What is ORM (Object Relational Mapping)?
ORM is a technique that allows interaction with databases using **object-oriented programming**.
Instead of writing SQL:
- You work with **classes and objects**
Benefits:
- Easier to use  
- More readable  
- Pythonic approach  

### 2. Popular ORM Tools in Python
- Peewee  
- Pony ORM  
- SQLAlchemy (most widely used)

### 3. SQLAlchemy Overview
SQLAlchemy provides:
- Database-agnostic interface  
- Works with multiple databases (SQLite, MySQL, PostgreSQL)  
Meaning:
Same code → can work across different databases

### 4 .Project Setup
Folder:
experiment-sqlalchemy/
Requirements:
- Python 3  
- Virtual Environment  
- SQLite database from previous lecture  
- DB Browser  

### 5. Installing SQLAlchemy
Activate virtual environment:
source bin/activate  
Install:
`pip install sqlalchemy`

### 6. Defining Models
Models represent database tables.
Steps:
1. Create Base class  
2. Define classes for each table  

### 7. Example: User Model
Table: user  
Columns:
- user_id → Integer, Primary Key, Auto Increment  
- username → String, Unique  
- email → String, Unique  
Important:
- Class name ≠ Table name  
- Table name must match database  

### 8. Example: Article Model
Table: article  
Columns:
- article_id → Primary Key  
- title  
- content  

### 9. Example: Association Table (Many-to-Many)
Table: article_authors  
Columns:
- article_id → Foreign Key  
- user_id → Foreign Key  
Properties:
- Composite Primary Key  
- Represents many-to-many relationship  

### 10. Relationships in ORM
Types:
- One-to-One  
- One-to-Many  
- Many-to-One  
- Many-to-Many  
In this case:
Article ↔ Users → Many-to-Many  
Defined using:
relationship + secondary table  

### 11. Relationship Usage
Example:
- Article has multiple authors  
- Authors are fetched automatically with article  
Access:
article.authors  

### 12. Connecting to Database (Engine)
Engine provides:
- Connection  
- Dialect  
- Connection Pool  
Create engine:
`sqlite:///./testdb.sqlite3`  
Format:
`dialect+driver://username:password@host:port/database  `
SQLite:
- No host  
- No port  

### 13. Executing Basic Query
Steps:
1. Create query (select)  
2. Get connection  
3. Execute  
4. Fetch results  
Example:
- Select all users  
- Print rows  

### 14. Using Session (Preferred Way)
Instead of raw connections → use session  
Session:
- Manages communication with DB  
- Holds objects  
- Tracks changes  
Create session:
Session(engine)  

### 15. Querying with Session
Example:
- Query article where article_id = 1  
- Fetch results  
- Access attributes  
Access related data:
`article.authors`

### 16. Example Output
- Article title  
- Author names  
Shows:
ORM automatically resolves relationships  

### 17. Filtering Data
Example:
- filter(article_id = 1)  
Multiple conditions:
- Use AND  

### 18. Joins in ORM
Supported:
- Inner Join  
- Outer Join  
- Left Join  
- Right Join  
Used for:
Combining tables  

### 19. Transactions
Transaction = unit of work  
Goal:
- Either fully complete  
- Or fully rollback  

### 20. Why Transactions?
Example:
1. Insert article  
2. Insert authors  
If step 2 fails:
→ Step 1 should also rollback  

### 21. Manual Transaction Flow
Steps:
1. Create session  
2. Add object  
3. Flush (send to DB)  
4. Perform next operations  
5. Commit  
If error:
- Rollback  

### 22. Error Handling
Structure:
- Try → Commit  
- Except → Rollback  
Ensures:
Database consistency  

### 23. Flush vs Commit
Flush:
- Sends changes to DB  
- Does not finalize  
Commit:
- Permanently saves  

### 24. Using Relationships for Insert
Instead of manual insert:
Do:
- `article.authors.append(user)`
Then:
- session.add(article)  
- session.commit()  

### 25. Advantage of ORM Relationships
- Cleaner code  
- Automatic linking  
- Less manual work  
#### Example: Multiple Authors
- Add multiple users to article  
- ORM inserts into association table automatically  

### 26. Key Concepts Covered
- ORM basics  
- Model definition  
- Relationships  
- Engine  
- Sessions  
- Queries  
- Transactions  

### 27. Important Notes
- Always match table + column names  
- Use one engine per application  
- Prefer session over raw connection  
- Use relationships instead of manual inserts  

### 28. Key Takeaways
ORM makes database interaction:
- Easier  
- Cleaner  
- Object-oriented  
Core workflow:
- Define models  
- Create engine  
- Create session  
- Query and manipulate data  
Transactions ensure:
- Data integrity  
Relationships reduce:
- Complexity  
- Boilerplate code  
Understanding these concepts prepares you to:
- Build database-driven applications  
- Integrate with web frameworks  
---
### Week 5 Extra Lecture 3
#### Flask + SQLAlchemy Integration (Building a Dynamic Web App)  
##### Description: Demonstrates integrating SQLAlchemy with Flask using Flask-SQLAlchemy. Covers project setup, database configuration, models, querying data, and rendering dynamic content using templates.

### 1. Development Environment Setup
#### 1.1 Required Tools
- Browser (Chrome / Firefox)
- IDE / Editor:
  - VS Code / VSCodium / PyCharm / Sublime / Geany / Thonny
  - OR Online IDE (Replit)
- Terminal
- File Explorer
#### 1.2 Project Structure
- Create project folder:
  ```
  experiment-flask-sqlalchemy
  ```
- Files:
  - `main.py`
  - `requirements.txt`
  - `testdb.sqlite3` (existing database)

### 2. Virtual Environment Setup
#### 2.1 Create Virtual Environment
```bash
python3 -m venv .experiment-env
```
#### 2.2 Activate Environment
```bash
source .experiment-env/bin/activate
```
#### 2.3 Verify Environment
```bash
python --version
which python
```

### 3. Installing Dependencies
#### 3.1 requirements.txt
```
flask
flask_sqlalchemy
```
#### 3.2 Install Packages
```bash
pip install -r requirements.txt
```
#### 3.3 Verify Installation
```bash
pip freeze
```

### 4. Flask + SQLAlchemy Configuration
#### 4.1 Import Required Modules
```python
from flask import Flask, render_template
from flask_sqlalchemy import SQLAlchemy
import os
```
#### 4.2 Create Flask Application
```python
app = Flask(__name__)
```
#### 4.3 Configure Database URI
- Get current directory:
```python
current_dir = os.path.abspath(os.path.dirname(__file__))
```
- Set database path:
```python
app.config['SQLALCHEMY_DATABASE_URI'] = "sqlite:///" + os.path.join(current_dir, "testdb.sqlite3")
```
#### 4.4 Initialize Database
```python
db = SQLAlchemy()
db.init_app(app)
app.app_context().push()
```

### 5. Models using Flask-SQLAlchemy
#### 5.1 Key Difference from SQLAlchemy
- All components accessed via `db`

| Standard SQLAlchemy | Flask-SQLAlchemy |
| ------------------- | ---------------- |
| Column              | db.Column        |
| Integer             | db.Integer       |
| ForeignKey          | db.ForeignKey    |
#### 5.2 Insight
- Flask-SQLAlchemy is a **wrapper over SQLAlchemy**
- Simplifies integration with Flask apps

### 6. Running the Application
```python
if __name__ == "__main__":
    app.run(debug=True, port=8080)
```

### 7. Basic Route Setup
#### 7.1 Hello World Route
```python
@app.route("/")
def home():
    return render_template("home.html")
```

### 8. Templates Setup
#### 8.1 Create Templates Folder
```
templates/
```
#### 8.2 Create Template File
```
home.html
```

### 9. Moving to Dynamic Content
#### 9.1 Goal
- Replace static content with **database-driven content**
#### 9.2 Fetch Data from Database
```python
articles = Article.query.all()
```
#### 9.3 Pass Data to Template
```python
return render_template("articles.html", articles=articles)
```
#### 9.4 Debug Output
```html
{{ articles }}
```
- Returns list of database rows (objects)

### 10. Rendering Data using Jinja
#### 10.1 Loop Through Data
```html
{% for article in articles %}
    {{ article }}
{% endfor %}
```

### 11. UI Design using Bootstrap
#### 11.1 Add Bootstrap CDN
- Include in `<head>` section
#### 11.2 Layout Structure
##### Container
```html
<div class="container">
```
#### 11.3 Page Sections
##### Header Section
- Use Bootstrap **jumbotron**
##### Main Layout
```html
<div class="row">
    <div class="col-8">
        Main Content (Articles)
    </div>
    <div class="col-4">
        Sidebar
    </div>
</div>
```
#### 11.4 Grid System
- Total width = 12
- Example:
  - Main content = 8
  - Sidebar = 4

### 12. Application Flow
1. User sends request to `/`
2. Flask route (controller) is triggered
3. Database queried:
   ```python
   Article.query.all()
   ```
4. Data passed to template
5. Template renders HTML using Jinja
6. Response sent to browser

### 13. MVC Mapping

| Component  | Role                     |
| ---------- | ------------------------ |
| Model      | Database (Article table) |
| View       | HTML template            |
| Controller | Flask route function     |

### 14. Key Takeaways
- Flask-SQLAlchemy simplifies ORM usage
- Routes act as controllers
- Templates handle presentation (views)
- Models represent database structure
- Enables full dynamic web application flow

### 15. Final Insight
- This lecture connects:
  - Flask basics
  - SQLAlchemy ORM
  - MVC architecture
- Represents a **complete request → database → response pipeline**
---
