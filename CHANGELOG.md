# Changelog

## [1.1.1] — 2026-11-12

### Changed
- README skrócone do dwóch fragmentów konfiguracji; bez adresów usług Rondo w README i komentarzach.

## [1.1.0] — 2026-11-12

### Added
- Szablony GitLab CI do `include: remote`: `gitlab/rondo.gitlab-ci.yml` (executor docker) i
  `gitlab/rondo.shell.gitlab-ci.yml` (executor shell), obraz `rondo:0.5` — przeniesione z rondo-platform.

## [1.0.0] — 2026-11-11

### Added
- Reusable workflow `.github/workflows/rondo.yml`: skan obecności README, CHANGELOG, speców i testów obrazem
  `registry.workwithrondo.com/rondo/rondo:0.3` (raport v4), wysyłka wyniku do panelu Rondo, artefakt `rondo-scan`.
