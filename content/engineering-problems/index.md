---
title: Random Engineering Problems
tags:
  - engineering
  - backend
  - problem-solving
---

# Random Engineering Problems

Practical software engineering problems that don't fit neatly into traditional algorithm, system design, or low-level design categories.

These problems focus on turning **ambiguous product requirements into reliable implementations**.

They often involve a combination of:

- API design
- Database transactions
- Concurrency
- Background processing
- Message queues
- Scheduling
- Idempotency
- Retry strategies
- Failure recovery
- Data consistency

---

## Problems

### Benefit Enrollment Processing

Design a system that processes benefit enrollments after an enrollment window closes.

Key considerations include:

- enrollment state transitions
- scheduled processing
- multiple application instances
- background workers
- retries
- idempotency
- partial failures

→ [[benefit-enrollment|Benefit Enrollment Processing]]

### Employee Data File Import

Design a system that allows users to upload a large employee data file and reliably process its records.

Key considerations include:

- file validation
- large file processing
- asynchronous jobs
- worker concurrency
- partial failures
- retries
- progress tracking
- idempotency

→ [[employee-data-import|Employee Data File Import]]

---

## How I Approach These Problems

Unlike algorithm problems, these problems usually don't have one exact solution.

I generally start with:

### 1. Clarify the Requirement

What does the user actually expect to happen?

### 2. Define the Happy Path

Walk through the simplest successful flow from beginning to end.

### 3. Identify State

What data needs to be persisted, and what states can it transition through?

### 4. Think About Concurrency

What happens if two threads, workers, or application instances process the same resource?

### 5. Think About Failure

What happens if the application crashes halfway through?

What happens if an external dependency fails?

### 6. Design Recovery

Consider:

- retries
- idempotency
- dead-letter handling
- transaction boundaries
- resumability

### 7. Consider Scale

Only after the basic design is correct:

> What changes when the workload becomes much larger?

---

## Key Principle

> Design the happy path first, then systematically break it.

A production-ready design comes from understanding not only how the system works when everything succeeds, but also how it behaves when things fail.