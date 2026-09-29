# Caching ⚡

## What is Caching?

Caching is a technique used to store frequently accessed data temporarily so that it can be retrieved faster.

Instead of fetching data from the database every time, the application first checks the cache.

If the data is available in the cache, it can be returned quickly.

```text
User
  |
  v
Application
  |
  v
Cache
  |
  +---- Data Found ----> Return Data
  |
  +---- Data Not Found
              |
              v
           Database
              |
              v
        Store in Cache
              |
              v
          Return Data
