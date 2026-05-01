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
### Week 12 Lecture 2  
#### Service-Based Deployment Models – SaaS, IaaS, and PaaS  
##### Description: Explains the service-oriented approach to deployment. Covers Software-as-a-Service (SaaS), Infrastructure-as-a-Service (IaaS), and Platform-as-a-Service (PaaS), along with practical examples like Replit and Glitch.

### 1. Introduction to Service Approach
- Idea:
  - Divide responsibilities  
- Goal:
  - Specialization  
  - Efficiency  

### 2. Traditional Approach Problem
- One person handles:
  - Hardware  
  - OS  
  - Networking  
  - Application  
- Result:
  - Complex  
  - Inefficient  

### 3. Service-Based Model
- Tasks split across:
  - Different providers  
- Each provider:
  - Specializes in one layer  

### 4. Role of Datacenter Operators
- Responsible for:
  - Physical infrastructure  
- Includes:
  - Buildings  
  - Cooling  
  - Security  

### 5. Infrastructure Responsibilities
- Provide:
  - Power  
  - Network  
  - Hardware  
- Do NOT manage:
  - Applications  

### 6. Developer Focus Shift
- Developers focus on:
  - Writing application code  
- No need to manage:
  - Hardware setup  

### 7. Software-as-a-Service (SaaS)
- Fully managed software  
- User only:
  - Uses application  

### 8. SaaS Examples
- Google Docs  
- Gmail  
- Office 365  
- WordPress  
- Drupal  

### 9. SaaS Characteristics
- No installation required  
- Access via:
  - Browser  
- Provider handles:
  - Updates  
  - Security  

### 10. Hosted Solutions Concept
- Software runs on:
  - Provider’s servers  
- User:
  - Creates account  
  - Uses features  

### 11. Example – GitLab
- Options:
  - Self-hosted  
  - Hosted service  
- Hosted:
  - No maintenance required  

### 12. SaaS Advantages
- Easy to use  
- No setup  
- Always updated  

### 13. SaaS Limitation
- Less control  
- Dependent on provider  

### 14. Infrastructure-as-a-Service (IaaS)
- Provides:
  - Raw computing resources  
- Includes:
  - Virtual machines  

### 15. IaaS Responsibilities
- Provider:
  - Hardware  
  - Networking  
- User:
  - Everything else  

### 16. User Responsibilities in IaaS
- Install OS  
- Manage updates  
- Install software  
- Handle security  

### 17. IaaS Analogy
- Like renting:
  - A bare computer  
- You control:
  - Everything inside  

### 18. IaaS Providers
- AWS  
- Google Compute Engine  
- Microsoft Azure  
- DigitalOcean  
- Linode  

### 19. IaaS Advantages
- Full control  
- Flexible setup  

### 20. IaaS Challenges
- Requires expertise  
- Maintenance overhead  

### 21. Choosing IaaS
- Depends on:
  - Skill level  
  - Project requirements  

### 22. Platform Concept
- Combines:
  - Hardware + software  
- Provides:
  - Ready environment  

### 23. Platform-as-a-Service (PaaS)
- Provider manages:
  - Infrastructure  
  - OS  
  - Runtime environment  

### 24. PaaS Responsibilities
- Handles:
  - OS installation  
  - Updates  
  - Security patches  

### 25. Developer Responsibilities in PaaS
- Write application code  
- Configure:
  - Requirements  

### 26. Platform Components
- OS (Linux/Windows)  
- Programming language  
- Frameworks  

### 27. Example Platform Setup
- Python + Flask  
- PHP + Laravel  
- Database connectivity  

### 28. Managed Dependencies
- Versions handled by:
  - Provider  
- Example:
  - Python versions  
  - Libraries  

### 29. Database Integration
- Options:
  - MySQL  
  - PostgreSQL  
  - MongoDB  
  - Firebase  

### 30. Developer Interaction with PaaS
- Specify:
  - Requirements  
- Deploy:
  - Code  

### 31. Scaling in PaaS
- Shared responsibility:
  - Developer + provider  
- Provider:
  - Suggests scaling options  

### 32. Benefits of PaaS
- Reduced complexity  
- Faster deployment  
- Built-in scaling support  

### 33. Trade-offs of PaaS
- Less control than IaaS  
- Dependent on platform constraints  

### 34. Example – Replit
- Provides:
  - Development + runtime environment  
- Includes:
  - Python  
  - Flask  
  - Web server  

### 35. Replit Characteristics
- Browser-based development  
- Automatic server setup  
- Shared infrastructure  

### 36. Replit Resource Model
- CPU and memory:
  - Shared across users  
- Not designed for:
  - Large-scale deployment  

### 37. Replit Behavior
- App:
  - May shut down after inactivity  
- Not always-on  

### 38. Example – Flask App on Replit
- Global state:
  - Maintained while running  
- Reset:
  - On restart  

### 39. Shell Access in Replit
- Linux environment  
- Commands:
  - ls  
  - lscpu  
  - free  

### 40. Example – Glitch
- Similar to:
  - Replit  
- Focus:
  - Development + lightweight deployment  

### 41. Glitch Features
- File editor  
- Shell access  
- Always-on options (limited)  

### 42. Resource Comparison
- Replit:
  - Higher shared resources  
- Glitch:
  - Smaller but sufficient  

### 43. Platform Characteristics (Replit/Glitch)
- Manage:
  - Infrastructure  
  - Runtime  
- Provide:
  - Ready-to-use environment  

### 44. Development vs Deployment Focus
- Replit:
  - Education + development  
- Glitch:
  - Development + lightweight hosting  

### 45. Platform Abstraction
- Developer sees:
  - Simple interface  
