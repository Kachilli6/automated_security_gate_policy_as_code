# Project Plan, Research & Progress

## 1. Project Topic
Building an Automated Infrastructure-as-Code Security Gate using Terraform, Checkov, Open Policy Agent, and GitHub Actions.

## 2. Goal
Develop a working CI/CD pipeline that automatically evaluates Terraform code against static analysis benchmarks and custom Rego policy rules, blocking insecure deployments at the pull-request stage.

## 3. Tasks
- [ ] Write secure and intentionally insecure Terraform definitions (`main.tf`).
- [ ] Configure local static security scans using Checkov.
- [ ] Convert Terraform execution plans into JSON format (`tfplan.json`).
- [ ] Write custom policy-as-code rules in Rego (`s3_policy.rego`).
- [ ] Build a GitHub Actions workflow to run scans automatically on Pull Requests.
- [ ] Enforce branch protection rules to prevent non-compliant code merges.

## 4. Relevance
This project addresses real-world cloud security misconfigurations by embedding automated policy checks into developer workflows. It provides hands-on mastery of policy-as-code syntax, pipeline integration, and static analysis techniques.

## 5. Research & Analysis

### Official Documentation
* [HashiCorp Terraform Documentation](https://developer.hashicorp.com/terraform/docs)
* [Bridgecrew Checkov Documentation](https://www.checkov.io/1.Welcome/What%20is%20Checkov.html)
* [Open Policy Agent Documentation](https://www.openpolicyagent.org/docs/latest/)
* [GitHub Actions Documentation](https://docs.github.com/en/actions)

### Important Concepts
* **Shift-Left Security:** Moving security validations earlier in the development pipeline (e.g., at the PR stage rather than post-deployment).
* **Policy-as-Code (PaC):** Writing compliance, authorization, and governance rules as version-controlled code.
* **Declarative Rules (Rego):** Querying structured JSON execution plans to assert mandatory attributes or deny violations.

## 6. Methods and Tools
* **Software:** Git, Terraform CLI, OPA CLI, Checkov Python CLI.
* **Platform:** GitHub Actions (Ubuntu-latest runners).
* **Environment:** Local Linux / WSL2 workstation.
* **Methods:**
  * Iterative local testing using `terraform plan` and `opa eval`.
  * Live CI/CD evaluation using triggered GitHub Action runs on test branches.

## 7. Work Plan

| Week | Tasks | Expected Result |
| **Week 1** | Local IaC setup & Checkov scanning | Terraform files (`main.tf`) created; Checkov CLI successfully catching intentional vulnerabilities locally. |
| **Week 2** | OPA integration & Rego custom policies | Execution plan JSON exported; custom `s3_policy.rego` denying non-compliant resources. |
| **Week 3** | GitHub Actions workflow & pipeline gating | Automated YAML pipeline running on PRs; branch protection blocking non-compliant code. |
