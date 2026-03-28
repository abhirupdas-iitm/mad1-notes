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
