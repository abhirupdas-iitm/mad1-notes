### Week 7 Lecture 1  
#### Backend Systems and Memory Hierarchy  
##### Description: Introduces backend systems with focus on memory hierarchy, storage types, performance parameters (latency, throughput, density), and their impact on application design and database choices.

### 1. Introduction to Backend Systems
- Focus shifts from APIs → deeper system-level understanding
- Goal:
  - Understand **how underlying systems affect application performance**
- Backend systems involve:
  - Data storage
  - Processing
  - Resource management
- Important for developers to:
  - Use resources efficiently
  - Make informed architectural decisions  

### 2. Memory Hierarchy Overview
- Memory = **storage elements used to store data in a computer**
- Organized in hierarchy based on:
  - Speed
  - Capacity
  - Cost  

Hierarchy (top → bottom):
- Registers  
- Cache (SRAM)  
- Main Memory (DRAM)  
- SSD (Flash storage)  
- HDD (Magnetic disk)  
- Cold storage / archival systems  

### 3. Registers (Fastest, Smallest)
- Located **inside CPU**
- Used for:
  - Temporary variables
  - Immediate computations
- Capacity:
  - Very small (≈ 10–30 values)
- Example:
  - Variables in programs may be stored here temporarily
- Key property:
  - **Extremely fast (nanoseconds latency)**  

### 4. Cache Memory (SRAM)
- Types:
  - L1, L2, L3 cache
- Implemented using **SRAM**
- Capacity:
  - Kilobytes → Megabytes
- Purpose:
  - Acts as **intermediate layer between CPU and DRAM**
- Advantage:
  - Much faster than DRAM
- Role:
  - Speeds up frequently accessed data  

### 5. Main Memory (DRAM)
- Commonly referred to as **RAM**
- Capacity:
  - Typically 4GB – 16GB (consumer systems)
- Stores:
  - Active programs
  - Working data
- Slower than cache but much larger  

### 6. SSD (Solid State Drive)
- Based on **flash memory**
- Non-volatile:
  - Data persists after power off
- Capacity:
  - Hundreds of GBs
- Faster than HDD but slower than DRAM  

### 7. HDD (Magnetic Disk)
- Traditional storage
- Capacity:
  - Several TB
- Very high storage capability
- Slower access compared to SSD  

### 8. Large-Scale Storage (Beyond HDD)
- Used in:
  - Data centers (Google, cloud systems)
- Scale:
  - Petabytes (10^15 bytes)
- Requires:
  - Specialized storage architectures  

### 9. Storage Performance Parameters
#### 9.1 Latency
- Time to access data
- Lower is better  

Order (fast → slow):
- Registers  
- Cache (SRAM)  
- DRAM  
- SSD  
- HDD  
- Difference:
  - Nanoseconds → milliseconds (huge gap)

#### 9.2 Throughput
- Data read per second
- Higher is better  
Order:
- DRAM > SSD > HDD  

#### 9.3 Density (Cost Efficiency)
- Bits stored per unit cost
- Higher is better  
Order:
- HDD > SSD > DRAM > SRAM > Registers  

### 10. Computer Organization (Layered Storage)
- CPU uses:
  - Registers (fastest)
- Backed by:
  - Cache (SRAM)
  - DRAM (working memory)
  - SSD (secondary storage)
  - HDD (mass storage)
  - Backup systems  

### 11. Cold Storage
- Used for:
  - Backups
  - Archival data
- Characteristics:
  - Very high capacity  
  - Very low cost  
  - Very high latency (can take hours to retrieve)  
- Examples:
  - Cloud archival systems  
- Key idea:
  - Data is **rarely accessed but must be محفوظ (safe)**  

### 12. Importance of Redundancy
- Data must not be stored in a single place
- Systems use:
  - Multiple copies
  - Backup layers
- Ensures:
  - Data durability  
  - Fault tolerance  

### 13. Impact on Application Development
Developers must consider:

#### 13.1 Storage Strategy
- Where to store data:
  - Memory vs disk vs archive  

#### 13.2 Performance Trade-offs
- Faster storage = expensive  
- Slower storage = cheaper but higher latency  

#### 13.3 Example Problems
- Storing everything on disk:
  - Slow performance  
