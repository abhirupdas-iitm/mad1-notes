## Week 5 Lecture 1
### Controllers and the Concept of Taking Action
##### Description: This lecture introduces the concept of controllers in the MVC paradigm. It explores the origins of MVC, the roles of model, view, and controller, and emphasizes controllers as the component responsible for handling user actions. It also discusses limitations of MVC in web applications and highlights MVC as a conceptual framework rather than a strict rule.

### 1. Introduction to Controllers
Controllers are fundamentally about **taking action**.

They:
- respond to **user input**
- interact with the **model**
- determine what the **user sees (view)**

So the flow becomes:
User → Controller → Model → View → User
Controllers sit at the **center of interaction**.

### 2. MVC is NOT a Strict Rule
Important mindset:

- MVC is **not a fixed implementation**
- It is a **way of thinking**
- Different people interpret MVC differently

Especially in frameworks like Flask:
- Many argue Flask is **not truly MVC**
- Others adapt MVC loosely

Key takeaway:
**MVC is a conceptual framework, not a rigid structure**

### 3. Origins of MVC
MVC originated in:

- **Smalltalk-80 (around 1980)**
- Context: **GUI (Graphical User Interface) design**
- Developed by **Trygve Reenskaug**

Important implication:
- MVC was designed for **desktop applications**, NOT web apps

### 4. Core Components of MVC
#### 4.1 Model
- Represents **knowledge/data**
- Can be:
  - a single object
  - a structure of objects

Examples:
- Student data
- Courses
- Relationships (Student–Course)
- Model = **data + structure**

#### 4.2 View
- **Visual representation** of the model
- Acts as a **presentation filter**

Meaning:
- Shows only relevant data
- Hides unnecessary complexity

Example:
- Database → raw data
- View → formatted HTML page
##### Key idea:
View does NOT store data  
It only **displays** data

#### 4.3 View interacts with Model via Queries
- View gets data by **asking questions**
- Example:
  - SQL queries
  - fetching student lists

- Query = asking model for data

#### 4.4 Model Communication (Object-Oriented Insight)
- Interaction happens via **messages**
- You don’t directly manipulate data
- You **send instructions**

This comes from **Object-Oriented Programming (OOP)**:
- Encapsulation
- Controlled access

### 5. Understanding the Controller
Controller is the **most subtle component**.
#### 5.1 Definition
Controller = **link between user and system**
It:
- receives user input
- processes it
- communicates with model
- selects appropriate view

#### 5.2 Controller Responsibilities
##### 1. Provide Input to User
- Decides **what is shown**
- Arranges views on screen

Examples:
- menus
- buttons
- layout decisions
##### 2. Handle User Output
- Receives:
  - clicks
  - keystrokes
- Converts them into **actions**
##### 3. Communicate with Model
- Sends messages to model
- Retrieves or updates data
##### 4. Return Updated View
- Final output is shown to user

### 6. Important Design Rules
#### 6.1 Separation of Concerns
Strict separation:
- Model → data
- View → display
- Controller → logic/actions

#### 6.2 Controller SHOULD NOT Modify Views Directly
- Cannot create new UI elements dynamically
- Only controls **data shown in view**

#### 6.3 View SHOULD NOT Handle Input
- No direct handling of:
  - mouse clicks
  - keyboard input

Instead:
- input → controller → action

#### 6.4 User NEVER Directly Accesses Model
- No direct database manipulation
- Everything goes through controller

### 7. What is an "Action"?
Action = **core idea of controller**
An action:
- takes user input
- processes it
- interacts with model
- returns result via view

Examples:
- submit form
- fetch data
- update record

### 8. General Controller Flow
```
User Input
   ↓
Controller Action
   ↓
Model (read/update)
   ↓
View Generation
   ↓
User Output
```

### 9. MVC in GUI Applications
MVC works best in:
- desktop applications
- tightly integrated systems

Reason:
- system maintains **state**

Example:
- app knows:
  - what is on screen
  - what user can do next

### 10. Problem with MVC in Web Applications
Web introduces major changes:
#### 10.1 Stateless Nature
- Server does NOT know client state
- Between requests:
  - client may disconnect
  - restart
  - change location

- Server must treat every request independently
#### 10.2 Client-Server Separation
- Client = browser (frontend)
- Server = backend logic

They are:
- separate machines
- loosely connected
#### 10.3 MVC Assumptions Break
Original MVC assumed:
- continuous interaction
- shared state

Web reality:
- disconnected interactions
- no guaranteed state

