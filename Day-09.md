# Database Sharding 🔀

## What is Database Sharding?

Database sharding is a technique used to split a large database into smaller parts called **shards**.

Each shard stores a portion of the total data and can be hosted on a different server.

Instead of storing all data on a single database server, the data is distributed across multiple servers.


                Application
                     |
               Sharding Layer
              /       |       \
             /        |        \
        Shard 1    Shard 2    Shard 3
        Users 1    Users 2    Users 3

Why Do We Need Sharding?

As an application grows, a single database may become a bottleneck.

Sharding helps with:

Handling large amounts of data
Distributing database load
Improving scalability
Increasing storage capacity
Supporting large numbers of users
How Does Sharding Work?

Data is divided based on a shard key.

For example, users can be divided based on their user ID:

User ID 1–1000       → Shard 1
User ID 1001–2000    → Shard 2
User ID 2001–3000    → Shard 3

The shard key determines which shard will store a particular piece of data.

Types of Sharding
1. Range-Based Sharding

Data is divided into specific ranges.

1–1000       → Shard 1
1001–2000    → Shard 2
2001–3000    → Shard 3
2. Hash-Based Sharding

A hash function is used to determine which shard stores the data.

hash(user_id) → Shard

This can help distribute data more evenly across shards.

3. Geographic Sharding

Data is divided based on geographical location.

India       → Shard 1
USA         → Shard 2
Europe      → Shard 3
Sharding vs Replication
Sharding	Replication
Splits data	Copies data
Improves scalability	Improves availability
Each shard stores different data	Replicas store copies of data
Helps handle large datasets	Helps handle failures and read load
Advantages of Sharding
Scalability: More servers can be added as data grows.
Performance: Database load is distributed across multiple servers.
Storage: Large datasets can be distributed across multiple machines.
Availability: Failure of one shard does not necessarily affect all data.
Disadvantages of Sharding
More complex database architecture
Difficult to choose the correct shard key
Queries across multiple shards can be complicated
Rebalancing data can be difficult
Real-World Example

Imagine an application with millions of users.

Instead of storing all users in one database:

                 Users Database
                      |
          ┌───────────┼───────────┐
          ↓           ↓           ↓
       Shard 1     Shard 2     Shard 3
       Users       Users       Users
       1–1M        1M–2M       2M–3M

Each shard handles a portion of the users.

This allows the system to distribute the workload across multiple database servers.

Key Takeaway

Sharding = Splitting data across multiple databases or servers.

Replication = Creating copies of the same data.

Sharding is mainly used to improve scalability and performance when a database becomes very large.
