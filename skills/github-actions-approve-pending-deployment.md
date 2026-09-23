---
generated: '2026-09-17'
method: generated
name: Approve a pending deployment
description: Find a run waiting on an environment protection rule, read its pending deployments, approve or reject them, and follow the run to completion.
api: openapi/github-actions-workflow-runs-api-openapi.yml
operations: [getWorkflowRun, getPendingDeployments, reviewPendingDeployments, getWorkflowRunApprovals, reviewCustomGatesForRun, cancelWorkflowRun]
source: >-
  Grounded in arazzo/github-actions-approve-pending-deployment-workflow.yml;
  operationIds verified verbatim in openapi/github-actions-workflow-runs-api-openapi.yml.
---

# Approve a pending deployment

The human-in-the-loop gate. An agent running this skill is **casting a review decision that releases code to an environment** — treat it as the highest-consequence operation in this API.

## Auth
- `Authorization: Bearer <token>` for a principal that is a **named reviewer** on the environment. Membership in the reviewer list, not scope alone, is what authorises the decision. See `authentication/github-actions-authentication.yml`.

## Steps
1. **Confirm the run is waiting** — `getWorkflowRun` (`GET /repos/{owner}/{repo}/actions/runs/{run_id}`); `status` should be `waiting`.
2. **Read what is pending** — `getPendingDeployments` (`GET /repos/{owner}/{repo}/actions/runs/{run_id}/pending_deployments`). Each entry names the `environment`, the `wait_timer`, the `reviewers[]`, and `current_user_can_approve`. **Check `current_user_can_approve` before attempting a decision** — a `false` here means the call will fail and you should escalate to a human instead.
3. **Decide** — `reviewPendingDeployments` (`POST /repos/{owner}/{repo}/actions/runs/{run_id}/pending_deployments`) with `environment_ids[]`, `state` (`approved` or `rejected`) and a `comment`. Always write a comment naming *why*; it is the audit record.
4. **Follow the run** — poll `getWorkflowRun` until `completed`, then read `conclusion`.
5. **Audit** — `getWorkflowRunApprovals` (`GET /repos/{owner}/{repo}/actions/runs/{run_id}/approvals`) returns who approved what and when.

## Custom gates
- An external system that owns a custom deployment protection rule responds with `reviewCustomGatesForRun` (`POST /repos/{owner}/{repo}/actions/runs/{run_id}/deployment_protection_rule`) using the `environment_name` and a `state` of `approved` or `rejected`, plus the callback identifier delivered in the `deployment_protection_rule` webhook. See `asyncapi/github-actions-webhooks.yml`.

## Reversibility — the important part
- **An approval cannot be revoked.** Once `state: approved` is posted, the deployment proceeds; there is no un-approve operation and no window. The only remaining lever is `cancelWorkflowRun` (or `forceCancelWorkflowRun`) on the run that is now deploying, and by then the deployment job may already have taken effect on the target system.
- A rejection IS terminal too: the run concludes as `failure`, and restarting requires a new dispatch or re-run.
- Because of this, an agent should require explicit human confirmation before step 3 unless it has been given standing authority for the specific environment. See `agentic-access/github-actions-agentic-access.yml`.

## Errors
- `422` typically means the environment is not actually awaiting review, or the caller is not a reviewer.
- Envelope: `{ message, documentation_url }`. See `errors/github-actions-error-codes.yml`.
