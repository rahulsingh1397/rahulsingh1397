<div align="center">

# Rahul Singh
### ML Security Engineer · LLM Security · Threat Detection · AI Governance

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&pause=1000&color=00F5D4&center=true&vCenter=true&width=900&lines=Threat+Detection+ML+%7C+MITRE+ATT%26CK+Systems;LLM+Red+Teaming+%7C+Prompt+Injection+Testing;AI+Governance+%7C+Compliance+Monitoring;Anomaly+Detection+%7C+SOC+ML+Engineering;GNN+Research+%7C+ARI+0.8224+%7C+p%3D0.021" />

<br/>

<a href="https://rahulaiportfolio.netlify.app/">
  <img src="https://img.shields.io/badge/🌐 Portfolio-rahulaiportfolio.netlify.app-00F5D4?style=for-the-badge" />
</a>
<a href="mailto:rahul.rs1397@gmail.com">
  <img src="https://img.shields.io/badge/📩 Email-rahul.rs1397@gmail.com-D14836?style=for-the-badge&logo=gmail&logoColor=white" />
</a>
<a href="https://linkedin.com/in/rahulsingh1397">
  <img src="https://img.shields.io/badge/LinkedIn-rahulsingh1397-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" />
</a>

<br/><br/>

![Profile Views](https://komarev.com/ghpvc/?username=rahulsingh1397&color=00F5D4&style=flat-square&label=profile+views)

</div>

---

## 🎯 What I Build

<img align="right" src="https://media.giphy.com/media/077i6AULCXc0FKTj9s/giphy.gif" width="190" />

I'm an ML Security Engineer working at the intersection of machine learning and cybersecurity. My work breaks into three connected areas:

**🔍 Threat Detection ML** — GNN-based systems that cluster raw security alerts into attack campaigns mapped to MITRE ATT&CK. Research-grade, evaluated on real enterprise datasets.

**🛡️ LLM Security** — Automated red-teaming platforms that test production LLM deployments for prompt injection, jailbreaks, data leakage, and RAG poisoning — with actual reports, not just scripts.

**📋 AI Governance** — Compliance monitoring systems for production ML — the unglamorous work that keeps regulated teams (healthcare, fintech, defense) from failing audits.

> *I've seen what happens when AI ships without security. These projects exist because that's a solvable problem.*

<br clear="right"/>

---

## 🔍 Pillar 1 — Threat Detection ML

*Building ML systems that find real attacks in real data*

---

### MITRE-Core v2 — Heterogeneous GNN Alert Correlation Engine

<img align="right" src="https://media.giphy.com/media/l0HlNQ03J5JxX6lva/giphy.gif" width="175" />

🔗 [Mitre-Core_v2](https://github.com/rahulsingh1397/Mitre-Core_v2) &nbsp;·&nbsp; `Research`

The centrepiece. SOC teams drown in thousands of disconnected alerts — this system correlates them into coherent attack campaigns and maps each one to MITRE ATT&CK tactics automatically.

**What makes it research-grade:**
- Heterogeneous GNN (HGNN) treating hosts, IPs, and tactics as different node types — not a homogeneous graph pretending everything is equal
- **Cross-sensor bridge edges** (IP↔hostname): proved statistically that connecting network and host sensors improves APT clustering — **ARI +0.067, p=0.021, Cohen's d=1.28**
- Multi-domain training on **UNSW-NB15 + BETH + DARPA OpTC** → ARI **0.8224**
- **9 real-world security datasets**, 14/14 MITRE ATT&CK tactics, SIEM integration layer

`PyTorch Geometric` `HDBSCAN` `Flask` `Docker` `DARPA OpTC` `UNSW-NB15` `Python`

<br clear="right"/>

---

### RL Logon Anomaly Detection — Adaptive SOC Threshold Engine

🔗 [Reinforcement_learning_AnomalyDetection](https://github.com/rahulsingh1397/Reinforcement_learning_AnomalyDetection) &nbsp;·&nbsp; `SOC ML`

Static detection thresholds are why SOC teams ignore 90% of their alerts. This system learns from analyst feedback and adapts.

- Aggregates authentication logs into **3-hour behavioral windows** per identity
- **Reinforcement feedback loop** — analyst verdicts (true positive / false positive) directly update per-user thresholds
- Distinguishes weekday vs weekend behavioral patterns automatically
- Outputs **SIEM-ready JSON** anomaly summaries — plugs into existing ops stack

`Python` `Reinforcement Learning` `Pandas` `NumPy` `SIEM Integration`

---

## 🛡️ Pillar 2 — LLM Security

*Testing AI systems before attackers do*

<img align="right" src="https://media.giphy.com/media/3o7aCSPqXE5C6T8tBC/giphy.gif" width="175" />

---

### Enterprise LLM Security Auditor — Production Red-Teaming Platform

🔗 [Enterprise_LLM_Security_Auditor](https://github.com/rahulsingh1397/Enterprise_LLM_Security_Auditor) &nbsp;·&nbsp; `LLM Security`

Most LLM security "testing" is a person manually typing prompts. This turns red-teaming into a repeatable, client-ready workflow.

- **61 adversarial tests** across 6 vulnerability classes: prompt injection, jailbreaks, PII leakage, data exfiltration, RAG poisoning, system prompt extraction
- **Claude as semantic evaluator** — understands whether a response actually exposed a vulnerability, not just pattern-matching keywords
- Full audit completes in **5–10 minutes** with live WebSocket progress
- Generates executive-ready PDF reports with risk scores and remediation steps per finding
- FastAPI backend + React frontend — actually deployable, not a notebook

`FastAPI` `React` `WebSockets` `SQLite` `Anthropic Claude API` `Docker`

<br clear="right"/>

---

### Community Rule Classification — Explainable NLP Security

🔗 [Community_rule_classification](https://github.com/rahulsingh1397/Community_rule_classification) &nbsp;·&nbsp; `NLP · Security Adjacent`

Generic content moderation APIs fail because they don't understand context. This system learns the specific semantic rules of a community and explains *why* something violates them.

- Transfer learning on transformer models fine-tuned to community-specific guidelines
- **Explanation-first design** — model outputs the violated rule, not just a flag
- **92% precision** on violation detection vs lower rates from keyword filters
- Reduced moderator workload by ~60% in evaluation

`PyTorch` `Transformers` `HuggingFace` `NLTK` `Python`

---

## 📋 Pillar 3 — AI Governance & Compliance

*Making AI auditable for the teams that have to answer to regulators*

---

### AI Compliance Monitor — Agent-Based Production ML Governance

<img align="right" src="https://media.giphy.com/media/du3J3cXyzhj75IOgvA/giphy.gif" width="170" />

🔗 [AI_Compliance_Monitor](https://github.com/rahulsingh1397/AI_Compliance_Monitor) &nbsp;·&nbsp; `AI Governance`

The unglamorous but necessary work. Enterprise AI programs ship models without a unified way to monitor privacy exposure, log AI behavior, or generate audit evidence. This fixes that.

- **6 specialized agents** (Data Discovery, Monitoring, Privacy, Remediation, Reporting, UI) coordinating via shared event bus
- Native integrations: **QRadar, JIRA, Slack, email** — alerts flow into the stack teams already use
- One-click **PDF + PPT audit exports** auto-generated from live scan data
- Designed for **SOC2 / ISO 27001** compliance workflows in regulated environments

`Python` `FastAPI` `Kafka` `QRadar` `Slack API` `xhtml2pdf` `Docker`

<br clear="right"/>

---

## ⚡ Technical Arsenal

```
Threat Detection    MITRE ATT&CK · Alert Correlation · Anomaly Detection · SIEM Integration
                    Behavioral Analysis · SOC Workflows · Incident Response ML

LLM Security        Prompt Injection · Jailbreak Testing · RAG Poisoning · PII Leakage
                    LLM Red Teaming · Adversarial Evaluation · AI Risk Assessment

Graph ML            PyTorch Geometric · Heterogeneous GNN · HDBSCAN · NetworkX
                    Unsupervised Clustering · Graph Neural Networks · Statistical Validation

AI Governance       Model Monitoring · Drift Detection · Audit Trail Generation
                    Compliance Frameworks · AI Auditing · Explainability

LLM Engineering     LangChain · RAG · Fine-Tuning · Anthropic Claude API
                    Agent Workflows · Prompt Engineering · HuggingFace

Production Stack    Python · FastAPI · Docker · Kubernetes · AWS · CI/CD · PyTorch
```

---

## 📊 By The Numbers

<div align="center">

```
  0.8224 ARI          p = 0.021           61 Tests            60%
  ─────────────       ─────────────       ─────────────       ─────────────
  Multi-domain        Bridge edge         Adversarial         SOC reporting
  threat clustering   statistical proof   LLM security        effort reduced
  MITRE-Core v2       DARPA OpTC          tests per audit     Sequretek
```

</div>

---

## 🧪 Active Research

<div align="center">

| What | Status |
|------|--------|
| MITRE-Core v3.0 — `all_points_membership_vectors()` HDBSCAN fix | 🔄 In Progress |
| Multi-domain expansion: LANL 2015 + DAPT2020 | 📋 Planned |
| arXiv preprint — bridge edge hypothesis | ✍️ Drafting |
| Conference target: IEEE S&P workshops / CAMLIS / RAID | 🎯 Targeting |

</div>

---

## 📈 GitHub Stats

<div align="center">

<img height="155" src="https://github-readme-stats.vercel.app/api?username=rahulsingh1397&show_icons=true&theme=dark&hide_border=true&title_color=00F5D4&icon_color=00F5D4&text_color=ffffff&bg_color=0a0a0a" />
<img height="155" src="https://github-readme-stats.vercel.app/api/top-langs/?username=rahulsingh1397&layout=compact&theme=dark&hide_border=true&title_color=00F5D4&text_color=ffffff&bg_color=0a0a0a&langs_count=6" />

</div>

---

<div align="center">

<img src="https://media.giphy.com/media/Dh5q0sShxgp13DwrvG/giphy.gif" width="100" />

> **AI without security is a liability. Security without ML can't scale.**

*Stevens Institute of Technology · MS Information Systems · Jersey City, NJ*

**Open to:** ML Security Engineer · Threat Detection ML · LLM Security Engineer · Applied AI Security

</div>
