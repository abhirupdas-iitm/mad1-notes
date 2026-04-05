### Week 8 Extra Lecture 1  
#### Database Indexing and Query Optimization  
##### Description: Explains database indexes, their role in optimizing query performance, use of query planners, creating composite indexes, and understanding how indexes improve search efficiency in relational databases.

### 1. Introduction to Database Indexes
- Index = **data structure for faster lookup**
- Purpose:
  - Locate rows quickly  
  - Avoid full table scans  

### 2. Why Indexes are Needed
- Without index:
  - Database scans entire table  
- With index:
  - Searches subset of data  
- Result:
  - Faster queries  
  - Less resource usage  

### 3. Query Execution Concept
- Database uses:
  - Query planner / query executor  
- Determines:
  - How query will run  

### 4. Example Query
- Fetch user using:
  - username  
  - email  
- Uses:
  - WHERE clause  

### 5. Query Plan Analysis
- Use:
  - `EXPLAIN QUERY PLAN`  
- Shows:
  - Execution strategy  

### 6. Understanding Query Plan Output
- Key term:
  - SEARCH vs SCAN  
- SEARCH:
  - Efficient (uses index)  
- SCAN:
  - Full table scan (slow)  

### 7. Auto-Index Concept
- Database may:
  - Automatically create indexes  
- Problem:
  - Created at runtime  
  - Extra overhead  

### 8. Drawbacks of Auto-Index
- Temporary  
- Resource intensive  
- Less efficient than manual index  

### 9. Manual Index Creation
- Preferred approach  
- Developer defines:
  - Which columns to index  

### 10. Composite Index
- Index on:
  - Multiple columns  
- Example:
  - username + email  

### 11. Why Composite Index?
- Matches:
  - Query conditions  
- Improves:
  - Multi-column filtering  

### 12. Creating Index (Concept)
- Syntax:
  - `CREATE INDEX`  
- Can also use:
  - GUI tools  

### 13. Index Naming Convention
- Suggested format:
  - `idx_<table>_<columns>`  
- Example:
  - idx_user_username_email  

### 14. Unique Index
- Ensures:
  - No duplicate combinations  
- Acts as:
  - Constraint  

### 15. Benefits of Unique Index
- Data integrity  
- Prevents duplicate entries  

### 16. Sorting in Index
- Options:
  - Ascending  
  - Descending  
- Depends on:
  - Query pattern  

### 17. Verifying Index Usage
- Re-run:
  - `EXPLAIN QUERY PLAN`  
- Check:
  - If index is used  

### 18. Covering Index
- Optimized index  
- Contains:
  - All required query data  
- Faster than:
  - Regular index  

### 19. Performance Improvement
- Manual index:
  - Faster than auto-index  
- Uses:
  - Less computation  

### 20. Index Design Strategy
- Steps:
  1. Analyze query  
  2. Check execution plan  
  3. Create index  
  4. Re-evaluate performance  

### 21. Flexible Indexing
- Can create:
  - Single-column index  
  - Multi-column index  
- Can set:
  - Unique / non-unique  

### 22. SQLAlchemy and Indexes
- Index can be defined in:
  - Model/schema  
- Not covered in this lecture  

### 23. Schema vs Data Operations
- Current focus:
  - Data querying  
- Not:
  - Schema modification  

### 24. Database Migration Tools
- Example:
  - Alembic  
- Used for:
  - Schema changes  

### 25. Future Integration
- Sync:
  - SQLAlchemy models  
  - Database schema  

### 26. Key Takeaways
- Index:
  - Speeds up queries  
- Avoid:
  - Full table scans  
- Use:
  - Composite indexes when needed  
- Always:
  - Analyze query plan before optimizing
---
