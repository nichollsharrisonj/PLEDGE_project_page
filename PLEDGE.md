---
tags:
  - Project/PLEDGE
  - Type/Landing
aliases:
  - PLEDGE Home
  - Home
---

# PLEDGE Chatbot Development


## General

In developing the PLEDGE chatbot, there are two distinct dimensions along which we want to optimize its behavior: safety and quality. In this vault, we outline the process to implement and evaluate the chatbot.


## Components

```dataview
TABLE 
FROM "components"
WHERE contains(file.tags, "Project/PLEDGE")
SORT priority DESC
```

## Open tasks (project-wide)


```dataview
TASK
FROM "components"
WHERE !completed
SORT file.name
```


## Reference

- [[reference/architecture]] 
- [[reference/eval-testing]] 
- [[kanban/pledge-roadmap]] 
