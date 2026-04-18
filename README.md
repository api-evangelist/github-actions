# GitHub Actions (github-actions)
APIs for GitHub Actions - automation and CI/CD platform.

**URL:** [Visit APIs.json URL](https://docs.github.com/en/rest/actions)

## Timestamps

- **Created:** 2024
- **Modified:** 2026-04-18

## APIs

### GitHub Actions API
REST API for managing GitHub Actions workflows, runs, artifacts, and secrets.

**Human URL:** [https://docs.github.com/en/actions](https://docs.github.com/en/actions)

#### Tags

 - Automation, CI/CD, DevOps, Workflows

#### Properties

- [Documentation](https://docs.github.com/en/rest/actions)
- [OpenAPI](openapi/github-actions-openapi.yml)
- [Authentication](https://docs.github.com/en/rest/overview/authenticating-to-the-rest-api)
- [Getting Started](https://docs.github.com/en/actions/get-started/quickstart)
- [API Reference](https://docs.github.com/en/rest/actions)
- [Change Log](https://github.blog/changelog/label/actions/)
- [SDK - JavaScript](https://github.com/octokit/octokit.js)
- [SDK - Ruby](https://github.com/octokit/octokit.rb)
- [SDK - .NET](https://github.com/octokit/octokit.net)
- [SDK - Go](https://github.com/google/go-github)
- [CLI](https://cli.github.com/manual/gh_workflow_run)
- [Rate Limits](https://docs.github.com/en/rest/overview/rate-limits-for-the-rest-api)
- [JSON Schema - Workflow](json-schema/github-actions-workflow-schema.json)
- [JSON Schema - Run](json-schema/github-actions-run-schema.json)
- [JSON Schema - Job](json-schema/github-actions-job-schema.json)
- [JSON Schema - Artifact](json-schema/github-actions-artifact-schema.json)
- [JSON Schema - Secret](json-schema/github-actions-secret-schema.json)
- [JSON Schema - Runner](json-schema/github-actions-runner-schema.json)
- [JSON Schema - Variable](json-schema/github-actions-variable-schema.json)
- [JSON Schema - Cache](json-schema/github-actions-cache-schema.json)
- [JSON-LD](json-ld/github-actions-context.jsonld)

#### Endpoints

| Group | Description |
|---|---|
| Workflows | Manage workflow files and workflow runs |
| Workflow Runs | Manage and monitor workflow run executions |
| Artifacts | Download and manage workflow run artifacts |
| Secrets | Manage encrypted secrets for Actions |
| Self-hosted Runners | Manage self-hosted runners for workflows |
| Jobs | Access information about workflow jobs |
| Cache | Manage workflow dependency caches |
| Variables | Create and manage workflow variables |
| Permissions | Control Actions enablement and permissions |
| OIDC | Manage OIDC subject claim customization |
| Self-hosted Runner Groups | Manage runner groups for organizations |
| GitHub-hosted Runners | Provision and manage GitHub-hosted runners |

## Capabilities

### Workflow Capabilities

| Capability | Description | File |
|---|---|---|
| CI/CD Automation | Unified capability for GitHub Actions CI/CD automation combining workflow management, run monitoring, artifact handling, secrets/variables management, and runner administration. | [ci-cd-automation.yaml](capabilities/ci-cd-automation.yaml) |

### Shared Definitions

| API | File |
|---|---|
| GitHub Actions API | [actions.yaml](capabilities/shared/actions.yaml) |

## Common Properties

- [Terms of Service](https://docs.github.com/en/site-policy/github-terms/github-terms-of-service)
- [Privacy Policy](https://docs.github.com/en/site-policy/privacy-policies/github-privacy-statement)
- [Rate Limits](https://docs.github.com/en/rest/overview/rate-limits-for-the-rest-api)
- [Blog](https://github.blog/category/product/actions/)
- [Status](https://www.githubstatus.com)
- [Change Log](https://github.blog/changelog/label/actions/)
- [Getting Started](https://docs.github.com/en/actions/get-started/quickstart)
- [Authentication](https://docs.github.com/en/rest/overview/authenticating-to-the-rest-api)
- [Support](https://support.github.com)
- [Pricing](https://github.com/pricing)
- [GitHub Organization](https://github.com/github)
- [Portal](https://docs.github.com/en/rest)
- [Documentation](https://docs.github.com/en/actions)
- [Sign Up](https://github.com/signup)
- [Login](https://github.com/login)
- [Developer Portal](https://developer.github.com/)
- [Marketplace](https://github.com/marketplace?type=actions)
- [Stack Overflow](https://stackoverflow.com/questions/tagged/github-actions)
- [YouTube](https://www.youtube.com/github)
- [SDK - JavaScript](https://github.com/octokit/octokit.js)
- [SDK - Ruby](https://github.com/octokit/octokit.rb)
- [SDK - .NET](https://github.com/octokit/octokit.net)
- [SDK - Go](https://github.com/google/go-github)
- [CLI](https://cli.github.com/)
- [Security](https://docs.github.com/en/actions/security-for-github-actions)

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
