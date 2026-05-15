---
type: project
status: in-progress
started: 2026-05-15
finished:
tags:
  - Linkai
  - project
  - planning
MOCs:
---
# Thesis
> *Existing branching AI chat tools treat conversational context as either fully inherited or fully isolated a binary that wastes tokens or loses information. **Linkai introduces structured, graph-aware context composition.** When a user branches from a highlighted span within a parent response, the child branch receives a hierarchically composed context: the span at full fidelity, the parent at medium fidelity, and progressively older ancestors at decaying fidelity. Beyond a configurable depth threshold, ancestor content is compressed into summaries with retrieval drill-down a two-tier memory system where summaries serve as the default and full text is retrieved on demand when relevance scoring justifies the cost. **The system is evaluated against linear-context and full-inheritance baselines using an LLM-judge framework on a curated multi-turn task set, measuring answer quality per token consumed.***
