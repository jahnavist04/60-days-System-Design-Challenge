# Database Sharding 🧩

## What is Database Sharding?

Database sharding is a technique that divides a large database into smaller parts called **shards**. Each shard stores a subset of the overall data and can run on a separate database server.

Instead of storing all the data on one server, the application distributes it across multiple servers.

## Why is Database Sharding Needed?

Imagine an e-commerce application with millions of users and billions of orders.

A single database server may run out of storage or struggle to handle the increasing traffic.

Sharding distributes data across multiple servers, allowing the system to scale horizontally.

## How Does Database Sharding Work?

```text
             Application
                  |
                  v
             Shard Router
             /     |     \
            v      v      v
        Shard 1  Shard 2  Shard 3
        Users    Users    Users
        1-1000   1001-    2001-
                 2000     3000
```

1. The application receives a request.
2. A shard key identifies which shard contains the required data.
3. The shard router directs the request to the appropriate shard.
4. The selected shard processes the request and returns the result.

## What is a Shard Key?

A shard key is a field used to determine how records are distributed across shards.

Examples include:

- User ID
- Customer ID
- Order ID
- Geographic region

Choosing a good shard key is important because it affects data distribution, query performance, and scalability.

## Types of Sharding

### 1. Range-Based Sharding

Data is divided into ranges based on the shard key.

Example:

- Shard 1: User IDs 1–1000
- Shard 2: User IDs 1001–2000
- Shard 3: User IDs 2001–3000

**Advantages:**
- Simple to understand.
- Efficient for queries involving ranges.

**Disadvantages:**
- Some shards may receive more traffic than others.
- New records may overload a particular shard if the key increases sequentially.

### 2. Hash-Based Sharding

A hash function is applied to the shard key to determine the destination shard.

Example:

```text
Shard Number = Hash(User ID) % Number of Shards
```

**Advantages:**
- Can distribute records more evenly.
- Reduces dependence on sequential key ranges.

**Disadvantages:**
- Range queries may require accessing multiple shards.
- Changing the number of shards can require data redistribution, depending on the strategy.

### 3. Geographic Sharding

Data is partitioned according to geographical regions.

Example:

- Shard 1: Asia
- Shard 2: Europe
- Shard 3: North America

**Advantages:**
- Can reduce latency for regional users.
- Helps support regional data residency requirements.

**Disadvantages:**
- Traffic can be uneven across regions.
- Cross-region queries and replication can become complex.

## Sharding vs. Replication

| Feature | Sharding | Replication |
|---|---|---|
| Purpose | Distributes data | Creates copies of data |
| Data on each node | Usually a subset | Often a copy of the same dataset |
| Storage capacity | Can increase across shards | Copies require additional storage |
| Write scaling | Can improve write capacity | Depends on the replication architecture |
| Complexity | Shard routing and rebalancing | Consistency and failover |

Both techniques can be used together.

## Challenges of Sharding

### 1. Choosing a Shard Key

A poor shard key can create uneven data distribution or hot spots.

### 2. Cross-Shard Queries

Queries involving data across multiple shards may require extra coordination and can be slower.

### 3. Rebalancing

When shards become uneven or capacity grows, data may need to be redistributed.

### 4. Transactions

Transactions spanning multiple shards can be more complex than transactions within a single shard.

### 5. Operational Complexity

Monitoring, backups, schema changes, and failure recovery become more complicated.

## What is a Hot Shard?

A hot shard is a shard that receives significantly more traffic or workload than other shards.

For example, if a popular celebrity's account receives millions of requests, the shard storing that account may become overloaded.

Possible solutions include selecting a better shard key, distributing hot data, and caching frequently accessed records.

## Real-World Example

Consider a social media application with millions of users.

The database is partitioned by user ID across several shards. Each shard stores information for a subset of users.

When a user opens their profile, the application uses the user's ID to locate the correct shard.

As the platform grows, additional shards can be introduced, although adding capacity may require data migration or rebalancing.

## Advantages of Sharding

- Supports horizontal scaling.
- Distributes storage across servers.
- Can improve performance for appropriately routed queries.
- Reduces the workload handled by an individual database server.
- Allows capacity to grow as data increases.

## Key Takeaways

- Sharding divides a database into smaller partitions called shards.
- A shard key determines where records are stored.
- Range-based, hash-based, and geographic sharding are common approaches.
- Poor shard keys can cause hot spots and uneven workloads.
- Cross-shard queries and rebalancing add complexity.
- Sharding and replication solve different problems and can work together.
