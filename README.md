<div align="center">

# Rahul Singh

**AI/ML Engineer · AI Safety & Agent Security Researcher**

I build production ML systems — and the adversarial benchmarks that test whether they actually hold up.

**Multi-Agent Security · Attribution · Non-Repudiation&nbsp;|&nbsp;Graph Neural Networks&nbsp;|&nbsp;LLM Pipelines · RAG · Evaluation&nbsp;|&nbsp;Pre-registered, Reproducible Research**

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

</div>

> [!NOTE]
> **Just shipped — [AEGIS-AT `v3.0.0`](https://github.com/rahulsingh1397/aegis-at):** the completion-record protocols arriving in 2026 (AIP / PEDIGREE / HDP) default to trusting an agent's *self-reported* account of what it did — so I put **four real open-weight LLMs** in the executor seat and showed they forge that self-report ~90–100% of the time under prompt injection, while an independent verifier drives it to **zero**. Pre-registered, reproducible, and archived on Zenodo ([`10.5281/zenodo.20693303`](https://doi.org/10.5281/zenodo.20693303)).

---

## What I do

- **AI Safety & Agent Security** — when an AI agent takes a consequential action, can you prove *which* agent did it? I build red-team benchmarks that answer this with measurements, not assumptions — including whether a real LLM can be induced to lie about its own actions.
- **Graph ML for cybersecurity** — heterogeneous graph neural networks that cluster thousands of raw security alerts into coherent attack campaigns, without needing labeled data.
- **LLM systems in production** — retrieval-augmented pipelines, agents, and the evaluation harnesses that keep them honest, in regulated enterprise environments.

Every project below follows the same discipline: **state the prediction before writing the code, lock it, then report whatever the measurement shows.**

---

## 🛡️ Flagship: AEGIS-AT — Attribution Integrity Benchmark

🔗 [`github.com/rahulsingh1397/aegis-at`](https://github.com/rahulsingh1397/aegis-at) · releases [`v1.0.0`](https://github.com/rahulsingh1397/aegis-at/releases/tag/v1.0.0) · [`v2.0.0`](https://github.com/rahulsingh1397/aegis-at/releases/tag/v2.0.0) · [`v3.0.0`](https://github.com/rahulsingh1397/aegis-at/releases/tag/v3.0.0) · [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20693303.svg)](https://doi.org/10.5281/zenodo.20693303)

**In one sentence:** when AI agents delegate work to each other, the audit log can end up naming the *wrong agent* — this benchmark measures exactly when that happens, and proves which defense actually fixes it, from OAuth delegation up to the completion-record protocols shipping in 2026.

**Why it matters (no jargon):** imagine a hospital's automated security system where a low-privilege "triage" agent asks a high-privilege "containment" agent to quarantine a machine. Afterward, the log should say who did it. Under the *industry-standard* delegation protocol, the log names the agent that *asked* — not the one that *acted*. An attacker can exploit that to hide who really took a dangerous action. NIST flagged this exact accountability question as an open problem in Feb 2026.

**v3's escalation (2026):** the newest agent-identity proposals let agents file their *own* "completion record" — a signed note saying what they did. Trusting that self-report collapses the moment the agent lies — and v3 puts **four real open-weight LLMs** in the seat to prove they *do* lie (forging the record ~90–100% of the time under prompt injection), while an independent verifier nulls every attempt.

**The measured result — attribution score (1.0 = perfect, 0.0 = always wrong):**

| Defense configuration | What it adds | Score |
|---|---|:---:|
| B1 — shared service account | nothing (the common default) | 0.0 |
| B2 — per-agent identity | each agent gets its own credential | **1.0** ✅ |
| B3 — + RFC 8693 delegation | the standards-recommended protocol | 0.0 ⚠️ |
| B4 — + tamper-evident log | cryptographic log protection | 0.0 ⚠️ |
| B5 — + DPoP sender-constraint | token bound to its true holder | **1.0** ✅ |
| B6 — + mTLS (RFC 8705) | certificate-bound token | **1.0** ✅ |
| B7 — + A-JWT execution assertion | per-agent proof-of-possession | **1.0** ✅ |
| B8 — + self-reported completion | trust the agent's own report | **0.0** ⚠️ *(collapses under a lying agent)* |
| B9 — + tool-verified completion | an independent observer confirms it | **1.0** ✅ |

The counter-intuitive headline: **adding the recommended delegation standard makes attribution *worse*** (B2 → B3), tamper-proofing can't fix it (B4 protects a *wrong* record perfectly), and accountability is restored only by *verifying the executor at execution* — DPoP, mTLS, A-JWT, or an independent verifier (B5–B7, B9). The 2026 completion-record default (B8) trusts self-report and fails under collusion — where, in v3, the colluder is a **real LLM**.

<details>
<summary><b>🔬 Technical depth — methodology & rigor</b> (click to expand)</summary>
<br/>

- **Nine baselines as config flags over one codebase** — score differences are attributable to the defense, never to incidental implementation differences; v3 *imports* v2's code rather than forking it
- **Real-model LLM tier** — four open-weight models (Llama-3.1-8B → Llama-3.3-70B → GPT-OSS-20B → GPT-OSS-120B) placed in the executor seat and induced by prompt injection on a structured tool-call argument; **B8 forging 90–100%, B9 evasion 0** across every model, summarized as evasion rates with Wilson 95% intervals against a locked hypothesis set (H1–H4)
- **Honest reporting** — the pre-registered capability curve (H1) came back *flat* and is reported as a finding under a disclosed forced-call confound, **not coded around**; the deterministic B9 result is framed as a structural control, not oversold as an empirical surprise
- **Process-boundary ground truth** — the recorder reads the executing agent's OS process identity (`os.getpid()` via a kernel-side PID registry); an agent that renames its thread or process title cannot spoof it
- **Two topologies** (2-agent and 3-agent delegation chains) — the gap does **not** heal with chain depth; the deeper chain just names a different non-executor
- **Log Integrity Score (LIS)** — a second metric proving B4 is simultaneously tamper-proof (LIS = 1.0) and mis-attributing (AIS = 0.0): a cryptographically perfect record of the wrong actor
- **Two-stage mechanized pre-registration** — deterministic core + LLM-tier parameters, each SHA-256-locked with a CI gate; *any* edit to the predictions fails the build. Every domain claim (RFC 8693/8705/9449, AIP, PEDIGREE, HDP, MCP, A-JWT) is verified at primary source, contradictions reported rather than reconciled
- **283 tests across three versions** (150 v3 + 74 v2 + 59 frozen v1) — the deterministic core reproduces in seconds with no API key; all paper figures regenerate from the live harness
- **Standards implemented by hand** — DPoP (RFC 9449: Ed25519 PoP + RFC 7638 thumbprints + replay cache + freshness windows), mTLS certificate binding (RFC 8705), A-JWT execution assertions, over an MCP-shaped transport boundary
- **Archived + citable** — three peer-style papers (v1 17 pp · v2 14 pp · v3 17 pp) and a Zenodo deposit under concept DOI [`10.5281/zenodo.20693303`](https://doi.org/10.5281/zenodo.20693303)

`Python` `RFC 8693 / OAuth` `RFC 9449 / DPoP` `RFC 8705 / mTLS` `A-JWT` `MCP` `LLM red-teaming` `Groq` `PyJWT` `cryptography` `pytest` `Threat Modeling`

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
![Groq](https://img.shields.io/badge/Groq-F55036?style=flat-square&logoColor=white)

**Security & standards** &nbsp;
![RFC 8693 / OAuth](https://img.shields.io/badge/RFC_8693_/_OAuth-2C2255?style=flat-square&logo=auth0&logoColor=white)
![RFC 9449 / DPoP](https://img.shields.io/badge/RFC_9449_/_DPoP-1B5E20?style=flat-square&logo=auth0&logoColor=white)
![RFC 8705 / mTLS](https://img.shields.io/badge/RFC_8705_/_mTLS-0B3D2E?style=flat-square&logo=auth0&logoColor=white)
![MCP](https://img.shields.io/badge/MCP-000000?style=flat-square&logoColor=white)
![PyJWT](https://img.shields.io/badge/PyJWT-000000?style=flat-square&logo=jsonwebtokens&logoColor=white)
![Threat Modeling](https://img.shields.io/badge/Threat_Modeling-8A1538?style=flat-square&logo=hackthebox&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white)

---

<div align="center">

> *Building reliable, production-oriented AI systems — and the benchmarks that test whether they hold.*

**Stevens Institute of Technology · MS Information Systems**

Open to: **AI/ML Engineer · AI Safety Researcher · Applied ML Researcher · LLM Systems Engineer**

</div>
