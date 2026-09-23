---
generated: '2026-09-17'
method: generated
name: Diagnose a failed workflow run
description: Find the most recent failed run, identify the failing job and step, and resolve its log download URL.
api: openapi/github-actions-workflow-runs-api-openapi.yml
operations: [listWorkflowRunsForRepo, listJobsForWorkflowRun, getJobForWorkflowRun, downloadJobLogsForWorkflowRun, downloadWorkflowRunLogs]
source: >-
  Grounded in arazzo/github-actions-inspect-failed-job-logs-workflow.yml;
  operationIds verified verbatim in openapi/github-actions-workflow-runs-api-openapi.yml
  and openapi/github-actions-jobs-api-openapi.yml.
---

# Diagnose a failed workflow run

The read-only triage flow — safe for an agent to run unattended, because every operation here is a `GET`.

## Auth
- `Authorization: Bearer <token>` with read access to Actions (`actions:read`). See `authentication/github-actions-authentication.yml`.

## Steps
1. **Find the failure** — `listWorkflowRunsForRepo` (`GET /repos/{owner}/{repo}/actions/runs`) with `status=failure` and `per_page=1`. Narrow with `branch`, `event` or `created` (supports `>=YYYY-MM-DD` range syntax) when you need a specific window.
2. **List the jobs** — `listJobsForWorkflowRun` (`GET /repos/{owner}/{repo}/actions/runs/{run_id}/jobs`). Filter to `conclusion == "failure"`. Each job carries a `steps[]` array; the failing step's `number` and `name` are usually enough to answer "what broke" without reading a log at all.
3. **Get the job** — `getJobForWorkflowRun` (`GET /repos/{owner}/{repo}/actions/jobs/{job_id}`) for the full step timeline, runner labels and timings.
4. **Resolve the log** — `downloadJobLogsForWorkflowRun` (`GET /repos/{owner}/{repo}/actions/jobs/{job_id}/logs`) returns a **302 redirect** to a short-lived Location URL, not the log body. Capture the `Location` header; do not follow it with the `Authorization` header attached. `downloadWorkflowRunLogs` does the same for the whole run as a zip archive.
5. **Re-run only what failed** — when the cause is transient, `rerunFailedJobs` (`POST /repos/{owner}/{repo}/actions/runs/{run_id}/rerun-failed-jobs`) re-runs just the failed jobs; `rerunJobForWorkflowRun` re-runs one named job.

## Notes for agents
- Attempts matter: a re-run creates a new attempt on the SAME run id. Use `getWorkflowRunAttempt` and `listJobsForWorkflowRunAttempt` to read a specific historical attempt — the default endpoints return the latest attempt, which silently changes underneath you after a re-run.
- The MCP `get_job_logs` tool does this in one call with `failed_only=true` and `tail_lines`, which the REST API has no equivalent for. See `mcp/github-actions-tool-crosswalk.yml`.

## Errors
- `410 Gone` on logs means the retention window expired (90 days default for public repos; configurable).
- Error envelope: `{ message, documentation_url }`. See `errors/github-actions-error-codes.yml`.
