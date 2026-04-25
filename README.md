<div align="center">

# Rahul Singh

### AI/ML Engineer · Graph Neural Networks · LLM Systems · Production AI

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&pause=1000&color=00F5D4&center=true&vCenter=true&width=900&lines=Production+ML+%7C+End-to-End+Ownership;Graph+Neural+Networks+%7C+Heterogeneous+Graphs;LLM+Pipelines+%7C+RAG+%7C+Agentic+Systems;Evaluation+Frameworks+%7C+Research+Rigour;Security+%7C+Healthcare+%7C+Enterprise+AI" />

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

I build **production AI systems** — from heterogeneous GNNs to LLM pipelines — across security, healthcare, and enterprise environments.

Five years of owning ML end-to-end: architecture decisions, training pipelines, evaluation frameworks, production deployment, and continuous improvement. Not just notebooks — systems that run against real data, real users, and real constraints.

**🔬 ML Research** — Graph neural networks, unsupervised clustering, anomaly detection. Evaluated on real-world datasets with rigorous methodology and honest reporting.

**🤖 LLM Systems** — RAG pipelines, ReAct agents, evaluation harnesses, prompt engineering. Built for regulated environments where every output needs to be auditable.

**⚙️ Production Engineering** — FastAPI, Docker, Kubernetes, CI/CD. Systems that run at scale, not just demos.

> *Most AI projects die in notebooks. Mine run in production.*

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
|RAG pipeline queries daily     |**2K–5K**                      |Syneos Health                             |
|Hallucination rate reduction   |**via RAGAS-driven iteration** |Syneos Health                             |
|SOC reporting effort reduced   |**60%**                        |Sequretek                                 |

</div>

-----

## 🚀 Featured Projects

-----

### 🔬 ML Research

-----

#### MITRE-Core v2 — Heterogeneous GNN Alert Correlation Engine

<img align="right" src="https://media.giphy.com/media/RDZo7znAdn2u7sAcWH/giphy.gif" width="200" />

