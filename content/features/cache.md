---
title: Cache
draft: false
weight: 4
---

{{< callout type="info" >}}
  This feature has not been yet implemented.
{{< /callout >}}

Parapluie can cache results to avoid calling the backend infrastructure on every request. 

```mermaid
graph TD
    A[Client Request] -->|New Request| B{Check Cache}
    B -->|Cache Hit| C[Return Cached Data]
    B -->|Cache Miss| D[Fetch Data from Backend]
    D --> E[Return Data to Client]
    D --> F[Update Cache with Data]
``` 

When a client requests data, Parapluie first checks its cache. If the data is present and still valid (i.e., not expired), it returns the cached data immediately. 

This speeds up response times and prevents the backend from being overwhelmed by repeated identical queries, thus optimizing resource utilization and improving overall system performance.

