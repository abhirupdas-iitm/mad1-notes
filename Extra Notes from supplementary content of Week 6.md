### Week 6 Extra Lecture 1  
#### Documenting REST APIs using OpenAPI Specification  
##### Description: Explains how to document RESTful APIs using OpenAPI (Swagger). Covers structure of API documentation, YAML format, endpoints, parameters, responses, and tools for visualization and testing.

### 1. What is OpenAPI Specification?
OpenAPI Specification (OAS) is a **machine-readable format** for describing RESTful APIs. :contentReference[oaicite:0]{index=0}  
Key purposes:
- Document APIs  
- Share API structure with developers  
- Enable machines to consume API definitions  
- Generate client/server code automatically  

Previously known as:
- Swagger Specification  

Formats:
- JSON  
- YAML  

### 2. Why API Documentation is Important
API documentation helps:
- Developers implement APIs (server-side)  
- Clients consume APIs (frontend/mobile)  

Benefits:
- No need to ask backend developers repeatedly  
- Clear input/output definition  
- Standardized communication  
- Faster development  

### 3. Structure of OpenAPI Documentation
OpenAPI documentation includes:
- API title and description  
- Version information  
- Server details  
- Authentication methods  
- Endpoints (paths)  
- Request parameters  
- Response formats  
- Error codes  

### 4. Example: Real API (CoWIN)
A real-world API example includes:
- Base URL (server)  
- Endpoint path  
- HTTP method (GET/POST)  
- Request body (JSON)  
- Response codes  

Example structure:
- POST request → generate OTP  
- Input → mobile number (JSON)  
- Output → transaction ID  

Response codes:
- 200 → Success  
- 400 → Bad request  
- 401 → Unauthorized  
- 500 → Server error  

### 5. Machine-Readable API Definition
The actual API definition is written in:
- YAML or JSON  

Contains:
- Metadata (title, version)  
- Paths and operations  
- Parameters and schemas  

This file is:
- Source of truth  
- Used to generate UI documentation  

### 6. YAML-Based API Description
YAML file defines:
- API metadata  
- Endpoints  
- Parameters  
- Responses  

Example elements:
- `openapi: 3.0.0`  
- `info:` → title, description  
- `servers:` → base URLs  
- `paths:` → endpoints  

### 7. Designing an API (User Example)
Example database:
- user_id (auto-generated)  
- username  
- email  

API is designed before implementation:
- First → document  
- Then → build  

### 8. Adding Top-Level Information
Includes:
- API name  
- Description  
- Version  

Optional:
- Diagrams (via tools like Mermaid)  
- Tables for schema explanation  
- Error code tables  

### 9. Defining Servers
Specify where API is hosted:
- Local server → `127.0.0.1:5000`  
- Multiple servers can be defined  

### 10. Defining API Paths
Paths represent endpoints:
Example:
- `/api/user/{username}`  

Includes:
- Description  
- Parameters  
- Required fields  

### 11. Parameters in API
Parameters define inputs:
- Path parameters  
- Query parameters  
- Request body  

Example:
- username → string  
- required → true  

### 12. API Responses
Defines output structure:
- Success response  
- Error responses  

Example success:
- user_id  
- username  
- email  

Error responses:
- 400 → Bad request  
- 404 → Not found  
- 500 → Server error  

### 13. CRUD Mapping in API
Different HTTP methods:

GET:
- Retrieve user  

PUT:
- Update user  
- Example → update email  

DELETE:
- Delete user  
- Constraints may apply  

POST:
- Create user  
- Input → username + email  
- Response → 201 Created  

### 14. Error Handling in APIs
Errors include:
- Duplicate username  
- Duplicate email  
- Invalid input  

Returned as:
- JSON object  
- error_code  
- error_message  

### 15. Constraints and Relationships
Example:
- User cannot be deleted if linked to articles  

Requires:
- Delete dependent records first  

### 16. API Documentation Usage
Two main scenarios:

