---
title: "Index and Snapshot Isolation"
date: 2023-08-28T16:19:06-05:00
draft: false
---
## Index and Snapshot Isolation

How do indexes work in a multi-version database? One option is to have the index simply point to all version of an object and require and index query to filter out any object versions that are not visible to the current transaction. When garbage collection removes old object versions that are no longer visible to any transaction, the corresponding index entries can also be removed.

In practice, many implementations details determine the performance of multi-version concurrency control. For example, PostgresSQL has optimizations for avoiding index updates if different versions of the same object can fit on the same page.
