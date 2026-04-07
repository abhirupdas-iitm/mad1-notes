### Week 8 Lecture 1  
#### Frontend Fundamentals, Rendering Approaches, and Client-Side Processing  
##### Description: Introduces frontend concepts, browser-based applications, HTML/CSS/JavaScript roles, and compares static vs dynamic rendering approaches along with client-side computation and performance trade-offs.

### 1. Introduction to Frontend
- Frontend = **user-facing part of application**
- Can be:
  - Desktop GUI  
  - Web browser (primary focus)  
  - Embedded systems (e.g., voice assistants)  
- Users interact only with:
  - Frontend interface  

### 2. Types of Client Interfaces
- Traditional:
  - Keyboard  
  - Mouse  
  - Touchscreen  
- Modern:
  - Voice input (e.g., assistants)  
- May not always include:
  - Visual display  

### 3. Focus on Web Browsers
- Web applications rely on:
  - Browser as client  
- Browser responsibilities:
  - Render content  
  - Handle interaction  
  - Execute scripts  

### 4. UI vs UX
- **UI (User Interface):**
  - Visual elements  
- **UX (User Experience):**
  - Overall interaction quality  
- Goal:
  - Smooth, intuitive experience  

### 5. Core Frontend Technologies
- HTML:
  - Defines **content**  
- CSS:
  - Defines **presentation/style**  
- JavaScript:
  - Adds **interactivity**  

### 6. Role of JavaScript
- Initially:
  - Minor enhancements  
- Now:
  - Essential for dynamic behavior  
- Enables:
  - Responsive interfaces  
  - Real-time updates  

### 7. Risks of JavaScript
- Can be:
  - Misused easily  
- May introduce:
  - Security vulnerabilities  
  - Poor performance  

### 8. Functional Reuse in Frontend
- Reusable components:
  - Navigation bars  
  - UI widgets  
- Example:
  - Bootstrap (CSS framework)  

### 9. Performance Considerations
- Design impacts:
  - Server load  
  - Client load  
- Trade-offs must be balanced  

### 10. Security Considerations
- Frontend security is important:
  - Data exposure risks  
  - Script vulnerabilities  

### 11. Fully Static Web Pages
- Definition:
  - Pages pre-generated  
- Server behavior:
  - Simply sends files  

### 12. Characteristics of Static Pages
- No runtime processing  
- Precompiled content  
- Extremely fast  

### 13. Advantages of Static Pages
- High performance  
- Minimal server load  
- Easy scaling  

### 14. Limitations of Static Pages
- No personalization  
- Limited interactivity  
- Requires rebuild for updates  

### 15. Static Site Generators
Examples:
- Jekyll  
- Hugo  
- Next.js  
- Generate:
  - Static HTML ahead of time  

### 16. Dynamic Content Challenge
- Need:
  - User-specific data  
- Example:
  - Login systems  
  - Personalized dashboards  

### 17. Role of JavaScript in Static Sites
- Adds:
  - Dynamic updates  
- Makes:
  - Additional server requests  

### 18. Server-Side Rendering (SSR)
- Pages generated:
  - At runtime  
- Example frameworks:
  - Flask  
  - WordPress  
  - Drupal  

### 19. Advantages of SSR
- High flexibility  
- Easy content updates  
- Supports personalization  

### 20. Disadvantages of SSR
- High server load  
- Slower response time  
- Requires:
  - Database access  
  - More resources  

### 21. Database Bottleneck
- Multiple servers:
  - Depend on same database  
- Database becomes:
  - Performance bottleneck  

### 22. Caching in Dynamic Systems
- Helps reduce:
  - Server load  
- Challenges:
  - Complex implementation  
  - Not fully effective  

### 23. Client-Side Computation
- Idea:
  - Move processing to client  
- Browser:
  - Often idle  
- Opportunity:
  - Utilize client resources  

### 24. Evolution of JavaScript
- From:
  - Simple scripting  
- To:
  - Full-fledged programming language  

