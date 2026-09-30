---
title: JdbcTemplate vs Hibernate
tags: [java, spring, database, hibernate, jdbc]
---

# JdbcTemplate vs Hibernate

JdbcTemplate and Hibernate both let Java applications interact with relational databases, but they operate at different abstraction levels.

## JdbcTemplate

Spring's `JdbcTemplate` is a thin abstraction over JDBC. Developers generally write SQL explicitly and commonly use a `RowMapper` to convert query results into Java objects.

```java
String sql = "SELECT id, name, email FROM users WHERE id = ?";

User user = jdbcTemplate.queryForObject(
    sql,
    userRowMapper,
    userId
);
```

### Advantages
- Explicit control over SQL
- Predictable queries
- Low abstraction overhead
- Useful for SQL-heavy applications
- Complex queries can be optimized directly

### Disadvantages
- More manual mapping
- More SQL to maintain
- Database-specific SQL can reduce portability
- Relationships are managed manually

## Hibernate

Hibernate is an **Object-Relational Mapping (ORM)** framework.

```java
@Entity
@Table(name = "users")
public class User {
    @Id
    private Long id;

    private String name;
    private String email;
}
```

Hibernate supports entity/relationship mapping, dirty checking, persistence contexts, lazy loading, first-level caching, JPQL/HQL, and SQL generation.

## Comparison

| Aspect | JdbcTemplate | Hibernate |
|---|---|---|
| Abstraction | JDBC abstraction | ORM |
| SQL | Usually manual | Often generated |
| Object Mapping | Manual / RowMapper | Entity mapping |
| Query Control | High | More abstract |
| Relationships | Manual | ORM relationships |
| Persistence Context | No | Yes |
| First-Level Cache | No | Yes |
| Learning Complexity | Lower | Higher |

Neither approach is universally better. JdbcTemplate is useful when SQL control matters; Hibernate is useful when ORM features reduce repetitive mapping and relationship-management code.

## Important Distinction

JdbcTemplate and Hibernate are not "old vs new" technologies. They represent different abstraction levels.

## Related
- [[transactions-and-connections|Transactions and Database Connections]]
- [[../hibernate/lazy-loading|Hibernate Lazy Loading]]
