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
  - OpenAPI specification

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
  - OpenAPI specs

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
---