### 25. Component-Based Development
- Reusable UI elements  
- Modular design approach  

### 26. Node.js Concept
- JavaScript used:
  - On backend  
- Enables:
  - Full-stack JavaScript  

### 27. Rendering Approaches Comparison
#### Server-Side Rendering
- Pros:
  - Flexible  
  - Centralized control  
- Cons:
  - High server load  

#### Static Rendering
- Pros:
  - Fast  
  - Cache-friendly  
- Cons:
  - Limited interaction  

#### Hybrid Approach
- Combines:
  - Static + dynamic  
- Benefits:
  - Balanced performance  

### 28. Hybrid Model Characteristics
- Mostly static pages  
- Dynamic updates via:
  - Client-side logic  

### 29. Trade-offs in Hybrid Approach
- Reduced server load  
- Increased client complexity  
- Potential:
  - Security issues  

### 30. Client-Side Risks
- Running complex scripts:
  - May expose data  
- Requires:
  - Careful design  

### 31. Web Server Performance Example
- Static:
  - ~10,000–20,000 requests/sec  
- Dynamic:
  - ~100 requests/sec  

### 32. Reason for Performance Gap
- Static:
  - File retrieval only  
- Dynamic:
  - Script execution  
  - Database access  

### 33. Network Considerations
- Throughput limits:
  - Network bandwidth  
- Server must:
  - Match network capacity  

### 34. Scalability Challenges
- Dynamic systems:
  - Harder to scale  
- Static systems:
  - Easier to distribute  

### 35. Key Takeaways
- Frontend = user interaction layer  
- HTML, CSS, JS form core stack  
- Static vs dynamic = key trade-off  
- Client-side computation reduces server load  
- Hybrid models are widely used  
- Performance and security must be balanced

### Notes to be taken for `Activity Question 1`
1. Run-time HTML generation provides better flexibility. (Question: 1)
2. Server-side rendering can be easier to develop. (Question: 3)
3. Client-side rendering provides dynamic loading but puts less load on the server. (Question: 4)
4. Spring is not a WSGI-compatible application. (Question: 8)
---
### Week 8 Lecture 2  
#### Asynchronous Updates, AJAX, and DOM Manipulation  
##### Description: Explains asynchronous updates in web applications, introduces AJAX (Asynchronous JavaScript and XML), and covers DOM (Document Object Model) concepts for dynamic frontend manipulation.

### 1. Introduction to Frontend Rendering Approaches
- Rendering approaches:
  - Server-side rendering  
  - Static pages  
  - Hybrid (client-side + server-side)  
- Key enabler of dynamic frontend:
  - **Asynchronous updates**

### 2. Traditional Web Model
- Workflow:
  - Client sends request  
  - Server returns full HTML page  
  - Browser re-renders entire page  
- Every update:
  - Requires full page reload  

### 3. Limitations of Traditional Model
- Redundant data transfer:
  - Headers, footers sent repeatedly  
- Increased:
  - Network load  
- Poor UX:
  - Full page refresh each time  

### 4. Impact of Server-Side Rendering
- Additional server processing required  
- Slower page load times  
- More computational overhead  

### 5. Motivation for Asynchronous Updates
- Improve:
  - Speed  
  - User experience  
- Idea:
  - Update only **specific parts** of page  

### 6. Concept of Asynchronous Updates
- Load main page first  
- Fetch additional data:
  - In background  
- Update:
  - Only required section  

### 7. Example Scenario
- Selecting an animal (e.g., cat)
- Instead of:
  - Reloading entire page  
- System:
  - Fetches only animal data  
  - Updates specific section  

### 8. Structured Data Response
- Server returns:
  - Structured data (not full HTML)  
- Example fields:
  - Name  
  - Latin name  
  - Habitat  

### 9. Partial Page Updates
- Only a portion (e.g., a `div`) is updated  
- Remaining page:
  - Remains unchanged  

### 10. Introduction to AJAX
- Stands for:
  - **Asynchronous JavaScript and XML**  
