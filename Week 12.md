### Week 12 Lecture 1  
#### Deployment – From Local Development to Scalable Infrastructure  
##### Description: Introduces deployment as the process of making applications accessible to users. Covers local vs permanent deployment, infrastructure requirements, cloud computing, scaling architecture, load balancing, logging, and content delivery networks (CDNs).

### 1. Introduction to Deployment
- Deployment:
  - Making an app available to users  
- Focus:
  - Steps involved  
  - Conditions required  
  - Practical considerations  

### 2. Components of Deployment Topic
- Understand:
  - Components of an app  
  - Service approach  
  - Automation and containers  

### 3. Starting Point – Idea
- App begins with:
  - Idea  
- Goal:
  - Solve a user need  
- Typical structure:
  - Frontend (HTML, CSS, JS)  
  - Backend + database  

### 4. Local Development
- Code developed on:
  - Local machine  
- Includes:
  - Source code  
  - Documentation  
  - Assets (images, styles, etc.)  

### 5. Development Environment
- Tools:
  - Editors  
  - File system  
  - Desktop environment  
- Files:
  - Code  
  - Docs  
  - Media  

### 6. Limitation of Local Development
- Single machine:
  - Risk of data loss  
- Not always available:
  - Cannot serve users continuously  
- Laptop constraints:
  - Power  
  - Portability  

### 7. Multiple Services in Local Setup
- Components:
  - Web server  
  - Database  
  - Other processes  
- Problem:
  - Too much load on one system  

### 8. Need for Deployment
- Goal:
  - Make app accessible to others  
- Requirement:
  - Move from local → remote system  

### 9. Permanent Deployment Concept
- Dedicated system:
  - Runs app continuously  
- Independent of:
  - Personal machine  

### 10. Requirements for Deployment Infrastructure
- Dedicated servers  
- Always-on internet  
- Uninterrupted power  

### 11. Infrastructure Definition
- Includes:
  - Servers  
  - Power systems  
  - Network connectivity  

### 12. Data Centers
- Centralized facilities:
  - Host multiple servers  
- Features:
  - Cooling  
  - Backup power  
  - High bandwidth connectivity  

### 13. Introduction to Cloud
- Shared infrastructure model  
- Users:
  - Rent resources  
- Avoid:
  - Managing physical data centers  

### 14. Cloud Providers
- Examples:
  - AWS  
  - Google Cloud  
  - Azure  
- Accessible:
  - To anyone  

### 15. Advantages of Cloud
- No setup overhead  
- Scalable resources  
- Pay-as-you-use  

### 16. Scaling Problem
- Small system:
  - Works for few users  
- Large system:
  - Needs to handle thousands/millions  

### 17. Basic Architecture (Single Server)
- User → Frontend server  
- Communication:
  - HTTP  
- Server:
  - Sends responses  

### 18. Network Identity
- Requires:
  - IP address  
  - Domain name (DNS)  

### 19. DNS Role
- Maps:
  - Domain → IP address  
- Enables:
  - User-friendly access  

### 20. Scaling by Separation
- Split system into:
  - Frontend  
  - Database  
- Benefits:
  - Optimized resource usage  

### 21. Frontend vs Database Roles
- Frontend:
  - Handles requests  
  - Network heavy  
- Database:
  - Storage  
  - Memory + disk intensive  

### 22. Internal Communication
- Frontend ↔ Database:
  - Private network  
- Not exposed to:
  - Public internet  

### 23. Security Layer (HTTPS)
- Add:
  - Encryption  
- Use:
  - Certificates  
- Improves:
  - Security  

### 24. Load Balancer Introduction
- Sits between:
  - Users and servers  
- Role:
  - Distribute requests  

### 25. Load Balancing Mechanism
- Multiple frontends  
- Requests distributed:
  - Across servers  

### 26. Benefits of Load Balancer
- Prevent overload  
- Improve performance  
- Enable scaling  

### 27. Transparency to User
- User connects to:
  - Load balancer only  
- Backend complexity:
  - Hidden  

### 28. Logging System
- Records:
  - Requests  
  - Errors  
- Used for:
  - Debugging  
  - Security analysis  

### 29. Dedicated Logging Service
- Separate machine:
  - Handles logs  
- Avoids:
  - Overloading main system  

### 30. Horizontal Scaling
- Add:
  - More frontend servers  
- Improves:
  - Capacity  

### 31. Database Scaling
- Multiple database instances  
- Handles:
  - High data load  

### 32. Cloud-Based Scaling
- Cloud provider offers:
  - Load balancers  
  - Compute instances  
  - Storage systems  

### 33. Unified Interface
- Entire system appears as:
  - Single server  
- Internally:
  - Multiple components  

### 34. Content Delivery Network (CDN)
- Specialized service:
  - Delivers static content  

### 35. CDN Use Cases
- Static files:
  - CSS  
  - JavaScript libraries  
  - Images  

### 36. CDN Advantages
- Reduces server load  
- Faster delivery  
- Uses caching  

### 37. Example – External Libraries
- Bootstrap  
- jQuery  
- React  
- Loaded via CDN  

### 38. Caching Benefit
- Files:
  - Already stored in browser  
- Result:
  - Faster loading  

### 39. Deployment Complexity
- Requires:
  - Infrastructure planning  
  - Resource allocation  
  - System design  

### 40. Key Challenges
- Scaling  
- Security  
- Performance  
- Reliability  

### 41. Small vs Large Deployment
- Small scale:
  - Single server sufficient  
- Large scale:
  - Requires distributed system  

### 42. Cost Consideration
- Cloud servers:
  - Affordable for small usage  
- Scaling:
  - Increases cost  

### 43. Infrastructure Requirements Recap
- Always-on servers  
- Reliable network  
- Backup power  
- Monitoring  

### 44. Monitoring and Maintenance
- Track:
  - System health  
- Detect:
  - Failures  
- Auto-restart systems  

### 45. Role of Cloud Providers
- Provide:
  - Infrastructure  
  - Tools  
- Simplify:
  - Deployment process  

### 46. Key Takeaways
- Development:
  - Relatively easy  
- Deployment:
  - Complex  
- Scaling:
  - Requires architecture changes  
- Cloud:
  - Enables scalable deployment  
- Real-world systems:
  - Distributed and multi-layered  
---
