### Week 11 Lecture 1  
#### Beyond HTML – Evolution of Markup Languages and the Need for JavaScript 
##### Description: Explains the evolution of markup languages leading to HTML5. Covers SGML, HTML, XML, XHTML, and the need for extending HTML using JavaScript and custom elements for modern dynamic web applications.

### 1. Introduction to Beyond HTML
- Focus:
  - What comes after basic HTML/CSS  
- Modern applications:
  - More dynamic  
  - More interactive  
- Goal:
  - Understand future directions of web development  

### 2. Importance of Concepts over Frameworks
- No single “best” framework  
- Developers have:
  - Different coding styles  
- Approach:
  - Learn fundamental concepts  
  - Evaluate tools based on understanding  

### 3. HTML is Not a Programming Language
- HTML:
  - Markup language  
- Limitations:
  - No control flow  
  - No loops or conditions  
- Purpose:
  - Structure content  

### 4. Need for Evolution
- Increasing requirements:
  - Dynamic UI  
  - Better interactivity  
- Motivation:
  - Extend HTML capabilities  

### 5. What is a Markup Language?
- Concept:
  - Add tags to text  
- Purpose:
  - Provide additional meaning  
- Used by:
  - Humans  
  - Machines  

### 6. Origin of Markup Languages
- Started:
  - 1960s  
- Used for:
  - Typesetting  
  - Document management  
- Example:
  - IBM document systems  

### 7. Problems in Early Markup Systems
- No standardization  
- Different audiences:
  - Publishers  
  - Programmers  
  - Academics  
- Different outputs:
  - Print  
  - Electronic formats  
- Machine readability:
  - Needed structured meaning  

### 8. Introduction to SGML
- Full form:
  - Standard Generalized Markup Language  
- Type:
  - Meta-language  
- Purpose:
  - Define other markup languages  

### 9. SGML Characteristics
- Declarative:
  - Define structure, not processing  
- Rigorous:
  - Strict rules  
- Can represent:
  - Complex data structures  

### 10. Document Type Definition (DTD)
- Defines:
  - Allowed tags  
  - Structure  
- Used to:
  - Create specific applications of SGML  

### 11. SGML Applications
- Each application:
  - Has its own tags  
  - Own interpretation rules  
- Enables:
  - Flexible document design  

### 12. Declarative vs Imperative Concept
- Declarative:
  - Specify what is needed  
- Imperative:
  - Specify how to do it  
- Advantage:
  - Higher abstraction  

### 13. Limitations of SGML
- Too complex  
- Difficult to:
  - Implement  
  - Understand  
- Led to:
  - Simpler alternatives  

### 14. HTML as an SGML Application
- Designed by:
  - Tim Berners-Lee  
- Intended:
  - Subset of SGML  
- Focus:
  - Simplicity  

### 15. HTML Parsing Behavior
- Lenient:
  - Forgives errors  
- Examples:
  - Missing closing tags allowed  
- Result:
  - Not strict SGML  

### 16. HTML Evolution Challenges
- Need:
  - Backward compatibility  
- Problem:
  - Cannot break existing pages  

### 17. HTML Versions
- HTML 2.0:
  - Attempt at SGML compliance  
- HTML 4:
  - Closer to SGML  
- Issue:
  - Legacy support limits strictness  

### 18. HTML5 Breakthrough
- Not SGML-based  
- Defines:
  - Own parsing rules  
- Goal:
  - Balance flexibility + structure  

### 19. Introduction to XML
- Full form:
  - Extensible Markup Language  
- Based on:
  - SGML  
- Focus:
  - Simplicity  
  - Usability  

### 20. XML Features
- Custom tags allowed  
- Human + machine readable  
- Strict structure  
- Supports:
  - Complex data relationships  

### 21. XML Use Cases
- Data exchange  
- Document formats  
- Examples:
  - RSS feeds  
  - SVG graphics  
  - DOCX, ODT files  

### 22. RSS Example Concept
- Purpose:
  - Content syndication  
- Structure:
  - Channel → items  
- Used for:
  - Blog updates  

### 23. SVG Example Concept
- XML-based graphics  
- Supports:
  - Shapes  
  - Text  