- Key idea:
  - Background data fetching  

### 11. Role of XML in AJAX
- Provides:
  - Structured data format  
- Enables:
  - Easy parsing and interpretation  

### 12. Evolution Beyond AJAX
- Concept still used  
- Name less common now  
- Modern systems:
  - Use JSON instead of XML  

### 13. Benefits of Asynchronous Updates
- Faster loading  
- Better UX  
- Reduced data transfer  

### 14. Background Processing
- Asynchronous = happens:
  - Without blocking UI  
- Page renders:
  - While data is fetched  

### 15. Introduction to DOM
- DOM = **Document Object Model**  
- Represents:
  - Web page as a structured object  

### 16. Nature of DOM
- Abstract representation  
- Stored as:
  - Tree structure  

### 17. DOM Tree Structure
- Nodes represent:
  - Elements  
  - Text  
- Hierarchical organization  

### 18. DOM as Programming Interface
- Allows:
  - Accessing page elements  
- Enables:
  - Dynamic manipulation  

### 19. Parsing HTML into DOM
- Browser:
  - Converts HTML → DOM tree  
- Used internally:
  - For rendering and updates  

### 20. DOM Manipulation
- Modify:
  - Content  
  - Structure  
- Without reloading page  

### 21. Object-Oriented Approach
- DOM elements treated as:
  - Objects  
- Supports:
  - Methods and properties  

### 22. JavaScript and DOM
- JavaScript:
  - Primary language for DOM manipulation  
- Supported by:
  - All browsers  

### 23. Example: Selecting Elements
- Query elements:
  - By tag (e.g., `<p>`)  
- Returns:
  - Collection of elements  

### 24. Accessing DOM Elements
- Example:
  - `paragraphs[0]` → first element  
- Can retrieve:
  - Properties (e.g., node name)  

### 25. Document Object
- Represents:
  - Entire page  
- Entry point:
  - `document` object  

### 26. DOM API Usage
- Methods:
  - `querySelectorAll()`  
- Allows:
  - Flexible element selection  

### 27. Event Handling
- Example:
  - `window.onload`  
- Executes:
  - Code after page loads  

### 28. Anonymous Functions
- Functions without names  
- Used for:
  - Inline logic execution  

### 29. Creating Elements Dynamically
- Example:
  - Create `<h1>` element  
- Add:
  - Text nodes  

### 30. Appending Elements
- Insert elements into:
  - DOM tree  
- Example:
  - Append to `<body>`  

### 31. Dynamic Page Modification
- Page updated:
  - Without reload  
- Content:
  - Added at runtime  

### 32. DOM Update Flow
1. Create element  
2. Create text  
3. Attach text to element  
4. Insert element into DOM  

### 33. Power of DOM Manipulation
- Enables:
  - Real-time UI updates  
- Supports:
  - Interactive applications  

### 34. Programming Concepts in Frontend
- Supports:
  - Loops  
  - Conditions  
  - Object composition  

### 35. Flexibility vs Complexity
- More power:
  - More complexity  
- Risk:
  - Hard-to-maintain code  

### 36. Best Practices
- Avoid:
  - Over-complication  
- Keep:
  - Code maintainable  

### 37. Importance of UX
- Asynchronous updates:
  - Improve responsiveness  
- Users perceive:
  - Faster systems  

### 38. Modern Frontend Frameworks
- Built on:
  - DOM + asynchronous updates  
- Examples (conceptual):
  - React  
  - Angular  

### 39. Key Takeaways
- Traditional model:
  - Full page reloads  
- AJAX introduced:
  - Partial updates  
- DOM enables:
  - Dynamic manipulation  
- JavaScript:
  - Core tool for frontend logic  
- Balance:
  - Power vs complexity

### Notes to be taken for `Activity Question 2`
1. For updating a particular page in case of original web, client has to render the page again from scratch. (Question: 1)
---
### Week 8 Lecture 3  
#### Browser Capabilities, Client-Side Processing, and Frontend Evolution  
##### Description: Explores browser functionality, client-side execution, JavaScript engines, accessibility, alternative frontend approaches, and emerging technologies like WebAssembly and native-like web applications.

