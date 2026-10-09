# Database Replication 🗄️

## What is Database Replication?

Database replication is the process of copying and maintaining data across multiple database servers.

It improves availability, supports read scalability, and helps applications continue operating when a database server fails.

## Why is Database Replication Needed?

Imagine an application with thousands of users accessing the database simultaneously.

A single database server may become overloaded or unavailable.

Replication allows multiple database copies to serve requests and can provide additional resilience.

## How Does Database Replication Work?

```text
              Application
                   |
                   v
             Primary Database
                   |
             Replication
              /         \
             v           v
       Replica 1      Replica 2
```

1. The application writes data to the primary database.
2. The primary database sends changes to its replicas.
3. Replicas apply the changes to their own copies of the data.
4. Applications can read from replicas when the system is configured to support it.

## Types of Database Replication

### 1. Primary-Replica Replication

One database acts as the primary, while other databases act as replicas.

- Writes are typically sent to the primary.
- Replicas receive updates from the primary.
- Read queries can be distributed across replicas.
- The primary may become a bottleneck if it handles too many writes.

### 2. Synchronous Replication

The primary waits for the required replica acknowledgements before confirming a write, depending on the database's configuration.

**Advantages:**
- Can provide stronger consistency guarantees.
- Helps ensure changes reach the required replicas before confirmation.

**Disadvantages:**
- Can increase write latency.
- Network or replica failures can affect write availability.

### 3. Asynchronous Replication

The primary confirms a write before all replicas have applied the change.

**Advantages:**
- Usually offers lower write latency.
- The primary does not need to wait for every replica.

**Disadvantages:**
- Replicas may temporarily contain outdated data.
- Recent writes may be lost during certain failures before replication completes.

### 4. Multi-Primary Replication

Multiple database nodes can accept writes.

**Advantages:**
- Supports writes across multiple locations.
- Can improve write availability in some architectures.

**Disadvantages:**
- Concurrent updates can cause conflicts.
- Conflict resolution and consistency become more complex.

## Read Scaling with Replication

Replication can distribute read traffic across several database servers.

```text
                 Application
                 /          \
             Writes         Reads
                |              |
                v              v
             Primary       Read Router
                           /         \
                          v           v
                     Replica 1    Replica 2
```

This is useful when an application performs many more reads than writes.

For example, a news website may receive thousands of article views for every article published.

## Replication Lag

Replication lag is the delay between a change being committed on the primary and becoming available on a replica.

For example, a user updates their profile, but an immediate read from a replica may still return the previous profile details.

Possible solutions include:

- Reading recent updates from the primary.
- Waiting until the replica has applied the required change.
- Using database-specific consistency mechanisms.
- Monitoring replication lag.

## Failover

Failover occurs when the system switches database responsibilities after a failure.

If the primary database becomes unavailable, a healthy replica may be promoted to become the new primary.

A failover system should consider:

- Replica health.
- Data freshness.
- Whether the old primary is truly unavailable.
- Preventing two primaries from accepting conflicting writes.
- Recovery of the failed server.

Automatic failover must be designed carefully to avoid data loss and split-brain situations.

## Replication vs. Sharding

| Feature | Replication | Sharding |
|---|---|---|
| Main purpose | Maintain copies of data | Split data across partitions |
| Data distribution | Same data on multiple nodes | Different data across shards |
| Read scaling | Often improves read capacity | Can distribute reads and writes |
| Write scaling | Limited in primary-replica setups | Can improve write capacity |
| Complexity | Consistency and failover | Partitioning and shard routing |

Replication and sharding can also be used together.

## Advantages of Database Replication

- Improves availability.
- Supports read scaling.
- Provides additional copies of data.
- Can support disaster recovery.
- Helps distribute database traffic.

## Challenges of Database Replication

- Replication lag can produce stale reads.
- Synchronous replication can increase latency.
- Failover requires careful coordination.
- Replicas consume storage and resources.
- Replication alone is not a complete backup strategy.

## Real-World Example

Consider an e-commerce application with a large number of product searches.

The primary database handles product updates, while read replicas serve product browsing requests.

If the primary fails, a replica may be promoted through a configured failover process.

This architecture can improve read capacity and resilience, provided replication and failover are configured correctly.

## Key Takeaways

- Database replication maintains copies of data across multiple servers.
- Primary-replica replication commonly separates writes from reads.
- Synchronous and asynchronous replication have different consistency and latency trade-offs.
- Replication lag can cause stale reads.
- Failover can improve availability but requires careful coordination.
- Replication and sharding solve different problems and can be combined.
