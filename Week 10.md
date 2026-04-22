### Week 10 Lecture 1  
#### Software Testing – Concepts, Types, and Coverage  
##### Description: Introduces the concept of software testing, its importance, types (static vs dynamic, white box vs black box), regression testing, and different coverage metrics including statement, branch, and condition coverage.

### 1. Introduction to Testing
- Testing is a fundamental concept in **software development**
- Applies to:
  - Software systems  
  - General engineered systems  
- Core questions:
  - Why test?  
  - What to test?  
  - When to test?  
  - How to test?  
- Example tool:
  - `pytest` for Python programs :contentReference[oaicite:0]{index=0}  

### 2. Why Testing is Needed
- Primary goal:
  - Check if system **works as intended**
- Requires:
  - Defined **requirements/specifications**
- Example (analogy: car system):
  - Accepts correct fuel  
  - Handles load conditions  
  - Operates within limits  
- In web applications:
  - Correct UI display  
  - Correct input handling  
  - Proper interaction flow  

### 3. Functional Requirements Testing
- Verifies:
  - Correct page rendering  
  - Input fields and controls  
  - UI components (e.g., date picker)  
- Ensures:
  - System behaves correctly under expected conditions  

### 4. Input and Response Testing
- Checks:
  - Correct handling of user inputs  
  - Data storage and processing  
- Example:
  - Enter date → stored correctly → appropriate response generated  

### 5. Performance and Timing Constraints
- Some systems require:
  - **Time-bound responses**
- Example:
  - Online exams  
  - Real-time systems  
- Requirement:
  - Response within acceptable time  

### 6. Deployment and Usability Testing
- Checks:
  - Installation correctness  
  - Environment setup  
- Evaluates:
  - Usability  
  - User-friendliness  
- Final goal:
  - Correctness + usability  

### 7. Static vs Dynamic Testing
#### 7.1 Static Testing
- Code is **not executed**
- Examples:
  - Code review  
  - Manual inspection  
  - Proof checking tools  
- Focus:
  - Code structure  
  - Logic correctness  

#### 7.2 Dynamic Testing
- Code is **executed**
- Uses:
  - Test inputs  
- Types of inputs:
  - Valid inputs  
  - Invalid inputs (edge cases)  
- Goal:
  - Verify runtime behavior  

### 8. White Box Testing
- Tester has **full knowledge of internal code**
- Can:
  - Inspect variables  
  - Track execution  
  - Design targeted tests  
- Advantages:
  - More precise debugging  
- Disadvantages:
  - Bias toward implementation  
  - Weak separation of concerns  

### 9. Black Box Testing
- Tester has **no knowledge of internal implementation**
- Only uses:
  - API/interface  
- Advantages:
  - Real-world testing  
  - Clean abstraction  
- Disadvantages:
  - Harder debugging  
  - May miss edge cases  

### 10. Grey Box Testing
- Combination of:
  - White box + Black box  
- Approach:
  - Test via interface  
  - Inspect internals when needed  
- Requires:
  - Partial knowledge of system  

### 11. Regression Testing
- Ensures:
  - New changes do NOT break existing functionality  
- Example:
  - Adding course feature should not break student feature  
- Uses:
  - **Test suite (collection of tests)**  
- Important for:
  - Continuous development  

### 12. Handling Breaking Changes
- When changes break compatibility:
  - Versioning used  
- Example:
  - API v1 → API v2  
- Approaches:
  - Deprecate old version  
  - Maintain multiple versions  

### 13. Code Coverage
- Measures:
  - How much code is tested  
- Key idea:
  - Whether code lines are executed during testing  
- Important:
  - 100% coverage ≠ bug-free code  

### 14. Example Function Testing
- Function:
  - Takes inputs x, y  
  - Uses condition  
  - Returns value  
- Test cases:
  - `foo(0,0)` → 0  
  - `foo(1,1)` → 1  
  - `foo(1,0)` → 0  

### 15. Types of Coverage
#### 15.1 Function Coverage
- Each function is:
  - Called at least once  

#### 15.2 Statement Coverage
- Each line:
  - Executed at least once  
- Example:
  - Single test may achieve 100%  

#### 15.3 Branch Coverage
- Each branch:
  - True and false paths executed  
- Requires:
  - Multiple test cases  

#### 15.4 Condition Coverage
- Each condition:
  - Evaluated independently  
- Example:
  - x > 0  
  - y > 0  

### 16. Coverage Limitations
- 100% coverage does NOT guarantee:
  - No bugs  
- Reasons:
  - Limited test inputs  
  - Missing edge cases  

