---
generated: '2026-09-17'
method: generated
name: Register and manage a self-hosted runner
description: List runner application binaries, mint a registration token, label a runner, and remove it cleanly.
api: openapi/github-actions-self-hosted-runners-api-openapi.yml
operations: [listRunnerApplicationsForRepo, createRegistrationTokenForRepo, listSelfHostedRunnersForRepo, getSelfHostedRunnerForRepo, addCustomLabelsToSelfHostedRunnerForRepo, setCustomLabelsForSelfHostedRunnerForRepo, createRemoveTokenForRepo, deleteSelfHostedRunnerFromRepo]
source: >-
  Grounded in arazzo/github-actions-register-runner-workflow.yml; operationIds
  verified verbatim in openapi/github-actions-self-hosted-runners-api-openapi.yml.
---

# Register and manage a self-hosted runner

The capacity side of Actions. This is the flow an autoscaler runs, usually triggered by the `workflow_job` webhook with action `queued`.

## Auth
- `Authorization: Bearer <token>` with admin access to the repository (or `administration:write` on a fine-grained PAT). Organization-level runner groups need org admin. See `authentication/github-actions-authentication.yml`.

## Steps
1. **Pick the binary** — `listRunnerApplicationsForRepo` (`GET /repos/{owner}/{repo}/actions/runners/downloads`) returns per-OS/architecture download URLs, filenames and SHA-256 checksums. Verify the checksum before executing anything.
2. **Mint a registration token** — `createRegistrationTokenForRepo` (`POST /repos/{owner}/{repo}/actions/runners/registration-token`). Returns `{ token, expires_at }`. **The token expires in one hour and registers a machine into your repository** — treat it exactly as a credential: never log it, never put it in an artifact, never pass it through a third party.
3. **Register the runner** on the machine with `config.sh --url <repo url> --token <token>`, then start the service.
4. **Confirm and label** — `listSelfHostedRunnersForRepo` (`GET /repos/{owner}/{repo}/actions/runners`) to find the runner id; `addCustomLabelsToSelfHostedRunnerForRepo` (`POST .../runners/{runner_id}/labels`) to add labels additively, or `setCustomLabelsForSelfHostedRunnerForRepo` (`PUT`) to replace the whole custom label set.
5. **Decommission** — `createRemoveTokenForRepo` (`POST .../runners/remove-token`) then `config.sh remove --token <token>` on the machine, and finally `deleteSelfHostedRunnerFromRepo` (`DELETE .../runners/{runner_id}`).

## Reversibility
- `addCustomLabelsToSelfHostedRunnerForRepo` is reversible — `removeCustomLabelFromSelfHostedRunnerForRepo` removes one label, `removeAllCustomLabelsFromSelfHostedRunnerForRepo` removes all custom labels. No window.
- `setCustomLabelsForSelfHostedRunnerForRepo` (`PUT`) **overwrites the entire custom label set** and does not return the previous one. Read the labels first with `listLabelsForSelfHostedRunnerForRepo` if you intend to be able to restore them.
- `deleteSelfHostedRunnerFromRepo` is **not reversible** — re-adding the machine requires a fresh registration token and a re-run of step 3.

## Security note
- A self-hosted runner on a **public** repository is a documented risk: a fork's pull request can run untrusted code on your machine. GitHub's own guidance is not to use self-hosted runners with public repositories. See `security/github-actions-domain-security.yml` and the Actions security docs.

## Errors
- `409` on delete means the runner is currently executing a job; wait for it to idle.
- Envelope: `{ message, documentation_url }`. See `errors/github-actions-error-codes.yml`.