- Storing everything in memory:
  - Expensive + volatile  

#### 13.4 Data Access Patterns
- Some systems optimized for:
  - Writing large volumes (logs)
- Others optimized for:
  - Fast reads  

### 14. Real-World Application Examples
- Social media:
  - User data + relationships
- Education platforms:
  - Student records
  - Grades
- Large-scale systems:
  - Massive data growth over time  

### 15. Key Takeaways
- Memory hierarchy is fundamental to performance  
- Trade-offs:
  - Speed vs cost vs capacity  
- Developers must:
  - Choose appropriate storage systems  
  - Design based on application needs  
- Backend design decisions directly impact:
  - Scalability  
  - Efficiency  
  - Reliability  

### Notes to be taken for `Activity Question 1`
1. 
---
### Week 7 Lecture 2  
#### Data Search, Time Complexity, and Data Structures for Efficient Retrieval  
##### Description: Explains how data search works using Big-O notation, compares different time complexities, and introduces data structures like arrays, binary search, trees, B-trees, and hash tables for efficient database operations.

### 1. Introduction to Data Search
- Before studying databases → understand **how search works**
- Key goal:
  - Efficient retrieval of data
- Performance depends on:
  - Data structure used  
  - Search algorithm  

### 2. Big-O Notation (O())
- Represents **order of growth of computation time**
- Focus:
  - How runtime scales with input size (N)
- Ignores:
  - Constants  
  - Lower-order terms  

### 3. Common Time Complexities
#### 3.1 O(1) – Constant Time
- Time independent of input size  
- Example:
  - Direct access (ideal case)
- Best possible scenario  
- Limitation:
  - Often unrealistic for meaningful search  

#### 3.2 O(log N) – Logarithmic Time
- Time increases slowly as N increases  
- Example:
  - Binary search  
- Very efficient and practical  

#### 3.3 O(N) – Linear Time
- Time proportional to number of elements  
- Example:
  - Sequential search  
- Acceptable for small datasets  
- Not scalable for large databases  

#### 3.4 O(N²), O(N³) – Polynomial Time
- Time grows rapidly  
- Inefficient for large datasets  

#### 3.5 O(2^N) – Exponential Time
- Extremely inefficient  
- Doubles work with each added element  
- Not practical for real systems  

### 4. Linked List Search
- Data stored as:
  - Nodes connected via pointers  
- Search process:
  - Traverse one by one  
- Complexity:
  - Worst case: O(N)  
  - Average case: O(N)  
- Problem:
  - Not efficient for large-scale search  

### 5. Array Search (Unsorted)
- Direct indexing possible  
- But:
  - Position of element unknown  
- Requires:
  - Sequential traversal  
- Complexity:
  - O(N)  

### 6. Sorted Array and Binary Search
- Key requirement:
  - Data must be **sorted**
- Strategy:
  - Check middle element  
  - Eliminate half of search space  
- Process:
  - N → N/2 → N/4 → ... → 1  
- Complexity:
  - O(log N)  
- Advantage:
  - Very efficient search  

### 7. Limitations of Arrays
- Fixed size  
- Insertions:
  - Require shifting elements  
- Deletions:
  - Require reorganization  
- Not flexible for dynamic data  

### 8. Binary Search Trees (BST)
- Tree structure with properties:
  - Left subtree < root  
  - Right subtree > root  
- Enables:
  - Efficient search using comparisons  
- Average complexity:
  - O(log N)  

### 9. Tree Balancing Issue
- Problem:
  - Trees can become **unbalanced**
- Effect:
  - Performance degrades to O(N)  
- Solutions:
  - AVL Trees  
  - Red-Black Trees  

### 10. B-Trees (Disk-Oriented Trees)
- Designed for:
  - **Disk storage systems**
- Key features:
  - Efficient for large data  
  - Works with block-based storage  
- Advantage:
  - Reduces number of disk accesses  
- Widely used in:
  - Databases  

### 11. Hash Tables
- Use:
  - Hash function → maps key → index  
- Operation:
  - Direct lookup using computed index  
- Complexity:
  - Average: O(1)  
- Advantage:
  - Fastest possible search  

