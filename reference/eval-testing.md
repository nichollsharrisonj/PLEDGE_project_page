---
tags:
  - Project/PLEDGE
  - Type/Reference
---

# Eval and Testing for the PLEDGE chatbot

Our process will treat each **quibl** instance (manifest + rails + corpus + retrieval strategy) as a versioned system evaluated in a loop. The optimization is over two distinct categories: safety and quality. These will be evaluated independently, as safety depends on a bot's NeMo guardrails config, while quality depends on the RAG/Agent configuration. 

The goal is to standardize as much of each evaluation loop as possible (and automate in some cases). Quality eval will be conducted with human feedback on pairwise comparisons (ablation of guardrails) and resulting ELO, while safety eval will be conducted through red-teaming and benchmarking.
## Quality

See [[quibl-bench-quality]]

## Safety

See [[quibl-bench-safety]]