### 17. Key Observations
- Testing is:
  - Complex  
  - Non-trivial  
- Requires:
  - Careful test design  
- Trade-offs:
  - Internal knowledge vs abstraction  

### 18. Key Takeaways
- Testing ensures:
  - Correctness  
  - Reliability  
- Types:
  - Static vs Dynamic  
  - White box vs Black box vs Grey box  
- Important practices:
  - Regression testing  
  - Code coverage analysis  
- Final insight:
  - Testing improves confidence, NOT guarantees correctness

### Notes to be taken for `Activity Question 1`
1. 
---
### Week 10 Lecture 2  
#### Levels of Testing – Requirements, Unit, Integration, System, and Acceptance Testing  
##### Description: Explores different levels of testing in software development including requirements gathering, unit testing, integration testing, continuous integration, system testing, and user acceptance testing with real-world application examples.

### 1. Introduction to Testing Levels
- Testing applies at **multiple levels** in software development  
- Example context:
  - Online degree dashboard system :contentReference[oaicite:0]{index=0}  
- Key idea:
  - Testing starts **before coding begins**  

### 2. Requirements Gathering
- First step:
  - Identify **what needs to be built**  
- Key questions:
  - Who are the stakeholders?  
  - What functionality is required?  

### 3. Stakeholders Identification
- Stakeholders = people who use or depend on system  
- Examples:
  - Students  
    - View courses  
    - Add/drop courses  
    - Download certificates  
  - Administrators  
    - Manage student database  
  - Teachers  
    - Update course content  

### 4. Functional vs Non-Functional Requirements
#### 4.1 Functional Requirements
- Define:
  - What system should do  
- Examples:
  - View updates  
  - Register exam preferences  
  - Modify course registration  

#### 4.2 Non-Functional Requirements
- Define:
  - Look and feel / usability  
- Examples:
  - Page color  
  - Font style  
  - Layout design  

### 5. Dashboard Structure Understanding
- Typical UI structure:
  - Navigation panel (left side)  
  - Main content area  
  - Header (logo, user info)  
  - Footer (additional info)  
- Based on:
  - UX design principles  

### 6. Mapping Requirements to MVC
- Each functionality:
  - Maps to **controller action**  
- Flow:
  - User action → Controller → Model → View  
- Example:
  - Click "updates" → fetch data → display in view  

### 7. Importance of Clear Specifications
- Natural language is:
  - Ambiguous  
- Example ambiguity:
  - “Update course registration”  
    - Add course?  
    - Drop course?  
    - Modify anytime?  
- Solution:
  - Define precise behavior  

### 8. Use Cases for Clarity
- Use cases describe:
  - Step-by-step user actions  
- Benefits:
  - Removes ambiguity  
  - Helps implementation  
  - Helps testing design  

### 9. Early Test Case Design
- Testing begins during:
  - Requirements phase  
- Example:
  - Add course functionality  
- Test aspects:
  - Correct UI  
  - Correct response  
  - Valid/invalid inputs  

### 10. Breaking into Units
- System divided into:
  - Small components (units)  
- Examples:
  - View courses  
  - Edit course status  
  - Set exam preferences  
- Each unit:
  - Maps to controller + model + view  

### 11. Unit Testing
- Tests:
  - Individual components  
- Characteristics:
  - Small scope  
  - Clearly defined inputs/outputs  
- Example:
  - GET request → display form  
  - POST request → update database  

### 12. Testing in Isolation
- Question:
  - Can unit be tested independently?  
- Issue:
  - Some features depend on others  
- Solution:
  - Use **dummy/pre-populated data**  

### 13. Dummy Database Usage
- Purpose:
  - Avoid using live data  
- Benefits:
  - Safe testing  
  - Repeatability  
- Example:
  - One student + one course dataset  

### 14. Unit Test Scenarios
- Examples:
  - Form display correctness  
  - Invalid input handling  
  - Duplicate entry handling  
- Goal:
  - Ensure robustness  

### 15. Test Driven Development (TDD)
- Approach:
  - Write tests BEFORE code  
- Process:
  1. Write tests → all fail  
  2. Implement code  
  3. Tests start passing  
- Result:
  - Reliable implementation  

### 16. Regression Testing
- Ensures:
  - New changes do not break old features  
- Example:
  - Adding admin feature should not break student module  
- Uses:
  - Existing test suite  

### 17. Integration Testing
- Combines:
  - Multiple modules  
- Examples:
  - Student + Course  
  - Student + Payment  
- Goal:
  - Ensure modules work together  