### 12. Limitations of Hashing
- Requires:
  - Good hash function  
- Issues:
  - Collisions  
  - Not always applicable  
- Not suitable for:
  - Range queries  
  - Ordered data  

### 13. Key Insights for Databases
- Efficient search is critical  
- Choice of data structure affects:
  - Performance  
  - Scalability  
- Common strategies:
  - Sorted data → binary search  
  - Trees → structured search  
  - Hashing → direct access  

### 14. Key Takeaways
- Big-O helps evaluate scalability  
- O(log N) and O(1) are ideal targets  
- Data structures determine performance  
- Databases rely heavily on:
  - B-trees  
  - Hashing  
- Efficient design requires:
  - Matching data structure to use case  

### Notes to be taken for `Activity Question 2`
1. 
---
### Week 7 Lecture 3  
#### Database Indexing, Query Optimization, and Performance Trade-offs  
##### Description: Explains how database indexing works, importance of indexes, types of indexes (B-Tree, Hash), query optimization techniques, and how query structure impacts performance.

### 1. Introduction to Database Search
- Databases use **tabular structure**
  - Tables → rows + columns  
- Example:
  - Student table → roll number, name, department  
  - Course table → course ID, name  
  - Relationship table → `student_id`, `course_id`  
- Goal:
  - Efficiently search and retrieve data  

### 2. Need for Indexing
- Data insertion order:
  - Not sorted  
- Searching directly:
  - Inefficient (O(N))  
- Solution:
  - Use **indexes**  

### 3. What is an Index?
- Index = **sorted copy of a column**
- Contains:
  - Column values (sorted)  
  - Pointers to original table rows  
- Purpose:
  - Faster search  

### 4. How Index Improves Search
- Search in index:
  - O(log N) using tree structures  
- Then:
  - Fetch actual row from table  
- Result:
  - Efficient lookup  

### 5. Trade-offs of Indexing
- Too few indexes:
  - Slow queries  
- Too many indexes:
  - Extra storage  
  - Slower writes  
- Requires:
  - Careful design  

### 6. Types of Indexes
#### 6.1 B-Tree Index
- Most common type  
- Based on:
  - Balanced tree structure  
- Supports:
  - Range queries  
  - Ordered data  
- Efficient for:
  - Prefix-based search  

#### 6.2 Hash Index
- Uses:
  - Hash function → direct lookup  
- Complexity:
  - O(1) (average case)  
- Limitation:
  - Only supports equality search  
  - Cannot handle range queries  

### 7. Prefix-Based Search Optimization
- Example:
  - `LIKE 'Patrick%'`
- Works efficiently:
  - Because prefix is known  
- Process:
  - Traverse tree using prefix  
  - Narrow down search space  

### 8. Partial Pattern Search Limitations
- Example:
  - `LIKE 'Pat%ck'`
- Issue:
  - Only partial prefix usable  
- Result:
  - Partial index usage  
  - Additional scanning required  

### 9. Full Wildcard Search Problem
- Example:
  - `LIKE '%Patrick%'`
- Problem:
  - No fixed prefix  
- Result:
  - Cannot use index  
  - Full scan required  

### 10. Column Comparison Queries
- Example:
  - Comparing two columns  
- Issue:
  - Index becomes useless  
- Reason:
  - No fixed reference point for search  

### 11. Multi-Column Indexes
- Combine multiple columns into one index  
- Example:
  - (date_of_birth, city, name)  

### 12. Working of Multi-Column Index
- Sorted in order:
  - First column → second → third  
- Query efficiency depends on:
  - Matching prefix order  

### 13. Multi-Column Index Usage Rules
#### Good Usage:
- Query uses:
  - First column  
  - First + second column  

#### Partial Usage:
- Uses only first column  

#### Poor Usage:
- Skips first column  
- Uses later columns directly  

### 14. AND vs OR in Queries
- AND:
  - Works well with indexes  
- OR:
  - Breaks index usage  
- Reason:
  - Index designed for sequential filtering  

### 15. Query Optimization Responsibility
- ORM (e.g., SQLAlchemy):
  - Does NOT optimize queries automatically  
- Developer must:
  - Write efficient queries  
  - Understand indexing  

