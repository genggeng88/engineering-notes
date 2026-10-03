---
title: System Design
tags:
  - system-design
---

# System Design

Notes and design exercises for building scalable, reliable, and maintainable distributed systems.

This section focuses on both **system design fundamentals** and applying those concepts to real design problems.

## Fundamentals

Core concepts and patterns used across distributed systems.

- Scalability
- Availability & Reliability
- Load Balancing
- Caching
- Database Scaling
- Replication & Sharding
- Message Queues
- Event-Driven Architecture
- Consistency
- Distributed Locking
- Idempotency
- Rate Limiting
- Retry & Failure Handling

→ [[fundamentals/index|Explore System Design Fundamentals]]

---

## Design Problems

System design exercises and case studies.

For each problem, I try to follow a consistent process:

1. Clarify requirements
2. Estimate scale when necessary
3. Define APIs and data models
4. Design the high-level architecture
5. Identify bottlenecks and failure scenarios
6. Discuss scalability and reliability
7. Evaluate trade-offs

→ [[problems/index|Explore System Design Problems]]

---

## Design Principles

When designing a system, I try to answer four questions:

> **What are we building?**

> **What can fail?**

> **What happens when the system scales?**

> **What trade-offs are we making?**

The goal is not to find a single "correct" architecture, but to understand why a particular design makes sense under a given set of requirements.