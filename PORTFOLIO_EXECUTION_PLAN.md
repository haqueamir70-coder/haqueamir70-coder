# Portfolio Execution Plan — Evidence-First Upgrade

**Owner:** MD Amirul Haque  
**Last reviewed:** 7 November 2026  
**Objective:** Raise the portfolio's engineering credibility through verifiable implementation, security hygiene, operational evidence and external collaboration.

This is an execution plan, not a declaration that every item is complete. Scores are qualitative review targets, not GitHub or recruiter ratings.

## 1. Critical security gate — historical credential exposure

The portfolio audit records that an earlier revision of `azure-terraform-cicd` contained a service-principal credential. The current README warns that removing the value from the latest workflow does not remove it from Git history.

- [ ] Revoke the exposed Azure service-principal credential in Microsoft Entra ID.
- [ ] Identify the affected application/service principal and issue a replacement only if still required.
- [ ] Review Entra sign-in logs and Azure Activity Logs for the exposure window.
- [ ] Confirm current workflows use GitHub OIDC/workload federation where supported.
- [ ] Review Git history and coordinate a history rewrite if required; notify collaborators before rewriting.
- [ ] Enable GitHub secret scanning and push protection where available.
- [ ] Run a repository-wide secret scan and remediate any findings.
- [ ] Record the remediation date and evidence without publishing secret values or sensitive log data.

**Status: UNVERIFIED / BLOCKING.** Repository edits alone cannot revoke an Azure credential or establish that logs were reviewed. Do not mark this section complete until the Azure-side actions are actually performed.

## 2. Profile presentation

- [x] Refocus the profile README on six flagship engineering projects.
- [x] Add explicit boundaries between CI validation, local testing, cloud deployment and planned work.
- [x] Link the execution plan and repository audit.
- [ ] Manually pin the six selected repositories on the GitHub profile.
- [ ] Verify profile bio, location, public contact preference and social links.
- [ ] Review the profile on desktop and mobile after pinning.

Suggested pin order:
1. Cloud-Native Software Supply Chain Security Platform
2. Enterprise Internal Developer Platform
3. Azure AKS Zero-Trust Platform
4. SRE Observability Platform
5. Azure Industrial IoT Reliability Platform
6. Kubernetes AI Inference Platform

## 3. Runtime evidence — flagship projects

For each project, capture evidence from a real local lab or disposable test environment. Do not fabricate screenshots, metrics, cloud resources or workflow outcomes.

### Supply-chain security
- [ ] Run the complete documented lab from a clean checkout.
- [ ] Save test output, scan report, SBOM and immutable image digest.
- [ ] Verify signature and provenance against the expected workflow identity.
- [ ] Install Kyverno in a disposable cluster.
- [ ] Test both an accepted signed image and a rejected unsigned/untrusted image.
- [ ] Record policy mode, cluster version and exact commands.

### Secure GitOps / application platform
- [ ] Run API tests and container locally from a clean checkout.
- [ ] Deploy to a disposable Kubernetes cluster.
- [ ] Verify readiness/liveness, rollout, resource limits and PodDisruptionBudget.
- [ ] Verify NetworkPolicy behavior with an allowed and denied connection.
- [ ] Capture rollout and test output; document CNI and metrics-server dependencies.

### SRE observability
- [ ] Start the lab from documented Compose configuration.
- [ ] Verify Prometheus targets and Grafana dashboards.
- [ ] Trigger a controlled test alert and record delivery.
- [ ] Run a bounded failure/recovery exercise.
- [ ] Calculate availability/latency from collected data; label the measurement window and sample size.
- [ ] Publish a postmortem with timeline, detection, mitigation and follow-up actions.

### Azure AKS / Terraform
- [ ] Run fmt, init, validate, lint and security scans from a clean checkout.
- [ ] Inspect and save a redacted Terraform plan.
- [ ] Deploy only to an explicitly approved non-production subscription after cost review.
- [ ] Verify private DNS, routing, NSG behavior and identity permissions.
- [ ] Capture resource outputs and teardown evidence.
- [ ] Never publish state files, plan files, credentials, subscription identifiers or private keys.

