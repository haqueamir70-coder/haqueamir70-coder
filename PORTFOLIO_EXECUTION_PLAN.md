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


## 6. OIDC migration progress — 8 November 2026

- [x] Created GitHub Actions environment `azure-plan` in `haqueamir70-coder/azure-terraform-cicd` (confirmed by user screenshot).
- [x] Created an Entra federated credential named `github-azure-plan` on app registration `twischat_new` (confirmed by user screenshot).
- [x] Documented the immutable GitHub organization/repository identity and environment-secret requirements in the Terraform CI/CD repository README.
- [ ] Add `AZURE_CLIENT_ID`, `AZURE_TENANT_ID` and `AZURE_SUBSCRIPTION_ID` as GitHub environment secrets for `azure-plan`.
- [ ] Verify the federated credential subject matches the generated portal value for this exact repository and environment.
- [ ] Run the manually dispatched authenticated Terraform plan and retain the workflow run as evidence.
- [ ] Confirm the new app registration has the minimum required Azure RBAC role assignments.
- [ ] Revoke the historical exposed service-principal credential only after identifying the exact old app/service principal and checking dependencies.
- [ ] Review Entra service-principal sign-in logs and Azure Activity Logs for the relevant exposure period.

**Current state: Azure-side federation and GitHub environment creation are confirmed. GitHub environment secrets, authenticated workflow execution, RBAC verification and historical credential revocation remain unverified.**
