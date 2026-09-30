---
title: Diagnosing Slow Applications
tags: [performance, backend, observability, system-design]
---

# Diagnosing Slow Applications

When an application becomes slow, the first step should not be immediately adding caching, indexes, or servers.

> Identify where the latency comes from.

```text
Measure
   ↓
Identify Bottleneck
   ↓
Form Hypothesis
   ↓
Optimize
   ↓
Measure Again
```

## 1. Measure the Problem

Useful metrics include:
- request latency and p50/p95/p99
- throughput and error rate
- CPU and memory utilization
- GC activity
- database query latency
- connection pool utilization
- external service latency

Useful techniques include metrics, distributed tracing, structured logs, profilers, and database query analysis.

## 2. Determine the Bottleneck

### CPU

Possible causes include expensive computation, inefficient algorithms, excessive serialization, or excessive GC.

### Database

Look for:
- slow queries
- missing indexes
- N+1 queries
- large table scans
- lock contention
- exhausted connection pools

Use `EXPLAIN` / `EXPLAIN ANALYZE` to inspect query plans. Possible improvements include indexing, query rewriting, batching, pagination, caching, schema changes, or partitioning.

Sharding is a major architectural decision and should not be the first response to a slow query.

### External Services / I/O

Possible techniques include timeouts, retries with backoff, caching, batching, asynchronous processing, and circuit breakers.

### High Traffic

If individual requests are efficient but total traffic exceeds application capacity, horizontal scaling may help. Scaling application instances will not necessarily solve a downstream database bottleneck.

## 3. Optimize

Avoid:

```text
It is slow → add Redis.
```

Prefer:

```text
Repeated expensive read-only query
        ↓
Introduce caching
        ↓
Measure DB QPS and p99 again
```

## 4. Verify

Measure after the change and compare the same metrics. An optimization is successful only when measurements demonstrate improvement without unacceptable trade-offs.

## Key Principle

> **Measure → Diagnose → Optimize → Verify**

rather than:

> **Guess → Optimize**
