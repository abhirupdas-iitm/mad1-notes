### Week 11 Extra Lecture 1  
#### Database Schema Migrations using Flask-Migrate and Alembic  
##### Description: Explains how to manage database schema changes programmatically using Flask-Migrate. Covers migration concepts, version control, upgrade/downgrade, handling virtual tables, and maintaining synchronization between application code and database schema.

### 1. Introduction to Schema Migrations
- Earlier approach:
  - Manual DB changes  
- New approach:
  - Programmatic schema management  
- Benefit:
  - Reproducible changes 

### 2. What is Schema Migration?
- Definition:
  - Incremental, reversible changes to DB schema  
- Includes:
  - Tables  
  - Columns  
  - Constraints  
- May also modify:
  - Data  

### 3. Key Characteristics
- Incremental:
  - Step-by-step changes  
- Reversible:
  - Can undo changes  
- Version-controlled:
  - Stored as code  

### 4. Purpose of Migrations
- Keep:
  - Code and DB schema in sync  
- Enable:
  - Easy updates and rollbacks  

### 5. Benefits in Team Environments
- Multiple developers:
  - Share schema changes  
- Avoid:
  - Conflicts  
- Maintain:
  - Consistency  

### 6. Multi-Environment Support
- Environments:
  - Local  
  - Development  
  - Staging  
  - Production  
- Migration ensures:
  - Same schema everywhere  

### 7. Version Control Integration
- Schema stored:
  - Along with code  
- Checkout code version:
  - Gets matching schema  

### 8. Tools Used
- Flask-Migrate:
  - Simplifies migrations  
- Alembic:
  - Core migration engine  

### 9. Installation
- Install:
  - Flask-Migrate  
- Uses:
  - SQLAlchemy backend  

### 10. Application Setup
- Initialize:
  - Migration object  
- Connect:
  - App + DB  

### 11. Initial Migration Setup
- Command:
  - `flask db init`  
- Creates:
  - migrations/ folder  
  - config files  

### 12. Migration Directory Structure
- migrations/
  - versions/  
  - env.py  
  - config files  

### 13. Creating First Migration
- Command:
  - `flask db migrate -m "message"`  
- Generates:
  - Migration script  

### 14. Migration Script Contents
- Contains:
  - Table creation code  
- Sections:
  - upgrade()  
  - downgrade()  

### 15. Upgrade Operation
- Applies:
  - Schema changes  
- Command:
  - `flask db upgrade`  

### 16. Downgrade Operation
- Reverts:
  - Schema changes  
- Command:
  - `flask db downgrade`  

### 17. Alembic Version Table
- Tracks:
  - Current schema version  
- Automatically created  

### 18. Automatic Table Creation
- Based on:
  - SQLAlchemy models  
- No manual DB setup needed  

### 19. Manual Adjustments
- Required when:
  - Auto-generated code incorrect  
- Example:
  - Removing unwanted tables  

### 20. Virtual Tables Issue
- Example:
  - Full-text search tables  
- Problem:
  - Treated as normal tables  

### 21. Handling Virtual Tables
- Mark as:
  - Virtual  
- Avoid:
  - Auto-generation  

### 22. Creating Empty Migration
- Command:
  - `flask db revision -m "message"`  
- Use case:
  - Custom SQL operations  

### 23. Writing Manual Migration
- Add:
  - Custom SQL queries  
- Example:
  - Create virtual tables  

### 24. Using SQLAlchemy Text
- Import:
  - text  
- Execute:
  - Raw SQL  

### 25. Trigger Creation
- Types:
  - Insert  
  - Update  
  - Delete  
- Used for:
  - FTS updates  

### 26. Transaction Handling
- Group operations:
  - Single transaction  
- Ensures:
  - Atomic execution  

### 27. Migration Workflow
1. Modify models  
2. Generate migration  
3. Review script  
4. Apply migration  

### 28. Detecting Schema Differences
- Migration tool:
  - Compares DB vs models  
- Generates:
  - Required changes  

### 29. Problem with Auto-Delete
- May remove:
  - Existing tables  
- Risk:
  - Data loss  

### 30. Preventing Auto Deletion
- Modify:
  - Migration config  
- Use:
  - include_object  

### 31. include_object Function
- Controls:
  - What to include  
- Returns:
  - True/False  

### 32. Filtering Logic
- Exclude:
  - Virtual tables  
  - Unwanted drops  

### 33. Configuration Update
- Add:
  - include_object to context  
- Applied:
  - During migration  

### 34. Running Migration Again
- After config:
  - Regenerate migration  
- Result:
  - Correct schema updates  

### 35. Viewing Migration History
- Command:
  - `flask db history`  
- Shows:
  - All revisions  

### 36. Checking Current Version
- Command:
  - `flask db current`  
- Displays:
  - Active version  

### 37. Downgrade Example
- Removes:
  - Recently added tables  
- Reverts:
  - Previous state  

### 38. Upgrade Example
- Reapplies:
  - Latest changes  
- Restores:
  - Tables  

### 39. Fresh Setup Scenario
- Delete DB  
- Run:
  - `flask db upgrade`  
- Recreates:
  - Entire schema  

### 40. Migration as Version Control
- Similar to:
  - Git  
- Actions:
  - Move forward/backward  

### 41. Practical Use Cases
- Adding features  
- Modifying schema  
- Team collaboration  

### 42. Best Practices
- Always:
  - Review migrations  
- Avoid:
  - Blind execution  

### 43. Advantages
- Automation  
- Consistency  
- Reversibility  

### 44. Key Takeaways
- Migrations:
  - Essential for real projects  
- Flask-Migrate:
  - Simplifies process  
- Alembic:
  - Core engine  
- Enables:
  - Safe schema evolution  
---
