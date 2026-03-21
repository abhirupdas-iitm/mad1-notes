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
### Week 5 Extra Lecture 4  
#### Rendering Dynamic Content, Relationships, and Filtering in Flask-SQLAlchemy  
##### Description: Focuses on displaying database content using Jinja templates, handling relationships (articles ↔ authors), formatting output, and implementing filtered queries with dynamic routing.

### 1. Rendering Articles Dynamically
#### 1.1 Iterating Over Articles
- Articles are passed from Flask:
```python
articles = Article.query.all()
```
- Use Jinja loop:
```html
{% for article in articles %}
    {{ article.title }}
    {{ article.content }}
{% endfor %}
```
#### 1.2 Problem
- Output appears in a single line
- No structure or readability

### 2. Structuring Content using HTML
#### 2.1 Wrapping Each Article
```html
<div>
    <h2>{{ article.title }}</h2>
    <div>
        {{ article.content }}
    </div>
</div>
```
#### 2.2 Benefits
- Better readability
- Easier styling later
- Logical separation of content

### 3. Displaying Article Authors (Relationships)
#### 3.1 Understanding Relationship
- Each article has:
  - **Multiple authors (list of users)**
#### 3.2 Iterating Over Authors
```html
<p>
    written by
    {% for author in article.authors %}
        {{ author.username }}
    {% endfor %}
</p>
```

### 4. Formatting Author List
#### 4.1 Problem
- Names appear without separation
#### 4.2 Naive Approach
```html
{{ author.username }},
```
- Adds comma even after last author ❌
#### 4.3 Correct Approach (Jinja Loop Condition)
```html
{% for author in article.authors %}
    {{ author.username }}{% if not loop.last %}, {% endif %}
{% endfor %}
```
#### 4.4 Key Concept
- `loop.last` → True for last element
- Avoids trailing comma

### 5. Improving UI Readability
#### 5.1 Enhancements
- Add spacing between articles
- Use separate divs
- Format text properly
#### 5.2 Optional Styling Ideas
- Background color for article blocks
- Padding and margins
- Typography improvements

### 6. Adding Meaningful Content
- Replace dummy text with real content
- Add:
  - Titles
  - Paragraphs
- Ensures layout behaves properly

### 7. Adding Dynamic Filtering (Articles by Author)
#### 7.1 Goal
- Click author name → show only their articles

### 8. Creating New Route
#### 8.1 Route Definition
```python
@app.route("/articles/<username>")
def articles_by_author(username):
```
#### 8.2 Filtering Query
```python
articles = Article.query.filter(
    Article.authors.any(username=username)
).all()
```
#### 8.3 Key Concept
- `.any()` → checks relationship
- Filters articles where:
  - Any author has given username

### 9. Rendering Filtered Results
#### 9.1 Use Separate Template
```python
return render_template("author_articles.html", articles=articles)
```
#### 9.2 Why Separate Template?
- Simpler structure
- Clear separation of concerns
- Avoids complexity

### 10. Making Author Names Clickable
#### 10.1 Convert to Link
```html
<a href="/articles/{{ author.username }}">
    {{ author.username }}
</a>
```
#### 10.2 Result
- Clicking username → triggers route
- Displays filtered articles

### 11. Passing Additional Data to Template
#### 11.1 Pass Username
```python
return render_template(
    "author_articles.html",
    articles=articles,
    username=username
)
```
#### 11.2 Use in Template
```html
<h2>Articles by {{ username }}</h2>
```

### 12. Final Application Flow
1. User visits homepage
2. Articles displayed
3. User clicks author name
4. Request sent:
   ```
   /articles/<username>
   ```
5. Flask route triggered
6. Database filtered query executed
7. Filtered articles returned
8. Template renders results

### 13. Key Concepts Covered
#### 13.1 Jinja Templating
- Loops (`for`)
- Conditions (`if`)
- Loop metadata (`loop.last`)
#### 13.2 ORM Relationships
- One-to-many / many-to-many handling
- Access related objects via attributes
#### 13.3 Dynamic Routing
- URL parameters (`<username>`)
- Passed into controller function
#### 13.4 Query Filtering
- `.filter()`
- `.any()` for relationships

### 14. Deployment on Replit
#### 14.1 Setup Steps
1. Create new Python repl
2. Install packages:
   - Flask
   - Flask-SQLAlchemy
#### 14.2 Differences from Local Setup

| Local Setup      | Replit Setup      |
| ---------------- | ----------------- |
| requirements.txt | Packages tab      |
| pip              | poetry (internal) |
#### 14.3 Upload Database
- Upload `testdb.sqlite3`
- Ensure correct path handling
#### 14.4 Run Application
- Click **Run**
- Access via generated URL

### 15. Key Takeaways
- Jinja enables dynamic rendering
- Relationships allow complex data linking
- Filtering enables dynamic views
- Routing connects user actions to logic
- Flask + SQLAlchemy = full-stack capability

### 16. Final Insight
- This lecture completes:
  - **Dynamic rendering**
  - **Relationship handling**
  - **User-driven filtering**
- Represents:
  > 🔴 Data → Query → Filter → Render → User Interaction Loop
---
### Week 5 Extra Lecture 5  
#### Structuring a Scalable Flask Project (Project Layout, Config, and Deployment)  
##### Description: Explains how to organize a Flask project into modules for scalability. Covers project structure, configuration management, environment variables, static/templates handling, and local vs deployment setup.

### 1. Why Project Structure Matters
#### 1.1 Problem with Single File Flask Apps
- Earlier approach:
  - Everything in `main.py`
  - Includes:
    - App setup
    - Models
    - Controllers
    - DB config
