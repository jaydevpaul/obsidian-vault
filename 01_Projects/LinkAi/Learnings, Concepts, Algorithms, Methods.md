---
type: project
status: in-progress
started: 2026-05-19
finished:
tags:
  - generic
MOCs:
---
# Overview
Documenting new concepts, methods etc that i learn while building this project.

## 1. HNSW (Hierarchial Navigable Small World)

**Its an index type that helps in finding "top k vector that are most simillar to the query vector" in sub-linear time.**
*The Naive Approach* : compare the query against every stored embedding, sort, take top K. That's O(n) per query.
#### The intuition for how HNSW works.
Imagine a graph where each vector is a node, and each node has edges to a handful of its nearest neighbors. To find the closest vector to a query, you start at some entry point, look at its neighbors, jump to whichever neighbor is closer to the query, and repeat until no neighbor is closer than where you are. That's a greedy walk on a nearest-neighbor graph. It works, but in a single flat graph the walk can take a while to converge.