### 16. Database Optimization Tools
- Databases provide:
  - Query analysis tools  
  - Index recommendations  
- Examples:
  - MySQL documentation  
  - SQLite optimization  
  - PostgreSQL advanced techniques  

### 17. Impact of Indexing on Performance
- Without index:
  - O(N) search  
- With index:
  - O(log N) search  
- Example:
  - 1000 entries → 1000 steps vs ~10 steps  

### 18. Over-Indexing Problem
- Too many indexes:
  - Increased storage  
  - Slower updates  
  - Confusion in query planner  

### 19. Importance of Query Design
- Query structure directly affects:
  - Index usage  
  - Performance  
- Poor queries:
  - Can negate indexing benefits  

### 20. Normalization (Brief Mention)
- Organizing data efficiently  
- Avoid redundancy  
- Improves:
  - Consistency  
  - Performance  

### 21. Key Takeaways
- Indexes are critical for performance  
- B-Trees:
  - Default and versatile  
- Hash indexes:
  - Fast but limited  
- Query design matters as much as indexing  
- Developers must:
  - Anticipate query patterns  
  - Design indexes accordingly  
- Balance:
  - Speed vs storage vs complexity

### Notes to be taken for `Activity Question 3`
1. 
---
### Week 7 Lecture 4  
#### NoSQL Databases, Data Storage Models, and ACID vs Scalability  
##### Description: Introduces NoSQL databases, compares them with relational databases, explores different data storage models (document, key-value, column, graph, time-series), and discusses ACID properties, consistency trade-offs, and scalability.

### 1. Introduction to NoSQL
- Traditional focus:
  - **Relational Databases (RDBMS)**  
- Limitation:
  - Fixed tabular structure  
- Alternative:
  - **NoSQL databases**  

### 2. What is SQL?
- SQL = **Structured Query Language**  
- Used for:
  - Querying structured/tabular data  
- Not tied to:
  - Specific database  
- Example:
  - Used even in Google Sheets  

### 3. Structure of Relational Databases
- Data stored as:
  - Tables  
- Each row:
  - Same set of columns  
- Supports:
  - Relationships between tables  

### 4. Advantages of RDBMS
- Structured data  
- Efficient indexing  
- Predictable schema  
- Strong consistency  

### 5. Limitations of RDBMS
- Fixed schema → inflexible  
- Example:
  - Student:
    - Hosteller → mess info  
    - Day scholar → gate pass  
- Result:
  - Many NULL values  
  - Inefficient storage  

### 6. Need for NoSQL
- Flexible data representation  
- Handle:
  - Heterogeneous data  
- Avoid:
  - Rigid schemas  

### 7. Document Databases
- Data stored as:
  - JSON-like documents  
- Each document:
  - Can have different structure  
- Example:
  - Some fields present in one document but not another  

### 8. Features of Document Databases
- Flexible schema  
- Nested data structures  
- Efficient retrieval via indexing  
- Example:
  - MongoDB  
  - Amazon DocumentDB  

### 9. Advantages of Document Databases
- No fixed schema  
- Natural mapping to application objects  
- Handles complex data easily  

### 10. Key-Value Stores
- Data stored as:
  - Key → Value pairs  
- Example:
  - `key = "apple"` → value = "red"  

### 11. Characteristics of Key-Value Stores
- Very fast lookup  
- Usually implemented using:
  - Hash tables  
- Limited queries:
  - Only exact match  

### 12. Examples of Key-Value Stores
- Redis  
- Memcached  
- BerkeleyDB  

### 13. Use Cases of Key-Value Stores
- Caching  
- Session storage  
- Fast lookups  

### 14. In-Memory Databases
- Stored in:
  - RAM  
- Benefits:
  - Extremely fast  
- Limitation:
  - Not persistent by default  

### 15. Column-Oriented Databases
- Store data by:
  - Columns instead of rows  
- Efficient for:
  - Column-based queries  

### 16. Use Case of Column Stores
- Example:
  - Find all users with a specific attribute  
- Faster because:
  - Data for that column stored together  

### 17. Wide Column Stores
- Large data per column  
- Nested structures inside columns  
- Used for:
  - Big data applications  

