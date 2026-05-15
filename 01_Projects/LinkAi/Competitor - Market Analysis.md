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
# Overview
![[Pasted image 20260515113326.png|333]]
## Competitor List
- ### [gitchat](https://github.com/DrustZ/GitChat)
	- it has a canvas like background something like Miro and when you ask a question it creates a node( box like structure with your prompt) and then another node with the AI response.
	- the ai response is connected to user input node using a arrow.
	- Can branch out multiple input and response with option to connect any input to any outputs something like graph like structure.
	- Option to edit user input
	- can delete multiple nodes by selecting using mouse
	- ### Gaps
	- i think this is a mostly UI project
	- doesnot provide the usual chat like interface that chatgpt claude gemini follows
	- no option of selecting a part of AI response and ask related question about it which creates a side chat.
	- no option of clicking on the selected part leading to the related questions chat
	- no context management process
	- too big of a convo with ai clutters the canvas makes it look complex
- ### [Prompt-Tree](https://github.com/yxp934/Prompt-Tree)
	- Very close to what i am planning
	- it also models each chat as a node based DAG
	- Allows unified system prompt, selecting models, tools use like web search, token usage data, modify/ arrange nodes.
	- option for compressed context
	- Claude project like setup
	- #### [ Key Features accordint to them](https://github.com/yxp934/Prompt-Tree#key-features)
		-  **Conversation DAG (tree + branches)**: continue from any node and compare outcomes.
		- **Canvas + chat in one place**: visualize the thread while you talk.
		- **Context Box**: drag nodes into a curated context, reorder, preview, and track tokens.
		- **Long-term memory (3-layer)**:
		    - **User Profile (JSON → derived Markdown)**: persistent preferences/identity, fully visible & editable in Settings.
		    - **Memory Bank (items)**: atomic memories with tags, status, confidence, and sources; supports user/folder scope.
		    - **Folder Doc (JSON → derived Markdown)**: per-folder long-term doc, visible & editable in the folder page.
		    - **First-message base injection + per-message memory refresh**: on a thread’s first user message, inject Profile/Folder Doc + initial `topK(folder) + topK(user)` memories; on every user message, refresh auto memory hits in the Context Box.
		    - **Recent messages continuity (optional)**: on a thread’s first user message, copy the last N messages from your most recent thread (same folder) into the Context Box.
		    - **Async memory writer**: runs on every user message; reads system prompt + all USER messages + a live memory snapshot resolved at execution time; can patch Profile/Folder Doc and upsert memories (first message can be forced to write at least 1 memory).
		    - **`search_memory` tool + pin**: the model can search the full memory library during the tool loop; retrieved memories are added into the Context Box and can be pinned; per-thread caps are enforced (pinned wins over auto).
		    - **Embeddings (optional)**: embedding model is configurable; lexical fallback is used when embeddings are disabled/unavailable.
		- **Multi-model branching**: select multiple models and send once to get parallel branches.
		- **Compression**: compress a selected chain (or the Context Box) into a compact node; decompress when needed.
		- **Tools (optional)**: Web Search (Tavily/Exa), MCP servers, local Python execution.
		- **Local-first storage**: conversations in IndexedDB; settings (providers/tools) in localStorage.

	- ### Gaps
	- 