1. API Implementation:
- Developer receives YAML  
- Builds backend accordingly  

2. API Consumption:
- Client reads documentation  
- Uses API directly  

### 17. Tools for Writing OpenAPI
Manual:
- Write YAML/JSON  

Tools:
- Swagger Editor (web-based)  

Features:
- Live preview  
- Auto-render documentation  

### 18. Tools for Viewing API Docs
Popular tools:
- Swagger UI  
- RapidDoc  
- ReDoc  

Function:
- Convert YAML → interactive UI  

### 19. Testing APIs with Tools
Tools like:
- Insomnia  

Features:
- Send requests  
- Auto-fill parameters  
- Debug APIs  

Capabilities:
- Test endpoints  
- View responses  
- Validate API behavior  

### 20. API Exploration Platforms
Examples:
- API Setu  

Used for:
- Discovering public APIs  
- Learning API structures  

### 21. Workflow of API Development
Typical flow:

1. Design API  
2. Write OpenAPI documentation  
3. Implement backend  
4. Test using tools  
5. Share documentation  

### 22. Key Takeaways
- OpenAPI standardizes API documentation  
- YAML/JSON used for machine-readable definitions  
- Enables automation and collaboration  
- Tools simplify writing, testing, and visualization  
- Essential for scalable API development  
---
### Week 6 Extra Lecture 2  
#### Building a RESTful API using Flask + SQLAlchemy  
##### Description: Covers building a REST API using Flask-RESTful. Includes API design using documentation, routing, request handling, CRUD implementation, validation, error handling, marshalling responses, and database integration with SQLAlchemy.

### 1. Introduction to RESTful API Development
REST API = Interface for communication between client and server using HTTP.  
Uses standard HTTP methods:
- GET → retrieve data  
- POST → create data  
- PUT → update data  
- DELETE → remove data  

APIs are usually designed **before implementation** using documentation.

### 2. Importance of API Documentation
Always start with API documentation:
- Defines endpoints  
- Specifies input format  
- Specifies output format  
- Defines error responses  

Example:
- `/api/user/<username>` → GET, PUT, DELETE  
- `/api/user` → POST  

Prevents:
- Wrong implementation  
- Miscommunication between teams  

### 3. Project Setup
Tools required:
- Browser  
- Text editor / IDE  
- Terminal  
- API testing tool (e.g., Insomnia)  

Environment setup:
- Virtual environment  
- `requirements.txt` updated  

Install:
- `flask-restful`  

Run project:
- `local_setup.sh` → setup environment  
- `local_run.sh` → start server  

### 4. Flask-RESTful Framework
Flask-RESTful simplifies API creation.

Key components:
- `Resource` → represents an API endpoint  
- `Api` → binds API with Flask app  

Initialization:
- Import `Api`, `Resource`  
- `api = Api(app)`  

### 5. Creating API Module
Create new file:
`api.py`

Structure:
- Each model → one API class  
Example:
`UserAPI`

### 6. Resource Class Structure
Each API class extends `Resource`.

Basic methods:
- `get()`  
- `post()`  
- `put()`  
- `delete()`  

Each method handles corresponding HTTP request.

### 7. Routing (URL Mapping)
Routes map URLs → API classes.

Example:
- `/api/user`  
- `/api/user/<string:username>`  

Mapping:
- Done in main app  
- Uses `api.add_resource()`  

Behavior:
- URL parameter → passed as function argument  

### 8. Request Handling Flow
Flow:
1. Client sends request  
2. Route matches URL  
3. Corresponding method executes  
4. Database interaction happens  
5. Response returned  

### 9. Testing API Endpoints
Use API tools (Insomnia/Postman):
- Send requests  
- Verify responses  
- Debug mapping  

Initial testing:
- Return dummy values  
- Confirm routing works  

### 10. Implementing GET (Read Operation)
Goal:
- Fetch user by username  

Steps:
1. Receive username  
2. Query database  
3. Return user data  
4. Handle "not found"  

