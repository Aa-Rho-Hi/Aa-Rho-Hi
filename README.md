# Aarohi Mohrir

**Cybersecurity Engineer · M.S. Computer Science, Texas A&M University**

I build security systems end to end — detection engineering, threat exposure management, ML-based malware detection, and production AI applications with security hardening built in. Currently seeking cybersecurity internship and full-time roles in cloud security, AI security, SOC operations, and infrastructure security.

[![Email](https://img.shields.io/badge/Email-aarohi0402%40gmail.com-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:aarohi0402@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-Aa--Rho--Hi-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/Aa-Rho-Hi)

---

## Featured Projects

### 🔴 EIRA — Production RAG Chatbot for Texas A&M ECE — **[Live](https://ecen-chatbot-199137295144.us-central1.run.app)**

**Repo:** [ECEN-Chatbot](https://github.com/Aa-Rho-Hi/ECEN-Chatbot) · **Stack:** FastAPI, Next.js 15, Supabase pgvector, OpenAI, GCP Cloud Run

- **Situation:** The Texas A&M ECE department's information (programs, courses, faculty, research, admissions) was scattered across hundreds of web pages, making answers hard to find for students and visitors.
- **Task:** Build and deploy a production-grade, secure RAG chatbot grounded in the department's official website, under the guidance of Prof. Krishna Narayanan.
- **Action:** Designed a full pipeline — BFS site crawler with PII scrubbing and data-poisoning guards, hybrid retrieval (pgvector HNSW dense search + BM25 + RRF fusion + cross-encoder re-ranking), an LLM intent router, and a faculty knowledge graph. Hardened it with per-IP rate limiting, layered prompt-injection defense, mid-stream secret redaction, citation relevance gates, and structured audit logging. Deployed on Cloud Run with CI via Cloud Build and nightly automated re-indexing.
- **Result:** A live public service answering department questions with grounded citations and an honest "couldn't find that" instead of hallucinations — security-screened at every layer from ingestion to output. **Try it: [ecen-chatbot-199137295144.us-central1.run.app](https://ecen-chatbot-199137295144.us-central1.run.app)**

### 🛡️ ATLAS-CTEM — Continuous Threat Exposure Management Platform

**Repo:** [CTEM](https://github.com/Aa-Rho-Hi/CTEM) · **Stack:** FastAPI (async), PostgreSQL, Celery/Redis, Neo4j/NetworkX, Next.js 16, Docker, Kubernetes

- **Situation:** Vulnerability data from scanners (Nessus, Qualys, Burp, Snyk, and others) arrives in incompatible formats with no shared notion of business risk, leaving teams to prioritize by raw CVSS alone.
- **Task:** Build an enterprise-grade, multi-tenant platform unifying vulnerability discovery, risk prioritization, attack-path analysis, compliance, and remediation in one workflow.
- **Action:** Implemented ingestion parsers for 10+ scanner formats; a composite risk engine combining CVSS, EPSS, KEV status, network exposure, and business impact; NetworkX attack-graph analysis for lateral-movement paths and choke points; CWE-to-control mapping across 10 compliance frameworks (NIST CSF 2.0, PCI-DSS 4.0, HIPAA, ISO 27001, SOC 2, and more); and an LLM agent framework with tool whitelists, risk ceilings, a Redis-backed fail-closed kill switch, and immutable audit trails. Added six-role RBAC with database-level tenant isolation and a 50+ file pytest suite.
- **Result:** A deployable platform (Docker Compose + Kubernetes manifests, Swagger/ReDoc API docs) that turns raw scan output into context-ranked, compliance-mapped, approval-gated remediation — with an accompanying IEEE-format paper.

### 🧬 DAFCS — Malware Detection on EMBER2024 (Beat the Published Baseline)

**Repo:** [DAFCS](https://github.com/Aa-Rho-Hi/DAFCS) · **Stack:** Python, LightGBM, PyTorch, contrastive learning

- **Situation:** The EMBER2024 benchmark includes a challenge set of 6,315 evasive malware samples engineered to evade detection; the published baseline catches only 66.5% of them.
- **Task:** Benchmark and beat the official EMBER2024 paper baseline on malware detection and family classification across 2.6M+ training samples.
- **Action:** Trained per-file-type LightGBM specialist models, grid-searched ensemble weights over 1,200 combinations, and designed a novel rank-based (Borda count) ensemble with power sharpening that eliminates cross-model score-scale bias. Built a parallel PyTorch pipeline with supervised contrastive pre-training, multi-task fine-tuning, and prototypical inference for long-tail malware families.
- **Result:** Beat the paper baseline on **all four metrics** (test ROC-AUC 0.9976, challenge PR-AUC +0.156); the novel rank ensemble raised evasive-malware detection from **66.5% → 97.86%** (+31.3 pp).

### 🔍 ShadowProbe — Autonomous Vulnerability Discovery Pipeline

**Repo:** [ShadowProbe](https://github.com/Aa-Rho-Hi/ShadowProbe) · **Stack:** Python, Bandit, Semgrep, LLM reasoning

- **Situation:** Static analyzers flood developers with findings that lack semantic context, exploitability assessment, and prioritization.
- **Task:** Design a research-grade system that takes a repository URL and autonomously produces a prioritized, contextual vulnerability report.
- **Action:** Architected a hybrid pipeline — repo acquisition, Bandit + Semgrep static analysis, LLM-based semantic reasoning over suspicious code segments, exploit-path simulation, contextual risk scoring, and JSON/Markdown report generation — with clean module boundaries per stage.
- **Result:** Working pipeline skeleton with full architecture in place; active development toward end-to-end automated triage.

### 🧩 OWASP Risk Intelligence — VS Code Security Extension

**Repo:** [owasp-risk-intelligence](https://github.com/Aa-Rho-Hi/owasp-risk-intelligence) · **Stack:** TypeScript, VS Code Extension API, esbuild

- **Situation:** Developers usually learn about OWASP Top 10 issues at review or scan time — long after the insecure pattern was written.
- **Task:** Surface vulnerability detection and risk scoring directly in the editor, at the moment code is written.
- **Action:** Built a static-analysis engine detecting SQL injection, XSS, command injection, `eval()` use, weak hashing (MD5/SHA1), insecure randomness, hardcoded secrets, and HTTP misuse — each scored with a weighted exploitability/impact model (Risk = E×0.6 + I×0.4) and rendered as inline highlights with hover explanations.
- **Result:** A working shift-left security tool that gives per-finding severity, per-file average risk, and educational context inside the SSDLC's earliest stage.

### 🤖 Claude-FPR — LLM-Assisted False-Positive Reduction *(in progress)*

**Repo:** [Claude-FPR](https://github.com/Aa-Rho-Hi/Claude-FPR) · **Stack:** Python

Active research applying LLM reasoning to reduce false positives in security alert triage. Public release in progress — watch the repo.

---

## Also Built

- **Endpoint Detection Lab** — Sigma rules authored and tuned for Windows/Linux telemetry, each mapped to MITRE ATT&CK techniques; full SOC loop of collection → detection → triage → gap analysis
- **AWS Security Fundamentals** — least-privilege IAM policies, CloudWatch alarming, S3 hardening (encryption at rest, public-access blocks, bucket policies)
- **API Security Research** — OWASP API Top 10 validated hands-on against test APIs with documented repro steps and mitigations

## Skills

**Security:** detection engineering (Sigma, MITRE ATT&CK), CTEM & risk modeling, AppSec/OWASP, API security, threat intel, incident response
**Cloud:** AWS (IAM, CloudWatch, S3), GCP (Cloud Run, Cloud Build, Scheduler), Docker, Kubernetes
**Engineering:** Python, TypeScript, FastAPI, Next.js/React, PostgreSQL + pgvector, Celery/Redis, PyTorch, LightGBM
**ML for Security:** RAG pipelines, hybrid retrieval, contrastive learning, ensemble methods, LLM safety hardening

---

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=Aa-Rho-Hi&show_icons=true&hide_border=true" alt="GitHub stats" height="165" />
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Aa-Rho-Hi&layout=compact&hide_border=true" alt="Top languages" height="165" />
</p>
