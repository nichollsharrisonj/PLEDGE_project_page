---
tags:
  - Project/PLEDGE
  - Type/Project-Note
  - Area/Bench
priority: 3
repo: quibl_bench
---

## Goal
The goal of the safety evaluation loop is to standardize our process for iterating on the safety (guardrail performance) of the chatbot.

We will curate and use a balanced dataset of query and response pairs with a diversity of violation categories and attack styles to optimize the guardrails to refuse when appropriate. 

To score metrics will be derived from dataset benchmark performance (over-refusal / under-refusal rates):

* **Over-refusal**

	$$FPR = FP / (FP + TN)$$
* **Under-refusal**

	$$TPR = FN / (TP + FN)$$
* **F-beta** - We want $\beta >> 1$ to favor recall over precision for safety.

	$$F_\beta = \frac{(1 + \beta^2) \times TP}{(1 + \beta^2) \times TP + FP + \beta^2 \times FN}$$


## Benchmark
N -TBD- (query, response) refuse/accept pairs that should be balanced across a joint distribution of:

* Violation category: topic that could yield unsafe content
* Attack style: phrasing / jailbreak type

Balance must be enforced for statistical validity.

See [OWASP LLM top 10](https://genai.owasp.org/llm-top-10/) for some examples of known real-world threats to LLMS.



## Readings

* [MART - Multi-Round Automatic Red-Teaming](https://arxiv.org/pdf/2311.07689)
* [Llama 2 - Safety/red teaming sections](https://arxiv.org/pdf/2307.09288)

## Constructing the Benchmark

### Red teaming phase

In order to actually determine the benchmarking dataset, we will use exploratory red-teaming to find failure modes to test in the benchmark sets (jailbreaks, edge cases, multi-turn adversarial behavior, hypothetical framing, universal suffix attack, multi-topic queries, and so on). 

We might want a testing harness allowing red-teamers to report their findings in a convenient and systematic way while chatting with the bot (TBD). 

The goal of red-teaming is to map out the vulnerabilities of the chatbot before constructing the benchmark dataset. At the red-teaming stage, everyone has equal visibility, and no one is blinded. After the exploratory phase concludes, findings are compiled into an attack taxonomy. This will be a structured table of violation categories/attack styles and their confirmed success rates. This taxonomy is shared with all contributors and serves as the basis for dataset construction.
### Dataset construction

After the exploratory phase concludes, findings will be compiled into an attack taxonomy describing violation category, attack style, and success rates. The taxonomy is shared with all contributors. Then, contributors are split into two groups:

- **Group A** draws from the taxonomy to construct the public tuning corpus. This corpus is used directly to inform quibl config iterations and is visible to the config author throughout the tuning process (update quibl configs, evaluate against public red-team corpus benchmarks, try to maximize F-beta)
- **Group B** draws from the same taxonomy independently to construct the blinded eval set. Group B writes their own distinct instances of the confirmed attack types without coordinating with Group A. Whoever is tuning the quibl config does not see the eval set, just the bot's score on the eval when a formal eval is run.


The blinding operates at the level of specific query instances, but attack types are considered public knowledge. This prevents direct overfitting to known phrasing (or, for example, specific suffixes) while ensuring the eval set testing confirmed effective attack patterns.

A regression set is accumulated over time. Cases that the latest validated config handles correctly are promoted to this set to guard against regressions in later iteration cycles.


Process diagram:
![[Pasted image 20260518211229.png]]


### Guardrail Tuning Loop Structure

The guardrail optimization loop will run in two phases:

1. **Exploratory**: Config iterations run against the visible red-team corpus and regression set only. The goal is to explore a variety of guardrail styles (different models, different LLM-as-Judge prompts, different context passed to guardrails, finetuning of guardrail models, and so on) and map which parameters move F-beta significantly.
2. **Refinement**: After the exploratory tuning, take the guardrail pattern with the highest F-beta on the tuning set, and refine it further with more fine-grainwd adjustments.

After these phase, a single formal evaluation is run against the blinded eval set. If the config fails to meet a target  $F_{\beta}$ threshold (TBD), we return to the exploratory red-teaming phase and start over. The config author does not review which individual eval cases failed before deciding on the next config iteration.

## Individual Guardrail Finetuning 
For certain very sensitive topics, we might find that LLM-as-judge with base OpenAI LLMs are not sufficient. In this case, it will make sense to fine-tune a model on a specific refusal category and add this as its own guardrail (In any case, fine-tuning would likely save on inference cost for guardrails at scale, so may ultimately be worthwhile)
To achieve this, we will gather a set of potentially human created, or AI-created and human-validated Q/R pairs
As this is out of scope of a quibl config, it would require an extension of chatbot versioning to include finetuning checkpoint as well as quibl config (e.g. quibl_\<checkpoints>\_<config_ver>)

One very basic approach to fine tuning is "Safety Context Distillation" (see llama paper)


---
## Tasks
- [ ] Red-teaming result reporting solution
- [ ] Produce Jupyter Notebook which instantiates quibl intervention bots and runs eval benchmark analysis, computing key refusal statistics
- [ ] Refine benchmark dataset through red-teaming
