---
tags:
  - Project/PLEDGE
  - Type/Reference
---

# Timeline

This page offers a proposed dev/rollout scheduled for PLEDGE v1 and after. The bars in the gantt chart are guidelines, but it's hard to give a strict prediction about various parts of the process. See [[Eval and Testing General]], [[PLEDGE Safety Iteration]], and [[PLEDGE Quality Iteration]] for details.

## v1 release target

I set **2026-09-15** as the hopeful target for release of a first usable pilot: a live hosted [[PLEDGE API]] backed by a **v1** QUIBL config implementing primitive retrieval on a fixed reference corpus, with basic chunking/RAG and guardrails that have passed the safety loop. 

Response quality for v1 is whatever the leading config earns in pairwise eval before freeze, but will naturally be constrained by the above. v2 and later (larger corpus, richer retrieval, tool access) will be under ongoing development after the v1 release, always passing through the same quality and safety eval loops (pending changes we decide on based on what we learn from v1 rollout)

```mermaid
gantt
    title PLEDGE Development and Testing Timeline
    dateFormat YYYY-MM-DD
    axisFormat %b %Y
    tickInterval 1month
    todayMarker on

    section Release Milestone
    PLEDGE v1 pilot live! :milestone, v1, 2026-09-15, 0d

    section QUIBL
    QUIBL v1.0 library and RAG :lib, 2026-05-20, 2026-07-25
    QUIBL v1.0 publish, packaging, and docs :pypi, 2026-07-15, 2026-08-05

    section Safety
    Safety eval harness :sh, 2026-06-10, 2026-07-15
    Guardrail tuning cycles optimizing F-beta :stune, 2026-07-15, 2026-09-05
    Blinded safety eval for v1 (if we fail, more tuning) :sblind, 2026-09-01, 2026-09-12

    section Quality
    Quality eval harness :qh, 2026-06-25, 2026-07-25
    Head-to-head quality eval cycles :qc, 2026-07-25, 2026-09-10

    section Analytics
    Analytics backend :ainst, 2026-06-10, 2026-08-10
    
    section Production
    Build prod/nonprod PLEDGE API :app, 2026-08-15, 2026-09-01
    Hosting and CI/CD :host, 2026-08-20, 2026-09-10
    Integrate on PLEDGE site? :integrate 2026-08-20, 2026-09-10

    section Post-v1
    v2+ QUIBL research-capable bot :v2, 2026-09-15, 2026-12-15
    Ongoing safety and quality loops :oloop, 2026-09-15, 2026-12-15
```

### Notes:

Within 'Guardrail tuning cycles' there is a lot going on. Would be good to get to this point ASAP.