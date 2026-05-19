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

## 1. HNSW (Hierarchial Navigable Small World) -> Used in retrieval 

**Its an index type that helps in finding "top k vector that are most simillar to the query vector" in sub-linear time.**
*The Naive Approach* : compare the query against every stored embedding, sort, take top K. That's O(n) per query.
#### The intuition for how HNSW works.
Imagine a graph where each vector is a node, and each node has edges to a handful of its nearest neighbors. To find the closest vector to a query, you start at some entry point, look at its neighbors, jump to whichever neighbor is closer to the query, and repeat until no neighbor is closer than where you are. That's a greedy walk on a nearest-neighbor graph. It works, but in a single flat graph the walk can take a while to converge.

The "hierarchical" part is the trick. HNSW builds multiple layers. The top layer is sparse — only a few nodes, with long-range connections between them. The bottom layer contains every vector with short-range connections. You start your search at the top, take big jumps to land roughly in the right neighborhood, drop down a layer, refine, drop down again, refine, until you're at the bottom layer doing fine-grained local search. Think of zooming in on a map: country level, then city level, then street level. Each layer narrows the search region before the next layer does precision work.

**The trade-offs that matter to you:**

- HNSW is **approximate** — it usually finds the true top-K but occasionally misses. For your use case (relevance scoring for retrieval drill-down), occasional approximation is harmless. You're not running a banking ledger; you're picking which old messages to surface.
- HNSW has **two main tuning knobs**: `m` (how many neighbors each node connects to) and `ef_construction` / `ef_search` (how thoroughly to explore during build and query). Higher values = better recall, more memory, slower builds. pgvector defaults are reasonable. Don't tune until you measure.
- HNSW is **memory-hungry**. The whole index ideally fits in RAM for fast queries. At your scale (low thousands of embeddings, 1536 dimensions each, ~6KB per vector → tens of MB), this is a non-issue. At millions, it becomes one.
- pgvector also offers **IVFFlat** as an alternative index. IVFFlat is faster to build and uses less memory but has worse recall/speed trade-offs at query time. For MVP, HNSW is the right default.



