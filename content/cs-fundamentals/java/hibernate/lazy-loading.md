---
title: Hibernate Lazy Loading
tags: [java, hibernate, jpa, database]
---

# Hibernate Lazy Loading

Lazy loading is a fetching strategy where associated data is not loaded until it is actually accessed.

```java
@Entity
public class User {
    @OneToMany(mappedBy = "user", fetch = FetchType.LAZY)
    private List<Order> orders;
}
```

Fetching the user does not necessarily fetch the orders immediately:

```java
User user = entityManager.find(User.class, 1L);
```

Later, `user.getOrders()` may trigger another database query.

## Why Use Lazy Loading?

It can avoid retrieving associated data that is never used. If an API only needs a user's id and name, loading thousands of orders would be unnecessary.

## JPA Default Fetch Types

| Relationship | Default |
|---|---|
| `@OneToMany` | LAZY |
| `@ManyToMany` | LAZY |
| `@ManyToOne` | EAGER |
| `@OneToOne` | EAGER |

Relying blindly on defaults is usually not ideal. Fetching behavior should be selected based on each use case.

## Trade-Off

Lazy loading can reduce unnecessary fetching, but can also introduce:
- additional queries
- N+1 query problems
- `LazyInitializationException`

> Lazy loading is not automatically a performance optimization. It is a tool for controlling when related data is fetched.

## Related
- [[lazy-initialization-exception|LazyInitializationException]]
- [[../spring-data/jdbctemplate-vs-hibernate|JdbcTemplate vs Hibernate]]
