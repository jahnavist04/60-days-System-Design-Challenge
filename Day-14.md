# API Gateway 🚪

## What is an API Gateway?

An **API Gateway** is a server that acts as a single entry point for clients accessing multiple backend services.

Instead of clients communicating directly with every service, they communicate with the API Gateway.

             ┌── User Service
             |
Client → API Gateway ── Product Service
             |
             └── Order Service

---

## Why is an API Gateway Needed?

Consider an application with many microservices.

### Without an API Gateway

    Client
      |
      ├── User Service
      ├── Product Service
      ├── Order Service
      ├── Payment Service
      └── Notification Service

The client needs to know about every service.

This can make the architecture complicated.

### With an API Gateway

    Client
      |
      ↓
    API Gateway
      |
      ├── User Service
      ├── Product Service
      ├── Order Service
      ├── Payment Service
      └── Notification Service

The client only communicates with one entry point.

---

## How Does an API Gateway Work?

A client sends a request to the API Gateway.

    Client
      |
      ↓
    API Gateway
      |
      ↓
    Select Backend Service
      |
      ↓
    Backend Service
      |
      ↓
    Response

The gateway determines where the request should go.

---

## Request Routing

One of the main responsibilities of an API Gateway is **request routing**.

For example:

    /api/users
          ↓
    User Service

    /api/products
          ↓
    Product Service

    /api/orders
          ↓
    Order Service

The API Gateway routes each request to the appropriate service.

---

## Authentication

An API Gateway can also perform authentication.

    Client
      |
      ↓
    API Gateway
      |
      ├── Valid Token → Service
      |
      └── Invalid Token → Reject

This allows backend services to avoid repeating the same authentication logic.

---

## Rate Limiting

API Gateways can also enforce rate limits.

    Client
      |
      ↓
    API Gateway
      |
      ↓
    Rate Limiter
      |
      ↓
    Backend Service

This protects backend services from excessive traffic.

---

## Load Balancing

An API Gateway can distribute requests among multiple instances of a service.

                 ┌── Server 1
                 |
    Gateway ─────┼── Server 2
                 |
                 └── Server 3

This can improve scalability and availability.

---

## Request Transformation

An API Gateway can modify requests before forwarding them.

    Client Request
          |
          ↓
    API Gateway
          |
          ↓
    Transformed Request
          |
          ↓
    Backend Service

This can be useful when different clients require different formats.

---

## Response Aggregation

Sometimes a client needs data from multiple services.

### Without an API Gateway

    Client
      |
      ├── User Service
      ├── Order Service
      └── Product Service

### With an API Gateway

    Client
      |
      ↓
    API Gateway
      |
      ├── User Service
      ├── Order Service
      └── Product Service
      |
      ↓
    Combined Response
      |
      ↓
    Client

The gateway can combine the results into one response.

---

## API Gateway Architecture

A typical architecture may look like:

                    ┌── User Service
                    |
                    ├── Product Service
    Client → API Gateway ── Order Service
                    |
                    ├── Payment Service
                    |
                    └── Notification Service

The gateway becomes the main entry point to the backend system.

---

## Benefits of API Gateway

### 1. Single Entry Point

Clients communicate with one endpoint.

### 2. Security 🛡️

Authentication and authorization can be handled centrally.

### 3. Rate Limiting 🚦

The gateway can control incoming traffic.

### 4. Request Routing

Requests can be sent to the correct backend service.

### 5. Response Aggregation

Responses from multiple services can be combined.

---

## Disadvantages

An API Gateway can also introduce problems.

### 1. Single Point of Failure

If the gateway fails and there is no redundancy, clients may not reach backend services.

### 2. Additional Latency

Every request passes through the gateway.

### 3. Complexity

The gateway itself needs to be designed, monitored, and scaled.

---

## Real-World Example

Consider an e-commerce application.

                    ┌── User Service
                    |
                    ├── Product Service
    Customer → API Gateway ── Order Service
                    |
                    ├── Payment Service
                    |
                    └── Notification Service

The customer only interacts with the API Gateway.

The gateway handles routing, authentication, rate limiting, and communication with backend services.

---

## Key Takeaways

- An API Gateway acts as a single entry point for backend services.
- It routes requests to appropriate services.
- It can handle authentication and authorization.
- It can perform rate limiting.
- It can perform load balancing.
- It can aggregate responses from multiple services.
- It simplifies communication between clients and microservices.

## What I Learned Today

Today I learned how an API Gateway provides a single entry point between clients and multiple backend services.

It can centralize common responsibilities such as routing, authentication, rate limiting, and request processing.

