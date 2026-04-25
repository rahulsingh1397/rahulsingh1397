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
  <img src="https://img.shields.io/badge/❤️ Sponsor-Fund My Work-EA4AAA?style=for-the-badge&logo=githubsponsons&logoColor=white" />
</a>

<br/>

![Profile Views](https://komarev.com/ghpvc/?username=rahulsingh1397&color=00F5D4&style=for-the-badge&label=PROFILE+VIEWS)

</div>

-----

## 🎯 What I Build

<img align="right" src="https://media.giphy.com/media/077i6AULCXc0FKTj9s/giphy.gif" width="190" />

I build **production AI systems** — from heterogeneous GNNs to LLM pipelines — across security, healthcare, and enterprise environments.

Five years of owning ML end-to-end: architecture decisions, training pipelines, evaluation frameworks, production deployment, and continuous improvement. Not just notebooks — systems that run against real data, real users, and real constraints.

**🔬 ML Research** — Heterogeneous graph neural networks, unsupervised clustering, anomaly detection. Evaluated on real-world datasets with rigorous methodology and honest reporting.

**🤖 LLM Systems** — RAG pipelines, ReAct agents, evaluation harnesses, prompt engineering. Built for regulated environments where every output needs to be auditable.

**⚙️ Production Engineering** — FastAPI, Docker, Kubernetes, CI/CD. Systems that run at scale, not just demos.

> *Most AI projects die in notebooks. Mine run in production.*

<br clear="right"/>

-----

## 📊 By The Numbers

<div align="center">

|Metric                           |Value                               |Where                                                        |
|---------------------------------|------------------------------------|-------------------------------------------------------------|
|Security datasets evaluated      |**6**                               |UNSW-NB15 · OpTC · TON_IoT · NSL-KDD · CICIDS2017 · SQTK_SIEM|
|Best zero-shot ARI               |**0.979**                           |DARPA OpTC (host telemetry)                                  |
|NSL-KDD improvement over baseline|**2.4× GMM** (0.299 → 0.722)        |Zero-shot                                                    |
|MITRE ATT&CK node/edge types     |**8 node types · 26 edge relations**|MITRE-Core v2                                                |
|Adversarial LLM tests per audit  |**61** across 6 vuln classes        |LLM Auditor                                                  |
|RAG pipeline daily queries       |**2K–5K**                           |Syneos Health                                                |
|SOC reporting effort reduced     |**60%**                             |Sequretek                                                    |

</div>

-----

## 🚀 Featured Projects

-----

### 🔬 ML Research

-----

#### MITRE-Core v2 — Unsupervised Attack Campaign Correlation Engine

<img align="right" src="https://media.giphy.com/media/RDZo7znAdn2u7sAcWH/giphy.gif" width="200" />

🔗 [Mitre-Core_v2](https://github.com/rahulsingh1397/Mitre-Core_v2)  ·  `Research · Production`

Production-grade alert correlation engine that clusters raw SOC/SIEM alerts into MITRE ATT&CK-mapped attack campaigns — **entirely unsupervised at inference time**.

**Architecture**

```
Raw Alerts (CSV · Parquet · SIEM)
              │
              ▼
  AlertToGraphConverter
  shares_ip · shares_host · temporal_near
  8 node types · 26 edge relations
              │
              ▼
  MITREHeteroGNN (HeteroGATConv)
  15-dim features → 128-dim embeddings
  LayerNorm + residual · 4 attention heads
              │
              ▼
  [Optional] Soft-ZCA Whitening
  Fixes embedding collapse (cosine_sim > 0.95)
              │
              ▼
  GAEC — Geometry-Aware Ensemble Clustering
  HDBSCAN · Spectral · BGMM
  Per-alert confidence scoring
              │
      ┌───────┴────────┐
      ▼                ▼
High-confidence   Low-confidence
HGNN assignment   Union-Find pass
      │                │
      └───────┬────────┘
              ▼
  Campaign Clusters + MITRE ATT&CK Mapping
```

**Three operating modes — production inference is always unsupervised:**

|Mode     |Training Signal                     |Inference                                  |
|---------|------------------------------------|-------------------------------------------|
|Zero-shot|None                                |HDBSCAN / Spectral on embeddings           |
|SupCon   |Campaign labels at training only    |Spectral clustering, no labels at inference|
|Prototype|Campaign labels at train + inference|Nearest-centroid in embedding space        |

**Results across 6 datasets (canonical checkpoint: `network_v9_v3`):**

|Dataset       |Domain                |Zero-Shot ARI|Best ARI |Mode                     |
|--------------|----------------------|-------------|---------|-------------------------|
|**DARPA OpTC**|Host/Windows telemetry|**0.979**    |0.979    |Zero-shot                |
|**TON_IoT**   |IoT Network           |**0.737**    |0.845    |Supervised prototype     |
|**NSL-KDD**   |Network IDS           |**0.722**    |0.722    |Zero-shot · 2.4× over GMM|
|**UNSW-NB15** |Network               |0.034        |**0.487**|SupCon v7 + Spectral k=8 |
|**CICIDS2017**|Network               |**0.284**    |0.440    |Semi-supervised          |
|**SQTK_SIEM** |Enterprise SIEM       |0.111        |**0.814**|Supervised prototype     |

**Key technical innovations:**

- **15-dim contextual features** — tactic frequency, IP entropy, temporal density computed at inference (no training domain bias) — reduces embedding cosine similarity from >0.99 to ~0.26
- **Soft-ZCA whitening** — post-hoc `W = U(Λ+εI)^{-½}Uᵀ` decorrelates collapsed embeddings without retraining (arXiv:2411.17538)
- **Label-pure edge filtering** during SupCon — removes cross-campaign edges to prevent boundary blurring
- **Two-phase batch inference** — embeds full dataset before clustering, not chunk-by-chunk (recovered ARI from ~0 to verified baselines)

**Selected ablation findings:**

|Finding                    |Result                                                                    |
|---------------------------|--------------------------------------------------------------------------|
|Union-Find refinement      |Net-harmful across all datasets (singleton fraction >0.80) — disabled     |
|HDBSCAN per-chunk windowing|ARI ≈ 0 (random) vs. ARI=0.72 full-set — always embed full batch first    |
|6-dim vs. 15-dim features  |cosine_sim 0.99→0.26, large ARI improvement — 15-dim is production default|
|ZCA eps=0.1 on SQTK_SIEM   |cosine_sim 0.95→0.10 — clustering recovers structure                      |

`PyTorch Geometric` `HeteroGATConv` `HDBSCAN` `Spectral Clustering` `UMAP` `Docker` `DARPA OpTC` `UNSW-NB15`

<br clear="right"/>

-----

#### RL Logon Anomaly Detection — Adaptive Threshold Engine

🔗 [Reinforcement_learning_AnomalyDetection](https://github.com/rahulsingh1397/Reinforcement_learning_AnomalyDetection)  ·  `Anomaly Detection · RL`

Per-user behavioral anomaly detection that adapts thresholds from analyst feedback — replacing static rules with learned, dynamic profiles.

- 3-hour behavioral windows per identity — source IP, destination, temporal patterns
- **RL feedback loop** — analyst verdicts directly retrain per-user thresholds
- Weekday vs weekend separation per identity
- SIEM-ready JSON output · 60% reduction in manual SOC reporting

`Python` `Reinforcement Learning` `Pandas` `NumPy` `SIEM Integration`

-----

### 🤖 LLM Systems

-----

#### Enterprise AI Knowledge Agent — Production RAG + ReAct System

`Production · Regulated Environment · Syneos Health`

Production-grade RAG pipeline and LangChain ReAct agent serving 50–100 clinical analysts across 50K+ HIPAA-regulated documents.

**Architecture**

```
User Query
    │
    ▼
Governance Layer (Presidio PII + OPA RBAC)
    │
    ▼
ReAct Agent (LangChain) — Tool Router
    │              │              │
    ▼              ▼              ▼
Hybrid           SQL           External
Retrieval        Tool           API
BM25 + Dense  Structured    Filings/refs
FAISS + RRF     data
Cross-encoder
re-ranking
    │              │              │
    └──────────────┴──────────────┘
                   │
                   ▼
             GPT-4o Inference
                   │
                   ▼
      Post-gen PII scan · Confidence score
      Immutable audit logging (S3)
                   │
                   ▼
             Final Response
```

- Hybrid retrieval: BM25 + dense embeddings fused with RRF — Recall@5 improved 0.68 → 0.91
- Cross-encoder re-ranking (BGE-reranker-v2-m3) — nDCG +18–27%
- Double-layer PII governance: pre-LLM Presidio + post-generation masking — **zero compliance incidents**
- RAGAS + LangSmith continuous evaluation: faithfulness, answer relevance, context precision
- **P99 latency: 1.45s** at 2K–5K daily queries · 50–100 concurrent analysts

`LangChain` `OpenAI` `FAISS` `FastAPI` `Docker` `RAGAS` `LangSmith` `spaCy`

-----

#### Enterprise LLM Security Auditor — Adversarial Evaluation Harness

<img align="right" src="https://media.giphy.com/media/3o7aCSPqXE5C6T8tBC/giphy.gif" width="175" />

🔗 [Enterprise_LLM_Security_Auditor](https://github.com/rahulsingh1397/Enterprise_LLM_Security_Auditor)  ·  `LLM Evaluation`

Systematic evaluation harness for measuring LLM vulnerability surface in production deployments — repeatable, semantically evaluated.

- **61 adversarial tests** across 6 vulnerability classes: prompt injection, jailbreaks, PII leakage, data exfiltration, RAG poisoning, system prompt extraction
- **Claude as semantic evaluator** — judges whether a response actually exposed a vulnerability
- Full audit in **5–10 minutes** · PDF reports with risk scores and remediation steps

`FastAPI` `React` `WebSockets` `Anthropic Claude API` `Docker`

<br clear="right"/>

-----

### ⚙️ Production Systems

-----

#### AI Compliance Monitor — Multi-Module ML Governance System

<img align="right" src="https://media.giphy.com/media/du3J3cXyzhj75IOgvA/giphy.gif" width="170" />

🔗 [AI_Compliance_Monitor](https://github.com/rahulsingh1397/AI_Compliance_Monitor)  ·  `MLOps · Governance`

Event-driven multi-module system for monitoring production ML behavior and generating regulatory audit evidence automatically.

- **6 specialized modules** coordinated through event-driven orchestration
- ML anomaly detection: **Isolation Forest + Autoencoders**
- Privacy-preserving: **differential privacy · federated learning · zero-knowledge proofs**
- Native integrations: **QRadar · JIRA · Slack · email**
- One-click **PDF + PPT audit exports** for SOC2 / ISO 27001 / GDPR / HIPAA

`Python` `FastAPI` `Kafka` `QRadar` `Slack API` `Docker`

<br clear="right"/>

-----

#### Community Rule Classification — Explainable NLP

🔗 [Community_rule_classification](https://github.com/rahulsingh1397/Community_rule_classification)  ·  `NLP · Classification`

Fine-tuned transformer that classifies content violations and explains *which rule* was violated — not just a flag.

- **Explanation-first design** — outputs the violated rule, not just a binary label
- **92% precision** vs lower rates from keyword filters · ~60% reduction in moderator workload

`PyTorch` `Transformers` `HuggingFace` `NLTK`

-----

## ⚡ Technical Arsenal

```
Graph ML            PyTorch Geometric · HeteroGATConv · HDBSCAN · Spectral Clustering
                    UMAP · Soft-ZCA Whitening · Confidence Calibration · SupCon Fine-tuning

LLM Engineering     RAG Pipelines · ReAct Agents · Prompt Engineering · Tool Use
                    RAGAS · LangSmith · Evaluation Frameworks · Hallucination Mitigation

ML Fundamentals     Anomaly Detection · Reinforcement Learning · Transformers · XGBoost
                    Feature Engineering · Statistical Testing · Ablation Methodology

Production Stack    FastAPI · Docker · Kubernetes · AWS · CI/CD · Redis · Kafka
                    Model Monitoring · Drift Detection · Audit Logging · RBAC
```

-----

## 🧪 Active Research

|What                             |Status     |Details                                                |
|---------------------------------|-----------|-------------------------------------------------------|
|**SupCon label-pure fine-tuning**|✅ Verified |ARI 0.034→0.408 on UNSW-NB15 (SupCon v7 + Spectral k=8)|
|**ZCA whitening for SIEM data**  |✅ Verified |cosine_sim 0.95→0.10 · ARI 0.111→0.814 on SQTK_SIEM    |
|**network_v9_v3 backbone**       |✅ Canonical|Zero-shot ARI=0.979 on OpTC · 0.722 on NSL-KDD         |
|**Multi-domain expansion**       |📋 Planned  |LANL 2015 + DAPT2020 → 5-domain training               |
|**Bridge edge replication**      |📋 Planned  |Multi-seed validation — current finding preliminary    |
|**arXiv preprint**               |✍️ Drafting |GAEC pipeline + ablation results across 6 datasets     |

-----

## 📈 GitHub Activity

<div align="center">

![Profile Views](https://komarev.com/ghpvc/?username=rahulsingh1397&color=00F5D4&style=for-the-badge&label=PROFILE+VIEWS)

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
