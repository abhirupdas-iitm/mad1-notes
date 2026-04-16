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
