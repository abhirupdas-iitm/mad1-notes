### Week 10 Extra Lecture 1  
#### Authentication and Authorization in Flask using Flask-Security  
##### Description: Demonstrates how to implement authentication and authorization in a Flask application using Flask-Security. Covers user verification, role-based access control, password hashing with bcrypt, database modifications, configuration setup, login protection, and role-based permissions.

### 1. Authentication vs Authorization
- **Authentication**:
  - Verifies identity of user  
  - Example:
    - Username + password  

- **Authorization**:
  - Defines what user can do  
  - Based on:
    - Roles  
    - Permissions  

- Relationship:
  - Authorization requires authentication  

### 2. Role-Based Access Control (RBAC)
- Users assigned roles:
  - Admin  
  - Author  
  - Commenter  
- Permissions based on roles:
  - Admin → full access  
  - Author → create content  
  - Commenter → limited actions :contentReference[oaicite:0]{index=0}  

### 3. Flask-Security Introduction
- Extension for:
  - Authentication  
  - Authorization  
- Provides:
  - User model  
  - Role model  
  - Prebuilt workflows  

### 4. Required Packages
- Install:
  - Flask-Security  
  - Email validator  
  - bcrypt  
- Purpose:
  - Email validation  
  - Password hashing  

### 5. Password Hashing (bcrypt)
- One-way hashing:
  - Cannot reverse hash  
- Ensures:
  - Password security  
- Even if leaked:
  - Password not easily recoverable  

### 6. Database Changes
- Modify user table:
  - Add:
    - id (primary key)  
    - email (unique)  
    - password (hashed)  
    - active (boolean as integer)  

- Remove:
  - Username uniqueness  

### 7. Role Model
- Create:
  - Role table  
- Fields:
  - id  
  - name  
  - description  

### 8. User-Role Relationship
- Many-to-many relation:
  - One user → multiple roles  
  - One role → multiple users  
- Implement via:
  - `roles_users` table  

### 9. Updating Foreign Keys
- Ensure:
  - Consistency after renaming fields  
- Adjust:
  - All references to user id  

### 10. Flask-Security Models
- Extend:
  - `UserMixin`  
  - `RoleMixin`  
- Benefit:
  - Built-in authentication features  

### 11. Application Configuration
- Setup:
  - Security datastore  
  - Link:
    - User model  
    - Role model  

### 12. Secret Key Configuration
- Used for:
  - Sessions  
  - Cookies  
- Best practice:
  - Store in environment variables  

### 13. Password Hash Configuration
- Set:
  - Hash type → bcrypt  
  - Salt/key for hashing  
- Important:
  - Keep secret  

### 14. Registration Configuration
- Enable/disable:
  - User registration  
- Option:
  - `SECURITY_REGISTERABLE`  

### 15. Email Configuration
- Can enable:
  - Email confirmation  
  - Password reset emails  
- Disabled here:
  - No SMTP setup  

### 16. Unauthorized Access Handling
- Default:
  - 403 Forbidden  
- Configurable:
  - Custom error page  

### 17. Default Flask-Security Routes
- Automatically created:
  - `/login`  
  - `/logout`  
  - `/register`  

### 18. Login Protection
- Use:
  - `@login_required`  
- Restricts:
  - Access to authenticated users only  

### 19. Creating Users
- Register via:
  - `/register`  
- Password stored:
  - Hashed form  

### 20. Login Workflow
- Input:
  - Email + password  
- System:
  - Verifies hashed password  
- Outcome:
  - Login success/failure  

### 21. Session Management
- Uses:
  - Cookies  
- Behavior:
  - Session stored in browser  
- Deleting cookie:
  - Logs user out  

### 22. Template Access to User
- Variable:
  - `current_user`  
- Used in:
  - Templates  

### 23. Checking Authentication in Templates
- Condition:
  - `current_user.is_authenticated`  
- Enables:
  - Dynamic UI rendering  

### 24. Sidebar Implementation
- Shows:
  - User info when logged in  
  - Login/Register when not logged in  

### 25. Role Assignment
- Assign roles:
  - Direct DB insertion  
- Example:
  - User → author role  

### 26. Role-Based Access Control
- Use:
  - `@roles_required("role")`  
- Restricts:
  - Access based on role  

### 27. Testing Role Restrictions
- If role missing:
  - 403 error  
- If role present:
  - Access granted  

### 28. Custom Error Pages
- Implement:
  - 404 page  
  - 403 page  
- Improves:
  - User experience  

### 29. Roles Required vs Roles Accepted
- `roles_required`:
  - User must have ALL roles  

- `roles_accepted`:
  - User must have ANY one role  

### 30. Multiple Roles Handling
- User can:
  - Have multiple roles  
- Access:
  - Based on decorator used  

### 31. Protecting Routes
- Apply decorators:
  - Per route/controller  
- Fine-grained control:
  - Different permissions per route  

### 32. Default Templates
- Flask-Security provides:
  - Login page  
  - Register page  
- Can:
  - Customize/override  

### 33. Cookie-Based Authentication
- Mechanism:
  - Session cookies  
- Works for:
  - Web apps  
  - REST calls (via browser)  

### 34. API Authentication (Advanced)
- For external clients:
  - Use API keys / JWT  
- Example:
  - Flask-JWT  

### 35. Security Best Practices
- Use:
  - Strong secrets  
  - Hashed passwords  
- Avoid:
  - Hardcoding sensitive values  

### 36. Key Takeaways
- Authentication:
  - Verifies identity  
- Authorization:
  - Controls access  
- Flask-Security:
  - Simplifies both  
- Role-based design:
  - Essential for scalable apps  
---
