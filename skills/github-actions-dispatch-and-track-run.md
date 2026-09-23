---
generated: '2026-09-17'
method: generated
name: Dispatch a workflow and track the run
description: Trigger a workflow_dispatch event, find the run it created, poll it to completion, and enumerate the jobs that executed.
api: openapi/github-actions-workflows-api-openapi.yml
operations: [createWorkflowDispatch, listWorkflowRuns, getWorkflowRun, listJobsForWorkflowRun]
source: >-
  Grounded in arazzo/github-actions-dispatch-and-track-run-workflow.yml;
  operationIds verified verbatim in openapi/github-actions-workflows-api-openapi.yml,
  openapi/github-actions-workflow-runs-api-openapi.yml and
  openapi/github-actions-jobs-api-openapi.yml.
---

# Dispatch a workflow and track the run

The core automation loop: start a workflow on demand, then follow it until it finishes.

## Auth
- `Authorization: Bearer <token>` — fine-grained PAT, OAuth user token, GitHub App installation token, or the job's own `GITHUB_TOKEN`. See `authentication/github-actions-authentication.yml`.
- Send `Accept: application/vnd.github+json` and `X-GitHub-Api-Version: 2022-11-28` on every request.
- The token needs write access to the repository's Actions (`actions:write`).

## Idempotency — read this before retrying
- **There is no `Idempotency-Key` header on this API.** `createWorkflowDispatch` is a `POST` and it is **not** idempotent: a blind retry after a timeout starts a SECOND run. See `conventions/github-actions-conventions.yml`.
- Retry safely by *reading* instead of re-posting: after a failed/ambiguous dispatch, call `listWorkflowRuns` filtered on your `ref` and check whether a run already exists before dispatching again.

## Steps
1. **Dispatch** — `createWorkflowDispatch` (`POST /repos/{owner}/{repo}/actions/workflows/{workflow_id}/dispatches`) with `ref` (branch or tag) and optional `inputs`. `workflow_id` accepts the numeric id **or** the workflow file name (`ci.yml`). Returns `204 No Content` — no run id comes back, which is why step 2 exists.
2. **Find the run it created** — `listWorkflowRuns` (`GET /repos/{owner}/{repo}/actions/workflows/{workflow_id}/runs`) with `event=workflow_dispatch`, `branch=<ref>`, `per_page=1`. Take `workflow_runs[0].id`. The run may not appear for a second or two; poll this call, do not assume the first response is empty because it failed.
3. **Poll to completion** — `getWorkflowRun` (`GET /repos/{owner}/{repo}/actions/runs/{run_id}`) until `status == "completed"`, then read `conclusion` (`success`, `failure`, `cancelled`, `timed_out`, `action_required`, `neutral`, `skipped`, `stale`).
4. **Enumerate the jobs** — `listJobsForWorkflowRun` (`GET /repos/{owner}/{repo}/actions/runs/{run_id}/jobs`) for per-job status, conclusion and step detail.

## Rate limits and polling
- 5,000 requests/hour for an authenticated user; see `rate-limits/github-actions-rate-limits.yml`.
- Read `X-RateLimit-Remaining` and back off before it reaches zero. On `403`/`429` honour `Retry-After`.
- Prefer a conditional request: send `If-None-Match` with the previous `ETag` while polling — a `304` does **not** count against the primary rate limit. This is the single biggest cost saving in a polling loop.
- Better still, subscribe to the `workflow_run` webhook (`completed`) instead of polling. See `asyncapi/github-actions-webhooks.yml`.

## Errors
- `404` on dispatch usually means the workflow has no `workflow_dispatch:` trigger on the default branch, not that the repo is missing.
- `422` means the `ref` does not exist or a required input is absent.
- Envelope is `{ message, documentation_url, status?, errors[]? }` — not RFC 9457. See `errors/github-actions-error-codes.yml`.

## Reversibility
- A dispatched run can be cancelled (`cancelWorkflowRun`) while it is queued or in progress, and force-cancelled (`forceCancelWorkflowRun`) if it hangs. Once it is `completed`, nothing undoes its side effects. See the reversibility block in `conventions/github-actions-conventions.yml`.