### 11. Multiple Interpretations of MVC
Because of these differences:

- Many MVC variants exist
- No single “correct” definition

You may see:
- conflicting opinions online
- different implementations

### 12. MVC as a Conceptual Framework
Final mindset shift:

Do NOT ask:
- “Is this MVC?”
Instead ask:
- “Is my design clean?”
- “Are responsibilities separated?”

### 13. Why MVC Still Matters
Even if imperfect:
MVC helps with:
- structuring applications
- maintaining clarity
- separating responsibilities

### 14. Practical Advice
#### 14.1 Use MVC Flexibly
- Follow principles
- Don’t enforce rigid rules
#### 14.2 Adapt to Context
- Web ≠ GUI
- Adjust architecture accordingly
#### 14.3 Focus on Clarity
Goal:
- clean architecture
- understandable flow

### 15. Additional Considerations
#### 15.1 Language Differences
Example:
- ASP.NET (C#):
  - static typing
  - strict MVC structures

- Python:
  - dynamic typing
  - flexible design

- Some MVC ideas do not translate directly

### 16. Final Summary
- Controllers handle **actions**
- MVC = **conceptual design pattern**
- Model → data
- View → presentation
- Controller → logic + interaction
Key idea:
- Separation of concerns is more important than strict MVC

### 17. Core Takeaway
Controllers are about:
- responding to user actions
- coordinating between model and view
- enabling interaction in an application
MVC should be used as:
- **a way of thinking, not a rulebook**

### Notes to be taken for `Activity Question 1`
1. The controller updates the view directly in response to input from the users of the app. (Question: 4)
---
## Week 5 Lecture 2
### Requests, Responses, and the Basis of Web Interaction
##### Description: This lecture explains how web applications operate using the request-response model. It connects this model with MVC, explains how URLs encode information, and shows how user interactions translate into controller actions. It also introduces the motivation for identifying common patterns in applications, leading toward CRUD operations.

### 1. Why Requests and Responses Matter
To understand MVC in web applications, we must understand:
- **Request–Response Cycle**

Web applications are NOT continuous programs.  
They work through:
- Client → sends request  
- Server → sends response  
This is the **core foundation of the web**.

### 2. Dynamic Web Pages
Earlier web:
- Static HTML pages
- Server simply returned files

Modern web:
- Pages are **dynamically generated**
- Clicking a link can:
  - load a new page
  - trigger backend logic
  - modify data
- Clicking a link = **triggering behavior**, not just loading a page

### 3. Understanding the View in Web Context
- View = **page shown to user**
- Includes:
  - content
  - layout
  - navigation elements

Example layout:
- Header (title, navigation)
- Sidebar (links)
- Main content area
- View is still just **presentation**

### 4. Role of URLs
A URL contains structured information.
Example structure:
```
domain / path / resource
```

Components:
- **Domain** → server location
- **Path** → what is being requested
- **Resource details** → specific data

### 5. How a Request Works
When user clicks a link:
1. Browser extracts URL
2. Resolves domain → IP address
3. Sends request to server
4. Server processes request
5. Server returns response

- User does NOT care:
- which machine handled request
- how backend is structured

### 6. URLs Encode Meaning
Example interpretation:

- `/course` → request course data
- `/assessment` → request quiz/assignment
- `/unit` → specific module inside course
- URL = **instruction to server**

### 7. Controllers in Action (Real Meaning)
When user clicks:
- It triggers a **controller**
- Controller decides:
  - which model to access
  - what data to fetch/update
  - which view to render

- Controller = decision-maker

### 8. Example Flow
Click on “Assignment 0”:
1. URL changes
2. Request sent to server
3. Controller triggered
4. Controller:
   - fetches assignment data from model
   - selects appropriate view
5. Response sent back
6. User sees assignment page

### 9. Requests Are Everywhere
Every interaction:
- clicking link
- pressing button
- selecting option
- generates a request

### 10. Types of HTTP Requests
#### 10.1 GET Request
- Used for **retrieving data**
- Triggered by:
  - clicking links
  - entering URLs
- Basic operation of web
#### 10.2 POST Request
- Used for **sending data to server**
- Example:
  - form submission
Why POST?
- cleaner than encoding data in URL
- supports multiple data fields
- safer encoding

### 11. Difference: URL vs Page
Important distinction:
- You request a **URL**, not necessarily a page
- URL may:
  - return a page
  - perform backend action
  - return data only

### 12. Forms and Data Submission
Example:
User fills form:
- name
- details
Clicks submit → POST request sent
Server:
- extracts data
- processes it
- returns response

### 13. Web is Fully Request-Driven
Key principle:
- EVERYTHING is a request-response cycle
- No continuous execution
- No persistent interaction by default

### 14. Any URL Can Be Requested
Examples:

- lectures
- assignments
- quizzes
- profile info
- shopping cart

- All are just **different endpoints**

### 15. Searching for Common Patterns
Now comes an important shift:
Different systems:
- education platform
- e-commerce site
- social media
But all perform similar operations.

### 16. Example: Gradebook System
Entities:
- Students
- Courses
- Student-Course relationships

Stored as:
- tables
- structured data

### 17. Typical User Operations

User may want to:
- create student
- create course
- assign student to course
- enter/update marks
- view summaries
- delete/archive data

### 18. Recognizing the Pattern
All these actions fall into a **small set of core operations**
- This leads to:

### 19. CRUD (Coming Next)
CRUD stands for:
- Create
- Read
- Update
- Delete
These represent:
- **fundamental operations on data**

### 20. Connection to Controllers
Controllers:
- receive request
- map it to an action
- perform CRUD-like operations
- return appropriate view

### 21. Big Picture Flow
```
User Action (click / form)
        ↓
HTTP Request (GET / POST)
        ↓
Controller
        ↓
Model (data operations)
        ↓
View (rendered output)
        ↓
HTTP Response
        ↓
User sees result
```

### 22. Core Takeaways
- Web apps run on **request-response model**
- URLs carry **meaning and instructions**
- Controllers are triggered by **requests**
- GET → retrieve data
- POST → send data
- All applications share **common patterns**
- These patterns lead to **CRUD abstraction**

### 23. Key Insight
Even though applications look different:
- Course platform
- Shopping app
- Social network
- Internally, they all perform similar operations
This realization is what leads to:
- **standardization of backend logic (CRUD + Controllers)**

### Notes to be taken for `Activity Question 2`
1. Trygve Reenskaug formulated the Model-view-controller pattern. (Question: 3)
---
## Week 5 Lecture 3
### CRUD and the Data Lifecycle in Applications
##### Description: This lecture introduces CRUD (Create, Read, Update, Delete) as a fundamental abstraction for handling data. It explains how CRUD emerges from common data operations, its role in databases, and how it is adapted into web applications via APIs.

### 1. What is CRUD?
CRUD is an acronym:
- **C** → Create  
- **R** → Read  
- **U** → Update  
- **D** → Delete  
It represents:
- **the complete lifecycle of data**

### 2. Why CRUD Exists
CRUD is NOT arbitrary.
It comes from:
- years of practical experience
- repeated patterns in data handling
Observation:
- No matter the system, data operations tend to fall into these four categories

### 3. Create Operation
#### 3.1 Purpose
- Add a new object/entry to the system
Example:
- Add a new student
- Create a new course

#### 3.2 Important Constraints
- Object should **not already exist**
- Must ensure **uniqueness**
Example:
- Names may not be unique
- Use IDs for uniqueness

#### 3.3 Field Constraints
Some fields:
- mandatory (e.g., name)
- optional (e.g., phone number)
- Create = **introducing new data into system**

### 4. Read Operation
#### 4.1 Purpose
- Retrieve data from the system
#### 4.2 Types of Reads
- Single record
- List of records
- Aggregations
- Analytics
Examples:
- list all students
- compute average marks
- generate histograms
- Read = **extracting information**

### 5. Update Operation
#### 5.1 Purpose
- Modify existing data
#### 5.2 Examples
- change address
- update marks
- modify course schedule
- Update = **editing existing data**

### 6. Delete Operation
#### 6.1 Purpose
- Remove data from system
#### 6.2 Practical Use Cases
- remove outdated entries
- correct wrong entries
- clean large datasets
#### 6.3 Archiving vs Deleting
Instead of permanent deletion:
- move data to archive
- store in separate tables/database
Reason:
- improves performance
- reduces database size
- Delete = **removing or offloading data**

### 7. CRUD as a Lifecycle
Complete flow:
```
Create → Read → Update → Delete
```
This represents:
- **entire lifecycle of any data entity**

### 8. CRUD is NOT Web-Specific
Important clarification:
- CRUD originated in **databases**
- NOT originally designed for web
#### 8.1 Why It Fits the Web
Web apps:
- heavily data-driven
- require same operations
👉 Hence CRUD is adapted into web systems

### 9. Database Optimization and CRUD
Different systems emphasize different operations:
#### 9.1 Read-Heavy Systems
Examples:
- analytics platforms
- reporting systems
Characteristics:
- frequent reads
- minimal writes
#### 9.2 Write-Heavy Systems
Examples:
- logging systems
- monitoring systems
Characteristics:
- continuous data insertion
- rare reads
- CRUD helps understand system behavior

### 10. From CRUD to APIs
CRUD is often implemented via:
- **APIs (Application Programming Interfaces)**

### 11. What is an API?
API defines:
- how to communicate with a system
- how to request services
- what responses look like
#### 11.1 General Meaning
API is NOT limited to web:
Example:
- C library API
- function calls to interact with system
#### 11.2 Web API
In web context:
- communication via **HTTP**
- client ↔ server interaction

### 12. Communication Models
#### 12.1 Traditional (C Program)
- function calls
- direct linking with libraries
#### 12.2 Web-Based
- HTTP requests
- remote communication

- Difference:
- local vs network communication

### 13. API Abstraction
Key benefit:
- Client does NOT need to know implementation
Example:
 database type irrelevant
  - MySQL
  - PostgreSQL
  - MongoDB
As long as:
- request format is correct
- response format is expected

### 14. API Responsibilities
API defines:
1. How to send requests  
2. What data format to use  
3. What response will be returned  

### 15. CRUD as an API Design Pattern
CRUD naturally maps to APIs:
- Create → request to add data
- Read → request to fetch data
- Update → request to modify data
- Delete → request to remove data
- CRUD = **foundation of most web APIs**

### 16. CRUD and Controllers
Controllers:
- receive API requests
- determine CRUD operation
- interact with model
- return response

### 17. Example Mapping
```
User Action → Controller → CRUD Operation → Model → Response
```

### 18. Why CRUD is Powerful
- simple abstraction
- universally applicable
- reduces design complexity
- standardizes backend logic

### 19. Limitations of CRUD
CRUD only handles:
- data lifecycle
It does NOT handle:
- complex workflows
- advanced logic
- business rules
- Additional control logic may be required

### 20. Final Takeaways
- CRUD = core data operations
- Applies to ALL data-driven systems
- Not web-specific, but widely used in web
- Forms the basis of APIs
- Helps structure backend design

### 21. Core Insight
No matter how complex an application is:
- At its core, it is mostly doing:
- creating data  
- reading data  
- updating data  
- deleting data  
Everything else builds on top of this.

### Notes to be taken for `Activity Question 3`
1. Security archive logs can be considered as a ‘write-heavy’ operation. (Question: 3)
2. The MVC design pattern was originally designed for GUI applications. (Question: 5)
---
## Week 5 Lecture 4
### What Exactly is a Controller? Actions, Controllers, and API Design
##### Description: This lecture clarifies the concept of a controller in web applications. It connects controllers with actions, shows how actions are grouped, explains resource controllers (with examples), and discusses best practices for clean architecture including separation of concerns and API design using HTTP methods.

### 1. The Core Question: What is a Controller?
So far, we have seen:
- requests and responses  
- actions  
- CRUD  
- APIs  
But the key question remains:
- **What exactly is a controller?**

### 2. Start with Actions
The simplest way to understand controllers is:
- **Controller = organized collection of actions**
#### 2.1 What is an Action?
An action is:
- something the user requests the server to do  
- may or may not modify data  

Examples:
- Create a record  
- Fetch data  
- Update information  
- Delete entry  
#### 2.2 Beyond CRUD Actions
Not all actions are CRUD.
Examples:
- send email  
- write logs  
- trigger alerts (WhatsApp, Telegram)  
- validate quiz answer  
- request extra time  
- These are **side actions**, not strictly CRUD

### 3. From Actions to Controllers
Now the key idea:
- If multiple actions are **logically related**, group them → Controller
#### 3.1 Example
If we have actions related to "Photos":
- create photo  
- store photo  
- display photo  
- edit photo  
- delete photo  
- All grouped → **PhotoController**
#### 3.2 Important Insight
- Controller = grouping of related actions  
- Action = individual operation  
- In practice:
Controller ≈ set of actions

### 4. Example: Resource Controller (Laravel)
Frameworks provide **predefined controllers**.
Example: Resource Controller for "photos"
#### 4.1 Common Actions Provided
##### 1. Index
```
GET /photos
```
- List all photos
##### 2. Create
```
GET /photos/create
```
- Prepare to create new photo
- Usually returns a form
##### 3. Store
```
POST /photos
```
- Save photo to database
- Includes file upload + metadata
##### 4. Show
```
GET /photos/{id}
```

- Display specific photo
##### 5. Edit
```
GET /photos/{id}/edit
```
- Load form to edit photo
##### 6. Update
```
PUT/PATCH /photos/{id}
```
- Modify existing photo
##### 7. Delete
```
DELETE /photos/{id}
```
- Remove photo

### 5. Subtle Difference: Create vs Store
Important distinction:
- **Create** → prepares object (form / memory state)
- **Store** → actually saves data in database

- Create = setup  
- Store = commit

### 6. Role of HTTP Verbs
HTTP methods (verbs):
- GET  
- POST  
- PUT  
- PATCH  
- DELETE  
#### 6.1 Meaning of Verbs
- GET → retrieve data  
- POST → send data  
- PUT/PATCH → update  
- DELETE → remove  
#### 6.2 Important Insight
- HTTP does NOT enforce meaning strictly
You *could*:
- use GET to delete data  
- use POST to retrieve data  
As long as:
- client and server agree on behavior

### 7. Controller Execution Flow
When a request is made:
1. URL is invoked  
2. Controller is triggered  
3. Controller performs action  
4. Model is accessed/modified  
5. View is selected  
6. Response sent back  

### 8. Controllers Decide Views
Key role:
- Controller decides **which view to return**
Examples:
- success message  
- error message  
- data display page  

### 9. Controllers and Models
Controllers:
- interact with models  
- do NOT directly handle database logic  

### 10. Controllers and APIs
When actions are grouped:
- They form an **API**
API = structured way to:
- request actions  
- receive responses  

### 11. Everything Runs via HTTP
Important constraint:
- All interaction happens through HTTP
- no direct function calls  
- no shared memory  

### 12. Design Rules (Rules of Thumb)
#### 12.1 Separation of Concerns
- Model → data  
- View → presentation  
- Controller → actions  
#### 12.2 Model Independence
Views should NOT depend on model implementation
Example:
- changing database → should NOT break views
#### 12.3 View Independence
Model should NOT know about views
Example:
- mobile vs desktop display → model unchanged
#### 12.4 Controller–Model Interaction Rule
Controllers should NOT directly query database
Wrong:
```
controller → SQL query
```
Correct:
```
controller → model → database
```
#### 12.5 ORM Role
ORM (e.g., SQLAlchemy):
- abstracts database layer  
- keeps model independent  
- ensures clean architecture  

### 13. Controller–View Relationship
Unlike model:
Controller and view are more tightly coupled
Reason:
- controller must decide:
  - which view to render  
  - what data to send  

### 14. Flexibility Over Strictness
Important mindset:
Do NOT follow MVC rigidly
If strict separation:
- makes system complex  
- reduces clarity  
Then:
- adapt the design

### 15. Final Summary
- Controller = collection of related actions  
- Actions = operations triggered by user  
- Controllers coordinate:
  - requests  
  - models  
  - views  

### 16. Core Takeaways
- Think in terms of **actions first**
- Group actions → controller  
- Use controllers to build APIs  
- Maintain separation of concerns  
- Avoid direct DB access in controllers  
- Be flexible with MVC

### 17. Ultimate Insight
MVC is not about strict rules.
- It is about:
- clean thinking  
- structured design  
- logical separation  
Controllers are simply:
**the bridge between user actions and system behavior**

### Notes to be taken for `Activity Question 4`
1. URN is a subset of URI and URI is a superset of URN and URL. (Question: 1)
2. For the Laravel PHP framework, *POST* is used to store an image in the database. (Question: 4)
---
## Week 5 Lecture 5
### Controllers in Practice: Routing, HTTP Mapping, and Flask Implementation
##### Description: This lecture explains how controllers are actually implemented in web applications using routing. It covers stateless client-server architecture, HTTP request structure, Flask routing via decorators, dynamic URL mapping, and best practices for secure and clean application design.

### 1. Controllers in Practice → Routes
So far:
- controllers = actions  
- actions = server operations  
Now the key question:
**How are controllers actually implemented?**
Answer: **Routes**

### 2. Stateless Nature of Web Applications
Web apps follow:
**Client–Server Model**
#### 2.1 What does "Stateless" mean?
- Server does NOT remember client state  
- Every request is independent  
#### 2.2 Example
- You open a page  
- Connection drops  
- Server has NO idea:
  - what page you were on  
  - what you were doing  
Next request = completely new interaction
#### 2.3 Design Implication
Server must:
- respond without assumptions  
- handle incomplete workflows gracefully  
#### 2.4 Bad Design Example
- user fills half form  
- refresh breaks system  
Not acceptable  
#### 2.5 Good Design
- system recovers cleanly  
- user can restart safely  

### 3. HTTP Protocol Basics
All communication happens via:
**HTTP (text-based protocol)**
#### 3.1 Structure of a Request
```
<HTTP VERB> + <URL>
```
#### 3.2 Meaning of Components
##### Verb → WHAT action
- GET → fetch  
- POST → submit  
- etc.
##### URL → WHERE action
- identifies resource  
- provides context  
#### 3.3 Key Insight
Web apps = mapping:
```
(verb + URL) → action
```

### 4. Need for Routing
We must map:
URL → Controller (function)
#### 4.1 Core Idea
```
Request → Route → Function → Response
```

### 5. Flask Routing Mechanism
Flask uses:
**Decorators**

### 6. Python Decorators (Concept)
A decorator:
- wraps a function  
- adds extra functionality  
#### 6.1 Conceptual View
```
@decorator
def function():
    ...
```
Means:
```
function = decorator(function)
```
#### 6.2 Purpose
- modify behavior  
- add logic before/after function  

### 7. Flask Route Decorator
Example:
```
@app.route("/")
def home():
    return "Hello World"
```
#### 7.1 What Happens Internally
Flask builds mapping:
```
"/" → home()
```
#### 7.2 Execution Flow
```
GET / → home() → "Hello World"
```

### 8. Route Mapping in Flask
Flask creates a **routing table**:

| URL | Function |
|-----|----------|
| /   | home()   |

### 9. Method-Based Routing
Example:
```
@app.route("/", methods=["GET"])
def index():
    ...
```
#### 9.1 Important Behavior
- Only GET allowed  
- POST → error  
#### 9.2 Why?
Security + clarity

### 10. Multiple Routes
Example:
```
@app.route("/create", methods=["POST"])
def store():
    ...
```
Mapping:
```
POST /create → store()
```

### 11. Dynamic Routing (Very Important)
Example:
```
@app.route("/<int:user_id>")
def show(user_id):
    ...
```
#### 11.1 Meaning
- URL contains variable  
- Flask extracts value  
#### 11.2 Example
```
GET /42 → show(42)
```

### 12. Advanced Routing
Example:
```
@app.route("/<int:user_id>/edit", methods=["POST"])
def update(user_id):
    ...
```
#### 12.1 Behavior
```
POST /42/edit → update(42)
```

### 13. Same Route, Different Methods
Example:
```
GET /<id> → show()
DELETE /<id> → destroy()
```
#### 13.1 Meaning
Same URL → different action based on method

### 14. Routing Summary
Routing defines:
**Which function runs for which request**

### 15. Security Considerations
- Critical point
#### 15.1 Dangerous Case
```
GET /delete → deletes everything
```
❌ Very bad
#### 15.2 Required Safeguards
- authentication  
- tokens  
- validation  
#### 15.3 Goal
Prevent unauthorized actions

### 16. Controllers = Routed Functions
In Flask:
- Controller = Python function  
- Route = entry point  

### 17. Mapping Summary
```
URL + Method → Route → Function → Model → View → Response
```

### 18. Flask and MVC
Important clarification:
Flask is NOT strictly MVC
#### 18.1 Why?
- no enforced structure  
- flexible design  
#### 18.2 But can implement MVC ideas
- models → SQLAlchemy  
- views → templates  
- controllers → routes/functions  

### 19. Separation of Concerns (Again)
Very important:
- model → data  
- view → presentation  
- controller → logic  

### 20. Why Separation Matters
- prevents bad data modification  
- improves maintainability  
- ensures consistency  

### 21. Power of Flask
Flask is:
- simple  
- flexible  
- lightweight  
#### 21.1 Advantages
- minimal restrictions  
- supports clean design  
- scalable with proper structure  

### 22. Final Takeaways
- Controllers implemented via **routes**
- Web is **stateless**
- Routing maps:

  ```
  request → function
  ```
- Flask uses **decorators** for routing  
- Supports **dynamic URLs**  
- Must ensure **security**  
- MVC = mindset, not strict rule  

### 23. Final Insight
A well-designed system:
- clean routing  
- clear separation  
- secure actions  
- predictable behavior  
That’s what makes a web app robust.

### Notes to be taken for `Activity Question 5`
1. 5000 is the default port of Flask. (Question: 3)
---
[[Extra Notes from supplementary content of Week 5]]
