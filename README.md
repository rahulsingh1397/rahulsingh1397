<div align="center">

# Rahul Singh

### AI/ML Engineer · AI Safety & Agent Security · Graph Neural Networks · Production ML

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&pause=1000&color=00F5D4&center=true&vCenter=true&width=900&lines=At+the+Intersection+of+AI%2FML+and+AI+Safety;Multi-Agent+Security+%7C+Attribution+%7C+Non-Repudiation;Graph+Neural+Networks+%7C+Heterogeneous+Graphs;LLM+Pipelines+%7C+RAG+%7C+Agentic+Systems;Evaluation+Frameworks+%7C+Research+Rigour" />

<br/>

<a href="https://rahulaiportfolio.netlify.app/">
  <img src="https://img.shields.io/badge/🌐_Portfolio-rahulaiportfolio.netlify.app-00F5D4?style=for-the-badge" />
</a>
<a href="mailto:rahul.rs1397@gmail.com">
  <img src="https://img.shields.io/badge/📩_Email-Contact-D14836?style=for-the-badge&logo=gmail&logoColor=white" />
</a>
<a href="https://linkedin.com/in/rahulsingh1397">
  <img src="https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" />
</a>
<a href="https://github.com/sponsors/rahulsingh1397">
  <img src="https://img.shields.io/badge/❤️_Sponsor-Fund_My_Work-EA4AAA?style=for-the-badge&logo=githubsponsors&logoColor=white" />
</a>

<br/>

