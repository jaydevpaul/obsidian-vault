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
	-  Pick one or more enabled models (sending one message creates parallel branches)
	- Pick a compression model (for summaries/meta instructions)
	- Pick a title model (for thread titles)
	- Send a message once; if multiple models are selected, you’ll get multiple assistant branches.
	- Use the branch list to switch, or continue from any node.
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
	- Branching happens cause of multiple models still select specific part of the response and branching not present which is our basic need
- ### [treeGPT](https://github.com/jamesmoore24/treegpt)
	1. **Tangential Conversations**
		- Traditional interfaces don't allow for branching conversations
	    - TreeGPT enables chat tangents with easy context control
	2. **Natural Language Search**
	    - Search through chats using natural language descriptions
	    - Uses metadata embeddings and RAG lookup for better search results
	3. **Token Management**
	    - Real-time token usage tracking and cost estimation
	    - Control over output length and context window
	4. **Model Selection**
	    - Intelligent model routing based on heuristics and benchmarks
	    - Support for multiple providers (OpenAI, Anthropic, Gemini, DeepSeek
	###  [Key Features](https://github.com/jamesmoore24/treegpt#key-features)
	5. **Interactive Tree Visualization**
	    - Mini-map showing the conversation tree
	    - Visual "context lineage" highlighting
	    - Node summaries and hover previews
	6. **Vim-like Keybindings**
	    - Toggle between "chatting" and "viewing" modes [`]
	    - Tree navigation with [j] for up, [1-9] for edge selection
	    - Root navigation [r]
	    - Search functionality [/]
	    - Node editing [e]
	    - Node deletion [dd]
	7. **Model Selection Shortcuts**
	    - 1 - Select Llama 3.1 (8B)
		 - Select Llama 3.3 (70B)
	    - 3 - Select Llama 4 Scout (17B)
	    - 4 - Select Qwen 3 (32B)
	    - 5 - Select DeepSeek Chat
	    - 6 - Select DeepSeek Reasoner
	8. **Advanced Architecture**
	    - Tree-based data modeling for efficient search and caching
	    - LiteLLM integration for API and context management
	    - Support for personal API keys or subscription-based usage
	9. **Multi-Model Support**
	    - Connect to various LLM providers using your own API keys
	    - Intelligent model routing between providers
	    - Comparative testing of different models
	- ### Gaps
		- in a chat window each user msg and ai response is a node in canvas if multiple pair of user msg and ai response is present in a chat window it just stacks nodes on top of each other
		- for branching you have to be on the specific node and then press branch button to branch out from the  node so no option of selecting a word or para in ai response and then branch out.
		- No option of project folder setup like claude which have all the chats in a cluster
		- the branching out of next query is also asked in the same chat window only thing it solves is easier to reach any response because of the nodes in canvas but still the chat window clutters everything


I have checked some apps form HN aslo there also same problem the branching out happens out of an entire AI response and no option to select some specific part of the response and dig deep 


## Links 
https://a9.io/glue-comic/page-2
