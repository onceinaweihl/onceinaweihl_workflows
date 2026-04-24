# onceinaweihl_workflows

Zentrale GitHub Actions für alle onceinaweihl Flutter-Apps. Jede App bindet die Workflows hier als Reusable Workflows ein — die eigentliche CI/CD-Logik liegt einmal an diesem Ort.

---

## Struktur

```
.github/workflows/
  reusable-ci.yml            # PR-Checks: Lint, Codegen, Tests, Android Build
  reusable-cd.yml            # Release: Build + Sign + Store Upload
  reusable-release-please.yml # Automatisches Versioning via Conventional Commits

actions/
  setup-core-auth/           # GitHub App Token für onceinaweihl_core

template/
  .github/workflows/
    ci.yml                   # Thin wrapper — kopieren, 3 Werte anpassen
    cd.yml
    release.yml
  release-please-config.json
  .release-please-manifest.json
```

---

## Neue App einrichten

### 1. Template-Dateien kopieren

Kopiere den gesamten Inhalt von `template/` in das Root des neuen App-Repos:

```
.github/workflows/ci.yml
.github/workflows/cd.yml
.github/workflows/release.yml
release-please-config.json
.release-please-manifest.json
```

### 2. App-spezifische Werte anpassen

In `.github/workflows/ci.yml`:
```yaml
flutter_version: '3.41.4'       # aktuelle Flutter-Version
working_dir: frontend            # Pfad zum Flutter-Projekt
coverage_threshold: 70           # Mindestzahl für Test-Coverage in %
```

In `.github/workflows/cd.yml`:
```yaml
flutter_version: '3.41.4'
working_dir: frontend
android_app_id: de.onceinaweihl.APPNAME   # Package Name aus build.gradle
ios_bundle_id: de.onceinaweihl.APPNAME    # Bundle ID aus Xcode
has_screenshots: true                      # false wenn keine Screenshot-Tests vorhanden
```

In `release-please-config.json`:
```json
"package-name": "APPNAME",
"component": "APPNAME",
"changelog-path": "frontend/CHANGELOG.md"
```

In `.release-please-manifest.json`:
```json
{ ".": "1.0.0" }
```

### 3. Repository-Variablen setzen

Unter **Settings → Secrets and variables → Actions → Variables**:

| Variable | Wert |
|---|---|
| `CORE_ACCESS_APP_ID` | GitHub App ID für onceinaweihl_core Zugriff |
| `DEPLOY_ANDROID_ENABLED` | `true` (auf `false` setzen um Android-Deploy zu pausieren) |
| `DEPLOY_IOS_ENABLED` | `true` (auf `false` setzen um iOS-Deploy zu pausieren) |

### 4. Secrets setzen

Unter **Settings → Secrets and variables → Actions → Secrets**:

**Core Auth**

| Secret | Beschreibung |
|---|---|
| `CORE_ACCESS_APP_KEY` | Private Key der GitHub App für onceinaweihl_core |

**Android**

| Secret | Beschreibung |
|---|---|
| `ANDROID_KEYSTORE_BASE64` | Release Keystore, base64-enkodiert |
| `ANDROID_KEYSTORE_PASSWORD` | Keystore-Passwort |
| `ANDROID_KEY_ALIAS` | Key Alias |
| `ANDROID_KEY_PASSWORD` | Key-Passwort |
| `GOOGLE_PLAY_JSON_KEY` | Service Account JSON für Google Play API |

**iOS**

| Secret | Beschreibung |
|---|---|
| `MATCH_PASSWORD` | Passwort für Fastlane Match Repo |
| `MATCH_GIT_TOKEN` | Token für Fastlane Match Git-Repo (Basic Auth Base64) |
| `ASC_KEY_ID` | App Store Connect API Key ID |
| `ASC_ISSUER_ID` | App Store Connect Issuer ID |
| `ASC_PRIVATE_KEY` | App Store Connect API Private Key (.p8 Inhalt) |

**Wiredash**

| Secret | Beschreibung |
|---|---|
| `WIREDASH_PROJECT_ID` | Wiredash Project ID |
| `WIREDASH_SECRET` | Wiredash Secret |

**Notifications**

| Secret | Beschreibung |
|---|---|
| `SLACK_WEBHOOK_URL` | Slack Incoming Webhook URL für Fehler-Notifications |

### 5. Actions-Zugriff auf dieses Repo erlauben

Im App-Repo unter **Settings → Actions → General**:
- "Allow all actions and reusable workflows" **oder**
- "Allow actions created by GitHub, and select non-GitHub actions" + `onceinaweihl/onceinaweihl_workflows` explizit erlauben

---

## Release-Prozess

Der Release läuft vollautomatisch über [Conventional Commits](https://www.conventionalcommits.org/) und [release-please](https://github.com/googleapis/release-please):

```
feat: add dark mode        → Minor-Bump  (1.0.0 → 1.1.0)
fix: crash on startup      → Patch-Bump  (1.0.0 → 1.0.1)
feat!: rewrite auth        → Major-Bump  (1.0.0 → 2.0.0)
chore:, docs:, refactor:   → kein Release
```

**Ablauf:**

1. Commits mit Conventional Commit Messages auf `main` pushen
2. release-please öffnet automatisch einen **Release PR** mit Version-Bump und Changelog
3. Vor dem Merge: Release Notes in `frontend/assets/whats_new/` ergänzen
4. Release PR mergen → release-please erstellt einen `v1.1.0`-Tag
5. Tag triggert den CD-Workflow → Build + Store Upload

**Tracks via Tag-Suffix:**

| Tag | Track |
|---|---|
| `v1.1.0` | Production |
| `v1.1.0-beta.1` | Beta / TestFlight |
| `v1.1.0-alpha.1` | Alpha (Android only) |

---

## iOS Build in CI deaktivieren

Der iOS Debug Build in CI ist standardmäßig **deaktiviert** (`run_ios_build: false`), da macOS Runner 10× teurer sind als Linux. Nur aktivieren wenn wirklich nötig:

```yaml
# .github/workflows/ci.yml
with:
  run_ios_build: true
```

iOS Release Builds laufen ausschließlich im CD-Workflow auf Tag-Pushes.
