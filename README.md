# GitHub Actions

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

GitHub Actions is GitHub's hosted CI/CD and workflow automation platform, and this record covers the REST API surface that drives it. Eighty-two operations across eleven resource areas let a caller dispatch and cancel workflow runs, poll runs and jobs, read and prune logs, artifacts and caches, seal and rotate encrypted secrets and variables, set Actions permissions and default workflow token scopes, customize the OIDC subject claim used for cloud federation, and register, label and retire self-hosted runners and runner groups. The API is authenticated with bearer tokens (fine-grained or classic PATs, OAuth user tokens, GitHub App installation tokens, or the workflow's own GITHUB_TOKEN), versioned by a dated X-GitHub-Api-Version header, rate limited per hour by authentication method, and paired with a nine-event webhook surface that carries the run and job lifecycle plus the deployment approval callback.

**Areas:** CI/CD · Continuous Integration · Continuous Deployment · DevOps · Pipelines · Workflows · Automation · Developer Tools · Software Development · Build Automation · T1 · GitHub

## GitHub Actions on APIs.io

Everything profiled for GitHub Actions is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/github-actions/](https://apis.io/providers/github-actions/)** — or go straight to one of the APIs or properties below.

### APIs (11)

- [GitHub Actions Artifacts API](https://apis.io/apis/github-actions/github-actions-artifacts-api/) — Download and manage workflow run artifacts
- [GitHub Actions Cache API](https://apis.io/apis/github-actions/github-actions-cache-api/) — Manage workflow dependency caches
- [GitHub Actions Jobs API](https://apis.io/apis/github-actions/github-actions-jobs-api/) — Access information about workflow jobs
- [GitHub Actions OIDC API](https://apis.io/apis/github-actions/github-actions-oidc-api/) — Manage OIDC subject claim customization
- [GitHub Actions Permissions API](https://apis.io/apis/github-actions/github-actions-permissions-api/) — Control Actions enablement and permissions
- [GitHub Actions Secrets API](https://apis.io/apis/github-actions/github-actions-secrets-api/) — Manage encrypted secrets for Actions
- [GitHub Actions Self-Hosted Runner Groups API](https://apis.io/apis/github-actions/github-actions-self-hosted-runner-groups-api/) — Manage runner groups for organizations
- [GitHub Actions Self-Hosted Runners API](https://apis.io/apis/github-actions/github-actions-self-hosted-runners-api/) — Manage self-hosted runners for workflows
- [GitHub Actions Variables API](https://apis.io/apis/github-actions/github-actions-variables-api/) — Create and manage workflow variables
- [GitHub Actions Workflow Runs API](https://apis.io/apis/github-actions/github-actions-workflow-runs-api/) — Manage and monitor workflow run executions
- [GitHub Actions Workflows API](https://apis.io/apis/github-actions/github-actions-workflows-api/) — Manage workflow files and workflow runs

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### Arazzo workflows (11)

Multi-step workflows that chain operations into a business task.

- [GitHub Actions Approve a Pending Deployment](https://apis.io/arazzos/github-actions/github-actions-approve-pending-deployment-workflow/)
- [GitHub Actions Cancel a Workflow Run and Confirm](https://apis.io/arazzos/github-actions/github-actions-cancel-run-workflow/)
- [GitHub Actions Collect Workflow Run Artifacts](https://apis.io/arazzos/github-actions/github-actions-collect-run-artifacts-workflow/)
- [GitHub Actions Dispatch and Track a Workflow Run](https://apis.io/arazzos/github-actions/github-actions-dispatch-and-track-run-workflow/)
- [GitHub Actions Inspect Failed Job Logs](https://apis.io/arazzos/github-actions/github-actions-inspect-failed-job-logs-workflow/)
- [GitHub Actions Prune Repository Caches](https://apis.io/arazzos/github-actions/github-actions-prune-repo-caches-workflow/)
- [GitHub Actions Register a Self-hosted Runner](https://apis.io/arazzos/github-actions/github-actions-register-runner-workflow/)
- [GitHub Actions Re-run Failed Jobs and Track](https://apis.io/arazzos/github-actions/github-actions-rerun-failed-run-workflow/)
- [GitHub Actions Share an Organization Secret with Selected Repositories](https://apis.io/arazzos/github-actions/github-actions-share-org-secret-workflow/)
- [GitHub Actions Upsert a Repository Secret](https://apis.io/arazzos/github-actions/github-actions-upsert-repo-secret-workflow/)
- [GitHub Actions Upsert a Repository Variable](https://apis.io/arazzos/github-actions/github-actions-upsert-repo-variable-workflow/)

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Github Actions Webhooks](https://apis.io/asyncapis/github-actions/github-actions-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [github](https://apis.io/servers/github-actions/github/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Github Actions Agentic Access](https://apis.io/agentic-access/github-actions/github-actions-agentic-access/)

#### JSON Schema (34)

The data models the API reads and writes.

- [ActionsCacheEntry](https://apis.io/schemas/github-actions/github-actions-actions-cache-entry/)
- [ActionsCacheUsage](https://apis.io/schemas/github-actions/github-actions-actions-cache-usage/)
- [ActionsDefaultWorkflowPermissions](https://apis.io/schemas/github-actions/github-actions-actions-default-workflow-permissions/)
- [ActionsOrganizationPermissions](https://apis.io/schemas/github-actions/github-actions-actions-organization-permissions/)
- [ActionsPublicKey](https://apis.io/schemas/github-actions/github-actions-actions-public-key/)
- [ActionsRepositoryPermissions](https://apis.io/schemas/github-actions/github-actions-actions-repository-permissions/)
- [ActionsSecret](https://apis.io/schemas/github-actions/github-actions-actions-secret/)
- [ActionsVariable](https://apis.io/schemas/github-actions/github-actions-actions-variable/)
- [Artifact](https://apis.io/schemas/github-actions/github-actions-artifact/)
- [AuthenticationToken](https://apis.io/schemas/github-actions/github-actions-authentication-token/)
- [GitHub Actions Cache Entry](https://apis.io/schemas/github-actions/github-actions-cache/)
- [Deployment](https://apis.io/schemas/github-actions/github-actions-deployment/)
- [EnvironmentApproval](https://apis.io/schemas/github-actions/github-actions-environment-approval/)
- [Job](https://apis.io/schemas/github-actions/github-actions-job/)
- [JobStep](https://apis.io/schemas/github-actions/github-actions-job-step/)
- [MinimalRepository](https://apis.io/schemas/github-actions/github-actions-minimal-repository/)
- [OidcCustomSub](https://apis.io/schemas/github-actions/github-actions-oidc-custom-sub/)
- [OidcCustomSubOrg](https://apis.io/schemas/github-actions/github-actions-oidc-custom-sub-org/)
- [OrgActionsSecret](https://apis.io/schemas/github-actions/github-actions-org-actions-secret/)
- [PendingDeployment](https://apis.io/schemas/github-actions/github-actions-pending-deployment/)
- [GitHub Actions Workflow Run](https://apis.io/schemas/github-actions/github-actions-run/)
- [GitHub Actions Self-Hosted Runner](https://apis.io/schemas/github-actions/github-actions-runner/)
- [RunnerApplication](https://apis.io/schemas/github-actions/github-actions-runner-application/)
- [RunnerGroup](https://apis.io/schemas/github-actions/github-actions-runner-group/)
- [RunnerLabel](https://apis.io/schemas/github-actions/github-actions-runner-label/)
- …and 9 more published on APIs.io

#### JSON Structure (29)

Data models expressed in JSON Structure.

- [Github Actions Actions Cache Entry Structure](https://apis.io/json-structure/github-actions/github-actions-actions-cache-entry-structure/)
- [Github Actions Actions Cache Usage Structure](https://apis.io/json-structure/github-actions/github-actions-actions-cache-usage-structure/)
- [Github Actions Actions Default Workflow Permissions Structure](https://apis.io/json-structure/github-actions/github-actions-actions-default-workflow-permissions-structure/)
- [Github Actions Actions Organization Permissions Structure](https://apis.io/json-structure/github-actions/github-actions-actions-organization-permissions-structure/)
- [Github Actions Actions Public Key Structure](https://apis.io/json-structure/github-actions/github-actions-actions-public-key-structure/)
- [Github Actions Actions Repository Permissions Structure](https://apis.io/json-structure/github-actions/github-actions-actions-repository-permissions-structure/)
- [Github Actions Actions Secret Structure](https://apis.io/json-structure/github-actions/github-actions-actions-secret-structure/)
- [Github Actions Actions Variable Structure](https://apis.io/json-structure/github-actions/github-actions-actions-variable-structure/)
- [Github Actions Artifact Structure](https://apis.io/json-structure/github-actions/github-actions-artifact-structure/)
- [Github Actions Authentication Token Structure](https://apis.io/json-structure/github-actions/github-actions-authentication-token-structure/)
- [Github Actions Deployment Structure](https://apis.io/json-structure/github-actions/github-actions-deployment-structure/)
- [Github Actions Environment Approval Structure](https://apis.io/json-structure/github-actions/github-actions-environment-approval-structure/)
- [Github Actions Job Step Structure](https://apis.io/json-structure/github-actions/github-actions-job-step-structure/)
- [Github Actions Job Structure](https://apis.io/json-structure/github-actions/github-actions-job-structure/)
- [Github Actions Minimal Repository Structure](https://apis.io/json-structure/github-actions/github-actions-minimal-repository-structure/)
- [Github Actions Oidc Custom Sub Org Structure](https://apis.io/json-structure/github-actions/github-actions-oidc-custom-sub-org-structure/)
- [Github Actions Oidc Custom Sub Structure](https://apis.io/json-structure/github-actions/github-actions-oidc-custom-sub-structure/)
- [Github Actions Org Actions Secret Structure](https://apis.io/json-structure/github-actions/github-actions-org-actions-secret-structure/)
- [Github Actions Pending Deployment Structure](https://apis.io/json-structure/github-actions/github-actions-pending-deployment-structure/)
- [Github Actions Runner Application Structure](https://apis.io/json-structure/github-actions/github-actions-runner-application-structure/)
- [Github Actions Runner Group Structure](https://apis.io/json-structure/github-actions/github-actions-runner-group-structure/)
- [Github Actions Runner Label Structure](https://apis.io/json-structure/github-actions/github-actions-runner-label-structure/)
- [Github Actions Self Hosted Runner Structure](https://apis.io/json-structure/github-actions/github-actions-self-hosted-runner-structure/)
- [Github Actions Simple Commit Structure](https://apis.io/json-structure/github-actions/github-actions-simple-commit-structure/)
- [Github Actions Simple User Structure](https://apis.io/json-structure/github-actions/github-actions-simple-user-structure/)
- …and 4 more published on APIs.io

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Github Actions Context](https://apis.io/jsonld/github-actions/github-actions-context/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [github-actions API Vocabulary](https://apis.io/vocabularies/github-actions/github-actions-vocabulary/)

#### Examples (29)

Example requests and responses.

- [Github Actions Actions Cache Entry Example](https://apis.io/examples/github-actions/github-actions-actions-cache-entry-example/)
- [Github Actions Actions Cache Usage Example](https://apis.io/examples/github-actions/github-actions-actions-cache-usage-example/)
- [Github Actions Actions Default Workflow Permissions Example](https://apis.io/examples/github-actions/github-actions-actions-default-workflow-permissions-example/)
- [Github Actions Actions Organization Permissions Example](https://apis.io/examples/github-actions/github-actions-actions-organization-permissions-example/)
- [Github Actions Actions Public Key Example](https://apis.io/examples/github-actions/github-actions-actions-public-key-example/)
- [Github Actions Actions Repository Permissions Example](https://apis.io/examples/github-actions/github-actions-actions-repository-permissions-example/)
- [Github Actions Actions Secret Example](https://apis.io/examples/github-actions/github-actions-actions-secret-example/)
- [Github Actions Actions Variable Example](https://apis.io/examples/github-actions/github-actions-actions-variable-example/)
- [Github Actions Artifact Example](https://apis.io/examples/github-actions/github-actions-artifact-example/)
- [Github Actions Authentication Token Example](https://apis.io/examples/github-actions/github-actions-authentication-token-example/)
- [Github Actions Deployment Example](https://apis.io/examples/github-actions/github-actions-deployment-example/)
- [Github Actions Environment Approval Example](https://apis.io/examples/github-actions/github-actions-environment-approval-example/)
- [Github Actions Job Example](https://apis.io/examples/github-actions/github-actions-job-example/)
- [Github Actions Job Step Example](https://apis.io/examples/github-actions/github-actions-job-step-example/)
- [Github Actions Minimal Repository Example](https://apis.io/examples/github-actions/github-actions-minimal-repository-example/)
- [Github Actions Oidc Custom Sub Example](https://apis.io/examples/github-actions/github-actions-oidc-custom-sub-example/)
- [Github Actions Oidc Custom Sub Org Example](https://apis.io/examples/github-actions/github-actions-oidc-custom-sub-org-example/)
- [Github Actions Org Actions Secret Example](https://apis.io/examples/github-actions/github-actions-org-actions-secret-example/)
- [Github Actions Pending Deployment Example](https://apis.io/examples/github-actions/github-actions-pending-deployment-example/)
- [Github Actions Runner Application Example](https://apis.io/examples/github-actions/github-actions-runner-application-example/)
- [Github Actions Runner Group Example](https://apis.io/examples/github-actions/github-actions-runner-group-example/)
- [Github Actions Runner Label Example](https://apis.io/examples/github-actions/github-actions-runner-label-example/)
- [Github Actions Self Hosted Runner Example](https://apis.io/examples/github-actions/github-actions-self-hosted-runner-example/)
- [Github Actions Simple Commit Example](https://apis.io/examples/github-actions/github-actions-simple-commit-example/)
- [Github Actions Simple User Example](https://apis.io/examples/github-actions/github-actions-simple-user-example/)
- …and 4 more published on APIs.io

#### Collections (13)

Postman and Open Collection request collections.

- [GitHub Actions API](https://apis.io/collections/github-actions/open-github-actions/)
- [GitHub Actions Artifacts API](https://apis.io/collections/github-actions/open-github-actions-artifacts-api/)
- [GitHub Actions Artifacts Cache API](https://apis.io/collections/github-actions/open-github-actions-cache-api/)
- [GitHub Actions Artifacts Jobs API](https://apis.io/collections/github-actions/open-github-actions-jobs-api/)
- [GitHub Actions Artifacts OIDC API](https://apis.io/collections/github-actions/open-github-actions-oidc-api/)
- [GitHub Actions Artifacts Permissions API](https://apis.io/collections/github-actions/open-github-actions-permissions-api/)
- [GitHub Actions Artifacts Secrets API](https://apis.io/collections/github-actions/open-github-actions-secrets-api/)
- [GitHub Actions Artifacts Self-Hosted Runner Groups API](https://apis.io/collections/github-actions/open-github-actions-self-hosted-runner-groups-api/)
- [GitHub Actions Artifacts Self-Hosted Runners API](https://apis.io/collections/github-actions/open-github-actions-self-hosted-runners-api/)
- [GitHub Actions Artifacts Variables API](https://apis.io/collections/github-actions/open-github-actions-variables-api/)
- [GitHub Actions Artifacts Workflow Runs API](https://apis.io/collections/github-actions/open-github-actions-workflow-runs-api/)
- [GitHub Actions Artifacts Workflows API](https://apis.io/collections/github-actions/open-github-actions-workflows-api/)
- [GitHub Actions API](https://apis.io/collections/github-actions/postman-github-actions/)

#### Overlays (22)

OpenAPI overlays, including conversational phrasing for each operation.

- [Github Actions Artifacts Api Overlay](https://apis.io/overlays/github-actions/github-actions-artifacts-api-overlay/)
- [Github Actions Artifacts Api Phrasing Overlay](https://apis.io/overlays/github-actions/github-actions-artifacts-api-phrasing-overlay/)
- [Github Actions Cache Api Overlay](https://apis.io/overlays/github-actions/github-actions-cache-api-overlay/)
- [Github Actions Cache Api Phrasing Overlay](https://apis.io/overlays/github-actions/github-actions-cache-api-phrasing-overlay/)
- [Github Actions Jobs Api Overlay](https://apis.io/overlays/github-actions/github-actions-jobs-api-overlay/)
- [Github Actions Jobs Api Phrasing Overlay](https://apis.io/overlays/github-actions/github-actions-jobs-api-phrasing-overlay/)
- [Github Actions Oidc Api Overlay](https://apis.io/overlays/github-actions/github-actions-oidc-api-overlay/)
- [Github Actions Oidc Api Phrasing Overlay](https://apis.io/overlays/github-actions/github-actions-oidc-api-phrasing-overlay/)
- [Github Actions Permissions Api Overlay](https://apis.io/overlays/github-actions/github-actions-permissions-api-overlay/)
- [Github Actions Permissions Api Phrasing Overlay](https://apis.io/overlays/github-actions/github-actions-permissions-api-phrasing-overlay/)
- [Github Actions Secrets Api Overlay](https://apis.io/overlays/github-actions/github-actions-secrets-api-overlay/)
- [Github Actions Secrets Api Phrasing Overlay](https://apis.io/overlays/github-actions/github-actions-secrets-api-phrasing-overlay/)
- [Github Actions Self Hosted Runner Groups Api Overlay](https://apis.io/overlays/github-actions/github-actions-self-hosted-runner-groups-api-overlay/)
- [Github Actions Self Hosted Runner Groups Api Phrasing Overlay](https://apis.io/overlays/github-actions/github-actions-self-hosted-runner-groups-api-phrasing-overlay/)
- [Github Actions Self Hosted Runners Api Overlay](https://apis.io/overlays/github-actions/github-actions-self-hosted-runners-api-overlay/)
- [Github Actions Self Hosted Runners Api Phrasing Overlay](https://apis.io/overlays/github-actions/github-actions-self-hosted-runners-api-phrasing-overlay/)
- [Github Actions Variables Api Overlay](https://apis.io/overlays/github-actions/github-actions-variables-api-overlay/)
- [Github Actions Variables Api Phrasing Overlay](https://apis.io/overlays/github-actions/github-actions-variables-api-phrasing-overlay/)
- [Github Actions Workflow Runs Api Overlay](https://apis.io/overlays/github-actions/github-actions-workflow-runs-api-overlay/)
- [Github Actions Workflow Runs Api Phrasing Overlay](https://apis.io/overlays/github-actions/github-actions-workflow-runs-api-phrasing-overlay/)
- [Github Actions Workflows Api Overlay](https://apis.io/overlays/github-actions/github-actions-workflows-api-overlay/)
- [Github Actions Workflows Api Phrasing Overlay](https://apis.io/overlays/github-actions/github-actions-workflows-api-phrasing-overlay/)

#### Governance rules (2)

Spectral rulesets for the provider's contracts.

- [GitHub Actions — jsonschema rules](https://apis.io/rules/github-actions/github-actions-jsonschema-spectral-rules/)
- [GitHub Actions API Rules](https://apis.io/rules/github-actions/github-actions-spectral-rules/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Github Actions Authentication](https://apis.io/security/github-actions/github-actions-authentication/)
- [Github Actions Domain Security](https://apis.io/security/github-actions/github-actions-domain-security/)
- [Github Actions Trust Center](https://apis.io/security/github-actions/github-actions-trust-center/)
- [Github Actions Vulnerability Disclosure](https://apis.io/security/github-actions/github-actions-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Github Actions Scopes](https://apis.io/scopes/github-actions/github-actions-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Github Actions Plans Pricing](https://apis.io/plans/github-actions/github-actions-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Github Actions Rate Limits](https://apis.io/rate-limits/github-actions/github-actions-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Github Actions Finops](https://apis.io/finops/github-actions/github-actions-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://github.com)
- [Documentation](https://docs.github.com/en/actions)
- [Getting started](https://docs.github.com/en/actions/get-started/quickstart)
- [Pricing](https://github.com/pricing)
- [Support](https://support.github.com)
- [Changelog](https://github.blog/changelog/label/actions/)
- [Blog](https://github.blog/tag/github-actions/)
- [Security](https://docs.github.com/en/actions/security-for-github-actions)
- [Compliance](https://github.com/trust-center)
- [Terms of service](https://docs.github.com/en/site-policy/github-terms/github-terms-of-service)
- [Privacy policy](https://docs.github.com/en/site-policy/privacy-policies/github-privacy-statement)
- [GitHub](https://github.com/github)
- [Status](https://www.githubstatus.com)

## API Evangelist rating

**Kin Score 81.3** — exemplar · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 75.0 |
| Contract quality | 70.2 |
| Contract governance | 31.8 |
| Operational transparency | 97.4 |
| Developer ergonomics | 83.3 |
| Access clarity | 85.5 |

**Agent readiness 48.3** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
| MCP Server | documented (partial credit) |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | mostly |

**Regulatory alignment 45.1** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/github-actions/](https://apis.io/providers/github-actions/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for GitHub Actions: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/github-actions/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
