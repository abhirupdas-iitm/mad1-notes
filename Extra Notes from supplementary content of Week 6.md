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
