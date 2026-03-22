### Week 6 Lecture 1
#### REST and APIs – Introduction and Web Architecture  
##### Description: Introduces APIs and REST (Representational State Transfer), explains distributed web architecture, and covers REST constraints including client-server, statelessness, layered systems, cache-ability, uniform interface, and code-on-demand.

### 1. Introduction to APIs and REST
- Focus shifts from MVC and web basics → **Application Programming Interfaces (APIs)**
- Key concept: **REST (Representational State Transfer)**
- REST is crucial for:
  - Understanding how web applications work
  - Designing scalable web architectures
- Topics covered:
  - Web architecture
  - REST concepts
  - API examples
  - `OpenAPI` specification

### 2. Web as a Distributed Architecture
- Web applications are inherently **distributed systems**
  - Client and server are usually on different machines
- Requires **standard communication protocols**
  - Client sends request → Server sends response
- Possible assumptions in general distributed systems:
  - Server always running
  - Server knows client state
  - Authentication always enforced
  - Low network latency

### 3. Characteristics of the Web
- Client and server can be:
  - Geographically far apart (even across continents)
- Network variability:
  - Different networks (mobile, broadband, office)
  - Different latency, speed, reliability
- Authentication:
  - Not part of original web design
  - Added later (login systems)
- **State uncertainty:**
  - Server does NOT know:
    - If client received response
    - What user is doing
  - Client does NOT know:
    - Server state
    - Server identity (exact machine)
    - Server uptime/status

### 4. Origin of REST
- Introduced by **Roy Fielding (2000, UC Irvine PhD thesis)**
- Based on:
  - Limitations of the web
  - Need for scalable architecture
- REST is:
  - A **software architecture style**
  - NOT strict rules
  - A set of **guidelines/constraints**

### 5. REST Constraints
#### 5.1 Client–Server Architecture
- Separation of concerns:
  - **Client:**
    - User interaction
    - Requests data
  - **Server:**
    - Stores data
    - Processes requests

- Communication via network
#### 5.2 Statelessness
- No shared state between client and server
- Server does NOT know:
  - Client history
  - Current page/user actions
- Client does NOT know:
  - Server condition
  - Whether same server handled previous request
- Each request must be:
  - **Independent**
  - **Self-contained**
#### 5.3 Layered System
- System may have multiple layers:
  - Load balancer (proxy frontend)
  - Middleware (authentication)
  - Backend servers (actual logic)
- Example flow:
  - Client → Load balancer → Middleware → Backend
- Key idea:
  - Client does NOT know:
    - Which layer responded
    - How many layers exist
- Benefits:
  - Scalability
  - Flexibility
  - Modularity
#### 5.4 Cacheability
- Responses can be cached to improve performance
- Example:
  - Static pages (e.g., homepage)
- Cache can exist at:
  - Proxy/frontend
  - Client-side
- Controlled via:
  - Response metadata (e.g., cache expiry)
- Goal:
  - Reduce unnecessary server load
  - Faster responses
#### 5.5 Uniform Interface
- Client-server interaction should be:
  - Consistent
  - Predictable
- Server exposes **resources**
  - Example:
    - Products
    - Shopping cart
- Operations are standardized:
  - Add item
  - Remove item
  - View item
- Discoverability:
  - Client learns available actions via responses (hypertext)
#### 5.6 Code on Demand (Optional)
- Server can extend client functionality
- Examples:
  - JavaScript
  - (Earlier) Java applets
- Allows:
  - Offloading computation to client

### 6. Key Takeaways
- REST is:
  - A **design philosophy**, not strict rules
- Built on constraints:
  - Client-server
  - Statelessness
  - Layered system
  - Cacheability
  - Uniform interface
  - Code-on-demand (optional)
- Goal:
  - Design systems suited for the **real-world web environment**

### Notes to be taken for `Activity Question 1`
1. REST is *not* an API. (Question: 5)
---
### Week 6 Lecture 2  
#### REST – Deep Dive, HTTP Methods, Idempotency, and Data Encoding  
##### Description: Explains the meaning of Representational State Transfer, how REST communication works, mapping HTTP methods to actions, idempotency, relation between REST and CRUD, and data encoding formats like JSON, XML, and YAML.

