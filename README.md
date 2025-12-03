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
_Modular evaluation engine for validating and scoring multi-agent AI workflows_

Friday Evaluation provides the validation layer for Friday’s orchestration runtime.  
It is designed to support **enterprise-grade evaluation** inspired by systems like:

- **LangSmith scoring pipelines**  
- **DeepEval-style structured evaluation**  
- **OpenAI A2A safety & compliance flows**  
- **Microsoft Agent Framework evaluation patterns**  
- **Model Context Protocol (MCP)-aligned validation interfaces**  

It allows AI workflows to enforce correctness, safety, consistency, and policy adherence.

---

# 🌟 Why Evaluation Matters

Multi-agent systems cannot be trusted without proper evaluation.

Friday Evaluation provides:

- guardrails against hallucination  
- correctness scoring  
- business rule validation  
- structured output enforcement  
- acceptance thresholds  
- audit trails for enterprise governance  

It ensures agent workflows behave **predictably**, **safely**, and **repeatably**.

---

# ✨ Features

- **LLM-based evaluators**  
- **Rule-based Python evaluators**  
- **Composite evaluators (chain/parallel)**  
- **Scoring + pass/fail logic**  
- **Threshold enforcement**  
- **DeepEval compatibility**  
- **Extensible evaluation hooks for enterprises**  

---

# 🏛 Architecture Overview

Friday Evaluation sits between agent executions:

```
Agent Output → Evaluation → Router → Next Agent
```

### **LLM Evaluator**
Ask an LLM to judge correctness or quality.

### **Rule Evaluator**
Pure Python rules to enforce structure & logic.

### **Composite Evaluator**
Combine multiple evaluators into a unified scoring pipeline.

### **Policies & Thresholds**
Define acceptance criteria for enterprise workflows.

---

# 📁 Repository Structure

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

# 🚀 Example: Rule-Based Evaluation

```python
from friday_evaluation import RuleEvaluator

def is_not_empty(output):
    return output is not None and len(str(output)) > 0

evaluator = RuleEvaluator(rules=[is_not_empty])
score = evaluator.evaluate("hello world")
print(score.passed)  # True
```

---

# 🤖 Example: LLM Evaluation

```python
from friday_evaluation import LlmEvaluator

evaluator = LlmEvaluator(
    model="gpt-4o-mini",
    prompt_template="Rate correctness of the agent output from 1-10: {output}"
)

score = evaluator.evaluate("Generated onboarding workflow...")
print(score.score)  # e.g., 8.3
```

---

# 🔗 Integration with Friday Core

```python
from friday import Orchestrator
from friday_evaluation import LlmEvaluator

evaluator = LlmEvaluator(model="gpt-4o-mini")

orchestrator = Orchestrator(agents=agents)
orchestrator.with_evaluation(evaluator)

result = orchestrator.run("start")
```

---

# 🧪 Roadmap

- JSON Schema evaluation  
- Business rule policy DSL  
- Standard evaluation templates  
- Multi-turn evaluation metrics  
- Policy-driven composite evaluators  
- Visual evaluation dashboards  

---

# 🔭 Vision

Friday Evaluation aims to make multi-agent AI systems:

- measurable  
- inspectable  
- trustworthy  
- compliant  
- enterprise-safe  

---

# 📄 License

MIT License