### 1. Role of the Browser
- Browser = **client in web architecture**  
- Primary responsibility:
  - Render HTML content  

### 2. HTML Rendering Requirements
- Browser must:
  - Display HTML meaningfully  
- Does NOT need:
  - Exact styling rules  
- Example:
  - `<h1>` → just indicates heading (not necessarily larger text)  

### 3. Minimal Browser Capabilities
- Render HTML  
- Support basic interaction  
- Handle cookies  

### 4. Cookies and Sessions
- Cookies:
  - Stored by browser  
- Used for:
  - Session management  
- Enables:
  - Authentication  
  - State persistence  

### 5. Text-Based Browsers
- Operate:
  - Without GUI  
- Features:
  - Display HTML text  
  - Limited form interaction  
- Limitations:
  - No JavaScript  
  - Minimal styling  
  - Limited media support  

### 6. Implications for Developers
- Must consider:
  - Users on limited browsers  
- Ensure:
  - Content still accessible  

### 7. Accessibility Considerations
- Follow:
  - W3C guidelines  
- Avoid:
  - Conveying meaning via color or font alone  
- Ensure:
  - Usability across devices  

### 8. Trade-offs in Accessibility
- Cannot:
  - Fully support all environments  
- Design choice:
  - Balance functionality vs accessibility  

### 9. Introduction to CSS
- CSS = **Cascading Style Sheets**  
- Used for:
  - Styling webpages  

### 10. Benefits of CSS Separation
- HTML:
  - Structure  
- CSS:
  - Presentation  
- Leads to:
  - Better design flexibility  

### 11. CSS and Accessibility
- Browsers can:
  - Ignore CSS if needed  
- Improves:
  - Adaptability  

### 12. Principle of Separation of Concerns
- Each component:
  - Handles one responsibility  
- Example:
  - HTML → structure  
  - CSS → styling  

### 13. Need for Interactivity
- Static pages:
  - Not sufficient  
- Requires:
  - Client-side logic  

### 14. JavaScript as Standard
- JavaScript = **de facto client-side language**  
- Widely supported  
- No strong alternative replacement  

### 15. Evolution of JavaScript
- Initially:
  - Limited functionality  
- Now:
  - Full DOM interaction  
  - Complex application support  

### 16. JavaScript Engines
- Execute JavaScript in browser  
- Examples:
  - V8 (Chrome)  
  - Firefox engine  
  - Safari engine  

### 17. Differences Between Engines
- Variations in:
  - Performance  
  - Memory usage  
- Mostly:
  - API-compatible  

### 18. Standardization of JavaScript
- Ensures:
  - Consistent behavior across browsers  

### 19. Client-Side Execution
- JavaScript runs on:
  - Client CPU  
- Reduces:
  - Server workload  

### 20. Performance Implications
- Heavy scripts:
  - Increase CPU usage  
- May:
  - Slow system  

### 21. GPU Utilization
- Some engines support:
  - Graphics acceleration  
- Useful for:
  - Video  
  - Rendering  

### 22. Risks of Heavy JavaScript
- Can:
  - Freeze browser  
- Extreme cases:
  - System slowdown  

### 23. Browser Safety Mechanisms
- Isolation:
  - Tabs run separately  
- Prevents:
  - System-wide crashes  

### 24. Resource Impact Awareness
- Webpages:
  - Consume energy  
- Factors:
  - Requests  
  - Data size  

### 25. Non-Human Clients
- Clients may be:
  - Machines  
- Example:
  - IoT devices  

### 26. Machine-to-Server Communication
- Uses:
  - APIs  
- Example:
  - Sensors sending data  

### 27. Benefits of Using Web Protocols
- Easier than:
  - Custom network protocols  
- Provides:
  - Standardization  
  - Integration  

### 28. API-Based Communication
- Enables:
  - Structured interaction  