### 18. Graph Databases
- Data represented as:
  - Nodes + edges  
- Focus:
  - Relationships  

### 19. Use Cases of Graph Databases
- Social networks  
- Recommendation systems  
- Pathfinding  
- Example:
  - Neo4j  

### 20. Graph Query Types
- Shortest path  
- Connection discovery  
- Network traversal  

### 21. Time Series Databases (TSDB)
- Data indexed by:
  - Time  
- Example:
  - Logs  
  - Metrics  
- Queries:
  - Time range  
  - Aggregations  

### 22. TSDB Examples
- InfluxDB  
- Prometheus  
- Grafana (visualization layer)  

### 23. Why NoSQL?
- Better scalability  
- Flexible schemas  
- Optimized for specific use cases  

### 24. Meaning of NoSQL
- Originally:
  - "Not SQL"  
- Now:
  - **"Not Only SQL"**  

### 25. SQL vs NoSQL
- SQL:
  - Structured  
  - Fixed schema  
- NoSQL:
  - Flexible  
  - Schema-less  

### 26. ACID Properties
- Atomicity  
- Consistency  
- Isolation  
- Durability  

### 27. Transactions in Databases
- Example:
  - Creating a user  
- Must ensure:
  - Complete success or no change  

### 28. ACID Importance
- Critical for:
  - Financial systems  
- Ensures:
  - Data correctness  

### 29. Scalability Challenges
- Consistency:
  - Hard to maintain at scale  
- Multiple servers:
  - Data replication issues  

### 30. Eventual Consistency
- Data may be:
  - Temporarily inconsistent  
- Eventually:
  - Becomes consistent  

### 31. Example of Eventual Consistency
- Social media:
  - Friend updates appear with delay  
- Acceptable:
  - Non-critical systems  

### 32. Strong Consistency Requirement
- Financial transactions:
  - Must be exact  
- No room for delay  

### 33. NoSQL and ACID
- Not mutually exclusive  
- Some NoSQL databases:
  - Support ACID  
- Others:
  - Relax constraints  

### 34. Storage Considerations
- In-memory:
  - Fast but limited  
- Disk:
  - Slower but scalable  

### 35. Data Structure Adaptation
- Different storage:
  - Requires different structures  
- Optimization:
  - Depends on use case  

### 36. Key Takeaways
- NoSQL ≠ No SQL  
- Choose database based on:
  - Data type  
  - Query type  
  - Scale  
- Trade-offs:
  - Consistency vs performance  
- No single best database:
  - Depends on application needs

### Notes to be taken for `Activity Question 4`
1. 
---
### Week 7 Lecture 5 
#### NoSQL Databases, Data Storage Models, and ACID vs Scalability  
##### Description: Introduces NoSQL databases, compares them with relational databases, explores different data storage models (document, key-value, column, graph, time-series), and discusses ACID properties, consistency trade-offs, and scalability.

### 1. Introduction to NoSQL
- Traditional focus:
  - **Relational Databases (RDBMS)**  
- Limitation:
  - Fixed tabular structure  
- Alternative:
  - **NoSQL databases**  

### 2. What is SQL?
- SQL = **Structured Query Language**  
- Used for:
  - Querying structured/tabular data  
- Not tied to:
  - Specific database  
- Example:
  - Used even in Google Sheets  

### 3. Structure of Relational Databases
- Data stored as:
  - Tables  
- Each row:
  - Same set of columns  
- Supports:
  - Relationships between tables  

### 4. Advantages of RDBMS
- Structured data  
- Efficient indexing  
- Predictable schema  
- Strong consistency  

### 5. Limitations of RDBMS
- Fixed schema → inflexible  
- Example:
  - Student:
    - Hosteller → mess info  
    - Day scholar → gate pass  
- Result:
  - Many NULL values  
  - Inefficient storage  

### 6. Need for NoSQL
- Flexible data representation  
- Handle:
  - Heterogeneous data  
- Avoid:
  - Rigid schemas  

### 7. Document Databases
- Data stored as:
  - JSON-like documents  
- Each document:
  - Can have different structure  
- Example:
  - Some fields present in one document but not another  

