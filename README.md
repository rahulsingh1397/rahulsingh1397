<div align="center">

# Rahul Singh

**AI/ML Engineer · AI Safety & Agent Security Researcher**

I build production ML systems — and the adversarial benchmarks that test whether they actually hold up.

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=20&pause=1200&color=00F5D4&center=true&vCenter=true&width=820&lines=Multi-Agent+Security+%7C+Attribution+%7C+Non-Repudiation;Graph+Neural+Networks+%7C+Heterogeneous+Graphs;LLM+Pipelines+%7C+RAG+%7C+Evaluation+Harnesses;Pre-registered%2C+Reproducible+Research" alt="Rotating taglines: multi-agent security, graph neural networks, LLM pipelines, reproducible research" />

<br/>

<a href="https://rahulaiportfolio.netlify.app/">
  <img src="https://img.shields.io/badge/🌐_Portfolio-rahulaiportfolio.netlify.app-00F5D4?style=for-the-badge" alt="Portfolio website" />
</a>
<a href="mailto:rahul.rs1397@gmail.com">
  <img src="https://img.shields.io/badge/📩_Email-Contact-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email contact" />
</a>
<a href="https://linkedin.com/in/rahulsingh1397">
  <img src="https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn profile" />
</a>
<a href="https://github.com/sponsors/rahulsingh1397">
  <img src="https://img.shields.io/badge/❤️_Sponsor-Fund_My_Work-EA4AAA?style=for-the-badge&logo=githubsponsors&logoColor=white" alt="GitHub Sponsors" />
</a>

</div>

