<div align="center">

# Rahul Singh
### ML Security Engineer · LLM Security · Threat Detection · AI Governance

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&pause=1000&color=00F5D4&center=true&vCenter=true&width=900&lines=Threat+Detection+ML+%7C+MITRE+ATT%26CK+Systems;LLM+Red+Teaming+%7C+Prompt+Injection+Testing;AI+Governance+%7C+Compliance+Monitoring;Anomaly+Detection+%7C+SOC+ML+Engineering;GNN+Research+%7C+ARI+0.8224+%7C+p%3D0.021" />

<br/>

<a href="https://rahulaiportfolio.netlify.app/">
  <img src="https://img.shields.io/badge/🌐 Portfolio-rahulaiportfolio.netlify.app-00F5D4?style=for-the-badge" />
</a>
<a href="mailto:rahul.rs1397@gmail.com">
  <img src="https://img.shields.io/badge/📩 Email-Contact-D14836?style=for-the-badge&logo=gmail&logoColor=white" />
</a>
<a href="https://linkedin.com/in/rahulsingh1397">
  <img src="https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" />
</a>

</div>

---

## 🎯 What I Build

<img align="right" src="https://media.giphy.com/media/077i6AULCXc0FKTj9s/giphy.gif" width="190" />

I'm an ML Security Engineer working at the intersection of machine learning and cybersecurity. My work breaks into three connected areas:

**🔍 Threat Detection ML** — GNN-based systems that cluster raw security alerts into attack campaigns mapped to MITRE ATT&CK. Research-grade, evaluated on real enterprise datasets.

**🛡️ LLM Security** — Automated red-teaming platforms that test production LLM deployments for prompt injection, jailbreaks, data leakage, and RAG poisoning — with actual reports, not just scripts.

**📋 AI Governance** — Compliance monitoring systems for production ML — the unglamorous work that keeps regulated teams from failing audits.

> *Most AI projects die in notebooks. Mine run in production against real attacks.*

<br clear="right"/>

---

## 📊 By The Numbers

<div align="center">

| Metric | Value | Where |
|--------|-------|-------|
| Multi-domain clustering ARI | **0.8224** | MITRE-Core v2 |
| Bridge edge Δ ARI | **+0.067** | DARPA OpTC |
| Statistical significance | **p = 0.021** | DARPA OpTC |
| Effect size | **Cohen's d = 1.28** | DARPA OpTC |
| Security datasets evaluated | **9** | UNSW-NB15 · OpTC · BETH · TON\_IoT + 5 more |
| MITRE ATT&CK tactics covered | **14 / 14** | MITRE-Core v2 |
| Adversarial LLM tests per audit | **61** across 6 vuln classes | LLM Auditor |
| SOC reporting effort reduced | **60%** | Sequretek |

</div>

---

## 🚀 Featured Projects

---

### 🔍 Threat Detection ML

---

#### MITRE-Core v2 — Heterogeneous GNN Alert Correlation Engine

<img align="right" src="https://media.giphy.com/media/RDZo7znAdn2u7sAcWH/giphy.gif" width="200" />

