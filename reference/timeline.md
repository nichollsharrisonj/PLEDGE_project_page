---
tags:
  - Project/PLEDGE
  - Type/Reference
---

# Timeline

Update this chart as milestones shift. Todos tracking: [[kanban/pledge-roadmap]].

```mermaid
gantt
    title PLEDGE chatbot development/rollout timeline
    dateFormat YYYY-MM-DD
    axisFormat %b %Y
    section Quibl
    Core library           :done, q1, 2026-05-01, 2026-07-31
    section API
    pledge_api_app pilot   :active, a1, 2026-06-01, 2026-09-30
    pledge_default profile :a2, 2026-07-01, 2026-08-15
    section Bench
    quibl_bench scaffold   :b0, 2026-07-01, 2026-08-31
    Quality loop           :b1, 2026-08-01, 2026-10-15
    Safety benchmark       :b2, 2026-09-01, 2026-11-30
    section Team
    Intern onboarding      :t1, 2026-05-16, 2026-06-01
```

## Milestones

| Date | Milestone |
|------|-----------|
| 2026-06-01 | Interns onboarded; first blocks assigned |
| 2026-08-15 | `pledge_default` profile frozen for pilot |
| 2026-10-31 | `quibl_bench` running frozen config evals |
| 2026-11-30 | Safety golden set v1 + report template |

Embedded on [[PLEDGE]] — edit dates here or on individual block notes.
