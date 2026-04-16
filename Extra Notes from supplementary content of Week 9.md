### Week 9 Extra Lecture 1  
#### JavaScript in Web Applications – Events, Validation, Fetch API, and DOM Manipulation  
##### Description: Introduces practical usage of JavaScript in web applications. Covers client-side validation, event handling, form submission control, Fetch API for asynchronous requests, and DOM manipulation for dynamic UI updates.

### 1. Introduction to JavaScript in Web Applications
- JavaScript:
  - Large ecosystem (browser + server-side like Node.js)  
- Focus in this lecture:
  - Client-side JavaScript with Flask  
- Learning approach:
  - Use-based learning (practical usage) :contentReference[oaicite:0]{index=0}  

### 2. Key JavaScript Concepts Covered
- Events  
- DOM manipulation  
- Fetch API  

### 3. Including JavaScript in Web Apps
- Two methods:
  - Inline script in HTML  
  - External JS file  
- Preferred:
  - External file (reusability)  

### 4. Building a Feedback Form
- Fields:
  - Email  
  - Subject  
  - Feedback content  
- Uses:
  - HTML form  
  - Flask route handling GET and POST  

### 5. Basic Form Submission Behavior
- Default:
  - Form submits even if empty  
- Problem:
  - No validation  

### 6. HTML-Based Validation
- Use:
  - `required` attribute  
- Effect:
  - Prevents empty submission  
- Limitation:
  - Limited control  

### 7. Need for Custom Validation
- Example:
  - Email must contain `@`  
- Solution:
  - JavaScript validation  

### 8. Event Handling in JavaScript
- Event:
  - `onsubmit`  
- Flow:
  - Capture event  
  - Validate input  
  - Allow/block submission  

### 9. Writing Validation Function
- Steps:
  - Get input value  
  - Check condition  
  - If invalid:
    - Stop submission (`event.preventDefault()`)  
    - Show error  
- If valid:
  - Allow submission  

### 10. Client-Side vs Server-Side Validation
- Client-side:
  - Faster response  
  - Better UX  
- Server-side:
  - Mandatory for security  
- Best practice:
  - Use both  

### 11. Server-Side Validation
- Implemented in:
  - Flask controller  
- Logic:
  - Check input  
  - Return error if invalid  
- UI:
  - Show error message in template  

### 12. JavaScript Events Overview
- Examples:
  - Click  
  - Submit  
  - Input change  
- Used for:
  - User interaction handling  

### 13. Adding Interactive Feature (Like Button)
- Goal:
  - Like an article  
- Requirement:
  - No page reload  

### 14. Problem with Traditional Approach
- Form submission:
  - Reloads page  
- Solution:
  - AJAX-style request  

### 15. Fetch API Introduction
- Used for:
  - Sending asynchronous requests  
- Syntax:
  - `fetch(url)`  
- Handles:
  - Response and errors  

### 16. Adding Click Event Dynamically
- Use:
  - `querySelectorAll()`  
- Select elements:
  - Based on class  
- Loop through:
  - Attach event listeners  

### 17. Initializing Event Listeners
- Function:
  - `initialize()`  
- Called:
  - After page load  
- Purpose:
  - Setup event bindings  

### 18. Handling Click Event
- On click:
  - Call function (e.g., sendLike)  
- Access element:
  - `event.target`  

### 19. Using Data Attributes
- Add:
  - `data-article_id` in HTML  
- Access in JS:
  - `element.dataset.article_id`  
- Purpose:
  - Pass dynamic data  

### 20. Sending Data to Server
- Use:
  - Fetch API  
- Endpoint:
  - `/article_like/<article_id>`  
- Method:
  - GET/POST  

### 21. Handling Server Response
- On success:
  - Process response  
- On error:
  - Handle failure  

### 22. DOM Manipulation
- Create element:
  - `document.createElement()`  
- Add content:
  - `innerHTML`  
- Insert into page:
  - `append()`  

### 23. Showing Feedback to User
- Example:
  - “Thank you for liking”  
- Display:
  - Without page reload  

### 24. Parent vs Child Node Handling
- Problem:
  - Adding inside clickable element triggers re-click  
- Solution:
  - Append to parent node  

### 25. Dynamic UI Updates
- Benefits:
  - Faster interaction  
  - Better UX  
- No reload required  

### 26. Full Flow Summary
1. User clicks icon  
2. Event triggered  
3. JS captures event  
4. Fetch request sent  
5. Server processes  
6. Response returned  
7. DOM updated  

### 27. Advantages of JavaScript Integration
- Real-time updates  
- Reduced server load  
- Improved user experience  

### 28. Advanced JavaScript Ecosystem
- Frameworks:
  - Vue  
  - React  
- Capabilities:
  - Single Page Applications (SPA)  

### 29. Use Case in This Lecture
- Not full JS app  
- Only:
  - Enhancing Flask app  

### 30. Key Takeaways
- Use JavaScript for:
  - Validation  
  - Event handling  
  - Async requests  
  - UI updates  
- Always combine:
  - Client-side + server-side validation  
- Fetch + DOM manipulation:
  - Core for dynamic web apps  
---