### Industrial IoT reliability
- [ ] Run the synthetic telemetry simulator and deterministic tests.
- [ ] Demonstrate schema validation and malformed-event handling.
- [ ] Demonstrate threshold/alert logic with synthetic data.
- [ ] Publish a dashboard screenshot generated from the running lab.
- [ ] Keep all customer, refinery, OT and production data out of the repository.

### AI inference
- [ ] Run the CPU-compatible local profile first.
- [ ] Verify API health, inference response, resource behavior and telemetry.
- [ ] Test autoscaling only in a cluster with the required metrics components.
- [ ] Treat GPU scheduling/vLLM deployment as pending until actually run on compatible hardware.
- [ ] Record model, runtime, hardware, test load and measured latency if benchmarked.

## 4. External engineering collaboration

- [ ] Identify one actively maintained project in Terraform, Kubernetes, GitHub Actions or cloud-native security.
- [ ] Read contribution guidelines and reproduce an existing issue.
- [ ] Submit a small, test-backed fix or documentation improvement.
- [ ] Respond to maintainer feedback and update the change.
- [ ] Publish only merged/accepted contributions as completed achievements.
- [ ] Repeat with a second project after the first contribution is complete.

Do not create self-authored issues or empty pull requests merely to inflate activity.

## 5. Repository hygiene

- [ ] Review overlapping Azure DevSecOps and Terraform repositories; explain their distinct scope.
- [ ] Archive genuinely obsolete experiments rather than presenting placeholders as active products.
- [ ] Add branch protection/rulesets to flagship repositories where account settings permit.
- [ ] Require CI checks before merge where practical.
- [ ] Pin third-party GitHub Actions to immutable commit SHAs for high-trust workflows.
- [ ] Review workflow permissions and use least privilege.
- [ ] Add Dependabot or equivalent dependency update automation where appropriate.
- [ ] Keep README status tables synchronized with code and actual evidence.

## 6. Evidence publication standard

Every flagship repository should eventually expose:
- Reproducible setup and teardown instructions.
- A clean CI run on the current default branch.
- Test output and security scan artifacts.
- Architecture and threat-model documentation.
- At least one real execution screenshot or short demo.
- Known limitations and unimplemented controls.
- A concise explanation of design trade-offs.

Redact tokens, account IDs, private IPs, customer identifiers, internal hostnames and other sensitive operational details.

## 7. Review gates and score targets

| Dimension | Target standard |
|---|---|
| Profile clarity | Focused identity and six relevant pinned projects |
| Reproducibility | Clean-checkout setup works as documented |
| CI quality | Current workflows run on current commits and publish useful artifacts |
| Security | Historical credential exposure closed and secret scanning enabled |
| Runtime proof | Multiple flagship labs actually executed and documented |
| Reliability | At least one measured failure/recovery exercise with methodology |
| Collaboration | Accepted external contribution(s) with review history |
| Maintenance | Clear scope, current dependencies and honest implementation status |

A target of 9.5/10 should be considered only after the critical security gate and the runtime/collaboration evidence gates are independently verified. A README refresh by itself cannot justify that score.


## 8. OIDC migration progress — 8 November 2026

