---
title: Caching Fundamentals
tags: [caching, redis, performance, system-design]
---

# Caching Fundamentals

Caching stores frequently accessed data in a faster storage layer to reduce latency and backend load.

```text
Client
   ↓
Application
   ↓
Cache
   ├── HIT  → Return Data
   └── MISS → Database → Update Cache → Return Data
```

## Cache Hit

A **cache hit** occurs when requested data already exists in the cache.

## Cache Miss

A **cache miss** occurs when requested data is unavailable in the cache. The application retrieves it from the source of truth and may cache the result.

## TTL

**TTL (Time To Live)** determines how long a cache entry remains valid. After expiration, a later request normally becomes a cache miss.

## Eviction Policies

- **LRU** — evicts least recently used entries.
- **LFU** — evicts least frequently used entries.
- **FIFO** — evicts older entries first.

TTL and eviction solve different problems:

```text
TTL      → How long should data remain valid?
Eviction → What should be removed when capacity is limited?
```

## Cache Avalanche

A cache avalanche can occur when many cached entries expire around the same time, producing a burst of database traffic.

### Mitigation: TTL Jitter

```java
ttl = BASE_TTL + randomJitter();
```

Randomizing expiration slightly spreads cache misses over time.

## Cache Penetration

Cache penetration occurs when clients repeatedly request data that does not exist. Every request misses the cache and reaches the database.

### Mitigation: Negative Caching

Cache the "not found" result for a short period:

```text
user:999999999
value = NOT_FOUND
TTL = 1 minute
```

Bloom filters can also help in some high-volume workloads.

## Related Concepts

- Cache Aside
- Write Through
- Write Behind
- Cache Stampede
- Distributed Cache
- Redis