### 18. Integration Issues
- Problems:
  - Dependency mismatch  
  - Assumption conflicts  
- Cause:
  - Poor communication between developers  
- Solution:
  - Coordination + design consistency  

### 19. Continuous Integration (CI)
- Trigger:
  - Code commit to main branch  
- Action:
  - Run automated tests  
- Tools:
  - GitHub / GitLab CI pipelines  
- Benefit:
  - Early detection of issues  

### 20. CI Best Practices
- Avoid:
  - Excessive test triggers  
- Recommended:
  - Periodic commits  
- Goal:
  - Balance speed and reliability  

### 21. System Level Testing
- Tests:
  - Entire system  
- Includes:
  - Server  
  - Deployment environment  
- Focus:
  - Real-world usage  

### 22. System Testing Characteristics
- Often:
  - Black-box testing  
- May include:
  - Manual testing  
- Requires:
  - Full deployment setup  

### 23. Non-Functional Testing at System Level
- Evaluates:
  - Performance  
  - Scalability  
- Example:
  - Response under heavy load  
- Questions:
  - Does system slow down?  
  - Does cost increase?  

### 24. Browser Automation
- Tools simulate:
  - User interactions  
- Actions:
  - Click buttons  
  - Navigate pages  
- Used for:
  - Automated UI testing  

### 25. Test Environment Setup
- Separate environment:
  - Testing system  
  - Production system  
- Purpose:
  - Safe validation before release  

### 26. User Acceptance Testing (UAT)
- Final testing stage  
- Performed by:
  - Real users / stakeholders  
- Goal:
  - Validate system usability  

### 27. Beta Testing
- Pre-release testing phase  
- Users:
  - Limited group  
- Purpose:
  - Gather feedback  
- Output:
  - Real-world bug reports  

### 28. Feedback Importance
- Users provide:
  - Detailed issue reports  
- Helps:
  - Faster debugging  
  - Better improvements  

### 29. Final Deployment
- After:
  - All tests pass  
- System is:
  - Released to production  

### 30. Key Takeaways
- Testing spans:
  - Entire development lifecycle  
- Levels:
  - Requirements  
  - Unit  
  - Integration  
  - System  
  - Acceptance  
- Important practices:
  - Early testing  
  - Automation  
  - Continuous integration  
- Final goal:
  - Reliable and scalable software  

### Notes to be taken for `Activity Question 2`
1. 
---
### Week 10 Lecture 3  
#### Systematic Test Generation – API Testing, Abstract Tests, Model-Based Testing, UI and Security Testing  
##### Description: Explores systematic approaches to generating test cases including API-based testing using OpenAPI/Swagger, abstract and executable tests, model-based testing using state machines, GUI testing with tools like Selenium, and security testing techniques such as fuzzing and SQL injection testing.

### 1. Introduction to Systematic Test Generation
- Goal:
  - Generate tests in a **structured and repeatable way**  
- Question:
  - Can test cases be **automatically generated**? :contentReference[oaicite:0]{index=0}  

### 2. API-Based Testing
- Based on:
  - **Application Programming Interface (API)**  
- Uses:
  - REST APIs  
  - OpenAPI / Swagger specifications  
- Idea:
  - Generate tests directly from API definition  

### 3. OpenAPI and Test Generation
- OpenAPI provides:
  - API documentation  
  - Endpoint definitions  
- Enables:
  - Code generation  
  - Test case generation  
- Benefit:
  - Single source of truth  

### 4. Swagger-Based Testing Tools
- Example:
  - Swagger Inspector  
- Capabilities:
  - Generate tests from endpoints  
  - Define query parameters  
  - Define request body  
  - Define authentication  
- Output:
  - Automated test cases  

### 5. Benefits of API-Based Testing
- Advantages:
  - Reduces manual effort  
  - Standardized testing  
  - Captures best practices  
- Helps:
  - Beginners adopt proven techniques  

### 6. Abstract Tests
- Definition:
  - **Semi-formal test description**  
- Example:
  - “Request / endpoint and check for ‘Hello world’”  
- Characteristics:
  - Human-readable  
  - Not executable  

### 7. Executable Tests
- Implementation:
  - Convert abstract tests → code  
- Example:
  - `client.get("/")`  
  - `assert "Hello world" in response`  
- Result:
  - Runnable test case  

### 8. Abstract vs Executable Tests
- Abstract:
  - General  
  - Reusable  
- Executable:
  - Specific  
  - Implemented in code  
- Workflow:
  - Abstract → Translate → Execute  

### 9. Automation Possibilities
- Partial automation:
  - Convert abstract tests to code  
