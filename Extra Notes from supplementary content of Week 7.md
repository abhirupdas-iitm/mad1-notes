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
- Essential for scalable application development :contentReference[oaicite:0]{index=0}
---