- Simplifies:
  - Backend design  

### 29. Alternative Client-Side Languages
- Example:
  - Brython (Python in browser)  

### 30. How Brython Works
- Python code:
  - Translated into JavaScript  
- Executes via:
  - JS engine  

### 31. Concept of Transpilation
- Conversion:
  - One language → JavaScript  
- Combines:
  - Translation + compilation  

### 32. Limitations of Alternatives
- Still depend on:
  - JavaScript execution  

### 33. Introduction to WebAssembly (WASM)
- Binary instruction format  
- Runs in:
  - Browser  

### 34. Features of WebAssembly
- High performance  
- Near-native execution  
- Supports:
  - Graphics  
  - Complex apps  

### 35. Use Cases of WebAssembly
- Heavy applications:
  - Office tools  
  - 3D editing  

### 36. Limitations of WebAssembly
- Complexity  
- Limited adoption  

### 37. Compilation to WASM
- Tools:
  - Emscripten  
- Converts:
  - C/C++ → WebAssembly  

### 38. Future of Frontend
- Increasing:
  - Capability  
  - Performance  

### 39. Native Mode Concept
- Web apps behave like:
  - Native applications  

### 40. Native Features
- Access to:
  - Files  
  - Camera  
  - System APIs  

### 41. Security Restrictions
- Direct access limited due to:
  - Security concerns  

### 42. Controlled Access via APIs
- User permissions required  
- Enables:
  - Safe interaction  

### 43. Hybrid Applications
- Combine:
  - Web + native features  

### 44. Example: VS Code
- Built using:
  - Web technologies  
- Runs like:
  - Desktop application  

### 45. Advantages of Native-like Web Apps
- Cross-platform  
- Easier deployment  

### 46. Key Takeaways
- Browser:
  - Powerful execution environment  
- JavaScript:
  - Core frontend engine  
- Alternatives:
  - Exist but rely on JS  
- WebAssembly:
  - Future potential  
- Design must consider:
  - Performance  
  - Accessibility  
  - Security

### Notes to be taken for `Activity Question 3`
1. `Emscripten` is a compiler framework that can compile C or C++ directly into Web assembly. (Question: 3)
2. `WebAssembly` is designed to run along with JavaScript. (Question: 7)
---
### Week 8 Lecture 4  
#### Client-Side Computation, Validation, and Security Implications  
##### Description: Covers client-side validation techniques, JavaScript-based validation, CAPTCHA systems, advanced client-side computation, and associated security risks including sandboxing and denial-of-service scenarios.

### 1. Client-Side Computation
- Refers to:
  - Processing done in the browser  
- Enhances:
  - Performance  
  - User experience  

### 2. Importance of Validation
- Ensures:
  - Correct data before processing  
- Types:
  - Client-side validation  
  - Server-side validation  

### 3. Server-Side Validation (Critical)
- Must always be performed  
- Prevents:
  - Invalid data reaching database  
- Final safeguard  

### 4. Role of Client-Side Validation
- Reduces:
  - Unnecessary server requests  
- Handles:
  - User mistakes early  

### 5. Benefits of Client-Side Validation
- Faster feedback  
- Better UX  
- Reduced network traffic  

### 6. Limitation of Client-Side Validation
- Can be bypassed  
- Not secure alone  

### 7. Common Validation Examples
- Email format  
- Date fields  
- Input sanitization  

### 8. HTML5 Built-in Validation
- Features:
  - Required fields  
  - Min/Max length  
  - Numeric ranges  

### 9. Browser-Level Validation
- Automatically handled by:
  - Browser  
- Prevents:
  - Invalid submissions  

### 10. Validation Attributes
- Examples:
  - `required`  
  - `minlength`  
  - `maxlength`  
  - `min`, `max`  

### 11. Pattern Matching
- Uses:
  - Regular expressions  
- Enables:
  - Complex validation  

### 12. Compatibility Concerns
- Older browsers:
  - May not support features  
- Developer decision:
  - Support vs ignore  

