---
title: Low-Level Design
tags:
  - lld
  - object-oriented-design
---

# Low-Level Design

Object-oriented design exercises focused on translating requirements into clean, extensible software models.

The emphasis is not only on producing working code, but on identifying the right **entities, responsibilities, relationships, and abstractions**.

## Fundamentals

Topics include:

- Object-Oriented Design
- SOLID Principles
- Composition vs. Inheritance
- Interfaces & Abstraction
- Encapsulation
- Design Patterns
- Dependency Management
- Extensibility

→ [[fundamentals/index|Explore LLD Fundamentals]]

---

## Design Problems

Practice problems for applying object-oriented design principles.

Examples include:

- Parking Lot
- Vending Machine
- Library Management
- Elevator System
- Reservation Systems

→ [[problems/index|Explore LLD Problems]]

---

## My Approach

For most LLD problems, I use the following process:

### 1. Clarify Requirements

Understand the core use cases and define what is inside or outside the scope.

### 2. Identify Core Entities

Find the important objects in the domain.

### 3. Define Core Operations

Walk through the major workflows the system needs to support.

### 4. Assign Responsibilities

Determine which class should own each behavior.

### 5. Define Relationships

Identify composition, inheritance, interfaces, and dependencies between objects.

### 6. Implement the Core Flow

Start with the simplest working design before introducing unnecessary abstractions.

### 7. Evaluate Extensibility

Consider how the design would change if new requirements were introduced.

---

## Key Principle

> Start from requirements and behavior, then derive the class structure.

The class diagram should be the result of understanding the problem — not the starting point.