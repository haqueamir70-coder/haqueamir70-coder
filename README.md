<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:071A2F,45:0066CC,100:00D4FF&height=210&section=header&text=MD%20Amirul%20Haque&fontSize=44&fontColor=ffffff&animation=fadeIn" width="100%" alt="MD Amirul Haque — Cloud, DevOps and Platform Engineering" />

# Senior DevOps / DevSecOps Engineer
### Microsoft Azure · Terraform · Kubernetes · CI/CD · Cloud Security · SRE

**I build secure, automated and observable cloud platforms — with infrastructure, delivery workflows and operational evidence documented as code.**

[![LinkedIn](https://img.shields.io/badge/LINKEDIN-CONNECT-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/md-amirul-haque/)
[![GitHub](https://img.shields.io/badge/GITHUB-PORTFOLIO-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/haqueamir70-coder?tab=repositories)
[![Location](https://img.shields.io/badge/LOCATION-SAUDI%20ARABIA-16803D?style=for-the-badge&logo=googlemaps&logoColor=white)](https://www.google.com/maps/place/Saudi+Arabia/)

</div>

---

## Engineering focus

My work spans the engineering lifecycle: **design → provision → build → secure → release → observe → recover**.

| Domain | Technologies and practices |
|---|---|
| Cloud | Microsoft Azure; AWS governance and architecture patterns |
| Infrastructure as Code | Terraform, Azure networking, reusable modules, state management |
| Delivery engineering | GitHub Actions, Azure Pipelines, CI quality gates, GitOps |
| Containers and platforms | Docker, Kubernetes, AKS, platform engineering |
| DevSecOps | Trivy, Checkov, SBOM, Cosign, OIDC, least privilege, policy-as-code |
| Reliability | Prometheus, Grafana, SLI/SLO, alerting, incident response |
| Automation | Python, Bash, PowerShell |

## Certifications

- **AZ-104** — Microsoft Azure Administrator
- **AZ-400** — Designing and Implementing Microsoft DevOps Solutions
- **AZ-305** — Designing Microsoft Azure Infrastructure Solutions

## Selected engineering work

The repositories below are selected for technical depth and relevance. Their READMEs state what is implemented, what CI validates, and what still requires a live environment. A passing workflow is not presented as proof of production deployment.

### 1. Software supply-chain security
[**Cloud-Native Software Supply Chain Security Platform**](https://github.com/haqueamir70-coder/cloud-native-software-supply-chain-security-platform)

Source-to-artifact trust workflow with container scanning, SBOM generation, Cosign signing, provenance and Kubernetes admission policy examples. The repository includes a successful signed-image release run; cluster admission enforcement still requires disposable-cluster verification.

**Stack:** GitHub Actions · Trivy · Syft · Cosign · SBOM · provenance · Kyverno

### 2. Internal developer platform
[**Enterprise Internal Developer Platform**](https://github.com/haqueamir70-coder/enterprise-internal-developer-platform)

Platform engineering reference covering developer golden paths, Backstage examples, Kubernetes delivery patterns, GitOps, policy controls and platform operations. Treat optional cloud/runtime integrations according to the repository delivery-status document.

**Stack:** Backstage · Kubernetes · GitOps · Terraform · Policy-as-Code

### 3. Azure AKS zero-trust foundation
[**Azure AKS Zero-Trust Platform**](https://github.com/haqueamir70-coder/azure-aks-zero-trust-platform)

Terraform-managed Azure network foundation with segmented subnets and NSG associations. Private AKS, identity and workload-security extensions are documented separately from the implemented foundation.

**Stack:** Azure · AKS · Terraform · Network Security · Entra ID

### 4. SRE and observability
[**SRE Observability Platform**](https://github.com/haqueamir70-coder/sre-observability-platform)

Containerized observability lab with Prometheus, Grafana, alert rules, SLO/error-budget material and incident response documentation. Measured reliability outcomes should be taken from actual lab runs, not assumed from example targets.

**Stack:** Prometheus · Grafana · Docker · SLO · Alerting

### 5. Industrial IoT reliability
[**Azure Industrial IoT Reliability Platform**](https://github.com/haqueamir70-coder/azure-industrial-iot-reliability-platform)

Synthetic telemetry reference for equipment monitoring, event ingestion, processing and alerting. It is a portfolio lab and is not connected to customer refinery systems or operational technology.

**Stack:** Azure Event Hubs · Event-driven architecture · Telemetry contracts · Python

### 6. Kubernetes AI inference
[**Kubernetes AI Inference Platform**](https://github.com/haqueamir70-coder/kubernetes-ai-inference-platform)

Inference platform lab with FastAPI, vLLM integration profile, autoscaling patterns, observability manifests, Terraform foundations and operational runbooks. GPU deployment requires compatible infrastructure and is not claimed as provisioned.

**Stack:** Kubernetes · vLLM · FastAPI · GPU scheduling · HPA/KEDA · Prometheus

### Additional projects

- [Azure FinOps Cost Governance](https://github.com/haqueamir70-coder/azure-finops-cost-governance)
- [Azure VMware Cloud Migration Factory](https://github.com/haqueamir70-coder/azure-vmware-cloud-migration-factory)
- [Secure GitOps Platform](https://github.com/haqueamir70-coder/secure-gitops-platform)
- [Terraform Security Policy Gate](https://github.com/haqueamir70-coder/terraform-security-policy-gate)
- [Azure Key Vault Private Secrets](https://github.com/haqueamir70-coder/azure-key-vault-private-secrets)
- [Azure Enterprise 3-Tier Architecture](https://github.com/haqueamir70-coder/azure-enterprise-3-tier-architecture)
- [Azure Production Landing Zone](https://github.com/haqueamir70-coder/azure-production-landing-zone)
- [Azure Terraform CI/CD](https://github.com/haqueamir70-coder/azure-terraform-cicd)

## Engineering principles

- **Security by default:** least privilege, federated identity, explicit trust boundaries and private networking.
- **Repeatable infrastructure:** reviewed Terraform, version constraints and protected state.
- **Automated verification:** formatting, validation, tests and security scanning before release.
- **Operational readiness:** health signals, actionable alerts, runbooks and rollback paths.
- **Evidence over claims:** distinguish local tests, CI validation, cloud deployment and future-state design.
- **Cost-aware engineering:** disclose billable resources, prerequisites and teardown steps.

## Portfolio evidence and transparency

- [Repository audit and remediation history](REPOSITORY_AUDIT.md)
- [Portfolio execution plan and outstanding evidence gates](PORTFOLIO_EXECUTION_PLAN.md)
- [Repository activity](https://github.com/haqueamir70-coder?tab=overview)

I do not treat a README, architecture diagram or green static-validation workflow as proof of a production deployment. Live demonstrations, test reports and operational measurements will be added as they are actually produced.

## Connect

Open to technical conversations and opportunities in **DevOps, DevSecOps, Azure Cloud, Platform Engineering, Kubernetes, Infrastructure Automation and SRE**.

[Connect on LinkedIn](https://www.linkedin.com/in/md-amirul-haque/)

<div align="center">
<sub>Build securely. Automate deliberately. Operate with evidence.</sub>
</div>

## Architecture and interview preparation

See [this profile repository's architecture and interview guide](docs/README.md) and each selected project's own documentation for implementation details and design decisions.
