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

Week,Tasks,Expected Result
Week 1,"Workspace & IaC Foundations• Initialize directory structure (configs/, scripts/, policy/).• Install Terraform CLI and Python/pip locally.• Author initial main.tf with baseline compliant and non-compliant AWS S3 bucket declarations.",Working local workspace with a functional main.tf ready for static analysis.
Week 2,Off-the-Shelf Static Scanning• Install Checkov CLI.• Execute local static scans against main.tf.• Document identified misconfigurations and standard CIS benchmark rules in implementation.md.,CLI scan logs detailing detected security vulnerabilities and pass/fail states.
Week 3,IaC Plan Generation & AST Parsing• Initialize Terraform working directory (terraform init).• Generate binary execution plans (terraform plan -out).• Convert plans to JSON format (terraform show -json).,A structured tfplan.json file representing the infrastructure state.
Week 4,Rego Language & OPA Basics• Install Open Policy Agent (OPA) CLI locally.• Complete core Styra Academy / Rego tutorials.• Inspect tfplan.json data structure using opa eval queries.,Working local OPA environment and baseline Rego query comprehension.
Week 5,Custom Policy Authoring (Part 1)• Draft s3_policy.rego to target public ACLs (public-read).• Implement deny rules parsing resource change arrays.• Test evaluation against tfplan.json.,Local Rego policy file successfully blocking public S3 bucket ACL configurations.
Week 6,"Custom Policy Authoring (Part 2)• Add mandatory tag compliance rules (e.g., required Environment tag).• Refactor Rego logic to produce explicit error messages per violation.• Document policy logic in implementation.md.",Robust s3_policy.rego enforcing both security ACLs and organizational metadata tags.
Week 7,GitHub Actions Pipeline Setup• Create public GitHub repository and push project files.• Draft .github/workflows/devsecops-gate.yml.• Configure workflow triggers on pull_request events to main.,Automated GitHub Actions workflow triggering on incoming code changes.
Week 8,Pipeline Tool Integration• Add Checkov Action step to pipeline.• Add OPA setup and opa eval evaluation step to pipeline.• Configure exit code assertions (exit 1 on policy failure).,Complete CI/CD security gate executing full scans on every pull request.
Week 9,Branch Protection & Gate Enforcement• Configure GitHub Branch Protection rules for main.• Require status checks from the DevSecOps gate to pass before merging.• Conduct positive test (compliant code merge).,Verified pipeline allowing compliant pull requests to merge cleanly.
Week 10,"Negative Testing & Edge Case Validation• Submit intentionally flawed PRs (public ACLs, missing tags).• Verify that GitHub Actions blocks non-compliant merges.• Log findings and edge-case behaviors in troubleshooting.md.",Confirmed security gate blocking non-compliant code with clear feedback.
Week 11,"Repository Documentation & Polish• Finalize all 4 Markdown files (README.md, project.md, implementation.md, troubleshooting.md).• Add execution logs and pipeline run screenshots to screenshots/.• Clean up workspace files and configs/.","Complete, reproducible open-source portfolio repository."
Week 12,Academic Framing & Thesis Outline• Analyze pipeline execution latencies and developer friction metrics.• Select Master's research direction (Policy-as-Code vs. Software Supply Chain).• Draft formal Master's thesis proposal based on empirical project findings.,A completed Master's thesis proposal backed by a functional DevSecOps lab.
