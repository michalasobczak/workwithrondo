# workwithrondo — Rondo w GitHub Actions

Workflow do dołączenia w projektach na GitHubie: skan obecności artefaktów [Rondo/CDD](https://workwithrondo.com)
— README, CHANGELOG, specy, testy — z wynikiem w logu joba i w panelu Rondo (https://app.workwithrondo.com).

## Instalacja w projekcie

1. **Sekrety repozytorium** (Settings → Secrets and variables → Actions → New repository secret), wartości z panelu
   Rondo, strona licencji:
   - `RONDO_DOCKER_AUTH_CONFIG` — JSON logowania do `registry.workwithrondo.com` (robot tylko do pobierania),
   - `RONDO_LICENSE` — token licencji (wysyłka wyniku do panelu).
2. **Workflow** `.github/workflows/rondo.yml`:

   ```yaml
   name: Rondo
   on: [push, pull_request]
   jobs:
     rondo:
       uses: michalasobczak/workwithrondo/.github/workflows/rondo.yml@v1
       secrets: inherit
   ```

## Zachowanie

- Job nigdy nie blokuje pipeline'u; braki artefaktów to obserwacja, nie błąd.
- Bez `RONDO_DOCKER_AUTH_CONFIG` (np. pull request z forka) — ostrzeżenie, skan pominięty.
  Bez `RONDO_LICENSE` — wynik tylko w logu.
- Artefakt `rondo-scan` (JSON skanu) — 30 dni.
- Wyłączenie w projekcie: zmienna repozytorium `RONDO_DISABLED` = `true`.

## Bezpieczeństwo i prywatność

- Workflow ma tylko odczyt kodu (`contents: read`); akcje przypięte do commitów.
- Kontener `rondo` jako zwykły użytkownik, repozytorium zamontowane tylko do odczytu, skan bez dostępu do sieci.
- Do panelu trafiają wyłącznie metadane: projekt, gałąź, commit, obecność plików, liczba speców i testów, ścieżki speców.
  Nigdy treść plików ani dane osób.

## Wersje

Projekty wskazują tag `v1`; poprawki go przesuwają, zmiany niezgodne idą jako `v2`. Historia: [CHANGELOG.md](CHANGELOG.md).
