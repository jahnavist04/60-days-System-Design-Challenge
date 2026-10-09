# Content Delivery Network (CDN) 🌍

## What is a CDN?

A **Content Delivery Network (CDN)** is a distributed network of servers that delivers content to users from a location closer to them.

Instead of every user requesting content from one central server, a CDN can serve cached content from nearby servers.

    Origin Server
          |
    ┌─────┼─────┐
    ↓     ↓     ↓
   CDN   CDN   CDN
  Edge  Edge  Edge
 Server Server Server
    ↑     ↑     ↑
  Users Users Users

---

## Why is a CDN Needed?

Imagine a website whose main server is located in the USA.

A user in India requests an image.

### Without a CDN

    User in India
          |
          | Long Distance
          ↓
      Server in USA
          |
          ↓
        Image

The request has to travel a long distance.

This can increase latency.

### With a CDN

    User in India
          |
          ↓
    CDN Server in India
          |
          ↓
        Image

The content can be delivered faster.

---

## What Does a CDN Store?

A CDN commonly stores static content such as:

- Images
- Videos
- CSS files
- JavaScript files
- HTML pages
- Fonts
- Other static assets

For example:

    website.com/logo.png
    website.com/style.css
    website.com/app.js

These files can be cached by CDN edge servers.

---

## How Does a CDN Work?

Suppose a user requests an image.

    User
      |
      ↓
     CDN
      |
      ├── Cache Hit → Return Image
      |
      └── Cache Miss
              |
              ↓
         Origin Server
              |
              ↓
         Store in CDN
              |
              ↓
          Return Image

---

## Cache Hit

A **cache hit** occurs when the requested content already exists on the CDN server.

    User
      |
      ↓
     CDN
      |
      ↓
    Content Found
      |
      ↓
    Return Content

The origin server does not need to be contacted.

---

## Cache Miss

A **cache miss** occurs when the requested content is not available in the CDN cache.

    User
      |
      ↓
     CDN
      |
      ↓
    Content Not Found
      |
      ↓
    Origin Server
      |
      ↓
    CDN stores content
      |
      ↓
      User

The next request can then be served from the CDN.

---

## Edge Servers

CDNs use servers called **edge servers**.

These servers are distributed across different geographical locations.

             Origin Server
                  |
       ┌──────────┼──────────┐
       ↓          ↓          ↓
     India       USA       Europe
      Edge       Edge        Edge
       ↓          ↓          ↓
     Users      Users      Users

Users can receive content from a nearby edge server.

---

## Benefits of CDN

### 1. Lower Latency ⚡

Content can be delivered from a geographically closer server.

### 2. Reduced Server Load

The origin server receives fewer requests.

### 3. Better Scalability 📈

CDNs can handle large numbers of users requesting static content.

### 4. Better Availability

If one edge server has problems, requests may be served from another location.

---

## CDN and Caching

A CDN is closely related to caching.

The CDN stores frequently requested content closer to users.

    Origin Server
          |
          ↓
      CDN Cache
          |
          ↓
        Users

This reduces the need to repeatedly access the origin server.

---

## Real-World Example

Consider a video streaming application.

Millions of users may request the same popular video.

### Without CDN

    Millions of Users
           |
           ↓
      Origin Server

The origin server may become overloaded.

### With CDN

                  Origin
                    |
        ┌───────────┼───────────┐
        ↓           ↓           ↓
      CDN 1       CDN 2       CDN 3
        ↑           ↑           ↑
      Users       Users       Users

Popular content can be served from CDN edge servers.

---

## Key Takeaways

- CDN stands for **Content Delivery Network**.
- A CDN distributes content through servers located in different regions.
- CDN edge servers store cached content.
- Cache hits allow content to be delivered quickly.
- Cache misses fetch content from the origin server.
- CDNs reduce latency and origin server load.
- CDNs are especially useful for static and frequently accessed content.

## What I Learned Today

Today I learned how CDNs bring content closer to users by using distributed edge servers.

This reduces latency, decreases load on the origin server, and helps applications serve large numbers of users.
