### Week 9 Lecture 1  
#### Security – Introduction and Access Control  
##### Description: Introduces the concept of security in web applications, focusing on access control, types of permissions, discretionary vs mandatory control, role-based and attribute-based access, policies, principle of least privilege, privilege escalation, and enforcement mechanisms.

### 1. Introduction to Security
- Security in web applications includes:
  - Access control  
  - Web-based mechanisms  
  - Session management  
  - HTTPS (secure communication)  
  - Logs and analysis  
- Focus of this lecture:
  - **Access control**

### 2. What is Access Control?
- Access = ability to:
  - Read  
  - Write  
  - Modify data  
- Not all data should be public:
  - Personal information (email, phone, address)  
  - Financial data  
  - Academic records  
  - Company data  
- Goal:
  - Restrict **who can access what**

### 3. Types of Access
- Read-only access  
- Read-write (CRUD operations)  
- Partial modification:
  - Modify but not create  
  - Modify but not delete  
- Fine-grained control:
  - Specific permissions for specific actions

### 4. Examples of Access Control
#### 4.1 Linux File System
- Each file has:
  - Owner  
  - Group  
- Permissions:
  - Read / Write / Execute  
- Owner:
  - Full control  
  - Can change permissions  
- Superuser (root/admin):
  - Full system access  

#### 4.2 Email Systems
- Can:
  - Read own email  
  - Forward emails  
- Forwarding = implicit permission  

#### 4.3 E-commerce Applications
- Shopping cart:
  - Visible only to user  
- Financial data:
  - Must be strictly protected  

### 5. Discretionary vs Mandatory Access Control
#### 5.1 Discretionary Access Control (DAC)
- User controls access  
- Example:
  - File owner changes permissions  
  - Email forwarding  
- Flexible but less strict  

#### 5.2 Mandatory Access Control (MAC)
- Central authority controls access  
- Users cannot:
  - Modify permissions  
  - Share access  
- Used in:
  - Military  
  - High-security environments  

### 6. Role-Based Access Control (RBAC)
- Access based on **roles**, not usernames  
- Example roles:
  - Head of Department (HOD)  
  - Teacher  
  - Student  
  - Sports club member  
- Benefits:
  - Easier management when roles change  
- Features:
  - One user → multiple roles  
  - One role → multiple users  
- Role hierarchy:
  - HOD > Teacher > Student  
- Independent roles:
  - HOD ≠ Sports club member  

### 7. Attribute-Based Access Control (ABAC)
- Access depends on **attributes**
- Examples:
  - Time of day  
  - User properties (age, role, location)  
- Example rule:
  - Access allowed only between 9 AM – 5 PM  
- Extends RBAC with additional conditions  

### 8. Permissions vs Policies
#### 8.1 Permissions
- Simple, static rules  
- Example:
  - User can read file  

#### 8.2 Policies
- Combine multiple conditions  
- Example:
  - Bank employee can view ledger  
  - Only after 8 AM on working days  
- More flexible and expressive  

### 9. Principle of Least Privilege
- Give **minimum access required**  
- Examples:
  - Delivery person:
    - Needs address only  
  - Linux:
    - Users can read libraries  
    - Cannot modify system files  
    - Sensitive files (e.g., `/etc/shadow`) restricted  

#### Benefits:
- Better security  
- Better system stability  
- Easier deployment  

#### Challenges:
- Not always easy to enforce  
- Some systems require relaxed permissions (e.g., file uploads)  

### 10. Privilege Escalation
- Temporarily gaining higher privileges  
- Tools:
  - `sudo` → execute one command as admin  
  - `su` → switch user  
- Risks:
  - Can damage system  
- Best practices:
  - Use only when necessary  
  - Avoid running as root  
  - Maintain logs  

### 11. Access Control in Web Applications
- Example:
  - Admin dashboard:
    - Add/delete users  
    - Modify data  
  - Regular user:
    - Read-only access to own data  
- Additional checks:
  - Login required  
  - Role/permission verification  

### 12. Enforcement of Access Control
#### 12.1 Hardware Level
- Physical access:
  - Keys  
  - Security tokens  
  - NFC cards  

#### 12.2 Operating System Level
- File permissions  
- Memory protection  
- Process isolation  

#### 12.3 Application Level
- Database restrictions:
  - Access to specific databases  

#### 12.4 Web Application Level
- Controllers enforce access  
- Use wrappers (decorators)  
- Example:
  - Flask decorators (`@app.route`, auth decorators)  
- Idea:
  - Check permissions before executing controller logic  

### 13. Key Takeaways
- Access control is fundamental to security  
- Multiple models:
  - DAC, MAC, RBAC, ABAC  
- Policies provide flexibility over permissions  
- Principle of least privilege is essential  
- Enforcement happens at multiple layers  
- In web apps:
  - Controllers + decorators = main enforcement point  
