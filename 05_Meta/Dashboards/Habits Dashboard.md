---
type: dashboard
tags: [dashboard, habits]
---

# 🧱 Habits

[[Home Dashboard|⬅ Back to Home]]

## 📈 Study Hours Heatmap

```dataviewjs
const calendarData = {
  year: 2026,
  colors: {
    blue: ["#1a365d", "#2c5282", "#3182ce", "#4299e1", "#63b3ed"]
  },
  showCurrentDayBorder: true,
  defaultEntryIntensity: 4,
  intensityScaleStart: 0,
  intensityScaleEnd: 8,
  entries: []
}

for (let page of dv.pages('"02_Areas/Journal"').where(p => p.type === "daily" && p.study_hours)) {
  calendarData.entries.push({
    date: page.file.name,
    intensity: page.study_hours,
    content: `${page.study_hours}h`
  })
}

renderHeatmapCalendar(this.container, calendarData)
```

## 🏋️ DSA Problems Solved

```dataviewjs
const calendarData = {
  year: 2026,
  colors: {
    green: ["#1a4d2e", "#2d7a44", "#4caf50", "#81c784", "#c8e6c9"]
  },
  showCurrentDayBorder: true,
  defaultEntryIntensity: 3,
  intensityScaleStart: 0,
  intensityScaleEnd: 5,
  entries: []
}

for (let page of dv.pages('"02_Areas/Journal"').where(p => p.type === "daily" && p.dsa_problems)) {
  calendarData.entries.push({
    date: page.file.name,
    intensity: page.dsa_problems,
    content: `${page.dsa_problems}`
  })
}

renderHeatmapCalendar(this.container, calendarData)
```

## 🚶 Steps

```dataviewjs
const calendarData = {
  year: 2026,
  colors: {
    orange: ["#7c2d12", "#9a3412", "#c2410c", "#ea580c", "#fb923c"]
  },
  showCurrentDayBorder: true,
  defaultEntryIntensity: 5000,
  intensityScaleStart: 0,
  intensityScaleEnd: 12000,
  entries: []
}

for (let page of dv.pages('"02_Areas/Journal"').where(p => p.type === "daily" && p.steps)) {
  calendarData.entries.push({
    date: page.file.name,
    intensity: page.steps,
    content: `${page.steps}`
  })
}

renderHeatmapCalendar(this.container, calendarData)
```

## 📅 Last 7 Days

```dataview
TABLE WITHOUT ID file.link as "Day", study_hours as "Study", dsa_problems as "DSA", steps as "Steps", gym as "Gym", deficit as "Deficit"
FROM "02_Areas/Journal"
WHERE type = "daily"
SORT file.name DESC
LIMIT 7
```

## 🔥 Streaks (Current)

**Days with study (≥1h) this week:** `$= dv.pages('"02_Areas/Journal"').where(p => p.type === "daily" && p.study_hours >= 1 && p.file.cday >= dv.date("today") - dv.duration("7 days")).length`

**Gym sessions this week:** `$= dv.pages('"02_Areas/Journal"').where(p => p.type === "daily" && p.gym === true && p.file.cday >= dv.date("today") - dv.duration("7 days")).length`

**DSA problems this week:** `$= dv.pages('"02_Areas/Journal"').where(p => p.type === "daily" && p.dsa_problems > 0).array().reduce((sum, p) => sum + p.dsa_problems, 0)`