### 8. Features of Document Databases
- Flexible schema  
- Nested data structures  
- Efficient retrieval via indexing  
- Example:
  - MongoDB  
  - Amazon DocumentDB  

### 9. Advantages of Document Databases
- No fixed schema  
- Natural mapping to application objects  
- Handles complex data easily  

### 10. Key-Value Stores
- Data stored as:
  - Key → Value pairs  
- Example:
  - `key = "apple"` → value = "red"  

### 11. Characteristics of Key-Value Stores
- Very fast lookup  
- Usually implemented using:
  - Hash tables  
- Limited queries:
  - Only exact match  

### 12. Examples of Key-Value Stores
- Redis  
- Memcached  
- BerkeleyDB  

### 13. Use Cases of Key-Value Stores
- Caching  
- Session storage  
- Fast lookups  

### 14. In-Memory Databases
- Stored in:
  - RAM  
- Benefits:
  - Extremely fast  
- Limitation:
  - Not persistent by default  

### 15. Column-Oriented Databases
- Store data by:
  - Columns instead of rows  
- Efficient for:
  - Column-based queries  

### 16. Use Case of Column Stores
- Example:
  - Find all users with a specific attribute  
- Faster because:
  - Data for that column stored together  

### 17. Wide Column Stores
- Large data per column  
- Nested structures inside columns  
- Used for:
  - Big data applications  

### 18. Graph Databases
- Data represented as:
  - Nodes + edges  
- Focus:
  - Relationships  

### 19. Use Cases of Graph Databases
- Social networks  
- Recommendation systems  
- Pathfinding  
- Example:
  - Neo4j  

### 20. Graph Query Types
- Shortest path  
- Connection discovery  
- Network traversal  

### 21. Time Series Databases (TSDB)
- Data indexed by:
  - Time  
- Example:
  - Logs  
  - Metrics  
- Queries:
  - Time range  
  - Aggregations  

### 22. TSDB Examples
- InfluxDB  
- Prometheus  
- Grafana (visualization layer)  

### 23. Why NoSQL?
- Better scalability  
- Flexible schemas  
- Optimized for specific use cases  

### 24. Meaning of NoSQL
- Originally:
  - "Not SQL"  
- Now:
  - **"Not Only SQL"**  

### 25. SQL vs NoSQL
- SQL:
  - Structured  
  - Fixed schema  
- NoSQL:
  - Flexible  
  - Schema-less  

### 26. ACID Properties
- Atomicity  
- Consistency  
- Isolation  
- Durability  

### 27. Transactions in Databases
- Example:
  - Creating a user  
- Must ensure:
  - Complete success or no change  

### 28. ACID Importance
- Critical for:
  - Financial systems  
- Ensures:
  - Data correctness  

### 29. Scalability Challenges
- Consistency:
  - Hard to maintain at scale  
- Multiple servers:
  - Data replication issues  

### 30. Eventual Consistency
- Data may be:
  - Temporarily inconsistent  
- Eventually:
  - Becomes consistent  

### 31. Example of Eventual Consistency
- Social media:
  - Friend updates appear with delay  
- Acceptable:
  - Non-critical systems  

### 32. Strong Consistency Requirement
- Financial transactions:
  - Must be exact  
- No room for delay  

### 33. NoSQL and ACID
- Not mutually exclusive  
- Some NoSQL databases:
  - Support ACID  
- Others:
  - Relax constraints  

### 34. Storage Considerations
- In-memory:
  - Fast but limited  
- Disk:
  - Slower but scalable  

### 35. Data Structure Adaptation
- Different storage:
  - Requires different structures  
- Optimization:
  - Depends on use case  

### 36. Key Takeaways
- NoSQL ≠ No SQL  
- Choose database based on:
  - Data type  
  - Query type  
  - Scale  
- Trade-offs:
  - Consistency vs performance  
- No single best database:
  - Depends on application needs
---
### Week 7 Lecture 5  
#### Database Scaling, Replication, and BASE vs ACID Trade-offs  
##### Description: Explains database scaling strategies, replication, redundancy vs performance, scale-up vs scale-out architectures, and contrasts ACID with BASE philosophy in distributed systems.

### 1. Introduction to Scaling
- Scaling = handling:
  - Increased data  
  - Increased users  
