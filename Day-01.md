# Day 1 — System Design Basics

## What is System Design?

System design is the process of designing the architecture, components, databases, APIs, and communication between different parts of a software system.

The goal is to build a system that is:

* Scalable
* Reliable
* Available
* Maintainable
* Secure
* Efficient

## Why is System Design Important?

A small application can work perfectly with a few users, but problems start appearing when millions of users access it simultaneously.

System design helps us answer questions like:

* How will the system handle millions of users?
* Where will the data be stored?
* How will different services communicate?
* What happens if a server fails?
* How can we reduce response time?
* How can the system scale as users increase?

## Important Concepts

### 1. Scalability

The ability of a system to handle increasing numbers of users or requests.

There are two common approaches:

**Vertical Scaling:**
Increasing the resources of an existing server, such as CPU, RAM, or storage.

**Horizontal Scaling:**
Adding more servers to distribute the workload.

### 2. Availability

Availability refers to how often a system remains operational and accessible to users.

A highly available system should continue working even when some components fail.

### 3. Reliability

Reliability is the ability of a system to consistently perform its intended function correctly.

### 4. Performance

Performance describes how quickly a system responds to requests and processes workloads.

Important metrics include:

* Latency
* Throughput
* Response time

### 5. Fault Tolerance

A fault-tolerant system can continue operating even when one or more components fail.

## High-Level vs Low-Level Design

### High-Level Design (HLD)

Focuses on the overall architecture of the system.

Examples:

* Client
* Server
* Database
* Load balancer
* Cache
* Message queue

### Low-Level Design (LLD)

Focuses on the internal implementation of components.

Examples:

* Classes
* Objects
* Interfaces
* Design patterns
* Database schemas

## Day 1 Takeaway

System design is not just about writing code.

It is about deciding **how different components work together to build a system that can handle real-world scale, failures, and increasing demand.**

### Today's Goal

Understand the basic terminology before moving into individual system design components.

**Progress: 1 / 60 Days 🚀**
