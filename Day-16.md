# Caching ⚡

## What is Caching?

Caching is a technique used to store frequently accessed data in a temporary storage location so that future requests can retrieve it faster.

Instead of fetching the same data from a database every time, an application can retrieve it from a cache.

## Why is Caching Needed?

Imagine an e-commerce website where thousands of users repeatedly view the same product.

Without caching, every request may access the database, increasing its workload and response time.

With caching, frequently requested product details can be served directly from memory.

## How Does Caching Work?

```text
        Client Request
              |
              v
           Application
              |
              v
          Check Cache
           /      \
        Hit        Miss
         |           |
         v           v
    Return Data   Query Database
                      |
                      v
                 Store in Cache
                      |
                      v
                  Return Data
```

1. The application checks whether the requested data exists in the cache.
2. If the data exists, it returns the cached result. This is called a **cache hit**.
3. If the data does not exist, it fetches the data from the database. This is called a **cache miss**.
4. The application may store the retrieved data in the cache for future requests.

## Types of Caching

### 1. Browser Cache

Stores resources such as images, CSS files, and JavaScript files in the user's browser.

**Example:** A website's logo does not need to be downloaded again on every visit if a valid cached copy is available.

### 2. Application Cache

Stores frequently used application data in memory or a dedicated caching system.

**Example:** Caching product information to reduce repeated database queries.

### 3. Database Cache

Stores frequently accessed query results or data pages to reduce the work required to serve repeated requests.

### 4. CDN Cache

A Content Delivery Network (CDN) caches content at geographically distributed edge locations.

**Example:** Images and videos can be served from an edge location closer to the user.

## Common Caching Strategies

### 1. Cache-Aside

- The application checks the cache first.
- If the data is missing, it reads from the database.
- The application stores the retrieved data in the cache.

This strategy gives the application control over what gets cached.

### 2. Write-Through

- Data is written to the cache and the underlying data store as part of the write operation.
- This helps keep the cache updated, although the exact consistency depends on the implementation.

### 3. Write-Back

- Data is written to the cache first.
- Changes are written to the underlying data store later.
- This can improve write performance but introduces a risk of losing unflushed changes.

### 4. Read-Through

- The application requests data through the cache.
- On a cache miss, the cache loads the data from the underlying data store.

## Cache Eviction Policies

When a cache becomes full, it may need to remove existing entries.

### LRU (Least Recently Used)

Removes the item that has not been accessed for the longest time.

### LFU (Least Frequently Used)

Removes the item with the lowest access frequency.

### FIFO (First In, First Out)

Removes the item that entered the cache earliest.

## Cache Expiration (TTL)

TTL stands for **Time To Live**.

It defines how long a cached item can remain valid before it expires.

For example, product recommendations might be cached for a few minutes, while rarely changing reference data could be cached longer.

Choosing an appropriate TTL helps balance performance and freshness.

## Cache Hit Ratio

The cache hit ratio measures the proportion of cache requests served successfully from the cache.

**Formula:**

Cache Hit Ratio = Cache Hits / Total Cache Requests × 100

For example, if 80 out of 100 requests are served from the cache, the hit ratio is 80%.

A higher hit ratio often indicates effective caching, although the ideal value depends on the workload.

## Popular Caching Technologies

- **Redis:** An in-memory data store commonly used for caching.
- **Memcached:** A distributed in-memory caching system.
- **Amazon CloudFront:** A CDN that caches content at edge locations.
- **Browser Cache:** Stores web resources on the client side.

## Advantages of Caching

- Reduces response time.
- Decreases database workload.
- Improves application performance.
- Helps applications handle more requests.
- Can reduce infrastructure costs.

## Challenges of Caching

- Stale data may be returned.
- Cache invalidation can be difficult.
- Cached data consumes memory.
- Cache misses can increase database traffic.
- A heavily used cache may become a bottleneck.

## Real-World Example

Consider a shopping application where users repeatedly view the same product page.

Instead of querying the database for every request, the application caches product details in Redis.

Subsequent requests can retrieve the cached information quickly, reducing database load and improving response times.

## Key Takeaways

- Caching stores frequently accessed data for faster retrieval.
- Cache hits serve data from the cache; cache misses require another data source.
- Cache-aside and read-through are common caching strategies.
- LRU, LFU, and FIFO are common eviction policies.
- TTL controls how long cached entries remain valid.
- Cache invalidation and data freshness are important design challenges.
