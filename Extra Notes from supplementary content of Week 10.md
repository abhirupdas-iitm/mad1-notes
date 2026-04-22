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
### Week 10 Extra Lecture 2  
#### Testing Flask Applications using Pytest and Test Client  
##### Description: Demonstrates how to test Flask applications using pytest. Covers unit vs functional testing, test discovery, Flask test client usage, fixtures, database setup/cleanup, HTML validation using BeautifulSoup, and measuring test coverage.

### 1. Types of Testing
- **Unit Testing**:
  - Tests smallest components (functions)  

- **Integration Testing**:
  - Tests interaction between components  

- **Functional Testing**:
  - Tests full application behavior  

- Focus:
  - Flask → integration + functional testing :contentReference[oaicite:0]{index=0}  

### 2. Pytest Setup
- Install:
  - pytest  
  - coverage  
  - BeautifulSoup  
- Add to:
  - `requirements.txt`  

### 3. Test Directory Structure
- Create:
  - `test/` folder  
- Subfolders:
  - `unit/`  
  - `functional/`  
- Add:
  - `__init__.py` to make packages  

### 4. Test Discovery Rules
- Pytest automatically finds:
  - Files starting with `test_`  
- Functions:
  - Must start with `test_`  

### 5. Basic Unit Test Example
- Function:
  - `add(x, y)`  
- Test:
  - `assert add(1,2) == 3`  
- Assertion:
  - Validates expected output  

### 6. Running Tests
- Command:
  - `pytest`  
- Options:
  - Verbose output  
  - Disable warnings  

### 7. Assertion Failure
- Shows:
  - Expected vs actual result  
- Helps:
  - Debug logic errors  

### 8. Flask Testing Approach
- Two options:
  - Run server + send requests  
  - Use Flask **test client**  

- Preferred:
  - Test client (faster, cleaner)  

### 9. Flask Test Client
- Create:
  - `client = app.test_client()`  
- Allows:
  - Simulating HTTP requests  

### 10. App Context Requirement
- Needed:
  - For database and app operations  
- Use:
  - `app.app_context().push()`  

### 11. Database Setup in Tests
- Use:
  - `db.create_all()`  
- Ensures:
  - Tables exist before test  

### 12. Sending Requests
- Example:
  - `client.get("/")`  
- Returns:
  - Response object  

### 13. Validating Response
- Check:
  - Content  
  - Status  
- Example:
  - Page title = "All Articles"  

### 14. Cleanup After Test
- Remove:
  - App context  
  - Database data  
- Ensures:
  - No side effects  

### 15. Testing Configuration
- Separate config:
  - Testing environment  
- Changes:
  - In-memory database  
  - Disable CSRF  

### 16. In-Memory Database
- Benefits:
  - Fast  
  - Temporary  
- Auto-destroyed after tests  

### 17. CSRF Disable for Testing
- Reason:
  - Avoid blocking automated requests  
- Variable:
  - `WTF_CSRF_ENABLED = False`  

### 18. Arrange–Act–Assert–Cleanup Pattern
- **Arrange**:
  - Setup environment  

- **Act**:
  - Execute functionality  

- **Assert**:
  - Verify output  

- **Cleanup**:
  - Reset state  

### 19. Pytest Fixtures
- Purpose:
  - Reusable setup/teardown  
- Avoid:
  - Code duplication  

### 20. Fixture Example – Client
- Setup:
  - Create test client  
- Yield:
  - Client for test  
- Cleanup:
  - Runs after test  

### 21. Fixture Example – Database
- Setup:
  - `db.create_all()`  
- Cleanup:
  - `db.drop_all()`  

### 22. Yield vs Return
- `yield`:
  - Allows cleanup after test  
- `return`:
  - Ends function immediately  

### 23. Fixture Execution Flow
- Order:
  1. Setup  
  2. Yield  
  3. Run test  
  4. Cleanup  

### 24. Using Fixtures in Tests
- Pass as:
  - Function parameters  
- Pytest:
  - Injects automatically  

### 25. Shared Fixtures (conftest.py)
- Store fixtures in:
  - `conftest.py`  
- Scope:
  - Available across all tests  

### 26. Functional Testing Example
- Scenario:
  - Homepage with no articles  
- Test:
  - Check "All Articles" text  

### 27. Testing Database Data
- Insert:
  - User  
  - Article  
- Validate:
  - Appears in UI  

### 28. HTML Parsing with BeautifulSoup
- Parse:
  - Response HTML  
- Extract:
  - Elements (tags, classes)  

### 29. Validating UI Elements
- Example:
  - Count "like icons"  
- Assertion:
  - Number of elements = expected  

### 30. Checking Content
- Extract:
  - `<h2>` or headings  
- Compare:
  - Text with expected value  

### 31. Testing Login Flow
- Send:
  - POST `/login`  
- Data:
  - Email + password  
- Verify:
  - Login success  

### 32. Testing Without Login
- Access:
  - Protected route  
- Expect:
  - Redirect to login page  

### 33. Testing With Login
- After login:
  - Access route  
- Verify:
  - Content displayed  

### 34. Role of Response Data
- Used for:
  - Assertions  
- Contains:
  - HTML output  

### 35. Class-Based Tests
- Group:
  - Related test cases  
- Run:
  - Top-to-bottom  

### 36. Drawback of Class Tests
- Tests may:
  - Depend on each other  
- Risk:
  - Reduced independence  

### 37. Best Practice
- Prefer:
  - Independent test functions  
- Avoid:
  - Dependency between tests  

### 38. Advanced Testing Scenarios
- Test:
  - Forms  
  - Tables  
  - Multiple records  
- Add:
  - Multiple assertions  

### 39. Coverage Tool
- Measures:
  - Code coverage  
- Shows:
  - % of code tested  

### 40. Running Coverage
- Command:
  - `coverage run -m pytest`  
- Report:
  - `coverage report`  

### 41. Coverage Insights
- Shows:
  - Total statements  
  - Covered lines  
  - Missing lines  

### 42. Limiting Coverage Scope
- Focus:
  - Application code only  
- Ignore:
  - Test files  

### 43. Importance of Testing
- Ensures:
  - Reliability  
  - Stability  
- Helps:
  - Catch bugs early  

### 44. Key Takeaways
- Pytest:
  - Powerful and flexible  
- Flask test client:
  - Simplifies API testing  
- Fixtures:
  - Improve reusability  
- Coverage:
  - Measures test completeness  
---
