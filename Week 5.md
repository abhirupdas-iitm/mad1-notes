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
1. d
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