- Backend:
  - Complex infrastructure  

### 46. Key Takeaways
- SaaS:
  - Use software  
- IaaS:
  - Manage everything  
- PaaS:
  - Focus on code  
- Service model:
  - Improves efficiency  
- Platforms:
  - Simplify deployment  
---
### Week 12 Lecture 3  
#### Platform-as-a-Service in Practice – Google App Engine and Deployment Tools  
##### Description: Explores real-world Platform-as-a-Service (PaaS) using Google App Engine. Covers cloud console, cloud shell, deployment workflow, comparison with Replit/Glitch, and introduces the need for CI/CD and automation. 

### 1. Introduction to Advanced PaaS
- Focus:
  - Larger-scale platforms  
- Example:
  - Google App Engine  

### 2. App Engine vs Compute Engine
- Compute Engine:
  - IaaS (raw VM)  
- App Engine:
  - PaaS (managed platform)  

### 3. Key Idea of App Engine
- Provides:
  - Runtime environment  
  - Web server  
- Developer:
  - Focuses on code  

### 4. Getting Started
- Requires:
  - Google Cloud account  
- Access via:
  - console.cloud.google.com  

### 5. Cloud Console Overview
- Shows:
  - Project details  
  - Resource usage  
  - Request statistics  

### 6. Monitoring Features
- Displays:
  - Requests per second  
  - Service health  
- Helps:
  - Debugging and scaling decisions  

### 7. Platform Status
- Tracks:
  - Frontend services  
  - HTTPS  
  - Logging  
- Ensures:
  - System reliability  

### 8. Billing Aspect
- Paid service  
- Includes:
  - Free tier  
  - Trial credits  

### 9. Cloud Shell Introduction
- Provides:
  - Linux environment  
- Used for:
  - Managing deployment  

### 10. Cloud Shell Features
- Pre-installed tools  
- Commands for:
  - Google Cloud interaction  

### 11. CLI Integration
- Example:
  - gcloud commands  
- Used to:
  - Configure projects  
  - Deploy apps  

### 12. Interface Characteristics
- Less visual than:
  - Replit/Glitch  
- More focused on:
  - Professional usage  

### 13. Intended Use Case
- Designed for:
  - Large-scale applications  
- Not for:
  - Simple experiments  

### 14. Development vs Production
- Development:
  - Simple tools sufficient  
- Production:
  - Requires robust systems  

### 15. Resource Availability
- Example:
  - Multi-core CPUs  
  - Significant RAM  
- Shared infrastructure  

### 16. Resource Abstraction
- Resources:
  - Virtualized  
- Not dedicated:
  - Fully to one user  

### 17. Development Workflow
- Clone sample project  
- Edit code  
- Deploy to platform  

### 18. Editor Environment
- Browser-based editor  
- Similar to:
  - VS Code  

### 19. Code Structure Example
- Flask app:
  - Defines route  
  - Returns response  

### 20. Deployment Output
- App accessible via:
  - *.appspot.com domain  
- Example:
  - hello world output  

### 21. URL Generation
- Unique deployment URL  
- Managed by:
  - Platform  

### 22. Comparison – Replit
- Focus:
  - Education  
  - Development  
- Limited:
  - Scaling  

### 23. Replit Behavior
- Auto shutdown:
  - After inactivity  
- Restart:
  - On new request  

### 24. Comparison – Glitch
- Focus:
  - Lightweight deployment  
- Provides:
  - Always-on options  

### 25. Glitch vs Replit
- Both:
  - PaaS-like  
- Differences:
  - Target users  
  - Deployment features  

### 26. App Engine Position
- Higher complexity  
- Better suited for:
  - Production systems  

### 27. Ease vs Power Tradeoff
- Simple tools:
  - Easy to use  
- Advanced tools:
  - More powerful  
  - More complex  

### 28. Platform Responsibilities
- Handles:
  - OS  
  - Web server  
  - Scaling basics  

### 29. Failure Handling
- Detect:
  - Crashes  
- Restart:
  - Automatically  

### 30. Resource Monitoring
- Tracks:
  - Usage limits  
- Provides:
  - Alerts  

### 31. Scalability Support
- Handles:
  - Increased load  
- Requires:
  - Proper app design  

### 32. Multi-Service Integration
- Supports:
  - Databases  
  - Logging  
  - Monitoring  

### 33. Common PaaS Providers
- Google App Engine  
- AWS Elastic Beanstalk  
- Heroku  

### 34. Supported Platforms
- Python (Flask, Django)  
- PHP (Laravel)  
- Node.js  
- React  

### 35. Developer Workflow in PaaS
- Write code  
- Push to platform  
- Platform:
  - Deploys automatically  

### 36. Abstraction Benefits
- No need to manage:
  - Infrastructure  
- Faster development  

### 37. Trade-offs
- Less control  
- Platform dependency  

### 38. Importance of Integration
- Must connect with:
  - Version control  
  - Deployment pipelines  

### 39. CI/CD Introduction
- Continuous Integration:
  - Frequent merging  
- Continuous Deployment:
  - Automated release  

### 40. Automation Need
- Reduce:
  - Manual steps  
- Improve:
  - Reliability  

### 41. Development Best Practices
- Use:
  - Version control  
- Automate:
  - Testing  
  - Deployment  

### 42. Scaling Considerations
- Requires:
  - Infrastructure support  
  - Code optimization  

### 43. Platform Ecosystem
- Provides:
  - Tools + services  
- Enables:
  - End-to-end deployment  

### 44. Key Takeaways
- PaaS:
  - Simplifies deployment  
- App Engine:
  - Production-ready platform  
- Tradeoff:
  - Ease vs control  
- Future steps:
  - CI/CD and automation  
---
