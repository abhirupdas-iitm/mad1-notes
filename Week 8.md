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
1. Registers are located on the CPU. (Question: 1)
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
1. Registers are located on the CPU. (Question: 1)
---