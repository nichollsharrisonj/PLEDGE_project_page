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

#### Architecture

The PLEDGE chatbot will be an API that enables safe chatting with a bot who acts as an authority on gun literacy topics. Its context will be constructed through retrieval of nonpartisan peer-reviewed literature to allow accurate, science-backed responses.

It will be built on top of the the **quibl** library, which enables config-driven development and eval of chatbots for digital intervention purposes. A **quibl** config acts as a single source of truth defining the response behavior, guardrails, and retrieval corpus for a chatbot. A quibl intervention bot can be inserted into any backend/deployment. 

We will make use of several backends/stages to facilitate incremental eval and improvement of the chatbot as well as eventual deployment. 

See the pages below for more info.

[[quibl-bench-safety]]
[[quibl-bench-quality]]
[[quibl-core]]
[[pledge-api]]