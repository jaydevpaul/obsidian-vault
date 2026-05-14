---
type: moc
created: <% tp.date.now("YYYY-MM-DD") %>
tags: [moc]
parent_moc: 
---

# <% tp.file.title %>

> **What this MOC covers:** 

## 🌐 Overview
<!-- 2-4 sentences: what this domain is, why I care, current depth of understanding -->


## 🧱 Core Concepts
<!-- the foundational atomic notes — handpicked, ordered pedagogically -->
- 

## 🔬 Sub-Topics
<!-- when this section grows past ~15 items, promote a sub-topic to its own MOC -->


## 📚 Resources
### Papers, Videos & Articles
```dataview
LIST FROM "03_Resources" 
WHERE contains(MOCs, this.file.link) AND type = "literature"
SORT file.ctime DESC
```

### Books
- 

## 🛤️ Related Roadmaps
- 

## ❓ Open Questions
<!-- things I don't yet understand; convert to atomic notes once resolved -->
- 

## 🔗 Related MOCs
- 

## 🗂️ All Notes in This MOC
```dataview
LIST FROM "" 
WHERE contains(MOCs, this.file.link) AND file.name != this.file.name
SORT file.mtime DESC
```