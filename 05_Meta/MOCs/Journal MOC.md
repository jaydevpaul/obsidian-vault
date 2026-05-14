---
type: moc
created: 2026-05-02
tags:
  - moc
parent_moc:
---

# Journal MOC

> **What this MOC covers:** Index of journal reflections — daily highlights worth remembering, weekly reviews, monthly retrospectives, and yearly themes.


## 🌐 Overview
The journal accumulates as raw daily notes; this MOC surfaces the patterns. Weekly and monthly reviews live here as standalone notes, and standout learnings from daily reflections get promoted into atomic notes elsewhere. This is where I look back, not where I write.



## 📅 Recent Daily Notes
```dataview
LIST file.cday
FROM "02_Areas/Journal"
WHERE type = "daily"
SORT file.cday DESC
LIMIT 7
```

## 📈 Weekly Reviews
<!-- will populate as you start doing weekly reviews -->

## 🗓️ Monthly Reviews
<!-- will populate as you start doing monthly reviews -->

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