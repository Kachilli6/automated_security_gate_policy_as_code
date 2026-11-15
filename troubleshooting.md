# Problems and fixes

No runtime bug has been reproduced for this project yet.

## Design corrections already identified

- Terraform generates plan JSON; OPA evaluates it. Plan JSON is not simply an HCL syntax tree.
- A failed workflow does not enforce merging without required-check settings.
- Deliberate violations belong outside the normal scan target.
- S3 default encryption and a custom requirement for SSE-KMS are different.
- If OPA is added, successful evaluation alone does not mean its decision allows the change.

These are design findings, not verified runtime fixes.

## Add an entry when a real problem occurs

### Short problem title

- Date / commit / environment:
- Command and error:
- Expected behavior:
- Root cause: unknown until verified
- Fix attempted:
- Verification command and actual result:
- Status: open or resolved

Do not mark a problem resolved until the original failing step has been rerun successfully.
