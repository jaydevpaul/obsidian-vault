---
type: moc
created: 2026-05-02
tags:
  - moc
parent_moc:
---

# Projects MOC

> **What this MOC covers:** Index of all my coding projects — active, paused, completed, and abandoned. The narrative arc of what I've built.


## 🌐 Overview
This MOC is the project portfolio in one view. Active projects surface on the Home Dashboard via Dataview; this MOC adds curation, retrospectives, and lessons learned across projects.



## 🚀 Active Projects
```dataview
TABLE status, deadline, file.mtime as "Last Touched"
FROM "01_Projects"
WHERE type = "project" AND status = "active"
SORT file.mtime DESC
```

## ⏸️ Paused Projects
```dataview
TABLE status, file.mtime as "Last Touched"
FROM "01_Projects"
WHERE type = "project" AND status = "paused"
SORT file.mtime DESC
```

## ✅ Completed Projects
```dataview
TABLE status, file.mtime as "Completed"
FROM "04_Archive/Projects"
WHERE type = "project"
SORT file.mtime DESC
```

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