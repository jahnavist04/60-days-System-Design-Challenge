# Load Balancing ⚖️

## What is Load Balancing?

Load balancing is the process of distributing incoming network traffic across multiple servers to prevent any single server from becoming overloaded.

It improves application performance, availability, and reliability.

## Why is Load Balancing Needed?

Imagine an application receiving thousands of requests every second. A single server may become slow or crash.

A load balancer distributes these requests across multiple servers.

### Without Load Balancing

```text
         Client Requests
                |
                v
          Single Server
                |
        Server Overloaded
```

### With Load Balancing

```text
             Clients
                |
                v
          Load Balancer
          /     |     \
         v      v      v
      Server  Server  Server
         1      2       3
```

## How Does Load Balancing Work?

1. Clients send requests to the load balancer.
2. The load balancer selects an available backend server.
3. The selected server processes the request.
4. The response is returned to the client.

## Types of Load Balancers

### 1. Layer 4 Load Balancer

- Works at the transport layer.
- Uses information such as IP addresses and TCP/UDP ports.
- Does not inspect application-level HTTP content.
- Usually offers efficient traffic distribution.

### 2. Layer 7 Load Balancer

- Works at the application layer.
- Can route requests based on URLs, HTTP headers, cookies, or hostnames.
- Supports application-aware routing.
- Commonly used for HTTP and HTTPS traffic.

## Load Balancing Algorithms

### 1. Round Robin

Distributes requests to servers in a fixed, repeating order.

Example: Server 1 → Server 2 → Server 3 → Server 1.

### 2. Weighted Round Robin

Servers with higher assigned weights receive a larger share of requests.

### 3. Least Connections

Routes requests to the server with the fewest active connections.

### 4. IP Hash

Uses the client's IP address to select a server, helping requests from the same client reach the same server when the configuration remains stable.

## Health Checks

A load balancer periodically checks whether backend servers are healthy.

- Healthy servers receive traffic.
- Unhealthy servers can be temporarily removed from rotation.
- Traffic can be routed to other healthy servers.

## Advantages of Load Balancing

- Improves application availability.
- Prevents individual servers from becoming overloaded.
- Improves scalability.
- Supports fault tolerance.
- Helps distribute traffic efficiently.

## Challenges

- The load balancer itself can become a bottleneck.
- Session management may require additional configuration.
- Incorrect health checks can route traffic poorly.
- High availability may require multiple load balancers.

## Real-World Example

Consider an e-commerce application during a major sale.

Thousands of users browse products and place orders simultaneously. A load balancer distributes requests across several application servers so that traffic is handled more efficiently.

## Key Takeaways

- Load balancing distributes incoming requests across multiple servers.
- Layer 4 operates at the transport layer, while Layer 7 operates at the application layer.
- Round Robin and Least Connections are common load balancing algorithms.
- Health checks help prevent traffic from being sent to unhealthy servers.
- Load balancing improves scalability and availability.

**Day 15 completed! 🚀**