- Used for:
  - Scalable visuals  

### 24. XML vs JSON
- Both:
  - Data representation formats  
- XML:
  - More structured  
- JSON:
  - Simpler  
- Choice:
  - Depends on use case  

### 25. XHTML Introduction
- Based on:
  - XML  
- Reformulation of:
  - HTML4  
- Goal:
  - Clean structure  

### 26. XHTML Features
- Strict syntax  
- Uses:
  - XML namespaces  
- Advantage:
  - Better modularity  

### 27. XHTML Limitations
- Too restrictive  
- Hard to extend  
- Not ideal for evolving web needs  

### 28. HTML5 Objectives
- Add:
  - Multimedia support  
  - Canvas  
- Maintain:
  - Simplicity  
  - Backward compatibility  

### 29. HTML5 Key Decision
- Break from:
  - SGML and XML  
- Define:
  - Own parsing system  

### 30. HTML Living Standard
- Maintained by:
  - WHATWG  
- Characteristics:
  - Continuously updated  
- No fixed versioning  

### 31. Extension Problem
- Need:
  - New features  
  - New tags  
- Challenge:
  - Avoid modifying standard constantly  

### 32. Software-Defined Approach
- Solution:
  - Extend via code  
- Mechanism:
  - JavaScript  

### 33. Custom Elements Concept
- Define:
  - New HTML tags  
- Done using:
  - JavaScript APIs  
- Supported by:
  - Browsers  

### 34. Power of Custom Elements
- Enables:
  - Arbitrary functionality  
- No need:
  - Standard-level changes  

### 35. Problems with Custom Elements
- Anyone can define tags  
- Issues:
  - Lack of standard semantics  

### 36. Semantic Importance
- Search engines rely on:
  - Tag meaning  
- Custom tags:
  - Hard to interpret  

### 37. Impact on Search Engines
- Standard tags:
  - Provide structure  
- Custom tags:
  - Reduce machine understanding  

### 38. Role of JavaScript
- Required for:
  - Extending HTML  
- Acts as:
  - Behavior layer  

### 39. Key Insight
- HTML alone:
  - Not sufficient  
- JavaScript:
  - Enables dynamic functionality  

### 40. Key Takeaways
- Markup evolution:
  - SGML → HTML → XML → XHTML → HTML5  
- HTML5:
  - Flexible, independent standard  
- JavaScript:
  - Essential for modern web  
- Future:
  - Dynamic, extensible applications  

### Notes to be taken for `Activity Question 1`
1. 
---
### Week 11 Lecture 2  
#### Introduction to JavaScript – Language Features and DOM Interaction  
##### Description: Provides an overview of JavaScript as a high-level, multi-paradigm language. Covers dynamic typing, functional and event-driven paradigms, DOM manipulation, and how JavaScript enables interactivity in web applications.

### 1. Introduction to JavaScript
- Not a full tutorial  
- Focus:
  - Capabilities  
  - Purpose  
  - Role in web development

### 2. What is JavaScript?
- High-level programming language  
- Similar to:
  - Python  
- Used primarily:
  - In web browsers  

### 3. Levels of Programming Languages
- Low-level:
  - Assembly (machine instructions)  
- Mid-level:
  - C (memory control, pointers)  
- High-level:
  - Python, JavaScript  
- Higher level:
  - More abstraction  

### 4. Features of High-Level Languages
- Dynamic typing  
- Abstract data types  
- Easier syntax  
- Less hardware interaction  

### 5. JavaScript Characteristics
- Dynamic typing  
- Object-oriented (prototype-based)  
- Supports:
  - Arrays  
  - Dictionaries (maps)  

### 6. Complex Data Structures
- Using objects and references:
  - Trees  
  - Graphs  
- Flexible data modeling  

### 7. Multi-Paradigm Nature
- Supports multiple programming styles:
  - Imperative  
  - Functional  
  - Event-driven  

### 8. Imperative Programming
- Step-by-step execution  
- Functions called sequentially  
- Example:
  - Traditional C-style programming  

### 9. Functional Programming
- Based on:
  - Mathematical functions  
- Features:
  - Functions as first-class objects  
  - Higher-order functions  