### 1. What is Representational State Transfer (REST)?
- REST = **Representational State Transfer**
- Meaning:
  - Interaction between **client and server has a “state”**
  - That state must be:
    - **Transferred back and forth**
    - In a **standardized representation format**
- Example (Shopping Cart):
  - State = items in cart, actions (add/remove)
  - Server stores full state
  - Client sends **action-specific state info**
  - Server responds with updated representation
- Key idea:
  - Not entire data → only **relevant interaction state**

### 2. REST Communication Flow
1. Client accesses a **Resource Identifier**
   - Typically a **URI (Uniform Resource Identifier)**
   - URL ⊂ URI
1. Client specifies an **operation**
   - Example:
     - Read
     - Create
     - Update
     - Delete
1. Server:
   - Interprets request
   - Performs action
   - Returns **new representation**
1. Client:
   - Uses response
   - Decides next action

### 3. URI vs URL
- **URL (Uniform Resource Locator):**
  - Web address (browser)
- **URI (Uniform Resource Identifier):**
  - More general
  - Includes:
    - Protocol
    - Resource identification

### 4. REST and Statelessness
- Server:
  - Only processes **current request**
  - Cannot assume:
    - Previous state
    - User context
- Additional data (like cookies):
  - Must be included in request
- Each request must contain:
  - Enough information to be processed independently

### 5. HTTP as REST Implementation
- REST is **not tied to HTTP**
- HTTP is the most common implementation
- HTTP methods (verbs):
- GET → Retrieve  
- POST → Send data  
- PUT → Create/replace  
- DELETE → Remove  

### 6. Mapping HTTP Methods to REST Actions
- **GET**
  - Retrieve resource
  - Read-only
- **POST**
  - Send data to server
  - Create/update
- **PUT**
  - Create resource with fixed identity
  - Overwrites if exists
- **DELETE**
  - Remove resource

### 7. Idempotent Operations
- Definition:
  - Repeating operation multiple times → **same effect**
#### 7.1 Idempotent Methods
- **GET**
  - Safe (read-only)
- **PUT**
  - Same object → no duplicates
- **DELETE**
  - Repeated delete → no further effect
#### 7.2 Non-Idempotent Method
- **POST**
  - Can create duplicates
- Example:
  - Clicking submit multiple times → duplicate entries
#### 7.3 Practical Importance
- Users may:
  - Click repeatedly
  - Retry requests
- Must handle carefully:
  - Avoid duplicate payments
  - Prevent repeated actions

### 8. REST vs CRUD
- **CRUD**
  - Database operations
- **REST**
  - Web architecture
- Relationship:
  - REST is used to implement CRUD
  - But they are **not the same**

### 9. Data Encoding in REST
- Traditional:
  - HTML (for humans)
- REST:
  - Machine-readable data
- Purpose:
  - Separate:
    - Data (Model)
    - Presentation (View)

### 10. Data Formats
#### 10.1 XML (Extensible Markup Language)
- Structured
- Strict
- Verbose
#### 10.2 JSON (JavaScript Object Notation)
- Most widely used
- Features:
  - Lightweight
  - Human-readable
  - Easy to parse
#### 10.3 JSON Structure
- Key-value format (like Python dict)
Example:
```
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 27,
  "address": {
    "streetAddress": "...",
    "postalCode": "..."
  },
  "phoneNumbers": [
    {"type": "home", "number": "..."},
    {"type": "work", "number": "..."}
  ]
}
```
- Supports:
  - Strings
  - Numbers
  - Nested objects
  - Arrays

### 11. Serialization
- Convert:
  - Complex data → string format
- Purpose:
  - Network transfer
  - Storage
  - Interoperability

### 12. Role of JSON in MVC
- Model → returns JSON  
- Controller → processes data  
- View → renders output  
- Key idea:
  - Controller deals with **data, not HTML**

### 13. YAML (Yet Another Markup Language)
- Alternative to JSON
- Used for:
  - Configuration
  - Documentation
- Common in:
  - `OpenAPI` specs

### 14. Key Takeaways
- REST:
  - Transfers **state as representations**
- HTTP:
  - Implements REST using verbs
- Idempotency:
  - Critical for reliability
- REST ≠ CRUD:
  - Different layers
- JSON:
  - Standard data format
- Core principle:
  - **Separation of concerns**

