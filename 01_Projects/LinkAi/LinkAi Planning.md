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

# The MVP Scope
## In MVP
- **Linear chat with branching from highlighted spans.** User can select any contiguous text span within an AI response and create a child branch anchored to that span. The anchor must survive page reload. Each branch is a node in a graph; the graph is a DAG with one parent per node.
- **Hierarchical context composition.** When sending a message in a branch, the system constructs context using: the anchor span at full text, the parent message at full text, grandparents and beyond summarized with a configurable decay function. The decay function lives behind an interface so it can be swapped — this matters for evaluation.
- **Two-tier memory beyond the decay threshold.** Ancestors beyond depth N (start with N=3, make it configurable) are stored as summaries plus embeddings of the original text. At context construction time, a retrieval step scores ancestors for relevance to the current query and "drills down" — replaces the summary with the original text — for the top-k hits above a threshold.
- **Pluggable context strategies.** Context construction is an interface with multiple implementations: `FullInheritance`, `ParentOnly`, `HierarchicalDecay`, `HierarchicalDecayWithRetrieval`. The active strategy is selectable per-branch (for the user) and per-eval-run (for you). This is the architectural concession to evaluation.
- **Evaluation framework.** A separate offline harness that runs a curated task set through each context strategy and produces a comparison report. LLM-judge with a documented rubric. Token usage tracking per strategy. Output: a markdown report with tables, ideally checked into the repo so it's visible from the README.
- **Persistence and multi-user auth.** Real database, real users, real sessions. Not "demo deployed for myself." This is non-negotiable for the resume audience you're targeting.
- **Minimal but coherent UI.** Functional, not flashy. The graph view from your original pitch is _out of MVP_. A simple sidebar tree of branches is sufficient. We do not get bogged down in canvas rendering.

## Not in MVP
- Graph/canvas visualization (the Obsidian-style view). v2.
- Sibling context bridging. v2.
- Multi-model branching. v2 if ever.
- Tools/MCP integration. Out of scope, period.
- Mobile UI. Out of scope.
- Real-time collaboration. Out of scope.
- A "compress this chain into a node" user-facing feature. Out of scope — compression is a backend mechanism, not a user feature.
- Anything you see in Prompt-Tree or treeGPT that looks cool. If it's not on the "In MVP" list, it's not in MVP.

# Milestones
- **Weeks 1–2: Architecture.** Phase 2. Tech stack, data model, deployment plan, evaluation harness design. Output: a written design document in your Obsidian vault that you could hand to another engineer. We'll do this together over the next few exchanges.
- **Weeks 3–6: Core backend.** Auth, persistence, basic chat (no branching yet), the conversation graph data model, the context strategy interface with two implementations (`FullInheritance` and `ParentOnly`). At the end of this phase you have a working linear chat. Boring but foundational.
- **Weeks 7–10: Branching and hierarchical context.** Span-anchored branching. The `HierarchicalDecay` strategy. Summarization pipeline for ancestors beyond depth N. End of this phase you have the headline feature working.
- **Weeks 11–14: Retrieval drill-down and evaluation.** Embedding store, retrieval scoring, the `HierarchicalDecayWithRetrieval` strategy. Build the evaluation harness in parallel. Curate the task set (20–30 multi-turn scenarios is plenty for MVP).
- **Weeks 15–18: Run evaluations, iterate, polish.** This is where the project either becomes good or stays mediocre. You run experiments, find that something doesn't work, fix it, re-run. The README gets written. The evaluation report gets generated.
- **Weeks 19–24: Buffer.** Things will slip. They always do. The buffer is real time you should plan to use, not optimism padding.