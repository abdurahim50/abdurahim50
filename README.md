# Hi, I'm Abdurahim Yongho 👋

**DevSecOps · Cloud & Applied AI · Minneapolis–St. Paul, MN**

Cybersecurity and Computer Science student at Metropolitan State University, with a background in software application development. I build infrastructure that's automated first and secured at the same time: Kubernetes clusters, Terraform-provisioned cloud environments, and CI/CD pipelines where a failing security check stops the deploy instead of filing a report nobody reads.

Lately that includes AI systems, which turn out to raise the same question as a deploy pipeline: what happens when it fails, and does it fail loudly?

🔗 **[Portfolio & writeups → abdurahim50.github.io](https://abdurahim50.github.io)**

---

## 🔭 What I'm working on

- Building and hardening Kubernetes clusters, including one assembled by hand with `kubeadm`, because the managed services only make sense once you've done it the hard way
- Supply-chain security in CI/CD: SHA-pinned actions, keyless image signing, SBOM attestation, and OIDC federation instead of long-lived cloud keys
- Applied AI with guardrails: LLMs for language, deterministic code for decisions
- Working toward AWS Solutions Architect – Associate

---

## 📂 Featured projects

| Project | What it demonstrates | Links |
|---|---|---|
| **VibeMatch AI Concierge** | Agentic `plan → act → check → explain` recommender. Claude parses free text into a schema-constrained profile, a guardrail validates it, and a deterministic engine ranks. Ships with an evaluation harness and a full no-API-key fallback. | [Code](https://github.com/abdurahim50/applied-ai-music-recommender) · [Writeup](https://abdurahim50.github.io/writeups/the-guardrail-that-invented-a-genre.html) |
| **Kubernetes Cluster Autoscaler on EKS** | Terraform-provisioned EKS with the autoscaler deployed via Helm, load-tested until nodes genuinely scale. Covers the IAM/OIDC service-account wiring that trips people up. | [Code](https://github.com/abdurahim50/my-eks-module) · [Article](https://yonghoabdurahim.medium.com/kubernetes-cluster-autoscaler-deployed-on-eks-cluster-4b3a1c2791e5) |
| **Kubernetes the Hard Way with kubeadm** | Multi-node cluster from scratch: certificate distribution, CNI setup, kubelet config, node hardening. No managed control plane. | [Code](https://github.com/abdurahim50/kubernetes_multi-nodes_cluster_using_kubeadm) |
| **HumanGov: Multi-Tenant SaaS on AWS** | Reusable multi-tenant infrastructure via Terraform modules. One module set provisions an isolated stack per tenant, so onboarding a new state is a variable change. | [Article](https://yonghoabdurahim.medium.com/humangov-deployment-of-a-reusable-saas-multi-tenant-aws-infrastructure-using-terraform-modules-722de6698760) |
| **CI/CD to EKS with Jenkins & CodePipeline** | Automated build-and-deploy onto EKS with security checks inside the pipeline rather than alongside it. | [Code](https://github.com/abdurahim50/jenkins_training_docker) · [Article](https://yonghoabdurahim.medium.com/deploy-a-sample-application-onto-eks-cluster-utilizing-aws-ci-cd-code-pipeline-codecommit-aws-81b1b2ea5cde) |

More on the [portfolio site](https://abdurahim50.github.io/projects.html).

---

## 🛠️ Skills

**Cloud & IaC:** AWS · Azure · Terraform · Ansible · IAM design · VPC architecture

**Containers & CI/CD:** Docker · Kubernetes · Helm · Argo CD · Jenkins · GitHub Actions · AWS CodePipeline

**Security:** Linux hardening · Nmap · Wireshark · Nessus · Splunk · container scanning · supply-chain security (Cosign, SBOM)

**Applied AI:** LLM integration · structured outputs · agentic workflows · output guardrails · evaluation harnesses

**Languages:** Python · Bash · C · YAML · HCL · JavaScript · React

---

## 🎓 Certifications

![Security+](https://img.shields.io/badge/CompTIA-Security%2B-2ea44f?style=flat-square)
![Network+](https://img.shields.io/badge/CompTIA-Network%2B-2ea44f?style=flat-square)
![AWS SAA](https://img.shields.io/badge/AWS-Solutions%20Architect%20Associate-lightgrey?style=flat-square)

CompTIA Security+ · CompTIA Network+ · AWS Solutions Architect – Associate *(in progress)*

---

## ✍️ Writing

I write up what I build, including the parts that broke. Recent:

- [The guardrail that invented a genre](https://abdurahim50.github.io/writeups/the-guardrail-that-invented-a-genre.html): an AI-written fallback that confidently ranked the wrong result, and why that's worse than a crash
- [Kubernetes Cluster Autoscaler on EKS](https://yonghoabdurahim.medium.com/kubernetes-cluster-autoscaler-deployed-on-eks-cluster-4b3a1c2791e5)
- [Jenkins with SSL behind an Nginx reverse proxy](https://yonghoabdurahim.medium.com/install-and-configure-jenkins-with-ssl-in-digitalocean-set-up-tools-and-use-nginx-as-reverse-proxy-8ae7077b6f52)

All posts: [Medium](https://yonghoabdurahim.medium.com/) · [dev.to](https://dev.to/abdurahim50)

---

## 🤝 Let's connect

Open to DevSecOps and cloud security roles, collaborations, and freelance infrastructure work. Happy to talk about Kubernetes, Terraform, pipeline security, or homelabs.

[Portfolio](https://abdurahim50.github.io) · [LinkedIn](https://www.linkedin.com/in/abdurahim-yongho/) · [Medium](https://yonghoabdurahim.medium.com/) · [dev.to](https://dev.to/abdurahim50) · [X](https://x.com/AYongho)

He/Him · ⚡ I once ran a half marathon with no training, purely to win a bet.

---