### Notes to be taken for `Activity Question 2`
1. The information on cache is solely controlled by the server. (Question: 1)
2. POST is not always idempotent. (Question: 4)
---
### Week 6 Lecture 3  
#### REST in Practice – APIs, Real-World Examples, and Documentation  
##### Description: Explains how REST is implemented in real systems using APIs. Covers practical examples like Wikipedia API, how requests and responses work using tools like curl, JSON responses, API documentation structure, schemas, parameters, and error handling.

### 1. From Theory to Practice (REST Implementation)
- REST is not just theoretical → used in real systems  
- Used for:
  - CRUD operations (data management)
  - System-level actions (e.g., reboot VM)
  - Control systems (e.g., smart city lights)
- Core idea:
  - REST defines how data/state is transferred
  - Controller + View decide how it is presented

### 2. REST Beyond CRUD
- REST is NOT limited to database operations  
Examples:
- Cloud APIs:
  - Create VM
  - Reboot VM
- Smart systems:
  - Turn lights ON/OFF
  - Check system state  
- Insight:
  - REST = general-purpose interaction system
  - Not just data manipulation

### 3. Why APIs Are Needed
- Direct DB access:
  - Unsafe
  - Not scalable
  - Not available to users  
- API provides:
  - Controlled access
  - Structured communication
  - Automation capability

### 4. Example: Wikipedia REST API
- Public API  
- Allows:
  - Searching pages
  - Fetching history
  - Extracting structured data

### 5. API Request Structure
`Example URL: https://en.wikipedia.org/w/rest.php/v1/search/page?q=earth&limit=1  `
Breakdown:
- Domain → en.wikipedia.org  
- REST endpoint → /w/rest.php  
- Version → /v1  
- Resource → /search/page  
- Parameters:
  - q=earth  
  - limit=1  

### 6. API Versioning
- Example: v1  
- Purpose:
  - Prevent breaking existing systems  
  - Allow upgrades safely  
- Rule:
  - Breaking change ⇒ new version  

### 7. Using curl
- Command-line HTTP client  
Example: curl `<URL>`
- Default method: GET  
- Sends request → receives response  

### 8. JSON Response Example
Example response:
```
{  
  "pages": [  
    {  
      "id": 9228,  
      "title": "Earth",  
      "excerpt": "...",  
      "description": "Third planet from the Sun",  
      "thumbnail": {...}  
    }  
  ]  
}
```

### 9. Understanding JSON Response
- pages → array  
- each element → object  
Fields:
- id → unique identifier  
- title → readable name  
- excerpt → partial HTML content  
- description → metadata  
- thumbnail → image info  

### 10. JSON as Data Structure
- Equivalent to Python dictionary  
- Supports:
  - nested objects  
  - arrays  
  - key-value pairs  
- Advantage:
  - easy parsing  
  - structured access  

### 11. Page History API
- Returns revision data  
Each revision:
- id  
- timestamp  
- size  
- author  
- comment  

### 12. API Use Cases
- Build scripts to:
  - track edits  
  - analyze changes  
  - monitor contributors  
- Advantage:
  - no need to parse HTML manually  

### 13. Responsible API Usage
- APIs = public resources  
Rules:
- limit request rate  
- avoid spamming  
- avoid automation abuse  
- Risk:
  - IP blocking  

### 14. API Documentation Structure
#### 14.1 Schema
- defines data structure  
Examples:
- id → integer  
- title → string  
- description → string/null  
#### 14.2 Route
- endpoint path  
Example: /search/page  
#### 14.3 Method
- HTTP method  
Example:
- GET  
#### 14.4 Response Format
- usually JSON  
- defines output structure  
#### 14.5 Example Usage
`Example: ?q=jupiter&limit=20`  
#### 14.6 Parameters
- Required:
  - q → query  
- Optional:
  - limit → number of results  
#### 14.7 Response Codes
- 200 → success  
- 200 (empty) → success, no data  
- 400 → bad request  
- 500 → server error  

### 15. Error Handling
- Missing input → 400  
- Invalid values → 400  
- Server failure → 500  

### 16. Key Takeaways
- REST APIs enable structured communication  
- JSON is standard response format  
- APIs define:
  - routes  
  - methods  
  - parameters  
  - responses  
- documentation is critical  
- core idea:
  → REST = standardized client-server communication  