🔗 [Mitre-Core_v2](https://github.com/rahulsingh1397/Mitre-Core_v2)  ·  `Research · Production`

Unsupervised heterogeneous GNN that clusters raw security alerts into structured attack campaigns — without labeled training data.

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
   Structured Campaign Output
```

**Research contributions:**

- Novel heterogeneous graph construction — hosts, IPs, and tactics as distinct node types with separate edge semantics
- **Cross-sensor bridge edges** (IP↔hostname): ARI 0.215 → 0.282 (+6.7 pp) on DARPA OpTC — preliminary finding, single dataset, single sweep
- Confidence-gated hybrid clustering: HGNN for high-confidence alerts, Union-Find structural fallback for uncertain ones
- Rigorous evaluation across **9 real-world datasets** with honest failure documentation (BETH, NSL-KDD limitations clearly reported)

```
With bridge edges:    ARI = 0.282 ± 0.048
Without bridge edges: ARI = 0.215 ± 0.056
Δ ARI = +6.7 pp — consistent across all gate configurations
Preliminary analysis — single dataset, single sweep
```

`PyTorch Geometric` `HDBSCAN` `HGT` `Flask` `Docker` `DARPA OpTC` `UNSW-NB15`

<br clear="right"/>

-----

#### RL Logon Anomaly Detection — Adaptive Threshold Engine

🔗 [Reinforcement_learning_AnomalyDetection](https://github.com/rahulsingh1397/Reinforcement_learning_AnomalyDetection)  ·  `Anomaly Detection · RL`

Per-user behavioral anomaly detection that adapts thresholds from analyst feedback — replacing static rules with learned, dynamic profiles.

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
│           feedback     │
└──────────┬────────────┘
           │
           ▼
  Anomaly Score → SIEM
```

- 3-hour behavioral windows per identity across source IP, destination, and temporal dimensions
- **Reinforcement feedback loop** — analyst verdicts directly retrain per-user thresholds
- Weekday vs weekend behavioral separation per identity
- SIEM-ready JSON output

`Python` `Reinforcement Learning` `Pandas` `NumPy` `SIEM Integration`

-----

### 🤖 LLM Systems

-----

#### Enterprise AI Knowledge Agent — Production RAG + ReAct System

`Production · Regulated Environment`

Production-grade RAG pipeline and LangChain ReAct agent serving 50–100 clinical analysts across 50K+ sensitive documents in a HIPAA-regulated environment.

**Architecture**

```
User Query
    │
    ▼
┌─────────────────────────────────────┐
│  Governance Layer                    │
│  PII Detection (Presidio + regex)    │
│  RBAC (OPA policies)                 │
└──────────────┬──────────────────────┘
               │
               ▼
┌─────────────────────────────────────┐
│  ReAct Agent (LangChain)             │
│  Tool Router                         │
│  Retrieval · SQL · API               │
└──────┬──────────────┬───────────────┘
       │              │
       ▼              ▼
Hybrid Retrieval    SQL Tool
BM25 + Dense        Structured
FAISS + RRF         financial data
Cross-encoder
re-ranking
       │              │
       └──────┬───────┘
              │
              ▼
         GPT-4o / LLM
              │
              ▼
    Post-gen PII scan
    Confidence scoring
    Audit logging (S3)
              │
              ▼
        Final Response
```

- End-to-end ownership: ingestion → chunking → embedding → retrieval → reranking → generation → evaluation → deployment
- Hybrid retrieval: BM25 + dense embeddings fused with RRF — Recall@5 improved from 0.68 → 0.91
- Cross-encoder re-ranking (BGE-reranker-v2-m3) — nDCG improvement +18–27%
- Double-layer PII governance: pre-LLM Presidio scan + post-generation masking — zero incidents in production
- RAGAS + LangSmith evaluation: faithfulness, answer relevance, context precision tracked continuously
- P99 latency: 1.45s at 2K–5K daily queries across 50–100 concurrent analysts

`LangChain` `OpenAI` `FAISS` `FastAPI` `Docker` `RAGAS` `LangSmith` `spaCy`

-----

#### Enterprise LLM Security Auditor — Adversarial Evaluation Harness

<img align="right" src="https://media.giphy.com/media/3o7aCSPqXE5C6T8tBC/giphy.gif" width="175" />

🔗 [Enterprise_LLM_Security_Auditor](https://github.com/rahulsingh1397/Enterprise_LLM_Security_Auditor)  ·  `LLM Evaluation`

Systematic evaluation harness for measuring LLM vulnerability surface in production deployments — repeatable, client-ready, semantically evaluated.

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

- **61 adversarial tests** across 6 vulnerability classes
- **Claude as semantic evaluator** — judges whether a response actually exposed a vulnerability, not just keyword matching
- Full audit in **5–10 minutes** with live WebSocket progress
- Executive-ready PDF reports with per-class risk scores and remediation steps

`FastAPI` `React` `WebSockets` `Anthropic Claude API` `Docker`

<br clear="right"/>

-----

### ⚙️ Production Systems

-----

#### AI Compliance Monitor — Multi-Module ML Governance System

<img align="right" src="https://media.giphy.com/media/du3J3cXyzhj75IOgvA/giphy.gif" width="170" />

🔗 [AI_Compliance_Monitor](https://github.com/rahulsingh1397/AI_Compliance_Monitor)  ·  `MLOps · Governance`

Event-driven multi-module system for monitoring production ML behavior and generating regulatory audit evidence automatically.

**Architecture**

```
┌──────────────────────────────────────────┐
│          Event Bus (Orchestrator)         │
└──┬──────┬──────┬──────┬──────┬───────────┘
   │      │      │      │      │
   ▼      ▼      ▼      ▼      ▼
 Data  Monitor Privacy Remed Report
 Disc   (ML    (Diff   (Human  (PDF·
 (PII  anomaly  priv·  apprvl  PPT)
 scan) detect) fedlt)  reqd)
   │      │      │      │      │
   └──────┴──────┴──────┴──────┘
                  │
                  ▼
    QRadar · JIRA · Slack · Email
```

- **6 specialized modules** coordinated through event-driven orchestration
- ML-powered anomaly detection: **Isolation Forest + Autoencoders**
- Privacy-preserving techniques: **differential privacy · federated learning · zero-knowledge proofs**
- Native integrations: **QRadar · JIRA · Slack · email**
- One-click **PDF + PPT audit exports** for SOC2 / ISO 27001 / GDPR / HIPAA

`Python` `FastAPI` `Kafka` `QRadar` `Slack API` `Docker`

<br clear="right"/>

-----

#### Community Rule Classification — Explainable NLP

🔗 [Community_rule_classification](https://github.com/rahulsingh1397/Community_rule_classification)  ·  `NLP · Classification`

Fine-tuned transformer that classifies content violations and explains *which rule* was violated — not just a flag.

- **Explanation-first design** — outputs the violated rule with reasoning, not just a binary label
- **92% precision** vs lower rates from keyword filters
- ~60% reduction in moderator workload

`PyTorch` `Transformers` `HuggingFace` `NLTK`

-----

## ⚡ Technical Arsenal

```
Graph ML            PyTorch Geometric · Heterogeneous GNN · HDBSCAN · NetworkX
                    Unsupervised Clustering · Confidence Calibration · Graph Construction

LLM Engineering     RAG Pipelines · ReAct Agents · Prompt Engineering · Tool Use
                    RAGAS · LangSmith · Evaluation Frameworks · Hallucination Mitigation

ML Fundamentals     Anomaly Detection · RL · Transformers · XGBoost · scikit-learn
                    Feature Engineering · Model Calibration · Statistical Testing

Production Stack    FastAPI · Docker · Kubernetes · AWS · CI/CD · Redis · Kafka
                    Model Monitoring · Drift Detection · Audit Logging · RBAC
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

-----

## 📈 GitHub Activity

<div align="center">

[![GitHub Streak](https://streak-stats.demolab.com?user=rahulsingh1397&theme=dark&hide_border=true&ring=00F5D4&fire=00F5D4&currStreakLabel=00F5D4&background=0a0a0a)](https://git.io/streak-stats)

</div>

-----

<div align="center">

<img src="https://media.giphy.com/media/Dh5q0sShxgp13DwrvG/giphy.gif" width="90" />


> *Building AI systems that are accurate, reliable, and production-ready.*

*Stevens Institute of Technology · MS Information Systems · Jersey City, NJ*

**Open to:** AI/ML Engineer · Applied ML Researcher · LLM Systems Engineer · ML Platform Engineer

<br/>

<a href="https://github.com/sponsors/rahulsingh1397">
  <img src="https://img.shields.io/badge/❤️ Support My Research-Sponsor on GitHub-EA4AAA?style=for-the-badge&logo=githubsponsors&logoColor=white" />
</a>

</div>
