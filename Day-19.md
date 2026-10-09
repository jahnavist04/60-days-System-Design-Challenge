# SQL vs. NoSQL Databases 🗄️

## What is SQL?

SQL stands for Structured Query Language. SQL databases are commonly used to store structured data in tables containing rows and columns.

They typically use a predefined schema and support relationships between tables.

**Examples:**
- MySQL
- PostgreSQL
- Microsoft SQL Server
- Oracle Database

## What is NoSQL?

NoSQL databases use data models other than the traditional relational table model. They are often designed for flexible data structures, specific access patterns, or distributed workloads.

Depending on the database, they may use documents, key-value pairs, wide-column structures, or graphs.

**Examples:**
- MongoDB
- Redis
- Apache Cassandra
- Neo4j

## SQL vs. NoSQL

| Feature | SQL | NoSQL |
|---|---|---|
| Data model | Relational tables | Documents, key-value, wide-column, graph |
| Schema | Usually predefined | Often flexible or model-specific |
| Relationships | Supports joins and foreign keys | Depends on the database and data model |
| Transactions | Commonly supports ACID transactions | Varies by database; some support ACID transactions |
| Scaling | Often scales vertically; horizontal options exist | Many are designed for horizontal scaling |
| Query language | SQL is widely used | Query methods vary by database |
| Best suited for | Relational data and complex queries | Workloads suited to its particular data model |

## Types of NoSQL Databases

### 1. Document Database

Stores data as documents, often using JSON-like structures.

**Example:** MongoDB

**Use cases:** Product catalogs, user profiles, and content management systems.

### 2. Key-Value Database

Stores data as key-value pairs.

**Example:** Redis

**Use cases:** Caching, sessions, and fast lookups.

### 3. Wide-Column Database

Stores data in flexible column families and is designed for distributed data workloads.

**Example:** Apache Cassandra

**Use cases:** Large-scale event data, time-series workloads, and high-volume writes.

### 4. Graph Database

Stores entities as nodes and their connections as relationships.

**Example:** Neo4j

**Use cases:** Social networks, recommendation systems, and fraud detection.

## What is ACID?

ACID describes properties commonly used to ensure reliable database transactions.

- **Atomicity:** A transaction completes entirely or does not take effect.
- **Consistency:** A transaction preserves defined data rules.
- **Isolation:** Concurrent transactions are controlled to prevent unwanted interference.
- **Durability:** Committed changes persist according to the database's durability guarantees.

SQL databases commonly provide ACID transactions. Some NoSQL databases also support ACID transactions, so ACID is not exclusive to SQL.

## What is BASE?

BASE is a model often associated with highly available distributed systems.

- **Basically Available:** The system aims to remain available.
- **Soft State:** State may change as replicas and background processes update.
- **Eventual Consistency:** Replicas may converge if no new updates occur and synchronization continues.

Not every NoSQL database follows BASE, and consistency guarantees vary between systems.

## Scaling SQL and NoSQL Databases

### Vertical Scaling

Increasing the CPU, memory, or storage capacity of a single server.

### Horizontal Scaling

Adding more servers to distribute data or workload.

SQL databases can use replication, partitioning, sharding, and distributed architectures. Many NoSQL databases provide built-in support for distributing workloads across multiple nodes.

The best choice depends on the database, workload, consistency needs, and operational requirements.

## When Should You Choose SQL?

Choose a relational database when:

- Data has clear relationships.
- Complex joins and queries are important.
- Strong transactional guarantees are required.
- Data integrity constraints are important.

**Example:** Banking transactions, inventory systems, and order management.

## When Should You Choose NoSQL?

Consider a NoSQL database when:

- Its data model fits the application naturally.
- The workload needs a particular distributed access pattern.
- Flexible document structures are useful.
- High-volume writes or specialized key-value or graph operations are required.

**Example:** Session storage, product catalogs, event ingestion, and social graph queries.

## Can SQL and NoSQL Be Used Together?

Yes! Applications can use multiple database technologies when each serves a distinct purpose.

For example, an e-commerce application might use:

- PostgreSQL for orders and payments.
- Redis for caching and user sessions.
- MongoDB for flexible product information, if its document model fits the requirements.

This is sometimes called polyglot persistence.

However, each additional database introduces operational and data consistency complexity.

## Key Takeaways

- SQL databases organize data using relational tables.
- NoSQL databases support several alternative data models.
- SQL and NoSQL can both support transactions and distributed architectures, depending on the product.
- SQL is often a strong choice for relational data and complex transactions.
- NoSQL is useful when a particular data model or distributed workload calls for it.
- Choose a database based on requirements rather than assuming one category is always faster or better.

**Day 19 completed! 🚀**