### Notes to be taken for `Activity Question 3`
1. URI is used to identify any resource on the internet using location, name, or both. (Question: 2)
---
### Week 6 Lecture 4  
#### Real-World REST APIs – `CoWIN` Case Study and Authentication  
##### Description: Demonstrates real-world REST API usage using the CoWIN platform. Covers public vs authenticated APIs, request construction using curl, headers, parameters, JSON responses, API usage ethics, and authentication mechanisms like tokens and API keys.

### 1. Real-World REST API Example – CoWIN
- CoWIN platform:
  - Used for vaccine registration and availability  
  - Built using RESTful APIs  
- Why APIs are needed:
  - Large-scale data handling  
  - Separation of frontend and backend  
  - Enables multiple applications to use same backend  
- Scale:
  - Designed for massive population (millions of users)

### 2. Types of APIs in CoWIN
- Unauthenticated APIs:
  - Used for:
    - Searching vaccine availability  
    - Fetching public data  
- Authenticated APIs:
  - Used for:
    - Booking appointments  
    - Downloading certificates  

### 3. API Documentation Components
- Production server → actual live API  
- API categories:
  - Authentication  
  - Metadata  
  - Appointment availability  
  - Certificate download  
- Schema:
  - Defines structure of returned data  
  - Example fields:
    - center name  
    - address  
    - pincode  
    - capacity  

### 4. Example: Availability API
- Endpoint:
  - Versioned → v2  
  - Route → appointment/sessions/public/findByPin  
- Required parameters:
  - pincode  
  - date  

### 5. Using curl for API Requests
Basic request:  
`curl -X GET <URL>`  
- -X GET → specifies HTTP method (default GET)  
- -H → adds headers  
Example headers:
- Accept: application/json  
- Accept-Language: en  

### 6. Missing Parameters Error
- If required parameters not provided:
  - API returns error  
Example:
- Missing pin-code/date → "input parameter missing"

### 7. Correct API Request Example
- Add query parameters:  
`?pincode=600001&date=04-08-2021`  
- Result:
  - Returns JSON data  

### 8. API Response Structure
- Returns:
  - Array of sessions  
Each session contains:
- center_id  
- name of hospital  
- address  
- district  
- capacity  
- dose1 capacity  
- dose2 capacity  

### 9. Using API Data
- Can build scripts to:
  - Track availability  
  - Automate queries  
IMPORTANT:
- Do NOT overload API  
- Respect usage limits  

### 10. Responsible API Usage
- APIs serve real-world systems (healthcare here)
Rules:
- Avoid excessive requests  
- Avoid automation abuse  
- Prefer non-production servers for testing  
- Risk:
  - Service disruption  
  - Ethical issues  

### 11. Headers and User-Agent
- Some APIs require:
  - User-Agent header  
Purpose:
- Identify client  
- Prevent bot abuse  

### 12. Authenticated API Example
- Example:
  - Download vaccination certificate  
- Without authentication:
  - Response → "unauthenticated access"

### 13. Why Authentication is Needed
- Protect sensitive data  
- Restrict access to valid users  
- Prevent misuse  

### 14. Authentication Methods
#### 14.1 Token-Based Authentication
- User logs in (e.g., OTP)  
- Server returns unique token  
- Token used in future requests  
- Key property:
  - Hard to guess  
#### 14.2 API Keys
- Unique key assigned to user  
- Used in requests  
Examples:
- GitHub  
- Cloud APIs  

### 15. Authentication Flow
1. User logs in  
2. Server generates token  
3. Client sends token with each request  
4. Server validates token  

### 16. API as Remote Function Call
- API request = trigger action on remote server  
Example:
- Call endpoint → server executes logic  
- Returns response  

### 17. Key Takeaways
- REST APIs power real-world systems (e.g., `CoWIN`)  
- APIs can be:
  - Public  
  - Authenticated  
- Requests include:
  - URL  
  - parameters  
  - headers  
- Authentication ensures:
  - security  
  - controlled access  
- Core idea:
  → API = controlled, structured remote interaction with a server

### Notes to be taken for `Activity Question 4`
---
### Week 6 Lecture 5  
#### API Standardization and `OpenAPI` Specification (OAS)  
##### Description: Explains the need for standardized API documentation, introduces machine-readable API descriptions, discusses limitations of traditional documentation, and presents `OpenAPI` Specification (OAS) and Swagger as solutions.

