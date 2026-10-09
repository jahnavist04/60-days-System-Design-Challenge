# Rate Limiting 🚦

## What is Rate Limiting?

**Rate limiting** is a technique used to control how many requests a user or client can make to a system within a specific period.

For example:

    100 requests per minute

This means a client can make a maximum of 100 requests in one minute.

---

## Why is Rate Limiting Needed?

Without rate limiting, a single user or application could send a huge number of requests.

    User
     |
     ├── Request
     ├── Request
     ├── Request
     ├── Request
     ├── Request
     ├── ...
     └── Millions of Requests
              |
              ↓
           Server ❌

This can cause:

- Server overload
- Slow response times
- Increased costs
- Denial-of-service attacks
- Poor experience for other users

---

## How Rate Limiting Works

A rate limiter checks every incoming request.

    Client
      |
      ↓
    Rate Limiter
      |
      ├── Allowed → Server
      |
      └── Limit Exceeded → Reject Request

For example:

    Limit = 5 requests/minute

Requests 1 to 5 are allowed.

Request 6 is rejected.

---

## Example

Suppose an API allows:

    100 requests per minute per user

A user sends:

    Request 1 → Allowed
    Request 2 → Allowed
    Request 3 → Allowed
    ...
    Request 100 → Allowed
    Request 101 → Rejected

The user must wait until the rate limit window allows more requests.

---

## Common Rate Limiting Algorithms

### 1. Fixed Window

The number of requests is counted within a fixed time interval.

For example:

    10:00 - 10:01
    Maximum = 100 requests

After the window ends, the counter resets.

    Requests
       |
    100|████████████
       |
      0|____________
         10:00 10:01

---

### 2. Sliding Window

The system continuously considers the most recent time period.

For example:

    Last 60 seconds

This provides smoother rate limiting than a simple fixed window.

---

### 3. Token Bucket

The system maintains a bucket containing tokens.

Each request consumes one token.

        Token Bucket
     ┌───────────────┐
     | ● ● ● ● ● ● ● |
     └───────────────┘
             |
          Request
             ↓
       Token consumed

Tokens are added to the bucket at a fixed rate.

If no token is available, the request may be rejected.

---

## Rate Limiting by User

A system can apply different limits to different users.

    User A → 100 requests/minute
    User B → 100 requests/minute
    User C → 100 requests/minute

This prevents one user from consuming all available resources.

---

## Rate Limiting by IP Address

Requests can also be limited based on IP address.

For example:

    IP: 192.168.1.10
    Limit: 100 requests/minute

If the IP exceeds the limit, additional requests can be rejected.

---

## Rate Limiting in APIs

Rate limiting is commonly used in APIs.

    Client
      |
      ↓
    API Gateway
      |
      ↓
    Rate Limiter
      |
      ↓
    Backend Services

This protects backend services from excessive traffic.

---

## What Happens When the Limit is Exceeded?

The server can reject the request.

For example, an API may return:

    HTTP 429 Too Many Requests

This tells the client that it has sent too many requests.

---

## Benefits of Rate Limiting

### 1. Protects Servers 🛡️

Prevents excessive traffic from overwhelming the system.

### 2. Fair Resource Usage

Prevents one client from consuming all resources.

### 3. Improves Availability

Helps keep the system available during traffic spikes.

### 4. Prevents Abuse

Makes it harder for clients to repeatedly send large numbers of requests.

---

## Real-World Example

Consider a login API.

### Without Rate Limiting

    Attacker
       |
       ↓
    Thousands of Login Requests
       |
       ↓
    Login Server

### With Rate Limiting

    Attacker
       |
       ↓
    Rate Limiter
       |
       ├── Allowed Requests
       |
       └── Excess Requests → Blocked

This helps protect the login service.

---

## Key Takeaways

- Rate limiting controls the number of requests a client can make.
- It protects systems from excessive traffic.
- Rate limits can be applied per user, IP address, API key, or other identifier.
- Common algorithms include Fixed Window, Sliding Window, and Token Bucket.
- HTTP 429 indicates too many requests.
- Rate limiting improves system stability and fairness.

## What I Learned Today

Today I learned that rate limiting is an important protection mechanism for APIs and large-scale systems.

It controls traffic, prevents abuse, and ensures that system resources are shared fairly.
