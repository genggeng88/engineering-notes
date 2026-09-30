---
title: Transactions and Database Connections
tags: [java, spring, database, transactions]
---

# Transactions and Database Connections

A **connection** represents communication with a database. A **transaction** represents a logical unit of database work that should commit or roll back atomically.

## Connection Pool

Creating physical database connections is relatively expensive, so applications typically use a connection pool such as HikariCP.

```text
Requests
   │
   ▼
Connection Pool
├── Connection 1
├── Connection 2
└── Connection 3
   │
   ▼
Database
```

When all connections are busy, additional requests generally wait until a connection becomes available or a timeout occurs.

JdbcTemplate and Hibernate commonly obtain connections through a configured Spring `DataSource`.

## JdbcTemplate and `@Transactional`

A standalone database operation does not necessarily need an explicit `@Transactional` boundary in application code. Multiple related operations often do:

```java
@Transactional
public void transferMoney(long from, long to, BigDecimal amount) {
    jdbcTemplate.update(
        "UPDATE account SET balance = balance - ? WHERE id = ?",
        amount, from
    );

    jdbcTemplate.update(
        "UPDATE account SET balance = balance + ? WHERE id = ?",
        amount, to
    );
}
```

Both updates participate in the same transaction: either both commit or the transaction rolls back.

## Hibernate + Spring Transactions

```java
@Service
public class UserService {
    private final SessionFactory sessionFactory;

    public UserService(SessionFactory sessionFactory) {
        this.sessionFactory = sessionFactory;
    }

    @Transactional
    public void save(User user) {
        Session session = sessionFactory.getCurrentSession();
        session.persist(user);
    }
}
```

Spring manages the transaction lifecycle around the method.

## `getCurrentSession()` vs `openSession()`

`getCurrentSession()` typically returns a session associated with the current transaction/context and fits naturally with Spring-managed transactions.

`openSession()` creates an independent Hibernate session. If managed manually, the developer is responsible for transaction and session lifecycle:

```java
Session session = sessionFactory.openSession();
Transaction tx = null;

try {
    tx = session.beginTransaction();
    session.persist(entity);
    tx.commit();
} catch (Exception e) {
    if (tx != null) tx.rollback();
    throw e;
} finally {
    session.close();
}
```

For normal Spring applications, declarative transaction management with `@Transactional` is usually preferred.

## Key Takeaway

```text
Application
     ↓
Transaction
     ↓
JdbcTemplate / Hibernate
     ↓
DataSource
     ↓
Connection Pool
     ↓
Database
```

## Related
- [[jdbctemplate-vs-hibernate|JdbcTemplate vs Hibernate]]
- [[../hibernate/lazy-loading|Lazy Loading]]
