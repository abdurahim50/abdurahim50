# Hi, I'm Abdurahim Yongho 👋

## DevSecOps · Cloud Security · Minneapolis-St. Paul, MN

![Security+](https://img.shields.io/badge/CompTIA-Security%2B-2ea44f?style=flat-square)
![Network+](https://img.shields.io/badge/CompTIA-Network%2B-2ea44f?style=flat-square)
![AWS Cloud Practitioner](https://img.shields.io/badge/AWS-Cloud%20Practitioner-FF9900?style=flat-square)
![PSM I](https://img.shields.io/badge/Scrum.org-PSM%20I-0b5d8c?style=flat-square)

I build cloud systems where security is part of the delivery path, not a report filed afterwards. A failing scan stops the merge, an unsigned image never reaches production, and every claim in my READMEs links to the evidence behind it.

Cybersecurity student at Metropolitan State University, with an A.S. in Software Application Development and a background in HIPAA-regulated compliance work.

### 🔎 Currently looking for

DevSecOps and cloud security **internships or entry-level roles** where I can help teams ship secure-by-default pipelines and infrastructure.

---

## 📂 Featured projects

| Project | What it is | Technologies | Status |
|---|---|---|---|
| **[MediBook](https://github.com/abdurahim50/medibook)** | Secure patient appointment-booking API on AWS with a signed, policy-gated delivery pipeline | Python · FastAPI · Terraform · ECS Fargate · RDS · GitHub Actions · Cosign · OPA | [![CI](https://github.com/abdurahim50/medibook/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/abdurahim50/medibook/actions/workflows/ci.yml) |

*More projects are being rebuilt to the same evidence-first standard and will be added as they're ready.*

### MediBook in detail

A patient appointment-booking API on AWS, built end to end as a secure delivery exercise on synthetic data. Built across 28 merged pull requests.

- **Pipeline:** 8 required checks on every pull request: tests, SAST, dependency, secret and image scans, policy tests, authenticated DAST and a Terraform plan
- **Supply chain:** keyless Cosign signatures and SBOM attestation, pushed to ECR through GitHub OIDC with no stored AWS keys
- **Deploy gate:** Terraform verifies the image signature during the plan, and Conftest policies block non-compliant infrastructure
- **Data protection:** private, KMS-encrypted RDS PostgreSQL with verified TLS, IAM database auth and a least-privilege app role
- **Recovery:** point-in-time restore drilled and measured at an RTO of 23 min 50 s with no data lost
- **Governance:** controls mapped to NIST SP 800-53 Rev. 5, with a STRIDE threat model and known gaps tracked in the open

```mermaid
flowchart LR
    PR["Pull request"] --> CI{"8 CI checks<br/>tests · SAST · SCA<br/>secrets · Trivy · DAST<br/>policy · TF plan"}
    CI -- fail --> X["Merge blocked"]
    CI -- pass --> M["main"]
    M --> R["Release<br/>build · Trivy · SBOM<br/>Cosign sign"]
    R -- "OIDC, no keys" --> ECR[("Amazon ECR")]
    ECR --> TF{"Terraform plan<br/>verify signature<br/>Conftest policy"}
    TF -- "unsigned or non-compliant" --> X2["Deploy refused"]
    TF -- pass --> AWS["WAF · ALB<br/>ECS Fargate<br/>RDS PostgreSQL"]
```

📄 [Architecture](https://github.com/abdurahim50/medibook/blob/main/docs/architecture.md) · [Threat model](https://github.com/abdurahim50/medibook/blob/main/docs/threat-model.md) · [NIST controls](https://github.com/abdurahim50/medibook/blob/main/docs/controls.md) · [Evidence](https://github.com/abdurahim50/medibook/blob/main/docs/evidence.md) · [Runbook](https://github.com/abdurahim50/medibook/blob/main/docs/runbook.md)

---

## 🎯 Skills mapped to DevSecOps job requirements

| Typical job requirement | Where to see it in MediBook |
|---|---|
| CI/CD with integrated security testing (SAST, SCA, DAST) | [CI workflow](https://github.com/abdurahim50/medibook/blob/main/.github/workflows/ci.yml): Bandit, Semgrep, pip-audit, gitleaks, Trivy, OWASP ZAP |
| Infrastructure as Code on AWS | [Terraform stacks](https://github.com/abdurahim50/medibook/tree/main/infra): VPC, ALB, WAF, ECS Fargate, RDS, CloudWatch |
| Policy as code and compliance | [Conftest policies](https://github.com/abdurahim50/medibook/tree/main/policy) mapped to NIST SP 800-53 |
| Container security | Multi-stage, non-root, read-only image pinned by digest; Trivy gate |
| Software supply-chain security | [Release workflow](https://github.com/abdurahim50/medibook/blob/main/.github/workflows/release.yml): Syft SBOM, Cosign signing, OIDC to ECR |
| IAM and least privilege | Read-only CI plan role, RDS IAM auth, row-access-only database role |
| Threat modeling and secure design | [STRIDE threat model](https://github.com/abdurahim50/medibook/blob/main/docs/threat-model.md) |
| Monitoring, incident response, recovery | [Runbook](https://github.com/abdurahim50/medibook/blob/main/docs/runbook.md) and [recovery drills](https://github.com/abdurahim50/medibook/blob/main/docs/evidence/deployment/recovery-drills.md) |
| Secure application development | FastAPI with argon2id hashing, session revocation, rate limiting, audit logging, security headers |

---

## 🛠️ Tech stack

![AWS](https://img.shields.io/badge/-AWS-FF9900?style=flat-square)
![Terraform](https://img.shields.io/badge/-Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)
![Docker](https://img.shields.io/badge/-Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/-GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Open Policy Agent](https://img.shields.io/badge/-OPA%20%2F%20Conftest-7D9199?style=flat-square)
![Sigstore](https://img.shields.io/badge/-Cosign-2E2E2E?style=flat-square)
![Python](https://img.shields.io/badge/-Python-3776AB?style=flat-square&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/-FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/-PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Linux](https://img.shields.io/badge/-Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Bash](https://img.shields.io/badge/-Bash-4EAA25?style=flat-square&logo=gnubash&logoColor=white)

**Cloud & IaC:** AWS (ECS Fargate, RDS, ECR, WAF, IAM, KMS, CloudWatch) · Terraform

**CI/CD & supply chain:** GitHub Actions · Docker · Cosign · Syft (SBOM) · Conftest/OPA

**Security testing:** Bandit · Semgrep · pip-audit · gitleaks · Trivy · OWASP ZAP · Nmap · Wireshark · Nessus

**Languages:** Python · Bash · HCL · Rego · YAML · SQL

---

## 🔭 What I'm working on

- Next MediBook milestones: Terraform modules for a second environment, a clinic staff portal, and running migrations from CI
- Rebuilding earlier Kubernetes and Terraform projects to the same evidence-first standard

---

## 🤝 Let's connect

Open to DevSecOps and cloud security roles and internships. Happy to talk about pipeline security, Terraform, or AWS.

👉 **Start with [MediBook](https://github.com/abdurahim50/medibook), then reach out on LinkedIn.**

[LinkedIn](https://www.linkedin.com/in/abdurahim-yongho/) · [Medium](https://yonghoabdurahim.medium.com/) · [dev.to](https://dev.to/abdurahim50) · [X](https://x.com/AYongho)

He/Him · ⚡ I once ran a half marathon with no training, purely to win a bet.