---
### Week 9 Lecture 2  
#### Authentication Mechanisms and Web Security  
##### Description: Covers various authentication and security mechanisms in web applications including security by obscurity, host-based access, login systems, tokens, HTTP authentication (Basic and Digest), client certificates, cookies, sessions, and API key-based authentication.

### 1. Introduction to Web Security Mechanisms
- Focus:
  - How to **implement access control on the web**
- Key question:
  - What checks can a server perform to verify access?

### 2. Security by Obscurity (Bad Practice)
- Idea:
  - Hide system details (e.g., use non-standard port like 1356 instead of 80)
- Assumption:
  - Only people who know the port can access
- Problems:
  - Information can leak easily  
  - Not reliable security  
- Conclusion:
  - **Never rely on obscurity for security**

### 3. Host-Based Access Control
- Based on:
  - **Client IP address**
- Mechanism:
  - Allow only specific IPs (whitelisting)
- Example:
  - SSH access restricted to certain machines  
- Problem:
  - If trusted machine is compromised → security breaks  
- Conclusion:
  - Useful but **not sufficient alone**

### 4. Login-Based Authentication
- Most common approach:
  - Username + Password  
- Server:
  - Prompts user for credentials  
- Important rule:
  - Do NOT store passwords as plain text  
- Reason:
  - Server compromise → all passwords exposed  
- Solution:
  - Store **hashed passwords**  
- Risk:
  - Users reuse passwords across platforms  

### 5. Token-Based Authentication
- Used for:
  - **Machine-to-machine communication**
- Instead of:
  - Username/password input  
- Use:
  - Token (long random string)  
- Properties:
  - Hard to guess  
  - Stored securely  
- Risk:
  - Token leakage → unauthorized access  

### 6. HTTP Authentication Mechanisms
#### 6.1 Basic HTTP Authentication
- Process:
  1. Client sends request  
  2. Server responds with **401 Unauthorized**  
  3. Server sends:
     - `WWW-Authenticate` header  
  4. Client sends:
     - Username + Password (Base64 encoded)  

- Issues:
  - Base64 is **NOT encryption** (easily reversible)  
  - Credentials visible in transit  
  - No proper logout mechanism  
- Conclusion:
  - **Insecure without HTTPS**

#### 6.2 HTTP Status Codes
- `401` → Unauthorized (needs authentication)  
- `403` → Forbidden (access denied)  
- `404` → Resource not found  

### 7. Digest Authentication
- Improvement over Basic Auth  
- Uses:
  - **Cryptographic hash functions**  
- Key idea:
  - Do NOT send password directly  

#### 7.1 One-Way Functions
- Properties:
  - Easy to compute forward:  
    - `f(A) → B`  
  - Hard to reverse:  
    - Cannot get A from B  
- Used for:
  - Secure password handling  

#### 7.2 Nonce (Number Used Once)
- Server generates random value  
- Client:
  - Combines:
    - Username  
    - Password  
    - Nonce  
  - Applies hashing  
- Benefits:
  - Prevents replay attacks  
  - Each request is unique  

#### 7.3 Advantages
- More secure than Basic Auth  
- Password not transmitted directly  

### 8. Client Certificate Authentication
- Based on:
  - **Certificates (like HTTPS)**
- Instead of password:
  - Client proves identity using certificate  
- Trusted authority:
  - Issues certificates  
- Problem:
  - If certificate is stolen → security compromised  

### 9. Form-Based Authentication
- Users enter:
  - Username  
  - Password  
- Sent to server via HTTP  

#### 9.1 GET vs POST
- GET (unsafe):
  - Credentials appear in URL  
  - Stored in logs  
- POST (safer):
  - Data in request body  
  - Safer  

#### 9.2 Best Practice
- Use:
  - POST + HTTPS  
- Avoid:
  - Sending credentials in URL  

### 10. Connection-Based Security
- Each request:
  - Requires authentication  
- Optimization:
  - Keep connection alive  
- Benefit:
  - Reduces repeated authentication overhead  

### 11. Cookies and Sessions
#### 11.1 What is a Cookie?
- Small data sent by server to client  
- Stored in browser  

#### 11.2 Purpose
- Maintain **state in stateless HTTP**
- Example:
  - Remember user session  

#### 11.3 How It Works
1. Server sends:
   - `Set-Cookie` header  
2. Client stores cookie  
3. Client sends cookie in future requests  

#### 11.4 Uses
- Authentication  
- Session tracking  
- Personalization  

#### 11.5 Session Concept
- Cookie acts as:
  - Session identifier  
- Server:
  - Maps cookie → user state  

#### 11.6 Control Mechanisms
- Server:
  - Can expire cookies  
  - Force logout  
- Client:
  - Can block/delete cookies  
  - Incognito mode → no persistent cookies  