### 1. Need for Standardizing APIs
- APIs provide:
  - Information hiding → client does NOT need to know backend implementation  
  - Abstraction → database type (MySQL, PostgreSQL, etc.) is irrelevant to client  
- Separation of concerns:
  - Client uses API  
  - Server handles logic and storage  
- Important requirement:
  → API should act as an **unbreakable contract**

### 2. Why API Stability Matters
- If API changes:
  - Client applications break  
  - Scripts depending on API fail  
Examples:
- `CoWIN` API changes → third-party apps break  
- Cloud APIs change → automation scripts fail  
- Solution:
  - Use **versioning**
    - v1, v2, v3  
  - Deprecate old versions gradually  

### 3. Problems with Traditional Documentation
Documentation issues:
- Subjective quality:
  - Some developers write good docs  
  - Others write poor or no docs  
- Incomplete documentation:
  - Missing explanations  
  - Assumed knowledge  
- Outdated documentation:
  - Code changes but docs don’t  
- Language barriers:
  - Written in human language (e.g., English)  
  - Not universally accessible  

### 4. Need for Machine-Readable API Descriptions
- Goal:
  → Make APIs understandable by machines  
- Benefits:
  - Automation  
  - Code generation  
  - Reduced human error  
- Solution:
  → Use **structured description files**

### 5. Description Files Concept
- Characteristics:
  - Structured format  
  - Strict syntax  
  - Machine-readable  
- Example format:
  - XML-like structure  
  - Defined tags and hierarchy  
- Purpose:
  - Describe API behavior formally  

### 6. Automation Using Description Files
- Enables:
  - Auto-generation of boilerplate code  
  - Scaffolding  
Example:
- Automatically generate:
  - index()  
  - show()  
  - create()  
  - delete()  
- Developer only writes:
  → business logic  

### 7. Comparison with Programming Languages
- Assembly language:
  - Human-readable  
  - Machine-processable  
- C language:
  - Structured and compilable  
- API descriptions:
  - Not full programs  
  - But structured enough for machines  

### 8. `OpenAPI` Specification (OAS)
- Definition:
  → Standard for describing REST APIs  
- Key properties:
  - HTTP-based  
  - Vendor-neutral  
  - Machine-readable  

### 9. Why Vendor-Neutral Matters
- Prevents:
  - Vendor lock-in  
  - Biased implementations  
- Ensures:
  - Long-term stability  
  - Interoperability  

### 10. Scope of OAS
- Focus:
  - HTTP-based APIs  
  - Web applications  
- NOT intended for:
  - All programming APIs  
  - Low-level system APIs  

### 11. Evolution of OAS
- Origin:
  - Swagger (by SmartBear, ~2015)  
- Current version:
  - OAS 3  
- Terminology:
  - Often still called "Swagger"  

### 12. Swagger Ecosystem
- Tools:
  - Swagger UI  
  - Swagger Editor  
- Features:
  - Visual API documentation  
  - Interactive API testing  
  - Auto-generated interfaces  

### 13. Key Takeaways
- APIs require:
  - Stability  
  - Standardization  
  - Clear contracts  
- Human documentation is:
  - Useful but insufficient  
- Machine-readable formats:
  → Solve scalability and clarity issues  
- `OpenAPI` (OAS):
  → Industry-standard way to define APIs  
- Core idea:
  → API = structured, stable, machine-understandable interface between client and server

### Notes to be taken for `Activity Question 5`
---
### Week 6 Lecture 6  
#### `OpenAPI` Specification (OAS) in Practice (YAML Structure & Design Philosophy)
##### Description: Explains how `OpenAPI` specifications are written using YAML, details the structure of an `OpenAPI` document (paths, operations, responses, schemas), and highlights design-first principles, automation, and best practices for scalable API development.

### 1. `OpenAPI` Specification File Format
- `OpenAPI` specs are typically written in:
  - YAML (most common)
  - JSON (alternative)
- Key requirement:
  → Must be **structured and machine-readable**
- Purpose:
  → Remove ambiguity  
  → Enable automation  

### 2. Basic YAML Structure (Minimal Example)
- Core fields:
  - ``OpenAPI`` → version (e.g., 3.1.0)  
  - `info` → metadata  
    - title  
    - version  
  - `paths` → endpoints (can be empty initially)