- Goal:
  - Maintain performance  
  - Ensure availability  

### 2. Data Replication
- Replication:
  - Multiple copies of data  
- Used for:
  - Performance  
  - Availability  

### 3. Redundancy vs Replication
#### Redundancy:
- Purpose:
  - Backup  
- Example:
  - Copy files to another device  
- Not optimized for:
  - Performance  

#### Replication:
- Purpose:
  - Performance improvement  
- Multiple servers:
  - Same data  
- Used for:
  - Faster query handling  

### 4. Benefits of Replication
- Multiple servers can:
  - Handle read requests  
- Improves:
  - Load balancing  
- Reduces:
  - Response time  

### 5. Limitation of Replication
- Same data center:
  - No disaster protection  
- Example:
  - Fire → all replicas lost  

### 6. Replication Complexity
- Requires:
  - Careful database design  
- Challenges:
  - Synchronization  
  - Consistency  

### 7. BASE Philosophy
- Used in:
  - NoSQL systems  
- Stands for:
  - Basically Available  
  - Soft State  
  - Eventually Consistent  

### 8. BASE Characteristics
- High availability  
- Data may be:
  - Temporarily inconsistent  
- Eventually:
  - Becomes consistent  

### 9. Replication in RDBMS
- Supported by:
  - MySQL  
  - PostgreSQL  
  - Oracle  
- Usually:
  - Same data center  
- Uses:
  - High-speed networks  

### 10. Geographical Replication Challenges
- Issues:
  - Network latency  
  - Delay in synchronization  
- Hard to maintain:
  - Strong consistency  

### 11. Scaling Approaches
#### 11.1 Scale-Up (Vertical Scaling)
- Increase:
  - CPU  
  - RAM  
  - Storage  
- Example:
  - Upgrade server  

### 12. Limitations of Scale-Up
- Requires:
  - Hardware upgrade  
- May require:
  - System restart  
- Expensive  

### 13. Scale-Out (Horizontal Scaling)
- Add:
  - More machines  
- Distribute:
  - Load across servers  

### 14. Advantages of Scale-Out
- Flexible  
- Easily expandable  
- Suited for:
  - Cloud environments  

### 15. Cloud-Based Scaling
- Providers:
  - AWS  
  - Google Cloud  
- Features:
  - Auto-scaling  
  - Dynamic resource allocation  

### 16. Scale-Out Workflow
- Add new server  
- Replicate data  
- Include in system pool  

### 17. Scale-Out vs ACID
- Problem:
  - Maintaining consistency  
- Result:
  - ACID harder to enforce  

### 18. NoSQL and Scaling
- Works well with:
  - Scale-out  
- Accepts:
  - Eventual consistency  

### 19. Application-Specific Trade-offs
- Financial systems:
  - Require ACID  
- Social/media systems:
  - Accept eventual consistency  

### 20. Example: E-Commerce Systems
- Product listings:
  - Can use NoSQL  
- Payments:
  - Must use ACID  

### 21. Consistency Trade-off
- Accept:
  - Slight delay in updates  
- Avoid:
  - Incorrect financial transactions  

### 22. Real-World Example
- Product availability:
  - May show item available  
- At purchase:
  - Item may be sold out  

### 23. Critical Systems Requirement
- Must ensure:
  - Strong consistency  
- No compromise:
  - Financial transactions  

### 24. Design Considerations
- Choose based on:
  - Application type  
- Trade-offs:
  - Performance vs consistency  

### 25. Key Takeaways
- Replication improves performance  
- Redundancy ensures backup  
- Scale-up:
  - Limited and expensive  
- Scale-out:
  - Flexible and cloud-friendly  
- NoSQL:
  - Better for large-scale distributed systems  
- ACID vs BASE:
  - Depends on application needs
---
### Week 7 Lecture 6  
#### Database Security, SQL Injection, and HTTPS  
##### Description: Covers database security concerns, SQL injection attacks, input validation, and the role of HTTPS in securing client-server communication.

### 1. Introduction to Database Security
- Security is critical in:
  - Web applications  
  - Database interactions  
- Improper handling:
  - Can lead to data leaks or destruction  

