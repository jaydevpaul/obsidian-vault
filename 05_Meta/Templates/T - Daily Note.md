---
date: <% tp.date.now("YYYY-MM-DD") %>
type: daily
tags: [daily]
study_hours: 0
steps: 0
calories: 
gym: false
deficit: false
dsa_problems: 0
---

# <% tp.date.now("dddd, MMMM Do YYYY") %>

[[<% tp.date.now("YYYY-MM-DD", -1) %>|⬅ Yesterday]] | [[<% tp.date.now("YYYY-MM-DD", 1) %>|Tomorrow ➡]]

## 🎯 Today's Targets
- [ ] 
- [ ] 
- [ ] 

## 🧱 Habits
- [ ] Gym
- [ ] Calorie deficit hit
- [ ] 8k+ steps
- [ ] Study (≥ 2h)
- [ ] DSA problem(s)



## 📝 Log
<!-- timestamped scratchpad throughout the day -->

## 🔗 Notes Created Today
```dataview
LIST FROM "" WHERE file.cday = date("<% tp.date.now("YYYY-MM-DD") %>") AND file.name != this.file.name
SORT file.ctime ASC
```

## 🌙 End-of-Day Reflection
**What went well:**

**What didn't:**

**What I learned:**

**Tomorrow's #1 priority:**