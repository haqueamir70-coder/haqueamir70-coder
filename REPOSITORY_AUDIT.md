# GitHub Portfolio — Repository Audit

**Audit date:** 7 November 2026  
**Account:** [haqueamir70-coder](https://github.com/haqueamir70-coder)  
**Scope:** 25 public repositories (24 previously audited repositories plus the new Kubernetes Chaos Engineering & Resilience Lab). Repository trees, READMEs and available GitHub Actions history were reviewed. Selected Terraform, workflow, security and Python implementation files received deeper review and fixes. This is not a claim that every line of every repository has been manually reviewed or that any cloud environment is production-deployed.

## Executive findings

- The account contains a coherent Azure/DevOps portfolio, but several repositories are small learning exercises or placeholders and should not compete with flagship projects.
- A serious credential-handling defect was found in the legacy Azure Terraform CI/CD workflow: an Azure service-principal credential was embedded in YAML and the workflow performed automatic apply. The current workflow removes embedded credentials and automatic apply, and offers an optional OIDC-authenticated plan. **The historical credential must be revoked/rotated because it may remain in Git history.**
- Two Terraform practice repositories lacked a root composition layer, typed inputs/outputs and CI; those foundations have now been added.
- The industrial IoT repository previously documented an architecture without runnable telemetry code; it now has a synthetic event simulator, JSON Schema and unit tests.
- Azure landing-zone and 3-tier examples had broad ingress/public-access weaknesses; private endpoint patterns, tighter network boundaries and CI checks have been added.
- Several repositories are already strong reference implementations; their next value comes from real test evidence and controlled cloud validation, not more decorative README content.

## Repository-by-repository inventory

| # | Repository | Portfolio role | Audit finding / work performed | Latest observed automation |
|---:|---|---|---|---|
| 1 | [cloud-native-software-supply-chain-security-platform](https://github.com/haqueamir70-coder/cloud-native-software-supply-chain-security-platform) | Flagship — DevSecOps | Strong source-to-image trust chain, SBOM, signing, provenance, Kyverno and runbooks. Continue positive/negative admission tests in a disposable cluster. | CI/release run observed passing |
| 2 | [terraform-extend](https://github.com/haqueamir70-coder/terraform-extend) | Learning — Terraform modules | Added typed map/object inputs, module outputs, root outputs, provider constraints, secure storage defaults, example inputs and CI. Historical misspellings in paths retained to avoid breaking references. | New Terraform CI passed |
| 3 | [azure-aks-zero-trust-platform](https://github.com/haqueamir70-coder/azure-aks-zero-trust-platform) | Flagship — Azure/AKS | README clearly separates deployed VNet/subnet/NSG foundation from planned private AKS, DNS and workload controls. Keep that evidence boundary. | Latest observed validation passed |
| 4 | [sre-observability-platform](https://github.com/haqueamir70-coder/sre-observability-platform) | Flagship — SRE | Useful Prometheus/Grafana, SLO, incident and nested project examples. Verify live alert behavior and dashboard screenshots before claiming runtime proof. | Latest observed CI passed |
| 5 | [azure-production-landing-zone](https://github.com/haqueamir70-coder/azure-production-landing-zone) | Supporting flagship — Azure foundation | Removed direct Internet-to-app subnet rule; added private-only Key Vault, private endpoint/DNS, purge protection, name validation and outputs. | New Terraform CI passed |
| 6 | [azure-finops-cost-governance](https://github.com/haqueamir70-coder/azure-finops-cost-governance) | Flagship — FinOps | Python analyzer and Terraform sample are useful. Added rejection of NaN/Infinity costs, budgets and thresholds with regression tests. | New Python + Terraform CI passed |
| 7 | [azure-terraform-cicd](https://github.com/haqueamir70-coder/azure-terraform-cicd) | Supporting — Terraform delivery | Critical exposed credential and auto-apply pattern removed from current workflow. Added credential-free validation, optional protected OIDC plan, and nested-root validation. Rotate the historical secret immediately. | Latest Terraform validation passed; optional OIDC plan remains unconfigured until environment secrets/federation are set |
| 8 | [azure-enterprise-3-tier-architecture](https://github.com/haqueamir70-coder/azure-enterprise-3-tier-architecture) | Flagship — Azure architecture | Added web/app/database/private-endpoint subnet segmentation, NSG associations, private SQL/Key Vault/Blob endpoints and DNS, unique global names, removal of broad SQL firewall exception, and PR CI. | New Terraform CI passed |
| 9 | [MD-AMIRUL-HAQUE](https://github.com/haqueamir70-coder/MD-AMIRUL-HAQUE) | Legacy learning | Two-file placeholder; documented as a learning workspace, not a flagship engineering project. | No workflow configured |
| 10 | [dockerized-application-devops](https://github.com/haqueamir70-coder/dockerized-application-devops) | Supporting — container delivery | Docker build, security workflow and Kubernetes deployment examples. Live cluster deployment is not claimed; keep deployment gated by explicit environment credentials. | Latest observed Docker CI passed |
| 11 | [azure-devsecops-platform](https://github.com/haqueamir70-coder/azure-devsecops-platform) | Supporting flagship — Azure DevSecOps | Modular Terraform, TFLint/Checkov, security docs and a nested Key Vault project. Added dedicated private-endpoint subnet, NSG association, VNet-scoped HTTPS ingress, private Blob endpoint/DNS and disabled public/shared-key storage access. Checkov still reports CMK and Blob read-diagnostics gaps; these are documented and the scan is advisory until closed. | Latest observed Terraform CI passed |
| 12 | [aws-enterprise-cloud-governance-security-platform](https://github.com/haqueamir70-coder/aws-enterprise-cloud-governance-security-platform) | Flagship — AWS governance | Strong network foundation, governance examples, OIDC patterns, runbooks and scenarios. Corrected missing module provider constraints. Organization-level services are correctly labelled reference patterns. | New Terraform CI passed |
| 13 | [secure-gitops-platform](https://github.com/haqueamir70-coder/secure-gitops-platform) | Flagship — Kubernetes/DevSecOps | API, hardened manifests, tests, Trivy and SBOM. Current Trivy scan uses exit code 0, so findings are informational rather than a blocking security gate; decide enforcement after triage. | Latest observed CI passed |
| 14 | [enterprise-internal-developer-platform](https://github.com/haqueamir70-coder/enterprise-internal-developer-platform) | Flagship — Platform Engineering | Good architecture, golden-path, Backstage and policy starter assets. Terraform AWS foundation and OIDC integration remain explicitly planned. | Latest observed repository-quality CI passed |
| 15 | [haqueamir70-coder](https://github.com/haqueamir70-coder/haqueamir70-coder) | Public profile | Rebuilt profile README with role positioning, skills, certifications and featured project navigation. Pin the six recommended repositories manually in GitHub profile settings. | Profile README only |
| 16 | [terraform-security-policy-gate](https://github.com/haqueamir70-coder/terraform-security-policy-gate) | Flagship — IaC security | Checkov + OPA/Rego + compliant/non-compliant fixtures and CI. Keep the distinction between static policy checks and cloud runtime validation. | Latest observed security-gate CI passed |
| 17 | [twishchatamir](https://github.com/haqueamir70-coder/twishchatamir) | Placeholder | Empty project placeholder; README now clearly labels it as not maintained or featured. | No workflow configured |
| 18 | [resource_creation_9th-aug-haq](https://github.com/haqueamir70-coder/resource_creation_9th-aug-haq) | Legacy scratchpad | Minimal historical scratch repository; README now marks it as legacy and points to maintained infrastructure projects. | No workflow configured |
| 19 | [Terraform-_Storage_Module](https://github.com/haqueamir70-coder/Terraform-_Storage_Module) | Learning — Terraform modules | Added root module composition, typed inputs, child/root outputs, secure storage defaults, example variables and CI. | New Terraform CI passed |
| 20 | [azure-industrial-iot-reliability-platform](https://github.com/haqueamir70-coder/azure-industrial-iot-reliability-platform) | Flagship — Industrial IoT | Added synthetic telemetry simulator, versioned JSON Schema, deterministic tests and CI. No customer/refinery telemetry or OT connectivity is included. | New Python/docs CI passed |
| 21 | [azure-key-vault-private-secrets](https://github.com/haqueamir70-coder/azure-key-vault-private-secrets) | Flagship — Azure security | Added NSG association/rules, AzureRM v5 RBAC schema correction and formatting fixes. Private endpoint, private DNS and default-deny design documented. | New Terraform + Checkov CI passed |
| 22 | [azure-vmware-cloud-migration-factory](https://github.com/haqueamir70-coder/azure-vmware-cloud-migration-factory) | Flagship — Migration architecture | Good wave planning, decision records, pilot/cutover/rollback runbooks and Terraform scaffold. No real estate migration is claimed. | Latest observed Terraform CI passed |
| 23 | [azure-enterprise-devsecops-platform](https://github.com/haqueamir70-coder/azure-enterprise-devsecops-platform) | Supporting — Azure foundations | Resource-group/network module foundation now includes app and management NSGs with subnet associations. Added Terraform formatting, backend-free validation, TFLint and advisory Checkov scanning; module-level provider/version constraints added after TFLint findings. | New Terraform CI passed |
| 24 | [kubernetes-ai-inference-platform](https://github.com/haqueamir70-coder/kubernetes-ai-inference-platform) | Flagship — AI platform | FastAPI scaffold, vLLM profile, GPU scheduling, HPA/KEDA examples, GitOps, observability manifests, Terraform and runbooks. GPU/AKS/operator deployment remains an extension, not a live deployment claim. | Latest observed security CI passed; recheck CI after final changes |
| 25 | [kubernetes-chaos-engineering-resilience-lab](https://github.com/haqueamir70-coder/kubernetes-chaos-engineering-resilience-lab) | Flagship — SRE / resilience | Added provisioned Grafana dashboard (8 panels), Prometheus scrape/alert configuration, Helm installation guide, three one-pod/30-second Chaos Mesh templates, evidence report and GitHub Actions asset validation. Live cluster deployment and chaos execution are deferred until the user changes laptops; no runtime result is claimed. | Workflow committed; first run and live lab execution pending |

## Recommended profile pin order

1. Cloud-Native Software Supply Chain Security Platform
2. Enterprise Internal Developer Platform
3. Kubernetes AI Inference Platform
4. Azure AKS Zero-Trust Platform
5. SRE Observability Platform
6. Azure Industrial IoT Reliability Platform

## Remaining actions

### Immediate security action
- Revoke and rotate the service-principal secret previously committed in the old azure-terraform-cicd workflow.
- Review Azure service-principal sign-in and subscription activity logs for unexpected use.
- Consider GitHub secret scanning / push protection and repository-wide Gitleaks checks.

### Portfolio quality actions
- Pin the six projects above.
- Add genuine screenshots from running local labs or test clusters; never use mock screenshots as deployment evidence.
- Add real CI badges only for the actual workflows.
- Keep the README status table current: implemented, CI-validated, cloud-validated and planned are separate states.
- Archive or keep placeholders unpinned rather than deleting learning history.

### Deployment boundary
No Azure/AWS infrastructure was provisioned as part of this repository audit. Terraform validate and successful GitHub Actions runs are not proof of a deployed cloud environment. Any deployment requires the user's target subscription/account, approval and cost review.


## Documentation standard — architecture and interview guide

A repository-specific `docs/README.md` has now been added to all 24 public repositories, including the profile repository and legacy learning repositories. Each guide contains:

- A Mermaid architecture or workflow diagram tailored to that repository's subject.
- Ten repository-specific technical interview questions.
- A preparation note requiring candidates to explain design rationale, security boundaries, failure modes, observability and validation evidence.
- Explicit scope wording so legacy/placeholder repositories and planned architecture are not presented as deployed production systems.

Each repository root README links to its `docs/README.md` guide. The diagrams are source-controlled Mermaid diagrams rendered by GitHub; they are editable text, not screenshots. The legacy learning repository `MD-AMIRUL-HAQUE` is also linked to its guide.


## Interview answer standard — completed 4 November 2026

All 24 public repositories now have a repository-specific `docs/README.md` containing a Mermaid architecture/workflow diagram, 10 technical interview questions, and a separate suggested-answer section with 10 technically grounded answers. Each root README links to the guide. Answers explain trade-offs, implementation boundaries, security controls, failure modes and validation; placeholder repositories explicitly identify conceptual/future-state architecture. Total published coverage: **240 questions and 240 suggested answers**.


## Zero-to-Hero project learning guides — completed 4 November 2026

Added a separate `docs/ZERO-TO-HERO.md` to all 24 public repositories and linked it from each repository's `docs/README.md`. The guides expand beyond short interview Q&A and cover:

- Business scenario, operational pain point and target outcome.
- End-to-end architecture/request or deployment flow.
- Tool/service inventory with each tool's purpose and why it fits the project.
- Implementation sequence and practical CLI commands where applicable.
- Additional scenario-based interview questions with explanatory answers.
- Troubleshooting approach, security/reliability/cost considerations and a staged learning path.
- Explicit scope honesty: implemented, CI-validated, cloud-deployed and planned capabilities are distinct.

The tool inventories distinguish project tools from optional/conditional services where relevant. Conceptual placeholders (including TwisChat and legacy learning workspaces) are clearly labelled; their proposed tools and architectures are not represented as existing implementation. These are structured learning guides, not proof that every optional service has been deployed or every command has been executed.


## Expanded project question banks — completed 4 November 2026

Added `docs/ADVANCED-INTERVIEW-BANK.md` to all 24 public repositories. Each bank contains 40 additional Q&A covering business context, architecture, tool selection, CI/CD, identity, security, troubleshooting, observability, recovery, scaling, cost and evidence. Each also includes a source-code deep-dive checklist and hands-on labs. A central index is available at [docs/PROJECT-QUESTION-BANK-INDEX.md](./docs/PROJECT-QUESTION-BANK-INDEX.md).

Combined documentation coverage is now **50 questions and 50 answers per repository: 1,200 questions and 1,200 answers across 24 repositories** (10 introductory plus 40 advanced per repository). The advanced banks are learning guides; they do not imply every optional tool is deployed. Conceptual and legacy repositories are labelled accordingly.


## First actual source-code walkthrough — Azure 3-tier project

Completed a source-level walkthrough of the current `terraform/` directory in [azure-enterprise-3-tier-architecture](https://github.com/haqueamir70-coder/azure-enterprise-3-tier-architecture/tree/main/terraform). The guide covers 15 Terraform files and includes 20 code-specific Q&A. It also records implementation gaps found in source: Front Door WAF policy has no endpoint/origin/route/security-policy association; Load Balancer has no backend pool/probe/rule; Key Vault and Storage have no workload data-plane role assignments; Recovery Services vault has no backup policy/protected item; Log Analytics/Application Insights have no diagnostic settings or application instrumentation; and location/environment variables are not consistently used. These are findings from code inspection, not a claim that cloud deployment was tested.

The walkthrough is at [docs/SOURCE-CODE-WALKTHROUGH.md](https://github.com/haqueamir70-coder/azure-enterprise-3-tier-architecture/blob/main/docs/SOURCE-CODE-WALKTHROUGH.md). This is the first actual file-by-file source review; the other repositories' question banks contain structured source-review checklists, not yet equivalent line-by-line walkthroughs.


## Portfolio README visual refresh — 7 November 2026

The GitHub account currently exposes 25 public repositories. A portfolio-wide README visual audit was performed. Fifteen maintained project READMEs received a project-specific animated banner, typing-line treatment and technology badges where those elements were missing. Other maintained repositories already had banners, SVG architecture visuals or substantial diagrams and were retained rather than duplicated. Three legacy/placeholder repositories remain deliberately plain and explicitly labelled as non-featured; they were not given artificial architecture or technology claims. The profile README now links to the 25th chaos engineering project. All changes preserve the distinction between implementation, CI validation, deployed infrastructure and planned work.
