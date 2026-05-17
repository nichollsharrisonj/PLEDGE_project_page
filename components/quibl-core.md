---
tags:
  - Project/PLEDGE
  - Type/Project-Note
  - Area/Quibl
priority: 3
repo: quibl
---

# Quibl core library

## Goal

Stable `InterventionBot` API: intervention profile manifest loading, guardrails orchestration, optional Chroma RAG (or external), unstructured data ETL pipeline, agentic behavior?

## Tasks

- [ ] Settle on complete set of retrieval and chunking implementation
  - [x] Muti-query
  - [x] Prompt-rewrite
- [ ] Documentation - where does it go, what does it look like?
- [ ] Create example FastAPI/Flask template repo as a consumer of the quibl library implementing a chatbot endpoint. Should allow easy creation of an equivalent chatbot backend with a different intervention profile.

## Notes

See [[reference/architecture]].

## Links

- [[resources/repos]]
- [[pledge-default-intervention]]