- Limitation:
  - Context-specific logic required  
- Developer role:
  - Final implementation  

### 10. Model-Based Testing
- Idea:
  - Represent system as a **model**  
- Common model:
  - Finite State Machine (FSM)  

### 11. Example – Authentication Flow
- States:
  - Not logged in  
  - Login page  
  - Logged in  
  - Password reset  
- Transitions:
  - Login  
  - Reset password  
  - Redirect  

### 12. Generating Tests from Models
- Approach:
  - Identify states  
  - Identify transitions  
- Tests:
  - Validate each transition  
- Example:
  - Password reset → return to correct page  

### 13. Advantages of Model-Based Testing
- Covers:
  - All possible scenarios  
- Ensures:
  - Transition correctness  
- Supports:
  - Automated test generation  

### 14. Combining Models and Abstract Tests
- Model:
  - Defines system behavior  
- Abstract test:
  - Defines expected outcomes  
- Together:
  - Generate executable tests  

### 15. GUI (User Interface) Testing
- Focus:
  - Graphical User Interface  
- In web apps:
  - HTML + CSS separation  

### 16. Types of UI Testing
- Check:
  - Element presence  
  - Layout positioning  
- Examples:
  - Navigation links exist  
  - Button position on screen  

### 17. Behavior Testing in UI
- Actions:
  - Random clicks  
  - Navigation flow  
- Goal:
  - Detect crashes  
  - Detect data corruption  

### 18. Challenges in UI Testing
- Issues:
  - CAPTCHA  
  - Access restrictions  
- Result:
  - Hard to fully automate  

### 19. Selenium for UI Testing
- Tool:
  - Browser automation framework  
- Features:
  - Controls browser programmatically  
  - Simulates user actions  
- Actions:
  - Click  
  - Scroll  
  - Input text  

### 20. Advantages of Selenium
- Realistic testing:
  - Uses actual browser  
- Supports:
  - Cookies  
  - Sessions  
- Mimics:
  - Real user behavior  

### 21. Alternative Tools
- Example:
  - Python `requests` library  
- Limitation:
  - No UI interaction  
- Use case:
  - API-level testing  

### 22. Security Testing
- Goal:
  - Identify vulnerabilities  
- Risks:
  - Application crash  
  - Data corruption  

### 23. Importance of Data Integrity
- Worst case:
  - Incorrect data without detection  
- Better case:
  - System crash (visible issue)  

### 24. Types of Security Testing
- Techniques:
  - SQL injection testing  
  - Input validation testing  
- Approach:
  - Simulate attacks  

### 25. Black Box vs White Box Testing
#### Black Box
- No knowledge of internals  
- Simulates external attacker  

#### White Box
- Full knowledge of code  
- More thorough testing  

### 26. Developer Responsibility
- Must assume:
  - Attacker knows implementation  
- Goal:
  - Secure even in worst-case scenario  

### 27. Fuzz Testing
- Definition:
  - Random/semi-random input generation  
- Purpose:
  - Break system  

### 28. Fuzzing Techniques
- Methods:
  - Random text inputs  
  - Random clicks  
- Targets:
  - Forms  
  - Input fields  

### 29. Goals of Fuzz Testing
- Detect:
  - Crashes  
  - Overflows  
  - Unexpected behavior  

### 30. Key Takeaways
- Test generation can be:
  - Automated (partially)  
- Techniques:
  - API-based testing  
  - Abstract tests  
  - Model-based testing  
  - UI testing  
  - Security testing  
- Important principle:
  - Combine multiple approaches for robustness  
---
### Week 10 Lecture 4  
#### Testing in Python using Pytest Framework  
##### Description: Introduces the pytest framework for writing and executing tests in Python. Covers test discovery, assertions, fixtures, exception testing, temporary resources, and testing Flask applications using client fixtures.

### 1. Introduction to Pytest
- Framework for:
  - Writing and running tests in Python  
- Characteristics:
  - Easy to use  
  - Opinionated (follows conventions automatically) :contentReference[oaicite:0]{index=0}  

### 2. Opinionated Nature of Pytest
- Automatically detects:
  - Test files  
  - Test functions  
- Convention:
  - Files start with `test_`  
  - Functions start with `test_`  
- Benefit:
  - Reduces boilerplate code  

### 3. Features of Pytest
- Provides:
  - Automatic setup/teardown  
  - Test fixtures  
  - Monkeypatching support  
- Helps:
  - Simplify test writing  

### 4. Pytest vs unittest
- `unittest`:
  - Built-in Python library  
- `pytest`:
  - More features  
  - Cleaner syntax  
