# Hi, I'm Abdurahim Yongho 👋

## DevSecOps · Cloud Security · Minneapolis-St. Paul, MN

[![Security+](https://img.shields.io/badge/CompTIA-Security%2B-2ea44f?style=flat-square)](https://www.credly.com/badges/80c26a33-d2c7-4bf2-9041-04d08e3fc770)
[![Network+](https://img.shields.io/badge/CompTIA-Network%2B-2ea44f?style=flat-square)](https://www.credly.com/badges/39e56155-56d5-4e24-8f83-4cee81cec34a)
[![PSM I](https://img.shields.io/badge/Scrum.org-PSM%20I-0b5d8c?style=flat-square)](https://www.credly.com/badges/2d3b50e8-cd51-494c-8ab7-ea4bff0e9457)
[![AWS Cloud Practitioner (expired)](https://img.shields.io/badge/AWS-Cloud%20Practitioner%20%28expired%29-lightgrey?style=flat-square)](https://www.credly.com/badges/97b749f6-0859-48cc-91e5-f852d68d52c0)
[![OCI Foundations Associate (expired 2024)](https://img.shields.io/badge/Oracle-OCI%20Foundations%20%28expired%202024%29-lightgrey?style=flat-square)](https://catalog-education.oracle.com/ords/certview/sharebadge?id=6B54E672FE4DDE556CB7F718E52197FC2CBC39CB268E26684EECA734764DE08A)

I build cloud applications and delivery pipelines with security checks, least-privilege access, and recovery testing. MediBook brings those pieces together, with links to code, deployment records, and the gaps I still need to address.

Cybersecurity student at Metropolitan State University, with an A.S. in Software Application Development and a background in HIPAA-regulated compliance work.

### 🔎 Currently looking for

DevSecOps and cloud security **internships or entry-level roles** where I can help teams ship secure-by-default pipelines and infrastructure.

---

## 📂 Featured projects

| Project | What it is | Technologies | Status |
|---|---|---|---|
| **[MediBook](https://github.com/abdurahim50/medibook)** | Patient booking API on AWS with image signing, Terraform policy checks, and approved database migrations | Python · FastAPI · Terraform · ECS Fargate · RDS · GitHub Actions · Cosign · OPA | [![CI](https://github.com/abdurahim50/medibook/actions/workflows/ci.yml/badge.svg?branch=main&event=push)](https://github.com/abdurahim50/medibook/actions/workflows/ci.yml) |

*More projects are being rebuilt to the same evidence-first standard and will be added as they're ready.*

### MediBook in detail

A patient appointment-booking API built with synthetic data and verified through automated tests and live AWS drills. The [engineering case study](https://github.com/abdurahim50/medibook/blob/main/docs/case-study.md) explains why I built it, the challenges I solved, and what I learned.

- **Pipeline:** pull requests run tests, SAST, dependency, secret and image scans, policy tests, authenticated DAST, and a Terraform plan. [CI workflow](https://github.com/abdurahim50/medibook/blob/main/.github/workflows/ci.yml).
- **Supply chain:** keyless Cosign signatures and SBOM attestations, published to ECR through GitHub OIDC without stored AWS access keys.
- **Deployment:** workstation Terraform plans verify the image signature and SBOM attestation; Conftest checks infrastructure policies before apply. Direct AWS API or console deployments can bypass these checks.
- **Migrations:** an approval-gated GitHub workflow uses a dedicated AWS role to run the migration task before the API starts. [Implemented delivery flow](https://github.com/abdurahim50/medibook/blob/main/docs/architecture.md#delivery-path).
- **Data protection:** private, KMS-encrypted RDS PostgreSQL with verified TLS, IAM database authentication, and a least-privilege application role.
- **Recovery:** drill 5 on October 9, 2026 measured **21 min 26 s** from data loss to verified recovery. [Drill results and limitations](https://github.com/abdurahim50/medibook/blob/main/docs/evidence/deployment/recovery-drills.md#drill-5-drill-4-repeated-after-hardening-2026-10-09).
- **Governance:** controls mapped to NIST SP 800-53 Rev. 5, with a STRIDE threat model and documented gaps.

The AWS dev environment is created for verification sessions and destroyed afterward. The CI badge reports workflow status on `main`. [Dev environment and production target](https://github.com/abdurahim50/medibook/blob/main/docs/architecture.md#dev-environment-versus-production).

<details>
<summary>View the delivery flow</summary>

For code or infrastructure releases and fresh dev deployments:

```mermaid
flowchart TD
    PR["Pull request"] --> CI{"Tests and security checks"}
    CI -- fail --> BLOCK["Merge blocked"]
    CI -- pass --> REL["Merge: build and release"]
    REL --> ECR["ECR: signed image and SBOM"]
    ECR --> TF{"Workstation Terraform: signature and policy checks"}
    TF -- fail --> STOP["Plan rejected"]
    TF -- pass --> MIG["Approved GitHub migration workflow"]
    MIG -- "Migration succeeds" --> APP["Terraform starts API on ECS Fargate"]
```

The [architecture walkthrough](https://github.com/abdurahim50/medibook/blob/main/docs/architecture.md) covers the full deployment sequence and remaining access-control limits.

</details>

📄 [Case study](https://github.com/abdurahim50/medibook/blob/main/docs/case-study.md) · [Architecture](https://github.com/abdurahim50/medibook/blob/main/docs/architecture.md) · [Threat model](https://github.com/abdurahim50/medibook/blob/main/docs/threat-model.md) · [NIST controls](https://github.com/abdurahim50/medibook/blob/main/docs/controls.md) · [Evidence](https://github.com/abdurahim50/medibook/blob/main/docs/evidence.md) · [Runbook](https://github.com/abdurahim50/medibook/blob/main/docs/runbook.md)

---

## 🎯 Skills mapped to DevSecOps job requirements

| Typical job requirement | Where to see it in MediBook |
|---|---|
| CI/CD with integrated security testing (SAST, SCA, DAST) | [CI workflow](https://github.com/abdurahim50/medibook/blob/main/.github/workflows/ci.yml): Bandit, Semgrep, pip-audit, gitleaks, Trivy, OWASP ZAP |
| Infrastructure as Code on AWS | [Terraform stacks](https://github.com/abdurahim50/medibook/tree/main/infra): VPC, ALB, WAF, ECS Fargate, RDS, CloudWatch |
| Policy as code and compliance | [Conftest policies](https://github.com/abdurahim50/medibook/tree/main/policy) mapped to NIST SP 800-53 |
| Container security | [Dockerfile](https://github.com/abdurahim50/medibook/blob/main/Dockerfile) and [ECS task configuration](https://github.com/abdurahim50/medibook/blob/main/infra/ecs.tf): non-root user, read-only filesystem, digest pinning, and scanning |
| Software supply-chain security | [Release workflow](https://github.com/abdurahim50/medibook/blob/main/.github/workflows/release.yml): Syft SBOM, Cosign signing, OIDC to ECR |
| IAM and least privilege | [Role configuration](https://github.com/abdurahim50/medibook/blob/main/infra/iam.tf) and [database role tests](https://github.com/abdurahim50/medibook/blob/main/tests/test_least_privilege.py): RDS IAM authentication, row-access-only application role, and separate migration permissions |
| Threat modeling and secure design | [STRIDE threat model](https://github.com/abdurahim50/medibook/blob/main/docs/threat-model.md) |
| Monitoring, incident response, recovery | [Runbook](https://github.com/abdurahim50/medibook/blob/main/docs/runbook.md) and [recovery drills](https://github.com/abdurahim50/medibook/blob/main/docs/evidence/deployment/recovery-drills.md) |
| Secure application development | [Application code](https://github.com/abdurahim50/medibook/tree/main/app) and [tests](https://github.com/abdurahim50/medibook/tree/main/tests): argon2id hashing, session revocation, ownership checks, rate limiting, audit logging, and security headers |

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

- Next MediBook milestones: Terraform modules for a second environment, a clinic staff portal, and AI-assisted intake
- Rebuilding earlier Kubernetes and Terraform projects to the same evidence-first standard

---

## 🤝 Let's connect

Open to DevSecOps and cloud security roles and internships. Happy to talk about pipeline security, Terraform, or AWS.

👉 **Start with [MediBook](https://github.com/abdurahim50/medibook), then reach out on LinkedIn.**

[LinkedIn](https://www.linkedin.com/in/abdurahim-yongho/) · [Medium](https://yonghoabdurahim.medium.com/) · [dev.to](https://dev.to/abdurahim50) · [X](https://x.com/AYongho)

He/Him · ⚡ I once ran a half marathon with no training, purely to win a bet.

