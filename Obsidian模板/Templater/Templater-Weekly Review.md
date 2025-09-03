---
creation date: 2024-09-11
modification date: 
tags:
  - "#WeeklyReview"
type: WeeklyReview
---
# 本周计划
- [ ] 123

---
# 本周日记
```dataview
Table file.cday as "创建日期", file.mday as "最后修改"
From "我的日记"
WHERE file.cday >= date(this.file.cday) AND file.cday <= date(this.file.cday) + dur(1 week)
SORT date ASCENDING
```
# 本周课堂笔记
```dataview
Table file.cday as "创建日期", file.mday as "最后修改"
From "瞬时笔记(fleetting note)" 
WHERE type = "CourseNotes" AND  file.cday >= date(this.file.cday) AND file.cday <= date(this.file.cday) + dur(1 week)
SORT date ASCENDING
```

---
