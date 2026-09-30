---
title: LazyInitializationException
tags: [java, hibernate, database]
---

# LazyInitializationException

A `LazyInitializationException` occurs when Hibernate tries to initialize a lazily loaded association after the required session/persistence context is no longer available.

```text
Transaction
    ├── Load User
    └── orders NOT loaded
    ↓
Transaction ends / Session closes
    ↓
user.getOrders()
    ↓
LazyInitializationException
```

## Approaches

### 1. Fetch Required Data Inside the Transaction

The required association can be loaded while the persistence context is active. However, manually touching relationships merely to initialize them can become difficult to maintain.

### 2. `JOIN FETCH`

Fetch the required relationship explicitly:

```java
User user = entityManager
    .createQuery("""
        SELECT u
        FROM User u
        JOIN FETCH u.orders
        WHERE u.id = :userId
        """, User.class)
    .setParameter("userId", userId)
    .getSingleResult();
```

### 3. Entity Graph

JPA Entity Graphs allow a use case to specify which associations should be fetched without permanently changing the entity's default fetch strategy.

### 4. DTO Projection

If the application only needs a subset of fields, query directly into a DTO rather than loading a large entity graph.

### 5. Open Session in View (OSIV)

OSIV keeps the persistence context available for more of the web request. It can prevent some lazy initialization errors, but can also cause database queries in unexpected places such as serialization. It should be treated as a trade-off rather than a universal fix.

## What About `FetchType.EAGER`?

Changing every relationship to `EAGER` is usually not a good general solution because it can cause unnecessary fetching and make query behavior harder to control.

A better question is:

> What data does this specific use case require?

Then fetch that data intentionally.

## Related
- [[lazy-loading|Hibernate Lazy Loading]]
- [[../spring-data/transactions-and-connections|Transactions and Database Connections]]