- Both:
  - Can be used together  

### 5. Basic Test Example
- Function:
  - `func(x) = x + 1`  
- Test:
  - Assert expected output  
- Purpose:
  - Validate correctness  

### 6. Assertion Mechanism
- Uses:
  - `assert` statement  
- Behavior:
  - True → pass  
  - False → fail with error  
- Example:
  - `assert func(3) == 5` (fails)  

### 7. Understanding Test Failures
- Output includes:
  - Expected vs actual values  
- Helps:
  - Debug quickly  
- Developer decides:
  - Bug in test or code  

### 8. Testing Exceptions
- Use:
  - `pytest.raises()`  
- Purpose:
  - Verify error conditions  
- Example:
  - Out-of-bound access → IndexError  

### 9. Temporary Resources in Tests
- Need:
  - Temporary files/directories  
- Pytest:
  - Creates safely  
  - Cleans automatically  
- Avoids:
  - Side effects on system  

### 10. Test Fixtures
- Definition:
  - Setup + teardown logic  
- Purpose:
  - Prepare environment before test  
- Cleanup:
  - Done after test  

### 11. Fixture Example
- Setup:
  - Create list `[apple, banana]`  
- Tests:
  - Check presence of elements  
- Result:
  - Pass/fail based on assertions  

### 12. Fixture Behavior
- Automatically:
  - Runs before test  
- Isolated:
  - Each test gets fresh data  
- No interference between tests  

### 13. Multiple Test Results
- Output:
  - `..F`  
- Meaning:
  - Two passed, one failed  
- Helps:
  - Identify failing test quickly  

### 14. Test Discovery Rules
- Pytest searches:
  - Current directory  
  - Subdirectories  
- File patterns:
  - `test_*.py`  
  - `*_test.py`  

### 15. Function Naming Rules
- Test functions:
  - Must start with `test`  
- Class-based tests:
  - Class starts with `Test`  
  - Methods start with `test`  

### 16. Best Practice
- Follow:
  - Consistent naming conventions  
- Avoid:
  - Mixing patterns randomly  

### 17. Pytest as Superset
- Compatible with:
  - `unittest`  
- Adds:
  - Fixtures  
  - Simpler syntax  

### 18. Testing Flask Applications
- Flask supports:
  - Pytest integration  
- Key concept:
  - Test client  

### 19. Client Fixture
- Purpose:
  - Simulate HTTP requests  
- Setup:
  - Create app instance  
  - Enable testing mode  
- Uses:
  - Temporary database  

### 20. Role of Yield in Fixtures
- Behavior:
  - Setup → yield → cleanup  
- After tests:
  - Resources removed  

### 21. Temporary Database Setup
- Example:
  - SQLite file  
- Used for:
  - Isolated testing  
- Ensures:
  - No real data affected  

### 22. Making Requests in Tests
- Methods:
  - `client.get()`  
  - `client.post()`  
- Simulates:
  - User interaction  

### 23. Validating Responses
- Response object:
  - `rv.data` → content  
  - `rv.headers` → metadata  
- Assertions:
  - Check expected output  

### 24. Example – Empty Database Test
- Action:
  - GET `/`  
- Check:
  - “No entries” message  
- Purpose:
  - Verify initial state  

### 25. Helper Functions in Tests
- Example:
  - `login()`  
  - `logout()`  
- Role:
  - Simplify repeated logic  
- Not tests:
  - Names do not start with `test`  

### 26. Testing Authentication
- Scenarios:
  - Valid login  
  - Invalid username  
  - Invalid password  
- Assertions:
  - Correct messages returned  

### 27. Handling Redirects
- Option:
  - `follow_redirects=True`  
- Ensures:
  - Final response captured  

### 28. Comprehensive Testing
- Combine:
  - Fixtures  
  - Helper functions  
  - Assertions  
- Covers:
  - Multiple scenarios  

### 29. Automated Grading Use Case
- Example:
  - Checking HTML files exist  
- Tests:
  - Verify file presence  
- Application:
  - Auto-evaluation systems  

### 30. Importance of Automated Testing
- Benefits:
  - Detect regressions  
  - Improve confidence  
- Limitation:
  - 100% coverage ≠ bug-free  

### 31. Continuous Testing
- Needed for:
  - Stability  
  - Reliability  
- Process:
  - Ongoing, not one-time  

### 32. Key Takeaways
- Pytest:
  - Powerful testing framework  
- Supports:
  - Fixtures  
  - API testing  
  - Flask testing  
- Essential for:
  - Scalable, reliable applications  
---
