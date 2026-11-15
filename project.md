# Project plan

## 1. Topic

DevSecOps Automated Security Gate & Policy-as-Code Lab: checking AWS S3 Terraform configurations before merge.

## 2. Goal

Build and demonstrate an automated check that detects selected infrastructure misconfigurations. Configure and verify merge enforcement before describing it as an enforced gate.

The broader university project remains a 12-week design. Our immediate presentation milestone is deliberately smaller: four weeks at 5–6 hours per week, approximately 20–24 hours total. The presentation date and instructor acceptance of this interim scope still need confirmation.

## 3. Tasks

1. Learn the essential Git branch, commit, push, and pull-request workflow.
2. Prepare the Ubuntu development environment.
3. Write one small Terraform example and select a few Checkov rules.
4. Demonstrate an intended failure and a corrected passing configuration.
5. Run the same checks in GitHub Actions.
6. Configure required checks if available and prove blocked merging.
7. Record results and prepare a repeatable presentation.

Optional after this works: one custom Rego policy with positive and negative tests. Real Terraform-generated plan integration is a later milestone.

## 4. Relevance

Infrastructure configuration errors can be repeated through automation. Checking changes during review gives earlier feedback and makes requirements testable. We study whether a small, documented set of rules catches our deliberately introduced mistakes. This complements runtime security; it does not replace it.

## 5. Research and source analysis

These design findings are condensed from the earlier project research, not new experimental results. Recheck relevant official documentation when implementing version-specific commands.

| Source | Design lesson |
| --- | --- |
| [NIST SSDF](https://csrc.nist.gov/pubs/sp/800/218/final) | Integrate security requirements and verification into development. One gate is not the whole framework. |
| [Checkov CLI](https://www.checkov.io/2.Basics/CLI%20Command%20Reference.html) | Record selected check IDs and failure behavior; passing selected checks is not complete security or CIS certification. |
| [Terraform JSON format](https://developer.hashicorp.com/terraform/internals/json-format) | Terraform creates plan data; it contains planned values, changes, and unknowns, not just parsed HCL. |
| [OPA Terraform integration](https://www.openpolicyagent.org/docs/terraform) and [CLI](https://www.openpolicyagent.org/docs/cli) | Custom policy evaluates structured input. An evaluation completing does not itself prove an allow decision. |
| [GitHub protected branches](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches) | Failed checks block merging only when enforcement is configured and applies to the actor. |
| [GitHub secure workflow use](https://docs.github.com/en/actions/reference/security/secure-use) | Keep permissions small and review changes to the checks themselves. |
| [AWS S3 encryption FAQ](https://docs.aws.amazon.com/AmazonS3/latest/userguide/default-encryption-faq.html) | S3 encrypts new uploads by default; requiring explicit SSE-KMS is an additional lab requirement. |
| [Terraform show](https://developer.hashicorp.com/terraform/cli/commands/show) | Exported JSON can expose sensitive values; do not commit unsanitized plans. |

## 6. Methods and tools

- Ubuntu VM: write files, run checks, and investigate errors.
- Git/GitHub: version changes and review pull requests.
- Terraform: describe the example S3 infrastructure.
- Checkov: scan configuration against selected checks.
- GitHub Actions: repeat checks on pull requests.
- OPA/Rego: optional custom-policy extension.

Method: define expected results, introduce one controlled violation, run the check, correct it, and rerun. Record tool versions, commands, findings, exit codes, and evidence in implementation.md.

Initial flow: Terraform configuration → local Checkov scan → branch and PR → Actions scan → required-check enforcement.

S3 is the example being checked; it is not hosted on the VM. Initial scans do not require deploying AWS resources. Do not add deployment, Kubernetes, multi-cloud support, or application scanning to this milestone.

Start with public-access-block settings and/or versioning. Add explicit SSE-KMS or required tags only when the first checks work. Document exact coverage instead of promising four implemented controls.

## 7. Work plan

### Current four-week presentation milestone

| Week | Work | Evidence |
| --- | --- | --- |
| 1 | Git basics, environment, small Terraform example, first local scan | Actual versions and first scan output |
| 2 | Select rules; test violating and corrected examples | Expected/actual results and finding IDs |
| 3 | Build Actions workflow; configure enforcement if available | Failed and passing PR checks; blocked-merge evidence if verified |
| 4 | Fix problems, reproduce, document, rehearse | Demonstration and honest limitations |

OPA is optional, not a condition for the first demonstration. If setup takes longer, present the verified local checks as an interim result rather than claiming CI is complete.

### Broader 12-week academic outline

This is a planning outline, not a statement that these weeks have been completed. The original start date is unconfirmed; the four-week milestone above is the current working priority.

| Week | Stage |
| --- | --- |
| 1 | Topic, scope, and research |
| 2 | Git and development environment |
| 3 | Local Terraform/Checkov pass-and-fail examples |
| 4 | Initial automated PR checks |
| 5 | Merge enforcement and reproducibility |
| 6 | First custom Rego policy and tests |
| 7 | Real Terraform plan generation |
| 8 | Connect plans to policy evaluation |
| 9 | Missing/unknown inputs and execution-failure tests |
| 10 | Evaluate rule coverage and limitations |
| 11 | Clean-checkout rehearsal and documentation |
| 12 | Final demonstration and report |

## 8. Current progress

Repository organization and planning are complete; executable implementation is not.
The repository review found documentation only. VM installations and test results remain unverified.
Read STATUS.md for the next task and implementation.md for actual execution evidence.

## 9. Problems and bugs

Record reproduced errors and verified fixes in troubleshooting.md. Do not invent results, backdate work, or treat expected risks as observed bugs.

## 10. Documentation

- README.md: short overview and navigation.
- This file: requirements, sources, scope, and schedule.
- implementation.md: setup, tests, session notes, and evidence.
- troubleshooting.md: actual errors and fixes.
- STATUS.md: current handoff.
- AGENTS.md: assistant working instructions.

The former separate catalogue, weekly log, security model, and test matrix are consolidated here and in implementation.md. Prior proposals remain recoverable through Git history.

## Success criteria and limits

A known compliant example passes selected checks; a deliberate violation produces the intended finding; the corrected example passes. Failed execution must not be reported as a successful scan. Only claim merge blocking after testing applicable required-check settings.

Review workflow and scanner changes, use minimal CI permissions and pinned dependencies, and do not run cloud deployment in PR jobs. A repository owner can change rules or bypass settings; this lab does not protect against a malicious administrator.

If OPA is added, label synthetic fixtures, require an explicit allow decision, and test violations and invalid inputs. Before claiming real plan integration, verify Terraform-generated data, unknown-value handling, and correct associations between buckets and their separate protection resources.