### 12. API-Level Security
- Used in:
  - REST APIs  
- Mechanism:
  - **API Keys / Tokens**  

#### 12.1 API Key Workflow
1. User registers  
2. Server issues API key  
3. Client sends key with each request  
4. Server validates key  

#### 12.2 Advantages
- Simple  
- Suitable for automation  
- No interactive login needed  

#### 12.3 Security Features
- Keys can be:
  - Revoked  
  - Expired  
- Risks:
  - Key leakage → misuse  

### 13. Key Takeaways
- Security mechanisms include:
  - Login/password  
  - Tokens  
  - Cookies  
  - Certificates  
  - API keys  
- Avoid:
  - Security by obscurity  
  - Plain text passwords  
  - GET for sensitive data  
- Prefer:
  - HTTPS  
  - Hashing  
  - Secure tokens  
- Cookies enable:
  - Stateful sessions over stateless HTTP  
- API keys enable:
  - Secure automated access  
---
### Week 9 Lecture 3  
#### Sessions, Cookies, and Authentication Enforcement  
##### Description: Explains session management in web applications, client-side vs server-side sessions, security concerns with cookies, session handling in Flask, CSRF attacks, server-side storage, and enforcing authentication using decorators.

### 1. Introduction to Sessions
- A **session** represents:
  - Multiple requests from the same client  
- Purpose:
  - Maintain **state across requests**
- Example state:
  - Logged-in status  
  - Shopping cart contents  
- Server uses session data to:
  - Customize responses  

### 2. Why Sessions are Needed
- HTTP is:
  - **Stateless by design**
- Problem:
  - Server cannot remember client state  
- Solution:
  - Add session mechanisms on top of HTTP  

### 3. Types of Sessions
#### 3.1 Client-Side Sessions
- Data stored:
  - Inside **cookies**
- Advantages:
  - Simple  
- Risks:
  - Can be tampered with  

#### 3.2 Server-Side Sessions
- Cookie stores:
  - Only session ID  
- Server stores:
  - Actual session data  
- Example stored data:
  - Preferences  
  - Cart items  
- Advantages:
  - More secure  
- Requires:
  - Backend storage  

### 4. Cookies in Session Management
- Cookie:
  - A string sent by server  
- Stored in:
  - Browser  
- Sent with:
  - Every request  

#### 4.1 Usage
- Store:
  - UI preferences  
  - Session identifiers  

#### 4.2 Security Concern
- If cookie contains sensitive data:
  - Must prevent modification  

#### 4.3 Solution
- Use:
  - **Encryption / signing with secret key**  
- Ensures:
  - Client cannot alter cookie  

### 5. Flask Session Example
- Flask provides:
  - `session` object  
- Acts like:
  - Dictionary  

#### 5.1 Checking Login
- If `username` in session:
  - User is logged in  
- Else:
  - Not logged in  

#### 5.2 Login Flow
- POST request:
  - Set session value  
- GET request:
  - Show login form  

#### 5.3 Logout Flow
- Use:
  - `session.pop()`  
- Removes:
  - Session data  

### 6. Security Issues in Sessions
#### 6.1 Cookie Modification
- Risk:
  - User alters cookie  
- Solution:
  - Use secret key  

#### 6.2 Session Hijacking
- Risk:
  - Someone steals cookie  
- Example:
  - Public computers  
- Solution:
  - Logout properly  
  - Use HTTPS  

#### 6.3 Cross-Site Request Forgery (CSRF)
- Attack:
  - Malicious site triggers requests on behalf of user  
- Example:
  - Change password silently  
- Reason:
  - Browser automatically sends cookies  

#### 6.4 CSRF Protection
- Use:
  - **CSRF tokens in forms**  
- Ensures:
  - Request originates from trusted source  

### 7. Server-Side Session Storage
- Server must store:
  - Session data  

#### 7.1 Storage Options
- Files  
- Databases  
- Key-value stores (e.g., Redis)  

#### 7.2 Redis
- Features:
  - Fast  
  - Lightweight  
- Use:
  - Temporary session storage  

### 8. Authentication Enforcement
- Not all pages:
  - Should be publicly accessible  
- Need:
  - **Fine-grained access control**  

### 9. Protecting Views (Controllers)
- Access control happens at:
  - **Controller level**  

#### 9.1 Using Decorators
- Add authentication checks  
- Example:
  - `@login_required`  

#### 9.2 Workflow
1. Request made  
2. Decorator checks authentication  
3. If not authenticated:
   - Redirect to login  
4. If authenticated:
   - Execute controller  

### 10. Flask-Login Example
- Provides:
  - `login_required`  
  - `current_user`  

#### 10.1 Protected Route
- Only logged-in users:
  - Can access `/profile`  

#### 10.2 Role-Based Access
- Can extend:
  - Check user roles  
- Example:
  - Admin vs normal user  