> [!NOTE]
> **Just shipped — [AEGIS-AT `v2.0.0`](https://github.com/rahulsingh1397/AEGIS-AT):** sender-constrained tokens (DPoP, RFC 9449) recover multi-agent audit attribution to 100% — the standardized fix that v1 identified is now measured, pre-registered, and reproducible.

---

## What I do

- **AI Safety & Agent Security** — when an AI agent takes a consequential action, can you prove *which* agent did it? I build red-team benchmarks that answer this with measurements, not assumptions.
- **Graph ML for cybersecurity** — heterogeneous graph neural networks that cluster thousands of raw security alerts into coherent attack campaigns, without needing labeled data.
- **LLM systems in production** — retrieval-augmented pipelines, agents, and the evaluation harnesses that keep them honest, in regulated enterprise environments.

Every project below follows the same discipline: **state the prediction before writing the code, lock it, then report whatever the measurement shows.**

---

## 🛡️ Flagship: AEGIS-AT — Attribution Integrity Benchmark

🔗 [`github.com/rahulsingh1397/AEGIS-AT`](https://github.com/rahulsingh1397/AEGIS-AT) · releases [`v1.0.0`](https://github.com/rahulsingh1397/AEGIS-AT/releases/tag/v1.0.0) · [`v2.0.0`](https://github.com/rahulsingh1397/AEGIS-AT/releases/tag/v2.0.0)

**In one sentence:** when AI agents delegate work to each other, the audit log can end up naming the *wrong agent* — this benchmark measures exactly when that happens, and proves which defense fixes it.

**Why it matters (no jargon):** imagine a hospital's automated security system where a low-privilege "triage" agent asks a high-privilege "containment" agent to quarantine a machine. Afterward, the log should say who did it. Under the *industry-standard* delegation protocol, the log names the agent that *asked* — not the one that *acted*. An attacker can exploit that to hide who really took a dangerous action. NIST flagged this exact accountability question as an open problem in Feb 2026.

**The measured result — attribution score (1.0 = perfect, 0.0 = always wrong):**

| Defense configuration | What it adds | Score |
|---|---|:---:|
| B1 — shared service account | nothing (the common default) | 0.0 |
| B2 — per-agent identity | each agent gets its own credential | **1.0** ✅ |
| B3 — + RFC 8693 delegation | the standards-recommended protocol | 0.0 ⚠️ |
| B4 — + tamper-evident log | cryptographic log protection | 0.0 ⚠️ |
| **B5 — + DPoP sender-constraint** | **token bound to its true holder** | **1.0** ✅ |

The counter-intuitive headline: **adding the recommended delegation standard makes attribution *worse*** (B2 → B3), tamper-proofing can't fix it (B4 protects a *wrong* record perfectly), and only binding tokens to their holders (B5) restores accountability.

<details>
<summary><b>🔬 Technical depth — methodology & rigor</b> (click to expand)</summary>
<br/>

- **Five baselines as config flags over one codebase** — score differences are attributable to the defense, never to incidental implementation differences
- **Two topologies** (2-agent and 3-agent delegation chains) — the gap does **not** heal with chain depth; the deeper chain just names a different non-executor
- **Process-boundary ground truth** — the recorder reads the executing agent's OS process identity (`os.getpid()` via a kernel-side PID registry); an agent that renames its thread or process title cannot spoof it
- **Log Integrity Score (LIS)** — a second metric proving B4 is simultaneously tamper-proof (LIS = 1.0) and mis-attributing (AIS = 0.0): a cryptographically perfect record of the wrong actor
- **Stochastic sweep** — Bernoulli(p) attack frequency across p ∈ {0.1, 0.5, 0.9} with Wilson 95% intervals and adaptive sample-size escalation; the curve shape is invariant to attack frequency, confirming the failure is structural
- **Mechanized pre-registration** — the threat model is SHA-256-locked with a CI gate; *any* edit to the predictions fails the build. Contradicted predictions get reported, not reconciled
- **133 tests** (74 v2 + 59 frozen v1), fully deterministic, reproduces in seconds; all paper figures regenerate from the live harness
- **DPoP (RFC 9449) implemented by hand** — Ed25519 proof-of-possession keys, RFC 7638 thumbprints, replay cache, freshness windows

`Python` `RFC 8693 / OAuth` `RFC 9449 / DPoP` `PyJWT` `cryptography` `pytest` `Threat Modeling`

</details>

---

## 🕸️ Flagship: MITRE-Core v2 — Attack Campaign Correlation

🔗 [`github.com/rahulsingh1397/Mitre-Core_v2`](https://github.com/rahulsingh1397/Mitre-Core_v2)

**In one sentence:** security teams drown in thousands of disconnected alerts — this engine uses graph neural networks to group them into coherent attack campaigns, without needing labeled examples.

**Why it matters (no jargon):** a real intrusion shows up as dozens of small alerts scattered across systems. Connecting them by hand is slow; most automated tools need labeled past attacks to learn from, which real security teams rarely have. MITRE-Core clusters attack activity *without* labels at detection time, and maps the result onto the MITRE ATT&CK framework analysts already use.

```text
Raw Alerts → Graph Converter → Heterogeneous GNN (HeteroGATConv)
           → Soft-ZCA Whitening → GAEC Clustering (HDBSCAN · Spectral · BGMM)
           → Campaign Clusters + ATT&CK Mapping
```

<details>
<summary><b>🔬 Technical depth — architecture & verified benchmarks</b> (click to expand)</summary>
<br/>

**Core technical contributions**

- Heterogeneous graph modeling: 8 node types, 29 edge relations
- 6-dim alert features projected into a 128-dim embedding space
- Geometry-Aware Embedding Confidence (GAEC) for cluster-quality estimation
- Soft-ZCA whitening to mitigate representation collapse on sparse data
- Full-batch embedding inference for stable clustering

**Verified benchmark results (Apr 25, 2026 · fixed seeds · canonical checkpoint `network_v9_v3`)**

| Dataset | Domain | Zero-Shot ARI | Best ARI | Best Mode |
|---|---|:---:|:---:|---|
| DARPA OpTC | Host telemetry | **0.979** *(binary)* | 0.979 | Zero-shot |
| NSL-KDD | Network IDS | **0.739** | 0.739 | Zero-shot |
| TON_IoT | IoT network | 0.431 | **0.845** | Supervised |
| UNSW-NB15 | Enterprise network | **0.401** | **0.538** | SupCon |
| CICIDS2017 | Enterprise IDS | **0.284** | 0.284 | Zero-shot |
| SQTK_SIEM | SIEM / SOC alerts | **0.184** | 0.184 | Zero-shot |

*Zero-shot = clustering without campaign labels at inference. Negative results kept: Union-Find refinement was disabled after net-negative evaluation across datasets.*

`PyTorch Geometric` `HDBSCAN` `Spectral Clustering` `Docker`

</details>

---

## 📦 More projects

| Project | What it does | Stack | Link |
|---|---|---|---|
| **Enterprise LLM Security Auditor** | 61-test adversarial harness for production LLMs — prompt injection, jailbreaks, PII leakage, RAG poisoning; automated PDF audits in 5–10 min | FastAPI · React · Docker | [repo](https://github.com/rahulsingh1397/Enterprise_LLM_Security_Auditor) |
| **AI Compliance Monitor** | Event-driven ML governance — anomaly monitoring + SOC2/GDPR/HIPAA audit-evidence pipelines | FastAPI · Kafka · QRadar | [repo](https://github.com/rahulsingh1397/AI_Compliance_Monitor) |
| **RL Logon Anomaly Detection** | Behavioral anomaly detection with analyst-feedback threshold adaptation; SIEM-ready outputs | Python · RL · Pandas | [repo](https://github.com/rahulsingh1397/Reinforcement_learning_AnomalyDetection) |
| **Enterprise AI Knowledge Agent** | Production RAG + ReAct agent for regulated workflows — Recall@5 0.68 → 0.91, P99 1.45s, 2–5K queries/day, zero compliance incidents | LangChain · FAISS · FastAPI | *proprietary* |

---

## 🔭 Research status

| Area | Status | Details |
|---|:---:|---|
| AEGIS-AT v2 | ✅ Shipped | DPoP Baseline 5 (AIS → 1.0) · real hash-chain + LIS · 3-agent topology · Wilson CIs · SHA-256-locked threat model · tag `v2.0.0` |
| AEGIS-AT v3 | 📋 Planned | mTLS Baseline 5b (RFC 8705) · fan-in + cross-org topologies · LLM-in-the-loop adapter · real-telemetry attack distributions |
| GAEC arXiv preprint | ✍️ Drafting | Full methodology + ablation analysis |
| SupCon fine-tuning | ✅ Verified | Improved UNSW-NB15 clustering stability |
| ZCA whitening for SIEM | ✅ Verified | Improved sparse-embedding separability |
| Multi-domain training | 📋 Planned | Expansion across additional telemetry domains |

---

## 🧰 Stack

<div align="center">

[![Core tooling](https://skillicons.dev/icons?i=python,pytorch,sklearn,fastapi,docker,kubernetes,kafka,redis,aws,git,linux,github&theme=dark&perline=12)](https://skillicons.dev)

</div>

**Specialist tooling** &nbsp;
![PyTorch Geometric](https://img.shields.io/badge/PyTorch_Geometric-3C2179?style=flat-square&logo=pytorch&logoColor=white)
![HDBSCAN](https://img.shields.io/badge/HDBSCAN-1D9E75?style=flat-square&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![FAISS](https://img.shields.io/badge/FAISS-0467DF?style=flat-square&logo=meta&logoColor=white)
![RAGAS](https://img.shields.io/badge/RAGAS-6E40C9?style=flat-square&logoColor=white)
![LangSmith](https://img.shields.io/badge/LangSmith-1C3C3C?style=flat-square&logoColor=white)

**Security & standards** &nbsp;
![RFC 8693 / OAuth](https://img.shields.io/badge/RFC_8693_/_OAuth-2C2255?style=flat-square&logo=auth0&logoColor=white)
![RFC 9449 / DPoP](https://img.shields.io/badge/RFC_9449_/_DPoP-1B5E20?style=flat-square&logo=auth0&logoColor=white)
![PyJWT](https://img.shields.io/badge/PyJWT-000000?style=flat-square&logo=jsonwebtokens&logoColor=white)
![Threat Modeling](https://img.shields.io/badge/Threat_Modeling-8A1538?style=flat-square&logo=hackthebox&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white)

---

## ⚡ Activity

<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/rahulsingh1397/rahulsingh1397/output/github-snake-dark.svg" />
  <img alt="Snake animation eating my GitHub contribution graph" src="https://raw.githubusercontent.com/rahulsingh1397/rahulsingh1397/output/github-snake.svg" />
</picture>

<br/><br/>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-activity-graph.vercel.app/graph?username=rahulsingh1397&bg_color=050816&color=22d3ee&line=06b6d4&point=67e8f9&area_color=164e63&area=true&hide_border=true&radius=10" />
  <img alt="GitHub contribution activity graph" src="https://github-readme-activity-graph.vercel.app/graph?username=rahulsingh1397&bg_color=ffffff&color=0d9488&line=0d9488&point=0f766e&area_color=ccfbf1&area=true&hide_border=true&radius=10" />
</picture>

</div>

---

<div align="center">

> *Building reliable, production-oriented AI systems — and the benchmarks that test whether they hold.*

**Stevens Institute of Technology · MS Information Systems**

Open to: **AI/ML Engineer · AI Safety Researcher · Applied ML Researcher · LLM Systems Engineer**

<img src="https://capsule-render.vercel.app/api?type=waving&height=110&section=footer&color=0:0d9488,50:00F5D4,100:0d9488&animation=fadeIn" width="100%" alt="" />

</div>