#### 1.2 Issues
- Hard to read
- Hard to maintain
- Difficult to scale
#### 1.3 Solution
- Break into **modules + packages**
- Follow **separation of concerns**

### 2. Project Structure Overview
```
project/
│
├── main.py
├── requirements.txt
├── application/
│   ├── __init__.py
│   ├── config.py
│   ├── controllers.py
│   ├── models.py
│   ├── database.py
│
├── templates/
├── static/
│   ├── css/
│   ├── js/
│
├── db/
│   └── testdb.sqlite3
```

### 3. Role of Each Component
#### 3.1 `main.py`
- Entry point
- Responsibilities:
  - Create app
  - Load config
  - Initialize DB
  - Run server
#### 3.2 `application/` Package
- Core logic lives here
##### a) `models.py`
- Contains all database models
- Extracted from earlier single-file app
##### b) `database.py`
- Initializes SQLAlchemy
```python
db = SQLAlchemy()
```
##### c) `controllers.py`
- Contains routes + logic
- Can be split further:
  - `article_controllers.py`
  - `user_controllers.py`
##### d) `config.py`
- Handles environment-specific settings

### 4. Configuration Management
#### 4.1 Base Config Class
```python
class Config:
    DEBUG = False
```
#### 4.2 Local Development Config
```python
class LocalDevelopmentConfig(Config):
    DEBUG = True
    SQLALCHEMY_DATABASE_URI = ...
```
#### 4.3 Production Config
```python
class ProductionConfig(Config):
    DEBUG = False
    SQLALCHEMY_DATABASE_URI = ...
```

### 5. Environment-Based Configuration
#### 5.1 Reading Environment Variable
```python
env = os.getenv("ENV", "development")
```
#### 5.2 Behavior
- If ENV not set → defaults to `development`
- If ENV = production → use production config
#### 5.3 Why This Matters
- Same code works in:
  - Local
  - Staging
  - Production

### 6. Handling Sensitive Data
#### 6.1 Problem
❌ Hardcoding passwords:
```python
PASSWORD = "mysecret"
```
#### 6.2 Correct Approach
```python
PASSWORD = os.getenv("DB_PASSWORD")
```
#### 6.3 Benefits
- Security
- No accidental leaks
- Safe for version control

### 7. Templates Organization
#### 7.1 Default Folder
```
templates/
```
#### 7.2 Best Practice
- Use subfolders if needed:
```
templates/
  ├── articles/
  ├── users/
```

### 8. Static Files Handling
#### 8.1 Default Static Folder
```
static/
```
#### 8.2 Types of Files
- CSS
- JS
- Images
#### 8.3 Example Structure
```
static/
  ├── css/style.css
  ├── js/validation.js
```
#### 8.4 Using Static Files in Template
```html
<link rel="stylesheet" href="{{ url_for('static', filename='css/style.css') }}">
```
#### 8.5 Example JS Include
```html
<script src="{{ url_for('static', filename='js/custom_validation.js') }}"></script>
```

### 9. Requirements File
#### 9.1 Purpose
- Define dependencies
#### 9.2 Example
```
Flask==2.x.x
Flask-SQLAlchemy==3.x.x
```
#### 9.3 Why Pin Versions?
- Avoid unexpected bugs
- Ensure consistency across systems

---

### 10. Virtual Environment Setup
#### 10.1 Create Environment
```bash
python -m venv .env
```
#### 10.2 Activate
```bash
source .env/bin/activate
```
#### 10.3 Install Dependencies
```bash
pip install -r requirements.txt
```

### 11. Running the Application
#### 11.1 Set Environment
```bash
export ENV=development
```
#### 11.2 Run
```bash
python main.py
```
#### 11.3 Output
- Runs on:
```
http://localhost:8080
```

### 12. Flask Development Server Warning
- Built-in server:
  - Not for production
- Production requires:
  - Gunicorn / uWSGI (not covered here)

### 13. Deployment on Replit
#### 13.1 Steps
- Create Python repl
- Install:
  - Flask
  - Flask-SQLAlchemy
#### 13.2 Add Environment Variable
- Key: `ENV`
- Value: `development`
#### 13.3 Upload Files
- Project structure same as local
- Include:
  - templates
  - static
  - db
#### 13.4 Run
- Click **Run**
- App launches automatically

### 14. Database Configuration
#### 14.1 SQLite URI Construction
```python
sqlite:///db/testdb.sqlite3
```
#### 14.2 Dynamic Path
- Use directory + filename
- Construct via config

### 15. Scaling the Project
#### 15.1 Extend Models
- Add new tables:
  - Tags
  - Categories
#### 15.2 Extend Controllers
- Add routes:
  - `/articles/tag/<tag>`
  - `/users/<id>`
#### 15.3 Modular Expansion
- Split controllers
- Use Blueprints (advanced)

### 16. Blueprints (Advanced Concept)
- Flask feature for:
  - Modular routing
- Useful for:
  - Large applications
- Not covered deeply here

### 17. Automation Scripts (Optional)
#### 17.1 Setup Script
- Automates:
  - venv creation
  - dependency install
#### 17.2 Run Script
- Automates:
  - env setup
  - running app

### 18. Key Design Principles
#### 18.1 Separation of Concerns
- Models → data
- Controllers → logic
- Templates → view
#### 18.2 Maintainability
- Easier debugging
- Easier collaboration
#### 18.3 Scalability
- Supports growth
- Clean architecture

### 19. Final Insight
- Flask does NOT enforce structure  
- You must design it thoughtfully  
> 🔵 Clean structure = scalable system  
> 🔴 Messy structure = technical debt

### 20. Summary Flow
1. Create modular structure  
2. Define config classes  
3. Use environment variables  
4. Organize templates + static  
5. Setup DB + models  
6. Run via main.py  
7. Scale gradually  
---