### 2. MVC and Database Access
- In MVC:
  - SQL queries → handled in **model**  
- Controller:
  - Sends requests  
- Model:
  - Interacts with database  

### 3. Danger of Direct SQL Usage
- Writing raw SQL using:
  - String concatenation  
- Risk:
  - Untrusted user input included directly  

### 4. HTML Form Input Example
- Inputs:
  - Username  
  - Password  
- Data sent to server:
  - Used to build SQL query  

### 5. Unsafe Query Construction
- Example:
  - `SELECT * FROM users WHERE name="input" AND pass="input"`  
- Problem:
  - Input inserted without validation  

### 6. SQL Injection Attack
- Malicious input:
  - Alters SQL query structure  
- Example:
  - `"" OR ""`  
- Effect:
  - Condition becomes always true  
- Result:
  - Returns all data  

### 7. Severe SQL Injection Example
- Input:
  - `; DROP TABLE users;`  
- Result:
  - Executes multiple queries  
- Outcome:
  - Database destruction  

### 8. Root Cause of SQL Injection
- Trusting:
  - External input  
- Lack of:
  - Validation and sanitization  

### 9. Input Validation
- Must ensure:
  - Only valid data is accepted  
- Checks include:
  - No special characters  
  - No SQL control symbols  
- Examples:
  - No `;`, `"`, `'`  

### 10. Data Format Validation
- Validate based on type:
  - Email → must match format  
  - Date → must be valid date  
- Prevents:
  - Invalid or malicious input  

### 11. Validation Timing
- Must happen:
  - Just before database query  
- Reason:
  - Client-side checks can be bypassed  

### 12. Bypassing Frontend Validation
- Attackers can:
  - Send direct HTTP requests  
- Example tools:
  - curl  
- Result:
  - Skip frontend checks entirely  

### 13. Other Security Threats
- Buffer overflows  
- Input overflow attacks  
- Encoding-based attacks  

### 14. Character Encoding Issues
- Different character sets:
  - Can mimic valid characters  
- Risk:
  - Server misinterpretation  

### 15. Consequences of Security Failures
- Data leakage  
- Data corruption  
- Unauthorized modifications  
- Financial/legal damage  

### 16. SQL Injection Definition
- Injecting malicious SQL into queries  
- Goal:
  - Manipulate database behavior  

### 17. Prevention Strategies
- Use:
  - Trusted frameworks  
- Benefits:
  - Pre-tested security mechanisms  

### 18. Framework Advantage
- Regular updates  
- Community-tested fixes  
- Reduced risk of missing edge cases  

### 19. HTTPS Overview
- Secure version of HTTP  
- Encrypts:
  - Client-server communication  

### 20. HTTP vs HTTPS
#### HTTP:
- Data is:
  - Plain text  
- Vulnerable to:
  - Interception  

#### HTTPS:
- Data is:
  - Encrypted  
- Secure against:
  - Eavesdropping  

### 21. Man-in-the-Middle Risk
- HTTP:
  - Data can be intercepted  
- HTTPS:
  - Prevents interception  

### 22. HTTPS Mechanism
- Uses:
  - SSL/TLS  
- Encrypts:
  - Entire communication channel  

### 23. Server Certificates
- Provided by:
  - Trusted authorities  
- Ensures:
  - Authenticity of server  

### 24. HTTPS Limitations
- Does NOT:
  - Validate input  
  - Prevent SQL injection  
- Only protects:
  - Data in transit  

### 25. Performance Considerations
- HTTPS:
  - Adds overhead  
- Affects:
  - Caching  
  - Proxy efficiency  

### 26. Security Layers
- Application security  
- Server security  
- Network security  
- Infrastructure security  

### 27. Deployment Awareness
- Must know:
  - Where app is running  
- Example:
  - Local server vs cloud  

### 28. Cloud Advantages
- Managed platforms:
  - Handle security patches  
- Examples:
  - Google App Engine  

### 29. Developer Responsibility
- Ensure:
  - Input validation  
- Prevent:
  - Injection attacks  

### 30. Key Takeaways
- Never trust user input  
- Always validate data  
- Use frameworks for safety  
- HTTPS protects communication, not logic  
- Security is multi-layered and critical
---
