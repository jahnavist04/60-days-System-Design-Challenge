# Load Balancing ⚖️

## What is Load Balancing?

**Load balancing** is the process of distributing incoming network traffic across multiple servers.

When an application has a large number of users, sending all requests to a single server can overload it.

A **Load Balancer** sits between the users and the servers and distributes requests among them.

```text
                 ┌── Server 1
                 |
Users → Load Balancer ── Server 2
                 |
                 └── Server 3
```

This helps prevent one server from handling too much traffic.

---

## Why is Load Balancing Needed?

Imagine an application with only one server:

```text
Users
  |
  ↓
Server
  |
  ↓
Database
```

As the number of users increases, the server may become overloaded.

This can cause:

- Slow response times
- Server crashes
- Poor user experience
- Downtime

With a load balancer, traffic can be distributed across multiple servers.

```text
                    ┌── Server 1
                    |
Users → Load Balancer ├── Server 2
                    |
                    └── Server 3
```

---

## How Does a Load Balancer Work?

When a user sends a request, it first reaches the **Load Balancer**.

The load balancer then decides which server should handle the request.

```text
User Request
     |
     ↓
Load Balancer
     |
     ├──→ Server 1
     |
     ├──→ Server 2
     |
     └──→ Server 3
```

The response is then sent back to the user.

---

## Load Balancing Algorithms

A load balancer can use different methods to decide where to send requests.

### 1. Round Robin 🔄

Requests are distributed in order.

```text
Request 1 → Server 1
Request 2 → Server 2
Request 3 → Server 3
Request 4 → Server 1
Request 5 → Server 2
```

This works well when servers have similar capacity.

---

### 2. Least Connections

The request is sent to the server that currently has the **fewest active connections**.

```text
Server 1 → 10 connections
Server 2 →  5 connections
Server 3 →  8 connections
```

The next request would be sent to **Server 2**.

---

### 3. IP Hash

The user's IP address is used to determine which server receives the request.

```text
User A → Server 1
User B → Server 2
User C → Server 3
```

This can help keep requests from the same user going to the same server.

---

## Health Checks ❤️‍🩹

Load balancers can perform **health checks** on servers.

For example:

```text
Load Balancer
     |
     ├── Server 1 ✅
     |
     ├── Server 2 ❌
     |
     └── Server 3 ✅
```

If Server 2 fails, the load balancer can stop sending requests to it.

This improves the **availability and reliability** of the system.

---

## Benefits of Load Balancing

### Scalability 📈

More servers can be added to handle increasing traffic.

### High Availability 🛡️

If one server fails, requests can be sent to other healthy servers.

### Better Performance ⚡

Traffic is distributed instead of overwhelming a single server.

### Fault Tolerance 🔧

The system can continue working even when one or more servers fail.

---

## Real-World Example

Consider an online shopping website during a major sale.

Millions of users may send requests at the same time.

Instead of:

```text
Millions of Users
       |
       ↓
 Single Server ❌
```

we can use:

```text
                    ┌── Server 1
                    |
Millions of Users → Load Balancer ── Server 2
                    |
                    ├── Server 3
                    |
                    └── Server 4
```

The load balancer distributes the traffic across multiple servers, allowing the application to handle much higher traffic.

---

## Key Takeaways

- A load balancer distributes traffic across multiple servers.
- It helps prevent individual servers from becoming overloaded.
- Common algorithms include **Round Robin, Least Connections, and IP Hash**.
- Health checks help identify failed servers.
- Load balancing improves **scalability, availability, performance, and fault tolerance**.

## What I Learned Today

Today I learned how multiple servers can work together to handle large amounts of traffic.

A load balancer acts as the **traffic controller** of a system, directing requests to healthy servers and helping the application remain available as traffic increases.

> **Don't let one server carry the whole load. ⚖️🚀**
