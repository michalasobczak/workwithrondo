# workwithrondo

Rondo for GitHub Actions and GitLab CI. Secrets, variables and ready-to-paste config are in the Rondo panel (license page).

GitHub, `.github/workflows/rondo.yml`:

```yaml
name: Rondo
on: [push, pull_request]
jobs:
  rondo:
    uses: michalasobczak/workwithrondo/.github/workflows/rondo.yml@v1
    secrets: inherit
```

GitLab, `.gitlab-ci.yml` (shell executor: `rondo.shell.gitlab-ci.yml`):

```yaml
include:
  - remote: 'https://raw.githubusercontent.com/michalasobczak/workwithrondo/v1/gitlab/rondo.gitlab-ci.yml'
```

The job never blocks the pipeline. Disable it with `RONDO_DISABLED` = `true`.