![Profile Views](https://komarev.com/ghpvc/?username=rahulsingh1397&color=00F5D4&style=for-the-badge&label=PROFILE+VIEWS)

</div>

---

## What I Build

<img align="right" src="https://media.giphy.com/media/077i6AULCXc0FKTj9s/giphy.gif" width="180" />

I work at the intersection of AI/ML engineering and AI safety research — building
production-grade systems *and* the adversarial benchmarks that test whether they
actually hold up. My work spans cybersecurity, healthcare, and enterprise AI: from
heterogeneous graph neural networks, to retrieval-augmented LLM systems, to
red-team benchmarks for multi-agent agent security.

My work focuses on the full ML lifecycle:
- architecture design
- model training
- evaluation methodology
- deployment infrastructure
- operational monitoring
- continuous improvement

I specialize in:
- **AI Safety & Agent Security** — attribution integrity, non-repudiation, adversarial evaluation of multi-agent systems
- **Graph ML** — heterogeneous GNNs, clustering systems, anomaly detection
- **LLM Systems** — RAG pipelines, ReAct agents, evaluation harnesses
- **Production Engineering** — FastAPI, Docker, Kubernetes, CI/CD

<br clear="right"/>

---

## Technical Stack

**AI Safety / Security**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![RFC 8693 / OAuth](https://img.shields.io/badge/RFC_8693_/_OAuth-2C2255?style=flat-square&logo=auth0&logoColor=white)
![RFC 9449 / DPoP](https://img.shields.io/badge/RFC_9449_/_DPoP-1B5E20?style=flat-square&logo=auth0&logoColor=white)
![PyJWT](https://img.shields.io/badge/PyJWT-000000?style=flat-square&logo=jsonwebtokens&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white)
![Threat Modeling](https://img.shields.io/badge/Threat_Modeling-8A1538?style=flat-square&logo=hackthebox&logoColor=white)

**Graph ML**

![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![PyG](https://img.shields.io/badge/PyTorch_Geometric-3C2179?style=flat-square&logo=pytorch&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)
![HDBSCAN](https://img.shields.io/badge/HDBSCAN-1D9E75?style=flat-square&logoColor=white)

**LLM Engineering**

![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![FAISS](https://img.shields.io/badge/FAISS-0467DF?style=flat-square&logo=meta&logoColor=white)
![RAGAS](https://img.shields.io/badge/RAGAS-6E40C9?style=flat-square&logoColor=white)
![LangSmith](https://img.shields.io/badge/LangSmith-1C3C3C?style=flat-square&logoColor=white)

**Production Stack**

![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Kafka](https://img.shields.io/badge/Kafka-231F20?style=flat-square&logo=apachekafka&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonaws&logoColor=white)

<div align="center">

[![Skills](https://skillicons.dev/icons?i=python,pytorch,sklearn,fastapi,docker,kubernetes,kafka,redis,aws,git,linux,github&theme=dark&perline=12)](https://skillicons.dev)

</div>

---

## Featured Projects

### AEGIS-AT — Attribution Integrity Benchmark for Multi-Agent AI

<img align="right" src="https://media.giphy.com/media/077i6AULCXc0FKTj9s/giphy.gif" width="180" />

🔗 **Repository:** https://github.com/rahulsingh1397/aegis-at · Tags: `v1.0.0`, `v2.0.0`

A red-team benchmark measuring whether **audit attribution survives delegation**
in multi-agent AI systems. **v1 headline:** adding the industry-standard
delegation mechanism (RFC 8693) makes attribution *worse* — the log names the
**requester**, not the **executor**. **v2 headline:** sender-constrained tokens
(DPoP, RFC 9449) recover attribution to 1.0 — the standardized fix v1 named is
now measured and works.

**Why this research matters.** NIST's NCCoE (Feb 2026) named auditing and
non-repudiation of AI agents as an open problem; the CSA's confused-deputy
research note (Mar 2026) warns that when an action runs under a trusted agent's
identity, audit logs "look legitimate and delay detection." AEGIS-AT measures
exactly that gap — and demonstrates the standardized layer that closes it.

**The finding — a non-monotonic attribution curve (v2, on both topologies):**

| Baseline | Defense in place | AIS |
|---|---|---|
| B1 | Shared service account | 0.0 |
| B2 | Per-agent identity | 1.0 |
| B3 | + RFC 8693 delegation | 0.0 |
| B4 | + tamper-evident log (real hash chain, LIS = 1.0) | 0.0 |
| **B5** | **+ DPoP sender-constraint** | **1.0** |

Attribution is perfect under per-agent identity (B2), **regresses to zero** when
signed delegation is added (B3), **stays at zero** under tamper-evident logging
(B4) — and **recovers to 1.0** under DPoP-bound tokens (B5). A new **Log
Integrity Score** shows B4 is tamper-proof (LIS = 1.0) yet still mis-attributing
(AIS = 0.0) — a cryptographically perfect record of the wrong actor.

**Approach & rigor**

- Minimal SOC pipeline — five config-flag baselines over **one** codebase
- Two topologies (T1: 2-agent, T2: 3-agent linear chain) — the gap does **not** heal with depth
- Process-boundary ground-truth recorder (`os.getpid()` — unspoofable by an in-process rename)
- Stochastic Bernoulli(p) policy with Wilson 95% intervals and adaptive sample sizes
- Pre-registration **mechanized**: SHA-256-locked threat model + CI gate (any edit fails the build)
- **133 tests** (74 v2 + 59 frozen v1); fully reproducible

`Python` `RFC 8693 / OAuth` `RFC 9449 / DPoP` `PyJWT` `cryptography` `pytest` `Threat Modeling`

<br clear="right"/>

---

### MITRE-Core v2 — Attack Campaign Correlation Engine

<img align="right" src="https://media.giphy.com/media/RDZo7znAdn2u7sAcWH/giphy.gif" width="190" />

🔗 **Repository:** https://github.com/rahulsingh1397/Mitre-Core_v2

Graph-based cybersecurity correlation engine that clusters SOC/SIEM alerts into MITRE ATT&CK-aligned attack campaigns.

**Why this research matters.** Security analysts receive thousands of fragmented
alerts daily. Most correlation systems depend on labeled attack campaigns, which
are expensive and often unavailable in real SOC environments. MITRE-Core v2
explores whether heterogeneous GNNs can cluster attack activity without labels at
inference time, while staying robust across telemetry domains.

**Architecture**

```text
Raw Alerts → AlertToGraphConverter → MITREHeteroGNN (HeteroGATConv)
           → Soft-ZCA Whitening → GAEC Clustering (HDBSCAN · Spectral · BGMM)
           → Campaign Clusters + ATT&CK Mapping
```

**Core technical contributions**

- Heterogeneous graph modeling with 8 node types and 29 edge relations
- 6-dim alert features projected into 128-dim embedding space
- Geometry-Aware Embedding Confidence (GAEC)
- Soft-ZCA whitening to mitigate representation collapse
- Full-batch embedding inference for stable clustering

**Selected findings**

| Finding | Result |
|---|---|
| Full-batch inference | Restored clustering separability after inference correction |
| 6-dim alert features | Stable cosine similarity ~0.73 (no collapse) |
| ZCA whitening | Recovered clustering structure on sparse SIEM datasets |
| Union-Find refinement | Disabled after net-negative evaluation across datasets |

`PyTorch Geometric` `HDBSCAN` `Spectral Clustering` `Docker`

<br clear="right"/>

---

## Verified Benchmark Results — MITRE-Core v2 (Apr 2026)

All results reproduced using fixed seeds and full-dataset inference. Canonical checkpoint: `network_v9_v3`.

| Dataset | Domain | Zero-Shot ARI | Best ARI | Best Mode |
|---|---|---|---|---|
| DARPA OpTC | Host telemetry | **0.979** *(binary setup)* | 0.979 | Zero-shot |
| NSL-KDD | Network IDS | **0.739** | 0.739 | Zero-shot |
| TON_IoT | IoT Network | 0.431 | **0.845** | Supervised |
| UNSW-NB15 | Enterprise network | **0.401** | **0.538** | SupCon |
| CICIDS2017 | Enterprise IDS | **0.284** | 0.284 | Zero-shot |
| SQTK_SIEM | SIEM / SOC alerts | **0.184** | 0.184 | Zero-shot |

- Zero-shot inference uses clustering without campaign labels at inference time
- Supervised mode uses prototype classification in embedding space
- Metrics verified Apr 25, 2026

---

### RL Logon Anomaly Detection — Adaptive Threshold Engine

🔗 **Repository:** https://github.com/rahulsingh1397/Reinforcement_learning_AnomalyDetection

Behavioral anomaly detection that adapts user-level thresholds using analyst feedback loops.

- Reinforcement-learning-based threshold adaptation
- Identity-specific behavioral profiling
- SIEM-ready structured outputs

`Python` `Reinforcement Learning` `Pandas`

---

### Enterprise AI Knowledge Agent — Production RAG System

Production RAG pipeline and ReAct agent supporting regulated enterprise workflows across large-scale document environments.

- Hybrid retrieval (BM25 + dense + RRF), cross-encoder re-ranking
- Presidio + RBAC governance layer
- Continuous evaluation (RAGAS, LangSmith); audit logging + compliance checks

**Operational metrics:** Recall@5 0.68 → 0.91 · 2K–5K daily queries · P99 latency 1.45s · zero reported compliance incidents

`LangChain` `FAISS` `FastAPI` `Docker`

---

### Enterprise LLM Security Auditor

<img align="right" src="https://media.giphy.com/media/3o7aCSPqXE5C6T8tBC/giphy.gif" width="170" />

🔗 **Repository:** https://github.com/rahulsingh1397/Enterprise_LLM_Security_Auditor

Evaluation harness for measuring vulnerability exposure in production LLM deployments.

- Coverage: prompt injection, jailbreaks, PII leakage, data exfiltration, RAG poisoning, system-prompt extraction
- 61 adversarial evaluation tests; semantic vulnerability evaluation
- Automated PDF audit generation; end-to-end audits in 5–10 minutes

`FastAPI` `React` `Docker`

<br clear="right"/>

---

### AI Compliance Monitor

<img align="right" src="https://media.giphy.com/media/du3J3cXyzhj75IOgvA/giphy.gif" width="170" />

🔗 **Repository:** https://github.com/rahulsingh1397/AI_Compliance_Monitor

Event-driven ML governance system for monitoring production AI behavior and generating audit evidence.

- Isolation Forest + Autoencoder monitoring; differential privacy support
- SOC2 / GDPR / HIPAA export pipelines; native enterprise-tool integrations

`FastAPI` `Kafka` `Docker` `QRadar`

<br clear="right"/>

---

## Active Research

| Research Area | Status | Details |
|---|---|---|
| AEGIS-AT v2 | ✅ Shipped | Real B4 hash-chain + LIS; DPoP Baseline 5 (AIS → 1.0); 3-agent T2 topology; Wilson 95% CIs; threat-model SHA-256-locked. Tag `v2.0.0`. |
| AEGIS-AT v3 | 📋 Planned | mTLS Baseline 5b (RFC 8705); fan-in + cross-org topologies; LLM-in-the-loop adapter; real-telemetry attack distributions |
| SupCon fine-tuning | ✅ Verified | Improved UNSW-NB15 clustering stability |
| ZCA whitening for SIEM | ✅ Verified | Improved sparse embedding separability |
| Multi-domain training | 📋 Planned | Expansion across additional telemetry domains |
| GAEC arXiv preprint | ✍️ Drafting | Full methodology and ablation analysis |

---

## GitHub Stats

<div align="center">

<img height="165" src="https://github-readme-stats.vercel.app/api?username=rahulsingh1397&show_icons=true&hide_border=true&title_color=00F5D4&icon_color=00F5D4&text_color=c9d1d9&bg_color=0a0a0a" />
<img height="165" src="https://github-readme-stats.vercel.app/api/top-langs/?username=rahulsingh1397&layout=compact&hide_border=true&title_color=00F5D4&text_color=c9d1d9&bg_color=0a0a0a" />

<br/><br/>

![GitHub Streak](https://streak-stats.demolab.com?user=rahulsingh1397&theme=dark&hide_border=true&ring=00F5D4&fire=00F5D4&currStreakLabel=00F5D4&background=0a0a0a)

<br/><br/>

![Trophies](https://github-profile-trophy.vercel.app/?username=rahulsingh1397&theme=onedark&no-frame=true&column=7&margin-w=4&title_color=00F5D4)

<br/><br/>

![GitHub Activity Graph](https://github-readme-activity-graph.vercel.app/graph?username=rahulsingh1397&bg_color=050816&color=22d3ee&line=06b6d4&point=67e8f9&area_color=164e63&area=true&hide_border=true&radius=10)

</div>

---

<div align="center">

> Building reliable, production-oriented AI systems — and the benchmarks that test whether they hold.

**Stevens Institute of Technology · MS Information Systems**

Open to: AI/ML Engineer · AI Safety Researcher · Applied ML Researcher · LLM Systems Engineer

</div>
