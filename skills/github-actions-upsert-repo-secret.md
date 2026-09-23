---
generated: '2026-09-17'
method: generated
name: Store a repository secret
description: Fetch the repository public key, seal a value with libsodium, create or update the encrypted secret, then confirm it.
api: openapi/github-actions-secrets-api-openapi.yml
operations: [getRepoPublicKey, createOrUpdateRepoSecret, getRepoSecret, listRepoSecrets, deleteRepoSecret]
source: >-
  Grounded in arazzo/github-actions-upsert-repo-secret-workflow.yml;
  operationIds verified verbatim in openapi/github-actions-secrets-api-openapi.yml.
---

# Store a repository secret

Secrets are **never** sent in plaintext. The API takes a value already sealed against a per-repository public key, which is why this is a two-call flow and not one.

## Auth
- `Authorization: Bearer <token>` with `secrets:write` on the repository (admin or a fine-grained PAT with the Secrets permission). See `authentication/github-actions-authentication.yml` and `scopes/github-actions-scopes.yml`.

## Steps
1. **Get the public key** — `getRepoPublicKey` (`GET /repos/{owner}/{repo}/actions/secrets/public-key`). Returns `{ key_id, key }` where `key` is base64. Cache `key_id`; it rotates rarely but you must send the one that matches the key you encrypted with.
2. **Seal the value locally** — libsodium sealed box against the base64 `key`, then base64 the ciphertext. **Do this in your own process.** Never send the plaintext to any endpoint, never log it, and never write it into an artifact in this repo.
3. **Create or update** — `createOrUpdateRepoSecret` (`PUT /repos/{owner}/{repo}/actions/secrets/{secret_name}`) with `encrypted_value` and `key_id`. `201` on create, `204` on update — the status code is the only signal telling you which happened.
4. **Confirm** — `getRepoSecret` (`GET /repos/{owner}/{repo}/actions/secrets/{secret_name}`) returns `{ name, created_at, updated_at }`. **It never returns the value.** A read-back that shows the value would mean you are not talking to GitHub.

## Idempotency
- `PUT` here is idempotent by HTTP semantics — re-sending the same sealed value is safe and simply overwrites. There is no `Idempotency-Key` header on this API. See `conventions/github-actions-conventions.yml`.

## Reversibility
- `deleteRepoSecret` (`DELETE .../secrets/{secret_name}`) removes a secret. There is **no undo and no restore window** — a deleted secret is gone and must be re-sealed and re-created from a value you still hold elsewhere. Treat deletion as unrecoverable.
- Overwriting a secret is likewise unrecoverable: the previous value is not retained anywhere GitHub will show you.

## Naming rules
- Secret names may contain only alphanumerics and `_`, must not start with a digit, and must not start with the `GITHUB_` prefix. A name that violates this returns `422`.

## Errors
- `403` on the public key almost always means the token lacks the Secrets permission rather than repository access.
- Envelope: `{ message, documentation_url, errors[] }`. See `errors/github-actions-error-codes.yml`.
