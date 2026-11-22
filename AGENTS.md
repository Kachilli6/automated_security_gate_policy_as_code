# Working on this project

Beginner university DevSecOps lab. Work in small steps and explain important changes and commands. The student has about 5–6 hours per week and runs learning steps on an Ubuntu VM.

## Read as needed

- README.md: overview and file map.
- STATUS.md: current milestone, verified progress, blockers, and next step.
- project.md: instructor requirements, research, and design rationale.
- implementation.md: actual setup commands, versions, tests, and evidence.
- troubleshooting.md: reproduced problems and fixes.
- For behavior, inspect the actual Terraform, Checkov configuration, workflow, policies, and tests. Some files are only planned; check the tree first.

Inspect the current branch and open PRs when resuming. Repository files cannot reveal uncommitted changes on the student's VM.

## Working rules

- Follow the current milestone in STATUS.md; preserve unrelated work.
- Use a branch and a reviewable pull request for repository edits.
- Distinguish assistant-environment tests from student-VM tests.
- Do not deploy AWS resources unless explicitly requested.
- Never commit secrets, Terraform state, or unsanitized plans.
- Never call untested work verified or claim merge enforcement without evidence.
- Scan deliberate violations separately from normal configurations; check the intended finding rather than any failure.
- In CI use minimal permissions, pinned dependencies, and no cloud credentials for initial scans.
- Keep documentation and this file brief. Add code or folders only when needed.
- Keep project conversations focused and redirect unrelated questions to another chat.

## Finish a task

Update STATUS.md with the result, PR/commit state, blocker, and next small task. Record commands and evidence in implementation.md; record actual bugs and fixes in troubleshooting.md.
