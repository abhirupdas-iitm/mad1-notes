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
  - Relationship table → student_id, course_id  
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
---