- Benefits:
  - Cleaner abstraction  
  - Powerful composition  

### 10. Event-Driven Programming
- Code responds to events  
- Events:
  - Click  
  - Input  
  - Selection  
- Functions triggered automatically  

### 11. Importance of Event-Driven Model
- Ideal for:
  - GUI systems  
  - Web pages  
- User interaction:
  - Drives execution flow  

### 12. Ease of Learning
- Similar to Python  
- Beginner-friendly  
- Widely used  

### 13. Java vs JavaScript
- No direct relationship  
- Only similarity:
  - Some syntax  
- JavaScript closer to:
  - Python in usage style  

### 14. Why JavaScript is Needed
- Browsers include:
  - JavaScript engines  
- Enables:
  - Interactive web pages  
- Became:
  - Essential for web  

### 15. No Native I/O
- Cannot:
  - Directly read/write files  
- Uses:
  - APIs for I/O  

### 16. Role of APIs
- Provide functionality:
  - File access (controlled)  
  - Network operations  
  - Data handling  

### 17. Built-in Capabilities
- String manipulation  
- Date handling  
- Regular expressions  
- Data structures  

### 18. DOM (Document Object Model)
- Represents:
  - Web page structure  
- JavaScript can:
  - Modify DOM  
- Enables:
  - Dynamic updates  

### 19. Power of DOM Manipulation
- Change content dynamically  
- Update UI without reload  
- Core feature of modern web  

### 20. Three Pillars of Web
- HTML:
  - Structure  
- CSS:
  - Styling  
- JavaScript:
  - Behavior  

### 21. Example – Selecting Elements
- Use:
  - `document.querySelector()`  
- Purpose:
  - Access HTML elements  

### 22. Variable Declaration
- `const`:
  - Constant value  
- `let`:
  - Block-scoped variable  

### 23. Event Listener Example
- `addEventListener()`  
- Binds:
  - Event → function  
- Example:
  - Click event  

### 24. Function Definition
- Syntax:
  - `function name() { }`  
- Similar to:
  - Python `def`  

### 25. Example – Updating Text
- Prompt user input  
- Update:
  - `textContent`  
- Result:
  - Dynamic content change  

### 26. Interactive Behavior
- Clicking element:
  - Triggers function  
- Page updates:
  - Without reload  

### 27. Creating Elements Dynamically
- Use:
  - `document.createElement()`  
- Add to DOM:
  - `appendChild()`  

### 28. Button Interaction Example
- Button click:
  - Calls function  
- Function:
  - Adds new paragraph  

### 29. Repeated Interaction
- Multiple clicks:
  - Add multiple elements  
- Demonstrates:
  - Dynamic UI building  

### 30. Anonymous Functions
- Functions without name  
- Used for:
  - Inline logic  
- Common in:
  - Event handling  

### 31. Direct Event Assignment
- Example:
  - `onclick = function()`  
- Alternative to:
  - addEventListener  

### 32. DOM Modification vs Source Code
- Changes:
  - Visible in browser  
- Not present in:
  - Original HTML source  

### 33. Developer Tools
- Inspect page:
  - View DOM structure  
- Helps:
  - Debug UI changes  

### 34. Browser Developer Tools Access
- Found in:
  - Browser menu  
- Includes:
  - Elements inspector  
  - Console  

### 35. Variables in JavaScript
- Declare:
  - var / let / const  
- Differences:
  - Scope and mutability  

### 36. Basic Syntax Elements
- Comments:
  - `//`  
  - `/* */`  
- Operators:
  - +, -, *, /  

### 37. Conditional Statements
- Example:
  - if-else  
- Controls:
  - Program flow  

### 38. Functions Recap
- Define logic  
- Reusable code blocks  
- Accept parameters  

### 39. Events Recap
- Core concept:
  - User interaction triggers code  
- Examples:
  - Click  
  - Input  

### 40. Learning Resources
- Mozilla Developer Network (MDN)  
- Online tutorials  
- Practice-based learning  

### 41. Best Way to Learn JavaScript
- Write code  
- Experiment  
- Build small projects  

### 42. Key Takeaways
- JavaScript:
  - High-level, multi-paradigm language  
