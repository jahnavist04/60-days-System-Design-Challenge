# Day 8 — Database Replication 🔄

## What is Database Replication?

**Database replication** is the process of creating and maintaining copies of a database on multiple servers.

Instead of relying on a single database server, we can have multiple copies of the data.

```text
                 ┌── Database Replica 1
                 |
Application → Primary Database
                 |
                 └── Database Replica 2
```

The copies are called **replicas**.

---

## Why is Database Replication Needed?

As an application grows, a single database can become overloaded.

Replication can help with:

- Handling more read requests
- Improving availability
- Reducing database load
- Providing fault tolerance
- Recovering from database failures

For example:

```text
Users
  |
  ↓
Application
  |
  ↓
Primary Database
  |
  ├──→ Replica 1
  |
  └──→ Replica 2
```

The replicas can be used to handle additional read traffic.

---

## Primary and Replica

A common replication architecture uses a **Primary Database** and one or more **Replica Databases**.

### Primary Database

The primary database usually handles:

- `INSERT`
- `UPDATE`
- `DELETE`

```text
Application
     |
     ↓
Primary Database
     |
     ↓
Replicas
```

Changes made to the primary are replicated to the replicas.

---

### Replica Database

Replicas usually handle **read operations**.

```text
              ┌── Replica 1 → Read
              |
Primary ──────┼── Replica 2 → Read
              |
              └── Replica 3 → Read
```

This allows read traffic to be distributed across multiple databases.

---

## How Replication Works

Suppose a new user is added.

```text
Application
     |
     | INSERT
     ↓
Primary Database
     |
     | Replicate Changes
     ↓
Replica 1
Replica 2
Replica 3
```

The replicas eventually receive the same change.

This keeps multiple copies of the database available.

---

## Synchronous Replication

In **synchronous replication**, the primary waits for replicas to confirm that the data has been replicated.

```text
Application
     |
     ↓
Primary
  /   \
 ↓     ↓
R1     R2
  \   /
   ↓
Confirmation
```

### Advantage

- Stronger consistency between databases

### Disadvantage

- Can increase write latency
- If a replica is unavailable, writes may be affected

---

## Asynchronous Replication

In **asynchronous replication**, the primary does not wait for replicas before responding to the application.

```text
Application
     |
     ↓
Primary → Response
     |
     ├──→ Replica 1
     └──→ Replica 2
```

### Advantage

- Faster writes
- Better performance

### Disadvantage

- Replicas may temporarily contain older data
- Can result in **replication lag**

---

## What is Replication Lag?

**Replication lag** occurs when a replica has not yet received the latest changes from the primary.

For example:

```text
Primary:
User Balance = ₹1000

Replica:
User Balance = ₹500
```

For a short period, the replica may contain outdated information.

This is an important consideration when designing distributed systems.

---

## What Happens if the Primary Fails?

Replication can improve availability.

For example:

```text
              ❌ Primary
                 |
                 X
                 |
        ┌────────┴────────┐
        ↓                 ↓
    Replica 1         Replica 2
       ✅                 ✅
```

A replica can potentially be promoted to become the new primary.

This process is commonly called **failover**.

---

## Read Scaling

One of the biggest advantages of replication is **read scaling**.

Imagine an application receiving:

```text
1,000,000 read requests
100,000 write requests
```

Instead of sending all requests to one database, we can distribute reads across replicas.

```text
                     ┌── Replica 1
                     |
Users → Application ─┼── Replica 2
                     |
                     ├── Replica 3
                     |
                     └── Primary
                          ↑
                       Writes
```

This reduces the read load on the primary database.

---

## Real-World Example

Consider a social media application.

Millions of users may constantly view posts.

Most operations are reads:

```text
View Post
View Profile
View Comments
View Likes
```

Instead of making the primary database handle every read, replicas can handle read traffic.

```text
                    ┌── Read Replica 1
                    |
Users → Application ├── Read Replica 2
                    |
                    └── Primary Database
                            ↑
                          Writes
```

This allows the system to handle a much larger number of users.

---

## Key Takeaways

- Database replication creates multiple copies of data.
- A **primary database** usually handles writes.
- **Replicas** can handle read operations.
- Replication can improve availability and read scalability.
- Synchronous replication provides stronger consistency but can increase latency.
- Asynchronous replication provides better performance but can cause replication lag.
- Failover can allow a replica to take over if the primary fails.

## What I Learned Today

Today I learned that a single database can become a bottleneck as a system grows.

Database replication allows us to create multiple copies of data and distribute read traffic, while also improving the system's availability and fault tolerance.

> **One database can work. Multiple synchronized databases can scale. 🔄🚀**
