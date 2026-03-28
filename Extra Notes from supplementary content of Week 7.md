### Week 7 Extra Lecture 1  
#### Developer Logging in Flask Applications  
##### Description: Explains developer logging in Flask applications. Covers differences between print statements and logging, logging levels, configuring logs, writing logs to files, and advanced logging handlers.

### 1. Introduction to Debugging in Applications
- During development:
  - Developers frequently check:
    - Returned data  
    - Object values  
    - Flow of execution  
- Common approach:
  - Use `print` statements  

### 2. Problems with Print Statements
- Simple and easy to use  
- But:
  - Becomes **unmanageable** in large applications  
  - Hard to track:
    - Order of execution  
    - Source of logs  
- No control over:
  - Format  
  - Destination  
  - Severity  

### 3. Need for Logging
- Logging provides:
  - Better control over output  
  - Structured debugging  
- Allows:
  - Sending logs to:
    - Console  
    - Files  
    - Email  
- Helps in:
  - Debugging  
  - Monitoring  
  - Maintenance  

### 4. Logging Levels
Logging supports severity levels:

- DEBUG → lowest level (detailed debugging info)  
- INFO → general information  
- WARNING → potential issues  
- ERROR → errors in execution  
- CRITICAL → system-level failures  

Usage:
- DEBUG/INFO → development  
- ERROR/CRITICAL → production alerts  

### 5. Flask Logging Support
- Flask provides:
  - Built-in logger (`app.logger`)  
- No configuration needed initially  
- Can directly use:
  - `app.logger.debug()`  
  - `app.logger.info()`  

### 6. Replacing Print with Logging
Instead of:
- `print(data)`  

Use:
- `app.logger.debug(data)`  

Advantages:
- Structured output  
- Includes metadata:
  - Timestamp  
  - Log level  
  - Source location  

### 7. Benefits of Structured Logs
- Logs contain:
  - Time of execution  
  - Log severity  
  - File/line reference  
- Helps:
  - Trace execution sequence  
  - Identify issues faster  

### 8. Logging Output Destinations
Logs can be directed to:
- Console (default)  
- File  
- Email  
- External systems  

Default in Flask:
- Console output  

### 9. Logging to a File
- Configure logging using Python logging module  

Steps:
1. Import logging  
2. Configure:
   - File name (`debug.log`)  
   - Format  
3. Logs stored in file instead of console  

Result:
- Console → minimal output  
- File → complete logs  

### 10. Advantages of File Logging
- Easy to:
  - Share logs (zip & send)  
  - Persist logs for analysis  
- Better than:
  - Scrolling console output  

### 11. Logging Configuration
- Controlled using:
  - `logging.basicConfig()`  
- Configurable parameters:
  - File name  
  - Format  
  - Log level  

### 12. Advanced Logging (dictConfig)
- Flask supports:
  - `dictConfig`  
- Enables:
  - Complex configurations  
- Allows:
  - Multiple handlers  

### 13. Logging Handlers
Handlers define where logs go:

Examples:
- Stream handler → console  
- File handler → log file  
- Email handler → alerts  

### 14. Multi-Handler Logging
- Different logs handled differently:
  - DEBUG → file  
  - ERROR → email  
- Improves:
  - Monitoring  
  - Alert systems  

### 15. Real-World Logging Strategy
Typical setup:
- DEBUG logs → file  
- INFO logs → console  
- ERROR/CRITICAL → email alerts  

### 16. Logging Best Practices
- Avoid excessive print statements  
- Use logging from early stages  
- Use appropriate log levels  
- Keep logs structured  

### 17. When to Use Critical Logs
Used for:
- System failures  
- Database downtime  
- Application crashes  

Action:
- Trigger alerts (e.g., email)  

### 18. Debugging Workflow with Logs
1. Add logging statements  
2. Run application  
3. Observe logs:
   - Console or file  
4. Identify issues  

### 19. Importance in Large Applications
- Logging becomes essential when:
  - Application grows  
  - Multiple modules exist  
- Helps:
  - Maintain clarity  
  - Debug faster  

### 20. Key Takeaways
- Logging is superior to print debugging  
- Provides:
  - Structure  
  - Flexibility  
  - Control  
- Flask offers built-in logging support  
- Logs can be routed to:
  - Console  
  - Files  
  - External systems  
