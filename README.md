# Solution-App-releases

Public repository for app releases — APK files are automatically pushed here whenever a release is published in one of the private app repos.

## How it works

```
Private repo (e.g. aafiya)          This public repo
─────────────────────────           ────────────────────────────────
 Release published (v1)   ───────►  sync-apk-release workflow runs
                                    Downloads *.apk from private release
                                    Creates public release  aafiya-v1
                                    Attaches APK to the public release
```

## One-time setup

### 1 – Secret in *this* repo (`Solution-App-releases`)

| Secret name | What it is |
|---|---|
| `PRIVATE_REPO_TOKEN` | A fine-grained PAT (or classic PAT) belonging to `Singulary-tee` with **Contents read** access to every private app repo |

Go to **Settings → Secrets and variables → Actions → New repository secret** and add `PRIVATE_REPO_TOKEN`.

### 2 – Add the trigger workflow to each private repo

Copy `.github/private-repo-templates/notify-public-releases.yml` into the private repo at:

```
.github/workflows/notify-public-releases.yml
```

Then add a secret to the **private** repo:

| Secret name | What it is |
|---|---|
| `RELEASES_REPO_TOKEN` | A fine-grained PAT with **Contents read/write** and **Actions read/write** on `Singulary-tee/Solution-App-releases` |

That's it. The next time you publish a release in the private repo the APK will appear here automatically.

## Manual sync

You can also trigger a sync manually from the **Actions** tab → **Sync APK Release** → **Run workflow**, filling in:

- **Source repo** – e.g. `Singulary-tee/aafiya`
- **Release tag** – e.g. `v1`
- **App name** – e.g. `aafiya`

## Released apps

| App | Latest release |
|---|---|
| *(releases will appear here automatically)* | |