- Enables:
  - Interactivity  
  - Dynamic web pages  
- Core strength:
  - DOM manipulation  
- Learning approach:
  - Practice-driven  
---
### Week 11 Lecture 3  
#### Custom Elements and Web Components in HTML5 using JavaScript  
##### Description: Explains how JavaScript enables the creation of custom HTML elements. Covers limitations of HTML, custom elements API, Shadow DOM, HTML templates, and the concept of reusable web components.

### 1. Need for JavaScript in HTML
- HTML limitation:
  - Fixed set of elements  
- Requirement:
  - Extend functionality  
- Solution:
  - Use JavaScript to define custom elements  

### 2. What are Custom Elements?
- User-defined HTML tags  
- Example:
  - `<my-button>`  
- Problem:
  - Browser does not understand meaning automatically  

### 3. Semantic Limitation
- Custom tag names:
  - No inherent meaning  
- Browser cannot infer:
  - Type (button, heading, etc.)  
- Leads to:
  - Ambiguity  

### 4. Role of JavaScript in Custom Elements
- Defines:
  - Behavior  
  - Rendering  
- Controls:
  - How element appears on screen  

### 5. Elements and State
- Elements can have:
  - Internal state  
- Example:
  - Checkbox → checked/unchecked  
- Custom elements:
  - Can define own state  

### 6. Managing State
- JavaScript used to:
  - Store state  
  - Update state  
  - Use state in rendering  

### 7. Types of Custom Elements
- Extend existing elements  
- Create autonomous elements:
  - Fully independent tags  

### 8. HTML Living Standard
- Defines:
  - Custom elements specification  
- Characteristics:
  - Continuously updated  
- Sections:
  - Include custom elements API  

### 9. Normative vs Non-Normative
- Normative:
  - Official standard  
- Non-normative:
  - Subject to change  
- Living standard:
  - Frequently updated  

### 10. Custom Elements API
- Provided by:
  - Browser (JavaScript)  
- Used to:
  - Define new tags  

### 11. Example – Custom Element Definition
- Create class:
  - Extends HTMLElement  
- Define behavior:
  - Attributes  
  - Rendering logic  

### 12. Registering Custom Elements
- Use:
  - `customElements.define()`  
- Maps:
  - Tag name → class  

### 13. Example – Flag Icon
- Custom tag:
  - `<flag-icon>`  
- Behavior:
  - Display country flag  
- Logic:
  - Fetch image  
  - Render  

### 14. Rendering Responsibility
- Developer defines:
  - What appears on screen  
- Browser:
  - Executes logic  

### 15. Limitation of Raw Custom Elements
- Difficult to manage:
  - Styling  
  - Structure  
- Need:
  - Better abstraction  

### 16. Introduction to Web Components
- Built on:
  - Custom elements  
- Adds:
  - More structure  
- Goal:
  - Simplify usage  

### 17. Components of Web Components
- Custom Elements  
- Shadow DOM  
- HTML Templates  

### 18. Custom Elements Recap
- Define:
  - New HTML tags  
- Provide:
  - Functionality  

### 19. Shadow DOM Concept
- Encapsulation mechanism  
- Separates:
  - Component styling  
  - Global styling  

### 20. Purpose of Shadow DOM
- Prevent:
  - Style conflicts  
- Restrict:
  - Scope of CSS  

### 21. Example – Style Isolation
- Style applied inside component:
  - Does not affect page  
- External styles:
  - Do not affect component  

### 22. Encapsulation Benefit
- Self-contained components  
- Predictable behavior  

### 23. HTML Templates
- Define:
  - Reusable structure  
- Tags:
  - `<template>`  
  - `<slot>`  

### 24. Template Functionality
- Acts like:
  - Blueprint  
- Allows:
  - Reuse of UI patterns  

### 25. Dynamic Rendering with Templates
- Data inserted into:
  - Template structure  
- Example:
  - Book title + author  

### 26. Template Switching Example
- Change template:
  - Changes display format  
- Same data:
  - Different representation  

### 27. Combining Web Component Features
- Custom elements:
  - Structure  
- Shadow DOM:
  - Styling isolation  
- Templates:
  - Rendering logic  

