---
generated: '2026-09-17'
method: generated
name: Collect artifacts from a workflow run
description: Find a run, list the artifacts it produced, resolve a download URL, and prune old artifacts and caches.
api: openapi/github-actions-artifacts-api-openapi.yml
operations: [listWorkflowRunsForRepo, listWorkflowRunArtifacts, getArtifact, downloadArtifact, listArtifactsForRepo, deleteArtifact, getActionsCacheUsage, listActionsCaches, deleteActionsCacheById]
source: >-
  Grounded in arazzo/github-actions-collect-run-artifacts-workflow.yml and
  arazzo/github-actions-prune-repo-caches-workflow.yml; operationIds verified
  verbatim in openapi/github-actions-artifacts-api-openapi.yml and
  openapi/github-actions-cache-api-openapi.yml.
---

# Collect artifacts from a workflow run

How a downstream system picks up what a build produced — and how it keeps storage from growing without limit.

## Auth
- `Authorization: Bearer <token>` with `actions:read` to list and download, `actions:write` to delete. See `authentication/github-actions-authentication.yml`.

## Steps
1. **Find the run** — `listWorkflowRunsForRepo` (`GET /repos/{owner}/{repo}/actions/runs`) with `status=success&per_page=1`, or use a run id you already hold.
2. **List its artifacts** — `listWorkflowRunArtifacts` (`GET /repos/{owner}/{repo}/actions/runs/{run_id}/artifacts`). Each entry carries `id`, `name`, `size_in_bytes`, `expired` and `expires_at`. **Check `expired` before downloading** — an expired artifact still appears in the listing.
3. **Resolve the download** — `downloadArtifact` (`GET /repos/{owner}/{repo}/actions/artifacts/{artifact_id}/{archive_format}`) with `archive_format=zip`. It returns a **302** to a short-lived storage URL; capture the `Location` header and fetch it **without** your `Authorization` header attached.
4. **Inspect one** — `getArtifact` (`GET /repos/{owner}/{repo}/actions/artifacts/{artifact_id}`) for a single artifact's metadata.

## Pruning
5. **Repository-wide sweep** — `listArtifactsForRepo` (`GET /repos/{owner}/{repo}/actions/artifacts`) paginates every artifact in the repository; `deleteArtifact` (`DELETE .../artifacts/{artifact_id}`) removes one.
6. **Caches** — `getActionsCacheUsage` (`GET /repos/{owner}/{repo}/actions/cache/usage`) gives the total; `listActionsCaches` (`GET .../actions/caches`) supports `sort=size_in_bytes&direction=desc` to find the worst offenders; `deleteActionsCacheById` (`DELETE .../actions/caches/{cache_id}`) or `deleteActionsCacheByKey` (`DELETE .../actions/caches?key=`) removes them.

## Reversibility
- `deleteArtifact`, `deleteActionsCacheById` and `deleteActionsCacheByKey` are **permanent and immediate**. There is no trash, no restore window and no undo. Before an agent prunes, it should confirm the artifact is not the input to a downstream deployment.
- Deleting a cache is cheap to recover from in practice (the next run rebuilds it, more slowly); deleting an artifact is not, because the build that produced it may no longer be reproducible.

## Retention
- Default retention is 90 days and is configurable per repository/organization; expired artifacts return `410 Gone` on download. See `lifecycle/github-actions-lifecycle.yml`.

## Errors
- Envelope: `{ message, documentation_url }`. See `errors/github-actions-error-codes.yml`.
