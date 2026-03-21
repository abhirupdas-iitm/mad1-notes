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
