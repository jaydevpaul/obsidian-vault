---
type: dashboard
tags: [dashboard]
---
	
# 🏠 Home

> *"You don't rise to the level of your goals; you fall to the level of your systems."*

## Task List

- [ ] NodeJs architecture


## 📅 Today
- [[Habits Dashboard]]
- [[FAANG Prep MOC]]

## 🚀 Active Projects
```dataview
TABLE status, deadline, file.mtime as "Last Touched"
FROM "01_Projects"
WHERE type = "project" AND status = "active"
SORT file.mtime DESC
```

## 🗺️ Top-Level MOCs
- [[DL MOC]]
- [[DSA MOC]]
- [[System Design MOC]]
- [[Python MOC]]
- [[Projects MOC]]
- [[FAANG Prep MOC]]
- [[Journal MOC]]

## 📥 Inbox (clear me)
```dataview
LIST FROM "00_Inbox"
SORT file.ctime DESC
```

## 🔥 Recently Edited
```dataview
LIST file.mtime
FROM "" 
WHERE !contains(file.path, "Templates") AND !contains(file.path, "Journal/") AND !contains(file.path, "Dashboards/")
SORT file.mtime DESC
LIMIT 10
```

## 📊 This Week's Stats
- Notes created (last 7 days): `$= dv.pages('"03_Resources" or "01_Projects"').where(p => p.file.cday >= dv.date("today") - dv.duration("7 days")).length`
- Daily notes completed (last 7 days): `$= dv.pages('"02_Areas/Journal"').where(p => p.file.cday >= dv.date("today") - dv.duration("7 days")).length`

## 🛤️ Roadmaps
- [[ML Roadmap]]
- [[Backend Roadmap]]
- [[FAANG Prep Roadmap]]