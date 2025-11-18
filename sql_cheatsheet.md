# SQL CHEATSHEET

## TABLE OF CONTENTS
1. ACID
2. CAP Theorem 
4. Joins 
5. Aggregations
6. Filters in queries
7. Normalization 
8. Indexes 
9. Transactions 
10. Locking mechanism 
11. Database Isolation Levels
12. Triggers

### 1. ACID PROPERTIES
- ACID ensures reliable transactions in databases.
- **A — Atomicity**
A transaction happens completely or not at all.
- Example:
Bank transfer: ₹500 from A → B
Deduct ₹500 from A
Add ₹500 to B
If second step fails, first step must be rolled back.

- **C — Consistency**
Database must move from one valid state to another.
Invalid data should never be written.

- Example:
If account balance cannot go below 0, the DB must enforce this.

- **I — Isolation**

Parallel transactions should not affect each other.

- Example:
Two users buying the last movie ticket — DB ensures only one gets it.

- **D — Durability**
Once a transaction is committed, it is permanently saved (even after crash).

### 2. CAP Theorem
- In a distributed system, you can only guarantee two out of the three:
Consistency (C), Availability (A), and Partition Tolerance (P).
- A distributed database must tolerate partitions (network failures). So in practice, it chooses CP or AP.
1. **Consistency (C)**
- All nodes see the same data at the same time. If you write data to node A and immediately read from node B, you should get the same value.
- Example:
User updates profile photo.
Write goes to Server A
User reads from Server B
If Server B immediately shows the updated photo → Consistent
- Guarantee:
Reads always return the latest committed data.
2. **Availability (A)**
- The system always responds, even if some nodes are down. The response may not be the latest data
- But the system never refuses the request
- Example:
If you ask for product price and the DB replies:
“Price: ₹499” → OK
“Error: Unable to get data” → NOT available
3. **Partition Tolerance (P)**
- The system continues to work even if the network breaks into two or more parts and nodes can’t talk to each other.
- This happens in real life very often:
network outages
server failures
dropped packetscluster split into halves ("split-brain")
A distributed system must handle partitions. So P is mandatory.

### 3. Joins
- A join combines rows from two (or more) tables based on a related column between them. Joins let you pull related data together without duplicating storage.
There are five types of joins:

  **1. Inner Join:** It returns rows where the join condition matches in both tables.
  
  **2. Left outer join(Left join):** It returns all rows from the left table; matching rows from right table or NULLs if no match.
  
  **3. Right outer join(Right join):** It is symmetric to LEFT JOIN all rows from right table, matching from left or NULL.
  
  **4. Full outer join:** It returns rows when there is a match in either left or right table. Non-matching sides produce NULLs.

  **5. Self join:** A table joined with itself (useful for hierarchical or comparing rows in same table).

### 4. Aggregation
- Aggregation functions operate on a set of rows and return a single value.
These functions summarize data.
- Common Aggregation Functions:
1. COUNT() – number of rows
2. SUM() – total of a numeric column
3. AVG() – average
4. MIN() – smallest
5. MAX() – largest
Aggregation functions always work together with GROUP BY (unless applied to entire table).

## 5. Filtering queries


| **Filter**      | **Description** |
|------------------|-----------------|
| `WHERE`          | Filters rows **before** grouping or aggregation; used for non-aggregated conditions. |
| `HAVING`         | Filters groups **after** aggregation; used with `GROUP BY`. |
| `AND`            | Combines multiple conditions (all must be true). |
| `OR`             | Combines conditions where at least one must be true. |
| `NOT`            | Negates a condition. |
| `IN`             | Checks if a value exists within a list of values. |
| `NOT IN`         | Checks if a value does **not** exist in a list. |
| `BETWEEN`        | Filters values within an inclusive range. |
| `LIKE`           | Pattern matching using `%` or `_`. |
| `NOT LIKE`       | Opposite of `LIKE`; excludes matching patterns. |
| `IS NULL`        | Returns rows where the column value is `NULL`. |
| `IS NOT NULL`    | Returns rows where the value is **not** `NULL`. |
| `EXISTS`         | True if a subquery returns at least one row. |
| `ANY / SOME`     | Compares a value with **any** value returned by a list/subquery. |
| `ALL`            | Compares a value with **all** values returned by a list/subquery. |

### 6. Normalization
- Reduce redundancy, avoid anomalies, improve data integrity.
**1NF (First Normal Form)***
Rule:
- No repeating groups
- Each cell = atomic value
- Each record = unique

**2NF (Second Normal Form)**
- Applies only when composite primary key exists.
Rule:
- Must be in 1NF
- No partial dependency
(Non-key column should depend on whole composite key)

**3NF (Third Normal Form)**
Rule:
- Must be in 2NF
- No transitive dependency
(Non-key attribute must depend ONLY on primary key)

**BCNF (Boyce-Codd Normal Form)**
3NF with stronger rules.
Rule:
- For every functional dependency A → B, A must be a super key
- Must be in 3NF
When BCNF is needed:
When non-key columns determine other non-key columns.

**4NF (Fourth Normal Form)**
Rule:
- Must be in BCNF
- No multi-valued dependencies

**5NF (Fifth Normal Form)**
 - Projection Join NF
Rule:
- Must be in 4NF
- All join dependencies must be from candidate keys
- Eliminates rare complex redundancy across 3+ table

### 7. Indexes
- Indexes are data structures that databases use to speed up searching, sorting, and joining.
- You can think of an index like the index at the back of a textbook → it helps you jump directly to the page instead of reading the whole book.
- What is an Index
An index is a separate, smaller, sorted data structure (usually B-Tree) that stores:
- the indexed column
- a pointer to the actual row in the table

### 8. Transactions
- A transaction is a group of SQL statements that run as a single unit of work.
- What is a Transaction?
A transaction ensures data consistency using ACID properties.
- Example: money transfer
Deduct ₹500 from Account A
Add ₹500 to Account B
These MUST happen together.
If step 2 fails → rollback step 1.

### 9. Locking Mechanism
- Locking is how a database controls concurrent access to data. It prevents two transactions from modifying the same row at the same time and ensures consistency.

**Shared Lock (S-Lock)** : Allows read, but no write. Multiple readers allowed.     
**Exclusive Lock (X-Lock)** : Allows write. Blocks all others.                         
**Row Lock**: Locks only the row.                                      
**Table Lock**: Locks entire table.                                      
**Intent Locks**: Signal that a transaction wants to lock rows in a table. 

### 10. Database Isolation Levels
- Isolation levels define how much transactions are allowed to interfere with each other.
Different isolation levels prevent different concurrency problems.

**Dirty Read**: Reading uncommitted data                                      
**Non-Repeatable Read**: Same SELECT returns different results in the same transaction 
**Phantom Read**: New rows appear in repeated SELECT                            

### 11. Triggers
- A trigger is an automatic operation executed by the database when an event occurs on a table—INSERT, UPDATE, DELETE.
Types of Triggers
1. BEFORE INSERT / UPDATE / DELETE
2. AFTER INSERT / UPDATE / DELETE
3. FOR EACH ROW or FOR EACH STATEMENT
