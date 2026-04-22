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
