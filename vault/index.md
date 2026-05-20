---
tags:
  - Project/PLEDGE
  - Type/Landing
aliases:
  - PLEDGE Home
  - Home
---

# PLEDGE Chatbot Development

## Overview

The PLEDGE chatbot will be an API that enables safe, reliable chatting with a bot who acts as an authority on gun literacy topics informed by the PLEDGE initiative's research. Its context will be constructed through retrieval of nonpartisan peer-reviewed literature to allow accurate, science-backed responses.

It will be built on top of the **QUIBL** library (see [[Quibl Core]]), which enables config-driven development and eval of chatbots for digital intervention purposes. A **QUIBL** config acts as a single source of truth defining the response behavior, guardrails, and retrieval corpus for a chatbot. A QUIBL intervention bot can be inserted into any backend or deployment.

In developing the PLEDGE chatbot, there are two distinct dimensions along which we want to optimize its behavior: safety and quality. In this vault, we outline the process to implement and evaluate the chatbot.

We will make use of several backends in different stages to facilitate incremental eval and improvement of the chatbot as well as eventual deployment. The pages below aim to describe each component of the project.

> **See [[reference/Timeline]] for a proposed dev and rollout schedule.**

### QUIBL library

[[Quibl Core]] explains the **QUIBL** (**QU**ick **I**ntervention **B**ot **L**ibrary). Both eval pipelines will rely on the QUIBL library for quick instantiation and tuning of bots.

### Evaluation

There are two independent eval loops:

[[PLEDGE Safety Iteration]] is how we optimize the bot's guardrails for safety

[[PLEDGE Quality Iteration]] is how we optimize the bot's response quality

### Production

[[PLEDGE API]] will cover the FastAPI wrapper around the production PLEDGE intervention profile

### Project Code


[[resources/repos]] lists the git repositories for this program.