- Example meaning:
  - Valid API spec  
  - But useless if no endpoints defined  

### 3. Core Components of `OpenAPI` Document
#### 3.1 Top-Level Structure
- Required:
  - ``OpenAPI``
  - `info`
  - `paths`
#### 3.2 Paths
- Represents:
  → API endpoints (URLs)
- Example:
  - `/board`
  - `/users/{id}`
#### 3.3 Endpoint Definition
- Endpoint =  
  → URL + HTTP operation (GET, POST, etc.)
- Each path contains:
  - One or more operations  
#### 3.4 Operations
Each operation includes:
- Summary  
- Description  
- Parameters  
- Request body  
- Responses  

### 4. Example: Tic Tac Toe API Concept
- API defines:
  - Create game  
  - Make move  
  - Get board state  
  - Check winner  
- Important:
  → API defines **functionality only**  
  → NOT UI or rendering  

### 5. GET Operation Example
Under `/board`:
- GET operation:
  - Summary: get board state  
  - Description: detailed explanation  
#### 5.1 Responses
- Defined using HTTP codes:
  - `200` → Success  
  - `404` → Not found  
- Each response includes:
  - Description  
  - Content  

### 6. Content Types in Responses
- API can return multiple formats:
  - `application/json`  
  - `text/html`  
- Meaning:
  → Client chooses preferred format  

### 7. Role of Controller in API Flow
- Model:
  → returns raw data  
- Controller:
  → selects appropriate format (JSON / HTML)  
- View:
  → renders output  

### 8. Schema Definition
- Used to define structure of response data  
Example:
- Simple:
  - type: integer  
  - range constraints  
- Complex:
  - type: object  
  - properties:
    - product_name → string  
    - product_price → number  

### 9. Path Parameters
Example:
- `/users/{id}`
- Meaning:
  - `id` is required  
  - Must be provided  
- Missing parameter:
  → Error response  

### 10. Request Body Specification
- Used mainly in:
  - POST  
  - PUT  
- Structure:
  - Defined using schema  
- Example:
  - JSON object  
  - integer input  
  - structured payload  

### 11. Full API Flow Structure
Hierarchy:
- `OpenAPI`  
  → Paths  
    → Endpoint  
      → Operation  
        → Responses  
          → Content  
            → Schema  

### 12. Automation Benefits
From YAML spec:
- Generate:
  - Boilerplate backend code  
  - API handlers  
  - Documentation pages  
- Developer writes:
  → only business logic  

### 13. Swagger’s Role
- Combines:
  - Documentation  
  - Code generation  
- Output:
  - Interactive API docs  
  - Ready-to-use endpoints  

### 14. Drawback of YAML
- Hard to write manually  
- Error-prone  
- Requires strict formatting  

### 15. Design-First Approach
- Key principle:
  → Design API BEFORE writing code  
- Benefits:
  - Cleaner architecture  
  - Fewer bugs  
  - Better scalability  

### 16. Importance of Design vs Coding
- Good design:
  → saves debugging time  
- Poor design:
  → leads to long debugging cycles  

### 17. Single Source of Truth
- Definition:
  → One authoritative representation  
Two approaches:
1. Spec-first:
   - YAML = source of truth  
   - Code generated from spec  
1. Code-first:
   - Code = source  
   - Docs generated from code  
- Avoid:
  → divergence between code and documentation  

### 18. Version Control for API Specs
- Use:
  - Git  
- Track:
  - Changes  
  - Features  
  - Contributors  

### 19. Public APIs and Ecosystem Growth
- Benefits of public APIs:
  - External usage  
  - Innovation  
  - Ecosystem expansion  
Examples:
- Wikipedia  
- CoWIN  
- GitHub  
- Google Cloud  

### 20. Tools and Best Practices
- Do NOT write everything manually  
Use:
- Editors  
- API tools  
- Generators  
- Ensure:
  - Consistency  
  - Maintainability  
  - Scalability  

### 21. Final Takeaways
- `OpenAPI` = structured API definition  
- YAML enables:
  - Machine readability  
  - Automation  
- Key ideas:
  - Design-first  
  - Single source of truth  
  - Separation of concerns  
- Goal:
  → Build scalable, maintainable, and robust APIs

### Notes to be taken for `Activity Question 6`
---