🔗 [Mitre-Core_v2](https://github.com/rahulsingh1397/Mitre-Core_v2) &nbsp;·&nbsp; `Research · Production`

SOC teams drown in disconnected alerts. This system correlates them into coherent MITRE ATT&CK-mapped attack campaigns automatically.

**What makes it research-grade:**
- Heterogeneous GNN (HGNN) — hosts, IPs, and tactics treated as distinct node types with different edge semantics
- **Cross-sensor bridge edges** (IP↔hostname): statistically proven to improve APT clustering — **ARI +0.067, p=0.021, Cohen's d=1.28 (large effect)**
- Multi-domain ARI **0.8224** — trained across UNSW-NB15 + BETH + DARPA OpTC
- **9 real-world security datasets** · 14/14 MITRE ATT&CK tactics · SIEM integration
- 2-tier architecture: HGNN → Union-Find structural fallback with optional Transformer hybrid

```
With bridge edges:    ARI = 0.282 ± 0.048
Without bridge edges: ARI = 0.215 ± 0.056
Δ ARI = +0.067  |  p = 0.021  |  Cohen's d = 1.28
```

`PyTorch Geometric` `HDBSCAN` `Flask` `Plotly` `Docker` `DARPA OpTC` `UNSW-NB15`

<br clear="right"/>

---

#### RL Logon Anomaly Detection — Adaptive SOC Threshold Engine

🔗 [Reinforcement_learning_AnomalyDetection](https://github.com/rahulsingh1397/Reinforcement_learning_AnomalyDetection) &nbsp;·&nbsp; `SOC ML`

Static thresholds are why SOC teams ignore most of their alerts. This learns from analyst feedback and adapts.

- 3-hour behavioral windows per identity — source IP, destination, temporal patterns
- **Reinforcement feedback loop** — analyst verdicts directly update per-user thresholds
- Weekday vs weekend pattern separation per identity
- SIEM-ready JSON anomaly output

`Python` `Reinforcement Learning` `Pandas` `NumPy` `SIEM Integration`

---

### 🛡️ LLM Security

---

#### Enterprise LLM Security Auditor — Production Red-Teaming Platform

<img align="right" src="https://media.giphy.com/media/3o7aCSPqXE5C6T8tBC/giphy.gif" width="175" />

🔗 [Enterprise_LLM_Security_Auditor](https://github.com/rahulsingh1397/Enterprise_LLM_Security_Auditor) &nbsp;·&nbsp; `LLM Security`

Turns LLM red-teaming from a person manually typing prompts into a repeatable, client-ready workflow.

- **61 adversarial tests** across 6 vuln classes: prompt injection, jailbreaks, PII leakage, data exfiltration, RAG poisoning, system prompt extraction
- **Claude as semantic evaluator** — understands whether a response actually exposed a vulnerability
- Full audit in **5–10 minutes** with live WebSocket progress
- Executive-ready PDF reports with risk scores and remediation steps

`FastAPI` `React` `WebSockets` `SQLite` `Anthropic Claude API` `Docker`

<br clear="right"/>

---

#### Community Rule Classification — Explainable NLP Security

🔗 [Community_rule_classification](https://github.com/rahulsingh1397/Community_rule_classification) &nbsp;·&nbsp; `NLP · Security`

Generic moderation APIs fail because they don't understand context. This learns the specific semantic rules of a community and explains *why* something violates them.

- Fine-tuned transformer with **explanation-first design** — outputs the violated rule, not just a flag
- **92% precision** vs lower rates from keyword filters
- ~60% reduction in moderator workload

`PyTorch` `Transformers` `HuggingFace` `NLTK`

---

### 📋 AI Governance

---

#### AI Compliance Monitor — Agent-Based Production ML Governance

<img align="right" src="https://media.giphy.com/media/du3J3cXyzhj75IOgvA/giphy.gif" width="170" />

🔗 [AI_Compliance_Monitor](https://github.com/rahulsingh1397/AI_Compliance_Monitor) &nbsp;·&nbsp; `AI Governance`

Enterprise AI programs ship models without a unified way to monitor behavior or generate audit evidence. This fixes that.

- **6 specialized agents** (Data Discovery, Monitoring, Privacy, Remediation, Reporting, UI) on shared event bus
- Native integrations: **QRadar · JIRA · Slack · email**
- One-click **PDF + PPT audit exports** auto-generated from live scan data
- Built for **SOC2 / ISO 27001** compliance workflows

`Python` `FastAPI` `Kafka` `QRadar` `Slack API` `Docker`

<br clear="right"/>

---

## ⚡ Technical Arsenal

```
Threat Detection    MITRE ATT&CK · Alert Correlation · Anomaly Detection · SIEM Integration
                    Behavioral Analysis · SOC Workflows · Provenance Graph Analysis

LLM Security        Prompt Injection · Jailbreak Testing · RAG Poisoning · PII Leakage
                    LLM Red Teaming · Adversarial Evaluation · Agentic AI Security

Graph ML            PyTorch Geometric · Heterogeneous GNN · HDBSCAN · NetworkX
                    Unsupervised Clustering · Statistical Validation (ARI · Cohen's d)

AI Governance       Model Monitoring · Drift Detection · Audit Trail Generation
                    Compliance Frameworks · AI Auditing · Explainability

Production Stack    Python · FastAPI · Docker · Kubernetes · AWS · PyTorch · CI/CD
```

---

## 🧪 Active Research

Pulled directly from [MITRE-Core v2 current state](https://github.com/rahulsingh1397/Mitre-Core_v2):

| What | Status | Details |
|------|--------|---------|
| **v3.0 — HDBSCAN border point fix** | 🔄 In Progress | Replace `clusterer.probabilities_` with `all_points_membership_vectors()` — fixes border points routing to UF incorrectly |
| **Multi-domain expansion** | 📋 Planned | LANL 2015 (temporal network flow) + DAPT2020 → 5-domain training |
| **Cross-domain transfer studies** | 📋 Planned | OpTC → UNSW/BETH performance analysis |
| **arXiv preprint** | ✍️ Drafting | Bridge edge hypothesis: ARI +0.067, p=0.021, d=1.28 |
| **Domain-specialized checkpoints** | 🔭 Research | Separate models for network IT / host APT / IoT instead of forced transfer |

**Why this matters right now:**
M-Trends 2026 confirms that state-sponsored and financially motivated actors are integrating AI to accelerate the attack lifecycle — malware families like PROMPTFLUX and PROMPTSTEAL now actively query LLMs mid-execution to evade detection. Static correlation systems can't keep up. Multi-domain GNNs that adapt across sensor types are the direction the field is moving.

The 2026 LLM security landscape shows that attackers are not just exploiting bugs — they are manipulating how models interpret instructions, assemble context, and interact with connected tools. This is exactly why the LLM Security Auditor focuses on semantic evaluation, not just keyword matching.

---

## 📈 GitHub Activity

<div align="center">

[![GitHub Streak](https://streak-stats.demolab.com?user=rahulsingh1397&theme=dark&hide_border=true&ring=00F5D4&fire=00F5D4&currStreakLabel=00F5D4&background=0a0a0a)](https://git.io/streak-stats)

</div>



<div align="center">

<img src="https://media.giphy.com/media/Dh5q0sShxgp13DwrvG/giphy.gif" width="90" />

> **AI without security is a liability. Security without ML can't scale.**

*Stevens Institute of Technology · MS Information Systems · Jersey City, NJ*

**Open to:** ML Security Engineer · Threat Detection ML · LLM Security Engineer · Applied AI Security

</div>