### 11. Logout Mechanism
- Requires:
  - User to be logged in  
- Action:
  - Remove session data  
- Redirect:
  - Back to homepage  

### 12. Key Takeaways
- Sessions:
  - Add state to stateless HTTP  
- Cookies:
  - Enable session tracking  
- Security concerns:
  - Cookie tampering  
  - Session hijacking  
  - CSRF attacks  
- Solutions:
  - Secret keys  
  - Tokens  
  - HTTPS  
- Authentication:
  - Enforced using decorators  
- Controllers:
  - Central point for access control  
---
### Week 9 Lecture 4  
#### HTTPS, Encryption, and Secure Communication  
##### Description: Explains the need for HTTPS, how encryption secures communication, SSL/TLS concepts, key exchange, certificate-based trust, chain of trust, and trade-offs of using HTTPS.

### 1. HTTP Communication Basics
- Client connects to server:
  - Typically via **port 80**
- Sends:
  - HTTP request (plain text)  
- Receives:
  - HTTP response (plain text)  
- Problem:
  - Data is **readable by anyone on the network**  

### 2. The Security Problem
- Communication travels through:
  - Multiple networks (WiFi, routers, fiber, etc.)  
- Possible attacker:
  - Can **intercept (sniff)** data  
  - Can **modify** requests/responses  

### 3. Types of Attacks
#### 3.1 Eavesdropping
- Attacker reads:
  - Requests  
  - Responses  
- Sensitive data exposed:
  - Passwords  
  - Personal info  

#### 3.2 Data Tampering
- Attacker modifies:
  - Requests (e.g., GET → POST)  
  - Responses  

### 4. Need for Encryption
- Goal:
  - Make intercepted data **unreadable**  
- Approach:
  - Convert data into:
    - Encrypted form (ciphertext)  
- Only client + server:
  - Can decrypt  

### 5. Secure Channel (SSL/TLS)
- HTTPS uses:
  - **Secure Sockets Layer (SSL) / TLS**  
- Creates:
  - Encrypted communication channel  

### 6. Encryption Key Concept
- Requires:
  - **Shared secret key**  
- Process:
  - Combine data + key → encrypted data  
- Without key:
  - Attacker cannot decode  

### 7. Challenge: Key Exchange
- Problem:
  - How to share secret securely?  
- Constraint:
  - Communication channel is already insecure  

### 8. Conceptual Solution
- Use:
  - Mathematical methods  
- Combine:
  - Client secret + Server secret  
- Result:
  - Shared key unknown to attacker  

### 9. Additional Security Guarantees
- Prevent:
  - Unauthorized decryption  
- Prevent:
  - Fake requests (integrity protection)  

### 10. Server Authentication
- Client must verify:
  - Server identity  
- Prevents:
  - Fake servers (phishing)  

### 11. Certificates
- Server provides:
  - **Digital certificate**  
- Contains:
  - Identity  
  - Expiry date  
  - Issuer information  

### 12. Certificate Authority (CA)
- Trusted organization:
  - Issues certificates  
- Example:
  - Google Trust Services  

### 13. Chain of Trust
- Certificate hierarchy:
  1. Website certificate  
  2. Intermediate CA  
  3. Root CA  
- Root CA:
  - Trusted by browser/OS  

### 14. Root of Trust
- Stored in:
  - Browser  
  - Operating system  
- Trust assumption:
  - Root certificates are valid  

### 15. Browser Verification Process
- Steps:
  1. Receive server certificate  
  2. Verify chain of trust  
  3. Check expiry  
  4. Confirm domain match  
- If valid:
  - Show **HTTPS lock icon**  

### 16. Risks in Trust Model
- If root certificate compromised:
  - Entire system at risk  
- Fake certificates:
  - Can impersonate websites  

### 17. DNS Consideration
- DNS may redirect to wrong server  
- Protection:
  - Certificate mismatch detected  
- Result:
  - Browser shows warning  

### 18. Wildcard Certificates
- Covers:
  - Multiple subdomains  
- Example:
  - `*.iitm.ac.in`  
- Useful for:
  - Large systems  

### 19. Benefits of HTTPS
- Encryption:
  - Protects confidentiality  
- Integrity:
  - Prevents tampering  
- Authentication:
  - Verifies server identity  

### 20. Limitations of HTTPS
#### 20.1 Performance Overhead
- Encryption/decryption:
  - Requires computation  

#### 20.2 Reduced Caching
- Proxies cannot:
  - Read encrypted content  
- Limits:
  - Intermediate caching  

### 21. Key Takeaways
- HTTP:
  - Insecure (plain text)  
- HTTPS:
  - Secure via encryption  
- Core components:
  - SSL/TLS  
  - Certificates  
  - Chain of trust  
- Trade-off:
  - Security vs performance  
- Essential for:
  - Safe web communication  
---
