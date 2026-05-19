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

### RAG Materials/Strategy
- [GraphRAG](https://colab.research.google.com/github/Unstructured-IO/notebooks/blob/main/notebooks/GraphRAG_for_Academic_Papers.ipynb)
- [unstructured.io](https://docs.unstructured.io/welcome)
- [unstructred.io best practices](https://unstructured.io/blog/chunking-for-rag-best-practices)
- [LlamaIndex](https://www.llamaindex.ai/)
- [Docling](https://www.docling.ai/)
- [OR-bench - overrefusal benchmark](https://arxiv.org/html/2405.20947v5#bib.bib25)
- [ELO Uncovered](https://neurips.cc/virtual/2024/poster/95297)
## Tasks

- [ ] Settle on complete set of retrieval and chunking implementation
  - [x] Muti-query
  - [x] Prompt-rewrite
- [ ] quibl library documentation - where to publish?
- [ ] Create example FastAPI/Flask template repo as a consumer of the quibl library implementing a chatbot endpoint. Should allow easy creation of an equivalent chatbot backend with a different intervention profile.

## Notes

See [[reference/architecture]].

## Links

- [[resources/repos]]
- [[pledge-default-intervention]]
