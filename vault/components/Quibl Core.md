---
tags:
  - Project/PLEDGE
  - Type/Project-Note
  - Area/Quibl
priority: 3
repo: quibl
---

# QUIBL core library

## Goal

The goal of **QUIBL** (**QU**ick **I**ntervention **B**ot **L**ibrary) is to create a human-readable single source of truth defining a complete chatbot. Because we want to comparatively evaluate many strategies for things like guardrails and corpus retrieval, defining each bot in as a `quibl.InterventionBot` instantiated from a config folder allows easy referencing, evaluation, and comparison, as well as observability into the guardrail internals when, for example, a refusal occurs. The library is designed to separate the bot logic from any app code, so we can easily create testing harnesses that swap in many different bot configs and collect informative analytics about how each one performs. 

Within a QUIBL config, the following things are defined:
- System prompt
- Application Model
- Full NeMo guardrails config
	- Individual rails
	- Rail models
	- Rail prompts
- Extract, Transform, Load pipeline
	- Parsing
	- Chunking
	- Metadata
	- Retrieval orchestration logic
- Vector Database (default is ChromaDB)
- Retrieval Strategy

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
