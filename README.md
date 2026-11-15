# DevSecOps Automated Security Gate & Policy-as-Code Lab

A university and portfolio project about checking infrastructure changes before they are merged.

**Current status: planning only.** No Terraform configuration, executable security workflow, or Rego policy exists yet. No security tests have been verified.

## Our next milestone

Over four weeks at 5–6 hours per week, aim to:
1. Describe a small AWS S3 example in Terraform.
2. Use Checkov locally to demonstrate a violation and its correction.
3. Run the same selected checks automatically on GitHub pull requests.
4. Configure and demonstrate required-check enforcement if available.
5. Document the results and explain the demonstration.

OPA/Rego is optional for this milestone. Real Terraform plan evaluation is later work. No AWS deployment is needed for the initial configuration scans.

## Where to look

| File | Purpose |
| --- | --- |
| [project.md](project.md) | Instructor requirements, research, scope, and schedule |
| [implementation.md](implementation.md) | Setup, commands, test results, and session notes |
| [troubleshooting.md](troubleshooting.md) | Actual errors, attempted fixes, and verification |
| [STATUS.md](STATUS.md) | Short handoff: what works and what comes next |
| [AGENTS.md](AGENTS.md) | Instructions for Codex and other coding assistants |
| [.gitignore](.gitignore) | Keeps local/generated files and credentials out of commits |

Start each session with STATUS.md. Work on one small branch, review the changes, test them, and open a pull request.

## Code folders will appear when needed

- `configs/`: normal Terraform scan target.
- `examples/insecure/`: isolated examples with deliberate violations.
- `.github/workflows/`: the actual GitHub Actions workflow.
- `policy/`: optional Rego rules and their tests.
- `docs/evidence/`: actual sanitized logs or screenshots, when collected.

These are planned paths, not existing implementations. Empty folders and placeholder guides are unnecessary.

## Demonstration boundary

A failed CI job is an automated check. It becomes an enforced merge gate only after required-check settings and a blocked-merge experiment are verified. Passing selected checks does not prove complete security.

Earlier detailed plans remain available in Git history. Existing issues describe the broader backlog; the current milestone in project.md and STATUS.md takes priority.
