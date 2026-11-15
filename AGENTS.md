# Working instructions

This repository belongs to the wider learning project "Becoming who I want to be".
The student is learning Linux, Git, and DevSecOps and has 5–6 hours per week.

## Read first

Read README.md and STATUS.md, then the relevant code and documentation.
Use project.md for scope; implementation.md for verified commands and results.
Do not rely on chat memory or old issues as the authoritative current plan.

## Current scope

Terraform + selected Checkov checks + GitHub Actions is the next presentation milestone.
OPA/Rego is optional. Real Terraform plans and broader policy coverage are later work.
No AWS deployment unless the user explicitly requests it.

## Working style

- Work on one small, understandable task at a time.
- Explain important changes and commands in plain language.
- Let the student run learning steps on their Ubuntu VM.
- Distinguish assistant-environment tests from student-VM tests.
- Keep documentation short; reuse existing files instead of adding templates or placeholder folders.
- Inspect current files before editing. Preserve unrelated user changes.
- Use a branch and a reviewable pull request for repository changes.
- Never claim installation, test success, or merge enforcement without evidence.
- Keep deliberate violations separate from the normal scan target.
- A negative test must detect the intended violation, not merely return any error.
- Never commit secrets, Terraform state, or unsanitized plan output.
- For CI, use minimal permissions, pinned dependencies, and no cloud credentials for the initial scans.
- At the end of a task, update STATUS.md. Record useful commands, results, and evidence in implementation.md; actual bugs in troubleshooting.md.

## Resuming after a lost or new chat

- Inspect the current branch, open PRs, and actual files; STATUS.md may lag behind a recent change.
- Read project.md for instructor requirements and implementation.md for tested setup/results.
- Ask only for missing local state: available session time, uncommitted work, environment output, and deadline if unknown.
- Keep this conversation dedicated to the project; gently redirect unrelated requests.
- At session end, record the exact next task and relevant PR/commit in STATUS.md. Distinguish merged, unmerged, and local-only work.