- Essential for scalable application development
---
### Week 7 Extra Lecture 2  
#### Debugging Flask Applications (Debug Mode, PDB, Flask Shell)  
##### Description: Explains multiple methods for debugging Flask applications including debug mode, interactive debugger, Python debugger (PDB), and Flask shell for inspecting application state.

### 1. Introduction to Debugging
- Debugging is essential when:
  - Errors occur  
  - Unexpected behavior happens  
- Example issue:
  - Division by zero error  
- Goal:
  - Identify where and why error occurs  

### 2. Enabling Debug Mode in Flask
- Debug mode helps:
  - Display detailed error information  
- Enable using:
  - `app.run(debug=True)`  
  - OR config variable  

### 3. Debug Mode Behavior
- When enabled:
  - Shows detailed error page  
  - Displays:
    - Stack trace  
    - Code location  
    - Variable context  
- Also shows:
  - Debugger PIN  
  - Debugger status  

### 4. Why Debug Mode is Dangerous in Production
- Exposes:
  - Internal code  
  - Application structure  
- Allows:
  - Code execution via debugger console  
- Risk:
  - Security vulnerability  

### 5. Interactive Debugger (Browser Console)
- Flask provides:
  - Built-in interactive debugger  
- Features:
  - Run Python code in app context  
  - Inspect variables  

### 6. Debugger PIN Protection
- Required to:
  - Access interactive console  
- Provides:
  - Basic security  
- Not strong enough for production  

### 7. Inspecting Variables in Debugger
- Example:
  - Check variable values  
- Helps:
  - Identify incorrect inputs  
- Can:
  - Execute Python expressions  

### 8. Dumping Context
- Use:
  - `dump()`  
- Displays:
  - All available variables  
- Useful for:
  - Understanding application state  

### 9. Debugging Workflow (Flask Debug Mode)
1. Enable debug mode  
2. Trigger error  
3. View stack trace  
4. Inspect variables  
5. Fix issue  

### 10. Python Debugger (PDB)
- Alternative debugging method  
- Works for:
  - Any Python application  

### 11. Starting PDB
Two approaches:

1. Run program with debugger:
   - `python -m pdb app.py`  

2. Insert breakpoint:
   - `import pdb`  
   - `pdb.set_trace()`  

### 12. Breakpoints in Code
- Code execution:
  - Pauses at breakpoint  
- Allows:
  - Step-by-step execution  

### 13. PDB Commands
Common commands:
- `h` → help  
- `n` → next line  
- `c` → continue  
- Step execution control  

### 14. Identifying Errors with PDB
- Example:
  - Division by zero  
- Observations:
  - Execution stops  
  - Error message displayed  

### 15. Stepping Through Code
- Allows:
  - Line-by-line execution  
- Helps:
  - Trace logic  
  - Identify faulty operations  

### 16. Continuing Execution
- Use:
  - `c` command  
- Resumes:
  - Normal program flow  

### 17. Flask Shell
- Provides:
  - Interactive Python shell  
- Runs in:
  - Flask app context  

### 18. Setting Up Flask Shell
Required:
- Set environment variables:
  - `FLASK_ENV=development`  
  - `FLASK_APP=main.py`  

Run:
- `flask shell`  

### 19. Using Flask Shell
- Can:
  - Execute queries  
  - Access database  
  - Inspect models  

### 20. Example: Query Debugging
- Run database queries  
- Inspect:
  - Returned objects  
  - Query structure  

### 21. Inspecting Query Results
- Use:
  - `.all()` → list of objects  
- Access:
  - Individual elements  
- Example:
  - `articles[0].title`  

### 22. Benefits of Flask Shell
- Test logic without UI  
- Debug database interactions  
- Explore application state  

### 23. Multiple Debugging Methods
Available methods:
- Flask debug mode  
- Interactive debugger  
- Python debugger (PDB)  
- Flask shell  

### 24. Choosing Debugging Method
Depends on:
- Type of issue  
- Level of control required  

### 25. Best Practices
- Use debug mode:
  - Only in development  
- Use PDB:
  - For deep debugging  
- Use shell:
  - For testing queries  

### 26. Key Takeaways
- Debugging is critical for development  
- Flask provides multiple debugging tools  
- Debug mode is powerful but unsafe for production  
- PDB allows step-by-step debugging  
- Flask shell enables context-based inspection  
- Use the right tool based on problem complexity
---