### 28. Example – Basic Custom Component
- Define:
  - `<my-component>`  
- Behavior:
  - Replace content  
- Output:
  - Render predefined text  

### 29. Reusability of Components
- Same component:
  - Used multiple times  
- Behavior:
  - Consistent across page  

### 30. Example – Dynamic Content Rendering
- Replace inner HTML  
- Multiple instances:
  - Render independently  

### 31. Shadow DOM Example
- Modify:
  - Component style  
- Result:
  - Local change only  

### 32. Avoiding Global Side Effects
- Shadow DOM ensures:
  - Isolation  
- No unintended changes  

### 33. Template Example – Books
- Data:
  - Title + author  
- Display:
  - Different formats  
- Controlled via:
  - Template  

### 34. Example – Word Count Component
- Extends:
  - Paragraph element  
- Function:
  - Count words dynamically  

### 35. Implementation Details
- Use:
  - JavaScript class  
- Create:
  - Shadow root  
- Update:
  - Text dynamically  

### 36. Word Count Logic
- Split text:
  - Based on spaces  
- Count:
  - Words  

### 37. Dynamic Updates
- Update interval:
  - Every few milliseconds  
- Reflect:
  - Real-time changes  

### 38. User Interaction
- Editable text area  
- Word count updates:
  - Automatically  

### 39. Non-Editable UI Elements
- Generated elements:
  - Cannot be edited directly  
- Controlled by:
  - JavaScript  

### 40. Reusability Advantage
- Component:
  - Independent  
- Can be reused:
  - Across applications  

### 41. Extensibility
- Modify JavaScript:
  - Add features  
- Example:
  - Word limit  
  - Timer  

### 42. Widget Concept
- Component:
  - UI building block  
- Examples:
  - Counters  
  - Forms  
  - Buttons  

### 43. Purpose of Web Components
- Create:
  - Reusable UI widgets  
- Improve:
  - Development efficiency  

### 44. Limitations of Web Components
- Not fully standardized  
- Implementation differences:
  - Across developers  

### 45. Subjectivity in Design
- Different approaches:
  - Different implementations  
- No single standard:
  - For usage patterns  

### 46. Key Takeaways
- Custom elements:
  - Extend HTML  
- Web components:
  - Combine multiple APIs  
- Benefits:
  - Reusability  
  - Encapsulation  
- Challenge:
  - Lack of standardization  
---
### Week 11 Lecture 4  
#### Frontend Frameworks and React – Purpose, Design Patterns, and Single Page Applications  
##### Description: Explains the need for frontend frameworks, problems of boilerplate and code repetition, introduction to design patterns, and how frameworks like React enable declarative UI development and single page applications.

### 1. Introduction to Frontend Frameworks
- Builds on:
  - Web components  
- Leads to:
  - Framework-based development  

### 2. Purpose of a Framework
- Provide:
  - Predefined structure  
  - Reusable functionality  
- Reduce:
  - Development effort  

### 3. Existing Capabilities Without Frameworks
- Python:
  - Networking  
  - String manipulation  
  - Basic templating  
- JavaScript:
  - DOM manipulation  
  - Custom elements  

### 4. Problem Without Frameworks
- Code repetition  
- Boilerplate code  
- Reinventing solutions  

### 5. Boilerplate Code
- Definition:
  - Repeated standard code  
- Example:
  - Import statements  
- Problem:
  - Time-consuming  
  - Redundant  

### 6. Reinventing the Wheel
- Different developers:
  - Different implementations  
- Result:
  - Inconsistency  
  - Duplication  

### 7. Solution – Design Patterns
- Based on:
  - Experience over time  
- Provide:
  - Standard approaches  
- Example:
  - MVC  

### 8. Framework Definition
- Collection of:
  - Best practices  
  - Reusable patterns  
- Goal:
  - Simplify development  

### 9. Examples of Frameworks
- Backend:
  - Flask  
- Frontend:
  - React  
  - Angular  
  - Vue  
  - Ember  

### 10. React Overview
- JavaScript library  
- Focus:
  - User interface  
- Purpose:
  - Build UI components  

### 11. React vs Web Components
- Similar goal:
  - UI abstraction  
