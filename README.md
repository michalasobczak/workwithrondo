# workwithrondo

Rondo w GitHub Actions i GitLab CI. Sekrety / zmienne i gotowy fragment konfiguracji — w panelu Rondo, strona licencji.

GitHub — `.github/workflows/rondo.yml`:

```yaml
name: Rondo
on: [push, pull_request]
jobs:
  rondo:
    uses: michalasobczak/workwithrondo/.github/workflows/rondo.yml@v1
    secrets: inherit
```

GitLab — `.gitlab-ci.yml` (runner shell: `rondo.shell.gitlab-ci.yml`):

```yaml
include:
  - remote: 'https://raw.githubusercontent.com/michalasobczak/workwithrondo/v1/gitlab/rondo.gitlab-ci.yml'
```

Job nie blokuje pipeline'u. Wyłączenie: zmienna `RONDO_DISABLED` = `true`.
