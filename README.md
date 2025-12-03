<p align="left">
  <a href="https://github.com/theaiintegrators">
    <img src="https://img.shields.io/badge/Friday-Ecosystem-4B8BF5" />
  </a>
  <img src="https://img.shields.io/badge/status-active-success" />
  <img src="https://img.shields.io/badge/python-3.9%20|%203.10%20|%203.11-blue" />
  <img src="https://img.shields.io/badge/license-MIT-yellow" />
  <img src="https://img.shields.io/badge/docs-in%20progress-lightgrey" />
  <img src="https://img.shields.io/badge/PRs-welcome-brightgreen" />
</p>

# 🧪 friday-evaluation  
_Modular evaluation engine for validating multi-agent outputs_

Friday Evaluation provides a modular layer for **validating agent decisions, scoring outputs, and enforcing safety or correctness rules** within Friday's orchestration engine.

It integrates seamlessly with **Friday Core** and works with:

- LLM-based evaluators  
- Rule-based evaluators  
- DeepEval evaluators  
- Custom enterprise validation logic  

---

## 📦 Installation

Friday Evaluation will be available on PyPI soon.

```bash
pip install friday-evaluation   # coming soon
```
---

![License](https://img.shields.io/badge/License-MIT-blue.svg)
![Status](https://img.shields.io/badge/Status-Under%20Development-orange.svg)
![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)

---

## 🌟 Why Evaluation Matters

Multi-agent systems fail silently without proper evaluation. Common issues include:

- Hallucinated outputs  
- Incorrect next-step routing  
- Invalid intermediate data  
- Violations of business rules  
- No measurable correctness  

Friday Evaluation introduces a consistent and modular validation pipeline that plugs directly into Friday Core.

---

## ✨ Features

- **LLM-based evaluation** (Azure OpenAI / OpenAI)  
- **Rule-based validators** (Python conditions)  
- **DeepEval integration**  
- **Scoring + pass/fail logic**  
- **Thresholds for enterprise safety**  
- **Multi-step workflow compatibility**  
- **Plug-and-play design**  

---

## 🧩 Architecture Overview

Friday Evaluation sits between agent executions:

```
Agent → Evaluation → Router → Next Agent
```

### **LLM Evaluator**
Uses an LLM to score correctness.

### **Rule Evaluator**
Executes Python rules (e.g., "non-empty", "is JSON", etc.)

### **Composite Evaluator**
Chains multiple evaluators.

### **Policies & Thresholds**
Define business acceptance criteria.

---

## 📁 Repository Structure

```
friday-evaluation/
  ├── friday_evaluation/
  │     ├── base.py
  │     ├── llm_evaluator.py
  │     ├── rule_evaluator.py
  │     ├── composite.py
  │     └── types.py
  ├── examples/
  ├── tests/
  └── README.md
```

---

## 🚀 Example: Rule-Based Evaluation

```python
from friday_evaluation import RuleEvaluator

def is_not_empty(output):
    return output is not None and len(str(output)) > 0

evaluator = RuleEvaluator(rules=[is_not_empty])
score = evaluator.evaluate("hello world")
print(score.passed)  # True
```

---

## 🤖 Example: LLM-Based Evaluation

```python
from friday_evaluation import LlmEvaluator

evaluator = LlmEvaluator(
    model="gpt-4o-mini",
    prompt_template="Rate the correctness of the agent output from 1-10: {output}"
)

score = evaluator.evaluate("Generated onboarding workflow...")
print(score.score)  # e.g., 8.3
```

---

## 🔗 Integrating With Friday Core

```python
from friday import Orchestrator
from friday_evaluation import LlmEvaluator

evaluator = LlmEvaluator(model="gpt-4o-mini")

orchestrator = Orchestrator(agents=agents)
orchestrator.with_evaluation(evaluator)

result = orchestrator.run("start")
```

---

## 🧪 Roadmap

- [ ] JSON schema evaluation  
- [ ] Business rule policy DSL  
- [ ] Standard evaluation templates  
- [ ] Multi-turn evaluation metrics  
- [ ] Visual evaluation reports  

---

## 🔭 Vision

Friday Evaluation aims to make multi-agent workflows **measurable**, **trustworthy**, and **production-ready**.

---

## 📄 License
MIT License