- Difference:
  - React → declarative  
  - Web components → more imperative  

### 12. Declarative Approach
- Specify:
  - What to display  
- Not:
  - How to render step-by-step  

### 13. Imperative Approach
- Specify:
  - Exact steps  
- Used in:
  - Traditional programming  

### 14. React Design Philosophy
- Build:
  - Components  
- Compose:
  - UI from components  

### 15. Component-Based Architecture
- UI divided into:
  - Small reusable parts  
- Each component:
  - Independent  

### 16. Single Page Applications (SPA)
- Entire app:
  - Runs in one page  
- No full page reloads  
- Updates:
  - Dynamically  

### 17. Benefits of SPA
- Faster interaction  
- Better user experience  
- Reduced server load  

### 18. Role of JavaScript in SPA
- Handles:
  - UI updates  
  - State changes  
- Minimizes:
  - Server communication  

### 19. React Example – Basic Component
- Define:
  - Component class  
- Render:
  - UI element  
- Output:
  - Immediate display  

### 20. Live Updates in React
- Changes in code:
  - Reflect instantly  
- No reload required  

### 21. JSX Concept (Implicit)
- Combines:
  - HTML-like syntax  
  - JavaScript  
- Used in:
  - React components  

### 22. Modifying UI Dynamically
- Add text:
  - Updates immediately  
- Example:
  - Add line breaks  

### 23. Stateful Components
- Maintain:
  - Internal state  
- Example:
  - Timer  

### 24. State Management
- State variable:
  - Stores data  
- UI:
  - Updates based on state  

### 25. Example – Timer Component
- Initial state:
  - Seconds = 0  
- Updates:
  - Every second  

### 26. State Reinitialization
- Component change:
  - Resets state  
- Re-render:
  - From scratch  

### 27. Interactive Components
- Example:
  - To-do list  
- Behavior:
  - Add items dynamically  

### 28. Limitations of UI-Only Frameworks
- No backend logic  
- No database connection  
- Only:
  - Interface handling  

### 29. Combining Frontend and Backend
- React:
  - Frontend only  
- Can integrate with:
  - Any backend (Python, PHP, etc.)  

### 30. Markdown Rendering Example
- Input:
  - Markdown text  
- Output:
  - Formatted HTML  
- Done using:
  - Components  

### 31. Advantages of React
- Fast updates  
- Clean UI structure  
- Reusable components  

### 32. Other Frameworks
- Angular:
  - Full-featured  
- Vue:
  - Simpler alternative  
- Ember:
  - Includes services and routing  

### 33. Framework Evolution
- Become:
  - Complex over time  
- New frameworks:
  - Simplify previous ones  

### 34. Learning Frameworks
- Use:
  - Documentation  
  - Tutorials  
- Compare:
  - Different frameworks  

### 35. Role of MDN
- Provides:
  - Guides  
  - Tutorials  
- Useful for:
  - Learning frameworks  

### 36. HTML5 as a Living Standard
- Continuously updated  
- No fixed version  

### 37. Role of JavaScript in Modern Web
- Extends HTML functionality  
- Enables:
  - Dynamic applications  

### 38. Core Web Stack
- HTML:
  - Structure  
- CSS:
  - Styling  
- JavaScript:
  - Behavior  

### 39. Need for Frameworks
- Simplify:
  - Development  
- Reduce:
  - Boilerplate  
- Provide:
  - Structure  

### 40. Performance Consideration
- Network:
  - Slowest component  
- Client-side JS:
  - Improves speed  

### 41. Avoid Overuse of JavaScript
- Too many effects:
  - Bad UX  
- Balance:
  - Functionality + usability  

### 42. UI Design Principles
- Focus on:
  - Simplicity  
  - Clarity  
- Avoid:
  - Overcomplication  

### 43. Future of Frontend Development
- Likely remains:
  - HTML + CSS + JS  
- Frameworks:
  - Continue evolving  

### 44. Key Takeaways
- Frameworks:
  - Reduce repetition  
  - Provide structure  
- React:
  - Declarative UI framework  
- SPA:
  - Improves performance  
- Core stack:
  - HTML + CSS + JavaScript  
---
[[Extra Notes from supplementary content of Week 11]]