- [x] Created GitHub Actions environment `azure-plan` in `haqueamir70-coder/azure-terraform-cicd` (confirmed by user screenshot).
- [x] Created Entra federated credential `github-azure-plan` on app registration `twischat_new` (confirmed by user screenshot).
- [x] Added GitHub environment secrets `AZURE_CLIENT_ID`, `AZURE_TENANT_ID` and `AZURE_SUBSCRIPTION_ID` (confirmed by user screenshot).
- [x] Verified the immutable-ID GitHub OIDC subject against the actual Azure Login job log.
- [x] Ran authenticated workflow [Azure Terraform CI #31](https://github.com/haqueamir70-coder/azure-terraform-cicd/actions/runs/42474695790); all three jobs succeeded.
- [x] Verified Azure CLI OIDC login and subscription selection in the job log.
- [x] Verified backend-free Terraform plan completed with 1 add, 0 change, 0 destroy.
- [x] Published run evidence and limitations in `azure-terraform-cicd/docs/OIDC-VERIFICATION.md`.
- [x] Create the Azure Storage Account and private blob container manually; add a repository-specific remote-state bootstrap runbook. Remote backend access remains blocked pending the app's Blob data-plane role.
- [x] Change the root Terraform example to read the manually created `rg-github-cicd-demo` as a data source instead of attempting to create a duplicate; CI validation runs #34, #35 and #36 passed.
- [ ] Grant and test `Storage Blob Data Contributor` for the OIDC app, then configure and test the remote backend; no remote-state plan has run.
- [ ] Confirm the new app registration has only the minimum required Azure RBAC assignments, including any required state-storage data-plane access.
- [ ] Identify and revoke the historical exposed service-principal credential only after confirming the exact old app/service principal and checking dependencies.
- [ ] Review Entra service-principal sign-in logs and Azure Activity Logs for the relevant exposure period.
- [ ] Verify GitHub secret scanning and push protection; pin third-party GitHub Actions to reviewed immutable commit SHAs.

**Current state: GitHub-to-Entra OIDC authentication and a backend-free authenticated Terraform plan are verified. The existing resource group is now read as a data source and root CI validation passed. The Storage Account/container exist and the remote-state runbook is published, but the OIDC app lacks Blob data-plane access, so remote backend initialization is blocked. No infrastructure apply or deployment was performed. Historical credential revocation and log review remain open.**


## Dependency update automation — 8 November 2026

- [x] Confirmed the supply-chain security flagship already has a Dependabot configuration.
- [x] Added weekly GitHub Actions, Python/pip and Terraform dependency update schedules to the five remaining selected flagship repositories where those ecosystems exist:
  - `enterprise-internal-developer-platform`
  - `azure-aks-zero-trust-platform`
  - `sre-observability-platform`
  - `azure-industrial-iot-reliability-platform`
  - `kubernetes-ai-inference-platform`
- [ ] Review the first Dependabot pull requests and run the relevant CI/security tests before merging.
- [ ] Resolve vulnerable or unsupported dependencies based on actual alerts and compatibility tests; do not auto-merge updates without review.

These configurations enable scheduled update PRs. They do not prove that dependencies are current or vulnerability-free until Dependabot produces and the maintainer reviews the updates.


## First Dependabot PR review queue — 8 November 2026

Dependabot began opening update PRs after the new schedules were committed. The following PRs were visible during this review:

- [Enterprise Internal Developer Platform #1](https://github.com/haqueamir70-coder/enterprise-internal-developer-platform/pull/1) — actions/checkout 4 → 7.
- [Azure AKS Zero-Trust #1](https://github.com/haqueamir70-coder/azure-aks-zero-trust-platform/pull/1) — hashicorp/setup-terraform 3 → 4.
- [Azure AKS Zero-Trust #2](https://github.com/haqueamir70-coder/azure-aks-zero-trust-platform/pull/2) — actions/checkout 4 → 7.

At review time, these PRs were open and their commit statuses were pending. They were deliberately not merged. Check compatibility, inspect release notes and wait for CI before merging. Additional update PRs may appear as scheduled checks complete.


## CI failure triage — 8 November 2026

- [x] Inspected checks for the latest Dependabot PRs in the internal developer platform, Azure AKS zero-trust, SRE observability, industrial IoT reliability and Kubernetes AI inference repositories.
- [x] Confirmed passing checks for Enterprise Internal Developer Platform #1 (2/2), Azure AKS Zero Trust #1 and #2 (2/2 each), and Kubernetes AI Inference #11 (4/4).
- [x] Identified SRE Observability build-scan failure: the workflow still references `aquasecurity/trivy-action@0.28.0`, which GitHub cannot resolve. Existing Dependabot PR #4 proposes 0.36.0; review its checks before merging.
- [x] Identified Industrial IoT Gitleaks failure: the action was given a shallow checkout and could not resolve the PR commit range. Opened [fix PR #4](https://github.com/haqueamir70-coder/azure-industrial-iot-reliability-platform/pull/4) to set `fetch-depth: 0` for both checkout steps.
- [ ] Re-check CI on Industrial IoT fix PR #4 and merge only after all required checks pass.
- [ ] Verify SRE Trivy update PR #4 checks and merge only after build/scan succeeds.

The CI failures are workflow execution/configuration failures, not evidence of a clean security scan. No Dependabot PR was merged in this review.


## Security scan remediation follow-up — 8 November 2026

- [x] Inspected the Trivy findings in SRE Observability: HIGH CVE-2026-76844 in Debian `zlib1g` and HIGH CVE-2025-62727 in Starlette 0.41.3.
- [x] Opened [SRE remediation PR #13](https://github.com/haqueamir70-coder/sre-observability-platform/pull/13): upgrade FastAPI to 0.162.0, pin Starlette to the scanner-reported fixed version 0.49.1, upgrade Debian packages during image build, and update the Trivy action to resolvable v0.36.0.
- [ ] Wait for PR #13 CI and inspect the new Trivy report. Do not merge unless the scan and application validation pass.
- [x] Industrial IoT Gitleaks fix PR #4 passed both required checks (synthetic telemetry tests and documentation/repository checks); merge review remains pending.

The remediation is not considered complete until a fresh image scan confirms the findings are cleared. The Trivy action update itself does not remediate vulnerabilities.


## Dependabot execution update — 8 November 2026 (later review)

- [x] Merged passing dependency PRs after checking the relevant CI results: 18 Dependabot PRs across the flagship repositories to date.
- [x] SRE Observability #13 merged after FastAPI/Starlette remediation, Debian package upgrade, Trivy v0.36.0 update, successful blocking Trivy filesystem/image scans and SBOM upload.
- [x] SRE Observability #8 and #9 and #10 merged after their latest validation/security checks passed.
- [x] Kubernetes AI Inference #2, #4, #5, #6, #8, #9, #10 and #11 merged after their respective validation/API/Trivy checks passed.
- [x] Industrial IoT #1, #2 and #3 merged after required checks passed; #2 was updated to fetch full Git history so Gitleaks could inspect the PR commit range.
- [x] Enterprise Internal Developer Platform #1 and Azure AKS Zero Trust #1 and #2 merged after checks passed.
- [ ] Resolve remaining stale/conflicting PRs by regenerating updates against current main rather than forcing merges: SRE #7, #3, #5, #6 and #2; Kubernetes AI #7 and #3. Recheck current PR state before action.
- [ ] Confirm all latest default-branch workflow runs after these merges are complete.
- [ ] Azure tenant-side blockers remain: Blob data-plane RBAC for OIDC state access, historical service-principal credential revocation and audit-log review.

**Important:** PRs were merged only when the relevant checks passed and GitHub accepted the merge. A successful CI run is repository validation, not proof of cloud deployment or production runtime. The 2-hour target is a work window, not a guarantee that tenant-owner actions or external review can be completed without access.


## Two-hour execution closeout — 8 November 2026

- [x] Dependabot merges increased to **24** across the selected flagship repositories after fresh checks and conflict-safe merges.
- [x] Repaired Industrial IoT Gitleaks v3 by fetching full Git history; the updated PR checks passed and the update was merged.
- [x] Updated stale SRE Dependabot branches and resolved the Trivy action reference; merged the passing upload-artifact, setup-python, checkout and Uvicorn updates.
- [x] Updated Kubernetes AI Inference dependency branches; merged passing Pydantic, checkout, AzureRM, setup-python, setup-terraform, kubectl and Uvicorn updates.
- [x] Added a dedicated Terraform format/init/validate job for the Azure Cost Guardrails nested project and verified the default-branch job passed.
- [ ] SRE Observability AzureRM provider update PR #2 remains open pending a refreshed PR run against the new nested-project validation job and review of provider compatibility.
- [ ] SRE Observability PR #5/#3 were merged only after their Trivy action references were corrected and the latest relevant checks passed.
- [ ] Confirm the latest Checkov result on the newest SRE main workflow run.
- [ ] Azure tenant owner must still grant Blob data-plane RBAC, revoke the historical credential and review Entra/Azure logs. These cannot be completed from repository permissions.
- [ ] Live Kubernetes/AKS execution, runtime screenshots and external open-source contribution remain outside this repository-only session.

**Closeout boundary:** 24 dependency PRs merged; one SRE Terraform provider PR remains open for targeted verification. No Azure infrastructure apply or live cluster test was performed.

**Final correction:** The stale SRE AzureRM Dependabot PR #2 was closed as superseded. A clean replacement [PR #14](https://github.com/haqueamir70-coder/sre-observability-platform/pull/14) was opened from current main with the new dedicated Terraform validation path. Its checks are running; do not merge until all required jobs pass.
