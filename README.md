<div align="center">

# Rahul Singh

### ML Engineer · LLM Security · Threat Detection · AI Governance

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&pause=1000&color=00F5D4&center=true&vCenter=true&width=900&lines=Threat+Detection+ML+%7C+MITRE+ATT%26CK+Systems;LLM+Red+Teaming+%7C+Prompt+Injection+Testing;AI+Governance+%7C+Compliance+Monitoring;Anomaly+Detection+%7C+SOC+ML+Engineering;GNN+Research+%7C+Cross-Sensor+Alert+Correlation" />

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
<a href="https://github.com/sponsors/rahulsingh1397">
  <img src="https://img.shields.io/badge/❤️ Sponsor-Fund My Work-EA4AAA?style=for-the-badge&logo=githubsponsors&logoColor=white" />
</a>

</div>

-----

## 🎯 What I Build

<img align="right" src="https://media.giphy.com/media/077i6AULCXc0FKTj9s/giphy.gif" width="190" />

I design and deploy **machine learning systems for security-critical environments**. My work breaks into three connected areas:

**🔍 Threat Detection ML** — GNN-based systems that cluster raw security alerts into attack campaigns mapped to MITRE ATT&CK. Research-grade, evaluated on real enterprise datasets.

**🛡️ LLM Security** — Automated red-teaming platforms that test production LLM deployments for prompt injection, jailbreaks, data leakage, and RAG poisoning — with actual reports, not just scripts.

**📋 AI Governance** — Compliance monitoring systems for production ML — the unglamorous work that keeps regulated teams from failing audits.

> *Most AI projects die in notebooks. Mine run in production against real attacks.*

<br clear="right"/>

-----

## 📊 By The Numbers

<div align="center">

|Metric                         |Value                          |Where                                     |
|-------------------------------|-------------------------------|------------------------------------------|
|Security datasets evaluated    |**9**                          |UNSW-NB15 · OpTC · BETH · TON_IoT + 5 more|
|Bridge edge improvement (OpTC) |**ARI 0.215 → 0.282 (+6.7 pp)**|DARPA OpTC                                |
|Bridge edge coverage           |**21% of alerts**              |DARPA OpTC (IP↔hostname pairs)            |
|MITRE ATT&CK tactics covered   |**14 / 14**                    |MITRE-Core v2                             |
|Adversarial LLM tests per audit|**61** across 6 vuln classes   |LLM Auditor                               |
|SOC reporting effort reduced   |**60%**                        |Sequretek                                 |

</div>

-----

## 🚀 Featured Projects

-----

### 🔍 Threat Detection ML

-----

#### MITRE-Core v2 — Heterogeneous GNN Alert Correlation Engine

<img align="right" src="https://media.giphy.com/media/RDZo7znAdn2u7sAcWH/giphy.gif" width="200" />

