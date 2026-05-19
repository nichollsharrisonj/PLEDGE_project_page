---
tags:
  - Project/PLEDGE
  - Type/Reference
---
```mermaid
gantt
    title PLEDGE chatbot program
    dateFormat YYYY-MM-DD
    axisFormat %b %Y
    todayMarker on

    section Milestone
    First Usable PLEDGE Chatbot Live           :milestone, v0, 2026-09-15, 0d

    section Evaluation loops
    Quality improvement cycle             :loopq, 2026-10-15, 2027-03-31
    Safety improvement cycle              :loops, 2026-11-01, 2027-03-31
```


## Open tasks (project-wide)


```dataview
TASK
FROM "components"
WHERE !completed
SORT file.name
```