Query:
- `db.session.query(User).filter(...).first()`  

If user exists:
- Return JSON  

If not:
- Return 404  

### 11. Returning JSON Response
Basic approach:
- Manually create dictionary  

Problem:
- Hard to maintain  
- No formatting control  

Solution:
- Use **marshalling**

### 12. Marshalling (Response Formatting)
Marshalling standardizes output.

Define fields:
- `user_id` → Integer  
- `username` → String  
- `email` → String  

Use:
- `@marshal_with(fields)`  

Benefits:
- Clean output  
- Easy formatting  
- Flexible structure  

### 13. Error Handling Strategy
Types of errors:
- 404 → Not found  
- 400 → Bad request  
- 500 → Internal server error  

Avoid:
- Returning empty JSON blindly  

Use:
- Structured error responses  

### 14. Custom Exception Handling
Create custom exceptions:
- Extend `HTTPException`  

Example:
- `NotFoundError`  

Purpose:
- Standardized error handling  
- Clean responses  

### 15. Business Validation Errors
Used for input validation.

Example:
- Missing username  
- Missing email  
- Invalid email  
- Duplicate user  

Error structure:
- `error_code`  
- `error_message`  

Example:
- BE1001 → username required  
- BE1002 → email required  

### 16. Implementing POST (Create Operation)
Goal:
- Create new user  

Steps:
1. Parse input  
2. Validate fields  
3. Check duplicates  
4. Insert into database  
5. Commit transaction  
6. Return response  

### 17. Parsing Request Data
Use:
- Request parser OR JSON  

Extract:
- `username`  
- `email`  

If missing:
- Throw validation error  

### 18. Input Validation
Checks:
- Username present  
- Email present  
- Email format  

Simple validation:
- Check for `@`  

If invalid:
- Raise error  

### 19. Duplicate Check
Query database:
- Check username OR email  

If exists:
- Throw duplicate error  

Ensures:
- Data integrity  

### 20. Inserting Data into Database
Steps:
1. Create model object  
2. Add to session  
3. Commit  

Example:
- `db.session.add()`  
- `db.session.commit()`  

### 21. POST Response Handling
Two approaches:

#### 1. Minimal (as per documentation)
- Return status code `201`  
- No response body  

#### 2. Full response
- Return created object  
- Use marshalling  

Follow:
- Documentation strictly  

### 22. HTTP Status Codes
Common codes:
- 200 → success  
- 201 → created  
- 400 → bad request  
- 404 → not found  
- 500 → server error  

### 23. API Design Principles
- Follow documentation strictly  
- Keep responses consistent  
- Use standard status codes  
- Separate validation and logic  

### 24. Debugging Techniques
- Print intermediate values  
- Test each endpoint separately  
- Validate inputs manually  

### 25. Advantages of Flask-RESTful
- Simplifies routing  
- Clean class-based design  
- Easy request handling  
- Built-in marshalling support  

### 26. Key Takeaways
- API design starts with documentation  
- Resource classes map to endpoints  
- CRUD operations map to HTTP methods  
- Validation + error handling are critical  
- Marshalling ensures clean responses  
- Follow API contract strictly  
---
### Week 6 Extra Lecture 3  
#### Implementing PUT and DELETE APIs with Validation and Dependencies  
##### Description: Covers implementation of PUT (update) and DELETE operations in a REST API using Flask-RESTful and SQLAlchemy. Includes dependency checks, validation logic, database updates, and handling real-world constraints like foreign key relationships.

### 1. Overview of Remaining CRUD Operations
Previously implemented:
- GET → Read  
- POST → Create  

Remaining:
- PUT → Update  
- DELETE → Remove  

Both require:
- Validation  
- Database interaction  
- Error handling  

### 2. DELETE Operation Logic
Goal:
- Delete a user  

But with constraints:
- Cannot delete if dependencies exist  

Example:
- User has articles → cannot delete  

### 3. Handling Dependencies
Two approaches:

#### 1. Database-Level Handling
- Attempt delete  
- Catch database exception  

#### 2. Application-Level Handling (preferred here)
- Check dependencies before deletion  
- Prevent invalid operation  

Used approach:
- Query related data first  

### 4. DELETE Workflow
Steps:
1. Check if user exists  
2. Check if user has related articles  
3. If yes → throw error  
4. If no → delete user  
5. Return status  

### 5. Checking User Existence
Query:
- Fetch user by username  

If not found:
- Throw 404 error  

Same logic as GET  

### 6. Checking Related Articles
Query:
- Search articles by user  

If any article exists:
- Do not delete  

Error:
- Business validation error  

Example:
- BE1005 → cannot delete user  

### 7. Business Rule Enforcement
Rule:
- A user with articles cannot be deleted  

Reason:
- Maintain data consistency  
- Prevent orphan records  

Alternative designs:
- Cascade delete (delete articles too)  
- Force delete (not recommended)  

### 8. DELETE Implementation
Steps:
- `db.session.delete(user)`  
- `db.session.commit()`  

Response:
- Status code `200`  
- Empty body  

### 9. Debugging DELETE Issues
Common issues:
- Server not restarted  
- Query errors  
- Incorrect object handling  

Example error:
- "BaseQuery has no length"  

Fix:
- Use `.first()` instead of checking length  

### 10. Testing DELETE API
Cases:

#### Case 1: User has articles
- Expect error  

#### Case 2: User has no articles
- Delete successfully  
- Return `200`  

### 11. PUT Operation Overview
Goal:
- Update user details  

Common updates:
- Email  
- Other fields  

Not updating:
- Username (treated as identifier)  

### 12. PUT Workflow
Steps:
1. Parse input  
2. Validate input  
3. Check duplicates  
4. Check user existence  
5. Update database  
6. Return updated object  

### 13. Parsing Input for PUT
Use:
- Request parser  

Fields:
- Email only  

Reason:
- Controlled update  

### 14. Input Validation in PUT
Checks:
- Email exists  
- Email format valid  

If invalid:
- Throw business error  

### 15. Duplicate Email Check
Goal:
- Prevent duplicate email  

Query:
- Check if another user has same email  

If exists:
- Throw error  

Example:
- BE1006 → duplicate email  

### 16. Checking User Existence
Query:
- Find user by username  

If not found:
- Throw NotFoundError  

### 17. Updating User Data
Steps:
- Modify object:
  - `user.email = new_email`  
- Save:
  - `db.session.add(user)`  
  - `db.session.commit()`  

### 18. Returning Response for PUT
Return:
- Updated user object  

Use:
- Marshalling  

Ensures:
- Consistent output format  

### 19. PUT Response Example
Output:
- user_id  
- username  
- updated email  

Formatted using:
- `@marshal_with`  

### 20. Testing PUT API
Test cases:

#### Case 1: Missing email
- Error  

#### Case 2: Invalid email
- Error  

#### Case 3: Duplicate email
- Error  

#### Case 4: Non-existent user
- Error  

#### Case 5: Valid update
- Success  
- Returns updated object  

### 21. Validation Importance
Validation ensures:
- Data correctness  
- System stability  

Types:
- Input validation  
- Business validation  

### 22. Error Handling Consistency
All errors should:
- Follow same structure  
- Include:
  - error_code  
  - error_message  

Ensures:
- Predictable API behavior  

### 23. API Design Considerations
- Follow documentation strictly  
- Handle edge cases  
- Prevent invalid operations  
- Maintain consistency  

### 24. Extensibility
Possible extensions:
- Add more validations  
- Add logging  
- Add authentication  
- Add role-based access  

### 25. Real-World Considerations
- Foreign key constraints  
- Data integrity  
- Transaction safety  

### 26. Key Takeaways
- DELETE requires dependency checks  
- PUT requires careful validation  
- Always check existence before update/delete  
- Maintain consistency with API design  
- Business rules are critical in real systems  
---