🔗 [Mitre-Core_v2](https://github.com/rahulsingh1397/Mitre-Core_v2)  ·  `Research · Production`

SOC teams drown in disconnected alerts. This system correlates them into coherent MITRE ATT&CK-mapped attack campaigns automatically.

**Architecture**

```
Raw Alerts (SIEM · EDR · Network)
              │
              ▼
┌─────────────────────────────────┐
│     Heterogeneous Graph          │
│     Host · IP · Tactic nodes     │
│     + Bridge Edges (IP↔Hostname) │
└──────────────┬──────────────────┘
               │
               ▼
┌─────────────────────────────────┐
│     HGNN Encoder (HGT, 15-dim)   │
│     Multi-head attention         │
│     per edge type                │
└──────────────┬──────────────────┘
               │
       ┌───────┴────────┐
       │                │
       ▼                ▼
High confidence    Low confidence
       │                │
       ▼                ▼
  HDBSCAN          Union-Find
  clustering        fallback
       │                │
       └───────┬────────┘
               │
               ▼
   MITRE ATT&CK Campaign Map
```

**What makes it different:**

- Heterogeneous GNN — hosts, IPs, and tactics as distinct node types with different edge semantics
- **Cross-sensor bridge edges** (IP↔hostname): ARI 0.215 → 0.282 (+6.7 pp) on DARPA OpTC — preliminary finding, single dataset
- **9 real-world security datasets** · 14/14 MITRE ATT&CK tactics · SIEM integration
- 2-tier architecture: HGNN semantic clustering + Union-Find structural fallback

```
With bridge edges:    ARI = 0.282 ± 0.048
Without bridge edges: ARI = 0.215 ± 0.056
Δ ARI = +6.7 pp — consistent across all gate configurations
Bridge edge coverage: 21% of OpTC alerts (IP↔hostname pairs)
Preliminary analysis — single dataset, single sweep
```

`PyTorch Geometric` `HDBSCAN` `Flask` `Plotly` `Docker` `DARPA OpTC` `UNSW-NB15`

<br clear="right"/>

-----

#### RL Logon Anomaly Detection — Adaptive SOC Threshold Engine

🔗 [Reinforcement_learning_AnomalyDetection](https://github.com/rahulsingh1397/Reinforcement_learning_AnomalyDetection)  ·  `SOC ML`

Static thresholds are why SOC teams ignore most of their alerts. This learns from analyst feedback and adapts.

**Architecture**

```
Windows Event Logs
        │
        ▼
┌───────────────────────┐
│   Behavioral Profile   │
│   Per-user baseline    │
│   Time · IP · Dest     │
└──────────┬────────────┘
           │
           ▼
┌───────────────────────┐
│   RL Agent             │
│   State: user profile  │
│   Action: threshold    │
│   Reward: analyst      │
│   feedback             │
└──────────┬────────────┘
           │
           ▼
  Anomaly Score → SIEM
```

- 3-hour behavioral windows per identity — source IP, destination, temporal patterns
- **Reinforcement feedback loop** — analyst verdicts directly update per-user thresholds
- Weekday vs weekend pattern separation per identity
- SIEM-ready JSON anomaly output

`Python` `Reinforcement Learning` `Pandas` `NumPy` `SIEM Integration`

-----

### 🛡️ LLM Security

-----

#### Enterprise LLM Security Auditor — Production Red-Teaming Platform

<img align="right" src="https://media.giphy.com/media/3o7aCSPqXE5C6T8tBC/giphy.gif" width="175" />

🔗 [Enterprise_LLM_Security_Auditor](https://github.com/rahulsingh1397/Enterprise_LLM_Security_Auditor)  ·  `LLM Security`

Turns LLM red-teaming from a person manually typing prompts into a repeatable, client-ready workflow.

**Architecture**

```
Target LLM Endpoint
        │
        ▼
┌─────────────────────────────────┐
│      Attack Orchestrator         │
│      61 adversarial tests        │
│      6 vulnerability classes     │
└──────┬──────┬──────┬─────┬──────┘
       │      │      │     │
       ▼      ▼      ▼     ▼
  Prompt  Jailbreak PII  RAG
  Inject  Testing  Leak  Poison
       │      │      │     │
       └──────┴──────┴─────┘
                  │
                  ▼
     Claude Semantic Evaluator
     (did the attack succeed?)
                  │
                  ▼
     PDF Report · Risk Scores
     Remediation Steps
```

- **61 adversarial tests** across 6 vuln classes: prompt injection, jailbreaks, PII leakage, data exfiltration, RAG poisoning, system prompt extraction
- **Claude as semantic evaluator** — understands whether a response actually exposed a vulnerability
- Full audit in **5–10 minutes** with live WebSocket progress
- Executive-ready PDF reports with risk scores and remediation steps

`FastAPI` `React` `WebSockets` `SQLite` `Anthropic Claude API` `Docker`

<br clear="right"/>

-----

#### Community Rule Classification — Explainable NLP Security

🔗 [Community_rule_classification](https://github.com/rahulsingh1397/Community_rule_classification)  ·  `NLP · Security`

Generic moderation APIs fail because they don’t understand context. This learns the specific semantic rules of a community and explains *why* something violates them.

- Fine-tuned transformer with **explanation-first design** — outputs the violated rule, not just a flag
- **92% precision** vs lower rates from keyword filters
- ~60% reduction in moderator workload

`PyTorch` `Transformers` `HuggingFace` `NLTK`

-----

### 📋 AI Governance

-----

#### AI Compliance Monitor — Multi-Module Production ML Governance

<img align="right" src="https://media.giphy.com/media/du3J3cXyzhj75IOgvA/giphy.gif" width="170" />

🔗 [AI_Compliance_Monitor](https://github.com/rahulsingh1397/AI_Compliance_Monitor)  ·  `AI Governance`

Enterprise AI programs ship models without a unified way to monitor behavior or generate audit evidence. This fixes that.

**Architecture**

```
┌──────────────────────────────────────────┐
│          Event Bus (Orchestrator)         │
└──┬──────┬──────┬──────┬──────┬───────────┘
   │      │      │      │      │
   ▼      ▼      ▼      ▼      ▼
 Data  Monitor Privacy Remed Report
 Disc   Agent   Agent  Agent  Agent
 Agent  (ML     (Diff  (Human (PDF·
 (PII   anomaly priv·  apprvl PPT)
 scan)  detect) fedlt) reqd)
   │      │      │      │      │
   └──────┴──────┴──────┴──────┘
                  │
                  ▼
    QRadar · JIRA · Slack · Email
```

- **6 specialized modules** coordinated through event-driven orchestration
- ML-powered anomaly detection: **Isolation Forest + Autoencoders**
- Privacy-preserving: **differential privacy · federated learning · zero-knowledge proofs**
- Native integrations: **QRadar · JIRA · Slack · email**
- One-click **PDF + PPT audit exports** auto-generated from live scan data
- Built for **SOC2 / ISO 27001 / GDPR / HIPAA** compliance workflows

`Python` `FastAPI` `Kafka` `QRadar` `Slack API` `Docker`

<br clear="right"/>

-----

## ⚡ Technical Arsenal

```
Threat Detection    MITRE ATT&CK · Alert Correlation · Anomaly Detection · SIEM Integration
                    Behavioral Analysis · SOC Workflows · Provenance Graph Analysis

LLM Security        Prompt Injection · Jailbreak Testing · RAG Poisoning · PII Leakage
                    LLM Red Teaming · Adversarial Evaluation · Agentic AI Security

Graph ML            PyTorch Geometric · Heterogeneous GNN · HDBSCAN · NetworkX
                    Unsupervised Clustering · Cross-Sensor Correlation

AI Governance       Model Monitoring · Drift Detection · Audit Trail Generation
                    Compliance Frameworks · AI Auditing · Explainability

Production Stack    Python · FastAPI · Docker · Kubernetes · AWS · PyTorch · CI/CD
```

-----

## 🧪 Active Research

|What                                      |Status       |Details                                                                  |
|------------------------------------------|-------------|-------------------------------------------------------------------------|
|**v3.0 — HDBSCAN border point fix**       |🔄 In Progress|Replace `clusterer.probabilities_` with `all_points_membership_vectors()`|
|**Hybrid SSL + Supervised architecture**  |🔄 In Progress|Dual-path loss: NT-Xent + SupCon — Stage 1 SSL warmup, Stage 2 λ-annealed|
|**network_v9_v2 (15-dim self-supervised)**|🔄 Training   |First true 15-dim checkpoint — joint training on RTX 5060 Ti             |
|**Multi-domain expansion**                |📋 Planned    |LANL 2015 + DAPT2020 → 5-domain training                                 |
|**Bridge edge replication**               |📋 Planned    |Multi-seed validation across UNSW and TON_IoT                            |
|**arXiv preprint**                        |✍️ Drafting   |Bridge edge cross-sensor correlation: preliminary findings on DARPA OpTC |
|**Domain-specialized checkpoints**        |🔭 Research   |Separate models for network IT / host APT / IoT                          |

**Why this matters:**
M-Trends 2026 confirms state-sponsored actors are integrating AI mid-attack — malware families like PROMPTFLUX and PROMPTSTEAL now query LLMs during execution to evade detection. Static correlation systems can’t keep up. Multi-domain GNNs that adapt across sensor types are where the field is moving.

-----

## 📈 GitHub Activity

<div align="center">

[![GitHub Streak](https://streak-stats.demolab.com?user=rahulsingh1397&theme=dark&hide_border=true&ring=00F5D4&fire=00F5D4&currStreakLabel=00F5D4&background=0a0a0a)](https://git.io/streak-stats)

</div>

-----

<div align="center">

<img src="https://media.giphy.com/media/Dh5q0sShxgp13DwrvG/giphy.gif" width="90" />


> **AI without security is a liability. Security without ML can’t scale.**

*Stevens Institute of Technology · MS Information Systems · Jersey City, NJ*

**Open to:** ML Security Engineer · Threat Detection ML · LLM Security Engineer · Applied AI Security

<br/>

<a href="https://github.com/sponsors/rahulsingh1397">
  <img src="https://img.shields.io/badge/❤️ Support My Research-Sponsor on GitHub-EA4AAA?style=for-the-badge&logo=githubsponsors&logoColor=white" />
</a>

</div>
