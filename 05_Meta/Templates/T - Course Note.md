---
type: course
status: in-progress
provider: 
instructor: 
url: 
started: <% tp.date.now("YYYY-MM-DD") %>
finished: 
tags: [course, literature]
MOCs: 
---

# <% tp.file.title %>

**Provider:** 
**Instructor:** 
**URL:** 

## 🎯 What I'm Hoping to Learn


## 🗂️ Lecture Notes
```dataview
TABLE status, date_consumed as "Watched"
FROM "03_Resources/Literature/Courses"
WHERE type = "literature" AND contains(file.path, this.file.name)
SORT file.name ASC
```

## 🧠 Big Takeaways (filled in as I progress)


## 🌱 Atomic Notes Spawned
- 

## 🔗 Linked MOCs
-