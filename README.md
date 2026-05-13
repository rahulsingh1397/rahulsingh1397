<div align="center">

# Rahul Singh

### AI/ML Engineer · Graph Neural Networks · RAG Systems · Production ML

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&pause=1000&color=00F5D4&center=true&vCenter=true&width=900&lines=Production+ML+%7C+End-to-End+Ownership;Graph+Neural+Networks+%7C+Heterogeneous+Graphs;LLM+Pipelines+%7C+RAG+%7C+Agentic+Systems;Evaluation+Frameworks+%7C+Research+Rigour;Security+%7C+Healthcare+%7C+Enterprise+AI" />

<br/>

</div>

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

<br/>

![Profile Views](https://komarev.com/ghpvc/?username=rahulsingh1397&color=00F5D4&style=for-the-badge&label=PROFILE+VIEWS)

</div>

---

## What I Build

<img align="right" src="https://media.giphy.com/media/077i6AULCXc0FKTj9s/giphy.gif" width="180" />

I build production-grade AI systems across cybersecurity, healthcare, and enterprise environments — from heterogeneous graph neural networks to retrieval-augmented LLM systems.

My work focuses on the full ML lifecycle:
- architecture design
- model training
- evaluation methodology
- deployment infrastructure
- operational monitoring
- continuous improvement

I specialize in:
- **Graph ML** — heterogeneous GNNs, clustering systems, anomaly detection
- **LLM Systems** — RAG pipelines, ReAct agents, evaluation harnesses
- **Production Engineering** — FastAPI, Docker, Kubernetes, CI/CD

I focus on production-grade AI systems with measurable evaluation, deployment, and operational monitoring.

<br clear="right"/>

---

## Technical Stack

```text
Graph ML            PyTorch Geometric · HeteroGATConv · HDBSCAN
                    Spectral Clustering · UMAP · SupCon Fine-tuning

LLM Engineering     RAG Pipelines · ReAct Agents · LangChain
                    RAGAS · LangSmith · Prompt Engineering

ML Fundamentals     Anomaly Detection · Reinforcement Learning
                    Transformers · XGBoost · Statistical Evaluation

Production Stack    FastAPI · Docker · Kubernetes · Kafka
                    Redis · AWS · CI/CD · Monitoring Pipelines
```

---

## Verified Benchmark Results (Apr 2026)

All results reproduced using fixed seeds and full-dataset inference.

Canonical checkpoint: `network_v9_v3`

| Dataset | Domain | Zero-Shot ARI | Best ARI | Best Mode |
|---|---|---|---|---|
| DARPA OpTC | Host telemetry | **0.979** *(binary setup)* | 0.979 | Zero-shot |
| NSL-KDD | Network IDS | **0.739** | 0.739 | Zero-shot |
| TON_IoT | IoT Network | 0.431 | **0.845** | Supervised |
| UNSW-NB15 | Enterprise network | **0.401** | **0.538** | SupCon |
| CICIDS2017 | Enterprise IDS | **0.284** | 0.284 | Zero-shot |
| SQTK_SIEM | SIEM / SOC alerts | **0.184** | 0.184 | Zero-shot |

### Evaluation Notes

- Zero-shot inference uses clustering without campaign labels at inference time
- Supervised mode uses prototype classification in embedding space
- All clustering performed on full-dataset embeddings
- Metrics verified Apr 25, 2026

---

## Featured Projects

### MITRE-Core v2 — Attack Campaign Correlation Engine

<img align="right" src="https://media.giphy.com/media/RDZo7znAdn2u7sAcWH/giphy.gif" width="190" />

🔗 **Repository:**  
https://github.com/rahulsingh1397/Mitre-Core_v2

Graph-based cybersecurity correlation engine that clusters SOC/SIEM alerts into MITRE ATT&CK-aligned attack campaigns.

### Why This Research Matters

Security analysts receive thousands of fragmented alerts daily.  
Most existing correlation systems depend heavily on labeled attack campaigns, which are expensive and often unavailable in real-world SOC environments.

MITRE-Core v2 explores whether heterogeneous graph neural networks can cluster attack activity without requiring labels during inference, while remaining robust across multiple telemetry domains.

### Architecture

```text
Raw Alerts
    ↓
AlertToGraphConverter
    ↓
MITREHeteroGNN (HeteroGATConv)
    ↓
Soft-ZCA Whitening
    ↓
GAEC Clustering
(HDBSCAN · Spectral · BGMM)
    ↓
Campaign Clusters + ATT&CK Mapping
```

### Core Technical Contributions

- Heterogeneous graph modeling with 8 node types and 29 edge relations
- 6-dimensional alert features (tactic, alert_type, hour, day, protocol, service) projected into 128-dimensional embedding space
- Geometry-Aware Embedding Confidence (GAEC)
- Soft-ZCA whitening to mitigate representation collapse
- Confidence-aware clustering refinement
- Full-batch embedding inference for stable clustering

### Selected Findings

| Finding | Result |
|---|---|
| Full-batch inference | Restored clustering separability after inference correction |
| 6-dim alert features | Stable cosine similarity ~0.73 (no collapse) |
| ZCA whitening | Recovered clustering structure on sparse SIEM datasets |
| Union-Find refinement | Disabled after net-negative evaluation across datasets |

### Reproducibility

- Fixed random seeds
- Evaluation scripts included
- Dataset preprocessing documented
- Full benchmark commands reproducible

`PyTorch Geometric` `HDBSCAN` `Spectral Clustering` `Docker`

<br clear="right"/>

---

### RL Logon Anomaly Detection — Adaptive Threshold Engine

🔗 **Repository:**  
https://github.com/rahulsingh1397/Reinforcement_learning_AnomalyDetection

Behavioral anomaly detection system that adapts user-level thresholds using analyst feedback loops.

- Reinforcement-learning-based threshold adaptation
- Identity-specific behavioral profiling
- SIEM-ready structured outputs
- Reduced manual SOC reporting workload

`Python` `Reinforcement Learning` `Pandas`

---

### Enterprise AI Knowledge Agent — Production RAG System

Production RAG pipeline and ReAct agent supporting regulated enterprise workflows across large-scale document environments.

### Key Capabilities

- Hybrid retrieval (BM25 + dense retrieval + RRF)
- Cross-encoder re-ranking
- Presidio + RBAC governance layer
- Continuous evaluation using RAGAS and LangSmith
- Audit logging and post-generation compliance checks

### Operational Metrics

- Recall@5 improved from 0.68 → 0.91
- 2K–5K daily queries
- P99 latency: 1.45s
- Zero reported compliance incidents

`LangChain` `FAISS` `FastAPI` `Docker`

---

### Enterprise LLM Security Auditor

<img align="right" src="https://media.giphy.com/media/3o7aCSPqXE5C6T8tBC/giphy.gif" width="170" />

🔗 **Repository:**  
https://github.com/rahulsingh1397/Enterprise_LLM_Security_Auditor

Evaluation harness for measuring vulnerability exposure in production LLM deployments.

### Coverage

- Prompt injection
- Jailbreaks
- PII leakage
- Data exfiltration
- RAG poisoning
- System prompt extraction

### Highlights

- 61 adversarial evaluation tests
- Semantic vulnerability evaluation
- Automated PDF audit generation
- End-to-end audits completed in 5–10 minutes

`FastAPI` `React` `Docker`

<br clear="right"/>

---

### AI Compliance Monitor

<img align="right" src="https://media.giphy.com/media/du3J3cXyzhj75IOgvA/giphy.gif" width="170" />

🔗 **Repository:**  
https://github.com/rahulsingh1397/AI_Compliance_Monitor

Event-driven ML governance system for monitoring production AI behavior and generating audit evidence.

### Features

- Multi-module orchestration
- Isolation Forest + Autoencoder monitoring
- Differential privacy support
- SOC2 / GDPR / HIPAA export pipelines
- Native integrations with enterprise tooling

`FastAPI` `Kafka` `Docker` `QRadar`

<br clear="right"/>

---

## Active Research

| Research Area | Status | Details |
|---|---|---|
| SupCon fine-tuning | ✅ Verified | Improved UNSW-NB15 clustering stability |
| ZCA whitening for SIEM | ✅ Verified | Improved sparse embedding separability |
| Multi-domain training | 📋 Planned | Expansion across additional telemetry domains |
| GAEC arXiv preprint | ✍️ Drafting | Full methodology and ablation analysis |

---

## GitHub Activity

<div align="center">

![GitHub Streak](https://streak-stats.demolab.com?user=rahulsingh1397&theme=dark&hide_border=true&ring=00F5D4&fire=00F5D4&currStreakLabel=00F5D4&background=0a0a0a)

<br/><br/>

![GitHub Activity Graph](https://github-readme-activity-graph.vercel.app/graph?username=rahulsingh1397&bg_color=050816&color=22d3ee&line=06b6d4&point=67e8f9&area_color=164e63&area=true&hide_border=true&radius=10)


</div>

---

<div align="center">

> Building reliable and production-oriented AI systems.

**Stevens Institute of Technology · MS Information Systems**

Open to:
AI/ML Engineer · Applied ML Researcher · LLM Systems Engineer · ML Platform Engineer

</div>
