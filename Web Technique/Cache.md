# Cache

Category: Web Storage
First Refrence: What%20is%20cache%204ab613a13449486e89ef0f003840a585.md
Tags: Basic, Concept

## Concept

- A cache is a reserved storage location that collects temporary data to help websites, browsers, and apps load faster.
- It acts like a memory bank, making it easy to access data locally instead of redownloading it every time you visit a website or open an app.

## Storage

### ****Devices and software****

- Caches are found in both software and hardware.
- A CPU cache is a small block of memory that's designed to help the CPU easily retrieve frequently used information.

### ****Web Browsers****

- A browser cache stores files needed by your browser to display the web sites it visits.

### App

- Like browsers, apps save files and data they deem important so they can quickly reload the information as needed.

## Strategies

1. **Pre-caching data**, for small pieces of data, usually during the application initialization, before any request.
2. **On-demand**, checking first if the requested data is in the cache (if the data is found, it is called a *cache hit*), using it.

## HTTP caching

- HTTP caching is a solution for improving the performance of your web application.
- Cache invalidation is process that replaced or removed cache when value is change.
    - **Purge**
        - Removes content from *cache*
         immediately.
    - **Refresh**
        - Fetches requested content from the application, even if cached content is available.
    - **Ban**
        - A reference to the cached content is added to a blacklist

---

# Vocabulary

- temporary: tạm thời
- reserve: dự trữ