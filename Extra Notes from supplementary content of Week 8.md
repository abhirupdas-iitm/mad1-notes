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
### Week 8 Extra Lecture 2  
#### Full Text Search using SQLite FTS5 and SQLAlchemy  
##### Description: Explains implementation of full text search using SQLite FTS5. Covers limitations of LIKE queries, creation of virtual tables, triggers for synchronization, advanced search queries, and integration with SQLAlchemy.

### 1. Introduction to Full Text Search
- Goal:
  - Search keywords inside article content  
- Example:
  - Searching "flask" inside articles  

### 2. Basic Search using LIKE
- Query:
  - `SELECT * FROM article WHERE content LIKE '%keyword%'`  
- Works for:
  - Simple substring matching  

### 3. Limitations of LIKE Queries
- Cannot handle:
  - Complex conditions (AND, OR properly)  
  - Ranking or relevance  
  - Prefix-specific searches efficiently  
- Performance:
  - Expensive (slow queries)  

### 4. Search Feature in Web App
- Endpoint:
  - `/search?q=keyword`  
- Controller:
  - Extract query parameter  
  - Perform filtering  
- Result:
  - Display matching articles  

### 5. SQLAlchemy LIKE Implementation
- Uses:
  - `.filter(column.like(query))`  
- Query format:
  - `%keyword%`  

### 6. Problems with LIKE in Practice
- Cannot:
  - Combine keywords effectively  
  - Perform logical queries (AND, OR, NOT)  
- Example limitations:
  - "flask AND documentation"  
  - "my OR content"  

### 7. Need for Full Text Search
- Provides:
  - Efficient searching  
  - Rich query capabilities  
- Solution:
  - SQLite FTS5  

### 8. Introduction to FTS5
- Feature of SQLite  
- Creates:
  - Specialized search indexes  
- Benefits:
  - Faster search  
  - Flexible queries  

### 9. Virtual Table Concept
- FTS5 creates:
  - Virtual table for indexing  
- Example:
  - `article_search`  

### 10. Virtual Table Structure
- Columns:
  - title  
  - content  
- Linked to:
  - Original table (`article`)  

### 11. Row Mapping
- Uses:
  - rowid  
- Maps:
  - Virtual table → actual table  

### 12. Tokenization
- Purpose:
  - Break text into searchable tokens  
- Example:
  - `porter unicode61` tokenizer  

### 13. Creating FTS5 Table
- Syntax:
  - `CREATE VIRTUAL TABLE ... USING FTS5`  
- Includes:
  - Columns  
  - Tokenizer  
  - Content mapping  

### 14. Data Synchronization Problem
- Virtual table is separate  
- Needs manual sync:
  - Insert  
  - Update  
  - Delete  

### 15. Using Triggers
- Automate synchronization  
- Trigger types:
  - INSERT  
  - DELETE  
  - UPDATE  

### 16. Insert Trigger
- Action:
  - Add entry to virtual table  
- Uses:
  - New row values  

### 17. Delete Trigger
- Action:
  - Remove entry from virtual table  

### 18. Update Trigger
- Action:
  - Delete old entry  
  - Insert updated entry  

### 19. Initial Index Build
- Required:
  - Populate virtual table for existing data  

### 20. MATCH Query
- Used for searching:
  - `WHERE column MATCH query`  
- Replaces:
  - LIKE  

### 21. Prefix Search
- Example:
  - `flask*`  
- Matches:
  - Words starting with "flask"  

### 22. AND Queries
- Example:
  - `dummy AND content`  
- Returns:
  - Rows containing both  

### 23. OR Queries
- Example:
  - `my OR content OR flask`  
- Returns:
  - Rows matching any  

### 24. Advanced Queries
- Supports:
  - NOT  
  - NEAR  
  - Phrase matching  
- Much richer than LIKE  

### 25. Performance Benefits
- Faster:
  - Optimized indexing  
- Efficient:
  - Less resource usage  

### 26. Integration with SQLAlchemy
- Create model:
  - `ArticleSearch`  
- Maps:
  - Virtual table  

### 27. Controller Update
- Replace:
  - LIKE query  
- With:
  - MATCH query  

### 28. Dynamic Query Handling
- User input:
  - Passed directly to MATCH  
- Can also:
  - Sanitize or preprocess  

### 29. Enhancing Search UI
- Show:
  - Titles  
  - Links to articles  
- Possible improvements:
  - Highlight keywords  
  - Show snippets  

### 30. Highlighting Results
- FTS5 supports:
  - Returning matched text segments  

### 31. Security Considerations
- Restrict: Query scope  
- Avoid: Arbitrary query execution  

### 32. Extending Search
- Add:
  - Article detail page  
- Use:
  - rowid mapping  

### 33. Alternatives to FTS
- External systems:
  - Elasticsearch  
  - Dedicated search engines  

### 34. When to Use FTS5
- Suitable for:
  - Most applications  
- Lightweight:
  - Built into SQLite  

### 35. Key Takeaways
- LIKE:
  - Simple but limited  
- FTS5:
  - Powerful and scalable  
- Use:
  - Virtual tables + triggers  
- Enables:
  - Advanced search features
---
