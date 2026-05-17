---
tags:
  - Project/PLEDGE
  - Type/Project-Note
  - Area/Bench
priority: 3
repo: quibl_bench
---
# Bot Response Safety Evaluation Loop
## Goal
The goal of the safety evaluation loop is to standardize our process for iterating on the safety (guardrail performance) of the chatbot.

We will curate and use a balanced dataset of query and response pairs with balanced violation categories and attack styles to optimize the guardrails to refuse when appropriate. 

To score metrics will be derived from dataset benchmark performance (over-refusal / under-refusal rates):

* **Over-refusal**
	$$FPR = FP / (FP + TN)$$
* **Under-refusal**
	$$TPR = FN / (TP + FN)$$
* **F-beta** - We want $\beta >> 1$ to favor recall over precision for safety.
	$$F_\beta = \frac{(1 + \beta^2) \times TP}{(1 + \beta^2) \times TP + FP + \beta^2 \times FN}$$


## Benchmark
N (query, response) refuse/accept pairs that should be balanced across the joint distribution of:

* Violation category: topic that could yield unsafe content
* Attack style: phrasing / jailbreak type

Note: balance must be enforced
	
## Readings

* [MART - Multi-Round Automatic Red-Teaming](https://arxiv.org/pdf/2311.07689)

## Red teaming
In order to actually determine the benchmarking dataset, we will use exploratory read-teaming to find failure modes to test in the defninitive benchmark: jailbreaks, edge cases, multi-turn adversarial behavior, universal suffix attack, etc.
We will need some kind of testing harness for this as well, allowing red-teamers to report their findings. TBD

## Individual Guardrail Finetuning (future)
For certain very sensitive topics, we might find that LLM-as-judge with base OpenAI LLMs are not sufficient. In this case, it will make sense to fine-tune a model on a specific refusal category and add this as its own guardrail (In any case, fine-tuning would likely save on inference cost for guardrails at scale, so may ultimately be worthwhile)
To achieve this, we will gather a set of potentially human created, or AI-created and human-validated Q/R pairs
As this is out of scope of a quibl config, it would require an extension of chatbot versioning to include finetuning checkpoint as well as quibl config (e.g. quibl_\<checkpoints>\_<config_ver>)

---
## Tasks
 - [ ] Produce Jupyter Notebook which instantiates quibl intervention bots and runs benchmark analysis
 - [ ] Refine benchmark dataset through red-teaming