### 13. Role of Frameworks
- Provide:
  - Cross-browser compatibility  
- Trade-off:
  - Increased complexity  

### 14. JavaScript-Based Validation
- More powerful than HTML5  
- Allows:
  - Custom logic  

### 15. Constraint Validation API
- Enables:
  - Advanced validation rules  
- Works via:
  - JavaScript  

### 16. Example Validation Flow
- Select input field via DOM  
- Add event listener  
- Check validity  
- Show custom message  

### 17. Custom Error Messages
- Improves:
  - User clarity  
- Overrides:
  - Default browser messages  

### 18. Event-Driven Validation
- Triggered by:
  - Input events  
- Allows:
  - Real-time validation  

### 19. CAPTCHA Concept
- Purpose:
  - Distinguish human vs bot  

### 20. Need for CAPTCHA
- Prevent:
  - Automated abuse  
- Example:
  - Ticket booking systems  

### 21. CAPTCHA Mechanism
- Tracks:
  - Mouse movement  
  - Typing patterns  

### 22. reCAPTCHA Example
- Simple checkbox:
  - “I am not a robot”  
- May escalate to:
  - Image selection  

### 23. Behavioral Analysis
- Detects:
  - Human-like interaction  

### 24. Privacy Concerns
- Tracks:
  - User behavior  
- Raises:
  - Data concerns  

### 25. Advanced Client-Side Computation
- Includes:
  - Complex scripts  
  - Data processing  

### 26. Crypto Mining via Browser
- Possible using:
  - JavaScript  
- Uses:
  - Client CPU  

### 27. Ethical Concerns
- Unauthorized computation:
  - Considered malicious  
- Can lead to:
  - Blacklisting  

### 28. JavaScript Power
- Near-native performance  
- Access to:
  - CPU  
  - GPU  

### 29. Background Processing
- Uses:
  - Asynchronous calls  
- User may be:
  - Unaware  

### 30. Security Implications
- Major concern:
  - Executing external scripts  

### 31. Risk of Data Theft
- Malicious scripts may:
  - Access sensitive data  

### 32. Sandboxing Concept
- Restricts:
  - JavaScript access  
- Prevents:
  - Unauthorized operations  

### 33. Sandbox Limitations
- Cannot access:
  - Local files  
  - System resources  

### 34. Denial-of-Service (DoS) Attacks
- Overloads:
  - Server with requests  
- Caused by:
  - Malicious scripts  

### 35. Distributed Attacks
- Many clients:
  - Send requests simultaneously  
- Impact:
  - Server crash  

### 36. Client-Side Resource Abuse
- Scripts may:
  - Consume CPU heavily  
- Result:
  - System slowdown  

### 37. Browser Protection Mechanisms
- Detect:
  - High resource usage  
- Action:
  - Prompt user / kill script  

### 38. Malicious Script Injection
- Replace:
  - Popular JS files  
- Trigger:
  - Hidden attacks  

### 39. Native Resource Access
- Includes:
  - Camera  
  - Sensors  
  - Storage  

### 40. Security Restrictions
- Access requires:
  - User permission  

### 41. Trusted Applications
- Installed locally  
- Gain:
  - Extended access  

### 42. Native Integration
- Web apps can:
  - Use OS APIs  
- Improves:
  - Performance  

### 43. Hybrid Applications
- Combine:
  - Web + native capabilities  

### 44. Core Takeaways
- Client-side computation:
  - Enhances UX  
- Validation:
  - Must be dual-layered  
- JavaScript:
  - Powerful but risky  
- Security:
  - Critical concern  
- Always:
  - Validate on server side

### Notes to be taken for `Activity Question 4`
1. Client-side validation can reduce the number of hits on server. (Question: 1)
2. Client-side validation helps in reducing the number of hits on the server. (Question: 2)
3. CAPTCHA stands for Completely Automatic Public Turing `**test**` to tell Computers and Humans Apart. (Question: 5)
---
[[Extra Notes from supplementary content of Week 8]]
