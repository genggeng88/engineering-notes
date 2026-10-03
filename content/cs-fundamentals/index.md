---
title: CS Fundamentals
tags:
  - cs-fundamentals
---

# CS Fundamentals

Notes on programming languages and core computer science concepts that form the foundation of software engineering.

This section focuses on understanding **how programming languages work, how common abstractions are implemented, and how to use them effectively in real applications**.

---

## ☕ Java

My primary programming language for backend development and algorithm problem solving.

Topics include:

- Java Language Fundamentals
- JDK, JRE & JVM
- Object-Oriented Programming
- Collections
- Generics
- Exception Handling
- Concurrency & Multithreading
- JVM & Memory Management
- Spring
- Database Access
- Hibernate / JPA
- Transactions
- Caching
- Application Performance

→ [[java/index|Explore Java]]

---

## 🐍 Python

Notes on Python language fundamentals and commonly used patterns.

Topics will include:

- Python Language Fundamentals
- Data Types & Collections
- Functions
- Object-Oriented Programming
- Iterators & Generators
- Error Handling
- Concurrency
- Python Runtime

→ [[python/index|Explore Python]]

---

## 🐹 Golang

Notes on Go language fundamentals with an emphasis on backend and concurrent programming.

Topics will include:

- Go Language Fundamentals
- Structs & Interfaces
- Pointers
- Error Handling
- Goroutines
- Channels
- Context
- Synchronization
- Go Concurrency Patterns

→ [[golang/index|Explore Golang]]

---

## What I Focus On

Rather than documenting language syntax exhaustively, these notes focus on concepts that are useful for understanding and building software:

### Language Semantics

How does the language actually behave?

### Runtime

What happens when the program executes?

### Concurrency

How does the language handle multiple tasks executing concurrently?

### Data Structures

What abstractions does the standard library provide, and what are their performance characteristics?

### Engineering Trade-offs

When should one approach be preferred over another?

---

## Cross-Language Learning

Many concepts appear across languages with different implementations.

For example:

| Concept | Java | Python | Go |
|---|---|---|---|
| Concurrency Unit | Thread / Virtual Thread | Thread / Process / Coroutine | Goroutine |
| Synchronization | `synchronized`, Lock | Lock | Mutex / Channel |
| Interface | `interface` | Protocol / Duck Typing | `interface` |
| Error Handling | Exceptions | Exceptions | Explicit `error` |
| Generics | Generics | Type Hints / Generics | Generics |
| Memory Management | GC | Reference Counting + GC | GC |

Understanding these differences helps separate **fundamental computer science concepts** from language-specific implementations.